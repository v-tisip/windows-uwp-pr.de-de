---
title: Web Account Manager
description: In diesem Artikel wird beschrieben, wie Sie AccountsSettingsPane verwenden, um Ihre App für die Universelle Windows-Plattform (UWP) mit externen Identitätsanbietern wie Microsoft oder Facebook zu verbinden. Dazu verwenden Sie die Web Account Manager-APIs in Windows 10.
author: PatrickFarley
ms.author: pafarley
ms.date: 12/6/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Sicherheit
ms.assetid: ec9293a1-237d-47b4-bcde-18112586241a
ms.localizationpriority: medium
ms.openlocfilehash: 2de5c969610aa6b4fa1a3af01af565d35854b5f2
ms.sourcegitcommit: 4f6dc806229a8226894c55ceb6d6eab391ec8ab6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/20/2018
ms.locfileid: "4087651"
---
# <a name="web-account-manager"></a><span data-ttu-id="87e05-104">Web Account Manager</span><span class="sxs-lookup"><span data-stu-id="87e05-104">Web Account Manager</span></span>

<span data-ttu-id="87e05-105">In diesem Artikel wird beschrieben, wie Sie **[AccountsSettingsPane](https://docs.microsoft.com/uwp/api/Windows.UI.ApplicationSettings.AccountsSettingsPane)** verwenden, um Ihre App für die Universelle Windows-Plattform (UWP) mit externen Identitätsanbietern wie Microsoft oder Facebook zu verbinden. Dazu verwenden Sie die Web Account Manager-APIs in Windows 10.</span><span class="sxs-lookup"><span data-stu-id="87e05-105">This article describes how to use the **[AccountsSettingsPane](https://docs.microsoft.com/uwp/api/Windows.UI.ApplicationSettings.AccountsSettingsPane)** to connect your Universal Windows Platform (UWP) app to external identity providers, like Microsoft or Facebook, using the Windows 10 Web Account Manager APIs.</span></span> <span data-ttu-id="87e05-106">Sie erfahren, wie Sie die Berechtigung eines Benutzers für die Verwendung des Microsoft-Kontos des Benutzers anfordern können, ein Zugriffstoken erhalten und mit diesem grundlegende Vorgänge wie das Abrufen von Profildaten oder das Hochladen von Daten in das OneDrive-Konto des Benutzers durchführen können.</span><span class="sxs-lookup"><span data-stu-id="87e05-106">You'll learn how to request a user's permission to use their Microsoft account, obtain an access token, and use it to perform basic operations (like get profile data or upload files to their OneDrive account).</span></span> <span data-ttu-id="87e05-107">Die Schritte ähneln denen, die zum Abrufen einer Benutzerberechtigung und für den Zugriff über einen beliebigen Identitätsanbieter ausgeführt werden, der Web Account Manager unterstützt.</span><span class="sxs-lookup"><span data-stu-id="87e05-107">The steps are similar for getting user permission and access with any identity provider that supports the Web Account Manager.</span></span>

> [!NOTE]
> <span data-ttu-id="87e05-108">Ein vollständiges Codebeispiel finden Sie im [WebAccountManagement-Beispiel auf GitHub](http://go.microsoft.com/fwlink/p/?LinkId=620621).</span><span class="sxs-lookup"><span data-stu-id="87e05-108">For a complete code sample, see the [WebAccountManagement sample on GitHub](http://go.microsoft.com/fwlink/p/?LinkId=620621).</span></span>

## <a name="get-set-up"></a><span data-ttu-id="87e05-109">Vorbereitung</span><span class="sxs-lookup"><span data-stu-id="87e05-109">Get set up</span></span>

<span data-ttu-id="87e05-110">Erstellen Sie zunächst eine neue leere App in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="87e05-110">First, create a new, blank app in Visual Studio.</span></span> 

<span data-ttu-id="87e05-111">Um eine Verbindung mit Identitätsanbietern herzustellen, müssen Sie die App als Nächstes mit dem Store verknüpfen.</span><span class="sxs-lookup"><span data-stu-id="87e05-111">Second, in order to connect to identity providers, you'll need to associate your app with the Store.</span></span> <span data-ttu-id="87e05-112">Klicken Sie dazu mit der rechten Maustaste auf das Projekt, wählen Sie **Store** > **App mit Store verknüpfen** aus, und folgen Sie den Anweisungen des Assistenten.</span><span class="sxs-lookup"><span data-stu-id="87e05-112">To do this, right click your project, choose **Store** > **Associate app with the store**, and follow the wizard's instructions.</span></span> 

<span data-ttu-id="87e05-113">Erstellen Sie drittens eine allgemein verwendete Benutzeroberfläche, die eine einfache XAML-Schaltfläche und zwei Textfelder umfasst.</span><span class="sxs-lookup"><span data-stu-id="87e05-113">Third, create a very basic UI consisting of a simple XAML button and two text boxes.</span></span>

```XML
<StackPanel HorizontalAlignment="Center" VerticalAlignment="Center">
    <Button x:Name="LoginButton" Content="Log in" Click="LoginButton_Click" />
    <TextBlock x:Name="UserIdTextBlock"/>
    <TextBlock x:Name="UserNameTextBlock"/>
</StackPanel>
```

<span data-ttu-id="87e05-114">Im CodeBehind ist ein Ereignishandler an die Schaltfläche angefügt:</span><span class="sxs-lookup"><span data-stu-id="87e05-114">And an event handler attached to your button in the code-behind:</span></span>

```csharp
private void LoginButton_Click(object sender, RoutedEventArgs e)
{   
}
```

<span data-ttu-id="87e05-115">Fügen Sie zum Schluss die folgenden Namespaces hinzu, damit später keine Verweisprobleme auftreten:</span><span class="sxs-lookup"><span data-stu-id="87e05-115">Lastly, add the following namespaces so you don't have to worry about any reference issues later:</span></span> 

```csharp
using System;
using Windows.Security.Authentication.Web.Core;
using Windows.System;
using Windows.UI.ApplicationSettings;
using Windows.UI.Xaml;
using Windows.UI.Xaml.Controls;
using Windows.Data.Json;
using Windows.UI.Xaml.Navigation;
using Windows.Web.Http;
```

## <a name="show-the-accounts-settings-pane"></a><span data-ttu-id="87e05-116">Anzeigen des Bereichs mit Kontoeinstellungen</span><span class="sxs-lookup"><span data-stu-id="87e05-116">Show the accounts settings pane</span></span>

<span data-ttu-id="87e05-117">Das System bietet mit **AccountsSettingsPane** eine integrierte Benutzeroberfläche für die Verwaltung von Identitätsanbietern und Webkonten.</span><span class="sxs-lookup"><span data-stu-id="87e05-117">The system provides a built-in user interface for managing identity providers and web accounts called **AccountsSettingsPane**.</span></span> <span data-ttu-id="87e05-118">Sie können sie wie folgt anzeigen:</span><span class="sxs-lookup"><span data-stu-id="87e05-118">You can show it like this:</span></span>

```csharp
private void LoginButton_Click(object sender, RoutedEventArgs e)
{
    AccountsSettingsPane.Show(); 
}
```

<span data-ttu-id="87e05-119">Wenn Sie Ihre App ausführen und auf die Anmeldeschaltfläche klicken, sollte ein leeres Fenster angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="87e05-119">If you run your app and click the "Log in" button, it should display an empty window.</span></span> 

![Bereich mit Kontoeinstellungen](images/tb-1.png)

<span data-ttu-id="87e05-121">Der Bereich ist leer, weil das System nur eine UI-Shell bereitstellt. Der Entwickler kann den Bereich programmgesteuert mit Identitätsanbietern auffüllen.</span><span class="sxs-lookup"><span data-stu-id="87e05-121">The pane is empty because the system only provides a UI shell - it's up to the developer to programatically populate the pane with the identity providers.</span></span> 

## <a name="register-for-accountcommandsrequested"></a><span data-ttu-id="87e05-122">Registrieren für AccountCommandsRequested</span><span class="sxs-lookup"><span data-stu-id="87e05-122">Register for AccountCommandsRequested</span></span>

<span data-ttu-id="87e05-123">Um dem Bereich Befehle hinzuzufügen, führen wir zunächst eine Registrierung für den AccountCommandsRequested-Ereignishandler durch.</span><span class="sxs-lookup"><span data-stu-id="87e05-123">To add commands to the pane, we start by registering for the AccountCommandsRequested event handler.</span></span> <span data-ttu-id="87e05-124">Dadurch wird das System angewiesen, unsere Buildlogik auszuführen, wenn der Benutzer die Anzeige des Bereichs anfordert (d. h. auf die XAML-Schaltfläche klickt).</span><span class="sxs-lookup"><span data-stu-id="87e05-124">This tells the system to run our build logic when the user asks to see the pane (e.g., clicks our XAML button).</span></span> 

<span data-ttu-id="87e05-125">Überschreiben Sie im CodeBehind das OnNavigatedTo-Ereignis und das OnNavigatedFrom-Ereignis, und fügen Sie ihnen den folgenden Code hinzu:</span><span class="sxs-lookup"><span data-stu-id="87e05-125">In your code behind, override the OnNavigatedTo and OnNavigatedFrom events and add the following code to them:</span></span> 

```csharp
protected override void OnNavigatedTo(NavigationEventArgs e)
{
    AccountsSettingsPane.GetForCurrentView().AccountCommandsRequested += BuildPaneAsync; 
}
```

```csharp
protected override void OnNavigatedFrom(NavigationEventArgs e)
{
    AccountsSettingsPane.GetForCurrentView().AccountCommandsRequested -= BuildPaneAsync; 
}
```

<span data-ttu-id="87e05-126">Da Benutzer nicht sehr häufig mit Konten interagieren, empfiehlt es sich, den Ereignishandler in der beschriebenen Weise zu registrieren bzw. seine Registrierung aufzuheben, um Arbeitsspeicherverluste zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="87e05-126">Users don't interact with accounts very often, so registering and deregistering your event handler in this fashion helps prevent memory leaks.</span></span> <span data-ttu-id="87e05-127">Dadurch wird der angepasste Bereich nur im Arbeitsspeicher vorgehalten, wenn eine hohe Wahrscheinlichkeit vorliegt, dass er vom Benutzer angefordert wird (der Benutzer befindet sich z. B. auf der Seite „Einstellungen“ oder „Anmelden“).</span><span class="sxs-lookup"><span data-stu-id="87e05-127">This way, your customized pane is only in memory when there's a high chance a user is going to ask for it (because they're on a "settings" or "login" page, for example).</span></span> 

## <a name="build-the-account-settings-pane"></a><span data-ttu-id="87e05-128">Erstellen des Bereichs mit Kontoeinstellungen</span><span class="sxs-lookup"><span data-stu-id="87e05-128">Build the account settings pane</span></span>

<span data-ttu-id="87e05-129">Die BuildPaneAsync-Methode wird immer dann aufgerufen, wenn **AccountsSettingsPane** angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="87e05-129">The BuildPaneAsync method is called whenever the **AccountsSettingsPane** is shown.</span></span> <span data-ttu-id="87e05-130">Dort legen wir den Code zur Anpassung der im Bereich angezeigten Befehle ab.</span><span class="sxs-lookup"><span data-stu-id="87e05-130">This is where we'll put the code to customize the commands shown in the pane.</span></span> 

<span data-ttu-id="87e05-131">Sie beginnen, indem Sie eine Verzögerung abrufen.</span><span class="sxs-lookup"><span data-stu-id="87e05-131">Start by obtaining a deferral.</span></span> <span data-ttu-id="87e05-132">Dadurch wird das System angewiesen, die Anzeige von **AccountsSettingsPane** so lange zu verzögern, bis der Buildvorgang abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="87e05-132">This tells the system to delay showing the **AccountsSettingsPane** until we're finished building it.</span></span>

```csharp
private async void BuildPaneAsync(AccountsSettingsPane s,
    AccountsSettingsPaneCommandsRequestedEventArgs e)
{
    var deferral = e.GetDeferral();
        
    deferral.Complete(); 
}
```

<span data-ttu-id="87e05-133">Als Nächstes rufen Sie einen Anbieter mit der WebAuthenticationCoreManager.FindAccountProviderAsync-Methode ab.</span><span class="sxs-lookup"><span data-stu-id="87e05-133">Next, get a provider using the WebAuthenticationCoreManager.FindAccountProviderAsync method.</span></span> <span data-ttu-id="87e05-134">Die Anbieter-URL ist je nach Anbieter verschieden und kann in der Anbieterdokumentation nachgeschlagen werden.</span><span class="sxs-lookup"><span data-stu-id="87e05-134">The URL for the provider varies based on the provider and can be found in the provider's documentation.</span></span> <span data-ttu-id="87e05-135">Für Microsoft-Konten und Azure Active Directory (Azure AD) lautet sie „https://login.microsoft.com“.</span><span class="sxs-lookup"><span data-stu-id="87e05-135">For Microsoft Accounts and Azure Active Directory, it's "https://login.microsoft.com".</span></span> 

```csharp
private async void BuildPaneAsync(AccountsSettingsPane s,
    AccountsSettingsPaneCommandsRequestedEventArgs e)
{
    var deferral = e.GetDeferral();
        
    var msaProvider = await WebAuthenticationCoreManager.FindAccountProviderAsync(
        "https://login.microsoft.com", "consumers"); 
        
    deferral.Complete(); 
}
```

<span data-ttu-id="87e05-136">Beachten Sie, dass auch die Zeichenfolge „consumers“ an den optionalen *authority*-Parameter übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="87e05-136">Notice that we also pass the string "consumers" to the optional *authority* parameter.</span></span> <span data-ttu-id="87e05-137">Dies liegt daran, dass Microsoft zwei verschiedene Authentifizierungsmethoden bereitstellt: Microsoft-Konten (MSA) für „Heimanwender“ und Azure Active Directory (AAD) für „Organisationen“.</span><span class="sxs-lookup"><span data-stu-id="87e05-137">This is because Microsoft provides two different types of authentication - Microsoft Accounts (MSA) for "consumers", and Azure Active Directory (AAD) for "organizations".</span></span> <span data-ttu-id="87e05-138">Die Autorität „consumers“ gibt an, dass die MSA-Option verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="87e05-138">The "consumers" authority indicates we want the MSA option.</span></span> <span data-ttu-id="87e05-139">Wenn Sie eine Unternehmens-App entwickeln, verwenden Sie stattdessen die Zeichenfolge „organizations“.</span><span class="sxs-lookup"><span data-stu-id="87e05-139">If you're developing an enterprise app, use the string "organizations" instead.</span></span>

<span data-ttu-id="87e05-140">Schließlich fügen Sie **AccountsSettingsPane** den Anbieter hinzu, indem Sie wie folgt einen neuen **[WebAccountProviderCommand](https://docs.microsoft.com/uwp/api/windows.ui.applicationsettings.webaccountprovidercommand)** erstellen:</span><span class="sxs-lookup"><span data-stu-id="87e05-140">Finally, add the provider to the **AccountsSettingsPane** by creating a new **[WebAccountProviderCommand](https://docs.microsoft.com/uwp/api/windows.ui.applicationsettings.webaccountprovidercommand)** like this:</span></span> 

```csharp
private async void BuildPaneAsync(AccountsSettingsPane s,
    AccountsSettingsPaneCommandsRequestedEventArgs e)
{
    var deferral = e.GetDeferral();

    var msaProvider = await WebAuthenticationCoreManager.FindAccountProviderAsync(
        "https://login.microsoft.com", "consumers");

    var command = new WebAccountProviderCommand(msaProvider, GetMsaTokenAsync);  

    e.WebAccountProviderCommands.Add(command);

    deferral.Complete(); 
}
```

<span data-ttu-id="87e05-141">Die an unseren neuen **WebAccountProviderCommand** übergebene GetMsaToken-Methode ist noch nicht vorhanden (da sie erst im nächsten Schritt erstellt wird). Sie können sie vorläufig als leere Methode hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="87e05-141">The GetMsaToken method we passed to our new **WebAccountProviderCommand** doesn't exist yet (we'll build that in the next step), so feel free to add it as an empty method for now.</span></span>

<span data-ttu-id="87e05-142">Führen Sie den vorangehenden Code aus. Der Bereich sollte jetzt wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="87e05-142">Run the above code and your pane should look something like this:</span></span> 

![Bereich mit Kontoeinstellungen](images/tb-2.png)

### <a name="request-a-token"></a><span data-ttu-id="87e05-144">Anfordern eines Tokens</span><span class="sxs-lookup"><span data-stu-id="87e05-144">Request a token</span></span>

<span data-ttu-id="87e05-145">Sobald die Option für das Microsoft-Konto in **AccountsSettingsPane** angezeigt wird, müssen wir festlegen, was bei der Auswahl der Option durch den Benutzer passiert.</span><span class="sxs-lookup"><span data-stu-id="87e05-145">Once we have the Microsoft Account option displaying in the **AccountsSettingsPane**, we need to handle what happens when the user selects it.</span></span> <span data-ttu-id="87e05-146">Die GetMsaToken-Methode wurde so registriert, dass sie ausgelöst wird, wenn sich der Benutzer für die Anmeldung mit seinem Microsoft-Konto entscheidet. Deshalb fordern wir an dieser Stelle das Token an.</span><span class="sxs-lookup"><span data-stu-id="87e05-146">We registered our GetMsaToken method to fire when the user chooses to log in with their Microsoft Account, so we'll obtain the token there.</span></span> 

<span data-ttu-id="87e05-147">Um ein Token anzufordern, verwenden Sie die RequestTokenAsync-Methode wie folgt:</span><span class="sxs-lookup"><span data-stu-id="87e05-147">To obtain a token, use the RequestTokenAsync method like this:</span></span> 

```csharp
private async void GetMsaTokenAsync(WebAccountProviderCommand command)
{
    WebTokenRequest request = new WebTokenRequest(command.WebAccountProvider, "wl.basic");
    WebTokenRequestResult result = await WebAuthenticationCoreManager.RequestTokenAsync(request);
}
```

<span data-ttu-id="87e05-148">In diesem Beispiel wird die Zeichenfolge „wl.basic“ an den Parameter _scope_ übergeben.</span><span class="sxs-lookup"><span data-stu-id="87e05-148">In this example, we pass the string "wl.basic" to the _scope_ parameter.</span></span> <span data-ttu-id="87e05-149">„scope“ steht für den Typ von Informationen, die Sie vom bereitstellenden Dienst für einen bestimmten Benutzer anfordern.</span><span class="sxs-lookup"><span data-stu-id="87e05-149">Scope represents the type of information you are requesting from the providing service on a specific user.</span></span> <span data-ttu-id="87e05-150">Bestimmte Bereiche ermöglichen nur den Zugriff auf grundlegende Informationen eines Benutzers, z.B. Name und E-Mail-Adresse, während andere Bereiche möglicherweise Zugriff auf vertrauliche Informationen wie die Fotos oder den E-Mail-Posteingang des Benutzers gewähren.</span><span class="sxs-lookup"><span data-stu-id="87e05-150">Certain scopes provide access only to a user's basic information, like name and email address, while other scopes might grant access to sensitive information such as the user's photos or email inbox.</span></span> <span data-ttu-id="87e05-151">Im Allgemeinen sollte Ihre App Berechtigungen in dem Umfang verwenden, der für die Durchführung ihrer Funktion am geringsten erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="87e05-151">Generally, your app should use the least permissive scope necessary to achieve its function.</span></span> <span data-ttu-id="87e05-152">Dienstanbieter stellen in ihrer Dokumentation Informationen dazu bereit, welche Bereiche erforderlich sind, um die für den betreffenden Dienst zu verwendenden Token anzufordern.</span><span class="sxs-lookup"><span data-stu-id="87e05-152">Service providers will provide documentation on which scopes are needed to get tokens for use with their services.</span></span> 

* <span data-ttu-id="87e05-153">Informationen zu Office365- und Outlook.com-Bereichen finden Sie unter [Authentifizieren von Office 365- und Outlook.com-APIs mit dem v2.0-Authentifizierungsendpunkt](https://msdn.microsoft.com/office/office365/howto/authenticate-Office-365-APIs-using-v2).</span><span class="sxs-lookup"><span data-stu-id="87e05-153">For Office 365 and Outlook.com scopes, see [Authenticate Office 365 and Outlook.com APIs using the v2.0 authentication endpoint](https://msdn.microsoft.com/office/office365/howto/authenticate-Office-365-APIs-using-v2).</span></span> 
* <span data-ttu-id="87e05-154">Informationen zu OneDrive-Bereichen finden Sie unter [Authentifizierung und Anmeldung bei OneDrive](https://dev.onedrive.com/auth/msa_oauth.htm#authentication-scopes).</span><span class="sxs-lookup"><span data-stu-id="87e05-154">For OneDrive scopes, see [OneDrive authentication and sign-in](https://dev.onedrive.com/auth/msa_oauth.htm#authentication-scopes).</span></span> 

> [!TIP]
> <span data-ttu-id="87e05-155">Wenn Ihre app Anmeldung Hinweis (für das Benutzerfeld mit der Standard-e-Mail-Adresse zu füllen) oder andere spezielle Eigenschaft, die im Zusammenhang mit der Oberfläche-Anmeldung verwendet, führen Sie sie optional in der **[WebTokenRequest.AppProperties](https://docs.microsoft.com/uwp/api/windows.security.authentication.web.core.webtokenrequest.appproperties#Windows_Security_Authentication_Web_Core_WebTokenRequest_AppProperties)** -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="87e05-155">Optionally, if your app uses a login hint (to populate the user field with a default email address) or other special property related to the sign-in experience, list it in the **[WebTokenRequest.AppProperties](https://docs.microsoft.com/uwp/api/windows.security.authentication.web.core.webtokenrequest.appproperties#Windows_Security_Authentication_Web_Core_WebTokenRequest_AppProperties)** property.</span></span> <span data-ttu-id="87e05-156">Dadurch wird das System an die Eigenschaft ignoriert werden sollen, das Web-Konto, das Konto Unterschiede im Cache verhindert, dass für die Zwischenspeicherung.</span><span class="sxs-lookup"><span data-stu-id="87e05-156">This will cause the system to ignore the property when caching the web account, which prevents account mismatches in the cache.</span></span>

<span data-ttu-id="87e05-157">Wenn Sie eine Unternehmens-App entwickeln, möchten Sie wahrscheinlich eine Verbindung mit einer Azure Active Directory (AAD)-Instanz herstellen und die Microsoft Graph-API anstelle regulärer MSA-Dienste verwenden.</span><span class="sxs-lookup"><span data-stu-id="87e05-157">If you're developing an enterprise app, you'll likely want to connect to an Azure Active Directory (AAD) instance and use the Microsoft Graph API instead of regular MSA services.</span></span> <span data-ttu-id="87e05-158">Verwenden Sie in diesem Szenario stattdessen folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="87e05-158">In this scenario, use the following code instead:</span></span> 

```csharp
private async void GetAadTokenAsync(WebAccountProviderCommand command)
{
    string clientId = "your_guid_here"; // Obtain your clientId from the Azure Portal
    WebTokenRequest request = new WebTokenRequest(provider, "User.Read", clientId);
    request.Properties.Add("resource", "https://graph.microsoft.com");
    WebTokenRequestResult result = await WebAuthenticationCoreManager.RequestTokenAsync(request);
}
```

<span data-ttu-id="87e05-159">Im weiteren Verlauf dieses Artikels wird das MSA-Szenario beschrieben, der Code für AAD ist allerdings sehr ähnlich.</span><span class="sxs-lookup"><span data-stu-id="87e05-159">The rest of this article continues describing the MSA scenario, but the code for AAD is very similar.</span></span> <span data-ttu-id="87e05-160">Weitere Informationen zu AAD/Graph einschließlich eines vollständigen Beispiels auf GitHub finden Sie in der [Microsoft Graph-Dokumentation](https://graph.microsoft.io/docs/platform/get-started).</span><span class="sxs-lookup"><span data-stu-id="87e05-160">For more info on AAD/Graph, including a full sample on GitHub, see the [Microsoft Graph documentation](https://graph.microsoft.io/docs/platform/get-started).</span></span>

## <a name="use-the-token"></a><span data-ttu-id="87e05-161">Verwenden des Tokens</span><span class="sxs-lookup"><span data-stu-id="87e05-161">Use the token</span></span>

<span data-ttu-id="87e05-162">Die RequestTokenAsync-Methode gibt ein WebTokenRequestResult-Objekt zurück, das die Ergebnisse für Ihre Anforderung enthält.</span><span class="sxs-lookup"><span data-stu-id="87e05-162">The RequestTokenAsync method returns a WebTokenRequestResult object, which contains the results of your request.</span></span> <span data-ttu-id="87e05-163">Wenn die Anforderung erfolgreich war, enthält sie ein Token.</span><span class="sxs-lookup"><span data-stu-id="87e05-163">If your request was successful, it will contain a token.</span></span>  

```csharp
private async void GetMsaTokenAsync(WebAccountProviderCommand command)
{
    WebTokenRequest request = new WebTokenRequest(command.WebAccountProvider, "wl.basic");
    WebTokenRequestResult result = await WebAuthenticationCoreManager.RequestTokenAsync(request);
    
    if (result.ResponseStatus == WebTokenRequestStatus.Success)
    {
        string token = result.ResponseData[0].Token; 
    }
}
```

> [!NOTE]
> <span data-ttu-id="87e05-164">Wenn Sie eine Fehlermeldung erhalten, wenn ein Token angefordert haben, stellen Sie sicher, dass Sie Ihre App im Store wie in Schritt 1 beschrieben zugeordnet haben.</span><span class="sxs-lookup"><span data-stu-id="87e05-164">If you receive an error when requesting a token, make sure you've associated your app with the Store as described in step one.</span></span> <span data-ttu-id="87e05-165">Ihre App wird nicht in der Lage sein, ein Token abzurufen, wenn Sie diesen Schritt übersprungen haben.</span><span class="sxs-lookup"><span data-stu-id="87e05-165">Your app won't be able to get a token if you skipped this step.</span></span> 

<span data-ttu-id="87e05-166">Sobald Sie im Besitz des Tokens sind, können Sie darüber die API Ihres Anbieters aufrufen.</span><span class="sxs-lookup"><span data-stu-id="87e05-166">Once you have a token, you can use it to call your provider's API.</span></span> <span data-ttu-id="87e05-167">Im folgenden Code wird die [Microsoft Live-API für Benutzerinformationen](https://msdn.microsoft.com/library/hh826533.aspx) aufgerufen, um grundlegende Informationen zum Benutzer zu erhalten und sie auf der Benutzeroberfläche anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="87e05-167">In the code below, we'll call the [user info Microsoft Live API](https://msdn.microsoft.com/library/hh826533.aspx) to obtain basic information about the user and display it in our UI.</span></span> <span data-ttu-id="87e05-168">Beachten Sie jedoch, dass in den meisten Fällen empfohlen wird, die einmal erhaltenen Tokens zu speichern und sie dann in einer separaten Methode zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="87e05-168">Note however that in most cases it is recommended that you store the token once obtained and then use it in a separate method.</span></span>

```csharp
private async void GetMsaTokenAsync(WebAccountProviderCommand command)
{
    WebTokenRequest request = new WebTokenRequest(command.WebAccountProvider, "wl.basic");
    WebTokenRequestResult result = await WebAuthenticationCoreManager.RequestTokenAsync(request);
    
    if (result.ResponseStatus == WebTokenRequestStatus.Success)
    {
        string token = result.ResponseData[0].Token; 
        
        var restApi = new Uri(@"https://apis.live.net/v5.0/me?access_token=" + token);

        using (var client = new HttpClient())
        {
            var infoResult = await client.GetAsync(restApi);
            string content = await infoResult.Content.ReadAsStringAsync();

            var jsonObject = JsonObject.Parse(content);
            string id = jsonObject["id"].GetString();
            string name = jsonObject["name"].GetString();

            UserIdTextBlock.Text = "Id: " + id; 
            UserNameTextBlock.Text = "Name: " + name;
        }
    }
}
```

<span data-ttu-id="87e05-169">Die Methode zum Aufrufen verschiedener REST-APIs ist je nach Anbieter verschieden. Informationen zur Verwendung des Tokens finden Sie in der API-Dokumentation des Anbieters.</span><span class="sxs-lookup"><span data-stu-id="87e05-169">How you call various REST APIs varies between providers; see the provider's API documentation for information on how to use your token.</span></span> 

## <a name="store-the-account-for-future-use"></a><span data-ttu-id="87e05-170">Speichern des Kontos für zukünftige Verwendung</span><span class="sxs-lookup"><span data-stu-id="87e05-170">Store the account for future use</span></span>

<span data-ttu-id="87e05-171">Token sind hilfreich, um sofort Informationen über einen Benutzer abzurufen, in der Regel haben sie jedoch unterschiedliche Ablaufzeiten. MSA-Token sind beispielsweise nur wenige Stunden gültig.</span><span class="sxs-lookup"><span data-stu-id="87e05-171">Tokens are useful for immediately obtaining information about a user, but they usually have varying lifespans - MSA tokens, for instance, are only valid for a few hours.</span></span> <span data-ttu-id="87e05-172">Sie müssen **AccountsSettingsPane** jedoch nicht jedes Mal erneut anzeigen, wenn ein Token abläuft.</span><span class="sxs-lookup"><span data-stu-id="87e05-172">Fortunately, you don't need to re-show the **AccountsSettingsPane** each time a token expires.</span></span> <span data-ttu-id="87e05-173">Nachdem Ihre App einmal von einem Benutzer autorisiert wurde, können Sie die Kontoinformationen des Benutzers für die zukünftige Verwendung speichern.</span><span class="sxs-lookup"><span data-stu-id="87e05-173">Once a user has authorized your app once, you can store the user's account information for future use.</span></span> 

<span data-ttu-id="87e05-174">Zu diesem Zweck verwenden Sie die **[WebAccount](https://docs.microsoft.com/uwp/api/windows.security.credentials.webaccount)**-Klasse.</span><span class="sxs-lookup"><span data-stu-id="87e05-174">To do this, use the **[WebAccount](https://docs.microsoft.com/uwp/api/windows.security.credentials.webaccount)** class.</span></span> <span data-ttu-id="87e05-175">Ein **WebAccount** wird von derselben Methode zurückgegeben, die Sie verwendet haben, um das Token anzufordern:</span><span class="sxs-lookup"><span data-stu-id="87e05-175">A **WebAccount** is returned by the same method you used to request the token:</span></span>

```csharp
private async void GetMsaTokenAsync(WebAccountProviderCommand command)
{
    WebTokenRequest request = new WebTokenRequest(command.WebAccountProvider, "wl.basic");
    WebTokenRequestResult result = await WebAuthenticationCoreManager.RequestTokenAsync(request);
    
    if (result.ResponseStatus == WebTokenRequestStatus.Success)
    {
        WebAccount account = result.ResponseData[0].WebAccount; 
    }
}
```

<span data-ttu-id="87e05-176">Sobald Sie über eine **WebAccount**-Instanz verfügen, können Sie es ganz einfach speichern.</span><span class="sxs-lookup"><span data-stu-id="87e05-176">Once you have a **WebAccount** instance, you can easily store it.</span></span> <span data-ttu-id="87e05-177">Im folgenden Beispiel verwenden wir LocalSettings.</span><span class="sxs-lookup"><span data-stu-id="87e05-177">In the following example, we use LocalSettings.</span></span> <span data-ttu-id="87e05-178">Weitere Informationen zur Verwendung von LocalSettings und anderen Methoden zum Speichern von Benutzerdaten finden Sie unter [Speichern und Abrufen von App-Einstellungen und -Daten](https://docs.microsoft.com/windows/uwp/app-settings/store-and-retrieve-app-data).</span><span class="sxs-lookup"><span data-stu-id="87e05-178">For more information on using LocalSettings and other methods to store user data, see [Store and retrieve app settings and data](https://docs.microsoft.com/windows/uwp/app-settings/store-and-retrieve-app-data).</span></span>

```csharp
private async void StoreWebAccount(WebAccount account)
{
    ApplicationData.Current.LocalSettings.Values["CurrentUserProviderId"] = account.WebAccountProvider.Id;
    ApplicationData.Current.LocalSettings.Values["CurrentUserId"] = account.Id; 
}
```

<span data-ttu-id="87e05-179">Anschließend können wir eine asynchrone Methode wie die folgende verwenden, um zu versuchen, ein Token im Hintergrund mit dem gespeicherten **WebAccount** abzurufen.</span><span class="sxs-lookup"><span data-stu-id="87e05-179">Then, we can use an asynchronous method like the following to attempt to obtain a token in the background with the stored **WebAccount**.</span></span>

```csharp
private async Task<string> GetTokenSilentlyAsync()
{
    string providerId = ApplicationData.Current.LocalSettings.Values["CurrentUserProviderId"]?.ToString();
    string accountId = ApplicationData.Current.LocalSettings.Values["CurrentUserId"]?.ToString();

    if (null == providerId || null == accountId)
    {
        return null; 
    }

    WebAccountProvider provider = await WebAuthenticationCoreManager.FindAccountProviderAsync(providerId);
    WebAccount account = await WebAuthenticationCoreManager.FindAccountAsync(provider, accountId);

    WebTokenRequest request = new WebTokenRequest(provider, "wl.basic");

    WebTokenRequestResult result = await WebAuthenticationCoreManager.GetTokenSilentlyAsync(request, account);
    if (result.ResponseStatus == WebTokenRequestStatus.UserInteractionRequired)
    {
        // Unable to get a token silently - you'll need to show the UI
        return null; 
    }
    else if (result.ResponseStatus == WebTokenRequestStatus.Success)
    {
        // Success
        return result.ResponseData[0].Token;
    }
    else
    {
        // Other error 
        return null; 
    }
}
```

<span data-ttu-id="87e05-180">Platzieren Sie die oben beschriebene Methode unmittelbar vor den Code, der **AccountsSettingsPane** aufbaut.</span><span class="sxs-lookup"><span data-stu-id="87e05-180">Place the above method just before the code that builds the **AccountsSettingsPane**.</span></span> <span data-ttu-id="87e05-181">Wenn das Token im Hintergrund abgerufen wird, muss der Bereich nicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="87e05-181">If the token is obtained in the background, there is no need to show the pane.</span></span> 

```csharp
private void LoginButton_Click(object sender, RoutedEventArgs e)
{
    string silentToken = await GetMsaTokenSilentlyAsync();

    if (silentToken != null)
    {
        // the token was obtained. store a reference to it or do something with it here.
    }
    else
    {
        // the token could not be obtained silently. Show the AccountsSettingsPane
        AccountsSettingsPane.Show();
    }
}
```

<span data-ttu-id="87e05-182">Da der Tokenabruf im Hintergrund sehr einfach ist, sollten Sie diese Methode verwenden, um Ihr Token zwischen Sitzungen zu aktualisieren, anstatt ein vorhandenes Token zwischenzuspeichern (da das Token jederzeit ablaufen kann).</span><span class="sxs-lookup"><span data-stu-id="87e05-182">Because obtaining a token silently is very simple, you should use this process to refresh your token between sessions rather than caching an existing token (since that token might expire at any time).</span></span>

> [!NOTE]
> <span data-ttu-id="87e05-183">Im vorangehenden Beispiel sind nur einfache Erfolgs- und Fehlerereignisse dargestellt.</span><span class="sxs-lookup"><span data-stu-id="87e05-183">The example above only covers basic success and fail cases.</span></span> <span data-ttu-id="87e05-184">Ihre App sollte auch außergewöhnliche Szenarien berücksichtigen (z. B. wenn ein Benutzer die Berechtigung für die App widerruft oder das Konto aus Windows entfernt) und sie angemessen behandeln.</span><span class="sxs-lookup"><span data-stu-id="87e05-184">Your app should also account for unusual scenarios (like a user revoking your app's permission or removing their account from Windows, for example) and handle them gracefully.</span></span>  

## <a name="remove-a-stored-account"></a><span data-ttu-id="87e05-185">Entfernen eines gespeicherten Kontos</span><span class="sxs-lookup"><span data-stu-id="87e05-185">Remove a stored account</span></span>

<span data-ttu-id="87e05-186">Wenn Sie ein Webkonto beibehalten, sollten Sie Benutzern die Möglichkeit geben, ihr Konto von Ihrer App zu trennen.</span><span class="sxs-lookup"><span data-stu-id="87e05-186">If you persist a web account, you may want to give your users the ability to disassociate their account with your app.</span></span> <span data-ttu-id="87e05-187">Auf diese Weise können sie sich effektiv von der App „abmelden“: Ihre Kontoinformationen werden nach dem Start nicht mehr automatisch geladen.</span><span class="sxs-lookup"><span data-stu-id="87e05-187">This way, they can can effectively "log out" of the app: their account information will no longer be loaded automatically upon launch.</span></span> <span data-ttu-id="87e05-188">Entfernen Sie dafür zuerst alle gespeicherten Konto- und Anbieterinformationen aus dem Speicher.</span><span class="sxs-lookup"><span data-stu-id="87e05-188">To do this, first remove any saved account and provider information from storage.</span></span> <span data-ttu-id="87e05-189">Rufen Sie dann **[SignOutAsync](https://docs.microsoft.com/uwp/api/windows.security.credentials.webaccount.SignOutAsync)** auf, um den Cache zu löschen und vorhandene App-Tokens für ungültig zu erklären.</span><span class="sxs-lookup"><span data-stu-id="87e05-189">Then call **[SignOutAsync](https://docs.microsoft.com/uwp/api/windows.security.credentials.webaccount.SignOutAsync)** to clear the cache and invalidate any existing tokens your app may have.</span></span> 

```csharp
private async Task SignOutAccountAsync(WebAccount account)
{
    ApplicationData.Current.LocalSettings.Values.Remove("CurrentUserProviderId");
    ApplicationData.Current.LocalSettings.Values.Remove("CurrentUserId"); 
    account.SignOutAsync(); 
}
```

## <a name="add-providers-that-dont-support-webaccountmanager"></a><span data-ttu-id="87e05-190">Hinzufügen von Anbietern, die WebAccountManager nicht unterstützen</span><span class="sxs-lookup"><span data-stu-id="87e05-190">Add providers that don't support WebAccountManager</span></span>

<span data-ttu-id="87e05-191">Wenn Sie die Authentifizierung über einen Dienst in Ihre App integrieren möchten, der Dienst WebAccountManager jedoch nicht unterstützt (z. B. Google+ oder Twitter), können Sie **AccountsSettingsPane** den Anbieter trotzdem manuell hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="87e05-191">If you want to integrate authentication from a service into your app but that service doesn't support WebAccountManager - Google+ or Twitter, for example - you can still manually add that provider to the **AccountsSettingsPane**.</span></span> <span data-ttu-id="87e05-192">Erstellen Sie dazu ein neues WebAccountProvider-Objekt unter Angabe Ihres eigenen Namens und PNG-Symbols. Fügen Sie das Objekt dann zur WebAccountProviderCommands-Liste hinzu.</span><span class="sxs-lookup"><span data-stu-id="87e05-192">To do so, create a new WebAccountProvider object and provide your own name and .png icon, then and add it to the WebAccountProviderCommands list.</span></span> <span data-ttu-id="87e05-193">Stubcode-Beispiel:</span><span class="sxs-lookup"><span data-stu-id="87e05-193">Here's some stub code:</span></span> 

 ```csharp
private async void BuildPaneAsync(AccountsSettingsPane s, AccountsSettingsPaneCommandsRequestedEventArgs e)
{
    // other code here 

    var twitterProvider = new WebAccountProvider("twitter", "Twitter", new Uri(@"ms-appx:///Assets/twitter-auth-icon.png")); 
    var twitterCmd = new WebAccountProviderCommand(twitterProvider, GetTwitterTokenAsync);
    e.WebAccountProviderCommands.Add(twitterCmd);   
    
    // other code here
}

private async void GetTwitterTokenAsync(WebAccountProviderCommand command)
{
    // Manually handle Twitter login here
}

```

> [!NOTE] 
> <span data-ttu-id="87e05-194">Dadurch wird **AccountsSettingsPane** lediglich ein Symbol hinzugefügt und die Methode ausgeführt, die beim Klicken auf das Symbol ausgeführt werden soll (in diesem Fall GetTwitterTokenAsync).</span><span class="sxs-lookup"><span data-stu-id="87e05-194">This only adds an icon to the **AccountsSettingsPane** and runs the method you specify when the icon is clicked (GetTwitterTokenAsync, in this case).</span></span> <span data-ttu-id="87e05-195">Sie müssen den Code angeben, durch den die eigentliche Authentifizierung behandelt wird.</span><span class="sxs-lookup"><span data-stu-id="87e05-195">You must provide the code that handles the actual authentication.</span></span> <span data-ttu-id="87e05-196">Weitere Informationen finden Sie unter (Webauthentifizierungsbroker)[web-authentication-broker], der Hilfsmethoden für die Authentifizierung mithilfe von REST-Diensten bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="87e05-196">For more information, see (Web authentication broker)[web-authentication-broker], which provides helper methods for authenticating using REST services.</span></span> 

## <a name="add-a-custom-header"></a><span data-ttu-id="87e05-197">Hinzufügen eines benutzerdefinierten Headers</span><span class="sxs-lookup"><span data-stu-id="87e05-197">Add a custom header</span></span>

<span data-ttu-id="87e05-198">Sie können den Bereich mit den Kontoeinstellungen mithilfe der HeaderText-Eigenschaft wie folgt anpassen:</span><span class="sxs-lookup"><span data-stu-id="87e05-198">You can customize the account settings pane using the HeaderText property, like this:</span></span> 

```csharp
private async void BuildPaneAsync(AccountsSettingsPane s, AccountsSettingsPaneCommandsRequestedEventArgs e)
{
    // other code here 
    
    args.HeaderText = "MyAwesomeApp works best if you're signed in.";   
    
    // other code here
}
```

![Bereich mit Kontoeinstellungen](images/tb-3.png)

<span data-ttu-id="87e05-200">Halten Sie Headertext kurz und einfach, und vermeiden Sie überflüssige Informationen.</span><span class="sxs-lookup"><span data-stu-id="87e05-200">Don't go overboard with header text; keep it short and sweet.</span></span> <span data-ttu-id="87e05-201">Wenn der Anmeldevorgang komplex ist und weitere Informationen angezeigt werden müssen, verknüpfen Sie den Benutzer über einen benutzerdefinierten Link mit einer separaten Seite.</span><span class="sxs-lookup"><span data-stu-id="87e05-201">If your login process is complicated and you need to display more information, link the user to a separate page using a custom link.</span></span> 

## <a name="add-custom-links"></a><span data-ttu-id="87e05-202">Hinzufügen von benutzerdefinierten Links</span><span class="sxs-lookup"><span data-stu-id="87e05-202">Add custom links</span></span>

<span data-ttu-id="87e05-203">Sie können dem AccountsSettingsPane benutzerdefinierte Befehle hinzufügen, die als Links unter den unterstützten WebAccountProviders angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="87e05-203">You can add custom commands to the AccountsSettingsPane, which appear as links below your supported WebAccountProviders.</span></span> <span data-ttu-id="87e05-204">Benutzerdefinierte Befehle eignen sich hervorragend für einfache Aufgaben in Verbindung mit Benutzerkonten, z. B. das Anzeigen einer Datenschutzrichtlinie oder das Öffnen einer Supportseite, wenn auf Benutzerseite ein Problem auftritt.</span><span class="sxs-lookup"><span data-stu-id="87e05-204">Custom commands are great for simple tasks related to user accounts, like displaying a privacy policy or launching a support page for users having trouble.</span></span> 

<span data-ttu-id="87e05-205">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="87e05-205">Here's an example:</span></span> 

```csharp
private async void BuildPaneAsync(AccountsSettingsPane s, AccountsSettingsPaneCommandsRequestedEventArgs e)
{
    // other code here 
    
    var settingsCmd = new SettingsCommand(
        "settings_privacy", 
        "Privacy policy", 
        async (x) => await Launcher.LaunchUriAsync(new Uri(@"https://privacy.microsoft.com/en-US/"))); 

    e.Commands.Add(settingsCmd); 
    
    // other code here
}
```

![Bereich mit Kontoeinstellungen](images/tb-4.png)

<span data-ttu-id="87e05-207">Einstellungsbefehle lassen sich grundsätzlich überall verwenden.</span><span class="sxs-lookup"><span data-stu-id="87e05-207">Theoretically, you can use settings commands for anything.</span></span> <span data-ttu-id="87e05-208">Es wird jedoch empfohlen, diese Art Befehle auf die oben beschriebenen intuitiven Kontoszenarien zu beschränken.</span><span class="sxs-lookup"><span data-stu-id="87e05-208">However, we suggest limiting their use to intuitive, account-related scenarios like those described above.</span></span> 

## <a name="see-also"></a><span data-ttu-id="87e05-209">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="87e05-209">See also</span></span>

[<span data-ttu-id="87e05-210">Windows.Security.Authentication.Web.Core-Namespace</span><span class="sxs-lookup"><span data-stu-id="87e05-210">Windows.Security.Authentication.Web.Core namespace</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.authentication.web.core.aspx)

[<span data-ttu-id="87e05-211">Windows.Security.Credentials-Namespace</span><span class="sxs-lookup"><span data-stu-id="87e05-211">Windows.Security.Credentials namespace</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.credentials.aspx)

[<span data-ttu-id="87e05-212">AccountsSettingsPane-Klasse</span><span class="sxs-lookup"><span data-stu-id="87e05-212">AccountsSettingsPane class</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.ui.applicationsettings.accountssettingspane)

[<span data-ttu-id="87e05-213">Webauthentifizierungsbroker</span><span class="sxs-lookup"><span data-stu-id="87e05-213">Web authentication broker</span></span>](web-authentication-broker.md)

[<span data-ttu-id="87e05-214">Beispiel für die Webkontoverwaltung</span><span class="sxs-lookup"><span data-stu-id="87e05-214">Web account management sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=620621)

[<span data-ttu-id="87e05-215">Lunch Scheduler-App</span><span class="sxs-lookup"><span data-stu-id="87e05-215">Lunch Scheduler app</span></span>](https://github.com/Microsoft/Windows-appsample-lunch-scheduler)
