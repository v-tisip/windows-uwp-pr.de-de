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
ms.sourcegitcommit: 6cc275f2151f78db40c11ace381ee2d35f0155f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5565824"
---
# <a name="xdefaultbindmode-attribute"></a>x:DefaultBindMode-Attribut

Gibt in XAML-Markup einen Standardmodus für x:Bind an.

**x:DefaultBindMode** ist ab Windows10, Version 1607 (Anniversary Update), SDK-Version 14393, verfügbar.

## <a name="xaml-attribute-usage"></a>XAML-Attributverwendung

``` syntax
<object x:DefaultBindMode="OneTime \| OneWay \| TwoWay" .../>
```

## <a name="remarks"></a>Hinweise

[x:Bind](x-bind-markup-extension.md) verfügt über den Standardmodus **OneTime**. Diese wurde aus Leistungsgründen so gewählt, da **OneWay** bewirkt, dass mehr Code generiert wird, um die Änderungserkennung zu verknüpfen und zu behandeln. Sie können **x:DefaultBindMode** verwenden, um für ein bestimmtes Segment der Markupstruktur den Standardmodus für x:Bind zu ändern. Der angegebene Modus gilt für alle x:Bind-Ausdrücke in diesem Element und seinen untergeordneten Elementen, die nicht explizit einen Bindungsmodus festlegen.

## <a name="related-topics"></a>Verwandte Themen

* [x:Bind-Markuperweiterung](x-bind-markup-extension.md)
