---
author: mijacobs
title: Bildschirmgrößen und Haltepunkte für reaktionsfähiges Design
description: Anstatt Ihre Benutzeroberfläche für die vielen Geräte im gesamten Windows 10-Ökosystem zu optimieren, empfehlen wir, ein Design für einige Schlüsselbreiten (sogenannte Breakpoints) zu erstellen.
ms.author: mijacobs
ms.date: 08/30/2017
ms.topic: article
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: dbe71805ac0607a974374fb7a4f50a1d3f4d6811
ms.sourcegitcommit: 3257416aebb5a7b1515e107866806f8bd57845a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2018
ms.locfileid: "7156165"
---
#  <a name="screen-sizes-and-breakpoints"></a><span data-ttu-id="9e1df-104">Bildschirmgrößen und Breakpoints</span><span class="sxs-lookup"><span data-stu-id="9e1df-104">Screen sizes and breakpoints</span></span>

<span data-ttu-id="9e1df-105">UWP-Apps können auf jedem Gerät mit Windows 10 ausgeführt werden – z. B. Telefone, Tablets, Desktops, Fernseher und mehr.</span><span class="sxs-lookup"><span data-stu-id="9e1df-105">UWP apps can run on any device running Windows 10, which includes phones, tablets, desktops, TVs, and more.</span></span> <span data-ttu-id="9e1df-106">Mit einer großen Anzahl der geräteziele und Bildschirmgrößen über das Windows 10-Ökosystem, anstatt die Optimierung der Benutzeroberfläche für jedes Gerät empfehlen wir, ein Design für einige schlüsselbreiten (sogenannte "Breakpoints"):</span><span class="sxs-lookup"><span data-stu-id="9e1df-106">With a huge number of device targets and screen sizes across the Windows10 ecosystem, rather than optimizing your UI for each device, we recommended designing for a few key width categories (also called "breakpoints"):</span></span> 
- <span data-ttu-id="9e1df-107">Klein (kleiner als 640 Pixel)</span><span class="sxs-lookup"><span data-stu-id="9e1df-107">Small (smaller than 640px)</span></span>
- <span data-ttu-id="9e1df-108">Mittel (641 Pixel bis 1007 Pixel)</span><span class="sxs-lookup"><span data-stu-id="9e1df-108">Medium (641px to 1007px)</span></span>
- <span data-ttu-id="9e1df-109">Groß (1008 Pixel und größer)</span><span class="sxs-lookup"><span data-stu-id="9e1df-109">Large (1008px and larger)</span></span>

> [!TIP]
> <span data-ttu-id="9e1df-110">Beim Entwerfen für bestimmte Breakpoints sollten Sie den für Ihre App verfügbaren Bildschirmbereich (App-Fenster) berücksichtigen, nicht die Bildschirmgröße.</span><span class="sxs-lookup"><span data-stu-id="9e1df-110">When designing for specific breakpoints, design for the amount of screen space available to your app (the app's window), not the screen size.</span></span> <span data-ttu-id="9e1df-111">Wenn die App im Vollbildmodus läuft, hat das App-Fenster die gleiche Größe wie der Bildschirm, aber wenn die App nicht im Vollbildmodus ist, ist das Fenster kleiner als der Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="9e1df-111">When the app is running full-screen, the app window is the same size as the screen, but when the app is not full-screen, the window is smaller than the screen.</span></span>

## <a name="breakpoints"></a><span data-ttu-id="9e1df-112">Breakpoints</span><span class="sxs-lookup"><span data-stu-id="9e1df-112">Breakpoints</span></span>
<span data-ttu-id="9e1df-113">Diese Tabelle beschreibt die verschiedenen Größenklassen und Breakpoints.</span><span class="sxs-lookup"><span data-stu-id="9e1df-113">This table describes the different size classes and breakpoints.</span></span>

![Reaktionsfähige Designbreakpoints](images/breakpoints/size-classes.svg)

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="9e1df-115">Größenklasse</span><span class="sxs-lookup"><span data-stu-id="9e1df-115">Size class</span></span></th>
<th align="left"><span data-ttu-id="9e1df-116">Breakpoints</span><span class="sxs-lookup"><span data-stu-id="9e1df-116">Breakpoints</span></span></th>
<th align="left"><span data-ttu-id="9e1df-117">Typische Bildschirmgröße (diagonal)</span><span class="sxs-lookup"><span data-stu-id="9e1df-117">Typical screen size (diagonal)</span></span></th>
<th align="left"><span data-ttu-id="9e1df-118">Geräte</span><span class="sxs-lookup"><span data-stu-id="9e1df-118">Devices</span></span></th>
<th align="left"><span data-ttu-id="9e1df-119">Fenstergrößen</span><span class="sxs-lookup"><span data-stu-id="9e1df-119">Window sizes</span></span></th>
</tr>
</thead>
<tbody>
<tr class="even">
<td style="vertical-align:top;"><span data-ttu-id="9e1df-120">Klein</span><span class="sxs-lookup"><span data-stu-id="9e1df-120">Small</span></span></td>
<td style="vertical-align:top;"><span data-ttu-id="9e1df-121">640 Pixel oder weniger</span><span class="sxs-lookup"><span data-stu-id="9e1df-121">640px or less</span></span></td>
<td style="vertical-align:top;"><span data-ttu-id="9e1df-122">4&quot; bis 6&quot;; 20&quot; bis 65&quot;</span><span class="sxs-lookup"><span data-stu-id="9e1df-122">4&quot; to 6&quot;; 20&quot; to 65&quot;</span></span></td>
<td style="vertical-align:top;"><span data-ttu-id="9e1df-123">Smartphones, TV-Geräte</span><span class="sxs-lookup"><span data-stu-id="9e1df-123">Phones, TVs</span></span></td>
<td style="vertical-align:top;"><span data-ttu-id="9e1df-124">320 x 569, 360 x 640, 480 x 854</span><span class="sxs-lookup"><span data-stu-id="9e1df-124">320x569, 360x640, 480x854</span></span></td>
</tr>
<tr class="odd">
<td style="vertical-align:top;"><span data-ttu-id="9e1df-125">Mittel</span><span class="sxs-lookup"><span data-stu-id="9e1df-125">Medium</span></span></td>
<td style="vertical-align:top;"><span data-ttu-id="9e1df-126">641 Pixel bis 1007 Pixel</span><span class="sxs-lookup"><span data-stu-id="9e1df-126">641px to 1007px</span></span></td>
<td style="vertical-align:top;"><span data-ttu-id="9e1df-127">7&quot; bis 12&quot;</span><span class="sxs-lookup"><span data-stu-id="9e1df-127">7&quot; to 12&quot;</span></span></td>
<td style="vertical-align:top;"><span data-ttu-id="9e1df-128">Phablets, Tablets</span><span class="sxs-lookup"><span data-stu-id="9e1df-128">Phablets, tablets</span></span></td>
<td style="vertical-align:top;"><span data-ttu-id="9e1df-129">960 x 540</span><span class="sxs-lookup"><span data-stu-id="9e1df-129">960x540</span></span></td>
</tr>
<tr class="even">
<td style="vertical-align:top;"><span data-ttu-id="9e1df-130">Groß</span><span class="sxs-lookup"><span data-stu-id="9e1df-130">Large</span></span></td>
<td style="vertical-align:top;"><span data-ttu-id="9e1df-131">1008 Pixel oder mehr</span><span class="sxs-lookup"><span data-stu-id="9e1df-131">1008px or greater</span></span></td>
<td style="vertical-align:top;"><span data-ttu-id="9e1df-132">13&quot; und größer</span><span class="sxs-lookup"><span data-stu-id="9e1df-132">13&quot; and larger</span></span></td>
<td style="vertical-align:top;"><span data-ttu-id="9e1df-133">PCs, Laptops, Surface Hubs</span><span class="sxs-lookup"><span data-stu-id="9e1df-133">PCs, laptops, Surface Hubs</span></span></td>
<td style="vertical-align:top;"><span data-ttu-id="9e1df-134">1024 x 640, 1366 x 768, 1920 x 1080</span><span class="sxs-lookup"><span data-stu-id="9e1df-134">1024x640, 1366x768, 1920x1080</span></span></td>
</tr>
</tbody>
</table>

## <a name="why-are-tvs-considered-small"></a><span data-ttu-id="9e1df-135">Warum stehen TV-Geräte unter „klein”?</span><span class="sxs-lookup"><span data-stu-id="9e1df-135">Why are TVs considered "small"?</span></span> 

<span data-ttu-id="9e1df-136">Obwohl die meisten TV-Geräte physisch ziemlich groß sind (40 bis 65 Zoll sind üblich) und hohe Auflösungen haben (HD oder 4k), unterscheidet sich das Entwerfen für ein 1080P-TV-Gerät, das Sie aus 3 Meter Abstand betrachten, vom Entwerfen für einem 1080p-Monitor auf Ihrem Schreibtisch.</span><span class="sxs-lookup"><span data-stu-id="9e1df-136">While most TVs are physically quite large (40 to 65 inches is common) and have high resolutions (HD or 4k), designing for a 1080P TV that you view from 10 feet away is different from designing for a 1080p monitor sitting a foot away on your desk.</span></span> <span data-ttu-id="9e1df-137">Wenn Sie den Abstand berücksichtigen, entsprechen die 1080-Pixel des TV-Geräts eher einem 540-Pixel-Monitor, der viel näher steht.</span><span class="sxs-lookup"><span data-stu-id="9e1df-137">When you account for distance, the TV's 1080 pixels are more like a 540-pixel monitor that's much closer.</span></span>

<span data-ttu-id="9e1df-138">Das UWP-System effektiver Pixel berücksichtigt den Betrachtungsabstand automatisch.</span><span class="sxs-lookup"><span data-stu-id="9e1df-138">UWP's effective pixel system automatically takes viewing distance in account for you.</span></span> <span data-ttu-id="9e1df-139">Wenn Sie eine Größe für ein Steuerelement oder einen Breakpointbereich angeben, verwenden Sie dabei automatisch „effektive” Pixel.</span><span class="sxs-lookup"><span data-stu-id="9e1df-139">When you specify a size for a control or a breakpoint range, you're actually using "effective" pixels.</span></span> <span data-ttu-id="9e1df-140">Wenn Sie beispielsweise einen reaktionsfähigen Code für 1080 Pixel und mehr erstellen, wird ein 1080-Monitor diesen Code verwenden, ein 1080p-Fernsehgerät jedoch nicht, denn obwohl ein 1080p-Fernsehgerät 1080 physische Pixel besitzt, hat es nur 540 effektive Pixel.</span><span class="sxs-lookup"><span data-stu-id="9e1df-140">For example, if you create responsive code for 1080 pixels and higher, a 1080 monitor will use that code, but a 1080p TV will not--because although a 1080p TV has 1080 physical pixels, it only has 540 effective pixels.</span></span> <span data-ttu-id="9e1df-141">Dadurch entspricht das Entwerfen für ein Fernsehgerät dem Entwerfen für ein Smartphone.</span><span class="sxs-lookup"><span data-stu-id="9e1df-141">Which makes designing for a TV similar to designing for a phone.</span></span>

## <a name="effective-pixels-and-scale-factor"></a><span data-ttu-id="9e1df-142">Effektive Pixel und Skalierungsfaktor</span><span class="sxs-lookup"><span data-stu-id="9e1df-142">Effective pixels and scale factor</span></span>

<span data-ttu-id="9e1df-143">UWP-Apps skalieren Ihre Benutzeroberfläche automatisch, um sicherzustellen, dass Ihre Anwendung auf allen Windows 10-Geräten lesbar ist.</span><span class="sxs-lookup"><span data-stu-id="9e1df-143">UWP apps automatically scale your UI to guarantee that your app will be legible on all Windows 10 devices.</span></span> <span data-ttu-id="9e1df-144">Windows wählt automatisch einen Skalierungsfaktor für jede Anzeige aus, basierend auf dem DPI-Wert (Punkte pro Zoll) und dem Betrachtungsabstand des Geräts.</span><span class="sxs-lookup"><span data-stu-id="9e1df-144">Windows automatically scales for each display based on its DPI (dots-per-inch) and the viewing distance of the device.</span></span> <span data-ttu-id="9e1df-145">Benutzer können den Standardwert überschreiben, indem Sie auf **Einstellungen** > **Anzeige** > **Skalierung und Layout**-Einstellungsseite wechseln.</span><span class="sxs-lookup"><span data-stu-id="9e1df-145">Users can override the default value and by going to **Settings** > **Display** > **Scale and layout** settings page.</span></span> 


## <a name="general-recommendations"></a><span data-ttu-id="9e1df-146">Allgemeine Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="9e1df-146">General recommendations</span></span>

### <a name="small"></a><span data-ttu-id="9e1df-147">Klein</span><span class="sxs-lookup"><span data-stu-id="9e1df-147">Small</span></span>
- <span data-ttu-id="9e1df-148">Legen Sie den linken und den rechten Fensterrand auf 12px fest, um eine visuelle Trennung zwischen dem linken und dem rechten Rand des App-Fensters zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="9e1df-148">Set left and right window margins to 12px to create a visual separation between the left and right edges of the app window.</span></span>
- <span data-ttu-id="9e1df-149">Docken Sie [App-Leisten](../controls-and-patterns/app-bars.md) für bessere Erreichbarkeit am unteren Fensterrand an.</span><span class="sxs-lookup"><span data-stu-id="9e1df-149">Dock [app bars](../controls-and-patterns/app-bars.md) to the bottom of the window for improved reachability.</span></span>
- <span data-ttu-id="9e1df-150">Verwenden Sie jeweils eine Spalte/Region.</span><span class="sxs-lookup"><span data-stu-id="9e1df-150">Use one column/region at a time.</span></span>
- <span data-ttu-id="9e1df-151">Verwenden Sie ein Symbol zum Darstellen der Suche (kein Suchfeld anzeigen).</span><span class="sxs-lookup"><span data-stu-id="9e1df-151">Use an icon to represent search (don't show a search box).</span></span>
- <span data-ttu-id="9e1df-152">Verwenden Sie den [Navigationsbereich](../controls-and-patterns/navigationview.md) im Überlagerungsmodus, um Platz auf dem Bildschirm zu sparen.</span><span class="sxs-lookup"><span data-stu-id="9e1df-152">Put the [navigation pane](../controls-and-patterns/navigationview.md) in overlay mode to conserve screen space.</span></span>
- <span data-ttu-id="9e1df-153">Verwenden Sie für das [Master/Details-Modell](../controls-and-patterns/master-details.md) den gestapelten Darstellungsmodus, um Platz auf dem Bildschirm zu sparen.</span><span class="sxs-lookup"><span data-stu-id="9e1df-153">If you're using the [master details pattern](../controls-and-patterns/master-details.md), use the stacked presentation mode to save screen space.</span></span>

### <a name="medium"></a><span data-ttu-id="9e1df-154">Mittel</span><span class="sxs-lookup"><span data-stu-id="9e1df-154">Medium</span></span>
- <span data-ttu-id="9e1df-155">Legen Sie den linken und den rechten Fensterrand auf 24px fest, um eine visuelle Trennung zwischen dem linken und dem rechten Rand des App-Fensters zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="9e1df-155">Set left and right window margins to 24px to create a visual separation between the left and right edges of the app window.</span></span>
- <span data-ttu-id="9e1df-156">Positionieren Sie Elemente wie [App-Leisten](../controls-and-patterns/app-bars.md) am oberen Rand des App-Fensters.</span><span class="sxs-lookup"><span data-stu-id="9e1df-156">Put command elements like [app bars](../controls-and-patterns/app-bars.md) at the top of the app window.</span></span>
- <span data-ttu-id="9e1df-157">Verwenden Sie bis zu zwei Spalten/Regionen.</span><span class="sxs-lookup"><span data-stu-id="9e1df-157">Use up to two columns/regions.</span></span>
- <span data-ttu-id="9e1df-158">Zeigen Sie das Suchfeld an.</span><span class="sxs-lookup"><span data-stu-id="9e1df-158">Show the search box.</span></span>
- <span data-ttu-id="9e1df-159">Legen Sie für [Navigationsleiste](../controls-and-patterns/navigationview.md) den Streifenmodus fest, sodass immer ein schmaler Streifen mit Symbolen angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="9e1df-159">Put the [navigation pane](../controls-and-patterns/navigationview.md) into sliver mode so a narrow strip of icons always shows.</span></span>
- <span data-ttu-id="9e1df-160">Ziehen Sie weitere Anpassungen für [TV-Umgebungen](http://go.microsoft.com/fwlink/?LinkId=760736) in Erwägung.</span><span class="sxs-lookup"><span data-stu-id="9e1df-160">Consider further tailoring for [TV experiences](http://go.microsoft.com/fwlink/?LinkId=760736).</span></span>

### <a name="large"></a><span data-ttu-id="9e1df-161">Groß</span><span class="sxs-lookup"><span data-stu-id="9e1df-161">Large</span></span>
- <span data-ttu-id="9e1df-162">Legen Sie den linken und den rechten Fensterrand auf 24px fest, um eine visuelle Trennung zwischen dem linken und dem rechten Rand des App-Fensters zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="9e1df-162">Set left and right window margins to 24px to create a visual separation between the left and right edges of the app window.</span></span>
- <span data-ttu-id="9e1df-163">Positionieren Sie Elemente wie [App-Leisten](../controls-and-patterns/app-bars.md) am oberen Rand des App-Fensters.</span><span class="sxs-lookup"><span data-stu-id="9e1df-163">Put command elements like [app bars](../controls-and-patterns/app-bars.md) at the top of the app window.</span></span>
- <span data-ttu-id="9e1df-164">Verwenden Sie bis zu drei Spalten/Regionen.</span><span class="sxs-lookup"><span data-stu-id="9e1df-164">Use up to three columns/regions.</span></span>
- <span data-ttu-id="9e1df-165">Zeigen Sie das Suchfeld an.</span><span class="sxs-lookup"><span data-stu-id="9e1df-165">Show the search box.</span></span>
- <span data-ttu-id="9e1df-166">Platzieren Sie den [Navigationsbereich](../controls-and-patterns/navigationview.md) im angedockten Modus so, dass er immer angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="9e1df-166">Put the [navigation pane](../controls-and-patterns/navigationview.md) into docked mode so that it always shows.</span></span>

>[!TIP] 
> <span data-ttu-id="9e1df-167">Mit [**Continuum für Smartphones**](http://go.microsoft.com/fwlink/p/?LinkID=699431)können Benutzer kompatible Windows 10 mobile-Geräte mit Monitor, Maus und Tastatur auf ihren Smartphones wie Laptops arbeiten verbinden.</span><span class="sxs-lookup"><span data-stu-id="9e1df-167">With [**Continuum for Phones**](http://go.microsoft.com/fwlink/p/?LinkID=699431), users can connect compatible Windows10 mobile devices to a monitor, mouse and keyboard to make their phones work like laptops.</span></span> <span data-ttu-id="9e1df-168">Berücksichtigen Sie diese neue Funktion beim Entwerfen für bestimmte Breakpoints – ein Mobiltelefon bleibt nicht immer in einer Klasse mit geringer Größe.</span><span class="sxs-lookup"><span data-stu-id="9e1df-168">Keep this new capability in mind when designing for specific breakpoints - a mobile phone will not always stay in the size class.</span></span>


