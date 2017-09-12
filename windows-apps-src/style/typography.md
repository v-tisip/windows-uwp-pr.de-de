---
author: mijacobs
description: "Typografie muss übersichtlich sein, da sie zur visuellen Darstellung von Sprache dient. Ihr Stil darf diesem Ziel nie im Wege stehen. Typografie spielt jedoch auch als Layoutkomponente eine wichtige Rolle und wirkt sich maßgeblich auf die Dichte und Komplexität des Designs und damit auf die Benutzerfreundlichkeit des Designs aus."
title: Typografie
ms.assetid: ca35f78a-e4da-423d-9f5b-75896e0b8f82
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 0609622053d0ae25b5039766137db1b195c0d69d
ms.sourcegitcommit: 5ece992c31870df4c089360ef47501bd4ce14fa9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2017
---
# <a name="typography"></a><span data-ttu-id="e5852-106">Typografie</span><span class="sxs-lookup"><span data-stu-id="e5852-106">Typography</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css"> 

<span data-ttu-id="e5852-107">Typografie muss übersichtlich sein, da sie zur visuellen Darstellung von Sprache dient.</span><span class="sxs-lookup"><span data-stu-id="e5852-107">As the visual representation of language, typography’s main task is to be clear.</span></span> <span data-ttu-id="e5852-108">Ihr Stil darf diesem Ziel nie im Wege stehen.</span><span class="sxs-lookup"><span data-stu-id="e5852-108">Its style should never get in the way of that goal.</span></span> <span data-ttu-id="e5852-109">Typografie spielt jedoch auch als Layoutkomponente eine wichtige Rolle und wirkt sich maßgeblich auf die Dichte und Komplexität des Designs und damit auf die Benutzerfreundlichkeit des Designs aus.</span><span class="sxs-lookup"><span data-stu-id="e5852-109">But typography also has an important role as a layout component—with a powerful effect on the density and complexity of the design—and on the user’s experience of that design.</span></span>

## <a name="typeface"></a><span data-ttu-id="e5852-110">Schriftart</span><span class="sxs-lookup"><span data-stu-id="e5852-110">Typeface</span></span>

<span data-ttu-id="e5852-111">Wir haben uns dafür entschieden, für alle digitalen Microsoft-Designs „SegoeUI“ zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="e5852-111">We’ve selected Segoe UI for use on all Microsoft digital designs.</span></span> <span data-ttu-id="e5852-112">„SegoeUI“ bietet eine breite Palette von Zeichen und zeichnet sich durch optimale Lesbarkeit bei unterschiedlichsten Größen und Pixeldichten aus.</span><span class="sxs-lookup"><span data-stu-id="e5852-112">Segoe UI provides a wide range of characters and is designed to maintain optimal legibility across sizes and pixel densities.</span></span> <span data-ttu-id="e5852-113">Die klare, ansprechende und offene Ästhetik passt perfekt zum Inhalt des Systems.</span><span class="sxs-lookup"><span data-stu-id="e5852-113">It offers a clean, light, and open aesthetic that complements the content of the system.</span></span>

![Beispieltext für die Schriftart „SegoeUI“](images/segoe-sample.png)

## <a name="weights"></a><span data-ttu-id="e5852-115">Breiten</span><span class="sxs-lookup"><span data-stu-id="e5852-115">Weights</span></span>

<span data-ttu-id="e5852-116">Bei der Typografie legen wir unter anderem Wert auf Schlichtheit und Effizienz.</span><span class="sxs-lookup"><span data-stu-id="e5852-116">We approach typography with an eye to simplicity and efficiency.</span></span> <span data-ttu-id="e5852-117">Wir verwenden eine einzelne Schriftart, eine geringe Anzahl von Schriftbreiten und -graden sowie eine klare Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="e5852-117">We choose to use one typeface, a minimum of weights and sizes, and a clear hierarchy.</span></span> <span data-ttu-id="e5852-118">Positionierung und Ausrichtung basieren auf dem Standardstil für die jeweilige Sprache.</span><span class="sxs-lookup"><span data-stu-id="e5852-118">Positioning and alignment follow the default style for the given language.</span></span> <span data-ttu-id="e5852-119">Im Deutschen wird Text von links nach rechts und von oben nach unten verwendet.</span><span class="sxs-lookup"><span data-stu-id="e5852-119">In English the sequence runs left to right, top to bottom.</span></span> <span data-ttu-id="e5852-120">Beziehungen zwischen Text und Bildern sind klar und einfach.</span><span class="sxs-lookup"><span data-stu-id="e5852-120">Relationships between text and images are clear and straightforward.</span></span>

![Unterstützte Schriftbreiten:](images/weights.png)

## <a name="line-spacing"></a><span data-ttu-id="e5852-123">Zeilenabstand</span><span class="sxs-lookup"><span data-stu-id="e5852-123">Line spacing</span></span>

![Beispiel für einen Zeilenabstand von 125Prozent](images/line-spacing.png)

<span data-ttu-id="e5852-125">Der Zeilenabstand muss mit 125Prozent des Schriftgrads berechnet und bei Bedarf auf das nächste Vielfache von Vier gerundet werden.</span><span class="sxs-lookup"><span data-stu-id="e5852-125">Line spacing should be calculated at 125% of the font size, rounding to the closest multiple of four when necessary.</span></span> <span data-ttu-id="e5852-126">Bei SegoeUI mit 15px wären 125Prozent beispielsweise 18,75px.</span><span class="sxs-lookup"><span data-stu-id="e5852-126">For example with 15px Segoe UI, 125% of 15px is 18.75px.</span></span> <span data-ttu-id="e5852-127">Wir empfehlen, den Wert aufzurunden und den Zeilenabstand auf 20px festzulegen, um dem 4px-Raster zu entsprechen.</span><span class="sxs-lookup"><span data-stu-id="e5852-127">We recommend rounding up and setting line height to 20px to stay on the 4px grid.</span></span> <span data-ttu-id="e5852-128">Dadurch wird eine gute Lesbarkeit gewährleistet, und es steht ausreichend Platz für diakritische Zeichen zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="e5852-128">This ensures a good reading experience and adequate space for diacritical marks.</span></span> <span data-ttu-id="e5852-129">Spezifische Beispiele finden Sie weiter unten im Abschnitt „Typhierarchie“.</span><span class="sxs-lookup"><span data-stu-id="e5852-129">See the Type ramp section below for specific examples.</span></span>

<span data-ttu-id="e5852-130">Wird sich größere Schrift über kleinerer Schrift befindet, muss der Abstand zwischen der letzten Grundlinie der größeren Schrift und der ersten Grundlinie der kleineren Schrift dem Zeilenabstand der größeren Schrift entsprechen.</span><span class="sxs-lookup"><span data-stu-id="e5852-130">When stacking larger type on top of smaller type, the distance from the last baseline of the larger type to the first baseline of the smaller type should be equal to the larger type’s line height.</span></span>

![Große Schrift über kleinerer Schrift](images/line-height-stacking.png)

<span data-ttu-id="e5852-132">Im XAML-Code wird dies durch Stapeln zweier [TextBlock](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.textblock.aspx)-Elemente sowie durch Festlegen des entsprechenden Rands erreicht.</span><span class="sxs-lookup"><span data-stu-id="e5852-132">In XAML, this is accomplished by stacking two [TextBlocks](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) and setting the appropriate margin.</span></span>

```xaml
<StackPanel Width="200">
    <!-- Setting a bottom margin of 3px on the header
         puts the baseline of the body text exactly 24px
         below the baseline of the header. 24px is the
         recommended line height for a 20px font size,
         which is what’s set in SubtitleTextBlockStyle.
         The bottom margin will be different for
         different font size pairings. -->
    <TextBlock
        Style="{StaticResource SubtitleTextBlockStyle}"
        Margin="0,0,0,3"
        Text="Header text" />
    <TextBlock
        Style="{StaticResource BodyTextBlockStyle}"
        TextWrapping="Wrap"
        Text="This line of text should be positioned where the above header would have wrapped." />
</StackPanel>
```


<div class="side-by-side">
<div class="side-by-side-content">
  <div class="side-by-side-content-left">
<h2><span data-ttu-id="e5852-133">Kerning und Laufweite</span><span class="sxs-lookup"><span data-stu-id="e5852-133">Kerning and tracking</span></span></h2>

<span data-ttu-id="e5852-134">Segoe ist eine humanistische Schriftart mit weicher, ansprechender Optik und organischen, offenen Formen, die von handschriftlichen Texten inspiriert sind.</span><span class="sxs-lookup"><span data-stu-id="e5852-134">Segoe is a humanist typeface, with a soft, friendly appearance, it has organic, open forms based on handwritten text.</span></span> <span data-ttu-id="e5852-135">Um eine optimale Lesbarkeit zu gewährleisten und den humanistischen Charakter zu bewahren, müssen für Kerning und Laufweite bestimmte Werte verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e5852-135">To ensure optimum legibility and maintain its humanist integrity, the kerning and tracking settings must have specific values.</span></span>

<span data-ttu-id="e5852-136">Kerning muss auf „Metrik“ und die Laufweite auf„0“ festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="e5852-136">Kerning should be set to “metrics” and tracking should be set to “0”.</span></span>
  </div>
  <div class="side-by-side-content-right">
<h2><span data-ttu-id="e5852-137">Wort- und Zeichenabstand</span><span class="sxs-lookup"><span data-stu-id="e5852-137">Word and letter spacing</span></span></h2>

<span data-ttu-id="e5852-138">Ähnlich wie bei Kerning und Laufweite werden auch beim Wort- und Zeichenabstand bestimmte Einstellungen verwendet, um eine optimale Lesbarkeit und die Wahrung des humanistischen Charakters zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="e5852-138">Similar to kerning and tracking, word spacing and letter spacing use specific settings to ensure optimum legibility and humanist integrity.</span></span>

<span data-ttu-id="e5852-139">Der Wortabstand beträgt standardmäßig immer 100Prozent. Der Zeichenabstand muss auf„0“ festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="e5852-139">Word spacing by default is always 100% and letter spacing should be set to “0”.</span></span>
  </div>
</div>
</div>
<div class="side-by-side">
<div class="side-by-side-content">
  <div class="side-by-side-content-left">
![Der Unterschied zwischen Kerning und Laufweite](images/kerning-tracking.png)  
  </div>
  <div class="side-by-side-content-right">
![Der Unterschied zwischen Wort- und Zeichenabstand.](images/word-letter.png) 
  </div>
</div>
</div>


>[!NOTE]
><span data-ttu-id="e5852-142">Verwenden Sie in einem XAML-Textsteuerelement [Typogrphy.Kerning](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.documents.typography.kerning.aspx), um das Kerning zu steuern, und [FontStretch](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Control#Windows_UI_Xaml_Controls_Control_FontStretch). um die Nachverfolgung zu steuern.</span><span class="sxs-lookup"><span data-stu-id="e5852-142">In a XAML text control use [Typogrphy.Kerning](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.documents.typography.kerning.aspx) to control kerning and [FontStretch](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Control#Windows_UI_Xaml_Controls_Control_FontStretch) to control tracking.</span></span> <span data-ttu-id="e5852-143">Typography.Kerning ist standardmäßig auf „true“ und FontStretch ist standardmäßig auf „Normal“ festgelegt. Dies sind die empfohlenen Werte.</span><span class="sxs-lookup"><span data-stu-id="e5852-143">By default Typography.Kerning is set to “true” and FontStretch is set to “Normal”, which are the recommended values.</span></span>

<div class="side-by-side">
<div class="side-by-side-content">
  <div class="side-by-side-content-left">
<h2><span data-ttu-id="e5852-144">Ausrichtung</span><span class="sxs-lookup"><span data-stu-id="e5852-144">Alignment</span></span></h2>

<span data-ttu-id="e5852-145">Im Allgemeinen wird die linksbündige Ausrichtung visueller Elemente und Spalten mit Schrift empfohlen.</span><span class="sxs-lookup"><span data-stu-id="e5852-145">Generally, we recommend that visual elements and columns of type be left-aligned.</span></span> <span data-ttu-id="e5852-146">In den meisten Fällen sorgt das Konzept „links bündig, rechts mit Flatterrand“ für eine konsistente Verankerung des Inhalts und für ein einheitliches Layout.</span><span class="sxs-lookup"><span data-stu-id="e5852-146">In most instances, this flush-left and ragged-right approach provides consistent anchoring of the content and a uniform layout.</span></span> 
  </div>
  <div class="side-by-side-content-right">
<h2><span data-ttu-id="e5852-147">Zeilenenden</span><span class="sxs-lookup"><span data-stu-id="e5852-147">Line endings</span></span></h2>

<span data-ttu-id="e5852-148">Wenn Typografie nicht linksbündig mit rechtem Flatterrand positioniert wird, versuchen Sie, gleichmäßige Zeilenenden zu erreichen, und vermeiden Sie die Verwendung von Silbentrennung.</span><span class="sxs-lookup"><span data-stu-id="e5852-148">When typography is not positioned as flush left and ragged right, try to ensure even line endings and avoid hyphenation.</span></span>
  </div>
</div>
</div>

<div class="side-by-side">
<div class="side-by-side-content">
  <div class="side-by-side-content-left">
![Zeigt linksbündigen Text.](images/alignment.png)  
  </div>
  <div class="side-by-side-content-right">
![Zeigt gleichmäßige Zeilenenden.](images/line-endings.png) 
  </div>
</div>
</div>


## <a name="paragraphs"></a><span data-ttu-id="e5852-151">Absätze</span><span class="sxs-lookup"><span data-stu-id="e5852-151">Paragraphs</span></span>

<span data-ttu-id="e5852-152">Absätze müssen als übersprungene Zeile ohne Einzug dargestellt werden, um aufeinander abgestimmte Spaltenränder zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="e5852-152">To provide aligned column edges, paragraphs should be indicated by skipping a line without indentation.</span></span>

![Vollständige Leerzeile zwischen Absätzen](images/paragraphs.png)

## <a name="character-count"></a><span data-ttu-id="e5852-154">Zeichenanzahl</span><span class="sxs-lookup"><span data-stu-id="e5852-154">Character count</span></span>

<span data-ttu-id="e5852-155">Ist eine Zeile zu kurz, muss das Auge zu oft hin und her bewegt werden, was den Lesefluss stört.</span><span class="sxs-lookup"><span data-stu-id="e5852-155">If a line is too short, the eye will have to travel left and right too often, breaking the reader’s rhythm.</span></span> <span data-ttu-id="e5852-156">Verwenden Sie daher möglichst50 bis 60Wörter pro Zeile. Dies bietet den höchsten Lesekomfort.</span><span class="sxs-lookup"><span data-stu-id="e5852-156">If possible, 50–60 letters per line is best for ease of reading.</span></span>

<span data-ttu-id="e5852-157">Segoe bietet eine breite Palette von Zeichen und zeichnet sich durch optimale Lesbarkeit bei unterschiedlichen Größen und Pixeldichten aus.</span><span class="sxs-lookup"><span data-stu-id="e5852-157">Segoe provides a wide range of characters and is designed to maintain optimal legibility in both small and large sizes as well as low and high pixel densities.</span></span> <span data-ttu-id="e5852-158">Eine optimale Anzahl von Buchstaben in einer Textspaltenzeile erhöht den Lesekomfort in einer Anwendung.</span><span class="sxs-lookup"><span data-stu-id="e5852-158">Using the optimal number of letters in a text column line ensures good legibility in an application.</span></span>

<span data-ttu-id="e5852-159">Zu lange Zeilen können für den Benutzer anstrengend und verwirrend sein.</span><span class="sxs-lookup"><span data-stu-id="e5852-159">Lines that are too long will strain the eye and may disorient the user.</span></span> <span data-ttu-id="e5852-160">Bei zu kurzen Zeilen muss das Auge zu viel hin und her bewegt werden, was sich als ermüdend erweisen kann.</span><span class="sxs-lookup"><span data-stu-id="e5852-160">Lines that are too short force the reader’s eye to travel too much and can cause fatigue.</span></span>

![Drei Absätze mit unterschiedlichen Zeilenlängen](images/character-count.png)

## <a name="hanging-text-alignment"></a><span data-ttu-id="e5852-162">Ausrichtung von hängendem Text</span><span class="sxs-lookup"><span data-stu-id="e5852-162">Hanging text alignment</span></span>

<span data-ttu-id="e5852-163">Die horizontale Ausrichtung von Symbolen mit Text kann je nach Symbolgröße und Textmenge auf unterschiedliche Arten gehandhabt werden.</span><span class="sxs-lookup"><span data-stu-id="e5852-163">The horizontal alignment of icons with text can be handled in a number of ways depending on the size of the icon and the amount of text.</span></span> <span data-ttu-id="e5852-164">Wenn der Text (einzelne Zeile oder mehrere Zeilen) die Höhe des Symbols nicht übersteigt, muss der Text vertikal zentriert werden.</span><span class="sxs-lookup"><span data-stu-id="e5852-164">When the text, either single or multiple lines, fits within the height of the icon, the text should be vertically centered.</span></span>

<span data-ttu-id="e5852-165">Sobald die Höhe des Texts die Höhe des Symbols übersteigt, muss die erste Textzeile vertikal ausgerichtet werden, und der weitere Text muss dem natürlichen Textfluss folgen.</span><span class="sxs-lookup"><span data-stu-id="e5852-165">Once the height of the text extends beyond the height of the icon, the first line of text should align vertically and the additional text should flow on naturally below.</span></span> <span data-ttu-id="e5852-166">Für höhere Großbuchstaben bzw. Zeichen mit höherer Ober- und Unterlänge gelten die gleichen Ausrichtungsrichtlinien.</span><span class="sxs-lookup"><span data-stu-id="e5852-166">When using characters with larger cap, ascender and descender heights, care should be taken to observe the same alignment guidance.</span></span>

![Mehrere Kombinationen aus Symbol und Text](images/hanging-text-alignment.png)

>[!NOTE]
><span data-ttu-id="e5852-168">Die XAML-Eigenschaft [TextBlock.TextLineBounds](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.textblock.textlinebounds.aspx) ermöglicht den Zugriff auf die Höhe von Großbuchstaben und die Metrik der Basisschriftart.</span><span class="sxs-lookup"><span data-stu-id="e5852-168">XAML’s [TextBlock.TextLineBounds](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.textblock.textlinebounds.aspx) property provides access to the cap height and baseline font metrics.</span></span> <span data-ttu-id="e5852-169">Sie kann verwendet werden, um visuell vertikal zu zentrieren oder oben ausgerichtet einzugeben.</span><span class="sxs-lookup"><span data-stu-id="e5852-169">It can be used to visually vertically center or top-align type.</span></span>

## <a name="clipping-and-ellipses"></a><span data-ttu-id="e5852-170">Beschnitt und Ellipsen</span><span class="sxs-lookup"><span data-stu-id="e5852-170">Clipping and ellipses</span></span>

<span data-ttu-id="e5852-171">Nutzen Sie standardmäßig das Beschnittkonzept, und gehen Sie davon aus, dass der Text umgebrochen wird – es sei denn, es ist etwas anderes angegeben.</span><span class="sxs-lookup"><span data-stu-id="e5852-171">Clip by default—assume that text will wrap unless the redline specifies otherwise.</span></span> <span data-ttu-id="e5852-172">Bei Verwendung von nicht umgebrochenem Text empfiehlt es sich, anstelle von Ellipsen den Beschnitt zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="e5852-172">When using non-wrapping text, we recommend clipping rather than using ellipses.</span></span> <span data-ttu-id="e5852-173">Der Beschnitt kann am Rand des Containers, am Rand des Geräts, am Rand der Bildlaufleiste usw. erfolgen.</span><span class="sxs-lookup"><span data-stu-id="e5852-173">Clipping can occur at the edge of the container, at the edge of the device, at the edge of a scrollbar, etc.</span></span>

<span data-ttu-id="e5852-174">Ausnahme: Bei Containern, die nicht klar definiert sind (also sich etwa nicht durch eine andere Hintergrundfarbe abheben), kann eine Ellipse(...) verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e5852-174">Exceptions—for containers which are not well-defined (e.g. no differentiating background color), then non-wrapping text can be redlined to use the ellipse ”…”.</span></span>

![Gerät mit abgeschnittenem Text](images/clipping.png)

## <a name="type-ramp"></a><span data-ttu-id="e5852-176">Typhierarchie</span><span class="sxs-lookup"><span data-stu-id="e5852-176">Type ramp</span></span>
<span data-ttu-id="e5852-177">Die Typhierarchie stellt eine wichtige gestalterische Beziehung zwischen Überschrift und Textkörper her und schafft damit eine klare und verständliche Hierarchie zwischen den verschiedenen Ebenen.</span><span class="sxs-lookup"><span data-stu-id="e5852-177">The type ramp establishes a crucial design relationship from headlines to body text and ensures a clear and understandable hierarchy between the different levels.</span></span> <span data-ttu-id="e5852-178">Diese Hierarchie bildet eine Struktur, die Benutzern die Navigation durch schriftliche Kommunikation erleichtert.</span><span class="sxs-lookup"><span data-stu-id="e5852-178">This hierarchy builds a structure which enables users to easily navigate through written communication.</span></span>

<div class="uwpd-image-with-caption">
    <img src="images/type-ramp.png" alt="Shows the type ramp" />
    <div><span data-ttu-id="e5852-179">Die Größe wird jeweils in effektiven Pixeln angegeben.</span><span class="sxs-lookup"><span data-stu-id="e5852-179">All sizes are in effective pixels.</span></span> <span data-ttu-id="e5852-180">Weitere Informationen finden Sie unter [Einführung in das UWP-App-Design](../layout/design-and-ui-intro.md).</span><span class="sxs-lookup"><span data-stu-id="e5852-180">For more details, see [Intro to UWP app design](../layout/design-and-ui-intro.md).</span></span></div>
</div>

>[!NOTE]
><span data-ttu-id="e5852-181">Die meisten Ebenen der Typhierarchie sind in XAML als [statische Ressourcen](https://msdn.microsoft.com/en-us/library/windows/apps/Mt187274.aspx#the_xaml_type_ramp) verfügbar, die der `*TextBlockStyle`-Benennungskonvention folgen (z.B.: `HeaderTextBlockStyle`).</span><span class="sxs-lookup"><span data-stu-id="e5852-181">Most levels of the ramp are available as XAML [static resources](https://msdn.microsoft.com/en-us/library/windows/apps/Mt187274.aspx#the_xaml_type_ramp) that follow the `*TextBlockStyle` naming convention (ex: `HeaderTextBlockStyle`).</span></span>


<!--
<div class="microsoft-internal-note">
SubtitleAlt, BaseAlt, and CaptionAlt are not currently included. You can create the styles in your own app following the code snippets in the above link. Also note that XAML does not currently match the line height exactly.
</div>
-->


## <a name="primary-and-secondary-text"></a><span data-ttu-id="e5852-182">Primärer und sekundärer Text</span><span class="sxs-lookup"><span data-stu-id="e5852-182">Primary and secondary text</span></span>

<span data-ttu-id="e5852-183">Zur Erweiterung der Typhierarchie kann die Deckkraft des sekundären Texts auf 60Prozent festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="e5852-183">To create additional hierarchy beyond the type ramp, set secondary text to 60% opacity.</span></span> <span data-ttu-id="e5852-184">In der [Farbschemapalette](color.md#color-theming) wird dafür „BaseMedium“ verwendet.</span><span class="sxs-lookup"><span data-stu-id="e5852-184">In the [theming color palette](color.md#color-theming), you would use BaseMedium.</span></span> <span data-ttu-id="e5852-185">Der primäre Text muss immer eine Deckkraft von 100Prozent (BaseHigh) besitzen.</span><span class="sxs-lookup"><span data-stu-id="e5852-185">Primary text should always be at 100% opacity, or BaseHigh.</span></span>

<!-- Need new images
![Two phone apps using SubtitleAlt](images/type-ramp-example-2.png)
Recommended use of SubtitleAlt. Also note the primary and secondary text usage in list items.

![Two phone apps using CaptionAlt](images/type-ramp-example-1.png)
Recommended use of CaptionAlt.
-->

## <a name="all-caps-titles"></a><span data-ttu-id="e5852-186">Titel in Großbuchstaben</span><span class="sxs-lookup"><span data-stu-id="e5852-186">All caps titles</span></span>

<span data-ttu-id="e5852-187">Bestimmte Seitentitel sollten in GROSSBUCHSTABEN angegeben werden, um die Hierarchie um eine weitere Dimension zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="e5852-187">Certain page titles should be in ALL CAPS to add yet another dimension of hierarchy.</span></span> <span data-ttu-id="e5852-188">Diese Titel müssen „BaseAlt“ und einen Zeichenabstand von 0,075em verwenden.</span><span class="sxs-lookup"><span data-stu-id="e5852-188">These titles should use BaseAlt with the character spacing set to 75 thousandths of an em.</span></span> <span data-ttu-id="e5852-189">Dies kann auch bei der App-Navigation hilfreich sein.</span><span class="sxs-lookup"><span data-stu-id="e5852-189">This treatment may also be used to help with app navigation.</span></span>

<span data-ttu-id="e5852-190">In bestimmten Sprachen ändert sich durch eine Großschreibung jedoch die Bedeutung von Eigennamen. Daher dürfen auf Namen oder Benutzereingaben basierende Seitentitel *nicht* in Großbuchstaben umgewandelt werden.</span><span class="sxs-lookup"><span data-stu-id="e5852-190">However, proper names change their meaning when capitalized in certain languages, so any page titles based on names or user input should *not* be converted to all caps.</span></span>


<!-- Need new images
![Shows several apps where they should and should not use all caps](images/all-caps.png)
Green shows where all caps should be used. Red shows where it should not.
-->

## <a name="dos-and-donts"></a><span data-ttu-id="e5852-191">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="e5852-191">Do’s and don’ts</span></span>
* <span data-ttu-id="e5852-192">Verwenden Sie „Body“ für die meisten Texte.</span><span class="sxs-lookup"><span data-stu-id="e5852-192">Use Body for most text</span></span>
* <span data-ttu-id="e5852-193">Verwenden Sie „Base“ für Titel mit begrenztem Platz.</span><span class="sxs-lookup"><span data-stu-id="e5852-193">Use Base for titles when space is constrained</span></span>
* <span data-ttu-id="e5852-194">Integrieren Sie „SubtitleAlt“, um durch Hervorhebung des übergeordneten Inhalts einen Kontrast und eine Hierarchie zu schaffen.</span><span class="sxs-lookup"><span data-stu-id="e5852-194">Incorporate SubtitleAlt to create contrast and hierarchy by emphasizing top level content</span></span>
* <span data-ttu-id="e5852-195">Verwenden Sie „Caption“ nicht für lange Zeichenfolgen oder Hauptaktionen.</span><span class="sxs-lookup"><span data-stu-id="e5852-195">Don’t use Caption for long strings or any primary action</span></span>
* <span data-ttu-id="e5852-196">Verwenden Sie „Header“ oder „Subheader“ nicht, wenn der Text umgebrochen werden muss.</span><span class="sxs-lookup"><span data-stu-id="e5852-196">Don’t use Header or Subheader if text needs to wrap</span></span>
* <span data-ttu-id="e5852-197">Verwenden Sie „Subtitle“ und „SubtitleAlt“ nicht auf der gleichen Seite.</span><span class="sxs-lookup"><span data-stu-id="e5852-197">Don’t combine Subtitle and SubtitleAlt on the same page</span></span>


## <a name="related-articles"></a><span data-ttu-id="e5852-198">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="e5852-198">Related articles</span></span>

* [<span data-ttu-id="e5852-199">Textsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="e5852-199">Text controls</span></span>](../controls-and-patterns/text-controls.md)
* [<span data-ttu-id="e5852-200">Schriftarten</span><span class="sxs-lookup"><span data-stu-id="e5852-200">Fonts</span></span>](fonts.md)
* [<span data-ttu-id="e5852-201">Segoe MDL2-Symbole</span><span class="sxs-lookup"><span data-stu-id="e5852-201">Segoe MDL2 icons</span></span>](segoe-ui-symbol-font.md)
