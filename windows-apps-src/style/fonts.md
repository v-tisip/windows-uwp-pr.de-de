---
author: Jwmsft
Description: "Befolgen Sie bei der Auswahl von Schriftarten und der Angabe von Schriftgraden und Schriftfarben für UWP-Apps die folgenden Richtlinien."
title: "Schriftarten für UWP-Apps"
ms.assetid: 1B8B90AD-CDC4-4997-ACDE-871C1E94A929
label: Fonts
template: detail.hbs
ms.author: jimwalk
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 08f6a712d73c58d3719c0555cda6688b5aa138ab
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
# <a name="fonts-for-uwp-apps"></a><span data-ttu-id="90966-104">Schriftarten für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="90966-104">Fonts for UWP apps</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css"> 

<span data-ttu-id="90966-105">In diesem Artikel sind die empfohlenen Schriftarten für UWP-Apps aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="90966-105">This article lists the recommended fonts for UWP apps.</span></span> <span data-ttu-id="90966-106">Diese Schriftarten sind garantiert in allen Editionen von Windows10 verfügbar, die UWP-Apps unterstützen.</span><span class="sxs-lookup"><span data-stu-id="90966-106">These fonts are guaranteed to be available in all Windows 10 editions that support UWP apps.</span></span>

<div class="important-apis" >
<b><span data-ttu-id="90966-107">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="90966-107">Important APIs</span></span></b><br/>
<ul>
<li>[**<span data-ttu-id="90966-108">FontFamily-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="90966-108">FontFamily property</span></span>**](https://msdn.microsoft.com/library/windows/apps/br209655)</li>
</ul>
</div>

<span data-ttu-id="90966-109">Der [UWP-Typografieleitfaden](typography.md) empfiehlt für Apps die Schriftart „SegoeUI“. Zwar eignet sich SegoeUI für zahlreiche Apps, muss jedoch nicht überall verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="90966-109">The [UWP typography guide](typography.md) recommends that apps use the Segoe UI font, and although Segoe UI is a great choice for most apps, you don't have to use it for everything.</span></span> <span data-ttu-id="90966-110">Sie können andere Schriftarten für bestimmte Szenarien verwenden, z.B. zum Lesen oder wenn Sie Text in bestimmten Sprachen anzeigen.</span><span class="sxs-lookup"><span data-stu-id="90966-110">You might use other fonts for certain scenarios, such as reading, or when displaying text in certain non-English languages.</span></span> 
 
## <a name="sans-serif-fonts"></a><span data-ttu-id="90966-111">Serifenlose Schriftarten</span><span class="sxs-lookup"><span data-stu-id="90966-111">Sans-serif fonts</span></span>

<span data-ttu-id="90966-112">Serifenlose Schriftarten eignen sich für Überschriften und UI-Elemente.</span><span class="sxs-lookup"><span data-stu-id="90966-112">Sans-serif fonts are a great choice for headings and UI elements.</span></span> 

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="90966-113">Schriftfamilie</span><span class="sxs-lookup"><span data-stu-id="90966-113">Font-family</span></span></th>
<th align="left"><span data-ttu-id="90966-114">Stile</span><span class="sxs-lookup"><span data-stu-id="90966-114">Styles</span></span></th>
<th align="left"><span data-ttu-id="90966-115">Hinweise</span><span class="sxs-lookup"><span data-stu-id="90966-115">Notes</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left" style="font-family: Arial;"><span data-ttu-id="90966-116">Arial</span><span class="sxs-lookup"><span data-stu-id="90966-116">Arial</span></span></td>
<td align="left"><span data-ttu-id="90966-117">Normal, kursiv, fett, fett kursiv, schwarz</span><span class="sxs-lookup"><span data-stu-id="90966-117">Regular, Italic, Bold, Bold Italic, Black</span></span></td>
<td align="left"><span data-ttu-id="90966-118">Unterstützung für europäische und nahöstliche Schriften (Lateinisch, Griechisch, Kyrillisch, Arabisch, Armenisch und Hebräisch). Die Schriftbreite „Black“ unterstützt nur europäische Schriften.</span><span class="sxs-lookup"><span data-stu-id="90966-118">Supports European and Middle Eastern scripts (Latin, Greek, Cyrillic, Arabic, Armenian, and Hebrew) Black weight supports European scripts only.</span></span></td>
</tr>
<tr class="even">
<td align="left" style="font-family: Calibri;"><span data-ttu-id="90966-119">Calibri</span><span class="sxs-lookup"><span data-stu-id="90966-119">Calibri</span></span></td>
<td align="left"><span data-ttu-id="90966-120">Normal, kursiv, fett, fett kursiv, dünn, dünn kursiv</span><span class="sxs-lookup"><span data-stu-id="90966-120">Regular, Italic, Bold, Bold Italic, Light, Light Italic</span></span></td>
<td align="left"><span data-ttu-id="90966-121">Unterstützung für europäische und nahöstliche Schriften (Lateinisch, Griechisch, Kyrillisch, Arabisch und Hebräisch).</span><span class="sxs-lookup"><span data-stu-id="90966-121">Supports European and Middle Eastern scripts (Latin, Greek, Cyrillic, Arabic and Hebrew).</span></span> <span data-ttu-id="90966-122">Arabisch nur in gerader Schrift verfügbar.</span><span class="sxs-lookup"><span data-stu-id="90966-122">Arabic available in the uprights only.</span></span></td>
</tr>
<td style="font-family: Consolas;"><span data-ttu-id="90966-123">Consolas</span><span class="sxs-lookup"><span data-stu-id="90966-123">Consolas</span></span></td>
<td><span data-ttu-id="90966-124">Normal, kursiv, fett, fett kursiv</span><span class="sxs-lookup"><span data-stu-id="90966-124">Regular, Italic, Bold, Bold Italic</span></span></td>
<td><span data-ttu-id="90966-125">Schriftart mit fester Breite mit Unterstützung für europäische Schriften (Lateinisch, Griechisch und Kyrillisch).</span><span class="sxs-lookup"><span data-stu-id="90966-125">Fixed width font that supports European scripts (Latin, Greek and Cyrillic).</span></span></td>
</tr>

<tr>
<td style="font-family: Segoe UI;"><span data-ttu-id="90966-126">Segoe UI</span><span class="sxs-lookup"><span data-stu-id="90966-126">Segoe UI</span></span></td>
<td><span data-ttu-id="90966-127">Normal, kursiv, Light kursiv, Black kursiv, fett, fett kursiv, Light, Semilight, Semibold, Black</span><span class="sxs-lookup"><span data-stu-id="90966-127">Regular, Italic, Light Italic, Black Italic, Bold, Bold Italic, Light, Semilight, Semibold, Black</span></span></td>
<td><span data-ttu-id="90966-128">Benutzeroberflächen-Schriftart für europäische und nahöstliche Schriften (Arabisch, Armenisch, Kyrillisch, Georgisch, Griechisch, Hebräisch, Lateinisch) und auch Lisu-Schrift.</span><span class="sxs-lookup"><span data-stu-id="90966-128">User-interface font for European and Middle East scripts (Arabic, Armenian, Cyrillic, Georgian, Greek, Hebrew, Latin), and also Lisu script.</span></span></td>
</tr>

<tr class="odd">
<td><span data-ttu-id="90966-129">Segoe UI historisch</span><span class="sxs-lookup"><span data-stu-id="90966-129">Segoe UI Historic</span></span></td>
<td align="left"><span data-ttu-id="90966-130">Regular</span><span class="sxs-lookup"><span data-stu-id="90966-130">Regular</span></span></td>
<td align="left"><span data-ttu-id="90966-131">Fallbackschriftart für historische Schriften</span><span class="sxs-lookup"><span data-stu-id="90966-131">Fallback font for historic scripts</span></span></td>
</tr>

<tr class="even">
<td style="font-family: Selawik;"><span data-ttu-id="90966-132">Selawik</span><span class="sxs-lookup"><span data-stu-id="90966-132">Selawik</span></span></td>
<td align="left"><span data-ttu-id="90966-133">Normal, Semilight, Light, fett, Semibold</span><span class="sxs-lookup"><span data-stu-id="90966-133">Regular, Semilight, Light, Bold, Semibold</span></span></td>
<td align="left"><span data-ttu-id="90966-134">Open-Source-Schriftart, die metrisch kompatibel mit SegoeUI ist. Vorgesehen für Apps auf anderen Plattformen, auf denen SegoeUI nicht verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="90966-134">An open-source font that's metrically compatible with Segoe UI, intended for apps on other platforms that don’t want to bundle Segoe UI.</span></span> [<span data-ttu-id="90966-135">Laden Sie Selawik über GitHub herunter.</span><span class="sxs-lookup"><span data-stu-id="90966-135">Get Selawik on GitHub.</span></span>](https://github.com/Microsoft/Selawik)</td>
</tr>

<tr class="even">
<td style="font-family: Verdana;"><span data-ttu-id="90966-136">Verdana</span><span class="sxs-lookup"><span data-stu-id="90966-136">Verdana</span></span></td>
<td align="left"><span data-ttu-id="90966-137">Normal, kursiv, fett, fett kursiv</span><span class="sxs-lookup"><span data-stu-id="90966-137">Regular, Italic, Bold, Bold Italic</span></span></td>
<td align="left"><span data-ttu-id="90966-138">Unterstützung für europäische Schriften (Lateinisch, Griechisch, Kyrillisch und Armenisch).</span><span class="sxs-lookup"><span data-stu-id="90966-138">Supports European scripts (Latin, Greek, Cyrillic and Armenian).</span></span></td>
</tr>

</tbody>
</table>


## <a name="serif-fonts"></a><span data-ttu-id="90966-139">Serifenschriftarten</span><span class="sxs-lookup"><span data-stu-id="90966-139">Serif fonts</span></span>

<span data-ttu-id="90966-140">Mit Serifenschriftarten lassen sich größere Textmengen gut darstellen.</span><span class="sxs-lookup"><span data-stu-id="90966-140">Serif fonts are good for presenting large amounts of text.</span></span> 

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="90966-141">Schriftfamilie</span><span class="sxs-lookup"><span data-stu-id="90966-141">Font-family</span></span></th>
<th align="left"><span data-ttu-id="90966-142">Stile</span><span class="sxs-lookup"><span data-stu-id="90966-142">Styles</span></span></th>
<th align="left"><span data-ttu-id="90966-143">Hinweise</span><span class="sxs-lookup"><span data-stu-id="90966-143">Notes</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="font-family: Cambria;"><span data-ttu-id="90966-144">Cambria</span><span class="sxs-lookup"><span data-stu-id="90966-144">Cambria</span></span></td>
<td align="left"><span data-ttu-id="90966-145">Regular</span><span class="sxs-lookup"><span data-stu-id="90966-145">Regular</span></span></td>
<td align="left"><span data-ttu-id="90966-146">Serifenschriftart mit Unterstützung für europäischen Schriften (Lateinisch, Griechisch, Kyrillisch).</span><span class="sxs-lookup"><span data-stu-id="90966-146">Serif font that supports European scripts (Latin, Greek, Cyrillic).</span></span></td>
</tr>
<tr class="even">
<td style="font-family: Courier New;"><span data-ttu-id="90966-147">Courier New</span><span class="sxs-lookup"><span data-stu-id="90966-147">Courier New</span></span></td>
<td align="left"><span data-ttu-id="90966-148">Normal, kursiv, fett, fett kursiv</span><span class="sxs-lookup"><span data-stu-id="90966-148">Regular, Italic, Bold, Bold Italic</span></span></td>
<td align="left"><span data-ttu-id="90966-149">Serifenschriftart mit fester Breite und Unterstützung für europäische und nahöstliche Schriften (Lateinisch, Griechisch, Kyrillisch, Arabisch, Armenisch und Hebräisch).</span><span class="sxs-lookup"><span data-stu-id="90966-149">Serif fixed width font supports European and Middle Eastern scripts (Latin, Greek, Cyrillic, Arabic, Armenian, and Hebrew).</span></span></td>
</tr>
<tr class="odd">
<td style="font-family: Georgia;"><span data-ttu-id="90966-150">Georgia</span><span class="sxs-lookup"><span data-stu-id="90966-150">Georgia</span></span></td>
<td align="left"><span data-ttu-id="90966-151">Normal, kursiv, fett, fett kursiv</span><span class="sxs-lookup"><span data-stu-id="90966-151">Regular, Italic, Bold, Bold Italic</span></span></td>
<td align="left"><span data-ttu-id="90966-152">Unterstützung für europäische Schriften (Lateinisch, Griechisch und Kyrillisch).</span><span class="sxs-lookup"><span data-stu-id="90966-152">Supports European scripts (Latin, Greek and Cyrillic).</span></span></td>
</tr>


<tr class="even">
<td style="font-family: Times New Roman;"><span data-ttu-id="90966-153">Times New Roman</span><span class="sxs-lookup"><span data-stu-id="90966-153">Times New Roman</span></span></td>
<td align="left"><span data-ttu-id="90966-154">Normal, kursiv, fett, fett kursiv</span><span class="sxs-lookup"><span data-stu-id="90966-154">Regular, Italic, Bold, Bold Italic</span></span></td>
<td align="left"><span data-ttu-id="90966-155">Ältere Schriftart mit Unterstützung für europäische Schriften (Lateinisch, Griechisch, Kyrillisch, Arabisch, Armenisch, Hebräisch).</span><span class="sxs-lookup"><span data-stu-id="90966-155">Legacy font that supports European scripts (Latin, Greek, Cyrillic, Arabic, Armenian, Hebrew).</span></span></td>
</tr>

</tbody>
</table>

## <a name="symbols-and-icons"></a><span data-ttu-id="90966-156">Symbole</span><span class="sxs-lookup"><span data-stu-id="90966-156">Symbols and icons</span></span>


<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="90966-157">Schriftfamilie</span><span class="sxs-lookup"><span data-stu-id="90966-157">Font-family</span></span></th>
<th align="left"><span data-ttu-id="90966-158">Stile</span><span class="sxs-lookup"><span data-stu-id="90966-158">Styles</span></span></th>
<th align="left"><span data-ttu-id="90966-159">Hinweise</span><span class="sxs-lookup"><span data-stu-id="90966-159">Notes</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="90966-160">Segoe MDL2-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="90966-160">Segoe MDL2 Assets</span></span></td>
<td align="left"><span data-ttu-id="90966-161">Regular</span><span class="sxs-lookup"><span data-stu-id="90966-161">Regular</span></span></td>
<td align="left"><span data-ttu-id="90966-162">Benutzeroberflächen-Schriftart für App-Symbole.</span><span class="sxs-lookup"><span data-stu-id="90966-162">User-interface font for app icons.</span></span> <span data-ttu-id="90966-163">Weitere Informationen finden Sie im Artikel [Segoe MDL2 Assets](segoe-ui-symbol-font.md).</span><span class="sxs-lookup"><span data-stu-id="90966-163">For more info, see the [Segoe MDL2 assets article](segoe-ui-symbol-font.md).</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="90966-164">Segoe UI-Emoji</span><span class="sxs-lookup"><span data-stu-id="90966-164">Segoe UI Emoji</span></span></td>
<td align="left"><span data-ttu-id="90966-165">Regular</span><span class="sxs-lookup"><span data-stu-id="90966-165">Regular</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="90966-166">Segoe UI Symbol</span><span class="sxs-lookup"><span data-stu-id="90966-166">Segoe UI Symbol</span></span></td>
<td align="left"><span data-ttu-id="90966-167">Regular</span><span class="sxs-lookup"><span data-stu-id="90966-167">Regular</span></span></td>
<td align="left"><span data-ttu-id="90966-168">Fallbackschriftart für Symbole</span><span class="sxs-lookup"><span data-stu-id="90966-168">Fallback font for symbols</span></span></td>
</tr>
</tbody>
</table>



## <a name="fonts-for-non-latin-languages"></a><span data-ttu-id="90966-169">Schriftarten für nicht lateinische Sprachen</span><span class="sxs-lookup"><span data-stu-id="90966-169">Fonts for non-Latin languages</span></span>

<span data-ttu-id="90966-170">Obwohl viele dieser Schriftarten auch lateinische Zeichen anbieten.</span><span class="sxs-lookup"><span data-stu-id="90966-170">Although many of these fonts provide Latin characters.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="90966-171">Schriftfamilie</span><span class="sxs-lookup"><span data-stu-id="90966-171">Font-family</span></span></th>
<th align="left"><span data-ttu-id="90966-172">Stile</span><span class="sxs-lookup"><span data-stu-id="90966-172">Styles</span></span></th>
<th align="left"><span data-ttu-id="90966-173">Hinweise</span><span class="sxs-lookup"><span data-stu-id="90966-173">Notes</span></span></th>
</tr>
</thead>
<tbody>

<tr class="odd">
<td style="font-family: Embrima;"><span data-ttu-id="90966-174">Ebrima</span><span class="sxs-lookup"><span data-stu-id="90966-174">Ebrima</span></span></td>
<td align="left"><span data-ttu-id="90966-175">Normal, fett</span><span class="sxs-lookup"><span data-stu-id="90966-175">Regular, Bold</span></span></td>
<td align="left"><span data-ttu-id="90966-176">Benutzeroberflächen-Schriftart für afrikanische Schriften (Äthiopisch, N'Ko, Osmanya, Tifinagh, Vai).</span><span class="sxs-lookup"><span data-stu-id="90966-176">User-interface font for African scripts (Ethiopic, N'Ko, Osmanya, Tifinagh, Vai).</span></span></td>
</tr>
<tr class="even">
<td style="font-family: Gadugi;"><span data-ttu-id="90966-177">Gadugi</span><span class="sxs-lookup"><span data-stu-id="90966-177">Gadugi</span></span></td>
<td align="left"><span data-ttu-id="90966-178">Normal, fett</span><span class="sxs-lookup"><span data-stu-id="90966-178">Regular, Bold</span></span></td>
<td align="left"><span data-ttu-id="90966-179">Benutzeroberflächen-Schriftart für nordamerikanische Schriften (Kanadische Silbenschrift, Cherokee).</span><span class="sxs-lookup"><span data-stu-id="90966-179">User-interface font for North American scripts (Canadian Syllabics, Cherokee).</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="90966-180">Javanischer Text Normal Fallbackschriftart für javanische Schrift</span><span class="sxs-lookup"><span data-stu-id="90966-180">Javanese Text Regular Fallback font for Javanese script</span></span></td>
<td align="left"><span data-ttu-id="90966-181">Regular</span><span class="sxs-lookup"><span data-stu-id="90966-181">Regular</span></span></td>
<td align="left"><span data-ttu-id="90966-182">Fallbackschriftart für javanische Schrift</span><span class="sxs-lookup"><span data-stu-id="90966-182">Fallback font for Javanese script</span></span></td>
</tr>
<tr class="odd">
<td align="left" style="font-family: Leelawadee UI;"><span data-ttu-id="90966-183">LeelawadeeUI</span><span class="sxs-lookup"><span data-stu-id="90966-183">Leelawadee UI</span></span></td>
<td align="left"><span data-ttu-id="90966-184">Normal, Semilight, fett</span><span class="sxs-lookup"><span data-stu-id="90966-184">Regular, Semilight, Bold</span></span></td>
<td align="left"><span data-ttu-id="90966-185">Benutzeroberflächen-Schriftart für südostasiatische Schriften (Buginesisch, Laotisch, Khmer, Thailändisch).</span><span class="sxs-lookup"><span data-stu-id="90966-185">User-interface font for Southeast Asian scripts (Buginese, Lao, Khmer, Thai).</span></span></td>
</tr>

<tr class="odd">
<td align="left" style="font-family: Malgun Gothic;"><span data-ttu-id="90966-186">Malgun Gothic</span><span class="sxs-lookup"><span data-stu-id="90966-186">Malgun Gothic</span></span></td>
<td align="left"><span data-ttu-id="90966-187">Regular</span><span class="sxs-lookup"><span data-stu-id="90966-187">Regular</span></span></td>
<td align="left"><span data-ttu-id="90966-188">Benutzeroberflächen-Schriftart für Koreanisch.</span><span class="sxs-lookup"><span data-stu-id="90966-188">User-interface font for Korean.</span></span></td>
</tr>
<tr class="even">
<td align="left" style="font-family: Microsoft Himalaya;"><span data-ttu-id="90966-189">Microsoft Himalaya</span><span class="sxs-lookup"><span data-stu-id="90966-189">Microsoft Himalaya</span></span></td>
<td align="left"><span data-ttu-id="90966-190">Regular</span><span class="sxs-lookup"><span data-stu-id="90966-190">Regular</span></span></td>
<td align="left"><span data-ttu-id="90966-191">Fallbackschriftart für die tibetische Schrift.</span><span class="sxs-lookup"><span data-stu-id="90966-191">Fallback font for Tibetan script.</span></span></td>
</tr>
<!--
<tr class="odd">
<td align="left" style="font-family: Microsoft JhengHei;">Microsoft JhengHei</td>
<td align="left">Regular</td>
<td align="left"></td>
</tr>
-->
<tr class="even">
<td align="left" style="font-family: Microsoft JhengHei UI;"><span data-ttu-id="90966-192">Microsoft JhengHei UI</span><span class="sxs-lookup"><span data-stu-id="90966-192">Microsoft JhengHei UI</span></span></td>
<td align="left"><span data-ttu-id="90966-193">Normal, fett, Light</span><span class="sxs-lookup"><span data-stu-id="90966-193">Regular, Bold, Light</span></span></td>
<td align="left"><span data-ttu-id="90966-194">Benutzeroberflächen-Schriftart für Chinesisch (traditionell).</span><span class="sxs-lookup"><span data-stu-id="90966-194">User-interface font for Traditional Chinese.</span></span></td>
</tr>
<tr class="odd">
<td align="left" style="font-family: Microsoft New Tai Lue;"><span data-ttu-id="90966-195">Microsoft Neu-Tai-Lue</span><span class="sxs-lookup"><span data-stu-id="90966-195">Microsoft New Tai Lue</span></span></td>
<td align="left"><span data-ttu-id="90966-196">Regular</span><span class="sxs-lookup"><span data-stu-id="90966-196">Regular</span></span></td>
<td align="left"><span data-ttu-id="90966-197">Fallbackschriftart für die Neu-Tai-Lue-Schrift.</span><span class="sxs-lookup"><span data-stu-id="90966-197">Fallback font for New Tai Lue script.</span></span></td>
</tr>
<tr class="even">
<td align="left" style="font-family: Microsoft PhagsPa;"><span data-ttu-id="90966-198">Microsoft PhagsPa</span><span class="sxs-lookup"><span data-stu-id="90966-198">Microsoft PhagsPa</span></span></td>
<td align="left"><span data-ttu-id="90966-199">Regular</span><span class="sxs-lookup"><span data-stu-id="90966-199">Regular</span></span></td>
<td align="left"><span data-ttu-id="90966-200">Fallbackschriftart für die Phags-pa-Schrift.</span><span class="sxs-lookup"><span data-stu-id="90966-200">Fallback font for Phags-pa script.</span></span></td>
</tr>
<tr class="odd">
<td align="left" style="font-family: Microsoft Tai Le;"><span data-ttu-id="90966-201">Microsoft Tai Le</span><span class="sxs-lookup"><span data-stu-id="90966-201">Microsoft Tai Le</span></span></td>
<td align="left"><span data-ttu-id="90966-202">Regular</span><span class="sxs-lookup"><span data-stu-id="90966-202">Regular</span></span></td>
<td align="left"><span data-ttu-id="90966-203">Fallbackschriftart für die Tai Le-Schrift.</span><span class="sxs-lookup"><span data-stu-id="90966-203">Fallback font for Tai Le script.</span></span></td>
</tr>
<!--
<tr class="even">
<td align="left" style="font-family: Microsoft YaHei;">Microsoft YaHei</td>
<td align="left">Regular</td>
<td align="left"></td>
</tr>
-->
<tr class="odd">
<td align="left" style="font-family: Microsoft YaHei UI;"><span data-ttu-id="90966-204">Microsoft YaHei UI</span><span class="sxs-lookup"><span data-stu-id="90966-204">Microsoft YaHei UI</span></span></td>
<td align="left"><span data-ttu-id="90966-205">Normal, fett, Light</span><span class="sxs-lookup"><span data-stu-id="90966-205">Regular, Bold, Light</span></span></td>
<td align="left"><span data-ttu-id="90966-206">Benutzeroberflächen-Schriftart für Chinesisch (vereinfacht).</span><span class="sxs-lookup"><span data-stu-id="90966-206">User-interface font for Simplified Chinese.</span></span></td>
</tr>
<tr class="even">
<td align="left" style="font-family: Microsoft Yi Baiti;"><span data-ttu-id="90966-207">Microsoft Yi Baiti</span><span class="sxs-lookup"><span data-stu-id="90966-207">Microsoft Yi Baiti</span></span></td>
<td align="left"><span data-ttu-id="90966-208">Regular</span><span class="sxs-lookup"><span data-stu-id="90966-208">Regular</span></span></td>
<td align="left"><span data-ttu-id="90966-209">Fallbackschriftart für die Yi-Schrift.</span><span class="sxs-lookup"><span data-stu-id="90966-209">Fallback font for Yi script.</span></span></td>
</tr>
<tr class="odd">
<td align="left" style="font-family: Mongolian Baiti;"><span data-ttu-id="90966-210">Mongolisches Baiti</span><span class="sxs-lookup"><span data-stu-id="90966-210">Mongolian Baiti</span></span></td>
<td align="left"><span data-ttu-id="90966-211">Regular</span><span class="sxs-lookup"><span data-stu-id="90966-211">Regular</span></span></td>
<td align="left"><span data-ttu-id="90966-212">Fallbackschriftart für die mongolische Schrift.</span><span class="sxs-lookup"><span data-stu-id="90966-212">Fallback font for Mongolian script.</span></span></td>
</tr>
<tr class="even">
<td align="left" style="font-family: MV Boli;"><span data-ttu-id="90966-213">MV Boli</span><span class="sxs-lookup"><span data-stu-id="90966-213">MV Boli</span></span></td>
<td align="left"><span data-ttu-id="90966-214">Regular</span><span class="sxs-lookup"><span data-stu-id="90966-214">Regular</span></span></td>
<td align="left"><span data-ttu-id="90966-215">Fallbackschriftart für die Thaana-Schrift.</span><span class="sxs-lookup"><span data-stu-id="90966-215">Fallback font for Thaana script.</span></span></td>
</tr>
<tr class="odd">
<td align="left" style="font-family: Myanmar Text;"><span data-ttu-id="90966-216">Myanmar Text</span><span class="sxs-lookup"><span data-stu-id="90966-216">Myanmar Text</span></span></td>
<td align="left"><span data-ttu-id="90966-217">Regular</span><span class="sxs-lookup"><span data-stu-id="90966-217">Regular</span></span></td>
<td align="left"><span data-ttu-id="90966-218">Fallbackschriftart für die Myanmar-Schrift.</span><span class="sxs-lookup"><span data-stu-id="90966-218">Fallback font for Myanmar script.</span></span></td>
</tr>
<tr class="even">
<td align="left" style="font-family: Nirmala UI;"><span data-ttu-id="90966-219">Nirmala UI</span><span class="sxs-lookup"><span data-stu-id="90966-219">Nirmala UI</span></span></td>
<td align="left"><span data-ttu-id="90966-220">Normal, Semilight, fett</span><span class="sxs-lookup"><span data-stu-id="90966-220">Regular, Semilight, Bold</span></span></td>
<td align="left"><span data-ttu-id="90966-221">Benutzeroberflächen-Schriftart für südasiatische Schriften (Bangla, Devanagari, Gujarati, Gurmukhi, Kannada, Malayalam, Odia, Ol Chiki, Singhalesisch, Sora Sompeng, Tamil, Telugu)</span><span class="sxs-lookup"><span data-stu-id="90966-221">User-interface font for South Asian scripts (Bangla, Devanagari, Gujarati, Gurmukhi, Kannada, Malayalam, Odia, Ol Chiki, Sinhala, Sora Sompeng, Tamil, Telugu)</span></span></td>
</tr>

<tr class="odd">
<td align="left" style="font-family: SimSun;"><span data-ttu-id="90966-222">SimSun</span><span class="sxs-lookup"><span data-stu-id="90966-222">SimSun</span></span></td>
<td align="left"><span data-ttu-id="90966-223">Regular</span><span class="sxs-lookup"><span data-stu-id="90966-223">Regular</span></span></td>
<td align="left"><span data-ttu-id="90966-224">Eine ältere chinesische UI-Schriftart.</span><span class="sxs-lookup"><span data-stu-id="90966-224">A legacy Chinese UI font.</span></span> </td>
</tr>
<tr class="odd">
<td align="left" style="font-family: Yu Gothic;"><span data-ttu-id="90966-225">Yu Gothic</span><span class="sxs-lookup"><span data-stu-id="90966-225">Yu Gothic</span></span></td>
<td align="left"><span data-ttu-id="90966-226">Light, normal, Medium, fett</span><span class="sxs-lookup"><span data-stu-id="90966-226">Light, Regular, Medium, Bold</span></span></td>
<td align="left"><span data-ttu-id="90966-227">Verwenden Sie Yu Gothic Medium für Textkörper und ähnlichen Inhalt.</span><span class="sxs-lookup"><span data-stu-id="90966-227">Use Yu Gothic Medium for body text and similar content.</span></span></td>
</tr>
<tr class="even">
<td align="left" style="font-family: Yu Gothic UI;"><span data-ttu-id="90966-228">Yu Gothic UI</span><span class="sxs-lookup"><span data-stu-id="90966-228">Yu Gothic UI</span></span></td>
<td align="left"><span data-ttu-id="90966-229">Light, Semilight, normal, Semibold, fett</span><span class="sxs-lookup"><span data-stu-id="90966-229">Light, Semilight, Regular, Semibold, Bold</span></span></td>
<td align="left"><span data-ttu-id="90966-230">Benutzeroberflächen-Schriftart für Japanisch.</span><span class="sxs-lookup"><span data-stu-id="90966-230">User-interface font for Japanese.</span></span></td>
</tr>
</tbody>
</table>


## <a name="globalizinglocalizing-fonts"></a><span data-ttu-id="90966-231">Globalisierung/Lokalisierung von Schriftarten</span><span class="sxs-lookup"><span data-stu-id="90966-231">Globalizing/localizing fonts</span></span>
<span data-ttu-id="90966-232">Verwenden Sie die [LanguageFont-Schriftartenersetzungs-APIs](https://msdn.microsoft.com/library/windows/apps/br206864) für den programmgesteuerten Zugriff auf die Empfohlenen Einstellungen für Familie, Grad, Breite und Schnitt der Schriftart für eine spezielle Sprache.</span><span class="sxs-lookup"><span data-stu-id="90966-232">Use the [LanguageFont font-mapping APIs](https://msdn.microsoft.com/library/windows/apps/br206864) for programmatic access to the recommended font family, size, weight, and style for a particular language.</span></span> <span data-ttu-id="90966-233">Das LanguageFont-Objekt ermöglicht den Zugriff auf die richtigen Schriftartinformationen für verschiedene Inhaltskategorien: UI-Kopfzeilen, Benachrichtigungen, Textkörper und Schriftarten für den Textkörper, die vom Benutzer bearbeitet werden können.</span><span class="sxs-lookup"><span data-stu-id="90966-233">The LanguageFont object provides access to the correct font info for various categories of content including UI headers, notifications, body text, and user-editable document body fonts.</span></span> <span data-ttu-id="90966-234">Weitere Informationen finden Sie unter [Anpassen von Layout und Schriftarten zur Globalisierungsunterstützung](https://msdn.microsoft.com/windows/uwp/globalizing/adjust-layout-and-fonts--and-support-rtl).</span><span class="sxs-lookup"><span data-stu-id="90966-234">For more info, see [Adjusting layout and fonts to support globalization](https://msdn.microsoft.com/windows/uwp/globalizing/adjust-layout-and-fonts--and-support-rtl).</span></span>


## <a name="get-the-samples"></a><span data-ttu-id="90966-235">Beispiele herunterladen</span><span class="sxs-lookup"><span data-stu-id="90966-235">Get the samples</span></span>

* [<span data-ttu-id="90966-236">Beispiel: Herunterladbare Schriftarten</span><span class="sxs-lookup"><span data-stu-id="90966-236">Downloadable fonts sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/XamlCloudFontIntegration)
* [<span data-ttu-id="90966-237">Beispiel: UI-Grundlagen</span><span class="sxs-lookup"><span data-stu-id="90966-237">UI basics sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/XamlUIBasics)
* [<span data-ttu-id="90966-238">Zeilenabstand mit DirectWrite-Beispiel</span><span class="sxs-lookup"><span data-stu-id="90966-238">Line spacing with DirectWrite sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/DWriteLineSpacingModes) 

## <a name="related-articles"></a><span data-ttu-id="90966-239">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="90966-239">Related articles</span></span>

* [<span data-ttu-id="90966-240">Anpassen von Layout und Schriftarten zur Globalisierungsunterstützung</span><span class="sxs-lookup"><span data-stu-id="90966-240">Adjusting layout and fonts to support globalization</span></span>](https://msdn.microsoft.com/windows/uwp/globalizing/adjust-layout-and-fonts--and-support-rtl)
* [<span data-ttu-id="90966-241">Segoe MDL2</span><span class="sxs-lookup"><span data-stu-id="90966-241">Segoe MDL2</span></span>](segoe-ui-symbol-font.md)
* [<span data-ttu-id="90966-242">Textsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="90966-242">Text controls)</span></span>](../controls-and-patterns/text-controls.md)
* [<span data-ttu-id="90966-243">XAML-Designressourcen</span><span class="sxs-lookup"><span data-stu-id="90966-243">XAML theme resources</span></span>](https://msdn.microsoft.com/library/windows/apps/mt187274)

 

 




