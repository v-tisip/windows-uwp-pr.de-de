---
author: jwmsft
Description: Learn how Fluent motion fundamentals come together in your app.
title: Bewegung in der Praxis – Animationen in UWP-Apps
label: Motion in practice
template: detail.hbs
ms.author: jimwalk
ms.date: 10/02/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
pm-contact: stmoy
design-contact: jeffarn
doc-status: Draft
ms.localizationpriority: medium
ms.openlocfilehash: 6001f955b3ab6a60446eb84296dc3bc52ad3a99e
ms.sourcegitcommit: 82c3fc0b06ad490c3456ad18180a6b23ecd9c1a7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2018
ms.locfileid: "5482995"
---
# <a name="bringing-it-together"></a><span data-ttu-id="848e8-103">Alles zusammenführen</span><span class="sxs-lookup"><span data-stu-id="848e8-103">Bringing it together</span></span>

<span data-ttu-id="848e8-104">Timing, Geschwindigkeitsverlauf, Direktionalität und Schwerkraft bilden zusammen die Grundlage für fließende Bewegungen.</span><span class="sxs-lookup"><span data-stu-id="848e8-104">Timing, easing, directionality, and gravity work together to form the foundation of Fluent motion.</span></span> <span data-ttu-id="848e8-105">Jede Komponente muss im Zusammenhang mit den anderen betrachtet und dem Kontext Ihrer App entsprechend angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="848e8-105">Each has to be considered in the context of the others, and applied appropriately in the context of your app.</span></span>

<span data-ttu-id="848e8-106">Im Folgenden finden Sie 3 Möglichkeiten, die Grundlagen für fließende Bewegung in Ihrer App anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="848e8-106">Here are 3 ways to apply Fluent motion fundamentals in your app.</span></span>

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

**<span data-ttu-id="848e8-107">Beispielübergang</span><span class="sxs-lookup"><span data-stu-id="848e8-107">Transition example</span></span>**

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

**<span data-ttu-id="848e8-109">Objektbeispiel</span><span class="sxs-lookup"><span data-stu-id="848e8-109">Object example</span></span>**

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

## <a name="implicit-animations"></a><span data-ttu-id="848e8-111">Implizite Animationen</span><span class="sxs-lookup"><span data-stu-id="848e8-111">Implicit Animations</span></span>

> <span data-ttu-id="848e8-112">**Vorschau**: implizite Animation ist der [neuesten Windows 10 Insider Preview-Build und SDK](https://insider.windows.com/for-developers/)erforderlich.</span><span class="sxs-lookup"><span data-stu-id="848e8-112">**Preview**: Implicit animation requires the [latest Windows 10 Insider Preview build and SDK](https://insider.windows.com/for-developers/).</span></span>

<span data-ttu-id="848e8-113">Implizite Animationen sind eine einfache Möglichkeit, fließende Bewegung zu erzielen, indem Sie automatisch zwischen der alten und neuen Werte während der eine Änderung der Parameter interpoliert.</span><span class="sxs-lookup"><span data-stu-id="848e8-113">Implicit animations are a simple way to achieve Fluent motion by automatically interpolating between the old and new values during a parameter change.</span></span>

<span data-ttu-id="848e8-114">Sie können implizit animieren, Änderungen an die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="848e8-114">You can implicitly animate changes to the following properties:</span></span>

- [<span data-ttu-id="848e8-115">UIElement</span><span class="sxs-lookup"><span data-stu-id="848e8-115">UIElement</span></span>](/uwp/api/windows.ui.xaml.uielement)
  - **<span data-ttu-id="848e8-116">Opacity</span><span class="sxs-lookup"><span data-stu-id="848e8-116">Opacity</span></span>**
  - **<span data-ttu-id="848e8-117">Drehung</span><span class="sxs-lookup"><span data-stu-id="848e8-117">Rotation</span></span>**
  - **<span data-ttu-id="848e8-118">Skalierung</span><span class="sxs-lookup"><span data-stu-id="848e8-118">Scale</span></span>**
  - **<span data-ttu-id="848e8-119">Translation</span><span class="sxs-lookup"><span data-stu-id="848e8-119">Translation</span></span>**

- <span data-ttu-id="848e8-120">[Rahmen](/uwp/api/windows.ui.xaml.controls.border), [ContentPresenter](/uwp/api/windows.ui.xaml.controls.contentpresenter)oder [Panel](/uwp/api/windows.ui.xaml.controls.panel)</span><span class="sxs-lookup"><span data-stu-id="848e8-120">[Border](/uwp/api/windows.ui.xaml.controls.border), [ContentPresenter](/uwp/api/windows.ui.xaml.controls.contentpresenter), or [Panel](/uwp/api/windows.ui.xaml.controls.panel)</span></span>
  - **<span data-ttu-id="848e8-121">Hintergrund</span><span class="sxs-lookup"><span data-stu-id="848e8-121">Background</span></span>**

<span data-ttu-id="848e8-122">Jede Eigenschaft, die Änderungen implizit animiert haben können hat eine entsprechende _Übergang_ -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="848e8-122">Each property that can have changes implicitly animated has a corresponding _transition_ property.</span></span> <span data-ttu-id="848e8-123">Um die Eigenschaft zu animieren, weisen Sie ein anderes Übergang auf die entsprechende _Übergang_ -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="848e8-123">To animate the property, you assign a transition type to the corresponding _transition_ property.</span></span> <span data-ttu-id="848e8-124">Diese Tabelle zeigt den _Übergang_ Eigenschaften und den Übergangstyp für jeden Typ verwenden.</span><span class="sxs-lookup"><span data-stu-id="848e8-124">This table shows the _transition_ properties and the transition type to use for each one.</span></span>

| <span data-ttu-id="848e8-125">Animierten Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="848e8-125">Animated property</span></span> | <span data-ttu-id="848e8-126">Übergang-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="848e8-126">Transition property</span></span> | <span data-ttu-id="848e8-127">Implizite Übergangstyp</span><span class="sxs-lookup"><span data-stu-id="848e8-127">Implicit transition type</span></span> |
| -- | -- | -- |
| [<span data-ttu-id="848e8-128">UIElement.Opacity</span><span class="sxs-lookup"><span data-stu-id="848e8-128">UIElement.Opacity</span></span>](/uwp/api/windows.ui.xaml.uielement.opacity) | [<span data-ttu-id="848e8-129">OpacityTransition</span><span class="sxs-lookup"><span data-stu-id="848e8-129">OpacityTransition</span></span>](/uwp/api/windows.ui.xaml.uielement.opacitytransition) | [<span data-ttu-id="848e8-130">ScalarTransition</span><span class="sxs-lookup"><span data-stu-id="848e8-130">ScalarTransition</span></span>](/uwp/api/windows.ui.xaml.scalartransition) |
| [<span data-ttu-id="848e8-131">UIElement.Rotation</span><span class="sxs-lookup"><span data-stu-id="848e8-131">UIElement.Rotation</span></span>](/uwp/api/windows.ui.xaml.uielement.rotation) | [<span data-ttu-id="848e8-132">RotationTransition</span><span class="sxs-lookup"><span data-stu-id="848e8-132">RotationTransition</span></span>](/uwp/api/windows.ui.xaml.uielement.rotationtransition) | [<span data-ttu-id="848e8-133">ScalarTransition</span><span class="sxs-lookup"><span data-stu-id="848e8-133">ScalarTransition</span></span>](/uwp/api/windows.ui.xaml.scalartransition) |
| [<span data-ttu-id="848e8-134">UIElement.Scale</span><span class="sxs-lookup"><span data-stu-id="848e8-134">UIElement.Scale</span></span>](/uwp/api/windows.ui.xaml.uielement.scale) | [<span data-ttu-id="848e8-135">ScaleTransition</span><span class="sxs-lookup"><span data-stu-id="848e8-135">ScaleTransition</span></span>](/uwp/api/windows.ui.xaml.uielement.scaletransition) | [<span data-ttu-id="848e8-136">Vector3Transition</span><span class="sxs-lookup"><span data-stu-id="848e8-136">Vector3Transition</span></span>](/uwp/api/windows.ui.xaml.uielement.vector3transition) |
| [<span data-ttu-id="848e8-137">UIElement.Translation</span><span class="sxs-lookup"><span data-stu-id="848e8-137">UIElement.Translation</span></span>](/uwp/api/windows.ui.xaml.uielement.scale) | [<span data-ttu-id="848e8-138">TranslationTransition</span><span class="sxs-lookup"><span data-stu-id="848e8-138">TranslationTransition</span></span>](/uwp/api/windows.ui.xaml.uielement.translationtransition) | [<span data-ttu-id="848e8-139">Vector3Transition</span><span class="sxs-lookup"><span data-stu-id="848e8-139">Vector3Transition</span></span>](/uwp/api/windows.ui.xaml.uielement.vector3transition) |
| [<span data-ttu-id="848e8-140">Border.Background</span><span class="sxs-lookup"><span data-stu-id="848e8-140">Border.Background</span></span>](/uwp/api/windows.ui.xaml.controls.border.background) | [<span data-ttu-id="848e8-141">BackgroundTransition</span><span class="sxs-lookup"><span data-stu-id="848e8-141">BackgroundTransition</span></span>](/uwp/api/windows.ui.xaml.controls.border.backgroundtransition) | [<span data-ttu-id="848e8-142">BrushTransition</span><span class="sxs-lookup"><span data-stu-id="848e8-142">BrushTransition</span></span>](//uwp/api/windows.ui.xaml.uielement.brushtransition) |
| [<span data-ttu-id="848e8-143">ContentPresenter.Background</span><span class="sxs-lookup"><span data-stu-id="848e8-143">ContentPresenter.Background</span></span>](/uwp/api/windows.ui.xaml.controls.contentpresenter.background) | [<span data-ttu-id="848e8-144">BackgroundTransition</span><span class="sxs-lookup"><span data-stu-id="848e8-144">BackgroundTransition</span></span>](/uwp/api/windows.ui.xaml.controls.contentpresenter.backgroundtransition) | [<span data-ttu-id="848e8-145">BrushTransition</span><span class="sxs-lookup"><span data-stu-id="848e8-145">BrushTransition</span></span>](//uwp/api/windows.ui.xaml.uielement.brushtransition) |
| [<span data-ttu-id="848e8-146">Panel.Background</span><span class="sxs-lookup"><span data-stu-id="848e8-146">Panel.Background</span></span>](/uwp/api/windows.ui.xaml.controls.panel.background) | [<span data-ttu-id="848e8-147">BackgroundTransition</span><span class="sxs-lookup"><span data-stu-id="848e8-147">BackgroundTransition</span></span>](/uwp/api/windows.ui.xaml.controls.panel.backgroundtransition)  | [<span data-ttu-id="848e8-148">BrushTransition</span><span class="sxs-lookup"><span data-stu-id="848e8-148">BrushTransition</span></span>](//uwp/api/windows.ui.xaml.uielement.brushtransition) |

<span data-ttu-id="848e8-149">In diesem Beispiel wird veranschaulicht, wie Sie die Opacity-Eigenschaft und Übergang zum Stellen einer Schaltfläche eingeblendet, wenn das Steuerelement aktiviert ist und ausblendungsanimationen, wenn es deaktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="848e8-149">This example shows how to use the Opacity property and transition to make a button fade in when the control is enabled and fade out when it's disabled.</span></span>

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

## <a name="related-articles"></a><span data-ttu-id="848e8-150">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="848e8-150">Related articles</span></span>

- [<span data-ttu-id="848e8-151">Übersicht über Bewegungen</span><span class="sxs-lookup"><span data-stu-id="848e8-151">Motion overview</span></span>](index.md)
- [<span data-ttu-id="848e8-152">Timing und Geschwindigkeitsverlauf</span><span class="sxs-lookup"><span data-stu-id="848e8-152">Timing and easing</span></span>](timing-and-easing.md)
- [<span data-ttu-id="848e8-153">Direktionalität und Schwerkraft</span><span class="sxs-lookup"><span data-stu-id="848e8-153">Directionality and gravity</span></span>](directionality-and-gravity.md)