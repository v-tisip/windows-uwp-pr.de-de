---
author: jwmsft
description: Gibt in XAML-Markup einen Standardmodus für x:Bind an.
title: xDefaultBindMode-Attribut
ms.author: jimwalk
ms.date: 02/08/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 2696cb46591757421795b15083ea7fdab54943c5
ms.sourcegitcommit: e38b334edb82bf2b1474ba686990f4299b8f59c7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6851664"
---
# <a name="xdefaultbindmode-attribute"></a><span data-ttu-id="59058-104">x:DefaultBindMode-Attribut</span><span class="sxs-lookup"><span data-stu-id="59058-104">x:DefaultBindMode attribute</span></span>

<span data-ttu-id="59058-105">Gibt in XAML-Markup einen Standardmodus für x:Bind an.</span><span class="sxs-lookup"><span data-stu-id="59058-105">In XAML markup, specifies a default mode for x:Bind.</span></span>

<span data-ttu-id="59058-106">**x:DefaultBindMode** ist ab Windows10, Version 1607 (Anniversary Update), SDK-Version 14393, verfügbar.</span><span class="sxs-lookup"><span data-stu-id="59058-106">**x:DefaultBindMode** is available starting in Windows 10, version 1607 (Anniversary Update), SDK version 14393.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="59058-107">XAML-Attributverwendung</span><span class="sxs-lookup"><span data-stu-id="59058-107">XAML attribute usage</span></span>

``` syntax
<object x:DefaultBindMode="OneTime \| OneWay \| TwoWay" .../>
```

## <a name="remarks"></a><span data-ttu-id="59058-108">Hinweise</span><span class="sxs-lookup"><span data-stu-id="59058-108">Remarks</span></span>

<span data-ttu-id="59058-109">[x:Bind](x-bind-markup-extension.md) verfügt über den Standardmodus **OneTime**.</span><span class="sxs-lookup"><span data-stu-id="59058-109">[x:Bind](x-bind-markup-extension.md) has a default mode of **OneTime**.</span></span> <span data-ttu-id="59058-110">Diese wurde aus Leistungsgründen so gewählt, da **OneWay** bewirkt, dass mehr Code generiert wird, um die Änderungserkennung zu verknüpfen und zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="59058-110">This was chosen for performance reasons, as using **OneWay** causes more code to be generated to hookup and handle change detection.</span></span> <span data-ttu-id="59058-111">Sie können **x:DefaultBindMode** verwenden, um für ein bestimmtes Segment der Markupstruktur den Standardmodus für x:Bind zu ändern.</span><span class="sxs-lookup"><span data-stu-id="59058-111">You can use **x:DefaultBindMode** to change the default mode for x:Bind for a specific segment of the markup tree.</span></span> <span data-ttu-id="59058-112">Der angegebene Modus gilt für alle x:Bind-Ausdrücke in diesem Element und seinen untergeordneten Elementen, die nicht explizit einen Bindungsmodus festlegen.</span><span class="sxs-lookup"><span data-stu-id="59058-112">The specified mode applies to any x:Bind expressions on that element and its children, that do not explicitly specify a mode as part of the binding.</span></span>

## <a name="related-topics"></a><span data-ttu-id="59058-113">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="59058-113">Related topics</span></span>

* [<span data-ttu-id="59058-114">x:Bind-Markuperweiterung</span><span class="sxs-lookup"><span data-stu-id="59058-114">x:Bind markup extension</span></span>](x-bind-markup-extension.md)
