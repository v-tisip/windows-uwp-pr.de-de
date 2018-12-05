---
Description: This article lists and provides usage guidance for the glyphs that come with the Segoe MDL2 Assets font.
Search.Refinement.TopicID: 184
title: Richtlinien für Segoe MDL2-Symbole
ms.assetid: DFB215C2-8A61-4957-B662-3B1991AC9BE1
label: Segoe MDL2 icons
template: detail.hbs
ms.date: 05/19/2017
ms.topic: article
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 076e4b0ddf30a23271bbb6b488f235f7233b28c2
ms.sourcegitcommit: c01c29cd97f1cbf050950526e18e15823b6a12a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8710750"
---
# <a name="segoe-mdl2-icons"></a><span data-ttu-id="44fc0-103">Segoe MDL2-Symbole</span><span class="sxs-lookup"><span data-stu-id="44fc0-103">Segoe MDL2 icons</span></span>

 

<span data-ttu-id="44fc0-104">In diesem Artikel werden die Symbole der Schriftart Segoe MDL2 Assets aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="44fc0-104">This article lists the icons provided by the Segoe MDL2 Assets font.</span></span> 

> <span data-ttu-id="44fc0-105">**Wichtige APIs**: [**Symbol-Enumeration**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.symbol), [**FontIcon-Klasse**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.fonticon)</span><span class="sxs-lookup"><span data-stu-id="44fc0-105">**Important APIs**: [**Symbol enum**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.symbol), [**FontIcon class**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.fonticon)</span></span>

## <a name="about-segoe-mdl2-assets"></a><span data-ttu-id="44fc0-106">Informationen zu MDL2 Assets</span><span class="sxs-lookup"><span data-stu-id="44fc0-106">About Segoe MDL2 Assets</span></span>

<span data-ttu-id="44fc0-107">Mit der Veröffentlichung von Windows10 wurde die Schriftart Segoe UI Symbol von Windows8/8.1 durch die Schriftart Segoe MDL2 Assets ersetzt.</span><span class="sxs-lookup"><span data-stu-id="44fc0-107">With the release of Windows 10, the Segoe MDL2 Assets font replaced the Windows 8/8.1 Segoe UI Symbol icon font.</span></span> <!-- It can be used in much the same manner as the older font, but many glyphs have been redrawn in the Windows 10 icon style with the font’s metrics set so that icons are aligned within the font’s em-square instead of on a typographic baseline. --> <span data-ttu-id="44fc0-108">(**Segoe UI Symbol** ist jedoch weiterhin als „veraltete“ Ressource verfügbar. Es wird jedoch empfohlen, Apps auf die neue Schriftart **Segoe MDL2 Assets** zu aktualisieren.)</span><span class="sxs-lookup"><span data-stu-id="44fc0-108">(**Segoe UI Symbol** will still be available as a "legacy" resource, but we recommend updating your app to use the new **Segoe MDL2 Assets**.)</span></span>

<span data-ttu-id="44fc0-109">Die Mehrzahl der in der Schriftart **Segoe MDL2 Assets** enthaltenen Symbole und Benutzeroberflächen-Steuerelemente sind dem Unicode-Bereich „Private Use Area“ (PUA) zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="44fc0-109">Most of the icons and UI controls included in the **Segoe MDL2 Assets** font are mapped to the Private Use Area of Unicode (PUA).</span></span> <span data-ttu-id="44fc0-110">Mithilfe des PUA können Entwickler Glyphen, die keinen vorhandenen Codepunkten zugeordnet sind, private Unicode-Werte zuweisen.</span><span class="sxs-lookup"><span data-stu-id="44fc0-110">The PUA allows font developers to assign private Unicode values to glyphs that don’t map to existing code points.</span></span> <span data-ttu-id="44fc0-111">Dies ist hilfreich bei der Erstellung einer Symbolschriftart, führt jedoch auch zu einem Interoperabilitätsproblem.</span><span class="sxs-lookup"><span data-stu-id="44fc0-111">This is useful when creating a symbol font, but it creates an interoperability problem.</span></span> <span data-ttu-id="44fc0-112">Ist die Schriftart nicht verfügbar, werden die Glyphen nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="44fc0-112">If the font is not available, the glyphs won’t show up.</span></span> <span data-ttu-id="44fc0-113">Verwenden Sie die Glyphen nur, wenn Sie die Schriftart **Segoe MDL2 Assets** explizit angeben können.</span><span class="sxs-lookup"><span data-stu-id="44fc0-113">Only use these glyphs when you can specify the **Segoe MDL2 Assets** font.</span></span>

<span data-ttu-id="44fc0-114">Verwenden Sie diese Glyphen nur, wenn Sie die Schriftart **Segoe MDL2 Assets** explizit angeben können.</span><span class="sxs-lookup"><span data-stu-id="44fc0-114">Use these glyphs only when you can explicitly specify the **Segoe MDL2 Assets** font.</span></span> <span data-ttu-id="44fc0-115">Bei Verwendung von Kacheln können Sie diese Glyphen nicht nutzen, da Sie die Kachelschriftart nicht angeben können und PUA-Glyphen nicht per Schriftartfallback verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="44fc0-115">If you are working with tiles, you can't use these glyphs because you can't specify the tile font and PUA glyphs are not available via font-fallback.</span></span>

<span data-ttu-id="44fc0-116">Anders als bei **Segoe UI Symbol** sind die Symbole in der Schriftart **Segoe MDL2 Assets** nicht für die Inlineverwendung mit Text vorgesehen.</span><span class="sxs-lookup"><span data-stu-id="44fc0-116">Unlike with **Segoe UI Symbol**, the icons in the **Segoe MDL2 Assets** font are not intended for use in-line with text.</span></span> <span data-ttu-id="44fc0-117">Demnach gelten einige ältere „Tricks“ wie die Pfeile für schrittweise Anzeige nicht mehr.</span><span class="sxs-lookup"><span data-stu-id="44fc0-117">This means that some older "tricks" like the progressive disclosure arrows no longer apply.</span></span> <span data-ttu-id="44fc0-118">Da alle neuen Symbole gleichermaßen größentechnisch angepasst und positioniert werden, müssen sie entsprechend nicht mit einer Nullbreite erstellt werden. Wir haben hingegen sichergestellt, dass sie einfach als ein Satz funktionieren.</span><span class="sxs-lookup"><span data-stu-id="44fc0-118">Likewise, since all of the new icons are sized and positioned the same, they do not have to be made with zero width; we have just made sure they work as a set.</span></span> <span data-ttu-id="44fc0-119">Im Idealfall können Sie zwei Symbole überlagern, die als ein Satz konzipiert wurden, und sie nehmen Gestalt an.</span><span class="sxs-lookup"><span data-stu-id="44fc0-119">Ideally, you can overlay two icons that were designed as a set and they will fall into place.</span></span> <span data-ttu-id="44fc0-120">Wir können dies vornehmen, um die Farbgebung im Code zu erlauben.</span><span class="sxs-lookup"><span data-stu-id="44fc0-120">We may do this to allow colorization in the code.</span></span> <span data-ttu-id="44fc0-121">Beispielsweise wurden U+EA3A und U+EA3B für den Badgestatus der Startkachel erstellt.</span><span class="sxs-lookup"><span data-stu-id="44fc0-121">For example, U+EA3A and U+EA3B were created for the Start tile Badge status.</span></span> <span data-ttu-id="44fc0-122">Da diese bereits zentriert sind, kann die Kreisfüllung für unterschiedliche Status gefärbt werden.</span><span class="sxs-lookup"><span data-stu-id="44fc0-122">Because these are already centered the circle fill can be colored for different states.</span></span>

## <a name="layering-and-mirroring"></a><span data-ttu-id="44fc0-123">Überlagern und Spiegeln</span><span class="sxs-lookup"><span data-stu-id="44fc0-123">Layering and mirroring</span></span>

<span data-ttu-id="44fc0-124">Alle Glyphen in **Segoe MDL2 Assets** haben dieselbe feste Breite mit einer konsistenten Höhe und einem linken Ursprungspunkt. So können Überlagerungs- und Farbgebungseffekte erzielt werden, indem Glyphen direkt übereinander gezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="44fc0-124">All glyphs in **Segoe MDL2 Assets** have the same fixed width with a consistent height and left origin point, so layering and colorization effects can be achieved by drawing glyphs directly on top of each other.</span></span> <span data-ttu-id="44fc0-125">Dieses Beispiel zeigt einen schwarzen Rand, der über das rote Herz mit einer Breite von Null gezeichnet wurde.</span><span class="sxs-lookup"><span data-stu-id="44fc0-125">This example show a black outline drawn on top of the zero-width red heart.</span></span>

![Verwenden von Glyphen mit der Breite 0](images/segoe-ui-symbol-layering.png)

<span data-ttu-id="44fc0-127">Viele der Symbole verfügen zudem über gespiegelte Formen, die in Sprachen verwendet werden können, in denen die Rechts-nach-Links-Ausrichtung verwendet wird, beispielsweise Arabisch, Farsi und Hebräisch.</span><span class="sxs-lookup"><span data-stu-id="44fc0-127">Many of the icons also have mirrored forms available for use in languages that use right-to-left text directionality such as Arabic, Farsi, and Hebrew.</span></span>

## <a name="using-the-icons"></a><span data-ttu-id="44fc0-128">Verwenden der Symbole</span><span class="sxs-lookup"><span data-stu-id="44fc0-128">Using the icons</span></span>
<span data-ttu-id="44fc0-129">Wenn Sie eine app in c#/VB/C++- und XAML entwickeln, können Sie bestimmte Glyphen der Segoe MDL2 Assets mit der [Symbol-Enumeration](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.symbol).</span><span class="sxs-lookup"><span data-stu-id="44fc0-129">If you are developing an app in C#/VB/C++ and XAML, you can use specified glyphs from Segoe MDL2 Assets with the [Symbol enumeration](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.symbol).</span></span> 

```xaml
<SymbolIcon Symbol="GlobalNavigationButton"/>
```

<span data-ttu-id="44fc0-130">Wenn Sie ein Glyphen der Schriftart **Segoe MDL2 Assets** verwenden möchten, das nicht in der Symbolenumeration enthalten ist, verwenden Sie ein [**FontIcon**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.fonticon).</span><span class="sxs-lookup"><span data-stu-id="44fc0-130">If you would like to use a glyph from the **Segoe MDL2 Assets** font that is not included in the Symbol enum, then use a [**FontIcon**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.fonticon).</span></span>

```xaml
<FontIcon FontFamily="Segoe MDL2 Assets" Glyph="&#xE700;"/>
```

<span data-ttu-id="44fc0-131">Sie können auch die statische Ressource `SymbolThemeFontFamily` auf **Segoe MDL2 Assets**, statt die Schriftart nach Namen anzugeben:</span><span class="sxs-lookup"><span data-stu-id="44fc0-131">You can also use the static resource `SymbolThemeFontFamily` to access **Segoe MDL2 Assets**, instead of specifying the font by name:</span></span>
```xaml
<FontIcon FontFamily="{StaticResource SymbolThemeFontFamily}" Glyph="&#xE700;"/>
```


## <a name="how-do-i-get-this-font"></a><span data-ttu-id="44fc0-132">Wie erhalte ich diese Schriftart?</span><span class="sxs-lookup"><span data-stu-id="44fc0-132">How do I get this font?</span></span>
* <span data-ttu-id="44fc0-133">Unter Windows 10: Vorhanden ist, Sie müssen, nichts weiter, die Schriftart im Lieferumfang von Windows.</span><span class="sxs-lookup"><span data-stu-id="44fc0-133">On Windows 10: There's nothing you need to do, the font comes with Windows.</span></span>
* <span data-ttu-id="44fc0-134">Auf einem Mac, müssen Sie zum Herunterladen und installieren Sie die Schriftart: <a href="https://aka.ms/SegoeFonts">erhalten Sie die Segoe UI und MDL2 Symbolschriftarten</a></span><span class="sxs-lookup"><span data-stu-id="44fc0-134">On a Mac, you need to download and install the font: <a href="https://aka.ms/SegoeFonts">Get the Segoe UI and MDL2 icon fonts</a></span></span>

## <a name="icon-list"></a><span data-ttu-id="44fc0-135">Liste der Symbole</span><span class="sxs-lookup"><span data-stu-id="44fc0-135">Icon list</span></span>
<span data-ttu-id="44fc0-136">Beachten Sie zudem, dass die Schriftart **Segoe MDL2-Ressourcen** viel mehr Symbole enthält, als hier gezeigt werden kann.</span><span class="sxs-lookup"><span data-stu-id="44fc0-136">Please keep in mind that the **Segoe MDL2 Assets** font includes many more icons than we can show here.</span></span> <span data-ttu-id="44fc0-137">Viele der Symbole dienen speziellen Zwecken und werden für gewöhnlich nicht an anderer Stelle verwendet.</span><span class="sxs-lookup"><span data-stu-id="44fc0-137">Many of the icons are intended for specialized purposed and are not typically used anywhere else.</span></span>


<table style="background-color: white; color: black">

 <tr>
  <td><span data-ttu-id="44fc0-138">Symbol</span><span class="sxs-lookup"><span data-stu-id="44fc0-138">Symbol</span></span></td>
  <td><span data-ttu-id="44fc0-139">Unicode-Punkt</span><span class="sxs-lookup"><span data-stu-id="44fc0-139">Unicode point</span></span></td>
  <td><span data-ttu-id="44fc0-140">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="44fc0-140">Description</span></span></td>
 </tr>
 <tr><td><img src="images/segoe-mdl/E700.png" width="32" height="32" alt="GlobalNavigationButton" /></td>
  <td><span data-ttu-id="44fc0-141">E700</span><span class="sxs-lookup"><span data-stu-id="44fc0-141">E700</span></span></td>
  <td><span data-ttu-id="44fc0-142">GlobalNavigationButton</span><span class="sxs-lookup"><span data-stu-id="44fc0-142">GlobalNavigationButton</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E701.png" width="32" height="32" alt="Wifi" /></td>
  <td><span data-ttu-id="44fc0-143">E701</span><span class="sxs-lookup"><span data-stu-id="44fc0-143">E701</span></span></td>
  <td><span data-ttu-id="44fc0-144">WLAN</span><span class="sxs-lookup"><span data-stu-id="44fc0-144">Wifi</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E702.png" width="32" height="32" alt="Bluetooth" /></td>
  <td><span data-ttu-id="44fc0-145">E702</span><span class="sxs-lookup"><span data-stu-id="44fc0-145">E702</span></span></td>
  <td><span data-ttu-id="44fc0-146">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="44fc0-146">Bluetooth</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E703.png" width="32" height="32" alt="Connect" /></td>
  <td><span data-ttu-id="44fc0-147">E703</span><span class="sxs-lookup"><span data-stu-id="44fc0-147">E703</span></span></td>
  <td><span data-ttu-id="44fc0-148">Verbinden</span><span class="sxs-lookup"><span data-stu-id="44fc0-148">Connect</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E704.png" width="32" height="32" alt="InternetSharing" /></td>
  <td><span data-ttu-id="44fc0-149">E704</span><span class="sxs-lookup"><span data-stu-id="44fc0-149">E704</span></span></td>
  <td><span data-ttu-id="44fc0-150">InternetSharing</span><span class="sxs-lookup"><span data-stu-id="44fc0-150">InternetSharing</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E705.png" width="32" height="32" alt="VPN" /></td>
  <td><span data-ttu-id="44fc0-151">E705</span><span class="sxs-lookup"><span data-stu-id="44fc0-151">E705</span></span></td>
  <td><span data-ttu-id="44fc0-152">VPN</span><span class="sxs-lookup"><span data-stu-id="44fc0-152">VPN</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E706.png" width="32" height="32" alt="Brightness" /></td>
  <td><span data-ttu-id="44fc0-153">E706</span><span class="sxs-lookup"><span data-stu-id="44fc0-153">E706</span></span></td>
  <td><span data-ttu-id="44fc0-154">Helligkeit</span><span class="sxs-lookup"><span data-stu-id="44fc0-154">Brightness</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E707.png" width="32" height="32" alt="MapPin" /></td>
  <td><span data-ttu-id="44fc0-155">E707</span><span class="sxs-lookup"><span data-stu-id="44fc0-155">E707</span></span></td>
  <td><span data-ttu-id="44fc0-156">MapPin</span><span class="sxs-lookup"><span data-stu-id="44fc0-156">MapPin</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E708.png" width="32" height="32" alt="QuietHours" /></td>
  <td><span data-ttu-id="44fc0-157">E708</span><span class="sxs-lookup"><span data-stu-id="44fc0-157">E708</span></span></td>
  <td><span data-ttu-id="44fc0-158">QuietHours</span><span class="sxs-lookup"><span data-stu-id="44fc0-158">QuietHours</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E709.png" width="32" height="32" alt="Airplane" /></td>
  <td><span data-ttu-id="44fc0-159">E709</span><span class="sxs-lookup"><span data-stu-id="44fc0-159">E709</span></span></td>
  <td><span data-ttu-id="44fc0-160">Airplane</span><span class="sxs-lookup"><span data-stu-id="44fc0-160">Airplane</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E70A.png" width="32" height="32" alt="Tablet" /></td>
  <td><span data-ttu-id="44fc0-161">E70A</span><span class="sxs-lookup"><span data-stu-id="44fc0-161">E70A</span></span></td>
  <td><span data-ttu-id="44fc0-162">Tablet</span><span class="sxs-lookup"><span data-stu-id="44fc0-162">Tablet</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E70B.png" width="32" height="32" alt="QuickNote" /></td>
  <td><span data-ttu-id="44fc0-163">E70B</span><span class="sxs-lookup"><span data-stu-id="44fc0-163">E70B</span></span></td>
  <td><span data-ttu-id="44fc0-164">QuickNote</span><span class="sxs-lookup"><span data-stu-id="44fc0-164">QuickNote</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E70C.png" width="32" height="32" alt="RememberedDevice" /></td>
  <td><span data-ttu-id="44fc0-165">E70C</span><span class="sxs-lookup"><span data-stu-id="44fc0-165">E70C</span></span></td>
  <td><span data-ttu-id="44fc0-166">RememberedDevice</span><span class="sxs-lookup"><span data-stu-id="44fc0-166">RememberedDevice</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E70D.png" width="32" height="32" alt="ChevronDown" /></td>
  <td><span data-ttu-id="44fc0-167">E70D</span><span class="sxs-lookup"><span data-stu-id="44fc0-167">E70D</span></span></td>
  <td><span data-ttu-id="44fc0-168">ChevronDown</span><span class="sxs-lookup"><span data-stu-id="44fc0-168">ChevronDown</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E70E.png" width="32" height="32" alt="ChevronUp" /></td>
  <td><span data-ttu-id="44fc0-169">E70E</span><span class="sxs-lookup"><span data-stu-id="44fc0-169">E70E</span></span></td>
  <td><span data-ttu-id="44fc0-170">ChevronUp</span><span class="sxs-lookup"><span data-stu-id="44fc0-170">ChevronUp</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E70F.png" width="32" height="32" alt="Edit" /></td>
  <td><span data-ttu-id="44fc0-171">E70F</span><span class="sxs-lookup"><span data-stu-id="44fc0-171">E70F</span></span></td>
  <td><span data-ttu-id="44fc0-172">Bearbeiten</span><span class="sxs-lookup"><span data-stu-id="44fc0-172">Edit</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E710.png" width="32" height="32" alt="Add" /></td>
  <td><span data-ttu-id="44fc0-173">E710</span><span class="sxs-lookup"><span data-stu-id="44fc0-173">E710</span></span></td>
  <td><span data-ttu-id="44fc0-174">Add</span><span class="sxs-lookup"><span data-stu-id="44fc0-174">Add</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E711.png" width="32" height="32" alt="Cancel" /></td>
  <td><span data-ttu-id="44fc0-175">E711</span><span class="sxs-lookup"><span data-stu-id="44fc0-175">E711</span></span></td>
  <td><span data-ttu-id="44fc0-176">Abbrechen</span><span class="sxs-lookup"><span data-stu-id="44fc0-176">Cancel</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E712.png" width="32" height="32" alt="More" /></td>
  <td><span data-ttu-id="44fc0-177">E712</span><span class="sxs-lookup"><span data-stu-id="44fc0-177">E712</span></span></td>
  <td><span data-ttu-id="44fc0-178">More</span><span class="sxs-lookup"><span data-stu-id="44fc0-178">More</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E713.png" width="32" height="32" alt="Settings" /></td>
  <td><span data-ttu-id="44fc0-179">E713</span><span class="sxs-lookup"><span data-stu-id="44fc0-179">E713</span></span></td>
  <td><span data-ttu-id="44fc0-180">Einstellungen</span><span class="sxs-lookup"><span data-stu-id="44fc0-180">Settings</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E714.png" width="32" height="32" alt="Video" /></td>
  <td><span data-ttu-id="44fc0-181">E714</span><span class="sxs-lookup"><span data-stu-id="44fc0-181">E714</span></span></td>
  <td><span data-ttu-id="44fc0-182">Video</span><span class="sxs-lookup"><span data-stu-id="44fc0-182">Video</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E715.png" width="32" height="32" alt="Mail" /></td>
  <td><span data-ttu-id="44fc0-183">E715</span><span class="sxs-lookup"><span data-stu-id="44fc0-183">E715</span></span></td>
  <td><span data-ttu-id="44fc0-184">Mail</span><span class="sxs-lookup"><span data-stu-id="44fc0-184">Mail</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E716.png" width="32" height="32" alt="People" /></td>
  <td><span data-ttu-id="44fc0-185">E716</span><span class="sxs-lookup"><span data-stu-id="44fc0-185">E716</span></span></td>
  <td><span data-ttu-id="44fc0-186">Kontakte</span><span class="sxs-lookup"><span data-stu-id="44fc0-186">People</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E717.png" width="32" height="32" alt="Phone" /></td>
  <td><span data-ttu-id="44fc0-187">E717</span><span class="sxs-lookup"><span data-stu-id="44fc0-187">E717</span></span></td>
  <td><span data-ttu-id="44fc0-188">Telefone</span><span class="sxs-lookup"><span data-stu-id="44fc0-188">Phone</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E718.png" width="32" height="32" alt="Pin" /></td>
  <td><span data-ttu-id="44fc0-189">E718</span><span class="sxs-lookup"><span data-stu-id="44fc0-189">E718</span></span></td>
  <td><span data-ttu-id="44fc0-190">Pin</span><span class="sxs-lookup"><span data-stu-id="44fc0-190">Pin</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E719.png" width="32" height="32" alt="Shop" /></td>
  <td><span data-ttu-id="44fc0-191">E719</span><span class="sxs-lookup"><span data-stu-id="44fc0-191">E719</span></span></td>
  <td><span data-ttu-id="44fc0-192">Shop</span><span class="sxs-lookup"><span data-stu-id="44fc0-192">Shop</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E71A.png" width="32" height="32" alt="Stop" /></td>
  <td><span data-ttu-id="44fc0-193">E71A</span><span class="sxs-lookup"><span data-stu-id="44fc0-193">E71A</span></span></td>
  <td><span data-ttu-id="44fc0-194">Stop</span><span class="sxs-lookup"><span data-stu-id="44fc0-194">Stop</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E71B.png" width="32" height="32" alt="Link" /></td>
  <td><span data-ttu-id="44fc0-195">E71B</span><span class="sxs-lookup"><span data-stu-id="44fc0-195">E71B</span></span></td>
  <td><span data-ttu-id="44fc0-196">Link</span><span class="sxs-lookup"><span data-stu-id="44fc0-196">Link</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E71C.png" width="32" height="32" alt="Filter" /></td>
  <td><span data-ttu-id="44fc0-197">E71C</span><span class="sxs-lookup"><span data-stu-id="44fc0-197">E71C</span></span></td>
  <td><span data-ttu-id="44fc0-198">Filter</span><span class="sxs-lookup"><span data-stu-id="44fc0-198">Filter</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E71D.png" width="32" height="32" alt="AllApps" /></td>
  <td><span data-ttu-id="44fc0-199">E71D</span><span class="sxs-lookup"><span data-stu-id="44fc0-199">E71D</span></span></td>
  <td><span data-ttu-id="44fc0-200">AllApps</span><span class="sxs-lookup"><span data-stu-id="44fc0-200">AllApps</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E71E.png" width="32" height="32" alt="Zoom" /></td>
  <td><span data-ttu-id="44fc0-201">E71E</span><span class="sxs-lookup"><span data-stu-id="44fc0-201">E71E</span></span></td>
  <td><span data-ttu-id="44fc0-202">Zoom</span><span class="sxs-lookup"><span data-stu-id="44fc0-202">Zoom</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E71F.png" width="32" height="32" alt="ZoomOut" /></td>
  <td><span data-ttu-id="44fc0-203">E71F</span><span class="sxs-lookup"><span data-stu-id="44fc0-203">E71F</span></span></td>
  <td><span data-ttu-id="44fc0-204">ZoomOut</span><span class="sxs-lookup"><span data-stu-id="44fc0-204">ZoomOut</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E720.png" width="32" height="32" alt="Microphone" /></td>
  <td><span data-ttu-id="44fc0-205">E720</span><span class="sxs-lookup"><span data-stu-id="44fc0-205">E720</span></span></td>
  <td><span data-ttu-id="44fc0-206">Mikrofon</span><span class="sxs-lookup"><span data-stu-id="44fc0-206">Microphone</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E721.png" width="32" height="32" alt="Search" /></td>
  <td><span data-ttu-id="44fc0-207">E721</span><span class="sxs-lookup"><span data-stu-id="44fc0-207">E721</span></span></td>
  <td><span data-ttu-id="44fc0-208">Suche</span><span class="sxs-lookup"><span data-stu-id="44fc0-208">Search</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E722.png" width="32" height="32" alt="Camera" /></td>
  <td><span data-ttu-id="44fc0-209">E722</span><span class="sxs-lookup"><span data-stu-id="44fc0-209">E722</span></span></td>
  <td><span data-ttu-id="44fc0-210">Kamera</span><span class="sxs-lookup"><span data-stu-id="44fc0-210">Camera</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E723.png" width="32" height="32" alt="Attach" /></td>
  <td><span data-ttu-id="44fc0-211">E723</span><span class="sxs-lookup"><span data-stu-id="44fc0-211">E723</span></span></td>
  <td><span data-ttu-id="44fc0-212">Attach</span><span class="sxs-lookup"><span data-stu-id="44fc0-212">Attach</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E724.png" width="32" height="32" alt="Send" /></td>
  <td><span data-ttu-id="44fc0-213">E724</span><span class="sxs-lookup"><span data-stu-id="44fc0-213">E724</span></span></td>
  <td><span data-ttu-id="44fc0-214">Send</span><span class="sxs-lookup"><span data-stu-id="44fc0-214">Send</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E725.png" width="32" height="32" alt="SendFill" /></td>
  <td><span data-ttu-id="44fc0-215">E725</span><span class="sxs-lookup"><span data-stu-id="44fc0-215">E725</span></span></td>
  <td><span data-ttu-id="44fc0-216">SendFill</span><span class="sxs-lookup"><span data-stu-id="44fc0-216">SendFill</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E726.png" width="32" height="32" alt="WalkSolid" /></td>
  <td><span data-ttu-id="44fc0-217">E726</span><span class="sxs-lookup"><span data-stu-id="44fc0-217">E726</span></span></td>
  <td><span data-ttu-id="44fc0-218">WalkSolid</span><span class="sxs-lookup"><span data-stu-id="44fc0-218">WalkSolid</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E727.png" width="32" height="32" alt="InPrivate" /></td>
  <td><span data-ttu-id="44fc0-219">E727</span><span class="sxs-lookup"><span data-stu-id="44fc0-219">E727</span></span></td>
  <td><span data-ttu-id="44fc0-220">InPrivate</span><span class="sxs-lookup"><span data-stu-id="44fc0-220">InPrivate</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E728.png" width="32" height="32" alt="FavoriteList" /></td>
  <td><span data-ttu-id="44fc0-221">E728</span><span class="sxs-lookup"><span data-stu-id="44fc0-221">E728</span></span></td>
  <td><span data-ttu-id="44fc0-222">FavoriteList</span><span class="sxs-lookup"><span data-stu-id="44fc0-222">FavoriteList</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E729.png" width="32" height="32" alt="PageSolid" /></td>
  <td><span data-ttu-id="44fc0-223">E729</span><span class="sxs-lookup"><span data-stu-id="44fc0-223">E729</span></span></td>
  <td><span data-ttu-id="44fc0-224">PageSolid</span><span class="sxs-lookup"><span data-stu-id="44fc0-224">PageSolid</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E72A.png" width="32" height="32" alt="Forward" /></td>
  <td><span data-ttu-id="44fc0-225">E72A</span><span class="sxs-lookup"><span data-stu-id="44fc0-225">E72A</span></span></td>
  <td><span data-ttu-id="44fc0-226">Vorwärts</span><span class="sxs-lookup"><span data-stu-id="44fc0-226">Forward</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E72B.png" width="32" height="32" alt="Back" /></td>
  <td><span data-ttu-id="44fc0-227">E72B</span><span class="sxs-lookup"><span data-stu-id="44fc0-227">E72B</span></span></td>
  <td><span data-ttu-id="44fc0-228">Zurück</span><span class="sxs-lookup"><span data-stu-id="44fc0-228">Back</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E72C.png" width="32" height="32" alt="Refresh" /></td>
  <td><span data-ttu-id="44fc0-229">E72C</span><span class="sxs-lookup"><span data-stu-id="44fc0-229">E72C</span></span></td>
  <td><span data-ttu-id="44fc0-230">Aktualisieren</span><span class="sxs-lookup"><span data-stu-id="44fc0-230">Refresh</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E72D.png" width="32" height="32" alt="Share" /></td>
  <td><span data-ttu-id="44fc0-231">E72D</span><span class="sxs-lookup"><span data-stu-id="44fc0-231">E72D</span></span></td>
  <td><span data-ttu-id="44fc0-232">Freigabe</span><span class="sxs-lookup"><span data-stu-id="44fc0-232">Share</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E72E.png" width="32" height="32" alt="Lock" /></td>
  <td><span data-ttu-id="44fc0-233">E72E</span><span class="sxs-lookup"><span data-stu-id="44fc0-233">E72E</span></span></td>
  <td><span data-ttu-id="44fc0-234">Lock</span><span class="sxs-lookup"><span data-stu-id="44fc0-234">Lock</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E730.png" width="32" height="32" alt="ReportHacked" /></td>
  <td><span data-ttu-id="44fc0-235">E730</span><span class="sxs-lookup"><span data-stu-id="44fc0-235">E730</span></span></td>
  <td><span data-ttu-id="44fc0-236">ReportHacked</span><span class="sxs-lookup"><span data-stu-id="44fc0-236">ReportHacked</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E731.png" width="32" height="32" alt="EMI" /></td>
  <td><span data-ttu-id="44fc0-237">E731</span><span class="sxs-lookup"><span data-stu-id="44fc0-237">E731</span></span></td>
  <td><span data-ttu-id="44fc0-238">EMI</span><span class="sxs-lookup"><span data-stu-id="44fc0-238">EMI</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E734.png" width="32" height="32" alt="FavoriteStar" /></td>
  <td><span data-ttu-id="44fc0-239">E734</span><span class="sxs-lookup"><span data-stu-id="44fc0-239">E734</span></span></td>
  <td><span data-ttu-id="44fc0-240">FavoriteStar</span><span class="sxs-lookup"><span data-stu-id="44fc0-240">FavoriteStar</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E735.png" width="32" height="32" alt="FavoriteStarFill" /></td>
  <td><span data-ttu-id="44fc0-241">E735</span><span class="sxs-lookup"><span data-stu-id="44fc0-241">E735</span></span></td>
  <td><span data-ttu-id="44fc0-242">FavoriteStarFill</span><span class="sxs-lookup"><span data-stu-id="44fc0-242">FavoriteStarFill</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E737.png" width="32" height="32" alt="Favicon" /></td>
  <td><span data-ttu-id="44fc0-243">E737</span><span class="sxs-lookup"><span data-stu-id="44fc0-243">E737</span></span></td>
  <td><span data-ttu-id="44fc0-244">Favicon</span><span class="sxs-lookup"><span data-stu-id="44fc0-244">Favicon</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E738.png" width="32" height="32" alt="Remove" /></td>
  <td><span data-ttu-id="44fc0-245">E738</span><span class="sxs-lookup"><span data-stu-id="44fc0-245">E738</span></span></td>
  <td><span data-ttu-id="44fc0-246">Entfernen</span><span class="sxs-lookup"><span data-stu-id="44fc0-246">Remove</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E739.png" width="32" height="32" alt="Checkbox" /></td>
  <td><span data-ttu-id="44fc0-247">E739</span><span class="sxs-lookup"><span data-stu-id="44fc0-247">E739</span></span></td>
  <td><span data-ttu-id="44fc0-248">Kontrollkästchen</span><span class="sxs-lookup"><span data-stu-id="44fc0-248">Checkbox</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E73A.png" width="32" height="32" alt="CheckboxComposite" /></td>
  <td><span data-ttu-id="44fc0-249">E73A</span><span class="sxs-lookup"><span data-stu-id="44fc0-249">E73A</span></span></td>
  <td><span data-ttu-id="44fc0-250">CheckboxComposite</span><span class="sxs-lookup"><span data-stu-id="44fc0-250">CheckboxComposite</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E73B.png" width="32" height="32" alt="CheckboxFill" /></td>
  <td><span data-ttu-id="44fc0-251">E73B</span><span class="sxs-lookup"><span data-stu-id="44fc0-251">E73B</span></span></td>
  <td><span data-ttu-id="44fc0-252">CheckboxFill</span><span class="sxs-lookup"><span data-stu-id="44fc0-252">CheckboxFill</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E73C.png" width="32" height="32" alt="CheckboxIndeterminate" /></td>
  <td><span data-ttu-id="44fc0-253">E73C</span><span class="sxs-lookup"><span data-stu-id="44fc0-253">E73C</span></span></td>
  <td><span data-ttu-id="44fc0-254">CheckboxIndeterminate</span><span class="sxs-lookup"><span data-stu-id="44fc0-254">CheckboxIndeterminate</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E73D.png" width="32" height="32" alt="CheckboxCompositeReversed" /></td>
  <td><span data-ttu-id="44fc0-255">E73D</span><span class="sxs-lookup"><span data-stu-id="44fc0-255">E73D</span></span></td>
  <td><span data-ttu-id="44fc0-256">CheckboxCompositeReversed</span><span class="sxs-lookup"><span data-stu-id="44fc0-256">CheckboxCompositeReversed</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E73E.png" width="32" height="32" alt="CheckMark" /></td>
  <td><span data-ttu-id="44fc0-257">E73E</span><span class="sxs-lookup"><span data-stu-id="44fc0-257">E73E</span></span></td>
  <td><span data-ttu-id="44fc0-258">CheckMark</span><span class="sxs-lookup"><span data-stu-id="44fc0-258">CheckMark</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E73F.png" width="32" height="32" alt="BackToWindow" /></td>
  <td><span data-ttu-id="44fc0-259">E73F</span><span class="sxs-lookup"><span data-stu-id="44fc0-259">E73F</span></span></td>
  <td><span data-ttu-id="44fc0-260">BackToWindow</span><span class="sxs-lookup"><span data-stu-id="44fc0-260">BackToWindow</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E740.png" width="32" height="32" alt="FullScreen" /></td>
  <td><span data-ttu-id="44fc0-261">E740</span><span class="sxs-lookup"><span data-stu-id="44fc0-261">E740</span></span></td>
  <td><span data-ttu-id="44fc0-262">FullScreen</span><span class="sxs-lookup"><span data-stu-id="44fc0-262">FullScreen</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E741.png" width="32" height="32" alt="ResizeTouchLarger" /></td>
  <td><span data-ttu-id="44fc0-263">E741</span><span class="sxs-lookup"><span data-stu-id="44fc0-263">E741</span></span></td>
  <td><span data-ttu-id="44fc0-264">ResizeTouchLarger</span><span class="sxs-lookup"><span data-stu-id="44fc0-264">ResizeTouchLarger</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E742.png" width="32" height="32" alt="ResizeTouchSmaller" /></td>
  <td><span data-ttu-id="44fc0-265">E742</span><span class="sxs-lookup"><span data-stu-id="44fc0-265">E742</span></span></td>
  <td><span data-ttu-id="44fc0-266">ResizeTouchSmaller</span><span class="sxs-lookup"><span data-stu-id="44fc0-266">ResizeTouchSmaller</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E743.png" width="32" height="32" alt="ResizeMouseSmall" /></td>
  <td><span data-ttu-id="44fc0-267">E743</span><span class="sxs-lookup"><span data-stu-id="44fc0-267">E743</span></span></td>
  <td><span data-ttu-id="44fc0-268">ResizeMouseSmall</span><span class="sxs-lookup"><span data-stu-id="44fc0-268">ResizeMouseSmall</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E744.png" width="32" height="32" alt="ResizeMouseMedium" /></td>
  <td><span data-ttu-id="44fc0-269">E744</span><span class="sxs-lookup"><span data-stu-id="44fc0-269">E744</span></span></td>
  <td><span data-ttu-id="44fc0-270">ResizeMouseMedium</span><span class="sxs-lookup"><span data-stu-id="44fc0-270">ResizeMouseMedium</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E745.png" width="32" height="32" alt="ResizeMouseWide" /></td>
  <td><span data-ttu-id="44fc0-271">E745</span><span class="sxs-lookup"><span data-stu-id="44fc0-271">E745</span></span></td>
  <td><span data-ttu-id="44fc0-272">ResizeMouseWide</span><span class="sxs-lookup"><span data-stu-id="44fc0-272">ResizeMouseWide</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E746.png" width="32" height="32" alt="ResizeMouseTall" /></td>
  <td><span data-ttu-id="44fc0-273">E746</span><span class="sxs-lookup"><span data-stu-id="44fc0-273">E746</span></span></td>
  <td><span data-ttu-id="44fc0-274">ResizeMouseTall</span><span class="sxs-lookup"><span data-stu-id="44fc0-274">ResizeMouseTall</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E747.png" width="32" height="32" alt="ResizeMouseLarge" /></td>
  <td><span data-ttu-id="44fc0-275">E747</span><span class="sxs-lookup"><span data-stu-id="44fc0-275">E747</span></span></td>
  <td><span data-ttu-id="44fc0-276">ResizeMouseLarge</span><span class="sxs-lookup"><span data-stu-id="44fc0-276">ResizeMouseLarge</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E748.png" width="32" height="32" alt="SwitchUser" /></td>
  <td><span data-ttu-id="44fc0-277">E748</span><span class="sxs-lookup"><span data-stu-id="44fc0-277">E748</span></span></td>
  <td><span data-ttu-id="44fc0-278">SwitchUser</span><span class="sxs-lookup"><span data-stu-id="44fc0-278">SwitchUser</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E749.png" width="32" height="32" alt="Print" /></td>
  <td><span data-ttu-id="44fc0-279">E749</span><span class="sxs-lookup"><span data-stu-id="44fc0-279">E749</span></span></td>
  <td><span data-ttu-id="44fc0-280">Drucken</span><span class="sxs-lookup"><span data-stu-id="44fc0-280">Print</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E74A.png" width="32" height="32" alt="Up" /></td>
  <td><span data-ttu-id="44fc0-281">E74A</span><span class="sxs-lookup"><span data-stu-id="44fc0-281">E74A</span></span></td>
  <td><span data-ttu-id="44fc0-282">Oben</span><span class="sxs-lookup"><span data-stu-id="44fc0-282">Up</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E74B.png" width="32" height="32" alt="Down" /></td>
  <td><span data-ttu-id="44fc0-283">E74B</span><span class="sxs-lookup"><span data-stu-id="44fc0-283">E74B</span></span></td>
  <td><span data-ttu-id="44fc0-284">Unten</span><span class="sxs-lookup"><span data-stu-id="44fc0-284">Down</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E74C.png" width="32" height="32" alt="OEM" /></td>
  <td><span data-ttu-id="44fc0-285">E74C</span><span class="sxs-lookup"><span data-stu-id="44fc0-285">E74C</span></span></td>
  <td><span data-ttu-id="44fc0-286">OEM</span><span class="sxs-lookup"><span data-stu-id="44fc0-286">OEM</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E74D.png" width="32" height="32" alt="Delete" /></td>
  <td><span data-ttu-id="44fc0-287">E74D</span><span class="sxs-lookup"><span data-stu-id="44fc0-287">E74D</span></span></td>
  <td><span data-ttu-id="44fc0-288">Delete</span><span class="sxs-lookup"><span data-stu-id="44fc0-288">Delete</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E74E.png" width="32" height="32" alt="Save" /></td>
  <td><span data-ttu-id="44fc0-289">E74E</span><span class="sxs-lookup"><span data-stu-id="44fc0-289">E74E</span></span></td>
  <td><span data-ttu-id="44fc0-290">Speichern</span><span class="sxs-lookup"><span data-stu-id="44fc0-290">Save</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E74F.png" width="32" height="32" alt="Mute" /></td>
  <td><span data-ttu-id="44fc0-291">E74F</span><span class="sxs-lookup"><span data-stu-id="44fc0-291">E74F</span></span></td>
  <td><span data-ttu-id="44fc0-292">Stummschalten</span><span class="sxs-lookup"><span data-stu-id="44fc0-292">Mute</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E750.png" width="32" height="32" alt="BackSpaceQWERTY" /></td>
  <td><span data-ttu-id="44fc0-293">E750</span><span class="sxs-lookup"><span data-stu-id="44fc0-293">E750</span></span></td>
  <td><span data-ttu-id="44fc0-294">BackSpaceQWERTY</span><span class="sxs-lookup"><span data-stu-id="44fc0-294">BackSpaceQWERTY</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E751.png" width="32" height="32" alt="ReturnKey" /></td>
  <td><span data-ttu-id="44fc0-295">E751</span><span class="sxs-lookup"><span data-stu-id="44fc0-295">E751</span></span></td>
  <td><span data-ttu-id="44fc0-296">ReturnKey</span><span class="sxs-lookup"><span data-stu-id="44fc0-296">ReturnKey</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E752.png" width="32" height="32" alt="UpArrowShiftKey" /></td>
  <td><span data-ttu-id="44fc0-297">E752</span><span class="sxs-lookup"><span data-stu-id="44fc0-297">E752</span></span></td>
  <td><span data-ttu-id="44fc0-298">UpArrowShiftKey</span><span class="sxs-lookup"><span data-stu-id="44fc0-298">UpArrowShiftKey</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E753.png" width="32" height="32" alt="Cloud" /></td>
  <td><span data-ttu-id="44fc0-299">E753</span><span class="sxs-lookup"><span data-stu-id="44fc0-299">E753</span></span></td>
  <td><span data-ttu-id="44fc0-300">Cloud</span><span class="sxs-lookup"><span data-stu-id="44fc0-300">Cloud</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E754.png" width="32" height="32" alt="Flashlight" /></td>
  <td><span data-ttu-id="44fc0-301">E754</span><span class="sxs-lookup"><span data-stu-id="44fc0-301">E754</span></span></td>
  <td><span data-ttu-id="44fc0-302">Flashlight</span><span class="sxs-lookup"><span data-stu-id="44fc0-302">Flashlight</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E755.png" width="32" height="32" alt="RotationLock" /></td>
  <td><span data-ttu-id="44fc0-303">E755</span><span class="sxs-lookup"><span data-stu-id="44fc0-303">E755</span></span></td>
  <td><span data-ttu-id="44fc0-304">RotationLock</span><span class="sxs-lookup"><span data-stu-id="44fc0-304">RotationLock</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E756.png" width="32" height="32" alt="CommandPrompt" /></td>
  <td><span data-ttu-id="44fc0-305">E756</span><span class="sxs-lookup"><span data-stu-id="44fc0-305">E756</span></span></td>
  <td><span data-ttu-id="44fc0-306">CommandPrompt</span><span class="sxs-lookup"><span data-stu-id="44fc0-306">CommandPrompt</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E759.png" width="32" height="32" alt="SIPMove" /></td>
  <td><span data-ttu-id="44fc0-307">E759</span><span class="sxs-lookup"><span data-stu-id="44fc0-307">E759</span></span></td>
  <td><span data-ttu-id="44fc0-308">SIPMove</span><span class="sxs-lookup"><span data-stu-id="44fc0-308">SIPMove</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E75A.png" width="32" height="32" alt="SIPUndock" /></td>
  <td><span data-ttu-id="44fc0-309">E75A</span><span class="sxs-lookup"><span data-stu-id="44fc0-309">E75A</span></span></td>
  <td><span data-ttu-id="44fc0-310">SIPUndock</span><span class="sxs-lookup"><span data-stu-id="44fc0-310">SIPUndock</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E75B.png" width="32" height="32" alt="SIPRedock" /></td>
  <td><span data-ttu-id="44fc0-311">E75B</span><span class="sxs-lookup"><span data-stu-id="44fc0-311">E75B</span></span></td>
  <td><span data-ttu-id="44fc0-312">SIPRedock</span><span class="sxs-lookup"><span data-stu-id="44fc0-312">SIPRedock</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E75C.png" width="32" height="32" alt="EraseTool" /></td>
  <td><span data-ttu-id="44fc0-313">E75C</span><span class="sxs-lookup"><span data-stu-id="44fc0-313">E75C</span></span></td>
  <td><span data-ttu-id="44fc0-314">EraseTool</span><span class="sxs-lookup"><span data-stu-id="44fc0-314">EraseTool</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E75D.png" width="32" height="32" alt="UnderscoreSpace" /></td>
  <td><span data-ttu-id="44fc0-315">E75D</span><span class="sxs-lookup"><span data-stu-id="44fc0-315">E75D</span></span></td>
  <td><span data-ttu-id="44fc0-316">UnderscoreSpace</span><span class="sxs-lookup"><span data-stu-id="44fc0-316">UnderscoreSpace</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E75E.png" width="32" height="32" alt="GripperTool" /></td>
  <td><span data-ttu-id="44fc0-317">E75E</span><span class="sxs-lookup"><span data-stu-id="44fc0-317">E75E</span></span></td>
  <td><span data-ttu-id="44fc0-318">GripperTool</span><span class="sxs-lookup"><span data-stu-id="44fc0-318">GripperTool</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E75F.png" width="32" height="32" alt="Dialpad" /></td>
  <td><span data-ttu-id="44fc0-319">E75F</span><span class="sxs-lookup"><span data-stu-id="44fc0-319">E75F</span></span></td>
  <td><span data-ttu-id="44fc0-320">Dialpad</span><span class="sxs-lookup"><span data-stu-id="44fc0-320">Dialpad</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E760.png" width="32" height="32" alt="PageLeft" /></td>
  <td><span data-ttu-id="44fc0-321">E760</span><span class="sxs-lookup"><span data-stu-id="44fc0-321">E760</span></span></td>
  <td><span data-ttu-id="44fc0-322">PageLeft</span><span class="sxs-lookup"><span data-stu-id="44fc0-322">PageLeft</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E761.png" width="32" height="32" alt="PageRight" /></td>
  <td><span data-ttu-id="44fc0-323">E761</span><span class="sxs-lookup"><span data-stu-id="44fc0-323">E761</span></span></td>
  <td><span data-ttu-id="44fc0-324">PageRight</span><span class="sxs-lookup"><span data-stu-id="44fc0-324">PageRight</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E762.png" width="32" height="32" alt="MultiSelect" /></td>
  <td><span data-ttu-id="44fc0-325">E762</span><span class="sxs-lookup"><span data-stu-id="44fc0-325">E762</span></span></td>
  <td><span data-ttu-id="44fc0-326">MultiSelect</span><span class="sxs-lookup"><span data-stu-id="44fc0-326">MultiSelect</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E763.png" width="32" height="32" alt="KeyboardLeftHanded" /></td>
  <td><span data-ttu-id="44fc0-327">E763</span><span class="sxs-lookup"><span data-stu-id="44fc0-327">E763</span></span></td>
  <td><span data-ttu-id="44fc0-328">KeyboardLeftHanded</span><span class="sxs-lookup"><span data-stu-id="44fc0-328">KeyboardLeftHanded</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E764.png" width="32" height="32" alt="KeyboardRightHanded" /></td>
  <td><span data-ttu-id="44fc0-329">E764</span><span class="sxs-lookup"><span data-stu-id="44fc0-329">E764</span></span></td>
  <td><span data-ttu-id="44fc0-330">KeyboardRightHanded</span><span class="sxs-lookup"><span data-stu-id="44fc0-330">KeyboardRightHanded</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E765.png" width="32" height="32" alt="KeyboardClassic" /></td>
  <td><span data-ttu-id="44fc0-331">E765</span><span class="sxs-lookup"><span data-stu-id="44fc0-331">E765</span></span></td>
  <td><span data-ttu-id="44fc0-332">KeyboardClassic</span><span class="sxs-lookup"><span data-stu-id="44fc0-332">KeyboardClassic</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E766.png" width="32" height="32" alt="KeyboardSplit" /></td>
  <td><span data-ttu-id="44fc0-333">E766</span><span class="sxs-lookup"><span data-stu-id="44fc0-333">E766</span></span></td>
  <td><span data-ttu-id="44fc0-334">KeyboardSplit</span><span class="sxs-lookup"><span data-stu-id="44fc0-334">KeyboardSplit</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E767.png" width="32" height="32" alt="Volume" /></td>
  <td><span data-ttu-id="44fc0-335">E767</span><span class="sxs-lookup"><span data-stu-id="44fc0-335">E767</span></span></td>
  <td><span data-ttu-id="44fc0-336">Volume</span><span class="sxs-lookup"><span data-stu-id="44fc0-336">Volume</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E768.png" width="32" height="32" alt="Play" /></td>
  <td><span data-ttu-id="44fc0-337">E768</span><span class="sxs-lookup"><span data-stu-id="44fc0-337">E768</span></span></td>
  <td><span data-ttu-id="44fc0-338">Wiedergeben</span><span class="sxs-lookup"><span data-stu-id="44fc0-338">Play</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E769.png" width="32" height="32" alt="Pause" /></td>
  <td><span data-ttu-id="44fc0-339">E769</span><span class="sxs-lookup"><span data-stu-id="44fc0-339">E769</span></span></td>
  <td><span data-ttu-id="44fc0-340">Anhalten</span><span class="sxs-lookup"><span data-stu-id="44fc0-340">Pause</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E76B.png" width="32" height="32" alt="ChevronLeft" /></td>
  <td><span data-ttu-id="44fc0-341">E76B</span><span class="sxs-lookup"><span data-stu-id="44fc0-341">E76B</span></span></td>
  <td><span data-ttu-id="44fc0-342">ChevronLeft</span><span class="sxs-lookup"><span data-stu-id="44fc0-342">ChevronLeft</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E76C.png" width="32" height="32" alt="ChevronRight" /></td>
  <td><span data-ttu-id="44fc0-343">E76C</span><span class="sxs-lookup"><span data-stu-id="44fc0-343">E76C</span></span></td>
  <td><span data-ttu-id="44fc0-344">ChevronRight</span><span class="sxs-lookup"><span data-stu-id="44fc0-344">ChevronRight</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E76D.png" width="32" height="32" alt="InkingTool" /></td>
  <td><span data-ttu-id="44fc0-345">E76D</span><span class="sxs-lookup"><span data-stu-id="44fc0-345">E76D</span></span></td>
  <td><span data-ttu-id="44fc0-346">InkingTool</span><span class="sxs-lookup"><span data-stu-id="44fc0-346">InkingTool</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E76E.png" width="32" height="32" alt="Emoji2" /></td>
  <td><span data-ttu-id="44fc0-347">E76E</span><span class="sxs-lookup"><span data-stu-id="44fc0-347">E76E</span></span></td>
  <td><span data-ttu-id="44fc0-348">Emoji2</span><span class="sxs-lookup"><span data-stu-id="44fc0-348">Emoji2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E76F.png" width="32" height="32" alt="GripperBarHorizontal" /></td>
  <td><span data-ttu-id="44fc0-349">E76F</span><span class="sxs-lookup"><span data-stu-id="44fc0-349">E76F</span></span></td>
  <td><span data-ttu-id="44fc0-350">GripperBarHorizontal</span><span class="sxs-lookup"><span data-stu-id="44fc0-350">GripperBarHorizontal</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E770.png" width="32" height="32" alt="System" /></td>
  <td><span data-ttu-id="44fc0-351">E770</span><span class="sxs-lookup"><span data-stu-id="44fc0-351">E770</span></span></td>
  <td><span data-ttu-id="44fc0-352">System</span><span class="sxs-lookup"><span data-stu-id="44fc0-352">System</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E771.png" width="32" height="32" alt="Personalize" /></td>
  <td><span data-ttu-id="44fc0-353">E771</span><span class="sxs-lookup"><span data-stu-id="44fc0-353">E771</span></span></td>
  <td><span data-ttu-id="44fc0-354">Personalisieren</span><span class="sxs-lookup"><span data-stu-id="44fc0-354">Personalize</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E772.png" width="32" height="32" alt="Devices" /></td>
  <td><span data-ttu-id="44fc0-355">E772</span><span class="sxs-lookup"><span data-stu-id="44fc0-355">E772</span></span></td>
  <td><span data-ttu-id="44fc0-356">Geräte</span><span class="sxs-lookup"><span data-stu-id="44fc0-356">Devices</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E773.png" width="32" height="32" alt="SearchAndApps" /></td>
  <td><span data-ttu-id="44fc0-357">E773</span><span class="sxs-lookup"><span data-stu-id="44fc0-357">E773</span></span></td>
  <td><span data-ttu-id="44fc0-358">SearchAndApps</span><span class="sxs-lookup"><span data-stu-id="44fc0-358">SearchAndApps</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E774.png" width="32" height="32" alt="Globe" /></td>
  <td><span data-ttu-id="44fc0-359">E774</span><span class="sxs-lookup"><span data-stu-id="44fc0-359">E774</span></span></td>
  <td><span data-ttu-id="44fc0-360">Globe</span><span class="sxs-lookup"><span data-stu-id="44fc0-360">Globe</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E775.png" width="32" height="32" alt="TimeLanguage" /></td>
  <td><span data-ttu-id="44fc0-361">E775</span><span class="sxs-lookup"><span data-stu-id="44fc0-361">E775</span></span></td>
  <td><span data-ttu-id="44fc0-362">TimeLanguage</span><span class="sxs-lookup"><span data-stu-id="44fc0-362">TimeLanguage</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E776.png" width="32" height="32" alt="EaseOfAccess" /></td>
  <td><span data-ttu-id="44fc0-363">E776</span><span class="sxs-lookup"><span data-stu-id="44fc0-363">E776</span></span></td>
  <td><span data-ttu-id="44fc0-364">EaseOfAccess</span><span class="sxs-lookup"><span data-stu-id="44fc0-364">EaseOfAccess</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E777.png" width="32" height="32" alt="UpdateRestore" /></td>
  <td><span data-ttu-id="44fc0-365">E777</span><span class="sxs-lookup"><span data-stu-id="44fc0-365">E777</span></span></td>
  <td><span data-ttu-id="44fc0-366">UpdateRestore</span><span class="sxs-lookup"><span data-stu-id="44fc0-366">UpdateRestore</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E778.png" width="32" height="32" alt="HangUp" /></td>
  <td><span data-ttu-id="44fc0-367">E778</span><span class="sxs-lookup"><span data-stu-id="44fc0-367">E778</span></span></td>
  <td><span data-ttu-id="44fc0-368">HangUp</span><span class="sxs-lookup"><span data-stu-id="44fc0-368">HangUp</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E779.png" width="32" height="32" alt="ContactInfo" /></td>
  <td><span data-ttu-id="44fc0-369">E779</span><span class="sxs-lookup"><span data-stu-id="44fc0-369">E779</span></span></td>
  <td><span data-ttu-id="44fc0-370">ContactInfo</span><span class="sxs-lookup"><span data-stu-id="44fc0-370">ContactInfo</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E77A.png" width="32" height="32" alt="Unpin" /></td>
  <td><span data-ttu-id="44fc0-371">E77A</span><span class="sxs-lookup"><span data-stu-id="44fc0-371">E77A</span></span></td>
  <td><span data-ttu-id="44fc0-372">Loslösen</span><span class="sxs-lookup"><span data-stu-id="44fc0-372">Unpin</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E77B.png" width="32" height="32" alt="Contact" /></td>
  <td><span data-ttu-id="44fc0-373">E77B</span><span class="sxs-lookup"><span data-stu-id="44fc0-373">E77B</span></span></td>
  <td><span data-ttu-id="44fc0-374">Contact</span><span class="sxs-lookup"><span data-stu-id="44fc0-374">Contact</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E77C.png" width="32" height="32" alt="Memo" /></td>
  <td><span data-ttu-id="44fc0-375">E77C</span><span class="sxs-lookup"><span data-stu-id="44fc0-375">E77C</span></span></td>
  <td><span data-ttu-id="44fc0-376">Memo</span><span class="sxs-lookup"><span data-stu-id="44fc0-376">Memo</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E77F.png" width="32" height="32" alt="Paste" /></td>
  <td><span data-ttu-id="44fc0-377">E77F</span><span class="sxs-lookup"><span data-stu-id="44fc0-377">E77F</span></span></td>
  <td><span data-ttu-id="44fc0-378">Einfügen</span><span class="sxs-lookup"><span data-stu-id="44fc0-378">Paste</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E780.png" width="32" height="32" alt="PhoneBook" /></td>
  <td><span data-ttu-id="44fc0-379">E780</span><span class="sxs-lookup"><span data-stu-id="44fc0-379">E780</span></span></td>
  <td><span data-ttu-id="44fc0-380">PhoneBook</span><span class="sxs-lookup"><span data-stu-id="44fc0-380">PhoneBook</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E781.png" width="32" height="32" alt="LEDLight" /></td>
  <td><span data-ttu-id="44fc0-381">E781</span><span class="sxs-lookup"><span data-stu-id="44fc0-381">E781</span></span></td>
  <td><span data-ttu-id="44fc0-382">LEDLight</span><span class="sxs-lookup"><span data-stu-id="44fc0-382">LEDLight</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E783.png" width="32" height="32" alt="Error" /></td>
  <td><span data-ttu-id="44fc0-383">E783</span><span class="sxs-lookup"><span data-stu-id="44fc0-383">E783</span></span></td>
  <td><span data-ttu-id="44fc0-384">Fehler</span><span class="sxs-lookup"><span data-stu-id="44fc0-384">Error</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E784.png" width="32" height="32" alt="GripperBarVertical" /></td>
  <td><span data-ttu-id="44fc0-385">E784</span><span class="sxs-lookup"><span data-stu-id="44fc0-385">E784</span></span></td>
  <td><span data-ttu-id="44fc0-386">GripperBarVertical</span><span class="sxs-lookup"><span data-stu-id="44fc0-386">GripperBarVertical</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E785.png" width="32" height="32" alt="Unlock" /></td>
  <td><span data-ttu-id="44fc0-387">E785</span><span class="sxs-lookup"><span data-stu-id="44fc0-387">E785</span></span></td>
  <td><span data-ttu-id="44fc0-388">Entsperren</span><span class="sxs-lookup"><span data-stu-id="44fc0-388">Unlock</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E786.png" width="32" height="32" alt="Slideshow" /></td>
  <td><span data-ttu-id="44fc0-389">E786</span><span class="sxs-lookup"><span data-stu-id="44fc0-389">E786</span></span></td>
  <td><span data-ttu-id="44fc0-390">Slideshow</span><span class="sxs-lookup"><span data-stu-id="44fc0-390">Slideshow</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E787.png" width="32" height="32" alt="Calendar" /></td>
  <td><span data-ttu-id="44fc0-391">E787</span><span class="sxs-lookup"><span data-stu-id="44fc0-391">E787</span></span></td>
  <td><span data-ttu-id="44fc0-392">Kalender</span><span class="sxs-lookup"><span data-stu-id="44fc0-392">Calendar</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E788.png" width="32" height="32" alt="GripperResize" /></td>
  <td><span data-ttu-id="44fc0-393">E788</span><span class="sxs-lookup"><span data-stu-id="44fc0-393">E788</span></span></td>
  <td><span data-ttu-id="44fc0-394">GripperResize</span><span class="sxs-lookup"><span data-stu-id="44fc0-394">GripperResize</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E789.png" width="32" height="32" alt="Megaphone" /></td>
  <td><span data-ttu-id="44fc0-395">E789</span><span class="sxs-lookup"><span data-stu-id="44fc0-395">E789</span></span></td>
  <td><span data-ttu-id="44fc0-396">Megaphone</span><span class="sxs-lookup"><span data-stu-id="44fc0-396">Megaphone</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E78A.png" width="32" height="32" alt="Trim" /></td>
  <td><span data-ttu-id="44fc0-397">E78A</span><span class="sxs-lookup"><span data-stu-id="44fc0-397">E78A</span></span></td>
  <td><span data-ttu-id="44fc0-398">Trim</span><span class="sxs-lookup"><span data-stu-id="44fc0-398">Trim</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E78B.png" width="32" height="32" alt="NewWindow" /></td>
  <td><span data-ttu-id="44fc0-399">E78B</span><span class="sxs-lookup"><span data-stu-id="44fc0-399">E78B</span></span></td>
  <td><span data-ttu-id="44fc0-400">NewWindow</span><span class="sxs-lookup"><span data-stu-id="44fc0-400">NewWindow</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E78C.png" width="32" height="32" alt="SaveLocal" /></td>
  <td><span data-ttu-id="44fc0-401">E78C</span><span class="sxs-lookup"><span data-stu-id="44fc0-401">E78C</span></span></td>
  <td><span data-ttu-id="44fc0-402">SaveLocal</span><span class="sxs-lookup"><span data-stu-id="44fc0-402">SaveLocal</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E790.png" width="32" height="32" alt="Color" /></td>
  <td><span data-ttu-id="44fc0-403">E790</span><span class="sxs-lookup"><span data-stu-id="44fc0-403">E790</span></span></td>
  <td><span data-ttu-id="44fc0-404">Farben</span><span class="sxs-lookup"><span data-stu-id="44fc0-404">Color</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E791.png" width="32" height="32" alt="DataSense" /></td>
  <td><span data-ttu-id="44fc0-405">E791</span><span class="sxs-lookup"><span data-stu-id="44fc0-405">E791</span></span></td>
  <td><span data-ttu-id="44fc0-406">DataSense</span><span class="sxs-lookup"><span data-stu-id="44fc0-406">DataSense</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E792.png" width="32" height="32" alt="SaveAs" /></td>
  <td><span data-ttu-id="44fc0-407">E792</span><span class="sxs-lookup"><span data-stu-id="44fc0-407">E792</span></span></td>
  <td><span data-ttu-id="44fc0-408">SaveAs</span><span class="sxs-lookup"><span data-stu-id="44fc0-408">SaveAs</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E793.png" width="32" height="32" alt="Light" /></td>
  <td><span data-ttu-id="44fc0-409">E793</span><span class="sxs-lookup"><span data-stu-id="44fc0-409">E793</span></span></td>
  <td><span data-ttu-id="44fc0-410">Licht</span><span class="sxs-lookup"><span data-stu-id="44fc0-410">Light</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E799.png" width="32" height="32" alt="AspectRatio" /></td>
  <td><span data-ttu-id="44fc0-411">E799</span><span class="sxs-lookup"><span data-stu-id="44fc0-411">E799</span></span></td>
  <td><span data-ttu-id="44fc0-412">AspectRatio</span><span class="sxs-lookup"><span data-stu-id="44fc0-412">AspectRatio</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7A5.png" width="32" height="32" alt="DataSenseBar" /></td>
  <td><span data-ttu-id="44fc0-413">E7A5</span><span class="sxs-lookup"><span data-stu-id="44fc0-413">E7A5</span></span></td>
  <td><span data-ttu-id="44fc0-414">DataSenseBar</span><span class="sxs-lookup"><span data-stu-id="44fc0-414">DataSenseBar</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7A6.png" width="32" height="32" alt="Redo" /></td>
  <td><span data-ttu-id="44fc0-415">E7A6</span><span class="sxs-lookup"><span data-stu-id="44fc0-415">E7A6</span></span></td>
  <td><span data-ttu-id="44fc0-416">Wiederholen</span><span class="sxs-lookup"><span data-stu-id="44fc0-416">Redo</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7A7.png" width="32" height="32" alt="Undo" /></td>
  <td><span data-ttu-id="44fc0-417">E7A7</span><span class="sxs-lookup"><span data-stu-id="44fc0-417">E7A7</span></span></td>
  <td><span data-ttu-id="44fc0-418">Rückgängig machen</span><span class="sxs-lookup"><span data-stu-id="44fc0-418">Undo</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7A8.png" width="32" height="32" alt="Crop" /></td>
  <td><span data-ttu-id="44fc0-419">E7A8</span><span class="sxs-lookup"><span data-stu-id="44fc0-419">E7A8</span></span></td>
  <td><span data-ttu-id="44fc0-420">Crop</span><span class="sxs-lookup"><span data-stu-id="44fc0-420">Crop</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7AC.png" width="32" height="32" alt="OpenWith" /></td>
  <td><span data-ttu-id="44fc0-421">E7AC</span><span class="sxs-lookup"><span data-stu-id="44fc0-421">E7AC</span></span></td>
  <td><span data-ttu-id="44fc0-422">OpenWith</span><span class="sxs-lookup"><span data-stu-id="44fc0-422">OpenWith</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7AD.png" width="32" height="32" alt="Rotate" /></td>
  <td><span data-ttu-id="44fc0-423">E7AD</span><span class="sxs-lookup"><span data-stu-id="44fc0-423">E7AD</span></span></td>
  <td><span data-ttu-id="44fc0-424">Drehen</span><span class="sxs-lookup"><span data-stu-id="44fc0-424">Rotate</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7B3.png" width="32" height="32" alt="RedEye" /></td>
  <td><span data-ttu-id="44fc0-425">E7B3</span><span class="sxs-lookup"><span data-stu-id="44fc0-425">E7B3</span></span></td>
  <td><span data-ttu-id="44fc0-426">RedEye</span><span class="sxs-lookup"><span data-stu-id="44fc0-426">RedEye</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7B5.png" width="32" height="32" alt="SetlockScreen" /></td>
  <td><span data-ttu-id="44fc0-427">E7B5</span><span class="sxs-lookup"><span data-stu-id="44fc0-427">E7B5</span></span></td>
  <td><span data-ttu-id="44fc0-428">SetLockScreen</span><span class="sxs-lookup"><span data-stu-id="44fc0-428">SetlockScreen</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7B7.png" width="32" height="32" alt="MapPin2" /></td>
  <td><span data-ttu-id="44fc0-429">E7B7</span><span class="sxs-lookup"><span data-stu-id="44fc0-429">E7B7</span></span></td>
  <td><span data-ttu-id="44fc0-430">MapPin2</span><span class="sxs-lookup"><span data-stu-id="44fc0-430">MapPin2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7B8.png" width="32" height="32" alt="Package" /></td>
  <td><span data-ttu-id="44fc0-431">E7B8</span><span class="sxs-lookup"><span data-stu-id="44fc0-431">E7B8</span></span></td>
  <td><span data-ttu-id="44fc0-432">Paket</span><span class="sxs-lookup"><span data-stu-id="44fc0-432">Package</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7BA.png" width="32" height="32" alt="Warning" /></td>
  <td><span data-ttu-id="44fc0-433">E7BA</span><span class="sxs-lookup"><span data-stu-id="44fc0-433">E7BA</span></span></td>
  <td><span data-ttu-id="44fc0-434">Warnung</span><span class="sxs-lookup"><span data-stu-id="44fc0-434">Warning</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7BC.png" width="32" height="32" alt="ReadingList" /></td>
  <td><span data-ttu-id="44fc0-435">E7BC</span><span class="sxs-lookup"><span data-stu-id="44fc0-435">E7BC</span></span></td>
  <td><span data-ttu-id="44fc0-436">ReadingList</span><span class="sxs-lookup"><span data-stu-id="44fc0-436">ReadingList</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7BE.png" width="32" height="32" alt="Education" /></td>
  <td><span data-ttu-id="44fc0-437">E7BE</span><span class="sxs-lookup"><span data-stu-id="44fc0-437">E7BE</span></span></td>
  <td><span data-ttu-id="44fc0-438">Bildung</span><span class="sxs-lookup"><span data-stu-id="44fc0-438">Education</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7BF.png" width="32" height="32" alt="ShoppingCart" /></td>
  <td><span data-ttu-id="44fc0-439">E7BF</span><span class="sxs-lookup"><span data-stu-id="44fc0-439">E7BF</span></span></td>
  <td><span data-ttu-id="44fc0-440">ShoppingCart</span><span class="sxs-lookup"><span data-stu-id="44fc0-440">ShoppingCart</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7C0.png" width="32" height="32" alt="Train" /></td>
  <td><span data-ttu-id="44fc0-441">E7C0</span><span class="sxs-lookup"><span data-stu-id="44fc0-441">E7C0</span></span></td>
  <td><span data-ttu-id="44fc0-442">Train</span><span class="sxs-lookup"><span data-stu-id="44fc0-442">Train</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7C1.png" width="32" height="32" alt="Flag" /></td>
  <td><span data-ttu-id="44fc0-443">E7C1</span><span class="sxs-lookup"><span data-stu-id="44fc0-443">E7C1</span></span></td>
  <td><span data-ttu-id="44fc0-444">Flag</span><span class="sxs-lookup"><span data-stu-id="44fc0-444">Flag</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7C3.png" width="32" height="32" alt="Page" /></td>
  <td><span data-ttu-id="44fc0-445">E7C3</span><span class="sxs-lookup"><span data-stu-id="44fc0-445">E7C3</span></span></td>
  <td><span data-ttu-id="44fc0-446">Seite</span><span class="sxs-lookup"><span data-stu-id="44fc0-446">Page</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7C4.png" width="32" height="32" alt="TaskView" /></td>
  <td><span data-ttu-id="44fc0-447">E7C4</span><span class="sxs-lookup"><span data-stu-id="44fc0-447">E7C4</span></span></td>
  <td><span data-ttu-id="44fc0-448">TaskView</span><span class="sxs-lookup"><span data-stu-id="44fc0-448">TaskView</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7C5.png" width="32" height="32" alt="BrowsePhotos" /></td>
  <td><span data-ttu-id="44fc0-449">E7C5</span><span class="sxs-lookup"><span data-stu-id="44fc0-449">E7C5</span></span></td>
  <td><span data-ttu-id="44fc0-450">BrowsePhotos</span><span class="sxs-lookup"><span data-stu-id="44fc0-450">BrowsePhotos</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7C6.png" width="32" height="32" alt="HalfStarLeft" /></td>
  <td><span data-ttu-id="44fc0-451">E7C6</span><span class="sxs-lookup"><span data-stu-id="44fc0-451">E7C6</span></span></td>
  <td><span data-ttu-id="44fc0-452">HalfStarLeft</span><span class="sxs-lookup"><span data-stu-id="44fc0-452">HalfStarLeft</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7C7.png" width="32" height="32" alt="HalfStarRight" /></td>
  <td><span data-ttu-id="44fc0-453">E7C7</span><span class="sxs-lookup"><span data-stu-id="44fc0-453">E7C7</span></span></td>
  <td><span data-ttu-id="44fc0-454">HalfStarRight</span><span class="sxs-lookup"><span data-stu-id="44fc0-454">HalfStarRight</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7C8.png" width="32" height="32" alt="Record" /></td>
  <td><span data-ttu-id="44fc0-455">E7C8</span><span class="sxs-lookup"><span data-stu-id="44fc0-455">E7C8</span></span></td>
  <td><span data-ttu-id="44fc0-456">Record</span><span class="sxs-lookup"><span data-stu-id="44fc0-456">Record</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7C9.png" width="32" height="32" alt="TouchPointer" /></td>
  <td><span data-ttu-id="44fc0-457">E7C9</span><span class="sxs-lookup"><span data-stu-id="44fc0-457">E7C9</span></span></td>
  <td><span data-ttu-id="44fc0-458">TouchPointer</span><span class="sxs-lookup"><span data-stu-id="44fc0-458">TouchPointer</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7DE.png" width="32" height="32" alt="LangJPN" /></td>
  <td><span data-ttu-id="44fc0-459">E7DE</span><span class="sxs-lookup"><span data-stu-id="44fc0-459">E7DE</span></span></td>
  <td><span data-ttu-id="44fc0-460">LangJPN</span><span class="sxs-lookup"><span data-stu-id="44fc0-460">LangJPN</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7E3.png" width="32" height="32" alt="Ferry" /></td>
  <td><span data-ttu-id="44fc0-461">E7E3</span><span class="sxs-lookup"><span data-stu-id="44fc0-461">E7E3</span></span></td>
  <td><span data-ttu-id="44fc0-462">Ferry</span><span class="sxs-lookup"><span data-stu-id="44fc0-462">Ferry</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7E6.png" width="32" height="32" alt="Highlight" /></td>
  <td><span data-ttu-id="44fc0-463">E7E6</span><span class="sxs-lookup"><span data-stu-id="44fc0-463">E7E6</span></span></td>
  <td><span data-ttu-id="44fc0-464">Hervorheben</span><span class="sxs-lookup"><span data-stu-id="44fc0-464">Highlight</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7E7.png" width="32" height="32" alt="ActionCenterNotification" /></td>
  <td><span data-ttu-id="44fc0-465">E7E7</span><span class="sxs-lookup"><span data-stu-id="44fc0-465">E7E7</span></span></td>
  <td><span data-ttu-id="44fc0-466">ActionCenterNotification</span><span class="sxs-lookup"><span data-stu-id="44fc0-466">ActionCenterNotification</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7E8.png" width="32" height="32" alt="PowerButton" /></td>
  <td><span data-ttu-id="44fc0-467">E7E8</span><span class="sxs-lookup"><span data-stu-id="44fc0-467">E7E8</span></span></td>
  <td><span data-ttu-id="44fc0-468">PowerButton</span><span class="sxs-lookup"><span data-stu-id="44fc0-468">PowerButton</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7EA.png" width="32" height="32" alt="ResizeTouchNarrower" /></td>
  <td><span data-ttu-id="44fc0-469">E7EA</span><span class="sxs-lookup"><span data-stu-id="44fc0-469">E7EA</span></span></td>
  <td><span data-ttu-id="44fc0-470">ResizeTouchNarrower</span><span class="sxs-lookup"><span data-stu-id="44fc0-470">ResizeTouchNarrower</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7EB.png" width="32" height="32" alt="ResizeTouchShorter" /></td>
  <td><span data-ttu-id="44fc0-471">E7EB</span><span class="sxs-lookup"><span data-stu-id="44fc0-471">E7EB</span></span></td>
  <td><span data-ttu-id="44fc0-472">ResizeTouchShorter</span><span class="sxs-lookup"><span data-stu-id="44fc0-472">ResizeTouchShorter</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7EC.png" width="32" height="32" alt="DrivingMode" /></td>
  <td><span data-ttu-id="44fc0-473">E7EC</span><span class="sxs-lookup"><span data-stu-id="44fc0-473">E7EC</span></span></td>
  <td><span data-ttu-id="44fc0-474">DrivingMode</span><span class="sxs-lookup"><span data-stu-id="44fc0-474">DrivingMode</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7ED.png" width="32" height="32" alt="RingerSilent" /></td>
  <td><span data-ttu-id="44fc0-475">E7ED</span><span class="sxs-lookup"><span data-stu-id="44fc0-475">E7ED</span></span></td>
  <td><span data-ttu-id="44fc0-476">RingerSilent</span><span class="sxs-lookup"><span data-stu-id="44fc0-476">RingerSilent</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7EE.png" width="32" height="32" alt="OtherUser" /></td>
  <td><span data-ttu-id="44fc0-477">E7EE</span><span class="sxs-lookup"><span data-stu-id="44fc0-477">E7EE</span></span></td>
  <td><span data-ttu-id="44fc0-478">OtherUser</span><span class="sxs-lookup"><span data-stu-id="44fc0-478">OtherUser</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7EF.png" width="32" height="32" alt="Admin" /></td>
  <td><span data-ttu-id="44fc0-479">E7EF</span><span class="sxs-lookup"><span data-stu-id="44fc0-479">E7EF</span></span></td>
  <td><span data-ttu-id="44fc0-480">Administrator</span><span class="sxs-lookup"><span data-stu-id="44fc0-480">Admin</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7F0.png" width="32" height="32" alt="CC" /></td>
  <td><span data-ttu-id="44fc0-481">E7F0</span><span class="sxs-lookup"><span data-stu-id="44fc0-481">E7F0</span></span></td>
  <td><span data-ttu-id="44fc0-482">CC</span><span class="sxs-lookup"><span data-stu-id="44fc0-482">CC</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7F1.png" width="32" height="32" alt="SDCard" /></td>
  <td><span data-ttu-id="44fc0-483">E7F1</span><span class="sxs-lookup"><span data-stu-id="44fc0-483">E7F1</span></span></td>
  <td><span data-ttu-id="44fc0-484">SDCard</span><span class="sxs-lookup"><span data-stu-id="44fc0-484">SDCard</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7F2.png" width="32" height="32" alt="CallForwarding" /></td>
  <td><span data-ttu-id="44fc0-485">E7F2</span><span class="sxs-lookup"><span data-stu-id="44fc0-485">E7F2</span></span></td>
  <td><span data-ttu-id="44fc0-486">CallForwarding</span><span class="sxs-lookup"><span data-stu-id="44fc0-486">CallForwarding</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7F3.png" width="32" height="32" alt="SettingsDisplaySound" /></td>
  <td><span data-ttu-id="44fc0-487">E7F3</span><span class="sxs-lookup"><span data-stu-id="44fc0-487">E7F3</span></span></td>
  <td><span data-ttu-id="44fc0-488">SettingsDisplaySound</span><span class="sxs-lookup"><span data-stu-id="44fc0-488">SettingsDisplaySound</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7F4.png" width="32" height="32" alt="TVMonitor" /></td>
  <td><span data-ttu-id="44fc0-489">E7F4</span><span class="sxs-lookup"><span data-stu-id="44fc0-489">E7F4</span></span></td>
  <td><span data-ttu-id="44fc0-490">TVMonitor</span><span class="sxs-lookup"><span data-stu-id="44fc0-490">TVMonitor</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7F5.png" width="32" height="32" alt="Speakers" /></td>
  <td><span data-ttu-id="44fc0-491">E7F5</span><span class="sxs-lookup"><span data-stu-id="44fc0-491">E7F5</span></span></td>
  <td><span data-ttu-id="44fc0-492">Lautsprecher</span><span class="sxs-lookup"><span data-stu-id="44fc0-492">Speakers</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7F6.png" width="32" height="32" alt="Headphone" /></td>
  <td><span data-ttu-id="44fc0-493">E7F6</span><span class="sxs-lookup"><span data-stu-id="44fc0-493">E7F6</span></span></td>
  <td><span data-ttu-id="44fc0-494">Headphone</span><span class="sxs-lookup"><span data-stu-id="44fc0-494">Headphone</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7F7.png" width="32" height="32" alt="DeviceLaptopPic" /></td>
  <td><span data-ttu-id="44fc0-495">E7F7</span><span class="sxs-lookup"><span data-stu-id="44fc0-495">E7F7</span></span></td>
  <td><span data-ttu-id="44fc0-496">DeviceLaptopPic</span><span class="sxs-lookup"><span data-stu-id="44fc0-496">DeviceLaptopPic</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7F8.png" width="32" height="32" alt="DeviceLaptopNoPic" /></td>
  <td><span data-ttu-id="44fc0-497">E7F8</span><span class="sxs-lookup"><span data-stu-id="44fc0-497">E7F8</span></span></td>
  <td><span data-ttu-id="44fc0-498">DeviceLaptopNoPic</span><span class="sxs-lookup"><span data-stu-id="44fc0-498">DeviceLaptopNoPic</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7F9.png" width="32" height="32" alt="DeviceMonitorRightPic" /></td>
  <td><span data-ttu-id="44fc0-499">E7F9</span><span class="sxs-lookup"><span data-stu-id="44fc0-499">E7F9</span></span></td>
  <td><span data-ttu-id="44fc0-500">DeviceMonitorRightPic</span><span class="sxs-lookup"><span data-stu-id="44fc0-500">DeviceMonitorRightPic</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7FA.png" width="32" height="32" alt="DeviceMonitorLeftPic" /></td>
  <td><span data-ttu-id="44fc0-501">E7FA</span><span class="sxs-lookup"><span data-stu-id="44fc0-501">E7FA</span></span></td>
  <td><span data-ttu-id="44fc0-502">DeviceMonitorLeftPic</span><span class="sxs-lookup"><span data-stu-id="44fc0-502">DeviceMonitorLeftPic</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7FB.png" width="32" height="32" alt="DeviceMonitorNoPic" /></td>
  <td><span data-ttu-id="44fc0-503">E7FB</span><span class="sxs-lookup"><span data-stu-id="44fc0-503">E7FB</span></span></td>
  <td><span data-ttu-id="44fc0-504">DeviceMonitorNoPic</span><span class="sxs-lookup"><span data-stu-id="44fc0-504">DeviceMonitorNoPic</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7FC.png" width="32" height="32" alt="Game" /></td>
  <td><span data-ttu-id="44fc0-505">E7FC</span><span class="sxs-lookup"><span data-stu-id="44fc0-505">E7FC</span></span></td>
  <td><span data-ttu-id="44fc0-506">Game</span><span class="sxs-lookup"><span data-stu-id="44fc0-506">Game</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E7FD.png" width="32" height="32" alt="HorizontalTabKey" /></td>
  <td><span data-ttu-id="44fc0-507">E7FD</span><span class="sxs-lookup"><span data-stu-id="44fc0-507">E7FD</span></span></td>
  <td><span data-ttu-id="44fc0-508">HorizontalTabKey</span><span class="sxs-lookup"><span data-stu-id="44fc0-508">HorizontalTabKey</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E802.png" width="32" height="32" alt="StreetsideSplitMinimize" /></td>
  <td><span data-ttu-id="44fc0-509">E802</span><span class="sxs-lookup"><span data-stu-id="44fc0-509">E802</span></span></td>
  <td><span data-ttu-id="44fc0-510">StreetsideSplitMinimize</span><span class="sxs-lookup"><span data-stu-id="44fc0-510">StreetsideSplitMinimize</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E803.png" width="32" height="32" alt="StreetsideSplitExpand" /></td>
  <td><span data-ttu-id="44fc0-511">E803</span><span class="sxs-lookup"><span data-stu-id="44fc0-511">E803</span></span></td>
  <td><span data-ttu-id="44fc0-512">StreetsideSplitExpand</span><span class="sxs-lookup"><span data-stu-id="44fc0-512">StreetsideSplitExpand</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E804.png" width="32" height="32" alt="Car" /></td>
  <td><span data-ttu-id="44fc0-513">E804</span><span class="sxs-lookup"><span data-stu-id="44fc0-513">E804</span></span></td>
  <td><span data-ttu-id="44fc0-514">Car</span><span class="sxs-lookup"><span data-stu-id="44fc0-514">Car</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E805.png" width="32" height="32" alt="Walk" /></td>
  <td><span data-ttu-id="44fc0-515">E805</span><span class="sxs-lookup"><span data-stu-id="44fc0-515">E805</span></span></td>
  <td><span data-ttu-id="44fc0-516">Walk</span><span class="sxs-lookup"><span data-stu-id="44fc0-516">Walk</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E806.png" width="32" height="32" alt="Bus" /></td>
  <td><span data-ttu-id="44fc0-517">E806</span><span class="sxs-lookup"><span data-stu-id="44fc0-517">E806</span></span></td>
  <td><span data-ttu-id="44fc0-518">Bus</span><span class="sxs-lookup"><span data-stu-id="44fc0-518">Bus</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E809.png" width="32" height="32" alt="TiltUp" /></td>
  <td><span data-ttu-id="44fc0-519">E809</span><span class="sxs-lookup"><span data-stu-id="44fc0-519">E809</span></span></td>
  <td><span data-ttu-id="44fc0-520">TiltUp</span><span class="sxs-lookup"><span data-stu-id="44fc0-520">TiltUp</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E80A.png" width="32" height="32" alt="TiltDown" /></td>
  <td><span data-ttu-id="44fc0-521">E80A</span><span class="sxs-lookup"><span data-stu-id="44fc0-521">E80A</span></span></td>
  <td><span data-ttu-id="44fc0-522">TiltDown</span><span class="sxs-lookup"><span data-stu-id="44fc0-522">TiltDown</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E80C.png" width="32" height="32" alt="RotateMapRight" /></td>
  <td><span data-ttu-id="44fc0-523">E80C</span><span class="sxs-lookup"><span data-stu-id="44fc0-523">E80C</span></span></td>
  <td><span data-ttu-id="44fc0-524">RotateMapRight</span><span class="sxs-lookup"><span data-stu-id="44fc0-524">RotateMapRight</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E80D.png" width="32" height="32" alt="RotateMapLeft" /></td>
  <td><span data-ttu-id="44fc0-525">E80D</span><span class="sxs-lookup"><span data-stu-id="44fc0-525">E80D</span></span></td>
  <td><span data-ttu-id="44fc0-526">RotateMapLeft</span><span class="sxs-lookup"><span data-stu-id="44fc0-526">RotateMapLeft</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E80F.png" width="32" height="32" alt="Home" /></td>
  <td><span data-ttu-id="44fc0-527">E80F</span><span class="sxs-lookup"><span data-stu-id="44fc0-527">E80F</span></span></td>
  <td><span data-ttu-id="44fc0-528">Startseite</span><span class="sxs-lookup"><span data-stu-id="44fc0-528">Home</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E811.png" width="32" height="32" alt="ParkingLocation" /></td>
  <td><span data-ttu-id="44fc0-529">E811</span><span class="sxs-lookup"><span data-stu-id="44fc0-529">E811</span></span></td>
  <td><span data-ttu-id="44fc0-530">ParkingLocation</span><span class="sxs-lookup"><span data-stu-id="44fc0-530">ParkingLocation</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E812.png" width="32" height="32" alt="MapCompassTop" /></td>
  <td><span data-ttu-id="44fc0-531">E812</span><span class="sxs-lookup"><span data-stu-id="44fc0-531">E812</span></span></td>
  <td><span data-ttu-id="44fc0-532">MapCompassTop</span><span class="sxs-lookup"><span data-stu-id="44fc0-532">MapCompassTop</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E813.png" width="32" height="32" alt="MapCompassBottom" /></td>
  <td><span data-ttu-id="44fc0-533">E813</span><span class="sxs-lookup"><span data-stu-id="44fc0-533">E813</span></span></td>
  <td><span data-ttu-id="44fc0-534">MapCompassBottom</span><span class="sxs-lookup"><span data-stu-id="44fc0-534">MapCompassBottom</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E814.png" width="32" height="32" alt="IncidentTriangle" /></td>
  <td><span data-ttu-id="44fc0-535">E814</span><span class="sxs-lookup"><span data-stu-id="44fc0-535">E814</span></span></td>
  <td><span data-ttu-id="44fc0-536">IncidentTriangle</span><span class="sxs-lookup"><span data-stu-id="44fc0-536">IncidentTriangle</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E815.png" width="32" height="32" alt="Touch" /></td>
  <td><span data-ttu-id="44fc0-537">E815</span><span class="sxs-lookup"><span data-stu-id="44fc0-537">E815</span></span></td>
  <td><span data-ttu-id="44fc0-538">Toucheingabe</span><span class="sxs-lookup"><span data-stu-id="44fc0-538">Touch</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E816.png" width="32" height="32" alt="MapDirections" /></td>
  <td><span data-ttu-id="44fc0-539">E816</span><span class="sxs-lookup"><span data-stu-id="44fc0-539">E816</span></span></td>
  <td><span data-ttu-id="44fc0-540">MapDirections</span><span class="sxs-lookup"><span data-stu-id="44fc0-540">MapDirections</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E819.png" width="32" height="32" alt="StartPoint" /></td>
  <td><span data-ttu-id="44fc0-541">E819</span><span class="sxs-lookup"><span data-stu-id="44fc0-541">E819</span></span></td>
  <td><span data-ttu-id="44fc0-542">StartPoint</span><span class="sxs-lookup"><span data-stu-id="44fc0-542">StartPoint</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E81A.png" width="32" height="32" alt="StopPoint" /></td>
  <td><span data-ttu-id="44fc0-543">E81A</span><span class="sxs-lookup"><span data-stu-id="44fc0-543">E81A</span></span></td>
  <td><span data-ttu-id="44fc0-544">StopPoint</span><span class="sxs-lookup"><span data-stu-id="44fc0-544">StopPoint</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E81B.png" width="32" height="32" alt="EndPoint" /></td>
  <td><span data-ttu-id="44fc0-545">E81B</span><span class="sxs-lookup"><span data-stu-id="44fc0-545">E81B</span></span></td>
  <td><span data-ttu-id="44fc0-546">EndPoint</span><span class="sxs-lookup"><span data-stu-id="44fc0-546">EndPoint</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E81C.png" width="32" height="32" alt="History" /></td>
  <td><span data-ttu-id="44fc0-547">E81C</span><span class="sxs-lookup"><span data-stu-id="44fc0-547">E81C</span></span></td>
  <td><span data-ttu-id="44fc0-548">Verlauf</span><span class="sxs-lookup"><span data-stu-id="44fc0-548">History</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E81D.png" width="32" height="32" alt="Location" /></td>
  <td><span data-ttu-id="44fc0-549">E81D</span><span class="sxs-lookup"><span data-stu-id="44fc0-549">E81D</span></span></td>
  <td><span data-ttu-id="44fc0-550">Speicherort</span><span class="sxs-lookup"><span data-stu-id="44fc0-550">Location</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E81E.png" width="32" height="32" alt="MapLayers" /></td>
  <td><span data-ttu-id="44fc0-551">E81E</span><span class="sxs-lookup"><span data-stu-id="44fc0-551">E81E</span></span></td>
  <td><span data-ttu-id="44fc0-552">MapLayers</span><span class="sxs-lookup"><span data-stu-id="44fc0-552">MapLayers</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E81F.png" width="32" height="32" alt="Accident" /></td>
  <td><span data-ttu-id="44fc0-553">E81F</span><span class="sxs-lookup"><span data-stu-id="44fc0-553">E81F</span></span></td>
  <td><span data-ttu-id="44fc0-554">Accident</span><span class="sxs-lookup"><span data-stu-id="44fc0-554">Accident</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E821.png" width="32" height="32" alt="Work" /></td>
  <td><span data-ttu-id="44fc0-555">E821</span><span class="sxs-lookup"><span data-stu-id="44fc0-555">E821</span></span></td>
  <td><span data-ttu-id="44fc0-556">Aufgabe</span><span class="sxs-lookup"><span data-stu-id="44fc0-556">Work</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E822.png" width="32" height="32" alt="Construction" /></td>
  <td><span data-ttu-id="44fc0-557">E822</span><span class="sxs-lookup"><span data-stu-id="44fc0-557">E822</span></span></td>
  <td><span data-ttu-id="44fc0-558">Construction</span><span class="sxs-lookup"><span data-stu-id="44fc0-558">Construction</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E823.png" width="32" height="32" alt="Recent" /></td>
  <td><span data-ttu-id="44fc0-559">E823</span><span class="sxs-lookup"><span data-stu-id="44fc0-559">E823</span></span></td>
  <td><span data-ttu-id="44fc0-560">Zuletzt verwendet</span><span class="sxs-lookup"><span data-stu-id="44fc0-560">Recent</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E825.png" width="32" height="32" alt="Bank" /></td>
  <td><span data-ttu-id="44fc0-561">E825</span><span class="sxs-lookup"><span data-stu-id="44fc0-561">E825</span></span></td>
  <td><span data-ttu-id="44fc0-562">Bank</span><span class="sxs-lookup"><span data-stu-id="44fc0-562">Bank</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E826.png" width="32" height="32" alt="DownloadMap" /></td>
  <td><span data-ttu-id="44fc0-563">E826</span><span class="sxs-lookup"><span data-stu-id="44fc0-563">E826</span></span></td>
  <td><span data-ttu-id="44fc0-564">DownloadMap</span><span class="sxs-lookup"><span data-stu-id="44fc0-564">DownloadMap</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E829.png" width="32" height="32" alt="InkingToolFill2" /></td>
  <td><span data-ttu-id="44fc0-565">E829</span><span class="sxs-lookup"><span data-stu-id="44fc0-565">E829</span></span></td>
  <td><span data-ttu-id="44fc0-566">InkingToolFill2</span><span class="sxs-lookup"><span data-stu-id="44fc0-566">InkingToolFill2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E82A.png" width="32" height="32" alt="HighlightFill2" /></td>
  <td><span data-ttu-id="44fc0-567">E82A</span><span class="sxs-lookup"><span data-stu-id="44fc0-567">E82A</span></span></td>
  <td><span data-ttu-id="44fc0-568">HighlightFill2</span><span class="sxs-lookup"><span data-stu-id="44fc0-568">HighlightFill2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E82B.png" width="32" height="32" alt="EraseToolFill" /></td>
  <td><span data-ttu-id="44fc0-569">E82B</span><span class="sxs-lookup"><span data-stu-id="44fc0-569">E82B</span></span></td>
  <td><span data-ttu-id="44fc0-570">EraseToolFill</span><span class="sxs-lookup"><span data-stu-id="44fc0-570">EraseToolFill</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E82C.png" width="32" height="32" alt="EraseToolFill2" /></td>
  <td><span data-ttu-id="44fc0-571">E82C</span><span class="sxs-lookup"><span data-stu-id="44fc0-571">E82C</span></span></td>
  <td><span data-ttu-id="44fc0-572">EraseToolFill2</span><span class="sxs-lookup"><span data-stu-id="44fc0-572">EraseToolFill2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E82D.png" width="32" height="32" alt="Dictionary" /></td>
  <td><span data-ttu-id="44fc0-573">E82D</span><span class="sxs-lookup"><span data-stu-id="44fc0-573">E82D</span></span></td>
  <td><span data-ttu-id="44fc0-574">Dictionary</span><span class="sxs-lookup"><span data-stu-id="44fc0-574">Dictionary</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E82E.png" width="32" height="32" alt="DictionaryAdd" /></td>
  <td><span data-ttu-id="44fc0-575">E82E</span><span class="sxs-lookup"><span data-stu-id="44fc0-575">E82E</span></span></td>
  <td><span data-ttu-id="44fc0-576">DictionaryAdd</span><span class="sxs-lookup"><span data-stu-id="44fc0-576">DictionaryAdd</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E82F.png" width="32" height="32" alt="ToolTip" /></td>
  <td><span data-ttu-id="44fc0-577">E82F</span><span class="sxs-lookup"><span data-stu-id="44fc0-577">E82F</span></span></td>
  <td><span data-ttu-id="44fc0-578">ToolTip</span><span class="sxs-lookup"><span data-stu-id="44fc0-578">ToolTip</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E830.png" width="32" height="32" alt="ChromeBack" /></td>
  <td><span data-ttu-id="44fc0-579">E830</span><span class="sxs-lookup"><span data-stu-id="44fc0-579">E830</span></span></td>
  <td><span data-ttu-id="44fc0-580">ChromeBack</span><span class="sxs-lookup"><span data-stu-id="44fc0-580">ChromeBack</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E835.png" width="32" height="32" alt="ProvisioningPackage" /></td>
  <td><span data-ttu-id="44fc0-581">E835</span><span class="sxs-lookup"><span data-stu-id="44fc0-581">E835</span></span></td>
  <td><span data-ttu-id="44fc0-582">ProvisioningPackage</span><span class="sxs-lookup"><span data-stu-id="44fc0-582">ProvisioningPackage</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E836.png" width="32" height="32" alt="AddRemoteDevice" /></td>
  <td><span data-ttu-id="44fc0-583">E836</span><span class="sxs-lookup"><span data-stu-id="44fc0-583">E836</span></span></td>
  <td><span data-ttu-id="44fc0-584">AddRemoteDevice</span><span class="sxs-lookup"><span data-stu-id="44fc0-584">AddRemoteDevice</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E838.png" width="32" height="32" alt="FolderOpen" /></td>
  <td><span data-ttu-id="44fc0-585">E838</span><span class="sxs-lookup"><span data-stu-id="44fc0-585">E838</span></span></td>
  <td><span data-ttu-id="44fc0-586">FolderOpen</span><span class="sxs-lookup"><span data-stu-id="44fc0-586">FolderOpen</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E839.png" width="32" height="32" alt="Ethernet" /></td>
  <td><span data-ttu-id="44fc0-587">E839</span><span class="sxs-lookup"><span data-stu-id="44fc0-587">E839</span></span></td>
  <td><span data-ttu-id="44fc0-588">Ethernet</span><span class="sxs-lookup"><span data-stu-id="44fc0-588">Ethernet</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E83A.png" width="32" height="32" alt=" ShareBroadband" /></td>
  <td><span data-ttu-id="44fc0-589">E83A</span><span class="sxs-lookup"><span data-stu-id="44fc0-589">E83A</span></span></td>
  <td> <span data-ttu-id="44fc0-590">ShareBroadband</span><span class="sxs-lookup"><span data-stu-id="44fc0-590">ShareBroadband</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E83B.png" width="32" height="32" alt="DirectAccess" /></td>
  <td><span data-ttu-id="44fc0-591">E83B</span><span class="sxs-lookup"><span data-stu-id="44fc0-591">E83B</span></span></td>
  <td><span data-ttu-id="44fc0-592">DirectAccess</span><span class="sxs-lookup"><span data-stu-id="44fc0-592">DirectAccess</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E83C.png" width="32" height="32" alt=" DialUp" /></td>
  <td><span data-ttu-id="44fc0-593">E83C</span><span class="sxs-lookup"><span data-stu-id="44fc0-593">E83C</span></span></td>
  <td> <span data-ttu-id="44fc0-594">DialUp</span><span class="sxs-lookup"><span data-stu-id="44fc0-594">DialUp</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E83D.png" width="32" height="32" alt="DefenderApp " /></td>
  <td><span data-ttu-id="44fc0-595">E83D</span><span class="sxs-lookup"><span data-stu-id="44fc0-595">E83D</span></span></td>
  <td><span data-ttu-id="44fc0-596">DefenderApp</span><span class="sxs-lookup"><span data-stu-id="44fc0-596">DefenderApp</span></span> </td>
 </tr>
<tr><td><img src="images/segoe-mdl/E83E.png" width="32" height="32" alt="BatteryCharging9" /></td>
  <td><span data-ttu-id="44fc0-597">E83E</span><span class="sxs-lookup"><span data-stu-id="44fc0-597">E83E</span></span></td>
  <td><span data-ttu-id="44fc0-598">BatteryCharging9</span><span class="sxs-lookup"><span data-stu-id="44fc0-598">BatteryCharging9</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E83F.png" width="32" height="32" alt="Battery10" /></td>
  <td><span data-ttu-id="44fc0-599">E83F</span><span class="sxs-lookup"><span data-stu-id="44fc0-599">E83F</span></span></td>
  <td><span data-ttu-id="44fc0-600">Battery10</span><span class="sxs-lookup"><span data-stu-id="44fc0-600">Battery10</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E840.png" width="32" height="32" alt="Pinned" /></td>
  <td><span data-ttu-id="44fc0-601">E840</span><span class="sxs-lookup"><span data-stu-id="44fc0-601">E840</span></span></td>
  <td><span data-ttu-id="44fc0-602">Pinned</span><span class="sxs-lookup"><span data-stu-id="44fc0-602">Pinned</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E841.png" width="32" height="32" alt="PinFill" /></td>
  <td><span data-ttu-id="44fc0-603">E841</span><span class="sxs-lookup"><span data-stu-id="44fc0-603">E841</span></span></td>
  <td><span data-ttu-id="44fc0-604">PinFill</span><span class="sxs-lookup"><span data-stu-id="44fc0-604">PinFill</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E842.png" width="32" height="32" alt="PinnedFill" /></td>
  <td><span data-ttu-id="44fc0-605">E842</span><span class="sxs-lookup"><span data-stu-id="44fc0-605">E842</span></span></td>
  <td><span data-ttu-id="44fc0-606">PinnedFill</span><span class="sxs-lookup"><span data-stu-id="44fc0-606">PinnedFill</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E843.png" width="32" height="32" alt="PeriodKey" /></td>
  <td><span data-ttu-id="44fc0-607">E843</span><span class="sxs-lookup"><span data-stu-id="44fc0-607">E843</span></span></td>
  <td><span data-ttu-id="44fc0-608">PeriodKey</span><span class="sxs-lookup"><span data-stu-id="44fc0-608">PeriodKey</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E844.png" width="32" height="32" alt="PuncKey" /></td>
  <td><span data-ttu-id="44fc0-609">E844</span><span class="sxs-lookup"><span data-stu-id="44fc0-609">E844</span></span></td>
  <td><span data-ttu-id="44fc0-610">PuncKey</span><span class="sxs-lookup"><span data-stu-id="44fc0-610">PuncKey</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E845.png" width="32" height="32" alt="RevToggleKey" /></td>
  <td><span data-ttu-id="44fc0-611">E845</span><span class="sxs-lookup"><span data-stu-id="44fc0-611">E845</span></span></td>
  <td><span data-ttu-id="44fc0-612">RevToggleKey</span><span class="sxs-lookup"><span data-stu-id="44fc0-612">RevToggleKey</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E846.png" width="32" height="32" alt="RightArrowKeyTime1" /></td>
  <td><span data-ttu-id="44fc0-613">E846</span><span class="sxs-lookup"><span data-stu-id="44fc0-613">E846</span></span></td>
  <td><span data-ttu-id="44fc0-614">RightArrowKeyTime1</span><span class="sxs-lookup"><span data-stu-id="44fc0-614">RightArrowKeyTime1</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E847.png" width="32" height="32" alt="RightArrowKeyTime2" /></td>
  <td><span data-ttu-id="44fc0-615">E847</span><span class="sxs-lookup"><span data-stu-id="44fc0-615">E847</span></span></td>
  <td><span data-ttu-id="44fc0-616">RightArrowKeyTime2</span><span class="sxs-lookup"><span data-stu-id="44fc0-616">RightArrowKeyTime2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E848.png" width="32" height="32" alt="LeftQuote" /></td>
  <td><span data-ttu-id="44fc0-617">E848</span><span class="sxs-lookup"><span data-stu-id="44fc0-617">E848</span></span></td>
  <td><span data-ttu-id="44fc0-618">LeftQuote</span><span class="sxs-lookup"><span data-stu-id="44fc0-618">LeftQuote</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E849.png" width="32" height="32" alt="RightQuote" /></td>
  <td><span data-ttu-id="44fc0-619">E849</span><span class="sxs-lookup"><span data-stu-id="44fc0-619">E849</span></span></td>
  <td><span data-ttu-id="44fc0-620">RightQuote</span><span class="sxs-lookup"><span data-stu-id="44fc0-620">RightQuote</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E84A.png" width="32" height="32" alt="DownShiftKey" /></td>
  <td><span data-ttu-id="44fc0-621">E84A</span><span class="sxs-lookup"><span data-stu-id="44fc0-621">E84A</span></span></td>
  <td><span data-ttu-id="44fc0-622">DownShiftKey</span><span class="sxs-lookup"><span data-stu-id="44fc0-622">DownShiftKey</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E84B.png" width="32" height="32" alt="UpShiftKey" /></td>
  <td><span data-ttu-id="44fc0-623">E84B</span><span class="sxs-lookup"><span data-stu-id="44fc0-623">E84B</span></span></td>
  <td><span data-ttu-id="44fc0-624">UpShiftKey</span><span class="sxs-lookup"><span data-stu-id="44fc0-624">UpShiftKey</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E84C.png" width="32" height="32" alt="PuncKey0" /></td>
  <td><span data-ttu-id="44fc0-625">E84C</span><span class="sxs-lookup"><span data-stu-id="44fc0-625">E84C</span></span></td>
  <td><span data-ttu-id="44fc0-626">PuncKey0</span><span class="sxs-lookup"><span data-stu-id="44fc0-626">PuncKey0</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E84D.png" width="32" height="32" alt="PuncKeyLeftBottom" /></td>
  <td><span data-ttu-id="44fc0-627">E84D</span><span class="sxs-lookup"><span data-stu-id="44fc0-627">E84D</span></span></td>
  <td><span data-ttu-id="44fc0-628">PuncKeyLeftBottom</span><span class="sxs-lookup"><span data-stu-id="44fc0-628">PuncKeyLeftBottom</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E84E.png" width="32" height="32" alt="RightArrowKeyTime3" /></td>
  <td><span data-ttu-id="44fc0-629">E84E</span><span class="sxs-lookup"><span data-stu-id="44fc0-629">E84E</span></span></td>
  <td><span data-ttu-id="44fc0-630">RightArrowKeyTime3</span><span class="sxs-lookup"><span data-stu-id="44fc0-630">RightArrowKeyTime3</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E84F.png" width="32" height="32" alt="RightArrowKeyTime4" /></td>
  <td><span data-ttu-id="44fc0-631">E84F</span><span class="sxs-lookup"><span data-stu-id="44fc0-631">E84F</span></span></td>
  <td><span data-ttu-id="44fc0-632">RightArrowKeyTime4</span><span class="sxs-lookup"><span data-stu-id="44fc0-632">RightArrowKeyTime4</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E850.png" width="32" height="32" alt="Battery0" /></td>
  <td><span data-ttu-id="44fc0-633">E850</span><span class="sxs-lookup"><span data-stu-id="44fc0-633">E850</span></span></td>
  <td><span data-ttu-id="44fc0-634">Battery0</span><span class="sxs-lookup"><span data-stu-id="44fc0-634">Battery0</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E851.png" width="32" height="32" alt="Battery1" /></td>
  <td><span data-ttu-id="44fc0-635">E851</span><span class="sxs-lookup"><span data-stu-id="44fc0-635">E851</span></span></td>
  <td><span data-ttu-id="44fc0-636">Battery1</span><span class="sxs-lookup"><span data-stu-id="44fc0-636">Battery1</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E852.png" width="32" height="32" alt="Battery2" /></td>
  <td><span data-ttu-id="44fc0-637">E852</span><span class="sxs-lookup"><span data-stu-id="44fc0-637">E852</span></span></td>
  <td><span data-ttu-id="44fc0-638">Battery2</span><span class="sxs-lookup"><span data-stu-id="44fc0-638">Battery2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E853.png" width="32" height="32" alt="Battery3" /></td>
  <td><span data-ttu-id="44fc0-639">E853</span><span class="sxs-lookup"><span data-stu-id="44fc0-639">E853</span></span></td>
  <td><span data-ttu-id="44fc0-640">Battery3</span><span class="sxs-lookup"><span data-stu-id="44fc0-640">Battery3</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E854.png" width="32" height="32" alt="Battery4" /></td>
  <td><span data-ttu-id="44fc0-641">E854</span><span class="sxs-lookup"><span data-stu-id="44fc0-641">E854</span></span></td>
  <td><span data-ttu-id="44fc0-642">Battery4</span><span class="sxs-lookup"><span data-stu-id="44fc0-642">Battery4</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E855.png" width="32" height="32" alt="Battery5" /></td>
  <td><span data-ttu-id="44fc0-643">E855</span><span class="sxs-lookup"><span data-stu-id="44fc0-643">E855</span></span></td>
  <td><span data-ttu-id="44fc0-644">Battery5</span><span class="sxs-lookup"><span data-stu-id="44fc0-644">Battery5</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E856.png" width="32" height="32" alt="Battery6" /></td>
  <td><span data-ttu-id="44fc0-645">E856</span><span class="sxs-lookup"><span data-stu-id="44fc0-645">E856</span></span></td>
  <td><span data-ttu-id="44fc0-646">Battery6</span><span class="sxs-lookup"><span data-stu-id="44fc0-646">Battery6</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E857.png" width="32" height="32" alt="Battery7" /></td>
  <td><span data-ttu-id="44fc0-647">E857</span><span class="sxs-lookup"><span data-stu-id="44fc0-647">E857</span></span></td>
  <td><span data-ttu-id="44fc0-648">Battery7</span><span class="sxs-lookup"><span data-stu-id="44fc0-648">Battery7</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E858.png" width="32" height="32" alt="Battery8" /></td>
  <td><span data-ttu-id="44fc0-649">E858</span><span class="sxs-lookup"><span data-stu-id="44fc0-649">E858</span></span></td>
  <td><span data-ttu-id="44fc0-650">Battery8</span><span class="sxs-lookup"><span data-stu-id="44fc0-650">Battery8</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E859.png" width="32" height="32" alt="Battery9" /></td>
  <td><span data-ttu-id="44fc0-651">E859</span><span class="sxs-lookup"><span data-stu-id="44fc0-651">E859</span></span></td>
  <td><span data-ttu-id="44fc0-652">Battery9</span><span class="sxs-lookup"><span data-stu-id="44fc0-652">Battery9</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E85A.png" width="32" height="32" alt="BatteryCharging0" /></td>
  <td><span data-ttu-id="44fc0-653">E85A</span><span class="sxs-lookup"><span data-stu-id="44fc0-653">E85A</span></span></td>
  <td><span data-ttu-id="44fc0-654">BatteryCharging0</span><span class="sxs-lookup"><span data-stu-id="44fc0-654">BatteryCharging0</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E85B.png" width="32" height="32" alt="BatteryCharging1" /></td>
  <td><span data-ttu-id="44fc0-655">E85B</span><span class="sxs-lookup"><span data-stu-id="44fc0-655">E85B</span></span></td>
  <td><span data-ttu-id="44fc0-656">BatteryCharging1</span><span class="sxs-lookup"><span data-stu-id="44fc0-656">BatteryCharging1</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E85C.png" width="32" height="32" alt="BatteryCharging2" /></td>
  <td><span data-ttu-id="44fc0-657">E85C</span><span class="sxs-lookup"><span data-stu-id="44fc0-657">E85C</span></span></td>
  <td><span data-ttu-id="44fc0-658">BatteryCharging2</span><span class="sxs-lookup"><span data-stu-id="44fc0-658">BatteryCharging2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E85D.png" width="32" height="32" alt="BatteryCharging3" /></td>
  <td><span data-ttu-id="44fc0-659">E85D</span><span class="sxs-lookup"><span data-stu-id="44fc0-659">E85D</span></span></td>
  <td><span data-ttu-id="44fc0-660">BatteryCharging3</span><span class="sxs-lookup"><span data-stu-id="44fc0-660">BatteryCharging3</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E85E.png" width="32" height="32" alt="BatteryCharging4" /></td>
  <td><span data-ttu-id="44fc0-661">E85E</span><span class="sxs-lookup"><span data-stu-id="44fc0-661">E85E</span></span></td>
  <td><span data-ttu-id="44fc0-662">BatteryCharging4</span><span class="sxs-lookup"><span data-stu-id="44fc0-662">BatteryCharging4</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E85F.png" width="32" height="32" alt="BatteryCharging5" /></td>
  <td><span data-ttu-id="44fc0-663">E85F</span><span class="sxs-lookup"><span data-stu-id="44fc0-663">E85F</span></span></td>
  <td><span data-ttu-id="44fc0-664">BatteryCharging5</span><span class="sxs-lookup"><span data-stu-id="44fc0-664">BatteryCharging5</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E860.png" width="32" height="32" alt="BatteryCharging6" /></td>
  <td><span data-ttu-id="44fc0-665">E860</span><span class="sxs-lookup"><span data-stu-id="44fc0-665">E860</span></span></td>
  <td><span data-ttu-id="44fc0-666">BatteryCharging6</span><span class="sxs-lookup"><span data-stu-id="44fc0-666">BatteryCharging6</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E861.png" width="32" height="32" alt="BatteryCharging7" /></td>
  <td><span data-ttu-id="44fc0-667">E861</span><span class="sxs-lookup"><span data-stu-id="44fc0-667">E861</span></span></td>
  <td><span data-ttu-id="44fc0-668">BatteryCharging7</span><span class="sxs-lookup"><span data-stu-id="44fc0-668">BatteryCharging7</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E862.png" width="32" height="32" alt="BatteryCharging8" /></td>
  <td><span data-ttu-id="44fc0-669">E862</span><span class="sxs-lookup"><span data-stu-id="44fc0-669">E862</span></span></td>
  <td><span data-ttu-id="44fc0-670">BatteryCharging8</span><span class="sxs-lookup"><span data-stu-id="44fc0-670">BatteryCharging8</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E863.png" width="32" height="32" alt="BatterySaver0" /></td>
  <td><span data-ttu-id="44fc0-671">E863</span><span class="sxs-lookup"><span data-stu-id="44fc0-671">E863</span></span></td>
  <td><span data-ttu-id="44fc0-672">BatterySaver0</span><span class="sxs-lookup"><span data-stu-id="44fc0-672">BatterySaver0</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E864.png" width="32" height="32" alt="BatterySaver1" /></td>
  <td><span data-ttu-id="44fc0-673">E864</span><span class="sxs-lookup"><span data-stu-id="44fc0-673">E864</span></span></td>
  <td><span data-ttu-id="44fc0-674">BatterySaver1</span><span class="sxs-lookup"><span data-stu-id="44fc0-674">BatterySaver1</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E865.png" width="32" height="32" alt="BatterySaver2" /></td>
  <td><span data-ttu-id="44fc0-675">E865</span><span class="sxs-lookup"><span data-stu-id="44fc0-675">E865</span></span></td>
  <td><span data-ttu-id="44fc0-676">BatterySaver2</span><span class="sxs-lookup"><span data-stu-id="44fc0-676">BatterySaver2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E866.png" width="32" height="32" alt="BatterySaver3" /></td>
  <td><span data-ttu-id="44fc0-677">E866</span><span class="sxs-lookup"><span data-stu-id="44fc0-677">E866</span></span></td>
  <td><span data-ttu-id="44fc0-678">BatterySaver3</span><span class="sxs-lookup"><span data-stu-id="44fc0-678">BatterySaver3</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E867.png" width="32" height="32" alt="BatterySaver4" /></td>
  <td><span data-ttu-id="44fc0-679">E867</span><span class="sxs-lookup"><span data-stu-id="44fc0-679">E867</span></span></td>
  <td><span data-ttu-id="44fc0-680">BatterySaver4</span><span class="sxs-lookup"><span data-stu-id="44fc0-680">BatterySaver4</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E868.png" width="32" height="32" alt="BatterySaver5" /></td>
  <td><span data-ttu-id="44fc0-681">E868</span><span class="sxs-lookup"><span data-stu-id="44fc0-681">E868</span></span></td>
  <td><span data-ttu-id="44fc0-682">BatterySaver5</span><span class="sxs-lookup"><span data-stu-id="44fc0-682">BatterySaver5</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E869.png" width="32" height="32" alt="BatterySaver6" /></td>
  <td><span data-ttu-id="44fc0-683">E869</span><span class="sxs-lookup"><span data-stu-id="44fc0-683">E869</span></span></td>
  <td><span data-ttu-id="44fc0-684">BatterySaver6</span><span class="sxs-lookup"><span data-stu-id="44fc0-684">BatterySaver6</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E86A.png" width="32" height="32" alt="BatterySaver7" /></td>
  <td><span data-ttu-id="44fc0-685">E86A</span><span class="sxs-lookup"><span data-stu-id="44fc0-685">E86A</span></span></td>
  <td><span data-ttu-id="44fc0-686">BatterySaver7</span><span class="sxs-lookup"><span data-stu-id="44fc0-686">BatterySaver7</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E86B.png" width="32" height="32" alt="BatterySaver8" /></td>
  <td><span data-ttu-id="44fc0-687">E86B</span><span class="sxs-lookup"><span data-stu-id="44fc0-687">E86B</span></span></td>
  <td><span data-ttu-id="44fc0-688">BatterySaver8</span><span class="sxs-lookup"><span data-stu-id="44fc0-688">BatterySaver8</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E86C.png" width="32" height="32" alt="SignalBars1" /></td>
  <td><span data-ttu-id="44fc0-689">E86C</span><span class="sxs-lookup"><span data-stu-id="44fc0-689">E86C</span></span></td>
  <td><span data-ttu-id="44fc0-690">SignalBars1</span><span class="sxs-lookup"><span data-stu-id="44fc0-690">SignalBars1</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E86D.png" width="32" height="32" alt="SignalBars2" /></td>
  <td><span data-ttu-id="44fc0-691">E86D</span><span class="sxs-lookup"><span data-stu-id="44fc0-691">E86D</span></span></td>
  <td><span data-ttu-id="44fc0-692">SignalBars2</span><span class="sxs-lookup"><span data-stu-id="44fc0-692">SignalBars2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E86E.png" width="32" height="32" alt="SignalBars3" /></td>
  <td><span data-ttu-id="44fc0-693">E86E</span><span class="sxs-lookup"><span data-stu-id="44fc0-693">E86E</span></span></td>
  <td><span data-ttu-id="44fc0-694">SignalBars3</span><span class="sxs-lookup"><span data-stu-id="44fc0-694">SignalBars3</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E86F.png" width="32" height="32" alt="SignalBars4" /></td>
  <td><span data-ttu-id="44fc0-695">E86F</span><span class="sxs-lookup"><span data-stu-id="44fc0-695">E86F</span></span></td>
  <td><span data-ttu-id="44fc0-696">SignalBars4</span><span class="sxs-lookup"><span data-stu-id="44fc0-696">SignalBars4</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E870.png" width="32" height="32" alt="SignalBars5" /></td>
  <td><span data-ttu-id="44fc0-697">E870</span><span class="sxs-lookup"><span data-stu-id="44fc0-697">E870</span></span></td>
  <td><span data-ttu-id="44fc0-698">SignalBars5</span><span class="sxs-lookup"><span data-stu-id="44fc0-698">SignalBars5</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E871.png" width="32" height="32" alt="SignalNotConnected" /></td>
  <td><span data-ttu-id="44fc0-699">E871</span><span class="sxs-lookup"><span data-stu-id="44fc0-699">E871</span></span></td>
  <td><span data-ttu-id="44fc0-700">SignalNotConnected</span><span class="sxs-lookup"><span data-stu-id="44fc0-700">SignalNotConnected</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E872.png" width="32" height="32" alt="Wifi1" /></td>
  <td><span data-ttu-id="44fc0-701">E872</span><span class="sxs-lookup"><span data-stu-id="44fc0-701">E872</span></span></td>
  <td><span data-ttu-id="44fc0-702">Wifi1</span><span class="sxs-lookup"><span data-stu-id="44fc0-702">Wifi1</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E873.png" width="32" height="32" alt="Wifi2" /></td>
  <td><span data-ttu-id="44fc0-703">E873</span><span class="sxs-lookup"><span data-stu-id="44fc0-703">E873</span></span></td>
  <td><span data-ttu-id="44fc0-704">Wifi2</span><span class="sxs-lookup"><span data-stu-id="44fc0-704">Wifi2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E874.png" width="32" height="32" alt="Wifi3" /></td>
  <td><span data-ttu-id="44fc0-705">E874</span><span class="sxs-lookup"><span data-stu-id="44fc0-705">E874</span></span></td>
  <td><span data-ttu-id="44fc0-706">Wifi3</span><span class="sxs-lookup"><span data-stu-id="44fc0-706">Wifi3</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E875.png" width="32" height="32" alt="MobSIMLock" /></td>
  <td><span data-ttu-id="44fc0-707">E875</span><span class="sxs-lookup"><span data-stu-id="44fc0-707">E875</span></span></td>
  <td><span data-ttu-id="44fc0-708">MobSIMLock</span><span class="sxs-lookup"><span data-stu-id="44fc0-708">MobSIMLock</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E876.png" width="32" height="32" alt="MobSIMMissing" /></td>
  <td><span data-ttu-id="44fc0-709">E876</span><span class="sxs-lookup"><span data-stu-id="44fc0-709">E876</span></span></td>
  <td><span data-ttu-id="44fc0-710">MobSIMMissing</span><span class="sxs-lookup"><span data-stu-id="44fc0-710">MobSIMMissing</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E877.png" width="32" height="32" alt="Vibrate" /></td>
  <td><span data-ttu-id="44fc0-711">E877</span><span class="sxs-lookup"><span data-stu-id="44fc0-711">E877</span></span></td>
  <td><span data-ttu-id="44fc0-712">Vibrate</span><span class="sxs-lookup"><span data-stu-id="44fc0-712">Vibrate</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E878.png" width="32" height="32" alt="RoamingInternational" /></td>
  <td><span data-ttu-id="44fc0-713">E878</span><span class="sxs-lookup"><span data-stu-id="44fc0-713">E878</span></span></td>
  <td><span data-ttu-id="44fc0-714">RoamingInternational</span><span class="sxs-lookup"><span data-stu-id="44fc0-714">RoamingInternational</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E879.png" width="32" height="32" alt="RoamingDomestic" /></td>
  <td><span data-ttu-id="44fc0-715">E879</span><span class="sxs-lookup"><span data-stu-id="44fc0-715">E879</span></span></td>
  <td><span data-ttu-id="44fc0-716">RoamingDomestic</span><span class="sxs-lookup"><span data-stu-id="44fc0-716">RoamingDomestic</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E87A.png" width="32" height="32" alt="CallForwardInternational" /></td>
  <td><span data-ttu-id="44fc0-717">E87A</span><span class="sxs-lookup"><span data-stu-id="44fc0-717">E87A</span></span></td>
  <td><span data-ttu-id="44fc0-718">CallForwardInternational</span><span class="sxs-lookup"><span data-stu-id="44fc0-718">CallForwardInternational</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E87B.png" width="32" height="32" alt="CallForwardRoaming" /></td>
  <td><span data-ttu-id="44fc0-719">E87B</span><span class="sxs-lookup"><span data-stu-id="44fc0-719">E87B</span></span></td>
  <td><span data-ttu-id="44fc0-720">CallForwardRoaming</span><span class="sxs-lookup"><span data-stu-id="44fc0-720">CallForwardRoaming</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E87C.png" width="32" height="32" alt="JpnRomanji" /></td>
  <td><span data-ttu-id="44fc0-721">E87C</span><span class="sxs-lookup"><span data-stu-id="44fc0-721">E87C</span></span></td>
  <td><span data-ttu-id="44fc0-722">JpnRomanji</span><span class="sxs-lookup"><span data-stu-id="44fc0-722">JpnRomanji</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E87D.png" width="32" height="32" alt="JpnRomanjiLock" /></td>
  <td><span data-ttu-id="44fc0-723">E87D</span><span class="sxs-lookup"><span data-stu-id="44fc0-723">E87D</span></span></td>
  <td><span data-ttu-id="44fc0-724">JpnRomanjiLock</span><span class="sxs-lookup"><span data-stu-id="44fc0-724">JpnRomanjiLock</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E87E.png" width="32" height="32" alt="JpnRomanjiShift" /></td>
  <td><span data-ttu-id="44fc0-725">E87E</span><span class="sxs-lookup"><span data-stu-id="44fc0-725">E87E</span></span></td>
  <td><span data-ttu-id="44fc0-726">JpnRomanjiShift</span><span class="sxs-lookup"><span data-stu-id="44fc0-726">JpnRomanjiShift</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E87F.png" width="32" height="32" alt="JpnRomanjiShiftLock" /></td>
  <td><span data-ttu-id="44fc0-727">E87F</span><span class="sxs-lookup"><span data-stu-id="44fc0-727">E87F</span></span></td>
  <td><span data-ttu-id="44fc0-728">JpnRomanjiShiftLock</span><span class="sxs-lookup"><span data-stu-id="44fc0-728">JpnRomanjiShiftLock</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E880.png" width="32" height="32" alt="StatusDataTransfer" /></td>
  <td><span data-ttu-id="44fc0-729">E880</span><span class="sxs-lookup"><span data-stu-id="44fc0-729">E880</span></span></td>
  <td><span data-ttu-id="44fc0-730">StatusDataTransfer</span><span class="sxs-lookup"><span data-stu-id="44fc0-730">StatusDataTransfer</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E881.png" width="32" height="32" alt="StatusDataTransferVPN" /></td>
  <td><span data-ttu-id="44fc0-731">E881</span><span class="sxs-lookup"><span data-stu-id="44fc0-731">E881</span></span></td>
  <td><span data-ttu-id="44fc0-732">StatusDataTransferVPN</span><span class="sxs-lookup"><span data-stu-id="44fc0-732">StatusDataTransferVPN</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E882.png" width="32" height="32" alt="StatusDualSIM2" /></td>
  <td><span data-ttu-id="44fc0-733">E882</span><span class="sxs-lookup"><span data-stu-id="44fc0-733">E882</span></span></td>
  <td><span data-ttu-id="44fc0-734">StatusDualSIM2</span><span class="sxs-lookup"><span data-stu-id="44fc0-734">StatusDualSIM2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E883.png" width="32" height="32" alt="StatusDualSIM2VPN" /></td>
  <td><span data-ttu-id="44fc0-735">E883</span><span class="sxs-lookup"><span data-stu-id="44fc0-735">E883</span></span></td>
  <td><span data-ttu-id="44fc0-736">StatusDualSIM2VPN</span><span class="sxs-lookup"><span data-stu-id="44fc0-736">StatusDualSIM2VPN</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E884.png" width="32" height="32" alt="StatusDualSIM1" /></td>
  <td><span data-ttu-id="44fc0-737">E884</span><span class="sxs-lookup"><span data-stu-id="44fc0-737">E884</span></span></td>
  <td><span data-ttu-id="44fc0-738">StatusDualSIM1</span><span class="sxs-lookup"><span data-stu-id="44fc0-738">StatusDualSIM1</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E885.png" width="32" height="32" alt="StatusDualSIM1VPN" /></td>
  <td><span data-ttu-id="44fc0-739">E885</span><span class="sxs-lookup"><span data-stu-id="44fc0-739">E885</span></span></td>
  <td><span data-ttu-id="44fc0-740">StatusDualSIM1VPN</span><span class="sxs-lookup"><span data-stu-id="44fc0-740">StatusDualSIM1VPN</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E886.png" width="32" height="32" alt="StatusSGLTE" /></td>
  <td><span data-ttu-id="44fc0-741">E886</span><span class="sxs-lookup"><span data-stu-id="44fc0-741">E886</span></span></td>
  <td><span data-ttu-id="44fc0-742">StatusSGLTE</span><span class="sxs-lookup"><span data-stu-id="44fc0-742">StatusSGLTE</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E887.png" width="32" height="32" alt="StatusSGLTECell" /></td>
  <td><span data-ttu-id="44fc0-743">E887</span><span class="sxs-lookup"><span data-stu-id="44fc0-743">E887</span></span></td>
  <td><span data-ttu-id="44fc0-744">StatusSGLTECell</span><span class="sxs-lookup"><span data-stu-id="44fc0-744">StatusSGLTECell</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E888.png" width="32" height="32" alt="StatusSGLTEDataVPN" /></td>
  <td><span data-ttu-id="44fc0-745">E888</span><span class="sxs-lookup"><span data-stu-id="44fc0-745">E888</span></span></td>
  <td><span data-ttu-id="44fc0-746">StatusSGLTEDataVPN</span><span class="sxs-lookup"><span data-stu-id="44fc0-746">StatusSGLTEDataVPN</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E889.png" width="32" height="32" alt="StatusVPN" /></td>
  <td><span data-ttu-id="44fc0-747">E889</span><span class="sxs-lookup"><span data-stu-id="44fc0-747">E889</span></span></td>
  <td><span data-ttu-id="44fc0-748">StatusVPN</span><span class="sxs-lookup"><span data-stu-id="44fc0-748">StatusVPN</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E88A.png" width="32" height="32" alt="WifiHotspot" /></td>
  <td><span data-ttu-id="44fc0-749">E88A</span><span class="sxs-lookup"><span data-stu-id="44fc0-749">E88A</span></span></td>
  <td><span data-ttu-id="44fc0-750">WifiHotspot</span><span class="sxs-lookup"><span data-stu-id="44fc0-750">WifiHotspot</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E88B.png" width="32" height="32" alt="LanguageKor" /></td>
  <td><span data-ttu-id="44fc0-751">E88B</span><span class="sxs-lookup"><span data-stu-id="44fc0-751">E88B</span></span></td>
  <td><span data-ttu-id="44fc0-752">LanguageKor</span><span class="sxs-lookup"><span data-stu-id="44fc0-752">LanguageKor</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E88C.png" width="32" height="32" alt="LanguageCht" /></td>
  <td><span data-ttu-id="44fc0-753">E88C</span><span class="sxs-lookup"><span data-stu-id="44fc0-753">E88C</span></span></td>
  <td><span data-ttu-id="44fc0-754">LanguageCht</span><span class="sxs-lookup"><span data-stu-id="44fc0-754">LanguageCht</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E88D.png" width="32" height="32" alt="LanguageChs" /></td>
  <td><span data-ttu-id="44fc0-755">E88D</span><span class="sxs-lookup"><span data-stu-id="44fc0-755">E88D</span></span></td>
  <td><span data-ttu-id="44fc0-756">LanguageChs</span><span class="sxs-lookup"><span data-stu-id="44fc0-756">LanguageChs</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E88E.png" width="32" height="32" alt="USB" /></td>
  <td><span data-ttu-id="44fc0-757">E88E</span><span class="sxs-lookup"><span data-stu-id="44fc0-757">E88E</span></span></td>
  <td><span data-ttu-id="44fc0-758">USB</span><span class="sxs-lookup"><span data-stu-id="44fc0-758">USB</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E88F.png" width="32" height="32" alt="InkingToolFill" /></td>
  <td><span data-ttu-id="44fc0-759">E88F</span><span class="sxs-lookup"><span data-stu-id="44fc0-759">E88F</span></span></td>
  <td><span data-ttu-id="44fc0-760">InkingToolFill</span><span class="sxs-lookup"><span data-stu-id="44fc0-760">InkingToolFill</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E890.png" width="32" height="32" alt="View" /></td>
  <td><span data-ttu-id="44fc0-761">E890</span><span class="sxs-lookup"><span data-stu-id="44fc0-761">E890</span></span></td>
  <td><span data-ttu-id="44fc0-762">Ansicht</span><span class="sxs-lookup"><span data-stu-id="44fc0-762">View</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E891.png" width="32" height="32" alt="HighlightFill" /></td>
  <td><span data-ttu-id="44fc0-763">E891</span><span class="sxs-lookup"><span data-stu-id="44fc0-763">E891</span></span></td>
  <td><span data-ttu-id="44fc0-764">HighlightFill</span><span class="sxs-lookup"><span data-stu-id="44fc0-764">HighlightFill</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E892.png" width="32" height="32" alt="Previous" /></td>
  <td><span data-ttu-id="44fc0-765">E892</span><span class="sxs-lookup"><span data-stu-id="44fc0-765">E892</span></span></td>
  <td><span data-ttu-id="44fc0-766">Vorherige</span><span class="sxs-lookup"><span data-stu-id="44fc0-766">Previous</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E893.png" width="32" height="32" alt="Next" /></td>
  <td><span data-ttu-id="44fc0-767">E893</span><span class="sxs-lookup"><span data-stu-id="44fc0-767">E893</span></span></td>
  <td><span data-ttu-id="44fc0-768">Nächste</span><span class="sxs-lookup"><span data-stu-id="44fc0-768">Next</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E894.png" width="32" height="32" alt="Clear" /></td>
  <td><span data-ttu-id="44fc0-769">E894</span><span class="sxs-lookup"><span data-stu-id="44fc0-769">E894</span></span></td>
  <td><span data-ttu-id="44fc0-770">Clear</span><span class="sxs-lookup"><span data-stu-id="44fc0-770">Clear</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E895.png" width="32" height="32" alt="Sync" /></td>
  <td><span data-ttu-id="44fc0-771">E895</span><span class="sxs-lookup"><span data-stu-id="44fc0-771">E895</span></span></td>
  <td><span data-ttu-id="44fc0-772">Synchronisieren</span><span class="sxs-lookup"><span data-stu-id="44fc0-772">Sync</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E896.png" width="32" height="32" alt="Download" /></td>
  <td><span data-ttu-id="44fc0-773">E896</span><span class="sxs-lookup"><span data-stu-id="44fc0-773">E896</span></span></td>
  <td><span data-ttu-id="44fc0-774">Herunterladen</span><span class="sxs-lookup"><span data-stu-id="44fc0-774">Download</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E897.png" width="32" height="32" alt="Help" /></td>
  <td><span data-ttu-id="44fc0-775">E897</span><span class="sxs-lookup"><span data-stu-id="44fc0-775">E897</span></span></td>
  <td><span data-ttu-id="44fc0-776">Hilfe</span><span class="sxs-lookup"><span data-stu-id="44fc0-776">Help</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E898.png" width="32" height="32" alt="Upload" /></td>
  <td><span data-ttu-id="44fc0-777">E898</span><span class="sxs-lookup"><span data-stu-id="44fc0-777">E898</span></span></td>
  <td><span data-ttu-id="44fc0-778">Upload</span><span class="sxs-lookup"><span data-stu-id="44fc0-778">Upload</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E899.png" width="32" height="32" alt="Emoji" /></td>
  <td><span data-ttu-id="44fc0-779">E899</span><span class="sxs-lookup"><span data-stu-id="44fc0-779">E899</span></span></td>
  <td><span data-ttu-id="44fc0-780">Emoji</span><span class="sxs-lookup"><span data-stu-id="44fc0-780">Emoji</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E89A.png" width="32" height="32" alt="TwoPage" /></td>
  <td><span data-ttu-id="44fc0-781">E89A</span><span class="sxs-lookup"><span data-stu-id="44fc0-781">E89A</span></span></td>
  <td><span data-ttu-id="44fc0-782">TwoPage</span><span class="sxs-lookup"><span data-stu-id="44fc0-782">TwoPage</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E89B.png" width="32" height="32" alt="LeaveChat" /></td>
  <td><span data-ttu-id="44fc0-783">E89B</span><span class="sxs-lookup"><span data-stu-id="44fc0-783">E89B</span></span></td>
  <td><span data-ttu-id="44fc0-784">LeaveChat</span><span class="sxs-lookup"><span data-stu-id="44fc0-784">LeaveChat</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E89C.png" width="32" height="32" alt="MailForward" /></td>
  <td><span data-ttu-id="44fc0-785">E89C</span><span class="sxs-lookup"><span data-stu-id="44fc0-785">E89C</span></span></td>
  <td><span data-ttu-id="44fc0-786">MailForward</span><span class="sxs-lookup"><span data-stu-id="44fc0-786">MailForward</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E89E.png" width="32" height="32" alt="RotateCamera" /></td>
  <td><span data-ttu-id="44fc0-787">E89E</span><span class="sxs-lookup"><span data-stu-id="44fc0-787">E89E</span></span></td>
  <td><span data-ttu-id="44fc0-788">RotateCamera</span><span class="sxs-lookup"><span data-stu-id="44fc0-788">RotateCamera</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E89F.png" width="32" height="32" alt="ClosePane" /></td>
  <td><span data-ttu-id="44fc0-789">E89F</span><span class="sxs-lookup"><span data-stu-id="44fc0-789">E89F</span></span></td>
  <td><span data-ttu-id="44fc0-790">ClosePane</span><span class="sxs-lookup"><span data-stu-id="44fc0-790">ClosePane</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8A0.png" width="32" height="32" alt="OpenPane" /></td>
  <td><span data-ttu-id="44fc0-791">E8A0</span><span class="sxs-lookup"><span data-stu-id="44fc0-791">E8A0</span></span></td>
  <td><span data-ttu-id="44fc0-792">OpenPane</span><span class="sxs-lookup"><span data-stu-id="44fc0-792">OpenPane</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8A1.png" width="32" height="32" alt="PreviewLink" /></td>
  <td><span data-ttu-id="44fc0-793">E8A1</span><span class="sxs-lookup"><span data-stu-id="44fc0-793">E8A1</span></span></td>
  <td><span data-ttu-id="44fc0-794">PreviewLink</span><span class="sxs-lookup"><span data-stu-id="44fc0-794">PreviewLink</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8A2.png" width="32" height="32" alt="AttachCamera" /></td>
  <td><span data-ttu-id="44fc0-795">E8A2</span><span class="sxs-lookup"><span data-stu-id="44fc0-795">E8A2</span></span></td>
  <td><span data-ttu-id="44fc0-796">AttachCamera</span><span class="sxs-lookup"><span data-stu-id="44fc0-796">AttachCamera</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8A3.png" width="32" height="32" alt="ZoomIn" /></td>
  <td><span data-ttu-id="44fc0-797">E8A3</span><span class="sxs-lookup"><span data-stu-id="44fc0-797">E8A3</span></span></td>
  <td><span data-ttu-id="44fc0-798">ZoomIn</span><span class="sxs-lookup"><span data-stu-id="44fc0-798">ZoomIn</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8A4.png" width="32" height="32" alt="Bookmarks" /></td>
  <td><span data-ttu-id="44fc0-799">E8A4</span><span class="sxs-lookup"><span data-stu-id="44fc0-799">E8A4</span></span></td>
  <td><span data-ttu-id="44fc0-800">Bookmarks</span><span class="sxs-lookup"><span data-stu-id="44fc0-800">Bookmarks</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8A5.png" width="32" height="32" alt="Document" /></td>
  <td><span data-ttu-id="44fc0-801">E8A5</span><span class="sxs-lookup"><span data-stu-id="44fc0-801">E8A5</span></span></td>
  <td><span data-ttu-id="44fc0-802">Dokument</span><span class="sxs-lookup"><span data-stu-id="44fc0-802">Document</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8A6.png" width="32" height="32" alt="ProtectedDocument" /></td>
  <td><span data-ttu-id="44fc0-803">E8A6</span><span class="sxs-lookup"><span data-stu-id="44fc0-803">E8A6</span></span></td>
  <td><span data-ttu-id="44fc0-804">ProtectedDocument</span><span class="sxs-lookup"><span data-stu-id="44fc0-804">ProtectedDocument</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8A7.png" width="32" height="32" alt="OpenInNewWindow" /></td>
  <td><span data-ttu-id="44fc0-805">E8A7</span><span class="sxs-lookup"><span data-stu-id="44fc0-805">E8A7</span></span></td>
  <td><span data-ttu-id="44fc0-806">OpenInNewWindow</span><span class="sxs-lookup"><span data-stu-id="44fc0-806">OpenInNewWindow</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8A8.png" width="32" height="32" alt="MailFill" /></td>
  <td><span data-ttu-id="44fc0-807">E8A8</span><span class="sxs-lookup"><span data-stu-id="44fc0-807">E8A8</span></span></td>
  <td><span data-ttu-id="44fc0-808">MailFill</span><span class="sxs-lookup"><span data-stu-id="44fc0-808">MailFill</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8A9.png" width="32" height="32" alt="ViewAll" /></td>
  <td><span data-ttu-id="44fc0-809">E8A9</span><span class="sxs-lookup"><span data-stu-id="44fc0-809">E8A9</span></span></td>
  <td><span data-ttu-id="44fc0-810">ViewAll</span><span class="sxs-lookup"><span data-stu-id="44fc0-810">ViewAll</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8AA.png" width="32" height="32" alt="VideoChat" /></td>
  <td><span data-ttu-id="44fc0-811">E8AA</span><span class="sxs-lookup"><span data-stu-id="44fc0-811">E8AA</span></span></td>
  <td><span data-ttu-id="44fc0-812">VideoChat</span><span class="sxs-lookup"><span data-stu-id="44fc0-812">VideoChat</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8AB.png" width="32" height="32" alt="Switch" /></td>
  <td><span data-ttu-id="44fc0-813">E8AB</span><span class="sxs-lookup"><span data-stu-id="44fc0-813">E8AB</span></span></td>
  <td><span data-ttu-id="44fc0-814">Wechsel</span><span class="sxs-lookup"><span data-stu-id="44fc0-814">Switch</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8AC.png" width="32" height="32" alt="Rename" /></td>
  <td><span data-ttu-id="44fc0-815">E8AC</span><span class="sxs-lookup"><span data-stu-id="44fc0-815">E8AC</span></span></td>
  <td><span data-ttu-id="44fc0-816">Rename</span><span class="sxs-lookup"><span data-stu-id="44fc0-816">Rename</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8AD.png" width="32" height="32" alt="Go" /></td>
  <td><span data-ttu-id="44fc0-817">E8AD</span><span class="sxs-lookup"><span data-stu-id="44fc0-817">E8AD</span></span></td>
  <td><span data-ttu-id="44fc0-818">Go</span><span class="sxs-lookup"><span data-stu-id="44fc0-818">Go</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8AE.png" width="32" height="32" alt="SurfaceHub" /></td>
  <td><span data-ttu-id="44fc0-819">E8AE</span><span class="sxs-lookup"><span data-stu-id="44fc0-819">E8AE</span></span></td>
  <td><span data-ttu-id="44fc0-820">SurfaceHub</span><span class="sxs-lookup"><span data-stu-id="44fc0-820">SurfaceHub</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8AF.png" width="32" height="32" alt="Remote" /></td>
  <td><span data-ttu-id="44fc0-821">E8AF</span><span class="sxs-lookup"><span data-stu-id="44fc0-821">E8AF</span></span></td>
  <td><span data-ttu-id="44fc0-822">Remote</span><span class="sxs-lookup"><span data-stu-id="44fc0-822">Remote</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8B0.png" width="32" height="32" alt="Click" /></td>
  <td><span data-ttu-id="44fc0-823">E8B0</span><span class="sxs-lookup"><span data-stu-id="44fc0-823">E8B0</span></span></td>
  <td><span data-ttu-id="44fc0-824">Klick</span><span class="sxs-lookup"><span data-stu-id="44fc0-824">Click</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8B1.png" width="32" height="32" alt="Shuffle" /></td>
  <td><span data-ttu-id="44fc0-825">E8B1</span><span class="sxs-lookup"><span data-stu-id="44fc0-825">E8B1</span></span></td>
  <td><span data-ttu-id="44fc0-826">Shuffle</span><span class="sxs-lookup"><span data-stu-id="44fc0-826">Shuffle</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8B2.png" width="32" height="32" alt="Movies" /></td>
  <td><span data-ttu-id="44fc0-827">E8B2</span><span class="sxs-lookup"><span data-stu-id="44fc0-827">E8B2</span></span></td>
  <td><span data-ttu-id="44fc0-828">Filme</span><span class="sxs-lookup"><span data-stu-id="44fc0-828">Movies</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8B3.png" width="32" height="32" alt="SelectAll" /></td>
  <td><span data-ttu-id="44fc0-829">E8B3</span><span class="sxs-lookup"><span data-stu-id="44fc0-829">E8B3</span></span></td>
  <td><span data-ttu-id="44fc0-830">SelectAll</span><span class="sxs-lookup"><span data-stu-id="44fc0-830">SelectAll</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8B4.png" width="32" height="32" alt="Orientation" /></td>
  <td><span data-ttu-id="44fc0-831">E8B4</span><span class="sxs-lookup"><span data-stu-id="44fc0-831">E8B4</span></span></td>
  <td><span data-ttu-id="44fc0-832">Orientation</span><span class="sxs-lookup"><span data-stu-id="44fc0-832">Orientation</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8B5.png" width="32" height="32" alt="Import" /></td>
  <td><span data-ttu-id="44fc0-833">E8B5</span><span class="sxs-lookup"><span data-stu-id="44fc0-833">E8B5</span></span></td>
  <td><span data-ttu-id="44fc0-834">Import</span><span class="sxs-lookup"><span data-stu-id="44fc0-834">Import</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8B6.png" width="32" height="32" alt="ImportAll" /></td>
  <td><span data-ttu-id="44fc0-835">E8B6</span><span class="sxs-lookup"><span data-stu-id="44fc0-835">E8B6</span></span></td>
  <td><span data-ttu-id="44fc0-836">ImportAll</span><span class="sxs-lookup"><span data-stu-id="44fc0-836">ImportAll</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8B7.png" width="32" height="32" alt="Folder" /></td>
  <td><span data-ttu-id="44fc0-837">E8B7</span><span class="sxs-lookup"><span data-stu-id="44fc0-837">E8B7</span></span></td>
  <td><span data-ttu-id="44fc0-838">Ordner</span><span class="sxs-lookup"><span data-stu-id="44fc0-838">Folder</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8B8.png" width="32" height="32" alt="Webcam" /></td>
  <td><span data-ttu-id="44fc0-839">E8B8</span><span class="sxs-lookup"><span data-stu-id="44fc0-839">E8B8</span></span></td>
  <td><span data-ttu-id="44fc0-840">Webcam</span><span class="sxs-lookup"><span data-stu-id="44fc0-840">Webcam</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8B9.png" width="32" height="32" alt="Picture" /></td>
  <td><span data-ttu-id="44fc0-841">E8B9</span><span class="sxs-lookup"><span data-stu-id="44fc0-841">E8B9</span></span></td>
  <td><span data-ttu-id="44fc0-842">Bild</span><span class="sxs-lookup"><span data-stu-id="44fc0-842">Picture</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8BA.png" width="32" height="32" alt="Caption" /></td>
  <td><span data-ttu-id="44fc0-843">E8BA</span><span class="sxs-lookup"><span data-stu-id="44fc0-843">E8BA</span></span></td>
  <td><span data-ttu-id="44fc0-844">Untertitel für Hörgeschädigte</span><span class="sxs-lookup"><span data-stu-id="44fc0-844">Caption</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8BB.png" width="32" height="32" alt="ChromeClose" /></td>
  <td><span data-ttu-id="44fc0-845">E8BB</span><span class="sxs-lookup"><span data-stu-id="44fc0-845">E8BB</span></span></td>
  <td><span data-ttu-id="44fc0-846">ChromeClose</span><span class="sxs-lookup"><span data-stu-id="44fc0-846">ChromeClose</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8BC.png" width="32" height="32" alt="ShowResults" /></td>
  <td><span data-ttu-id="44fc0-847">E8BC</span><span class="sxs-lookup"><span data-stu-id="44fc0-847">E8BC</span></span></td>
  <td><span data-ttu-id="44fc0-848">ShowResults</span><span class="sxs-lookup"><span data-stu-id="44fc0-848">ShowResults</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8BD.png" width="32" height="32" alt="Message" /></td>
  <td><span data-ttu-id="44fc0-849">E8BD</span><span class="sxs-lookup"><span data-stu-id="44fc0-849">E8BD</span></span></td>
  <td><span data-ttu-id="44fc0-850">Nachricht</span><span class="sxs-lookup"><span data-stu-id="44fc0-850">Message</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8BE.png" width="32" height="32" alt="Leaf" /></td>
  <td><span data-ttu-id="44fc0-851">E8BE</span><span class="sxs-lookup"><span data-stu-id="44fc0-851">E8BE</span></span></td>
  <td><span data-ttu-id="44fc0-852">Leaf</span><span class="sxs-lookup"><span data-stu-id="44fc0-852">Leaf</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8BF.png" width="32" height="32" alt="CalendarDay" /></td>
  <td><span data-ttu-id="44fc0-853">E8BF</span><span class="sxs-lookup"><span data-stu-id="44fc0-853">E8BF</span></span></td>
  <td><span data-ttu-id="44fc0-854">CalendarDay</span><span class="sxs-lookup"><span data-stu-id="44fc0-854">CalendarDay</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8C0.png" width="32" height="32" alt="CalendarWeek" /></td>
  <td><span data-ttu-id="44fc0-855">E8C0</span><span class="sxs-lookup"><span data-stu-id="44fc0-855">E8C0</span></span></td>
  <td><span data-ttu-id="44fc0-856">CalendarWeek</span><span class="sxs-lookup"><span data-stu-id="44fc0-856">CalendarWeek</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8C1.png" width="32" height="32" alt="Characters" /></td>
  <td><span data-ttu-id="44fc0-857">E8C1</span><span class="sxs-lookup"><span data-stu-id="44fc0-857">E8C1</span></span></td>
  <td><span data-ttu-id="44fc0-858">Characters</span><span class="sxs-lookup"><span data-stu-id="44fc0-858">Characters</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8C2.png" width="32" height="32" alt="MailReplyAll" /></td>
  <td><span data-ttu-id="44fc0-859">E8C2</span><span class="sxs-lookup"><span data-stu-id="44fc0-859">E8C2</span></span></td>
  <td><span data-ttu-id="44fc0-860">MailReplyAll</span><span class="sxs-lookup"><span data-stu-id="44fc0-860">MailReplyAll</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8C3.png" width="32" height="32" alt="Read" /></td>
  <td><span data-ttu-id="44fc0-861">E8C3</span><span class="sxs-lookup"><span data-stu-id="44fc0-861">E8C3</span></span></td>
  <td><span data-ttu-id="44fc0-862">Lesen</span><span class="sxs-lookup"><span data-stu-id="44fc0-862">Read</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8C4.png" width="32" height="32" alt="ShowBcc" /></td>
  <td><span data-ttu-id="44fc0-863">E8C4</span><span class="sxs-lookup"><span data-stu-id="44fc0-863">E8C4</span></span></td>
  <td><span data-ttu-id="44fc0-864">ShowBcc</span><span class="sxs-lookup"><span data-stu-id="44fc0-864">ShowBcc</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8C5.png" width="32" height="32" alt="HideBcc" /></td>
  <td><span data-ttu-id="44fc0-865">E8C5</span><span class="sxs-lookup"><span data-stu-id="44fc0-865">E8C5</span></span></td>
  <td><span data-ttu-id="44fc0-866">HideBcc</span><span class="sxs-lookup"><span data-stu-id="44fc0-866">HideBcc</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8C6.png" width="32" height="32" alt="Cut" /></td>
  <td><span data-ttu-id="44fc0-867">E8C6</span><span class="sxs-lookup"><span data-stu-id="44fc0-867">E8C6</span></span></td>
  <td><span data-ttu-id="44fc0-868">Ausschneiden</span><span class="sxs-lookup"><span data-stu-id="44fc0-868">Cut</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8C7.png" width="32" height="32" alt="PaymentCard" /></td>
  <td><span data-ttu-id="44fc0-869">E8C7</span><span class="sxs-lookup"><span data-stu-id="44fc0-869">E8C7</span></span></td>
  <td><span data-ttu-id="44fc0-870">PaymentCard</span><span class="sxs-lookup"><span data-stu-id="44fc0-870">PaymentCard</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8C8.png" width="32" height="32" alt="Copy" /></td>
  <td><span data-ttu-id="44fc0-871">E8C8</span><span class="sxs-lookup"><span data-stu-id="44fc0-871">E8C8</span></span></td>
  <td><span data-ttu-id="44fc0-872">Kopieren</span><span class="sxs-lookup"><span data-stu-id="44fc0-872">Copy</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8C9.png" width="32" height="32" alt="Important" /></td>
  <td><span data-ttu-id="44fc0-873">E8C9</span><span class="sxs-lookup"><span data-stu-id="44fc0-873">E8C9</span></span></td>
  <td><span data-ttu-id="44fc0-874">Wichtig</span><span class="sxs-lookup"><span data-stu-id="44fc0-874">Important</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8CA.png" width="32" height="32" alt="MailReply" /></td>
  <td><span data-ttu-id="44fc0-875">E8CA</span><span class="sxs-lookup"><span data-stu-id="44fc0-875">E8CA</span></span></td>
  <td><span data-ttu-id="44fc0-876">MailReply</span><span class="sxs-lookup"><span data-stu-id="44fc0-876">MailReply</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8CB.png" width="32" height="32" alt="Sort" /></td>
  <td><span data-ttu-id="44fc0-877">E8CB</span><span class="sxs-lookup"><span data-stu-id="44fc0-877">E8CB</span></span></td>
  <td><span data-ttu-id="44fc0-878">Sort</span><span class="sxs-lookup"><span data-stu-id="44fc0-878">Sort</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8CC.png" width="32" height="32" alt="MobileTablet" /></td>
  <td><span data-ttu-id="44fc0-879">E8CC</span><span class="sxs-lookup"><span data-stu-id="44fc0-879">E8CC</span></span></td>
  <td><span data-ttu-id="44fc0-880">MobileTablet</span><span class="sxs-lookup"><span data-stu-id="44fc0-880">MobileTablet</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8CD.png" width="32" height="32" alt="DisconnectDrive" /></td>
  <td><span data-ttu-id="44fc0-881">E8CD</span><span class="sxs-lookup"><span data-stu-id="44fc0-881">E8CD</span></span></td>
  <td><span data-ttu-id="44fc0-882">DisconnectDrive</span><span class="sxs-lookup"><span data-stu-id="44fc0-882">DisconnectDrive</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8CE.png" width="32" height="32" alt="MapDrive" /></td>
  <td><span data-ttu-id="44fc0-883">E8CE</span><span class="sxs-lookup"><span data-stu-id="44fc0-883">E8CE</span></span></td>
  <td><span data-ttu-id="44fc0-884">MapDrive</span><span class="sxs-lookup"><span data-stu-id="44fc0-884">MapDrive</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8CF.png" width="32" height="32" alt="ContactPresence" /></td>
  <td><span data-ttu-id="44fc0-885">E8CF</span><span class="sxs-lookup"><span data-stu-id="44fc0-885">E8CF</span></span></td>
  <td><span data-ttu-id="44fc0-886">ContactPresence</span><span class="sxs-lookup"><span data-stu-id="44fc0-886">ContactPresence</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8D0.png" width="32" height="32" alt="Priority" /></td>
  <td><span data-ttu-id="44fc0-887">E8D0</span><span class="sxs-lookup"><span data-stu-id="44fc0-887">E8D0</span></span></td>
  <td><span data-ttu-id="44fc0-888">Priorität</span><span class="sxs-lookup"><span data-stu-id="44fc0-888">Priority</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8D1.png" width="32" height="32" alt="GotoToday" /></td>
  <td><span data-ttu-id="44fc0-889">E8D1</span><span class="sxs-lookup"><span data-stu-id="44fc0-889">E8D1</span></span></td>
  <td><span data-ttu-id="44fc0-890">GoToToday</span><span class="sxs-lookup"><span data-stu-id="44fc0-890">GotoToday</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8D2.png" width="32" height="32" alt="Font" /></td>
  <td><span data-ttu-id="44fc0-891">E8D2</span><span class="sxs-lookup"><span data-stu-id="44fc0-891">E8D2</span></span></td>
  <td><span data-ttu-id="44fc0-892">Font</span><span class="sxs-lookup"><span data-stu-id="44fc0-892">Font</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8D3.png" width="32" height="32" alt="FontColor" /></td>
  <td><span data-ttu-id="44fc0-893">E8D3</span><span class="sxs-lookup"><span data-stu-id="44fc0-893">E8D3</span></span></td>
  <td><span data-ttu-id="44fc0-894">FontColor</span><span class="sxs-lookup"><span data-stu-id="44fc0-894">FontColor</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8D4.png" width="32" height="32" alt="Contact2" /></td>
  <td><span data-ttu-id="44fc0-895">E8D4</span><span class="sxs-lookup"><span data-stu-id="44fc0-895">E8D4</span></span></td>
  <td><span data-ttu-id="44fc0-896">Contact2</span><span class="sxs-lookup"><span data-stu-id="44fc0-896">Contact2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8D5.png" width="32" height="32" alt="FolderFill" /></td>
  <td><span data-ttu-id="44fc0-897">E8D5</span><span class="sxs-lookup"><span data-stu-id="44fc0-897">E8D5</span></span></td>
  <td><span data-ttu-id="44fc0-898">FolderFill</span><span class="sxs-lookup"><span data-stu-id="44fc0-898">FolderFill</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8D6.png" width="32" height="32" alt="Audio" /></td>
  <td><span data-ttu-id="44fc0-899">E8D6</span><span class="sxs-lookup"><span data-stu-id="44fc0-899">E8D6</span></span></td>
  <td><span data-ttu-id="44fc0-900">Audio</span><span class="sxs-lookup"><span data-stu-id="44fc0-900">Audio</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8D7.png" width="32" height="32" alt="Permissions" /></td>
  <td><span data-ttu-id="44fc0-901">E8D7</span><span class="sxs-lookup"><span data-stu-id="44fc0-901">E8D7</span></span></td>
  <td><span data-ttu-id="44fc0-902">Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="44fc0-902">Permissions</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8D8.png" width="32" height="32" alt="DisableUpdates" /></td>
  <td><span data-ttu-id="44fc0-903">E8D8</span><span class="sxs-lookup"><span data-stu-id="44fc0-903">E8D8</span></span></td>
  <td><span data-ttu-id="44fc0-904">DisableUpdates</span><span class="sxs-lookup"><span data-stu-id="44fc0-904">DisableUpdates</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8D9.png" width="32" height="32" alt="Unfavorite" /></td>
  <td><span data-ttu-id="44fc0-905">E8D9</span><span class="sxs-lookup"><span data-stu-id="44fc0-905">E8D9</span></span></td>
  <td><span data-ttu-id="44fc0-906">Unfavorite</span><span class="sxs-lookup"><span data-stu-id="44fc0-906">Unfavorite</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8DA.png" width="32" height="32" alt="OpenLocal" /></td>
  <td><span data-ttu-id="44fc0-907">E8DA</span><span class="sxs-lookup"><span data-stu-id="44fc0-907">E8DA</span></span></td>
  <td><span data-ttu-id="44fc0-908">OpenLocal</span><span class="sxs-lookup"><span data-stu-id="44fc0-908">OpenLocal</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8DB.png" width="32" height="32" alt="Italic" /></td>
  <td><span data-ttu-id="44fc0-909">E8DB</span><span class="sxs-lookup"><span data-stu-id="44fc0-909">E8DB</span></span></td>
  <td><span data-ttu-id="44fc0-910">Kursiv</span><span class="sxs-lookup"><span data-stu-id="44fc0-910">Italic</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8DC.png" width="32" height="32" alt="Underline" /></td>
  <td><span data-ttu-id="44fc0-911">E8DC</span><span class="sxs-lookup"><span data-stu-id="44fc0-911">E8DC</span></span></td>
  <td><span data-ttu-id="44fc0-912">Unterstreichen</span><span class="sxs-lookup"><span data-stu-id="44fc0-912">Underline</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8DD.png" width="32" height="32" alt="Bold" /></td>
  <td><span data-ttu-id="44fc0-913">E8DD</span><span class="sxs-lookup"><span data-stu-id="44fc0-913">E8DD</span></span></td>
  <td><span data-ttu-id="44fc0-914">Fett</span><span class="sxs-lookup"><span data-stu-id="44fc0-914">Bold</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8DE.png" width="32" height="32" alt="MoveToFolder" /></td>
  <td><span data-ttu-id="44fc0-915">E8DE</span><span class="sxs-lookup"><span data-stu-id="44fc0-915">E8DE</span></span></td>
  <td><span data-ttu-id="44fc0-916">MoveToFolder</span><span class="sxs-lookup"><span data-stu-id="44fc0-916">MoveToFolder</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8DF.png" width="32" height="32" alt="LikeDislike" /></td>
  <td><span data-ttu-id="44fc0-917">E8DF</span><span class="sxs-lookup"><span data-stu-id="44fc0-917">E8DF</span></span></td>
  <td><span data-ttu-id="44fc0-918">LikeDislike</span><span class="sxs-lookup"><span data-stu-id="44fc0-918">LikeDislike</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8E0.png" width="32" height="32" alt="Dislike" /></td>
  <td><span data-ttu-id="44fc0-919">E8E0</span><span class="sxs-lookup"><span data-stu-id="44fc0-919">E8E0</span></span></td>
  <td><span data-ttu-id="44fc0-920">Dislike</span><span class="sxs-lookup"><span data-stu-id="44fc0-920">Dislike</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8E1.png" width="32" height="32" alt="Like" /></td>
  <td><span data-ttu-id="44fc0-921">E8E1</span><span class="sxs-lookup"><span data-stu-id="44fc0-921">E8E1</span></span></td>
  <td><span data-ttu-id="44fc0-922">Like</span><span class="sxs-lookup"><span data-stu-id="44fc0-922">Like</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8E2.png" width="32" height="32" alt="AlignRight" /></td>
  <td><span data-ttu-id="44fc0-923">E8E2</span><span class="sxs-lookup"><span data-stu-id="44fc0-923">E8E2</span></span></td>
  <td><span data-ttu-id="44fc0-924">AlignRight</span><span class="sxs-lookup"><span data-stu-id="44fc0-924">AlignRight</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8E3.png" width="32" height="32" alt="AlignCenter" /></td>
  <td><span data-ttu-id="44fc0-925">E8E3</span><span class="sxs-lookup"><span data-stu-id="44fc0-925">E8E3</span></span></td>
  <td><span data-ttu-id="44fc0-926">AlignCenter</span><span class="sxs-lookup"><span data-stu-id="44fc0-926">AlignCenter</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8E4.png" width="32" height="32" alt="AlignLeft" /></td>
  <td><span data-ttu-id="44fc0-927">E8E4</span><span class="sxs-lookup"><span data-stu-id="44fc0-927">E8E4</span></span></td>
  <td><span data-ttu-id="44fc0-928">AlignLeft</span><span class="sxs-lookup"><span data-stu-id="44fc0-928">AlignLeft</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8E5.png" width="32" height="32" alt="OpenFile" /></td>
  <td><span data-ttu-id="44fc0-929">E8E5</span><span class="sxs-lookup"><span data-stu-id="44fc0-929">E8E5</span></span></td>
  <td><span data-ttu-id="44fc0-930">OpenFile</span><span class="sxs-lookup"><span data-stu-id="44fc0-930">OpenFile</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8E6.png" width="32" height="32" alt="ClearSelection" /></td>
  <td><span data-ttu-id="44fc0-931">E8E6</span><span class="sxs-lookup"><span data-stu-id="44fc0-931">E8E6</span></span></td>
  <td><span data-ttu-id="44fc0-932">ClearSelection</span><span class="sxs-lookup"><span data-stu-id="44fc0-932">ClearSelection</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8E7.png" width="32" height="32" alt="FontDecrease" /></td>
  <td><span data-ttu-id="44fc0-933">E8E7</span><span class="sxs-lookup"><span data-stu-id="44fc0-933">E8E7</span></span></td>
  <td><span data-ttu-id="44fc0-934">FontDecrease</span><span class="sxs-lookup"><span data-stu-id="44fc0-934">FontDecrease</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8E8.png" width="32" height="32" alt="FontIncrease" /></td>
  <td><span data-ttu-id="44fc0-935">E8E8</span><span class="sxs-lookup"><span data-stu-id="44fc0-935">E8E8</span></span></td>
  <td><span data-ttu-id="44fc0-936">FontIncrease</span><span class="sxs-lookup"><span data-stu-id="44fc0-936">FontIncrease</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8E9.png" width="32" height="32" alt="FontSize" /></td>
  <td><span data-ttu-id="44fc0-937">E8E9</span><span class="sxs-lookup"><span data-stu-id="44fc0-937">E8E9</span></span></td>
  <td><span data-ttu-id="44fc0-938">FontSize</span><span class="sxs-lookup"><span data-stu-id="44fc0-938">FontSize</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8EA.png" width="32" height="32" alt="CellPhone" /></td>
  <td><span data-ttu-id="44fc0-939">E8EA</span><span class="sxs-lookup"><span data-stu-id="44fc0-939">E8EA</span></span></td>
  <td><span data-ttu-id="44fc0-940">CellPhone</span><span class="sxs-lookup"><span data-stu-id="44fc0-940">CellPhone</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8EB.png" width="32" height="32" alt="Reshare" /></td>
  <td><span data-ttu-id="44fc0-941">E8EB</span><span class="sxs-lookup"><span data-stu-id="44fc0-941">E8EB</span></span></td>
  <td><span data-ttu-id="44fc0-942">Reshare</span><span class="sxs-lookup"><span data-stu-id="44fc0-942">Reshare</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8EC.png" width="32" height="32" alt="Tag" /></td>
  <td><span data-ttu-id="44fc0-943">E8EC</span><span class="sxs-lookup"><span data-stu-id="44fc0-943">E8EC</span></span></td>
  <td><span data-ttu-id="44fc0-944">Tag</span><span class="sxs-lookup"><span data-stu-id="44fc0-944">Tag</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8ED.png" width="32" height="32" alt="RepeatOne" /></td>
  <td><span data-ttu-id="44fc0-945">E8ED</span><span class="sxs-lookup"><span data-stu-id="44fc0-945">E8ED</span></span></td>
  <td><span data-ttu-id="44fc0-946">RepeatOne</span><span class="sxs-lookup"><span data-stu-id="44fc0-946">RepeatOne</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8EE.png" width="32" height="32" alt="RepeatAll" /></td>
  <td><span data-ttu-id="44fc0-947">E8EE</span><span class="sxs-lookup"><span data-stu-id="44fc0-947">E8EE</span></span></td>
  <td><span data-ttu-id="44fc0-948">RepeatAll</span><span class="sxs-lookup"><span data-stu-id="44fc0-948">RepeatAll</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8EF.png" width="32" height="32" alt="Calculator" /></td>
  <td><span data-ttu-id="44fc0-949">E8EF</span><span class="sxs-lookup"><span data-stu-id="44fc0-949">E8EF</span></span></td>
  <td><span data-ttu-id="44fc0-950">Rechner</span><span class="sxs-lookup"><span data-stu-id="44fc0-950">Calculator</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8F0.png" width="32" height="32" alt="Directions" /></td>
  <td><span data-ttu-id="44fc0-951">E8F0</span><span class="sxs-lookup"><span data-stu-id="44fc0-951">E8F0</span></span></td>
  <td><span data-ttu-id="44fc0-952">Directions</span><span class="sxs-lookup"><span data-stu-id="44fc0-952">Directions</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8F1.png" width="32" height="32" alt="Library" /></td>
  <td><span data-ttu-id="44fc0-953">E8F1</span><span class="sxs-lookup"><span data-stu-id="44fc0-953">E8F1</span></span></td>
  <td><span data-ttu-id="44fc0-954">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="44fc0-954">Library</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8F2.png" width="32" height="32" alt="ChatBubbles" /></td>
  <td><span data-ttu-id="44fc0-955">E8F2</span><span class="sxs-lookup"><span data-stu-id="44fc0-955">E8F2</span></span></td>
  <td><span data-ttu-id="44fc0-956">ChatBubbles</span><span class="sxs-lookup"><span data-stu-id="44fc0-956">ChatBubbles</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8F3.png" width="32" height="32" alt="PostUpdate" /></td>
  <td><span data-ttu-id="44fc0-957">E8F3</span><span class="sxs-lookup"><span data-stu-id="44fc0-957">E8F3</span></span></td>
  <td><span data-ttu-id="44fc0-958">PostUpdate</span><span class="sxs-lookup"><span data-stu-id="44fc0-958">PostUpdate</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8F4.png" width="32" height="32" alt="NewFolder" /></td>
  <td><span data-ttu-id="44fc0-959">E8F4</span><span class="sxs-lookup"><span data-stu-id="44fc0-959">E8F4</span></span></td>
  <td><span data-ttu-id="44fc0-960">NewFolder</span><span class="sxs-lookup"><span data-stu-id="44fc0-960">NewFolder</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8F5.png" width="32" height="32" alt="CalendarReply" /></td>
  <td><span data-ttu-id="44fc0-961">E8F5</span><span class="sxs-lookup"><span data-stu-id="44fc0-961">E8F5</span></span></td>
  <td><span data-ttu-id="44fc0-962">CalendarReply</span><span class="sxs-lookup"><span data-stu-id="44fc0-962">CalendarReply</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8F6.png" width="32" height="32" alt="UnsyncFolder" /></td>
  <td><span data-ttu-id="44fc0-963">E8F6</span><span class="sxs-lookup"><span data-stu-id="44fc0-963">E8F6</span></span></td>
  <td><span data-ttu-id="44fc0-964">UnsyncFolder</span><span class="sxs-lookup"><span data-stu-id="44fc0-964">UnsyncFolder</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8F7.png" width="32" height="32" alt="SyncFolder" /></td>
  <td><span data-ttu-id="44fc0-965">E8F7</span><span class="sxs-lookup"><span data-stu-id="44fc0-965">E8F7</span></span></td>
  <td><span data-ttu-id="44fc0-966">SyncFolder</span><span class="sxs-lookup"><span data-stu-id="44fc0-966">SyncFolder</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8F8.png" width="32" height="32" alt="BlockContact" /></td>
  <td><span data-ttu-id="44fc0-967">E8F8</span><span class="sxs-lookup"><span data-stu-id="44fc0-967">E8F8</span></span></td>
  <td><span data-ttu-id="44fc0-968">BlockContact</span><span class="sxs-lookup"><span data-stu-id="44fc0-968">BlockContact</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8F9.png" width="32" height="32" alt="SwitchApps" /></td>
  <td><span data-ttu-id="44fc0-969">E8F9</span><span class="sxs-lookup"><span data-stu-id="44fc0-969">E8F9</span></span></td>
  <td><span data-ttu-id="44fc0-970">SwitchApps</span><span class="sxs-lookup"><span data-stu-id="44fc0-970">SwitchApps</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8FA.png" width="32" height="32" alt="AddFriend" /></td>
  <td><span data-ttu-id="44fc0-971">E8FA</span><span class="sxs-lookup"><span data-stu-id="44fc0-971">E8FA</span></span></td>
  <td><span data-ttu-id="44fc0-972">AddFriend</span><span class="sxs-lookup"><span data-stu-id="44fc0-972">AddFriend</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8FB.png" width="32" height="32" alt="Accept" /></td>
  <td><span data-ttu-id="44fc0-973">E8FB</span><span class="sxs-lookup"><span data-stu-id="44fc0-973">E8FB</span></span></td>
  <td><span data-ttu-id="44fc0-974">Akzeptieren</span><span class="sxs-lookup"><span data-stu-id="44fc0-974">Accept</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8FC.png" width="32" height="32" alt="GoToStart" /></td>
  <td><span data-ttu-id="44fc0-975">E8FC</span><span class="sxs-lookup"><span data-stu-id="44fc0-975">E8FC</span></span></td>
  <td><span data-ttu-id="44fc0-976">GoToStart</span><span class="sxs-lookup"><span data-stu-id="44fc0-976">GoToStart</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8FD.png" width="32" height="32" alt="BulletedList" /></td>
  <td><span data-ttu-id="44fc0-977">E8FD</span><span class="sxs-lookup"><span data-stu-id="44fc0-977">E8FD</span></span></td>
  <td><span data-ttu-id="44fc0-978">BulletedList</span><span class="sxs-lookup"><span data-stu-id="44fc0-978">BulletedList</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8FE.png" width="32" height="32" alt="Scan" /></td>
  <td><span data-ttu-id="44fc0-979">E8FE</span><span class="sxs-lookup"><span data-stu-id="44fc0-979">E8FE</span></span></td>
  <td><span data-ttu-id="44fc0-980">Scannen</span><span class="sxs-lookup"><span data-stu-id="44fc0-980">Scan</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E8FF.png" width="32" height="32" alt="Preview" /></td>
  <td><span data-ttu-id="44fc0-981">E8FF</span><span class="sxs-lookup"><span data-stu-id="44fc0-981">E8FF</span></span></td>
  <td><span data-ttu-id="44fc0-982">Preview</span><span class="sxs-lookup"><span data-stu-id="44fc0-982">Preview</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E902.png" width="32" height="32" alt="Group" /></td>
  <td><span data-ttu-id="44fc0-983">E902</span><span class="sxs-lookup"><span data-stu-id="44fc0-983">E902</span></span></td>
  <td><span data-ttu-id="44fc0-984">Gruppe</span><span class="sxs-lookup"><span data-stu-id="44fc0-984">Group</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E904.png" width="32" height="32" alt="ZeroBars" /></td>
  <td><span data-ttu-id="44fc0-985">E904</span><span class="sxs-lookup"><span data-stu-id="44fc0-985">E904</span></span></td>
  <td><span data-ttu-id="44fc0-986">ZeroBars</span><span class="sxs-lookup"><span data-stu-id="44fc0-986">ZeroBars</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E905.png" width="32" height="32" alt="OneBar" /></td>
  <td><span data-ttu-id="44fc0-987">E905</span><span class="sxs-lookup"><span data-stu-id="44fc0-987">E905</span></span></td>
  <td><span data-ttu-id="44fc0-988">OneBar</span><span class="sxs-lookup"><span data-stu-id="44fc0-988">OneBar</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E906.png" width="32" height="32" alt="TwoBars" /></td>
  <td><span data-ttu-id="44fc0-989">E906</span><span class="sxs-lookup"><span data-stu-id="44fc0-989">E906</span></span></td>
  <td><span data-ttu-id="44fc0-990">TwoBars</span><span class="sxs-lookup"><span data-stu-id="44fc0-990">TwoBars</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E907.png" width="32" height="32" alt="ThreeBars" /></td>
  <td><span data-ttu-id="44fc0-991">E907</span><span class="sxs-lookup"><span data-stu-id="44fc0-991">E907</span></span></td>
  <td><span data-ttu-id="44fc0-992">ThreeBars</span><span class="sxs-lookup"><span data-stu-id="44fc0-992">ThreeBars</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E908.png" width="32" height="32" alt="FourBars" /></td>
  <td><span data-ttu-id="44fc0-993">E908</span><span class="sxs-lookup"><span data-stu-id="44fc0-993">E908</span></span></td>
  <td><span data-ttu-id="44fc0-994">FourBars</span><span class="sxs-lookup"><span data-stu-id="44fc0-994">FourBars</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E909.png" width="32" height="32" alt="World" /></td>
  <td><span data-ttu-id="44fc0-995">E909</span><span class="sxs-lookup"><span data-stu-id="44fc0-995">E909</span></span></td>
  <td><span data-ttu-id="44fc0-996">World</span><span class="sxs-lookup"><span data-stu-id="44fc0-996">World</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E90A.png" width="32" height="32" alt="Comment" /></td>
  <td><span data-ttu-id="44fc0-997">E90A</span><span class="sxs-lookup"><span data-stu-id="44fc0-997">E90A</span></span></td>
  <td><span data-ttu-id="44fc0-998">Kommentar</span><span class="sxs-lookup"><span data-stu-id="44fc0-998">Comment</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E90B.png" width="32" height="32" alt="MusicInfo" /></td>
  <td><span data-ttu-id="44fc0-999">E90B</span><span class="sxs-lookup"><span data-stu-id="44fc0-999">E90B</span></span></td>
  <td><span data-ttu-id="44fc0-1000">MusicInfo</span><span class="sxs-lookup"><span data-stu-id="44fc0-1000">MusicInfo</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E90C.png" width="32" height="32" alt="DockLeft" /></td>
  <td><span data-ttu-id="44fc0-1001">E90C</span><span class="sxs-lookup"><span data-stu-id="44fc0-1001">E90C</span></span></td>
  <td><span data-ttu-id="44fc0-1002">DockLeft</span><span class="sxs-lookup"><span data-stu-id="44fc0-1002">DockLeft</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E90D.png" width="32" height="32" alt="DockRight" /></td>
  <td><span data-ttu-id="44fc0-1003">E90D</span><span class="sxs-lookup"><span data-stu-id="44fc0-1003">E90D</span></span></td>
  <td><span data-ttu-id="44fc0-1004">DockRight</span><span class="sxs-lookup"><span data-stu-id="44fc0-1004">DockRight</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E90E.png" width="32" height="32" alt="DockBottom" /></td>
  <td><span data-ttu-id="44fc0-1005">E90E</span><span class="sxs-lookup"><span data-stu-id="44fc0-1005">E90E</span></span></td>
  <td><span data-ttu-id="44fc0-1006">DockBottom</span><span class="sxs-lookup"><span data-stu-id="44fc0-1006">DockBottom</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E90F.png" width="32" height="32" alt="Repair" /></td>
  <td><span data-ttu-id="44fc0-1007">E90F</span><span class="sxs-lookup"><span data-stu-id="44fc0-1007">E90F</span></span></td>
  <td><span data-ttu-id="44fc0-1008">Repair</span><span class="sxs-lookup"><span data-stu-id="44fc0-1008">Repair</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E910.png" width="32" height="32" alt="Accounts" /></td>
  <td><span data-ttu-id="44fc0-1009">E910</span><span class="sxs-lookup"><span data-stu-id="44fc0-1009">E910</span></span></td>
  <td><span data-ttu-id="44fc0-1010">Konten</span><span class="sxs-lookup"><span data-stu-id="44fc0-1010">Accounts</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E911.png" width="32" height="32" alt="DullSound" /></td>
  <td><span data-ttu-id="44fc0-1011">E911</span><span class="sxs-lookup"><span data-stu-id="44fc0-1011">E911</span></span></td>
  <td><span data-ttu-id="44fc0-1012">DullSound</span><span class="sxs-lookup"><span data-stu-id="44fc0-1012">DullSound</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E912.png" width="32" height="32" alt="Manage" /></td>
  <td><span data-ttu-id="44fc0-1013">E912</span><span class="sxs-lookup"><span data-stu-id="44fc0-1013">E912</span></span></td>
  <td><span data-ttu-id="44fc0-1014">Verwalten</span><span class="sxs-lookup"><span data-stu-id="44fc0-1014">Manage</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E913.png" width="32" height="32" alt="Street" /></td>
  <td><span data-ttu-id="44fc0-1015">E913</span><span class="sxs-lookup"><span data-stu-id="44fc0-1015">E913</span></span></td>
  <td><span data-ttu-id="44fc0-1016">Street</span><span class="sxs-lookup"><span data-stu-id="44fc0-1016">Street</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E914.png" width="32" height="32" alt="Printer3D" /></td>
  <td><span data-ttu-id="44fc0-1017">E914</span><span class="sxs-lookup"><span data-stu-id="44fc0-1017">E914</span></span></td>
  <td><span data-ttu-id="44fc0-1018">Printer3D</span><span class="sxs-lookup"><span data-stu-id="44fc0-1018">Printer3D</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E915.png" width="32" height="32" alt="RadioBullet" /></td>
  <td><span data-ttu-id="44fc0-1019">E915</span><span class="sxs-lookup"><span data-stu-id="44fc0-1019">E915</span></span></td>
  <td><span data-ttu-id="44fc0-1020">RadioBullet</span><span class="sxs-lookup"><span data-stu-id="44fc0-1020">RadioBullet</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E916.png" width="32" height="32" alt="Stopwatch" /></td>
  <td><span data-ttu-id="44fc0-1021">E916</span><span class="sxs-lookup"><span data-stu-id="44fc0-1021">E916</span></span></td>
  <td><span data-ttu-id="44fc0-1022">Stopwatch</span><span class="sxs-lookup"><span data-stu-id="44fc0-1022">Stopwatch</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E91B.png" width="32" height="32" alt="Photo" /></td>
  <td><span data-ttu-id="44fc0-1023">E91B</span><span class="sxs-lookup"><span data-stu-id="44fc0-1023">E91B</span></span></td>
  <td><span data-ttu-id="44fc0-1024">Foto</span><span class="sxs-lookup"><span data-stu-id="44fc0-1024">Photo</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E91C.png" width="32" height="32" alt="ActionCenter" /></td>
  <td><span data-ttu-id="44fc0-1025">E91C</span><span class="sxs-lookup"><span data-stu-id="44fc0-1025">E91C</span></span></td>
  <td><span data-ttu-id="44fc0-1026">ActionCenter</span><span class="sxs-lookup"><span data-stu-id="44fc0-1026">ActionCenter</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E91F.png" width="32" height="32" alt="FullCircleMask" /></td>
  <td><span data-ttu-id="44fc0-1027">E91F</span><span class="sxs-lookup"><span data-stu-id="44fc0-1027">E91F</span></span></td>
  <td><span data-ttu-id="44fc0-1028">FullCircleMask</span><span class="sxs-lookup"><span data-stu-id="44fc0-1028">FullCircleMask</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E921.png" width="32" height="32" alt="ChromeMinimize" /></td>
  <td><span data-ttu-id="44fc0-1029">E921</span><span class="sxs-lookup"><span data-stu-id="44fc0-1029">E921</span></span></td>
  <td><span data-ttu-id="44fc0-1030">ChromeMinimize</span><span class="sxs-lookup"><span data-stu-id="44fc0-1030">ChromeMinimize</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E922.png" width="32" height="32" alt="ChromeMaximize" /></td>
  <td><span data-ttu-id="44fc0-1031">E922</span><span class="sxs-lookup"><span data-stu-id="44fc0-1031">E922</span></span></td>
  <td><span data-ttu-id="44fc0-1032">ChromeMaximize</span><span class="sxs-lookup"><span data-stu-id="44fc0-1032">ChromeMaximize</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E923.png" width="32" height="32" alt="ChromeRestore" /></td>
  <td><span data-ttu-id="44fc0-1033">E923</span><span class="sxs-lookup"><span data-stu-id="44fc0-1033">E923</span></span></td>
  <td><span data-ttu-id="44fc0-1034">ChromeRestore</span><span class="sxs-lookup"><span data-stu-id="44fc0-1034">ChromeRestore</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E924.png" width="32" height="32" alt="Annotation" /></td>
  <td><span data-ttu-id="44fc0-1035">E924</span><span class="sxs-lookup"><span data-stu-id="44fc0-1035">E924</span></span></td>
  <td><span data-ttu-id="44fc0-1036">Annotation</span><span class="sxs-lookup"><span data-stu-id="44fc0-1036">Annotation</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E925.png" width="32" height="32" alt="BackSpaceQWERTYSm" /></td>
  <td><span data-ttu-id="44fc0-1037">E925</span><span class="sxs-lookup"><span data-stu-id="44fc0-1037">E925</span></span></td>
  <td><span data-ttu-id="44fc0-1038">BackSpaceQWERTYSm</span><span class="sxs-lookup"><span data-stu-id="44fc0-1038">BackSpaceQWERTYSm</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E926.png" width="32" height="32" alt="BackSpaceQWERTYMd" /></td>
  <td><span data-ttu-id="44fc0-1039">E926</span><span class="sxs-lookup"><span data-stu-id="44fc0-1039">E926</span></span></td>
  <td><span data-ttu-id="44fc0-1040">BackSpaceQWERTYMd</span><span class="sxs-lookup"><span data-stu-id="44fc0-1040">BackSpaceQWERTYMd</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E927.png" width="32" height="32" alt="Swipe" /></td>
  <td><span data-ttu-id="44fc0-1041">E927</span><span class="sxs-lookup"><span data-stu-id="44fc0-1041">E927</span></span></td>
  <td><span data-ttu-id="44fc0-1042">Wischen</span><span class="sxs-lookup"><span data-stu-id="44fc0-1042">Swipe</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E928.png" width="32" height="32" alt="Fingerprint" /></td>
  <td><span data-ttu-id="44fc0-1043">E928</span><span class="sxs-lookup"><span data-stu-id="44fc0-1043">E928</span></span></td>
  <td><span data-ttu-id="44fc0-1044">Fingerprint</span><span class="sxs-lookup"><span data-stu-id="44fc0-1044">Fingerprint</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E929.png" width="32" height="32" alt="Handwriting" /></td>
  <td><span data-ttu-id="44fc0-1045">E929</span><span class="sxs-lookup"><span data-stu-id="44fc0-1045">E929</span></span></td>
  <td><span data-ttu-id="44fc0-1046">Handwriting</span><span class="sxs-lookup"><span data-stu-id="44fc0-1046">Handwriting</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E92C.png" width="32" height="32" alt="ChromeBackToWindow" /></td>
  <td><span data-ttu-id="44fc0-1047">E92C</span><span class="sxs-lookup"><span data-stu-id="44fc0-1047">E92C</span></span></td>
  <td><span data-ttu-id="44fc0-1048">ChromeBackToWindow</span><span class="sxs-lookup"><span data-stu-id="44fc0-1048">ChromeBackToWindow</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E92D.png" width="32" height="32" alt="ChromeFullScreen" /></td>
  <td><span data-ttu-id="44fc0-1049">E92D</span><span class="sxs-lookup"><span data-stu-id="44fc0-1049">E92D</span></span></td>
  <td><span data-ttu-id="44fc0-1050">ChromeFullScreen</span><span class="sxs-lookup"><span data-stu-id="44fc0-1050">ChromeFullScreen</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E92E.png" width="32" height="32" alt="KeyboardStandard" /></td>
  <td><span data-ttu-id="44fc0-1051">E92E</span><span class="sxs-lookup"><span data-stu-id="44fc0-1051">E92E</span></span></td>
  <td><span data-ttu-id="44fc0-1052">KeyboardStandard</span><span class="sxs-lookup"><span data-stu-id="44fc0-1052">KeyboardStandard</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E92F.png" width="32" height="32" alt="KeyboardDismiss" /></td>
  <td><span data-ttu-id="44fc0-1053">E92F</span><span class="sxs-lookup"><span data-stu-id="44fc0-1053">E92F</span></span></td>
  <td><span data-ttu-id="44fc0-1054">KeyboardDismiss</span><span class="sxs-lookup"><span data-stu-id="44fc0-1054">KeyboardDismiss</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E930.png" width="32" height="32" alt="Completed" /></td>
  <td><span data-ttu-id="44fc0-1055">E930</span><span class="sxs-lookup"><span data-stu-id="44fc0-1055">E930</span></span></td>
  <td><span data-ttu-id="44fc0-1056">Completed</span><span class="sxs-lookup"><span data-stu-id="44fc0-1056">Completed</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E931.png" width="32" height="32" alt="ChromeAnnotate" /></td>
  <td><span data-ttu-id="44fc0-1057">E931</span><span class="sxs-lookup"><span data-stu-id="44fc0-1057">E931</span></span></td>
  <td><span data-ttu-id="44fc0-1058">ChromeAnnotate</span><span class="sxs-lookup"><span data-stu-id="44fc0-1058">ChromeAnnotate</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E932.png" width="32" height="32" alt="Label" /></td>
  <td><span data-ttu-id="44fc0-1059">E932</span><span class="sxs-lookup"><span data-stu-id="44fc0-1059">E932</span></span></td>
  <td><span data-ttu-id="44fc0-1060">Label</span><span class="sxs-lookup"><span data-stu-id="44fc0-1060">Label</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E933.png" width="32" height="32" alt="IBeam" /></td>
  <td><span data-ttu-id="44fc0-1061">E933</span><span class="sxs-lookup"><span data-stu-id="44fc0-1061">E933</span></span></td>
  <td><span data-ttu-id="44fc0-1062">IBeam</span><span class="sxs-lookup"><span data-stu-id="44fc0-1062">IBeam</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E934.png" width="32" height="32" alt="IBeamOutline" /></td>
  <td><span data-ttu-id="44fc0-1063">E934</span><span class="sxs-lookup"><span data-stu-id="44fc0-1063">E934</span></span></td>
  <td><span data-ttu-id="44fc0-1064">IBeamOutline</span><span class="sxs-lookup"><span data-stu-id="44fc0-1064">IBeamOutline</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E935.png" width="32" height="32" alt="FlickDown" /></td>
  <td><span data-ttu-id="44fc0-1065">E935</span><span class="sxs-lookup"><span data-stu-id="44fc0-1065">E935</span></span></td>
  <td><span data-ttu-id="44fc0-1066">FlickDown</span><span class="sxs-lookup"><span data-stu-id="44fc0-1066">FlickDown</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E936.png" width="32" height="32" alt="FlickUp" /></td>
  <td><span data-ttu-id="44fc0-1067">E936</span><span class="sxs-lookup"><span data-stu-id="44fc0-1067">E936</span></span></td>
  <td><span data-ttu-id="44fc0-1068">FlickUp</span><span class="sxs-lookup"><span data-stu-id="44fc0-1068">FlickUp</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E937.png" width="32" height="32" alt="FlickLeft" /></td>
  <td><span data-ttu-id="44fc0-1069">E937</span><span class="sxs-lookup"><span data-stu-id="44fc0-1069">E937</span></span></td>
  <td><span data-ttu-id="44fc0-1070">FlickLeft</span><span class="sxs-lookup"><span data-stu-id="44fc0-1070">FlickLeft</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E938.png" width="32" height="32" alt="FlickRight" /></td>
  <td><span data-ttu-id="44fc0-1071">E938</span><span class="sxs-lookup"><span data-stu-id="44fc0-1071">E938</span></span></td>
  <td><span data-ttu-id="44fc0-1072">FlickRight</span><span class="sxs-lookup"><span data-stu-id="44fc0-1072">FlickRight</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E939.png" width="32" height="32" alt="FeedbackApp" /></td>
  <td><span data-ttu-id="44fc0-1073">E939</span><span class="sxs-lookup"><span data-stu-id="44fc0-1073">E939</span></span></td>
  <td><span data-ttu-id="44fc0-1074">FeedbackApp</span><span class="sxs-lookup"><span data-stu-id="44fc0-1074">FeedbackApp</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E93C.png" width="32" height="32" alt="MusicAlbum" /></td>
  <td><span data-ttu-id="44fc0-1075">E93C</span><span class="sxs-lookup"><span data-stu-id="44fc0-1075">E93C</span></span></td>
  <td><span data-ttu-id="44fc0-1076">MusicAlbum</span><span class="sxs-lookup"><span data-stu-id="44fc0-1076">MusicAlbum</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E93E.png" width="32" height="32" alt="Streaming" /></td>
  <td><span data-ttu-id="44fc0-1077">E93E</span><span class="sxs-lookup"><span data-stu-id="44fc0-1077">E93E</span></span></td>
  <td><span data-ttu-id="44fc0-1078">Streaming</span><span class="sxs-lookup"><span data-stu-id="44fc0-1078">Streaming</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E943.png" width="32" height="32" alt="Code" /></td>
  <td><span data-ttu-id="44fc0-1079">E943</span><span class="sxs-lookup"><span data-stu-id="44fc0-1079">E943</span></span></td>
  <td><span data-ttu-id="44fc0-1080">Code</span><span class="sxs-lookup"><span data-stu-id="44fc0-1080">Code</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E944.png" width="32" height="32" alt="ReturnToWindow" /></td>
  <td><span data-ttu-id="44fc0-1081">E944</span><span class="sxs-lookup"><span data-stu-id="44fc0-1081">E944</span></span></td>
  <td><span data-ttu-id="44fc0-1082">ReturnToWindow</span><span class="sxs-lookup"><span data-stu-id="44fc0-1082">ReturnToWindow</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E945.png" width="32" height="32" alt="LightningBolt" /></td>
  <td><span data-ttu-id="44fc0-1083">E945</span><span class="sxs-lookup"><span data-stu-id="44fc0-1083">E945</span></span></td>
  <td><span data-ttu-id="44fc0-1084">LightningBolt</span><span class="sxs-lookup"><span data-stu-id="44fc0-1084">LightningBolt</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E946.png" width="32" height="32" alt="Info" /></td>
  <td><span data-ttu-id="44fc0-1085">E946</span><span class="sxs-lookup"><span data-stu-id="44fc0-1085">E946</span></span></td>
  <td><span data-ttu-id="44fc0-1086">Info</span><span class="sxs-lookup"><span data-stu-id="44fc0-1086">Info</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E947.png" width="32" height="32" alt="CalculatorMultiply" /></td>
  <td><span data-ttu-id="44fc0-1087">E947</span><span class="sxs-lookup"><span data-stu-id="44fc0-1087">E947</span></span></td>
  <td><span data-ttu-id="44fc0-1088">CalculatorMultiply</span><span class="sxs-lookup"><span data-stu-id="44fc0-1088">CalculatorMultiply</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E948.png" width="32" height="32" alt="CalculatorAddition" /></td>
  <td><span data-ttu-id="44fc0-1089">E948</span><span class="sxs-lookup"><span data-stu-id="44fc0-1089">E948</span></span></td>
  <td><span data-ttu-id="44fc0-1090">CalculatorAddition</span><span class="sxs-lookup"><span data-stu-id="44fc0-1090">CalculatorAddition</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E949.png" width="32" height="32" alt="CalculatorSubtract" /></td>
  <td><span data-ttu-id="44fc0-1091">E949</span><span class="sxs-lookup"><span data-stu-id="44fc0-1091">E949</span></span></td>
  <td><span data-ttu-id="44fc0-1092">CalculatorSubtract</span><span class="sxs-lookup"><span data-stu-id="44fc0-1092">CalculatorSubtract</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E94A.png" width="32" height="32" alt="CalculatorDivide" /></td>
  <td><span data-ttu-id="44fc0-1093">E94A</span><span class="sxs-lookup"><span data-stu-id="44fc0-1093">E94A</span></span></td>
  <td><span data-ttu-id="44fc0-1094">CalculatorDivide</span><span class="sxs-lookup"><span data-stu-id="44fc0-1094">CalculatorDivide</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E94B.png" width="32" height="32" alt="CalculatorSquareroot" /></td>
  <td><span data-ttu-id="44fc0-1095">E94B</span><span class="sxs-lookup"><span data-stu-id="44fc0-1095">E94B</span></span></td>
  <td><span data-ttu-id="44fc0-1096">CalculatorSquareroot</span><span class="sxs-lookup"><span data-stu-id="44fc0-1096">CalculatorSquareroot</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E94C.png" width="32" height="32" alt="CalculatorPercentage" /></td>
  <td><span data-ttu-id="44fc0-1097">E94C</span><span class="sxs-lookup"><span data-stu-id="44fc0-1097">E94C</span></span></td>
  <td><span data-ttu-id="44fc0-1098">CalculatorPercentage</span><span class="sxs-lookup"><span data-stu-id="44fc0-1098">CalculatorPercentage</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E94D.png" width="32" height="32" alt="CalculatorNegate" /></td>
  <td><span data-ttu-id="44fc0-1099">E94D</span><span class="sxs-lookup"><span data-stu-id="44fc0-1099">E94D</span></span></td>
  <td><span data-ttu-id="44fc0-1100">CalculatorNegate</span><span class="sxs-lookup"><span data-stu-id="44fc0-1100">CalculatorNegate</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E94E.png" width="32" height="32" alt="CalculatorEqualTo" /></td>
  <td><span data-ttu-id="44fc0-1101">E94E</span><span class="sxs-lookup"><span data-stu-id="44fc0-1101">E94E</span></span></td>
  <td><span data-ttu-id="44fc0-1102">CalculatorEqualTo</span><span class="sxs-lookup"><span data-stu-id="44fc0-1102">CalculatorEqualTo</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E94F.png" width="32" height="32" alt="CalculatorBackspace" /></td>
  <td><span data-ttu-id="44fc0-1103">E94F</span><span class="sxs-lookup"><span data-stu-id="44fc0-1103">E94F</span></span></td>
  <td><span data-ttu-id="44fc0-1104">CalculatorBackspace</span><span class="sxs-lookup"><span data-stu-id="44fc0-1104">CalculatorBackspace</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E950.png" width="32" height="32" alt="Component" /></td>
  <td><span data-ttu-id="44fc0-1105">E950</span><span class="sxs-lookup"><span data-stu-id="44fc0-1105">E950</span></span></td>
  <td><span data-ttu-id="44fc0-1106">Komponente</span><span class="sxs-lookup"><span data-stu-id="44fc0-1106">Component</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E951.png" width="32" height="32" alt="DMC" /></td>
  <td><span data-ttu-id="44fc0-1107">E951</span><span class="sxs-lookup"><span data-stu-id="44fc0-1107">E951</span></span></td>
  <td><span data-ttu-id="44fc0-1108">DMC</span><span class="sxs-lookup"><span data-stu-id="44fc0-1108">DMC</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E952.png" width="32" height="32" alt="Dock" /></td>
  <td><span data-ttu-id="44fc0-1109">E952</span><span class="sxs-lookup"><span data-stu-id="44fc0-1109">E952</span></span></td>
  <td><span data-ttu-id="44fc0-1110">Dock</span><span class="sxs-lookup"><span data-stu-id="44fc0-1110">Dock</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E953.png" width="32" height="32" alt="MultimediaDMS" /></td>
  <td><span data-ttu-id="44fc0-1111">E953</span><span class="sxs-lookup"><span data-stu-id="44fc0-1111">E953</span></span></td>
  <td><span data-ttu-id="44fc0-1112">MultimediaDMS</span><span class="sxs-lookup"><span data-stu-id="44fc0-1112">MultimediaDMS</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E954.png" width="32" height="32" alt="MultimediaDVR" /></td>
  <td><span data-ttu-id="44fc0-1113">E954</span><span class="sxs-lookup"><span data-stu-id="44fc0-1113">E954</span></span></td>
  <td><span data-ttu-id="44fc0-1114">MultimediaDVR</span><span class="sxs-lookup"><span data-stu-id="44fc0-1114">MultimediaDVR</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E955.png" width="32" height="32" alt="MultimediaPMP" /></td>
  <td><span data-ttu-id="44fc0-1115">E955</span><span class="sxs-lookup"><span data-stu-id="44fc0-1115">E955</span></span></td>
  <td><span data-ttu-id="44fc0-1116">MultimediaPMP</span><span class="sxs-lookup"><span data-stu-id="44fc0-1116">MultimediaPMP</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E956.png" width="32" height="32" alt="PrintfaxPrinterFile" /></td>
  <td><span data-ttu-id="44fc0-1117">E956</span><span class="sxs-lookup"><span data-stu-id="44fc0-1117">E956</span></span></td>
  <td><span data-ttu-id="44fc0-1118">PrintfaxPrinterFile</span><span class="sxs-lookup"><span data-stu-id="44fc0-1118">PrintfaxPrinterFile</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E957.png" width="32" height="32" alt="Sensor" /></td>
  <td><span data-ttu-id="44fc0-1119">E957</span><span class="sxs-lookup"><span data-stu-id="44fc0-1119">E957</span></span></td>
  <td><span data-ttu-id="44fc0-1120">Sensor</span><span class="sxs-lookup"><span data-stu-id="44fc0-1120">Sensor</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E958.png" width="32" height="32" alt="StorageOptical" /></td>
  <td><span data-ttu-id="44fc0-1121">E958</span><span class="sxs-lookup"><span data-stu-id="44fc0-1121">E958</span></span></td>
  <td><span data-ttu-id="44fc0-1122">StorageOptical</span><span class="sxs-lookup"><span data-stu-id="44fc0-1122">StorageOptical</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E95A.png" width="32" height="32" alt="Communications" /></td>
  <td><span data-ttu-id="44fc0-1123">E95A</span><span class="sxs-lookup"><span data-stu-id="44fc0-1123">E95A</span></span></td>
  <td><span data-ttu-id="44fc0-1124">Communications</span><span class="sxs-lookup"><span data-stu-id="44fc0-1124">Communications</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E95B.png" width="32" height="32" alt="Headset" /></td>
  <td><span data-ttu-id="44fc0-1125">E95B</span><span class="sxs-lookup"><span data-stu-id="44fc0-1125">E95B</span></span></td>
  <td><span data-ttu-id="44fc0-1126">Headset</span><span class="sxs-lookup"><span data-stu-id="44fc0-1126">Headset</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E95D.png" width="32" height="32" alt="Projector" /></td>
  <td><span data-ttu-id="44fc0-1127">E95D</span><span class="sxs-lookup"><span data-stu-id="44fc0-1127">E95D</span></span></td>
  <td><span data-ttu-id="44fc0-1128">Projector</span><span class="sxs-lookup"><span data-stu-id="44fc0-1128">Projector</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E95E.png" width="32" height="32" alt="Health" /></td>
  <td><span data-ttu-id="44fc0-1129">E95E</span><span class="sxs-lookup"><span data-stu-id="44fc0-1129">E95E</span></span></td>
  <td><span data-ttu-id="44fc0-1130">Integrität</span><span class="sxs-lookup"><span data-stu-id="44fc0-1130">Health</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E960.png" width="32" height="32" alt="Webcam2" /></td>
  <td><span data-ttu-id="44fc0-1131">E960</span><span class="sxs-lookup"><span data-stu-id="44fc0-1131">E960</span></span></td>
  <td><span data-ttu-id="44fc0-1132">Webcam2</span><span class="sxs-lookup"><span data-stu-id="44fc0-1132">Webcam2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E961.png" width="32" height="32" alt="Input" /></td>
  <td><span data-ttu-id="44fc0-1133">E961</span><span class="sxs-lookup"><span data-stu-id="44fc0-1133">E961</span></span></td>
  <td><span data-ttu-id="44fc0-1134">Eingabeart</span><span class="sxs-lookup"><span data-stu-id="44fc0-1134">Input</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E962.png" width="32" height="32" alt="Mouse" /></td>
  <td><span data-ttu-id="44fc0-1135">E962</span><span class="sxs-lookup"><span data-stu-id="44fc0-1135">E962</span></span></td>
  <td><span data-ttu-id="44fc0-1136">Maus</span><span class="sxs-lookup"><span data-stu-id="44fc0-1136">Mouse</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E963.png" width="32" height="32" alt="Smartcard" /></td>
  <td><span data-ttu-id="44fc0-1137">E963</span><span class="sxs-lookup"><span data-stu-id="44fc0-1137">E963</span></span></td>
  <td><span data-ttu-id="44fc0-1138">Smartcard</span><span class="sxs-lookup"><span data-stu-id="44fc0-1138">Smartcard</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E964.png" width="32" height="32" alt="SmartcardVirtual" /></td>
  <td><span data-ttu-id="44fc0-1139">E964</span><span class="sxs-lookup"><span data-stu-id="44fc0-1139">E964</span></span></td>
  <td><span data-ttu-id="44fc0-1140">SmartcardVirtual</span><span class="sxs-lookup"><span data-stu-id="44fc0-1140">SmartcardVirtual</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E965.png" width="32" height="32" alt="MediaStorageTower" /></td>
  <td><span data-ttu-id="44fc0-1141">E965</span><span class="sxs-lookup"><span data-stu-id="44fc0-1141">E965</span></span></td>
  <td><span data-ttu-id="44fc0-1142">MediaStorageTower</span><span class="sxs-lookup"><span data-stu-id="44fc0-1142">MediaStorageTower</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E966.png" width="32" height="32" alt="ReturnKeySm" /></td>
  <td><span data-ttu-id="44fc0-1143">E966</span><span class="sxs-lookup"><span data-stu-id="44fc0-1143">E966</span></span></td>
  <td><span data-ttu-id="44fc0-1144">ReturnKeySm</span><span class="sxs-lookup"><span data-stu-id="44fc0-1144">ReturnKeySm</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E967.png" width="32" height="32" alt="GameConsole" /></td>
  <td><span data-ttu-id="44fc0-1145">E967</span><span class="sxs-lookup"><span data-stu-id="44fc0-1145">E967</span></span></td>
  <td><span data-ttu-id="44fc0-1146">GameConsole</span><span class="sxs-lookup"><span data-stu-id="44fc0-1146">GameConsole</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E968.png" width="32" height="32" alt="Network" /></td>
  <td><span data-ttu-id="44fc0-1147">E968</span><span class="sxs-lookup"><span data-stu-id="44fc0-1147">E968</span></span></td>
  <td><span data-ttu-id="44fc0-1148">Netzwerk</span><span class="sxs-lookup"><span data-stu-id="44fc0-1148">Network</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E969.png" width="32" height="32" alt="StorageNetworkWireless" /></td>
  <td><span data-ttu-id="44fc0-1149">E969</span><span class="sxs-lookup"><span data-stu-id="44fc0-1149">E969</span></span></td>
  <td><span data-ttu-id="44fc0-1150">StorageNetworkWireless</span><span class="sxs-lookup"><span data-stu-id="44fc0-1150">StorageNetworkWireless</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E96A.png" width="32" height="32" alt="StorageTape" /></td>
  <td><span data-ttu-id="44fc0-1151">E96A</span><span class="sxs-lookup"><span data-stu-id="44fc0-1151">E96A</span></span></td>
  <td><span data-ttu-id="44fc0-1152">StorageTape</span><span class="sxs-lookup"><span data-stu-id="44fc0-1152">StorageTape</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E96D.png" width="32" height="32" alt="ChevronUpSmall" /></td>
  <td><span data-ttu-id="44fc0-1153">E96D</span><span class="sxs-lookup"><span data-stu-id="44fc0-1153">E96D</span></span></td>
  <td><span data-ttu-id="44fc0-1154">ChevronUpSmall</span><span class="sxs-lookup"><span data-stu-id="44fc0-1154">ChevronUpSmall</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E96E.png" width="32" height="32" alt="ChevronDownSmall" /></td>
  <td><span data-ttu-id="44fc0-1155">E96E</span><span class="sxs-lookup"><span data-stu-id="44fc0-1155">E96E</span></span></td>
  <td><span data-ttu-id="44fc0-1156">ChevronDownSmall</span><span class="sxs-lookup"><span data-stu-id="44fc0-1156">ChevronDownSmall</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E96F.png" width="32" height="32" alt="ChevronLeftSmall" /></td>
  <td><span data-ttu-id="44fc0-1157">E96F</span><span class="sxs-lookup"><span data-stu-id="44fc0-1157">E96F</span></span></td>
  <td><span data-ttu-id="44fc0-1158">ChevronLeftSmall</span><span class="sxs-lookup"><span data-stu-id="44fc0-1158">ChevronLeftSmall</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E970.png" width="32" height="32" alt="ChevronRightSmall" /></td>
  <td><span data-ttu-id="44fc0-1159">E970</span><span class="sxs-lookup"><span data-stu-id="44fc0-1159">E970</span></span></td>
  <td><span data-ttu-id="44fc0-1160">ChevronRightSmall</span><span class="sxs-lookup"><span data-stu-id="44fc0-1160">ChevronRightSmall</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E971.png" width="32" height="32" alt="ChevronUpMed" /></td>
  <td><span data-ttu-id="44fc0-1161">E971</span><span class="sxs-lookup"><span data-stu-id="44fc0-1161">E971</span></span></td>
  <td><span data-ttu-id="44fc0-1162">ChevronUpMed</span><span class="sxs-lookup"><span data-stu-id="44fc0-1162">ChevronUpMed</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E972.png" width="32" height="32" alt="ChevronDownMed" /></td>
  <td><span data-ttu-id="44fc0-1163">E972</span><span class="sxs-lookup"><span data-stu-id="44fc0-1163">E972</span></span></td>
  <td><span data-ttu-id="44fc0-1164">ChevronDownMed</span><span class="sxs-lookup"><span data-stu-id="44fc0-1164">ChevronDownMed</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E973.png" width="32" height="32" alt="ChevronLeftMed" /></td>
  <td><span data-ttu-id="44fc0-1165">E973</span><span class="sxs-lookup"><span data-stu-id="44fc0-1165">E973</span></span></td>
  <td><span data-ttu-id="44fc0-1166">ChevronLeftMed</span><span class="sxs-lookup"><span data-stu-id="44fc0-1166">ChevronLeftMed</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E974.png" width="32" height="32" alt="ChevronRightMed" /></td>
  <td><span data-ttu-id="44fc0-1167">E974</span><span class="sxs-lookup"><span data-stu-id="44fc0-1167">E974</span></span></td>
  <td><span data-ttu-id="44fc0-1168">ChevronRightMed</span><span class="sxs-lookup"><span data-stu-id="44fc0-1168">ChevronRightMed</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E975.png" width="32" height="32" alt="Devices2" /></td>
  <td><span data-ttu-id="44fc0-1169">E975</span><span class="sxs-lookup"><span data-stu-id="44fc0-1169">E975</span></span></td>
  <td><span data-ttu-id="44fc0-1170">Devices2</span><span class="sxs-lookup"><span data-stu-id="44fc0-1170">Devices2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E976.png" width="32" height="32" alt="ExpandTile" /></td>
  <td><span data-ttu-id="44fc0-1171">E976</span><span class="sxs-lookup"><span data-stu-id="44fc0-1171">E976</span></span></td>
  <td><span data-ttu-id="44fc0-1172">ExpandTile</span><span class="sxs-lookup"><span data-stu-id="44fc0-1172">ExpandTile</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E977.png" width="32" height="32" alt="PC1" /></td>
  <td><span data-ttu-id="44fc0-1173">E977</span><span class="sxs-lookup"><span data-stu-id="44fc0-1173">E977</span></span></td>
  <td><span data-ttu-id="44fc0-1174">PC1</span><span class="sxs-lookup"><span data-stu-id="44fc0-1174">PC1</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E978.png" width="32" height="32" alt="PresenceChicklet" /></td>
  <td><span data-ttu-id="44fc0-1175">E978</span><span class="sxs-lookup"><span data-stu-id="44fc0-1175">E978</span></span></td>
  <td><span data-ttu-id="44fc0-1176">PresenceChicklet</span><span class="sxs-lookup"><span data-stu-id="44fc0-1176">PresenceChicklet</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E979.png" width="32" height="32" alt="PresenceChickletVideo" /></td>
  <td><span data-ttu-id="44fc0-1177">E979</span><span class="sxs-lookup"><span data-stu-id="44fc0-1177">E979</span></span></td>
  <td><span data-ttu-id="44fc0-1178">PresenceChickletVideo</span><span class="sxs-lookup"><span data-stu-id="44fc0-1178">PresenceChickletVideo</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E97A.png" width="32" height="32" alt="Reply" /></td>
  <td><span data-ttu-id="44fc0-1179">E97A</span><span class="sxs-lookup"><span data-stu-id="44fc0-1179">E97A</span></span></td>
  <td><span data-ttu-id="44fc0-1180">Antworten</span><span class="sxs-lookup"><span data-stu-id="44fc0-1180">Reply</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E97B.png" width="32" height="32" alt="SetTile" /></td>
  <td><span data-ttu-id="44fc0-1181">E97B</span><span class="sxs-lookup"><span data-stu-id="44fc0-1181">E97B</span></span></td>
  <td><span data-ttu-id="44fc0-1182">SetTile</span><span class="sxs-lookup"><span data-stu-id="44fc0-1182">SetTile</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E97C.png" width="32" height="32" alt="Type" /></td>
  <td><span data-ttu-id="44fc0-1183">E97C</span><span class="sxs-lookup"><span data-stu-id="44fc0-1183">E97C</span></span></td>
  <td><span data-ttu-id="44fc0-1184">Eingabe</span><span class="sxs-lookup"><span data-stu-id="44fc0-1184">Type</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E97D.png" width="32" height="32" alt="Korean" /></td>
  <td><span data-ttu-id="44fc0-1185">E97D</span><span class="sxs-lookup"><span data-stu-id="44fc0-1185">E97D</span></span></td>
  <td><span data-ttu-id="44fc0-1186">Koreanisch</span><span class="sxs-lookup"><span data-stu-id="44fc0-1186">Korean</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E97E.png" width="32" height="32" alt="HalfAlpha" /></td>
  <td><span data-ttu-id="44fc0-1187">E97E</span><span class="sxs-lookup"><span data-stu-id="44fc0-1187">E97E</span></span></td>
  <td><span data-ttu-id="44fc0-1188">HalfAlpha</span><span class="sxs-lookup"><span data-stu-id="44fc0-1188">HalfAlpha</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E97F.png" width="32" height="32" alt="FullAlpha" /></td>
  <td><span data-ttu-id="44fc0-1189">E97F</span><span class="sxs-lookup"><span data-stu-id="44fc0-1189">E97F</span></span></td>
  <td><span data-ttu-id="44fc0-1190">FullAlpha</span><span class="sxs-lookup"><span data-stu-id="44fc0-1190">FullAlpha</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E980.png" width="32" height="32" alt="Key12On" /></td>
  <td><span data-ttu-id="44fc0-1191">E980</span><span class="sxs-lookup"><span data-stu-id="44fc0-1191">E980</span></span></td>
  <td><span data-ttu-id="44fc0-1192">Key12On</span><span class="sxs-lookup"><span data-stu-id="44fc0-1192">Key12On</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E981.png" width="32" height="32" alt="ChineseChangjie" /></td>
  <td><span data-ttu-id="44fc0-1193">E981</span><span class="sxs-lookup"><span data-stu-id="44fc0-1193">E981</span></span></td>
  <td><span data-ttu-id="44fc0-1194">ChineseChangjie</span><span class="sxs-lookup"><span data-stu-id="44fc0-1194">ChineseChangjie</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E982.png" width="32" height="32" alt="QWERTYOn" /></td>
  <td><span data-ttu-id="44fc0-1195">E982</span><span class="sxs-lookup"><span data-stu-id="44fc0-1195">E982</span></span></td>
  <td><span data-ttu-id="44fc0-1196">QWERTYOn</span><span class="sxs-lookup"><span data-stu-id="44fc0-1196">QWERTYOn</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E983.png" width="32" height="32" alt="QWERTYOff" /></td>
  <td><span data-ttu-id="44fc0-1197">E983</span><span class="sxs-lookup"><span data-stu-id="44fc0-1197">E983</span></span></td>
  <td><span data-ttu-id="44fc0-1198">QWERTYOff</span><span class="sxs-lookup"><span data-stu-id="44fc0-1198">QWERTYOff</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E984.png" width="32" height="32" alt="ChineseQuick" /></td>
  <td><span data-ttu-id="44fc0-1199">E984</span><span class="sxs-lookup"><span data-stu-id="44fc0-1199">E984</span></span></td>
  <td><span data-ttu-id="44fc0-1200">ChineseQuick</span><span class="sxs-lookup"><span data-stu-id="44fc0-1200">ChineseQuick</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E985.png" width="32" height="32" alt="Japanese" /></td>
  <td><span data-ttu-id="44fc0-1201">E985</span><span class="sxs-lookup"><span data-stu-id="44fc0-1201">E985</span></span></td>
  <td><span data-ttu-id="44fc0-1202">Japanisch</span><span class="sxs-lookup"><span data-stu-id="44fc0-1202">Japanese</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E986.png" width="32" height="32" alt="FullHiragana" /></td>
  <td><span data-ttu-id="44fc0-1203">E986</span><span class="sxs-lookup"><span data-stu-id="44fc0-1203">E986</span></span></td>
  <td><span data-ttu-id="44fc0-1204">FullHiragana</span><span class="sxs-lookup"><span data-stu-id="44fc0-1204">FullHiragana</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E987.png" width="32" height="32" alt="FullKatakana" /></td>
  <td><span data-ttu-id="44fc0-1205">E987</span><span class="sxs-lookup"><span data-stu-id="44fc0-1205">E987</span></span></td>
  <td><span data-ttu-id="44fc0-1206">FullKatakana</span><span class="sxs-lookup"><span data-stu-id="44fc0-1206">FullKatakana</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E988.png" width="32" height="32" alt="HalfKatakana" /></td>
  <td><span data-ttu-id="44fc0-1207">E988</span><span class="sxs-lookup"><span data-stu-id="44fc0-1207">E988</span></span></td>
  <td><span data-ttu-id="44fc0-1208">HalfKatakana</span><span class="sxs-lookup"><span data-stu-id="44fc0-1208">HalfKatakana</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E989.png" width="32" height="32" alt="ChineseBoPoMoFo" /></td>
  <td><span data-ttu-id="44fc0-1209">E989</span><span class="sxs-lookup"><span data-stu-id="44fc0-1209">E989</span></span></td>
  <td><span data-ttu-id="44fc0-1210">ChineseBoPoMoFo</span><span class="sxs-lookup"><span data-stu-id="44fc0-1210">ChineseBoPoMoFo</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E98A.png" width="32" height="32" alt="ChinesePinyin" /></td>
  <td><span data-ttu-id="44fc0-1211">E98A</span><span class="sxs-lookup"><span data-stu-id="44fc0-1211">E98A</span></span></td>
  <td><span data-ttu-id="44fc0-1212">ChinesePinyin</span><span class="sxs-lookup"><span data-stu-id="44fc0-1212">ChinesePinyin</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E98F.png" width="32" height="32" alt="ConstructionCone" /></td>
  <td><span data-ttu-id="44fc0-1213">E98F</span><span class="sxs-lookup"><span data-stu-id="44fc0-1213">E98F</span></span></td>
  <td><span data-ttu-id="44fc0-1214">ConstructionCone</span><span class="sxs-lookup"><span data-stu-id="44fc0-1214">ConstructionCone</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E990.png" width="32" height="32" alt="XboxOneConsole" /></td>
  <td><span data-ttu-id="44fc0-1215">E990</span><span class="sxs-lookup"><span data-stu-id="44fc0-1215">E990</span></span></td>
  <td><span data-ttu-id="44fc0-1216">XboxOneConsole</span><span class="sxs-lookup"><span data-stu-id="44fc0-1216">XboxOneConsole</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E992.png" width="32" height="32" alt="Volume0" /></td>
  <td><span data-ttu-id="44fc0-1217">E992</span><span class="sxs-lookup"><span data-stu-id="44fc0-1217">E992</span></span></td>
  <td><span data-ttu-id="44fc0-1218">Volume0</span><span class="sxs-lookup"><span data-stu-id="44fc0-1218">Volume0</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E993.png" width="32" height="32" alt="Volume1" /></td>
  <td><span data-ttu-id="44fc0-1219">E993</span><span class="sxs-lookup"><span data-stu-id="44fc0-1219">E993</span></span></td>
  <td><span data-ttu-id="44fc0-1220">Volume1</span><span class="sxs-lookup"><span data-stu-id="44fc0-1220">Volume1</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E994.png" width="32" height="32" alt="Volume2" /></td>
  <td><span data-ttu-id="44fc0-1221">E994</span><span class="sxs-lookup"><span data-stu-id="44fc0-1221">E994</span></span></td>
  <td><span data-ttu-id="44fc0-1222">Volume2</span><span class="sxs-lookup"><span data-stu-id="44fc0-1222">Volume2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E995.png" width="32" height="32" alt="Volume3" /></td>
  <td><span data-ttu-id="44fc0-1223">E995</span><span class="sxs-lookup"><span data-stu-id="44fc0-1223">E995</span></span></td>
  <td><span data-ttu-id="44fc0-1224">Volume3</span><span class="sxs-lookup"><span data-stu-id="44fc0-1224">Volume3</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E996.png" width="32" height="32" alt="BatteryUnknown" /></td>
  <td><span data-ttu-id="44fc0-1225">E996</span><span class="sxs-lookup"><span data-stu-id="44fc0-1225">E996</span></span></td>
  <td><span data-ttu-id="44fc0-1226">BatteryUnknown</span><span class="sxs-lookup"><span data-stu-id="44fc0-1226">BatteryUnknown</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E998.png" width="32" height="32" alt="WifiAttentionOverlay" /></td>
  <td><span data-ttu-id="44fc0-1227">E998</span><span class="sxs-lookup"><span data-stu-id="44fc0-1227">E998</span></span></td>
  <td><span data-ttu-id="44fc0-1228">WifiAttentionOverlay</span><span class="sxs-lookup"><span data-stu-id="44fc0-1228">WifiAttentionOverlay</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E99A.png" width="32" height="32" alt="Robot" /></td>
  <td><span data-ttu-id="44fc0-1229">E99A</span><span class="sxs-lookup"><span data-stu-id="44fc0-1229">E99A</span></span></td>
  <td><span data-ttu-id="44fc0-1230">Robot</span><span class="sxs-lookup"><span data-stu-id="44fc0-1230">Robot</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E9A1.png" width="32" height="32" alt="TapAndSend" /></td>
  <td><span data-ttu-id="44fc0-1231">E9A1</span><span class="sxs-lookup"><span data-stu-id="44fc0-1231">E9A1</span></span></td>
  <td><span data-ttu-id="44fc0-1232">TapAndSend</span><span class="sxs-lookup"><span data-stu-id="44fc0-1232">TapAndSend</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E9A6.png" width="32" height="32" alt="FitPage" /></td>
  <td><span data-ttu-id="44fc0-1233">E9A6</span><span class="sxs-lookup"><span data-stu-id="44fc0-1233">E9A6</span></span></td>
  <td><span data-ttu-id="44fc0-1234">FitPage</span><span class="sxs-lookup"><span data-stu-id="44fc0-1234">FitPage</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E9A8.png" width="32" height="32" alt="PasswordKeyShow" /></td>
  <td><span data-ttu-id="44fc0-1235">E9A8</span><span class="sxs-lookup"><span data-stu-id="44fc0-1235">E9A8</span></span></td>
  <td><span data-ttu-id="44fc0-1236">PasswordKeyShow</span><span class="sxs-lookup"><span data-stu-id="44fc0-1236">PasswordKeyShow</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E9A9.png" width="32" height="32" alt="PasswordKeyHide" /></td>
  <td><span data-ttu-id="44fc0-1237">E9A9</span><span class="sxs-lookup"><span data-stu-id="44fc0-1237">E9A9</span></span></td>
  <td><span data-ttu-id="44fc0-1238">PasswordKeyHide</span><span class="sxs-lookup"><span data-stu-id="44fc0-1238">PasswordKeyHide</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E9AA.png" width="32" height="32" alt="BidiLtr" /></td>
  <td><span data-ttu-id="44fc0-1239">E9AA</span><span class="sxs-lookup"><span data-stu-id="44fc0-1239">E9AA</span></span></td>
  <td><span data-ttu-id="44fc0-1240">BidiLtr</span><span class="sxs-lookup"><span data-stu-id="44fc0-1240">BidiLtr</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E9AB.png" width="32" height="32" alt="BidiRtl" /></td>
  <td><span data-ttu-id="44fc0-1241">E9AB</span><span class="sxs-lookup"><span data-stu-id="44fc0-1241">E9AB</span></span></td>
  <td><span data-ttu-id="44fc0-1242">BidiRtl</span><span class="sxs-lookup"><span data-stu-id="44fc0-1242">BidiRtl</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E9AC.png" width="32" height="32" alt="ForwardSm" /></td>
  <td><span data-ttu-id="44fc0-1243">E9AC</span><span class="sxs-lookup"><span data-stu-id="44fc0-1243">E9AC</span></span></td>
  <td><span data-ttu-id="44fc0-1244">ForwardSm</span><span class="sxs-lookup"><span data-stu-id="44fc0-1244">ForwardSm</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E9AD.png" width="32" height="32" alt="CommaKey" /></td>
  <td><span data-ttu-id="44fc0-1245">E9AD</span><span class="sxs-lookup"><span data-stu-id="44fc0-1245">E9AD</span></span></td>
  <td><span data-ttu-id="44fc0-1246">CommaKey</span><span class="sxs-lookup"><span data-stu-id="44fc0-1246">CommaKey</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E9AE.png" width="32" height="32" alt="DashKey" /></td>
  <td><span data-ttu-id="44fc0-1247">E9AE</span><span class="sxs-lookup"><span data-stu-id="44fc0-1247">E9AE</span></span></td>
  <td><span data-ttu-id="44fc0-1248">DashKey</span><span class="sxs-lookup"><span data-stu-id="44fc0-1248">DashKey</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E9AF.png" width="32" height="32" alt="DullSoundKey" /></td>
  <td><span data-ttu-id="44fc0-1249">E9AF</span><span class="sxs-lookup"><span data-stu-id="44fc0-1249">E9AF</span></span></td>
  <td><span data-ttu-id="44fc0-1250">DullSoundKey</span><span class="sxs-lookup"><span data-stu-id="44fc0-1250">DullSoundKey</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E9B0.png" width="32" height="32" alt="HalfDullSound" /></td>
  <td><span data-ttu-id="44fc0-1251">E9B0</span><span class="sxs-lookup"><span data-stu-id="44fc0-1251">E9B0</span></span></td>
  <td><span data-ttu-id="44fc0-1252">HalfDullSound</span><span class="sxs-lookup"><span data-stu-id="44fc0-1252">HalfDullSound</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E9B1.png" width="32" height="32" alt="RightDoubleQuote" /></td>
  <td><span data-ttu-id="44fc0-1253">E9B1</span><span class="sxs-lookup"><span data-stu-id="44fc0-1253">E9B1</span></span></td>
  <td><span data-ttu-id="44fc0-1254">RightDoubleQuote</span><span class="sxs-lookup"><span data-stu-id="44fc0-1254">RightDoubleQuote</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E9B2.png" width="32" height="32" alt="LeftDoubleQuote" /></td>
  <td><span data-ttu-id="44fc0-1255">E9B2</span><span class="sxs-lookup"><span data-stu-id="44fc0-1255">E9B2</span></span></td>
  <td><span data-ttu-id="44fc0-1256">LeftDoubleQuote</span><span class="sxs-lookup"><span data-stu-id="44fc0-1256">LeftDoubleQuote</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E9B3.png" width="32" height="32" alt="PuncKeyRightBottom" /></td>
  <td><span data-ttu-id="44fc0-1257">E9B3</span><span class="sxs-lookup"><span data-stu-id="44fc0-1257">E9B3</span></span></td>
  <td><span data-ttu-id="44fc0-1258">PuncKeyRightBottom</span><span class="sxs-lookup"><span data-stu-id="44fc0-1258">PuncKeyRightBottom</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E9B4.png" width="32" height="32" alt="PuncKey1" /></td>
  <td><span data-ttu-id="44fc0-1259">E9B4</span><span class="sxs-lookup"><span data-stu-id="44fc0-1259">E9B4</span></span></td>
  <td><span data-ttu-id="44fc0-1260">PuncKey1</span><span class="sxs-lookup"><span data-stu-id="44fc0-1260">PuncKey1</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E9B5.png" width="32" height="32" alt="PuncKey2" /></td>
  <td><span data-ttu-id="44fc0-1261">E9B5</span><span class="sxs-lookup"><span data-stu-id="44fc0-1261">E9B5</span></span></td>
  <td><span data-ttu-id="44fc0-1262">PuncKey2</span><span class="sxs-lookup"><span data-stu-id="44fc0-1262">PuncKey2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E9B6.png" width="32" height="32" alt="PuncKey3" /></td>
  <td><span data-ttu-id="44fc0-1263">E9B6</span><span class="sxs-lookup"><span data-stu-id="44fc0-1263">E9B6</span></span></td>
  <td><span data-ttu-id="44fc0-1264">PuncKey3</span><span class="sxs-lookup"><span data-stu-id="44fc0-1264">PuncKey3</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E9B7.png" width="32" height="32" alt="PuncKey4" /></td>
  <td><span data-ttu-id="44fc0-1265">E9B7</span><span class="sxs-lookup"><span data-stu-id="44fc0-1265">E9B7</span></span></td>
  <td><span data-ttu-id="44fc0-1266">PuncKey4</span><span class="sxs-lookup"><span data-stu-id="44fc0-1266">PuncKey4</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E9B8.png" width="32" height="32" alt="PuncKey5" /></td>
  <td><span data-ttu-id="44fc0-1267">E9B8</span><span class="sxs-lookup"><span data-stu-id="44fc0-1267">E9B8</span></span></td>
  <td><span data-ttu-id="44fc0-1268">PuncKey5</span><span class="sxs-lookup"><span data-stu-id="44fc0-1268">PuncKey5</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E9B9.png" width="32" height="32" alt="PuncKey6" /></td>
  <td><span data-ttu-id="44fc0-1269">E9B9</span><span class="sxs-lookup"><span data-stu-id="44fc0-1269">E9B9</span></span></td>
  <td><span data-ttu-id="44fc0-1270">PuncKey6</span><span class="sxs-lookup"><span data-stu-id="44fc0-1270">PuncKey6</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E9BA.png" width="32" height="32" alt="PuncKey9" /></td>
  <td><span data-ttu-id="44fc0-1271">E9BA</span><span class="sxs-lookup"><span data-stu-id="44fc0-1271">E9BA</span></span></td>
  <td><span data-ttu-id="44fc0-1272">PuncKey9</span><span class="sxs-lookup"><span data-stu-id="44fc0-1272">PuncKey9</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E9BB.png" width="32" height="32" alt="PuncKey7" /></td>
  <td><span data-ttu-id="44fc0-1273">E9BB</span><span class="sxs-lookup"><span data-stu-id="44fc0-1273">E9BB</span></span></td>
  <td><span data-ttu-id="44fc0-1274">PuncKey7</span><span class="sxs-lookup"><span data-stu-id="44fc0-1274">PuncKey7</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E9BC.png" width="32" height="32" alt="PuncKey8" /></td>
  <td><span data-ttu-id="44fc0-1275">E9BC</span><span class="sxs-lookup"><span data-stu-id="44fc0-1275">E9BC</span></span></td>
  <td><span data-ttu-id="44fc0-1276">PuncKey8</span><span class="sxs-lookup"><span data-stu-id="44fc0-1276">PuncKey8</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E9CA.png" width="32" height="32" alt="Frigid" /></td>
  <td><span data-ttu-id="44fc0-1277">E9CA</span><span class="sxs-lookup"><span data-stu-id="44fc0-1277">E9CA</span></span></td>
  <td><span data-ttu-id="44fc0-1278">Frigid</span><span class="sxs-lookup"><span data-stu-id="44fc0-1278">Frigid</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E9CE.png" width="32" height="32" alt="Unknown" /></td>
  <td><span data-ttu-id="44fc0-1279">E9CE</span><span class="sxs-lookup"><span data-stu-id="44fc0-1279">E9CE</span></span></td>
  <td><span data-ttu-id="44fc0-1280">Unknown</span><span class="sxs-lookup"><span data-stu-id="44fc0-1280">Unknown</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E9D2.png" width="32" height="32" alt="AreaChart" /></td>
  <td><span data-ttu-id="44fc0-1281">E9D2</span><span class="sxs-lookup"><span data-stu-id="44fc0-1281">E9D2</span></span></td>
  <td><span data-ttu-id="44fc0-1282">AreaChart</span><span class="sxs-lookup"><span data-stu-id="44fc0-1282">AreaChart</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E9D5.png" width="32" height="32" alt="CheckList" /></td>
  <td><span data-ttu-id="44fc0-1283">E9D5</span><span class="sxs-lookup"><span data-stu-id="44fc0-1283">E9D5</span></span></td>
  <td><span data-ttu-id="44fc0-1284">Prüfliste</span><span class="sxs-lookup"><span data-stu-id="44fc0-1284">CheckList</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E9D9.png" width="32" height="32" alt="Diagnostic" /></td>
  <td><span data-ttu-id="44fc0-1285">E9D9</span><span class="sxs-lookup"><span data-stu-id="44fc0-1285">E9D9</span></span></td>
  <td><span data-ttu-id="44fc0-1286">Diagnostic</span><span class="sxs-lookup"><span data-stu-id="44fc0-1286">Diagnostic</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E9E9.png" width="32" height="32" alt="Equalizer" /></td>
  <td><span data-ttu-id="44fc0-1287">E9E9</span><span class="sxs-lookup"><span data-stu-id="44fc0-1287">E9E9</span></span></td>
  <td><span data-ttu-id="44fc0-1288">Equalizer</span><span class="sxs-lookup"><span data-stu-id="44fc0-1288">Equalizer</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E9F3.png" width="32" height="32" alt="Process" /></td>
  <td><span data-ttu-id="44fc0-1289">E9F3</span><span class="sxs-lookup"><span data-stu-id="44fc0-1289">E9F3</span></span></td>
  <td><span data-ttu-id="44fc0-1290">Verarbeiten</span><span class="sxs-lookup"><span data-stu-id="44fc0-1290">Process</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E9F5.png" width="32" height="32" alt="Processing" /></td>
  <td><span data-ttu-id="44fc0-1291">E9F5</span><span class="sxs-lookup"><span data-stu-id="44fc0-1291">E9F5</span></span></td>
  <td><span data-ttu-id="44fc0-1292">Verarbeitung</span><span class="sxs-lookup"><span data-stu-id="44fc0-1292">Processing</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/E9F9.png" width="32" height="32" alt="ReportDocument" /></td>
  <td><span data-ttu-id="44fc0-1293">E9F9</span><span class="sxs-lookup"><span data-stu-id="44fc0-1293">E9F9</span></span></td>
  <td><span data-ttu-id="44fc0-1294">ReportDocument</span><span class="sxs-lookup"><span data-stu-id="44fc0-1294">ReportDocument</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA0C.png" width="32" height="32" alt="VideoSolid" /></td>
  <td><span data-ttu-id="44fc0-1295">EA0C</span><span class="sxs-lookup"><span data-stu-id="44fc0-1295">EA0C</span></span></td>
  <td><span data-ttu-id="44fc0-1296">VideoSolid</span><span class="sxs-lookup"><span data-stu-id="44fc0-1296">VideoSolid</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA14.png" width="32" height="32" alt="DisconnectDisplay" /></td>
  <td><span data-ttu-id="44fc0-1297">EA14</span><span class="sxs-lookup"><span data-stu-id="44fc0-1297">EA14</span></span></td>
  <td><span data-ttu-id="44fc0-1298">DisconnectDisplay</span><span class="sxs-lookup"><span data-stu-id="44fc0-1298">DisconnectDisplay</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA18.png" width="32" height="32" alt="Shield" /></td>
  <td><span data-ttu-id="44fc0-1299">EA18</span><span class="sxs-lookup"><span data-stu-id="44fc0-1299">EA18</span></span></td>
  <td><span data-ttu-id="44fc0-1300">Schildsymbol</span><span class="sxs-lookup"><span data-stu-id="44fc0-1300">Shield</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA1F.png" width="32" height="32" alt="Info2" /></td>
  <td><span data-ttu-id="44fc0-1301">EA1F</span><span class="sxs-lookup"><span data-stu-id="44fc0-1301">EA1F</span></span></td>
  <td><span data-ttu-id="44fc0-1302">Info2</span><span class="sxs-lookup"><span data-stu-id="44fc0-1302">Info2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA21.png" width="32" height="32" alt="ActionCenterAsterisk" /></td>
  <td><span data-ttu-id="44fc0-1303">EA21</span><span class="sxs-lookup"><span data-stu-id="44fc0-1303">EA21</span></span></td>
  <td><span data-ttu-id="44fc0-1304">ActionCenterAsterisk</span><span class="sxs-lookup"><span data-stu-id="44fc0-1304">ActionCenterAsterisk</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA24.png" width="32" height="32" alt="Beta" /></td>
  <td><span data-ttu-id="44fc0-1305">EA24</span><span class="sxs-lookup"><span data-stu-id="44fc0-1305">EA24</span></span></td>
  <td><span data-ttu-id="44fc0-1306">Beta</span><span class="sxs-lookup"><span data-stu-id="44fc0-1306">Beta</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA35.png" width="32" height="32" alt="SaveCopy" /></td>
  <td><span data-ttu-id="44fc0-1307">EA35</span><span class="sxs-lookup"><span data-stu-id="44fc0-1307">EA35</span></span></td>
  <td><span data-ttu-id="44fc0-1308">SaveCopy</span><span class="sxs-lookup"><span data-stu-id="44fc0-1308">SaveCopy</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA37.png" width="32" height="32" alt="List" /></td>
  <td><span data-ttu-id="44fc0-1309">EA37</span><span class="sxs-lookup"><span data-stu-id="44fc0-1309">EA37</span></span></td>
  <td><span data-ttu-id="44fc0-1310">Liste</span><span class="sxs-lookup"><span data-stu-id="44fc0-1310">List</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA38.png" width="32" height="32" alt="Asterisk" /></td>
  <td><span data-ttu-id="44fc0-1311">EA38</span><span class="sxs-lookup"><span data-stu-id="44fc0-1311">EA38</span></span></td>
  <td><span data-ttu-id="44fc0-1312">Asterisk</span><span class="sxs-lookup"><span data-stu-id="44fc0-1312">Asterisk</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA39.png" width="32" height="32" alt="ErrorBadge" /></td>
  <td><span data-ttu-id="44fc0-1313">EA39</span><span class="sxs-lookup"><span data-stu-id="44fc0-1313">EA39</span></span></td>
  <td><span data-ttu-id="44fc0-1314">ErrorBadge</span><span class="sxs-lookup"><span data-stu-id="44fc0-1314">ErrorBadge</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA3A.png" width="32" height="32" alt="CircleRing" /></td>
  <td><span data-ttu-id="44fc0-1315">EA3A</span><span class="sxs-lookup"><span data-stu-id="44fc0-1315">EA3A</span></span></td>
  <td><span data-ttu-id="44fc0-1316">CircleRing</span><span class="sxs-lookup"><span data-stu-id="44fc0-1316">CircleRing</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA3B.png" width="32" height="32" alt="CircleFill" /></td>
  <td><span data-ttu-id="44fc0-1317">EA3B</span><span class="sxs-lookup"><span data-stu-id="44fc0-1317">EA3B</span></span></td>
  <td><span data-ttu-id="44fc0-1318">CircleFill</span><span class="sxs-lookup"><span data-stu-id="44fc0-1318">CircleFill</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA40.png" width="32" height="32" alt="AllAppsMirrored" /></td>
  <td><span data-ttu-id="44fc0-1319">EA40</span><span class="sxs-lookup"><span data-stu-id="44fc0-1319">EA40</span></span></td>
  <td><span data-ttu-id="44fc0-1320">AllAppsMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1320">AllAppsMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA41.png" width="32" height="32" alt="BookmarksMirrored" /></td>
  <td><span data-ttu-id="44fc0-1321">EA41</span><span class="sxs-lookup"><span data-stu-id="44fc0-1321">EA41</span></span></td>
  <td><span data-ttu-id="44fc0-1322">BookmarksMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1322">BookmarksMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA42.png" width="32" height="32" alt="BulletedListMirrored" /></td>
  <td><span data-ttu-id="44fc0-1323">EA42</span><span class="sxs-lookup"><span data-stu-id="44fc0-1323">EA42</span></span></td>
  <td><span data-ttu-id="44fc0-1324">BulletedListMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1324">BulletedListMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA43.png" width="32" height="32" alt="CallForwardInternationalMirrored" /></td>
  <td><span data-ttu-id="44fc0-1325">EA43</span><span class="sxs-lookup"><span data-stu-id="44fc0-1325">EA43</span></span></td>
  <td><span data-ttu-id="44fc0-1326">CallForwardInternationalMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1326">CallForwardInternationalMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA44.png" width="32" height="32" alt="CallForwardRoamingMirrored" /></td>
  <td><span data-ttu-id="44fc0-1327">EA44</span><span class="sxs-lookup"><span data-stu-id="44fc0-1327">EA44</span></span></td>
  <td><span data-ttu-id="44fc0-1328">CallForwardRoamingMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1328">CallForwardRoamingMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA47.png" width="32" height="32" alt="ChromeBackMirrored" /></td>
  <td><span data-ttu-id="44fc0-1329">EA47</span><span class="sxs-lookup"><span data-stu-id="44fc0-1329">EA47</span></span></td>
  <td><span data-ttu-id="44fc0-1330">ChromeBackMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1330">ChromeBackMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA48.png" width="32" height="32" alt="ClearSelectionMirrored" /></td>
  <td><span data-ttu-id="44fc0-1331">EA48</span><span class="sxs-lookup"><span data-stu-id="44fc0-1331">EA48</span></span></td>
  <td><span data-ttu-id="44fc0-1332">ClearSelectionMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1332">ClearSelectionMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA49.png" width="32" height="32" alt="ClosePaneMirrored" /></td>
  <td><span data-ttu-id="44fc0-1333">EA49</span><span class="sxs-lookup"><span data-stu-id="44fc0-1333">EA49</span></span></td>
  <td><span data-ttu-id="44fc0-1334">ClosePaneMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1334">ClosePaneMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA4A.png" width="32" height="32" alt="ContactInfoMirrored" /></td>
  <td><span data-ttu-id="44fc0-1335">EA4A</span><span class="sxs-lookup"><span data-stu-id="44fc0-1335">EA4A</span></span></td>
  <td><span data-ttu-id="44fc0-1336">ContactInfoMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1336">ContactInfoMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA4B.png" width="32" height="32" alt="DockRightMirrored" /></td>
  <td><span data-ttu-id="44fc0-1337">EA4B</span><span class="sxs-lookup"><span data-stu-id="44fc0-1337">EA4B</span></span></td>
  <td><span data-ttu-id="44fc0-1338">DockRightMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1338">DockRightMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA4C.png" width="32" height="32" alt="DockLeftMirrored" /></td>
  <td><span data-ttu-id="44fc0-1339">EA4C</span><span class="sxs-lookup"><span data-stu-id="44fc0-1339">EA4C</span></span></td>
  <td><span data-ttu-id="44fc0-1340">DockLeftMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1340">DockLeftMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA4E.png" width="32" height="32" alt="ExpandTileMirrored" /></td>
  <td><span data-ttu-id="44fc0-1341">EA4E</span><span class="sxs-lookup"><span data-stu-id="44fc0-1341">EA4E</span></span></td>
  <td><span data-ttu-id="44fc0-1342">ExpandTileMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1342">ExpandTileMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA4F.png" width="32" height="32" alt="GoMirrored" /></td>
  <td><span data-ttu-id="44fc0-1343">EA4F</span><span class="sxs-lookup"><span data-stu-id="44fc0-1343">EA4F</span></span></td>
  <td><span data-ttu-id="44fc0-1344">GoMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1344">GoMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA50.png" width="32" height="32" alt="GripperResizeMirrored" /></td>
  <td><span data-ttu-id="44fc0-1345">EA50</span><span class="sxs-lookup"><span data-stu-id="44fc0-1345">EA50</span></span></td>
  <td><span data-ttu-id="44fc0-1346">GripperResizeMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1346">GripperResizeMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA51.png" width="32" height="32" alt="HelpMirrored" /></td>
  <td><span data-ttu-id="44fc0-1347">EA51</span><span class="sxs-lookup"><span data-stu-id="44fc0-1347">EA51</span></span></td>
  <td><span data-ttu-id="44fc0-1348">HelpMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1348">HelpMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA52.png" width="32" height="32" alt="ImportMirrored" /></td>
  <td><span data-ttu-id="44fc0-1349">EA52</span><span class="sxs-lookup"><span data-stu-id="44fc0-1349">EA52</span></span></td>
  <td><span data-ttu-id="44fc0-1350">ImportMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1350">ImportMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA53.png" width="32" height="32" alt="ImportAllMirrored" /></td>
  <td><span data-ttu-id="44fc0-1351">EA53</span><span class="sxs-lookup"><span data-stu-id="44fc0-1351">EA53</span></span></td>
  <td><span data-ttu-id="44fc0-1352">ImportAllMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1352">ImportAllMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA54.png" width="32" height="32" alt="LeaveChatMirrored" /></td>
  <td><span data-ttu-id="44fc0-1353">EA54</span><span class="sxs-lookup"><span data-stu-id="44fc0-1353">EA54</span></span></td>
  <td><span data-ttu-id="44fc0-1354">LeaveChatMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1354">LeaveChatMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA55.png" width="32" height="32" alt="ListMirrored" /></td>
  <td><span data-ttu-id="44fc0-1355">EA55</span><span class="sxs-lookup"><span data-stu-id="44fc0-1355">EA55</span></span></td>
  <td><span data-ttu-id="44fc0-1356">ListMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1356">ListMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA56.png" width="32" height="32" alt="MailForwardMirrored" /></td>
  <td><span data-ttu-id="44fc0-1357">EA56</span><span class="sxs-lookup"><span data-stu-id="44fc0-1357">EA56</span></span></td>
  <td><span data-ttu-id="44fc0-1358">MailForwardMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1358">MailForwardMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA57.png" width="32" height="32" alt="MailReplyMirrored" /></td>
  <td><span data-ttu-id="44fc0-1359">EA57</span><span class="sxs-lookup"><span data-stu-id="44fc0-1359">EA57</span></span></td>
  <td><span data-ttu-id="44fc0-1360">MailReplyMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1360">MailReplyMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA58.png" width="32" height="32" alt="MailReplyAllMirrored" /></td>
  <td><span data-ttu-id="44fc0-1361">EA58</span><span class="sxs-lookup"><span data-stu-id="44fc0-1361">EA58</span></span></td>
  <td><span data-ttu-id="44fc0-1362">MailReplyAllMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1362">MailReplyAllMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA5B.png" width="32" height="32" alt="OpenPaneMirrored" /></td>
  <td><span data-ttu-id="44fc0-1363">EA5B</span><span class="sxs-lookup"><span data-stu-id="44fc0-1363">EA5B</span></span></td>
  <td><span data-ttu-id="44fc0-1364">OpenPaneMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1364">OpenPaneMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA5C.png" width="32" height="32" alt="OpenWithMirrored" /></td>
  <td><span data-ttu-id="44fc0-1365">EA5C</span><span class="sxs-lookup"><span data-stu-id="44fc0-1365">EA5C</span></span></td>
  <td><span data-ttu-id="44fc0-1366">OpenWithMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1366">OpenWithMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA5E.png" width="32" height="32" alt="ParkingLocationMirrored" /></td>
  <td><span data-ttu-id="44fc0-1367">EA5E</span><span class="sxs-lookup"><span data-stu-id="44fc0-1367">EA5E</span></span></td>
  <td><span data-ttu-id="44fc0-1368">ParkingLocationMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1368">ParkingLocationMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA5F.png" width="32" height="32" alt="ResizeMouseMediumMirrored" /></td>
  <td><span data-ttu-id="44fc0-1369">EA5F</span><span class="sxs-lookup"><span data-stu-id="44fc0-1369">EA5F</span></span></td>
  <td><span data-ttu-id="44fc0-1370">ResizeMouseMediumMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1370">ResizeMouseMediumMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA60.png" width="32" height="32" alt="ResizeMouseSmallMirrored" /></td>
  <td><span data-ttu-id="44fc0-1371">EA60</span><span class="sxs-lookup"><span data-stu-id="44fc0-1371">EA60</span></span></td>
  <td><span data-ttu-id="44fc0-1372">ResizeMouseSmallMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1372">ResizeMouseSmallMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA61.png" width="32" height="32" alt="ResizeMouseTallMirrored" /></td>
  <td><span data-ttu-id="44fc0-1373">EA61</span><span class="sxs-lookup"><span data-stu-id="44fc0-1373">EA61</span></span></td>
  <td><span data-ttu-id="44fc0-1374">ResizeMouseTallMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1374">ResizeMouseTallMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA62.png" width="32" height="32" alt="ResizeTouchNarrowerMirrored" /></td>
  <td><span data-ttu-id="44fc0-1375">EA62</span><span class="sxs-lookup"><span data-stu-id="44fc0-1375">EA62</span></span></td>
  <td><span data-ttu-id="44fc0-1376">ResizeTouchNarrowerMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1376">ResizeTouchNarrowerMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA63.png" width="32" height="32" alt="SendMirrored" /></td>
  <td><span data-ttu-id="44fc0-1377">EA63</span><span class="sxs-lookup"><span data-stu-id="44fc0-1377">EA63</span></span></td>
  <td><span data-ttu-id="44fc0-1378">SendMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1378">SendMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA64.png" width="32" height="32" alt="SendFillMirrored" /></td>
  <td><span data-ttu-id="44fc0-1379">EA64</span><span class="sxs-lookup"><span data-stu-id="44fc0-1379">EA64</span></span></td>
  <td><span data-ttu-id="44fc0-1380">SendFillMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1380">SendFillMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA65.png" width="32" height="32" alt="ShowResultsMirrored" /></td>
  <td><span data-ttu-id="44fc0-1381">EA65</span><span class="sxs-lookup"><span data-stu-id="44fc0-1381">EA65</span></span></td>
  <td><span data-ttu-id="44fc0-1382">ShowResultsMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1382">ShowResultsMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA69.png" width="32" height="32" alt="Media" /></td>
  <td><span data-ttu-id="44fc0-1383">EA69</span><span class="sxs-lookup"><span data-stu-id="44fc0-1383">EA69</span></span></td>
  <td><span data-ttu-id="44fc0-1384">Medien</span><span class="sxs-lookup"><span data-stu-id="44fc0-1384">Media</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA6A.png" width="32" height="32" alt="SyncError" /></td>
  <td><span data-ttu-id="44fc0-1385">EA6A</span><span class="sxs-lookup"><span data-stu-id="44fc0-1385">EA6A</span></span></td>
  <td><span data-ttu-id="44fc0-1386">SyncError</span><span class="sxs-lookup"><span data-stu-id="44fc0-1386">SyncError</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA6C.png" width="32" height="32" alt="Devices3" /></td>
  <td><span data-ttu-id="44fc0-1387">EA6C</span><span class="sxs-lookup"><span data-stu-id="44fc0-1387">EA6C</span></span></td>
  <td><span data-ttu-id="44fc0-1388">Devices3</span><span class="sxs-lookup"><span data-stu-id="44fc0-1388">Devices3</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA79.png" width="32" height="32" alt="SlowMotionOn" /></td>
  <td><span data-ttu-id="44fc0-1389">EA79</span><span class="sxs-lookup"><span data-stu-id="44fc0-1389">EA79</span></span></td>
  <td><span data-ttu-id="44fc0-1390">SlowMotionOn</span><span class="sxs-lookup"><span data-stu-id="44fc0-1390">SlowMotionOn</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA80.png" width="32" height="32" alt="Lightbulb" /></td>
  <td><span data-ttu-id="44fc0-1391">EA80</span><span class="sxs-lookup"><span data-stu-id="44fc0-1391">EA80</span></span></td>
  <td><span data-ttu-id="44fc0-1392">Lightbulb</span><span class="sxs-lookup"><span data-stu-id="44fc0-1392">Lightbulb</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA81.png" width="32" height="32" alt="StatusCircle" /></td>
  <td><span data-ttu-id="44fc0-1393">EA81</span><span class="sxs-lookup"><span data-stu-id="44fc0-1393">EA81</span></span></td>
  <td><span data-ttu-id="44fc0-1394">StatusCircle</span><span class="sxs-lookup"><span data-stu-id="44fc0-1394">StatusCircle</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA82.png" width="32" height="32" alt="StatusTriangle" /></td>
  <td><span data-ttu-id="44fc0-1395">EA82</span><span class="sxs-lookup"><span data-stu-id="44fc0-1395">EA82</span></span></td>
  <td><span data-ttu-id="44fc0-1396">StatusTriangle</span><span class="sxs-lookup"><span data-stu-id="44fc0-1396">StatusTriangle</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA83.png" width="32" height="32" alt="StatusError" /></td>
  <td><span data-ttu-id="44fc0-1397">EA83</span><span class="sxs-lookup"><span data-stu-id="44fc0-1397">EA83</span></span></td>
  <td><span data-ttu-id="44fc0-1398">StatusError</span><span class="sxs-lookup"><span data-stu-id="44fc0-1398">StatusError</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA84.png" width="32" height="32" alt="StatusWarning" /></td>
  <td><span data-ttu-id="44fc0-1399">EA84</span><span class="sxs-lookup"><span data-stu-id="44fc0-1399">EA84</span></span></td>
  <td><span data-ttu-id="44fc0-1400">StatusWarning</span><span class="sxs-lookup"><span data-stu-id="44fc0-1400">StatusWarning</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA86.png" width="32" height="32" alt="Puzzle" /></td>
  <td><span data-ttu-id="44fc0-1401">EA86</span><span class="sxs-lookup"><span data-stu-id="44fc0-1401">EA86</span></span></td>
  <td><span data-ttu-id="44fc0-1402">Puzzle</span><span class="sxs-lookup"><span data-stu-id="44fc0-1402">Puzzle</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA89.png" width="32" height="32" alt="CalendarSolid" /></td>
  <td><span data-ttu-id="44fc0-1403">EA89</span><span class="sxs-lookup"><span data-stu-id="44fc0-1403">EA89</span></span></td>
  <td><span data-ttu-id="44fc0-1404">CalendarSolid</span><span class="sxs-lookup"><span data-stu-id="44fc0-1404">CalendarSolid</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA8A.png" width="32" height="32" alt="HomeSolid" /></td>
  <td><span data-ttu-id="44fc0-1405">EA8A</span><span class="sxs-lookup"><span data-stu-id="44fc0-1405">EA8A</span></span></td>
  <td><span data-ttu-id="44fc0-1406">HomeSolid</span><span class="sxs-lookup"><span data-stu-id="44fc0-1406">HomeSolid</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA8B.png" width="32" height="32" alt="ParkingLocationSolid" /></td>
  <td><span data-ttu-id="44fc0-1407">EA8B</span><span class="sxs-lookup"><span data-stu-id="44fc0-1407">EA8B</span></span></td>
  <td><span data-ttu-id="44fc0-1408">ParkingLocationSolid</span><span class="sxs-lookup"><span data-stu-id="44fc0-1408">ParkingLocationSolid</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA8C.png" width="32" height="32" alt="ContactSolid" /></td>
  <td><span data-ttu-id="44fc0-1409">EA8C</span><span class="sxs-lookup"><span data-stu-id="44fc0-1409">EA8C</span></span></td>
  <td><span data-ttu-id="44fc0-1410">ContactSolid</span><span class="sxs-lookup"><span data-stu-id="44fc0-1410">ContactSolid</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA8D.png" width="32" height="32" alt="ConstructionSolid" /></td>
  <td><span data-ttu-id="44fc0-1411">EA8D</span><span class="sxs-lookup"><span data-stu-id="44fc0-1411">EA8D</span></span></td>
  <td><span data-ttu-id="44fc0-1412">ConstructionSolid</span><span class="sxs-lookup"><span data-stu-id="44fc0-1412">ConstructionSolid</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA8E.png" width="32" height="32" alt="AccidentSolid" /></td>
  <td><span data-ttu-id="44fc0-1413">EA8E</span><span class="sxs-lookup"><span data-stu-id="44fc0-1413">EA8E</span></span></td>
  <td><span data-ttu-id="44fc0-1414">AccidentSolid</span><span class="sxs-lookup"><span data-stu-id="44fc0-1414">AccidentSolid</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA8F.png" width="32" height="32" alt="Ringer" /></td>
  <td><span data-ttu-id="44fc0-1415">EA8F</span><span class="sxs-lookup"><span data-stu-id="44fc0-1415">EA8F</span></span></td>
  <td><span data-ttu-id="44fc0-1416">Ringer</span><span class="sxs-lookup"><span data-stu-id="44fc0-1416">Ringer</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA91.png" width="32" height="32" alt="ThoughtBubble" /></td>
  <td><span data-ttu-id="44fc0-1417">EA91</span><span class="sxs-lookup"><span data-stu-id="44fc0-1417">EA91</span></span></td>
  <td><span data-ttu-id="44fc0-1418">ThoughtBubble</span><span class="sxs-lookup"><span data-stu-id="44fc0-1418">ThoughtBubble</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA92.png" width="32" height="32" alt="HeartBroken" /></td>
  <td><span data-ttu-id="44fc0-1419">EA92</span><span class="sxs-lookup"><span data-stu-id="44fc0-1419">EA92</span></span></td>
  <td><span data-ttu-id="44fc0-1420">HeartBroken</span><span class="sxs-lookup"><span data-stu-id="44fc0-1420">HeartBroken</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA93.png" width="32" height="32" alt="BatteryCharging10" /></td>
  <td><span data-ttu-id="44fc0-1421">EA93</span><span class="sxs-lookup"><span data-stu-id="44fc0-1421">EA93</span></span></td>
  <td><span data-ttu-id="44fc0-1422">BatteryCharging10</span><span class="sxs-lookup"><span data-stu-id="44fc0-1422">BatteryCharging10</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA94.png" width="32" height="32" alt="BatterySaver9" /></td>
  <td><span data-ttu-id="44fc0-1423">EA94</span><span class="sxs-lookup"><span data-stu-id="44fc0-1423">EA94</span></span></td>
  <td><span data-ttu-id="44fc0-1424">BatterySaver9</span><span class="sxs-lookup"><span data-stu-id="44fc0-1424">BatterySaver9</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA95.png" width="32" height="32" alt="BatterySaver10" /></td>
  <td><span data-ttu-id="44fc0-1425">EA95</span><span class="sxs-lookup"><span data-stu-id="44fc0-1425">EA95</span></span></td>
  <td><span data-ttu-id="44fc0-1426">BatterySaver10</span><span class="sxs-lookup"><span data-stu-id="44fc0-1426">BatterySaver10</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA97.png" width="32" height="32" alt="CallForwardingMirrored" /></td>
  <td><span data-ttu-id="44fc0-1427">EA97</span><span class="sxs-lookup"><span data-stu-id="44fc0-1427">EA97</span></span></td>
  <td><span data-ttu-id="44fc0-1428">CallForwardingMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1428">CallForwardingMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA98.png" width="32" height="32" alt="MultiSelectMirrored" /></td>
  <td><span data-ttu-id="44fc0-1429">EA98</span><span class="sxs-lookup"><span data-stu-id="44fc0-1429">EA98</span></span></td>
  <td><span data-ttu-id="44fc0-1430">MultiSelectMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1430">MultiSelectMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EA99.png" width="32" height="32" alt="Broom" /></td>
  <td><span data-ttu-id="44fc0-1431">EA99</span><span class="sxs-lookup"><span data-stu-id="44fc0-1431">EA99</span></span></td>
  <td><span data-ttu-id="44fc0-1432">Broom</span><span class="sxs-lookup"><span data-stu-id="44fc0-1432">Broom</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EADF.png" width="32" height="32" alt="Trackers" /></td>
  <td><span data-ttu-id="44fc0-1433">EADF</span><span class="sxs-lookup"><span data-stu-id="44fc0-1433">EADF</span></span></td>
  <td><span data-ttu-id="44fc0-1434">Trackers</span><span class="sxs-lookup"><span data-stu-id="44fc0-1434">Trackers</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB05.png" width="32" height="32" alt="PieSingle" /></td>
  <td><span data-ttu-id="44fc0-1435">EB05</span><span class="sxs-lookup"><span data-stu-id="44fc0-1435">EB05</span></span></td>
  <td><span data-ttu-id="44fc0-1436">PieSingle</span><span class="sxs-lookup"><span data-stu-id="44fc0-1436">PieSingle</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB0F.png" width="32" height="32" alt="StockDown" /></td>
  <td><span data-ttu-id="44fc0-1437">EB0F</span><span class="sxs-lookup"><span data-stu-id="44fc0-1437">EB0F</span></span></td>
  <td><span data-ttu-id="44fc0-1438">StockDown</span><span class="sxs-lookup"><span data-stu-id="44fc0-1438">StockDown</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB11.png" width="32" height="32" alt="StockUp" /></td>
  <td><span data-ttu-id="44fc0-1439">EB11</span><span class="sxs-lookup"><span data-stu-id="44fc0-1439">EB11</span></span></td>
  <td><span data-ttu-id="44fc0-1440">StockUp</span><span class="sxs-lookup"><span data-stu-id="44fc0-1440">StockUp</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB3C.png" width="32" height="32" alt="Design" /></td>
  <td><span data-ttu-id="44fc0-1441">EB3C</span><span class="sxs-lookup"><span data-stu-id="44fc0-1441">EB3C</span></span></td>
  <td><span data-ttu-id="44fc0-1442">Entwerfen</span><span class="sxs-lookup"><span data-stu-id="44fc0-1442">Design</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB41.png" width="32" height="32" alt="Website" /></td>
  <td><span data-ttu-id="44fc0-1443">EB41</span><span class="sxs-lookup"><span data-stu-id="44fc0-1443">EB41</span></span></td>
  <td><span data-ttu-id="44fc0-1444">Webseite</span><span class="sxs-lookup"><span data-stu-id="44fc0-1444">Website</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB42.png" width="32" height="32" alt="Drop" /></td>
  <td><span data-ttu-id="44fc0-1445">EB42</span><span class="sxs-lookup"><span data-stu-id="44fc0-1445">EB42</span></span></td>
  <td><span data-ttu-id="44fc0-1446">Drop</span><span class="sxs-lookup"><span data-stu-id="44fc0-1446">Drop</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB44.png" width="32" height="32" alt="Radar" /></td>
  <td><span data-ttu-id="44fc0-1447">EB44</span><span class="sxs-lookup"><span data-stu-id="44fc0-1447">EB44</span></span></td>
  <td><span data-ttu-id="44fc0-1448">Netz</span><span class="sxs-lookup"><span data-stu-id="44fc0-1448">Radar</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB47.png" width="32" height="32" alt="BusSolid" /></td>
  <td><span data-ttu-id="44fc0-1449">EB47</span><span class="sxs-lookup"><span data-stu-id="44fc0-1449">EB47</span></span></td>
  <td><span data-ttu-id="44fc0-1450">BusSolid</span><span class="sxs-lookup"><span data-stu-id="44fc0-1450">BusSolid</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB48.png" width="32" height="32" alt="FerrySolid" /></td>
  <td><span data-ttu-id="44fc0-1451">EB48</span><span class="sxs-lookup"><span data-stu-id="44fc0-1451">EB48</span></span></td>
  <td><span data-ttu-id="44fc0-1452">FerrySolid</span><span class="sxs-lookup"><span data-stu-id="44fc0-1452">FerrySolid</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB49.png" width="32" height="32" alt="StartPointSolid" /></td>
  <td><span data-ttu-id="44fc0-1453">EB49</span><span class="sxs-lookup"><span data-stu-id="44fc0-1453">EB49</span></span></td>
  <td><span data-ttu-id="44fc0-1454">StartPointSolid</span><span class="sxs-lookup"><span data-stu-id="44fc0-1454">StartPointSolid</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB4A.png" width="32" height="32" alt="StopPointSolid" /></td>
  <td><span data-ttu-id="44fc0-1455">EB4A</span><span class="sxs-lookup"><span data-stu-id="44fc0-1455">EB4A</span></span></td>
  <td><span data-ttu-id="44fc0-1456">StopPointSolid</span><span class="sxs-lookup"><span data-stu-id="44fc0-1456">StopPointSolid</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB4B.png" width="32" height="32" alt="EndPointSolid" /></td>
  <td><span data-ttu-id="44fc0-1457">EB4B</span><span class="sxs-lookup"><span data-stu-id="44fc0-1457">EB4B</span></span></td>
  <td><span data-ttu-id="44fc0-1458">EndPointSolid</span><span class="sxs-lookup"><span data-stu-id="44fc0-1458">EndPointSolid</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB4C.png" width="32" height="32" alt="AirplaneSolid" /></td>
  <td><span data-ttu-id="44fc0-1459">EB4C</span><span class="sxs-lookup"><span data-stu-id="44fc0-1459">EB4C</span></span></td>
  <td><span data-ttu-id="44fc0-1460">AirplaneSolid</span><span class="sxs-lookup"><span data-stu-id="44fc0-1460">AirplaneSolid</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB4D.png" width="32" height="32" alt="TrainSolid" /></td>
  <td><span data-ttu-id="44fc0-1461">EB4D</span><span class="sxs-lookup"><span data-stu-id="44fc0-1461">EB4D</span></span></td>
  <td><span data-ttu-id="44fc0-1462">TrainSolid</span><span class="sxs-lookup"><span data-stu-id="44fc0-1462">TrainSolid</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB4E.png" width="32" height="32" alt="WorkSolid" /></td>
  <td><span data-ttu-id="44fc0-1463">EB4E</span><span class="sxs-lookup"><span data-stu-id="44fc0-1463">EB4E</span></span></td>
  <td><span data-ttu-id="44fc0-1464">WorkSolid</span><span class="sxs-lookup"><span data-stu-id="44fc0-1464">WorkSolid</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB4F.png" width="32" height="32" alt="ReminderFill" /></td>
  <td><span data-ttu-id="44fc0-1465">EB4F</span><span class="sxs-lookup"><span data-stu-id="44fc0-1465">EB4F</span></span></td>
  <td><span data-ttu-id="44fc0-1466">ReminderFill</span><span class="sxs-lookup"><span data-stu-id="44fc0-1466">ReminderFill</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB50.png" width="32" height="32" alt="Reminder" /></td>
  <td><span data-ttu-id="44fc0-1467">EB50</span><span class="sxs-lookup"><span data-stu-id="44fc0-1467">EB50</span></span></td>
  <td><span data-ttu-id="44fc0-1468">Erinnerung</span><span class="sxs-lookup"><span data-stu-id="44fc0-1468">Reminder</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB51.png" width="32" height="32" alt="Heart" /></td>
  <td><span data-ttu-id="44fc0-1469">EB51</span><span class="sxs-lookup"><span data-stu-id="44fc0-1469">EB51</span></span></td>
  <td><span data-ttu-id="44fc0-1470">Heart</span><span class="sxs-lookup"><span data-stu-id="44fc0-1470">Heart</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB52.png" width="32" height="32" alt="HeartFill" /></td>
  <td><span data-ttu-id="44fc0-1471">EB52</span><span class="sxs-lookup"><span data-stu-id="44fc0-1471">EB52</span></span></td>
  <td><span data-ttu-id="44fc0-1472">HeartFill</span><span class="sxs-lookup"><span data-stu-id="44fc0-1472">HeartFill</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB55.png" width="32" height="32" alt="EthernetError" /></td>
  <td><span data-ttu-id="44fc0-1473">EB55</span><span class="sxs-lookup"><span data-stu-id="44fc0-1473">EB55</span></span></td>
  <td><span data-ttu-id="44fc0-1474">EthernetError</span><span class="sxs-lookup"><span data-stu-id="44fc0-1474">EthernetError</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB56.png" width="32" height="32" alt="EthernetWarning" /></td>
  <td><span data-ttu-id="44fc0-1475">EB56</span><span class="sxs-lookup"><span data-stu-id="44fc0-1475">EB56</span></span></td>
  <td><span data-ttu-id="44fc0-1476">EthernetWarning</span><span class="sxs-lookup"><span data-stu-id="44fc0-1476">EthernetWarning</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB57.png" width="32" height="32" alt="StatusConnecting1" /></td>
  <td><span data-ttu-id="44fc0-1477">EB57</span><span class="sxs-lookup"><span data-stu-id="44fc0-1477">EB57</span></span></td>
  <td><span data-ttu-id="44fc0-1478">StatusConnecting1</span><span class="sxs-lookup"><span data-stu-id="44fc0-1478">StatusConnecting1</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB58.png" width="32" height="32" alt="StatusConnecting2" /></td>
  <td><span data-ttu-id="44fc0-1479">EB58</span><span class="sxs-lookup"><span data-stu-id="44fc0-1479">EB58</span></span></td>
  <td><span data-ttu-id="44fc0-1480">StatusConnecting2</span><span class="sxs-lookup"><span data-stu-id="44fc0-1480">StatusConnecting2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB59.png" width="32" height="32" alt="StatusUnsecure" /></td>
  <td><span data-ttu-id="44fc0-1481">EB59</span><span class="sxs-lookup"><span data-stu-id="44fc0-1481">EB59</span></span></td>
  <td><span data-ttu-id="44fc0-1482">StatusUnsecure</span><span class="sxs-lookup"><span data-stu-id="44fc0-1482">StatusUnsecure</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB5A.png" width="32" height="32" alt="WifiError0" /></td>
  <td><span data-ttu-id="44fc0-1483">EB5A</span><span class="sxs-lookup"><span data-stu-id="44fc0-1483">EB5A</span></span></td>
  <td><span data-ttu-id="44fc0-1484">WifiError0</span><span class="sxs-lookup"><span data-stu-id="44fc0-1484">WifiError0</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB5B.png" width="32" height="32" alt="WifiError1" /></td>
  <td><span data-ttu-id="44fc0-1485">EB5B</span><span class="sxs-lookup"><span data-stu-id="44fc0-1485">EB5B</span></span></td>
  <td><span data-ttu-id="44fc0-1486">WifiError1</span><span class="sxs-lookup"><span data-stu-id="44fc0-1486">WifiError1</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB5C.png" width="32" height="32" alt="WifiError2" /></td>
  <td><span data-ttu-id="44fc0-1487">EB5C</span><span class="sxs-lookup"><span data-stu-id="44fc0-1487">EB5C</span></span></td>
  <td><span data-ttu-id="44fc0-1488">WifiError2</span><span class="sxs-lookup"><span data-stu-id="44fc0-1488">WifiError2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB5D.png" width="32" height="32" alt="WifiError3" /></td>
  <td><span data-ttu-id="44fc0-1489">EB5D</span><span class="sxs-lookup"><span data-stu-id="44fc0-1489">EB5D</span></span></td>
  <td><span data-ttu-id="44fc0-1490">WifiError3</span><span class="sxs-lookup"><span data-stu-id="44fc0-1490">WifiError3</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB5E.png" width="32" height="32" alt="WifiError4" /></td>
  <td><span data-ttu-id="44fc0-1491">EB5E</span><span class="sxs-lookup"><span data-stu-id="44fc0-1491">EB5E</span></span></td>
  <td><span data-ttu-id="44fc0-1492">WifiError4</span><span class="sxs-lookup"><span data-stu-id="44fc0-1492">WifiError4</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB5F.png" width="32" height="32" alt="WifiWarning0" /></td>
  <td><span data-ttu-id="44fc0-1493">EB5F</span><span class="sxs-lookup"><span data-stu-id="44fc0-1493">EB5F</span></span></td>
  <td><span data-ttu-id="44fc0-1494">WifiWarning0</span><span class="sxs-lookup"><span data-stu-id="44fc0-1494">WifiWarning0</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB60.png" width="32" height="32" alt="WifiWarning1" /></td>
  <td><span data-ttu-id="44fc0-1495">EB60</span><span class="sxs-lookup"><span data-stu-id="44fc0-1495">EB60</span></span></td>
  <td><span data-ttu-id="44fc0-1496">WifiWarning1</span><span class="sxs-lookup"><span data-stu-id="44fc0-1496">WifiWarning1</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB61.png" width="32" height="32" alt="WifiWarning2" /></td>
  <td><span data-ttu-id="44fc0-1497">EB61</span><span class="sxs-lookup"><span data-stu-id="44fc0-1497">EB61</span></span></td>
  <td><span data-ttu-id="44fc0-1498">WifiWarning2</span><span class="sxs-lookup"><span data-stu-id="44fc0-1498">WifiWarning2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB62.png" width="32" height="32" alt="WifiWarning3" /></td>
  <td><span data-ttu-id="44fc0-1499">EB62</span><span class="sxs-lookup"><span data-stu-id="44fc0-1499">EB62</span></span></td>
  <td><span data-ttu-id="44fc0-1500">WifiWarning3</span><span class="sxs-lookup"><span data-stu-id="44fc0-1500">WifiWarning3</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB63.png" width="32" height="32" alt="WifiWarning4" /></td>
  <td><span data-ttu-id="44fc0-1501">EB63</span><span class="sxs-lookup"><span data-stu-id="44fc0-1501">EB63</span></span></td>
  <td><span data-ttu-id="44fc0-1502">WifiWarning4</span><span class="sxs-lookup"><span data-stu-id="44fc0-1502">WifiWarning4</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB66.png" width="32" height="32" alt="Devices4" /></td>
  <td><span data-ttu-id="44fc0-1503">EB66</span><span class="sxs-lookup"><span data-stu-id="44fc0-1503">EB66</span></span></td>
  <td><span data-ttu-id="44fc0-1504">Devices4</span><span class="sxs-lookup"><span data-stu-id="44fc0-1504">Devices4</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB67.png" width="32" height="32" alt="NUIIris" /></td>
  <td><span data-ttu-id="44fc0-1505">EB67</span><span class="sxs-lookup"><span data-stu-id="44fc0-1505">EB67</span></span></td>
  <td><span data-ttu-id="44fc0-1506">NUIIris</span><span class="sxs-lookup"><span data-stu-id="44fc0-1506">NUIIris</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB68.png" width="32" height="32" alt="NUIFace" /></td>
  <td><span data-ttu-id="44fc0-1507">EB68</span><span class="sxs-lookup"><span data-stu-id="44fc0-1507">EB68</span></span></td>
  <td><span data-ttu-id="44fc0-1508">NUIFace</span><span class="sxs-lookup"><span data-stu-id="44fc0-1508">NUIFace</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB7E.png" width="32" height="32" alt="EditMirrored" /></td>
  <td><span data-ttu-id="44fc0-1509">EB7E</span><span class="sxs-lookup"><span data-stu-id="44fc0-1509">EB7E</span></span></td>
  <td><span data-ttu-id="44fc0-1510">EditMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1510">EditMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB82.png" width="32" height="32" alt="NUIFPStartSlideHand " /></td>
  <td><span data-ttu-id="44fc0-1511">EB82</span><span class="sxs-lookup"><span data-stu-id="44fc0-1511">EB82</span></span></td>
  <td><span data-ttu-id="44fc0-1512">NUIFPStartSlideHand</span><span class="sxs-lookup"><span data-stu-id="44fc0-1512">NUIFPStartSlideHand</span></span> </td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB83.png" width="32" height="32" alt="NUIFPStartSlideAction " /></td>
  <td><span data-ttu-id="44fc0-1513">EB83</span><span class="sxs-lookup"><span data-stu-id="44fc0-1513">EB83</span></span></td>
  <td><span data-ttu-id="44fc0-1514">NUIFPStartSlideAction</span><span class="sxs-lookup"><span data-stu-id="44fc0-1514">NUIFPStartSlideAction</span></span> </td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB84.png" width="32" height="32" alt="NUIFPContinueSlideHand " /></td>
  <td><span data-ttu-id="44fc0-1515">EB84</span><span class="sxs-lookup"><span data-stu-id="44fc0-1515">EB84</span></span></td>
  <td><span data-ttu-id="44fc0-1516">NUIFPContinueSlideHand</span><span class="sxs-lookup"><span data-stu-id="44fc0-1516">NUIFPContinueSlideHand</span></span> </td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB85.png" width="32" height="32" alt="NUIFPContinueSlideAction" /></td>
  <td><span data-ttu-id="44fc0-1517">EB85</span><span class="sxs-lookup"><span data-stu-id="44fc0-1517">EB85</span></span></td>
  <td><span data-ttu-id="44fc0-1518">NUIFPContinueSlideAction</span><span class="sxs-lookup"><span data-stu-id="44fc0-1518">NUIFPContinueSlideAction</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB86.png" width="32" height="32" alt="NUIFPRollRightHand " /></td>
  <td><span data-ttu-id="44fc0-1519">EB86</span><span class="sxs-lookup"><span data-stu-id="44fc0-1519">EB86</span></span></td>
  <td><span data-ttu-id="44fc0-1520">NUIFPRollRightHand</span><span class="sxs-lookup"><span data-stu-id="44fc0-1520">NUIFPRollRightHand</span></span> </td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB87.png" width="32" height="32" alt="NUIFPRollRightHandAction" /></td>
  <td><span data-ttu-id="44fc0-1521">EB87</span><span class="sxs-lookup"><span data-stu-id="44fc0-1521">EB87</span></span></td>
  <td><span data-ttu-id="44fc0-1522">NUIFPRollRightHandAction</span><span class="sxs-lookup"><span data-stu-id="44fc0-1522">NUIFPRollRightHandAction</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB88.png" width="32" height="32" alt="NUIFPRollLeftHand " /></td>
  <td><span data-ttu-id="44fc0-1523">EB88</span><span class="sxs-lookup"><span data-stu-id="44fc0-1523">EB88</span></span></td>
  <td><span data-ttu-id="44fc0-1524">NUIFPRollLeftHand</span><span class="sxs-lookup"><span data-stu-id="44fc0-1524">NUIFPRollLeftHand</span></span> </td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB89.png" width="32" height="32" alt="NUIFPRollLeftAction" /></td>
  <td><span data-ttu-id="44fc0-1525">EB89</span><span class="sxs-lookup"><span data-stu-id="44fc0-1525">EB89</span></span></td>
  <td><span data-ttu-id="44fc0-1526">NUIFPRollLeftAction</span><span class="sxs-lookup"><span data-stu-id="44fc0-1526">NUIFPRollLeftAction</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB8A.png" width="32" height="32" alt="NUIFPPressHand " /></td>
  <td><span data-ttu-id="44fc0-1527">EB8A</span><span class="sxs-lookup"><span data-stu-id="44fc0-1527">EB8A</span></span></td>
  <td><span data-ttu-id="44fc0-1528">NUIFPPressHand</span><span class="sxs-lookup"><span data-stu-id="44fc0-1528">NUIFPPressHand</span></span> </td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB8B.png" width="32" height="32" alt="NUIFPPressAction" /></td>
  <td><span data-ttu-id="44fc0-1529">EB8B</span><span class="sxs-lookup"><span data-stu-id="44fc0-1529">EB8B</span></span></td>
  <td><span data-ttu-id="44fc0-1530">NUIFPPressAction</span><span class="sxs-lookup"><span data-stu-id="44fc0-1530">NUIFPPressAction</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB8C.png" width="32" height="32" alt="NUIFPPressRepeatHand " /></td>
  <td><span data-ttu-id="44fc0-1531">EB8C</span><span class="sxs-lookup"><span data-stu-id="44fc0-1531">EB8C</span></span></td>
  <td><span data-ttu-id="44fc0-1532">NUIFPPressRepeatHand</span><span class="sxs-lookup"><span data-stu-id="44fc0-1532">NUIFPPressRepeatHand</span></span> </td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB8D.png" width="32" height="32" alt="NUIFPPressRepeatAction" /></td>
  <td><span data-ttu-id="44fc0-1533">EB8D</span><span class="sxs-lookup"><span data-stu-id="44fc0-1533">EB8D</span></span></td>
  <td><span data-ttu-id="44fc0-1534">NUIFPPressRepeatAction</span><span class="sxs-lookup"><span data-stu-id="44fc0-1534">NUIFPPressRepeatAction</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB90.png" width="32" height="32" alt="StatusErrorFull" /></td>
  <td><span data-ttu-id="44fc0-1535">EB90</span><span class="sxs-lookup"><span data-stu-id="44fc0-1535">EB90</span></span></td>
  <td><span data-ttu-id="44fc0-1536">StatusErrorFull</span><span class="sxs-lookup"><span data-stu-id="44fc0-1536">StatusErrorFull</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB91.png" width="32" height="32" alt="TaskViewExpanded" /></td>
  <td><span data-ttu-id="44fc0-1537">EB91</span><span class="sxs-lookup"><span data-stu-id="44fc0-1537">EB91</span></span></td>
  <td><span data-ttu-id="44fc0-1538">TaskViewExpanded</span><span class="sxs-lookup"><span data-stu-id="44fc0-1538">TaskViewExpanded</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB95.png" width="32" height="32" alt="Certificate" /></td>
  <td><span data-ttu-id="44fc0-1539">EB95</span><span class="sxs-lookup"><span data-stu-id="44fc0-1539">EB95</span></span></td>
  <td><span data-ttu-id="44fc0-1540">Zertifikat</span><span class="sxs-lookup"><span data-stu-id="44fc0-1540">Certificate</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB96.png" width="32" height="32" alt="BackSpaceQWERTYLg" /></td>
  <td><span data-ttu-id="44fc0-1541">EB96</span><span class="sxs-lookup"><span data-stu-id="44fc0-1541">EB96</span></span></td>
  <td><span data-ttu-id="44fc0-1542">BackSpaceQWERTYLg</span><span class="sxs-lookup"><span data-stu-id="44fc0-1542">BackSpaceQWERTYLg</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB97.png" width="32" height="32" alt="ReturnKeyLg" /></td>
  <td><span data-ttu-id="44fc0-1543">EB97</span><span class="sxs-lookup"><span data-stu-id="44fc0-1543">EB97</span></span></td>
  <td><span data-ttu-id="44fc0-1544">ReturnKeyLg</span><span class="sxs-lookup"><span data-stu-id="44fc0-1544">ReturnKeyLg</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB9D.png" width="32" height="32" alt="FastForward" /></td>
  <td><span data-ttu-id="44fc0-1545">EB9D</span><span class="sxs-lookup"><span data-stu-id="44fc0-1545">EB9D</span></span></td>
  <td><span data-ttu-id="44fc0-1546">FastForward</span><span class="sxs-lookup"><span data-stu-id="44fc0-1546">FastForward</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB9E.png" width="32" height="32" alt="Rewind" /></td>
  <td><span data-ttu-id="44fc0-1547">EB9E</span><span class="sxs-lookup"><span data-stu-id="44fc0-1547">EB9E</span></span></td>
  <td><span data-ttu-id="44fc0-1548">Rewind</span><span class="sxs-lookup"><span data-stu-id="44fc0-1548">Rewind</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EB9F.png" width="32" height="32" alt="Photo2" /></td>
  <td><span data-ttu-id="44fc0-1549">EB9F</span><span class="sxs-lookup"><span data-stu-id="44fc0-1549">EB9F</span></span></td>
  <td><span data-ttu-id="44fc0-1550">Photo2</span><span class="sxs-lookup"><span data-stu-id="44fc0-1550">Photo2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBA0.png" width="32" height="32" alt=" MobBattery0" /></td>
  <td><span data-ttu-id="44fc0-1551">EBA0</span><span class="sxs-lookup"><span data-stu-id="44fc0-1551">EBA0</span></span></td>
  <td> <span data-ttu-id="44fc0-1552">MobBattery0</span><span class="sxs-lookup"><span data-stu-id="44fc0-1552">MobBattery0</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBA1.png" width="32" height="32" alt=" MobBattery1" /></td>
  <td><span data-ttu-id="44fc0-1553">EBA1</span><span class="sxs-lookup"><span data-stu-id="44fc0-1553">EBA1</span></span></td>
  <td> <span data-ttu-id="44fc0-1554">MobBattery1</span><span class="sxs-lookup"><span data-stu-id="44fc0-1554">MobBattery1</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBA2.png" width="32" height="32" alt=" MobBattery2" /></td>
  <td><span data-ttu-id="44fc0-1555">EBA2</span><span class="sxs-lookup"><span data-stu-id="44fc0-1555">EBA2</span></span></td>
  <td> <span data-ttu-id="44fc0-1556">MobBattery2</span><span class="sxs-lookup"><span data-stu-id="44fc0-1556">MobBattery2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBA3.png" width="32" height="32" alt=" MobBattery3" /></td>
  <td><span data-ttu-id="44fc0-1557">EBA3</span><span class="sxs-lookup"><span data-stu-id="44fc0-1557">EBA3</span></span></td>
  <td> <span data-ttu-id="44fc0-1558">MobBattery3</span><span class="sxs-lookup"><span data-stu-id="44fc0-1558">MobBattery3</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBA4.png" width="32" height="32" alt=" MobBattery4" /></td>
  <td><span data-ttu-id="44fc0-1559">EBA4</span><span class="sxs-lookup"><span data-stu-id="44fc0-1559">EBA4</span></span></td>
  <td> <span data-ttu-id="44fc0-1560">MobBattery4</span><span class="sxs-lookup"><span data-stu-id="44fc0-1560">MobBattery4</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBA5.png" width="32" height="32" alt=" MobBattery5" /></td>
  <td><span data-ttu-id="44fc0-1561">EBA5</span><span class="sxs-lookup"><span data-stu-id="44fc0-1561">EBA5</span></span></td>
  <td> <span data-ttu-id="44fc0-1562">MobBattery5</span><span class="sxs-lookup"><span data-stu-id="44fc0-1562">MobBattery5</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBA6.png" width="32" height="32" alt=" MobBattery6" /></td>
  <td><span data-ttu-id="44fc0-1563">EBA6</span><span class="sxs-lookup"><span data-stu-id="44fc0-1563">EBA6</span></span></td>
  <td> <span data-ttu-id="44fc0-1564">MobBattery6</span><span class="sxs-lookup"><span data-stu-id="44fc0-1564">MobBattery6</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBA7.png" width="32" height="32" alt=" MobBattery7" /></td>
  <td><span data-ttu-id="44fc0-1565">EBA7</span><span class="sxs-lookup"><span data-stu-id="44fc0-1565">EBA7</span></span></td>
  <td> <span data-ttu-id="44fc0-1566">MobBattery7</span><span class="sxs-lookup"><span data-stu-id="44fc0-1566">MobBattery7</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBA8.png" width="32" height="32" alt=" MobBattery8" /></td>
  <td><span data-ttu-id="44fc0-1567">EBA8</span><span class="sxs-lookup"><span data-stu-id="44fc0-1567">EBA8</span></span></td>
  <td> <span data-ttu-id="44fc0-1568">MobBattery8</span><span class="sxs-lookup"><span data-stu-id="44fc0-1568">MobBattery8</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBA9.png" width="32" height="32" alt=" MobBattery9" /></td>
  <td><span data-ttu-id="44fc0-1569">EBA9</span><span class="sxs-lookup"><span data-stu-id="44fc0-1569">EBA9</span></span></td>
  <td> <span data-ttu-id="44fc0-1570">MobBattery9</span><span class="sxs-lookup"><span data-stu-id="44fc0-1570">MobBattery9</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBAA.png" width="32" height="32" alt="MobBattery10" /></td>
  <td><span data-ttu-id="44fc0-1571">EBAA</span><span class="sxs-lookup"><span data-stu-id="44fc0-1571">EBAA</span></span></td>
  <td><span data-ttu-id="44fc0-1572">MobBattery10</span><span class="sxs-lookup"><span data-stu-id="44fc0-1572">MobBattery10</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBAB.png" width="32" height="32" alt=" MobBatteryCharging0" /></td>
  <td><span data-ttu-id="44fc0-1573">EBAB</span><span class="sxs-lookup"><span data-stu-id="44fc0-1573">EBAB</span></span></td>
  <td> <span data-ttu-id="44fc0-1574">MobBatteryCharging0</span><span class="sxs-lookup"><span data-stu-id="44fc0-1574">MobBatteryCharging0</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBAC.png" width="32" height="32" alt=" MobBatteryCharging1" /></td>
  <td><span data-ttu-id="44fc0-1575">EBAC</span><span class="sxs-lookup"><span data-stu-id="44fc0-1575">EBAC</span></span></td>
  <td> <span data-ttu-id="44fc0-1576">MobBatteryCharging1</span><span class="sxs-lookup"><span data-stu-id="44fc0-1576">MobBatteryCharging1</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBAD.png" width="32" height="32" alt=" MobBatteryCharging2" /></td>
  <td><span data-ttu-id="44fc0-1577">EBAD</span><span class="sxs-lookup"><span data-stu-id="44fc0-1577">EBAD</span></span></td>
  <td> <span data-ttu-id="44fc0-1578">MobBatteryCharging2</span><span class="sxs-lookup"><span data-stu-id="44fc0-1578">MobBatteryCharging2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBAE.png" width="32" height="32" alt=" MobBatteryCharging3" /></td>
  <td><span data-ttu-id="44fc0-1579">EBAE</span><span class="sxs-lookup"><span data-stu-id="44fc0-1579">EBAE</span></span></td>
  <td> <span data-ttu-id="44fc0-1580">MobBatteryCharging3</span><span class="sxs-lookup"><span data-stu-id="44fc0-1580">MobBatteryCharging3</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBAF.png" width="32" height="32" alt=" MobBatteryCharging4" /></td>
  <td><span data-ttu-id="44fc0-1581">EBAF</span><span class="sxs-lookup"><span data-stu-id="44fc0-1581">EBAF</span></span></td>
  <td> <span data-ttu-id="44fc0-1582">MobBatteryCharging4</span><span class="sxs-lookup"><span data-stu-id="44fc0-1582">MobBatteryCharging4</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBB0.png" width="32" height="32" alt=" MobBatteryCharging5" /></td>
  <td><span data-ttu-id="44fc0-1583">EBB0</span><span class="sxs-lookup"><span data-stu-id="44fc0-1583">EBB0</span></span></td>
  <td> <span data-ttu-id="44fc0-1584">MobBatteryCharging5</span><span class="sxs-lookup"><span data-stu-id="44fc0-1584">MobBatteryCharging5</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBB1.png" width="32" height="32" alt=" MobBatteryCharging6" /></td>
  <td><span data-ttu-id="44fc0-1585">EBB1</span><span class="sxs-lookup"><span data-stu-id="44fc0-1585">EBB1</span></span></td>
  <td> <span data-ttu-id="44fc0-1586">MobBatteryCharging6</span><span class="sxs-lookup"><span data-stu-id="44fc0-1586">MobBatteryCharging6</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBB2.png" width="32" height="32" alt=" MobBatteryCharging7" /></td>
  <td><span data-ttu-id="44fc0-1587">EBB2</span><span class="sxs-lookup"><span data-stu-id="44fc0-1587">EBB2</span></span></td>
  <td> <span data-ttu-id="44fc0-1588">MobBatteryCharging7</span><span class="sxs-lookup"><span data-stu-id="44fc0-1588">MobBatteryCharging7</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBB3.png" width="32" height="32" alt=" MobBatteryCharging8" /></td>
  <td><span data-ttu-id="44fc0-1589">EBB3</span><span class="sxs-lookup"><span data-stu-id="44fc0-1589">EBB3</span></span></td>
  <td> <span data-ttu-id="44fc0-1590">MobBatteryCharging8</span><span class="sxs-lookup"><span data-stu-id="44fc0-1590">MobBatteryCharging8</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBB4.png" width="32" height="32" alt=" MobBatteryCharging9" /></td>
  <td><span data-ttu-id="44fc0-1591">EBB4</span><span class="sxs-lookup"><span data-stu-id="44fc0-1591">EBB4</span></span></td>
  <td> <span data-ttu-id="44fc0-1592">MobBatteryCharging9</span><span class="sxs-lookup"><span data-stu-id="44fc0-1592">MobBatteryCharging9</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBB5.png" width="32" height="32" alt=" MobBatteryCharging10" /></td>
  <td><span data-ttu-id="44fc0-1593">EBB5</span><span class="sxs-lookup"><span data-stu-id="44fc0-1593">EBB5</span></span></td>
  <td> <span data-ttu-id="44fc0-1594">MobBatteryCharging10</span><span class="sxs-lookup"><span data-stu-id="44fc0-1594">MobBatteryCharging10</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBB6.png" width="32" height="32" alt=" MobBatterySaver0" /></td>
  <td><span data-ttu-id="44fc0-1595">EBB6</span><span class="sxs-lookup"><span data-stu-id="44fc0-1595">EBB6</span></span></td>
  <td> <span data-ttu-id="44fc0-1596">MobBatterySaver0</span><span class="sxs-lookup"><span data-stu-id="44fc0-1596">MobBatterySaver0</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBB7.png" width="32" height="32" alt=" MobBatterySaver1" /></td>
  <td><span data-ttu-id="44fc0-1597">EBB7</span><span class="sxs-lookup"><span data-stu-id="44fc0-1597">EBB7</span></span></td>
  <td> <span data-ttu-id="44fc0-1598">MobBatterySaver1</span><span class="sxs-lookup"><span data-stu-id="44fc0-1598">MobBatterySaver1</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBB8.png" width="32" height="32" alt=" MobBatterySaver2" /></td>
  <td><span data-ttu-id="44fc0-1599">EBB8</span><span class="sxs-lookup"><span data-stu-id="44fc0-1599">EBB8</span></span></td>
  <td> <span data-ttu-id="44fc0-1600">MobBatterySaver2</span><span class="sxs-lookup"><span data-stu-id="44fc0-1600">MobBatterySaver2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBB9.png" width="32" height="32" alt=" MobBatterySaver3" /></td>
  <td><span data-ttu-id="44fc0-1601">EBB9</span><span class="sxs-lookup"><span data-stu-id="44fc0-1601">EBB9</span></span></td>
  <td> <span data-ttu-id="44fc0-1602">MobBatterySaver3</span><span class="sxs-lookup"><span data-stu-id="44fc0-1602">MobBatterySaver3</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBBA.png" width="32" height="32" alt=" MobBatterySaver4" /></td>
  <td><span data-ttu-id="44fc0-1603">EBBA</span><span class="sxs-lookup"><span data-stu-id="44fc0-1603">EBBA</span></span></td>
  <td> <span data-ttu-id="44fc0-1604">MobBatterySaver4</span><span class="sxs-lookup"><span data-stu-id="44fc0-1604">MobBatterySaver4</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBBB.png" width="32" height="32" alt=" MobBatterySaver5" /></td>
  <td><span data-ttu-id="44fc0-1605">EBBB</span><span class="sxs-lookup"><span data-stu-id="44fc0-1605">EBBB</span></span></td>
  <td> <span data-ttu-id="44fc0-1606">MobBatterySaver5</span><span class="sxs-lookup"><span data-stu-id="44fc0-1606">MobBatterySaver5</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBBC.png" width="32" height="32" alt=" MobBatterySaver6" /></td>
  <td><span data-ttu-id="44fc0-1607">EBBC</span><span class="sxs-lookup"><span data-stu-id="44fc0-1607">EBBC</span></span></td>
  <td> <span data-ttu-id="44fc0-1608">MobBatterySaver6</span><span class="sxs-lookup"><span data-stu-id="44fc0-1608">MobBatterySaver6</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBBD.png" width="32" height="32" alt=" MobBatterySaver7" /></td>
  <td><span data-ttu-id="44fc0-1609">EBBD</span><span class="sxs-lookup"><span data-stu-id="44fc0-1609">EBBD</span></span></td>
  <td> <span data-ttu-id="44fc0-1610">MobBatterySaver7</span><span class="sxs-lookup"><span data-stu-id="44fc0-1610">MobBatterySaver7</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBBE.png" width="32" height="32" alt=" MobBatterySaver8" /></td>
  <td><span data-ttu-id="44fc0-1611">EBBE</span><span class="sxs-lookup"><span data-stu-id="44fc0-1611">EBBE</span></span></td>
  <td> <span data-ttu-id="44fc0-1612">MobBatterySaver8</span><span class="sxs-lookup"><span data-stu-id="44fc0-1612">MobBatterySaver8</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBBF.png" width="32" height="32" alt=" MobBatterySaver9" /></td>
  <td><span data-ttu-id="44fc0-1613">EBBF</span><span class="sxs-lookup"><span data-stu-id="44fc0-1613">EBBF</span></span></td>
  <td> <span data-ttu-id="44fc0-1614">MobBatterySaver9</span><span class="sxs-lookup"><span data-stu-id="44fc0-1614">MobBatterySaver9</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBC0.png" width="32" height="32" alt=" MobBatterySaver10" /></td>
  <td><span data-ttu-id="44fc0-1615">EBC0</span><span class="sxs-lookup"><span data-stu-id="44fc0-1615">EBC0</span></span></td>
  <td> <span data-ttu-id="44fc0-1616">MobBatterySaver10</span><span class="sxs-lookup"><span data-stu-id="44fc0-1616">MobBatterySaver10</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBC3.png" width="32" height="32" alt="DictionaryCloud" /></td>
  <td><span data-ttu-id="44fc0-1617">EBC3</span><span class="sxs-lookup"><span data-stu-id="44fc0-1617">EBC3</span></span></td>
  <td><span data-ttu-id="44fc0-1618">DictionaryCloud</span><span class="sxs-lookup"><span data-stu-id="44fc0-1618">DictionaryCloud</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBC4.png" width="32" height="32" alt="ResetDrive" /></td>
  <td><span data-ttu-id="44fc0-1619">EBC4</span><span class="sxs-lookup"><span data-stu-id="44fc0-1619">EBC4</span></span></td>
  <td><span data-ttu-id="44fc0-1620">ResetDrive</span><span class="sxs-lookup"><span data-stu-id="44fc0-1620">ResetDrive</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBC5.png" width="32" height="32" alt="VolumeBars" /></td>
  <td><span data-ttu-id="44fc0-1621">EBC5</span><span class="sxs-lookup"><span data-stu-id="44fc0-1621">EBC5</span></span></td>
  <td><span data-ttu-id="44fc0-1622">VolumeBars</span><span class="sxs-lookup"><span data-stu-id="44fc0-1622">VolumeBars</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBC6.png" width="32" height="32" alt="Project" /></td>
  <td><span data-ttu-id="44fc0-1623">EBC6</span><span class="sxs-lookup"><span data-stu-id="44fc0-1623">EBC6</span></span></td>
  <td><span data-ttu-id="44fc0-1624">Projizieren</span><span class="sxs-lookup"><span data-stu-id="44fc0-1624">Project</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBD2.png" width="32" height="32" alt="AdjustHologram" /></td>
  <td><span data-ttu-id="44fc0-1625">EBD2</span><span class="sxs-lookup"><span data-stu-id="44fc0-1625">EBD2</span></span></td>
  <td><span data-ttu-id="44fc0-1626">AdjustHologram</span><span class="sxs-lookup"><span data-stu-id="44fc0-1626">AdjustHologram</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBD4.png" width="32" height="32" alt="WifiCallBars" /></td>
  <td><span data-ttu-id="44fc0-1627">EBD4</span><span class="sxs-lookup"><span data-stu-id="44fc0-1627">EBD4</span></span></td>
  <td><span data-ttu-id="44fc0-1628">WifiCallBars</span><span class="sxs-lookup"><span data-stu-id="44fc0-1628">WifiCallBars</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBD5.png" width="32" height="32" alt="WifiCall0" /></td>
  <td><span data-ttu-id="44fc0-1629">EBD5</span><span class="sxs-lookup"><span data-stu-id="44fc0-1629">EBD5</span></span></td>
  <td><span data-ttu-id="44fc0-1630">WifiCall0</span><span class="sxs-lookup"><span data-stu-id="44fc0-1630">WifiCall0</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBD6.png" width="32" height="32" alt="WifiCall1" /></td>
  <td><span data-ttu-id="44fc0-1631">EBD6</span><span class="sxs-lookup"><span data-stu-id="44fc0-1631">EBD6</span></span></td>
  <td><span data-ttu-id="44fc0-1632">WifiCall1</span><span class="sxs-lookup"><span data-stu-id="44fc0-1632">WifiCall1</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBD7.png" width="32" height="32" alt="WifiCall2" /></td>
  <td><span data-ttu-id="44fc0-1633">EBD7</span><span class="sxs-lookup"><span data-stu-id="44fc0-1633">EBD7</span></span></td>
  <td><span data-ttu-id="44fc0-1634">WifiCall2</span><span class="sxs-lookup"><span data-stu-id="44fc0-1634">WifiCall2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBD8.png" width="32" height="32" alt="WifiCall3" /></td>
  <td><span data-ttu-id="44fc0-1635">EBD8</span><span class="sxs-lookup"><span data-stu-id="44fc0-1635">EBD8</span></span></td>
  <td><span data-ttu-id="44fc0-1636">WifiCall3</span><span class="sxs-lookup"><span data-stu-id="44fc0-1636">WifiCall3</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBD9.png" width="32" height="32" alt="WifiCall4" /></td>
  <td><span data-ttu-id="44fc0-1637">EBD9</span><span class="sxs-lookup"><span data-stu-id="44fc0-1637">EBD9</span></span></td>
  <td><span data-ttu-id="44fc0-1638">WifiCall4</span><span class="sxs-lookup"><span data-stu-id="44fc0-1638">WifiCall4</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBDA.png" width="32" height="32" alt="Family" /></td>
  <td><span data-ttu-id="44fc0-1639">EBDA</span><span class="sxs-lookup"><span data-stu-id="44fc0-1639">EBDA</span></span></td>
  <td><span data-ttu-id="44fc0-1640">Familie</span><span class="sxs-lookup"><span data-stu-id="44fc0-1640">Family</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBDB.png" width="32" height="32" alt="LockFeedback" /></td>
  <td><span data-ttu-id="44fc0-1641">EBDB</span><span class="sxs-lookup"><span data-stu-id="44fc0-1641">EBDB</span></span></td>
  <td><span data-ttu-id="44fc0-1642">LockFeedback</span><span class="sxs-lookup"><span data-stu-id="44fc0-1642">LockFeedback</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBDE.png" width="32" height="32" alt="DeviceDiscovery" /></td>
  <td><span data-ttu-id="44fc0-1643">EBDE</span><span class="sxs-lookup"><span data-stu-id="44fc0-1643">EBDE</span></span></td>
  <td><span data-ttu-id="44fc0-1644">DeviceDiscovery</span><span class="sxs-lookup"><span data-stu-id="44fc0-1644">DeviceDiscovery</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBE6.png" width="32" height="32" alt="WindDirection" /></td>
  <td><span data-ttu-id="44fc0-1645">EBE6</span><span class="sxs-lookup"><span data-stu-id="44fc0-1645">EBE6</span></span></td>
  <td><span data-ttu-id="44fc0-1646">WindDirection</span><span class="sxs-lookup"><span data-stu-id="44fc0-1646">WindDirection</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBE7.png" width="32" height="32" alt="RightArrowKeyTime0" /></td>
  <td><span data-ttu-id="44fc0-1647">EBE7</span><span class="sxs-lookup"><span data-stu-id="44fc0-1647">EBE7</span></span></td>
  <td><span data-ttu-id="44fc0-1648">RightArrowKeyTime0</span><span class="sxs-lookup"><span data-stu-id="44fc0-1648">RightArrowKeyTime0</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBE8.png" width="32" height="32" alt="Bug" /></td>
  <td><span data-ttu-id="44fc0-1649">EBE8</span><span class="sxs-lookup"><span data-stu-id="44fc0-1649">EBE8</span></span></td>
  <td><span data-ttu-id="44fc0-1650">Fehler</span><span class="sxs-lookup"><span data-stu-id="44fc0-1650">Bug</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBFC.png" width="32" height="32" alt="TabletMode" /></td>
  <td><span data-ttu-id="44fc0-1651">EBFC</span><span class="sxs-lookup"><span data-stu-id="44fc0-1651">EBFC</span></span></td>
  <td><span data-ttu-id="44fc0-1652">TabletMode</span><span class="sxs-lookup"><span data-stu-id="44fc0-1652">TabletMode</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBFD.png" width="32" height="32" alt="StatusCircleLeft" /></td>
  <td><span data-ttu-id="44fc0-1653">EBFD</span><span class="sxs-lookup"><span data-stu-id="44fc0-1653">EBFD</span></span></td>
  <td><span data-ttu-id="44fc0-1654">StatusCircleLeft</span><span class="sxs-lookup"><span data-stu-id="44fc0-1654">StatusCircleLeft</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBFE.png" width="32" height="32" alt="StatusTriangleLeft" /></td>
  <td><span data-ttu-id="44fc0-1655">EBFE</span><span class="sxs-lookup"><span data-stu-id="44fc0-1655">EBFE</span></span></td>
  <td><span data-ttu-id="44fc0-1656">StatusTriangleLeft</span><span class="sxs-lookup"><span data-stu-id="44fc0-1656">StatusTriangleLeft</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EBFF.png" width="32" height="32" alt="StatusErrorLeft" /></td>
  <td><span data-ttu-id="44fc0-1657">EBFF</span><span class="sxs-lookup"><span data-stu-id="44fc0-1657">EBFF</span></span></td>
  <td><span data-ttu-id="44fc0-1658">StatusErrorLeft</span><span class="sxs-lookup"><span data-stu-id="44fc0-1658">StatusErrorLeft</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC00.png" width="32" height="32" alt="StatusWarningLeft" /></td>
  <td><span data-ttu-id="44fc0-1659">EC00</span><span class="sxs-lookup"><span data-stu-id="44fc0-1659">EC00</span></span></td>
  <td><span data-ttu-id="44fc0-1660">StatusWarningLeft</span><span class="sxs-lookup"><span data-stu-id="44fc0-1660">StatusWarningLeft</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC02.png" width="32" height="32" alt="MobBatteryUnknown" /></td>
  <td><span data-ttu-id="44fc0-1661">EC02</span><span class="sxs-lookup"><span data-stu-id="44fc0-1661">EC02</span></span></td>
  <td><span data-ttu-id="44fc0-1662">MobBatteryUnknown</span><span class="sxs-lookup"><span data-stu-id="44fc0-1662">MobBatteryUnknown</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC05.png" width="32" height="32" alt="NetworkTower" /></td>
  <td><span data-ttu-id="44fc0-1663">EC05</span><span class="sxs-lookup"><span data-stu-id="44fc0-1663">EC05</span></span></td>
  <td><span data-ttu-id="44fc0-1664">NetworkTower</span><span class="sxs-lookup"><span data-stu-id="44fc0-1664">NetworkTower</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC06.png" width="32" height="32" alt="CityNext" /></td>
  <td><span data-ttu-id="44fc0-1665">EC06</span><span class="sxs-lookup"><span data-stu-id="44fc0-1665">EC06</span></span></td>
  <td><span data-ttu-id="44fc0-1666">CityNext</span><span class="sxs-lookup"><span data-stu-id="44fc0-1666">CityNext</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC07.png" width="32" height="32" alt="CityNext2" /></td>
  <td><span data-ttu-id="44fc0-1667">EC07</span><span class="sxs-lookup"><span data-stu-id="44fc0-1667">EC07</span></span></td>
  <td><span data-ttu-id="44fc0-1668">CityNext2</span><span class="sxs-lookup"><span data-stu-id="44fc0-1668">CityNext2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC08.png" width="32" height="32" alt="Courthouse" /></td>
  <td><span data-ttu-id="44fc0-1669">EC08</span><span class="sxs-lookup"><span data-stu-id="44fc0-1669">EC08</span></span></td>
  <td><span data-ttu-id="44fc0-1670">Courthouse</span><span class="sxs-lookup"><span data-stu-id="44fc0-1670">Courthouse</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC09.png" width="32" height="32" alt="Groceries" /></td>
  <td><span data-ttu-id="44fc0-1671">EC09</span><span class="sxs-lookup"><span data-stu-id="44fc0-1671">EC09</span></span></td>
  <td><span data-ttu-id="44fc0-1672">Groceries</span><span class="sxs-lookup"><span data-stu-id="44fc0-1672">Groceries</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC0A.png" width="32" height="32" alt="Sustainable" /></td>
  <td><span data-ttu-id="44fc0-1673">EC0A</span><span class="sxs-lookup"><span data-stu-id="44fc0-1673">EC0A</span></span></td>
  <td><span data-ttu-id="44fc0-1674">Sustainable</span><span class="sxs-lookup"><span data-stu-id="44fc0-1674">Sustainable</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC0B.png" width="32" height="32" alt="BuildingEnergy" /></td>
  <td><span data-ttu-id="44fc0-1675">EC0B</span><span class="sxs-lookup"><span data-stu-id="44fc0-1675">EC0B</span></span></td>
  <td><span data-ttu-id="44fc0-1676">BuildingEnergy</span><span class="sxs-lookup"><span data-stu-id="44fc0-1676">BuildingEnergy</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC11.png" width="32" height="32" alt="ToggleFilled" /></td>
  <td><span data-ttu-id="44fc0-1677">EC11</span><span class="sxs-lookup"><span data-stu-id="44fc0-1677">EC11</span></span></td>
  <td><span data-ttu-id="44fc0-1678">ToggleFilled</span><span class="sxs-lookup"><span data-stu-id="44fc0-1678">ToggleFilled</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC12.png" width="32" height="32" alt="ToggleBorder" /></td>
  <td><span data-ttu-id="44fc0-1679">EC12</span><span class="sxs-lookup"><span data-stu-id="44fc0-1679">EC12</span></span></td>
  <td><span data-ttu-id="44fc0-1680">ToggleBorder</span><span class="sxs-lookup"><span data-stu-id="44fc0-1680">ToggleBorder</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC13.png" width="32" height="32" alt="SliderThumb" /></td>
  <td><span data-ttu-id="44fc0-1681">EC13</span><span class="sxs-lookup"><span data-stu-id="44fc0-1681">EC13</span></span></td>
  <td><span data-ttu-id="44fc0-1682">SliderThumb</span><span class="sxs-lookup"><span data-stu-id="44fc0-1682">SliderThumb</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC14.png" width="32" height="32" alt="ToggleThumb" /></td>
  <td><span data-ttu-id="44fc0-1683">EC14</span><span class="sxs-lookup"><span data-stu-id="44fc0-1683">EC14</span></span></td>
  <td><span data-ttu-id="44fc0-1684">ToggleThumb</span><span class="sxs-lookup"><span data-stu-id="44fc0-1684">ToggleThumb</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC15.png" width="32" height="32" alt="MiracastLogoSmall" /></td>
  <td><span data-ttu-id="44fc0-1685">EC15</span><span class="sxs-lookup"><span data-stu-id="44fc0-1685">EC15</span></span></td>
  <td><span data-ttu-id="44fc0-1686">MiracastLogoSmall</span><span class="sxs-lookup"><span data-stu-id="44fc0-1686">MiracastLogoSmall</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC16.png" width="32" height="32" alt="MiracastLogoLarge" /></td>
  <td><span data-ttu-id="44fc0-1687">EC16</span><span class="sxs-lookup"><span data-stu-id="44fc0-1687">EC16</span></span></td>
  <td><span data-ttu-id="44fc0-1688">MiracastLogoLarge</span><span class="sxs-lookup"><span data-stu-id="44fc0-1688">MiracastLogoLarge</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC19.png" width="32" height="32" alt="PLAP" /></td>
  <td><span data-ttu-id="44fc0-1689">EC19</span><span class="sxs-lookup"><span data-stu-id="44fc0-1689">EC19</span></span></td>
  <td><span data-ttu-id="44fc0-1690">PLAP</span><span class="sxs-lookup"><span data-stu-id="44fc0-1690">PLAP</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC1B.png" width="32" height="32" alt="Badge" /></td>
  <td><span data-ttu-id="44fc0-1691">EC1B</span><span class="sxs-lookup"><span data-stu-id="44fc0-1691">EC1B</span></span></td>
  <td><span data-ttu-id="44fc0-1692">Badge</span><span class="sxs-lookup"><span data-stu-id="44fc0-1692">Badge</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC1E.png" width="32" height="32" alt="SignalRoaming" /></td>
  <td><span data-ttu-id="44fc0-1693">EC1E</span><span class="sxs-lookup"><span data-stu-id="44fc0-1693">EC1E</span></span></td>
  <td><span data-ttu-id="44fc0-1694">SignalRoaming</span><span class="sxs-lookup"><span data-stu-id="44fc0-1694">SignalRoaming</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC20.png" width="32" height="32" alt="MobileLocked" /></td>
  <td><span data-ttu-id="44fc0-1695">EC20</span><span class="sxs-lookup"><span data-stu-id="44fc0-1695">EC20</span></span></td>
  <td><span data-ttu-id="44fc0-1696">MobileLocked</span><span class="sxs-lookup"><span data-stu-id="44fc0-1696">MobileLocked</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC24.png" width="32" height="32" alt="InsiderHubApp" /></td>
  <td><span data-ttu-id="44fc0-1697">EC24</span><span class="sxs-lookup"><span data-stu-id="44fc0-1697">EC24</span></span></td>
  <td><span data-ttu-id="44fc0-1698">InsiderHubApp</span><span class="sxs-lookup"><span data-stu-id="44fc0-1698">InsiderHubApp</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC25.png" width="32" height="32" alt="PersonalFolder" /></td>
  <td><span data-ttu-id="44fc0-1699">EC25</span><span class="sxs-lookup"><span data-stu-id="44fc0-1699">EC25</span></span></td>
  <td><span data-ttu-id="44fc0-1700">PersonalFolder</span><span class="sxs-lookup"><span data-stu-id="44fc0-1700">PersonalFolder</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC26.png" width="32" height="32" alt="HomeGroup" /></td>
  <td><span data-ttu-id="44fc0-1701">EC26</span><span class="sxs-lookup"><span data-stu-id="44fc0-1701">EC26</span></span></td>
  <td><span data-ttu-id="44fc0-1702">HomeGroup</span><span class="sxs-lookup"><span data-stu-id="44fc0-1702">HomeGroup</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC27.png" width="32" height="32" alt="MyNetwork" /></td>
  <td><span data-ttu-id="44fc0-1703">EC27</span><span class="sxs-lookup"><span data-stu-id="44fc0-1703">EC27</span></span></td>
  <td><span data-ttu-id="44fc0-1704">MyNetwork</span><span class="sxs-lookup"><span data-stu-id="44fc0-1704">MyNetwork</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC31.png" width="32" height="32" alt="KeyboardFull" /></td>
  <td><span data-ttu-id="44fc0-1705">EC31</span><span class="sxs-lookup"><span data-stu-id="44fc0-1705">EC31</span></span></td>
  <td><span data-ttu-id="44fc0-1706">KeyboardFull</span><span class="sxs-lookup"><span data-stu-id="44fc0-1706">KeyboardFull</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC32.png" width="32" height="32" alt="Cafe" /></td>
  <td><span data-ttu-id="44fc0-1707">EC32</span><span class="sxs-lookup"><span data-stu-id="44fc0-1707">EC32</span></span></td>
  <td><span data-ttu-id="44fc0-1708">Cafe</span><span class="sxs-lookup"><span data-stu-id="44fc0-1708">Cafe</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC37.png" width="32" height="32" alt="MobSignal1" /></td>
  <td><span data-ttu-id="44fc0-1709">EC37</span><span class="sxs-lookup"><span data-stu-id="44fc0-1709">EC37</span></span></td>
  <td><span data-ttu-id="44fc0-1710">MobSignal1</span><span class="sxs-lookup"><span data-stu-id="44fc0-1710">MobSignal1</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC38.png" width="32" height="32" alt="MobSignal2" /></td>
  <td><span data-ttu-id="44fc0-1711">EC38</span><span class="sxs-lookup"><span data-stu-id="44fc0-1711">EC38</span></span></td>
  <td><span data-ttu-id="44fc0-1712">MobSignal2</span><span class="sxs-lookup"><span data-stu-id="44fc0-1712">MobSignal2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC39.png" width="32" height="32" alt="MobSignal3" /></td>
  <td><span data-ttu-id="44fc0-1713">EC39</span><span class="sxs-lookup"><span data-stu-id="44fc0-1713">EC39</span></span></td>
  <td><span data-ttu-id="44fc0-1714">MobSignal3</span><span class="sxs-lookup"><span data-stu-id="44fc0-1714">MobSignal3</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC3A.png" width="32" height="32" alt="MobSignal4" /></td>
  <td><span data-ttu-id="44fc0-1715">EC3A</span><span class="sxs-lookup"><span data-stu-id="44fc0-1715">EC3A</span></span></td>
  <td><span data-ttu-id="44fc0-1716">MobSignal4</span><span class="sxs-lookup"><span data-stu-id="44fc0-1716">MobSignal4</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC3B.png" width="32" height="32" alt="MobSignal5" /></td>
  <td><span data-ttu-id="44fc0-1717">EC3B</span><span class="sxs-lookup"><span data-stu-id="44fc0-1717">EC3B</span></span></td>
  <td><span data-ttu-id="44fc0-1718">MobSignal5</span><span class="sxs-lookup"><span data-stu-id="44fc0-1718">MobSignal5</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC3C.png" width="32" height="32" alt="MobWifi1" /></td>
  <td><span data-ttu-id="44fc0-1719">EC3C</span><span class="sxs-lookup"><span data-stu-id="44fc0-1719">EC3C</span></span></td>
  <td><span data-ttu-id="44fc0-1720">MobWifi1</span><span class="sxs-lookup"><span data-stu-id="44fc0-1720">MobWifi1</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC3D.png" width="32" height="32" alt="MobWifi2" /></td>
  <td><span data-ttu-id="44fc0-1721">EC3D</span><span class="sxs-lookup"><span data-stu-id="44fc0-1721">EC3D</span></span></td>
  <td><span data-ttu-id="44fc0-1722">MobWifi2</span><span class="sxs-lookup"><span data-stu-id="44fc0-1722">MobWifi2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC3E.png" width="32" height="32" alt="MobWifi3" /></td>
  <td><span data-ttu-id="44fc0-1723">EC3E</span><span class="sxs-lookup"><span data-stu-id="44fc0-1723">EC3E</span></span></td>
  <td><span data-ttu-id="44fc0-1724">MobWifi3</span><span class="sxs-lookup"><span data-stu-id="44fc0-1724">MobWifi3</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC3F.png" width="32" height="32" alt="MobWifi4" /></td>
  <td><span data-ttu-id="44fc0-1725">EC3F</span><span class="sxs-lookup"><span data-stu-id="44fc0-1725">EC3F</span></span></td>
  <td><span data-ttu-id="44fc0-1726">MobWifi4</span><span class="sxs-lookup"><span data-stu-id="44fc0-1726">MobWifi4</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC40.png" width="32" height="32" alt="MobAirplane" /></td>
  <td><span data-ttu-id="44fc0-1727">EC40</span><span class="sxs-lookup"><span data-stu-id="44fc0-1727">EC40</span></span></td>
  <td><span data-ttu-id="44fc0-1728">MobAirplane</span><span class="sxs-lookup"><span data-stu-id="44fc0-1728">MobAirplane</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC41.png" width="32" height="32" alt="MobBluetooth" /></td>
  <td><span data-ttu-id="44fc0-1729">EC41</span><span class="sxs-lookup"><span data-stu-id="44fc0-1729">EC41</span></span></td>
  <td><span data-ttu-id="44fc0-1730">MobBluetooth</span><span class="sxs-lookup"><span data-stu-id="44fc0-1730">MobBluetooth</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC42.png" width="32" height="32" alt="MobActionCenter" /></td>
  <td><span data-ttu-id="44fc0-1731">EC42</span><span class="sxs-lookup"><span data-stu-id="44fc0-1731">EC42</span></span></td>
  <td><span data-ttu-id="44fc0-1732">MobActionCenter</span><span class="sxs-lookup"><span data-stu-id="44fc0-1732">MobActionCenter</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC43.png" width="32" height="32" alt="MobLocation" /></td>
  <td><span data-ttu-id="44fc0-1733">EC43</span><span class="sxs-lookup"><span data-stu-id="44fc0-1733">EC43</span></span></td>
  <td><span data-ttu-id="44fc0-1734">MobLocation</span><span class="sxs-lookup"><span data-stu-id="44fc0-1734">MobLocation</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC44.png" width="32" height="32" alt="MobWifiHotspot" /></td>
  <td><span data-ttu-id="44fc0-1735">EC44</span><span class="sxs-lookup"><span data-stu-id="44fc0-1735">EC44</span></span></td>
  <td><span data-ttu-id="44fc0-1736">MobWifiHotspot</span><span class="sxs-lookup"><span data-stu-id="44fc0-1736">MobWifiHotspot</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC45.png" width="32" height="32" alt="LanguageJpn" /></td>
  <td><span data-ttu-id="44fc0-1737">EC45</span><span class="sxs-lookup"><span data-stu-id="44fc0-1737">EC45</span></span></td>
  <td><span data-ttu-id="44fc0-1738">LanguageJpn</span><span class="sxs-lookup"><span data-stu-id="44fc0-1738">LanguageJpn</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC46.png" width="32" height="32" alt="MobQuietHours" /></td>
  <td><span data-ttu-id="44fc0-1739">EC46</span><span class="sxs-lookup"><span data-stu-id="44fc0-1739">EC46</span></span></td>
  <td><span data-ttu-id="44fc0-1740">MobQuietHours</span><span class="sxs-lookup"><span data-stu-id="44fc0-1740">MobQuietHours</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC47.png" width="32" height="32" alt="MobDrivingMode" /></td>
  <td><span data-ttu-id="44fc0-1741">EC47</span><span class="sxs-lookup"><span data-stu-id="44fc0-1741">EC47</span></span></td>
  <td><span data-ttu-id="44fc0-1742">MobDrivingMode</span><span class="sxs-lookup"><span data-stu-id="44fc0-1742">MobDrivingMode</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC48.png" width="32" height="32" alt="SpeedOff" /></td>
  <td><span data-ttu-id="44fc0-1743">EC48</span><span class="sxs-lookup"><span data-stu-id="44fc0-1743">EC48</span></span></td>
  <td><span data-ttu-id="44fc0-1744">SpeedOff</span><span class="sxs-lookup"><span data-stu-id="44fc0-1744">SpeedOff</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC49.png" width="32" height="32" alt="SpeedMedium" /></td>
  <td><span data-ttu-id="44fc0-1745">EC49</span><span class="sxs-lookup"><span data-stu-id="44fc0-1745">EC49</span></span></td>
  <td><span data-ttu-id="44fc0-1746">SpeedMedium</span><span class="sxs-lookup"><span data-stu-id="44fc0-1746">SpeedMedium</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC4A.png" width="32" height="32" alt="SpeedHigh" /></td>
  <td><span data-ttu-id="44fc0-1747">EC4A</span><span class="sxs-lookup"><span data-stu-id="44fc0-1747">EC4A</span></span></td>
  <td><span data-ttu-id="44fc0-1748">SpeedHigh</span><span class="sxs-lookup"><span data-stu-id="44fc0-1748">SpeedHigh</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC4E.png" width="32" height="32" alt="ThisPC" /></td>
  <td><span data-ttu-id="44fc0-1749">EC4E</span><span class="sxs-lookup"><span data-stu-id="44fc0-1749">EC4E</span></span></td>
  <td><span data-ttu-id="44fc0-1750">ThisPC</span><span class="sxs-lookup"><span data-stu-id="44fc0-1750">ThisPC</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC4F.png" width="32" height="32" alt="MusicNote" /></td>
  <td><span data-ttu-id="44fc0-1751">EC4F</span><span class="sxs-lookup"><span data-stu-id="44fc0-1751">EC4F</span></span></td>
  <td><span data-ttu-id="44fc0-1752">MusicNote</span><span class="sxs-lookup"><span data-stu-id="44fc0-1752">MusicNote</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC50.png" width="32" height="32" alt="FileExplorer" /></td>
  <td><span data-ttu-id="44fc0-1753">EC50</span><span class="sxs-lookup"><span data-stu-id="44fc0-1753">EC50</span></span></td>
  <td><span data-ttu-id="44fc0-1754">FileExplorer</span><span class="sxs-lookup"><span data-stu-id="44fc0-1754">FileExplorer</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC51.png" width="32" height="32" alt="FileExplorerApp" /></td>
  <td><span data-ttu-id="44fc0-1755">EC51</span><span class="sxs-lookup"><span data-stu-id="44fc0-1755">EC51</span></span></td>
  <td><span data-ttu-id="44fc0-1756">FileExplorerApp</span><span class="sxs-lookup"><span data-stu-id="44fc0-1756">FileExplorerApp</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC52.png" width="32" height="32" alt="LeftArrowKeyTime0" /></td>
  <td><span data-ttu-id="44fc0-1757">EC52</span><span class="sxs-lookup"><span data-stu-id="44fc0-1757">EC52</span></span></td>
  <td><span data-ttu-id="44fc0-1758">LeftArrowKeyTime0</span><span class="sxs-lookup"><span data-stu-id="44fc0-1758">LeftArrowKeyTime0</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC54.png" width="32" height="32" alt="MicOff" /></td>
  <td><span data-ttu-id="44fc0-1759">EC54</span><span class="sxs-lookup"><span data-stu-id="44fc0-1759">EC54</span></span></td>
  <td><span data-ttu-id="44fc0-1760">MicOff</span><span class="sxs-lookup"><span data-stu-id="44fc0-1760">MicOff</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC55.png" width="32" height="32" alt="MicSleep" /></td>
  <td><span data-ttu-id="44fc0-1761">EC55</span><span class="sxs-lookup"><span data-stu-id="44fc0-1761">EC55</span></span></td>
  <td><span data-ttu-id="44fc0-1762">MicSleep</span><span class="sxs-lookup"><span data-stu-id="44fc0-1762">MicSleep</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC56.png" width="32" height="32" alt="MicError" /></td>
  <td><span data-ttu-id="44fc0-1763">EC56</span><span class="sxs-lookup"><span data-stu-id="44fc0-1763">EC56</span></span></td>
  <td><span data-ttu-id="44fc0-1764">MicError</span><span class="sxs-lookup"><span data-stu-id="44fc0-1764">MicError</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC57.png" width="32" height="32" alt="PlaybackRate1x" /></td>
  <td><span data-ttu-id="44fc0-1765">EC57</span><span class="sxs-lookup"><span data-stu-id="44fc0-1765">EC57</span></span></td>
  <td><span data-ttu-id="44fc0-1766">PlaybackRate1x</span><span class="sxs-lookup"><span data-stu-id="44fc0-1766">PlaybackRate1x</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC58.png" width="32" height="32" alt="PlaybackRateOther" /></td>
  <td><span data-ttu-id="44fc0-1767">EC58</span><span class="sxs-lookup"><span data-stu-id="44fc0-1767">EC58</span></span></td>
  <td><span data-ttu-id="44fc0-1768">PlaybackRateOther</span><span class="sxs-lookup"><span data-stu-id="44fc0-1768">PlaybackRateOther</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC59.png" width="32" height="32" alt="CashDrawer" /></td>
  <td><span data-ttu-id="44fc0-1769">EC59</span><span class="sxs-lookup"><span data-stu-id="44fc0-1769">EC59</span></span></td>
  <td><span data-ttu-id="44fc0-1770">CashDrawer</span><span class="sxs-lookup"><span data-stu-id="44fc0-1770">CashDrawer</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC5A.png" width="32" height="32" alt="BarcodeScanner" /></td>
  <td><span data-ttu-id="44fc0-1771">EC5A</span><span class="sxs-lookup"><span data-stu-id="44fc0-1771">EC5A</span></span></td>
  <td><span data-ttu-id="44fc0-1772">BarcodeScanner</span><span class="sxs-lookup"><span data-stu-id="44fc0-1772">BarcodeScanner</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC5B.png" width="32" height="32" alt="ReceiptPrinter" /></td>
  <td><span data-ttu-id="44fc0-1773">EC5B</span><span class="sxs-lookup"><span data-stu-id="44fc0-1773">EC5B</span></span></td>
  <td><span data-ttu-id="44fc0-1774">ReceiptPrinter</span><span class="sxs-lookup"><span data-stu-id="44fc0-1774">ReceiptPrinter</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC5C.png" width="32" height="32" alt="MagStripeReader" /></td>
  <td><span data-ttu-id="44fc0-1775">EC5C</span><span class="sxs-lookup"><span data-stu-id="44fc0-1775">EC5C</span></span></td>
  <td><span data-ttu-id="44fc0-1776">MagStripeReader</span><span class="sxs-lookup"><span data-stu-id="44fc0-1776">MagStripeReader</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC61.png" width="32" height="32" alt="CompletedSolid" /></td>
  <td><span data-ttu-id="44fc0-1777">EC61</span><span class="sxs-lookup"><span data-stu-id="44fc0-1777">EC61</span></span></td>
  <td><span data-ttu-id="44fc0-1778">CompletedSolid</span><span class="sxs-lookup"><span data-stu-id="44fc0-1778">CompletedSolid</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC64.png" width="32" height="32" alt="CompanionApp" /></td>
  <td><span data-ttu-id="44fc0-1779">EC64</span><span class="sxs-lookup"><span data-stu-id="44fc0-1779">EC64</span></span></td>
  <td><span data-ttu-id="44fc0-1780">CompanionApp</span><span class="sxs-lookup"><span data-stu-id="44fc0-1780">CompanionApp</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC6D.png" width="32" height="32" alt="SwipeRevealArt" /></td>
  <td><span data-ttu-id="44fc0-1781">EC6D</span><span class="sxs-lookup"><span data-stu-id="44fc0-1781">EC6D</span></span></td>
  <td><span data-ttu-id="44fc0-1782">SwipeRevealArt</span><span class="sxs-lookup"><span data-stu-id="44fc0-1782">SwipeRevealArt</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC71.png" width="32" height="32" alt="MicOn" /></td>
  <td><span data-ttu-id="44fc0-1783">EC71</span><span class="sxs-lookup"><span data-stu-id="44fc0-1783">EC71</span></span></td>
  <td><span data-ttu-id="44fc0-1784">MicOn</span><span class="sxs-lookup"><span data-stu-id="44fc0-1784">MicOn</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC72.png" width="32" height="32" alt="MicClipping" /></td>
  <td><span data-ttu-id="44fc0-1785">EC72</span><span class="sxs-lookup"><span data-stu-id="44fc0-1785">EC72</span></span></td>
  <td><span data-ttu-id="44fc0-1786">MicClipping</span><span class="sxs-lookup"><span data-stu-id="44fc0-1786">MicClipping</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC74.png" width="32" height="32" alt="TabletSelected" /></td>
  <td><span data-ttu-id="44fc0-1787">EC74</span><span class="sxs-lookup"><span data-stu-id="44fc0-1787">EC74</span></span></td>
  <td><span data-ttu-id="44fc0-1788">TabletSelected</span><span class="sxs-lookup"><span data-stu-id="44fc0-1788">TabletSelected</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC75.png" width="32" height="32" alt="MobileSelected" /></td>
  <td><span data-ttu-id="44fc0-1789">EC75</span><span class="sxs-lookup"><span data-stu-id="44fc0-1789">EC75</span></span></td>
  <td><span data-ttu-id="44fc0-1790">MobileSelected</span><span class="sxs-lookup"><span data-stu-id="44fc0-1790">MobileSelected</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC76.png" width="32" height="32" alt="LaptopSelected" /></td>
  <td><span data-ttu-id="44fc0-1791">EC76</span><span class="sxs-lookup"><span data-stu-id="44fc0-1791">EC76</span></span></td>
  <td><span data-ttu-id="44fc0-1792">LaptopSelected</span><span class="sxs-lookup"><span data-stu-id="44fc0-1792">LaptopSelected</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC77.png" width="32" height="32" alt="TVMonitorSelected" /></td>
  <td><span data-ttu-id="44fc0-1793">EC77</span><span class="sxs-lookup"><span data-stu-id="44fc0-1793">EC77</span></span></td>
  <td><span data-ttu-id="44fc0-1794">TVMonitorSelected</span><span class="sxs-lookup"><span data-stu-id="44fc0-1794">TVMonitorSelected</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC7A.png" width="32" height="32" alt="DeveloperTools" /></td>
  <td><span data-ttu-id="44fc0-1795">EC7A</span><span class="sxs-lookup"><span data-stu-id="44fc0-1795">EC7A</span></span></td>
  <td><span data-ttu-id="44fc0-1796">DeveloperTools</span><span class="sxs-lookup"><span data-stu-id="44fc0-1796">DeveloperTools</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC7E.png" width="32" height="32" alt="MobCallForwarding" /></td>
  <td><span data-ttu-id="44fc0-1797">EC7E</span><span class="sxs-lookup"><span data-stu-id="44fc0-1797">EC7E</span></span></td>
  <td><span data-ttu-id="44fc0-1798">MobCallForwarding</span><span class="sxs-lookup"><span data-stu-id="44fc0-1798">MobCallForwarding</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC7F.png" width="32" height="32" alt="MobCallForwardingMirrored" /></td>
  <td><span data-ttu-id="44fc0-1799">EC7F</span><span class="sxs-lookup"><span data-stu-id="44fc0-1799">EC7F</span></span></td>
  <td><span data-ttu-id="44fc0-1800">MobCallForwardingMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1800">MobCallForwardingMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC80.png" width="32" height="32" alt="BodyCam" /></td>
  <td><span data-ttu-id="44fc0-1801">EC80</span><span class="sxs-lookup"><span data-stu-id="44fc0-1801">EC80</span></span></td>
  <td><span data-ttu-id="44fc0-1802">BodyCam</span><span class="sxs-lookup"><span data-stu-id="44fc0-1802">BodyCam</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC81.png" width="32" height="32" alt="PoliceCar" /></td>
  <td><span data-ttu-id="44fc0-1803">EC81</span><span class="sxs-lookup"><span data-stu-id="44fc0-1803">EC81</span></span></td>
  <td><span data-ttu-id="44fc0-1804">PoliceCar</span><span class="sxs-lookup"><span data-stu-id="44fc0-1804">PoliceCar</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC87.png" width="32" height="32" alt="Draw" /></td>
  <td><span data-ttu-id="44fc0-1805">EC87</span><span class="sxs-lookup"><span data-stu-id="44fc0-1805">EC87</span></span></td>
  <td><span data-ttu-id="44fc0-1806">Draw</span><span class="sxs-lookup"><span data-stu-id="44fc0-1806">Draw</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC88.png" width="32" height="32" alt="DrawSolid" /></td>
  <td><span data-ttu-id="44fc0-1807">EC88</span><span class="sxs-lookup"><span data-stu-id="44fc0-1807">EC88</span></span></td>
  <td><span data-ttu-id="44fc0-1808">DrawSolid</span><span class="sxs-lookup"><span data-stu-id="44fc0-1808">DrawSolid</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC8A.png" width="32" height="32" alt="LowerBrightness" /></td>
  <td><span data-ttu-id="44fc0-1809">EC8A</span><span class="sxs-lookup"><span data-stu-id="44fc0-1809">EC8A</span></span></td>
  <td><span data-ttu-id="44fc0-1810">LowerBrightness</span><span class="sxs-lookup"><span data-stu-id="44fc0-1810">LowerBrightness</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC8F.png" width="32" height="32" alt="ScrollUpDown" /></td>
  <td><span data-ttu-id="44fc0-1811">EC8F</span><span class="sxs-lookup"><span data-stu-id="44fc0-1811">EC8F</span></span></td>
  <td><span data-ttu-id="44fc0-1812">ScrollUpDown</span><span class="sxs-lookup"><span data-stu-id="44fc0-1812">ScrollUpDown</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EC92.png" width="32" height="32" alt="DateTime" /></td>
  <td><span data-ttu-id="44fc0-1813">EC92</span><span class="sxs-lookup"><span data-stu-id="44fc0-1813">EC92</span></span></td>
  <td><span data-ttu-id="44fc0-1814">DateTime</span><span class="sxs-lookup"><span data-stu-id="44fc0-1814">DateTime</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ECA5.png" width="32" height="32" alt="Tiles" /></td>
  <td><span data-ttu-id="44fc0-1815">ECA5</span><span class="sxs-lookup"><span data-stu-id="44fc0-1815">ECA5</span></span></td>
  <td><span data-ttu-id="44fc0-1816">Kacheln</span><span class="sxs-lookup"><span data-stu-id="44fc0-1816">Tiles</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ECA7.png" width="32" height="32" alt="PartyLeader" /></td>
  <td><span data-ttu-id="44fc0-1817">ECA7</span><span class="sxs-lookup"><span data-stu-id="44fc0-1817">ECA7</span></span></td>
  <td><span data-ttu-id="44fc0-1818">PartyLeader</span><span class="sxs-lookup"><span data-stu-id="44fc0-1818">PartyLeader</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ECAA.png" width="32" height="32" alt="AppIconDefault" /></td>
  <td><span data-ttu-id="44fc0-1819">ECAA</span><span class="sxs-lookup"><span data-stu-id="44fc0-1819">ECAA</span></span></td>
  <td><span data-ttu-id="44fc0-1820">AppIconDefault</span><span class="sxs-lookup"><span data-stu-id="44fc0-1820">AppIconDefault</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ECAD.png" width="32" height="32" alt="Calories" /></td>
  <td><span data-ttu-id="44fc0-1821">ECAD</span><span class="sxs-lookup"><span data-stu-id="44fc0-1821">ECAD</span></span></td>
  <td><span data-ttu-id="44fc0-1822">Kalorienverbrauch</span><span class="sxs-lookup"><span data-stu-id="44fc0-1822">Calories</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ECB9.png" width="32" height="32" alt="BandBattery0" /></td>
  <td><span data-ttu-id="44fc0-1823">ECB9</span><span class="sxs-lookup"><span data-stu-id="44fc0-1823">ECB9</span></span></td>
  <td><span data-ttu-id="44fc0-1824">BandBattery0</span><span class="sxs-lookup"><span data-stu-id="44fc0-1824">BandBattery0</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ECBA.png" width="32" height="32" alt="BandBattery1" /></td>
  <td><span data-ttu-id="44fc0-1825">ECBA</span><span class="sxs-lookup"><span data-stu-id="44fc0-1825">ECBA</span></span></td>
  <td><span data-ttu-id="44fc0-1826">BandBattery1</span><span class="sxs-lookup"><span data-stu-id="44fc0-1826">BandBattery1</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ECBB.png" width="32" height="32" alt="BandBattery2" /></td>
  <td><span data-ttu-id="44fc0-1827">ECBB</span><span class="sxs-lookup"><span data-stu-id="44fc0-1827">ECBB</span></span></td>
  <td><span data-ttu-id="44fc0-1828">BandBattery2</span><span class="sxs-lookup"><span data-stu-id="44fc0-1828">BandBattery2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ECBC.png" width="32" height="32" alt="BandBattery3" /></td>
  <td><span data-ttu-id="44fc0-1829">ECBC</span><span class="sxs-lookup"><span data-stu-id="44fc0-1829">ECBC</span></span></td>
  <td><span data-ttu-id="44fc0-1830">BandBattery3</span><span class="sxs-lookup"><span data-stu-id="44fc0-1830">BandBattery3</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ECBD.png" width="32" height="32" alt="BandBattery4" /></td>
  <td><span data-ttu-id="44fc0-1831">ECBD</span><span class="sxs-lookup"><span data-stu-id="44fc0-1831">ECBD</span></span></td>
  <td><span data-ttu-id="44fc0-1832">BandBattery4</span><span class="sxs-lookup"><span data-stu-id="44fc0-1832">BandBattery4</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ECBE.png" width="32" height="32" alt="BandBattery5" /></td>
  <td><span data-ttu-id="44fc0-1833">ECBE</span><span class="sxs-lookup"><span data-stu-id="44fc0-1833">ECBE</span></span></td>
  <td><span data-ttu-id="44fc0-1834">BandBattery5</span><span class="sxs-lookup"><span data-stu-id="44fc0-1834">BandBattery5</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ECBF.png" width="32" height="32" alt="BandBattery6" /></td>
  <td><span data-ttu-id="44fc0-1835">ECBF</span><span class="sxs-lookup"><span data-stu-id="44fc0-1835">ECBF</span></span></td>
  <td><span data-ttu-id="44fc0-1836">BandBattery6</span><span class="sxs-lookup"><span data-stu-id="44fc0-1836">BandBattery6</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ECC4.png" width="32" height="32" alt="AddSurfaceHub" /></td>
  <td><span data-ttu-id="44fc0-1837">ECC4</span><span class="sxs-lookup"><span data-stu-id="44fc0-1837">ECC4</span></span></td>
  <td><span data-ttu-id="44fc0-1838">AddSurfaceHub</span><span class="sxs-lookup"><span data-stu-id="44fc0-1838">AddSurfaceHub</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ECC5.png" width="32" height="32" alt="DevUpdate" /></td>
  <td><span data-ttu-id="44fc0-1839">ECC5</span><span class="sxs-lookup"><span data-stu-id="44fc0-1839">ECC5</span></span></td>
  <td><span data-ttu-id="44fc0-1840">DevUpdate</span><span class="sxs-lookup"><span data-stu-id="44fc0-1840">DevUpdate</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ECC6.png" width="32" height="32" alt="Unit" /></td>
  <td><span data-ttu-id="44fc0-1841">ECC6</span><span class="sxs-lookup"><span data-stu-id="44fc0-1841">ECC6</span></span></td>
  <td><span data-ttu-id="44fc0-1842">Einheit</span><span class="sxs-lookup"><span data-stu-id="44fc0-1842">Unit</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ECC8.png" width="32" height="32" alt="AddTo" /></td>
  <td><span data-ttu-id="44fc0-1843">ECC8</span><span class="sxs-lookup"><span data-stu-id="44fc0-1843">ECC8</span></span></td>
  <td><span data-ttu-id="44fc0-1844">AddTo</span><span class="sxs-lookup"><span data-stu-id="44fc0-1844">AddTo</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ECC9.png" width="32" height="32" alt="RemoveFrom" /></td>
  <td><span data-ttu-id="44fc0-1845">ECC9</span><span class="sxs-lookup"><span data-stu-id="44fc0-1845">ECC9</span></span></td>
  <td><span data-ttu-id="44fc0-1846">RemoveFrom</span><span class="sxs-lookup"><span data-stu-id="44fc0-1846">RemoveFrom</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ECCA.png" width="32" height="32" alt="RadioBtnOff" /></td>
  <td><span data-ttu-id="44fc0-1847">ECCA</span><span class="sxs-lookup"><span data-stu-id="44fc0-1847">ECCA</span></span></td>
  <td><span data-ttu-id="44fc0-1848">RadioBtnOff</span><span class="sxs-lookup"><span data-stu-id="44fc0-1848">RadioBtnOff</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ECCB.png" width="32" height="32" alt="RadioBtnOn" /></td>
  <td><span data-ttu-id="44fc0-1849">ECCB</span><span class="sxs-lookup"><span data-stu-id="44fc0-1849">ECCB</span></span></td>
  <td><span data-ttu-id="44fc0-1850">RadioBtnOn</span><span class="sxs-lookup"><span data-stu-id="44fc0-1850">RadioBtnOn</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ECCC.png" width="32" height="32" alt="RadioBullet2" /></td>
  <td><span data-ttu-id="44fc0-1851">ECCC</span><span class="sxs-lookup"><span data-stu-id="44fc0-1851">ECCC</span></span></td>
  <td><span data-ttu-id="44fc0-1852">RadioBullet2</span><span class="sxs-lookup"><span data-stu-id="44fc0-1852">RadioBullet2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ECCD.png" width="32" height="32" alt="ExploreContent" /></td>
  <td><span data-ttu-id="44fc0-1853">ECCD</span><span class="sxs-lookup"><span data-stu-id="44fc0-1853">ECCD</span></span></td>
  <td><span data-ttu-id="44fc0-1854">ExploreContent</span><span class="sxs-lookup"><span data-stu-id="44fc0-1854">ExploreContent</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ECE7.png" width="32" height="32" alt="ScrollMode" /></td>
  <td><span data-ttu-id="44fc0-1855">ECE7</span><span class="sxs-lookup"><span data-stu-id="44fc0-1855">ECE7</span></span></td>
  <td><span data-ttu-id="44fc0-1856">ScrollMode</span><span class="sxs-lookup"><span data-stu-id="44fc0-1856">ScrollMode</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ECE8.png" width="32" height="32" alt="ZoomMode" /></td>
  <td><span data-ttu-id="44fc0-1857">ECE8</span><span class="sxs-lookup"><span data-stu-id="44fc0-1857">ECE8</span></span></td>
  <td><span data-ttu-id="44fc0-1858">ZoomMode</span><span class="sxs-lookup"><span data-stu-id="44fc0-1858">ZoomMode</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ECE9.png" width="32" height="32" alt="PanMode" /></td>
  <td><span data-ttu-id="44fc0-1859">ECE9</span><span class="sxs-lookup"><span data-stu-id="44fc0-1859">ECE9</span></span></td>
  <td><span data-ttu-id="44fc0-1860">PanMode</span><span class="sxs-lookup"><span data-stu-id="44fc0-1860">PanMode</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ECF0.png" width="32" height="32" alt="WiredUSB  " /></td>
  <td><span data-ttu-id="44fc0-1861">ECF0</span><span class="sxs-lookup"><span data-stu-id="44fc0-1861">ECF0</span></span></td>
  <td><span data-ttu-id="44fc0-1862">WiredUSB</span><span class="sxs-lookup"><span data-stu-id="44fc0-1862">WiredUSB</span></span>  </td>
 </tr>
<tr><td><img src="images/segoe-mdl/ECF1.png" width="32" height="32" alt="WirelessUSB" /></td>
  <td><span data-ttu-id="44fc0-1863">ECF1</span><span class="sxs-lookup"><span data-stu-id="44fc0-1863">ECF1</span></span></td>
  <td><span data-ttu-id="44fc0-1864">WirelessUSB</span><span class="sxs-lookup"><span data-stu-id="44fc0-1864">WirelessUSB</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ECF3.png" width="32" height="32" alt="USBSafeConnect" /></td>
  <td><span data-ttu-id="44fc0-1865">ECF3</span><span class="sxs-lookup"><span data-stu-id="44fc0-1865">ECF3</span></span></td>
  <td><span data-ttu-id="44fc0-1866">USBSafeConnect</span><span class="sxs-lookup"><span data-stu-id="44fc0-1866">USBSafeConnect</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED0C.png" width="32" height="32" alt="ActionCenterNotificationMirrored" /></td>
  <td><span data-ttu-id="44fc0-1867">ED0C</span><span class="sxs-lookup"><span data-stu-id="44fc0-1867">ED0C</span></span></td>
  <td><span data-ttu-id="44fc0-1868">ActionCenterNotificationMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1868">ActionCenterNotificationMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED0D.png" width="32" height="32" alt="ActionCenterMirrored" /></td>
  <td><span data-ttu-id="44fc0-1869">ED0D</span><span class="sxs-lookup"><span data-stu-id="44fc0-1869">ED0D</span></span></td>
  <td><span data-ttu-id="44fc0-1870">ActionCenterMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1870">ActionCenterMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED10.png" width="32" height="32" alt="ResetDevice" /></td>
  <td><span data-ttu-id="44fc0-1871">ED10</span><span class="sxs-lookup"><span data-stu-id="44fc0-1871">ED10</span></span></td>
  <td><span data-ttu-id="44fc0-1872">ResetDevice</span><span class="sxs-lookup"><span data-stu-id="44fc0-1872">ResetDevice</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED15.png" width="32" height="32" alt="Feedback" /></td>
  <td><span data-ttu-id="44fc0-1873">ED15</span><span class="sxs-lookup"><span data-stu-id="44fc0-1873">ED15</span></span></td>
  <td><span data-ttu-id="44fc0-1874">Feedback</span><span class="sxs-lookup"><span data-stu-id="44fc0-1874">Feedback</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED1E.png" width="32" height="32" alt="Subtitles" /></td>
  <td><span data-ttu-id="44fc0-1875">ED1E</span><span class="sxs-lookup"><span data-stu-id="44fc0-1875">ED1E</span></span></td>
  <td><span data-ttu-id="44fc0-1876">Subtitles</span><span class="sxs-lookup"><span data-stu-id="44fc0-1876">Subtitles</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED1F.png" width="32" height="32" alt="SubtitlesAudio" /></td>
  <td><span data-ttu-id="44fc0-1877">ED1F</span><span class="sxs-lookup"><span data-stu-id="44fc0-1877">ED1F</span></span></td>
  <td><span data-ttu-id="44fc0-1878">SubtitlesAudio</span><span class="sxs-lookup"><span data-stu-id="44fc0-1878">SubtitlesAudio</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED25.png" width="32" height="32" alt="OpenFolderHorizontal" /></td>
  <td><span data-ttu-id="44fc0-1879">ED25</span><span class="sxs-lookup"><span data-stu-id="44fc0-1879">ED25</span></span></td>
  <td><span data-ttu-id="44fc0-1880">OpenFolderHorizontal</span><span class="sxs-lookup"><span data-stu-id="44fc0-1880">OpenFolderHorizontal</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED28.png" width="32" height="32" alt="CalendarMirrored" /></td>
  <td><span data-ttu-id="44fc0-1881">ED28</span><span class="sxs-lookup"><span data-stu-id="44fc0-1881">ED28</span></span></td>
  <td><span data-ttu-id="44fc0-1882">CalendarMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1882">CalendarMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED2A.png" width="32" height="32" alt="MobeSIM" /></td>
  <td><span data-ttu-id="44fc0-1883">ED2A</span><span class="sxs-lookup"><span data-stu-id="44fc0-1883">ED2A</span></span></td>
  <td><span data-ttu-id="44fc0-1884">MobeSIM</span><span class="sxs-lookup"><span data-stu-id="44fc0-1884">MobeSIM</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED2B.png" width="32" height="32" alt="MobeSIMNoProfile" /></td>
  <td><span data-ttu-id="44fc0-1885">ED2B</span><span class="sxs-lookup"><span data-stu-id="44fc0-1885">ED2B</span></span></td>
  <td><span data-ttu-id="44fc0-1886">MobeSIMNoProfile</span><span class="sxs-lookup"><span data-stu-id="44fc0-1886">MobeSIMNoProfile</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED2C.png" width="32" height="32" alt="MobeSIMLocked" /></td>
  <td><span data-ttu-id="44fc0-1887">ED2C</span><span class="sxs-lookup"><span data-stu-id="44fc0-1887">ED2C</span></span></td>
  <td><span data-ttu-id="44fc0-1888">MobeSIMLocked</span><span class="sxs-lookup"><span data-stu-id="44fc0-1888">MobeSIMLocked</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED2D.png" width="32" height="32" alt="MobeSIMBusy" /></td>
  <td><span data-ttu-id="44fc0-1889">ED2D</span><span class="sxs-lookup"><span data-stu-id="44fc0-1889">ED2D</span></span></td>
  <td><span data-ttu-id="44fc0-1890">MobeSIMBusy</span><span class="sxs-lookup"><span data-stu-id="44fc0-1890">MobeSIMBusy</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED2E.png" width="32" height="32" alt="SignalError" /></td>
  <td><span data-ttu-id="44fc0-1891">ED2E</span><span class="sxs-lookup"><span data-stu-id="44fc0-1891">ED2E</span></span></td>
  <td><span data-ttu-id="44fc0-1892">SignalError</span><span class="sxs-lookup"><span data-stu-id="44fc0-1892">SignalError</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED2F.png" width="32" height="32" alt="StreamingEnterprise" /></td>
  <td><span data-ttu-id="44fc0-1893">ED2F</span><span class="sxs-lookup"><span data-stu-id="44fc0-1893">ED2F</span></span></td>
  <td><span data-ttu-id="44fc0-1894">StreamingEnterprise</span><span class="sxs-lookup"><span data-stu-id="44fc0-1894">StreamingEnterprise</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED30.png" width="32" height="32" alt="Headphone0" /></td>
  <td><span data-ttu-id="44fc0-1895">ED30</span><span class="sxs-lookup"><span data-stu-id="44fc0-1895">ED30</span></span></td>
  <td><span data-ttu-id="44fc0-1896">Headphone0</span><span class="sxs-lookup"><span data-stu-id="44fc0-1896">Headphone0</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED31.png" width="32" height="32" alt="Headphone1" /></td>
  <td><span data-ttu-id="44fc0-1897">ED31</span><span class="sxs-lookup"><span data-stu-id="44fc0-1897">ED31</span></span></td>
  <td><span data-ttu-id="44fc0-1898">Headphone1</span><span class="sxs-lookup"><span data-stu-id="44fc0-1898">Headphone1</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED32.png" width="32" height="32" alt="Headphone2" /></td>
  <td><span data-ttu-id="44fc0-1899">ED32</span><span class="sxs-lookup"><span data-stu-id="44fc0-1899">ED32</span></span></td>
  <td><span data-ttu-id="44fc0-1900">Headphone2</span><span class="sxs-lookup"><span data-stu-id="44fc0-1900">Headphone2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED33.png" width="32" height="32" alt="Headphone3" /></td>
  <td><span data-ttu-id="44fc0-1901">ED33</span><span class="sxs-lookup"><span data-stu-id="44fc0-1901">ED33</span></span></td>
  <td><span data-ttu-id="44fc0-1902">Headphone3</span><span class="sxs-lookup"><span data-stu-id="44fc0-1902">Headphone3</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED35.png" width="32" height="32" alt="Apps" /></td>
  <td><span data-ttu-id="44fc0-1903">ED35</span><span class="sxs-lookup"><span data-stu-id="44fc0-1903">ED35</span></span></td>
  <td><span data-ttu-id="44fc0-1904">Apps</span><span class="sxs-lookup"><span data-stu-id="44fc0-1904">Apps</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED39.png" width="32" height="32" alt="KeyboardBrightness" /></td>
  <td><span data-ttu-id="44fc0-1905">ED39</span><span class="sxs-lookup"><span data-stu-id="44fc0-1905">ED39</span></span></td>
  <td><span data-ttu-id="44fc0-1906">KeyboardBrightness</span><span class="sxs-lookup"><span data-stu-id="44fc0-1906">KeyboardBrightness</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED3A.png" width="32" height="32" alt="KeyboardLowerBrightness" /></td>
  <td><span data-ttu-id="44fc0-1907">ED3A</span><span class="sxs-lookup"><span data-stu-id="44fc0-1907">ED3A</span></span></td>
  <td><span data-ttu-id="44fc0-1908">KeyboardLowerBrightness</span><span class="sxs-lookup"><span data-stu-id="44fc0-1908">KeyboardLowerBrightness</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED3C.png" width="32" height="32" alt="SkipBack10" /></td>
  <td><span data-ttu-id="44fc0-1909">ED3C</span><span class="sxs-lookup"><span data-stu-id="44fc0-1909">ED3C</span></span></td>
  <td><span data-ttu-id="44fc0-1910">SkipBack10</span><span class="sxs-lookup"><span data-stu-id="44fc0-1910">SkipBack10</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED3D.png" width="32" height="32" alt="SkipForward30 " /></td>
  <td><span data-ttu-id="44fc0-1911">ED3D</span><span class="sxs-lookup"><span data-stu-id="44fc0-1911">ED3D</span></span></td>
  <td><span data-ttu-id="44fc0-1912">SkipForward30</span><span class="sxs-lookup"><span data-stu-id="44fc0-1912">SkipForward30</span></span> </td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED41.png" width="32" height="32" alt="TreeFolderFolder" /></td>
  <td><span data-ttu-id="44fc0-1913">ED41</span><span class="sxs-lookup"><span data-stu-id="44fc0-1913">ED41</span></span></td>
  <td><span data-ttu-id="44fc0-1914">TreeFolderFolder</span><span class="sxs-lookup"><span data-stu-id="44fc0-1914">TreeFolderFolder</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED42.png" width="32" height="32" alt="TreeFolderFolderFill" /></td>
  <td><span data-ttu-id="44fc0-1915">ED42</span><span class="sxs-lookup"><span data-stu-id="44fc0-1915">ED42</span></span></td>
  <td><span data-ttu-id="44fc0-1916">TreeFolderFolderFill</span><span class="sxs-lookup"><span data-stu-id="44fc0-1916">TreeFolderFolderFill</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED43.png" width="32" height="32" alt="TreeFolderFolderOpen" /></td>
  <td><span data-ttu-id="44fc0-1917">ED43</span><span class="sxs-lookup"><span data-stu-id="44fc0-1917">ED43</span></span></td>
  <td><span data-ttu-id="44fc0-1918">TreeFolderFolderOpen</span><span class="sxs-lookup"><span data-stu-id="44fc0-1918">TreeFolderFolderOpen</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED44.png" width="32" height="32" alt="TreeFolderFolderOpenFill" /></td>
  <td><span data-ttu-id="44fc0-1919">ED44</span><span class="sxs-lookup"><span data-stu-id="44fc0-1919">ED44</span></span></td>
  <td><span data-ttu-id="44fc0-1920">TreeFolderFolderOpenFill</span><span class="sxs-lookup"><span data-stu-id="44fc0-1920">TreeFolderFolderOpenFill</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED47.png" width="32" height="32" alt="MultimediaDMP" /></td>
  <td><span data-ttu-id="44fc0-1921">ED47</span><span class="sxs-lookup"><span data-stu-id="44fc0-1921">ED47</span></span></td>
  <td><span data-ttu-id="44fc0-1922">MultimediaDMP</span><span class="sxs-lookup"><span data-stu-id="44fc0-1922">MultimediaDMP</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED4C.png" width="32" height="32" alt="KeyboardOneHanded" /></td>
  <td><span data-ttu-id="44fc0-1923">ED4C</span><span class="sxs-lookup"><span data-stu-id="44fc0-1923">ED4C</span></span></td>
  <td><span data-ttu-id="44fc0-1924">KeyboardOneHanded</span><span class="sxs-lookup"><span data-stu-id="44fc0-1924">KeyboardOneHanded</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED4D.png" width="32" height="32" alt="Narrator" /></td>
  <td><span data-ttu-id="44fc0-1925">ED4D</span><span class="sxs-lookup"><span data-stu-id="44fc0-1925">ED4D</span></span></td>
  <td><span data-ttu-id="44fc0-1926">Sprachausgabe</span><span class="sxs-lookup"><span data-stu-id="44fc0-1926">Narrator</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED53.png" width="32" height="32" alt="EmojiTabPeople" /></td>
  <td><span data-ttu-id="44fc0-1927">ED53</span><span class="sxs-lookup"><span data-stu-id="44fc0-1927">ED53</span></span></td>
  <td><span data-ttu-id="44fc0-1928">EmojiTabPeople</span><span class="sxs-lookup"><span data-stu-id="44fc0-1928">EmojiTabPeople</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED54.png" width="32" height="32" alt="EmojiTabSmilesAnimals" /></td>
  <td><span data-ttu-id="44fc0-1929">ED54</span><span class="sxs-lookup"><span data-stu-id="44fc0-1929">ED54</span></span></td>
  <td><span data-ttu-id="44fc0-1930">EmojiTabSmilesAnimals</span><span class="sxs-lookup"><span data-stu-id="44fc0-1930">EmojiTabSmilesAnimals</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED55.png" width="32" height="32" alt="EmojiTabCelebrationObjects" /></td>
  <td><span data-ttu-id="44fc0-1931">ED55</span><span class="sxs-lookup"><span data-stu-id="44fc0-1931">ED55</span></span></td>
  <td><span data-ttu-id="44fc0-1932">EmojiTabCelebrationObjects</span><span class="sxs-lookup"><span data-stu-id="44fc0-1932">EmojiTabCelebrationObjects</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED56.png" width="32" height="32" alt="EmojiTabFoodPlants" /></td>
  <td><span data-ttu-id="44fc0-1933">ED56</span><span class="sxs-lookup"><span data-stu-id="44fc0-1933">ED56</span></span></td>
  <td><span data-ttu-id="44fc0-1934">EmojiTabFoodPlants</span><span class="sxs-lookup"><span data-stu-id="44fc0-1934">EmojiTabFoodPlants</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED57.png" width="32" height="32" alt="EmojiTabTransitPlaces" /></td>
  <td><span data-ttu-id="44fc0-1935">ED57</span><span class="sxs-lookup"><span data-stu-id="44fc0-1935">ED57</span></span></td>
  <td><span data-ttu-id="44fc0-1936">EmojiTabTransitPlaces</span><span class="sxs-lookup"><span data-stu-id="44fc0-1936">EmojiTabTransitPlaces</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED58.png" width="32" height="32" alt="EmojiTabSymbols" /></td>
  <td><span data-ttu-id="44fc0-1937">ED58</span><span class="sxs-lookup"><span data-stu-id="44fc0-1937">ED58</span></span></td>
  <td><span data-ttu-id="44fc0-1938">EmojiTabSymbols</span><span class="sxs-lookup"><span data-stu-id="44fc0-1938">EmojiTabSymbols</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED59.png" width="32" height="32" alt="EmojiTabTextSmiles" /></td>
  <td><span data-ttu-id="44fc0-1939">ED59</span><span class="sxs-lookup"><span data-stu-id="44fc0-1939">ED59</span></span></td>
  <td><span data-ttu-id="44fc0-1940">EmojiTabTextSmiles</span><span class="sxs-lookup"><span data-stu-id="44fc0-1940">EmojiTabTextSmiles</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED5A.png" width="32" height="32" alt="EmojiTabFavorites" /></td>
  <td><span data-ttu-id="44fc0-1941">ED5A</span><span class="sxs-lookup"><span data-stu-id="44fc0-1941">ED5A</span></span></td>
  <td><span data-ttu-id="44fc0-1942">EmojiTabFavorites</span><span class="sxs-lookup"><span data-stu-id="44fc0-1942">EmojiTabFavorites</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED5B.png" width="32" height="32" alt="EmojiSwatch" /></td>
  <td><span data-ttu-id="44fc0-1943">ED5B</span><span class="sxs-lookup"><span data-stu-id="44fc0-1943">ED5B</span></span></td>
  <td><span data-ttu-id="44fc0-1944">EmojiSwatch</span><span class="sxs-lookup"><span data-stu-id="44fc0-1944">EmojiSwatch</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED5C.png" width="32" height="32" alt="ConnectApp" /></td>
  <td><span data-ttu-id="44fc0-1945">ED5C</span><span class="sxs-lookup"><span data-stu-id="44fc0-1945">ED5C</span></span></td>
  <td><span data-ttu-id="44fc0-1946">ConnectApp</span><span class="sxs-lookup"><span data-stu-id="44fc0-1946">ConnectApp</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED5D.png" width="32" height="32" alt="CompanionDeviceFramework" /></td>
  <td><span data-ttu-id="44fc0-1947">ED5D</span><span class="sxs-lookup"><span data-stu-id="44fc0-1947">ED5D</span></span></td>
  <td><span data-ttu-id="44fc0-1948">CompanionDeviceFramework</span><span class="sxs-lookup"><span data-stu-id="44fc0-1948">CompanionDeviceFramework</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED5E.png" width="32" height="32" alt="Ruler" /></td>
  <td><span data-ttu-id="44fc0-1949">ED5E</span><span class="sxs-lookup"><span data-stu-id="44fc0-1949">ED5E</span></span></td>
  <td><span data-ttu-id="44fc0-1950">Ruler</span><span class="sxs-lookup"><span data-stu-id="44fc0-1950">Ruler</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED5F.png" width="32" height="32" alt="FingerInking" /></td>
  <td><span data-ttu-id="44fc0-1951">ED5F</span><span class="sxs-lookup"><span data-stu-id="44fc0-1951">ED5F</span></span></td>
  <td><span data-ttu-id="44fc0-1952">FingerInking</span><span class="sxs-lookup"><span data-stu-id="44fc0-1952">FingerInking</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED60.png" width="32" height="32" alt="StrokeErase" /></td>
  <td><span data-ttu-id="44fc0-1953">ED60</span><span class="sxs-lookup"><span data-stu-id="44fc0-1953">ED60</span></span></td>
  <td><span data-ttu-id="44fc0-1954">StrokeErase</span><span class="sxs-lookup"><span data-stu-id="44fc0-1954">StrokeErase</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED61.png" width="32" height="32" alt="PointErase" /></td>
  <td><span data-ttu-id="44fc0-1955">ED61</span><span class="sxs-lookup"><span data-stu-id="44fc0-1955">ED61</span></span></td>
  <td><span data-ttu-id="44fc0-1956">PointErase</span><span class="sxs-lookup"><span data-stu-id="44fc0-1956">PointErase</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED62.png" width="32" height="32" alt="ClearAllInk" /></td>
  <td><span data-ttu-id="44fc0-1957">ED62</span><span class="sxs-lookup"><span data-stu-id="44fc0-1957">ED62</span></span></td>
  <td><span data-ttu-id="44fc0-1958">ClearAllInk</span><span class="sxs-lookup"><span data-stu-id="44fc0-1958">ClearAllInk</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED63.png" width="32" height="32" alt="Pencil" /></td>
  <td><span data-ttu-id="44fc0-1959">ED63</span><span class="sxs-lookup"><span data-stu-id="44fc0-1959">ED63</span></span></td>
  <td><span data-ttu-id="44fc0-1960">Pencil</span><span class="sxs-lookup"><span data-stu-id="44fc0-1960">Pencil</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED64.png" width="32" height="32" alt="Marker" /></td>
  <td><span data-ttu-id="44fc0-1961">ED64</span><span class="sxs-lookup"><span data-stu-id="44fc0-1961">ED64</span></span></td>
  <td><span data-ttu-id="44fc0-1962">Marker</span><span class="sxs-lookup"><span data-stu-id="44fc0-1962">Marker</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED65.png" width="32" height="32" alt="InkingCaret" /></td>
  <td><span data-ttu-id="44fc0-1963">ED65</span><span class="sxs-lookup"><span data-stu-id="44fc0-1963">ED65</span></span></td>
  <td><span data-ttu-id="44fc0-1964">InkingCaret</span><span class="sxs-lookup"><span data-stu-id="44fc0-1964">InkingCaret</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED66.png" width="32" height="32" alt="InkingColorOutline" /></td>
  <td><span data-ttu-id="44fc0-1965">ED66</span><span class="sxs-lookup"><span data-stu-id="44fc0-1965">ED66</span></span></td>
  <td><span data-ttu-id="44fc0-1966">InkingColorOutline</span><span class="sxs-lookup"><span data-stu-id="44fc0-1966">InkingColorOutline</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/ED67.png" width="32" height="32" alt="InkingColorFill" /></td>
  <td><span data-ttu-id="44fc0-1967">ED67</span><span class="sxs-lookup"><span data-stu-id="44fc0-1967">ED67</span></span></td>
  <td><span data-ttu-id="44fc0-1968">InkingColorFill</span><span class="sxs-lookup"><span data-stu-id="44fc0-1968">InkingColorFill</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EDA2.png" width="32" height="32" alt="HardDrive" /></td>
  <td><span data-ttu-id="44fc0-1969">EDA2</span><span class="sxs-lookup"><span data-stu-id="44fc0-1969">EDA2</span></span></td>
  <td><span data-ttu-id="44fc0-1970">HardDrive</span><span class="sxs-lookup"><span data-stu-id="44fc0-1970">HardDrive</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EDA3.png" width="32" height="32" alt="NetworkAdapter" /></td>
  <td><span data-ttu-id="44fc0-1971">EDA3</span><span class="sxs-lookup"><span data-stu-id="44fc0-1971">EDA3</span></span></td>
  <td><span data-ttu-id="44fc0-1972">NetworkAdapter</span><span class="sxs-lookup"><span data-stu-id="44fc0-1972">NetworkAdapter</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EDA4.png" width="32" height="32" alt="Touchscreen" /></td>
  <td><span data-ttu-id="44fc0-1973">EDA4</span><span class="sxs-lookup"><span data-stu-id="44fc0-1973">EDA4</span></span></td>
  <td><span data-ttu-id="44fc0-1974">Touchscreen</span><span class="sxs-lookup"><span data-stu-id="44fc0-1974">Touchscreen</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EDA5.png" width="32" height="32" alt="NetworkPrinter" /></td>
  <td><span data-ttu-id="44fc0-1975">EDA5</span><span class="sxs-lookup"><span data-stu-id="44fc0-1975">EDA5</span></span></td>
  <td><span data-ttu-id="44fc0-1976">NetworkPrinter</span><span class="sxs-lookup"><span data-stu-id="44fc0-1976">NetworkPrinter</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EDA6.png" width="32" height="32" alt="CloudPrinter" /></td>
  <td><span data-ttu-id="44fc0-1977">EDA6</span><span class="sxs-lookup"><span data-stu-id="44fc0-1977">EDA6</span></span></td>
  <td><span data-ttu-id="44fc0-1978">CloudPrinter</span><span class="sxs-lookup"><span data-stu-id="44fc0-1978">CloudPrinter</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EDA7.png" width="32" height="32" alt="KeyboardShortcut" /></td>
  <td><span data-ttu-id="44fc0-1979">EDA7</span><span class="sxs-lookup"><span data-stu-id="44fc0-1979">EDA7</span></span></td>
  <td><span data-ttu-id="44fc0-1980">KeyboardShortcut</span><span class="sxs-lookup"><span data-stu-id="44fc0-1980">KeyboardShortcut</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EDA8.png" width="32" height="32" alt="BrushSize" /></td>
  <td><span data-ttu-id="44fc0-1981">EDA8</span><span class="sxs-lookup"><span data-stu-id="44fc0-1981">EDA8</span></span></td>
  <td><span data-ttu-id="44fc0-1982">BrushSize</span><span class="sxs-lookup"><span data-stu-id="44fc0-1982">BrushSize</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EDA9.png" width="32" height="32" alt="NarratorForward" /></td>
  <td><span data-ttu-id="44fc0-1983">EDA9</span><span class="sxs-lookup"><span data-stu-id="44fc0-1983">EDA9</span></span></td>
  <td><span data-ttu-id="44fc0-1984">NarratorForward</span><span class="sxs-lookup"><span data-stu-id="44fc0-1984">NarratorForward</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EDAA.png" width="32" height="32" alt="NarratorForwardMirrored" /></td>
  <td><span data-ttu-id="44fc0-1985">EDAA</span><span class="sxs-lookup"><span data-stu-id="44fc0-1985">EDAA</span></span></td>
  <td><span data-ttu-id="44fc0-1986">NarratorForwardMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-1986">NarratorForwardMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EDAB.png" width="32" height="32" alt="SyncBadge12" /></td>
  <td><span data-ttu-id="44fc0-1987">EDAB</span><span class="sxs-lookup"><span data-stu-id="44fc0-1987">EDAB</span></span></td>
  <td><span data-ttu-id="44fc0-1988">SyncBadge12</span><span class="sxs-lookup"><span data-stu-id="44fc0-1988">SyncBadge12</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EDAC.png" width="32" height="32" alt="RingerBadge12" /></td>
  <td><span data-ttu-id="44fc0-1989">EDAC</span><span class="sxs-lookup"><span data-stu-id="44fc0-1989">EDAC</span></span></td>
  <td><span data-ttu-id="44fc0-1990">RingerBadge12</span><span class="sxs-lookup"><span data-stu-id="44fc0-1990">RingerBadge12</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EDAD.png" width="32" height="32" alt="AsteriskBadge12" /></td>
  <td><span data-ttu-id="44fc0-1991">EDAD</span><span class="sxs-lookup"><span data-stu-id="44fc0-1991">EDAD</span></span></td>
  <td><span data-ttu-id="44fc0-1992">AsteriskBadge12</span><span class="sxs-lookup"><span data-stu-id="44fc0-1992">AsteriskBadge12</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EDAE.png" width="32" height="32" alt="ErrorBadge12" /></td>
  <td><span data-ttu-id="44fc0-1993">EDAE</span><span class="sxs-lookup"><span data-stu-id="44fc0-1993">EDAE</span></span></td>
  <td><span data-ttu-id="44fc0-1994">ErrorBadge12</span><span class="sxs-lookup"><span data-stu-id="44fc0-1994">ErrorBadge12</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EDAF.png" width="32" height="32" alt="CircleRingBadge12" /></td>
  <td><span data-ttu-id="44fc0-1995">EDAF</span><span class="sxs-lookup"><span data-stu-id="44fc0-1995">EDAF</span></span></td>
  <td><span data-ttu-id="44fc0-1996">CircleRingBadge12</span><span class="sxs-lookup"><span data-stu-id="44fc0-1996">CircleRingBadge12</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EDB0.png" width="32" height="32" alt="CircleFillBadge12" /></td>
  <td><span data-ttu-id="44fc0-1997">EDB0</span><span class="sxs-lookup"><span data-stu-id="44fc0-1997">EDB0</span></span></td>
  <td><span data-ttu-id="44fc0-1998">CircleFillBadge12</span><span class="sxs-lookup"><span data-stu-id="44fc0-1998">CircleFillBadge12</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EDB1.png" width="32" height="32" alt="ImportantBadge12" /></td>
  <td><span data-ttu-id="44fc0-1999">EDB1</span><span class="sxs-lookup"><span data-stu-id="44fc0-1999">EDB1</span></span></td>
  <td><span data-ttu-id="44fc0-2000">ImportantBadge12</span><span class="sxs-lookup"><span data-stu-id="44fc0-2000">ImportantBadge12</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EDB3.png" width="32" height="32" alt="MailBadge12" /></td>
  <td><span data-ttu-id="44fc0-2001">EDB3</span><span class="sxs-lookup"><span data-stu-id="44fc0-2001">EDB3</span></span></td>
  <td><span data-ttu-id="44fc0-2002">MailBadge12</span><span class="sxs-lookup"><span data-stu-id="44fc0-2002">MailBadge12</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EDB4.png" width="32" height="32" alt="PauseBadge12" /></td>
  <td><span data-ttu-id="44fc0-2003">EDB4</span><span class="sxs-lookup"><span data-stu-id="44fc0-2003">EDB4</span></span></td>
  <td><span data-ttu-id="44fc0-2004">PauseBadge12</span><span class="sxs-lookup"><span data-stu-id="44fc0-2004">PauseBadge12</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EDB5.png" width="32" height="32" alt="PlayBadge12" /></td>
  <td><span data-ttu-id="44fc0-2005">EDB5</span><span class="sxs-lookup"><span data-stu-id="44fc0-2005">EDB5</span></span></td>
  <td><span data-ttu-id="44fc0-2006">PlayBadge12</span><span class="sxs-lookup"><span data-stu-id="44fc0-2006">PlayBadge12</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EDC6.png" width="32" height="32" alt="PenWorkspace" /></td>
  <td><span data-ttu-id="44fc0-2007">EDC6</span><span class="sxs-lookup"><span data-stu-id="44fc0-2007">EDC6</span></span></td>
  <td><span data-ttu-id="44fc0-2008">PenWorkspace</span><span class="sxs-lookup"><span data-stu-id="44fc0-2008">PenWorkspace</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EDD6.png" width="32" height="32" alt="CaretRight8" /></td>
  <td><span data-ttu-id="44fc0-2009">EDD6</span><span class="sxs-lookup"><span data-stu-id="44fc0-2009">EDD6</span></span></td>
  <td><span data-ttu-id="44fc0-2010">CaretRight8</span><span class="sxs-lookup"><span data-stu-id="44fc0-2010">CaretRight8</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EDD9.png" width="32" height="32" alt="CaretLeftSolid8" /></td>
  <td><span data-ttu-id="44fc0-2011">EDD9</span><span class="sxs-lookup"><span data-stu-id="44fc0-2011">EDD9</span></span></td>
  <td><span data-ttu-id="44fc0-2012">CaretLeftSolid8</span><span class="sxs-lookup"><span data-stu-id="44fc0-2012">CaretLeftSolid8</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EDDA.png" width="32" height="32" alt="CaretRightSolid8" /></td>
  <td><span data-ttu-id="44fc0-2013">EDDA</span><span class="sxs-lookup"><span data-stu-id="44fc0-2013">EDDA</span></span></td>
  <td><span data-ttu-id="44fc0-2014">CaretRightSolid8</span><span class="sxs-lookup"><span data-stu-id="44fc0-2014">CaretRightSolid8</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EDDB.png" width="32" height="32" alt="CaretUpSolid8" /></td>
  <td><span data-ttu-id="44fc0-2015">EDDB</span><span class="sxs-lookup"><span data-stu-id="44fc0-2015">EDDB</span></span></td>
  <td><span data-ttu-id="44fc0-2016">CaretUpSolid8</span><span class="sxs-lookup"><span data-stu-id="44fc0-2016">CaretUpSolid8</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EDDC.png" width="32" height="32" alt="CaretDownSolid8" /></td>
  <td><span data-ttu-id="44fc0-2017">EDDC</span><span class="sxs-lookup"><span data-stu-id="44fc0-2017">EDDC</span></span></td>
  <td><span data-ttu-id="44fc0-2018">CaretDownSolid8</span><span class="sxs-lookup"><span data-stu-id="44fc0-2018">CaretDownSolid8</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EDE1.png" width="32" height="32" alt="Export" /></td>
  <td><span data-ttu-id="44fc0-2019">EDE1</span><span class="sxs-lookup"><span data-stu-id="44fc0-2019">EDE1</span></span></td>
  <td><span data-ttu-id="44fc0-2020">Export</span><span class="sxs-lookup"><span data-stu-id="44fc0-2020">Export</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EDE2.png" width="32" height="32" alt="ExportMirrored" /></td>
  <td><span data-ttu-id="44fc0-2021">EDE2</span><span class="sxs-lookup"><span data-stu-id="44fc0-2021">EDE2</span></span></td>
  <td><span data-ttu-id="44fc0-2022">ExportMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-2022">ExportMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EDE3.png" width="32" height="32" alt="ButtonMenu" /></td>
  <td><span data-ttu-id="44fc0-2023">EDE3</span><span class="sxs-lookup"><span data-stu-id="44fc0-2023">EDE3</span></span></td>
  <td><span data-ttu-id="44fc0-2024">ButtonMenu</span><span class="sxs-lookup"><span data-stu-id="44fc0-2024">ButtonMenu</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EDE4.png" width="32" height="32" alt="CloudSeach" /></td>
  <td><span data-ttu-id="44fc0-2025">EDE4</span><span class="sxs-lookup"><span data-stu-id="44fc0-2025">EDE4</span></span></td>
  <td><span data-ttu-id="44fc0-2026">CloudSeach</span><span class="sxs-lookup"><span data-stu-id="44fc0-2026">CloudSeach</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EDE5.png" width="32" height="32" alt="PinyinIMELogo" /></td>
  <td><span data-ttu-id="44fc0-2027">EDE5</span><span class="sxs-lookup"><span data-stu-id="44fc0-2027">EDE5</span></span></td>
  <td><span data-ttu-id="44fc0-2028">PinyinIMELogo</span><span class="sxs-lookup"><span data-stu-id="44fc0-2028">PinyinIMELogo</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EDFB.png" width="32" height="32" alt="CalligraphyPen" /></td>
  <td><span data-ttu-id="44fc0-2029">EDFB</span><span class="sxs-lookup"><span data-stu-id="44fc0-2029">EDFB</span></span></td>
  <td><span data-ttu-id="44fc0-2030">CalligraphyPen</span><span class="sxs-lookup"><span data-stu-id="44fc0-2030">CalligraphyPen</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EE35.png" width="32" height="32" alt="ReplyMirrored" /></td>
  <td><span data-ttu-id="44fc0-2031">EE35</span><span class="sxs-lookup"><span data-stu-id="44fc0-2031">EE35</span></span></td>
  <td><span data-ttu-id="44fc0-2032">ReplyMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-2032">ReplyMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EE3F.png" width="32" height="32" alt="LockscreenDesktop" /></td>
  <td><span data-ttu-id="44fc0-2033">EE3F</span><span class="sxs-lookup"><span data-stu-id="44fc0-2033">EE3F</span></span></td>
  <td><span data-ttu-id="44fc0-2034">LockscreenDesktop</span><span class="sxs-lookup"><span data-stu-id="44fc0-2034">LockscreenDesktop</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EE40.png" width="32" height="32" alt="TaskViewSettings" /></td>
  <td><span data-ttu-id="44fc0-2035">EE40</span><span class="sxs-lookup"><span data-stu-id="44fc0-2035">EE40</span></span></td>
  <td><span data-ttu-id="44fc0-2036">TaskViewSettings</span><span class="sxs-lookup"><span data-stu-id="44fc0-2036">TaskViewSettings</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EE4A.png" width="32" height="32" alt="Play36" /></td>
  <td><span data-ttu-id="44fc0-2037">EE4A</span><span class="sxs-lookup"><span data-stu-id="44fc0-2037">EE4A</span></span></td>
  <td><span data-ttu-id="44fc0-2038">Play36</span><span class="sxs-lookup"><span data-stu-id="44fc0-2038">Play36</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EE56.png" width="32" height="32" alt="PenPalette" /></td>
  <td><span data-ttu-id="44fc0-2039">EE56</span><span class="sxs-lookup"><span data-stu-id="44fc0-2039">EE56</span></span></td>
  <td><span data-ttu-id="44fc0-2040">PenPalette</span><span class="sxs-lookup"><span data-stu-id="44fc0-2040">PenPalette</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EE57.png" width="32" height="32" alt="GuestUser" /></td>
  <td><span data-ttu-id="44fc0-2041">EE57</span><span class="sxs-lookup"><span data-stu-id="44fc0-2041">EE57</span></span></td>
  <td><span data-ttu-id="44fc0-2042">GuestUser</span><span class="sxs-lookup"><span data-stu-id="44fc0-2042">GuestUser</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EE63.png" width="32" height="32" alt="SettingsBattery" /></td>
  <td><span data-ttu-id="44fc0-2043">EE63</span><span class="sxs-lookup"><span data-stu-id="44fc0-2043">EE63</span></span></td>
  <td><span data-ttu-id="44fc0-2044">SettingsBattery</span><span class="sxs-lookup"><span data-stu-id="44fc0-2044">SettingsBattery</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EE64.png" width="32" height="32" alt="TaskbarPhone" /></td>
  <td><span data-ttu-id="44fc0-2045">EE64</span><span class="sxs-lookup"><span data-stu-id="44fc0-2045">EE64</span></span></td>
  <td><span data-ttu-id="44fc0-2046">TaskbarPhone</span><span class="sxs-lookup"><span data-stu-id="44fc0-2046">TaskbarPhone</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EE65.png" width="32" height="32" alt="LockScreenGlance" /></td>
  <td><span data-ttu-id="44fc0-2047">EE65</span><span class="sxs-lookup"><span data-stu-id="44fc0-2047">EE65</span></span></td>
  <td><span data-ttu-id="44fc0-2048">LockScreenGlance</span><span class="sxs-lookup"><span data-stu-id="44fc0-2048">LockScreenGlance</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EE71.png" width="32" height="32" alt="ImageExport " /></td>
  <td><span data-ttu-id="44fc0-2049">EE71</span><span class="sxs-lookup"><span data-stu-id="44fc0-2049">EE71</span></span></td>
  <td><span data-ttu-id="44fc0-2050">ImageExport</span><span class="sxs-lookup"><span data-stu-id="44fc0-2050">ImageExport</span></span> </td>
 </tr>
<tr><td><img src="images/segoe-mdl/EE77.png" width="32" height="32" alt="WifiEthernet" /></td>
  <td><span data-ttu-id="44fc0-2051">EE77</span><span class="sxs-lookup"><span data-stu-id="44fc0-2051">EE77</span></span></td>
  <td><span data-ttu-id="44fc0-2052">WifiEthernet</span><span class="sxs-lookup"><span data-stu-id="44fc0-2052">WifiEthernet</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EE79.png" width="32" height="32" alt="ActionCenterQuiet" /></td>
  <td><span data-ttu-id="44fc0-2053">EE79</span><span class="sxs-lookup"><span data-stu-id="44fc0-2053">EE79</span></span></td>
  <td><span data-ttu-id="44fc0-2054">ActionCenterQuiet</span><span class="sxs-lookup"><span data-stu-id="44fc0-2054">ActionCenterQuiet</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EE7A.png" width="32" height="32" alt="ActionCenterQuietNotification" /></td>
  <td><span data-ttu-id="44fc0-2055">EE7A</span><span class="sxs-lookup"><span data-stu-id="44fc0-2055">EE7A</span></span></td>
  <td><span data-ttu-id="44fc0-2056">ActionCenterQuietNotification</span><span class="sxs-lookup"><span data-stu-id="44fc0-2056">ActionCenterQuietNotification</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EE92.png" width="32" height="32" alt="TrackersMirrored" /></td>
  <td><span data-ttu-id="44fc0-2057">EE92</span><span class="sxs-lookup"><span data-stu-id="44fc0-2057">EE92</span></span></td>
  <td><span data-ttu-id="44fc0-2058">TrackersMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-2058">TrackersMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EE93.png" width="32" height="32" alt="DateTimeMirrored" /></td>
  <td><span data-ttu-id="44fc0-2059">EE93</span><span class="sxs-lookup"><span data-stu-id="44fc0-2059">EE93</span></span></td>
  <td><span data-ttu-id="44fc0-2060">DateTimeMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-2060">DateTimeMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EE94.png" width="32" height="32" alt="Wheel" /></td>
  <td><span data-ttu-id="44fc0-2061">EE94</span><span class="sxs-lookup"><span data-stu-id="44fc0-2061">EE94</span></span></td>
  <td><span data-ttu-id="44fc0-2062">Rad</span><span class="sxs-lookup"><span data-stu-id="44fc0-2062">Wheel</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EECA.png" width="32" height="32" alt="ButtonView2" /></td>
  <td><span data-ttu-id="44fc0-2063">EECA</span><span class="sxs-lookup"><span data-stu-id="44fc0-2063">EECA</span></span></td>
  <td><span data-ttu-id="44fc0-2064">ButtonView2</span><span class="sxs-lookup"><span data-stu-id="44fc0-2064">ButtonView2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EF15.png" width="32" height="32" alt="PenWorkspaceMirrored" /></td>
  <td><span data-ttu-id="44fc0-2065">EF15</span><span class="sxs-lookup"><span data-stu-id="44fc0-2065">EF15</span></span></td>
  <td><span data-ttu-id="44fc0-2066">PenWorkspaceMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-2066">PenWorkspaceMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EF16.png" width="32" height="32" alt="PenPaletteMirrored" /></td>
  <td><span data-ttu-id="44fc0-2067">EF16</span><span class="sxs-lookup"><span data-stu-id="44fc0-2067">EF16</span></span></td>
  <td><span data-ttu-id="44fc0-2068">PenPaletteMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-2068">PenPaletteMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EF17.png" width="32" height="32" alt="StrokeEraseMirrored" /></td>
  <td><span data-ttu-id="44fc0-2069">EF17</span><span class="sxs-lookup"><span data-stu-id="44fc0-2069">EF17</span></span></td>
  <td><span data-ttu-id="44fc0-2070">StrokeEraseMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-2070">StrokeEraseMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EF18.png" width="32" height="32" alt="PointEraseMirrored" /></td>
  <td><span data-ttu-id="44fc0-2071">EF18</span><span class="sxs-lookup"><span data-stu-id="44fc0-2071">EF18</span></span></td>
  <td><span data-ttu-id="44fc0-2072">PointEraseMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-2072">PointEraseMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EF19.png" width="32" height="32" alt="ClearAllInkMirrored" /></td>
  <td><span data-ttu-id="44fc0-2073">EF19</span><span class="sxs-lookup"><span data-stu-id="44fc0-2073">EF19</span></span></td>
  <td><span data-ttu-id="44fc0-2074">ClearAllInkMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-2074">ClearAllInkMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EF1F.png" width="32" height="32" alt="BackgroundToggle" /></td>
  <td><span data-ttu-id="44fc0-2075">EF1F</span><span class="sxs-lookup"><span data-stu-id="44fc0-2075">EF1F</span></span></td>
  <td><span data-ttu-id="44fc0-2076">BackgroundToggle</span><span class="sxs-lookup"><span data-stu-id="44fc0-2076">BackgroundToggle</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EF20.png" width="32" height="32" alt="Marquee" /></td>
  <td><span data-ttu-id="44fc0-2077">EF20</span><span class="sxs-lookup"><span data-stu-id="44fc0-2077">EF20</span></span></td>
  <td><span data-ttu-id="44fc0-2078">Marquee</span><span class="sxs-lookup"><span data-stu-id="44fc0-2078">Marquee</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EF2C.png" width="32" height="32" alt="ChromeCloseContrast" /></td>
  <td><span data-ttu-id="44fc0-2079">EF2C</span><span class="sxs-lookup"><span data-stu-id="44fc0-2079">EF2C</span></span></td>
  <td><span data-ttu-id="44fc0-2080">ChromeCloseContrast</span><span class="sxs-lookup"><span data-stu-id="44fc0-2080">ChromeCloseContrast</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EF2D.png" width="32" height="32" alt="ChromeMinimizeContrast" /></td>
  <td><span data-ttu-id="44fc0-2081">EF2D</span><span class="sxs-lookup"><span data-stu-id="44fc0-2081">EF2D</span></span></td>
  <td><span data-ttu-id="44fc0-2082">ChromeMinimizeContrast</span><span class="sxs-lookup"><span data-stu-id="44fc0-2082">ChromeMinimizeContrast</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EF2E.png" width="32" height="32" alt="ChromeMaximizeContrast" /></td>
  <td><span data-ttu-id="44fc0-2083">EF2E</span><span class="sxs-lookup"><span data-stu-id="44fc0-2083">EF2E</span></span></td>
  <td><span data-ttu-id="44fc0-2084">ChromeMaximizeContrast</span><span class="sxs-lookup"><span data-stu-id="44fc0-2084">ChromeMaximizeContrast</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EF2F.png" width="32" height="32" alt="ChromeRestoreContrast" /></td>
  <td><span data-ttu-id="44fc0-2085">EF2F</span><span class="sxs-lookup"><span data-stu-id="44fc0-2085">EF2F</span></span></td>
  <td><span data-ttu-id="44fc0-2086">ChromeRestoreContrast</span><span class="sxs-lookup"><span data-stu-id="44fc0-2086">ChromeRestoreContrast</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EF31.png" width="32" height="32" alt="TrafficLight" /></td>
  <td><span data-ttu-id="44fc0-2087">EF31</span><span class="sxs-lookup"><span data-stu-id="44fc0-2087">EF31</span></span></td>
  <td><span data-ttu-id="44fc0-2088">TrafficLight</span><span class="sxs-lookup"><span data-stu-id="44fc0-2088">TrafficLight</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EF3B.png" width="32" height="32" alt="Replay" /></td>
  <td><span data-ttu-id="44fc0-2089">EF3B</span><span class="sxs-lookup"><span data-stu-id="44fc0-2089">EF3B</span></span></td>
  <td><span data-ttu-id="44fc0-2090">Wiedergabe</span><span class="sxs-lookup"><span data-stu-id="44fc0-2090">Replay</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EF3C.png" width="32" height="32" alt="Eyedropper" /></td>
  <td><span data-ttu-id="44fc0-2091">EF3C</span><span class="sxs-lookup"><span data-stu-id="44fc0-2091">EF3C</span></span></td>
  <td><span data-ttu-id="44fc0-2092">Pipette</span><span class="sxs-lookup"><span data-stu-id="44fc0-2092">Eyedropper</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EF3D.png" width="32" height="32" alt="LineDisplay" /></td>
  <td><span data-ttu-id="44fc0-2093">EF3D</span><span class="sxs-lookup"><span data-stu-id="44fc0-2093">EF3D</span></span></td>
  <td><span data-ttu-id="44fc0-2094">LineDisplay</span><span class="sxs-lookup"><span data-stu-id="44fc0-2094">LineDisplay</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EF3E.png" width="32" height="32" alt="PINPad" /></td>
  <td><span data-ttu-id="44fc0-2095">EF3E</span><span class="sxs-lookup"><span data-stu-id="44fc0-2095">EF3E</span></span></td>
  <td><span data-ttu-id="44fc0-2096">PINPad</span><span class="sxs-lookup"><span data-stu-id="44fc0-2096">PINPad</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EF3F.png" width="32" height="32" alt="SignatureCapture" /></td>
  <td><span data-ttu-id="44fc0-2097">EF3F</span><span class="sxs-lookup"><span data-stu-id="44fc0-2097">EF3F</span></span></td>
  <td><span data-ttu-id="44fc0-2098">SignatureCapture</span><span class="sxs-lookup"><span data-stu-id="44fc0-2098">SignatureCapture</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EF40.png" width="32" height="32" alt="ChipCardCreditCardReader" /></td>
  <td><span data-ttu-id="44fc0-2099">EF40</span><span class="sxs-lookup"><span data-stu-id="44fc0-2099">EF40</span></span></td>
  <td><span data-ttu-id="44fc0-2100">ChipCardCreditCardReader</span><span class="sxs-lookup"><span data-stu-id="44fc0-2100">ChipCardCreditCardReader</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EF58.png" width="32" height="32" alt="PlayerSettings" /></td>
  <td><span data-ttu-id="44fc0-2101">EF58</span><span class="sxs-lookup"><span data-stu-id="44fc0-2101">EF58</span></span></td>
  <td><span data-ttu-id="44fc0-2102">PlayerSettings</span><span class="sxs-lookup"><span data-stu-id="44fc0-2102">PlayerSettings</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EF6B.png" width="32" height="32" alt="LandscapeOrientation" /></td>
  <td><span data-ttu-id="44fc0-2103">EF6B</span><span class="sxs-lookup"><span data-stu-id="44fc0-2103">EF6B</span></span></td>
  <td><span data-ttu-id="44fc0-2104">LandscapeOrientation</span><span class="sxs-lookup"><span data-stu-id="44fc0-2104">LandscapeOrientation</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EFA5.png" width="32" height="32" alt="Touchpad" /></td>
  <td><span data-ttu-id="44fc0-2105">EFA5</span><span class="sxs-lookup"><span data-stu-id="44fc0-2105">EFA5</span></span></td>
  <td><span data-ttu-id="44fc0-2106">Touchpad</span><span class="sxs-lookup"><span data-stu-id="44fc0-2106">Touchpad</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/EFA9.png" width="32" height="32" alt="Speech" /></td>
  <td><span data-ttu-id="44fc0-2107">EFA9</span><span class="sxs-lookup"><span data-stu-id="44fc0-2107">EFA9</span></span></td>
  <td><span data-ttu-id="44fc0-2108">Spracherkennung</span><span class="sxs-lookup"><span data-stu-id="44fc0-2108">Speech</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F000.png" width="32" height="32" alt="KnowledgeArticle" /></td>
  <td><span data-ttu-id="44fc0-2109">F000</span><span class="sxs-lookup"><span data-stu-id="44fc0-2109">F000</span></span></td>
  <td><span data-ttu-id="44fc0-2110">KnowledgeArticle</span><span class="sxs-lookup"><span data-stu-id="44fc0-2110">KnowledgeArticle</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F003.png" width="32" height="32" alt="Relationship" /></td>
  <td><span data-ttu-id="44fc0-2111">F003</span><span class="sxs-lookup"><span data-stu-id="44fc0-2111">F003</span></span></td>
  <td><span data-ttu-id="44fc0-2112">Beziehung</span><span class="sxs-lookup"><span data-stu-id="44fc0-2112">Relationship</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F080.png" width="32" height="32" alt="DefaultAPN" /></td>
  <td><span data-ttu-id="44fc0-2113">F080</span><span class="sxs-lookup"><span data-stu-id="44fc0-2113">F080</span></span></td>
  <td><span data-ttu-id="44fc0-2114">DefaultAPN</span><span class="sxs-lookup"><span data-stu-id="44fc0-2114">DefaultAPN</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F081.png" width="32" height="32" alt="UserAPN " /></td>
  <td><span data-ttu-id="44fc0-2115">F081</span><span class="sxs-lookup"><span data-stu-id="44fc0-2115">F081</span></span></td>
  <td><span data-ttu-id="44fc0-2116">UserAPN</span><span class="sxs-lookup"><span data-stu-id="44fc0-2116">UserAPN</span></span> </td>
 </tr>
<tr><td><img src="images/segoe-mdl/F085.png" width="32" height="32" alt="DoublePinyin" /></td>
  <td><span data-ttu-id="44fc0-2117">F085</span><span class="sxs-lookup"><span data-stu-id="44fc0-2117">F085</span></span></td>
  <td><span data-ttu-id="44fc0-2118">DoublePinyin</span><span class="sxs-lookup"><span data-stu-id="44fc0-2118">DoublePinyin</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F08C.png" width="32" height="32" alt="BlueLight" /></td>
  <td><span data-ttu-id="44fc0-2119">F08C</span><span class="sxs-lookup"><span data-stu-id="44fc0-2119">F08C</span></span></td>
  <td><span data-ttu-id="44fc0-2120">BlueLight</span><span class="sxs-lookup"><span data-stu-id="44fc0-2120">BlueLight</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F093.png" width="32" height="32" alt="ButtonA" /></td>
  <td><span data-ttu-id="44fc0-2121">F093</span><span class="sxs-lookup"><span data-stu-id="44fc0-2121">F093</span></span></td>
  <td><span data-ttu-id="44fc0-2122">ButtonA</span><span class="sxs-lookup"><span data-stu-id="44fc0-2122">ButtonA</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F094.png" width="32" height="32" alt="ButtonB" /></td>
  <td><span data-ttu-id="44fc0-2123">F094</span><span class="sxs-lookup"><span data-stu-id="44fc0-2123">F094</span></span></td>
  <td><span data-ttu-id="44fc0-2124">ButtonB</span><span class="sxs-lookup"><span data-stu-id="44fc0-2124">ButtonB</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F095.png" width="32" height="32" alt="ButtonY" /></td>
  <td><span data-ttu-id="44fc0-2125">F095</span><span class="sxs-lookup"><span data-stu-id="44fc0-2125">F095</span></span></td>
  <td><span data-ttu-id="44fc0-2126">ButtonY</span><span class="sxs-lookup"><span data-stu-id="44fc0-2126">ButtonY</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F096.png" width="32" height="32" alt="ButtonX" /></td>
  <td><span data-ttu-id="44fc0-2127">F096</span><span class="sxs-lookup"><span data-stu-id="44fc0-2127">F096</span></span></td>
  <td><span data-ttu-id="44fc0-2128">ButtonX</span><span class="sxs-lookup"><span data-stu-id="44fc0-2128">ButtonX</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0AD.png" width="32" height="32" alt="ArrowUp8" /></td>
  <td><span data-ttu-id="44fc0-2129">F0AD</span><span class="sxs-lookup"><span data-stu-id="44fc0-2129">F0AD</span></span></td>
  <td><span data-ttu-id="44fc0-2130">ArrowUp8</span><span class="sxs-lookup"><span data-stu-id="44fc0-2130">ArrowUp8</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0AE.png" width="32" height="32" alt="ArrowDown8" /></td>
  <td><span data-ttu-id="44fc0-2131">F0AE</span><span class="sxs-lookup"><span data-stu-id="44fc0-2131">F0AE</span></span></td>
  <td><span data-ttu-id="44fc0-2132">ArrowDown8</span><span class="sxs-lookup"><span data-stu-id="44fc0-2132">ArrowDown8</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0AF.png" width="32" height="32" alt="ArrowRight8" /></td>
  <td><span data-ttu-id="44fc0-2133">F0AF</span><span class="sxs-lookup"><span data-stu-id="44fc0-2133">F0AF</span></span></td>
  <td><span data-ttu-id="44fc0-2134">ArrowRight8</span><span class="sxs-lookup"><span data-stu-id="44fc0-2134">ArrowRight8</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0B0.png" width="32" height="32" alt="ArrowLeft8" /></td>
  <td><span data-ttu-id="44fc0-2135">F0B0</span><span class="sxs-lookup"><span data-stu-id="44fc0-2135">F0B0</span></span></td>
  <td><span data-ttu-id="44fc0-2136">ArrowLeft8</span><span class="sxs-lookup"><span data-stu-id="44fc0-2136">ArrowLeft8</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0B2.png" width="32" height="32" alt="QuarentinedItems" /></td>
  <td><span data-ttu-id="44fc0-2137">F0B2</span><span class="sxs-lookup"><span data-stu-id="44fc0-2137">F0B2</span></span></td>
  <td><span data-ttu-id="44fc0-2138">QuarentinedItems</span><span class="sxs-lookup"><span data-stu-id="44fc0-2138">QuarentinedItems</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0B3.png" width="32" height="32" alt="QuarentinedItemsMirrored" /></td>
  <td><span data-ttu-id="44fc0-2139">F0B3</span><span class="sxs-lookup"><span data-stu-id="44fc0-2139">F0B3</span></span></td>
  <td><span data-ttu-id="44fc0-2140">QuarentinedItemsMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-2140">QuarentinedItemsMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0B4.png" width="32" height="32" alt="Protractor" /></td>
  <td><span data-ttu-id="44fc0-2141">F0B4</span><span class="sxs-lookup"><span data-stu-id="44fc0-2141">F0B4</span></span></td>
  <td><span data-ttu-id="44fc0-2142">Winkelmesser</span><span class="sxs-lookup"><span data-stu-id="44fc0-2142">Protractor</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0B5.png" width="32" height="32" alt="ChecklistMirrored" /></td>
  <td><span data-ttu-id="44fc0-2143">F0B5</span><span class="sxs-lookup"><span data-stu-id="44fc0-2143">F0B5</span></span></td>
  <td><span data-ttu-id="44fc0-2144">ChecklistMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-2144">ChecklistMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0B6.png" width="32" height="32" alt="StatusCircle7" /></td>
  <td><span data-ttu-id="44fc0-2145">F0B6</span><span class="sxs-lookup"><span data-stu-id="44fc0-2145">F0B6</span></span></td>
  <td><span data-ttu-id="44fc0-2146">StatusCircle7</span><span class="sxs-lookup"><span data-stu-id="44fc0-2146">StatusCircle7</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0B7.png" width="32" height="32" alt="StatusCheckmark7" /></td>
  <td><span data-ttu-id="44fc0-2147">F0B7</span><span class="sxs-lookup"><span data-stu-id="44fc0-2147">F0B7</span></span></td>
  <td><span data-ttu-id="44fc0-2148">StatusCheckmark7</span><span class="sxs-lookup"><span data-stu-id="44fc0-2148">StatusCheckmark7</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0B8.png" width="32" height="32" alt="StatusErrorCircle7" /></td>
  <td><span data-ttu-id="44fc0-2149">F0B8</span><span class="sxs-lookup"><span data-stu-id="44fc0-2149">F0B8</span></span></td>
  <td><span data-ttu-id="44fc0-2150">StatusErrorCircle7</span><span class="sxs-lookup"><span data-stu-id="44fc0-2150">StatusErrorCircle7</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0B9.png" width="32" height="32" alt="Connected" /></td>
  <td><span data-ttu-id="44fc0-2151">F0B9</span><span class="sxs-lookup"><span data-stu-id="44fc0-2151">F0B9</span></span></td>
  <td><span data-ttu-id="44fc0-2152">Connected</span><span class="sxs-lookup"><span data-stu-id="44fc0-2152">Connected</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0C6.png" width="32" height="32" alt="PencilFill" /></td>
  <td><span data-ttu-id="44fc0-2153">F0C6</span><span class="sxs-lookup"><span data-stu-id="44fc0-2153">F0C6</span></span></td>
  <td><span data-ttu-id="44fc0-2154">PencilFill</span><span class="sxs-lookup"><span data-stu-id="44fc0-2154">PencilFill</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0C7.png" width="32" height="32" alt="CalligraphyFill" /></td>
  <td><span data-ttu-id="44fc0-2155">F0C7</span><span class="sxs-lookup"><span data-stu-id="44fc0-2155">F0C7</span></span></td>
  <td><span data-ttu-id="44fc0-2156">CalligraphyFill</span><span class="sxs-lookup"><span data-stu-id="44fc0-2156">CalligraphyFill</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0CA.png" width="32" height="32" alt="QuarterStarLeft" /></td>
  <td><span data-ttu-id="44fc0-2157">F0CA</span><span class="sxs-lookup"><span data-stu-id="44fc0-2157">F0CA</span></span></td>
  <td><span data-ttu-id="44fc0-2158">QuarterStarLeft</span><span class="sxs-lookup"><span data-stu-id="44fc0-2158">QuarterStarLeft</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0CB.png" width="32" height="32" alt="QuarterStarRight" /></td>
  <td><span data-ttu-id="44fc0-2159">F0CB</span><span class="sxs-lookup"><span data-stu-id="44fc0-2159">F0CB</span></span></td>
  <td><span data-ttu-id="44fc0-2160">QuarterStarRight</span><span class="sxs-lookup"><span data-stu-id="44fc0-2160">QuarterStarRight</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0CC.png" width="32" height="32" alt="ThreeQuarterStarLeft" /></td>
  <td><span data-ttu-id="44fc0-2161">F0CC</span><span class="sxs-lookup"><span data-stu-id="44fc0-2161">F0CC</span></span></td>
  <td><span data-ttu-id="44fc0-2162">ThreeQuarterStarLeft</span><span class="sxs-lookup"><span data-stu-id="44fc0-2162">ThreeQuarterStarLeft</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0CD.png" width="32" height="32" alt="ThreeQuarterStarRight" /></td>
  <td><span data-ttu-id="44fc0-2163">F0CD</span><span class="sxs-lookup"><span data-stu-id="44fc0-2163">F0CD</span></span></td>
  <td><span data-ttu-id="44fc0-2164">ThreeQuarterStarRight</span><span class="sxs-lookup"><span data-stu-id="44fc0-2164">ThreeQuarterStarRight</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0CE.png" width="32" height="32" alt="QuietHoursBadge12" /></td>
  <td><span data-ttu-id="44fc0-2165">F0CE</span><span class="sxs-lookup"><span data-stu-id="44fc0-2165">F0CE</span></span></td>
  <td><span data-ttu-id="44fc0-2166">QuietHoursBadge12</span><span class="sxs-lookup"><span data-stu-id="44fc0-2166">QuietHoursBadge12</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0D2.png" width="32" height="32" alt="BackMirrored" /></td>
  <td><span data-ttu-id="44fc0-2167">F0D2</span><span class="sxs-lookup"><span data-stu-id="44fc0-2167">F0D2</span></span></td>
  <td><span data-ttu-id="44fc0-2168">BackMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-2168">BackMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0D3.png" width="32" height="32" alt="ForwardMirrored" /></td>
  <td><span data-ttu-id="44fc0-2169">F0D3</span><span class="sxs-lookup"><span data-stu-id="44fc0-2169">F0D3</span></span></td>
  <td><span data-ttu-id="44fc0-2170">ForwardMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-2170">ForwardMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0D5.png" width="32" height="32" alt="ChromeBackContrast" /></td>
  <td><span data-ttu-id="44fc0-2171">F0D5</span><span class="sxs-lookup"><span data-stu-id="44fc0-2171">F0D5</span></span></td>
  <td><span data-ttu-id="44fc0-2172">ChromeBackContrast</span><span class="sxs-lookup"><span data-stu-id="44fc0-2172">ChromeBackContrast</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0D6.png" width="32" height="32" alt="ChromeBackContrastMirrored" /></td>
  <td><span data-ttu-id="44fc0-2173">F0D6</span><span class="sxs-lookup"><span data-stu-id="44fc0-2173">F0D6</span></span></td>
  <td><span data-ttu-id="44fc0-2174">ChromeBackContrastMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-2174">ChromeBackContrastMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0D7.png" width="32" height="32" alt="ChromeBackToWindowContrast" /></td>
  <td><span data-ttu-id="44fc0-2175">F0D7</span><span class="sxs-lookup"><span data-stu-id="44fc0-2175">F0D7</span></span></td>
  <td><span data-ttu-id="44fc0-2176">ChromeBackToWindowContrast</span><span class="sxs-lookup"><span data-stu-id="44fc0-2176">ChromeBackToWindowContrast</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0D8.png" width="32" height="32" alt="ChromeFullScreenContrast" /></td>
  <td><span data-ttu-id="44fc0-2177">F0D8</span><span class="sxs-lookup"><span data-stu-id="44fc0-2177">F0D8</span></span></td>
  <td><span data-ttu-id="44fc0-2178">ChromeFullScreenContrast</span><span class="sxs-lookup"><span data-stu-id="44fc0-2178">ChromeFullScreenContrast</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0E2.png" width="32" height="32" alt="GridView" /></td>
  <td><span data-ttu-id="44fc0-2179">F0E2</span><span class="sxs-lookup"><span data-stu-id="44fc0-2179">F0E2</span></span></td>
  <td><span data-ttu-id="44fc0-2180">GridView</span><span class="sxs-lookup"><span data-stu-id="44fc0-2180">GridView</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0E3.png" width="32" height="32" alt="ClipboardList" /></td>
  <td><span data-ttu-id="44fc0-2181">F0E3</span><span class="sxs-lookup"><span data-stu-id="44fc0-2181">F0E3</span></span></td>
  <td><span data-ttu-id="44fc0-2182">ClipboardList</span><span class="sxs-lookup"><span data-stu-id="44fc0-2182">ClipboardList</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0E4.png" width="32" height="32" alt="ClipboardListMirrored" /></td>
  <td><span data-ttu-id="44fc0-2183">F0E4</span><span class="sxs-lookup"><span data-stu-id="44fc0-2183">F0E4</span></span></td>
  <td><span data-ttu-id="44fc0-2184">ClipboardListMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-2184">ClipboardListMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0E5.png" width="32" height="32" alt="OutlineQuarterStarLeft" /></td>
  <td><span data-ttu-id="44fc0-2185">F0E5</span><span class="sxs-lookup"><span data-stu-id="44fc0-2185">F0E5</span></span></td>
  <td><span data-ttu-id="44fc0-2186">OutlineQuarterStarLeft</span><span class="sxs-lookup"><span data-stu-id="44fc0-2186">OutlineQuarterStarLeft</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0E6.png" width="32" height="32" alt="OutlineQuarterStarRight" /></td>
  <td><span data-ttu-id="44fc0-2187">F0E6</span><span class="sxs-lookup"><span data-stu-id="44fc0-2187">F0E6</span></span></td>
  <td><span data-ttu-id="44fc0-2188">OutlineQuarterStarRight</span><span class="sxs-lookup"><span data-stu-id="44fc0-2188">OutlineQuarterStarRight</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0E7.png" width="32" height="32" alt="OutlineHalfStarLeft" /></td>
  <td><span data-ttu-id="44fc0-2189">F0E7</span><span class="sxs-lookup"><span data-stu-id="44fc0-2189">F0E7</span></span></td>
  <td><span data-ttu-id="44fc0-2190">OutlineHalfStarLeft</span><span class="sxs-lookup"><span data-stu-id="44fc0-2190">OutlineHalfStarLeft</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0E8.png" width="32" height="32" alt="OutlineHalfStarRight" /></td>
  <td><span data-ttu-id="44fc0-2191">F0E8</span><span class="sxs-lookup"><span data-stu-id="44fc0-2191">F0E8</span></span></td>
  <td><span data-ttu-id="44fc0-2192">OutlineHalfStarRight</span><span class="sxs-lookup"><span data-stu-id="44fc0-2192">OutlineHalfStarRight</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0E9.png" width="32" height="32" alt="OutlineThreeQuarterStarLeft" /></td>
  <td><span data-ttu-id="44fc0-2193">F0E9</span><span class="sxs-lookup"><span data-stu-id="44fc0-2193">F0E9</span></span></td>
  <td><span data-ttu-id="44fc0-2194">OutlineThreeQuarterStarLeft</span><span class="sxs-lookup"><span data-stu-id="44fc0-2194">OutlineThreeQuarterStarLeft</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0EA.png" width="32" height="32" alt="OutlineThreeQuarterStarRight" /></td>
  <td><span data-ttu-id="44fc0-2195">F0EA</span><span class="sxs-lookup"><span data-stu-id="44fc0-2195">F0EA</span></span></td>
  <td><span data-ttu-id="44fc0-2196">OutlineThreeQuarterStarRight</span><span class="sxs-lookup"><span data-stu-id="44fc0-2196">OutlineThreeQuarterStarRight</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0EB.png" width="32" height="32" alt="SpatialVolume0" /></td>
  <td><span data-ttu-id="44fc0-2197">F0EB</span><span class="sxs-lookup"><span data-stu-id="44fc0-2197">F0EB</span></span></td>
  <td><span data-ttu-id="44fc0-2198">SpatialVolume0</span><span class="sxs-lookup"><span data-stu-id="44fc0-2198">SpatialVolume0</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0EC.png" width="32" height="32" alt="SpatialVolume1" /></td>
  <td><span data-ttu-id="44fc0-2199">F0EC</span><span class="sxs-lookup"><span data-stu-id="44fc0-2199">F0EC</span></span></td>
  <td><span data-ttu-id="44fc0-2200">SpatialVolume1</span><span class="sxs-lookup"><span data-stu-id="44fc0-2200">SpatialVolume1</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0ED.png" width="32" height="32" alt="SpatialVolume2" /></td>
  <td><span data-ttu-id="44fc0-2201">F0ED</span><span class="sxs-lookup"><span data-stu-id="44fc0-2201">F0ED</span></span></td>
  <td><span data-ttu-id="44fc0-2202">SpatialVolume2</span><span class="sxs-lookup"><span data-stu-id="44fc0-2202">SpatialVolume2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0EE.png" width="32" height="32" alt="SpatialVolume3" /></td>
  <td><span data-ttu-id="44fc0-2203">F0EE</span><span class="sxs-lookup"><span data-stu-id="44fc0-2203">F0EE</span></span></td>
  <td><span data-ttu-id="44fc0-2204">SpatialVolume3</span><span class="sxs-lookup"><span data-stu-id="44fc0-2204">SpatialVolume3</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0F7.png" width="32" height="32" alt="OutlineStarLeftHalf" /></td>
  <td><span data-ttu-id="44fc0-2205">F0F7</span><span class="sxs-lookup"><span data-stu-id="44fc0-2205">F0F7</span></span></td>
  <td><span data-ttu-id="44fc0-2206">OutlineStarLeftHalf</span><span class="sxs-lookup"><span data-stu-id="44fc0-2206">OutlineStarLeftHalf</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0F8.png" width="32" height="32" alt="OutlineStarRightHalf" /></td>
  <td><span data-ttu-id="44fc0-2207">F0F8</span><span class="sxs-lookup"><span data-stu-id="44fc0-2207">F0F8</span></span></td>
  <td><span data-ttu-id="44fc0-2208">OutlineStarRightHalf</span><span class="sxs-lookup"><span data-stu-id="44fc0-2208">OutlineStarRightHalf</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0F9.png" width="32" height="32" alt="ChromeAnnotateContrast" /></td>
  <td><span data-ttu-id="44fc0-2209">F0F9</span><span class="sxs-lookup"><span data-stu-id="44fc0-2209">F0F9</span></span></td>
  <td><span data-ttu-id="44fc0-2210">ChromeAnnotateContrast</span><span class="sxs-lookup"><span data-stu-id="44fc0-2210">ChromeAnnotateContrast</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F0FB.png" width="32" height="32" alt="DefenderBadge12" /></td>
  <td><span data-ttu-id="44fc0-2211">F0FB</span><span class="sxs-lookup"><span data-stu-id="44fc0-2211">F0FB</span></span></td>
  <td><span data-ttu-id="44fc0-2212">DefenderBadge12</span><span class="sxs-lookup"><span data-stu-id="44fc0-2212">DefenderBadge12</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F103.png" width="32" height="32" alt="DetachablePC" /></td>
  <td><span data-ttu-id="44fc0-2213">F103</span><span class="sxs-lookup"><span data-stu-id="44fc0-2213">F103</span></span></td>
  <td><span data-ttu-id="44fc0-2214">DetachablePC</span><span class="sxs-lookup"><span data-stu-id="44fc0-2214">DetachablePC</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F108.png" width="32" height="32" alt="LeftStick" /></td>
  <td><span data-ttu-id="44fc0-2215">F108</span><span class="sxs-lookup"><span data-stu-id="44fc0-2215">F108</span></span></td>
  <td><span data-ttu-id="44fc0-2216">LeftStick</span><span class="sxs-lookup"><span data-stu-id="44fc0-2216">LeftStick</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F109.png" width="32" height="32" alt="RightStick" /></td>
  <td><span data-ttu-id="44fc0-2217">F109</span><span class="sxs-lookup"><span data-stu-id="44fc0-2217">F109</span></span></td>
  <td><span data-ttu-id="44fc0-2218">RightStick</span><span class="sxs-lookup"><span data-stu-id="44fc0-2218">RightStick</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F10A.png" width="32" height="32" alt="TriggerLeft" /></td>
  <td><span data-ttu-id="44fc0-2219">F10A</span><span class="sxs-lookup"><span data-stu-id="44fc0-2219">F10A</span></span></td>
  <td><span data-ttu-id="44fc0-2220">TriggerLeft</span><span class="sxs-lookup"><span data-stu-id="44fc0-2220">TriggerLeft</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F10B.png" width="32" height="32" alt="TriggerRight" /></td>
  <td><span data-ttu-id="44fc0-2221">F10B</span><span class="sxs-lookup"><span data-stu-id="44fc0-2221">F10B</span></span></td>
  <td><span data-ttu-id="44fc0-2222">TriggerRight</span><span class="sxs-lookup"><span data-stu-id="44fc0-2222">TriggerRight</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F10C.png" width="32" height="32" alt="BumperLeft" /></td>
  <td><span data-ttu-id="44fc0-2223">F10C</span><span class="sxs-lookup"><span data-stu-id="44fc0-2223">F10C</span></span></td>
  <td><span data-ttu-id="44fc0-2224">BumperLeft</span><span class="sxs-lookup"><span data-stu-id="44fc0-2224">BumperLeft</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F10D.png" width="32" height="32" alt="BumperRight" /></td>
  <td><span data-ttu-id="44fc0-2225">F10D</span><span class="sxs-lookup"><span data-stu-id="44fc0-2225">F10D</span></span></td>
  <td><span data-ttu-id="44fc0-2226">BumperRight</span><span class="sxs-lookup"><span data-stu-id="44fc0-2226">BumperRight</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F10E.png" width="32" height="32" alt="Dpad" /></td>
  <td><span data-ttu-id="44fc0-2227">F10E</span><span class="sxs-lookup"><span data-stu-id="44fc0-2227">F10E</span></span></td>
  <td><span data-ttu-id="44fc0-2228">Dpad</span><span class="sxs-lookup"><span data-stu-id="44fc0-2228">Dpad</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F110.png" width="32" height="32" alt="EnglishPunctuation" /></td>
  <td><span data-ttu-id="44fc0-2229">F110</span><span class="sxs-lookup"><span data-stu-id="44fc0-2229">F110</span></span></td>
  <td><span data-ttu-id="44fc0-2230">EnglishPunctuation</span><span class="sxs-lookup"><span data-stu-id="44fc0-2230">EnglishPunctuation</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F111.png" width="32" height="32" alt="ChinesePunctuation" /></td>
  <td><span data-ttu-id="44fc0-2231">F111</span><span class="sxs-lookup"><span data-stu-id="44fc0-2231">F111</span></span></td>
  <td><span data-ttu-id="44fc0-2232">ChinesePunctuation</span><span class="sxs-lookup"><span data-stu-id="44fc0-2232">ChinesePunctuation</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F119.png" width="32" height="32" alt="HMD" /></td>
  <td><span data-ttu-id="44fc0-2233">F119</span><span class="sxs-lookup"><span data-stu-id="44fc0-2233">F119</span></span></td>
  <td><span data-ttu-id="44fc0-2234">HMD</span><span class="sxs-lookup"><span data-stu-id="44fc0-2234">HMD</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F11B.png" width="32" height="32" alt="CtrlSpatialRight" /></td>
  <td><span data-ttu-id="44fc0-2235">F11B</span><span class="sxs-lookup"><span data-stu-id="44fc0-2235">F11B</span></span></td>
  <td><span data-ttu-id="44fc0-2236">CtrlSpatialRight</span><span class="sxs-lookup"><span data-stu-id="44fc0-2236">CtrlSpatialRight</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F126.png" width="32" height="32" alt="PaginationDotOutline10" /></td>
  <td><span data-ttu-id="44fc0-2237">F126</span><span class="sxs-lookup"><span data-stu-id="44fc0-2237">F126</span></span></td>
  <td><span data-ttu-id="44fc0-2238">PaginationDotOutline10</span><span class="sxs-lookup"><span data-stu-id="44fc0-2238">PaginationDotOutline10</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F127.png" width="32" height="32" alt="PaginationDotSolid10" /></td>
  <td><span data-ttu-id="44fc0-2239">F127</span><span class="sxs-lookup"><span data-stu-id="44fc0-2239">F127</span></span></td>
  <td><span data-ttu-id="44fc0-2240">PaginationDotSolid10</span><span class="sxs-lookup"><span data-stu-id="44fc0-2240">PaginationDotSolid10</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F128.png" width="32" height="32" alt="StrokeErase2" /></td>
  <td><span data-ttu-id="44fc0-2241">F128</span><span class="sxs-lookup"><span data-stu-id="44fc0-2241">F128</span></span></td>
  <td><span data-ttu-id="44fc0-2242">StrokeErase2</span><span class="sxs-lookup"><span data-stu-id="44fc0-2242">StrokeErase2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F129.png" width="32" height="32" alt="SmallErase" /></td>
  <td><span data-ttu-id="44fc0-2243">F129</span><span class="sxs-lookup"><span data-stu-id="44fc0-2243">F129</span></span></td>
  <td><span data-ttu-id="44fc0-2244">SmallErase</span><span class="sxs-lookup"><span data-stu-id="44fc0-2244">SmallErase</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F12A.png" width="32" height="32" alt="LargeErase" /></td>
  <td><span data-ttu-id="44fc0-2245">F12A</span><span class="sxs-lookup"><span data-stu-id="44fc0-2245">F12A</span></span></td>
  <td><span data-ttu-id="44fc0-2246">LargeErase</span><span class="sxs-lookup"><span data-stu-id="44fc0-2246">LargeErase</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F12B.png" width="32" height="32" alt="FolderHorizontal" /></td>
  <td><span data-ttu-id="44fc0-2247">F12B</span><span class="sxs-lookup"><span data-stu-id="44fc0-2247">F12B</span></span></td>
  <td><span data-ttu-id="44fc0-2248">FolderHorizontal</span><span class="sxs-lookup"><span data-stu-id="44fc0-2248">FolderHorizontal</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F12E.png" width="32" height="32" alt="MicrophoneListening" /></td>
  <td><span data-ttu-id="44fc0-2249">F12E</span><span class="sxs-lookup"><span data-stu-id="44fc0-2249">F12E</span></span></td>
  <td><span data-ttu-id="44fc0-2250">MicrophoneListening</span><span class="sxs-lookup"><span data-stu-id="44fc0-2250">MicrophoneListening</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F12F.png" width="32" height="32" alt="StatusExclamationCircle7 " /></td>
  <td><span data-ttu-id="44fc0-2251">F12F</span><span class="sxs-lookup"><span data-stu-id="44fc0-2251">F12F</span></span></td>
  <td><span data-ttu-id="44fc0-2252">StatusExclamationCircle7</span><span class="sxs-lookup"><span data-stu-id="44fc0-2252">StatusExclamationCircle7</span></span> </td>
 </tr>
<tr><td><img src="images/segoe-mdl/F131.png" width="32" height="32" alt="Video360" /></td>
  <td><span data-ttu-id="44fc0-2253">F131</span><span class="sxs-lookup"><span data-stu-id="44fc0-2253">F131</span></span></td>
  <td><span data-ttu-id="44fc0-2254">Video360</span><span class="sxs-lookup"><span data-stu-id="44fc0-2254">Video360</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F133.png" width="32" height="32" alt="GiftboxOpen" /></td>
  <td><span data-ttu-id="44fc0-2255">F133</span><span class="sxs-lookup"><span data-stu-id="44fc0-2255">F133</span></span></td>
  <td><span data-ttu-id="44fc0-2256">GiftboxOpen</span><span class="sxs-lookup"><span data-stu-id="44fc0-2256">GiftboxOpen</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F136.png" width="32" height="32" alt="StatusCircleOuter" /></td>
  <td><span data-ttu-id="44fc0-2257">F136</span><span class="sxs-lookup"><span data-stu-id="44fc0-2257">F136</span></span></td>
  <td><span data-ttu-id="44fc0-2258">StatusCircleOuter</span><span class="sxs-lookup"><span data-stu-id="44fc0-2258">StatusCircleOuter</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F137.png" width="32" height="32" alt="StatusCircleInner" /></td>
  <td><span data-ttu-id="44fc0-2259">F137</span><span class="sxs-lookup"><span data-stu-id="44fc0-2259">F137</span></span></td>
  <td><span data-ttu-id="44fc0-2260">StatusCircleInner</span><span class="sxs-lookup"><span data-stu-id="44fc0-2260">StatusCircleInner</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F138.png" width="32" height="32" alt="StatusCircleRing" /></td>
  <td><span data-ttu-id="44fc0-2261">F138</span><span class="sxs-lookup"><span data-stu-id="44fc0-2261">F138</span></span></td>
  <td><span data-ttu-id="44fc0-2262">StatusCircleRing</span><span class="sxs-lookup"><span data-stu-id="44fc0-2262">StatusCircleRing</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F139.png" width="32" height="32" alt="StatusTriangleOuter" /></td>
  <td><span data-ttu-id="44fc0-2263">F139</span><span class="sxs-lookup"><span data-stu-id="44fc0-2263">F139</span></span></td>
  <td><span data-ttu-id="44fc0-2264">StatusTriangleOuter</span><span class="sxs-lookup"><span data-stu-id="44fc0-2264">StatusTriangleOuter</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F13A.png" width="32" height="32" alt="StatusTriangleInner" /></td>
  <td><span data-ttu-id="44fc0-2265">F13A</span><span class="sxs-lookup"><span data-stu-id="44fc0-2265">F13A</span></span></td>
  <td><span data-ttu-id="44fc0-2266">StatusTriangleInner</span><span class="sxs-lookup"><span data-stu-id="44fc0-2266">StatusTriangleInner</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F13B.png" width="32" height="32" alt="StatusTriangleExclamation" /></td>
  <td><span data-ttu-id="44fc0-2267">F13B</span><span class="sxs-lookup"><span data-stu-id="44fc0-2267">F13B</span></span></td>
  <td><span data-ttu-id="44fc0-2268">StatusTriangleExclamation</span><span class="sxs-lookup"><span data-stu-id="44fc0-2268">StatusTriangleExclamation</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F13C.png" width="32" height="32" alt="StatusCircleExclamation" /></td>
  <td><span data-ttu-id="44fc0-2269">F13C</span><span class="sxs-lookup"><span data-stu-id="44fc0-2269">F13C</span></span></td>
  <td><span data-ttu-id="44fc0-2270">StatusCircleExclamation</span><span class="sxs-lookup"><span data-stu-id="44fc0-2270">StatusCircleExclamation</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F13D.png" width="32" height="32" alt="StatusCircleErrorX" /></td>
  <td><span data-ttu-id="44fc0-2271">F13D</span><span class="sxs-lookup"><span data-stu-id="44fc0-2271">F13D</span></span></td>
  <td><span data-ttu-id="44fc0-2272">StatusCircleErrorX</span><span class="sxs-lookup"><span data-stu-id="44fc0-2272">StatusCircleErrorX</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F13E.png" width="32" height="32" alt="StatusCircleCheckmark" /></td>
  <td><span data-ttu-id="44fc0-2273">F13E</span><span class="sxs-lookup"><span data-stu-id="44fc0-2273">F13E</span></span></td>
  <td><span data-ttu-id="44fc0-2274">StatusCircleCheckmark</span><span class="sxs-lookup"><span data-stu-id="44fc0-2274">StatusCircleCheckmark</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F13F.png" width="32" height="32" alt="StatusCircleInfo" /></td>
  <td><span data-ttu-id="44fc0-2275">F13F</span><span class="sxs-lookup"><span data-stu-id="44fc0-2275">F13F</span></span></td>
  <td><span data-ttu-id="44fc0-2276">StatusCircleInfo</span><span class="sxs-lookup"><span data-stu-id="44fc0-2276">StatusCircleInfo</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F140.png" width="32" height="32" alt="StatusCircleBlock" /></td>
  <td><span data-ttu-id="44fc0-2277">F140</span><span class="sxs-lookup"><span data-stu-id="44fc0-2277">F140</span></span></td>
  <td><span data-ttu-id="44fc0-2278">StatusCircleBlock</span><span class="sxs-lookup"><span data-stu-id="44fc0-2278">StatusCircleBlock</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F141.png" width="32" height="32" alt="StatusCircleBlock2" /></td>
  <td><span data-ttu-id="44fc0-2279">F141</span><span class="sxs-lookup"><span data-stu-id="44fc0-2279">F141</span></span></td>
  <td><span data-ttu-id="44fc0-2280">StatusCircleBlock2</span><span class="sxs-lookup"><span data-stu-id="44fc0-2280">StatusCircleBlock2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F142.png" width="32" height="32" alt="StatusCircleQuestionMark" /></td>
  <td><span data-ttu-id="44fc0-2281">F142</span><span class="sxs-lookup"><span data-stu-id="44fc0-2281">F142</span></span></td>
  <td><span data-ttu-id="44fc0-2282">StatusCircleQuestionMark</span><span class="sxs-lookup"><span data-stu-id="44fc0-2282">StatusCircleQuestionMark</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F143.png" width="32" height="32" alt="StatusCircleSync" /></td>
  <td><span data-ttu-id="44fc0-2283">F143</span><span class="sxs-lookup"><span data-stu-id="44fc0-2283">F143</span></span></td>
  <td><span data-ttu-id="44fc0-2284">StatusCircleSync</span><span class="sxs-lookup"><span data-stu-id="44fc0-2284">StatusCircleSync</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F146.png" width="32" height="32" alt="Dial1" /></td>
  <td><span data-ttu-id="44fc0-2285">F146</span><span class="sxs-lookup"><span data-stu-id="44fc0-2285">F146</span></span></td>
  <td><span data-ttu-id="44fc0-2286">Dial1</span><span class="sxs-lookup"><span data-stu-id="44fc0-2286">Dial1</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F147.png" width="32" height="32" alt="Dial2" /></td>
  <td><span data-ttu-id="44fc0-2287">F147</span><span class="sxs-lookup"><span data-stu-id="44fc0-2287">F147</span></span></td>
  <td><span data-ttu-id="44fc0-2288">Dial2</span><span class="sxs-lookup"><span data-stu-id="44fc0-2288">Dial2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F148.png" width="32" height="32" alt="Dial3" /></td>
  <td><span data-ttu-id="44fc0-2289">F148</span><span class="sxs-lookup"><span data-stu-id="44fc0-2289">F148</span></span></td>
  <td><span data-ttu-id="44fc0-2290">Dial3</span><span class="sxs-lookup"><span data-stu-id="44fc0-2290">Dial3</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F149.png" width="32" height="32" alt="Dial4" /></td>
  <td><span data-ttu-id="44fc0-2291">F149</span><span class="sxs-lookup"><span data-stu-id="44fc0-2291">F149</span></span></td>
  <td><span data-ttu-id="44fc0-2292">Dial4</span><span class="sxs-lookup"><span data-stu-id="44fc0-2292">Dial4</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F14A.png" width="32" height="32" alt="Dial5" /></td>
  <td><span data-ttu-id="44fc0-2293">F14A</span><span class="sxs-lookup"><span data-stu-id="44fc0-2293">F14A</span></span></td>
  <td><span data-ttu-id="44fc0-2294">Dial5</span><span class="sxs-lookup"><span data-stu-id="44fc0-2294">Dial5</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F14B.png" width="32" height="32" alt="Dial6" /></td>
  <td><span data-ttu-id="44fc0-2295">F14B</span><span class="sxs-lookup"><span data-stu-id="44fc0-2295">F14B</span></span></td>
  <td><span data-ttu-id="44fc0-2296">Dial6</span><span class="sxs-lookup"><span data-stu-id="44fc0-2296">Dial6</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F14C.png" width="32" height="32" alt="Dial7" /></td>
  <td><span data-ttu-id="44fc0-2297">F14C</span><span class="sxs-lookup"><span data-stu-id="44fc0-2297">F14C</span></span></td>
  <td><span data-ttu-id="44fc0-2298">Dial7</span><span class="sxs-lookup"><span data-stu-id="44fc0-2298">Dial7</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F14D.png" width="32" height="32" alt="Dial8" /></td>
  <td><span data-ttu-id="44fc0-2299">F14D</span><span class="sxs-lookup"><span data-stu-id="44fc0-2299">F14D</span></span></td>
  <td><span data-ttu-id="44fc0-2300">Dial8</span><span class="sxs-lookup"><span data-stu-id="44fc0-2300">Dial8</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F14E.png" width="32" height="32" alt="Dial9" /></td>
  <td><span data-ttu-id="44fc0-2301">F14E</span><span class="sxs-lookup"><span data-stu-id="44fc0-2301">F14E</span></span></td>
  <td><span data-ttu-id="44fc0-2302">Dial9</span><span class="sxs-lookup"><span data-stu-id="44fc0-2302">Dial9</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F14F.png" width="32" height="32" alt="Dial10" /></td>
  <td><span data-ttu-id="44fc0-2303">F14F</span><span class="sxs-lookup"><span data-stu-id="44fc0-2303">F14F</span></span></td>
  <td><span data-ttu-id="44fc0-2304">Dial10</span><span class="sxs-lookup"><span data-stu-id="44fc0-2304">Dial10</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F150.png" width="32" height="32" alt="Dial11" /></td>
  <td><span data-ttu-id="44fc0-2305">F150</span><span class="sxs-lookup"><span data-stu-id="44fc0-2305">F150</span></span></td>
  <td><span data-ttu-id="44fc0-2306">Dial11</span><span class="sxs-lookup"><span data-stu-id="44fc0-2306">Dial11</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F151.png" width="32" height="32" alt="Dial12" /></td>
  <td><span data-ttu-id="44fc0-2307">F151</span><span class="sxs-lookup"><span data-stu-id="44fc0-2307">F151</span></span></td>
  <td><span data-ttu-id="44fc0-2308">Dial12</span><span class="sxs-lookup"><span data-stu-id="44fc0-2308">Dial12</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F152.png" width="32" height="32" alt="Dial13" /></td>
  <td><span data-ttu-id="44fc0-2309">F152</span><span class="sxs-lookup"><span data-stu-id="44fc0-2309">F152</span></span></td>
  <td><span data-ttu-id="44fc0-2310">Dial13</span><span class="sxs-lookup"><span data-stu-id="44fc0-2310">Dial13</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F153.png" width="32" height="32" alt="Dial14" /></td>
  <td><span data-ttu-id="44fc0-2311">F153</span><span class="sxs-lookup"><span data-stu-id="44fc0-2311">F153</span></span></td>
  <td><span data-ttu-id="44fc0-2312">Dial14</span><span class="sxs-lookup"><span data-stu-id="44fc0-2312">Dial14</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F154.png" width="32" height="32" alt="Dial15" /></td>
  <td><span data-ttu-id="44fc0-2313">F154</span><span class="sxs-lookup"><span data-stu-id="44fc0-2313">F154</span></span></td>
  <td><span data-ttu-id="44fc0-2314">Dial15</span><span class="sxs-lookup"><span data-stu-id="44fc0-2314">Dial15</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F155.png" width="32" height="32" alt="Dial16" /></td>
  <td><span data-ttu-id="44fc0-2315">F155</span><span class="sxs-lookup"><span data-stu-id="44fc0-2315">F155</span></span></td>
  <td><span data-ttu-id="44fc0-2316">Dial16</span><span class="sxs-lookup"><span data-stu-id="44fc0-2316">Dial16</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F156.png" width="32" height="32" alt="DialShape1" /></td>
  <td><span data-ttu-id="44fc0-2317">F156</span><span class="sxs-lookup"><span data-stu-id="44fc0-2317">F156</span></span></td>
  <td><span data-ttu-id="44fc0-2318">DialShape1</span><span class="sxs-lookup"><span data-stu-id="44fc0-2318">DialShape1</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F157.png" width="32" height="32" alt="DialShape2" /></td>
  <td><span data-ttu-id="44fc0-2319">F157</span><span class="sxs-lookup"><span data-stu-id="44fc0-2319">F157</span></span></td>
  <td><span data-ttu-id="44fc0-2320">DialShape2</span><span class="sxs-lookup"><span data-stu-id="44fc0-2320">DialShape2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F158.png" width="32" height="32" alt="DialShape3" /></td>
  <td><span data-ttu-id="44fc0-2321">F158</span><span class="sxs-lookup"><span data-stu-id="44fc0-2321">F158</span></span></td>
  <td><span data-ttu-id="44fc0-2322">DialShape3</span><span class="sxs-lookup"><span data-stu-id="44fc0-2322">DialShape3</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F159.png" width="32" height="32" alt="DialShape4" /></td>
  <td><span data-ttu-id="44fc0-2323">F159</span><span class="sxs-lookup"><span data-stu-id="44fc0-2323">F159</span></span></td>
  <td><span data-ttu-id="44fc0-2324">DialShape4</span><span class="sxs-lookup"><span data-stu-id="44fc0-2324">DialShape4</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F161.png" width="32" height="32" alt="TollSolid" /></td>
  <td><span data-ttu-id="44fc0-2325">F161</span><span class="sxs-lookup"><span data-stu-id="44fc0-2325">F161</span></span></td>
  <td><span data-ttu-id="44fc0-2326">TollSolid</span><span class="sxs-lookup"><span data-stu-id="44fc0-2326">TollSolid</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F163.png" width="32" height="32" alt="TrafficCongestionSolid" /></td>
  <td><span data-ttu-id="44fc0-2327">F163</span><span class="sxs-lookup"><span data-stu-id="44fc0-2327">F163</span></span></td>
  <td><span data-ttu-id="44fc0-2328">TrafficCongestionSolid</span><span class="sxs-lookup"><span data-stu-id="44fc0-2328">TrafficCongestionSolid</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F164.png" width="32" height="32" alt="ExploreContentSingle" /></td>
  <td><span data-ttu-id="44fc0-2329">F164</span><span class="sxs-lookup"><span data-stu-id="44fc0-2329">F164</span></span></td>
  <td><span data-ttu-id="44fc0-2330">ExploreContentSingle</span><span class="sxs-lookup"><span data-stu-id="44fc0-2330">ExploreContentSingle</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F165.png" width="32" height="32" alt="CollapseContent" /></td>
  <td><span data-ttu-id="44fc0-2331">F165</span><span class="sxs-lookup"><span data-stu-id="44fc0-2331">F165</span></span></td>
  <td><span data-ttu-id="44fc0-2332">CollapseContent</span><span class="sxs-lookup"><span data-stu-id="44fc0-2332">CollapseContent</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F166.png" width="32" height="32" alt="CollapseContentSingle" /></td>
  <td><span data-ttu-id="44fc0-2333">F166</span><span class="sxs-lookup"><span data-stu-id="44fc0-2333">F166</span></span></td>
  <td><span data-ttu-id="44fc0-2334">CollapseContentSingle</span><span class="sxs-lookup"><span data-stu-id="44fc0-2334">CollapseContentSingle</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F167.png" width="32" height="32" alt="InfoSolid" /></td>
  <td><span data-ttu-id="44fc0-2335">F167</span><span class="sxs-lookup"><span data-stu-id="44fc0-2335">F167</span></span></td>
  <td><span data-ttu-id="44fc0-2336">InfoSolid</span><span class="sxs-lookup"><span data-stu-id="44fc0-2336">InfoSolid</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F168.png" width="32" height="32" alt="GroupList" /></td>
  <td><span data-ttu-id="44fc0-2337">F168</span><span class="sxs-lookup"><span data-stu-id="44fc0-2337">F168</span></span></td>
  <td><span data-ttu-id="44fc0-2338">GroupList</span><span class="sxs-lookup"><span data-stu-id="44fc0-2338">GroupList</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F169.png" width="32" height="32" alt="CaretBottomRightSolidCenter8" /></td>
  <td><span data-ttu-id="44fc0-2339">F169</span><span class="sxs-lookup"><span data-stu-id="44fc0-2339">F169</span></span></td>
  <td><span data-ttu-id="44fc0-2340">CaretBottomRightSolidCenter8</span><span class="sxs-lookup"><span data-stu-id="44fc0-2340">CaretBottomRightSolidCenter8</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F16A.png" width="32" height="32" alt="ProgressRingDots" /></td>
  <td><span data-ttu-id="44fc0-2341">F16A</span><span class="sxs-lookup"><span data-stu-id="44fc0-2341">F16A</span></span></td>
  <td><span data-ttu-id="44fc0-2342">ProgressRingDots</span><span class="sxs-lookup"><span data-stu-id="44fc0-2342">ProgressRingDots</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F16B.png" width="32" height="32" alt="Checkbox14" /></td>
  <td><span data-ttu-id="44fc0-2343">F16B</span><span class="sxs-lookup"><span data-stu-id="44fc0-2343">F16B</span></span></td>
  <td><span data-ttu-id="44fc0-2344">Checkbox14</span><span class="sxs-lookup"><span data-stu-id="44fc0-2344">Checkbox14</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F16C.png" width="32" height="32" alt="CheckboxComposite14" /></td>
  <td><span data-ttu-id="44fc0-2345">F16C</span><span class="sxs-lookup"><span data-stu-id="44fc0-2345">F16C</span></span></td>
  <td><span data-ttu-id="44fc0-2346">CheckboxComposite14</span><span class="sxs-lookup"><span data-stu-id="44fc0-2346">CheckboxComposite14</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F16D.png" width="32" height="32" alt="CheckboxIndeterminateCombo14" /></td>
  <td><span data-ttu-id="44fc0-2347">F16D</span><span class="sxs-lookup"><span data-stu-id="44fc0-2347">F16D</span></span></td>
  <td><span data-ttu-id="44fc0-2348">CheckboxIndeterminateCombo14</span><span class="sxs-lookup"><span data-stu-id="44fc0-2348">CheckboxIndeterminateCombo14</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F16E.png" width="32" height="32" alt="CheckboxIndeterminateCombo" /></td>
  <td><span data-ttu-id="44fc0-2349">F16E</span><span class="sxs-lookup"><span data-stu-id="44fc0-2349">F16E</span></span></td>
  <td><span data-ttu-id="44fc0-2350">CheckboxIndeterminateCombo</span><span class="sxs-lookup"><span data-stu-id="44fc0-2350">CheckboxIndeterminateCombo</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F175.png" width="32" height="32" alt="StatusPause7" /></td>
  <td><span data-ttu-id="44fc0-2351">F175</span><span class="sxs-lookup"><span data-stu-id="44fc0-2351">F175</span></span></td>
  <td><span data-ttu-id="44fc0-2352">StatusPause7</span><span class="sxs-lookup"><span data-stu-id="44fc0-2352">StatusPause7</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F17F.png" width="32" height="32" alt="CharacterAppearance" /></td>
  <td><span data-ttu-id="44fc0-2353">F17F</span><span class="sxs-lookup"><span data-stu-id="44fc0-2353">F17F</span></span></td>
  <td><span data-ttu-id="44fc0-2354">CharacterAppearance</span><span class="sxs-lookup"><span data-stu-id="44fc0-2354">CharacterAppearance</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F180.png" width="32" height="32" alt="Lexicon " /></td>
  <td><span data-ttu-id="44fc0-2355">F180</span><span class="sxs-lookup"><span data-stu-id="44fc0-2355">F180</span></span></td>
  <td><span data-ttu-id="44fc0-2356">Lexikon</span><span class="sxs-lookup"><span data-stu-id="44fc0-2356">Lexicon</span></span> </td>
 </tr>
<tr><td><img src="images/segoe-mdl/F182.png" width="32" height="32" alt="ScreenTime" /></td>
  <td><span data-ttu-id="44fc0-2357">F182</span><span class="sxs-lookup"><span data-stu-id="44fc0-2357">F182</span></span></td>
  <td><span data-ttu-id="44fc0-2358">ScreenTime</span><span class="sxs-lookup"><span data-stu-id="44fc0-2358">ScreenTime</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F191.png" width="32" height="32" alt="HeadlessDevice" /></td>
  <td><span data-ttu-id="44fc0-2359">F191</span><span class="sxs-lookup"><span data-stu-id="44fc0-2359">F191</span></span></td>
  <td><span data-ttu-id="44fc0-2360">HeadlessDevice</span><span class="sxs-lookup"><span data-stu-id="44fc0-2360">HeadlessDevice</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F193.png" width="32" height="32" alt="NetworkSharing" /></td>
  <td><span data-ttu-id="44fc0-2361">F193</span><span class="sxs-lookup"><span data-stu-id="44fc0-2361">F193</span></span></td>
  <td><span data-ttu-id="44fc0-2362">NetworkSharing</span><span class="sxs-lookup"><span data-stu-id="44fc0-2362">NetworkSharing</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F19D.png" width="32" height="32" alt="EyeGaze" /></td>
  <td><span data-ttu-id="44fc0-2363">F19D</span><span class="sxs-lookup"><span data-stu-id="44fc0-2363">F19D</span></span></td>
  <td><span data-ttu-id="44fc0-2364">EyeGaze</span><span class="sxs-lookup"><span data-stu-id="44fc0-2364">EyeGaze</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F1AD.png" width="32" height="32" alt="WindowsInsider" /></td>
  <td><span data-ttu-id="44fc0-2365">F1AD</span><span class="sxs-lookup"><span data-stu-id="44fc0-2365">F1AD</span></span></td>
  <td><span data-ttu-id="44fc0-2366">WindowsInsider</span><span class="sxs-lookup"><span data-stu-id="44fc0-2366">WindowsInsider</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F1CB.png" width="32" height="32" alt="ChromeSwitch" /></td>
  <td><span data-ttu-id="44fc0-2367">F1CB</span><span class="sxs-lookup"><span data-stu-id="44fc0-2367">F1CB</span></span></td>
  <td><span data-ttu-id="44fc0-2368">ChromeSwitch</span><span class="sxs-lookup"><span data-stu-id="44fc0-2368">ChromeSwitch</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F1CC.png" width="32" height="32" alt="ChromeSwitchContast" /></td>
  <td><span data-ttu-id="44fc0-2369">F1CC</span><span class="sxs-lookup"><span data-stu-id="44fc0-2369">F1CC</span></span></td>
  <td><span data-ttu-id="44fc0-2370">ChromeSwitchContast</span><span class="sxs-lookup"><span data-stu-id="44fc0-2370">ChromeSwitchContast</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F1D8.png" width="32" height="32" alt="StatusCheckmark" /></td>
  <td><span data-ttu-id="44fc0-2371">F1D8</span><span class="sxs-lookup"><span data-stu-id="44fc0-2371">F1D8</span></span></td>
  <td><span data-ttu-id="44fc0-2372">StatusCheckmark</span><span class="sxs-lookup"><span data-stu-id="44fc0-2372">StatusCheckmark</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F1D9.png" width="32" height="32" alt="StatusCheckmarkLeft" /></td>
  <td><span data-ttu-id="44fc0-2373">F1D9</span><span class="sxs-lookup"><span data-stu-id="44fc0-2373">F1D9</span></span></td>
  <td><span data-ttu-id="44fc0-2374">StatusCheckmarkLeft</span><span class="sxs-lookup"><span data-stu-id="44fc0-2374">StatusCheckmarkLeft</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F20C.png" width="32" height="32" alt="KeyboardLeftAligned" /></td>
  <td><span data-ttu-id="44fc0-2375">F20C</span><span class="sxs-lookup"><span data-stu-id="44fc0-2375">F20C</span></span></td>
  <td><span data-ttu-id="44fc0-2376">KeyboardLeftAligned</span><span class="sxs-lookup"><span data-stu-id="44fc0-2376">KeyboardLeftAligned</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F20D.png" width="32" height="32" alt="KeyboardRightAligned" /></td>
  <td><span data-ttu-id="44fc0-2377">F20D</span><span class="sxs-lookup"><span data-stu-id="44fc0-2377">F20D</span></span></td>
  <td><span data-ttu-id="44fc0-2378">KeyboardRightAligned</span><span class="sxs-lookup"><span data-stu-id="44fc0-2378">KeyboardRightAligned</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F210.png" width="32" height="32" alt="KeyboardSettings" /></td>
  <td><span data-ttu-id="44fc0-2379">F210</span><span class="sxs-lookup"><span data-stu-id="44fc0-2379">F210</span></span></td>
  <td><span data-ttu-id="44fc0-2380">KeyboardSettings</span><span class="sxs-lookup"><span data-stu-id="44fc0-2380">KeyboardSettings</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F22C.png" width="32" height="32" alt="IOT" /></td>
  <td><span data-ttu-id="44fc0-2381">F22C</span><span class="sxs-lookup"><span data-stu-id="44fc0-2381">F22C</span></span></td>
  <td><span data-ttu-id="44fc0-2382">IOT</span><span class="sxs-lookup"><span data-stu-id="44fc0-2382">IOT</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F22E.png" width="32" height="32" alt="UnknownMirrored" /></td>
  <td><span data-ttu-id="44fc0-2383">F22E</span><span class="sxs-lookup"><span data-stu-id="44fc0-2383">F22E</span></span></td>
  <td><span data-ttu-id="44fc0-2384">UnknownMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-2384">UnknownMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F246.png" width="32" height="32" alt="ViewDashboard" /></td>
  <td><span data-ttu-id="44fc0-2385">F246</span><span class="sxs-lookup"><span data-stu-id="44fc0-2385">F246</span></span></td>
  <td><span data-ttu-id="44fc0-2386">ViewDashboard</span><span class="sxs-lookup"><span data-stu-id="44fc0-2386">ViewDashboard</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F259.png" width="32" height="32" alt="ExploitProtectionSettings" /></td>
  <td><span data-ttu-id="44fc0-2387">F259</span><span class="sxs-lookup"><span data-stu-id="44fc0-2387">F259</span></span></td>
  <td><span data-ttu-id="44fc0-2388">ExploitProtectionSettings</span><span class="sxs-lookup"><span data-stu-id="44fc0-2388">ExploitProtectionSettings</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F260.png" width="32" height="32" alt="KeyboardNarrow" /></td>
  <td><span data-ttu-id="44fc0-2389">F260</span><span class="sxs-lookup"><span data-stu-id="44fc0-2389">F260</span></span></td>
  <td><span data-ttu-id="44fc0-2390">KeyboardNarrow</span><span class="sxs-lookup"><span data-stu-id="44fc0-2390">KeyboardNarrow</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F261.png" width="32" height="32" alt="Keyboard12Key" /></td>
  <td><span data-ttu-id="44fc0-2391">F261</span><span class="sxs-lookup"><span data-stu-id="44fc0-2391">F261</span></span></td>
  <td><span data-ttu-id="44fc0-2392">Keyboard12Key</span><span class="sxs-lookup"><span data-stu-id="44fc0-2392">Keyboard12Key</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F26B.png" width="32" height="32" alt="KeyboardDock" /></td>
  <td><span data-ttu-id="44fc0-2393">F26B</span><span class="sxs-lookup"><span data-stu-id="44fc0-2393">F26B</span></span></td>
  <td><span data-ttu-id="44fc0-2394">KeyboardDock</span><span class="sxs-lookup"><span data-stu-id="44fc0-2394">KeyboardDock</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F26C.png" width="32" height="32" alt="KeyboardUndock" /></td>
  <td><span data-ttu-id="44fc0-2395">F26C</span><span class="sxs-lookup"><span data-stu-id="44fc0-2395">F26C</span></span></td>
  <td><span data-ttu-id="44fc0-2396">KeyboardUndock</span><span class="sxs-lookup"><span data-stu-id="44fc0-2396">KeyboardUndock</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F26D.png" width="32" height="32" alt="KeyboardLeftDock" /></td>
  <td><span data-ttu-id="44fc0-2397">F26D</span><span class="sxs-lookup"><span data-stu-id="44fc0-2397">F26D</span></span></td>
  <td><span data-ttu-id="44fc0-2398">KeyboardLeftDock</span><span class="sxs-lookup"><span data-stu-id="44fc0-2398">KeyboardLeftDock</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F26E.png" width="32" height="32" alt="KeyboardRightDock" /></td>
  <td><span data-ttu-id="44fc0-2399">F26E</span><span class="sxs-lookup"><span data-stu-id="44fc0-2399">F26E</span></span></td>
  <td><span data-ttu-id="44fc0-2400">KeyboardRightDock</span><span class="sxs-lookup"><span data-stu-id="44fc0-2400">KeyboardRightDock</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F270.png" width="32" height="32" alt="Ear" /></td>
  <td><span data-ttu-id="44fc0-2401">F270</span><span class="sxs-lookup"><span data-stu-id="44fc0-2401">F270</span></span></td>
  <td><span data-ttu-id="44fc0-2402">Ohr</span><span class="sxs-lookup"><span data-stu-id="44fc0-2402">Ear</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F271.png" width="32" height="32" alt="PointerHand" /></td>
  <td><span data-ttu-id="44fc0-2403">F271</span><span class="sxs-lookup"><span data-stu-id="44fc0-2403">F271</span></span></td>
  <td><span data-ttu-id="44fc0-2404">PointerHand</span><span class="sxs-lookup"><span data-stu-id="44fc0-2404">PointerHand</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F272.png" width="32" height="32" alt="Bullseye" /></td>
  <td><span data-ttu-id="44fc0-2405">F272</span><span class="sxs-lookup"><span data-stu-id="44fc0-2405">F272</span></span></td>
  <td><span data-ttu-id="44fc0-2406">Bullseye</span><span class="sxs-lookup"><span data-stu-id="44fc0-2406">Bullseye</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F32A.png" width="32" height="32" alt="PassiveAuthentication" /></td>
  <td><span data-ttu-id="44fc0-2407">F32A</span><span class="sxs-lookup"><span data-stu-id="44fc0-2407">F32A</span></span></td>
  <td><span data-ttu-id="44fc0-2408">PassiveAuthentication</span><span class="sxs-lookup"><span data-stu-id="44fc0-2408">PassiveAuthentication</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F384.png" width="32" height="32" alt="NetworkOffline" /></td>
  <td><span data-ttu-id="44fc0-2409">F384</span><span class="sxs-lookup"><span data-stu-id="44fc0-2409">F384</span></span></td>
  <td><span data-ttu-id="44fc0-2410">NetworkOffline</span><span class="sxs-lookup"><span data-stu-id="44fc0-2410">NetworkOffline</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F385.png" width="32" height="32" alt="NetworkConnected" /></td>
  <td><span data-ttu-id="44fc0-2411">F385</span><span class="sxs-lookup"><span data-stu-id="44fc0-2411">F385</span></span></td>
  <td><span data-ttu-id="44fc0-2412">NetworkConnected</span><span class="sxs-lookup"><span data-stu-id="44fc0-2412">NetworkConnected</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F386.png" width="32" height="32" alt="NetworkConnectedCheckmark" /></td>
  <td><span data-ttu-id="44fc0-2413">F386</span><span class="sxs-lookup"><span data-stu-id="44fc0-2413">F386</span></span></td>
  <td><span data-ttu-id="44fc0-2414">NetworkConnectedCheckmark</span><span class="sxs-lookup"><span data-stu-id="44fc0-2414">NetworkConnectedCheckmark</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F3CC.png" width="32" height="32" alt="StatusInfo" /></td>
  <td><span data-ttu-id="44fc0-2415">F3CC</span><span class="sxs-lookup"><span data-stu-id="44fc0-2415">F3CC</span></span></td>
  <td><span data-ttu-id="44fc0-2416">StatusInfo</span><span class="sxs-lookup"><span data-stu-id="44fc0-2416">StatusInfo</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F3CD.png" width="32" height="32" alt="StatusInfoLeft" /></td>
  <td><span data-ttu-id="44fc0-2417">F3CD</span><span class="sxs-lookup"><span data-stu-id="44fc0-2417">F3CD</span></span></td>
  <td><span data-ttu-id="44fc0-2418">StatusInfoLeft</span><span class="sxs-lookup"><span data-stu-id="44fc0-2418">StatusInfoLeft</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F3E2.png" width="32" height="32" alt="NearbySharing" /></td>
  <td><span data-ttu-id="44fc0-2419">F3E2</span><span class="sxs-lookup"><span data-stu-id="44fc0-2419">F3E2</span></span></td>
  <td><span data-ttu-id="44fc0-2420">NearbySharing</span><span class="sxs-lookup"><span data-stu-id="44fc0-2420">NearbySharing</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F3E7.png" width="32" height="32" alt="CtrlSpatialLeft" /></td>
  <td><span data-ttu-id="44fc0-2421">F3E7</span><span class="sxs-lookup"><span data-stu-id="44fc0-2421">F3E7</span></span></td>
  <td><span data-ttu-id="44fc0-2422">CtrlSpatialLeft</span><span class="sxs-lookup"><span data-stu-id="44fc0-2422">CtrlSpatialLeft</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F404.png" width="32" height="32" alt="InteractiveDashboard" /></td>
  <td><span data-ttu-id="44fc0-2423">F404</span><span class="sxs-lookup"><span data-stu-id="44fc0-2423">F404</span></span></td>
  <td><span data-ttu-id="44fc0-2424">InteractiveDashboard</span><span class="sxs-lookup"><span data-stu-id="44fc0-2424">InteractiveDashboard</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F406.png" width="32" height="32" alt="ClippingTool" /></td>
  <td><span data-ttu-id="44fc0-2425">F406</span><span class="sxs-lookup"><span data-stu-id="44fc0-2425">F406</span></span></td>
  <td><span data-ttu-id="44fc0-2426">ClippingTool</span><span class="sxs-lookup"><span data-stu-id="44fc0-2426">ClippingTool</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F407.png" width="32" height="32" alt="RectangularClipping " /></td>
  <td><span data-ttu-id="44fc0-2427">F407</span><span class="sxs-lookup"><span data-stu-id="44fc0-2427">F407</span></span></td>
  <td><span data-ttu-id="44fc0-2428">RectangularClipping</span><span class="sxs-lookup"><span data-stu-id="44fc0-2428">RectangularClipping</span></span> </td>
 </tr>
<tr><td><img src="images/segoe-mdl/F408.png" width="32" height="32" alt="FreeFormClipping" /></td>
  <td><span data-ttu-id="44fc0-2429">F408</span><span class="sxs-lookup"><span data-stu-id="44fc0-2429">F408</span></span></td>
  <td><span data-ttu-id="44fc0-2430">FreeFormClipping</span><span class="sxs-lookup"><span data-stu-id="44fc0-2430">FreeFormClipping</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F413.png" width="32" height="32" alt="CopyTo" /></td>
  <td><span data-ttu-id="44fc0-2431">F413</span><span class="sxs-lookup"><span data-stu-id="44fc0-2431">F413</span></span></td>
  <td><span data-ttu-id="44fc0-2432">CopyTo</span><span class="sxs-lookup"><span data-stu-id="44fc0-2432">CopyTo</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F439.png" width="32" height="32" alt="DynamicLock" /></td>
  <td><span data-ttu-id="44fc0-2433">F439</span><span class="sxs-lookup"><span data-stu-id="44fc0-2433">F439</span></span></td>
  <td><span data-ttu-id="44fc0-2434">DynamicLock</span><span class="sxs-lookup"><span data-stu-id="44fc0-2434">DynamicLock</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F45E.png" width="32" height="32" alt="PenTips" /></td>
  <td><span data-ttu-id="44fc0-2435">F45E</span><span class="sxs-lookup"><span data-stu-id="44fc0-2435">F45E</span></span></td>
  <td><span data-ttu-id="44fc0-2436">PenTips</span><span class="sxs-lookup"><span data-stu-id="44fc0-2436">PenTips</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F45F.png" width="32" height="32" alt="PenTipsMirrored" /></td>
  <td><span data-ttu-id="44fc0-2437">F45F</span><span class="sxs-lookup"><span data-stu-id="44fc0-2437">F45F</span></span></td>
  <td><span data-ttu-id="44fc0-2438">PenTipsMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-2438">PenTipsMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F460.png" width="32" height="32" alt="HWPJoin" /></td>
  <td><span data-ttu-id="44fc0-2439">F460</span><span class="sxs-lookup"><span data-stu-id="44fc0-2439">F460</span></span></td>
  <td><span data-ttu-id="44fc0-2440">HWPJoin</span><span class="sxs-lookup"><span data-stu-id="44fc0-2440">HWPJoin</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F461.png" width="32" height="32" alt="HWPInsert" /></td>
  <td><span data-ttu-id="44fc0-2441">F461</span><span class="sxs-lookup"><span data-stu-id="44fc0-2441">F461</span></span></td>
  <td><span data-ttu-id="44fc0-2442">HWPInsert</span><span class="sxs-lookup"><span data-stu-id="44fc0-2442">HWPInsert</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F462.png" width="32" height="32" alt="HWPStrikeThrough" /></td>
  <td><span data-ttu-id="44fc0-2443">F462</span><span class="sxs-lookup"><span data-stu-id="44fc0-2443">F462</span></span></td>
  <td><span data-ttu-id="44fc0-2444">HWPStrikeThrough</span><span class="sxs-lookup"><span data-stu-id="44fc0-2444">HWPStrikeThrough</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F463.png" width="32" height="32" alt="HWPScratchOut" /></td>
  <td><span data-ttu-id="44fc0-2445">F463</span><span class="sxs-lookup"><span data-stu-id="44fc0-2445">F463</span></span></td>
  <td><span data-ttu-id="44fc0-2446">HWPScratchOut</span><span class="sxs-lookup"><span data-stu-id="44fc0-2446">HWPScratchOut</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F464.png" width="32" height="32" alt="HWPSplit" /></td>
  <td><span data-ttu-id="44fc0-2447">F464</span><span class="sxs-lookup"><span data-stu-id="44fc0-2447">F464</span></span></td>
  <td><span data-ttu-id="44fc0-2448">HWPSplit</span><span class="sxs-lookup"><span data-stu-id="44fc0-2448">HWPSplit</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F465.png" width="32" height="32" alt="HWPNewLine" /></td>
  <td><span data-ttu-id="44fc0-2449">F465</span><span class="sxs-lookup"><span data-stu-id="44fc0-2449">F465</span></span></td>
  <td><span data-ttu-id="44fc0-2450">HWPNewLine</span><span class="sxs-lookup"><span data-stu-id="44fc0-2450">HWPNewLine</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F466.png" width="32" height="32" alt="HWPOverwrite" /></td>
  <td><span data-ttu-id="44fc0-2451">F466</span><span class="sxs-lookup"><span data-stu-id="44fc0-2451">F466</span></span></td>
  <td><span data-ttu-id="44fc0-2452">HWPOverwrite</span><span class="sxs-lookup"><span data-stu-id="44fc0-2452">HWPOverwrite</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F473.png" width="32" height="32" alt="MobWifiWarning1" /></td>
  <td><span data-ttu-id="44fc0-2453">F473</span><span class="sxs-lookup"><span data-stu-id="44fc0-2453">F473</span></span></td>
  <td><span data-ttu-id="44fc0-2454">MobWifiWarning1</span><span class="sxs-lookup"><span data-stu-id="44fc0-2454">MobWifiWarning1</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F474.png" width="32" height="32" alt="MobWifiWarning2" /></td>
  <td><span data-ttu-id="44fc0-2455">F474</span><span class="sxs-lookup"><span data-stu-id="44fc0-2455">F474</span></span></td>
  <td><span data-ttu-id="44fc0-2456">MobWifiWarning2</span><span class="sxs-lookup"><span data-stu-id="44fc0-2456">MobWifiWarning2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F475.png" width="32" height="32" alt="MobWifiWarning3" /></td>
  <td><span data-ttu-id="44fc0-2457">F475</span><span class="sxs-lookup"><span data-stu-id="44fc0-2457">F475</span></span></td>
  <td><span data-ttu-id="44fc0-2458">MobWifiWarning3</span><span class="sxs-lookup"><span data-stu-id="44fc0-2458">MobWifiWarning3</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F476.png" width="32" height="32" alt="MobWifiWarning4" /></td>
  <td><span data-ttu-id="44fc0-2459">F476</span><span class="sxs-lookup"><span data-stu-id="44fc0-2459">F476</span></span></td>
  <td><span data-ttu-id="44fc0-2460">MobWifiWarning4</span><span class="sxs-lookup"><span data-stu-id="44fc0-2460">MobWifiWarning4</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F4A9.png" width="32" height="32" alt="GIF" /></td>
  <td><span data-ttu-id="44fc0-2461">F4A9</span><span class="sxs-lookup"><span data-stu-id="44fc0-2461">F4A9</span></span></td>
  <td><span data-ttu-id="44fc0-2462">GIF</span><span class="sxs-lookup"><span data-stu-id="44fc0-2462">GIF</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F4AA.png" width="32" height="32" alt="Sticker2" /></td>
  <td><span data-ttu-id="44fc0-2463">F4AA</span><span class="sxs-lookup"><span data-stu-id="44fc0-2463">F4AA</span></span></td>
  <td><span data-ttu-id="44fc0-2464">Sticker2</span><span class="sxs-lookup"><span data-stu-id="44fc0-2464">Sticker2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F4BE.png" width="32" height="32" alt="SurfaceHubSelected" /></td>
  <td><span data-ttu-id="44fc0-2465">F4BE</span><span class="sxs-lookup"><span data-stu-id="44fc0-2465">F4BE</span></span></td>
  <td><span data-ttu-id="44fc0-2466">SurfaceHubSelected</span><span class="sxs-lookup"><span data-stu-id="44fc0-2466">SurfaceHubSelected</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F4BF.png" width="32" height="32" alt="HoloLensSelected" /></td>
  <td><span data-ttu-id="44fc0-2467">F4BF</span><span class="sxs-lookup"><span data-stu-id="44fc0-2467">F4BF</span></span></td>
  <td><span data-ttu-id="44fc0-2468">HoloLensSelected</span><span class="sxs-lookup"><span data-stu-id="44fc0-2468">HoloLensSelected</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F4C0.png" width="32" height="32" alt="Earbud" /></td>
  <td><span data-ttu-id="44fc0-2469">F4C0</span><span class="sxs-lookup"><span data-stu-id="44fc0-2469">F4C0</span></span></td>
  <td><span data-ttu-id="44fc0-2470">Earbud</span><span class="sxs-lookup"><span data-stu-id="44fc0-2470">Earbud</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F4C3.png" width="32" height="32" alt="MixVolumes" /></td>
  <td><span data-ttu-id="44fc0-2471">F4C3</span><span class="sxs-lookup"><span data-stu-id="44fc0-2471">F4C3</span></span></td>
  <td><span data-ttu-id="44fc0-2472">MixVolumes</span><span class="sxs-lookup"><span data-stu-id="44fc0-2472">MixVolumes</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F540.png" width="32" height="32" alt="Safe" /></td>
  <td><span data-ttu-id="44fc0-2473">F540</span><span class="sxs-lookup"><span data-stu-id="44fc0-2473">F540</span></span></td>
  <td><span data-ttu-id="44fc0-2474">Sichere</span><span class="sxs-lookup"><span data-stu-id="44fc0-2474">Safe</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F552.png" width="32" height="32" alt="LaptopSecure" /></td>
  <td><span data-ttu-id="44fc0-2475">F552</span><span class="sxs-lookup"><span data-stu-id="44fc0-2475">F552</span></span></td>
  <td><span data-ttu-id="44fc0-2476">LaptopSecure</span><span class="sxs-lookup"><span data-stu-id="44fc0-2476">LaptopSecure</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F56D.png" width="32" height="32" alt="PrintDefault" /></td>
  <td><span data-ttu-id="44fc0-2477">F56D</span><span class="sxs-lookup"><span data-stu-id="44fc0-2477">F56D</span></span></td>
  <td><span data-ttu-id="44fc0-2478">PrintDefault</span><span class="sxs-lookup"><span data-stu-id="44fc0-2478">PrintDefault</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F56E.png" width="32" height="32" alt="PageMirrored" /></td>
  <td><span data-ttu-id="44fc0-2479">F56E</span><span class="sxs-lookup"><span data-stu-id="44fc0-2479">F56E</span></span></td>
  <td><span data-ttu-id="44fc0-2480">PageMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-2480">PageMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F56F.png" width="32" height="32" alt="LandscapeOrientationMirrored" /></td>
  <td><span data-ttu-id="44fc0-2481">F56F</span><span class="sxs-lookup"><span data-stu-id="44fc0-2481">F56F</span></span></td>
  <td><span data-ttu-id="44fc0-2482">LandscapeOrientationMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-2482">LandscapeOrientationMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F570.png" width="32" height="32" alt="ColorOff" /></td>
  <td><span data-ttu-id="44fc0-2483">F570</span><span class="sxs-lookup"><span data-stu-id="44fc0-2483">F570</span></span></td>
  <td><span data-ttu-id="44fc0-2484">ColorOff</span><span class="sxs-lookup"><span data-stu-id="44fc0-2484">ColorOff</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F571.png" width="32" height="32" alt="PrintAllPages" /></td>
  <td><span data-ttu-id="44fc0-2485">F571</span><span class="sxs-lookup"><span data-stu-id="44fc0-2485">F571</span></span></td>
  <td><span data-ttu-id="44fc0-2486">PrintAllPages</span><span class="sxs-lookup"><span data-stu-id="44fc0-2486">PrintAllPages</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F572.png" width="32" height="32" alt="PrintCustomRange" /></td>
  <td><span data-ttu-id="44fc0-2487">F572</span><span class="sxs-lookup"><span data-stu-id="44fc0-2487">F572</span></span></td>
  <td><span data-ttu-id="44fc0-2488">PrintCustomRange</span><span class="sxs-lookup"><span data-stu-id="44fc0-2488">PrintCustomRange</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F573.png" width="32" height="32" alt="PageMarginPortraitNarrow" /></td>
  <td><span data-ttu-id="44fc0-2489">F573</span><span class="sxs-lookup"><span data-stu-id="44fc0-2489">F573</span></span></td>
  <td><span data-ttu-id="44fc0-2490">PageMarginPortraitNarrow</span><span class="sxs-lookup"><span data-stu-id="44fc0-2490">PageMarginPortraitNarrow</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F574.png" width="32" height="32" alt="PageMarginPortraitNormal" /></td>
  <td><span data-ttu-id="44fc0-2491">F574</span><span class="sxs-lookup"><span data-stu-id="44fc0-2491">F574</span></span></td>
  <td><span data-ttu-id="44fc0-2492">PageMarginPortraitNormal</span><span class="sxs-lookup"><span data-stu-id="44fc0-2492">PageMarginPortraitNormal</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F575.png" width="32" height="32" alt="PageMarginPortraitModerate" /></td>
  <td><span data-ttu-id="44fc0-2493">F575</span><span class="sxs-lookup"><span data-stu-id="44fc0-2493">F575</span></span></td>
  <td><span data-ttu-id="44fc0-2494">PageMarginPortraitModerate</span><span class="sxs-lookup"><span data-stu-id="44fc0-2494">PageMarginPortraitModerate</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F576.png" width="32" height="32" alt="PageMarginPortraitWide" /></td>
  <td><span data-ttu-id="44fc0-2495">F576</span><span class="sxs-lookup"><span data-stu-id="44fc0-2495">F576</span></span></td>
  <td><span data-ttu-id="44fc0-2496">PageMarginPortraitWide</span><span class="sxs-lookup"><span data-stu-id="44fc0-2496">PageMarginPortraitWide</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F577.png" width="32" height="32" alt="PageMarginLandscapeNarrow" /></td>
  <td><span data-ttu-id="44fc0-2497">F577</span><span class="sxs-lookup"><span data-stu-id="44fc0-2497">F577</span></span></td>
  <td><span data-ttu-id="44fc0-2498">PageMarginLandscapeNarrow</span><span class="sxs-lookup"><span data-stu-id="44fc0-2498">PageMarginLandscapeNarrow</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F578.png" width="32" height="32" alt="PageMarginLandscapeNormal" /></td>
  <td><span data-ttu-id="44fc0-2499">F578</span><span class="sxs-lookup"><span data-stu-id="44fc0-2499">F578</span></span></td>
  <td><span data-ttu-id="44fc0-2500">PageMarginLandscapeNormal</span><span class="sxs-lookup"><span data-stu-id="44fc0-2500">PageMarginLandscapeNormal</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F579.png" width="32" height="32" alt="PageMarginLandscapeModerate" /></td>
  <td><span data-ttu-id="44fc0-2501">F579</span><span class="sxs-lookup"><span data-stu-id="44fc0-2501">F579</span></span></td>
  <td><span data-ttu-id="44fc0-2502">PageMarginLandscapeModerate</span><span class="sxs-lookup"><span data-stu-id="44fc0-2502">PageMarginLandscapeModerate</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F57A.png" width="32" height="32" alt="PageMarginLandscapeWide" /></td>
  <td><span data-ttu-id="44fc0-2503">F57A</span><span class="sxs-lookup"><span data-stu-id="44fc0-2503">F57A</span></span></td>
  <td><span data-ttu-id="44fc0-2504">PageMarginLandscapeWide</span><span class="sxs-lookup"><span data-stu-id="44fc0-2504">PageMarginLandscapeWide</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F57B.png" width="32" height="32" alt="CollateLandscape" /></td>
  <td><span data-ttu-id="44fc0-2505">F57B</span><span class="sxs-lookup"><span data-stu-id="44fc0-2505">F57B</span></span></td>
  <td><span data-ttu-id="44fc0-2506">CollateLandscape</span><span class="sxs-lookup"><span data-stu-id="44fc0-2506">CollateLandscape</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F57C.png" width="32" height="32" alt="CollatePortrait" /></td>
  <td><span data-ttu-id="44fc0-2507">F57C</span><span class="sxs-lookup"><span data-stu-id="44fc0-2507">F57C</span></span></td>
  <td><span data-ttu-id="44fc0-2508">CollatePortrait</span><span class="sxs-lookup"><span data-stu-id="44fc0-2508">CollatePortrait</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F57D.png" width="32" height="32" alt="CollatePortraitSeparated" /></td>
  <td><span data-ttu-id="44fc0-2509">F57D</span><span class="sxs-lookup"><span data-stu-id="44fc0-2509">F57D</span></span></td>
  <td><span data-ttu-id="44fc0-2510">CollatePortraitSeparated</span><span class="sxs-lookup"><span data-stu-id="44fc0-2510">CollatePortraitSeparated</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F57E.png" width="32" height="32" alt="DuplexLandscapeOneSided" /></td>
  <td><span data-ttu-id="44fc0-2511">F57E</span><span class="sxs-lookup"><span data-stu-id="44fc0-2511">F57E</span></span></td>
  <td><span data-ttu-id="44fc0-2512">DuplexLandscapeOneSided</span><span class="sxs-lookup"><span data-stu-id="44fc0-2512">DuplexLandscapeOneSided</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F57F.png" width="32" height="32" alt="DuplexLandscapeOneSidedMirrored" /></td>
  <td><span data-ttu-id="44fc0-2513">F57F</span><span class="sxs-lookup"><span data-stu-id="44fc0-2513">F57F</span></span></td>
  <td><span data-ttu-id="44fc0-2514">DuplexLandscapeOneSidedMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-2514">DuplexLandscapeOneSidedMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F580.png" width="32" height="32" alt="DuplexLandscapeTwoSidedLongEdge" /></td>
  <td><span data-ttu-id="44fc0-2515">F580</span><span class="sxs-lookup"><span data-stu-id="44fc0-2515">F580</span></span></td>
  <td><span data-ttu-id="44fc0-2516">DuplexLandscapeTwoSidedLongEdge</span><span class="sxs-lookup"><span data-stu-id="44fc0-2516">DuplexLandscapeTwoSidedLongEdge</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F581.png" width="32" height="32" alt="DuplexLandscapeTwoSidedLongEdgeMirrored" /></td>
  <td><span data-ttu-id="44fc0-2517">F581</span><span class="sxs-lookup"><span data-stu-id="44fc0-2517">F581</span></span></td>
  <td><span data-ttu-id="44fc0-2518">DuplexLandscapeTwoSidedLongEdgeMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-2518">DuplexLandscapeTwoSidedLongEdgeMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F582.png" width="32" height="32" alt="DuplexLandscapeTwoSidedShortEdge" /></td>
  <td><span data-ttu-id="44fc0-2519">F582</span><span class="sxs-lookup"><span data-stu-id="44fc0-2519">F582</span></span></td>
  <td><span data-ttu-id="44fc0-2520">DuplexLandscapeTwoSidedShortEdge</span><span class="sxs-lookup"><span data-stu-id="44fc0-2520">DuplexLandscapeTwoSidedShortEdge</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F583.png" width="32" height="32" alt="DuplexLandscapeTwoSidedShortEdgeMirrored" /></td>
  <td><span data-ttu-id="44fc0-2521">F583</span><span class="sxs-lookup"><span data-stu-id="44fc0-2521">F583</span></span></td>
  <td><span data-ttu-id="44fc0-2522">DuplexLandscapeTwoSidedShortEdgeMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-2522">DuplexLandscapeTwoSidedShortEdgeMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F584.png" width="32" height="32" alt="DuplexPortraitOneSided" /></td>
  <td><span data-ttu-id="44fc0-2523">F584</span><span class="sxs-lookup"><span data-stu-id="44fc0-2523">F584</span></span></td>
  <td><span data-ttu-id="44fc0-2524">DuplexPortraitOneSided</span><span class="sxs-lookup"><span data-stu-id="44fc0-2524">DuplexPortraitOneSided</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F585.png" width="32" height="32" alt="DuplexPortraitOneSidedMirrored" /></td>
  <td><span data-ttu-id="44fc0-2525">F585</span><span class="sxs-lookup"><span data-stu-id="44fc0-2525">F585</span></span></td>
  <td><span data-ttu-id="44fc0-2526">DuplexPortraitOneSidedMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-2526">DuplexPortraitOneSidedMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F586.png" width="32" height="32" alt="DuplexPortraitTwoSidedLongEdge" /></td>
  <td><span data-ttu-id="44fc0-2527">F586</span><span class="sxs-lookup"><span data-stu-id="44fc0-2527">F586</span></span></td>
  <td><span data-ttu-id="44fc0-2528">DuplexPortraitTwoSidedLongEdge</span><span class="sxs-lookup"><span data-stu-id="44fc0-2528">DuplexPortraitTwoSidedLongEdge</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F587.png" width="32" height="32" alt="DuplexPortraitTwoSidedLongEdgeMirrored" /></td>
  <td><span data-ttu-id="44fc0-2529">F587</span><span class="sxs-lookup"><span data-stu-id="44fc0-2529">F587</span></span></td>
  <td><span data-ttu-id="44fc0-2530">DuplexPortraitTwoSidedLongEdgeMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-2530">DuplexPortraitTwoSidedLongEdgeMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F588.png" width="32" height="32" alt="DuplexPortraitTwoSidedShortEdge" /></td>
  <td><span data-ttu-id="44fc0-2531">F588</span><span class="sxs-lookup"><span data-stu-id="44fc0-2531">F588</span></span></td>
  <td><span data-ttu-id="44fc0-2532">DuplexPortraitTwoSidedShortEdge</span><span class="sxs-lookup"><span data-stu-id="44fc0-2532">DuplexPortraitTwoSidedShortEdge</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F589.png" width="32" height="32" alt="DuplexPortraitTwoSidedShortEdgeMirrored" /></td>
  <td><span data-ttu-id="44fc0-2533">F589</span><span class="sxs-lookup"><span data-stu-id="44fc0-2533">F589</span></span></td>
  <td><span data-ttu-id="44fc0-2534">DuplexPortraitTwoSidedShortEdgeMirrored</span><span class="sxs-lookup"><span data-stu-id="44fc0-2534">DuplexPortraitTwoSidedShortEdgeMirrored</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F58A.png" width="32" height="32" alt="PPSOneLandscape" /></td>
  <td><span data-ttu-id="44fc0-2535">F58A</span><span class="sxs-lookup"><span data-stu-id="44fc0-2535">F58A</span></span></td>
  <td><span data-ttu-id="44fc0-2536">PPSOneLandscape</span><span class="sxs-lookup"><span data-stu-id="44fc0-2536">PPSOneLandscape</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F58B.png" width="32" height="32" alt="PPSTwoLandscape" /></td>
  <td><span data-ttu-id="44fc0-2537">F58B</span><span class="sxs-lookup"><span data-stu-id="44fc0-2537">F58B</span></span></td>
  <td><span data-ttu-id="44fc0-2538">PPSTwoLandscape</span><span class="sxs-lookup"><span data-stu-id="44fc0-2538">PPSTwoLandscape</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F58C.png" width="32" height="32" alt="PPSTwoPortrait" /></td>
  <td><span data-ttu-id="44fc0-2539">F58C</span><span class="sxs-lookup"><span data-stu-id="44fc0-2539">F58C</span></span></td>
  <td><span data-ttu-id="44fc0-2540">PPSTwoPortrait</span><span class="sxs-lookup"><span data-stu-id="44fc0-2540">PPSTwoPortrait</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F58D.png" width="32" height="32" alt="PPSFourLandscape" /></td>
  <td><span data-ttu-id="44fc0-2541">F58D</span><span class="sxs-lookup"><span data-stu-id="44fc0-2541">F58D</span></span></td>
  <td><span data-ttu-id="44fc0-2542">PPSFourLandscape</span><span class="sxs-lookup"><span data-stu-id="44fc0-2542">PPSFourLandscape</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F58E.png" width="32" height="32" alt="PPSFourPortrait" /></td>
  <td><span data-ttu-id="44fc0-2543">F58E</span><span class="sxs-lookup"><span data-stu-id="44fc0-2543">F58E</span></span></td>
  <td><span data-ttu-id="44fc0-2544">PPSFourPortrait</span><span class="sxs-lookup"><span data-stu-id="44fc0-2544">PPSFourPortrait</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F58F.png" width="32" height="32" alt="HolePunchOff" /></td>
  <td><span data-ttu-id="44fc0-2545">F58F</span><span class="sxs-lookup"><span data-stu-id="44fc0-2545">F58F</span></span></td>
  <td><span data-ttu-id="44fc0-2546">HolePunchOff</span><span class="sxs-lookup"><span data-stu-id="44fc0-2546">HolePunchOff</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F590.png" width="32" height="32" alt="HolePunchPortraitLeft" /></td>
  <td><span data-ttu-id="44fc0-2547">F590</span><span class="sxs-lookup"><span data-stu-id="44fc0-2547">F590</span></span></td>
  <td><span data-ttu-id="44fc0-2548">HolePunchPortraitLeft</span><span class="sxs-lookup"><span data-stu-id="44fc0-2548">HolePunchPortraitLeft</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F591.png" width="32" height="32" alt="HolePunchPortraitRight" /></td>
  <td><span data-ttu-id="44fc0-2549">F591.</span><span class="sxs-lookup"><span data-stu-id="44fc0-2549">F591</span></span></td>
  <td><span data-ttu-id="44fc0-2550">HolePunchPortraitRight</span><span class="sxs-lookup"><span data-stu-id="44fc0-2550">HolePunchPortraitRight</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F592.png" width="32" height="32" alt="HolePunchPortraitTop" /></td>
  <td><span data-ttu-id="44fc0-2551">F592</span><span class="sxs-lookup"><span data-stu-id="44fc0-2551">F592</span></span></td>
  <td><span data-ttu-id="44fc0-2552">HolePunchPortraitTop</span><span class="sxs-lookup"><span data-stu-id="44fc0-2552">HolePunchPortraitTop</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F593.png" width="32" height="32" alt="HolePunchPortraitBottom" /></td>
  <td><span data-ttu-id="44fc0-2553">F593</span><span class="sxs-lookup"><span data-stu-id="44fc0-2553">F593</span></span></td>
  <td><span data-ttu-id="44fc0-2554">HolePunchPortraitBottom</span><span class="sxs-lookup"><span data-stu-id="44fc0-2554">HolePunchPortraitBottom</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F594.png" width="32" height="32" alt="HolePunchLandscapeLeft" /></td>
  <td><span data-ttu-id="44fc0-2555">F594</span><span class="sxs-lookup"><span data-stu-id="44fc0-2555">F594</span></span></td>
  <td><span data-ttu-id="44fc0-2556">HolePunchLandscapeLeft</span><span class="sxs-lookup"><span data-stu-id="44fc0-2556">HolePunchLandscapeLeft</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F595.png" width="32" height="32" alt="HolePunchLandscapeRight" /></td>
  <td><span data-ttu-id="44fc0-2557">F595</span><span class="sxs-lookup"><span data-stu-id="44fc0-2557">F595</span></span></td>
  <td><span data-ttu-id="44fc0-2558">HolePunchLandscapeRight</span><span class="sxs-lookup"><span data-stu-id="44fc0-2558">HolePunchLandscapeRight</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F596.png" width="32" height="32" alt="HolePunchLandscapeTop" /></td>
  <td><span data-ttu-id="44fc0-2559">F596</span><span class="sxs-lookup"><span data-stu-id="44fc0-2559">F596</span></span></td>
  <td><span data-ttu-id="44fc0-2560">HolePunchLandscapeTop</span><span class="sxs-lookup"><span data-stu-id="44fc0-2560">HolePunchLandscapeTop</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F597.png" width="32" height="32" alt="HolePunchLandscapeBottom" /></td>
  <td><span data-ttu-id="44fc0-2561">F597</span><span class="sxs-lookup"><span data-stu-id="44fc0-2561">F597</span></span></td>
  <td><span data-ttu-id="44fc0-2562">HolePunchLandscapeBottom</span><span class="sxs-lookup"><span data-stu-id="44fc0-2562">HolePunchLandscapeBottom</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F598.png" width="32" height="32" alt="StaplingOff" /></td>
  <td><span data-ttu-id="44fc0-2563">F598</span><span class="sxs-lookup"><span data-stu-id="44fc0-2563">F598</span></span></td>
  <td><span data-ttu-id="44fc0-2564">StaplingOff</span><span class="sxs-lookup"><span data-stu-id="44fc0-2564">StaplingOff</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F599.png" width="32" height="32" alt="StaplingPortraitTopLeft" /></td>
  <td><span data-ttu-id="44fc0-2565">F599</span><span class="sxs-lookup"><span data-stu-id="44fc0-2565">F599</span></span></td>
  <td><span data-ttu-id="44fc0-2566">StaplingPortraitTopLeft</span><span class="sxs-lookup"><span data-stu-id="44fc0-2566">StaplingPortraitTopLeft</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F59A.png" width="32" height="32" alt="StaplingPortraitTopRight" /></td>
  <td><span data-ttu-id="44fc0-2567">F59A</span><span class="sxs-lookup"><span data-stu-id="44fc0-2567">F59A</span></span></td>
  <td><span data-ttu-id="44fc0-2568">StaplingPortraitTopRight</span><span class="sxs-lookup"><span data-stu-id="44fc0-2568">StaplingPortraitTopRight</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F59B.png" width="32" height="32" alt="StaplingPortraitBottomRight" /></td>
  <td><span data-ttu-id="44fc0-2569">F59B</span><span class="sxs-lookup"><span data-stu-id="44fc0-2569">F59B</span></span></td>
  <td><span data-ttu-id="44fc0-2570">StaplingPortraitBottomRight</span><span class="sxs-lookup"><span data-stu-id="44fc0-2570">StaplingPortraitBottomRight</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F59C.png" width="32" height="32" alt="StaplingPortraitTwoLeft" /></td>
  <td><span data-ttu-id="44fc0-2571">F59C</span><span class="sxs-lookup"><span data-stu-id="44fc0-2571">F59C</span></span></td>
  <td><span data-ttu-id="44fc0-2572">StaplingPortraitTwoLeft</span><span class="sxs-lookup"><span data-stu-id="44fc0-2572">StaplingPortraitTwoLeft</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F59D.png" width="32" height="32" alt="StaplingPortraitTwoRight" /></td>
  <td><span data-ttu-id="44fc0-2573">F59D</span><span class="sxs-lookup"><span data-stu-id="44fc0-2573">F59D</span></span></td>
  <td><span data-ttu-id="44fc0-2574">StaplingPortraitTwoRight</span><span class="sxs-lookup"><span data-stu-id="44fc0-2574">StaplingPortraitTwoRight</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F59E.png" width="32" height="32" alt="StaplingPortraitTwoTop" /></td>
  <td><span data-ttu-id="44fc0-2575">F59E</span><span class="sxs-lookup"><span data-stu-id="44fc0-2575">F59E</span></span></td>
  <td><span data-ttu-id="44fc0-2576">StaplingPortraitTwoTop</span><span class="sxs-lookup"><span data-stu-id="44fc0-2576">StaplingPortraitTwoTop</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F59F.png" width="32" height="32" alt="StaplingPortraitTwoBottom" /></td>
  <td><span data-ttu-id="44fc0-2577">F59F</span><span class="sxs-lookup"><span data-stu-id="44fc0-2577">F59F</span></span></td>
  <td><span data-ttu-id="44fc0-2578">StaplingPortraitTwoBottom</span><span class="sxs-lookup"><span data-stu-id="44fc0-2578">StaplingPortraitTwoBottom</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F5A0.png" width="32" height="32" alt="StaplingPortraitBookBinding" /></td>
  <td><span data-ttu-id="44fc0-2579">F5A0</span><span class="sxs-lookup"><span data-stu-id="44fc0-2579">F5A0</span></span></td>
  <td><span data-ttu-id="44fc0-2580">StaplingPortraitBookBinding</span><span class="sxs-lookup"><span data-stu-id="44fc0-2580">StaplingPortraitBookBinding</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F5A1.png" width="32" height="32" alt="StaplingLandscapeTopLeft" /></td>
  <td><span data-ttu-id="44fc0-2581">F5A1</span><span class="sxs-lookup"><span data-stu-id="44fc0-2581">F5A1</span></span></td>
  <td><span data-ttu-id="44fc0-2582">StaplingLandscapeTopLeft</span><span class="sxs-lookup"><span data-stu-id="44fc0-2582">StaplingLandscapeTopLeft</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F5A2.png" width="32" height="32" alt="StaplingLandscapeTopRight" /></td>
  <td><span data-ttu-id="44fc0-2583">F5A2</span><span class="sxs-lookup"><span data-stu-id="44fc0-2583">F5A2</span></span></td>
  <td><span data-ttu-id="44fc0-2584">StaplingLandscapeTopRight</span><span class="sxs-lookup"><span data-stu-id="44fc0-2584">StaplingLandscapeTopRight</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F5A3.png" width="32" height="32" alt="StaplingLandscapeBottomLeft" /></td>
  <td><span data-ttu-id="44fc0-2585">F5A3</span><span class="sxs-lookup"><span data-stu-id="44fc0-2585">F5A3</span></span></td>
  <td><span data-ttu-id="44fc0-2586">StaplingLandscapeBottomLeft</span><span class="sxs-lookup"><span data-stu-id="44fc0-2586">StaplingLandscapeBottomLeft</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F5A4.png" width="32" height="32" alt="StaplingLandscapeBottomRight" /></td>
  <td><span data-ttu-id="44fc0-2587">F5A4</span><span class="sxs-lookup"><span data-stu-id="44fc0-2587">F5A4</span></span></td>
  <td><span data-ttu-id="44fc0-2588">StaplingLandscapeBottomRight</span><span class="sxs-lookup"><span data-stu-id="44fc0-2588">StaplingLandscapeBottomRight</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F5A5.png" width="32" height="32" alt="StaplingLandscapeTwoLeft" /></td>
  <td><span data-ttu-id="44fc0-2589">F5A5</span><span class="sxs-lookup"><span data-stu-id="44fc0-2589">F5A5</span></span></td>
  <td><span data-ttu-id="44fc0-2590">StaplingLandscapeTwoLeft</span><span class="sxs-lookup"><span data-stu-id="44fc0-2590">StaplingLandscapeTwoLeft</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F5A6.png" width="32" height="32" alt="StaplingLandscapeTwoRight" /></td>
  <td><span data-ttu-id="44fc0-2591">F5A6</span><span class="sxs-lookup"><span data-stu-id="44fc0-2591">F5A6</span></span></td>
  <td><span data-ttu-id="44fc0-2592">StaplingLandscapeTwoRight</span><span class="sxs-lookup"><span data-stu-id="44fc0-2592">StaplingLandscapeTwoRight</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F5A7.png" width="32" height="32" alt="StaplingLandscapeTwoTop" /></td>
  <td><span data-ttu-id="44fc0-2593">F5A7</span><span class="sxs-lookup"><span data-stu-id="44fc0-2593">F5A7</span></span></td>
  <td><span data-ttu-id="44fc0-2594">StaplingLandscapeTwoTop</span><span class="sxs-lookup"><span data-stu-id="44fc0-2594">StaplingLandscapeTwoTop</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F5A8.png" width="32" height="32" alt="StaplingLandscapeTwoBottom" /></td>
  <td><span data-ttu-id="44fc0-2595">F5A8</span><span class="sxs-lookup"><span data-stu-id="44fc0-2595">F5A8</span></span></td>
  <td><span data-ttu-id="44fc0-2596">StaplingLandscapeTwoBottom</span><span class="sxs-lookup"><span data-stu-id="44fc0-2596">StaplingLandscapeTwoBottom</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F5A9.png" width="32" height="32" alt="StaplingLandscapeBookBinding" /></td>
  <td><span data-ttu-id="44fc0-2597">F5A9</span><span class="sxs-lookup"><span data-stu-id="44fc0-2597">F5A9</span></span></td>
  <td><span data-ttu-id="44fc0-2598">StaplingLandscapeBookBinding</span><span class="sxs-lookup"><span data-stu-id="44fc0-2598">StaplingLandscapeBookBinding</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F5AB.png" width="32" height="32" alt="MobSIMError" /></td>
  <td><span data-ttu-id="44fc0-2599">F5AB</span><span class="sxs-lookup"><span data-stu-id="44fc0-2599">F5AB</span></span></td>
  <td><span data-ttu-id="44fc0-2600">MobSIMError</span><span class="sxs-lookup"><span data-stu-id="44fc0-2600">MobSIMError</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F5AC.png" width="32" height="32" alt="CollateLandscapeSeparated" /></td>
  <td><span data-ttu-id="44fc0-2601">F5AC</span><span class="sxs-lookup"><span data-stu-id="44fc0-2601">F5AC</span></span></td>
  <td><span data-ttu-id="44fc0-2602">CollateLandscapeSeparated</span><span class="sxs-lookup"><span data-stu-id="44fc0-2602">CollateLandscapeSeparated</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F5AD.png" width="32" height="32" alt="PPSOnePortrait" /></td>
  <td><span data-ttu-id="44fc0-2603">F5AD</span><span class="sxs-lookup"><span data-stu-id="44fc0-2603">F5AD</span></span></td>
  <td><span data-ttu-id="44fc0-2604">PPSOnePortrait</span><span class="sxs-lookup"><span data-stu-id="44fc0-2604">PPSOnePortrait</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F5AE.png" width="32" height="32" alt="StaplingPortraitBottomLeft" /></td>
  <td><span data-ttu-id="44fc0-2605">F5AE</span><span class="sxs-lookup"><span data-stu-id="44fc0-2605">F5AE</span></span></td>
  <td><span data-ttu-id="44fc0-2606">StaplingPortraitBottomLeft</span><span class="sxs-lookup"><span data-stu-id="44fc0-2606">StaplingPortraitBottomLeft</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F5B0.png" width="32" height="32" alt="PlaySolid" /></td>
  <td><span data-ttu-id="44fc0-2607">F5B0</span><span class="sxs-lookup"><span data-stu-id="44fc0-2607">F5B0</span></span></td>
  <td><span data-ttu-id="44fc0-2608">PlaySolid</span><span class="sxs-lookup"><span data-stu-id="44fc0-2608">PlaySolid</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F5ED.png" width="32" height="32" alt="Set" /></td>
  <td><span data-ttu-id="44fc0-2609">F5ED</span><span class="sxs-lookup"><span data-stu-id="44fc0-2609">F5ED</span></span></td>
  <td><span data-ttu-id="44fc0-2610">Legen Sie fest</span><span class="sxs-lookup"><span data-stu-id="44fc0-2610">Set</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F5EE.png" width="32" height="32" alt="SetSolid" /></td>
  <td><span data-ttu-id="44fc0-2611">F5EE</span><span class="sxs-lookup"><span data-stu-id="44fc0-2611">F5EE</span></span></td>
  <td><span data-ttu-id="44fc0-2612">SetSolid</span><span class="sxs-lookup"><span data-stu-id="44fc0-2612">SetSolid</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F5EF.png" width="32" height="32" alt="FuzzyReading" /></td>
  <td><span data-ttu-id="44fc0-2613">F5EF</span><span class="sxs-lookup"><span data-stu-id="44fc0-2613">F5EF</span></span></td>
  <td><span data-ttu-id="44fc0-2614">FuzzyReading</span><span class="sxs-lookup"><span data-stu-id="44fc0-2614">FuzzyReading</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F5F2.png" width="32" height="32" alt="VerticalBattery0" /></td>
  <td><span data-ttu-id="44fc0-2615">F5F2</span><span class="sxs-lookup"><span data-stu-id="44fc0-2615">F5F2</span></span></td>
  <td><span data-ttu-id="44fc0-2616">VerticalBattery0</span><span class="sxs-lookup"><span data-stu-id="44fc0-2616">VerticalBattery0</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F5F3.png" width="32" height="32" alt="VerticalBattery1" /></td>
  <td><span data-ttu-id="44fc0-2617">F5F3</span><span class="sxs-lookup"><span data-stu-id="44fc0-2617">F5F3</span></span></td>
  <td><span data-ttu-id="44fc0-2618">VerticalBattery1</span><span class="sxs-lookup"><span data-stu-id="44fc0-2618">VerticalBattery1</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F5F4.png" width="32" height="32" alt="VerticalBattery2" /></td>
  <td><span data-ttu-id="44fc0-2619">F5F4</span><span class="sxs-lookup"><span data-stu-id="44fc0-2619">F5F4</span></span></td>
  <td><span data-ttu-id="44fc0-2620">VerticalBattery2</span><span class="sxs-lookup"><span data-stu-id="44fc0-2620">VerticalBattery2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F5F5.png" width="32" height="32" alt="VerticalBattery3" /></td>
  <td><span data-ttu-id="44fc0-2621">F5F5</span><span class="sxs-lookup"><span data-stu-id="44fc0-2621">F5F5</span></span></td>
  <td><span data-ttu-id="44fc0-2622">VerticalBattery3</span><span class="sxs-lookup"><span data-stu-id="44fc0-2622">VerticalBattery3</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F5F6.png" width="32" height="32" alt="VerticalBattery4" /></td>
  <td><span data-ttu-id="44fc0-2623">F5F6</span><span class="sxs-lookup"><span data-stu-id="44fc0-2623">F5F6</span></span></td>
  <td><span data-ttu-id="44fc0-2624">VerticalBattery4</span><span class="sxs-lookup"><span data-stu-id="44fc0-2624">VerticalBattery4</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F5F7.png" width="32" height="32" alt="VerticalBattery5" /></td>
  <td><span data-ttu-id="44fc0-2625">F5F7</span><span class="sxs-lookup"><span data-stu-id="44fc0-2625">F5F7</span></span></td>
  <td><span data-ttu-id="44fc0-2626">VerticalBattery5</span><span class="sxs-lookup"><span data-stu-id="44fc0-2626">VerticalBattery5</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F5F8.png" width="32" height="32" alt="VerticalBattery6" /></td>
  <td><span data-ttu-id="44fc0-2627">F5F8</span><span class="sxs-lookup"><span data-stu-id="44fc0-2627">F5F8</span></span></td>
  <td><span data-ttu-id="44fc0-2628">VerticalBattery6</span><span class="sxs-lookup"><span data-stu-id="44fc0-2628">VerticalBattery6</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F5F9.png" width="32" height="32" alt="VerticalBattery7" /></td>
  <td><span data-ttu-id="44fc0-2629">F5F9</span><span class="sxs-lookup"><span data-stu-id="44fc0-2629">F5F9</span></span></td>
  <td><span data-ttu-id="44fc0-2630">VerticalBattery7</span><span class="sxs-lookup"><span data-stu-id="44fc0-2630">VerticalBattery7</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F5FA.png" width="32" height="32" alt="VerticalBattery8" /></td>
  <td><span data-ttu-id="44fc0-2631">F5FA</span><span class="sxs-lookup"><span data-stu-id="44fc0-2631">F5FA</span></span></td>
  <td><span data-ttu-id="44fc0-2632">VerticalBattery8</span><span class="sxs-lookup"><span data-stu-id="44fc0-2632">VerticalBattery8</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F5FB.png" width="32" height="32" alt="VerticalBattery9" /></td>
  <td><span data-ttu-id="44fc0-2633">F5FB</span><span class="sxs-lookup"><span data-stu-id="44fc0-2633">F5FB</span></span></td>
  <td><span data-ttu-id="44fc0-2634">VerticalBattery9</span><span class="sxs-lookup"><span data-stu-id="44fc0-2634">VerticalBattery9</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F5FC.png" width="32" height="32" alt="VerticalBattery10" /></td>
  <td><span data-ttu-id="44fc0-2635">F5FC</span><span class="sxs-lookup"><span data-stu-id="44fc0-2635">F5FC</span></span></td>
  <td><span data-ttu-id="44fc0-2636">VerticalBattery10</span><span class="sxs-lookup"><span data-stu-id="44fc0-2636">VerticalBattery10</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F5FD.png" width="32" height="32" alt="VerticalBatteryCharging0" /></td>
  <td><span data-ttu-id="44fc0-2637">F5FD</span><span class="sxs-lookup"><span data-stu-id="44fc0-2637">F5FD</span></span></td>
  <td><span data-ttu-id="44fc0-2638">VerticalBatteryCharging0</span><span class="sxs-lookup"><span data-stu-id="44fc0-2638">VerticalBatteryCharging0</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F5FE.png" width="32" height="32" alt="VerticalBatteryCharging1" /></td>
  <td><span data-ttu-id="44fc0-2639">F5FE</span><span class="sxs-lookup"><span data-stu-id="44fc0-2639">F5FE</span></span></td>
  <td><span data-ttu-id="44fc0-2640">VerticalBatteryCharging1</span><span class="sxs-lookup"><span data-stu-id="44fc0-2640">VerticalBatteryCharging1</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F5FF.png" width="32" height="32" alt="VerticalBatteryCharging2" /></td>
  <td><span data-ttu-id="44fc0-2641">F5FF</span><span class="sxs-lookup"><span data-stu-id="44fc0-2641">F5FF</span></span></td>
  <td><span data-ttu-id="44fc0-2642">VerticalBatteryCharging2</span><span class="sxs-lookup"><span data-stu-id="44fc0-2642">VerticalBatteryCharging2</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F600.png" width="32" height="32" alt="VerticalBatteryCharging3" /></td>
  <td><span data-ttu-id="44fc0-2643">F600</span><span class="sxs-lookup"><span data-stu-id="44fc0-2643">F600</span></span></td>
  <td><span data-ttu-id="44fc0-2644">VerticalBatteryCharging3</span><span class="sxs-lookup"><span data-stu-id="44fc0-2644">VerticalBatteryCharging3</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F601.png" width="32" height="32" alt="VerticalBatteryCharging4" /></td>
  <td><span data-ttu-id="44fc0-2645">F601</span><span class="sxs-lookup"><span data-stu-id="44fc0-2645">F601</span></span></td>
  <td><span data-ttu-id="44fc0-2646">VerticalBatteryCharging4</span><span class="sxs-lookup"><span data-stu-id="44fc0-2646">VerticalBatteryCharging4</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F602.png" width="32" height="32" alt="VerticalBatteryCharging5" /></td>
  <td><span data-ttu-id="44fc0-2647">F602</span><span class="sxs-lookup"><span data-stu-id="44fc0-2647">F602</span></span></td>
  <td><span data-ttu-id="44fc0-2648">VerticalBatteryCharging5</span><span class="sxs-lookup"><span data-stu-id="44fc0-2648">VerticalBatteryCharging5</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F603.png" width="32" height="32" alt="VerticalBatteryCharging6" /></td>
  <td><span data-ttu-id="44fc0-2649">F603</span><span class="sxs-lookup"><span data-stu-id="44fc0-2649">F603</span></span></td>
  <td><span data-ttu-id="44fc0-2650">VerticalBatteryCharging6</span><span class="sxs-lookup"><span data-stu-id="44fc0-2650">VerticalBatteryCharging6</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F604.png" width="32" height="32" alt="VerticalBatteryCharging7" /></td>
  <td><span data-ttu-id="44fc0-2651">F604</span><span class="sxs-lookup"><span data-stu-id="44fc0-2651">F604</span></span></td>
  <td><span data-ttu-id="44fc0-2652">VerticalBatteryCharging7</span><span class="sxs-lookup"><span data-stu-id="44fc0-2652">VerticalBatteryCharging7</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F605.png" width="32" height="32" alt="VerticalBatteryCharging8" /></td>
  <td><span data-ttu-id="44fc0-2653">F605</span><span class="sxs-lookup"><span data-stu-id="44fc0-2653">F605</span></span></td>
  <td><span data-ttu-id="44fc0-2654">VerticalBatteryCharging8</span><span class="sxs-lookup"><span data-stu-id="44fc0-2654">VerticalBatteryCharging8</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F606.png" width="32" height="32" alt="VerticalBatteryCharging9" /></td>
  <td><span data-ttu-id="44fc0-2655">F606</span><span class="sxs-lookup"><span data-stu-id="44fc0-2655">F606</span></span></td>
  <td><span data-ttu-id="44fc0-2656">VerticalBatteryCharging9</span><span class="sxs-lookup"><span data-stu-id="44fc0-2656">VerticalBatteryCharging9</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F607.png" width="32" height="32" alt="VerticalBatteryCharging10" /></td>
  <td><span data-ttu-id="44fc0-2657">F607</span><span class="sxs-lookup"><span data-stu-id="44fc0-2657">F607</span></span></td>
  <td><span data-ttu-id="44fc0-2658">VerticalBatteryCharging10</span><span class="sxs-lookup"><span data-stu-id="44fc0-2658">VerticalBatteryCharging10</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F608.png" width="32" height="32" alt="VerticalBatteryUnknown" /></td>
  <td><span data-ttu-id="44fc0-2659">F608</span><span class="sxs-lookup"><span data-stu-id="44fc0-2659">F608</span></span></td>
  <td><span data-ttu-id="44fc0-2660">VerticalBatteryUnknown</span><span class="sxs-lookup"><span data-stu-id="44fc0-2660">VerticalBatteryUnknown</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F618.png" width="32" height="32" alt="SIMError" /></td>
  <td><span data-ttu-id="44fc0-2661">F618</span><span class="sxs-lookup"><span data-stu-id="44fc0-2661">F618</span></span></td>
  <td><span data-ttu-id="44fc0-2662">SIMError</span><span class="sxs-lookup"><span data-stu-id="44fc0-2662">SIMError</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F619.png" width="32" height="32" alt="SIMMissing" /></td>
  <td><span data-ttu-id="44fc0-2663">F619</span><span class="sxs-lookup"><span data-stu-id="44fc0-2663">F619</span></span></td>
  <td><span data-ttu-id="44fc0-2664">SIMMissing</span><span class="sxs-lookup"><span data-stu-id="44fc0-2664">SIMMissing</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F61A.png" width="32" height="32" alt="SIMLock" /></td>
  <td><span data-ttu-id="44fc0-2665">F61A</span><span class="sxs-lookup"><span data-stu-id="44fc0-2665">F61A</span></span></td>
  <td><span data-ttu-id="44fc0-2666">SIMLock</span><span class="sxs-lookup"><span data-stu-id="44fc0-2666">SIMLock</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F61B.png" width="32" height="32" alt="eSIM" /></td>
  <td><span data-ttu-id="44fc0-2667">F61B</span><span class="sxs-lookup"><span data-stu-id="44fc0-2667">F61B</span></span></td>
  <td><span data-ttu-id="44fc0-2668">eSIM</span><span class="sxs-lookup"><span data-stu-id="44fc0-2668">eSIM</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F61C.png" width="32" height="32" alt="eSIMNoProfile" /></td>
  <td><span data-ttu-id="44fc0-2669">F61C</span><span class="sxs-lookup"><span data-stu-id="44fc0-2669">F61C</span></span></td>
  <td><span data-ttu-id="44fc0-2670">eSIMNoProfile</span><span class="sxs-lookup"><span data-stu-id="44fc0-2670">eSIMNoProfile</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F61D.png" width="32" height="32" alt="eSIMLocked" /></td>
  <td><span data-ttu-id="44fc0-2671">F61D</span><span class="sxs-lookup"><span data-stu-id="44fc0-2671">F61D</span></span></td>
  <td><span data-ttu-id="44fc0-2672">eSIMLocked</span><span class="sxs-lookup"><span data-stu-id="44fc0-2672">eSIMLocked</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F61E.png" width="32" height="32" alt="eSIMBusy" /></td>
  <td><span data-ttu-id="44fc0-2673">F61E</span><span class="sxs-lookup"><span data-stu-id="44fc0-2673">F61E</span></span></td>
  <td><span data-ttu-id="44fc0-2674">eSIMBusy</span><span class="sxs-lookup"><span data-stu-id="44fc0-2674">eSIMBusy</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F61F.png" width="32" height="32" alt="NoiseCancelation" /></td>
  <td><span data-ttu-id="44fc0-2675">F61F</span><span class="sxs-lookup"><span data-stu-id="44fc0-2675">F61F</span></span></td>
  <td><span data-ttu-id="44fc0-2676">NoiseCancelation</span><span class="sxs-lookup"><span data-stu-id="44fc0-2676">NoiseCancelation</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F620.png" width="32" height="32" alt="NoiseCancelationOff" /></td>
  <td><span data-ttu-id="44fc0-2677">F620</span><span class="sxs-lookup"><span data-stu-id="44fc0-2677">F620</span></span></td>
  <td><span data-ttu-id="44fc0-2678">NoiseCancelationOff</span><span class="sxs-lookup"><span data-stu-id="44fc0-2678">NoiseCancelationOff</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F623.png" width="32" height="32" alt="MusicSharing" /></td>
  <td><span data-ttu-id="44fc0-2679">F623</span><span class="sxs-lookup"><span data-stu-id="44fc0-2679">F623</span></span></td>
  <td><span data-ttu-id="44fc0-2680">MusicSharing</span><span class="sxs-lookup"><span data-stu-id="44fc0-2680">MusicSharing</span></span></td>
 </tr>
<tr><td><img src="images/segoe-mdl/F624.png" width="32" height="32" alt="MusicSharingOff" /></td>
  <td><span data-ttu-id="44fc0-2681">F624</span><span class="sxs-lookup"><span data-stu-id="44fc0-2681">F624</span></span></td>
  <td><span data-ttu-id="44fc0-2682">MusicSharingOff</span><span class="sxs-lookup"><span data-stu-id="44fc0-2682">MusicSharingOff</span></span></td>
 </tr>
</table>



## <a name="related-articles"></a><span data-ttu-id="44fc0-2683">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="44fc0-2683">Related articles</span></span>

* [<span data-ttu-id="44fc0-2684">Richtlinien für Symbole</span><span class="sxs-lookup"><span data-stu-id="44fc0-2684">Guidelines for icons</span></span>](../style/icons.md)
* [<span data-ttu-id="44fc0-2685">Symbol-Enumeration</span><span class="sxs-lookup"><span data-stu-id="44fc0-2685">Symbol enumeration</span></span>](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Controls.Symbol)
* [<span data-ttu-id="44fc0-2686">FontIcon-Klasse</span><span class="sxs-lookup"><span data-stu-id="44fc0-2686">FontIcon class</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.fonticon)


