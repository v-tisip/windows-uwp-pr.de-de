---
author: mtoepke
title: Zuordnen von OpenGLES2.0 zu Direct3D11
description: Machen Sie sich zu Beginn des Prozesses zur ersten Portierung Ihrer Grafikarchitektur von OpenGL ES 2.0 zu Direct3D mit den Hauptunterschieden zwischen den APIs vertraut.
ms.assetid: 7f9b136c-aa22-04b3-d385-6e9e1f38b948
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, OpenGL, Direct3D, Portieren
ms.localizationpriority: medium
ms.openlocfilehash: 532c2a0a9779ae3eaedb2217175dc0805514f792
ms.sourcegitcommit: cbe7cf620622a5e4df7414f9e38dfecec1cfca99
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2018
ms.locfileid: "7434710"
---
# <a name="map-opengl-es-20-to-direct3d-11"></a><span data-ttu-id="28dbb-104">Zuordnen von OpenGLES2.0 zu Direct3D11</span><span class="sxs-lookup"><span data-stu-id="28dbb-104">Map OpenGL ES 2.0 to Direct3D 11</span></span>



<span data-ttu-id="28dbb-105">Machen Sie sich zu Beginn des Prozesses zur ersten Portierung Ihrer Grafikarchitektur von OpenGL ES 2.0 zu Direct3D mit den Hauptunterschieden zwischen den APIs vertraut.</span><span class="sxs-lookup"><span data-stu-id="28dbb-105">When starting the process of porting your graphics architecture from OpenGL ES 2.0 to Direct3D for the first time, familiarize yourself with the key differences between the APIs.</span></span> <span data-ttu-id="28dbb-106">Mithilfe der Themen in diesem Abschnitt können Sie die Portierungsstrategie und die API-Änderungen planen, die erforderlich sind, wenn Sie die Grafikverarbeitung auf Direct3D umstellen.</span><span class="sxs-lookup"><span data-stu-id="28dbb-106">The topics in this section help you plan your port strategy and the API changes that you must make when moving your graphics processing to Direct3D.</span></span>
## 
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="28dbb-107">Thema</span><span class="sxs-lookup"><span data-stu-id="28dbb-107">Topic</span></span></th>
<th align="left"><span data-ttu-id="28dbb-108">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="28dbb-108">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="compare-opengl-es-2-0-api-design-to-directx.md"><span data-ttu-id="28dbb-109">Planen der Portierung von OpenGLES2.0 zu Direct3D</span><span class="sxs-lookup"><span data-stu-id="28dbb-109">Plan your port from OpenGL ES 2.0 to Direct3D</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="28dbb-110">Wenn Sie ein Spiel von der iOS- oder Android-Plattform portieren, haben Sie vermutlich erheblich in OpenGLES2.0 investiert.</span><span class="sxs-lookup"><span data-stu-id="28dbb-110">If you are porting a game from the iOS or Android platforms, you have probably made a significant investment in OpenGL ES 2.0.</span></span> <span data-ttu-id="28dbb-111">Beim Vorbereiten der Portierung Ihrer Grafikpipeline-Codebasis zu Direct3D11 und der Windows-Runtime sind im Vorfeld einige Dinge zu beachten.</span><span class="sxs-lookup"><span data-stu-id="28dbb-111">When preparing to move your graphics pipeline codebase to Direct3D 11 and the Windows Runtime, there are a few things you should consider before you start.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="moving-from-egl-to-dxgi.md"><span data-ttu-id="28dbb-112">Vergleichen des EGL-Codes mit DXGI und Direct3D</span><span class="sxs-lookup"><span data-stu-id="28dbb-112">Compare EGL code to DXGI and Direct3D</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="28dbb-113">Die DirectX-Grafikschnittstelle (DXGI) und verschiedene Direct3D-APIs erfüllen die gleiche Rolle wie EGL.</span><span class="sxs-lookup"><span data-stu-id="28dbb-113">The DirectX Graphics Interface (DXGI) and several Direct3D APIs serve the same role as EGL.</span></span> <span data-ttu-id="28dbb-114">In diesem Thema werden die DXGI und Direct3D11 aus Sicht von EGL erläutert.</span><span class="sxs-lookup"><span data-stu-id="28dbb-114">This topic helps you understand DXGI and Direct3D 11 from the perspective of EGL.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="porting-uniforms-and-attributes.md"><span data-ttu-id="28dbb-115">Vergleichen von OpenGLES2.0-Puffern, -uniform-Elementen und -Vertexattributen mit Direct3D</span><span class="sxs-lookup"><span data-stu-id="28dbb-115">Compare OpenGL ES 2.0 buffers, uniforms, and vertex attributes to Direct3D</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="28dbb-116">Während des Portierens zu Direct3D 11 aus OpenGL ES 2.0 müssen Sie die Syntax und das API-Verhalten zum Übergeben von Daten zwischen der App und den Shaderprogrammen ändern.</span><span class="sxs-lookup"><span data-stu-id="28dbb-116">During the process of porting to Direct3D 11 from OpenGL ES 2.0, you must change the syntax and API behavior for passing data between the app and the shader programs.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="change-your-shader-loading-code.md"><span data-ttu-id="28dbb-117">Vergleich der OpenGLES2.0-Shaderpipeline mit Direct3D</span><span class="sxs-lookup"><span data-stu-id="28dbb-117">Compare the OpenGL ES 2.0 shader pipeline to Direct3D</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="28dbb-118">Vom Konzept her ist die Direct3D11-Shaderpipeline der in OpenGLES2.0 sehr ähnlich.</span><span class="sxs-lookup"><span data-stu-id="28dbb-118">Conceptually, the Direct3D 11 shader pipeline is very similar to the one in OpenGL ES 2.0.</span></span> <span data-ttu-id="28dbb-119">Hinsichtlich des API-Entwurfs sind die Hauptkomponenten für die Erstellung und Verwaltung der Shaderstufen jedoch Teile der zwei primären Schnittstellen <a href="https://msdn.microsoft.com/library/windows/desktop/hh404575"><strong>ID3D11Device1</strong></a> und <a href="https://msdn.microsoft.com/library/windows/desktop/hh404598"><strong>ID3D11DeviceContext1</strong></a>.</span><span class="sxs-lookup"><span data-stu-id="28dbb-119">In terms of API design, however, the major components for creating and managing the shader stages are parts of two primary interfaces, <a href="https://msdn.microsoft.com/library/windows/desktop/hh404575"><strong>ID3D11Device1</strong></a> and <a href="https://msdn.microsoft.com/library/windows/desktop/hh404598"><strong>ID3D11DeviceContext1</strong></a>.</span></span> <span data-ttu-id="28dbb-120">In diesem Thema versuchen wir, allgemeine Muster der OpenGLES2.0-Shaderpipeline-API den Direct3D11-Entsprechungen in diesen Schnittstellen zuzuordnen.</span><span class="sxs-lookup"><span data-stu-id="28dbb-120">This topic attempts to map common OpenGL ES 2.0 shader pipeline API patterns to the Direct3D 11 equivalents in these interfaces.</span></span></p></td>
</tr>
</tbody>
</table>

 

## <a name="notes-on-specific-opengl-es-20-providers"></a><span data-ttu-id="28dbb-121">Hinweise zu bestimmten OpenGLES2.0-Anbietern</span><span class="sxs-lookup"><span data-stu-id="28dbb-121">Notes on specific OpenGL ES 2.0 providers</span></span>


<span data-ttu-id="28dbb-122">In diesen Themen wird die OpenGLES2.0-Spezifikation von Khronos mit der plattformagnostischen ProgrammierspracheC verwendet. Sowohl von iOS als auch von Android wird dieselbe Spezifikation genutzt, und der für diese Plattformen entwickelte OpenGLES2.0-Code weist große Ähnlichkeit mit den Codeausschnitten auf, die wir durchgehen werden, obwohl diese meist als objektorientierte APIs verfügbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="28dbb-122">These topics use the Khronos OpenGL ES 2.0 specification with platform-agnostic C. Both iOS and Android utilize the same specification and OpenGL ES 2.0 code developed for those platforms is very similar to the code snippets we will walk through, although they are typically exposed as object-oriented APIs.</span></span> <span data-ttu-id="28dbb-123">Aufgrund der Eigenheiten und Sprachunterschiede der einzelnen Plattformen können geringe Unterschiede bestehen, vor allem bei den Typen der Methodenparameter oder bei der allgemeinen Sprachsyntax.</span><span class="sxs-lookup"><span data-stu-id="28dbb-123">Also, due to the intricacies and language differences of each platform, there may be minor differences, especially in method parameter types, or in general language syntax.</span></span> <span data-ttu-id="28dbb-124">Für iOS wird beispielsweise Objective-C genutzt.</span><span class="sxs-lookup"><span data-stu-id="28dbb-124">iOS, for instance, uses Objective-C.</span></span> <span data-ttu-id="28dbb-125">Für Android kann C++ verwendet werden. Einige Entwickler verlassen sich jedoch möglicherweise auf eine reine Java-Implementierung.</span><span class="sxs-lookup"><span data-stu-id="28dbb-125">Android has the capability to use C++; however, some developers may have relied on a pure Java implementation.</span></span> <span data-ttu-id="28dbb-126">Trotz dieser Unterschiede sind diese Themen hilfreich, da bei den allgemeinen Konzepten, dem Aufbau und der Verwendung der OpenGLES-APIs keine Abweichungen bestehen.</span><span class="sxs-lookup"><span data-stu-id="28dbb-126">With that in mind, these topics should still be useful as the overall concepts, structure and usage of the OpenGL ES APIs do not differ.</span></span>

 

 




