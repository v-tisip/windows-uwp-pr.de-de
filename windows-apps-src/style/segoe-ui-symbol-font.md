---
author: mijacobs
Description: "In diesem Artikel finden Sie eine Liste der in der Schriftart „Segoe MDL2 Assets“ enthaltenen Glyphen und Hinweise zu deren Verwendung."
Search.Refinement.TopicID: "184"
title: "Richtlinien für Segoe MDL2-Symbole"
ms.assetid: DFB215C2-8A61-4957-B662-3B1991AC9BE1
label: Segoe MDL2 icons
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.openlocfilehash: 554667a8db5870ec9d9ba781b20cca41000049c5
ms.sourcegitcommit: 5ece992c31870df4c089360ef47501bd4ce14fa9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2017
---
# <a name="segoe-mdl2-icons"></a><span data-ttu-id="127e7-104">Segoe MDL2-Symbole</span><span class="sxs-lookup"><span data-stu-id="127e7-104">Segoe MDL2 icons</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css"> 

<span data-ttu-id="127e7-105">In diesem Artikel werden die Symbole der Schriftart Segoe MDL2 Assets aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="127e7-105">This article lists the icons provided by the Segoe MDL2 Assets font.</span></span> 

<div class="important-apis" >
<b><span data-ttu-id="127e7-106">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="127e7-106">Important APIs</span></span></b><br/>
<ul>
<li>[**<span data-ttu-id="127e7-107">Symbolenumeration (XAML)</span><span class="sxs-lookup"><span data-stu-id="127e7-107">Symbol enumeration (XAML)</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn252842)</li>
</ul>
</div>


## <a name="about-segoe-mdl2-assets"></a><span data-ttu-id="127e7-108">Informationen zu MDL2 Assets</span><span class="sxs-lookup"><span data-stu-id="127e7-108">About Segoe MDL2 Assets</span></span>

<span data-ttu-id="127e7-109">Mit der Veröffentlichung von Windows10 wurde die Schriftart Segoe UI Symbol von Windows8/8.1 durch die Schriftart Segoe MDL2 Assets ersetzt.</span><span class="sxs-lookup"><span data-stu-id="127e7-109">With the release Windows 10, the Segoe MDL2 Assets font replaced the Windows 8/8.1 Segoe UI Symbol icon font.</span></span> <!-- It can be used in much the same manner as the older font, but many glyphs have been redrawn in the Windows 10 icon style with the font’s metrics set so that icons are aligned within the font’s em-square instead of on a typographic baseline. --> <span data-ttu-id="127e7-110">(**Segoe UI Symbol** ist jedoch weiterhin als „veraltete“ Ressource verfügbar. Es wird jedoch empfohlen, Apps auf die neue Schriftart **Segoe MDL2 Assets** zu aktualisieren.)</span><span class="sxs-lookup"><span data-stu-id="127e7-110">( **Segoe UI Symbol** will still be available as a "legacy" resource, but we recommend updating your app to use the new **Segoe MDL2 Assets**.)</span></span>

<span data-ttu-id="127e7-111">Die Mehrzahl der in der Schriftart **Segoe MDL2 Assets** enthaltenen Symbole und Benutzeroberflächen-Steuerelemente sind dem Unicode-Bereich „Private Use Area“ (PUA) zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="127e7-111">Most of the icons and UI controls included in the **Segoe MDL2 Assets** font are mapped to the Private Use Area of Unicode (PUA).</span></span> <span data-ttu-id="127e7-112">Mithilfe des PUA können Entwickler Glyphen, die keinen vorhandenen Codepunkten zugeordnet sind, private Unicode-Werte zuweisen.</span><span class="sxs-lookup"><span data-stu-id="127e7-112">The PUA allows font developers to assign private Unicode values to glyphs that don’t map to existing code points.</span></span> <span data-ttu-id="127e7-113">Dies ist hilfreich bei der Erstellung einer Symbolschriftart, führt jedoch auch zu einem Interoperabilitätsproblem.</span><span class="sxs-lookup"><span data-stu-id="127e7-113">This is useful when creating a symbol font, but it creates an interoperability problem.</span></span> <span data-ttu-id="127e7-114">Ist die Schriftart nicht verfügbar, werden die Glyphen nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="127e7-114">If the font is not available, the glyphs won’t show up.</span></span> <span data-ttu-id="127e7-115">Verwenden Sie die Glyphen nur, wenn Sie die Schriftart **Segoe MDL2 Assets** explizit angeben können.</span><span class="sxs-lookup"><span data-stu-id="127e7-115">Only use these glyphs when you can specify the **Segoe MDL2 Assets** font.</span></span>

<span data-ttu-id="127e7-116">Verwenden Sie diese Glyphen nur, wenn Sie die Schriftart **Segoe MDL2 Assets** explizit angeben können.</span><span class="sxs-lookup"><span data-stu-id="127e7-116">Use these glyphs only when you can explicitly specify the **Segoe MDL2 Assets** font.</span></span> <span data-ttu-id="127e7-117">Bei Verwendung von Kacheln können Sie diese Glyphen nicht nutzen, da Sie die Kachelschriftart nicht angeben können und PUA-Glyphen nicht per Schriftartfallback verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="127e7-117">If you are working with tiles, you can't use these glyphs because you can't specify the tile font and PUA glyphs are not available via font-fallback.</span></span>

<span data-ttu-id="127e7-118">Anders als bei **Segoe UI Symbol** sind die Symbole in der Schriftart **Segoe MDL2 Assets** nicht für die Inlineverwendung mit Text vorgesehen.</span><span class="sxs-lookup"><span data-stu-id="127e7-118">Unlike with **Segoe UI Symbol**, the icons in the **Segoe MDL2 Assets** font are not intended for use in-line with text.</span></span> <span data-ttu-id="127e7-119">Demnach gelten einige ältere „Tricks“ wie die Pfeile für schrittweise Anzeige nicht mehr.</span><span class="sxs-lookup"><span data-stu-id="127e7-119">This means that some older "tricks" like the progressive disclosure arrows no longer apply.</span></span> <span data-ttu-id="127e7-120">Da alle neuen Symbole gleichermaßen größentechnisch angepasst und positioniert werden, müssen sie entsprechend nicht mit einer Nullbreite erstellt werden. Wir haben hingegen sichergestellt, dass sie einfach als ein Satz funktionieren.</span><span class="sxs-lookup"><span data-stu-id="127e7-120">Likewise, since all of the new icons are sized and positioned the same, they do not have to be made with zero width; we have just made sure they work as a set.</span></span> <span data-ttu-id="127e7-121">Im Idealfall können Sie zwei Symbole überlagern, die als ein Satz konzipiert wurden, und sie nehmen Gestalt an.</span><span class="sxs-lookup"><span data-stu-id="127e7-121">Ideally, you can overlay two icons that were designed as a set and they will fall into place.</span></span> <span data-ttu-id="127e7-122">Wir können dies vornehmen, um die Farbgebung im Code zu erlauben.</span><span class="sxs-lookup"><span data-stu-id="127e7-122">We may do this to allow colorization in the code.</span></span> <span data-ttu-id="127e7-123">Beispielsweise wurden U+EA3A und U+EA3B für den Badgestatus der Startkachel erstellt.</span><span class="sxs-lookup"><span data-stu-id="127e7-123">For example, U+EA3A and U+EA3B were created for the Start tile Badge status.</span></span> <span data-ttu-id="127e7-124">Da diese bereits zentriert sind, kann die Kreisfüllung für unterschiedliche Status gefärbt werden.</span><span class="sxs-lookup"><span data-stu-id="127e7-124">Because these are already centered the circle fill can be colored for different states.</span></span>

## <a name="layering-and-mirroring"></a><span data-ttu-id="127e7-125">Überlagern und Spiegeln</span><span class="sxs-lookup"><span data-stu-id="127e7-125">Layering and mirroring</span></span>

<span data-ttu-id="127e7-126">Alle Glyphen in **Segoe MDL2 Assets** haben dieselbe feste Breite mit einer konsistenten Höhe und einem linken Ursprungspunkt. So können Überlagerungs- und Farbgebungseffekte erzielt werden, indem Glyphen direkt übereinander gezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="127e7-126">All glyphs in **Segoe MDL2 Assets** have the same fixed width with a consistent height and left origin point, so layering and colorization effects can be achieved by drawing glyphs directly on top of each other.</span></span> <span data-ttu-id="127e7-127">Dieses Beispiel zeigt einen schwarzen Rand, der über das rote Herz mit einer Breite von Null gezeichnet wurde.</span><span class="sxs-lookup"><span data-stu-id="127e7-127">This example show a black outline drawn on top of the zero-width red heart.</span></span>

![Verwenden von Glyphen mit der Breite 0](images/segoe-ui-symbol-layering.png)

<span data-ttu-id="127e7-129">Viele der Symbole verfügen zudem über gespiegelte Formen, die in Sprachen verwendet werden können, in denen die Rechts-nach-Links-Ausrichtung verwendet wird, beispielsweise Arabisch, Farsi und Hebräisch.</span><span class="sxs-lookup"><span data-stu-id="127e7-129">Many of the icons also have mirrored forms available for use in languages that use right-to-left text directionality such as Arabic, Farsi, and Hebrew.</span></span>

## <a name="symbol-enumeration"></a><span data-ttu-id="127e7-130">Symbol-Enumeration</span><span class="sxs-lookup"><span data-stu-id="127e7-130">Symbol enumeration</span></span>
<span data-ttu-id="127e7-131">Wenn Sie eine App in C#/VB/C++ und XAML entwickeln, können Sie mithilfe der [**Symbolenumeration**](https://msdn.microsoft.com/library/windows/apps/dn252842) Symbole der Schriftart Segoe MDL2 Assets verwenden.</span><span class="sxs-lookup"><span data-stu-id="127e7-131">If you are developing an app in C#/VB/C++ and XAML, you can use the [**Symbol enumeration**](https://msdn.microsoft.com/library/windows/apps/dn252842) to use icons from the Segoe MDL2 Assets font.</span></span> 

## <a name="how-do-i-get-this-font"></a><span data-ttu-id="127e7-132">Wie erhalte ich diese Schriftart?</span><span class="sxs-lookup"><span data-stu-id="127e7-132">How do I get this font?</span></span>
<span data-ttu-id="127e7-133">Um Segoe MDL2 Assets zu erhalten, müssen Sie Windows10 installieren.</span><span class="sxs-lookup"><span data-stu-id="127e7-133">To obtain Segoe MDL2 Assets, you must install Windows 10.</span></span> 

<!--
Also, keep in mind that the **Segoe MDL2 Assets** font includes many more icons than we can show here. Many of these are intended for specialized purposed and are not typically used anywhere else.
-->

## <a name="icon-list"></a><span data-ttu-id="127e7-134">Liste der Symbole</span><span class="sxs-lookup"><span data-stu-id="127e7-134">Icon list</span></span>

<table style="background-color: white; color: black">

 <tr>
  <td><span data-ttu-id="127e7-135">Symbol</span><span class="sxs-lookup"><span data-stu-id="127e7-135">Symbol</span></span></td>
  <td><span data-ttu-id="127e7-136">Unicode-Punkt</span><span class="sxs-lookup"><span data-stu-id="127e7-136">Unicode point</span></span></td>
  <td><span data-ttu-id="127e7-137">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="127e7-137">Description</span></span></td>
 </tr>
 <tr><td>![CheckMarkLegacy](images/segoe-mdl/e001.png)</td>
  <td><span data-ttu-id="127e7-139">E001</span><span class="sxs-lookup"><span data-stu-id="127e7-139">E001</span></span></td>
  <td><span data-ttu-id="127e7-140">CheckMarkLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-140">CheckMarkLegacy</span></span></td>
 </tr>
 <tr><td>![CheckboxFillLegacy](images/segoe-mdl/e002.png)</td>
  <td><span data-ttu-id="127e7-142">E002</span><span class="sxs-lookup"><span data-stu-id="127e7-142">E002</span></span></td>
  <td><span data-ttu-id="127e7-143">CheckboxFillLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-143">CheckboxFillLegacy</span></span></td>
 </tr>
 <tr><td>![CheckboxLegacy](images/segoe-mdl/e003.png)</td>
  <td><span data-ttu-id="127e7-145">E003</span><span class="sxs-lookup"><span data-stu-id="127e7-145">E003</span></span></td>
  <td><span data-ttu-id="127e7-146">CheckboxLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-146">CheckboxLegacy</span></span></td>
 </tr>
 <tr><td>![CheckboxIndeterminateLegacy](images/segoe-mdl/e004.png)</td>
  <td><span data-ttu-id="127e7-148">E004</span><span class="sxs-lookup"><span data-stu-id="127e7-148">E004</span></span></td>
  <td><span data-ttu-id="127e7-149">CheckboxIndeterminateLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-149">CheckboxIndeterminateLegacy</span></span></td>
 </tr>
 <tr><td>![CheckboxCompositeReversedLegacy](images/segoe-mdl/e005.png)</td>
  <td><span data-ttu-id="127e7-151">E005</span><span class="sxs-lookup"><span data-stu-id="127e7-151">E005</span></span></td>
  <td><span data-ttu-id="127e7-152">CheckboxCompositeReversedLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-152">CheckboxCompositeReversedLegacy</span></span></td>
 </tr>
 <tr><td>![HeartLegacy](images/segoe-mdl/e006.png)</td>
  <td><span data-ttu-id="127e7-154">E006</span><span class="sxs-lookup"><span data-stu-id="127e7-154">E006</span></span></td>
  <td><span data-ttu-id="127e7-155">HeartLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-155">HeartLegacy</span></span></td>
 </tr>
 <tr><td>![HeartBrokenLegacy](images/segoe-mdl/e007.png)</td>
  <td><span data-ttu-id="127e7-157">E007</span><span class="sxs-lookup"><span data-stu-id="127e7-157">E007</span></span></td>
  <td><span data-ttu-id="127e7-158">HeartBrokenLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-158">HeartBrokenLegacy</span></span></td>
 </tr>
 <tr><td>![CheckMarkZeroWidthLegacy](images/segoe-mdl/e008.png)</td>
  <td><span data-ttu-id="127e7-160">E008</span><span class="sxs-lookup"><span data-stu-id="127e7-160">E008</span></span></td>
  <td><span data-ttu-id="127e7-161">CheckMarkZeroWidthLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-161">CheckMarkZeroWidthLegacy</span></span></td>
 </tr>
 <tr><td>![CheckboxFillZeroWidthLegacy](images/segoe-mdl/e009.png)</td>
  <td><span data-ttu-id="127e7-163">E009</span><span class="sxs-lookup"><span data-stu-id="127e7-163">E009</span></span></td>
  <td><span data-ttu-id="127e7-164">CheckboxFillZeroWidthLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-164">CheckboxFillZeroWidthLegacy</span></span></td>
 </tr>
 <tr><td>![RatingStarFillZeroWidthLegacy](images/segoe-mdl/e00a.png)</td>
  <td><span data-ttu-id="127e7-166">E00A</span><span class="sxs-lookup"><span data-stu-id="127e7-166">E00A</span></span></td>
  <td><span data-ttu-id="127e7-167">RatingStarFillZeroWidthLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-167">RatingStarFillZeroWidthLegacy</span></span></td>
 </tr>
 <tr><td>![HeartFillZeroWidthLegacy](images/segoe-mdl/e00b.png)</td>
  <td><span data-ttu-id="127e7-169">E00B</span><span class="sxs-lookup"><span data-stu-id="127e7-169">E00B</span></span></td>
  <td><span data-ttu-id="127e7-170">HeartFillZeroWidthLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-170">HeartFillZeroWidthLegacy</span></span></td>
 </tr>
 <tr><td>![HeartBrokenZeroWidthLegacy](images/segoe-mdl/e00c.png)</td>
  <td><span data-ttu-id="127e7-172">E00C</span><span class="sxs-lookup"><span data-stu-id="127e7-172">E00C</span></span></td>
  <td><span data-ttu-id="127e7-173">HeartBrokenZeroWidthLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-173">HeartBrokenZeroWidthLegacy</span></span></td>
 </tr>
 <tr><td>![ScrollChevronLeftLegacy](images/segoe-mdl/e00e.png)</td>
  <td><span data-ttu-id="127e7-175">E00E</span><span class="sxs-lookup"><span data-stu-id="127e7-175">E00E</span></span></td>
  <td><span data-ttu-id="127e7-176">ScrollChevronLeftLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-176">ScrollChevronLeftLegacy</span></span></td>
 </tr>
 <tr><td>![ScrollChevronRightLegacy](images/segoe-mdl/e00f.png)</td>
  <td><span data-ttu-id="127e7-178">E00F</span><span class="sxs-lookup"><span data-stu-id="127e7-178">E00F</span></span></td>
  <td><span data-ttu-id="127e7-179">ScrollChevronRightLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-179">ScrollChevronRightLegacy</span></span></td>
 </tr>
 <tr><td>![ScrollChevronUpLegacy](images/segoe-mdl/e010.png)</td>
  <td><span data-ttu-id="127e7-181">E010</span><span class="sxs-lookup"><span data-stu-id="127e7-181">E010</span></span></td>
  <td><span data-ttu-id="127e7-182">ScrollChevronUpLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-182">ScrollChevronUpLegacy</span></span></td>
 </tr>
 <tr><td>![ScrollChevronDownLegacy](images/segoe-mdl/e011.png)</td>
  <td><span data-ttu-id="127e7-184">E011</span><span class="sxs-lookup"><span data-stu-id="127e7-184">E011</span></span></td>
  <td><span data-ttu-id="127e7-185">ScrollChevronDownLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-185">ScrollChevronDownLegacy</span></span></td>
 </tr>
 <tr><td>![ChevronLeft3Legacy](images/segoe-mdl/e012.png)</td>
  <td><span data-ttu-id="127e7-187">E012</span><span class="sxs-lookup"><span data-stu-id="127e7-187">E012</span></span></td>
  <td><span data-ttu-id="127e7-188">ChevronLeft3Legacy</span><span class="sxs-lookup"><span data-stu-id="127e7-188">ChevronLeft3Legacy</span></span></td>
 </tr>
 <tr><td>![ChevronRight3Legacy](images/segoe-mdl/e013.png)</td>
  <td><span data-ttu-id="127e7-190">E013</span><span class="sxs-lookup"><span data-stu-id="127e7-190">E013</span></span></td>
  <td><span data-ttu-id="127e7-191">ChevronRight3Legacy</span><span class="sxs-lookup"><span data-stu-id="127e7-191">ChevronRight3Legacy</span></span></td>
 </tr>
 <tr><td>![ChevronUp3Legacy](images/segoe-mdl/e014.png)</td>
  <td><span data-ttu-id="127e7-193">E014</span><span class="sxs-lookup"><span data-stu-id="127e7-193">E014</span></span></td>
  <td><span data-ttu-id="127e7-194">ChevronUp3Legacy</span><span class="sxs-lookup"><span data-stu-id="127e7-194">ChevronUp3Legacy</span></span></td>
 </tr>
 <tr><td>![ChevronDown3Legacy](images/segoe-mdl/e015.png)</td>
  <td><span data-ttu-id="127e7-196">E015</span><span class="sxs-lookup"><span data-stu-id="127e7-196">E015</span></span></td>
  <td><span data-ttu-id="127e7-197">ChevronDown3Legacy</span><span class="sxs-lookup"><span data-stu-id="127e7-197">ChevronDown3Legacy</span></span></td>
 </tr>
 <tr><td>![ScrollChevronLeftBoldLegacy](images/segoe-mdl/e016.png)</td>
  <td><span data-ttu-id="127e7-199">E016</span><span class="sxs-lookup"><span data-stu-id="127e7-199">E016</span></span></td>
  <td><span data-ttu-id="127e7-200">ScrollChevronLeftBoldLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-200">ScrollChevronLeftBoldLegacy</span></span></td>
 </tr>
 <tr><td>![ScrollChevronRightBoldLegacy](images/segoe-mdl/e017.png)</td>
  <td><span data-ttu-id="127e7-202">E017</span><span class="sxs-lookup"><span data-stu-id="127e7-202">E017</span></span></td>
  <td><span data-ttu-id="127e7-203">ScrollChevronRightBoldLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-203">ScrollChevronRightBoldLegacy</span></span></td>
 </tr>
 <tr><td>![ScrollChevronUpBoldLegacy](images/segoe-mdl/e018.png)</td>
  <td><span data-ttu-id="127e7-205">E018</span><span class="sxs-lookup"><span data-stu-id="127e7-205">E018</span></span></td>
  <td><span data-ttu-id="127e7-206">ScrollChevronUpBoldLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-206">ScrollChevronUpBoldLegacy</span></span></td>
 </tr>
 <tr><td>![ScrollChevronDownBoldLegacy](images/segoe-mdl/e019.png)</td>
  <td><span data-ttu-id="127e7-208">E019</span><span class="sxs-lookup"><span data-stu-id="127e7-208">E019</span></span></td>
  <td><span data-ttu-id="127e7-209">ScrollChevronDownBoldLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-209">ScrollChevronDownBoldLegacy</span></span></td>
 </tr>
 <tr><td>![RevealPasswordLegacy](images/segoe-mdl/e052.png)</td>
  <td><span data-ttu-id="127e7-211">E052</span><span class="sxs-lookup"><span data-stu-id="127e7-211">E052</span></span></td>
  <td><span data-ttu-id="127e7-212">RevealPasswordLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-212">RevealPasswordLegacy</span></span></td>
 </tr>
 <tr><td>![EaseOfAccessLegacy](images/segoe-mdl/e07f.png)</td>
  <td><span data-ttu-id="127e7-214">E07F</span><span class="sxs-lookup"><span data-stu-id="127e7-214">E07F</span></span></td>
  <td><span data-ttu-id="127e7-215">EaseOfAccessLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-215">EaseOfAccessLegacy</span></span></td>
 </tr>
 <tr><td>![CheckmarkListviewLegacy](images/segoe-mdl/e081.png)</td>
  <td><span data-ttu-id="127e7-217">E081</span><span class="sxs-lookup"><span data-stu-id="127e7-217">E081</span></span></td>
  <td><span data-ttu-id="127e7-218">CheckmarkListviewLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-218">CheckmarkListviewLegacy</span></span></td>
 </tr>
 <tr><td>![RatingStarFillReducedPaddingHTMLLegacy](images/segoe-mdl/e082.png)</td>
  <td><span data-ttu-id="127e7-220">E082</span><span class="sxs-lookup"><span data-stu-id="127e7-220">E082</span></span></td>
  <td><span data-ttu-id="127e7-221">RatingStarFillReducedPaddingHTMLLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-221">RatingStarFillReducedPaddingHTMLLegacy</span></span></td>
 </tr>
 <tr><td>![KeyboardStandardLegacy](images/segoe-mdl/e087.png)</td>
  <td><span data-ttu-id="127e7-223">E087</span><span class="sxs-lookup"><span data-stu-id="127e7-223">E087</span></span></td>
  <td><span data-ttu-id="127e7-224">KeyboardStandardLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-224">KeyboardStandardLegacy</span></span></td>
 </tr>
 <tr><td>![KeyboardSplitLegacy](images/segoe-mdl/e08f.png)</td>
  <td><span data-ttu-id="127e7-226">E08F</span><span class="sxs-lookup"><span data-stu-id="127e7-226">E08F</span></span></td>
  <td><span data-ttu-id="127e7-227">KeyboardSplitLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-227">KeyboardSplitLegacy</span></span></td>
 </tr>
 <tr><td>![SearchboxLegacy](images/segoe-mdl/e094.png)</td>
  <td><span data-ttu-id="127e7-229">E094</span><span class="sxs-lookup"><span data-stu-id="127e7-229">E094</span></span></td>
  <td><span data-ttu-id="127e7-230">SearchboxLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-230">SearchboxLegacy</span></span></td>
 </tr>
 <tr><td>![ChevronLeft1Legacy](images/segoe-mdl/e096.png)</td>
  <td><span data-ttu-id="127e7-232">E096</span><span class="sxs-lookup"><span data-stu-id="127e7-232">E096</span></span></td>
  <td><span data-ttu-id="127e7-233">ChevronLeft1Legacy</span><span class="sxs-lookup"><span data-stu-id="127e7-233">ChevronLeft1Legacy</span></span></td>
 </tr>
 <tr><td>![ChevronRight1Legacy](images/segoe-mdl/e097.png)</td>
  <td><span data-ttu-id="127e7-235">E097</span><span class="sxs-lookup"><span data-stu-id="127e7-235">E097</span></span></td>
  <td><span data-ttu-id="127e7-236">ChevronRight1Legacy</span><span class="sxs-lookup"><span data-stu-id="127e7-236">ChevronRight1Legacy</span></span></td>
 </tr>
 <tr><td>![ChevronUp1Legacy](images/segoe-mdl/e098.png)</td>
  <td><span data-ttu-id="127e7-238">E098</span><span class="sxs-lookup"><span data-stu-id="127e7-238">E098</span></span></td>
  <td><span data-ttu-id="127e7-239">ChevronUp1Legacy</span><span class="sxs-lookup"><span data-stu-id="127e7-239">ChevronUp1Legacy</span></span></td>
 </tr>
 <tr><td>![ChevronDown1Legacy](images/segoe-mdl/e099.png)</td>
  <td><span data-ttu-id="127e7-241">E099</span><span class="sxs-lookup"><span data-stu-id="127e7-241">E099</span></span></td>
  <td><span data-ttu-id="127e7-242">ChevronDown1Legacy</span><span class="sxs-lookup"><span data-stu-id="127e7-242">ChevronDown1Legacy</span></span></td>
 </tr>
 <tr><td>![ChevronLeft2Legacy](images/segoe-mdl/e09a.png)</td>
  <td><span data-ttu-id="127e7-244">E09A</span><span class="sxs-lookup"><span data-stu-id="127e7-244">E09A</span></span></td>
  <td><span data-ttu-id="127e7-245">ChevronLeft2Legacy</span><span class="sxs-lookup"><span data-stu-id="127e7-245">ChevronLeft2Legacy</span></span></td>
 </tr>
 <tr><td>![ChevronRight2Legacy](images/segoe-mdl/e09b.png)</td>
  <td><span data-ttu-id="127e7-247">E09B</span><span class="sxs-lookup"><span data-stu-id="127e7-247">E09B</span></span></td>
  <td><span data-ttu-id="127e7-248">ChevronRight2Legacy</span><span class="sxs-lookup"><span data-stu-id="127e7-248">ChevronRight2Legacy</span></span></td>
 </tr>
 <tr><td>![ChevronUp2Legacy](images/segoe-mdl/e09c.png)</td>
  <td><span data-ttu-id="127e7-250">E09C</span><span class="sxs-lookup"><span data-stu-id="127e7-250">E09C</span></span></td>
  <td><span data-ttu-id="127e7-251">ChevronUp2Legacy</span><span class="sxs-lookup"><span data-stu-id="127e7-251">ChevronUp2Legacy</span></span></td>
 </tr>
 <tr><td>![ChevronDown2Legacy](images/segoe-mdl/e09d.png)</td>
  <td><span data-ttu-id="127e7-253">E09D</span><span class="sxs-lookup"><span data-stu-id="127e7-253">E09D</span></span></td>
  <td><span data-ttu-id="127e7-254">ChevronDown2Legacy</span><span class="sxs-lookup"><span data-stu-id="127e7-254">ChevronDown2Legacy</span></span></td>
 </tr>
 <tr><td>![ChevronLeft4Legacy](images/segoe-mdl/e09e.png)</td>
  <td><span data-ttu-id="127e7-256">E09E</span><span class="sxs-lookup"><span data-stu-id="127e7-256">E09E</span></span></td>
  <td><span data-ttu-id="127e7-257">ChevronLeft4Legacy</span><span class="sxs-lookup"><span data-stu-id="127e7-257">ChevronLeft4Legacy</span></span></td>
 </tr>
 <tr><td>![ChevronRight4Legacy](images/segoe-mdl/e09f.png)</td>
  <td><span data-ttu-id="127e7-259">E09F</span><span class="sxs-lookup"><span data-stu-id="127e7-259">E09F</span></span></td>
  <td><span data-ttu-id="127e7-260">ChevronRight4Legacy</span><span class="sxs-lookup"><span data-stu-id="127e7-260">ChevronRight4Legacy</span></span></td>
 </tr>
 <tr><td>![ChevronUp4Legacy](images/segoe-mdl/e0a0.png)</td>
  <td><span data-ttu-id="127e7-262">E0A0</span><span class="sxs-lookup"><span data-stu-id="127e7-262">E0A0</span></span></td>
  <td><span data-ttu-id="127e7-263">ChevronUp4Legacy</span><span class="sxs-lookup"><span data-stu-id="127e7-263">ChevronUp4Legacy</span></span></td>
 </tr>
 <tr><td>![ChevronDown4Legacy](images/segoe-mdl/e0a1.png)</td>
  <td><span data-ttu-id="127e7-265">E0A1</span><span class="sxs-lookup"><span data-stu-id="127e7-265">E0A1</span></span></td>
  <td><span data-ttu-id="127e7-266">ChevronDown4Legacy</span><span class="sxs-lookup"><span data-stu-id="127e7-266">ChevronDown4Legacy</span></span></td>
 </tr>
 <tr><td>![CheckboxCompositeLegacy](images/segoe-mdl/e0a2.png)</td>
  <td><span data-ttu-id="127e7-268">E0A2</span><span class="sxs-lookup"><span data-stu-id="127e7-268">E0A2</span></span></td>
  <td><span data-ttu-id="127e7-269">CheckboxCompositeLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-269">CheckboxCompositeLegacy</span></span></td>
 </tr>
 <tr><td>![HeartFillLegacy](images/segoe-mdl/e0a5.png)</td>
  <td><span data-ttu-id="127e7-271">E0A5</span><span class="sxs-lookup"><span data-stu-id="127e7-271">E0A5</span></span></td>
  <td><span data-ttu-id="127e7-272">HeartFillLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-272">HeartFillLegacy</span></span></td>
 </tr>
 <tr><td>![BackBttnArrow42Legacy](images/segoe-mdl/e0a6.png)</td>
  <td><span data-ttu-id="127e7-274">E0A6</span><span class="sxs-lookup"><span data-stu-id="127e7-274">E0A6</span></span></td>
  <td><span data-ttu-id="127e7-275">BackBttnArrow42Legacy</span><span class="sxs-lookup"><span data-stu-id="127e7-275">BackBttnArrow42Legacy</span></span></td>
 </tr>
 <tr><td>![BackBttnMirroredArrow42Legacy](images/segoe-mdl/e0ab.png)</td>
  <td><span data-ttu-id="127e7-277">E0AB</span><span class="sxs-lookup"><span data-stu-id="127e7-277">E0AB</span></span></td>
  <td><span data-ttu-id="127e7-278">BackBttnMirroredArrow42Legacy</span><span class="sxs-lookup"><span data-stu-id="127e7-278">BackBttnMirroredArrow42Legacy</span></span></td>
 </tr>
 <tr><td>![BackBttnMirroredArrow20Legacy](images/segoe-mdl/e0ad.png)</td>
  <td><span data-ttu-id="127e7-280">E0AD</span><span class="sxs-lookup"><span data-stu-id="127e7-280">E0AD</span></span></td>
  <td><span data-ttu-id="127e7-281">BackBttnMirroredArrow20Legacy</span><span class="sxs-lookup"><span data-stu-id="127e7-281">BackBttnMirroredArrow20Legacy</span></span></td>
 </tr>
 <tr><td>![ArrowHTMLLegacyMirrored](images/segoe-mdl/e0ae.png)</td>
  <td><span data-ttu-id="127e7-283">E0AE</span><span class="sxs-lookup"><span data-stu-id="127e7-283">E0AE</span></span></td>
  <td><span data-ttu-id="127e7-284">ArrowHTMLLegacyMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-284">ArrowHTMLLegacyMirrored</span></span></td>
 </tr>
 <tr><td>![RatingStarFillLegacy](images/segoe-mdl/e0b4.png)</td>
  <td><span data-ttu-id="127e7-286">E0B4</span><span class="sxs-lookup"><span data-stu-id="127e7-286">E0B4</span></span></td>
  <td><span data-ttu-id="127e7-287">RatingStarFillLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-287">RatingStarFillLegacy</span></span></td>
 </tr>
 <tr><td>![RatingStarFillSmallLegacy](images/segoe-mdl/e0b5.png)</td>
  <td><span data-ttu-id="127e7-289">E0B5</span><span class="sxs-lookup"><span data-stu-id="127e7-289">E0B5</span></span></td>
  <td><span data-ttu-id="127e7-290">RatingStarFillSmallLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-290">RatingStarFillSmallLegacy</span></span></td>
 </tr>
 <tr><td>![SemanticZoomLegacy](images/segoe-mdl/e0b8.png)</td>
  <td><span data-ttu-id="127e7-292">E0B8</span><span class="sxs-lookup"><span data-stu-id="127e7-292">E0B8</span></span></td>
  <td><span data-ttu-id="127e7-293">SemanticZoomLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-293">SemanticZoomLegacy</span></span></td>
 </tr>
 <tr><td>![BackBttnArrow20Legacy](images/segoe-mdl/e0c4.png)</td>
  <td><span data-ttu-id="127e7-295">E0C4</span><span class="sxs-lookup"><span data-stu-id="127e7-295">E0C4</span></span></td>
  <td><span data-ttu-id="127e7-296">BackBttnArrow20Legacy</span><span class="sxs-lookup"><span data-stu-id="127e7-296">BackBttnArrow20Legacy</span></span></td>
 </tr>
 <tr><td>![ArrowHTMLLegacy](images/segoe-mdl/e0d5.png)</td>
  <td><span data-ttu-id="127e7-298">E0D5</span><span class="sxs-lookup"><span data-stu-id="127e7-298">E0D5</span></span></td>
  <td><span data-ttu-id="127e7-299">ArrowHTMLLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-299">ArrowHTMLLegacy</span></span></td>
 </tr>
 <tr><td>![ChevronFlipLeftLegacy](images/segoe-mdl/e0e2.png)</td>
  <td><span data-ttu-id="127e7-301">E0E2</span><span class="sxs-lookup"><span data-stu-id="127e7-301">E0E2</span></span></td>
  <td><span data-ttu-id="127e7-302">ChevronFlipLeftLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-302">ChevronFlipLeftLegacy</span></span></td>
 </tr>
 <tr><td>![ChevronFlipRightLegacy](images/segoe-mdl/e0e3.png)</td>
  <td><span data-ttu-id="127e7-304">E0E3</span><span class="sxs-lookup"><span data-stu-id="127e7-304">E0E3</span></span></td>
  <td><span data-ttu-id="127e7-305">ChevronFlipRightLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-305">ChevronFlipRightLegacy</span></span></td>
 </tr>
 <tr><td>![ChevronFlipUpLegacy](images/segoe-mdl/e0e4.png)</td>
  <td><span data-ttu-id="127e7-307">E0E4</span><span class="sxs-lookup"><span data-stu-id="127e7-307">E0E4</span></span></td>
  <td><span data-ttu-id="127e7-308">ChevronFlipUpLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-308">ChevronFlipUpLegacy</span></span></td>
 </tr>
 <tr><td>![ChevronFlipDownLegacy](images/segoe-mdl/e0e5.png)</td>
  <td><span data-ttu-id="127e7-310">E0E5</span><span class="sxs-lookup"><span data-stu-id="127e7-310">E0E5</span></span></td>
  <td><span data-ttu-id="127e7-311">ChevronFlipDownLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-311">ChevronFlipDownLegacy</span></span></td>
 </tr>
 <tr><td>![CheckmarkMenuLegacy](images/segoe-mdl/e0e7.png)</td>
  <td><span data-ttu-id="127e7-313">E0E7</span><span class="sxs-lookup"><span data-stu-id="127e7-313">E0E7</span></span></td>
  <td><span data-ttu-id="127e7-314">CheckmarkMenuLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-314">CheckmarkMenuLegacy</span></span></td>
 </tr>
 <tr><td>![PreviousLegacy](images/segoe-mdl/e100.png)</td>
  <td><span data-ttu-id="127e7-316">E100</span><span class="sxs-lookup"><span data-stu-id="127e7-316">E100</span></span></td>
  <td><span data-ttu-id="127e7-317">PreviousLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-317">PreviousLegacy</span></span></td>
 </tr>
 <tr><td>![NextLegacy](images/segoe-mdl/e101.png)</td>
  <td><span data-ttu-id="127e7-319">E101</span><span class="sxs-lookup"><span data-stu-id="127e7-319">E101</span></span></td>
  <td><span data-ttu-id="127e7-320">NextLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-320">NextLegacy</span></span></td>
 </tr>
 <tr><td>![PlayLegacy](images/segoe-mdl/e102.png)</td>
  <td><span data-ttu-id="127e7-322">E102</span><span class="sxs-lookup"><span data-stu-id="127e7-322">E102</span></span></td>
  <td><span data-ttu-id="127e7-323">PlayLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-323">PlayLegacy</span></span></td>
 </tr>
 <tr><td>![PauseLegacy](images/segoe-mdl/e103.png)</td>
  <td><span data-ttu-id="127e7-325">E103</span><span class="sxs-lookup"><span data-stu-id="127e7-325">E103</span></span></td>
  <td><span data-ttu-id="127e7-326">PauseLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-326">PauseLegacy</span></span></td>
 </tr>
 <tr><td>![EditLegacy](images/segoe-mdl/e104.png)</td>
  <td><span data-ttu-id="127e7-328">E104</span><span class="sxs-lookup"><span data-stu-id="127e7-328">E104</span></span></td>
  <td><span data-ttu-id="127e7-329">EditLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-329">EditLegacy</span></span></td>
 </tr>
 <tr><td>![SaveLegacy](images/segoe-mdl/e105.png)</td>
  <td><span data-ttu-id="127e7-331">E105</span><span class="sxs-lookup"><span data-stu-id="127e7-331">E105</span></span></td>
  <td><span data-ttu-id="127e7-332">SaveLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-332">SaveLegacy</span></span></td>
 </tr>
 <tr><td>![ClearLegacy](images/segoe-mdl/e106.png)</td>
  <td><span data-ttu-id="127e7-334">E106</span><span class="sxs-lookup"><span data-stu-id="127e7-334">E106</span></span></td>
  <td><span data-ttu-id="127e7-335">ClearLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-335">ClearLegacy</span></span></td>
 </tr>
 <tr><td>![DeleteLegacy](images/segoe-mdl/e107.png)</td>
  <td><span data-ttu-id="127e7-337">E107</span><span class="sxs-lookup"><span data-stu-id="127e7-337">E107</span></span></td>
  <td><span data-ttu-id="127e7-338">DeleteLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-338">DeleteLegacy</span></span></td>
 </tr>
 <tr><td>![RemoveLegacy](images/segoe-mdl/e108.png)</td>
  <td><span data-ttu-id="127e7-340">E108</span><span class="sxs-lookup"><span data-stu-id="127e7-340">E108</span></span></td>
  <td><span data-ttu-id="127e7-341">RemoveLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-341">RemoveLegacy</span></span></td>
 </tr>
 <tr><td>![AddLegacy](images/segoe-mdl/e109.png)</td>
  <td><span data-ttu-id="127e7-343">E109</span><span class="sxs-lookup"><span data-stu-id="127e7-343">E109</span></span></td>
  <td><span data-ttu-id="127e7-344">AddLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-344">AddLegacy</span></span></td>
 </tr>
 <tr><td>![CancelLegacy](images/segoe-mdl/e10a.png)</td>
  <td><span data-ttu-id="127e7-346">E10A</span><span class="sxs-lookup"><span data-stu-id="127e7-346">E10A</span></span></td>
  <td><span data-ttu-id="127e7-347">CancelLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-347">CancelLegacy</span></span></td>
 </tr>
 <tr><td>![AcceptLegacy](images/segoe-mdl/e10b.png)</td>
  <td><span data-ttu-id="127e7-349">E10B</span><span class="sxs-lookup"><span data-stu-id="127e7-349">E10B</span></span></td>
  <td><span data-ttu-id="127e7-350">AcceptLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-350">AcceptLegacy</span></span></td>
 </tr>
 <tr><td>![MoreLegacy](images/segoe-mdl/e10c.png)</td>
  <td><span data-ttu-id="127e7-352">E10C</span><span class="sxs-lookup"><span data-stu-id="127e7-352">E10C</span></span></td>
  <td><span data-ttu-id="127e7-353">MoreLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-353">MoreLegacy</span></span></td>
 </tr>
 <tr><td>![RedoLegacy](images/segoe-mdl/e10d.png)</td>
  <td><span data-ttu-id="127e7-355">E10D</span><span class="sxs-lookup"><span data-stu-id="127e7-355">E10D</span></span></td>
  <td><span data-ttu-id="127e7-356">RedoLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-356">RedoLegacy</span></span></td>
 </tr>
 <tr><td>![UndoLegacy](images/segoe-mdl/e10e.png)</td>
  <td><span data-ttu-id="127e7-358">E10E</span><span class="sxs-lookup"><span data-stu-id="127e7-358">E10E</span></span></td>
  <td><span data-ttu-id="127e7-359">UndoLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-359">UndoLegacy</span></span></td>
 </tr>
 <tr><td>![HomeLegacy](images/segoe-mdl/e10f.png)</td>
  <td><span data-ttu-id="127e7-361">E10F</span><span class="sxs-lookup"><span data-stu-id="127e7-361">E10F</span></span></td>
  <td><span data-ttu-id="127e7-362">HomeLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-362">HomeLegacy</span></span></td>
 </tr>
 <tr><td>![UpLegacy](images/segoe-mdl/e110.png)</td>
  <td><span data-ttu-id="127e7-364">E110</span><span class="sxs-lookup"><span data-stu-id="127e7-364">E110</span></span></td>
  <td><span data-ttu-id="127e7-365">UpLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-365">UpLegacy</span></span></td>
 </tr>
 <tr><td>![ForwardLegacy](images/segoe-mdl/e111.png)</td>
  <td><span data-ttu-id="127e7-367">E111</span><span class="sxs-lookup"><span data-stu-id="127e7-367">E111</span></span></td>
  <td><span data-ttu-id="127e7-368">ForwardLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-368">ForwardLegacy</span></span></td>
 </tr>
 <tr><td>![BackLegacy](images/segoe-mdl/e112.png)</td>
  <td><span data-ttu-id="127e7-370">E112</span><span class="sxs-lookup"><span data-stu-id="127e7-370">E112</span></span></td>
  <td><span data-ttu-id="127e7-371">BackLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-371">BackLegacy</span></span></td>
 </tr>
 <tr><td>![FavoriteLegacy](images/segoe-mdl/e113.png)</td>
  <td><span data-ttu-id="127e7-373">E113</span><span class="sxs-lookup"><span data-stu-id="127e7-373">E113</span></span></td>
  <td><span data-ttu-id="127e7-374">FavoriteLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-374">FavoriteLegacy</span></span></td>
 </tr>
 <tr><td>![CameraLegacy](images/segoe-mdl/e114.png)</td>
  <td><span data-ttu-id="127e7-376">E114</span><span class="sxs-lookup"><span data-stu-id="127e7-376">E114</span></span></td>
  <td><span data-ttu-id="127e7-377">CameraLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-377">CameraLegacy</span></span></td>
 </tr>
 <tr><td>![SettingsLegacy](images/segoe-mdl/e115.png)</td>
  <td><span data-ttu-id="127e7-379">E115</span><span class="sxs-lookup"><span data-stu-id="127e7-379">E115</span></span></td>
  <td><span data-ttu-id="127e7-380">SettingsLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-380">SettingsLegacy</span></span></td>
 </tr>
 <tr><td>![VideoLegacy](images/segoe-mdl/e116.png)</td>
  <td><span data-ttu-id="127e7-382">E116</span><span class="sxs-lookup"><span data-stu-id="127e7-382">E116</span></span></td>
  <td><span data-ttu-id="127e7-383">VideoLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-383">VideoLegacy</span></span></td>
 </tr>
 <tr><td>![SyncLegacy](images/segoe-mdl/e117.png)</td>
  <td><span data-ttu-id="127e7-385">E117</span><span class="sxs-lookup"><span data-stu-id="127e7-385">E117</span></span></td>
  <td><span data-ttu-id="127e7-386">SyncLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-386">SyncLegacy</span></span></td>
 </tr>
 <tr><td>![DownloadLegacy](images/segoe-mdl/e118.png)</td>
  <td><span data-ttu-id="127e7-388">E118</span><span class="sxs-lookup"><span data-stu-id="127e7-388">E118</span></span></td>
  <td><span data-ttu-id="127e7-389">DownloadLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-389">DownloadLegacy</span></span></td>
 </tr>
 <tr><td>![MailLegacy](images/segoe-mdl/e119.png)</td>
  <td><span data-ttu-id="127e7-391">E119</span><span class="sxs-lookup"><span data-stu-id="127e7-391">E119</span></span></td>
  <td><span data-ttu-id="127e7-392">MailLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-392">MailLegacy</span></span></td>
 </tr>
 <tr><td>![FindLegacy](images/segoe-mdl/e11a.png)</td>
  <td><span data-ttu-id="127e7-394">E11A</span><span class="sxs-lookup"><span data-stu-id="127e7-394">E11A</span></span></td>
  <td><span data-ttu-id="127e7-395">FindLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-395">FindLegacy</span></span></td>
 </tr>
 <tr><td>![HelpLegacy](images/segoe-mdl/e11b.png)</td>
  <td><span data-ttu-id="127e7-397">E11B</span><span class="sxs-lookup"><span data-stu-id="127e7-397">E11B</span></span></td>
  <td><span data-ttu-id="127e7-398">HelpLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-398">HelpLegacy</span></span></td>
 </tr>
 <tr><td>![UploadLegacy](images/segoe-mdl/e11c.png)</td>
  <td><span data-ttu-id="127e7-400">E11C</span><span class="sxs-lookup"><span data-stu-id="127e7-400">E11C</span></span></td>
  <td><span data-ttu-id="127e7-401">UploadLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-401">UploadLegacy</span></span></td>
 </tr>
 <tr><td>![EmojiLegacy](images/segoe-mdl/e11d.png)</td>
  <td><span data-ttu-id="127e7-403">E11D</span><span class="sxs-lookup"><span data-stu-id="127e7-403">E11D</span></span></td>
  <td><span data-ttu-id="127e7-404">EmojiLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-404">EmojiLegacy</span></span></td>
 </tr>
 <tr><td>![TwoPageLegacy](images/segoe-mdl/e11e.png)</td>
  <td><span data-ttu-id="127e7-406">E11E</span><span class="sxs-lookup"><span data-stu-id="127e7-406">E11E</span></span></td>
  <td><span data-ttu-id="127e7-407">TwoPageLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-407">TwoPageLegacy</span></span></td>
 </tr>
 <tr><td>![LeaveChatLegacy](images/segoe-mdl/e11f.png)</td>
  <td><span data-ttu-id="127e7-409">E11F</span><span class="sxs-lookup"><span data-stu-id="127e7-409">E11F</span></span></td>
  <td><span data-ttu-id="127e7-410">LeaveChatLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-410">LeaveChatLegacy</span></span></td>
 </tr>
 <tr><td>![MailForwardLegacy](images/segoe-mdl/e120.png)</td>
  <td><span data-ttu-id="127e7-412">E120</span><span class="sxs-lookup"><span data-stu-id="127e7-412">E120</span></span></td>
  <td><span data-ttu-id="127e7-413">MailForwardLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-413">MailForwardLegacy</span></span></td>
 </tr>
 <tr><td>![ClockLegacy](images/segoe-mdl/e121.png)</td>
  <td><span data-ttu-id="127e7-415">E121</span><span class="sxs-lookup"><span data-stu-id="127e7-415">E121</span></span></td>
  <td><span data-ttu-id="127e7-416">ClockLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-416">ClockLegacy</span></span></td>
 </tr>
 <tr><td>![SendLegacy](images/segoe-mdl/e122.png)</td>
  <td><span data-ttu-id="127e7-418">E122</span><span class="sxs-lookup"><span data-stu-id="127e7-418">E122</span></span></td>
  <td><span data-ttu-id="127e7-419">SendLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-419">SendLegacy</span></span></td>
 </tr>
 <tr><td>![CropLegacy](images/segoe-mdl/e123.png)</td>
  <td><span data-ttu-id="127e7-421">E123</span><span class="sxs-lookup"><span data-stu-id="127e7-421">E123</span></span></td>
  <td><span data-ttu-id="127e7-422">CropLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-422">CropLegacy</span></span></td>
 </tr>
 <tr><td>![RotateCameraLegacy](images/segoe-mdl/e124.png)</td>
  <td><span data-ttu-id="127e7-424">E124</span><span class="sxs-lookup"><span data-stu-id="127e7-424">E124</span></span></td>
  <td><span data-ttu-id="127e7-425">RotateCameraLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-425">RotateCameraLegacy</span></span></td>
 </tr>
 <tr><td>![PeopleLegacy](images/segoe-mdl/e125.png)</td>
  <td><span data-ttu-id="127e7-427">E125</span><span class="sxs-lookup"><span data-stu-id="127e7-427">E125</span></span></td>
  <td><span data-ttu-id="127e7-428">PeopleLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-428">PeopleLegacy</span></span></td>
 </tr>
 <tr><td>![ClosePaneLegacy](images/segoe-mdl/e126.png)</td>
  <td><span data-ttu-id="127e7-430">E126</span><span class="sxs-lookup"><span data-stu-id="127e7-430">E126</span></span></td>
  <td><span data-ttu-id="127e7-431">ClosePaneLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-431">ClosePaneLegacy</span></span></td>
 </tr>
 <tr><td>![OpenPaneLegacy](images/segoe-mdl/e127.png)</td>
  <td><span data-ttu-id="127e7-433">E127</span><span class="sxs-lookup"><span data-stu-id="127e7-433">E127</span></span></td>
  <td><span data-ttu-id="127e7-434">OpenPaneLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-434">OpenPaneLegacy</span></span></td>
 </tr>
 <tr><td>![WorldLegacy](images/segoe-mdl/e128.png)</td>
  <td><span data-ttu-id="127e7-436">E128</span><span class="sxs-lookup"><span data-stu-id="127e7-436">E128</span></span></td>
  <td><span data-ttu-id="127e7-437">WorldLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-437">WorldLegacy</span></span></td>
 </tr>
 <tr><td>![FlagLegacy](images/segoe-mdl/e129.png)</td>
  <td><span data-ttu-id="127e7-439">E129</span><span class="sxs-lookup"><span data-stu-id="127e7-439">E129</span></span></td>
  <td><span data-ttu-id="127e7-440">FlagLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-440">FlagLegacy</span></span></td>
 </tr>
 <tr><td>![PreviewLinkLegacy](images/segoe-mdl/e12a.png)</td>
  <td><span data-ttu-id="127e7-442">E12A</span><span class="sxs-lookup"><span data-stu-id="127e7-442">E12A</span></span></td>
  <td><span data-ttu-id="127e7-443">PreviewLinkLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-443">PreviewLinkLegacy</span></span></td>
 </tr>
 <tr><td>![GlobeLegacy](images/segoe-mdl/e12b.png)</td>
  <td><span data-ttu-id="127e7-445">E12B</span><span class="sxs-lookup"><span data-stu-id="127e7-445">E12B</span></span></td>
  <td><span data-ttu-id="127e7-446">GlobeLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-446">GlobeLegacy</span></span></td>
 </tr>
 <tr><td>![TrimLegacy](images/segoe-mdl/e12c.png)</td>
  <td><span data-ttu-id="127e7-448">E12C</span><span class="sxs-lookup"><span data-stu-id="127e7-448">E12C</span></span></td>
  <td><span data-ttu-id="127e7-449">TrimLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-449">TrimLegacy</span></span></td>
 </tr>
 <tr><td>![AttachCameraLegacy](images/segoe-mdl/e12d.png)</td>
  <td><span data-ttu-id="127e7-451">E12D</span><span class="sxs-lookup"><span data-stu-id="127e7-451">E12D</span></span></td>
  <td><span data-ttu-id="127e7-452">AttachCameraLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-452">AttachCameraLegacy</span></span></td>
 </tr>
 <tr><td>![ZoomInLegacy](images/segoe-mdl/e12e.png)</td>
  <td><span data-ttu-id="127e7-454">E12E</span><span class="sxs-lookup"><span data-stu-id="127e7-454">E12E</span></span></td>
  <td><span data-ttu-id="127e7-455">ZoomInLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-455">ZoomInLegacy</span></span></td>
 </tr>
 <tr><td>![BookmarksLegacy](images/segoe-mdl/e12f.png)</td>
  <td><span data-ttu-id="127e7-457">E12F</span><span class="sxs-lookup"><span data-stu-id="127e7-457">E12F</span></span></td>
  <td><span data-ttu-id="127e7-458">BookmarksLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-458">BookmarksLegacy</span></span></td>
 </tr>
 <tr><td>![DocumentLegacy](images/segoe-mdl/e130.png)</td>
  <td><span data-ttu-id="127e7-460">E130</span><span class="sxs-lookup"><span data-stu-id="127e7-460">E130</span></span></td>
  <td><span data-ttu-id="127e7-461">DocumentLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-461">DocumentLegacy</span></span></td>
 </tr>
 <tr><td>![ProtectedDocumentLegacy](images/segoe-mdl/e131.png)</td>
  <td><span data-ttu-id="127e7-463">E131</span><span class="sxs-lookup"><span data-stu-id="127e7-463">E131</span></span></td>
  <td><span data-ttu-id="127e7-464">ProtectedDocumentLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-464">ProtectedDocumentLegacy</span></span></td>
 </tr>
 <tr><td>![PageFillLegacy](images/segoe-mdl/e132.png)</td>
  <td><span data-ttu-id="127e7-466">E132</span><span class="sxs-lookup"><span data-stu-id="127e7-466">E132</span></span></td>
  <td><span data-ttu-id="127e7-467">PageFillLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-467">PageFillLegacy</span></span></td>
 </tr>
 <tr><td>![MultiSelectLegacy](images/segoe-mdl/e133.png)</td>
  <td><span data-ttu-id="127e7-469">E133</span><span class="sxs-lookup"><span data-stu-id="127e7-469">E133</span></span></td>
  <td><span data-ttu-id="127e7-470">MultiSelectLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-470">MultiSelectLegacy</span></span></td>
 </tr>
 <tr><td>![CommentLegacy](images/segoe-mdl/e134.png)</td>
  <td><span data-ttu-id="127e7-472">E134</span><span class="sxs-lookup"><span data-stu-id="127e7-472">E134</span></span></td>
  <td><span data-ttu-id="127e7-473">CommentLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-473">CommentLegacy</span></span></td>
 </tr>
 <tr><td>![MailFillLegacy](images/segoe-mdl/e135.png)</td>
  <td><span data-ttu-id="127e7-475">E135</span><span class="sxs-lookup"><span data-stu-id="127e7-475">E135</span></span></td>
  <td><span data-ttu-id="127e7-476">MailFillLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-476">MailFillLegacy</span></span></td>
 </tr>
 <tr><td>![ContactInfoLegacy](images/segoe-mdl/e136.png)</td>
  <td><span data-ttu-id="127e7-478">E136</span><span class="sxs-lookup"><span data-stu-id="127e7-478">E136</span></span></td>
  <td><span data-ttu-id="127e7-479">ContactInfoLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-479">ContactInfoLegacy</span></span></td>
 </tr>
 <tr><td>![HangUpLegacy](images/segoe-mdl/e137.png)</td>
  <td><span data-ttu-id="127e7-481">E137</span><span class="sxs-lookup"><span data-stu-id="127e7-481">E137</span></span></td>
  <td><span data-ttu-id="127e7-482">HangUpLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-482">HangUpLegacy</span></span></td>
 </tr>
 <tr><td>![ViewAllLegacy](images/segoe-mdl/e138.png)</td>
  <td><span data-ttu-id="127e7-484">E138</span><span class="sxs-lookup"><span data-stu-id="127e7-484">E138</span></span></td>
  <td><span data-ttu-id="127e7-485">ViewAllLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-485">ViewAllLegacy</span></span></td>
 </tr>
 <tr><td>![MapPinLegacy](images/segoe-mdl/e139.png)</td>
  <td><span data-ttu-id="127e7-487">E139</span><span class="sxs-lookup"><span data-stu-id="127e7-487">E139</span></span></td>
  <td><span data-ttu-id="127e7-488">MapPinLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-488">MapPinLegacy</span></span></td>
 </tr>
 <tr><td>![PhoneLegacy](images/segoe-mdl/e13a.png)</td>
  <td><span data-ttu-id="127e7-490">E13A</span><span class="sxs-lookup"><span data-stu-id="127e7-490">E13A</span></span></td>
  <td><span data-ttu-id="127e7-491">PhoneLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-491">PhoneLegacy</span></span></td>
 </tr>
 <tr><td>![VideoChatLegacy](images/segoe-mdl/e13b.png)</td>
  <td><span data-ttu-id="127e7-493">E13B</span><span class="sxs-lookup"><span data-stu-id="127e7-493">E13B</span></span></td>
  <td><span data-ttu-id="127e7-494">VideoChatLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-494">VideoChatLegacy</span></span></td>
 </tr>
 <tr><td>![SwitchLegacy](images/segoe-mdl/e13c.png)</td>
  <td><span data-ttu-id="127e7-496">E13C</span><span class="sxs-lookup"><span data-stu-id="127e7-496">E13C</span></span></td>
  <td><span data-ttu-id="127e7-497">SwitchLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-497">SwitchLegacy</span></span></td>
 </tr>
 <tr><td>![ContactLegacy](images/segoe-mdl/e13d.png)</td>
  <td><span data-ttu-id="127e7-499">E13D</span><span class="sxs-lookup"><span data-stu-id="127e7-499">E13D</span></span></td>
  <td><span data-ttu-id="127e7-500">ContactLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-500">ContactLegacy</span></span></td>
 </tr>
 <tr><td>![RenameLegacy](images/segoe-mdl/e13e.png)</td>
  <td><span data-ttu-id="127e7-502">E13E</span><span class="sxs-lookup"><span data-stu-id="127e7-502">E13E</span></span></td>
  <td><span data-ttu-id="127e7-503">RenameLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-503">RenameLegacy</span></span></td>
 </tr>
 <tr><td>![ExpandTileLegacy](images/segoe-mdl/e13f.png)</td>
  <td><span data-ttu-id="127e7-505">E13F</span><span class="sxs-lookup"><span data-stu-id="127e7-505">E13F</span></span></td>
  <td><span data-ttu-id="127e7-506">ExpandTileLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-506">ExpandTileLegacy</span></span></td>
 </tr>
 <tr><td>![ReduceTileLegacy](images/segoe-mdl/e140.png)</td>
  <td><span data-ttu-id="127e7-508">E140</span><span class="sxs-lookup"><span data-stu-id="127e7-508">E140</span></span></td>
  <td><span data-ttu-id="127e7-509">ReduceTileLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-509">ReduceTileLegacy</span></span></td>
 </tr>
 <tr><td>![PinLegacy](images/segoe-mdl/e141.png)</td>
  <td><span data-ttu-id="127e7-511">E141</span><span class="sxs-lookup"><span data-stu-id="127e7-511">E141</span></span></td>
  <td><span data-ttu-id="127e7-512">PinLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-512">PinLegacy</span></span></td>
 </tr>
 <tr><td>![MusicInfoLegacy](images/segoe-mdl/e142.png)</td>
  <td><span data-ttu-id="127e7-514">E142</span><span class="sxs-lookup"><span data-stu-id="127e7-514">E142</span></span></td>
  <td><span data-ttu-id="127e7-515">MusicInfoLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-515">MusicInfoLegacy</span></span></td>
 </tr>
 <tr><td>![GoLegacy](images/segoe-mdl/e143.png)</td>
  <td><span data-ttu-id="127e7-517">E143</span><span class="sxs-lookup"><span data-stu-id="127e7-517">E143</span></span></td>
  <td><span data-ttu-id="127e7-518">GoLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-518">GoLegacy</span></span></td>
 </tr>
 <tr><td>![KeyBoardLegacy](images/segoe-mdl/e144.png)</td>
  <td><span data-ttu-id="127e7-520">E144</span><span class="sxs-lookup"><span data-stu-id="127e7-520">E144</span></span></td>
  <td><span data-ttu-id="127e7-521">KeyBoardLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-521">KeyBoardLegacy</span></span></td>
 </tr>
 <tr><td>![DockLeftLegacy](images/segoe-mdl/e145.png)</td>
  <td><span data-ttu-id="127e7-523">E145</span><span class="sxs-lookup"><span data-stu-id="127e7-523">E145</span></span></td>
  <td><span data-ttu-id="127e7-524">DockLeftLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-524">DockLeftLegacy</span></span></td>
 </tr>
 <tr><td>![DockRightLegacy](images/segoe-mdl/e146.png)</td>
  <td><span data-ttu-id="127e7-526">E146</span><span class="sxs-lookup"><span data-stu-id="127e7-526">E146</span></span></td>
  <td><span data-ttu-id="127e7-527">DockRightLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-527">DockRightLegacy</span></span></td>
 </tr>
 <tr><td>![DockBottomLegacy](images/segoe-mdl/e147.png)</td>
  <td><span data-ttu-id="127e7-529">E147</span><span class="sxs-lookup"><span data-stu-id="127e7-529">E147</span></span></td>
  <td><span data-ttu-id="127e7-530">DockBottomLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-530">DockBottomLegacy</span></span></td>
 </tr>
 <tr><td>![RemoteLegacy](images/segoe-mdl/e148.png)</td>
  <td><span data-ttu-id="127e7-532">E148</span><span class="sxs-lookup"><span data-stu-id="127e7-532">E148</span></span></td>
  <td><span data-ttu-id="127e7-533">RemoteLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-533">RemoteLegacy</span></span></td>
 </tr>
 <tr><td>![RefreshLegacy](images/segoe-mdl/e149.png)</td>
  <td><span data-ttu-id="127e7-535">E149</span><span class="sxs-lookup"><span data-stu-id="127e7-535">E149</span></span></td>
  <td><span data-ttu-id="127e7-536">RefreshLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-536">RefreshLegacy</span></span></td>
 </tr>
 <tr><td>![RotateLegacy](images/segoe-mdl/e14a.png)</td>
  <td><span data-ttu-id="127e7-538">E14A</span><span class="sxs-lookup"><span data-stu-id="127e7-538">E14A</span></span></td>
  <td><span data-ttu-id="127e7-539">RotateLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-539">RotateLegacy</span></span></td>
 </tr>
 <tr><td>![ShuffleLegacy](images/segoe-mdl/e14b.png)</td>
  <td><span data-ttu-id="127e7-541">E14B</span><span class="sxs-lookup"><span data-stu-id="127e7-541">E14B</span></span></td>
  <td><span data-ttu-id="127e7-542">ShuffleLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-542">ShuffleLegacy</span></span></td>
 </tr>
 <tr><td>![ListLegacy](images/segoe-mdl/e14c.png)</td>
  <td><span data-ttu-id="127e7-544">E14C</span><span class="sxs-lookup"><span data-stu-id="127e7-544">E14C</span></span></td>
  <td><span data-ttu-id="127e7-545">ListLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-545">ListLegacy</span></span></td>
 </tr>
 <tr><td>![ShopLegacy](images/segoe-mdl/e14d.png)</td>
  <td><span data-ttu-id="127e7-547">E14D</span><span class="sxs-lookup"><span data-stu-id="127e7-547">E14D</span></span></td>
  <td><span data-ttu-id="127e7-548">ShopLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-548">ShopLegacy</span></span></td>
 </tr>
 <tr><td>![SelectAllLegacy](images/segoe-mdl/e14e.png)</td>
  <td><span data-ttu-id="127e7-550">E14E</span><span class="sxs-lookup"><span data-stu-id="127e7-550">E14E</span></span></td>
  <td><span data-ttu-id="127e7-551">SelectAllLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-551">SelectAllLegacy</span></span></td>
 </tr>
 <tr><td>![OrientationLegacy](images/segoe-mdl/e14f.png)</td>
  <td><span data-ttu-id="127e7-553">E14F</span><span class="sxs-lookup"><span data-stu-id="127e7-553">E14F</span></span></td>
  <td><span data-ttu-id="127e7-554">OrientationLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-554">OrientationLegacy</span></span></td>
 </tr>
 <tr><td>![ImportLegacy](images/segoe-mdl/e150.png)</td>
  <td><span data-ttu-id="127e7-556">E150</span><span class="sxs-lookup"><span data-stu-id="127e7-556">E150</span></span></td>
  <td><span data-ttu-id="127e7-557">ImportLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-557">ImportLegacy</span></span></td>
 </tr>
 <tr><td>![ImportAllLegacy](images/segoe-mdl/e151.png)</td>
  <td><span data-ttu-id="127e7-559">E151</span><span class="sxs-lookup"><span data-stu-id="127e7-559">E151</span></span></td>
  <td><span data-ttu-id="127e7-560">ImportAllLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-560">ImportAllLegacy</span></span></td>
 </tr>
 <tr><td>![ShowAllFiles3Legacy](images/segoe-mdl/e152.png)</td>
  <td><span data-ttu-id="127e7-562">E152</span><span class="sxs-lookup"><span data-stu-id="127e7-562">E152</span></span></td>
  <td><span data-ttu-id="127e7-563">ShowAllFiles3Legacy</span><span class="sxs-lookup"><span data-stu-id="127e7-563">ShowAllFiles3Legacy</span></span></td>
 </tr>
 <tr><td>![ShowAllFiles1Legacy](images/segoe-mdl/e153.png)</td>
  <td><span data-ttu-id="127e7-565">E153</span><span class="sxs-lookup"><span data-stu-id="127e7-565">E153</span></span></td>
  <td><span data-ttu-id="127e7-566">ShowAllFiles1Legacy</span><span class="sxs-lookup"><span data-stu-id="127e7-566">ShowAllFiles1Legacy</span></span></td>
 </tr>
 <tr><td>![ShowAllFilesLegacy](images/segoe-mdl/e154.png)</td>
  <td><span data-ttu-id="127e7-568">E154</span><span class="sxs-lookup"><span data-stu-id="127e7-568">E154</span></span></td>
  <td><span data-ttu-id="127e7-569">ShowAllFilesLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-569">ShowAllFilesLegacy</span></span></td>
 </tr>
 <tr><td>![BrowsePhotosLegacy](images/segoe-mdl/e155.png)</td>
  <td><span data-ttu-id="127e7-571">E155</span><span class="sxs-lookup"><span data-stu-id="127e7-571">E155</span></span></td>
  <td><span data-ttu-id="127e7-572">BrowsePhotosLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-572">BrowsePhotosLegacy</span></span></td>
 </tr>
 <tr><td>![WebcamLegacy](images/segoe-mdl/e156.png)</td>
  <td><span data-ttu-id="127e7-574">E156</span><span class="sxs-lookup"><span data-stu-id="127e7-574">E156</span></span></td>
  <td><span data-ttu-id="127e7-575">WebcamLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-575">WebcamLegacy</span></span></td>
 </tr>
 <tr><td>![PictureLegacy](images/segoe-mdl/e158.png)</td>
  <td><span data-ttu-id="127e7-577">E158</span><span class="sxs-lookup"><span data-stu-id="127e7-577">E158</span></span></td>
  <td><span data-ttu-id="127e7-578">PictureLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-578">PictureLegacy</span></span></td>
 </tr>
 <tr><td>![SaveLocalLegacy](images/segoe-mdl/e159.png)</td>
  <td><span data-ttu-id="127e7-580">E159</span><span class="sxs-lookup"><span data-stu-id="127e7-580">E159</span></span></td>
  <td><span data-ttu-id="127e7-581">SaveLocalLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-581">SaveLocalLegacy</span></span></td>
 </tr>
 <tr><td>![CaptionLegacy](images/segoe-mdl/e15a.png)</td>
  <td><span data-ttu-id="127e7-583">E15A</span><span class="sxs-lookup"><span data-stu-id="127e7-583">E15A</span></span></td>
  <td><span data-ttu-id="127e7-584">CaptionLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-584">CaptionLegacy</span></span></td>
 </tr>
 <tr><td>![StopLegacy](images/segoe-mdl/e15b.png)</td>
  <td><span data-ttu-id="127e7-586">E15B</span><span class="sxs-lookup"><span data-stu-id="127e7-586">E15B</span></span></td>
  <td><span data-ttu-id="127e7-587">StopLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-587">StopLegacy</span></span></td>
 </tr>
 <tr><td>![ShowResultsLegacy](images/segoe-mdl/e15c.png)</td>
  <td><span data-ttu-id="127e7-589">E15C</span><span class="sxs-lookup"><span data-stu-id="127e7-589">E15C</span></span></td>
  <td><span data-ttu-id="127e7-590">ShowResultsLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-590">ShowResultsLegacy</span></span></td>
 </tr>
 <tr><td>![VolumeLegacy](images/segoe-mdl/e15d.png)</td>
  <td><span data-ttu-id="127e7-592">E15D</span><span class="sxs-lookup"><span data-stu-id="127e7-592">E15D</span></span></td>
  <td><span data-ttu-id="127e7-593">VolumeLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-593">VolumeLegacy</span></span></td>
 </tr>
 <tr><td>![RepairLegacy](images/segoe-mdl/e15e.png)</td>
  <td><span data-ttu-id="127e7-595">E15E</span><span class="sxs-lookup"><span data-stu-id="127e7-595">E15E</span></span></td>
  <td><span data-ttu-id="127e7-596">RepairLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-596">RepairLegacy</span></span></td>
 </tr>
 <tr><td>![MessageLegacy](images/segoe-mdl/e15f.png)</td>
  <td><span data-ttu-id="127e7-598">E15F</span><span class="sxs-lookup"><span data-stu-id="127e7-598">E15F</span></span></td>
  <td><span data-ttu-id="127e7-599">MessageLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-599">MessageLegacy</span></span></td>
 </tr>
 <tr><td>![PageLegacy](images/segoe-mdl/e160.png)</td>
  <td><span data-ttu-id="127e7-601">E160</span><span class="sxs-lookup"><span data-stu-id="127e7-601">E160</span></span></td>
  <td><span data-ttu-id="127e7-602">PageLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-602">PageLegacy</span></span></td>
 </tr>
 <tr><td>![CalendarDayLegacy](images/segoe-mdl/e161.png)</td>
  <td><span data-ttu-id="127e7-604">E161</span><span class="sxs-lookup"><span data-stu-id="127e7-604">E161</span></span></td>
  <td><span data-ttu-id="127e7-605">CalendarDayLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-605">CalendarDayLegacy</span></span></td>
 </tr>
 <tr><td>![CalendarWeekLegacy](images/segoe-mdl/e162.png)</td>
  <td><span data-ttu-id="127e7-607">E162</span><span class="sxs-lookup"><span data-stu-id="127e7-607">E162</span></span></td>
  <td><span data-ttu-id="127e7-608">CalendarWeekLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-608">CalendarWeekLegacy</span></span></td>
 </tr>
 <tr><td>![CalendarLegacy](images/segoe-mdl/e163.png)</td>
  <td><span data-ttu-id="127e7-610">E163</span><span class="sxs-lookup"><span data-stu-id="127e7-610">E163</span></span></td>
  <td><span data-ttu-id="127e7-611">CalendarLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-611">CalendarLegacy</span></span></td>
 </tr>
 <tr><td>![CharactersLegacy](images/segoe-mdl/e164.png)</td>
  <td><span data-ttu-id="127e7-613">E164</span><span class="sxs-lookup"><span data-stu-id="127e7-613">E164</span></span></td>
  <td><span data-ttu-id="127e7-614">CharactersLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-614">CharactersLegacy</span></span></td>
 </tr>
 <tr><td>![MailReplyAllLegacy](images/segoe-mdl/e165.png)</td>
  <td><span data-ttu-id="127e7-616">E165</span><span class="sxs-lookup"><span data-stu-id="127e7-616">E165</span></span></td>
  <td><span data-ttu-id="127e7-617">MailReplyAllLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-617">MailReplyAllLegacy</span></span></td>
 </tr>
 <tr><td>![ReadLegacy](images/segoe-mdl/e166.png)</td>
  <td><span data-ttu-id="127e7-619">E166</span><span class="sxs-lookup"><span data-stu-id="127e7-619">E166</span></span></td>
  <td><span data-ttu-id="127e7-620">ReadLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-620">ReadLegacy</span></span></td>
 </tr>
 <tr><td>![LinkLegacy](images/segoe-mdl/e167.png)</td>
  <td><span data-ttu-id="127e7-622">E167</span><span class="sxs-lookup"><span data-stu-id="127e7-622">E167</span></span></td>
  <td><span data-ttu-id="127e7-623">LinkLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-623">LinkLegacy</span></span></td>
 </tr>
 <tr><td>![AccountsLegacy](images/segoe-mdl/e168.png)</td>
  <td><span data-ttu-id="127e7-625">E168</span><span class="sxs-lookup"><span data-stu-id="127e7-625">E168</span></span></td>
  <td><span data-ttu-id="127e7-626">AccountsLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-626">AccountsLegacy</span></span></td>
 </tr>
 <tr><td>![ShowBccLegacy](images/segoe-mdl/e169.png)</td>
  <td><span data-ttu-id="127e7-628">E169</span><span class="sxs-lookup"><span data-stu-id="127e7-628">E169</span></span></td>
  <td><span data-ttu-id="127e7-629">ShowBccLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-629">ShowBccLegacy</span></span></td>
 </tr>
 <tr><td>![HideBccLegacy](images/segoe-mdl/e16a.png)</td>
  <td><span data-ttu-id="127e7-631">E16A</span><span class="sxs-lookup"><span data-stu-id="127e7-631">E16A</span></span></td>
  <td><span data-ttu-id="127e7-632">HideBccLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-632">HideBccLegacy</span></span></td>
 </tr>
 <tr><td>![CutLegacy](images/segoe-mdl/e16b.png)</td>
  <td><span data-ttu-id="127e7-634">E16B</span><span class="sxs-lookup"><span data-stu-id="127e7-634">E16B</span></span></td>
  <td><span data-ttu-id="127e7-635">CutLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-635">CutLegacy</span></span></td>
 </tr>
 <tr><td>![AttachLegacy](images/segoe-mdl/e16c.png)</td>
  <td><span data-ttu-id="127e7-637">E16C</span><span class="sxs-lookup"><span data-stu-id="127e7-637">E16C</span></span></td>
  <td><span data-ttu-id="127e7-638">AttachLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-638">AttachLegacy</span></span></td>
 </tr>
 <tr><td>![PasteLegacy](images/segoe-mdl/e16d.png)</td>
  <td><span data-ttu-id="127e7-640">E16D</span><span class="sxs-lookup"><span data-stu-id="127e7-640">E16D</span></span></td>
  <td><span data-ttu-id="127e7-641">PasteLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-641">PasteLegacy</span></span></td>
 </tr>
 <tr><td>![FilterLegacy](images/segoe-mdl/e16e.png)</td>
  <td><span data-ttu-id="127e7-643">E16E</span><span class="sxs-lookup"><span data-stu-id="127e7-643">E16E</span></span></td>
  <td><span data-ttu-id="127e7-644">FilterLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-644">FilterLegacy</span></span></td>
 </tr>
 <tr><td>![CopyLegacy](images/segoe-mdl/e16f.png)</td>
  <td><span data-ttu-id="127e7-646">E16F</span><span class="sxs-lookup"><span data-stu-id="127e7-646">E16F</span></span></td>
  <td><span data-ttu-id="127e7-647">CopyLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-647">CopyLegacy</span></span></td>
 </tr>
 <tr><td>![Emoji2Legacy](images/segoe-mdl/e170.png)</td>
  <td><span data-ttu-id="127e7-649">E170</span><span class="sxs-lookup"><span data-stu-id="127e7-649">E170</span></span></td>
  <td><span data-ttu-id="127e7-650">Emoji2Legacy</span><span class="sxs-lookup"><span data-stu-id="127e7-650">Emoji2Legacy</span></span></td>
 </tr>
 <tr><td>![ImportantLegacy](images/segoe-mdl/e171.png)</td>
  <td><span data-ttu-id="127e7-652">E171</span><span class="sxs-lookup"><span data-stu-id="127e7-652">E171</span></span></td>
  <td><span data-ttu-id="127e7-653">ImportantLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-653">ImportantLegacy</span></span></td>
 </tr>
 <tr><td>![MailReplyLegacy](images/segoe-mdl/e172.png)</td>
  <td><span data-ttu-id="127e7-655">E172</span><span class="sxs-lookup"><span data-stu-id="127e7-655">E172</span></span></td>
  <td><span data-ttu-id="127e7-656">MailReplyLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-656">MailReplyLegacy</span></span></td>
 </tr>
 <tr><td>![SlideshowLegacy](images/segoe-mdl/e173.png)</td>
  <td><span data-ttu-id="127e7-658">E173</span><span class="sxs-lookup"><span data-stu-id="127e7-658">E173</span></span></td>
  <td><span data-ttu-id="127e7-659">SlideshowLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-659">SlideshowLegacy</span></span></td>
 </tr>
 <tr><td>![SortLegacy](images/segoe-mdl/e174.png)</td>
  <td><span data-ttu-id="127e7-661">E174</span><span class="sxs-lookup"><span data-stu-id="127e7-661">E174</span></span></td>
  <td><span data-ttu-id="127e7-662">SortLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-662">SortLegacy</span></span></td>
 </tr>
 <tr><td>![ListLegacyMirrored](images/segoe-mdl/e175.png)</td>
  <td><span data-ttu-id="127e7-664">E175</span><span class="sxs-lookup"><span data-stu-id="127e7-664">E175</span></span></td>
  <td><span data-ttu-id="127e7-665">ListLegacyMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-665">ListLegacyMirrored</span></span></td>
 </tr>
 <tr><td>![ExpandTileLegacyMirrored](images/segoe-mdl/e176.png)</td>
  <td><span data-ttu-id="127e7-667">E176</span><span class="sxs-lookup"><span data-stu-id="127e7-667">E176</span></span></td>
  <td><span data-ttu-id="127e7-668">ExpandTileLegacyMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-668">ExpandTileLegacyMirrored</span></span></td>
 </tr>
 <tr><td>![ReduceTileLegacyMirrored](images/segoe-mdl/e177.png)</td>
  <td><span data-ttu-id="127e7-670">E177</span><span class="sxs-lookup"><span data-stu-id="127e7-670">E177</span></span></td>
  <td><span data-ttu-id="127e7-671">ReduceTileLegacyMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-671">ReduceTileLegacyMirrored</span></span></td>
 </tr>
 <tr><td>![ManageLegacy](images/segoe-mdl/e178.png)</td>
  <td><span data-ttu-id="127e7-673">E178</span><span class="sxs-lookup"><span data-stu-id="127e7-673">E178</span></span></td>
  <td><span data-ttu-id="127e7-674">ManageLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-674">ManageLegacy</span></span></td>
 </tr>
 <tr><td>![AllAppsLegacy](images/segoe-mdl/e179.png)</td>
  <td><span data-ttu-id="127e7-676">E179</span><span class="sxs-lookup"><span data-stu-id="127e7-676">E179</span></span></td>
  <td><span data-ttu-id="127e7-677">AllAppsLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-677">AllAppsLegacy</span></span></td>
 </tr>
 <tr><td>![DisconnectDriveLegacy](images/segoe-mdl/e17a.png)</td>
  <td><span data-ttu-id="127e7-679">E17A</span><span class="sxs-lookup"><span data-stu-id="127e7-679">E17A</span></span></td>
  <td><span data-ttu-id="127e7-680">DisconnectDriveLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-680">DisconnectDriveLegacy</span></span></td>
 </tr>
 <tr><td>![MapDriveLegacy](images/segoe-mdl/e17b.png)</td>
  <td><span data-ttu-id="127e7-682">E17B</span><span class="sxs-lookup"><span data-stu-id="127e7-682">E17B</span></span></td>
  <td><span data-ttu-id="127e7-683">MapDriveLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-683">MapDriveLegacy</span></span></td>
 </tr>
 <tr><td>![NewWindowLegacy](images/segoe-mdl/e17c.png)</td>
  <td><span data-ttu-id="127e7-685">E17C</span><span class="sxs-lookup"><span data-stu-id="127e7-685">E17C</span></span></td>
  <td><span data-ttu-id="127e7-686">NewWindowLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-686">NewWindowLegacy</span></span></td>
 </tr>
 <tr><td>![OpenWithLegacy](images/segoe-mdl/e17d.png)</td>
  <td><span data-ttu-id="127e7-688">E17D</span><span class="sxs-lookup"><span data-stu-id="127e7-688">E17D</span></span></td>
  <td><span data-ttu-id="127e7-689">OpenWithLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-689">OpenWithLegacy</span></span></td>
 </tr>
 <tr><td>![ContactPresenceLegacy](images/segoe-mdl/e181.png)</td>
  <td><span data-ttu-id="127e7-691">E181</span><span class="sxs-lookup"><span data-stu-id="127e7-691">E181</span></span></td>
  <td><span data-ttu-id="127e7-692">ContactPresenceLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-692">ContactPresenceLegacy</span></span></td>
 </tr>
 <tr><td>![PriorityLegacy](images/segoe-mdl/e182.png)</td>
  <td><span data-ttu-id="127e7-694">E182</span><span class="sxs-lookup"><span data-stu-id="127e7-694">E182</span></span></td>
  <td><span data-ttu-id="127e7-695">PriorityLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-695">PriorityLegacy</span></span></td>
 </tr>
 <tr><td>![UploadSkyDriveLegacy](images/segoe-mdl/e183.png)</td>
  <td><span data-ttu-id="127e7-697">E183</span><span class="sxs-lookup"><span data-stu-id="127e7-697">E183</span></span></td>
  <td><span data-ttu-id="127e7-698">UploadSkyDriveLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-698">UploadSkyDriveLegacy</span></span></td>
 </tr>
 <tr><td>![GotoTodayLegacy](images/segoe-mdl/e184.png)</td>
  <td><span data-ttu-id="127e7-700">E184</span><span class="sxs-lookup"><span data-stu-id="127e7-700">E184</span></span></td>
  <td><span data-ttu-id="127e7-701">GotoTodayLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-701">GotoTodayLegacy</span></span></td>
 </tr>
 <tr><td>![FontLegacy](images/segoe-mdl/e185.png)</td>
  <td><span data-ttu-id="127e7-703">E185</span><span class="sxs-lookup"><span data-stu-id="127e7-703">E185</span></span></td>
  <td><span data-ttu-id="127e7-704">FontLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-704">FontLegacy</span></span></td>
 </tr>
 <tr><td>![FontColorLegacy](images/segoe-mdl/e186.png)</td>
  <td><span data-ttu-id="127e7-706">E186</span><span class="sxs-lookup"><span data-stu-id="127e7-706">E186</span></span></td>
  <td><span data-ttu-id="127e7-707">FontColorLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-707">FontColorLegacy</span></span></td>
 </tr>
 <tr><td>![Contact2Legacy](images/segoe-mdl/e187.png)</td>
  <td><span data-ttu-id="127e7-709">E187</span><span class="sxs-lookup"><span data-stu-id="127e7-709">E187</span></span></td>
  <td><span data-ttu-id="127e7-710">Contact2Legacy</span><span class="sxs-lookup"><span data-stu-id="127e7-710">Contact2Legacy</span></span></td>
 </tr>
 <tr><td>![FolderLegacy](images/segoe-mdl/e188.png)</td>
  <td><span data-ttu-id="127e7-712">E188</span><span class="sxs-lookup"><span data-stu-id="127e7-712">E188</span></span></td>
  <td><span data-ttu-id="127e7-713">FolderLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-713">FolderLegacy</span></span></td>
 </tr>
 <tr><td>![AudioLegacy](images/segoe-mdl/e189.png)</td>
  <td><span data-ttu-id="127e7-715">E189</span><span class="sxs-lookup"><span data-stu-id="127e7-715">E189</span></span></td>
  <td><span data-ttu-id="127e7-716">AudioLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-716">AudioLegacy</span></span></td>
 </tr>
 <tr><td>![PlaceFolderLegacy](images/segoe-mdl/e18a.png)</td>
  <td><span data-ttu-id="127e7-718">E18A</span><span class="sxs-lookup"><span data-stu-id="127e7-718">E18A</span></span></td>
  <td><span data-ttu-id="127e7-719">PlaceFolderLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-719">PlaceFolderLegacy</span></span></td>
 </tr>
 <tr><td>![ViewLegacy](images/segoe-mdl/e18b.png)</td>
  <td><span data-ttu-id="127e7-721">E18B</span><span class="sxs-lookup"><span data-stu-id="127e7-721">E18B</span></span></td>
  <td><span data-ttu-id="127e7-722">ViewLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-722">ViewLegacy</span></span></td>
 </tr>
 <tr><td>![SetlockScreenLegacy](images/segoe-mdl/e18c.png)</td>
  <td><span data-ttu-id="127e7-724">E18C</span><span class="sxs-lookup"><span data-stu-id="127e7-724">E18C</span></span></td>
  <td><span data-ttu-id="127e7-725">SetlockScreenLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-725">SetlockScreenLegacy</span></span></td>
 </tr>
 <tr><td>![SetTileLegacy](images/segoe-mdl/e18d.png)</td>
  <td><span data-ttu-id="127e7-727">E18D</span><span class="sxs-lookup"><span data-stu-id="127e7-727">E18D</span></span></td>
  <td><span data-ttu-id="127e7-728">SetTileLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-728">SetTileLegacy</span></span></td>
 </tr>
 <tr><td>![CCJapanLegacy](images/segoe-mdl/e18e.png)</td>
  <td><span data-ttu-id="127e7-730">E18E</span><span class="sxs-lookup"><span data-stu-id="127e7-730">E18E</span></span></td>
  <td><span data-ttu-id="127e7-731">CCJapanLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-731">CCJapanLegacy</span></span></td>
 </tr>
 <tr><td>![CCEuroLegacy](images/segoe-mdl/e18f.png)</td>
  <td><span data-ttu-id="127e7-733">E18F</span><span class="sxs-lookup"><span data-stu-id="127e7-733">E18F</span></span></td>
  <td><span data-ttu-id="127e7-734">CCEuroLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-734">CCEuroLegacy</span></span></td>
 </tr>
 <tr><td>![CCLegacy](images/segoe-mdl/e190.png)</td>
  <td><span data-ttu-id="127e7-736">E190</span><span class="sxs-lookup"><span data-stu-id="127e7-736">E190</span></span></td>
  <td><span data-ttu-id="127e7-737">CCLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-737">CCLegacy</span></span></td>
 </tr>
 <tr><td>![StopSlideshowLegacy](images/segoe-mdl/e191.png)</td>
  <td><span data-ttu-id="127e7-739">E191</span><span class="sxs-lookup"><span data-stu-id="127e7-739">E191</span></span></td>
  <td><span data-ttu-id="127e7-740">StopSlideshowLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-740">StopSlideshowLegacy</span></span></td>
 </tr>
 <tr><td>![PermissionsLegacy](images/segoe-mdl/e192.png)</td>
  <td><span data-ttu-id="127e7-742">E192</span><span class="sxs-lookup"><span data-stu-id="127e7-742">E192</span></span></td>
  <td><span data-ttu-id="127e7-743">PermissionsLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-743">PermissionsLegacy</span></span></td>
 </tr>
 <tr><td>![HighlightLegacy](images/segoe-mdl/e193.png)</td>
  <td><span data-ttu-id="127e7-745">E193</span><span class="sxs-lookup"><span data-stu-id="127e7-745">E193</span></span></td>
  <td><span data-ttu-id="127e7-746">HighlightLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-746">HighlightLegacy</span></span></td>
 </tr>
 <tr><td>![DisableUpdatesLegacy](images/segoe-mdl/e194.png)</td>
  <td><span data-ttu-id="127e7-748">E194</span><span class="sxs-lookup"><span data-stu-id="127e7-748">E194</span></span></td>
  <td><span data-ttu-id="127e7-749">DisableUpdatesLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-749">DisableUpdatesLegacy</span></span></td>
 </tr>
 <tr><td>![UnfavoriteLegacy](images/segoe-mdl/e195.png)</td>
  <td><span data-ttu-id="127e7-751">E195</span><span class="sxs-lookup"><span data-stu-id="127e7-751">E195</span></span></td>
  <td><span data-ttu-id="127e7-752">UnfavoriteLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-752">UnfavoriteLegacy</span></span></td>
 </tr>
 <tr><td>![UnpinLegacy](images/segoe-mdl/e196.png)</td>
  <td><span data-ttu-id="127e7-754">E196</span><span class="sxs-lookup"><span data-stu-id="127e7-754">E196</span></span></td>
  <td><span data-ttu-id="127e7-755">UnpinLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-755">UnpinLegacy</span></span></td>
 </tr>
 <tr><td>![OpenLocalLegacy](images/segoe-mdl/e197.png)</td>
  <td><span data-ttu-id="127e7-757">E197</span><span class="sxs-lookup"><span data-stu-id="127e7-757">E197</span></span></td>
  <td><span data-ttu-id="127e7-758">OpenLocalLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-758">OpenLocalLegacy</span></span></td>
 </tr>
 <tr><td>![MuteLegacy](images/segoe-mdl/e198.png)</td>
  <td><span data-ttu-id="127e7-760">E198</span><span class="sxs-lookup"><span data-stu-id="127e7-760">E198</span></span></td>
  <td><span data-ttu-id="127e7-761">MuteLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-761">MuteLegacy</span></span></td>
 </tr>
 <tr><td>![ItalicLegacy](images/segoe-mdl/e199.png)</td>
  <td><span data-ttu-id="127e7-763">E199</span><span class="sxs-lookup"><span data-stu-id="127e7-763">E199</span></span></td>
  <td><span data-ttu-id="127e7-764">ItalicLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-764">ItalicLegacy</span></span></td>
 </tr>
 <tr><td>![UnderlineLegacy](images/segoe-mdl/e19a.png)</td>
  <td><span data-ttu-id="127e7-766">E19A</span><span class="sxs-lookup"><span data-stu-id="127e7-766">E19A</span></span></td>
  <td><span data-ttu-id="127e7-767">UnderlineLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-767">UnderlineLegacy</span></span></td>
 </tr>
 <tr><td>![BoldLegacy](images/segoe-mdl/e19b.png)</td>
  <td><span data-ttu-id="127e7-769">E19B</span><span class="sxs-lookup"><span data-stu-id="127e7-769">E19B</span></span></td>
  <td><span data-ttu-id="127e7-770">BoldLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-770">BoldLegacy</span></span></td>
 </tr>
 <tr><td>![MoveToFolderLegacy](images/segoe-mdl/e19c.png)</td>
  <td><span data-ttu-id="127e7-772">E19C</span><span class="sxs-lookup"><span data-stu-id="127e7-772">E19C</span></span></td>
  <td><span data-ttu-id="127e7-773">MoveToFolderLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-773">MoveToFolderLegacy</span></span></td>
 </tr>
 <tr><td>![LikeDislikeLegacy](images/segoe-mdl/e19d.png)</td>
  <td><span data-ttu-id="127e7-775">E19D</span><span class="sxs-lookup"><span data-stu-id="127e7-775">E19D</span></span></td>
  <td><span data-ttu-id="127e7-776">LikeDislikeLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-776">LikeDislikeLegacy</span></span></td>
 </tr>
 <tr><td>![DislikeLegacy](images/segoe-mdl/e19e.png)</td>
  <td><span data-ttu-id="127e7-778">E19E</span><span class="sxs-lookup"><span data-stu-id="127e7-778">E19E</span></span></td>
  <td><span data-ttu-id="127e7-779">DislikeLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-779">DislikeLegacy</span></span></td>
 </tr>
 <tr><td>![LikeLegacy](images/segoe-mdl/e19f.png)</td>
  <td><span data-ttu-id="127e7-781">E19F</span><span class="sxs-lookup"><span data-stu-id="127e7-781">E19F</span></span></td>
  <td><span data-ttu-id="127e7-782">LikeLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-782">LikeLegacy</span></span></td>
 </tr>
 <tr><td>![AlignRightLegacy](images/segoe-mdl/e1a0.png)</td>
  <td><span data-ttu-id="127e7-784">E1A0</span><span class="sxs-lookup"><span data-stu-id="127e7-784">E1A0</span></span></td>
  <td><span data-ttu-id="127e7-785">AlignRightLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-785">AlignRightLegacy</span></span></td>
 </tr>
 <tr><td>![AlignCenterLegacy](images/segoe-mdl/e1a1.png)</td>
  <td><span data-ttu-id="127e7-787">E1A1</span><span class="sxs-lookup"><span data-stu-id="127e7-787">E1A1</span></span></td>
  <td><span data-ttu-id="127e7-788">AlignCenterLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-788">AlignCenterLegacy</span></span></td>
 </tr>
 <tr><td>![AlignLeftLegacy](images/segoe-mdl/e1a2.png)</td>
  <td><span data-ttu-id="127e7-790">E1A2</span><span class="sxs-lookup"><span data-stu-id="127e7-790">E1A2</span></span></td>
  <td><span data-ttu-id="127e7-791">AlignLeftLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-791">AlignLeftLegacy</span></span></td>
 </tr>
 <tr><td>![ZoomLegacy](images/segoe-mdl/e1a3.png)</td>
  <td><span data-ttu-id="127e7-793">E1A3</span><span class="sxs-lookup"><span data-stu-id="127e7-793">E1A3</span></span></td>
  <td><span data-ttu-id="127e7-794">ZoomLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-794">ZoomLegacy</span></span></td>
 </tr>
 <tr><td>![ZoomOutLegacy](images/segoe-mdl/e1a4.png)</td>
  <td><span data-ttu-id="127e7-796">E1A4</span><span class="sxs-lookup"><span data-stu-id="127e7-796">E1A4</span></span></td>
  <td><span data-ttu-id="127e7-797">ZoomOutLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-797">ZoomOutLegacy</span></span></td>
 </tr>
 <tr><td>![OpenFileLegacy](images/segoe-mdl/e1a5.png)</td>
  <td><span data-ttu-id="127e7-799">E1A5</span><span class="sxs-lookup"><span data-stu-id="127e7-799">E1A5</span></span></td>
  <td><span data-ttu-id="127e7-800">OpenFileLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-800">OpenFileLegacy</span></span></td>
 </tr>
 <tr><td>![OtherUserLegacy](images/segoe-mdl/e1a6.png)</td>
  <td><span data-ttu-id="127e7-802">E1A6</span><span class="sxs-lookup"><span data-stu-id="127e7-802">E1A6</span></span></td>
  <td><span data-ttu-id="127e7-803">OtherUserLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-803">OtherUserLegacy</span></span></td>
 </tr>
 <tr><td>![AdminLegacy](images/segoe-mdl/e1a7.png)</td>
  <td><span data-ttu-id="127e7-805">E1A7</span><span class="sxs-lookup"><span data-stu-id="127e7-805">E1A7</span></span></td>
  <td><span data-ttu-id="127e7-806">AdminLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-806">AdminLegacy</span></span></td>
 </tr>
 <tr><td>![MailForwardLegacyMirrored](images/segoe-mdl/e1a8.png)</td>
  <td><span data-ttu-id="127e7-808">E1A8</span><span class="sxs-lookup"><span data-stu-id="127e7-808">E1A8</span></span></td>
  <td><span data-ttu-id="127e7-809">MailForwardLegacyMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-809">MailForwardLegacyMirrored</span></span></td>
 </tr>
 <tr><td>![GoLegacyMirrored](images/segoe-mdl/e1aa.png)</td>
  <td><span data-ttu-id="127e7-811">E1AA</span><span class="sxs-lookup"><span data-stu-id="127e7-811">E1AA</span></span></td>
  <td><span data-ttu-id="127e7-812">GoLegacyMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-812">GoLegacyMirrored</span></span></td>
 </tr>
 <tr><td>![DockLeftLegacyMirrored](images/segoe-mdl/e1ab.png)</td>
  <td><span data-ttu-id="127e7-814">E1AB</span><span class="sxs-lookup"><span data-stu-id="127e7-814">E1AB</span></span></td>
  <td><span data-ttu-id="127e7-815">DockLeftLegacyMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-815">DockLeftLegacyMirrored</span></span></td>
 </tr>
 <tr><td>![DockRightLegacyMirrored](images/segoe-mdl/e1ac.png)</td>
  <td><span data-ttu-id="127e7-817">E1AC</span><span class="sxs-lookup"><span data-stu-id="127e7-817">E1AC</span></span></td>
  <td><span data-ttu-id="127e7-818">DockRightLegacyMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-818">DockRightLegacyMirrored</span></span></td>
 </tr>
 <tr><td>![ImportLegacyMirrored](images/segoe-mdl/e1ad.png)</td>
  <td><span data-ttu-id="127e7-820">E1AD</span><span class="sxs-lookup"><span data-stu-id="127e7-820">E1AD</span></span></td>
  <td><span data-ttu-id="127e7-821">ImportLegacyMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-821">ImportLegacyMirrored</span></span></td>
 </tr>
 <tr><td>![ImportAllLegacyMirrored](images/segoe-mdl/e1ae.png)</td>
  <td><span data-ttu-id="127e7-823">E1AE</span><span class="sxs-lookup"><span data-stu-id="127e7-823">E1AE</span></span></td>
  <td><span data-ttu-id="127e7-824">ImportAllLegacyMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-824">ImportAllLegacyMirrored</span></span></td>
 </tr>
 <tr><td>![MailReplyLegacyMirrored](images/segoe-mdl/e1af.png)</td>
  <td><span data-ttu-id="127e7-826">E1AF</span><span class="sxs-lookup"><span data-stu-id="127e7-826">E1AF</span></span></td>
  <td><span data-ttu-id="127e7-827">MailReplyLegacyMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-827">MailReplyLegacyMirrored</span></span></td>
 </tr>
 <tr><td>![ItalicCLegacy](images/segoe-mdl/e1b0.png)</td>
  <td><span data-ttu-id="127e7-829">E1B0</span><span class="sxs-lookup"><span data-stu-id="127e7-829">E1B0</span></span></td>
  <td><span data-ttu-id="127e7-830">ItalicCLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-830">ItalicCLegacy</span></span></td>
 </tr>
 <tr><td>![BoldGLegacy](images/segoe-mdl/e1b1.png)</td>
  <td><span data-ttu-id="127e7-832">E1B1</span><span class="sxs-lookup"><span data-stu-id="127e7-832">E1B1</span></span></td>
  <td><span data-ttu-id="127e7-833">BoldGLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-833">BoldGLegacy</span></span></td>
 </tr>
 <tr><td>![UnderlineSLegacy](images/segoe-mdl/e1b2.png)</td>
  <td><span data-ttu-id="127e7-835">E1B2</span><span class="sxs-lookup"><span data-stu-id="127e7-835">E1B2</span></span></td>
  <td><span data-ttu-id="127e7-836">UnderlineSLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-836">UnderlineSLegacy</span></span></td>
 </tr>
 <tr><td>![BoldFLegacy](images/segoe-mdl/e1b3.png)</td>
  <td><span data-ttu-id="127e7-838">E1B3</span><span class="sxs-lookup"><span data-stu-id="127e7-838">E1B3</span></span></td>
  <td><span data-ttu-id="127e7-839">BoldFLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-839">BoldFLegacy</span></span></td>
 </tr>
 <tr><td>![ItalicKLegacy](images/segoe-mdl/e1b4.png)</td>
  <td><span data-ttu-id="127e7-841">E1B4</span><span class="sxs-lookup"><span data-stu-id="127e7-841">E1B4</span></span></td>
  <td><span data-ttu-id="127e7-842">ItalicKLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-842">ItalicKLegacy</span></span></td>
 </tr>
 <tr><td>![UnderlineULegacy](images/segoe-mdl/e1b5.png)</td>
  <td><span data-ttu-id="127e7-844">E1B5</span><span class="sxs-lookup"><span data-stu-id="127e7-844">E1B5</span></span></td>
  <td><span data-ttu-id="127e7-845">UnderlineULegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-845">UnderlineULegacy</span></span></td>
 </tr>
 <tr><td>![ItalicILegacy](images/segoe-mdl/e1b6.png)</td>
  <td><span data-ttu-id="127e7-847">E1B6</span><span class="sxs-lookup"><span data-stu-id="127e7-847">E1B6</span></span></td>
  <td><span data-ttu-id="127e7-848">ItalicILegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-848">ItalicILegacy</span></span></td>
 </tr>
 <tr><td>![BoldNLegacy](images/segoe-mdl/e1b7.png)</td>
  <td><span data-ttu-id="127e7-850">E1B7</span><span class="sxs-lookup"><span data-stu-id="127e7-850">E1B7</span></span></td>
  <td><span data-ttu-id="127e7-851">BoldNLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-851">BoldNLegacy</span></span></td>
 </tr>
 <tr><td>![UnderlineRussianLegacy](images/segoe-mdl/e1b8.png)</td>
  <td><span data-ttu-id="127e7-853">E1B8</span><span class="sxs-lookup"><span data-stu-id="127e7-853">E1B8</span></span></td>
  <td><span data-ttu-id="127e7-854">UnderlineRussianLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-854">UnderlineRussianLegacy</span></span></td>
 </tr>
 <tr><td>![BoldRussionLegacy](images/segoe-mdl/e1b9.png)</td>
  <td><span data-ttu-id="127e7-856">E1B9</span><span class="sxs-lookup"><span data-stu-id="127e7-856">E1B9</span></span></td>
  <td><span data-ttu-id="127e7-857">BoldRussionLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-857">BoldRussionLegacy</span></span></td>
 </tr>
 <tr><td>![FontStyleKoreanLegacy](images/segoe-mdl/e1ba.png)</td>
  <td><span data-ttu-id="127e7-859">E1BA</span><span class="sxs-lookup"><span data-stu-id="127e7-859">E1BA</span></span></td>
  <td><span data-ttu-id="127e7-860">FontStyleKoreanLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-860">FontStyleKoreanLegacy</span></span></td>
 </tr>
 <tr><td>![UnderlineLKoreanLegacy](images/segoe-mdl/e1bb.png)</td>
  <td><span data-ttu-id="127e7-862">E1BB</span><span class="sxs-lookup"><span data-stu-id="127e7-862">E1BB</span></span></td>
  <td><span data-ttu-id="127e7-863">UnderlineLKoreanLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-863">UnderlineLKoreanLegacy</span></span></td>
 </tr>
 <tr><td>![ItalicKoreanLegacy](images/segoe-mdl/e1bc.png)</td>
  <td><span data-ttu-id="127e7-865">E1BC</span><span class="sxs-lookup"><span data-stu-id="127e7-865">E1BC</span></span></td>
  <td><span data-ttu-id="127e7-866">ItalicKoreanLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-866">ItalicKoreanLegacy</span></span></td>
 </tr>
 <tr><td>![BoldKoreanLegacy](images/segoe-mdl/e1bd.png)</td>
  <td><span data-ttu-id="127e7-868">E1BD</span><span class="sxs-lookup"><span data-stu-id="127e7-868">E1BD</span></span></td>
  <td><span data-ttu-id="127e7-869">BoldKoreanLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-869">BoldKoreanLegacy</span></span></td>
 </tr>
 <tr><td>![FontColorKoreanLegacy](images/segoe-mdl/e1be.png)</td>
  <td><span data-ttu-id="127e7-871">E1BE</span><span class="sxs-lookup"><span data-stu-id="127e7-871">E1BE</span></span></td>
  <td><span data-ttu-id="127e7-872">FontColorKoreanLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-872">FontColorKoreanLegacy</span></span></td>
 </tr>
 <tr><td>![ClosePaneLegacyMirrored](images/segoe-mdl/e1bf.png)</td>
  <td><span data-ttu-id="127e7-874">E1BF</span><span class="sxs-lookup"><span data-stu-id="127e7-874">E1BF</span></span></td>
  <td><span data-ttu-id="127e7-875">ClosePaneLegacyMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-875">ClosePaneLegacyMirrored</span></span></td>
 </tr>
 <tr><td>![OpenPaneLegacyMirrored](images/segoe-mdl/e1c0.png)</td>
  <td><span data-ttu-id="127e7-877">E1C0</span><span class="sxs-lookup"><span data-stu-id="127e7-877">E1C0</span></span></td>
  <td><span data-ttu-id="127e7-878">OpenPaneLegacyMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-878">OpenPaneLegacyMirrored</span></span></td>
 </tr>
 <tr><td>![EditLegacyMirrored](images/segoe-mdl/e1c2.png)</td>
  <td><span data-ttu-id="127e7-880">E1C2</span><span class="sxs-lookup"><span data-stu-id="127e7-880">E1C2</span></span></td>
  <td><span data-ttu-id="127e7-881">EditLegacyMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-881">EditLegacyMirrored</span></span></td>
 </tr>
 <tr><td>![StreetLegacy](images/segoe-mdl/e1c3.png)</td>
  <td><span data-ttu-id="127e7-883">E1C3</span><span class="sxs-lookup"><span data-stu-id="127e7-883">E1C3</span></span></td>
  <td><span data-ttu-id="127e7-884">StreetLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-884">StreetLegacy</span></span></td>
 </tr>
 <tr><td>![MapLegacy](images/segoe-mdl/e1c4.png)</td>
  <td><span data-ttu-id="127e7-886">E1C4</span><span class="sxs-lookup"><span data-stu-id="127e7-886">E1C4</span></span></td>
  <td><span data-ttu-id="127e7-887">MapLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-887">MapLegacy</span></span></td>
 </tr>
 <tr><td>![ClearSelectionLegacy](images/segoe-mdl/e1c5.png)</td>
  <td><span data-ttu-id="127e7-889">E1C5</span><span class="sxs-lookup"><span data-stu-id="127e7-889">E1C5</span></span></td>
  <td><span data-ttu-id="127e7-890">ClearSelectionLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-890">ClearSelectionLegacy</span></span></td>
 </tr>
 <tr><td>![FontDecreaseLegacy](images/segoe-mdl/e1c6.png)</td>
  <td><span data-ttu-id="127e7-892">E1C6</span><span class="sxs-lookup"><span data-stu-id="127e7-892">E1C6</span></span></td>
  <td><span data-ttu-id="127e7-893">FontDecreaseLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-893">FontDecreaseLegacy</span></span></td>
 </tr>
 <tr><td>![FontIncreaseLegacy](images/segoe-mdl/e1c7.png)</td>
  <td><span data-ttu-id="127e7-895">E1C7</span><span class="sxs-lookup"><span data-stu-id="127e7-895">E1C7</span></span></td>
  <td><span data-ttu-id="127e7-896">FontIncreaseLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-896">FontIncreaseLegacy</span></span></td>
 </tr>
 <tr><td>![FontSizeLegacy](images/segoe-mdl/e1c8.png)</td>
  <td><span data-ttu-id="127e7-898">E1C8</span><span class="sxs-lookup"><span data-stu-id="127e7-898">E1C8</span></span></td>
  <td><span data-ttu-id="127e7-899">FontSizeLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-899">FontSizeLegacy</span></span></td>
 </tr>
 <tr><td>![CellPhoneLegacy](images/segoe-mdl/e1c9.png)</td>
  <td><span data-ttu-id="127e7-901">E1C9</span><span class="sxs-lookup"><span data-stu-id="127e7-901">E1C9</span></span></td>
  <td><span data-ttu-id="127e7-902">CellPhoneLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-902">CellPhoneLegacy</span></span></td>
 </tr>
 <tr><td>![ReshareLegacy](images/segoe-mdl/e1ca.png)</td>
  <td><span data-ttu-id="127e7-904">E1CA</span><span class="sxs-lookup"><span data-stu-id="127e7-904">E1CA</span></span></td>
  <td><span data-ttu-id="127e7-905">ReshareLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-905">ReshareLegacy</span></span></td>
 </tr>
 <tr><td>![TagLegacy](images/segoe-mdl/e1cb.png)</td>
  <td><span data-ttu-id="127e7-907">E1CB</span><span class="sxs-lookup"><span data-stu-id="127e7-907">E1CB</span></span></td>
  <td><span data-ttu-id="127e7-908">TagLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-908">TagLegacy</span></span></td>
 </tr>
 <tr><td>![RepeatOneLegacy](images/segoe-mdl/e1cc.png)</td>
  <td><span data-ttu-id="127e7-910">E1CC</span><span class="sxs-lookup"><span data-stu-id="127e7-910">E1CC</span></span></td>
  <td><span data-ttu-id="127e7-911">RepeatOneLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-911">RepeatOneLegacy</span></span></td>
 </tr>
 <tr><td>![RepeatAllLegacy](images/segoe-mdl/e1cd.png)</td>
  <td><span data-ttu-id="127e7-913">E1CD</span><span class="sxs-lookup"><span data-stu-id="127e7-913">E1CD</span></span></td>
  <td><span data-ttu-id="127e7-914">RepeatAllLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-914">RepeatAllLegacy</span></span></td>
 </tr>
 <tr><td>![OutlineStarLegacy](images/segoe-mdl/e1ce.png)</td>
  <td><span data-ttu-id="127e7-916">E1CE</span><span class="sxs-lookup"><span data-stu-id="127e7-916">E1CE</span></span></td>
  <td><span data-ttu-id="127e7-917">OutlineStarLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-917">OutlineStarLegacy</span></span></td>
 </tr>
 <tr><td>![SolidStarLegacy](images/segoe-mdl/e1cf.png)</td>
  <td><span data-ttu-id="127e7-919">E1CF</span><span class="sxs-lookup"><span data-stu-id="127e7-919">E1CF</span></span></td>
  <td><span data-ttu-id="127e7-920">SolidStarLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-920">SolidStarLegacy</span></span></td>
 </tr>
 <tr><td>![CalculatorLegacy](images/segoe-mdl/e1d0.png)</td>
  <td><span data-ttu-id="127e7-922">E1D0</span><span class="sxs-lookup"><span data-stu-id="127e7-922">E1D0</span></span></td>
  <td><span data-ttu-id="127e7-923">CalculatorLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-923">CalculatorLegacy</span></span></td>
 </tr>
 <tr><td>![DirectionsLegacy](images/segoe-mdl/e1d1.png)</td>
  <td><span data-ttu-id="127e7-925">E1D1</span><span class="sxs-lookup"><span data-stu-id="127e7-925">E1D1</span></span></td>
  <td><span data-ttu-id="127e7-926">DirectionsLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-926">DirectionsLegacy</span></span></td>
 </tr>
 <tr><td>![LocationLegacy](images/segoe-mdl/e1d2.png)</td>
  <td><span data-ttu-id="127e7-928">E1D2</span><span class="sxs-lookup"><span data-stu-id="127e7-928">E1D2</span></span></td>
  <td><span data-ttu-id="127e7-929">LocationLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-929">LocationLegacy</span></span></td>
 </tr>
 <tr><td>![LibraryLegacy](images/segoe-mdl/e1d3.png)</td>
  <td><span data-ttu-id="127e7-931">E1D3</span><span class="sxs-lookup"><span data-stu-id="127e7-931">E1D3</span></span></td>
  <td><span data-ttu-id="127e7-932">LibraryLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-932">LibraryLegacy</span></span></td>
 </tr>
 <tr><td>![PhoneBookLegacy](images/segoe-mdl/e1d4.png)</td>
  <td><span data-ttu-id="127e7-934">E1D4</span><span class="sxs-lookup"><span data-stu-id="127e7-934">E1D4</span></span></td>
  <td><span data-ttu-id="127e7-935">PhoneBookLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-935">PhoneBookLegacy</span></span></td>
 </tr>
 <tr><td>![MemoLegacy](images/segoe-mdl/e1d5.png)</td>
  <td><span data-ttu-id="127e7-937">E1D5</span><span class="sxs-lookup"><span data-stu-id="127e7-937">E1D5</span></span></td>
  <td><span data-ttu-id="127e7-938">MemoLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-938">MemoLegacy</span></span></td>
 </tr>
 <tr><td>![MicrophoneLegacy](images/segoe-mdl/e1d6.png)</td>
  <td><span data-ttu-id="127e7-940">E1D6</span><span class="sxs-lookup"><span data-stu-id="127e7-940">E1D6</span></span></td>
  <td><span data-ttu-id="127e7-941">MicrophoneLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-941">MicrophoneLegacy</span></span></td>
 </tr>
 <tr><td>![PostUpdateLegacy](images/segoe-mdl/e1d7.png)</td>
  <td><span data-ttu-id="127e7-943">E1D7</span><span class="sxs-lookup"><span data-stu-id="127e7-943">E1D7</span></span></td>
  <td><span data-ttu-id="127e7-944">PostUpdateLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-944">PostUpdateLegacy</span></span></td>
 </tr>
 <tr><td>![BackToWindowLegacy](images/segoe-mdl/e1d8.png)</td>
  <td><span data-ttu-id="127e7-946">E1D8</span><span class="sxs-lookup"><span data-stu-id="127e7-946">E1D8</span></span></td>
  <td><span data-ttu-id="127e7-947">BackToWindowLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-947">BackToWindowLegacy</span></span></td>
 </tr>
 <tr><td>![FullScreenLegacy](images/segoe-mdl/e1d9.png)</td>
  <td><span data-ttu-id="127e7-949">E1D9</span><span class="sxs-lookup"><span data-stu-id="127e7-949">E1D9</span></span></td>
  <td><span data-ttu-id="127e7-950">FullScreenLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-950">FullScreenLegacy</span></span></td>
 </tr>
 <tr><td>![NewFolderLegacy](images/segoe-mdl/e1da.png)</td>
  <td><span data-ttu-id="127e7-952">E1DA</span><span class="sxs-lookup"><span data-stu-id="127e7-952">E1DA</span></span></td>
  <td><span data-ttu-id="127e7-953">NewFolderLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-953">NewFolderLegacy</span></span></td>
 </tr>
 <tr><td>![CalendarReplyLegacy](images/segoe-mdl/e1db.png)</td>
  <td><span data-ttu-id="127e7-955">E1DB</span><span class="sxs-lookup"><span data-stu-id="127e7-955">E1DB</span></span></td>
  <td><span data-ttu-id="127e7-956">CalendarReplyLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-956">CalendarReplyLegacy</span></span></td>
 </tr>
 <tr><td>![CalendarLegacyMirrored](images/segoe-mdl/e1dc.png)</td>
  <td><span data-ttu-id="127e7-958">E1DC</span><span class="sxs-lookup"><span data-stu-id="127e7-958">E1DC</span></span></td>
  <td><span data-ttu-id="127e7-959">CalendarLegacyMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-959">CalendarLegacyMirrored</span></span></td>
 </tr>
 <tr><td>![UnsyncFolderLegacy](images/segoe-mdl/e1dd.png)</td>
  <td><span data-ttu-id="127e7-961">E1DD</span><span class="sxs-lookup"><span data-stu-id="127e7-961">E1DD</span></span></td>
  <td><span data-ttu-id="127e7-962">UnsyncFolderLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-962">UnsyncFolderLegacy</span></span></td>
 </tr>
 <tr><td>![ReportHackedLegacy](images/segoe-mdl/e1de.png)</td>
  <td><span data-ttu-id="127e7-964">E1DE</span><span class="sxs-lookup"><span data-stu-id="127e7-964">E1DE</span></span></td>
  <td><span data-ttu-id="127e7-965">ReportHackedLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-965">ReportHackedLegacy</span></span></td>
 </tr>
 <tr><td>![SyncFolderLegacy](images/segoe-mdl/e1df.png)</td>
  <td><span data-ttu-id="127e7-967">E1DF</span><span class="sxs-lookup"><span data-stu-id="127e7-967">E1DF</span></span></td>
  <td><span data-ttu-id="127e7-968">SyncFolderLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-968">SyncFolderLegacy</span></span></td>
 </tr>
 <tr><td>![BlockContactLegacy](images/segoe-mdl/e1e0.png)</td>
  <td><span data-ttu-id="127e7-970">E1E0</span><span class="sxs-lookup"><span data-stu-id="127e7-970">E1E0</span></span></td>
  <td><span data-ttu-id="127e7-971">BlockContactLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-971">BlockContactLegacy</span></span></td>
 </tr>
 <tr><td>![SwitchAppsLegacy](images/segoe-mdl/e1e1.png)</td>
  <td><span data-ttu-id="127e7-973">E1E1</span><span class="sxs-lookup"><span data-stu-id="127e7-973">E1E1</span></span></td>
  <td><span data-ttu-id="127e7-974">SwitchAppsLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-974">SwitchAppsLegacy</span></span></td>
 </tr>
 <tr><td>![AddFriendLegacy](images/segoe-mdl/e1e2.png)</td>
  <td><span data-ttu-id="127e7-976">E1E2</span><span class="sxs-lookup"><span data-stu-id="127e7-976">E1E2</span></span></td>
  <td><span data-ttu-id="127e7-977">AddFriendLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-977">AddFriendLegacy</span></span></td>
 </tr>
 <tr><td>![TouchPointerLegacy](images/segoe-mdl/e1e3.png)</td>
  <td><span data-ttu-id="127e7-979">E1E3</span><span class="sxs-lookup"><span data-stu-id="127e7-979">E1E3</span></span></td>
  <td><span data-ttu-id="127e7-980">TouchPointerLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-980">TouchPointerLegacy</span></span></td>
 </tr>
 <tr><td>![GoToStartLegacy](images/segoe-mdl/e1e4.png)</td>
  <td><span data-ttu-id="127e7-982">E1E4</span><span class="sxs-lookup"><span data-stu-id="127e7-982">E1E4</span></span></td>
  <td><span data-ttu-id="127e7-983">GoToStartLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-983">GoToStartLegacy</span></span></td>
 </tr>
 <tr><td>![ZeroBarsLegacy](images/segoe-mdl/e1e5.png)</td>
  <td><span data-ttu-id="127e7-985">E1E5</span><span class="sxs-lookup"><span data-stu-id="127e7-985">E1E5</span></span></td>
  <td><span data-ttu-id="127e7-986">ZeroBarsLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-986">ZeroBarsLegacy</span></span></td>
 </tr>
 <tr><td>![OneBarLegacy](images/segoe-mdl/e1e6.png)</td>
  <td><span data-ttu-id="127e7-988">E1E6</span><span class="sxs-lookup"><span data-stu-id="127e7-988">E1E6</span></span></td>
  <td><span data-ttu-id="127e7-989">OneBarLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-989">OneBarLegacy</span></span></td>
 </tr>
 <tr><td>![TwoBarsLegacy](images/segoe-mdl/e1e7.png)</td>
  <td><span data-ttu-id="127e7-991">E1E7</span><span class="sxs-lookup"><span data-stu-id="127e7-991">E1E7</span></span></td>
  <td><span data-ttu-id="127e7-992">TwoBarsLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-992">TwoBarsLegacy</span></span></td>
 </tr>
 <tr><td>![ThreeBarsLegacy](images/segoe-mdl/e1e8.png)</td>
  <td><span data-ttu-id="127e7-994">E1E8</span><span class="sxs-lookup"><span data-stu-id="127e7-994">E1E8</span></span></td>
  <td><span data-ttu-id="127e7-995">ThreeBarsLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-995">ThreeBarsLegacy</span></span></td>
 </tr>
 <tr><td>![FourBarsLegacy](images/segoe-mdl/e1e9.png)</td>
  <td><span data-ttu-id="127e7-997">E1E9</span><span class="sxs-lookup"><span data-stu-id="127e7-997">E1E9</span></span></td>
  <td><span data-ttu-id="127e7-998">FourBarsLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-998">FourBarsLegacy</span></span></td>
 </tr>
 <tr><td>![ItalicRussianLegacy](images/segoe-mdl/e1ea.png)</td>
  <td><span data-ttu-id="127e7-1000">E1EA</span><span class="sxs-lookup"><span data-stu-id="127e7-1000">E1EA</span></span></td>
  <td><span data-ttu-id="127e7-1001">ItalicRussianLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1001">ItalicRussianLegacy</span></span></td>
 </tr>
 <tr><td>![AllAppsLegacyMirrored](images/segoe-mdl/e1ec.png)</td>
  <td><span data-ttu-id="127e7-1003">E1EC</span><span class="sxs-lookup"><span data-stu-id="127e7-1003">E1EC</span></span></td>
  <td><span data-ttu-id="127e7-1004">AllAppsLegacyMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-1004">AllAppsLegacyMirrored</span></span></td>
 </tr>
 <tr><td>![OpenWithLegacyMirrored](images/segoe-mdl/e1ed.png)</td>
  <td><span data-ttu-id="127e7-1006">E1ED</span><span class="sxs-lookup"><span data-stu-id="127e7-1006">E1ED</span></span></td>
  <td><span data-ttu-id="127e7-1007">OpenWithLegacyMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-1007">OpenWithLegacyMirrored</span></span></td>
 </tr>
 <tr><td>![BookmarksLegacyMirrored](images/segoe-mdl/e1ee.png)</td>
  <td><span data-ttu-id="127e7-1009">E1EE</span><span class="sxs-lookup"><span data-stu-id="127e7-1009">E1EE</span></span></td>
  <td><span data-ttu-id="127e7-1010">BookmarksLegacyMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-1010">BookmarksLegacyMirrored</span></span></td>
 </tr>
 <tr><td>![MultiSelectLegacyMirrored](images/segoe-mdl/e1ef.png)</td>
  <td><span data-ttu-id="127e7-1012">E1EF</span><span class="sxs-lookup"><span data-stu-id="127e7-1012">E1EF</span></span></td>
  <td><span data-ttu-id="127e7-1013">MultiSelectLegacyMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-1013">MultiSelectLegacyMirrored</span></span></td>
 </tr>
 <tr><td>![ShowResultsLegacyMirrored](images/segoe-mdl/e1f1.png)</td>
  <td><span data-ttu-id="127e7-1015">E1F1</span><span class="sxs-lookup"><span data-stu-id="127e7-1015">E1F1</span></span></td>
  <td><span data-ttu-id="127e7-1016">ShowResultsLegacyMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-1016">ShowResultsLegacyMirrored</span></span></td>
 </tr>
 <tr><td>![MailReplyAllLegacyMirrored](images/segoe-mdl/e1f2.png)</td>
  <td><span data-ttu-id="127e7-1018">E1F2</span><span class="sxs-lookup"><span data-stu-id="127e7-1018">E1F2</span></span></td>
  <td><span data-ttu-id="127e7-1019">MailReplyAllLegacyMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-1019">MailReplyAllLegacyMirrored</span></span></td>
 </tr>
 <tr><td>![HelpLegacyMirrored](images/segoe-mdl/e1f3.png)</td>
  <td><span data-ttu-id="127e7-1021">E1F3</span><span class="sxs-lookup"><span data-stu-id="127e7-1021">E1F3</span></span></td>
  <td><span data-ttu-id="127e7-1022">HelpLegacyMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-1022">HelpLegacyMirrored</span></span></td>
 </tr>
 <tr><td>![ClearSelectionLegacyMirrored](images/segoe-mdl/e1f4.png)</td>
  <td><span data-ttu-id="127e7-1024">E1F4</span><span class="sxs-lookup"><span data-stu-id="127e7-1024">E1F4</span></span></td>
  <td><span data-ttu-id="127e7-1025">ClearSelectionLegacyMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-1025">ClearSelectionLegacyMirrored</span></span></td>
 </tr>
 <tr><td>![RecordLegacy](images/segoe-mdl/e1f5.png)</td>
  <td><span data-ttu-id="127e7-1027">E1F5</span><span class="sxs-lookup"><span data-stu-id="127e7-1027">E1F5</span></span></td>
  <td><span data-ttu-id="127e7-1028">RecordLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1028">RecordLegacy</span></span></td>
 </tr>
 <tr><td>![LockLegacy](images/segoe-mdl/e1f6.png)</td>
  <td><span data-ttu-id="127e7-1030">E1F6</span><span class="sxs-lookup"><span data-stu-id="127e7-1030">E1F6</span></span></td>
  <td><span data-ttu-id="127e7-1031">LockLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1031">LockLegacy</span></span></td>
 </tr>
 <tr><td>![UnlockLegacy](images/segoe-mdl/e1f7.png)</td>
  <td><span data-ttu-id="127e7-1033">E1F7</span><span class="sxs-lookup"><span data-stu-id="127e7-1033">E1F7</span></span></td>
  <td><span data-ttu-id="127e7-1034">UnlockLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1034">UnlockLegacy</span></span></td>
 </tr>
 <tr><td>![DownLegacy](images/segoe-mdl/e1fd.png)</td>
  <td><span data-ttu-id="127e7-1036">E1FD</span><span class="sxs-lookup"><span data-stu-id="127e7-1036">E1FD</span></span></td>
  <td><span data-ttu-id="127e7-1037">DownLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1037">DownLegacy</span></span></td>
 </tr>
 <tr><td>![CommentInlineLegacy](images/segoe-mdl/e206.png)</td>
  <td><span data-ttu-id="127e7-1039">E206</span><span class="sxs-lookup"><span data-stu-id="127e7-1039">E206</span></span></td>
  <td><span data-ttu-id="127e7-1040">CommentInlineLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1040">CommentInlineLegacy</span></span></td>
 </tr>
 <tr><td>![FavoriteInlineLegacy](images/segoe-mdl/e208.png)</td>
  <td><span data-ttu-id="127e7-1042">E208</span><span class="sxs-lookup"><span data-stu-id="127e7-1042">E208</span></span></td>
  <td><span data-ttu-id="127e7-1043">FavoriteInlineLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1043">FavoriteInlineLegacy</span></span></td>
 </tr>
 <tr><td>![LikeInlineLegacy](images/segoe-mdl/e209.png)</td>
  <td><span data-ttu-id="127e7-1045">E209</span><span class="sxs-lookup"><span data-stu-id="127e7-1045">E209</span></span></td>
  <td><span data-ttu-id="127e7-1046">LikeInlineLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1046">LikeInlineLegacy</span></span></td>
 </tr>
 <tr><td>![VideoInlineLegacy](images/segoe-mdl/e20a.png)</td>
  <td><span data-ttu-id="127e7-1048">E20A</span><span class="sxs-lookup"><span data-stu-id="127e7-1048">E20A</span></span></td>
  <td><span data-ttu-id="127e7-1049">VideoInlineLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1049">VideoInlineLegacy</span></span></td>
 </tr>
 <tr><td>![MailMessageLegacy](images/segoe-mdl/e20b.png)</td>
  <td><span data-ttu-id="127e7-1051">E20B</span><span class="sxs-lookup"><span data-stu-id="127e7-1051">E20B</span></span></td>
  <td><span data-ttu-id="127e7-1052">MailMessageLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1052">MailMessageLegacy</span></span></td>
 </tr>
 <tr><td>![PC1Legacy](images/segoe-mdl/e211.png)</td>
  <td><span data-ttu-id="127e7-1054">E211</span><span class="sxs-lookup"><span data-stu-id="127e7-1054">E211</span></span></td>
  <td><span data-ttu-id="127e7-1055">PC1Legacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1055">PC1Legacy</span></span></td>
 </tr>
 <tr><td>![DevicesLegacy](images/segoe-mdl/e212.png)</td>
  <td><span data-ttu-id="127e7-1057">E212</span><span class="sxs-lookup"><span data-stu-id="127e7-1057">E212</span></span></td>
  <td><span data-ttu-id="127e7-1058">DevicesLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1058">DevicesLegacy</span></span></td>
 </tr>
 <tr><td>![RatingStarLegacy](images/segoe-mdl/e224.png)</td>
  <td><span data-ttu-id="127e7-1060">E224</span><span class="sxs-lookup"><span data-stu-id="127e7-1060">E224</span></span></td>
  <td><span data-ttu-id="127e7-1061">RatingStarLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1061">RatingStarLegacy</span></span></td>
 </tr>
 <tr><td>![ChevronDownSmLegacy](images/segoe-mdl/e228.png)</td>
  <td><span data-ttu-id="127e7-1063">E228</span><span class="sxs-lookup"><span data-stu-id="127e7-1063">E228</span></span></td>
  <td><span data-ttu-id="127e7-1064">ChevronDownSmLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1064">ChevronDownSmLegacy</span></span></td>
 </tr>
 <tr><td>![ReplyLegacy](images/segoe-mdl/e248.png)</td>
  <td><span data-ttu-id="127e7-1066">E248</span><span class="sxs-lookup"><span data-stu-id="127e7-1066">E248</span></span></td>
  <td><span data-ttu-id="127e7-1067">ReplyLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1067">ReplyLegacy</span></span></td>
 </tr>
 <tr><td>![Favorite2Legacy](images/segoe-mdl/e249.png)</td>
  <td><span data-ttu-id="127e7-1069">E249</span><span class="sxs-lookup"><span data-stu-id="127e7-1069">E249</span></span></td>
  <td><span data-ttu-id="127e7-1070">Favorite2Legacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1070">Favorite2Legacy</span></span></td>
 </tr>
 <tr><td>![Unfavorite2Legacy](images/segoe-mdl/e24a.png)</td>
  <td><span data-ttu-id="127e7-1072">E24A</span><span class="sxs-lookup"><span data-stu-id="127e7-1072">E24A</span></span></td>
  <td><span data-ttu-id="127e7-1073">Unfavorite2Legacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1073">Unfavorite2Legacy</span></span></td>
 </tr>
 <tr><td>![MobileContactLegacy](images/segoe-mdl/e25a.png)</td>
  <td><span data-ttu-id="127e7-1075">E25A</span><span class="sxs-lookup"><span data-stu-id="127e7-1075">E25A</span></span></td>
  <td><span data-ttu-id="127e7-1076">MobileContactLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1076">MobileContactLegacy</span></span></td>
 </tr>
 <tr><td>![BlockedLegacy](images/segoe-mdl/e25b.png)</td>
  <td><span data-ttu-id="127e7-1078">E25B</span><span class="sxs-lookup"><span data-stu-id="127e7-1078">E25B</span></span></td>
  <td><span data-ttu-id="127e7-1079">BlockedLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1079">BlockedLegacy</span></span></td>
 </tr>
 <tr><td>![TypingIndicatorLegacy](images/segoe-mdl/e25c.png)</td>
  <td><span data-ttu-id="127e7-1081">E25C</span><span class="sxs-lookup"><span data-stu-id="127e7-1081">E25C</span></span></td>
  <td><span data-ttu-id="127e7-1082">TypingIndicatorLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1082">TypingIndicatorLegacy</span></span></td>
 </tr>
 <tr><td>![PresenceChickletVideoLegacy](images/segoe-mdl/e25d.png)</td>
  <td><span data-ttu-id="127e7-1084">E25D</span><span class="sxs-lookup"><span data-stu-id="127e7-1084">E25D</span></span></td>
  <td><span data-ttu-id="127e7-1085">PresenceChickletVideoLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1085">PresenceChickletVideoLegacy</span></span></td>
 </tr>
 <tr><td>![PresenceChickletLegacy](images/segoe-mdl/e25e.png)</td>
  <td><span data-ttu-id="127e7-1087">E25E</span><span class="sxs-lookup"><span data-stu-id="127e7-1087">E25E</span></span></td>
  <td><span data-ttu-id="127e7-1088">PresenceChickletLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1088">PresenceChickletLegacy</span></span></td>
 </tr>
 <tr><td>![ChevronRightSmLegacy](images/segoe-mdl/e26b.png)</td>
  <td><span data-ttu-id="127e7-1090">E26B</span><span class="sxs-lookup"><span data-stu-id="127e7-1090">E26B</span></span></td>
  <td><span data-ttu-id="127e7-1091">ChevronRightSmLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1091">ChevronRightSmLegacy</span></span></td>
 </tr>
 <tr><td>![ChevronLeftSmLegacy](images/segoe-mdl/e26c.png)</td>
  <td><span data-ttu-id="127e7-1093">E26C</span><span class="sxs-lookup"><span data-stu-id="127e7-1093">E26C</span></span></td>
  <td><span data-ttu-id="127e7-1094">ChevronLeftSmLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1094">ChevronLeftSmLegacy</span></span></td>
 </tr>
 <tr><td>![SaveAsLegacy](images/segoe-mdl/e28f.png)</td>
  <td><span data-ttu-id="127e7-1096">E28F</span><span class="sxs-lookup"><span data-stu-id="127e7-1096">E28F</span></span></td>
  <td><span data-ttu-id="127e7-1097">SaveAsLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1097">SaveAsLegacy</span></span></td>
 </tr>
 <tr><td>![DecreaseIndentLegacy](images/segoe-mdl/e290.png)</td>
  <td><span data-ttu-id="127e7-1099">E290</span><span class="sxs-lookup"><span data-stu-id="127e7-1099">E290</span></span></td>
  <td><span data-ttu-id="127e7-1100">DecreaseIndentLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1100">DecreaseIndentLegacy</span></span></td>
 </tr>
 <tr><td>![IncreaseIndentLegacy](images/segoe-mdl/e291.png)</td>
  <td><span data-ttu-id="127e7-1102">E291</span><span class="sxs-lookup"><span data-stu-id="127e7-1102">E291</span></span></td>
  <td><span data-ttu-id="127e7-1103">IncreaseIndentLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1103">IncreaseIndentLegacy</span></span></td>
 </tr>
 <tr><td>![BulletedListLegacy](images/segoe-mdl/e292.png)</td>
  <td><span data-ttu-id="127e7-1105">E292</span><span class="sxs-lookup"><span data-stu-id="127e7-1105">E292</span></span></td>
  <td><span data-ttu-id="127e7-1106">BulletedListLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1106">BulletedListLegacy</span></span></td>
 </tr>
 <tr><td>![ScanLegacy](images/segoe-mdl/e294.png)</td>
  <td><span data-ttu-id="127e7-1108">E294</span><span class="sxs-lookup"><span data-stu-id="127e7-1108">E294</span></span></td>
  <td><span data-ttu-id="127e7-1109">ScanLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1109">ScanLegacy</span></span></td>
 </tr>
 <tr><td>![PreviewLegacy](images/segoe-mdl/e295.png)</td>
  <td><span data-ttu-id="127e7-1111">E295</span><span class="sxs-lookup"><span data-stu-id="127e7-1111">E295</span></span></td>
  <td><span data-ttu-id="127e7-1112">PreviewLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1112">PreviewLegacy</span></span></td>
 </tr>
 <tr><td>![DecreaseIndentLegacyMirrored](images/segoe-mdl/e297.png)</td>
  <td><span data-ttu-id="127e7-1114">E297</span><span class="sxs-lookup"><span data-stu-id="127e7-1114">E297</span></span></td>
  <td><span data-ttu-id="127e7-1115">DecreaseIndentLegacyMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-1115">DecreaseIndentLegacyMirrored</span></span></td>
 </tr>
 <tr><td>![IncreaseIndentLegacyMirrored](images/segoe-mdl/e298.png)</td>
  <td><span data-ttu-id="127e7-1117">E298</span><span class="sxs-lookup"><span data-stu-id="127e7-1117">E298</span></span></td>
  <td><span data-ttu-id="127e7-1118">IncreaseIndentLegacyMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-1118">IncreaseIndentLegacyMirrored</span></span></td>
 </tr>
 <tr><td>![BulletedListLegacyMirrored](images/segoe-mdl/e299.png)</td>
  <td><span data-ttu-id="127e7-1120">E299</span><span class="sxs-lookup"><span data-stu-id="127e7-1120">E299</span></span></td>
  <td><span data-ttu-id="127e7-1121">BulletedListLegacyMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-1121">BulletedListLegacyMirrored</span></span></td>
 </tr>
 <tr><td>![PlayOnLegacy](images/segoe-mdl/e29b.png)</td>
  <td><span data-ttu-id="127e7-1123">E29B</span><span class="sxs-lookup"><span data-stu-id="127e7-1123">E29B</span></span></td>
  <td><span data-ttu-id="127e7-1124">PlayOnLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1124">PlayOnLegacy</span></span></td>
 </tr>
 <tr><td>![ResolutionLegacy](images/segoe-mdl/e2ac.png)</td>
  <td><span data-ttu-id="127e7-1126">E2AC</span><span class="sxs-lookup"><span data-stu-id="127e7-1126">E2AC</span></span></td>
  <td><span data-ttu-id="127e7-1127">ResolutionLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1127">ResolutionLegacy</span></span></td>
 </tr>
 <tr><td>![LengthLegacy](images/segoe-mdl/e2ad.png)</td>
  <td><span data-ttu-id="127e7-1129">E2AD</span><span class="sxs-lookup"><span data-stu-id="127e7-1129">E2AD</span></span></td>
  <td><span data-ttu-id="127e7-1130">LengthLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1130">LengthLegacy</span></span></td>
 </tr>
 <tr><td>![LayoutLegacy](images/segoe-mdl/e2ae.png)</td>
  <td><span data-ttu-id="127e7-1132">E2AE</span><span class="sxs-lookup"><span data-stu-id="127e7-1132">E2AE</span></span></td>
  <td><span data-ttu-id="127e7-1133">LayoutLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1133">LayoutLegacy</span></span></td>
 </tr>
 <tr><td>![Contact3Legacy](images/segoe-mdl/e2af.png)</td>
  <td><span data-ttu-id="127e7-1135">E2AF</span><span class="sxs-lookup"><span data-stu-id="127e7-1135">E2AF</span></span></td>
  <td><span data-ttu-id="127e7-1136">Contact3Legacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1136">Contact3Legacy</span></span></td>
 </tr>
 <tr><td>![TypeLegacy](images/segoe-mdl/e2b0.png)</td>
  <td><span data-ttu-id="127e7-1138">E2B0</span><span class="sxs-lookup"><span data-stu-id="127e7-1138">E2B0</span></span></td>
  <td><span data-ttu-id="127e7-1139">TypeLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1139">TypeLegacy</span></span></td>
 </tr>
 <tr><td>![ColorLegacy](images/segoe-mdl/e2b1.png)</td>
  <td><span data-ttu-id="127e7-1141">E2B1</span><span class="sxs-lookup"><span data-stu-id="127e7-1141">E2B1</span></span></td>
  <td><span data-ttu-id="127e7-1142">ColorLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1142">ColorLegacy</span></span></td>
 </tr>
 <tr><td>![SizeLegacy](images/segoe-mdl/e2b2.png)</td>
  <td><span data-ttu-id="127e7-1144">E2B2</span><span class="sxs-lookup"><span data-stu-id="127e7-1144">E2B2</span></span></td>
  <td><span data-ttu-id="127e7-1145">SizeLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1145">SizeLegacy</span></span></td>
 </tr>
 <tr><td>![ReturnToWindowLegacy](images/segoe-mdl/e2b3.png)</td>
  <td><span data-ttu-id="127e7-1147">E2B3</span><span class="sxs-lookup"><span data-stu-id="127e7-1147">E2B3</span></span></td>
  <td><span data-ttu-id="127e7-1148">ReturnToWindowLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1148">ReturnToWindowLegacy</span></span></td>
 </tr>
 <tr><td>![OpenInNewWindowLegacy](images/segoe-mdl/e2b4.png)</td>
  <td><span data-ttu-id="127e7-1150">E2B4</span><span class="sxs-lookup"><span data-stu-id="127e7-1150">E2B4</span></span></td>
  <td><span data-ttu-id="127e7-1151">OpenInNewWindowLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1151">OpenInNewWindowLegacy</span></span></td>
 </tr>
 <tr><td>![PrintLegacy](images/segoe-mdl/e2f6.png)</td>
  <td><span data-ttu-id="127e7-1153">E2F6</span><span class="sxs-lookup"><span data-stu-id="127e7-1153">E2F6</span></span></td>
  <td><span data-ttu-id="127e7-1154">PrintLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1154">PrintLegacy</span></span></td>
 </tr>
 <tr><td>![Printer3DLegacy](images/segoe-mdl/e2f7.png)</td>
  <td><span data-ttu-id="127e7-1156">E2F7</span><span class="sxs-lookup"><span data-stu-id="127e7-1156">E2F7</span></span></td>
  <td><span data-ttu-id="127e7-1157">Printer3DLegacy</span><span class="sxs-lookup"><span data-stu-id="127e7-1157">Printer3DLegacy</span></span></td>
 </tr>
 <tr><td>![GlobalNavButton](images/segoe-mdl/e700.png)</td>
  <td><span data-ttu-id="127e7-1159">E700</span><span class="sxs-lookup"><span data-stu-id="127e7-1159">E700</span></span></td>
  <td><span data-ttu-id="127e7-1160">GlobalNavigationButton</span><span class="sxs-lookup"><span data-stu-id="127e7-1160">GlobalNavigationButton</span></span></td>
 </tr>
 <tr><td>![Wifi](images/segoe-mdl/e701.png)</td>
  <td><span data-ttu-id="127e7-1162">E701</span><span class="sxs-lookup"><span data-stu-id="127e7-1162">E701</span></span></td>
  <td><span data-ttu-id="127e7-1163">Wifi</span><span class="sxs-lookup"><span data-stu-id="127e7-1163">Wifi</span></span></td>
 </tr>
 <tr><td>![Bluetooth](images/segoe-mdl/e702.png)</td>
  <td><span data-ttu-id="127e7-1165">E702</span><span class="sxs-lookup"><span data-stu-id="127e7-1165">E702</span></span></td>
  <td><span data-ttu-id="127e7-1166">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="127e7-1166">Bluetooth</span></span></td>
 </tr>
 <tr><td>![Connect](images/segoe-mdl/e703.png)</td>
  <td><span data-ttu-id="127e7-1168">E703</span><span class="sxs-lookup"><span data-stu-id="127e7-1168">E703</span></span></td>
  <td><span data-ttu-id="127e7-1169">Connect</span><span class="sxs-lookup"><span data-stu-id="127e7-1169">Connect</span></span></td>
 </tr>
 <tr><td>![InternetSharing](images/segoe-mdl/e704.png)</td>
  <td><span data-ttu-id="127e7-1171">E704</span><span class="sxs-lookup"><span data-stu-id="127e7-1171">E704</span></span></td>
  <td><span data-ttu-id="127e7-1172">InternetSharing</span><span class="sxs-lookup"><span data-stu-id="127e7-1172">InternetSharing</span></span></td>
 </tr>
 <tr><td>![VPN](images/segoe-mdl/e705.png)</td>
  <td><span data-ttu-id="127e7-1174">E705</span><span class="sxs-lookup"><span data-stu-id="127e7-1174">E705</span></span></td>
  <td><span data-ttu-id="127e7-1175">VPN</span><span class="sxs-lookup"><span data-stu-id="127e7-1175">VPN</span></span></td>
 </tr>
 <tr><td>![Brightness](images/segoe-mdl/e706.png)</td>
  <td><span data-ttu-id="127e7-1177">E706</span><span class="sxs-lookup"><span data-stu-id="127e7-1177">E706</span></span></td>
  <td><span data-ttu-id="127e7-1178">Brightness</span><span class="sxs-lookup"><span data-stu-id="127e7-1178">Brightness</span></span></td>
 </tr>
 <tr><td>![MapPin](images/segoe-mdl/e707.png)</td>
  <td><span data-ttu-id="127e7-1180">E707</span><span class="sxs-lookup"><span data-stu-id="127e7-1180">E707</span></span></td>
  <td><span data-ttu-id="127e7-1181">MapPin</span><span class="sxs-lookup"><span data-stu-id="127e7-1181">MapPin</span></span></td>
 </tr>
 <tr><td>![QuietHours](images/segoe-mdl/e708.png)</td>
  <td><span data-ttu-id="127e7-1183">E708</span><span class="sxs-lookup"><span data-stu-id="127e7-1183">E708</span></span></td>
  <td><span data-ttu-id="127e7-1184">QuietHours</span><span class="sxs-lookup"><span data-stu-id="127e7-1184">QuietHours</span></span></td>
 </tr>
 <tr><td>![Airplane](images/segoe-mdl/e709.png)</td>
  <td><span data-ttu-id="127e7-1186">E709</span><span class="sxs-lookup"><span data-stu-id="127e7-1186">E709</span></span></td>
  <td><span data-ttu-id="127e7-1187">Airplane</span><span class="sxs-lookup"><span data-stu-id="127e7-1187">Airplane</span></span></td>
 </tr>
 <tr><td>![Tablet](images/segoe-mdl/e70a.png)</td>
  <td><span data-ttu-id="127e7-1189">E70A</span><span class="sxs-lookup"><span data-stu-id="127e7-1189">E70A</span></span></td>
  <td><span data-ttu-id="127e7-1190">Tablet</span><span class="sxs-lookup"><span data-stu-id="127e7-1190">Tablet</span></span></td>
 </tr>
 <tr><td>![QuickNote](images/segoe-mdl/e70b.png)</td>
  <td><span data-ttu-id="127e7-1192">E70B</span><span class="sxs-lookup"><span data-stu-id="127e7-1192">E70B</span></span></td>
  <td><span data-ttu-id="127e7-1193">QuickNote</span><span class="sxs-lookup"><span data-stu-id="127e7-1193">QuickNote</span></span></td>
 </tr>
 <tr><td>![RememberedDevice](images/segoe-mdl/e70c.png)</td>
  <td><span data-ttu-id="127e7-1195">E70C</span><span class="sxs-lookup"><span data-stu-id="127e7-1195">E70C</span></span></td>
  <td><span data-ttu-id="127e7-1196">RememberedDevice</span><span class="sxs-lookup"><span data-stu-id="127e7-1196">RememberedDevice</span></span></td>
 </tr>
 <tr><td>![ChevronDown](images/segoe-mdl/e70d.png)</td>
  <td><span data-ttu-id="127e7-1198">E70D</span><span class="sxs-lookup"><span data-stu-id="127e7-1198">E70D</span></span></td>
  <td><span data-ttu-id="127e7-1199">ChevronDown</span><span class="sxs-lookup"><span data-stu-id="127e7-1199">ChevronDown</span></span></td>
 </tr>
 <tr><td>![ChevronUp](images/segoe-mdl/e70e.png)</td>
  <td><span data-ttu-id="127e7-1201">E70E</span><span class="sxs-lookup"><span data-stu-id="127e7-1201">E70E</span></span></td>
  <td><span data-ttu-id="127e7-1202">ChevronUp</span><span class="sxs-lookup"><span data-stu-id="127e7-1202">ChevronUp</span></span></td>
 </tr>
 <tr><td>![Edit](images/segoe-mdl/e70f.png)</td>
  <td><span data-ttu-id="127e7-1204">E70F</span><span class="sxs-lookup"><span data-stu-id="127e7-1204">E70F</span></span></td>
  <td><span data-ttu-id="127e7-1205">Edit</span><span class="sxs-lookup"><span data-stu-id="127e7-1205">Edit</span></span></td>
 </tr>
 <tr><td>![Add](images/segoe-mdl/e710.png)</td>
  <td><span data-ttu-id="127e7-1207">E710</span><span class="sxs-lookup"><span data-stu-id="127e7-1207">E710</span></span></td>
  <td><span data-ttu-id="127e7-1208">Add</span><span class="sxs-lookup"><span data-stu-id="127e7-1208">Add</span></span></td>
 </tr>
 <tr><td>![Cancel](images/segoe-mdl/e711.png)</td>
  <td><span data-ttu-id="127e7-1210">E711</span><span class="sxs-lookup"><span data-stu-id="127e7-1210">E711</span></span></td>
  <td><span data-ttu-id="127e7-1211">Cancel</span><span class="sxs-lookup"><span data-stu-id="127e7-1211">Cancel</span></span></td>
 </tr>
 <tr><td>![More](images/segoe-mdl/e712.png)</td>
  <td><span data-ttu-id="127e7-1213">E712</span><span class="sxs-lookup"><span data-stu-id="127e7-1213">E712</span></span></td>
  <td><span data-ttu-id="127e7-1214">More</span><span class="sxs-lookup"><span data-stu-id="127e7-1214">More</span></span></td>
 </tr>
 <tr><td>![Settings](images/segoe-mdl/e713.png)</td>
  <td><span data-ttu-id="127e7-1216">E713</span><span class="sxs-lookup"><span data-stu-id="127e7-1216">E713</span></span></td>
  <td><span data-ttu-id="127e7-1217">Settings</span><span class="sxs-lookup"><span data-stu-id="127e7-1217">Settings</span></span></td>
 </tr>
 <tr><td>![Video](images/segoe-mdl/e714.png)</td>
  <td><span data-ttu-id="127e7-1219">E714</span><span class="sxs-lookup"><span data-stu-id="127e7-1219">E714</span></span></td>
  <td><span data-ttu-id="127e7-1220">Video</span><span class="sxs-lookup"><span data-stu-id="127e7-1220">Video</span></span></td>
 </tr>
 <tr><td>![Mail](images/segoe-mdl/e715.png)</td>
  <td><span data-ttu-id="127e7-1222">E715</span><span class="sxs-lookup"><span data-stu-id="127e7-1222">E715</span></span></td>
  <td><span data-ttu-id="127e7-1223">Mail</span><span class="sxs-lookup"><span data-stu-id="127e7-1223">Mail</span></span></td>
 </tr>
 <tr><td>![People](images/segoe-mdl/e716.png)</td>
  <td><span data-ttu-id="127e7-1225">E716</span><span class="sxs-lookup"><span data-stu-id="127e7-1225">E716</span></span></td>
  <td><span data-ttu-id="127e7-1226">People</span><span class="sxs-lookup"><span data-stu-id="127e7-1226">People</span></span></td>
 </tr>
 <tr><td>![Phone](images/segoe-mdl/e717.png)</td>
  <td><span data-ttu-id="127e7-1228">E717</span><span class="sxs-lookup"><span data-stu-id="127e7-1228">E717</span></span></td>
  <td><span data-ttu-id="127e7-1229">Phone</span><span class="sxs-lookup"><span data-stu-id="127e7-1229">Phone</span></span></td>
 </tr>
 <tr><td>![Pin](images/segoe-mdl/e718.png)</td>
  <td><span data-ttu-id="127e7-1231">E718</span><span class="sxs-lookup"><span data-stu-id="127e7-1231">E718</span></span></td>
  <td><span data-ttu-id="127e7-1232">Pin</span><span class="sxs-lookup"><span data-stu-id="127e7-1232">Pin</span></span></td>
 </tr>
 <tr><td>![Shop](images/segoe-mdl/e719.png)</td>
  <td><span data-ttu-id="127e7-1234">E719</span><span class="sxs-lookup"><span data-stu-id="127e7-1234">E719</span></span></td>
  <td><span data-ttu-id="127e7-1235">Shop</span><span class="sxs-lookup"><span data-stu-id="127e7-1235">Shop</span></span></td>
 </tr>
 <tr><td>![Stop](images/segoe-mdl/e71a.png)</td>
  <td><span data-ttu-id="127e7-1237">E71A</span><span class="sxs-lookup"><span data-stu-id="127e7-1237">E71A</span></span></td>
  <td><span data-ttu-id="127e7-1238">Stop</span><span class="sxs-lookup"><span data-stu-id="127e7-1238">Stop</span></span></td>
 </tr>
 <tr><td>![Link](images/segoe-mdl/e71b.png)</td>
  <td><span data-ttu-id="127e7-1240">E71B</span><span class="sxs-lookup"><span data-stu-id="127e7-1240">E71B</span></span></td>
  <td><span data-ttu-id="127e7-1241">Link</span><span class="sxs-lookup"><span data-stu-id="127e7-1241">Link</span></span></td>
 </tr>
 <tr><td>![Filter](images/segoe-mdl/e71c.png)</td>
  <td><span data-ttu-id="127e7-1243">E71C</span><span class="sxs-lookup"><span data-stu-id="127e7-1243">E71C</span></span></td>
  <td><span data-ttu-id="127e7-1244">Filter</span><span class="sxs-lookup"><span data-stu-id="127e7-1244">Filter</span></span></td>
 </tr>
 <tr><td>![AllApps](images/segoe-mdl/e71d.png)</td>
  <td><span data-ttu-id="127e7-1246">E71D</span><span class="sxs-lookup"><span data-stu-id="127e7-1246">E71D</span></span></td>
  <td><span data-ttu-id="127e7-1247">AllApps</span><span class="sxs-lookup"><span data-stu-id="127e7-1247">AllApps</span></span></td>
 </tr>
 <tr><td>![Zoom](images/segoe-mdl/e71e.png)</td>
  <td><span data-ttu-id="127e7-1249">E71E</span><span class="sxs-lookup"><span data-stu-id="127e7-1249">E71E</span></span></td>
  <td><span data-ttu-id="127e7-1250">Zoom</span><span class="sxs-lookup"><span data-stu-id="127e7-1250">Zoom</span></span></td>
 </tr>
 <tr><td>![ZoomOut](images/segoe-mdl/e71f.png)</td>
  <td><span data-ttu-id="127e7-1252">E71F</span><span class="sxs-lookup"><span data-stu-id="127e7-1252">E71F</span></span></td>
  <td><span data-ttu-id="127e7-1253">ZoomOut</span><span class="sxs-lookup"><span data-stu-id="127e7-1253">ZoomOut</span></span></td>
 </tr>
 <tr><td>![Microphone](images/segoe-mdl/e720.png)</td>
  <td><span data-ttu-id="127e7-1255">E720</span><span class="sxs-lookup"><span data-stu-id="127e7-1255">E720</span></span></td>
  <td><span data-ttu-id="127e7-1256">Microphone</span><span class="sxs-lookup"><span data-stu-id="127e7-1256">Microphone</span></span></td>
 </tr>
 <tr><td>![Search](images/segoe-mdl/e721.png)</td>
  <td><span data-ttu-id="127e7-1258">E721</span><span class="sxs-lookup"><span data-stu-id="127e7-1258">E721</span></span></td>
  <td><span data-ttu-id="127e7-1259">Search</span><span class="sxs-lookup"><span data-stu-id="127e7-1259">Search</span></span></td>
 </tr>
 <tr><td>![Camera](images/segoe-mdl/e722.png)</td>
  <td><span data-ttu-id="127e7-1261">E722</span><span class="sxs-lookup"><span data-stu-id="127e7-1261">E722</span></span></td>
  <td><span data-ttu-id="127e7-1262">Camera</span><span class="sxs-lookup"><span data-stu-id="127e7-1262">Camera</span></span></td>
 </tr>
 <tr><td>![Attach](images/segoe-mdl/e723.png)</td>
  <td><span data-ttu-id="127e7-1264">E723</span><span class="sxs-lookup"><span data-stu-id="127e7-1264">E723</span></span></td>
  <td><span data-ttu-id="127e7-1265">Attach</span><span class="sxs-lookup"><span data-stu-id="127e7-1265">Attach</span></span></td>
 </tr>
 <tr><td>![Send](images/segoe-mdl/e724.png)</td>
  <td><span data-ttu-id="127e7-1267">E724</span><span class="sxs-lookup"><span data-stu-id="127e7-1267">E724</span></span></td>
  <td><span data-ttu-id="127e7-1268">Send</span><span class="sxs-lookup"><span data-stu-id="127e7-1268">Send</span></span></td>
 </tr>
 <tr><td>![SendFill](images/segoe-mdl/e725.png)</td>
  <td><span data-ttu-id="127e7-1270">E725</span><span class="sxs-lookup"><span data-stu-id="127e7-1270">E725</span></span></td>
  <td><span data-ttu-id="127e7-1271">SendFill</span><span class="sxs-lookup"><span data-stu-id="127e7-1271">SendFill</span></span></td>
 </tr>
 <tr><td>![WalkSolid](images/segoe-mdl/e726.png)</td>
  <td><span data-ttu-id="127e7-1273">E726</span><span class="sxs-lookup"><span data-stu-id="127e7-1273">E726</span></span></td>
  <td><span data-ttu-id="127e7-1274">WalkSolid</span><span class="sxs-lookup"><span data-stu-id="127e7-1274">WalkSolid</span></span></td>
 </tr>
 <tr><td>![InPrivate](images/segoe-mdl/e727.png)</td>
  <td><span data-ttu-id="127e7-1276">E727</span><span class="sxs-lookup"><span data-stu-id="127e7-1276">E727</span></span></td>
  <td><span data-ttu-id="127e7-1277">InPrivate</span><span class="sxs-lookup"><span data-stu-id="127e7-1277">InPrivate</span></span></td>
 </tr>
 <tr><td>![FavoriteList](images/segoe-mdl/e728.png)</td>
  <td><span data-ttu-id="127e7-1279">E728</span><span class="sxs-lookup"><span data-stu-id="127e7-1279">E728</span></span></td>
  <td><span data-ttu-id="127e7-1280">FavoriteList</span><span class="sxs-lookup"><span data-stu-id="127e7-1280">FavoriteList</span></span></td>
 </tr>
 <tr><td>![PageSolid](images/segoe-mdl/e729.png)</td>
  <td><span data-ttu-id="127e7-1282">E729</span><span class="sxs-lookup"><span data-stu-id="127e7-1282">E729</span></span></td>
  <td><span data-ttu-id="127e7-1283">PageSolid</span><span class="sxs-lookup"><span data-stu-id="127e7-1283">PageSolid</span></span></td>
 </tr>
 <tr><td>![Forward](images/segoe-mdl/e72a.png)</td>
  <td><span data-ttu-id="127e7-1285">E72A</span><span class="sxs-lookup"><span data-stu-id="127e7-1285">E72A</span></span></td>
  <td><span data-ttu-id="127e7-1286">Forward</span><span class="sxs-lookup"><span data-stu-id="127e7-1286">Forward</span></span></td>
 </tr>
 <tr><td>![Back](images/segoe-mdl/e72b.png)</td>
  <td><span data-ttu-id="127e7-1288">E72B</span><span class="sxs-lookup"><span data-stu-id="127e7-1288">E72B</span></span></td>
  <td><span data-ttu-id="127e7-1289">Back</span><span class="sxs-lookup"><span data-stu-id="127e7-1289">Back</span></span></td>
 </tr>
 <tr><td>![Refresh](images/segoe-mdl/e72c.png)</td>
  <td><span data-ttu-id="127e7-1291">E72C</span><span class="sxs-lookup"><span data-stu-id="127e7-1291">E72C</span></span></td>
  <td><span data-ttu-id="127e7-1292">Refresh</span><span class="sxs-lookup"><span data-stu-id="127e7-1292">Refresh</span></span></td>
 </tr>
 <tr><td>![Share](images/segoe-mdl/e72d.png)</td>
  <td><span data-ttu-id="127e7-1294">E72D</span><span class="sxs-lookup"><span data-stu-id="127e7-1294">E72D</span></span></td>
  <td><span data-ttu-id="127e7-1295">Share</span><span class="sxs-lookup"><span data-stu-id="127e7-1295">Share</span></span></td>
 </tr>
 <tr><td>![Lock](images/segoe-mdl/e72e.png)</td>
  <td><span data-ttu-id="127e7-1297">E72E</span><span class="sxs-lookup"><span data-stu-id="127e7-1297">E72E</span></span></td>
  <td><span data-ttu-id="127e7-1298">Lock</span><span class="sxs-lookup"><span data-stu-id="127e7-1298">Lock</span></span></td>
 </tr>
 <tr><td>![ReportHacked](images/segoe-mdl/e730.png)</td>
  <td><span data-ttu-id="127e7-1300">E730</span><span class="sxs-lookup"><span data-stu-id="127e7-1300">E730</span></span></td>
  <td><span data-ttu-id="127e7-1301">ReportHacked</span><span class="sxs-lookup"><span data-stu-id="127e7-1301">ReportHacked</span></span></td>
 </tr>
 <tr><td>![FavoriteStar](images/segoe-mdl/e734.png)</td>
  <td><span data-ttu-id="127e7-1303">E734</span><span class="sxs-lookup"><span data-stu-id="127e7-1303">E734</span></span></td>
  <td><span data-ttu-id="127e7-1304">FavoriteStar</span><span class="sxs-lookup"><span data-stu-id="127e7-1304">FavoriteStar</span></span></td>
 </tr>
 <tr><td>![FavoriteStarFill](images/segoe-mdl/e735.png)</td>
  <td><span data-ttu-id="127e7-1306">E735</span><span class="sxs-lookup"><span data-stu-id="127e7-1306">E735</span></span></td>
  <td><span data-ttu-id="127e7-1307">FavoriteStarFill</span><span class="sxs-lookup"><span data-stu-id="127e7-1307">FavoriteStarFill</span></span></td>
 </tr>
 <tr><td>![Remove](images/segoe-mdl/e738.png)</td>
  <td><span data-ttu-id="127e7-1309">E738</span><span class="sxs-lookup"><span data-stu-id="127e7-1309">E738</span></span></td>
  <td><span data-ttu-id="127e7-1310">Remove</span><span class="sxs-lookup"><span data-stu-id="127e7-1310">Remove</span></span></td>
 </tr>
 <tr><td>![Checkbox](images/segoe-mdl/e739.png)</td>
  <td><span data-ttu-id="127e7-1312">E739</span><span class="sxs-lookup"><span data-stu-id="127e7-1312">E739</span></span></td>
  <td><span data-ttu-id="127e7-1313">Checkbox</span><span class="sxs-lookup"><span data-stu-id="127e7-1313">Checkbox</span></span></td>
 </tr>
 <tr><td>![CheckboxComposite](images/segoe-mdl/e73a.png)</td>
  <td><span data-ttu-id="127e7-1315">E73A</span><span class="sxs-lookup"><span data-stu-id="127e7-1315">E73A</span></span></td>
  <td><span data-ttu-id="127e7-1316">CheckboxComposite</span><span class="sxs-lookup"><span data-stu-id="127e7-1316">CheckboxComposite</span></span></td>
 </tr>
 <tr><td>![CheckboxFill](images/segoe-mdl/e73b.png)</td>
  <td><span data-ttu-id="127e7-1318">E73B</span><span class="sxs-lookup"><span data-stu-id="127e7-1318">E73B</span></span></td>
  <td><span data-ttu-id="127e7-1319">CheckboxFill</span><span class="sxs-lookup"><span data-stu-id="127e7-1319">CheckboxFill</span></span></td>
 </tr>
 <tr><td>![CheckboxIndeterminate](images/segoe-mdl/e73c.png)</td>
  <td><span data-ttu-id="127e7-1321">E73C</span><span class="sxs-lookup"><span data-stu-id="127e7-1321">E73C</span></span></td>
  <td><span data-ttu-id="127e7-1322">CheckboxIndeterminate</span><span class="sxs-lookup"><span data-stu-id="127e7-1322">CheckboxIndeterminate</span></span></td>
 </tr>
 <tr><td>![CheckboxCompositeReversed](images/segoe-mdl/e73d.png)</td>
  <td><span data-ttu-id="127e7-1324">E73D</span><span class="sxs-lookup"><span data-stu-id="127e7-1324">E73D</span></span></td>
  <td><span data-ttu-id="127e7-1325">CheckboxCompositeReversed</span><span class="sxs-lookup"><span data-stu-id="127e7-1325">CheckboxCompositeReversed</span></span></td>
 </tr>
 <tr><td>![CheckMark](images/segoe-mdl/e73e.png)</td>
  <td><span data-ttu-id="127e7-1327">E73E</span><span class="sxs-lookup"><span data-stu-id="127e7-1327">E73E</span></span></td>
  <td><span data-ttu-id="127e7-1328">CheckMark</span><span class="sxs-lookup"><span data-stu-id="127e7-1328">CheckMark</span></span></td>
 </tr>
 <tr><td>![BackToWindow](images/segoe-mdl/e73f.png)</td>
  <td><span data-ttu-id="127e7-1330">E73F</span><span class="sxs-lookup"><span data-stu-id="127e7-1330">E73F</span></span></td>
  <td><span data-ttu-id="127e7-1331">BackToWindow</span><span class="sxs-lookup"><span data-stu-id="127e7-1331">BackToWindow</span></span></td>
 </tr>
 <tr><td>![FullScreen](images/segoe-mdl/e740.png)</td>
  <td><span data-ttu-id="127e7-1333">E740</span><span class="sxs-lookup"><span data-stu-id="127e7-1333">E740</span></span></td>
  <td><span data-ttu-id="127e7-1334">FullScreen</span><span class="sxs-lookup"><span data-stu-id="127e7-1334">FullScreen</span></span></td>
 </tr>
 <tr><td>![ResizeTouchLarger](images/segoe-mdl/e741.png)</td>
  <td><span data-ttu-id="127e7-1336">E741</span><span class="sxs-lookup"><span data-stu-id="127e7-1336">E741</span></span></td>
  <td><span data-ttu-id="127e7-1337">ResizeTouchLarger</span><span class="sxs-lookup"><span data-stu-id="127e7-1337">ResizeTouchLarger</span></span></td>
 </tr>
 <tr><td>![ResizeTouchSmaller](images/segoe-mdl/e742.png)</td>
  <td><span data-ttu-id="127e7-1339">E742</span><span class="sxs-lookup"><span data-stu-id="127e7-1339">E742</span></span></td>
  <td><span data-ttu-id="127e7-1340">ResizeTouchSmaller</span><span class="sxs-lookup"><span data-stu-id="127e7-1340">ResizeTouchSmaller</span></span></td>
 </tr>
 <tr><td>![ResizeMouseSmall](images/segoe-mdl/e743.png)</td>
  <td><span data-ttu-id="127e7-1342">E743</span><span class="sxs-lookup"><span data-stu-id="127e7-1342">E743</span></span></td>
  <td><span data-ttu-id="127e7-1343">ResizeMouseSmall</span><span class="sxs-lookup"><span data-stu-id="127e7-1343">ResizeMouseSmall</span></span></td>
 </tr>
 <tr><td>![ResizeMouseMedium](images/segoe-mdl/e744.png)</td>
  <td><span data-ttu-id="127e7-1345">E744</span><span class="sxs-lookup"><span data-stu-id="127e7-1345">E744</span></span></td>
  <td><span data-ttu-id="127e7-1346">ResizeMouseMedium</span><span class="sxs-lookup"><span data-stu-id="127e7-1346">ResizeMouseMedium</span></span></td>
 </tr>
 <tr><td>![ResizeMouseWide](images/segoe-mdl/e745.png)</td>
  <td><span data-ttu-id="127e7-1348">E745</span><span class="sxs-lookup"><span data-stu-id="127e7-1348">E745</span></span></td>
  <td><span data-ttu-id="127e7-1349">ResizeMouseWide</span><span class="sxs-lookup"><span data-stu-id="127e7-1349">ResizeMouseWide</span></span></td>
 </tr>
 <tr><td>![ResizeMouseTall](images/segoe-mdl/e746.png)</td>
  <td><span data-ttu-id="127e7-1351">E746</span><span class="sxs-lookup"><span data-stu-id="127e7-1351">E746</span></span></td>
  <td><span data-ttu-id="127e7-1352">ResizeMouseTall</span><span class="sxs-lookup"><span data-stu-id="127e7-1352">ResizeMouseTall</span></span></td>
 </tr>
 <tr><td>![ResizeMouseLarge](images/segoe-mdl/e747.png)</td>
  <td><span data-ttu-id="127e7-1354">E747</span><span class="sxs-lookup"><span data-stu-id="127e7-1354">E747</span></span></td>
  <td><span data-ttu-id="127e7-1355">ResizeMouseLarge</span><span class="sxs-lookup"><span data-stu-id="127e7-1355">ResizeMouseLarge</span></span></td>
 </tr>
 <tr><td>![SwitchUser](images/segoe-mdl/e748.png)</td>
  <td><span data-ttu-id="127e7-1357">E748</span><span class="sxs-lookup"><span data-stu-id="127e7-1357">E748</span></span></td>
  <td><span data-ttu-id="127e7-1358">SwitchUser</span><span class="sxs-lookup"><span data-stu-id="127e7-1358">SwitchUser</span></span></td>
 </tr>
 <tr><td>![Print](images/segoe-mdl/e749.png)</td>
  <td><span data-ttu-id="127e7-1360">E749</span><span class="sxs-lookup"><span data-stu-id="127e7-1360">E749</span></span></td>
  <td><span data-ttu-id="127e7-1361">Print</span><span class="sxs-lookup"><span data-stu-id="127e7-1361">Print</span></span></td>
 </tr>
 <tr><td>![Up](images/segoe-mdl/e74a.png)</td>
  <td><span data-ttu-id="127e7-1363">E74A</span><span class="sxs-lookup"><span data-stu-id="127e7-1363">E74A</span></span></td>
  <td><span data-ttu-id="127e7-1364">Up</span><span class="sxs-lookup"><span data-stu-id="127e7-1364">Up</span></span></td>
 </tr>
 <tr><td>![Down](images/segoe-mdl/e74b.png)</td>
  <td><span data-ttu-id="127e7-1366">E74B</span><span class="sxs-lookup"><span data-stu-id="127e7-1366">E74B</span></span></td>
  <td><span data-ttu-id="127e7-1367">Down</span><span class="sxs-lookup"><span data-stu-id="127e7-1367">Down</span></span></td>
 </tr>
 <tr><td>![OEM](images/segoe-mdl/e74c.png)</td>
  <td><span data-ttu-id="127e7-1369">E74C</span><span class="sxs-lookup"><span data-stu-id="127e7-1369">E74C</span></span></td>
  <td><span data-ttu-id="127e7-1370">OEM</span><span class="sxs-lookup"><span data-stu-id="127e7-1370">OEM</span></span></td>
 </tr>
 <tr><td>![Delete](images/segoe-mdl/e74d.png)</td>
  <td><span data-ttu-id="127e7-1372">E74D</span><span class="sxs-lookup"><span data-stu-id="127e7-1372">E74D</span></span></td>
  <td><span data-ttu-id="127e7-1373">Delete</span><span class="sxs-lookup"><span data-stu-id="127e7-1373">Delete</span></span></td>
 </tr>
 <tr><td>![Save](images/segoe-mdl/e74e.png)</td>
  <td><span data-ttu-id="127e7-1375">E74E</span><span class="sxs-lookup"><span data-stu-id="127e7-1375">E74E</span></span></td>
  <td><span data-ttu-id="127e7-1376">Save</span><span class="sxs-lookup"><span data-stu-id="127e7-1376">Save</span></span></td>
 </tr>
 <tr><td>![Mute](images/segoe-mdl/e74f.png)</td>
  <td><span data-ttu-id="127e7-1378">E74F</span><span class="sxs-lookup"><span data-stu-id="127e7-1378">E74F</span></span></td>
  <td><span data-ttu-id="127e7-1379">Mute</span><span class="sxs-lookup"><span data-stu-id="127e7-1379">Mute</span></span></td>
 </tr>
 <tr><td>![BackSpaceQWERTY](images/segoe-mdl/e750.png)</td>
  <td><span data-ttu-id="127e7-1381">E750</span><span class="sxs-lookup"><span data-stu-id="127e7-1381">E750</span></span></td>
  <td><span data-ttu-id="127e7-1382">BackSpaceQWERTY</span><span class="sxs-lookup"><span data-stu-id="127e7-1382">BackSpaceQWERTY</span></span></td>
 </tr>
 <tr><td>![ReturnKey](images/segoe-mdl/e751.png)</td>
  <td><span data-ttu-id="127e7-1384">E751</span><span class="sxs-lookup"><span data-stu-id="127e7-1384">E751</span></span></td>
  <td><span data-ttu-id="127e7-1385">ReturnKey</span><span class="sxs-lookup"><span data-stu-id="127e7-1385">ReturnKey</span></span></td>
 </tr>
 <tr><td>![UpArrowShiftKey](images/segoe-mdl/e752.png)</td>
  <td><span data-ttu-id="127e7-1387">E752</span><span class="sxs-lookup"><span data-stu-id="127e7-1387">E752</span></span></td>
  <td><span data-ttu-id="127e7-1388">UpArrowShiftKey</span><span class="sxs-lookup"><span data-stu-id="127e7-1388">UpArrowShiftKey</span></span></td>
 </tr>
 <tr><td>![Cloud](images/segoe-mdl/e753.png)</td>
  <td><span data-ttu-id="127e7-1390">E753</span><span class="sxs-lookup"><span data-stu-id="127e7-1390">E753</span></span></td>
  <td><span data-ttu-id="127e7-1391">Cloud</span><span class="sxs-lookup"><span data-stu-id="127e7-1391">Cloud</span></span></td>
 </tr>
 <tr><td>![Flashlight](images/segoe-mdl/e754.png)</td>
  <td><span data-ttu-id="127e7-1393">E754</span><span class="sxs-lookup"><span data-stu-id="127e7-1393">E754</span></span></td>
  <td><span data-ttu-id="127e7-1394">Flashlight</span><span class="sxs-lookup"><span data-stu-id="127e7-1394">Flashlight</span></span></td>
 </tr>
 <tr><td>![RotationLock](images/segoe-mdl/e755.png)</td>
  <td><span data-ttu-id="127e7-1396">E755</span><span class="sxs-lookup"><span data-stu-id="127e7-1396">E755</span></span></td>
  <td><span data-ttu-id="127e7-1397">RotationLock</span><span class="sxs-lookup"><span data-stu-id="127e7-1397">RotationLock</span></span></td>
 </tr>
 <tr><td>![CommandPrompt](images/segoe-mdl/e756.png)</td>
  <td><span data-ttu-id="127e7-1399">E756</span><span class="sxs-lookup"><span data-stu-id="127e7-1399">E756</span></span></td>
  <td><span data-ttu-id="127e7-1400">CommandPrompt</span><span class="sxs-lookup"><span data-stu-id="127e7-1400">CommandPrompt</span></span></td>
 </tr>
 <tr><td>![SIPMove](images/segoe-mdl/e759.png)</td>
  <td><span data-ttu-id="127e7-1402">E759</span><span class="sxs-lookup"><span data-stu-id="127e7-1402">E759</span></span></td>
  <td><span data-ttu-id="127e7-1403">SIPMove</span><span class="sxs-lookup"><span data-stu-id="127e7-1403">SIPMove</span></span></td>
 </tr>
 <tr><td>![SIPUndock](images/segoe-mdl/e75a.png)</td>
  <td><span data-ttu-id="127e7-1405">E75A</span><span class="sxs-lookup"><span data-stu-id="127e7-1405">E75A</span></span></td>
  <td><span data-ttu-id="127e7-1406">SIPUndock</span><span class="sxs-lookup"><span data-stu-id="127e7-1406">SIPUndock</span></span></td>
 </tr>
 <tr><td>![SIPRedock](images/segoe-mdl/e75b.png)</td>
  <td><span data-ttu-id="127e7-1408">E75B</span><span class="sxs-lookup"><span data-stu-id="127e7-1408">E75B</span></span></td>
  <td><span data-ttu-id="127e7-1409">SIPRedock</span><span class="sxs-lookup"><span data-stu-id="127e7-1409">SIPRedock</span></span></td>
 </tr>
 <tr><td>![EraseTool](images/segoe-mdl/e75c.png)</td>
  <td><span data-ttu-id="127e7-1411">E75C</span><span class="sxs-lookup"><span data-stu-id="127e7-1411">E75C</span></span></td>
  <td><span data-ttu-id="127e7-1412">EraseTool</span><span class="sxs-lookup"><span data-stu-id="127e7-1412">EraseTool</span></span></td>
 </tr>
 <tr><td>![UnderscoreSpace](images/segoe-mdl/e75d.png)</td>
  <td><span data-ttu-id="127e7-1414">E75D</span><span class="sxs-lookup"><span data-stu-id="127e7-1414">E75D</span></span></td>
  <td><span data-ttu-id="127e7-1415">UnderscoreSpace</span><span class="sxs-lookup"><span data-stu-id="127e7-1415">UnderscoreSpace</span></span></td>
 </tr>
 <tr><td>![GripperTool](images/segoe-mdl/e75e.png)</td>
  <td><span data-ttu-id="127e7-1417">E75E</span><span class="sxs-lookup"><span data-stu-id="127e7-1417">E75E</span></span></td>
  <td><span data-ttu-id="127e7-1418">GripperTool</span><span class="sxs-lookup"><span data-stu-id="127e7-1418">GripperTool</span></span></td>
 </tr>
 <tr><td>![Dialpad](images/segoe-mdl/e75f.png)</td>
  <td><span data-ttu-id="127e7-1420">E75F</span><span class="sxs-lookup"><span data-stu-id="127e7-1420">E75F</span></span></td>
  <td><span data-ttu-id="127e7-1421">Dialpad</span><span class="sxs-lookup"><span data-stu-id="127e7-1421">Dialpad</span></span></td>
 </tr>
 <tr><td>![PageLeft](images/segoe-mdl/e760.png)</td>
  <td><span data-ttu-id="127e7-1423">E760</span><span class="sxs-lookup"><span data-stu-id="127e7-1423">E760</span></span></td>
  <td><span data-ttu-id="127e7-1424">PageLeft</span><span class="sxs-lookup"><span data-stu-id="127e7-1424">PageLeft</span></span></td>
 </tr>
 <tr><td>![PageRight](images/segoe-mdl/e761.png)</td>
  <td><span data-ttu-id="127e7-1426">E761</span><span class="sxs-lookup"><span data-stu-id="127e7-1426">E761</span></span></td>
  <td><span data-ttu-id="127e7-1427">PageRight</span><span class="sxs-lookup"><span data-stu-id="127e7-1427">PageRight</span></span></td>
 </tr>
 <tr><td>![MultiSelect](images/segoe-mdl/e762.png)</td>
  <td><span data-ttu-id="127e7-1429">E762</span><span class="sxs-lookup"><span data-stu-id="127e7-1429">E762</span></span></td>
  <td><span data-ttu-id="127e7-1430">MultiSelect</span><span class="sxs-lookup"><span data-stu-id="127e7-1430">MultiSelect</span></span></td>
 </tr>
 <tr><td>![KeyboardLeftHanded](images/segoe-mdl/e763.png)</td>
  <td><span data-ttu-id="127e7-1432">E763</span><span class="sxs-lookup"><span data-stu-id="127e7-1432">E763</span></span></td>
  <td><span data-ttu-id="127e7-1433">KeyboardLeftHanded</span><span class="sxs-lookup"><span data-stu-id="127e7-1433">KeyboardLeftHanded</span></span></td>
 </tr>
 <tr><td>![KeyboardRightHanded](images/segoe-mdl/e764.png)</td>
  <td><span data-ttu-id="127e7-1435">E764</span><span class="sxs-lookup"><span data-stu-id="127e7-1435">E764</span></span></td>
  <td><span data-ttu-id="127e7-1436">KeyboardRightHanded</span><span class="sxs-lookup"><span data-stu-id="127e7-1436">KeyboardRightHanded</span></span></td>
 </tr>
 <tr><td>![KeyboardClassic](images/segoe-mdl/e765.png)</td>
  <td><span data-ttu-id="127e7-1438">E765</span><span class="sxs-lookup"><span data-stu-id="127e7-1438">E765</span></span></td>
  <td><span data-ttu-id="127e7-1439">KeyboardClassic</span><span class="sxs-lookup"><span data-stu-id="127e7-1439">KeyboardClassic</span></span></td>
 </tr>
 <tr><td>![KeyboardSplit](images/segoe-mdl/e766.png)</td>
  <td><span data-ttu-id="127e7-1441">E766</span><span class="sxs-lookup"><span data-stu-id="127e7-1441">E766</span></span></td>
  <td><span data-ttu-id="127e7-1442">KeyboardSplit</span><span class="sxs-lookup"><span data-stu-id="127e7-1442">KeyboardSplit</span></span></td>
 </tr>
 <tr><td>![Volume](images/segoe-mdl/e767.png)</td>
  <td><span data-ttu-id="127e7-1444">E767</span><span class="sxs-lookup"><span data-stu-id="127e7-1444">E767</span></span></td>
  <td><span data-ttu-id="127e7-1445">Volume</span><span class="sxs-lookup"><span data-stu-id="127e7-1445">Volume</span></span></td>
 </tr>
 <tr><td>![Play](images/segoe-mdl/e768.png)</td>
  <td><span data-ttu-id="127e7-1447">E768</span><span class="sxs-lookup"><span data-stu-id="127e7-1447">E768</span></span></td>
  <td><span data-ttu-id="127e7-1448">Play</span><span class="sxs-lookup"><span data-stu-id="127e7-1448">Play</span></span></td>
 </tr>
 <tr><td>![Pause](images/segoe-mdl/e769.png)</td>
  <td><span data-ttu-id="127e7-1450">E769</span><span class="sxs-lookup"><span data-stu-id="127e7-1450">E769</span></span></td>
  <td><span data-ttu-id="127e7-1451">Pause</span><span class="sxs-lookup"><span data-stu-id="127e7-1451">Pause</span></span></td>
 </tr>
 <tr><td>![ChevronLeft](images/segoe-mdl/e76b.png)</td>
  <td><span data-ttu-id="127e7-1453">E76B</span><span class="sxs-lookup"><span data-stu-id="127e7-1453">E76B</span></span></td>
  <td><span data-ttu-id="127e7-1454">ChevronLeft</span><span class="sxs-lookup"><span data-stu-id="127e7-1454">ChevronLeft</span></span></td>
 </tr>
 <tr><td>![ChevronRight](images/segoe-mdl/e76c.png)</td>
  <td><span data-ttu-id="127e7-1456">E76C</span><span class="sxs-lookup"><span data-stu-id="127e7-1456">E76C</span></span></td>
  <td><span data-ttu-id="127e7-1457">ChevronRight</span><span class="sxs-lookup"><span data-stu-id="127e7-1457">ChevronRight</span></span></td>
 </tr>
 <tr><td>![InkingTool](images/segoe-mdl/e76d.png)</td>
  <td><span data-ttu-id="127e7-1459">E76D</span><span class="sxs-lookup"><span data-stu-id="127e7-1459">E76D</span></span></td>
  <td><span data-ttu-id="127e7-1460">InkingTool</span><span class="sxs-lookup"><span data-stu-id="127e7-1460">InkingTool</span></span></td>
 </tr>
 <tr><td>![Emoji2](images/segoe-mdl/e76e.png)</td>
  <td><span data-ttu-id="127e7-1462">E76E</span><span class="sxs-lookup"><span data-stu-id="127e7-1462">E76E</span></span></td>
  <td><span data-ttu-id="127e7-1463">Emoji2</span><span class="sxs-lookup"><span data-stu-id="127e7-1463">Emoji2</span></span></td>
 </tr>
 <tr><td>![GripperBarHorizontal](images/segoe-mdl/e76f.png)</td>
  <td><span data-ttu-id="127e7-1465">E76F</span><span class="sxs-lookup"><span data-stu-id="127e7-1465">E76F</span></span></td>
  <td><span data-ttu-id="127e7-1466">GripperBarHorizontal</span><span class="sxs-lookup"><span data-stu-id="127e7-1466">GripperBarHorizontal</span></span></td>
 </tr>
 <tr><td>![System](images/segoe-mdl/e770.png)</td>
  <td><span data-ttu-id="127e7-1468">E770</span><span class="sxs-lookup"><span data-stu-id="127e7-1468">E770</span></span></td>
  <td><span data-ttu-id="127e7-1469">System</span><span class="sxs-lookup"><span data-stu-id="127e7-1469">System</span></span></td>
 </tr>
 <tr><td>![Personalize](images/segoe-mdl/e771.png)</td>
  <td><span data-ttu-id="127e7-1471">E771</span><span class="sxs-lookup"><span data-stu-id="127e7-1471">E771</span></span></td>
  <td><span data-ttu-id="127e7-1472">Personalize</span><span class="sxs-lookup"><span data-stu-id="127e7-1472">Personalize</span></span></td>
 </tr>
 <tr><td>![Devices](images/segoe-mdl/e772.png)</td>
  <td><span data-ttu-id="127e7-1474">E772</span><span class="sxs-lookup"><span data-stu-id="127e7-1474">E772</span></span></td>
  <td><span data-ttu-id="127e7-1475">Devices</span><span class="sxs-lookup"><span data-stu-id="127e7-1475">Devices</span></span></td>
 </tr>
 <tr><td>![SearchAndApps](images/segoe-mdl/e773.png)</td>
  <td><span data-ttu-id="127e7-1477">E773</span><span class="sxs-lookup"><span data-stu-id="127e7-1477">E773</span></span></td>
  <td><span data-ttu-id="127e7-1478">SearchAndApps</span><span class="sxs-lookup"><span data-stu-id="127e7-1478">SearchAndApps</span></span></td>
 </tr>
 <tr><td>![Globe](images/segoe-mdl/e774.png)</td>
  <td><span data-ttu-id="127e7-1480">E774</span><span class="sxs-lookup"><span data-stu-id="127e7-1480">E774</span></span></td>
  <td><span data-ttu-id="127e7-1481">Globe</span><span class="sxs-lookup"><span data-stu-id="127e7-1481">Globe</span></span></td>
 </tr>
 <tr><td>![TimeLanguage](images/segoe-mdl/e775.png)</td>
  <td><span data-ttu-id="127e7-1483">E775</span><span class="sxs-lookup"><span data-stu-id="127e7-1483">E775</span></span></td>
  <td><span data-ttu-id="127e7-1484">TimeLanguage</span><span class="sxs-lookup"><span data-stu-id="127e7-1484">TimeLanguage</span></span></td>
 </tr>
 <tr><td>![EaseOfAccess](images/segoe-mdl/e776.png)</td>
  <td><span data-ttu-id="127e7-1486">E776</span><span class="sxs-lookup"><span data-stu-id="127e7-1486">E776</span></span></td>
  <td><span data-ttu-id="127e7-1487">EaseOfAccess</span><span class="sxs-lookup"><span data-stu-id="127e7-1487">EaseOfAccess</span></span></td>
 </tr>
 <tr><td>![UpdateRestore](images/segoe-mdl/e777.png)</td>
  <td><span data-ttu-id="127e7-1489">E777</span><span class="sxs-lookup"><span data-stu-id="127e7-1489">E777</span></span></td>
  <td><span data-ttu-id="127e7-1490">UpdateRestore</span><span class="sxs-lookup"><span data-stu-id="127e7-1490">UpdateRestore</span></span></td>
 </tr>
 <tr><td>![HangUp](images/segoe-mdl/e778.png)</td>
  <td><span data-ttu-id="127e7-1492">E778</span><span class="sxs-lookup"><span data-stu-id="127e7-1492">E778</span></span></td>
  <td><span data-ttu-id="127e7-1493">HangUp</span><span class="sxs-lookup"><span data-stu-id="127e7-1493">HangUp</span></span></td>
 </tr>
 <tr><td>![ContactInfo](images/segoe-mdl/e779.png)</td>
  <td><span data-ttu-id="127e7-1495">E779</span><span class="sxs-lookup"><span data-stu-id="127e7-1495">E779</span></span></td>
  <td><span data-ttu-id="127e7-1496">ContactInfo</span><span class="sxs-lookup"><span data-stu-id="127e7-1496">ContactInfo</span></span></td>
 </tr>
 <tr><td>![Unpin](images/segoe-mdl/e77a.png)</td>
  <td><span data-ttu-id="127e7-1498">E77A</span><span class="sxs-lookup"><span data-stu-id="127e7-1498">E77A</span></span></td>
  <td><span data-ttu-id="127e7-1499">Unpin</span><span class="sxs-lookup"><span data-stu-id="127e7-1499">Unpin</span></span></td>
 </tr>
 <tr><td>![Contact](images/segoe-mdl/e77b.png)</td>
  <td><span data-ttu-id="127e7-1501">E77B</span><span class="sxs-lookup"><span data-stu-id="127e7-1501">E77B</span></span></td>
  <td><span data-ttu-id="127e7-1502">Contact</span><span class="sxs-lookup"><span data-stu-id="127e7-1502">Contact</span></span></td>
 </tr>
 <tr><td>![Memo](images/segoe-mdl/e77c.png)</td>
  <td><span data-ttu-id="127e7-1504">E77C</span><span class="sxs-lookup"><span data-stu-id="127e7-1504">E77C</span></span></td>
  <td><span data-ttu-id="127e7-1505">Memo</span><span class="sxs-lookup"><span data-stu-id="127e7-1505">Memo</span></span></td>
 </tr>
 <tr><td>![Paste](images/segoe-mdl/e77f.png)</td>
  <td><span data-ttu-id="127e7-1507">E77F</span><span class="sxs-lookup"><span data-stu-id="127e7-1507">E77F</span></span></td>
  <td><span data-ttu-id="127e7-1508">Paste</span><span class="sxs-lookup"><span data-stu-id="127e7-1508">Paste</span></span></td>
 </tr>
 <tr><td>![PhoneBook](images/segoe-mdl/e780.png)</td>
  <td><span data-ttu-id="127e7-1510">E780</span><span class="sxs-lookup"><span data-stu-id="127e7-1510">E780</span></span></td>
  <td><span data-ttu-id="127e7-1511">PhoneBook</span><span class="sxs-lookup"><span data-stu-id="127e7-1511">PhoneBook</span></span></td>
 </tr>
 <tr><td>![LEDLight](images/segoe-mdl/e781.png)</td>
  <td><span data-ttu-id="127e7-1513">E781</span><span class="sxs-lookup"><span data-stu-id="127e7-1513">E781</span></span></td>
  <td><span data-ttu-id="127e7-1514">LEDLight</span><span class="sxs-lookup"><span data-stu-id="127e7-1514">LEDLight</span></span></td>
 </tr>
 <tr><td>![Error](images/segoe-mdl/e783.png)</td>
  <td><span data-ttu-id="127e7-1516">E783</span><span class="sxs-lookup"><span data-stu-id="127e7-1516">E783</span></span></td>
  <td><span data-ttu-id="127e7-1517">Error</span><span class="sxs-lookup"><span data-stu-id="127e7-1517">Error</span></span></td>
 </tr>
 <tr><td>![GripperBarVertical](images/segoe-mdl/e784.png)</td>
  <td><span data-ttu-id="127e7-1519">E784</span><span class="sxs-lookup"><span data-stu-id="127e7-1519">E784</span></span></td>
  <td><span data-ttu-id="127e7-1520">GripperBarVertical</span><span class="sxs-lookup"><span data-stu-id="127e7-1520">GripperBarVertical</span></span></td>
 </tr>
 <tr><td>![Unlock](images/segoe-mdl/e785.png)</td>
  <td><span data-ttu-id="127e7-1522">E785</span><span class="sxs-lookup"><span data-stu-id="127e7-1522">E785</span></span></td>
  <td><span data-ttu-id="127e7-1523">Unlock</span><span class="sxs-lookup"><span data-stu-id="127e7-1523">Unlock</span></span></td>
 </tr>
 <tr><td>![Slideshow](images/segoe-mdl/e786.png)</td>
  <td><span data-ttu-id="127e7-1525">E786</span><span class="sxs-lookup"><span data-stu-id="127e7-1525">E786</span></span></td>
  <td><span data-ttu-id="127e7-1526">Slideshow</span><span class="sxs-lookup"><span data-stu-id="127e7-1526">Slideshow</span></span></td>
 </tr>
 <tr><td>![Calendar](images/segoe-mdl/e787.png)</td>
  <td><span data-ttu-id="127e7-1528">E787</span><span class="sxs-lookup"><span data-stu-id="127e7-1528">E787</span></span></td>
  <td><span data-ttu-id="127e7-1529">Calendar</span><span class="sxs-lookup"><span data-stu-id="127e7-1529">Calendar</span></span></td>
 </tr>
 <tr><td>![GripperResize](images/segoe-mdl/e788.png)</td>
  <td><span data-ttu-id="127e7-1531">E788</span><span class="sxs-lookup"><span data-stu-id="127e7-1531">E788</span></span></td>
  <td><span data-ttu-id="127e7-1532">GripperResize</span><span class="sxs-lookup"><span data-stu-id="127e7-1532">GripperResize</span></span></td>
 </tr>
 <tr><td>![Megaphone](images/segoe-mdl/e789.png)</td>
  <td><span data-ttu-id="127e7-1534">E789</span><span class="sxs-lookup"><span data-stu-id="127e7-1534">E789</span></span></td>
  <td><span data-ttu-id="127e7-1535">Megaphone</span><span class="sxs-lookup"><span data-stu-id="127e7-1535">Megaphone</span></span></td>
 </tr>
 <tr><td>![Trim](images/segoe-mdl/e78a.png)</td>
  <td><span data-ttu-id="127e7-1537">E78A</span><span class="sxs-lookup"><span data-stu-id="127e7-1537">E78A</span></span></td>
  <td><span data-ttu-id="127e7-1538">Trim</span><span class="sxs-lookup"><span data-stu-id="127e7-1538">Trim</span></span></td>
 </tr>
 <tr><td>![NewWindow](images/segoe-mdl/e78b.png)</td>
  <td><span data-ttu-id="127e7-1540">E78B</span><span class="sxs-lookup"><span data-stu-id="127e7-1540">E78B</span></span></td>
  <td><span data-ttu-id="127e7-1541">NewWindow</span><span class="sxs-lookup"><span data-stu-id="127e7-1541">NewWindow</span></span></td>
 </tr>
 <tr><td>![SaveLocal](images/segoe-mdl/e78c.png)</td>
  <td><span data-ttu-id="127e7-1543">E78C</span><span class="sxs-lookup"><span data-stu-id="127e7-1543">E78C</span></span></td>
  <td><span data-ttu-id="127e7-1544">SaveLocal</span><span class="sxs-lookup"><span data-stu-id="127e7-1544">SaveLocal</span></span></td>
 </tr>
 <tr><td>![Color](images/segoe-mdl/e790.png)</td>
  <td><span data-ttu-id="127e7-1546">E790</span><span class="sxs-lookup"><span data-stu-id="127e7-1546">E790</span></span></td>
  <td><span data-ttu-id="127e7-1547">Color</span><span class="sxs-lookup"><span data-stu-id="127e7-1547">Color</span></span></td>
 </tr>
 <tr><td>![DataSense](images/segoe-mdl/e791.png)</td>
  <td><span data-ttu-id="127e7-1549">E791</span><span class="sxs-lookup"><span data-stu-id="127e7-1549">E791</span></span></td>
  <td><span data-ttu-id="127e7-1550">DataSense</span><span class="sxs-lookup"><span data-stu-id="127e7-1550">DataSense</span></span></td>
 </tr>
 <tr><td>![SaveAs](images/segoe-mdl/e792.png)</td>
  <td><span data-ttu-id="127e7-1552">E792</span><span class="sxs-lookup"><span data-stu-id="127e7-1552">E792</span></span></td>
  <td><span data-ttu-id="127e7-1553">SaveAs</span><span class="sxs-lookup"><span data-stu-id="127e7-1553">SaveAs</span></span></td>
 </tr>
 <tr><td>![Light](images/segoe-mdl/e793.png)</td>
  <td><span data-ttu-id="127e7-1555">E793</span><span class="sxs-lookup"><span data-stu-id="127e7-1555">E793</span></span></td>
  <td><span data-ttu-id="127e7-1556">Light</span><span class="sxs-lookup"><span data-stu-id="127e7-1556">Light</span></span></td>
 </tr>
 <tr><td>![AspectRatio](images/segoe-mdl/e799.png)</td>
  <td><span data-ttu-id="127e7-1558">E799</span><span class="sxs-lookup"><span data-stu-id="127e7-1558">E799</span></span></td>
  <td><span data-ttu-id="127e7-1559">AspectRatio</span><span class="sxs-lookup"><span data-stu-id="127e7-1559">AspectRatio</span></span></td>
 </tr>
 <tr><td>![DataSenseBar](images/segoe-mdl/e7a5.png)</td>
  <td><span data-ttu-id="127e7-1561">E7A5</span><span class="sxs-lookup"><span data-stu-id="127e7-1561">E7A5</span></span></td>
  <td><span data-ttu-id="127e7-1562">DataSenseBar</span><span class="sxs-lookup"><span data-stu-id="127e7-1562">DataSenseBar</span></span></td>
 </tr>
 <tr><td>![Redo](images/segoe-mdl/e7a6.png)</td>
  <td><span data-ttu-id="127e7-1564">E7A6</span><span class="sxs-lookup"><span data-stu-id="127e7-1564">E7A6</span></span></td>
  <td><span data-ttu-id="127e7-1565">Redo</span><span class="sxs-lookup"><span data-stu-id="127e7-1565">Redo</span></span></td>
 </tr>
 <tr><td>![Undo](images/segoe-mdl/e7a7.png)</td>
  <td><span data-ttu-id="127e7-1567">E7A7</span><span class="sxs-lookup"><span data-stu-id="127e7-1567">E7A7</span></span></td>
  <td><span data-ttu-id="127e7-1568">Undo</span><span class="sxs-lookup"><span data-stu-id="127e7-1568">Undo</span></span></td>
 </tr>
 <tr><td>![Crop](images/segoe-mdl/e7a8.png)</td>
  <td><span data-ttu-id="127e7-1570">E7A8</span><span class="sxs-lookup"><span data-stu-id="127e7-1570">E7A8</span></span></td>
  <td><span data-ttu-id="127e7-1571">Crop</span><span class="sxs-lookup"><span data-stu-id="127e7-1571">Crop</span></span></td>
 </tr>
 <tr><td>![OpenWith](images/segoe-mdl/e7ac.png)</td>
  <td><span data-ttu-id="127e7-1573">E7AC</span><span class="sxs-lookup"><span data-stu-id="127e7-1573">E7AC</span></span></td>
  <td><span data-ttu-id="127e7-1574">OpenWith</span><span class="sxs-lookup"><span data-stu-id="127e7-1574">OpenWith</span></span></td>
 </tr>
 <tr><td>![Rotate](images/segoe-mdl/e7ad.png)</td>
  <td><span data-ttu-id="127e7-1576">E7AD</span><span class="sxs-lookup"><span data-stu-id="127e7-1576">E7AD</span></span></td>
  <td><span data-ttu-id="127e7-1577">Rotate</span><span class="sxs-lookup"><span data-stu-id="127e7-1577">Rotate</span></span></td>
 </tr>
 <tr><td>![SetLockScreen](images/segoe-mdl/e7b5.png)</td>
  <td><span data-ttu-id="127e7-1579">E7B5</span><span class="sxs-lookup"><span data-stu-id="127e7-1579">E7B5</span></span></td>
  <td><span data-ttu-id="127e7-1580">SetLockScreen</span><span class="sxs-lookup"><span data-stu-id="127e7-1580">SetlockScreen</span></span></td>
 </tr>
 <tr><td>![MapPin2](images/segoe-mdl/e7b7.png)</td>
  <td><span data-ttu-id="127e7-1582">E7B7</span><span class="sxs-lookup"><span data-stu-id="127e7-1582">E7B7</span></span></td>
  <td><span data-ttu-id="127e7-1583">MapPin2</span><span class="sxs-lookup"><span data-stu-id="127e7-1583">MapPin2</span></span></td>
 </tr>
 <tr><td>![Package](images/segoe-mdl/e7b8.png)</td>
  <td><span data-ttu-id="127e7-1585">E7B8</span><span class="sxs-lookup"><span data-stu-id="127e7-1585">E7B8</span></span></td>
  <td><span data-ttu-id="127e7-1586">Package</span><span class="sxs-lookup"><span data-stu-id="127e7-1586">Package</span></span></td>
 </tr>
 <tr><td>![Warning](images/segoe-mdl/e7ba.png)</td>
  <td><span data-ttu-id="127e7-1588">E7BA</span><span class="sxs-lookup"><span data-stu-id="127e7-1588">E7BA</span></span></td>
  <td><span data-ttu-id="127e7-1589">Warning</span><span class="sxs-lookup"><span data-stu-id="127e7-1589">Warning</span></span></td>
 </tr>
 <tr><td>![ReadingList](images/segoe-mdl/e7bc.png)</td>
  <td><span data-ttu-id="127e7-1591">E7BC</span><span class="sxs-lookup"><span data-stu-id="127e7-1591">E7BC</span></span></td>
  <td><span data-ttu-id="127e7-1592">ReadingList</span><span class="sxs-lookup"><span data-stu-id="127e7-1592">ReadingList</span></span></td>
 </tr>
 <tr><td>![Education](images/segoe-mdl/e7be.png)</td>
  <td><span data-ttu-id="127e7-1594">E7BE</span><span class="sxs-lookup"><span data-stu-id="127e7-1594">E7BE</span></span></td>
  <td><span data-ttu-id="127e7-1595">Education</span><span class="sxs-lookup"><span data-stu-id="127e7-1595">Education</span></span></td>
 </tr>
 <tr><td>![ShoppingCart](images/segoe-mdl/e7bf.png)</td>
  <td><span data-ttu-id="127e7-1597">E7BF</span><span class="sxs-lookup"><span data-stu-id="127e7-1597">E7BF</span></span></td>
  <td><span data-ttu-id="127e7-1598">ShoppingCart</span><span class="sxs-lookup"><span data-stu-id="127e7-1598">ShoppingCart</span></span></td>
 </tr>
 <tr><td>![Train](images/segoe-mdl/e7c0.png)</td>
  <td><span data-ttu-id="127e7-1600">E7C0</span><span class="sxs-lookup"><span data-stu-id="127e7-1600">E7C0</span></span></td>
  <td><span data-ttu-id="127e7-1601">Train</span><span class="sxs-lookup"><span data-stu-id="127e7-1601">Train</span></span></td>
 </tr>
 <tr><td>![Flag](images/segoe-mdl/e7c1.png)</td>
  <td><span data-ttu-id="127e7-1603">E7C1</span><span class="sxs-lookup"><span data-stu-id="127e7-1603">E7C1</span></span></td>
  <td><span data-ttu-id="127e7-1604">Flag</span><span class="sxs-lookup"><span data-stu-id="127e7-1604">Flag</span></span></td>
 </tr>
 <tr><td>![Page](images/segoe-mdl/e7c3.png)</td>
  <td><span data-ttu-id="127e7-1606">E7C3</span><span class="sxs-lookup"><span data-stu-id="127e7-1606">E7C3</span></span></td>
  <td><span data-ttu-id="127e7-1607">Page</span><span class="sxs-lookup"><span data-stu-id="127e7-1607">Page</span></span></td>
 </tr>
 <tr><td>![Multitask](images/segoe-mdl/e7c4.png)</td>
  <td><span data-ttu-id="127e7-1609">E7C4</span><span class="sxs-lookup"><span data-stu-id="127e7-1609">E7C4</span></span></td>
  <td><span data-ttu-id="127e7-1610">Multitask</span><span class="sxs-lookup"><span data-stu-id="127e7-1610">Multitask</span></span></td>
 </tr>
 <tr><td>![BrowsePhotos](images/segoe-mdl/e7c5.png)</td>
  <td><span data-ttu-id="127e7-1612">E7C5</span><span class="sxs-lookup"><span data-stu-id="127e7-1612">E7C5</span></span></td>
  <td><span data-ttu-id="127e7-1613">BrowsePhotos</span><span class="sxs-lookup"><span data-stu-id="127e7-1613">BrowsePhotos</span></span></td>
 </tr>
 <tr><td>![HalfStarLeft](images/segoe-mdl/e7c6.png)</td>
  <td><span data-ttu-id="127e7-1615">E7C6</span><span class="sxs-lookup"><span data-stu-id="127e7-1615">E7C6</span></span></td>
  <td><span data-ttu-id="127e7-1616">HalfStarLeft</span><span class="sxs-lookup"><span data-stu-id="127e7-1616">HalfStarLeft</span></span></td>
 </tr>
 <tr><td>![HalfStarRight](images/segoe-mdl/e7c7.png)</td>
  <td><span data-ttu-id="127e7-1618">E7C7</span><span class="sxs-lookup"><span data-stu-id="127e7-1618">E7C7</span></span></td>
  <td><span data-ttu-id="127e7-1619">HalfStarRight</span><span class="sxs-lookup"><span data-stu-id="127e7-1619">HalfStarRight</span></span></td>
 </tr>
 <tr><td>![Record](images/segoe-mdl/e7c8.png)</td>
  <td><span data-ttu-id="127e7-1621">E7C8</span><span class="sxs-lookup"><span data-stu-id="127e7-1621">E7C8</span></span></td>
  <td><span data-ttu-id="127e7-1622">Record</span><span class="sxs-lookup"><span data-stu-id="127e7-1622">Record</span></span></td>
 </tr>
 <tr><td>![TouchPointer](images/segoe-mdl/e7c9.png)</td>
  <td><span data-ttu-id="127e7-1624">E7C9</span><span class="sxs-lookup"><span data-stu-id="127e7-1624">E7C9</span></span></td>
  <td><span data-ttu-id="127e7-1625">TouchPointer</span><span class="sxs-lookup"><span data-stu-id="127e7-1625">TouchPointer</span></span></td>
 </tr>
 <tr><td>![LangJPN](images/segoe-mdl/e7de.png)</td>
  <td><span data-ttu-id="127e7-1627">E7DE</span><span class="sxs-lookup"><span data-stu-id="127e7-1627">E7DE</span></span></td>
  <td><span data-ttu-id="127e7-1628">LangJPN</span><span class="sxs-lookup"><span data-stu-id="127e7-1628">LangJPN</span></span></td>
 </tr>
 <tr><td>![Ferry](images/segoe-mdl/e7e3.png)</td>
  <td><span data-ttu-id="127e7-1630">E7E3</span><span class="sxs-lookup"><span data-stu-id="127e7-1630">E7E3</span></span></td>
  <td><span data-ttu-id="127e7-1631">Ferry</span><span class="sxs-lookup"><span data-stu-id="127e7-1631">Ferry</span></span></td>
 </tr>
 <tr><td>![Highlight](images/segoe-mdl/e7e6.png)</td>
  <td><span data-ttu-id="127e7-1633">E7E6</span><span class="sxs-lookup"><span data-stu-id="127e7-1633">E7E6</span></span></td>
  <td><span data-ttu-id="127e7-1634">Highlight</span><span class="sxs-lookup"><span data-stu-id="127e7-1634">Highlight</span></span></td>
 </tr>
 <tr><td>![ActionCenterNotification](images/segoe-mdl/e7e7.png)</td>
  <td><span data-ttu-id="127e7-1636">E7E7</span><span class="sxs-lookup"><span data-stu-id="127e7-1636">E7E7</span></span></td>
  <td><span data-ttu-id="127e7-1637">ActionCenterNotification</span><span class="sxs-lookup"><span data-stu-id="127e7-1637">ActionCenterNotification</span></span></td>
 </tr>
 <tr><td>![PowerButton](images/segoe-mdl/e7e8.png)</td>
  <td><span data-ttu-id="127e7-1639">E7E8</span><span class="sxs-lookup"><span data-stu-id="127e7-1639">E7E8</span></span></td>
  <td><span data-ttu-id="127e7-1640">PowerButton</span><span class="sxs-lookup"><span data-stu-id="127e7-1640">PowerButton</span></span></td>
 </tr>
 <tr><td>![ResizeTouchNarrower](images/segoe-mdl/e7ea.png)</td>
  <td><span data-ttu-id="127e7-1642">E7EA</span><span class="sxs-lookup"><span data-stu-id="127e7-1642">E7EA</span></span></td>
  <td><span data-ttu-id="127e7-1643">ResizeTouchNarrower</span><span class="sxs-lookup"><span data-stu-id="127e7-1643">ResizeTouchNarrower</span></span></td>
 </tr>
 <tr><td>![ResizeTouchShorter](images/segoe-mdl/e7eb.png)</td>
  <td><span data-ttu-id="127e7-1645">E7EB</span><span class="sxs-lookup"><span data-stu-id="127e7-1645">E7EB</span></span></td>
  <td><span data-ttu-id="127e7-1646">ResizeTouchShorter</span><span class="sxs-lookup"><span data-stu-id="127e7-1646">ResizeTouchShorter</span></span></td>
 </tr>
 <tr><td>![DrivingMode](images/segoe-mdl/e7ec.png)</td>
  <td><span data-ttu-id="127e7-1648">E7EC</span><span class="sxs-lookup"><span data-stu-id="127e7-1648">E7EC</span></span></td>
  <td><span data-ttu-id="127e7-1649">DrivingMode</span><span class="sxs-lookup"><span data-stu-id="127e7-1649">DrivingMode</span></span></td>
 </tr>
 <tr><td>![RingerSilent](images/segoe-mdl/e7ed.png)</td>
  <td><span data-ttu-id="127e7-1651">E7ED</span><span class="sxs-lookup"><span data-stu-id="127e7-1651">E7ED</span></span></td>
  <td><span data-ttu-id="127e7-1652">RingerSilent</span><span class="sxs-lookup"><span data-stu-id="127e7-1652">RingerSilent</span></span></td>
 </tr>
 <tr><td>![OtherUser](images/segoe-mdl/e7ee.png)</td>
  <td><span data-ttu-id="127e7-1654">E7EE</span><span class="sxs-lookup"><span data-stu-id="127e7-1654">E7EE</span></span></td>
  <td><span data-ttu-id="127e7-1655">OtherUser</span><span class="sxs-lookup"><span data-stu-id="127e7-1655">OtherUser</span></span></td>
 </tr>
 <tr><td>![Admin](images/segoe-mdl/e7ef.png)</td>
  <td><span data-ttu-id="127e7-1657">E7EF</span><span class="sxs-lookup"><span data-stu-id="127e7-1657">E7EF</span></span></td>
  <td><span data-ttu-id="127e7-1658">Admin</span><span class="sxs-lookup"><span data-stu-id="127e7-1658">Admin</span></span></td>
 </tr>
 <tr><td>![CC](images/segoe-mdl/e7f0.png)</td>
  <td><span data-ttu-id="127e7-1660">E7F0</span><span class="sxs-lookup"><span data-stu-id="127e7-1660">E7F0</span></span></td>
  <td><span data-ttu-id="127e7-1661">CC</span><span class="sxs-lookup"><span data-stu-id="127e7-1661">CC</span></span></td>
 </tr>
 <tr><td>![SDCard](images/segoe-mdl/e7f1.png)</td>
  <td><span data-ttu-id="127e7-1663">E7F1</span><span class="sxs-lookup"><span data-stu-id="127e7-1663">E7F1</span></span></td>
  <td><span data-ttu-id="127e7-1664">SDCard</span><span class="sxs-lookup"><span data-stu-id="127e7-1664">SDCard</span></span></td>
 </tr>
 <tr><td>![CallForwarding](images/segoe-mdl/e7f2.png)</td>
  <td><span data-ttu-id="127e7-1666">E7F2</span><span class="sxs-lookup"><span data-stu-id="127e7-1666">E7F2</span></span></td>
  <td><span data-ttu-id="127e7-1667">CallForwarding</span><span class="sxs-lookup"><span data-stu-id="127e7-1667">CallForwarding</span></span></td>
 </tr>
 <tr><td>![SettingsDisplaySound](images/segoe-mdl/e7f3.png)</td>
  <td><span data-ttu-id="127e7-1669">E7F3</span><span class="sxs-lookup"><span data-stu-id="127e7-1669">E7F3</span></span></td>
  <td><span data-ttu-id="127e7-1670">SettingsDisplaySound</span><span class="sxs-lookup"><span data-stu-id="127e7-1670">SettingsDisplaySound</span></span></td>
 </tr>
 <tr><td>![TVMonitor](images/segoe-mdl/e7f4.png)</td>
  <td><span data-ttu-id="127e7-1672">E7F4</span><span class="sxs-lookup"><span data-stu-id="127e7-1672">E7F4</span></span></td>
  <td><span data-ttu-id="127e7-1673">TVMonitor</span><span class="sxs-lookup"><span data-stu-id="127e7-1673">TVMonitor</span></span></td>
 </tr>
 <tr><td>![Speakers](images/segoe-mdl/e7f5.png)</td>
  <td><span data-ttu-id="127e7-1675">E7F5</span><span class="sxs-lookup"><span data-stu-id="127e7-1675">E7F5</span></span></td>
  <td><span data-ttu-id="127e7-1676">Speakers</span><span class="sxs-lookup"><span data-stu-id="127e7-1676">Speakers</span></span></td>
 </tr>
 <tr><td>![Headphone](images/segoe-mdl/e7f6.png)</td>
  <td><span data-ttu-id="127e7-1678">E7F6</span><span class="sxs-lookup"><span data-stu-id="127e7-1678">E7F6</span></span></td>
  <td><span data-ttu-id="127e7-1679">Headphone</span><span class="sxs-lookup"><span data-stu-id="127e7-1679">Headphone</span></span></td>
 </tr>
 <tr><td>![DeviceLaptopPic](images/segoe-mdl/e7f7.png)</td>
  <td><span data-ttu-id="127e7-1681">E7F7</span><span class="sxs-lookup"><span data-stu-id="127e7-1681">E7F7</span></span></td>
  <td><span data-ttu-id="127e7-1682">DeviceLaptopPic</span><span class="sxs-lookup"><span data-stu-id="127e7-1682">DeviceLaptopPic</span></span></td>
 </tr>
 <tr><td>![DeviceLaptopNoPic](images/segoe-mdl/e7f8.png)</td>
  <td><span data-ttu-id="127e7-1684">E7F8</span><span class="sxs-lookup"><span data-stu-id="127e7-1684">E7F8</span></span></td>
  <td><span data-ttu-id="127e7-1685">DeviceLaptopNoPic</span><span class="sxs-lookup"><span data-stu-id="127e7-1685">DeviceLaptopNoPic</span></span></td>
 </tr>
 <tr><td>![DeviceMonitorRightPic](images/segoe-mdl/e7f9.png)</td>
  <td><span data-ttu-id="127e7-1687">E7F9</span><span class="sxs-lookup"><span data-stu-id="127e7-1687">E7F9</span></span></td>
  <td><span data-ttu-id="127e7-1688">DeviceMonitorRightPic</span><span class="sxs-lookup"><span data-stu-id="127e7-1688">DeviceMonitorRightPic</span></span></td>
 </tr>
 <tr><td>![DeviceMonitorLeftPic](images/segoe-mdl/e7fa.png)</td>
  <td><span data-ttu-id="127e7-1690">E7FA</span><span class="sxs-lookup"><span data-stu-id="127e7-1690">E7FA</span></span></td>
  <td><span data-ttu-id="127e7-1691">DeviceMonitorLeftPic</span><span class="sxs-lookup"><span data-stu-id="127e7-1691">DeviceMonitorLeftPic</span></span></td>
 </tr>
 <tr><td>![DeviceMonitorNoPic](images/segoe-mdl/e7fb.png)</td>
  <td><span data-ttu-id="127e7-1693">E7FB</span><span class="sxs-lookup"><span data-stu-id="127e7-1693">E7FB</span></span></td>
  <td><span data-ttu-id="127e7-1694">DeviceMonitorNoPic</span><span class="sxs-lookup"><span data-stu-id="127e7-1694">DeviceMonitorNoPic</span></span></td>
 </tr>
 <tr><td>![Game](images/segoe-mdl/e7fc.png)</td>
  <td><span data-ttu-id="127e7-1696">E7FC</span><span class="sxs-lookup"><span data-stu-id="127e7-1696">E7FC</span></span></td>
  <td><span data-ttu-id="127e7-1697">Game</span><span class="sxs-lookup"><span data-stu-id="127e7-1697">Game</span></span></td>
 </tr>
 <tr><td>![HorizontalTabKey](images/segoe-mdl/e7fd.png)</td>
  <td><span data-ttu-id="127e7-1699">E7FD</span><span class="sxs-lookup"><span data-stu-id="127e7-1699">E7FD</span></span></td>
  <td><span data-ttu-id="127e7-1700">HorizontalTabKey</span><span class="sxs-lookup"><span data-stu-id="127e7-1700">HorizontalTabKey</span></span></td>
 </tr>
 <tr><td>![StreetsideSplitMinimize](images/segoe-mdl/e802.png)</td>
  <td><span data-ttu-id="127e7-1702">E802</span><span class="sxs-lookup"><span data-stu-id="127e7-1702">E802</span></span></td>
  <td><span data-ttu-id="127e7-1703">StreetsideSplitMinimize</span><span class="sxs-lookup"><span data-stu-id="127e7-1703">StreetsideSplitMinimize</span></span></td>
 </tr>
 <tr><td>![StreetsideSplitExpand](images/segoe-mdl/e803.png)</td>
  <td><span data-ttu-id="127e7-1705">E803</span><span class="sxs-lookup"><span data-stu-id="127e7-1705">E803</span></span></td>
  <td><span data-ttu-id="127e7-1706">StreetsideSplitExpand</span><span class="sxs-lookup"><span data-stu-id="127e7-1706">StreetsideSplitExpand</span></span></td>
 </tr>
 <tr><td>![Car](images/segoe-mdl/e804.png)</td>
  <td><span data-ttu-id="127e7-1708">E804</span><span class="sxs-lookup"><span data-stu-id="127e7-1708">E804</span></span></td>
  <td><span data-ttu-id="127e7-1709">Car</span><span class="sxs-lookup"><span data-stu-id="127e7-1709">Car</span></span></td>
 </tr>
 <tr><td>![Walk](images/segoe-mdl/e805.png)</td>
  <td><span data-ttu-id="127e7-1711">E805</span><span class="sxs-lookup"><span data-stu-id="127e7-1711">E805</span></span></td>
  <td><span data-ttu-id="127e7-1712">Walk</span><span class="sxs-lookup"><span data-stu-id="127e7-1712">Walk</span></span></td>
 </tr>
 <tr><td>![Bus](images/segoe-mdl/e806.png)</td>
  <td><span data-ttu-id="127e7-1714">E806</span><span class="sxs-lookup"><span data-stu-id="127e7-1714">E806</span></span></td>
  <td><span data-ttu-id="127e7-1715">Bus</span><span class="sxs-lookup"><span data-stu-id="127e7-1715">Bus</span></span></td>
 </tr>
 <tr><td>![TiltUp](images/segoe-mdl/e809.png)</td>
  <td><span data-ttu-id="127e7-1717">E809</span><span class="sxs-lookup"><span data-stu-id="127e7-1717">E809</span></span></td>
  <td><span data-ttu-id="127e7-1718">TiltUp</span><span class="sxs-lookup"><span data-stu-id="127e7-1718">TiltUp</span></span></td>
 </tr>
 <tr><td>![TiltDown](images/segoe-mdl/e80a.png)</td>
  <td><span data-ttu-id="127e7-1720">E80A</span><span class="sxs-lookup"><span data-stu-id="127e7-1720">E80A</span></span></td>
  <td><span data-ttu-id="127e7-1721">TiltDown</span><span class="sxs-lookup"><span data-stu-id="127e7-1721">TiltDown</span></span></td>
 </tr>
 <tr><td>![RotateMapRight](images/segoe-mdl/e80c.png)</td>
  <td><span data-ttu-id="127e7-1723">E80C</span><span class="sxs-lookup"><span data-stu-id="127e7-1723">E80C</span></span></td>
  <td><span data-ttu-id="127e7-1724">RotateMapRight</span><span class="sxs-lookup"><span data-stu-id="127e7-1724">RotateMapRight</span></span></td>
 </tr>
 <tr><td>![RotateMapLeft](images/segoe-mdl/e80d.png)</td>
  <td><span data-ttu-id="127e7-1726">E80D</span><span class="sxs-lookup"><span data-stu-id="127e7-1726">E80D</span></span></td>
  <td><span data-ttu-id="127e7-1727">RotateMapLeft</span><span class="sxs-lookup"><span data-stu-id="127e7-1727">RotateMapLeft</span></span></td>
 </tr>
 <tr><td>![Home](images/segoe-mdl/e80f.png)</td>
  <td><span data-ttu-id="127e7-1729">E80F</span><span class="sxs-lookup"><span data-stu-id="127e7-1729">E80F</span></span></td>
  <td><span data-ttu-id="127e7-1730">Home</span><span class="sxs-lookup"><span data-stu-id="127e7-1730">Home</span></span></td>
 </tr>
 <tr><td>![ParkingLocation](images/segoe-mdl/e811.png)</td>
  <td><span data-ttu-id="127e7-1732">E811</span><span class="sxs-lookup"><span data-stu-id="127e7-1732">E811</span></span></td>
  <td><span data-ttu-id="127e7-1733">ParkingLocation</span><span class="sxs-lookup"><span data-stu-id="127e7-1733">ParkingLocation</span></span></td>
 </tr>
 <tr><td>![MapCompassTop](images/segoe-mdl/e812.png)</td>
  <td><span data-ttu-id="127e7-1735">E812</span><span class="sxs-lookup"><span data-stu-id="127e7-1735">E812</span></span></td>
  <td><span data-ttu-id="127e7-1736">MapCompassTop</span><span class="sxs-lookup"><span data-stu-id="127e7-1736">MapCompassTop</span></span></td>
 </tr>
 <tr><td>![MapCompassBottom](images/segoe-mdl/e813.png)</td>
  <td><span data-ttu-id="127e7-1738">E813</span><span class="sxs-lookup"><span data-stu-id="127e7-1738">E813</span></span></td>
  <td><span data-ttu-id="127e7-1739">MapCompassBottom</span><span class="sxs-lookup"><span data-stu-id="127e7-1739">MapCompassBottom</span></span></td>
 </tr>
 <tr><td>![IncidentTriangle](images/segoe-mdl/e814.png)</td>
  <td><span data-ttu-id="127e7-1741">E814</span><span class="sxs-lookup"><span data-stu-id="127e7-1741">E814</span></span></td>
  <td><span data-ttu-id="127e7-1742">IncidentTriangle</span><span class="sxs-lookup"><span data-stu-id="127e7-1742">IncidentTriangle</span></span></td>
 </tr>
 <tr><td>![Touch](images/segoe-mdl/e815.png)</td>
  <td><span data-ttu-id="127e7-1744">E815</span><span class="sxs-lookup"><span data-stu-id="127e7-1744">E815</span></span></td>
  <td><span data-ttu-id="127e7-1745">Touch</span><span class="sxs-lookup"><span data-stu-id="127e7-1745">Touch</span></span></td>
 </tr>
 <tr><td>![MapDirections](images/segoe-mdl/e816.png)</td>
  <td><span data-ttu-id="127e7-1747">E816</span><span class="sxs-lookup"><span data-stu-id="127e7-1747">E816</span></span></td>
  <td><span data-ttu-id="127e7-1748">MapDirections</span><span class="sxs-lookup"><span data-stu-id="127e7-1748">MapDirections</span></span></td>
 </tr>
 <tr><td>![StartPoint](images/segoe-mdl/e819.png)</td>
  <td><span data-ttu-id="127e7-1750">E819</span><span class="sxs-lookup"><span data-stu-id="127e7-1750">E819</span></span></td>
  <td><span data-ttu-id="127e7-1751">StartPoint</span><span class="sxs-lookup"><span data-stu-id="127e7-1751">StartPoint</span></span></td>
 </tr>
 <tr><td>![StopPoint](images/segoe-mdl/e81a.png)</td>
  <td><span data-ttu-id="127e7-1753">E81A</span><span class="sxs-lookup"><span data-stu-id="127e7-1753">E81A</span></span></td>
  <td><span data-ttu-id="127e7-1754">StopPoint</span><span class="sxs-lookup"><span data-stu-id="127e7-1754">StopPoint</span></span></td>
 </tr>
 <tr><td>![EndPoint](images/segoe-mdl/e81b.png)</td>
  <td><span data-ttu-id="127e7-1756">E81B</span><span class="sxs-lookup"><span data-stu-id="127e7-1756">E81B</span></span></td>
  <td><span data-ttu-id="127e7-1757">EndPoint</span><span class="sxs-lookup"><span data-stu-id="127e7-1757">EndPoint</span></span></td>
 </tr>
 <tr><td>![History](images/segoe-mdl/e81c.png)</td>
  <td><span data-ttu-id="127e7-1759">E81C</span><span class="sxs-lookup"><span data-stu-id="127e7-1759">E81C</span></span></td>
  <td><span data-ttu-id="127e7-1760">History</span><span class="sxs-lookup"><span data-stu-id="127e7-1760">History</span></span></td>
 </tr>
 <tr><td>![Location](images/segoe-mdl/e81d.png)</td>
  <td><span data-ttu-id="127e7-1762">E81D</span><span class="sxs-lookup"><span data-stu-id="127e7-1762">E81D</span></span></td>
  <td><span data-ttu-id="127e7-1763">Location</span><span class="sxs-lookup"><span data-stu-id="127e7-1763">Location</span></span></td>
 </tr>
 <tr><td>![MapLayers](images/segoe-mdl/e81e.png)</td>
  <td><span data-ttu-id="127e7-1765">E81E</span><span class="sxs-lookup"><span data-stu-id="127e7-1765">E81E</span></span></td>
  <td><span data-ttu-id="127e7-1766">MapLayers</span><span class="sxs-lookup"><span data-stu-id="127e7-1766">MapLayers</span></span></td>
 </tr>
 <tr><td>![Accident](images/segoe-mdl/e81f.png)</td>
  <td><span data-ttu-id="127e7-1768">E81F</span><span class="sxs-lookup"><span data-stu-id="127e7-1768">E81F</span></span></td>
  <td><span data-ttu-id="127e7-1769">Accident</span><span class="sxs-lookup"><span data-stu-id="127e7-1769">Accident</span></span></td>
 </tr>
 <tr><td>![Work](images/segoe-mdl/e821.png)</td>
  <td><span data-ttu-id="127e7-1771">E821</span><span class="sxs-lookup"><span data-stu-id="127e7-1771">E821</span></span></td>
  <td><span data-ttu-id="127e7-1772">Work</span><span class="sxs-lookup"><span data-stu-id="127e7-1772">Work</span></span></td>
 </tr>
 <tr><td>![Construction](images/segoe-mdl/e822.png)</td>
  <td><span data-ttu-id="127e7-1774">E822</span><span class="sxs-lookup"><span data-stu-id="127e7-1774">E822</span></span></td>
  <td><span data-ttu-id="127e7-1775">Construction</span><span class="sxs-lookup"><span data-stu-id="127e7-1775">Construction</span></span></td>
 </tr>
 <tr><td>![Recent](images/segoe-mdl/e823.png)</td>
  <td><span data-ttu-id="127e7-1777">E823</span><span class="sxs-lookup"><span data-stu-id="127e7-1777">E823</span></span></td>
  <td><span data-ttu-id="127e7-1778">Recent</span><span class="sxs-lookup"><span data-stu-id="127e7-1778">Recent</span></span></td>
 </tr>
 <tr><td>![Bank](images/segoe-mdl/e825.png)</td>
  <td><span data-ttu-id="127e7-1780">E825</span><span class="sxs-lookup"><span data-stu-id="127e7-1780">E825</span></span></td>
  <td><span data-ttu-id="127e7-1781">Bank</span><span class="sxs-lookup"><span data-stu-id="127e7-1781">Bank</span></span></td>
 </tr>
 <tr><td>![DownloadMap](images/segoe-mdl/e826.png)</td>
  <td><span data-ttu-id="127e7-1783">E826</span><span class="sxs-lookup"><span data-stu-id="127e7-1783">E826</span></span></td>
  <td><span data-ttu-id="127e7-1784">DownloadMap</span><span class="sxs-lookup"><span data-stu-id="127e7-1784">DownloadMap</span></span></td>
 </tr>
 <tr><td>![InkingToolFill2](images/segoe-mdl/e829.png)</td>
  <td><span data-ttu-id="127e7-1786">E829</span><span class="sxs-lookup"><span data-stu-id="127e7-1786">E829</span></span></td>
  <td><span data-ttu-id="127e7-1787">InkingToolFill2</span><span class="sxs-lookup"><span data-stu-id="127e7-1787">InkingToolFill2</span></span></td>
 </tr>
 <tr><td>![HighlightFill2](images/segoe-mdl/e82a.png)</td>
  <td><span data-ttu-id="127e7-1789">E82A</span><span class="sxs-lookup"><span data-stu-id="127e7-1789">E82A</span></span></td>
  <td><span data-ttu-id="127e7-1790">HighlightFill2</span><span class="sxs-lookup"><span data-stu-id="127e7-1790">HighlightFill2</span></span></td>
 </tr>
 <tr><td>![EraseToolFill](images/segoe-mdl/e82b.png)</td>
  <td><span data-ttu-id="127e7-1792">E82B</span><span class="sxs-lookup"><span data-stu-id="127e7-1792">E82B</span></span></td>
  <td><span data-ttu-id="127e7-1793">EraseToolFill</span><span class="sxs-lookup"><span data-stu-id="127e7-1793">EraseToolFill</span></span></td>
 </tr>
 <tr><td>![EraseToolFill2](images/segoe-mdl/e82c.png)</td>
  <td><span data-ttu-id="127e7-1795">E82C</span><span class="sxs-lookup"><span data-stu-id="127e7-1795">E82C</span></span></td>
  <td><span data-ttu-id="127e7-1796">EraseToolFill2</span><span class="sxs-lookup"><span data-stu-id="127e7-1796">EraseToolFill2</span></span></td>
 </tr>
 <tr><td>![Dictionary](images/segoe-mdl/e82d.png)</td>
  <td><span data-ttu-id="127e7-1798">E82D</span><span class="sxs-lookup"><span data-stu-id="127e7-1798">E82D</span></span></td>
  <td><span data-ttu-id="127e7-1799">Dictionary</span><span class="sxs-lookup"><span data-stu-id="127e7-1799">Dictionary</span></span></td>
 </tr>
 <tr><td>![DictionaryAdd](images/segoe-mdl/e82e.png)</td>
  <td><span data-ttu-id="127e7-1801">E82E</span><span class="sxs-lookup"><span data-stu-id="127e7-1801">E82E</span></span></td>
  <td><span data-ttu-id="127e7-1802">DictionaryAdd</span><span class="sxs-lookup"><span data-stu-id="127e7-1802">DictionaryAdd</span></span></td>
 </tr>
 <tr><td>![ToolTip](images/segoe-mdl/e82f.png)</td>
  <td><span data-ttu-id="127e7-1804">E82F</span><span class="sxs-lookup"><span data-stu-id="127e7-1804">E82F</span></span></td>
  <td><span data-ttu-id="127e7-1805">ToolTip</span><span class="sxs-lookup"><span data-stu-id="127e7-1805">ToolTip</span></span></td>
 </tr>
 <tr><td>![ChromeBack](images/segoe-mdl/e830.png)</td>
  <td><span data-ttu-id="127e7-1807">E830</span><span class="sxs-lookup"><span data-stu-id="127e7-1807">E830</span></span></td>
  <td><span data-ttu-id="127e7-1808">ChromeBack</span><span class="sxs-lookup"><span data-stu-id="127e7-1808">ChromeBack</span></span></td>
 </tr>
 <tr><td>![ProvisioningPackage](images/segoe-mdl/e835.png)</td>
  <td><span data-ttu-id="127e7-1810">E835</span><span class="sxs-lookup"><span data-stu-id="127e7-1810">E835</span></span></td>
  <td><span data-ttu-id="127e7-1811">ProvisioningPackage</span><span class="sxs-lookup"><span data-stu-id="127e7-1811">ProvisioningPackage</span></span></td>
 </tr>
 <tr><td>![AddRemoteDevice](images/segoe-mdl/e836.png)</td>
  <td><span data-ttu-id="127e7-1813">E836</span><span class="sxs-lookup"><span data-stu-id="127e7-1813">E836</span></span></td>
  <td><span data-ttu-id="127e7-1814">AddRemoteDevice</span><span class="sxs-lookup"><span data-stu-id="127e7-1814">AddRemoteDevice</span></span></td>
 </tr>
 <tr><td>![Ethernet](images/segoe-mdl/e839.png)</td>
  <td><span data-ttu-id="127e7-1816">E839</span><span class="sxs-lookup"><span data-stu-id="127e7-1816">E839</span></span></td>
  <td><span data-ttu-id="127e7-1817">Ethernet</span><span class="sxs-lookup"><span data-stu-id="127e7-1817">Ethernet</span></span></td>
 </tr>
 <tr><td>![&nbsp;ShareBroadband](images/segoe-mdl/e83a.png)</td>
  <td><span data-ttu-id="127e7-1819">E83A</span><span class="sxs-lookup"><span data-stu-id="127e7-1819">E83A</span></span></td>
  <td><span data-ttu-id="127e7-1820">&nbsp;ShareBroadband</span><span class="sxs-lookup"><span data-stu-id="127e7-1820">&nbsp;ShareBroadband</span></span></td>
 </tr>
 <tr><td>![DirectAccess](images/segoe-mdl/e83b.png)</td>
  <td><span data-ttu-id="127e7-1822">E83B</span><span class="sxs-lookup"><span data-stu-id="127e7-1822">E83B</span></span></td>
  <td><span data-ttu-id="127e7-1823">DirectAccess</span><span class="sxs-lookup"><span data-stu-id="127e7-1823">DirectAccess</span></span></td>
 </tr>
 <tr><td>![&nbsp;DialUp](images/segoe-mdl/e83c.png)</td>
  <td><span data-ttu-id="127e7-1825">E83C</span><span class="sxs-lookup"><span data-stu-id="127e7-1825">E83C</span></span></td>
  <td><span data-ttu-id="127e7-1826">&nbsp;DialUp</span><span class="sxs-lookup"><span data-stu-id="127e7-1826">&nbsp;DialUp</span></span></td>
 </tr>
 <tr><td>![DefenderApp](images/segoe-mdl/e83d.png)</td>
  <td><span data-ttu-id="127e7-1828">E83D</span><span class="sxs-lookup"><span data-stu-id="127e7-1828">E83D</span></span></td>
  <td><span data-ttu-id="127e7-1829">DefenderApp</span><span class="sxs-lookup"><span data-stu-id="127e7-1829">DefenderApp</span></span></td>
 </tr>
 <tr><td>![BatteryCharging9](images/segoe-mdl/e83e.png)</td>
  <td><span data-ttu-id="127e7-1831">E83E</span><span class="sxs-lookup"><span data-stu-id="127e7-1831">E83E</span></span></td>
  <td><span data-ttu-id="127e7-1832">BatteryCharging9</span><span class="sxs-lookup"><span data-stu-id="127e7-1832">BatteryCharging9</span></span></td>
 </tr>
 <tr><td>![Battery10](images/segoe-mdl/e83f.png)</td>
  <td><span data-ttu-id="127e7-1834">E83F</span><span class="sxs-lookup"><span data-stu-id="127e7-1834">E83F</span></span></td>
  <td><span data-ttu-id="127e7-1835">Battery10</span><span class="sxs-lookup"><span data-stu-id="127e7-1835">Battery10</span></span></td>
 </tr>
 <tr><td>![Pinned](images/segoe-mdl/e840.png)</td>
  <td><span data-ttu-id="127e7-1837">E840</span><span class="sxs-lookup"><span data-stu-id="127e7-1837">E840</span></span></td>
  <td><span data-ttu-id="127e7-1838">Pinned</span><span class="sxs-lookup"><span data-stu-id="127e7-1838">Pinned</span></span></td>
 </tr>
 <tr><td>![PinFill](images/segoe-mdl/e841.png)</td>
  <td><span data-ttu-id="127e7-1840">E841</span><span class="sxs-lookup"><span data-stu-id="127e7-1840">E841</span></span></td>
  <td><span data-ttu-id="127e7-1841">PinFill</span><span class="sxs-lookup"><span data-stu-id="127e7-1841">PinFill</span></span></td>
 </tr>
 <tr><td>![PinnedFill](images/segoe-mdl/e842.png)</td>
  <td><span data-ttu-id="127e7-1843">E842</span><span class="sxs-lookup"><span data-stu-id="127e7-1843">E842</span></span></td>
  <td><span data-ttu-id="127e7-1844">PinnedFill</span><span class="sxs-lookup"><span data-stu-id="127e7-1844">PinnedFill</span></span></td>
 </tr>
 <tr><td>![PeriodKey](images/segoe-mdl/e843.png)</td>
  <td><span data-ttu-id="127e7-1846">E843</span><span class="sxs-lookup"><span data-stu-id="127e7-1846">E843</span></span></td>
  <td><span data-ttu-id="127e7-1847">PeriodKey</span><span class="sxs-lookup"><span data-stu-id="127e7-1847">PeriodKey</span></span></td>
 </tr>
 <tr><td>![PuncKey](images/segoe-mdl/e844.png)</td>
  <td><span data-ttu-id="127e7-1849">E844</span><span class="sxs-lookup"><span data-stu-id="127e7-1849">E844</span></span></td>
  <td><span data-ttu-id="127e7-1850">PuncKey</span><span class="sxs-lookup"><span data-stu-id="127e7-1850">PuncKey</span></span></td>
 </tr>
 <tr><td>![RevToggleKey](images/segoe-mdl/e845.png)</td>
  <td><span data-ttu-id="127e7-1852">E845</span><span class="sxs-lookup"><span data-stu-id="127e7-1852">E845</span></span></td>
  <td><span data-ttu-id="127e7-1853">RevToggleKey</span><span class="sxs-lookup"><span data-stu-id="127e7-1853">RevToggleKey</span></span></td>
 </tr>
 <tr><td>![RightArrowKeyTime1](images/segoe-mdl/e846.png)</td>
  <td><span data-ttu-id="127e7-1855">E846</span><span class="sxs-lookup"><span data-stu-id="127e7-1855">E846</span></span></td>
  <td><span data-ttu-id="127e7-1856">RightArrowKeyTime1</span><span class="sxs-lookup"><span data-stu-id="127e7-1856">RightArrowKeyTime1</span></span></td>
 </tr>
 <tr><td>![RightArrowKeyTime2](images/segoe-mdl/e847.png)</td>
  <td><span data-ttu-id="127e7-1858">E847</span><span class="sxs-lookup"><span data-stu-id="127e7-1858">E847</span></span></td>
  <td><span data-ttu-id="127e7-1859">RightArrowKeyTime2</span><span class="sxs-lookup"><span data-stu-id="127e7-1859">RightArrowKeyTime2</span></span></td>
 </tr>
 <tr><td>![LeftQuote](images/segoe-mdl/e848.png)</td>
  <td><span data-ttu-id="127e7-1861">E848</span><span class="sxs-lookup"><span data-stu-id="127e7-1861">E848</span></span></td>
  <td><span data-ttu-id="127e7-1862">LeftQuote</span><span class="sxs-lookup"><span data-stu-id="127e7-1862">LeftQuote</span></span></td>
 </tr>
 <tr><td>![RightQuote](images/segoe-mdl/e849.png)</td>
  <td><span data-ttu-id="127e7-1864">E849</span><span class="sxs-lookup"><span data-stu-id="127e7-1864">E849</span></span></td>
  <td><span data-ttu-id="127e7-1865">RightQuote</span><span class="sxs-lookup"><span data-stu-id="127e7-1865">RightQuote</span></span></td>
 </tr>
 <tr><td>![DownShiftKey](images/segoe-mdl/e84a.png)</td>
  <td><span data-ttu-id="127e7-1867">E84A</span><span class="sxs-lookup"><span data-stu-id="127e7-1867">E84A</span></span></td>
  <td><span data-ttu-id="127e7-1868">DownShiftKey</span><span class="sxs-lookup"><span data-stu-id="127e7-1868">DownShiftKey</span></span></td>
 </tr>
 <tr><td>![UpShiftKey](images/segoe-mdl/e84b.png)</td>
  <td><span data-ttu-id="127e7-1870">E84B</span><span class="sxs-lookup"><span data-stu-id="127e7-1870">E84B</span></span></td>
  <td><span data-ttu-id="127e7-1871">UpShiftKey</span><span class="sxs-lookup"><span data-stu-id="127e7-1871">UpShiftKey</span></span></td>
 </tr>
 <tr><td>![PuncKey0](images/segoe-mdl/e84c.png)</td>
  <td><span data-ttu-id="127e7-1873">E84C</span><span class="sxs-lookup"><span data-stu-id="127e7-1873">E84C</span></span></td>
  <td><span data-ttu-id="127e7-1874">PuncKey0</span><span class="sxs-lookup"><span data-stu-id="127e7-1874">PuncKey0</span></span></td>
 </tr>
 <tr><td>![PuncKeyLeftBottom](images/segoe-mdl/e84d.png)</td>
  <td><span data-ttu-id="127e7-1876">E84D</span><span class="sxs-lookup"><span data-stu-id="127e7-1876">E84D</span></span></td>
  <td><span data-ttu-id="127e7-1877">PuncKeyLeftBottom</span><span class="sxs-lookup"><span data-stu-id="127e7-1877">PuncKeyLeftBottom</span></span></td>
 </tr>
 <tr><td>![RightArrowKeyTime3](images/segoe-mdl/e84e.png)</td>
  <td><span data-ttu-id="127e7-1879">E84E</span><span class="sxs-lookup"><span data-stu-id="127e7-1879">E84E</span></span></td>
  <td><span data-ttu-id="127e7-1880">RightArrowKeyTime3</span><span class="sxs-lookup"><span data-stu-id="127e7-1880">RightArrowKeyTime3</span></span></td>
 </tr>
 <tr><td>![RightArrowKeyTime4](images/segoe-mdl/e84f.png)</td>
  <td><span data-ttu-id="127e7-1882">E84F</span><span class="sxs-lookup"><span data-stu-id="127e7-1882">E84F</span></span></td>
  <td><span data-ttu-id="127e7-1883">RightArrowKeyTime4</span><span class="sxs-lookup"><span data-stu-id="127e7-1883">RightArrowKeyTime4</span></span></td>
 </tr>
 <tr><td>![Battery0](images/segoe-mdl/e850.png)</td>
  <td><span data-ttu-id="127e7-1885">E850</span><span class="sxs-lookup"><span data-stu-id="127e7-1885">E850</span></span></td>
  <td><span data-ttu-id="127e7-1886">Battery0</span><span class="sxs-lookup"><span data-stu-id="127e7-1886">Battery0</span></span></td>
 </tr>
 <tr><td>![Battery1](images/segoe-mdl/e851.png)</td>
  <td><span data-ttu-id="127e7-1888">E851</span><span class="sxs-lookup"><span data-stu-id="127e7-1888">E851</span></span></td>
  <td><span data-ttu-id="127e7-1889">Battery1</span><span class="sxs-lookup"><span data-stu-id="127e7-1889">Battery1</span></span></td>
 </tr>
 <tr><td>![Battery2](images/segoe-mdl/e852.png)</td>
  <td><span data-ttu-id="127e7-1891">E852</span><span class="sxs-lookup"><span data-stu-id="127e7-1891">E852</span></span></td>
  <td><span data-ttu-id="127e7-1892">Battery2</span><span class="sxs-lookup"><span data-stu-id="127e7-1892">Battery2</span></span></td>
 </tr>
 <tr><td>![Battery3](images/segoe-mdl/e853.png)</td>
  <td><span data-ttu-id="127e7-1894">E853</span><span class="sxs-lookup"><span data-stu-id="127e7-1894">E853</span></span></td>
  <td><span data-ttu-id="127e7-1895">Battery3</span><span class="sxs-lookup"><span data-stu-id="127e7-1895">Battery3</span></span></td>
 </tr>
 <tr><td>![Battery4](images/segoe-mdl/e854.png)</td>
  <td><span data-ttu-id="127e7-1897">E854</span><span class="sxs-lookup"><span data-stu-id="127e7-1897">E854</span></span></td>
  <td><span data-ttu-id="127e7-1898">Battery4</span><span class="sxs-lookup"><span data-stu-id="127e7-1898">Battery4</span></span></td>
 </tr>
 <tr><td>![Battery5](images/segoe-mdl/e855.png)</td>
  <td><span data-ttu-id="127e7-1900">E855</span><span class="sxs-lookup"><span data-stu-id="127e7-1900">E855</span></span></td>
  <td><span data-ttu-id="127e7-1901">Battery5</span><span class="sxs-lookup"><span data-stu-id="127e7-1901">Battery5</span></span></td>
 </tr>
 <tr><td>![Battery6](images/segoe-mdl/e856.png)</td>
  <td><span data-ttu-id="127e7-1903">E856</span><span class="sxs-lookup"><span data-stu-id="127e7-1903">E856</span></span></td>
  <td><span data-ttu-id="127e7-1904">Battery6</span><span class="sxs-lookup"><span data-stu-id="127e7-1904">Battery6</span></span></td>
 </tr>
 <tr><td>![Battery7](images/segoe-mdl/e857.png)</td>
  <td><span data-ttu-id="127e7-1906">E857</span><span class="sxs-lookup"><span data-stu-id="127e7-1906">E857</span></span></td>
  <td><span data-ttu-id="127e7-1907">Battery7</span><span class="sxs-lookup"><span data-stu-id="127e7-1907">Battery7</span></span></td>
 </tr>
 <tr><td>![Battery8](images/segoe-mdl/e858.png)</td>
  <td><span data-ttu-id="127e7-1909">E858</span><span class="sxs-lookup"><span data-stu-id="127e7-1909">E858</span></span></td>
  <td><span data-ttu-id="127e7-1910">Battery8</span><span class="sxs-lookup"><span data-stu-id="127e7-1910">Battery8</span></span></td>
 </tr>
 <tr><td>![Battery9](images/segoe-mdl/e859.png)</td>
  <td><span data-ttu-id="127e7-1912">E859</span><span class="sxs-lookup"><span data-stu-id="127e7-1912">E859</span></span></td>
  <td><span data-ttu-id="127e7-1913">Battery9</span><span class="sxs-lookup"><span data-stu-id="127e7-1913">Battery9</span></span></td>
 </tr>
 <tr><td>![BatteryCharging0](images/segoe-mdl/e85a.png)</td>
  <td><span data-ttu-id="127e7-1915">E85A</span><span class="sxs-lookup"><span data-stu-id="127e7-1915">E85A</span></span></td>
  <td><span data-ttu-id="127e7-1916">BatteryCharging0</span><span class="sxs-lookup"><span data-stu-id="127e7-1916">BatteryCharging0</span></span></td>
 </tr>
 <tr><td>![BatteryCharging1](images/segoe-mdl/e85b.png)</td>
  <td><span data-ttu-id="127e7-1918">E85B</span><span class="sxs-lookup"><span data-stu-id="127e7-1918">E85B</span></span></td>
  <td><span data-ttu-id="127e7-1919">BatteryCharging1</span><span class="sxs-lookup"><span data-stu-id="127e7-1919">BatteryCharging1</span></span></td>
 </tr>
 <tr><td>![BatteryCharging2](images/segoe-mdl/e85c.png)</td>
  <td><span data-ttu-id="127e7-1921">E85C</span><span class="sxs-lookup"><span data-stu-id="127e7-1921">E85C</span></span></td>
  <td><span data-ttu-id="127e7-1922">BatteryCharging2</span><span class="sxs-lookup"><span data-stu-id="127e7-1922">BatteryCharging2</span></span></td>
 </tr>
 <tr><td>![BatteryCharging3](images/segoe-mdl/e85d.png)</td>
  <td><span data-ttu-id="127e7-1924">E85D</span><span class="sxs-lookup"><span data-stu-id="127e7-1924">E85D</span></span></td>
  <td><span data-ttu-id="127e7-1925">BatteryCharging3</span><span class="sxs-lookup"><span data-stu-id="127e7-1925">BatteryCharging3</span></span></td>
 </tr>
 <tr><td>![BatteryCharging4](images/segoe-mdl/e85e.png)</td>
  <td><span data-ttu-id="127e7-1927">E85E</span><span class="sxs-lookup"><span data-stu-id="127e7-1927">E85E</span></span></td>
  <td><span data-ttu-id="127e7-1928">BatteryCharging4</span><span class="sxs-lookup"><span data-stu-id="127e7-1928">BatteryCharging4</span></span></td>
 </tr>
 <tr><td>![BatteryCharging5](images/segoe-mdl/e85f.png)</td>
  <td><span data-ttu-id="127e7-1930">E85F</span><span class="sxs-lookup"><span data-stu-id="127e7-1930">E85F</span></span></td>
  <td><span data-ttu-id="127e7-1931">BatteryCharging5</span><span class="sxs-lookup"><span data-stu-id="127e7-1931">BatteryCharging5</span></span></td>
 </tr>
 <tr><td>![BatteryCharging6](images/segoe-mdl/e860.png)</td>
  <td><span data-ttu-id="127e7-1933">E860</span><span class="sxs-lookup"><span data-stu-id="127e7-1933">E860</span></span></td>
  <td><span data-ttu-id="127e7-1934">BatteryCharging6</span><span class="sxs-lookup"><span data-stu-id="127e7-1934">BatteryCharging6</span></span></td>
 </tr>
 <tr><td>![BatteryCharging7](images/segoe-mdl/e861.png)</td>
  <td><span data-ttu-id="127e7-1936">E861</span><span class="sxs-lookup"><span data-stu-id="127e7-1936">E861</span></span></td>
  <td><span data-ttu-id="127e7-1937">BatteryCharging7</span><span class="sxs-lookup"><span data-stu-id="127e7-1937">BatteryCharging7</span></span></td>
 </tr>
 <tr><td>![BatteryCharging8](images/segoe-mdl/e862.png)</td>
  <td><span data-ttu-id="127e7-1939">E862</span><span class="sxs-lookup"><span data-stu-id="127e7-1939">E862</span></span></td>
  <td><span data-ttu-id="127e7-1940">BatteryCharging8</span><span class="sxs-lookup"><span data-stu-id="127e7-1940">BatteryCharging8</span></span></td>
 </tr>
 <tr><td>![BatterySaver0](images/segoe-mdl/e863.png)</td>
  <td><span data-ttu-id="127e7-1942">E863</span><span class="sxs-lookup"><span data-stu-id="127e7-1942">E863</span></span></td>
  <td><span data-ttu-id="127e7-1943">BatterySaver0</span><span class="sxs-lookup"><span data-stu-id="127e7-1943">BatterySaver0</span></span></td>
 </tr>
 <tr><td>![BatterySaver1](images/segoe-mdl/e864.png)</td>
  <td><span data-ttu-id="127e7-1945">E864</span><span class="sxs-lookup"><span data-stu-id="127e7-1945">E864</span></span></td>
  <td><span data-ttu-id="127e7-1946">BatterySaver1</span><span class="sxs-lookup"><span data-stu-id="127e7-1946">BatterySaver1</span></span></td>
 </tr>
 <tr><td>![BatterySaver2](images/segoe-mdl/e865.png)</td>
  <td><span data-ttu-id="127e7-1948">E865</span><span class="sxs-lookup"><span data-stu-id="127e7-1948">E865</span></span></td>
  <td><span data-ttu-id="127e7-1949">BatterySaver2</span><span class="sxs-lookup"><span data-stu-id="127e7-1949">BatterySaver2</span></span></td>
 </tr>
 <tr><td>![BatterySaver3](images/segoe-mdl/e866.png)</td>
  <td><span data-ttu-id="127e7-1951">E866</span><span class="sxs-lookup"><span data-stu-id="127e7-1951">E866</span></span></td>
  <td><span data-ttu-id="127e7-1952">BatterySaver3</span><span class="sxs-lookup"><span data-stu-id="127e7-1952">BatterySaver3</span></span></td>
 </tr>
 <tr><td>![BatterySaver4](images/segoe-mdl/e867.png)</td>
  <td><span data-ttu-id="127e7-1954">E867</span><span class="sxs-lookup"><span data-stu-id="127e7-1954">E867</span></span></td>
  <td><span data-ttu-id="127e7-1955">BatterySaver4</span><span class="sxs-lookup"><span data-stu-id="127e7-1955">BatterySaver4</span></span></td>
 </tr>
 <tr><td>![BatterySaver5](images/segoe-mdl/e868.png)</td>
  <td><span data-ttu-id="127e7-1957">E868</span><span class="sxs-lookup"><span data-stu-id="127e7-1957">E868</span></span></td>
  <td><span data-ttu-id="127e7-1958">BatterySaver5</span><span class="sxs-lookup"><span data-stu-id="127e7-1958">BatterySaver5</span></span></td>
 </tr>
 <tr><td>![BatterySaver6](images/segoe-mdl/e869.png)</td>
  <td><span data-ttu-id="127e7-1960">E869</span><span class="sxs-lookup"><span data-stu-id="127e7-1960">E869</span></span></td>
  <td><span data-ttu-id="127e7-1961">BatterySaver6</span><span class="sxs-lookup"><span data-stu-id="127e7-1961">BatterySaver6</span></span></td>
 </tr>
 <tr><td>![BatterySaver7](images/segoe-mdl/e86a.png)</td>
  <td><span data-ttu-id="127e7-1963">E86A</span><span class="sxs-lookup"><span data-stu-id="127e7-1963">E86A</span></span></td>
  <td><span data-ttu-id="127e7-1964">BatterySaver7</span><span class="sxs-lookup"><span data-stu-id="127e7-1964">BatterySaver7</span></span></td>
 </tr>
 <tr><td>![BatterySaver8](images/segoe-mdl/e86b.png)</td>
  <td><span data-ttu-id="127e7-1966">E86B</span><span class="sxs-lookup"><span data-stu-id="127e7-1966">E86B</span></span></td>
  <td><span data-ttu-id="127e7-1967">BatterySaver8</span><span class="sxs-lookup"><span data-stu-id="127e7-1967">BatterySaver8</span></span></td>
 </tr>
 <tr><td>![SignalBars1](images/segoe-mdl/e86c.png)</td>
  <td><span data-ttu-id="127e7-1969">E86C</span><span class="sxs-lookup"><span data-stu-id="127e7-1969">E86C</span></span></td>
  <td><span data-ttu-id="127e7-1970">SignalBars1</span><span class="sxs-lookup"><span data-stu-id="127e7-1970">SignalBars1</span></span></td>
 </tr>
 <tr><td>![SignalBars2](images/segoe-mdl/e86d.png)</td>
  <td><span data-ttu-id="127e7-1972">E86D</span><span class="sxs-lookup"><span data-stu-id="127e7-1972">E86D</span></span></td>
  <td><span data-ttu-id="127e7-1973">SignalBars2</span><span class="sxs-lookup"><span data-stu-id="127e7-1973">SignalBars2</span></span></td>
 </tr>
 <tr><td>![SignalBars3](images/segoe-mdl/e86e.png)</td>
  <td><span data-ttu-id="127e7-1975">E86E</span><span class="sxs-lookup"><span data-stu-id="127e7-1975">E86E</span></span></td>
  <td><span data-ttu-id="127e7-1976">SignalBars3</span><span class="sxs-lookup"><span data-stu-id="127e7-1976">SignalBars3</span></span></td>
 </tr>
 <tr><td>![SignalBars4](images/segoe-mdl/e86f.png)</td>
  <td><span data-ttu-id="127e7-1978">E86F</span><span class="sxs-lookup"><span data-stu-id="127e7-1978">E86F</span></span></td>
  <td><span data-ttu-id="127e7-1979">SignalBars4</span><span class="sxs-lookup"><span data-stu-id="127e7-1979">SignalBars4</span></span></td>
 </tr>
 <tr><td>![SignalBars5](images/segoe-mdl/e870.png)</td>
  <td><span data-ttu-id="127e7-1981">E870</span><span class="sxs-lookup"><span data-stu-id="127e7-1981">E870</span></span></td>
  <td><span data-ttu-id="127e7-1982">SignalBars5</span><span class="sxs-lookup"><span data-stu-id="127e7-1982">SignalBars5</span></span></td>
 </tr>
 <tr><td>![SignalNotConnected](images/segoe-mdl/e871.png)</td>
  <td><span data-ttu-id="127e7-1984">E871</span><span class="sxs-lookup"><span data-stu-id="127e7-1984">E871</span></span></td>
  <td><span data-ttu-id="127e7-1985">SignalNotConnected</span><span class="sxs-lookup"><span data-stu-id="127e7-1985">SignalNotConnected</span></span></td>
 </tr>
 <tr><td>![Wifi1](images/segoe-mdl/e872.png)</td>
  <td><span data-ttu-id="127e7-1987">E872</span><span class="sxs-lookup"><span data-stu-id="127e7-1987">E872</span></span></td>
  <td><span data-ttu-id="127e7-1988">Wifi1</span><span class="sxs-lookup"><span data-stu-id="127e7-1988">Wifi1</span></span></td>
 </tr>
 <tr><td>![Wifi2](images/segoe-mdl/e873.png)</td>
  <td><span data-ttu-id="127e7-1990">E873</span><span class="sxs-lookup"><span data-stu-id="127e7-1990">E873</span></span></td>
  <td><span data-ttu-id="127e7-1991">Wifi2</span><span class="sxs-lookup"><span data-stu-id="127e7-1991">Wifi2</span></span></td>
 </tr>
 <tr><td>![Wifi3](images/segoe-mdl/e874.png)</td>
  <td><span data-ttu-id="127e7-1993">E874</span><span class="sxs-lookup"><span data-stu-id="127e7-1993">E874</span></span></td>
  <td><span data-ttu-id="127e7-1994">Wifi3</span><span class="sxs-lookup"><span data-stu-id="127e7-1994">Wifi3</span></span></td>
 </tr>
 <tr><td>![SIMLock](images/segoe-mdl/e875.png)</td>
  <td><span data-ttu-id="127e7-1996">E875</span><span class="sxs-lookup"><span data-stu-id="127e7-1996">E875</span></span></td>
  <td><span data-ttu-id="127e7-1997">SIMLock</span><span class="sxs-lookup"><span data-stu-id="127e7-1997">SIMLock</span></span></td>
 </tr>
 <tr><td>![SIMMissing](images/segoe-mdl/e876.png)</td>
  <td><span data-ttu-id="127e7-1999">E876</span><span class="sxs-lookup"><span data-stu-id="127e7-1999">E876</span></span></td>
  <td><span data-ttu-id="127e7-2000">SIMMissing</span><span class="sxs-lookup"><span data-stu-id="127e7-2000">SIMMissing</span></span></td>
 </tr>
 <tr><td>![Vibrate](images/segoe-mdl/e877.png)</td>
  <td><span data-ttu-id="127e7-2002">E877</span><span class="sxs-lookup"><span data-stu-id="127e7-2002">E877</span></span></td>
  <td><span data-ttu-id="127e7-2003">Vibrate</span><span class="sxs-lookup"><span data-stu-id="127e7-2003">Vibrate</span></span></td>
 </tr>
 <tr><td>![RoamingInternational](images/segoe-mdl/e878.png)</td>
  <td><span data-ttu-id="127e7-2005">E878</span><span class="sxs-lookup"><span data-stu-id="127e7-2005">E878</span></span></td>
  <td><span data-ttu-id="127e7-2006">RoamingInternational</span><span class="sxs-lookup"><span data-stu-id="127e7-2006">RoamingInternational</span></span></td>
 </tr>
 <tr><td>![RoamingDomestic](images/segoe-mdl/e879.png)</td>
  <td><span data-ttu-id="127e7-2008">E879</span><span class="sxs-lookup"><span data-stu-id="127e7-2008">E879</span></span></td>
  <td><span data-ttu-id="127e7-2009">RoamingDomestic</span><span class="sxs-lookup"><span data-stu-id="127e7-2009">RoamingDomestic</span></span></td>
 </tr>
 <tr><td>![CallForwardInternational](images/segoe-mdl/e87a.png)</td>
  <td><span data-ttu-id="127e7-2011">E87A</span><span class="sxs-lookup"><span data-stu-id="127e7-2011">E87A</span></span></td>
  <td><span data-ttu-id="127e7-2012">CallForwardInternational</span><span class="sxs-lookup"><span data-stu-id="127e7-2012">CallForwardInternational</span></span></td>
 </tr>
 <tr><td>![CallForwardRoaming](images/segoe-mdl/e87b.png)</td>
  <td><span data-ttu-id="127e7-2014">E87B</span><span class="sxs-lookup"><span data-stu-id="127e7-2014">E87B</span></span></td>
  <td><span data-ttu-id="127e7-2015">CallForwardRoaming</span><span class="sxs-lookup"><span data-stu-id="127e7-2015">CallForwardRoaming</span></span></td>
 </tr>
 <tr><td>![JpnRomanji](images/segoe-mdl/e87c.png)</td>
  <td><span data-ttu-id="127e7-2017">E87C</span><span class="sxs-lookup"><span data-stu-id="127e7-2017">E87C</span></span></td>
  <td><span data-ttu-id="127e7-2018">JpnRomanji</span><span class="sxs-lookup"><span data-stu-id="127e7-2018">JpnRomanji</span></span></td>
 </tr>
 <tr><td>![JpnRomanjiLock](images/segoe-mdl/e87d.png)</td>
  <td><span data-ttu-id="127e7-2020">E87D</span><span class="sxs-lookup"><span data-stu-id="127e7-2020">E87D</span></span></td>
  <td><span data-ttu-id="127e7-2021">JpnRomanjiLock</span><span class="sxs-lookup"><span data-stu-id="127e7-2021">JpnRomanjiLock</span></span></td>
 </tr>
 <tr><td>![JpnRomanjiShift](images/segoe-mdl/e87e.png)</td>
  <td><span data-ttu-id="127e7-2023">E87E</span><span class="sxs-lookup"><span data-stu-id="127e7-2023">E87E</span></span></td>
  <td><span data-ttu-id="127e7-2024">JpnRomanjiShift</span><span class="sxs-lookup"><span data-stu-id="127e7-2024">JpnRomanjiShift</span></span></td>
 </tr>
 <tr><td>![JpnRomanjiShiftLock](images/segoe-mdl/e87f.png)</td>
  <td><span data-ttu-id="127e7-2026">E87F</span><span class="sxs-lookup"><span data-stu-id="127e7-2026">E87F</span></span></td>
  <td><span data-ttu-id="127e7-2027">JpnRomanjiShiftLock</span><span class="sxs-lookup"><span data-stu-id="127e7-2027">JpnRomanjiShiftLock</span></span></td>
 </tr>
 <tr><td>![StatusDataTransfer](images/segoe-mdl/e880.png)</td>
  <td><span data-ttu-id="127e7-2029">E880</span><span class="sxs-lookup"><span data-stu-id="127e7-2029">E880</span></span></td>
  <td><span data-ttu-id="127e7-2030">StatusDataTransfer</span><span class="sxs-lookup"><span data-stu-id="127e7-2030">StatusDataTransfer</span></span></td>
 </tr>
 <tr><td>![StatusDataTransferVPN](images/segoe-mdl/e881.png)</td>
  <td><span data-ttu-id="127e7-2032">E881</span><span class="sxs-lookup"><span data-stu-id="127e7-2032">E881</span></span></td>
  <td><span data-ttu-id="127e7-2033">StatusDataTransferVPN</span><span class="sxs-lookup"><span data-stu-id="127e7-2033">StatusDataTransferVPN</span></span></td>
 </tr>
 <tr><td>![StatusDualSIM2](images/segoe-mdl/e882.png)</td>
  <td><span data-ttu-id="127e7-2035">E882</span><span class="sxs-lookup"><span data-stu-id="127e7-2035">E882</span></span></td>
  <td><span data-ttu-id="127e7-2036">StatusDualSIM2</span><span class="sxs-lookup"><span data-stu-id="127e7-2036">StatusDualSIM2</span></span></td>
 </tr>
 <tr><td>![StatusDualSIM2VPN](images/segoe-mdl/e883.png)</td>
  <td><span data-ttu-id="127e7-2038">E883</span><span class="sxs-lookup"><span data-stu-id="127e7-2038">E883</span></span></td>
  <td><span data-ttu-id="127e7-2039">StatusDualSIM2VPN</span><span class="sxs-lookup"><span data-stu-id="127e7-2039">StatusDualSIM2VPN</span></span></td>
 </tr>
 <tr><td>![StatusDualSIM1](images/segoe-mdl/e884.png)</td>
  <td><span data-ttu-id="127e7-2041">E884</span><span class="sxs-lookup"><span data-stu-id="127e7-2041">E884</span></span></td>
  <td><span data-ttu-id="127e7-2042">StatusDualSIM1</span><span class="sxs-lookup"><span data-stu-id="127e7-2042">StatusDualSIM1</span></span></td>
 </tr>
 <tr><td>![StatusDualSIM1VPN](images/segoe-mdl/e885.png)</td>
  <td><span data-ttu-id="127e7-2044">E885</span><span class="sxs-lookup"><span data-stu-id="127e7-2044">E885</span></span></td>
  <td><span data-ttu-id="127e7-2045">StatusDualSIM1VPN</span><span class="sxs-lookup"><span data-stu-id="127e7-2045">StatusDualSIM1VPN</span></span></td>
 </tr>
 <tr><td>![StatusSGLTE](images/segoe-mdl/e886.png)</td>
  <td><span data-ttu-id="127e7-2047">E886</span><span class="sxs-lookup"><span data-stu-id="127e7-2047">E886</span></span></td>
  <td><span data-ttu-id="127e7-2048">StatusSGLTE</span><span class="sxs-lookup"><span data-stu-id="127e7-2048">StatusSGLTE</span></span></td>
 </tr>
 <tr><td>![StatusSGLTECell](images/segoe-mdl/e887.png)</td>
  <td><span data-ttu-id="127e7-2050">E887</span><span class="sxs-lookup"><span data-stu-id="127e7-2050">E887</span></span></td>
  <td><span data-ttu-id="127e7-2051">StatusSGLTECell</span><span class="sxs-lookup"><span data-stu-id="127e7-2051">StatusSGLTECell</span></span></td>
 </tr>
 <tr><td>![StatusSGLTEDataVPN](images/segoe-mdl/e888.png)</td>
  <td><span data-ttu-id="127e7-2053">E888</span><span class="sxs-lookup"><span data-stu-id="127e7-2053">E888</span></span></td>
  <td><span data-ttu-id="127e7-2054">StatusSGLTEDataVPN</span><span class="sxs-lookup"><span data-stu-id="127e7-2054">StatusSGLTEDataVPN</span></span></td>
 </tr>
 <tr><td>![StatusVPN](images/segoe-mdl/e889.png)</td>
  <td><span data-ttu-id="127e7-2056">E889</span><span class="sxs-lookup"><span data-stu-id="127e7-2056">E889</span></span></td>
  <td><span data-ttu-id="127e7-2057">StatusVPN</span><span class="sxs-lookup"><span data-stu-id="127e7-2057">StatusVPN</span></span></td>
 </tr>
 <tr><td>![WifiHotspot](images/segoe-mdl/e88a.png)</td>
  <td><span data-ttu-id="127e7-2059">E88A</span><span class="sxs-lookup"><span data-stu-id="127e7-2059">E88A</span></span></td>
  <td><span data-ttu-id="127e7-2060">WifiHotspot</span><span class="sxs-lookup"><span data-stu-id="127e7-2060">WifiHotspot</span></span></td>
 </tr>
 <tr><td>![LanguageKor](images/segoe-mdl/e88b.png)</td>
  <td><span data-ttu-id="127e7-2062">E88B</span><span class="sxs-lookup"><span data-stu-id="127e7-2062">E88B</span></span></td>
  <td><span data-ttu-id="127e7-2063">LanguageKor</span><span class="sxs-lookup"><span data-stu-id="127e7-2063">LanguageKor</span></span></td>
 </tr>
 <tr><td>![LanguageCht](images/segoe-mdl/e88c.png)</td>
  <td><span data-ttu-id="127e7-2065">E88C</span><span class="sxs-lookup"><span data-stu-id="127e7-2065">E88C</span></span></td>
  <td><span data-ttu-id="127e7-2066">LanguageCht</span><span class="sxs-lookup"><span data-stu-id="127e7-2066">LanguageCht</span></span></td>
 </tr>
 <tr><td>![LanguageChs](images/segoe-mdl/e88d.png)</td>
  <td><span data-ttu-id="127e7-2068">E88D</span><span class="sxs-lookup"><span data-stu-id="127e7-2068">E88D</span></span></td>
  <td><span data-ttu-id="127e7-2069">LanguageChs</span><span class="sxs-lookup"><span data-stu-id="127e7-2069">LanguageChs</span></span></td>
 </tr>
 <tr><td>![USB](images/segoe-mdl/e88e.png)</td>
  <td><span data-ttu-id="127e7-2071">E88E</span><span class="sxs-lookup"><span data-stu-id="127e7-2071">E88E</span></span></td>
  <td><span data-ttu-id="127e7-2072">USB</span><span class="sxs-lookup"><span data-stu-id="127e7-2072">USB</span></span></td>
 </tr>
 <tr><td>![InkingToolFill](images/segoe-mdl/e88f.png)</td>
  <td><span data-ttu-id="127e7-2074">E88F</span><span class="sxs-lookup"><span data-stu-id="127e7-2074">E88F</span></span></td>
  <td><span data-ttu-id="127e7-2075">InkingToolFill</span><span class="sxs-lookup"><span data-stu-id="127e7-2075">InkingToolFill</span></span></td>
 </tr>
 <tr><td>![View](images/segoe-mdl/e890.png)</td>
  <td><span data-ttu-id="127e7-2077">E890</span><span class="sxs-lookup"><span data-stu-id="127e7-2077">E890</span></span></td>
  <td><span data-ttu-id="127e7-2078">View</span><span class="sxs-lookup"><span data-stu-id="127e7-2078">View</span></span></td>
 </tr>
 <tr><td>![HighlightFill](images/segoe-mdl/e891.png)</td>
  <td><span data-ttu-id="127e7-2080">E891</span><span class="sxs-lookup"><span data-stu-id="127e7-2080">E891</span></span></td>
  <td><span data-ttu-id="127e7-2081">HighlightFill</span><span class="sxs-lookup"><span data-stu-id="127e7-2081">HighlightFill</span></span></td>
 </tr>
 <tr><td>![Previous](images/segoe-mdl/e892.png)</td>
  <td><span data-ttu-id="127e7-2083">E892</span><span class="sxs-lookup"><span data-stu-id="127e7-2083">E892</span></span></td>
  <td><span data-ttu-id="127e7-2084">Previous</span><span class="sxs-lookup"><span data-stu-id="127e7-2084">Previous</span></span></td>
 </tr>
 <tr><td>![Next](images/segoe-mdl/e893.png)</td>
  <td><span data-ttu-id="127e7-2086">E893</span><span class="sxs-lookup"><span data-stu-id="127e7-2086">E893</span></span></td>
  <td><span data-ttu-id="127e7-2087">Next</span><span class="sxs-lookup"><span data-stu-id="127e7-2087">Next</span></span></td>
 </tr>
 <tr><td>![Clear](images/segoe-mdl/e894.png)</td>
  <td><span data-ttu-id="127e7-2089">E894</span><span class="sxs-lookup"><span data-stu-id="127e7-2089">E894</span></span></td>
  <td><span data-ttu-id="127e7-2090">Clear</span><span class="sxs-lookup"><span data-stu-id="127e7-2090">Clear</span></span></td>
 </tr>
 <tr><td>![Sync](images/segoe-mdl/e895.png)</td>
  <td><span data-ttu-id="127e7-2092">E895</span><span class="sxs-lookup"><span data-stu-id="127e7-2092">E895</span></span></td>
  <td><span data-ttu-id="127e7-2093">Sync</span><span class="sxs-lookup"><span data-stu-id="127e7-2093">Sync</span></span></td>
 </tr>
 <tr><td>![Download](images/segoe-mdl/e896.png)</td>
  <td><span data-ttu-id="127e7-2095">E896</span><span class="sxs-lookup"><span data-stu-id="127e7-2095">E896</span></span></td>
  <td><span data-ttu-id="127e7-2096">Download</span><span class="sxs-lookup"><span data-stu-id="127e7-2096">Download</span></span></td>
 </tr>
 <tr><td>![Help](images/segoe-mdl/e897.png)</td>
  <td><span data-ttu-id="127e7-2098">E897</span><span class="sxs-lookup"><span data-stu-id="127e7-2098">E897</span></span></td>
  <td><span data-ttu-id="127e7-2099">Help</span><span class="sxs-lookup"><span data-stu-id="127e7-2099">Help</span></span></td>
 </tr>
 <tr><td>![Upload](images/segoe-mdl/e898.png)</td>
  <td><span data-ttu-id="127e7-2101">E898</span><span class="sxs-lookup"><span data-stu-id="127e7-2101">E898</span></span></td>
  <td><span data-ttu-id="127e7-2102">Upload</span><span class="sxs-lookup"><span data-stu-id="127e7-2102">Upload</span></span></td>
 </tr>
 <tr><td>![Emoji](images/segoe-mdl/e899.png)</td>
  <td><span data-ttu-id="127e7-2104">E899</span><span class="sxs-lookup"><span data-stu-id="127e7-2104">E899</span></span></td>
  <td><span data-ttu-id="127e7-2105">Emoji</span><span class="sxs-lookup"><span data-stu-id="127e7-2105">Emoji</span></span></td>
 </tr>
 <tr><td>![TwoPage](images/segoe-mdl/e89a.png)</td>
  <td><span data-ttu-id="127e7-2107">E89A</span><span class="sxs-lookup"><span data-stu-id="127e7-2107">E89A</span></span></td>
  <td><span data-ttu-id="127e7-2108">TwoPage</span><span class="sxs-lookup"><span data-stu-id="127e7-2108">TwoPage</span></span></td>
 </tr>
 <tr><td>![LeaveChat](images/segoe-mdl/e89b.png)</td>
  <td><span data-ttu-id="127e7-2110">E89B</span><span class="sxs-lookup"><span data-stu-id="127e7-2110">E89B</span></span></td>
  <td><span data-ttu-id="127e7-2111">LeaveChat</span><span class="sxs-lookup"><span data-stu-id="127e7-2111">LeaveChat</span></span></td>
 </tr>
 <tr><td>![MailForward](images/segoe-mdl/e89c.png)</td>
  <td><span data-ttu-id="127e7-2113">E89C</span><span class="sxs-lookup"><span data-stu-id="127e7-2113">E89C</span></span></td>
  <td><span data-ttu-id="127e7-2114">MailForward</span><span class="sxs-lookup"><span data-stu-id="127e7-2114">MailForward</span></span></td>
 </tr>
 <tr><td>![RotateCamera](images/segoe-mdl/e89e.png)</td>
  <td><span data-ttu-id="127e7-2116">E89E</span><span class="sxs-lookup"><span data-stu-id="127e7-2116">E89E</span></span></td>
  <td><span data-ttu-id="127e7-2117">RotateCamera</span><span class="sxs-lookup"><span data-stu-id="127e7-2117">RotateCamera</span></span></td>
 </tr>
 <tr><td>![ClosePane](images/segoe-mdl/e89f.png)</td>
  <td><span data-ttu-id="127e7-2119">E89F</span><span class="sxs-lookup"><span data-stu-id="127e7-2119">E89F</span></span></td>
  <td><span data-ttu-id="127e7-2120">ClosePane</span><span class="sxs-lookup"><span data-stu-id="127e7-2120">ClosePane</span></span></td>
 </tr>
 <tr><td>![OpenPane](images/segoe-mdl/e8a0.png)</td>
  <td><span data-ttu-id="127e7-2122">E8A0</span><span class="sxs-lookup"><span data-stu-id="127e7-2122">E8A0</span></span></td>
  <td><span data-ttu-id="127e7-2123">OpenPane</span><span class="sxs-lookup"><span data-stu-id="127e7-2123">OpenPane</span></span></td>
 </tr>
 <tr><td>![PreviewLink](images/segoe-mdl/e8a1.png)</td>
  <td><span data-ttu-id="127e7-2125">E8A1</span><span class="sxs-lookup"><span data-stu-id="127e7-2125">E8A1</span></span></td>
  <td><span data-ttu-id="127e7-2126">PreviewLink</span><span class="sxs-lookup"><span data-stu-id="127e7-2126">PreviewLink</span></span></td>
 </tr>
 <tr><td>![AttachCamera](images/segoe-mdl/e8a2.png)</td>
  <td><span data-ttu-id="127e7-2128">E8A2</span><span class="sxs-lookup"><span data-stu-id="127e7-2128">E8A2</span></span></td>
  <td><span data-ttu-id="127e7-2129">AttachCamera</span><span class="sxs-lookup"><span data-stu-id="127e7-2129">AttachCamera</span></span></td>
 </tr>
 <tr><td>![ZoomIn](images/segoe-mdl/e8a3.png)</td>
  <td><span data-ttu-id="127e7-2131">E8A3</span><span class="sxs-lookup"><span data-stu-id="127e7-2131">E8A3</span></span></td>
  <td><span data-ttu-id="127e7-2132">ZoomIn</span><span class="sxs-lookup"><span data-stu-id="127e7-2132">ZoomIn</span></span></td>
 </tr>
 <tr><td>![Bookmarks](images/segoe-mdl/e8a4.png)</td>
  <td><span data-ttu-id="127e7-2134">E8A4</span><span class="sxs-lookup"><span data-stu-id="127e7-2134">E8A4</span></span></td>
  <td><span data-ttu-id="127e7-2135">Bookmarks</span><span class="sxs-lookup"><span data-stu-id="127e7-2135">Bookmarks</span></span></td>
 </tr>
 <tr><td>![Document](images/segoe-mdl/e8a5.png)</td>
  <td><span data-ttu-id="127e7-2137">E8A5</span><span class="sxs-lookup"><span data-stu-id="127e7-2137">E8A5</span></span></td>
  <td><span data-ttu-id="127e7-2138">Document</span><span class="sxs-lookup"><span data-stu-id="127e7-2138">Document</span></span></td>
 </tr>
 <tr><td>![ProtectedDocument](images/segoe-mdl/e8a6.png)</td>
  <td><span data-ttu-id="127e7-2140">E8A6</span><span class="sxs-lookup"><span data-stu-id="127e7-2140">E8A6</span></span></td>
  <td><span data-ttu-id="127e7-2141">ProtectedDocument</span><span class="sxs-lookup"><span data-stu-id="127e7-2141">ProtectedDocument</span></span></td>
 </tr>
 <tr><td>![OpenInNewWindow](images/segoe-mdl/e8a7.png)</td>
  <td><span data-ttu-id="127e7-2143">E8A7</span><span class="sxs-lookup"><span data-stu-id="127e7-2143">E8A7</span></span></td>
  <td><span data-ttu-id="127e7-2144">OpenInNewWindow</span><span class="sxs-lookup"><span data-stu-id="127e7-2144">OpenInNewWindow</span></span></td>
 </tr>
 <tr><td>![MailFill](images/segoe-mdl/e8a8.png)</td>
  <td><span data-ttu-id="127e7-2146">E8A8</span><span class="sxs-lookup"><span data-stu-id="127e7-2146">E8A8</span></span></td>
  <td><span data-ttu-id="127e7-2147">MailFill</span><span class="sxs-lookup"><span data-stu-id="127e7-2147">MailFill</span></span></td>
 </tr>
 <tr><td>![ViewAll](images/segoe-mdl/e8a9.png)</td>
  <td><span data-ttu-id="127e7-2149">E8A9</span><span class="sxs-lookup"><span data-stu-id="127e7-2149">E8A9</span></span></td>
  <td><span data-ttu-id="127e7-2150">ViewAll</span><span class="sxs-lookup"><span data-stu-id="127e7-2150">ViewAll</span></span></td>
 </tr>
 <tr><td>![VideoChat](images/segoe-mdl/e8aa.png)</td>
  <td><span data-ttu-id="127e7-2152">E8AA</span><span class="sxs-lookup"><span data-stu-id="127e7-2152">E8AA</span></span></td>
  <td><span data-ttu-id="127e7-2153">VideoChat</span><span class="sxs-lookup"><span data-stu-id="127e7-2153">VideoChat</span></span></td>
 </tr>
 <tr><td>![Switch](images/segoe-mdl/e8ab.png)</td>
  <td><span data-ttu-id="127e7-2155">E8AB</span><span class="sxs-lookup"><span data-stu-id="127e7-2155">E8AB</span></span></td>
  <td><span data-ttu-id="127e7-2156">Switch</span><span class="sxs-lookup"><span data-stu-id="127e7-2156">Switch</span></span></td>
 </tr>
 <tr><td>![Rename](images/segoe-mdl/e8ac.png)</td>
  <td><span data-ttu-id="127e7-2158">E8AC</span><span class="sxs-lookup"><span data-stu-id="127e7-2158">E8AC</span></span></td>
  <td><span data-ttu-id="127e7-2159">Rename</span><span class="sxs-lookup"><span data-stu-id="127e7-2159">Rename</span></span></td>
 </tr>
 <tr><td>![Go](images/segoe-mdl/e8ad.png)</td>
  <td><span data-ttu-id="127e7-2161">E8AD</span><span class="sxs-lookup"><span data-stu-id="127e7-2161">E8AD</span></span></td>
  <td><span data-ttu-id="127e7-2162">Go</span><span class="sxs-lookup"><span data-stu-id="127e7-2162">Go</span></span></td>
 </tr>
 <tr><td>![SurfaceHub](images/segoe-mdl/e8ae.png)</td>
  <td><span data-ttu-id="127e7-2164">E8AE</span><span class="sxs-lookup"><span data-stu-id="127e7-2164">E8AE</span></span></td>
  <td><span data-ttu-id="127e7-2165">SurfaceHub</span><span class="sxs-lookup"><span data-stu-id="127e7-2165">SurfaceHub</span></span></td>
 </tr>
 <tr><td>![Remote](images/segoe-mdl/e8af.png)</td>
  <td><span data-ttu-id="127e7-2167">E8AF</span><span class="sxs-lookup"><span data-stu-id="127e7-2167">E8AF</span></span></td>
  <td><span data-ttu-id="127e7-2168">Remote</span><span class="sxs-lookup"><span data-stu-id="127e7-2168">Remote</span></span></td>
 </tr>
 <tr><td>![Click](images/segoe-mdl/e8b0.png)</td>
  <td><span data-ttu-id="127e7-2170">E8B0</span><span class="sxs-lookup"><span data-stu-id="127e7-2170">E8B0</span></span></td>
  <td><span data-ttu-id="127e7-2171">Click</span><span class="sxs-lookup"><span data-stu-id="127e7-2171">Click</span></span></td>
 </tr>
 <tr><td>![Shuffle](images/segoe-mdl/e8b1.png)</td>
  <td><span data-ttu-id="127e7-2173">E8B1</span><span class="sxs-lookup"><span data-stu-id="127e7-2173">E8B1</span></span></td>
  <td><span data-ttu-id="127e7-2174">Shuffle</span><span class="sxs-lookup"><span data-stu-id="127e7-2174">Shuffle</span></span></td>
 </tr>
 <tr><td>![Movies](images/segoe-mdl/e8b2.png)</td>
  <td><span data-ttu-id="127e7-2176">E8B2</span><span class="sxs-lookup"><span data-stu-id="127e7-2176">E8B2</span></span></td>
  <td><span data-ttu-id="127e7-2177">Movies</span><span class="sxs-lookup"><span data-stu-id="127e7-2177">Movies</span></span></td>
 </tr>
 <tr><td>![SelectAll](images/segoe-mdl/e8b3.png)</td>
  <td><span data-ttu-id="127e7-2179">E8B3</span><span class="sxs-lookup"><span data-stu-id="127e7-2179">E8B3</span></span></td>
  <td><span data-ttu-id="127e7-2180">SelectAll</span><span class="sxs-lookup"><span data-stu-id="127e7-2180">SelectAll</span></span></td>
 </tr>
 <tr><td>![Orientation](images/segoe-mdl/e8b4.png)</td>
  <td><span data-ttu-id="127e7-2182">E8B4</span><span class="sxs-lookup"><span data-stu-id="127e7-2182">E8B4</span></span></td>
  <td><span data-ttu-id="127e7-2183">Orientation</span><span class="sxs-lookup"><span data-stu-id="127e7-2183">Orientation</span></span></td>
 </tr>
 <tr><td>![Import](images/segoe-mdl/e8b5.png)</td>
  <td><span data-ttu-id="127e7-2185">E8B5</span><span class="sxs-lookup"><span data-stu-id="127e7-2185">E8B5</span></span></td>
  <td><span data-ttu-id="127e7-2186">Import</span><span class="sxs-lookup"><span data-stu-id="127e7-2186">Import</span></span></td>
 </tr>
 <tr><td>![ImportAll](images/segoe-mdl/e8b6.png)</td>
  <td><span data-ttu-id="127e7-2188">E8B6</span><span class="sxs-lookup"><span data-stu-id="127e7-2188">E8B6</span></span></td>
  <td><span data-ttu-id="127e7-2189">ImportAll</span><span class="sxs-lookup"><span data-stu-id="127e7-2189">ImportAll</span></span></td>
 </tr>
 <tr><td>![Folder](images/segoe-mdl/e8b7.png)</td>
  <td><span data-ttu-id="127e7-2191">E8B7</span><span class="sxs-lookup"><span data-stu-id="127e7-2191">E8B7</span></span></td>
  <td><span data-ttu-id="127e7-2192">Folder</span><span class="sxs-lookup"><span data-stu-id="127e7-2192">Folder</span></span></td>
 </tr>
 <tr><td>![Webcam](images/segoe-mdl/e8b8.png)</td>
  <td><span data-ttu-id="127e7-2194">E8B8</span><span class="sxs-lookup"><span data-stu-id="127e7-2194">E8B8</span></span></td>
  <td><span data-ttu-id="127e7-2195">Webcam</span><span class="sxs-lookup"><span data-stu-id="127e7-2195">Webcam</span></span></td>
 </tr>
 <tr><td>![Picture](images/segoe-mdl/e8b9.png)</td>
  <td><span data-ttu-id="127e7-2197">E8B9</span><span class="sxs-lookup"><span data-stu-id="127e7-2197">E8B9</span></span></td>
  <td><span data-ttu-id="127e7-2198">Picture</span><span class="sxs-lookup"><span data-stu-id="127e7-2198">Picture</span></span></td>
 </tr>
 <tr><td>![Caption](images/segoe-mdl/e8ba.png)</td>
  <td><span data-ttu-id="127e7-2200">E8BA</span><span class="sxs-lookup"><span data-stu-id="127e7-2200">E8BA</span></span></td>
  <td><span data-ttu-id="127e7-2201">Caption</span><span class="sxs-lookup"><span data-stu-id="127e7-2201">Caption</span></span></td>
 </tr>
 <tr><td>![ChromeClose](images/segoe-mdl/e8bb.png)</td>
  <td><span data-ttu-id="127e7-2203">E8BB</span><span class="sxs-lookup"><span data-stu-id="127e7-2203">E8BB</span></span></td>
  <td><span data-ttu-id="127e7-2204">ChromeClose</span><span class="sxs-lookup"><span data-stu-id="127e7-2204">ChromeClose</span></span></td>
 </tr>
 <tr><td>![ShowResults](images/segoe-mdl/e8bc.png)</td>
  <td><span data-ttu-id="127e7-2206">E8BC</span><span class="sxs-lookup"><span data-stu-id="127e7-2206">E8BC</span></span></td>
  <td><span data-ttu-id="127e7-2207">ShowResults</span><span class="sxs-lookup"><span data-stu-id="127e7-2207">ShowResults</span></span></td>
 </tr>
 <tr><td>![Message](images/segoe-mdl/e8bd.png)</td>
  <td><span data-ttu-id="127e7-2209">E8BD</span><span class="sxs-lookup"><span data-stu-id="127e7-2209">E8BD</span></span></td>
  <td><span data-ttu-id="127e7-2210">Message</span><span class="sxs-lookup"><span data-stu-id="127e7-2210">Message</span></span></td>
 </tr>
 <tr><td>![Leaf](images/segoe-mdl/e8be.png)</td>
  <td><span data-ttu-id="127e7-2212">E8BE</span><span class="sxs-lookup"><span data-stu-id="127e7-2212">E8BE</span></span></td>
  <td><span data-ttu-id="127e7-2213">Leaf</span><span class="sxs-lookup"><span data-stu-id="127e7-2213">Leaf</span></span></td>
 </tr>
 <tr><td>![CalendarDay](images/segoe-mdl/e8bf.png)</td>
  <td><span data-ttu-id="127e7-2215">E8BF</span><span class="sxs-lookup"><span data-stu-id="127e7-2215">E8BF</span></span></td>
  <td><span data-ttu-id="127e7-2216">CalendarDay</span><span class="sxs-lookup"><span data-stu-id="127e7-2216">CalendarDay</span></span></td>
 </tr>
 <tr><td>![CalendarWeek](images/segoe-mdl/e8c0.png)</td>
  <td><span data-ttu-id="127e7-2218">E8C0</span><span class="sxs-lookup"><span data-stu-id="127e7-2218">E8C0</span></span></td>
  <td><span data-ttu-id="127e7-2219">CalendarWeek</span><span class="sxs-lookup"><span data-stu-id="127e7-2219">CalendarWeek</span></span></td>
 </tr>
 <tr><td>![Characters](images/segoe-mdl/e8c1.png)</td>
  <td><span data-ttu-id="127e7-2221">E8C1</span><span class="sxs-lookup"><span data-stu-id="127e7-2221">E8C1</span></span></td>
  <td><span data-ttu-id="127e7-2222">Characters</span><span class="sxs-lookup"><span data-stu-id="127e7-2222">Characters</span></span></td>
 </tr>
 <tr><td>![MailReplyAll](images/segoe-mdl/e8c2.png)</td>
  <td><span data-ttu-id="127e7-2224">E8C2</span><span class="sxs-lookup"><span data-stu-id="127e7-2224">E8C2</span></span></td>
  <td><span data-ttu-id="127e7-2225">MailReplyAll</span><span class="sxs-lookup"><span data-stu-id="127e7-2225">MailReplyAll</span></span></td>
 </tr>
 <tr><td>![Read](images/segoe-mdl/e8c3.png)</td>
  <td><span data-ttu-id="127e7-2227">E8C3</span><span class="sxs-lookup"><span data-stu-id="127e7-2227">E8C3</span></span></td>
  <td><span data-ttu-id="127e7-2228">Read</span><span class="sxs-lookup"><span data-stu-id="127e7-2228">Read</span></span></td>
 </tr>
 <tr><td>![ShowBcc](images/segoe-mdl/e8c4.png)</td>
  <td><span data-ttu-id="127e7-2230">E8C4</span><span class="sxs-lookup"><span data-stu-id="127e7-2230">E8C4</span></span></td>
  <td><span data-ttu-id="127e7-2231">ShowBcc</span><span class="sxs-lookup"><span data-stu-id="127e7-2231">ShowBcc</span></span></td>
 </tr>
 <tr><td>![HideBcc](images/segoe-mdl/e8c5.png)</td>
  <td><span data-ttu-id="127e7-2233">E8C5</span><span class="sxs-lookup"><span data-stu-id="127e7-2233">E8C5</span></span></td>
  <td><span data-ttu-id="127e7-2234">HideBcc</span><span class="sxs-lookup"><span data-stu-id="127e7-2234">HideBcc</span></span></td>
 </tr>
 <tr><td>![Cut](images/segoe-mdl/e8c6.png)</td>
  <td><span data-ttu-id="127e7-2236">E8C6</span><span class="sxs-lookup"><span data-stu-id="127e7-2236">E8C6</span></span></td>
  <td><span data-ttu-id="127e7-2237">Cut</span><span class="sxs-lookup"><span data-stu-id="127e7-2237">Cut</span></span></td>
 </tr>
 <tr><td>![Copy](images/segoe-mdl/e8c8.png)</td>
  <td><span data-ttu-id="127e7-2239">E8C8</span><span class="sxs-lookup"><span data-stu-id="127e7-2239">E8C8</span></span></td>
  <td><span data-ttu-id="127e7-2240">Copy</span><span class="sxs-lookup"><span data-stu-id="127e7-2240">Copy</span></span></td>
 </tr>
 <tr><td>![Important](images/segoe-mdl/e8c9.png)</td>
  <td><span data-ttu-id="127e7-2242">E8C9</span><span class="sxs-lookup"><span data-stu-id="127e7-2242">E8C9</span></span></td>
  <td><span data-ttu-id="127e7-2243">Important</span><span class="sxs-lookup"><span data-stu-id="127e7-2243">Important</span></span></td>
 </tr>
 <tr><td>![MailReply](images/segoe-mdl/e8ca.png)</td>
  <td><span data-ttu-id="127e7-2245">E8CA</span><span class="sxs-lookup"><span data-stu-id="127e7-2245">E8CA</span></span></td>
  <td><span data-ttu-id="127e7-2246">MailReply</span><span class="sxs-lookup"><span data-stu-id="127e7-2246">MailReply</span></span></td>
 </tr>
 <tr><td>![Sort](images/segoe-mdl/e8cb.png)</td>
  <td><span data-ttu-id="127e7-2248">E8CB</span><span class="sxs-lookup"><span data-stu-id="127e7-2248">E8CB</span></span></td>
  <td><span data-ttu-id="127e7-2249">Sort</span><span class="sxs-lookup"><span data-stu-id="127e7-2249">Sort</span></span></td>
 </tr>
 <tr><td>![MobileTablet](images/segoe-mdl/e8cc.png)</td>
  <td><span data-ttu-id="127e7-2251">E8CC</span><span class="sxs-lookup"><span data-stu-id="127e7-2251">E8CC</span></span></td>
  <td><span data-ttu-id="127e7-2252">MobileTablet</span><span class="sxs-lookup"><span data-stu-id="127e7-2252">MobileTablet</span></span></td>
 </tr>
 <tr><td>![DisconnectDrive](images/segoe-mdl/e8cd.png)</td>
  <td><span data-ttu-id="127e7-2254">E8CD</span><span class="sxs-lookup"><span data-stu-id="127e7-2254">E8CD</span></span></td>
  <td><span data-ttu-id="127e7-2255">DisconnectDrive</span><span class="sxs-lookup"><span data-stu-id="127e7-2255">DisconnectDrive</span></span></td>
 </tr>
 <tr><td>![MapDrive](images/segoe-mdl/e8ce.png)</td>
  <td><span data-ttu-id="127e7-2257">E8CE</span><span class="sxs-lookup"><span data-stu-id="127e7-2257">E8CE</span></span></td>
  <td><span data-ttu-id="127e7-2258">MapDrive</span><span class="sxs-lookup"><span data-stu-id="127e7-2258">MapDrive</span></span></td>
 </tr>
 <tr><td>![ContactPresence](images/segoe-mdl/e8cf.png)</td>
  <td><span data-ttu-id="127e7-2260">E8CF</span><span class="sxs-lookup"><span data-stu-id="127e7-2260">E8CF</span></span></td>
  <td><span data-ttu-id="127e7-2261">ContactPresence</span><span class="sxs-lookup"><span data-stu-id="127e7-2261">ContactPresence</span></span></td>
 </tr>
 <tr><td>![Priority](images/segoe-mdl/e8d0.png)</td>
  <td><span data-ttu-id="127e7-2263">E8D0</span><span class="sxs-lookup"><span data-stu-id="127e7-2263">E8D0</span></span></td>
  <td><span data-ttu-id="127e7-2264">Priority</span><span class="sxs-lookup"><span data-stu-id="127e7-2264">Priority</span></span></td>
 </tr>
 <tr><td>![GoToToday](images/segoe-mdl/e8d1.png)</td>
  <td><span data-ttu-id="127e7-2266">E8D1</span><span class="sxs-lookup"><span data-stu-id="127e7-2266">E8D1</span></span></td>
  <td><span data-ttu-id="127e7-2267">GoToToday</span><span class="sxs-lookup"><span data-stu-id="127e7-2267">GotoToday</span></span></td>
 </tr>
 <tr><td>![Font](images/segoe-mdl/e8d2.png)</td>
  <td><span data-ttu-id="127e7-2269">E8D2</span><span class="sxs-lookup"><span data-stu-id="127e7-2269">E8D2</span></span></td>
  <td><span data-ttu-id="127e7-2270">Font</span><span class="sxs-lookup"><span data-stu-id="127e7-2270">Font</span></span></td>
 </tr>
 <tr><td>![FontColor](images/segoe-mdl/e8d3.png)</td>
  <td><span data-ttu-id="127e7-2272">E8D3</span><span class="sxs-lookup"><span data-stu-id="127e7-2272">E8D3</span></span></td>
  <td><span data-ttu-id="127e7-2273">FontColor</span><span class="sxs-lookup"><span data-stu-id="127e7-2273">FontColor</span></span></td>
 </tr>
 <tr><td>![Contact2](images/segoe-mdl/e8d4.png)</td>
  <td><span data-ttu-id="127e7-2275">E8D4</span><span class="sxs-lookup"><span data-stu-id="127e7-2275">E8D4</span></span></td>
  <td><span data-ttu-id="127e7-2276">Contact2</span><span class="sxs-lookup"><span data-stu-id="127e7-2276">Contact2</span></span></td>
 </tr>
 <tr><td>![FolderFill](images/segoe-mdl/e8d5.png)</td>
  <td><span data-ttu-id="127e7-2278">E8D5</span><span class="sxs-lookup"><span data-stu-id="127e7-2278">E8D5</span></span></td>
  <td><span data-ttu-id="127e7-2279">FolderFill</span><span class="sxs-lookup"><span data-stu-id="127e7-2279">FolderFill</span></span></td>
 </tr>
 <tr><td>![Audio](images/segoe-mdl/e8d6.png)</td>
  <td><span data-ttu-id="127e7-2281">E8D6</span><span class="sxs-lookup"><span data-stu-id="127e7-2281">E8D6</span></span></td>
  <td><span data-ttu-id="127e7-2282">Audio</span><span class="sxs-lookup"><span data-stu-id="127e7-2282">Audio</span></span></td>
 </tr>
 <tr><td>![Permissions](images/segoe-mdl/e8d7.png)</td>
  <td><span data-ttu-id="127e7-2284">E8D7</span><span class="sxs-lookup"><span data-stu-id="127e7-2284">E8D7</span></span></td>
  <td><span data-ttu-id="127e7-2285">Permissions</span><span class="sxs-lookup"><span data-stu-id="127e7-2285">Permissions</span></span></td>
 </tr>
 <tr><td>![DisableUpdates](images/segoe-mdl/e8d8.png)</td>
  <td><span data-ttu-id="127e7-2287">E8D8</span><span class="sxs-lookup"><span data-stu-id="127e7-2287">E8D8</span></span></td>
  <td><span data-ttu-id="127e7-2288">DisableUpdates</span><span class="sxs-lookup"><span data-stu-id="127e7-2288">DisableUpdates</span></span></td>
 </tr>
 <tr><td>![Unfavorite](images/segoe-mdl/e8d9.png)</td>
  <td><span data-ttu-id="127e7-2290">E8D9</span><span class="sxs-lookup"><span data-stu-id="127e7-2290">E8D9</span></span></td>
  <td><span data-ttu-id="127e7-2291">Unfavorite</span><span class="sxs-lookup"><span data-stu-id="127e7-2291">Unfavorite</span></span></td>
 </tr>
 <tr><td>![OpenLocal](images/segoe-mdl/e8da.png)</td>
  <td><span data-ttu-id="127e7-2293">E8DA</span><span class="sxs-lookup"><span data-stu-id="127e7-2293">E8DA</span></span></td>
  <td><span data-ttu-id="127e7-2294">OpenLocal</span><span class="sxs-lookup"><span data-stu-id="127e7-2294">OpenLocal</span></span></td>
 </tr>
 <tr><td>![Italic](images/segoe-mdl/e8db.png)</td>
  <td><span data-ttu-id="127e7-2296">E8DB</span><span class="sxs-lookup"><span data-stu-id="127e7-2296">E8DB</span></span></td>
  <td><span data-ttu-id="127e7-2297">Italic</span><span class="sxs-lookup"><span data-stu-id="127e7-2297">Italic</span></span></td>
 </tr>
 <tr><td>![Underline](images/segoe-mdl/e8dc.png)</td>
  <td><span data-ttu-id="127e7-2299">E8DC</span><span class="sxs-lookup"><span data-stu-id="127e7-2299">E8DC</span></span></td>
  <td><span data-ttu-id="127e7-2300">Underline</span><span class="sxs-lookup"><span data-stu-id="127e7-2300">Underline</span></span></td>
 </tr>
 <tr><td>![Bold](images/segoe-mdl/e8dd.png)</td>
  <td><span data-ttu-id="127e7-2302">E8DD</span><span class="sxs-lookup"><span data-stu-id="127e7-2302">E8DD</span></span></td>
  <td><span data-ttu-id="127e7-2303">Bold</span><span class="sxs-lookup"><span data-stu-id="127e7-2303">Bold</span></span></td>
 </tr>
 <tr><td>![MoveToFolder](images/segoe-mdl/e8de.png)</td>
  <td><span data-ttu-id="127e7-2305">E8DE</span><span class="sxs-lookup"><span data-stu-id="127e7-2305">E8DE</span></span></td>
  <td><span data-ttu-id="127e7-2306">MoveToFolder</span><span class="sxs-lookup"><span data-stu-id="127e7-2306">MoveToFolder</span></span></td>
 </tr>
 <tr><td>![LikeDislike](images/segoe-mdl/e8df.png)</td>
  <td><span data-ttu-id="127e7-2308">E8DF</span><span class="sxs-lookup"><span data-stu-id="127e7-2308">E8DF</span></span></td>
  <td><span data-ttu-id="127e7-2309">LikeDislike</span><span class="sxs-lookup"><span data-stu-id="127e7-2309">LikeDislike</span></span></td>
 </tr>
 <tr><td>![Dislike](images/segoe-mdl/e8e0.png)</td>
  <td><span data-ttu-id="127e7-2311">E8E0</span><span class="sxs-lookup"><span data-stu-id="127e7-2311">E8E0</span></span></td>
  <td><span data-ttu-id="127e7-2312">Dislike</span><span class="sxs-lookup"><span data-stu-id="127e7-2312">Dislike</span></span></td>
 </tr>
 <tr><td>![Like](images/segoe-mdl/e8e1.png)</td>
  <td><span data-ttu-id="127e7-2314">E8E1</span><span class="sxs-lookup"><span data-stu-id="127e7-2314">E8E1</span></span></td>
  <td><span data-ttu-id="127e7-2315">Like</span><span class="sxs-lookup"><span data-stu-id="127e7-2315">Like</span></span></td>
 </tr>
 <tr><td>![AlignRight](images/segoe-mdl/e8e2.png)</td>
  <td><span data-ttu-id="127e7-2317">E8E2</span><span class="sxs-lookup"><span data-stu-id="127e7-2317">E8E2</span></span></td>
  <td><span data-ttu-id="127e7-2318">AlignRight</span><span class="sxs-lookup"><span data-stu-id="127e7-2318">AlignRight</span></span></td>
 </tr>
 <tr><td>![AlignCenter](images/segoe-mdl/e8e3.png)</td>
  <td><span data-ttu-id="127e7-2320">E8E3</span><span class="sxs-lookup"><span data-stu-id="127e7-2320">E8E3</span></span></td>
  <td><span data-ttu-id="127e7-2321">AlignCenter</span><span class="sxs-lookup"><span data-stu-id="127e7-2321">AlignCenter</span></span></td>
 </tr>
 <tr><td>![AlignLeft](images/segoe-mdl/e8e4.png)</td>
  <td><span data-ttu-id="127e7-2323">E8E4</span><span class="sxs-lookup"><span data-stu-id="127e7-2323">E8E4</span></span></td>
  <td><span data-ttu-id="127e7-2324">AlignLeft</span><span class="sxs-lookup"><span data-stu-id="127e7-2324">AlignLeft</span></span></td>
 </tr>
 <tr><td>![OpenFile](images/segoe-mdl/e8e5.png)</td>
  <td><span data-ttu-id="127e7-2326">E8E5</span><span class="sxs-lookup"><span data-stu-id="127e7-2326">E8E5</span></span></td>
  <td><span data-ttu-id="127e7-2327">OpenFile</span><span class="sxs-lookup"><span data-stu-id="127e7-2327">OpenFile</span></span></td>
 </tr>
 <tr><td>![ClearSelection](images/segoe-mdl/e8e6.png)</td>
  <td><span data-ttu-id="127e7-2329">E8E6</span><span class="sxs-lookup"><span data-stu-id="127e7-2329">E8E6</span></span></td>
  <td><span data-ttu-id="127e7-2330">ClearSelection</span><span class="sxs-lookup"><span data-stu-id="127e7-2330">ClearSelection</span></span></td>
 </tr>
 <tr><td>![FontDecrease](images/segoe-mdl/e8e7.png)</td>
  <td><span data-ttu-id="127e7-2332">E8E7</span><span class="sxs-lookup"><span data-stu-id="127e7-2332">E8E7</span></span></td>
  <td><span data-ttu-id="127e7-2333">FontDecrease</span><span class="sxs-lookup"><span data-stu-id="127e7-2333">FontDecrease</span></span></td>
 </tr>
 <tr><td>![FontIncrease](images/segoe-mdl/e8e8.png)</td>
  <td><span data-ttu-id="127e7-2335">E8E8</span><span class="sxs-lookup"><span data-stu-id="127e7-2335">E8E8</span></span></td>
  <td><span data-ttu-id="127e7-2336">FontIncrease</span><span class="sxs-lookup"><span data-stu-id="127e7-2336">FontIncrease</span></span></td>
 </tr>
 <tr><td>![FontSize](images/segoe-mdl/e8e9.png)</td>
  <td><span data-ttu-id="127e7-2338">E8E9</span><span class="sxs-lookup"><span data-stu-id="127e7-2338">E8E9</span></span></td>
  <td><span data-ttu-id="127e7-2339">FontSize</span><span class="sxs-lookup"><span data-stu-id="127e7-2339">FontSize</span></span></td>
 </tr>
 <tr><td>![CellPhone](images/segoe-mdl/e8ea.png)</td>
  <td><span data-ttu-id="127e7-2341">E8EA</span><span class="sxs-lookup"><span data-stu-id="127e7-2341">E8EA</span></span></td>
  <td><span data-ttu-id="127e7-2342">CellPhone</span><span class="sxs-lookup"><span data-stu-id="127e7-2342">CellPhone</span></span></td>
 </tr>
 <tr><td>![Reshare](images/segoe-mdl/e8eb.png)</td>
  <td><span data-ttu-id="127e7-2344">E8EB</span><span class="sxs-lookup"><span data-stu-id="127e7-2344">E8EB</span></span></td>
  <td><span data-ttu-id="127e7-2345">Reshare</span><span class="sxs-lookup"><span data-stu-id="127e7-2345">Reshare</span></span></td>
 </tr>
 <tr><td>![Tag](images/segoe-mdl/e8ec.png)</td>
  <td><span data-ttu-id="127e7-2347">E8EC</span><span class="sxs-lookup"><span data-stu-id="127e7-2347">E8EC</span></span></td>
  <td><span data-ttu-id="127e7-2348">Tag</span><span class="sxs-lookup"><span data-stu-id="127e7-2348">Tag</span></span></td>
 </tr>
 <tr><td>![RepeatOne](images/segoe-mdl/e8ed.png)</td>
  <td><span data-ttu-id="127e7-2350">E8ED</span><span class="sxs-lookup"><span data-stu-id="127e7-2350">E8ED</span></span></td>
  <td><span data-ttu-id="127e7-2351">RepeatOne</span><span class="sxs-lookup"><span data-stu-id="127e7-2351">RepeatOne</span></span></td>
 </tr>
 <tr><td>![RepeatAll](images/segoe-mdl/e8ee.png)</td>
  <td><span data-ttu-id="127e7-2353">E8EE</span><span class="sxs-lookup"><span data-stu-id="127e7-2353">E8EE</span></span></td>
  <td><span data-ttu-id="127e7-2354">RepeatAll</span><span class="sxs-lookup"><span data-stu-id="127e7-2354">RepeatAll</span></span></td>
 </tr>
 <tr><td>![Calculator](images/segoe-mdl/e8ef.png)</td>
  <td><span data-ttu-id="127e7-2356">E8EF</span><span class="sxs-lookup"><span data-stu-id="127e7-2356">E8EF</span></span></td>
  <td><span data-ttu-id="127e7-2357">Calculator</span><span class="sxs-lookup"><span data-stu-id="127e7-2357">Calculator</span></span></td>
 </tr>
 <tr><td>![Directions](images/segoe-mdl/e8f0.png)</td>
  <td><span data-ttu-id="127e7-2359">E8F0</span><span class="sxs-lookup"><span data-stu-id="127e7-2359">E8F0</span></span></td>
  <td><span data-ttu-id="127e7-2360">Directions</span><span class="sxs-lookup"><span data-stu-id="127e7-2360">Directions</span></span></td>
 </tr>
 <tr><td>![Library](images/segoe-mdl/e8f1.png)</td>
  <td><span data-ttu-id="127e7-2362">E8F1</span><span class="sxs-lookup"><span data-stu-id="127e7-2362">E8F1</span></span></td>
  <td><span data-ttu-id="127e7-2363">Library</span><span class="sxs-lookup"><span data-stu-id="127e7-2363">Library</span></span></td>
 </tr>
 <tr><td>![ChatBubbles](images/segoe-mdl/e8f2.png)</td>
  <td><span data-ttu-id="127e7-2365">E8F2</span><span class="sxs-lookup"><span data-stu-id="127e7-2365">E8F2</span></span></td>
  <td><span data-ttu-id="127e7-2366">ChatBubbles</span><span class="sxs-lookup"><span data-stu-id="127e7-2366">ChatBubbles</span></span></td>
 </tr>
 <tr><td>![PostUpdate](images/segoe-mdl/e8f3.png)</td>
  <td><span data-ttu-id="127e7-2368">E8F3</span><span class="sxs-lookup"><span data-stu-id="127e7-2368">E8F3</span></span></td>
  <td><span data-ttu-id="127e7-2369">PostUpdate</span><span class="sxs-lookup"><span data-stu-id="127e7-2369">PostUpdate</span></span></td>
 </tr>
 <tr><td>![NewFolder](images/segoe-mdl/e8f4.png)</td>
  <td><span data-ttu-id="127e7-2371">E8F4</span><span class="sxs-lookup"><span data-stu-id="127e7-2371">E8F4</span></span></td>
  <td><span data-ttu-id="127e7-2372">NewFolder</span><span class="sxs-lookup"><span data-stu-id="127e7-2372">NewFolder</span></span></td>
 </tr>
 <tr><td>![CalendarReply](images/segoe-mdl/e8f5.png)</td>
  <td><span data-ttu-id="127e7-2374">E8F5</span><span class="sxs-lookup"><span data-stu-id="127e7-2374">E8F5</span></span></td>
  <td><span data-ttu-id="127e7-2375">CalendarReply</span><span class="sxs-lookup"><span data-stu-id="127e7-2375">CalendarReply</span></span></td>
 </tr>
 <tr><td>![UnsyncFolder](images/segoe-mdl/e8f6.png)</td>
  <td><span data-ttu-id="127e7-2377">E8F6</span><span class="sxs-lookup"><span data-stu-id="127e7-2377">E8F6</span></span></td>
  <td><span data-ttu-id="127e7-2378">UnsyncFolder</span><span class="sxs-lookup"><span data-stu-id="127e7-2378">UnsyncFolder</span></span></td>
 </tr>
 <tr><td>![SyncFolder](images/segoe-mdl/e8f7.png)</td>
  <td><span data-ttu-id="127e7-2380">E8F7</span><span class="sxs-lookup"><span data-stu-id="127e7-2380">E8F7</span></span></td>
  <td><span data-ttu-id="127e7-2381">SyncFolder</span><span class="sxs-lookup"><span data-stu-id="127e7-2381">SyncFolder</span></span></td>
 </tr>
 <tr><td>![BlockContact](images/segoe-mdl/e8f8.png)</td>
  <td><span data-ttu-id="127e7-2383">E8F8</span><span class="sxs-lookup"><span data-stu-id="127e7-2383">E8F8</span></span></td>
  <td><span data-ttu-id="127e7-2384">BlockContact</span><span class="sxs-lookup"><span data-stu-id="127e7-2384">BlockContact</span></span></td>
 </tr>
 <tr><td>![SwitchApps](images/segoe-mdl/e8f9.png)</td>
  <td><span data-ttu-id="127e7-2386">E8F9</span><span class="sxs-lookup"><span data-stu-id="127e7-2386">E8F9</span></span></td>
  <td><span data-ttu-id="127e7-2387">SwitchApps</span><span class="sxs-lookup"><span data-stu-id="127e7-2387">SwitchApps</span></span></td>
 </tr>
 <tr><td>![AddFriend](images/segoe-mdl/e8fa.png)</td>
  <td><span data-ttu-id="127e7-2389">E8FA</span><span class="sxs-lookup"><span data-stu-id="127e7-2389">E8FA</span></span></td>
  <td><span data-ttu-id="127e7-2390">AddFriend</span><span class="sxs-lookup"><span data-stu-id="127e7-2390">AddFriend</span></span></td>
 </tr>
 <tr><td>![Accept](images/segoe-mdl/e8fb.png)</td>
  <td><span data-ttu-id="127e7-2392">E8FB</span><span class="sxs-lookup"><span data-stu-id="127e7-2392">E8FB</span></span></td>
  <td><span data-ttu-id="127e7-2393">Accept</span><span class="sxs-lookup"><span data-stu-id="127e7-2393">Accept</span></span></td>
 </tr>
 <tr><td>![GoToStart](images/segoe-mdl/e8fc.png)</td>
  <td><span data-ttu-id="127e7-2395">E8FC</span><span class="sxs-lookup"><span data-stu-id="127e7-2395">E8FC</span></span></td>
  <td><span data-ttu-id="127e7-2396">GoToStart</span><span class="sxs-lookup"><span data-stu-id="127e7-2396">GoToStart</span></span></td>
 </tr>
 <tr><td>![BulletedList](images/segoe-mdl/e8fd.png)</td>
  <td><span data-ttu-id="127e7-2398">E8FD</span><span class="sxs-lookup"><span data-stu-id="127e7-2398">E8FD</span></span></td>
  <td><span data-ttu-id="127e7-2399">BulletedList</span><span class="sxs-lookup"><span data-stu-id="127e7-2399">BulletedList</span></span></td>
 </tr>
 <tr><td>![Scan](images/segoe-mdl/e8fe.png)</td>
  <td><span data-ttu-id="127e7-2401">E8FE</span><span class="sxs-lookup"><span data-stu-id="127e7-2401">E8FE</span></span></td>
  <td><span data-ttu-id="127e7-2402">Scan</span><span class="sxs-lookup"><span data-stu-id="127e7-2402">Scan</span></span></td>
 </tr>
 <tr><td>![Preview](images/segoe-mdl/e8ff.png)</td>
  <td><span data-ttu-id="127e7-2404">E8FF</span><span class="sxs-lookup"><span data-stu-id="127e7-2404">E8FF</span></span></td>
  <td><span data-ttu-id="127e7-2405">Preview</span><span class="sxs-lookup"><span data-stu-id="127e7-2405">Preview</span></span></td>
 </tr>
 <tr><td>![ZeroBars](images/segoe-mdl/e904.png)</td>
  <td><span data-ttu-id="127e7-2407">E904</span><span class="sxs-lookup"><span data-stu-id="127e7-2407">E904</span></span></td>
  <td><span data-ttu-id="127e7-2408">ZeroBars</span><span class="sxs-lookup"><span data-stu-id="127e7-2408">ZeroBars</span></span></td>
 </tr>
 <tr><td>![OneBar](images/segoe-mdl/e905.png)</td>
  <td><span data-ttu-id="127e7-2410">E905</span><span class="sxs-lookup"><span data-stu-id="127e7-2410">E905</span></span></td>
  <td><span data-ttu-id="127e7-2411">OneBar</span><span class="sxs-lookup"><span data-stu-id="127e7-2411">OneBar</span></span></td>
 </tr>
 <tr><td>![TwoBars](images/segoe-mdl/e906.png)</td>
  <td><span data-ttu-id="127e7-2413">E906</span><span class="sxs-lookup"><span data-stu-id="127e7-2413">E906</span></span></td>
  <td><span data-ttu-id="127e7-2414">TwoBars</span><span class="sxs-lookup"><span data-stu-id="127e7-2414">TwoBars</span></span></td>
 </tr>
 <tr><td>![ThreeBars](images/segoe-mdl/e907.png)</td>
  <td><span data-ttu-id="127e7-2416">E907</span><span class="sxs-lookup"><span data-stu-id="127e7-2416">E907</span></span></td>
  <td><span data-ttu-id="127e7-2417">ThreeBars</span><span class="sxs-lookup"><span data-stu-id="127e7-2417">ThreeBars</span></span></td>
 </tr>
 <tr><td>![FourBars](images/segoe-mdl/e908.png)</td>
  <td><span data-ttu-id="127e7-2419">E908</span><span class="sxs-lookup"><span data-stu-id="127e7-2419">E908</span></span></td>
  <td><span data-ttu-id="127e7-2420">FourBars</span><span class="sxs-lookup"><span data-stu-id="127e7-2420">FourBars</span></span></td>
 </tr>
 <tr><td>![World](images/segoe-mdl/e909.png)</td>
  <td><span data-ttu-id="127e7-2422">E909</span><span class="sxs-lookup"><span data-stu-id="127e7-2422">E909</span></span></td>
  <td><span data-ttu-id="127e7-2423">World</span><span class="sxs-lookup"><span data-stu-id="127e7-2423">World</span></span></td>
 </tr>
 <tr><td>![Comment](images/segoe-mdl/e90a.png)</td>
  <td><span data-ttu-id="127e7-2425">E90A</span><span class="sxs-lookup"><span data-stu-id="127e7-2425">E90A</span></span></td>
  <td><span data-ttu-id="127e7-2426">Comment</span><span class="sxs-lookup"><span data-stu-id="127e7-2426">Comment</span></span></td>
 </tr>
 <tr><td>![MusicInfo](images/segoe-mdl/e90b.png)</td>
  <td><span data-ttu-id="127e7-2428">E90B</span><span class="sxs-lookup"><span data-stu-id="127e7-2428">E90B</span></span></td>
  <td><span data-ttu-id="127e7-2429">MusicInfo</span><span class="sxs-lookup"><span data-stu-id="127e7-2429">MusicInfo</span></span></td>
 </tr>
 <tr><td>![DockLeft](images/segoe-mdl/e90c.png)</td>
  <td><span data-ttu-id="127e7-2431">E90C</span><span class="sxs-lookup"><span data-stu-id="127e7-2431">E90C</span></span></td>
  <td><span data-ttu-id="127e7-2432">DockLeft</span><span class="sxs-lookup"><span data-stu-id="127e7-2432">DockLeft</span></span></td>
 </tr>
 <tr><td>![DockRight](images/segoe-mdl/e90d.png)</td>
  <td><span data-ttu-id="127e7-2434">E90D</span><span class="sxs-lookup"><span data-stu-id="127e7-2434">E90D</span></span></td>
  <td><span data-ttu-id="127e7-2435">DockRight</span><span class="sxs-lookup"><span data-stu-id="127e7-2435">DockRight</span></span></td>
 </tr>
 <tr><td>![DockBottom](images/segoe-mdl/e90e.png)</td>
  <td><span data-ttu-id="127e7-2437">E90E</span><span class="sxs-lookup"><span data-stu-id="127e7-2437">E90E</span></span></td>
  <td><span data-ttu-id="127e7-2438">DockBottom</span><span class="sxs-lookup"><span data-stu-id="127e7-2438">DockBottom</span></span></td>
 </tr>
 <tr><td>![Repair](images/segoe-mdl/e90f.png)</td>
  <td><span data-ttu-id="127e7-2440">E90F</span><span class="sxs-lookup"><span data-stu-id="127e7-2440">E90F</span></span></td>
  <td><span data-ttu-id="127e7-2441">Repair</span><span class="sxs-lookup"><span data-stu-id="127e7-2441">Repair</span></span></td>
 </tr>
 <tr><td>![Accounts](images/segoe-mdl/e910.png)</td>
  <td><span data-ttu-id="127e7-2443">E910</span><span class="sxs-lookup"><span data-stu-id="127e7-2443">E910</span></span></td>
  <td><span data-ttu-id="127e7-2444">Accounts</span><span class="sxs-lookup"><span data-stu-id="127e7-2444">Accounts</span></span></td>
 </tr>
 <tr><td>![DullSound](images/segoe-mdl/e911.png)</td>
  <td><span data-ttu-id="127e7-2446">E911</span><span class="sxs-lookup"><span data-stu-id="127e7-2446">E911</span></span></td>
  <td><span data-ttu-id="127e7-2447">DullSound</span><span class="sxs-lookup"><span data-stu-id="127e7-2447">DullSound</span></span></td>
 </tr>
 <tr><td>![Manage](images/segoe-mdl/e912.png)</td>
  <td><span data-ttu-id="127e7-2449">E912</span><span class="sxs-lookup"><span data-stu-id="127e7-2449">E912</span></span></td>
  <td><span data-ttu-id="127e7-2450">Manage</span><span class="sxs-lookup"><span data-stu-id="127e7-2450">Manage</span></span></td>
 </tr>
 <tr><td>![Street](images/segoe-mdl/e913.png)</td>
  <td><span data-ttu-id="127e7-2452">E913</span><span class="sxs-lookup"><span data-stu-id="127e7-2452">E913</span></span></td>
  <td><span data-ttu-id="127e7-2453">Street</span><span class="sxs-lookup"><span data-stu-id="127e7-2453">Street</span></span></td>
 </tr>
 <tr><td>![Printer3D](images/segoe-mdl/e914.png)</td>
  <td><span data-ttu-id="127e7-2455">E914</span><span class="sxs-lookup"><span data-stu-id="127e7-2455">E914</span></span></td>
  <td><span data-ttu-id="127e7-2456">Printer3D</span><span class="sxs-lookup"><span data-stu-id="127e7-2456">Printer3D</span></span></td>
 </tr>
 <tr><td>![RadioBullet](images/segoe-mdl/e915.png)</td>
  <td><span data-ttu-id="127e7-2458">E915</span><span class="sxs-lookup"><span data-stu-id="127e7-2458">E915</span></span></td>
  <td><span data-ttu-id="127e7-2459">RadioBullet</span><span class="sxs-lookup"><span data-stu-id="127e7-2459">RadioBullet</span></span></td>
 </tr>
 <tr><td>![Stopwatch](images/segoe-mdl/e916.png)</td>
  <td><span data-ttu-id="127e7-2461">E916</span><span class="sxs-lookup"><span data-stu-id="127e7-2461">E916</span></span></td>
  <td><span data-ttu-id="127e7-2462">Stopwatch</span><span class="sxs-lookup"><span data-stu-id="127e7-2462">Stopwatch</span></span></td>
 </tr>
 <tr><td>![Photo](images/segoe-mdl/e91b.png)</td>
  <td><span data-ttu-id="127e7-2464">E91B</span><span class="sxs-lookup"><span data-stu-id="127e7-2464">E91B</span></span></td>
  <td><span data-ttu-id="127e7-2465">Photo</span><span class="sxs-lookup"><span data-stu-id="127e7-2465">Photo</span></span></td>
 </tr>
 <tr><td>![ActionCenter](images/segoe-mdl/e91c.png)</td>
  <td><span data-ttu-id="127e7-2467">E91C</span><span class="sxs-lookup"><span data-stu-id="127e7-2467">E91C</span></span></td>
  <td><span data-ttu-id="127e7-2468">ActionCenter</span><span class="sxs-lookup"><span data-stu-id="127e7-2468">ActionCenter</span></span></td>
 </tr>
 <tr><td>![FullCircleMask](images/segoe-mdl/e91f.png)</td>
  <td><span data-ttu-id="127e7-2470">E91F</span><span class="sxs-lookup"><span data-stu-id="127e7-2470">E91F</span></span></td>
  <td><span data-ttu-id="127e7-2471">FullCircleMask</span><span class="sxs-lookup"><span data-stu-id="127e7-2471">FullCircleMask</span></span></td>
 </tr>
 <tr><td>![ChromeMinimize](images/segoe-mdl/e921.png)</td>
  <td><span data-ttu-id="127e7-2473">E921</span><span class="sxs-lookup"><span data-stu-id="127e7-2473">E921</span></span></td>
  <td><span data-ttu-id="127e7-2474">ChromeMinimize</span><span class="sxs-lookup"><span data-stu-id="127e7-2474">ChromeMinimize</span></span></td>
 </tr>
 <tr><td>![ChromeMaximize](images/segoe-mdl/e922.png)</td>
  <td><span data-ttu-id="127e7-2476">E922</span><span class="sxs-lookup"><span data-stu-id="127e7-2476">E922</span></span></td>
  <td><span data-ttu-id="127e7-2477">ChromeMaximize</span><span class="sxs-lookup"><span data-stu-id="127e7-2477">ChromeMaximize</span></span></td>
 </tr>
 <tr><td>![ChromeRestore](images/segoe-mdl/e923.png)</td>
  <td><span data-ttu-id="127e7-2479">E923</span><span class="sxs-lookup"><span data-stu-id="127e7-2479">E923</span></span></td>
  <td><span data-ttu-id="127e7-2480">ChromeRestore</span><span class="sxs-lookup"><span data-stu-id="127e7-2480">ChromeRestore</span></span></td>
 </tr>
 <tr><td>![Annotation](images/segoe-mdl/e924.png)</td>
  <td><span data-ttu-id="127e7-2482">E924</span><span class="sxs-lookup"><span data-stu-id="127e7-2482">E924</span></span></td>
  <td><span data-ttu-id="127e7-2483">Annotation</span><span class="sxs-lookup"><span data-stu-id="127e7-2483">Annotation</span></span></td>
 </tr>
 <tr><td>![BackSpaceQWERTYSm](images/segoe-mdl/e925.png)</td>
  <td><span data-ttu-id="127e7-2485">E925</span><span class="sxs-lookup"><span data-stu-id="127e7-2485">E925</span></span></td>
  <td><span data-ttu-id="127e7-2486">BackSpaceQWERTYSm</span><span class="sxs-lookup"><span data-stu-id="127e7-2486">BackSpaceQWERTYSm</span></span></td>
 </tr>
 <tr><td>![BackSpaceQWERTYMd](images/segoe-mdl/e926.png)</td>
  <td><span data-ttu-id="127e7-2488">E926</span><span class="sxs-lookup"><span data-stu-id="127e7-2488">E926</span></span></td>
  <td><span data-ttu-id="127e7-2489">BackSpaceQWERTYMd</span><span class="sxs-lookup"><span data-stu-id="127e7-2489">BackSpaceQWERTYMd</span></span></td>
 </tr>
 <tr><td>![Swipe](images/segoe-mdl/e927.png)</td>
  <td><span data-ttu-id="127e7-2491">E927</span><span class="sxs-lookup"><span data-stu-id="127e7-2491">E927</span></span></td>
  <td><span data-ttu-id="127e7-2492">Swipe</span><span class="sxs-lookup"><span data-stu-id="127e7-2492">Swipe</span></span></td>
 </tr>
 <tr><td>![Fingerprint](images/segoe-mdl/e928.png)</td>
  <td><span data-ttu-id="127e7-2494">E928</span><span class="sxs-lookup"><span data-stu-id="127e7-2494">E928</span></span></td>
  <td><span data-ttu-id="127e7-2495">Fingerprint</span><span class="sxs-lookup"><span data-stu-id="127e7-2495">Fingerprint</span></span></td>
 </tr>
 <tr><td>![Handwriting](images/segoe-mdl/e929.png)</td>
  <td><span data-ttu-id="127e7-2497">E929</span><span class="sxs-lookup"><span data-stu-id="127e7-2497">E929</span></span></td>
  <td><span data-ttu-id="127e7-2498">Handwriting</span><span class="sxs-lookup"><span data-stu-id="127e7-2498">Handwriting</span></span></td>
 </tr>
 <tr><td>![ChromeBackToWindow](images/segoe-mdl/e92c.png)</td>
  <td><span data-ttu-id="127e7-2500">E92C</span><span class="sxs-lookup"><span data-stu-id="127e7-2500">E92C</span></span></td>
  <td><span data-ttu-id="127e7-2501">ChromeBackToWindow</span><span class="sxs-lookup"><span data-stu-id="127e7-2501">ChromeBackToWindow</span></span></td>
 </tr>
 <tr><td>![ChromeFullScreen](images/segoe-mdl/e92d.png)</td>
  <td><span data-ttu-id="127e7-2503">E92D</span><span class="sxs-lookup"><span data-stu-id="127e7-2503">E92D</span></span></td>
  <td><span data-ttu-id="127e7-2504">ChromeFullScreen</span><span class="sxs-lookup"><span data-stu-id="127e7-2504">ChromeFullScreen</span></span></td>
 </tr>
 <tr><td>![KeyboardStandard](images/segoe-mdl/e92e.png)</td>
  <td><span data-ttu-id="127e7-2506">E92E</span><span class="sxs-lookup"><span data-stu-id="127e7-2506">E92E</span></span></td>
  <td><span data-ttu-id="127e7-2507">KeyboardStandard</span><span class="sxs-lookup"><span data-stu-id="127e7-2507">KeyboardStandard</span></span></td>
 </tr>
 <tr><td>![KeyboardDismiss](images/segoe-mdl/e92f.png)</td>
  <td><span data-ttu-id="127e7-2509">E92F</span><span class="sxs-lookup"><span data-stu-id="127e7-2509">E92F</span></span></td>
  <td><span data-ttu-id="127e7-2510">KeyboardDismiss</span><span class="sxs-lookup"><span data-stu-id="127e7-2510">KeyboardDismiss</span></span></td>
 </tr>
 <tr><td>![Completed](images/segoe-mdl/e930.png)</td>
  <td><span data-ttu-id="127e7-2512">E930</span><span class="sxs-lookup"><span data-stu-id="127e7-2512">E930</span></span></td>
  <td><span data-ttu-id="127e7-2513">Completed</span><span class="sxs-lookup"><span data-stu-id="127e7-2513">Completed</span></span></td>
 </tr>
 <tr><td>![ChromeAnnotate](images/segoe-mdl/e931.png)</td>
  <td><span data-ttu-id="127e7-2515">E931</span><span class="sxs-lookup"><span data-stu-id="127e7-2515">E931</span></span></td>
  <td><span data-ttu-id="127e7-2516">ChromeAnnotate</span><span class="sxs-lookup"><span data-stu-id="127e7-2516">ChromeAnnotate</span></span></td>
 </tr>
 <tr><td>![Label](images/segoe-mdl/e932.png)</td>
  <td><span data-ttu-id="127e7-2518">E932</span><span class="sxs-lookup"><span data-stu-id="127e7-2518">E932</span></span></td>
  <td><span data-ttu-id="127e7-2519">Label</span><span class="sxs-lookup"><span data-stu-id="127e7-2519">Label</span></span></td>
 </tr>
 <tr><td>![IBeam](images/segoe-mdl/e933.png)</td>
  <td><span data-ttu-id="127e7-2521">E933</span><span class="sxs-lookup"><span data-stu-id="127e7-2521">E933</span></span></td>
  <td><span data-ttu-id="127e7-2522">IBeam</span><span class="sxs-lookup"><span data-stu-id="127e7-2522">IBeam</span></span></td>
 </tr>
 <tr><td>![IBeamOutline](images/segoe-mdl/e934.png)</td>
  <td><span data-ttu-id="127e7-2524">E934</span><span class="sxs-lookup"><span data-stu-id="127e7-2524">E934</span></span></td>
  <td><span data-ttu-id="127e7-2525">IBeamOutline</span><span class="sxs-lookup"><span data-stu-id="127e7-2525">IBeamOutline</span></span></td>
 </tr>
 <tr><td>![FlickDown](images/segoe-mdl/e935.png)</td>
  <td><span data-ttu-id="127e7-2527">E935</span><span class="sxs-lookup"><span data-stu-id="127e7-2527">E935</span></span></td>
  <td><span data-ttu-id="127e7-2528">FlickDown</span><span class="sxs-lookup"><span data-stu-id="127e7-2528">FlickDown</span></span></td>
 </tr>
 <tr><td>![FlickUp](images/segoe-mdl/e936.png)</td>
  <td><span data-ttu-id="127e7-2530">E936</span><span class="sxs-lookup"><span data-stu-id="127e7-2530">E936</span></span></td>
  <td><span data-ttu-id="127e7-2531">FlickUp</span><span class="sxs-lookup"><span data-stu-id="127e7-2531">FlickUp</span></span></td>
 </tr>
 <tr><td>![FlickLeft](images/segoe-mdl/e937.png)</td>
  <td><span data-ttu-id="127e7-2533">E937</span><span class="sxs-lookup"><span data-stu-id="127e7-2533">E937</span></span></td>
  <td><span data-ttu-id="127e7-2534">FlickLeft</span><span class="sxs-lookup"><span data-stu-id="127e7-2534">FlickLeft</span></span></td>
 </tr>
 <tr><td>![FlickRight](images/segoe-mdl/e938.png)</td>
  <td><span data-ttu-id="127e7-2536">E938</span><span class="sxs-lookup"><span data-stu-id="127e7-2536">E938</span></span></td>
  <td><span data-ttu-id="127e7-2537">FlickRight</span><span class="sxs-lookup"><span data-stu-id="127e7-2537">FlickRight</span></span></td>
 </tr>
 <tr><td>![FeedbackApp](images/segoe-mdl/e939.png)</td>
  <td><span data-ttu-id="127e7-2539">E939</span><span class="sxs-lookup"><span data-stu-id="127e7-2539">E939</span></span></td>
  <td><span data-ttu-id="127e7-2540">FeedbackApp</span><span class="sxs-lookup"><span data-stu-id="127e7-2540">FeedbackApp</span></span></td>
 </tr>
 <tr><td>![MusicAlbum](images/segoe-mdl/e93c.png)</td>
  <td><span data-ttu-id="127e7-2542">E93C</span><span class="sxs-lookup"><span data-stu-id="127e7-2542">E93C</span></span></td>
  <td><span data-ttu-id="127e7-2543">MusicAlbum</span><span class="sxs-lookup"><span data-stu-id="127e7-2543">MusicAlbum</span></span></td>
 </tr>
 <tr><td>![Streaming](images/segoe-mdl/e93e.png)</td>
  <td><span data-ttu-id="127e7-2545">E93E</span><span class="sxs-lookup"><span data-stu-id="127e7-2545">E93E</span></span></td>
  <td><span data-ttu-id="127e7-2546">Streaming</span><span class="sxs-lookup"><span data-stu-id="127e7-2546">Streaming</span></span></td>
 </tr>
 <tr><td>![Code](images/segoe-mdl/e943.png)</td>
  <td><span data-ttu-id="127e7-2548">E943</span><span class="sxs-lookup"><span data-stu-id="127e7-2548">E943</span></span></td>
  <td><span data-ttu-id="127e7-2549">Code</span><span class="sxs-lookup"><span data-stu-id="127e7-2549">Code</span></span></td>
 </tr>
 <tr><td>![ReturnToWindow](images/segoe-mdl/e944.png)</td>
  <td><span data-ttu-id="127e7-2551">E944</span><span class="sxs-lookup"><span data-stu-id="127e7-2551">E944</span></span></td>
  <td><span data-ttu-id="127e7-2552">ReturnToWindow</span><span class="sxs-lookup"><span data-stu-id="127e7-2552">ReturnToWindow</span></span></td>
 </tr>
 <tr><td>![LightningBolt](images/segoe-mdl/e945.png)</td>
  <td><span data-ttu-id="127e7-2554">E945</span><span class="sxs-lookup"><span data-stu-id="127e7-2554">E945</span></span></td>
  <td><span data-ttu-id="127e7-2555">LightningBolt</span><span class="sxs-lookup"><span data-stu-id="127e7-2555">LightningBolt</span></span></td>
 </tr>
 <tr><td>![Info](images/segoe-mdl/e946.png)</td>
  <td><span data-ttu-id="127e7-2557">E946</span><span class="sxs-lookup"><span data-stu-id="127e7-2557">E946</span></span></td>
  <td><span data-ttu-id="127e7-2558">Info</span><span class="sxs-lookup"><span data-stu-id="127e7-2558">Info</span></span></td>
 </tr>
 <tr><td>![CalculatorMultiply](images/segoe-mdl/e947.png)</td>
  <td><span data-ttu-id="127e7-2560">E947</span><span class="sxs-lookup"><span data-stu-id="127e7-2560">E947</span></span></td>
  <td><span data-ttu-id="127e7-2561">CalculatorMultiply</span><span class="sxs-lookup"><span data-stu-id="127e7-2561">CalculatorMultiply</span></span></td>
 </tr>
 <tr><td>![CalculatorAddition](images/segoe-mdl/e948.png)</td>
  <td><span data-ttu-id="127e7-2563">E948</span><span class="sxs-lookup"><span data-stu-id="127e7-2563">E948</span></span></td>
  <td><span data-ttu-id="127e7-2564">CalculatorAddition</span><span class="sxs-lookup"><span data-stu-id="127e7-2564">CalculatorAddition</span></span></td>
 </tr>
 <tr><td>![CalculatorSubtract](images/segoe-mdl/e949.png)</td>
  <td><span data-ttu-id="127e7-2566">E949</span><span class="sxs-lookup"><span data-stu-id="127e7-2566">E949</span></span></td>
  <td><span data-ttu-id="127e7-2567">CalculatorSubtract</span><span class="sxs-lookup"><span data-stu-id="127e7-2567">CalculatorSubtract</span></span></td>
 </tr>
 <tr><td>![CalculatorDivide](images/segoe-mdl/e94a.png)</td>
  <td><span data-ttu-id="127e7-2569">E94A</span><span class="sxs-lookup"><span data-stu-id="127e7-2569">E94A</span></span></td>
  <td><span data-ttu-id="127e7-2570">CalculatorDivide</span><span class="sxs-lookup"><span data-stu-id="127e7-2570">CalculatorDivide</span></span></td>
 </tr>
 <tr><td>![CalculatorSquareroot](images/segoe-mdl/e94b.png)</td>
  <td><span data-ttu-id="127e7-2572">E94B</span><span class="sxs-lookup"><span data-stu-id="127e7-2572">E94B</span></span></td>
  <td><span data-ttu-id="127e7-2573">CalculatorSquareroot</span><span class="sxs-lookup"><span data-stu-id="127e7-2573">CalculatorSquareroot</span></span></td>
 </tr>
 <tr><td>![CalculatorPercentage](images/segoe-mdl/e94c.png)</td>
  <td><span data-ttu-id="127e7-2575">E94C</span><span class="sxs-lookup"><span data-stu-id="127e7-2575">E94C</span></span></td>
  <td><span data-ttu-id="127e7-2576">CalculatorPercentage</span><span class="sxs-lookup"><span data-stu-id="127e7-2576">CalculatorPercentage</span></span></td>
 </tr>
 <tr><td>![CalculatorNegate](images/segoe-mdl/e94d.png)</td>
  <td><span data-ttu-id="127e7-2578">E94D</span><span class="sxs-lookup"><span data-stu-id="127e7-2578">E94D</span></span></td>
  <td><span data-ttu-id="127e7-2579">CalculatorNegate</span><span class="sxs-lookup"><span data-stu-id="127e7-2579">CalculatorNegate</span></span></td>
 </tr>
 <tr><td>![CalculatorEqualTo](images/segoe-mdl/e94e.png)</td>
  <td><span data-ttu-id="127e7-2581">E94E</span><span class="sxs-lookup"><span data-stu-id="127e7-2581">E94E</span></span></td>
  <td><span data-ttu-id="127e7-2582">CalculatorEqualTo</span><span class="sxs-lookup"><span data-stu-id="127e7-2582">CalculatorEqualTo</span></span></td>
 </tr>
 <tr><td>![CalculatorBackspace](images/segoe-mdl/e94f.png)</td>
  <td><span data-ttu-id="127e7-2584">E94F</span><span class="sxs-lookup"><span data-stu-id="127e7-2584">E94F</span></span></td>
  <td><span data-ttu-id="127e7-2585">CalculatorBackspace</span><span class="sxs-lookup"><span data-stu-id="127e7-2585">CalculatorBackspace</span></span></td>
 </tr>
 <tr><td>![Component](images/segoe-mdl/e950.png)</td>
  <td><span data-ttu-id="127e7-2587">E950</span><span class="sxs-lookup"><span data-stu-id="127e7-2587">E950</span></span></td>
  <td><span data-ttu-id="127e7-2588">Component</span><span class="sxs-lookup"><span data-stu-id="127e7-2588">Component</span></span></td>
 </tr>
 <tr><td>![DMC](images/segoe-mdl/e951.png)</td>
  <td><span data-ttu-id="127e7-2590">E951</span><span class="sxs-lookup"><span data-stu-id="127e7-2590">E951</span></span></td>
  <td><span data-ttu-id="127e7-2591">DMC</span><span class="sxs-lookup"><span data-stu-id="127e7-2591">DMC</span></span></td>
 </tr>
 <tr><td>![Dock](images/segoe-mdl/e952.png)</td>
  <td><span data-ttu-id="127e7-2593">E952</span><span class="sxs-lookup"><span data-stu-id="127e7-2593">E952</span></span></td>
  <td><span data-ttu-id="127e7-2594">Dock</span><span class="sxs-lookup"><span data-stu-id="127e7-2594">Dock</span></span></td>
 </tr>
 <tr><td>![MultimediaDMS](images/segoe-mdl/e953.png)</td>
  <td><span data-ttu-id="127e7-2596">E953</span><span class="sxs-lookup"><span data-stu-id="127e7-2596">E953</span></span></td>
  <td><span data-ttu-id="127e7-2597">MultimediaDMS</span><span class="sxs-lookup"><span data-stu-id="127e7-2597">MultimediaDMS</span></span></td>
 </tr>
 <tr><td>![MultimediaDVR](images/segoe-mdl/e954.png)</td>
  <td><span data-ttu-id="127e7-2599">E954</span><span class="sxs-lookup"><span data-stu-id="127e7-2599">E954</span></span></td>
  <td><span data-ttu-id="127e7-2600">MultimediaDVR</span><span class="sxs-lookup"><span data-stu-id="127e7-2600">MultimediaDVR</span></span></td>
 </tr>
 <tr><td>![MultimediaPMP](images/segoe-mdl/e955.png)</td>
  <td><span data-ttu-id="127e7-2602">E955</span><span class="sxs-lookup"><span data-stu-id="127e7-2602">E955</span></span></td>
  <td><span data-ttu-id="127e7-2603">MultimediaPMP</span><span class="sxs-lookup"><span data-stu-id="127e7-2603">MultimediaPMP</span></span></td>
 </tr>
 <tr><td>![PrintfaxPrinterFile](images/segoe-mdl/e956.png)</td>
  <td><span data-ttu-id="127e7-2605">E956</span><span class="sxs-lookup"><span data-stu-id="127e7-2605">E956</span></span></td>
  <td><span data-ttu-id="127e7-2606">PrintfaxPrinterFile</span><span class="sxs-lookup"><span data-stu-id="127e7-2606">PrintfaxPrinterFile</span></span></td>
 </tr>
 <tr><td>![Sensor](images/segoe-mdl/e957.png)</td>
  <td><span data-ttu-id="127e7-2608">E957</span><span class="sxs-lookup"><span data-stu-id="127e7-2608">E957</span></span></td>
  <td><span data-ttu-id="127e7-2609">Sensor</span><span class="sxs-lookup"><span data-stu-id="127e7-2609">Sensor</span></span></td>
 </tr>
 <tr><td>![StorageOptical](images/segoe-mdl/e958.png)</td>
  <td><span data-ttu-id="127e7-2611">E958</span><span class="sxs-lookup"><span data-stu-id="127e7-2611">E958</span></span></td>
  <td><span data-ttu-id="127e7-2612">StorageOptical</span><span class="sxs-lookup"><span data-stu-id="127e7-2612">StorageOptical</span></span></td>
 </tr>
 <tr><td>![Communications](images/segoe-mdl/e95a.png)</td>
  <td><span data-ttu-id="127e7-2614">E95A</span><span class="sxs-lookup"><span data-stu-id="127e7-2614">E95A</span></span></td>
  <td><span data-ttu-id="127e7-2615">Communications</span><span class="sxs-lookup"><span data-stu-id="127e7-2615">Communications</span></span></td>
 </tr>
 <tr><td>![Headset](images/segoe-mdl/e95b.png)</td>
  <td><span data-ttu-id="127e7-2617">E95B</span><span class="sxs-lookup"><span data-stu-id="127e7-2617">E95B</span></span></td>
  <td><span data-ttu-id="127e7-2618">Headset</span><span class="sxs-lookup"><span data-stu-id="127e7-2618">Headset</span></span></td>
 </tr>
 <tr><td>![Projector](images/segoe-mdl/e95d.png)</td>
  <td><span data-ttu-id="127e7-2620">E95D</span><span class="sxs-lookup"><span data-stu-id="127e7-2620">E95D</span></span></td>
  <td><span data-ttu-id="127e7-2621">Projector</span><span class="sxs-lookup"><span data-stu-id="127e7-2621">Projector</span></span></td>
 </tr>
 <tr><td>![Health](images/segoe-mdl/e95e.png)</td>
  <td><span data-ttu-id="127e7-2623">E95E</span><span class="sxs-lookup"><span data-stu-id="127e7-2623">E95E</span></span></td>
  <td><span data-ttu-id="127e7-2624">Health</span><span class="sxs-lookup"><span data-stu-id="127e7-2624">Health</span></span></td>
 </tr>
 <tr><td>![Webcam2](images/segoe-mdl/e960.png)</td>
  <td><span data-ttu-id="127e7-2626">E960</span><span class="sxs-lookup"><span data-stu-id="127e7-2626">E960</span></span></td>
  <td><span data-ttu-id="127e7-2627">Webcam2</span><span class="sxs-lookup"><span data-stu-id="127e7-2627">Webcam2</span></span></td>
 </tr>
 <tr><td>![Input](images/segoe-mdl/e961.png)</td>
  <td><span data-ttu-id="127e7-2629">E961</span><span class="sxs-lookup"><span data-stu-id="127e7-2629">E961</span></span></td>
  <td><span data-ttu-id="127e7-2630">Input</span><span class="sxs-lookup"><span data-stu-id="127e7-2630">Input</span></span></td>
 </tr>
 <tr><td>![Mouse](images/segoe-mdl/e962.png)</td>
  <td><span data-ttu-id="127e7-2632">E962</span><span class="sxs-lookup"><span data-stu-id="127e7-2632">E962</span></span></td>
  <td><span data-ttu-id="127e7-2633">Mouse</span><span class="sxs-lookup"><span data-stu-id="127e7-2633">Mouse</span></span></td>
 </tr>
 <tr><td>![Smartcard](images/segoe-mdl/e963.png)</td>
  <td><span data-ttu-id="127e7-2635">E963</span><span class="sxs-lookup"><span data-stu-id="127e7-2635">E963</span></span></td>
  <td><span data-ttu-id="127e7-2636">Smartcard</span><span class="sxs-lookup"><span data-stu-id="127e7-2636">Smartcard</span></span></td>
 </tr>
 <tr><td>![SmartcardVirtual](images/segoe-mdl/e964.png)</td>
  <td><span data-ttu-id="127e7-2638">E964</span><span class="sxs-lookup"><span data-stu-id="127e7-2638">E964</span></span></td>
  <td><span data-ttu-id="127e7-2639">SmartcardVirtual</span><span class="sxs-lookup"><span data-stu-id="127e7-2639">SmartcardVirtual</span></span></td>
 </tr>
 <tr><td>![MediaStorageTower](images/segoe-mdl/e965.png)</td>
  <td><span data-ttu-id="127e7-2641">E965</span><span class="sxs-lookup"><span data-stu-id="127e7-2641">E965</span></span></td>
  <td><span data-ttu-id="127e7-2642">MediaStorageTower</span><span class="sxs-lookup"><span data-stu-id="127e7-2642">MediaStorageTower</span></span></td>
 </tr>
 <tr><td>![ReturnKeySm](images/segoe-mdl/e966.png)</td>
  <td><span data-ttu-id="127e7-2644">E966</span><span class="sxs-lookup"><span data-stu-id="127e7-2644">E966</span></span></td>
  <td><span data-ttu-id="127e7-2645">ReturnKeySm</span><span class="sxs-lookup"><span data-stu-id="127e7-2645">ReturnKeySm</span></span></td>
 </tr>
 <tr><td>![GameConsole](images/segoe-mdl/e967.png)</td>
  <td><span data-ttu-id="127e7-2647">E967</span><span class="sxs-lookup"><span data-stu-id="127e7-2647">E967</span></span></td>
  <td><span data-ttu-id="127e7-2648">GameConsole</span><span class="sxs-lookup"><span data-stu-id="127e7-2648">GameConsole</span></span></td>
 </tr>
 <tr><td>![Network](images/segoe-mdl/e968.png)</td>
  <td><span data-ttu-id="127e7-2650">E968</span><span class="sxs-lookup"><span data-stu-id="127e7-2650">E968</span></span></td>
  <td><span data-ttu-id="127e7-2651">Network</span><span class="sxs-lookup"><span data-stu-id="127e7-2651">Network</span></span></td>
 </tr>
 <tr><td>![StorageNetworkWireless](images/segoe-mdl/e969.png)</td>
  <td><span data-ttu-id="127e7-2653">E969</span><span class="sxs-lookup"><span data-stu-id="127e7-2653">E969</span></span></td>
  <td><span data-ttu-id="127e7-2654">StorageNetworkWireless</span><span class="sxs-lookup"><span data-stu-id="127e7-2654">StorageNetworkWireless</span></span></td>
 </tr>
 <tr><td>![StorageTape](images/segoe-mdl/e96a.png)</td>
  <td><span data-ttu-id="127e7-2656">E96A</span><span class="sxs-lookup"><span data-stu-id="127e7-2656">E96A</span></span></td>
  <td><span data-ttu-id="127e7-2657">StorageTape</span><span class="sxs-lookup"><span data-stu-id="127e7-2657">StorageTape</span></span></td>
 </tr>
 <tr><td>![ChevronUpSmall](images/segoe-mdl/e96d.png)</td>
  <td><span data-ttu-id="127e7-2659">E96D</span><span class="sxs-lookup"><span data-stu-id="127e7-2659">E96D</span></span></td>
  <td><span data-ttu-id="127e7-2660">ChevronUpSmall</span><span class="sxs-lookup"><span data-stu-id="127e7-2660">ChevronUpSmall</span></span></td>
 </tr>
 <tr><td>![ChevronDownSmall](images/segoe-mdl/e96e.png)</td>
  <td><span data-ttu-id="127e7-2662">E96E</span><span class="sxs-lookup"><span data-stu-id="127e7-2662">E96E</span></span></td>
  <td><span data-ttu-id="127e7-2663">ChevronDownSmall</span><span class="sxs-lookup"><span data-stu-id="127e7-2663">ChevronDownSmall</span></span></td>
 </tr>
 <tr><td>![ChevronLeftSmall](images/segoe-mdl/e96f.png)</td>
  <td><span data-ttu-id="127e7-2665">E96F</span><span class="sxs-lookup"><span data-stu-id="127e7-2665">E96F</span></span></td>
  <td><span data-ttu-id="127e7-2666">ChevronLeftSmall</span><span class="sxs-lookup"><span data-stu-id="127e7-2666">ChevronLeftSmall</span></span></td>
 </tr>
 <tr><td>![ChevronRightSmall](images/segoe-mdl/e970.png)</td>
  <td><span data-ttu-id="127e7-2668">E970</span><span class="sxs-lookup"><span data-stu-id="127e7-2668">E970</span></span></td>
  <td><span data-ttu-id="127e7-2669">ChevronRightSmall</span><span class="sxs-lookup"><span data-stu-id="127e7-2669">ChevronRightSmall</span></span></td>
 </tr>
 <tr><td>![ChevronUpMed](images/segoe-mdl/e971.png)</td>
  <td><span data-ttu-id="127e7-2671">E971</span><span class="sxs-lookup"><span data-stu-id="127e7-2671">E971</span></span></td>
  <td><span data-ttu-id="127e7-2672">ChevronUpMed</span><span class="sxs-lookup"><span data-stu-id="127e7-2672">ChevronUpMed</span></span></td>
 </tr>
 <tr><td>![ChevronDownMed](images/segoe-mdl/e972.png)</td>
  <td><span data-ttu-id="127e7-2674">E972</span><span class="sxs-lookup"><span data-stu-id="127e7-2674">E972</span></span></td>
  <td><span data-ttu-id="127e7-2675">ChevronDownMed</span><span class="sxs-lookup"><span data-stu-id="127e7-2675">ChevronDownMed</span></span></td>
 </tr>
 <tr><td>![ChevronLeftMed](images/segoe-mdl/e973.png)</td>
  <td><span data-ttu-id="127e7-2677">E973</span><span class="sxs-lookup"><span data-stu-id="127e7-2677">E973</span></span></td>
  <td><span data-ttu-id="127e7-2678">ChevronLeftMed</span><span class="sxs-lookup"><span data-stu-id="127e7-2678">ChevronLeftMed</span></span></td>
 </tr>
 <tr><td>![ChevronRightMed](images/segoe-mdl/e974.png)</td>
  <td><span data-ttu-id="127e7-2680">E974</span><span class="sxs-lookup"><span data-stu-id="127e7-2680">E974</span></span></td>
  <td><span data-ttu-id="127e7-2681">ChevronRightMed</span><span class="sxs-lookup"><span data-stu-id="127e7-2681">ChevronRightMed</span></span></td>
 </tr>
 <tr><td>![Devices2](images/segoe-mdl/e975.png)</td>
  <td><span data-ttu-id="127e7-2683">E975</span><span class="sxs-lookup"><span data-stu-id="127e7-2683">E975</span></span></td>
  <td><span data-ttu-id="127e7-2684">Devices2</span><span class="sxs-lookup"><span data-stu-id="127e7-2684">Devices2</span></span></td>
 </tr>
 <tr><td>![ExpandTile](images/segoe-mdl/e976.png)</td>
  <td><span data-ttu-id="127e7-2686">E976</span><span class="sxs-lookup"><span data-stu-id="127e7-2686">E976</span></span></td>
  <td><span data-ttu-id="127e7-2687">ExpandTile</span><span class="sxs-lookup"><span data-stu-id="127e7-2687">ExpandTile</span></span></td>
 </tr>
 <tr><td>![PC1](images/segoe-mdl/e977.png)</td>
  <td><span data-ttu-id="127e7-2689">E977</span><span class="sxs-lookup"><span data-stu-id="127e7-2689">E977</span></span></td>
  <td><span data-ttu-id="127e7-2690">PC1</span><span class="sxs-lookup"><span data-stu-id="127e7-2690">PC1</span></span></td>
 </tr>
 <tr><td>![PresenceChicklet](images/segoe-mdl/e978.png)</td>
  <td><span data-ttu-id="127e7-2692">E978</span><span class="sxs-lookup"><span data-stu-id="127e7-2692">E978</span></span></td>
  <td><span data-ttu-id="127e7-2693">PresenceChicklet</span><span class="sxs-lookup"><span data-stu-id="127e7-2693">PresenceChicklet</span></span></td>
 </tr>
 <tr><td>![PresenceChickletVideo](images/segoe-mdl/e979.png)</td>
  <td><span data-ttu-id="127e7-2695">E979</span><span class="sxs-lookup"><span data-stu-id="127e7-2695">E979</span></span></td>
  <td><span data-ttu-id="127e7-2696">PresenceChickletVideo</span><span class="sxs-lookup"><span data-stu-id="127e7-2696">PresenceChickletVideo</span></span></td>
 </tr>
 <tr><td>![Reply](images/segoe-mdl/e97a.png)</td>
  <td><span data-ttu-id="127e7-2698">E97A</span><span class="sxs-lookup"><span data-stu-id="127e7-2698">E97A</span></span></td>
  <td><span data-ttu-id="127e7-2699">Reply</span><span class="sxs-lookup"><span data-stu-id="127e7-2699">Reply</span></span></td>
 </tr>
 <tr><td>![SetTile](images/segoe-mdl/e97b.png)</td>
  <td><span data-ttu-id="127e7-2701">E97B</span><span class="sxs-lookup"><span data-stu-id="127e7-2701">E97B</span></span></td>
  <td><span data-ttu-id="127e7-2702">SetTile</span><span class="sxs-lookup"><span data-stu-id="127e7-2702">SetTile</span></span></td>
 </tr>
 <tr><td>![Type](images/segoe-mdl/e97c.png)</td>
  <td><span data-ttu-id="127e7-2704">E97C</span><span class="sxs-lookup"><span data-stu-id="127e7-2704">E97C</span></span></td>
  <td><span data-ttu-id="127e7-2705">Type</span><span class="sxs-lookup"><span data-stu-id="127e7-2705">Type</span></span></td>
 </tr>
 <tr><td>![Korean](images/segoe-mdl/e97d.png)</td>
  <td><span data-ttu-id="127e7-2707">E97D</span><span class="sxs-lookup"><span data-stu-id="127e7-2707">E97D</span></span></td>
  <td><span data-ttu-id="127e7-2708">Korean</span><span class="sxs-lookup"><span data-stu-id="127e7-2708">Korean</span></span></td>
 </tr>
 <tr><td>![HalfAlpha](images/segoe-mdl/e97e.png)</td>
  <td><span data-ttu-id="127e7-2710">E97E</span><span class="sxs-lookup"><span data-stu-id="127e7-2710">E97E</span></span></td>
  <td><span data-ttu-id="127e7-2711">HalfAlpha</span><span class="sxs-lookup"><span data-stu-id="127e7-2711">HalfAlpha</span></span></td>
 </tr>
 <tr><td>![FullAlpha](images/segoe-mdl/e97f.png)</td>
  <td><span data-ttu-id="127e7-2713">E97F</span><span class="sxs-lookup"><span data-stu-id="127e7-2713">E97F</span></span></td>
  <td><span data-ttu-id="127e7-2714">FullAlpha</span><span class="sxs-lookup"><span data-stu-id="127e7-2714">FullAlpha</span></span></td>
 </tr>
 <tr><td>![Key12On](images/segoe-mdl/e980.png)</td>
  <td><span data-ttu-id="127e7-2716">E980</span><span class="sxs-lookup"><span data-stu-id="127e7-2716">E980</span></span></td>
  <td><span data-ttu-id="127e7-2717">Key12On</span><span class="sxs-lookup"><span data-stu-id="127e7-2717">Key12On</span></span></td>
 </tr>
 <tr><td>![ChineseChangjie](images/segoe-mdl/e981.png)</td>
  <td><span data-ttu-id="127e7-2719">E981</span><span class="sxs-lookup"><span data-stu-id="127e7-2719">E981</span></span></td>
  <td><span data-ttu-id="127e7-2720">ChineseChangjie</span><span class="sxs-lookup"><span data-stu-id="127e7-2720">ChineseChangjie</span></span></td>
 </tr>
 <tr><td>![QWERTYOn](images/segoe-mdl/e982.png)</td>
  <td><span data-ttu-id="127e7-2722">E982</span><span class="sxs-lookup"><span data-stu-id="127e7-2722">E982</span></span></td>
  <td><span data-ttu-id="127e7-2723">QWERTYOn</span><span class="sxs-lookup"><span data-stu-id="127e7-2723">QWERTYOn</span></span></td>
 </tr>
 <tr><td>![QWERTYOff](images/segoe-mdl/e983.png)</td>
  <td><span data-ttu-id="127e7-2725">E983</span><span class="sxs-lookup"><span data-stu-id="127e7-2725">E983</span></span></td>
  <td><span data-ttu-id="127e7-2726">QWERTYOff</span><span class="sxs-lookup"><span data-stu-id="127e7-2726">QWERTYOff</span></span></td>
 </tr>
 <tr><td>![ChineseQuick](images/segoe-mdl/e984.png)</td>
  <td><span data-ttu-id="127e7-2728">E984</span><span class="sxs-lookup"><span data-stu-id="127e7-2728">E984</span></span></td>
  <td><span data-ttu-id="127e7-2729">ChineseQuick</span><span class="sxs-lookup"><span data-stu-id="127e7-2729">ChineseQuick</span></span></td>
 </tr>
 <tr><td>![Japanese](images/segoe-mdl/e985.png)</td>
  <td><span data-ttu-id="127e7-2731">E985</span><span class="sxs-lookup"><span data-stu-id="127e7-2731">E985</span></span></td>
  <td><span data-ttu-id="127e7-2732">Japanese</span><span class="sxs-lookup"><span data-stu-id="127e7-2732">Japanese</span></span></td>
 </tr>
 <tr><td>![FullHiragana](images/segoe-mdl/e986.png)</td>
  <td><span data-ttu-id="127e7-2734">E986</span><span class="sxs-lookup"><span data-stu-id="127e7-2734">E986</span></span></td>
  <td><span data-ttu-id="127e7-2735">FullHiragana</span><span class="sxs-lookup"><span data-stu-id="127e7-2735">FullHiragana</span></span></td>
 </tr>
 <tr><td>![FullKatakana](images/segoe-mdl/e987.png)</td>
  <td><span data-ttu-id="127e7-2737">E987</span><span class="sxs-lookup"><span data-stu-id="127e7-2737">E987</span></span></td>
  <td><span data-ttu-id="127e7-2738">FullKatakana</span><span class="sxs-lookup"><span data-stu-id="127e7-2738">FullKatakana</span></span></td>
 </tr>
 <tr><td>![HalfKatakana](images/segoe-mdl/e988.png)</td>
  <td><span data-ttu-id="127e7-2740">E988</span><span class="sxs-lookup"><span data-stu-id="127e7-2740">E988</span></span></td>
  <td><span data-ttu-id="127e7-2741">HalfKatakana</span><span class="sxs-lookup"><span data-stu-id="127e7-2741">HalfKatakana</span></span></td>
 </tr>
 <tr><td>![ChineseBoPoMoFo](images/segoe-mdl/e989.png)</td>
  <td><span data-ttu-id="127e7-2743">E989</span><span class="sxs-lookup"><span data-stu-id="127e7-2743">E989</span></span></td>
  <td><span data-ttu-id="127e7-2744">ChineseBoPoMoFo</span><span class="sxs-lookup"><span data-stu-id="127e7-2744">ChineseBoPoMoFo</span></span></td>
 </tr>
 <tr><td>![ChinesePinyin](images/segoe-mdl/e98a.png)</td>
  <td><span data-ttu-id="127e7-2746">E98A</span><span class="sxs-lookup"><span data-stu-id="127e7-2746">E98A</span></span></td>
  <td><span data-ttu-id="127e7-2747">ChinesePinyin</span><span class="sxs-lookup"><span data-stu-id="127e7-2747">ChinesePinyin</span></span></td>
 </tr>
 <tr><td>![ConstructionCone](images/segoe-mdl/e98f.png)</td>
  <td><span data-ttu-id="127e7-2749">E98F</span><span class="sxs-lookup"><span data-stu-id="127e7-2749">E98F</span></span></td>
  <td><span data-ttu-id="127e7-2750">ConstructionCone</span><span class="sxs-lookup"><span data-stu-id="127e7-2750">ConstructionCone</span></span></td>
 </tr>
 <tr><td>![XboxOneConsole](images/segoe-mdl/e990.png)</td>
  <td><span data-ttu-id="127e7-2752">E990</span><span class="sxs-lookup"><span data-stu-id="127e7-2752">E990</span></span></td>
  <td><span data-ttu-id="127e7-2753">XboxOneConsole</span><span class="sxs-lookup"><span data-stu-id="127e7-2753">XboxOneConsole</span></span></td>
 </tr>
 <tr><td>![Volume0](images/segoe-mdl/e992.png)</td>
  <td><span data-ttu-id="127e7-2755">E992</span><span class="sxs-lookup"><span data-stu-id="127e7-2755">E992</span></span></td>
  <td><span data-ttu-id="127e7-2756">Volume0</span><span class="sxs-lookup"><span data-stu-id="127e7-2756">Volume0</span></span></td>
 </tr>
 <tr><td>![Volume1](images/segoe-mdl/e993.png)</td>
  <td><span data-ttu-id="127e7-2758">E993</span><span class="sxs-lookup"><span data-stu-id="127e7-2758">E993</span></span></td>
  <td><span data-ttu-id="127e7-2759">Volume1</span><span class="sxs-lookup"><span data-stu-id="127e7-2759">Volume1</span></span></td>
 </tr>
 <tr><td>![Volume2](images/segoe-mdl/e994.png)</td>
  <td><span data-ttu-id="127e7-2761">E994</span><span class="sxs-lookup"><span data-stu-id="127e7-2761">E994</span></span></td>
  <td><span data-ttu-id="127e7-2762">Volume2</span><span class="sxs-lookup"><span data-stu-id="127e7-2762">Volume2</span></span></td>
 </tr>
 <tr><td>![Volume3](images/segoe-mdl/e995.png)</td>
  <td><span data-ttu-id="127e7-2764">E995</span><span class="sxs-lookup"><span data-stu-id="127e7-2764">E995</span></span></td>
  <td><span data-ttu-id="127e7-2765">Volume3</span><span class="sxs-lookup"><span data-stu-id="127e7-2765">Volume3</span></span></td>
 </tr>
 <tr><td>![BatteryUnknown](images/segoe-mdl/e996.png)</td>
  <td><span data-ttu-id="127e7-2767">E996</span><span class="sxs-lookup"><span data-stu-id="127e7-2767">E996</span></span></td>
  <td><span data-ttu-id="127e7-2768">BatteryUnknown</span><span class="sxs-lookup"><span data-stu-id="127e7-2768">BatteryUnknown</span></span></td>
 </tr>
 <tr><td>![WifiAttentionOverlay](images/segoe-mdl/e998.png)</td>
  <td><span data-ttu-id="127e7-2770">E998</span><span class="sxs-lookup"><span data-stu-id="127e7-2770">E998</span></span></td>
  <td><span data-ttu-id="127e7-2771">WifiAttentionOverlay</span><span class="sxs-lookup"><span data-stu-id="127e7-2771">WifiAttentionOverlay</span></span></td>
 </tr>
 <tr><td>![Robot](images/segoe-mdl/e99a.png)</td>
  <td><span data-ttu-id="127e7-2773">E99A</span><span class="sxs-lookup"><span data-stu-id="127e7-2773">E99A</span></span></td>
  <td><span data-ttu-id="127e7-2774">Robot</span><span class="sxs-lookup"><span data-stu-id="127e7-2774">Robot</span></span></td>
 </tr>
 <tr><td>![TapAndSend](images/segoe-mdl/e9a1.png)</td>
  <td><span data-ttu-id="127e7-2776">E9A1</span><span class="sxs-lookup"><span data-stu-id="127e7-2776">E9A1</span></span></td>
  <td><span data-ttu-id="127e7-2777">TapAndSend</span><span class="sxs-lookup"><span data-stu-id="127e7-2777">TapAndSend</span></span></td>
 </tr>
 <tr><td>![PasswordKeyShow](images/segoe-mdl/e9a8.png)</td>
  <td><span data-ttu-id="127e7-2779">E9A8</span><span class="sxs-lookup"><span data-stu-id="127e7-2779">E9A8</span></span></td>
  <td><span data-ttu-id="127e7-2780">PasswordKeyShow</span><span class="sxs-lookup"><span data-stu-id="127e7-2780">PasswordKeyShow</span></span></td>
 </tr>
 <tr><td>![PasswordKeyHide](images/segoe-mdl/e9a9.png)</td>
  <td><span data-ttu-id="127e7-2782">E9A9</span><span class="sxs-lookup"><span data-stu-id="127e7-2782">E9A9</span></span></td>
  <td><span data-ttu-id="127e7-2783">PasswordKeyHide</span><span class="sxs-lookup"><span data-stu-id="127e7-2783">PasswordKeyHide</span></span></td>
 </tr>
 <tr><td>![BidiLtr](images/segoe-mdl/e9aa.png)</td>
  <td><span data-ttu-id="127e7-2785">E9AA</span><span class="sxs-lookup"><span data-stu-id="127e7-2785">E9AA</span></span></td>
  <td><span data-ttu-id="127e7-2786">BidiLtr</span><span class="sxs-lookup"><span data-stu-id="127e7-2786">BidiLtr</span></span></td>
 </tr>
 <tr><td>![BidiRtl](images/segoe-mdl/e9ab.png)</td>
  <td><span data-ttu-id="127e7-2788">E9AB</span><span class="sxs-lookup"><span data-stu-id="127e7-2788">E9AB</span></span></td>
  <td><span data-ttu-id="127e7-2789">BidiRtl</span><span class="sxs-lookup"><span data-stu-id="127e7-2789">BidiRtl</span></span></td>
 </tr>
 <tr><td>![ForwardSm](images/segoe-mdl/e9ac.png)</td>
  <td><span data-ttu-id="127e7-2791">E9AC</span><span class="sxs-lookup"><span data-stu-id="127e7-2791">E9AC</span></span></td>
  <td><span data-ttu-id="127e7-2792">ForwardSm</span><span class="sxs-lookup"><span data-stu-id="127e7-2792">ForwardSm</span></span></td>
 </tr>
 <tr><td>![CommaKey](images/segoe-mdl/e9ad.png)</td>
  <td><span data-ttu-id="127e7-2794">E9AD</span><span class="sxs-lookup"><span data-stu-id="127e7-2794">E9AD</span></span></td>
  <td><span data-ttu-id="127e7-2795">CommaKey</span><span class="sxs-lookup"><span data-stu-id="127e7-2795">CommaKey</span></span></td>
 </tr>
 <tr><td>![DashKey](images/segoe-mdl/e9ae.png)</td>
  <td><span data-ttu-id="127e7-2797">E9AE</span><span class="sxs-lookup"><span data-stu-id="127e7-2797">E9AE</span></span></td>
  <td><span data-ttu-id="127e7-2798">DashKey</span><span class="sxs-lookup"><span data-stu-id="127e7-2798">DashKey</span></span></td>
 </tr>
 <tr><td>![DullSoundKey](images/segoe-mdl/e9af.png)</td>
  <td><span data-ttu-id="127e7-2800">E9AF</span><span class="sxs-lookup"><span data-stu-id="127e7-2800">E9AF</span></span></td>
  <td><span data-ttu-id="127e7-2801">DullSoundKey</span><span class="sxs-lookup"><span data-stu-id="127e7-2801">DullSoundKey</span></span></td>
 </tr>
 <tr><td>![HalfDullSound](images/segoe-mdl/e9b0.png)</td>
  <td><span data-ttu-id="127e7-2803">E9B0</span><span class="sxs-lookup"><span data-stu-id="127e7-2803">E9B0</span></span></td>
  <td><span data-ttu-id="127e7-2804">HalfDullSound</span><span class="sxs-lookup"><span data-stu-id="127e7-2804">HalfDullSound</span></span></td>
 </tr>
 <tr><td>![RightDoubleQuote](images/segoe-mdl/e9b1.png)</td>
  <td><span data-ttu-id="127e7-2806">E9B1</span><span class="sxs-lookup"><span data-stu-id="127e7-2806">E9B1</span></span></td>
  <td><span data-ttu-id="127e7-2807">RightDoubleQuote</span><span class="sxs-lookup"><span data-stu-id="127e7-2807">RightDoubleQuote</span></span></td>
 </tr>
 <tr><td>![LeftDoubleQuote](images/segoe-mdl/e9b2.png)</td>
  <td><span data-ttu-id="127e7-2809">E9B2</span><span class="sxs-lookup"><span data-stu-id="127e7-2809">E9B2</span></span></td>
  <td><span data-ttu-id="127e7-2810">LeftDoubleQuote</span><span class="sxs-lookup"><span data-stu-id="127e7-2810">LeftDoubleQuote</span></span></td>
 </tr>
 <tr><td>![PuncKeyRightBottom](images/segoe-mdl/e9b3.png)</td>
  <td><span data-ttu-id="127e7-2812">E9B3</span><span class="sxs-lookup"><span data-stu-id="127e7-2812">E9B3</span></span></td>
  <td><span data-ttu-id="127e7-2813">PuncKeyRightBottom</span><span class="sxs-lookup"><span data-stu-id="127e7-2813">PuncKeyRightBottom</span></span></td>
 </tr>
 <tr><td>![PuncKey1](images/segoe-mdl/e9b4.png)</td>
  <td><span data-ttu-id="127e7-2815">E9B4</span><span class="sxs-lookup"><span data-stu-id="127e7-2815">E9B4</span></span></td>
  <td><span data-ttu-id="127e7-2816">PuncKey1</span><span class="sxs-lookup"><span data-stu-id="127e7-2816">PuncKey1</span></span></td>
 </tr>
 <tr><td>![PuncKey2](images/segoe-mdl/e9b5.png)</td>
  <td><span data-ttu-id="127e7-2818">E9B5</span><span class="sxs-lookup"><span data-stu-id="127e7-2818">E9B5</span></span></td>
  <td><span data-ttu-id="127e7-2819">PuncKey2</span><span class="sxs-lookup"><span data-stu-id="127e7-2819">PuncKey2</span></span></td>
 </tr>
 <tr><td>![PuncKey3](images/segoe-mdl/e9b6.png)</td>
  <td><span data-ttu-id="127e7-2821">E9B6</span><span class="sxs-lookup"><span data-stu-id="127e7-2821">E9B6</span></span></td>
  <td><span data-ttu-id="127e7-2822">PuncKey3</span><span class="sxs-lookup"><span data-stu-id="127e7-2822">PuncKey3</span></span></td>
 </tr>
 <tr><td>![PuncKey4](images/segoe-mdl/e9b7.png)</td>
  <td><span data-ttu-id="127e7-2824">E9B7</span><span class="sxs-lookup"><span data-stu-id="127e7-2824">E9B7</span></span></td>
  <td><span data-ttu-id="127e7-2825">PuncKey4</span><span class="sxs-lookup"><span data-stu-id="127e7-2825">PuncKey4</span></span></td>
 </tr>
 <tr><td>![PuncKey5](images/segoe-mdl/e9b8.png)</td>
  <td><span data-ttu-id="127e7-2827">E9B8</span><span class="sxs-lookup"><span data-stu-id="127e7-2827">E9B8</span></span></td>
  <td><span data-ttu-id="127e7-2828">PuncKey5</span><span class="sxs-lookup"><span data-stu-id="127e7-2828">PuncKey5</span></span></td>
 </tr>
 <tr><td>![PuncKey6](images/segoe-mdl/e9b9.png)</td>
  <td><span data-ttu-id="127e7-2830">E9B9</span><span class="sxs-lookup"><span data-stu-id="127e7-2830">E9B9</span></span></td>
  <td><span data-ttu-id="127e7-2831">PuncKey6</span><span class="sxs-lookup"><span data-stu-id="127e7-2831">PuncKey6</span></span></td>
 </tr>
 <tr><td>![PuncKey9](images/segoe-mdl/e9ba.png)</td>
  <td><span data-ttu-id="127e7-2833">E9BA</span><span class="sxs-lookup"><span data-stu-id="127e7-2833">E9BA</span></span></td>
  <td><span data-ttu-id="127e7-2834">PuncKey9</span><span class="sxs-lookup"><span data-stu-id="127e7-2834">PuncKey9</span></span></td>
 </tr>
 <tr><td>![PuncKey7](images/segoe-mdl/e9bb.png)</td>
  <td><span data-ttu-id="127e7-2836">E9BB</span><span class="sxs-lookup"><span data-stu-id="127e7-2836">E9BB</span></span></td>
  <td><span data-ttu-id="127e7-2837">PuncKey7</span><span class="sxs-lookup"><span data-stu-id="127e7-2837">PuncKey7</span></span></td>
 </tr>
 <tr><td>![PuncKey8](images/segoe-mdl/e9bc.png)</td>
  <td><span data-ttu-id="127e7-2839">E9BC</span><span class="sxs-lookup"><span data-stu-id="127e7-2839">E9BC</span></span></td>
  <td><span data-ttu-id="127e7-2840">PuncKey8</span><span class="sxs-lookup"><span data-stu-id="127e7-2840">PuncKey8</span></span></td>
 </tr>
 <tr><td>![Frigid](images/segoe-mdl/e9ca.png)</td>
  <td><span data-ttu-id="127e7-2842">E9CA</span><span class="sxs-lookup"><span data-stu-id="127e7-2842">E9CA</span></span></td>
  <td><span data-ttu-id="127e7-2843">Frigid</span><span class="sxs-lookup"><span data-stu-id="127e7-2843">Frigid</span></span></td>
 </tr>
 <tr><td>![Diagnostic](images/segoe-mdl/e9d9.png)</td>
  <td><span data-ttu-id="127e7-2845">E9D9</span><span class="sxs-lookup"><span data-stu-id="127e7-2845">E9D9</span></span></td>
  <td><span data-ttu-id="127e7-2846">Diagnostic</span><span class="sxs-lookup"><span data-stu-id="127e7-2846">Diagnostic</span></span></td>
 </tr>
 <tr><td>![Process](images/segoe-mdl/e9f3.png)</td>
  <td><span data-ttu-id="127e7-2848">E9F3</span><span class="sxs-lookup"><span data-stu-id="127e7-2848">E9F3</span></span></td>
  <td><span data-ttu-id="127e7-2849">Process</span><span class="sxs-lookup"><span data-stu-id="127e7-2849">Process</span></span></td>
 </tr>
 <tr><td>![DisconnectDisplay](images/segoe-mdl/ea14.png)</td>
  <td><span data-ttu-id="127e7-2851">EA14</span><span class="sxs-lookup"><span data-stu-id="127e7-2851">EA14</span></span></td>
  <td><span data-ttu-id="127e7-2852">DisconnectDisplay</span><span class="sxs-lookup"><span data-stu-id="127e7-2852">DisconnectDisplay</span></span></td>
 </tr>
 <tr><td>![Info2](images/segoe-mdl/ea1f.png)</td>
  <td><span data-ttu-id="127e7-2854">EA1F</span><span class="sxs-lookup"><span data-stu-id="127e7-2854">EA1F</span></span></td>
  <td><span data-ttu-id="127e7-2855">Info2</span><span class="sxs-lookup"><span data-stu-id="127e7-2855">Info2</span></span></td>
 </tr>
 <tr><td>![ActionCenterAsterisk](images/segoe-mdl/ea21.png)</td>
  <td><span data-ttu-id="127e7-2857">EA21</span><span class="sxs-lookup"><span data-stu-id="127e7-2857">EA21</span></span></td>
  <td><span data-ttu-id="127e7-2858">ActionCenterAsterisk</span><span class="sxs-lookup"><span data-stu-id="127e7-2858">ActionCenterAsterisk</span></span></td>
 </tr>
 <tr><td>![Beta](images/segoe-mdl/ea24.png)</td>
  <td><span data-ttu-id="127e7-2860">EA24</span><span class="sxs-lookup"><span data-stu-id="127e7-2860">EA24</span></span></td>
  <td><span data-ttu-id="127e7-2861">Beta</span><span class="sxs-lookup"><span data-stu-id="127e7-2861">Beta</span></span></td>
 </tr>
 <tr><td>![SaveCopy](images/segoe-mdl/ea35.png)</td>
  <td><span data-ttu-id="127e7-2863">EA35</span><span class="sxs-lookup"><span data-stu-id="127e7-2863">EA35</span></span></td>
  <td><span data-ttu-id="127e7-2864">SaveCopy</span><span class="sxs-lookup"><span data-stu-id="127e7-2864">SaveCopy</span></span></td>
 </tr>
 <tr><td>![List](images/segoe-mdl/ea37.png)</td>
  <td><span data-ttu-id="127e7-2866">EA37</span><span class="sxs-lookup"><span data-stu-id="127e7-2866">EA37</span></span></td>
  <td><span data-ttu-id="127e7-2867">List</span><span class="sxs-lookup"><span data-stu-id="127e7-2867">List</span></span></td>
 </tr>
 <tr><td>![Asterisk](images/segoe-mdl/ea38.png)</td>
  <td><span data-ttu-id="127e7-2869">EA38</span><span class="sxs-lookup"><span data-stu-id="127e7-2869">EA38</span></span></td>
  <td><span data-ttu-id="127e7-2870">Asterisk</span><span class="sxs-lookup"><span data-stu-id="127e7-2870">Asterisk</span></span></td>
 </tr>
 <tr><td>![ErrorBadge](images/segoe-mdl/ea39.png)</td>
  <td><span data-ttu-id="127e7-2872">EA39</span><span class="sxs-lookup"><span data-stu-id="127e7-2872">EA39</span></span></td>
  <td><span data-ttu-id="127e7-2873">ErrorBadge</span><span class="sxs-lookup"><span data-stu-id="127e7-2873">ErrorBadge</span></span></td>
 </tr>
 <tr><td>![CircleRing](images/segoe-mdl/ea3a.png)</td>
  <td><span data-ttu-id="127e7-2875">EA3A</span><span class="sxs-lookup"><span data-stu-id="127e7-2875">EA3A</span></span></td>
  <td><span data-ttu-id="127e7-2876">CircleRing</span><span class="sxs-lookup"><span data-stu-id="127e7-2876">CircleRing</span></span></td>
 </tr>
 <tr><td>![CircleFill](images/segoe-mdl/ea3b.png)</td>
  <td><span data-ttu-id="127e7-2878">EA3B</span><span class="sxs-lookup"><span data-stu-id="127e7-2878">EA3B</span></span></td>
  <td><span data-ttu-id="127e7-2879">CircleFill</span><span class="sxs-lookup"><span data-stu-id="127e7-2879">CircleFill</span></span></td>
 </tr>
 <tr><td>![AllAppsMirrored](images/segoe-mdl/ea40.png)</td>
  <td><span data-ttu-id="127e7-2881">EA40</span><span class="sxs-lookup"><span data-stu-id="127e7-2881">EA40</span></span></td>
  <td><span data-ttu-id="127e7-2882">AllAppsMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-2882">AllAppsMirrored</span></span></td>
 </tr>
 <tr><td>![BookmarksMirrored](images/segoe-mdl/ea41.png)</td>
  <td><span data-ttu-id="127e7-2884">EA41</span><span class="sxs-lookup"><span data-stu-id="127e7-2884">EA41</span></span></td>
  <td><span data-ttu-id="127e7-2885">BookmarksMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-2885">BookmarksMirrored</span></span></td>
 </tr>
 <tr><td>![BulletedListMirrored](images/segoe-mdl/ea42.png)</td>
  <td><span data-ttu-id="127e7-2887">EA42</span><span class="sxs-lookup"><span data-stu-id="127e7-2887">EA42</span></span></td>
  <td><span data-ttu-id="127e7-2888">BulletedListMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-2888">BulletedListMirrored</span></span></td>
 </tr>
 <tr><td>![CallForwardInternationalMirrored](images/segoe-mdl/ea43.png)</td>
  <td><span data-ttu-id="127e7-2890">EA43</span><span class="sxs-lookup"><span data-stu-id="127e7-2890">EA43</span></span></td>
  <td><span data-ttu-id="127e7-2891">CallForwardInternationalMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-2891">CallForwardInternationalMirrored</span></span></td>
 </tr>
 <tr><td>![CallForwardRoamingMirrored](images/segoe-mdl/ea44.png)</td>
  <td><span data-ttu-id="127e7-2893">EA44</span><span class="sxs-lookup"><span data-stu-id="127e7-2893">EA44</span></span></td>
  <td><span data-ttu-id="127e7-2894">CallForwardRoamingMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-2894">CallForwardRoamingMirrored</span></span></td>
 </tr>
 <tr><td>![ChromeBackMirrored](images/segoe-mdl/ea47.png)</td>
  <td><span data-ttu-id="127e7-2896">EA47</span><span class="sxs-lookup"><span data-stu-id="127e7-2896">EA47</span></span></td>
  <td><span data-ttu-id="127e7-2897">ChromeBackMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-2897">ChromeBackMirrored</span></span></td>
 </tr>
 <tr><td>![ClearSelectionMirrored](images/segoe-mdl/ea48.png)</td>
  <td><span data-ttu-id="127e7-2899">EA48</span><span class="sxs-lookup"><span data-stu-id="127e7-2899">EA48</span></span></td>
  <td><span data-ttu-id="127e7-2900">ClearSelectionMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-2900">ClearSelectionMirrored</span></span></td>
 </tr>
 <tr><td>![ClosePaneMirrored](images/segoe-mdl/ea49.png)</td>
  <td><span data-ttu-id="127e7-2902">EA49</span><span class="sxs-lookup"><span data-stu-id="127e7-2902">EA49</span></span></td>
  <td><span data-ttu-id="127e7-2903">ClosePaneMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-2903">ClosePaneMirrored</span></span></td>
 </tr>
 <tr><td>![ContactInfoMirrored](images/segoe-mdl/ea4a.png)</td>
  <td><span data-ttu-id="127e7-2905">EA4A</span><span class="sxs-lookup"><span data-stu-id="127e7-2905">EA4A</span></span></td>
  <td><span data-ttu-id="127e7-2906">ContactInfoMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-2906">ContactInfoMirrored</span></span></td>
 </tr>
 <tr><td>![DockRightMirrored](images/segoe-mdl/ea4b.png)</td>
  <td><span data-ttu-id="127e7-2908">EA4B</span><span class="sxs-lookup"><span data-stu-id="127e7-2908">EA4B</span></span></td>
  <td><span data-ttu-id="127e7-2909">DockRightMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-2909">DockRightMirrored</span></span></td>
 </tr>
 <tr><td>![DockLeftMirrored](images/segoe-mdl/ea4c.png)</td>
  <td><span data-ttu-id="127e7-2911">EA4C</span><span class="sxs-lookup"><span data-stu-id="127e7-2911">EA4C</span></span></td>
  <td><span data-ttu-id="127e7-2912">DockLeftMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-2912">DockLeftMirrored</span></span></td>
 </tr>
 <tr><td>![ExpandTileMirrored](images/segoe-mdl/ea4e.png)</td>
  <td><span data-ttu-id="127e7-2914">EA4E</span><span class="sxs-lookup"><span data-stu-id="127e7-2914">EA4E</span></span></td>
  <td><span data-ttu-id="127e7-2915">ExpandTileMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-2915">ExpandTileMirrored</span></span></td>
 </tr>
 <tr><td>![GoMirrored](images/segoe-mdl/ea4f.png)</td>
  <td><span data-ttu-id="127e7-2917">EA4F</span><span class="sxs-lookup"><span data-stu-id="127e7-2917">EA4F</span></span></td>
  <td><span data-ttu-id="127e7-2918">GoMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-2918">GoMirrored</span></span></td>
 </tr>
 <tr><td>![GripperResizeMirrored](images/segoe-mdl/ea50.png)</td>
  <td><span data-ttu-id="127e7-2920">EA50</span><span class="sxs-lookup"><span data-stu-id="127e7-2920">EA50</span></span></td>
  <td><span data-ttu-id="127e7-2921">GripperResizeMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-2921">GripperResizeMirrored</span></span></td>
 </tr>
 <tr><td>![HelpMirrored](images/segoe-mdl/ea51.png)</td>
  <td><span data-ttu-id="127e7-2923">EA51</span><span class="sxs-lookup"><span data-stu-id="127e7-2923">EA51</span></span></td>
  <td><span data-ttu-id="127e7-2924">HelpMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-2924">HelpMirrored</span></span></td>
 </tr>
 <tr><td>![ImportMirrored](images/segoe-mdl/ea52.png)</td>
  <td><span data-ttu-id="127e7-2926">EA52</span><span class="sxs-lookup"><span data-stu-id="127e7-2926">EA52</span></span></td>
  <td><span data-ttu-id="127e7-2927">ImportMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-2927">ImportMirrored</span></span></td>
 </tr>
 <tr><td>![ImportAllMirrored](images/segoe-mdl/ea53.png)</td>
  <td><span data-ttu-id="127e7-2929">EA53</span><span class="sxs-lookup"><span data-stu-id="127e7-2929">EA53</span></span></td>
  <td><span data-ttu-id="127e7-2930">ImportAllMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-2930">ImportAllMirrored</span></span></td>
 </tr>
 <tr><td>![LeaveChatMirrored](images/segoe-mdl/ea54.png)</td>
  <td><span data-ttu-id="127e7-2932">EA54</span><span class="sxs-lookup"><span data-stu-id="127e7-2932">EA54</span></span></td>
  <td><span data-ttu-id="127e7-2933">LeaveChatMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-2933">LeaveChatMirrored</span></span></td>
 </tr>
 <tr><td>![ListMirrored](images/segoe-mdl/ea55.png)</td>
  <td><span data-ttu-id="127e7-2935">EA55</span><span class="sxs-lookup"><span data-stu-id="127e7-2935">EA55</span></span></td>
  <td><span data-ttu-id="127e7-2936">ListMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-2936">ListMirrored</span></span></td>
 </tr>
 <tr><td>![MailForwardMirrored](images/segoe-mdl/ea56.png)</td>
  <td><span data-ttu-id="127e7-2938">EA56</span><span class="sxs-lookup"><span data-stu-id="127e7-2938">EA56</span></span></td>
  <td><span data-ttu-id="127e7-2939">MailForwardMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-2939">MailForwardMirrored</span></span></td>
 </tr>
 <tr><td>![MailReplyMirrored](images/segoe-mdl/ea57.png)</td>
  <td><span data-ttu-id="127e7-2941">EA57</span><span class="sxs-lookup"><span data-stu-id="127e7-2941">EA57</span></span></td>
  <td><span data-ttu-id="127e7-2942">MailReplyMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-2942">MailReplyMirrored</span></span></td>
 </tr>
 <tr><td>![MailReplyAllMirrored](images/segoe-mdl/ea58.png)</td>
  <td><span data-ttu-id="127e7-2944">EA58</span><span class="sxs-lookup"><span data-stu-id="127e7-2944">EA58</span></span></td>
  <td><span data-ttu-id="127e7-2945">MailReplyAllMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-2945">MailReplyAllMirrored</span></span></td>
 </tr>
 <tr><td>![OpenPaneMirrored](images/segoe-mdl/ea5b.png)</td>
  <td><span data-ttu-id="127e7-2947">EA5B</span><span class="sxs-lookup"><span data-stu-id="127e7-2947">EA5B</span></span></td>
  <td><span data-ttu-id="127e7-2948">OpenPaneMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-2948">OpenPaneMirrored</span></span></td>
 </tr>
 <tr><td>![OpenWithMirrored](images/segoe-mdl/ea5c.png)</td>
  <td><span data-ttu-id="127e7-2950">EA5C</span><span class="sxs-lookup"><span data-stu-id="127e7-2950">EA5C</span></span></td>
  <td><span data-ttu-id="127e7-2951">OpenWithMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-2951">OpenWithMirrored</span></span></td>
 </tr>
 <tr><td>![ParkingLocationMirrored](images/segoe-mdl/ea5e.png)</td>
  <td><span data-ttu-id="127e7-2953">EA5E</span><span class="sxs-lookup"><span data-stu-id="127e7-2953">EA5E</span></span></td>
  <td><span data-ttu-id="127e7-2954">ParkingLocationMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-2954">ParkingLocationMirrored</span></span></td>
 </tr>
 <tr><td>![ResizeMouseMediumMirrored](images/segoe-mdl/ea5f.png)</td>
  <td><span data-ttu-id="127e7-2956">EA5F</span><span class="sxs-lookup"><span data-stu-id="127e7-2956">EA5F</span></span></td>
  <td><span data-ttu-id="127e7-2957">ResizeMouseMediumMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-2957">ResizeMouseMediumMirrored</span></span></td>
 </tr>
 <tr><td>![ResizeMouseSmallMirrored](images/segoe-mdl/ea60.png)</td>
  <td><span data-ttu-id="127e7-2959">EA60</span><span class="sxs-lookup"><span data-stu-id="127e7-2959">EA60</span></span></td>
  <td><span data-ttu-id="127e7-2960">ResizeMouseSmallMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-2960">ResizeMouseSmallMirrored</span></span></td>
 </tr>
 <tr><td>![ResizeMouseTallMirrored](images/segoe-mdl/ea61.png)</td>
  <td><span data-ttu-id="127e7-2962">EA61</span><span class="sxs-lookup"><span data-stu-id="127e7-2962">EA61</span></span></td>
  <td><span data-ttu-id="127e7-2963">ResizeMouseTallMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-2963">ResizeMouseTallMirrored</span></span></td>
 </tr>
 <tr><td>![ResizeTouchNarrowerMirrored](images/segoe-mdl/ea62.png)</td>
  <td><span data-ttu-id="127e7-2965">EA62</span><span class="sxs-lookup"><span data-stu-id="127e7-2965">EA62</span></span></td>
  <td><span data-ttu-id="127e7-2966">ResizeTouchNarrowerMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-2966">ResizeTouchNarrowerMirrored</span></span></td>
 </tr>
 <tr><td>![SendMirrored](images/segoe-mdl/ea63.png)</td>
  <td><span data-ttu-id="127e7-2968">EA63</span><span class="sxs-lookup"><span data-stu-id="127e7-2968">EA63</span></span></td>
  <td><span data-ttu-id="127e7-2969">SendMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-2969">SendMirrored</span></span></td>
 </tr>
 <tr><td>![SendFillMirrored](images/segoe-mdl/ea64.png)</td>
  <td><span data-ttu-id="127e7-2971">EA64</span><span class="sxs-lookup"><span data-stu-id="127e7-2971">EA64</span></span></td>
  <td><span data-ttu-id="127e7-2972">SendFillMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-2972">SendFillMirrored</span></span></td>
 </tr>
 <tr><td>![ShowResultsMirrored](images/segoe-mdl/ea65.png)</td>
  <td><span data-ttu-id="127e7-2974">EA65</span><span class="sxs-lookup"><span data-stu-id="127e7-2974">EA65</span></span></td>
  <td><span data-ttu-id="127e7-2975">ShowResultsMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-2975">ShowResultsMirrored</span></span></td>
 </tr>
 <tr><td>![Media](images/segoe-mdl/ea69.png)</td>
  <td><span data-ttu-id="127e7-2977">EA69</span><span class="sxs-lookup"><span data-stu-id="127e7-2977">EA69</span></span></td>
  <td><span data-ttu-id="127e7-2978">Media</span><span class="sxs-lookup"><span data-stu-id="127e7-2978">Media</span></span></td>
 </tr>
 <tr><td>![SyncError](images/segoe-mdl/ea6a.png)</td>
  <td><span data-ttu-id="127e7-2980">EA6A</span><span class="sxs-lookup"><span data-stu-id="127e7-2980">EA6A</span></span></td>
  <td><span data-ttu-id="127e7-2981">SyncError</span><span class="sxs-lookup"><span data-stu-id="127e7-2981">SyncError</span></span></td>
 </tr>
 <tr><td>![Devices3](images/segoe-mdl/ea6c.png)</td>
  <td><span data-ttu-id="127e7-2983">EA6C</span><span class="sxs-lookup"><span data-stu-id="127e7-2983">EA6C</span></span></td>
  <td><span data-ttu-id="127e7-2984">Devices3</span><span class="sxs-lookup"><span data-stu-id="127e7-2984">Devices3</span></span></td>
 </tr>
 <tr><td>![Lightbulb](images/segoe-mdl/ea80.png)</td>
  <td><span data-ttu-id="127e7-2986">EA80</span><span class="sxs-lookup"><span data-stu-id="127e7-2986">EA80</span></span></td>
  <td><span data-ttu-id="127e7-2987">Lightbulb</span><span class="sxs-lookup"><span data-stu-id="127e7-2987">Lightbulb</span></span></td>
 </tr>
 <tr><td>![StatusCircle](images/segoe-mdl/ea81.png)</td>
  <td><span data-ttu-id="127e7-2989">EA81</span><span class="sxs-lookup"><span data-stu-id="127e7-2989">EA81</span></span></td>
  <td><span data-ttu-id="127e7-2990">StatusCircle</span><span class="sxs-lookup"><span data-stu-id="127e7-2990">StatusCircle</span></span></td>
 </tr>
 <tr><td>![StatusTriangle](images/segoe-mdl/ea82.png)</td>
  <td><span data-ttu-id="127e7-2992">EA82</span><span class="sxs-lookup"><span data-stu-id="127e7-2992">EA82</span></span></td>
  <td><span data-ttu-id="127e7-2993">StatusTriangle</span><span class="sxs-lookup"><span data-stu-id="127e7-2993">StatusTriangle</span></span></td>
 </tr>
 <tr><td>![StatusError](images/segoe-mdl/ea83.png)</td>
  <td><span data-ttu-id="127e7-2995">EA83</span><span class="sxs-lookup"><span data-stu-id="127e7-2995">EA83</span></span></td>
  <td><span data-ttu-id="127e7-2996">StatusError</span><span class="sxs-lookup"><span data-stu-id="127e7-2996">StatusError</span></span></td>
 </tr>
 <tr><td>![StatusWarning](images/segoe-mdl/ea84.png)</td>
  <td><span data-ttu-id="127e7-2998">EA84</span><span class="sxs-lookup"><span data-stu-id="127e7-2998">EA84</span></span></td>
  <td><span data-ttu-id="127e7-2999">StatusWarning</span><span class="sxs-lookup"><span data-stu-id="127e7-2999">StatusWarning</span></span></td>
 </tr>
 <tr><td>![Puzzle](images/segoe-mdl/ea86.png)</td>
  <td><span data-ttu-id="127e7-3001">EA86</span><span class="sxs-lookup"><span data-stu-id="127e7-3001">EA86</span></span></td>
  <td><span data-ttu-id="127e7-3002">Puzzle</span><span class="sxs-lookup"><span data-stu-id="127e7-3002">Puzzle</span></span></td>
 </tr>
 <tr><td>![CalendarSolid](images/segoe-mdl/ea89.png)</td>
  <td><span data-ttu-id="127e7-3004">EA89</span><span class="sxs-lookup"><span data-stu-id="127e7-3004">EA89</span></span></td>
  <td><span data-ttu-id="127e7-3005">CalendarSolid</span><span class="sxs-lookup"><span data-stu-id="127e7-3005">CalendarSolid</span></span></td>
 </tr>
 <tr><td>![HomeSolid](images/segoe-mdl/ea8a.png)</td>
  <td><span data-ttu-id="127e7-3007">EA8A</span><span class="sxs-lookup"><span data-stu-id="127e7-3007">EA8A</span></span></td>
  <td><span data-ttu-id="127e7-3008">HomeSolid</span><span class="sxs-lookup"><span data-stu-id="127e7-3008">HomeSolid</span></span></td>
 </tr>
 <tr><td>![ParkingLocationSolid](images/segoe-mdl/ea8b.png)</td>
  <td><span data-ttu-id="127e7-3010">EA8B</span><span class="sxs-lookup"><span data-stu-id="127e7-3010">EA8B</span></span></td>
  <td><span data-ttu-id="127e7-3011">ParkingLocationSolid</span><span class="sxs-lookup"><span data-stu-id="127e7-3011">ParkingLocationSolid</span></span></td>
 </tr>
 <tr><td>![ContactSolid](images/segoe-mdl/ea8c.png)</td>
  <td><span data-ttu-id="127e7-3013">EA8C</span><span class="sxs-lookup"><span data-stu-id="127e7-3013">EA8C</span></span></td>
  <td><span data-ttu-id="127e7-3014">ContactSolid</span><span class="sxs-lookup"><span data-stu-id="127e7-3014">ContactSolid</span></span></td>
 </tr>
 <tr><td>![ConstructionSolid](images/segoe-mdl/ea8d.png)</td>
  <td><span data-ttu-id="127e7-3016">EA8D</span><span class="sxs-lookup"><span data-stu-id="127e7-3016">EA8D</span></span></td>
  <td><span data-ttu-id="127e7-3017">ConstructionSolid</span><span class="sxs-lookup"><span data-stu-id="127e7-3017">ConstructionSolid</span></span></td>
 </tr>
 <tr><td>![AccidentSolid](images/segoe-mdl/ea8e.png)</td>
  <td><span data-ttu-id="127e7-3019">EA8E</span><span class="sxs-lookup"><span data-stu-id="127e7-3019">EA8E</span></span></td>
  <td><span data-ttu-id="127e7-3020">AccidentSolid</span><span class="sxs-lookup"><span data-stu-id="127e7-3020">AccidentSolid</span></span></td>
 </tr>
 <tr><td>![Ringer](images/segoe-mdl/ea8f.png)</td>
  <td><span data-ttu-id="127e7-3022">EA8F</span><span class="sxs-lookup"><span data-stu-id="127e7-3022">EA8F</span></span></td>
  <td><span data-ttu-id="127e7-3023">Ringer</span><span class="sxs-lookup"><span data-stu-id="127e7-3023">Ringer</span></span></td>
 </tr>
 <tr><td>![ThoughtBubble](images/segoe-mdl/ea91.png)</td>
  <td><span data-ttu-id="127e7-3025">EA91</span><span class="sxs-lookup"><span data-stu-id="127e7-3025">EA91</span></span></td>
  <td><span data-ttu-id="127e7-3026">ThoughtBubble</span><span class="sxs-lookup"><span data-stu-id="127e7-3026">ThoughtBubble</span></span></td>
 </tr>
 <tr><td>![HeartBroken](images/segoe-mdl/ea92.png)</td>
  <td><span data-ttu-id="127e7-3028">EA92</span><span class="sxs-lookup"><span data-stu-id="127e7-3028">EA92</span></span></td>
  <td><span data-ttu-id="127e7-3029">HeartBroken</span><span class="sxs-lookup"><span data-stu-id="127e7-3029">HeartBroken</span></span></td>
 </tr>
 <tr><td>![BatteryCharging10](images/segoe-mdl/ea93.png)</td>
  <td><span data-ttu-id="127e7-3031">EA93</span><span class="sxs-lookup"><span data-stu-id="127e7-3031">EA93</span></span></td>
  <td><span data-ttu-id="127e7-3032">BatteryCharging10</span><span class="sxs-lookup"><span data-stu-id="127e7-3032">BatteryCharging10</span></span></td>
 </tr>
 <tr><td>![BatterySaver9](images/segoe-mdl/ea94.png)</td>
  <td><span data-ttu-id="127e7-3034">EA94</span><span class="sxs-lookup"><span data-stu-id="127e7-3034">EA94</span></span></td>
  <td><span data-ttu-id="127e7-3035">BatterySaver9</span><span class="sxs-lookup"><span data-stu-id="127e7-3035">BatterySaver9</span></span></td>
 </tr>
 <tr><td>![BatterySaver10](images/segoe-mdl/ea95.png)</td>
  <td><span data-ttu-id="127e7-3037">EA95</span><span class="sxs-lookup"><span data-stu-id="127e7-3037">EA95</span></span></td>
  <td><span data-ttu-id="127e7-3038">BatterySaver10</span><span class="sxs-lookup"><span data-stu-id="127e7-3038">BatterySaver10</span></span></td>
 </tr>
 <tr><td>![CallForwardingMirrored](images/segoe-mdl/ea97.png)</td>
  <td><span data-ttu-id="127e7-3040">EA97</span><span class="sxs-lookup"><span data-stu-id="127e7-3040">EA97</span></span></td>
  <td><span data-ttu-id="127e7-3041">CallForwardingMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-3041">CallForwardingMirrored</span></span></td>
 </tr>
 <tr><td>![MultiSelectMirrored](images/segoe-mdl/ea98.png)</td>
  <td><span data-ttu-id="127e7-3043">EA98</span><span class="sxs-lookup"><span data-stu-id="127e7-3043">EA98</span></span></td>
  <td><span data-ttu-id="127e7-3044">MultiSelectMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-3044">MultiSelectMirrored</span></span></td>
 </tr>
 <tr><td>![Broom](images/segoe-mdl/ea99.png)</td>
  <td><span data-ttu-id="127e7-3046">EA99</span><span class="sxs-lookup"><span data-stu-id="127e7-3046">EA99</span></span></td>
  <td><span data-ttu-id="127e7-3047">Broom</span><span class="sxs-lookup"><span data-stu-id="127e7-3047">Broom</span></span></td>
 </tr>
 <tr><td>![Trackers](images/segoe-mdl/eadf.png)</td>
  <td><span data-ttu-id="127e7-3049">EADF</span><span class="sxs-lookup"><span data-stu-id="127e7-3049">EADF</span></span></td>
  <td><span data-ttu-id="127e7-3050">Trackers</span><span class="sxs-lookup"><span data-stu-id="127e7-3050">Trackers</span></span></td>
 </tr>
 <tr><td>![PieSingle](images/segoe-mdl/eb05.png)</td>
  <td><span data-ttu-id="127e7-3052">EB05</span><span class="sxs-lookup"><span data-stu-id="127e7-3052">EB05</span></span></td>
  <td><span data-ttu-id="127e7-3053">PieSingle</span><span class="sxs-lookup"><span data-stu-id="127e7-3053">PieSingle</span></span></td>
 </tr>
 <tr><td>![StockDown](images/segoe-mdl/eb0f.png)</td>
  <td><span data-ttu-id="127e7-3055">EB0F</span><span class="sxs-lookup"><span data-stu-id="127e7-3055">EB0F</span></span></td>
  <td><span data-ttu-id="127e7-3056">StockDown</span><span class="sxs-lookup"><span data-stu-id="127e7-3056">StockDown</span></span></td>
 </tr>
 <tr><td>![StockUp](images/segoe-mdl/eb11.png)</td>
  <td><span data-ttu-id="127e7-3058">EB11</span><span class="sxs-lookup"><span data-stu-id="127e7-3058">EB11</span></span></td>
  <td><span data-ttu-id="127e7-3059">StockUp</span><span class="sxs-lookup"><span data-stu-id="127e7-3059">StockUp</span></span></td>
 </tr>
 <tr><td>![Drop](images/segoe-mdl/eb42.png)</td>
  <td><span data-ttu-id="127e7-3061">EB42</span><span class="sxs-lookup"><span data-stu-id="127e7-3061">EB42</span></span></td>
  <td><span data-ttu-id="127e7-3062">Drop</span><span class="sxs-lookup"><span data-stu-id="127e7-3062">Drop</span></span></td>
 </tr>
 <tr><td>![BusSolid](images/segoe-mdl/eb47.png)</td>
  <td><span data-ttu-id="127e7-3064">EB47</span><span class="sxs-lookup"><span data-stu-id="127e7-3064">EB47</span></span></td>
  <td><span data-ttu-id="127e7-3065">BusSolid</span><span class="sxs-lookup"><span data-stu-id="127e7-3065">BusSolid</span></span></td>
 </tr>
 <tr><td>![FerrySolid](images/segoe-mdl/eb48.png)</td>
  <td><span data-ttu-id="127e7-3067">EB48</span><span class="sxs-lookup"><span data-stu-id="127e7-3067">EB48</span></span></td>
  <td><span data-ttu-id="127e7-3068">FerrySolid</span><span class="sxs-lookup"><span data-stu-id="127e7-3068">FerrySolid</span></span></td>
 </tr>
 <tr><td>![StartPointSolid](images/segoe-mdl/eb49.png)</td>
  <td><span data-ttu-id="127e7-3070">EB49</span><span class="sxs-lookup"><span data-stu-id="127e7-3070">EB49</span></span></td>
  <td><span data-ttu-id="127e7-3071">StartPointSolid</span><span class="sxs-lookup"><span data-stu-id="127e7-3071">StartPointSolid</span></span></td>
 </tr>
 <tr><td>![StopPointSolid](images/segoe-mdl/eb4a.png)</td>
  <td><span data-ttu-id="127e7-3073">EB4A</span><span class="sxs-lookup"><span data-stu-id="127e7-3073">EB4A</span></span></td>
  <td><span data-ttu-id="127e7-3074">StopPointSolid</span><span class="sxs-lookup"><span data-stu-id="127e7-3074">StopPointSolid</span></span></td>
 </tr>
 <tr><td>![EndPointSolid](images/segoe-mdl/eb4b.png)</td>
  <td><span data-ttu-id="127e7-3076">EB4B</span><span class="sxs-lookup"><span data-stu-id="127e7-3076">EB4B</span></span></td>
  <td><span data-ttu-id="127e7-3077">EndPointSolid</span><span class="sxs-lookup"><span data-stu-id="127e7-3077">EndPointSolid</span></span></td>
 </tr>
 <tr><td>![AirplaneSolid](images/segoe-mdl/eb4c.png)</td>
  <td><span data-ttu-id="127e7-3079">EB4C</span><span class="sxs-lookup"><span data-stu-id="127e7-3079">EB4C</span></span></td>
  <td><span data-ttu-id="127e7-3080">AirplaneSolid</span><span class="sxs-lookup"><span data-stu-id="127e7-3080">AirplaneSolid</span></span></td>
 </tr>
 <tr><td>![TrainSolid](images/segoe-mdl/eb4d.png)</td>
  <td><span data-ttu-id="127e7-3082">EB4D</span><span class="sxs-lookup"><span data-stu-id="127e7-3082">EB4D</span></span></td>
  <td><span data-ttu-id="127e7-3083">TrainSolid</span><span class="sxs-lookup"><span data-stu-id="127e7-3083">TrainSolid</span></span></td>
 </tr>
 <tr><td>![WorkSolid](images/segoe-mdl/eb4e.png)</td>
  <td><span data-ttu-id="127e7-3085">EB4E</span><span class="sxs-lookup"><span data-stu-id="127e7-3085">EB4E</span></span></td>
  <td><span data-ttu-id="127e7-3086">WorkSolid</span><span class="sxs-lookup"><span data-stu-id="127e7-3086">WorkSolid</span></span></td>
 </tr>
 <tr><td>![ReminderFill](images/segoe-mdl/eb4f.png)</td>
  <td><span data-ttu-id="127e7-3088">EB4F</span><span class="sxs-lookup"><span data-stu-id="127e7-3088">EB4F</span></span></td>
  <td><span data-ttu-id="127e7-3089">ReminderFill</span><span class="sxs-lookup"><span data-stu-id="127e7-3089">ReminderFill</span></span></td>
 </tr>
 <tr><td>![Reminder](images/segoe-mdl/eb50.png)</td>
  <td><span data-ttu-id="127e7-3091">EB50</span><span class="sxs-lookup"><span data-stu-id="127e7-3091">EB50</span></span></td>
  <td><span data-ttu-id="127e7-3092">Reminder</span><span class="sxs-lookup"><span data-stu-id="127e7-3092">Reminder</span></span></td>
 </tr>
 <tr><td>![Heart](images/segoe-mdl/eb51.png)</td>
  <td><span data-ttu-id="127e7-3094">EB51</span><span class="sxs-lookup"><span data-stu-id="127e7-3094">EB51</span></span></td>
  <td><span data-ttu-id="127e7-3095">Heart</span><span class="sxs-lookup"><span data-stu-id="127e7-3095">Heart</span></span></td>
 </tr>
 <tr><td>![HeartFill](images/segoe-mdl/eb52.png)</td>
  <td><span data-ttu-id="127e7-3097">EB52</span><span class="sxs-lookup"><span data-stu-id="127e7-3097">EB52</span></span></td>
  <td><span data-ttu-id="127e7-3098">HeartFill</span><span class="sxs-lookup"><span data-stu-id="127e7-3098">HeartFill</span></span></td>
 </tr>
 <tr><td>![EthernetError](images/segoe-mdl/eb55.png)</td>
  <td><span data-ttu-id="127e7-3100">EB55</span><span class="sxs-lookup"><span data-stu-id="127e7-3100">EB55</span></span></td>
  <td><span data-ttu-id="127e7-3101">EthernetError</span><span class="sxs-lookup"><span data-stu-id="127e7-3101">EthernetError</span></span></td>
 </tr>
 <tr><td>![EthernetWarning](images/segoe-mdl/eb56.png)</td>
  <td><span data-ttu-id="127e7-3103">EB56</span><span class="sxs-lookup"><span data-stu-id="127e7-3103">EB56</span></span></td>
  <td><span data-ttu-id="127e7-3104">EthernetWarning</span><span class="sxs-lookup"><span data-stu-id="127e7-3104">EthernetWarning</span></span></td>
 </tr>
 <tr><td>![StatusConnecting1](images/segoe-mdl/eb57.png)</td>
  <td><span data-ttu-id="127e7-3106">EB57</span><span class="sxs-lookup"><span data-stu-id="127e7-3106">EB57</span></span></td>
  <td><span data-ttu-id="127e7-3107">StatusConnecting1</span><span class="sxs-lookup"><span data-stu-id="127e7-3107">StatusConnecting1</span></span></td>
 </tr>
 <tr><td>![StatusConnecting2](images/segoe-mdl/eb58.png)</td>
  <td><span data-ttu-id="127e7-3109">EB58</span><span class="sxs-lookup"><span data-stu-id="127e7-3109">EB58</span></span></td>
  <td><span data-ttu-id="127e7-3110">StatusConnecting2</span><span class="sxs-lookup"><span data-stu-id="127e7-3110">StatusConnecting2</span></span></td>
 </tr>
 <tr><td>![StatusUnsecure](images/segoe-mdl/eb59.png)</td>
  <td><span data-ttu-id="127e7-3112">EB59</span><span class="sxs-lookup"><span data-stu-id="127e7-3112">EB59</span></span></td>
  <td><span data-ttu-id="127e7-3113">StatusUnsecure</span><span class="sxs-lookup"><span data-stu-id="127e7-3113">StatusUnsecure</span></span></td>
 </tr>
 <tr><td>![WifiError0](images/segoe-mdl/eb5a.png)</td>
  <td><span data-ttu-id="127e7-3115">EB5A</span><span class="sxs-lookup"><span data-stu-id="127e7-3115">EB5A</span></span></td>
  <td><span data-ttu-id="127e7-3116">WifiError0</span><span class="sxs-lookup"><span data-stu-id="127e7-3116">WifiError0</span></span></td>
 </tr>
 <tr><td>![WifiError1](images/segoe-mdl/eb5b.png)</td>
  <td><span data-ttu-id="127e7-3118">EB5B</span><span class="sxs-lookup"><span data-stu-id="127e7-3118">EB5B</span></span></td>
  <td><span data-ttu-id="127e7-3119">WifiError1</span><span class="sxs-lookup"><span data-stu-id="127e7-3119">WifiError1</span></span></td>
 </tr>
 <tr><td>![WifiError2](images/segoe-mdl/eb5c.png)</td>
  <td><span data-ttu-id="127e7-3121">EB5C</span><span class="sxs-lookup"><span data-stu-id="127e7-3121">EB5C</span></span></td>
  <td><span data-ttu-id="127e7-3122">WifiError2</span><span class="sxs-lookup"><span data-stu-id="127e7-3122">WifiError2</span></span></td>
 </tr>
 <tr><td>![WifiError3](images/segoe-mdl/eb5d.png)</td>
  <td><span data-ttu-id="127e7-3124">EB5D</span><span class="sxs-lookup"><span data-stu-id="127e7-3124">EB5D</span></span></td>
  <td><span data-ttu-id="127e7-3125">WifiError3</span><span class="sxs-lookup"><span data-stu-id="127e7-3125">WifiError3</span></span></td>
 </tr>
 <tr><td>![WifiError4](images/segoe-mdl/eb5e.png)</td>
  <td><span data-ttu-id="127e7-3127">EB5E</span><span class="sxs-lookup"><span data-stu-id="127e7-3127">EB5E</span></span></td>
  <td><span data-ttu-id="127e7-3128">WifiError4</span><span class="sxs-lookup"><span data-stu-id="127e7-3128">WifiError4</span></span></td>
 </tr>
 <tr><td>![WifiWarning0](images/segoe-mdl/eb5f.png)</td>
  <td><span data-ttu-id="127e7-3130">EB5F</span><span class="sxs-lookup"><span data-stu-id="127e7-3130">EB5F</span></span></td>
  <td><span data-ttu-id="127e7-3131">WifiWarning0</span><span class="sxs-lookup"><span data-stu-id="127e7-3131">WifiWarning0</span></span></td>
 </tr>
 <tr><td>![WifiWarning1](images/segoe-mdl/eb60.png)</td>
  <td><span data-ttu-id="127e7-3133">EB60</span><span class="sxs-lookup"><span data-stu-id="127e7-3133">EB60</span></span></td>
  <td><span data-ttu-id="127e7-3134">WifiWarning1</span><span class="sxs-lookup"><span data-stu-id="127e7-3134">WifiWarning1</span></span></td>
 </tr>
 <tr><td>![WifiWarning2](images/segoe-mdl/eb61.png)</td>
  <td><span data-ttu-id="127e7-3136">EB61</span><span class="sxs-lookup"><span data-stu-id="127e7-3136">EB61</span></span></td>
  <td><span data-ttu-id="127e7-3137">WifiWarning2</span><span class="sxs-lookup"><span data-stu-id="127e7-3137">WifiWarning2</span></span></td>
 </tr>
 <tr><td>![WifiWarning3](images/segoe-mdl/eb62.png)</td>
  <td><span data-ttu-id="127e7-3139">EB62</span><span class="sxs-lookup"><span data-stu-id="127e7-3139">EB62</span></span></td>
  <td><span data-ttu-id="127e7-3140">WifiWarning3</span><span class="sxs-lookup"><span data-stu-id="127e7-3140">WifiWarning3</span></span></td>
 </tr>
 <tr><td>![WifiWarning4](images/segoe-mdl/eb63.png)</td>
  <td><span data-ttu-id="127e7-3142">EB63</span><span class="sxs-lookup"><span data-stu-id="127e7-3142">EB63</span></span></td>
  <td><span data-ttu-id="127e7-3143">WifiWarning4</span><span class="sxs-lookup"><span data-stu-id="127e7-3143">WifiWarning4</span></span></td>
 </tr>
 <tr><td>![Devices4](images/segoe-mdl/eb66.png)</td>
  <td><span data-ttu-id="127e7-3145">EB66</span><span class="sxs-lookup"><span data-stu-id="127e7-3145">EB66</span></span></td>
  <td><span data-ttu-id="127e7-3146">Devices4</span><span class="sxs-lookup"><span data-stu-id="127e7-3146">Devices4</span></span></td>
 </tr>
 <tr><td>![NUIIris](images/segoe-mdl/eb67.png)</td>
  <td><span data-ttu-id="127e7-3148">EB67</span><span class="sxs-lookup"><span data-stu-id="127e7-3148">EB67</span></span></td>
  <td><span data-ttu-id="127e7-3149">NUIIris</span><span class="sxs-lookup"><span data-stu-id="127e7-3149">NUIIris</span></span></td>
 </tr>
 <tr><td>![NUIFace](images/segoe-mdl/eb68.png)</td>
  <td><span data-ttu-id="127e7-3151">EB68</span><span class="sxs-lookup"><span data-stu-id="127e7-3151">EB68</span></span></td>
  <td><span data-ttu-id="127e7-3152">NUIFace</span><span class="sxs-lookup"><span data-stu-id="127e7-3152">NUIFace</span></span></td>
 </tr>
 <tr><td>![EditMirrored](images/segoe-mdl/eb7e.png)</td>
  <td><span data-ttu-id="127e7-3154">EB7E</span><span class="sxs-lookup"><span data-stu-id="127e7-3154">EB7E</span></span></td>
  <td><span data-ttu-id="127e7-3155">EditMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-3155">EditMirrored</span></span></td>
 </tr>
 <tr><td>![NUIFPStartSlideHand](images/segoe-mdl/eb82.png)</td>
  <td><span data-ttu-id="127e7-3157">EB82</span><span class="sxs-lookup"><span data-stu-id="127e7-3157">EB82</span></span></td>
  <td><span data-ttu-id="127e7-3158">NUIFPStartSlideHand</span><span class="sxs-lookup"><span data-stu-id="127e7-3158">NUIFPStartSlideHand</span></span></td>
 </tr>
 <tr><td>![NUIFPStartSlideAction](images/segoe-mdl/eb83.png)</td>
  <td><span data-ttu-id="127e7-3160">EB83</span><span class="sxs-lookup"><span data-stu-id="127e7-3160">EB83</span></span></td>
  <td><span data-ttu-id="127e7-3161">NUIFPStartSlideAction</span><span class="sxs-lookup"><span data-stu-id="127e7-3161">NUIFPStartSlideAction</span></span></td>
 </tr>
 <tr><td>![NUIFPContinueSlideHand](images/segoe-mdl/eb84.png)</td>
  <td><span data-ttu-id="127e7-3163">EB84</span><span class="sxs-lookup"><span data-stu-id="127e7-3163">EB84</span></span></td>
  <td><span data-ttu-id="127e7-3164">NUIFPContinueSlideHand</span><span class="sxs-lookup"><span data-stu-id="127e7-3164">NUIFPContinueSlideHand</span></span></td>
 </tr>
 <tr><td>![NUIFPContinueSlideAction](images/segoe-mdl/eb85.png)</td>
  <td><span data-ttu-id="127e7-3166">EB85</span><span class="sxs-lookup"><span data-stu-id="127e7-3166">EB85</span></span></td>
  <td><span data-ttu-id="127e7-3167">NUIFPContinueSlideAction</span><span class="sxs-lookup"><span data-stu-id="127e7-3167">NUIFPContinueSlideAction</span></span></td>
 </tr>
 <tr><td>![NUIFPRollRightHand](images/segoe-mdl/eb86.png)</td>
  <td><span data-ttu-id="127e7-3169">EB86</span><span class="sxs-lookup"><span data-stu-id="127e7-3169">EB86</span></span></td>
  <td><span data-ttu-id="127e7-3170">NUIFPRollRightHand</span><span class="sxs-lookup"><span data-stu-id="127e7-3170">NUIFPRollRightHand</span></span></td>
 </tr>
 <tr><td>![NUIFPRollRightHandAction](images/segoe-mdl/eb87.png)</td>
  <td><span data-ttu-id="127e7-3172">EB87</span><span class="sxs-lookup"><span data-stu-id="127e7-3172">EB87</span></span></td>
  <td><span data-ttu-id="127e7-3173">NUIFPRollRightHandAction</span><span class="sxs-lookup"><span data-stu-id="127e7-3173">NUIFPRollRightHandAction</span></span></td>
 </tr>
 <tr><td>![NUIFPRollLeftHand](images/segoe-mdl/eb88.png)</td>
  <td><span data-ttu-id="127e7-3175">EB88</span><span class="sxs-lookup"><span data-stu-id="127e7-3175">EB88</span></span></td>
  <td><span data-ttu-id="127e7-3176">NUIFPRollLeftHand</span><span class="sxs-lookup"><span data-stu-id="127e7-3176">NUIFPRollLeftHand</span></span></td>
 </tr>
 <tr><td>![NUIFPRollLeftAction](images/segoe-mdl/eb89.png)</td>
  <td><span data-ttu-id="127e7-3178">EB89</span><span class="sxs-lookup"><span data-stu-id="127e7-3178">EB89</span></span></td>
  <td><span data-ttu-id="127e7-3179">NUIFPRollLeftAction</span><span class="sxs-lookup"><span data-stu-id="127e7-3179">NUIFPRollLeftAction</span></span></td>
 </tr>
 <tr><td>![NUIFPPressHand](images/segoe-mdl/eb8a.png)</td>
  <td><span data-ttu-id="127e7-3181">EB8A</span><span class="sxs-lookup"><span data-stu-id="127e7-3181">EB8A</span></span></td>
  <td><span data-ttu-id="127e7-3182">NUIFPPressHand</span><span class="sxs-lookup"><span data-stu-id="127e7-3182">NUIFPPressHand</span></span></td>
 </tr>
 <tr><td>![NUIFPPressAction](images/segoe-mdl/eb8b.png)</td>
  <td><span data-ttu-id="127e7-3184">EB8B</span><span class="sxs-lookup"><span data-stu-id="127e7-3184">EB8B</span></span></td>
  <td><span data-ttu-id="127e7-3185">NUIFPPressAction</span><span class="sxs-lookup"><span data-stu-id="127e7-3185">NUIFPPressAction</span></span></td>
 </tr>
 <tr><td>![NUIFPPressRepeatHand](images/segoe-mdl/eb8c.png)</td>
  <td><span data-ttu-id="127e7-3187">EB8C</span><span class="sxs-lookup"><span data-stu-id="127e7-3187">EB8C</span></span></td>
  <td><span data-ttu-id="127e7-3188">NUIFPPressRepeatHand</span><span class="sxs-lookup"><span data-stu-id="127e7-3188">NUIFPPressRepeatHand</span></span></td>
 </tr>
 <tr><td>![NUIFPPressRepeatAction](images/segoe-mdl/eb8d.png)</td>
  <td><span data-ttu-id="127e7-3190">EB8D</span><span class="sxs-lookup"><span data-stu-id="127e7-3190">EB8D</span></span></td>
  <td><span data-ttu-id="127e7-3191">NUIFPPressRepeatAction</span><span class="sxs-lookup"><span data-stu-id="127e7-3191">NUIFPPressRepeatAction</span></span></td>
 </tr>
 <tr><td>![StatusErrorFull](images/segoe-mdl/eb90.png)</td>
  <td><span data-ttu-id="127e7-3193">EB90</span><span class="sxs-lookup"><span data-stu-id="127e7-3193">EB90</span></span></td>
  <td><span data-ttu-id="127e7-3194">StatusErrorFull</span><span class="sxs-lookup"><span data-stu-id="127e7-3194">StatusErrorFull</span></span></td>
 </tr>
 <tr><td>![MultitaskExpanded](images/segoe-mdl/eb91.png)</td>
  <td><span data-ttu-id="127e7-3196">EB91</span><span class="sxs-lookup"><span data-stu-id="127e7-3196">EB91</span></span></td>
  <td><span data-ttu-id="127e7-3197">MultitaskExpanded</span><span class="sxs-lookup"><span data-stu-id="127e7-3197">MultitaskExpanded</span></span></td>
 </tr>
 <tr><td>![Certificate](images/segoe-mdl/eb95.png)</td>
  <td><span data-ttu-id="127e7-3199">EB95</span><span class="sxs-lookup"><span data-stu-id="127e7-3199">EB95</span></span></td>
  <td><span data-ttu-id="127e7-3200">Certificate</span><span class="sxs-lookup"><span data-stu-id="127e7-3200">Certificate</span></span></td>
 </tr>
 <tr><td>![BackSpaceQWERTYLg](images/segoe-mdl/eb96.png)</td>
  <td><span data-ttu-id="127e7-3202">EB96</span><span class="sxs-lookup"><span data-stu-id="127e7-3202">EB96</span></span></td>
  <td><span data-ttu-id="127e7-3203">BackSpaceQWERTYLg</span><span class="sxs-lookup"><span data-stu-id="127e7-3203">BackSpaceQWERTYLg</span></span></td>
 </tr>
 <tr><td>![ReturnKeyLg](images/segoe-mdl/eb97.png)</td>
  <td><span data-ttu-id="127e7-3205">EB97</span><span class="sxs-lookup"><span data-stu-id="127e7-3205">EB97</span></span></td>
  <td><span data-ttu-id="127e7-3206">ReturnKeyLg</span><span class="sxs-lookup"><span data-stu-id="127e7-3206">ReturnKeyLg</span></span></td>
 </tr>
 <tr><td>![FastForward](images/segoe-mdl/eb9d.png)</td>
  <td><span data-ttu-id="127e7-3208">EB9D</span><span class="sxs-lookup"><span data-stu-id="127e7-3208">EB9D</span></span></td>
  <td><span data-ttu-id="127e7-3209">FastForward</span><span class="sxs-lookup"><span data-stu-id="127e7-3209">FastForward</span></span></td>
 </tr>
 <tr><td>![Rewind](images/segoe-mdl/eb9e.png)</td>
  <td><span data-ttu-id="127e7-3211">EB9E</span><span class="sxs-lookup"><span data-stu-id="127e7-3211">EB9E</span></span></td>
  <td><span data-ttu-id="127e7-3212">Rewind</span><span class="sxs-lookup"><span data-stu-id="127e7-3212">Rewind</span></span></td>
 </tr>
 <tr><td>![Photo2](images/segoe-mdl/eb9f.png)</td>
  <td><span data-ttu-id="127e7-3214">EB9F</span><span class="sxs-lookup"><span data-stu-id="127e7-3214">EB9F</span></span></td>
  <td><span data-ttu-id="127e7-3215">Photo2</span><span class="sxs-lookup"><span data-stu-id="127e7-3215">Photo2</span></span></td>
 </tr>
 <tr><td>![&nbsp;MobBattery0](images/segoe-mdl/eba0.png)</td>
  <td><span data-ttu-id="127e7-3217">EBA0</span><span class="sxs-lookup"><span data-stu-id="127e7-3217">EBA0</span></span></td>
  <td><span data-ttu-id="127e7-3218">&nbsp;MobBattery0</span><span class="sxs-lookup"><span data-stu-id="127e7-3218">&nbsp;MobBattery0</span></span></td>
 </tr>
 <tr><td>![&nbsp;MobBattery1](images/segoe-mdl/eba1.png)</td>
  <td><span data-ttu-id="127e7-3220">EBA1</span><span class="sxs-lookup"><span data-stu-id="127e7-3220">EBA1</span></span></td>
  <td><span data-ttu-id="127e7-3221">&nbsp;MobBattery1</span><span class="sxs-lookup"><span data-stu-id="127e7-3221">&nbsp;MobBattery1</span></span></td>
 </tr>
 <tr><td>![&nbsp;MobBattery2](images/segoe-mdl/eba2.png)</td>
  <td><span data-ttu-id="127e7-3223">EBA2</span><span class="sxs-lookup"><span data-stu-id="127e7-3223">EBA2</span></span></td>
  <td><span data-ttu-id="127e7-3224">&nbsp;MobBattery2</span><span class="sxs-lookup"><span data-stu-id="127e7-3224">&nbsp;MobBattery2</span></span></td>
 </tr>
 <tr><td>![&nbsp;MobBattery3](images/segoe-mdl/eba3.png)</td>
  <td><span data-ttu-id="127e7-3226">EBA3</span><span class="sxs-lookup"><span data-stu-id="127e7-3226">EBA3</span></span></td>
  <td><span data-ttu-id="127e7-3227">&nbsp;MobBattery3</span><span class="sxs-lookup"><span data-stu-id="127e7-3227">&nbsp;MobBattery3</span></span></td>
 </tr>
 <tr><td>![&nbsp;MobBattery4](images/segoe-mdl/eba4.png)</td>
  <td><span data-ttu-id="127e7-3229">EBA4</span><span class="sxs-lookup"><span data-stu-id="127e7-3229">EBA4</span></span></td>
  <td><span data-ttu-id="127e7-3230">&nbsp;MobBattery4</span><span class="sxs-lookup"><span data-stu-id="127e7-3230">&nbsp;MobBattery4</span></span></td>
 </tr>
 <tr><td>![&nbsp;MobBattery5](images/segoe-mdl/eba5.png)</td>
  <td><span data-ttu-id="127e7-3232">EBA5</span><span class="sxs-lookup"><span data-stu-id="127e7-3232">EBA5</span></span></td>
  <td><span data-ttu-id="127e7-3233">&nbsp;MobBattery5</span><span class="sxs-lookup"><span data-stu-id="127e7-3233">&nbsp;MobBattery5</span></span></td>
 </tr>
 <tr><td>![&nbsp;MobBattery6](images/segoe-mdl/eba6.png)</td>
  <td><span data-ttu-id="127e7-3235">EBA6</span><span class="sxs-lookup"><span data-stu-id="127e7-3235">EBA6</span></span></td>
  <td><span data-ttu-id="127e7-3236">&nbsp;MobBattery6</span><span class="sxs-lookup"><span data-stu-id="127e7-3236">&nbsp;MobBattery6</span></span></td>
 </tr>
 <tr><td>![&nbsp;MobBattery7](images/segoe-mdl/eba7.png)</td>
  <td><span data-ttu-id="127e7-3238">EBA7</span><span class="sxs-lookup"><span data-stu-id="127e7-3238">EBA7</span></span></td>
  <td><span data-ttu-id="127e7-3239">&nbsp;MobBattery7</span><span class="sxs-lookup"><span data-stu-id="127e7-3239">&nbsp;MobBattery7</span></span></td>
 </tr>
 <tr><td>![&nbsp;MobBattery8](images/segoe-mdl/eba8.png)</td>
  <td><span data-ttu-id="127e7-3241">EBA8</span><span class="sxs-lookup"><span data-stu-id="127e7-3241">EBA8</span></span></td>
  <td><span data-ttu-id="127e7-3242">&nbsp;MobBattery8</span><span class="sxs-lookup"><span data-stu-id="127e7-3242">&nbsp;MobBattery8</span></span></td>
 </tr>
 <tr><td>![&nbsp;MobBattery9](images/segoe-mdl/eba9.png)</td>
  <td><span data-ttu-id="127e7-3244">EBA9</span><span class="sxs-lookup"><span data-stu-id="127e7-3244">EBA9</span></span></td>
  <td><span data-ttu-id="127e7-3245">&nbsp;MobBattery9</span><span class="sxs-lookup"><span data-stu-id="127e7-3245">&nbsp;MobBattery9</span></span></td>
 </tr>
 <tr><td>![MobBattery10](images/segoe-mdl/ebaa.png)</td>
  <td><span data-ttu-id="127e7-3247">EBAA</span><span class="sxs-lookup"><span data-stu-id="127e7-3247">EBAA</span></span></td>
  <td><span data-ttu-id="127e7-3248">MobBattery10</span><span class="sxs-lookup"><span data-stu-id="127e7-3248">MobBattery10</span></span></td>
 </tr>
 <tr><td>![&nbsp;MobBatteryCharging0](images/segoe-mdl/ebab.png)</td>
  <td><span data-ttu-id="127e7-3250">EBAB</span><span class="sxs-lookup"><span data-stu-id="127e7-3250">EBAB</span></span></td>
  <td><span data-ttu-id="127e7-3251">&nbsp;MobBatteryCharging0</span><span class="sxs-lookup"><span data-stu-id="127e7-3251">&nbsp;MobBatteryCharging0</span></span></td>
 </tr>
 <tr><td>![&nbsp;MobBatteryCharging1](images/segoe-mdl/ebac.png)</td>
  <td><span data-ttu-id="127e7-3253">EBAC</span><span class="sxs-lookup"><span data-stu-id="127e7-3253">EBAC</span></span></td>
  <td><span data-ttu-id="127e7-3254">&nbsp;MobBatteryCharging1</span><span class="sxs-lookup"><span data-stu-id="127e7-3254">&nbsp;MobBatteryCharging1</span></span></td>
 </tr>
 <tr><td>![&nbsp;MobBatteryCharging2](images/segoe-mdl/ebad.png)</td>
  <td><span data-ttu-id="127e7-3256">EBAD</span><span class="sxs-lookup"><span data-stu-id="127e7-3256">EBAD</span></span></td>
  <td><span data-ttu-id="127e7-3257">&nbsp;MobBatteryCharging2</span><span class="sxs-lookup"><span data-stu-id="127e7-3257">&nbsp;MobBatteryCharging2</span></span></td>
 </tr>
 <tr><td>![&nbsp;MobBatteryCharging3](images/segoe-mdl/ebae.png)</td>
  <td><span data-ttu-id="127e7-3259">EBAE</span><span class="sxs-lookup"><span data-stu-id="127e7-3259">EBAE</span></span></td>
  <td><span data-ttu-id="127e7-3260">&nbsp;MobBatteryCharging3</span><span class="sxs-lookup"><span data-stu-id="127e7-3260">&nbsp;MobBatteryCharging3</span></span></td>
 </tr>
 <tr><td>![&nbsp;MobBatteryCharging4](images/segoe-mdl/ebaf.png)</td>
  <td><span data-ttu-id="127e7-3262">EBAF</span><span class="sxs-lookup"><span data-stu-id="127e7-3262">EBAF</span></span></td>
  <td><span data-ttu-id="127e7-3263">&nbsp;MobBatteryCharging4</span><span class="sxs-lookup"><span data-stu-id="127e7-3263">&nbsp;MobBatteryCharging4</span></span></td>
 </tr>
 <tr><td>![&nbsp;MobBatteryCharging5](images/segoe-mdl/ebb0.png)</td>
  <td><span data-ttu-id="127e7-3265">EBB0</span><span class="sxs-lookup"><span data-stu-id="127e7-3265">EBB0</span></span></td>
  <td><span data-ttu-id="127e7-3266">&nbsp;MobBatteryCharging5</span><span class="sxs-lookup"><span data-stu-id="127e7-3266">&nbsp;MobBatteryCharging5</span></span></td>
 </tr>
 <tr><td>![&nbsp;MobBatteryCharging6](images/segoe-mdl/ebb1.png)</td>
  <td><span data-ttu-id="127e7-3268">EBB1</span><span class="sxs-lookup"><span data-stu-id="127e7-3268">EBB1</span></span></td>
  <td><span data-ttu-id="127e7-3269">&nbsp;MobBatteryCharging6</span><span class="sxs-lookup"><span data-stu-id="127e7-3269">&nbsp;MobBatteryCharging6</span></span></td>
 </tr>
 <tr><td>![&nbsp;MobBatteryCharging7](images/segoe-mdl/ebb2.png)</td>
  <td><span data-ttu-id="127e7-3271">EBB2</span><span class="sxs-lookup"><span data-stu-id="127e7-3271">EBB2</span></span></td>
  <td><span data-ttu-id="127e7-3272">&nbsp;MobBatteryCharging7</span><span class="sxs-lookup"><span data-stu-id="127e7-3272">&nbsp;MobBatteryCharging7</span></span></td>
 </tr>
 <tr><td>![&nbsp;MobBatteryCharging8](images/segoe-mdl/ebb3.png)</td>
  <td><span data-ttu-id="127e7-3274">EBB3</span><span class="sxs-lookup"><span data-stu-id="127e7-3274">EBB3</span></span></td>
  <td><span data-ttu-id="127e7-3275">&nbsp;MobBatteryCharging8</span><span class="sxs-lookup"><span data-stu-id="127e7-3275">&nbsp;MobBatteryCharging8</span></span></td>
 </tr>
 <tr><td>![&nbsp;MobBatteryCharging9](images/segoe-mdl/ebb4.png)</td>
  <td><span data-ttu-id="127e7-3277">EBB4</span><span class="sxs-lookup"><span data-stu-id="127e7-3277">EBB4</span></span></td>
  <td><span data-ttu-id="127e7-3278">&nbsp;MobBatteryCharging9</span><span class="sxs-lookup"><span data-stu-id="127e7-3278">&nbsp;MobBatteryCharging9</span></span></td>
 </tr>
 <tr><td>![&nbsp;MobBatteryCharging10](images/segoe-mdl/ebb5.png)</td>
  <td><span data-ttu-id="127e7-3280">EBB5</span><span class="sxs-lookup"><span data-stu-id="127e7-3280">EBB5</span></span></td>
  <td><span data-ttu-id="127e7-3281">&nbsp;MobBatteryCharging10</span><span class="sxs-lookup"><span data-stu-id="127e7-3281">&nbsp;MobBatteryCharging10</span></span></td>
 </tr>
 <tr><td>![&nbsp;MobBatterySaver0](images/segoe-mdl/ebb6.png)</td>
  <td><span data-ttu-id="127e7-3283">EBB6</span><span class="sxs-lookup"><span data-stu-id="127e7-3283">EBB6</span></span></td>
  <td><span data-ttu-id="127e7-3284">&nbsp;MobBatterySaver0</span><span class="sxs-lookup"><span data-stu-id="127e7-3284">&nbsp;MobBatterySaver0</span></span></td>
 </tr>
 <tr><td>![&nbsp;MobBatterySaver1](images/segoe-mdl/ebb7.png)</td>
  <td><span data-ttu-id="127e7-3286">EBB7</span><span class="sxs-lookup"><span data-stu-id="127e7-3286">EBB7</span></span></td>
  <td><span data-ttu-id="127e7-3287">&nbsp;MobBatterySaver1</span><span class="sxs-lookup"><span data-stu-id="127e7-3287">&nbsp;MobBatterySaver1</span></span></td>
 </tr>
 <tr><td>![&nbsp;MobBatterySaver2](images/segoe-mdl/ebb8.png)</td>
  <td><span data-ttu-id="127e7-3289">EBB8</span><span class="sxs-lookup"><span data-stu-id="127e7-3289">EBB8</span></span></td>
  <td><span data-ttu-id="127e7-3290">&nbsp;MobBatterySaver2</span><span class="sxs-lookup"><span data-stu-id="127e7-3290">&nbsp;MobBatterySaver2</span></span></td>
 </tr>
 <tr><td>![&nbsp;MobBatterySaver3](images/segoe-mdl/ebb9.png)</td>
  <td><span data-ttu-id="127e7-3292">EBB9</span><span class="sxs-lookup"><span data-stu-id="127e7-3292">EBB9</span></span></td>
  <td><span data-ttu-id="127e7-3293">&nbsp;MobBatterySaver3</span><span class="sxs-lookup"><span data-stu-id="127e7-3293">&nbsp;MobBatterySaver3</span></span></td>
 </tr>
 <tr><td>![&nbsp;MobBatterySaver4](images/segoe-mdl/ebba.png)</td>
  <td><span data-ttu-id="127e7-3295">EBBA</span><span class="sxs-lookup"><span data-stu-id="127e7-3295">EBBA</span></span></td>
  <td><span data-ttu-id="127e7-3296">&nbsp;MobBatterySaver4</span><span class="sxs-lookup"><span data-stu-id="127e7-3296">&nbsp;MobBatterySaver4</span></span></td>
 </tr>
 <tr><td>![&nbsp;MobBatterySaver5](images/segoe-mdl/ebbb.png)</td>
  <td><span data-ttu-id="127e7-3298">EBBB</span><span class="sxs-lookup"><span data-stu-id="127e7-3298">EBBB</span></span></td>
  <td><span data-ttu-id="127e7-3299">&nbsp;MobBatterySaver5</span><span class="sxs-lookup"><span data-stu-id="127e7-3299">&nbsp;MobBatterySaver5</span></span></td>
 </tr>
 <tr><td>![&nbsp;MobBatterySaver6](images/segoe-mdl/ebbc.png)</td>
  <td><span data-ttu-id="127e7-3301">EBBC</span><span class="sxs-lookup"><span data-stu-id="127e7-3301">EBBC</span></span></td>
  <td><span data-ttu-id="127e7-3302">&nbsp;MobBatterySaver6</span><span class="sxs-lookup"><span data-stu-id="127e7-3302">&nbsp;MobBatterySaver6</span></span></td>
 </tr>
 <tr><td>![&nbsp;MobBatterySaver7](images/segoe-mdl/ebbd.png)</td>
  <td><span data-ttu-id="127e7-3304">EBBD</span><span class="sxs-lookup"><span data-stu-id="127e7-3304">EBBD</span></span></td>
  <td><span data-ttu-id="127e7-3305">&nbsp;MobBatterySaver7</span><span class="sxs-lookup"><span data-stu-id="127e7-3305">&nbsp;MobBatterySaver7</span></span></td>
 </tr>
 <tr><td>![&nbsp;MobBatterySaver8](images/segoe-mdl/ebbe.png)</td>
  <td><span data-ttu-id="127e7-3307">EBBE</span><span class="sxs-lookup"><span data-stu-id="127e7-3307">EBBE</span></span></td>
  <td><span data-ttu-id="127e7-3308">&nbsp;MobBatterySaver8</span><span class="sxs-lookup"><span data-stu-id="127e7-3308">&nbsp;MobBatterySaver8</span></span></td>
 </tr>
 <tr><td>![&nbsp;MobBatterySaver9](images/segoe-mdl/ebbf.png)</td>
  <td><span data-ttu-id="127e7-3310">EBBF</span><span class="sxs-lookup"><span data-stu-id="127e7-3310">EBBF</span></span></td>
  <td><span data-ttu-id="127e7-3311">&nbsp;MobBatterySaver9</span><span class="sxs-lookup"><span data-stu-id="127e7-3311">&nbsp;MobBatterySaver9</span></span></td>
 </tr>
 <tr><td>![&nbsp;MobBatterySaver10](images/segoe-mdl/ebc0.png)</td>
  <td><span data-ttu-id="127e7-3313">EBC0</span><span class="sxs-lookup"><span data-stu-id="127e7-3313">EBC0</span></span></td>
  <td><span data-ttu-id="127e7-3314">&nbsp;MobBatterySaver10</span><span class="sxs-lookup"><span data-stu-id="127e7-3314">&nbsp;MobBatterySaver10</span></span></td>
 </tr>
 <tr><td>![DictionaryCloud](images/segoe-mdl/ebc3.png)</td>
  <td><span data-ttu-id="127e7-3316">EBC3</span><span class="sxs-lookup"><span data-stu-id="127e7-3316">EBC3</span></span></td>
  <td><span data-ttu-id="127e7-3317">DictionaryCloud</span><span class="sxs-lookup"><span data-stu-id="127e7-3317">DictionaryCloud</span></span></td>
 </tr>
 <tr><td>![ResetDrive](images/segoe-mdl/ebc4.png)</td>
  <td><span data-ttu-id="127e7-3319">EBC4</span><span class="sxs-lookup"><span data-stu-id="127e7-3319">EBC4</span></span></td>
  <td><span data-ttu-id="127e7-3320">ResetDrive</span><span class="sxs-lookup"><span data-stu-id="127e7-3320">ResetDrive</span></span></td>
 </tr>
 <tr><td>![VolumeBars](images/segoe-mdl/ebc5.png)</td>
  <td><span data-ttu-id="127e7-3322">EBC5</span><span class="sxs-lookup"><span data-stu-id="127e7-3322">EBC5</span></span></td>
  <td><span data-ttu-id="127e7-3323">VolumeBars</span><span class="sxs-lookup"><span data-stu-id="127e7-3323">VolumeBars</span></span></td>
 </tr>
 <tr><td>![Project](images/segoe-mdl/ebc6.png)</td>
  <td><span data-ttu-id="127e7-3325">EBC6</span><span class="sxs-lookup"><span data-stu-id="127e7-3325">EBC6</span></span></td>
  <td><span data-ttu-id="127e7-3326">Project</span><span class="sxs-lookup"><span data-stu-id="127e7-3326">Project</span></span></td>
 </tr>
 <tr><td>![AdjustHologram](images/segoe-mdl/ebd2.png)</td>
  <td><span data-ttu-id="127e7-3328">EBD2</span><span class="sxs-lookup"><span data-stu-id="127e7-3328">EBD2</span></span></td>
  <td><span data-ttu-id="127e7-3329">AdjustHologram</span><span class="sxs-lookup"><span data-stu-id="127e7-3329">AdjustHologram</span></span></td>
 </tr>
 <tr><td>![WifiCallBars](images/segoe-mdl/ebd4.png)</td>
  <td><span data-ttu-id="127e7-3331">EBD4</span><span class="sxs-lookup"><span data-stu-id="127e7-3331">EBD4</span></span></td>
  <td><span data-ttu-id="127e7-3332">WifiCallBars</span><span class="sxs-lookup"><span data-stu-id="127e7-3332">WifiCallBars</span></span></td>
 </tr>
 <tr><td>![WifiCall0](images/segoe-mdl/ebd5.png)</td>
  <td><span data-ttu-id="127e7-3334">EBD5</span><span class="sxs-lookup"><span data-stu-id="127e7-3334">EBD5</span></span></td>
  <td><span data-ttu-id="127e7-3335">WifiCall0</span><span class="sxs-lookup"><span data-stu-id="127e7-3335">WifiCall0</span></span></td>
 </tr>
 <tr><td>![WifiCall1](images/segoe-mdl/ebd6.png)</td>
  <td><span data-ttu-id="127e7-3337">EBD6</span><span class="sxs-lookup"><span data-stu-id="127e7-3337">EBD6</span></span></td>
  <td><span data-ttu-id="127e7-3338">WifiCall1</span><span class="sxs-lookup"><span data-stu-id="127e7-3338">WifiCall1</span></span></td>
 </tr>
 <tr><td>![WifiCall2](images/segoe-mdl/ebd7.png)</td>
  <td><span data-ttu-id="127e7-3340">EBD7</span><span class="sxs-lookup"><span data-stu-id="127e7-3340">EBD7</span></span></td>
  <td><span data-ttu-id="127e7-3341">WifiCall2</span><span class="sxs-lookup"><span data-stu-id="127e7-3341">WifiCall2</span></span></td>
 </tr>
 <tr><td>![WifiCall3](images/segoe-mdl/ebd8.png)</td>
  <td><span data-ttu-id="127e7-3343">EBD8</span><span class="sxs-lookup"><span data-stu-id="127e7-3343">EBD8</span></span></td>
  <td><span data-ttu-id="127e7-3344">WifiCall3</span><span class="sxs-lookup"><span data-stu-id="127e7-3344">WifiCall3</span></span></td>
 </tr>
 <tr><td>![WifiCall4](images/segoe-mdl/ebd9.png)</td>
  <td><span data-ttu-id="127e7-3346">EBD9</span><span class="sxs-lookup"><span data-stu-id="127e7-3346">EBD9</span></span></td>
  <td><span data-ttu-id="127e7-3347">WifiCall4</span><span class="sxs-lookup"><span data-stu-id="127e7-3347">WifiCall4</span></span></td>
 </tr>
 <tr><td>![DeviceDiscovery](images/segoe-mdl/ebde.png)</td>
  <td><span data-ttu-id="127e7-3349">EBDE</span><span class="sxs-lookup"><span data-stu-id="127e7-3349">EBDE</span></span></td>
  <td><span data-ttu-id="127e7-3350">DeviceDiscovery</span><span class="sxs-lookup"><span data-stu-id="127e7-3350">DeviceDiscovery</span></span></td>
 </tr>
 <tr><td>![WindDirection](images/segoe-mdl/ebe6.png)</td>
  <td><span data-ttu-id="127e7-3352">EBE6</span><span class="sxs-lookup"><span data-stu-id="127e7-3352">EBE6</span></span></td>
  <td><span data-ttu-id="127e7-3353">WindDirection</span><span class="sxs-lookup"><span data-stu-id="127e7-3353">WindDirection</span></span></td>
 </tr>
 <tr><td>![RightArrowKeyTime0](images/segoe-mdl/ebe7.png)</td>
  <td><span data-ttu-id="127e7-3355">EBE7</span><span class="sxs-lookup"><span data-stu-id="127e7-3355">EBE7</span></span></td>
  <td><span data-ttu-id="127e7-3356">RightArrowKeyTime0</span><span class="sxs-lookup"><span data-stu-id="127e7-3356">RightArrowKeyTime0</span></span></td>
 </tr>
 <tr><td>![TabletMode](images/segoe-mdl/ebfc.png)</td>
  <td><span data-ttu-id="127e7-3358">EBFC</span><span class="sxs-lookup"><span data-stu-id="127e7-3358">EBFC</span></span></td>
  <td><span data-ttu-id="127e7-3359">TabletMode</span><span class="sxs-lookup"><span data-stu-id="127e7-3359">TabletMode</span></span></td>
 </tr>
 <tr><td>![StatusCircleLeft](images/segoe-mdl/ebfd.png)</td>
  <td><span data-ttu-id="127e7-3361">EBFD</span><span class="sxs-lookup"><span data-stu-id="127e7-3361">EBFD</span></span></td>
  <td><span data-ttu-id="127e7-3362">StatusCircleLeft</span><span class="sxs-lookup"><span data-stu-id="127e7-3362">StatusCircleLeft</span></span></td>
 </tr>
 <tr><td>![StatusTriangleLeft](images/segoe-mdl/ebfe.png)</td>
  <td><span data-ttu-id="127e7-3364">EBFE</span><span class="sxs-lookup"><span data-stu-id="127e7-3364">EBFE</span></span></td>
  <td><span data-ttu-id="127e7-3365">StatusTriangleLeft</span><span class="sxs-lookup"><span data-stu-id="127e7-3365">StatusTriangleLeft</span></span></td>
 </tr>
 <tr><td>![StatusErrorLeft](images/segoe-mdl/ebff.png)</td>
  <td><span data-ttu-id="127e7-3367">EBFF</span><span class="sxs-lookup"><span data-stu-id="127e7-3367">EBFF</span></span></td>
  <td><span data-ttu-id="127e7-3368">StatusErrorLeft</span><span class="sxs-lookup"><span data-stu-id="127e7-3368">StatusErrorLeft</span></span></td>
 </tr>
 <tr><td>![StatusWarningLeft](images/segoe-mdl/ec00.png)</td>
  <td><span data-ttu-id="127e7-3370">EC00</span><span class="sxs-lookup"><span data-stu-id="127e7-3370">EC00</span></span></td>
  <td><span data-ttu-id="127e7-3371">StatusWarningLeft</span><span class="sxs-lookup"><span data-stu-id="127e7-3371">StatusWarningLeft</span></span></td>
 </tr>
 <tr><td>![MobBatteryUnknown](images/segoe-mdl/ec02.png)</td>
  <td><span data-ttu-id="127e7-3373">EC02</span><span class="sxs-lookup"><span data-stu-id="127e7-3373">EC02</span></span></td>
  <td><span data-ttu-id="127e7-3374">MobBatteryUnknown</span><span class="sxs-lookup"><span data-stu-id="127e7-3374">MobBatteryUnknown</span></span></td>
 </tr>
 <tr><td>![NetworkTower](images/segoe-mdl/ec05.png)</td>
  <td><span data-ttu-id="127e7-3376">EC05</span><span class="sxs-lookup"><span data-stu-id="127e7-3376">EC05</span></span></td>
  <td><span data-ttu-id="127e7-3377">NetworkTower</span><span class="sxs-lookup"><span data-stu-id="127e7-3377">NetworkTower</span></span></td>
 </tr>
 <tr><td>![CityNext](images/segoe-mdl/ec06.png)</td>
  <td><span data-ttu-id="127e7-3379">EC06</span><span class="sxs-lookup"><span data-stu-id="127e7-3379">EC06</span></span></td>
  <td><span data-ttu-id="127e7-3380">CityNext</span><span class="sxs-lookup"><span data-stu-id="127e7-3380">CityNext</span></span></td>
 </tr>
 <tr><td>![CityNext2](images/segoe-mdl/ec07.png)</td>
  <td><span data-ttu-id="127e7-3382">EC07</span><span class="sxs-lookup"><span data-stu-id="127e7-3382">EC07</span></span></td>
  <td><span data-ttu-id="127e7-3383">CityNext2</span><span class="sxs-lookup"><span data-stu-id="127e7-3383">CityNext2</span></span></td>
 </tr>
 <tr><td>![Courthouse](images/segoe-mdl/ec08.png)</td>
  <td><span data-ttu-id="127e7-3385">EC08</span><span class="sxs-lookup"><span data-stu-id="127e7-3385">EC08</span></span></td>
  <td><span data-ttu-id="127e7-3386">Courthouse</span><span class="sxs-lookup"><span data-stu-id="127e7-3386">Courthouse</span></span></td>
 </tr>
 <tr><td>![Groceries](images/segoe-mdl/ec09.png)</td>
  <td><span data-ttu-id="127e7-3388">EC09</span><span class="sxs-lookup"><span data-stu-id="127e7-3388">EC09</span></span></td>
  <td><span data-ttu-id="127e7-3389">Groceries</span><span class="sxs-lookup"><span data-stu-id="127e7-3389">Groceries</span></span></td>
 </tr>
 <tr><td>![Sustainable](images/segoe-mdl/ec0a.png)</td>
  <td><span data-ttu-id="127e7-3391">EC0A</span><span class="sxs-lookup"><span data-stu-id="127e7-3391">EC0A</span></span></td>
  <td><span data-ttu-id="127e7-3392">Sustainable</span><span class="sxs-lookup"><span data-stu-id="127e7-3392">Sustainable</span></span></td>
 </tr>
 <tr><td>![BuildingEnergy](images/segoe-mdl/ec0b.png)</td>
  <td><span data-ttu-id="127e7-3394">EC0B</span><span class="sxs-lookup"><span data-stu-id="127e7-3394">EC0B</span></span></td>
  <td><span data-ttu-id="127e7-3395">BuildingEnergy</span><span class="sxs-lookup"><span data-stu-id="127e7-3395">BuildingEnergy</span></span></td>
 </tr>
 <tr><td>![ToggleFilled](images/segoe-mdl/ec11.png)</td>
  <td><span data-ttu-id="127e7-3397">EC11</span><span class="sxs-lookup"><span data-stu-id="127e7-3397">EC11</span></span></td>
  <td><span data-ttu-id="127e7-3398">ToggleFilled</span><span class="sxs-lookup"><span data-stu-id="127e7-3398">ToggleFilled</span></span></td>
 </tr>
 <tr><td>![ToggleBorder](images/segoe-mdl/ec12.png)</td>
  <td><span data-ttu-id="127e7-3400">EC12</span><span class="sxs-lookup"><span data-stu-id="127e7-3400">EC12</span></span></td>
  <td><span data-ttu-id="127e7-3401">ToggleBorder</span><span class="sxs-lookup"><span data-stu-id="127e7-3401">ToggleBorder</span></span></td>
 </tr>
 <tr><td>![SliderThumb](images/segoe-mdl/ec13.png)</td>
  <td><span data-ttu-id="127e7-3403">EC13</span><span class="sxs-lookup"><span data-stu-id="127e7-3403">EC13</span></span></td>
  <td><span data-ttu-id="127e7-3404">SliderThumb</span><span class="sxs-lookup"><span data-stu-id="127e7-3404">SliderThumb</span></span></td>
 </tr>
 <tr><td>![ToggleThumb](images/segoe-mdl/ec14.png)</td>
  <td><span data-ttu-id="127e7-3406">EC14</span><span class="sxs-lookup"><span data-stu-id="127e7-3406">EC14</span></span></td>
  <td><span data-ttu-id="127e7-3407">ToggleThumb</span><span class="sxs-lookup"><span data-stu-id="127e7-3407">ToggleThumb</span></span></td>
 </tr>
 <tr><td>![MiracastLogoSmall](images/segoe-mdl/ec15.png)</td>
  <td><span data-ttu-id="127e7-3409">EC15</span><span class="sxs-lookup"><span data-stu-id="127e7-3409">EC15</span></span></td>
  <td><span data-ttu-id="127e7-3410">MiracastLogoSmall</span><span class="sxs-lookup"><span data-stu-id="127e7-3410">MiracastLogoSmall</span></span></td>
 </tr>
 <tr><td>![MiracastLogoLarge](images/segoe-mdl/ec16.png)</td>
  <td><span data-ttu-id="127e7-3412">EC16</span><span class="sxs-lookup"><span data-stu-id="127e7-3412">EC16</span></span></td>
  <td><span data-ttu-id="127e7-3413">MiracastLogoLarge</span><span class="sxs-lookup"><span data-stu-id="127e7-3413">MiracastLogoLarge</span></span></td>
 </tr>
 <tr><td>![PLAP](images/segoe-mdl/ec19.png)</td>
  <td><span data-ttu-id="127e7-3415">EC19</span><span class="sxs-lookup"><span data-stu-id="127e7-3415">EC19</span></span></td>
  <td><span data-ttu-id="127e7-3416">PLAP</span><span class="sxs-lookup"><span data-stu-id="127e7-3416">PLAP</span></span></td>
 </tr>
 <tr><td>![Badge](images/segoe-mdl/ec1b.png)</td>
  <td><span data-ttu-id="127e7-3418">EC1B</span><span class="sxs-lookup"><span data-stu-id="127e7-3418">EC1B</span></span></td>
  <td><span data-ttu-id="127e7-3419">Badge</span><span class="sxs-lookup"><span data-stu-id="127e7-3419">Badge</span></span></td>
 </tr>
 <tr><td>![SignalRoaming](images/segoe-mdl/ec1e.png)</td>
  <td><span data-ttu-id="127e7-3421">EC1E</span><span class="sxs-lookup"><span data-stu-id="127e7-3421">EC1E</span></span></td>
  <td><span data-ttu-id="127e7-3422">SignalRoaming</span><span class="sxs-lookup"><span data-stu-id="127e7-3422">SignalRoaming</span></span></td>
 </tr>
 <tr><td>![MobileLocked](images/segoe-mdl/ec20.png)</td>
  <td><span data-ttu-id="127e7-3424">EC20</span><span class="sxs-lookup"><span data-stu-id="127e7-3424">EC20</span></span></td>
  <td><span data-ttu-id="127e7-3425">MobileLocked</span><span class="sxs-lookup"><span data-stu-id="127e7-3425">MobileLocked</span></span></td>
 </tr>
 <tr><td>![InsiderHubApp](images/segoe-mdl/ec24.png)</td>
  <td><span data-ttu-id="127e7-3427">EC24</span><span class="sxs-lookup"><span data-stu-id="127e7-3427">EC24</span></span></td>
  <td><span data-ttu-id="127e7-3428">InsiderHubApp</span><span class="sxs-lookup"><span data-stu-id="127e7-3428">InsiderHubApp</span></span></td>
 </tr>
 <tr><td>![PersonalFolder](images/segoe-mdl/ec25.png)</td>
  <td><span data-ttu-id="127e7-3430">EC25</span><span class="sxs-lookup"><span data-stu-id="127e7-3430">EC25</span></span></td>
  <td><span data-ttu-id="127e7-3431">PersonalFolder</span><span class="sxs-lookup"><span data-stu-id="127e7-3431">PersonalFolder</span></span></td>
 </tr>
 <tr><td>![HomeGroup](images/segoe-mdl/ec26.png)</td>
  <td><span data-ttu-id="127e7-3433">EC26</span><span class="sxs-lookup"><span data-stu-id="127e7-3433">EC26</span></span></td>
  <td><span data-ttu-id="127e7-3434">HomeGroup</span><span class="sxs-lookup"><span data-stu-id="127e7-3434">HomeGroup</span></span></td>
 </tr>
 <tr><td>![MyNetwork](images/segoe-mdl/ec27.png)</td>
  <td><span data-ttu-id="127e7-3436">EC27</span><span class="sxs-lookup"><span data-stu-id="127e7-3436">EC27</span></span></td>
  <td><span data-ttu-id="127e7-3437">MyNetwork</span><span class="sxs-lookup"><span data-stu-id="127e7-3437">MyNetwork</span></span></td>
 </tr>
 <tr><td>![KeyboardFull](images/segoe-mdl/ec31.png)</td>
  <td><span data-ttu-id="127e7-3439">EC31</span><span class="sxs-lookup"><span data-stu-id="127e7-3439">EC31</span></span></td>
  <td><span data-ttu-id="127e7-3440">KeyboardFull</span><span class="sxs-lookup"><span data-stu-id="127e7-3440">KeyboardFull</span></span></td>
 </tr>
 <tr><td>![MobSignal1](images/segoe-mdl/ec37.png)</td>
  <td><span data-ttu-id="127e7-3442">EC37</span><span class="sxs-lookup"><span data-stu-id="127e7-3442">EC37</span></span></td>
  <td><span data-ttu-id="127e7-3443">MobSignal1</span><span class="sxs-lookup"><span data-stu-id="127e7-3443">MobSignal1</span></span></td>
 </tr>
 <tr><td>![MobSignal2](images/segoe-mdl/ec38.png)</td>
  <td><span data-ttu-id="127e7-3445">EC38</span><span class="sxs-lookup"><span data-stu-id="127e7-3445">EC38</span></span></td>
  <td><span data-ttu-id="127e7-3446">MobSignal2</span><span class="sxs-lookup"><span data-stu-id="127e7-3446">MobSignal2</span></span></td>
 </tr>
 <tr><td>![MobSignal3](images/segoe-mdl/ec39.png)</td>
  <td><span data-ttu-id="127e7-3448">EC39</span><span class="sxs-lookup"><span data-stu-id="127e7-3448">EC39</span></span></td>
  <td><span data-ttu-id="127e7-3449">MobSignal3</span><span class="sxs-lookup"><span data-stu-id="127e7-3449">MobSignal3</span></span></td>
 </tr>
 <tr><td>![MobSignal4](images/segoe-mdl/ec3a.png)</td>
  <td><span data-ttu-id="127e7-3451">EC3A</span><span class="sxs-lookup"><span data-stu-id="127e7-3451">EC3A</span></span></td>
  <td><span data-ttu-id="127e7-3452">MobSignal4</span><span class="sxs-lookup"><span data-stu-id="127e7-3452">MobSignal4</span></span></td>
 </tr>
 <tr><td>![MobSignal5](images/segoe-mdl/ec3b.png)</td>
  <td><span data-ttu-id="127e7-3454">EC3B</span><span class="sxs-lookup"><span data-stu-id="127e7-3454">EC3B</span></span></td>
  <td><span data-ttu-id="127e7-3455">MobSignal5</span><span class="sxs-lookup"><span data-stu-id="127e7-3455">MobSignal5</span></span></td>
 </tr>
 <tr><td>![MobWifi1](images/segoe-mdl/ec3c.png)</td>
  <td><span data-ttu-id="127e7-3457">EC3C</span><span class="sxs-lookup"><span data-stu-id="127e7-3457">EC3C</span></span></td>
  <td><span data-ttu-id="127e7-3458">MobWifi1</span><span class="sxs-lookup"><span data-stu-id="127e7-3458">MobWifi1</span></span></td>
 </tr>
 <tr><td>![MobWifi2](images/segoe-mdl/ec3d.png)</td>
  <td><span data-ttu-id="127e7-3460">EC3D</span><span class="sxs-lookup"><span data-stu-id="127e7-3460">EC3D</span></span></td>
  <td><span data-ttu-id="127e7-3461">MobWifi2</span><span class="sxs-lookup"><span data-stu-id="127e7-3461">MobWifi2</span></span></td>
 </tr>
 <tr><td>![MobWifi3](images/segoe-mdl/ec3e.png)</td>
  <td><span data-ttu-id="127e7-3463">EC3E</span><span class="sxs-lookup"><span data-stu-id="127e7-3463">EC3E</span></span></td>
  <td><span data-ttu-id="127e7-3464">MobWifi3</span><span class="sxs-lookup"><span data-stu-id="127e7-3464">MobWifi3</span></span></td>
 </tr>
 <tr><td>![MobWifi4](images/segoe-mdl/ec3f.png)</td>
  <td><span data-ttu-id="127e7-3466">EC3F</span><span class="sxs-lookup"><span data-stu-id="127e7-3466">EC3F</span></span></td>
  <td><span data-ttu-id="127e7-3467">MobWifi4</span><span class="sxs-lookup"><span data-stu-id="127e7-3467">MobWifi4</span></span></td>
 </tr>
 <tr><td>![MobAirplane](images/segoe-mdl/ec40.png)</td>
  <td><span data-ttu-id="127e7-3469">EC40</span><span class="sxs-lookup"><span data-stu-id="127e7-3469">EC40</span></span></td>
  <td><span data-ttu-id="127e7-3470">MobAirplane</span><span class="sxs-lookup"><span data-stu-id="127e7-3470">MobAirplane</span></span></td>
 </tr>
 <tr><td>![MobBluetooth](images/segoe-mdl/ec41.png)</td>
  <td><span data-ttu-id="127e7-3472">EC41</span><span class="sxs-lookup"><span data-stu-id="127e7-3472">EC41</span></span></td>
  <td><span data-ttu-id="127e7-3473">MobBluetooth</span><span class="sxs-lookup"><span data-stu-id="127e7-3473">MobBluetooth</span></span></td>
 </tr>
 <tr><td>![MobActionCenter](images/segoe-mdl/ec42.png)</td>
  <td><span data-ttu-id="127e7-3475">EC42</span><span class="sxs-lookup"><span data-stu-id="127e7-3475">EC42</span></span></td>
  <td><span data-ttu-id="127e7-3476">MobActionCenter</span><span class="sxs-lookup"><span data-stu-id="127e7-3476">MobActionCenter</span></span></td>
 </tr>
 <tr><td>![MobLocation](images/segoe-mdl/ec43.png)</td>
  <td><span data-ttu-id="127e7-3478">EC43</span><span class="sxs-lookup"><span data-stu-id="127e7-3478">EC43</span></span></td>
  <td><span data-ttu-id="127e7-3479">MobLocation</span><span class="sxs-lookup"><span data-stu-id="127e7-3479">MobLocation</span></span></td>
 </tr>
 <tr><td>![MobWifiHotspot](images/segoe-mdl/ec44.png)</td>
  <td><span data-ttu-id="127e7-3481">EC44</span><span class="sxs-lookup"><span data-stu-id="127e7-3481">EC44</span></span></td>
  <td><span data-ttu-id="127e7-3482">MobWifiHotspot</span><span class="sxs-lookup"><span data-stu-id="127e7-3482">MobWifiHotspot</span></span></td>
 </tr>
 <tr><td>![LanguageJpn](images/segoe-mdl/ec45.png)</td>
  <td><span data-ttu-id="127e7-3484">EC45</span><span class="sxs-lookup"><span data-stu-id="127e7-3484">EC45</span></span></td>
  <td><span data-ttu-id="127e7-3485">LanguageJpn</span><span class="sxs-lookup"><span data-stu-id="127e7-3485">LanguageJpn</span></span></td>
 </tr>
 <tr><td>![MobQuietHours](images/segoe-mdl/ec46.png)</td>
  <td><span data-ttu-id="127e7-3487">EC46</span><span class="sxs-lookup"><span data-stu-id="127e7-3487">EC46</span></span></td>
  <td><span data-ttu-id="127e7-3488">MobQuietHours</span><span class="sxs-lookup"><span data-stu-id="127e7-3488">MobQuietHours</span></span></td>
 </tr>
 <tr><td>![MobDrivingMode](images/segoe-mdl/ec47.png)</td>
  <td><span data-ttu-id="127e7-3490">EC47</span><span class="sxs-lookup"><span data-stu-id="127e7-3490">EC47</span></span></td>
  <td><span data-ttu-id="127e7-3491">MobDrivingMode</span><span class="sxs-lookup"><span data-stu-id="127e7-3491">MobDrivingMode</span></span></td>
 </tr>
 <tr><td>![SpeedOff](images/segoe-mdl/ec48.png)</td>
  <td><span data-ttu-id="127e7-3493">EC48</span><span class="sxs-lookup"><span data-stu-id="127e7-3493">EC48</span></span></td>
  <td><span data-ttu-id="127e7-3494">SpeedOff</span><span class="sxs-lookup"><span data-stu-id="127e7-3494">SpeedOff</span></span></td>
 </tr>
 <tr><td>![SpeedMedium](images/segoe-mdl/ec49.png)</td>
  <td><span data-ttu-id="127e7-3496">EC49</span><span class="sxs-lookup"><span data-stu-id="127e7-3496">EC49</span></span></td>
  <td><span data-ttu-id="127e7-3497">SpeedMedium</span><span class="sxs-lookup"><span data-stu-id="127e7-3497">SpeedMedium</span></span></td>
 </tr>
 <tr><td>![SpeedHigh](images/segoe-mdl/ec4a.png)</td>
  <td><span data-ttu-id="127e7-3499">EC4A</span><span class="sxs-lookup"><span data-stu-id="127e7-3499">EC4A</span></span></td>
  <td><span data-ttu-id="127e7-3500">SpeedHigh</span><span class="sxs-lookup"><span data-stu-id="127e7-3500">SpeedHigh</span></span></td>
 </tr>
 <tr><td>![ThisPC](images/segoe-mdl/ec4e.png)</td>
  <td><span data-ttu-id="127e7-3502">EC4E</span><span class="sxs-lookup"><span data-stu-id="127e7-3502">EC4E</span></span></td>
  <td><span data-ttu-id="127e7-3503">ThisPC</span><span class="sxs-lookup"><span data-stu-id="127e7-3503">ThisPC</span></span></td>
 </tr>
 <tr><td>![MusicNote](images/segoe-mdl/ec4f.png)</td>
  <td><span data-ttu-id="127e7-3505">EC4F</span><span class="sxs-lookup"><span data-stu-id="127e7-3505">EC4F</span></span></td>
  <td><span data-ttu-id="127e7-3506">MusicNote</span><span class="sxs-lookup"><span data-stu-id="127e7-3506">MusicNote</span></span></td>
 </tr>
 <tr><td>![FileExplorer](images/segoe-mdl/ec50.png)</td>
  <td><span data-ttu-id="127e7-3508">EC50</span><span class="sxs-lookup"><span data-stu-id="127e7-3508">EC50</span></span></td>
  <td><span data-ttu-id="127e7-3509">FileExplorer</span><span class="sxs-lookup"><span data-stu-id="127e7-3509">FileExplorer</span></span></td>
 </tr>
 <tr><td>![FileExplorerApp](images/segoe-mdl/ec51.png)</td>
  <td><span data-ttu-id="127e7-3511">EC51</span><span class="sxs-lookup"><span data-stu-id="127e7-3511">EC51</span></span></td>
  <td><span data-ttu-id="127e7-3512">FileExplorerApp</span><span class="sxs-lookup"><span data-stu-id="127e7-3512">FileExplorerApp</span></span></td>
 </tr>
 <tr><td>![LeftArrowKeyTime0](images/segoe-mdl/ec52.png)</td>
  <td><span data-ttu-id="127e7-3514">EC52</span><span class="sxs-lookup"><span data-stu-id="127e7-3514">EC52</span></span></td>
  <td><span data-ttu-id="127e7-3515">LeftArrowKeyTime0</span><span class="sxs-lookup"><span data-stu-id="127e7-3515">LeftArrowKeyTime0</span></span></td>
 </tr>
 <tr><td>![MicOff](images/segoe-mdl/ec54.png)</td>
  <td><span data-ttu-id="127e7-3517">EC54</span><span class="sxs-lookup"><span data-stu-id="127e7-3517">EC54</span></span></td>
  <td><span data-ttu-id="127e7-3518">MicOff</span><span class="sxs-lookup"><span data-stu-id="127e7-3518">MicOff</span></span></td>
 </tr>
 <tr><td>![MicSleep](images/segoe-mdl/ec55.png)</td>
  <td><span data-ttu-id="127e7-3520">EC55</span><span class="sxs-lookup"><span data-stu-id="127e7-3520">EC55</span></span></td>
  <td><span data-ttu-id="127e7-3521">MicSleep</span><span class="sxs-lookup"><span data-stu-id="127e7-3521">MicSleep</span></span></td>
 </tr>
 <tr><td>![MicError](images/segoe-mdl/ec56.png)</td>
  <td><span data-ttu-id="127e7-3523">EC56</span><span class="sxs-lookup"><span data-stu-id="127e7-3523">EC56</span></span></td>
  <td><span data-ttu-id="127e7-3524">MicError</span><span class="sxs-lookup"><span data-stu-id="127e7-3524">MicError</span></span></td>
 </tr>
 <tr><td>![PlaybackRate1x](images/segoe-mdl/ec57.png)</td>
  <td><span data-ttu-id="127e7-3526">EC57</span><span class="sxs-lookup"><span data-stu-id="127e7-3526">EC57</span></span></td>
  <td><span data-ttu-id="127e7-3527">PlaybackRate1x</span><span class="sxs-lookup"><span data-stu-id="127e7-3527">PlaybackRate1x</span></span></td>
 </tr>
 <tr><td>![PlaybackRateOther](images/segoe-mdl/ec58.png)</td>
  <td><span data-ttu-id="127e7-3529">EC58</span><span class="sxs-lookup"><span data-stu-id="127e7-3529">EC58</span></span></td>
  <td><span data-ttu-id="127e7-3530">PlaybackRateOther</span><span class="sxs-lookup"><span data-stu-id="127e7-3530">PlaybackRateOther</span></span></td>
 </tr>
 <tr><td>![CashDrawer](images/segoe-mdl/ec59.png)</td>
  <td><span data-ttu-id="127e7-3532">EC59</span><span class="sxs-lookup"><span data-stu-id="127e7-3532">EC59</span></span></td>
  <td><span data-ttu-id="127e7-3533">CashDrawer</span><span class="sxs-lookup"><span data-stu-id="127e7-3533">CashDrawer</span></span></td>
 </tr>
 <tr><td>![BarcodeScanner](images/segoe-mdl/ec5a.png)</td>
  <td><span data-ttu-id="127e7-3535">EC5A</span><span class="sxs-lookup"><span data-stu-id="127e7-3535">EC5A</span></span></td>
  <td><span data-ttu-id="127e7-3536">BarcodeScanner</span><span class="sxs-lookup"><span data-stu-id="127e7-3536">BarcodeScanner</span></span></td>
 </tr>
 <tr><td>![ReceiptPrinter](images/segoe-mdl/ec5b.png)</td>
  <td><span data-ttu-id="127e7-3538">EC5B</span><span class="sxs-lookup"><span data-stu-id="127e7-3538">EC5B</span></span></td>
  <td><span data-ttu-id="127e7-3539">ReceiptPrinter</span><span class="sxs-lookup"><span data-stu-id="127e7-3539">ReceiptPrinter</span></span></td>
 </tr>
 <tr><td>![MagStripeReader](images/segoe-mdl/ec5c.png)</td>
  <td><span data-ttu-id="127e7-3541">EC5C</span><span class="sxs-lookup"><span data-stu-id="127e7-3541">EC5C</span></span></td>
  <td><span data-ttu-id="127e7-3542">MagStripeReader</span><span class="sxs-lookup"><span data-stu-id="127e7-3542">MagStripeReader</span></span></td>
 </tr>
 <tr><td>![CompletedSolid](images/segoe-mdl/ec61.png)</td>
  <td><span data-ttu-id="127e7-3544">EC61</span><span class="sxs-lookup"><span data-stu-id="127e7-3544">EC61</span></span></td>
  <td><span data-ttu-id="127e7-3545">CompletedSolid</span><span class="sxs-lookup"><span data-stu-id="127e7-3545">CompletedSolid</span></span></td>
 </tr>
 <tr><td>![CompanionApp](images/segoe-mdl/ec64.png)</td>
  <td><span data-ttu-id="127e7-3547">EC64</span><span class="sxs-lookup"><span data-stu-id="127e7-3547">EC64</span></span></td>
  <td><span data-ttu-id="127e7-3548">CompanionApp</span><span class="sxs-lookup"><span data-stu-id="127e7-3548">CompanionApp</span></span></td>
 </tr>
 <tr><td>![SwipeRevealArt](images/segoe-mdl/ec6d.png)</td>
  <td><span data-ttu-id="127e7-3550">EC6D</span><span class="sxs-lookup"><span data-stu-id="127e7-3550">EC6D</span></span></td>
  <td><span data-ttu-id="127e7-3551">SwipeRevealArt</span><span class="sxs-lookup"><span data-stu-id="127e7-3551">SwipeRevealArt</span></span></td>
 </tr>
 <tr><td>![MicOn](images/segoe-mdl/ec71.png)</td>
  <td><span data-ttu-id="127e7-3553">EC71</span><span class="sxs-lookup"><span data-stu-id="127e7-3553">EC71</span></span></td>
  <td><span data-ttu-id="127e7-3554">MicOn</span><span class="sxs-lookup"><span data-stu-id="127e7-3554">MicOn</span></span></td>
 </tr>
 <tr><td>![MicClipping](images/segoe-mdl/ec72.png)</td>
  <td><span data-ttu-id="127e7-3556">EC72</span><span class="sxs-lookup"><span data-stu-id="127e7-3556">EC72</span></span></td>
  <td><span data-ttu-id="127e7-3557">MicClipping</span><span class="sxs-lookup"><span data-stu-id="127e7-3557">MicClipping</span></span></td>
 </tr>
 <tr><td>![TabletSelected](images/segoe-mdl/ec74.png)</td>
  <td><span data-ttu-id="127e7-3559">EC74</span><span class="sxs-lookup"><span data-stu-id="127e7-3559">EC74</span></span></td>
  <td><span data-ttu-id="127e7-3560">TabletSelected</span><span class="sxs-lookup"><span data-stu-id="127e7-3560">TabletSelected</span></span></td>
 </tr>
 <tr><td>![MobileSelected](images/segoe-mdl/ec75.png)</td>
  <td><span data-ttu-id="127e7-3562">EC75</span><span class="sxs-lookup"><span data-stu-id="127e7-3562">EC75</span></span></td>
  <td><span data-ttu-id="127e7-3563">MobileSelected</span><span class="sxs-lookup"><span data-stu-id="127e7-3563">MobileSelected</span></span></td>
 </tr>
 <tr><td>![LaptopSelected](images/segoe-mdl/ec76.png)</td>
  <td><span data-ttu-id="127e7-3565">EC76</span><span class="sxs-lookup"><span data-stu-id="127e7-3565">EC76</span></span></td>
  <td><span data-ttu-id="127e7-3566">LaptopSelected</span><span class="sxs-lookup"><span data-stu-id="127e7-3566">LaptopSelected</span></span></td>
 </tr>
 <tr><td>![TVMonitorSelected](images/segoe-mdl/ec77.png)</td>
  <td><span data-ttu-id="127e7-3568">EC77</span><span class="sxs-lookup"><span data-stu-id="127e7-3568">EC77</span></span></td>
  <td><span data-ttu-id="127e7-3569">TVMonitorSelected</span><span class="sxs-lookup"><span data-stu-id="127e7-3569">TVMonitorSelected</span></span></td>
 </tr>
 <tr><td>![DeveloperTools](images/segoe-mdl/ec7a.png)</td>
  <td><span data-ttu-id="127e7-3571">EC7A</span><span class="sxs-lookup"><span data-stu-id="127e7-3571">EC7A</span></span></td>
  <td><span data-ttu-id="127e7-3572">DeveloperTools</span><span class="sxs-lookup"><span data-stu-id="127e7-3572">DeveloperTools</span></span></td>
 </tr>
 <tr><td>![MobCallForwarding](images/segoe-mdl/ec7e.png)</td>
  <td><span data-ttu-id="127e7-3574">EC7E</span><span class="sxs-lookup"><span data-stu-id="127e7-3574">EC7E</span></span></td>
  <td><span data-ttu-id="127e7-3575">MobCallForwarding</span><span class="sxs-lookup"><span data-stu-id="127e7-3575">MobCallForwarding</span></span></td>
 </tr>
 <tr><td>![MobCallForwardingMirrored](images/segoe-mdl/ec7f.png)</td>
  <td><span data-ttu-id="127e7-3577">EC7F</span><span class="sxs-lookup"><span data-stu-id="127e7-3577">EC7F</span></span></td>
  <td><span data-ttu-id="127e7-3578">MobCallForwardingMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-3578">MobCallForwardingMirrored</span></span></td>
 </tr>
 <tr><td>![BodyCam](images/segoe-mdl/ec80.png)</td>
  <td><span data-ttu-id="127e7-3580">EC80</span><span class="sxs-lookup"><span data-stu-id="127e7-3580">EC80</span></span></td>
  <td><span data-ttu-id="127e7-3581">BodyCam</span><span class="sxs-lookup"><span data-stu-id="127e7-3581">BodyCam</span></span></td>
 </tr>
 <tr><td>![PoliceCar](images/segoe-mdl/ec81.png)</td>
  <td><span data-ttu-id="127e7-3583">EC81</span><span class="sxs-lookup"><span data-stu-id="127e7-3583">EC81</span></span></td>
  <td><span data-ttu-id="127e7-3584">PoliceCar</span><span class="sxs-lookup"><span data-stu-id="127e7-3584">PoliceCar</span></span></td>
 </tr>
 <tr><td>![Draw](images/segoe-mdl/ec87.png)</td>
  <td><span data-ttu-id="127e7-3586">EC87</span><span class="sxs-lookup"><span data-stu-id="127e7-3586">EC87</span></span></td>
  <td><span data-ttu-id="127e7-3587">Draw</span><span class="sxs-lookup"><span data-stu-id="127e7-3587">Draw</span></span></td>
 </tr>
 <tr><td>![DrawSolid](images/segoe-mdl/ec88.png)</td>
  <td><span data-ttu-id="127e7-3589">EC88</span><span class="sxs-lookup"><span data-stu-id="127e7-3589">EC88</span></span></td>
  <td><span data-ttu-id="127e7-3590">DrawSolid</span><span class="sxs-lookup"><span data-stu-id="127e7-3590">DrawSolid</span></span></td>
 </tr>
 <tr><td>![LowerBrightness](images/segoe-mdl/ec8a.png)</td>
  <td><span data-ttu-id="127e7-3592">EC8A</span><span class="sxs-lookup"><span data-stu-id="127e7-3592">EC8A</span></span></td>
  <td><span data-ttu-id="127e7-3593">LowerBrightness</span><span class="sxs-lookup"><span data-stu-id="127e7-3593">LowerBrightness</span></span></td>
 </tr>
 <tr><td>![ScrollUpDown](images/segoe-mdl/ec8f.png)</td>
  <td><span data-ttu-id="127e7-3595">EC8F</span><span class="sxs-lookup"><span data-stu-id="127e7-3595">EC8F</span></span></td>
  <td><span data-ttu-id="127e7-3596">ScrollUpDown</span><span class="sxs-lookup"><span data-stu-id="127e7-3596">ScrollUpDown</span></span></td>
 </tr>
 <tr><td>![DateTime](images/segoe-mdl/ec92.png)</td>
  <td><span data-ttu-id="127e7-3598">EC92</span><span class="sxs-lookup"><span data-stu-id="127e7-3598">EC92</span></span></td>
  <td><span data-ttu-id="127e7-3599">DateTime</span><span class="sxs-lookup"><span data-stu-id="127e7-3599">DateTime</span></span></td>
 </tr>
 <tr><td>![Tiles](images/segoe-mdl/eca5.png)</td>
  <td><span data-ttu-id="127e7-3601">ECA5</span><span class="sxs-lookup"><span data-stu-id="127e7-3601">ECA5</span></span></td>
  <td><span data-ttu-id="127e7-3602">Tiles</span><span class="sxs-lookup"><span data-stu-id="127e7-3602">Tiles</span></span></td>
 </tr>
 <tr><td>![PartyLeader](images/segoe-mdl/eca7.png)</td>
  <td><span data-ttu-id="127e7-3604">ECA7</span><span class="sxs-lookup"><span data-stu-id="127e7-3604">ECA7</span></span></td>
  <td><span data-ttu-id="127e7-3605">PartyLeader</span><span class="sxs-lookup"><span data-stu-id="127e7-3605">PartyLeader</span></span></td>
 </tr>
 <tr><td>![AppIconDefault](images/segoe-mdl/ecaa.png)</td>
  <td><span data-ttu-id="127e7-3607">ECAA</span><span class="sxs-lookup"><span data-stu-id="127e7-3607">ECAA</span></span></td>
  <td><span data-ttu-id="127e7-3608">AppIconDefault</span><span class="sxs-lookup"><span data-stu-id="127e7-3608">AppIconDefault</span></span></td>
 </tr>
 <tr><td>![AddSurfaceHub](images/segoe-mdl/ecc4.png)</td>
  <td><span data-ttu-id="127e7-3610">ECC4</span><span class="sxs-lookup"><span data-stu-id="127e7-3610">ECC4</span></span></td>
  <td><span data-ttu-id="127e7-3611">AddSurfaceHub</span><span class="sxs-lookup"><span data-stu-id="127e7-3611">AddSurfaceHub</span></span></td>
 </tr>
 <tr><td>![DevUpdate](images/segoe-mdl/ecc5.png)</td>
  <td><span data-ttu-id="127e7-3613">ECC5</span><span class="sxs-lookup"><span data-stu-id="127e7-3613">ECC5</span></span></td>
  <td><span data-ttu-id="127e7-3614">DevUpdate</span><span class="sxs-lookup"><span data-stu-id="127e7-3614">DevUpdate</span></span></td>
 </tr>
 <tr><td>![Unit](images/segoe-mdl/ecc6.png)</td>
  <td><span data-ttu-id="127e7-3616">ECC6</span><span class="sxs-lookup"><span data-stu-id="127e7-3616">ECC6</span></span></td>
  <td><span data-ttu-id="127e7-3617">Unit</span><span class="sxs-lookup"><span data-stu-id="127e7-3617">Unit</span></span></td>
 </tr>
 <tr><td>![AddTo](images/segoe-mdl/ecc8.png)</td>
  <td><span data-ttu-id="127e7-3619">ECC8</span><span class="sxs-lookup"><span data-stu-id="127e7-3619">ECC8</span></span></td>
  <td><span data-ttu-id="127e7-3620">AddTo</span><span class="sxs-lookup"><span data-stu-id="127e7-3620">AddTo</span></span></td>
 </tr>
 <tr><td>![RemoveFrom](images/segoe-mdl/ecc9.png)</td>
  <td><span data-ttu-id="127e7-3622">ECC9</span><span class="sxs-lookup"><span data-stu-id="127e7-3622">ECC9</span></span></td>
  <td><span data-ttu-id="127e7-3623">RemoveFrom</span><span class="sxs-lookup"><span data-stu-id="127e7-3623">RemoveFrom</span></span></td>
 </tr>
 <tr><td>![RadioBtnOff](images/segoe-mdl/ecca.png)</td>
  <td><span data-ttu-id="127e7-3625">ECCA</span><span class="sxs-lookup"><span data-stu-id="127e7-3625">ECCA</span></span></td>
  <td><span data-ttu-id="127e7-3626">RadioBtnOff</span><span class="sxs-lookup"><span data-stu-id="127e7-3626">RadioBtnOff</span></span></td>
 </tr>
 <tr><td>![RadioBtnOn](images/segoe-mdl/eccb.png)</td>
  <td><span data-ttu-id="127e7-3628">ECCB</span><span class="sxs-lookup"><span data-stu-id="127e7-3628">ECCB</span></span></td>
  <td><span data-ttu-id="127e7-3629">RadioBtnOn</span><span class="sxs-lookup"><span data-stu-id="127e7-3629">RadioBtnOn</span></span></td>
 </tr>
 <tr><td>![RadioBullet2](images/segoe-mdl/eccc.png)</td>
  <td><span data-ttu-id="127e7-3631">ECCC</span><span class="sxs-lookup"><span data-stu-id="127e7-3631">ECCC</span></span></td>
  <td><span data-ttu-id="127e7-3632">RadioBullet2</span><span class="sxs-lookup"><span data-stu-id="127e7-3632">RadioBullet2</span></span></td>
 </tr>
 <tr><td>![ExploreContent](images/segoe-mdl/eccd.png)</td>
  <td><span data-ttu-id="127e7-3634">ECCD</span><span class="sxs-lookup"><span data-stu-id="127e7-3634">ECCD</span></span></td>
  <td><span data-ttu-id="127e7-3635">ExploreContent</span><span class="sxs-lookup"><span data-stu-id="127e7-3635">ExploreContent</span></span></td>
 </tr>
 <tr><td>![ScrollMode](images/segoe-mdl/ece7.png)</td>
  <td><span data-ttu-id="127e7-3637">ECE7</span><span class="sxs-lookup"><span data-stu-id="127e7-3637">ECE7</span></span></td>
  <td><span data-ttu-id="127e7-3638">ScrollMode</span><span class="sxs-lookup"><span data-stu-id="127e7-3638">ScrollMode</span></span></td>
 </tr>
 <tr><td>![ZoomMode](images/segoe-mdl/ece8.png)</td>
  <td><span data-ttu-id="127e7-3640">ECE8</span><span class="sxs-lookup"><span data-stu-id="127e7-3640">ECE8</span></span></td>
  <td><span data-ttu-id="127e7-3641">ZoomMode</span><span class="sxs-lookup"><span data-stu-id="127e7-3641">ZoomMode</span></span></td>
 </tr>
 <tr><td>![PanMode](images/segoe-mdl/ece9.png)</td>
  <td><span data-ttu-id="127e7-3643">ECE9</span><span class="sxs-lookup"><span data-stu-id="127e7-3643">ECE9</span></span></td>
  <td><span data-ttu-id="127e7-3644">PanMode</span><span class="sxs-lookup"><span data-stu-id="127e7-3644">PanMode</span></span></td>
 </tr>
 <tr><td>![WiredUSB&nbsp;](images/segoe-mdl/ecf0.png)</td>
  <td><span data-ttu-id="127e7-3646">ECF0</span><span class="sxs-lookup"><span data-stu-id="127e7-3646">ECF0</span></span></td>
  <td><span data-ttu-id="127e7-3647">WiredUSB&nbsp;</span><span class="sxs-lookup"><span data-stu-id="127e7-3647">WiredUSB&nbsp;</span></span></td>
 </tr>
 <tr><td>![WirelessUSB](images/segoe-mdl/ecf1.png)</td>
  <td><span data-ttu-id="127e7-3649">ECF1</span><span class="sxs-lookup"><span data-stu-id="127e7-3649">ECF1</span></span></td>
  <td><span data-ttu-id="127e7-3650">WirelessUSB</span><span class="sxs-lookup"><span data-stu-id="127e7-3650">WirelessUSB</span></span></td>
 </tr>
 <tr><td>![USBSafeConnect](images/segoe-mdl/ecf3.png)</td>
  <td><span data-ttu-id="127e7-3652">ECF3</span><span class="sxs-lookup"><span data-stu-id="127e7-3652">ECF3</span></span></td>
  <td><span data-ttu-id="127e7-3653">USBSafeConnect</span><span class="sxs-lookup"><span data-stu-id="127e7-3653">USBSafeConnect</span></span></td>
 </tr>
 <tr><td>![ActionCenterNotificationMirrored](images/segoe-mdl/ed0c.png)</td>
  <td><span data-ttu-id="127e7-3655">ED0C</span><span class="sxs-lookup"><span data-stu-id="127e7-3655">ED0C</span></span></td>
  <td><span data-ttu-id="127e7-3656">ActionCenterNotificationMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-3656">ActionCenterNotificationMirrored</span></span></td>
 </tr>
 <tr><td>![ActionCenterMirrored](images/segoe-mdl/ed0d.png)</td>
  <td><span data-ttu-id="127e7-3658">ED0D</span><span class="sxs-lookup"><span data-stu-id="127e7-3658">ED0D</span></span></td>
  <td><span data-ttu-id="127e7-3659">ActionCenterMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-3659">ActionCenterMirrored</span></span></td>
 </tr>
 <tr><td>![ResetDevice](images/segoe-mdl/ed10.png)</td>
  <td><span data-ttu-id="127e7-3661">ED10</span><span class="sxs-lookup"><span data-stu-id="127e7-3661">ED10</span></span></td>
  <td><span data-ttu-id="127e7-3662">ResetDevice</span><span class="sxs-lookup"><span data-stu-id="127e7-3662">ResetDevice</span></span></td>
 </tr>
 <tr><td>![Feedback](images/segoe-mdl/ed15.png)</td>
  <td><span data-ttu-id="127e7-3664">ED15</span><span class="sxs-lookup"><span data-stu-id="127e7-3664">ED15</span></span></td>
  <td><span data-ttu-id="127e7-3665">Feedback</span><span class="sxs-lookup"><span data-stu-id="127e7-3665">Feedback</span></span></td>
 </tr>
 <tr><td>![Subtitles](images/segoe-mdl/ed1e.png)</td>
  <td><span data-ttu-id="127e7-3667">ED1E</span><span class="sxs-lookup"><span data-stu-id="127e7-3667">ED1E</span></span></td>
  <td><span data-ttu-id="127e7-3668">Subtitles</span><span class="sxs-lookup"><span data-stu-id="127e7-3668">Subtitles</span></span></td>
 </tr>
 <tr><td>![SubtitlesAudio](images/segoe-mdl/ed1f.png)</td>
  <td><span data-ttu-id="127e7-3670">ED1F</span><span class="sxs-lookup"><span data-stu-id="127e7-3670">ED1F</span></span></td>
  <td><span data-ttu-id="127e7-3671">SubtitlesAudio</span><span class="sxs-lookup"><span data-stu-id="127e7-3671">SubtitlesAudio</span></span></td>
 </tr>
 <tr><td>![CalendarMirrored](images/segoe-mdl/ed28.png)</td>
  <td><span data-ttu-id="127e7-3673">ED28</span><span class="sxs-lookup"><span data-stu-id="127e7-3673">ED28</span></span></td>
  <td><span data-ttu-id="127e7-3674">CalendarMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-3674">CalendarMirrored</span></span></td>
 </tr>
 <tr><td>![eSIM](images/segoe-mdl/ed2a.png)</td>
  <td><span data-ttu-id="127e7-3676">ED2A</span><span class="sxs-lookup"><span data-stu-id="127e7-3676">ED2A</span></span></td>
  <td><span data-ttu-id="127e7-3677">eSIM</span><span class="sxs-lookup"><span data-stu-id="127e7-3677">eSIM</span></span></td>
 </tr>
 <tr><td>![eSIMNoProfile](images/segoe-mdl/ed2b.png)</td>
  <td><span data-ttu-id="127e7-3679">ED2B</span><span class="sxs-lookup"><span data-stu-id="127e7-3679">ED2B</span></span></td>
  <td><span data-ttu-id="127e7-3680">eSIMNoProfile</span><span class="sxs-lookup"><span data-stu-id="127e7-3680">eSIMNoProfile</span></span></td>
 </tr>
 <tr><td>![eSIMLocked](images/segoe-mdl/ed2c.png)</td>
  <td><span data-ttu-id="127e7-3682">ED2C</span><span class="sxs-lookup"><span data-stu-id="127e7-3682">ED2C</span></span></td>
  <td><span data-ttu-id="127e7-3683">eSIMLocked</span><span class="sxs-lookup"><span data-stu-id="127e7-3683">eSIMLocked</span></span></td>
 </tr>
 <tr><td>![eSIMBusy](images/segoe-mdl/ed2d.png)</td>
  <td><span data-ttu-id="127e7-3685">ED2D</span><span class="sxs-lookup"><span data-stu-id="127e7-3685">ED2D</span></span></td>
  <td><span data-ttu-id="127e7-3686">eSIMBusy</span><span class="sxs-lookup"><span data-stu-id="127e7-3686">eSIMBusy</span></span></td>
 </tr>
 <tr><td>![SignalError](images/segoe-mdl/ed2e.png)</td>
  <td><span data-ttu-id="127e7-3688">ED2E</span><span class="sxs-lookup"><span data-stu-id="127e7-3688">ED2E</span></span></td>
  <td><span data-ttu-id="127e7-3689">SignalError</span><span class="sxs-lookup"><span data-stu-id="127e7-3689">SignalError</span></span></td>
 </tr>
 <tr><td>![StreamingEnterprise](images/segoe-mdl/ed2f.png)</td>
  <td><span data-ttu-id="127e7-3691">ED2F</span><span class="sxs-lookup"><span data-stu-id="127e7-3691">ED2F</span></span></td>
  <td><span data-ttu-id="127e7-3692">StreamingEnterprise</span><span class="sxs-lookup"><span data-stu-id="127e7-3692">StreamingEnterprise</span></span></td>
 </tr>
 <tr><td>![Headphone0](images/segoe-mdl/ed30.png)</td>
  <td><span data-ttu-id="127e7-3694">ED30</span><span class="sxs-lookup"><span data-stu-id="127e7-3694">ED30</span></span></td>
  <td><span data-ttu-id="127e7-3695">Headphone0</span><span class="sxs-lookup"><span data-stu-id="127e7-3695">Headphone0</span></span></td>
 </tr>
 <tr><td>![Headphone1](images/segoe-mdl/ed31.png)</td>
  <td><span data-ttu-id="127e7-3697">ED31</span><span class="sxs-lookup"><span data-stu-id="127e7-3697">ED31</span></span></td>
  <td><span data-ttu-id="127e7-3698">Headphone1</span><span class="sxs-lookup"><span data-stu-id="127e7-3698">Headphone1</span></span></td>
 </tr>
 <tr><td>![Headphone2](images/segoe-mdl/ed32.png)</td>
  <td><span data-ttu-id="127e7-3700">ED32</span><span class="sxs-lookup"><span data-stu-id="127e7-3700">ED32</span></span></td>
  <td><span data-ttu-id="127e7-3701">Headphone2</span><span class="sxs-lookup"><span data-stu-id="127e7-3701">Headphone2</span></span></td>
 </tr>
 <tr><td>![Headphone3](images/segoe-mdl/ed33.png)</td>
  <td><span data-ttu-id="127e7-3703">ED33</span><span class="sxs-lookup"><span data-stu-id="127e7-3703">ED33</span></span></td>
  <td><span data-ttu-id="127e7-3704">Headphone3</span><span class="sxs-lookup"><span data-stu-id="127e7-3704">Headphone3</span></span></td>
 </tr>
 <tr><td>![KeyboardBrightness](images/segoe-mdl/ed39.png)</td>
  <td><span data-ttu-id="127e7-3706">ED39</span><span class="sxs-lookup"><span data-stu-id="127e7-3706">ED39</span></span></td>
  <td><span data-ttu-id="127e7-3707">KeyboardBrightness</span><span class="sxs-lookup"><span data-stu-id="127e7-3707">KeyboardBrightness</span></span></td>
 </tr>
 <tr><td>![KeyboardLowerBrightness](images/segoe-mdl/ed3a.png)</td>
  <td><span data-ttu-id="127e7-3709">ED3A</span><span class="sxs-lookup"><span data-stu-id="127e7-3709">ED3A</span></span></td>
  <td><span data-ttu-id="127e7-3710">KeyboardLowerBrightness</span><span class="sxs-lookup"><span data-stu-id="127e7-3710">KeyboardLowerBrightness</span></span></td>
 </tr>
 <tr><td>![SkipBack10](images/segoe-mdl/ed3c.png)</td>
  <td><span data-ttu-id="127e7-3712">ED3C</span><span class="sxs-lookup"><span data-stu-id="127e7-3712">ED3C</span></span></td>
  <td><span data-ttu-id="127e7-3713">SkipBack10</span><span class="sxs-lookup"><span data-stu-id="127e7-3713">SkipBack10</span></span></td>
 </tr>
 <tr><td>![SkipForward30](images/segoe-mdl/ed3d.png)</td>
  <td><span data-ttu-id="127e7-3715">ED3D</span><span class="sxs-lookup"><span data-stu-id="127e7-3715">ED3D</span></span></td>
  <td><span data-ttu-id="127e7-3716">SkipForward30</span><span class="sxs-lookup"><span data-stu-id="127e7-3716">SkipForward30</span></span></td>
 </tr>
 <tr><td>![TreeFolderFolder](images/segoe-mdl/ed41.png)</td>
  <td><span data-ttu-id="127e7-3718">ED41</span><span class="sxs-lookup"><span data-stu-id="127e7-3718">ED41</span></span></td>
  <td><span data-ttu-id="127e7-3719">TreeFolderFolder</span><span class="sxs-lookup"><span data-stu-id="127e7-3719">TreeFolderFolder</span></span></td>
 </tr>
 <tr><td>![TreeFolderFolderFill](images/segoe-mdl/ed42.png)</td>
  <td><span data-ttu-id="127e7-3721">ED42</span><span class="sxs-lookup"><span data-stu-id="127e7-3721">ED42</span></span></td>
  <td><span data-ttu-id="127e7-3722">TreeFolderFolderFill</span><span class="sxs-lookup"><span data-stu-id="127e7-3722">TreeFolderFolderFill</span></span></td>
 </tr>
 <tr><td>![TreeFolderFolderOpen](images/segoe-mdl/ed43.png)</td>
  <td><span data-ttu-id="127e7-3724">ED43</span><span class="sxs-lookup"><span data-stu-id="127e7-3724">ED43</span></span></td>
  <td><span data-ttu-id="127e7-3725">TreeFolderFolderOpen</span><span class="sxs-lookup"><span data-stu-id="127e7-3725">TreeFolderFolderOpen</span></span></td>
 </tr>
 <tr><td>![TreeFolderFolderOpenFill](images/segoe-mdl/ed44.png)</td>
  <td><span data-ttu-id="127e7-3727">ED44</span><span class="sxs-lookup"><span data-stu-id="127e7-3727">ED44</span></span></td>
  <td><span data-ttu-id="127e7-3728">TreeFolderFolderOpenFill</span><span class="sxs-lookup"><span data-stu-id="127e7-3728">TreeFolderFolderOpenFill</span></span></td>
 </tr>
 <tr><td>![MultimediaDMP](images/segoe-mdl/ed47.png)</td>
  <td><span data-ttu-id="127e7-3730">ED47</span><span class="sxs-lookup"><span data-stu-id="127e7-3730">ED47</span></span></td>
  <td><span data-ttu-id="127e7-3731">MultimediaDMP</span><span class="sxs-lookup"><span data-stu-id="127e7-3731">MultimediaDMP</span></span></td>
 </tr>
 <tr><td>![KeyboardOneHanded](images/segoe-mdl/ed4c.png)</td>
  <td><span data-ttu-id="127e7-3733">ED4C</span><span class="sxs-lookup"><span data-stu-id="127e7-3733">ED4C</span></span></td>
  <td><span data-ttu-id="127e7-3734">KeyboardOneHanded</span><span class="sxs-lookup"><span data-stu-id="127e7-3734">KeyboardOneHanded</span></span></td>
 </tr>
 <tr><td>![Narrator](images/segoe-mdl/ed4d.png)</td>
  <td><span data-ttu-id="127e7-3736">ED4D</span><span class="sxs-lookup"><span data-stu-id="127e7-3736">ED4D</span></span></td>
  <td><span data-ttu-id="127e7-3737">Narrator</span><span class="sxs-lookup"><span data-stu-id="127e7-3737">Narrator</span></span></td>
 </tr>
 <tr><td>![EmojiTabPeople](images/segoe-mdl/ed53.png)</td>
  <td><span data-ttu-id="127e7-3739">ED53</span><span class="sxs-lookup"><span data-stu-id="127e7-3739">ED53</span></span></td>
  <td><span data-ttu-id="127e7-3740">EmojiTabPeople</span><span class="sxs-lookup"><span data-stu-id="127e7-3740">EmojiTabPeople</span></span></td>
 </tr>
 <tr><td>![EmojiTabSmilesAnimals](images/segoe-mdl/ed54.png)</td>
  <td><span data-ttu-id="127e7-3742">ED54</span><span class="sxs-lookup"><span data-stu-id="127e7-3742">ED54</span></span></td>
  <td><span data-ttu-id="127e7-3743">EmojiTabSmilesAnimals</span><span class="sxs-lookup"><span data-stu-id="127e7-3743">EmojiTabSmilesAnimals</span></span></td>
 </tr>
 <tr><td>![EmojiTabCelebrationObjects](images/segoe-mdl/ed55.png)</td>
  <td><span data-ttu-id="127e7-3745">ED55</span><span class="sxs-lookup"><span data-stu-id="127e7-3745">ED55</span></span></td>
  <td><span data-ttu-id="127e7-3746">EmojiTabCelebrationObjects</span><span class="sxs-lookup"><span data-stu-id="127e7-3746">EmojiTabCelebrationObjects</span></span></td>
 </tr>
 <tr><td>![EmojiTabFoodPlants](images/segoe-mdl/ed56.png)</td>
  <td><span data-ttu-id="127e7-3748">ED56</span><span class="sxs-lookup"><span data-stu-id="127e7-3748">ED56</span></span></td>
  <td><span data-ttu-id="127e7-3749">EmojiTabFoodPlants</span><span class="sxs-lookup"><span data-stu-id="127e7-3749">EmojiTabFoodPlants</span></span></td>
 </tr>
 <tr><td>![EmojiTabTransitPlaces](images/segoe-mdl/ed57.png)</td>
  <td><span data-ttu-id="127e7-3751">ED57</span><span class="sxs-lookup"><span data-stu-id="127e7-3751">ED57</span></span></td>
  <td><span data-ttu-id="127e7-3752">EmojiTabTransitPlaces</span><span class="sxs-lookup"><span data-stu-id="127e7-3752">EmojiTabTransitPlaces</span></span></td>
 </tr>
 <tr><td>![EmojiTabSymbols](images/segoe-mdl/ed58.png)</td>
  <td><span data-ttu-id="127e7-3754">ED58</span><span class="sxs-lookup"><span data-stu-id="127e7-3754">ED58</span></span></td>
  <td><span data-ttu-id="127e7-3755">EmojiTabSymbols</span><span class="sxs-lookup"><span data-stu-id="127e7-3755">EmojiTabSymbols</span></span></td>
 </tr>
 <tr><td>![EmojiTabTextSmiles](images/segoe-mdl/ed59.png)</td>
  <td><span data-ttu-id="127e7-3757">ED59</span><span class="sxs-lookup"><span data-stu-id="127e7-3757">ED59</span></span></td>
  <td><span data-ttu-id="127e7-3758">EmojiTabTextSmiles</span><span class="sxs-lookup"><span data-stu-id="127e7-3758">EmojiTabTextSmiles</span></span></td>
 </tr>
 <tr><td>![EmojiTabFavorites](images/segoe-mdl/ed5a.png)</td>
  <td><span data-ttu-id="127e7-3760">ED5A</span><span class="sxs-lookup"><span data-stu-id="127e7-3760">ED5A</span></span></td>
  <td><span data-ttu-id="127e7-3761">EmojiTabFavorites</span><span class="sxs-lookup"><span data-stu-id="127e7-3761">EmojiTabFavorites</span></span></td>
 </tr>
 <tr><td>![EmojiSwatch](images/segoe-mdl/ed5b.png)</td>
  <td><span data-ttu-id="127e7-3763">ED5B</span><span class="sxs-lookup"><span data-stu-id="127e7-3763">ED5B</span></span></td>
  <td><span data-ttu-id="127e7-3764">EmojiSwatch</span><span class="sxs-lookup"><span data-stu-id="127e7-3764">EmojiSwatch</span></span></td>
 </tr>
 <tr><td>![ConnectApp](images/segoe-mdl/ed5c.png)</td>
  <td><span data-ttu-id="127e7-3766">ED5C</span><span class="sxs-lookup"><span data-stu-id="127e7-3766">ED5C</span></span></td>
  <td><span data-ttu-id="127e7-3767">ConnectApp</span><span class="sxs-lookup"><span data-stu-id="127e7-3767">ConnectApp</span></span></td>
 </tr>
 <tr><td>![CompanionDeviceFramework](images/segoe-mdl/ed5d.png)</td>
  <td><span data-ttu-id="127e7-3769">ED5D</span><span class="sxs-lookup"><span data-stu-id="127e7-3769">ED5D</span></span></td>
  <td><span data-ttu-id="127e7-3770">CompanionDeviceFramework</span><span class="sxs-lookup"><span data-stu-id="127e7-3770">CompanionDeviceFramework</span></span></td>
 </tr>
 <tr><td>![Ruler](images/segoe-mdl/ed5e.png)</td>
  <td><span data-ttu-id="127e7-3772">ED5E</span><span class="sxs-lookup"><span data-stu-id="127e7-3772">ED5E</span></span></td>
  <td><span data-ttu-id="127e7-3773">Ruler</span><span class="sxs-lookup"><span data-stu-id="127e7-3773">Ruler</span></span></td>
 </tr>
 <tr><td>![FingerInking](images/segoe-mdl/ed5f.png)</td>
  <td><span data-ttu-id="127e7-3775">ED5F</span><span class="sxs-lookup"><span data-stu-id="127e7-3775">ED5F</span></span></td>
  <td><span data-ttu-id="127e7-3776">FingerInking</span><span class="sxs-lookup"><span data-stu-id="127e7-3776">FingerInking</span></span></td>
 </tr>
 <tr><td>![StrokeErase](images/segoe-mdl/ed60.png)</td>
  <td><span data-ttu-id="127e7-3778">ED60</span><span class="sxs-lookup"><span data-stu-id="127e7-3778">ED60</span></span></td>
  <td><span data-ttu-id="127e7-3779">StrokeErase</span><span class="sxs-lookup"><span data-stu-id="127e7-3779">StrokeErase</span></span></td>
 </tr>
 <tr><td>![PointErase](images/segoe-mdl/ed61.png)</td>
  <td><span data-ttu-id="127e7-3781">ED61</span><span class="sxs-lookup"><span data-stu-id="127e7-3781">ED61</span></span></td>
  <td><span data-ttu-id="127e7-3782">PointErase</span><span class="sxs-lookup"><span data-stu-id="127e7-3782">PointErase</span></span></td>
 </tr>
 <tr><td>![ClearAllInk](images/segoe-mdl/ed62.png)</td>
  <td><span data-ttu-id="127e7-3784">ED62</span><span class="sxs-lookup"><span data-stu-id="127e7-3784">ED62</span></span></td>
  <td><span data-ttu-id="127e7-3785">ClearAllInk</span><span class="sxs-lookup"><span data-stu-id="127e7-3785">ClearAllInk</span></span></td>
 </tr>
 <tr><td>![Pencil](images/segoe-mdl/ed63.png)</td>
  <td><span data-ttu-id="127e7-3787">ED63</span><span class="sxs-lookup"><span data-stu-id="127e7-3787">ED63</span></span></td>
  <td><span data-ttu-id="127e7-3788">Pencil</span><span class="sxs-lookup"><span data-stu-id="127e7-3788">Pencil</span></span></td>
 </tr>
 <tr><td>![Marker](images/segoe-mdl/ed64.png)</td>
  <td><span data-ttu-id="127e7-3790">ED64</span><span class="sxs-lookup"><span data-stu-id="127e7-3790">ED64</span></span></td>
  <td><span data-ttu-id="127e7-3791">Marker</span><span class="sxs-lookup"><span data-stu-id="127e7-3791">Marker</span></span></td>
 </tr>
 <tr><td>![InkingCaret](images/segoe-mdl/ed65.png)</td>
  <td><span data-ttu-id="127e7-3793">ED65</span><span class="sxs-lookup"><span data-stu-id="127e7-3793">ED65</span></span></td>
  <td><span data-ttu-id="127e7-3794">InkingCaret</span><span class="sxs-lookup"><span data-stu-id="127e7-3794">InkingCaret</span></span></td>
 </tr>
 <tr><td>![InkingColorOutline](images/segoe-mdl/ed66.png)</td>
  <td><span data-ttu-id="127e7-3796">ED66</span><span class="sxs-lookup"><span data-stu-id="127e7-3796">ED66</span></span></td>
  <td><span data-ttu-id="127e7-3797">InkingColorOutline</span><span class="sxs-lookup"><span data-stu-id="127e7-3797">InkingColorOutline</span></span></td>
 </tr>
 <tr><td>![InkingColorFill](images/segoe-mdl/ed67.png)</td>
  <td><span data-ttu-id="127e7-3799">ED67</span><span class="sxs-lookup"><span data-stu-id="127e7-3799">ED67</span></span></td>
  <td><span data-ttu-id="127e7-3800">InkingColorFill</span><span class="sxs-lookup"><span data-stu-id="127e7-3800">InkingColorFill</span></span></td>
 </tr>
 <tr><td>![HardDrive](images/segoe-mdl/eda2.png)</td>
  <td><span data-ttu-id="127e7-3802">EDA2</span><span class="sxs-lookup"><span data-stu-id="127e7-3802">EDA2</span></span></td>
  <td><span data-ttu-id="127e7-3803">HardDrive</span><span class="sxs-lookup"><span data-stu-id="127e7-3803">HardDrive</span></span></td>
 </tr>
 <tr><td>![NetworkAdapter](images/segoe-mdl/eda3.png)</td>
  <td><span data-ttu-id="127e7-3805">EDA3</span><span class="sxs-lookup"><span data-stu-id="127e7-3805">EDA3</span></span></td>
  <td><span data-ttu-id="127e7-3806">NetworkAdapter</span><span class="sxs-lookup"><span data-stu-id="127e7-3806">NetworkAdapter</span></span></td>
 </tr>
 <tr><td>![Touchscreen](images/segoe-mdl/eda4.png)</td>
  <td><span data-ttu-id="127e7-3808">EDA4</span><span class="sxs-lookup"><span data-stu-id="127e7-3808">EDA4</span></span></td>
  <td><span data-ttu-id="127e7-3809">Touchscreen</span><span class="sxs-lookup"><span data-stu-id="127e7-3809">Touchscreen</span></span></td>
 </tr>
 <tr><td>![NetworkPrinter](images/segoe-mdl/eda5.png)</td>
  <td><span data-ttu-id="127e7-3811">EDA5</span><span class="sxs-lookup"><span data-stu-id="127e7-3811">EDA5</span></span></td>
  <td><span data-ttu-id="127e7-3812">NetworkPrinter</span><span class="sxs-lookup"><span data-stu-id="127e7-3812">NetworkPrinter</span></span></td>
 </tr>
 <tr><td>![CloudPrinter](images/segoe-mdl/eda6.png)</td>
  <td><span data-ttu-id="127e7-3814">EDA6</span><span class="sxs-lookup"><span data-stu-id="127e7-3814">EDA6</span></span></td>
  <td><span data-ttu-id="127e7-3815">CloudPrinter</span><span class="sxs-lookup"><span data-stu-id="127e7-3815">CloudPrinter</span></span></td>
 </tr>
 <tr><td>![KeyboardShortcut](images/segoe-mdl/eda7.png)</td>
  <td><span data-ttu-id="127e7-3817">EDA7</span><span class="sxs-lookup"><span data-stu-id="127e7-3817">EDA7</span></span></td>
  <td><span data-ttu-id="127e7-3818">KeyboardShortcut</span><span class="sxs-lookup"><span data-stu-id="127e7-3818">KeyboardShortcut</span></span></td>
 </tr>
 <tr><td>![BrushSize](images/segoe-mdl/eda8.png)</td>
  <td><span data-ttu-id="127e7-3820">EDA8</span><span class="sxs-lookup"><span data-stu-id="127e7-3820">EDA8</span></span></td>
  <td><span data-ttu-id="127e7-3821">BrushSize</span><span class="sxs-lookup"><span data-stu-id="127e7-3821">BrushSize</span></span></td>
 </tr>
 <tr><td>![NarratorForward](images/segoe-mdl/eda9.png)</td>
  <td><span data-ttu-id="127e7-3823">EDA9</span><span class="sxs-lookup"><span data-stu-id="127e7-3823">EDA9</span></span></td>
  <td><span data-ttu-id="127e7-3824">NarratorForward</span><span class="sxs-lookup"><span data-stu-id="127e7-3824">NarratorForward</span></span></td>
 </tr>
 <tr><td>![NarratorForwardMirrored](images/segoe-mdl/edaa.png)</td>
  <td><span data-ttu-id="127e7-3826">EDAA</span><span class="sxs-lookup"><span data-stu-id="127e7-3826">EDAA</span></span></td>
  <td><span data-ttu-id="127e7-3827">NarratorForwardMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-3827">NarratorForwardMirrored</span></span></td>
 </tr>
 <tr><td>![SyncBadge12](images/segoe-mdl/edab.png)</td>
  <td><span data-ttu-id="127e7-3829">EDAB</span><span class="sxs-lookup"><span data-stu-id="127e7-3829">EDAB</span></span></td>
  <td><span data-ttu-id="127e7-3830">SyncBadge12</span><span class="sxs-lookup"><span data-stu-id="127e7-3830">SyncBadge12</span></span></td>
 </tr>
 <tr><td>![RingerBadge12](images/segoe-mdl/edac.png)</td>
  <td><span data-ttu-id="127e7-3832">EDAC</span><span class="sxs-lookup"><span data-stu-id="127e7-3832">EDAC</span></span></td>
  <td><span data-ttu-id="127e7-3833">RingerBadge12</span><span class="sxs-lookup"><span data-stu-id="127e7-3833">RingerBadge12</span></span></td>
 </tr>
 <tr><td>![AsteriskBadge12](images/segoe-mdl/edad.png)</td>
  <td><span data-ttu-id="127e7-3835">EDAD</span><span class="sxs-lookup"><span data-stu-id="127e7-3835">EDAD</span></span></td>
  <td><span data-ttu-id="127e7-3836">AsteriskBadge12</span><span class="sxs-lookup"><span data-stu-id="127e7-3836">AsteriskBadge12</span></span></td>
 </tr>
 <tr><td>![ErrorBadge12](images/segoe-mdl/edae.png)</td>
  <td><span data-ttu-id="127e7-3838">EDAE</span><span class="sxs-lookup"><span data-stu-id="127e7-3838">EDAE</span></span></td>
  <td><span data-ttu-id="127e7-3839">ErrorBadge12</span><span class="sxs-lookup"><span data-stu-id="127e7-3839">ErrorBadge12</span></span></td>
 </tr>
 <tr><td>![CircleRingBadge12](images/segoe-mdl/edaf.png)</td>
  <td><span data-ttu-id="127e7-3841">EDAF</span><span class="sxs-lookup"><span data-stu-id="127e7-3841">EDAF</span></span></td>
  <td><span data-ttu-id="127e7-3842">CircleRingBadge12</span><span class="sxs-lookup"><span data-stu-id="127e7-3842">CircleRingBadge12</span></span></td>
 </tr>
 <tr><td>![CircleFillBadge12](images/segoe-mdl/edb0.png)</td>
  <td><span data-ttu-id="127e7-3844">EDB0</span><span class="sxs-lookup"><span data-stu-id="127e7-3844">EDB0</span></span></td>
  <td><span data-ttu-id="127e7-3845">CircleFillBadge12</span><span class="sxs-lookup"><span data-stu-id="127e7-3845">CircleFillBadge12</span></span></td>
 </tr>
 <tr><td>![ImportantBadge12](images/segoe-mdl/edb1.png)</td>
  <td><span data-ttu-id="127e7-3847">EDB1</span><span class="sxs-lookup"><span data-stu-id="127e7-3847">EDB1</span></span></td>
  <td><span data-ttu-id="127e7-3848">ImportantBadge12</span><span class="sxs-lookup"><span data-stu-id="127e7-3848">ImportantBadge12</span></span></td>
 </tr>
 <tr><td>![MailBadge12](images/segoe-mdl/edb3.png)</td>
  <td><span data-ttu-id="127e7-3850">EDB3</span><span class="sxs-lookup"><span data-stu-id="127e7-3850">EDB3</span></span></td>
  <td><span data-ttu-id="127e7-3851">MailBadge12</span><span class="sxs-lookup"><span data-stu-id="127e7-3851">MailBadge12</span></span></td>
 </tr>
 <tr><td>![PauseBadge12](images/segoe-mdl/edb4.png)</td>
  <td><span data-ttu-id="127e7-3853">EDB4</span><span class="sxs-lookup"><span data-stu-id="127e7-3853">EDB4</span></span></td>
  <td><span data-ttu-id="127e7-3854">PauseBadge12</span><span class="sxs-lookup"><span data-stu-id="127e7-3854">PauseBadge12</span></span></td>
 </tr>
 <tr><td>![PlayBadge12](images/segoe-mdl/edb5.png)</td>
  <td><span data-ttu-id="127e7-3856">EDB5</span><span class="sxs-lookup"><span data-stu-id="127e7-3856">EDB5</span></span></td>
  <td><span data-ttu-id="127e7-3857">PlayBadge12</span><span class="sxs-lookup"><span data-stu-id="127e7-3857">PlayBadge12</span></span></td>
 </tr>
 <tr><td>![PenWorkspace](images/segoe-mdl/edc6.png)</td>
  <td><span data-ttu-id="127e7-3859">EDC6</span><span class="sxs-lookup"><span data-stu-id="127e7-3859">EDC6</span></span></td>
  <td><span data-ttu-id="127e7-3860">PenWorkspace</span><span class="sxs-lookup"><span data-stu-id="127e7-3860">PenWorkspace</span></span></td>
 </tr>
 <tr><td>![Export](images/segoe-mdl/ede1.png)</td>
  <td><span data-ttu-id="127e7-3862">EDE1</span><span class="sxs-lookup"><span data-stu-id="127e7-3862">EDE1</span></span></td>
  <td><span data-ttu-id="127e7-3863">Export</span><span class="sxs-lookup"><span data-stu-id="127e7-3863">Export</span></span></td>
 </tr>
 <tr><td>![ExportMirrored](images/segoe-mdl/ede2.png)</td>
  <td><span data-ttu-id="127e7-3865">EDE2</span><span class="sxs-lookup"><span data-stu-id="127e7-3865">EDE2</span></span></td>
  <td><span data-ttu-id="127e7-3866">ExportMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-3866">ExportMirrored</span></span></td>
 </tr>
 <tr><td>![CaligraphyPen](images/segoe-mdl/edfb.png)</td>
  <td><span data-ttu-id="127e7-3868">EDFB</span><span class="sxs-lookup"><span data-stu-id="127e7-3868">EDFB</span></span></td>
  <td><span data-ttu-id="127e7-3869">CaligraphyPen</span><span class="sxs-lookup"><span data-stu-id="127e7-3869">CaligraphyPen</span></span></td>
 </tr>
 <tr><td>![ReplyMirrored](images/segoe-mdl/ee35.png)</td>
  <td><span data-ttu-id="127e7-3871">EE35</span><span class="sxs-lookup"><span data-stu-id="127e7-3871">EE35</span></span></td>
  <td><span data-ttu-id="127e7-3872">ReplyMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-3872">ReplyMirrored</span></span></td>
 </tr>
 <tr><td>![LockscreenDesktop](images/segoe-mdl/ee3f.png)</td>
  <td><span data-ttu-id="127e7-3874">EE3F</span><span class="sxs-lookup"><span data-stu-id="127e7-3874">EE3F</span></span></td>
  <td><span data-ttu-id="127e7-3875">LockscreenDesktop</span><span class="sxs-lookup"><span data-stu-id="127e7-3875">LockscreenDesktop</span></span></td>
 </tr>
 <tr><td>![Multitask16](images/segoe-mdl/ee40.png)</td>
  <td><span data-ttu-id="127e7-3877">EE40</span><span class="sxs-lookup"><span data-stu-id="127e7-3877">EE40</span></span></td>
  <td><span data-ttu-id="127e7-3878">Multitask16</span><span class="sxs-lookup"><span data-stu-id="127e7-3878">Multitask16</span></span></td>
 </tr>
 <tr><td>![Play36](images/segoe-mdl/ee4a.png)</td>
  <td><span data-ttu-id="127e7-3880">EE4A</span><span class="sxs-lookup"><span data-stu-id="127e7-3880">EE4A</span></span></td>
  <td><span data-ttu-id="127e7-3881">Play36</span><span class="sxs-lookup"><span data-stu-id="127e7-3881">Play36</span></span></td>
 </tr>
 <tr><td>![PenPalette](images/segoe-mdl/ee56.png)</td>
  <td><span data-ttu-id="127e7-3883">EE56</span><span class="sxs-lookup"><span data-stu-id="127e7-3883">EE56</span></span></td>
  <td><span data-ttu-id="127e7-3884">PenPalette</span><span class="sxs-lookup"><span data-stu-id="127e7-3884">PenPalette</span></span></td>
 </tr>
 <tr><td>![GuestUser](images/segoe-mdl/ee57.png)</td>
  <td><span data-ttu-id="127e7-3886">EE57</span><span class="sxs-lookup"><span data-stu-id="127e7-3886">EE57</span></span></td>
  <td><span data-ttu-id="127e7-3887">GuestUser</span><span class="sxs-lookup"><span data-stu-id="127e7-3887">GuestUser</span></span></td>
 </tr>
 <tr><td>![SettingsBattery](images/segoe-mdl/ee63.png)</td>
  <td><span data-ttu-id="127e7-3889">EE63</span><span class="sxs-lookup"><span data-stu-id="127e7-3889">EE63</span></span></td>
  <td><span data-ttu-id="127e7-3890">SettingsBattery</span><span class="sxs-lookup"><span data-stu-id="127e7-3890">SettingsBattery</span></span></td>
 </tr>
 <tr><td>![TaskbarPhone](images/segoe-mdl/ee64.png)</td>
  <td><span data-ttu-id="127e7-3892">EE64</span><span class="sxs-lookup"><span data-stu-id="127e7-3892">EE64</span></span></td>
  <td><span data-ttu-id="127e7-3893">TaskbarPhone</span><span class="sxs-lookup"><span data-stu-id="127e7-3893">TaskbarPhone</span></span></td>
 </tr>
 <tr><td>![LockScreenGlance](images/segoe-mdl/ee65.png)</td>
  <td><span data-ttu-id="127e7-3895">EE65</span><span class="sxs-lookup"><span data-stu-id="127e7-3895">EE65</span></span></td>
  <td><span data-ttu-id="127e7-3896">LockScreenGlance</span><span class="sxs-lookup"><span data-stu-id="127e7-3896">LockScreenGlance</span></span></td>
 </tr>
 <tr><td>![ImageExport](images/segoe-mdl/ee71.png)</td>
  <td><span data-ttu-id="127e7-3898">EE71</span><span class="sxs-lookup"><span data-stu-id="127e7-3898">EE71</span></span></td>
  <td><span data-ttu-id="127e7-3899">ImageExport</span><span class="sxs-lookup"><span data-stu-id="127e7-3899">ImageExport</span></span></td>
 </tr>
 <tr><td>![WifiEthernet](images/segoe-mdl/ee77.png)</td>
  <td><span data-ttu-id="127e7-3901">EE77</span><span class="sxs-lookup"><span data-stu-id="127e7-3901">EE77</span></span></td>
  <td><span data-ttu-id="127e7-3902">WifiEthernet</span><span class="sxs-lookup"><span data-stu-id="127e7-3902">WifiEthernet</span></span></td>
 </tr>
 <tr><td>![ActionCenterQuiet](images/segoe-mdl/ee79.png)</td>
  <td><span data-ttu-id="127e7-3904">EE79</span><span class="sxs-lookup"><span data-stu-id="127e7-3904">EE79</span></span></td>
  <td><span data-ttu-id="127e7-3905">ActionCenterQuiet</span><span class="sxs-lookup"><span data-stu-id="127e7-3905">ActionCenterQuiet</span></span></td>
 </tr>
 <tr><td>![ActionCenterQuietNotification](images/segoe-mdl/ee7a.png)</td>
  <td><span data-ttu-id="127e7-3907">EE7A</span><span class="sxs-lookup"><span data-stu-id="127e7-3907">EE7A</span></span></td>
  <td><span data-ttu-id="127e7-3908">ActionCenterQuietNotification</span><span class="sxs-lookup"><span data-stu-id="127e7-3908">ActionCenterQuietNotification</span></span></td>
 </tr>
 <tr><td>![TrackersMirrored](images/segoe-mdl/ee92.png)</td>
  <td><span data-ttu-id="127e7-3910">EE92</span><span class="sxs-lookup"><span data-stu-id="127e7-3910">EE92</span></span></td>
  <td><span data-ttu-id="127e7-3911">TrackersMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-3911">TrackersMirrored</span></span></td>
 </tr>
 <tr><td>![DateTimeMirrored](images/segoe-mdl/ee93.png)</td>
  <td><span data-ttu-id="127e7-3913">EE93</span><span class="sxs-lookup"><span data-stu-id="127e7-3913">EE93</span></span></td>
  <td><span data-ttu-id="127e7-3914">DateTimeMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-3914">DateTimeMirrored</span></span></td>
 </tr>
 <tr><td>![Wheel](images/segoe-mdl/ee94.png)</td>
  <td><span data-ttu-id="127e7-3916">EE94</span><span class="sxs-lookup"><span data-stu-id="127e7-3916">EE94</span></span></td>
  <td><span data-ttu-id="127e7-3917">Wheel</span><span class="sxs-lookup"><span data-stu-id="127e7-3917">Wheel</span></span></td>
 </tr>
 <tr><td>![PenWorkspaceMirrored](images/segoe-mdl/ef15.png)</td>
  <td><span data-ttu-id="127e7-3919">EF15</span><span class="sxs-lookup"><span data-stu-id="127e7-3919">EF15</span></span></td>
  <td><span data-ttu-id="127e7-3920">PenWorkspaceMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-3920">PenWorkspaceMirrored</span></span></td>
 </tr>
 <tr><td>![PenPaletteMirrored](images/segoe-mdl/ef16.png)</td>
  <td><span data-ttu-id="127e7-3922">EF16</span><span class="sxs-lookup"><span data-stu-id="127e7-3922">EF16</span></span></td>
  <td><span data-ttu-id="127e7-3923">PenPaletteMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-3923">PenPaletteMirrored</span></span></td>
 </tr>
 <tr><td>![StrokeEraseMirrored](images/segoe-mdl/ef17.png)</td>
  <td><span data-ttu-id="127e7-3925">EF17</span><span class="sxs-lookup"><span data-stu-id="127e7-3925">EF17</span></span></td>
  <td><span data-ttu-id="127e7-3926">StrokeEraseMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-3926">StrokeEraseMirrored</span></span></td>
 </tr>
 <tr><td>![PointEraseMirrored](images/segoe-mdl/ef18.png)</td>
  <td><span data-ttu-id="127e7-3928">EF18</span><span class="sxs-lookup"><span data-stu-id="127e7-3928">EF18</span></span></td>
  <td><span data-ttu-id="127e7-3929">PointEraseMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-3929">PointEraseMirrored</span></span></td>
 </tr>
 <tr><td>![ClearAllInkMirrored](images/segoe-mdl/ef19.png)</td>
  <td><span data-ttu-id="127e7-3931">EF19</span><span class="sxs-lookup"><span data-stu-id="127e7-3931">EF19</span></span></td>
  <td><span data-ttu-id="127e7-3932">ClearAllInkMirrored</span><span class="sxs-lookup"><span data-stu-id="127e7-3932">ClearAllInkMirrored</span></span></td>
 </tr>
 <tr><td>![BackgroundToggle](images/segoe-mdl/ef1f.png)</td>
  <td><span data-ttu-id="127e7-3934">EF1F</span><span class="sxs-lookup"><span data-stu-id="127e7-3934">EF1F</span></span></td>
  <td><span data-ttu-id="127e7-3935">BackgroundToggle</span><span class="sxs-lookup"><span data-stu-id="127e7-3935">BackgroundToggle</span></span></td>
 </tr>
 <tr><td>![Marquee](images/segoe-mdl/ef20.png)</td>
  <td><span data-ttu-id="127e7-3937">EF20</span><span class="sxs-lookup"><span data-stu-id="127e7-3937">EF20</span></span></td>
  <td><span data-ttu-id="127e7-3938">Marquee</span><span class="sxs-lookup"><span data-stu-id="127e7-3938">Marquee</span></span></td>
 </tr>
 
</table>



## <a name="related-articles"></a><span data-ttu-id="127e7-3939">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="127e7-3939">Related articles</span></span>

* [<span data-ttu-id="127e7-3940">Richtlinien für Schriftarten</span><span class="sxs-lookup"><span data-stu-id="127e7-3940">Guidelines for fonts</span></span>](fonts.md)
* [**<span data-ttu-id="127e7-3941">Symbol-Enumeration</span><span class="sxs-lookup"><span data-stu-id="127e7-3941">Symbol enumeration</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn252842)


 




