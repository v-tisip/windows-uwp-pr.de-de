---
author: mtoepke
title: Grundlegendes zu 3D-Grafiken für DirectX-Spiele
description: Im Folgenden wird gezeigt, wie Sie grundlegende Konzepte von 3D-Grafiken durch die Programmierung mit DirectX umsetzen können.
ms.assetid: 2989c91f-7b45-7377-4e83-9daa0325e92e
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Spiele, DirectX, Grafiken
ms.openlocfilehash: 2ac11ce220bc1c62c81df12fbf9c2a41fda1d940
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
ms.translationtype: MT
ms.contentlocale: de-DE
ms.locfileid: "233590"
---
# <a name="basic-3d-graphics-for-directx-games"></a><span data-ttu-id="1e6d6-104">Grundlegendes zu 3D-Grafiken für DirectX-Spiele</span><span class="sxs-lookup"><span data-stu-id="1e6d6-104">Basic 3D graphics for DirectX games</span></span>


<span data-ttu-id="1e6d6-105">\[ Aktualisiert für UWP-Apps unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="1e6d6-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="1e6d6-106">Artikel zu Windows 8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span><span class="sxs-lookup"><span data-stu-id="1e6d6-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>

<span data-ttu-id="1e6d6-107">Im Folgenden zeigen wir Ihnen, wie Sie grundlegende Konzepte von 3D-Grafiken durch die Programmierung mit DirectX umsetzen können.</span><span class="sxs-lookup"><span data-stu-id="1e6d6-107">We show how to use DirectX programming to implement the fundamental concepts of 3D graphics.</span></span>

<span data-ttu-id="1e6d6-108">**Ziel:** Lernen Sie, eine 3D-Grafik-App zu programmieren.</span><span class="sxs-lookup"><span data-stu-id="1e6d6-108">**Objective:** Learn to program a 3D graphics app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1e6d6-109">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="1e6d6-109">Prerequisites</span></span>


<span data-ttu-id="1e6d6-110">Es wird davon ausgegangen, dass Sie mit C+ vertraut sind.</span><span class="sxs-lookup"><span data-stu-id="1e6d6-110">We assume that you are familiar with C++.</span></span> <span data-ttu-id="1e6d6-111">Sie müssen außerdem mit den grundlegenden Konzepten der Grafikprogrammierung vertraut sein.</span><span class="sxs-lookup"><span data-stu-id="1e6d6-111">You also need basic experience with graphics programming concepts.</span></span>

<span data-ttu-id="1e6d6-112">**Gesamter Zeitaufwand:** 30 Minuten</span><span class="sxs-lookup"><span data-stu-id="1e6d6-112">**Total time to complete:** 30 minutes.</span></span>

## <a name="where-to-go-from-here"></a><span data-ttu-id="1e6d6-113">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="1e6d6-113">Where to go from here</span></span>


<span data-ttu-id="1e6d6-114">Hier geht es um die Entwicklung von 3D-Grafiken mit DirectX und C ++\\Cx.</span><span class="sxs-lookup"><span data-stu-id="1e6d6-114">Here, we talk about how to develop 3D graphics with DirectX and C++\\Cx.</span></span> <span data-ttu-id="1e6d6-115">In diesem fünfteiligen Lernprogramm werden die [Direct3D](https://msdn.microsoft.com/library/windows/desktop/hh309466)-API sowie die Konzepte und der Code vorgestellt, die auch in zahlreichen anderen DirectX-Beispielen zum Einsatz kommen.</span><span class="sxs-lookup"><span data-stu-id="1e6d6-115">This five-part tutorial introduces you to the [Direct3D](https://msdn.microsoft.com/library/windows/desktop/hh309466) API and the concepts and code that are also used in many of the other DirectX samples.</span></span> <span data-ttu-id="1e6d6-116">Die einzelnen Teile bauen aufeinander auf. Sie behandeln u. a. das Konfigurieren von DirectX für Ihre UWP-App mit C++ sowie Grundtypen mit Texturen und das Hinzufügen von Effekten.</span><span class="sxs-lookup"><span data-stu-id="1e6d6-116">These parts build upon each other, from configuring DirectX for your UWP C++ app to texturing primitives and adding effects.</span></span>

> <span data-ttu-id="1e6d6-117">**Hinweis**  In diesem Lernprogramm wird ein rechtshändiges Koordinatensystem mit Spaltenvektoren verwendet.</span><span class="sxs-lookup"><span data-stu-id="1e6d6-117">**Note**  This tutorial uses a right-handed coordinate system with column vectors.</span></span> <span data-ttu-id="1e6d6-118">Bei vielen DirectX-Beispielen und -Apps wird ein linkshändiges Koordinatensystem mit Zeilenvektoren verwendet.</span><span class="sxs-lookup"><span data-stu-id="1e6d6-118">Many DirectX samples and apps use a left-handed coordinate system with row vectors.</span></span> <span data-ttu-id="1e6d6-119">Für eine umfangreichere mathematische Grafiklösung, die ein linkshändiges Koordinatensystem mit Zeilenvektoren unterstützt, sollten Sie [DirectXMath](https://msdn.microsoft.com/library/windows/desktop/hh437833) verwenden.</span><span class="sxs-lookup"><span data-stu-id="1e6d6-119">For a more complete graphics math solution and one that supports a left-handed coordinate system with row vectors, consider using [DirectXMath](https://msdn.microsoft.com/library/windows/desktop/hh437833).</span></span> <span data-ttu-id="1e6d6-120">Weitere Informationen finden Sie unter [Verwenden von DirectXMath mit Direct3D](https://msdn.microsoft.com/library/windows/desktop/ff729728#Use_DXMath_with_D3D).</span><span class="sxs-lookup"><span data-stu-id="1e6d6-120">For more info, see [Using DirectXMath with Direct3D](https://msdn.microsoft.com/library/windows/desktop/ff729728#Use_DXMath_with_D3D).</span></span>

 

<span data-ttu-id="1e6d6-121">Folgende Inhalte werden behandelt:</span><span class="sxs-lookup"><span data-stu-id="1e6d6-121">We show you how to:</span></span>

-   <span data-ttu-id="1e6d6-122">Initialisieren von [Direct3D](https://msdn.microsoft.com/library/windows/desktop/hh309466)-Schnittstellen mit der Windows-Runtime</span><span class="sxs-lookup"><span data-stu-id="1e6d6-122">Initialize [Direct3D](https://msdn.microsoft.com/library/windows/desktop/hh309466) interfaces by using the Windows Runtime</span></span>
-   <span data-ttu-id="1e6d6-123">Anwenden von Vertex-Shader-Operationen</span><span class="sxs-lookup"><span data-stu-id="1e6d6-123">Apply per-vertex shader operations</span></span>
-   <span data-ttu-id="1e6d6-124">Einrichten der Geometrie</span><span class="sxs-lookup"><span data-stu-id="1e6d6-124">Set up the geometry</span></span>
-   <span data-ttu-id="1e6d6-125">Rastern der Szene (Glätten der 3D-Szene auf eine 2D-Projektion)</span><span class="sxs-lookup"><span data-stu-id="1e6d6-125">Rasterize the scene (flattening the 3D scene to a 2D projection)</span></span>
-   <span data-ttu-id="1e6d6-126">Culling verborgener Oberflächen</span><span class="sxs-lookup"><span data-stu-id="1e6d6-126">Cull the hidden surfaces</span></span>

> **<span data-ttu-id="1e6d6-127">Hinweis</span><span class="sxs-lookup"><span data-stu-id="1e6d6-127">Note</span></span>**  
<span data-ttu-id="1e6d6-128">Dieser Artikel ist für Windows10-Entwickler bestimmt, die Apps für die universelle Windows-Plattform (UWP) schreiben.</span><span class="sxs-lookup"><span data-stu-id="1e6d6-128">This article is for Windows 10 developers writing Universal Windows Platform (UWP) apps.</span></span> <span data-ttu-id="1e6d6-129">Wenn Sie für Windows 8.x oder Windows Phone 8.x entwickeln, finden Sie Informationen dazu in der [archivierten Dokumentation](http://go.microsoft.com/fwlink/p/?linkid=619132).</span><span class="sxs-lookup"><span data-stu-id="1e6d6-129">If you’re developing for Windows 8.x or Windows Phone 8.x, see the [archived documentation](http://go.microsoft.com/fwlink/p/?linkid=619132).</span></span>

 

<span data-ttu-id="1e6d6-130">Als Nächstes erstellen wir ein Direct3D-Gerät, eine Swapchain sowie eine Renderingzielansicht und stellen das gerenderte Bild auf dem Display dar.</span><span class="sxs-lookup"><span data-stu-id="1e6d6-130">Next, we create a Direct3D device, swap chain, and render-target view, and present the rendered image to the display.</span></span>

[<span data-ttu-id="1e6d6-131">Schnellstart: Einrichten von DirectX-Ressourcen und Anzeigen eines Bilds</span><span class="sxs-lookup"><span data-stu-id="1e6d6-131">Quickstart: setting up DirectX resources and displaying an image</span></span>](setting-up-directx-resources.md)

## <a name="related-topics"></a><span data-ttu-id="1e6d6-132">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="1e6d6-132">Related topics</span></span>


* [<span data-ttu-id="1e6d6-133">Direct3D 11-Grafik</span><span class="sxs-lookup"><span data-stu-id="1e6d6-133">Direct3D 11 Graphics</span></span>](https://msdn.microsoft.com/library/windows/desktop/ff476080)
* [<span data-ttu-id="1e6d6-134">DXGI</span><span class="sxs-lookup"><span data-stu-id="1e6d6-134">DXGI</span></span>](https://msdn.microsoft.com/library/windows/desktop/hh404534)
* [<span data-ttu-id="1e6d6-135">HLSL</span><span class="sxs-lookup"><span data-stu-id="1e6d6-135">HLSL</span></span>](https://msdn.microsoft.com/library/windows/desktop/bb509561)

 

 




