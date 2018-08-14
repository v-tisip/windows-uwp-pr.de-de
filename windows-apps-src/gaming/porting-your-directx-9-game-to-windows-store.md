---
author: mtoepke
title: Portieren von DirectX9 zur Universellen Windows-Plattform (UWP)
description: Dieser Abschnitt enthält Artikel, Übersichten und exemplarische Vorgehensweisen zum Portieren von DirectX 9-Spielen zur Universellen Windows-Plattform (UWP).
ms.assetid: 536c0b99-cdf3-1527-1ee2-4187f50a2cf0
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Spiele, Directx 9, Directx 11, Portieren
ms.openlocfilehash: 9ea27288fd239b2af4b63985a3c8e0ad4055b0b9
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
ms.translationtype: MT
ms.contentlocale: de-DE
ms.locfileid: "233710"
---
# <a name="port-from-directx-9-to-universal-windows-platform-uwp"></a><span data-ttu-id="f27d9-104">Portieren von DirectX9 zur Universellen Windows-Plattform (UWP)</span><span class="sxs-lookup"><span data-stu-id="f27d9-104">Port from DirectX 9 to Universal Windows Platform (UWP)</span></span>


<span data-ttu-id="f27d9-105">\[ Aktualisiert für UWP-Apps unter Windows 10.</span><span class="sxs-lookup"><span data-stu-id="f27d9-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="f27d9-106">Artikel zu Windows 8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span><span class="sxs-lookup"><span data-stu-id="f27d9-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>

<span data-ttu-id="f27d9-107">Dieser Abschnitt enthält Artikel, Übersichten und exemplarische Vorgehensweisen zum Portieren von DirectX 9-Spielen zur Universellen Windows-Plattform (UWP).</span><span class="sxs-lookup"><span data-stu-id="f27d9-107">This section includes articles, overviews, and walkthroughs for porting DirectX 9 games to Universal Windows Platform (UWP).</span></span>

##  <a name="port-your-directx-9-game-to-uwp"></a><span data-ttu-id="f27d9-108">Portieren von DirectX 9-Spielen zu UWP</span><span class="sxs-lookup"><span data-stu-id="f27d9-108">Port your DirectX 9 game to UWP</span></span>


-   <span data-ttu-id="f27d9-109">Erreichen der UWP-Zielgruppe, um mit dem Spiel Geld zu verdienen</span><span class="sxs-lookup"><span data-stu-id="f27d9-109">Reach the UWP audiences and monetize your game.</span></span>
-   <span data-ttu-id="f27d9-110">Erreichen einer großen Zahl von Geräten, auf denen jeweils mindestens die Direct3D9.1-Grafikfeatures unterstützt werden</span><span class="sxs-lookup"><span data-stu-id="f27d9-110">Target a wide array of devices, all of which support at least the Direct3D 9.1 set of graphics features.</span></span>
-   <span data-ttu-id="f27d9-111">Erlernen wertvoller neuer Fähigkeiten zur Entwicklung von Windows-Spielen, z.B. Direct3D11, vereinheitlichte Shadermodelle, Windows-APIs, XAudio2, Toucheingabe, C++/CX usw.</span><span class="sxs-lookup"><span data-stu-id="f27d9-111">Learn valuable new Windows game development skills - including Direct3D 11, the unified shader models, Windows APIs, XAudio2, touch input, C++/CX and more.</span></span>

## <a name="where-do-i-start"></a><span data-ttu-id="f27d9-112">Wo soll ich beginnen?</span><span class="sxs-lookup"><span data-stu-id="f27d9-112">Where do I start?</span></span>


-   <span data-ttu-id="f27d9-113">Unter [Wechseln von DirectX 9 zu DirectX 11 und zu UWP](porting-considerations.md) wird beschrieben, was Sie beim Planen Ihres Projekts zum Portieren von Spielen beachten sollten. Außerdem erfahren Sie mehr zu den Direct3D 11-Konzepten und dazu, wie die vertrauten Features für DirectX 11-UWP-Apps gelten.</span><span class="sxs-lookup"><span data-stu-id="f27d9-113">Visit [Moving from DirectX 9 to DirectX 11 and UWP](porting-considerations.md) to learn what you should plan for in your game porting project, catch up on Direct3D 11 concepts, and understand how the features you're familiar with map to DirectX 11 UWP apps.</span></span>
-   <span data-ttu-id="f27d9-114">Die exemplarische Vorgehensweise unter [Portieren einer einfachen Direct3D 9-App zu DirectX 11 und zu UWP](walkthrough--simple-port-from-direct3d-9-to-11-1.md) enthält einen direkten Vergleich von Direct3D 9- und Direct3D 11-Grafikframeworks.</span><span class="sxs-lookup"><span data-stu-id="f27d9-114">Follow the [Port a simple Direct3D 9 app to DirectX 11 and UWP](walkthrough--simple-port-from-direct3d-9-to-11-1.md) walkthrough article for a direct comparison of Direct3D 9 and Direct3D 11 graphics frameworks.</span></span> <span data-ttu-id="f27d9-115">Außerdem erhalten Sie dort einen Code zum Einrichten eines App-Fensters und -Viewports.</span><span class="sxs-lookup"><span data-stu-id="f27d9-115">This walkthrough also has code for setting up an app window and viewport.</span></span>
-   <span data-ttu-id="f27d9-116">Antworten auf häufig gestellte Fragen zum Portieren aus DirectX 9 finden Sie unter [DirectX 11.-Portierung – Häufig gestellte Fragen](directx-porting-faq.md).</span><span class="sxs-lookup"><span data-stu-id="f27d9-116">See the [DirectX 11 porting FAQ](directx-porting-faq.md) for answers to common questions about porting from DirectX 9.</span></span>

 

 




