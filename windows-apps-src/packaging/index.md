---
author: laurenhughes
ms.assetid: 1abcbb13-80f0-4bf1-a812-649ee8bd1915
title: Verpacken von Apps
description: Dieser Abschnitt enthält Artikel oder Links zum Verpacken von UWP (Universelle Windows-Plattform)-Apps.
ms.author: lahugh
ms.date: 09/30/2018
ms.topic: article
keywords: Windows10, UWP, Verpacken
ms.localizationpriority: medium
ms.openlocfilehash: fa18ff3c5910dfb3a0f4c2f89407cda1fc736146
ms.sourcegitcommit: 4d88adfaf544a3dab05f4660e2f59bbe60311c00
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "6470580"
---
# <a name="packaging-apps"></a>Verpacken von Apps


## <a name="purpose"></a>Zweck

Dieser Abschnitt enthält Artikel oder Links zum Verpacken von UWP (Universelle Windows-Plattform)-Apps.

| Thema | Beschreibung |
|-------|-------------|
| [Verpacken einer UWP-App mit Visual Studio](packaging-uwp-apps.md) | Um Ihre UWP-App (Universelle Windows-Plattform) zu vertreiben und zu verkaufen, müssen Sie ein App-Paket erstellen. |
| [Manuelles Verpacken von Apps](manual-packaging-root.md) | Wenn Sie ein App-Paket erstellen und signieren möchten, für die Entwicklung der App aber nicht Visual Studio verwendet haben, müssen Sie die Tools für die manuelle App-Verpackung verwenden. |
| [App-Paketarchitektur](device-architecture.md) | Hier erfahren Sie mehr über die Prozessorarchitekturen, die beim Erstellen des UWP-App-Pakets verwendet werden sollten. |
| [UWP-App-Streaming-Installation](streaming-install.md) | Durch die Installation des Universelle Windows Plattform (UWP)-App-Streaming können Sie angeben, welche Teile der App der Microsoft Store zuerst herunterladen soll. Wenn die wichtigen Dateien der App zuerst heruntergeladen werden, können Benutzer die App starten und mit dieser interagieren, während der Rest noch im Hintergrund heruntergeladen wird. |
| [Optionale Pakete und die Erstellung zugehöriger Sets](optional-packages.md) | Optionale Pakete enthalten Inhalte, die in ein Hauptpaket integriert werden können. Diese sind nützlich für herunterladbare Inhalte (DLC), da große Apps so im Hinblick auf Größenbeschränkungen geteilt werden, oder auch, um zusätzliche Inhalte getrennt von der ursprünglichen App zu liefern. |
| [Optionale Pakete mit ausführbarem Code](optional-packages-with-executable-code.md) | Erfahren Sie, wie Sie Visual Studio verwenden, um ein optionales Paket mit ausführbarem Code zu erstellen. |
| [Installieren von UWP-Apps mit dem App-Installer](appinstaller-root.md) | Mit dem App-Installer können UWP-Apps durch Doppelklicken auf das App-Paket installiert werden. |
| [Installieren von Apps mit dem Tool WinAppDeployCmd.exe](install-universal-windows-apps-with-the-winappdeploycmd-tool.md) | Windows-Anwendungsbereitstellung (WinAppDeployCmd.exe) ist ein Befehlszeilentool, mit denen eine UWP-app von einem Windows 10-Computer auf beliebigen Windows 10 Mobile-Geräten bereitstellen. Sie können dieses Tool verwenden, um ein app-Paket bereitzustellen, wenn das Windows 10 Mobile-Gerät über USB verbunden ist oder sich im gleichen Subnetz verfügbar ist, ohne Microsoft Visual Studio oder die Projektmappe für diese app. Dieser Artikel beschreibt, wie UWP-Apps mit diesem Tool installiert werden. |
| [Einrichten automatisierter Builds für UWP-Apps](auto-build-package-uwp-apps.md) | Wenn Sie Ihre App als Teil eines automatisierten Buildprozesses packen möchten, erfahren Sie hier, wie Sie Visual Studio Team Services (VSTS) dazu verwenden können. |
| [Deklarationen der App-Funktionen](app-capability-declarations.md) | Funktionen müssen im [Paketmanifest](https://msdn.microsoft.com/library/windows/apps/BR211474) der UWP-App für den Zugriff auf bestimmte APIs oder Ressourcen deklariert werden, z.B. Bilder, Musik oder Geräte wie die Kamera oder das Mikrofon. |
| [Herunterladen und Installieren von Paketupdates aus dem Store](self-install-package-updates.md) | Ihre UWP-App kann programmgesteuert nach Paketupdates suchen und die Updates installieren. Ihre app kann auch Abfragen für Pakete, die im Partner Center als obligatorisch gekennzeichnet wurden und Funktionen deaktivieren, bis das erforderliche Update installiert ist.  |
