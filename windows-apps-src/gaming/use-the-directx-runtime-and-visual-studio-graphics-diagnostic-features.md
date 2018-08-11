---
author: mtoepke
title: Tools für die Grafikdiagnose
description: Hier erfahren Sie, wie Sie in Visual Studio die Grafikdiagnosefeatures, einschließlich Grafikdebugging, Analyse von Grafikframes und GPU-Verwendung, abrufen und verwenden.
ms.assetid: 629ea462-18ed-a333-07e9-cc87ea2dcd93
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Spiele, Grafiken, Diagnose, Tools, directx
ms.openlocfilehash: 076020d88889a9cc8b417befa2dd54b41d688e5e
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
ms.translationtype: MT
ms.contentlocale: de-DE
ms.locfileid: "233733"
---
# <a name="graphics-diagnostics-tools"></a><span data-ttu-id="89d93-104">Tools für die Grafikdiagnose</span><span class="sxs-lookup"><span data-stu-id="89d93-104">Graphics diagnostics tools</span></span>


<span data-ttu-id="89d93-105">\[ Aktualisiert für UWP-Apps unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="89d93-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="89d93-106">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132). \]</span><span class="sxs-lookup"><span data-stu-id="89d93-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>

<span data-ttu-id="89d93-107">Unter Windows10 stehen die Grafikdiagnosetools jetzt als optionales Feature in Windows zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="89d93-107">With Windows 10, the graphics diagnostic tools are now available from within Windows as an optional feature.</span></span> <span data-ttu-id="89d93-108">Installieren Sie das optionale Grafiktoolfeature, um die in der Runtime und in VisualStudio bereitgestellten Grafikdiagnosefeatures für die Entwicklung von DirectX-Apps oder -Spielen zu nutzen:</span><span class="sxs-lookup"><span data-stu-id="89d93-108">To use the graphics diagnostic features provided in the runtime and Visual Studio to develop DirectX apps or games, install the optional Graphics Tools feature:</span></span>

1.  <span data-ttu-id="89d93-109">Klicken Sie unter **Einstellungen**> **System**> **Apps und Features** auf **Optionale Features verwalten**.</span><span class="sxs-lookup"><span data-stu-id="89d93-109">Go to **Settings**, select **System**, select **Apps & Features**, and then click **Manage optional features**.</span></span>
2.  <span data-ttu-id="89d93-110">Klicken Sie auf **Feature hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="89d93-110">Click **Add a feature**</span></span>   
3.  <span data-ttu-id="89d93-111">Wählen Sie in der Liste **Optionale Features** **Grafiktools** aus, und klicken Sie dann auf **Installieren**.</span><span class="sxs-lookup"><span data-stu-id="89d93-111">In the **Optional features** list, select **Graphics Tools** and then click **Install**.</span></span>

<span data-ttu-id="89d93-112">Die Grafikdiagnosefeatures ermöglichen das Erstellen von Direct3D-Debugging-Geräten (über Direct3D-SDK-Ebenen) in der DirectX-Runtime sowie das Grafikdebugging, die Frame-Analyse und die GPU-Verwendung.</span><span class="sxs-lookup"><span data-stu-id="89d93-112">Graphics diagnostics features include the ability to create Direct3D debug devices (via Direct3D SDK Layers) in the DirectX runtime, plus Graphics Debugging, Frame Analysis, and GPU Usage.</span></span>

-   <span data-ttu-id="89d93-113">Mit dem Grafikdebugging können Sie Direct3D-Aufrufe Ihrer App nachverfolgen.</span><span class="sxs-lookup"><span data-stu-id="89d93-113">Graphics Debugging lets you trace the Direct3D calls being made by your app.</span></span> <span data-ttu-id="89d93-114">Anschließend können Sie diese Aufrufe wiedergeben, Parameter untersuchen, Shader debuggen und mit ihnen experimentieren sowie Grafikobjekte visualisieren, um Renderingprobleme zu diagnostizieren.</span><span class="sxs-lookup"><span data-stu-id="89d93-114">Then, you can replay those calls, inspect parameters, debug and experiment with shaders, and visualize graphics assets to diagnose rendering issues.</span></span> <span data-ttu-id="89d93-115">Protokolle können auf Windows-PCs, in Simulatoren oder auf Geräten erstellt und auf anderer Hardware wiedergegeben werden.</span><span class="sxs-lookup"><span data-stu-id="89d93-115">Logs can be taken on Windows PCs, simulators, or devices, and be played back on different hardware.</span></span>
-   <span data-ttu-id="89d93-116">Die Analyse von Grafikframes in VisualStudio wird für ein Grafikdebuggingprotokoll ausgeführt und erfasst Details der Grundlinienzeitsteuerung für die Direct3D-Draw-Aufrufe.</span><span class="sxs-lookup"><span data-stu-id="89d93-116">Graphics Frame Analysis in Visual Studio runs on a graphics debugging log and gathers baseline timing for the Direct3D draw calls.</span></span> <span data-ttu-id="89d93-117">Anschließend führt sie eine Reihe von Versuchen aus, indem sie verschiedene Grafikeinstellungen ändert, und generiert eine Tabelle der Zeitsteuerungsergebnisse.</span><span class="sxs-lookup"><span data-stu-id="89d93-117">It then performs a set of experiments by modifying various graphics settings and produces a table of timing results.</span></span> <span data-ttu-id="89d93-118">Diese Daten können Aufschluss über Probleme mit der Grafikleistung Ihrer App geben, und anhand der Ergebnisse der verschiedenen Versuche können Sie feststellen, wie sich die Leistung verbessern lässt.</span><span class="sxs-lookup"><span data-stu-id="89d93-118">You can use this data to understand graphics performance issues in your app, and you can review results of the various experiments to identify opportunities for performance improvements.</span></span>
-   <span data-ttu-id="89d93-119">Anhand der GPU-Verwendung in VisualStudio können Sie die GPU-Verwendung in Echtzeit überwachen.</span><span class="sxs-lookup"><span data-stu-id="89d93-119">GPU Usage in Visual Studio allows you to monitor GPU use in real time.</span></span> <span data-ttu-id="89d93-120">Sie erfasst und analysiert die Zeitdaten der Arbeitsauslastungen, die von der CPU und GPU verarbeitet werden, und ermöglicht so die Erkennung von Engpässen.</span><span class="sxs-lookup"><span data-stu-id="89d93-120">It collects and analyzes the timing data of the workloads being handled by the CPU and GPU, so you can determine where the bottlenecks are.</span></span>

## <a name="related-topics"></a><span data-ttu-id="89d93-121">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="89d93-121">Related topics</span></span>


[<span data-ttu-id="89d93-122">Übersicht über die Grafikdiagnose in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="89d93-122">Graphics Diagnostics Overview in Visual Studio</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=526382)

 

 




