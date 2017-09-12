---
author: mijacobs
title: "Bildschirmgrößen und Haltepunkte für reaktionsfähiges Design"
description: .
ms.assetid: BF42E810-CDC8-47D2-9C30-BAA19DCBE2DA
label: Screen sizes and break points
template: detail.hbs
op-migration-status: ready
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.openlocfilehash: b56cdeeb9a3c3d3ca89e19d8057e3d93241e6c3c
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
#  <a name="screen-sizes-and-break-points-for-responsive-design"></a><span data-ttu-id="71d91-104">Bildschirmgrößen und Haltepunkte für reaktionsfähiges Design</span><span class="sxs-lookup"><span data-stu-id="71d91-104">Screen sizes and break points for responsive design</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

<span data-ttu-id="71d91-105">Die Anzahl der Geräteziele und Bildschirmgrößen bei Windows 10 ist zu groß, um alle beim Optimieren der Benutzeroberfläche zu bedenken.</span><span class="sxs-lookup"><span data-stu-id="71d91-105">The number of device targets and screen sizes across the Windows 10 ecosystem is too great to worry about optimizing your UI for each one.</span></span> <span data-ttu-id="71d91-106">Stattdessen wird empfohlen, bei der Entwicklung einige wichtige Bildschirmbreiten (auch als „Haltepunkte“ bezeichnet) zu berücksichtigen: 360, 640, 1024 und 1366 epx.</span><span class="sxs-lookup"><span data-stu-id="71d91-106">Instead, we recommended designing for a few key widths (also called "breakpoints"): 360, 640, 1024 and 1366 epx.</span></span>

> [!TIP]
> <span data-ttu-id="71d91-107">Bei der Entwicklung für bestimmte Haltepunkte sollten Sie den für Ihre App verfügbaren Bildschirmbereich (App-Fenster) berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="71d91-107">When designing for specific breakpoints, design for the amount of screen space available to your app (the app's window).</span></span> <span data-ttu-id="71d91-108">Wenn die App im Vollbildmodus ausgeführt wird, hat das App-Fenster die gleiche Bildschirmgröße zur Verfügung, in anderen Fällen ist es jedoch kleiner.</span><span class="sxs-lookup"><span data-stu-id="71d91-108">When the app is running full-screen, the app window is the same size as the screen, but in other cases, it's smaller.</span></span>
 

<span data-ttu-id="71d91-109">In dieser Tabelle werden die verschiedenen Größenklassen beschrieben und allgemeine Empfehlungen für die Anpassung für diese Größenklassen aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="71d91-109">This table describes the different size classes and provides general recommendations for tailoring for those size classes.</span></span>

![Reaktionsfähige Designhaltepunkte](images/rsp-design/rspd-breakpoints.png)

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="71d91-111">Größenklasse</span><span class="sxs-lookup"><span data-stu-id="71d91-111">Size class</span></span></th>
<th align="left"><span data-ttu-id="71d91-112">klein</span><span class="sxs-lookup"><span data-stu-id="71d91-112">small</span></span></th>
<th align="left"><span data-ttu-id="71d91-113">mittel</span><span class="sxs-lookup"><span data-stu-id="71d91-113">medium</span></span></th>
<th align="left"><span data-ttu-id="71d91-114">groß</span><span class="sxs-lookup"><span data-stu-id="71d91-114">large</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top;"><span data-ttu-id="71d91-115">Normale Bildschirmgröße (diagonal)</span><span class="sxs-lookup"><span data-stu-id="71d91-115">Typical screen size (diagonal)</span></span></td>
<td style="vertical-align:top;"><span data-ttu-id="71d91-116">4&quot; bis 6</span><span class="sxs-lookup"><span data-stu-id="71d91-116">4&quot; to 6</span></span>&quot;</td>
<td style="vertical-align:top;"><span data-ttu-id="71d91-117">7&quot; bis 12&quot;, oder TV-Geräte</span><span class="sxs-lookup"><span data-stu-id="71d91-117">7&quot; to 12&quot;, or TVs</span></span></td>
<td style="vertical-align:top;"><span data-ttu-id="71d91-118">13&quot; und größer</span><span class="sxs-lookup"><span data-stu-id="71d91-118">13&quot; and larger</span></span></td>
</tr>
<tr class="even">
<td style="vertical-align:top;"><span data-ttu-id="71d91-119">Typische Geräte</span><span class="sxs-lookup"><span data-stu-id="71d91-119">Typical devices</span></span></td>
<td style="vertical-align:top;"><span data-ttu-id="71d91-120">Smartphones</span><span class="sxs-lookup"><span data-stu-id="71d91-120">Phones</span></span></td>
<td style="vertical-align:top;"><span data-ttu-id="71d91-121">Phablets, Tablets, TV-Geräte</span><span class="sxs-lookup"><span data-stu-id="71d91-121">Phablets, tablets, TVs</span></span></td>
<td style="vertical-align:top;"><span data-ttu-id="71d91-122">PCs, Laptops, Surface Hubs</span><span class="sxs-lookup"><span data-stu-id="71d91-122">PCs, laptops, Surface Hubs</span></span></td>
</tr>
<tr class="odd">
<td style="vertical-align:top;"><span data-ttu-id="71d91-123">Übliche Fenstergrößen in effektiven Pixeln</span><span class="sxs-lookup"><span data-stu-id="71d91-123">Common window sizes in effective pixels</span></span></td>
<td style="vertical-align:top;"><span data-ttu-id="71d91-124">320 x 569, 360 x 640, 480 x 854</span><span class="sxs-lookup"><span data-stu-id="71d91-124">320x569, 360x640, 480x854</span></span></td>
<td style="vertical-align:top;"><span data-ttu-id="71d91-125">960 x 540, 1024 x 640</span><span class="sxs-lookup"><span data-stu-id="71d91-125">960x540, 1024x640</span></span></td>
<td style="vertical-align:top;"><span data-ttu-id="71d91-126">1366 x 768, 1920 x 1080</span><span class="sxs-lookup"><span data-stu-id="71d91-126">1366x768, 1920x1080</span></span></td>
</tr>
<tr class="even">
<td style="vertical-align:top;"><span data-ttu-id="71d91-127">Fensterbreite-Haltepunkte in effektiven Pixeln</span><span class="sxs-lookup"><span data-stu-id="71d91-127">Window width breakpoints in effective pixels</span></span></td>
<td style="vertical-align:top;"><span data-ttu-id="71d91-128">640 Pixel oder weniger</span><span class="sxs-lookup"><span data-stu-id="71d91-128">640px or less</span></span></td>
<td style="vertical-align:top;"><span data-ttu-id="71d91-129">641 Pixel bis 1007 Pixel</span><span class="sxs-lookup"><span data-stu-id="71d91-129">641px to 1007px</span></span></td>
<td style="vertical-align:top;"><span data-ttu-id="71d91-130">1008 Pixel oder größer</span><span class="sxs-lookup"><span data-stu-id="71d91-130">1008px or greater</span></span></td>
</tr>
<tr class="odd">
<td style="vertical-align:top;"><span data-ttu-id="71d91-131">Allgemeine Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="71d91-131">General recommendations</span></span></td>
<td style="vertical-align:top;"><ul>
<li><span data-ttu-id="71d91-132">Zentrieren Sie Registerkartenelemente.</span><span class="sxs-lookup"><span data-stu-id="71d91-132">Center tab elements.</span></span></li>
<li><span data-ttu-id="71d91-133">Legen Sie den linken und den rechten Fensterrand auf 12px fest, um eine visuelle Trennung zwischen dem linken und dem rechten Rand des App-Fensters zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="71d91-133">Set left and right window margins to 12px to create a visual separation between the left and right edges of the app window.</span></span></li>
<li><span data-ttu-id="71d91-134">Docken Sie [App-Leisten](../controls-and-patterns/app-bars.md) für bessere Erreichbarkeit am unteren Fensterrand an.</span><span class="sxs-lookup"><span data-stu-id="71d91-134">Dock [app bars](../controls-and-patterns/app-bars.md) to the bottom of the window for improved reachability</span></span></li>
<li><span data-ttu-id="71d91-135">Verwenden Sie jeweils eine Spalte/Region.</span><span class="sxs-lookup"><span data-stu-id="71d91-135">Use one column/region at a time</span></span></li>
<li><span data-ttu-id="71d91-136">Verwenden Sie ein Symbol zum Darstellen der Suche (kein Suchfeld anzeigen).</span><span class="sxs-lookup"><span data-stu-id="71d91-136">Use an icon to represent search (don't show a search box).</span></span></li>
<li><span data-ttu-id="71d91-137">Verwenden Sie den [Navigationsbereich](../controls-and-patterns/navigationview.md) im Überlagerungsmodus, um Platz auf dem Bildschirm zu sparen.</span><span class="sxs-lookup"><span data-stu-id="71d91-137">Put the [navigation pane](../controls-and-patterns/navigationview.md) in overlay mode to conserve screen space.</span></span></li>
<li><span data-ttu-id="71d91-138">Verwenden Sie für das [Master/Details-Modell](../controls-and-patterns/master-details.md) den gestapelten Darstellungsmodus, um Platz auf dem Bildschirm zu sparen.</span><span class="sxs-lookup"><span data-stu-id="71d91-138">If you're using the [master details pattern](../controls-and-patterns/master-details.md), use the stacked presentation mode to save screen space.</span></span></li>
</ul></td>
<td style="vertical-align:top;"><ul>
<li><span data-ttu-id="71d91-139">Richten Sie Registerkartenelemente linksbündig aus.</span><span class="sxs-lookup"><span data-stu-id="71d91-139">Make tab elements left-aligned.</span></span></li>
<li><span data-ttu-id="71d91-140">Legen Sie den linken und den rechten Fensterrand auf 24px fest, um eine visuelle Trennung zwischen dem linken und dem rechten Rand des App-Fensters zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="71d91-140">Set left and right window margins to 24px to create a visual separation between the left and right edges of the app window.</span></span></li>
<li><span data-ttu-id="71d91-141">Positionieren Sie Elemente wie [App-Leisten](../controls-and-patterns/app-bars.md) am oberen Rand des App-Fensters.</span><span class="sxs-lookup"><span data-stu-id="71d91-141">Put command elements like [app bars](../controls-and-patterns/app-bars.md) at the top of the app window.</span></span></li>
<li><span data-ttu-id="71d91-142">Bis zu zwei Spalten/Regionen</span><span class="sxs-lookup"><span data-stu-id="71d91-142">Up to two columns/regions</span></span></li>
<li><span data-ttu-id="71d91-143">Zeigen Sie das Suchfeld an.</span><span class="sxs-lookup"><span data-stu-id="71d91-143">Show the search box.</span></span></li>
<li><span data-ttu-id="71d91-144">Legen Sie für [Navigationsleiste](../controls-and-patterns/navigationview.md) den Streifenmodus fest, sodass immer ein schmaler Streifen mit Symbolen angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="71d91-144">Put the [navigation pane](../controls-and-patterns/navigationview.md) into sliver mode so a narrow strip of icons always shows.</span></span></li>
<li><span data-ttu-id="71d91-145">Ziehen Sie weitere Anpassungen für [TV-Umgebungen](http://go.microsoft.com/fwlink/?LinkId=760736) in Erwägung.</span><span class="sxs-lookup"><span data-stu-id="71d91-145">Consider further tailoring for [TV experiences](http://go.microsoft.com/fwlink/?LinkId=760736).</span></span></li>
</ul></td>
<td style="vertical-align:top;"><ul>
<li><span data-ttu-id="71d91-146">Richten Sie Registerkartenelemente linksbündig aus.</span><span class="sxs-lookup"><span data-stu-id="71d91-146">Make tab elements left-aligned.</span></span></li>
<li><span data-ttu-id="71d91-147">Legen Sie den linken und den rechten Fensterrand auf 24px fest, um eine visuelle Trennung zwischen dem linken und dem rechten Rand des App-Fensters zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="71d91-147">Set left and right window margins to 24px to create a visual separation between the left and right edges of the app window.</span></span></li>
<li><span data-ttu-id="71d91-148">Positionieren Sie Elemente wie [App-Leisten](../controls-and-patterns/app-bars.md) am oberen Rand des App-Fensters.</span><span class="sxs-lookup"><span data-stu-id="71d91-148">Put command elements like [app bars](../controls-and-patterns/app-bars.md) at the top of the app window.</span></span></li>
<li><span data-ttu-id="71d91-149">Bis zu drei Spalten/Regionen</span><span class="sxs-lookup"><span data-stu-id="71d91-149">Up to three columns/regions</span></span></li>
<li><span data-ttu-id="71d91-150">Zeigen Sie das Suchfeld an.</span><span class="sxs-lookup"><span data-stu-id="71d91-150">Show the search box.</span></span></li>
<li><span data-ttu-id="71d91-151">Platzieren Sie den [Navigationsbereich](../controls-and-patterns/navigationview.md) im angedockten Modus so, dass er immer angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="71d91-151">Put the [navigation pane](../controls-and-patterns/navigationview.md) into docked mode so that it always shows.</span></span></li>
</ul></td>
</tr>
</tbody>
</table>

<span data-ttu-id="71d91-152">Mit [**Continuum for Phones**](http://go.microsoft.com/fwlink/p/?LinkID=699431), einer neuen Funktion für kompatible Windows 10-Mobilgeräte, können Benutzer ihre Smartphones mit einem Bildschirm, einer Maus und einer Tastatur verbinden und damit ihr Gerät wie einen Laptop nutzen.</span><span class="sxs-lookup"><span data-stu-id="71d91-152">With [**Continuum for Phones**](http://go.microsoft.com/fwlink/p/?LinkID=699431), a new experience for compatible Windows 10 mobile devices, users can connect their phones to a monitor, mouse and keyboard to make their phones work like laptops.</span></span> <span data-ttu-id="71d91-153">Berücksichtigen Sie diese neue Funktion beim Entwerfen für bestimmte Haltepunkte – ein Mobiltelefon bleibt nicht immer in einer Klasse mit geringer Größe.</span><span class="sxs-lookup"><span data-stu-id="71d91-153">Keep this new capability in mind when designing for specific breakpoints - a mobile phone will not always stay in the small size class.</span></span>
 
