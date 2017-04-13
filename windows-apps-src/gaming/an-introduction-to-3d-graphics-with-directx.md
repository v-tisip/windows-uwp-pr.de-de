---
author: mtoepke
title: "Grundlegendes zu 3D-Grafiken für DirectX-Spiele"
description: "Im Folgenden wird gezeigt, wie Sie grundlegende Konzepte von 3D-Grafiken durch die Programmierung mit DirectX umsetzen können."
ms.assetid: 2989c91f-7b45-7377-4e83-9daa0325e92e
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Spiele, DirectX, Grafiken
ms.openlocfilehash: 2ac11ce220bc1c62c81df12fbf9c2a41fda1d940
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="basic-3d-graphics-for-directx-games"></a>Grundlegendes zu 3D-Grafiken für DirectX-Spiele


\[ Aktualisiert für UWP-Apps unter Windows10. Artikel zu Windows 8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]

Im Folgenden zeigen wir Ihnen, wie Sie grundlegende Konzepte von 3D-Grafiken durch die Programmierung mit DirectX umsetzen können.

**Ziel:** Lernen Sie, eine 3D-Grafik-App zu programmieren.

## <a name="prerequisites"></a>Voraussetzungen


Es wird davon ausgegangen, dass Sie mit C+ vertraut sind. Sie müssen außerdem mit den grundlegenden Konzepten der Grafikprogrammierung vertraut sein.

**Gesamter Zeitaufwand:** 30 Minuten

## <a name="where-to-go-from-here"></a>Weitere Informationen


Hier geht es um die Entwicklung von 3D-Grafiken mit DirectX und C ++\\Cx. In diesem fünfteiligen Lernprogramm werden die [Direct3D](https://msdn.microsoft.com/library/windows/desktop/hh309466)-API sowie die Konzepte und der Code vorgestellt, die auch in zahlreichen anderen DirectX-Beispielen zum Einsatz kommen. Die einzelnen Teile bauen aufeinander auf. Sie behandeln u. a. das Konfigurieren von DirectX für Ihre UWP-App mit C++ sowie Grundtypen mit Texturen und das Hinzufügen von Effekten.

> **Hinweis**  In diesem Lernprogramm wird ein rechtshändiges Koordinatensystem mit Spaltenvektoren verwendet. Bei vielen DirectX-Beispielen und -Apps wird ein linkshändiges Koordinatensystem mit Zeilenvektoren verwendet. Für eine umfangreichere mathematische Grafiklösung, die ein linkshändiges Koordinatensystem mit Zeilenvektoren unterstützt, sollten Sie [DirectXMath](https://msdn.microsoft.com/library/windows/desktop/hh437833) verwenden. Weitere Informationen finden Sie unter [Verwenden von DirectXMath mit Direct3D](https://msdn.microsoft.com/library/windows/desktop/ff729728#Use_DXMath_with_D3D).

 

Folgende Inhalte werden behandelt:

-   Initialisieren von [Direct3D](https://msdn.microsoft.com/library/windows/desktop/hh309466)-Schnittstellen mit der Windows-Runtime
-   Anwenden von Vertex-Shader-Operationen
-   Einrichten der Geometrie
-   Rastern der Szene (Glätten der 3D-Szene auf eine 2D-Projektion)
-   Culling verborgener Oberflächen

> **Hinweis**  
Dieser Artikel ist für Windows10-Entwickler bestimmt, die Apps für die universelle Windows-Plattform (UWP) schreiben. Wenn Sie für Windows 8.x oder Windows Phone 8.x entwickeln, finden Sie Informationen dazu in der [archivierten Dokumentation](http://go.microsoft.com/fwlink/p/?linkid=619132).

 

Als Nächstes erstellen wir ein Direct3D-Gerät, eine Swapchain sowie eine Renderingzielansicht und stellen das gerenderte Bild auf dem Display dar.

[Schnellstart: Einrichten von DirectX-Ressourcen und Anzeigen eines Bilds](setting-up-directx-resources.md)

## <a name="related-topics"></a>Verwandte Themen


* [Direct3D 11-Grafik](https://msdn.microsoft.com/library/windows/desktop/ff476080)
* [DXGI](https://msdn.microsoft.com/library/windows/desktop/hh404534)
* [HLSL](https://msdn.microsoft.com/library/windows/desktop/bb509561)

 

 




