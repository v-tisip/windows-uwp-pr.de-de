---
title: Bereitstellen einer App über Registrieren loser Dateien
description: Diese Anleitung zeigt, wie Sie das Layout registrieren loser Dateien zu überprüfen und Freigeben von Windows 10-apps ohne Verpackung verwenden.
ms.date: 6/1/2018
ms.topic: article
keywords: Windows 10, Uwp, geräteportal, App-Manager, Bereitstellung, sdk
ms.localizationpriority: medium
ms.openlocfilehash: 928c07bd23228f0fefd78be6019a0d116b2e6e4b
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2018
ms.locfileid: "8878657"
---
# <a name="deploy-an-app-through-loose-file-registration"></a>Bereitstellen einer App über Registrieren loser Dateien 

Diese Anleitung zeigt, wie Sie das Layout registrieren loser Dateien zu überprüfen und Freigeben von Windows 10-apps ohne Verpackung verwenden. Registrieren loser Dateilayouts kann Entwickler schnell ihre apps, ohne dass das Paket, und installieren Sie die apps überprüfen. 

## <a name="what-is-a-loose-file-layout"></a>Was ist ein Layout registrieren loser Dateien?

Registrieren loser Dateilayout ist einfach das Platzieren von app-Inhalt in einem Ordner anstelle der Verpackung durchlaufen. Der Inhalt des Pakets sind in einem Ordner "lose" verfügbar und nicht verpackten. 

> [!WARNING]
> Layout registrieren loser ist für Entwicklern und Designern, um ihre apps während der aktiven Entwicklung schnell zu überprüfen. Dieser Ansatz sollte nicht verwendet werden, um "Dogfood" oder Flight-app. Es wird empfohlen, dass die endgültige Überprüfung auf eine verpackte app durchgeführt werden, die mit einem vertrauenswürdigen Zertifikat signiert ist. 

## <a name="advantages-of-loose-file-registration"></a>Vorteile von registrieren loser Dateien

- **Schnelle Überprüfung** – da die app-Dateien bereits sind, Benutzer können schnell registrieren loser Datei-Layout und Starten der app. Wie bei einer regulären app kann der Benutzer die app zu verwenden, da es entwickelt wurde. 
- **Einfache im Netzwerk-Verteilung** - losen Dateien befinden sich in einer Netzwerkfreigabe anstelle von einem lokalen Laufwerk, Entwickler können der Netzwerkfreigabe an andere Benutzer senden, die Zugriff auf das Netzwerk haben, und können sie das Layout registrieren loser Dateien zu registrieren und Ausführen der app. Dadurch können mehrere Benutzer gleichzeitig die app zu überprüfen. 
- **Zusammenarbeit** - registrieren loser Dateien ermöglicht Entwicklern und Designern auch weiterhin funktionieren auf visuelle Ressourcen, während die app registriert ist. Benutzern wird diese Änderungen angezeigt, wenn sie die app zu starten. Beachten Sie, dass Sie nur statische Ressourcen auf diese Weise ändern können. Wenn Sie keine Code oder dynamisch erstellte Inhalte ändern müssen, müssen Sie die app erneut kompilieren.

## <a name="how-to-register-a-loose-file-layout"></a>So registrieren Sie ein Layout registrieren loser Dateien

Windows bietet mehrere Developer Tools zum Registrieren loser Dateilayouts auf lokale und remote-Geräte zu registrieren. Sie können auswählen, aus `WinDeployAppCmd` (Windows SDK-Tool), Windows Device Portal, PowerShell und [Visual Studio](https://docs.microsoft.com/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#register-layout-from-network). Im folgenden gehen wir wie, lose Dateien, die mit diesen Tools zu registrieren. Aber stellen Sie zunächst sicher, dass Sie nach dem Setup haben:

- Ihre Geräte müssen die Windows 10 Creators Update (Build 14965) oder höher installiert sein.
- Sie müssen [den Entwicklermodus](https://msdn.microsoft.com/windows/uwp/get-started/enable-your-device-for-development) und [Gerätesuche](https://docs.microsoft.com/en-us/windows/uwp/get-started/enable-your-device-for-development#device-discovery) auf allen Geräten aktivieren.

> [!IMPORTANT]
> Registrieren loser Dateien ist nur verfügbar auf Geräten, die die Netzwerk-Freigabe (SMB)-Protokoll unterstützen: Desktop und Xbox. 

### <a name="register-with-windeployappcmd"></a>WinDeployAppCmd registrieren

Wenn Sie die SDK-Tools, die entsprechende auf Windows 10 Creators Update (Build 14965) oder höher verwenden, können Sie mithilfe der `WinDeployAppCmd` Befehl in einer Befehlszeile eingeben.

```cmd
WinAppDeployCmd.exe registerfiles -remotedeploydir <Network Path> -ip <IP Address> -pin <target machine PIN>
```

**Netzwerkpfad** – der Pfad zum Registrieren loser Dateien der app.

**IP-Adresse** – die IP-Adresse des Zielcomputers.

**Zielcomputer PIN** – eine PIN, bei Bedarf zum Herstellen einer Verbindung mit dem Zielgerät. Werden Sie aufgefordert, versuchen mit der `-pin` option, wenn eine Authentifizierung erforderlich ist. Finden Sie unter [Gerätesuche](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development#device-discovery) erfahren Sie, wie Sie eine PIN zu erhalten.

### <a name="windows-device-portal"></a>Windows Geräteportal

Windows Device Portal ist auf allen Windows 10-Geräten verfügbar und wird von Entwicklern verwendet, um zu testen, und überprüfen ihre Arbeit. Es bietet für alle Beteiligten der Entwicklercommunity mit den Browser UX und REST-Endpunkte. Weitere Informationen zum Device Portal finden Sie in der [Übersicht über Windows Device Portal](device-portal.md).

Gehen Sie folgendermaßen vor, um das Layout registrieren loser Dateien im Device Portal zu registrieren.

1. Verbinden Sie mithilfe der Schritte im Abschnitt für die [Übersicht über Windows Device Portal](device-portal.md) **Einrichten** Device Portal.
1. Wählen Sie auf der Registerkarte Apps-Manager **von Netzwerkfreigabe registrieren**.
1. Geben Sie die Netzwerk-Freigabepfad auf das Layout registrieren loser Dateien. 
1. Wenn der Host-Gerät den Zugriff auf die Netzwerkfreigabe besitzt, werden eine Aufforderung zur Eingabe der Anmeldeinformationen erforderlichen.
1. Nachdem die Registrierung abgeschlossen ist, können Sie die app starten.

Auf der Device Portal-Apps-Manager-Seite können Sie auch optionale registrieren loser Dateilayouts für Ihre Haupt-app registrieren, das Kontrollkästchen **ich optionale Pakete angeben möchten** , und geben Sie die Bereitstellungsfreigabe Netzwerkpfade der optionalen apps. 

### <a name="powershell"></a>PowerShell 

Windows PowerShell können Sie zum Registrieren loser Dateilayouts, aber nur auf dem lokalen Gerät zu registrieren. Wenn Sie ein Layout auf einem Remotegerät registrieren möchten, müssen Sie eine der anderen Methoden verwenden. 

Starten von PowerShell, und geben Sie Folgendes, um das Layout registrieren loser Dateien zu registrieren.

```PowerShell
Add-AppxPackage -Register <path to manifest file>
```

## <a name="troubleshooting"></a>Problembehandlung

### <a name="mapped-network-drives"></a>Zugeordnete Netzwerklaufwerke
Zugeordnete Netzwerklaufwerke werden derzeit zum Erfassen von registrieren loser Dateien nicht unterstützt. Finden Sie in das zugeordnete Laufwerk mit vollständigen Pfad der Bereitstellungsfreigabe.

### <a name="registration-failure"></a>Registrierungsfehler
Das Gerät, auf dem die Registrierung stattfindet, müssen Zugriff auf das Layout der Datei. Wenn das Layout der Datei auf einer Netzwerkfreigabe gehostet wird, stellen Sie sicher, dass das Gerät zugreifen kann. 

### <a name="modifications-to-visual-assets-arent-being-loaded-in-the-app"></a>Änderungen an der visuellen Ressourcen sind nicht in der app geladen wird 
Die app wird beim Starten die visuellen Ressourcen geladen. Wenn Änderungen für die visuellen Ressourcen nach dem Starten der app vorgenommen wurden, müssen Sie die app, um die neuesten Änderungen anzeigen erneut starten.