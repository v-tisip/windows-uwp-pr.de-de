---
author: PatrickFarley
ms.assetid: 60fc48dd-91a9-4dd6-a116-9292a7c1f3be
title: Übersicht über das Windows Device Portal
description: Hier erfahren Sie, wie Sie mit dem Windows Device Portal Ihr Gerät per Remotezugriff über ein Netzwerk oder eine USB-Verbindung konfigurieren und verwalten.
ms.author: pafarley
ms.date: 12/12/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Gerät portal
ms.localizationpriority: medium
ms.openlocfilehash: 08e7d8fcfbab0d0b22fffa3e3e0aecc38d5b095c
ms.sourcegitcommit: c6d6f8b54253e79354f8db14e5cf3b113a3e5014
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "2837215"
---
# <a name="windows-device-portal-overview"></a>Übersicht über das Windows Device Portal

Mit dem Windows Device Portal können Sie Ihr Gerät per Remotezugriff über ein Netzwerk oder eine USB-Verbindung konfigurieren und verwalten. Darüber hinaus erweiterte Diagnosetools zur einfacheren Problembehandlung und die Leistung in Echtzeit Ihr Windows-Gerät anzeigen.

Windows-Gerät Portal ist ein Webserver, auf dem Gerät, das Sie über einen Webbrowser auf einem PC verbinden können. Wenn das Gerät über einen Webbrowser verfügt, können Sie auch lokal mit dem Browser auf diesem Gerät verbinden.

Windows-Gerät Portal ist auf jedem Gerät-Produktfamilie verfügbar, aber Features und Setup unterschiedlich Anforderungen jedes Geräts. Dieser Artikel enthält eine allgemeine Beschreibung des Device Portals und Links zu Artikeln mit ausführlicheren Informationen für jede Gerätefamilie.

Die Funktionalität des Portals Gerät Windows wird mit [REST-APIs](device-portal-api-core.md) implementiert, die Sie direkt auf Daten zugreifen und Steuerung des Geräts programmgesteuert verwenden können.

## <a name="setup"></a>Setup

Für jedes Gerät gelten spezielle Anweisungen zum Herstellen der Verbindung mit dem Device Portal, diese allgemeinen Schritte sind jedoch für jedes Gerät erforderlich:
1. Aktivieren Sie auf dem Gerät (in der app Einstellungen konfiguriert) Entwicklermodus und Gerät Portal.
2. Verbinden Sie über ein lokales Netzwerk oder mit USB-Gerät und vom PC.
3. Navigieren Sie im Browser zu der Seite für das Geräteportal. Diese Tabelle zeigt die Ports und Protokolle, die von jedem Gerät-Produktfamilie verwendet.

Gerätefamilie | Standardmäßig aktiviert? | HTTP | HTTPS | USB
--------------|----------------|------|-------|----
HoloLens | Ja, im Entwicklermodus | 80 (Standard) | 443 (Standard) | http://127.0.0.1:10080
IoT | Ja, im Entwicklermodus | 8080 | Über Registrierungsschlüssel aktivieren | Nicht verfügbar
Xbox | Im Entwicklermodus aktivieren | Deaktiviert | 11443 | Nicht verfügbar
Desktop| Im Entwicklermodus aktivieren | 50080\* | 50043\* | Nicht verfügbar
Telefon | Im Entwicklermodus aktivieren | 80| 443 | http://127.0.0.1:10080

\ * Dies ist nicht stets der Fall, da Device Portal auf Desktops Ports in flüchtigen Bereich anfordert (> 50.000), um Konflikte mit vorhandenen Portanforderungen auf dem Gerät zu verhindern. Weitere Informationen hierzu finden Sie im Abschnitt zu [Porteinstellungen](device-portal-desktop.md#registry-based-configuration-for-device-portal) für den Desktop.  

Gerätespezifische Anweisungen zum Einrichten finden Sie in folgenden Artikeln:
- [Device Portal für HoloLens](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens)
- [Device Portal für IoT](https://go.microsoft.com/fwlink/?LinkID=616499)
- [Device Portal für Mobilgeräte](device-portal-mobile.md)
- [Device Portal für Xbox](device-portal-xbox.md)
- [Device Portal für Desktop](device-portal-desktop.md#set-up-device-portal-on-windows-desktop)

## <a name="features"></a>Features

### <a name="toolbar-and-navigation"></a>Symbolleiste und Navigation

Die Symbolleiste am oberen Rand der Seite bietet Zugriff auf häufig verwendete Funktionen.
- **Power**: Zugriff auf Energieoptionen.
  - **Herunterfahren**: Schaltet das Gerät aus.
  - **Neu starten**: Schaltet das Gerät aus und wieder ein.
- **Hilfe**: Öffnet die Hilfeseite.

Verwenden Sie die Links im Navigationsbereich am linken Rand der Seite, um zu den verfügbaren Verwaltungs- und Überwachungstools für Ihr Gerät zu navigieren.

Tools, die für gerätefamilien sind werden hier beschrieben. Je nach Gerät sind möglicherweise andere Optionen verfügbar. Weitere Informationen finden Sie unter die Seite für den Typ Ihres Geräts.

### <a name="apps-manager"></a>App-Manager

Der Manager Apps bietet installieren/deinstallieren und Management-Funktionen für die app verpackt und auf dem Host Gerät zusammengefasst.

![Gerät Portal Apps Manager-Seite](images/device-portal/wdp-apps.png)

- **Installierte apps**: Verwenden Sie im Dropdown-Menü zu entfernen, oder starten Sie apps, die auf dem Gerät installiert werden. Installieren Sie eine neue app, indem Sie auf **Hinzufügen**. Dadurch wird die Installation UX gepackte apps aus der lokalen Bereitstellung von initiiert, Netzwerk- oder Web gehostet wird und Registrieren von Netzwerkfreigaben lose Dateien.
- **Ausführen von apps**: Abrufen von Informationen über die apps, die derzeit ausgeführt werden, und schließen Sie sie nach Bedarf.

#### <a name="install-an-app"></a>Installieren einer App

1.  Wenn Sie ein App-Paket erstellt haben, können Sie es per Remotezugriff auf Ihrem Gerät installieren. Nachdem Sie es in Visual Studio erstellt haben, wird ein Ausgabeordner generiert.
  ![App-Installation](images/device-portal/iot-installapp0.png)
2.  Klicken Sie im Abschnitt für das Gerät Portal Apps-Manager klicken Sie auf **Hinzufügen** , und wählen Sie **app-Paket aus dem lokalen Speicher installieren**.
3.  Klicken Sie auf **Durchsuchen** , und suchen Sie nach Ihrer app-Paket.
3.  Klicken Sie auf **Durchsuchen** , und suchen Sie die Zertifikatdatei (._CER_) (nicht auf allen Geräten erforderlich.)
4.  Überprüfen Sie die entsprechenden Felder, wenn Sie optional installieren möchten oder Framework Pakete zusammen mit der app-Installation. Wenn mehrere vorhanden sind, fügen Sie jede einzeln hinzu.     
5.  Klicken Sie auf **Weiter** , um zum nächsten Schritt und **Installieren** zu verschieben, um die Installation zu initiieren. 

#### <a name="uninstall-an-app"></a>Deinstallieren einer App
1.  Stellen Sie sicher, dass die App nicht ausgeführt wird. 
2.  Wenn dies der Fall, wechseln Sie zum **Ausführen von apps** , und schließen sie. Wenn Sie versuchen, deinstallieren, solange die app ausgeführt wird, verursacht es Probleme, wenn Sie versuchen, die app zu installieren. 
3.  Wählen Sie die app aus der Dropdownliste aus, und klicken Sie auf **Entfernen**.

### <a name="running-processes"></a>Ausgeführte Prozesse

Diese Seite enthält Details zu Prozesse auf dem Host-Gerät. Diese umfassen Apps und Systemprozesse. Auf manchen Plattformen (Desktop, IoT und HoloLens) können Sie Prozesse beenden.

![Seite verarbeitet Gerät Portal ausgeführt.](images/device-portal/mob-device-portal-processes.png)

### <a name="file-explorer"></a>Datei-Explorer

Auf dieser Seite können Sie anzeigen und Bearbeiten von apps, die Sideloaded gespeicherte Dateien. Finden Sie im [Datei-Explorer die App verwenden](https://blogs.windows.com/buildingapps/2016/06/08/using-the-app-file-explorer-to-see-your-app-data/) Blogbeitrag, um weitere Informationen zu den Datei-Explorer und dessen Verwendung. 

![Seite für Geräte Portal Datei-explorer](images/device-portal/mob-device-portal-AppFileExplorer.png)

### <a name="performance"></a>Leistung

Auf der Seite Leistung zeigt in Echtzeit Diagrammen von Diagnoseinformationen wie Stromverbrauchs, Framerate, System, und Laden Sie CPU.

Die folgenden Metriken sind verfügbar:
- **CPU**: Prozent des gesamten verfügbaren CPU-Auslastung
- **Arbeitsspeicher**: insgesamt, verwendet, zur Verfügung, ein Commit ausgeführt, ausgelagerten und nicht ausgelagerten
- **E/a**: Lesen und schreiben Daten Mengen
- **Netzwerk**: empfangenen und gesendeten Daten
- **GPU**: % der gesamten verfügbaren GPU engine-Auslastung


![Gerät Portal Leistung Seite](images/device-portal/mob-device-portal-perf.png)

### <a name="event-tracing-for-windows-etw-logging"></a>Ereignisprotokollierung Tracing for Windows (ETW)

Die ETW-Protokollierung Seite verwaltet Event Tracing for Windows (ETW) Echtzeitinformationen auf dem Gerät.

![Seite für Geräte Portal ETW-Protokollierung](images/device-portal/mob-device-portal-etw.png)

Aktivieren Sie **Anbieter ausblenden**, um nur die Liste der Ereignisse anzuzeigen.
- **Registered-Anbieter**: Wählen Sie den Provider und die Protokollierungsstufe. Die Protokollierungsstufe hat einen der folgenden Werte:
  1. Abnormal exit or termination
  2. Severe errors
  3. Warnungen
  4. Non-error warnings
  5. Detaillierter Ablaufverfolgungsprotokolle

  Klicken oder tippen Sie auf **Aktivieren**, um die Ablaufverfolgung zu starten. Der Anbieter wird der Liste **Aktivierte Anbieter** hinzugefügt.
- **Benutzerdefinierte Anbieter**: Wählen Sie einen benutzerdefinierten ETW-Anbieter und die Ablaufverfolgungsebene aus. Identifizieren Sie den Anbieter anhand seiner GUID. Nehmen Sie Klammern nicht in die GUID aus.
- **Enabled-Anbieter**: Dies sind die aktivierten Dienstanbieter aufgeführt. Wählen Sie einen Anbieter aus der Dropdownliste aus, und klicken oder tippen Sie auf **Deaktivieren**, um die Ablaufverfolgung zu beenden. Klicken oder tippen Sie auf **Beenden**, um sämtliche Ablaufverfolgung anzuhalten.
- **Anbieter Verlauf**: Dieses Feld zeigt die ETW-Anbieter, die während der aktuellen Sitzung aktiviert wurden. Klicken oder tippen Sie auf **Aktivieren**, um einen Anbieter zu aktivieren, der deaktiviert war. Klicken oder tippen Sie auf **Löschen**, um den Verlauf zu löschen.
- **Filter / Ereignisse**: Bereich " **Ereignisse** " ETW-Ereignisse aus der ausgewählten Anbieter im Tabellenformat enthält. Die Tabelle wird in Echtzeit aktualisiert. Verwenden Sie das Menü " **Filter** ", um benutzerdefinierte Filter einzurichten für die Ereignisse angezeigt werden sollen. Klicken Sie auf die Schaltfläche **Löschen** , um alle ETW-Ereignisse aus der Tabelle zu löschen. Hierdurch werden keine Anbieter deaktiviert. Klicken Sie auf **in Datei speichern** , um die derzeit erfassten ETW-Ereignisse in einer lokalen CSV-Datei zu exportieren.

Weitere Informationen zur Verwendung von ETW-Protokollierung finden Sie unter im Blogbeitrag [Verwendung Gerät Portal Debugprotokolle anzeigen](https://blogs.windows.com/buildingapps/2016/06/10/using-device-portal-to-view-debug-logs-for-uwp/) . 

### <a name="performance-tracing"></a>Leistungsüberwachung

Auf der Seite Tracing Leistung können Sie für die Ansicht die Spuren [Windows Performance Aufzeichnung (WPR)](https://msdn.microsoft.com/library/hh448205.aspx) aus der Host-Gerät.

![Gerät Portal Leistung Tracing-Seite](images/device-portal/mob-device-portal-perf-tracing.png)

- **Verfügbare Profile**: Wählen Sie in der Dropdownliste das WPR-Profil aus, und klicken oder tippen Sie auf **Starten**, um die Ablaufverfolgung zu starten.
- **Benutzerdefinierte Profile**: Klicken oder tippen Sie auf **Durchsuchen**, um ein WPR-Profil vom PC auszuwählen. Klicken oder tippen Sie auf **Hochladen und starten**, um die Ablaufverfolgung zu starten.

Klicken Sie auf **Beenden**, um die Ablaufverfolgung zu beenden. Auf dieser Seite bleiben, bis die Ablaufverfolgungsdatei (. ETL) vollständig heruntergeladen.

Erfasst. ETL-Dateien können für die Analyse im [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/desktop/hh448170.aspx)geöffnet werden.

### <a name="device-manager"></a>Geräte-Manager

Die Geräte-Manager-Seite listet alle Peripheriegeräte auf Ihrem Gerät angeschlossen. Sie können die Einstellungen für Symbole zum Anzeigen der Eigenschaften der einzelnen klicken.

![Seite für Gerät Portal Geräte-manager](images/device-portal/mob-device-portal-devices.png)

### <a name="networking"></a>Networking

Der Netzwerkseite verwaltet Netzwerkverbindungen auf dem Gerät. Es sei denn, Sie Portal über USB-Gerät verbunden sind, werden diese Einstellungen ändern wahrscheinlich Sie Gerät Portal trennen.
- **Verfügbare Netzwerke**: Zeigt die WLAN-Netzwerke für das Gerät verfügbar. Durch Klicken oder Tippen auf ein Netzwerk können Sie eine Verbindung mit ihm herstellen und ggf. ein Kennwort eingeben. Gerät Portal unterstützt noch keine Enterprise-Authentifizierung. Die Dropdownliste **Profile** aus können auch versuchen, eine der WLAN-Profile bekannt, dass das Gerät eine Verbindung herstellen.
- **IP-Konfiguration**: Zeigt Adressinformationen zu den einzelnen des Hosts Netzwerkports des Geräts.

![Gerät Portal Networking-Seite](images/device-portal/mob-device-portal-network.png)

## <a name="service-features-and-notes"></a>Features für den Dienst und Notizen

### <a name="dns-sd"></a>DNS-SD

Das Geräteportal kündigt seine Präsenz im lokalen Netzwerk mithilfe von DNS-SD an. Alle Geräteportalinstanzen, unabhängig von deren Gerätetyp, kündigen sich unter „WDP._wdp._tcp.local“ an. Die TXT-Datensätze für die Instanz des Dienstes liefern Folgendes:

Key | Typ | Beschreibung 
----|------|-------------
S | int | Sicherer Port für Geräteportal. Wenn 0 (null), lauscht das Geräteportal nicht auf HTTPS-Verbindungen. 
D | String | Typ des Geräts. Dieser wird das Format „Windows.*“ aufweisen, z. B. Windows.Xbox oder Windows.Desktop
A | String | Gerätearchitektur. Diese ist ARM, x86 oder AMD64.  
T | Mit NULL-Zeichen getrennt Liste mit Zeichenfolgen | Vom Benutzer angewendete Tags für das Gerät. Informationen zur Verwendung finden Sie unter der Tags-REST-API. Liste wird durch Doppelnull beendet.  

Es wird vorgeschlagen, die Verbindung über den HTTPS-Anschluss herzustellen, da nicht alle Geräte auf dem vom DNS-SD-Datensatz angekündigten HTTP-Port lauschen. 

### <a name="csrf-protection-and-scripting"></a>CSRF-Schutz und -Skripting

Zum Schutz vor [CSRF-Angriffen](https://wikipedia.org/wiki/Cross-site_request_forgery) ist bei allen Nicht-GET-Anfragen ein eindeutiges Token erforderlich. Dieses Token, der X-CSFR-Token-Anforderungsheader, wird von einem Sitzungscookie CSRF-Token, abgeleitet. In der Web-Benutzeroberfläche des Geräteportals wird das CSRF-Token-Cookie bei jeder Anforderung in den X-CSRF-Token-Header kopiert.

> [!IMPORTANT]
> Dieser Schutz verhindert, dass Verwendungen der REST-APIs von einem eigenständigen Client (beispielsweise Befehlszeilenprogrammen). Dies kann auf drei Arten gelöst werden: 
> - Verwenden Sie einen Benutzernamen "Auto-". Clients, die ihrem Benutzernamen „Auto-“ voranstellen, umgehen CSRF-Schutz. Es ist wichtig, dass dieser Benutzername nicht zur Anmeldung beim Geräteportal über den Browser verwendet wird, da dies den Dienst für CSRF-Angriffe öffnet. Beispiel: Wenn der Benutzername des Geräteportals „Admin“ lautet, sollte ```curl -u auto-admin:password <args>``` zum Umgehen des CSRF Schutzes verwendet werden. 
> - Implementieren des Cookie-zu-Header-Schemas in den Client. Dies erfordert eine GET-Anforderung zur Erstellung des Sitzungscookies und dann die Aufnahme von Header und Cookie in alle nachfolgenden Anforderungen. 
> - Deaktivieren der Authentifizierung und Verwenden von HTTP. CSRF-Schutz bezieht sich nur auf HTTPS-Endpunkte, sodass für Verbindungen auf HTTP-Endpunkten keine der oben genannten Schritte ausgeführt werden müssen. 

#### <a name="cross-site-websocket-hijacking-cswsh-protection"></a>Schutz vor websiteübergreifendem WebSocket-Hijacking (Cross-Site WebSocket Hijacking, CSWSH)

Zum Schutz vor [CSWSH-Angriffen](https://www.christian-schneider.net/CrossSiteWebSocketHijacking.html) müssen alle Clients, die eine WebSocket-Verbindung mit einem Geräteportal herstellen, einen dem Hostheader entsprechenden Origin-Header angeben. Dadurch wird gegenüber dem Geräteportal belegt, dass die Anforderung entweder von der Benutzeroberfläche des Geräteportals oder von einer gültigen Clientanwendung stammt. Anforderungen ohne Origin-Header werden abgelehnt. 
