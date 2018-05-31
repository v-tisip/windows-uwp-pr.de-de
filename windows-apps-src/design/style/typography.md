---
author: mijacobs
description: Erfahren Sie, wie Sie die Typografie in Ihrer App verwenden, um Benutzern Inhalte leicht verständlich zu machen.
title: Typografie in UWP-Apps
ms.author: mijacobs
ms.date: 04/06/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 3dd5e6f3dbddca2f6a944ee18e32463afe029f89
ms.sourcegitcommit: 91511d2d1dc8ab74b566aaeab3ef2139e7ed4945
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2018
ms.locfileid: "1816775"
---
# <a name="typography"></a><span data-ttu-id="a8813-104">Typografie</span><span class="sxs-lookup"><span data-stu-id="a8813-104">Typography</span></span>

![Headerbild für die Typografie](images/type/header-typography.svg)

<span data-ttu-id="a8813-106">Typografie muss übersichtlich sein, da sie zur visuellen Darstellung von Sprache dient, um Informationen zu kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="a8813-106">As the visual representation of language, typography’s main task is to communicate information.</span></span> <span data-ttu-id="a8813-107">Ihr Stil darf diesem Ziel nie im Wege stehen.</span><span class="sxs-lookup"><span data-stu-id="a8813-107">Its style should never get in the way of that goal.</span></span> <span data-ttu-id="a8813-108">In diesem Artikel erläutern wir, wie Sie die Typografie in Ihre UWP-App formatieren, damit Benutzer Inhalte schnell und effizient verstehen.</span><span class="sxs-lookup"><span data-stu-id="a8813-108">In this article, we'll discuss how to style typography in your UWP app to help users understand content easily and efficiently.</span></span>

## <a name="font"></a><span data-ttu-id="a8813-109">Font</span><span class="sxs-lookup"><span data-stu-id="a8813-109">Font</span></span>

<span data-ttu-id="a8813-110">Verwenden Sie eine Schriftart in der gesamten Benutzeroberfläche Ihrer App. Es wird empfohlen, wenn möglich, die Standardschriftart für UWP-Apps **Segoe UI** zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="a8813-110">You should use one font throughout your app's UI, and we recommend sticking with the default font for UWP apps, **Segoe UI**.</span></span> <span data-ttu-id="a8813-111">Sie wurde entwickelt, um eine optimale Lesbarkeit für Größe und Pixeldichte zu wahren und bietet eine klare, ansprechende und offene Ästhetik, die den Inhalt des Systems ergänzt.</span><span class="sxs-lookup"><span data-stu-id="a8813-111">It's designed to maintain optimal legibility across sizes and pixel densities and offers a clean, light, and open aesthetic that complements the content of the system.</span></span>

![Beispieltext für die Schriftart „SegoeUI“](images/type/segoe-sample.svg)

<span data-ttu-id="a8813-113">Weitere Informationen zum Anzeigen anderer Sprachen als Englisch oder um eine andere Schriftart für Ihre App auszuwählen finden Sie unter [Sprachen](#Languages) und [Schriftarten](#Fonts) für unsere empfohlenen Schriftarten für UWP-Apps.</span><span class="sxs-lookup"><span data-stu-id="a8813-113">To display non-English languages or to select a different font for your app, please see [Languages](#Languages) and [Fonts](#Fonts) for our recommended fonts for UWP apps.</span></span>

<span data-ttu-id="a8813-114">:::row::: :::column::: ![Ja](images/do.svg) Wählen Sie eine Schriftart für Ihre Benutzeroberfläche aus.</span><span class="sxs-lookup"><span data-stu-id="a8813-114">:::row::: :::column::: ![do](images/do.svg) Pick one font for your UI.</span></span>
<span data-ttu-id="a8813-115">:::column-end::: :::column::: ![Nein](images/dont.svg) Mischen Sie nicht mehrere Schriftarten.</span><span class="sxs-lookup"><span data-stu-id="a8813-115">:::column-end::: :::column::: ![don't](images/dont.svg) Don't mix multiple fonts.</span></span>
<span data-ttu-id="a8813-116">:::column-end::: :::row-end:::</span><span class="sxs-lookup"><span data-stu-id="a8813-116">:::column-end::: :::row-end:::</span></span>

## <a name="size-and-scaling"></a><span data-ttu-id="a8813-117">Größe und Skalierung</span><span class="sxs-lookup"><span data-stu-id="a8813-117">Size and scaling</span></span>

<span data-ttu-id="a8813-118">Schriftgrade in UWP-Apps werden automatisch auf allen Geräten skaliert.</span><span class="sxs-lookup"><span data-stu-id="a8813-118">Font sizes in UWP apps automatically scale on all devices.</span></span> <span data-ttu-id="a8813-119">Mit dem Skalierungsalgorithmus wird sichergestellt, dass der Schriftgrad 24 Pixel auf einem 3 Meter entfernten Surface Hub genauso lesbar ist wie der Schriftgrad 24 Pixel auf einem 5-Zoll-Smartphone, das nur einige Zentimeter entfernt ist.</span><span class="sxs-lookup"><span data-stu-id="a8813-119">The scaling algorithm ensures that a 24 px font on Surface Hub 10 feet away is just as legible as a 24 px font on 5" phone that's a few inches away.</span></span>

![Sichtabstände für verschiedene Geräte](images/type/scaling-chart.svg)

<span data-ttu-id="a8813-121">Aufgrund der Funktionsweise der Skalierung, entwerfen Sie in effektiven Pixeln, nicht in den tatsächlichen physischen Pixeln, und Sie müssen den Schriftgrad für unterschiedliche Bildschirmgrößen und Auflösungen nicht ändern.</span><span class="sxs-lookup"><span data-stu-id="a8813-121">Because of how the scaling system works, you're designing in effective pixels, not actual physical pixels, and you shouldn't have to alter font sizes for different screens sizes or resolutions.</span></span>

<span data-ttu-id="a8813-122">::: Zeile:::::: Spalte::: ![Ja](images/do.svg) Folgen Sie der UWP-[Typhierarchie](#type-ramp)-Größe.</span><span class="sxs-lookup"><span data-stu-id="a8813-122">:::row::: :::column::: ![do](images/do.svg) Follow the UWP [type ramp](#type-ramp) sizing.</span></span>
<span data-ttu-id="a8813-123">::: Spalte End:::::: Spalte::: ![Nein](images/dont.svg) Verwenden Sie einen Schriftgrad, der kleiner als 12 Pixel ist.</span><span class="sxs-lookup"><span data-stu-id="a8813-123">:::column-end::: :::column::: ![don't](images/dont.svg) Use a font size smaller than 12 px.</span></span>
<span data-ttu-id="a8813-124">:::column-end::: :::row-end:::</span><span class="sxs-lookup"><span data-stu-id="a8813-124">:::column-end::: :::row-end:::</span></span>

## <a name="hierarchy"></a><span data-ttu-id="a8813-125">Hierarchie</span><span class="sxs-lookup"><span data-stu-id="a8813-125">Hierarchy</span></span>

<span data-ttu-id="a8813-126">:::row::: :::column::: Benutzer verlassen Sie sich auf die visuelle Hierarchie beim Scannen eines Seitenabschnitts: Header fassen Inhalte zusammen und Textkörper enthalten weitere Details.</span><span class="sxs-lookup"><span data-stu-id="a8813-126">:::row::: :::column::: Users rely on visual hierarchy when scanning a page: headers summarize content, and body text provides more detail.</span></span> <span data-ttu-id="a8813-127">Um eine klare visuelle Hierarchie in Ihrer App zu erstellen, folgen Sie der UWP-Typhierarchie.</span><span class="sxs-lookup"><span data-stu-id="a8813-127">To create a clear visual hierarchy in your app, follow the UWP type ramp.</span></span>
<span data-ttu-id="a8813-128">:::column-end::: :::column::: ![Textblock-Stile](images/type/type-hierarchy.svg) :::column-end::: :::row-end:::</span><span class="sxs-lookup"><span data-stu-id="a8813-128">:::column-end::: :::column::: ![text block styles](images/type/type-hierarchy.svg) :::column-end::: :::row-end:::</span></span>

### <a name="type-ramp"></a><span data-ttu-id="a8813-129">Typhierarchie</span><span class="sxs-lookup"><span data-stu-id="a8813-129">Type ramp</span></span>

<span data-ttu-id="a8813-130">Die UWP-Typhierarchie stellt wichtige Beziehungen zwischen den Schriftschnitte auf einer Seite her, damit der Benutzer den Inhalt einfach lesen kann.</span><span class="sxs-lookup"><span data-stu-id="a8813-130">The UWP type ramp establishes crucial relationships between the type styles on a page, helping users read content easily.</span></span> <span data-ttu-id="a8813-131">Alle Größen werden in effektiven Pixeln angegeben und sind für UWP-Apps optimiert, die auf allen Geräten ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="a8813-131">All sizes are in effective pixels and are optimized for UWP apps running on all devices.</span></span>

![Typhierarchie](images/type/type-ramp.svg)

### <a name="using-the-type-ramp"></a><span data-ttu-id="a8813-133">Die Typhierarchie verwenden</span><span class="sxs-lookup"><span data-stu-id="a8813-133">Using the type ramp</span></span>

<span data-ttu-id="a8813-134">:::row::: :::column::: Sie können Ebenen der Typhierarchie als [statische Ressourcen](../controls-and-patterns/xaml-theme-resources.md#the-xaml-type-ramp) für XAML erreichen.</span><span class="sxs-lookup"><span data-stu-id="a8813-134">:::row::: :::column::: You can access levels of the type ramp as XAML [static resources](../controls-and-patterns/xaml-theme-resources.md#the-xaml-type-ramp).</span></span> <span data-ttu-id="a8813-135">Stile folgen der `*TextBlockStyle` Namenskonvention</span><span class="sxs-lookup"><span data-stu-id="a8813-135">The styles follow the `*TextBlockStyle` naming convention.</span></span>
<span data-ttu-id="a8813-136">:::column-end::: :::column::: ![Textblock-Stile](images/type/text-block-type-ramp.svg) :::column-end::: :::row-end:::</span><span class="sxs-lookup"><span data-stu-id="a8813-136">:::column-end::: :::column::: ![text block styles](images/type/text-block-type-ramp.svg) :::column-end::: :::row-end:::</span></span>

```XAML
<TextBlock Text="Header" Style="{StaticResource HeaderTextBlockStyle}"/>
<TextBlock Text="SubHeader" Style="{StaticResource SubheaderTextBlockStyle}"/>
<TextBlock Text="Title" Style="{StaticResource TitleTextBlockStyle}"/>
<TextBlock Text="SubTitle" Style="{StaticResource SubtitleTextBlockStyle}"/>
<TextBlock Text="Base" Style="{StaticResource BaseTextBlockStyle}"/>
<TextBlock Text="Body" Style="{StaticResource BodyTextBlockStyle}"/>
<TextBlock Text="Caption" Style="{StaticResource CaptionTextBlockStyle}"/>
```

<span data-ttu-id="a8813-137">:::row::: :::column::: ![Ja](images/do.svg) Verwenden Sie den "Inhalt" für den meisten Text.</span><span class="sxs-lookup"><span data-stu-id="a8813-137">:::row::: :::column::: ![do](images/do.svg) Use "Body" for most text.</span></span>

        Use "Base" for titles when space is constrained.
    :::column-end:::
    :::column:::
        ![don't](images/dont.svg)
        Use "Caption" for primary action or any long strings.

        Use "Header" or "Subheader" if text needs to wrap.
    :::column-end:::
<span data-ttu-id="a8813-138">:::row-end:::</span><span class="sxs-lookup"><span data-stu-id="a8813-138">:::row-end:::</span></span>

## <a name="alignment"></a><span data-ttu-id="a8813-139">Ausrichtung</span><span class="sxs-lookup"><span data-stu-id="a8813-139">Alignment</span></span>

<span data-ttu-id="a8813-140">Standardmäßig ist das [TextAlignment](https://docs.microsoft.com/uwp/api/windows.ui.xaml.textalignment) links. In den meisten Fällen sorgt das Konzept „links bündig, rechts mit Flatterrand“ für eine konsistente Verankerung des Inhalts und für ein einheitliches Layout.</span><span class="sxs-lookup"><span data-stu-id="a8813-140">The default [TextAlignment](https://docs.microsoft.com/uwp/api/windows.ui.xaml.textalignment) is Left, and in most instances, flush-left and ragged right provides consistent anchoring of the content and a uniform layout.</span></span> <span data-ttu-id="a8813-141">Weitere Informationen für RTL-Sprachen finden Sie unter [Anpassen von Layout und Schriftarten zur Globalisierungsunterstützung](../globalizing/adjust-layout-and-fonts--and-support-rtl.md).</span><span class="sxs-lookup"><span data-stu-id="a8813-141">For RTL languages, see [Adjusting layout and fonts to support globalization](../globalizing/adjust-layout-and-fonts--and-support-rtl.md).</span></span>

![Zeigt linksbündigen Text.](images/type/alignment.svg)

```xaml
<TextBlock TextAlignment="Left">
```

## <a name="character-count"></a><span data-ttu-id="a8813-143">Zeichenanzahl</span><span class="sxs-lookup"><span data-stu-id="a8813-143">Character count</span></span>

<span data-ttu-id="a8813-144">:::row::: :::column::: ![Ja](images/do.svg) Bleiben Sie bei 50 bis 60 Wörtern pro Zeile zur besseren Lesbarkeit.</span><span class="sxs-lookup"><span data-stu-id="a8813-144">:::row::: :::column::: ![do](images/do.svg) Keep to 50–60 letters per line for ease of reading.</span></span>
<span data-ttu-id="a8813-145">:::column-end::: :::column::: ![Nein](images/dont.svg) Weniger als 20 Zeichen oder mehr als 60 Zeichen pro Zeile lassen sich schwer lesen.</span><span class="sxs-lookup"><span data-stu-id="a8813-145">:::column-end::: :::column::: ![don't](images/dont.svg) Less than 20 characters or more than 60 characters per line is difficult to read.</span></span>
<span data-ttu-id="a8813-146">:::column-end::: :::row-end:::</span><span class="sxs-lookup"><span data-stu-id="a8813-146">:::column-end::: :::row-end:::</span></span>

## <a name="clipping-and-ellipses"></a><span data-ttu-id="a8813-147">Beschnitt und Ellipsen</span><span class="sxs-lookup"><span data-stu-id="a8813-147">Clipping and ellipses</span></span>

<span data-ttu-id="a8813-148">Wenn die Textmenge den verfügbaren Speicherplatz überschreitet, wird empfohlen, den Text zuzuschneiden, was das Standardverhalten der meisten [UWP-Textsteuerelemente](../controls-and-patterns/text-controls.md)ist.</span><span class="sxs-lookup"><span data-stu-id="a8813-148">When the amount of text extends beyond the space available, we recommend clipping text, which is the default behavior of most [UWP text controls](../controls-and-patterns/text-controls.md).</span></span>

![Gerät mit abgeschnittenem Text](images/type/clipping.svg)

```xaml
<TextBlock TextWrapping="WrapWholeWords" TextTrimming="Clip"/>
```

<span data-ttu-id="a8813-150">:::row::: :::column::: ![Ja](images/do.svg) Text zuschneiden und umbrechen, wenn mehrere Zeilen vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="a8813-150">:::row::: :::column::: ![do](images/do.svg) Clip text, and wrap if multiple lines are enabled.</span></span>
<span data-ttu-id="a8813-151">:::column-end::: :::column::: ![Nein](images/dont.svg) Verwenden Sie Ellipsen für mehr Übersichtlichkeit.</span><span class="sxs-lookup"><span data-stu-id="a8813-151">:::column-end::: :::column::: ![don't](images/dont.svg) Use ellipses to avoid visual clutter.</span></span>
<span data-ttu-id="a8813-152">:::column-end::: :::row-end:::</span><span class="sxs-lookup"><span data-stu-id="a8813-152">:::column-end::: :::row-end:::</span></span>

<span data-ttu-id="a8813-153">**Hinweis**: Bei Containern, die nicht klar definiert sind (also sich etwa nicht durch eine andere Hintergrundfarbe abheben) oder wenn ein Link zu mehr Text existiert, kann eine Ellipse verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a8813-153">**Note**: If containers are not well-defined (e.g. no differentiating background color), or when there is a link to see more text, then use ellipses.</span></span>

## <a name="languages"></a><span data-ttu-id="a8813-154">Sprachen</span><span class="sxs-lookup"><span data-stu-id="a8813-154">Languages</span></span> 

<span data-ttu-id="a8813-155">Segoe UI ist unsere Schriftart für Englisch, für europäische Sprachen, Griechisch, Hebräisch, Armenisch, Georgisch und Arabisch.</span><span class="sxs-lookup"><span data-stu-id="a8813-155">Segoe UI is our font for English, European languages, Greek, Hebrew, Armenian, Georgian, and Arabic.</span></span> <span data-ttu-id="a8813-156">Lesen Sie die folgenden Empfehlungen für andere Sprachen.</span><span class="sxs-lookup"><span data-stu-id="a8813-156">For other languages, see the following recommendations.</span></span>

### <a name="globalizinglocalizing-fonts"></a><span data-ttu-id="a8813-157">Globalisierung/Lokalisierung von Schriftarten</span><span class="sxs-lookup"><span data-stu-id="a8813-157">Globalizing/localizing fonts</span></span>

<span data-ttu-id="a8813-158">Verwenden Sie die [LanguageFont-Schriftartenersetzungs-APIs](https://docs.microsoft.com/uwp/api/Windows.Globalization.Fonts.LanguageFont) für den programmgesteuerten Zugriff auf die Empfohlenen Einstellungen für Familie, Grad, Breite und Schnitt der Schriftart für eine spezielle Sprache.</span><span class="sxs-lookup"><span data-stu-id="a8813-158">Use the [LanguageFont font-mapping APIs](https://docs.microsoft.com/uwp/api/Windows.Globalization.Fonts.LanguageFont) for programmatic access to the recommended font family, size, weight, and style for a particular language.</span></span> <span data-ttu-id="a8813-159">Das LanguageFont-Objekt ermöglicht den Zugriff auf die richtigen Schriftartinformationen für verschiedene Inhaltskategorien: UI-Kopfzeilen, Benachrichtigungen, Textkörper und Schriftarten für den Textkörper, die vom Benutzer bearbeitet werden können.</span><span class="sxs-lookup"><span data-stu-id="a8813-159">The LanguageFont object provides access to the correct font info for various categories of content including UI headers, notifications, body text, and user-editable document body fonts.</span></span> <span data-ttu-id="a8813-160">Weitere Informationen finden Sie unter [Anpassen von Layout und Schriftarten zur Globalisierungsunterstützung](../globalizing/adjust-layout-and-fonts--and-support-rtl.md).</span><span class="sxs-lookup"><span data-stu-id="a8813-160">For more info, see [Adjusting layout and fonts to support globalization](../globalizing/adjust-layout-and-fonts--and-support-rtl.md).</span></span>

### <a name="fonts-for-non-latin-languages"></a><span data-ttu-id="a8813-161">Schriftarten für nicht lateinische Sprachen</span><span class="sxs-lookup"><span data-stu-id="a8813-161">Fonts for non-Latin languages</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="a8813-162">Schriftfamilie</span><span class="sxs-lookup"><span data-stu-id="a8813-162">Font-family</span></span></th>
<th align="left"><span data-ttu-id="a8813-163">Stile</span><span class="sxs-lookup"><span data-stu-id="a8813-163">Styles</span></span></th>
<th align="left"><span data-ttu-id="a8813-164">Hinweise</span><span class="sxs-lookup"><span data-stu-id="a8813-164">Notes</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="font-family: Embrima;"><span data-ttu-id="a8813-165">Ebrima</span><span class="sxs-lookup"><span data-stu-id="a8813-165">Ebrima</span></span></td>
<td align="left"><span data-ttu-id="a8813-166">Normal, fett</span><span class="sxs-lookup"><span data-stu-id="a8813-166">Regular, Bold</span></span></td>
<td align="left"><span data-ttu-id="a8813-167">Benutzeroberflächen-Schriftart für afrikanische Schriften (Äthiopisch, N'Ko, Osmanya, Tifinagh, Vai).</span><span class="sxs-lookup"><span data-stu-id="a8813-167">User-interface font for African scripts (Ethiopic, N'Ko, Osmanya, Tifinagh, Vai).</span></span></td>
</tr>
<tr class="even">
<td style="font-family: Gadugi;"><span data-ttu-id="a8813-168">Gadugi</span><span class="sxs-lookup"><span data-stu-id="a8813-168">Gadugi</span></span></td>
<td align="left"><span data-ttu-id="a8813-169">Normal, fett</span><span class="sxs-lookup"><span data-stu-id="a8813-169">Regular, Bold</span></span></td>
<td align="left"><span data-ttu-id="a8813-170">Benutzeroberflächen-Schriftart für nordamerikanische Schriften (Kanadische Silbenschrift, Cherokee).</span><span class="sxs-lookup"><span data-stu-id="a8813-170">User-interface font for North American scripts (Canadian Syllabics, Cherokee).</span></span></td>
</tr>
<tr class="odd">
<td align="left" style="font-family: Leelawadee UI;"><span data-ttu-id="a8813-171">LeelawadeeUI</span><span class="sxs-lookup"><span data-stu-id="a8813-171">Leelawadee UI</span></span></td>
<td align="left"><span data-ttu-id="a8813-172">Normal, Semilight, fett</span><span class="sxs-lookup"><span data-stu-id="a8813-172">Regular, Semilight, Bold</span></span></td>
<td align="left"><span data-ttu-id="a8813-173">Benutzeroberflächen-Schriftart für südostasiatische Schriften (Buginesisch, Laotisch, Khmer, Thailändisch).</span><span class="sxs-lookup"><span data-stu-id="a8813-173">User-interface font for Southeast Asian scripts (Buginese, Lao, Khmer, Thai).</span></span></td>
</tr>
<tr class="odd">
<td align="left" style="font-family: Malgun Gothic;"><span data-ttu-id="a8813-174">Malgun Gothic</span><span class="sxs-lookup"><span data-stu-id="a8813-174">Malgun Gothic</span></span></td>
<td align="left"><span data-ttu-id="a8813-175">Regular</span><span class="sxs-lookup"><span data-stu-id="a8813-175">Regular</span></span></td>
<td align="left"><span data-ttu-id="a8813-176">Benutzeroberflächen-Schriftart für Koreanisch.</span><span class="sxs-lookup"><span data-stu-id="a8813-176">User-interface font for Korean.</span></span></td>
</tr>
<tr class="even">
<td align="left" style="font-family: Microsoft JhengHei UI;"><span data-ttu-id="a8813-177">Microsoft JhengHei UI</span><span class="sxs-lookup"><span data-stu-id="a8813-177">Microsoft JhengHei UI</span></span></td>
<td align="left"><span data-ttu-id="a8813-178">Normal, fett, Light</span><span class="sxs-lookup"><span data-stu-id="a8813-178">Regular, Bold, Light</span></span></td>
<td align="left"><span data-ttu-id="a8813-179">Benutzeroberflächen-Schriftart für Chinesisch (traditionell).</span><span class="sxs-lookup"><span data-stu-id="a8813-179">User-interface font for Traditional Chinese.</span></span></td>
</tr>
<tr class="odd">
<td align="left" style="font-family: Microsoft YaHei UI;"><span data-ttu-id="a8813-180">Microsoft YaHei UI</span><span class="sxs-lookup"><span data-stu-id="a8813-180">Microsoft YaHei UI</span></span></td>
<td align="left"><span data-ttu-id="a8813-181">Normal, fett, Light</span><span class="sxs-lookup"><span data-stu-id="a8813-181">Regular, Bold, Light</span></span></td>
<td align="left"><span data-ttu-id="a8813-182">Benutzeroberflächen-Schriftart für Chinesisch (vereinfacht).</span><span class="sxs-lookup"><span data-stu-id="a8813-182">User-interface font for Simplified Chinese.</span></span></td>
</tr>
<tr class="odd">
<td align="left" style="font-family: Myanmar Text;"><span data-ttu-id="a8813-183">Myanmar Text</span><span class="sxs-lookup"><span data-stu-id="a8813-183">Myanmar Text</span></span></td>
<td align="left"><span data-ttu-id="a8813-184">Regular</span><span class="sxs-lookup"><span data-stu-id="a8813-184">Regular</span></span></td>
<td align="left"><span data-ttu-id="a8813-185">Fallbackschriftart für die Myanmar-Schrift.</span><span class="sxs-lookup"><span data-stu-id="a8813-185">Fallback font for Myanmar script.</span></span></td>
</tr>
<tr class="even">
<td align="left" style="font-family: Nirmala UI;"><span data-ttu-id="a8813-186">Nirmala UI</span><span class="sxs-lookup"><span data-stu-id="a8813-186">Nirmala UI</span></span></td>
<td align="left"><span data-ttu-id="a8813-187">Normal, Semilight, fett</span><span class="sxs-lookup"><span data-stu-id="a8813-187">Regular, Semilight, Bold</span></span></td>
<td align="left"><span data-ttu-id="a8813-188">Benutzeroberflächen-Schriftart für südasiatische Schriften (Bangla, Devanagari, Gujarati, Gurmukhi, Kannada, Malayalam, Odia, Ol Chiki, Singhalesisch, Sora Sompeng, Tamil, Telugu)</span><span class="sxs-lookup"><span data-stu-id="a8813-188">User-interface font for South Asian scripts (Bangla, Devanagari, Gujarati, Gurmukhi, Kannada, Malayalam, Odia, Ol Chiki, Sinhala, Sora Sompeng, Tamil, Telugu)</span></span></td>
</tr>
<tr class="odd">
<td align="left" style="font-family: SimSun;"><span data-ttu-id="a8813-189">SimSun</span><span class="sxs-lookup"><span data-stu-id="a8813-189">SimSun</span></span></td>
<td align="left"><span data-ttu-id="a8813-190">Regular</span><span class="sxs-lookup"><span data-stu-id="a8813-190">Regular</span></span></td>
<td align="left"><span data-ttu-id="a8813-191">Eine ältere chinesische UI-Schriftart.</span><span class="sxs-lookup"><span data-stu-id="a8813-191">A legacy Chinese UI font.</span></span> </td>
</tr>
<tr class="even">
<td align="left" style="font-family: Yu Gothic UI;"><span data-ttu-id="a8813-192">Yu Gothic UI</span><span class="sxs-lookup"><span data-stu-id="a8813-192">Yu Gothic UI</span></span></td>
<td align="left"><span data-ttu-id="a8813-193">Light, Semilight, normal, Semibold, fett</span><span class="sxs-lookup"><span data-stu-id="a8813-193">Light, Semilight, Regular, Semibold, Bold</span></span></td>
<td align="left"><span data-ttu-id="a8813-194">Benutzeroberflächen-Schriftart für Japanisch.</span><span class="sxs-lookup"><span data-stu-id="a8813-194">User-interface font for Japanese.</span></span></td>
</tr>
</tbody>
</table>

## <a name="fonts"></a><span data-ttu-id="a8813-195">Schriftarten</span><span class="sxs-lookup"><span data-stu-id="a8813-195">Fonts</span></span>

### <a name="sans-serif-fonts"></a><span data-ttu-id="a8813-196">Serifenlose Schriftarten</span><span class="sxs-lookup"><span data-stu-id="a8813-196">Sans-serif fonts</span></span>

<span data-ttu-id="a8813-197">Serifenlose Schriftarten eignen sich für Überschriften und UI-Elemente.</span><span class="sxs-lookup"><span data-stu-id="a8813-197">Sans-serif fonts are a great choice for headings and UI elements.</span></span> 

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="a8813-198">Schriftfamilie</span><span class="sxs-lookup"><span data-stu-id="a8813-198">Font-family</span></span></th>
<th align="left"><span data-ttu-id="a8813-199">Stile</span><span class="sxs-lookup"><span data-stu-id="a8813-199">Styles</span></span></th>
<th align="left"><span data-ttu-id="a8813-200">Hinweise</span><span class="sxs-lookup"><span data-stu-id="a8813-200">Notes</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left" style="font-family: Arial;"><span data-ttu-id="a8813-201">Arial</span><span class="sxs-lookup"><span data-stu-id="a8813-201">Arial</span></span></td>
<td align="left"><span data-ttu-id="a8813-202">Normal, kursiv, fett, fett kursiv, schwarz</span><span class="sxs-lookup"><span data-stu-id="a8813-202">Regular, Italic, Bold, Bold Italic, Black</span></span></td>
<td align="left"><span data-ttu-id="a8813-203">Unterstützung für europäische und nahöstliche Schriften (Lateinisch, Griechisch, Kyrillisch, Arabisch, Armenisch und Hebräisch). Die Schriftbreite „Black“ unterstützt nur europäische Schriften.</span><span class="sxs-lookup"><span data-stu-id="a8813-203">Supports European and Middle Eastern scripts (Latin, Greek, Cyrillic, Arabic, Armenian, and Hebrew) Black weight supports European scripts only.</span></span></td>
</tr>
<tr class="even">
<td align="left" style="font-family: Calibri;"><span data-ttu-id="a8813-204">Calibri</span><span class="sxs-lookup"><span data-stu-id="a8813-204">Calibri</span></span></td>
<td align="left"><span data-ttu-id="a8813-205">Normal, kursiv, fett, fett kursiv, dünn, dünn kursiv</span><span class="sxs-lookup"><span data-stu-id="a8813-205">Regular, Italic, Bold, Bold Italic, Light, Light Italic</span></span></td>
<td align="left"><span data-ttu-id="a8813-206">Unterstützung für europäische und nahöstliche Schriften (Lateinisch, Griechisch, Kyrillisch, Arabisch und Hebräisch).</span><span class="sxs-lookup"><span data-stu-id="a8813-206">Supports European and Middle Eastern scripts (Latin, Greek, Cyrillic, Arabic and Hebrew).</span></span> <span data-ttu-id="a8813-207">Arabisch nur in gerader Schrift verfügbar.</span><span class="sxs-lookup"><span data-stu-id="a8813-207">Arabic available in the uprights only.</span></span></td>
</tr>
<td style="font-family: Consolas;"><span data-ttu-id="a8813-208">Consolas</span><span class="sxs-lookup"><span data-stu-id="a8813-208">Consolas</span></span></td>
<td><span data-ttu-id="a8813-209">Normal, kursiv, fett, fett kursiv</span><span class="sxs-lookup"><span data-stu-id="a8813-209">Regular, Italic, Bold, Bold Italic</span></span></td>
<td><span data-ttu-id="a8813-210">Schriftart mit fester Breite mit Unterstützung für europäische Schriften (Lateinisch, Griechisch und Kyrillisch).</span><span class="sxs-lookup"><span data-stu-id="a8813-210">Fixed width font that supports European scripts (Latin, Greek and Cyrillic).</span></span></td>
</tr>

<tr>
<td style="font-family: Segoe UI;"><span data-ttu-id="a8813-211">Segoe UI</span><span class="sxs-lookup"><span data-stu-id="a8813-211">Segoe UI</span></span></td>
<td><span data-ttu-id="a8813-212">Normal, kursiv, Light kursiv, Black kursiv, fett, fett kursiv, Light, Semilight, Semibold, Black</span><span class="sxs-lookup"><span data-stu-id="a8813-212">Regular, Italic, Light Italic, Black Italic, Bold, Bold Italic, Light, Semilight, Semibold, Black</span></span></td>
<td><span data-ttu-id="a8813-213">Benutzeroberflächen-Schriftart für europäische und nahöstliche Schriften (Arabisch, Armenisch, Kyrillisch, Georgisch, Griechisch, Hebräisch, Lateinisch) und auch Lisu-Schrift.</span><span class="sxs-lookup"><span data-stu-id="a8813-213">User-interface font for European and Middle East scripts (Arabic, Armenian, Cyrillic, Georgian, Greek, Hebrew, Latin), and also Lisu script.</span></span></td>
</tr>

<tr class="even">
<td style="font-family: Selawik;"><span data-ttu-id="a8813-214">Selawik</span><span class="sxs-lookup"><span data-stu-id="a8813-214">Selawik</span></span></td>
<td align="left"><span data-ttu-id="a8813-215">Normal, Semilight, Light, fett, Semibold</span><span class="sxs-lookup"><span data-stu-id="a8813-215">Regular, Semilight, Light, Bold, Semibold</span></span></td>
<td align="left"><span data-ttu-id="a8813-216">Open-Source-Schriftart, die metrisch kompatibel mit SegoeUI ist. Vorgesehen für Apps auf anderen Plattformen, auf denen SegoeUI nicht verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="a8813-216">An open-source font that's metrically compatible with Segoe UI, intended for apps on other platforms that don’t want to bundle Segoe UI.</span></span> <a href="https://github.com/Microsoft/Selawik"><span data-ttu-id="a8813-217">Laden Sie Selawik über GitHub herunter.</span><span class="sxs-lookup"><span data-stu-id="a8813-217">Get Selawik on GitHub.</span></span></a></td>
</tr>

</tbody>
</table>

### <a name="serif-fonts"></a><span data-ttu-id="a8813-218">Serifenschriftarten</span><span class="sxs-lookup"><span data-stu-id="a8813-218">Serif fonts</span></span>

<span data-ttu-id="a8813-219">Mit Serifenschriftarten lassen sich größere Textmengen gut darstellen.</span><span class="sxs-lookup"><span data-stu-id="a8813-219">Serif fonts are good for presenting large amounts of text.</span></span> 

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="a8813-220">Schriftfamilie</span><span class="sxs-lookup"><span data-stu-id="a8813-220">Font-family</span></span></th>
<th align="left"><span data-ttu-id="a8813-221">Stile</span><span class="sxs-lookup"><span data-stu-id="a8813-221">Styles</span></span></th>
<th align="left"><span data-ttu-id="a8813-222">Hinweise</span><span class="sxs-lookup"><span data-stu-id="a8813-222">Notes</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="font-family: Cambria;"><span data-ttu-id="a8813-223">Cambria</span><span class="sxs-lookup"><span data-stu-id="a8813-223">Cambria</span></span></td>
<td align="left"><span data-ttu-id="a8813-224">Regular</span><span class="sxs-lookup"><span data-stu-id="a8813-224">Regular</span></span></td>
<td align="left"><span data-ttu-id="a8813-225">Serifenschriftart mit Unterstützung für europäischen Schriften (Lateinisch, Griechisch, Kyrillisch).</span><span class="sxs-lookup"><span data-stu-id="a8813-225">Serif font that supports European scripts (Latin, Greek, Cyrillic).</span></span></td>
</tr>
<tr class="even">
<td style="font-family: Courier New;"><span data-ttu-id="a8813-226">Courier New</span><span class="sxs-lookup"><span data-stu-id="a8813-226">Courier New</span></span></td>
<td align="left"><span data-ttu-id="a8813-227">Normal, kursiv, fett, fett kursiv</span><span class="sxs-lookup"><span data-stu-id="a8813-227">Regular, Italic, Bold, Bold Italic</span></span></td>
<td align="left"><span data-ttu-id="a8813-228">Serifenschriftart mit fester Breite und Unterstützung für europäische und nahöstliche Schriften (Lateinisch, Griechisch, Kyrillisch, Arabisch, Armenisch und Hebräisch).</span><span class="sxs-lookup"><span data-stu-id="a8813-228">Serif fixed width font supports European and Middle Eastern scripts (Latin, Greek, Cyrillic, Arabic, Armenian, and Hebrew).</span></span></td>
</tr>
<tr class="odd">
<td style="font-family: Georgia;"><span data-ttu-id="a8813-229">Georgia</span><span class="sxs-lookup"><span data-stu-id="a8813-229">Georgia</span></span></td>
<td align="left"><span data-ttu-id="a8813-230">Normal, kursiv, fett, fett kursiv</span><span class="sxs-lookup"><span data-stu-id="a8813-230">Regular, Italic, Bold, Bold Italic</span></span></td>
<td align="left"><span data-ttu-id="a8813-231">Unterstützung für europäische Schriften (Lateinisch, Griechisch und Kyrillisch).</span><span class="sxs-lookup"><span data-stu-id="a8813-231">Supports European scripts (Latin, Greek and Cyrillic).</span></span></td>
</tr>

<tr class="even">
<td style="font-family: Times New Roman;"><span data-ttu-id="a8813-232">Times New Roman</span><span class="sxs-lookup"><span data-stu-id="a8813-232">Times New Roman</span></span></td>
<td align="left"><span data-ttu-id="a8813-233">Normal, kursiv, fett, fett kursiv</span><span class="sxs-lookup"><span data-stu-id="a8813-233">Regular, Italic, Bold, Bold Italic</span></span></td>
<td align="left"><span data-ttu-id="a8813-234">Ältere Schriftart mit Unterstützung für europäische Schriften (Lateinisch, Griechisch, Kyrillisch, Arabisch, Armenisch, Hebräisch).</span><span class="sxs-lookup"><span data-stu-id="a8813-234">Legacy font that supports European scripts (Latin, Greek, Cyrillic, Arabic, Armenian, Hebrew).</span></span></td>
</tr>

</tbody>
</table>

### <a name="symbols-and-icons"></a><span data-ttu-id="a8813-235">Symbole</span><span class="sxs-lookup"><span data-stu-id="a8813-235">Symbols and icons</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="a8813-236">Schriftfamilie</span><span class="sxs-lookup"><span data-stu-id="a8813-236">Font-family</span></span></th>
<th align="left"><span data-ttu-id="a8813-237">Stile</span><span class="sxs-lookup"><span data-stu-id="a8813-237">Styles</span></span></th>
<th align="left"><span data-ttu-id="a8813-238">Hinweise</span><span class="sxs-lookup"><span data-stu-id="a8813-238">Notes</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="a8813-239">Segoe MDL2-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="a8813-239">Segoe MDL2 Assets</span></span></td>
<td align="left"><span data-ttu-id="a8813-240">Regular</span><span class="sxs-lookup"><span data-stu-id="a8813-240">Regular</span></span></td>
<td align="left"><span data-ttu-id="a8813-241">Benutzeroberflächen-Schriftart für App-Symbole.</span><span class="sxs-lookup"><span data-stu-id="a8813-241">User-interface font for app icons.</span></span> <span data-ttu-id="a8813-242">Weitere Informationen finden Sie im Artikel <a href="segoe-ui-symbol-font.md">Segoe MDL2 Assets</a>.</span><span class="sxs-lookup"><span data-stu-id="a8813-242">For more info, see the <a href="segoe-ui-symbol-font.md">Segoe MDL2 assets article</a>.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a8813-243">Segoe UI-Emoji</span><span class="sxs-lookup"><span data-stu-id="a8813-243">Segoe UI Emoji</span></span></td>
<td align="left"><span data-ttu-id="a8813-244">Regular</span><span class="sxs-lookup"><span data-stu-id="a8813-244">Regular</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a8813-245">Segoe UI Symbol</span><span class="sxs-lookup"><span data-stu-id="a8813-245">Segoe UI Symbol</span></span></td>
<td align="left"><span data-ttu-id="a8813-246">Regular</span><span class="sxs-lookup"><span data-stu-id="a8813-246">Regular</span></span></td>
<td align="left"><span data-ttu-id="a8813-247">Fallbackschriftart für Symbole</span><span class="sxs-lookup"><span data-stu-id="a8813-247">Fallback font for symbols</span></span></td>
</tr>
</tbody>
</table>

## <a name="related-articles"></a><span data-ttu-id="a8813-248">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="a8813-248">Related articles</span></span>

* [<span data-ttu-id="a8813-249">Textsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="a8813-249">Text controls</span></span>](../controls-and-patterns/text-controls.md)
* [<span data-ttu-id="a8813-250">XAML-Designressourcen</span><span class="sxs-lookup"><span data-stu-id="a8813-250">XAML theme resources</span></span>](../controls-and-patterns/xaml-theme-resources.md#the-xaml-type-ramp)
* [<span data-ttu-id="a8813-251">XAML-Formatvorlagen</span><span class="sxs-lookup"><span data-stu-id="a8813-251">XAML styles</span></span>](../controls-and-patterns/xaml-styles.md)
* [<span data-ttu-id="a8813-252">Microsoft Typografie</span><span class="sxs-lookup"><span data-stu-id="a8813-252">Microsoft Typography</span></span>](https://docs.microsoft.com/typography/)