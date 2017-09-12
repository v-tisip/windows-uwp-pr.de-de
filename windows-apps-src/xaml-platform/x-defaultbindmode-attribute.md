---
author: tbd
description: "Gibt in XAML-Markup einen Standardmodus für x:Bind an."
title: xDefaultBindMode-Markuperweiterung
ms.assetid: 
ms.author: 
ms.date: 
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 0fa037b4c59566cb1b9bacd4d2e36520a86c508d
ms.sourcegitcommit: ba0d20f6fad75ce98c25ceead78aab6661250571
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2017
---
# <a name="xdefaultbindmode-markup-extension"></a><span data-ttu-id="72d46-104">{x:DefaultBindMode}-Markuperweiterung</span><span class="sxs-lookup"><span data-stu-id="72d46-104">{x:DefaultBindMode} markup extension</span></span>

<span data-ttu-id="72d46-105">\[ Aktualisiert für UWP-Apps unter Windows 10.</span><span class="sxs-lookup"><span data-stu-id="72d46-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="72d46-106">Artikel zu Windows 8.x finden Sie unter [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span><span class="sxs-lookup"><span data-stu-id="72d46-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>

<span data-ttu-id="72d46-107">Gibt in XAML-Markup einen Standardmodus für x:Bind an.</span><span class="sxs-lookup"><span data-stu-id="72d46-107">In XAML markup, specifies a default mode for x:Bind.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="72d46-108">XAML-Attributverwendung</span><span class="sxs-lookup"><span data-stu-id="72d46-108">XAML attribute usage</span></span>

``` syntax
<object x:DefaultBindMode="OneTime \| OneWay \| TwoWay" .../>
```

## <a name="remarks"></a><span data-ttu-id="72d46-109">Hinweise</span><span class="sxs-lookup"><span data-stu-id="72d46-109">Remarks</span></span>

<span data-ttu-id="72d46-110">x:Bind verfügt über den Standardwert OneTime. Dieser wurde aus Leistungsgründen gewählt, da OneTime bewirkt, dass mehr Code generiert wird, um die Änderungserkennung zu verknüpfen und zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="72d46-110">x:Bind has a default mode of OneTime, and this was chosen for performance reasons as using OneTime will cause more code to be generated to hookup and handle the change detection.</span></span> <span data-ttu-id="72d46-111">**x:DefaultBindMode** kann verwendet werden, um für ein bestimmtes Segment der Markupstruktur den Standardmodus für x:Bind zu ändern.</span><span class="sxs-lookup"><span data-stu-id="72d46-111">**x:DefaultBindMode** can be used to change the default mode for x:Bind for a specific segment of the markup tree.</span></span> <span data-ttu-id="72d46-112">Der ausgewählte Modus gilt für alle x:Bind-Ausdrücke in diesem Element und seinen untergeordneten Elementen, die nicht explizit einen Bindungsmodus festlegen.</span><span class="sxs-lookup"><span data-stu-id="72d46-112">The mode selected will apply any x:Bind expressions on that element and its children, that do not explicitly specify a mode as part of the binding.</span></span>

## <a name="related-topics"></a><span data-ttu-id="72d46-113">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="72d46-113">Related topics</span></span>

* [**<span data-ttu-id="72d46-114">x:Bind</span><span class="sxs-lookup"><span data-stu-id="72d46-114">x:Bind</span></span>**](https://docs.microsoft.com/en-us/windows/uwp/xaml-platform/x-bind-markup-extension)
