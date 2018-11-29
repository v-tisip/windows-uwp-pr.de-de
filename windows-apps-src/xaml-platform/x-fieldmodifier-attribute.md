---
description: Ändert das XAML-Kompilierungsverhalten, sodass Felder für Verweise auf benannte Objekte mit öffentlichem Zugriff definiert werden und nicht das private Standardverhalten aufweisen.
title: xFieldModifier-Attribut
ms.assetid: 6FBCC00B-848D-4454-8B1F-287CA8406DDF
ms.date: 02/08/2017
ms.topic: article
keywords: windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 751cda36fc58d0e6add9204327a74ec947c9fc53
ms.sourcegitcommit: 89ff8ff88ef58f4fe6d3b1368fe94f62e59118ad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/29/2018
ms.locfileid: "8199725"
---
# <a name="xfieldmodifier-attribute"></a>x:FieldModifier-Attribut


Ändert das XAML-Kompilierungsverhalten, sodass Felder für Verweise auf benannte Objekte mit **öffentlichem** Zugriff definiert werden und nicht das **private** Standardverhalten aufweisen.

## <a name="xaml-attribute-usage"></a>XAML-Attributsyntax

``` syntax
<object x:FieldModifier="public".../>
```

## <a name="dependencies"></a>Abhängigkeiten

[x:Name-Attribut](x-name-attribute.md) muss in demselben Element ebenfalls bereitgestellt werden.

## <a name="remarks"></a>Hinweise

Der Wert für das **x:FieldModifier**-Attribut variiert je nach Programmiersprache. Gültige Werte sind **private**, **public**, **protected**, **internal** oder **friend**. Für c#, Microsoft Visual Basic oder für VisualC++-komponentenerweiterungen (C++ / CX), können Sie den Zeichenfolgenwert "public" oder "Public"; der Parser die Groß-/Kleinschreibung für diesen Attributwert nicht erzwungen werden.

**Private**-Zugriff ist die Standardeinstellung.

**x:FieldModifier** ist nur für Elemente mit einem [x:Name-Attribut](x-name-attribute.md) relevant, weil unter diesem Namen auf das Feld verwiesen wird, nachdem dieses den Zustand „public“ erreicht hat.

**Hinweis:** Windows-Runtime-XAML unterstützt keine **X: ClassModifier** oder **X: Unterklasse**.

