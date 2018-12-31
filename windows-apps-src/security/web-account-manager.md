---
title: Web Account Manager
description: In diesem Artikel wird beschrieben, wie Sie AccountsSettingsPane verwenden, um Ihre App für die Universelle Windows-Plattform (UWP) mit externen Identitätsanbietern wie Microsoft oder Facebook zu verbinden. Dazu verwenden Sie die Web Account Manager-APIs in Windows 10.
ms.date: 12/6/2017
ms.topic: article
keywords: Windows 10, Uwp, Sicherheit
ms.assetid: ec9293a1-237d-47b4-bcde-18112586241a
ms.localizationpriority: medium
ms.openlocfilehash: 14f5139f5fe2c3d5d1f97040ee3bec33ea48d6ac
ms.sourcegitcommit: ffad7cfb5d5c099f9f559e966fd93b705b47d2bd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/31/2018
ms.locfileid: "8990328"
---
# <a name="web-account-manager"></a><span data-ttu-id="6017e-104">Web Account Manager</span><span class="sxs-lookup"><span data-stu-id="6017e-104">Web Account Manager</span></span>

<span data-ttu-id="6017e-105">In diesem Artikel wird beschrieben, wie Sie **[AccountsSettingsPane](https://docs.microsoft.com/uwp/api/Windows.UI.ApplicationSettings.AccountsSettingsPane)** verwenden, um Ihre App für die Universelle Windows-Plattform (UWP) mit externen Identitätsanbietern wie Microsoft oder Facebook zu verbinden. Dazu verwenden Sie die Web Account Manager-APIs in Windows 10.</span><span class="sxs-lookup"><span data-stu-id="6017e-105">This article describes how to use the **[AccountsSettingsPane](https://docs.microsoft.com/uwp/api/Windows.UI.ApplicationSettings.AccountsSettingsPane)** to connect your Universal Windows Platform (UWP) app to external identity providers, like Microsoft or Facebook, using the Windows 10 Web Account Manager APIs.</span></span> <span data-ttu-id="6017e-106">Sie erfahren, wie Sie die Berechtigung eines Benutzers für die Verwendung des Microsoft-Kontos des Benutzers anfordern können, ein Zugriffstoken erhalten und mit diesem grundlegende Vorgänge wie das Abrufen von Profildaten oder das Hochladen von Daten in das OneDrive-Konto des Benutzers durchführen können.</span><span class="sxs-lookup"><span data-stu-id="6017e-106">You'll learn how to request a user's permission to use their Microsoft account, obtain an access token, and use it to perform basic operations (like get profile data or upload files to their OneDrive account).</span></span> <span data-ttu-id="6017e-107">Die Schritte ähneln denen, die zum Abrufen einer Benutzerberechtigung und für den Zugriff über einen beliebigen Identitätsanbieter ausgeführt werden, der Web Account Manager unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6017e-107">The steps are similar for getting user permission and access with any identity provider that supports the Web Account Manager.</span></span>

> [!NOTE]
> <span data-ttu-id="6017e-108">Ein vollständiges Codebeispiel finden Sie im [WebAccountManagement-Beispiel auf GitHub](http://go.microsoft.com/fwlink/p/?LinkId=620621).</span><span class="sxs-lookup"><span data-stu-id="6017e-108">For a complete code sample, see the [WebAccountManagement sample on GitHub](http://go.microsoft.com/fwlink/p/?LinkId=620621).</span></span>

## <a name="get-set-up"></a><span data-ttu-id="6017e-109">Vorbereitung</span><span class="sxs-lookup"><span data-stu-id="6017e-109">Get set up</span></span>

<span data-ttu-id="6017e-110">Erstellen Sie zunächst eine neue leere App in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6017e-110">First, create a new, blank app in Visual Studio.</span></span> 

<span data-ttu-id="6017e-111">Um eine Verbindung mit Identitätsanbietern herzustellen, müssen Sie die App als Nächstes mit dem Store verknüpfen.</span><span class="sxs-lookup"><span data-stu-id="6017e-111">Second, in order to connect to identity providers, you'll need to associate your app with the Store.</span></span> <span data-ttu-id="6017e-112">Klicken Sie dazu mit der rechten Maustaste auf das Projekt, wählen Sie **Store** > **App mit Store verknüpfen** aus, und folgen Sie den Anweisungen des Assistenten.</span><span class="sxs-lookup"><span data-stu-id="6017e-112">To do this, right click your project, choose **Store** > **Associate app with the store**, and follow the wizard's instructions.</span></span> 

<span data-ttu-id="6017e-113">Erstellen Sie drittens eine allgemein verwendete Benutzeroberfläche, die eine einfache XAML-Schaltfläche und zwei Textfelder umfasst.</span><span class="sxs-lookup"><span data-stu-id="6017e-113">Third, create a very basic UI consisting of a simple XAML button and two text boxes.</span></span>

```XML
<StackPanel HorizontalAlignment="Center" VerticalAlignment="Center">
    <Button x:Name="LoginButton" Content="Log in" Click="LoginButton_Click" />
    <TextBlock x:Name="UserIdTextBlock"/>
    <TextBlock x:Name="UserNameTextBlock"/>
</StackPanel>
```

<span data-ttu-id="6017e-114">Im CodeBehind ist ein Ereignishandler an die Schaltfläche angefügt:</span><span class="sxs-lookup"><span data-stu-id="6017e-114">And an event handler attached to your button in the code-behind:</span></span>

```csharp
private void LoginButton_Click(object sender, RoutedEventArgs e)
{   
}
```

<span data-ttu-id="6017e-115">Fügen Sie zum Schluss die folgenden Namespaces hinzu, damit später keine Verweisprobleme auftreten:</span><span class="sxs-lookup"><span data-stu-id="6017e-115">Lastly, add the following namespaces so you don't have to worry about any reference issues later:</span></span> 

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

## <a name="show-the-accounts-settings-pane"></a><span data-ttu-id="6017e-116">Anzeigen des Bereichs mit Kontoeinstellungen</span><span class="sxs-lookup"><span data-stu-id="6017e-116">Show the accounts settings pane</span></span>

<span data-ttu-id="6017e-117">Das System bietet mit **AccountsSettingsPane** eine integrierte Benutzeroberfläche für die Verwaltung von Identitätsanbietern und Webkonten.</span><span class="sxs-lookup"><span data-stu-id="6017e-117">The system provides a built-in user interface for managing identity providers and web accounts called **AccountsSettingsPane**.</span></span> <span data-ttu-id="6017e-118">Sie können sie wie folgt anzeigen:</span><span class="sxs-lookup"><span data-stu-id="6017e-118">You can show it like this:</span></span>

```csharp
private void LoginButton_Click(object sender, RoutedEventArgs e)
{
    AccountsSettingsPane.Show(); 
}
```

<span data-ttu-id="6017e-119">Wenn Sie Ihre App ausführen und auf die Anmeldeschaltfläche klicken, sollte ein leeres Fenster angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="6017e-119">If you run your app and click the "Log in" button, it should display an empty window.</span></span> 

![Bereich mit Kontoeinstellungen](images/tb-1.png)

<span data-ttu-id="6017e-121">Der Bereich ist leer, weil das System nur eine UI-Shell bereitstellt. Der Entwickler kann den Bereich programmgesteuert mit Identitätsanbietern auffüllen.</span><span class="sxs-lookup"><span data-stu-id="6017e-121">The pane is empty because the system only provides a UI shell - it's up to the developer to programatically populate the pane with the identity providers.</span></span> 

> [!TIP]
> <span data-ttu-id="6017e-122">Optional können Sie **[ShowAddAccountAsync](https://docs.microsoft.com/uwp/api/windows.ui.applicationsettings.accountssettingspane.showaddaccountasync)** anstelle von **[Anzeigen](https://docs.microsoft.com/uwp/api/windows.ui.applicationsettings.accountssettingspane.show#Windows_UI_ApplicationSettings_AccountsSettingsPane_Show)** verwenden, die eine **[IAsyncAction](https://docs.microsoft.com/uwp/api/Windows.Foundation.IAsyncAction)**, für die Abfrage für den Status des Vorgangs zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="6017e-122">Optionally, you can use **[ShowAddAccountAsync](https://docs.microsoft.com/uwp/api/windows.ui.applicationsettings.accountssettingspane.showaddaccountasync)** instead of **[Show](https://docs.microsoft.com/uwp/api/windows.ui.applicationsettings.accountssettingspane.show#Windows_UI_ApplicationSettings_AccountsSettingsPane_Show)**, which will return an **[IAsyncAction](https://docs.microsoft.com/uwp/api/Windows.Foundation.IAsyncAction)**, to query for the status of the operation.</span></span> 

## <a name="register-for-accountcommandsrequested"></a><span data-ttu-id="6017e-123">Registrieren für AccountCommandsRequested</span><span class="sxs-lookup"><span data-stu-id="6017e-123">Register for AccountCommandsRequested</span></span>

<span data-ttu-id="6017e-124">Um dem Bereich Befehle hinzuzufügen, führen wir zunächst eine Registrierung für den AccountCommandsRequested-Ereignishandler durch.</span><span class="sxs-lookup"><span data-stu-id="6017e-124">To add commands to the pane, we start by registering for the AccountCommandsRequested event handler.</span></span> <span data-ttu-id="6017e-125">Dadurch wird das System angewiesen, unsere Buildlogik auszuführen, wenn der Benutzer die Anzeige des Bereichs anfordert (d. h. auf die XAML-Schaltfläche klickt).</span><span class="sxs-lookup"><span data-stu-id="6017e-125">This tells the system to run our build logic when the user asks to see the pane (e.g., clicks our XAML button).</span></span> 

<span data-ttu-id="6017e-126">Überschreiben Sie im CodeBehind das OnNavigatedTo-Ereignis und das OnNavigatedFrom-Ereignis, und fügen Sie ihnen den folgenden Code hinzu:</span><span class="sxs-lookup"><span data-stu-id="6017e-126">In your code behind, override the OnNavigatedTo and OnNavigatedFrom events and add the following code to them:</span></span> 

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

<span data-ttu-id="6017e-127">Da Benutzer nicht sehr häufig mit Konten interagieren, empfiehlt es sich, den Ereignishandler in der beschriebenen Weise zu registrieren bzw. seine Registrierung aufzuheben, um Arbeitsspeicherverluste zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="6017e-127">Users don't interact with accounts very often, so registering and deregistering your event handler in this fashion helps prevent memory leaks.</span></span> <span data-ttu-id="6017e-128">Dadurch wird der angepasste Bereich nur im Arbeitsspeicher vorgehalten, wenn eine hohe Wahrscheinlichkeit vorliegt, dass er vom Benutzer angefordert wird (der Benutzer befindet sich z. B. auf der Seite „Einstellungen“ oder „Anmelden“).</span><span class="sxs-lookup"><span data-stu-id="6017e-128">This way, your customized pane is only in memory when there's a high chance a user is going to ask for it (because they're on a "settings" or "login" page, for example).</span></span> 

## <a name="build-the-account-settings-pane"></a><span data-ttu-id="6017e-129">Erstellen des Bereichs mit Kontoeinstellungen</span><span class="sxs-lookup"><span data-stu-id="6017e-129">Build the account settings pane</span></span>

<span data-ttu-id="6017e-130">Die BuildPaneAsync-Methode wird immer dann aufgerufen, wenn **AccountsSettingsPane** angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="6017e-130">The BuildPaneAsync method is called whenever the **AccountsSettingsPane** is shown.</span></span> <span data-ttu-id="6017e-131">Dort legen wir den Code zur Anpassung der im Bereich angezeigten Befehle ab.</span><span class="sxs-lookup"><span data-stu-id="6017e-131">This is where we'll put the code to customize the commands shown in the pane.</span></span> 

<span data-ttu-id="6017e-132">Sie beginnen, indem Sie eine Verzögerung abrufen.</span><span class="sxs-lookup"><span data-stu-id="6017e-132">Start by obtaining a deferral.</span></span> <span data-ttu-id="6017e-133">Dadurch wird das System angewiesen, die Anzeige von **AccountsSettingsPane** so lange zu verzögern, bis der Buildvorgang abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="6017e-133">This tells the system to delay showing the **AccountsSettingsPane** until we're finished building it.</span></span>

```csharp
private async void BuildPaneAsync(AccountsSettingsPane s,
    AccountsSettingsPaneCommandsRequestedEventArgs e)
{
    var deferral = e.GetDeferral();
        
    deferral.Complete(); 
}
```

<span data-ttu-id="6017e-134">Als Nächstes rufen Sie einen Anbieter mit der WebAuthenticationCoreManager.FindAccountProviderAsync-Methode ab.</span><span class="sxs-lookup"><span data-stu-id="6017e-134">Next, get a provider using the WebAuthenticationCoreManager.FindAccountProviderAsync method.</span></span> <span data-ttu-id="6017e-135">Die Anbieter-URL ist je nach Anbieter verschieden und kann in der Anbieterdokumentation nachgeschlagen werden.</span><span class="sxs-lookup"><span data-stu-id="6017e-135">The URL for the provider varies based on the provider and can be found in the provider's documentation.</span></span> <span data-ttu-id="6017e-136">Für Microsoft-Konten und Azure Active Directory (Azure AD) lautet sie „https://login.microsoft.com“.</span><span class="sxs-lookup"><span data-stu-id="6017e-136">For Microsoft Accounts and Azure Active Directory, it's "https://login.microsoft.com".</span></span> 

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

<span data-ttu-id="6017e-137">Beachten Sie, dass auch die Zeichenfolge „consumers“ an den optionalen *authority*-Parameter übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="6017e-137">Notice that we also pass the string "consumers" to the optional *authority* parameter.</span></span> <span data-ttu-id="6017e-138">Dies liegt daran, dass Microsoft zwei verschiedene Authentifizierungsmethoden bereitstellt: Microsoft-Konten (MSA) für „Heimanwender“ und Azure Active Directory (AAD) für „Organisationen“.</span><span class="sxs-lookup"><span data-stu-id="6017e-138">This is because Microsoft provides two different types of authentication - Microsoft Accounts (MSA) for "consumers", and Azure Active Directory (AAD) for "organizations".</span></span> <span data-ttu-id="6017e-139">Die Autorität „consumers“ gibt an, dass die MSA-Option verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="6017e-139">The "consumers" authority indicates we want the MSA option.</span></span> <span data-ttu-id="6017e-140">Wenn Sie eine Unternehmens-App entwickeln, verwenden Sie stattdessen die Zeichenfolge „organizations“.</span><span class="sxs-lookup"><span data-stu-id="6017e-140">If you're developing an enterprise app, use the string "organizations" instead.</span></span>

<span data-ttu-id="6017e-141">Schließlich fügen Sie **AccountsSettingsPane** den Anbieter hinzu, indem Sie wie folgt einen neuen **[WebAccountProviderCommand](https://docs.microsoft.com/uwp/api/windows.ui.applicationsettings.webaccountprovidercommand)** erstellen:</span><span class="sxs-lookup"><span data-stu-id="6017e-141">Finally, add the provider to the **AccountsSettingsPane** by creating a new **[WebAccountProviderCommand](https://docs.microsoft.com/uwp/api/windows.ui.applicationsettings.webaccountprovidercommand)** like this:</span></span> 

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

<span data-ttu-id="6017e-142">Die an unseren neuen **WebAccountProviderCommand** übergebene GetMsaToken-Methode ist noch nicht vorhanden (da sie erst im nächsten Schritt erstellt wird). Sie können sie vorläufig als leere Methode hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="6017e-142">The GetMsaToken method we passed to our new **WebAccountProviderCommand** doesn't exist yet (we'll build that in the next step), so feel free to add it as an empty method for now.</span></span>

<span data-ttu-id="6017e-143">Führen Sie den vorangehenden Code aus. Der Bereich sollte jetzt wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="6017e-143">Run the above code and your pane should look something like this:</span></span> 

![Bereich mit Kontoeinstellungen](images/tb-2.png)

### <a name="request-a-token"></a><span data-ttu-id="6017e-145">Anfordern eines Tokens</span><span class="sxs-lookup"><span data-stu-id="6017e-145">Request a token</span></span>

<span data-ttu-id="6017e-146">Sobald die Option für das Microsoft-Konto in **AccountsSettingsPane** angezeigt wird, müssen wir festlegen, was bei der Auswahl der Option durch den Benutzer passiert.</span><span class="sxs-lookup"><span data-stu-id="6017e-146">Once we have the Microsoft Account option displaying in the **AccountsSettingsPane**, we need to handle what happens when the user selects it.</span></span> <span data-ttu-id="6017e-147">Die GetMsaToken-Methode wurde so registriert, dass sie ausgelöst wird, wenn sich der Benutzer für die Anmeldung mit seinem Microsoft-Konto entscheidet. Deshalb fordern wir an dieser Stelle das Token an.</span><span class="sxs-lookup"><span data-stu-id="6017e-147">We registered our GetMsaToken method to fire when the user chooses to log in with their Microsoft Account, so we'll obtain the token there.</span></span> 

<span data-ttu-id="6017e-148">Um ein Token anzufordern, verwenden Sie die RequestTokenAsync-Methode wie folgt:</span><span class="sxs-lookup"><span data-stu-id="6017e-148">To obtain a token, use the RequestTokenAsync method like this:</span></span> 

```csharp
private async void GetMsaTokenAsync(WebAccountProviderCommand command)
{
    WebTokenRequest request = new WebTokenRequest(command.WebAccountProvider, "wl.basic");
    WebTokenRequestResult result = await WebAuthenticationCoreManager.RequestTokenAsync(request);
}
```

<span data-ttu-id="6017e-149">In diesem Beispiel wird die Zeichenfolge „wl.basic“ an den Parameter _scope_ übergeben.</span><span class="sxs-lookup"><span data-stu-id="6017e-149">In this example, we pass the string "wl.basic" to the _scope_ parameter.</span></span> <span data-ttu-id="6017e-150">„scope“ steht für den Typ von Informationen, die Sie vom bereitstellenden Dienst für einen bestimmten Benutzer anfordern.</span><span class="sxs-lookup"><span data-stu-id="6017e-150">Scope represents the type of information you are requesting from the providing service on a specific user.</span></span> <span data-ttu-id="6017e-151">Bestimmte Bereiche ermöglichen nur den Zugriff auf grundlegende Informationen eines Benutzers, z.B. Name und E-Mail-Adresse, während andere Bereiche möglicherweise Zugriff auf vertrauliche Informationen wie die Fotos oder den E-Mail-Posteingang des Benutzers gewähren.</span><span class="sxs-lookup"><span data-stu-id="6017e-151">Certain scopes provide access only to a user's basic information, like name and email address, while other scopes might grant access to sensitive information such as the user's photos or email inbox.</span></span> <span data-ttu-id="6017e-152">Im Allgemeinen sollte Ihre App Berechtigungen in dem Umfang verwenden, der für die Durchführung ihrer Funktion am geringsten erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="6017e-152">Generally, your app should use the least permissive scope necessary to achieve its function.</span></span> <span data-ttu-id="6017e-153">Dienstanbieter stellen in ihrer Dokumentation Informationen dazu bereit, welche Bereiche erforderlich sind, um die für den betreffenden Dienst zu verwendenden Token anzufordern.</span><span class="sxs-lookup"><span data-stu-id="6017e-153">Service providers will provide documentation on which scopes are needed to get tokens for use with their services.</span></span> 

* <span data-ttu-id="6017e-154">Informationen zu Office365- und Outlook.com-Bereichen finden Sie unter [Authentifizieren von Office 365- und Outlook.com-APIs mit dem v2.0-Authentifizierungsendpunkt](https://msdn.microsoft.com/office/office365/howto/authenticate-Office-365-APIs-using-v2).</span><span class="sxs-lookup"><span data-stu-id="6017e-154">For Office 365 and Outlook.com scopes, see [Authenticate Office 365 and Outlook.com APIs using the v2.0 authentication endpoint](https://msdn.microsoft.com/office/office365/howto/authenticate-Office-365-APIs-using-v2).</span></span> 
* <span data-ttu-id="6017e-155">Informationen zu OneDrive-Bereichen finden Sie unter [Authentifizierung und Anmeldung bei OneDrive](https://dev.onedrive.com/auth/msa_oauth.htm#authentication-scopes).</span><span class="sxs-lookup"><span data-stu-id="6017e-155">For OneDrive scopes, see [OneDrive authentication and sign-in](https://dev.onedrive.com/auth/msa_oauth.htm#authentication-scopes).</span></span> 

> [!TIP]
> <span data-ttu-id="6017e-156">Wenn Ihre app Hinweis Anmeldung (für die Benutzerfeld mit einem standardmäßigen e-Mail-Adresse zu füllen) oder andere spezielle Eigenschaft, die im Zusammenhang mit der Oberfläche-Anmeldung verwendet, führen Sie sie optional in der **[WebTokenRequest.AppProperties](https://docs.microsoft.com/uwp/api/windows.security.authentication.web.core.webtokenrequest.appproperties#Windows_Security_Authentication_Web_Core_WebTokenRequest_AppProperties)** -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="6017e-156">Optionally, if your app uses a login hint (to populate the user field with a default email address) or other special property related to the sign-in experience, list it in the **[WebTokenRequest.AppProperties](https://docs.microsoft.com/uwp/api/windows.security.authentication.web.core.webtokenrequest.appproperties#Windows_Security_Authentication_Web_Core_WebTokenRequest_AppProperties)** property.</span></span> <span data-ttu-id="6017e-157">Dadurch wird das System an die Eigenschaft ignoriert werden sollen, die Web-Konto, das Konto Unterschiede im Cache verhindert, dass für die Zwischenspeicherung.</span><span class="sxs-lookup"><span data-stu-id="6017e-157">This will cause the system to ignore the property when caching the web account, which prevents account mismatches in the cache.</span></span>

<span data-ttu-id="6017e-158">Wenn Sie eine Unternehmens-App entwickeln, möchten Sie wahrscheinlich eine Verbindung mit einer Azure Active Directory (AAD)-Instanz herstellen und die Microsoft Graph-API anstelle regulärer MSA-Dienste verwenden.</span><span class="sxs-lookup"><span data-stu-id="6017e-158">If you're developing an enterprise app, you'll likely want to connect to an Azure Active Directory (AAD) instance and use the Microsoft Graph API instead of regular MSA services.</span></span> <span data-ttu-id="6017e-159">Verwenden Sie in diesem Szenario stattdessen folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="6017e-159">In this scenario, use the following code instead:</span></span> 

```csharp
private async void GetAadTokenAsync(WebAccountProviderCommand command)
{
    string clientId = "your_guid_here"; // Obtain your clientId from the Azure Portal
    WebTokenRequest request = new WebTokenRequest(provider, "User.Read", clientId);
    request.Properties.Add("resource", "https://graph.microsoft.com");
    WebTokenRequestResult result = await WebAuthenticationCoreManager.RequestTokenAsync(request);
}
```

<span data-ttu-id="6017e-160">Im weiteren Verlauf dieses Artikels wird das MSA-Szenario beschrieben, der Code für AAD ist allerdings sehr ähnlich.</span><span class="sxs-lookup"><span data-stu-id="6017e-160">The rest of this article continues describing the MSA scenario, but the code for AAD is very similar.</span></span> <span data-ttu-id="6017e-161">Weitere Informationen zu AAD/Graph einschließlich eines vollständigen Beispiels auf GitHub finden Sie in der [Microsoft Graph-Dokumentation](https://graph.microsoft.io/docs/platform/get-started).</span><span class="sxs-lookup"><span data-stu-id="6017e-161">For more info on AAD/Graph, including a full sample on GitHub, see the [Microsoft Graph documentation](https://graph.microsoft.io/docs/platform/get-started).</span></span>

## <a name="use-the-token"></a><span data-ttu-id="6017e-162">Verwenden des Tokens</span><span class="sxs-lookup"><span data-stu-id="6017e-162">Use the token</span></span>

<span data-ttu-id="6017e-163">Die RequestTokenAsync-Methode gibt ein WebTokenRequestResult-Objekt zurück, das die Ergebnisse für Ihre Anforderung enthält.</span><span class="sxs-lookup"><span data-stu-id="6017e-163">The RequestTokenAsync method returns a WebTokenRequestResult object, which contains the results of your request.</span></span> <span data-ttu-id="6017e-164">Wenn die Anforderung erfolgreich war, enthält sie ein Token.</span><span class="sxs-lookup"><span data-stu-id="6017e-164">If your request was successful, it will contain a token.</span></span>  

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
> <span data-ttu-id="6017e-165">Wenn Sie eine Fehlermeldung erhalten, wenn ein Token angefordert haben, stellen Sie sicher, dass Sie Ihre App im Store wie in Schritt 1 beschrieben zugeordnet haben.</span><span class="sxs-lookup"><span data-stu-id="6017e-165">If you receive an error when requesting a token, make sure you've associated your app with the Store as described in step one.</span></span> <span data-ttu-id="6017e-166">Ihre App wird nicht in der Lage sein, ein Token abzurufen, wenn Sie diesen Schritt übersprungen haben.</span><span class="sxs-lookup"><span data-stu-id="6017e-166">Your app won't be able to get a token if you skipped this step.</span></span> 

<span data-ttu-id="6017e-167">Sobald Sie im Besitz des Tokens sind, können Sie darüber die API Ihres Anbieters aufrufen.</span><span class="sxs-lookup"><span data-stu-id="6017e-167">Once you have a token, you can use it to call your provider's API.</span></span> <span data-ttu-id="6017e-168">Im folgenden Code wird die [Microsoft Live-API für Benutzerinformationen](https://msdn.microsoft.com/library/hh826533.aspx) aufgerufen, um grundlegende Informationen zum Benutzer zu erhalten und sie auf der Benutzeroberfläche anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="6017e-168">In the code below, we'll call the [user info Microsoft Live API](https://msdn.microsoft.com/library/hh826533.aspx) to obtain basic information about the user and display it in our UI.</span></span> <span data-ttu-id="6017e-169">Beachten Sie jedoch, dass in den meisten Fällen empfohlen wird, die einmal erhaltenen Tokens zu speichern und sie dann in einer separaten Methode zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="6017e-169">Note however that in most cases it is recommended that you store the token once obtained and then use it in a separate method.</span></span>

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

<span data-ttu-id="6017e-170">Die Methode zum Aufrufen verschiedener REST-APIs ist je nach Anbieter verschieden. Informationen zur Verwendung des Tokens finden Sie in der API-Dokumentation des Anbieters.</span><span class="sxs-lookup"><span data-stu-id="6017e-170">How you call various REST APIs varies between providers; see the provider's API documentation for information on how to use your token.</span></span> 

## <a name="store-the-account-for-future-use"></a><span data-ttu-id="6017e-171">Speichern des Kontos für zukünftige Verwendung</span><span class="sxs-lookup"><span data-stu-id="6017e-171">Store the account for future use</span></span>

<span data-ttu-id="6017e-172">Token sind hilfreich, um sofort Informationen über einen Benutzer abzurufen, in der Regel haben sie jedoch unterschiedliche Ablaufzeiten. MSA-Token sind beispielsweise nur wenige Stunden gültig.</span><span class="sxs-lookup"><span data-stu-id="6017e-172">Tokens are useful for immediately obtaining information about a user, but they usually have varying lifespans - MSA tokens, for instance, are only valid for a few hours.</span></span> <span data-ttu-id="6017e-173">Sie müssen **AccountsSettingsPane** jedoch nicht jedes Mal erneut anzeigen, wenn ein Token abläuft.</span><span class="sxs-lookup"><span data-stu-id="6017e-173">Fortunately, you don't need to re-show the **AccountsSettingsPane** each time a token expires.</span></span> <span data-ttu-id="6017e-174">Nachdem Ihre App einmal von einem Benutzer autorisiert wurde, können Sie die Kontoinformationen des Benutzers für die zukünftige Verwendung speichern.</span><span class="sxs-lookup"><span data-stu-id="6017e-174">Once a user has authorized your app once, you can store the user's account information for future use.</span></span> 

<span data-ttu-id="6017e-175">Zu diesem Zweck verwenden Sie die **[WebAccount](https://docs.microsoft.com/uwp/api/windows.security.credentials.webaccount)**-Klasse.</span><span class="sxs-lookup"><span data-stu-id="6017e-175">To do this, use the **[WebAccount](https://docs.microsoft.com/uwp/api/windows.security.credentials.webaccount)** class.</span></span> <span data-ttu-id="6017e-176">Ein **WebAccount** wird von derselben Methode zurückgegeben, die Sie verwendet haben, um das Token anzufordern:</span><span class="sxs-lookup"><span data-stu-id="6017e-176">A **WebAccount** is returned by the same method you used to request the token:</span></span>

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

<span data-ttu-id="6017e-177">Sobald Sie über eine **WebAccount**-Instanz verfügen, können Sie es ganz einfach speichern.</span><span class="sxs-lookup"><span data-stu-id="6017e-177">Once you have a **WebAccount** instance, you can easily store it.</span></span> <span data-ttu-id="6017e-178">Im folgenden Beispiel verwenden wir LocalSettings.</span><span class="sxs-lookup"><span data-stu-id="6017e-178">In the following example, we use LocalSettings.</span></span> <span data-ttu-id="6017e-179">Weitere Informationen zur Verwendung von LocalSettings und anderen Methoden zum Speichern von Benutzerdaten finden Sie unter [Speichern und Abrufen von App-Einstellungen und -Daten](https://docs.microsoft.com/windows/uwp/app-settings/store-and-retrieve-app-data).</span><span class="sxs-lookup"><span data-stu-id="6017e-179">For more information on using LocalSettings and other methods to store user data, see [Store and retrieve app settings and data](https://docs.microsoft.com/windows/uwp/app-settings/store-and-retrieve-app-data).</span></span>

```csharp
private async void StoreWebAccount(WebAccount account)
{
    ApplicationData.Current.LocalSettings.Values["CurrentUserProviderId"] = account.WebAccountProvider.Id;
    ApplicationData.Current.LocalSettings.Values["CurrentUserId"] = account.Id; 
}
```

<span data-ttu-id="6017e-180">Anschließend können wir eine asynchrone Methode wie die folgende verwenden, um zu versuchen, ein Token im Hintergrund mit dem gespeicherten **WebAccount** abzurufen.</span><span class="sxs-lookup"><span data-stu-id="6017e-180">Then, we can use an asynchronous method like the following to attempt to obtain a token in the background with the stored **WebAccount**.</span></span>

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

<span data-ttu-id="6017e-181">Platzieren Sie die oben beschriebene Methode unmittelbar vor den Code, der **AccountsSettingsPane** aufbaut.</span><span class="sxs-lookup"><span data-stu-id="6017e-181">Place the above method just before the code that builds the **AccountsSettingsPane**.</span></span> <span data-ttu-id="6017e-182">Wenn das Token im Hintergrund abgerufen wird, muss der Bereich nicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="6017e-182">If the token is obtained in the background, there is no need to show the pane.</span></span> 

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

<span data-ttu-id="6017e-183">Da der Tokenabruf im Hintergrund sehr einfach ist, sollten Sie diese Methode verwenden, um Ihr Token zwischen Sitzungen zu aktualisieren, anstatt ein vorhandenes Token zwischenzuspeichern (da das Token jederzeit ablaufen kann).</span><span class="sxs-lookup"><span data-stu-id="6017e-183">Because obtaining a token silently is very simple, you should use this process to refresh your token between sessions rather than caching an existing token (since that token might expire at any time).</span></span>

> [!NOTE]
> <span data-ttu-id="6017e-184">Im vorangehenden Beispiel sind nur einfache Erfolgs- und Fehlerereignisse dargestellt.</span><span class="sxs-lookup"><span data-stu-id="6017e-184">The example above only covers basic success and fail cases.</span></span> <span data-ttu-id="6017e-185">Ihre App sollte auch außergewöhnliche Szenarien berücksichtigen (z. B. wenn ein Benutzer die Berechtigung für die App widerruft oder das Konto aus Windows entfernt) und sie angemessen behandeln.</span><span class="sxs-lookup"><span data-stu-id="6017e-185">Your app should also account for unusual scenarios (like a user revoking your app's permission or removing their account from Windows, for example) and handle them gracefully.</span></span>  

## <a name="remove-a-stored-account"></a><span data-ttu-id="6017e-186">Entfernen eines gespeicherten Kontos</span><span class="sxs-lookup"><span data-stu-id="6017e-186">Remove a stored account</span></span>

<span data-ttu-id="6017e-187">Wenn Sie ein Webkonto beibehalten, sollten Sie Benutzern die Möglichkeit geben, ihr Konto von Ihrer App zu trennen.</span><span class="sxs-lookup"><span data-stu-id="6017e-187">If you persist a web account, you may want to give your users the ability to disassociate their account with your app.</span></span> <span data-ttu-id="6017e-188">Auf diese Weise sie können effektiv "Abmelden" der app: ihre Kontoinformationen werden nach dem Start nicht mehr automatisch geladen.</span><span class="sxs-lookup"><span data-stu-id="6017e-188">This way, they can effectively "log out" of the app: their account information will no longer be loaded automatically upon launch.</span></span> <span data-ttu-id="6017e-189">Entfernen Sie dafür zuerst alle gespeicherten Konto- und Anbieterinformationen aus dem Speicher.</span><span class="sxs-lookup"><span data-stu-id="6017e-189">To do this, first remove any saved account and provider information from storage.</span></span> <span data-ttu-id="6017e-190">Rufen Sie dann **[SignOutAsync](https://docs.microsoft.com/uwp/api/windows.security.credentials.webaccount.SignOutAsync)** auf, um den Cache zu löschen und vorhandene App-Tokens für ungültig zu erklären.</span><span class="sxs-lookup"><span data-stu-id="6017e-190">Then call **[SignOutAsync](https://docs.microsoft.com/uwp/api/windows.security.credentials.webaccount.SignOutAsync)** to clear the cache and invalidate any existing tokens your app may have.</span></span> 

```csharp
private async Task SignOutAccountAsync(WebAccount account)
{
    ApplicationData.Current.LocalSettings.Values.Remove("CurrentUserProviderId");
    ApplicationData.Current.LocalSettings.Values.Remove("CurrentUserId"); 
    account.SignOutAsync(); 
}
```

## <a name="add-providers-that-dont-support-webaccountmanager"></a><span data-ttu-id="6017e-191">Hinzufügen von Anbietern, die WebAccountManager nicht unterstützen</span><span class="sxs-lookup"><span data-stu-id="6017e-191">Add providers that don't support WebAccountManager</span></span>

<span data-ttu-id="6017e-192">Wenn Sie die Authentifizierung über einen Dienst in Ihre App integrieren möchten, der Dienst WebAccountManager jedoch nicht unterstützt (z. B. Google+ oder Twitter), können Sie **AccountsSettingsPane** den Anbieter trotzdem manuell hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="6017e-192">If you want to integrate authentication from a service into your app but that service doesn't support WebAccountManager - Google+ or Twitter, for example - you can still manually add that provider to the **AccountsSettingsPane**.</span></span> <span data-ttu-id="6017e-193">Erstellen Sie dazu ein neues WebAccountProvider-Objekt unter Angabe Ihres eigenen Namens und PNG-Symbols. Fügen Sie das Objekt dann zur WebAccountProviderCommands-Liste hinzu.</span><span class="sxs-lookup"><span data-stu-id="6017e-193">To do so, create a new WebAccountProvider object and provide your own name and .png icon, then and add it to the WebAccountProviderCommands list.</span></span> <span data-ttu-id="6017e-194">Stubcode-Beispiel:</span><span class="sxs-lookup"><span data-stu-id="6017e-194">Here's some stub code:</span></span> 

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
> <span data-ttu-id="6017e-195">Dadurch wird **AccountsSettingsPane** lediglich ein Symbol hinzugefügt und die Methode ausgeführt, die beim Klicken auf das Symbol ausgeführt werden soll (in diesem Fall GetTwitterTokenAsync).</span><span class="sxs-lookup"><span data-stu-id="6017e-195">This only adds an icon to the **AccountsSettingsPane** and runs the method you specify when the icon is clicked (GetTwitterTokenAsync, in this case).</span></span> <span data-ttu-id="6017e-196">Sie müssen den Code angeben, durch den die eigentliche Authentifizierung behandelt wird.</span><span class="sxs-lookup"><span data-stu-id="6017e-196">You must provide the code that handles the actual authentication.</span></span> <span data-ttu-id="6017e-197">Weitere Informationen finden Sie unter (Webauthentifizierungsbroker)[web-authentication-broker], der Hilfsmethoden für die Authentifizierung mithilfe von REST-Diensten bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="6017e-197">For more information, see (Web authentication broker)[web-authentication-broker], which provides helper methods for authenticating using REST services.</span></span> 

## <a name="add-a-custom-header"></a><span data-ttu-id="6017e-198">Hinzufügen eines benutzerdefinierten Headers</span><span class="sxs-lookup"><span data-stu-id="6017e-198">Add a custom header</span></span>

<span data-ttu-id="6017e-199">Sie können den Bereich mit den Kontoeinstellungen mithilfe der HeaderText-Eigenschaft wie folgt anpassen:</span><span class="sxs-lookup"><span data-stu-id="6017e-199">You can customize the account settings pane using the HeaderText property, like this:</span></span> 

```csharp
private async void BuildPaneAsync(AccountsSettingsPane s, AccountsSettingsPaneCommandsRequestedEventArgs e)
{
    // other code here 
    
    args.HeaderText = "MyAwesomeApp works best if you're signed in.";   
    
    // other code here
}
```

![Bereich mit Kontoeinstellungen](images/tb-3.png)

<span data-ttu-id="6017e-201">Halten Sie Headertext kurz und einfach, und vermeiden Sie überflüssige Informationen.</span><span class="sxs-lookup"><span data-stu-id="6017e-201">Don't go overboard with header text; keep it short and sweet.</span></span> <span data-ttu-id="6017e-202">Wenn der Anmeldevorgang komplex ist und weitere Informationen angezeigt werden müssen, verknüpfen Sie den Benutzer über einen benutzerdefinierten Link mit einer separaten Seite.</span><span class="sxs-lookup"><span data-stu-id="6017e-202">If your login process is complicated and you need to display more information, link the user to a separate page using a custom link.</span></span> 

## <a name="add-custom-links"></a><span data-ttu-id="6017e-203">Hinzufügen von benutzerdefinierten Links</span><span class="sxs-lookup"><span data-stu-id="6017e-203">Add custom links</span></span>

<span data-ttu-id="6017e-204">Sie können dem AccountsSettingsPane benutzerdefinierte Befehle hinzufügen, die als Links unter den unterstützten WebAccountProviders angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="6017e-204">You can add custom commands to the AccountsSettingsPane, which appear as links below your supported WebAccountProviders.</span></span> <span data-ttu-id="6017e-205">Benutzerdefinierte Befehle eignen sich hervorragend für einfache Aufgaben in Verbindung mit Benutzerkonten, z. B. das Anzeigen einer Datenschutzrichtlinie oder das Öffnen einer Supportseite, wenn auf Benutzerseite ein Problem auftritt.</span><span class="sxs-lookup"><span data-stu-id="6017e-205">Custom commands are great for simple tasks related to user accounts, like displaying a privacy policy or launching a support page for users having trouble.</span></span> 

<span data-ttu-id="6017e-206">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="6017e-206">Here's an example:</span></span> 

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

<span data-ttu-id="6017e-208">Einstellungsbefehle lassen sich grundsätzlich überall verwenden.</span><span class="sxs-lookup"><span data-stu-id="6017e-208">Theoretically, you can use settings commands for anything.</span></span> <span data-ttu-id="6017e-209">Es wird jedoch empfohlen, diese Art Befehle auf die oben beschriebenen intuitiven Kontoszenarien zu beschränken.</span><span class="sxs-lookup"><span data-stu-id="6017e-209">However, we suggest limiting their use to intuitive, account-related scenarios like those described above.</span></span> 

## <a name="see-also"></a><span data-ttu-id="6017e-210">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="6017e-210">See also</span></span>

[<span data-ttu-id="6017e-211">Windows.Security.Authentication.Web.Core-Namespace</span><span class="sxs-lookup"><span data-stu-id="6017e-211">Windows.Security.Authentication.Web.Core namespace</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.authentication.web.core.aspx)

[<span data-ttu-id="6017e-212">Windows.Security.Credentials-Namespace</span><span class="sxs-lookup"><span data-stu-id="6017e-212">Windows.Security.Credentials namespace</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.credentials.aspx)

[<span data-ttu-id="6017e-213">AccountsSettingsPane-Klasse</span><span class="sxs-lookup"><span data-stu-id="6017e-213">AccountsSettingsPane class</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.ui.applicationsettings.accountssettingspane)

[<span data-ttu-id="6017e-214">Webauthentifizierungsbroker</span><span class="sxs-lookup"><span data-stu-id="6017e-214">Web authentication broker</span></span>](web-authentication-broker.md)

[<span data-ttu-id="6017e-215">Beispiel für die Webkontoverwaltung</span><span class="sxs-lookup"><span data-stu-id="6017e-215">Web account management sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=620621)

[<span data-ttu-id="6017e-216">Lunch Scheduler-App</span><span class="sxs-lookup"><span data-stu-id="6017e-216">Lunch Scheduler app</span></span>](https://github.com/Microsoft/Windows-appsample-lunch-scheduler)
