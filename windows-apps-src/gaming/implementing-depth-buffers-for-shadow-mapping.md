---
author: mtoepke
title: Exemplarische Vorgehensweise -- Tiefenpuffer für Schattenvolumen in Direct3D11
description: In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie Schattenvolumen mit Tiefenkarten unter Verwendung von Direct3D 11 auf Geräten aller Direct3D-Funktionsebenen rendern.
ms.assetid: d15e6501-1a1d-d99c-d1d8-ad79b849db90
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, DirectX, Schattenvolumen, Tiefenpuffer, DirectX 11
ms.localizationpriority: medium
ms.openlocfilehash: 269f8423795d7c2515ce555cf8e65f14a8c63431
ms.sourcegitcommit: e38b334edb82bf2b1474ba686990f4299b8f59c7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/14/2018
ms.locfileid: "6834690"
---
# <a name="walkthrough-implement-shadow-volumes-using-depth-buffers-in-direct3d-11"></a><span data-ttu-id="ac018-104">Exemplarische Vorgehensweise - Implementieren von Schattenvolumen mithilfe von Tiefenpuffern in Direct3D 11</span><span class="sxs-lookup"><span data-stu-id="ac018-104">Walkthrough: Implement shadow volumes using depth buffers in Direct3D 11</span></span>



<span data-ttu-id="ac018-105">In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie Schattenvolumen mit Tiefenkarten unter Verwendung von Direct3D 11 auf Geräten aller Direct3D-Funktionsebenen rendern.</span><span class="sxs-lookup"><span data-stu-id="ac018-105">This walkthrough demonstrates how to render shadow volumes using depth maps, using Direct3D 11 on devices of all Direct3D feature levels.</span></span>
## 
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="ac018-106">Thema</span><span class="sxs-lookup"><span data-stu-id="ac018-106">Topic</span></span></th>
<th align="left"><span data-ttu-id="ac018-107">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ac018-107">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="create-depth-buffer-resource--view--and-sampler-state.md"><span data-ttu-id="ac018-108">Erstellen von Tiefenpuffer-Geräteressourcen</span><span class="sxs-lookup"><span data-stu-id="ac018-108">Create depth buffer device resources</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="ac018-109">Hier erfahren Sie, wie Sie die zum Unterstützen von Tiefentests für Schattenvolumen erforderlichen Direct3D-Geräteressourcen erstellen.</span><span class="sxs-lookup"><span data-stu-id="ac018-109">Learn how to create the Direct3D device resources necessary to support depth testing for shadow volumes.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="render-the-shadow-map-to-the-depth-buffer.md"><span data-ttu-id="ac018-110">Rendern der Schattenmap zum Tiefenpuffer</span><span class="sxs-lookup"><span data-stu-id="ac018-110">Render the shadow map to the depth buffer</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="ac018-111">Führen Sie das Rendern aus dem Blickwinkel durch, aus dem das Licht kommt, um eine zweidimensionale Tiefenkarte zu erstellen, mit der das Schattenvolumen dargestellt wird.</span><span class="sxs-lookup"><span data-stu-id="ac018-111">Render from the point of view of the light to create a two-dimensional depth map representing the shadow volume.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="render-the-scene-with-depth-testing.md"><span data-ttu-id="ac018-112">Rendern der Szene mit Tiefentest</span><span class="sxs-lookup"><span data-stu-id="ac018-112">Render the scene with depth testing</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="ac018-113">Erstellen Sie einen Schatteneffekt, indem Sie dem Vertex-Shader (bzw. Geometry-Shader) und dem Pixel-Shader einen Tiefentest hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="ac018-113">Create a shadow effect by adding depth testing to your vertex (or geometry) shader and your pixel shader.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="target-a-range-of-hardware.md"><span data-ttu-id="ac018-114">Unterstützen von Schattenmaps für unterschiedliche Hardware</span><span class="sxs-lookup"><span data-stu-id="ac018-114">Support shadow maps on a range of hardware</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="ac018-115">Rendern Sie Schatten in noch besserer Qualität auf schnelleren Geräten und schnellere Schatten auf weniger leistungsfähigen Geräten.</span><span class="sxs-lookup"><span data-stu-id="ac018-115">Render higher-fidelity shadows on faster devices and faster shadows on less powerful devices.</span></span></p></td>
</tr>
</tbody>
</table>

 

## <a name="shadow-mapping-application-to-direct3d-9-desktop-porting"></a><span data-ttu-id="ac018-116">Schattenabbildung – Portieren von Direct3D9-Desktop-Apps</span><span class="sxs-lookup"><span data-stu-id="ac018-116">Shadow mapping application to Direct3D 9 desktop porting</span></span>


<span data-ttu-id="ac018-117">Windows8 den tiefenvergleich hinzugefügt Funktionen auf Featureebene 9\_1 und 9\_3.</span><span class="sxs-lookup"><span data-stu-id="ac018-117">Windows8 adde d depth comparison functionality to feature level 9\_1 and 9\_3.</span></span> <span data-ttu-id="ac018-118">Jetzt können Sie Renderingcode mit Schattenvolumen zu DirectX11 migrieren. Der Direct3D11-Renderer ist abwärtskompatibel mit Geräten der Featureebene9.</span><span class="sxs-lookup"><span data-stu-id="ac018-118">Now you can migrate rendering code with shadow volumes to DirectX 11, and the Direct3D 11 renderer will be downlevel compatible with feature level 9 devices.</span></span> <span data-ttu-id="ac018-119">In dieser exemplarischen Vorgehensweise zeigen wir, wie herkömmliche Schattenvolumen mit Tiefentests in Direct3D11-Apps oder -Spielen implementiert werden können.</span><span class="sxs-lookup"><span data-stu-id="ac018-119">This walkthrough shows how any Direct3D 11 app or game can implement traditional shadow volumes using depth testing.</span></span> <span data-ttu-id="ac018-120">Der Code umfasst die folgenden Prozesse:</span><span class="sxs-lookup"><span data-stu-id="ac018-120">The code covers the following process:</span></span>

1.  <span data-ttu-id="ac018-121">Erstellen von Direct3D-Geräteressourcen für die Schattenabbildung</span><span class="sxs-lookup"><span data-stu-id="ac018-121">Creating Direct3D device resources for shadow mapping.</span></span>
2.  <span data-ttu-id="ac018-122">Hinzufügen eines Renderingdurchgangs zum Erstellen der Tiefenkarte</span><span class="sxs-lookup"><span data-stu-id="ac018-122">Adding a rendering pass to create the depth map.</span></span>
3.  <span data-ttu-id="ac018-123">Hinzufügen von Tiefentests zum Hauptrenderingdurchgang</span><span class="sxs-lookup"><span data-stu-id="ac018-123">Adding depth testing to the main rendering pass.</span></span>
4.  <span data-ttu-id="ac018-124">Implementieren des erforderlichen Shadercodes</span><span class="sxs-lookup"><span data-stu-id="ac018-124">Implementing the necessary shader code.</span></span>
5.  <span data-ttu-id="ac018-125">Optionen für schnelles Rendering auf kompatibler Hardware</span><span class="sxs-lookup"><span data-stu-id="ac018-125">Options for fast rendering on downlevel hardware.</span></span>

<span data-ttu-id="ac018-126">Nach Abschluss dieser exemplarischen Vorgehensweise wissen Sie, wie Sie eine einfache kompatible Schattenvolumentechnik in Direct3D11 implementieren, die mit Funktionsebene9\_1 und höher kompatibel ist.</span><span class="sxs-lookup"><span data-stu-id="ac018-126">Upon completing this walkthrough, you should be familiar with how to implement a basic compatible shadow volume technique in Direct3D 11 that's compatible with feature level 9\_1 and above.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ac018-127">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="ac018-127">Prerequisites</span></span>


<span data-ttu-id="ac018-128">Führen Sie die Schritte unter [Vorbereiten der Entwicklungsumgebung für die Entwicklung von Spielen für die universelle Windows-Plattform (UWP) und DirectX](prepare-your-dev-environment-for-windows-store-directx-game-development.md) aus.</span><span class="sxs-lookup"><span data-stu-id="ac018-128">You should [Prepare your dev environment for Universal Windows Platform (UWP) DirectX game development](prepare-your-dev-environment-for-windows-store-directx-game-development.md).</span></span> <span data-ttu-id="ac018-129">Sie benötigen keine Vorlage noch nicht, aber Sie benötigen Microsoft Visual Studio2015 Codebeispiel für diese exemplarische Vorgehensweise zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="ac018-129">You don't need a template yet, but you'll need Microsoft Visual Studio2015 to build the code sample for this walkthrough.</span></span>

## <a name="related-topics"></a><span data-ttu-id="ac018-130">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="ac018-130">Related topics</span></span>


**<span data-ttu-id="ac018-131">Direct3D</span><span class="sxs-lookup"><span data-stu-id="ac018-131">Direct3D</span></span>**

* [<span data-ttu-id="ac018-132">Schreiben von HLSL-Shadern in Direct3D9</span><span class="sxs-lookup"><span data-stu-id="ac018-132">Writing HLSL Shaders in Direct3D 9</span></span>](https://msdn.microsoft.com/library/windows/desktop/bb944006)
* [<span data-ttu-id="ac018-133">Erstellen eines neuen DirectX11-Projekts für die UWP</span><span class="sxs-lookup"><span data-stu-id="ac018-133">Create a new DirectX 11 project for UWP</span></span>](user-interface.md)

**<span data-ttu-id="ac018-134">Technische Artikel zur Schattenabbildung</span><span class="sxs-lookup"><span data-stu-id="ac018-134">Shadow mapping technical articles</span></span>**

* [<span data-ttu-id="ac018-135">Allgemeine Artikel zum Verbessern von Tiefenkarten für Schatten</span><span class="sxs-lookup"><span data-stu-id="ac018-135">Common Techniques to Improve Shadow Depth Maps</span></span>](https://msdn.microsoft.com/library/windows/desktop/ee416324)
* [<span data-ttu-id="ac018-136">Überlappende Schattenkarten</span><span class="sxs-lookup"><span data-stu-id="ac018-136">Cascaded Shadow Maps</span></span>](https://msdn.microsoft.com/library/windows/desktop/ee416307)

 

 




