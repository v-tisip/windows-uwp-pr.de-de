---
author: laurenhughes
ms.assetid: 1abcbb13-80f0-4bf1-a812-649ee8bd1915
title: Verpacken von Apps
description: "Dieser Abschnitt enthält Artikel oder Links zum Verpacken von UWP (Universelle Windows-Plattform)-Apps."
ms.author: lahugh
ms.date: 08/09/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Verpacken
ms.openlocfilehash: 0b4f8cf2e90a125539c3dade51f6b3db78219e3f
ms.sourcegitcommit: 63c815f8c6665872987b5410cabf324f2b7e3c7c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/10/2017
---
# <a name="packaging-apps"></a>Verpacken von Apps

\[ Aktualisiert für UWP-Apps unter Windows10. Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]

## <a name="purpose"></a>Zweck

Dieser Abschnitt enthält Artikel oder Links zum Verpacken von UWP (Universelle Windows-Plattform)-Apps.

| Thema | Beschreibung |
|-------|-------------|
| [Verpacken einer UWP-App mit Visual Studio](packaging-uwp-apps.md) | Um Ihre UWP-App (Universelle Windows-Plattform) zu vertreiben und zu verkaufen, müssen Sie ein App-Paket erstellen. |
| [Manuelles Verpacken von Apps](manual-packaging-root.md) | Wenn Sie ein App-Paket erstellen und signieren möchten, für die Entwicklung der App aber nicht Visual Studio verwendet haben, müssen Sie die Tools für die manuelle App-Verpackung verwenden. |
| [App-Paketarchitektur](device-architecture.md) | Hier erfahren Sie mehr über die Prozessorarchitekturen, die beim Erstellen des UWP-App-Pakets verwendet werden sollten. | 
| [UWP-App-Streaming-Installation](streaming-install.md) | Durch die Installation von UWP(Universal Windows Platform)-App-Streaming können Sie angeben, welche Teile der App der Windows Store-zuerst herunterladen soll. Wenn die wichtigen Dateien der App zuerst heruntergeladen werden, können Benutzer die App starten und mit dieser interagieren, während der Rest noch im Hintergrund heruntergeladen wird. |
| [Optionale Pakete und die Erstellung zugehöriger Sets](optional-packages.md) | Optionale Pakete enthalten Inhalte, die in ein Hauptpaket integriert werden können. Diese sind nützlich für herunterladbare Inhalte (DLC), da große Apps so im Hinblick auf Größenbeschränkungen geteilt werden, oder auch, um zusätzliche Inhalte getrennt von der ursprünglichen App zu liefern. | 
| [Installieren von Apps mit dem Tool WinAppDeployCmd.exe](install-universal-windows-apps-with-the-winappdeploycmd-tool.md) | Die Windows-Anwendungsbereitstellung (WinAppDeployCmd.exe) ist ein Befehlszeilentool, mit dem Sie eine UWP-App von einem Windows10-Computer auf beliebigen Windows10 Mobile-Geräten bereitstellen können. Dieses Tool ermöglicht die Bereitstellung eines APPX-Pakets, wenn das Windows 10Mobile-Gerät über USB verbunden ist oder sich im selben Subnetz befindet, ohne dass Microsoft Visual Studio oder die Projektmappe für diese App erforderlich ist. Dieser Artikel beschreibt, wie UWP-Apps mit diesem Tool installiert werden. |
| [Einrichten automatisierter Builds für UWP-Apps](auto-build-package-uwp-apps.md) | Wenn Sie Ihre App als Teil eines automatisierten Buildprozesses packen möchten, erfahren Sie hier, wie Sie Visual Studio Team Services (VSTS) dazu verwenden können. |
| [Deklarationen der App-Funktionen](app-capability-declarations.md) | Funktionen müssen im [Paketmanifest](https://msdn.microsoft.com/library/windows/apps/BR211474) der UWP-App für den Zugriff auf bestimmte APIs oder Ressourcen deklariert werden, z.B. Bilder, Musik oder Geräte wie die Kamera oder das Mikrofon. |
| [Herunterladen und Installieren von Paketupdates für Ihre App](self-install-package-updates.md) | Ihre UWP-App kann programmgesteuert nach Paketupdates suchen und die Updates installieren. Ihre App kann auch Abfragen für Pakete ausführen, die im Windows Dev Center-Dashboard als obligatorisch gekennzeichnet wurden, und Funktionen deaktivieren, bis das erforderliche Update installiert wird. Dieser Artikel beschreibt, wie Sie diese Aufgaben ausführen. |