---
author: TylerMSFT
title: Starten der Einstellungs-App von Windows
description: Erfahren Sie, wie Sie die Windows-Einstellungs-App aus Ihrer App starten können. In diesem Thema wird das ms-settings-URI-Schema beschrieben. Verwenden Sie dieses URI-Schema, um die Windows-Einstellungs-App mit bestimmten Einstellungsseiten zu starten.
ms.assetid: C84D4BEE-1FEE-4648-AD7D-8321EAC70290
ms.author: twhitney
ms.date: 03/20/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 00baa088f0cb01068f1d1d78d101e6cd294c77f7
ms.sourcegitcommit: 82c3fc0b06ad490c3456ad18180a6b23ecd9c1a7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2018
ms.locfileid: "5476414"
---
# <a name="launch-the-windows-settings-app"></a>Starten der Windows-Einstellungs-App


**Wichtige APIs**

-   [**LaunchUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701476)
-   [**PreferredApplicationPackageFamilyName**](https://msdn.microsoft.com/library/windows/apps/hh965482)
-   [**DesiredRemainingView**](https://msdn.microsoft.com/library/windows/apps/dn298314)

Erfahren Sie, wie Sie die Einstellungs-App von Windows starten. In diesem Thema wird das **ms-settings:**-URI-Schema beschrieben. Verwenden Sie dieses URI-Schema, um die Windows-Einstellungs-App mit bestimmten Einstellungsseiten zu starten.

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

Alternativ kann Ihre App die [**LaunchUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701476)-Methode aufrufen, um die **Einstellungs**-App zu starten. In diesem Beispiel wird gezeigt, wie die Datenschutzeinstellungsseite für die Kamera mit dem `ms-settings:privacy-webcam`-URI gestartet werden kann.

```cs
bool result = await Windows.System.Launcher.LaunchUriAsync(new Uri("ms-settings:privacy-webcam"));
```

Der eben gezeigte Code startet die Datenschutzeinstellungsseite für die Kamera:

![Datenschutzeinstellungen für die Kamera.](images/privacyawarenesssettingsapp.png)

Weitere Informationen zum Starten von URIs finden Sie unter [Starten der Standard-App für einen URI](launch-default-app.md).

## <a name="ms-settings-uri-scheme-reference"></a>ms-settings: URI-Schemareferenz

Verwenden Sie die folgenden URIs, um verschiedenen Seiten der Einstellungs-App zu öffnen.

> Hinweis: ob die Seite "Einstellungen" verfügbar ist, variiert je nach Windows-SKU. Nicht alle Einstellungsseiten von Windows10 für Desktop sind für Windows10 Mobile verfügbar und umgekehrt. Der Bereich „Anmerkungen” in dieser Spalte erfasst auch zusätzliche Anforderungen, die erfüllt sein müssen, damit eine Seite zur Verfügung steht.

## <a name="accounts"></a>Konten

|Seite „Einstellungen“| URI |
|-------------|-----|
| Geschäfts- oder Schulkonto öffnen | ms-settings:workplace |
| E-Mail- & App-Konten  | ms-settings:emailandaccounts |
| Familie und andere Personen | ms-settings:otherusers |
| Anmeldeoptionen | ms-settings:signinoptions<br>ms-settings:signinoptions-dynamiclock |
| Einstellungen synchronisieren | ms-settings:sync |
| Einrichten von Windows Hello | ms-settings:signinoptions-launchfaceenrollment<br>ms-settings:signinoptions-launchfingerprintenrollment |
| Ihre Informationen | ms-settings:yourinfo |

## <a name="apps"></a>Apps

|Seite „Einstellungen“| URI |
|-------------|-----|
| Apps & Features | ms-settings:appsfeatures |
| App-Features | ms-settings:appsfeatures-app (Zusätzliche und heruntergeladene Inhalte für die App zurücksetzen, verwalten etc.)|
| Apps für Websites | ms-settings:appsforwebsites |
| Standard-Apps | ms-settings:defaultapps |
| Optionale Funktionen verwalten | ms-settings:optionalfeatures |
| Offlinekarten | ms-settings:maps |
| Startup-Apps | ms-settings:startupapps |
| Videowiedergabe | ms-settings:videoplayback |

## <a name="cortana"></a>Cortana

|Seite „Einstellungen“| URI |
|-------------|-----|
| Berechtigungen und-Verlauf | ms-settings:cortana-permissions |
| Weitere Details | ms-settings:cortana-moredetails |
| Cortana für meine Geräte | ms-settings:cortana-notifications |
| Sprechen mit Cortana | ms-settings:cortana-language |

> [!NOTE] 
> In diesem Abschnitt Einstellungen auf dem Desktop wird Suche aufgerufen werden, wenn der PC, Regionen gesetzt ist, in denen Cortana ist derzeit nicht verfügbar oder Cortana deaktiviert wurde. Cortana-spezifische Seiten (Cortana für meine Geräte) und sprechen Sie mit Cortana werden in diesem Fall nicht aufgeführt. 

## <a name="devices"></a>Geräte

|Seite „Einstellungen“| URI |
|-------------|-----|
| Audio und Sprache | ms-settings:holographic-audio (nur verfügbar, wenn das App Mixed Reality-Portal installiert ist – verfügbar im Microsoft Store) |
| Automatische Wiedergabe | ms-settings:autoplay |
| Bluetooth | ms-settings:bluetooth |
| Verbundene Geräte | ms-settings:connecteddevices |
| Standardkamera | ms-settings:camera |
| Maus und Touchpad | ms-settings:mousetouchpad (Touchpadeinstellungen nur auf Geräten mit Touchpad verfügbar) |
| Stift & Windows Ink | ms-settings:pen |
| Drucker und Scanner | ms-settings:printers |
| Touchpad | ms-settings:devices-touchpad (Touchpadeinstellungen nur auf Geräten mit Touchpad verfügbar) |
| Tippen | ms-settings:typing |
| USB | ms-settings:usb |
| Rad | ms-settings:wheel (nur verfügbar, wenn das Rad gekoppelt ist) |
| Ihr Smartphone | ms-settings:mobile-devices  |

## <a name="ease-of-access"></a>Erleichterte Bedienung

|Seite „Einstellungen“| URI |
|-------------|-----|
| Audio | ms-settings:easeofaccess-audio |
| Untertitel | ms-settings:easeofaccess-closedcaptioning |
| Farbe Filter | MS-Settings: Easeofaccess-Colorfilter |
| Anzeige | ms-settings:easeofaccess-display |
| Augensteuerung | ms-settings:easeofaccess-eyecontrol |
| Schriftarten | ms-settings:fonts |
| Hoher Kontrast | ms-settings:easeofaccess-highcontrast |
| Holografisches Headset | ms-settings:holographic-headset (holografische Hardware erforderlich) |
| Keyboard | ms-settings:easeofaccess-keyboard |
| Bildschirmlupe | ms-settings:easeofaccess-magnifier |
| Maus | ms-settings:easeofaccess-mouse |
| Sprachausgabe | ms-settings:easeofaccess-narrator |
| Andere Optionen | ms-settings:easeofaccess-otheroptions |
| Sprache | ms-settings:easeofaccess-speechrecognition |

## <a name="extras"></a>Extras

|Seite „Einstellungen“| URI |
|-------------|-----|
| Extras | ms-settings:extras (nur verfügbar, wenn "Apps-Einstellungen" installiert sind (z.B. von Drittanbietern) |

## <a name="gaming"></a>Gaming

|Seite „Einstellungen“| URI |
|-------------|-----|
| Senden | ms-settings:gaming-broadcasting |
| Spieleleiste | ms-settings:gaming-gamebar |
| Game DVR | ms-settings:gaming-gamedvr |
| Spielmodus | ms-settings:gaming-gamemode |
| Ein Spiel im Vollbildmodus wiedergeben | ms-settings:quietmomentsgame |
| TruePlay | ms-settings:gaming-trueplay |
| Xbox Netzwerk | ms-settings:gaming-xboxnetworking |

## <a name="home-page"></a>Startseite

|Seite „Einstellungen“| URI |
|-------------|-----|
| Startseite „Einstellungen“ | ms-settings: |


## <a name="network--internet"></a>Netzwerk und Internet

|Seite „Einstellungen“| URI |
|-------------|-----|
| Flugzeugmodus | ms-settings:network-airplanemode (ms-settings:proximity unter Windows 8.x verwenden) |
| Mobilfunk und SIM | ms-settings:network-cellular |
| Datennutzung | ms-settings:datausage |
| DFÜ-Verbindung | ms-settings:network-dialup |
| DirectAccess | ms-Settings:network-directaccess (nur verfügbar, wenn die DirectAccess aktiviert ist) |
| Ethernet | ms-settings:network-ethernet |
| Bekannte Netzwerke verwalten | ms-settings:network-wifisettings |
| Mobiler Hotspot | ms-settings:network-mobilehotspot |
| NFC | ms-settings:nfctransactions |
| Proxy | ms-settings:network-proxy |
| Status | ms-settings:network-status |
| VPN | ms-settings:network-vpn |
| WLAN | ms-settings:network-wifi (nur verfügbar, wenn das Gerät über einen WLAN-Adapter verfügt) |
| WLAN-Anruf | ms-settings:network-wificalling (nur verfügbar, wenn WLAN-Anruf aktiviert ist) |

## <a name="personalization"></a>Personalisierung

|Seite „Einstellungen“| URI |
|-------------|-----|
| Hintergrund | ms-settings:personalization-background |
| Ordner auswählen, die im Menü „Start“ angezeigt werden | ms-settings:personalization-start-places |
| Farben | ms-settings:personalization-colors |
| Blick | ms-settings:personalization-glance |
| Sperrbildschirm | ms-settings:lockscreen |
| Navigationsleiste | ms-settings:personalization-navbar |
| Personalisierung (Kategorie) | ms-settings:personalization |
| Start | ms-settings:personalization-start |
| Taskleiste | ms-settings:taskbar |
| Designs | ms-settings:themes |

## <a name="phone"></a>Phone

|Seite „Einstellungen“| URI |
|-------------|-----|
| Ihr Smartphone | ms-settings:mobile-devices  |

## <a name="privacy"></a>Privatsphäre

|Seite „Einstellungen“| URI |
|-------------|-----|
| Zubehör-Apps | ms-settings:privacy-accessoryapps |
| Kontoinformationen | ms-settings:privacy-accountinfo |
| Aktivitätsverlauf | ms-settings:privacy-activityhistory |
| Werbe-ID | ms-settings:privacy-advertisingid |
| App-Diagnose | ms-settings:privacy-appdiagnostics |
| Automatische Dateidownloads | ms-settings:privacy-automaticfiledownloads |
| Hintergrund-Apps | ms-settings:privacy-backgroundapps |
| Kalender | ms-settings:privacy-calendar |
| Anrufliste | ms-settings:privacy-callhistory |
| Kamera | ms-settings:privacy-webcam |
| Kontakte | ms-settings:privacy-contacts |
| Dokumente | ms-settings:privacy-documents |
| E-Mail | ms-settings:privacy-email |
| Eyetracker | ms-settings:privacy-eyetracker (Eyetracker-Hardware erforderlich) |
| Feedback und Diagnose | ms-settings:privacy-feedback |
| Dateisystem | ms-settings:privacy-broadfilesystemaccess |
| Allgemein | ms-settings:privacy-general |
| Ort | ms-settings:privacy-location |
| Microsoft-Nachrichten | ms-settings:privacy-messaging |
| Mikrofon | ms-settings:privacy-microphone |
| Bewegung | ms-settings:privacy-motion |
| Benachrichtigungen | ms-settings:privacy-notifications |
| Weitere Geräte | ms-settings:privacy-customdevices |
| Bilder | ms-settings:privacy-pictures |
| Telefonanrufe | ms-settings:privacy-phonecall |
| Funkempfang | ms-settings:privacy-radios |
| Spracherkennung, Freihand und Eingabe |ms-settings:privacy-speechtyping |
| Aufgaben | ms-settings:privacy-tasks |
| Videos | ms-settings:privacy-videos |

## <a name="surface-hub"></a>Surface Hub

|Seite „Einstellungen“| URI |
|-------------|-----|
| Konten | ms-settings:surfacehub-accounts |
| Bereinigung der Sitzung | ms-settings:surfacehub-sessioncleanup |
| Team-Konferenz | ms-settings:surfacehub-calling |
| Team-Geräteverwaltung | ms-settings:surfacehub-devicemanagenent |
| Willkommensseite | ms-settings:surfacehub-welcome |

## <a name="system"></a>System

|Seite „Einstellungen“| URI |
|-------------|-----|
| Info | ms-settings:about |
| Erweiterte Anzeigeeinstellungen | ms-settings:display-advanced (nur verfügbar auf Geräten, die erweiterte Anzeigeeinstellungen) |
| Stromsparmodus | ms-settings:batterysaver (nur verfügbar auf Geräten mit Akku, z.B. Tablets) |
| Einstellungen „Stromsparmodus” | ms-settings:batterysaver-settings (nur verfügbar auf Geräten mit Akku, z.B. Tablets) |
| Akkubetrieb | ms-settings:batterysaver-usagedetails (nur verfügbar auf Geräten mit Akku, z.B. Tablets) |
| Anzeige | ms-settings:display |
| Standard-Speicherorte | ms-settings:savelocations |
| Anzeige | ms-settings:screenrotation |
| Duplizieren meines Bildschirms | ms-Settings:quietmomentspresentation |
| Zu dieser Zeit | ms-settings:quietmomentsscheduled |
| Verschlüsselung | ms-settings:deviceencryption |
| Fokus-Assist | ms-settings:quiethours <br> ms-settings:quietmomentshome |
| Einstellungen für Grafiken | ms-settings:display-advancedgraphics (nur verfügbar auf Geräten, die erweiterte Anzeigeeinstellungen) |
| Microsoft-Nachrichten | ms-settings:messaging |
| Multitasking | ms-settings:multitasking |
| Einstellungen „Nachtmodus” | ms-settings:nightlight |
| Telefon | ms-settings:phone-defaultapps |
| Projizieren auf diesen PC | ms-settings:project |
| Gemeinsame Erfahrung | ms-settings:crossdevice |
| Tabletmodus | ms-settings:tabletmode |
| Taskleiste | ms-settings:taskbar |
| Benachrichtigungen & Infos | ms-settings:notifications |
| Remotedesktop | Einstellungen „Remotedesktop” |
| Telefon | ms-settings:phone |
| Ein/Aus und Standbymodus | ms-settings:powersleep |
| Sounds | ms-settings:sounds |
| Speicher | ms-settings:storagesense |
| Speicheroptimierung | ms-settings:storagepolicies |

## <a name="time-and-language"></a>Zeit und Sprache

|Seite „Einstellungen“| URI |
|-------------|-----|
| Datum und Uhrzeit | ms-settings:dateandtime |
| Japan IME-Einstellungen | ms-settings:regionlanguage-jpnime (nur verfügbar, wenn der Eingabemethodeneditor „Microsoft Japan” installiert ist) |
| Pinyin-IME-Einstellungen | ms-settings:regionlanguage-chsime-pinyin (nur verfügbar, wenn der Eingabemethodeneditor „Microsoft Pinyin” installiert ist) |
| Region & Sprache | ms-settings:regionlanguage |
| Spracherkennungssprache | ms-settings:speech |
| Wubi-IME-Einstellungen  | ms-settings:regionlanguage-chsime-wubi (nur verfügbar, wenn der Eingabemethodeneditor „Microsoft Wubi” installiert ist) |

## <a name="update--security"></a>Update und Sicherheit

|Seite „Einstellungen“| URI |
|-------------|-----|
| Aktivierung | ms-settings:activation |
| Sicherung | ms-settings:backup |
| Übermittlungsoptimierung | ms-settings:delivery-optimization |
| Mein Gerät suchen | ms-settings:findmydevice |
| Für Entwickler | ms-settings:developers |
| Wiederherstellung | ms-settings:recovery |
| Problembehandlung | ms-settings:troubleshoot |
| Windows-Sicherheit | ms-settings:windowsdefender |
| Windows-Insider-Programm | ms-settings:windowsinsider (nur verfügbar, wenn der Benutzer bei WIP registriert ist) |
| Windows Update | ms-settings:windowsupdate<br>ms-settings:windowsupdate-action |
| Windows Update-Advanced options | ms-settings:windowsupdate-options |
| Windows Update-Restart options | ms-settings:windowsupdate-restartoptions |
| Windows-Update – Updateverlauf anzeigen | ms-settings:windowsupdate-history |

## <a name="user--accounts"></a>Benutzerkonten

|Seite „Einstellungen“| URI |
|-------------|-----|
| Bereitstellung | ms-settings:workplace-provisioning (nur verfügbar, wenn das Unternehmen ein Bereitstellungspaket bereitgestellt hat) |
| Bereitstellung | ms-settings:provisioning (nur mobil verfügbar und nur, wenn das Unternehmen ein Bereitstellungspaket bereitgestellt hat) |
| Windows Anywhere | ms-settings:windowsanywhere (Gerät muss Windows Anywhere-fähig sein) |
