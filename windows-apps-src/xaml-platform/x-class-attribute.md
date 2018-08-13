---
author: jwmsft
description: Konfiguriert die XAML-Kompilierung, um partielle Klassen zwischen Markup und CodeBehind zu verknüpfen. Die partielle Codeklasse wird in einer separaten Codedatei definiert, die partielle Markupklasse wird von der Codegenerierung während der XAML-Kompilierung erstellt.
title: xClass-Attribut
ms.assetid: 40A7C036-133A-44DF-9D11-0D39232C948F
ms.author: jimwalk
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.openlocfilehash: d3105e8ac345e1eb6f0d974f8ea29e741dae9f58
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
ms.translationtype: MT
ms.contentlocale: de-DE
ms.locfileid: "235000"
---
# <a name="xclass-attribute"></a><span data-ttu-id="1dcb9-105">x:Class-Attribut</span><span class="sxs-lookup"><span data-stu-id="1dcb9-105">x:Class attribute</span></span>

<span data-ttu-id="1dcb9-106">\[ Aktualisiert für UWP-Apps unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="1dcb9-106">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="1dcb9-107">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132). \]</span><span class="sxs-lookup"><span data-stu-id="1dcb9-107">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>

<span data-ttu-id="1dcb9-108">Konfiguriert die XAML-Kompilierung, um partielle Klassen zwischen Markup und CodeBehind beizutreten.</span><span class="sxs-lookup"><span data-stu-id="1dcb9-108">Configures XAML compilation to join partial classes between markup and code-behind.</span></span> <span data-ttu-id="1dcb9-109">Die partielle Codeklasse wird in einer separaten Codedatei definiert, die partielle Markupklasse wird von der Codegenerierung während der XAML-Kompilierung erstellt.</span><span class="sxs-lookup"><span data-stu-id="1dcb9-109">The code partial class is defined in a separate code file, and the markup partial class is created by code generation during XAML compilation.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="1dcb9-110">XAML-Attributsyntax</span><span class="sxs-lookup"><span data-stu-id="1dcb9-110">XAML attribute usage</span></span>


``` syntax
<object x:Class="namespace.classname"...>
  ...
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="1dcb9-111">XAML-Werte</span><span class="sxs-lookup"><span data-stu-id="1dcb9-111">XAML values</span></span>

| <span data-ttu-id="1dcb9-112">Benennung</span><span class="sxs-lookup"><span data-stu-id="1dcb9-112">Term</span></span> | <span data-ttu-id="1dcb9-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="1dcb9-113">Description</span></span> |
|------|-------------|
| <span data-ttu-id="1dcb9-114">Namespace</span><span class="sxs-lookup"><span data-stu-id="1dcb9-114">namespace</span></span> | <span data-ttu-id="1dcb9-115">Optional.</span><span class="sxs-lookup"><span data-stu-id="1dcb9-115">Optional.</span></span> <span data-ttu-id="1dcb9-116">Gibt einen Namespace an, der die partielle Klasse gemäß Angabe durch _classname_.</span><span class="sxs-lookup"><span data-stu-id="1dcb9-116">Specifies a namespace that contains the partial class identified by _classname_.</span></span> <span data-ttu-id="1dcb9-117">Wenn _Namespace_ angegeben ist, werden _namespace_ und _classname_ durch einen Punkt getrennt.</span><span class="sxs-lookup"><span data-stu-id="1dcb9-117">If _namespace_ is specified, a dot (.) separates _namespace_ and _classname_.</span></span> <span data-ttu-id="1dcb9-118">Ist kein _namespace_ angegeben, wird davon ausgegangen, dass _classname_ keinen Namespace besitzt.</span><span class="sxs-lookup"><span data-stu-id="1dcb9-118">If _namespace_ is omitted, _classname_ is assumed to have no namespace.</span></span> |
| <span data-ttu-id="1dcb9-119">classname</span><span class="sxs-lookup"><span data-stu-id="1dcb9-119">classname</span></span> | <span data-ttu-id="1dcb9-120">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="1dcb9-120">Required.</span></span> <span data-ttu-id="1dcb9-121">Gibt den Namen der partiellen Klasse an, die das geladene XAML und Ihr CodeBehind für dieses XAML verbindet.</span><span class="sxs-lookup"><span data-stu-id="1dcb9-121">Specifies the name of the partial class that connects the loaded XAML and your code-behind for that XAML.</span></span> | 

## <a name="remarks"></a><span data-ttu-id="1dcb9-122">Hinweise</span><span class="sxs-lookup"><span data-stu-id="1dcb9-122">Remarks</span></span>

<span data-ttu-id="1dcb9-123">**x:Class** kann als Attribut für ein beliebiges Element deklariert werden, das als Stamm einer XAML-Datei-/-Objektstruktur fungiert und durch Buildvorgänge kompiliert wird, oder für den [**Application**](https://msdn.microsoft.com/library/windows/apps/br242324)-Stamm in der Anwendungsdefinition einer kompilierten Anwendung.</span><span class="sxs-lookup"><span data-stu-id="1dcb9-123">**x:Class** can be declared as an attribute for any element that is the root of a XAML file/object tree and is being compiled by build actions, or for the [**Application**](https://msdn.microsoft.com/library/windows/apps/br242324) root in the application definition of a compiled application.</span></span> <span data-ttu-id="1dcb9-124">Wenn Sie **x:Class** für ein Element, bei dem es sich nicht um einen Stammknoten handelt, oder unter beliebigen Umständen für eine nicht mit der Buildaktion **Seite** kompilierte XAML-Datei deklarieren, tritt zur Kompilierzeit ein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="1dcb9-124">Declaring **x:Class** on any element other than a root node, and under any circumstances for a XAML file that is not compiled with the **Page** build action, results in a compile-time error.</span></span>

<span data-ttu-id="1dcb9-125">Die als **x:Class** verwendete Klasse darf keine geschachtelte Klasse sein.</span><span class="sxs-lookup"><span data-stu-id="1dcb9-125">The class used as **x:Class** cannot be a nested class.</span></span>

<span data-ttu-id="1dcb9-126">Der Wert des **x:Class**-Attributs muss eine Zeichenfolge sein, die den vollqualifizierten Namen einer Klasse angibt.</span><span class="sxs-lookup"><span data-stu-id="1dcb9-126">The value of the **x:Class** attribute must be a string that specifies the fully qualified name of a class.</span></span> <span data-ttu-id="1dcb9-127">Bei entsprechender CodeBehind-Struktur (Klassendefinition beginnt auf Klassenebene) können Sie die Namespaceinformationen auch weglassen.</span><span class="sxs-lookup"><span data-stu-id="1dcb9-127">You can omit namespace information so long as that is how the code-behind is structured also (your class definition starts at the class level).</span></span> <span data-ttu-id="1dcb9-128">Die CodeBehind-Datei für eine Seiten- oder Anwendungsdefinition muss sich in einer Codedatei befinden, die Teil des Projekts ist.</span><span class="sxs-lookup"><span data-stu-id="1dcb9-128">The code-behind file for a page or application definition must be within a code file that is included as part of the project.</span></span> <span data-ttu-id="1dcb9-129">Die CodeBehind-Klasse muss öffentlich sein.</span><span class="sxs-lookup"><span data-stu-id="1dcb9-129">The code-behind class must be public.</span></span> <span data-ttu-id="1dcb9-130">Die CodeBehind-Klasse muss partiell sein.</span><span class="sxs-lookup"><span data-stu-id="1dcb9-130">The code-behind class must be partial.</span></span>

## <a name="clr-language-rules"></a><span data-ttu-id="1dcb9-131">CLR-Sprachregeln</span><span class="sxs-lookup"><span data-stu-id="1dcb9-131">CLR language rules</span></span>

<span data-ttu-id="1dcb9-132">Ihre CodeBehind-Datei kann zwar eine C++-Datei sein, bestimmte Konventionen richten sich aber trotzdem nach der CLR-Sprachform, damit keine Abweichungen bei der XAML-Syntax auftreten.</span><span class="sxs-lookup"><span data-stu-id="1dcb9-132">Although your code-behind file can be a C++ file, there are certain conventions that still follow the CLR language form, so that there is no difference in the XAML syntax.</span></span> <span data-ttu-id="1dcb9-133">Genauer: Das Trennzeichen zwischen Namespace- und Klassennamenkomponenten eines beliebigen **x:Class**-Werts ist immer ein Punkt („.“), auch wenn das Trennzeichen zwischen Namespace und Klassenname in der zum XAML-Code gehörigen C++-Codedatei „::“ ist.</span><span class="sxs-lookup"><span data-stu-id="1dcb9-133">In particular, the separator between the namespace and classname components of any **x:Class** value is always a dot ("."), even though the separator between namespace and classname in the C++ code file associated with the XAML is "::".</span></span> <span data-ttu-id="1dcb9-134">Wenn Sie geschachtelte Namespaces in C++ deklarieren, sollte das Trennzeichen zwischen den aufeinander folgenden geschachtelten Namespacezeichenfolgen auch „.“ statt „::“ sein, wenn Sie den *namespace*-Teil des **x:Class**-Werts angeben.</span><span class="sxs-lookup"><span data-stu-id="1dcb9-134">If you declare nested namespaces in C++, then the separator between the successive nested namespace strings should also be "." rather than "::" when you specify the *namespace* part of the **x:Class** value.</span></span>

