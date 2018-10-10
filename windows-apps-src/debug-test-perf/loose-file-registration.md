---
author: c-don
title: Bereitstellen einer app über registrieren loser Dateien
description: Dieser Anleitung zeigt, wie Sie das Layout registrieren loser Dateien zu überprüfen und Freigeben von Windows 10-apps ohne Verpackung verwenden.
ms.author: cdon
ms.date: 6/1/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, geräteportal, App-Manager, Bereitstellung, sdk
ms.localizationpriority: medium
ms.openlocfilehash: a6a96a78cf03ce4994ddee1c929997b12a2d028f
ms.sourcegitcommit: 8e30651fd691378455ea1a57da10b2e4f50e66a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/10/2018
ms.locfileid: "4502522"
---
# <a name="deploy-an-app-through-loose-file-registration"></a>Bereitstellen einer app über registrieren loser Dateien 

Dieser Anleitung zeigt, wie Sie das Layout registrieren loser Dateien zu überprüfen und Freigeben von Windows 10-apps ohne Verpackung verwenden. Registrieren loser Dateilayouts kann Entwickler schnell ihre apps ohne die Notwendigkeit zum Packen und installieren Sie die apps zu überprüfen. 

## <a name="what-is-a-loose-file-layout"></a>Was ist ein Layout loser Datei?

Registrieren loser Dateilayout ist einfach das Platzieren von app-Inhalt in einem Ordner anstelle des Verpackungsprozesses durchlaufen. Der Inhalt des Pakets sind in einen Ordner "lose" verfügbar und nicht verpackten. 

> [!WARNING]
> Layout registrieren loser ist für Entwickler und Entwickler schnell ihre apps während der aktiven Entwicklung überprüft. Dieser Ansatz sollte nicht verwendet werden, um "Dogfood" oder flight die app. Es wird empfohlen, dass die endgültige Überprüfung auf eine verpackte app durchgeführt werden, die mit einem vertrauenswürdigen Zertifikat signiert ist. 

## <a name="advantages-of-loose-file-registration"></a>Vorteile von registrieren loser Dateien

- **Schnelle Validierung** – da die app Dateien bereits entpackt, Benutzer können schnell registrieren loser Datei-Layout und Starten der app. Wie bei einer regulären app kann der Benutzer die app zu verwenden, da es entwickelt wurde. 
- **Einfache im Netzwerk-Verteilung** - losen Dateien befinden sich in einer Netzwerkfreigabe anstelle von einem lokalen Laufwerk Entwickler können Senden der Netzwerkfreigabe an andere Benutzer, die Zugriff auf das Netzwerk haben und sie registrieren loser Datei-Layout und die app ausführen können. Dadurch können mehrere Benutzer die app gleichzeitig zu überprüfen. 
- **Zusammenarbeit** - registrieren loser Dateien ermöglicht Entwicklern und Designern weiterarbeiten auf visuelle Ressourcen, während die app registriert ist. Benutzern wird diese Änderungen angezeigt, wenn sie die app zu starten. Beachten Sie, dass Sie nur statische Ressourcen auf diese Weise ändern können. Wenn Sie keine Code oder dynamisch erstellte Inhalte ändern müssen, müssen Sie die app erneut kompilieren.

## <a name="how-to-register-a-loose-file-layout"></a>Wie Sie ein Layout registrieren loser Dateien registrieren

Windows bietet mehrere Developer Tools zum Registrieren loser Dateilayouts auf lokale und remote-Geräten. Sie können auswählen, aus `WinDeployAppCmd` (Windows SDK-Tool), Windows Device Portal, PowerShell und [Visual Studio](https://docs.microsoft.com/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#register-layout-from-network). Im folgenden gehen wir über zum Registrieren loser Dateien, die mit diesen Tools. Aber stellen Sie zunächst sicher, dass Sie nach dem Setup haben:

- Ihre Geräte müssen die Windows 10 Creators Update (Build 14965) oder höher installiert sein.
- Sie müssen [den Entwicklermodus](https://msdn.microsoft.com/windows/uwp/get-started/enable-your-device-for-development) und [Gerätesuche](https://docs.microsoft.com/en-us/windows/uwp/get-started/enable-your-device-for-development#device-discovery) auf allen Geräten aktivieren.

> [!IMPORTANT]
> Registrieren loser Dateien ist nur verfügbar auf Geräten, die das Netzwerk Freigabe (SMB)-Protokoll unterstützen: Desktop und Xbox. 

### <a name="register-with-windeployappcmd"></a>Registrieren mit WinDeployAppCmd

Wenn Sie die SDK-Tools, die entsprechende auf Windows 10 Creators Update (Build 14965) oder höher verwenden, können Sie mithilfe der `WinDeployAppCmd` Befehl in einer Befehlszeile eingeben.

```cmd
WinAppDeployCmd.exe registerfiles -remotedeploydir <Network Path> -ip <IP Address> -pin <target machine PIN>
```

**Netzwerkpfad** – der Pfad zum Registrieren loser Dateien der app.

**IP-Adresse** – die IP-Adresse des Zielcomputers.

**Zielcomputer PIN** – eine PIN, bei Bedarf herstellen eine Verbindung mit dem Zielgerät. Werden Sie aufgefordert, wiederholen Sie mit den `-pin` option, wenn eine Authentifizierung erforderlich ist. Finden Sie unter [Gerätesuche](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development#device-discovery) erfahren Sie, wie Sie eine PIN erhalten.

### <a name="windows-device-portal"></a>Windows Geräteportal

Windows Device Portal ist auf allen Windows 10-Geräten verfügbar und wird von Entwicklern verwendet, um zu testen, und überprüfen ihre Arbeit. Es bietet für alle Beteiligten der Entwicklercommunity mit der UX-Browser und REST-Endpunkte. Weitere Informationen zum Device Portal finden Sie in der [Übersicht über Windows Device Portal](device-portal.md).

Gehen Sie folgendermaßen vor, um das Layout registrieren loser Dateien im Device Portal registrieren.

1. Mit dem Geräteportal mithilfe der Schritte im Abschnitt **Setup** für die [Übersicht über Windows-Geräteportal](device-portal.md)verbinden.
1. Wählen Sie in der Registerkarte "Apps-Manager" **von Netzwerkfreigabe zu registrieren**.
1. Geben Sie den Netzwerk-Freigabepfad auf das Layout registrieren loser Dateien. 
1. Wenn das Hostgerät Zugriff auf die Netzwerkfreigabe besitzt, wird eine Aufforderung, geben Sie die erforderlichen Anmeldeinformationen vorhanden sein.
1. Nachdem die Registrierung abgeschlossen ist, können Sie die app starten.

Auf dem Device Portal Apps-Manager-Seite können Sie auch optionale loser Dateilayouts für Ihre Haupt-app registrieren, durch Aktivieren des Kontrollkästchens **ich optionale Pakete angeben möchten** , und dann angeben, die Freigabe Netzwerkpfade der optionalen apps. 

### <a name="powershell"></a>PowerShell 

Windows PowerShell können Sie zum Registrieren loser Dateilayouts, aber nur auf dem lokalen Gerät zu registrieren. Wenn Sie ein Layout auf einem Remotegerät registrieren möchten, müssen Sie eine der anderen Methoden verwenden. 

Registrieren loser Datei-Layout, starten PowerShell, und geben Sie Folgendes.

```PowerShell
Add-AppxPackage -Register <path to manifest file>
```

## <a name="troubleshooting"></a>Problembehandlung

### <a name="mapped-network-drives"></a>Zugeordneten Netzwerklaufwerken
Derzeit sind nicht zugeordneten Netzwerklaufwerken für lose Datei Registrierungen unterstützt. Verweisen Sie auf das zugeordnete Laufwerk mit vollständigem den Netzwerk-Freigabepfad.

### <a name="registration-failure"></a>Registrierungsfehler
Das Gerät, auf dem die Registrierung Vorgangstyps, müssen Zugriff auf das Dateilayout haben. Wenn das Dateilayout auf einer Netzwerkfreigabe gehostet wird, stellen Sie sicher, dass das Gerät zugreifen kann. 

### <a name="modifications-to-visual-assets-arent-being-loaded-in-the-app"></a>Änderungen an visuellen Ressourcen sind nicht in der app geladen wird 
Die app wird die visuellen Ressourcen zur Startzeit geladen. Wenn Änderungen an der visuellen Ressourcen nach dem Starten der app vorgenommen wurden, müssen Sie die app, um die neuesten Änderungen anzeigen neu starten.