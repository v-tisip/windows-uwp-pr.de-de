---
author: jwmsft
description: Verknüpft den Wert einer Eigenschaft in einer Steuerelementvorlage mit dem Wert einer anderen Eigenschaft, die im Steuerelement mit Vorlagen verfügbar gemacht wird. TemplateBinding kann nur in einer ControlTemplate-Definition in XAML verwendet werden.
title: TemplateBinding-Markuperweiterung
ms.assetid: FDE71086-9D42-4287-89ED-8FBFCDF169DC
ms.author: jimwalk
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.openlocfilehash: ca551ff53a0a91b5bc60263b6e282b95c32bf976
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
ms.translationtype: MT
ms.contentlocale: de-DE
ms.locfileid: "235016"
---
# <a name="templatebinding-markup-extension"></a><span data-ttu-id="309cf-105">{TemplateBinding}-Markuperweiterung</span><span class="sxs-lookup"><span data-stu-id="309cf-105">{TemplateBinding} markup extension</span></span>

<span data-ttu-id="309cf-106">\[ Aktualisiert für UWP-Apps unter Windows 10.</span><span class="sxs-lookup"><span data-stu-id="309cf-106">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="309cf-107">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span><span class="sxs-lookup"><span data-stu-id="309cf-107">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>

<span data-ttu-id="309cf-108">Verknüpft den Wert einer Eigenschaft in einer Steuerelementvorlage mit dem Wert einer anderen Eigenschaft, die im Steuerelement mit Vorlagen verfügbar gemacht wird.</span><span class="sxs-lookup"><span data-stu-id="309cf-108">Links the value of a property in a control template to the value of some other exposed property on the templated control.</span></span> <span data-ttu-id="309cf-109">**TemplateBinding** kann nur in einer [**ControlTemplate**](https://msdn.microsoft.com/library/windows/apps/br209391)-Definition in XAML verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="309cf-109">**TemplateBinding** can only be used within a [**ControlTemplate**](https://msdn.microsoft.com/library/windows/apps/br209391) definition in XAML.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="309cf-110">XAML-Attributsyntax</span><span class="sxs-lookup"><span data-stu-id="309cf-110">XAML attribute usage</span></span>

``` syntax
<object propertyName="{TemplateBinding sourceProperty}" .../>
```

## <a name="xaml-attribute-usage-for-setter-property-in-template-or-style"></a><span data-ttu-id="309cf-111">XAML-Attributsyntax (für die Setter-Eigenschaft in einer Vorlage oder Formatvorlage)</span><span class="sxs-lookup"><span data-stu-id="309cf-111">XAML attribute usage (for Setter property in template or style)</span></span>

``` syntax
<Setter Property="propertyName" Value="{TemplateBinding sourceProperty}" .../>
```

## <a name="xaml-values"></a><span data-ttu-id="309cf-112">XAML-Werte</span><span class="sxs-lookup"><span data-stu-id="309cf-112">XAML values</span></span>

| <span data-ttu-id="309cf-113">Benennung</span><span class="sxs-lookup"><span data-stu-id="309cf-113">Term</span></span> | <span data-ttu-id="309cf-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="309cf-114">Description</span></span> |
|------|-------------|
| <span data-ttu-id="309cf-115">propertyName</span><span class="sxs-lookup"><span data-stu-id="309cf-115">propertyName</span></span> | <span data-ttu-id="309cf-116">Der Name der Eigenschaft, die in der Setter-Syntax festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="309cf-116">The name of the property being set in the setter syntax.</span></span> <span data-ttu-id="309cf-117">Diese Eigenschaft muss eine Abhängigkeitseigenschaft sein.</span><span class="sxs-lookup"><span data-stu-id="309cf-117">This must be a dependency property.</span></span> |
| <span data-ttu-id="309cf-118">sourceProperty</span><span class="sxs-lookup"><span data-stu-id="309cf-118">sourceProperty</span></span> | <span data-ttu-id="309cf-119">Der Name einer anderen Abhängigkeitseigenschaft, die für den als Vorlage festgelegten Typ vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="309cf-119">The name of another dependency property that exists on the type being templated.</span></span> |

## <a name="remarks"></a><span data-ttu-id="309cf-120">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="309cf-120">Remarks</span></span>

<span data-ttu-id="309cf-121">Die Verwendung von **TemplateBinding** ist ein grundlegender Punkt beim Definieren einer Steuerelementvorlage, wenn Sie entweder ein Autor von benutzerdefinierten Steuerelementen sind oder eine Steuerelementvorlage für vorhandene Steuerelemente ersetzen.</span><span class="sxs-lookup"><span data-stu-id="309cf-121">Using **TemplateBinding** is a fundamental part of how you define a control template, either if you are a custom control author or if you are replacing a control template for existing controls.</span></span> <span data-ttu-id="309cf-122">Weitere Informationen finden Sie unter [Schnellstart: Steuerelementvorlagen](https://msdn.microsoft.com/library/windows/apps/xaml/hh465374).</span><span class="sxs-lookup"><span data-stu-id="309cf-122">For more info, see [Quickstart: Control templates](https://msdn.microsoft.com/library/windows/apps/xaml/hh465374).</span></span>

<span data-ttu-id="309cf-123">Für *propertyName* und *targetProperty* wird häufig derselbe Eigenschaftsname verwendet.</span><span class="sxs-lookup"><span data-stu-id="309cf-123">It's fairly common for *propertyName* and *targetProperty* to use the same property name.</span></span> <span data-ttu-id="309cf-124">In diesem Fall kann ein Steuerelement eine Eigenschaft für sich selbst definieren und diese an eine vorhandene, intuitiv benannte Eigenschaft eines seiner Komponententeile weiterleiten.</span><span class="sxs-lookup"><span data-stu-id="309cf-124">In this case, a control might define a property on itself and forward the property to an existing and intuitively named property of one of its component parts.</span></span> <span data-ttu-id="309cf-125">Ein Steuerelement, dessen Zusammensetzung einen zum Anzeigen seiner **Text**-Eigenschaft verwendeten [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652) enthält, kann beispielsweise diesen XAML-Code als Teil der Steuerelementvorlage enthalten:</span><span class="sxs-lookup"><span data-stu-id="309cf-125">For example, a control that incorporates a [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652) in its compositing, which is used to display the control's own **Text** property, might include this XAML as a part in the control template:</span></span> `<TextBlock Text="{TemplateBinding Text}" .... />`

<span data-ttu-id="309cf-126">Die Typen, die als Wert für die Quelleigenschaft und die Zieleigenschaft verwendet werden, müssen übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="309cf-126">The types used as the value for the source property and the target property must match.</span></span> <span data-ttu-id="309cf-127">Bei Verwendung von **TemplateBinding** gibt es keine Möglichkeit, einen Konverter zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="309cf-127">There's no opportunity to introduce a converter when you're using **TemplateBinding**.</span></span> <span data-ttu-id="309cf-128">Falls die Werte nicht übereinstimmen, tritt beim Analysieren des XAML-Codes ein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="309cf-128">Failing to match values results in an error when parsing the XAML.</span></span> <span data-ttu-id="309cf-129">Wenn Sie einen Konverter benötigen, können Sie die ausführliche Syntax für eine Vorlagenbindung verwenden, z.B.: </span><span class="sxs-lookup"><span data-stu-id="309cf-129">If you need a converter you can use the verbose syntax for a template binding such as:</span></span> `{Binding RelativeSource={RelativeSource TemplatedParent}, Converter="..." ...}`

<span data-ttu-id="309cf-130">Wenn Sie versuchen, eine **TemplateBinding** außerhalb einer [**ControlTemplate**](https://msdn.microsoft.com/library/windows/apps/br209391)-Definition in XAML zu verwenden, führt dies zu einem Parserfehler.</span><span class="sxs-lookup"><span data-stu-id="309cf-130">Attempting to use a **TemplateBinding** outside of a [**ControlTemplate**](https://msdn.microsoft.com/library/windows/apps/br209391) definition in XAML will result in a parser error.</span></span>

<span data-ttu-id="309cf-131">Sie können **TemplateBinding** für Fälle verwenden, in denen der übergeordnete Wert mit Vorlagen auch als weitere Bindung zurückgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="309cf-131">You can use **TemplateBinding** for cases where the templated parent value is also deferred as another binding.</span></span> <span data-ttu-id="309cf-132">Die Auswertung für **TemplateBinding** kann warten, bis etwaige erforderliche Laufzeitbindungen über Werte verfügen.</span><span class="sxs-lookup"><span data-stu-id="309cf-132">The evaluation for **TemplateBinding** can wait until any required runtime bindings have values.</span></span>

<span data-ttu-id="309cf-133">Ein **TemplateBinding**-Element ist stets eine unidirektionale Bindung.</span><span class="sxs-lookup"><span data-stu-id="309cf-133">A **TemplateBinding** is always a one-way binding.</span></span> <span data-ttu-id="309cf-134">Bei beiden beteiligten Eigenschaften muss es sich um Abhängigkeitseigenschaften handeln.</span><span class="sxs-lookup"><span data-stu-id="309cf-134">Both properties involved must be dependency properties.</span></span>

<span data-ttu-id="309cf-135">**TemplateBinding** ist eine Markuperweiterung.</span><span class="sxs-lookup"><span data-stu-id="309cf-135">**TemplateBinding** is a markup extension.</span></span> <span data-ttu-id="309cf-136">Markuperweiterungen werden in der Regel implementiert, wenn für Attributwerte Escapezeichen verwendet werden müssen, damit sie keine Literalwerte oder Handlernamen darstellen, und es nicht ausreicht, Typkonverter für bestimmte Typen oder Eigenschaften zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="309cf-136">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="309cf-137">Alle Markuperweiterungen in XAML verwenden die Zeichen „{” und „}” in ihrer Attributsyntax. Anhand dieser Konvention erkennt ein XAML-Prozessor, dass eine Markuperweiterung das Attribut verarbeiten muss.</span><span class="sxs-lookup"><span data-stu-id="309cf-137">All markup extensions in XAML use the "{" and "}" characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute.</span></span>

<span data-ttu-id="309cf-138">**Hinweis**  Die XAML-Prozessorimplementierung der Windows-Runtime enthält keine Sicherungsklassendarstellung für **TemplateBinding**.</span><span class="sxs-lookup"><span data-stu-id="309cf-138">**Note**  In the Windows Runtime XAML processor implementation, there is no backing class representation for **TemplateBinding**.</span></span> <span data-ttu-id="309cf-139">**TemplateBinding** ist ausschließlich für die Verwendung im XAML-Markup vorgesehen.</span><span class="sxs-lookup"><span data-stu-id="309cf-139">**TemplateBinding** is exclusively for use in XAML markup.</span></span> <span data-ttu-id="309cf-140">Es gibt keine einfache Methode zum Reproduzieren des Verhaltens im Code.</span><span class="sxs-lookup"><span data-stu-id="309cf-140">There isn't a straightforward way to reproduce the behavior in code.</span></span>

## <a name="related-topics"></a><span data-ttu-id="309cf-141">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="309cf-141">Related topics</span></span>

* [<span data-ttu-id="309cf-142">Schnellstart: Steuerelementvorlagen</span><span class="sxs-lookup"><span data-stu-id="309cf-142">Quickstart: Control templates</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/hh465374)
* [<span data-ttu-id="309cf-143">Datenbindung im Detail</span><span class="sxs-lookup"><span data-stu-id="309cf-143">Data binding in depth</span></span>](https://msdn.microsoft.com/library/windows/apps/mt210946)
* [**<span data-ttu-id="309cf-144">ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="309cf-144">ControlTemplate</span></span>**](https://msdn.microsoft.com/library/windows/apps/br209391)
* [<span data-ttu-id="309cf-145">Übersicht über XAML</span><span class="sxs-lookup"><span data-stu-id="309cf-145">XAML overview</span></span>](xaml-overview.md)
* [<span data-ttu-id="309cf-146">Übersicht über Abhängigkeitseigenschaften</span><span class="sxs-lookup"><span data-stu-id="309cf-146">Dependency properties overview</span></span>](dependency-properties-overview.md)
 

