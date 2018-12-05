---
description: Sie können mit Stilen die Steuerelementeigenschaften festlegen und diese Einstellungen dann für andere Steuerelemente übernehmen, um so für ein einheitliches Erscheinungsbild zu sorgen.
MS-HAID: dev\_ctrl\_layout\_txt.styling\_controls
MSHAttr: PreferredLib:/library/windows/apps
Search.Product: eADQiWindows 10XVcnh
title: XAML-Formatvorlagen
ms.assetid: AB469A46-FAF5-42D0-9340-948D0EDF4150
label: XAML styles
template: detail.hbs
ms.localizationpriority: medium
ms.openlocfilehash: d9f77d92e3c80e4a0d4e0808289f032b4a1125a5
ms.sourcegitcommit: d7613c791107f74b6a3dc12a372d9de916c0454b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8736775"
---
# <a name="xaml-styles"></a><span data-ttu-id="39602-103">XAML-Formatvorlagen</span><span class="sxs-lookup"><span data-stu-id="39602-103">XAML styles</span></span>





<span data-ttu-id="39602-104">Das XAML-Framework bietet zahlreiche Anpassungsmöglichkeiten für die App-Darstellung.</span><span class="sxs-lookup"><span data-stu-id="39602-104">You can customize the appearance of your apps in many ways by using the XAML framework.</span></span> <span data-ttu-id="39602-105">Sie können mit Stilen die Steuerelementeigenschaften festlegen und diese Einstellungen dann für andere Steuerelemente übernehmen, um so für ein einheitliches Erscheinungsbild zu sorgen.</span><span class="sxs-lookup"><span data-stu-id="39602-105">Styles let you set control properties and reuse those settings for a consistent appearance across multiple controls.</span></span>

## <a name="style-basics"></a><span data-ttu-id="39602-106">Grundlagen zu Stilen</span><span class="sxs-lookup"><span data-stu-id="39602-106">Style basics</span></span>

<span data-ttu-id="39602-107">Verwenden Sie Stile, um visuelle Eigenschaften in wiederverwendbare Ressourcen auszulagern.</span><span class="sxs-lookup"><span data-stu-id="39602-107">Use styles to extract visual property settings into reusable resources.</span></span> <span data-ttu-id="39602-108">Dieses Beispiel zeigt drei Schaltflächen mit einem Stil, der die Eigenschaften [BorderBrush](https://msdn.microsoft.com/library/windows/apps/br209397), [BorderThickness](https://msdn.microsoft.com/library/windows/apps/br209399) und [Foreground](https://msdn.microsoft.com/library/windows/apps/br209414) festlegt.</span><span class="sxs-lookup"><span data-stu-id="39602-108">Here's an example that shows 3 buttons with a style that sets the [BorderBrush](https://msdn.microsoft.com/library/windows/apps/br209397), [BorderThickness](https://msdn.microsoft.com/library/windows/apps/br209399) and [Foreground](https://msdn.microsoft.com/library/windows/apps/br209414) properties.</span></span> <span data-ttu-id="39602-109">Durch Anwenden eines Stils können Sie eine einheitliche Darstellung der Steuerelemente erreichen, ohne diese Eigenschaften separat für jedes Steuerelement festlegen zu müssen.</span><span class="sxs-lookup"><span data-stu-id="39602-109">By applying a style, you can make the controls appear the same without having to set these properties on each control separately.</span></span>

![Formatierte Schaltflächen](images/styles-rainbow-buttons.png)

<span data-ttu-id="39602-111">Sie können einen Stil inline im XAML-Code für ein Steuerelement oder als wiederverwendbare Ressource definieren.</span><span class="sxs-lookup"><span data-stu-id="39602-111">You can define a style inline in the XAML for a control, or as a reusable resource.</span></span> <span data-ttu-id="39602-112">Sie können Ressourcen in der XAML-Datei einer bestimmten Seite, in der Datei App.xaml oder in einer separaten XAML-Datei mit Ressourcenverzeichnis definieren.</span><span class="sxs-lookup"><span data-stu-id="39602-112">Define resources in an individual page's XAML file, in the App.xaml file, or in a separate resource dictionary XAML file.</span></span> <span data-ttu-id="39602-113">Eine XAML-Datei mit einem Ressourcenverzeichnis kann App-übergreifend genutzt werden. Außerdem können in einer einzelnen App mehrere Ressourcenverzeichnisse zusammengeführt werden.</span><span class="sxs-lookup"><span data-stu-id="39602-113">A resource dictionary XAML file can be shared across apps, and more than one resource dictionary can be merged in a single app.</span></span> <span data-ttu-id="39602-114">Der Ort, an dem die Ressource definiert wird, bestimmt den Bereich, in dem sie verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="39602-114">Where the resource is defined determines the scope in which it can be used.</span></span> <span data-ttu-id="39602-115">Ressourcen auf Seitenebene sind nur auf der Seite verfügbar, für die sie definiert sind.</span><span class="sxs-lookup"><span data-stu-id="39602-115">Page-level resources are available only in the page where they are defined.</span></span> <span data-ttu-id="39602-116">Sind Ressourcen mit demselben Schlüssel sowohl in „App.xaml“ als auch auf einer Seite definiert, haben die Ressourcen auf der Seite Vorrang vor den Ressourcen in App.xaml.</span><span class="sxs-lookup"><span data-stu-id="39602-116">If resources with the same key are defined in both App.xaml and in a page, the resource in the page overrides the resource in App.xaml.</span></span> <span data-ttu-id="39602-117">Wenn eine Ressource in einer separaten Ressourcenwörterbuchdatei definiert ist, wird Ihr Bereich dadurch bestimmt, von wo auf das Ressourcenwörterbuch verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="39602-117">If a resource is defined in a separate resource dictionary file, it's scope is determined by where the resource dictionary is referenced.</span></span>

<span data-ttu-id="39602-118">In der [Style](https://msdn.microsoft.com/library/windows/apps/br208849)-Definition benötigen wir ein [TargetType](https://msdn.microsoft.com/library/windows/apps/br208857)-Attribut und eine Auflistung eines oder mehrerer [Setter](https://msdn.microsoft.com/library/windows/apps/br208817)-Elemente.</span><span class="sxs-lookup"><span data-stu-id="39602-118">In the [Style](https://msdn.microsoft.com/library/windows/apps/br208849) definition, you need a [TargetType](https://msdn.microsoft.com/library/windows/apps/br208857) attribute and a collection of one or more [Setter](https://msdn.microsoft.com/library/windows/apps/br208817) elements.</span></span> <span data-ttu-id="39602-119">Das **TargetType**-Attribut ist eine Zeichenfolge, die einen [FrameworkElement](https://msdn.microsoft.com/library/windows/apps/br208706)-Typ angibt, auf den der Stil angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="39602-119">The **TargetType** attribute is a string that specifies a [FrameworkElement](https://msdn.microsoft.com/library/windows/apps/br208706) type to apply the style to.</span></span> <span data-ttu-id="39602-120">Der **TargetType**-Wert muss einen von **FrameworkElement** abgeleiteten Typ angeben, der durch die Windows-Runtime definiert ist, oder einen benutzerdefinierten Typ, der in einer referenzierten Assembly verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="39602-120">The **TargetType** value must specify a **FrameworkElement**-derived type that's defined by the Windows Runtime or a custom type that's available in a referenced assembly.</span></span> <span data-ttu-id="39602-121">Wenn Sie versuchen, einen Stil auf ein Steuerelement anzuwenden, das nicht zum **TargetType**-Attribut des Stils passt, der angewendet werden soll, wird eine Ausnahme ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="39602-121">If you try to apply a style to a control and the control's type doesn't match the **TargetType** attribute of the style you're trying to apply, an exception occurs.</span></span>

<span data-ttu-id="39602-122">Jedes [Setter](https://msdn.microsoft.com/library/windows/apps/br208817)-Element benötigt eine [Property](https://msdn.microsoft.com/library/windows/apps/br208836) und einen [Value](https://msdn.microsoft.com/library/windows/apps/br208838).</span><span class="sxs-lookup"><span data-stu-id="39602-122">Each [Setter](https://msdn.microsoft.com/library/windows/apps/br208817) element requires a [Property](https://msdn.microsoft.com/library/windows/apps/br208836) and a [Value](https://msdn.microsoft.com/library/windows/apps/br208838).</span></span> <span data-ttu-id="39602-123">Diese Eigenschaftseinstellungen geben die Steuerelementeigenschaft an, auf die die Einstellung angewendet wird, und den Wert, der für diese Eigenschaft festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="39602-123">These property settings indicate what control property the setting applies to, and the value to set for that property.</span></span> <span data-ttu-id="39602-124">Sie können den **Setter.Value** entweder mit Attribut- oder Eigenschaftselementsyntax angeben.</span><span class="sxs-lookup"><span data-stu-id="39602-124">You can set the **Setter.Value** with either attribute or property element syntax.</span></span> <span data-ttu-id="39602-125">Dieses XAML-Codebeispiel zeigt den Stil, der auf die zuvor abgebildeten Schaltflächen angewendet wurde.</span><span class="sxs-lookup"><span data-stu-id="39602-125">The XAML here shows the style applied to the buttons shown previously.</span></span> <span data-ttu-id="39602-126">In diesem XAML-Code verwenden die ersten beiden **Setter**-Elemente Attributsyntax, aber der letzte **Setter** (für die [BorderBrush](https://msdn.microsoft.com/library/windows/apps/br209397)-Eigenschaft) verwendet Eigenschaftselementsyntax.</span><span class="sxs-lookup"><span data-stu-id="39602-126">In this XAML, the first two **Setter** elements use attribute syntax, but the last **Setter**, for the [BorderBrush](https://msdn.microsoft.com/library/windows/apps/br209397) property, uses property element syntax.</span></span> <span data-ttu-id="39602-127">Bei diesem Beispiel wird das [x:Key-Attribut](../../xaml-platform/x-key-attribute.md) nicht verwendet, sodass der Stil implizit auf die Schaltflächen angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="39602-127">The example doesn't use the [x:Key attribute](../../xaml-platform/x-key-attribute.md) attribute, so the style is implicitly applied to the buttons.</span></span> <span data-ttu-id="39602-128">Das implizite oder explizite Anwenden von Stilen wird im nächsten Abschnitt beschrieben.</span><span class="sxs-lookup"><span data-stu-id="39602-128">Applying styles implicitly or explicitly is explained in the next section.</span></span>

```XAML
<Page.Resources>
    <Style TargetType="Button">
        <Setter Property="BorderThickness" Value="5" />
        <Setter Property="Foreground" Value="Black" />
        <Setter Property="BorderBrush" >
            <Setter.Value>
                <LinearGradientBrush StartPoint="0.5,0" EndPoint="0.5,1">
                    <GradientStop Color="Yellow" Offset="0.0" />
                    <GradientStop Color="Red" Offset="0.25" />
                    <GradientStop Color="Blue" Offset="0.75" />
                    <GradientStop Color="LimeGreen" Offset="1.0" />
                </LinearGradientBrush>
            </Setter.Value>
        </Setter>
    </Style>
</Page.Resources>

<StackPanel Orientation="Horizontal">
    <Button Content="Button"/>
    <Button Content="Button"/>
    <Button Content="Button"/>
</StackPanel>
```

## <a name="apply-an-implicit-or-explicit-style"></a><span data-ttu-id="39602-129">Anwenden impliziter oder expliziter Stile</span><span class="sxs-lookup"><span data-stu-id="39602-129">Apply an implicit or explicit style</span></span>

<span data-ttu-id="39602-130">Wenn Sie einen Stil als Ressource definieren, können Sie ihn auf zwei Arten auf Ihre Steuerelemente anwenden:</span><span class="sxs-lookup"><span data-stu-id="39602-130">If you define a style as a resource, there are two ways to apply it to your controls:</span></span>

-   <span data-ttu-id="39602-131">Implizit, indem Sie nur einen [TargetType](https://msdn.microsoft.com/library/windows/apps/br208857) für den [Style](https://msdn.microsoft.com/library/windows/apps/br208849) festlegen.</span><span class="sxs-lookup"><span data-stu-id="39602-131">Implicitly, by specifying only a [TargetType](https://msdn.microsoft.com/library/windows/apps/br208857) for the [Style](https://msdn.microsoft.com/library/windows/apps/br208849).</span></span>
-   <span data-ttu-id="39602-132">Explizit, indem Sie einen [TargetType](https://msdn.microsoft.com/library/windows/apps/br208857) und ein [x:Key-Attribut](../../xaml-platform/x-key-attribute.md) für den [Style](https://msdn.microsoft.com/library/windows/apps/br208849) angeben und die [Style](https://msdn.microsoft.com/library/windows/apps/br208743)-Eigenschaft des Zielsteuerelements mit einem Verweis auf die [{StaticResource}-Markuperweiterung](https://msdn.microsoft.com/library/windows/apps/mt185588) festlegen, die den expliziten Schlüssel verwendet.</span><span class="sxs-lookup"><span data-stu-id="39602-132">Explicitly, by specifying a [TargetType](https://msdn.microsoft.com/library/windows/apps/br208857) and an [x:Key attribute](../../xaml-platform/x-key-attribute.md) attribute for the [Style](https://msdn.microsoft.com/library/windows/apps/br208849) and then by setting the target control's [Style](https://msdn.microsoft.com/library/windows/apps/br208743) property with a [{StaticResource} markup extension](https://msdn.microsoft.com/library/windows/apps/mt185588) reference that uses the explicit key.</span></span>

<span data-ttu-id="39602-133">Wenn ein Stil ein [x:Key-Attribut](../../xaml-platform/x-key-attribute.md) enthält, können Sie ihn nur auf Steuerelemente anwenden, indem Sie die [Style](https://msdn.microsoft.com/library/windows/apps/br208743)-Eigenschaft des Steuerelements auf den Stilschlüssel festlegen.</span><span class="sxs-lookup"><span data-stu-id="39602-133">If a style contains the [x:Key attribute](../../xaml-platform/x-key-attribute.md), you can only apply it to a control by setting the [Style](https://msdn.microsoft.com/library/windows/apps/br208743) property of the control to the keyed style.</span></span> <span data-ttu-id="39602-134">Im Gegensatz dazu wird ein Stil ohne x:Key-Attribut automatisch auf jedes Steuerelement mit dem Zieltyp angewendet, das ansonsten über keine explizite Stileinstellung verfügt.</span><span class="sxs-lookup"><span data-stu-id="39602-134">In contrast, a style without an x:Key attribute is automatically applied to every control of its target type, that doesn't otherwise have an explicit style setting.</span></span>

<span data-ttu-id="39602-135">Diese beiden Schaltflächen veranschaulichen implizite und explizite Stile.</span><span class="sxs-lookup"><span data-stu-id="39602-135">Here are two buttons that demonstrate implicit and explicit styles.</span></span>

![Schaltflächen mit impliziten und expliziten Stilen](images/styles-buttons-implicit-explicit.png)

<span data-ttu-id="39602-137">In diesem Beispiel besitzt der erste Stil ein [x:Key](../../xaml-platform/x-key-attribute.md)-Attribut, und der Zieltyp ist [Button](https://msdn.microsoft.com/library/windows/apps/br209265).</span><span class="sxs-lookup"><span data-stu-id="39602-137">In this example, the first style has an [x:Key attribute](../../xaml-platform/x-key-attribute.md) and its target type is [Button](https://msdn.microsoft.com/library/windows/apps/br209265).</span></span> <span data-ttu-id="39602-138">Die [Style](https://msdn.microsoft.com/library/windows/apps/br208743)-Eigenschaft der ersten Schaltfläche wird auf diesen Schlüssel festgelegt, sodass der Stil explizit angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="39602-138">The first button's [Style](https://msdn.microsoft.com/library/windows/apps/br208743) property is set to this key, so this style is applied explicitly.</span></span> <span data-ttu-id="39602-139">Der zweite Stil wird implizit auf die zweite Schaltfläche angewendet, da deren Zieltyp **Button** ist und der Stil kein x:Key-Attribut besitzt.</span><span class="sxs-lookup"><span data-stu-id="39602-139">The second style is applied implicitly to the second button because its target type is **Button** and the style doesn't have an x:Key attribute.</span></span>

```XAML
<Page.Resources>
    <Style x:Key="PurpleStyle" TargetType="Button">
        <Setter Property="FontFamily" Value="Segoe UI"/>
        <Setter Property="FontSize" Value="14"/>
        <Setter Property="Foreground" Value="Purple"/>
    </Style>

    <Style TargetType="Button">
        <Setter Property="FontFamily" Value="Segoe UI"/>
        <Setter Property="FontSize" Value="14"/>
        <Setter Property="RenderTransform">
            <Setter.Value>
                <RotateTransform Angle="25"/>
            </Setter.Value>
        </Setter>
        <Setter Property="BorderBrush" Value="Green"/>
        <Setter Property="BorderThickness" Value="2"/>
        <Setter Property="Foreground" Value="Green"/>
    </Style>
</Page.Resources>

<Grid x:Name="LayoutRoot">
    <Button Content="Button" Style="{StaticResource PurpleStyle}"/>
    <Button Content="Button"/>
</Grid>
```

## <a name="use-based-on-styles"></a><span data-ttu-id="39602-140">Verwenden abgeleiteter Stile</span><span class="sxs-lookup"><span data-stu-id="39602-140">Use based-on styles</span></span>

<span data-ttu-id="39602-141">Um die Verwaltung von Stilen zu vereinfachen und die Wiederverwendung zu optimieren, können Sie Stile erstellen, die von anderen Stilen erben.</span><span class="sxs-lookup"><span data-stu-id="39602-141">To make styles easier to maintain and to optimize style reuse, you can create styles that inherit from other styles.</span></span> <span data-ttu-id="39602-142">Verwenden Sie die [BasedOn](https://msdn.microsoft.com/library/windows/apps/br208852)-Eigenschaft, um abgeleitete Stile zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="39602-142">You use the [BasedOn](https://msdn.microsoft.com/library/windows/apps/br208852) property to create inherited styles.</span></span> <span data-ttu-id="39602-143">Stile, die von anderen Stilen erben, müssen als Ziel denselben Steuerelementtyp haben oder ein Steuerelement, das von dem Typ abgeleitet wird, auf den der Basisstil verweist.</span><span class="sxs-lookup"><span data-stu-id="39602-143">Styles that inherit from other styles must target the same type of control or a control that derives from the type targeted by the base style.</span></span> <span data-ttu-id="39602-144">Wenn das Ziel des Basisstils z.B. [ContentControl](https://msdn.microsoft.com/library/windows/apps/br209365) ist, können die von diesem abgeleiteten Stile **ContentControl** als Ziel haben oder Typen, die von **ContentControl** abgeleitet sind, z.B. [Button](https://msdn.microsoft.com/library/windows/apps/br209265) und [ScrollViewer](https://msdn.microsoft.com/library/windows/apps/br209527).</span><span class="sxs-lookup"><span data-stu-id="39602-144">For example, if a base style targets [ContentControl](https://msdn.microsoft.com/library/windows/apps/br209365), styles that are based on this style can target **ContentControl** or types that derive from **ContentControl** such as [Button](https://msdn.microsoft.com/library/windows/apps/br209265) and [ScrollViewer](https://msdn.microsoft.com/library/windows/apps/br209527).</span></span> <span data-ttu-id="39602-145">Wenn ein Wert im abgeleiteten Stil nicht festgelegt wurde, wird er vom Basisstil vererbt.</span><span class="sxs-lookup"><span data-stu-id="39602-145">If a value is not set in the based-on style, it's inherited from the base style.</span></span> <span data-ttu-id="39602-146">Möchten Sie den Wert vom Basisstil ändern, können Sie ihn im abgeleiteten Stil überschreiben.</span><span class="sxs-lookup"><span data-stu-id="39602-146">To change a value from the base style, the based-on style overrides that value.</span></span> <span data-ttu-id="39602-147">Das nächste Beispiel zeigt einen **Button** und ein [CheckBox](https://msdn.microsoft.com/library/windows/apps/br209316) mit Stilen, die von demselben Basisstil abgeleitet sind.</span><span class="sxs-lookup"><span data-stu-id="39602-147">The next example shows a **Button** and a [CheckBox](https://msdn.microsoft.com/library/windows/apps/br209316) with styles that inherit from the same base style.</span></span>

![Formatierte Schaltflächen mit abgeleiteten Stilen](images/styles-buttons-based-on.png)

<span data-ttu-id="39602-149">Der Basisstil hat als Ziel [ContentControl](https://msdn.microsoft.com/library/windows/apps/br209365). Er legt die [Height](/uwp/api/Windows.UI.Xaml.FrameworkElement.Height)-Eigenschaft und die [Width](/uwp/api/Windows.UI.Xaml.FrameworkElement.Width)-Eigenschaft fest.</span><span class="sxs-lookup"><span data-stu-id="39602-149">The base style targets [ContentControl](https://msdn.microsoft.com/library/windows/apps/br209365), and sets the [Height](/uwp/api/Windows.UI.Xaml.FrameworkElement.Height), and [Width](/uwp/api/Windows.UI.Xaml.FrameworkElement.Width) properties.</span></span> <span data-ttu-id="39602-150">Die von diesem Stil abgeleiteten Stile haben als Ziel [CheckBox](https://msdn.microsoft.com/library/windows/apps/br209316) und [Button](https://msdn.microsoft.com/library/windows/apps/br209265), die von **ContentControl** abgeleitet sind.</span><span class="sxs-lookup"><span data-stu-id="39602-150">The styles based on this style target [CheckBox](https://msdn.microsoft.com/library/windows/apps/br209316) and [Button](https://msdn.microsoft.com/library/windows/apps/br209265), which derive from **ContentControl**.</span></span> <span data-ttu-id="39602-151">Die abgeleiteten Stile legen andere Farben für die [BorderBrush](https://msdn.microsoft.com/library/windows/apps/br209397)-Eigenschaft und die [Foreground](https://msdn.microsoft.com/library/windows/apps/br209414)-Eigenschaft fest.</span><span class="sxs-lookup"><span data-stu-id="39602-151">The based-on styles set different colors for the [BorderBrush](https://msdn.microsoft.com/library/windows/apps/br209397) and [Foreground](https://msdn.microsoft.com/library/windows/apps/br209414) properties.</span></span> <span data-ttu-id="39602-152">(Normalerweise wird eine **CheckBox** nicht mit einem Rahmen versehen.</span><span class="sxs-lookup"><span data-stu-id="39602-152">(You don't typically put a border around a **CheckBox**.</span></span> <span data-ttu-id="39602-153">Hier dient dies zur Veranschaulichung der Auswirkungen des Stils.)</span><span class="sxs-lookup"><span data-stu-id="39602-153">We do it here to show the effects of the style.)</span></span>

```XAML
<Page.Resources>
    <Style x:Key="BasicStyle" TargetType="ContentControl">
        <Setter Property="Width" Value="130" />
        <Setter Property="Height" Value="30" />
    </Style>

    <Style x:Key="ButtonStyle" TargetType="Button"
           BasedOn="{StaticResource BasicStyle}">
        <Setter Property="BorderBrush" Value="Orange" />
        <Setter Property="BorderThickness" Value="2" />
        <Setter Property="Foreground" Value="Red" />
    </Style>

    <Style x:Key="CheckBoxStyle" TargetType="CheckBox"
           BasedOn="{StaticResource BasicStyle}">
        <Setter Property="BorderBrush" Value="Blue" />
        <Setter Property="BorderThickness" Value="2" />
        <Setter Property="Foreground" Value="Green" />
    </Style>
</Page.Resources>

<StackPanel>
    <Button Content="Button" Style="{StaticResource ButtonStyle}" Margin="0,10"/>
    <CheckBox Content="CheckBox" Style="{StaticResource CheckBoxStyle}"/>
</StackPanel>
```

## <a name="use-tools-to-work-with-styles-easily"></a><span data-ttu-id="39602-154">Verwenden von Tools für die problemlose Arbeit mit Stilen</span><span class="sxs-lookup"><span data-stu-id="39602-154">Use tools to work with styles easily</span></span>

<span data-ttu-id="39602-155">Wenn Sie schnell einen Stil auf Ihr Steuerelement anwenden möchten, klicken Sie auf der Microsoft Visual Studio XAML-Entwicklungsoberfläche mit der rechten Maustaste auf das Steuerelement, und wählen Sie **Stil bearbeiten** oder **Vorlage bearbeiten** aus (je nach Steuerelement).</span><span class="sxs-lookup"><span data-stu-id="39602-155">A fast way to apply styles to your controls is to right-click on a control on the Microsoft Visual Studio XAML design surface and select **Edit Style** or **Edit Template** (depending on the control you are right-clicking on).</span></span> <span data-ttu-id="39602-156">Anschließend können Sie einen vorhandenen Stil anwenden, indem Sie **Ressource übernehmen** auswählen, oder einen neuen erstellen, indem Sie **Leer erstellen** auswählen.</span><span class="sxs-lookup"><span data-stu-id="39602-156">You can then apply an existing style by selecting **Apply Resource** or define a new style by selecting **Create Empty**.</span></span> <span data-ttu-id="39602-157">Wenn Sie einen leeren Stil erstellen, haben Sie die Möglichkeit, diesen auf der Seite, in der Datei App.xaml oder in einem eigenen Ressourcenverzeichnis zu definieren.</span><span class="sxs-lookup"><span data-stu-id="39602-157">If you create an empty style, you are given the option to define it in the page, in the App.xaml file, or in a separate resource dictionary.</span></span>

## <a name="lightweight-styling"></a><span data-ttu-id="39602-158">Einfache Formatierung</span><span class="sxs-lookup"><span data-stu-id="39602-158">Lightweight styling</span></span>

<span data-ttu-id="39602-159">Das Überschreiben der Systempinsel geschieht grundsätzlich auf App- oder Seitenebene, und in keinem Fall wirkt sich die Farbüberschreibung auf alle Steuerelemente aus, die auf diesen Pinsel verweisen – und in XAML können zahlreiche Steuerelemente auf denselben Pinsel verweisen.</span><span class="sxs-lookup"><span data-stu-id="39602-159">Overriding the system brushes is generally done at the App or Page level, and in either case the color override will affect all controls that reference that brush – and in XAML many controls can reference the same system brush.</span></span>

![Formatierte Schaltflächen](images/LightweightStyling_ButtonStatesExample.png)

```XAML
<Page.Resources>
    <ResourceDictionary>
        <ResourceDictionary.ThemeDictionaries>
            <ResourceDictionary x:Key="Light">
                 <SolidColorBrush x:Key="ButtonBackground" Color="Transparent"/>
                 <SolidColorBrush x:Key="ButtonForeground" Color="MediumSlateBlue"/>
                 <SolidColorBrush x:Key="ButtonBorderBrush" Color="MediumSlateBlue"/>
            </ResourceDictionary>
        </ResourceDictionary.ThemeDictionaries>
    </ResourceDictionary>
</Page.Resources>
```

<span data-ttu-id="39602-161">Für Zustände wie PointerOver (Mauszeiger über der Schaltfläche), **PointerPressed** (Schaltfläche betätigt) oder Deaktiviert (Schaltfläche erlaubt keine Interaktion).</span><span class="sxs-lookup"><span data-stu-id="39602-161">For states like PointerOver (mouse is hovered over the button), **PointerPressed** (button has been invoked), or Disabled (button is not interactable).</span></span> <span data-ttu-id="39602-162">Diese Endungen werden an die ursprünglichen einfachen Formatnahmen angehängt: **ButtonBackgroundPointerOver**, **ButtonForegroundPointerPressed**, **ButtonBorderBrushDisabled** usw. Wenn Sie auch diese Pinsel modifizieren, stellen Sie sicher, dass Ihre Steuerelemente konsistent gemäß dem Thema Ihrer App gestaltet sind.</span><span class="sxs-lookup"><span data-stu-id="39602-162">These endings are appended onto the original Lightweight styling names: **ButtonBackgroundPointerOver**, **ButtonForegroundPointerPressed**, **ButtonBorderBrushDisabled**, etc. Modifying those brushes as well, will make sure that your controls are colored consistently to your app's theme.</span></span>

<span data-ttu-id="39602-163">Die Verwendung dieser Pinselüberschreibungen auf der **App.Resources**-Ebene verändert alle Schaltflächen in der gesamten App und nicht nur auf einer Seite.</span><span class="sxs-lookup"><span data-stu-id="39602-163">Placing these brush overrides at the **App.Resources** level, will alter all the buttons within the entire app, instead of on a single page.</span></span>

### <a name="per-control-styling"></a><span data-ttu-id="39602-164">Formatierung pro Steuerelement</span><span class="sxs-lookup"><span data-stu-id="39602-164">Per-control styling</span></span>

<span data-ttu-id="39602-165">In anderen Fällen ist es möglicherweise erwünscht, nur ein einzelnes Steuerelement auf einer Seite in einer bestimmten Weise zu gestalten, ohne dass dies andere Versionen dieses Steuerelements betrifft:</span><span class="sxs-lookup"><span data-stu-id="39602-165">In other cases, changing a single control on one page only to look a certain way, without altering any other versions of that control, is desired:</span></span>

![Formatierte Schaltflächen](images/LightweightStyling_CheckboxExample.png)

```XAML
<CheckBox Content="Normal CheckBox" Margin="5"/>
    <CheckBox Content="Special CheckBox" Margin="5">
        <CheckBox.Resources>
            <ResourceDictionary>
                <ResourceDictionary.ThemeDictionaries>
                    <ResourceDictionary x:Key="Light">
                        <SolidColorBrush x:Key="CheckBoxForegroundUnchecked"
                            Color="Purple"/>
                        <SolidColorBrush x:Key="CheckBoxForegroundChecked"
                            Color="Purple"/>
                        <SolidColorBrush x:Key="CheckBoxCheckGlyphForegroundChecked"
                            Color="White"/>
                        <SolidColorBrush x:Key="CheckBoxCheckBackgroundStrokeChecked"  
                            Color="Purple"/>
                        <SolidColorBrush x:Key="CheckBoxCheckBackgroundFillChecked"
                            Color="Purple"/>
                    </ResourceDictionary>
                </ResourceDictionary.ThemeDictionaries>
            </ResourceDictionary>
        </CheckBox.Resources>
    </CheckBox>
<CheckBox Content="Normal CheckBox" Margin="5"/>
```

<span data-ttu-id="39602-167">Dies betrifft nur das eine „besondere Kontrollkästchen“ (Special CheckBox) auf der Seite, auf der dieses Steuerelement vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="39602-167">This would only effect that one “Special CheckBox” on the page where that control existed.</span></span>

## <a name="modify-the-default-system-styles"></a><span data-ttu-id="39602-168">Ändern der standardmäßigen Systemstile</span><span class="sxs-lookup"><span data-stu-id="39602-168">Modify the default system styles</span></span>

<span data-ttu-id="39602-169">Verwenden Sie nach Möglichkeit die Stile der standardmäßigen Windows-Runtime-XAML-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="39602-169">You should use the styles that come from the Windows Runtime default XAML resources when you can.</span></span> <span data-ttu-id="39602-170">Wenn Sie eigene Formatierungen definieren müssen, leiten Sie Ihre Stile am besten von diesen Standardstilen ab (indem Sie, wie zuvor erläutert, abgeleitete Stile verwenden oder eine Kopie des Originalstandardstils bearbeiten).</span><span class="sxs-lookup"><span data-stu-id="39602-170">When you have to define your own styles, try to base your styles on the default ones when possible (using based-on styles as explained earlier, or start by editing a copy of the original default style).</span></span>

## <a name="the-template-property"></a><span data-ttu-id="39602-171">Die Eigenschaft eines Templates</span><span class="sxs-lookup"><span data-stu-id="39602-171">The template property</span></span>

<span data-ttu-id="39602-172">Für die [Template](https://msdn.microsoft.com/library/windows/apps/br209465)-Eigenschaft eines [Control](https://msdn.microsoft.com/library/windows/apps/br209390)-Elements kann ein Stilsetter verwendet werden. Dieser erstellt letztendlich den größten Teil eines typischen XAML-Stils und der XAML-Ressourcen einer App.</span><span class="sxs-lookup"><span data-stu-id="39602-172">A style setter can be used for the [Template](https://msdn.microsoft.com/library/windows/apps/br209465) property of a [Control](https://msdn.microsoft.com/library/windows/apps/br209390), and in fact this makes up the majority of a typical XAML style and an app's XAML resources.</span></span> <span data-ttu-id="39602-173">Eine ausführlichere Beschreibung finden Sie im Thema [Steuerelementvorlagen](control-templates.md).</span><span class="sxs-lookup"><span data-stu-id="39602-173">This is discussed in more detail in the topic [Control templates](control-templates.md).</span></span>
