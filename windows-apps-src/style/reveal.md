---
author: mijacobs
description: "„Einblendungen” ist ein neues Interaktionsmodell, mit dem sich ein stärkerer Fokus und mehr Spaß in Ihre Anwendung bringen lassen."
title: Einblendungen
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
ms.openlocfilehash: d50e3f47faad5fff0ef461a4b5312127a0b9ec9c
ms.sourcegitcommit: 0d5b3daddb3ae74f91178c58e35cbab33854cb7f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2017
---
# <a name="reveal"></a><span data-ttu-id="813c1-104">Einblendungen</span><span class="sxs-lookup"><span data-stu-id="813c1-104">Reveal</span></span>

> [!IMPORTANT]
> <span data-ttu-id="813c1-105">In diesem Artikel werden Funktionen beschrieben, die noch nicht veröffentlicht wurden und vor der kommerziellen Freigabe evtl. grundlegend geändert werden.</span><span class="sxs-lookup"><span data-stu-id="813c1-105">This article describes functionality that hasn’t been released yet and may be substantially modified before it's commercially released.</span></span> <span data-ttu-id="813c1-106">Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.</span><span class="sxs-lookup"><span data-stu-id="813c1-106">Microsoft makes no warranties, express or implied, with respect to the information provided here.</span></span>

<span data-ttu-id="813c1-107">Einblendungen sind neue Lichteffekte, welche die interaktiven Elemente in Ihrer App mit Tiefe und Fokus versehen kann.</span><span class="sxs-lookup"><span data-stu-id="813c1-107">Reveal is a lighting effect that helps bring depth and focus to your app's interactive elements.</span></span>

> <span data-ttu-id="813c1-108">**Wichtige APIs**: [RevealBrush-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.revealbrush), [RevealBackgroundBrush-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.revealbackgroundbrush), [RevealBorderBrush-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.revealborderbrush), [RevealBrushHelper-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.revealbrushhelper), [VisualState-Klasse](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.VisualState)</span><span class="sxs-lookup"><span data-stu-id="813c1-108">**Important APIs**: [RevealBrush class](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.revealbrush), [RevealBackgroundBrush class](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.revealbackgroundbrush), [RevealBorderBrush class](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.revealborderbrush), [RevealBrushHelper class](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.revealbrushhelper), [VisualState class](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.VisualState)</span></span>

<span data-ttu-id="813c1-109">Zu diesem Zweck werden mithilfe des Einblendeverhaltens Teile von Elementen um Favoriteninhalt (oder zentralen Inhalt) herum eingeblendet, wenn die Maus oder das Fokusrechteck über die gewünschten Bereiche bewegt wird.</span><span class="sxs-lookup"><span data-stu-id="813c1-109">The Reveal behavior does this by revealing pieces of elements around hero (or focal) content when the mouse or focus rectangle is over the desired areas.</span></span>

![Einblendeanzeige](images/Nav_Reveal_Animation.gif)

<span data-ttu-id="813c1-111">Da durch Einblendungen die ausgeblendeten Rahmen um Objekte herum angezeigt werden, entwickeln Benutzer ein besseres Verständnis von dem Raum, mit dem diese Objekte interagieren. Darüber hinaus erfahren sie dadurch, welche Aktionen verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="813c1-111">Through exposing the hidden borders around objects, Reveal gives users a better understanding of the space that they are interacting with, and helps them understand the actions available.</span></span> <span data-ttu-id="813c1-112">Dies ist besonders wichtig in Listensteuerelementen und Steuerelementen mit Backplates.</span><span class="sxs-lookup"><span data-stu-id="813c1-112">This is especially important in list controls and controls with backplates.</span></span>

## <a name="reveal-and-the-fluent-design-system"></a><span data-ttu-id="813c1-113">Einblendungen und das Fluent Design-System</span><span class="sxs-lookup"><span data-stu-id="813c1-113">Reveal and the Fluent Design System</span></span>

 <span data-ttu-id="813c1-114">Mit dem Fluent Design-System erstellen Sie moderne Oberflächen, die Licht, Tiefe, Bewegung, Material und Skalierungsmöglichkeiten beinhalten.</span><span class="sxs-lookup"><span data-stu-id="813c1-114">The Fluent Design System helps you create modern, bold UI that incorporates light, depth, motion, material, and scale.</span></span> <span data-ttu-id="813c1-115">„Einblendungen” ist eine Komponente des Fluent Design-Systems, die Lichteffekte in Ihrer App ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="813c1-115">Reveal is a Fluent Design System component that adds light to your app.</span></span> 

## <a name="what-is-reveal"></a><span data-ttu-id="813c1-116">Was sind Einblendungen?</span><span class="sxs-lookup"><span data-stu-id="813c1-116">What is reveal?</span></span>

<span data-ttu-id="813c1-117">Es gibt zwei visuelle Hauptkomponenten für Einblendungen: das Verhalten **Einblenden durch Daraufzeigen** und das Verhalten **Rahmen einblenden**.</span><span class="sxs-lookup"><span data-stu-id="813c1-117">There are two main visual components to Reveal: the **Hover Reveal** behavior, and the **Border Reveal** behavior.</span></span>

![Ebenen einblenden](images/RevealLayers.png)

<span data-ttu-id="813c1-119">Das Verhalten „Einblenden durch Daraufzeigen” ist direkt mit dem Inhalt verbunden, auf den gezeigt wird (mit Zeiger- oder Fokuseingaben). Dabei wird ein leichter Lichthof um das Element herum eingeblendet, auf das gezeigt oder das fokussiert wird, sodass Sie wissen, dass Sie damit interagieren können.</span><span class="sxs-lookup"><span data-stu-id="813c1-119">The Hover Reveal is tied directly to the content being hovered over (via pointer or focus input), and applies a gentle halo shape around the hovered or focused item, letting you know you can interact with it.</span></span>

<span data-ttu-id="813c1-120">Das Verhalten „Rahmen einblenden” wird auf das fokussierte Element und andere Elemente in dessen Nähe angewendet.</span><span class="sxs-lookup"><span data-stu-id="813c1-120">The Border Reveal is applied to the focused item and items nearby.</span></span> <span data-ttu-id="813c1-121">Dadurch erfahren Sie, dass diese Objekte in der Nähe ähnliche Aktionen wie das aktuell fokussierte Objekt durchführen können.</span><span class="sxs-lookup"><span data-stu-id="813c1-121">This shows you that those nearby objects can take actions similar to the one currently focused.</span></span>

<span data-ttu-id="813c1-122">Die Aufschlüsselung der Anleitung für Einblendungen sieht folgendermaßen aus:</span><span class="sxs-lookup"><span data-stu-id="813c1-122">The Reveal recipe breakdown is:</span></span>

- <span data-ttu-id="813c1-123">Das Verhalten „Rahmen einblenden” befindet sich über dem gesamten Inhalt, jedoch an den angegebenen Rändern.</span><span class="sxs-lookup"><span data-stu-id="813c1-123">Border Reveal will be on top of all content but on the designated edges</span></span>
- <span data-ttu-id="813c1-124">Text und Inhalt werden direkt unter dem Verhalten „Rahmen einblenden” angezeigt.</span><span class="sxs-lookup"><span data-stu-id="813c1-124">Text and content will be displayed directly under Border Reveal</span></span>
- <span data-ttu-id="813c1-125">Das Verhalten „Einblenden durch Daraufzeigen” befindet sich unterhalb von Inhalt und Text.</span><span class="sxs-lookup"><span data-stu-id="813c1-125">Hover Reveal will be beneath content and text</span></span>
- <span data-ttu-id="813c1-126">Die Backplate (die das Verhalten „Rahmen einblenden” aktiviert)</span><span class="sxs-lookup"><span data-stu-id="813c1-126">The backplate (that turns on and enables Hover Reveal)</span></span>
- <span data-ttu-id="813c1-127">Der Hintergrund (Hintergrund des Steuerelements)</span><span class="sxs-lookup"><span data-stu-id="813c1-127">The background (background of control)</span></span>

<!--
<div class=”microsoft-internal-note”>
To create your own Reveal lighting effect for static comps or prototype purposes, see the full [uni design guidance](http://uni/DesignDepot.FrontEnd/#/ProductNav/3020/1/dv/?t=Resources%7CToolkit%7CReveal&f=Neon) for this effect in illustrator.
</div>
-->

## <a name="how-to-use-it"></a><span data-ttu-id="813c1-128">Verwendung</span><span class="sxs-lookup"><span data-stu-id="813c1-128">How to use it</span></span>

<span data-ttu-id="813c1-129">Durch Einblendungen wird Geometrie um den Cursor herum angezeigt, wenn diese benötigt wird, und sie wird nahtlos ausgeblendet, wenn der Cursor weiterbewegt wird.</span><span class="sxs-lookup"><span data-stu-id="813c1-129">Reveal exposes geometry around your cursor when you need it, and seamlessly fades it out once you’ve moved on.</span></span>

<span data-ttu-id="813c1-130">Einblendungen lassen sich am besten verwenden, wenn sie für den Hauptinhalt Ihrer App (Favoriteninhalt) aktiviert sind, der Grenzen und Backplates aufweist.</span><span class="sxs-lookup"><span data-stu-id="813c1-130">Reveal is best used when enabled on the main content of your app (hero content) that has implied boundries and backplates to them.</span></span> <span data-ttu-id="813c1-131">Einblendungen sollten darüber hinaus für Auflistungs- oder listenähnliche Steuerelemente verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="813c1-131">Reveal should additionally be used on collection or list-like controls.</span></span>

## <a name="controls-that-automatically-use-reveal"></a><span data-ttu-id="813c1-132">Steuerelemente, die Einblendungen automatisch verwenden</span><span class="sxs-lookup"><span data-stu-id="813c1-132">Controls that automatically use Reveal</span></span>

- [**<span data-ttu-id="813c1-133">ListView</span><span class="sxs-lookup"><span data-stu-id="813c1-133">ListView</span></span>**](../controls-and-patterns/lists.md)
- [**<span data-ttu-id="813c1-134">TreeView</span><span class="sxs-lookup"><span data-stu-id="813c1-134">TreeView</span></span>**](../controls-and-patterns/tree-view.md)
- [**<span data-ttu-id="813c1-135">NavigationView</span><span class="sxs-lookup"><span data-stu-id="813c1-135">NavigationView</span></span>**](../controls-and-patterns/navigationview.md)
- [**<span data-ttu-id="813c1-136">AutosuggestBox</span><span class="sxs-lookup"><span data-stu-id="813c1-136">AutosuggestBox</span></span>**](../controls-and-patterns/auto-suggest-box.md)

## <a name="enabling-reveal-on-other-common-controls"></a><span data-ttu-id="813c1-137">Aktivieren von Einblendungen für andere allgemeine Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="813c1-137">Enabling Reveal on other common controls</span></span>

<span data-ttu-id="813c1-138">Für Szenarien, in denen Einblendungen angewendet werden sollten (diese Steuerelemente sind Hauptinhalt und/oder werden in einer Liste oder Auflistungsausrichtung verwendet), haben wir optionale Ressourcenformate bereitgestellt, mithilfe derer Sie Einblendungen für solche Situationen aktivieren können.</span><span class="sxs-lookup"><span data-stu-id="813c1-138">If you have a scenario where Reveal should be applied (these controls are main content and/or are used in a list or collection orientation), we've provided opt-in resourse styles that allow you to enable Reveal for those types of situations.</span></span>

<span data-ttu-id="813c1-139">Diese Steuerelemente verfügen nicht standardmäßig über Einblendungen, da sie kleinere Steuerelemente sind, die in der Regel als Hilfssteuerelemente für die zentralen Punkte Ihrer Anwendung dienen. Alle Apps sind jedoch verschieden, und wenn diese Steuerelemente in Ihrer App am meisten verwendet werden, stehen Ihnen einige Formate als Hilfe zur Verfügung:</span><span class="sxs-lookup"><span data-stu-id="813c1-139">These controls do not have Reveal by default as they are smaller controls that are usually helper controls to the main focal points of your application; but every app is different, and if these controls are used the most in your app, we've provided some styles to aid with that:</span></span>

| <span data-ttu-id="813c1-140">Name des Steuerelements</span><span class="sxs-lookup"><span data-stu-id="813c1-140">Control Name</span></span>   | <span data-ttu-id="813c1-141">Ressourcenname</span><span class="sxs-lookup"><span data-stu-id="813c1-141">Resource Name</span></span> |
|----------|:-------------:|
| <span data-ttu-id="813c1-142">Button</span><span class="sxs-lookup"><span data-stu-id="813c1-142">Button</span></span> |  <span data-ttu-id="813c1-143">ButtonRevealStyle</span><span class="sxs-lookup"><span data-stu-id="813c1-143">ButtonRevealStyle</span></span> |
| <span data-ttu-id="813c1-144">ToggleButton</span><span class="sxs-lookup"><span data-stu-id="813c1-144">ToggleButton</span></span> | <span data-ttu-id="813c1-145">ToggleButtonRevealStyle</span><span class="sxs-lookup"><span data-stu-id="813c1-145">ToggleButtonRevealStyle</span></span> |
| <span data-ttu-id="813c1-146">RepeatButton</span><span class="sxs-lookup"><span data-stu-id="813c1-146">RepeatButton</span></span> | <span data-ttu-id="813c1-147">RepeatButtonRevealStyle</span><span class="sxs-lookup"><span data-stu-id="813c1-147">RepeatButtonRevealStyle</span></span> |
| <span data-ttu-id="813c1-148">AppBarButton</span><span class="sxs-lookup"><span data-stu-id="813c1-148">AppBarButton</span></span> | <span data-ttu-id="813c1-149">AppBarButtonRevealStyle</span><span class="sxs-lookup"><span data-stu-id="813c1-149">AppBarButtonRevealStyle</span></span> |
| <span data-ttu-id="813c1-150">SemanticZoom</span><span class="sxs-lookup"><span data-stu-id="813c1-150">SemanticZoom</span></span> | <span data-ttu-id="813c1-151">SemanticZoomRevealStyle</span><span class="sxs-lookup"><span data-stu-id="813c1-151">SemanticZoomRevealStyle</span></span> |
| <span data-ttu-id="813c1-152">ComboBoxItem</span><span class="sxs-lookup"><span data-stu-id="813c1-152">ComboBoxItem</span></span> | <span data-ttu-id="813c1-153">ComboxBoxItemRevealStyle</span><span class="sxs-lookup"><span data-stu-id="813c1-153">ComboxBoxItemRevealStyle</span></span> |

<span data-ttu-id="813c1-154">Um diese Formate anzuwenden, aktualisieren Sie einfach folgendermaßen die Eigenschaft „Style”:</span><span class="sxs-lookup"><span data-stu-id="813c1-154">To apply these styles, simply update the Style property like so:</span></span>

```XAML
<Button Content="Button Content" Style="{StaticResource ButtonRevealStyle}"/>
```

> [!NOTE]
> <span data-ttu-id="813c1-155">In Version 16190 des SDK werden diese Formate nicht automatisch zur Verfügung gestellt.</span><span class="sxs-lookup"><span data-stu-id="813c1-155">The 16190 version of the SDK does not make these styles automatically available.</span></span> <span data-ttu-id="813c1-156">Um sie zu verwenden, müssen Sie diese Formate manuell aus generic.xaml in Ihre App kopieren.</span><span class="sxs-lookup"><span data-stu-id="813c1-156">To get them, you need to manually copy them from generic.xaml into your app.</span></span> <span data-ttu-id="813c1-157">Generic.xaml finden Sie normalerweise unter C:\Programme (x86)\Windows Kits\10\DesignTime\CommonConfiguration\Neutral\UAP\10.0.16190.0\Generic.</span><span class="sxs-lookup"><span data-stu-id="813c1-157">Generic.xaml is typically located at C:\Program Files (x86)\Windows Kits\10\DesignTime\CommonConfiguration\Neutral\UAP\10.0.16190.0\Generic.</span></span> <span data-ttu-id="813c1-158">Dieses Problem wird in einem späteren Build behoben.</span><span class="sxs-lookup"><span data-stu-id="813c1-158">This issue will be fixed in a later build.</span></span> 

## <a name="enabling-reveal-on-custom-controls"></a><span data-ttu-id="813c1-159">Aktivieren von Einblendungen für benutzerdefinierte Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="813c1-159">Enabling Reveal on custom controls</span></span>

<span data-ttu-id="813c1-160">Rufen Sie zum Aktivieren von Einblendungen für benutzerdefinierte Steuerelemente oder Steuerelemente mit neuen Vorlagen das Format für dieses Steuerelement in den visuellen Zuständen der Vorlage für dieses Steuerelement auf, und legen Sie Einblendungen im Stammraster fest:</span><span class="sxs-lookup"><span data-stu-id="813c1-160">To enable Reveal on custom controls or re-templated controls, you can go into the style for that control in the Visual States of that control's template, specify Reveal on the root grid:</span></span>

```xaml
<VisualState x:Name="PointerOver">
  <VisualState.Setters>
    <Setter Target="RootGrid.(RevealBrushHelper.State)" Value="PointerOver" />
    <Setter Target="RootGrid.Background" Value="{ThemeResource ButtonRevealBackgroundPointerOver}"/>
    <Setter Target="ContentPresenter.BorderBrush" Value="{ThemeResource ButtonRevealBorderBrushPointerOver}"/>
    <Setter Target="ContentPresenter.Foreground" Value="{ThemeResource ButtonForegroundPointerOver}"/>
  </VisualState.Setters>
</VisualState>
```

<span data-ttu-id="813c1-161">Um den Pull-Effekt bei Einblendungen zu erhalten, müssen Sie denselben RevealBrushHelper zu PressedState hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="813c1-161">To get the pull effect of Reveal you'll need to add the same RevealBrushHelper to the PressedState as well:</span></span>

```xaml
<VisualState x:Name="Pressed">
  <VisualState.Setters>
    <Setter Target="RootGrid.(RevealBrushHelper.State)" Value="Pressed" />
    <Setter Target="RootGrid.Background" Value="{ThemeResource ButtonRevealBackgroundPressed}"/>
    <Setter Target="ContentPresenter.BorderBrush" Value="{ThemeResource ButtonRevealBorderBrushPressed}"/>
    <Setter Target="ContentPresenter.Foreground" Value="{ThemeResource ButtonForegroundPressed}"/>
  </VisualState.Setters>
</VisualState>
```


<span data-ttu-id="813c1-162">Wenn Sie unsere Systemressource „Einblendungen” verwenden, kümmern wir uns für Sie um alle Designänderungen.</span><span class="sxs-lookup"><span data-stu-id="813c1-162">Using our system resource Reveal means we will handle all the theme changes for you.</span></span>

## <a name="dos-and-donts"></a><span data-ttu-id="813c1-163">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="813c1-163">Do's and don'ts</span></span>
- <span data-ttu-id="813c1-164">Verwenden Sie Einblendungen für Elemente, auf denen Benutzer Aktionen durchführen können – Einblendungen sollten nicht für statischen Inhalt verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="813c1-164">Do have Reveal on elements that the user can take actions on - Reveal should not be on static content</span></span>
- <span data-ttu-id="813c1-165">Verwenden Sie Einblendungen in Listen oder Datensammlungen.</span><span class="sxs-lookup"><span data-stu-id="813c1-165">Do show Reveal in lists or collections of data</span></span>
- <span data-ttu-id="813c1-166">Wenden Sie Einblendungen auf klar eingebundene Inhalte mit Backplates an.</span><span class="sxs-lookup"><span data-stu-id="813c1-166">Do apply Reveal to clearly contained content with backplates</span></span>
- <span data-ttu-id="813c1-167">Verwenden Sie keine Einblendungen auf statischen Hintergründen, Text oder Bildern, mit denen keine Interaktionen möglich sind.</span><span class="sxs-lookup"><span data-stu-id="813c1-167">Don’t show Reveal on static backgrounds, text, or images that you can’t interact with</span></span>
- <span data-ttu-id="813c1-168">Wenden Sie Einblendungen nicht auf nicht irrelevanten, schwebenden Inhalt an.</span><span class="sxs-lookup"><span data-stu-id="813c1-168">Don’t apply Reveal to unrelated floating content</span></span>
- <span data-ttu-id="813c1-169">Verwenden Sie Einblendungen nicht für einmalige, isolierte Situationen, wie Dialoge oder Benachrichtigungen zum Inhalt.</span><span class="sxs-lookup"><span data-stu-id="813c1-169">Don’t use Reveal in one-off, isolated situations, like content dialogs or notifications</span></span>
- <span data-ttu-id="813c1-170">Verwenden Sie Einblendungen nicht bei sicherheitsbezogenen Entscheidungen, da es die Aufmerksamkeit von der Nachricht, die Sie an die Benutzer übermitteln möchten, weglenken kann.</span><span class="sxs-lookup"><span data-stu-id="813c1-170">Don’t use Reveal in security decisions, as it may draw attention away from the message you need to deliver to your user</span></span>

## <a name="related-articles"></a><span data-ttu-id="813c1-171">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="813c1-171">Related articles</span></span>

- [<span data-ttu-id="813c1-172">RevealBrush-Klasse</span><span class="sxs-lookup"><span data-stu-id="813c1-172">RevealBrush class</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.revealbrush)
- [**<span data-ttu-id="813c1-173">Acryl</span><span class="sxs-lookup"><span data-stu-id="813c1-173">Acrylic</span></span>**](acrylic.md)
- [**<span data-ttu-id="813c1-174">Kompositionseffekte</span><span class="sxs-lookup"><span data-stu-id="813c1-174">Composition Effects</span></span>**](https://msdn.microsoft.com/windows/uwp/graphics/composition-effects)
