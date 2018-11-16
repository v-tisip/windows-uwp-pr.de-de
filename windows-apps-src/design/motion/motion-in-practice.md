---
author: jwmsft
Description: Learn how Fluent motion fundamentals come together in your app.
title: Bewegung in der Praxis – Animationen in UWP-Apps
label: Motion in practice
template: detail.hbs
ms.author: jimwalk
ms.date: 10/02/2018
ms.topic: article
keywords: Windows 10, UWP
pm-contact: stmoy
design-contact: jeffarn
doc-status: Draft
ms.localizationpriority: medium
ms.openlocfilehash: 36081c14cfb75a1cedb103ba17eff4a05f5e4e83
ms.sourcegitcommit: e2fca6c79f31e521ba76f7ecf343cf8f278e6a15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6988319"
---
# <a name="bringing-it-together"></a><span data-ttu-id="8683d-103">Alles zusammenführen</span><span class="sxs-lookup"><span data-stu-id="8683d-103">Bringing it together</span></span>

<span data-ttu-id="8683d-104">Timing, Geschwindigkeitsverlauf, Direktionalität und Schwerkraft bilden zusammen die Grundlage für fließende Bewegungen.</span><span class="sxs-lookup"><span data-stu-id="8683d-104">Timing, easing, directionality, and gravity work together to form the foundation of Fluent motion.</span></span> <span data-ttu-id="8683d-105">Jede Komponente muss im Zusammenhang mit den anderen betrachtet und dem Kontext Ihrer App entsprechend angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="8683d-105">Each has to be considered in the context of the others, and applied appropriately in the context of your app.</span></span>

<span data-ttu-id="8683d-106">Im Folgenden finden Sie 3 Möglichkeiten, die Grundlagen für fließende Bewegung in Ihrer App anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="8683d-106">Here are 3 ways to apply Fluent motion fundamentals in your app.</span></span>

:::row:::
    :::column:::
        **Implicit animation**

        Automatic tween and timing between values in a parameter change to achieve very simple Fluent motion using the standardized values.
    :::column-end:::
    :::column:::
        **Built-in animation**

        System components, such as common controls and shared motion, are "Fluent by default". Fundamentals have been applied in a manner consistent with their implied usage.
    :::column-end:::
    :::column:::
        **Custom animation following guidance recommendations**

        There may be times when the system does not yet provide an exact motion solution for your scenario. In those cases, use the baseline fundamental recommendations as a starting point for your experiences.
    :::column-end:::
:::row-end:::

**<span data-ttu-id="8683d-107">Beispielübergang</span><span class="sxs-lookup"><span data-stu-id="8683d-107">Transition example</span></span>**

![funktionelle Animation](images/pageRefresh.gif)

:::row:::
    :::column:::
        <b>Direction Forward Out:</b><br>
        Fade out: 150m; Easing: Default Accelerate

        <b>Direction Forward In:</b><br>
        Slide up 150px: 300ms; Easing: Default Decelerate
    :::column-end:::
    :::column:::
         <b>Direction Backward Out:</b><br>
        Slide down 150px: 150ms; Easing: Default Accelerate

        <b>Direction Backward In:</b><br>
        Fade in: 300ms; Easing: Default Decelerate
    :::column-end:::
:::row-end:::

**<span data-ttu-id="8683d-109">Objektbeispiel</span><span class="sxs-lookup"><span data-stu-id="8683d-109">Object example</span></span>**

 ![300 ms Bewegung](images/control.gif)

:::row:::
    :::column:::
        <b>Direction Expand:</b><br>
        Grow: 300ms; Easing: Standard
    :::column-end:::
    :::column:::
        <b>Direction Contract:</b><br>
        Grow: 150ms; Easing: Default Accelerate
    :::column-end:::
:::row-end:::

## <a name="implicit-animations"></a><span data-ttu-id="8683d-111">Implizite Animationen</span><span class="sxs-lookup"><span data-stu-id="8683d-111">Implicit Animations</span></span>

> <span data-ttu-id="8683d-112">Implizite Animationen erfordert Windows 10, Version 1809 ([SDK 17763](https://developer.microsoft.com/windows/downloads/windows-10-sdk)) oder höher.</span><span class="sxs-lookup"><span data-stu-id="8683d-112">Implicit animations require Windows 10, version 1809 ([SDK 17763](https://developer.microsoft.com/windows/downloads/windows-10-sdk)) or later.</span></span>


<span data-ttu-id="8683d-113">Implizite Animationen sind eine einfache Möglichkeit, fließende Bewegung zu erzielen, indem Sie automatisch zwischen der alten und neuen Werte während der eine Änderung der Parameter interpoliert.</span><span class="sxs-lookup"><span data-stu-id="8683d-113">Implicit animations are a simple way to achieve Fluent motion by automatically interpolating between the old and new values during a parameter change.</span></span>

<span data-ttu-id="8683d-114">Sie können implizit animieren, Änderungen an die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="8683d-114">You can implicitly animate changes to the following properties:</span></span>

- [<span data-ttu-id="8683d-115">UIElement</span><span class="sxs-lookup"><span data-stu-id="8683d-115">UIElement</span></span>](/uwp/api/windows.ui.xaml.uielement)
  - **<span data-ttu-id="8683d-116">Opacity</span><span class="sxs-lookup"><span data-stu-id="8683d-116">Opacity</span></span>**
  - **<span data-ttu-id="8683d-117">Drehung</span><span class="sxs-lookup"><span data-stu-id="8683d-117">Rotation</span></span>**
  - **<span data-ttu-id="8683d-118">Skalierung</span><span class="sxs-lookup"><span data-stu-id="8683d-118">Scale</span></span>**
  - **<span data-ttu-id="8683d-119">Translation</span><span class="sxs-lookup"><span data-stu-id="8683d-119">Translation</span></span>**

- <span data-ttu-id="8683d-120">[Rahmen](/uwp/api/windows.ui.xaml.controls.border), [ContentPresenter](/uwp/api/windows.ui.xaml.controls.contentpresenter)oder [Panel](/uwp/api/windows.ui.xaml.controls.panel)</span><span class="sxs-lookup"><span data-stu-id="8683d-120">[Border](/uwp/api/windows.ui.xaml.controls.border), [ContentPresenter](/uwp/api/windows.ui.xaml.controls.contentpresenter), or [Panel](/uwp/api/windows.ui.xaml.controls.panel)</span></span>
  - **<span data-ttu-id="8683d-121">Hintergrund</span><span class="sxs-lookup"><span data-stu-id="8683d-121">Background</span></span>**

<span data-ttu-id="8683d-122">Jede Eigenschaft, die Änderungen, die implizit animiert haben, können verfügt über eine entsprechende _Übergang_ -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="8683d-122">Each property that can have changes implicitly animated has a corresponding _transition_ property.</span></span> <span data-ttu-id="8683d-123">Um die Eigenschaft zu animieren, weisen Sie einen Übergangstyp auf die entsprechende Eigenschaft für den _Übergang_ .</span><span class="sxs-lookup"><span data-stu-id="8683d-123">To animate the property, you assign a transition type to the corresponding _transition_ property.</span></span> <span data-ttu-id="8683d-124">Diese Tabelle zeigt den _Übergang_ Eigenschaften und den Übergangstyp für jeden Typ verwenden.</span><span class="sxs-lookup"><span data-stu-id="8683d-124">This table shows the _transition_ properties and the transition type to use for each one.</span></span>

| <span data-ttu-id="8683d-125">Animierten Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="8683d-125">Animated property</span></span> | <span data-ttu-id="8683d-126">Übergang-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="8683d-126">Transition property</span></span> | <span data-ttu-id="8683d-127">Implizite Übergangstyp</span><span class="sxs-lookup"><span data-stu-id="8683d-127">Implicit transition type</span></span> |
| -- | -- | -- |
| [<span data-ttu-id="8683d-128">UIElement.Opacity</span><span class="sxs-lookup"><span data-stu-id="8683d-128">UIElement.Opacity</span></span>](/uwp/api/windows.ui.xaml.uielement.opacity) | [<span data-ttu-id="8683d-129">OpacityTransition</span><span class="sxs-lookup"><span data-stu-id="8683d-129">OpacityTransition</span></span>](/uwp/api/windows.ui.xaml.uielement.opacitytransition) | [<span data-ttu-id="8683d-130">ScalarTransition</span><span class="sxs-lookup"><span data-stu-id="8683d-130">ScalarTransition</span></span>](/uwp/api/windows.ui.xaml.scalartransition) |
| [<span data-ttu-id="8683d-131">UIElement.Rotation</span><span class="sxs-lookup"><span data-stu-id="8683d-131">UIElement.Rotation</span></span>](/uwp/api/windows.ui.xaml.uielement.rotation) | [<span data-ttu-id="8683d-132">RotationTransition</span><span class="sxs-lookup"><span data-stu-id="8683d-132">RotationTransition</span></span>](/uwp/api/windows.ui.xaml.uielement.rotationtransition) | [<span data-ttu-id="8683d-133">ScalarTransition</span><span class="sxs-lookup"><span data-stu-id="8683d-133">ScalarTransition</span></span>](/uwp/api/windows.ui.xaml.scalartransition) |
| [<span data-ttu-id="8683d-134">UIElement.Scale</span><span class="sxs-lookup"><span data-stu-id="8683d-134">UIElement.Scale</span></span>](/uwp/api/windows.ui.xaml.uielement.scale) | [<span data-ttu-id="8683d-135">ScaleTransition</span><span class="sxs-lookup"><span data-stu-id="8683d-135">ScaleTransition</span></span>](/uwp/api/windows.ui.xaml.uielement.scaletransition) | [<span data-ttu-id="8683d-136">Vector3Transition</span><span class="sxs-lookup"><span data-stu-id="8683d-136">Vector3Transition</span></span>](/uwp/api/windows.ui.xaml.uielement.vector3transition) |
| [<span data-ttu-id="8683d-137">UIElement.Translation</span><span class="sxs-lookup"><span data-stu-id="8683d-137">UIElement.Translation</span></span>](/uwp/api/windows.ui.xaml.uielement.scale) | [<span data-ttu-id="8683d-138">TranslationTransition</span><span class="sxs-lookup"><span data-stu-id="8683d-138">TranslationTransition</span></span>](/uwp/api/windows.ui.xaml.uielement.translationtransition) | [<span data-ttu-id="8683d-139">Vector3Transition</span><span class="sxs-lookup"><span data-stu-id="8683d-139">Vector3Transition</span></span>](/uwp/api/windows.ui.xaml.uielement.vector3transition) |
| [<span data-ttu-id="8683d-140">Border.Background</span><span class="sxs-lookup"><span data-stu-id="8683d-140">Border.Background</span></span>](/uwp/api/windows.ui.xaml.controls.border.background) | [<span data-ttu-id="8683d-141">BackgroundTransition</span><span class="sxs-lookup"><span data-stu-id="8683d-141">BackgroundTransition</span></span>](/uwp/api/windows.ui.xaml.controls.border.backgroundtransition) | [<span data-ttu-id="8683d-142">BrushTransition</span><span class="sxs-lookup"><span data-stu-id="8683d-142">BrushTransition</span></span>](//uwp/api/windows.ui.xaml.uielement.brushtransition) |
| [<span data-ttu-id="8683d-143">ContentPresenter.Background</span><span class="sxs-lookup"><span data-stu-id="8683d-143">ContentPresenter.Background</span></span>](/uwp/api/windows.ui.xaml.controls.contentpresenter.background) | [<span data-ttu-id="8683d-144">BackgroundTransition</span><span class="sxs-lookup"><span data-stu-id="8683d-144">BackgroundTransition</span></span>](/uwp/api/windows.ui.xaml.controls.contentpresenter.backgroundtransition) | [<span data-ttu-id="8683d-145">BrushTransition</span><span class="sxs-lookup"><span data-stu-id="8683d-145">BrushTransition</span></span>](//uwp/api/windows.ui.xaml.uielement.brushtransition) |
| [<span data-ttu-id="8683d-146">Panel.Background</span><span class="sxs-lookup"><span data-stu-id="8683d-146">Panel.Background</span></span>](/uwp/api/windows.ui.xaml.controls.panel.background) | [<span data-ttu-id="8683d-147">BackgroundTransition</span><span class="sxs-lookup"><span data-stu-id="8683d-147">BackgroundTransition</span></span>](/uwp/api/windows.ui.xaml.controls.panel.backgroundtransition)  | [<span data-ttu-id="8683d-148">BrushTransition</span><span class="sxs-lookup"><span data-stu-id="8683d-148">BrushTransition</span></span>](//uwp/api/windows.ui.xaml.uielement.brushtransition) |

<span data-ttu-id="8683d-149">In diesem Beispiel wird veranschaulicht, wie Sie die Opacity-Eigenschaft und den Übergang zum Stellen einer Schaltfläche eingeblendet, wenn das Steuerelement aktiviert ist und ausblendungsanimationen, wenn es deaktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="8683d-149">This example shows how to use the Opacity property and transition to make a button fade in when the control is enabled and fade out when it's disabled.</span></span>

```xaml
<Button x:Name="SubmitButton"
        Content="Submit"
        Opacity="{x:Bind OpaqueIfEnabled(SubmitButton.IsEnabled), Mode=OneWay}">
    <Button.OpacityTransition>
        <ScalarTransition />
    </Button.OpacityTransition>
</Button>
```

```csharp
public double OpaqueIfEnabled(bool IsEnabled)
{
    return IsEnabled ? 1.0 : 0.2;
}
```

## <a name="related-articles"></a><span data-ttu-id="8683d-150">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="8683d-150">Related articles</span></span>

- [<span data-ttu-id="8683d-151">Übersicht über Bewegungen</span><span class="sxs-lookup"><span data-stu-id="8683d-151">Motion overview</span></span>](index.md)
- [<span data-ttu-id="8683d-152">Timing und Geschwindigkeitsverlauf</span><span class="sxs-lookup"><span data-stu-id="8683d-152">Timing and easing</span></span>](timing-and-easing.md)
- [<span data-ttu-id="8683d-153">Direktionalität und Schwerkraft</span><span class="sxs-lookup"><span data-stu-id="8683d-153">Directionality and gravity</span></span>](directionality-and-gravity.md)