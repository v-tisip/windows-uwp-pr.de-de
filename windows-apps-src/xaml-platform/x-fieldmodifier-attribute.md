---
author: jwmsft
description: "Ändert das XAML-Kompilierungsverhalten, sodass Felder für Verweise auf benannte Objekte mit öffentlichem Zugriff definiert werden und nicht das private Standardverhalten aufweisen."
title: xFieldModifier-Attribut
ms.assetid: 6FBCC00B-848D-4454-8B1F-287CA8406DDF
ms.author: jimwalk
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "windows 10, UWP"
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: 2c1bf910303f0c26761a3c63c3e1159dd2d0c6bb
ms.lasthandoff: 02/07/2017

---

# <a name="xfieldmodifier-attribute"></a>x:FieldModifier-Attribut

\[ Aktualisiert für UWP-Apps unter Windows 10. Artikel zu Windows 8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]

Ändert das XAML-Kompilierungsverhalten, sodass Felder für Verweise auf benannte Objekte mit **öffentlichem** Zugriff definiert werden und nicht das **private** Standardverhalten aufweisen.

## <a name="xaml-attribute-usage"></a>XAML-Attributsyntax

``` syntax
<object x:FieldModifier="public".../>
```

## <a name="dependencies"></a>Abhängigkeiten

[x:Name-Attribut](x-name-attribute.md) muss in demselben Element ebenfalls bereitgestellt werden.

## <a name="remarks"></a>Hinweise

Der Wert für das **x:FieldModifier**-Attribut variiert je nach Programmiersprache. Gültige Werte sind **private**, **public**, **protected**, **internal** oder **friend**. Für C#-, Microsoft Visual Basic- oder Visual C++-Komponentenerweiterungen (C++/CX) können Sie den Zeichenfolgenwert „public“ oder „Public“ angeben. Vom Parser wird die Groß-/Kleinschreibung für diesen Attributwert nicht berücksichtigt.

**Private**-Zugriff ist die Standardeinstellung.

**x:FieldModifier** ist nur für Elemente mit einem [x:Name-Attribut](x-name-attribute.md) relevant, weil unter diesem Namen auf das Feld verwiesen wird, nachdem dieses den Zustand „public“ erreicht hat.

**Hinweis**  Windows-Runtime-XAML unterstützt weder **x:ClassModifier** noch **x:Subclass**.


