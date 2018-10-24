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
ms.sourcegitcommit: 4b97117d3aff38db89d560502a3c372f12bb6ed5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "5434102"
---
# <a name="bringing-it-together"></a>Alles zusammenführen

Timing, Geschwindigkeitsverlauf, Direktionalität und Schwerkraft bilden zusammen die Grundlage für fließende Bewegungen. Jede Komponente muss im Zusammenhang mit den anderen betrachtet und dem Kontext Ihrer App entsprechend angewendet werden.

Im Folgenden finden Sie 3 Möglichkeiten, die Grundlagen für fließende Bewegung in Ihrer App anzuwenden.

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

**Beispielübergang**

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

**Objektbeispiel**

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

## <a name="implicit-animations"></a>Implizite Animationen

> **Vorschau**: implizite Animation ist der [neuesten Windows 10 Insider Preview-Build und SDK](https://insider.windows.com/for-developers/)erforderlich.

Implizite Animationen sind eine einfache Möglichkeit, Fluent-Bewegungen zu erreichen, indem Sie automatisch zwischen dem alte und neue Werte während der eine Änderung der Parameter interpoliert.

Sie können implizit Änderungen an die folgenden Eigenschaften animieren:

- [UIElement](/uwp/api/windows.ui.xaml.uielement)
  - **Opacity**
  - **Drehung**
  - **Skalierung**
  - **Translation**

- [Rahmen](/uwp/api/windows.ui.xaml.controls.border), [ContentPresenter](/uwp/api/windows.ui.xaml.controls.contentpresenter)oder [Panel](/uwp/api/windows.ui.xaml.controls.panel)
  - **Hintergrund**

Jede Eigenschaft, die Änderungen, die implizit animiert haben können verfügt über eine entsprechende _Übergang_ -Eigenschaft. Um die Eigenschaft zu animieren, weisen Sie ein anderes Übergang auf die entsprechende _Übergang_ -Eigenschaft. Diese Tabelle zeigt den _Übergang_ Eigenschaften und der Übergangstyp, verwenden Sie für jede Datei.

| Animierten Eigenschaft | Übergang-Eigenschaft | Implizite Übergangstyp |
| -- | -- | -- |
| [UIElement.Opacity](/uwp/api/windows.ui.xaml.uielement.opacity) | [OpacityTransition](/uwp/api/windows.ui.xaml.uielement.opacitytransition) | [ScalarTransition](/uwp/api/windows.ui.xaml.scalartransition) |
| [UIElement.Rotation](/uwp/api/windows.ui.xaml.uielement.rotation) | [RotationTransition](/uwp/api/windows.ui.xaml.uielement.rotationtransition) | [ScalarTransition](/uwp/api/windows.ui.xaml.scalartransition) |
| [UIElement.Scale](/uwp/api/windows.ui.xaml.uielement.scale) | [ScaleTransition](/uwp/api/windows.ui.xaml.uielement.scaletransition) | [Vector3Transition](/uwp/api/windows.ui.xaml.uielement.vector3transition) |
| [UIElement.Translation](/uwp/api/windows.ui.xaml.uielement.scale) | [TranslationTransition](/uwp/api/windows.ui.xaml.uielement.translationtransition) | [Vector3Transition](/uwp/api/windows.ui.xaml.uielement.vector3transition) |
| [Border.Background](/uwp/api/windows.ui.xaml.controls.border.background) | [BackgroundTransition](/uwp/api/windows.ui.xaml.controls.border.backgroundtransition) | [BrushTransition](//uwp/api/windows.ui.xaml.uielement.brushtransition) |
| [ContentPresenter.Background](/uwp/api/windows.ui.xaml.controls.contentpresenter.background) | [BackgroundTransition](/uwp/api/windows.ui.xaml.controls.contentpresenter.backgroundtransition) | [BrushTransition](//uwp/api/windows.ui.xaml.uielement.brushtransition) |
| [Panel.Background](/uwp/api/windows.ui.xaml.controls.panel.background) | [BackgroundTransition](/uwp/api/windows.ui.xaml.controls.panel.backgroundtransition)  | [BrushTransition](//uwp/api/windows.ui.xaml.uielement.brushtransition) |

In diesem Beispiel wird veranschaulicht, wie mit der Opacity-Eigenschaft und Übergang zu einer Schaltfläche eingeblendet, wenn das Steuerelement aktiviert ist und ausblenden, wenn es deaktiviert ist.

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

## <a name="related-articles"></a>Verwandte Artikel

- [Übersicht über Bewegungen](index.md)
- [Timing und Geschwindigkeitsverlauf](timing-and-easing.md)
- [Direktionalität und Schwerkraft](directionality-and-gravity.md)