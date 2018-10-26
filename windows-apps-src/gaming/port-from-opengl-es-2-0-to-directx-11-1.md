---
author: mtoepke
title: Portieren von OpenGLES2.0 zu Direct3D11
description: Enthält Artikel, Übersichten und exemplarische Vorgehensweisen zum Portieren einer OpenGL ES 2.0-Grafikpipeline zu Direct3D 11 und zur Windows-Runtime.
ms.assetid: 1e1cf668-a15f-0c7b-8daf-3260d27c6d9c
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, Opengl, Direct3D 11, Portieren, Grafiken
ms.localizationpriority: medium
ms.openlocfilehash: 6421f5a5a71828d5234a11bab9e442a5accecda5
ms.sourcegitcommit: 6cc275f2151f78db40c11ace381ee2d35f0155f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5570518"
---
# <a name="port-from-opengl-es-20-to-direct3d-11"></a><span data-ttu-id="75f58-104">Portieren von OpenGL ES 2.0 zu Direct3D 11</span><span class="sxs-lookup"><span data-stu-id="75f58-104">Port from OpenGL ES 2.0 to Direct3D 11</span></span>



<span data-ttu-id="75f58-105">Enthält Artikel, Übersichten und exemplarische Vorgehensweisen zum Portieren einer OpenGL ES 2.0-Grafikpipeline zu Direct3D 11 und zur Windows-Runtime.</span><span class="sxs-lookup"><span data-stu-id="75f58-105">Includes articles, overviews, and walkthroughs for porting an OpenGL ES 2.0 graphics pipeline to a Direct3D 11 and the Windows Runtime.</span></span>

> <span data-ttu-id="75f58-106">**Hinweis:**  ein Zwischenschritt zum Portieren Ihres OpenGL ES 2.0-Projekts ist die Verwendung von ANGLE für Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="75f58-106">**Note** An intermediate step to porting your OpenGL ES 2.0 project is to use ANGLE for Microsoft Store.</span></span> <span data-ttu-id="75f58-107">Mit ANGLE können Sie OpenGL ES-Inhalte unter Windows ausführen, indem Sie OpenGL ES-API-Aufrufe in DirectX11-API-Aufrufe übersetzen.</span><span class="sxs-lookup"><span data-stu-id="75f58-107">ANGLE allows you to run OpenGL ES content on Windows by translating OpenGL ES API calls to DirectX 11 API calls.</span></span> <span data-ttu-id="75f58-108">Weitere Informationen zu ANGLE finden Sie im [ANGLE für Microsoft Store-Wiki](http://go.microsoft.com/fwlink/p/?linkid=618387).</span><span class="sxs-lookup"><span data-stu-id="75f58-108">For more information about ANGLE, go to the [ANGLE for Microsoft Store Wiki](http://go.microsoft.com/fwlink/p/?linkid=618387).</span></span>

 

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="75f58-109">Thema</span><span class="sxs-lookup"><span data-stu-id="75f58-109">Topic</span></span></th>
<th align="left"><span data-ttu-id="75f58-110">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="75f58-110">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="map-concepts-and-infrastructure.md"><span data-ttu-id="75f58-111">Zuordnen von OpenGL ES 2.0 zu Direct3D 11,1</span><span class="sxs-lookup"><span data-stu-id="75f58-111">Map OpenGL ES 2.0 to Direct3D 11.1</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="75f58-112">Machen Sie sich zu Beginn des Prozesses zur ersten Portierung Ihrer Grafikarchitektur von OpenGL ES 2.0 zu Direct3D mit den Hauptunterschieden zwischen den APIs vertraut.</span><span class="sxs-lookup"><span data-stu-id="75f58-112">When starting the process of porting your graphics architecture from OpenGL ES 2.0 to Direct3D for the first time, familiarize yourself with the key differences between the APIs.</span></span> <span data-ttu-id="75f58-113">Mithilfe der Themen in diesem Abschnitt können Sie die Portierungsstrategie und die API-Änderungen planen, die erforderlich sind, wenn Sie die Grafikverarbeitung auf Direct3D umstellen.</span><span class="sxs-lookup"><span data-stu-id="75f58-113">The topics in this section help you plan your port strategy and the API changes that you must make when moving your graphics processing to Direct3D.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="port-a-simple-opengl-es-2-0-renderer-to-directx-11-1.md"><span data-ttu-id="75f58-114">So wird's gemacht: Portieren eines einfachen OpenGLES2.0-Renderers zu Direct3D11.1</span><span class="sxs-lookup"><span data-stu-id="75f58-114">How to: port a simple OpenGL ES 2.0 renderer to Direct3D 11.1</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="75f58-115">In dieser Portierungsübung beginnen wir mit den Grundlagen: Umstellen eines einfachen Renderers für einen sich drehenden Würfel mit Vertexschattierungen von OpenGLES2.0 auf Direct3D, damit er der Vorlage „DirectX11-App (Universelle Windows-App)“ aus Visual Studio2015 entspricht.</span><span class="sxs-lookup"><span data-stu-id="75f58-115">For this porting exercise, we'll start with the basics: bringing a simple renderer for a spinning, vertex-shaded cube from OpenGL ES 2.0 into Direct3D, such that it matches the DirectX 11 App (Universal Windows) template from Visual Studio 2015.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="opengl-es-2-0-to-directx-11-1-reference.md"><span data-ttu-id="75f58-116">OpenGLES2.0 zu Direct3D11.1 – Referenz</span><span class="sxs-lookup"><span data-stu-id="75f58-116">OpenGL ES 2.0 to Direct3D 11.1 reference</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="75f58-117">Verwenden Sie diese Referenzthemen zum Suchen nach der API-Zuordnung und kurzen Codebeispielen, wenn Sie die Portierung von OpenGL ES 2.0 zu Direct3D 11 durchführen.</span><span class="sxs-lookup"><span data-stu-id="75f58-117">Use these reference topics to look up API mapping and short code samples when porting from OpenGL ES 2.0 to Direct3D 11.</span></span></p></td>
</tr>
</tbody>
</table>

 

 

 




