---
author: c-don
title: Bereitstellen einer app über registrieren loser Dateien
description: Dieser Anleitung zeigt, wie Sie das Layout registrieren loser Dateien zu überprüfen und Freigeben von Windows 10-apps ohne Verpackung verwenden.
ms.author: cdon
ms.date: 6/1/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, geräteportal, apps-Manager, Bereitstellung, sdk
ms.localizationpriority: medium
ms.openlocfilehash: a6a96a78cf03ce4994ddee1c929997b12a2d028f
ms.sourcegitcommit: fbdc9372dea898a01c7686be54bea47125bab6c0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/08/2018
ms.locfileid: "4426718"
---
# <a name="deploy-an-app-through-loose-file-registration"></a>Bereitstellen einer app über registrieren loser Dateien 

Dieser Anleitung zeigt, wie Sie das Layout registrieren loser Dateien zu überprüfen und Freigeben von Windows 10-apps ohne Verpackung verwenden. Registrieren loser Dateilayouts kann Entwickler schnell ihre apps ohne die Notwendigkeit zum Packen und installieren Sie die apps zu überprüfen. 

## <a name="what-is-a-loose-file-layout"></a>Was ist ein Layout loser Datei?

Loser Datei-Layout ist einfach das Platzieren von app-Inhalt in einem Ordner anstelle des Verpackungsprozesses durchlaufen. Der Inhalt des Pakets sind in einen Ordner "lose" verfügbar und nicht verpackten. 

> [!WARNING]
> Layout registrieren loser ist für Entwicklern und Designern, um ihre apps während der aktiven Entwicklung schnell zu überprüfen. Dieser Ansatz sollte nicht verwendet werden, um "Dogfood" oder die app flight. Es wird empfohlen, dass die abschließende Überprüfung auf eine verpackte app durchgeführt werden, die mit einem vertrauenswürdigen Zertifikat signiert ist. 

## <a name="advantages-of-loose-file-registration"></a>Vorteile von registrieren loser Dateien

- **Schnelle Validierung** – da die app-Dateien bereits sind, Benutzer können schnell registrieren loser Datei-Layout und Starten der app. Wie bei einer regulären app kann der Benutzer die app zu verwenden, da es entwickelt wurde. 
- **Einfache im Netzwerk-Verteilung** - losen Dateien befinden sich in einer Netzwerkfreigabe anstelle von einem lokalen Laufwerk, Entwickler können der Netzwerkfreigabe an andere Benutzer senden, die auf das Netzwerk zugreifen, und können sie das Layout registrieren loser Dateien zu registrieren und Ausführen der app. Dadurch können mehrere Benutzer gleichzeitig die app zu überprüfen. 
- **Zusammenarbeit** - registrieren loser Dateien ermöglicht Entwicklern und Designern weiterarbeiten auf visuelle Ressourcen, während die app registriert ist. Benutzern wird diese Änderungen angezeigt, wenn sie die app zu starten. Beachten Sie, dass Sie nur statische Ressourcen auf diese Weise ändern können. Wenn Sie keine Code oder dynamisch erstellte Inhalte ändern müssen, müssen Sie die app erneut kompilieren.

## <a name="how-to-register-a-loose-file-layout"></a>Wie Sie ein Layout loser Datei registrieren

Windows bietet mehrere Developer Tools zum Registrieren loser Dateilayouts auf lokale und remote-Geräten. Sie können auswählen, aus `WinDeployAppCmd` (Windows SDK-Tool), Windows Device Portal, PowerShell und [Visual Studio](https://docs.microsoft.com/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#register-layout-from-network). Im folgenden gehen wir über lose Dateien, die mit diesen Tools zu registrieren. Allerdings stellen Sie zunächst sicher, dass Sie nach dem Setup haben:

- Ihre Geräte müssen die Windows 10 Creators Update (Build 14965) oder höher installiert sein.
- Sie müssen [den Entwicklermodus](https://msdn.microsoft.com/windows/uwp/get-started/enable-your-device-for-development) und [Gerätesuche](https://docs.microsoft.com/en-us/windows/uwp/get-started/enable-your-device-for-development#device-discovery) auf allen Geräten aktivieren.

> [!IMPORTANT]
> Registrieren loser Dateien ist nur verfügbar auf Geräten, die das Netzwerk Freigabe (SMB)-Protokoll unterstützen: Desktop und Xbox. 

### <a name="register-with-windeployappcmd"></a>Registrieren mit WinDeployAppCmd

Wenn Sie die SDK-Tools, die entsprechende auf Windows 10 Creators Update (Build 14965) oder höher verwenden, können Sie mithilfe der `WinDeployAppCmd` Befehl in einer Befehlszeile eingeben.

```cmd
WinAppDeployCmd.exe registerfiles -remotedeploydir <Network Path> -ip <IP Address> -pin <target machine PIN>
```

**Netzwerkpfad** – der Pfad zu der app lose Dateien.

**IP-Adresse** – die IP-Adresse des Zielcomputers.

**Zielcomputer PIN** – eine PIN, bei Bedarf herstellen eine Verbindung mit dem Zielgerät. Werden Sie aufgefordert, wiederholen Sie mit den `-pin` option, wenn eine Authentifizierung erforderlich ist. Finden Sie unter [Gerätesuche](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development#device-discovery) erfahren Sie, wie Sie eine PIN erhalten.

### <a name="windows-device-portal"></a>Windows Geräteportal

Windows Device Portal ist auf allen Windows 10-Geräten verfügbar und wird von Entwicklern verwendet, um zu testen, und überprüfen ihre Arbeit. Es bietet für alle Beteiligten der Entwicklercommunity mit den Browser UX und REST-Endpunkte. Weitere Informationen zum Device Portal finden Sie in der [Übersicht über Windows Device Portal](device-portal.md).

Gehen Sie folgendermaßen vor, um das Layout registrieren loser Dateien im Device Portal registrieren.

1. Verbinden Sie mithilfe der Schritte im Abschnitt für die [Übersicht über Windows Device Portal](device-portal.md) **Einrichten** Device Portal.
1. Wählen Sie in der Registerkarte Apps-Manager **von Netzwerkfreigabe zu registrieren**.
1. Geben Sie die Netzwerk-Freigabepfad auf das Layout loser Datei. 
1. Wenn der Host-Gerät den Zugriff auf die Netzwerkfreigabe besitzt, wird eine Aufforderung zur Eingabe der Anmeldeinformationen erforderlichen sein.
1. Nachdem die Registrierung abgeschlossen ist, können Sie die app starten.

Auf dem Device Portal Apps-Manager-Seite können Sie auch optionale loser Dateilayouts für Ihre Haupt-app registrieren, durch Aktivieren des Kontrollkästchens **festzulegen, welche optionalen Pakete werden soll** und dann die Freigabe Netzwerkpfade der optionalen apps angeben. 

### <a name="powershell"></a>PowerShell 

Windows PowerShell ermöglicht auch, lose Dateilayouts, aber nur auf dem lokalen Gerät zu registrieren. Wenn Sie ein Layout auf einem Remotegerät registrieren möchten, müssen Sie eine der anderen Methoden verwenden. 

Um das Layout loser Datei registrieren, starten Sie PowerShell, und geben Sie Folgendes.

```PowerShell
Add-AppxPackage -Register <path to manifest file>
```

## <a name="troubleshooting"></a>Problembehandlung

### <a name="mapped-network-drives"></a>Zugeordnete Netzwerklaufwerke
Derzeit sind nicht zugeordneten Netzwerklaufwerken für lose Datei Registrierungen unterstützt. Verweisen Sie auf das zugeordnete Laufwerk mit vollständigem den Netzwerk-Freigabepfad.

### <a name="registration-failure"></a>Registrierungsfehler
Das Gerät, auf dem die Registrierung stattfindet, müssen Zugriff auf das Dateilayout haben. Wenn das Layout der Datei auf einer Netzwerkfreigabe gehostet wird, stellen Sie sicher, dass das Gerät zugreifen kann. 

### <a name="modifications-to-visual-assets-arent-being-loaded-in-the-app"></a>Änderungen an visuellen Ressourcen sind nicht in der app geladen wird 
Die app wird die visuellen Anlagen beim Starten geladen. Wenn Änderungen für die visuellen Ressourcen nach dem Starten der app vorgenommen wurden, müssen Sie die app, um die neuesten Änderungen anzeigen neu starten.