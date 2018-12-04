---
description: Gibt in XAML-Markup einen Standardmodus für x:Bind an.
title: xDefaultBindMode-Attribut
ms.date: 02/08/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: c8917b09f04206a5466797f48414defeb35baf5e
ms.sourcegitcommit: b4c502d69a13340f6e3c887aa3c26ef2aeee9cee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "8461389"
---
# <a name="xdefaultbindmode-attribute"></a><span data-ttu-id="a755e-104">x:DefaultBindMode-Attribut</span><span class="sxs-lookup"><span data-stu-id="a755e-104">x:DefaultBindMode attribute</span></span>

<span data-ttu-id="a755e-105">Gibt in XAML-Markup einen Standardmodus für x:Bind an.</span><span class="sxs-lookup"><span data-stu-id="a755e-105">In XAML markup, specifies a default mode for x:Bind.</span></span>

<span data-ttu-id="a755e-106">**x:DefaultBindMode** ist ab Windows10, Version 1607 (Anniversary Update), SDK-Version 14393, verfügbar.</span><span class="sxs-lookup"><span data-stu-id="a755e-106">**x:DefaultBindMode** is available starting in Windows 10, version 1607 (Anniversary Update), SDK version 14393.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="a755e-107">XAML-Attributverwendung</span><span class="sxs-lookup"><span data-stu-id="a755e-107">XAML attribute usage</span></span>

``` syntax
<object x:DefaultBindMode="OneTime \| OneWay \| TwoWay" .../>
```

## <a name="remarks"></a><span data-ttu-id="a755e-108">Hinweise</span><span class="sxs-lookup"><span data-stu-id="a755e-108">Remarks</span></span>

<span data-ttu-id="a755e-109">[x:Bind](x-bind-markup-extension.md) verfügt über den Standardmodus **OneTime**.</span><span class="sxs-lookup"><span data-stu-id="a755e-109">[x:Bind](x-bind-markup-extension.md) has a default mode of **OneTime**.</span></span> <span data-ttu-id="a755e-110">Diese wurde aus Leistungsgründen so gewählt, da **OneWay** bewirkt, dass mehr Code generiert wird, um die Änderungserkennung zu verknüpfen und zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="a755e-110">This was chosen for performance reasons, as using **OneWay** causes more code to be generated to hookup and handle change detection.</span></span> <span data-ttu-id="a755e-111">Sie können **x:DefaultBindMode** verwenden, um für ein bestimmtes Segment der Markupstruktur den Standardmodus für x:Bind zu ändern.</span><span class="sxs-lookup"><span data-stu-id="a755e-111">You can use **x:DefaultBindMode** to change the default mode for x:Bind for a specific segment of the markup tree.</span></span> <span data-ttu-id="a755e-112">Der angegebene Modus gilt für alle x:Bind-Ausdrücke in diesem Element und seinen untergeordneten Elementen, die nicht explizit einen Bindungsmodus festlegen.</span><span class="sxs-lookup"><span data-stu-id="a755e-112">The specified mode applies to any x:Bind expressions on that element and its children, that do not explicitly specify a mode as part of the binding.</span></span>

## <a name="related-topics"></a><span data-ttu-id="a755e-113">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="a755e-113">Related topics</span></span>

* [<span data-ttu-id="a755e-114">x:Bind-Markuperweiterung</span><span class="sxs-lookup"><span data-stu-id="a755e-114">x:Bind markup extension</span></span>](x-bind-markup-extension.md)
