---
title: Aktivieren von apps für Websites mit app-URI-Handlern
description: Fördern Sie Nutzer an Ihrer app durch die Unterstützung von Apps für Websites Feature.
keywords: Deep-Links in Windows
ms.date: 08/25/2017
ms.topic: article
ms.assetid: 260cf387-88be-4a3d-93bc-7e4560f90abc
ms.localizationpriority: medium
ms.openlocfilehash: 66284538c97aee1a11c27beaa483dcfe109b6615
ms.sourcegitcommit: d2517e522cacc5240f7dffd5bc1eaa278e3f7768
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "8325596"
---
# <a name="enable-apps-for-websites-using-app-uri-handlers"></a>Aktivieren von apps für Websites mit app-URI-Handlern

Apps für Websites ordnet Ihrer app mit einer Website, sodass Ihre app, wenn ein Benutzer einen Link zu Ihrer Website öffnet, statt des Browsers gestartet werden wird. Wenn Ihre app nicht installiert ist, öffnet Ihre Website wie gewohnt im Browser. Benutzer können dieser Erfahrung vertrauen, da nur Urheber verifizierten Contents registrieren können. Benutzer kann auf alle ihre registrierten Web-zu-app-Hyperlinks überprüfen, indem Sie zu Einstellungen > Apps > Apps für Websites.

Um Web-zu-app Verlinkung zu aktivieren müssen:
- Identifizieren Sie die URIs, die Ihrer App in der Manifestdatei behandeln wird.
- Eine JSON-Datei, die Zuordnung zwischen Ihrer app und Ihre Website definiert. mit dem app-Paketfamiliennamen ein, im selben Stammverzeichnis wie die app-manifest Deklaration.
- Behandeln Sie die Aktivierung in der App

> [!Note]
> Ab Windows 10 Creators Update, wird unterstützten Links in Microsoft Edge geklickt die entsprechende app gestartet. Unterstützte Links, die in anderen Browsern (z. B. Internet Explorer usw.), geklickt hat, die Sie in das Browsen beibehalten wird.

## <a name="register-to-handle-http-and-https-links-in-the-app-manifest"></a>Registrieren Sie sich, um HTTP- und Https-Links im App-Manifest zu behandeln.

Ihre App muss die URIs für die Websites zu identifizieren, die sie behandeln soll. Fügen Sie hierzu die **Windows.appUriHandler** Erweiterung Registrierung zu Ihrer app-Manifestdatei hinzu **Package.appxmanifest**.

Wenn beispielsweise die Adresse Ihrer Website "msn.com" lautet, würden Sie den folgenden Eintrag in Ihrem App-Manifest machen:

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

Die obige Deklaration registriert Ihre App zur Behandlung von Links vom angegebenen Host. Wenn Ihre Website mehrere Adressen hat (z. B.: m.example.com, www.example.com und example.com), fügen Sie einen separaten `<uap3:Host Name=... />` Eintrag innerhalb des `<uap3:AppUriHandler>` für die einzelnen Adressen hinzu.

## <a name="associate-your-app-and-website-with-a-json-file"></a>Verknüpfen Sie Ihre App und die Website mit einer JSON-Datei

Um sicherzustellen, dass nur Ihre App die Inhalte auf Ihrer Website öffnen kann, sollten Sie den Paketfamiliennamen Ihrer App in eine JSON-Datei einbinden, die auf dem Webserver-Stammverzeichnis oder in einem bekannten Verzeichnis der Domäne liegt. Dies bedeutet, dass Ihre Website die Zustimmung gibt, dass die aufgeführten Apps Inhalte auf Ihrer Website öffnen können. Sie können den Paketfamiliennamen im Packages-Abschnitt Pakete des App-Manifest-Designers finden.

>[!Important]
> Die JSON-Datei sollte kein .json Dateisuffix aufweisen.

Erstellen Sie eine JSON-Datei (ohne die Erweiterung .json) mit dem Namen **Windows-App-Web-Link** und stellen Sie den Paketfamiliennamen Ihrer App bereit. Beispiel:

``` JSON
[{
  "packageFamilyName": "Your app's package family name, e.g MyApp_9jmtgj1pbbz6e",
  "paths": [ "*" ],
  "excludePaths" : [ "/news/*", "/blog/*" ]
 }]
```

Windows wird eine Https-Verbindung mit Ihrer Website herstellen und nach der entsprechenden JSON Datei auf dem Webserver suchen.

### <a name="wildcards"></a>Platzhalter

Das obige für eine JSON-Datei veranschaulicht die Verwendung von Platzhaltern. Platzhalter erlauben es Ihnen eine Vielzahl von Links mit weniger Codezeilen zu unterstützen. Die Web-zu-App-Verknüpfung unterstützt zwei Arten von Platzhaltern in der JSON-Datei:

| **Platzhalter** | **Beschreibung**               |
|--------------|-------------------------------|
| **\***       | Repräsentiert eine beliebige Teilzeichenfolge      |
| **?**        | Steht für ein einzelnes Zeichen |

Angenommen, `"excludePaths" : [ "/news/*", "/blog/*" ]` im obigen Beispiel wird Ihre app alle Pfade, die mit **Ihrer Website Adresse (z. B. msn.com)** Pfade unter beginnen unterstützen `/news/` und `/blog/`. **msn.com/weather.html** wird unterstützt, aber nicht ****msn.com/news/topnews.html****.

### <a name="multiple-apps"></a>Mehrere Apps

Wenn Sie zwei Apps haben, die Sie mit Ihrer Website verknüpfen möchten, listen Sie beide Paketfamiliennamen der Apps in der **Windows-App-Web-Link** JSON-Datei auf. Beide Apps können unterstützt werden. Dem Benutzer wird eine Auswahl für den Standardlink angezeigt, wenn beide Apps installiert sind. Falls sie den Standardlink später ändern möchten, können ändern sie ihn unter **Einstellungen > Apps für Websites** ändern. Entwickler können auch die JSON-Datei jederzeit ändern und die Änderung noch am selben Tag, aber bis spätestens acht Tage nach dem Update einsehen.

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

Um Ihren Benutzern die bestmögliche Erfahrung zu bieten, verwenden Sie Ausschlusspfade, um sicherzustellen, dass der nur online verfügbare Inhalt von den unterstützten Pfaden in der JSON-Datei ausgenommen ist.

Ausschlusspfade werden zuerst überprüft, und wenn eine Übereinstimmung vorliegt wird die entsprechende Seite mit dem Browser anstelle der angegebenen App geöffnet. Im obigen Beispiel enthält "/ News / \ *" alle Seiten unter diesem Pfad, während "/ News\ *" (keine vorwärts-Slash "news") Pfade unter "News\ *" wie "Newslocal /", "Newsinternational /" usw.. enthält.

## <a name="handle-links-on-activation-to-link-to-content"></a>Behandeln Sie Links auf Aktivierung, um Links mit Inhalt zu verbinden.

Navigieren Sie zu **App.xaml.cs** in der Visual Studio Lösung für Ihrer App und fügen Sie in **OnActivated()** die Behandlung für verknüpfte Inhalte hinzu. Im folgenden Beispiel hängt die Seite, die in der App geöffnet wird, vom URI-Pfad ab:

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

**Wichtig** Stellen Sie sicher, dass das finale `if (rootFrame.Content == null)` logic durch `rootFrame.Navigate(deepLinkPageType, e);` ersetzt wird, wie im obigen Beispiel gezeigt wird.

## <a name="test-it-out-local-validation-tool"></a>Testen Sie: Lokales Überprüfungswerkzeug

Sie können die Konfiguration Ihrer App und Website durch Ausführen des App-Host Registration Verifier Werkzeugs prüfen, der hier verfügbar ist:

%windir%\\system32\\**AppHostRegistrationVerifier.exe**

Testen Sie die Konfiguration Ihrer App und, indem Sie dieses Werkzeug mit folgenden Parametern ausführen.

**AppHostRegistrationVerifier.exe** *hostname packagefamilyname filepath*

-   Hostname: Ihre Website (z. B. microsoft.com)
-   Paketfamiliennamen (PFN): Ihre App-PFN
-   Dateipfad: die JSON-Datei für die lokale Überprüfung (z. B. C:\\SomeFolder\\windows-App-Web-link)

Wenn das Tool keine nichts zurückgibt, funktioniert die Überprüfung für diese Datei beim Hochladen. Wenn ein Fehlercode vorhanden ist, wird es nicht funktionieren.

Sie können den folgenden Registrierungsschlüssel zwingen Pfad Abgleich für quergeladene apps als Teil des lokalen Überprüfung aktivieren:

`HKCU\Software\Classes\LocalSettings\Software\Microsoft\Windows\CurrentVersion\
AppModel\SystemAppData\YourApp\AppUriHandlers`

Schlüsselname: `ForceValidation` Wert: `1`

## <a name="test-it-web-validation"></a>Testen Sie es: Web-Überprüfung

Schließen Sie die Anwendung, um sicherzustellen, dass die App aktiviert wird, wenn Sie auf einen Link klicken. Kopieren Sie dann die Adresse eines unterstützten Pfades in Ihrer Website. Wenn Ihre Websiteadresse beispielsweise "msn.com" lautet, und einer der unterstützen Pfade "path1" ist, verwenden Sie `http://msn.com/path1`

Stellen Sie sicher, dass Ihre app geschlossen ist. Drücken Sie die **Windows-Taste + R** zum Öffnen des **ausführen**-Dialogfelds fügen Sie den Link im Fenster ein. Ihre app sollte anstelle des Webbrowsers gestartet werden.

Darüber hinaus können Sie Ihre App testen, indem Sie sie über eine andere app mithilfe der [LaunchUriAsync](https://msdn.microsoft.com/library/windows/apps/hh701480.aspx) API starten. Diese API können auch Sie nutzen, um dies auf Telefonen zu testen.

Wenn Sie der protocol activation logic zu folgen möchten, legen Sie einen Haltepunkt im **OnActivated** -Ereignishandler fest.

## <a name="appurihandlers-tips"></a>AppUriHandlers Tipps:

- Stellen Sie sicher, dass Sie nur Links angeben, die mit Ihrer App kompatibel sind.
- Listen Sie alle Hosts auf, die Sie unterstützen werden.  Beachten Sie, dass www.example.com und example.com verschiedene Hosts sind.
- Benutzer können in den Einstellungen auswählen, welche App sie zum Öffnen von Websites bevorzugen.
- Ihre JSON-Datei muss auf einen Https-Server hochgeladen werden.
- Wenn Sie die Pfade, die Sie unterstützen möchten, ändern müssen, können Sie JSON-Datei erneut hochladen, ohne Ihre App erneut veröffentlichen zu müssen. Benutzern wird die Änderungen in 1 bis 8 Tagen angezeigt.
- Alle quergeladenen Apps mit AppUriHandlern werden validierte Links für den Host on Install haben Sie müssen kein JSON-Datei hochgeladen haben, um das Feature zu testen.
- Dieses Feature funktioniert, wann immer Ihre App eine UWP-App ist, die mit  [LaunchUriAsync](https://msdn.microsoft.com/library/windows/apps/hh701480.aspx) gestartet ist, oder eine Windows-Desktop-App, gestartet mit  [ShellExecuteEx](https://msdn.microsoft.com/library/windows/desktop/bb762154(v=vs.85).aspx). Wenn die URL einen registrierten URI App Handler entspricht, wird die App anstelle des Browsers gestartet werden.

## <a name="see-also"></a>Siehe auch

[Web-zu-App-Beispielprojekt](https://github.com/project-rome/AppUriHandlers/tree/master/NarwhalFacts)
[windows.protocol-Registrierung](https://msdn.microsoft.com/library/windows/apps/br211458.aspx)
[Behandeln der URI-Aktivierung](https://msdn.microsoft.com/windows/uwp/launch-resume/handle-uri-activation)
[Zuordnung starten Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AssociationLaunching) veranschaulicht, wie Sie des LaunchUriAsync() API.
