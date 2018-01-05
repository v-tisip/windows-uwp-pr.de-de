---
author: mtoepke
title: Umstellung von DirectX 9 auf DirectX 11 und UWP
description: "Dieser Abschnitt enthält eine Anleitung zum Portieren eines DirectX 9-Desktopspiels zu DirectX 11 und zur universellen Windows-Plattform (UWP)."
ms.assetid: 7a3f8ddf-d5b2-1c05-b532-70459befda4e
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Spiele, Directx 9, Directx 11, Portieren
ms.openlocfilehash: ea89fe1e87099f96b78e06664bd2a252d18ddc26
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
ms.translationtype: HT
ms.contentlocale: de-DE
---
# <a name="moving-from-directx-9-to-directx-11-and-universal-windows-platform-uwp"></a><span data-ttu-id="54e18-104">Wechseln von DirectX9 zu DirectX11 und zur Universellen Windows-Plattform (UWP)</span><span class="sxs-lookup"><span data-stu-id="54e18-104">Moving from DirectX 9 to DirectX 11 and Universal Windows Platform (UWP)</span></span>


<span data-ttu-id="54e18-105">\[ Aktualisiert für UWP-Apps unter Windows 10.</span><span class="sxs-lookup"><span data-stu-id="54e18-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="54e18-106">Artikel zu Windows 8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span><span class="sxs-lookup"><span data-stu-id="54e18-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>

<span data-ttu-id="54e18-107">Dieser Abschnitt enthält eine Anleitung zum Portieren eines DirectX 9-Desktopspiels zu DirectX 11 und zur Universellen Windows-Plattform (UWP).</span><span class="sxs-lookup"><span data-stu-id="54e18-107">This section has guidance on porting your DirectX 9 desktop game to DirectX 11 and Universal Windows Platform (UWP).</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="54e18-108">Thema</span><span class="sxs-lookup"><span data-stu-id="54e18-108">Topic</span></span></th>
<th align="left"><span data-ttu-id="54e18-109">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="54e18-109">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>[<span data-ttu-id="54e18-110">Planen der DirectX-Portierung</span><span class="sxs-lookup"><span data-stu-id="54e18-110">Plan your DirectX port</span></span>](plan-your-directx-port.md)</p></td>
<td align="left"><p><span data-ttu-id="54e18-111">Planen Sie das Portieren des Spiels von DirectX 9 zu DirectX 11 und zur UWP: Führen Sie ein Upgrade des Grafikcodes durch, und fügen Sie das Spiel in die Windows-Runtime-Umgebung ein.</span><span class="sxs-lookup"><span data-stu-id="54e18-111">Plan your game porting project from DirectX 9 to DirectX 11 and UWP: upgrade your graphics code, and put your game in the Windows Runtime environment.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p>[<span data-ttu-id="54e18-112">Wichtige Änderungen beim Wechsel von Direct3D9 zu Direct3D11.1</span><span class="sxs-lookup"><span data-stu-id="54e18-112">Important changes from Direct3D 9 to Direct3D 11.1</span></span>](understand-direct3d-11-1-concepts.md)</p></td>
<td align="left"><p><span data-ttu-id="54e18-113">In diesem Thema werden allgemeine Unterschiede zwischen DirectX9 und DirectX11 erläutert.</span><span class="sxs-lookup"><span data-stu-id="54e18-113">This topic explains the high-level differences between DirectX 9 and DirectX 11.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p>[<span data-ttu-id="54e18-114">Zuordnung von DirectX9-Features zu DirectX11.1-APIs</span><span class="sxs-lookup"><span data-stu-id="54e18-114">Map DirectX 9 features to DirectX 11.1 APIs</span></span>](feature-mapping.md)</p></td>
<td align="left"><p><span data-ttu-id="54e18-115">Erfahren Sie, wie die Features Ihres Direct3D 9-Spiels zu Direct3D 11 und zur UWP zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="54e18-115">Understand how the features your Direct3D 9 game uses will translate to Direct3D 11 and the UWP.</span></span></p></td>
</tr>
</tbody>
</table>

 

 

 




