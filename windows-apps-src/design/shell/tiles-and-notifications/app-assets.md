---
author: mijacobs
Description: App icon assets, which appear in a variety of forms throughout the Windows 10 operating system, are the calling cards for your Universal Windows Platform (UWP) app.
title: Ressourcen für Kacheln und Symbole
ms.assetid: D6CE21E5-2CFA-404F-8679-36AA522206C7
label: Tile and icon assets
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: cc614f7803e7546add8ecccb7cc20dc0250d0d22
ms.sourcegitcommit: eead3c00b27d9f66f79ec08c81a97e91dc1fdb3c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/18/2018
ms.locfileid: "1522789"
---
# <a name="guidelines-for-tile-and-icon-assets"></a><span data-ttu-id="120df-103">Richtlinien für die Ressourcen für Kacheln und Symbole</span><span class="sxs-lookup"><span data-stu-id="120df-103">Guidelines for tile and icon assets</span></span>

 


<span data-ttu-id="120df-104">Ressourcen für App-Symbole, die in einer Vielzahl von Formen innerhalb des Windows 10-Betriebssystems vorkommen, sind die Aushängeschilder für Ihre App für die Universelle Windows-Plattform (UWP).</span><span class="sxs-lookup"><span data-stu-id="120df-104">App icon assets, which appear in a variety of forms throughout the Windows 10 operating system, are the calling cards for your Universal Windows Platform (UWP) app.</span></span> <span data-ttu-id="120df-105">In diesen Richtlinien wird beschrieben, wo Ressourcen für App-Symbole im System angezeigt werden, und Sie erhalten ausführliche Designtipps zum Erstellen ansprechender Symbole.</span><span class="sxs-lookup"><span data-stu-id="120df-105">These guidelines detail where app icon assets appear in the system, and provide in-depth design tips on how to create the most polished icons.</span></span>

![Starten von Windows10 und Kacheln](images/assetguidance01.jpg)

## <a name="adaptive-scaling"></a><span data-ttu-id="120df-107">Adaptive Skalierung</span><span class="sxs-lookup"><span data-stu-id="120df-107">Adaptive scaling</span></span>


<span data-ttu-id="120df-108">Zunächst erhalten Sie einen kurzen Überblick über die adaptive Skalierung, um die Funktion der Skalierung mit Ressourcen verstehen zu können.</span><span class="sxs-lookup"><span data-stu-id="120df-108">First, a brief overview on adaptive scaling to better understand how scaling works with assets.</span></span> <span data-ttu-id="120df-109">Mit Windows10 wird eine Weiterentwicklung des vorhandenen Skalierungsmodells eingeführt.</span><span class="sxs-lookup"><span data-stu-id="120df-109">Windows 10 introduces an evolution of the existing scaling model.</span></span> <span data-ttu-id="120df-110">Neben der Skalierung von Vektorinhalten gibt es einen einheitlichen Satz von Skalierungsfaktoren, der eine einheitliche Größe für UI-Elemente für eine Vielzahl von Bildschirmgrößen und -auflösungen bietet.</span><span class="sxs-lookup"><span data-stu-id="120df-110">In addition to scaling vector content, there is a unified set of scale factors that provides a consistent size for UI elements across a variety of screen sizes and display resolutions.</span></span> <span data-ttu-id="120df-111">Die Skalierungsfaktoren sind auch mit den Skalierungsfaktoren anderer Betriebssysteme wie iOS und Android kompatibel, sodass die Ressourcen einfacher für alle diese Plattformen verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="120df-111">The scale factors are also compatible with the scale factors of other operating systems such as iOS and Android, which makes it easier to share assets between these platforms.</span></span>

<span data-ttu-id="120df-112">Die Auswahl der aus dem Store herunterzuladenden Ressourcen erfolgt zum Teil auf Grundlage des DPI-Werts eines Geräts.</span><span class="sxs-lookup"><span data-stu-id="120df-112">The Store picks the assets to download based in part on the DPI of the device.</span></span> <span data-ttu-id="120df-113">Nur die Ressourcen, die dem Gerät am besten entsprechen, werden heruntergeladen.</span><span class="sxs-lookup"><span data-stu-id="120df-113">Only the assets that best match the device are downloaded.</span></span>

## <a name="tile-elements"></a><span data-ttu-id="120df-114">Kachelelemente</span><span class="sxs-lookup"><span data-stu-id="120df-114">Tile elements</span></span>


<span data-ttu-id="120df-115">Die grundlegenden Komponenten einer Startkachel sind eine Rückwand, ein Symbol, eine Brandingleiste, Ränder und ein App-title:</span><span class="sxs-lookup"><span data-stu-id="120df-115">The basic components of a Start tile consist of a back plate, an icon, a branding bar, margins, and an app title:</span></span>

![Aufschlüsselung der Kachelelemente](images/assetguidance02.png)

<span data-ttu-id="120df-117">Auf der Brandingleiste am unteren Rand einer Kachel werden der App-Name, die Signalgebung und der Zähler (falls verwendet) angezeigt:</span><span class="sxs-lookup"><span data-stu-id="120df-117">The branding bar at the bottom of a tile is where the app name, badging, and counter (if used) appear:</span></span>

![Brandingleiste in der Kachel](images/assetguidance03.png)

<span data-ttu-id="120df-119">Die Höhe der Brandingleiste basiert auf dem Skalierungsfaktor des Geräts, auf dem sie angezeigt wird:</span><span class="sxs-lookup"><span data-stu-id="120df-119">The height of the branding bar is based on the scale factor of the device on which it appears:</span></span>

| <span data-ttu-id="120df-120">Skalierungsfaktor</span><span class="sxs-lookup"><span data-stu-id="120df-120">Scale factor</span></span> | <span data-ttu-id="120df-121">Pixel</span><span class="sxs-lookup"><span data-stu-id="120df-121">Pixels</span></span> |
|--------------|--------|
| <span data-ttu-id="120df-122">100%</span><span class="sxs-lookup"><span data-stu-id="120df-122">100%</span></span>         | <span data-ttu-id="120df-123">32</span><span class="sxs-lookup"><span data-stu-id="120df-123">32</span></span>     |
| <span data-ttu-id="120df-124">125%</span><span class="sxs-lookup"><span data-stu-id="120df-124">125%</span></span>         | <span data-ttu-id="120df-125">40</span><span class="sxs-lookup"><span data-stu-id="120df-125">40</span></span>     |
| <span data-ttu-id="120df-126">150%</span><span class="sxs-lookup"><span data-stu-id="120df-126">150%</span></span>         | <span data-ttu-id="120df-127">48</span><span class="sxs-lookup"><span data-stu-id="120df-127">48</span></span>     |
| <span data-ttu-id="120df-128">200%</span><span class="sxs-lookup"><span data-stu-id="120df-128">200%</span></span>         | <span data-ttu-id="120df-129">64</span><span class="sxs-lookup"><span data-stu-id="120df-129">64</span></span>     |
| <span data-ttu-id="120df-130">400%</span><span class="sxs-lookup"><span data-stu-id="120df-130">400%</span></span>         | <span data-ttu-id="120df-131">128</span><span class="sxs-lookup"><span data-stu-id="120df-131">128</span></span>    |

 

<span data-ttu-id="120df-132">Die Ränder der Kachel werden vom System festgelegt und können nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="120df-132">The system sets tile margins and cannot be modified.</span></span> <span data-ttu-id="120df-133">Die meisten Inhalte werden innerhalb der Ränder angezeigt, wie in diesem Beispiel:</span><span class="sxs-lookup"><span data-stu-id="120df-133">Most content appears inside the margins, as seen in this example:</span></span>

![Kachelfassaden](images/assetguidance04.png)

<span data-ttu-id="120df-135">Die Randbreite basiert auf dem Skalierungsfaktor des Geräts, auf dem sie angezeigt wird:</span><span class="sxs-lookup"><span data-stu-id="120df-135">Margin width is based on the scale factor of the device on which it appears:</span></span>

| <span data-ttu-id="120df-136">Skalierungsfaktor</span><span class="sxs-lookup"><span data-stu-id="120df-136">Scale factor</span></span> | <span data-ttu-id="120df-137">Pixel</span><span class="sxs-lookup"><span data-stu-id="120df-137">Pixels</span></span> |
|--------------|--------|
| <span data-ttu-id="120df-138">100%</span><span class="sxs-lookup"><span data-stu-id="120df-138">100%</span></span>         | <span data-ttu-id="120df-139">8</span><span class="sxs-lookup"><span data-stu-id="120df-139">8</span></span>      |
| <span data-ttu-id="120df-140">125%</span><span class="sxs-lookup"><span data-stu-id="120df-140">125%</span></span>         | <span data-ttu-id="120df-141">10</span><span class="sxs-lookup"><span data-stu-id="120df-141">10</span></span>     |
| <span data-ttu-id="120df-142">150%</span><span class="sxs-lookup"><span data-stu-id="120df-142">150%</span></span>         | <span data-ttu-id="120df-143">12</span><span class="sxs-lookup"><span data-stu-id="120df-143">12</span></span>     |
| <span data-ttu-id="120df-144">200%</span><span class="sxs-lookup"><span data-stu-id="120df-144">200%</span></span>         | <span data-ttu-id="120df-145">16</span><span class="sxs-lookup"><span data-stu-id="120df-145">16</span></span>     |
| <span data-ttu-id="120df-146">400%</span><span class="sxs-lookup"><span data-stu-id="120df-146">400%</span></span>         | <span data-ttu-id="120df-147">32</span><span class="sxs-lookup"><span data-stu-id="120df-147">32</span></span>     |

 

## <a name="tile-assets"></a><span data-ttu-id="120df-148">Kachelressourcen</span><span class="sxs-lookup"><span data-stu-id="120df-148">Tile assets</span></span>


<span data-ttu-id="120df-149">Jede Kachelressource hat die gleiche Größe wie die Kachel, auf der sie sich befindet.</span><span class="sxs-lookup"><span data-stu-id="120df-149">Each tile asset is the same size as the tile on which it is placed.</span></span> <span data-ttu-id="120df-150">Sie können die App-Kacheln mit zwei unterschiedlichen Darstellungsformen einer Ressource kennzeichnen:</span><span class="sxs-lookup"><span data-stu-id="120df-150">You can brand your app's tiles with two different representations of an asset:</span></span>

1. <span data-ttu-id="120df-151">Ein zentriertes Symbol oder Logo mit Abstand.</span><span class="sxs-lookup"><span data-stu-id="120df-151">An icon or logo centered with padding.</span></span> <span data-ttu-id="120df-152">Auf diese Weise scheint die Farbe der Rückwand durch:</span><span class="sxs-lookup"><span data-stu-id="120df-152">This lets the back plate color show through:</span></span>

![Kachel und Rückwand](images/assetguidance05.png)

2. <span data-ttu-id="120df-154">Eine randlose Brandingkachel ohne Abstand:</span><span class="sxs-lookup"><span data-stu-id="120df-154">A full-bleed, branded tile without padding:</span></span>

![Randlose Kachel](images/assetguidance06.png)

<span data-ttu-id="120df-156">Zum Zweck der Einheitlichkeit auf allen Geräten hat jede Kachelgröße (klein, mittel, breit und groß) eine eigene Größenbeziehung.</span><span class="sxs-lookup"><span data-stu-id="120df-156">For consistency across devices, each tile size (small, medium, wide, and large) has its own sizing relationship.</span></span> <span data-ttu-id="120df-157">Um eine einheitliche Symbolanordnung auf allen Kacheln zu erreichen, empfehlen wir einige grundlegende Abstandsrichtlinien für die folgenden Kachelgrößen.</span><span class="sxs-lookup"><span data-stu-id="120df-157">In order to achieve a consistent icon placement across tiles, we recommend a few basic padding guidelines for the following tile sizes.</span></span> <span data-ttu-id="120df-158">Der Bereich, in dem zwei violette Überlagerungen schneiden, ist die ideale Fläche für ein Symbol.</span><span class="sxs-lookup"><span data-stu-id="120df-158">The area where the two purple overlays intersect represents the ideal footprint for an icon.</span></span> <span data-ttu-id="120df-159">Symbole passen zwar nicht immer genau in die Fläche, das visuelle Volumen eines Symbols sollte aber ungefähr den dargestellten Beispielen entsprechen.</span><span class="sxs-lookup"><span data-stu-id="120df-159">Although icons won't always fit inside the footprint, the visual volume of an icon should be roughly equivalent to the provided examples.</span></span>

<span data-ttu-id="120df-160">Kleine Kachelgröße:</span><span class="sxs-lookup"><span data-stu-id="120df-160">Small tile sizing:</span></span>

![Beispiel für kleine Kachelgröße](images/assetguidance07a.png)

<span data-ttu-id="120df-162">Mittlere Kachelgröße:</span><span class="sxs-lookup"><span data-stu-id="120df-162">Medium tile sizing:</span></span>

![Beispiel für mittlere Kachelgröße](images/assetguidance07b.png)

<span data-ttu-id="120df-164">Breite Kachelgröße:</span><span class="sxs-lookup"><span data-stu-id="120df-164">Wide tile sizing:</span></span>

![Beispiel für breite Kachelgröße](images/assetguidance07c.png)

<span data-ttu-id="120df-166">Große Kachelgröße:</span><span class="sxs-lookup"><span data-stu-id="120df-166">Large tile sizing:</span></span>

![Beispiel für große Kachelgröße](images/assetguidance07d.png)

<span data-ttu-id="120df-168">In diesem Beispiel ist das Symbol für die Kachel zu groß:</span><span class="sxs-lookup"><span data-stu-id="120df-168">In this example, the icon is too large for the tile:</span></span>

![Symbol zu groß für die Kachel](images/assetguidance08a.png)

<span data-ttu-id="120df-170">In diesem Beispiel ist das Symbol für die Kachel zu klein:</span><span class="sxs-lookup"><span data-stu-id="120df-170">In this example, the icon is too small for the tile:</span></span>

![Symbol zu klein für die Kachel](images/assetguidance08b.png)

<span data-ttu-id="120df-172">Die folgenden Abstandsverhältnisse sind optimal für horizontal oder vertikal ausgerichtete Symbole.</span><span class="sxs-lookup"><span data-stu-id="120df-172">The following padding ratios are optimal for horizontally or vertically oriented icons.</span></span>

<span data-ttu-id="120df-173">Beschränken Sie bei kleinen Kacheln die Breite und Höhe auf 66% der Kachelgröße:</span><span class="sxs-lookup"><span data-stu-id="120df-173">For small tiles, limit the icon width and height to 66% of the tile size:</span></span>

![Verhältnisse bei kleinen Kachelgrößen](images/assetguidance09.png)

<span data-ttu-id="120df-175">Beschränken Sie bei mittelgroßen Kacheln die Symbolbreite auf 66% und die Höhe auf 50% der Kachelgröße.</span><span class="sxs-lookup"><span data-stu-id="120df-175">For medium tiles, limit the icon width to 66% and height to 50% of tile size.</span></span> <span data-ttu-id="120df-176">Dadurch wird verhindert, dass Elemente in der Brandingleiste überlappen:</span><span class="sxs-lookup"><span data-stu-id="120df-176">This prevents overlapping of elements in the branding bar:</span></span>

![Verhältnisse bei mittelgroßen Kacheln](images/assetguidance10.png)

<span data-ttu-id="120df-178">Beschränken Sie bei breiten Kacheln die Symbolbreite auf 66% und die Höhe auf 50% der Kachelgröße.</span><span class="sxs-lookup"><span data-stu-id="120df-178">For wide tiles, limit the icon width to 66% and height to 50% of tile size.</span></span> <span data-ttu-id="120df-179">Dadurch wird verhindert, dass Elemente in der Brandingleiste überlappen:</span><span class="sxs-lookup"><span data-stu-id="120df-179">This prevents overlapping of elements in the branding bar:</span></span>

![Verhältnisse bei breiten Kacheln](images/assetguidance11.png)

<span data-ttu-id="120df-181">Beschränken Sie bei großen Kacheln die Symbolbreite auf 66% und die Höhe auf 50% der Kachelgröße:</span><span class="sxs-lookup"><span data-stu-id="120df-181">For large tiles, limit the icon width to 66% and height to 50% of tile size:</span></span>

![Verhältnisse bei großen Kacheln](images/assetguidance12.png)

<span data-ttu-id="120df-183">Einige Symbole sind so konzipiert, dass sie horizontal oder vertikal ausgerichtet sind, andere Symbole hingegen weisen komplexere Formen auf, wodurch verhindert wird, dass sie direkt in die Zielabmessungen passen.</span><span class="sxs-lookup"><span data-stu-id="120df-183">Some icons are designed to be horizontally or vertically oriented, while others have more complex shapes that prevent them from fitting squarely within the target dimensions.</span></span> <span data-ttu-id="120df-184">Symbole, die zentriert erscheinen, können auf eine Seite geneigt sein.</span><span class="sxs-lookup"><span data-stu-id="120df-184">Icons that appear to be centered can be weighted to one side.</span></span> <span data-ttu-id="120df-185">In diesem Fall können Teile eines Symbols aus der empfohlenen Fläche heraushängen, vorausgesetzt, das Symbol belegt dasselbe visuelle Gewicht wie ein genau passendes Symbol:</span><span class="sxs-lookup"><span data-stu-id="120df-185">In this case, parts of an icon may hang outside the recommended footprint, provided it occupies the same visual weight as a squarely fitted icon:</span></span>

![Drei zentrierte Symbole](images/assetguidance13.png)

<span data-ttu-id="120df-187">Berücksichtigen Sie bei randlosen Ressourcen Elemente, die innerhalb der Ränder und Kanten der Kacheln interagieren.</span><span class="sxs-lookup"><span data-stu-id="120df-187">With full-bleed assets, take into account elements that interact within the margins and edges of the tiles.</span></span> <span data-ttu-id="120df-188">Behalten Sie Ränder von mindestens 16 % der Höhe oder Breite der Kachel bei.</span><span class="sxs-lookup"><span data-stu-id="120df-188">Maintain margins of at least 16% of the height or width of the tile.</span></span> <span data-ttu-id="120df-189">Dieser Prozentsatz stellt die doppelte Breite der Ränder bei den kleinsten Kachelgrößen dar:</span><span class="sxs-lookup"><span data-stu-id="120df-189">This percentage represents double the width of the margins at the smallest tile sizes:</span></span>

![Randlose Kachel mit Rändern](images/assetguidance14.png)

<span data-ttu-id="120df-191">In diesem Beispiel sind die Ränder zu eng:</span><span class="sxs-lookup"><span data-stu-id="120df-191">In this example, margins are too tight:</span></span>

![Randlose Kachel mit zu engen Rändern](images/assetguidance15.png)

## <a name="tile-assets-in-list-views"></a><span data-ttu-id="120df-193">Kachelressourcen in Listenansichten</span><span class="sxs-lookup"><span data-stu-id="120df-193">Tile assets in list views</span></span>


<span data-ttu-id="120df-194">Kacheln können auch in einer Listenansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="120df-194">Tiles can also appear in a list view.</span></span> <span data-ttu-id="120df-195">Größenrichtlinien für Kachelressourcen, die in Listenansichten angezeigt werden, unterscheiden sich leicht von den zuvor aufgeführten Kachelressourcen.</span><span class="sxs-lookup"><span data-stu-id="120df-195">Sizing guidelines for tile assets that appear in list views are a bit different than tile assets previously outlined.</span></span> <span data-ttu-id="120df-196">In diesem Abschnitt werden diese Einzelheiten bei der Größe erläutert.</span><span class="sxs-lookup"><span data-stu-id="120df-196">This section details those sizing specifics.</span></span>

![Kachelressourcen in einer Listenansicht](images/assetguidance16.png)

<span data-ttu-id="120df-198">Beschränken Sie die Breite und Höhe von Symbolen auf 75% der Kachelgröße:</span><span class="sxs-lookup"><span data-stu-id="120df-198">Limit icon width and height to 75% of the tile size:</span></span>

![Größe eines Symbols einer Listenansichtkachel](images/assetguidance17.png)

<span data-ttu-id="120df-200">Beschränken Sie bei vertikalen und horizontalen Symbolformaten die Breite und Höhe auf 75% der Kachelgröße:</span><span class="sxs-lookup"><span data-stu-id="120df-200">For vertical and horizontal icon formats, limit width and height to 75% of the tile size:</span></span>

![Größe eines Symbols einer Listenansichtkachel](images/assetguidance18.png)

<span data-ttu-id="120df-202">Behalten Sie bei randlosen Grafiken wichtiger Brandingelemente Ränder von 12,5% bei:</span><span class="sxs-lookup"><span data-stu-id="120df-202">For full bleed artwork of important brand elements, maintain margins of at least 12.5%:</span></span>

![Randlose Grafiken in Listenansichtkachel](images/assetguidance19.png)

<span data-ttu-id="120df-204">In diesem Beispiel ist das Symbol in der Kachel zu groß:</span><span class="sxs-lookup"><span data-stu-id="120df-204">In this example, the icon is too big inside its tile:</span></span>

![Symbol für die Kachel zu groß](images/assetguidance20a.png)

<span data-ttu-id="120df-206">In diesem Beispiel ist das Symbol in der Kachel zu klein:</span><span class="sxs-lookup"><span data-stu-id="120df-206">In this example, the icon is too small inside its tile:</span></span>

![Symbol für die Kachel zu klein](images/assetguidance20b.png)

## <a name="target-based-assets"></a><span data-ttu-id="120df-208">Zielbasierte Ressourcen</span><span class="sxs-lookup"><span data-stu-id="120df-208">Target-based assets</span></span>


<span data-ttu-id="120df-209">Zielbasierte Ressourcen gelten für Symbole und Kacheln, die in der Windows-Taskleiste, in der Aufgabenansicht, über ALT+TAB, in der Andockhilfe und in der unteren rechten Ecke von Startkacheln angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="120df-209">Target-based assets are for icons and tiles that appear on the Windows taskbar, task view, ALT+TAB, snap-assist, and the lower-right corner of Start tiles.</span></span> <span data-ttu-id="120df-210">Sie müssen für diese Ressourcen keine Abstände hinzufügen, diese werden bei Bedarf von Windows hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="120df-210">You don't have to add padding to these assets; Windows adds padding if needed.</span></span> <span data-ttu-id="120df-211">Bei diesen Ressourcen sollte eine minimale Fläche von 16Pixeln vorgesehen werden.</span><span class="sxs-lookup"><span data-stu-id="120df-211">These assets should account for a minimum footprint of 16 pixels.</span></span> <span data-ttu-id="120df-212">Unten sehen Sie ein Beispiel dafür, wie diese Ressourcen als Symbole in der Windows-Taskleiste angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="120df-212">Here's an example of these assets as they appear in icons on the Windows taskbar:</span></span>

![Ressourcen in Windows-Taskleiste](images/assetguidance21.png)

<span data-ttu-id="120df-214">Diese Benutzeroberfläche verwendet zwar neben einer farbigen Rückwand standardmäßig eine zielbasierte Ressource, Sie können aber auch eine zielbasierte Ressource ohne Anpassung verwenden.</span><span class="sxs-lookup"><span data-stu-id="120df-214">Although these UI will use a target-based asset on top of a colored backplate by default, you may use a target-based unplated asset as well.</span></span> <span data-ttu-id="120df-215">Ressourcen ohne Anpassung sollten so erstellt werden, dass es möglich ist, sie in unterschiedlichen Hintergrundfarben anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="120df-215">Unplated assets should be created with the possibility that they may appear on various background colors:</span></span>

![Ressourcen mit und ohne Anpassung](images/assetguidance22.png)

<span data-ttu-id="120df-217">Nachfolgend finden Sie die Größenempfehlungen für zielbasierte Ressourcen mit einer Skalierung von 100%:</span><span class="sxs-lookup"><span data-stu-id="120df-217">These are size recommendations for target-based assets, at 100% scale:</span></span>

![Zielbasierte Ressourcengröße bei einer Skalierung von 100%](images/assetguidance23.png)

## <a name="splash-screen-assets"></a><span data-ttu-id="120df-219">Ressourcen für den Begrüßungsbildschirm</span><span class="sxs-lookup"><span data-stu-id="120df-219">Splash screen assets</span></span>


<span data-ttu-id="120df-220">Das Bild für den Begrüßungsbildschirm kann als direkter Pfad zu einer Bilddatei oder als Ressource angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="120df-220">The splash screen image can be given either as a direct path to an image file or as a resource.</span></span> <span data-ttu-id="120df-221">Mithilfe eines Ressourcenverweises können Sie Bilder mit verschiedenen Skalierungen bereitstellen, damit Windows die optimale Größe für das jeweilige Gerät und die Bildschirmauflösung auswählen kann.</span><span class="sxs-lookup"><span data-stu-id="120df-221">By using a resource reference, you can supply images of different scales so that Windows can choose the best size for the device and screen resolution.</span></span> <span data-ttu-id="120df-222">Sie können auch Bilder mit hohem Kontrast für die Barrierefreiheit sowie lokalisierte Bilder für verschiedene Benutzeroberflächensprachen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="120df-222">You can also supply high contrast images for accessibility and localized images to match different UI languages.</span></span>

<span data-ttu-id="120df-223">Wenn Sie „Package.appxmanifest“ in einem Text-Editor öffnen, wird das [**SplashScreen**](https://docs.microsoft.com/uwp/schemas/appxpackage/appxmanifestschema/element-splashscreen)-Element als untergeordnetes Element des [**VisualElements**](https://docs.microsoft.com/uwp/schemas/appxpackage/appxmanifestschema/element-visualelements)-Elements angezeigt.</span><span class="sxs-lookup"><span data-stu-id="120df-223">If you open "Package.appxmanifest" in a text editor, the [**SplashScreen**](https://docs.microsoft.com/uwp/schemas/appxpackage/appxmanifestschema/element-splashscreen) element appears as a child of the [**VisualElements**](https://docs.microsoft.com/uwp/schemas/appxpackage/appxmanifestschema/element-visualelements) element.</span></span> <span data-ttu-id="120df-224">Das standardmäßige Begrüßungsbildschirm-Markup in der Manifestdatei sieht in einem Text-Editor wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="120df-224">The default splash screen markup in the manifest file looks like this in a text editor:</span></span>

```XML
<uap:SplashScreen Image="Assets\SplashScreen.png" /></code></pre></td>
</tr>
</tbody>
</table>
```

<span data-ttu-id="120df-225">Die Ressource für den Begrüßungsbildschirm wird von jedem Gerät zentriert, auf dem er angezeigt wird:</span><span class="sxs-lookup"><span data-stu-id="120df-225">The splash screen asset is centered by whichever device it appears on:</span></span>

![Größe der Ressource für den Begrüßungsbildschirm](images/assetguidance27.png)

## <a name="high-contrast-assets"></a><span data-ttu-id="120df-227">Ressourcen mit hohem Kontrast</span><span class="sxs-lookup"><span data-stu-id="120df-227">High-contrast assets</span></span>


<span data-ttu-id="120df-228">Der Modus mit hohem Kontrast verwendet separate Sätze von Ressourcen für kontrastreiches Weiß (weißer Hintergrund mit schwarzem Text) und kontrastreiches Schwarz (schwarzer Hintergrund mit weißem Text).</span><span class="sxs-lookup"><span data-stu-id="120df-228">High-contrast mode makes use of separate sets of assets for high-contrast white (white background with black text) and high-contrast black (black background with white text).</span></span> <span data-ttu-id="120df-229">Wenn Sie keine Ressourcen mit hohem Kontrast für Ihre App angeben, werden die Standardressourcen verwendet.</span><span class="sxs-lookup"><span data-stu-id="120df-229">If you don't provide high-contrast assets for your app, standard assets will be used.</span></span>

<span data-ttu-id="120df-230">Wenn die Standardressourcen für Ihre App eine akzeptable Anzeigeumgebung bei einem schwarzweißen Hintergrund bieten, sollte Ihre App im Modus mit hohem Kontrast zumindest zufriedenstellend aussehen.</span><span class="sxs-lookup"><span data-stu-id="120df-230">If your app's standard assets provide an acceptable viewing experience when rendered on a black-and-white background, then your app should look at least satisfactory in high-contrast mode.</span></span> <span data-ttu-id="120df-231">Wenn Ihre die Standardressourcen keine akzeptable Anzeigeumgebung bei einem schwarzweißen Hintergrund liefern, sollten Sie in Betracht ziehen, Ressourcen mit hohem Kontrast zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="120df-231">If your standard assets don't afford an acceptable viewing experience when rendered on a black-and-white background, consider specifically including high-contrast assets.</span></span> <span data-ttu-id="120df-232">Die folgenden Beispiele zeigen die zwei Arten von Ressourcen mit hohem Kontrast:</span><span class="sxs-lookup"><span data-stu-id="120df-232">These examples illustrate the two types of high-contrast assets:</span></span>

![Beispiele für hohes Kontrastverhältnis](images/assetguidance28.png)

<span data-ttu-id="120df-234">Wenn Sie Ressourcen mit hohem Kontrast bereitstellen möchten, müssen Sie beide Sätze – weiß auf schwarz und schwarz auf weiß – verwenden.</span><span class="sxs-lookup"><span data-stu-id="120df-234">If you decide to provide high-contrast assets, you need to include both sets—both white-on-black and black-on-white.</span></span> <span data-ttu-id="120df-235">Wenn Sie diese Ressourcen in Ihr Paket aufnehmen, können Sie einen Ordner "Kontrast Schwarz" für weiß auf schwarz, und einen Ordner "Kontrast Weiß" für schwarz auf weiß erstellen.</span><span class="sxs-lookup"><span data-stu-id="120df-235">When including these assets in your package, you could create a "contrast-black" folder for white-on-black assets, and a "contrast-white" folder for black-on-white assets.</span></span>

## <a name="asset-size-tables"></a><span data-ttu-id="120df-236">Größentabellen</span><span class="sxs-lookup"><span data-stu-id="120df-236">Asset size tables</span></span>


<span data-ttu-id="120df-237">Es wird dringend empfohlen, dass Sie mindestens Ressourcen für die Skalierungsfaktoren 100, 200 und 400 Skalierungsfaktoren bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="120df-237">At a bare minimum, we strongly recommend that you provide assets for the 100, 200, and 400 scale factors.</span></span> <span data-ttu-id="120df-238">Wenn Sie Ressourcen für alle Skalierungsfaktoren bereitstellen, liefert dies eine optimale Benutzererfahrung.</span><span class="sxs-lookup"><span data-stu-id="120df-238">Providing assets for all scale factors will provide the optimal user experience.</span></span>

<br/>

<table>
<thead>
<tr><th colspan="3"><span data-ttu-id="120df-239">Kleine Kachel (Square71x71Logo)</span><span class="sxs-lookup"><span data-stu-id="120df-239">Small tile (Square71x71Logo)</span></span></th></tr>
</thead>
<tbody>
<tr>
    <td width="20%"><span data-ttu-id="120df-240">Skalierung von 100 %</span><span class="sxs-lookup"><span data-stu-id="120df-240">100% scale</span></span></td>
    <td width="20%"><span data-ttu-id="120df-241">71 x 71</span><span class="sxs-lookup"><span data-stu-id="120df-241">71x71</span></span></td>
    <td><span data-ttu-id="120df-242">Square71x71Logo.scale-100.png</span><span class="sxs-lookup"><span data-stu-id="120df-242">Square71x71Logo.scale-100.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="120df-243">Skalierung von 125 %</span><span class="sxs-lookup"><span data-stu-id="120df-243">125% scale</span></span></td>
    <td><span data-ttu-id="120df-244">89 x 89</span><span class="sxs-lookup"><span data-stu-id="120df-244">89x89</span></span></td>
    <td><span data-ttu-id="120df-245">Square71x71Logo.scale-125.png</span><span class="sxs-lookup"><span data-stu-id="120df-245">Square71x71Logo.scale-125.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="120df-246">Skalierung von 150 %</span><span class="sxs-lookup"><span data-stu-id="120df-246">150% scale</span></span></td>
    <td><span data-ttu-id="120df-247">107 x 107</span><span class="sxs-lookup"><span data-stu-id="120df-247">107x107</span></span></td>
    <td><span data-ttu-id="120df-248">Square71x71Logo.scale-150.png</span><span class="sxs-lookup"><span data-stu-id="120df-248">Square71x71Logo.scale-150.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="120df-249">Skalierung von 200 %</span><span class="sxs-lookup"><span data-stu-id="120df-249">200% scale</span></span></td>
    <td><span data-ttu-id="120df-250">142 x 142</span><span class="sxs-lookup"><span data-stu-id="120df-250">142x142</span></span></td>
    <td><span data-ttu-id="120df-251">Square71x71Logo.scale-200.png</span><span class="sxs-lookup"><span data-stu-id="120df-251">Square71x71Logo.scale-200.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="120df-252">Skalierung von 400 %</span><span class="sxs-lookup"><span data-stu-id="120df-252">400% scale</span></span></td>
    <td><span data-ttu-id="120df-253">284x284</span><span class="sxs-lookup"><span data-stu-id="120df-253">284x284</span></span></td>
    <td><span data-ttu-id="120df-254">Square71x71Logo.scale-400.png</span><span class="sxs-lookup"><span data-stu-id="120df-254">Square71x71Logo.scale-400.png</span></span></td>
</tr>
</tbody>
</table>

<br/>

<table>
<thead>
<tr><th colspan="3"><span data-ttu-id="120df-255">Mittelgroße Kachel (Square150x150Logo)</span><span class="sxs-lookup"><span data-stu-id="120df-255">Medium tile (Square150x150Logo)</span></span></th></tr>
</thead>
<tbody>
<tr>
    <td width="20%"><span data-ttu-id="120df-256">Skalierung von 100 %</span><span class="sxs-lookup"><span data-stu-id="120df-256">100% scale</span></span></td>
    <td width="20%"><span data-ttu-id="120df-257">150x150</span><span class="sxs-lookup"><span data-stu-id="120df-257">150x150</span></span></td>
    <td><span data-ttu-id="120df-258">Square150x150Logo.scale-100.png</span><span class="sxs-lookup"><span data-stu-id="120df-258">Square150x150Logo.scale-100.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="120df-259">Skalierung von 125 %</span><span class="sxs-lookup"><span data-stu-id="120df-259">125% scale</span></span></td>
    <td><span data-ttu-id="120df-260">188 x 188</span><span class="sxs-lookup"><span data-stu-id="120df-260">188x188</span></span></td>
    <td><span data-ttu-id="120df-261">Square150x150Logo.scale-125.png</span><span class="sxs-lookup"><span data-stu-id="120df-261">Square150x150Logo.scale-125.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="120df-262">Skalierung von 150 %</span><span class="sxs-lookup"><span data-stu-id="120df-262">150% scale</span></span></td>
    <td><span data-ttu-id="120df-263">225 x 225</span><span class="sxs-lookup"><span data-stu-id="120df-263">225x225</span></span></td>
    <td><span data-ttu-id="120df-264">Square150x150Logo.scale-150.png</span><span class="sxs-lookup"><span data-stu-id="120df-264">Square150x150Logo.scale-150.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="120df-265">Skalierung von 200 %</span><span class="sxs-lookup"><span data-stu-id="120df-265">200% scale</span></span></td>
    <td><span data-ttu-id="120df-266">300 x 300</span><span class="sxs-lookup"><span data-stu-id="120df-266">300x300</span></span></td>
    <td><span data-ttu-id="120df-267">Square150x150Logo.scale-200.png</span><span class="sxs-lookup"><span data-stu-id="120df-267">Square150x150Logo.scale-200.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="120df-268">Skalierung von 400 %</span><span class="sxs-lookup"><span data-stu-id="120df-268">400% scale</span></span></td>
    <td><span data-ttu-id="120df-269">600 x 600</span><span class="sxs-lookup"><span data-stu-id="120df-269">600x600</span></span></td>
    <td><span data-ttu-id="120df-270">Square150x150Logo.scale-400.png</span><span class="sxs-lookup"><span data-stu-id="120df-270">Square150x150Logo.scale-400.png</span></span></td>
</tr>
</tbody>
</table>

<br/>

<table>
<thead>
<tr><th colspan="3"><span data-ttu-id="120df-271">Breite Kachel (Wide310x150Logo)</span><span class="sxs-lookup"><span data-stu-id="120df-271">Wide tile (Wide310x150Logo)</span></span></th></tr>
</thead>
<tbody>
<tr>
    <td width="20%"><span data-ttu-id="120df-272">Skalierung von 100 %</span><span class="sxs-lookup"><span data-stu-id="120df-272">100% scale</span></span></td>
    <td width="20%"><span data-ttu-id="120df-273">310x150</span><span class="sxs-lookup"><span data-stu-id="120df-273">310x150</span></span></td>
    <td><span data-ttu-id="120df-274">Wide310x150Logo.scale-100.png</span><span class="sxs-lookup"><span data-stu-id="120df-274">Wide310x150Logo.scale-100.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="120df-275">Skalierung von 125 %</span><span class="sxs-lookup"><span data-stu-id="120df-275">125% scale</span></span></td>
    <td><span data-ttu-id="120df-276">388 x 188</span><span class="sxs-lookup"><span data-stu-id="120df-276">388x188</span></span></td>
    <td><span data-ttu-id="120df-277">Wide310x150Logo.scale-125.png</span><span class="sxs-lookup"><span data-stu-id="120df-277">Wide310x150Logo.scale-125.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="120df-278">Skalierung von 150 %</span><span class="sxs-lookup"><span data-stu-id="120df-278">150% scale</span></span></td>
    <td><span data-ttu-id="120df-279">465 x 225</span><span class="sxs-lookup"><span data-stu-id="120df-279">465x225</span></span></td>
    <td><span data-ttu-id="120df-280">Wide310x150Logo.scale-150.png</span><span class="sxs-lookup"><span data-stu-id="120df-280">Wide310x150Logo.scale-150.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="120df-281">Skalierung von 200 %</span><span class="sxs-lookup"><span data-stu-id="120df-281">200% scale</span></span></td>
    <td><span data-ttu-id="120df-282">620 x 300</span><span class="sxs-lookup"><span data-stu-id="120df-282">620x300</span></span></td>
    <td><span data-ttu-id="120df-283">Wide310x150Logo.scale-200.png</span><span class="sxs-lookup"><span data-stu-id="120df-283">Wide310x150Logo.scale-200.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="120df-284">Skalierung von 400 %</span><span class="sxs-lookup"><span data-stu-id="120df-284">400% scale</span></span></td>
    <td><span data-ttu-id="120df-285">1240 x 600</span><span class="sxs-lookup"><span data-stu-id="120df-285">1240x600</span></span></td>
    <td><span data-ttu-id="120df-286">Wide310x150Logo.scale-400.png</span><span class="sxs-lookup"><span data-stu-id="120df-286">Wide310x150Logo.scale-400.png</span></span></td>
</tr>
</tbody>
</table>

<br/>

<table>
<thead>
<tr><th colspan="3"><span data-ttu-id="120df-287">Große Kachel (Square310x310Logo)</span><span class="sxs-lookup"><span data-stu-id="120df-287">Large tile (Square310x310Logo)</span></span></th></tr>
</thead>
<tbody>
<tr>
    <td width="20%"><span data-ttu-id="120df-288">Skalierung von 100 %</span><span class="sxs-lookup"><span data-stu-id="120df-288">100% scale</span></span></td>
    <td width="20%"><span data-ttu-id="120df-289">310x310</span><span class="sxs-lookup"><span data-stu-id="120df-289">310x310</span></span></td>
    <td><span data-ttu-id="120df-290">Square310x310Logo.scale-100.png</span><span class="sxs-lookup"><span data-stu-id="120df-290">Square310x310Logo.scale-100.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="120df-291">Skalierung von 125 %</span><span class="sxs-lookup"><span data-stu-id="120df-291">125% scale</span></span></td>
    <td><span data-ttu-id="120df-292">388 x 388</span><span class="sxs-lookup"><span data-stu-id="120df-292">388x388</span></span></td>
    <td><span data-ttu-id="120df-293">Square310x310Logo.scale-125.png</span><span class="sxs-lookup"><span data-stu-id="120df-293">Square310x310Logo.scale-125.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="120df-294">Skalierung von 150 %</span><span class="sxs-lookup"><span data-stu-id="120df-294">150% scale</span></span></td>
    <td><span data-ttu-id="120df-295">465 x 465</span><span class="sxs-lookup"><span data-stu-id="120df-295">465x465</span></span></td>
    <td><span data-ttu-id="120df-296">Square310x310Logo.scale-150.png</span><span class="sxs-lookup"><span data-stu-id="120df-296">Square310x310Logo.scale-150.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="120df-297">Skalierung von 200 %</span><span class="sxs-lookup"><span data-stu-id="120df-297">200% scale</span></span></td>
    <td><span data-ttu-id="120df-298">620 x 620</span><span class="sxs-lookup"><span data-stu-id="120df-298">620x620</span></span></td>
    <td><span data-ttu-id="120df-299">Square310x310Logo.scale-200.png</span><span class="sxs-lookup"><span data-stu-id="120df-299">Square310x310Logo.scale-200.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="120df-300">Skalierung von 400 %</span><span class="sxs-lookup"><span data-stu-id="120df-300">400% scale</span></span></td>
    <td><span data-ttu-id="120df-301">1240 x 1240</span><span class="sxs-lookup"><span data-stu-id="120df-301">1240x1240</span></span></td>
    <td><span data-ttu-id="120df-302">Square310x310Logo.scale-400.png</span><span class="sxs-lookup"><span data-stu-id="120df-302">Square310x310Logo.scale-400.png</span></span></td>
</tr>
</tbody>
</table>

<br/>

<table>
<thead>
<tr><th colspan="3"><span data-ttu-id="120df-303">App-Listensymbol (Square44x44Logo)</span><span class="sxs-lookup"><span data-stu-id="120df-303">App list icon (Square44x44Logo)</span></span></th></tr>
</thead>
<tbody>
<tr>
    <td width="20%"><span data-ttu-id="120df-304">Skalierung von 100 %</span><span class="sxs-lookup"><span data-stu-id="120df-304">100% scale</span></span></td>
    <td width="20%"><span data-ttu-id="120df-305">44 x 44</span><span class="sxs-lookup"><span data-stu-id="120df-305">44x44</span></span></td>
    <td><span data-ttu-id="120df-306">Square44x44Logo.scale-100.png</span><span class="sxs-lookup"><span data-stu-id="120df-306">Square44x44Logo.scale-100.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="120df-307">Skalierung von 125 %</span><span class="sxs-lookup"><span data-stu-id="120df-307">125% scale</span></span></td>
    <td><span data-ttu-id="120df-308">55 x 55</span><span class="sxs-lookup"><span data-stu-id="120df-308">55x55</span></span></td>
    <td><span data-ttu-id="120df-309">Square44x44Logo.scale-125.png</span><span class="sxs-lookup"><span data-stu-id="120df-309">Square44x44Logo.scale-125.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="120df-310">Skalierung von 150 %</span><span class="sxs-lookup"><span data-stu-id="120df-310">150% scale</span></span></td>
    <td><span data-ttu-id="120df-311">66 x 66</span><span class="sxs-lookup"><span data-stu-id="120df-311">66x66</span></span></td>
    <td><span data-ttu-id="120df-312">Square44x44Logo.scale-150.png</span><span class="sxs-lookup"><span data-stu-id="120df-312">Square44x44Logo.scale-150.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="120df-313">Skalierung von 200 %</span><span class="sxs-lookup"><span data-stu-id="120df-313">200% scale</span></span></td>
    <td><span data-ttu-id="120df-314">88 x 88</span><span class="sxs-lookup"><span data-stu-id="120df-314">88x88</span></span></td>
    <td><span data-ttu-id="120df-315">Square44x44Logo.scale-200.png</span><span class="sxs-lookup"><span data-stu-id="120df-315">Square44x44Logo.scale-200.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="120df-316">Skalierung von 400 %</span><span class="sxs-lookup"><span data-stu-id="120df-316">400% scale</span></span></td>
    <td><span data-ttu-id="120df-317">176 x 176</span><span class="sxs-lookup"><span data-stu-id="120df-317">176x176</span></span></td>
    <td><span data-ttu-id="120df-318">Square44x44Logo.scale-400.png</span><span class="sxs-lookup"><span data-stu-id="120df-318">Square44x44Logo.scale-400.png</span></span></td>
</tr>
</tbody>
</table>

<br/>

<table>
<thead>
<tr><th colspan="3"><span data-ttu-id="120df-319">Begrüßungsbildschirm (SplashScreen)</span><span class="sxs-lookup"><span data-stu-id="120df-319">Splash screen (SplashScreen)</span></span></th></tr>
</thead>
<tbody>
<tr>
    <td width="20%"><span data-ttu-id="120df-320">Skalierung von 100 %</span><span class="sxs-lookup"><span data-stu-id="120df-320">100% scale</span></span></td>
    <td width="20%"><span data-ttu-id="120df-321">620 x 300</span><span class="sxs-lookup"><span data-stu-id="120df-321">620x300</span></span></td>
    <td><span data-ttu-id="120df-322">SplashScreen.scale-100.png</span><span class="sxs-lookup"><span data-stu-id="120df-322">SplashScreen.scale-100.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="120df-323">Skalierung von 125 %</span><span class="sxs-lookup"><span data-stu-id="120df-323">125% scale</span></span></td>
    <td><span data-ttu-id="120df-324">775 x 375</span><span class="sxs-lookup"><span data-stu-id="120df-324">775x375</span></span></td>
    <td><span data-ttu-id="120df-325">SplashScreen.scale-125.png</span><span class="sxs-lookup"><span data-stu-id="120df-325">SplashScreen.scale-125.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="120df-326">Skalierung von 150 %</span><span class="sxs-lookup"><span data-stu-id="120df-326">150% scale</span></span></td>
    <td><span data-ttu-id="120df-327">930 x 450</span><span class="sxs-lookup"><span data-stu-id="120df-327">930x450</span></span></td>
    <td><span data-ttu-id="120df-328">SplashScreen.scale-150.png</span><span class="sxs-lookup"><span data-stu-id="120df-328">SplashScreen.scale-150.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="120df-329">Skalierung von 200 %</span><span class="sxs-lookup"><span data-stu-id="120df-329">200% scale</span></span></td>
    <td><span data-ttu-id="120df-330">1240 x 600</span><span class="sxs-lookup"><span data-stu-id="120df-330">1240x600</span></span></td>
    <td><span data-ttu-id="120df-331">SplashScreen.scale-200.png</span><span class="sxs-lookup"><span data-stu-id="120df-331">SplashScreen.scale-200.png</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="120df-332">Skalierung von 400 %</span><span class="sxs-lookup"><span data-stu-id="120df-332">400% scale</span></span></td>
    <td><span data-ttu-id="120df-333">2480 x 1200</span><span class="sxs-lookup"><span data-stu-id="120df-333">2480x1200</span></span></td>
    <td><span data-ttu-id="120df-334">SplashScreen.scale-400.png</span><span class="sxs-lookup"><span data-stu-id="120df-334">SplashScreen.scale-400.png</span></span></td>
</tr>
</tbody>
</table>

<br/>
 

**<span data-ttu-id="120df-335">Zielbasierte Ressourcen</span><span class="sxs-lookup"><span data-stu-id="120df-335">Target-based assets</span></span>**

<span data-ttu-id="120df-336">Zielbasierte Ressourcen werden über mehrere Skalierungsfaktoren hinweg verwendet.</span><span class="sxs-lookup"><span data-stu-id="120df-336">Target-based assets are used across multiple scale factors.</span></span> <span data-ttu-id="120df-337">Der Elementname für zielbasierte Ressourcen ist **Square44x44Logo**.</span><span class="sxs-lookup"><span data-stu-id="120df-337">The element name for target-based assets is **Square44x44Logo**.</span></span> <span data-ttu-id="120df-338">Es wird dringend empfohlen, mindestens die folgenden Ressourcen zu übermitteln:</span><span class="sxs-lookup"><span data-stu-id="120df-338">We strongly recommend submitting the following assets as a bare minimum:</span></span>

<span data-ttu-id="120df-339">16 x 16, 24 x 24, 32 x 32, 48 x 48, 256 x 256</span><span class="sxs-lookup"><span data-stu-id="120df-339">16x16, 24x24, 32x32, 48x48, 256x256</span></span>

<span data-ttu-id="120df-340">Die folgende Tabelle enthält alle zielbasierten Ressourcengrößen und die entsprechenden Dateinamenbeispiele:</span><span class="sxs-lookup"><span data-stu-id="120df-340">The following table lists all target-based asset sizes and corresponding file name examples:</span></span>

| <span data-ttu-id="120df-341">Ressourcengröße</span><span class="sxs-lookup"><span data-stu-id="120df-341">Asset size</span></span> | <span data-ttu-id="120df-342">Dateinamenbeispiel</span><span class="sxs-lookup"><span data-stu-id="120df-342">File name example</span></span>                  |
|------------|------------------------------------|
| <span data-ttu-id="120df-343">16 x 16\*</span><span class="sxs-lookup"><span data-stu-id="120df-343">16x16\*</span></span>    | <span data-ttu-id="120df-344">Square44x44Logo.targetsize-16.png</span><span class="sxs-lookup"><span data-stu-id="120df-344">Square44x44Logo.targetsize-16.png</span></span>  |
| <span data-ttu-id="120df-345">24 x 24\*</span><span class="sxs-lookup"><span data-stu-id="120df-345">24x24\*</span></span>    | <span data-ttu-id="120df-346">Square44x44Logo.targetsize-24.png</span><span class="sxs-lookup"><span data-stu-id="120df-346">Square44x44Logo.targetsize-24.png</span></span>  |
| <span data-ttu-id="120df-347">32 x 32\*</span><span class="sxs-lookup"><span data-stu-id="120df-347">32x32\*</span></span>    | <span data-ttu-id="120df-348">Square44x44Logo.targetsize-32.png</span><span class="sxs-lookup"><span data-stu-id="120df-348">Square44x44Logo.targetsize-32.png</span></span>  |
| <span data-ttu-id="120df-349">48 x 48\*</span><span class="sxs-lookup"><span data-stu-id="120df-349">48x48\*</span></span>    | <span data-ttu-id="120df-350">Square44x44Logo.targetsize-48.png</span><span class="sxs-lookup"><span data-stu-id="120df-350">Square44x44Logo.targetsize-48.png</span></span>  |
| <span data-ttu-id="120df-351">256 x 256\*</span><span class="sxs-lookup"><span data-stu-id="120df-351">256x256\*</span></span>  | <span data-ttu-id="120df-352">Square44x44Logo.targetsize-256.png</span><span class="sxs-lookup"><span data-stu-id="120df-352">Square44x44Logo.targetsize-256.png</span></span> |
| <span data-ttu-id="120df-353">20 x 20</span><span class="sxs-lookup"><span data-stu-id="120df-353">20x20</span></span>      | <span data-ttu-id="120df-354">Square44x44Logo.targetsize-20.png</span><span class="sxs-lookup"><span data-stu-id="120df-354">Square44x44Logo.targetsize-20.png</span></span>  |
| <span data-ttu-id="120df-355">30x30</span><span class="sxs-lookup"><span data-stu-id="120df-355">30x30</span></span>      | <span data-ttu-id="120df-356">Square44x44Logo.targetsize-30.png</span><span class="sxs-lookup"><span data-stu-id="120df-356">Square44x44Logo.targetsize-30.png</span></span>  |
| <span data-ttu-id="120df-357">36 x 36</span><span class="sxs-lookup"><span data-stu-id="120df-357">36x36</span></span>      | <span data-ttu-id="120df-358">Square44x44Logo.targetsize-36.png</span><span class="sxs-lookup"><span data-stu-id="120df-358">Square44x44Logo.targetsize-36.png</span></span>  |
| <span data-ttu-id="120df-359">40 x 40</span><span class="sxs-lookup"><span data-stu-id="120df-359">40x40</span></span>      | <span data-ttu-id="120df-360">Square44x44Logo.targetsize-40.png</span><span class="sxs-lookup"><span data-stu-id="120df-360">Square44x44Logo.targetsize-40.png</span></span>  |
| <span data-ttu-id="120df-361">60 x 60</span><span class="sxs-lookup"><span data-stu-id="120df-361">60x60</span></span>      | <span data-ttu-id="120df-362">Square44x44Logo.targetsize-60.png</span><span class="sxs-lookup"><span data-stu-id="120df-362">Square44x44Logo.targetsize-60.png</span></span>  |
| <span data-ttu-id="120df-363">64 x 64</span><span class="sxs-lookup"><span data-stu-id="120df-363">64x64</span></span>      | <span data-ttu-id="120df-364">Square44x44Logo.targetsize-64.png</span><span class="sxs-lookup"><span data-stu-id="120df-364">Square44x44Logo.targetsize-64.png</span></span>  |
| <span data-ttu-id="120df-365">72 x 72</span><span class="sxs-lookup"><span data-stu-id="120df-365">72x72</span></span>      | <span data-ttu-id="120df-366">Square44x44Logo.targetsize-72.png</span><span class="sxs-lookup"><span data-stu-id="120df-366">Square44x44Logo.targetsize-72.png</span></span>  |
| <span data-ttu-id="120df-367">80 x 80</span><span class="sxs-lookup"><span data-stu-id="120df-367">80x80</span></span>      | <span data-ttu-id="120df-368">Square44x44Logo.targetsize-80.png</span><span class="sxs-lookup"><span data-stu-id="120df-368">Square44x44Logo.targetsize-80.png</span></span>  |
| <span data-ttu-id="120df-369">96 x 96</span><span class="sxs-lookup"><span data-stu-id="120df-369">96x96</span></span>      | <span data-ttu-id="120df-370">Square44x44Logo.targetsize-96.png</span><span class="sxs-lookup"><span data-stu-id="120df-370">Square44x44Logo.targetsize-96.png</span></span>  |

 

<span data-ttu-id="120df-371">\* Übermitteln Sie diese Ressourcengrößen als Basislinie</span><span class="sxs-lookup"><span data-stu-id="120df-371">\* Submit these asset sizes as a baseline</span></span>

## <a name="asset-types"></a><span data-ttu-id="120df-372">Ressourcentypen</span><span class="sxs-lookup"><span data-stu-id="120df-372">Asset types</span></span>


<span data-ttu-id="120df-373">Nachfolgend sind alle Ressourcentypen, ihre Anwendungsmöglichkeiten sowie die empfohlenen Dateinamen aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="120df-373">Listed here are all asset types, their uses, and recommended file names.</span></span>

**<span data-ttu-id="120df-374">Kachelressourcen</span><span class="sxs-lookup"><span data-stu-id="120df-374">Tile assets</span></span>**

-   <span data-ttu-id="120df-375">Zentrierte Ressourcen werden in der Regel auf der Startseite zum Präsentieren Ihrer App verwendet.</span><span class="sxs-lookup"><span data-stu-id="120df-375">Centered assets are generally used on the Start to showcase your app.</span></span>
-   <span data-ttu-id="120df-376">Dateinamenformat: [Square\Wide]\*x\*Logo.scale-\*.png</span><span class="sxs-lookup"><span data-stu-id="120df-376">File name format: [Square\Wide]\*x\*Logo.scale-\*.png</span></span>
-   <span data-ttu-id="120df-377">Betroffene Apps: Jede UWP-App</span><span class="sxs-lookup"><span data-stu-id="120df-377">Impacted apps: Every UWP app</span></span>
-   <span data-ttu-id="120df-378">Anwendungsmöglichkeiten:</span><span class="sxs-lookup"><span data-stu-id="120df-378">Uses:</span></span>
    -   <span data-ttu-id="120df-379">Standard-Startkacheln (Desktop und mobil)</span><span class="sxs-lookup"><span data-stu-id="120df-379">Default Start tiles (desktop and mobile)</span></span>
    -   <span data-ttu-id="120df-380">Info-Center (Desktop und mobil)</span><span class="sxs-lookup"><span data-stu-id="120df-380">Action center (desktop and mobile)</span></span>
    -   <span data-ttu-id="120df-381">Aufgabenumschaltfunktion (mobil)</span><span class="sxs-lookup"><span data-stu-id="120df-381">Task switcher (mobile)</span></span>
    -   <span data-ttu-id="120df-382">Freigabeauswahl (mobil)</span><span class="sxs-lookup"><span data-stu-id="120df-382">Share picker (mobile)</span></span>
    -   <span data-ttu-id="120df-383">Datumsauswahl (mobil)</span><span class="sxs-lookup"><span data-stu-id="120df-383">Picker (mobile)</span></span>
    -   <span data-ttu-id="120df-384">Store</span><span class="sxs-lookup"><span data-stu-id="120df-384">Store</span></span>

**<span data-ttu-id="120df-385">Skalierbare Listeressourcen mit Anpassung</span><span class="sxs-lookup"><span data-stu-id="120df-385">Scalable list assets with plate</span></span>**

-   <span data-ttu-id="120df-386">Diese Ressourcen werden auf Flächen verwendet, die Skalierungsfaktoren erfordern.</span><span class="sxs-lookup"><span data-stu-id="120df-386">These assets are used on surfaces that request scale factors.</span></span> <span data-ttu-id="120df-387">Diese Ressourcen werden vom System angepasst oder weisen ihre eigene Hintergrundfarbe auf, wenn die App diese enthält.</span><span class="sxs-lookup"><span data-stu-id="120df-387">Assets either get plated by the system or come with their own background color if the app includes that.</span></span>
-   <span data-ttu-id="120df-388">Dateinamenformat: Square44x44Logo.scale-\*.png</span><span class="sxs-lookup"><span data-stu-id="120df-388">File name format: Square44x44Logo.scale-\*.png</span></span>
-   <span data-ttu-id="120df-389">Betroffene Apps: Jede UWP-App</span><span class="sxs-lookup"><span data-stu-id="120df-389">Impacted apps: Every UWP app</span></span>
-   <span data-ttu-id="120df-390">Anwendungsmöglichkeiten:</span><span class="sxs-lookup"><span data-stu-id="120df-390">Uses:</span></span>
    -   <span data-ttu-id="120df-391">Starten der Liste aller Apps (Desktop)</span><span class="sxs-lookup"><span data-stu-id="120df-391">Start all apps list (desktop)</span></span>
    -   <span data-ttu-id="120df-392">Liste zum Starten der am häufigsten verwendeten Apps (Desktop)</span><span class="sxs-lookup"><span data-stu-id="120df-392">Start most-frequently used list (desktop)</span></span>
    -   <span data-ttu-id="120df-393">Task-Manager (Desktop)</span><span class="sxs-lookup"><span data-stu-id="120df-393">Task manager (desktop)</span></span>
    -   <span data-ttu-id="120df-394">Cortana-Suchergebnisse</span><span class="sxs-lookup"><span data-stu-id="120df-394">Cortana search results</span></span>
    -   <span data-ttu-id="120df-395">Liste zum Starten aller Apps (mobil)</span><span class="sxs-lookup"><span data-stu-id="120df-395">Start all apps list (mobile)</span></span>
    -   <span data-ttu-id="120df-396">Einstellungen</span><span class="sxs-lookup"><span data-stu-id="120df-396">Settings</span></span>

**<span data-ttu-id="120df-397">Zielgröße-Listenressourcen mit Anpassung</span><span class="sxs-lookup"><span data-stu-id="120df-397">Target-size list assets with plate</span></span>**

-   <span data-ttu-id="120df-398">Dies sind feste Größen, die nicht skaliert werden.</span><span class="sxs-lookup"><span data-stu-id="120df-398">These are fixed asset sizes that don't scale with plateaus.</span></span> <span data-ttu-id="120df-399">Sie werden meistens für ältere Umgebungen verwendet.</span><span class="sxs-lookup"><span data-stu-id="120df-399">Mostly used for legacy experiences.</span></span> <span data-ttu-id="120df-400">Ressourcen werden vom System überprüft.</span><span class="sxs-lookup"><span data-stu-id="120df-400">Assets are checked by the system.</span></span>
-   <span data-ttu-id="120df-401">Dateinamenformat: Square44x44Logo.targetsize-\*.png</span><span class="sxs-lookup"><span data-stu-id="120df-401">File name format: Square44x44Logo.targetsize-\*.png</span></span>
-   <span data-ttu-id="120df-402">Betroffene Apps: Jede UWP-App</span><span class="sxs-lookup"><span data-stu-id="120df-402">Impacted apps: Every UWP app</span></span>
-   <span data-ttu-id="120df-403">Anwendungsmöglichkeiten:</span><span class="sxs-lookup"><span data-stu-id="120df-403">Uses:</span></span>
    -   <span data-ttu-id="120df-404">Starten der Sprungliste (Desktop)</span><span class="sxs-lookup"><span data-stu-id="120df-404">Start jump list (desktop)</span></span>
    -   <span data-ttu-id="120df-405">Starten der unteren Ecke der Kachel (Desktop)</span><span class="sxs-lookup"><span data-stu-id="120df-405">Start lower corner of tile (desktop)</span></span>
    -   <span data-ttu-id="120df-406">Tastenkombinationen (Desktop)</span><span class="sxs-lookup"><span data-stu-id="120df-406">Shortcuts (desktop)</span></span>
    -   <span data-ttu-id="120df-407">Systemsteuerung (Desktop)</span><span class="sxs-lookup"><span data-stu-id="120df-407">Control Panel (desktop)</span></span>

**<span data-ttu-id="120df-408">Zielgröße-Listenressourcen ohne Anpassung</span><span class="sxs-lookup"><span data-stu-id="120df-408">Target-size list assets without plate</span></span>**

-   <span data-ttu-id="120df-409">Dies sind Objekte, die nicht vom System angepasst oder skaliert werden.</span><span class="sxs-lookup"><span data-stu-id="120df-409">These are assets that don't get plated or scaled by the system.</span></span>
-   <span data-ttu-id="120df-410">Dateinamenformat: Square44x44Logo.targetsize-\*\_altform-unplated.png</span><span class="sxs-lookup"><span data-stu-id="120df-410">File name format: Square44x44Logo.targetsize-\*\_altform-unplated.png</span></span>
-   <span data-ttu-id="120df-411">Betroffene Apps: Jede UWP-App</span><span class="sxs-lookup"><span data-stu-id="120df-411">Impacted apps: Every UWP app</span></span>
-   <span data-ttu-id="120df-412">Anwendungsmöglichkeiten:</span><span class="sxs-lookup"><span data-stu-id="120df-412">Uses:</span></span>
    -   <span data-ttu-id="120df-413">Taskleiste und Miniaturansicht der Taskleiste (Desktop)</span><span class="sxs-lookup"><span data-stu-id="120df-413">Taskbar and taskbar thumbnail (desktop)</span></span>
    -   <span data-ttu-id="120df-414">Taskleisten-Sprungliste</span><span class="sxs-lookup"><span data-stu-id="120df-414">Taskbar jumplist</span></span>
    -   <span data-ttu-id="120df-415">Aufgabenansicht</span><span class="sxs-lookup"><span data-stu-id="120df-415">Task view</span></span>
    -   <span data-ttu-id="120df-416">ALT + TAB</span><span class="sxs-lookup"><span data-stu-id="120df-416">ALT+TAB</span></span>

**<span data-ttu-id="120df-417">Dateierweiterungsressourcen</span><span class="sxs-lookup"><span data-stu-id="120df-417">File extension assets</span></span>**

-   <span data-ttu-id="120df-418">Hierbei handelt es sich um spezielle Ressourcen für Dateierweiterungen.</span><span class="sxs-lookup"><span data-stu-id="120df-418">These are assets specific to file extensions.</span></span> <span data-ttu-id="120df-419">Sie werden neben Win32-Dateizuordnungssymbolen im Datei-Explorer angezeigt und müssen designunabhängig sein.</span><span class="sxs-lookup"><span data-stu-id="120df-419">They appear next to Win32-style file association icons in File Explorer and must be theme-agnostic.</span></span> <span data-ttu-id="120df-420">Die Größe ist auf Desktops und mobilen Plattformen unterschiedlich.</span><span class="sxs-lookup"><span data-stu-id="120df-420">Sizing is different on desktop and mobile platforms.</span></span>
-   <span data-ttu-id="120df-421">Dateinamenformat: \*LogoExtensions.targetsize-\*.png</span><span class="sxs-lookup"><span data-stu-id="120df-421">File name format: \*LogoExtensions.targetsize-\*.png</span></span>
-   <span data-ttu-id="120df-422">Betroffene Apps: Musik, Video, Fotos, Microsoft Edge, Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="120df-422">Impacted apps: Music, Video, Photos, Microsoft Edge, Microsoft Office</span></span>
-   <span data-ttu-id="120df-423">Anwendungsmöglichkeiten:</span><span class="sxs-lookup"><span data-stu-id="120df-423">Uses:</span></span>
    -   <span data-ttu-id="120df-424">Datei-Explorer</span><span class="sxs-lookup"><span data-stu-id="120df-424">File Explorer</span></span>
    -   <span data-ttu-id="120df-425">Cortana</span><span class="sxs-lookup"><span data-stu-id="120df-425">Cortana</span></span>
    -   <span data-ttu-id="120df-426">Verschiedene Benutzeroberflächen (Desktop)</span><span class="sxs-lookup"><span data-stu-id="120df-426">Various UI surfaces (desktop)</span></span>

**<span data-ttu-id="120df-427">Begrüßungsbildschirm</span><span class="sxs-lookup"><span data-stu-id="120df-427">Splash screen</span></span>**

-   <span data-ttu-id="120df-428">Die Ressource, die auf dem Begrüßungsbildschirm Ihrer App angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="120df-428">The asset that appears on your app's splash screen.</span></span> <span data-ttu-id="120df-429">Automatische Skalierung auf Desktops und mobilen Plattformen.</span><span class="sxs-lookup"><span data-stu-id="120df-429">Automatically scales on both desktop and mobile platforms.</span></span>
-   <span data-ttu-id="120df-430">Dateinamenformat: SplashScreen.scale-\*.png</span><span class="sxs-lookup"><span data-stu-id="120df-430">File name format: SplashScreen.scale-\*.png</span></span>
-   <span data-ttu-id="120df-431">Betroffene Apps: Jede UWP-App</span><span class="sxs-lookup"><span data-stu-id="120df-431">Impacted apps: Every UWP app</span></span>
-   <span data-ttu-id="120df-432">Anwendungsmöglichkeiten:</span><span class="sxs-lookup"><span data-stu-id="120df-432">Uses:</span></span>
    -   <span data-ttu-id="120df-433">Begrüßungsbildschirm der App</span><span class="sxs-lookup"><span data-stu-id="120df-433">App's splash screen</span></span>