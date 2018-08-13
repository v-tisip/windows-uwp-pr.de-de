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
# <a name="xfieldmodifier-attribute"></a>x:FieldModifier-Attribut

\[ Aktualisiert für UWP-Apps unter Windows10. Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]

Ändert das XAML-Kompilierungsverhalten, sodass Felder für Verweise auf benannte Objekte mit **öffentlichem** Zugriff definiert werden und nicht das **private** Standardverhalten aufweisen.

## <a name="xaml-attribute-usage"></a>XAML-Attributsyntax

``` syntax
<object x:FieldModifier="public".../>
```

## <a name="dependencies"></a>Abhängigkeiten

[x:Name-Attribut](x-name-attribute.md) muss in demselben Element ebenfalls bereitgestellt werden.

## <a name="remarks"></a>Hinweise

Der Wert für das **x:FieldModifier**-Attribut variiert je nach Programmiersprache. Gültige Werte sind **private**, **public**, **protected**, **internal** oder **friend**. Für C#-, Microsoft Visual Basic- oder VisualC++-Komponentenerweiterungen (C++/CX) können Sie den Zeichenfolgenwert „public“ oder „Public“ angeben. Vom Parser wird die Groß-/Kleinschreibung für diesen Attributwert nicht berücksichtigt.

**Private**-Zugriff ist die Standardeinstellung.

**x:FieldModifier** ist nur für Elemente mit einem [x:Name-Attribut](x-name-attribute.md) relevant, weil unter diesem Namen auf das Feld verwiesen wird, nachdem dieses den Zustand „public“ erreicht hat.

**Hinweis**  Windows-Runtime-XAML unterstützt weder **x:ClassModifier** noch **x:Subclass**.

