---
author: mtoepke
title: Grundlegendes zu 3D-Grafiken für DirectX-Spiele
description: Im Folgenden wird gezeigt, wie Sie grundlegende Konzepte von 3D-Grafiken durch die Programmierung mit DirectX umsetzen können.
ms.assetid: 2989c91f-7b45-7377-4e83-9daa0325e92e
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, DirectX, Grafiken
ms.localizationpriority: medium
ms.openlocfilehash: e9834a83620343f26acaabd0e05b30cc2c1dcfab
ms.sourcegitcommit: cbe7cf620622a5e4df7414f9e38dfecec1cfca99
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "7429982"
---
# <a name="basic-3d-graphics-for-directx-games"></a><span data-ttu-id="b3f38-104">Grundlegendes zu 3D-Grafiken für DirectX-Spiele</span><span class="sxs-lookup"><span data-stu-id="b3f38-104">Basic 3D graphics for DirectX games</span></span>



<span data-ttu-id="b3f38-105">Im Folgenden zeigen wir Ihnen, wie Sie grundlegende Konzepte von 3D-Grafiken durch die Programmierung mit DirectX umsetzen können.</span><span class="sxs-lookup"><span data-stu-id="b3f38-105">We show how to use DirectX programming to implement the fundamental concepts of 3D graphics.</span></span>

<span data-ttu-id="b3f38-106">**Ziel:** Lernen Sie, eine 3D-Grafik-App zu programmieren.</span><span class="sxs-lookup"><span data-stu-id="b3f38-106">**Objective:** Learn to program a 3D graphics app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b3f38-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="b3f38-107">Prerequisites</span></span>


<span data-ttu-id="b3f38-108">Es wird davon ausgegangen, dass Sie mit C+ vertraut sind.</span><span class="sxs-lookup"><span data-stu-id="b3f38-108">We assume that you are familiar with C++.</span></span> <span data-ttu-id="b3f38-109">Sie müssen außerdem mit den grundlegenden Konzepten der Grafikprogrammierung vertraut sein.</span><span class="sxs-lookup"><span data-stu-id="b3f38-109">You also need basic experience with graphics programming concepts.</span></span>

<span data-ttu-id="b3f38-110">**Gesamter Zeitaufwand:** 30 Minuten</span><span class="sxs-lookup"><span data-stu-id="b3f38-110">**Total time to complete:** 30 minutes.</span></span>

## <a name="where-to-go-from-here"></a><span data-ttu-id="b3f38-111">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b3f38-111">Where to go from here</span></span>


<span data-ttu-id="b3f38-112">Hier geht es um die Entwicklung von 3D-Grafiken mit DirectX und C ++\\Cx.</span><span class="sxs-lookup"><span data-stu-id="b3f38-112">Here, we talk about how to develop 3D graphics with DirectX and C++\\Cx.</span></span> <span data-ttu-id="b3f38-113">In diesem fünfteiligen Lernprogramm werden die [Direct3D](https://msdn.microsoft.com/library/windows/desktop/hh309466)-API sowie die Konzepte und der Code vorgestellt, die auch in zahlreichen anderen DirectX-Beispielen zum Einsatz kommen.</span><span class="sxs-lookup"><span data-stu-id="b3f38-113">This five-part tutorial introduces you to the [Direct3D](https://msdn.microsoft.com/library/windows/desktop/hh309466) API and the concepts and code that are also used in many of the other DirectX samples.</span></span> <span data-ttu-id="b3f38-114">Die einzelnen Teile bauen aufeinander auf. Sie behandeln u. a. das Konfigurieren von DirectX für Ihre UWP-App mit C++ sowie Grundtypen mit Texturen und das Hinzufügen von Effekten.</span><span class="sxs-lookup"><span data-stu-id="b3f38-114">These parts build upon each other, from configuring DirectX for your UWP C++ app to texturing primitives and adding effects.</span></span>

> <span data-ttu-id="b3f38-115">**Hinweis:** in diesem Lernprogramm wird ein rechtshändiges Koordinatensystem mit Spaltenvektoren verwendet.</span><span class="sxs-lookup"><span data-stu-id="b3f38-115">**Note**This tutorial uses a right-handed coordinate system with column vectors.</span></span> <span data-ttu-id="b3f38-116">Bei vielen DirectX-Beispielen und -Apps wird ein linkshändiges Koordinatensystem mit Zeilenvektoren verwendet.</span><span class="sxs-lookup"><span data-stu-id="b3f38-116">Many DirectX samples and apps use a left-handed coordinate system with row vectors.</span></span> <span data-ttu-id="b3f38-117">Für eine umfangreichere mathematische Grafiklösung, die ein linkshändiges Koordinatensystem mit Zeilenvektoren unterstützt, sollten Sie [DirectXMath](https://msdn.microsoft.com/library/windows/desktop/hh437833) verwenden.</span><span class="sxs-lookup"><span data-stu-id="b3f38-117">For a more complete graphics math solution and one that supports a left-handed coordinate system with row vectors, consider using [DirectXMath](https://msdn.microsoft.com/library/windows/desktop/hh437833).</span></span> <span data-ttu-id="b3f38-118">Weitere Informationen finden Sie unter [Verwenden von DirectXMath mit Direct3D](https://msdn.microsoft.com/library/windows/desktop/ff729728#Use_DXMath_with_D3D).</span><span class="sxs-lookup"><span data-stu-id="b3f38-118">For more info, see [Using DirectXMath with Direct3D](https://msdn.microsoft.com/library/windows/desktop/ff729728#Use_DXMath_with_D3D).</span></span>

 

<span data-ttu-id="b3f38-119">Folgende Inhalte werden behandelt:</span><span class="sxs-lookup"><span data-stu-id="b3f38-119">We show you how to:</span></span>

-   <span data-ttu-id="b3f38-120">Initialisieren von [Direct3D](https://msdn.microsoft.com/library/windows/desktop/hh309466)-Schnittstellen mit der Windows-Runtime</span><span class="sxs-lookup"><span data-stu-id="b3f38-120">Initialize [Direct3D](https://msdn.microsoft.com/library/windows/desktop/hh309466) interfaces by using the Windows Runtime</span></span>
-   <span data-ttu-id="b3f38-121">Anwenden von Vertex-Shader-Operationen</span><span class="sxs-lookup"><span data-stu-id="b3f38-121">Apply per-vertex shader operations</span></span>
-   <span data-ttu-id="b3f38-122">Einrichten der Geometrie</span><span class="sxs-lookup"><span data-stu-id="b3f38-122">Set up the geometry</span></span>
-   <span data-ttu-id="b3f38-123">Rastern der Szene (Glätten der 3D-Szene auf eine 2D-Projektion)</span><span class="sxs-lookup"><span data-stu-id="b3f38-123">Rasterize the scene (flattening the 3D scene to a 2D projection)</span></span>
-   <span data-ttu-id="b3f38-124">Culling verborgener Oberflächen</span><span class="sxs-lookup"><span data-stu-id="b3f38-124">Cull the hidden surfaces</span></span>

> **<span data-ttu-id="b3f38-125">Hinweis</span><span class="sxs-lookup"><span data-stu-id="b3f38-125">Note</span></span>**  

 

<span data-ttu-id="b3f38-126">Als Nächstes erstellen wir ein Direct3D-Gerät, eine Swapchain sowie eine Renderingzielansicht und stellen das gerenderte Bild auf dem Display dar.</span><span class="sxs-lookup"><span data-stu-id="b3f38-126">Next, we create a Direct3D device, swap chain, and render-target view, and present the rendered image to the display.</span></span>

[<span data-ttu-id="b3f38-127">Schnellstart: Einrichten von DirectX-Ressourcen und Anzeigen eines Bilds</span><span class="sxs-lookup"><span data-stu-id="b3f38-127">Quickstart: setting up DirectX resources and displaying an image</span></span>](setting-up-directx-resources.md)

## <a name="related-topics"></a><span data-ttu-id="b3f38-128">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="b3f38-128">Related topics</span></span>


* [<span data-ttu-id="b3f38-129">Direct3D 11-Grafik</span><span class="sxs-lookup"><span data-stu-id="b3f38-129">Direct3D 11 Graphics</span></span>](https://msdn.microsoft.com/library/windows/desktop/ff476080)
* [<span data-ttu-id="b3f38-130">DXGI</span><span class="sxs-lookup"><span data-stu-id="b3f38-130">DXGI</span></span>](https://msdn.microsoft.com/library/windows/desktop/hh404534)
* [<span data-ttu-id="b3f38-131">HLSL</span><span class="sxs-lookup"><span data-stu-id="b3f38-131">HLSL</span></span>](https://msdn.microsoft.com/library/windows/desktop/bb509561)

 

 




