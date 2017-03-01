---
author: TylerMSFT
title: Starten der Einstellungs-App von Windows
description: "Erfahren Sie, wie Sie die Windows-Einstellungs-App aus Ihrer App starten können. In diesem Thema wird das ms-settings-URI-Schema beschrieben. Verwenden Sie dieses URI-Schema, um die Windows-Einstellungs-App mit bestimmten Einstellungsseiten zu starten."
ms.assetid: C84D4BEE-1FEE-4648-AD7D-8321EAC70290
ms.author: twhitney
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: e4cc17bf268ddb470c3c64dfe3e471053d8fca55
ms.lasthandoff: 02/07/2017

---

# <a name="launch-the-windows-settings-app"></a>Starten der Windows-Einstellungs-App

\[ Aktualisiert für UWP-Apps unter Windows 10. Artikel zu Windows 8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]

**Wichtige APIs**

-   [**LaunchUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701476)
-   [**PreferredApplicationPackageFamilyName**](https://msdn.microsoft.com/library/windows/apps/hh965482)
-   [**DesiredRemainingView**](https://msdn.microsoft.com/library/windows/apps/dn298314)

Erfahren Sie, wie Sie die Windows-Einstellungs-App aus Ihrer App starten können. In diesem Thema wird das **ms-settings:**-URI-Schema beschrieben. Verwenden Sie dieses URI-Schema, um die Windows-Einstellungs-App mit bestimmten Einstellungsseiten zu starten.

Das Starten der Einstellungs-App ist ein wichtiger Bestandteil beim Schreiben einer datenschutzbewussten App. Wenn Ihre App nicht auf eine sensible Ressource zugreifen kann, wird empfohlen, dem Benutzer einen praktischen Link zu den Datenschutzeinstellungen für diese Ressource bereitzustellen. Weitere Informationen finden Sie unter [Richtlinien für Apps mit Berücksichtigung von Datenschutz](https://msdn.microsoft.com/library/windows/apps/hh768223).

## <a name="how-to-launch-the-settings-app"></a>So starten Sie die Einstellungs-App

Um die **Einstellungs**-App zu starten, verwenden Sie das in den folgenden Beispielen beschriebene URI-Schema `ms-settings:`.

In diesem Beispiel wird ein Hyperlink-XAML-Steuerelement verwendet, um die Datenschutzeinstellungsseite für das Mikrofon mit der `ms-settings:privacy-microphone`-URI zu starten.

```xml
<!--Set Visibility to Visible when access to the microphone is denied -->  
<TextBlock x:Name="LocationDisabledMessage" FontStyle="Italic"
                 Visibility="Collapsed" Margin="0,15,0,0" TextWrapping="Wrap" >
          <Run Text="This app is not able to access the microphone. Go to " />
              <Hyperlink NavigateUri="ms-settings:privacy-microphone">
                  <Run Text="Settings" />
              </Hyperlink>
          <Run Text=" to check the microphone privacy settings."/>
</TextBlock>
```

Alternativ kann Ihre App die [**LaunchUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701476)-Methode aufrufen, um die **Einstellungs**-App per Code zu starten. In diesem Beispiel wird gezeigt, wie die Datenschutzeinstellungsseite für die Kamera mit dem `ms-settings:privacy-webcam`-URI gestartet werden kann.

```cs
bool result = await Windows.System.Launcher.LaunchUriAsync(new Uri("ms-settings:privacy-webcam"));
```

Der eben gezeigte Code startet die Datenschutzeinstellungsseite für die Kamera:

![Datenschutzeinstellungen für die Kamera.](images/privacyawarenesssettingsapp.png)

Weitere Informationen zum Starten von URIs finden Sie unter [Starten der Standard-App für einen URI](launch-default-app.md).

## <a name="ms-settings-uri-scheme-reference"></a>ms-settings: URI-Schemareferenz

Verwenden Sie die folgenden URIs, um verschiedenen Seiten der Einstellungs-App zu öffnen. Beachten Sie, dass in der Spalte „Unterstützte SKUs“ angegeben wird, ob die Einstellungsseite in Windows 10 für Desktopeditionen (Home, Pro, Enterprise und Education), Windows 10 Mobile oder beiden vorhanden ist.

<table border="1">
    <tr>
        <th>Kategorie</th>
        <th>Einstellungsseite</th>
        <th>Unterstützte SKUs</th>
        <th>URI</th>
    </tr>
    <tr>
        <td>Startseite</td>
        <td>Angebotsseite für Einstellungen</td>
        <td>Beide</td>
        <td>ms-settings:</td>
    </tr>
    <tr>
        <td rowspan="10">System</td>
        <td>Anzeige</td>
        <td>Beide</td>
        <td>ms-settings:screenrotation</td>
    </tr>
    <tr>
        <td>Benachrichtigungen & Infos</td>
        <td>Beide</td>
        <td>ms-settings:notifications</td>
    </tr>
    <tr>
        <td>Telefon</td>
        <td>nur Mobile</td>
        <td>ms-settings:phone</td>
    </tr>
    <tr>
        <td>Nachrichten</td>
        <td>Nur Mobile</td>
        <td>ms-settings:messaging</td>
    </tr>
    <tr>
        <td>Stromsparmodus</td>
        <td>Beide<br>Nur auf Geräten mit Akku verfügbar, z. B. Tablets</td>
        <td>ms-settings:batterysaver</td>
    </tr>
    <tr>
        <td>Akkubetrieb</td>
        <td>Beide<br>Nur auf Geräten mit Akku verfügbar, z. B. Tablets</td>
        <td>ms-settings:batterysaver-usagedetails</td>
    </tr>
    <tr>
        <td>Ein/Aus und Standbymodus</td>
        <td>Nur Desktop</td>
        <td>ms-settings:powersleep</td>
    </tr>
    <tr>
        <td>Info</td>
        <td>Beide</td>
        <td>ms-settings:about</td>
    </tr>
    <tr>
        <td>Verschlüsselung</td>
        <td>Beide</td>
        <td>ms-settings:deviceencryption</td>
    </tr>
    <tr>
        <td>Offlinekarten</td>
        <td>Beide</td>
        <td>ms-settings:maps</td>
    </tr>
    <tr>
        <td rowspan="4">Geräte</td>
        <td>Standardkamera</td>
        <td>Nur Mobile</td>
        <td>ms-settings:camera</td>
    </tr>
    <tr>
        <td>Bluetooth</td>
        <td>Nur Desktop</td>
        <td>ms-settings:bluetooth</td>
    </tr>
    <tr>
        <td>Verbundene Geräte</td>
        <td>Nur Desktop</td>
        <td>ms-settings:connecteddevices</td>
    </tr>
    <tr>
        <td>Maus und Touchpad</td>
        <td>Beide<br>Touchpadeinstellungen nur auf Geräten mit Touchpad verfügbar</td>
        <td>ms-settings:mousetouchpad</td>
    </tr>
    <tr>
        <td rowspan="3">Netzwerk und WLAN</td>
        <td>NFC</td>
        <td>Beide</td>
        <td>ms-settings:nfctransactions</td>
    </tr>
    <tr>
        <td>WLAN</td>
        <td>Beide</td>
        <td>ms-settings:network-wifi</td>
    </tr>
    <tr>
        <td>Flugzeugmodus</td>
        <td>Beide</td>
        <td>ms-settings:network-airplanemode</td>
    </tr>
    <tr>
        <td rowspan="5">Netzwerk und Internet</td>
        <td>Datennutzung</td>
        <td>Beide</td>
        <td>ms-settings:datausage</td>
    </tr>
    <tr>
        <td>Mobilfunk und SIM</td>
        <td>Beide</td>
        <td>ms-settings:network-cellular</td>
    </tr>
    <tr>
        <td>Mobiler Hotspot</td>
        <td>Beide</td>
        <td>ms-settings:network-mobilehotspot</td>
    </tr>
    <tr>
        <td>Proxy</td>
        <td>Nur Desktop</td>
        <td>ms-settings:network-proxy</td>
    </tr>
    <tr>
        <td>Status</td>
        <td>Nur Desktop</td>
        <td>ms-settings:network-status</td>
    </tr>
    <tr>
        <td rowspan="5">Personalisierung</td>
        <td>Personalisierung (Kategorie)</td>
        <td>Beide</td>
        <td>ms-settings:personalization</td>
    </tr>
    <tr>
        <td>Hintergrund</td>
        <td>nur Desktop</td>
        <td>ms-settings:personalization-background</td>
    </tr>
    <tr>
        <td>Farben</td>
        <td>Beide</td>
        <td>ms-settings:personalization-colors</td>
    </tr>
    <tr>
        <td>Sounds</td>
        <td>nur Mobile </td>
        <td>ms-settings:sounds</td>
    </tr>
    <tr>
        <td>Sperrbildschirm</td>
        <td>Beide</td>
        <td>ms-settings:lockscreen</td>
    </tr>
    <tr>
        <td rowspan="7">Konten</td>
        <td>Geschäfts- oder Schulkonto öffnen</td>
        <td>Beide</td>
        <td>ms-settings:workplace</td>
    </tr>
    <tr>
        <td>E-Mail- & App-Konten</td>
        <td>Beide</td>
        <td>ms-settings:emailandaccounts</td>
    </tr>
    <tr>
        <td>Familie und andere Personen</td>
        <td>Beide</td>
        <td>ms-settings:otherusers</td>
    </tr>
    <tr>
        <td>Anmeldeoptionen</td>
        <td>Beide</td>
        <td>ms-settings:signinoptions</td>
    </tr>
    <tr>
        <td>Synchronisieren von Einstellungen</td>
        <td>Beide</td>
        <td>ms-settings:sync</td>
    </tr>
    <tr>
        <td>Andere Personen</td>
        <td>Beide</td>
        <td>ms-settings:otherusers</td>
    </tr>
    <tr>
        <td>Ihre Informationen</td>
        <td>Beide</td>
        <td>ms-settings:yourinfo</td>
    </tr>
    <tr>
        <td rowspan="2">Zeit und Sprache</td>
        <td>Datum und Uhrzeit</td>
        <td>Beide</td>
        <td>ms-settings:dateandtime</td>
    </tr>
    <tr>
        <td>Region & Sprache</td>
        <td>nur Desktop</td>
        <td>ms-settings:regionlanguage</td>
    </tr>
    <tr>
        <td rowspan="7">Erleichterte Bedienung</td>
        <td>Sprachausgabe</td>
        <td>Beide</td>
        <td>ms-settings:easeofaccess-narrator</td>
    </tr>
    <tr>
        <td>Bildschirmlupe</td>
        <td>Beide</td>
        <td>ms-settings:easeofaccess-magnifier</td>
    </tr>
    <tr>
        <td>Hoher Kontrast </td>
        <td>Beide</td>
        <td>ms-settings:easeofaccess-highcontrast</td>
    </tr>
    <tr>
        <td>Untertitel</td>
        <td>Beide</td>
        <td>ms-settings:easeofaccess-closedcaptioning</td>
    </tr>
    <tr>
        <td>Tastatur</td>
        <td>Beide</td>
        <td>ms-settings:easeofaccess-keyboard</td>
    </tr>
    <tr>
        <td>Maus</td>
        <td>Beide</td>
        <td>ms-settings:easeofaccess-mouse</td>
    </tr>
    <tr>
        <td>Weitere Optionen</td>
        <td>Beide</td>
        <td>ms-settings:easeofaccess-otheroptions</td>
    </tr>
    <tr>
        <td rowspan="15">Datenschutz</td>
        <td>Position</td>
        <td>Beide</td>
        <td>ms-settings:privacy-location</td>
    </tr>
    <tr>
        <td>Kamera</td>
        <td>Beide</td>
        <td>ms-settings:privacy-webcam</td>
    </tr>
    <tr>
        <td>Mikrofon</td>
        <td>Beide</td>
        <td>ms-settings:privacy-microphone</td>
    </tr>
    <tr>
        <td>Bewegung</td>
        <td>Beide</td>
        <td>ms-settings:privacy-motion</td>
    </tr>
    <tr>
        <td>Spracherkennung, Freihand und Eingabe</td>
        <td>Beide</td>
        <td>ms-settings:privacy-speechtyping</td>
    </tr>
    <tr>
        <td>Kontoinformationen</td>
        <td>Beide</td>
        <td>ms-settings:privacy-accountinfo</td>
    </tr>
    <tr>
        <td>Kontakte</td>
        <td>Beide</td>
        <td>ms-settings:privacy-contacts</td>
    </tr>
    <tr>
        <td>Kalender</td>
        <td>Beide</td>
        <td>ms-settings:privacy-calendar</td>
    </tr>
    <tr>
        <td>Anrufliste</td>
        <td>Beide</td>
        <td>ms-settings:privacy-callhistory</td>
    </tr>
    <tr>
        <td>E-Mail</td>
        <td>Beide</td>
        <td>ms-settings:privacy-email</td>
    </tr>
    <tr>
        <td>Nachrichten</td>
        <td>Beide</td>
        <td>ms-settings:privacy-messaging</td>
    </tr>
    <tr>
        <td>Funkempfang</td>
        <td>Beide</td>
        <td>ms-settings:privacy-radios</td>
    </tr>
    <tr>
        <td>Hintergrund-Apps</td>
        <td>Beide</td>
        <td>ms-settings:privacy-backgroundapps</td>
    </tr>
    <tr>
        <td>Weitere Geräte</td>
        <td>Beide</td>
        <td>ms-settings:privacy-customdevices</td>
    </tr>
    <tr>
        <td>Feedback und Diagnose</td>
        <td>Beide</td>
        <td>ms-settings:privacy-feedback</td>
    </tr>
    <tr>
        <td>Update und Sicherheit</td>
        <td>Für Entwickler</td>
        <td>Beide</td>
        <td>ms-settings:developers</td>
    </tr>
</table><br/>

