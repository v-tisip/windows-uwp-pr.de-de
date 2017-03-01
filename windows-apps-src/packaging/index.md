---
author: laurenhughes
ms.assetid: 1abcbb13-80f0-4bf1-a812-649ee8bd1915
title: Verpacken von Apps
description: "Dieser Abschnitt enthält Artikel oder Links zum Verpacken von UWP (Universelle Windows-Plattform)-Apps."
ms.author: lahugh
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: 0a9689738fac363012fb9af197f52ac8813b47c9
ms.lasthandoff: 02/07/2017

---
# <a name="packaging-apps"></a>Verpacken von Apps

\[ Aktualisiert für UWP-Apps unter Windows 10. Artikel zu Windows 8.x finden Sie unter [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]

## <a name="purpose"></a>Zweck

Dieser Abschnitt enthält Artikel oder Links zum Verpacken von UWP (Universelle Windows-Plattform)-Apps.

| Thema | Beschreibung |
|-------|-------------|
| [Verpacken von UWP-Apps](packaging-uwp-apps.md) | Um Ihre UWP-App zu verkaufen oder an andere Benutzer zu verteilen, müssen Sie ein APPXUPLOAD-Paket erstellen. Beim Erstellen des APPXUPLOAD-Pakets wird ein weiteres APPX-Paket für Testzwecke und das Querladen generiert. Sie können Ihre App direkt verteilen, indem Sie das APPX-Paket durch Querladen auf einem Gerät installieren. In diesem Artikel wird das Konfigurieren, Erstellen und Testen von UWP-App-Paketen beschrieben. Weitere Informationen über das Querladen finden Sie unter [Querladen von Apps mit DISM](http://go.microsoft.com/fwlink/?LinkID=231020). |
| [Erstellen eines App-Pakets mit dem Tool „MakeAppx.exe“](create-app-package-with-makeappx-tool.md) | MakeAppx.exe erstellt, verschlüsselt, entschlüsselt und extrahiert Dateien aus App-Paketen und -Bündeln. |
| [Erstellen von Zertifikaten für die Paketsignatur](create-certificate-package-signing.md) | Erstellen und Exportieren eines Zertifikats für die App-Paketsignatur mit PowerShell-Tools. |
| [Signieren eines App-Pakets mit SignTool](sign-app-package-using-signtool.md) | Verwenden von SignTool zur manuellen Signatur eines App-Pakets mit einem Zertifikat. |
| [Installieren von Apps mit dem Tool WinAppDeployCmd.exe](install-universal-windows-apps-with-the-winappdeploycmd-tool.md) | Windows Application Deployment (WinAppDeployCmd.exe) ist ein Befehlszeilen-Tool, mit dem Sie UWP-Apps von einem Windows 10-Computer auf jedes beliebige Windows 10 Mobile-Gerät bereitstellen können. Dieses Tool ermöglicht die Bereitstellung eines APPX-Pakets, wenn das Windows 10 Mobile-Gerät über USB verbunden ist oder sich im selben Subnetz befindet, ohne dass Microsoft Visual Studio oder die Projektmappe für diese App erforderlich ist. Dieser Artikel beschreibt, wie UWP-Apps mit diesem Tool installiert werden. |
| [Einrichten automatisierter Builds für UWP-Apps](auto-build-package-uwp-apps.md) | Wenn Sie Ihre App als Teil eines automatisierten Buildprozesses packen möchten, erfahren Sie hier, wie Sie Visual Studio Team Services (VSTS) dazu verwenden können. |
| [Deklarationen der App-Funktionen](app-capability-declarations.md) | Funktionen müssen im [Paketmanifest](https://msdn.microsoft.com/library/windows/apps/BR211474) der UWP-App für den Zugriff auf bestimmte APIs oder Ressourcen deklariert werden, z. B. Bilder, Musik oder Geräte wie die Kamera oder das Mikrofon. |
| [Herunterladen und Installieren von Paketupdates für Ihre App](self-install-package-updates.md) | Ihre UWP-App kann programmgesteuert nach Paketupdates suchen und die Updates installieren. Ihre App kann auch Abfragen für Pakete ausführen, die im Windows Dev Center-Dashboard als obligatorisch gekennzeichnet wurden, und Funktionen deaktivieren, bis das erforderliche Update installiert wird. Dieser Artikel beschreibt, wie Sie diese Aufgaben ausführen. |
 

