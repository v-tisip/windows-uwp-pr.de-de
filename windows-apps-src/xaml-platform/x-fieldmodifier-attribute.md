---
author: jwmsft
description: Ändert das XAML-Kompilierungsverhalten, sodass Felder für Verweise auf benannte Objekte mit öffentlichem Zugriff definiert werden und nicht das private Standardverhalten aufweisen.
title: xFieldModifier-Attribut
ms.assetid: 6FBCC00B-848D-4454-8B1F-287CA8406DDF
ms.author: jimwalk
ms.date: 02/08/2017
ms.topic: article
keywords: windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: de1d7dedbd2bd3d51bd2e1c1a9652d18f2b78ef0
ms.sourcegitcommit: cd00bb829306871e5103db481cf224ea7fb613f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5872686"
---
# <a name="xfieldmodifier-attribute"></a><span data-ttu-id="2b546-104">x:FieldModifier-Attribut</span><span class="sxs-lookup"><span data-stu-id="2b546-104">x:FieldModifier attribute</span></span>


<span data-ttu-id="2b546-105">Ändert das XAML-Kompilierungsverhalten, sodass Felder für Verweise auf benannte Objekte mit **öffentlichem** Zugriff definiert werden und nicht das **private** Standardverhalten aufweisen.</span><span class="sxs-lookup"><span data-stu-id="2b546-105">Modifies XAML compilation behavior, such that fields for named object references are defined with **public** access rather than the **private** default behavior.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="2b546-106">XAML-Attributsyntax</span><span class="sxs-lookup"><span data-stu-id="2b546-106">XAML attribute usage</span></span>

``` syntax
<object x:FieldModifier="public".../>
```

## <a name="dependencies"></a><span data-ttu-id="2b546-107">Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="2b546-107">Dependencies</span></span>

<span data-ttu-id="2b546-108">[x:Name-Attribut](x-name-attribute.md) muss in demselben Element ebenfalls bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="2b546-108">[x:Name attribute](x-name-attribute.md) must also be provided on the same element.</span></span>

## <a name="remarks"></a><span data-ttu-id="2b546-109">Hinweise</span><span class="sxs-lookup"><span data-stu-id="2b546-109">Remarks</span></span>

<span data-ttu-id="2b546-110">Der Wert für das **x:FieldModifier**-Attribut variiert je nach Programmiersprache.</span><span class="sxs-lookup"><span data-stu-id="2b546-110">The value for the **x:FieldModifier** attribute will vary by programming language.</span></span> <span data-ttu-id="2b546-111">Gültige Werte sind **private**, **public**, **protected**, **internal** oder **friend**.</span><span class="sxs-lookup"><span data-stu-id="2b546-111">Valid values are **private**, **public**, **protected**, **internal** or **friend**.</span></span> <span data-ttu-id="2b546-112">Für c#, Microsoft Visual Basic oder für VisualC++-komponentenerweiterungen (C++ / CX), können Sie den Zeichenfolgenwert "public" oder "Public"; der Parser die Groß-/Kleinschreibung für diesen Attributwert nicht erzwungen werden.</span><span class="sxs-lookup"><span data-stu-id="2b546-112">For C#, Microsoft Visual Basic or VisualC++ component extensions (C++/CX), you can give the string value "public" or "Public"; the parser doesn't enforce case on this attribute value.</span></span>

<span data-ttu-id="2b546-113">**Private**-Zugriff ist die Standardeinstellung.</span><span class="sxs-lookup"><span data-stu-id="2b546-113">**Private** access is the default.</span></span>

<span data-ttu-id="2b546-114">**x:FieldModifier** ist nur für Elemente mit einem [x:Name-Attribut](x-name-attribute.md) relevant, weil unter diesem Namen auf das Feld verwiesen wird, nachdem dieses den Zustand „public“ erreicht hat.</span><span class="sxs-lookup"><span data-stu-id="2b546-114">**x:FieldModifier** is only relevant for elements with an [x:Name attribute](x-name-attribute.md), because that name is used to reference the field once it is public.</span></span>

<span data-ttu-id="2b546-115">**Hinweis:** Windows-Runtime-XAML unterstützt keine **X: ClassModifier** oder **X: Unterklasse**.</span><span class="sxs-lookup"><span data-stu-id="2b546-115">**Note**Windows Runtime XAML doesn't support **x:ClassModifier** or **x:Subclass**.</span></span>

