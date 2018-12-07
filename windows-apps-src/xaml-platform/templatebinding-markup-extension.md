---
description: Verknüpft den Wert einer Eigenschaft in einer Steuerelementvorlage mit dem Wert einer anderen Eigenschaft, die im Steuerelement mit Vorlagen verfügbar gemacht wird. TemplateBinding kann nur in einer ControlTemplate-Definition in XAML verwendet werden.
title: TemplateBinding-Markuperweiterung
ms.assetid: FDE71086-9D42-4287-89ED-8FBFCDF169DC
ms.date: 10/29/2018
ms.topic: article
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 9ade10b4d5e2653eb214d93c2c9166e6a3e3defc
ms.sourcegitcommit: a3dc929858415b933943bba5aa7487ffa721899f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "8795684"
---
# <a name="templatebinding-markup-extension"></a><span data-ttu-id="cd864-105">{TemplateBinding}-Markuperweiterung</span><span class="sxs-lookup"><span data-stu-id="cd864-105">{TemplateBinding} markup extension</span></span>

<span data-ttu-id="cd864-106">Verknüpft den Wert einer Eigenschaft in einer Steuerelementvorlage mit dem Wert einer anderen Eigenschaft, die im Steuerelement mit Vorlagen verfügbar gemacht wird.</span><span class="sxs-lookup"><span data-stu-id="cd864-106">Links the value of a property in a control template to the value of some other exposed property on the templated control.</span></span> <span data-ttu-id="cd864-107">**TemplateBinding** kann nur in einer [**ControlTemplate**](https://msdn.microsoft.com/library/windows/apps/br209391)-Definition in XAML verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="cd864-107">**TemplateBinding** can only be used within a [**ControlTemplate**](https://msdn.microsoft.com/library/windows/apps/br209391) definition in XAML.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="cd864-108">XAML-Attributsyntax</span><span class="sxs-lookup"><span data-stu-id="cd864-108">XAML attribute usage</span></span>

``` syntax
<object propertyName="{TemplateBinding sourceProperty}" .../>
```

## <a name="xaml-attribute-usage-for-setter-property-in-template-or-style"></a><span data-ttu-id="cd864-109">XAML-Attributsyntax (für die Setter-Eigenschaft in einer Vorlage oder Formatvorlage)</span><span class="sxs-lookup"><span data-stu-id="cd864-109">XAML attribute usage (for Setter property in template or style)</span></span>

``` syntax
<Setter Property="propertyName" Value="{TemplateBinding sourceProperty}" .../>
```

## <a name="xaml-values"></a><span data-ttu-id="cd864-110">XAML-Werte</span><span class="sxs-lookup"><span data-stu-id="cd864-110">XAML values</span></span>

| <span data-ttu-id="cd864-111">Benennung</span><span class="sxs-lookup"><span data-stu-id="cd864-111">Term</span></span> | <span data-ttu-id="cd864-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="cd864-112">Description</span></span> |
|------|-------------|
| <span data-ttu-id="cd864-113">propertyName</span><span class="sxs-lookup"><span data-stu-id="cd864-113">propertyName</span></span> | <span data-ttu-id="cd864-114">Der Name der Eigenschaft, die in der Setter-Syntax festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="cd864-114">The name of the property being set in the setter syntax.</span></span> <span data-ttu-id="cd864-115">Diese Eigenschaft muss eine Abhängigkeitseigenschaft sein.</span><span class="sxs-lookup"><span data-stu-id="cd864-115">This must be a dependency property.</span></span> |
| <span data-ttu-id="cd864-116">sourceProperty</span><span class="sxs-lookup"><span data-stu-id="cd864-116">sourceProperty</span></span> | <span data-ttu-id="cd864-117">Der Name einer anderen Abhängigkeitseigenschaft, die für den als Vorlage festgelegten Typ vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="cd864-117">The name of another dependency property that exists on the type being templated.</span></span> |

## <a name="remarks"></a><span data-ttu-id="cd864-118">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="cd864-118">Remarks</span></span>

<span data-ttu-id="cd864-119">Die Verwendung von **TemplateBinding** ist ein grundlegender Punkt beim Definieren einer Steuerelementvorlage, wenn Sie entweder ein Autor von benutzerdefinierten Steuerelementen sind oder eine Steuerelementvorlage für vorhandene Steuerelemente ersetzen.</span><span class="sxs-lookup"><span data-stu-id="cd864-119">Using **TemplateBinding** is a fundamental part of how you define a control template, either if you are a custom control author or if you are replacing a control template for existing controls.</span></span> <span data-ttu-id="cd864-120">Weitere Informationen finden Sie unter [Schnellstart: Steuerelementvorlagen](https://msdn.microsoft.com/library/windows/apps/xaml/hh465374).</span><span class="sxs-lookup"><span data-stu-id="cd864-120">For more info, see [Quickstart: Control templates](https://msdn.microsoft.com/library/windows/apps/xaml/hh465374).</span></span>

<span data-ttu-id="cd864-121">Für *propertyName* und *targetProperty* wird häufig derselbe Eigenschaftsname verwendet.</span><span class="sxs-lookup"><span data-stu-id="cd864-121">It's fairly common for *propertyName* and *targetProperty* to use the same property name.</span></span> <span data-ttu-id="cd864-122">In diesem Fall kann ein Steuerelement eine Eigenschaft für sich selbst definieren und diese an eine vorhandene, intuitiv benannte Eigenschaft eines seiner Komponententeile weiterleiten.</span><span class="sxs-lookup"><span data-stu-id="cd864-122">In this case, a control might define a property on itself and forward the property to an existing and intuitively named property of one of its component parts.</span></span> <span data-ttu-id="cd864-123">Ein Steuerelement, dessen Zusammensetzung einen zum Anzeigen seiner **Text**-Eigenschaft verwendeten [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652) enthält, kann beispielsweise diesen XAML-Code als Teil der Steuerelementvorlage enthalten:</span><span class="sxs-lookup"><span data-stu-id="cd864-123">For example, a control that incorporates a [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652) in its compositing, which is used to display the control's own **Text** property, might include this XAML as a part in the control template:</span></span> `<TextBlock Text="{TemplateBinding Text}" .... />`

<span data-ttu-id="cd864-124">Die Typen, die als Wert für die Quelleigenschaft und die Zieleigenschaft verwendet werden, müssen übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="cd864-124">The types used as the value for the source property and the target property must match.</span></span> <span data-ttu-id="cd864-125">Bei Verwendung von **TemplateBinding** gibt es keine Möglichkeit, einen Konverter zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="cd864-125">There's no opportunity to introduce a converter when you're using **TemplateBinding**.</span></span> <span data-ttu-id="cd864-126">Falls die Werte nicht übereinstimmen, tritt beim Analysieren des XAML-Codes ein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="cd864-126">Failing to match values results in an error when parsing the XAML.</span></span> <span data-ttu-id="cd864-127">Wenn Sie einen Konverter benötigen, können Sie die ausführliche Syntax für eine Vorlagenbindung verwenden, z.B.: </span><span class="sxs-lookup"><span data-stu-id="cd864-127">If you need a converter you can use the verbose syntax for a template binding such as:</span></span> `{Binding RelativeSource={RelativeSource TemplatedParent}, Converter="..." ...}`

<span data-ttu-id="cd864-128">Wenn Sie versuchen, eine **TemplateBinding** außerhalb einer [**ControlTemplate**](https://msdn.microsoft.com/library/windows/apps/br209391)-Definition in XAML zu verwenden, führt dies zu einem Parserfehler.</span><span class="sxs-lookup"><span data-stu-id="cd864-128">Attempting to use a **TemplateBinding** outside of a [**ControlTemplate**](https://msdn.microsoft.com/library/windows/apps/br209391) definition in XAML will result in a parser error.</span></span>

<span data-ttu-id="cd864-129">Sie können **TemplateBinding** für Fälle verwenden, in denen der übergeordnete Wert mit Vorlagen auch als weitere Bindung zurückgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="cd864-129">You can use **TemplateBinding** for cases where the templated parent value is also deferred as another binding.</span></span> <span data-ttu-id="cd864-130">Die Auswertung für **TemplateBinding** kann warten, bis etwaige erforderliche Laufzeitbindungen über Werte verfügen.</span><span class="sxs-lookup"><span data-stu-id="cd864-130">The evaluation for **TemplateBinding** can wait until any required runtime bindings have values.</span></span>

<span data-ttu-id="cd864-131">Ein **TemplateBinding**-Element ist stets eine unidirektionale Bindung.</span><span class="sxs-lookup"><span data-stu-id="cd864-131">A **TemplateBinding** is always a one-way binding.</span></span> <span data-ttu-id="cd864-132">Bei beiden beteiligten Eigenschaften muss es sich um Abhängigkeitseigenschaften handeln.</span><span class="sxs-lookup"><span data-stu-id="cd864-132">Both properties involved must be dependency properties.</span></span>

<span data-ttu-id="cd864-133">**TemplateBinding** ist eine Markuperweiterung.</span><span class="sxs-lookup"><span data-stu-id="cd864-133">**TemplateBinding** is a markup extension.</span></span> <span data-ttu-id="cd864-134">Markuperweiterungen werden in der Regel implementiert, wenn für Attributwerte Escapezeichen verwendet werden müssen, damit sie keine Literalwerte oder Handlernamen darstellen, und es nicht ausreicht, Typkonverter für bestimmte Typen oder Eigenschaften zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="cd864-134">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="cd864-135">Alle Markuperweiterungen in XAML verwenden die Zeichen „{” und „}” in ihrer Attributsyntax. Anhand dieser Konvention erkennt ein XAML-Prozessor, dass eine Markuperweiterung das Attribut verarbeiten muss.</span><span class="sxs-lookup"><span data-stu-id="cd864-135">All markup extensions in XAML use the "{" and "}" characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute.</span></span>

<span data-ttu-id="cd864-136">**Hinweis:** In der Windows-Runtime-XAML-prozessorimplementierung, es gibt keine sicherungsklassendarstellung für **TemplateBinding**.</span><span class="sxs-lookup"><span data-stu-id="cd864-136">**Note**In the Windows Runtime XAML processor implementation, there is no backing class representation for **TemplateBinding**.</span></span> <span data-ttu-id="cd864-137">**TemplateBinding** ist ausschließlich für die Verwendung im XAML-Markup vorgesehen.</span><span class="sxs-lookup"><span data-stu-id="cd864-137">**TemplateBinding** is exclusively for use in XAML markup.</span></span> <span data-ttu-id="cd864-138">Es gibt keine einfache Methode zum Reproduzieren des Verhaltens im Code.</span><span class="sxs-lookup"><span data-stu-id="cd864-138">There isn't a straightforward way to reproduce the behavior in code.</span></span>

### <a name="xbind-in-controltemplate"></a><span data-ttu-id="cd864-139">X: Bind in ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="cd864-139">x:Bind in ControlTemplate</span></span>

> [!NOTE]
> <span data-ttu-id="cd864-140">X: Bind in einer ControlTemplate muss Windows 10, Version 1809 ([SDK 17763](https://developer.microsoft.com/windows/downloads/windows-10-sdk)) oder höher.</span><span class="sxs-lookup"><span data-stu-id="cd864-140">Using x:Bind in a ControlTemplate requires Windows 10, version 1809 ([SDK 17763](https://developer.microsoft.com/windows/downloads/windows-10-sdk)) or later.</span></span> <span data-ttu-id="cd864-141">Weitere Informationen zu Zielversionen finden Sie unter [Versionsadaptiver Code](https://msdn.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code).</span><span class="sxs-lookup"><span data-stu-id="cd864-141">For more info about target versions, see [Version adaptive code](https://msdn.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code).</span></span>

<span data-ttu-id="cd864-142">Ab Windows 10, Version 1809, können Sie die **X: Bind** -Markuperweiterung an einer beliebigen Stelle Sie **TemplateBinding** in einer [**ControlTemplate**](https://msdn.microsoft.com/library/windows/apps/br209391)verwenden.</span><span class="sxs-lookup"><span data-stu-id="cd864-142">Starting with Windows 10, version 1809, you can use the **x:Bind** markup extension anywhere you use **TemplateBinding** in a [**ControlTemplate**](https://msdn.microsoft.com/library/windows/apps/br209391).</span></span> 

<span data-ttu-id="cd864-143">Die [TargetType](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.controltemplate.targettype) -Eigenschaft ist erforderlich (nicht optional) auf [ControlTemplate](https://msdn.microsoft.com/library/windows/apps/br209391) bei Verwendung von **X: Bind**.</span><span class="sxs-lookup"><span data-stu-id="cd864-143">The [TargetType](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.controltemplate.targettype) property is required (not optional) on [ControlTemplate](https://msdn.microsoft.com/library/windows/apps/br209391) when using **x:Bind**.</span></span>

<span data-ttu-id="cd864-144">Mit der Unterstützung von **X: Bind** können Sie beide [Funktion Bindungen](../data-binding/function-bindings.md) als auch als bidirektionale Bindungen in einer [ControlTemplate](https://msdn.microsoft.com/library/windows/apps/br209391)verwenden.</span><span class="sxs-lookup"><span data-stu-id="cd864-144">With **x:Bind** support, you can use both [Function bindings](../data-binding/function-bindings.md) as well as two-way bindings in a [ControlTemplate](https://msdn.microsoft.com/library/windows/apps/br209391).</span></span>

<span data-ttu-id="cd864-145">In diesem Beispiel ergibt die Eigenschaft **TextBlock.Text** **Button.Content.ToString**.</span><span class="sxs-lookup"><span data-stu-id="cd864-145">In this example, the **TextBlock.Text** property evaluates to **Button.Content.ToString**.</span></span> <span data-ttu-id="cd864-146">TargetType auf das ControlTemplate-Element dient als Datenquelle und führt zum gleiche Ergebnis wie TemplateBinding übergeordneten Element.</span><span class="sxs-lookup"><span data-stu-id="cd864-146">The TargetType on the ControlTemplate acts as the data source and accomplishes the same result as a TemplateBinding to parent.</span></span>

```xaml
<ControlTemplate TargetType="Button">
    <Grid>
        <TextBlock Text="{x:Bind Content, Mode=OneWay}"/>
    </Grid>
</ControlTemplate>
```

## <a name="related-topics"></a><span data-ttu-id="cd864-147">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="cd864-147">Related topics</span></span>

* [<span data-ttu-id="cd864-148">Schnellstart: Steuerelementvorlagen</span><span class="sxs-lookup"><span data-stu-id="cd864-148">Quickstart: Control templates</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/hh465374)
* [<span data-ttu-id="cd864-149">Datenbindung im Detail</span><span class="sxs-lookup"><span data-stu-id="cd864-149">Data binding in depth</span></span>](https://msdn.microsoft.com/library/windows/apps/mt210946)
* [**<span data-ttu-id="cd864-150">ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="cd864-150">ControlTemplate</span></span>**](https://msdn.microsoft.com/library/windows/apps/br209391)
* [<span data-ttu-id="cd864-151">Übersicht über XAML</span><span class="sxs-lookup"><span data-stu-id="cd864-151">XAML overview</span></span>](xaml-overview.md)
* [<span data-ttu-id="cd864-152">Übersicht über Abhängigkeitseigenschaften</span><span class="sxs-lookup"><span data-stu-id="cd864-152">Dependency properties overview</span></span>](dependency-properties-overview.md)
 

