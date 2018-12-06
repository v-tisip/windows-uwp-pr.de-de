---
title: Umstellung von DirectX 9 auf DirectX 11 und UWP
description: Dieser Abschnitt enthält eine Anleitung zum Portieren eines DirectX 9-Desktopspiels zu DirectX 11 und zur universellen Windows-Plattform (UWP).
ms.assetid: 7a3f8ddf-d5b2-1c05-b532-70459befda4e
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, Directx 9, Directx 11, Portieren
ms.localizationpriority: medium
ms.openlocfilehash: 90a9273c33dd45904e2050af02fd52ddeaedb7e5
ms.sourcegitcommit: d7613c791107f74b6a3dc12a372d9de916c0454b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8743463"
---
# <a name="moving-from-directx-9-to-directx-11-and-universal-windows-platform-uwp"></a><span data-ttu-id="6f2bc-104">Wechseln von DirectX9 zu DirectX11 und zur Universellen Windows-Plattform (UWP)</span><span class="sxs-lookup"><span data-stu-id="6f2bc-104">Moving from DirectX 9 to DirectX 11 and Universal Windows Platform (UWP)</span></span>



<span data-ttu-id="6f2bc-105">Dieser Abschnitt enthält eine Anleitung zum Portieren eines DirectX 9-Desktopspiels zu DirectX 11 und zur Universellen Windows-Plattform (UWP).</span><span class="sxs-lookup"><span data-stu-id="6f2bc-105">This section has guidance on porting your DirectX 9 desktop game to DirectX 11 and Universal Windows Platform (UWP).</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="6f2bc-106">Thema</span><span class="sxs-lookup"><span data-stu-id="6f2bc-106">Topic</span></span></th>
<th align="left"><span data-ttu-id="6f2bc-107">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6f2bc-107">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="plan-your-directx-port.md"><span data-ttu-id="6f2bc-108">Planen der DirectX-Portierung</span><span class="sxs-lookup"><span data-stu-id="6f2bc-108">Plan your DirectX port</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="6f2bc-109">Planen Sie das Portieren des Spiels von DirectX 9 zu DirectX 11 und zur UWP: Führen Sie ein Upgrade des Grafikcodes durch, und fügen Sie das Spiel in die Windows-Runtime-Umgebung ein.</span><span class="sxs-lookup"><span data-stu-id="6f2bc-109">Plan your game porting project from DirectX 9 to DirectX 11 and UWP: upgrade your graphics code, and put your game in the Windows Runtime environment.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="understand-direct3d-11-1-concepts.md"><span data-ttu-id="6f2bc-110">Wichtige Änderungen beim Wechsel von Direct3D9 zu Direct3D11.1</span><span class="sxs-lookup"><span data-stu-id="6f2bc-110">Important changes from Direct3D 9 to Direct3D 11.1</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="6f2bc-111">In diesem Thema werden allgemeine Unterschiede zwischen DirectX9 und DirectX11 erläutert.</span><span class="sxs-lookup"><span data-stu-id="6f2bc-111">This topic explains the high-level differences between DirectX 9 and DirectX 11.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="feature-mapping.md"><span data-ttu-id="6f2bc-112">Zuordnung von DirectX9-Features zu DirectX11.1-APIs</span><span class="sxs-lookup"><span data-stu-id="6f2bc-112">Map DirectX 9 features to DirectX 11.1 APIs</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="6f2bc-113">Erfahren Sie, wie die Features Ihres Direct3D 9-Spiels zu Direct3D 11 und zur UWP zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="6f2bc-113">Understand how the features your Direct3D 9 game uses will translate to Direct3D 11 and the UWP.</span></span></p></td>
</tr>
</tbody>
</table>

 

 

 




