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
ms.sourcegitcommit: cbe7cf620622a5e4df7414f9e38dfecec1cfca99
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "7441778"
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

