---
author: mtoepke
title: Zuordnen von OpenGLES2.0 zu Direct3D11
description: Machen Sie sich zu Beginn des Prozesses zur ersten Portierung Ihrer Grafikarchitektur von OpenGL ES 2.0 zu Direct3D mit den Hauptunterschieden zwischen den APIs vertraut.
ms.assetid: 7f9b136c-aa22-04b3-d385-6e9e1f38b948
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Spiele, OpenGL, Direct3D, Portieren
ms.openlocfilehash: 1298f165444b31c75ca9d98f04eb82a58be46e5b
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
ms.translationtype: HT
ms.contentlocale: de-DE
---
# <a name="map-opengl-es-20-to-direct3d-11"></a><span data-ttu-id="84233-104">Zuordnen von OpenGLES2.0 zu Direct3D11</span><span class="sxs-lookup"><span data-stu-id="84233-104">Map OpenGL ES 2.0 to Direct3D 11</span></span>


<span data-ttu-id="84233-105">\[ Aktualisiert für UWP-Apps unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="84233-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="84233-106">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span><span class="sxs-lookup"><span data-stu-id="84233-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>

<span data-ttu-id="84233-107">Machen Sie sich zu Beginn des Prozesses zur ersten Portierung Ihrer Grafikarchitektur von OpenGL ES 2.0 zu Direct3D mit den Hauptunterschieden zwischen den APIs vertraut.</span><span class="sxs-lookup"><span data-stu-id="84233-107">When starting the process of porting your graphics architecture from OpenGL ES 2.0 to Direct3D for the first time, familiarize yourself with the key differences between the APIs.</span></span> <span data-ttu-id="84233-108">Mithilfe der Themen in diesem Abschnitt können Sie die Portierungsstrategie und die API-Änderungen planen, die erforderlich sind, wenn Sie die Grafikverarbeitung auf Direct3D umstellen.</span><span class="sxs-lookup"><span data-stu-id="84233-108">The topics in this section help you plan your port strategy and the API changes that you must make when moving your graphics processing to Direct3D.</span></span>
## 
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="84233-109">Thema</span><span class="sxs-lookup"><span data-stu-id="84233-109">Topic</span></span></th>
<th align="left"><span data-ttu-id="84233-110">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="84233-110">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>[<span data-ttu-id="84233-111">Planen der Portierung von OpenGLES2.0 zu Direct3D</span><span class="sxs-lookup"><span data-stu-id="84233-111">Plan your port from OpenGL ES 2.0 to Direct3D</span></span>](compare-opengl-es-2-0-api-design-to-directx.md)</p></td>
<td align="left"><p><span data-ttu-id="84233-112">Wenn Sie ein Spiel von der iOS- oder Android-Plattform portieren, haben Sie vermutlich erheblich in OpenGLES2.0 investiert.</span><span class="sxs-lookup"><span data-stu-id="84233-112">If you are porting a game from the iOS or Android platforms, you have probably made a significant investment in OpenGL ES 2.0.</span></span> <span data-ttu-id="84233-113">Beim Vorbereiten der Portierung Ihrer Grafikpipeline-Codebasis zu Direct3D11 und der Windows-Runtime sind im Vorfeld einige Dinge zu beachten.</span><span class="sxs-lookup"><span data-stu-id="84233-113">When preparing to move your graphics pipeline codebase to Direct3D 11 and the Windows Runtime, there are a few things you should consider before you start.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p>[<span data-ttu-id="84233-114">Vergleichen des EGL-Codes mit DXGI und Direct3D</span><span class="sxs-lookup"><span data-stu-id="84233-114">Compare EGL code to DXGI and Direct3D</span></span>](moving-from-egl-to-dxgi.md)</p></td>
<td align="left"><p><span data-ttu-id="84233-115">Die DirectX-Grafikschnittstelle (DXGI) und verschiedene Direct3D-APIs erfüllen die gleiche Rolle wie EGL.</span><span class="sxs-lookup"><span data-stu-id="84233-115">The DirectX Graphics Interface (DXGI) and several Direct3D APIs serve the same role as EGL.</span></span> <span data-ttu-id="84233-116">In diesem Thema werden die DXGI und Direct3D11 aus Sicht von EGL erläutert.</span><span class="sxs-lookup"><span data-stu-id="84233-116">This topic helps you understand DXGI and Direct3D 11 from the perspective of EGL.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p>[<span data-ttu-id="84233-117">Vergleichen von OpenGLES2.0-Puffern, -uniform-Elementen und -Vertexattributen mit Direct3D</span><span class="sxs-lookup"><span data-stu-id="84233-117">Compare OpenGL ES 2.0 buffers, uniforms, and vertex attributes to Direct3D</span></span>](porting-uniforms-and-attributes.md)</p></td>
<td align="left"><p><span data-ttu-id="84233-118">Während des Portierens zu Direct3D 11 aus OpenGL ES 2.0 müssen Sie die Syntax und das API-Verhalten zum Übergeben von Daten zwischen der App und den Shaderprogrammen ändern.</span><span class="sxs-lookup"><span data-stu-id="84233-118">During the process of porting to Direct3D 11 from OpenGL ES 2.0, you must change the syntax and API behavior for passing data between the app and the shader programs.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p>[<span data-ttu-id="84233-119">Vergleich der OpenGLES2.0-Shaderpipeline mit Direct3D</span><span class="sxs-lookup"><span data-stu-id="84233-119">Compare the OpenGL ES 2.0 shader pipeline to Direct3D</span></span>](change-your-shader-loading-code.md)</p></td>
<td align="left"><p><span data-ttu-id="84233-120">Vom Konzept her ist die Direct3D11-Shaderpipeline der in OpenGLES2.0 sehr ähnlich.</span><span class="sxs-lookup"><span data-stu-id="84233-120">Conceptually, the Direct3D 11 shader pipeline is very similar to the one in OpenGL ES 2.0.</span></span> <span data-ttu-id="84233-121">Hinsichtlich des API-Entwurfs sind die Hauptkomponenten für die Erstellung und Verwaltung der Shaderstufen jedoch Teile der zwei primären Schnittstellen [<strong>ID3D11Device1</strong>](https://msdn.microsoft.com/library/windows/desktop/hh404575) und [<strong>ID3D11DeviceContext1</strong>](https://msdn.microsoft.com/library/windows/desktop/hh404598).</span><span class="sxs-lookup"><span data-stu-id="84233-121">In terms of API design, however, the major components for creating and managing the shader stages are parts of two primary interfaces, [<strong>ID3D11Device1</strong>](https://msdn.microsoft.com/library/windows/desktop/hh404575) and [<strong>ID3D11DeviceContext1</strong>](https://msdn.microsoft.com/library/windows/desktop/hh404598).</span></span> <span data-ttu-id="84233-122">In diesem Thema versuchen wir, allgemeine Muster der OpenGLES2.0-Shaderpipeline-API den Direct3D11-Entsprechungen in diesen Schnittstellen zuzuordnen.</span><span class="sxs-lookup"><span data-stu-id="84233-122">This topic attempts to map common OpenGL ES 2.0 shader pipeline API patterns to the Direct3D 11 equivalents in these interfaces.</span></span></p></td>
</tr>
</tbody>
</table>

 

## <a name="notes-on-specific-opengl-es-20-providers"></a><span data-ttu-id="84233-123">Hinweise zu bestimmten OpenGLES2.0-Anbietern</span><span class="sxs-lookup"><span data-stu-id="84233-123">Notes on specific OpenGL ES 2.0 providers</span></span>


<span data-ttu-id="84233-124">In diesen Themen wird die OpenGLES2.0-Spezifikation von Khronos mit der plattformagnostischen ProgrammierspracheC verwendet. Sowohl von iOS als auch von Android wird dieselbe Spezifikation genutzt, und der für diese Plattformen entwickelte OpenGLES2.0-Code weist große Ähnlichkeit mit den Codeausschnitten auf, die wir durchgehen werden, obwohl diese meist als objektorientierte APIs verfügbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="84233-124">These topics use the Khronos OpenGL ES 2.0 specification with platform-agnostic C. Both iOS and Android utilize the same specification and OpenGL ES 2.0 code developed for those platforms is very similar to the code snippets we will walk through, although they are typically exposed as object-oriented APIs.</span></span> <span data-ttu-id="84233-125">Aufgrund der Eigenheiten und Sprachunterschiede der einzelnen Plattformen können geringe Unterschiede bestehen, vor allem bei den Typen der Methodenparameter oder bei der allgemeinen Sprachsyntax.</span><span class="sxs-lookup"><span data-stu-id="84233-125">Also, due to the intricacies and language differences of each platform, there may be minor differences, especially in method parameter types, or in general language syntax.</span></span> <span data-ttu-id="84233-126">Für iOS wird beispielsweise Objective-C genutzt.</span><span class="sxs-lookup"><span data-stu-id="84233-126">iOS, for instance, uses Objective-C.</span></span> <span data-ttu-id="84233-127">Für Android kann C++ verwendet werden. Einige Entwickler verlassen sich jedoch möglicherweise auf eine reine Java-Implementierung.</span><span class="sxs-lookup"><span data-stu-id="84233-127">Android has the capability to use C++; however, some developers may have relied on a pure Java implementation.</span></span> <span data-ttu-id="84233-128">Trotz dieser Unterschiede sind diese Themen hilfreich, da bei den allgemeinen Konzepten, dem Aufbau und der Verwendung der OpenGLES-APIs keine Abweichungen bestehen.</span><span class="sxs-lookup"><span data-stu-id="84233-128">With that in mind, these topics should still be useful as the overall concepts, structure and usage of the OpenGL ES APIs do not differ.</span></span>

 

 




