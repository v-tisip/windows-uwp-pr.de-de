---
ms.assetid: 60fc48dd-91a9-4dd6-a116-9292a7c1f3be
title: Übersicht über das Windows Device Portal
description: Hier erfahren Sie, wie Sie mit dem Windows Device Portal Ihr Gerät per Remotezugriff über ein Netzwerk oder eine USB-Verbindung konfigurieren und verwalten.
ms.date: 2/19/2019
ms.topic: article
keywords: Windows 10, Uwp, geräteportal
ms.localizationpriority: medium
ms.openlocfilehash: 372524b5a5f002e68c02a8f298703cb7ef99bfdf
ms.sourcegitcommit: a32f656253acc1e8b150919e73c886a59e65756a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2019
ms.locfileid: "9083718"
---
# <a name="windows-device-portal-overview"></a>Übersicht über das Windows Device Portal

Mit dem Windows Device Portal können Sie Ihr Gerät per Remotezugriff über ein Netzwerk oder eine USB-Verbindung konfigurieren und verwalten. Zudem erweiterte Diagnosetools Behebung von und die Leistung Ihrer Windows-Gerät in Echtzeit anzeigen.

Windows Device Portal ist ein Webserver auf Ihrem Gerät, das Sie über einen Webbrowser auf einem PC herstellen können. Wenn Ihr Gerät über einen Webbrowser verfügt, können Sie auch lokal mit dem Browser auf dem Gerät eine Verbindung herstellen.

Windows Device Portal ist für jede Gerätefamilie verfügbar, aber die Features und die Einrichtung variieren basierend auf jedem Gerät Anforderungen. Dieser Artikel enthält eine allgemeine Beschreibung des Device Portals und Links zu Artikeln mit ausführlicheren Informationen für jede Gerätefamilie.

Die Funktionalität des Windows Device Portal wird mit [REST-APIs](device-portal-api-core.md) implementiert, mit denen Sie direkt mit den Zugriff auf Daten und die programmatische Steuerung des Geräts.

## <a name="setup"></a>Setup

Für jedes Gerät gelten spezielle Anweisungen zum Herstellen der Verbindung mit dem Device Portal, diese allgemeinen Schritte sind jedoch für jedes Gerät erforderlich:
1. Aktivieren Sie den Entwicklermodus und Device Portal auf Ihrem Gerät (in den Einstellungen konfiguriert).
2. Verbinden Sie das Gerät und den PC über ein lokales Netzwerk oder mit USB.
3. Navigieren Sie im Browser zu der Seite für das Geräteportal. In der folgenden Tabelle sind die Ports und Protokolle, die von jeder Gerätefamilie verwendet.

Gerätefamilie | Standardmäßig aktiviert? | HTTP | HTTPS | USB
--------------|----------------|------|-------|----
HoloLens | Ja, im Entwicklermodus | 80 (Standard) | 443 (Standard) | http://127.0.0.1:10080
IoT | Ja, im Entwicklermodus | 8080 | Über Registrierungsschlüssel aktivieren | n.v.
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

Die Symbolleiste am oberen Rand der Seite ermöglicht den Zugriff auf häufig verwendete Funktionen.
- **Power**: Zugriff auf ein/aus-Optionen.
  - **Herunterfahren**: Schaltet das Gerät aus.
  - **Neu starten**: Schaltet das Gerät aus und wieder ein.
- **Hilfe**: Öffnet die Hilfeseite.

Verwenden Sie die Links im Navigationsbereich am linken Rand der Seite, um zu den verfügbaren Verwaltungs- und Überwachungstools für Ihr Gerät zu navigieren.

Tools, die für alle gerätefamilien verwendet werden, werden hier beschrieben. Je nach Gerät sind möglicherweise andere Optionen verfügbar. Weitere Informationen finden Sie unter der entsprechenden Seite für den Typ Ihres Geräts.

### <a name="apps-manager"></a>App-Manager

Der Apps-Manager bietet Installations-/Deinstallations- und Verwaltungsfunktionen für app-Pakete und gebündelt, auf dem Hostgerät.

![Seite "Device Portal Apps-Manager"](images/device-portal/WDP_AppsManager2.png)

* **Bereitstellen von apps**: Bereitstellen von verpackten apps aus lokalen Netzwerk oder web-Hosts und registrieren lose Dateien aus Netzwerkfreigaben.
* **Installierte apps**: Verwenden Sie im Dropdown-Menü zu entfernen, oder Starten von apps, die auf dem Gerät installiert sind.
* **Ausführen von apps**: Abrufen von Informationen über die apps, die derzeit ausgeführt werden, und schließen Sie sie nach Bedarf.

#### <a name="install-sideload-an-app"></a>Installieren Sie (querladen) einer app

Sie können querladen von apps während der Entwicklung mit Windows Device Portal:

1.  Wenn Sie ein App-Paket erstellt haben, können Sie es per Remotezugriff auf Ihrem Gerät installieren. Nachdem Sie es in Visual Studio erstellt haben, wird ein Ausgabeordner generiert.

  ![App-Installation](images/device-portal/iot-installapp0.png)

2. Navigieren Sie im Windows Device Portal auf der Seite " **App-Manager** ".

3. Wählen Sie im Abschnitt **Bereitstellen apps** **Lokalen Speicher**.

4. Wählen Sie unter, **Wählen Sie das Anwendungspaket**die **Datei auswählen** , und suchen Sie das app-Paket, das Sie querladen möchten.

5. Wählen Sie unter, **Wählen Sie die Zertifikatdatei (CER) verwendet, um app-Paket zu signieren**die **Datei auswählen** , und suchen Sie das Zertifikat, das app-Paket zugeordnet.

6. Überprüfen Sie die entsprechenden Felder, wenn Sie das optionale installieren möchten oder frameworkpakete zusammen mit der app-Installation, und wählen Sie **Weiter** um sie auszuwählen.

7. Wählen Sie **Installieren** , um die Installation zu initiieren.

8. Wenn das Gerät Windows 10 im S Modus ausgeführt wird, und es ist das erste Mal, die das Zertifikat auf dem Gerät installiert wurde, starten Sie das Gerät neu.

#### <a name="install-a-certificate"></a>Installieren eines Zertifikats

Alternativ können Sie installieren Sie das Zertifikat über Windows Device Portal, und installieren Sie die app auf andere Weise:

1. Navigieren Sie im Windows Device Portal auf der Seite " **App-Manager** ".

2. Wählen Sie im Abschnitt **Bereitstellen apps** **Zertifikat installieren**.

3. Wählen Sie unter, **Wählen Sie die Zertifikatdatei (CER) verwendet, um ein app-Paket zu signieren**die **Datei auswählen** , und suchen Sie das Zertifikat für das app-Paket, das Sie querladen möchten.

4. Wählen Sie **Installieren** , um die Installation zu initiieren.

5. Wenn das Gerät Windows 10 im S Modus ausgeführt wird, und es ist das erste Mal, die das Zertifikat auf dem Gerät installiert wurde, starten Sie das Gerät neu.

#### <a name="uninstall-an-app"></a>Deinstallieren einer App
1.  Stellen Sie sicher, dass die App nicht ausgeführt wird. 
2.  Wenn dies der Fall, wechseln Sie zum **Ausführen von apps** , und schließen sie. Wenn Sie versuchen, deinstallieren, während die app ausgeführt wird, verursacht dies Probleme, wenn Sie versuchen, die app zu installieren. 
3.  Wählen Sie die app aus der Dropdownliste aus, und klicken Sie auf **Entfernen**.

### <a name="running-processes"></a>Laufende Prozesse

Diese Seite zeigt im Detail auf dem Hostgerät derzeit ausgeführten Prozesse. Diese umfassen Apps und Systemprozesse. Auf manchen Plattformen (Desktop, IoT und HoloLens) können Sie Prozesse beenden.

![Device Portal ausgeführt verarbeitet Seite](images/device-portal/mob-device-portal-processes.png)

### <a name="file-explorer"></a>Datei-Explorer

Auf dieser Seite können Sie anzeigen und Bearbeiten von Dateien, die von allen quergeladenen apps gespeichert. Finden Sie die [die App Datei-Explorer](https://blogs.windows.com/buildingapps/2016/06/08/using-the-app-file-explorer-to-see-your-app-data/) Blogbeitrag Weitere Informationen zu den Datei-Explorer und wie sie zu verwenden. 

![Device Portal-Datei-Explorer-Seite](images/device-portal/mob-device-portal-AppFileExplorer.png)

### <a name="performance"></a>Leistung

Die Seite "Performance" zeigt echtzeitgraphen mit Informationen zur Systemdiagnose z. B. Stromverbrauch, Bildfrequenz an, und Laden Sie die CPU.

Die folgenden Metriken sind verfügbar:
- **CPU**: Prozent des gesamten verfügbaren CPU-Auslastung
- **Arbeitsspeicher**: insgesamt, verwendet, verfügbar, verpflichtet, ausgelagerter und nicht ausgelagerter
- **E/a**: Lesen und schreiben Daten Mengen
- **Netzwerk**: empfangene und gesendete Daten
- **GPU**: engine Prozent des gesamten verfügbaren GPU-Nutzung


![Seite "Device Portal-Leistung"](images/device-portal/mob-device-portal-perf.png)

### <a name="event-tracing-for-windows-etw-logging"></a>Event Tracing for Windows (ETW)-Protokollierung

Die ETW-Protokollierung Seite verwaltet Event Tracing for Windows (ETW) Echtzeitinformationen auf dem Gerät.

![Seite des Geräte-Portal ETW-Protokollierung](images/device-portal/mob-device-portal-etw.png)

Aktivieren Sie **Anbieter ausblenden**, um nur die Liste der Ereignisse anzuzeigen.
- **Registrierte Anbieter**: Wählen Sie die Ereignisanbieter und die Ablaufverfolgungsebene aus. Die Ablaufverfolgungsebene aus ist einer der folgenden Werte:
  1. Abnormal exit or termination
  2. Severe errors
  3. Warnungen
  4. Non-error warnings
  5. Detailed trace

  Klicken oder tippen Sie auf **Aktivieren**, um die Ablaufverfolgung zu starten. Der Anbieter wird der Liste **Aktivierte Anbieter** hinzugefügt.
- **Benutzerdefinierte Anbieter**: Wählen Sie einen benutzerdefinierten ETW-Anbieter und die Ablaufverfolgungsebene aus. Identifizieren Sie den Anbieter anhand seiner GUID. Schließen Sie keine Klammern in die GUID.
- **Aktiviert Anbieter**: Dies Listet die aktivierten Anbieter. Wählen Sie einen Anbieter aus der Dropdownliste aus, und klicken oder tippen Sie auf **Deaktivieren**, um die Ablaufverfolgung zu beenden. Klicken oder tippen Sie auf **Beenden**, um sämtliche Ablaufverfolgung anzuhalten.
- **Anbieterverlauf**: Zeigt die ETW-Anbieter, die während der aktuellen Sitzung aktiviert wurden. Klicken oder tippen Sie auf **Aktivieren**, um einen Anbieter zu aktivieren, der deaktiviert war. Klicken oder tippen Sie auf **Löschen**, um den Verlauf zu löschen.
- **Filter / Ereignisse**: Abschnitt **Ereignisse** listet ETW-Ereignisse der ausgewählten Anbieter in Tabellenform. Die Tabelle wird in Echtzeit aktualisiert. Verwenden Sie das Menü " **Filter** ", um benutzerdefinierte Filter einzurichten für die Ereignisse angezeigt werden sollen. Klicken Sie auf die Schaltfläche " **Löschen** ", um alle ETW-Ereignisse aus der Tabelle zu löschen. Hierdurch werden keine Anbieter deaktiviert. Klicken Sie auf **in Datei speichern** , um die derzeit erfassten ETW-Ereignisse in eine lokale CSV-Datei zu exportieren.

Weitere Informationen zur Verwendung von ETW-Protokollierung finden Sie unter im Blogbeitrag [Verwenden Device Portal Debugprotokolle anzeigen](https://blogs.windows.com/buildingapps/2016/06/10/using-device-portal-to-view-debug-logs-for-uwp/) . 

### <a name="performance-tracing"></a>Leistungsüberwachung

Die Seite "Performance Tracing" können Sie für Ansicht die Spuren [Windows Performance Recorder (WPR)](https://msdn.microsoft.com/library/hh448205.aspx) aus dem Hostgerät.

![Device Portal Seite "Performance Tracing"](images/device-portal/mob-device-portal-perf-tracing.png)

- **Verfügbare Profile**: Wählen Sie in der Dropdownliste das WPR-Profil aus, und klicken oder tippen Sie auf **Starten**, um die Ablaufverfolgung zu starten.
- **Benutzerdefinierte Profile**: Klicken oder tippen Sie auf **Durchsuchen**, um ein WPR-Profil vom PC auszuwählen. Klicken oder tippen Sie auf **Hochladen und starten**, um die Ablaufverfolgung zu starten.

Klicken Sie auf **Beenden**, um die Ablaufverfolgung zu beenden. Auf dieser Seite bleiben, bis der Ablaufverfolgungsdatei (. ETL) heruntergeladen wurde.

Erfasst. ETL-Dateien können für die Analyse im [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/desktop/hh448170.aspx)geöffnet werden.

### <a name="device-manager"></a>Geräte-Manager

Die Geräte-Manager-Seite listet alle Peripheriegeräte, die an das Gerät angeschlossen. Sie können die Einstellungen Symbole zum Anzeigen der Eigenschaften der einzelnen klicken.

![Device Portal-Geräte-Manager-Seite](images/device-portal/mob-device-portal-devices.png)

### <a name="networking"></a>Networking

Der Seite "Netzwerk" verwaltet die Netzwerkverbindungen auf dem Gerät. Es sei denn, Sie Device Portal über USB verbunden sind, wird das Ändern dieser Einstellungen wahrscheinlich Sie Device Portal trennen.
- **Verfügbare Netzwerke**: Zeigt die auf dem Gerät verfügbaren WLAN-Netzwerke. Durch Klicken oder Tippen auf ein Netzwerk können Sie eine Verbindung mit ihm herstellen und ggf. ein Kennwort eingeben. Geräteportal unterstützt noch keine Unternehmensauthentifizierung. Sie können auch die Dropdownliste **Profile** verwenden, versucht, auf die WLAN-Profile bekannt, dass das Gerät eine Verbindung herstellen.
- **IP-Konfiguration**: Zeigt Adressinformationen zu den einzelnen des Hosts des Geräts Netzwerk-Ports.

![Device Portal Networking-Seite](images/device-portal/mob-device-portal-network.png)

## <a name="service-features-and-notes"></a>Service-Features und Hinweise

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
> Dieser Schutz verhindert die Verwendung der REST-APIs auf einem eigenständigen Client (z. B. Befehlszeilenprogramme). Dies kann auf drei Arten gelöst werden: 
> - Verwenden Sie einen Benutzernamen "Auto-". Clients, die ihrem Benutzernamen „Auto-“ voranstellen, umgehen CSRF-Schutz. Es ist wichtig, dass dieser Benutzername nicht zur Anmeldung beim Geräteportal über den Browser verwendet wird, da dies den Dienst für CSRF-Angriffe öffnet. Beispiel: Wenn der Benutzername des Geräteportals „Admin“ lautet, sollte ```curl -u auto-admin:password <args>``` zum Umgehen des CSRF Schutzes verwendet werden. 
> - Implementieren des Cookie-zu-Header-Schemas in den Client. Dies erfordert eine GET-Anforderung zur Erstellung des Sitzungscookies und dann die Aufnahme von Header und Cookie in alle nachfolgenden Anforderungen. 
> - Deaktivieren der Authentifizierung und Verwenden von HTTP. CSRF-Schutz bezieht sich nur auf HTTPS-Endpunkte, sodass für Verbindungen auf HTTP-Endpunkten keine der oben genannten Schritte ausgeführt werden müssen. 

#### <a name="cross-site-websocket-hijacking-cswsh-protection"></a>Schutz vor websiteübergreifendem WebSocket-Hijacking (Cross-Site WebSocket Hijacking, CSWSH)

Zum Schutz vor [CSWSH-Angriffen](https://www.christian-schneider.net/CrossSiteWebSocketHijacking.html) müssen alle Clients, die eine WebSocket-Verbindung mit einem Geräteportal herstellen, einen dem Hostheader entsprechenden Origin-Header angeben. Dadurch wird gegenüber dem Geräteportal belegt, dass die Anforderung entweder von der Benutzeroberfläche des Geräteportals oder von einer gültigen Clientanwendung stammt. Anforderungen ohne Origin-Header werden abgelehnt. 
