---
author: jwmsft
description: Konfiguriert die XAML-Kompilierung, um partielle Klassen zwischen Markup und CodeBehind zu verknüpfen. Die partielle Codeklasse wird in einer separaten Codedatei definiert, die partielle Markupklasse wird von der Codegenerierung während der XAML-Kompilierung erstellt.
title: xClass-Attribut
ms.assetid: 40A7C036-133A-44DF-9D11-0D39232C948F
ms.author: jimwalk
ms.date: 02/08/2017
ms.topic: article
keywords: windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 6746969b1b717183894d6b941be41c9aca452960
ms.sourcegitcommit: e38b334edb82bf2b1474ba686990f4299b8f59c7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6846089"
---
# <a name="xclass-attribute"></a><span data-ttu-id="0f5fd-105">x:Class-Attribut</span><span class="sxs-lookup"><span data-stu-id="0f5fd-105">x:Class attribute</span></span>


<span data-ttu-id="0f5fd-106">Konfiguriert die XAML-Kompilierung, um partielle Klassen zwischen Markup und CodeBehind beizutreten.</span><span class="sxs-lookup"><span data-stu-id="0f5fd-106">Configures XAML compilation to join partial classes between markup and code-behind.</span></span> <span data-ttu-id="0f5fd-107">Die partielle Codeklasse wird in einer separaten Codedatei definiert, die partielle Markupklasse wird von der Codegenerierung während der XAML-Kompilierung erstellt.</span><span class="sxs-lookup"><span data-stu-id="0f5fd-107">The code partial class is defined in a separate code file, and the markup partial class is created by code generation during XAML compilation.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="0f5fd-108">XAML-Attributsyntax</span><span class="sxs-lookup"><span data-stu-id="0f5fd-108">XAML attribute usage</span></span>


``` syntax
<object x:Class="namespace.classname"...>
  ...
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="0f5fd-109">XAML-Werte</span><span class="sxs-lookup"><span data-stu-id="0f5fd-109">XAML values</span></span>

| <span data-ttu-id="0f5fd-110">Benennung</span><span class="sxs-lookup"><span data-stu-id="0f5fd-110">Term</span></span> | <span data-ttu-id="0f5fd-111">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0f5fd-111">Description</span></span> |
|------|-------------|
| <span data-ttu-id="0f5fd-112">Namespace</span><span class="sxs-lookup"><span data-stu-id="0f5fd-112">namespace</span></span> | <span data-ttu-id="0f5fd-113">Optional.</span><span class="sxs-lookup"><span data-stu-id="0f5fd-113">Optional.</span></span> <span data-ttu-id="0f5fd-114">Gibt einen Namespace an, der die partielle Klasse gemäß Angabe durch _classname_.</span><span class="sxs-lookup"><span data-stu-id="0f5fd-114">Specifies a namespace that contains the partial class identified by _classname_.</span></span> <span data-ttu-id="0f5fd-115">Wenn _Namespace_ angegeben ist, werden _namespace_ und _classname_ durch einen Punkt getrennt.</span><span class="sxs-lookup"><span data-stu-id="0f5fd-115">If _namespace_ is specified, a dot (.) separates _namespace_ and _classname_.</span></span> <span data-ttu-id="0f5fd-116">Ist kein _namespace_ angegeben, wird davon ausgegangen, dass _classname_ keinen Namespace besitzt.</span><span class="sxs-lookup"><span data-stu-id="0f5fd-116">If _namespace_ is omitted, _classname_ is assumed to have no namespace.</span></span> |
| <span data-ttu-id="0f5fd-117">classname</span><span class="sxs-lookup"><span data-stu-id="0f5fd-117">classname</span></span> | <span data-ttu-id="0f5fd-118">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="0f5fd-118">Required.</span></span> <span data-ttu-id="0f5fd-119">Gibt den Namen der partiellen Klasse an, die das geladene XAML und Ihr CodeBehind für dieses XAML verbindet.</span><span class="sxs-lookup"><span data-stu-id="0f5fd-119">Specifies the name of the partial class that connects the loaded XAML and your code-behind for that XAML.</span></span> | 

## <a name="remarks"></a><span data-ttu-id="0f5fd-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="0f5fd-120">Remarks</span></span>

<span data-ttu-id="0f5fd-121">**x:Class** kann als Attribut für ein beliebiges Element deklariert werden, das als Stamm einer XAML-Datei-/-Objektstruktur fungiert und durch Buildvorgänge kompiliert wird, oder für den [**Application**](https://msdn.microsoft.com/library/windows/apps/br242324)-Stamm in der Anwendungsdefinition einer kompilierten Anwendung.</span><span class="sxs-lookup"><span data-stu-id="0f5fd-121">**x:Class** can be declared as an attribute for any element that is the root of a XAML file/object tree and is being compiled by build actions, or for the [**Application**](https://msdn.microsoft.com/library/windows/apps/br242324) root in the application definition of a compiled application.</span></span> <span data-ttu-id="0f5fd-122">Wenn Sie **x:Class** für ein Element, bei dem es sich nicht um einen Stammknoten handelt, oder unter beliebigen Umständen für eine nicht mit der Buildaktion **Seite** kompilierte XAML-Datei deklarieren, tritt zur Kompilierzeit ein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="0f5fd-122">Declaring **x:Class** on any element other than a root node, and under any circumstances for a XAML file that is not compiled with the **Page** build action, results in a compile-time error.</span></span>

<span data-ttu-id="0f5fd-123">Die als **x:Class** verwendete Klasse darf keine geschachtelte Klasse sein.</span><span class="sxs-lookup"><span data-stu-id="0f5fd-123">The class used as **x:Class** cannot be a nested class.</span></span>

<span data-ttu-id="0f5fd-124">Der Wert des **x:Class**-Attributs muss eine Zeichenfolge sein, die den vollqualifizierten Namen einer Klasse angibt.</span><span class="sxs-lookup"><span data-stu-id="0f5fd-124">The value of the **x:Class** attribute must be a string that specifies the fully qualified name of a class.</span></span> <span data-ttu-id="0f5fd-125">Bei entsprechender CodeBehind-Struktur (Klassendefinition beginnt auf Klassenebene) können Sie die Namespaceinformationen auch weglassen.</span><span class="sxs-lookup"><span data-stu-id="0f5fd-125">You can omit namespace information so long as that is how the code-behind is structured also (your class definition starts at the class level).</span></span> <span data-ttu-id="0f5fd-126">Die CodeBehind-Datei für eine Seiten- oder Anwendungsdefinition muss sich in einer Codedatei befinden, die Teil des Projekts ist.</span><span class="sxs-lookup"><span data-stu-id="0f5fd-126">The code-behind file for a page or application definition must be within a code file that is included as part of the project.</span></span> <span data-ttu-id="0f5fd-127">Die CodeBehind-Klasse muss öffentlich sein.</span><span class="sxs-lookup"><span data-stu-id="0f5fd-127">The code-behind class must be public.</span></span> <span data-ttu-id="0f5fd-128">Die CodeBehind-Klasse muss partiell sein.</span><span class="sxs-lookup"><span data-stu-id="0f5fd-128">The code-behind class must be partial.</span></span>

## <a name="clr-language-rules"></a><span data-ttu-id="0f5fd-129">CLR-Sprachregeln</span><span class="sxs-lookup"><span data-stu-id="0f5fd-129">CLR language rules</span></span>

<span data-ttu-id="0f5fd-130">Ihre CodeBehind-Datei kann zwar eine C++-Datei sein, bestimmte Konventionen richten sich aber trotzdem nach der CLR-Sprachform, damit keine Abweichungen bei der XAML-Syntax auftreten.</span><span class="sxs-lookup"><span data-stu-id="0f5fd-130">Although your code-behind file can be a C++ file, there are certain conventions that still follow the CLR language form, so that there is no difference in the XAML syntax.</span></span> <span data-ttu-id="0f5fd-131">Genauer: Das Trennzeichen zwischen Namespace- und Klassennamenkomponenten eines beliebigen **x:Class**-Werts ist immer ein Punkt („.“), auch wenn das Trennzeichen zwischen Namespace und Klassenname in der zum XAML-Code gehörigen C++-Codedatei „::“ ist.</span><span class="sxs-lookup"><span data-stu-id="0f5fd-131">In particular, the separator between the namespace and classname components of any **x:Class** value is always a dot ("."), even though the separator between namespace and classname in the C++ code file associated with the XAML is "::".</span></span> <span data-ttu-id="0f5fd-132">Wenn Sie geschachtelte Namespaces in C++ deklarieren, sollte das Trennzeichen zwischen den aufeinander folgenden geschachtelten Namespacezeichenfolgen auch „.“ statt „::“ sein, wenn Sie den *namespace*-Teil des **x:Class**-Werts angeben.</span><span class="sxs-lookup"><span data-stu-id="0f5fd-132">If you declare nested namespaces in C++, then the separator between the successive nested namespace strings should also be "." rather than "::" when you specify the *namespace* part of the **x:Class** value.</span></span>

