---
author: jwmsft
description: Dient zum eindeutigen Identifizieren von Elementen, die als Ressourcen erstellt und referenziert werden und innerhalb eines ResourceDictionary-Elements vorhanden sind.
title: xKey-Attribut
ms.assetid: 141FC5AF-80EE-4401-8A1B-17CB22C2277A
ms.author: jimwalk
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.openlocfilehash: 4b76c16d276af295a1b2eed292ebeffc56b2e604
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
ms.translationtype: MT
ms.contentlocale: de-DE
ms.locfileid: "235034"
---
# <a name="xkey-attribute"></a><span data-ttu-id="c5484-104">x:Key-Attribut</span><span class="sxs-lookup"><span data-stu-id="c5484-104">x:Key attribute</span></span>

<span data-ttu-id="c5484-105">\[ Aktualisiert für UWP-Apps unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="c5484-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="c5484-106">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132). \]</span><span class="sxs-lookup"><span data-stu-id="c5484-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>

<span data-ttu-id="c5484-107">Dient zum eindeutigen Identifizieren von Elementen, die als Ressourcen erstellt und referenziert werden und innerhalb eines [**ResourceDictionary**](https://msdn.microsoft.com/library/windows/apps/br208794)-Elements vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="c5484-107">Uniquely identifies elements that are created and referenced as resources, and which exist within a [**ResourceDictionary**](https://msdn.microsoft.com/library/windows/apps/br208794).</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="c5484-108">XAML-Attributsyntax</span><span class="sxs-lookup"><span data-stu-id="c5484-108">XAML attribute usage</span></span>

``` syntax
<ResourceDictionary>
  <object x:Key="stringKeyValue".../>
</ResourceDictionary>
```

## <a name="xaml-attribute-usage-implicit-resourcedictionary"></a><span data-ttu-id="c5484-109">XAML-Attributverwendung (implizites **ResourceDictionary**)</span><span class="sxs-lookup"><span data-stu-id="c5484-109">XAML attribute usage (implicit **ResourceDictionary**)</span></span>

``` syntax
<object.Resources>
  <object x:Key="stringKeyValue".../>
</object.Resources>
```

## <a name="xaml-values"></a><span data-ttu-id="c5484-110">XAML-Werte</span><span class="sxs-lookup"><span data-stu-id="c5484-110">XAML values</span></span>

| <span data-ttu-id="c5484-111">Benennung</span><span class="sxs-lookup"><span data-stu-id="c5484-111">Term</span></span> | <span data-ttu-id="c5484-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c5484-112">Description</span></span> |
|------|-------------|
| <span data-ttu-id="c5484-113">object</span><span class="sxs-lookup"><span data-stu-id="c5484-113">object</span></span> | <span data-ttu-id="c5484-114">Beliebige Objekte, die freigegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="c5484-114">Any object that is shareable.</span></span> <span data-ttu-id="c5484-115">Weitere Informationen finden Sie unter [ResourceDictionary- und XAML-Ressourcenverweise](https://msdn.microsoft.com/library/windows/apps/mt187273).</span><span class="sxs-lookup"><span data-stu-id="c5484-115">See [ResourceDictionary and XAML resource references](https://msdn.microsoft.com/library/windows/apps/mt187273).</span></span> |
| <span data-ttu-id="c5484-116">stringKeyValue</span><span class="sxs-lookup"><span data-stu-id="c5484-116">stringKeyValue</span></span> | <span data-ttu-id="c5484-117">Eine als Schlüssel verwendete echte Zeichenfolge, die der _XamlName_-Grammatik entsprechen muss.</span><span class="sxs-lookup"><span data-stu-id="c5484-117">A true string used as a key, which must conform to the _XamlName_> grammar.</span></span> <span data-ttu-id="c5484-118">Weitere Informationen erhalten Sie in "XamlName-Grammatik" unten.</span><span class="sxs-lookup"><span data-stu-id="c5484-118">See "XamlName grammar" below.</span></span> | 

##  <a name="xamlname-grammar"></a><span data-ttu-id="c5484-119">XamlName-Grammatik</span><span class="sxs-lookup"><span data-stu-id="c5484-119">XamlName grammar</span></span>

<span data-ttu-id="c5484-120">Im Anschluss finden Sie die maßgebende Grammatik für eine Zeichenfolge, die in der UWP-XAML-Implementierung (Universelle Windows-Plattform) als Schlüssel verwendet wird:</span><span class="sxs-lookup"><span data-stu-id="c5484-120">The following is the normative grammar for a string that is used as a key in the Universal Windows Platform (UWP) XAML implementation:</span></span>

``` syntax
XamlName ::= NameStartChar (NameChar)*
NameStartChar ::= LetterCharacter | '_'
NameChar ::= NameStartChar | DecimalDigit
LetterCharacter ::= ('a'-'z') | ('A'-'Z')
DecimalDigit ::= '0'-'9'
CombiningCharacter::= none
```

-   <span data-ttu-id="c5484-121">Die Zeichen sind auf den unteren ASCII-Bereich beschränkt – genauer: auf Groß- und Kleinbuchstaben des lateinischen Alphabets sowie auf Ziffern und den Unterstrich (\_).</span><span class="sxs-lookup"><span data-stu-id="c5484-121">Characters are restricted to the lower ASCII range, and more specifically to Roman alphabet uppercase and lowercase letters, digits, and the underscore (\_) character.</span></span>
-   <span data-ttu-id="c5484-122">Der Unicode-Zeichenbereich wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c5484-122">The Unicode character range is not supported.</span></span>
-   <span data-ttu-id="c5484-123">Ein Name darf nicht mit einer Ziffer beginnen.</span><span class="sxs-lookup"><span data-stu-id="c5484-123">A name cannot begin with a digit.</span></span>

## <a name="remarks"></a><span data-ttu-id="c5484-124">Hinweise</span><span class="sxs-lookup"><span data-stu-id="c5484-124">Remarks</span></span>

<span data-ttu-id="c5484-125">Zu den untergeordneten Elementen eines [**ResourceDictionary**](https://msdn.microsoft.com/library/windows/apps/br208794)-Elements gehört im Allgemeinen ein **x:Key**-Attribut zum Angeben eines eindeutigen Schlüsselwerts innerhalb des Wörterbuchs.</span><span class="sxs-lookup"><span data-stu-id="c5484-125">Child elements of a [**ResourceDictionary**](https://msdn.microsoft.com/library/windows/apps/br208794) generally include an **x:Key** attribute that specifies a unique key value within that dictionary.</span></span> <span data-ttu-id="c5484-126">Die Eindeutigkeit von Schlüsseln wird beim Laden durch den XAML-Prozessor erzwungen.</span><span class="sxs-lookup"><span data-stu-id="c5484-126">Key uniqueness is enforced at load time by the XAML processor.</span></span> <span data-ttu-id="c5484-127">Nicht eindeutige **x:Key**-Werte haben XAML-Analyseausnahmen zur Folge.</span><span class="sxs-lookup"><span data-stu-id="c5484-127">Non-unique **x:Key** values will result in XAML parse exceptions.</span></span> <span data-ttu-id="c5484-128">Auf Anforderung der [{StaticResource}-Markuperweiterung](staticresource-markup-extension.md) haben auch nicht aufgelöste Schlüssel XAML-Analyseausnahmen zur Folge.</span><span class="sxs-lookup"><span data-stu-id="c5484-128">If requested by [{StaticResource} markup extension](staticresource-markup-extension.md), a non-resolved key will also result in XAML parse exceptions.</span></span>

<span data-ttu-id="c5484-129">**x:Key** und [x:Name](x-name-attribute.md) sind nicht identisch.</span><span class="sxs-lookup"><span data-stu-id="c5484-129">**x:Key** and [x:Name](x-name-attribute.md) are not identical concepts.</span></span> <span data-ttu-id="c5484-130">**x:Key** wird ausschließlich in Ressourcenwörterbüchern verwendet.</span><span class="sxs-lookup"><span data-stu-id="c5484-130">**x:Key** is used exclusively in resource dictionaries.</span></span> <span data-ttu-id="c5484-131">x:Name wird in allen XAML-Bereichen verwendet.</span><span class="sxs-lookup"><span data-stu-id="c5484-131">x:Name is used for all areas of XAML.</span></span> <span data-ttu-id="c5484-132">Durch einen [**FindName**](https://msdn.microsoft.com/library/windows/apps/br208715)-Aufruf mit einem Schlüsselwert wird keine Ressource mit Schlüssel abgerufen.</span><span class="sxs-lookup"><span data-stu-id="c5484-132">A [**FindName**](https://msdn.microsoft.com/library/windows/apps/br208715) call using a key value will not retrieve a keyed resource.</span></span> <span data-ttu-id="c5484-133">Objekte, die in einem Ressourcenwörterbuch definiert sind, verfügen über **x: Key** oder **x: Name** oder über beide.</span><span class="sxs-lookup"><span data-stu-id="c5484-133">Objects defined in a resource dictionary may have an **x:Key**, an **x:Name** or both.</span></span> <span data-ttu-id="c5484-134">„Key“ und „Name“ müssen nicht übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="c5484-134">The key and name are not required to match.</span></span>

<span data-ttu-id="c5484-135">Beachten Sie, dass das [**ResourceDictionary**](https://msdn.microsoft.com/library/windows/apps/br208794)-Objekt in der gezeigten impliziten Syntax dahingehend implizit ist, wie der XAML-Prozessor ein neues Objekt erzeugt, um eine [**Resources**](https://msdn.microsoft.com/library/windows/apps/br208740)-Sammlung aufzufüllen.</span><span class="sxs-lookup"><span data-stu-id="c5484-135">Note that in the implicit syntax shown, the [**ResourceDictionary**](https://msdn.microsoft.com/library/windows/apps/br208794) object is implicit in how the XAML processor produces a new object to populate a [**Resources**](https://msdn.microsoft.com/library/windows/apps/br208740) collection.</span></span>

<span data-ttu-id="c5484-136">Der Code zum Angeben von **x:Key** entspricht einem beliebigen Vorgang, in dem ein Schlüssel mit dem zugrunde liegenden [**ResourceDictionary**](https://msdn.microsoft.com/library/windows/apps/br208794) verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="c5484-136">The code equivalent of specifying **x:Key** is any operation that uses a key with the underlying [**ResourceDictionary**](https://msdn.microsoft.com/library/windows/apps/br208794).</span></span> <span data-ttu-id="c5484-137">So entspricht beispielsweise ein im Markup für eine Ressource angewendeter **x:Key** dem Wert des *key*-Parameters **Insert**, wenn Sie die Ressource einem **ResourceDictionary** hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="c5484-137">For example, an **x:Key** applied in markup for a resource is equivalent to the value of the *key* parameter of **Insert** when you add the resource to a **ResourceDictionary**.</span></span>

<span data-ttu-id="c5484-138">Ein Element in einem Ressourcenwörterbuch kann einen Wert für **x:Key** auslassen, wenn es sich um ein zielgerichtetes [**Style**](https://msdn.microsoft.com/library/windows/apps/br208849)- oder [**ControlTemplate**](https://msdn.microsoft.com/library/windows/apps/br209391)-Element handelt. In all diesen Fällen ist der implizite Schlüssel des Ressourcenelements der als Zeichenfolge interpretierte **TargetType**-Wert.</span><span class="sxs-lookup"><span data-stu-id="c5484-138">An item in a resource dictionary can omit a value for **x:Key** if it is a targeted [**Style**](https://msdn.microsoft.com/library/windows/apps/br208849) or [**ControlTemplate**](https://msdn.microsoft.com/library/windows/apps/br209391); in each of these cases the implicit key of the resource item is the **TargetType** value interpreted as a string.</span></span> <span data-ttu-id="c5484-139">Weitere Informationen finden Sie unter [Schnellstart: Formatieren von Steuerelementen](https://msdn.microsoft.com/library/windows/apps/hh465498) und [ResourceDictionary- und XAML-Ressourcenverweise](https://msdn.microsoft.com/library/windows/apps/mt187273).</span><span class="sxs-lookup"><span data-stu-id="c5484-139">For more info, see [Quickstart: styling controls](https://msdn.microsoft.com/library/windows/apps/hh465498) and [ResourceDictionary and XAML resource references](https://msdn.microsoft.com/library/windows/apps/mt187273).</span></span>

