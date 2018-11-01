---
author: PatrickFarley
ms.assetid: 5c34c78e-9ff7-477b-87f6-a31367cd3f8b
title: Geräteportal für Windows-Desktop
description: Hier erfahren Sie, wie das Windows Device Portal die Diagnose und Automatisierung auf dem Windows-Desktop öffnet.
ms.author: pafarley
ms.date: 03/15/2018
ms.topic: article
keywords: Windows 10, Uwp, geräteportal
ms.localizationpriority: medium
ms.openlocfilehash: 353afaa511eb382ba2d5772b9b88d3e6b5335ea6
ms.sourcegitcommit: 70ab58b88d248de2332096b20dbd6a4643d137a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "5922500"
---
# <a name="device-portal-for-windows-desktop"></a>Geräteportal für Windows-Desktop



Im Windows-Geräteportal können Sie Diagnoseinformationen anzeigen und über HTTP aus dem Browserfenster mit Ihrem Desktop interagieren. Sie haben im Geräteportal folgende Möglichkeiten:
- Anzeigen und Bearbeiten einer Liste laufender Prozesse
- Installieren, Löschen, Starten und Beenden von Apps
- Ändern von WLAN-Profilen und Anzeigen der Signalstärke und der ipconfig
- Anzeigen von Live-Diagrammen zur Auslastung von CPU, Arbeitsspeicher, E/A, Netzwerk und GPU
- Sammeln von Prozesssicherungen
- Sammeln von ETW-Ablaufverfolgungen 
- Bearbeiten des isolierten Speichers quergeladener Apps

## <a name="set-up-device-portal-on-windows-desktop"></a>Einrichten von des Geräteportals unter Windows-Desktop

### <a name="turn-on-developer-mode"></a>Entwicklermodus aktivieren

Ab Windows 10, Version 1607, sind einige der neueren Funktionen für den Desktop nur verfügbar, wenn der Entwicklermodus aktiviert ist. Informationen zum Aktivieren des Entwicklermodus finden Sie unter [Aktivieren Ihres Geräts für die Entwicklung](../get-started/enable-your-device-for-development.md).

> [!IMPORTANT]
> In manchen Fällen wird der Entwicklermodus aufgrund von Problemen mit dem Netzwerk oder der Kompatibilität nicht ordnungsgemäß installiert. Lesen Sie den [entsprechenden Abschnitt von „Aktivieren Sie Ihr Gerät für die Entwicklung”](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development#failure-to-install-developer-mode-package), um Hilfe bei der Behebung dieser Probleme zu erhalten.

### <a name="turn-on-device-portal"></a>Geräteportal einschalten

Sie können das Geräteportal im Bereich **Für Entwickler** unter **Einstellungen** aktivieren. Wenn Sie es aktivieren, müssen Sie auch einen entsprechenden Benutzernamen und ein Kennwort erstellen. Verwenden Sie nicht Ihr Microsoft-Konto oder andere Windows-Anmeldeinformationen. 

![Geräteportal-Abschnitt der Einstellungen-App](images/device-portal/device-portal-desk-settings.png) 

Nachdem Geräteportal aktiviert wurde, werden unten im Abschnitt Links angezeigt. Beachten Sie die Portnummer am Ende der aufgeführten URLs: Diese Nummer wird zufällig generiert, wenn Geräteportal aktiviert ist, sollte aber zwischen den Neustarts des Desktops konsistent bleiben. Wenn Sie die Portnummern manuell festlegen möchten, sodass sie erhalten bleiben, finden Sie unter [Portnummern setzen](device-portal-desktop.md#setting-port-numbers) weitere Informationen.

Diese Links bieten zwei Möglichkeiten, sich mit dem Geräteportal zu verbinden: über das lokale Netzwerk (einschließlich VPN) oder über den lokalen Host.

### <a name="connect-to-device-portal"></a>Mit dem Geräteportal verbinden

Um eine Verbindung über einen lokalen Host herzustellen, öffnen Sie ein Browserfenster und geben Sie die hier angezeigte Adresse für den von Ihnen verwendeten Verbindungstyp ein.

* Localhost: `http://127.0.0.1:<PORT>` oder `http://localhost:<PORT>`
* Local Network: `https://<IP address of the desktop>:<PORT>`

Für die Authentifizierung und sichere Kommunikation ist HTTPS erforderlich.

Sie können die Authentifizierung deaktivieren, wenn Sie Geräteportal in einer geschützten Umgebung verwenden, z.B. in einem Testlabor, in dem Sie allen im lokalen Netzwerk vertrauen, keine persönlichen Informationen auf dem Gerät gespeichert haben und in dem spezielle Anforderungen bestehen. Dies ermöglicht eine unverschlüsselte Kommunikation, und jeder, der die IP-Adresse Ihres Computers kennt, kann sich verbinden und es steuern.

## <a name="device-portal-content-on-windows-desktop"></a>Geräteportal-Inhalte auf dem Windows-Desktop

Das Geräteportal auf dem Windows-Desktop bietet die Standardseiten. Ausführliche Beschreibungen finden Sie unter [Übersicht über das Windows-Geräteportal](device-portal.md).

- App-Manager
- Datei-Explorer
- Laufende Prozesse
- Leistung
- Debugging
- Ereignisablaufverfolgung für Windows (ETW)
- Leistungsüberwachung
- Geräte-Manager
- Networking
- Absturzdaten
- Features
- Mixed Reality
- Streaming Install-Debugger
- Speicherort
- Entwurf

## <a name="more-device-portal-options"></a>Weitere Optionen für das Geräteportal
### <a name="registry-based-configuration-for-device-portal"></a>Registrierungsbasierte Konfiguration für das Geräteportal

Wenn Sie Portnummern für Geräteportal auswählen möchten (z. B. 80 und 443), können Sie die folgenden Registrierungsschlüssel festlegen:

- Under `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\WebManagement\Service`
    - `UseDynamicPorts`: Ein erforderlicher DWORD-Wert. Legen Sie den Wert auf 0 fest, um die von Ihnen ausgewählten Portnummern beizubehalten.
    - `HttpPort`: Ein erforderlicher DWORD-Wert. Enthält die Portnummer, an der Geräteportal nach HTTP-Verbindungen lauscht.    
    - `HttpsPort`: Ein erforderlicher DWORD-Wert. Enthält die Portnummer, an der Geräteportal nach HTTPS-Verbindungen lauscht.
    
Unter dem gleichen regkey-Pfad können Sie auch die Authentifizierungsanforderung deaktivieren:
- `UseDefaultAuthorizer` - `0` für deaktiviert, `1` für aktiviert.  
    - Dies steuert sowohl die grundlegende Authentifizierungsanforderung für jede Verbindung als auch die Weiterleitung von HTTP nach HTTPS.  
    
### <a name="command-line-options-for-device-portal"></a>Befehlszeilenoptionen für das Geräteportal
Über eine administrative Eingabeaufforderung können Sie Teile des Geräteportal aktivieren und konfigurieren. Um den neuesten Satz von Befehlen zu sehen, die von Ihrem Build unterstützt werden, können Sie Folgendes ausführen `webmanagement /?`

- `sc start webmanagement` oder `sc stop webmanagement` 
    - Schalten Sie den Dienst ein oder aus. Dazu muss ebenfalls der Entwicklermodus aktiviert sein. 
- `-Credentials <username> <password>` 
    - Legen Sie einen Benutzernamen und ein Passwort für das Geräteportal fest. Der Benutzername muss den Basic-Auth-Standards entsprechen, darf also keinen Doppelpunkt (:) enthalten und sollte aus Standard-ASCII-Zeichen wie z. B. [a-z, A-Z, 0-9] aufgebaut sein, da Browser standardmäßig nicht den gesamten Zeichensatz verarbeitet.  
- `-DeleteSSL` 
    - Dadurch wird der für HTTPS-Verbindungen verwendete SSL-Zertifikat-Cache zurückgesetzt. Wenn Sie auf TLS-Verbindungsfehler stoßen, die nicht umgangen werden können (im Gegensatz zur erwarteten Zertifikatswarnung), kann diese Option das Problem für Sie beheben. 
- `-SetCert <pfxPath> <pfxPassword>`
    - Weitere Informationen finden Sie unter [Bereitstellen eines Geräteportals mit einem benutzerdefinierten SSL-Zertifikat](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl).  
    - Auf diese Weise können Sie Ihr eigenes SSL-Zertifikat installieren, um die SSL-Warnseite zu reparieren, die normalerweise im Geräteportal angezeigt wird. 
- `-Debug <various options for authentication, port selection, and tracing level>`
    - Führen Sie eine eigenständige Version des Geräteportals mit einer bestimmten Konfiguration und sichtbaren Debug-Meldungen aus. Dies ist besonders nützlich für die Erstellung eines [gepackten Plugins](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-plugin). 
    - Lesen Sie den [Artikel im MSDN Magazine](https://msdn.microsoft.com/en-us/magazine/mt826332.aspx) mit Details darüber, wie Sie es als „System” ausführen können, um Ihr gepacktes Plugin vollständig zu testen.

## <a name="see-also"></a>Weitere Informationen:

* [Übersicht über das Windows Geräteportal](device-portal.md)
* [Referenz zu Kern-APIs des Geräteportal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
