---
author: mtoepke
title: Tools für die Grafikdiagnose
description: Hier erfahren Sie, wie Sie in Visual Studio die Grafikdiagnosefeatures, einschließlich Grafikdebugging, Analyse von Grafikframes und GPU-Verwendung, abrufen und verwenden.
ms.assetid: 629ea462-18ed-a333-07e9-cc87ea2dcd93
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, Grafiken, Diagnose, Tools, directx
ms.localizationpriority: medium
ms.openlocfilehash: aa1c14d15a966f23b86753cf8e5e62e067d10310
ms.sourcegitcommit: 6cc275f2151f78db40c11ace381ee2d35f0155f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "5545227"
---
# <a name="graphics-diagnostics-tools"></a><span data-ttu-id="a9982-104">Tools für die Grafikdiagnose</span><span class="sxs-lookup"><span data-stu-id="a9982-104">Graphics diagnostics tools</span></span>



<span data-ttu-id="a9982-105">Mit Windows 10 sind die Grafiken Diagnosetools jetzt als optionales Feature in Windows zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="a9982-105">With Windows10, the graphics diagnostic tools are now available from within Windows as an optional feature.</span></span> <span data-ttu-id="a9982-106">Installieren Sie das optionale Grafiktoolfeature, um die in der Runtime und in VisualStudio bereitgestellten Grafikdiagnosefeatures für die Entwicklung von DirectX-Apps oder -Spielen zu nutzen:</span><span class="sxs-lookup"><span data-stu-id="a9982-106">To use the graphics diagnostic features provided in the runtime and Visual Studio to develop DirectX apps or games, install the optional Graphics Tools feature:</span></span>

1.  <span data-ttu-id="a9982-107">Wechseln Sie zu **Einstellungen**, wählen Sie **Apps aus**, und klicken Sie dann auf **optionale Features verwalten**.</span><span class="sxs-lookup"><span data-stu-id="a9982-107">Go to **Settings**, select **Apps**, and then click **Manage optional features**.</span></span>
2.  <span data-ttu-id="a9982-108">Klicken Sie auf **Feature hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="a9982-108">Click **Add a feature**</span></span>   
3.  <span data-ttu-id="a9982-109">Wählen Sie in der Liste **Optionale Features** **Grafiktools** aus, und klicken Sie dann auf **Installieren**.</span><span class="sxs-lookup"><span data-stu-id="a9982-109">In the **Optional features** list, select **Graphics Tools** and then click **Install**.</span></span>

<span data-ttu-id="a9982-110">Die Grafikdiagnosefeatures ermöglichen das Erstellen von Direct3D-Debugging-Geräten (über Direct3D-SDK-Ebenen) in der DirectX-Runtime sowie das Grafikdebugging, die Frame-Analyse und die GPU-Verwendung.</span><span class="sxs-lookup"><span data-stu-id="a9982-110">Graphics diagnostics features include the ability to create Direct3D debug devices (via Direct3D SDK Layers) in the DirectX runtime, plus Graphics Debugging, Frame Analysis, and GPU Usage.</span></span>

-   <span data-ttu-id="a9982-111">Mit dem Grafikdebugging können Sie Direct3D-Aufrufe Ihrer App nachverfolgen.</span><span class="sxs-lookup"><span data-stu-id="a9982-111">Graphics Debugging lets you trace the Direct3D calls being made by your app.</span></span> <span data-ttu-id="a9982-112">Anschließend können Sie diese Aufrufe wiedergeben, Parameter untersuchen, Shader debuggen und mit ihnen experimentieren sowie Grafikobjekte visualisieren, um Renderingprobleme zu diagnostizieren.</span><span class="sxs-lookup"><span data-stu-id="a9982-112">Then, you can replay those calls, inspect parameters, debug and experiment with shaders, and visualize graphics assets to diagnose rendering issues.</span></span> <span data-ttu-id="a9982-113">Protokolle können auf Windows-PCs, in Simulatoren oder auf Geräten erstellt und auf anderer Hardware wiedergegeben werden.</span><span class="sxs-lookup"><span data-stu-id="a9982-113">Logs can be taken on Windows PCs, simulators, or devices, and be played back on different hardware.</span></span>
-   <span data-ttu-id="a9982-114">Die Analyse von Grafikframes in VisualStudio wird für ein Grafikdebuggingprotokoll ausgeführt und erfasst Details der Grundlinienzeitsteuerung für die Direct3D-Draw-Aufrufe.</span><span class="sxs-lookup"><span data-stu-id="a9982-114">Graphics Frame Analysis in Visual Studio runs on a graphics debugging log and gathers baseline timing for the Direct3D draw calls.</span></span> <span data-ttu-id="a9982-115">Anschließend führt sie eine Reihe von Versuchen aus, indem sie verschiedene Grafikeinstellungen ändert, und generiert eine Tabelle der Zeitsteuerungsergebnisse.</span><span class="sxs-lookup"><span data-stu-id="a9982-115">It then performs a set of experiments by modifying various graphics settings and produces a table of timing results.</span></span> <span data-ttu-id="a9982-116">Diese Daten können Aufschluss über Probleme mit der Grafikleistung Ihrer App geben, und anhand der Ergebnisse der verschiedenen Versuche können Sie feststellen, wie sich die Leistung verbessern lässt.</span><span class="sxs-lookup"><span data-stu-id="a9982-116">You can use this data to understand graphics performance issues in your app, and you can review results of the various experiments to identify opportunities for performance improvements.</span></span>
-   <span data-ttu-id="a9982-117">Anhand der GPU-Verwendung in VisualStudio können Sie die GPU-Verwendung in Echtzeit überwachen.</span><span class="sxs-lookup"><span data-stu-id="a9982-117">GPU Usage in Visual Studio allows you to monitor GPU use in real time.</span></span> <span data-ttu-id="a9982-118">Sie erfasst und analysiert die Zeitdaten der Arbeitsauslastungen, die von der CPU und GPU verarbeitet werden, und ermöglicht so die Erkennung von Engpässen.</span><span class="sxs-lookup"><span data-stu-id="a9982-118">It collects and analyzes the timing data of the workloads being handled by the CPU and GPU, so you can determine where the bottlenecks are.</span></span>

## <a name="related-topics"></a><span data-ttu-id="a9982-119">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="a9982-119">Related topics</span></span>


[<span data-ttu-id="a9982-120">Übersicht über die Grafikdiagnose in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a9982-120">Graphics Diagnostics Overview in Visual Studio</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=526382)

 

 




