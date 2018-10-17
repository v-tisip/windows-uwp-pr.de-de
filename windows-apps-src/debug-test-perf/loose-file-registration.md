---
author: c-don
title: Bereitstellen einer app über registrieren loser Dateien
description: Diese Anleitung zeigt, wie Sie das Layout registrieren loser Dateien zu überprüfen und Freigeben von Windows 10-apps ohne Verpackung verwenden.
ms.author: cdon
ms.date: 6/1/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, geräteportal, App-Manager, Bereitstellung, sdk
ms.localizationpriority: medium
ms.openlocfilehash: a6a96a78cf03ce4994ddee1c929997b12a2d028f
ms.sourcegitcommit: 1c6325aa572868b789fcdd2efc9203f67a83872a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/17/2018
ms.locfileid: "4745435"
---
# <a name="deploy-an-app-through-loose-file-registration"></a>Bereitstellen einer app über registrieren loser Dateien 

Diese Anleitung zeigt, wie Sie das Layout registrieren loser Dateien zu überprüfen und Freigeben von Windows 10-apps ohne Verpackung verwenden. Registrieren loser Dateilayouts kann Entwickler schnell ihre apps ohne die Notwendigkeit zum Packen und installieren Sie die apps zu überprüfen. 

## <a name="what-is-a-loose-file-layout"></a>Was ist ein Layout registrieren loser Dateien?

Registrieren loser Dateilayout ist einfach das Platzieren von app-Inhalt in einem Ordner anstelle des Verpackungsprozesses durchlaufen. Der Inhalt des Pakets sind nicht verpackten und in einem Ordner "lose" verfügbar. 

> [!WARNING]
> Layout registrieren loser ist für Entwicklern und Designern, um ihre apps während der aktiven Entwicklung schnell zu überprüfen. Dieser Ansatz sollte nicht verwendet werden, um "Dogfood" oder flight die app. Es wird empfohlen, dass die abschließende Überprüfung auf einer verpackten app durchgeführt werden, die mit einem vertrauenswürdigen Zertifikat signiert ist. 

## <a name="advantages-of-loose-file-registration"></a>Vorteile von registrieren loser Dateien

- **Schnelle Validierung** – da die app-Dateien bereits entpackt sind, Benutzer können schnell registrieren loser Datei-Layout und Starten der app. Wie bei einer regulären app kann der Benutzer die app zu verwenden, da es entwickelt wurde. 
- **Einfache im Netzwerk Verteilung** - Wenn die losen Dateien in einer Netzwerkfreigabe anstelle von einem lokalen Laufwerk gespeichert sind, Entwickler können Senden der Netzwerkfreigabe an andere Benutzer, die Zugriff auf das Netzwerk haben und sie registrieren loser Datei-Layout und die app ausführen können. Dadurch können mehrere Benutzer gleichzeitig Überprüfung der app. 
- **Zusammenarbeit** - registrieren loser Dateien ermöglicht Entwicklern und Designern weiterhin arbeiten auf visuelle Ressourcen, während die app registriert ist. Benutzern wird diese Änderungen angezeigt, wenn sie die app zu starten. Beachten Sie, dass Sie nur statische Ressourcen auf diese Weise ändern können. Wenn Sie keine Code oder dynamisch erstellte Inhalte ändern müssen, müssen Sie die app erneut kompilieren.

## <a name="how-to-register-a-loose-file-layout"></a>So registrieren Sie ein Layout registrieren loser Dateien

Windows bietet mehrere Developer Tools zum Registrieren loser Dateilayouts auf lokale und remote-Geräte zu registrieren. Sie können auswählen, aus `WinDeployAppCmd` (Windows SDK-Tool), Windows Device Portal, PowerShell und [Visual Studio](https://docs.microsoft.com/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#register-layout-from-network). Im folgenden werden wir über zum Registrieren von loser Dateien, die mit diesen Tools geleitet. Aber stellen Sie zunächst sicher, dass Sie nach dem Setup haben:

- Ihre Geräte müssen die Windows 10 Creators Update (Build 14965) oder höher installiert sein.
- Sie müssen [den Entwicklermodus](https://msdn.microsoft.com/windows/uwp/get-started/enable-your-device-for-development) und [Gerätesuche](https://docs.microsoft.com/en-us/windows/uwp/get-started/enable-your-device-for-development#device-discovery) auf allen Geräten aktivieren.

> [!IMPORTANT]
> Registrieren loser Dateien ist nur verfügbar auf Geräten, die das Netzwerk Freigabe (SMB)-Protokoll unterstützen: Desktop und Xbox. 

### <a name="register-with-windeployappcmd"></a>Registrieren mit WinDeployAppCmd

Wenn Sie die SDK-Tools entspricht, auf dem Windows 10 Creators Update (Build 14965) oder höher verwenden, können Sie mithilfe der `WinDeployAppCmd` Befehl in einer Befehlszeile eingeben.

```cmd
WinAppDeployCmd.exe registerfiles -remotedeploydir <Network Path> -ip <IP Address> -pin <target machine PIN>
```

**Netzwerkpfad** – der Pfad zum Registrieren loser Dateien der app.

**IP-Adresse** – die IP-Adresse des Zielcomputers.

**Zielcomputer PIN** – eine PIN, bei Bedarf herstellen eine Verbindung mit dem Zielgerät. Werden Sie aufgefordert, wiederholen Sie mit der `-pin` option, wenn eine Authentifizierung erforderlich ist. Finden Sie unter [Gerätesuche](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development#device-discovery) erfahren Sie, wie Sie eine PIN erhalten.

### <a name="windows-device-portal"></a>Windows Geräteportal

Windows Device Portal ist auf allen Windows 10-Geräten verfügbar und wird von Entwicklern verwendet, um zu testen und zu überprüfen ihrer Arbeit. Es bietet für alle Beteiligten der Entwicklercommunity mit seiner Browser UX und REST-Endpunkte. Weitere Informationen zum Device Portal finden Sie in der [Übersicht über Windows Device Portal](device-portal.md).

Gehen Sie folgendermaßen vor, um das Layout registrieren loser Dateien im Device Portal zu registrieren.

1. Mit dem Geräteportal mithilfe der Schritte im Abschnitt **Setup** für die [Übersicht über Windows-Geräteportal](device-portal.md)verbinden.
1. Wählen Sie in der Registerkarte "Apps-Manager" **von Netzwerkfreigabe zu registrieren**.
1. Geben Sie die Netzwerk-Freigabepfad auf das Layout registrieren loser Dateien. 
1. Wenn das Hostgerät Zugriff auf die Netzwerkfreigabe besitzt, werden dazu aufgefordert, geben Sie die erforderlichen Anmeldeinformationen.
1. Nachdem die Registrierung abgeschlossen ist, können Sie die app starten.

Auf der Seite "Apps-Manager" des Device Portal können Sie auch optionale registrieren loser Dateilayouts für Ihre Haupt-app registrieren, durch Aktivieren des Kontrollkästchens **ich optionale Pakete angeben möchten** und geben Sie die Bereitstellungsfreigabe Netzwerkpfade der optionalen apps. 

### <a name="powershell"></a>PowerShell 

Windows PowerShell ermöglicht auch zum Registrieren loser Dateilayouts, aber nur auf dem lokalen Gerät zu registrieren. Wenn Sie ein Layout auf einem Remotegerät registrieren möchten, müssen Sie eine der anderen Methoden verwenden. 

Registrieren loser Datei-Layout, starten PowerShell, und geben Sie Folgendes.

```PowerShell
Add-AppxPackage -Register <path to manifest file>
```

## <a name="troubleshooting"></a>Fehlerbehebung

### <a name="mapped-network-drives"></a>Zugeordnete Netzwerklaufwerke
Derzeit sind nicht zugeordneten Netzwerklaufwerken für lose Datei Registrierungen unterstützt. Verweisen Sie auf das zugeordnete Laufwerk mit vollständigem den Netzwerk-Freigabepfad.

### <a name="registration-failure"></a>Registrierungsfehler
Das Gerät, auf dem die Registrierung stattfindet, müssen Zugriff auf das Dateilayout haben. Wenn das Dateilayout auf einer Netzwerkfreigabe gehostet wird, stellen Sie sicher, dass das Gerät zugreifen kann. 

### <a name="modifications-to-visual-assets-arent-being-loaded-in-the-app"></a>Änderungen an visuellen Ressourcen sind nicht in der app geladen wird 
Die app wird die visuellen Anlagen zur Startzeit geladen. Wenn Änderungen an die visuellen Ressourcen nach dem Starten der app vorgenommen wurden, müssen Sie die app, um die neuesten Änderungen anzeigen neu starten.