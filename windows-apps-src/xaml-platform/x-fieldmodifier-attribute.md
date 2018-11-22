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
ms.sourcegitcommit: 93c0a60cf531c7d9fe7b00e7cf78df86906f9d6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2018
ms.locfileid: "7565773"
---
# <a name="xfieldmodifier-attribute"></a><span data-ttu-id="47871-104">x:FieldModifier-Attribut</span><span class="sxs-lookup"><span data-stu-id="47871-104">x:FieldModifier attribute</span></span>


<span data-ttu-id="47871-105">Ändert das XAML-Kompilierungsverhalten, sodass Felder für Verweise auf benannte Objekte mit **öffentlichem** Zugriff definiert werden und nicht das **private** Standardverhalten aufweisen.</span><span class="sxs-lookup"><span data-stu-id="47871-105">Modifies XAML compilation behavior, such that fields for named object references are defined with **public** access rather than the **private** default behavior.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="47871-106">XAML-Attributsyntax</span><span class="sxs-lookup"><span data-stu-id="47871-106">XAML attribute usage</span></span>

``` syntax
<object x:FieldModifier="public".../>
```

## <a name="dependencies"></a><span data-ttu-id="47871-107">Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="47871-107">Dependencies</span></span>

<span data-ttu-id="47871-108">[x:Name-Attribut](x-name-attribute.md) muss in demselben Element ebenfalls bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="47871-108">[x:Name attribute](x-name-attribute.md) must also be provided on the same element.</span></span>

## <a name="remarks"></a><span data-ttu-id="47871-109">Hinweise</span><span class="sxs-lookup"><span data-stu-id="47871-109">Remarks</span></span>

<span data-ttu-id="47871-110">Der Wert für das **x:FieldModifier**-Attribut variiert je nach Programmiersprache.</span><span class="sxs-lookup"><span data-stu-id="47871-110">The value for the **x:FieldModifier** attribute will vary by programming language.</span></span> <span data-ttu-id="47871-111">Gültige Werte sind **private**, **public**, **protected**, **internal** oder **friend**.</span><span class="sxs-lookup"><span data-stu-id="47871-111">Valid values are **private**, **public**, **protected**, **internal** or **friend**.</span></span> <span data-ttu-id="47871-112">Für c#, Microsoft Visual Basic oder für VisualC++-komponentenerweiterungen (C++ / CX), können Sie den Zeichenfolgenwert "public" oder "Public"; der Parser die Groß-/Kleinschreibung für diesen Attributwert nicht erzwungen werden.</span><span class="sxs-lookup"><span data-stu-id="47871-112">For C#, Microsoft Visual Basic or VisualC++ component extensions (C++/CX), you can give the string value "public" or "Public"; the parser doesn't enforce case on this attribute value.</span></span>

<span data-ttu-id="47871-113">**Private**-Zugriff ist die Standardeinstellung.</span><span class="sxs-lookup"><span data-stu-id="47871-113">**Private** access is the default.</span></span>

<span data-ttu-id="47871-114">**x:FieldModifier** ist nur für Elemente mit einem [x:Name-Attribut](x-name-attribute.md) relevant, weil unter diesem Namen auf das Feld verwiesen wird, nachdem dieses den Zustand „public“ erreicht hat.</span><span class="sxs-lookup"><span data-stu-id="47871-114">**x:FieldModifier** is only relevant for elements with an [x:Name attribute](x-name-attribute.md), because that name is used to reference the field once it is public.</span></span>

<span data-ttu-id="47871-115">**Hinweis:** Windows-Runtime-XAML unterstützt keine **X: ClassModifier** oder **X: Unterklasse**.</span><span class="sxs-lookup"><span data-stu-id="47871-115">**Note**Windows Runtime XAML doesn't support **x:ClassModifier** or **x:Subclass**.</span></span>

