---
title: Optimierung und fortgeschrittene Themen für DirectX-Spiele
description: Optimierung und fortgeschrittene Themen für die Programmierung von DirectX-Spielen.
ms.assetid: b5f29fb2-3bcf-43b2-9a68-f8819473bf62
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiel, DirectX, optimieren, Multisampling, Swapchains
ms.localizationpriority: medium
ms.openlocfilehash: e9618a35ecd8f9d1a37b627494c0f00a5ed84806
ms.sourcegitcommit: c01c29cd97f1cbf050950526e18e15823b6a12a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8709637"
---
# <a name="optimization-and-advanced-topics-for-directx-games"></a><span data-ttu-id="3edda-104">Optimierung und fortgeschrittene Themen für DirectX-Spiele</span><span class="sxs-lookup"><span data-stu-id="3edda-104">Optimization and advanced topics for DirectX games</span></span>

<span data-ttu-id="3edda-105">Dieser Abschnitt enthält Informationen zum Optimieren der Leistung Ihrer DirectX-Spiele sowie andere fortgeschrittene Themen.</span><span class="sxs-lookup"><span data-stu-id="3edda-105">This section provides information about optimizing your DirectX game performance and other advanced topics.</span></span>

<span data-ttu-id="3edda-106">Im Thema „Asynchrone Programmierung für Spiele” werden die verschiedene Aspekte erläutert, die zu berücksichtigen sind, wenn Sie mithilfe der asynchronen Programmierung einige der Komponenten parallelisieren und Multithreading verwenden möchten, um die Nutzung einer leistungsfähigen GPU zu maximieren.</span><span class="sxs-lookup"><span data-stu-id="3edda-106">Asynchronous programming for games topic discusses the various points to consider when you want to use asynchronous programming to parallelize some of the components and use multithreading to maximise the use of a powerful GPU.</span></span>

<span data-ttu-id="3edda-107">Im Thema „Behandeln von Szenarien mit entfernten Geräten in Direct3D11” wird eine exemplarische Vorgehensweise verwendet, um zu erläutern, wie mit Direct3D11 entwickelte Spiele Situationen, in denen die Grafikkarte zurückgesetzt, entfernt oder geändert wird, erkennen und darauf reagieren können.</span><span class="sxs-lookup"><span data-stu-id="3edda-107">Handle device removed scenarios in Direct3D 11 topic uses a walkthrough to explain how games developed using Direct3D 11 can detect and respond to situations where the graphics adapter is reset, removed, or changed.</span></span>

<span data-ttu-id="3edda-108">Das Thema „Multisampling in UWP-Apps” enthält eine Übersicht über die Verwendung von Multisampling Antialiasing. Hierbei handelt es sich um eine Grafiktechnik zum Reduzieren von treppenförmigen Kanten in mit Direct3D erstellten UWP-Spielen.</span><span class="sxs-lookup"><span data-stu-id="3edda-108">Multisampling in UWP apps topic provides an overview of how to use multi-sample antialiasing, a graphics technique to reduce the appearance of aliased edges in UWP games built with Direct3D.</span></span>

<span data-ttu-id="3edda-109">Das Thema „Optimieren von Eingabe und Renderschleife” enthält Anleitungen zum Auswählen der richtigen Verarbeitungsoptionen für Eingabeereignisse zum Verwalten der Eingabelatenz und Optimieren der Renderschleife.</span><span class="sxs-lookup"><span data-stu-id="3edda-109">Optimize input and rendering loop topic provides guidance on how to choose the right input event processing option to manage input latency and optimize the rendering loop.</span></span>

<span data-ttu-id="3edda-110">Im Thema „Reduzieren der Latenz mit DXGI 1.3-Swapchains” wird erläutert, wie Sie die geltende Framelatenz reduzieren, indem Sie warten, bis die Swapchain den geeigneten Zeitpunkt zum Rendern eines neuen Frames meldet.</span><span class="sxs-lookup"><span data-stu-id="3edda-110">Reduce latency with DXGI 1.3 swap chains topic explains how to reduce effective frame latency by waiting for the swap chain to signal the appropriate time to begin rendering a new frame.</span></span>

<span data-ttu-id="3edda-111">Im Thema „Swapchainskalierung und Überlagerungen” wird erläutert, wie Renderingzeiten verbessert werden können, indem Sie skalierte Swapchains verwenden, um Echtzeitinhalte von Spielen mit einer niedrigeren Auflösung als der Auflösung zu rendern, die das Display standardmäßig leisten kann.</span><span class="sxs-lookup"><span data-stu-id="3edda-111">Swap chain scaling and overlays topic explains how to improve rendering times by using scaled swap chains to render real-time game content at a lower resolution than the display is natively capable of.</span></span> <span data-ttu-id="3edda-112">Darüber hinaus wird erläutert, wie Überlagerungsswapchains für Geräte mit Hardwareüberlagerungsfunktion erstellt werden. Mit dieser Technik lässt sich das Problem einer herunterskalierten Benutzeroberfläche verringern, welches im Zusammenhang mit Swapchainskalierung auftritt.</span><span class="sxs-lookup"><span data-stu-id="3edda-112">It also explains how to create overlay swap chains for devices with the hardware overlay capability; this technique can be used to alleviate the issue of a scaled down UI resulting from the use of swap chain scaling.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="3edda-113">Thema</span><span class="sxs-lookup"><span data-stu-id="3edda-113">Topic</span></span></th>
<th align="left"><span data-ttu-id="3edda-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3edda-114">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="asynchronous-programming-directx-and-cpp.md"><span data-ttu-id="3edda-115">Asynchrone Programmierung für Spiele</span><span class="sxs-lookup"><span data-stu-id="3edda-115">Asynchronous programming for games</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="3edda-116">Machen Sie sich mit der asynchronen Programmierung und dem Threading mit DirectX vertraut.</span><span class="sxs-lookup"><span data-stu-id="3edda-116">Understand asynchronous programming and threading with DirectX.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="handling-device-lost-scenarios.md"><span data-ttu-id="3edda-117">Behandeln von Szenarien mit entfernten Geräten in Direct3D11</span><span class="sxs-lookup"><span data-stu-id="3edda-117">Handle device removed scenarios in Direct3D 11</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="3edda-118">Erstellen Sie die Geräteschnittstellenkette für Direct3D und DXGI neu, wenn die Grafikkarte entfernt oder neu initialisiert wird.</span><span class="sxs-lookup"><span data-stu-id="3edda-118">Recreate the Direct3D and DXGI device interface chain when the graphics adapter is removed or reinitialized.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="multisampling--multi-sample-anti-aliasing--in-windows-store-apps.md"><span data-ttu-id="3edda-119">Multisampling in UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="3edda-119">Multisampling in UWP apps</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="3edda-120">Verwenden Sie Multisampling in UWP-Spielen, die mit Direct3D erstellt wurden.</span><span class="sxs-lookup"><span data-stu-id="3edda-120">Use multisampling in UWP games built using Direct3D.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="optimize-performance-for-windows-store-direct3d-11-apps-with-coredispatcher.md"><span data-ttu-id="3edda-121">Optimieren von Eingabe und Renderschleife</span><span class="sxs-lookup"><span data-stu-id="3edda-121">Optimize input and rendering loop</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="3edda-122">Reduzieren Sie die Eingabelatenz und optimieren Sie die Renderschleife.</span><span class="sxs-lookup"><span data-stu-id="3edda-122">Reduce input latency and optimize the rendering loop.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="reduce-latency-with-dxgi-1-3-swap-chains.md"><span data-ttu-id="3edda-123">Reduzieren der Latenz mit DXGI 1.3-Swapchains</span><span class="sxs-lookup"><span data-stu-id="3edda-123">Reduce latency with DXGI 1.3 swap chains</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="3edda-124">Verwenden Sie DXGI 1.3, um die geltende Framelatenz zu reduzieren.</span><span class="sxs-lookup"><span data-stu-id="3edda-124">Use DXGI 1.3 to reduce the effective frame latency.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="multisampling--scaling--and-overlay-swap-chains.md"><span data-ttu-id="3edda-125">Swapchainskalierung und Überlagerungen</span><span class="sxs-lookup"><span data-stu-id="3edda-125">Swap chain scaling and overlays</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="3edda-126">Erstellen Sie skalierte Swapchains zum schnelleren Rendern auf mobilen Geräten, und verwenden Sie Überlagerungsswapchains, um die visuelle Qualität zu steigern.</span><span class="sxs-lookup"><span data-stu-id="3edda-126">Create scaled swap chains for faster rendering on mobile devices, and use overlay swap chains to increase the visual quality.</span></span></p></td>
</tr>
</tbody>
</table>