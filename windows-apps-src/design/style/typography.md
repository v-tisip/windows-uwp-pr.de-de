---
description: Erfahren Sie, wie Sie die Typografie in Ihrer App verwenden, um Benutzern Inhalte leicht verständlich zu machen.
title: Typografie in UWP-Apps
ms.date: 04/06/2018
ms.topic: article
keywords: windows 10, uwp
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: 0943273dab239669be75b30070222d698246aa41
ms.sourcegitcommit: d2517e522cacc5240f7dffd5bc1eaa278e3f7768
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "8339688"
---
# <a name="typography"></a><span data-ttu-id="fe271-104">Typografie</span><span class="sxs-lookup"><span data-stu-id="fe271-104">Typography</span></span>

![Favoritenbild](images/header-typography.svg)

<span data-ttu-id="fe271-106">Typografie muss übersichtlich sein, da sie zur visuellen Darstellung von Sprache dient, um Informationen zu kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="fe271-106">As the visual representation of language, typography’s main task is to communicate information.</span></span> <span data-ttu-id="fe271-107">Ihr Stil darf diesem Ziel nie im Wege stehen.</span><span class="sxs-lookup"><span data-stu-id="fe271-107">Its style should never get in the way of that goal.</span></span> <span data-ttu-id="fe271-108">In diesem Artikel erläutern wir, wie Sie die Typografie in Ihre UWP-App formatieren, damit Benutzer Inhalte schnell und effizient verstehen.</span><span class="sxs-lookup"><span data-stu-id="fe271-108">In this article, we'll discuss how to style typography in your UWP app to help users understand content easily and efficiently.</span></span>

## <a name="font"></a><span data-ttu-id="fe271-109">Font</span><span class="sxs-lookup"><span data-stu-id="fe271-109">Font</span></span>

<span data-ttu-id="fe271-110">Verwenden Sie eine Schriftart in der gesamten Benutzeroberfläche Ihrer App. Es wird empfohlen, wenn möglich, die Standardschriftart für UWP-Apps **Segoe UI** zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="fe271-110">You should use one font throughout your app's UI, and we recommend sticking with the default font for UWP apps, **Segoe UI**.</span></span> <span data-ttu-id="fe271-111">Sie wurde entwickelt, um eine optimale Lesbarkeit für Größe und Pixeldichte zu wahren und bietet eine klare, ansprechende und offene Ästhetik, die den Inhalt des Systems ergänzt.</span><span class="sxs-lookup"><span data-stu-id="fe271-111">It's designed to maintain optimal legibility across sizes and pixel densities and offers a clean, light, and open aesthetic that complements the content of the system.</span></span>

![Beispieltext für die Schriftart „SegoeUI“](images/type/segoe-sample.svg)

<span data-ttu-id="fe271-113">Weitere Informationen zum Anzeigen anderer Sprachen als Englisch oder um eine andere Schriftart für Ihre App auszuwählen finden Sie unter [Sprachen](#Languages) und [Schriftarten](#Fonts) für unsere empfohlenen Schriftarten für UWP-Apps.</span><span class="sxs-lookup"><span data-stu-id="fe271-113">To display non-English languages or to select a different font for your app, please see [Languages](#Languages) and [Fonts](#Fonts) for our recommended fonts for UWP apps.</span></span>

:::row:::
    :::column:::
        ![do](images/do.svg)
        Pick one font for your UI.
    :::column-end:::
    :::column:::
        ![don't](images/dont.svg)
        Don't mix multiple fonts.
    :::column-end:::
:::row-end:::

## <a name="size-and-scaling"></a><span data-ttu-id="fe271-114">Größe und Skalierung</span><span class="sxs-lookup"><span data-stu-id="fe271-114">Size and scaling</span></span>

<span data-ttu-id="fe271-115">Schriftgrade in UWP-Apps werden automatisch auf allen Geräten skaliert.</span><span class="sxs-lookup"><span data-stu-id="fe271-115">Font sizes in UWP apps automatically scale on all devices.</span></span> <span data-ttu-id="fe271-116">Mit dem Skalierungsalgorithmus wird sichergestellt, dass der Schriftgrad 24 Pixel auf einem 3 Meter entfernten Surface Hub genauso lesbar ist wie der Schriftgrad 24 Pixel auf einem 5-Zoll-Smartphone, das nur einige Zentimeter entfernt ist.</span><span class="sxs-lookup"><span data-stu-id="fe271-116">The scaling algorithm ensures that a 24 px font on Surface Hub 10 feet away is just as legible as a 24 px font on 5" phone that's a few inches away.</span></span>

![Sichtabstände für verschiedene Geräte](images/type/scaling-chart.svg)

<span data-ttu-id="fe271-118">Aufgrund der Funktionsweise der Skalierung, entwerfen Sie in effektiven Pixeln, nicht in den tatsächlichen physischen Pixeln, und Sie müssen den Schriftgrad für unterschiedliche Bildschirmgrößen und Auflösungen nicht ändern.</span><span class="sxs-lookup"><span data-stu-id="fe271-118">Because of how the scaling system works, you're designing in effective pixels, not actual physical pixels, and you shouldn't have to alter font sizes for different screens sizes or resolutions.</span></span>

:::row:::
    :::column:::
        ![do](images/do.svg)
        Follow the UWP [type ramp](#type-ramp) sizing.
    :::column-end:::
    :::column:::
        ![don't](images/dont.svg)
        Use a font size smaller than 12 px.
    :::column-end:::
:::row-end:::

## <a name="hierarchy"></a><span data-ttu-id="fe271-119">Hierarchie</span><span class="sxs-lookup"><span data-stu-id="fe271-119">Hierarchy</span></span>

:::row:::
    :::column:::
        Users rely on visual hierarchy when scanning a page: headers summarize content, and body text provides more detail. To create a clear visual hierarchy in your app, follow the UWP type ramp.
    :::column-end:::
    :::column:::
        ![text block styles](images/type/type-hierarchy.svg)
    :::column-end:::
:::row-end:::

### <a name="type-ramp"></a><span data-ttu-id="fe271-120">Typhierarchie</span><span class="sxs-lookup"><span data-stu-id="fe271-120">Type ramp</span></span>

<span data-ttu-id="fe271-121">Die UWP-Typhierarchie stellt wichtige Beziehungen zwischen den Schriftschnitte auf einer Seite her, damit der Benutzer den Inhalt einfach lesen kann.</span><span class="sxs-lookup"><span data-stu-id="fe271-121">The UWP type ramp establishes crucial relationships between the type styles on a page, helping users read content easily.</span></span> <span data-ttu-id="fe271-122">Alle Größen werden in effektiven Pixeln angegeben und sind für UWP-Apps optimiert, die auf allen Geräten ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="fe271-122">All sizes are in effective pixels and are optimized for UWP apps running on all devices.</span></span>

![Typhierarchie](images/type/type-ramp.svg)

### <a name="using-the-type-ramp"></a><span data-ttu-id="fe271-124">Die Typhierarchie verwenden</span><span class="sxs-lookup"><span data-stu-id="fe271-124">Using the type ramp</span></span>

:::row:::
    :::column:::
        You can access levels of the type ramp as XAML [static resources](../controls-and-patterns/xaml-theme-resources.md#the-xaml-type-ramp). The styles follow the `*TextBlockStyle` naming convention.
    :::column-end:::
    :::column:::
        ![text block styles](images/type/text-block-type-ramp.svg)
    :::column-end:::
:::row-end:::

```XAML
<TextBlock Text="Header" Style="{StaticResource HeaderTextBlockStyle}"/>
<TextBlock Text="SubHeader" Style="{StaticResource SubheaderTextBlockStyle}"/>
<TextBlock Text="Title" Style="{StaticResource TitleTextBlockStyle}"/>
<TextBlock Text="SubTitle" Style="{StaticResource SubtitleTextBlockStyle}"/>
<TextBlock Text="Base" Style="{StaticResource BaseTextBlockStyle}"/>
<TextBlock Text="Body" Style="{StaticResource BodyTextBlockStyle}"/>
<TextBlock Text="Caption" Style="{StaticResource CaptionTextBlockStyle}"/>
```

:::row:::
    :::column:::
        ![do](images/do.svg)
        Use "Body" for most text.

        Use "Base" for titles when space is constrained.
    :::column-end:::
    :::column:::
        ![don't](images/dont.svg)
        Use "Caption" for primary action or any long strings.

        Use "Header" or "Subheader" if text needs to wrap.
    :::column-end:::
:::row-end:::

## <a name="alignment"></a><span data-ttu-id="fe271-125">Ausrichtung</span><span class="sxs-lookup"><span data-stu-id="fe271-125">Alignment</span></span>

<span data-ttu-id="fe271-126">Standardmäßig ist das [TextAlignment](https://docs.microsoft.com/uwp/api/windows.ui.xaml.textalignment) links. In den meisten Fällen sorgt das Konzept „links bündig, rechts mit Flatterrand“ für eine konsistente Verankerung des Inhalts und für ein einheitliches Layout.</span><span class="sxs-lookup"><span data-stu-id="fe271-126">The default [TextAlignment](https://docs.microsoft.com/uwp/api/windows.ui.xaml.textalignment) is Left, and in most instances, flush-left and ragged right provides consistent anchoring of the content and a uniform layout.</span></span> <span data-ttu-id="fe271-127">Weitere Informationen für RTL-Sprachen finden Sie unter [Anpassen von Layout und Schriftarten zur Globalisierungsunterstützung](../globalizing/adjust-layout-and-fonts--and-support-rtl.md).</span><span class="sxs-lookup"><span data-stu-id="fe271-127">For RTL languages, see [Adjusting layout and fonts to support globalization](../globalizing/adjust-layout-and-fonts--and-support-rtl.md).</span></span>

![Zeigt linksbündigen Text.](images/type/alignment.svg)

```xaml
<TextBlock TextAlignment="Left">
```

## <a name="character-count"></a><span data-ttu-id="fe271-129">Zeichenanzahl</span><span class="sxs-lookup"><span data-stu-id="fe271-129">Character count</span></span>

:::row:::
    :::column:::
        ![do](images/do.svg)
        Keep to 50–60 letters per line for ease of reading.
    :::column-end:::
    :::column:::
        ![don't](images/dont.svg)
        Less than 20 characters or more than 60 characters per line is difficult to read.
    :::column-end:::
:::row-end:::

## <a name="clipping-and-ellipses"></a><span data-ttu-id="fe271-130">Beschnitt und Ellipsen</span><span class="sxs-lookup"><span data-stu-id="fe271-130">Clipping and ellipses</span></span>

<span data-ttu-id="fe271-131">Wenn die Textmenge den verfügbaren Speicherplatz überschreitet, wird empfohlen, den Text zuzuschneiden, was das Standardverhalten der meisten [UWP-Textsteuerelemente](../controls-and-patterns/text-controls.md)ist.</span><span class="sxs-lookup"><span data-stu-id="fe271-131">When the amount of text extends beyond the space available, we recommend clipping text, which is the default behavior of most [UWP text controls](../controls-and-patterns/text-controls.md).</span></span>

![Gerät mit abgeschnittenem Text](images/type/clipping.svg)

```xaml
<TextBlock TextWrapping="WrapWholeWords" TextTrimming="Clip"/>
```

:::row:::
    :::column:::
        ![do](images/do.svg)
        Clip text, and wrap if multiple lines are enabled.
    :::column-end:::
    :::column:::
        ![don't](images/dont.svg)
        Use ellipses to avoid visual clutter.
    :::column-end:::
:::row-end:::

<span data-ttu-id="fe271-133">**Hinweis**: Bei Containern, die nicht klar definiert sind (also sich etwa nicht durch eine andere Hintergrundfarbe abheben) oder wenn ein Link zu mehr Text existiert, kann eine Ellipse verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="fe271-133">**Note**: If containers are not well-defined (e.g. no differentiating background color), or when there is a link to see more text, then use ellipses.</span></span>

## <a name="languages"></a><span data-ttu-id="fe271-134">Sprachen</span><span class="sxs-lookup"><span data-stu-id="fe271-134">Languages</span></span> 

<span data-ttu-id="fe271-135">Segoe UI ist unsere Schriftart für Englisch, für europäische Sprachen, Griechisch, Hebräisch, Armenisch, Georgisch und Arabisch.</span><span class="sxs-lookup"><span data-stu-id="fe271-135">Segoe UI is our font for English, European languages, Greek, Hebrew, Armenian, Georgian, and Arabic.</span></span> <span data-ttu-id="fe271-136">Lesen Sie die folgenden Empfehlungen für andere Sprachen.</span><span class="sxs-lookup"><span data-stu-id="fe271-136">For other languages, see the following recommendations.</span></span>

### <a name="globalizinglocalizing-fonts"></a><span data-ttu-id="fe271-137">Globalisierung/Lokalisierung von Schriftarten</span><span class="sxs-lookup"><span data-stu-id="fe271-137">Globalizing/localizing fonts</span></span>

<span data-ttu-id="fe271-138">Verwenden Sie die [LanguageFont-Schriftartenersetzungs-APIs](https://docs.microsoft.com/uwp/api/Windows.Globalization.Fonts.LanguageFont) für den programmgesteuerten Zugriff auf die Empfohlenen Einstellungen für Familie, Grad, Breite und Schnitt der Schriftart für eine spezielle Sprache.</span><span class="sxs-lookup"><span data-stu-id="fe271-138">Use the [LanguageFont font-mapping APIs](https://docs.microsoft.com/uwp/api/Windows.Globalization.Fonts.LanguageFont) for programmatic access to the recommended font family, size, weight, and style for a particular language.</span></span> <span data-ttu-id="fe271-139">Das LanguageFont-Objekt ermöglicht den Zugriff auf die richtigen Schriftartinformationen für verschiedene Inhaltskategorien: UI-Kopfzeilen, Benachrichtigungen, Textkörper und Schriftarten für den Textkörper, die vom Benutzer bearbeitet werden können.</span><span class="sxs-lookup"><span data-stu-id="fe271-139">The LanguageFont object provides access to the correct font info for various categories of content including UI headers, notifications, body text, and user-editable document body fonts.</span></span> <span data-ttu-id="fe271-140">Weitere Informationen finden Sie unter [Anpassen von Layout und Schriftarten zur Globalisierungsunterstützung](../globalizing/adjust-layout-and-fonts--and-support-rtl.md).</span><span class="sxs-lookup"><span data-stu-id="fe271-140">For more info, see [Adjusting layout and fonts to support globalization](../globalizing/adjust-layout-and-fonts--and-support-rtl.md).</span></span>

### <a name="fonts-for-non-latin-languages"></a><span data-ttu-id="fe271-141">Schriftarten für nicht lateinische Sprachen</span><span class="sxs-lookup"><span data-stu-id="fe271-141">Fonts for non-Latin languages</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="fe271-142">Schriftfamilie</span><span class="sxs-lookup"><span data-stu-id="fe271-142">Font-family</span></span></th>
<th align="left"><span data-ttu-id="fe271-143">Stile</span><span class="sxs-lookup"><span data-stu-id="fe271-143">Styles</span></span></th>
<th align="left"><span data-ttu-id="fe271-144">Hinweise</span><span class="sxs-lookup"><span data-stu-id="fe271-144">Notes</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="font-family: Embrima;"><span data-ttu-id="fe271-145">Ebrima</span><span class="sxs-lookup"><span data-stu-id="fe271-145">Ebrima</span></span></td>
<td align="left"><span data-ttu-id="fe271-146">Normal, fett</span><span class="sxs-lookup"><span data-stu-id="fe271-146">Regular, Bold</span></span></td>
<td align="left"><span data-ttu-id="fe271-147">Benutzeroberflächen-Schriftart für afrikanische Schriften (Äthiopisch, N'Ko, Osmanya, Tifinagh, Vai).</span><span class="sxs-lookup"><span data-stu-id="fe271-147">User-interface font for African scripts (Ethiopic, N'Ko, Osmanya, Tifinagh, Vai).</span></span></td>
</tr>
<tr class="even">
<td style="font-family: Gadugi;"><span data-ttu-id="fe271-148">Gadugi</span><span class="sxs-lookup"><span data-stu-id="fe271-148">Gadugi</span></span></td>
<td align="left"><span data-ttu-id="fe271-149">Normal, fett</span><span class="sxs-lookup"><span data-stu-id="fe271-149">Regular, Bold</span></span></td>
<td align="left"><span data-ttu-id="fe271-150">Benutzeroberflächen-Schriftart für nordamerikanische Schriften (Kanadische Silbenschrift, Cherokee).</span><span class="sxs-lookup"><span data-stu-id="fe271-150">User-interface font for North American scripts (Canadian Syllabics, Cherokee).</span></span></td>
</tr>
<tr class="odd">
<td align="left" style="font-family: Leelawadee UI;"><span data-ttu-id="fe271-151">LeelawadeeUI</span><span class="sxs-lookup"><span data-stu-id="fe271-151">Leelawadee UI</span></span></td>
<td align="left"><span data-ttu-id="fe271-152">Normal, Semilight, fett</span><span class="sxs-lookup"><span data-stu-id="fe271-152">Regular, Semilight, Bold</span></span></td>
<td align="left"><span data-ttu-id="fe271-153">Benutzeroberflächen-Schriftart für südostasiatische Schriften (Buginesisch, Laotisch, Khmer, Thailändisch).</span><span class="sxs-lookup"><span data-stu-id="fe271-153">User-interface font for Southeast Asian scripts (Buginese, Lao, Khmer, Thai).</span></span></td>
</tr>
<tr class="odd">
<td align="left" style="font-family: Malgun Gothic;"><span data-ttu-id="fe271-154">Malgun Gothic</span><span class="sxs-lookup"><span data-stu-id="fe271-154">Malgun Gothic</span></span></td>
<td align="left"><span data-ttu-id="fe271-155">Regular</span><span class="sxs-lookup"><span data-stu-id="fe271-155">Regular</span></span></td>
<td align="left"><span data-ttu-id="fe271-156">Benutzeroberflächen-Schriftart für Koreanisch.</span><span class="sxs-lookup"><span data-stu-id="fe271-156">User-interface font for Korean.</span></span></td>
</tr>
<tr class="even">
<td align="left" style="font-family: Microsoft JhengHei UI;"><span data-ttu-id="fe271-157">Microsoft JhengHei UI</span><span class="sxs-lookup"><span data-stu-id="fe271-157">Microsoft JhengHei UI</span></span></td>
<td align="left"><span data-ttu-id="fe271-158">Normal, fett, Light</span><span class="sxs-lookup"><span data-stu-id="fe271-158">Regular, Bold, Light</span></span></td>
<td align="left"><span data-ttu-id="fe271-159">Benutzeroberflächen-Schriftart für Chinesisch (traditionell).</span><span class="sxs-lookup"><span data-stu-id="fe271-159">User-interface font for Traditional Chinese.</span></span></td>
</tr>
<tr class="odd">
<td align="left" style="font-family: Microsoft YaHei UI;"><span data-ttu-id="fe271-160">Microsoft YaHei UI</span><span class="sxs-lookup"><span data-stu-id="fe271-160">Microsoft YaHei UI</span></span></td>
<td align="left"><span data-ttu-id="fe271-161">Normal, fett, Light</span><span class="sxs-lookup"><span data-stu-id="fe271-161">Regular, Bold, Light</span></span></td>
<td align="left"><span data-ttu-id="fe271-162">Benutzeroberflächen-Schriftart für Chinesisch (vereinfacht).</span><span class="sxs-lookup"><span data-stu-id="fe271-162">User-interface font for Simplified Chinese.</span></span></td>
</tr>
<tr class="odd">
<td align="left" style="font-family: Myanmar Text;"><span data-ttu-id="fe271-163">Myanmar Text</span><span class="sxs-lookup"><span data-stu-id="fe271-163">Myanmar Text</span></span></td>
<td align="left"><span data-ttu-id="fe271-164">Regular</span><span class="sxs-lookup"><span data-stu-id="fe271-164">Regular</span></span></td>
<td align="left"><span data-ttu-id="fe271-165">Fallbackschriftart für die Myanmar-Schrift.</span><span class="sxs-lookup"><span data-stu-id="fe271-165">Fallback font for Myanmar script.</span></span></td>
</tr>
<tr class="even">
<td align="left" style="font-family: Nirmala UI;"><span data-ttu-id="fe271-166">Nirmala UI</span><span class="sxs-lookup"><span data-stu-id="fe271-166">Nirmala UI</span></span></td>
<td align="left"><span data-ttu-id="fe271-167">Normal, Semilight, fett</span><span class="sxs-lookup"><span data-stu-id="fe271-167">Regular, Semilight, Bold</span></span></td>
<td align="left"><span data-ttu-id="fe271-168">Benutzeroberflächen-Schriftart für südasiatische Schriften (Bangla, Devanagari, Gujarati, Gurmukhi, Kannada, Malayalam, Odia, Ol Chiki, Singhalesisch, Sora Sompeng, Tamil, Telugu)</span><span class="sxs-lookup"><span data-stu-id="fe271-168">User-interface font for South Asian scripts (Bangla, Devanagari, Gujarati, Gurmukhi, Kannada, Malayalam, Odia, Ol Chiki, Sinhala, Sora Sompeng, Tamil, Telugu)</span></span></td>
</tr>
<tr class="odd">
<td align="left" style="font-family: SimSun;"><span data-ttu-id="fe271-169">SimSun</span><span class="sxs-lookup"><span data-stu-id="fe271-169">SimSun</span></span></td>
<td align="left"><span data-ttu-id="fe271-170">Regular</span><span class="sxs-lookup"><span data-stu-id="fe271-170">Regular</span></span></td>
<td align="left"><span data-ttu-id="fe271-171">Eine ältere chinesische UI-Schriftart.</span><span class="sxs-lookup"><span data-stu-id="fe271-171">A legacy Chinese UI font.</span></span> </td>
</tr>
<tr class="even">
<td align="left" style="font-family: Yu Gothic UI;"><span data-ttu-id="fe271-172">Yu Gothic UI</span><span class="sxs-lookup"><span data-stu-id="fe271-172">Yu Gothic UI</span></span></td>
<td align="left"><span data-ttu-id="fe271-173">Light, Semilight, normal, Semibold, fett</span><span class="sxs-lookup"><span data-stu-id="fe271-173">Light, Semilight, Regular, Semibold, Bold</span></span></td>
<td align="left"><span data-ttu-id="fe271-174">Benutzeroberflächen-Schriftart für Japanisch.</span><span class="sxs-lookup"><span data-stu-id="fe271-174">User-interface font for Japanese.</span></span></td>
</tr>
</tbody>
</table>

## <a name="fonts"></a><span data-ttu-id="fe271-175">Schriftarten</span><span class="sxs-lookup"><span data-stu-id="fe271-175">Fonts</span></span>

### <a name="sans-serif-fonts"></a><span data-ttu-id="fe271-176">Serifenlose Schriftarten</span><span class="sxs-lookup"><span data-stu-id="fe271-176">Sans-serif fonts</span></span>

<span data-ttu-id="fe271-177">Serifenlose Schriftarten eignen sich für Überschriften und UI-Elemente.</span><span class="sxs-lookup"><span data-stu-id="fe271-177">Sans-serif fonts are a great choice for headings and UI elements.</span></span> 

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="fe271-178">Schriftfamilie</span><span class="sxs-lookup"><span data-stu-id="fe271-178">Font-family</span></span></th>
<th align="left"><span data-ttu-id="fe271-179">Stile</span><span class="sxs-lookup"><span data-stu-id="fe271-179">Styles</span></span></th>
<th align="left"><span data-ttu-id="fe271-180">Hinweise</span><span class="sxs-lookup"><span data-stu-id="fe271-180">Notes</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left" style="font-family: Arial;"><span data-ttu-id="fe271-181">Arial</span><span class="sxs-lookup"><span data-stu-id="fe271-181">Arial</span></span></td>
<td align="left"><span data-ttu-id="fe271-182">Normal, kursiv, fett, fett kursiv, schwarz</span><span class="sxs-lookup"><span data-stu-id="fe271-182">Regular, Italic, Bold, Bold Italic, Black</span></span></td>
<td align="left"><span data-ttu-id="fe271-183">Unterstützung für europäische und nahöstliche Schriften (Lateinisch, Griechisch, Kyrillisch, Arabisch, Armenisch und Hebräisch). Die Schriftbreite „Black“ unterstützt nur europäische Schriften.</span><span class="sxs-lookup"><span data-stu-id="fe271-183">Supports European and Middle Eastern scripts (Latin, Greek, Cyrillic, Arabic, Armenian, and Hebrew) Black weight supports European scripts only.</span></span></td>
</tr>
<tr class="even">
<td align="left" style="font-family: Calibri;"><span data-ttu-id="fe271-184">Calibri</span><span class="sxs-lookup"><span data-stu-id="fe271-184">Calibri</span></span></td>
<td align="left"><span data-ttu-id="fe271-185">Normal, kursiv, fett, fett kursiv, dünn, dünn kursiv</span><span class="sxs-lookup"><span data-stu-id="fe271-185">Regular, Italic, Bold, Bold Italic, Light, Light Italic</span></span></td>
<td align="left"><span data-ttu-id="fe271-186">Unterstützung für europäische und nahöstliche Schriften (Lateinisch, Griechisch, Kyrillisch, Arabisch und Hebräisch).</span><span class="sxs-lookup"><span data-stu-id="fe271-186">Supports European and Middle Eastern scripts (Latin, Greek, Cyrillic, Arabic and Hebrew).</span></span> <span data-ttu-id="fe271-187">Arabisch nur in gerader Schrift verfügbar.</span><span class="sxs-lookup"><span data-stu-id="fe271-187">Arabic available in the uprights only.</span></span></td>
</tr>
<td style="font-family: Consolas;"><span data-ttu-id="fe271-188">Consolas</span><span class="sxs-lookup"><span data-stu-id="fe271-188">Consolas</span></span></td>
<td><span data-ttu-id="fe271-189">Normal, kursiv, fett, fett kursiv</span><span class="sxs-lookup"><span data-stu-id="fe271-189">Regular, Italic, Bold, Bold Italic</span></span></td>
<td><span data-ttu-id="fe271-190">Schriftart mit fester Breite mit Unterstützung für europäische Schriften (Lateinisch, Griechisch und Kyrillisch).</span><span class="sxs-lookup"><span data-stu-id="fe271-190">Fixed width font that supports European scripts (Latin, Greek and Cyrillic).</span></span></td>
</tr>

<tr>
<td style="font-family: Segoe UI;"><span data-ttu-id="fe271-191">Segoe UI</span><span class="sxs-lookup"><span data-stu-id="fe271-191">Segoe UI</span></span></td>
<td><span data-ttu-id="fe271-192">Normal, kursiv, Light kursiv, Black kursiv, fett, fett kursiv, Light, Semilight, Semibold, Black</span><span class="sxs-lookup"><span data-stu-id="fe271-192">Regular, Italic, Light Italic, Black Italic, Bold, Bold Italic, Light, Semilight, Semibold, Black</span></span></td>
<td><span data-ttu-id="fe271-193">Benutzeroberflächen-Schriftart für europäische und nahöstliche Schriften (Arabisch, Armenisch, Kyrillisch, Georgisch, Griechisch, Hebräisch, Lateinisch) und auch Lisu-Schrift.</span><span class="sxs-lookup"><span data-stu-id="fe271-193">User-interface font for European and Middle East scripts (Arabic, Armenian, Cyrillic, Georgian, Greek, Hebrew, Latin), and also Lisu script.</span></span></td>
</tr>

<tr class="even">
<td style="font-family: Selawik;"><span data-ttu-id="fe271-194">Selawik</span><span class="sxs-lookup"><span data-stu-id="fe271-194">Selawik</span></span></td>
<td align="left"><span data-ttu-id="fe271-195">Normal, Semilight, Light, fett, Semibold</span><span class="sxs-lookup"><span data-stu-id="fe271-195">Regular, Semilight, Light, Bold, Semibold</span></span></td>
<td align="left"><span data-ttu-id="fe271-196">Open-Source-Schriftart, die metrisch kompatibel mit SegoeUI ist. Vorgesehen für Apps auf anderen Plattformen, auf denen SegoeUI nicht verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="fe271-196">An open-source font that's metrically compatible with Segoe UI, intended for apps on other platforms that don’t want to bundle Segoe UI.</span></span> <a href="https://github.com/Microsoft/Selawik"><span data-ttu-id="fe271-197">Laden Sie Selawik über GitHub herunter.</span><span class="sxs-lookup"><span data-stu-id="fe271-197">Get Selawik on GitHub.</span></span></a></td>
</tr>

</tbody>
</table>

### <a name="serif-fonts"></a><span data-ttu-id="fe271-198">Serifenschriftarten</span><span class="sxs-lookup"><span data-stu-id="fe271-198">Serif fonts</span></span>

<span data-ttu-id="fe271-199">Mit Serifenschriftarten lassen sich größere Textmengen gut darstellen.</span><span class="sxs-lookup"><span data-stu-id="fe271-199">Serif fonts are good for presenting large amounts of text.</span></span> 

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="fe271-200">Schriftfamilie</span><span class="sxs-lookup"><span data-stu-id="fe271-200">Font-family</span></span></th>
<th align="left"><span data-ttu-id="fe271-201">Stile</span><span class="sxs-lookup"><span data-stu-id="fe271-201">Styles</span></span></th>
<th align="left"><span data-ttu-id="fe271-202">Hinweise</span><span class="sxs-lookup"><span data-stu-id="fe271-202">Notes</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="font-family: Cambria;"><span data-ttu-id="fe271-203">Cambria</span><span class="sxs-lookup"><span data-stu-id="fe271-203">Cambria</span></span></td>
<td align="left"><span data-ttu-id="fe271-204">Regular</span><span class="sxs-lookup"><span data-stu-id="fe271-204">Regular</span></span></td>
<td align="left"><span data-ttu-id="fe271-205">Serifenschriftart mit Unterstützung für europäischen Schriften (Lateinisch, Griechisch, Kyrillisch).</span><span class="sxs-lookup"><span data-stu-id="fe271-205">Serif font that supports European scripts (Latin, Greek, Cyrillic).</span></span></td>
</tr>
<tr class="even">
<td style="font-family: Courier New;"><span data-ttu-id="fe271-206">Courier New</span><span class="sxs-lookup"><span data-stu-id="fe271-206">Courier New</span></span></td>
<td align="left"><span data-ttu-id="fe271-207">Normal, kursiv, fett, fett kursiv</span><span class="sxs-lookup"><span data-stu-id="fe271-207">Regular, Italic, Bold, Bold Italic</span></span></td>
<td align="left"><span data-ttu-id="fe271-208">Serifenschriftart mit fester Breite und Unterstützung für europäische und nahöstliche Schriften (Lateinisch, Griechisch, Kyrillisch, Arabisch, Armenisch und Hebräisch).</span><span class="sxs-lookup"><span data-stu-id="fe271-208">Serif fixed width font supports European and Middle Eastern scripts (Latin, Greek, Cyrillic, Arabic, Armenian, and Hebrew).</span></span></td>
</tr>
<tr class="odd">
<td style="font-family: Georgia;"><span data-ttu-id="fe271-209">Georgia</span><span class="sxs-lookup"><span data-stu-id="fe271-209">Georgia</span></span></td>
<td align="left"><span data-ttu-id="fe271-210">Normal, kursiv, fett, fett kursiv</span><span class="sxs-lookup"><span data-stu-id="fe271-210">Regular, Italic, Bold, Bold Italic</span></span></td>
<td align="left"><span data-ttu-id="fe271-211">Unterstützung für europäische Schriften (Lateinisch, Griechisch und Kyrillisch).</span><span class="sxs-lookup"><span data-stu-id="fe271-211">Supports European scripts (Latin, Greek and Cyrillic).</span></span></td>
</tr>

<tr class="even">
<td style="font-family: Times New Roman;"><span data-ttu-id="fe271-212">Times New Roman</span><span class="sxs-lookup"><span data-stu-id="fe271-212">Times New Roman</span></span></td>
<td align="left"><span data-ttu-id="fe271-213">Normal, kursiv, fett, fett kursiv</span><span class="sxs-lookup"><span data-stu-id="fe271-213">Regular, Italic, Bold, Bold Italic</span></span></td>
<td align="left"><span data-ttu-id="fe271-214">Ältere Schriftart mit Unterstützung für europäische Schriften (Lateinisch, Griechisch, Kyrillisch, Arabisch, Armenisch, Hebräisch).</span><span class="sxs-lookup"><span data-stu-id="fe271-214">Legacy font that supports European scripts (Latin, Greek, Cyrillic, Arabic, Armenian, Hebrew).</span></span></td>
</tr>

</tbody>
</table>

### <a name="symbols-and-icons"></a><span data-ttu-id="fe271-215">Symbole</span><span class="sxs-lookup"><span data-stu-id="fe271-215">Symbols and icons</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="fe271-216">Schriftfamilie</span><span class="sxs-lookup"><span data-stu-id="fe271-216">Font-family</span></span></th>
<th align="left"><span data-ttu-id="fe271-217">Stile</span><span class="sxs-lookup"><span data-stu-id="fe271-217">Styles</span></span></th>
<th align="left"><span data-ttu-id="fe271-218">Hinweise</span><span class="sxs-lookup"><span data-stu-id="fe271-218">Notes</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="fe271-219">Segoe MDL2-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="fe271-219">Segoe MDL2 Assets</span></span></td>
<td align="left"><span data-ttu-id="fe271-220">Regular</span><span class="sxs-lookup"><span data-stu-id="fe271-220">Regular</span></span></td>
<td align="left"><span data-ttu-id="fe271-221">Benutzeroberflächen-Schriftart für App-Symbole.</span><span class="sxs-lookup"><span data-stu-id="fe271-221">User-interface font for app icons.</span></span> <span data-ttu-id="fe271-222">Weitere Informationen finden Sie im Artikel <a href="segoe-ui-symbol-font.md">Segoe MDL2 Assets</a>.</span><span class="sxs-lookup"><span data-stu-id="fe271-222">For more info, see the <a href="segoe-ui-symbol-font.md">Segoe MDL2 assets article</a>.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fe271-223">Segoe UI-Emoji</span><span class="sxs-lookup"><span data-stu-id="fe271-223">Segoe UI Emoji</span></span></td>
<td align="left"><span data-ttu-id="fe271-224">Regular</span><span class="sxs-lookup"><span data-stu-id="fe271-224">Regular</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fe271-225">Segoe UI Symbol</span><span class="sxs-lookup"><span data-stu-id="fe271-225">Segoe UI Symbol</span></span></td>
<td align="left"><span data-ttu-id="fe271-226">Regular</span><span class="sxs-lookup"><span data-stu-id="fe271-226">Regular</span></span></td>
<td align="left"><span data-ttu-id="fe271-227">Fallbackschriftart für Symbole</span><span class="sxs-lookup"><span data-stu-id="fe271-227">Fallback font for symbols</span></span></td>
</tr>
</tbody>
</table>

## <a name="related-articles"></a><span data-ttu-id="fe271-228">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="fe271-228">Related articles</span></span>

* [<span data-ttu-id="fe271-229">Textsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="fe271-229">Text controls</span></span>](../controls-and-patterns/text-controls.md)
* [<span data-ttu-id="fe271-230">XAML-Designressourcen</span><span class="sxs-lookup"><span data-stu-id="fe271-230">XAML theme resources</span></span>](../controls-and-patterns/xaml-theme-resources.md#the-xaml-type-ramp)
* [<span data-ttu-id="fe271-231">XAML-Formatvorlagen</span><span class="sxs-lookup"><span data-stu-id="fe271-231">XAML styles</span></span>](../controls-and-patterns/xaml-styles.md)
* [<span data-ttu-id="fe271-232">Microsoft Typografie</span><span class="sxs-lookup"><span data-stu-id="fe271-232">Microsoft Typography</span></span>](https://docs.microsoft.com/typography/)
