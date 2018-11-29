---
description: Gibt im XAML-Markup einen NULL-Wert für eine Eigenschaft an.
title: xNull-Markuperweiterung
ms.assetid: E6A4038E-4ADA-4E82-9824-582FC16AB037
ms.date: 02/08/2017
ms.topic: article
keywords: windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: f0d6fd8f194a3c9c98fb969034cab5a3e9e2f0de
ms.sourcegitcommit: b5c9c18e70625ab770946b8243f3465ee1013184
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "7981034"
---
# <a name="xnull-markup-extension"></a>{x:Null}-Markuperweiterung


Gibt im XAML-Markup einen **NULL**-Wert für eine Eigenschaft an.

## <a name="xaml-attribute-usage"></a>XAML-Attributsyntax

``` syntax
<object property="{x:Null}" .../>
```

## <a name="remarks"></a>Hinweise

**null** ist das Nullverweis-Schlüsselwort für C# und C++. Das Microsoft Visual Basic-Schlüsselwort für einen Nullverweis lautet **Nothing**.

Der anfängliche Standardwert kann zwischen Abhängigkeitseigenschaften variieren und ist nicht unbedingt **null**. Viele Abhängigkeitseigenschaften akzeptieren **null** außerdem aufgrund ihrer internen Implementierung nicht als Wert (weder per Markup noch per Code). In einem solchen Fall tritt unter Umständen eine Analyseausnahme auf, wenn ein XAML-Attributwert mit **{x:Null}** festgelegt wird.

Einige Windows-Runtime-Typen akzeptieren NULL-Werte. Sollte bei einem Typ, der NULL-Werte akzeptiert, **null** nicht bereits als Standardwert festgelegt sein, können Sie **{x:Null}** in XAML verwenden, um den **NULL**-Wert festzulegen. Wenn für VisualC++-komponentenerweiterungen (C++ / CX), Typen werden als [**Platform:: ibox<T>**](https://msdn.microsoft.com/library/windows/apps/xaml/jj606120.aspx). In Microsoft .NET-Sprachen werden Typen, die NULL-Werte akzeptieren, mit [**Nullable<T>**](https://msdn.microsoft.com/library/windows/apps/xaml/b3h38hb0.aspx) angegeben.

## <a name="related-topics"></a>Verwandte Themen

* [**Null-Wert<T>**](https://msdn.microsoft.com/library/windows/apps/xaml/b3h38hb0.aspx)
* [**IReference<T>**](https://msdn.microsoft.com/library/windows/apps/br225864)
 

