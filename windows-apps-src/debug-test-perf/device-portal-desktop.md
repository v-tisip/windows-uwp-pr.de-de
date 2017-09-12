---
author: PatrickFarley
ms.assetid: 5c34c78e-9ff7-477b-87f6-a31367cd3f8b
title: "Device Portal für Desktop"
description: "Hier erfahren Sie, wie das Windows Device Portal die Diagnose und Automatisierung auf dem Windows-Desktop öffnet."
ms.author: pafarley
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp
ms.openlocfilehash: 32155bfbb676a5f79dd4b1629f0a88368da36828
ms.sourcegitcommit: 0fa9ae00117e8e6b04ed38956e605bb74c1261c6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2017
---
# <a name="device-portal-for-desktop"></a>Device Portal für Desktop

Ab Windows 10, Version 1607, sind weitere Entwicklerfeatures für Desktop verfügbar. Diese Features sind nur verfügbar, wenn der Entwicklermodus aktiviert ist.

Informationen zum Aktivieren des Entwicklermodus finden Sie unter [Aktivieren Ihres Geräts für die Entwicklung](../get-started/enable-your-device-for-development.md).

Im Device Portal können Sie Diagnoseinformationen anzeigen und über HTTP aus dem Browser mit Ihrem Desktop interagieren. Sie haben im Device Portal folgende Möglichkeiten:
- Anzeigen und Bearbeiten einer Liste laufender Prozesse
- Installieren, Löschen, Starten und Beenden von Apps
- Ändern von WLAN-Profilen und Anzeigen der Signalstärke und der ipconfig
- Anzeigen von Live-Diagrammen zur Auslastung von CPU, Arbeitsspeicher, E/A, Netzwerk und GPU
- Sammeln von Prozesssicherungen
- Sammeln von ETW-Ablaufverfolgungen 
- Bearbeiten des isolierten Speichers quergeladener Apps

## <a name="set-up-device-portal-on-windows-desktop"></a>Einrichten von Device Portal unter Windows-Desktop

### <a name="turn-on-device-portal"></a>Aktivieren von Device Portal

Sie können Device Portal im Menü **Entwicklereinstellungen** mit aktiviertem Entwicklermodus aktivieren.  

Wenn Sie Device Portal aktivieren, müssen Sie einen Benutzernamen und ein Kennwort für Device Portal erstellen. Verwenden Sie nicht Ihr Microsoft-Konto oder andere Windows-Anmeldeinformationen.  

Nachdem Device Portal aktiviert wurde, werden unten im Abschnitt **Einstellungen** Links angezeigt. Beachten Sie die Portnummer am Ende der URL: Diese Portnummer wird nach dem Zufallsprinzip generiert, wenn Device Portal aktiviert wird, sollte jedoch zwischen Neustarts des Desktops konsistent bleiben. Wenn Sie die Portnummern manuell festlegen möchten, sodass sie erhalten bleiben, finden Sie unter [Portnummern setzen](device-portal-desktop.md#setting-port-numbers) weitere Informationen.

Sie haben zwei Möglichkeiten zum Herstellen einer Verbindung mit Device Portal: über einen lokalen Host und über das lokale Netzwerk (einschließlich VPN).

**So stellen Sie eine Verbindung mit dem Device Portal her**

1. Geben Sie in Ihrem Browser die hier angegebene Adresse für den verwendeten Verbindungstyp ein.

    - Lokaler Host: `http://127.0.0.1:PORT` oder `http://localhost:PORT`

    Verwenden Sie diese Adresse, um Device Portal lokal anzuzeigen.
    
    - Lokales Netzwerk: `https://<The IP address of the desktop>:PORT`

    Verwenden Sie diese Adresse, um die Verbindung über ein lokales Netzwerk herzustellen.

Für die Authentifizierung und sichere Kommunikation ist HTTPS erforderlich.

Sie können die Authentifizierung deaktivieren, wenn Sie Device Portal in einer geschützten Umgebung verwenden, z.B. in einem Testlabor, in dem Sie allen im lokalen Netzwerk vertrauen, keine persönlichen Informationen auf dem Gerät gespeichert haben und in dem spezielle Anforderungen bestehen. Dies ermöglicht eine unverschlüsselte Kommunikation, und jeder, der die IP-Adresse Ihres Computers kennt, kann es steuern.

## <a name="device-portal-pages"></a>Seiten von Device Portal

Device Portal für Desktop enthält den Standardsatz der Seiten. Ausführliche Beschreibungen finden Sie unter [Übersicht über das Windows Device Portal](device-portal.md).

- Apps
- Prozesse
- Leistung
- Debuggen
- Ereignisablaufverfolgung für Windows (ETW)
- Leistungsüberwachung
- Geräte
- Netzwerk
- App-Datei-Explorer 

## <a name="setting-port-numbers"></a>Festlegen von Portnummern

Wenn Sie Portnummern für Device Portal auswählen möchten (z. B. 80 und 443), können Sie die folgenden Registrierungsschlüssel festlegen:

- Unter HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\WebManagement\Service
    - UseDynamicPorts: Ein erforderlicher DWORD-Wert. Legen Sie den Wert auf 0 fest, um die von Ihnen ausgewählten Portnummern beizubehalten.
    - HttpPort: Ein erforderlicher DWORD-Wert. Enthält die Portnummer, an der Device Portal nach HTTP-Verbindungen lauscht.  
    - HttpsPort: Ein erforderlicher DWORD-Wert. Enthält die Portnummer, an der Device Portal nach HTTPS-Verbindungen lauscht.

## <a name="failure-to-install-developer-mode-package"></a>Fehler beim Installieren des Entwicklermoduspakets
In manchen Fällen wird der Entwicklermodus aufgrund von Problemen mit dem Netzwerk oder der Kompatibilität nicht ordnungsgemäß installiert. Das Entwicklermoduspaket ist für die **remote** Bereitstellung auf dem PC erforderlich – verwenden Sie Device Portal über einen Browser oder Device Discovery zur Aktivierung von SSH – aber nicht für die lokale Entwicklung.  Selbst wenn diese Probleme auftreten, können Sie Ihre App weiterhin mithilfe von Visual Studio bereitstellen. 

Im Forum [Bekannte Probleme](https://social.msdn.microsoft.com/Forums/en-US/home?forum=Win10SDKToolsIssues&sort=relevancedesc&brandIgnore=True&searchTerm=%22device+portal%22) und auf der [Entwicklermodusseite](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development#failure-to-install-developer-mode-package) finden Sie entsprechende Problemumgehungen und vieles mehr. 

