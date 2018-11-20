---
author: jwmsft
description: Dient zum eindeutigen Identifizieren von Elementen, die als Ressourcen erstellt und referenziert werden und innerhalb eines ResourceDictionary-Elements vorhanden sind.
title: xKey-Attribut
ms.assetid: 141FC5AF-80EE-4401-8A1B-17CB22C2277A
ms.author: jimwalk
ms.date: 02/08/2017
ms.topic: article
keywords: windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 8d48ccb93a411e92b57059192de38366f27353a3
ms.sourcegitcommit: ed0304b8a214c03b8aab74b8ef12c9f82b8e3c5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "7290822"
---
# <a name="xkey-attribute"></a><span data-ttu-id="8f8fe-104">x:Key-Attribut</span><span class="sxs-lookup"><span data-stu-id="8f8fe-104">x:Key attribute</span></span>


<span data-ttu-id="8f8fe-105">Dient zum eindeutigen Identifizieren von Elementen, die als Ressourcen erstellt und referenziert werden und innerhalb eines [**ResourceDictionary**](https://msdn.microsoft.com/library/windows/apps/br208794)-Elements vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="8f8fe-105">Uniquely identifies elements that are created and referenced as resources, and which exist within a [**ResourceDictionary**](https://msdn.microsoft.com/library/windows/apps/br208794).</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="8f8fe-106">XAML-Attributsyntax</span><span class="sxs-lookup"><span data-stu-id="8f8fe-106">XAML attribute usage</span></span>

``` syntax
<ResourceDictionary>
  <object x:Key="stringKeyValue".../>
</ResourceDictionary>
```

## <a name="xaml-attribute-usage-implicit-resourcedictionary"></a><span data-ttu-id="8f8fe-107">XAML-Attributverwendung (implizites **ResourceDictionary**)</span><span class="sxs-lookup"><span data-stu-id="8f8fe-107">XAML attribute usage (implicit **ResourceDictionary**)</span></span>

``` syntax
<object.Resources>
  <object x:Key="stringKeyValue".../>
</object.Resources>
```

## <a name="xaml-values"></a><span data-ttu-id="8f8fe-108">XAML-Werte</span><span class="sxs-lookup"><span data-stu-id="8f8fe-108">XAML values</span></span>

| <span data-ttu-id="8f8fe-109">Benennung</span><span class="sxs-lookup"><span data-stu-id="8f8fe-109">Term</span></span> | <span data-ttu-id="8f8fe-110">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8f8fe-110">Description</span></span> |
|------|-------------|
| <span data-ttu-id="8f8fe-111">object</span><span class="sxs-lookup"><span data-stu-id="8f8fe-111">object</span></span> | <span data-ttu-id="8f8fe-112">Beliebige Objekte, die freigegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="8f8fe-112">Any object that is shareable.</span></span> <span data-ttu-id="8f8fe-113">Weitere Informationen finden Sie unter [ResourceDictionary- und XAML-Ressourcenverweise](https://msdn.microsoft.com/library/windows/apps/mt187273).</span><span class="sxs-lookup"><span data-stu-id="8f8fe-113">See [ResourceDictionary and XAML resource references](https://msdn.microsoft.com/library/windows/apps/mt187273).</span></span> |
| <span data-ttu-id="8f8fe-114">stringKeyValue</span><span class="sxs-lookup"><span data-stu-id="8f8fe-114">stringKeyValue</span></span> | <span data-ttu-id="8f8fe-115">Eine als Schlüssel verwendete echte Zeichenfolge, die der _XamlName_-Grammatik entsprechen muss.</span><span class="sxs-lookup"><span data-stu-id="8f8fe-115">A true string used as a key, which must conform to the _XamlName_> grammar.</span></span> <span data-ttu-id="8f8fe-116">Weitere Informationen erhalten Sie in "XamlName-Grammatik" unten.</span><span class="sxs-lookup"><span data-stu-id="8f8fe-116">See "XamlName grammar" below.</span></span> | 

##  <a name="xamlname-grammar"></a><span data-ttu-id="8f8fe-117">XamlName-Grammatik</span><span class="sxs-lookup"><span data-stu-id="8f8fe-117">XamlName grammar</span></span>

<span data-ttu-id="8f8fe-118">Im Anschluss finden Sie die maßgebende Grammatik für eine Zeichenfolge, die in der UWP-XAML-Implementierung (Universelle Windows-Plattform) als Schlüssel verwendet wird:</span><span class="sxs-lookup"><span data-stu-id="8f8fe-118">The following is the normative grammar for a string that is used as a key in the Universal Windows Platform (UWP) XAML implementation:</span></span>

``` syntax
XamlName ::= NameStartChar (NameChar)*
NameStartChar ::= LetterCharacter | '_'
NameChar ::= NameStartChar | DecimalDigit
LetterCharacter ::= ('a'-'z') | ('A'-'Z')
DecimalDigit ::= '0'-'9'
CombiningCharacter::= none
```

-   <span data-ttu-id="8f8fe-119">Die Zeichen sind auf den unteren ASCII-Bereich beschränkt – genauer: auf Groß- und Kleinbuchstaben des lateinischen Alphabets sowie auf Ziffern und den Unterstrich (\_).</span><span class="sxs-lookup"><span data-stu-id="8f8fe-119">Characters are restricted to the lower ASCII range, and more specifically to Roman alphabet uppercase and lowercase letters, digits, and the underscore (\_) character.</span></span>
-   <span data-ttu-id="8f8fe-120">Der Unicode-Zeichenbereich wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8f8fe-120">The Unicode character range is not supported.</span></span>
-   <span data-ttu-id="8f8fe-121">Ein Name darf nicht mit einer Ziffer beginnen.</span><span class="sxs-lookup"><span data-stu-id="8f8fe-121">A name cannot begin with a digit.</span></span>

## <a name="remarks"></a><span data-ttu-id="8f8fe-122">Hinweise</span><span class="sxs-lookup"><span data-stu-id="8f8fe-122">Remarks</span></span>

<span data-ttu-id="8f8fe-123">Zu den untergeordneten Elementen eines [**ResourceDictionary**](https://msdn.microsoft.com/library/windows/apps/br208794)-Elements gehört im Allgemeinen ein **x:Key**-Attribut zum Angeben eines eindeutigen Schlüsselwerts innerhalb des Wörterbuchs.</span><span class="sxs-lookup"><span data-stu-id="8f8fe-123">Child elements of a [**ResourceDictionary**](https://msdn.microsoft.com/library/windows/apps/br208794) generally include an **x:Key** attribute that specifies a unique key value within that dictionary.</span></span> <span data-ttu-id="8f8fe-124">Die Eindeutigkeit von Schlüsseln wird beim Laden durch den XAML-Prozessor erzwungen.</span><span class="sxs-lookup"><span data-stu-id="8f8fe-124">Key uniqueness is enforced at load time by the XAML processor.</span></span> <span data-ttu-id="8f8fe-125">Nicht eindeutige **x:Key**-Werte haben XAML-Analyseausnahmen zur Folge.</span><span class="sxs-lookup"><span data-stu-id="8f8fe-125">Non-unique **x:Key** values will result in XAML parse exceptions.</span></span> <span data-ttu-id="8f8fe-126">Auf Anforderung der [{StaticResource}-Markuperweiterung](staticresource-markup-extension.md) haben auch nicht aufgelöste Schlüssel XAML-Analyseausnahmen zur Folge.</span><span class="sxs-lookup"><span data-stu-id="8f8fe-126">If requested by [{StaticResource} markup extension](staticresource-markup-extension.md), a non-resolved key will also result in XAML parse exceptions.</span></span>

<span data-ttu-id="8f8fe-127">**x:Key** und [x:Name](x-name-attribute.md) sind nicht identisch.</span><span class="sxs-lookup"><span data-stu-id="8f8fe-127">**x:Key** and [x:Name](x-name-attribute.md) are not identical concepts.</span></span> <span data-ttu-id="8f8fe-128">**x:Key** wird ausschließlich in Ressourcenwörterbüchern verwendet.</span><span class="sxs-lookup"><span data-stu-id="8f8fe-128">**x:Key** is used exclusively in resource dictionaries.</span></span> <span data-ttu-id="8f8fe-129">x:Name wird in allen XAML-Bereichen verwendet.</span><span class="sxs-lookup"><span data-stu-id="8f8fe-129">x:Name is used for all areas of XAML.</span></span> <span data-ttu-id="8f8fe-130">Durch einen [**FindName**](https://msdn.microsoft.com/library/windows/apps/br208715)-Aufruf mit einem Schlüsselwert wird keine Ressource mit Schlüssel abgerufen.</span><span class="sxs-lookup"><span data-stu-id="8f8fe-130">A [**FindName**](https://msdn.microsoft.com/library/windows/apps/br208715) call using a key value will not retrieve a keyed resource.</span></span> <span data-ttu-id="8f8fe-131">Objekte, die in einem Ressourcenwörterbuch definiert sind, verfügen über **x: Key** oder **x: Name** oder über beide.</span><span class="sxs-lookup"><span data-stu-id="8f8fe-131">Objects defined in a resource dictionary may have an **x:Key**, an **x:Name** or both.</span></span> <span data-ttu-id="8f8fe-132">„Key“ und „Name“ müssen nicht übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="8f8fe-132">The key and name are not required to match.</span></span>

<span data-ttu-id="8f8fe-133">Beachten Sie, dass das [**ResourceDictionary**](https://msdn.microsoft.com/library/windows/apps/br208794)-Objekt in der gezeigten impliziten Syntax dahingehend implizit ist, wie der XAML-Prozessor ein neues Objekt erzeugt, um eine [**Resources**](https://msdn.microsoft.com/library/windows/apps/br208740)-Sammlung aufzufüllen.</span><span class="sxs-lookup"><span data-stu-id="8f8fe-133">Note that in the implicit syntax shown, the [**ResourceDictionary**](https://msdn.microsoft.com/library/windows/apps/br208794) object is implicit in how the XAML processor produces a new object to populate a [**Resources**](https://msdn.microsoft.com/library/windows/apps/br208740) collection.</span></span>

<span data-ttu-id="8f8fe-134">Der Code zum Angeben von **x:Key** entspricht einem beliebigen Vorgang, in dem ein Schlüssel mit dem zugrunde liegenden [**ResourceDictionary**](https://msdn.microsoft.com/library/windows/apps/br208794) verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="8f8fe-134">The code equivalent of specifying **x:Key** is any operation that uses a key with the underlying [**ResourceDictionary**](https://msdn.microsoft.com/library/windows/apps/br208794).</span></span> <span data-ttu-id="8f8fe-135">So entspricht beispielsweise ein im Markup für eine Ressource angewendeter **x:Key** dem Wert des *key*-Parameters **Insert**, wenn Sie die Ressource einem **ResourceDictionary** hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="8f8fe-135">For example, an **x:Key** applied in markup for a resource is equivalent to the value of the *key* parameter of **Insert** when you add the resource to a **ResourceDictionary**.</span></span>

<span data-ttu-id="8f8fe-136">Ein Element in einem Ressourcenwörterbuch kann einen Wert für **x:Key** auslassen, wenn es sich um ein zielgerichtetes [**Style**](https://msdn.microsoft.com/library/windows/apps/br208849)- oder [**ControlTemplate**](https://msdn.microsoft.com/library/windows/apps/br209391)-Element handelt. In all diesen Fällen ist der implizite Schlüssel des Ressourcenelements der als Zeichenfolge interpretierte **TargetType**-Wert.</span><span class="sxs-lookup"><span data-stu-id="8f8fe-136">An item in a resource dictionary can omit a value for **x:Key** if it is a targeted [**Style**](https://msdn.microsoft.com/library/windows/apps/br208849) or [**ControlTemplate**](https://msdn.microsoft.com/library/windows/apps/br209391); in each of these cases the implicit key of the resource item is the **TargetType** value interpreted as a string.</span></span> <span data-ttu-id="8f8fe-137">Weitere Informationen finden Sie unter [Schnellstart: Formatieren von Steuerelementen](https://msdn.microsoft.com/library/windows/apps/hh465498) und [ResourceDictionary- und XAML-Ressourcenverweise](https://msdn.microsoft.com/library/windows/apps/mt187273).</span><span class="sxs-lookup"><span data-stu-id="8f8fe-137">For more info, see [Quickstart: styling controls](https://msdn.microsoft.com/library/windows/apps/hh465498) and [ResourceDictionary and XAML resource references](https://msdn.microsoft.com/library/windows/apps/mt187273).</span></span>

