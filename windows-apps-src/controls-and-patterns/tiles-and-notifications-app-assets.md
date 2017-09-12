---
author: mijacobs
Description: "Ressourcen für App-Symbole, die in einer Vielzahl von Formen innerhalb des Windows 10-Betriebssystems vorkommen, sind die Aushängeschilder für Ihre App für die Universelle Windows-Plattform (UWP)."
title: "Ressourcen für Kacheln und Symbole"
ms.assetid: D6CE21E5-2CFA-404F-8679-36AA522206C7
label: Tile and icon assets
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.openlocfilehash: 54ad78d5799a96ddcec7b060704ee198e0bf8db5
ms.sourcegitcommit: 9a1310468970c8d1ade0fb200126dff56ea8c9e1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/14/2017
---
# <a name="guidelines-for-tile-and-icon-assets"></a><span data-ttu-id="b4ebd-104">Richtlinien für die Ressourcen für Kacheln und Symbole</span><span class="sxs-lookup"><span data-stu-id="b4ebd-104">Guidelines for tile and icon assets</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css"> 


<span data-ttu-id="b4ebd-105">Ressourcen für App-Symbole, die in einer Vielzahl von Formen innerhalb des Windows 10-Betriebssystems vorkommen, sind die Aushängeschilder für Ihre App für die Universelle Windows-Plattform (UWP).</span><span class="sxs-lookup"><span data-stu-id="b4ebd-105">App icon assets, which appear in a variety of forms throughout the Windows 10 operating system, are the calling cards for your Universal Windows Platform (UWP) app.</span></span> <span data-ttu-id="b4ebd-106">In diesen Richtlinien wird beschrieben, wo Ressourcen für App-Symbole im System angezeigt werden, und Sie erhalten ausführliche Designtipps zum Erstellen ansprechender Symbole.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-106">These guidelines detail where app icon assets appear in the system, and provide in-depth design tips on how to create the most polished icons.</span></span>

![Starten von Windows10 und Kacheln](images/assetguidance01.jpg)

## <a name="adaptive-scaling"></a><span data-ttu-id="b4ebd-108">Adaptive Skalierung</span><span class="sxs-lookup"><span data-stu-id="b4ebd-108">Adaptive scaling</span></span>


<span data-ttu-id="b4ebd-109">Zunächst erhalten Sie einen kurzen Überblick über die adaptive Skalierung, um die Funktion der Skalierung mit Ressourcen verstehen zu können.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-109">First, a brief overview on adaptive scaling to better understand how scaling works with assets.</span></span> <span data-ttu-id="b4ebd-110">Mit Windows10 wird eine Weiterentwicklung des vorhandenen Skalierungsmodells eingeführt.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-110">Windows 10 introduces an evolution of the existing scaling model.</span></span> <span data-ttu-id="b4ebd-111">Neben der Skalierung von Vektorinhalten gibt es einen einheitlichen Satz von Skalierungsfaktoren, der eine einheitliche Größe für UI-Elemente für eine Vielzahl von Bildschirmgrößen und -auflösungen bietet.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-111">In addition to scaling vector content, there is a unified set of scale factors that provides a consistent size for UI elements across a variety of screen sizes and display resolutions.</span></span> <span data-ttu-id="b4ebd-112">Die Skalierungsfaktoren sind auch mit den Skalierungsfaktoren anderer Betriebssysteme wie iOS und Android kompatibel, sodass die Ressourcen einfacher für alle diese Plattformen verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-112">The scale factors are also compatible with the scale factors of other operating systems such as iOS and Android, which makes it easier to share assets between these platforms.</span></span>

<span data-ttu-id="b4ebd-113">Die Auswahl der aus dem Store herunterzuladenden Ressourcen erfolgt zum Teil auf Grundlage des DPI-Werts eines Geräts.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-113">The Store picks the assets to download based in part of the DPI of the device.</span></span> <span data-ttu-id="b4ebd-114">Nur die Ressourcen, die dem Gerät am besten entsprechen, werden heruntergeladen.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-114">Only the assets that best match the device are downloaded.</span></span>

## <a name="tile-elements"></a><span data-ttu-id="b4ebd-115">Kachelelemente</span><span class="sxs-lookup"><span data-stu-id="b4ebd-115">Tile elements</span></span>


<span data-ttu-id="b4ebd-116">Die grundlegenden Komponenten einer Startkachel sind eine Rückwand, ein Symbol, eine Brandingleiste, Ränder und ein App-title:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-116">The basic components of a Start tile consist of a back plate, an icon, a branding bar, margins, and an app title:</span></span>

![Aufschlüsselung der Kachelelemente](images/assetguidance02.png)

<span data-ttu-id="b4ebd-118">Auf der Brandingleiste am unteren Rand einer Kachel werden der App-Name, die Signalgebung und der Zähler (falls verwendet) angezeigt:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-118">The branding bar at the bottom of a tile is where the app name, badging, and counter (if used) appear:</span></span>

![Brandingleiste in der Kachel](images/assetguidance03.png)

<span data-ttu-id="b4ebd-120">Die Höhe der Brandingleiste basiert auf dem Skalierungsfaktor des Geräts, auf dem sie angezeigt wird:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-120">The height of the branding bar is based on the scale factor of the device on which it appears:</span></span>

| <span data-ttu-id="b4ebd-121">Skalierungsfaktor</span><span class="sxs-lookup"><span data-stu-id="b4ebd-121">Scale factor</span></span> | <span data-ttu-id="b4ebd-122">Pixel</span><span class="sxs-lookup"><span data-stu-id="b4ebd-122">Pixels</span></span> |
|--------------|--------|
| <span data-ttu-id="b4ebd-123">100%</span><span class="sxs-lookup"><span data-stu-id="b4ebd-123">100%</span></span>         | <span data-ttu-id="b4ebd-124">32</span><span class="sxs-lookup"><span data-stu-id="b4ebd-124">32</span></span>     |
| <span data-ttu-id="b4ebd-125">125%</span><span class="sxs-lookup"><span data-stu-id="b4ebd-125">125%</span></span>         | <span data-ttu-id="b4ebd-126">40</span><span class="sxs-lookup"><span data-stu-id="b4ebd-126">40</span></span>     |
| <span data-ttu-id="b4ebd-127">150%</span><span class="sxs-lookup"><span data-stu-id="b4ebd-127">150%</span></span>         | <span data-ttu-id="b4ebd-128">48</span><span class="sxs-lookup"><span data-stu-id="b4ebd-128">48</span></span>     |
| <span data-ttu-id="b4ebd-129">200%</span><span class="sxs-lookup"><span data-stu-id="b4ebd-129">200%</span></span>         | <span data-ttu-id="b4ebd-130">64</span><span class="sxs-lookup"><span data-stu-id="b4ebd-130">64</span></span>     |
| <span data-ttu-id="b4ebd-131">400%</span><span class="sxs-lookup"><span data-stu-id="b4ebd-131">400%</span></span>         | <span data-ttu-id="b4ebd-132">128</span><span class="sxs-lookup"><span data-stu-id="b4ebd-132">128</span></span>    |

 

<span data-ttu-id="b4ebd-133">Die Ränder der Kachel werden vom System festgelegt und können nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-133">The system sets tile margins and cannot be modified.</span></span> <span data-ttu-id="b4ebd-134">Die meisten Inhalte werden innerhalb der Ränder angezeigt, wie in diesem Beispiel:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-134">Most content appears inside the margins, as seen in this example:</span></span>

![Kachelfassaden](images/assetguidance04.png)

<span data-ttu-id="b4ebd-136">Die Randbreite basiert auf dem Skalierungsfaktor des Geräts, auf dem sie angezeigt wird:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-136">Margin width is based on the scale factor of the device on which it appears:</span></span>

| <span data-ttu-id="b4ebd-137">Skalierungsfaktor</span><span class="sxs-lookup"><span data-stu-id="b4ebd-137">Scale factor</span></span> | <span data-ttu-id="b4ebd-138">Pixel</span><span class="sxs-lookup"><span data-stu-id="b4ebd-138">Pixels</span></span> |
|--------------|--------|
| <span data-ttu-id="b4ebd-139">100%</span><span class="sxs-lookup"><span data-stu-id="b4ebd-139">100%</span></span>         | <span data-ttu-id="b4ebd-140">8</span><span class="sxs-lookup"><span data-stu-id="b4ebd-140">8</span></span>      |
| <span data-ttu-id="b4ebd-141">125%</span><span class="sxs-lookup"><span data-stu-id="b4ebd-141">125%</span></span>         | <span data-ttu-id="b4ebd-142">10</span><span class="sxs-lookup"><span data-stu-id="b4ebd-142">10</span></span>     |
| <span data-ttu-id="b4ebd-143">150%</span><span class="sxs-lookup"><span data-stu-id="b4ebd-143">150%</span></span>         | <span data-ttu-id="b4ebd-144">12</span><span class="sxs-lookup"><span data-stu-id="b4ebd-144">12</span></span>     |
| <span data-ttu-id="b4ebd-145">200%</span><span class="sxs-lookup"><span data-stu-id="b4ebd-145">200%</span></span>         | <span data-ttu-id="b4ebd-146">16</span><span class="sxs-lookup"><span data-stu-id="b4ebd-146">16</span></span>     |
| <span data-ttu-id="b4ebd-147">400%</span><span class="sxs-lookup"><span data-stu-id="b4ebd-147">400%</span></span>         | <span data-ttu-id="b4ebd-148">32</span><span class="sxs-lookup"><span data-stu-id="b4ebd-148">32</span></span>     |

 

## <a name="tile-assets"></a><span data-ttu-id="b4ebd-149">Kachelressourcen</span><span class="sxs-lookup"><span data-stu-id="b4ebd-149">Tile assets</span></span>


<span data-ttu-id="b4ebd-150">Jede Kachelressource hat die gleiche Größe wie die Kachel, auf der sie sich befindet.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-150">Each tile asset is the same size as the tile on which it is placed.</span></span> <span data-ttu-id="b4ebd-151">Sie können die App-Kacheln mit zwei unterschiedlichen Darstellungsformen einer Ressource kennzeichnen:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-151">You can brand your app's tiles with two different representations of an asset:</span></span>

1. <span data-ttu-id="b4ebd-152">Ein zentriertes Symbol oder Logo mit Abstand.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-152">An icon or logo centered with padding.</span></span> <span data-ttu-id="b4ebd-153">Auf diese Weise scheint die Farbe der Rückwand durch:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-153">This lets the back plate color show through:</span></span>

![Kachel und Rückwand](images/assetguidance05.png)

2. <span data-ttu-id="b4ebd-155">Eine randlose Brandingkachel ohne Abstand:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-155">A full-bleed, branded tile without padding:</span></span>

![Randlose Kachel](images/assetguidance06.png)

<span data-ttu-id="b4ebd-157">Zum Zweck der Einheitlichkeit auf allen Geräten hat jede Kachelgröße (klein, mittel, breit und groß) eine eigene Größenbeziehung.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-157">For consistency across devices, each tile size (small, medium, wide, and large) has its own sizing relationship.</span></span> <span data-ttu-id="b4ebd-158">Um eine einheitliche Symbolanordnung auf allen Kacheln zu erreichen, empfehlen wir einige grundlegende Abstandsrichtlinien für die folgenden Kachelgrößen.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-158">In order to achieve a consistent icon placement across tiles, we recommend a few basic padding guidelines for the following tile sizes.</span></span> <span data-ttu-id="b4ebd-159">Der Bereich, in dem zwei violette Überlagerungen schneiden, ist die ideale Fläche für ein Symbol.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-159">The area where the two purple overlays intersect represents the ideal footprint for an icon.</span></span> <span data-ttu-id="b4ebd-160">Symbole passen zwar nicht immer genau in die Fläche, das visuelle Volumen eines Symbols sollte aber ungefähr den dargestellten Beispielen entsprechen.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-160">Although icons won't always fit inside the footprint, the visual volume of an icon should be roughly equivalent to the provided examples.</span></span>

<span data-ttu-id="b4ebd-161">Kleine Kachelgröße:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-161">Small tile sizing:</span></span>

![Beispiel für kleine Kachelgröße](images/assetguidance07a.png)

<span data-ttu-id="b4ebd-163">Mittlere Kachelgröße:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-163">Medium tile sizing:</span></span>

![Beispiel für mittlere Kachelgröße](images/assetguidance07b.png)

<span data-ttu-id="b4ebd-165">Breite Kachelgröße:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-165">Wide tile sizing:</span></span>

![Beispiel für breite Kachelgröße](images/assetguidance07c.png)

<span data-ttu-id="b4ebd-167">Große Kachelgröße:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-167">Large tile sizing:</span></span>

![Beispiel für große Kachelgröße](images/assetguidance07d.png)

<span data-ttu-id="b4ebd-169">In diesem Beispiel ist das Symbol für die Kachel zu groß:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-169">In this example, the icon is too large for the tile:</span></span>

![Symbol zu groß für die Kachel](images/assetguidance08a.png)

<span data-ttu-id="b4ebd-171">In diesem Beispiel ist das Symbol für die Kachel zu klein:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-171">In this example, the icon is too small for the tile:</span></span>

![Symbol zu klein für die Kachel](images/assetguidance08b.png)

<span data-ttu-id="b4ebd-173">Die folgenden Abstandsverhältnisse sind optimal für horizontal oder vertikal ausgerichtete Symbole.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-173">The following padding ratios are optimal for horizontally or vertically oriented icons.</span></span>

<span data-ttu-id="b4ebd-174">Beschränken Sie bei kleinen Kacheln die Breite und Höhe auf 66% der Kachelgröße:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-174">For small tiles, limit the icon width and height to 66% of the tile size:</span></span>

![Verhältnisse bei kleinen Kachelgrößen](images/assetguidance09.png)

<span data-ttu-id="b4ebd-176">Beschränken Sie bei mittelgroßen Kacheln die Symbolbreite auf 66% und die Höhe auf 50% der Kachelgröße.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-176">For medium tiles, limit the icon width to 66% and height to 50% of tile size.</span></span> <span data-ttu-id="b4ebd-177">Dadurch wird verhindert, dass Elemente in der Brandingleiste überlappen:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-177">This prevents overlapping of elements in the branding bar:</span></span>

![Verhältnisse bei mittelgroßen Kacheln](images/assetguidance10.png)

<span data-ttu-id="b4ebd-179">Beschränken Sie bei breiten Kacheln die Symbolbreite auf 66% und die Höhe auf 50% der Kachelgröße.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-179">For wide tiles, limit the icon width to 66% and height to 50% of tile size.</span></span> <span data-ttu-id="b4ebd-180">Dadurch wird verhindert, dass Elemente in der Brandingleiste überlappen:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-180">This prevents overlapping of elements in the branding bar:</span></span>

![Verhältnisse bei breiten Kacheln](images/assetguidance11.png)

<span data-ttu-id="b4ebd-182">Beschränken Sie bei großen Kacheln die Symbolbreite auf 66% und die Höhe auf 50% der Kachelgröße:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-182">For large tiles, limit the icon width to 66% and height to 50% of tile size:</span></span>

![Verhältnisse bei großen Kacheln](images/assetguidance12.png)

<span data-ttu-id="b4ebd-184">Einige Symbole sind so konzipiert, dass sie horizontal oder vertikal ausgerichtet sind, andere Symbole hingegen weisen komplexere Formen auf, wodurch verhindert wird, dass sie direkt in die Zielabmessungen passen.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-184">Some icons are designed to be horizontally or vertically oriented, while others have more complex shapes that prevent them from fitting squarely within the target dimensions.</span></span> <span data-ttu-id="b4ebd-185">Symbole, die zentriert erscheinen, können auf eine Seite geneigt sein.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-185">Icons that appear to be centered can be weighted to one side.</span></span> <span data-ttu-id="b4ebd-186">In diesem Fall können Teile eines Symbols aus der empfohlenen Fläche heraushängen, vorausgesetzt, das Symbol belegt dasselbe visuelle Gewicht wie ein genau passendes Symbol:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-186">In this case, parts of an icon may hang outside the recommended footprint, provided it occupies the same visual weight as a squarely fitted icon:</span></span>

![Drei zentrierte Symbole](images/assetguidance13.png)

<span data-ttu-id="b4ebd-188">Berücksichtigen Sie bei randlosen Ressourcen Elemente, die innerhalb der Ränder und Kanten der Kacheln interagieren.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-188">With full-bleed assets, take into account elements that interact within the margins and edges of the tiles.</span></span> <span data-ttu-id="b4ebd-189">Behalten Sie Ränder von mindestens 16 % der Höhe oder Breite der Kachel bei.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-189">Maintain margins of at least 16% of the height or width of the tile.</span></span> <span data-ttu-id="b4ebd-190">Dieser Prozentsatz stellt die doppelte Breite der Ränder bei den kleinsten Kachelgrößen dar:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-190">This percentage represents double the width of the margins at the smallest tile sizes:</span></span>

![Randlose Kachel mit Rändern](images/assetguidance14.png)

<span data-ttu-id="b4ebd-192">In diesem Beispiel sind die Ränder zu eng:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-192">In this example, margins are too tight:</span></span>

![Randlose Kachel mit zu engen Rändern](images/assetguidance15.png)

## <a name="tile-assets-in-list-views"></a><span data-ttu-id="b4ebd-194">Kachelressourcen in Listenansichten</span><span class="sxs-lookup"><span data-stu-id="b4ebd-194">Tile assets in list views</span></span>


<span data-ttu-id="b4ebd-195">Kacheln können auch in einer Listenansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-195">Tiles can also appear in a list view.</span></span> <span data-ttu-id="b4ebd-196">Größenrichtlinien für Kachelressourcen, die in Listenansichten angezeigt werden, unterscheiden sich leicht von den zuvor aufgeführten Kachelressourcen.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-196">Sizing guidelines for tile assets that appear in list views are a bit different than tile assets previously outlined.</span></span> <span data-ttu-id="b4ebd-197">In diesem Abschnitt werden diese Einzelheiten bei der Größe erläutert.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-197">This section details those sizing specifics.</span></span>

![Kachelressourcen in einer Listenansicht](images/assetguidance16.png)

<span data-ttu-id="b4ebd-199">Beschränken Sie die Breite und Höhe von Symbolen auf 75% der Kachelgröße:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-199">Limit icon width and height to 75% of the tile size:</span></span>

![Größe eines Symbols einer Listenansichtkachel](images/assetguidance17.png)

<span data-ttu-id="b4ebd-201">Beschränken Sie bei vertikalen und horizontalen Symbolformaten die Breite und Höhe auf 75% der Kachelgröße:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-201">For vertical and horizontal icon formats, limit width and height to 75% of the tile size:</span></span>

![Größe eines Symbols einer Listenansichtkachel](images/assetguidance18.png)

<span data-ttu-id="b4ebd-203">Behalten Sie bei randlosen Grafiken wichtiger Brandingelemente Ränder von 12,5% bei:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-203">For full bleed artwork of important brand elements, maintain margins of at least 12.5%:</span></span>

![Randlose Grafiken in Listenansichtkachel](images/assetguidance19.png)

<span data-ttu-id="b4ebd-205">In diesem Beispiel ist das Symbol in der Kachel zu groß:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-205">In this example, the icon is too big inside its tile:</span></span>

![Symbol für die Kachel zu groß](images/assetguidance20a.png)

<span data-ttu-id="b4ebd-207">In diesem Beispiel ist das Symbol in der Kachel zu klein:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-207">In this example, the icon is too small inside its tile:</span></span>

![Symbol für die Kachel zu klein](images/assetguidance20b.png)

## <a name="target-based-assets"></a><span data-ttu-id="b4ebd-209">Zielbasierte Ressourcen</span><span class="sxs-lookup"><span data-stu-id="b4ebd-209">Target-based assets</span></span>


<span data-ttu-id="b4ebd-210">Zielbasierte Ressourcen gelten für Symbole und Kacheln, die in der Windows-Taskleiste, in der Aufgabenansicht, über ALT+TAB, in der Andockhilfe und in der unteren rechten Ecke von Startkacheln angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-210">Target-based assets are for icons and tiles that appear on the Windows taskbar, task view, ALT+TAB, snap-assist, and the lower-right corner of Start tiles.</span></span> <span data-ttu-id="b4ebd-211">Sie müssen für diese Ressourcen keine Abstände hinzufügen, diese werden bei Bedarf von Windows hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-211">You don't have to add padding to these assets; Windows adds padding if needed.</span></span> <span data-ttu-id="b4ebd-212">Bei diesen Ressourcen sollte eine minimale Fläche von 16Pixeln vorgesehen werden.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-212">These assets should account for a minimum footprint of 16 pixels.</span></span> <span data-ttu-id="b4ebd-213">Unten sehen Sie ein Beispiel dafür, wie diese Ressourcen als Symbole in der Windows-Taskleiste angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-213">Here's an example of these assets as they appear in icons on the Windows taskbar:</span></span>

![Ressourcen in Windows-Taskleiste](images/assetguidance21.png)

<span data-ttu-id="b4ebd-215">Diese Benutzeroberfläche verwendet zwar neben einer farbigen Rückwand standardmäßig eine zielbasierte Ressource, Sie können aber auch eine zielbasierte Ressource ohne Anpassung verwenden.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-215">Although these UI will use a target-based asset on top of a colored backplate by default, you may use a target-based unplated asset as well.</span></span> <span data-ttu-id="b4ebd-216">Ressourcen ohne Anpassung sollten so erstellt werden, dass es möglich ist, sie in unterschiedlichen Hintergrundfarben anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-216">Unplated assets should be created with the possibility that they may appear on various background colors:</span></span>

![Ressourcen mit und ohne Anpassung](images/assetguidance22.png)

<span data-ttu-id="b4ebd-218">Nachfolgend finden Sie die Größenempfehlungen für zielbasierte Ressourcen mit einer Skalierung von 100%:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-218">These are size recommendations for target-based assets, at 100% scale:</span></span>

![Zielbasierte Ressourcengröße bei einer Skalierung von 100%](images/assetguidance23.png)

## <a name="splash-screen-assets"></a><span data-ttu-id="b4ebd-220">Ressourcen für den Begrüßungsbildschirm</span><span class="sxs-lookup"><span data-stu-id="b4ebd-220">Splash screen assets</span></span>


<span data-ttu-id="b4ebd-221">Das Bild für den Begrüßungsbildschirm kann als direkter Pfad zu einer Bilddatei oder als Ressource angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-221">The splash screen image can be given either as a direct path to an image file or as a resource.</span></span> <span data-ttu-id="b4ebd-222">Mithilfe eines Ressourcenverweises können Sie Bilder mit verschiedenen Skalierungen bereitstellen, damit Windows die optimale Größe für das jeweilige Gerät und die Bildschirmauflösung auswählen kann.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-222">By using a resource reference, you can supply images of different scales so that Windows can choose the best size for the device and screen resolution.</span></span> <span data-ttu-id="b4ebd-223">Sie können auch Bilder mit hohem Kontrast für die Barrierefreiheit sowie lokalisierte Bilder für verschiedene Benutzeroberflächensprachen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-223">You can also supply high contrast images for accessibility and localized images to match different UI languages.</span></span>

<span data-ttu-id="b4ebd-224">Wenn Sie „Package.appxmanifest“ in einem Text-Editor öffnen, wird das [**SplashScreen**](https://msdn.microsoft.com/library/windows/apps/br211467)-Element als untergeordnetes Element des [**VisualElements**](https://msdn.microsoft.com/library/windows/apps/br211471)-Elements angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-224">If you open "Package.appxmanifest" in a text editor, the [**SplashScreen**](https://msdn.microsoft.com/library/windows/apps/br211467) element appears as a child of the [**VisualElements**](https://msdn.microsoft.com/library/windows/apps/br211471) element.</span></span> <span data-ttu-id="b4ebd-225">Das standardmäßige Begrüßungsbildschirm-Markup in der Manifestdatei sieht in einem Text-Editor wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-225">The default splash screen markup in the manifest file looks like this in a text editor:</span></span>

```XML
<uap:SplashScreen Image="Assets\SplashScreen.png" /></code></pre></td>
</tr>
</tbody>
</table>
```

<span data-ttu-id="b4ebd-226">Die Ressource für den Begrüßungsbildschirm wird von jedem Gerät zentriert, auf dem er angezeigt wird:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-226">The splash screen asset is centered by whichever device it appears on:</span></span>

![Größe der Ressource für den Begrüßungsbildschirm](images/assetguidance27.png)

## <a name="high-contrast-assets"></a><span data-ttu-id="b4ebd-228">Ressourcen mit hohem Kontrast</span><span class="sxs-lookup"><span data-stu-id="b4ebd-228">High-contrast assets</span></span>


<span data-ttu-id="b4ebd-229">Der Modus mit hohem Kontrast verwendet separate Sätze von Ressourcen für kontrastreiches Weiß (weißer Hintergrund mit schwarzem Text) und kontrastreiches Schwarz (schwarzer Hintergrund mit weißem Text).</span><span class="sxs-lookup"><span data-stu-id="b4ebd-229">High-contrast mode makes use of separate sets of assets for high-contrast white (white background with black text) and high-contrast black (black background with white text).</span></span> <span data-ttu-id="b4ebd-230">Wenn Sie keine Ressourcen mit hohem Kontrast für Ihre App angeben, werden die Standardressourcen verwendet.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-230">If you don't provide high-contrast assets for your app, standard assets will be used.</span></span>

<span data-ttu-id="b4ebd-231">Wenn die Standardressourcen für Ihre App eine akzeptable Anzeigeumgebung bei einem schwarzweißen Hintergrund bieten, sollte Ihre App im Modus mit hohem Kontrast zumindest zufriedenstellend aussehen.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-231">If your app's standard assets provide an acceptable viewing experience when rendered on a black-and-white background, then your app should look at least satisfactory in high-contrast mode.</span></span> <span data-ttu-id="b4ebd-232">Wenn Ihre die Standardressourcen keine akzeptable Anzeigeumgebung bei einem schwarzweißen Hintergrund liefern, sollten Sie in Betracht ziehen, Ressourcen mit hohem Kontrast zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-232">If your standard assets don't afford an acceptable viewing experience when rendered on a black-and-white background, consider specifically including high-contrast assets.</span></span> <span data-ttu-id="b4ebd-233">Die folgenden Beispiele zeigen die zwei Arten von Ressourcen mit hohem Kontrast:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-233">These examples illustrate the two types of high-contrast assets:</span></span>

![Beispiele für hohes Kontrastverhältnis](images/assetguidance28.png)

<span data-ttu-id="b4ebd-235">Wenn Sie Ressourcen mit hohem Kontrast bereitstellen möchten, müssen Sie beide Sätze – weiß auf schwarz und schwarz auf weiß – verwenden.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-235">If you decide to provide high-contrast assets, you need to include both sets—both white-on-black and black-on-white.</span></span> <span data-ttu-id="b4ebd-236">Wenn Sie diese Ressourcen in Ihr Paket aufnehmen, können Sie einen Ordner "Kontrast Schwarz" für weiß auf schwarz, und einen Ordner "Kontrast Weiß" für schwarz auf weiß erstellen.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-236">When including these assets in your package, you could create a "contrast-black" folder for white-on-black assets, and a "contrast-white" folder for black-on-white assets.</span></span>

## <a name="asset-size-tables"></a><span data-ttu-id="b4ebd-237">Größentabellen</span><span class="sxs-lookup"><span data-stu-id="b4ebd-237">Asset size tables</span></span>


<span data-ttu-id="b4ebd-238">Es wird dringend empfohlen, dass Sie mindestens Ressourcen für die Skalierungsfaktoren 100, 200 und 400 Skalierungsfaktoren bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-238">At a bare minimum, we strongly recommend that you provide assets for the 100, 200, and 400 scale factors.</span></span> <span data-ttu-id="b4ebd-239">Wenn Sie Ressourcen für alle Skalierungsfaktoren bereitstellen, liefert dies eine optimale Benutzererfahrung.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-239">Providing assets for all scale factors will provide the optimal user experience.</span></span>

<br/>

<table>
<thead>
<tr><th colspan="3"><span data-ttu-id="b4ebd-240">Kleine Kachel (Square71x71Logo)</span><span class="sxs-lookup"><span data-stu-id="b4ebd-240">Small tile (Square71x71Logo)</span></span></th></tr>
</thead>
<tbody>
<tr>
    <td width="20%"><span data-ttu-id="b4ebd-241">Skalierung von 100 %</span><span class="sxs-lookup"><span data-stu-id="b4ebd-241">100% scale</span></span></td>
    <td width="20%"><span data-ttu-id="b4ebd-242">71 x 71</span><span class="sxs-lookup"><span data-stu-id="b4ebd-242">71x71</span></span></td>
    <td><span data-ttu-id="b4ebd-243">Square71x71Logo.scale-100.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-243">Square71x71Logo.scale-100.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="b4ebd-244">Skalierung von 125 %</span><span class="sxs-lookup"><span data-stu-id="b4ebd-244">125% scale</span></span></td>
    <td><span data-ttu-id="b4ebd-245">89 x 89</span><span class="sxs-lookup"><span data-stu-id="b4ebd-245">89x89</span></span></td>
    <td><span data-ttu-id="b4ebd-246">Square71x71Logo.scale-125.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-246">Square71x71Logo.scale-125.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="b4ebd-247">Skalierung von 150 %</span><span class="sxs-lookup"><span data-stu-id="b4ebd-247">150% scale</span></span></td>
    <td><span data-ttu-id="b4ebd-248">107 x 107</span><span class="sxs-lookup"><span data-stu-id="b4ebd-248">107x107</span></span></td>
    <td><span data-ttu-id="b4ebd-249">Square71x71Logo.scale-150.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-249">Square71x71Logo.scale-150.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="b4ebd-250">Skalierung von 200 %</span><span class="sxs-lookup"><span data-stu-id="b4ebd-250">200% scale</span></span></td>
    <td><span data-ttu-id="b4ebd-251">142 x 142</span><span class="sxs-lookup"><span data-stu-id="b4ebd-251">142x142</span></span></td>
    <td><span data-ttu-id="b4ebd-252">Square71x71Logo.scale-200.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-252">Square71x71Logo.scale-200.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="b4ebd-253">Skalierung von 400 %</span><span class="sxs-lookup"><span data-stu-id="b4ebd-253">400% scale</span></span></td>
    <td><span data-ttu-id="b4ebd-254">284x284</span><span class="sxs-lookup"><span data-stu-id="b4ebd-254">284x284</span></span></td>
    <td><span data-ttu-id="b4ebd-255">Square71x71Logo.scale-400.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-255">Square71x71Logo.scale-400.png</span></span></td>
</tr>
</tbody>
</table>

<br/>

<table>
<thead>
<tr><th colspan="3"><span data-ttu-id="b4ebd-256">Mittelgroße Kachel (Square150x150Logo)</span><span class="sxs-lookup"><span data-stu-id="b4ebd-256">Medium tile (Square150x150Logo)</span></span></th></tr>
</thead>
<tbody>
<tr>
    <td width="20%"><span data-ttu-id="b4ebd-257">Skalierung von 100 %</span><span class="sxs-lookup"><span data-stu-id="b4ebd-257">100% scale</span></span></td>
    <td width="20%"><span data-ttu-id="b4ebd-258">150x150</span><span class="sxs-lookup"><span data-stu-id="b4ebd-258">150x150</span></span></td>
    <td><span data-ttu-id="b4ebd-259">Square150x150Logo.scale-100.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-259">Square150x150Logo.scale-100.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="b4ebd-260">Skalierung von 125 %</span><span class="sxs-lookup"><span data-stu-id="b4ebd-260">125% scale</span></span></td>
    <td><span data-ttu-id="b4ebd-261">188 x 188</span><span class="sxs-lookup"><span data-stu-id="b4ebd-261">188x188</span></span></td>
    <td><span data-ttu-id="b4ebd-262">Square150x150Logo.scale-125.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-262">Square150x150Logo.scale-125.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="b4ebd-263">Skalierung von 150 %</span><span class="sxs-lookup"><span data-stu-id="b4ebd-263">150% scale</span></span></td>
    <td><span data-ttu-id="b4ebd-264">225 x 225</span><span class="sxs-lookup"><span data-stu-id="b4ebd-264">225x225</span></span></td>
    <td><span data-ttu-id="b4ebd-265">Square150x150Logo.scale-150.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-265">Square150x150Logo.scale-150.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="b4ebd-266">Skalierung von 200 %</span><span class="sxs-lookup"><span data-stu-id="b4ebd-266">200% scale</span></span></td>
    <td><span data-ttu-id="b4ebd-267">300 x 300</span><span class="sxs-lookup"><span data-stu-id="b4ebd-267">300x300</span></span></td>
    <td><span data-ttu-id="b4ebd-268">Square150x150Logo.scale-200.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-268">Square150x150Logo.scale-200.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="b4ebd-269">Skalierung von 400 %</span><span class="sxs-lookup"><span data-stu-id="b4ebd-269">400% scale</span></span></td>
    <td><span data-ttu-id="b4ebd-270">600 x 600</span><span class="sxs-lookup"><span data-stu-id="b4ebd-270">600x600</span></span></td>
    <td><span data-ttu-id="b4ebd-271">Square150x150Logo.scale-400.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-271">Square150x150Logo.scale-400.png</span></span></td>
</tr>
</tbody>
</table>

<br/>

<table>
<thead>
<tr><th colspan="3"><span data-ttu-id="b4ebd-272">Breite Kachel (Wide310x150Logo)</span><span class="sxs-lookup"><span data-stu-id="b4ebd-272">Wide tile (Wide310x150Logo)</span></span></th></tr>
</thead>
<tbody>
<tr>
    <td width="20%"><span data-ttu-id="b4ebd-273">Skalierung von 100 %</span><span class="sxs-lookup"><span data-stu-id="b4ebd-273">100% scale</span></span></td>
    <td width="20%"><span data-ttu-id="b4ebd-274">310x150</span><span class="sxs-lookup"><span data-stu-id="b4ebd-274">310x150</span></span></td>
    <td><span data-ttu-id="b4ebd-275">Wide310x150Logo.scale-100.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-275">Wide310x150Logo.scale-100.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="b4ebd-276">Skalierung von 125 %</span><span class="sxs-lookup"><span data-stu-id="b4ebd-276">125% scale</span></span></td>
    <td><span data-ttu-id="b4ebd-277">388 x 188</span><span class="sxs-lookup"><span data-stu-id="b4ebd-277">388x188</span></span></td>
    <td><span data-ttu-id="b4ebd-278">Wide310x150Logo.scale-125.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-278">Wide310x150Logo.scale-125.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="b4ebd-279">Skalierung von 150 %</span><span class="sxs-lookup"><span data-stu-id="b4ebd-279">150% scale</span></span></td>
    <td><span data-ttu-id="b4ebd-280">465 x 225</span><span class="sxs-lookup"><span data-stu-id="b4ebd-280">465x225</span></span></td>
    <td><span data-ttu-id="b4ebd-281">Wide310x150Logo.scale-150.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-281">Wide310x150Logo.scale-150.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="b4ebd-282">Skalierung von 200 %</span><span class="sxs-lookup"><span data-stu-id="b4ebd-282">200% scale</span></span></td>
    <td><span data-ttu-id="b4ebd-283">620 x 300</span><span class="sxs-lookup"><span data-stu-id="b4ebd-283">620x300</span></span></td>
    <td><span data-ttu-id="b4ebd-284">Wide310x150Logo.scale-200.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-284">Wide310x150Logo.scale-200.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="b4ebd-285">Skalierung von 400 %</span><span class="sxs-lookup"><span data-stu-id="b4ebd-285">400% scale</span></span></td>
    <td><span data-ttu-id="b4ebd-286">1240 x 600</span><span class="sxs-lookup"><span data-stu-id="b4ebd-286">1240x600</span></span></td>
    <td><span data-ttu-id="b4ebd-287">Wide310x150Logo.scale-400.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-287">Wide310x150Logo.scale-400.png</span></span></td>
</tr>
</tbody>
</table>

<br/>

<table>
<thead>
<tr><th colspan="3"><span data-ttu-id="b4ebd-288">Große Kachel (Square310x310Logo)</span><span class="sxs-lookup"><span data-stu-id="b4ebd-288">Large tile (Square310x310Logo)</span></span></th></tr>
</thead>
<tbody>
<tr>
    <td width="20%"><span data-ttu-id="b4ebd-289">Skalierung von 100 %</span><span class="sxs-lookup"><span data-stu-id="b4ebd-289">100% scale</span></span></td>
    <td width="20%"><span data-ttu-id="b4ebd-290">310x310</span><span class="sxs-lookup"><span data-stu-id="b4ebd-290">310x310</span></span></td>
    <td><span data-ttu-id="b4ebd-291">Square310x310Logo.scale-100.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-291">Square310x310Logo.scale-100.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="b4ebd-292">Skalierung von 125 %</span><span class="sxs-lookup"><span data-stu-id="b4ebd-292">125% scale</span></span></td>
    <td><span data-ttu-id="b4ebd-293">388 x 388</span><span class="sxs-lookup"><span data-stu-id="b4ebd-293">388x388</span></span></td>
    <td><span data-ttu-id="b4ebd-294">Square310x310Logo.scale-125.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-294">Square310x310Logo.scale-125.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="b4ebd-295">Skalierung von 150 %</span><span class="sxs-lookup"><span data-stu-id="b4ebd-295">150% scale</span></span></td>
    <td><span data-ttu-id="b4ebd-296">465 x 465</span><span class="sxs-lookup"><span data-stu-id="b4ebd-296">465x465</span></span></td>
    <td><span data-ttu-id="b4ebd-297">Square310x310Logo.scale-150.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-297">Square310x310Logo.scale-150.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="b4ebd-298">Skalierung von 200 %</span><span class="sxs-lookup"><span data-stu-id="b4ebd-298">200% scale</span></span></td>
    <td><span data-ttu-id="b4ebd-299">620 x 620</span><span class="sxs-lookup"><span data-stu-id="b4ebd-299">620x620</span></span></td>
    <td><span data-ttu-id="b4ebd-300">Square310x310Logo.scale-200.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-300">Square310x310Logo.scale-200.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="b4ebd-301">Skalierung von 400 %</span><span class="sxs-lookup"><span data-stu-id="b4ebd-301">400% scale</span></span></td>
    <td><span data-ttu-id="b4ebd-302">1240 x 1240</span><span class="sxs-lookup"><span data-stu-id="b4ebd-302">1240x1240</span></span></td>
    <td><span data-ttu-id="b4ebd-303">Square310x310Logo.scale-400.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-303">Square310x310Logo.scale-400.png</span></span></td>
</tr>
</tbody>
</table>

<br/>

<table>
<thead>
<tr><th colspan="3"><span data-ttu-id="b4ebd-304">App-Listensymbol (Square44x44Logo)</span><span class="sxs-lookup"><span data-stu-id="b4ebd-304">App list icon (Square44x44Logo)</span></span></th></tr>
</thead>
<tbody>
<tr>
    <td width="20%"><span data-ttu-id="b4ebd-305">Skalierung von 100 %</span><span class="sxs-lookup"><span data-stu-id="b4ebd-305">100% scale</span></span></td>
    <td width="20%"><span data-ttu-id="b4ebd-306">44 x 44</span><span class="sxs-lookup"><span data-stu-id="b4ebd-306">44x44</span></span></td>
    <td><span data-ttu-id="b4ebd-307">Square44x44Logo.scale-100.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-307">Square44x44Logo.scale-100.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="b4ebd-308">Skalierung von 125 %</span><span class="sxs-lookup"><span data-stu-id="b4ebd-308">125% scale</span></span></td>
    <td><span data-ttu-id="b4ebd-309">55 x 55</span><span class="sxs-lookup"><span data-stu-id="b4ebd-309">55x55</span></span></td>
    <td><span data-ttu-id="b4ebd-310">Square44x44Logo.scale-125.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-310">Square44x44Logo.scale-125.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="b4ebd-311">Skalierung von 150 %</span><span class="sxs-lookup"><span data-stu-id="b4ebd-311">150% scale</span></span></td>
    <td><span data-ttu-id="b4ebd-312">66 x 66</span><span class="sxs-lookup"><span data-stu-id="b4ebd-312">66x66</span></span></td>
    <td><span data-ttu-id="b4ebd-313">Square44x44Logo.scale-150.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-313">Square44x44Logo.scale-150.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="b4ebd-314">Skalierung von 200 %</span><span class="sxs-lookup"><span data-stu-id="b4ebd-314">200% scale</span></span></td>
    <td><span data-ttu-id="b4ebd-315">88 x 88</span><span class="sxs-lookup"><span data-stu-id="b4ebd-315">88x88</span></span></td>
    <td><span data-ttu-id="b4ebd-316">Square44x44Logo.scale-200.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-316">Square44x44Logo.scale-200.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="b4ebd-317">Skalierung von 400 %</span><span class="sxs-lookup"><span data-stu-id="b4ebd-317">400% scale</span></span></td>
    <td><span data-ttu-id="b4ebd-318">176 x 176</span><span class="sxs-lookup"><span data-stu-id="b4ebd-318">176x176</span></span></td>
    <td><span data-ttu-id="b4ebd-319">Square44x44Logo.scale-400.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-319">Square44x44Logo.scale-400.png</span></span></td>
</tr>
</tbody>
</table>

<br/>

<table>
<thead>
<tr><th colspan="3"><span data-ttu-id="b4ebd-320">Begrüßungsbildschirm (SplashScreen)</span><span class="sxs-lookup"><span data-stu-id="b4ebd-320">Splash screen (SplashScreen)</span></span></th></tr>
</thead>
<tbody>
<tr>
    <td width="20%"><span data-ttu-id="b4ebd-321">Skalierung von 100 %</span><span class="sxs-lookup"><span data-stu-id="b4ebd-321">100% scale</span></span></td>
    <td width="20%"><span data-ttu-id="b4ebd-322">620 x 300</span><span class="sxs-lookup"><span data-stu-id="b4ebd-322">620x300</span></span></td>
    <td><span data-ttu-id="b4ebd-323">SplashScreen.scale-100.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-323">SplashScreen.scale-100.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="b4ebd-324">Skalierung von 125 %</span><span class="sxs-lookup"><span data-stu-id="b4ebd-324">125% scale</span></span></td>
    <td><span data-ttu-id="b4ebd-325">775 x 375</span><span class="sxs-lookup"><span data-stu-id="b4ebd-325">775x375</span></span></td>
    <td><span data-ttu-id="b4ebd-326">SplashScreen.scale-125.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-326">SplashScreen.scale-125.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="b4ebd-327">Skalierung von 150 %</span><span class="sxs-lookup"><span data-stu-id="b4ebd-327">150% scale</span></span></td>
    <td><span data-ttu-id="b4ebd-328">930 x 450</span><span class="sxs-lookup"><span data-stu-id="b4ebd-328">930x450</span></span></td>
    <td><span data-ttu-id="b4ebd-329">SplashScreen.scale-150.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-329">SplashScreen.scale-150.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="b4ebd-330">Skalierung von 200 %</span><span class="sxs-lookup"><span data-stu-id="b4ebd-330">200% scale</span></span></td>
    <td><span data-ttu-id="b4ebd-331">1240 x 600</span><span class="sxs-lookup"><span data-stu-id="b4ebd-331">1240x600</span></span></td>
    <td><span data-ttu-id="b4ebd-332">SplashScreen.scale-200.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-332">SplashScreen.scale-200.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="b4ebd-333">Skalierung von 400 %</span><span class="sxs-lookup"><span data-stu-id="b4ebd-333">400% scale</span></span></td>
    <td><span data-ttu-id="b4ebd-334">2480 x 1200</span><span class="sxs-lookup"><span data-stu-id="b4ebd-334">2480x1200</span></span></td>
    <td><span data-ttu-id="b4ebd-335">SplashScreen.scale-400.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-335">SplashScreen.scale-400.png</span></span></td>
</tr>
</tbody>
</table>

<br/>
 

**<span data-ttu-id="b4ebd-336">Zielbasierte Ressourcen</span><span class="sxs-lookup"><span data-stu-id="b4ebd-336">Target-based assets</span></span>**

<span data-ttu-id="b4ebd-337">Zielbasierte Ressourcen werden über mehrere Skalierungsfaktoren hinweg verwendet.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-337">Target-based assets are used across multiple scale factors.</span></span> <span data-ttu-id="b4ebd-338">Der Elementname für zielbasierte Ressourcen ist **Square44x44Logo**.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-338">The element name for target-based assets is **Square44x44Logo**.</span></span> <span data-ttu-id="b4ebd-339">Es wird dringend empfohlen, mindestens die folgenden Ressourcen zu übermitteln:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-339">We strongly recommend submitting the following assets as a bare minimum:</span></span>

<span data-ttu-id="b4ebd-340">16 x 16, 24 x 24, 32 x 32, 48 x 48, 256 x 256</span><span class="sxs-lookup"><span data-stu-id="b4ebd-340">16x16, 24x24, 32x32, 48x48, 256x256</span></span>

<span data-ttu-id="b4ebd-341">Die folgende Tabelle enthält alle zielbasierten Ressourcengrößen und die entsprechenden Dateinamenbeispiele:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-341">The following table lists all target-based asset sizes and corresponding file name examples:</span></span>

| <span data-ttu-id="b4ebd-342">Ressourcengröße</span><span class="sxs-lookup"><span data-stu-id="b4ebd-342">Asset size</span></span> | <span data-ttu-id="b4ebd-343">Dateinamenbeispiel</span><span class="sxs-lookup"><span data-stu-id="b4ebd-343">File name example</span></span>                  |
|------------|------------------------------------|
| <span data-ttu-id="b4ebd-344">16 x 16\*</span><span class="sxs-lookup"><span data-stu-id="b4ebd-344">16x16\*</span></span>    | <span data-ttu-id="b4ebd-345">Square44x44Logo.targetsize-16.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-345">Square44x44Logo.targetsize-16.png</span></span>  |
| <span data-ttu-id="b4ebd-346">24 x 24\*</span><span class="sxs-lookup"><span data-stu-id="b4ebd-346">24x24\*</span></span>    | <span data-ttu-id="b4ebd-347">Square44x44Logo.targetsize-24.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-347">Square44x44Logo.targetsize-24.png</span></span>  |
| <span data-ttu-id="b4ebd-348">32 x 32\*</span><span class="sxs-lookup"><span data-stu-id="b4ebd-348">32x32\*</span></span>    | <span data-ttu-id="b4ebd-349">Square44x44Logo.targetsize-32.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-349">Square44x44Logo.targetsize-32.png</span></span>  |
| <span data-ttu-id="b4ebd-350">48 x 48\*</span><span class="sxs-lookup"><span data-stu-id="b4ebd-350">48x48\*</span></span>    | <span data-ttu-id="b4ebd-351">Square44x44Logo.targetsize-48.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-351">Square44x44Logo.targetsize-48.png</span></span>  |
| <span data-ttu-id="b4ebd-352">256 x 256\*</span><span class="sxs-lookup"><span data-stu-id="b4ebd-352">256x256\*</span></span>  | <span data-ttu-id="b4ebd-353">Square44x44Logo.targetsize-256.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-353">Square44x44Logo.targetsize-256.png</span></span> |
| <span data-ttu-id="b4ebd-354">20 x 20</span><span class="sxs-lookup"><span data-stu-id="b4ebd-354">20x20</span></span>      | <span data-ttu-id="b4ebd-355">Square44x44Logo.targetsize-20.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-355">Square44x44Logo.targetsize-20.png</span></span>  |
| <span data-ttu-id="b4ebd-356">30x30</span><span class="sxs-lookup"><span data-stu-id="b4ebd-356">30x30</span></span>      | <span data-ttu-id="b4ebd-357">Square44x44Logo.targetsize-30.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-357">Square44x44Logo.targetsize-30.png</span></span>  |
| <span data-ttu-id="b4ebd-358">36 x 36</span><span class="sxs-lookup"><span data-stu-id="b4ebd-358">36x36</span></span>      | <span data-ttu-id="b4ebd-359">Square44x44Logo.targetsize-36.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-359">Square44x44Logo.targetsize-36.png</span></span>  |
| <span data-ttu-id="b4ebd-360">40 x 40</span><span class="sxs-lookup"><span data-stu-id="b4ebd-360">40x40</span></span>      | <span data-ttu-id="b4ebd-361">Square44x44Logo.targetsize-40.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-361">Square44x44Logo.targetsize-40.png</span></span>  |
| <span data-ttu-id="b4ebd-362">60 x 60</span><span class="sxs-lookup"><span data-stu-id="b4ebd-362">60x60</span></span>      | <span data-ttu-id="b4ebd-363">Square44x44Logo.targetsize-60.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-363">Square44x44Logo.targetsize-60.png</span></span>  |
| <span data-ttu-id="b4ebd-364">64 x 64</span><span class="sxs-lookup"><span data-stu-id="b4ebd-364">64x64</span></span>      | <span data-ttu-id="b4ebd-365">Square44x44Logo.targetsize-64.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-365">Square44x44Logo.targetsize-64.png</span></span>  |
| <span data-ttu-id="b4ebd-366">72 x 72</span><span class="sxs-lookup"><span data-stu-id="b4ebd-366">72x72</span></span>      | <span data-ttu-id="b4ebd-367">Square44x44Logo.targetsize-72.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-367">Square44x44Logo.targetsize-72.png</span></span>  |
| <span data-ttu-id="b4ebd-368">80 x 80</span><span class="sxs-lookup"><span data-stu-id="b4ebd-368">80x80</span></span>      | <span data-ttu-id="b4ebd-369">Square44x44Logo.targetsize-80.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-369">Square44x44Logo.targetsize-80.png</span></span>  |
| <span data-ttu-id="b4ebd-370">96 x 96</span><span class="sxs-lookup"><span data-stu-id="b4ebd-370">96x96</span></span>      | <span data-ttu-id="b4ebd-371">Square44x44Logo.targetsize-96.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-371">Square44x44Logo.targetsize-96.png</span></span>  |

 

<span data-ttu-id="b4ebd-372">\* Übermitteln Sie diese Ressourcengrößen als Basislinie</span><span class="sxs-lookup"><span data-stu-id="b4ebd-372">\* Submit these asset sizes as a baseline</span></span>

## <a name="asset-types"></a><span data-ttu-id="b4ebd-373">Ressourcentypen</span><span class="sxs-lookup"><span data-stu-id="b4ebd-373">Asset types</span></span>


<span data-ttu-id="b4ebd-374">Nachfolgend sind alle Ressourcentypen, ihre Anwendungsmöglichkeiten sowie die empfohlenen Dateinamen aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-374">Listed here are all asset types, their uses, and recommended file names.</span></span>

**<span data-ttu-id="b4ebd-375">Kachelressourcen</span><span class="sxs-lookup"><span data-stu-id="b4ebd-375">Tile assets</span></span>**

-   <span data-ttu-id="b4ebd-376">Zentrierte Ressourcen werden in der Regel auf der Startseite zum Präsentieren Ihrer App verwendet.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-376">Centered assets are generally used on the Start to showcase your app.</span></span>
-   <span data-ttu-id="b4ebd-377">Dateinamenformat: [Square\Wide]\*x\*Logo.scale-\*.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-377">File name format: [Square\Wide]\*x\*Logo.scale-\*.png</span></span>
-   <span data-ttu-id="b4ebd-378">Betroffene Apps: Jede UWP-App</span><span class="sxs-lookup"><span data-stu-id="b4ebd-378">Impacted apps: Every UWP app</span></span>
-   <span data-ttu-id="b4ebd-379">Anwendungsmöglichkeiten:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-379">Uses:</span></span>
    -   <span data-ttu-id="b4ebd-380">Standard-Startkacheln (Desktop und mobil)</span><span class="sxs-lookup"><span data-stu-id="b4ebd-380">Default Start tiles (desktop and mobile)</span></span>
    -   <span data-ttu-id="b4ebd-381">Info-Center (Desktop und mobil)</span><span class="sxs-lookup"><span data-stu-id="b4ebd-381">Action center (desktop and mobile)</span></span>
    -   <span data-ttu-id="b4ebd-382">Aufgabenumschaltfunktion (mobil)</span><span class="sxs-lookup"><span data-stu-id="b4ebd-382">Task switcher (mobile)</span></span>
    -   <span data-ttu-id="b4ebd-383">Freigabeauswahl (mobil)</span><span class="sxs-lookup"><span data-stu-id="b4ebd-383">Share picker (mobile)</span></span>
    -   <span data-ttu-id="b4ebd-384">Datumsauswahl (mobil)</span><span class="sxs-lookup"><span data-stu-id="b4ebd-384">Picker (mobile)</span></span>
    -   <span data-ttu-id="b4ebd-385">Store</span><span class="sxs-lookup"><span data-stu-id="b4ebd-385">Store</span></span>

**<span data-ttu-id="b4ebd-386">Skalierbare Listeressourcen mit Anpassung</span><span class="sxs-lookup"><span data-stu-id="b4ebd-386">Scalable list assets with plate</span></span>**

-   <span data-ttu-id="b4ebd-387">Diese Ressourcen werden auf Flächen verwendet, die Skalierungsfaktoren erfordern.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-387">These assets are used on surfaces that request scale factors.</span></span> <span data-ttu-id="b4ebd-388">Diese Ressourcen werden vom System angepasst oder weisen ihre eigene Hintergrundfarbe auf, wenn die App diese enthält.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-388">Assets either get plated by the system or come with their own background color if the app includes that.</span></span>
-   <span data-ttu-id="b4ebd-389">Dateinamenformat: Square44x44Logo.scale-\*.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-389">File name format: Square44x44Logo.scale-\*.png</span></span>
-   <span data-ttu-id="b4ebd-390">Betroffene Apps: Jede UWP-App</span><span class="sxs-lookup"><span data-stu-id="b4ebd-390">Impacted apps: Every UWP app</span></span>
-   <span data-ttu-id="b4ebd-391">Anwendungsmöglichkeiten:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-391">Uses:</span></span>
    -   <span data-ttu-id="b4ebd-392">Starten der Liste aller Apps (Desktop)</span><span class="sxs-lookup"><span data-stu-id="b4ebd-392">Start all apps list (desktop)</span></span>
    -   <span data-ttu-id="b4ebd-393">Liste zum Starten der am häufigsten verwendeten Apps (Desktop)</span><span class="sxs-lookup"><span data-stu-id="b4ebd-393">Start most-frequently used list (desktop)</span></span>
    -   <span data-ttu-id="b4ebd-394">Task-Manager (Desktop)</span><span class="sxs-lookup"><span data-stu-id="b4ebd-394">Task manager (desktop)</span></span>
    -   <span data-ttu-id="b4ebd-395">Cortana-Suchergebnisse</span><span class="sxs-lookup"><span data-stu-id="b4ebd-395">Cortana search results</span></span>
    -   <span data-ttu-id="b4ebd-396">Liste zum Starten aller Apps (mobil)</span><span class="sxs-lookup"><span data-stu-id="b4ebd-396">Start all apps list (mobile)</span></span>
    -   <span data-ttu-id="b4ebd-397">Einstellungen</span><span class="sxs-lookup"><span data-stu-id="b4ebd-397">Settings</span></span>

**<span data-ttu-id="b4ebd-398">Zielgröße-Listenressourcen mit Anpassung</span><span class="sxs-lookup"><span data-stu-id="b4ebd-398">Target-size list assets with plate</span></span>**

-   <span data-ttu-id="b4ebd-399">Dies sind feste Größen, die nicht skaliert werden.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-399">These are fixed asset sizes that don't scale with plateaus.</span></span> <span data-ttu-id="b4ebd-400">Sie werden meistens für ältere Umgebungen verwendet.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-400">Mostly used for legacy experiences.</span></span> <span data-ttu-id="b4ebd-401">Ressourcen werden vom System überprüft.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-401">Assets are checked by the system.</span></span>
-   <span data-ttu-id="b4ebd-402">Dateinamenformat: Square44x44Logo.targetsize-\*.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-402">File name format: Square44x44Logo.targetsize-\*.png</span></span>
-   <span data-ttu-id="b4ebd-403">Betroffene Apps: Jede UWP-App</span><span class="sxs-lookup"><span data-stu-id="b4ebd-403">Impacted apps: Every UWP app</span></span>
-   <span data-ttu-id="b4ebd-404">Anwendungsmöglichkeiten:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-404">Uses:</span></span>
    -   <span data-ttu-id="b4ebd-405">Starten der Sprungliste (Desktop)</span><span class="sxs-lookup"><span data-stu-id="b4ebd-405">Start jump list (desktop)</span></span>
    -   <span data-ttu-id="b4ebd-406">Starten der unteren Ecke der Kachel (Desktop)</span><span class="sxs-lookup"><span data-stu-id="b4ebd-406">Start lower corner of tile (desktop)</span></span>
    -   <span data-ttu-id="b4ebd-407">Tastenkombinationen (Desktop)</span><span class="sxs-lookup"><span data-stu-id="b4ebd-407">Shortcuts (desktop)</span></span>
    -   <span data-ttu-id="b4ebd-408">Systemsteuerung (Desktop)</span><span class="sxs-lookup"><span data-stu-id="b4ebd-408">Control Panel (desktop)</span></span>

**<span data-ttu-id="b4ebd-409">Zielgröße-Listenressourcen ohne Anpassung</span><span class="sxs-lookup"><span data-stu-id="b4ebd-409">Target-size list assets without plate</span></span>**

-   <span data-ttu-id="b4ebd-410">Dies sind Objekte, die nicht vom System angepasst oder skaliert werden.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-410">These are assets that don't get plated or scaled by the system.</span></span>
-   <span data-ttu-id="b4ebd-411">Dateinamenformat: Square44x44Logo.targetsize-\*\_altform-unplated.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-411">File name format: Square44x44Logo.targetsize-\*\_altform-unplated.png</span></span>
-   <span data-ttu-id="b4ebd-412">Betroffene Apps: Jede UWP-App</span><span class="sxs-lookup"><span data-stu-id="b4ebd-412">Impacted apps: Every UWP app</span></span>
-   <span data-ttu-id="b4ebd-413">Anwendungsmöglichkeiten:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-413">Uses:</span></span>
    -   <span data-ttu-id="b4ebd-414">Taskleiste und Miniaturansicht der Taskleiste (Desktop)</span><span class="sxs-lookup"><span data-stu-id="b4ebd-414">Taskbar and taskbar thumbnail (desktop)</span></span>
    -   <span data-ttu-id="b4ebd-415">Taskleisten-Sprungliste</span><span class="sxs-lookup"><span data-stu-id="b4ebd-415">Taskbar jumplist</span></span>
    -   <span data-ttu-id="b4ebd-416">Aufgabenansicht</span><span class="sxs-lookup"><span data-stu-id="b4ebd-416">Task view</span></span>
    -   <span data-ttu-id="b4ebd-417">ALT + TAB</span><span class="sxs-lookup"><span data-stu-id="b4ebd-417">ALT+TAB</span></span>

**<span data-ttu-id="b4ebd-418">Dateierweiterungsressourcen</span><span class="sxs-lookup"><span data-stu-id="b4ebd-418">File extension assets</span></span>**

-   <span data-ttu-id="b4ebd-419">Hierbei handelt es sich um spezielle Ressourcen für Dateierweiterungen.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-419">These are assets specific to file extensions.</span></span> <span data-ttu-id="b4ebd-420">Sie werden neben Win32-Dateizuordnungssymbolen im Datei-Explorer angezeigt und müssen designunabhängig sein.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-420">They appear next to Win32-style file association icons in File Explorer and must be theme-agnostic.</span></span> <span data-ttu-id="b4ebd-421">Die Größe ist auf Desktops und mobilen Plattformen unterschiedlich.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-421">Sizing is different on desktop and mobile platforms.</span></span>
-   <span data-ttu-id="b4ebd-422">Dateinamenformat: \*LogoExtensions.targetsize-\*.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-422">File name format: \*LogoExtensions.targetsize-\*.png</span></span>
-   <span data-ttu-id="b4ebd-423">Betroffene Apps: Musik, Video, Fotos, Microsoft Edge, Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="b4ebd-423">Impacted apps: Music, Video, Photos, Microsoft Edge, Microsoft Office</span></span>
-   <span data-ttu-id="b4ebd-424">Anwendungsmöglichkeiten:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-424">Uses:</span></span>
    -   <span data-ttu-id="b4ebd-425">Datei-Explorer</span><span class="sxs-lookup"><span data-stu-id="b4ebd-425">File Explorer</span></span>
    -   <span data-ttu-id="b4ebd-426">Cortana</span><span class="sxs-lookup"><span data-stu-id="b4ebd-426">Cortana</span></span>
    -   <span data-ttu-id="b4ebd-427">Verschiedene Benutzeroberflächen (Desktop)</span><span class="sxs-lookup"><span data-stu-id="b4ebd-427">Various UI surfaces (desktop)</span></span>

**<span data-ttu-id="b4ebd-428">Begrüßungsbildschirm</span><span class="sxs-lookup"><span data-stu-id="b4ebd-428">Splash screen</span></span>**

-   <span data-ttu-id="b4ebd-429">Die Ressource, die auf dem Begrüßungsbildschirm Ihrer App angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-429">The asset that appears on your app's splash screen.</span></span> <span data-ttu-id="b4ebd-430">Automatische Skalierung auf Desktops und mobilen Plattformen.</span><span class="sxs-lookup"><span data-stu-id="b4ebd-430">Automatically scales on both desktop and mobile platforms.</span></span>
-   <span data-ttu-id="b4ebd-431">Dateinamenformat: SplashScreen.scale-*.png</span><span class="sxs-lookup"><span data-stu-id="b4ebd-431">File name format: SplashScreen.scale-*.png</span></span>
-   <span data-ttu-id="b4ebd-432">Betroffene Apps: Jede UWP-App</span><span class="sxs-lookup"><span data-stu-id="b4ebd-432">Impacted apps: Every UWP app</span></span>
-   <span data-ttu-id="b4ebd-433">Anwendungsmöglichkeiten:</span><span class="sxs-lookup"><span data-stu-id="b4ebd-433">Uses:</span></span>
    -   <span data-ttu-id="b4ebd-434">Begrüßungsbildschirm der App</span><span class="sxs-lookup"><span data-stu-id="b4ebd-434">App's splash screen</span></span>