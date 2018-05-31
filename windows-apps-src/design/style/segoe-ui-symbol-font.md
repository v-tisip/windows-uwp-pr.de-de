---
author: mijacobs
Description: This article lists and provides usage guidance for the glyphs that come with the Segoe MDL2 Assets font.
Search.Refinement.TopicID: 184
title: Richtlinien für Segoe MDL2-Symbole
ms.assetid: DFB215C2-8A61-4957-B662-3B1991AC9BE1
label: Segoe MDL2 icons
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 3da419c3193a3aa4481033d8489643f2daf40eba
ms.sourcegitcommit: 91511d2d1dc8ab74b566aaeab3ef2139e7ed4945
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2018
ms.locfileid: "1817641"
---
# <a name="segoe-mdl2-icons"></a><span data-ttu-id="d3f5b-103">Segoe MDL2-Symbole</span><span class="sxs-lookup"><span data-stu-id="d3f5b-103">Segoe MDL2 icons</span></span>

 

<span data-ttu-id="d3f5b-104">In diesem Artikel werden die Symbole der Schriftart Segoe MDL2 Assets aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-104">This article lists the icons provided by the Segoe MDL2 Assets font.</span></span> 

> <span data-ttu-id="d3f5b-105">**Wichtige APIs**: [**Symbol-Enumeration**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.symbol), [**FontIcon-Klasse**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.fonticon)</span><span class="sxs-lookup"><span data-stu-id="d3f5b-105">**Important APIs**: [**Symbol enum**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.symbol), [**FontIcon class**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.fonticon)</span></span>

## <a name="about-segoe-mdl2-assets"></a><span data-ttu-id="d3f5b-106">Informationen zu MDL2 Assets</span><span class="sxs-lookup"><span data-stu-id="d3f5b-106">About Segoe MDL2 Assets</span></span>

<span data-ttu-id="d3f5b-107">Mit der Veröffentlichung von Windows10 wurde die Schriftart Segoe UI Symbol von Windows8/8.1 durch die Schriftart Segoe MDL2 Assets ersetzt.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-107">With the release of Windows 10, the Segoe MDL2 Assets font replaced the Windows 8/8.1 Segoe UI Symbol icon font.</span></span> <!-- It can be used in much the same manner as the older font, but many glyphs have been redrawn in the Windows 10 icon style with the font’s metrics set so that icons are aligned within the font’s em-square instead of on a typographic baseline. --> <span data-ttu-id="d3f5b-108">(**Segoe UI Symbol** ist jedoch weiterhin als „veraltete“ Ressource verfügbar. Es wird jedoch empfohlen, Apps auf die neue Schriftart **Segoe MDL2 Assets** zu aktualisieren.)</span><span class="sxs-lookup"><span data-stu-id="d3f5b-108">(**Segoe UI Symbol** will still be available as a "legacy" resource, but we recommend updating your app to use the new **Segoe MDL2 Assets**.)</span></span>

<span data-ttu-id="d3f5b-109">Die Mehrzahl der in der Schriftart **Segoe MDL2 Assets** enthaltenen Symbole und Benutzeroberflächen-Steuerelemente sind dem Unicode-Bereich „Private Use Area“ (PUA) zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-109">Most of the icons and UI controls included in the **Segoe MDL2 Assets** font are mapped to the Private Use Area of Unicode (PUA).</span></span> <span data-ttu-id="d3f5b-110">Mithilfe des PUA können Entwickler Glyphen, die keinen vorhandenen Codepunkten zugeordnet sind, private Unicode-Werte zuweisen.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-110">The PUA allows font developers to assign private Unicode values to glyphs that don’t map to existing code points.</span></span> <span data-ttu-id="d3f5b-111">Dies ist hilfreich bei der Erstellung einer Symbolschriftart, führt jedoch auch zu einem Interoperabilitätsproblem.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-111">This is useful when creating a symbol font, but it creates an interoperability problem.</span></span> <span data-ttu-id="d3f5b-112">Ist die Schriftart nicht verfügbar, werden die Glyphen nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-112">If the font is not available, the glyphs won’t show up.</span></span> <span data-ttu-id="d3f5b-113">Verwenden Sie die Glyphen nur, wenn Sie die Schriftart **Segoe MDL2 Assets** explizit angeben können.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-113">Only use these glyphs when you can specify the **Segoe MDL2 Assets** font.</span></span>

<span data-ttu-id="d3f5b-114">Verwenden Sie diese Glyphen nur, wenn Sie die Schriftart **Segoe MDL2 Assets** explizit angeben können.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-114">Use these glyphs only when you can explicitly specify the **Segoe MDL2 Assets** font.</span></span> <span data-ttu-id="d3f5b-115">Bei Verwendung von Kacheln können Sie diese Glyphen nicht nutzen, da Sie die Kachelschriftart nicht angeben können und PUA-Glyphen nicht per Schriftartfallback verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-115">If you are working with tiles, you can't use these glyphs because you can't specify the tile font and PUA glyphs are not available via font-fallback.</span></span>

<span data-ttu-id="d3f5b-116">Anders als bei **Segoe UI Symbol** sind die Symbole in der Schriftart **Segoe MDL2 Assets** nicht für die Inlineverwendung mit Text vorgesehen.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-116">Unlike with **Segoe UI Symbol**, the icons in the **Segoe MDL2 Assets** font are not intended for use in-line with text.</span></span> <span data-ttu-id="d3f5b-117">Demnach gelten einige ältere „Tricks“ wie die Pfeile für schrittweise Anzeige nicht mehr.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-117">This means that some older "tricks" like the progressive disclosure arrows no longer apply.</span></span> <span data-ttu-id="d3f5b-118">Da alle neuen Symbole gleichermaßen größentechnisch angepasst und positioniert werden, müssen sie entsprechend nicht mit einer Nullbreite erstellt werden. Wir haben hingegen sichergestellt, dass sie einfach als ein Satz funktionieren.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-118">Likewise, since all of the new icons are sized and positioned the same, they do not have to be made with zero width; we have just made sure they work as a set.</span></span> <span data-ttu-id="d3f5b-119">Im Idealfall können Sie zwei Symbole überlagern, die als ein Satz konzipiert wurden, und sie nehmen Gestalt an.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-119">Ideally, you can overlay two icons that were designed as a set and they will fall into place.</span></span> <span data-ttu-id="d3f5b-120">Wir können dies vornehmen, um die Farbgebung im Code zu erlauben.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-120">We may do this to allow colorization in the code.</span></span> <span data-ttu-id="d3f5b-121">Beispielsweise wurden U+EA3A und U+EA3B für den Badgestatus der Startkachel erstellt.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-121">For example, U+EA3A and U+EA3B were created for the Start tile Badge status.</span></span> <span data-ttu-id="d3f5b-122">Da diese bereits zentriert sind, kann die Kreisfüllung für unterschiedliche Status gefärbt werden.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-122">Because these are already centered the circle fill can be colored for different states.</span></span>

## <a name="layering-and-mirroring"></a><span data-ttu-id="d3f5b-123">Überlagern und Spiegeln</span><span class="sxs-lookup"><span data-stu-id="d3f5b-123">Layering and mirroring</span></span>

<span data-ttu-id="d3f5b-124">Alle Glyphen in **Segoe MDL2 Assets** haben dieselbe feste Breite mit einer konsistenten Höhe und einem linken Ursprungspunkt. So können Überlagerungs- und Farbgebungseffekte erzielt werden, indem Glyphen direkt übereinander gezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-124">All glyphs in **Segoe MDL2 Assets** have the same fixed width with a consistent height and left origin point, so layering and colorization effects can be achieved by drawing glyphs directly on top of each other.</span></span> <span data-ttu-id="d3f5b-125">Dieses Beispiel zeigt einen schwarzen Rand, der über das rote Herz mit einer Breite von Null gezeichnet wurde.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-125">This example show a black outline drawn on top of the zero-width red heart.</span></span>

![Verwenden von Glyphen mit der Breite 0](images/segoe-ui-symbol-layering.png)

<span data-ttu-id="d3f5b-127">Viele der Symbole verfügen zudem über gespiegelte Formen, die in Sprachen verwendet werden können, in denen die Rechts-nach-Links-Ausrichtung verwendet wird, beispielsweise Arabisch, Farsi und Hebräisch.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-127">Many of the icons also have mirrored forms available for use in languages that use right-to-left text directionality such as Arabic, Farsi, and Hebrew.</span></span>

## <a name="using-the-icons"></a><span data-ttu-id="d3f5b-128">Verwenden der Symbole</span><span class="sxs-lookup"><span data-stu-id="d3f5b-128">Using the icons</span></span>
<span data-ttu-id="d3f5b-129">Wenn Sie eine App in C#/VB/C++ und XAML entwickeln, können Sie mithilfe der [Symbolenumeration](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.symbol) bestimmte Glyphen der Schriftart Segoe MDL2 Assets verwenden.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-129">If you are developing an app in C#/VB/C++ and XAML, you can use specified glyphs from Seogoe MDL2 Assets with the [Symbol enumeration](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.symbol).</span></span> 

```xaml
<SymbolIcon Symbol="GlobalNavigationButton"/>
```

<span data-ttu-id="d3f5b-130">Wenn Sie ein Glyphen der Schriftart **Segoe MDL2 Assets** verwenden möchten, das nicht in der Symbolenumeration enthalten ist, verwenden Sie ein [**FontIcon**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.fonticon).</span><span class="sxs-lookup"><span data-stu-id="d3f5b-130">If you would like to use a glyph from the **Segoe MDL2 Assets** font that is not included in the Symbol enum, then use a [**FontIcon**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.fonticon).</span></span>

```xaml
<FontIcon FontFamily="Segoe MDL2 Assets" Glyph="&#xE700;"/>
```

## <a name="how-do-i-get-this-font"></a><span data-ttu-id="d3f5b-131">Wie erhalte ich diese Schriftart?</span><span class="sxs-lookup"><span data-stu-id="d3f5b-131">How do I get this font?</span></span>
<span data-ttu-id="d3f5b-132">Um Segoe MDL2 Assets zu erhalten, müssen Sie Windows10 installieren.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-132">To obtain Segoe MDL2 Assets, you must install Windows 10.</span></span> 

## <a name="icon-list"></a><span data-ttu-id="d3f5b-133">Liste der Symbole</span><span class="sxs-lookup"><span data-stu-id="d3f5b-133">Icon list</span></span>
<span data-ttu-id="d3f5b-134">Beachten Sie zudem, dass die Schriftart **Segoe MDL2-Ressourcen** viel mehr Symbole enthält, als hier gezeigt werden kann.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-134">Please keep in mind that the **Segoe MDL2 Assets** font includes many more icons than we can show here.</span></span> <span data-ttu-id="d3f5b-135">Viele der Symbole dienen speziellen Zwecken und werden für gewöhnlich nicht an anderer Stelle verwendet.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-135">Many of the icons are intended for specialized purposed and are not typically used anywhere else.</span></span>


<table style="background-color: white; color: black">

 <tr>
  <td><span data-ttu-id="d3f5b-136">Symbol</span><span class="sxs-lookup"><span data-stu-id="d3f5b-136">Symbol</span></span></td>
  <td><span data-ttu-id="d3f5b-137">Unicode-Punkt</span><span class="sxs-lookup"><span data-stu-id="d3f5b-137">Unicode point</span></span></td>
  <td><span data-ttu-id="d3f5b-138">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d3f5b-138">Description</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e700.png" alt="GlobalNavButton" /></td>
  <td><span data-ttu-id="d3f5b-139">E700</span><span class="sxs-lookup"><span data-stu-id="d3f5b-139">E700</span></span></td>
  <td><span data-ttu-id="d3f5b-140">GlobalNavigationButton</span><span class="sxs-lookup"><span data-stu-id="d3f5b-140">GlobalNavigationButton</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e701.png" alt="Wifi" /></td>
  <td><span data-ttu-id="d3f5b-141">E701</span><span class="sxs-lookup"><span data-stu-id="d3f5b-141">E701</span></span></td>
  <td><span data-ttu-id="d3f5b-142">WLAN</span><span class="sxs-lookup"><span data-stu-id="d3f5b-142">Wifi</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e702.png" alt="Bluetooth" /></td>
  <td><span data-ttu-id="d3f5b-143">E702</span><span class="sxs-lookup"><span data-stu-id="d3f5b-143">E702</span></span></td>
  <td><span data-ttu-id="d3f5b-144">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="d3f5b-144">Bluetooth</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e703.png" alt="Connect" /></td>
  <td><span data-ttu-id="d3f5b-145">E703</span><span class="sxs-lookup"><span data-stu-id="d3f5b-145">E703</span></span></td>
  <td><span data-ttu-id="d3f5b-146">Verbinden</span><span class="sxs-lookup"><span data-stu-id="d3f5b-146">Connect</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e704.png" alt="InternetSharing" /></td>
  <td><span data-ttu-id="d3f5b-147">E704</span><span class="sxs-lookup"><span data-stu-id="d3f5b-147">E704</span></span></td>
  <td><span data-ttu-id="d3f5b-148">InternetSharing</span><span class="sxs-lookup"><span data-stu-id="d3f5b-148">InternetSharing</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e705.png" alt="VPN" /></td>
  <td><span data-ttu-id="d3f5b-149">E705</span><span class="sxs-lookup"><span data-stu-id="d3f5b-149">E705</span></span></td>
  <td><span data-ttu-id="d3f5b-150">VPN</span><span class="sxs-lookup"><span data-stu-id="d3f5b-150">VPN</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e706.png" alt="Brightness" /></td>
  <td><span data-ttu-id="d3f5b-151">E706</span><span class="sxs-lookup"><span data-stu-id="d3f5b-151">E706</span></span></td>
  <td><span data-ttu-id="d3f5b-152">Helligkeit</span><span class="sxs-lookup"><span data-stu-id="d3f5b-152">Brightness</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e707.png" alt="MapPin" /></td>
  <td><span data-ttu-id="d3f5b-153">E707</span><span class="sxs-lookup"><span data-stu-id="d3f5b-153">E707</span></span></td>
  <td><span data-ttu-id="d3f5b-154">MapPin</span><span class="sxs-lookup"><span data-stu-id="d3f5b-154">MapPin</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e708.png" alt="QuietHours" /></td>
  <td><span data-ttu-id="d3f5b-155">E708</span><span class="sxs-lookup"><span data-stu-id="d3f5b-155">E708</span></span></td>
  <td><span data-ttu-id="d3f5b-156">QuietHours</span><span class="sxs-lookup"><span data-stu-id="d3f5b-156">QuietHours</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e709.png" alt="Airplane" /></td>
  <td><span data-ttu-id="d3f5b-157">E709</span><span class="sxs-lookup"><span data-stu-id="d3f5b-157">E709</span></span></td>
  <td><span data-ttu-id="d3f5b-158">Airplane</span><span class="sxs-lookup"><span data-stu-id="d3f5b-158">Airplane</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e70a.png" alt="Tablet" /></td>
  <td><span data-ttu-id="d3f5b-159">E70A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-159">E70A</span></span></td>
  <td><span data-ttu-id="d3f5b-160">Tablet</span><span class="sxs-lookup"><span data-stu-id="d3f5b-160">Tablet</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e70b.png" alt="QuickNote" /></td>
  <td><span data-ttu-id="d3f5b-161">E70B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-161">E70B</span></span></td>
  <td><span data-ttu-id="d3f5b-162">QuickNote</span><span class="sxs-lookup"><span data-stu-id="d3f5b-162">QuickNote</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e70c.png" alt="RememberedDevice" /></td>
  <td><span data-ttu-id="d3f5b-163">E70C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-163">E70C</span></span></td>
  <td><span data-ttu-id="d3f5b-164">RememberedDevice</span><span class="sxs-lookup"><span data-stu-id="d3f5b-164">RememberedDevice</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e70d.png" alt="ChevronDown" /></td>
  <td><span data-ttu-id="d3f5b-165">E70D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-165">E70D</span></span></td>
  <td><span data-ttu-id="d3f5b-166">ChevronDown</span><span class="sxs-lookup"><span data-stu-id="d3f5b-166">ChevronDown</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e70e.png" alt="ChevronUp" /></td>
  <td><span data-ttu-id="d3f5b-167">E70E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-167">E70E</span></span></td>
  <td><span data-ttu-id="d3f5b-168">ChevronUp</span><span class="sxs-lookup"><span data-stu-id="d3f5b-168">ChevronUp</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e70f.png" alt="Edit" /></td>
  <td><span data-ttu-id="d3f5b-169">E70F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-169">E70F</span></span></td>
  <td><span data-ttu-id="d3f5b-170">Bearbeiten</span><span class="sxs-lookup"><span data-stu-id="d3f5b-170">Edit</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e710.png" alt="Add" /></td>
  <td><span data-ttu-id="d3f5b-171">E710</span><span class="sxs-lookup"><span data-stu-id="d3f5b-171">E710</span></span></td>
  <td><span data-ttu-id="d3f5b-172">Add</span><span class="sxs-lookup"><span data-stu-id="d3f5b-172">Add</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e711.png" alt="Cancel" /></td>
  <td><span data-ttu-id="d3f5b-173">E711</span><span class="sxs-lookup"><span data-stu-id="d3f5b-173">E711</span></span></td>
  <td><span data-ttu-id="d3f5b-174">Abbrechen</span><span class="sxs-lookup"><span data-stu-id="d3f5b-174">Cancel</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e712.png" alt="More" /></td>
  <td><span data-ttu-id="d3f5b-175">E712</span><span class="sxs-lookup"><span data-stu-id="d3f5b-175">E712</span></span></td>
  <td><span data-ttu-id="d3f5b-176">More</span><span class="sxs-lookup"><span data-stu-id="d3f5b-176">More</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e713.png" alt="Settings" /></td>
  <td><span data-ttu-id="d3f5b-177">E713</span><span class="sxs-lookup"><span data-stu-id="d3f5b-177">E713</span></span></td>
  <td><span data-ttu-id="d3f5b-178">Einstellungen</span><span class="sxs-lookup"><span data-stu-id="d3f5b-178">Settings</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e714.png" alt="Video" /></td>
  <td><span data-ttu-id="d3f5b-179">E714</span><span class="sxs-lookup"><span data-stu-id="d3f5b-179">E714</span></span></td>
  <td><span data-ttu-id="d3f5b-180">Video</span><span class="sxs-lookup"><span data-stu-id="d3f5b-180">Video</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e715.png" alt="Mail" /></td>
  <td><span data-ttu-id="d3f5b-181">E715</span><span class="sxs-lookup"><span data-stu-id="d3f5b-181">E715</span></span></td>
  <td><span data-ttu-id="d3f5b-182">Mail</span><span class="sxs-lookup"><span data-stu-id="d3f5b-182">Mail</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e716.png" alt="People" /></td>
  <td><span data-ttu-id="d3f5b-183">E716</span><span class="sxs-lookup"><span data-stu-id="d3f5b-183">E716</span></span></td>
  <td><span data-ttu-id="d3f5b-184">Kontakte</span><span class="sxs-lookup"><span data-stu-id="d3f5b-184">People</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e717.png" alt="Phone" /></td>
  <td><span data-ttu-id="d3f5b-185">E717</span><span class="sxs-lookup"><span data-stu-id="d3f5b-185">E717</span></span></td>
  <td><span data-ttu-id="d3f5b-186">Telefone</span><span class="sxs-lookup"><span data-stu-id="d3f5b-186">Phone</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e718.png" alt="Pin" /></td>
  <td><span data-ttu-id="d3f5b-187">E718</span><span class="sxs-lookup"><span data-stu-id="d3f5b-187">E718</span></span></td>
  <td><span data-ttu-id="d3f5b-188">Pin</span><span class="sxs-lookup"><span data-stu-id="d3f5b-188">Pin</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e719.png" alt="Shop" /></td>
  <td><span data-ttu-id="d3f5b-189">E719</span><span class="sxs-lookup"><span data-stu-id="d3f5b-189">E719</span></span></td>
  <td><span data-ttu-id="d3f5b-190">Shop</span><span class="sxs-lookup"><span data-stu-id="d3f5b-190">Shop</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e71a.png" alt="Stop" /></td>
  <td><span data-ttu-id="d3f5b-191">E71A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-191">E71A</span></span></td>
  <td><span data-ttu-id="d3f5b-192">Stop</span><span class="sxs-lookup"><span data-stu-id="d3f5b-192">Stop</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e71b.png" alt="Link" /></td>
  <td><span data-ttu-id="d3f5b-193">E71B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-193">E71B</span></span></td>
  <td><span data-ttu-id="d3f5b-194">Link</span><span class="sxs-lookup"><span data-stu-id="d3f5b-194">Link</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e71c.png" alt="Filter" /></td>
  <td><span data-ttu-id="d3f5b-195">E71C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-195">E71C</span></span></td>
  <td><span data-ttu-id="d3f5b-196">Filter</span><span class="sxs-lookup"><span data-stu-id="d3f5b-196">Filter</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e71d.png" alt="AllApps" /></td>
  <td><span data-ttu-id="d3f5b-197">E71D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-197">E71D</span></span></td>
  <td><span data-ttu-id="d3f5b-198">AllApps</span><span class="sxs-lookup"><span data-stu-id="d3f5b-198">AllApps</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e71e.png" alt="Zoom" /></td>
  <td><span data-ttu-id="d3f5b-199">E71E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-199">E71E</span></span></td>
  <td><span data-ttu-id="d3f5b-200">Zoom</span><span class="sxs-lookup"><span data-stu-id="d3f5b-200">Zoom</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e71f.png" alt="ZoomOut" /></td>
  <td><span data-ttu-id="d3f5b-201">E71F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-201">E71F</span></span></td>
  <td><span data-ttu-id="d3f5b-202">ZoomOut</span><span class="sxs-lookup"><span data-stu-id="d3f5b-202">ZoomOut</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e720.png" alt="Microphone" /></td>
  <td><span data-ttu-id="d3f5b-203">E720</span><span class="sxs-lookup"><span data-stu-id="d3f5b-203">E720</span></span></td>
  <td><span data-ttu-id="d3f5b-204">Mikrofon</span><span class="sxs-lookup"><span data-stu-id="d3f5b-204">Microphone</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e721.png" alt="Search" /></td>
  <td><span data-ttu-id="d3f5b-205">E721</span><span class="sxs-lookup"><span data-stu-id="d3f5b-205">E721</span></span></td>
  <td><span data-ttu-id="d3f5b-206">Suche</span><span class="sxs-lookup"><span data-stu-id="d3f5b-206">Search</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e722.png" alt="Camera" /></td>
  <td><span data-ttu-id="d3f5b-207">E722</span><span class="sxs-lookup"><span data-stu-id="d3f5b-207">E722</span></span></td>
  <td><span data-ttu-id="d3f5b-208">Kamera</span><span class="sxs-lookup"><span data-stu-id="d3f5b-208">Camera</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e723.png" alt="Attach" /></td>
  <td><span data-ttu-id="d3f5b-209">E723</span><span class="sxs-lookup"><span data-stu-id="d3f5b-209">E723</span></span></td>
  <td><span data-ttu-id="d3f5b-210">Attach</span><span class="sxs-lookup"><span data-stu-id="d3f5b-210">Attach</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e724.png" alt="Send" /></td>
  <td><span data-ttu-id="d3f5b-211">E724</span><span class="sxs-lookup"><span data-stu-id="d3f5b-211">E724</span></span></td>
  <td><span data-ttu-id="d3f5b-212">Send</span><span class="sxs-lookup"><span data-stu-id="d3f5b-212">Send</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e725.png" alt="SendFill" /></td>
  <td><span data-ttu-id="d3f5b-213">E725</span><span class="sxs-lookup"><span data-stu-id="d3f5b-213">E725</span></span></td>
  <td><span data-ttu-id="d3f5b-214">SendFill</span><span class="sxs-lookup"><span data-stu-id="d3f5b-214">SendFill</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e726.png" alt="WalkSolid" /></td>
  <td><span data-ttu-id="d3f5b-215">E726</span><span class="sxs-lookup"><span data-stu-id="d3f5b-215">E726</span></span></td>
  <td><span data-ttu-id="d3f5b-216">WalkSolid</span><span class="sxs-lookup"><span data-stu-id="d3f5b-216">WalkSolid</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e727.png" alt="InPrivate" /></td>
  <td><span data-ttu-id="d3f5b-217">E727</span><span class="sxs-lookup"><span data-stu-id="d3f5b-217">E727</span></span></td>
  <td><span data-ttu-id="d3f5b-218">InPrivate</span><span class="sxs-lookup"><span data-stu-id="d3f5b-218">InPrivate</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e728.png" alt="FavoriteList" /></td>
  <td><span data-ttu-id="d3f5b-219">E728</span><span class="sxs-lookup"><span data-stu-id="d3f5b-219">E728</span></span></td>
  <td><span data-ttu-id="d3f5b-220">FavoriteList</span><span class="sxs-lookup"><span data-stu-id="d3f5b-220">FavoriteList</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e729.png" alt="PageSolid" /></td>
  <td><span data-ttu-id="d3f5b-221">E729</span><span class="sxs-lookup"><span data-stu-id="d3f5b-221">E729</span></span></td>
  <td><span data-ttu-id="d3f5b-222">PageSolid</span><span class="sxs-lookup"><span data-stu-id="d3f5b-222">PageSolid</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e72a.png" alt="Forward" /></td>
  <td><span data-ttu-id="d3f5b-223">E72A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-223">E72A</span></span></td>
  <td><span data-ttu-id="d3f5b-224">Vorwärts</span><span class="sxs-lookup"><span data-stu-id="d3f5b-224">Forward</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e72b.png" alt="Back" /></td>
  <td><span data-ttu-id="d3f5b-225">E72B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-225">E72B</span></span></td>
  <td><span data-ttu-id="d3f5b-226">Zurück</span><span class="sxs-lookup"><span data-stu-id="d3f5b-226">Back</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e72c.png" alt="Refresh" /></td>
  <td><span data-ttu-id="d3f5b-227">E72C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-227">E72C</span></span></td>
  <td><span data-ttu-id="d3f5b-228">Aktualisieren</span><span class="sxs-lookup"><span data-stu-id="d3f5b-228">Refresh</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e72d.png" alt="Share" /></td>
  <td><span data-ttu-id="d3f5b-229">E72D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-229">E72D</span></span></td>
  <td><span data-ttu-id="d3f5b-230">Freigabe</span><span class="sxs-lookup"><span data-stu-id="d3f5b-230">Share</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e72e.png" alt="Lock" /></td>
  <td><span data-ttu-id="d3f5b-231">E72E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-231">E72E</span></span></td>
  <td><span data-ttu-id="d3f5b-232">Lock</span><span class="sxs-lookup"><span data-stu-id="d3f5b-232">Lock</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e730.png" alt="ReportHacked" /></td>
  <td><span data-ttu-id="d3f5b-233">E730</span><span class="sxs-lookup"><span data-stu-id="d3f5b-233">E730</span></span></td>
  <td><span data-ttu-id="d3f5b-234">ReportHacked</span><span class="sxs-lookup"><span data-stu-id="d3f5b-234">ReportHacked</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e734.png" alt="FavoriteStar" /></td>
  <td><span data-ttu-id="d3f5b-235">E734</span><span class="sxs-lookup"><span data-stu-id="d3f5b-235">E734</span></span></td>
  <td><span data-ttu-id="d3f5b-236">FavoriteStar</span><span class="sxs-lookup"><span data-stu-id="d3f5b-236">FavoriteStar</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e735.png" alt="FavoriteStarFill" /></td>
  <td><span data-ttu-id="d3f5b-237">E735</span><span class="sxs-lookup"><span data-stu-id="d3f5b-237">E735</span></span></td>
  <td><span data-ttu-id="d3f5b-238">FavoriteStarFill</span><span class="sxs-lookup"><span data-stu-id="d3f5b-238">FavoriteStarFill</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e738.png" alt="Remove" /></td>
  <td><span data-ttu-id="d3f5b-239">E738</span><span class="sxs-lookup"><span data-stu-id="d3f5b-239">E738</span></span></td>
  <td><span data-ttu-id="d3f5b-240">Entfernen</span><span class="sxs-lookup"><span data-stu-id="d3f5b-240">Remove</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e739.png" alt="Checkbox" /></td>
  <td><span data-ttu-id="d3f5b-241">E739</span><span class="sxs-lookup"><span data-stu-id="d3f5b-241">E739</span></span></td>
  <td><span data-ttu-id="d3f5b-242">Kontrollkästchen</span><span class="sxs-lookup"><span data-stu-id="d3f5b-242">Checkbox</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e73a.png" alt="CheckboxComposite" /></td>
  <td><span data-ttu-id="d3f5b-243">E73A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-243">E73A</span></span></td>
  <td><span data-ttu-id="d3f5b-244">CheckboxComposite</span><span class="sxs-lookup"><span data-stu-id="d3f5b-244">CheckboxComposite</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e73b.png" alt="CheckboxFill" /></td>
  <td><span data-ttu-id="d3f5b-245">E73B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-245">E73B</span></span></td>
  <td><span data-ttu-id="d3f5b-246">CheckboxFill</span><span class="sxs-lookup"><span data-stu-id="d3f5b-246">CheckboxFill</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e73c.png" alt="CheckboxIndeterminate" /></td>
  <td><span data-ttu-id="d3f5b-247">E73C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-247">E73C</span></span></td>
  <td><span data-ttu-id="d3f5b-248">CheckboxIndeterminate</span><span class="sxs-lookup"><span data-stu-id="d3f5b-248">CheckboxIndeterminate</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e73d.png" alt="CheckboxCompositeReversed" /></td>
  <td><span data-ttu-id="d3f5b-249">E73D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-249">E73D</span></span></td>
  <td><span data-ttu-id="d3f5b-250">CheckboxCompositeReversed</span><span class="sxs-lookup"><span data-stu-id="d3f5b-250">CheckboxCompositeReversed</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e73e.png" alt="CheckMark" /></td>
  <td><span data-ttu-id="d3f5b-251">E73E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-251">E73E</span></span></td>
  <td><span data-ttu-id="d3f5b-252">CheckMark</span><span class="sxs-lookup"><span data-stu-id="d3f5b-252">CheckMark</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e73f.png" alt="BackToWindow" /></td>
  <td><span data-ttu-id="d3f5b-253">E73F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-253">E73F</span></span></td>
  <td><span data-ttu-id="d3f5b-254">BackToWindow</span><span class="sxs-lookup"><span data-stu-id="d3f5b-254">BackToWindow</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e740.png" alt="FullScreen" /></td>
  <td><span data-ttu-id="d3f5b-255">E740</span><span class="sxs-lookup"><span data-stu-id="d3f5b-255">E740</span></span></td>
  <td><span data-ttu-id="d3f5b-256">FullScreen</span><span class="sxs-lookup"><span data-stu-id="d3f5b-256">FullScreen</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e741.png" alt="ResizeTouchLarger" /></td>
  <td><span data-ttu-id="d3f5b-257">E741</span><span class="sxs-lookup"><span data-stu-id="d3f5b-257">E741</span></span></td>
  <td><span data-ttu-id="d3f5b-258">ResizeTouchLarger</span><span class="sxs-lookup"><span data-stu-id="d3f5b-258">ResizeTouchLarger</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e742.png" alt="ResizeTouchSmaller" /></td>
  <td><span data-ttu-id="d3f5b-259">E742</span><span class="sxs-lookup"><span data-stu-id="d3f5b-259">E742</span></span></td>
  <td><span data-ttu-id="d3f5b-260">ResizeTouchSmaller</span><span class="sxs-lookup"><span data-stu-id="d3f5b-260">ResizeTouchSmaller</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e743.png" alt="ResizeMouseSmall" /></td>
  <td><span data-ttu-id="d3f5b-261">E743</span><span class="sxs-lookup"><span data-stu-id="d3f5b-261">E743</span></span></td>
  <td><span data-ttu-id="d3f5b-262">ResizeMouseSmall</span><span class="sxs-lookup"><span data-stu-id="d3f5b-262">ResizeMouseSmall</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e744.png" alt="ResizeMouseMedium" /></td>
  <td><span data-ttu-id="d3f5b-263">E744</span><span class="sxs-lookup"><span data-stu-id="d3f5b-263">E744</span></span></td>
  <td><span data-ttu-id="d3f5b-264">ResizeMouseMedium</span><span class="sxs-lookup"><span data-stu-id="d3f5b-264">ResizeMouseMedium</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e745.png" alt="ResizeMouseWide" /></td>
  <td><span data-ttu-id="d3f5b-265">E745</span><span class="sxs-lookup"><span data-stu-id="d3f5b-265">E745</span></span></td>
  <td><span data-ttu-id="d3f5b-266">ResizeMouseWide</span><span class="sxs-lookup"><span data-stu-id="d3f5b-266">ResizeMouseWide</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e746.png" alt="ResizeMouseTall" /></td>
  <td><span data-ttu-id="d3f5b-267">E746</span><span class="sxs-lookup"><span data-stu-id="d3f5b-267">E746</span></span></td>
  <td><span data-ttu-id="d3f5b-268">ResizeMouseTall</span><span class="sxs-lookup"><span data-stu-id="d3f5b-268">ResizeMouseTall</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e747.png" alt="ResizeMouseLarge" /></td>
  <td><span data-ttu-id="d3f5b-269">E747</span><span class="sxs-lookup"><span data-stu-id="d3f5b-269">E747</span></span></td>
  <td><span data-ttu-id="d3f5b-270">ResizeMouseLarge</span><span class="sxs-lookup"><span data-stu-id="d3f5b-270">ResizeMouseLarge</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e748.png" alt="SwitchUser" /></td>
  <td><span data-ttu-id="d3f5b-271">E748</span><span class="sxs-lookup"><span data-stu-id="d3f5b-271">E748</span></span></td>
  <td><span data-ttu-id="d3f5b-272">SwitchUser</span><span class="sxs-lookup"><span data-stu-id="d3f5b-272">SwitchUser</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e749.png" alt="Print" /></td>
  <td><span data-ttu-id="d3f5b-273">E749</span><span class="sxs-lookup"><span data-stu-id="d3f5b-273">E749</span></span></td>
  <td><span data-ttu-id="d3f5b-274">Drucken</span><span class="sxs-lookup"><span data-stu-id="d3f5b-274">Print</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e74a.png" alt="Up" /></td>
  <td><span data-ttu-id="d3f5b-275">E74A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-275">E74A</span></span></td>
  <td><span data-ttu-id="d3f5b-276">Oben</span><span class="sxs-lookup"><span data-stu-id="d3f5b-276">Up</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e74b.png" alt="Down" /></td>
  <td><span data-ttu-id="d3f5b-277">E74B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-277">E74B</span></span></td>
  <td><span data-ttu-id="d3f5b-278">Unten</span><span class="sxs-lookup"><span data-stu-id="d3f5b-278">Down</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e74c.png" alt="OEM" /></td>
  <td><span data-ttu-id="d3f5b-279">E74C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-279">E74C</span></span></td>
  <td><span data-ttu-id="d3f5b-280">OEM</span><span class="sxs-lookup"><span data-stu-id="d3f5b-280">OEM</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e74d.png" alt="Delete" /></td>
  <td><span data-ttu-id="d3f5b-281">E74D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-281">E74D</span></span></td>
  <td><span data-ttu-id="d3f5b-282">Delete</span><span class="sxs-lookup"><span data-stu-id="d3f5b-282">Delete</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e74e.png" alt="Save" /></td>
  <td><span data-ttu-id="d3f5b-283">E74E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-283">E74E</span></span></td>
  <td><span data-ttu-id="d3f5b-284">Speichern</span><span class="sxs-lookup"><span data-stu-id="d3f5b-284">Save</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e74f.png" alt="Mute" /></td>
  <td><span data-ttu-id="d3f5b-285">E74F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-285">E74F</span></span></td>
  <td><span data-ttu-id="d3f5b-286">Stummschalten</span><span class="sxs-lookup"><span data-stu-id="d3f5b-286">Mute</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e750.png" alt="BackSpaceQWERTY" /></td>
  <td><span data-ttu-id="d3f5b-287">E750</span><span class="sxs-lookup"><span data-stu-id="d3f5b-287">E750</span></span></td>
  <td><span data-ttu-id="d3f5b-288">BackSpaceQWERTY</span><span class="sxs-lookup"><span data-stu-id="d3f5b-288">BackSpaceQWERTY</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e751.png" alt="ReturnKey" /></td>
  <td><span data-ttu-id="d3f5b-289">E751</span><span class="sxs-lookup"><span data-stu-id="d3f5b-289">E751</span></span></td>
  <td><span data-ttu-id="d3f5b-290">ReturnKey</span><span class="sxs-lookup"><span data-stu-id="d3f5b-290">ReturnKey</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e752.png" alt="UpArrowShiftKey" /></td>
  <td><span data-ttu-id="d3f5b-291">E752</span><span class="sxs-lookup"><span data-stu-id="d3f5b-291">E752</span></span></td>
  <td><span data-ttu-id="d3f5b-292">UpArrowShiftKey</span><span class="sxs-lookup"><span data-stu-id="d3f5b-292">UpArrowShiftKey</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e753.png" alt="Cloud" /></td>
  <td><span data-ttu-id="d3f5b-293">E753</span><span class="sxs-lookup"><span data-stu-id="d3f5b-293">E753</span></span></td>
  <td><span data-ttu-id="d3f5b-294">Cloud</span><span class="sxs-lookup"><span data-stu-id="d3f5b-294">Cloud</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e754.png" alt="Flashlight" /></td>
  <td><span data-ttu-id="d3f5b-295">E754</span><span class="sxs-lookup"><span data-stu-id="d3f5b-295">E754</span></span></td>
  <td><span data-ttu-id="d3f5b-296">Flashlight</span><span class="sxs-lookup"><span data-stu-id="d3f5b-296">Flashlight</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e755.png" alt="RotationLock" /></td>
  <td><span data-ttu-id="d3f5b-297">E755</span><span class="sxs-lookup"><span data-stu-id="d3f5b-297">E755</span></span></td>
  <td><span data-ttu-id="d3f5b-298">RotationLock</span><span class="sxs-lookup"><span data-stu-id="d3f5b-298">RotationLock</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e756.png" alt="CommandPrompt" /></td>
  <td><span data-ttu-id="d3f5b-299">E756</span><span class="sxs-lookup"><span data-stu-id="d3f5b-299">E756</span></span></td>
  <td><span data-ttu-id="d3f5b-300">CommandPrompt</span><span class="sxs-lookup"><span data-stu-id="d3f5b-300">CommandPrompt</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e759.png" alt="SIPMove" /></td>
  <td><span data-ttu-id="d3f5b-301">E759</span><span class="sxs-lookup"><span data-stu-id="d3f5b-301">E759</span></span></td>
  <td><span data-ttu-id="d3f5b-302">SIPMove</span><span class="sxs-lookup"><span data-stu-id="d3f5b-302">SIPMove</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e75a.png" alt="SIPUndock" /></td>
  <td><span data-ttu-id="d3f5b-303">E75A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-303">E75A</span></span></td>
  <td><span data-ttu-id="d3f5b-304">SIPUndock</span><span class="sxs-lookup"><span data-stu-id="d3f5b-304">SIPUndock</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e75b.png" alt="SIPRedock" /></td>
  <td><span data-ttu-id="d3f5b-305">E75B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-305">E75B</span></span></td>
  <td><span data-ttu-id="d3f5b-306">SIPRedock</span><span class="sxs-lookup"><span data-stu-id="d3f5b-306">SIPRedock</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e75c.png" alt="EraseTool" /></td>
  <td><span data-ttu-id="d3f5b-307">E75C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-307">E75C</span></span></td>
  <td><span data-ttu-id="d3f5b-308">EraseTool</span><span class="sxs-lookup"><span data-stu-id="d3f5b-308">EraseTool</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e75d.png" alt="UnderscoreSpace" /></td>
  <td><span data-ttu-id="d3f5b-309">E75D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-309">E75D</span></span></td>
  <td><span data-ttu-id="d3f5b-310">UnderscoreSpace</span><span class="sxs-lookup"><span data-stu-id="d3f5b-310">UnderscoreSpace</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e75e.png" alt="GripperTool" /></td>
  <td><span data-ttu-id="d3f5b-311">E75E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-311">E75E</span></span></td>
  <td><span data-ttu-id="d3f5b-312">GripperTool</span><span class="sxs-lookup"><span data-stu-id="d3f5b-312">GripperTool</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e75f.png" alt="Dialpad" /></td>
  <td><span data-ttu-id="d3f5b-313">E75F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-313">E75F</span></span></td>
  <td><span data-ttu-id="d3f5b-314">Dialpad</span><span class="sxs-lookup"><span data-stu-id="d3f5b-314">Dialpad</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e760.png" alt="PageLeft" /></td>
  <td><span data-ttu-id="d3f5b-315">E760</span><span class="sxs-lookup"><span data-stu-id="d3f5b-315">E760</span></span></td>
  <td><span data-ttu-id="d3f5b-316">PageLeft</span><span class="sxs-lookup"><span data-stu-id="d3f5b-316">PageLeft</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e761.png" alt="PageRight" /></td>
  <td><span data-ttu-id="d3f5b-317">E761</span><span class="sxs-lookup"><span data-stu-id="d3f5b-317">E761</span></span></td>
  <td><span data-ttu-id="d3f5b-318">PageRight</span><span class="sxs-lookup"><span data-stu-id="d3f5b-318">PageRight</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e762.png" alt="MultiSelect" /></td>
  <td><span data-ttu-id="d3f5b-319">E762</span><span class="sxs-lookup"><span data-stu-id="d3f5b-319">E762</span></span></td>
  <td><span data-ttu-id="d3f5b-320">MultiSelect</span><span class="sxs-lookup"><span data-stu-id="d3f5b-320">MultiSelect</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e763.png" alt="KeyboardLeftHanded" /></td>
  <td><span data-ttu-id="d3f5b-321">E763</span><span class="sxs-lookup"><span data-stu-id="d3f5b-321">E763</span></span></td>
  <td><span data-ttu-id="d3f5b-322">KeyboardLeftHanded</span><span class="sxs-lookup"><span data-stu-id="d3f5b-322">KeyboardLeftHanded</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e764.png" alt="KeyboardRightHanded" /></td>
  <td><span data-ttu-id="d3f5b-323">E764</span><span class="sxs-lookup"><span data-stu-id="d3f5b-323">E764</span></span></td>
  <td><span data-ttu-id="d3f5b-324">KeyboardRightHanded</span><span class="sxs-lookup"><span data-stu-id="d3f5b-324">KeyboardRightHanded</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e765.png" alt="KeyboardClassic" /></td>
  <td><span data-ttu-id="d3f5b-325">E765</span><span class="sxs-lookup"><span data-stu-id="d3f5b-325">E765</span></span></td>
  <td><span data-ttu-id="d3f5b-326">KeyboardClassic</span><span class="sxs-lookup"><span data-stu-id="d3f5b-326">KeyboardClassic</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e766.png" alt="KeyboardSplit" /></td>
  <td><span data-ttu-id="d3f5b-327">E766</span><span class="sxs-lookup"><span data-stu-id="d3f5b-327">E766</span></span></td>
  <td><span data-ttu-id="d3f5b-328">KeyboardSplit</span><span class="sxs-lookup"><span data-stu-id="d3f5b-328">KeyboardSplit</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e767.png" alt="Volume" /></td>
  <td><span data-ttu-id="d3f5b-329">E767</span><span class="sxs-lookup"><span data-stu-id="d3f5b-329">E767</span></span></td>
  <td><span data-ttu-id="d3f5b-330">Volume</span><span class="sxs-lookup"><span data-stu-id="d3f5b-330">Volume</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e768.png" alt="Play" /></td>
  <td><span data-ttu-id="d3f5b-331">E768</span><span class="sxs-lookup"><span data-stu-id="d3f5b-331">E768</span></span></td>
  <td><span data-ttu-id="d3f5b-332">Wiedergeben</span><span class="sxs-lookup"><span data-stu-id="d3f5b-332">Play</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e769.png" alt="Pause" /></td>
  <td><span data-ttu-id="d3f5b-333">E769</span><span class="sxs-lookup"><span data-stu-id="d3f5b-333">E769</span></span></td>
  <td><span data-ttu-id="d3f5b-334">Anhalten</span><span class="sxs-lookup"><span data-stu-id="d3f5b-334">Pause</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e76b.png" alt="ChevronLeft" /></td>
  <td><span data-ttu-id="d3f5b-335">E76B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-335">E76B</span></span></td>
  <td><span data-ttu-id="d3f5b-336">ChevronLeft</span><span class="sxs-lookup"><span data-stu-id="d3f5b-336">ChevronLeft</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e76c.png" alt="ChevronRight" /></td>
  <td><span data-ttu-id="d3f5b-337">E76C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-337">E76C</span></span></td>
  <td><span data-ttu-id="d3f5b-338">ChevronRight</span><span class="sxs-lookup"><span data-stu-id="d3f5b-338">ChevronRight</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e76d.png" alt="InkingTool" /></td>
  <td><span data-ttu-id="d3f5b-339">E76D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-339">E76D</span></span></td>
  <td><span data-ttu-id="d3f5b-340">InkingTool</span><span class="sxs-lookup"><span data-stu-id="d3f5b-340">InkingTool</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e76e.png" alt="Emoji2" /></td>
  <td><span data-ttu-id="d3f5b-341">E76E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-341">E76E</span></span></td>
  <td><span data-ttu-id="d3f5b-342">Emoji2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-342">Emoji2</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e76f.png" alt="GripperBarHorizontal" /></td>
  <td><span data-ttu-id="d3f5b-343">E76F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-343">E76F</span></span></td>
  <td><span data-ttu-id="d3f5b-344">GripperBarHorizontal</span><span class="sxs-lookup"><span data-stu-id="d3f5b-344">GripperBarHorizontal</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e770.png" alt="System" /></td>
  <td><span data-ttu-id="d3f5b-345">E770</span><span class="sxs-lookup"><span data-stu-id="d3f5b-345">E770</span></span></td>
  <td><span data-ttu-id="d3f5b-346">System</span><span class="sxs-lookup"><span data-stu-id="d3f5b-346">System</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e771.png" alt="Personalize" /></td>
  <td><span data-ttu-id="d3f5b-347">E771</span><span class="sxs-lookup"><span data-stu-id="d3f5b-347">E771</span></span></td>
  <td><span data-ttu-id="d3f5b-348">Personalisieren</span><span class="sxs-lookup"><span data-stu-id="d3f5b-348">Personalize</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e772.png" alt="Devices" /></td>
  <td><span data-ttu-id="d3f5b-349">E772</span><span class="sxs-lookup"><span data-stu-id="d3f5b-349">E772</span></span></td>
  <td><span data-ttu-id="d3f5b-350">Geräte</span><span class="sxs-lookup"><span data-stu-id="d3f5b-350">Devices</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e773.png" alt="SearchAndApps" /></td>
  <td><span data-ttu-id="d3f5b-351">E773</span><span class="sxs-lookup"><span data-stu-id="d3f5b-351">E773</span></span></td>
  <td><span data-ttu-id="d3f5b-352">SearchAndApps</span><span class="sxs-lookup"><span data-stu-id="d3f5b-352">SearchAndApps</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e774.png" alt="Globe" /></td>
  <td><span data-ttu-id="d3f5b-353">E774</span><span class="sxs-lookup"><span data-stu-id="d3f5b-353">E774</span></span></td>
  <td><span data-ttu-id="d3f5b-354">Globe</span><span class="sxs-lookup"><span data-stu-id="d3f5b-354">Globe</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e775.png" alt="TimeLanguage" /></td>
  <td><span data-ttu-id="d3f5b-355">E775</span><span class="sxs-lookup"><span data-stu-id="d3f5b-355">E775</span></span></td>
  <td><span data-ttu-id="d3f5b-356">TimeLanguage</span><span class="sxs-lookup"><span data-stu-id="d3f5b-356">TimeLanguage</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e776.png" alt="EaseOfAccess" /></td>
  <td><span data-ttu-id="d3f5b-357">E776</span><span class="sxs-lookup"><span data-stu-id="d3f5b-357">E776</span></span></td>
  <td><span data-ttu-id="d3f5b-358">EaseOfAccess</span><span class="sxs-lookup"><span data-stu-id="d3f5b-358">EaseOfAccess</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e777.png" alt="UpdateRestore" /></td>
  <td><span data-ttu-id="d3f5b-359">E777</span><span class="sxs-lookup"><span data-stu-id="d3f5b-359">E777</span></span></td>
  <td><span data-ttu-id="d3f5b-360">UpdateRestore</span><span class="sxs-lookup"><span data-stu-id="d3f5b-360">UpdateRestore</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e778.png" alt="HangUp" /></td>
  <td><span data-ttu-id="d3f5b-361">E778</span><span class="sxs-lookup"><span data-stu-id="d3f5b-361">E778</span></span></td>
  <td><span data-ttu-id="d3f5b-362">HangUp</span><span class="sxs-lookup"><span data-stu-id="d3f5b-362">HangUp</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e779.png" alt="ContactInfo" /></td>
  <td><span data-ttu-id="d3f5b-363">E779</span><span class="sxs-lookup"><span data-stu-id="d3f5b-363">E779</span></span></td>
  <td><span data-ttu-id="d3f5b-364">ContactInfo</span><span class="sxs-lookup"><span data-stu-id="d3f5b-364">ContactInfo</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e77a.png" alt="Unpin" /></td>
  <td><span data-ttu-id="d3f5b-365">E77A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-365">E77A</span></span></td>
  <td><span data-ttu-id="d3f5b-366">Loslösen</span><span class="sxs-lookup"><span data-stu-id="d3f5b-366">Unpin</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e77b.png" alt="Contact" /></td>
  <td><span data-ttu-id="d3f5b-367">E77B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-367">E77B</span></span></td>
  <td><span data-ttu-id="d3f5b-368">Contact</span><span class="sxs-lookup"><span data-stu-id="d3f5b-368">Contact</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e77c.png" alt="Memo" /></td>
  <td><span data-ttu-id="d3f5b-369">E77C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-369">E77C</span></span></td>
  <td><span data-ttu-id="d3f5b-370">Memo</span><span class="sxs-lookup"><span data-stu-id="d3f5b-370">Memo</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e77f.png" alt="Paste" /></td>
  <td><span data-ttu-id="d3f5b-371">E77F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-371">E77F</span></span></td>
  <td><span data-ttu-id="d3f5b-372">Einfügen</span><span class="sxs-lookup"><span data-stu-id="d3f5b-372">Paste</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e780.png" alt="PhoneBook" /></td>
  <td><span data-ttu-id="d3f5b-373">E780</span><span class="sxs-lookup"><span data-stu-id="d3f5b-373">E780</span></span></td>
  <td><span data-ttu-id="d3f5b-374">PhoneBook</span><span class="sxs-lookup"><span data-stu-id="d3f5b-374">PhoneBook</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e781.png" alt="LEDLight" /></td>
  <td><span data-ttu-id="d3f5b-375">E781</span><span class="sxs-lookup"><span data-stu-id="d3f5b-375">E781</span></span></td>
  <td><span data-ttu-id="d3f5b-376">LEDLight</span><span class="sxs-lookup"><span data-stu-id="d3f5b-376">LEDLight</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e783.png" alt="Error" /></td>
  <td><span data-ttu-id="d3f5b-377">E783</span><span class="sxs-lookup"><span data-stu-id="d3f5b-377">E783</span></span></td>
  <td><span data-ttu-id="d3f5b-378">Fehler</span><span class="sxs-lookup"><span data-stu-id="d3f5b-378">Error</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e784.png" alt="GripperBarVertical" /></td>
  <td><span data-ttu-id="d3f5b-379">E784</span><span class="sxs-lookup"><span data-stu-id="d3f5b-379">E784</span></span></td>
  <td><span data-ttu-id="d3f5b-380">GripperBarVertical</span><span class="sxs-lookup"><span data-stu-id="d3f5b-380">GripperBarVertical</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e785.png" alt="Unlock" /></td>
  <td><span data-ttu-id="d3f5b-381">E785</span><span class="sxs-lookup"><span data-stu-id="d3f5b-381">E785</span></span></td>
  <td><span data-ttu-id="d3f5b-382">Entsperren</span><span class="sxs-lookup"><span data-stu-id="d3f5b-382">Unlock</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e786.png" alt="Slideshow" /></td>
  <td><span data-ttu-id="d3f5b-383">E786</span><span class="sxs-lookup"><span data-stu-id="d3f5b-383">E786</span></span></td>
  <td><span data-ttu-id="d3f5b-384">Slideshow</span><span class="sxs-lookup"><span data-stu-id="d3f5b-384">Slideshow</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e787.png" alt="Calendar" /></td>
  <td><span data-ttu-id="d3f5b-385">E787</span><span class="sxs-lookup"><span data-stu-id="d3f5b-385">E787</span></span></td>
  <td><span data-ttu-id="d3f5b-386">Kalender</span><span class="sxs-lookup"><span data-stu-id="d3f5b-386">Calendar</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e788.png" alt="GripperResize" /></td>
  <td><span data-ttu-id="d3f5b-387">E788</span><span class="sxs-lookup"><span data-stu-id="d3f5b-387">E788</span></span></td>
  <td><span data-ttu-id="d3f5b-388">GripperResize</span><span class="sxs-lookup"><span data-stu-id="d3f5b-388">GripperResize</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e789.png" alt="Megaphone" /></td>
  <td><span data-ttu-id="d3f5b-389">E789</span><span class="sxs-lookup"><span data-stu-id="d3f5b-389">E789</span></span></td>
  <td><span data-ttu-id="d3f5b-390">Megaphone</span><span class="sxs-lookup"><span data-stu-id="d3f5b-390">Megaphone</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e78a.png" alt="Trim" /></td>
  <td><span data-ttu-id="d3f5b-391">E78A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-391">E78A</span></span></td>
  <td><span data-ttu-id="d3f5b-392">Trim</span><span class="sxs-lookup"><span data-stu-id="d3f5b-392">Trim</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e78b.png" alt="NewWindow" /></td>
  <td><span data-ttu-id="d3f5b-393">E78B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-393">E78B</span></span></td>
  <td><span data-ttu-id="d3f5b-394">NewWindow</span><span class="sxs-lookup"><span data-stu-id="d3f5b-394">NewWindow</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e78c.png" alt="SaveLocal" /></td>
  <td><span data-ttu-id="d3f5b-395">E78C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-395">E78C</span></span></td>
  <td><span data-ttu-id="d3f5b-396">SaveLocal</span><span class="sxs-lookup"><span data-stu-id="d3f5b-396">SaveLocal</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e790.png" alt="Color" /></td>
  <td><span data-ttu-id="d3f5b-397">E790</span><span class="sxs-lookup"><span data-stu-id="d3f5b-397">E790</span></span></td>
  <td><span data-ttu-id="d3f5b-398">Farben</span><span class="sxs-lookup"><span data-stu-id="d3f5b-398">Color</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e791.png" alt="DataSense" /></td>
  <td><span data-ttu-id="d3f5b-399">E791</span><span class="sxs-lookup"><span data-stu-id="d3f5b-399">E791</span></span></td>
  <td><span data-ttu-id="d3f5b-400">DataSense</span><span class="sxs-lookup"><span data-stu-id="d3f5b-400">DataSense</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e792.png" alt="SaveAs" /></td>
  <td><span data-ttu-id="d3f5b-401">E792</span><span class="sxs-lookup"><span data-stu-id="d3f5b-401">E792</span></span></td>
  <td><span data-ttu-id="d3f5b-402">SaveAs</span><span class="sxs-lookup"><span data-stu-id="d3f5b-402">SaveAs</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e793.png" alt="Light" /></td>
  <td><span data-ttu-id="d3f5b-403">E793</span><span class="sxs-lookup"><span data-stu-id="d3f5b-403">E793</span></span></td>
  <td><span data-ttu-id="d3f5b-404">Licht</span><span class="sxs-lookup"><span data-stu-id="d3f5b-404">Light</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e799.png" alt="AspectRatio" /></td>
  <td><span data-ttu-id="d3f5b-405">E799</span><span class="sxs-lookup"><span data-stu-id="d3f5b-405">E799</span></span></td>
  <td><span data-ttu-id="d3f5b-406">AspectRatio</span><span class="sxs-lookup"><span data-stu-id="d3f5b-406">AspectRatio</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7a5.png" alt="DataSenseBar" /></td>
  <td><span data-ttu-id="d3f5b-407">E7A5</span><span class="sxs-lookup"><span data-stu-id="d3f5b-407">E7A5</span></span></td>
  <td><span data-ttu-id="d3f5b-408">DataSenseBar</span><span class="sxs-lookup"><span data-stu-id="d3f5b-408">DataSenseBar</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7a6.png" alt="Redo" /></td>
  <td><span data-ttu-id="d3f5b-409">E7A6</span><span class="sxs-lookup"><span data-stu-id="d3f5b-409">E7A6</span></span></td>
  <td><span data-ttu-id="d3f5b-410">Wiederholen</span><span class="sxs-lookup"><span data-stu-id="d3f5b-410">Redo</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7a7.png" alt="Undo" /></td>
  <td><span data-ttu-id="d3f5b-411">E7A7</span><span class="sxs-lookup"><span data-stu-id="d3f5b-411">E7A7</span></span></td>
  <td><span data-ttu-id="d3f5b-412">Rückgängig machen</span><span class="sxs-lookup"><span data-stu-id="d3f5b-412">Undo</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7a8.png" alt="Crop" /></td>
  <td><span data-ttu-id="d3f5b-413">E7A8</span><span class="sxs-lookup"><span data-stu-id="d3f5b-413">E7A8</span></span></td>
  <td><span data-ttu-id="d3f5b-414">Crop</span><span class="sxs-lookup"><span data-stu-id="d3f5b-414">Crop</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7ac.png" alt="OpenWith" /></td>
  <td><span data-ttu-id="d3f5b-415">E7AC</span><span class="sxs-lookup"><span data-stu-id="d3f5b-415">E7AC</span></span></td>
  <td><span data-ttu-id="d3f5b-416">OpenWith</span><span class="sxs-lookup"><span data-stu-id="d3f5b-416">OpenWith</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7ad.png" alt="Rotate" /></td>
  <td><span data-ttu-id="d3f5b-417">E7AD</span><span class="sxs-lookup"><span data-stu-id="d3f5b-417">E7AD</span></span></td>
  <td><span data-ttu-id="d3f5b-418">Drehen</span><span class="sxs-lookup"><span data-stu-id="d3f5b-418">Rotate</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7b5.png" alt="SetlockScreen" /></td>
  <td><span data-ttu-id="d3f5b-419">E7B5</span><span class="sxs-lookup"><span data-stu-id="d3f5b-419">E7B5</span></span></td>
  <td><span data-ttu-id="d3f5b-420">SetLockScreen</span><span class="sxs-lookup"><span data-stu-id="d3f5b-420">SetlockScreen</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7b7.png" alt="MapPin2" /></td>
  <td><span data-ttu-id="d3f5b-421">E7B7</span><span class="sxs-lookup"><span data-stu-id="d3f5b-421">E7B7</span></span></td>
  <td><span data-ttu-id="d3f5b-422">MapPin2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-422">MapPin2</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7b8.png" alt="Package" /></td>
  <td><span data-ttu-id="d3f5b-423">E7B8</span><span class="sxs-lookup"><span data-stu-id="d3f5b-423">E7B8</span></span></td>
  <td><span data-ttu-id="d3f5b-424">Paket</span><span class="sxs-lookup"><span data-stu-id="d3f5b-424">Package</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7ba.png" alt="Warning" /></td>
  <td><span data-ttu-id="d3f5b-425">E7BA</span><span class="sxs-lookup"><span data-stu-id="d3f5b-425">E7BA</span></span></td>
  <td><span data-ttu-id="d3f5b-426">Warnung</span><span class="sxs-lookup"><span data-stu-id="d3f5b-426">Warning</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7bc.png" alt="ReadingList" /></td>
  <td><span data-ttu-id="d3f5b-427">E7BC</span><span class="sxs-lookup"><span data-stu-id="d3f5b-427">E7BC</span></span></td>
  <td><span data-ttu-id="d3f5b-428">ReadingList</span><span class="sxs-lookup"><span data-stu-id="d3f5b-428">ReadingList</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7be.png" alt="Education" /></td>
  <td><span data-ttu-id="d3f5b-429">E7BE</span><span class="sxs-lookup"><span data-stu-id="d3f5b-429">E7BE</span></span></td>
  <td><span data-ttu-id="d3f5b-430">Bildung</span><span class="sxs-lookup"><span data-stu-id="d3f5b-430">Education</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7bf.png" alt="ShoppingCart" /></td>
  <td><span data-ttu-id="d3f5b-431">E7BF</span><span class="sxs-lookup"><span data-stu-id="d3f5b-431">E7BF</span></span></td>
  <td><span data-ttu-id="d3f5b-432">ShoppingCart</span><span class="sxs-lookup"><span data-stu-id="d3f5b-432">ShoppingCart</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7c0.png" alt="Train" /></td>
  <td><span data-ttu-id="d3f5b-433">E7C0</span><span class="sxs-lookup"><span data-stu-id="d3f5b-433">E7C0</span></span></td>
  <td><span data-ttu-id="d3f5b-434">Train</span><span class="sxs-lookup"><span data-stu-id="d3f5b-434">Train</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7c1.png" alt="Flag" /></td>
  <td><span data-ttu-id="d3f5b-435">E7C1</span><span class="sxs-lookup"><span data-stu-id="d3f5b-435">E7C1</span></span></td>
  <td><span data-ttu-id="d3f5b-436">Flag</span><span class="sxs-lookup"><span data-stu-id="d3f5b-436">Flag</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7c3.png" alt="Page" /></td>
  <td><span data-ttu-id="d3f5b-437">E7C3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-437">E7C3</span></span></td>
  <td><span data-ttu-id="d3f5b-438">Seite</span><span class="sxs-lookup"><span data-stu-id="d3f5b-438">Page</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7c4.png" alt="Multitask" /></td>
  <td><span data-ttu-id="d3f5b-439">E7C4</span><span class="sxs-lookup"><span data-stu-id="d3f5b-439">E7C4</span></span></td>
  <td><span data-ttu-id="d3f5b-440">Multitask</span><span class="sxs-lookup"><span data-stu-id="d3f5b-440">Multitask</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7c5.png" alt="BrowsePhotos" /></td>
  <td><span data-ttu-id="d3f5b-441">E7C5</span><span class="sxs-lookup"><span data-stu-id="d3f5b-441">E7C5</span></span></td>
  <td><span data-ttu-id="d3f5b-442">BrowsePhotos</span><span class="sxs-lookup"><span data-stu-id="d3f5b-442">BrowsePhotos</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7c6.png" alt="HalfStarLeft" /></td>
  <td><span data-ttu-id="d3f5b-443">E7C6</span><span class="sxs-lookup"><span data-stu-id="d3f5b-443">E7C6</span></span></td>
  <td><span data-ttu-id="d3f5b-444">HalfStarLeft</span><span class="sxs-lookup"><span data-stu-id="d3f5b-444">HalfStarLeft</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7c7.png" alt="HalfStarRight" /></td>
  <td><span data-ttu-id="d3f5b-445">E7C7</span><span class="sxs-lookup"><span data-stu-id="d3f5b-445">E7C7</span></span></td>
  <td><span data-ttu-id="d3f5b-446">HalfStarRight</span><span class="sxs-lookup"><span data-stu-id="d3f5b-446">HalfStarRight</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7c8.png" alt="Record" /></td>
  <td><span data-ttu-id="d3f5b-447">E7C8</span><span class="sxs-lookup"><span data-stu-id="d3f5b-447">E7C8</span></span></td>
  <td><span data-ttu-id="d3f5b-448">Record</span><span class="sxs-lookup"><span data-stu-id="d3f5b-448">Record</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7c9.png" alt="TouchPointer" /></td>
  <td><span data-ttu-id="d3f5b-449">E7C9</span><span class="sxs-lookup"><span data-stu-id="d3f5b-449">E7C9</span></span></td>
  <td><span data-ttu-id="d3f5b-450">TouchPointer</span><span class="sxs-lookup"><span data-stu-id="d3f5b-450">TouchPointer</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7de.png" alt="LangJPN" /></td>
  <td><span data-ttu-id="d3f5b-451">E7DE</span><span class="sxs-lookup"><span data-stu-id="d3f5b-451">E7DE</span></span></td>
  <td><span data-ttu-id="d3f5b-452">LangJPN</span><span class="sxs-lookup"><span data-stu-id="d3f5b-452">LangJPN</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7e3.png" alt="Ferry" /></td>
  <td><span data-ttu-id="d3f5b-453">E7E3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-453">E7E3</span></span></td>
  <td><span data-ttu-id="d3f5b-454">Ferry</span><span class="sxs-lookup"><span data-stu-id="d3f5b-454">Ferry</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7e6.png" alt="Highlight" /></td>
  <td><span data-ttu-id="d3f5b-455">E7E6</span><span class="sxs-lookup"><span data-stu-id="d3f5b-455">E7E6</span></span></td>
  <td><span data-ttu-id="d3f5b-456">Hervorheben</span><span class="sxs-lookup"><span data-stu-id="d3f5b-456">Highlight</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7e7.png" alt="ActionCenterNotification" /></td>
  <td><span data-ttu-id="d3f5b-457">E7E7</span><span class="sxs-lookup"><span data-stu-id="d3f5b-457">E7E7</span></span></td>
  <td><span data-ttu-id="d3f5b-458">ActionCenterNotification</span><span class="sxs-lookup"><span data-stu-id="d3f5b-458">ActionCenterNotification</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7e8.png" alt="PowerButton" /></td>
  <td><span data-ttu-id="d3f5b-459">E7E8</span><span class="sxs-lookup"><span data-stu-id="d3f5b-459">E7E8</span></span></td>
  <td><span data-ttu-id="d3f5b-460">PowerButton</span><span class="sxs-lookup"><span data-stu-id="d3f5b-460">PowerButton</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7ea.png" alt="ResizeTouchNarrower" /></td>
  <td><span data-ttu-id="d3f5b-461">E7EA</span><span class="sxs-lookup"><span data-stu-id="d3f5b-461">E7EA</span></span></td>
  <td><span data-ttu-id="d3f5b-462">ResizeTouchNarrower</span><span class="sxs-lookup"><span data-stu-id="d3f5b-462">ResizeTouchNarrower</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7eb.png" alt="ResizeTouchShorter" /></td>
  <td><span data-ttu-id="d3f5b-463">E7EB</span><span class="sxs-lookup"><span data-stu-id="d3f5b-463">E7EB</span></span></td>
  <td><span data-ttu-id="d3f5b-464">ResizeTouchShorter</span><span class="sxs-lookup"><span data-stu-id="d3f5b-464">ResizeTouchShorter</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7ec.png" alt="DrivingMode" /></td>
  <td><span data-ttu-id="d3f5b-465">E7EC</span><span class="sxs-lookup"><span data-stu-id="d3f5b-465">E7EC</span></span></td>
  <td><span data-ttu-id="d3f5b-466">DrivingMode</span><span class="sxs-lookup"><span data-stu-id="d3f5b-466">DrivingMode</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7ed.png" alt="RingerSilent" /></td>
  <td><span data-ttu-id="d3f5b-467">E7ED</span><span class="sxs-lookup"><span data-stu-id="d3f5b-467">E7ED</span></span></td>
  <td><span data-ttu-id="d3f5b-468">RingerSilent</span><span class="sxs-lookup"><span data-stu-id="d3f5b-468">RingerSilent</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7ee.png" alt="OtherUser" /></td>
  <td><span data-ttu-id="d3f5b-469">E7EE</span><span class="sxs-lookup"><span data-stu-id="d3f5b-469">E7EE</span></span></td>
  <td><span data-ttu-id="d3f5b-470">OtherUser</span><span class="sxs-lookup"><span data-stu-id="d3f5b-470">OtherUser</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7ef.png" alt="Admin" /></td>
  <td><span data-ttu-id="d3f5b-471">E7EF</span><span class="sxs-lookup"><span data-stu-id="d3f5b-471">E7EF</span></span></td>
  <td><span data-ttu-id="d3f5b-472">Administrator</span><span class="sxs-lookup"><span data-stu-id="d3f5b-472">Admin</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7f0.png" alt="CC" /></td>
  <td><span data-ttu-id="d3f5b-473">E7F0</span><span class="sxs-lookup"><span data-stu-id="d3f5b-473">E7F0</span></span></td>
  <td><span data-ttu-id="d3f5b-474">CC</span><span class="sxs-lookup"><span data-stu-id="d3f5b-474">CC</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7f1.png" alt="SDCard" /></td>
  <td><span data-ttu-id="d3f5b-475">E7F1</span><span class="sxs-lookup"><span data-stu-id="d3f5b-475">E7F1</span></span></td>
  <td><span data-ttu-id="d3f5b-476">SDCard</span><span class="sxs-lookup"><span data-stu-id="d3f5b-476">SDCard</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7f2.png" alt="CallForwarding" /></td>
  <td><span data-ttu-id="d3f5b-477">E7F2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-477">E7F2</span></span></td>
  <td><span data-ttu-id="d3f5b-478">CallForwarding</span><span class="sxs-lookup"><span data-stu-id="d3f5b-478">CallForwarding</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7f3.png" alt="SettingsDisplaySound" /></td>
  <td><span data-ttu-id="d3f5b-479">E7F3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-479">E7F3</span></span></td>
  <td><span data-ttu-id="d3f5b-480">SettingsDisplaySound</span><span class="sxs-lookup"><span data-stu-id="d3f5b-480">SettingsDisplaySound</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7f4.png" alt="TVMonitor" /></td>
  <td><span data-ttu-id="d3f5b-481">E7F4</span><span class="sxs-lookup"><span data-stu-id="d3f5b-481">E7F4</span></span></td>
  <td><span data-ttu-id="d3f5b-482">TVMonitor</span><span class="sxs-lookup"><span data-stu-id="d3f5b-482">TVMonitor</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7f5.png" alt="Speakers" /></td>
  <td><span data-ttu-id="d3f5b-483">E7F5</span><span class="sxs-lookup"><span data-stu-id="d3f5b-483">E7F5</span></span></td>
  <td><span data-ttu-id="d3f5b-484">Lautsprecher</span><span class="sxs-lookup"><span data-stu-id="d3f5b-484">Speakers</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7f6.png" alt="Headphone" /></td>
  <td><span data-ttu-id="d3f5b-485">E7F6</span><span class="sxs-lookup"><span data-stu-id="d3f5b-485">E7F6</span></span></td>
  <td><span data-ttu-id="d3f5b-486">Headphone</span><span class="sxs-lookup"><span data-stu-id="d3f5b-486">Headphone</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7f7.png" alt="DeviceLaptopPic" /></td>
  <td><span data-ttu-id="d3f5b-487">E7F7</span><span class="sxs-lookup"><span data-stu-id="d3f5b-487">E7F7</span></span></td>
  <td><span data-ttu-id="d3f5b-488">DeviceLaptopPic</span><span class="sxs-lookup"><span data-stu-id="d3f5b-488">DeviceLaptopPic</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7f8.png" alt="DeviceLaptopNoPic" /></td>
  <td><span data-ttu-id="d3f5b-489">E7F8</span><span class="sxs-lookup"><span data-stu-id="d3f5b-489">E7F8</span></span></td>
  <td><span data-ttu-id="d3f5b-490">DeviceLaptopNoPic</span><span class="sxs-lookup"><span data-stu-id="d3f5b-490">DeviceLaptopNoPic</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7f9.png" alt="DeviceMonitorRightPic" /></td>
  <td><span data-ttu-id="d3f5b-491">E7F9</span><span class="sxs-lookup"><span data-stu-id="d3f5b-491">E7F9</span></span></td>
  <td><span data-ttu-id="d3f5b-492">DeviceMonitorRightPic</span><span class="sxs-lookup"><span data-stu-id="d3f5b-492">DeviceMonitorRightPic</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7fa.png" alt="DeviceMonitorLeftPic" /></td>
  <td><span data-ttu-id="d3f5b-493">E7FA</span><span class="sxs-lookup"><span data-stu-id="d3f5b-493">E7FA</span></span></td>
  <td><span data-ttu-id="d3f5b-494">DeviceMonitorLeftPic</span><span class="sxs-lookup"><span data-stu-id="d3f5b-494">DeviceMonitorLeftPic</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7fb.png" alt="DeviceMonitorNoPic" /></td>
  <td><span data-ttu-id="d3f5b-495">E7FB</span><span class="sxs-lookup"><span data-stu-id="d3f5b-495">E7FB</span></span></td>
  <td><span data-ttu-id="d3f5b-496">DeviceMonitorNoPic</span><span class="sxs-lookup"><span data-stu-id="d3f5b-496">DeviceMonitorNoPic</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7fc.png" alt="Game" /></td>
  <td><span data-ttu-id="d3f5b-497">E7FC</span><span class="sxs-lookup"><span data-stu-id="d3f5b-497">E7FC</span></span></td>
  <td><span data-ttu-id="d3f5b-498">Game</span><span class="sxs-lookup"><span data-stu-id="d3f5b-498">Game</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e7fd.png" alt="HorizontalTabKey" /></td>
  <td><span data-ttu-id="d3f5b-499">E7FD</span><span class="sxs-lookup"><span data-stu-id="d3f5b-499">E7FD</span></span></td>
  <td><span data-ttu-id="d3f5b-500">HorizontalTabKey</span><span class="sxs-lookup"><span data-stu-id="d3f5b-500">HorizontalTabKey</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e802.png" alt="StreetsideSplitMinimize" /></td>
  <td><span data-ttu-id="d3f5b-501">E802</span><span class="sxs-lookup"><span data-stu-id="d3f5b-501">E802</span></span></td>
  <td><span data-ttu-id="d3f5b-502">StreetsideSplitMinimize</span><span class="sxs-lookup"><span data-stu-id="d3f5b-502">StreetsideSplitMinimize</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e803.png" alt="StreetsideSplitExpand" /></td>
  <td><span data-ttu-id="d3f5b-503">E803</span><span class="sxs-lookup"><span data-stu-id="d3f5b-503">E803</span></span></td>
  <td><span data-ttu-id="d3f5b-504">StreetsideSplitExpand</span><span class="sxs-lookup"><span data-stu-id="d3f5b-504">StreetsideSplitExpand</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e804.png" alt="Car" /></td>
  <td><span data-ttu-id="d3f5b-505">E804</span><span class="sxs-lookup"><span data-stu-id="d3f5b-505">E804</span></span></td>
  <td><span data-ttu-id="d3f5b-506">Car</span><span class="sxs-lookup"><span data-stu-id="d3f5b-506">Car</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e805.png" alt="Walk" /></td>
  <td><span data-ttu-id="d3f5b-507">E805</span><span class="sxs-lookup"><span data-stu-id="d3f5b-507">E805</span></span></td>
  <td><span data-ttu-id="d3f5b-508">Walk</span><span class="sxs-lookup"><span data-stu-id="d3f5b-508">Walk</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e806.png" alt="Bus" /></td>
  <td><span data-ttu-id="d3f5b-509">E806</span><span class="sxs-lookup"><span data-stu-id="d3f5b-509">E806</span></span></td>
  <td><span data-ttu-id="d3f5b-510">Bus</span><span class="sxs-lookup"><span data-stu-id="d3f5b-510">Bus</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e809.png" alt="TiltUp" /></td>
  <td><span data-ttu-id="d3f5b-511">E809</span><span class="sxs-lookup"><span data-stu-id="d3f5b-511">E809</span></span></td>
  <td><span data-ttu-id="d3f5b-512">TiltUp</span><span class="sxs-lookup"><span data-stu-id="d3f5b-512">TiltUp</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e80a.png" alt="TiltDown" /></td>
  <td><span data-ttu-id="d3f5b-513">E80A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-513">E80A</span></span></td>
  <td><span data-ttu-id="d3f5b-514">TiltDown</span><span class="sxs-lookup"><span data-stu-id="d3f5b-514">TiltDown</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e80c.png" alt="RotateMapRight" /></td>
  <td><span data-ttu-id="d3f5b-515">E80C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-515">E80C</span></span></td>
  <td><span data-ttu-id="d3f5b-516">RotateMapRight</span><span class="sxs-lookup"><span data-stu-id="d3f5b-516">RotateMapRight</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e80d.png" alt="RotateMapLeft" /></td>
  <td><span data-ttu-id="d3f5b-517">E80D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-517">E80D</span></span></td>
  <td><span data-ttu-id="d3f5b-518">RotateMapLeft</span><span class="sxs-lookup"><span data-stu-id="d3f5b-518">RotateMapLeft</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e80f.png" alt="Home" /></td>
  <td><span data-ttu-id="d3f5b-519">E80F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-519">E80F</span></span></td>
  <td><span data-ttu-id="d3f5b-520">Startseite</span><span class="sxs-lookup"><span data-stu-id="d3f5b-520">Home</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e811.png" alt="ParkingLocation" /></td>
  <td><span data-ttu-id="d3f5b-521">E811</span><span class="sxs-lookup"><span data-stu-id="d3f5b-521">E811</span></span></td>
  <td><span data-ttu-id="d3f5b-522">ParkingLocation</span><span class="sxs-lookup"><span data-stu-id="d3f5b-522">ParkingLocation</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e812.png" alt="MapCompassTop" /></td>
  <td><span data-ttu-id="d3f5b-523">E812</span><span class="sxs-lookup"><span data-stu-id="d3f5b-523">E812</span></span></td>
  <td><span data-ttu-id="d3f5b-524">MapCompassTop</span><span class="sxs-lookup"><span data-stu-id="d3f5b-524">MapCompassTop</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e813.png" alt="MapCompassBottom" /></td>
  <td><span data-ttu-id="d3f5b-525">E813</span><span class="sxs-lookup"><span data-stu-id="d3f5b-525">E813</span></span></td>
  <td><span data-ttu-id="d3f5b-526">MapCompassBottom</span><span class="sxs-lookup"><span data-stu-id="d3f5b-526">MapCompassBottom</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e814.png" alt="IncidentTriangle" /></td>
  <td><span data-ttu-id="d3f5b-527">E814</span><span class="sxs-lookup"><span data-stu-id="d3f5b-527">E814</span></span></td>
  <td><span data-ttu-id="d3f5b-528">IncidentTriangle</span><span class="sxs-lookup"><span data-stu-id="d3f5b-528">IncidentTriangle</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e815.png" alt="Touch" /></td>
  <td><span data-ttu-id="d3f5b-529">E815</span><span class="sxs-lookup"><span data-stu-id="d3f5b-529">E815</span></span></td>
  <td><span data-ttu-id="d3f5b-530">Toucheingabe</span><span class="sxs-lookup"><span data-stu-id="d3f5b-530">Touch</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e816.png" alt="MapDirections" /></td>
  <td><span data-ttu-id="d3f5b-531">E816</span><span class="sxs-lookup"><span data-stu-id="d3f5b-531">E816</span></span></td>
  <td><span data-ttu-id="d3f5b-532">MapDirections</span><span class="sxs-lookup"><span data-stu-id="d3f5b-532">MapDirections</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e819.png" alt="StartPoint" /></td>
  <td><span data-ttu-id="d3f5b-533">E819</span><span class="sxs-lookup"><span data-stu-id="d3f5b-533">E819</span></span></td>
  <td><span data-ttu-id="d3f5b-534">StartPoint</span><span class="sxs-lookup"><span data-stu-id="d3f5b-534">StartPoint</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e81a.png" alt="StopPoint" /></td>
  <td><span data-ttu-id="d3f5b-535">E81A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-535">E81A</span></span></td>
  <td><span data-ttu-id="d3f5b-536">StopPoint</span><span class="sxs-lookup"><span data-stu-id="d3f5b-536">StopPoint</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e81b.png" alt="EndPoint" /></td>
  <td><span data-ttu-id="d3f5b-537">E81B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-537">E81B</span></span></td>
  <td><span data-ttu-id="d3f5b-538">EndPoint</span><span class="sxs-lookup"><span data-stu-id="d3f5b-538">EndPoint</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e81c.png" alt="History" /></td>
  <td><span data-ttu-id="d3f5b-539">E81C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-539">E81C</span></span></td>
  <td><span data-ttu-id="d3f5b-540">Verlauf</span><span class="sxs-lookup"><span data-stu-id="d3f5b-540">History</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e81d.png" alt="Location" /></td>
  <td><span data-ttu-id="d3f5b-541">E81D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-541">E81D</span></span></td>
  <td><span data-ttu-id="d3f5b-542">Speicherort</span><span class="sxs-lookup"><span data-stu-id="d3f5b-542">Location</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e81e.png" alt="MapLayers" /></td>
  <td><span data-ttu-id="d3f5b-543">E81E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-543">E81E</span></span></td>
  <td><span data-ttu-id="d3f5b-544">MapLayers</span><span class="sxs-lookup"><span data-stu-id="d3f5b-544">MapLayers</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e81f.png" alt="Accident" /></td>
  <td><span data-ttu-id="d3f5b-545">E81F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-545">E81F</span></span></td>
  <td><span data-ttu-id="d3f5b-546">Accident</span><span class="sxs-lookup"><span data-stu-id="d3f5b-546">Accident</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e821.png" alt="Work" /></td>
  <td><span data-ttu-id="d3f5b-547">E821</span><span class="sxs-lookup"><span data-stu-id="d3f5b-547">E821</span></span></td>
  <td><span data-ttu-id="d3f5b-548">Aufgabe</span><span class="sxs-lookup"><span data-stu-id="d3f5b-548">Work</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e822.png" alt="Construction" /></td>
  <td><span data-ttu-id="d3f5b-549">E822</span><span class="sxs-lookup"><span data-stu-id="d3f5b-549">E822</span></span></td>
  <td><span data-ttu-id="d3f5b-550">Construction</span><span class="sxs-lookup"><span data-stu-id="d3f5b-550">Construction</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e823.png" alt="Recent" /></td>
  <td><span data-ttu-id="d3f5b-551">E823</span><span class="sxs-lookup"><span data-stu-id="d3f5b-551">E823</span></span></td>
  <td><span data-ttu-id="d3f5b-552">Zuletzt verwendet</span><span class="sxs-lookup"><span data-stu-id="d3f5b-552">Recent</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e825.png" alt="Bank" /></td>
  <td><span data-ttu-id="d3f5b-553">E825</span><span class="sxs-lookup"><span data-stu-id="d3f5b-553">E825</span></span></td>
  <td><span data-ttu-id="d3f5b-554">Bank</span><span class="sxs-lookup"><span data-stu-id="d3f5b-554">Bank</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e826.png" alt="DownloadMap" /></td>
  <td><span data-ttu-id="d3f5b-555">E826</span><span class="sxs-lookup"><span data-stu-id="d3f5b-555">E826</span></span></td>
  <td><span data-ttu-id="d3f5b-556">DownloadMap</span><span class="sxs-lookup"><span data-stu-id="d3f5b-556">DownloadMap</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e829.png" alt="InkingToolFill2" /></td>
  <td><span data-ttu-id="d3f5b-557">E829</span><span class="sxs-lookup"><span data-stu-id="d3f5b-557">E829</span></span></td>
  <td><span data-ttu-id="d3f5b-558">InkingToolFill2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-558">InkingToolFill2</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e82a.png" alt="HighlightFill2" /></td>
  <td><span data-ttu-id="d3f5b-559">E82A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-559">E82A</span></span></td>
  <td><span data-ttu-id="d3f5b-560">HighlightFill2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-560">HighlightFill2</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e82b.png" alt="EraseToolFill" /></td>
  <td><span data-ttu-id="d3f5b-561">E82B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-561">E82B</span></span></td>
  <td><span data-ttu-id="d3f5b-562">EraseToolFill</span><span class="sxs-lookup"><span data-stu-id="d3f5b-562">EraseToolFill</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e82c.png" alt="EraseToolFill2" /></td>
  <td><span data-ttu-id="d3f5b-563">E82C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-563">E82C</span></span></td>
  <td><span data-ttu-id="d3f5b-564">EraseToolFill2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-564">EraseToolFill2</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e82d.png" alt="Dictionary" /></td>
  <td><span data-ttu-id="d3f5b-565">E82D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-565">E82D</span></span></td>
  <td><span data-ttu-id="d3f5b-566">Dictionary</span><span class="sxs-lookup"><span data-stu-id="d3f5b-566">Dictionary</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e82e.png" alt="DictionaryAdd" /></td>
  <td><span data-ttu-id="d3f5b-567">E82E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-567">E82E</span></span></td>
  <td><span data-ttu-id="d3f5b-568">DictionaryAdd</span><span class="sxs-lookup"><span data-stu-id="d3f5b-568">DictionaryAdd</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e82f.png" alt="ToolTip" /></td>
  <td><span data-ttu-id="d3f5b-569">E82F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-569">E82F</span></span></td>
  <td><span data-ttu-id="d3f5b-570">ToolTip</span><span class="sxs-lookup"><span data-stu-id="d3f5b-570">ToolTip</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e830.png" alt="ChromeBack" /></td>
  <td><span data-ttu-id="d3f5b-571">E830</span><span class="sxs-lookup"><span data-stu-id="d3f5b-571">E830</span></span></td>
  <td><span data-ttu-id="d3f5b-572">ChromeBack</span><span class="sxs-lookup"><span data-stu-id="d3f5b-572">ChromeBack</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e835.png" alt="ProvisioningPackage" /></td>
  <td><span data-ttu-id="d3f5b-573">E835</span><span class="sxs-lookup"><span data-stu-id="d3f5b-573">E835</span></span></td>
  <td><span data-ttu-id="d3f5b-574">ProvisioningPackage</span><span class="sxs-lookup"><span data-stu-id="d3f5b-574">ProvisioningPackage</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e836.png" alt="AddRemoteDevice" /></td>
  <td><span data-ttu-id="d3f5b-575">E836</span><span class="sxs-lookup"><span data-stu-id="d3f5b-575">E836</span></span></td>
  <td><span data-ttu-id="d3f5b-576">AddRemoteDevice</span><span class="sxs-lookup"><span data-stu-id="d3f5b-576">AddRemoteDevice</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e839.png" alt="Ethernet" /></td>
  <td><span data-ttu-id="d3f5b-577">E839</span><span class="sxs-lookup"><span data-stu-id="d3f5b-577">E839</span></span></td>
  <td><span data-ttu-id="d3f5b-578">Ethernet</span><span class="sxs-lookup"><span data-stu-id="d3f5b-578">Ethernet</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e83a.png" alt="&nbsp;ShareBroadband" /></td>
  <td><span data-ttu-id="d3f5b-579">E83A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-579">E83A</span></span></td>
  <td><span data-ttu-id="d3f5b-580">&nbsp;ShareBroadband</span><span class="sxs-lookup"><span data-stu-id="d3f5b-580">&nbsp;ShareBroadband</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e83b.png" alt="DirectAccess" /></td>
  <td><span data-ttu-id="d3f5b-581">E83B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-581">E83B</span></span></td>
  <td><span data-ttu-id="d3f5b-582">DirectAccess</span><span class="sxs-lookup"><span data-stu-id="d3f5b-582">DirectAccess</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e83c.png" alt="&nbsp;DialUp" /></td>
  <td><span data-ttu-id="d3f5b-583">E83C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-583">E83C</span></span></td>
  <td><span data-ttu-id="d3f5b-584">&nbsp;DialUp</span><span class="sxs-lookup"><span data-stu-id="d3f5b-584">&nbsp;DialUp</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e83d.png" alt="DefenderApp" /></td>
  <td><span data-ttu-id="d3f5b-585">E83D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-585">E83D</span></span></td>
  <td><span data-ttu-id="d3f5b-586">DefenderApp</span><span class="sxs-lookup"><span data-stu-id="d3f5b-586">DefenderApp</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e83e.png" alt="BatteryCharging9" /></td>
  <td><span data-ttu-id="d3f5b-587">E83E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-587">E83E</span></span></td>
  <td><span data-ttu-id="d3f5b-588">BatteryCharging9</span><span class="sxs-lookup"><span data-stu-id="d3f5b-588">BatteryCharging9</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e83f.png" alt="Battery10" /></td>
  <td><span data-ttu-id="d3f5b-589">E83F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-589">E83F</span></span></td>
  <td><span data-ttu-id="d3f5b-590">Battery10</span><span class="sxs-lookup"><span data-stu-id="d3f5b-590">Battery10</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e840.png" alt="Pinned" /></td>
  <td><span data-ttu-id="d3f5b-591">E840</span><span class="sxs-lookup"><span data-stu-id="d3f5b-591">E840</span></span></td>
  <td><span data-ttu-id="d3f5b-592">Pinned</span><span class="sxs-lookup"><span data-stu-id="d3f5b-592">Pinned</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e841.png" alt="PinFill" /></td>
  <td><span data-ttu-id="d3f5b-593">E841</span><span class="sxs-lookup"><span data-stu-id="d3f5b-593">E841</span></span></td>
  <td><span data-ttu-id="d3f5b-594">PinFill</span><span class="sxs-lookup"><span data-stu-id="d3f5b-594">PinFill</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e842.png" alt="PinnedFill" /></td>
  <td><span data-ttu-id="d3f5b-595">E842</span><span class="sxs-lookup"><span data-stu-id="d3f5b-595">E842</span></span></td>
  <td><span data-ttu-id="d3f5b-596">PinnedFill</span><span class="sxs-lookup"><span data-stu-id="d3f5b-596">PinnedFill</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e843.png" alt="PeriodKey" /></td>
  <td><span data-ttu-id="d3f5b-597">E843</span><span class="sxs-lookup"><span data-stu-id="d3f5b-597">E843</span></span></td>
  <td><span data-ttu-id="d3f5b-598">PeriodKey</span><span class="sxs-lookup"><span data-stu-id="d3f5b-598">PeriodKey</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e844.png" alt="PuncKey" /></td>
  <td><span data-ttu-id="d3f5b-599">E844</span><span class="sxs-lookup"><span data-stu-id="d3f5b-599">E844</span></span></td>
  <td><span data-ttu-id="d3f5b-600">PuncKey</span><span class="sxs-lookup"><span data-stu-id="d3f5b-600">PuncKey</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e845.png" alt="RevToggleKey" /></td>
  <td><span data-ttu-id="d3f5b-601">E845</span><span class="sxs-lookup"><span data-stu-id="d3f5b-601">E845</span></span></td>
  <td><span data-ttu-id="d3f5b-602">RevToggleKey</span><span class="sxs-lookup"><span data-stu-id="d3f5b-602">RevToggleKey</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e846.png" alt="RightArrowKeyTime1" /></td>
  <td><span data-ttu-id="d3f5b-603">E846</span><span class="sxs-lookup"><span data-stu-id="d3f5b-603">E846</span></span></td>
  <td><span data-ttu-id="d3f5b-604">RightArrowKeyTime1</span><span class="sxs-lookup"><span data-stu-id="d3f5b-604">RightArrowKeyTime1</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e847.png" alt="RightArrowKeyTime2" /></td>
  <td><span data-ttu-id="d3f5b-605">E847</span><span class="sxs-lookup"><span data-stu-id="d3f5b-605">E847</span></span></td>
  <td><span data-ttu-id="d3f5b-606">RightArrowKeyTime2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-606">RightArrowKeyTime2</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e848.png" alt="LeftQuote" /></td>
  <td><span data-ttu-id="d3f5b-607">E848</span><span class="sxs-lookup"><span data-stu-id="d3f5b-607">E848</span></span></td>
  <td><span data-ttu-id="d3f5b-608">LeftQuote</span><span class="sxs-lookup"><span data-stu-id="d3f5b-608">LeftQuote</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e849.png" alt="RightQuote" /></td>
  <td><span data-ttu-id="d3f5b-609">E849</span><span class="sxs-lookup"><span data-stu-id="d3f5b-609">E849</span></span></td>
  <td><span data-ttu-id="d3f5b-610">RightQuote</span><span class="sxs-lookup"><span data-stu-id="d3f5b-610">RightQuote</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e84a.png" alt="DownShiftKey" /></td>
  <td><span data-ttu-id="d3f5b-611">E84A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-611">E84A</span></span></td>
  <td><span data-ttu-id="d3f5b-612">DownShiftKey</span><span class="sxs-lookup"><span data-stu-id="d3f5b-612">DownShiftKey</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e84b.png" alt="UpShiftKey" /></td>
  <td><span data-ttu-id="d3f5b-613">E84B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-613">E84B</span></span></td>
  <td><span data-ttu-id="d3f5b-614">UpShiftKey</span><span class="sxs-lookup"><span data-stu-id="d3f5b-614">UpShiftKey</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e84c.png" alt="PuncKey0" /></td>
  <td><span data-ttu-id="d3f5b-615">E84C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-615">E84C</span></span></td>
  <td><span data-ttu-id="d3f5b-616">PuncKey0</span><span class="sxs-lookup"><span data-stu-id="d3f5b-616">PuncKey0</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e84d.png" alt="PuncKeyLeftBottom" /></td>
  <td><span data-ttu-id="d3f5b-617">E84D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-617">E84D</span></span></td>
  <td><span data-ttu-id="d3f5b-618">PuncKeyLeftBottom</span><span class="sxs-lookup"><span data-stu-id="d3f5b-618">PuncKeyLeftBottom</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e84e.png" alt="RightArrowKeyTime3" /></td>
  <td><span data-ttu-id="d3f5b-619">E84E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-619">E84E</span></span></td>
  <td><span data-ttu-id="d3f5b-620">RightArrowKeyTime3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-620">RightArrowKeyTime3</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e84f.png" alt="RightArrowKeyTime4" /></td>
  <td><span data-ttu-id="d3f5b-621">E84F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-621">E84F</span></span></td>
  <td><span data-ttu-id="d3f5b-622">RightArrowKeyTime4</span><span class="sxs-lookup"><span data-stu-id="d3f5b-622">RightArrowKeyTime4</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e850.png" alt="Battery0" /></td>
  <td><span data-ttu-id="d3f5b-623">E850</span><span class="sxs-lookup"><span data-stu-id="d3f5b-623">E850</span></span></td>
  <td><span data-ttu-id="d3f5b-624">Battery0</span><span class="sxs-lookup"><span data-stu-id="d3f5b-624">Battery0</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e851.png" alt="Battery1" /></td>
  <td><span data-ttu-id="d3f5b-625">E851</span><span class="sxs-lookup"><span data-stu-id="d3f5b-625">E851</span></span></td>
  <td><span data-ttu-id="d3f5b-626">Battery1</span><span class="sxs-lookup"><span data-stu-id="d3f5b-626">Battery1</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e852.png" alt="Battery2" /></td>
  <td><span data-ttu-id="d3f5b-627">E852</span><span class="sxs-lookup"><span data-stu-id="d3f5b-627">E852</span></span></td>
  <td><span data-ttu-id="d3f5b-628">Battery2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-628">Battery2</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e853.png" alt="Battery3" /></td>
  <td><span data-ttu-id="d3f5b-629">E853</span><span class="sxs-lookup"><span data-stu-id="d3f5b-629">E853</span></span></td>
  <td><span data-ttu-id="d3f5b-630">Battery3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-630">Battery3</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e854.png" alt="Battery4" /></td>
  <td><span data-ttu-id="d3f5b-631">E854</span><span class="sxs-lookup"><span data-stu-id="d3f5b-631">E854</span></span></td>
  <td><span data-ttu-id="d3f5b-632">Battery4</span><span class="sxs-lookup"><span data-stu-id="d3f5b-632">Battery4</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e855.png" alt="Battery5" /></td>
  <td><span data-ttu-id="d3f5b-633">E855</span><span class="sxs-lookup"><span data-stu-id="d3f5b-633">E855</span></span></td>
  <td><span data-ttu-id="d3f5b-634">Battery5</span><span class="sxs-lookup"><span data-stu-id="d3f5b-634">Battery5</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e856.png" alt="Battery6" /></td>
  <td><span data-ttu-id="d3f5b-635">E856</span><span class="sxs-lookup"><span data-stu-id="d3f5b-635">E856</span></span></td>
  <td><span data-ttu-id="d3f5b-636">Battery6</span><span class="sxs-lookup"><span data-stu-id="d3f5b-636">Battery6</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e857.png" alt="Battery7" /></td>
  <td><span data-ttu-id="d3f5b-637">E857</span><span class="sxs-lookup"><span data-stu-id="d3f5b-637">E857</span></span></td>
  <td><span data-ttu-id="d3f5b-638">Battery7</span><span class="sxs-lookup"><span data-stu-id="d3f5b-638">Battery7</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e858.png" alt="Battery8" /></td>
  <td><span data-ttu-id="d3f5b-639">E858</span><span class="sxs-lookup"><span data-stu-id="d3f5b-639">E858</span></span></td>
  <td><span data-ttu-id="d3f5b-640">Battery8</span><span class="sxs-lookup"><span data-stu-id="d3f5b-640">Battery8</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e859.png" alt="Battery9" /></td>
  <td><span data-ttu-id="d3f5b-641">E859</span><span class="sxs-lookup"><span data-stu-id="d3f5b-641">E859</span></span></td>
  <td><span data-ttu-id="d3f5b-642">Battery9</span><span class="sxs-lookup"><span data-stu-id="d3f5b-642">Battery9</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e85a.png" alt="BatteryCharging0" /></td>
  <td><span data-ttu-id="d3f5b-643">E85A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-643">E85A</span></span></td>
  <td><span data-ttu-id="d3f5b-644">BatteryCharging0</span><span class="sxs-lookup"><span data-stu-id="d3f5b-644">BatteryCharging0</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e85b.png" alt="BatteryCharging1" /></td>
  <td><span data-ttu-id="d3f5b-645">E85B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-645">E85B</span></span></td>
  <td><span data-ttu-id="d3f5b-646">BatteryCharging1</span><span class="sxs-lookup"><span data-stu-id="d3f5b-646">BatteryCharging1</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e85c.png" alt="BatteryCharging2" /></td>
  <td><span data-ttu-id="d3f5b-647">E85C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-647">E85C</span></span></td>
  <td><span data-ttu-id="d3f5b-648">BatteryCharging2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-648">BatteryCharging2</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e85d.png" alt="BatteryCharging3" /></td>
  <td><span data-ttu-id="d3f5b-649">E85D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-649">E85D</span></span></td>
  <td><span data-ttu-id="d3f5b-650">BatteryCharging3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-650">BatteryCharging3</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e85e.png" alt="BatteryCharging4" /></td>
  <td><span data-ttu-id="d3f5b-651">E85E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-651">E85E</span></span></td>
  <td><span data-ttu-id="d3f5b-652">BatteryCharging4</span><span class="sxs-lookup"><span data-stu-id="d3f5b-652">BatteryCharging4</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e85f.png" alt="BatteryCharging5" /></td>
  <td><span data-ttu-id="d3f5b-653">E85F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-653">E85F</span></span></td>
  <td><span data-ttu-id="d3f5b-654">BatteryCharging5</span><span class="sxs-lookup"><span data-stu-id="d3f5b-654">BatteryCharging5</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e860.png" alt="BatteryCharging6" /></td>
  <td><span data-ttu-id="d3f5b-655">E860</span><span class="sxs-lookup"><span data-stu-id="d3f5b-655">E860</span></span></td>
  <td><span data-ttu-id="d3f5b-656">BatteryCharging6</span><span class="sxs-lookup"><span data-stu-id="d3f5b-656">BatteryCharging6</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e861.png" alt="BatteryCharging7" /></td>
  <td><span data-ttu-id="d3f5b-657">E861</span><span class="sxs-lookup"><span data-stu-id="d3f5b-657">E861</span></span></td>
  <td><span data-ttu-id="d3f5b-658">BatteryCharging7</span><span class="sxs-lookup"><span data-stu-id="d3f5b-658">BatteryCharging7</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e862.png" alt="BatteryCharging8" /></td>
  <td><span data-ttu-id="d3f5b-659">E862</span><span class="sxs-lookup"><span data-stu-id="d3f5b-659">E862</span></span></td>
  <td><span data-ttu-id="d3f5b-660">BatteryCharging8</span><span class="sxs-lookup"><span data-stu-id="d3f5b-660">BatteryCharging8</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e863.png" alt="BatterySaver0" /></td>
  <td><span data-ttu-id="d3f5b-661">E863</span><span class="sxs-lookup"><span data-stu-id="d3f5b-661">E863</span></span></td>
  <td><span data-ttu-id="d3f5b-662">BatterySaver0</span><span class="sxs-lookup"><span data-stu-id="d3f5b-662">BatterySaver0</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e864.png" alt="BatterySaver1" /></td>
  <td><span data-ttu-id="d3f5b-663">E864</span><span class="sxs-lookup"><span data-stu-id="d3f5b-663">E864</span></span></td>
  <td><span data-ttu-id="d3f5b-664">BatterySaver1</span><span class="sxs-lookup"><span data-stu-id="d3f5b-664">BatterySaver1</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e865.png" alt="BatterySaver2" /></td>
  <td><span data-ttu-id="d3f5b-665">E865</span><span class="sxs-lookup"><span data-stu-id="d3f5b-665">E865</span></span></td>
  <td><span data-ttu-id="d3f5b-666">BatterySaver2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-666">BatterySaver2</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e866.png" alt="BatterySaver3" /></td>
  <td><span data-ttu-id="d3f5b-667">E866</span><span class="sxs-lookup"><span data-stu-id="d3f5b-667">E866</span></span></td>
  <td><span data-ttu-id="d3f5b-668">BatterySaver3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-668">BatterySaver3</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e867.png" alt="BatterySaver4" /></td>
  <td><span data-ttu-id="d3f5b-669">E867</span><span class="sxs-lookup"><span data-stu-id="d3f5b-669">E867</span></span></td>
  <td><span data-ttu-id="d3f5b-670">BatterySaver4</span><span class="sxs-lookup"><span data-stu-id="d3f5b-670">BatterySaver4</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e868.png" alt="BatterySaver5" /></td>
  <td><span data-ttu-id="d3f5b-671">E868</span><span class="sxs-lookup"><span data-stu-id="d3f5b-671">E868</span></span></td>
  <td><span data-ttu-id="d3f5b-672">BatterySaver5</span><span class="sxs-lookup"><span data-stu-id="d3f5b-672">BatterySaver5</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e869.png" alt="BatterySaver6" /></td>
  <td><span data-ttu-id="d3f5b-673">E869</span><span class="sxs-lookup"><span data-stu-id="d3f5b-673">E869</span></span></td>
  <td><span data-ttu-id="d3f5b-674">BatterySaver6</span><span class="sxs-lookup"><span data-stu-id="d3f5b-674">BatterySaver6</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e86a.png" alt="BatterySaver7" /></td>
  <td><span data-ttu-id="d3f5b-675">E86A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-675">E86A</span></span></td>
  <td><span data-ttu-id="d3f5b-676">BatterySaver7</span><span class="sxs-lookup"><span data-stu-id="d3f5b-676">BatterySaver7</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e86b.png" alt="BatterySaver8" /></td>
  <td><span data-ttu-id="d3f5b-677">E86B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-677">E86B</span></span></td>
  <td><span data-ttu-id="d3f5b-678">BatterySaver8</span><span class="sxs-lookup"><span data-stu-id="d3f5b-678">BatterySaver8</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e86c.png" alt="SignalBars1" /></td>
  <td><span data-ttu-id="d3f5b-679">E86C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-679">E86C</span></span></td>
  <td><span data-ttu-id="d3f5b-680">SignalBars1</span><span class="sxs-lookup"><span data-stu-id="d3f5b-680">SignalBars1</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e86d.png" alt="SignalBars2" /></td>
  <td><span data-ttu-id="d3f5b-681">E86D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-681">E86D</span></span></td>
  <td><span data-ttu-id="d3f5b-682">SignalBars2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-682">SignalBars2</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e86e.png" alt="SignalBars3" /></td>
  <td><span data-ttu-id="d3f5b-683">E86E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-683">E86E</span></span></td>
  <td><span data-ttu-id="d3f5b-684">SignalBars3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-684">SignalBars3</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e86f.png" alt="SignalBars4" /></td>
  <td><span data-ttu-id="d3f5b-685">E86F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-685">E86F</span></span></td>
  <td><span data-ttu-id="d3f5b-686">SignalBars4</span><span class="sxs-lookup"><span data-stu-id="d3f5b-686">SignalBars4</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e870.png" alt="SignalBars5" /></td>
  <td><span data-ttu-id="d3f5b-687">E870</span><span class="sxs-lookup"><span data-stu-id="d3f5b-687">E870</span></span></td>
  <td><span data-ttu-id="d3f5b-688">SignalBars5</span><span class="sxs-lookup"><span data-stu-id="d3f5b-688">SignalBars5</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e871.png" alt="SignalNotConnected" /></td>
  <td><span data-ttu-id="d3f5b-689">E871</span><span class="sxs-lookup"><span data-stu-id="d3f5b-689">E871</span></span></td>
  <td><span data-ttu-id="d3f5b-690">SignalNotConnected</span><span class="sxs-lookup"><span data-stu-id="d3f5b-690">SignalNotConnected</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e872.png" alt="Wifi1" /></td>
  <td><span data-ttu-id="d3f5b-691">E872</span><span class="sxs-lookup"><span data-stu-id="d3f5b-691">E872</span></span></td>
  <td><span data-ttu-id="d3f5b-692">Wifi1</span><span class="sxs-lookup"><span data-stu-id="d3f5b-692">Wifi1</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e873.png" alt="Wifi2" /></td>
  <td><span data-ttu-id="d3f5b-693">E873</span><span class="sxs-lookup"><span data-stu-id="d3f5b-693">E873</span></span></td>
  <td><span data-ttu-id="d3f5b-694">Wifi2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-694">Wifi2</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e874.png" alt="Wifi3" /></td>
  <td><span data-ttu-id="d3f5b-695">E874</span><span class="sxs-lookup"><span data-stu-id="d3f5b-695">E874</span></span></td>
  <td><span data-ttu-id="d3f5b-696">Wifi3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-696">Wifi3</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e875.png" alt="SIMLock" /></td>
  <td><span data-ttu-id="d3f5b-697">E875</span><span class="sxs-lookup"><span data-stu-id="d3f5b-697">E875</span></span></td>
  <td><span data-ttu-id="d3f5b-698">SIMLock</span><span class="sxs-lookup"><span data-stu-id="d3f5b-698">SIMLock</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e876.png" alt="SIMMissing" /></td>
  <td><span data-ttu-id="d3f5b-699">E876</span><span class="sxs-lookup"><span data-stu-id="d3f5b-699">E876</span></span></td>
  <td><span data-ttu-id="d3f5b-700">SIMMissing</span><span class="sxs-lookup"><span data-stu-id="d3f5b-700">SIMMissing</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e877.png" alt="Vibrate" /></td>
  <td><span data-ttu-id="d3f5b-701">E877</span><span class="sxs-lookup"><span data-stu-id="d3f5b-701">E877</span></span></td>
  <td><span data-ttu-id="d3f5b-702">Vibrate</span><span class="sxs-lookup"><span data-stu-id="d3f5b-702">Vibrate</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e878.png" alt="RoamingInternational" /></td>
  <td><span data-ttu-id="d3f5b-703">E878</span><span class="sxs-lookup"><span data-stu-id="d3f5b-703">E878</span></span></td>
  <td><span data-ttu-id="d3f5b-704">RoamingInternational</span><span class="sxs-lookup"><span data-stu-id="d3f5b-704">RoamingInternational</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e879.png" alt="RoamingDomestic" /></td>
  <td><span data-ttu-id="d3f5b-705">E879</span><span class="sxs-lookup"><span data-stu-id="d3f5b-705">E879</span></span></td>
  <td><span data-ttu-id="d3f5b-706">RoamingDomestic</span><span class="sxs-lookup"><span data-stu-id="d3f5b-706">RoamingDomestic</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e87a.png" alt="CallForwardInternational" /></td>
  <td><span data-ttu-id="d3f5b-707">E87A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-707">E87A</span></span></td>
  <td><span data-ttu-id="d3f5b-708">CallForwardInternational</span><span class="sxs-lookup"><span data-stu-id="d3f5b-708">CallForwardInternational</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e87b.png" alt="CallForwardRoaming" /></td>
  <td><span data-ttu-id="d3f5b-709">E87B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-709">E87B</span></span></td>
  <td><span data-ttu-id="d3f5b-710">CallForwardRoaming</span><span class="sxs-lookup"><span data-stu-id="d3f5b-710">CallForwardRoaming</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e87c.png" alt="JpnRomanji" /></td>
  <td><span data-ttu-id="d3f5b-711">E87C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-711">E87C</span></span></td>
  <td><span data-ttu-id="d3f5b-712">JpnRomanji</span><span class="sxs-lookup"><span data-stu-id="d3f5b-712">JpnRomanji</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e87d.png" alt="JpnRomanjiLock" /></td>
  <td><span data-ttu-id="d3f5b-713">E87D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-713">E87D</span></span></td>
  <td><span data-ttu-id="d3f5b-714">JpnRomanjiLock</span><span class="sxs-lookup"><span data-stu-id="d3f5b-714">JpnRomanjiLock</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e87e.png" alt="JpnRomanjiShift" /></td>
  <td><span data-ttu-id="d3f5b-715">E87E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-715">E87E</span></span></td>
  <td><span data-ttu-id="d3f5b-716">JpnRomanjiShift</span><span class="sxs-lookup"><span data-stu-id="d3f5b-716">JpnRomanjiShift</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e87f.png" alt="JpnRomanjiShiftLock" /></td>
  <td><span data-ttu-id="d3f5b-717">E87F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-717">E87F</span></span></td>
  <td><span data-ttu-id="d3f5b-718">JpnRomanjiShiftLock</span><span class="sxs-lookup"><span data-stu-id="d3f5b-718">JpnRomanjiShiftLock</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e880.png" alt="StatusDataTransfer" /></td>
  <td><span data-ttu-id="d3f5b-719">E880</span><span class="sxs-lookup"><span data-stu-id="d3f5b-719">E880</span></span></td>
  <td><span data-ttu-id="d3f5b-720">StatusDataTransfer</span><span class="sxs-lookup"><span data-stu-id="d3f5b-720">StatusDataTransfer</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e881.png" alt="StatusDataTransferVPN" /></td>
  <td><span data-ttu-id="d3f5b-721">E881</span><span class="sxs-lookup"><span data-stu-id="d3f5b-721">E881</span></span></td>
  <td><span data-ttu-id="d3f5b-722">StatusDataTransferVPN</span><span class="sxs-lookup"><span data-stu-id="d3f5b-722">StatusDataTransferVPN</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e882.png" alt="StatusDualSIM2" /></td>
  <td><span data-ttu-id="d3f5b-723">E882</span><span class="sxs-lookup"><span data-stu-id="d3f5b-723">E882</span></span></td>
  <td><span data-ttu-id="d3f5b-724">StatusDualSIM2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-724">StatusDualSIM2</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e883.png" alt="StatusDualSIM2VPN" /></td>
  <td><span data-ttu-id="d3f5b-725">E883</span><span class="sxs-lookup"><span data-stu-id="d3f5b-725">E883</span></span></td>
  <td><span data-ttu-id="d3f5b-726">StatusDualSIM2VPN</span><span class="sxs-lookup"><span data-stu-id="d3f5b-726">StatusDualSIM2VPN</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e884.png" alt="StatusDualSIM1" /></td>
  <td><span data-ttu-id="d3f5b-727">E884</span><span class="sxs-lookup"><span data-stu-id="d3f5b-727">E884</span></span></td>
  <td><span data-ttu-id="d3f5b-728">StatusDualSIM1</span><span class="sxs-lookup"><span data-stu-id="d3f5b-728">StatusDualSIM1</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e885.png" alt="StatusDualSIM1VPN" /></td>
  <td><span data-ttu-id="d3f5b-729">E885</span><span class="sxs-lookup"><span data-stu-id="d3f5b-729">E885</span></span></td>
  <td><span data-ttu-id="d3f5b-730">StatusDualSIM1VPN</span><span class="sxs-lookup"><span data-stu-id="d3f5b-730">StatusDualSIM1VPN</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e886.png" alt="StatusSGLTE" /></td>
  <td><span data-ttu-id="d3f5b-731">E886</span><span class="sxs-lookup"><span data-stu-id="d3f5b-731">E886</span></span></td>
  <td><span data-ttu-id="d3f5b-732">StatusSGLTE</span><span class="sxs-lookup"><span data-stu-id="d3f5b-732">StatusSGLTE</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e887.png" alt="StatusSGLTECell" /></td>
  <td><span data-ttu-id="d3f5b-733">E887</span><span class="sxs-lookup"><span data-stu-id="d3f5b-733">E887</span></span></td>
  <td><span data-ttu-id="d3f5b-734">StatusSGLTECell</span><span class="sxs-lookup"><span data-stu-id="d3f5b-734">StatusSGLTECell</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e888.png" alt="StatusSGLTEDataVPN" /></td>
  <td><span data-ttu-id="d3f5b-735">E888</span><span class="sxs-lookup"><span data-stu-id="d3f5b-735">E888</span></span></td>
  <td><span data-ttu-id="d3f5b-736">StatusSGLTEDataVPN</span><span class="sxs-lookup"><span data-stu-id="d3f5b-736">StatusSGLTEDataVPN</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e889.png" alt="StatusVPN" /></td>
  <td><span data-ttu-id="d3f5b-737">E889</span><span class="sxs-lookup"><span data-stu-id="d3f5b-737">E889</span></span></td>
  <td><span data-ttu-id="d3f5b-738">StatusVPN</span><span class="sxs-lookup"><span data-stu-id="d3f5b-738">StatusVPN</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e88a.png" alt="WifiHotspot" /></td>
  <td><span data-ttu-id="d3f5b-739">E88A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-739">E88A</span></span></td>
  <td><span data-ttu-id="d3f5b-740">WifiHotspot</span><span class="sxs-lookup"><span data-stu-id="d3f5b-740">WifiHotspot</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e88b.png" alt="LanguageKor" /></td>
  <td><span data-ttu-id="d3f5b-741">E88B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-741">E88B</span></span></td>
  <td><span data-ttu-id="d3f5b-742">LanguageKor</span><span class="sxs-lookup"><span data-stu-id="d3f5b-742">LanguageKor</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e88c.png" alt="LanguageCht" /></td>
  <td><span data-ttu-id="d3f5b-743">E88C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-743">E88C</span></span></td>
  <td><span data-ttu-id="d3f5b-744">LanguageCht</span><span class="sxs-lookup"><span data-stu-id="d3f5b-744">LanguageCht</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e88d.png" alt="LanguageChs" /></td>
  <td><span data-ttu-id="d3f5b-745">E88D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-745">E88D</span></span></td>
  <td><span data-ttu-id="d3f5b-746">LanguageChs</span><span class="sxs-lookup"><span data-stu-id="d3f5b-746">LanguageChs</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e88e.png" alt="USB" /></td>
  <td><span data-ttu-id="d3f5b-747">E88E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-747">E88E</span></span></td>
  <td><span data-ttu-id="d3f5b-748">USB</span><span class="sxs-lookup"><span data-stu-id="d3f5b-748">USB</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e88f.png" alt="InkingToolFill" /></td>
  <td><span data-ttu-id="d3f5b-749">E88F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-749">E88F</span></span></td>
  <td><span data-ttu-id="d3f5b-750">InkingToolFill</span><span class="sxs-lookup"><span data-stu-id="d3f5b-750">InkingToolFill</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e890.png" alt="View" /></td>
  <td><span data-ttu-id="d3f5b-751">E890</span><span class="sxs-lookup"><span data-stu-id="d3f5b-751">E890</span></span></td>
  <td><span data-ttu-id="d3f5b-752">Ansicht</span><span class="sxs-lookup"><span data-stu-id="d3f5b-752">View</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e891.png" alt="HighlightFill" /></td>
  <td><span data-ttu-id="d3f5b-753">E891</span><span class="sxs-lookup"><span data-stu-id="d3f5b-753">E891</span></span></td>
  <td><span data-ttu-id="d3f5b-754">HighlightFill</span><span class="sxs-lookup"><span data-stu-id="d3f5b-754">HighlightFill</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e892.png" alt="Previous" /></td>
  <td><span data-ttu-id="d3f5b-755">E892</span><span class="sxs-lookup"><span data-stu-id="d3f5b-755">E892</span></span></td>
  <td><span data-ttu-id="d3f5b-756">Vorherige</span><span class="sxs-lookup"><span data-stu-id="d3f5b-756">Previous</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e893.png" alt="Next" /></td>
  <td><span data-ttu-id="d3f5b-757">E893</span><span class="sxs-lookup"><span data-stu-id="d3f5b-757">E893</span></span></td>
  <td><span data-ttu-id="d3f5b-758">Nächste</span><span class="sxs-lookup"><span data-stu-id="d3f5b-758">Next</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e894.png" alt="Clear" /></td>
  <td><span data-ttu-id="d3f5b-759">E894</span><span class="sxs-lookup"><span data-stu-id="d3f5b-759">E894</span></span></td>
  <td><span data-ttu-id="d3f5b-760">Clear</span><span class="sxs-lookup"><span data-stu-id="d3f5b-760">Clear</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e895.png" alt="Sync" /></td>
  <td><span data-ttu-id="d3f5b-761">E895</span><span class="sxs-lookup"><span data-stu-id="d3f5b-761">E895</span></span></td>
  <td><span data-ttu-id="d3f5b-762">Synchronisieren</span><span class="sxs-lookup"><span data-stu-id="d3f5b-762">Sync</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e896.png" alt="Download" /></td>
  <td><span data-ttu-id="d3f5b-763">E896</span><span class="sxs-lookup"><span data-stu-id="d3f5b-763">E896</span></span></td>
  <td><span data-ttu-id="d3f5b-764">Herunterladen</span><span class="sxs-lookup"><span data-stu-id="d3f5b-764">Download</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e897.png" alt="Help" /></td>
  <td><span data-ttu-id="d3f5b-765">E897</span><span class="sxs-lookup"><span data-stu-id="d3f5b-765">E897</span></span></td>
  <td><span data-ttu-id="d3f5b-766">Hilfe</span><span class="sxs-lookup"><span data-stu-id="d3f5b-766">Help</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e898.png" alt="Upload" /></td>
  <td><span data-ttu-id="d3f5b-767">E898</span><span class="sxs-lookup"><span data-stu-id="d3f5b-767">E898</span></span></td>
  <td><span data-ttu-id="d3f5b-768">Upload</span><span class="sxs-lookup"><span data-stu-id="d3f5b-768">Upload</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e899.png" alt="Emoji" /></td>
  <td><span data-ttu-id="d3f5b-769">E899</span><span class="sxs-lookup"><span data-stu-id="d3f5b-769">E899</span></span></td>
  <td><span data-ttu-id="d3f5b-770">Emoji</span><span class="sxs-lookup"><span data-stu-id="d3f5b-770">Emoji</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e89a.png" alt="TwoPage" /></td>
  <td><span data-ttu-id="d3f5b-771">E89A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-771">E89A</span></span></td>
  <td><span data-ttu-id="d3f5b-772">TwoPage</span><span class="sxs-lookup"><span data-stu-id="d3f5b-772">TwoPage</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e89b.png" alt="LeaveChat" /></td>
  <td><span data-ttu-id="d3f5b-773">E89B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-773">E89B</span></span></td>
  <td><span data-ttu-id="d3f5b-774">LeaveChat</span><span class="sxs-lookup"><span data-stu-id="d3f5b-774">LeaveChat</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e89c.png" alt="MailForward" /></td>
  <td><span data-ttu-id="d3f5b-775">E89C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-775">E89C</span></span></td>
  <td><span data-ttu-id="d3f5b-776">MailForward</span><span class="sxs-lookup"><span data-stu-id="d3f5b-776">MailForward</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e89e.png" alt="RotateCamera" /></td>
  <td><span data-ttu-id="d3f5b-777">E89E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-777">E89E</span></span></td>
  <td><span data-ttu-id="d3f5b-778">RotateCamera</span><span class="sxs-lookup"><span data-stu-id="d3f5b-778">RotateCamera</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e89f.png" alt="ClosePane" /></td>
  <td><span data-ttu-id="d3f5b-779">E89F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-779">E89F</span></span></td>
  <td><span data-ttu-id="d3f5b-780">ClosePane</span><span class="sxs-lookup"><span data-stu-id="d3f5b-780">ClosePane</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8a0.png" alt="OpenPane" /></td>
  <td><span data-ttu-id="d3f5b-781">E8A0</span><span class="sxs-lookup"><span data-stu-id="d3f5b-781">E8A0</span></span></td>
  <td><span data-ttu-id="d3f5b-782">OpenPane</span><span class="sxs-lookup"><span data-stu-id="d3f5b-782">OpenPane</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8a1.png" alt="PreviewLink" /></td>
  <td><span data-ttu-id="d3f5b-783">E8A1</span><span class="sxs-lookup"><span data-stu-id="d3f5b-783">E8A1</span></span></td>
  <td><span data-ttu-id="d3f5b-784">PreviewLink</span><span class="sxs-lookup"><span data-stu-id="d3f5b-784">PreviewLink</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8a2.png" alt="AttachCamera" /></td>
  <td><span data-ttu-id="d3f5b-785">E8A2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-785">E8A2</span></span></td>
  <td><span data-ttu-id="d3f5b-786">AttachCamera</span><span class="sxs-lookup"><span data-stu-id="d3f5b-786">AttachCamera</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8a3.png" alt="ZoomIn" /></td>
  <td><span data-ttu-id="d3f5b-787">E8A3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-787">E8A3</span></span></td>
  <td><span data-ttu-id="d3f5b-788">ZoomIn</span><span class="sxs-lookup"><span data-stu-id="d3f5b-788">ZoomIn</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8a4.png" alt="Bookmarks" /></td>
  <td><span data-ttu-id="d3f5b-789">E8A4</span><span class="sxs-lookup"><span data-stu-id="d3f5b-789">E8A4</span></span></td>
  <td><span data-ttu-id="d3f5b-790">Bookmarks</span><span class="sxs-lookup"><span data-stu-id="d3f5b-790">Bookmarks</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8a5.png" alt="Document" /></td>
  <td><span data-ttu-id="d3f5b-791">E8A5</span><span class="sxs-lookup"><span data-stu-id="d3f5b-791">E8A5</span></span></td>
  <td><span data-ttu-id="d3f5b-792">Dokument</span><span class="sxs-lookup"><span data-stu-id="d3f5b-792">Document</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8a6.png" alt="ProtectedDocument" /></td>
  <td><span data-ttu-id="d3f5b-793">E8A6</span><span class="sxs-lookup"><span data-stu-id="d3f5b-793">E8A6</span></span></td>
  <td><span data-ttu-id="d3f5b-794">ProtectedDocument</span><span class="sxs-lookup"><span data-stu-id="d3f5b-794">ProtectedDocument</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8a7.png" alt="OpenInNewWindow" /></td>
  <td><span data-ttu-id="d3f5b-795">E8A7</span><span class="sxs-lookup"><span data-stu-id="d3f5b-795">E8A7</span></span></td>
  <td><span data-ttu-id="d3f5b-796">OpenInNewWindow</span><span class="sxs-lookup"><span data-stu-id="d3f5b-796">OpenInNewWindow</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8a8.png" alt="MailFill" /></td>
  <td><span data-ttu-id="d3f5b-797">E8A8</span><span class="sxs-lookup"><span data-stu-id="d3f5b-797">E8A8</span></span></td>
  <td><span data-ttu-id="d3f5b-798">MailFill</span><span class="sxs-lookup"><span data-stu-id="d3f5b-798">MailFill</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8a9.png" alt="ViewAll" /></td>
  <td><span data-ttu-id="d3f5b-799">E8A9</span><span class="sxs-lookup"><span data-stu-id="d3f5b-799">E8A9</span></span></td>
  <td><span data-ttu-id="d3f5b-800">ViewAll</span><span class="sxs-lookup"><span data-stu-id="d3f5b-800">ViewAll</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8aa.png" alt="VideoChat" /></td>
  <td><span data-ttu-id="d3f5b-801">E8AA</span><span class="sxs-lookup"><span data-stu-id="d3f5b-801">E8AA</span></span></td>
  <td><span data-ttu-id="d3f5b-802">VideoChat</span><span class="sxs-lookup"><span data-stu-id="d3f5b-802">VideoChat</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8ab.png" alt="Switch" /></td>
  <td><span data-ttu-id="d3f5b-803">E8AB</span><span class="sxs-lookup"><span data-stu-id="d3f5b-803">E8AB</span></span></td>
  <td><span data-ttu-id="d3f5b-804">Wechsel</span><span class="sxs-lookup"><span data-stu-id="d3f5b-804">Switch</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8ac.png" alt="Rename" /></td>
  <td><span data-ttu-id="d3f5b-805">E8AC</span><span class="sxs-lookup"><span data-stu-id="d3f5b-805">E8AC</span></span></td>
  <td><span data-ttu-id="d3f5b-806">Rename</span><span class="sxs-lookup"><span data-stu-id="d3f5b-806">Rename</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8ad.png" alt="Go" /></td>
  <td><span data-ttu-id="d3f5b-807">E8AD</span><span class="sxs-lookup"><span data-stu-id="d3f5b-807">E8AD</span></span></td>
  <td><span data-ttu-id="d3f5b-808">Go</span><span class="sxs-lookup"><span data-stu-id="d3f5b-808">Go</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8ae.png" alt="SurfaceHub" /></td>
  <td><span data-ttu-id="d3f5b-809">E8AE</span><span class="sxs-lookup"><span data-stu-id="d3f5b-809">E8AE</span></span></td>
  <td><span data-ttu-id="d3f5b-810">SurfaceHub</span><span class="sxs-lookup"><span data-stu-id="d3f5b-810">SurfaceHub</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8af.png" alt="Remote" /></td>
  <td><span data-ttu-id="d3f5b-811">E8AF</span><span class="sxs-lookup"><span data-stu-id="d3f5b-811">E8AF</span></span></td>
  <td><span data-ttu-id="d3f5b-812">Remote</span><span class="sxs-lookup"><span data-stu-id="d3f5b-812">Remote</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8b0.png" alt="Click" /></td>
  <td><span data-ttu-id="d3f5b-813">E8B0</span><span class="sxs-lookup"><span data-stu-id="d3f5b-813">E8B0</span></span></td>
  <td><span data-ttu-id="d3f5b-814">Klick</span><span class="sxs-lookup"><span data-stu-id="d3f5b-814">Click</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8b1.png" alt="Shuffle" /></td>
  <td><span data-ttu-id="d3f5b-815">E8B1</span><span class="sxs-lookup"><span data-stu-id="d3f5b-815">E8B1</span></span></td>
  <td><span data-ttu-id="d3f5b-816">Shuffle</span><span class="sxs-lookup"><span data-stu-id="d3f5b-816">Shuffle</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8b2.png" alt="Movies" /></td>
  <td><span data-ttu-id="d3f5b-817">E8B2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-817">E8B2</span></span></td>
  <td><span data-ttu-id="d3f5b-818">Filme</span><span class="sxs-lookup"><span data-stu-id="d3f5b-818">Movies</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8b3.png" alt="SelectAll" /></td>
  <td><span data-ttu-id="d3f5b-819">E8B3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-819">E8B3</span></span></td>
  <td><span data-ttu-id="d3f5b-820">SelectAll</span><span class="sxs-lookup"><span data-stu-id="d3f5b-820">SelectAll</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8b4.png" alt="Orientation" /></td>
  <td><span data-ttu-id="d3f5b-821">E8B4</span><span class="sxs-lookup"><span data-stu-id="d3f5b-821">E8B4</span></span></td>
  <td><span data-ttu-id="d3f5b-822">Orientation</span><span class="sxs-lookup"><span data-stu-id="d3f5b-822">Orientation</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8b5.png" alt="Import" /></td>
  <td><span data-ttu-id="d3f5b-823">E8B5</span><span class="sxs-lookup"><span data-stu-id="d3f5b-823">E8B5</span></span></td>
  <td><span data-ttu-id="d3f5b-824">Import</span><span class="sxs-lookup"><span data-stu-id="d3f5b-824">Import</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8b6.png" alt="ImportAll" /></td>
  <td><span data-ttu-id="d3f5b-825">E8B6</span><span class="sxs-lookup"><span data-stu-id="d3f5b-825">E8B6</span></span></td>
  <td><span data-ttu-id="d3f5b-826">ImportAll</span><span class="sxs-lookup"><span data-stu-id="d3f5b-826">ImportAll</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8b7.png" alt="Folder" /></td>
  <td><span data-ttu-id="d3f5b-827">E8B7</span><span class="sxs-lookup"><span data-stu-id="d3f5b-827">E8B7</span></span></td>
  <td><span data-ttu-id="d3f5b-828">Ordner</span><span class="sxs-lookup"><span data-stu-id="d3f5b-828">Folder</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8b8.png" alt="Webcam" /></td>
  <td><span data-ttu-id="d3f5b-829">E8B8</span><span class="sxs-lookup"><span data-stu-id="d3f5b-829">E8B8</span></span></td>
  <td><span data-ttu-id="d3f5b-830">Webcam</span><span class="sxs-lookup"><span data-stu-id="d3f5b-830">Webcam</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8b9.png" alt="Picture" /></td>
  <td><span data-ttu-id="d3f5b-831">E8B9</span><span class="sxs-lookup"><span data-stu-id="d3f5b-831">E8B9</span></span></td>
  <td><span data-ttu-id="d3f5b-832">Bild</span><span class="sxs-lookup"><span data-stu-id="d3f5b-832">Picture</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8ba.png" alt="Caption" /></td>
  <td><span data-ttu-id="d3f5b-833">E8BA</span><span class="sxs-lookup"><span data-stu-id="d3f5b-833">E8BA</span></span></td>
  <td><span data-ttu-id="d3f5b-834">Untertitel für Hörgeschädigte</span><span class="sxs-lookup"><span data-stu-id="d3f5b-834">Caption</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8bb.png" alt="ChromeClose" /></td>
  <td><span data-ttu-id="d3f5b-835">E8BB</span><span class="sxs-lookup"><span data-stu-id="d3f5b-835">E8BB</span></span></td>
  <td><span data-ttu-id="d3f5b-836">ChromeClose</span><span class="sxs-lookup"><span data-stu-id="d3f5b-836">ChromeClose</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8bc.png" alt="ShowResults" /></td>
  <td><span data-ttu-id="d3f5b-837">E8BC</span><span class="sxs-lookup"><span data-stu-id="d3f5b-837">E8BC</span></span></td>
  <td><span data-ttu-id="d3f5b-838">ShowResults</span><span class="sxs-lookup"><span data-stu-id="d3f5b-838">ShowResults</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8bd.png" alt="Message" /></td>
  <td><span data-ttu-id="d3f5b-839">E8BD</span><span class="sxs-lookup"><span data-stu-id="d3f5b-839">E8BD</span></span></td>
  <td><span data-ttu-id="d3f5b-840">Nachricht</span><span class="sxs-lookup"><span data-stu-id="d3f5b-840">Message</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8be.png" alt="Leaf" /></td>
  <td><span data-ttu-id="d3f5b-841">E8BE</span><span class="sxs-lookup"><span data-stu-id="d3f5b-841">E8BE</span></span></td>
  <td><span data-ttu-id="d3f5b-842">Leaf</span><span class="sxs-lookup"><span data-stu-id="d3f5b-842">Leaf</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8bf.png" alt="CalendarDay" /></td>
  <td><span data-ttu-id="d3f5b-843">E8BF</span><span class="sxs-lookup"><span data-stu-id="d3f5b-843">E8BF</span></span></td>
  <td><span data-ttu-id="d3f5b-844">CalendarDay</span><span class="sxs-lookup"><span data-stu-id="d3f5b-844">CalendarDay</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8c0.png" alt="CalendarWeek" /></td>
  <td><span data-ttu-id="d3f5b-845">E8C0</span><span class="sxs-lookup"><span data-stu-id="d3f5b-845">E8C0</span></span></td>
  <td><span data-ttu-id="d3f5b-846">CalendarWeek</span><span class="sxs-lookup"><span data-stu-id="d3f5b-846">CalendarWeek</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8c1.png" alt="Characters" /></td>
  <td><span data-ttu-id="d3f5b-847">E8C1</span><span class="sxs-lookup"><span data-stu-id="d3f5b-847">E8C1</span></span></td>
  <td><span data-ttu-id="d3f5b-848">Characters</span><span class="sxs-lookup"><span data-stu-id="d3f5b-848">Characters</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8c2.png" alt="MailReplyAll" /></td>
  <td><span data-ttu-id="d3f5b-849">E8C2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-849">E8C2</span></span></td>
  <td><span data-ttu-id="d3f5b-850">MailReplyAll</span><span class="sxs-lookup"><span data-stu-id="d3f5b-850">MailReplyAll</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8c3.png" alt="Read" /></td>
  <td><span data-ttu-id="d3f5b-851">E8C3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-851">E8C3</span></span></td>
  <td><span data-ttu-id="d3f5b-852">Lesen</span><span class="sxs-lookup"><span data-stu-id="d3f5b-852">Read</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8c4.png" alt="ShowBcc" /></td>
  <td><span data-ttu-id="d3f5b-853">E8C4</span><span class="sxs-lookup"><span data-stu-id="d3f5b-853">E8C4</span></span></td>
  <td><span data-ttu-id="d3f5b-854">ShowBcc</span><span class="sxs-lookup"><span data-stu-id="d3f5b-854">ShowBcc</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8c5.png" alt="HideBcc" /></td>
  <td><span data-ttu-id="d3f5b-855">E8C5</span><span class="sxs-lookup"><span data-stu-id="d3f5b-855">E8C5</span></span></td>
  <td><span data-ttu-id="d3f5b-856">HideBcc</span><span class="sxs-lookup"><span data-stu-id="d3f5b-856">HideBcc</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8c6.png" alt="Cut" /></td>
  <td><span data-ttu-id="d3f5b-857">E8C6</span><span class="sxs-lookup"><span data-stu-id="d3f5b-857">E8C6</span></span></td>
  <td><span data-ttu-id="d3f5b-858">Ausschneiden</span><span class="sxs-lookup"><span data-stu-id="d3f5b-858">Cut</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8c8.png" alt="Copy" /></td>
  <td><span data-ttu-id="d3f5b-859">E8C8</span><span class="sxs-lookup"><span data-stu-id="d3f5b-859">E8C8</span></span></td>
  <td><span data-ttu-id="d3f5b-860">Kopieren</span><span class="sxs-lookup"><span data-stu-id="d3f5b-860">Copy</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8c9.png" alt="Important" /></td>
  <td><span data-ttu-id="d3f5b-861">E8C9</span><span class="sxs-lookup"><span data-stu-id="d3f5b-861">E8C9</span></span></td>
  <td><span data-ttu-id="d3f5b-862">Wichtig</span><span class="sxs-lookup"><span data-stu-id="d3f5b-862">Important</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8ca.png" alt="MailReply" /></td>
  <td><span data-ttu-id="d3f5b-863">E8CA</span><span class="sxs-lookup"><span data-stu-id="d3f5b-863">E8CA</span></span></td>
  <td><span data-ttu-id="d3f5b-864">MailReply</span><span class="sxs-lookup"><span data-stu-id="d3f5b-864">MailReply</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8cb.png" alt="Sort" /></td>
  <td><span data-ttu-id="d3f5b-865">E8CB</span><span class="sxs-lookup"><span data-stu-id="d3f5b-865">E8CB</span></span></td>
  <td><span data-ttu-id="d3f5b-866">Sort</span><span class="sxs-lookup"><span data-stu-id="d3f5b-866">Sort</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8cc.png" alt="MobileTablet" /></td>
  <td><span data-ttu-id="d3f5b-867">E8CC</span><span class="sxs-lookup"><span data-stu-id="d3f5b-867">E8CC</span></span></td>
  <td><span data-ttu-id="d3f5b-868">MobileTablet</span><span class="sxs-lookup"><span data-stu-id="d3f5b-868">MobileTablet</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8cd.png" alt="DisconnectDrive" /></td>
  <td><span data-ttu-id="d3f5b-869">E8CD</span><span class="sxs-lookup"><span data-stu-id="d3f5b-869">E8CD</span></span></td>
  <td><span data-ttu-id="d3f5b-870">DisconnectDrive</span><span class="sxs-lookup"><span data-stu-id="d3f5b-870">DisconnectDrive</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8ce.png" alt="MapDrive" /></td>
  <td><span data-ttu-id="d3f5b-871">E8CE</span><span class="sxs-lookup"><span data-stu-id="d3f5b-871">E8CE</span></span></td>
  <td><span data-ttu-id="d3f5b-872">MapDrive</span><span class="sxs-lookup"><span data-stu-id="d3f5b-872">MapDrive</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8cf.png" alt="ContactPresence" /></td>
  <td><span data-ttu-id="d3f5b-873">E8CF</span><span class="sxs-lookup"><span data-stu-id="d3f5b-873">E8CF</span></span></td>
  <td><span data-ttu-id="d3f5b-874">ContactPresence</span><span class="sxs-lookup"><span data-stu-id="d3f5b-874">ContactPresence</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8d0.png" alt="Priority" /></td>
  <td><span data-ttu-id="d3f5b-875">E8D0</span><span class="sxs-lookup"><span data-stu-id="d3f5b-875">E8D0</span></span></td>
  <td><span data-ttu-id="d3f5b-876">Priorität</span><span class="sxs-lookup"><span data-stu-id="d3f5b-876">Priority</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8d1.png" alt="GotoToday" /></td>
  <td><span data-ttu-id="d3f5b-877">E8D1</span><span class="sxs-lookup"><span data-stu-id="d3f5b-877">E8D1</span></span></td>
  <td><span data-ttu-id="d3f5b-878">GoToToday</span><span class="sxs-lookup"><span data-stu-id="d3f5b-878">GotoToday</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8d2.png" alt="Font" /></td>
  <td><span data-ttu-id="d3f5b-879">E8D2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-879">E8D2</span></span></td>
  <td><span data-ttu-id="d3f5b-880">Font</span><span class="sxs-lookup"><span data-stu-id="d3f5b-880">Font</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8d3.png" alt="FontColor" /></td>
  <td><span data-ttu-id="d3f5b-881">E8D3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-881">E8D3</span></span></td>
  <td><span data-ttu-id="d3f5b-882">FontColor</span><span class="sxs-lookup"><span data-stu-id="d3f5b-882">FontColor</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8d4.png" alt="Contact2" /></td>
  <td><span data-ttu-id="d3f5b-883">E8D4</span><span class="sxs-lookup"><span data-stu-id="d3f5b-883">E8D4</span></span></td>
  <td><span data-ttu-id="d3f5b-884">Contact2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-884">Contact2</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8d5.png" alt="FolderFill" /></td>
  <td><span data-ttu-id="d3f5b-885">E8D5</span><span class="sxs-lookup"><span data-stu-id="d3f5b-885">E8D5</span></span></td>
  <td><span data-ttu-id="d3f5b-886">FolderFill</span><span class="sxs-lookup"><span data-stu-id="d3f5b-886">FolderFill</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8d6.png" alt="Audio" /></td>
  <td><span data-ttu-id="d3f5b-887">E8D6</span><span class="sxs-lookup"><span data-stu-id="d3f5b-887">E8D6</span></span></td>
  <td><span data-ttu-id="d3f5b-888">Audio</span><span class="sxs-lookup"><span data-stu-id="d3f5b-888">Audio</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8d7.png" alt="Permissions" /></td>
  <td><span data-ttu-id="d3f5b-889">E8D7</span><span class="sxs-lookup"><span data-stu-id="d3f5b-889">E8D7</span></span></td>
  <td><span data-ttu-id="d3f5b-890">Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="d3f5b-890">Permissions</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8d8.png" alt="DisableUpdates" /></td>
  <td><span data-ttu-id="d3f5b-891">E8D8</span><span class="sxs-lookup"><span data-stu-id="d3f5b-891">E8D8</span></span></td>
  <td><span data-ttu-id="d3f5b-892">DisableUpdates</span><span class="sxs-lookup"><span data-stu-id="d3f5b-892">DisableUpdates</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8d9.png" alt="Unfavorite" /></td>
  <td><span data-ttu-id="d3f5b-893">E8D9</span><span class="sxs-lookup"><span data-stu-id="d3f5b-893">E8D9</span></span></td>
  <td><span data-ttu-id="d3f5b-894">Unfavorite</span><span class="sxs-lookup"><span data-stu-id="d3f5b-894">Unfavorite</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8da.png" alt="OpenLocal" /></td>
  <td><span data-ttu-id="d3f5b-895">E8DA</span><span class="sxs-lookup"><span data-stu-id="d3f5b-895">E8DA</span></span></td>
  <td><span data-ttu-id="d3f5b-896">OpenLocal</span><span class="sxs-lookup"><span data-stu-id="d3f5b-896">OpenLocal</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8db.png" alt="Italic" /></td>
  <td><span data-ttu-id="d3f5b-897">E8DB</span><span class="sxs-lookup"><span data-stu-id="d3f5b-897">E8DB</span></span></td>
  <td><span data-ttu-id="d3f5b-898">Kursiv</span><span class="sxs-lookup"><span data-stu-id="d3f5b-898">Italic</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8dc.png" alt="Underline" /></td>
  <td><span data-ttu-id="d3f5b-899">E8DC</span><span class="sxs-lookup"><span data-stu-id="d3f5b-899">E8DC</span></span></td>
  <td><span data-ttu-id="d3f5b-900">Unterstreichen</span><span class="sxs-lookup"><span data-stu-id="d3f5b-900">Underline</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8dd.png" alt="Bold" /></td>
  <td><span data-ttu-id="d3f5b-901">E8DD</span><span class="sxs-lookup"><span data-stu-id="d3f5b-901">E8DD</span></span></td>
  <td><span data-ttu-id="d3f5b-902">Fett</span><span class="sxs-lookup"><span data-stu-id="d3f5b-902">Bold</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8de.png" alt="MoveToFolder" /></td>
  <td><span data-ttu-id="d3f5b-903">E8DE</span><span class="sxs-lookup"><span data-stu-id="d3f5b-903">E8DE</span></span></td>
  <td><span data-ttu-id="d3f5b-904">MoveToFolder</span><span class="sxs-lookup"><span data-stu-id="d3f5b-904">MoveToFolder</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8df.png" alt="LikeDislike" /></td>
  <td><span data-ttu-id="d3f5b-905">E8DF</span><span class="sxs-lookup"><span data-stu-id="d3f5b-905">E8DF</span></span></td>
  <td><span data-ttu-id="d3f5b-906">LikeDislike</span><span class="sxs-lookup"><span data-stu-id="d3f5b-906">LikeDislike</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8e0.png" alt="Dislike" /></td>
  <td><span data-ttu-id="d3f5b-907">E8E0</span><span class="sxs-lookup"><span data-stu-id="d3f5b-907">E8E0</span></span></td>
  <td><span data-ttu-id="d3f5b-908">Dislike</span><span class="sxs-lookup"><span data-stu-id="d3f5b-908">Dislike</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8e1.png" alt="Like" /></td>
  <td><span data-ttu-id="d3f5b-909">E8E1</span><span class="sxs-lookup"><span data-stu-id="d3f5b-909">E8E1</span></span></td>
  <td><span data-ttu-id="d3f5b-910">Like</span><span class="sxs-lookup"><span data-stu-id="d3f5b-910">Like</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8e2.png" alt="AlignRight" /></td>
  <td><span data-ttu-id="d3f5b-911">E8E2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-911">E8E2</span></span></td>
  <td><span data-ttu-id="d3f5b-912">AlignRight</span><span class="sxs-lookup"><span data-stu-id="d3f5b-912">AlignRight</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8e3.png" alt="AlignCenter" /></td>
  <td><span data-ttu-id="d3f5b-913">E8E3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-913">E8E3</span></span></td>
  <td><span data-ttu-id="d3f5b-914">AlignCenter</span><span class="sxs-lookup"><span data-stu-id="d3f5b-914">AlignCenter</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8e4.png" alt="AlignLeft" /></td>
  <td><span data-ttu-id="d3f5b-915">E8E4</span><span class="sxs-lookup"><span data-stu-id="d3f5b-915">E8E4</span></span></td>
  <td><span data-ttu-id="d3f5b-916">AlignLeft</span><span class="sxs-lookup"><span data-stu-id="d3f5b-916">AlignLeft</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8e5.png" alt="OpenFile" /></td>
  <td><span data-ttu-id="d3f5b-917">E8E5</span><span class="sxs-lookup"><span data-stu-id="d3f5b-917">E8E5</span></span></td>
  <td><span data-ttu-id="d3f5b-918">OpenFile</span><span class="sxs-lookup"><span data-stu-id="d3f5b-918">OpenFile</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8e6.png" alt="ClearSelection" /></td>
  <td><span data-ttu-id="d3f5b-919">E8E6</span><span class="sxs-lookup"><span data-stu-id="d3f5b-919">E8E6</span></span></td>
  <td><span data-ttu-id="d3f5b-920">ClearSelection</span><span class="sxs-lookup"><span data-stu-id="d3f5b-920">ClearSelection</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8e7.png" alt="FontDecrease" /></td>
  <td><span data-ttu-id="d3f5b-921">E8E7</span><span class="sxs-lookup"><span data-stu-id="d3f5b-921">E8E7</span></span></td>
  <td><span data-ttu-id="d3f5b-922">FontDecrease</span><span class="sxs-lookup"><span data-stu-id="d3f5b-922">FontDecrease</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8e8.png" alt="FontIncrease" /></td>
  <td><span data-ttu-id="d3f5b-923">E8E8</span><span class="sxs-lookup"><span data-stu-id="d3f5b-923">E8E8</span></span></td>
  <td><span data-ttu-id="d3f5b-924">FontIncrease</span><span class="sxs-lookup"><span data-stu-id="d3f5b-924">FontIncrease</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8e9.png" alt="FontSize" /></td>
  <td><span data-ttu-id="d3f5b-925">E8E9</span><span class="sxs-lookup"><span data-stu-id="d3f5b-925">E8E9</span></span></td>
  <td><span data-ttu-id="d3f5b-926">FontSize</span><span class="sxs-lookup"><span data-stu-id="d3f5b-926">FontSize</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8ea.png" alt="CellPhone" /></td>
  <td><span data-ttu-id="d3f5b-927">E8EA</span><span class="sxs-lookup"><span data-stu-id="d3f5b-927">E8EA</span></span></td>
  <td><span data-ttu-id="d3f5b-928">CellPhone</span><span class="sxs-lookup"><span data-stu-id="d3f5b-928">CellPhone</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8eb.png" alt="Reshare" /></td>
  <td><span data-ttu-id="d3f5b-929">E8EB</span><span class="sxs-lookup"><span data-stu-id="d3f5b-929">E8EB</span></span></td>
  <td><span data-ttu-id="d3f5b-930">Reshare</span><span class="sxs-lookup"><span data-stu-id="d3f5b-930">Reshare</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8ec.png" alt="Tag" /></td>
  <td><span data-ttu-id="d3f5b-931">E8EC</span><span class="sxs-lookup"><span data-stu-id="d3f5b-931">E8EC</span></span></td>
  <td><span data-ttu-id="d3f5b-932">Tag</span><span class="sxs-lookup"><span data-stu-id="d3f5b-932">Tag</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8ed.png" alt="RepeatOne" /></td>
  <td><span data-ttu-id="d3f5b-933">E8ED</span><span class="sxs-lookup"><span data-stu-id="d3f5b-933">E8ED</span></span></td>
  <td><span data-ttu-id="d3f5b-934">RepeatOne</span><span class="sxs-lookup"><span data-stu-id="d3f5b-934">RepeatOne</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8ee.png" alt="RepeatAll" /></td>
  <td><span data-ttu-id="d3f5b-935">E8EE</span><span class="sxs-lookup"><span data-stu-id="d3f5b-935">E8EE</span></span></td>
  <td><span data-ttu-id="d3f5b-936">RepeatAll</span><span class="sxs-lookup"><span data-stu-id="d3f5b-936">RepeatAll</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8ef.png" alt="Calculator" /></td>
  <td><span data-ttu-id="d3f5b-937">E8EF</span><span class="sxs-lookup"><span data-stu-id="d3f5b-937">E8EF</span></span></td>
  <td><span data-ttu-id="d3f5b-938">Rechner</span><span class="sxs-lookup"><span data-stu-id="d3f5b-938">Calculator</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8f0.png" alt="Directions" /></td>
  <td><span data-ttu-id="d3f5b-939">E8F0</span><span class="sxs-lookup"><span data-stu-id="d3f5b-939">E8F0</span></span></td>
  <td><span data-ttu-id="d3f5b-940">Directions</span><span class="sxs-lookup"><span data-stu-id="d3f5b-940">Directions</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8f1.png" alt="Library" /></td>
  <td><span data-ttu-id="d3f5b-941">E8F1</span><span class="sxs-lookup"><span data-stu-id="d3f5b-941">E8F1</span></span></td>
  <td><span data-ttu-id="d3f5b-942">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="d3f5b-942">Library</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8f2.png" alt="ChatBubbles" /></td>
  <td><span data-ttu-id="d3f5b-943">E8F2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-943">E8F2</span></span></td>
  <td><span data-ttu-id="d3f5b-944">ChatBubbles</span><span class="sxs-lookup"><span data-stu-id="d3f5b-944">ChatBubbles</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8f3.png" alt="PostUpdate" /></td>
  <td><span data-ttu-id="d3f5b-945">E8F3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-945">E8F3</span></span></td>
  <td><span data-ttu-id="d3f5b-946">PostUpdate</span><span class="sxs-lookup"><span data-stu-id="d3f5b-946">PostUpdate</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8f4.png" alt="NewFolder" /></td>
  <td><span data-ttu-id="d3f5b-947">E8F4</span><span class="sxs-lookup"><span data-stu-id="d3f5b-947">E8F4</span></span></td>
  <td><span data-ttu-id="d3f5b-948">NewFolder</span><span class="sxs-lookup"><span data-stu-id="d3f5b-948">NewFolder</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8f5.png" alt="CalendarReply" /></td>
  <td><span data-ttu-id="d3f5b-949">E8F5</span><span class="sxs-lookup"><span data-stu-id="d3f5b-949">E8F5</span></span></td>
  <td><span data-ttu-id="d3f5b-950">CalendarReply</span><span class="sxs-lookup"><span data-stu-id="d3f5b-950">CalendarReply</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8f6.png" alt="UnsyncFolder" /></td>
  <td><span data-ttu-id="d3f5b-951">E8F6</span><span class="sxs-lookup"><span data-stu-id="d3f5b-951">E8F6</span></span></td>
  <td><span data-ttu-id="d3f5b-952">UnsyncFolder</span><span class="sxs-lookup"><span data-stu-id="d3f5b-952">UnsyncFolder</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8f7.png" alt="SyncFolder" /></td>
  <td><span data-ttu-id="d3f5b-953">E8F7</span><span class="sxs-lookup"><span data-stu-id="d3f5b-953">E8F7</span></span></td>
  <td><span data-ttu-id="d3f5b-954">SyncFolder</span><span class="sxs-lookup"><span data-stu-id="d3f5b-954">SyncFolder</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8f8.png" alt="BlockContact" /></td>
  <td><span data-ttu-id="d3f5b-955">E8F8</span><span class="sxs-lookup"><span data-stu-id="d3f5b-955">E8F8</span></span></td>
  <td><span data-ttu-id="d3f5b-956">BlockContact</span><span class="sxs-lookup"><span data-stu-id="d3f5b-956">BlockContact</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8f9.png" alt="SwitchApps" /></td>
  <td><span data-ttu-id="d3f5b-957">E8F9</span><span class="sxs-lookup"><span data-stu-id="d3f5b-957">E8F9</span></span></td>
  <td><span data-ttu-id="d3f5b-958">SwitchApps</span><span class="sxs-lookup"><span data-stu-id="d3f5b-958">SwitchApps</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8fa.png" alt="AddFriend" /></td>
  <td><span data-ttu-id="d3f5b-959">E8FA</span><span class="sxs-lookup"><span data-stu-id="d3f5b-959">E8FA</span></span></td>
  <td><span data-ttu-id="d3f5b-960">AddFriend</span><span class="sxs-lookup"><span data-stu-id="d3f5b-960">AddFriend</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8fb.png" alt="Accept" /></td>
  <td><span data-ttu-id="d3f5b-961">E8FB</span><span class="sxs-lookup"><span data-stu-id="d3f5b-961">E8FB</span></span></td>
  <td><span data-ttu-id="d3f5b-962">Akzeptieren</span><span class="sxs-lookup"><span data-stu-id="d3f5b-962">Accept</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8fc.png" alt="GoToStart" /></td>
  <td><span data-ttu-id="d3f5b-963">E8FC</span><span class="sxs-lookup"><span data-stu-id="d3f5b-963">E8FC</span></span></td>
  <td><span data-ttu-id="d3f5b-964">GoToStart</span><span class="sxs-lookup"><span data-stu-id="d3f5b-964">GoToStart</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8fd.png" alt="BulletedList" /></td>
  <td><span data-ttu-id="d3f5b-965">E8FD</span><span class="sxs-lookup"><span data-stu-id="d3f5b-965">E8FD</span></span></td>
  <td><span data-ttu-id="d3f5b-966">BulletedList</span><span class="sxs-lookup"><span data-stu-id="d3f5b-966">BulletedList</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8fe.png" alt="Scan" /></td>
  <td><span data-ttu-id="d3f5b-967">E8FE</span><span class="sxs-lookup"><span data-stu-id="d3f5b-967">E8FE</span></span></td>
  <td><span data-ttu-id="d3f5b-968">Scannen</span><span class="sxs-lookup"><span data-stu-id="d3f5b-968">Scan</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e8ff.png" alt="Preview" /></td>
  <td><span data-ttu-id="d3f5b-969">E8FF</span><span class="sxs-lookup"><span data-stu-id="d3f5b-969">E8FF</span></span></td>
  <td><span data-ttu-id="d3f5b-970">Preview</span><span class="sxs-lookup"><span data-stu-id="d3f5b-970">Preview</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e904.png" alt="ZeroBars" /></td>
  <td><span data-ttu-id="d3f5b-971">E904</span><span class="sxs-lookup"><span data-stu-id="d3f5b-971">E904</span></span></td>
  <td><span data-ttu-id="d3f5b-972">ZeroBars</span><span class="sxs-lookup"><span data-stu-id="d3f5b-972">ZeroBars</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e905.png" alt="OneBar" /></td>
  <td><span data-ttu-id="d3f5b-973">E905</span><span class="sxs-lookup"><span data-stu-id="d3f5b-973">E905</span></span></td>
  <td><span data-ttu-id="d3f5b-974">OneBar</span><span class="sxs-lookup"><span data-stu-id="d3f5b-974">OneBar</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e906.png" alt="TwoBars" /></td>
  <td><span data-ttu-id="d3f5b-975">E906</span><span class="sxs-lookup"><span data-stu-id="d3f5b-975">E906</span></span></td>
  <td><span data-ttu-id="d3f5b-976">TwoBars</span><span class="sxs-lookup"><span data-stu-id="d3f5b-976">TwoBars</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e907.png" alt="ThreeBars" /></td>
  <td><span data-ttu-id="d3f5b-977">E907</span><span class="sxs-lookup"><span data-stu-id="d3f5b-977">E907</span></span></td>
  <td><span data-ttu-id="d3f5b-978">ThreeBars</span><span class="sxs-lookup"><span data-stu-id="d3f5b-978">ThreeBars</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e908.png" alt="FourBars" /></td>
  <td><span data-ttu-id="d3f5b-979">E908</span><span class="sxs-lookup"><span data-stu-id="d3f5b-979">E908</span></span></td>
  <td><span data-ttu-id="d3f5b-980">FourBars</span><span class="sxs-lookup"><span data-stu-id="d3f5b-980">FourBars</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e909.png" alt="World" /></td>
  <td><span data-ttu-id="d3f5b-981">E909</span><span class="sxs-lookup"><span data-stu-id="d3f5b-981">E909</span></span></td>
  <td><span data-ttu-id="d3f5b-982">World</span><span class="sxs-lookup"><span data-stu-id="d3f5b-982">World</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e90a.png" alt="Comment" /></td>
  <td><span data-ttu-id="d3f5b-983">E90A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-983">E90A</span></span></td>
  <td><span data-ttu-id="d3f5b-984">Kommentar</span><span class="sxs-lookup"><span data-stu-id="d3f5b-984">Comment</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e90b.png" alt="MusicInfo" /></td>
  <td><span data-ttu-id="d3f5b-985">E90B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-985">E90B</span></span></td>
  <td><span data-ttu-id="d3f5b-986">MusicInfo</span><span class="sxs-lookup"><span data-stu-id="d3f5b-986">MusicInfo</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e90c.png" alt="DockLeft" /></td>
  <td><span data-ttu-id="d3f5b-987">E90C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-987">E90C</span></span></td>
  <td><span data-ttu-id="d3f5b-988">DockLeft</span><span class="sxs-lookup"><span data-stu-id="d3f5b-988">DockLeft</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e90d.png" alt="DockRight" /></td>
  <td><span data-ttu-id="d3f5b-989">E90D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-989">E90D</span></span></td>
  <td><span data-ttu-id="d3f5b-990">DockRight</span><span class="sxs-lookup"><span data-stu-id="d3f5b-990">DockRight</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e90e.png" alt="DockBottom" /></td>
  <td><span data-ttu-id="d3f5b-991">E90E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-991">E90E</span></span></td>
  <td><span data-ttu-id="d3f5b-992">DockBottom</span><span class="sxs-lookup"><span data-stu-id="d3f5b-992">DockBottom</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e90f.png" alt="Repair" /></td>
  <td><span data-ttu-id="d3f5b-993">E90F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-993">E90F</span></span></td>
  <td><span data-ttu-id="d3f5b-994">Repair</span><span class="sxs-lookup"><span data-stu-id="d3f5b-994">Repair</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e910.png" alt="Accounts" /></td>
  <td><span data-ttu-id="d3f5b-995">E910</span><span class="sxs-lookup"><span data-stu-id="d3f5b-995">E910</span></span></td>
  <td><span data-ttu-id="d3f5b-996">Konten</span><span class="sxs-lookup"><span data-stu-id="d3f5b-996">Accounts</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e911.png" alt="DullSound" /></td>
  <td><span data-ttu-id="d3f5b-997">E911</span><span class="sxs-lookup"><span data-stu-id="d3f5b-997">E911</span></span></td>
  <td><span data-ttu-id="d3f5b-998">DullSound</span><span class="sxs-lookup"><span data-stu-id="d3f5b-998">DullSound</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e912.png" alt="Manage" /></td>
  <td><span data-ttu-id="d3f5b-999">E912</span><span class="sxs-lookup"><span data-stu-id="d3f5b-999">E912</span></span></td>
  <td><span data-ttu-id="d3f5b-1000">Verwalten</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1000">Manage</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e913.png" alt="Street" /></td>
  <td><span data-ttu-id="d3f5b-1001">E913</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1001">E913</span></span></td>
  <td><span data-ttu-id="d3f5b-1002">Street</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1002">Street</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e914.png" alt="Printer3D" /></td>
  <td><span data-ttu-id="d3f5b-1003">E914</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1003">E914</span></span></td>
  <td><span data-ttu-id="d3f5b-1004">Printer3D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1004">Printer3D</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e915.png" alt="RadioBullet" /></td>
  <td><span data-ttu-id="d3f5b-1005">E915</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1005">E915</span></span></td>
  <td><span data-ttu-id="d3f5b-1006">RadioBullet</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1006">RadioBullet</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e916.png" alt="Stopwatch" /></td>
  <td><span data-ttu-id="d3f5b-1007">E916</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1007">E916</span></span></td>
  <td><span data-ttu-id="d3f5b-1008">Stopwatch</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1008">Stopwatch</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e91b.png" alt="Photo" /></td>
  <td><span data-ttu-id="d3f5b-1009">E91B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1009">E91B</span></span></td>
  <td><span data-ttu-id="d3f5b-1010">Foto</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1010">Photo</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e91c.png" alt="ActionCenter" /></td>
  <td><span data-ttu-id="d3f5b-1011">E91C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1011">E91C</span></span></td>
  <td><span data-ttu-id="d3f5b-1012">ActionCenter</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1012">ActionCenter</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e91f.png" alt="FullCircleMask" /></td>
  <td><span data-ttu-id="d3f5b-1013">E91F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1013">E91F</span></span></td>
  <td><span data-ttu-id="d3f5b-1014">FullCircleMask</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1014">FullCircleMask</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e921.png" alt="ChromeMinimize" /></td>
  <td><span data-ttu-id="d3f5b-1015">E921</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1015">E921</span></span></td>
  <td><span data-ttu-id="d3f5b-1016">ChromeMinimize</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1016">ChromeMinimize</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e922.png" alt="ChromeMaximize" /></td>
  <td><span data-ttu-id="d3f5b-1017">E922</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1017">E922</span></span></td>
  <td><span data-ttu-id="d3f5b-1018">ChromeMaximize</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1018">ChromeMaximize</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e923.png" alt="ChromeRestore" /></td>
  <td><span data-ttu-id="d3f5b-1019">E923</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1019">E923</span></span></td>
  <td><span data-ttu-id="d3f5b-1020">ChromeRestore</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1020">ChromeRestore</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e924.png" alt="Annotation" /></td>
  <td><span data-ttu-id="d3f5b-1021">E924</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1021">E924</span></span></td>
  <td><span data-ttu-id="d3f5b-1022">Annotation</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1022">Annotation</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e925.png" alt="BackSpaceQWERTYSm" /></td>
  <td><span data-ttu-id="d3f5b-1023">E925</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1023">E925</span></span></td>
  <td><span data-ttu-id="d3f5b-1024">BackSpaceQWERTYSm</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1024">BackSpaceQWERTYSm</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e926.png" alt="BackSpaceQWERTYMd" /></td>
  <td><span data-ttu-id="d3f5b-1025">E926</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1025">E926</span></span></td>
  <td><span data-ttu-id="d3f5b-1026">BackSpaceQWERTYMd</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1026">BackSpaceQWERTYMd</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e927.png" alt="Swipe" /></td>
  <td><span data-ttu-id="d3f5b-1027">E927</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1027">E927</span></span></td>
  <td><span data-ttu-id="d3f5b-1028">Wischen</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1028">Swipe</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e928.png" alt="Fingerprint" /></td>
  <td><span data-ttu-id="d3f5b-1029">E928</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1029">E928</span></span></td>
  <td><span data-ttu-id="d3f5b-1030">Fingerprint</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1030">Fingerprint</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e929.png" alt="Handwriting" /></td>
  <td><span data-ttu-id="d3f5b-1031">E929</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1031">E929</span></span></td>
  <td><span data-ttu-id="d3f5b-1032">Handwriting</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1032">Handwriting</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e92c.png" alt="ChromeBackToWindow" /></td>
  <td><span data-ttu-id="d3f5b-1033">E92C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1033">E92C</span></span></td>
  <td><span data-ttu-id="d3f5b-1034">ChromeBackToWindow</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1034">ChromeBackToWindow</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e92d.png" alt="ChromeFullScreen" /></td>
  <td><span data-ttu-id="d3f5b-1035">E92D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1035">E92D</span></span></td>
  <td><span data-ttu-id="d3f5b-1036">ChromeFullScreen</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1036">ChromeFullScreen</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e92e.png" alt="KeyboardStandard" /></td>
  <td><span data-ttu-id="d3f5b-1037">E92E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1037">E92E</span></span></td>
  <td><span data-ttu-id="d3f5b-1038">KeyboardStandard</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1038">KeyboardStandard</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e92f.png" alt="KeyboardDismiss" /></td>
  <td><span data-ttu-id="d3f5b-1039">E92F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1039">E92F</span></span></td>
  <td><span data-ttu-id="d3f5b-1040">KeyboardDismiss</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1040">KeyboardDismiss</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e930.png" alt="Completed" /></td>
  <td><span data-ttu-id="d3f5b-1041">E930</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1041">E930</span></span></td>
  <td><span data-ttu-id="d3f5b-1042">Completed</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1042">Completed</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e931.png" alt="ChromeAnnotate" /></td>
  <td><span data-ttu-id="d3f5b-1043">E931</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1043">E931</span></span></td>
  <td><span data-ttu-id="d3f5b-1044">ChromeAnnotate</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1044">ChromeAnnotate</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e932.png" alt="Label" /></td>
  <td><span data-ttu-id="d3f5b-1045">E932</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1045">E932</span></span></td>
  <td><span data-ttu-id="d3f5b-1046">Label</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1046">Label</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e933.png" alt="IBeam" /></td>
  <td><span data-ttu-id="d3f5b-1047">E933</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1047">E933</span></span></td>
  <td><span data-ttu-id="d3f5b-1048">IBeam</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1048">IBeam</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e934.png" alt="IBeamOutline" /></td>
  <td><span data-ttu-id="d3f5b-1049">E934</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1049">E934</span></span></td>
  <td><span data-ttu-id="d3f5b-1050">IBeamOutline</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1050">IBeamOutline</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e935.png" alt="FlickDown" /></td>
  <td><span data-ttu-id="d3f5b-1051">E935</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1051">E935</span></span></td>
  <td><span data-ttu-id="d3f5b-1052">FlickDown</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1052">FlickDown</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e936.png" alt="FlickUp" /></td>
  <td><span data-ttu-id="d3f5b-1053">E936</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1053">E936</span></span></td>
  <td><span data-ttu-id="d3f5b-1054">FlickUp</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1054">FlickUp</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e937.png" alt="FlickLeft" /></td>
  <td><span data-ttu-id="d3f5b-1055">E937</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1055">E937</span></span></td>
  <td><span data-ttu-id="d3f5b-1056">FlickLeft</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1056">FlickLeft</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e938.png" alt="FlickRight" /></td>
  <td><span data-ttu-id="d3f5b-1057">E938</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1057">E938</span></span></td>
  <td><span data-ttu-id="d3f5b-1058">FlickRight</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1058">FlickRight</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e939.png" alt="FeedbackApp" /></td>
  <td><span data-ttu-id="d3f5b-1059">E939</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1059">E939</span></span></td>
  <td><span data-ttu-id="d3f5b-1060">FeedbackApp</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1060">FeedbackApp</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e93c.png" alt="MusicAlbum" /></td>
  <td><span data-ttu-id="d3f5b-1061">E93C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1061">E93C</span></span></td>
  <td><span data-ttu-id="d3f5b-1062">MusicAlbum</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1062">MusicAlbum</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e93e.png" alt="Streaming" /></td>
  <td><span data-ttu-id="d3f5b-1063">E93E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1063">E93E</span></span></td>
  <td><span data-ttu-id="d3f5b-1064">Streaming</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1064">Streaming</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e943.png" alt="Code" /></td>
  <td><span data-ttu-id="d3f5b-1065">E943</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1065">E943</span></span></td>
  <td><span data-ttu-id="d3f5b-1066">Code</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1066">Code</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e944.png" alt="ReturnToWindow" /></td>
  <td><span data-ttu-id="d3f5b-1067">E944</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1067">E944</span></span></td>
  <td><span data-ttu-id="d3f5b-1068">ReturnToWindow</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1068">ReturnToWindow</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e945.png" alt="LightningBolt" /></td>
  <td><span data-ttu-id="d3f5b-1069">E945</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1069">E945</span></span></td>
  <td><span data-ttu-id="d3f5b-1070">LightningBolt</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1070">LightningBolt</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e946.png" alt="Info" /></td>
  <td><span data-ttu-id="d3f5b-1071">E946</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1071">E946</span></span></td>
  <td><span data-ttu-id="d3f5b-1072">Info</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1072">Info</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e947.png" alt="CalculatorMultiply" /></td>
  <td><span data-ttu-id="d3f5b-1073">E947</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1073">E947</span></span></td>
  <td><span data-ttu-id="d3f5b-1074">CalculatorMultiply</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1074">CalculatorMultiply</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e948.png" alt="CalculatorAddition" /></td>
  <td><span data-ttu-id="d3f5b-1075">E948</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1075">E948</span></span></td>
  <td><span data-ttu-id="d3f5b-1076">CalculatorAddition</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1076">CalculatorAddition</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e949.png" alt="CalculatorSubtract" /></td>
  <td><span data-ttu-id="d3f5b-1077">E949</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1077">E949</span></span></td>
  <td><span data-ttu-id="d3f5b-1078">CalculatorSubtract</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1078">CalculatorSubtract</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e94a.png" alt="CalculatorDivide" /></td>
  <td><span data-ttu-id="d3f5b-1079">E94A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1079">E94A</span></span></td>
  <td><span data-ttu-id="d3f5b-1080">CalculatorDivide</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1080">CalculatorDivide</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e94b.png" alt="CalculatorSquareroot" /></td>
  <td><span data-ttu-id="d3f5b-1081">E94B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1081">E94B</span></span></td>
  <td><span data-ttu-id="d3f5b-1082">CalculatorSquareroot</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1082">CalculatorSquareroot</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e94c.png" alt="CalculatorPercentage" /></td>
  <td><span data-ttu-id="d3f5b-1083">E94C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1083">E94C</span></span></td>
  <td><span data-ttu-id="d3f5b-1084">CalculatorPercentage</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1084">CalculatorPercentage</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e94d.png" alt="CalculatorNegate" /></td>
  <td><span data-ttu-id="d3f5b-1085">E94D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1085">E94D</span></span></td>
  <td><span data-ttu-id="d3f5b-1086">CalculatorNegate</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1086">CalculatorNegate</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e94e.png" alt="CalculatorEqualTo" /></td>
  <td><span data-ttu-id="d3f5b-1087">E94E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1087">E94E</span></span></td>
  <td><span data-ttu-id="d3f5b-1088">CalculatorEqualTo</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1088">CalculatorEqualTo</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e94f.png" alt="CalculatorBackspace" /></td>
  <td><span data-ttu-id="d3f5b-1089">E94F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1089">E94F</span></span></td>
  <td><span data-ttu-id="d3f5b-1090">CalculatorBackspace</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1090">CalculatorBackspace</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e950.png" alt="Component" /></td>
  <td><span data-ttu-id="d3f5b-1091">E950</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1091">E950</span></span></td>
  <td><span data-ttu-id="d3f5b-1092">Komponente</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1092">Component</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e951.png" alt="DMC" /></td>
  <td><span data-ttu-id="d3f5b-1093">E951</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1093">E951</span></span></td>
  <td><span data-ttu-id="d3f5b-1094">DMC</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1094">DMC</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e952.png" alt="Dock" /></td>
  <td><span data-ttu-id="d3f5b-1095">E952</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1095">E952</span></span></td>
  <td><span data-ttu-id="d3f5b-1096">Dock</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1096">Dock</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e953.png" alt="MultimediaDMS" /></td>
  <td><span data-ttu-id="d3f5b-1097">E953</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1097">E953</span></span></td>
  <td><span data-ttu-id="d3f5b-1098">MultimediaDMS</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1098">MultimediaDMS</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e954.png" alt="MultimediaDVR" /></td>
  <td><span data-ttu-id="d3f5b-1099">E954</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1099">E954</span></span></td>
  <td><span data-ttu-id="d3f5b-1100">MultimediaDVR</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1100">MultimediaDVR</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e955.png" alt="MultimediaPMP" /></td>
  <td><span data-ttu-id="d3f5b-1101">E955</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1101">E955</span></span></td>
  <td><span data-ttu-id="d3f5b-1102">MultimediaPMP</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1102">MultimediaPMP</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e956.png" alt="PrintfaxPrinterFile" /></td>
  <td><span data-ttu-id="d3f5b-1103">E956</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1103">E956</span></span></td>
  <td><span data-ttu-id="d3f5b-1104">PrintfaxPrinterFile</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1104">PrintfaxPrinterFile</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e957.png" alt="Sensor" /></td>
  <td><span data-ttu-id="d3f5b-1105">E957</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1105">E957</span></span></td>
  <td><span data-ttu-id="d3f5b-1106">Sensor</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1106">Sensor</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e958.png" alt="StorageOptical" /></td>
  <td><span data-ttu-id="d3f5b-1107">E958</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1107">E958</span></span></td>
  <td><span data-ttu-id="d3f5b-1108">StorageOptical</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1108">StorageOptical</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e95a.png" alt="Communications" /></td>
  <td><span data-ttu-id="d3f5b-1109">E95A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1109">E95A</span></span></td>
  <td><span data-ttu-id="d3f5b-1110">Communications</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1110">Communications</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e95b.png" alt="Headset" /></td>
  <td><span data-ttu-id="d3f5b-1111">E95B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1111">E95B</span></span></td>
  <td><span data-ttu-id="d3f5b-1112">Headset</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1112">Headset</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e95d.png" alt="Projector" /></td>
  <td><span data-ttu-id="d3f5b-1113">E95D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1113">E95D</span></span></td>
  <td><span data-ttu-id="d3f5b-1114">Projector</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1114">Projector</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e95e.png" alt="Health" /></td>
  <td><span data-ttu-id="d3f5b-1115">E95E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1115">E95E</span></span></td>
  <td><span data-ttu-id="d3f5b-1116">Integrität</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1116">Health</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e960.png" alt="Webcam2" /></td>
  <td><span data-ttu-id="d3f5b-1117">E960</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1117">E960</span></span></td>
  <td><span data-ttu-id="d3f5b-1118">Webcam2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1118">Webcam2</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e961.png" alt="Input" /></td>
  <td><span data-ttu-id="d3f5b-1119">E961</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1119">E961</span></span></td>
  <td><span data-ttu-id="d3f5b-1120">Eingabeart</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1120">Input</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e962.png" alt="Mouse" /></td>
  <td><span data-ttu-id="d3f5b-1121">E962</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1121">E962</span></span></td>
  <td><span data-ttu-id="d3f5b-1122">Maus</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1122">Mouse</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e963.png" alt="Smartcard" /></td>
  <td><span data-ttu-id="d3f5b-1123">E963</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1123">E963</span></span></td>
  <td><span data-ttu-id="d3f5b-1124">Smartcard</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1124">Smartcard</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e964.png" alt="SmartcardVirtual" /></td>
  <td><span data-ttu-id="d3f5b-1125">E964</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1125">E964</span></span></td>
  <td><span data-ttu-id="d3f5b-1126">SmartcardVirtual</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1126">SmartcardVirtual</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e965.png" alt="MediaStorageTower" /></td>
  <td><span data-ttu-id="d3f5b-1127">E965</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1127">E965</span></span></td>
  <td><span data-ttu-id="d3f5b-1128">MediaStorageTower</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1128">MediaStorageTower</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e966.png" alt="ReturnKeySm" /></td>
  <td><span data-ttu-id="d3f5b-1129">E966</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1129">E966</span></span></td>
  <td><span data-ttu-id="d3f5b-1130">ReturnKeySm</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1130">ReturnKeySm</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e967.png" alt="GameConsole" /></td>
  <td><span data-ttu-id="d3f5b-1131">E967</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1131">E967</span></span></td>
  <td><span data-ttu-id="d3f5b-1132">GameConsole</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1132">GameConsole</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e968.png" alt="Network" /></td>
  <td><span data-ttu-id="d3f5b-1133">E968</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1133">E968</span></span></td>
  <td><span data-ttu-id="d3f5b-1134">Netzwerk</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1134">Network</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e969.png" alt="StorageNetworkWireless" /></td>
  <td><span data-ttu-id="d3f5b-1135">E969</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1135">E969</span></span></td>
  <td><span data-ttu-id="d3f5b-1136">StorageNetworkWireless</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1136">StorageNetworkWireless</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e96a.png" alt="StorageTape" /></td>
  <td><span data-ttu-id="d3f5b-1137">E96A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1137">E96A</span></span></td>
  <td><span data-ttu-id="d3f5b-1138">StorageTape</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1138">StorageTape</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e96d.png" alt="ChevronUpSmall" /></td>
  <td><span data-ttu-id="d3f5b-1139">E96D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1139">E96D</span></span></td>
  <td><span data-ttu-id="d3f5b-1140">ChevronUpSmall</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1140">ChevronUpSmall</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e96e.png" alt="ChevronDownSmall" /></td>
  <td><span data-ttu-id="d3f5b-1141">E96E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1141">E96E</span></span></td>
  <td><span data-ttu-id="d3f5b-1142">ChevronDownSmall</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1142">ChevronDownSmall</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e96f.png" alt="ChevronLeftSmall" /></td>
  <td><span data-ttu-id="d3f5b-1143">E96F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1143">E96F</span></span></td>
  <td><span data-ttu-id="d3f5b-1144">ChevronLeftSmall</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1144">ChevronLeftSmall</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e970.png" alt="ChevronRightSmall" /></td>
  <td><span data-ttu-id="d3f5b-1145">E970</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1145">E970</span></span></td>
  <td><span data-ttu-id="d3f5b-1146">ChevronRightSmall</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1146">ChevronRightSmall</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e971.png" alt="ChevronUpMed" /></td>
  <td><span data-ttu-id="d3f5b-1147">E971</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1147">E971</span></span></td>
  <td><span data-ttu-id="d3f5b-1148">ChevronUpMed</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1148">ChevronUpMed</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e972.png" alt="ChevronDownMed" /></td>
  <td><span data-ttu-id="d3f5b-1149">E972</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1149">E972</span></span></td>
  <td><span data-ttu-id="d3f5b-1150">ChevronDownMed</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1150">ChevronDownMed</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e973.png" alt="ChevronLeftMed" /></td>
  <td><span data-ttu-id="d3f5b-1151">E973</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1151">E973</span></span></td>
  <td><span data-ttu-id="d3f5b-1152">ChevronLeftMed</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1152">ChevronLeftMed</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e974.png" alt="ChevronRightMed" /></td>
  <td><span data-ttu-id="d3f5b-1153">E974</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1153">E974</span></span></td>
  <td><span data-ttu-id="d3f5b-1154">ChevronRightMed</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1154">ChevronRightMed</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e975.png" alt="Devices2" /></td>
  <td><span data-ttu-id="d3f5b-1155">E975</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1155">E975</span></span></td>
  <td><span data-ttu-id="d3f5b-1156">Devices2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1156">Devices2</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e976.png" alt="ExpandTile" /></td>
  <td><span data-ttu-id="d3f5b-1157">E976</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1157">E976</span></span></td>
  <td><span data-ttu-id="d3f5b-1158">ExpandTile</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1158">ExpandTile</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e977.png" alt="PC1" /></td>
  <td><span data-ttu-id="d3f5b-1159">E977</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1159">E977</span></span></td>
  <td><span data-ttu-id="d3f5b-1160">PC1</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1160">PC1</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e978.png" alt="PresenceChicklet" /></td>
  <td><span data-ttu-id="d3f5b-1161">E978</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1161">E978</span></span></td>
  <td><span data-ttu-id="d3f5b-1162">PresenceChicklet</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1162">PresenceChicklet</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e979.png" alt="PresenceChickletVideo" /></td>
  <td><span data-ttu-id="d3f5b-1163">E979</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1163">E979</span></span></td>
  <td><span data-ttu-id="d3f5b-1164">PresenceChickletVideo</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1164">PresenceChickletVideo</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e97a.png" alt="Reply" /></td>
  <td><span data-ttu-id="d3f5b-1165">E97A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1165">E97A</span></span></td>
  <td><span data-ttu-id="d3f5b-1166">Antworten</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1166">Reply</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e97b.png" alt="SetTile" /></td>
  <td><span data-ttu-id="d3f5b-1167">E97B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1167">E97B</span></span></td>
  <td><span data-ttu-id="d3f5b-1168">SetTile</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1168">SetTile</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e97c.png" alt="Type" /></td>
  <td><span data-ttu-id="d3f5b-1169">E97C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1169">E97C</span></span></td>
  <td><span data-ttu-id="d3f5b-1170">Eingabe</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1170">Type</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e97d.png" alt="Korean" /></td>
  <td><span data-ttu-id="d3f5b-1171">E97D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1171">E97D</span></span></td>
  <td><span data-ttu-id="d3f5b-1172">Koreanisch</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1172">Korean</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e97e.png" alt="HalfAlpha" /></td>
  <td><span data-ttu-id="d3f5b-1173">E97E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1173">E97E</span></span></td>
  <td><span data-ttu-id="d3f5b-1174">HalfAlpha</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1174">HalfAlpha</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e97f.png" alt="FullAlpha" /></td>
  <td><span data-ttu-id="d3f5b-1175">E97F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1175">E97F</span></span></td>
  <td><span data-ttu-id="d3f5b-1176">FullAlpha</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1176">FullAlpha</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e980.png" alt="Key12On" /></td>
  <td><span data-ttu-id="d3f5b-1177">E980</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1177">E980</span></span></td>
  <td><span data-ttu-id="d3f5b-1178">Key12On</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1178">Key12On</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e981.png" alt="ChineseChangjie" /></td>
  <td><span data-ttu-id="d3f5b-1179">E981</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1179">E981</span></span></td>
  <td><span data-ttu-id="d3f5b-1180">ChineseChangjie</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1180">ChineseChangjie</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e982.png" alt="QWERTYOn" /></td>
  <td><span data-ttu-id="d3f5b-1181">E982</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1181">E982</span></span></td>
  <td><span data-ttu-id="d3f5b-1182">QWERTYOn</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1182">QWERTYOn</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e983.png" alt="QWERTYOff" /></td>
  <td><span data-ttu-id="d3f5b-1183">E983</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1183">E983</span></span></td>
  <td><span data-ttu-id="d3f5b-1184">QWERTYOff</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1184">QWERTYOff</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e984.png" alt="ChineseQuick" /></td>
  <td><span data-ttu-id="d3f5b-1185">E984</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1185">E984</span></span></td>
  <td><span data-ttu-id="d3f5b-1186">ChineseQuick</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1186">ChineseQuick</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e985.png" alt="Japanese" /></td>
  <td><span data-ttu-id="d3f5b-1187">E985</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1187">E985</span></span></td>
  <td><span data-ttu-id="d3f5b-1188">Japanisch</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1188">Japanese</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e986.png" alt="FullHiragana" /></td>
  <td><span data-ttu-id="d3f5b-1189">E986</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1189">E986</span></span></td>
  <td><span data-ttu-id="d3f5b-1190">FullHiragana</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1190">FullHiragana</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e987.png" alt="FullKatakana" /></td>
  <td><span data-ttu-id="d3f5b-1191">E987</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1191">E987</span></span></td>
  <td><span data-ttu-id="d3f5b-1192">FullKatakana</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1192">FullKatakana</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e988.png" alt="HalfKatakana" /></td>
  <td><span data-ttu-id="d3f5b-1193">E988</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1193">E988</span></span></td>
  <td><span data-ttu-id="d3f5b-1194">HalfKatakana</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1194">HalfKatakana</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e989.png" alt="ChineseBoPoMoFo" /></td>
  <td><span data-ttu-id="d3f5b-1195">E989</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1195">E989</span></span></td>
  <td><span data-ttu-id="d3f5b-1196">ChineseBoPoMoFo</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1196">ChineseBoPoMoFo</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e98a.png" alt="ChinesePinyin" /></td>
  <td><span data-ttu-id="d3f5b-1197">E98A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1197">E98A</span></span></td>
  <td><span data-ttu-id="d3f5b-1198">ChinesePinyin</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1198">ChinesePinyin</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e98f.png" alt="ConstructionCone" /></td>
  <td><span data-ttu-id="d3f5b-1199">E98F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1199">E98F</span></span></td>
  <td><span data-ttu-id="d3f5b-1200">ConstructionCone</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1200">ConstructionCone</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e990.png" alt="XboxOneConsole" /></td>
  <td><span data-ttu-id="d3f5b-1201">E990</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1201">E990</span></span></td>
  <td><span data-ttu-id="d3f5b-1202">XboxOneConsole</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1202">XboxOneConsole</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e992.png" alt="Volume0" /></td>
  <td><span data-ttu-id="d3f5b-1203">E992</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1203">E992</span></span></td>
  <td><span data-ttu-id="d3f5b-1204">Volume0</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1204">Volume0</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e993.png" alt="Volume1" /></td>
  <td><span data-ttu-id="d3f5b-1205">E993</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1205">E993</span></span></td>
  <td><span data-ttu-id="d3f5b-1206">Volume1</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1206">Volume1</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e994.png" alt="Volume2" /></td>
  <td><span data-ttu-id="d3f5b-1207">E994</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1207">E994</span></span></td>
  <td><span data-ttu-id="d3f5b-1208">Volume2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1208">Volume2</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e995.png" alt="Volume3" /></td>
  <td><span data-ttu-id="d3f5b-1209">E995</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1209">E995</span></span></td>
  <td><span data-ttu-id="d3f5b-1210">Volume3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1210">Volume3</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e996.png" alt="BatteryUnknown" /></td>
  <td><span data-ttu-id="d3f5b-1211">E996</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1211">E996</span></span></td>
  <td><span data-ttu-id="d3f5b-1212">BatteryUnknown</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1212">BatteryUnknown</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e998.png" alt="WifiAttentionOverlay" /></td>
  <td><span data-ttu-id="d3f5b-1213">E998</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1213">E998</span></span></td>
  <td><span data-ttu-id="d3f5b-1214">WifiAttentionOverlay</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1214">WifiAttentionOverlay</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e99a.png" alt="Robot" /></td>
  <td><span data-ttu-id="d3f5b-1215">E99A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1215">E99A</span></span></td>
  <td><span data-ttu-id="d3f5b-1216">Robot</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1216">Robot</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e9a1.png" alt="TapAndSend" /></td>
  <td><span data-ttu-id="d3f5b-1217">E9A1</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1217">E9A1</span></span></td>
  <td><span data-ttu-id="d3f5b-1218">TapAndSend</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1218">TapAndSend</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e9a8.png" alt="PasswordKeyShow" /></td>
  <td><span data-ttu-id="d3f5b-1219">E9A8</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1219">E9A8</span></span></td>
  <td><span data-ttu-id="d3f5b-1220">PasswordKeyShow</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1220">PasswordKeyShow</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e9a9.png" alt="PasswordKeyHide" /></td>
  <td><span data-ttu-id="d3f5b-1221">E9A9</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1221">E9A9</span></span></td>
  <td><span data-ttu-id="d3f5b-1222">PasswordKeyHide</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1222">PasswordKeyHide</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e9aa.png" alt="BidiLtr" /></td>
  <td><span data-ttu-id="d3f5b-1223">E9AA</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1223">E9AA</span></span></td>
  <td><span data-ttu-id="d3f5b-1224">BidiLtr</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1224">BidiLtr</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e9ab.png" alt="BidiRtl" /></td>
  <td><span data-ttu-id="d3f5b-1225">E9AB</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1225">E9AB</span></span></td>
  <td><span data-ttu-id="d3f5b-1226">BidiRtl</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1226">BidiRtl</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e9ac.png" alt="ForwardSm" /></td>
  <td><span data-ttu-id="d3f5b-1227">E9AC</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1227">E9AC</span></span></td>
  <td><span data-ttu-id="d3f5b-1228">ForwardSm</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1228">ForwardSm</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e9ad.png" alt="CommaKey" /></td>
  <td><span data-ttu-id="d3f5b-1229">E9AD</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1229">E9AD</span></span></td>
  <td><span data-ttu-id="d3f5b-1230">CommaKey</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1230">CommaKey</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e9ae.png" alt="DashKey" /></td>
  <td><span data-ttu-id="d3f5b-1231">E9AE</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1231">E9AE</span></span></td>
  <td><span data-ttu-id="d3f5b-1232">DashKey</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1232">DashKey</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e9af.png" alt="DullSoundKey" /></td>
  <td><span data-ttu-id="d3f5b-1233">E9AF</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1233">E9AF</span></span></td>
  <td><span data-ttu-id="d3f5b-1234">DullSoundKey</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1234">DullSoundKey</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e9b0.png" alt="HalfDullSound" /></td>
  <td><span data-ttu-id="d3f5b-1235">E9B0</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1235">E9B0</span></span></td>
  <td><span data-ttu-id="d3f5b-1236">HalfDullSound</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1236">HalfDullSound</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e9b1.png" alt="RightDoubleQuote" /></td>
  <td><span data-ttu-id="d3f5b-1237">E9B1</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1237">E9B1</span></span></td>
  <td><span data-ttu-id="d3f5b-1238">RightDoubleQuote</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1238">RightDoubleQuote</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e9b2.png" alt="LeftDoubleQuote" /></td>
  <td><span data-ttu-id="d3f5b-1239">E9B2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1239">E9B2</span></span></td>
  <td><span data-ttu-id="d3f5b-1240">LeftDoubleQuote</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1240">LeftDoubleQuote</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e9b3.png" alt="PuncKeyRightBottom" /></td>
  <td><span data-ttu-id="d3f5b-1241">E9B3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1241">E9B3</span></span></td>
  <td><span data-ttu-id="d3f5b-1242">PuncKeyRightBottom</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1242">PuncKeyRightBottom</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e9b4.png" alt="PuncKey1" /></td>
  <td><span data-ttu-id="d3f5b-1243">E9B4</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1243">E9B4</span></span></td>
  <td><span data-ttu-id="d3f5b-1244">PuncKey1</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1244">PuncKey1</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e9b5.png" alt="PuncKey2" /></td>
  <td><span data-ttu-id="d3f5b-1245">E9B5</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1245">E9B5</span></span></td>
  <td><span data-ttu-id="d3f5b-1246">PuncKey2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1246">PuncKey2</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e9b6.png" alt="PuncKey3" /></td>
  <td><span data-ttu-id="d3f5b-1247">E9B6</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1247">E9B6</span></span></td>
  <td><span data-ttu-id="d3f5b-1248">PuncKey3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1248">PuncKey3</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e9b7.png" alt="PuncKey4" /></td>
  <td><span data-ttu-id="d3f5b-1249">E9B7</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1249">E9B7</span></span></td>
  <td><span data-ttu-id="d3f5b-1250">PuncKey4</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1250">PuncKey4</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e9b8.png" alt="PuncKey5" /></td>
  <td><span data-ttu-id="d3f5b-1251">E9B8</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1251">E9B8</span></span></td>
  <td><span data-ttu-id="d3f5b-1252">PuncKey5</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1252">PuncKey5</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e9b9.png" alt="PuncKey6" /></td>
  <td><span data-ttu-id="d3f5b-1253">E9B9</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1253">E9B9</span></span></td>
  <td><span data-ttu-id="d3f5b-1254">PuncKey6</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1254">PuncKey6</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e9ba.png" alt="PuncKey9" /></td>
  <td><span data-ttu-id="d3f5b-1255">E9BA</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1255">E9BA</span></span></td>
  <td><span data-ttu-id="d3f5b-1256">PuncKey9</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1256">PuncKey9</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e9bb.png" alt="PuncKey7" /></td>
  <td><span data-ttu-id="d3f5b-1257">E9BB</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1257">E9BB</span></span></td>
  <td><span data-ttu-id="d3f5b-1258">PuncKey7</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1258">PuncKey7</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e9bc.png" alt="PuncKey8" /></td>
  <td><span data-ttu-id="d3f5b-1259">E9BC</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1259">E9BC</span></span></td>
  <td><span data-ttu-id="d3f5b-1260">PuncKey8</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1260">PuncKey8</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e9ca.png" alt="Frigid" /></td>
  <td><span data-ttu-id="d3f5b-1261">E9CA</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1261">E9CA</span></span></td>
  <td><span data-ttu-id="d3f5b-1262">Frigid</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1262">Frigid</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e9d9.png" alt="Diagnostic" /></td>
  <td><span data-ttu-id="d3f5b-1263">E9D9</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1263">E9D9</span></span></td>
  <td><span data-ttu-id="d3f5b-1264">Diagnostic</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1264">Diagnostic</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/e9f3.png" alt="Process" /></td>
  <td><span data-ttu-id="d3f5b-1265">E9F3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1265">E9F3</span></span></td>
  <td><span data-ttu-id="d3f5b-1266">Verarbeiten</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1266">Process</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea14.png" alt="DisconnectDisplay" /></td>
  <td><span data-ttu-id="d3f5b-1267">EA14</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1267">EA14</span></span></td>
  <td><span data-ttu-id="d3f5b-1268">DisconnectDisplay</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1268">DisconnectDisplay</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea1f.png" alt="Info2" /></td>
  <td><span data-ttu-id="d3f5b-1269">EA1F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1269">EA1F</span></span></td>
  <td><span data-ttu-id="d3f5b-1270">Info2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1270">Info2</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea21.png" alt="ActionCenterAsterisk" /></td>
  <td><span data-ttu-id="d3f5b-1271">EA21</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1271">EA21</span></span></td>
  <td><span data-ttu-id="d3f5b-1272">ActionCenterAsterisk</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1272">ActionCenterAsterisk</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea24.png" alt="Beta" /></td>
  <td><span data-ttu-id="d3f5b-1273">EA24</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1273">EA24</span></span></td>
  <td><span data-ttu-id="d3f5b-1274">Beta</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1274">Beta</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea35.png" alt="SaveCopy" /></td>
  <td><span data-ttu-id="d3f5b-1275">EA35</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1275">EA35</span></span></td>
  <td><span data-ttu-id="d3f5b-1276">SaveCopy</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1276">SaveCopy</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea37.png" alt="List" /></td>
  <td><span data-ttu-id="d3f5b-1277">EA37</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1277">EA37</span></span></td>
  <td><span data-ttu-id="d3f5b-1278">Liste</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1278">List</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea38.png" alt="Asterisk" /></td>
  <td><span data-ttu-id="d3f5b-1279">EA38</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1279">EA38</span></span></td>
  <td><span data-ttu-id="d3f5b-1280">Asterisk</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1280">Asterisk</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea39.png" alt="ErrorBadge" /></td>
  <td><span data-ttu-id="d3f5b-1281">EA39</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1281">EA39</span></span></td>
  <td><span data-ttu-id="d3f5b-1282">ErrorBadge</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1282">ErrorBadge</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea3a.png" alt="CircleRing" /></td>
  <td><span data-ttu-id="d3f5b-1283">EA3A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1283">EA3A</span></span></td>
  <td><span data-ttu-id="d3f5b-1284">CircleRing</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1284">CircleRing</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea3b.png" alt="CircleFill" /></td>
  <td><span data-ttu-id="d3f5b-1285">EA3B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1285">EA3B</span></span></td>
  <td><span data-ttu-id="d3f5b-1286">CircleFill</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1286">CircleFill</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea40.png" alt="AllAppsMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1287">EA40</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1287">EA40</span></span></td>
  <td><span data-ttu-id="d3f5b-1288">AllAppsMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1288">AllAppsMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea41.png" alt="BookmarksMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1289">EA41</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1289">EA41</span></span></td>
  <td><span data-ttu-id="d3f5b-1290">BookmarksMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1290">BookmarksMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea42.png" alt="BulletedListMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1291">EA42</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1291">EA42</span></span></td>
  <td><span data-ttu-id="d3f5b-1292">BulletedListMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1292">BulletedListMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea43.png" alt="CallForwardInternationalMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1293">EA43</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1293">EA43</span></span></td>
  <td><span data-ttu-id="d3f5b-1294">CallForwardInternationalMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1294">CallForwardInternationalMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea44.png" alt="CallForwardRoamingMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1295">EA44</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1295">EA44</span></span></td>
  <td><span data-ttu-id="d3f5b-1296">CallForwardRoamingMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1296">CallForwardRoamingMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea47.png" alt="ChromeBackMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1297">EA47</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1297">EA47</span></span></td>
  <td><span data-ttu-id="d3f5b-1298">ChromeBackMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1298">ChromeBackMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea48.png" alt="ClearSelectionMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1299">EA48</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1299">EA48</span></span></td>
  <td><span data-ttu-id="d3f5b-1300">ClearSelectionMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1300">ClearSelectionMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea49.png" alt="ClosePaneMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1301">EA49</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1301">EA49</span></span></td>
  <td><span data-ttu-id="d3f5b-1302">ClosePaneMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1302">ClosePaneMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea4a.png" alt="ContactInfoMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1303">EA4A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1303">EA4A</span></span></td>
  <td><span data-ttu-id="d3f5b-1304">ContactInfoMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1304">ContactInfoMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea4b.png" alt="DockRightMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1305">EA4B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1305">EA4B</span></span></td>
  <td><span data-ttu-id="d3f5b-1306">DockRightMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1306">DockRightMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea4c.png" alt="DockLeftMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1307">EA4C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1307">EA4C</span></span></td>
  <td><span data-ttu-id="d3f5b-1308">DockLeftMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1308">DockLeftMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea4e.png" alt="ExpandTileMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1309">EA4E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1309">EA4E</span></span></td>
  <td><span data-ttu-id="d3f5b-1310">ExpandTileMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1310">ExpandTileMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea4f.png" alt="GoMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1311">EA4F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1311">EA4F</span></span></td>
  <td><span data-ttu-id="d3f5b-1312">GoMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1312">GoMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea50.png" alt="GripperResizeMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1313">EA50</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1313">EA50</span></span></td>
  <td><span data-ttu-id="d3f5b-1314">GripperResizeMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1314">GripperResizeMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea51.png" alt="HelpMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1315">EA51</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1315">EA51</span></span></td>
  <td><span data-ttu-id="d3f5b-1316">HelpMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1316">HelpMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea52.png" alt="ImportMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1317">EA52</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1317">EA52</span></span></td>
  <td><span data-ttu-id="d3f5b-1318">ImportMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1318">ImportMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea53.png" alt="ImportAllMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1319">EA53</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1319">EA53</span></span></td>
  <td><span data-ttu-id="d3f5b-1320">ImportAllMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1320">ImportAllMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea54.png" alt="LeaveChatMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1321">EA54</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1321">EA54</span></span></td>
  <td><span data-ttu-id="d3f5b-1322">LeaveChatMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1322">LeaveChatMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea55.png" alt="ListMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1323">EA55</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1323">EA55</span></span></td>
  <td><span data-ttu-id="d3f5b-1324">ListMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1324">ListMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea56.png" alt="MailForwardMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1325">EA56</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1325">EA56</span></span></td>
  <td><span data-ttu-id="d3f5b-1326">MailForwardMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1326">MailForwardMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea57.png" alt="MailReplyMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1327">EA57</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1327">EA57</span></span></td>
  <td><span data-ttu-id="d3f5b-1328">MailReplyMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1328">MailReplyMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea58.png" alt="MailReplyAllMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1329">EA58</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1329">EA58</span></span></td>
  <td><span data-ttu-id="d3f5b-1330">MailReplyAllMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1330">MailReplyAllMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea5b.png" alt="OpenPaneMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1331">EA5B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1331">EA5B</span></span></td>
  <td><span data-ttu-id="d3f5b-1332">OpenPaneMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1332">OpenPaneMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea5c.png" alt="OpenWithMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1333">EA5C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1333">EA5C</span></span></td>
  <td><span data-ttu-id="d3f5b-1334">OpenWithMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1334">OpenWithMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea5e.png" alt="ParkingLocationMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1335">EA5E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1335">EA5E</span></span></td>
  <td><span data-ttu-id="d3f5b-1336">ParkingLocationMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1336">ParkingLocationMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea5f.png" alt="ResizeMouseMediumMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1337">EA5F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1337">EA5F</span></span></td>
  <td><span data-ttu-id="d3f5b-1338">ResizeMouseMediumMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1338">ResizeMouseMediumMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea60.png" alt="ResizeMouseSmallMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1339">EA60</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1339">EA60</span></span></td>
  <td><span data-ttu-id="d3f5b-1340">ResizeMouseSmallMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1340">ResizeMouseSmallMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea61.png" alt="ResizeMouseTallMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1341">EA61</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1341">EA61</span></span></td>
  <td><span data-ttu-id="d3f5b-1342">ResizeMouseTallMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1342">ResizeMouseTallMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea62.png" alt="ResizeTouchNarrowerMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1343">EA62</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1343">EA62</span></span></td>
  <td><span data-ttu-id="d3f5b-1344">ResizeTouchNarrowerMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1344">ResizeTouchNarrowerMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea63.png" alt="SendMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1345">EA63</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1345">EA63</span></span></td>
  <td><span data-ttu-id="d3f5b-1346">SendMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1346">SendMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea64.png" alt="SendFillMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1347">EA64</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1347">EA64</span></span></td>
  <td><span data-ttu-id="d3f5b-1348">SendFillMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1348">SendFillMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea65.png" alt="ShowResultsMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1349">EA65</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1349">EA65</span></span></td>
  <td><span data-ttu-id="d3f5b-1350">ShowResultsMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1350">ShowResultsMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea69.png" alt="Media" /></td>
  <td><span data-ttu-id="d3f5b-1351">EA69</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1351">EA69</span></span></td>
  <td><span data-ttu-id="d3f5b-1352">Medien</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1352">Media</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea6a.png" alt="SyncError" /></td>
  <td><span data-ttu-id="d3f5b-1353">EA6A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1353">EA6A</span></span></td>
  <td><span data-ttu-id="d3f5b-1354">SyncError</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1354">SyncError</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea6c.png" alt="Devices3" /></td>
  <td><span data-ttu-id="d3f5b-1355">EA6C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1355">EA6C</span></span></td>
  <td><span data-ttu-id="d3f5b-1356">Devices3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1356">Devices3</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea80.png" alt="Lightbulb" /></td>
  <td><span data-ttu-id="d3f5b-1357">EA80</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1357">EA80</span></span></td>
  <td><span data-ttu-id="d3f5b-1358">Lightbulb</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1358">Lightbulb</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea81.png" alt="StatusCircle" /></td>
  <td><span data-ttu-id="d3f5b-1359">EA81</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1359">EA81</span></span></td>
  <td><span data-ttu-id="d3f5b-1360">StatusCircle</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1360">StatusCircle</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea82.png" alt="StatusTriangle" /></td>
  <td><span data-ttu-id="d3f5b-1361">EA82</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1361">EA82</span></span></td>
  <td><span data-ttu-id="d3f5b-1362">StatusTriangle</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1362">StatusTriangle</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea83.png" alt="StatusError" /></td>
  <td><span data-ttu-id="d3f5b-1363">EA83</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1363">EA83</span></span></td>
  <td><span data-ttu-id="d3f5b-1364">StatusError</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1364">StatusError</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea84.png" alt="StatusWarning" /></td>
  <td><span data-ttu-id="d3f5b-1365">EA84</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1365">EA84</span></span></td>
  <td><span data-ttu-id="d3f5b-1366">StatusWarning</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1366">StatusWarning</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea86.png" alt="Puzzle" /></td>
  <td><span data-ttu-id="d3f5b-1367">EA86</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1367">EA86</span></span></td>
  <td><span data-ttu-id="d3f5b-1368">Puzzle</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1368">Puzzle</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea89.png" alt="CalendarSolid" /></td>
  <td><span data-ttu-id="d3f5b-1369">EA89</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1369">EA89</span></span></td>
  <td><span data-ttu-id="d3f5b-1370">CalendarSolid</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1370">CalendarSolid</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea8a.png" alt="HomeSolid" /></td>
  <td><span data-ttu-id="d3f5b-1371">EA8A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1371">EA8A</span></span></td>
  <td><span data-ttu-id="d3f5b-1372">HomeSolid</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1372">HomeSolid</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea8b.png" alt="ParkingLocationSolid" /></td>
  <td><span data-ttu-id="d3f5b-1373">EA8B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1373">EA8B</span></span></td>
  <td><span data-ttu-id="d3f5b-1374">ParkingLocationSolid</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1374">ParkingLocationSolid</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea8c.png" alt="ContactSolid" /></td>
  <td><span data-ttu-id="d3f5b-1375">EA8C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1375">EA8C</span></span></td>
  <td><span data-ttu-id="d3f5b-1376">ContactSolid</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1376">ContactSolid</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea8d.png" alt="ConstructionSolid" /></td>
  <td><span data-ttu-id="d3f5b-1377">EA8D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1377">EA8D</span></span></td>
  <td><span data-ttu-id="d3f5b-1378">ConstructionSolid</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1378">ConstructionSolid</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea8e.png" alt="AccidentSolid" /></td>
  <td><span data-ttu-id="d3f5b-1379">EA8E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1379">EA8E</span></span></td>
  <td><span data-ttu-id="d3f5b-1380">AccidentSolid</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1380">AccidentSolid</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea8f.png" alt="Ringer" /></td>
  <td><span data-ttu-id="d3f5b-1381">EA8F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1381">EA8F</span></span></td>
  <td><span data-ttu-id="d3f5b-1382">Ringer</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1382">Ringer</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea91.png" alt="ThoughtBubble" /></td>
  <td><span data-ttu-id="d3f5b-1383">EA91</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1383">EA91</span></span></td>
  <td><span data-ttu-id="d3f5b-1384">ThoughtBubble</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1384">ThoughtBubble</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea92.png" alt="HeartBroken" /></td>
  <td><span data-ttu-id="d3f5b-1385">EA92</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1385">EA92</span></span></td>
  <td><span data-ttu-id="d3f5b-1386">HeartBroken</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1386">HeartBroken</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea93.png" alt="BatteryCharging10" /></td>
  <td><span data-ttu-id="d3f5b-1387">EA93</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1387">EA93</span></span></td>
  <td><span data-ttu-id="d3f5b-1388">BatteryCharging10</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1388">BatteryCharging10</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea94.png" alt="BatterySaver9" /></td>
  <td><span data-ttu-id="d3f5b-1389">EA94</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1389">EA94</span></span></td>
  <td><span data-ttu-id="d3f5b-1390">BatterySaver9</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1390">BatterySaver9</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea95.png" alt="BatterySaver10" /></td>
  <td><span data-ttu-id="d3f5b-1391">EA95</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1391">EA95</span></span></td>
  <td><span data-ttu-id="d3f5b-1392">BatterySaver10</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1392">BatterySaver10</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea97.png" alt="CallForwardingMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1393">EA97</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1393">EA97</span></span></td>
  <td><span data-ttu-id="d3f5b-1394">CallForwardingMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1394">CallForwardingMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea98.png" alt="MultiSelectMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1395">EA98</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1395">EA98</span></span></td>
  <td><span data-ttu-id="d3f5b-1396">MultiSelectMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1396">MultiSelectMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ea99.png" alt="Broom" /></td>
  <td><span data-ttu-id="d3f5b-1397">EA99</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1397">EA99</span></span></td>
  <td><span data-ttu-id="d3f5b-1398">Broom</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1398">Broom</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eadf.png" alt="Trackers" /></td>
  <td><span data-ttu-id="d3f5b-1399">EADF</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1399">EADF</span></span></td>
  <td><span data-ttu-id="d3f5b-1400">Trackers</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1400">Trackers</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb05.png" alt="PieSingle" /></td>
  <td><span data-ttu-id="d3f5b-1401">EB05</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1401">EB05</span></span></td>
  <td><span data-ttu-id="d3f5b-1402">PieSingle</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1402">PieSingle</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb0f.png" alt="StockDown" /></td>
  <td><span data-ttu-id="d3f5b-1403">EB0F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1403">EB0F</span></span></td>
  <td><span data-ttu-id="d3f5b-1404">StockDown</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1404">StockDown</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb11.png" alt="StockUp" /></td>
  <td><span data-ttu-id="d3f5b-1405">EB11</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1405">EB11</span></span></td>
  <td><span data-ttu-id="d3f5b-1406">StockUp</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1406">StockUp</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb42.png" alt="Drop" /></td>
  <td><span data-ttu-id="d3f5b-1407">EB42</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1407">EB42</span></span></td>
  <td><span data-ttu-id="d3f5b-1408">Drop</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1408">Drop</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb47.png" alt="BusSolid" /></td>
  <td><span data-ttu-id="d3f5b-1409">EB47</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1409">EB47</span></span></td>
  <td><span data-ttu-id="d3f5b-1410">BusSolid</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1410">BusSolid</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb48.png" alt="FerrySolid" /></td>
  <td><span data-ttu-id="d3f5b-1411">EB48</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1411">EB48</span></span></td>
  <td><span data-ttu-id="d3f5b-1412">FerrySolid</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1412">FerrySolid</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb49.png" alt="StartPointSolid" /></td>
  <td><span data-ttu-id="d3f5b-1413">EB49</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1413">EB49</span></span></td>
  <td><span data-ttu-id="d3f5b-1414">StartPointSolid</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1414">StartPointSolid</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb4a.png" alt="StopPointSolid" /></td>
  <td><span data-ttu-id="d3f5b-1415">EB4A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1415">EB4A</span></span></td>
  <td><span data-ttu-id="d3f5b-1416">StopPointSolid</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1416">StopPointSolid</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb4b.png" alt="EndPointSolid" /></td>
  <td><span data-ttu-id="d3f5b-1417">EB4B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1417">EB4B</span></span></td>
  <td><span data-ttu-id="d3f5b-1418">EndPointSolid</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1418">EndPointSolid</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb4c.png" alt="AirplaneSolid" /></td>
  <td><span data-ttu-id="d3f5b-1419">EB4C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1419">EB4C</span></span></td>
  <td><span data-ttu-id="d3f5b-1420">AirplaneSolid</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1420">AirplaneSolid</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb4d.png" alt="TrainSolid" /></td>
  <td><span data-ttu-id="d3f5b-1421">EB4D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1421">EB4D</span></span></td>
  <td><span data-ttu-id="d3f5b-1422">TrainSolid</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1422">TrainSolid</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb4e.png" alt="WorkSolid" /></td>
  <td><span data-ttu-id="d3f5b-1423">EB4E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1423">EB4E</span></span></td>
  <td><span data-ttu-id="d3f5b-1424">WorkSolid</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1424">WorkSolid</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb4f.png" alt="ReminderFill" /></td>
  <td><span data-ttu-id="d3f5b-1425">EB4F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1425">EB4F</span></span></td>
  <td><span data-ttu-id="d3f5b-1426">ReminderFill</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1426">ReminderFill</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb50.png" alt="Reminder" /></td>
  <td><span data-ttu-id="d3f5b-1427">EB50</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1427">EB50</span></span></td>
  <td><span data-ttu-id="d3f5b-1428">Erinnerung</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1428">Reminder</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb51.png" alt="Heart" /></td>
  <td><span data-ttu-id="d3f5b-1429">EB51</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1429">EB51</span></span></td>
  <td><span data-ttu-id="d3f5b-1430">Heart</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1430">Heart</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb52.png" alt="HeartFill" /></td>
  <td><span data-ttu-id="d3f5b-1431">EB52</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1431">EB52</span></span></td>
  <td><span data-ttu-id="d3f5b-1432">HeartFill</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1432">HeartFill</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb55.png" alt="EthernetError" /></td>
  <td><span data-ttu-id="d3f5b-1433">EB55</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1433">EB55</span></span></td>
  <td><span data-ttu-id="d3f5b-1434">EthernetError</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1434">EthernetError</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb56.png" alt="EthernetWarning" /></td>
  <td><span data-ttu-id="d3f5b-1435">EB56</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1435">EB56</span></span></td>
  <td><span data-ttu-id="d3f5b-1436">EthernetWarning</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1436">EthernetWarning</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb57.png" alt="StatusConnecting1" /></td>
  <td><span data-ttu-id="d3f5b-1437">EB57</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1437">EB57</span></span></td>
  <td><span data-ttu-id="d3f5b-1438">StatusConnecting1</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1438">StatusConnecting1</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb58.png" alt="StatusConnecting2" /></td>
  <td><span data-ttu-id="d3f5b-1439">EB58</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1439">EB58</span></span></td>
  <td><span data-ttu-id="d3f5b-1440">StatusConnecting2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1440">StatusConnecting2</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb59.png" alt="StatusUnsecure" /></td>
  <td><span data-ttu-id="d3f5b-1441">EB59</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1441">EB59</span></span></td>
  <td><span data-ttu-id="d3f5b-1442">StatusUnsecure</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1442">StatusUnsecure</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb5a.png" alt="WifiError0" /></td>
  <td><span data-ttu-id="d3f5b-1443">EB5A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1443">EB5A</span></span></td>
  <td><span data-ttu-id="d3f5b-1444">WifiError0</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1444">WifiError0</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb5b.png" alt="WifiError1" /></td>
  <td><span data-ttu-id="d3f5b-1445">EB5B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1445">EB5B</span></span></td>
  <td><span data-ttu-id="d3f5b-1446">WifiError1</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1446">WifiError1</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb5c.png" alt="WifiError2" /></td>
  <td><span data-ttu-id="d3f5b-1447">EB5C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1447">EB5C</span></span></td>
  <td><span data-ttu-id="d3f5b-1448">WifiError2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1448">WifiError2</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb5d.png" alt="WifiError3" /></td>
  <td><span data-ttu-id="d3f5b-1449">EB5D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1449">EB5D</span></span></td>
  <td><span data-ttu-id="d3f5b-1450">WifiError3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1450">WifiError3</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb5e.png" alt="WifiError4" /></td>
  <td><span data-ttu-id="d3f5b-1451">EB5E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1451">EB5E</span></span></td>
  <td><span data-ttu-id="d3f5b-1452">WifiError4</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1452">WifiError4</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb5f.png" alt="WifiWarning0" /></td>
  <td><span data-ttu-id="d3f5b-1453">EB5F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1453">EB5F</span></span></td>
  <td><span data-ttu-id="d3f5b-1454">WifiWarning0</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1454">WifiWarning0</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb60.png" alt="WifiWarning1" /></td>
  <td><span data-ttu-id="d3f5b-1455">EB60</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1455">EB60</span></span></td>
  <td><span data-ttu-id="d3f5b-1456">WifiWarning1</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1456">WifiWarning1</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb61.png" alt="WifiWarning2" /></td>
  <td><span data-ttu-id="d3f5b-1457">EB61</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1457">EB61</span></span></td>
  <td><span data-ttu-id="d3f5b-1458">WifiWarning2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1458">WifiWarning2</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb62.png" alt="WifiWarning3" /></td>
  <td><span data-ttu-id="d3f5b-1459">EB62</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1459">EB62</span></span></td>
  <td><span data-ttu-id="d3f5b-1460">WifiWarning3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1460">WifiWarning3</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb63.png" alt="WifiWarning4" /></td>
  <td><span data-ttu-id="d3f5b-1461">EB63</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1461">EB63</span></span></td>
  <td><span data-ttu-id="d3f5b-1462">WifiWarning4</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1462">WifiWarning4</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb66.png" alt="Devices4" /></td>
  <td><span data-ttu-id="d3f5b-1463">EB66</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1463">EB66</span></span></td>
  <td><span data-ttu-id="d3f5b-1464">Devices4</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1464">Devices4</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb67.png" alt="NUIIris" /></td>
  <td><span data-ttu-id="d3f5b-1465">EB67</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1465">EB67</span></span></td>
  <td><span data-ttu-id="d3f5b-1466">NUIIris</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1466">NUIIris</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb68.png" alt="NUIFace" /></td>
  <td><span data-ttu-id="d3f5b-1467">EB68</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1467">EB68</span></span></td>
  <td><span data-ttu-id="d3f5b-1468">NUIFace</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1468">NUIFace</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb7e.png" alt="EditMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1469">EB7E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1469">EB7E</span></span></td>
  <td><span data-ttu-id="d3f5b-1470">EditMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1470">EditMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb82.png" alt="NUIFPStartSlideHand" /></td>
  <td><span data-ttu-id="d3f5b-1471">EB82</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1471">EB82</span></span></td>
  <td><span data-ttu-id="d3f5b-1472">NUIFPStartSlideHand</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1472">NUIFPStartSlideHand</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb83.png" alt="NUIFPStartSlideAction" /></td>
  <td><span data-ttu-id="d3f5b-1473">EB83</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1473">EB83</span></span></td>
  <td><span data-ttu-id="d3f5b-1474">NUIFPStartSlideAction</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1474">NUIFPStartSlideAction</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb84.png" alt="NUIFPContinueSlideHand" /></td>
  <td><span data-ttu-id="d3f5b-1475">EB84</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1475">EB84</span></span></td>
  <td><span data-ttu-id="d3f5b-1476">NUIFPContinueSlideHand</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1476">NUIFPContinueSlideHand</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb85.png" alt="NUIFPContinueSlideAction" /></td>
  <td><span data-ttu-id="d3f5b-1477">EB85</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1477">EB85</span></span></td>
  <td><span data-ttu-id="d3f5b-1478">NUIFPContinueSlideAction</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1478">NUIFPContinueSlideAction</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb86.png" alt="NUIFPRollRightHand" /></td>
  <td><span data-ttu-id="d3f5b-1479">EB86</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1479">EB86</span></span></td>
  <td><span data-ttu-id="d3f5b-1480">NUIFPRollRightHand</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1480">NUIFPRollRightHand</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb87.png" alt="NUIFPRollRightHandAction" /></td>
  <td><span data-ttu-id="d3f5b-1481">EB87</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1481">EB87</span></span></td>
  <td><span data-ttu-id="d3f5b-1482">NUIFPRollRightHandAction</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1482">NUIFPRollRightHandAction</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb88.png" alt="NUIFPRollLeftHand" /></td>
  <td><span data-ttu-id="d3f5b-1483">EB88</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1483">EB88</span></span></td>
  <td><span data-ttu-id="d3f5b-1484">NUIFPRollLeftHand</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1484">NUIFPRollLeftHand</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb89.png" alt="NUIFPRollLeftAction" /></td>
  <td><span data-ttu-id="d3f5b-1485">EB89</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1485">EB89</span></span></td>
  <td><span data-ttu-id="d3f5b-1486">NUIFPRollLeftAction</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1486">NUIFPRollLeftAction</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb8a.png" alt="NUIFPPressHand" /></td>
  <td><span data-ttu-id="d3f5b-1487">EB8A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1487">EB8A</span></span></td>
  <td><span data-ttu-id="d3f5b-1488">NUIFPPressHand</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1488">NUIFPPressHand</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb8b.png" alt="NUIFPPressAction" /></td>
  <td><span data-ttu-id="d3f5b-1489">EB8B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1489">EB8B</span></span></td>
  <td><span data-ttu-id="d3f5b-1490">NUIFPPressAction</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1490">NUIFPPressAction</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb8c.png" alt="NUIFPPressRepeatHand" /></td>
  <td><span data-ttu-id="d3f5b-1491">EB8C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1491">EB8C</span></span></td>
  <td><span data-ttu-id="d3f5b-1492">NUIFPPressRepeatHand</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1492">NUIFPPressRepeatHand</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb8d.png" alt="NUIFPPressRepeatAction" /></td>
  <td><span data-ttu-id="d3f5b-1493">EB8D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1493">EB8D</span></span></td>
  <td><span data-ttu-id="d3f5b-1494">NUIFPPressRepeatAction</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1494">NUIFPPressRepeatAction</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb90.png" alt="StatusErrorFull" /></td>
  <td><span data-ttu-id="d3f5b-1495">EB90</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1495">EB90</span></span></td>
  <td><span data-ttu-id="d3f5b-1496">StatusErrorFull</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1496">StatusErrorFull</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb91.png" alt="MultitaskExpanded" /></td>
  <td><span data-ttu-id="d3f5b-1497">EB91</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1497">EB91</span></span></td>
  <td><span data-ttu-id="d3f5b-1498">MultitaskExpanded</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1498">MultitaskExpanded</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb95.png" alt="Certificate" /></td>
  <td><span data-ttu-id="d3f5b-1499">EB95</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1499">EB95</span></span></td>
  <td><span data-ttu-id="d3f5b-1500">Zertifikat</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1500">Certificate</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb96.png" alt="BackSpaceQWERTYLg" /></td>
  <td><span data-ttu-id="d3f5b-1501">EB96</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1501">EB96</span></span></td>
  <td><span data-ttu-id="d3f5b-1502">BackSpaceQWERTYLg</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1502">BackSpaceQWERTYLg</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb97.png" alt="ReturnKeyLg" /></td>
  <td><span data-ttu-id="d3f5b-1503">EB97</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1503">EB97</span></span></td>
  <td><span data-ttu-id="d3f5b-1504">ReturnKeyLg</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1504">ReturnKeyLg</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb9d.png" alt="FastForward" /></td>
  <td><span data-ttu-id="d3f5b-1505">EB9D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1505">EB9D</span></span></td>
  <td><span data-ttu-id="d3f5b-1506">FastForward</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1506">FastForward</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb9e.png" alt="Rewind" /></td>
  <td><span data-ttu-id="d3f5b-1507">EB9E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1507">EB9E</span></span></td>
  <td><span data-ttu-id="d3f5b-1508">Rewind</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1508">Rewind</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eb9f.png" alt="Photo2" /></td>
  <td><span data-ttu-id="d3f5b-1509">EB9F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1509">EB9F</span></span></td>
  <td><span data-ttu-id="d3f5b-1510">Photo2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1510">Photo2</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eba0.png" alt="&nbsp;MobBattery0" /></td>
  <td><span data-ttu-id="d3f5b-1511">EBA0</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1511">EBA0</span></span></td>
  <td><span data-ttu-id="d3f5b-1512">&nbsp;MobBattery0</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1512">&nbsp;MobBattery0</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eba1.png" alt="&nbsp;MobBattery1" /></td>
  <td><span data-ttu-id="d3f5b-1513">EBA1</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1513">EBA1</span></span></td>
  <td><span data-ttu-id="d3f5b-1514">&nbsp;MobBattery1</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1514">&nbsp;MobBattery1</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eba2.png" alt="&nbsp;MobBattery2" /></td>
  <td><span data-ttu-id="d3f5b-1515">EBA2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1515">EBA2</span></span></td>
  <td><span data-ttu-id="d3f5b-1516">&nbsp;MobBattery2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1516">&nbsp;MobBattery2</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eba3.png" alt="&nbsp;MobBattery3" /></td>
  <td><span data-ttu-id="d3f5b-1517">EBA3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1517">EBA3</span></span></td>
  <td><span data-ttu-id="d3f5b-1518">&nbsp;MobBattery3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1518">&nbsp;MobBattery3</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eba4.png" alt="&nbsp;MobBattery4" /></td>
  <td><span data-ttu-id="d3f5b-1519">EBA4</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1519">EBA4</span></span></td>
  <td><span data-ttu-id="d3f5b-1520">&nbsp;MobBattery4</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1520">&nbsp;MobBattery4</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eba5.png" alt="&nbsp;MobBattery5" /></td>
  <td><span data-ttu-id="d3f5b-1521">EBA5</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1521">EBA5</span></span></td>
  <td><span data-ttu-id="d3f5b-1522">&nbsp;MobBattery5</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1522">&nbsp;MobBattery5</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eba6.png" alt="&nbsp;MobBattery6" /></td>
  <td><span data-ttu-id="d3f5b-1523">EBA6</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1523">EBA6</span></span></td>
  <td><span data-ttu-id="d3f5b-1524">&nbsp;MobBattery6</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1524">&nbsp;MobBattery6</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eba7.png" alt="&nbsp;MobBattery7" /></td>
  <td><span data-ttu-id="d3f5b-1525">EBA7</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1525">EBA7</span></span></td>
  <td><span data-ttu-id="d3f5b-1526">&nbsp;MobBattery7</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1526">&nbsp;MobBattery7</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eba8.png" alt="&nbsp;MobBattery8" /></td>
  <td><span data-ttu-id="d3f5b-1527">EBA8</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1527">EBA8</span></span></td>
  <td><span data-ttu-id="d3f5b-1528">&nbsp;MobBattery8</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1528">&nbsp;MobBattery8</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eba9.png" alt="&nbsp;MobBattery9" /></td>
  <td><span data-ttu-id="d3f5b-1529">EBA9</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1529">EBA9</span></span></td>
  <td><span data-ttu-id="d3f5b-1530">&nbsp;MobBattery9</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1530">&nbsp;MobBattery9</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebaa.png" alt="MobBattery10" /></td>
  <td><span data-ttu-id="d3f5b-1531">EBAA</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1531">EBAA</span></span></td>
  <td><span data-ttu-id="d3f5b-1532">MobBattery10</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1532">MobBattery10</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebab.png" alt="&nbsp;MobBatteryCharging0" /></td>
  <td><span data-ttu-id="d3f5b-1533">EBAB</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1533">EBAB</span></span></td>
  <td><span data-ttu-id="d3f5b-1534">&nbsp;MobBatteryCharging0</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1534">&nbsp;MobBatteryCharging0</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebac.png" alt="&nbsp;MobBatteryCharging1" /></td>
  <td><span data-ttu-id="d3f5b-1535">EBAC</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1535">EBAC</span></span></td>
  <td><span data-ttu-id="d3f5b-1536">&nbsp;MobBatteryCharging1</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1536">&nbsp;MobBatteryCharging1</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebad.png" alt="&nbsp;MobBatteryCharging2" /></td>
  <td><span data-ttu-id="d3f5b-1537">EBAD</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1537">EBAD</span></span></td>
  <td><span data-ttu-id="d3f5b-1538">&nbsp;MobBatteryCharging2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1538">&nbsp;MobBatteryCharging2</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebae.png" alt="&nbsp;MobBatteryCharging3" /></td>
  <td><span data-ttu-id="d3f5b-1539">EBAE</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1539">EBAE</span></span></td>
  <td><span data-ttu-id="d3f5b-1540">&nbsp;MobBatteryCharging3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1540">&nbsp;MobBatteryCharging3</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebaf.png" alt="&nbsp;MobBatteryCharging4" /></td>
  <td><span data-ttu-id="d3f5b-1541">EBAF</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1541">EBAF</span></span></td>
  <td><span data-ttu-id="d3f5b-1542">&nbsp;MobBatteryCharging4</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1542">&nbsp;MobBatteryCharging4</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebb0.png" alt="&nbsp;MobBatteryCharging5" /></td>
  <td><span data-ttu-id="d3f5b-1543">EBB0</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1543">EBB0</span></span></td>
  <td><span data-ttu-id="d3f5b-1544">&nbsp;MobBatteryCharging5</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1544">&nbsp;MobBatteryCharging5</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebb1.png" alt="&nbsp;MobBatteryCharging6" /></td>
  <td><span data-ttu-id="d3f5b-1545">EBB1</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1545">EBB1</span></span></td>
  <td><span data-ttu-id="d3f5b-1546">&nbsp;MobBatteryCharging6</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1546">&nbsp;MobBatteryCharging6</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebb2.png" alt="&nbsp;MobBatteryCharging7" /></td>
  <td><span data-ttu-id="d3f5b-1547">EBB2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1547">EBB2</span></span></td>
  <td><span data-ttu-id="d3f5b-1548">&nbsp;MobBatteryCharging7</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1548">&nbsp;MobBatteryCharging7</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebb3.png" alt="&nbsp;MobBatteryCharging8" /></td>
  <td><span data-ttu-id="d3f5b-1549">EBB3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1549">EBB3</span></span></td>
  <td><span data-ttu-id="d3f5b-1550">&nbsp;MobBatteryCharging8</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1550">&nbsp;MobBatteryCharging8</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebb4.png" alt="&nbsp;MobBatteryCharging9" /></td>
  <td><span data-ttu-id="d3f5b-1551">EBB4</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1551">EBB4</span></span></td>
  <td><span data-ttu-id="d3f5b-1552">&nbsp;MobBatteryCharging9</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1552">&nbsp;MobBatteryCharging9</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebb5.png" alt="&nbsp;MobBatteryCharging10" /></td>
  <td><span data-ttu-id="d3f5b-1553">EBB5</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1553">EBB5</span></span></td>
  <td><span data-ttu-id="d3f5b-1554">&nbsp;MobBatteryCharging10</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1554">&nbsp;MobBatteryCharging10</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebb6.png" alt="&nbsp;MobBatterySaver0" /></td>
  <td><span data-ttu-id="d3f5b-1555">EBB6</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1555">EBB6</span></span></td>
  <td><span data-ttu-id="d3f5b-1556">&nbsp;MobBatterySaver0</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1556">&nbsp;MobBatterySaver0</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebb7.png" alt="&nbsp;MobBatterySaver1" /></td>
  <td><span data-ttu-id="d3f5b-1557">EBB7</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1557">EBB7</span></span></td>
  <td><span data-ttu-id="d3f5b-1558">&nbsp;MobBatterySaver1</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1558">&nbsp;MobBatterySaver1</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebb8.png" alt="&nbsp;MobBatterySaver2" /></td>
  <td><span data-ttu-id="d3f5b-1559">EBB8</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1559">EBB8</span></span></td>
  <td><span data-ttu-id="d3f5b-1560">&nbsp;MobBatterySaver2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1560">&nbsp;MobBatterySaver2</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebb9.png" alt="&nbsp;MobBatterySaver3" /></td>
  <td><span data-ttu-id="d3f5b-1561">EBB9</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1561">EBB9</span></span></td>
  <td><span data-ttu-id="d3f5b-1562">&nbsp;MobBatterySaver3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1562">&nbsp;MobBatterySaver3</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebba.png" alt="&nbsp;MobBatterySaver4" /></td>
  <td><span data-ttu-id="d3f5b-1563">EBBA</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1563">EBBA</span></span></td>
  <td><span data-ttu-id="d3f5b-1564">&nbsp;MobBatterySaver4</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1564">&nbsp;MobBatterySaver4</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebbb.png" alt="&nbsp;MobBatterySaver5" /></td>
  <td><span data-ttu-id="d3f5b-1565">EBBB</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1565">EBBB</span></span></td>
  <td><span data-ttu-id="d3f5b-1566">&nbsp;MobBatterySaver5</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1566">&nbsp;MobBatterySaver5</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebbc.png" alt="&nbsp;MobBatterySaver6" /></td>
  <td><span data-ttu-id="d3f5b-1567">EBBC</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1567">EBBC</span></span></td>
  <td><span data-ttu-id="d3f5b-1568">&nbsp;MobBatterySaver6</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1568">&nbsp;MobBatterySaver6</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebbd.png" alt="&nbsp;MobBatterySaver7" /></td>
  <td><span data-ttu-id="d3f5b-1569">EBBD</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1569">EBBD</span></span></td>
  <td><span data-ttu-id="d3f5b-1570">&nbsp;MobBatterySaver7</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1570">&nbsp;MobBatterySaver7</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebbe.png" alt="&nbsp;MobBatterySaver8" /></td>
  <td><span data-ttu-id="d3f5b-1571">EBBE</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1571">EBBE</span></span></td>
  <td><span data-ttu-id="d3f5b-1572">&nbsp;MobBatterySaver8</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1572">&nbsp;MobBatterySaver8</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebbf.png" alt="&nbsp;MobBatterySaver9" /></td>
  <td><span data-ttu-id="d3f5b-1573">EBBF</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1573">EBBF</span></span></td>
  <td><span data-ttu-id="d3f5b-1574">&nbsp;MobBatterySaver9</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1574">&nbsp;MobBatterySaver9</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebc0.png" alt="&nbsp;MobBatterySaver10" /></td>
  <td><span data-ttu-id="d3f5b-1575">EBC0</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1575">EBC0</span></span></td>
  <td><span data-ttu-id="d3f5b-1576">&nbsp;MobBatterySaver10</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1576">&nbsp;MobBatterySaver10</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebc3.png" alt="DictionaryCloud" /></td>
  <td><span data-ttu-id="d3f5b-1577">EBC3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1577">EBC3</span></span></td>
  <td><span data-ttu-id="d3f5b-1578">DictionaryCloud</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1578">DictionaryCloud</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebc4.png" alt="ResetDrive" /></td>
  <td><span data-ttu-id="d3f5b-1579">EBC4</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1579">EBC4</span></span></td>
  <td><span data-ttu-id="d3f5b-1580">ResetDrive</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1580">ResetDrive</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebc5.png" alt="VolumeBars" /></td>
  <td><span data-ttu-id="d3f5b-1581">EBC5</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1581">EBC5</span></span></td>
  <td><span data-ttu-id="d3f5b-1582">VolumeBars</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1582">VolumeBars</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebc6.png" alt="Project" /></td>
  <td><span data-ttu-id="d3f5b-1583">EBC6</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1583">EBC6</span></span></td>
  <td><span data-ttu-id="d3f5b-1584">Projizieren</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1584">Project</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebd2.png" alt="AdjustHologram" /></td>
  <td><span data-ttu-id="d3f5b-1585">EBD2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1585">EBD2</span></span></td>
  <td><span data-ttu-id="d3f5b-1586">AdjustHologram</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1586">AdjustHologram</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebd4.png" alt="WifiCallBars" /></td>
  <td><span data-ttu-id="d3f5b-1587">EBD4</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1587">EBD4</span></span></td>
  <td><span data-ttu-id="d3f5b-1588">WifiCallBars</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1588">WifiCallBars</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebd5.png" alt="WifiCall0" /></td>
  <td><span data-ttu-id="d3f5b-1589">EBD5</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1589">EBD5</span></span></td>
  <td><span data-ttu-id="d3f5b-1590">WifiCall0</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1590">WifiCall0</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebd6.png" alt="WifiCall1" /></td>
  <td><span data-ttu-id="d3f5b-1591">EBD6</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1591">EBD6</span></span></td>
  <td><span data-ttu-id="d3f5b-1592">WifiCall1</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1592">WifiCall1</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebd7.png" alt="WifiCall2" /></td>
  <td><span data-ttu-id="d3f5b-1593">EBD7</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1593">EBD7</span></span></td>
  <td><span data-ttu-id="d3f5b-1594">WifiCall2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1594">WifiCall2</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebd8.png" alt="WifiCall3" /></td>
  <td><span data-ttu-id="d3f5b-1595">EBD8</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1595">EBD8</span></span></td>
  <td><span data-ttu-id="d3f5b-1596">WifiCall3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1596">WifiCall3</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebd9.png" alt="WifiCall4" /></td>
  <td><span data-ttu-id="d3f5b-1597">EBD9</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1597">EBD9</span></span></td>
  <td><span data-ttu-id="d3f5b-1598">WifiCall4</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1598">WifiCall4</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebde.png" alt="DeviceDiscovery" /></td>
  <td><span data-ttu-id="d3f5b-1599">EBDE</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1599">EBDE</span></span></td>
  <td><span data-ttu-id="d3f5b-1600">DeviceDiscovery</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1600">DeviceDiscovery</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebe6.png" alt="WindDirection" /></td>
  <td><span data-ttu-id="d3f5b-1601">EBE6</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1601">EBE6</span></span></td>
  <td><span data-ttu-id="d3f5b-1602">WindDirection</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1602">WindDirection</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebe7.png" alt="RightArrowKeyTime0" /></td>
  <td><span data-ttu-id="d3f5b-1603">EBE7</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1603">EBE7</span></span></td>
  <td><span data-ttu-id="d3f5b-1604">RightArrowKeyTime0</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1604">RightArrowKeyTime0</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebfc.png" alt="TabletMode" /></td>
  <td><span data-ttu-id="d3f5b-1605">EBFC</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1605">EBFC</span></span></td>
  <td><span data-ttu-id="d3f5b-1606">TabletMode</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1606">TabletMode</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebfd.png" alt="StatusCircleLeft" /></td>
  <td><span data-ttu-id="d3f5b-1607">EBFD</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1607">EBFD</span></span></td>
  <td><span data-ttu-id="d3f5b-1608">StatusCircleLeft</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1608">StatusCircleLeft</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebfe.png" alt="StatusTriangleLeft" /></td>
  <td><span data-ttu-id="d3f5b-1609">EBFE</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1609">EBFE</span></span></td>
  <td><span data-ttu-id="d3f5b-1610">StatusTriangleLeft</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1610">StatusTriangleLeft</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ebff.png" alt="StatusErrorLeft" /></td>
  <td><span data-ttu-id="d3f5b-1611">EBFF</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1611">EBFF</span></span></td>
  <td><span data-ttu-id="d3f5b-1612">StatusErrorLeft</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1612">StatusErrorLeft</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec00.png" alt="StatusWarningLeft" /></td>
  <td><span data-ttu-id="d3f5b-1613">EC00</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1613">EC00</span></span></td>
  <td><span data-ttu-id="d3f5b-1614">StatusWarningLeft</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1614">StatusWarningLeft</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec02.png" alt="MobBatteryUnknown" /></td>
  <td><span data-ttu-id="d3f5b-1615">EC02</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1615">EC02</span></span></td>
  <td><span data-ttu-id="d3f5b-1616">MobBatteryUnknown</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1616">MobBatteryUnknown</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec05.png" alt="NetworkTower" /></td>
  <td><span data-ttu-id="d3f5b-1617">EC05</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1617">EC05</span></span></td>
  <td><span data-ttu-id="d3f5b-1618">NetworkTower</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1618">NetworkTower</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec06.png" alt="CityNext" /></td>
  <td><span data-ttu-id="d3f5b-1619">EC06</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1619">EC06</span></span></td>
  <td><span data-ttu-id="d3f5b-1620">CityNext</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1620">CityNext</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec07.png" alt="CityNext2" /></td>
  <td><span data-ttu-id="d3f5b-1621">EC07</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1621">EC07</span></span></td>
  <td><span data-ttu-id="d3f5b-1622">CityNext2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1622">CityNext2</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec08.png" alt="Courthouse" /></td>
  <td><span data-ttu-id="d3f5b-1623">EC08</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1623">EC08</span></span></td>
  <td><span data-ttu-id="d3f5b-1624">Courthouse</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1624">Courthouse</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec09.png" alt="Groceries" /></td>
  <td><span data-ttu-id="d3f5b-1625">EC09</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1625">EC09</span></span></td>
  <td><span data-ttu-id="d3f5b-1626">Groceries</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1626">Groceries</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec0a.png" alt="Sustainable" /></td>
  <td><span data-ttu-id="d3f5b-1627">EC0A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1627">EC0A</span></span></td>
  <td><span data-ttu-id="d3f5b-1628">Sustainable</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1628">Sustainable</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec0b.png" alt="BuildingEnergy" /></td>
  <td><span data-ttu-id="d3f5b-1629">EC0B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1629">EC0B</span></span></td>
  <td><span data-ttu-id="d3f5b-1630">BuildingEnergy</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1630">BuildingEnergy</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec11.png" alt="ToggleFilled" /></td>
  <td><span data-ttu-id="d3f5b-1631">EC11</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1631">EC11</span></span></td>
  <td><span data-ttu-id="d3f5b-1632">ToggleFilled</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1632">ToggleFilled</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec12.png" alt="ToggleBorder" /></td>
  <td><span data-ttu-id="d3f5b-1633">EC12</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1633">EC12</span></span></td>
  <td><span data-ttu-id="d3f5b-1634">ToggleBorder</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1634">ToggleBorder</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec13.png" alt="SliderThumb" /></td>
  <td><span data-ttu-id="d3f5b-1635">EC13</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1635">EC13</span></span></td>
  <td><span data-ttu-id="d3f5b-1636">SliderThumb</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1636">SliderThumb</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec14.png" alt="ToggleThumb" /></td>
  <td><span data-ttu-id="d3f5b-1637">EC14</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1637">EC14</span></span></td>
  <td><span data-ttu-id="d3f5b-1638">ToggleThumb</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1638">ToggleThumb</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec15.png" alt="MiracastLogoSmall" /></td>
  <td><span data-ttu-id="d3f5b-1639">EC15</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1639">EC15</span></span></td>
  <td><span data-ttu-id="d3f5b-1640">MiracastLogoSmall</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1640">MiracastLogoSmall</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec16.png" alt="MiracastLogoLarge" /></td>
  <td><span data-ttu-id="d3f5b-1641">EC16</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1641">EC16</span></span></td>
  <td><span data-ttu-id="d3f5b-1642">MiracastLogoLarge</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1642">MiracastLogoLarge</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec19.png" alt="PLAP" /></td>
  <td><span data-ttu-id="d3f5b-1643">EC19</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1643">EC19</span></span></td>
  <td><span data-ttu-id="d3f5b-1644">PLAP</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1644">PLAP</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec1b.png" alt="Badge" /></td>
  <td><span data-ttu-id="d3f5b-1645">EC1B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1645">EC1B</span></span></td>
  <td><span data-ttu-id="d3f5b-1646">Badge</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1646">Badge</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec1e.png" alt="SignalRoaming" /></td>
  <td><span data-ttu-id="d3f5b-1647">EC1E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1647">EC1E</span></span></td>
  <td><span data-ttu-id="d3f5b-1648">SignalRoaming</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1648">SignalRoaming</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec20.png" alt="MobileLocked" /></td>
  <td><span data-ttu-id="d3f5b-1649">EC20</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1649">EC20</span></span></td>
  <td><span data-ttu-id="d3f5b-1650">MobileLocked</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1650">MobileLocked</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec24.png" alt="InsiderHubApp" /></td>
  <td><span data-ttu-id="d3f5b-1651">EC24</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1651">EC24</span></span></td>
  <td><span data-ttu-id="d3f5b-1652">InsiderHubApp</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1652">InsiderHubApp</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec25.png" alt="PersonalFolder" /></td>
  <td><span data-ttu-id="d3f5b-1653">EC25</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1653">EC25</span></span></td>
  <td><span data-ttu-id="d3f5b-1654">PersonalFolder</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1654">PersonalFolder</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec26.png" alt="HomeGroup" /></td>
  <td><span data-ttu-id="d3f5b-1655">EC26</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1655">EC26</span></span></td>
  <td><span data-ttu-id="d3f5b-1656">HomeGroup</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1656">HomeGroup</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec27.png" alt="MyNetwork" /></td>
  <td><span data-ttu-id="d3f5b-1657">EC27</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1657">EC27</span></span></td>
  <td><span data-ttu-id="d3f5b-1658">MyNetwork</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1658">MyNetwork</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec31.png" alt="KeyboardFull" /></td>
  <td><span data-ttu-id="d3f5b-1659">EC31</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1659">EC31</span></span></td>
  <td><span data-ttu-id="d3f5b-1660">KeyboardFull</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1660">KeyboardFull</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec37.png" alt="MobSignal1" /></td>
  <td><span data-ttu-id="d3f5b-1661">EC37</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1661">EC37</span></span></td>
  <td><span data-ttu-id="d3f5b-1662">MobSignal1</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1662">MobSignal1</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec38.png" alt="MobSignal2" /></td>
  <td><span data-ttu-id="d3f5b-1663">EC38</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1663">EC38</span></span></td>
  <td><span data-ttu-id="d3f5b-1664">MobSignal2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1664">MobSignal2</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec39.png" alt="MobSignal3" /></td>
  <td><span data-ttu-id="d3f5b-1665">EC39</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1665">EC39</span></span></td>
  <td><span data-ttu-id="d3f5b-1666">MobSignal3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1666">MobSignal3</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec3a.png" alt="MobSignal4" /></td>
  <td><span data-ttu-id="d3f5b-1667">EC3A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1667">EC3A</span></span></td>
  <td><span data-ttu-id="d3f5b-1668">MobSignal4</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1668">MobSignal4</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec3b.png" alt="MobSignal5" /></td>
  <td><span data-ttu-id="d3f5b-1669">EC3B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1669">EC3B</span></span></td>
  <td><span data-ttu-id="d3f5b-1670">MobSignal5</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1670">MobSignal5</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec3c.png" alt="MobWifi1" /></td>
  <td><span data-ttu-id="d3f5b-1671">EC3C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1671">EC3C</span></span></td>
  <td><span data-ttu-id="d3f5b-1672">MobWifi1</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1672">MobWifi1</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec3d.png" alt="MobWifi2" /></td>
  <td><span data-ttu-id="d3f5b-1673">EC3D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1673">EC3D</span></span></td>
  <td><span data-ttu-id="d3f5b-1674">MobWifi2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1674">MobWifi2</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec3e.png" alt="MobWifi3" /></td>
  <td><span data-ttu-id="d3f5b-1675">EC3E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1675">EC3E</span></span></td>
  <td><span data-ttu-id="d3f5b-1676">MobWifi3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1676">MobWifi3</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec3f.png" alt="MobWifi4" /></td>
  <td><span data-ttu-id="d3f5b-1677">EC3F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1677">EC3F</span></span></td>
  <td><span data-ttu-id="d3f5b-1678">MobWifi4</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1678">MobWifi4</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec40.png" alt="MobAirplane" /></td>
  <td><span data-ttu-id="d3f5b-1679">EC40</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1679">EC40</span></span></td>
  <td><span data-ttu-id="d3f5b-1680">MobAirplane</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1680">MobAirplane</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec41.png" alt="MobBluetooth" /></td>
  <td><span data-ttu-id="d3f5b-1681">EC41</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1681">EC41</span></span></td>
  <td><span data-ttu-id="d3f5b-1682">MobBluetooth</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1682">MobBluetooth</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec42.png" alt="MobActionCenter" /></td>
  <td><span data-ttu-id="d3f5b-1683">EC42</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1683">EC42</span></span></td>
  <td><span data-ttu-id="d3f5b-1684">MobActionCenter</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1684">MobActionCenter</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec43.png" alt="MobLocation" /></td>
  <td><span data-ttu-id="d3f5b-1685">EC43</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1685">EC43</span></span></td>
  <td><span data-ttu-id="d3f5b-1686">MobLocation</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1686">MobLocation</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec44.png" alt="MobWifiHotspot" /></td>
  <td><span data-ttu-id="d3f5b-1687">EC44</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1687">EC44</span></span></td>
  <td><span data-ttu-id="d3f5b-1688">MobWifiHotspot</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1688">MobWifiHotspot</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec45.png" alt="LanguageJpn" /></td>
  <td><span data-ttu-id="d3f5b-1689">EC45</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1689">EC45</span></span></td>
  <td><span data-ttu-id="d3f5b-1690">LanguageJpn</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1690">LanguageJpn</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec46.png" alt="MobQuietHours" /></td>
  <td><span data-ttu-id="d3f5b-1691">EC46</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1691">EC46</span></span></td>
  <td><span data-ttu-id="d3f5b-1692">MobQuietHours</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1692">MobQuietHours</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec47.png" alt="MobDrivingMode" /></td>
  <td><span data-ttu-id="d3f5b-1693">EC47</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1693">EC47</span></span></td>
  <td><span data-ttu-id="d3f5b-1694">MobDrivingMode</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1694">MobDrivingMode</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec48.png" alt="SpeedOff" /></td>
  <td><span data-ttu-id="d3f5b-1695">EC48</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1695">EC48</span></span></td>
  <td><span data-ttu-id="d3f5b-1696">SpeedOff</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1696">SpeedOff</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec49.png" alt="SpeedMedium" /></td>
  <td><span data-ttu-id="d3f5b-1697">EC49</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1697">EC49</span></span></td>
  <td><span data-ttu-id="d3f5b-1698">SpeedMedium</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1698">SpeedMedium</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec4a.png" alt="SpeedHigh" /></td>
  <td><span data-ttu-id="d3f5b-1699">EC4A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1699">EC4A</span></span></td>
  <td><span data-ttu-id="d3f5b-1700">SpeedHigh</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1700">SpeedHigh</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec4e.png" alt="ThisPC" /></td>
  <td><span data-ttu-id="d3f5b-1701">EC4E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1701">EC4E</span></span></td>
  <td><span data-ttu-id="d3f5b-1702">ThisPC</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1702">ThisPC</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec4f.png" alt="MusicNote" /></td>
  <td><span data-ttu-id="d3f5b-1703">EC4F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1703">EC4F</span></span></td>
  <td><span data-ttu-id="d3f5b-1704">MusicNote</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1704">MusicNote</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec50.png" alt="FileExplorer" /></td>
  <td><span data-ttu-id="d3f5b-1705">EC50</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1705">EC50</span></span></td>
  <td><span data-ttu-id="d3f5b-1706">FileExplorer</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1706">FileExplorer</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec51.png" alt="FileExplorerApp" /></td>
  <td><span data-ttu-id="d3f5b-1707">EC51</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1707">EC51</span></span></td>
  <td><span data-ttu-id="d3f5b-1708">FileExplorerApp</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1708">FileExplorerApp</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec52.png" alt="LeftArrowKeyTime0" /></td>
  <td><span data-ttu-id="d3f5b-1709">EC52</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1709">EC52</span></span></td>
  <td><span data-ttu-id="d3f5b-1710">LeftArrowKeyTime0</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1710">LeftArrowKeyTime0</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec54.png" alt="MicOff" /></td>
  <td><span data-ttu-id="d3f5b-1711">EC54</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1711">EC54</span></span></td>
  <td><span data-ttu-id="d3f5b-1712">MicOff</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1712">MicOff</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec55.png" alt="MicSleep" /></td>
  <td><span data-ttu-id="d3f5b-1713">EC55</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1713">EC55</span></span></td>
  <td><span data-ttu-id="d3f5b-1714">MicSleep</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1714">MicSleep</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec56.png" alt="MicError" /></td>
  <td><span data-ttu-id="d3f5b-1715">EC56</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1715">EC56</span></span></td>
  <td><span data-ttu-id="d3f5b-1716">MicError</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1716">MicError</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec57.png" alt="PlaybackRate1x" /></td>
  <td><span data-ttu-id="d3f5b-1717">EC57</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1717">EC57</span></span></td>
  <td><span data-ttu-id="d3f5b-1718">PlaybackRate1x</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1718">PlaybackRate1x</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec58.png" alt="PlaybackRateOther" /></td>
  <td><span data-ttu-id="d3f5b-1719">EC58</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1719">EC58</span></span></td>
  <td><span data-ttu-id="d3f5b-1720">PlaybackRateOther</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1720">PlaybackRateOther</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec59.png" alt="CashDrawer" /></td>
  <td><span data-ttu-id="d3f5b-1721">EC59</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1721">EC59</span></span></td>
  <td><span data-ttu-id="d3f5b-1722">CashDrawer</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1722">CashDrawer</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec5a.png" alt="BarcodeScanner" /></td>
  <td><span data-ttu-id="d3f5b-1723">EC5A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1723">EC5A</span></span></td>
  <td><span data-ttu-id="d3f5b-1724">BarcodeScanner</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1724">BarcodeScanner</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec5b.png" alt="ReceiptPrinter" /></td>
  <td><span data-ttu-id="d3f5b-1725">EC5B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1725">EC5B</span></span></td>
  <td><span data-ttu-id="d3f5b-1726">ReceiptPrinter</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1726">ReceiptPrinter</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec5c.png" alt="MagStripeReader" /></td>
  <td><span data-ttu-id="d3f5b-1727">EC5C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1727">EC5C</span></span></td>
  <td><span data-ttu-id="d3f5b-1728">MagStripeReader</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1728">MagStripeReader</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec61.png" alt="CompletedSolid" /></td>
  <td><span data-ttu-id="d3f5b-1729">EC61</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1729">EC61</span></span></td>
  <td><span data-ttu-id="d3f5b-1730">CompletedSolid</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1730">CompletedSolid</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec64.png" alt="CompanionApp" /></td>
  <td><span data-ttu-id="d3f5b-1731">EC64</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1731">EC64</span></span></td>
  <td><span data-ttu-id="d3f5b-1732">CompanionApp</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1732">CompanionApp</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec6d.png" alt="SwipeRevealArt" /></td>
  <td><span data-ttu-id="d3f5b-1733">EC6D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1733">EC6D</span></span></td>
  <td><span data-ttu-id="d3f5b-1734">SwipeRevealArt</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1734">SwipeRevealArt</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec71.png" alt="MicOn" /></td>
  <td><span data-ttu-id="d3f5b-1735">EC71</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1735">EC71</span></span></td>
  <td><span data-ttu-id="d3f5b-1736">MicOn</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1736">MicOn</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec72.png" alt="MicClipping" /></td>
  <td><span data-ttu-id="d3f5b-1737">EC72</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1737">EC72</span></span></td>
  <td><span data-ttu-id="d3f5b-1738">MicClipping</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1738">MicClipping</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec74.png" alt="TabletSelected" /></td>
  <td><span data-ttu-id="d3f5b-1739">EC74</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1739">EC74</span></span></td>
  <td><span data-ttu-id="d3f5b-1740">TabletSelected</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1740">TabletSelected</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec75.png" alt="MobileSelected" /></td>
  <td><span data-ttu-id="d3f5b-1741">EC75</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1741">EC75</span></span></td>
  <td><span data-ttu-id="d3f5b-1742">MobileSelected</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1742">MobileSelected</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec76.png" alt="LaptopSelected" /></td>
  <td><span data-ttu-id="d3f5b-1743">EC76</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1743">EC76</span></span></td>
  <td><span data-ttu-id="d3f5b-1744">LaptopSelected</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1744">LaptopSelected</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec77.png" alt="TVMonitorSelected" /></td>
  <td><span data-ttu-id="d3f5b-1745">EC77</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1745">EC77</span></span></td>
  <td><span data-ttu-id="d3f5b-1746">TVMonitorSelected</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1746">TVMonitorSelected</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec7a.png" alt="DeveloperTools" /></td>
  <td><span data-ttu-id="d3f5b-1747">EC7A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1747">EC7A</span></span></td>
  <td><span data-ttu-id="d3f5b-1748">DeveloperTools</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1748">DeveloperTools</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec7e.png" alt="MobCallForwarding" /></td>
  <td><span data-ttu-id="d3f5b-1749">EC7E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1749">EC7E</span></span></td>
  <td><span data-ttu-id="d3f5b-1750">MobCallForwarding</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1750">MobCallForwarding</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec7f.png" alt="MobCallForwardingMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1751">EC7F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1751">EC7F</span></span></td>
  <td><span data-ttu-id="d3f5b-1752">MobCallForwardingMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1752">MobCallForwardingMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec80.png" alt="BodyCam" /></td>
  <td><span data-ttu-id="d3f5b-1753">EC80</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1753">EC80</span></span></td>
  <td><span data-ttu-id="d3f5b-1754">BodyCam</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1754">BodyCam</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec81.png" alt="PoliceCar" /></td>
  <td><span data-ttu-id="d3f5b-1755">EC81</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1755">EC81</span></span></td>
  <td><span data-ttu-id="d3f5b-1756">PoliceCar</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1756">PoliceCar</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec87.png" alt="Draw" /></td>
  <td><span data-ttu-id="d3f5b-1757">EC87</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1757">EC87</span></span></td>
  <td><span data-ttu-id="d3f5b-1758">Draw</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1758">Draw</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec88.png" alt="DrawSolid" /></td>
  <td><span data-ttu-id="d3f5b-1759">EC88</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1759">EC88</span></span></td>
  <td><span data-ttu-id="d3f5b-1760">DrawSolid</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1760">DrawSolid</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec8a.png" alt="LowerBrightness" /></td>
  <td><span data-ttu-id="d3f5b-1761">EC8A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1761">EC8A</span></span></td>
  <td><span data-ttu-id="d3f5b-1762">LowerBrightness</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1762">LowerBrightness</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec8f.png" alt="ScrollUpDown" /></td>
  <td><span data-ttu-id="d3f5b-1763">EC8F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1763">EC8F</span></span></td>
  <td><span data-ttu-id="d3f5b-1764">ScrollUpDown</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1764">ScrollUpDown</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ec92.png" alt="DateTime" /></td>
  <td><span data-ttu-id="d3f5b-1765">EC92</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1765">EC92</span></span></td>
  <td><span data-ttu-id="d3f5b-1766">DateTime</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1766">DateTime</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eca5.png" alt="Tiles" /></td>
  <td><span data-ttu-id="d3f5b-1767">ECA5</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1767">ECA5</span></span></td>
  <td><span data-ttu-id="d3f5b-1768">Kacheln</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1768">Tiles</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eca7.png" alt="PartyLeader" /></td>
  <td><span data-ttu-id="d3f5b-1769">ECA7</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1769">ECA7</span></span></td>
  <td><span data-ttu-id="d3f5b-1770">PartyLeader</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1770">PartyLeader</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ecaa.png" alt="AppIconDefault" /></td>
  <td><span data-ttu-id="d3f5b-1771">ECAA</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1771">ECAA</span></span></td>
  <td><span data-ttu-id="d3f5b-1772">AppIconDefault</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1772">AppIconDefault</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ecc4.png" alt="AddSurfaceHub" /></td>
  <td><span data-ttu-id="d3f5b-1773">ECC4</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1773">ECC4</span></span></td>
  <td><span data-ttu-id="d3f5b-1774">AddSurfaceHub</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1774">AddSurfaceHub</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ecc5.png" alt="DevUpdate" /></td>
  <td><span data-ttu-id="d3f5b-1775">ECC5</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1775">ECC5</span></span></td>
  <td><span data-ttu-id="d3f5b-1776">DevUpdate</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1776">DevUpdate</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ecc6.png" alt="Unit" /></td>
  <td><span data-ttu-id="d3f5b-1777">ECC6</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1777">ECC6</span></span></td>
  <td><span data-ttu-id="d3f5b-1778">Einheit</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1778">Unit</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ecc8.png" alt="AddTo" /></td>
  <td><span data-ttu-id="d3f5b-1779">ECC8</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1779">ECC8</span></span></td>
  <td><span data-ttu-id="d3f5b-1780">AddTo</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1780">AddTo</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ecc9.png" alt="RemoveFrom" /></td>
  <td><span data-ttu-id="d3f5b-1781">ECC9</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1781">ECC9</span></span></td>
  <td><span data-ttu-id="d3f5b-1782">RemoveFrom</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1782">RemoveFrom</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ecca.png" alt="RadioBtnOff" /></td>
  <td><span data-ttu-id="d3f5b-1783">ECCA</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1783">ECCA</span></span></td>
  <td><span data-ttu-id="d3f5b-1784">RadioBtnOff</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1784">RadioBtnOff</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eccb.png" alt="RadioBtnOn" /></td>
  <td><span data-ttu-id="d3f5b-1785">ECCB</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1785">ECCB</span></span></td>
  <td><span data-ttu-id="d3f5b-1786">RadioBtnOn</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1786">RadioBtnOn</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eccc.png" alt="RadioBullet2" /></td>
  <td><span data-ttu-id="d3f5b-1787">ECCC</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1787">ECCC</span></span></td>
  <td><span data-ttu-id="d3f5b-1788">RadioBullet2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1788">RadioBullet2</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eccd.png" alt="ExploreContent" /></td>
  <td><span data-ttu-id="d3f5b-1789">ECCD</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1789">ECCD</span></span></td>
  <td><span data-ttu-id="d3f5b-1790">ExploreContent</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1790">ExploreContent</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ece7.png" alt="ScrollMode" /></td>
  <td><span data-ttu-id="d3f5b-1791">ECE7</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1791">ECE7</span></span></td>
  <td><span data-ttu-id="d3f5b-1792">ScrollMode</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1792">ScrollMode</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ece8.png" alt="ZoomMode" /></td>
  <td><span data-ttu-id="d3f5b-1793">ECE8</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1793">ECE8</span></span></td>
  <td><span data-ttu-id="d3f5b-1794">ZoomMode</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1794">ZoomMode</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ece9.png" alt="PanMode" /></td>
  <td><span data-ttu-id="d3f5b-1795">ECE9</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1795">ECE9</span></span></td>
  <td><span data-ttu-id="d3f5b-1796">PanMode</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1796">PanMode</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ecf0.png" alt="WiredUSB&nbsp;" /></td>
  <td><span data-ttu-id="d3f5b-1797">ECF0</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1797">ECF0</span></span></td>
  <td><span data-ttu-id="d3f5b-1798">WiredUSB&nbsp;</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1798">WiredUSB&nbsp;</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ecf1.png" alt="WirelessUSB" /></td>
  <td><span data-ttu-id="d3f5b-1799">ECF1</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1799">ECF1</span></span></td>
  <td><span data-ttu-id="d3f5b-1800">WirelessUSB</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1800">WirelessUSB</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ecf3.png" alt="USBSafeConnect" /></td>
  <td><span data-ttu-id="d3f5b-1801">ECF3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1801">ECF3</span></span></td>
  <td><span data-ttu-id="d3f5b-1802">USBSafeConnect</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1802">USBSafeConnect</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed0c.png" alt="ActionCenterNotificationMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1803">ED0C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1803">ED0C</span></span></td>
  <td><span data-ttu-id="d3f5b-1804">ActionCenterNotificationMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1804">ActionCenterNotificationMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed0d.png" alt="ActionCenterMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1805">ED0D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1805">ED0D</span></span></td>
  <td><span data-ttu-id="d3f5b-1806">ActionCenterMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1806">ActionCenterMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed10.png" alt="ResetDevice" /></td>
  <td><span data-ttu-id="d3f5b-1807">ED10</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1807">ED10</span></span></td>
  <td><span data-ttu-id="d3f5b-1808">ResetDevice</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1808">ResetDevice</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed15.png" alt="Feedback" /></td>
  <td><span data-ttu-id="d3f5b-1809">ED15</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1809">ED15</span></span></td>
  <td><span data-ttu-id="d3f5b-1810">Feedback</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1810">Feedback</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed1e.png" alt="Subtitles" /></td>
  <td><span data-ttu-id="d3f5b-1811">ED1E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1811">ED1E</span></span></td>
  <td><span data-ttu-id="d3f5b-1812">Subtitles</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1812">Subtitles</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed1f.png" alt="SubtitlesAudio" /></td>
  <td><span data-ttu-id="d3f5b-1813">ED1F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1813">ED1F</span></span></td>
  <td><span data-ttu-id="d3f5b-1814">SubtitlesAudio</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1814">SubtitlesAudio</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed28.png" alt="CalendarMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1815">ED28</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1815">ED28</span></span></td>
  <td><span data-ttu-id="d3f5b-1816">CalendarMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1816">CalendarMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed2a.png" alt="eSIM" /></td>
  <td><span data-ttu-id="d3f5b-1817">ED2A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1817">ED2A</span></span></td>
  <td><span data-ttu-id="d3f5b-1818">eSIM</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1818">eSIM</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed2b.png" alt="eSIMNoProfile" /></td>
  <td><span data-ttu-id="d3f5b-1819">ED2B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1819">ED2B</span></span></td>
  <td><span data-ttu-id="d3f5b-1820">eSIMNoProfile</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1820">eSIMNoProfile</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed2c.png" alt="eSIMLocked" /></td>
  <td><span data-ttu-id="d3f5b-1821">ED2C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1821">ED2C</span></span></td>
  <td><span data-ttu-id="d3f5b-1822">eSIMLocked</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1822">eSIMLocked</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed2d.png" alt="eSIMBusy" /></td>
  <td><span data-ttu-id="d3f5b-1823">ED2D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1823">ED2D</span></span></td>
  <td><span data-ttu-id="d3f5b-1824">eSIMBusy</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1824">eSIMBusy</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed2e.png" alt="SignalError" /></td>
  <td><span data-ttu-id="d3f5b-1825">ED2E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1825">ED2E</span></span></td>
  <td><span data-ttu-id="d3f5b-1826">SignalError</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1826">SignalError</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed2f.png" alt="StreamingEnterprise" /></td>
  <td><span data-ttu-id="d3f5b-1827">ED2F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1827">ED2F</span></span></td>
  <td><span data-ttu-id="d3f5b-1828">StreamingEnterprise</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1828">StreamingEnterprise</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed30.png" alt="Headphone0" /></td>
  <td><span data-ttu-id="d3f5b-1829">ED30</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1829">ED30</span></span></td>
  <td><span data-ttu-id="d3f5b-1830">Headphone0</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1830">Headphone0</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed31.png" alt="Headphone1" /></td>
  <td><span data-ttu-id="d3f5b-1831">ED31</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1831">ED31</span></span></td>
  <td><span data-ttu-id="d3f5b-1832">Headphone1</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1832">Headphone1</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed32.png" alt="Headphone2" /></td>
  <td><span data-ttu-id="d3f5b-1833">ED32</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1833">ED32</span></span></td>
  <td><span data-ttu-id="d3f5b-1834">Headphone2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1834">Headphone2</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed33.png" alt="Headphone3" /></td>
  <td><span data-ttu-id="d3f5b-1835">ED33</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1835">ED33</span></span></td>
  <td><span data-ttu-id="d3f5b-1836">Headphone3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1836">Headphone3</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed39.png" alt="KeyboardBrightness" /></td>
  <td><span data-ttu-id="d3f5b-1837">ED39</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1837">ED39</span></span></td>
  <td><span data-ttu-id="d3f5b-1838">KeyboardBrightness</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1838">KeyboardBrightness</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed3a.png" alt="KeyboardLowerBrightness" /></td>
  <td><span data-ttu-id="d3f5b-1839">ED3A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1839">ED3A</span></span></td>
  <td><span data-ttu-id="d3f5b-1840">KeyboardLowerBrightness</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1840">KeyboardLowerBrightness</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed3c.png" alt="SkipBack10" /></td>
  <td><span data-ttu-id="d3f5b-1841">ED3C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1841">ED3C</span></span></td>
  <td><span data-ttu-id="d3f5b-1842">SkipBack10</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1842">SkipBack10</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed3d.png" alt="SkipForward30" /></td>
  <td><span data-ttu-id="d3f5b-1843">ED3D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1843">ED3D</span></span></td>
  <td><span data-ttu-id="d3f5b-1844">SkipForward30</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1844">SkipForward30</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed41.png" alt="TreeFolderFolder" /></td>
  <td><span data-ttu-id="d3f5b-1845">ED41</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1845">ED41</span></span></td>
  <td><span data-ttu-id="d3f5b-1846">TreeFolderFolder</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1846">TreeFolderFolder</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed42.png" alt="TreeFolderFolderFill" /></td>
  <td><span data-ttu-id="d3f5b-1847">ED42</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1847">ED42</span></span></td>
  <td><span data-ttu-id="d3f5b-1848">TreeFolderFolderFill</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1848">TreeFolderFolderFill</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed43.png" alt="TreeFolderFolderOpen" /></td>
  <td><span data-ttu-id="d3f5b-1849">ED43</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1849">ED43</span></span></td>
  <td><span data-ttu-id="d3f5b-1850">TreeFolderFolderOpen</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1850">TreeFolderFolderOpen</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed44.png" alt="TreeFolderFolderOpenFill" /></td>
  <td><span data-ttu-id="d3f5b-1851">ED44</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1851">ED44</span></span></td>
  <td><span data-ttu-id="d3f5b-1852">TreeFolderFolderOpenFill</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1852">TreeFolderFolderOpenFill</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed47.png" alt="MultimediaDMP" /></td>
  <td><span data-ttu-id="d3f5b-1853">ED47</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1853">ED47</span></span></td>
  <td><span data-ttu-id="d3f5b-1854">MultimediaDMP</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1854">MultimediaDMP</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed4c.png" alt="KeyboardOneHanded" /></td>
  <td><span data-ttu-id="d3f5b-1855">ED4C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1855">ED4C</span></span></td>
  <td><span data-ttu-id="d3f5b-1856">KeyboardOneHanded</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1856">KeyboardOneHanded</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed4d.png" alt="Narrator" /></td>
  <td><span data-ttu-id="d3f5b-1857">ED4D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1857">ED4D</span></span></td>
  <td><span data-ttu-id="d3f5b-1858">Sprachausgabe</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1858">Narrator</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed53.png" alt="EmojiTabPeople" /></td>
  <td><span data-ttu-id="d3f5b-1859">ED53</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1859">ED53</span></span></td>
  <td><span data-ttu-id="d3f5b-1860">EmojiTabPeople</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1860">EmojiTabPeople</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed54.png" alt="EmojiTabSmilesAnimals" /></td>
  <td><span data-ttu-id="d3f5b-1861">ED54</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1861">ED54</span></span></td>
  <td><span data-ttu-id="d3f5b-1862">EmojiTabSmilesAnimals</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1862">EmojiTabSmilesAnimals</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed55.png" alt="EmojiTabCelebrationObjects" /></td>
  <td><span data-ttu-id="d3f5b-1863">ED55</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1863">ED55</span></span></td>
  <td><span data-ttu-id="d3f5b-1864">EmojiTabCelebrationObjects</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1864">EmojiTabCelebrationObjects</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed56.png" alt="EmojiTabFoodPlants" /></td>
  <td><span data-ttu-id="d3f5b-1865">ED56</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1865">ED56</span></span></td>
  <td><span data-ttu-id="d3f5b-1866">EmojiTabFoodPlants</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1866">EmojiTabFoodPlants</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed57.png" alt="EmojiTabTransitPlaces" /></td>
  <td><span data-ttu-id="d3f5b-1867">ED57</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1867">ED57</span></span></td>
  <td><span data-ttu-id="d3f5b-1868">EmojiTabTransitPlaces</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1868">EmojiTabTransitPlaces</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed58.png" alt="EmojiTabSymbols" /></td>
  <td><span data-ttu-id="d3f5b-1869">ED58</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1869">ED58</span></span></td>
  <td><span data-ttu-id="d3f5b-1870">EmojiTabSymbols</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1870">EmojiTabSymbols</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed59.png" alt="EmojiTabTextSmiles" /></td>
  <td><span data-ttu-id="d3f5b-1871">ED59</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1871">ED59</span></span></td>
  <td><span data-ttu-id="d3f5b-1872">EmojiTabTextSmiles</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1872">EmojiTabTextSmiles</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed5a.png" alt="EmojiTabFavorites" /></td>
  <td><span data-ttu-id="d3f5b-1873">ED5A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1873">ED5A</span></span></td>
  <td><span data-ttu-id="d3f5b-1874">EmojiTabFavorites</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1874">EmojiTabFavorites</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed5b.png" alt="EmojiSwatch" /></td>
  <td><span data-ttu-id="d3f5b-1875">ED5B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1875">ED5B</span></span></td>
  <td><span data-ttu-id="d3f5b-1876">EmojiSwatch</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1876">EmojiSwatch</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed5c.png" alt="ConnectApp" /></td>
  <td><span data-ttu-id="d3f5b-1877">ED5C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1877">ED5C</span></span></td>
  <td><span data-ttu-id="d3f5b-1878">ConnectApp</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1878">ConnectApp</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed5d.png" alt="CompanionDeviceFramework" /></td>
  <td><span data-ttu-id="d3f5b-1879">ED5D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1879">ED5D</span></span></td>
  <td><span data-ttu-id="d3f5b-1880">CompanionDeviceFramework</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1880">CompanionDeviceFramework</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed5e.png" alt="Ruler" /></td>
  <td><span data-ttu-id="d3f5b-1881">ED5E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1881">ED5E</span></span></td>
  <td><span data-ttu-id="d3f5b-1882">Ruler</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1882">Ruler</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed5f.png" alt="FingerInking" /></td>
  <td><span data-ttu-id="d3f5b-1883">ED5F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1883">ED5F</span></span></td>
  <td><span data-ttu-id="d3f5b-1884">FingerInking</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1884">FingerInking</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed60.png" alt="StrokeErase" /></td>
  <td><span data-ttu-id="d3f5b-1885">ED60</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1885">ED60</span></span></td>
  <td><span data-ttu-id="d3f5b-1886">StrokeErase</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1886">StrokeErase</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed61.png" alt="PointErase" /></td>
  <td><span data-ttu-id="d3f5b-1887">ED61</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1887">ED61</span></span></td>
  <td><span data-ttu-id="d3f5b-1888">PointErase</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1888">PointErase</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed62.png" alt="ClearAllInk" /></td>
  <td><span data-ttu-id="d3f5b-1889">ED62</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1889">ED62</span></span></td>
  <td><span data-ttu-id="d3f5b-1890">ClearAllInk</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1890">ClearAllInk</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed63.png" alt="Pencil" /></td>
  <td><span data-ttu-id="d3f5b-1891">ED63</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1891">ED63</span></span></td>
  <td><span data-ttu-id="d3f5b-1892">Pencil</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1892">Pencil</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed64.png" alt="Marker" /></td>
  <td><span data-ttu-id="d3f5b-1893">ED64</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1893">ED64</span></span></td>
  <td><span data-ttu-id="d3f5b-1894">Marker</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1894">Marker</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed65.png" alt="InkingCaret" /></td>
  <td><span data-ttu-id="d3f5b-1895">ED65</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1895">ED65</span></span></td>
  <td><span data-ttu-id="d3f5b-1896">InkingCaret</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1896">InkingCaret</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed66.png" alt="InkingColorOutline" /></td>
  <td><span data-ttu-id="d3f5b-1897">ED66</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1897">ED66</span></span></td>
  <td><span data-ttu-id="d3f5b-1898">InkingColorOutline</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1898">InkingColorOutline</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ed67.png" alt="InkingColorFill" /></td>
  <td><span data-ttu-id="d3f5b-1899">ED67</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1899">ED67</span></span></td>
  <td><span data-ttu-id="d3f5b-1900">InkingColorFill</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1900">InkingColorFill</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eda2.png" alt="HardDrive" /></td>
  <td><span data-ttu-id="d3f5b-1901">EDA2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1901">EDA2</span></span></td>
  <td><span data-ttu-id="d3f5b-1902">HardDrive</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1902">HardDrive</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eda3.png" alt="NetworkAdapter" /></td>
  <td><span data-ttu-id="d3f5b-1903">EDA3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1903">EDA3</span></span></td>
  <td><span data-ttu-id="d3f5b-1904">NetworkAdapter</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1904">NetworkAdapter</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eda4.png" alt="Touchscreen" /></td>
  <td><span data-ttu-id="d3f5b-1905">EDA4</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1905">EDA4</span></span></td>
  <td><span data-ttu-id="d3f5b-1906">Touchscreen</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1906">Touchscreen</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eda5.png" alt="NetworkPrinter" /></td>
  <td><span data-ttu-id="d3f5b-1907">EDA5</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1907">EDA5</span></span></td>
  <td><span data-ttu-id="d3f5b-1908">NetworkPrinter</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1908">NetworkPrinter</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eda6.png" alt="CloudPrinter" /></td>
  <td><span data-ttu-id="d3f5b-1909">EDA6</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1909">EDA6</span></span></td>
  <td><span data-ttu-id="d3f5b-1910">CloudPrinter</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1910">CloudPrinter</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eda7.png" alt="KeyboardShortcut" /></td>
  <td><span data-ttu-id="d3f5b-1911">EDA7</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1911">EDA7</span></span></td>
  <td><span data-ttu-id="d3f5b-1912">KeyboardShortcut</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1912">KeyboardShortcut</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eda8.png" alt="BrushSize" /></td>
  <td><span data-ttu-id="d3f5b-1913">EDA8</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1913">EDA8</span></span></td>
  <td><span data-ttu-id="d3f5b-1914">BrushSize</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1914">BrushSize</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/eda9.png" alt="NarratorForward" /></td>
  <td><span data-ttu-id="d3f5b-1915">EDA9</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1915">EDA9</span></span></td>
  <td><span data-ttu-id="d3f5b-1916">NarratorForward</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1916">NarratorForward</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/edaa.png" alt="NarratorForwardMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1917">EDAA</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1917">EDAA</span></span></td>
  <td><span data-ttu-id="d3f5b-1918">NarratorForwardMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1918">NarratorForwardMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/edab.png" alt="SyncBadge12" /></td>
  <td><span data-ttu-id="d3f5b-1919">EDAB</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1919">EDAB</span></span></td>
  <td><span data-ttu-id="d3f5b-1920">SyncBadge12</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1920">SyncBadge12</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/edac.png" alt="RingerBadge12" /></td>
  <td><span data-ttu-id="d3f5b-1921">EDAC</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1921">EDAC</span></span></td>
  <td><span data-ttu-id="d3f5b-1922">RingerBadge12</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1922">RingerBadge12</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/edad.png" alt="AsteriskBadge12" /></td>
  <td><span data-ttu-id="d3f5b-1923">EDAD</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1923">EDAD</span></span></td>
  <td><span data-ttu-id="d3f5b-1924">AsteriskBadge12</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1924">AsteriskBadge12</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/edae.png" alt="ErrorBadge12" /></td>
  <td><span data-ttu-id="d3f5b-1925">EDAE</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1925">EDAE</span></span></td>
  <td><span data-ttu-id="d3f5b-1926">ErrorBadge12</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1926">ErrorBadge12</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/edaf.png" alt="CircleRingBadge12" /></td>
  <td><span data-ttu-id="d3f5b-1927">EDAF</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1927">EDAF</span></span></td>
  <td><span data-ttu-id="d3f5b-1928">CircleRingBadge12</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1928">CircleRingBadge12</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/edb0.png" alt="CircleFillBadge12" /></td>
  <td><span data-ttu-id="d3f5b-1929">EDB0</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1929">EDB0</span></span></td>
  <td><span data-ttu-id="d3f5b-1930">CircleFillBadge12</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1930">CircleFillBadge12</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/edb1.png" alt="ImportantBadge12" /></td>
  <td><span data-ttu-id="d3f5b-1931">EDB1</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1931">EDB1</span></span></td>
  <td><span data-ttu-id="d3f5b-1932">ImportantBadge12</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1932">ImportantBadge12</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/edb3.png" alt="MailBadge12" /></td>
  <td><span data-ttu-id="d3f5b-1933">EDB3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1933">EDB3</span></span></td>
  <td><span data-ttu-id="d3f5b-1934">MailBadge12</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1934">MailBadge12</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/edb4.png" alt="PauseBadge12" /></td>
  <td><span data-ttu-id="d3f5b-1935">EDB4</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1935">EDB4</span></span></td>
  <td><span data-ttu-id="d3f5b-1936">PauseBadge12</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1936">PauseBadge12</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/edb5.png" alt="PlayBadge12" /></td>
  <td><span data-ttu-id="d3f5b-1937">EDB5</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1937">EDB5</span></span></td>
  <td><span data-ttu-id="d3f5b-1938">PlayBadge12</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1938">PlayBadge12</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/edc6.png" alt="PenWorkspace" /></td>
  <td><span data-ttu-id="d3f5b-1939">EDC6</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1939">EDC6</span></span></td>
  <td><span data-ttu-id="d3f5b-1940">PenWorkspace</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1940">PenWorkspace</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ede1.png" alt="Export" /></td>
  <td><span data-ttu-id="d3f5b-1941">EDE1</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1941">EDE1</span></span></td>
  <td><span data-ttu-id="d3f5b-1942">Export</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1942">Export</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ede2.png" alt="ExportMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1943">EDE2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1943">EDE2</span></span></td>
  <td><span data-ttu-id="d3f5b-1944">ExportMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1944">ExportMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/edfb.png" alt="CaligraphyPen" /></td>
  <td><span data-ttu-id="d3f5b-1945">EDFB</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1945">EDFB</span></span></td>
  <td><span data-ttu-id="d3f5b-1946">CaligraphyPen</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1946">CaligraphyPen</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ee35.png" alt="ReplyMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1947">EE35</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1947">EE35</span></span></td>
  <td><span data-ttu-id="d3f5b-1948">ReplyMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1948">ReplyMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ee3f.png" alt="LockscreenDesktop" /></td>
  <td><span data-ttu-id="d3f5b-1949">EE3F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1949">EE3F</span></span></td>
  <td><span data-ttu-id="d3f5b-1950">LockscreenDesktop</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1950">LockscreenDesktop</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ee40.png" alt="Multitask16" /></td>
  <td><span data-ttu-id="d3f5b-1951">EE40</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1951">EE40</span></span></td>
  <td><span data-ttu-id="d3f5b-1952">Multitask16</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1952">Multitask16</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ee4a.png" alt="Play36" /></td>
  <td><span data-ttu-id="d3f5b-1953">EE4A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1953">EE4A</span></span></td>
  <td><span data-ttu-id="d3f5b-1954">Play36</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1954">Play36</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ee56.png" alt="PenPalette" /></td>
  <td><span data-ttu-id="d3f5b-1955">EE56</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1955">EE56</span></span></td>
  <td><span data-ttu-id="d3f5b-1956">PenPalette</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1956">PenPalette</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ee57.png" alt="GuestUser" /></td>
  <td><span data-ttu-id="d3f5b-1957">EE57</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1957">EE57</span></span></td>
  <td><span data-ttu-id="d3f5b-1958">GuestUser</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1958">GuestUser</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ee63.png" alt="SettingsBattery" /></td>
  <td><span data-ttu-id="d3f5b-1959">EE63</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1959">EE63</span></span></td>
  <td><span data-ttu-id="d3f5b-1960">SettingsBattery</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1960">SettingsBattery</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ee64.png" alt="TaskbarPhone" /></td>
  <td><span data-ttu-id="d3f5b-1961">EE64</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1961">EE64</span></span></td>
  <td><span data-ttu-id="d3f5b-1962">TaskbarPhone</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1962">TaskbarPhone</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ee65.png" alt="LockScreenGlance" /></td>
  <td><span data-ttu-id="d3f5b-1963">EE65</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1963">EE65</span></span></td>
  <td><span data-ttu-id="d3f5b-1964">LockScreenGlance</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1964">LockScreenGlance</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ee71.png" alt="ImageExport" /></td>
  <td><span data-ttu-id="d3f5b-1965">EE71</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1965">EE71</span></span></td>
  <td><span data-ttu-id="d3f5b-1966">ImageExport</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1966">ImageExport</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ee77.png" alt="WifiEthernet" /></td>
  <td><span data-ttu-id="d3f5b-1967">EE77</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1967">EE77</span></span></td>
  <td><span data-ttu-id="d3f5b-1968">WifiEthernet</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1968">WifiEthernet</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ee79.png" alt="ActionCenterQuiet" /></td>
  <td><span data-ttu-id="d3f5b-1969">EE79</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1969">EE79</span></span></td>
  <td><span data-ttu-id="d3f5b-1970">ActionCenterQuiet</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1970">ActionCenterQuiet</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ee7a.png" alt="ActionCenterQuietNotification" /></td>
  <td><span data-ttu-id="d3f5b-1971">EE7A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1971">EE7A</span></span></td>
  <td><span data-ttu-id="d3f5b-1972">ActionCenterQuietNotification</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1972">ActionCenterQuietNotification</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ee92.png" alt="TrackersMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1973">EE92</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1973">EE92</span></span></td>
  <td><span data-ttu-id="d3f5b-1974">TrackersMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1974">TrackersMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ee93.png" alt="DateTimeMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1975">EE93</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1975">EE93</span></span></td>
  <td><span data-ttu-id="d3f5b-1976">DateTimeMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1976">DateTimeMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ee94.png" alt="Wheel" /></td>
  <td><span data-ttu-id="d3f5b-1977">EE94</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1977">EE94</span></span></td>
  <td><span data-ttu-id="d3f5b-1978">Rad</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1978">Wheel</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ef15.png" alt="PenWorkspaceMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1979">EF15</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1979">EF15</span></span></td>
  <td><span data-ttu-id="d3f5b-1980">PenWorkspaceMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1980">PenWorkspaceMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ef16.png" alt="PenPaletteMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1981">EF16</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1981">EF16</span></span></td>
  <td><span data-ttu-id="d3f5b-1982">PenPaletteMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1982">PenPaletteMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ef17.png" alt="StrokeEraseMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1983">EF17</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1983">EF17</span></span></td>
  <td><span data-ttu-id="d3f5b-1984">StrokeEraseMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1984">StrokeEraseMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ef18.png" alt="PointEraseMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1985">EF18</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1985">EF18</span></span></td>
  <td><span data-ttu-id="d3f5b-1986">PointEraseMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1986">PointEraseMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ef19.png" alt="ClearAllInkMirrored" /></td>
  <td><span data-ttu-id="d3f5b-1987">EF19</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1987">EF19</span></span></td>
  <td><span data-ttu-id="d3f5b-1988">ClearAllInkMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1988">ClearAllInkMirrored</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ef1f.png" alt="BackgroundToggle" /></td>
  <td><span data-ttu-id="d3f5b-1989">EF1F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1989">EF1F</span></span></td>
  <td><span data-ttu-id="d3f5b-1990">BackgroundToggle</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1990">BackgroundToggle</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/ef20.png" alt="Marquee" /></td>
  <td><span data-ttu-id="d3f5b-1991">EF20</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1991">EF20</span></span></td>
  <td><span data-ttu-id="d3f5b-1992">Marquee</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1992">Marquee</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/f003.png" alt="Relationship" /></td><td><span data-ttu-id="d3f5b-1993">F003</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1993">F003</span></span></td><td><span data-ttu-id="d3f5b-1994">Beziehung</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1994">Relationship</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f080.png" alt="DefaultAPN" /></td><td><span data-ttu-id="d3f5b-1995">F080</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1995">F080</span></span></td><td><span data-ttu-id="d3f5b-1996">DefaultAPN</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1996">DefaultAPN</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f081.png" alt="UserAPN " /></td><td><span data-ttu-id="d3f5b-1997">F081</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1997">F081</span></span></td><td><span data-ttu-id="d3f5b-1998">UserAPN</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1998">UserAPN</span></span> </td></tr>
<tr><td><img src="images/segoe-mdl/f085.png" alt="DoublePinyin" /></td><td><span data-ttu-id="d3f5b-1999">F085</span><span class="sxs-lookup"><span data-stu-id="d3f5b-1999">F085</span></span></td><td><span data-ttu-id="d3f5b-2000">DoublePinyin</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2000">DoublePinyin</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f08c.png" alt="BlueLight" /></td><td><span data-ttu-id="d3f5b-2001">F08C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2001">F08C</span></span></td><td><span data-ttu-id="d3f5b-2002">BlueLight</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2002">BlueLight</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f093.png" alt="ButtonA" /></td><td><span data-ttu-id="d3f5b-2003">F093</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2003">F093</span></span></td><td><span data-ttu-id="d3f5b-2004">ButtonA</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2004">ButtonA</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f094.png" alt="ButtonB" /></td><td><span data-ttu-id="d3f5b-2005">F094</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2005">F094</span></span></td><td><span data-ttu-id="d3f5b-2006">ButtonB</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2006">ButtonB</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f095.png" alt="ButtonY" /></td><td><span data-ttu-id="d3f5b-2007">F095</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2007">F095</span></span></td><td><span data-ttu-id="d3f5b-2008">ButtonY</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2008">ButtonY</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f096.png" alt="ButtonX" /></td><td><span data-ttu-id="d3f5b-2009">F096</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2009">F096</span></span></td><td><span data-ttu-id="d3f5b-2010">ButtonX</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2010">ButtonX</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0ad.png" alt="ArrowUp8" /></td><td><span data-ttu-id="d3f5b-2011">F0AD</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2011">F0AD</span></span></td><td><span data-ttu-id="d3f5b-2012">ArrowUp8</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2012">ArrowUp8</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0ae.png" alt="ArrowDown8" /></td><td><span data-ttu-id="d3f5b-2013">F0AE</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2013">F0AE</span></span></td><td><span data-ttu-id="d3f5b-2014">ArrowDown8</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2014">ArrowDown8</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0af.png" alt="ArrowRight8" /></td><td><span data-ttu-id="d3f5b-2015">F0AF</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2015">F0AF</span></span></td><td><span data-ttu-id="d3f5b-2016">ArrowRight8</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2016">ArrowRight8</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0b0.png" alt="ArrowLeft8" /></td><td><span data-ttu-id="d3f5b-2017">F0B0</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2017">F0B0</span></span></td><td><span data-ttu-id="d3f5b-2018">ArrowLeft8</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2018">ArrowLeft8</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0b2.png" alt="QuarentinedItems" /></td><td><span data-ttu-id="d3f5b-2019">F0B2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2019">F0B2</span></span></td><td><span data-ttu-id="d3f5b-2020">QuarentinedItems</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2020">QuarentinedItems</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0b3.png" alt="QuarentinedItemsMirrored" /></td><td><span data-ttu-id="d3f5b-2021">F0B3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2021">F0B3</span></span></td><td><span data-ttu-id="d3f5b-2022">QuarentinedItemsMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2022">QuarentinedItemsMirrored</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0b4.png" alt="Protractor" /></td><td><span data-ttu-id="d3f5b-2023">F0B4</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2023">F0B4</span></span></td><td><span data-ttu-id="d3f5b-2024">Winkelmesser</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2024">Protractor</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0b5.png" alt="ChecklistMirrored" /></td><td><span data-ttu-id="d3f5b-2025">F0B5</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2025">F0B5</span></span></td><td><span data-ttu-id="d3f5b-2026">ChecklistMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2026">ChecklistMirrored</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0b6.png" alt="StatusCircle7" /></td><td><span data-ttu-id="d3f5b-2027">F0B6</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2027">F0B6</span></span></td><td><span data-ttu-id="d3f5b-2028">StatusCircle7</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2028">StatusCircle7</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0b7.png" alt="StatusCheckmark7" /></td><td><span data-ttu-id="d3f5b-2029">F0B7</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2029">F0B7</span></span></td><td><span data-ttu-id="d3f5b-2030">StatusCheckmark7</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2030">StatusCheckmark7</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0b8.png" alt="StatusErrorCircle7" /></td><td><span data-ttu-id="d3f5b-2031">F0B8</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2031">F0B8</span></span></td><td><span data-ttu-id="d3f5b-2032">StatusErrorCircle7</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2032">StatusErrorCircle7</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0b9.png" alt="Connected" /></td><td><span data-ttu-id="d3f5b-2033">F0B9</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2033">F0B9</span></span></td><td><span data-ttu-id="d3f5b-2034">Connected</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2034">Connected</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0c6.png" alt="PencilFill" /></td><td><span data-ttu-id="d3f5b-2035">F0C6</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2035">F0C6</span></span></td><td><span data-ttu-id="d3f5b-2036">PencilFill</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2036">PencilFill</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0c7.png" alt="CalligraphyFill" /></td><td><span data-ttu-id="d3f5b-2037">F0C7</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2037">F0C7</span></span></td><td><span data-ttu-id="d3f5b-2038">CalligraphyFill</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2038">CalligraphyFill</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0ca.png" alt="QuarterStarLeft" /></td><td><span data-ttu-id="d3f5b-2039">F0CA</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2039">F0CA</span></span></td><td><span data-ttu-id="d3f5b-2040">QuarterStarLeft</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2040">QuarterStarLeft</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0cb.png" alt="QuarterStarRight" /></td><td><span data-ttu-id="d3f5b-2041">F0CB</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2041">F0CB</span></span></td><td><span data-ttu-id="d3f5b-2042">QuarterStarRight</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2042">QuarterStarRight</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0cc.png" alt="ThreeQuarterStarLeft" /></td><td><span data-ttu-id="d3f5b-2043">F0CC</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2043">F0CC</span></span></td><td><span data-ttu-id="d3f5b-2044">ThreeQuarterStarLeft</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2044">ThreeQuarterStarLeft</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0cd.png" alt="ThreeQuarterStarRight" /></td><td><span data-ttu-id="d3f5b-2045">F0CD</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2045">F0CD</span></span></td><td><span data-ttu-id="d3f5b-2046">ThreeQuarterStarRight</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2046">ThreeQuarterStarRight</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0ce.png" alt="QuietHoursBadge12" /></td><td><span data-ttu-id="d3f5b-2047">F0CE</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2047">F0CE</span></span></td><td><span data-ttu-id="d3f5b-2048">QuietHoursBadge12</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2048">QuietHoursBadge12</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0d2.png" alt="BackMirrored" /></td><td><span data-ttu-id="d3f5b-2049">F0D2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2049">F0D2</span></span></td><td><span data-ttu-id="d3f5b-2050">BackMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2050">BackMirrored</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0d3.png" alt="ForwardMirrored" /></td><td><span data-ttu-id="d3f5b-2051">F0D3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2051">F0D3</span></span></td><td><span data-ttu-id="d3f5b-2052">ForwardMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2052">ForwardMirrored</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0d5.png" alt="ChromeBackContrast" /></td><td><span data-ttu-id="d3f5b-2053">F0D5</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2053">F0D5</span></span></td><td><span data-ttu-id="d3f5b-2054">ChromeBackContrast</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2054">ChromeBackContrast</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0d6.png" alt="ChromeBackContrastMirrored" /></td><td><span data-ttu-id="d3f5b-2055">F0D6</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2055">F0D6</span></span></td><td><span data-ttu-id="d3f5b-2056">ChromeBackContrastMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2056">ChromeBackContrastMirrored</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0d7.png" alt="ChromeBackToWindowContrast" /></td><td><span data-ttu-id="d3f5b-2057">F0D7</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2057">F0D7</span></span></td><td><span data-ttu-id="d3f5b-2058">ChromeBackToWindowContrast</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2058">ChromeBackToWindowContrast</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0d8.png" alt="ChromeFullScreenContrast" /></td><td><span data-ttu-id="d3f5b-2059">F0D8</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2059">F0D8</span></span></td><td><span data-ttu-id="d3f5b-2060">ChromeFullScreenContrast</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2060">ChromeFullScreenContrast</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0e2.png" alt="GridView" /></td><td><span data-ttu-id="d3f5b-2061">F0E2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2061">F0E2</span></span></td><td><span data-ttu-id="d3f5b-2062">GridView</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2062">GridView</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0e3.png" alt="ClipboardList" /></td><td><span data-ttu-id="d3f5b-2063">F0E3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2063">F0E3</span></span></td><td><span data-ttu-id="d3f5b-2064">ClipboardList</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2064">ClipboardList</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0e4.png" alt="ClipboardListMirrored" /></td><td><span data-ttu-id="d3f5b-2065">F0E4</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2065">F0E4</span></span></td><td><span data-ttu-id="d3f5b-2066">ClipboardListMirrored</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2066">ClipboardListMirrored</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0e5.png" alt="OutlineQuarterStarLeft" /></td><td><span data-ttu-id="d3f5b-2067">F0E5</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2067">F0E5</span></span></td><td><span data-ttu-id="d3f5b-2068">OutlineQuarterStarLeft</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2068">OutlineQuarterStarLeft</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0e6.png" alt="OutlineQuarterStarRight" /></td><td><span data-ttu-id="d3f5b-2069">F0E6</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2069">F0E6</span></span></td><td><span data-ttu-id="d3f5b-2070">OutlineQuarterStarRight</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2070">OutlineQuarterStarRight</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0e7.png" alt="OutlineHalfStarLeft" /></td><td><span data-ttu-id="d3f5b-2071">F0E7</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2071">F0E7</span></span></td><td><span data-ttu-id="d3f5b-2072">OutlineHalfStarLeft</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2072">OutlineHalfStarLeft</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0e8.png" alt="OutlineHalfStarRight" /></td><td><span data-ttu-id="d3f5b-2073">F0E8</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2073">F0E8</span></span></td><td><span data-ttu-id="d3f5b-2074">OutlineHalfStarRight</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2074">OutlineHalfStarRight</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0e9.png" alt="OutlineThreeQuarterStarLeft" /></td><td><span data-ttu-id="d3f5b-2075">F0E9</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2075">F0E9</span></span></td><td><span data-ttu-id="d3f5b-2076">OutlineThreeQuarterStarLeft</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2076">OutlineThreeQuarterStarLeft</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0ea.png" alt="OutlineThreeQuarterStarRight" /></td><td><span data-ttu-id="d3f5b-2077">F0EA</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2077">F0EA</span></span></td><td><span data-ttu-id="d3f5b-2078">OutlineThreeQuarterStarRight</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2078">OutlineThreeQuarterStarRight</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0eb.png" alt="SpatialVolume0" /></td><td><span data-ttu-id="d3f5b-2079">F0EB</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2079">F0EB</span></span></td><td><span data-ttu-id="d3f5b-2080">SpatialVolume0</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2080">SpatialVolume0</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0ec.png" alt="SpatialVolume1" /></td><td><span data-ttu-id="d3f5b-2081">F0EC</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2081">F0EC</span></span></td><td><span data-ttu-id="d3f5b-2082">SpatialVolume1</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2082">SpatialVolume1</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0ed.png" alt="SpatialVolume2" /></td><td><span data-ttu-id="d3f5b-2083">F0ED</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2083">F0ED</span></span></td><td><span data-ttu-id="d3f5b-2084">SpatialVolume2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2084">SpatialVolume2</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0ee.png" alt="SpatialVolume3" /></td><td><span data-ttu-id="d3f5b-2085">F0EE</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2085">F0EE</span></span></td><td><span data-ttu-id="d3f5b-2086">SpatialVolume3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2086">SpatialVolume3</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0f7.png" alt="OutlineStarLeftHalf" /></td><td><span data-ttu-id="d3f5b-2087">F0F7</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2087">F0F7</span></span></td><td><span data-ttu-id="d3f5b-2088">OutlineStarLeftHalf</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2088">OutlineStarLeftHalf</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0f8.png" alt="OutlineStarRightHalf" /></td><td><span data-ttu-id="d3f5b-2089">F0F8</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2089">F0F8</span></span></td><td><span data-ttu-id="d3f5b-2090">OutlineStarRightHalf</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2090">OutlineStarRightHalf</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0f9.png" alt="ChromeAnnotateContrast" /></td><td><span data-ttu-id="d3f5b-2091">F0F9</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2091">F0F9</span></span></td><td><span data-ttu-id="d3f5b-2092">ChromeAnnotateContrast</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2092">ChromeAnnotateContrast</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f0fb.png" alt="DefenderBadge12" /></td><td><span data-ttu-id="d3f5b-2093">F0FB</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2093">F0FB</span></span></td><td><span data-ttu-id="d3f5b-2094">DefenderBadge12</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2094">DefenderBadge12</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f103.png" alt="DetachablePC" /></td><td><span data-ttu-id="d3f5b-2095">F103</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2095">F103</span></span></td><td><span data-ttu-id="d3f5b-2096">DetachablePC</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2096">DetachablePC</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f108.png" alt="LeftStick" /></td><td><span data-ttu-id="d3f5b-2097">F108</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2097">F108</span></span></td><td><span data-ttu-id="d3f5b-2098">LeftStick</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2098">LeftStick</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f109.png" alt="RightStick" /></td><td><span data-ttu-id="d3f5b-2099">F109</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2099">F109</span></span></td><td><span data-ttu-id="d3f5b-2100">RightStick</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2100">RightStick</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f10a.png" alt="TriggerLeft" /></td><td><span data-ttu-id="d3f5b-2101">F10A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2101">F10A</span></span></td><td><span data-ttu-id="d3f5b-2102">TriggerLeft</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2102">TriggerLeft</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f10b.png" alt="TriggerRight" /></td><td><span data-ttu-id="d3f5b-2103">F10B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2103">F10B</span></span></td><td><span data-ttu-id="d3f5b-2104">TriggerRight</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2104">TriggerRight</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f10c.png" alt="BumperLeft" /></td><td><span data-ttu-id="d3f5b-2105">F10C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2105">F10C</span></span></td><td><span data-ttu-id="d3f5b-2106">BumperLeft</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2106">BumperLeft</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f10d.png" alt="BumperRight" /></td><td><span data-ttu-id="d3f5b-2107">F10D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2107">F10D</span></span></td><td><span data-ttu-id="d3f5b-2108">BumperRight</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2108">BumperRight</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f10e.png" alt="Dpad" /></td><td><span data-ttu-id="d3f5b-2109">F10E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2109">F10E</span></span></td><td><span data-ttu-id="d3f5b-2110">Dpad</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2110">Dpad</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f110.png" alt="EnglishPunctuation" /></td><td><span data-ttu-id="d3f5b-2111">F110</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2111">F110</span></span></td><td><span data-ttu-id="d3f5b-2112">EnglishPunctuation</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2112">EnglishPunctuation</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f111.png" alt="ChinesePunctuation" /></td><td><span data-ttu-id="d3f5b-2113">F111</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2113">F111</span></span></td><td><span data-ttu-id="d3f5b-2114">ChinesePunctuation</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2114">ChinesePunctuation</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f119.png" alt="HMD" /></td><td><span data-ttu-id="d3f5b-2115">F119</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2115">F119</span></span></td><td><span data-ttu-id="d3f5b-2116">HMD</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2116">HMD</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f126.png" alt="PaginationDotOutline10" /></td><td><span data-ttu-id="d3f5b-2117">F126</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2117">F126</span></span></td><td><span data-ttu-id="d3f5b-2118">PaginationDotOutline10</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2118">PaginationDotOutline10</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f127.png" alt="PaginationDotSolid10" /></td><td><span data-ttu-id="d3f5b-2119">F127</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2119">F127</span></span></td><td><span data-ttu-id="d3f5b-2120">PaginationDotSolid10</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2120">PaginationDotSolid10</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f128.png" alt="StrokeErase2" /></td><td><span data-ttu-id="d3f5b-2121">F128</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2121">F128</span></span></td><td><span data-ttu-id="d3f5b-2122">StrokeErase2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2122">StrokeErase2</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f129.png" alt="SmallErase" /></td><td><span data-ttu-id="d3f5b-2123">F129</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2123">F129</span></span></td><td><span data-ttu-id="d3f5b-2124">SmallErase</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2124">SmallErase</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f12a.png" alt="LargeErase" /></td><td><span data-ttu-id="d3f5b-2125">F12A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2125">F12A</span></span></td><td><span data-ttu-id="d3f5b-2126">LargeErase</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2126">LargeErase</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f12b.png" alt="FolderHorizontal" /></td><td><span data-ttu-id="d3f5b-2127">F12B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2127">F12B</span></span></td><td><span data-ttu-id="d3f5b-2128">FolderHorizontal</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2128">FolderHorizontal</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f12e.png" alt="MicrophoneListening" /></td><td><span data-ttu-id="d3f5b-2129">F12E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2129">F12E</span></span></td><td><span data-ttu-id="d3f5b-2130">MicrophoneListening</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2130">MicrophoneListening</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f12f.png" alt="StatusExclamationCircle7 " /></td><td><span data-ttu-id="d3f5b-2131">F12F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2131">F12F</span></span></td><td><span data-ttu-id="d3f5b-2132">StatusExclamationCircle7</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2132">StatusExclamationCircle7</span></span> </td></tr>
<tr><td><img src="images/segoe-mdl/f136.png" alt="StatusCircleOuter" /></td><td><span data-ttu-id="d3f5b-2133">F136</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2133">F136</span></span></td><td><span data-ttu-id="d3f5b-2134">StatusCircleOuter</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2134">StatusCircleOuter</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f137.png" alt="StatusCircleInner" /></td><td><span data-ttu-id="d3f5b-2135">F137</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2135">F137</span></span></td><td><span data-ttu-id="d3f5b-2136">StatusCircleInner</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2136">StatusCircleInner</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f138.png" alt="StatusCircleRing" /></td><td><span data-ttu-id="d3f5b-2137">F138</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2137">F138</span></span></td><td><span data-ttu-id="d3f5b-2138">StatusCircleRing</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2138">StatusCircleRing</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f139.png" alt="StatusTriangleOuter" /></td><td><span data-ttu-id="d3f5b-2139">F139</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2139">F139</span></span></td><td><span data-ttu-id="d3f5b-2140">StatusTriangleOuter</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2140">StatusTriangleOuter</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f13a.png" alt="StatusTriangleInner" /></td><td><span data-ttu-id="d3f5b-2141">F13A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2141">F13A</span></span></td><td><span data-ttu-id="d3f5b-2142">StatusTriangleInner</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2142">StatusTriangleInner</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f13b.png" alt="StatusTriangleExclamation" /></td><td><span data-ttu-id="d3f5b-2143">F13B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2143">F13B</span></span></td><td><span data-ttu-id="d3f5b-2144">StatusTriangleExclamation</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2144">StatusTriangleExclamation</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f13c.png" alt="StatusCircleExclamation" /></td><td><span data-ttu-id="d3f5b-2145">F13C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2145">F13C</span></span></td><td><span data-ttu-id="d3f5b-2146">StatusCircleExclamation</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2146">StatusCircleExclamation</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f13d.png" alt="StatusCircleErrorX" /></td><td><span data-ttu-id="d3f5b-2147">F13D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2147">F13D</span></span></td><td><span data-ttu-id="d3f5b-2148">StatusCircleErrorX</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2148">StatusCircleErrorX</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f13e.png" alt="StatusCircleCheckmark" /></td><td><span data-ttu-id="d3f5b-2149">F13E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2149">F13E</span></span></td><td><span data-ttu-id="d3f5b-2150">StatusCircleCheckmark</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2150">StatusCircleCheckmark</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f13f.png" alt="StatusCircleInfo" /></td><td><span data-ttu-id="d3f5b-2151">F13F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2151">F13F</span></span></td><td><span data-ttu-id="d3f5b-2152">StatusCircleInfo</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2152">StatusCircleInfo</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f140.png" alt="StatusCircleBlock" /></td><td><span data-ttu-id="d3f5b-2153">F140</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2153">F140</span></span></td><td><span data-ttu-id="d3f5b-2154">StatusCircleBlock</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2154">StatusCircleBlock</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f141.png" alt="StatusCircleBlock2" /></td><td><span data-ttu-id="d3f5b-2155">F141</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2155">F141</span></span></td><td><span data-ttu-id="d3f5b-2156">StatusCircleBlock2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2156">StatusCircleBlock2</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f142.png" alt="StatusCircleQuestionMark" /></td><td><span data-ttu-id="d3f5b-2157">F142</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2157">F142</span></span></td><td><span data-ttu-id="d3f5b-2158">StatusCircleQuestionMark</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2158">StatusCircleQuestionMark</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f143.png" alt="StatusCircleSync" /></td><td><span data-ttu-id="d3f5b-2159">F143</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2159">F143</span></span></td><td><span data-ttu-id="d3f5b-2160">StatusCircleSync</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2160">StatusCircleSync</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f146.png" alt="Dial1" /></td><td><span data-ttu-id="d3f5b-2161">F146</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2161">F146</span></span></td><td><span data-ttu-id="d3f5b-2162">Dial1</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2162">Dial1</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f147.png" alt="Dial2" /></td><td><span data-ttu-id="d3f5b-2163">F147</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2163">F147</span></span></td><td><span data-ttu-id="d3f5b-2164">Dial2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2164">Dial2</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f148.png" alt="Dial3" /></td><td><span data-ttu-id="d3f5b-2165">F148</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2165">F148</span></span></td><td><span data-ttu-id="d3f5b-2166">Dial3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2166">Dial3</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f149.png" alt="Dial4" /></td><td><span data-ttu-id="d3f5b-2167">F149</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2167">F149</span></span></td><td><span data-ttu-id="d3f5b-2168">Dial4</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2168">Dial4</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f14a.png" alt="Dial5" /></td><td><span data-ttu-id="d3f5b-2169">F14A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2169">F14A</span></span></td><td><span data-ttu-id="d3f5b-2170">Dial5</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2170">Dial5</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f14b.png" alt="Dial6" /></td><td><span data-ttu-id="d3f5b-2171">F14B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2171">F14B</span></span></td><td><span data-ttu-id="d3f5b-2172">Dial6</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2172">Dial6</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f14c.png" alt="Dial7" /></td><td><span data-ttu-id="d3f5b-2173">F14C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2173">F14C</span></span></td><td><span data-ttu-id="d3f5b-2174">Dial7</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2174">Dial7</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f14d.png" alt="Dial8" /></td><td><span data-ttu-id="d3f5b-2175">F14D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2175">F14D</span></span></td><td><span data-ttu-id="d3f5b-2176">Dial8</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2176">Dial8</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f14e.png" alt="Dial9" /></td><td><span data-ttu-id="d3f5b-2177">F14E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2177">F14E</span></span></td><td><span data-ttu-id="d3f5b-2178">Dial9</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2178">Dial9</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f14f.png" alt="Dial10" /></td><td><span data-ttu-id="d3f5b-2179">F14F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2179">F14F</span></span></td><td><span data-ttu-id="d3f5b-2180">Dial10</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2180">Dial10</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f150.png" alt="Dial11" /></td><td><span data-ttu-id="d3f5b-2181">F150</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2181">F150</span></span></td><td><span data-ttu-id="d3f5b-2182">Dial11</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2182">Dial11</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f151.png" alt="Dial12" /></td><td><span data-ttu-id="d3f5b-2183">F151</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2183">F151</span></span></td><td><span data-ttu-id="d3f5b-2184">Dial12</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2184">Dial12</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f152.png" alt="Dial13" /></td><td><span data-ttu-id="d3f5b-2185">F152</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2185">F152</span></span></td><td><span data-ttu-id="d3f5b-2186">Dial13</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2186">Dial13</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f153.png" alt="Dial14" /></td><td><span data-ttu-id="d3f5b-2187">F153</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2187">F153</span></span></td><td><span data-ttu-id="d3f5b-2188">Dial14</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2188">Dial14</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f154.png" alt="Dial15" /></td><td><span data-ttu-id="d3f5b-2189">F154</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2189">F154</span></span></td><td><span data-ttu-id="d3f5b-2190">Dial15</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2190">Dial15</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f155.png" alt="Dial16" /></td><td><span data-ttu-id="d3f5b-2191">F155</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2191">F155</span></span></td><td><span data-ttu-id="d3f5b-2192">Dial16</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2192">Dial16</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f156.png" alt="DialShape1" /></td><td><span data-ttu-id="d3f5b-2193">F156</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2193">F156</span></span></td><td><span data-ttu-id="d3f5b-2194">DialShape1</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2194">DialShape1</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f157.png" alt="DialShape2" /></td><td><span data-ttu-id="d3f5b-2195">F157</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2195">F157</span></span></td><td><span data-ttu-id="d3f5b-2196">DialShape2</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2196">DialShape2</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f158.png" alt="DialShape3" /></td><td><span data-ttu-id="d3f5b-2197">F158</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2197">F158</span></span></td><td><span data-ttu-id="d3f5b-2198">DialShape3</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2198">DialShape3</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f159.png" alt="DialShape4" /></td><td><span data-ttu-id="d3f5b-2199">F159</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2199">F159</span></span></td><td><span data-ttu-id="d3f5b-2200">DialShape4</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2200">DialShape4</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f161.png" alt="TollSolid" /></td><td><span data-ttu-id="d3f5b-2201">F161</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2201">F161</span></span></td><td><span data-ttu-id="d3f5b-2202">TollSolid</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2202">TollSolid</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f163.png" alt="TrafficCongestionSolid" /></td><td><span data-ttu-id="d3f5b-2203">F163</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2203">F163</span></span></td><td><span data-ttu-id="d3f5b-2204">TrafficCongestionSolid</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2204">TrafficCongestionSolid</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f164.png" alt="ExploreContentSingle" /></td><td><span data-ttu-id="d3f5b-2205">F164</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2205">F164</span></span></td><td><span data-ttu-id="d3f5b-2206">ExploreContentSingle</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2206">ExploreContentSingle</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f165.png" alt="CollapseContent" /></td><td><span data-ttu-id="d3f5b-2207">F165</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2207">F165</span></span></td><td><span data-ttu-id="d3f5b-2208">CollapseContent</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2208">CollapseContent</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f166.png" alt="CollapseContentSingle" /></td><td><span data-ttu-id="d3f5b-2209">F166</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2209">F166</span></span></td><td><span data-ttu-id="d3f5b-2210">CollapseContentSingle</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2210">CollapseContentSingle</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f167.png" alt="InfoSolid" /></td><td><span data-ttu-id="d3f5b-2211">F167</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2211">F167</span></span></td><td><span data-ttu-id="d3f5b-2212">InfoSolid</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2212">InfoSolid</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f168.png" alt="GroupList" /></td><td><span data-ttu-id="d3f5b-2213">F168</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2213">F168</span></span></td><td><span data-ttu-id="d3f5b-2214">GroupList</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2214">GroupList</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f169.png" alt="CaretBottomRightSolidCenter8" /></td><td><span data-ttu-id="d3f5b-2215">F169</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2215">F169</span></span></td><td><span data-ttu-id="d3f5b-2216">CaretBottomRightSolidCenter8</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2216">CaretBottomRightSolidCenter8</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f16a.png" alt="ProgressRingDots" /></td><td><span data-ttu-id="d3f5b-2217">F16A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2217">F16A</span></span></td><td><span data-ttu-id="d3f5b-2218">ProgressRingDots</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2218">ProgressRingDots</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f16b.png" alt="Checkbox14" /></td><td><span data-ttu-id="d3f5b-2219">F16B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2219">F16B</span></span></td><td><span data-ttu-id="d3f5b-2220">Checkbox14</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2220">Checkbox14</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f16c.png" alt="CheckboxComposite14" /></td><td><span data-ttu-id="d3f5b-2221">F16C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2221">F16C</span></span></td><td><span data-ttu-id="d3f5b-2222">CheckboxComposite14</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2222">CheckboxComposite14</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f16d.png" alt="CheckboxIndeterminateCombo14" /></td><td><span data-ttu-id="d3f5b-2223">F16D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2223">F16D</span></span></td><td><span data-ttu-id="d3f5b-2224">CheckboxIndeterminateCombo14</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2224">CheckboxIndeterminateCombo14</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f16e.png" alt="CheckboxIndeterminateCombo" /></td><td><span data-ttu-id="d3f5b-2225">F16E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2225">F16E</span></span></td><td><span data-ttu-id="d3f5b-2226">CheckboxIndeterminateCombo</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2226">CheckboxIndeterminateCombo</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f175.png" alt="StatusPause7" /></td><td><span data-ttu-id="d3f5b-2227">F175</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2227">F175</span></span></td><td><span data-ttu-id="d3f5b-2228">StatusPause7</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2228">StatusPause7</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f17f.png" alt="CharacterAppearance" /></td><td><span data-ttu-id="d3f5b-2229">F17F</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2229">F17F</span></span></td><td><span data-ttu-id="d3f5b-2230">CharacterAppearance</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2230">CharacterAppearance</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f180.png" alt="Lexicon " /></td><td><span data-ttu-id="d3f5b-2231">F180</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2231">F180</span></span></td><td><span data-ttu-id="d3f5b-2232">Lexikon</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2232">Lexicon</span></span> </td></tr>
<tr><td><img src="images/segoe-mdl/f182.png" alt="ScreenTime" /></td><td><span data-ttu-id="d3f5b-2233">F182</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2233">F182</span></span></td><td><span data-ttu-id="d3f5b-2234">ScreenTime</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2234">ScreenTime</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f191.png" alt="HeadlessDevice" /></td><td><span data-ttu-id="d3f5b-2235">F191</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2235">F191</span></span></td><td><span data-ttu-id="d3f5b-2236">HeadlessDevice</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2236">HeadlessDevice</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f193.png" alt="NetworkSharing" /></td><td><span data-ttu-id="d3f5b-2237">F193</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2237">F193</span></span></td><td><span data-ttu-id="d3f5b-2238">NetworkSharing</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2238">NetworkSharing</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f1ad.png" alt="WindowsInsider" /></td><td><span data-ttu-id="d3f5b-2239">F1AD</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2239">F1AD</span></span></td><td><span data-ttu-id="d3f5b-2240">WindowsInsider</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2240">WindowsInsider</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f1cb.png" alt="ChromeSwitch" /></td><td><span data-ttu-id="d3f5b-2241">F1CB</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2241">F1CB</span></span></td><td><span data-ttu-id="d3f5b-2242">ChromeSwitch</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2242">ChromeSwitch</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f1cc.png" alt="ChromeSwitchContast" /></td><td><span data-ttu-id="d3f5b-2243">F1CC</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2243">F1CC</span></span></td><td><span data-ttu-id="d3f5b-2244">ChromeSwitchContast</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2244">ChromeSwitchContast</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f1d8.png" alt="StatusCheckmark" /></td><td><span data-ttu-id="d3f5b-2245">F1D8</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2245">F1D8</span></span></td><td><span data-ttu-id="d3f5b-2246">StatusCheckmark</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2246">StatusCheckmark</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f1d9.png" alt="StatusCheckmarkLeft" /></td><td><span data-ttu-id="d3f5b-2247">F1D9</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2247">F1D9</span></span></td><td><span data-ttu-id="d3f5b-2248">StatusCheckmarkLeft</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2248">StatusCheckmarkLeft</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f20c.png" alt="KeyboardLeftAligned" /></td><td><span data-ttu-id="d3f5b-2249">F20C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2249">F20C</span></span></td><td><span data-ttu-id="d3f5b-2250">KeyboardLeftAligned</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2250">KeyboardLeftAligned</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f20d.png" alt="KeyboardRightAligned" /></td><td><span data-ttu-id="d3f5b-2251">F20D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2251">F20D</span></span></td><td><span data-ttu-id="d3f5b-2252">KeyboardRightAligned</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2252">KeyboardRightAligned</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f210.png" alt="KeyboardSettings" /></td><td><span data-ttu-id="d3f5b-2253">F210</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2253">F210</span></span></td><td><span data-ttu-id="d3f5b-2254">KeyboardSettings</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2254">KeyboardSettings</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f22c.png" alt="IOT" /></td><td><span data-ttu-id="d3f5b-2255">F22C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2255">F22C</span></span></td><td><span data-ttu-id="d3f5b-2256">IOT</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2256">IOT</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f259.png" alt="ExploitProtectionSettings" /></td><td><span data-ttu-id="d3f5b-2257">F259</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2257">F259</span></span></td><td><span data-ttu-id="d3f5b-2258">ExploitProtectionSettings</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2258">ExploitProtectionSettings</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f260.png" alt="KeyboardNarrow" /></td><td><span data-ttu-id="d3f5b-2259">F260</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2259">F260</span></span></td><td><span data-ttu-id="d3f5b-2260">KeyboardNarrow</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2260">KeyboardNarrow</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f261.png" alt="Keyboard12Key" /></td><td><span data-ttu-id="d3f5b-2261">F261</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2261">F261</span></span></td><td><span data-ttu-id="d3f5b-2262">Keyboard12Key</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2262">Keyboard12Key</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f26b.png" alt="KeyboardDock" /></td><td><span data-ttu-id="d3f5b-2263">F26B</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2263">F26B</span></span></td><td><span data-ttu-id="d3f5b-2264">KeyboardDock</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2264">KeyboardDock</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f26c.png" alt="KeyboardUndock" /></td><td><span data-ttu-id="d3f5b-2265">F26C</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2265">F26C</span></span></td><td><span data-ttu-id="d3f5b-2266">KeyboardUndock</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2266">KeyboardUndock</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f26d.png" alt="KeyboardLeftDock" /></td><td><span data-ttu-id="d3f5b-2267">F26D</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2267">F26D</span></span></td><td><span data-ttu-id="d3f5b-2268">KeyboardLeftDock</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2268">KeyboardLeftDock</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f26e.png" alt="KeyboardRightDock" /></td><td><span data-ttu-id="d3f5b-2269">F26E</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2269">F26E</span></span></td><td><span data-ttu-id="d3f5b-2270">KeyboardRightDock</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2270">KeyboardRightDock</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f270.png" alt="Ear" /></td><td><span data-ttu-id="d3f5b-2271">F270</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2271">F270</span></span></td><td><span data-ttu-id="d3f5b-2272">Ohr</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2272">Ear</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f271.png" alt="PointerHand" /></td><td><span data-ttu-id="d3f5b-2273">F271</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2273">F271</span></span></td><td><span data-ttu-id="d3f5b-2274">PointerHand</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2274">PointerHand</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f272.png" alt="Bullseye" /></td><td><span data-ttu-id="d3f5b-2275">F272</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2275">F272</span></span></td><td><span data-ttu-id="d3f5b-2276">Bullseye</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2276">Bullseye</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f32a.png" alt="PassiveAuthentication" /></td><td><span data-ttu-id="d3f5b-2277">F32A</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2277">F32A</span></span></td><td><span data-ttu-id="d3f5b-2278">PassiveAuthentication</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2278">PassiveAuthentication</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f384.png" alt="NetworkOffline" /></td><td><span data-ttu-id="d3f5b-2279">F384</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2279">F384</span></span></td><td><span data-ttu-id="d3f5b-2280">NetworkOffline</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2280">NetworkOffline</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f385.png" alt="NetworkConnected" /></td><td><span data-ttu-id="d3f5b-2281">F385</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2281">F385</span></span></td><td><span data-ttu-id="d3f5b-2282">NetworkConnected</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2282">NetworkConnected</span></span></td></tr>
<tr><td><img src="images/segoe-mdl/f386.png" alt="NetworkConnectedCheckmark" /></td><td><span data-ttu-id="d3f5b-2283">F386</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2283">F386</span></span></td><td><span data-ttu-id="d3f5b-2284">NetworkConnectedCheckmark</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2284">NetworkConnectedCheckmark</span></span></td></tr>


</table>



## <a name="related-articles"></a><span data-ttu-id="d3f5b-2285">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2285">Related articles</span></span>

* [<span data-ttu-id="d3f5b-2286">Richtlinien für Symbole</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2286">Guidelines for icons</span></span>](../style/icons.md)
* [<span data-ttu-id="d3f5b-2287">Symbol-Enumeration</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2287">Symbol enumeration</span></span>](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Controls.Symbol)
* [<span data-ttu-id="d3f5b-2288">FontIcon-Klasse</span><span class="sxs-lookup"><span data-stu-id="d3f5b-2288">FontIcon class</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.fonticon)


