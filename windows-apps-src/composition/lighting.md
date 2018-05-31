---
author: jebishop
ms.assetid: fb8ae71d-5c88-4c85-9257-a9607d5179b1
title: Beleuchtung
description: Helle Objekte werden zusammen mit SceneLightingEffect verwendet, um dynamische Beleuchtung und Reflexionsvermögen zu simulieren.
ms.author: jimwalk
ms.date: 03/29/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 316b79fa9fc9a700d606f0881a89a299523330b1
ms.sourcegitcommit: 2470c6596d67e1f5ca26b44fad56a2f89773e9cc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
ms.locfileid: "1673707"
---
# <a name="lighting"></a><span data-ttu-id="c871c-104">Beleuchtung</span><span class="sxs-lookup"><span data-stu-id="c871c-104">Lighting</span></span>

<span data-ttu-id="c871c-105">[**CompositionLight**](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionLight)-Objekte werden zusammen mit [**SceneLightingEffect**](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.Effects.SceneLightingEffect) verwendet, um dynamische Beleuchtung und Reflexionsvermögen zu simulieren.</span><span class="sxs-lookup"><span data-stu-id="c871c-105">[**CompositionLight**](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionLight) objects are used in conjunction with [**SceneLightingEffect**](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.Effects.SceneLightingEffect) to simulate dynamic lighting and reflectivity.</span></span>

<span data-ttu-id="c871c-106">Sie können Lichter auf [**visuelle Elemente**](https://msdn.microsoft.com/library/windows/apps/Dn706858) und XAML-[**UI-Elemente**](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.UIElement) anwenden.</span><span class="sxs-lookup"><span data-stu-id="c871c-106">You can apply lights to [**Visuals**](https://msdn.microsoft.com/library/windows/apps/Dn706858) and XAML [**UIElements**](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.UIElement).</span></span>

## <a name="applying-lights-to-xaml-uielements"></a><span data-ttu-id="c871c-107">Anwenden von Lichtern auf XAML-UI-Elemente</span><span class="sxs-lookup"><span data-stu-id="c871c-107">Applying lights to XAML UIElements</span></span>

<span data-ttu-id="c871c-108">[**XamlLight**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.xamllight)-Objekte werden auf [**CompositionLights**](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionLight) angewendet, um XAML-UI-Elemente dynamisch zu beleuchten.</span><span class="sxs-lookup"><span data-stu-id="c871c-108">[**XamlLight**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.xamllight) objects are used to apply [**CompositionLights**](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionLight) to dynamically light XAML UIElements.</span></span> <span data-ttu-id="c871c-109">XamlLight bietet Methoden, um UI-Elemente oder XAML-Pinsel zu bearbeiten, Lichter auf UI-Elementstrukturen anzuwenden und die Lebensdauer von CompositionLight-Ressourcen zu steuern, falls diese in Verwendung sind.</span><span class="sxs-lookup"><span data-stu-id="c871c-109">XamlLight provides methods for targeting UIElements or other XAML Brushes, applying lights to trees of UIElements, and helping manage the lifetime of CompositionLight resources based on whether they're currently in use.</span></span>

* <span data-ttu-id="c871c-110">Wenn Sie XamlLight auf einen **Pinsel** anwenden, werden damit alle UI-Elemente beleuchtet, die den Pinsel nutzen.</span><span class="sxs-lookup"><span data-stu-id="c871c-110">If you target a **Brush** with a XamlLight then the portions of any UIElements using that Brush are lit by the light.</span></span>
* <span data-ttu-id="c871c-111">Wenn Sie XamlLight auf ein **UI-Element** anwenden, wird damit das gesamte UI-Element einschließlich seiner Unterelemente beleuchtet.</span><span class="sxs-lookup"><span data-stu-id="c871c-111">If you target a **UIElement** with a XamlLight then the entire UIElement and its child UIElements are all lit by the light.</span></span>

## <a name="creating-and-using-a-xamllight"></a><span data-ttu-id="c871c-112">Erstellen und Verwenden von XamlLight</span><span class="sxs-lookup"><span data-stu-id="c871c-112">Creating and using a XamlLight</span></span>

<span data-ttu-id="c871c-113">[**XamlLight**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.xamllight) ist eine Basisklasse zum Erstellen benutzerdefinierter Lichter.</span><span class="sxs-lookup"><span data-stu-id="c871c-113">[**XamlLight**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.xamllight) is a base class which can be used to create custom lights.</span></span>

<span data-ttu-id="c871c-114">Hier ein Beispiel für benutzerdefiniertes XamlLight, das durch eine angefügte Eigenschaft auf bestimmte Elemente angewendet wird:</span><span class="sxs-lookup"><span data-stu-id="c871c-114">Here is an example of a custom XamlLight that uses an attached property to target specific elements:</span></span>

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
        var spotLight = Window.Current.Compositor.CreateSpotLight();
        spotLight.InnerConeColor = Colors.Orange;
        spotLight.OuterConeColor = Colors.Yellow;
        spotLight.InnerConeAngleInDegrees = 30;
        spotLight.OuterConeAngleInDegrees = 45;
        CompositionLight = spotLight;
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

<span data-ttu-id="c871c-115">Und hier ein Beispiel für verschiedene Verwendungen des benutzerdefinierten Lichts (s. o.):</span><span class="sxs-lookup"><span data-stu-id="c871c-115">And here is an example showing different possible uses of the custom light defined above:</span></span>

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
> <span data-ttu-id="c871c-116">Die Einstellung UIElement.Lights im Markup des obigen Beispiels wird nur für Apps mit mindestens gleicher oder höherer Version des Windows10 Creators-Updates unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c871c-116">Setting UIElement.Lights in markup as shown in the above example is only supported for apps with a Minimum Version equal to the Windows 10 Creators Update or later.</span></span> <span data-ttu-id="c871c-117">Für Apps, die ältere Versionen verwenden, müssen die Lichter in CodeBehind erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="c871c-117">For apps that target earlier versions, lights must be created in code-behind.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="c871c-118">Weitere Ressourcen</span><span class="sxs-lookup"><span data-stu-id="c871c-118">Additional Resources</span></span>

* <span data-ttu-id="c871c-119">Erweiterte Beispiele für Benutzeroberfläche und Komposition finden Sie im [WindowsUIDevLabs-GitHub](https://github.com/microsoft/windowsuidevlabs).</span><span class="sxs-lookup"><span data-stu-id="c871c-119">Advanced UI and Composition samples in the [WindowsUIDevLabs GitHub](https://github.com/microsoft/windowsuidevlabs).</span></span>
