---
author: JordanEllis6809
title: Portieren von Unity-Spielen für Xbox auf die UWP
description: UWP-Entwicklung für Unity-Spiele auf Xbox.
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp
ms.assetid: fca3267a-0c0f-4872-8017-90384fb34215
ms.localizationpriority: medium
ms.openlocfilehash: 4c8bebd6b15a58979975180536cf037b2c61e71b
ms.sourcegitcommit: 6618517dc0a4e4100af06e6d27fac133d317e545
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2018
ms.locfileid: "1690416"
---
# <a name="bringing-unity-games-to-uwp-on-xbox"></a>Portieren von Unity-Spielen für Xbox auf die UWP


In diesem ausführlichen Lernprogramm wird davon ausgegangen, dass Sie bereits über ein Spiel in Unity verfügen, das zum Erstellen und Bereitstellen bereit ist.

Beachten Sie auch die [Videoversion des Lernprogramms](https://www.youtube.com/watch?v=f0Ptvw7k-CE).

Möchten Sie eine Versionsverwaltung für Ihr Unity-UWP-Projekt verwenden? Siehe [Versionskontrolle für Ihr UWP-Projekt](development-lanes-unity-versioning.md).

## <a name="step-0-ensure-unity-is-installed-correctly"></a>Schritt0: Sicherstellen, dass Unity richtig installiert wurde

Beim Installieren von Unity müssen folgende Komponenten ausgewählt sein:

![Installationskomponenten von Unity](images/unity-install-components.png)

## <a name="step-1-building-the-uwp-solution"></a>Schritt 1: Erstellen der UWP-Lösung

Öffnen Sie in Ihrem Unity-Spielprojekt das Fenster mit den **Build-Einstellungen** unter **Datei -> Build-Einstellungen**, und wechseln Sie zum Menü mit den Microsoft Store-Optionen.

![Fenster mit Build-Einstellungen](images/build-settings.png)

Stellen Sie sicher, dass die **SDK**-Einstellung auf **Universal10** gesetzt ist, und klicken Sie dann auf die Schaltfläche **Build**. Ein Datei-Explorer-Fenster wird geöffnet, in dem Sie nach einem Zielordner gefragt werden. Erstellen Sie neben dem Verzeichnis **Assets** Ihres Projekts den Ordner **UWP**, und wählen Sie diesen Ordner als Zielordner des Builds aus.

![Build-Zielordner](images/build-destination.png)

Unity hat eine neue Visual Studio-Lösung erstellt, die wir zum Bereitstellen Ihres UWP-Spiels verwenden.

![UWP-VS-Lösung](images/uwp-vs-solution.png)

## <a name="step-2-deploying-your-game"></a>Schritt 2: Bereitstellen des Spiels

Öffnen Sie die neu erstellte Lösung im Ordner **UWP**, und ändern Sie die Zielplattform zu **x64**.

![x64-Build-Plattform](images/x64-build-platform.png)

Nachdem Sie nun über eine Visual Studio-UWP-Lösung für Ihr Spiel verfügen, [befolgen Sie diese Schritte](getting-started.md), um Ihr Spiel erfolgreich auf Ihrer Xbox One-Konsole für den Einzelhandel bereitzustellen!

## <a name="step-3-modify-and-rebuild"></a>Schritt3: Ändern und Neuerstellen

Wenn etwas anderes als ein Skript geändert wird, muss das Projekt im Editor neu erstellt werden (siehe __Schritt1__), damit die Änderungen in den UWP-Build Ihres Spiel übernommen werden.

## <a name="versioning-your-uwp-project"></a>Versionsverwaltung für Ihr UWP-Projekt

In bestimmten Situationen müssen Teile dieses neu generierten UWP-Verzeichnisses der Versionskontrolle hinzugefügt werden. Dies ist beispielsweise der Fall, wenn Sie dem UWP-Projekt eine neue Abhängigkeit (z.B. das Xbox Live SDK) hinzufügen.  Wir betrachten dieses Beispiel unter [Versionskontrolle für Ihr UWP-Projekt](development-lanes-unity-versioning.md) ausführlich.

## <a name="see-also"></a>Weitere Informationen
- [Portieren vorhandener Spiele zu Xbox](development-lanes-landing.md)
- [UWP auf XboxOne](index.md)
