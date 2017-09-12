---
author: jebishop
ms.assetid: fb8ae71d-5c88-4c85-9257-a9607d5179b1
title: Beleuchtung
description: "Helle Objekte werden zusammen mit SceneLightingEffect verwendet, um dynamische Beleuchtung und Reflexionsvermögen zu simulieren."
ms.author: jimwalk
ms.date: 03/29/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 3f922cae8aa0787f8be6496997df1021dda8e142
ms.sourcegitcommit: b42d14c775efbf449a544ddb881abd1c65c1ee86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/20/2017
---
# <a name="lighting"></a>Beleuchtung

[**CompositionLight**](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionLight)-Objekte werden zusammen mit [**SceneLightingEffect**](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.Effects.SceneLightingEffect) verwendet, um dynamische Beleuchtung und Reflexionsvermögen zu simulieren.

Sie können Lichter auf [**visuelle Elemente**](https://msdn.microsoft.com/library/windows/apps/Dn706858) und XAML-[**UI-Elemente**](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.UIElement) anwenden.

## <a name="applying-lights-to-xaml-uielements"></a>Anwenden von Lichtern auf XAML-UI-Elemente

[**XamlLight**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.xamllight)-Objekte werden auf [**CompositionLights**](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionLight) angewendet, um XAML-UI-Elemente dynamisch zu beleuchten. XamlLight bietet Methoden, um UI-Elemente oder XAML-Pinsel zu bearbeiten, Lichter auf UI-Elementstrukturen anzuwenden und die Lebensdauer von CompositionLight-Ressourcen zu steuern, falls diese in Verwendung sind.

* Wenn Sie XamlLight auf einen **Pinsel** anwenden, werden damit alle UI-Elemente beleuchtet, die den Pinsel nutzen.
* Wenn Sie XamlLight auf ein **UI-Element** anwenden, wird damit das gesamte UI-Element einschließlich seiner Unterelemente beleuchtet.

## <a name="creating-and-using-a-xamllight"></a>Erstellen und Verwenden von XamlLight

[**XamlLight**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.xamllight) ist eine Basisklasse zum Erstellen benutzerdefinierter Lichter.

Hier ein Beispiel für benutzerdefiniertes XamlLight, das durch eine angefügte Eigenschaft auf bestimmte Elemente angewendet wird:

```csharp
public sealed class FancyOrangeSpotLight : XamlLight
{
    // Register an attached proeprty that enables apps to set a UIElement or Brush as a target for this light type in markup.
    public static readonly DependencyProperty IsTargetProperty =
        DependencyProperty.RegisterAttached(
        "IsTarget",
        typeof(Boolean),
        typeof(FancyOrangeSpotLight),
        new PropertyMetadata(null, OnIsTargetChanged)
    );
    public static void SetIsTarget(DependencyObject target, Boolean value)
    {
        target.SetValue(IsTargetProperty, value);
    }
    public static Boolean GetIsTarget(DependencyObject target)
    {
        return (Boolean) target.GetValue(IsTargetProperty);
    }

    // Handle attached property changed to automatically target and untarget UIElements and Brushes.
    private static void OnIsTargetChanged(DependencyObject obj,
                                            DependencyPropertyChangedEventArgs e)
    {
        var isAdding = (Boolean)e.NewValue;

        if (isAdding)
        {
            if (obj is UIElement)
            {
                XamlLight.AddTargetElement(GetIdStatic(), obj as UIElement);
            }
            else if (obj is Brush)
            {
                XamlLight.AddTargetBrush(GetIdStatic(), obj as Brush);
            }
        }
        else
        {
            if (obj is UIElement)
            {
                XamlLight.RemoveTargetElement(GetIdStatic(), obj as UIElement);
            }
            else if (obj is Brush)
            {
                XamlLight.RemoveTargetBrush(GetIdStatic(), obj as Brush);
            }
        }
    }

    protected override void OnConnected(UIElement newElement)
    {
        // OnConnected is called when the first target UIElement is shown on the screen. This enables delaying composition object creation until it's actually necessary.
        CompositionLight = Window.Current.Compositor.CreateSpotLight();
        CompositionLight.InnerConeColor = Colors.Orange;
        CompositionLight.OuterConeColor = Colors.Yellow;
        CompositionLight.InnerConeAngleInDegrees = 30;
        CompositionLight.OuterConeAngleInDegrees = 45;
    }

    protected override void OnDisconnected(UIElement oldElement)
    {
        // OnDisconnected is called when there are no more target UIElements on the screen. The CompositionLight should be disposed when no longer required.
        CompositionLight.Dispose();
        CompositionLight = null;
    }

    protected override string GetId()
    {
        return GetIdStatic();
    }

    private static string GetIdStatic()
    {
        // This specifies the unique name of the light. In most cases you should use the type's FullName.
        return typeof(FancyPointerTrackerLight).FullName;
    }
}
```

Und hier ein Beispiel für verschiedene Verwendungen des benutzerdefinierten Lichts (s. o.):

```xml
<Page>
    <Page.Lights>
        <local:SimpleOrangeSpotLight />
    </Page.Lights>

    <StackPanel>
        <!-- this border will be lit by a FancyOrangeSpotLight, but not its children -->
        <Border BorderThickness="1">
            <Border.BorderBrush>
                <SolidColorBrush Color="Orange" local:FancyOrangeSpotLight.IsTarget="true" />
            </Border.BorderBrush>
            <TextBlock Text="hello world" />
        </Border>

        <!-- this border and its children will be lit by FancyOrangeSpotLight -->
        <Border BorderThickness="2" local:FancyOrangeSpotLight.IsTarget="true">
            <Border.BorderBrush>
                <SolidColorBrush Color="Purple" />
            </Border.BorderBrush>
            <TextBlock Text="hello world" />
        </Border>

        <!-- this border will not be lit -->
        <Border BorderThickness="2">
            <Border.BorderBrush>
                <SolidColorBrush Color="Green" />
            </Border.BorderBrush>
            <TextBlock Text="hello world" />
        </Border>
    </StackPanel>
<Page>
```

> [!Important]
> Die Einstellung UIElement.Lights im Markup des obigen Beispiels wird nur für Apps mit mindestens gleicher oder höherer Version des Windows10 Creators-Updates unterstützt. Für Apps, die ältere Versionen verwenden, müssen die Lichter in CodeBehind erstellt werden.

## <a name="additional-resources"></a>Weitere Ressourcen

* Erweiterte Beispiele für Benutzeroberfläche und Komposition finden Sie im [WindowsUIDevLabs-GitHub](https://github.com/microsoft/windowsuidevlabs).