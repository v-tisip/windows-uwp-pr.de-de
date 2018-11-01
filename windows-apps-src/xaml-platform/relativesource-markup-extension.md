---
author: jwmsft
description: Stellt eine Methode bereit, um die Quelle einer Bindung als relative Beziehung im Laufzeitobjektdiagramm anzugeben.
title: RelativeSource-Markuperweiterung
ms.assetid: B87DEF36-BE1F-4C16-B32E-7A896BD09272
ms.author: jimwalk
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 5bb9d241569afdbbc9df95fa11cd2261e78c077a
ms.sourcegitcommit: cd00bb829306871e5103db481cf224ea7fb613f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5872101"
---
# <a name="relativesource-markup-extension"></a><span data-ttu-id="b4a1d-104">{RelativeSource}-Markuperweiterung</span><span class="sxs-lookup"><span data-stu-id="b4a1d-104">{RelativeSource} markup extension</span></span>


<span data-ttu-id="b4a1d-105">Stellt eine Methode bereit, um die Quelle einer Bindung als relative Beziehung im Laufzeitobjektdiagramm anzugeben.</span><span class="sxs-lookup"><span data-stu-id="b4a1d-105">Provides a means to specify the source of a binding in terms of a relative relationship in the run-time object graph.</span></span>

## <a name="xaml-attribute-usage-self-mode"></a><span data-ttu-id="b4a1d-106">Verwendung von XAML-Attributen (Self-Modus)</span><span class="sxs-lookup"><span data-stu-id="b4a1d-106">XAML attribute usage (Self mode)</span></span>

``` syntax
<Binding RelativeSource="{RelativeSource Self}" .../>
-or-
<object property="{Binding RelativeSource={RelativeSource Self} ...}" .../>
```

## <a name="xaml-attribute-usage-templatedparent-mode"></a><span data-ttu-id="b4a1d-107">Verwendung von XAML-Attributen (TemplatedParent-Modus)</span><span class="sxs-lookup"><span data-stu-id="b4a1d-107">XAML attribute usage (TemplatedParent mode)</span></span>

``` syntax
<Binding RelativeSource="{RelativeSource TemplatedParent}" .../>
-or-
<object property="{Binding RelativeSource={RelativeSource TemplatedParent} ...}" .../>
```

## <a name="xaml-values"></a><span data-ttu-id="b4a1d-108">XAML-Werte</span><span class="sxs-lookup"><span data-stu-id="b4a1d-108">XAML values</span></span>

| <span data-ttu-id="b4a1d-109">Benennung</span><span class="sxs-lookup"><span data-stu-id="b4a1d-109">Term</span></span> | <span data-ttu-id="b4a1d-110">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b4a1d-110">Description</span></span> |
|------|-------------|
| <span data-ttu-id="b4a1d-111">{RelativeSource Self}</span><span class="sxs-lookup"><span data-stu-id="b4a1d-111">{RelativeSource Self}</span></span> | <span data-ttu-id="b4a1d-112">Erzeugt den [<strong>Mode</strong>](https://msdn.microsoft.com/library/windows/apps/br209915)-Wert <strong>Self</strong>.</span><span class="sxs-lookup"><span data-stu-id="b4a1d-112">Produces a [<strong>Mode</strong>](https://msdn.microsoft.com/library/windows/apps/br209915) value of <strong>Self</strong>.</span></span> <span data-ttu-id="b4a1d-113">Das Zielelement sollte als Quelle für diese Bindung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="b4a1d-113">The target element should be used as the source for this binding.</span></span> <span data-ttu-id="b4a1d-114">Dies ist nützlich, wenn eine Eigenschaft eines Elements an eine andere Eigenschaft im gleichen Element gebunden werden soll.</span><span class="sxs-lookup"><span data-stu-id="b4a1d-114">This is useful for binding one property of an element to another property on the same element.</span></span> |
| <span data-ttu-id="b4a1d-115">{RelativeSource TemplatedParent}</span><span class="sxs-lookup"><span data-stu-id="b4a1d-115">{RelativeSource TemplatedParent}</span></span> | <span data-ttu-id="b4a1d-116">Erzeugt eine [<strong>ControlTemplate</strong>](https://msdn.microsoft.com/library/windows/apps/br209391), die als Quelle für diese Bindung angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="b4a1d-116">Produces a [<strong>ControlTemplate</strong>](https://msdn.microsoft.com/library/windows/apps/br209391) that is applied as the source for this binding.</span></span> <span data-ttu-id="b4a1d-117">Dies ist nützlich, wenn Laufzeitinformationen in Bindungen auf Vorlagenebene angewendet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="b4a1d-117">This is useful for applying runtime information to bindings at the template level.</span></span> | 

## <a name="remarks"></a><span data-ttu-id="b4a1d-118">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="b4a1d-118">Remarks</span></span>

<span data-ttu-id="b4a1d-119">Mit einer [**Bindung**](https://msdn.microsoft.com/library/windows/apps/br209820) kann [**Binding.RelativeSource**](https://msdn.microsoft.com/library/windows/apps/br209831) entweder als Attribut für ein **Binding**-Objektelement oder als Komponente in einer [{Binding}-Markuperweiterung](binding-markup-extension.md) festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="b4a1d-119">A [**Binding**](https://msdn.microsoft.com/library/windows/apps/br209820) can set [**Binding.RelativeSource**](https://msdn.microsoft.com/library/windows/apps/br209831) either as an attribute on a **Binding** object element or as a component within a [{Binding} markup extension](binding-markup-extension.md).</span></span> <span data-ttu-id="b4a1d-120">Aus diesem Grund werden zwei verschiedene Varianten der XAML-Syntax dargestellt.</span><span class="sxs-lookup"><span data-stu-id="b4a1d-120">This is why two different XAML syntaxes are shown.</span></span>

<span data-ttu-id="b4a1d-121">**RelativeSource** ist ähnlich der [{Binding}-Markuperweiterung](binding-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="b4a1d-121">**RelativeSource** is similar to [{Binding} markup extension](binding-markup-extension.md).</span></span>  <span data-ttu-id="b4a1d-122">Hierbei handelt es sich um eine Markuperweiterung, die Instanzen selbstständig zurückgeben kann und die eine zeichenfolgenbasierte Konstruktion unterstützt, die im Wesentlichen ein Argument an den Konstruktor übergibt.</span><span class="sxs-lookup"><span data-stu-id="b4a1d-122">It is a markup extension that is capable of returning instances of itself, and supporting a string-based construction that essentially passes an argument to the constructor.</span></span> <span data-ttu-id="b4a1d-123">In diesem Fall ist das Argument, das übergeben wird, der [**Mode**](https://msdn.microsoft.com/library/windows/apps/br209915)-Wert.</span><span class="sxs-lookup"><span data-stu-id="b4a1d-123">In this case, the argument being passed is the [**Mode**](https://msdn.microsoft.com/library/windows/apps/br209915) value.</span></span>

<span data-ttu-id="b4a1d-124">Der **Self**-Modus ist nützlich, wenn eine Eigenschaft eines Elements an eine andere Eigenschaft im gleichen Element gebunden werden soll. Dies stellt außerdem eine Variation der [**ElementName**](https://msdn.microsoft.com/library/windows/apps/br209828)-Bindung dar, erfordert aber keine Benennung und keinen anschließenden Selbstverweis des Elements.</span><span class="sxs-lookup"><span data-stu-id="b4a1d-124">The **Self** mode is useful for binding one property of an element to another property on the same element, and is a variation on [**ElementName**](https://msdn.microsoft.com/library/windows/apps/br209828) binding but does not require naming and then self-referencing the element.</span></span> <span data-ttu-id="b4a1d-125">Wenn Sie eine Eigenschaft eines Elements an eine andere Eigenschaft im gleichen Element binden, müssen die Eigenschaften den gleichen Eigenschaftentyp ausweisen. Andernfalls müssen Sie auch einen [**Converter**](https://msdn.microsoft.com/library/windows/apps/br209826) für die Bindung verwenden, um die Werte zu konvertieren.</span><span class="sxs-lookup"><span data-stu-id="b4a1d-125">If you bind one property of an element to another property on the same element, either the properties must use the same property type, or you must also use a [**Converter**](https://msdn.microsoft.com/library/windows/apps/br209826) on the binding to convert the values.</span></span> <span data-ttu-id="b4a1d-126">Sie können beispielsweise [**Height**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Height) als Quelle für [**Width**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Width) ohne Konvertierung verwenden. Sie benötigen jedoch einen Konverter, um [**IsEnabled**](https://msdn.microsoft.com/library/windows/apps/br209419) als Quelle für [**Visibility**](https://msdn.microsoft.com/library/windows/apps/br209006) zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="b4a1d-126">For example, you could use [**Height**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Height) as a source for [**Width**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Width) without conversion, but you'd need a converter to use [**IsEnabled**](https://msdn.microsoft.com/library/windows/apps/br209419) as a source for [**Visibility**](https://msdn.microsoft.com/library/windows/apps/br209006).</span></span>

<span data-ttu-id="b4a1d-127">Im Folgenden finden Sie ein Beispiel hierfür.</span><span class="sxs-lookup"><span data-stu-id="b4a1d-127">Here's an example.</span></span> <span data-ttu-id="b4a1d-128">Dieses [**Rechteck**](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle) verwendet eine [{Binding}-Markuperweiterung](binding-markup-extension.md), damit [**Height**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Height) und [**Width**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Width) immer gleich sind und eine Darstellung als Quadrat erfolgt.</span><span class="sxs-lookup"><span data-stu-id="b4a1d-128">This [**Rectangle**](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle) uses a [{Binding} markup extension](binding-markup-extension.md) so that its [**Height**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Height) and [**Width**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Width) are always equal and it renders as a square.</span></span> <span data-ttu-id="b4a1d-129">Nur die Höhe wird als fester Wert festgelegt.</span><span class="sxs-lookup"><span data-stu-id="b4a1d-129">Only the Height is set as a fixed value.</span></span> <span data-ttu-id="b4a1d-130">Der standardmäßige [**DataContext**](https://msdn.microsoft.com/library/windows/apps/br208713) dieses **Rechtecks** ist **null** anstelle von **this**.</span><span class="sxs-lookup"><span data-stu-id="b4a1d-130">For this **Rectangle** its default [**DataContext**](https://msdn.microsoft.com/library/windows/apps/br208713) is **null**, not **this**.</span></span> <span data-ttu-id="b4a1d-131">Daher verwenden wir das `RelativeSource={RelativeSource Self}`-Argument in der Syntax der {Binding}-Markuperweiterung, um die Datenkontextquelle auf das eigentliche Objekt festzulegen (und die Bindung an ihre anderen Eigenschaften zu ermöglichen).</span><span class="sxs-lookup"><span data-stu-id="b4a1d-131">So to establish the data context source to be the object itself (and enable binding to its other properties) we use the `RelativeSource={RelativeSource Self}` argument in the {Binding} markup extension usage.</span></span>

```XML
<Rectangle
  Fill="Orange" Width="200"
  Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}"
/>
```

<span data-ttu-id="b4a1d-132">Darüber hinaus kann `RelativeSource={RelativeSource Self}` auch verwendet werden, um den [**DataContext**](https://msdn.microsoft.com/library/windows/apps/br208713) eines Objekts auf sich selbst festzulegen.</span><span class="sxs-lookup"><span data-stu-id="b4a1d-132">Another use of `RelativeSource={RelativeSource Self}` is as a way to set an object's [**DataContext**](https://msdn.microsoft.com/library/windows/apps/br208713) to itself.</span></span>  <span data-ttu-id="b4a1d-133">Dieses Verfahren kommt etwa in einigen der SDK-Beispiele zum Einsatz, bei denen die [**Page**](https://msdn.microsoft.com/library/windows/apps/br227503)-Klasse mit einer benutzerdefinierten Eigenschaft erweitert wurde, die bereits ein verwendungsbereites Modell für die eigene Datenbindung bereitstellt. Beispiel:</span><span class="sxs-lookup"><span data-stu-id="b4a1d-133">For example, you may see this technique in some of the SDK examples where the [**Page**](https://msdn.microsoft.com/library/windows/apps/br227503) class has been extended with a custom property that's already providing a ready-to-go view model for its own data binding such as:</span></span> `<common:LayoutAwarePage ... DataContext="{Binding DefaultViewModel, RelativeSource={RelativeSource Self}}">`

<span data-ttu-id="b4a1d-134">**Hinweis:** die Verwendung von **RelativeSource** zeigt nur die Verwendung, für die es bestimmt ist: Festlegen eines Werts für [**Binding.RelativeSource**](https://msdn.microsoft.com/library/windows/apps/br209831) in XAML als Teil eines Bindungsausdrucks.</span><span class="sxs-lookup"><span data-stu-id="b4a1d-134">**Note**The XAML usage for **RelativeSource** shows only the usage for which it is intended: setting a value for [**Binding.RelativeSource**](https://msdn.microsoft.com/library/windows/apps/br209831) in XAML as part of a binding expression.</span></span> <span data-ttu-id="b4a1d-135">Theoretisch sind andere Verwendungen möglich, wenn Sie eine Eigenschaft mit einem [**RelativeSource**](https://msdn.microsoft.com/library/windows/apps/br209913)-Wert festlegen.</span><span class="sxs-lookup"><span data-stu-id="b4a1d-135">Theoretically, other usages are possible if setting a property where the value is [**RelativeSource**](https://msdn.microsoft.com/library/windows/apps/br209913).</span></span>

## <a name="related-topics"></a><span data-ttu-id="b4a1d-136">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="b4a1d-136">Related topics</span></span>

* [<span data-ttu-id="b4a1d-137">Übersicht über XAML</span><span class="sxs-lookup"><span data-stu-id="b4a1d-137">XAML overview</span></span>](xaml-overview.md)
* [<span data-ttu-id="b4a1d-138">Datenbindung im Detail</span><span class="sxs-lookup"><span data-stu-id="b4a1d-138">Data binding in depth</span></span>](https://msdn.microsoft.com/library/windows/apps/mt210946)
* [<span data-ttu-id="b4a1d-139">{Binding}-Markuperweiterung</span><span class="sxs-lookup"><span data-stu-id="b4a1d-139">{Binding} markup extension</span></span>](binding-markup-extension.md)
* [**<span data-ttu-id="b4a1d-140">Bindung</span><span class="sxs-lookup"><span data-stu-id="b4a1d-140">Binding</span></span>**](https://msdn.microsoft.com/library/windows/apps/br209820)
* [**<span data-ttu-id="b4a1d-141">RelativeSource</span><span class="sxs-lookup"><span data-stu-id="b4a1d-141">RelativeSource</span></span>**](https://msdn.microsoft.com/library/windows/apps/br209913)

