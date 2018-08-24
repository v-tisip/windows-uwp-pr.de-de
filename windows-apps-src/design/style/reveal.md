---
author: mijacobs
description: Einblendungen sind neue Lichteffekte, welche die interaktiven Elemente in Ihrer App mit Tiefe und Fokus versehen kann.
title: Anzeigen der Hervorhebung
template: detail.hbs
ms.author: mijacobs
ms.date: 08/9/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
pm-contact: kisai
design-contact: conrwi
dev-contact: jevansa
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 67bd984f4216be9eded51b6175829828e9c332f1
ms.sourcegitcommit: c6d6f8b54253e79354f8db14e5cf3b113a3e5014
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "2830882"
---
# <a name="reveal-highlight"></a><span data-ttu-id="c26ba-104">Anzeigen der Hervorhebung</span><span class="sxs-lookup"><span data-stu-id="c26ba-104">Reveal Highlight</span></span>

![Favoritenbild](images/header-reveal-highlight.svg)

<span data-ttu-id="c26ba-106">Anzuzeigen Sie, dass Hervorhebung einen Beleuchtungseffekt ist, der wichtigsten interaktive Elemente, wie etwa Befehlsleisten, wenn der Benutzer den Zeiger in der Nähe sie bewegt.</span><span class="sxs-lookup"><span data-stu-id="c26ba-106">Reveal Highlight is a lighting effect that highlights interactive elements, such as command bars, when the user moves the pointer near them.</span></span> 

> <span data-ttu-id="c26ba-107">**Wichtige APIs**: [RevealBrush-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.revealbrush), [RevealBackgroundBrush-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.revealbackgroundbrush), [RevealBorderBrush-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.revealborderbrush), [RevealBrushHelper-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.revealbrushhelper), [VisualState-Klasse](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.VisualState)</span><span class="sxs-lookup"><span data-stu-id="c26ba-107">**Important APIs**: [RevealBrush class](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.revealbrush), [RevealBackgroundBrush class](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.revealbackgroundbrush), [RevealBorderBrush class](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.revealborderbrush), [RevealBrushHelper class](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.revealbrushhelper), [VisualState class](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.VisualState)</span></span>

## <a name="how-it-works"></a><span data-ttu-id="c26ba-108">Funktionsweise</span><span class="sxs-lookup"><span data-stu-id="c26ba-108">How it works</span></span>
<span data-ttu-id="c26ba-109">Ermitteln Sie Hervorhebung Anrufe Aufmerksamkeit auf interaktive Elemente, indem Sie Container für das Element ausgeblendet, wenn der Mauszeiger in der Nähe, wie in dieser Abbildung dargestellt ist:</span><span class="sxs-lookup"><span data-stu-id="c26ba-109">Reveal Highlight calls attention to interactive elements by revealing the element's container when the pointer is nearby, as shown in this illustration:</span></span>

![Reveal Visual](images/Nav_Reveal_Animation.gif)

<span data-ttu-id="c26ba-111">Da durch Einblendungen die ausgeblendeten Rahmen um Objekte herum angezeigt werden, entwickeln Benutzer ein besseres Verständnis von dem Raum, mit dem diese Objekte interagieren. Darüber hinaus erfahren sie dadurch, welche Aktionen verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="c26ba-111">By exposing the hidden borders around objects, Reveal gives users a better understanding of the space that they are interacting with, and helps them understand the actions available.</span></span> <span data-ttu-id="c26ba-112">Dies ist besonders bei Listensteuerelementen und Gruppen von Schaltflächen wichtig.</span><span class="sxs-lookup"><span data-stu-id="c26ba-112">This is especially important in list controls and groupings of buttons.</span></span>

## <a name="examples"></a><span data-ttu-id="c26ba-113">Beispiele</span><span class="sxs-lookup"><span data-stu-id="c26ba-113">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="c26ba-114">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="c26ba-114">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="c26ba-115">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/Reveal">die App zu öffnen und Einblendungen in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="c26ba-115">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/Reveal">open the app and see Reveal in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="c26ba-116">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="c26ba-116">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="c26ba-117">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="c26ba-117">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

## <a name="video-summary"></a><span data-ttu-id="c26ba-118">Video-Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="c26ba-118">Video summary</span></span>

> [!VIDEO https://channel9.msdn.com/Events/Windows/Windows-Developer-Day-Fall-Creators-Update/WinDev013/player]

## <a name="how-to-use-it"></a><span data-ttu-id="c26ba-119">Verwendung</span><span class="sxs-lookup"><span data-stu-id="c26ba-119">How to use it</span></span>

<span data-ttu-id="c26ba-120">„Reveal” funktioniert automatisch bei einigen Steuerelementen.</span><span class="sxs-lookup"><span data-stu-id="c26ba-120">Reveal automatically works for some controls.</span></span> <span data-ttu-id="c26ba-121">Für andere Steuerelemente können Reveal Sie durch Zuweisen eines speziellen Formats auf das Steuerelement, wie in den Abschnitten [Aktivieren auf andere Steuerelemente anzuzeigen](#enabling-reveal-on-other-controls) und [Zu benutzerdefinierten Steuerelementen anzeigen aktivieren](#enabling-reveal-on-custom-controls) dieses Artikels beschrieben.</span><span class="sxs-lookup"><span data-stu-id="c26ba-121">For other controls, you can enable Reveal by assigning a special style to the control, as described in the [Enabling Reveal on other controls](#enabling-reveal-on-other-controls) and [Enabling Reveal on custom controls](#enabling-reveal-on-custom-controls) sections of this article.</span></span>

## <a name="controls-that-automatically-use-reveal"></a><span data-ttu-id="c26ba-122">Steuerelemente, die „Reveal” automatisch verwenden</span><span class="sxs-lookup"><span data-stu-id="c26ba-122">Controls that automatically use Reveal</span></span>

- [**<span data-ttu-id="c26ba-123">ListView</span><span class="sxs-lookup"><span data-stu-id="c26ba-123">ListView</span></span>**](../controls-and-patterns/lists.md)
- [**<span data-ttu-id="c26ba-124">GridView</span><span class="sxs-lookup"><span data-stu-id="c26ba-124">GridView</span></span>**](../controls-and-patterns/lists.md)
- [**<span data-ttu-id="c26ba-125">TreeView</span><span class="sxs-lookup"><span data-stu-id="c26ba-125">TreeView</span></span>**](../controls-and-patterns/tree-view.md)
- [**<span data-ttu-id="c26ba-126">NavigationView</span><span class="sxs-lookup"><span data-stu-id="c26ba-126">NavigationView</span></span>**](../controls-and-patterns/navigationview.md)
- [**<span data-ttu-id="c26ba-127">MediaTransportControl</span><span class="sxs-lookup"><span data-stu-id="c26ba-127">MediaTransportControl</span></span>**](../controls-and-patterns/media-playback.md)
- [**<span data-ttu-id="c26ba-128">CommandBar</span><span class="sxs-lookup"><span data-stu-id="c26ba-128">CommandBar</span></span>**](../controls-and-patterns/app-bars.md)

<span data-ttu-id="c26ba-129">Diese Abbildung zeigt markieren anzuzeigen, auf verschiedene Steuerelemente:</span><span class="sxs-lookup"><span data-stu-id="c26ba-129">These illustrations show Reveal Highlight on several different controls:</span></span>

![Beispiele für „Reveal”](images/RevealExamples_Collage.png)


## <a name="enabling-reveal-on-other-controls"></a><span data-ttu-id="c26ba-131">Aktivieren von „Reveal” für andere Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="c26ba-131">Enabling Reveal on other controls</span></span>

<span data-ttu-id="c26ba-132">Für Szenarien, in denen Einblendungen angewendet werden sollten (diese Steuerelemente sind Hauptinhalt und/oder werden in einer Liste oder Auflistungsausrichtung verwendet), haben wir optionale Ressourcenformate bereitgestellt, mithilfe derer Sie Einblendungen für solche Situationen aktivieren können.</span><span class="sxs-lookup"><span data-stu-id="c26ba-132">If you have a scenario where Reveal should be applied (these controls are main content and/or are used in a list or collection orientation), we've provided opt-in resource styles that allow you to enable Reveal for those types of situations.</span></span>

<span data-ttu-id="c26ba-133">Diese Steuerelemente verfügen nicht standardmäßig über Einblendungen, da sie kleinere Steuerelemente sind, die in der Regel als Hilfssteuerelemente für die zentralen Punkte Ihrer Anwendung dienen. Alle Apps sind jedoch verschieden, und wenn diese Steuerelemente in Ihrer App am meisten verwendet werden, stehen Ihnen einige Formate als Hilfe zur Verfügung:</span><span class="sxs-lookup"><span data-stu-id="c26ba-133">These controls do not have Reveal by default as they are smaller controls that are usually helper controls to the main focal points of your application; but every app is different, and if these controls are used the most in your app, we've provided some styles to aid with that:</span></span>

| <span data-ttu-id="c26ba-134">Name des Steuerelements</span><span class="sxs-lookup"><span data-stu-id="c26ba-134">Control Name</span></span>   | <span data-ttu-id="c26ba-135">Ressourcenname</span><span class="sxs-lookup"><span data-stu-id="c26ba-135">Resource Name</span></span> |
|----------|:-------------:|
| <span data-ttu-id="c26ba-136">Button</span><span class="sxs-lookup"><span data-stu-id="c26ba-136">Button</span></span> |  <span data-ttu-id="c26ba-137">ButtonRevealStyle</span><span class="sxs-lookup"><span data-stu-id="c26ba-137">ButtonRevealStyle</span></span> |
| <span data-ttu-id="c26ba-138">ToggleButton</span><span class="sxs-lookup"><span data-stu-id="c26ba-138">ToggleButton</span></span> | <span data-ttu-id="c26ba-139">ToggleButtonRevealStyle</span><span class="sxs-lookup"><span data-stu-id="c26ba-139">ToggleButtonRevealStyle</span></span> |
| <span data-ttu-id="c26ba-140">RepeatButton</span><span class="sxs-lookup"><span data-stu-id="c26ba-140">RepeatButton</span></span> | <span data-ttu-id="c26ba-141">RepeatButtonRevealStyle</span><span class="sxs-lookup"><span data-stu-id="c26ba-141">RepeatButtonRevealStyle</span></span> |
| <span data-ttu-id="c26ba-142">AppBarButton</span><span class="sxs-lookup"><span data-stu-id="c26ba-142">AppBarButton</span></span> | <span data-ttu-id="c26ba-143">AppBarButtonRevealStyle</span><span class="sxs-lookup"><span data-stu-id="c26ba-143">AppBarButtonRevealStyle</span></span> |
| <span data-ttu-id="c26ba-144">AppBarToggleButton</span><span class="sxs-lookup"><span data-stu-id="c26ba-144">AppBarToggleButton</span></span> | <span data-ttu-id="c26ba-145">AppBarToggleButtonRevealStyle</span><span class="sxs-lookup"><span data-stu-id="c26ba-145">AppBarToggleButtonRevealStyle</span></span> |
| <span data-ttu-id="c26ba-146">GridViewItem (Anzeigen über dem Inhalt)</span><span class="sxs-lookup"><span data-stu-id="c26ba-146">GridViewItem (Reveal overtop of content)</span></span> | <span data-ttu-id="c26ba-147">GridViewItemRevealBackgroundShowsAboveContentStyle</span><span class="sxs-lookup"><span data-stu-id="c26ba-147">GridViewItemRevealBackgroundShowsAboveContentStyle</span></span> |

<span data-ttu-id="c26ba-148">Um diese Formate anzuwenden, legen Sie die Eigenschaft [Style](/uwp/api/Windows.UI.Xaml.Style) folgendermaßen fest:</span><span class="sxs-lookup"><span data-stu-id="c26ba-148">To apply these styles, simply set the control's [Style](/uwp/api/Windows.UI.Xaml.Style) property:</span></span>

```xaml
<Button Content="Button Content" Style="{StaticResource ButtonRevealStyle}"/>
```

### <a name="reveal-in-themes"></a><span data-ttu-id="c26ba-149">Einblenden in Designs</span><span class="sxs-lookup"><span data-stu-id="c26ba-149">Reveal in themes</span></span>

<span data-ttu-id="c26ba-150">Einblenden ändert sich je nach angefordertem Design des Steuerelements, der App oder der Einstellung des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="c26ba-150">Reveal changes slightly depending on the requested theme of the control, app or user setting.</span></span> <span data-ttu-id="c26ba-151">Im dunklen Design ist das Licht des Rahmens und der Anzeige weiß, währen in hellem Design nur der Rahmen hellgrau angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="c26ba-151">In Dark theme Reveal's Border and Hover light is white, but in Light theme just the Borders darken to a light gray.</span></span>

![helles und dunkles Einblenden](images/Dark_vs_LightReveal.png)

<span data-ttu-id="c26ba-153">Um weiße Rahmen in einem hellen Design anzuzeigen, setzen Sie einfach das angeforderte Design für das Steuerelement auf dunkel fest.</span><span class="sxs-lookup"><span data-stu-id="c26ba-153">To enabled white borders while in light theme, simply set the requested theme on the control to Dark.</span></span>

```xaml
<Grid RequestedTheme="Dark">
    <Button Content="Button" Click="Button_Click" Style="{ThemeResource ButtonRevealStyle}"/>
</Grid>
```

<span data-ttu-id="c26ba-154">Oder ändern Sie das „TargetTheme” des „RevealBorderBrush” auf Dunkel.</span><span class="sxs-lookup"><span data-stu-id="c26ba-154">Or change the TargetTheme on the RevealBorderBrush to Dark.</span></span> <span data-ttu-id="c26ba-155">Beachten Sie Folgendes!</span><span class="sxs-lookup"><span data-stu-id="c26ba-155">Remember!</span></span> <span data-ttu-id="c26ba-156">Wenn „TargetTheme” auf dunkel festgelegt ist, wird Einblenden weiß angezeigt. Wenn es auf „Light” festgelegt ist, werden die Rahmen grau angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c26ba-156">If the TargetTheme is set to Dark, then Reveal will be white, but if it's set to Light, Reveal's borders will be gray.</span></span>

```xaml
 <RevealBorderBrush x:Key="MyLightBorderBrush" TargetTheme="Dark" Color="{ThemeResource SystemAccentColor}" FallbackColor="{ThemeResource SystemAccentColor}" />
```

## <a name="enabling-reveal-on-custom-controls"></a><span data-ttu-id="c26ba-157">Aktivieren von „Reveal” für benutzerdefinierte Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="c26ba-157">Enabling Reveal on custom controls</span></span>

<span data-ttu-id="c26ba-158">Sie können „Reveal” für benutzerdefinierte Steuerelemente hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="c26ba-158">You can add Reveal to custom controls.</span></span> <span data-ttu-id="c26ba-159">Bevor Sie dies tun, ist es hilfreich, etwas mehr über die Funktionsweise des Effekts von „Reveal” zu erfahren.</span><span class="sxs-lookup"><span data-stu-id="c26ba-159">Before you do, it's helpful to know a little more about about how the Reveal effect works.</span></span> <span data-ttu-id="c26ba-160">„Reveal” besteht aus zwei separaten Effekten: **Reveal border** (Rahmen) und **Reveal hover** (Draufzeigen).</span><span class="sxs-lookup"><span data-stu-id="c26ba-160">Reveal is made up of two separate effects: **Reveal border** and **Reveal hover**.</span></span>

- <span data-ttu-id="c26ba-161">**Rahmen** zeigt die Rahmen der interaktiven Elemente an, wenn sich ein Zeiger nähert.</span><span class="sxs-lookup"><span data-stu-id="c26ba-161">**Border** shows the borders of interactive elements when a pointer is nearby by.</span></span> <span data-ttu-id="c26ba-162">Dadurch können Objekte in der Nähe ähnliche Aktionen wie das aktuell fokussierte Objekt durchführen.</span><span class="sxs-lookup"><span data-stu-id="c26ba-162">This effect shows you that those nearby objects can take actions similar to the one currently focused.</span></span>
- <span data-ttu-id="c26ba-163">Durch **Draufzeigen** wird die angedeutete oder fokussierte Form mit einem leichten Schein umgeben und beim Anklicken wird eine gedrückte Animation angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c26ba-163">**Hover**  applies a gentle halo shape around the hovered or focused item and plays a press animation on click.</span></span> 

![Ebenen einblenden](images/RevealLayers.png)

<!-- The Reveal recipe breakdown is:

- Border reveal will be on top of all content but on the designated edges
- Text and content will be displayed directly under Border Reveal
- Hover reveal will be beneath content and text
- The backplate (that turns on and enables Hover Reveal)
- The background (background of control) -->


<span data-ttu-id="c26ba-165">Diese Effekte werden durch zwei Pinselelemente definiert:</span><span class="sxs-lookup"><span data-stu-id="c26ba-165">These effects are defined by two brushes:</span></span> 
* <span data-ttu-id="c26ba-166">Anzeigen der Rahmen wird durch **RevealBorderBrush** definiert.</span><span class="sxs-lookup"><span data-stu-id="c26ba-166">Border Reveal is defined by  **RevealBorderBrush**</span></span>
* <span data-ttu-id="c26ba-167">Beim Daraufzeigen Reveal wird durch **RevealBackgroundBrush** definiert.</span><span class="sxs-lookup"><span data-stu-id="c26ba-167">Hover Reveal is defined by **RevealBackgroundBrush**</span></span>

```xaml
<RevealBorderBrush x:Key="MyRevealBorderBrush" TargetTheme="Light" Color="{ThemeResource SystemAccentColor}" FallbackColor="{ThemeResource SystemAccentColor}"/>
<RevealBackgroundBrush x:Key="MyRevealBackgroundBrush" TargetTheme="Light" Color="{StaticResource SystemAccentColor}" FallbackColor="{StaticResource SystemAccentColor}" />
```
<span data-ttu-id="c26ba-168">In den meisten Fällen wird „Reveal” für bestimmte Steuerelemente von uns automatisch aktiviert.</span><span class="sxs-lookup"><span data-stu-id="c26ba-168">In most cases we handle the usage of both of them by turning Reveal on automatically for a certain controls.</span></span> <span data-ttu-id="c26ba-169">Andere Steuerelemente müssen jedoch über das Anwenden eines Stils oder das Ändern der Vorlagen direkt aktiviert.</span><span class="sxs-lookup"><span data-stu-id="c26ba-169">However, other controls will need to be enabled through applying a style, or changing their templates directly.</span></span>

### <a name="when-to-add-reveal"></a><span data-ttu-id="c26ba-170">Wann sollte „Reveal” hinzugefügt werden</span><span class="sxs-lookup"><span data-stu-id="c26ba-170">When to add Reveal</span></span>
<span data-ttu-id="c26ba-171">Sie können „Reveal” auf Ihre benutzerdefinierten Steuerelemente hinzufügen – es empfiehlt allerdings, den Typ des Steuerelements und sein Verhalten vorher festzulegen.</span><span class="sxs-lookup"><span data-stu-id="c26ba-171">You can add Reveal to your custom controls--but before you do, consider the type of control and how it behaves.</span></span> 
* <span data-ttu-id="c26ba-172">Wenn Ihr benutzerdefiniertes Steuerelement ein interaktives Element ist und keine ähnlichen Steuerelemente auf der gleichen Oberfläche angezeigt werden (wie z.B. Menüelemente), benötigt das benutzerdefinierte Steuerelement wahrscheinlich keine Einblendung.</span><span class="sxs-lookup"><span data-stu-id="c26ba-172">If your custom control is a single interactive element and doesn't have similar controls sharing it's space (such as menu items in a menu), it's likely that your custom control doesn't need Reveal.</span></span>  
* <span data-ttu-id="c26ba-173">Besitzen Sie eine Gruppe von verwandten interaktiven Inhalten oder Elementen, benötigen die Bereiche der App wahrscheinlich die Einblendung – dies wird häufig als [Steuerung](https://docs.microsoft.com/windows/uwp/design/controls-and-patterns/collection-commanding) der Oberfläche bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="c26ba-173">If you have a grouping of related interactive content or elements, then it's likely that that region of your app does need Reveal - this is commonly referred to as a [Commanding](https://docs.microsoft.com/windows/uwp/design/controls-and-patterns/collection-commanding) surface.</span></span>

<span data-ttu-id="c26ba-174">Eine allein angezeigte Schaltfläche muss keine Einblendung verwenden, aber eine Reihe von Schaltflächen in einer Befehlsleiste sollte „Reveal” verwenden.</span><span class="sxs-lookup"><span data-stu-id="c26ba-174">For example, a button by itself shouldn't use reveal, but a set of buttons in a command bar should use Reveal.</span></span>

<!-- For example, NavigationView's items are related to page navigation. CommandBar's buttons relate to menu actions or page feature actions. MediaTransportControl's buttons beneath all relate to the media being played. -->

### <a name="using-the-control-template-to-add-reveal"></a><span data-ttu-id="c26ba-175">Hinzufügen von „Reveal” mithilfe der Steuerelementvorlage</span><span class="sxs-lookup"><span data-stu-id="c26ba-175">Using the control template to add Reveal</span></span> 
<span data-ttu-id="c26ba-176">Um die Einblendung für benutzerdefinierte Steuerelemente oder Steuerelemente mit neuen Vorlagen zu aktivieren, ändern Sie die Steuerelementvorlage für das Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="c26ba-176">To enable Reveal on custom controls or re-templated controls, you modify the control's control template.</span></span> <span data-ttu-id="c26ba-177">Die meisten Steuerelementvorlagen besitzen ein Raster im Stammverzeichnis. Aktualisieren Sie [VisualState](/uwp/api/windows.ui.xaml.visualstate) des Stamm-Rasters, um die Einblendung zu verwenden:</span><span class="sxs-lookup"><span data-stu-id="c26ba-177">Most control templates have a grid at the root; update the [VisualState](/uwp/api/windows.ui.xaml.visualstate) of that root grid to use Reveal:</span></span>

```xaml
<VisualState x:Name="PointerOver">
    <VisualState.Setters>
        <Setter Target="RootGrid.(RevealBrush.State)" Value="PointerOver" />
        <Setter Target="RootGrid.Background" Value="{ThemeResource ButtonRevealBackgroundPointerOver}" />
        <Setter Target="ContentPresenter.BorderBrush" Value="Transparent"/>
        <Setter Target="ContentPresenter.Foreground" Value="{ThemeResource ButtonForegroundPointerOver}" />
    </VisualState.Setters>
</VisualState>
```

<span data-ttu-id="c26ba-178">Es ist wichtig zu beachten, dass zur Einblendung sowohl ein Pinsel als auch Setter in Visual State benötigt werden, um einwandfrei zu arbeiten.</span><span class="sxs-lookup"><span data-stu-id="c26ba-178">It's important to note that Reveal needs both the brush and the setters in it's Visual State to work correctly.</span></span> <span data-ttu-id="c26ba-179">Das einfache Festlegen eines Steuerelements für Reveal-Pinselressourcen alleine aktivieren das Steuerelement nicht.</span><span class="sxs-lookup"><span data-stu-id="c26ba-179">Simply setting a control's brush to one of our Reveal brush resources alone won't enable Reveal for that control.</span></span> <span data-ttu-id="c26ba-180">Ziele oder Einstellungen zu verwenden ohne die Werte als Reveal-Pinsel festgelegt zu haben, aktiviert die Einblendung auch nicht.</span><span class="sxs-lookup"><span data-stu-id="c26ba-180">Conversely, having only the targets or settings without the values being Reveal brushes will also not enable Reveal.</span></span>

<span data-ttu-id="c26ba-181">Weitere Informationen zum Ändern von Steuerelementvorlagen finden Sie im Artikel [XAML-Steuerelementvorlagen](../controls-and-patterns/control-templates.md) Artikel.</span><span class="sxs-lookup"><span data-stu-id="c26ba-181">To learn more about modifying control templates, see the [XAML control templates](../controls-and-patterns/control-templates.md) article.</span></span>

<span data-ttu-id="c26ba-182">Wir haben eine Reihe von System-Reveal-Pinsels erstellt, mit denen Sie die Vorlagen anpassen können.</span><span class="sxs-lookup"><span data-stu-id="c26ba-182">We've created a set of system Reveal brushes you can use to customize your template.</span></span> <span data-ttu-id="c26ba-183">Sie können z.B. den Pinsel **ButtonRevealBackground** zum Erstellen eines Hintergrunds für eine benutzerdefinierte Schaltfläche oder den Pinsel **ListViewItemRevealBackground** für benutzerdefinierte Listen und so weiter verwenden.</span><span class="sxs-lookup"><span data-stu-id="c26ba-183">For example, you can use the **ButtonRevealBackground** brush to create a custom button background, or the **ListViewItemRevealBackground** brush for custom lists, and so on.</span></span> <span data-ttu-id="c26ba-184">(Informationen zur Funktionsweise von Ressourcen in XAML finden Sie im Artikel [Xaml-Ressourcenverzeichnis](../controls-and-patterns/resourcedictionary-and-xaml-resource-references.md).)</span><span class="sxs-lookup"><span data-stu-id="c26ba-184">(To learn about how resources work in XAML, check out the [Xaml Resource Dictionary](../controls-and-patterns/resourcedictionary-and-xaml-resource-references.md) article.)</span></span>

### <a name="full-template-example"></a><span data-ttu-id="c26ba-185">Vollständiges Vorlagenbeispiel</span><span class="sxs-lookup"><span data-stu-id="c26ba-185">Full template example</span></span>

<span data-ttu-id="c26ba-186">Hier sehen Sie eine gesamte Vorlage und wie eine Schaltfläche zum Einblenden aussehen würde:</span><span class="sxs-lookup"><span data-stu-id="c26ba-186">Here's an entire template for what a Reveal Button would look like:</span></span>

```xaml
<Style TargetType="Button" x:Key="ButtonStyle1">
    <Setter Property="Background" Value="{ThemeResource ButtonRevealBackground}" />
    <Setter Property="Foreground" Value="{ThemeResource ButtonForeground}" />
    <Setter Property="BorderBrush" Value="{ThemeResource ButtonRevealBorderBrush}" />
    <Setter Property="BorderThickness" Value="2" />
    <Setter Property="Padding" Value="8,4,8,4" />
    <Setter Property="HorizontalAlignment" Value="Left" />
    <Setter Property="VerticalAlignment" Value="Center" />
    <Setter Property="FontFamily" Value="{ThemeResource ContentControlThemeFontFamily}" />
    <Setter Property="FontWeight" Value="Normal" />
    <Setter Property="FontSize" Value="{ThemeResource ControlContentThemeFontSize}" />
    <Setter Property="UseSystemFocusVisuals" Value="True" />
    <Setter Property="FocusVisualMargin" Value="-3" />
    <Setter Property="Template">
        <Setter.Value>
            <ControlTemplate TargetType="Button">
                <Grid x:Name="RootGrid" Background="{TemplateBinding Background}">

                    <VisualStateManager.VisualStateGroups>
                        <VisualStateGroup x:Name="CommonStates">
                            <VisualState x:Name="Normal">

                                <Storyboard>
                                    <PointerUpThemeAnimation Storyboard.TargetName="RootGrid" />
                                </Storyboard>
                            </VisualState>

                            <VisualState x:Name="PointerOver">
                                <VisualState.Setters>
                                    <Setter Target="RootGrid.(RevealBrush.State)" Value="PointerOver" />
                                    <Setter Target="RootGrid.Background" Value="{ThemeResource ButtonRevealBackgroundPointerOver}" />
                                    <Setter Target="ContentPresenter.BorderBrush" Value="Transparent"/>
                                    <Setter Target="ContentPresenter.Foreground" Value="{ThemeResource ButtonForegroundPointerOver}" />
                                </VisualState.Setters>

                                <Storyboard>
                                    <PointerUpThemeAnimation Storyboard.TargetName="RootGrid" />
                                </Storyboard>
                            </VisualState>

                            <VisualState x:Name="Pressed">
                                <VisualState.Setters>
                                    <Setter Target="RootGrid.(RevealBrush.State)" Value="Pressed" />
                                    <Setter Target="RootGrid.Background" Value="{ThemeResource ButtonRevealBackgroundPressed}" />
                                    <Setter Target="ContentPresenter.BorderBrush" Value="{ThemeResource ButtonRevealBackgroundPressed}" />
                                    <Setter Target="ContentPresenter.Foreground" Value="{ThemeResource ButtonForegroundPressed}" />
                                </VisualState.Setters>

                                <Storyboard>
                                    <PointerDownThemeAnimation Storyboard.TargetName="RootGrid" />
                                </Storyboard>
                            </VisualState>

                            <VisualState x:Name="Disabled">
                                <VisualState.Setters>
                                    <Setter Target="RootGrid.Background" Value="{ThemeResource ButtonRevealBackgroundDisabled}" />
                                    <Setter Target="ContentPresenter.BorderBrush" Value="{ThemeResource ButtonRevealBorderBrushDisabled}" />
                                    <Setter Target="ContentPresenter.Foreground" Value="{ThemeResource ButtonForegroundDisabled}" />
                                </VisualState.Setters>
                            </VisualState>
                        </VisualStateGroup>

              </VisualStateManager.VisualStateGroups>
                    <ContentPresenter x:Name="ContentPresenter"
                    BorderBrush="{TemplateBinding BorderBrush}"
                    BorderThickness="{TemplateBinding BorderThickness}"
                    Content="{TemplateBinding Content}"
                    ContentTransitions="{TemplateBinding ContentTransitions}"
                    ContentTemplate="{TemplateBinding ContentTemplate}"
                    Padding="{TemplateBinding Padding}"
                    HorizontalContentAlignment="{TemplateBinding HorizontalContentAlignment}"
                    VerticalContentAlignment="{TemplateBinding VerticalContentAlignment}"
                    AutomationProperties.AccessibilityView="Raw" />
                </Grid>
            </ControlTemplate>
        </Setter.Value>
    </Setter>
</Style>
```

### <a name="fine-tuning-the-reveal-effect-on-a-custom-control"></a><span data-ttu-id="c26ba-187">Optimieren des Effekts von „Reveal” für ein benutzerdefiniertes Steuerelement</span><span class="sxs-lookup"><span data-stu-id="c26ba-187">Fine-tuning the Reveal effect on a custom control</span></span> 

<span data-ttu-id="c26ba-188">Wenn Sie auf ein Steuerelement benutzerdefinierte oder Re-Vorlagen oder eine benutzerdefinierte Befehlsinfrastruktur Fläche Reveal aktivieren, helfen Ihnen die folgenden Tipps Ihnen den Effekt optimieren:</span><span class="sxs-lookup"><span data-stu-id="c26ba-188">When you enable Reveal on a custom or re-templated control or a custom commanding surface, these tips can help you optimize the effect:</span></span>
 
* <span data-ttu-id="c26ba-189">Auf benachbarten Elementen mit einer Größe, die nicht in Höhe oder Breite (insbesondere in Listen) ausgerichtet ist: entfernen Sie das Verhalten des Rahmens und aktivieren Sie die Rahmen nur für das Draufzeigen.</span><span class="sxs-lookup"><span data-stu-id="c26ba-189">On adjacent items with sizes that do not align either in height or width (particularly in lists): Remove the border approach behavior and keep the borders shown on hover only.</span></span>
* <span data-ttu-id="c26ba-190">Für Befehlselemente, die häufig aktiviert oder deaktiviert werden: platzieren Sie den Pinsel für den Rahmen auf die Backplates der Elemente sowie deren Rahmen, um ihren Zustand zu betonen.</span><span class="sxs-lookup"><span data-stu-id="c26ba-190">For commanding items that frequently go in and out of the disabled state: Place the border approach brush on the elements' backplates as well as their borders to emphasize their state.</span></span>
* <span data-ttu-id="c26ba-191">Für benachbarte Steuerelemente, die sich fast berühren: Fügen Sie einen Rand von einem Pixel zwischen den beiden Elementen hinzu.</span><span class="sxs-lookup"><span data-stu-id="c26ba-191">For adjacent commanding elements that are so close they touch: Add a 1px margin between the two elements.</span></span> 

## <a name="dos-and-donts"></a><span data-ttu-id="c26ba-192">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="c26ba-192">Do's and don'ts</span></span>
### <a name="do"></a><span data-ttu-id="c26ba-193">Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="c26ba-193">Do:</span></span>
- <span data-ttu-id="c26ba-194">Verwenden Sie „Reveal” für Elemente, in denen der Benutzer viele Aktionen (CommandBars, Navigationsmenüs) ausführt</span><span class="sxs-lookup"><span data-stu-id="c26ba-194">Do use Reveal on elements where the user can take many actions (CommandBars, Navigation menus)</span></span>
- <span data-ttu-id="c26ba-195">Verwenden Sie „Reveal” bei der Gruppierung von interaktiven Elementen, die nicht standardmäßig visuelle Trennzeichen haben (Listen, Menübänder)</span><span class="sxs-lookup"><span data-stu-id="c26ba-195">Do use Reveal in groupings of interactive elements that do not have visual separators by default (lists, ribbons)</span></span>
- <span data-ttu-id="c26ba-196">Verwenden Sie „Reveal” in Bereichen mit vielen interaktiven Elementen (Befehlszenarios)</span><span class="sxs-lookup"><span data-stu-id="c26ba-196">Do use Reveal in areas with a high density of interactive elements (commanding scenarios)</span></span>
- <span data-ttu-id="c26ba-197">Fügen Sie einen Rand von einem Pixel zwischen Einblendungselementen hinzu</span><span class="sxs-lookup"><span data-stu-id="c26ba-197">Do put 1px margin spaces between Reveal items</span></span>

### <a name="dont"></a><span data-ttu-id="c26ba-198">Nicht empfohlen</span><span class="sxs-lookup"><span data-stu-id="c26ba-198">Don't</span></span>
- <span data-ttu-id="c26ba-199">Verwenden Sie „Reveal” nicht auf statischen Inhalten (Hintergrund, Text)</span><span class="sxs-lookup"><span data-stu-id="c26ba-199">Don’t use Reveal on static content (backgrounds, text)</span></span>
- <span data-ttu-id="c26ba-200">Verwenden Sie „Reveal” nicht auf Popups, Flyouts oder Dropdownlisten</span><span class="sxs-lookup"><span data-stu-id="c26ba-200">Don't use Reveal on popups, flyouts or dropdowns</span></span>
- <span data-ttu-id="c26ba-201">Verwenden Sie „Reveal” nicht in einzelnen, isolierten Situationen</span><span class="sxs-lookup"><span data-stu-id="c26ba-201">Don’t use Reveal in one-off, isolated situations</span></span>
- <span data-ttu-id="c26ba-202">Verwenden Sie Einblendungen nicht auf sehr großen Elementen (größer als 500epx)</span><span class="sxs-lookup"><span data-stu-id="c26ba-202">Don’t use Reveal on very large items (greater than 500epx)</span></span>
- <span data-ttu-id="c26ba-203">Verwenden Sie „Reveal” nicht bei sicherheitsbezogenen Entscheidungen, da es die Aufmerksamkeit von der Nachricht, die Sie an die Benutzer übermitteln möchten, weglenken kann.</span><span class="sxs-lookup"><span data-stu-id="c26ba-203">Don’t use Reveal in security decisions, as it may draw attention away from the message you need to deliver to your user</span></span>


## <a name="get-the-sample-code"></a><span data-ttu-id="c26ba-204">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="c26ba-204">Get the sample code</span></span>

- <span data-ttu-id="c26ba-205">[Beispiel eines XAML-Steuerelementkatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="c26ba-205">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>

## <a name="reveal-and-the-fluent-design-system"></a><span data-ttu-id="c26ba-206">„Reveal” und das Fluent Design-System</span><span class="sxs-lookup"><span data-stu-id="c26ba-206">Reveal and the Fluent Design System</span></span>

 <span data-ttu-id="c26ba-207">Mit dem Fluent Design-System erstellen Sie moderne Oberflächen, die Licht, Tiefe, Bewegung, Material und Skalierungsmöglichkeiten beinhalten.</span><span class="sxs-lookup"><span data-stu-id="c26ba-207">The Fluent Design System helps you create modern, bold UI that incorporates light, depth, motion, material, and scale.</span></span> <span data-ttu-id="c26ba-208">„Einblendungen” ist eine Komponente des Fluent Design-Systems, die Lichteffekte in Ihrer App ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="c26ba-208">Reveal is a Fluent Design System component that adds light to your app.</span></span> <span data-ttu-id="c26ba-209">Weitere Informationen finden Sie in der [Fluent Design für UWP-Übersicht](../fluent-design-system/index.md).</span><span class="sxs-lookup"><span data-stu-id="c26ba-209">To learn more, see the [Fluent Design for UWP overview](../fluent-design-system/index.md).</span></span>

## <a name="related-articles"></a><span data-ttu-id="c26ba-210">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="c26ba-210">Related articles</span></span>

- [<span data-ttu-id="c26ba-211">RevealBrush-Klasse</span><span class="sxs-lookup"><span data-stu-id="c26ba-211">RevealBrush class</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.revealbrush)
- [<span data-ttu-id="c26ba-212">Acryl</span><span class="sxs-lookup"><span data-stu-id="c26ba-212">Acrylic</span></span>](acrylic.md)
- [<span data-ttu-id="c26ba-213">Kompositionseffekte</span><span class="sxs-lookup"><span data-stu-id="c26ba-213">Composition Effects</span></span>](https://msdn.microsoft.com/windows/uwp/graphics/composition-effects)
- [<span data-ttu-id="c26ba-214">Fluent Design für UWP</span><span class="sxs-lookup"><span data-stu-id="c26ba-214">Fluent Design for UWP</span></span>](../fluent-design-system/index.md)
- [<span data-ttu-id="c26ba-215">Wissenschaft im System: Fluent Design und Tiefe</span><span class="sxs-lookup"><span data-stu-id="c26ba-215">Science in the System: Fluent Design and Depth</span></span>](https://medium.com/microsoft-design/science-in-the-system-fluent-design-and-depth-fb6d0f23a53f)
- [<span data-ttu-id="c26ba-216">Wissenschaft im System: Fluent Design und Licht</span><span class="sxs-lookup"><span data-stu-id="c26ba-216">Science in the System: Fluent Design and Light</span></span>](https://medium.com/microsoft-design/the-science-in-the-system-fluent-design-and-light-94a17e0b3a4f)
