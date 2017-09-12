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
# <a name="xdefaultbindmode-markup-extension"></a>{x:DefaultBindMode}-Markuperweiterung

\[ Aktualisiert für UWP-Apps unter Windows 10. Artikel zu Windows 8.x finden Sie unter [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]

Gibt in XAML-Markup einen Standardmodus für x:Bind an.

## <a name="xaml-attribute-usage"></a>XAML-Attributverwendung

``` syntax
<object x:DefaultBindMode="OneTime \| OneWay \| TwoWay" .../>
```

## <a name="remarks"></a>Hinweise

x:Bind verfügt über den Standardwert OneTime. Dieser wurde aus Leistungsgründen gewählt, da OneTime bewirkt, dass mehr Code generiert wird, um die Änderungserkennung zu verknüpfen und zu behandeln. **x:DefaultBindMode** kann verwendet werden, um für ein bestimmtes Segment der Markupstruktur den Standardmodus für x:Bind zu ändern. Der ausgewählte Modus gilt für alle x:Bind-Ausdrücke in diesem Element und seinen untergeordneten Elementen, die nicht explizit einen Bindungsmodus festlegen.

## <a name="related-topics"></a>Verwandte Themen

* [**x:Bind**](https://docs.microsoft.com/en-us/windows/uwp/xaml-platform/x-bind-markup-extension)
