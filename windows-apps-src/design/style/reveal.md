---
author: mijacobs
description: Einblendungen sind neue Lichteffekte, welche die interaktiven Elemente in Ihrer App mit Tiefe und Fokus versehen kann.
title: Reveal-highlight
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
ms.localizationpriority: high
ms.openlocfilehash: 8ba0d9939d7ab1d9826ed2848e476499f09c628f
ms.sourcegitcommit: 4b522af988273946414a04fbbd1d7fde40f8ba5e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2018
---
# <a name="reveal-highlight"></a><span data-ttu-id="8e9f3-104">Reveal-highlight</span><span class="sxs-lookup"><span data-stu-id="8e9f3-104">Reveal highlight</span></span>

<span data-ttu-id="8e9f3-105">Einblendungen sind neue Lichteffekte, welche die interaktiven Elemente in Ihrer App mit Tiefe und Fokus versehen kann.</span><span class="sxs-lookup"><span data-stu-id="8e9f3-105">Reveal is a lighting effect that helps bring depth and focus to your app's interactive elements.</span></span>

> <span data-ttu-id="8e9f3-106">**Wichtige APIs**: [RevealBrush-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.revealbrush), [RevealBackgroundBrush-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.revealbackgroundbrush), [RevealBorderBrush-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.revealborderbrush), [RevealBrushHelper-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.revealbrushhelper), [VisualState-Klasse](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.VisualState)</span><span class="sxs-lookup"><span data-stu-id="8e9f3-106">**Important APIs**: [RevealBrush class](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.revealbrush), [RevealBackgroundBrush class](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.revealbackgroundbrush), [RevealBorderBrush class](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.revealborderbrush), [RevealBrushHelper class](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.revealbrushhelper), [VisualState class](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.VisualState)</span></span>

<span data-ttu-id="8e9f3-107">Das Verhalten von Einblendungen zeigt den klickbaren Inhalt des Containers an, wenn der Mauszeiger in der Nähe ist.</span><span class="sxs-lookup"><span data-stu-id="8e9f3-107">The Reveal behavior does this by revealing the clickable content’s container when the pointer is nearby.</span></span>

![Reveal Visual](images/Nav_Reveal_Animation.gif)

<span data-ttu-id="8e9f3-109">Da durch Einblendungen die ausgeblendeten Rahmen um Objekte herum angezeigt werden, entwickeln Benutzer ein besseres Verständnis von dem Raum, mit dem diese Objekte interagieren. Darüber hinaus erfahren sie dadurch, welche Aktionen verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="8e9f3-109">By exposing the hidden borders around objects, Reveal gives users a better understanding of the space that they are interacting with, and helps them understand the actions available.</span></span> <span data-ttu-id="8e9f3-110">Dies ist besonders bei Listensteuerelementen und Gruppen von Schaltflächen wichtig.</span><span class="sxs-lookup"><span data-stu-id="8e9f3-110">This is especially important in list controls and groupings of buttons.</span></span>

## <a name="examples"></a><span data-ttu-id="8e9f3-111">Beispiele</span><span class="sxs-lookup"><span data-stu-id="8e9f3-111">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="8e9f3-112">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="8e9f3-112">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="8e9f3-113">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/Reveal">die App zu öffnen und Einblendungen in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="8e9f3-113">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/Reveal">open the app and see Reveal in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="8e9f3-114">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="8e9f3-114">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="8e9f3-115">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="8e9f3-115">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

## <a name="video-summary"></a><span data-ttu-id="8e9f3-116">Video-Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="8e9f3-116">Video summary</span></span>

> [!VIDEO https://channel9.msdn.com/Events/Windows/Windows-Developer-Day-Fall-Creators-Update/WinDev013/player]

## <a name="reveal-and-the-fluent-design-system"></a><span data-ttu-id="8e9f3-117">Einblendungen und das Fluent Design-System</span><span class="sxs-lookup"><span data-stu-id="8e9f3-117">Reveal and the Fluent Design System</span></span>

 <span data-ttu-id="8e9f3-118">Mit dem Fluent Design-System erstellen Sie moderne Oberflächen, die Licht, Tiefe, Bewegung, Material und Skalierungsmöglichkeiten beinhalten.</span><span class="sxs-lookup"><span data-stu-id="8e9f3-118">The Fluent Design System helps you create modern, bold UI that incorporates light, depth, motion, material, and scale.</span></span> <span data-ttu-id="8e9f3-119">„Einblendungen” ist eine Komponente des Fluent Design-Systems, die Lichteffekte in Ihrer App ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="8e9f3-119">Reveal is a Fluent Design System component that adds light to your app.</span></span> <span data-ttu-id="8e9f3-120">Weitere Informationen finden Sie in der [Fluent Design für UWP-Übersicht](../fluent-design-system/index.md).</span><span class="sxs-lookup"><span data-stu-id="8e9f3-120">To learn more, see the [Fluent Design for UWP overview](../fluent-design-system/index.md).</span></span>

## <a name="how-to-use-it"></a><span data-ttu-id="8e9f3-121">Verwendung</span><span class="sxs-lookup"><span data-stu-id="8e9f3-121">How to use it</span></span>

<span data-ttu-id="8e9f3-122">Einblendungen funktionieren automatisch bei einigen Steuerelementen.</span><span class="sxs-lookup"><span data-stu-id="8e9f3-122">Reveal automatically works for some controls.</span></span> <span data-ttu-id="8e9f3-123">Für andere Steuerelemente können Sie Einblendungen aktivieren, indem Sie dem Steuerelement einen speziellen Stil zuweisen.</span><span class="sxs-lookup"><span data-stu-id="8e9f3-123">For other controls, you can enable reveal by assigning a special style to the control.</span></span>

## <a name="controls-that-automatically-use-reveal"></a><span data-ttu-id="8e9f3-124">Steuerelemente, die Einblendungen automatisch verwenden</span><span class="sxs-lookup"><span data-stu-id="8e9f3-124">Controls that automatically use Reveal</span></span>

- [**<span data-ttu-id="8e9f3-125">ListView</span><span class="sxs-lookup"><span data-stu-id="8e9f3-125">ListView</span></span>**](../controls-and-patterns/lists.md)
- [**<span data-ttu-id="8e9f3-126">GridView</span><span class="sxs-lookup"><span data-stu-id="8e9f3-126">GridView</span></span>**](../controls-and-patterns/lists.md)
- [**<span data-ttu-id="8e9f3-127">TreeView</span><span class="sxs-lookup"><span data-stu-id="8e9f3-127">TreeView</span></span>**](../controls-and-patterns/tree-view.md)
- [**<span data-ttu-id="8e9f3-128">NavigationView</span><span class="sxs-lookup"><span data-stu-id="8e9f3-128">NavigationView</span></span>**](../controls-and-patterns/navigationview.md)
- [**<span data-ttu-id="8e9f3-129">AutosuggestBox</span><span class="sxs-lookup"><span data-stu-id="8e9f3-129">AutosuggestBox</span></span>**](../controls-and-patterns/auto-suggest-box.md)
- [**<span data-ttu-id="8e9f3-130">MediaTransportControl</span><span class="sxs-lookup"><span data-stu-id="8e9f3-130">MediaTransportControl</span></span>**](../controls-and-patterns/media-playback.md)
- [**<span data-ttu-id="8e9f3-131">CommandBar</span><span class="sxs-lookup"><span data-stu-id="8e9f3-131">CommandBar</span></span>**](../controls-and-patterns/app-bars.md)
- [**<span data-ttu-id="8e9f3-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="8e9f3-132">ComboBox</span></span>**](../controls-and-patterns/lists.md)

<span data-ttu-id="8e9f3-133">Die folgenden Abbildungen zeigen die Auswirkungen von Einblendungen auf verschiedene Steuerelemente:</span><span class="sxs-lookup"><span data-stu-id="8e9f3-133">These illustrations show the reveal effect on several different controls:</span></span>

![Beispiele für Einblendungen](images/RevealExamples_Collage.png)

## <a name="enabling-reveal-on-other-common-controls"></a><span data-ttu-id="8e9f3-135">Aktivieren von Einblendungen für andere allgemeine Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="8e9f3-135">Enabling Reveal on other common controls</span></span>

<span data-ttu-id="8e9f3-136">Für Szenarien, in denen Einblendungen angewendet werden sollten (diese Steuerelemente sind Hauptinhalt und/oder werden in einer Liste oder Auflistungsausrichtung verwendet), haben wir optionale Ressourcenformate bereitgestellt, mithilfe derer Sie Einblendungen für solche Situationen aktivieren können.</span><span class="sxs-lookup"><span data-stu-id="8e9f3-136">If you have a scenario where Reveal should be applied (these controls are main content and/or are used in a list or collection orientation), we've provided opt-in resource styles that allow you to enable Reveal for those types of situations.</span></span>

<span data-ttu-id="8e9f3-137">Diese Steuerelemente verfügen nicht standardmäßig über Einblendungen, da sie kleinere Steuerelemente sind, die in der Regel als Hilfssteuerelemente für die zentralen Punkte Ihrer Anwendung dienen. Alle Apps sind jedoch verschieden, und wenn diese Steuerelemente in Ihrer App am meisten verwendet werden, stehen Ihnen einige Formate als Hilfe zur Verfügung:</span><span class="sxs-lookup"><span data-stu-id="8e9f3-137">These controls do not have Reveal by default as they are smaller controls that are usually helper controls to the main focal points of your application; but every app is different, and if these controls are used the most in your app, we've provided some styles to aid with that:</span></span>

| <span data-ttu-id="8e9f3-138">Name des Steuerelements</span><span class="sxs-lookup"><span data-stu-id="8e9f3-138">Control Name</span></span>   | <span data-ttu-id="8e9f3-139">Ressourcenname</span><span class="sxs-lookup"><span data-stu-id="8e9f3-139">Resource Name</span></span> |
|----------|:-------------:|
| <span data-ttu-id="8e9f3-140">Button</span><span class="sxs-lookup"><span data-stu-id="8e9f3-140">Button</span></span> |  <span data-ttu-id="8e9f3-141">ButtonRevealStyle</span><span class="sxs-lookup"><span data-stu-id="8e9f3-141">ButtonRevealStyle</span></span> |
| <span data-ttu-id="8e9f3-142">ToggleButton</span><span class="sxs-lookup"><span data-stu-id="8e9f3-142">ToggleButton</span></span> | <span data-ttu-id="8e9f3-143">ToggleButtonRevealStyle</span><span class="sxs-lookup"><span data-stu-id="8e9f3-143">ToggleButtonRevealStyle</span></span> |
| <span data-ttu-id="8e9f3-144">RepeatButton</span><span class="sxs-lookup"><span data-stu-id="8e9f3-144">RepeatButton</span></span> | <span data-ttu-id="8e9f3-145">RepeatButtonRevealStyle</span><span class="sxs-lookup"><span data-stu-id="8e9f3-145">RepeatButtonRevealStyle</span></span> |
| <span data-ttu-id="8e9f3-146">AppBarButton</span><span class="sxs-lookup"><span data-stu-id="8e9f3-146">AppBarButton</span></span> | <span data-ttu-id="8e9f3-147">AppBarButtonRevealStyle</span><span class="sxs-lookup"><span data-stu-id="8e9f3-147">AppBarButtonRevealStyle</span></span> |
| <span data-ttu-id="8e9f3-148">SemanticZoom</span><span class="sxs-lookup"><span data-stu-id="8e9f3-148">SemanticZoom</span></span> | <span data-ttu-id="8e9f3-149">SemanticZoomRevealStyle</span><span class="sxs-lookup"><span data-stu-id="8e9f3-149">SemanticZoomRevealStyle</span></span> |

<span data-ttu-id="8e9f3-150">Um diese Formate anzuwenden, aktualisieren Sie einfach folgendermaßen die Eigenschaft „Style”:</span><span class="sxs-lookup"><span data-stu-id="8e9f3-150">To apply these styles, simply update the Style property like so:</span></span>

```XAML
<Button Content="Button Content" Style="{StaticResource ButtonRevealStyle}"/>
```

## <a name="enabling-reveal-on-custom-controls"></a><span data-ttu-id="8e9f3-151">Aktivieren von Einblendungen für benutzerdefinierte Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="8e9f3-151">Enabling Reveal on custom controls</span></span>

<span data-ttu-id="8e9f3-152">Berücksichtigen Sie bei der Entscheidung, ob das benutzerdefinierte Steuerelement Einblendungen erhalten soll oder nicht, ob Sie eine Gruppierung von interaktiven Elementen benötigen, die sich alle auf eine übergeordnete Feature oder Aktion beziehen, die Sie in Ihrer App ausführen möchten.</span><span class="sxs-lookup"><span data-stu-id="8e9f3-152">The general rule to think about when deciding whether or not your custom control should get Reveal, is you must have a grouping of interactive elements that all relate to an overarching feature or action you wish to perform in your app.</span></span>

<span data-ttu-id="8e9f3-153">Beispielsweise sind NavigationView-Elemente mit der Seitennavigation verknüpft.</span><span class="sxs-lookup"><span data-stu-id="8e9f3-153">For example, NavigationView's items are related to page navigation.</span></span> <span data-ttu-id="8e9f3-154">CommandBar-Schaltflächen beziehen sich auf Menüaktionen oder Feature-Aktionen.</span><span class="sxs-lookup"><span data-stu-id="8e9f3-154">CommandBar's buttons relate to menu actions or page feature actions.</span></span> <span data-ttu-id="8e9f3-155">Die MediaTransportControl-Schaltflächen unterhalb beziehen sich auf das Medium, das wiedergegeben wird.</span><span class="sxs-lookup"><span data-stu-id="8e9f3-155">MediaTransportControl's buttons beneath all relate to the media being played.</span></span>

<span data-ttu-id="8e9f3-156">Die Steuerelemente, die die Einblendung erhalten, müssen nicht miteinander verknüpft werden, sondern nur in einem HD-Bereich sein und einen größeren Zweck dienen.</span><span class="sxs-lookup"><span data-stu-id="8e9f3-156">The controls that get Reveal do not have to be related to each other, they just have to be in a high-density area, and serve a greater purpose.</span></span>

<span data-ttu-id="8e9f3-157">Rufen Sie zum Aktivieren von Einblendungen für benutzerdefinierte Steuerelemente oder Steuerelemente mit neuen Vorlagen das Format für dieses Steuerelement in den visuellen Zuständen der Vorlage für dieses Steuerelement auf, und legen Sie Einblendungen im Stammraster fest:</span><span class="sxs-lookup"><span data-stu-id="8e9f3-157">To enable Reveal on custom controls or re-templated controls, you can go into the style for that control in the Visual States of that control's template and specify Reveal on the root grid:</span></span>

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

<span data-ttu-id="8e9f3-158">Es ist wichtig zu beachten, dass zur Einblendung sowohl ein Pinsel als auch Setter in Visual State benötigt werden, um einwandfrei zu arbeiten.</span><span class="sxs-lookup"><span data-stu-id="8e9f3-158">It's important to note that Reveal needs both the brush and the setters in it's Visual State in order to work fully.</span></span> <span data-ttu-id="8e9f3-159">Das einfache Festlegen eines Steuerelements für Reveal-Pinselressourcen alleine aktivieren das Steuerelement nicht.</span><span class="sxs-lookup"><span data-stu-id="8e9f3-159">Simply setting a control's brush to one of our Reveal brush resources alone won't enable Reveal for that control.</span></span> <span data-ttu-id="8e9f3-160">Ziele oder Einstellungen zu verwenden ohne die Werte als Reveal-Pinsel festgelegt zu haben, aktiviert die Einblendung auch nicht.</span><span class="sxs-lookup"><span data-stu-id="8e9f3-160">Conversely, having only the targets or settings without the values being Reveal brushes will also not enable Reveal.</span></span>

<span data-ttu-id="8e9f3-161">Wir haben eine Reihe von System-Reveal-Pinsels erstellt, mit denen Sie die Benutzeroberfläche anpassen können.</span><span class="sxs-lookup"><span data-stu-id="8e9f3-161">We've created a set of system Reveal brushes you can use to customize your UI.</span></span> <span data-ttu-id="8e9f3-162">Sie können z.B. den Pinsel **ButtonRevealBackground** zum Erstellen eines Hintergrunds für eine benutzerdefinierte Schaltfläche oder den Pinsel **ListViewItemRevealBackground** für benutzerdefinierte Listen und so weiter verwenden.</span><span class="sxs-lookup"><span data-stu-id="8e9f3-162">For example, you can use the **ButtonRevealBackground** brush to create a custom button background, or the **ListViewItemRevealBackground** brush for custom lists, and so on.</span></span>

<span data-ttu-id="8e9f3-163">(Informationen zur Funktionsweise von Ressourcen in XAMl finden Sie im Artikel [Xaml-Ressourcenverzeichnis](../controls-and-patterns/resourcedictionary-and-xaml-resource-references.md).)</span><span class="sxs-lookup"><span data-stu-id="8e9f3-163">(To learn about how resources work in XAMl, check out the [Xaml Resource Dictionary](../controls-and-patterns/resourcedictionary-and-xaml-resource-references.md) article.)</span></span>

### <a name="reveal-on-listview-controls-with-nested-buttons"></a><span data-ttu-id="8e9f3-164">Einblendung auf ListView-Steuerelementen mit geschachtelten Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="8e9f3-164">Reveal on ListView controls with nested buttons</span></span>

<span data-ttu-id="8e9f3-165">Besitzen Sie ein [ListView](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ListView) und Schaltflächen oder aufgerufene Inhalte, die innerhalb eines [ListViewItem](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.listviewitem)-Elements geschachtelt sind, sollten Sie die Einblendung für die geschachtelten Elemente aktivieren.</span><span class="sxs-lookup"><span data-stu-id="8e9f3-165">If you have a [ListView](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ListView) and also have buttons or invokable content nested inside its [ListViewItem](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.listviewitem) elements, you should enable Reveal for the nested items.</span></span>

<span data-ttu-id="8e9f3-166">Falls Sie Schaltflächen oder Schaltflächen ähnliche Steuerelemente in einem ListViewItem haben, legen Sie einfach die [Stil](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement#Windows_UI_Xaml_FrameworkElement_Style)-Eigenschaft des Steuerelements auf die statische Ressource **ButtonRevealStyle** fest.</span><span class="sxs-lookup"><span data-stu-id="8e9f3-166">In the case of Buttons, or button-like controls in a ListViewItem, simply set the control's  [Style](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement#Windows_UI_Xaml_FrameworkElement_Style) property to the **ButtonRevealStyle** static resource.</span></span> 

![Geschachtelte Einblendungen](images/NestedListContent.png)

<span data-ttu-id="8e9f3-168">Dieses Beispiel ermöglicht Einblendungen auf mehrere Schaltflächen in einem ListViewItem.</span><span class="sxs-lookup"><span data-stu-id="8e9f3-168">This example enables Reveal on several buttons inside a ListViewItem.</span></span> 

```XAML
<ListViewItem>
    <StackPanel Orientation="Horizontal">
        <TextBlock Margin="5">Test Text: lorem ipsum.</TextBlock>
        <StackPanel Orientation="Horizontal">
            <Button Content="&#xE71B;" FontFamily="Segoe MDL2 Assets" Width="45" Height="45" Margin="5" Style="{StaticResource ButtonRevealStyle}"/>
            <Button Content="&#xE728;" FontFamily="Segoe MDL2 Assets" Width="45" Height="45" Margin="5" Style="{StaticResource ButtonRevealStyle}"/>
            <Button Content="&#xE74D;" FontFamily="Segoe MDL2 Assets" Width="45" Height="45" Margin="5" Style="{StaticResource ButtonRevealStyle}"/>
         </StackPanel>
    </StackPanel>
</ListViewItem>
```

### <a name="listviewitempresenter-with-reveal"></a><span data-ttu-id="8e9f3-169">ListViewItemPresenter mit Einblendungen</span><span class="sxs-lookup"><span data-stu-id="8e9f3-169">ListViewItemPresenter with Reveal</span></span>

<span data-ttu-id="8e9f3-170">Listen werden in XAML besonders behandelt, und bei Einblendungen müssen wir Visual State-Manager für Einblendungen nur innerhalb des ListViewItemPresenters definieren:</span><span class="sxs-lookup"><span data-stu-id="8e9f3-170">Lists are a bit special in XAML, and for Reveal's case we'll have to define the Visual State Manager for Reveal only inside the ListViewItemPresenter:</span></span>

```XAML
<ListViewItemPresenter>
<!-- ContentTransitions, SelectedForeground, etc. properties -->
RevealBackground="{ThemeResource ListViewItemRevealBackground}"
RevealBorderThickness="{ThemeResource ListViewItemRevealBorderThemeThickness}"
RevealBorderBrush="{ThemeResource ListViewItemRevealBorderBrush}">
    <VisualStateManager.VisualStateGroups>
        <VisualStateGroup x:Name="CommonStates">
        <VisualState x:Name="Normal" />
        <VisualState x:Name="Selected" />
        <VisualState x:Name="PointerOver">
            <VisualState.Setters>
                <Setter Target="Root.(RevealBrush.State)" Value="PointerOver" />
            </VisualState.Setters>
            </VisualState>
            <VisualState x:Name="PointerOverSelected">
                <VisualState.Setters>
                    <Setter Target="Root.(RevealBrush.State)" Value="PointerOver" />
                </VisualState.Setters>
            </VisualState>
            <VisualState x:Name="PointerOverPressed">
                <VisualState.Setters>
                    <Setter Target="Root.(RevealBrush.State)" Value="Pressed" />
                </VisualState.Setters>
            </VisualState>
            <VisualState x:Name="Pressed">
                <VisualState.Setters>
                    <Setter Target="Root.(RevealBrush.State)" Value="Pressed" />
                </VisualState.Setters>
            </VisualState>
            <VisualState x:Name="PressedSelected">
                <VisualState.Setters>
                    <Setter Target="Root.(RevealBrush.State)" Value="Pressed" />
                </VisualState.Setters>
            </VisualState>
            </VisualStateGroup>
                <VisualStateGroup x:Name="EnabledGroup">
                    <VisualState x:Name="Enabled" />
                    <VisualState x:Name="Disabled">
                        <VisualState.Setters>
                             <Setter Target="Root.RevealBorderThickness" Value="0"/>
                        </VisualState.Setters>
                    </VisualState>
                </VisualStateGroup>
    </VisualStateManager.VisualStateGroups>
</ListViewItemPresenter>
```

<span data-ttu-id="8e9f3-171">Dies bedeutet ein Anfügen an das Ende der Eigenschaftssammlung innerhalb von ListViewItemPresenter mit den bestimmten Setter des Visual States für eine Einblendung.</span><span class="sxs-lookup"><span data-stu-id="8e9f3-171">This means appending to the end of the property collection within the ListViewItemPresenter with the Reveal specific Visual State setters.</span></span>

### <a name="full-template-example"></a><span data-ttu-id="8e9f3-172">Vollständiges Vorlagenbeispiel</span><span class="sxs-lookup"><span data-stu-id="8e9f3-172">Full Template Example</span></span>

<span data-ttu-id="8e9f3-173">Hier sehen Sie eine gesamte Vorlage und wie eine Schaltfläche zum Einblenden aussehen würde:</span><span class="sxs-lookup"><span data-stu-id="8e9f3-173">Here's an entire template for what a Reveal Button would look like:</span></span>

```XAML
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

## <a name="dos-and-donts"></a><span data-ttu-id="8e9f3-174">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="8e9f3-174">Do's and don'ts</span></span>
- <span data-ttu-id="8e9f3-175">Verwenden Sie die Einblendung für Elemente, in denen der Benutzer Aktionen (Schaltflächen, Auswahl) ausführt</span><span class="sxs-lookup"><span data-stu-id="8e9f3-175">Do use Reveal on elements where the user can take action (buttons, selections)</span></span>
- <span data-ttu-id="8e9f3-176">Verwenden Sie Einblendungen bei der Gruppierung von interaktiven Elementen, die nicht standardmäßig visuelle Trennzeichen haben (Listen, Befehlsleisten)</span><span class="sxs-lookup"><span data-stu-id="8e9f3-176">Do use Reveal in groupings of interactive elements that do not have visual separators by default (lists, command bars)</span></span>
- <span data-ttu-id="8e9f3-177">Verwenden Sie Einblendungen in Bereichen mit vielen interaktiven Elementen</span><span class="sxs-lookup"><span data-stu-id="8e9f3-177">Do use Reveal in areas with a high density of interactive elements</span></span>
- <span data-ttu-id="8e9f3-178">Verwenden Sie Einblendungen nicht auf statischen Inhalten (Hintergrund, Text)</span><span class="sxs-lookup"><span data-stu-id="8e9f3-178">Don’t use Reveal on static content (backgrounds, text)</span></span>
- <span data-ttu-id="8e9f3-179">Verwenden Sie Einblendungen nicht in einzelnen, isolierten Situationen</span><span class="sxs-lookup"><span data-stu-id="8e9f3-179">Don’t use Reveal in one-off, isolated situations</span></span>
- <span data-ttu-id="8e9f3-180">Verwenden Sie Einblendungen nicht auf sehr großen Elementen (größer als 500epx)</span><span class="sxs-lookup"><span data-stu-id="8e9f3-180">Don’t use Reveal on very large items (greater than 500epx)</span></span>
- <span data-ttu-id="8e9f3-181">Verwenden Sie Einblendungen nicht bei sicherheitsbezogenen Entscheidungen, da es die Aufmerksamkeit von der Nachricht, die Sie an die Benutzer übermitteln möchten, weglenken kann.</span><span class="sxs-lookup"><span data-stu-id="8e9f3-181">Don’t use Reveal in security decisions, as it may draw attention away from the message you need to deliver to your user</span></span>

## <a name="how-we-designed-reveal"></a><span data-ttu-id="8e9f3-182">Unser Einblendungs-Entwurfsansatz</span><span class="sxs-lookup"><span data-stu-id="8e9f3-182">How we designed Reveal</span></span>

<span data-ttu-id="8e9f3-183">Es gibt zwei visuelle Hauptkomponenten für Einblendungen: das Verhalten **Einblenden durch Daraufzeigen** und das Verhalten **Rahmen einblenden**.</span><span class="sxs-lookup"><span data-stu-id="8e9f3-183">There are two main visual components to Reveal: the **Hover Reveal** behavior, and the **Border Reveal** behavior.</span></span>

![Ebenen einblenden](images/RevealLayers.png)

<span data-ttu-id="8e9f3-185">Das Verhalten „Einblenden durch Daraufzeigen” ist direkt mit dem Inhalt verbunden, auf den gezeigt wird (mit Zeiger- oder Fokuseingaben). Dabei wird ein leichter Lichthof um das Element herum eingeblendet, auf das gezeigt oder das fokussiert wird, sodass Sie wissen, dass Sie damit interagieren können.</span><span class="sxs-lookup"><span data-stu-id="8e9f3-185">The Hover Reveal is tied directly to the content being hovered over (via pointer or focus input), and applies a gentle halo shape around the hovered or focused item, letting you know you can interact with it.</span></span>

<span data-ttu-id="8e9f3-186">Das Verhalten „Rahmen einblenden” wird auf das fokussierte Element und andere Elemente in dessen Nähe angewendet.</span><span class="sxs-lookup"><span data-stu-id="8e9f3-186">The Border Reveal is applied to the focused item and items nearby.</span></span> <span data-ttu-id="8e9f3-187">Dadurch erfahren Sie, dass diese Objekte in der Nähe ähnliche Aktionen wie das aktuell fokussierte Objekt durchführen können.</span><span class="sxs-lookup"><span data-stu-id="8e9f3-187">This shows you that those nearby objects can take actions similar to the one currently focused.</span></span>

<span data-ttu-id="8e9f3-188">Die Aufschlüsselung der Anleitung für Einblendungen sieht folgendermaßen aus:</span><span class="sxs-lookup"><span data-stu-id="8e9f3-188">The Reveal recipe breakdown is:</span></span>

- <span data-ttu-id="8e9f3-189">Das Verhalten „Rahmen einblenden” befindet sich über dem gesamten Inhalt, jedoch an den angegebenen Rändern.</span><span class="sxs-lookup"><span data-stu-id="8e9f3-189">Border Reveal will be on top of all content but on the designated edges</span></span>
- <span data-ttu-id="8e9f3-190">Text und Inhalt werden direkt unter dem Verhalten „Rahmen einblenden” angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8e9f3-190">Text and content will be displayed directly under Border Reveal</span></span>
- <span data-ttu-id="8e9f3-191">Das Verhalten „Einblenden durch Daraufzeigen” befindet sich unterhalb von Inhalt und Text.</span><span class="sxs-lookup"><span data-stu-id="8e9f3-191">Hover Reveal will be beneath content and text</span></span>
- <span data-ttu-id="8e9f3-192">Die Backplate (die das Verhalten „Rahmen einblenden” aktiviert)</span><span class="sxs-lookup"><span data-stu-id="8e9f3-192">The backplate (that turns on and enables Hover Reveal)</span></span>
- <span data-ttu-id="8e9f3-193">Der Hintergrund (Hintergrund des Steuerelements)</span><span class="sxs-lookup"><span data-stu-id="8e9f3-193">The background (background of control)</span></span>

<!--
<div class=”microsoft-internal-note”>
To create your own Reveal lighting effect for static comps or prototype purposes, see the full [uni design guidance](http://uni/DesignDepot.FrontEnd/#/ProductNav/3020/1/dv/?t=Resources%7CToolkit%7CReveal&f=Neon) for this effect in illustrator.
</div>
-->  

## <a name="get-the-sample-code"></a><span data-ttu-id="8e9f3-194">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="8e9f3-194">Get the sample code</span></span>

- <span data-ttu-id="8e9f3-195">[Beispiel eines XAML-Steuerelementkatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="8e9f3-195">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>

## <a name="related-articles"></a><span data-ttu-id="8e9f3-196">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="8e9f3-196">Related articles</span></span>

- [<span data-ttu-id="8e9f3-197">RevealBrush-Klasse</span><span class="sxs-lookup"><span data-stu-id="8e9f3-197">RevealBrush class</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.revealbrush)
- [<span data-ttu-id="8e9f3-198">Acryl</span><span class="sxs-lookup"><span data-stu-id="8e9f3-198">Acrylic</span></span>](acrylic.md)
- [<span data-ttu-id="8e9f3-199">Kompositionseffekte</span><span class="sxs-lookup"><span data-stu-id="8e9f3-199">Composition Effects</span></span>](https://msdn.microsoft.com/windows/uwp/graphics/composition-effects)
- [<span data-ttu-id="8e9f3-200">Fluent Design für UWP</span><span class="sxs-lookup"><span data-stu-id="8e9f3-200">Fluent Design for UWP</span></span>](../fluent-design-system/index.md)
- [<span data-ttu-id="8e9f3-201">Wissenschaft im System: Fluent Design und Tiefe</span><span class="sxs-lookup"><span data-stu-id="8e9f3-201">Science in the System: Fluent Design and Depth</span></span>](https://medium.com/microsoft-design/science-in-the-system-fluent-design-and-depth-fb6d0f23a53f)
- [<span data-ttu-id="8e9f3-202">Wissenschaft im System: Fluent Design und Licht</span><span class="sxs-lookup"><span data-stu-id="8e9f3-202">Science in the System: Fluent Design and Light</span></span>](https://medium.com/microsoft-design/the-science-in-the-system-fluent-design-and-light-94a17e0b3a4f)
