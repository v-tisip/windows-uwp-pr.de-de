---
author: TylerMSFT
title: Behandeln der URI-Aktivierung
description: Erfahren Sie, wie Sie eine App registrieren, damit sie der Standardhandler eines Uniform Resource Identifier (URI)-Schemanamens wird.
ms.assetid: 92D06F3E-C8F3-42E0-A476-7E94FD14B2BE
ms.author: twhitney
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 40c70770028853d5912ef63f84259245252ce881
ms.sourcegitcommit: 7f03e200ef34f7f24b6f8b6489ecb44aa2b870bc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2017
---
# <a name="handle-uri-activation"></a><span data-ttu-id="98c46-104">Behandeln der URI-Aktivierung</span><span class="sxs-lookup"><span data-stu-id="98c46-104">Handle URI activation</span></span>


<span data-ttu-id="98c46-105">\[ Aktualisiert für UWP-Apps unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="98c46-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="98c46-106">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span><span class="sxs-lookup"><span data-stu-id="98c46-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>


**<span data-ttu-id="98c46-107">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="98c46-107">Important APIs</span></span>**

-   [**<span data-ttu-id="98c46-108">Windows.ApplicationModel.Activation.ProtocolActivatedEventArgs</span><span class="sxs-lookup"><span data-stu-id="98c46-108">Windows.ApplicationModel.Activation.ProtocolActivatedEventArgs</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224742)
-   [**<span data-ttu-id="98c46-109">Windows.UI.Xaml.Application.OnActivated</span><span class="sxs-lookup"><span data-stu-id="98c46-109">Windows.UI.Xaml.Application.OnActivated</span></span>**](https://msdn.microsoft.com/library/windows/apps/br242330)

<span data-ttu-id="98c46-110">Erfahren Sie, wie Sie eine App registrieren müssen, damit sie der Standardhandler eines URI-Schemanamens (Uniform Resource Identifier) wird.</span><span class="sxs-lookup"><span data-stu-id="98c46-110">Learn how to register an app to become the default handler for a Uniform Resource Identifier (URI) scheme name.</span></span> <span data-ttu-id="98c46-111">Windows-Desktop-Apps und UWP (Universelle Windows-Plattform)-Apps können als Standarddateihandler für URI-Schemanamen registriert werden.</span><span class="sxs-lookup"><span data-stu-id="98c46-111">Both Windows desktop apps and Universal Windows Platform (UWP) apps can register to be a default handler for a URI scheme name.</span></span> <span data-ttu-id="98c46-112">Wenn Ihre App vom Benutzer als Standardhandler für einen URI-Schemanamen ausgewählt wird, wird sie immer dann aktiviert, wenn dieser URI-Typ gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="98c46-112">If the user chooses your app as the default handler for a URI scheme name, your app will be activated every time that type of URI is launched.</span></span>

<span data-ttu-id="98c46-113">Wir empfehlen, die Registrierung für einen URI-Schemanamen nur durchzuführen, wenn davon auszugehen ist, dass Sie alle entsprechenden Vorgänge für diesen URI-Schematyp behandeln werden.</span><span class="sxs-lookup"><span data-stu-id="98c46-113">We recommend that you only register for a URI scheme name if you expect to handle all URI launches for that type of URI scheme.</span></span> <span data-ttu-id="98c46-114">Wenn Sie sich entscheiden, die Registrierung für einen bestimmten URI-Schemanamen durchzuführen, müssen Sie die entsprechenden Funktionen bereitstellen, die vom Benutzer bei der Aktivierung für dieses URI-Schemas erwartet werden.</span><span class="sxs-lookup"><span data-stu-id="98c46-114">If you do choose to register for a URI scheme name, you must provide the end user with the functionality that is expected when your app is activated for that URI scheme.</span></span> <span data-ttu-id="98c46-115">Beispielsweise sollte eine App, die für den URI-Schemanamen "mailto:" registriert wird, eine neue E-Mail-Nachricht öffnen, damit Benutzer eine neue E-Mail erstellen können.</span><span class="sxs-lookup"><span data-stu-id="98c46-115">For example, an app that registers for the mailto: URI scheme name should open to a new e-mail message so that the user can compose a new e-mail.</span></span> <span data-ttu-id="98c46-116">Weitere Informationen zu URI-Zuordnungen finden Sie unter [Richtlinien und Prüflisten für Dateitypen und URIs](https://msdn.microsoft.com/library/windows/apps/hh700321).</span><span class="sxs-lookup"><span data-stu-id="98c46-116">For more info on URI associations, see [Guidelines and checklist for file types and URIs](https://msdn.microsoft.com/library/windows/apps/hh700321).</span></span>

<span data-ttu-id="98c46-117">Die folgenden Schritte zeigen, wie Sie den benutzerdefinierten Schemanamen „.alsdk://“ registrieren und Ihre App aktivieren, wenn der Benutzer einen URI vom Typ „.alsdk://“ startet.</span><span class="sxs-lookup"><span data-stu-id="98c46-117">These steps show how to register for a custom URI scheme name, alsdk://, and how to activate your app when the user launches a alsdk:// URI.</span></span>

> <span data-ttu-id="98c46-118">**Hinweis**  In UWP-Apps sind bestimmte URIs und Dateierweiterungen für die Verwendung durch vorinstallierte Apps und das Betriebssystem reserviert.</span><span class="sxs-lookup"><span data-stu-id="98c46-118">**Note**  In UWP apps, certain URIs and file extensions are reserved for use by built-in apps and the operating system.</span></span> <span data-ttu-id="98c46-119">Versuche, die App mit einem reservierten URI oder einer reservierten Dateierweiterung zu registrieren, werden ignoriert.</span><span class="sxs-lookup"><span data-stu-id="98c46-119">Attempts to register your app with a reserved URI or file extension will be ignored.</span></span> <span data-ttu-id="98c46-120">Eine alphabetische Liste der URI-Schemas, die Sie nicht für Ihre UWP-Apps registrieren können, da diese entweder reserviert oder verboten sind, finden Sie unter [Reservierte URI-Schemanamen und Dateitypen](reserved-uri-scheme-names.md).</span><span class="sxs-lookup"><span data-stu-id="98c46-120">See [Reserved URI scheme names and file types](reserved-uri-scheme-names.md) for an alphabetic list of Uri schemes that you can't register for your UWP apps because they are either reserved or forbidden.</span></span>

## <a name="step-1-specify-the-extension-point-in-the-package-manifest"></a><span data-ttu-id="98c46-121">Schritt 1: Angeben des Erweiterungspunkts im Paketmanifest</span><span class="sxs-lookup"><span data-stu-id="98c46-121">Step 1: Specify the extension point in the package manifest</span></span>


<span data-ttu-id="98c46-122">Die App empfängt nur für die im Paketmanifest angegebenen URI-Schemanamen Aktivierungsereignisse.</span><span class="sxs-lookup"><span data-stu-id="98c46-122">The app receives activation events only for the URI scheme names listed in the package manifest.</span></span> <span data-ttu-id="98c46-123">Im Folgenden wird beschrieben, wie Sie festlegen, dass die App den URI-Schemanamen `alsdk` behandelt.</span><span class="sxs-lookup"><span data-stu-id="98c46-123">Here's how you indicate that your app handles the `alsdk`URI scheme name.</span></span>

1.  <span data-ttu-id="98c46-124">Doppelklicken Sie im **Projektmappen-Explorer** auf „package.appxmanifest“, um den Manifest-Designer zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="98c46-124">In the **Solution Explorer**, double-click package.appxmanifest to open the manifest designer.</span></span> <span data-ttu-id="98c46-125">Wählen Sie die Registerkarte **Deklarationen** und in der Dropdownliste **Verfügbare Deklarationen** die Option **Protokoll** aus, und klicken Sie dann auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="98c46-125">Select the **Declarations** tab and in the **Available Declarations** drop-down, select **Protocol** and then click **Add**.</span></span>

    <span data-ttu-id="98c46-126">Es folgt eine kurze Beschreibung der einzelnen Felder, die Sie im Manifest-Designer für das Protokoll ausfüllen können (Einzelheiten finden Sie unter [**AppX Package Manifest**](https://msdn.microsoft.com/library/windows/apps/dn934791)):</span><span class="sxs-lookup"><span data-stu-id="98c46-126">Here is a brief description of each of the fields that you may fill in the manifest designer for the Protocol (see [**AppX Package Manifest**](https://msdn.microsoft.com/library/windows/apps/dn934791) for details):</span></span>

| <span data-ttu-id="98c46-127">Feld</span><span class="sxs-lookup"><span data-stu-id="98c46-127">Field</span></span> | <span data-ttu-id="98c46-128">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="98c46-128">Description</span></span> |
|-------|-------------|
| **<span data-ttu-id="98c46-129">Logo</span><span class="sxs-lookup"><span data-stu-id="98c46-129">Logo</span></span>** | <span data-ttu-id="98c46-130">Geben Sie das Logo zur Identifikation des URI-Schemanamens in der **Systemsteuerung** unter [Standardprogramme festlegen](https://msdn.microsoft.com/library/windows/desktop/cc144154) an.</span><span class="sxs-lookup"><span data-stu-id="98c46-130">Specify the logo that is used to identify the URI scheme name in the [Set Default Programs](https://msdn.microsoft.com/library/windows/desktop/cc144154) on the **Control Panel**.</span></span> <span data-ttu-id="98c46-131">Wenn kein Logo angegeben wird, wird das kleine Logo für die App verwendet.</span><span class="sxs-lookup"><span data-stu-id="98c46-131">If no Logo is specified, the small logo for the app is used.</span></span> |
| **<span data-ttu-id="98c46-132">Anzeigename</span><span class="sxs-lookup"><span data-stu-id="98c46-132">Display Name</span></span>** | <span data-ttu-id="98c46-133">Geben Sie den Anzeigenamen zur Identifikation des URI-Schemanamens in der **Systemsteuerung** unter [Standardprogramme festlegen](https://msdn.microsoft.com/library/windows/desktop/cc144154) an.</span><span class="sxs-lookup"><span data-stu-id="98c46-133">Specify the display name to identify the URI scheme name in the [Set Default Programs](https://msdn.microsoft.com/library/windows/desktop/cc144154) on the **Control Panel**.</span></span> |
| **<span data-ttu-id="98c46-134">Name</span><span class="sxs-lookup"><span data-stu-id="98c46-134">Name</span></span>** | <span data-ttu-id="98c46-135">Wählen Sie einen Namen für das URI-Schema aus.</span><span class="sxs-lookup"><span data-stu-id="98c46-135">Choose a name for the Uri scheme.</span></span> |
|  | <span data-ttu-id="98c46-136">**Hinweis**  Der Name darf nur aus Kleinbuchstaben bestehen.</span><span class="sxs-lookup"><span data-stu-id="98c46-136">**Note**  The Name must be in all lower case letters.</span></span> |
|  | <span data-ttu-id="98c46-137">**Reservierte und verbotene Dateitypen** Eine alphabetische Liste der URI-Schemas, die Sie nicht für Ihre UWP-Apps registrieren können, da diese entweder reserviert oder verboten sind, finden Sie unter [Reservierte URI-Schemanamen und Dateitypen](reserved-uri-scheme-names.md).</span><span class="sxs-lookup"><span data-stu-id="98c46-137">**Reserved and forbidden file types** See [Reserved URI scheme names and file types](reserved-uri-scheme-names.md) for an alphabetic list of Uri schemes that you can't register for your UWP apps because they are either reserved or forbidden.</span></span> |
| **<span data-ttu-id="98c46-138">Ausführbare Datei</span><span class="sxs-lookup"><span data-stu-id="98c46-138">Executable</span></span>** | <span data-ttu-id="98c46-139">Gibt die standardmäßige ausführbare Datei für den Start des Protokolls an.</span><span class="sxs-lookup"><span data-stu-id="98c46-139">Specifies the default launch executable for the protocol.</span></span> <span data-ttu-id="98c46-140">Wenn keine Datei angegeben wird, wird die ausführbare Datei der App verwendet.</span><span class="sxs-lookup"><span data-stu-id="98c46-140">If not specified, the app's executable is used.</span></span> <span data-ttu-id="98c46-141">Wenn angegeben, muss die Zeichenfolge zwischen 1 und 256 Zeichen lang sein und mit „.exe“ enden. Sie darf die folgenden Zeichen nicht enthalten: &gt;, &lt;, :, ", &#124;, ? oder \*.</span><span class="sxs-lookup"><span data-stu-id="98c46-141">If specified, the string must be between 1 and 256 characters in length, must end with ".exe", and cannot contain these characters: &gt;, &lt;, :, ", &#124;, ?, or \*.</span></span> <span data-ttu-id="98c46-142">Bei Angabe einer Datei wird auch der **Einstiegspunkt** verwendet.</span><span class="sxs-lookup"><span data-stu-id="98c46-142">If specified, the **Entry point** is also used.</span></span> <span data-ttu-id="98c46-143">Wenn der **Einstiegspunkt** nicht angegeben wird, wird der für die App definierte Einstiegspunkt verwendet.</span><span class="sxs-lookup"><span data-stu-id="98c46-143">If the **Entry point** isn't specified, the entry point defined for the app is used.</span></span> |
| **<span data-ttu-id="98c46-144">Einstiegspunkt</span><span class="sxs-lookup"><span data-stu-id="98c46-144">Entry point</span></span>** | <span data-ttu-id="98c46-145">Gibt die Aufgabe an, die die Protokollerweiterung behandelt.</span><span class="sxs-lookup"><span data-stu-id="98c46-145">Specifies the task that handles the protocol extension.</span></span> <span data-ttu-id="98c46-146">Dies ist normalerweise der vollständig qualifizierte Namespacename eines Windows-Runtime-Typs.</span><span class="sxs-lookup"><span data-stu-id="98c46-146">This is normally the fully namespace-qualified name of a Windows Runtime type.</span></span> <span data-ttu-id="98c46-147">Wenn keine Angabe erfolgt, wird der Einstiegspunkt für die App verwendet.</span><span class="sxs-lookup"><span data-stu-id="98c46-147">If not specified, the entry point for the app is used.</span></span> |
| **<span data-ttu-id="98c46-148">Startseite</span><span class="sxs-lookup"><span data-stu-id="98c46-148">Start page</span></span>** | <span data-ttu-id="98c46-149">Die Webseite, die den Erweiterungspunkt behandelt.</span><span class="sxs-lookup"><span data-stu-id="98c46-149">The web page that handles the extensibility point.</span></span> |
| **<span data-ttu-id="98c46-150">Ressourcengruppe</span><span class="sxs-lookup"><span data-stu-id="98c46-150">Resource group</span></span>** | <span data-ttu-id="98c46-151">Eine Markierung, die Sie zum Gruppieren von Erweiterungsaktivierungen zu Zwecken der Ressourcenverwaltung verwenden können.</span><span class="sxs-lookup"><span data-stu-id="98c46-151">A tag that you can use to group extension activations together for resource management purposes.</span></span> |
| <span data-ttu-id="98c46-152">**Gewünschte Ansicht** (nur Windows)</span><span class="sxs-lookup"><span data-stu-id="98c46-152">**Desired View** (Windows-only)</span></span> | <span data-ttu-id="98c46-153">Verwenden Sie das Feld **Gewünschte Ansicht**, um anzugeben, wie viel Platz für das Fenster der App benötigt wird, wenn sie für den URI-Schemanamen gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="98c46-153">Specify the **Desired View** field to indicate the amount of space the app's window needs when it is launched for the URI scheme name.</span></span> <span data-ttu-id="98c46-154">Die möglichen Werte für **Gewünschte Ansicht** sind **Default**, **UseLess**, **UseHalf**, **UseMore** oder **UseMinimum**.</span><span class="sxs-lookup"><span data-stu-id="98c46-154">The possible values for **Desired View** are **Default**, **UseLess**, **UseHalf**, **UseMore**, or **UseMinimum**.</span></span> <br/><span data-ttu-id="98c46-155">**Hinweis**  Windows bestimmt die endgültige Fenstergröße einer Ziel-App anhand mehrerer Faktoren, z.B. der Einstellung der Quell-App, der Anzahl der Apps auf dem Bildschirm, der Bildschirmausrichtung usw.</span><span class="sxs-lookup"><span data-stu-id="98c46-155">**Note**  Windows takes into account multiple different factors when determining the target app's final window size, for example, the preference of the source app, the number of apps on screen, the screen orientation, and so on.</span></span> <span data-ttu-id="98c46-156">Das Festlegen von **Gewünschte Ansicht** ist keine Garantie, dass das Fenster für die Ziel-App auch wirklich so angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="98c46-156">Setting **Desired View** doesn't guarantee a specific windowing behavior for the target app.</span></span><br/> <span data-ttu-id="98c46-157">**Mobilgerätfamilie: Gewünschte Ansicht** wird für die Mobilgerätfamilie nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="98c46-157">**Mobile device family:  Desired View** isn't supported on the mobile device family.</span></span> |
2.  <span data-ttu-id="98c46-158">Geben Sie `images\Icon.png` als **Logo** ein.</span><span class="sxs-lookup"><span data-stu-id="98c46-158">Enter `images\Icon.png` as the **Logo**.</span></span>
3.  <span data-ttu-id="98c46-159">Geben Sie `SDK Sample URI Scheme` als **Anzeigenamen** ein.</span><span class="sxs-lookup"><span data-stu-id="98c46-159">Enter `SDK Sample URI Scheme` as the **Display name**</span></span>
4.  <span data-ttu-id="98c46-160">Geben Sie `alsdk` in das Feld **Name** ein.</span><span class="sxs-lookup"><span data-stu-id="98c46-160">Enter `alsdk` as the **Name**.</span></span>
5.  <span data-ttu-id="98c46-161">Drücken Sie STRG+S, um die an „package.appxmanifest“ vorgenommenen Änderungen zu speichern.</span><span class="sxs-lookup"><span data-stu-id="98c46-161">Press Ctrl+S to save the change to package.appxmanifest.</span></span>

    <span data-ttu-id="98c46-162">Dadurch wird dem Paketmanifest ein [**Extension**](https://msdn.microsoft.com/library/windows/apps/br211400)-Element wie das unten dargestellte hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="98c46-162">This adds an [**Extension**](https://msdn.microsoft.com/library/windows/apps/br211400) element like this one to the package manifest.</span></span> <span data-ttu-id="98c46-163">Die **windows.protocol**-Kategorie gibt an, dass die App den URI-Schemanamen `alsdk` behandelt.</span><span class="sxs-lookup"><span data-stu-id="98c46-163">The **windows.protocol** category indicates that the app handles the `alsdk` URI scheme name.</span></span>

    ```xml
          <Extensions>
            <uap:Extension Category="windows.protocol">
              <uap:Protocol Name="alsdk">
                <uap:Logo>images\icon.png</uap:Logo>
                <uap:DisplayName>SDK Sample URI Scheme</uap:DisplayName>
              </uap:Protocol>
            </uap:Extension>
          </Extensions>
    ```

## <a name="step-2-add-the-proper-icons"></a><span data-ttu-id="98c46-164">Schritt 2: Hinzufügen der geeigneten Symbole</span><span class="sxs-lookup"><span data-stu-id="98c46-164">Step 2: Add the proper icons</span></span>

<span data-ttu-id="98c46-165">Die Symbole von Apps, die für einen URI-Schemanamen zum Standard werden, werden an verschiedenen Stellen innerhalb des Systems angezeigt wie beispielsweise in der Systemsteuerung unter "Standardprogramme".</span><span class="sxs-lookup"><span data-stu-id="98c46-165">Apps that become the default for a URI scheme name have their icons displayed in various places throughout the system such as in the Default programs control panel.</span></span> <span data-ttu-id="98c46-166">Fügen Sie daher ein 44 x 44-Symbol in das Projekt ein.</span><span class="sxs-lookup"><span data-stu-id="98c46-166">Include a 44x44 icon with your project for this purpose.</span></span> <span data-ttu-id="98c46-167">Stimmen Sie das Erscheinungsbild des Logos der App-Kachel ab, und verwenden Sie die Hintergrundfarbe der App, anstatt das Symbol transparent darzustellen.</span><span class="sxs-lookup"><span data-stu-id="98c46-167">Match the look of the app tile logo and use your app's background color rather than making the icon transparent.</span></span> <span data-ttu-id="98c46-168">Erweitern Sie das Logo bis zum Rand, ohne eine Auffüllung vorzunehmen.</span><span class="sxs-lookup"><span data-stu-id="98c46-168">Have the logo extend to the edge without padding it.</span></span> <span data-ttu-id="98c46-169">Testen Sie Ihre Symbole auf weißem Hintergrund.</span><span class="sxs-lookup"><span data-stu-id="98c46-169">Test your icons on white backgrounds.</span></span> <span data-ttu-id="98c46-170">Weitere Einzelheiten zu den Symbolen finden Sie unter [Richtlinien für Kacheln und Symbole](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-app-assets).</span><span class="sxs-lookup"><span data-stu-id="98c46-170">See [Guidelines for tile and icon assets](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-app-assets) for more details about icons.</span></span>

## <a name="step-3-handle-the-activated-event"></a><span data-ttu-id="98c46-171">Schritt 3: Behandeln des activated-Ereignisses</span><span class="sxs-lookup"><span data-stu-id="98c46-171">Step 3: Handle the activated event</span></span>


<span data-ttu-id="98c46-172">Der [**OnActivated**](https://msdn.microsoft.com/library/windows/apps/br242330)-Ereignishandler empfängt alle Aktivierungsereignisse.</span><span class="sxs-lookup"><span data-stu-id="98c46-172">The [**OnActivated**](https://msdn.microsoft.com/library/windows/apps/br242330) event handler receives all activation events.</span></span> <span data-ttu-id="98c46-173">Die **Kind**-Eigenschaft gibt den Typ des Aktivierungsereignisses an.</span><span class="sxs-lookup"><span data-stu-id="98c46-173">The **Kind** property indicates the type of activation event.</span></span> <span data-ttu-id="98c46-174">In diesem Beispiel werden [**Protocol**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.applicationmodel.activation.activationkind.aspx#Protocol)-Aktivierungsereignisse behandelt.</span><span class="sxs-lookup"><span data-stu-id="98c46-174">This example is set up to handle [**Protocol**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.applicationmodel.activation.activationkind.aspx#Protocol) activation events.</span></span>

> [!div class="tabbedCodeSnippets"]
> ```cs
> public partial class App
> {
>    protected override void OnActivated(IActivatedEventArgs args)
>   {
>       if (args.Kind == ActivationKind.Protocol)
>       {
>          ProtocolActivatedEventArgs eventArgs = args as ProtocolActivatedEventArgs;
>          // TODO: Handle URI activation
>          // The received URI is eventArgs.Uri.AbsoluteUri
>       }
>    }
> }
> ```
> ```vb
> Protected Overrides Sub OnActivated(ByVal args As Windows.ApplicationModel.Activation.IActivatedEventArgs)
>    If args.Kind = ActivationKind.Protocol Then
>       ProtocolActivatedEventArgs eventArgs = args As ProtocolActivatedEventArgs
>       
>       ' TODO: Handle URI activation
>       ' The received URI is eventArgs.Uri.AbsoluteUri
>  End If
> End Sub
> ```
> ```cpp
> void App::OnActivated(Windows::ApplicationModel::Activation::IActivatedEventArgs^ args)
> {
>    if (args->Kind == Windows::ApplicationModel::Activation::ActivationKind::Protocol)
>    {
>       Windows::ApplicationModel::Activation::ProtocolActivatedEventArgs^ eventArgs =
>           dynamic_cast<Windows::ApplicationModel::Activation::ProtocolActivatedEventArgs^>(args);
>       
>       // TODO: Handle URI activation  
>       // The received URI is eventArgs->Uri->RawUri
>    }
> }
> ```

> <span data-ttu-id="98c46-175">**Hinweis**  Stellen Sie sicher, dass beim Start über einen Protokollvertrag der Benutzer über die Schaltfläche „Zurück“ zu dem Bildschirm zurückkehrt, von dem aus die App gestartet wurde, und nicht zu den vorherigen Inhalten der App.</span><span class="sxs-lookup"><span data-stu-id="98c46-175">**Note**  When launched via Protocol Contract, make sure that Back button takes the user back to the screen that launched the app and not to the app's previous content.</span></span>

<span data-ttu-id="98c46-176">Apps sollten für jedes Aktivierungsereignis, durch das eine neue Seite geöffnet wird, einen neuen XAML-[**Frame**](https://msdn.microsoft.com/library/windows/apps/br242682) erstellen.</span><span class="sxs-lookup"><span data-stu-id="98c46-176">It is recommended that apps create a new XAML [**Frame**](https://msdn.microsoft.com/library/windows/apps/br242682) for each activation event that opens a new page.</span></span> <span data-ttu-id="98c46-177">So enthält der Navigationsbackstack für den neuen XAML-**Frame** keinen vorherigen Inhalt, der beim Anhalten der App im aktuellen Fenster angezeigt wurde.</span><span class="sxs-lookup"><span data-stu-id="98c46-177">This way, the navigation backstack for the new XAML **Frame** will not contain any previous content that the app might have on the current window when suspended.</span></span> <span data-ttu-id="98c46-178">Apps, für die ein einziger XAML-**Frame** für Start- und Dateiverträge verwendet wird, sollten vor dem Navigieren zu einer neuen Seite die Seiten im **Frame**-Navigationsjournal löschen.</span><span class="sxs-lookup"><span data-stu-id="98c46-178">Apps that decide to use a single XAML **Frame** for Launch and File Contracts should clear the pages on the **Frame** navigation journal before navigating to a new page.</span></span>

<span data-ttu-id="98c46-179">Per Protokollaktivierung gestartete Apps sollten ggf. eine Benutzeroberfläche enthalten, über die der Benutzer zur ersten Seite der App zurückkehren kann.</span><span class="sxs-lookup"><span data-stu-id="98c46-179">When launched via Protocol activation, apps should consider including UI that allows the user to go back to the top page of the app.</span></span>

## <a name="remarks"></a><span data-ttu-id="98c46-180">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="98c46-180">Remarks</span></span>


<span data-ttu-id="98c46-181">Ihr URI-Schemaname kann von jeder App oder Website verwendet werden, auch von schädlichen.</span><span class="sxs-lookup"><span data-stu-id="98c46-181">Any app or website can use your URI scheme name, including malicious ones.</span></span> <span data-ttu-id="98c46-182">Alle im URI empfangenen Daten könnten daher von einer nicht vertrauenswürdigen Quelle stammen.</span><span class="sxs-lookup"><span data-stu-id="98c46-182">So any data that you get in the URI could come from an untrusted source.</span></span> <span data-ttu-id="98c46-183">Wir empfehlen, niemals eine endgültige Aktion auf Grundlage der Parameter auszuführen, die Sie im URI erhalten.</span><span class="sxs-lookup"><span data-stu-id="98c46-183">We recommend that you never perform a permanent action based on the parameters that you receive in the URI.</span></span> <span data-ttu-id="98c46-184">URI-Parameter können z.B. zum Starten der App mit der Kontoseite eines Benutzers, aber nicht zum direkten Ändern des Kontos des Benutzers verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="98c46-184">For example, URI parameters could be used to launch the app to a user's account page, but we recommend that you never use them to directly modify the user's account.</span></span>

> <span data-ttu-id="98c46-185">**Hinweis**  Wenn Sie für Ihre App einen neuen URI-Schemanamen erstellen, ist es wichtig, dass Sie die Anleitungen in [RFC 4395](http://go.microsoft.com/fwlink/p/?LinkID=266550) befolgen.</span><span class="sxs-lookup"><span data-stu-id="98c46-185">**Note**  If you are creating a new URI scheme name for your app, be sure to follow the guidance in [RFC 4395](http://go.microsoft.com/fwlink/p/?LinkID=266550).</span></span> <span data-ttu-id="98c46-186">Damit wird sichergestellt, dass der Name die Standards für URI-Schemas erfüllt.</span><span class="sxs-lookup"><span data-stu-id="98c46-186">This ensures that your name meets the standards for URI schemes.</span></span>

> <span data-ttu-id="98c46-187">**Hinweis**  Stellen Sie sicher, dass beim Start über einen Protokollvertrag der Benutzer über die Schaltfläche „Zurück“ zu dem Bildschirm zurückkehrt, von dem aus die App gestartet wurde, und nicht zu den vorherigen Inhalten der App.</span><span class="sxs-lookup"><span data-stu-id="98c46-187">**Note**  When launched via Protocol Contract, make sure that Back button takes the user back to the screen that launched the app and not to the app's previous content.</span></span>

<span data-ttu-id="98c46-188">Apps sollten für jedes Aktivierungsereignis, durch das ein neues URI-Ziel geöffnet wird, einen neuen XAML-[**Frame**](https://msdn.microsoft.com/library/windows/apps/br242682) erstellen.</span><span class="sxs-lookup"><span data-stu-id="98c46-188">We recommend that apps create a new XAML [**Frame**](https://msdn.microsoft.com/library/windows/apps/br242682) for each activation event that opens a new Uri target.</span></span> <span data-ttu-id="98c46-189">So enthält der Navigationsbackstack für den neuen XAML-**Frame** keinen vorherigen Inhalt, der beim Anhalten der App im aktuellen Fenster angezeigt wurde.</span><span class="sxs-lookup"><span data-stu-id="98c46-189">This way, the navigation backstack for the new XAML **Frame** will not contain any previous content that the app might have on the current window when suspended.</span></span>

<span data-ttu-id="98c46-190">Falls Ihre Apps für Start- und Protokollverträge einen einzelnen XAML-[**Frame**](https://msdn.microsoft.com/library/windows/apps/br242682) verwenden sollen, müssen vor dem Navigieren zu einer neuen Seite die Seiten im **Frame**-Navigationsjournal gelöscht werden.</span><span class="sxs-lookup"><span data-stu-id="98c46-190">If you decide that you want your apps to use a single XAML [**Frame**](https://msdn.microsoft.com/library/windows/apps/br242682) for Launch and Protocol Contracts, clear the pages on the **Frame** navigation journal before navigating to a new page.</span></span> <span data-ttu-id="98c46-191">Über den Protokollvertrag gestartete Apps sollten ggf. eine Benutzeroberfläche enthalten, über die der Benutzer zum Anfang der App zurückkehren kann.</span><span class="sxs-lookup"><span data-stu-id="98c46-191">When launched via Protocol Contract, consider including UI into your apps that allows the user to go back to the top of the app.</span></span>

> <span data-ttu-id="98c46-192">**Hinweis**  Dieser Artikel ist für Windows 10-Entwickler gedacht, die Apps für die Universelle Windows-Plattform (UWP) schreiben.</span><span class="sxs-lookup"><span data-stu-id="98c46-192">**Note**  This article is for Windows 10 developers writing Universal Windows Platform (UWP) apps.</span></span> <span data-ttu-id="98c46-193">Wenn Sie für Windows8.x oder Windows Phone8.x entwickeln, finden Sie Informationen dazu in der [archivierten Dokumentation](http://go.microsoft.com/fwlink/p/?linkid=619132).</span><span class="sxs-lookup"><span data-stu-id="98c46-193">If you're developing for Windows 8.x or Windows Phone 8.x, see the [archived documentation](http://go.microsoft.com/fwlink/p/?linkid=619132).</span></span>

 

## <a name="related-topics"></a><span data-ttu-id="98c46-194">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="98c46-194">Related topics</span></span>


**<span data-ttu-id="98c46-195">Vollständiges Beispiel</span><span class="sxs-lookup"><span data-stu-id="98c46-195">Complete example</span></span>**

* [<span data-ttu-id="98c46-196">Beispiel für Assoziationsstart</span><span class="sxs-lookup"><span data-stu-id="98c46-196">Association launching sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=231484)

**<span data-ttu-id="98c46-197">Konzepte</span><span class="sxs-lookup"><span data-stu-id="98c46-197">Concepts</span></span>**

* [<span data-ttu-id="98c46-198">Standardprogramme</span><span class="sxs-lookup"><span data-stu-id="98c46-198">Default Programs</span></span>](https://msdn.microsoft.com/library/windows/desktop/cc144154)
* [<span data-ttu-id="98c46-199">Dateityp- und URI-Zuordnungsmodell</span><span class="sxs-lookup"><span data-stu-id="98c46-199">File Type and URI Associations Model</span></span>](https://msdn.microsoft.com/library/windows/desktop/hh848047)

**<span data-ttu-id="98c46-200">Aufgaben</span><span class="sxs-lookup"><span data-stu-id="98c46-200">Tasks</span></span>**

* [<span data-ttu-id="98c46-201">Starten der Standard-App für einen URI</span><span class="sxs-lookup"><span data-stu-id="98c46-201">Launch the default app for a URI</span></span>](launch-default-app.md)
* [<span data-ttu-id="98c46-202">Behandeln der Dateiaktivierung</span><span class="sxs-lookup"><span data-stu-id="98c46-202">Handle file activation</span></span>](handle-file-activation.md)

**<span data-ttu-id="98c46-203">Richtlinien</span><span class="sxs-lookup"><span data-stu-id="98c46-203">Guidelines</span></span>**

* [<span data-ttu-id="98c46-204">Richtlinien für Dateitypen und URIs</span><span class="sxs-lookup"><span data-stu-id="98c46-204">Guidelines for file types and URIs</span></span>](https://msdn.microsoft.com/library/windows/apps/hh700321)

**<span data-ttu-id="98c46-205">Referenz</span><span class="sxs-lookup"><span data-stu-id="98c46-205">Reference</span></span>**

* [**<span data-ttu-id="98c46-206">AppX Package Manifest</span><span class="sxs-lookup"><span data-stu-id="98c46-206">AppX Package Manifest</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn934791)
* [**<span data-ttu-id="98c46-207">Windows.ApplicationModel.Activation.ProtocolActivatedEventArgs</span><span class="sxs-lookup"><span data-stu-id="98c46-207">Windows.ApplicationModel.Activation.ProtocolActivatedEventArgs</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224742)
* [**<span data-ttu-id="98c46-208">Windows.UI.Xaml.Application.OnActivated</span><span class="sxs-lookup"><span data-stu-id="98c46-208">Windows.UI.Xaml.Application.OnActivated</span></span>**](https://msdn.microsoft.com/library/windows/apps/br242330)

 

 
