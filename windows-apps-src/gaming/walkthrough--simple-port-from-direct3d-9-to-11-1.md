---
title: Exemplarische Vorgehensweise -- Portieren von Direct3D9 zu DirectX11 und UWP
description: In dieser Portierungsübung wird veranschaulicht, wie Sie ein einfaches Renderingframework von Direct3D9 auf Direct3D11 und die universelle Windows-Plattform (UWP) umstellen.
ms.assetid: d4467e1f-929b-a4b8-b233-e142a8714c96
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, Directx, Port, direct3d 9, direct3d 11
ms.localizationpriority: medium
ms.openlocfilehash: c7569c6b2f041f5535e0eabe934a91da86b60b9a
ms.sourcegitcommit: a3dc929858415b933943bba5aa7487ffa721899f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "8808615"
---
# <a name="walkthrough-port-a-simple-direct3d-9-app-to-directx-11-and-universal-windows-platform-uwp"></a><span data-ttu-id="f1e64-104">Exemplarische Vorgehensweise Portieren einer einfachen Direct3D 9-App zu DirectX 11 und zur universellen Windows-Plattform (UWP)</span><span class="sxs-lookup"><span data-stu-id="f1e64-104">Walkthrough: Port a simple Direct3D 9 app to DirectX 11 and Universal Windows Platform (UWP)</span></span>



<span data-ttu-id="f1e64-105">In dieser Portierungsübung wird veranschaulicht, wie Sie ein einfaches Renderingframework von Direct3D9 auf Direct3D11 und die universelle Windows-Plattform (UWP) umstellen.</span><span class="sxs-lookup"><span data-stu-id="f1e64-105">This porting exercise shows how to bring a simple rendering framework from Direct3D 9 to Direct3D 11 and Universal Windows Platform (UWP).</span></span>
## 
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="f1e64-106">Thema</span><span class="sxs-lookup"><span data-stu-id="f1e64-106">Topic</span></span></th>
<th align="left"><span data-ttu-id="f1e64-107">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f1e64-107">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="simple-port-from-direct3d-9-to-11-1-part-1--initializing-direct3d.md"><span data-ttu-id="f1e64-108">Initialisieren von Direct3D11</span><span class="sxs-lookup"><span data-stu-id="f1e64-108">Initialize Direct3D 11</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="f1e64-109">Hier wird veranschaulicht, wie Sie Direct3D 9-Initialisierungscode in Direct3D 11 konvertieren, und Sie erfahren, wie Sie Handles zum Direct3D-Gerät und zum Gerätekontext abrufen und DXGI zum Einrichten einer Swapchain verwenden.</span><span class="sxs-lookup"><span data-stu-id="f1e64-109">Shows how to convert Direct3D 9 initialization code to Direct3D 11, including how to get handles to the Direct3D device and the device context and how to use DXGI to set up a swap chain.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="simple-port-from-direct3d-9-to-11-1-part-2--rendering.md"><span data-ttu-id="f1e64-110">Konvertieren des Renderingframeworks</span><span class="sxs-lookup"><span data-stu-id="f1e64-110">Convert the rendering framework</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="f1e64-111">Hier wird veranschaulicht, wie Sie ein einfaches Renderingframework von Direct3D9 in Direct3D11 konvertieren. Sie erfahren, wie Sie Geometriepuffer portieren, HLSL-Shaderprogramme kompilieren und laden und die Renderkette in Direct3D11 implementieren.</span><span class="sxs-lookup"><span data-stu-id="f1e64-111">Shows how to convert a simple rendering framework from Direct3D 9 to Direct3D 11, including how to port geometry buffers, how to compile and load HLSL shader programs, and how to implement the rendering chain in Direct3D 11.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="simple-port-from-direct3d-9-to-11-1-part-3--viewport-and-game-loop.md"><span data-ttu-id="f1e64-112">Portieren der Spielschleife</span><span class="sxs-lookup"><span data-stu-id="f1e64-112">Port the game loop</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="f1e64-113">In diesem Thema wird veranschaulicht, wie Sie ein Fenster für ein UWP-Spiel (Universelle Windows-Plattform) implementieren und die Spielschleife übertragen. Außerdem wird die Erstellung eines <a href="https://msdn.microsoft.com/library/windows/apps/hh700478"><strong>IFrameworkView</strong></a>-Elements zum Steuern eines <a href="https://msdn.microsoft.com/library/windows/apps/br208225"><strong>CoreWindow</strong></a>-Vollbilds erläutert.</span><span class="sxs-lookup"><span data-stu-id="f1e64-113">Shows how to implement a window for a UWP game and how to bring over the game loop, including how to build an <a href="https://msdn.microsoft.com/library/windows/apps/hh700478"><strong>IFrameworkView</strong></a> to control a full-screen <a href="https://msdn.microsoft.com/library/windows/apps/br208225"><strong>CoreWindow</strong></a>.</span></span></p></td>
</tr>
</tbody>
</table>

 

<span data-ttu-id="f1e64-114">Es werden zwei Codepfade durchgegangen, mit denen jeweils die gleiche grundlegende Grafikaufgabe durchgeführt wird: das Anzeigen eines sich drehenden Würfels mit Vertexschattierung.</span><span class="sxs-lookup"><span data-stu-id="f1e64-114">This topic walks through two code paths that perform the same basic graphics task: display a rotating vertex-shaded cube.</span></span> <span data-ttu-id="f1e64-115">In beiden Fällen wird mit dem Code der folgende Prozess abgedeckt:</span><span class="sxs-lookup"><span data-stu-id="f1e64-115">In both cases, the code covers the following process:</span></span>

1.  <span data-ttu-id="f1e64-116">Erstellen eines Direct3D-Geräts und einer Swapchain</span><span class="sxs-lookup"><span data-stu-id="f1e64-116">Creating a Direct3D device and a swap chain.</span></span>
2.  <span data-ttu-id="f1e64-117">Erstellen eines Vertexpuffers und eines Indexpuffers zum Darstellen eines farbigen Würfelgitters</span><span class="sxs-lookup"><span data-stu-id="f1e64-117">Creating a vertex buffer, and an index buffer, to represent a colorful cube mesh.</span></span>
3.  <span data-ttu-id="f1e64-118">Erstellen eines Vertexshaders, mit dem Vertizes in Bildschirmbereiche umgewandelt werden, eines Pixelshaders, mit dem Farbwerte vermischt werden, Kompilieren der Shader und Laden der Shader als Direct3D-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="f1e64-118">Creating a vertex shader that transforms vertices to screen space, a pixel shader that blends color values, compiling the shaders, and loading the shaders as Direct3D resources.</span></span>
4.  <span data-ttu-id="f1e64-119">Implementieren der Renderkette und Darstellen des gezeichneten Würfels auf dem Bildschirm</span><span class="sxs-lookup"><span data-stu-id="f1e64-119">Implementing the rendering chain and presenting the drawn cube to the screen.</span></span>
5.  <span data-ttu-id="f1e64-120">Erstellen eines Fensters, Starten einer Hauptschleife und Durchführen der Verarbeitung von Bildschirmmeldungen</span><span class="sxs-lookup"><span data-stu-id="f1e64-120">Creating a window, starting a main loop, and taking care of window message processing.</span></span>

<span data-ttu-id="f1e64-121">Nach der Durcharbeitung dieser exemplarischen Vorgehensweise sollten Ihnen die folgenden grundlegenden Unterschiede zwischen Direct3D9 und Direct3D11 bekannt sein:</span><span class="sxs-lookup"><span data-stu-id="f1e64-121">Upon completing this walkthrough, you should be familiar with the following basic differences between Direct3D 9 and Direct3D 11:</span></span>

-   <span data-ttu-id="f1e64-122">Trennung von Gerät, Gerätekontext und Grafikinfrastruktur</span><span class="sxs-lookup"><span data-stu-id="f1e64-122">The separation of device, device context, and graphics infrastructure.</span></span>
-   <span data-ttu-id="f1e64-123">Kompilierungsprozess für Shader und Laden von Shaderbytecode zur Laufzeit</span><span class="sxs-lookup"><span data-stu-id="f1e64-123">The process of compiling shaders, and loading shader bytecode at runtime.</span></span>
-   <span data-ttu-id="f1e64-124">Konfigurieren von Daten pro Vertex für den Eingabeassemblerzustand</span><span class="sxs-lookup"><span data-stu-id="f1e64-124">How to configure per-vertex data for the Input Assembler (IA) stage.</span></span>
-   <span data-ttu-id="f1e64-125">Verwenden eines [**IFrameworkView**](https://msdn.microsoft.com/library/windows/apps/hh700478)-Elements zum Erstellen einer CoreWindow-Ansicht</span><span class="sxs-lookup"><span data-stu-id="f1e64-125">How to use an [**IFrameworkView**](https://msdn.microsoft.com/library/windows/apps/hh700478) to create a CoreWindow view.</span></span>

<span data-ttu-id="f1e64-126">Beachten Sie, dass in dieser exemplarischen Vorgehensweise der Einfachheit halber [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225) verwendet wird. Die XAML-Interoperabilität wird nicht behandelt.</span><span class="sxs-lookup"><span data-stu-id="f1e64-126">Note that this walkthrough uses [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225) for simplicity, and does not cover XAML interop.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f1e64-127">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="f1e64-127">Prerequisites</span></span>


<span data-ttu-id="f1e64-128">Führen Sie die Schritte unter [Vorbereiten der Entwicklungsumgebung für die Entwicklung von UWP-DirectX-Spielen](prepare-your-dev-environment-for-windows-store-directx-game-development.md) aus.</span><span class="sxs-lookup"><span data-stu-id="f1e64-128">You should [Prepare your dev environment for UWP DirectX game development](prepare-your-dev-environment-for-windows-store-directx-game-development.md).</span></span> <span data-ttu-id="f1e64-129">Sie benötigen eine Vorlage noch, aber Sie benötigen Microsoft Visual Studio2015 die Codebeispiele für diese exemplarische Vorgehensweise zu laden.</span><span class="sxs-lookup"><span data-stu-id="f1e64-129">You don't need a template yet, but you'll need Microsoft Visual Studio2015 to load the code samples for this walkthrough.</span></span>

<span data-ttu-id="f1e64-130">Lesen Sie sich die Informationen unter [Konzepte und Aspekte der Portierung](porting-considerations.md) durch, um ein besseres Verständnis der in dieser exemplarischen Vorgehensweise verwendeten Programmierkonzepte für DirectX11 und UWP zu entwickeln.</span><span class="sxs-lookup"><span data-stu-id="f1e64-130">Visit [Porting concepts and considerations](porting-considerations.md) to gain a better understanding of the DirectX 11 and UWP programming concepts shown in this walkthrough.</span></span>

## <a name="related-topics"></a><span data-ttu-id="f1e64-131">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="f1e64-131">Related topics</span></span>

**<span data-ttu-id="f1e64-132">Direct3D</span><span class="sxs-lookup"><span data-stu-id="f1e64-132">Direct3D</span></span>**

* [<span data-ttu-id="f1e64-133">Schreiben von HLSL-Shadern in Direct3D9</span><span class="sxs-lookup"><span data-stu-id="f1e64-133">Writing HLSL Shaders in Direct3D 9</span></span>](https://msdn.microsoft.com/library/windows/desktop/bb944006)
* [<span data-ttu-id="f1e64-134">DirectX-Spielprojektvorlagen</span><span class="sxs-lookup"><span data-stu-id="f1e64-134">DirectX game project templates</span></span>](user-interface.md)

**<span data-ttu-id="f1e64-135">Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="f1e64-135">Microsoft Store</span></span>**

* [**<span data-ttu-id="f1e64-136">Microsoft::WRL::ComPtr</span><span class="sxs-lookup"><span data-stu-id="f1e64-136">Microsoft::WRL::ComPtr</span></span>**](https://msdn.microsoft.com/library/windows/apps/br244983.aspx)
* [**<span data-ttu-id="f1e64-137">Handle to Object Operator (^)</span><span class="sxs-lookup"><span data-stu-id="f1e64-137">Handle to Object Operator (^)</span></span>**](https://msdn.microsoft.com/library/windows/apps/yk97tc08.aspx)

