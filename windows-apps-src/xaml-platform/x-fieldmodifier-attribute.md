---
author: jwmsft
description: Ändert das XAML-Kompilierungsverhalten, sodass Felder für Verweise auf benannte Objekte mit öffentlichem Zugriff definiert werden und nicht das private Standardverhalten aufweisen.
title: xFieldModifier-Attribut
ms.assetid: 6FBCC00B-848D-4454-8B1F-287CA8406DDF
ms.author: jimwalk
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.openlocfilehash: cad84be24836bc6a33a4ab08f1ca4fa2d9e97512
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
ms.translationtype: MT
ms.contentlocale: de-DE
ms.locfileid: "235011"
---
# <a name="xfieldmodifier-attribute"></a><span data-ttu-id="db53e-104">x:FieldModifier-Attribut</span><span class="sxs-lookup"><span data-stu-id="db53e-104">x:FieldModifier attribute</span></span>

<span data-ttu-id="db53e-105">\[ Aktualisiert für UWP-Apps unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="db53e-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="db53e-106">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span><span class="sxs-lookup"><span data-stu-id="db53e-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>

<span data-ttu-id="db53e-107">Ändert das XAML-Kompilierungsverhalten, sodass Felder für Verweise auf benannte Objekte mit **öffentlichem** Zugriff definiert werden und nicht das **private** Standardverhalten aufweisen.</span><span class="sxs-lookup"><span data-stu-id="db53e-107">Modifies XAML compilation behavior, such that fields for named object references are defined with **public** access rather than the **private** default behavior.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="db53e-108">XAML-Attributsyntax</span><span class="sxs-lookup"><span data-stu-id="db53e-108">XAML attribute usage</span></span>

``` syntax
<object x:FieldModifier="public".../>
```

## <a name="dependencies"></a><span data-ttu-id="db53e-109">Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="db53e-109">Dependencies</span></span>

<span data-ttu-id="db53e-110">[x:Name-Attribut](x-name-attribute.md) muss in demselben Element ebenfalls bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="db53e-110">[x:Name attribute](x-name-attribute.md) must also be provided on the same element.</span></span>

## <a name="remarks"></a><span data-ttu-id="db53e-111">Hinweise</span><span class="sxs-lookup"><span data-stu-id="db53e-111">Remarks</span></span>

<span data-ttu-id="db53e-112">Der Wert für das **x:FieldModifier**-Attribut variiert je nach Programmiersprache.</span><span class="sxs-lookup"><span data-stu-id="db53e-112">The value for the **x:FieldModifier** attribute will vary by programming language.</span></span> <span data-ttu-id="db53e-113">Gültige Werte sind **private**, **public**, **protected**, **internal** oder **friend**.</span><span class="sxs-lookup"><span data-stu-id="db53e-113">Valid values are **private**, **public**, **protected**, **internal** or **friend**.</span></span> <span data-ttu-id="db53e-114">Für C#-, Microsoft Visual Basic- oder VisualC++-Komponentenerweiterungen (C++/CX) können Sie den Zeichenfolgenwert „public“ oder „Public“ angeben. Vom Parser wird die Groß-/Kleinschreibung für diesen Attributwert nicht berücksichtigt.</span><span class="sxs-lookup"><span data-stu-id="db53e-114">For C#, Microsoft Visual Basic or Visual C++ component extensions (C++/CX), you can give the string value "public" or "Public"; the parser doesn't enforce case on this attribute value.</span></span>

<span data-ttu-id="db53e-115">**Private**-Zugriff ist die Standardeinstellung.</span><span class="sxs-lookup"><span data-stu-id="db53e-115">**Private** access is the default.</span></span>

<span data-ttu-id="db53e-116">**x:FieldModifier** ist nur für Elemente mit einem [x:Name-Attribut](x-name-attribute.md) relevant, weil unter diesem Namen auf das Feld verwiesen wird, nachdem dieses den Zustand „public“ erreicht hat.</span><span class="sxs-lookup"><span data-stu-id="db53e-116">**x:FieldModifier** is only relevant for elements with an [x:Name attribute](x-name-attribute.md), because that name is used to reference the field once it is public.</span></span>

<span data-ttu-id="db53e-117">**Hinweis**  Windows-Runtime-XAML unterstützt weder **x:ClassModifier** noch **x:Subclass**.</span><span class="sxs-lookup"><span data-stu-id="db53e-117">**Note**  Windows Runtime XAML doesn't support **x:ClassModifier** or **x:Subclass**.</span></span>

