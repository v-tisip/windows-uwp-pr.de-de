---
author: TylerMSFT
title: Aktivieren von apps für Websites mit app-URI-Handlern
description: Fördern Sie Nutzer an Ihrer app durch die Unterstützung von Apps für Websites Feature.
keywords: Deep-Links in Windows
ms.author: twhitney
ms.date: 08/25/2017
ms.topic: article
ms.assetid: 260cf387-88be-4a3d-93bc-7e4560f90abc
ms.localizationpriority: medium
ms.openlocfilehash: 7f6438b8d1d7b8a8ce47ed4e5baddcb59285e660
ms.sourcegitcommit: cd00bb829306871e5103db481cf224ea7fb613f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5875604"
---
# <a name="enable-apps-for-websites-using-app-uri-handlers"></a><span data-ttu-id="61642-104">Aktivieren von apps für Websites mit app-URI-Handlern</span><span class="sxs-lookup"><span data-stu-id="61642-104">Enable apps for websites using app URI handlers</span></span>

<span data-ttu-id="61642-105">Apps für Websites ordnet Ihrer app mit einer Website, sodass Ihre app, wenn ein Benutzer einen Link zu Ihrer Website öffnet, statt des Browsers gestartet werden wird.</span><span class="sxs-lookup"><span data-stu-id="61642-105">Apps for Websites associates your app with a website so that when someone opens a link to your website, your app is launched instead of opening the browser.</span></span> <span data-ttu-id="61642-106">Wenn Ihre app nicht installiert ist, öffnet Ihre Website wie gewohnt im Browser.</span><span class="sxs-lookup"><span data-stu-id="61642-106">If your app is not installed, your website opens in the browser as usual.</span></span> <span data-ttu-id="61642-107">Benutzer können dieser Erfahrung vertrauen, da nur Urheber verifizierten Contents registrieren können.</span><span class="sxs-lookup"><span data-stu-id="61642-107">Users can trust this experience because only verified content owners can register for a link.</span></span> <span data-ttu-id="61642-108">Benutzer kann auf alle ihre registrierten Web-zu-app Hyperlinks überprüfen, indem Sie zu Einstellungen > Apps > Apps für Websites.</span><span class="sxs-lookup"><span data-stu-id="61642-108">Users will be able to check all of their registered web-to-app links by going to Settings > Apps > Apps for websites.</span></span>

<span data-ttu-id="61642-109">Um Web-zu-app Verlinkung zu aktivieren müssen:</span><span class="sxs-lookup"><span data-stu-id="61642-109">To enable web-to-app linking you will need to:</span></span>
- <span data-ttu-id="61642-110">Identifizieren Sie die URIs, die Ihrer App in der Manifestdatei behandeln wird.</span><span class="sxs-lookup"><span data-stu-id="61642-110">Identify the URIs your app will handle in the manifest file</span></span>
- <span data-ttu-id="61642-111">Eine JSON-Datei, die Zuordnung zwischen Ihrer app und Ihre Website definiert.</span><span class="sxs-lookup"><span data-stu-id="61642-111">A JSON file that defines the association between your app and your website.</span></span> <span data-ttu-id="61642-112">mit dem Paketfamiliennamen app im selben Stammverzeichnis wie die app-manifest Deklaration.</span><span class="sxs-lookup"><span data-stu-id="61642-112">with the app Package Family Name at the same host root as the app manifest declaration.</span></span>
- <span data-ttu-id="61642-113">Behandeln Sie die Aktivierung in der App</span><span class="sxs-lookup"><span data-stu-id="61642-113">Handle the activation in the app.</span></span>

> [!Note]
> <span data-ttu-id="61642-114">Ab Windows 10 Creators Update, wird unterstützten Links in Microsoft Edge geklickt die entsprechende app gestartet.</span><span class="sxs-lookup"><span data-stu-id="61642-114">Starting with the Windows 10 Creators update, supported links clicked in Microsoft Edge will launch the corresponding app.</span></span> <span data-ttu-id="61642-115">Unterstützte Links geklickt in anderen Browsern (z. B. Internet Explorer, usw.), wird Sie in das Browsen erhalten bleiben.</span><span class="sxs-lookup"><span data-stu-id="61642-115">Supported links clicked in other browsers (e.g. Internet Explorer, etc.), will keep you in the browsing experience.</span></span>

## <a name="register-to-handle-http-and-https-links-in-the-app-manifest"></a><span data-ttu-id="61642-116">Registrieren Sie sich, um HTTP- und Https-Links im App-Manifest zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="61642-116">Register to handle http and https links in the app manifest</span></span>

<span data-ttu-id="61642-117">Ihre App muss die URIs für die Websites zu identifizieren, die sie behandeln soll.</span><span class="sxs-lookup"><span data-stu-id="61642-117">Your app needs to identify the URIs for the websites it will handle.</span></span> <span data-ttu-id="61642-118">Fügen Sie hierzu die **Windows.appUriHandler** Erweiterung Registrierung zu Ihrer app-Manifestdatei hinzu **Package.appxmanifest**.</span><span class="sxs-lookup"><span data-stu-id="61642-118">To do so, add the **Windows.appUriHandler** extension registration to your app’s manifest file **Package.appxmanifest**.</span></span>

<span data-ttu-id="61642-119">Wenn beispielsweise die Adresse Ihrer Website "msn.com" lautet, würden Sie den folgenden Eintrag in Ihrem App-Manifest machen:</span><span class="sxs-lookup"><span data-stu-id="61642-119">For example, if your website’s address is “msn.com” you would make the following entry in your app’s manifest:</span></span>

```xml
<Applications>
  <Application ... >
      ...
      <Extensions>
         <uap3:Extension Category="windows.appUriHandler">
          <uap3:AppUriHandler>
            <uap3:Host Name="msn.com" />
          </uap3:AppUriHandler>
        </uap3:Extension>
      </Extensions>
  </Application>
</Applications>
```

<span data-ttu-id="61642-120">Die obige Deklaration registriert Ihre App zur Behandlung von Links vom angegebenen Host.</span><span class="sxs-lookup"><span data-stu-id="61642-120">The declaration above registers your app to handle links from the specified host.</span></span> <span data-ttu-id="61642-121">Wenn Ihre Website mehrere Adressen hat (z. B.: m.example.com, www.example.com und example.com), fügen Sie einen separaten `<uap3:Host Name=... />` Eintrag innerhalb des `<uap3:AppUriHandler>` für die einzelnen Adressen hinzu.</span><span class="sxs-lookup"><span data-stu-id="61642-121">If your website has multiple addresses (for example: m.example.com, www.example.com, and example.com) then add a separate `<uap3:Host Name=... />` entry inside of the `<uap3:AppUriHandler>` for each address.</span></span>

## <a name="associate-your-app-and-website-with-a-json-file"></a><span data-ttu-id="61642-122">Verknüpfen Sie Ihre App und die Website mit einer JSON-Datei</span><span class="sxs-lookup"><span data-stu-id="61642-122">Associate your app and website with a JSON file</span></span>

<span data-ttu-id="61642-123">Um sicherzustellen, dass nur Ihre App die Inhalte auf Ihrer Website öffnen kann, sollten Sie den Paketfamiliennamen Ihrer App in eine JSON-Datei einbinden, die auf dem Webserver-Stammverzeichnis oder in einem bekannten Verzeichnis der Domäne liegt.</span><span class="sxs-lookup"><span data-stu-id="61642-123">To ensure that only your app can open content on your website, include your app's package family name in a JSON file located in the web server root, or at the well-known directory on the domain.</span></span> <span data-ttu-id="61642-124">Dies bedeutet, dass Ihre Website die Zustimmung gibt, dass die aufgeführten Apps Inhalte auf Ihrer Website öffnen können.</span><span class="sxs-lookup"><span data-stu-id="61642-124">This signifies that your website gives consent for the listed apps to open content on your site.</span></span> <span data-ttu-id="61642-125">Sie können den Paketfamiliennamen im Packages-Abschnitt Pakete des App-Manifest-Designers finden.</span><span class="sxs-lookup"><span data-stu-id="61642-125">You can find the package family name in the Packages section in the app manifest designer.</span></span>

>[!Important]
> <span data-ttu-id="61642-126">Die JSON-Datei sollte kein .json Dateisuffix aufweisen.</span><span class="sxs-lookup"><span data-stu-id="61642-126">The JSON file should not have a .json file suffix.</span></span>

<span data-ttu-id="61642-127">Erstellen Sie eine JSON-Datei (ohne die Erweiterung .json) mit dem Namen **Windows-App-Web-Link** und stellen Sie den Paketfamiliennamen Ihrer App bereit.</span><span class="sxs-lookup"><span data-stu-id="61642-127">Create a JSON file (without the .json file extension) named **windows-app-web-link** and provide your app’s package family name.</span></span> <span data-ttu-id="61642-128">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="61642-128">For example:</span></span>

``` JSON
[{
  "packageFamilyName": "Your app's package family name, e.g MyApp_9jmtgj1pbbz6e",
  "paths": [ "*" ],
  "excludePaths" : [ "/news/*", "/blog/*" ]
 }]
```

<span data-ttu-id="61642-129">Windows wird eine Https-Verbindung mit Ihrer Website herstellen und nach der entsprechenden JSON Datei auf dem Webserver suchen.</span><span class="sxs-lookup"><span data-stu-id="61642-129">Windows will make an https connection to your website and will look for the corresponding JSON file on your web server.</span></span>

### <a name="wildcards"></a><span data-ttu-id="61642-130">Platzhalter</span><span class="sxs-lookup"><span data-stu-id="61642-130">Wildcards</span></span>

<span data-ttu-id="61642-131">Das obige für eine JSON-Datei veranschaulicht die Verwendung von Platzhaltern.</span><span class="sxs-lookup"><span data-stu-id="61642-131">The JSON file example above demonstrates the use of wildcards.</span></span> <span data-ttu-id="61642-132">Platzhalter erlauben es Ihnen eine Vielzahl von Links mit weniger Codezeilen zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="61642-132">Wildcards allow you to support a wide variety of links with fewer lines of code.</span></span> <span data-ttu-id="61642-133">Die Web-zu-App-Verknüpfung unterstützt zwei Arten von Platzhaltern in der JSON-Datei:</span><span class="sxs-lookup"><span data-stu-id="61642-133">Web-to-app linking supports two types of wildcards in the JSON file:</span></span>

| **<span data-ttu-id="61642-134">Platzhalter</span><span class="sxs-lookup"><span data-stu-id="61642-134">Wildcard</span></span>** | **<span data-ttu-id="61642-135">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="61642-135">Description</span></span>**               |
|--------------|-------------------------------|
| **\***       | <span data-ttu-id="61642-136">Repräsentiert eine beliebige Teilzeichenfolge</span><span class="sxs-lookup"><span data-stu-id="61642-136">Represents any substring</span></span>      |
| **<span data-ttu-id="61642-137">?</span><span class="sxs-lookup"><span data-stu-id="61642-137">?</span></span>**        | <span data-ttu-id="61642-138">Steht für ein einzelnes Zeichen</span><span class="sxs-lookup"><span data-stu-id="61642-138">Represents a single character</span></span> |

<span data-ttu-id="61642-139">Angenommen, `"excludePaths" : [ "/news/*", "/blog/*" ]` im obigen Beispiel wird Ihre app alle Pfade, die mit Ihrer Website Adresse (z. B. msn.com), **mit Ausnahme von** Pfade unter beginnen unterstützen `/news/` und `/blog/`.</span><span class="sxs-lookup"><span data-stu-id="61642-139">For example, given `"excludePaths" : [ "/news/*", "/blog/*" ]` in the example above, your app will support all paths that start with your website’s address (e.g. msn.com), **except** those under `/news/` and `/blog/`.</span></span> <span data-ttu-id="61642-140">**msn.com/weather.html** wird unterstützt, aber nicht \*\*\*\*msn.com/news/topnews.html\*\*\*\*.</span><span class="sxs-lookup"><span data-stu-id="61642-140">**msn.com/weather.html** will be supported, but not \*\*\*\*msn.com/news/topnews.html\*\*\*\*.</span></span>

### <a name="multiple-apps"></a><span data-ttu-id="61642-141">Mehrere Apps</span><span class="sxs-lookup"><span data-stu-id="61642-141">Multiple apps</span></span>

<span data-ttu-id="61642-142">Wenn Sie zwei Apps haben, die Sie mit Ihrer Website verknüpfen möchten, listen Sie beide Paketfamiliennamen der Apps in der **Windows-App-Web-Link** JSON-Datei auf.</span><span class="sxs-lookup"><span data-stu-id="61642-142">If you have two apps that you would like to link to your website, list both of the application package family names in your **windows-app-web-link** JSON file.</span></span> <span data-ttu-id="61642-143">Beide Apps können unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="61642-143">Both apps can be supported.</span></span> <span data-ttu-id="61642-144">Dem Benutzer wird eine Auswahl für den Standardlink angezeigt, wenn beide Apps installiert sind.</span><span class="sxs-lookup"><span data-stu-id="61642-144">The user will be presented with a choice of which is the default link if both are installed.</span></span> <span data-ttu-id="61642-145">Falls sie den Standardlink später ändern möchten, können ändern sie ihn unter **Einstellungen > Apps für Websites** ändern.</span><span class="sxs-lookup"><span data-stu-id="61642-145">If they want to change the default link later, they can change it in **Settings > Apps for Websites**.</span></span> <span data-ttu-id="61642-146">Entwickler können auch die JSON-Datei jederzeit ändern und die Änderung noch am selben Tag, aber bis spätestens acht Tage nach dem Update einsehen.</span><span class="sxs-lookup"><span data-stu-id="61642-146">Developers can also change the JSON file at any time and see the change as early as the same day but no later than eight days after the update.</span></span>

``` JSON
[{
  "packageFamilyName": "Your apps's package family name, e.g MyApp_9jmtgj1pbbz6e",
  "paths": [ "*" ],
  "excludePaths" : [ "/news/*", "/blog/*" ]
 },
 {
  "packageFamilyName": "Your second app's package family name, e.g. MyApp2_8jmtgj2pbbz6e",
  "paths": [ "/example/*", "/links/*" ]
 }]
```

<span data-ttu-id="61642-147">Um Ihren Benutzern die bestmögliche Erfahrung zu bieten, verwenden Sie Ausschlusspfade, um sicherzustellen, dass der nur online verfügbare Inhalt von den unterstützten Pfaden in der JSON-Datei ausgenommen ist.</span><span class="sxs-lookup"><span data-stu-id="61642-147">To provide the best experience for your users, use exclude paths to make sure that online-only content is excluded from the supported paths in your JSON file.</span></span>

<span data-ttu-id="61642-148">Ausschlusspfade werden zuerst überprüft, und wenn eine Übereinstimmung vorliegt wird die entsprechende Seite mit dem Browser anstelle der angegebenen App geöffnet.</span><span class="sxs-lookup"><span data-stu-id="61642-148">Exclude paths are checked first and if there is a match the corresponding page will be opened with the browser instead of the designated app.</span></span> <span data-ttu-id="61642-149">Im obigen Beispiel enthält "/ News / \ \*" alle Seiten unter diesem Pfad, während "/ News\ \*" (keine vorwärts-Slash "news") Pfade unter "News\ \*" wie "Newslocal /", "Newsinternational /" usw.. enthält.</span><span class="sxs-lookup"><span data-stu-id="61642-149">In the example above, ‘/news/\*’ includes any pages under that path while ‘/news\*’ (no forward slash trails 'news') includes any paths under ‘news\*’ such as ‘newslocal/’, ‘newsinternational/’, and so on.</span></span>

## <a name="handle-links-on-activation-to-link-to-content"></a><span data-ttu-id="61642-150">Behandeln Sie Links auf Aktivierung, um Links mit Inhalt zu verbinden.</span><span class="sxs-lookup"><span data-stu-id="61642-150">Handle links on Activation to link to content</span></span>

<span data-ttu-id="61642-151">Navigieren Sie zu **App.xaml.cs** in der Visual Studio Lösung für Ihrer App und fügen Sie in **OnActivated()** die Behandlung für verknüpfte Inhalte hinzu.</span><span class="sxs-lookup"><span data-stu-id="61642-151">Navigate to **App.xaml.cs** in your app’s Visual Studio solution and in **OnActivated()** add handling for linked content.</span></span> <span data-ttu-id="61642-152">Im folgenden Beispiel hängt die Seite, die in der App geöffnet wird, vom URI-Pfad ab:</span><span class="sxs-lookup"><span data-stu-id="61642-152">In the following example, the page that is opened in the app depends on the URI path:</span></span>

``` CS
protected override void OnActivated(IActivatedEventArgs e)
{
    Frame rootFrame = Window.Current.Content as Frame;
    if (rootFrame == null)
    {
        ...
    }

    // Check ActivationKind, Parse URI, and Navigate user to content
    Type deepLinkPageType = typeof(MainPage);
    if (e.Kind == ActivationKind.Protocol)
    {
        var protocolArgs = (ProtocolActivatedEventArgs)e;        
        switch (protocolArgs.Uri.AbsolutePath)
        {
            case "/":
                break;
            case "/index.html":
                break;
            case "/sports.html":
                deepLinkPageType = typeof(SportsPage);
                break;
            case "/technology.html":
                deepLinkPageType = typeof(TechnologyPage);
                break;
            case "/business.html":
                deepLinkPageType = typeof(BusinessPage);
                break;
            case "/science.html":
                deepLinkPageType = typeof(SciencePage);
                break;
        }
    }

    if (rootFrame.Content == null)
    {
        // Default navigation
        rootFrame.Navigate(deepLinkPageType, e);
    }

    // Ensure the current window is active
    Window.Current.Activate();
}
```

<span data-ttu-id="61642-153">**Wichtig** Stellen Sie sicher, dass das finale `if (rootFrame.Content == null)` logic durch `rootFrame.Navigate(deepLinkPageType, e);` ersetzt wird, wie im obigen Beispiel gezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="61642-153">**Important** Make sure to replace the final `if (rootFrame.Content == null)` logic with `rootFrame.Navigate(deepLinkPageType, e);` as shown in the example above.</span></span>

## <a name="test-it-out-local-validation-tool"></a><span data-ttu-id="61642-154">Testen Sie: Lokales Überprüfungswerkzeug</span><span class="sxs-lookup"><span data-stu-id="61642-154">Test it out: Local validation tool</span></span>

<span data-ttu-id="61642-155">Sie können die Konfiguration Ihrer App und Website durch Ausführen des App-Host Registration Verifier Werkzeugs prüfen, der hier verfügbar ist:</span><span class="sxs-lookup"><span data-stu-id="61642-155">You can test the configuration of your app and website by running the App host registration verifier tool which is available in:</span></span>

<span data-ttu-id="61642-156">%windir%\\system32\\**AppHostRegistrationVerifier.exe**</span><span class="sxs-lookup"><span data-stu-id="61642-156">%windir%\\system32\\**AppHostRegistrationVerifier.exe**</span></span>

<span data-ttu-id="61642-157">Testen Sie die Konfiguration Ihrer App und, indem Sie dieses Werkzeug mit folgenden Parametern ausführen.</span><span class="sxs-lookup"><span data-stu-id="61642-157">Test the configuration of your app and website by running this tool with the following parameters:</span></span>

<span data-ttu-id="61642-158">**AppHostRegistrationVerifier.exe** *hostname packagefamilyname filepath*</span><span class="sxs-lookup"><span data-stu-id="61642-158">**AppHostRegistrationVerifier.exe** *hostname packagefamilyname filepath*</span></span>

-   <span data-ttu-id="61642-159">Hostname: Ihre Website (z. B. microsoft.com)</span><span class="sxs-lookup"><span data-stu-id="61642-159">Hostname: Your website (e.g. microsoft.com)</span></span>
-   <span data-ttu-id="61642-160">Paketfamiliennamen (PFN): Ihre App-PFN</span><span class="sxs-lookup"><span data-stu-id="61642-160">Package Family Name (PFN): Your app’s PFN</span></span>
-   <span data-ttu-id="61642-161">Dateipfad: die JSON-Datei für die lokale Überprüfung (z. B. C:\\SomeFolder\\windows-App-Web-link)</span><span class="sxs-lookup"><span data-stu-id="61642-161">File path: The JSON file for local validation (e.g. C:\\SomeFolder\\windows-app-web-link)</span></span>

<span data-ttu-id="61642-162">Wenn das Tool keine nichts zurückgibt, funktioniert Überprüfung für diese Datei beim Hochladen.</span><span class="sxs-lookup"><span data-stu-id="61642-162">If the tool does not return anything, validation will work on that file when uploaded.</span></span> <span data-ttu-id="61642-163">Wenn ein Fehlercode vorhanden ist, wird es nicht funktionieren.</span><span class="sxs-lookup"><span data-stu-id="61642-163">If there is an error code, it will not work.</span></span>

<span data-ttu-id="61642-164">Sie können den folgenden Registrierungsschlüssel Pfad Abgleich für quergeladene apps als Teil des lokalen Überprüfung erzwingen aktivieren:</span><span class="sxs-lookup"><span data-stu-id="61642-164">You can enable the following registry key to force path matching for side-loaded apps as part of local validation:</span></span>

`HKCU\Software\Classes\LocalSettings\Software\Microsoft\Windows\CurrentVersion\
AppModel\SystemAppData\YourApp\AppUriHandlers`

<span data-ttu-id="61642-165">Schlüsselname: `ForceValidation` Wert:</span><span class="sxs-lookup"><span data-stu-id="61642-165">Keyname: `ForceValidation` Value:</span></span> `1`

## <a name="test-it-web-validation"></a><span data-ttu-id="61642-166">Testen Sie es: Web-Überprüfung</span><span class="sxs-lookup"><span data-stu-id="61642-166">Test it: Web validation</span></span>

<span data-ttu-id="61642-167">Schließen Sie die Anwendung, um sicherzustellen, dass die App aktiviert wird, wenn Sie auf einen Link klicken.</span><span class="sxs-lookup"><span data-stu-id="61642-167">Close your application to verify that the app is activated when you click a link.</span></span> <span data-ttu-id="61642-168">Kopieren Sie dann die Adresse eines unterstützten Pfades in Ihrer Website.</span><span class="sxs-lookup"><span data-stu-id="61642-168">Then, copy the address of one of the supported paths in your website.</span></span> <span data-ttu-id="61642-169">Wenn Ihre Websiteadresse beispielsweise "msn.com" lautet, und einer der unterstützen Pfade "path1" ist, verwenden Sie</span><span class="sxs-lookup"><span data-stu-id="61642-169">For example, if your website’s address is “msn.com”, and one of the support paths is “path1”, you would use</span></span> `http://msn.com/path1`

<span data-ttu-id="61642-170">Stellen Sie sicher, dass Ihre app geschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="61642-170">Verify that your app is closed.</span></span> <span data-ttu-id="61642-171">Drücken Sie die **Windows-Taste + R** zum Öffnen des **ausführen**-Dialogfelds fügen Sie den Link im Fenster ein.</span><span class="sxs-lookup"><span data-stu-id="61642-171">Press **Windows Key + R** to open the **Run** dialog box and paste the link in the window.</span></span> <span data-ttu-id="61642-172">Ihre app sollte anstelle des Webbrowsers gestartet werden.</span><span class="sxs-lookup"><span data-stu-id="61642-172">Your app should launch instead of the web browser.</span></span>

<span data-ttu-id="61642-173">Darüber hinaus können Sie Ihre App testen, indem Sie sie über eine andere app mithilfe der [LaunchUriAsync](https://msdn.microsoft.com/library/windows/apps/hh701480.aspx) API starten.</span><span class="sxs-lookup"><span data-stu-id="61642-173">Additionally, you can test your app by launching it from another app using the [LaunchUriAsync](https://msdn.microsoft.com/library/windows/apps/hh701480.aspx) API.</span></span> <span data-ttu-id="61642-174">Diese API können auch Sie nutzen, um dies auf Telefonen zu testen.</span><span class="sxs-lookup"><span data-stu-id="61642-174">You can use this API to test on phones as well.</span></span>

<span data-ttu-id="61642-175">Wenn Sie der protocol activation logic zu folgen möchten, legen Sie einen Haltepunkt im **OnActivated** -Ereignishandler fest.</span><span class="sxs-lookup"><span data-stu-id="61642-175">If you would like to follow the protocol activation logic, set a breakpoint in the **OnActivated** event handler.</span></span>

## <a name="appurihandlers-tips"></a><span data-ttu-id="61642-176">AppUriHandlers Tipps:</span><span class="sxs-lookup"><span data-stu-id="61642-176">AppUriHandlers tips:</span></span>

- <span data-ttu-id="61642-177">Stellen Sie sicher, dass Sie nur Links angeben, die mit Ihrer App kompatibel sind.</span><span class="sxs-lookup"><span data-stu-id="61642-177">Make sure to only specify links that your app can handle.</span></span>
- <span data-ttu-id="61642-178">Listen Sie alle Hosts auf, die Sie unterstützen werden.</span><span class="sxs-lookup"><span data-stu-id="61642-178">List all of the hosts that you will support.</span></span>  <span data-ttu-id="61642-179">Beachten Sie, dass www.example.com und example.com verschiedene Hosts sind.</span><span class="sxs-lookup"><span data-stu-id="61642-179">Note that www.example.com and example.com are different hosts.</span></span>
- <span data-ttu-id="61642-180">Benutzer können in den Einstellungen auswählen, welche App sie zum Öffnen von Websites bevorzugen.</span><span class="sxs-lookup"><span data-stu-id="61642-180">Users can choose which app they prefer to handle websites in Settings.</span></span>
- <span data-ttu-id="61642-181">Ihre JSON-Datei muss auf einen Https-Server hochgeladen werden.</span><span class="sxs-lookup"><span data-stu-id="61642-181">Your JSON file must be uploaded to an https server.</span></span>
- <span data-ttu-id="61642-182">Wenn Sie die Pfade, die Sie unterstützen möchten, ändern müssen, können Sie JSON-Datei erneut hochladen, ohne Ihre App erneut veröffentlichen zu müssen.</span><span class="sxs-lookup"><span data-stu-id="61642-182">If you need to change the paths that you wish to support, you can republish your JSON file without republishing your app.</span></span> <span data-ttu-id="61642-183">Benutzern wird die Änderungen in 1 bis 8 Tagen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="61642-183">Users will see the changes in 1-8 days.</span></span>
- <span data-ttu-id="61642-184">Alle quergeladenen Apps mit AppUriHandlern werden validierte Links für den Host on Install haben</span><span class="sxs-lookup"><span data-stu-id="61642-184">All sideloaded apps with AppUriHandlers will have validated links for the host on install.</span></span> <span data-ttu-id="61642-185">Sie müssen kein JSON-Datei hochgeladen haben, um das Feature zu testen.</span><span class="sxs-lookup"><span data-stu-id="61642-185">You do not need to have a JSON file uploaded to test the feature.</span></span>
- <span data-ttu-id="61642-186">Dieses Feature funktioniert, wann immer Ihre App eine UWP-App ist, die mit  [LaunchUriAsync](https://msdn.microsoft.com/library/windows/apps/hh701480.aspx) gestartet ist, oder eine Windows-Desktop-App, gestartet mit  [ShellExecuteEx](https://msdn.microsoft.com/library/windows/desktop/bb762154(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="61642-186">This feature works whenever your app is a UWP app launched with  [LaunchUriAsync](https://msdn.microsoft.com/library/windows/apps/hh701480.aspx) or a Windows desktop app launched with  [ShellExecuteEx](https://msdn.microsoft.com/library/windows/desktop/bb762154(v=vs.85).aspx).</span></span> <span data-ttu-id="61642-187">Wenn die URL einen registrierten URI App Handler entspricht, wird die App anstelle des Browsers gestartet werden.</span><span class="sxs-lookup"><span data-stu-id="61642-187">If the URL corresponds to a registered App URI handler, the app will be launched instead of the browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="61642-188">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="61642-188">See also</span></span>

<span data-ttu-id="61642-189">[Web-zu-App-Beispielprojekt](https://github.com/project-rome/AppUriHandlers/tree/master/NarwhalFacts)
[windows.protocol-Registrierung](https://msdn.microsoft.com/library/windows/apps/br211458.aspx)
[Behandeln der URI-Aktivierung](https://msdn.microsoft.com/windows/uwp/launch-resume/handle-uri-activation)
[Zuordnung starten-Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AssociationLaunching) veranschaulicht, wie die LaunchUriAsync() API verwenden.</span><span class="sxs-lookup"><span data-stu-id="61642-189">[Web-to-App example project](https://github.com/project-rome/AppUriHandlers/tree/master/NarwhalFacts)
[windows.protocol registration](https://msdn.microsoft.com/library/windows/apps/br211458.aspx)
[Handle URI Activation](https://msdn.microsoft.com/windows/uwp/launch-resume/handle-uri-activation)
[Association Launching sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AssociationLaunching) illustrates how to use the LaunchUriAsync() API.</span></span>
