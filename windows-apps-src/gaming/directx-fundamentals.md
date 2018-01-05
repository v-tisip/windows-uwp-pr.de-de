---
author: joannaleecy
title: Grundlagen der DirectX-Programmierung
description: Die Grundlagen der DirectX-Programmierung.
ms.assetid: 05a1bc59-f32e-44a0-8902-94cf1e099b1b
ms.author: joanlee
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Spiel, DirectX, laden, rastern, Gitter, Bitmap, 2D, 3D
ms.openlocfilehash: 2633bba5425ca78c3f109a4571fd8c0529f17b56
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
ms.translationtype: HT
ms.contentlocale: de-DE
---
# <a name="fundamentals-of-directx-programming"></a><span data-ttu-id="7024b-104">Grundlagen der DirectX-Programmierung</span><span class="sxs-lookup"><span data-stu-id="7024b-104">Fundamentals of DirectX programming</span></span>

<span data-ttu-id="7024b-105">Dieser Abschnitt enthält Informationen zu den Grundbausteinen der DirectX-Programmierung.</span><span class="sxs-lookup"><span data-stu-id="7024b-105">This section provides information about the basic blocks of DirectX programming.</span></span>

<span data-ttu-id="7024b-106">Im Thema „2D-Grafiken für DirectX-Spiele” wird die Verwendung von 2D-Bitmap-Grafiken und -Effekten erläutert, und wie Sie diese mithilfe von Elementen aus Direct2D- und Direct3D-Bibliotheken in Ihrem Spiel verwenden können.</span><span class="sxs-lookup"><span data-stu-id="7024b-106">2D graphics for DirectX games topic explains the use of 2D bitmap graphics and effects, and how to use them in your game using a combination of elements from both Direct2D and Direct3D libraries.</span></span>

<span data-ttu-id="7024b-107">Das Thema „Lernanleitung für Direct3D-Grafiken” enthält eine Übersicht über die Konzepte, die Direct3D verwendet.</span><span class="sxs-lookup"><span data-stu-id="7024b-107">Direct3D graphics learning guide topic provides an overview of the concepts that Direct3D uses.</span></span>

<span data-ttu-id="7024b-108">Im Thema „Grundlegendes zu 3D-Grafiken für DirectX-Spiele” werden die grundlegenden Konzepte von 3D-Grafiken anhand eines fünfteiligen Lernprogramms erläutert, das das Direct3D-Konzept und die API vorstellt.</span><span class="sxs-lookup"><span data-stu-id="7024b-108">Basic 3D graphics for DirectX games topic explains the fundamental concepts of 3D graphics using a five-part tutorial that introduces the Direct3D concept and API.</span></span> <span data-ttu-id="7024b-109">Dieses Lernprogramm erläutert das Initialisieren der Direct3D-Schnittstellen mit der Windows-Runtime, das Anwenden von Vertex-Shader-Operationen, das Einrichten der Geometrie, das Rastern der Szene und das Culling verborgener Oberflächen.</span><span class="sxs-lookup"><span data-stu-id="7024b-109">This tutorial shows you how to initialize Direct3D interfaces using Windows Runtime, apply per-vertex shader operations, set up the geometry, rasterize the scene, and cull hidden surfaces.</span></span>

<span data-ttu-id="7024b-110">Das Thema „Laden von Ressourcen im DirectX-Spiel” führt Sie durch die grundlegenden Schritte zum Laden der Gitter (Modelle), Texturen (Bitmaps) und kompilierten Shaderobjekte aus einem lokalen Speicher oder anderen Datenströmen zur Verwendung in Ihrem UWP-Spiel.</span><span class="sxs-lookup"><span data-stu-id="7024b-110">Load resources in your DirectX game topic guides you through the basic steps for loading meshes (models), textures (bitmaps), and compiled shader objects from local storage or other data streams for use in your UWP game.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="7024b-111">Thema</span><span class="sxs-lookup"><span data-stu-id="7024b-111">Topic</span></span></th>
<th align="left"><span data-ttu-id="7024b-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7024b-112">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>[<span data-ttu-id="7024b-113">2D-Grafiken für DirectX-Spiele</span><span class="sxs-lookup"><span data-stu-id="7024b-113">2D graphics for DirectX games</span></span>](working-with-2d-graphics-in-your-directx-game.md)</p></td>
<td align="left"><p><span data-ttu-id="7024b-114">Erstellen von 2D-Grafiken mit DirectX</span><span class="sxs-lookup"><span data-stu-id="7024b-114">Create 2D graphics using DirectX.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p>[<span data-ttu-id="7024b-115">Lernanleitung für Direct3D-Grafiken</span><span class="sxs-lookup"><span data-stu-id="7024b-115">Direct3D graphics learning guide</span></span>](https://msdn.microsoft.com/windows/uwp/graphics-concepts/index)</p></td>
<td align="left"><p><span data-ttu-id="7024b-116">Machen Sie sich mit den Direct3D-Grafikkonzepten vertraut.</span><span class="sxs-lookup"><span data-stu-id="7024b-116">Understand Direct3D graphics concepts.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p>[<span data-ttu-id="7024b-117">Grundlegendes zu 3D-Grafiken für DirectX-Spiele</span><span class="sxs-lookup"><span data-stu-id="7024b-117">Basic 3D graphics for DirectX games</span></span>](an-introduction-to-3d-graphics-with-directx.md)</p></td>
<td align="left"><p><span data-ttu-id="7024b-118">Erstellen Sie einfache 3D DirectX-Grafiken.</span><span class="sxs-lookup"><span data-stu-id="7024b-118">Create basic 3D DirectX graphics.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p>[<span data-ttu-id="7024b-119">Laden von Ressourcen im DirectX-Spiel</span><span class="sxs-lookup"><span data-stu-id="7024b-119">Load resources in your DirectX game</span></span>](load-a-game-asset.md)</p></td>
<td align="left"><p><span data-ttu-id="7024b-120">Laden Sie Gitter in Ihrem DirectX-Spiel.</span><span class="sxs-lookup"><span data-stu-id="7024b-120">Load meshes in your DirectX game.</span></span></p></td>
</tr>
</tbody>
</table>