---
author: Jwmsft
title: XAML-Eigenschaftenanimationen
description: XAML-Elemente mit kompositionsanimationen animieren.
ms.author: jimwalk
ms.date: 09/13/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
pm-contact: stmoy
design-contact: jeffarn
ms.localizationpriority: medium
ms.openlocfilehash: a03ffc8d5ea78ee6cbdf78feaae7ba1cd1448f37
ms.sourcegitcommit: e16c9845b52d5bd43fc02bbe92296a9682d96926
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2018
ms.locfileid: "4948019"
---
# <a name="animating-xaml-elements-with-composition-animations"></a>Animieren von XAML-Elemente mit kompositionsanimationen

Dieser Artikel führt neue Eigenschaften, mit die Sie eine XAML-UIElement mit der Leistung von kompositionsanimationen und die einfache Einstellung XAML-Eigenschaften animieren können.

Vor Windows 10, Version 1809, mussten Sie 2 Optionen zum Erstellen von Animationen in Ihren UWP-apps:

- Verwenden Sie XAML-Konstrukte wie [storyboardanimationen](storyboarded-animations.md), oder die _* ThemeTransition_ und _* ThemeAnimation_ Klassen im Namespace [Windows.UI.Xaml.Media.Animation](/uwp/api/windows.ui.xaml.media.animation) .
- Verwenden Sie kompositionsanimationen, wie sich [mit der visuellen Ebene mit XAML](../../composition/using-the-visual-layer-with-xaml.md)beschrieben.

Mit der visuellen Ebene bietet eine bessere Leistung als mit der XAML-Code erstellt. Aber mit [ElementCompositionPreview](/uwp/api/Windows.UI.Xaml.Hosting.ElementCompositionPreview) des Elements zugrunde liegenden Composition [Visual](/uwp/api/windows.ui.composition.visual) -Objekt abzurufen, und klicken Sie dann Animieren des visuellen Elements mit kompositionsanimationen, ist schwieriger zu verwenden.

Ab Windows 10, Version 1809, können Sie Eigenschaften für ein UIElement direkt mit kompositionsanimationen ohne die Anforderung zum Abrufen der zugrunde liegenden Kompositions Visual animieren.

> [!NOTE]
> Um diese Eigenschaften auf UIElement zu verwenden, muss Ihre UWP-Projekt-Zielversion 1809 oder höher sein. Weitere Informationen zum Konfigurieren von Ihrem Projektversion finden Sie unter [versionsadaptive apps](../../debug-test-perf/version-adaptive-apps.md).

## <a name="new-rendering-properties-replace-old-rendering-properties"></a>Neue Renderingeigenschaften ersetzen alte Renderingeigenschaften

Diese Tabelle zeigt die Eigenschaften, mit denen Sie die Darstellung eines UI-Elements, ändern, die auch mit einem [CompositionAnimation](/uwp/api/windows.ui.composition.compositionanimation)animiert werden kann.

| Eigenschaft | Typ | Beschreibung |
| -- | -- | -- |
| [Opacity](/uwp/api/windows.ui.xaml.uielement.opacity) | Double | Der Grad der Deckkraft des Objekts |
| [Translation](/uwp/api/windows.ui.xaml.uielement.translation) | Vector3 | Die X/Y/Z-Position des Elements zu verschieben |
| [TransformMatrix](/uwp/api/windows.ui.xaml.uielement.transformmatrix) | Matrix4x4 | Die Transformationsmatrix auf das Element anwenden |
| [Scale](/uwp/api/windows.ui.xaml.uielement.scale) | Vector3 | Skalieren Sie das Element, auf den Mittelpunkt zentriert |
| [Drehung](/uwp/api/windows.ui.xaml.uielement.rotation) | Gleitkomma | Das Element, um die Drehachse und Mittelpunkt drehen |
| [RotationAxis](/uwp/api/windows.ui.xaml.uielement.rotationaxis) | Vector3 | Die Drehachse |
| [CenterPoint](/uwp/api/windows.ui.xaml.uielement.centerpoint) | Vector3 | Der Mittelpunkt der Skalierung und Drehung |

Der Wert der TransformMatrix-Eigenschaft ist in Kombination mit der Skalierung, Drehung und Translation Eigenschaften in der folgenden Reihenfolge: TransformMatrix, Skalierung, Drehung, Translation.

Diese Eigenschaften wirken sich nicht auf das Element Layout, also ändern diese Eigenschaften nicht dazu, dass ein neues [Measure](/uwp/api/windows.ui.xaml.uielement.measure)/[Anordnungsübergabe](/uwp/api/windows.ui.xaml.uielement.arrange) .

Diese Eigenschaften haben den gleichen Zweck und Verhalten, als der gleichnamigen Eigenschaften für die Komposition [Visual](/uwp/api/windows.ui.composition.visual) -Klasse (außer für die Übersetzung Visual nicht ist).

### <a name="example-setting-the-scale-property"></a>Beispiel: Festlegen der Scale-Eigenschaft

In diesem Beispiel wird veranschaulicht, wie die Scale-Eigenschaft auf einer Schaltfläche festgelegt.

```xaml
<Button Scale="2,2,1" Content="I am a large button" />
```

```csharp
var button = new Button();
button.Content = "I am a large button";
button.Scale = new Vector3(2.0f,2.0f,1.0f);
```

### <a name="mutual-exclusivity-between-new-and-old-properties"></a>Gegenseitigen Ausschließlichkeit zwischen neuen und alten Eigenschaften

> [!NOTE]
> Die **Opacity** -Eigenschaft wird die gegenseitige Exklusivität in diesem Abschnitt beschriebenen nicht erzwungen. Sie verwenden die gleiche Opacity-Eigenschaft, ob Sie die Verwendung von XAML oder Komposition Animationen.

Die Eigenschaften, die mit einem CompositionAnimation animiert werden können sind Ersatz für mehrere vorhandenen UIElement-Eigenschaften:

- [RenderTransform](/uwp/api/windows.ui.xaml.uielement.rendertransform)
- [RenderTransformOrigin](/uwp/api/windows.ui.xaml.uielement.rendertransformorigin)
- [Projection](/uwp/api/windows.ui.xaml.uielement.projection)
- [Transform3D](/uwp/api/windows.ui.xaml.uielement.transform3d)

Wenn Sie festgelegt (oder animieren) der neuen Eigenschaften, können nicht Sie die alten Eigenschaften verwenden. Im Gegensatz dazu festlegen (oder animieren) der alten Eigenschaften, kann nicht die neuen Eigenschaften verwenden.

Sie können nicht die neuen Eigenschaften auch verwenden, wenn Sie ElementCompositionPreview zum Abrufen und Verwalten des visuellen Elements selbst mithilfe der folgenden Methoden verwenden:

- [ElementCompositionPreview.GetElementVisual](/uwp/api/windows.ui.xaml.hosting.elementcompositionpreview.getelementvisual)
- [ElementCompositionPreview.SetIsTranslationEnabled](/uwp/api/windows.ui.xaml.hosting.elementcompositionpreview.setistranslationenabled)

> [!IMPORTANT]
> Wenn Sie versuchen, die Verwendung von zwei Gruppen von Eigenschaften mischen bewirkt, dass die API-Aufruf fehl, und erstellen eine Fehlermeldung angezeigt.

Es ist möglich, wechseln aus einer Reihe von Eigenschaften durch deaktivieren, obwohl der Einfachheit halber nicht empfohlen wird. Wenn die Eigenschaft durch einen DependencyProperty unterstützt wird (z. B. UIElement.Projection durch UIElement.ProjectionProperty gesichert ist), rufen Sie dann ClearValue zum Zustand "nicht verwendete" wiederherstellen. Andernfalls (z. B. die Scale-Eigenschaft), festlegen die Eigenschaft auf den Standardwert.

## <a name="animating-uielement-properties-with-compositionanimation"></a>Animieren von UIElement Eigenschaften mit CompositionAnimation

Sie können in der Tabelle mit einer CompositionAnimation aufgeführten Renderingeigenschaften animieren. Diese Eigenschaften können auch von einer [ExpressionAnimation](/uwp/api/windows.ui.composition.expressionanimation)verwiesen werden.

Verwenden Sie die Methoden [StartAnimation](/uwp/api/windows.ui.xaml.uielement.startanimation) und ["stopanimation"](/uwp/api/windows.ui.xaml.uielement.stopanimation) auf UIElement UIElement-Eigenschaften animieren.

### <a name="example-animating-the-scale-property-with-a-vector3keyframeanimation"></a>Beispiel: Animieren der Skalierung-Eigenschaft mit einem Vector3KeyFrameAnimation

In diesem Beispiel wird veranschaulicht, wie die Skalierung einer Schaltfläche animieren.

```csharp
var compositor = Window.Current.Compositor;
var animation = compositor.CreateVector3KeyFrameAnimation();

animation.InsertKeyFrame(1.0f, new Vector3(2.0f,2.0f,1.0f));
animation.Duration = TimeSpan.FromSeconds(1);
animation.Target = "Scale";

button.StartAnimation(animation);
```

### <a name="example-animating-the-scale-property-with-an-expressionanimation"></a>Beispiel: Animieren der Skalierungseigenschaft mit einer ExpressionAnimation

Eine Seite verfügt über zwei Schaltflächen. Die zweite Schaltfläche animiert, um doppelt so groß (über Skalierung) sein wie die erste Schaltfläche.

```xaml
<Button x:Name="sourceButton" Content="Source"/>
<Button x:Name="destinationButton" Content="Destination"/>
```

```csharp
var compositor = Window.Current.Compositor;
var animation = compositor.CreateExpressionAnimation("sourceButton.Scale*2");
animation.SetExpressionReferenceParameter("sourceButton", sourceButton);
animation.Target = "Scale";
destinationButton.StartAnimation(animation);
```

## <a name="related-topics"></a>Verwandte Themen

- [Storyboard-Animationen](storyboarded-animations.md)
- [Benutzung des Visual Layer mit XAML](../../composition/using-the-visual-layer-with-xaml.md)
- [Transformationen – Übersicht](../layout/transforms.md)