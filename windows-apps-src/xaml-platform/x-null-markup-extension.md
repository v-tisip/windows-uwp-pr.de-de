---
description: Gibt im XAML-Markup einen NULL-Wert für eine Eigenschaft an.
title: xNull-Markuperweiterung
ms.assetid: E6A4038E-4ADA-4E82-9824-582FC16AB037
ms.date: 02/08/2017
ms.topic: article
keywords: windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: f0d6fd8f194a3c9c98fb969034cab5a3e9e2f0de
ms.sourcegitcommit: d7613c791107f74b6a3dc12a372d9de916c0454b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8741075"
---
# <a name="xnull-markup-extension"></a><span data-ttu-id="92e84-104">{x:Null}-Markuperweiterung</span><span class="sxs-lookup"><span data-stu-id="92e84-104">{x:Null} markup extension</span></span>


<span data-ttu-id="92e84-105">Gibt im XAML-Markup einen **NULL**-Wert für eine Eigenschaft an.</span><span class="sxs-lookup"><span data-stu-id="92e84-105">In XAML markup, specifies a **null** value for a property.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="92e84-106">XAML-Attributsyntax</span><span class="sxs-lookup"><span data-stu-id="92e84-106">XAML attribute usage</span></span>

``` syntax
<object property="{x:Null}" .../>
```

## <a name="remarks"></a><span data-ttu-id="92e84-107">Hinweise</span><span class="sxs-lookup"><span data-stu-id="92e84-107">Remarks</span></span>

<span data-ttu-id="92e84-108">**null** ist das Nullverweis-Schlüsselwort für C# und C++.</span><span class="sxs-lookup"><span data-stu-id="92e84-108">**null** is the null reference keyword for C# and C++.</span></span> <span data-ttu-id="92e84-109">Das Microsoft Visual Basic-Schlüsselwort für einen Nullverweis lautet **Nothing**.</span><span class="sxs-lookup"><span data-stu-id="92e84-109">The Microsoft Visual Basic keyword for a null reference is **Nothing**.</span></span>

<span data-ttu-id="92e84-110">Der anfängliche Standardwert kann zwischen Abhängigkeitseigenschaften variieren und ist nicht unbedingt **null**.</span><span class="sxs-lookup"><span data-stu-id="92e84-110">The initial default value can vary between dependency properties, and it is not necessarily **null**.</span></span> <span data-ttu-id="92e84-111">Viele Abhängigkeitseigenschaften akzeptieren **null** außerdem aufgrund ihrer internen Implementierung nicht als Wert (weder per Markup noch per Code).</span><span class="sxs-lookup"><span data-stu-id="92e84-111">Further, many dependency properties will not accept **null** as a value (whether through markup or code) due to their internal implementation.</span></span> <span data-ttu-id="92e84-112">In einem solchen Fall tritt unter Umständen eine Analyseausnahme auf, wenn ein XAML-Attributwert mit **{x:Null}** festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="92e84-112">In such cases, setting a XAML attribute value with **{x:Null}** can result in a parser exception.</span></span>

<span data-ttu-id="92e84-113">Einige Windows-Runtime-Typen akzeptieren NULL-Werte.</span><span class="sxs-lookup"><span data-stu-id="92e84-113">Some Windows Runtime types are nullable.</span></span> <span data-ttu-id="92e84-114">Sollte bei einem Typ, der NULL-Werte akzeptiert, **null** nicht bereits als Standardwert festgelegt sein, können Sie **{x:Null}** in XAML verwenden, um den **NULL**-Wert festzulegen.</span><span class="sxs-lookup"><span data-stu-id="92e84-114">In cases where a nullable type does not already have **null** as the default, you could use **{x:Null}** in XAML to set to the **null** value.</span></span> <span data-ttu-id="92e84-115">Wenn für VisualC++-komponentenerweiterungen (C++ / CX), Typen werden als [**Platform:: ibox<T>**](https://msdn.microsoft.com/library/windows/apps/xaml/jj606120.aspx).</span><span class="sxs-lookup"><span data-stu-id="92e84-115">If using VisualC++ component extensions (C++/CX), nullable types are represented as [**Platform::IBox<T>**](https://msdn.microsoft.com/library/windows/apps/xaml/jj606120.aspx).</span></span> <span data-ttu-id="92e84-116">In Microsoft .NET-Sprachen werden Typen, die NULL-Werte akzeptieren, mit [**Nullable<T>**](https://msdn.microsoft.com/library/windows/apps/xaml/b3h38hb0.aspx) angegeben.</span><span class="sxs-lookup"><span data-stu-id="92e84-116">If using Microsoft .NET languages, nullable types are represented as [**Nullable<T>**](https://msdn.microsoft.com/library/windows/apps/xaml/b3h38hb0.aspx).</span></span>

## <a name="related-topics"></a><span data-ttu-id="92e84-117">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="92e84-117">Related topics</span></span>

* [**<span data-ttu-id="92e84-118">Null-Wert</span><span class="sxs-lookup"><span data-stu-id="92e84-118">Nullable</span></span><T>**](https://msdn.microsoft.com/library/windows/apps/xaml/b3h38hb0.aspx)
* [**<span data-ttu-id="92e84-119">IReference</span><span class="sxs-lookup"><span data-stu-id="92e84-119">IReference</span></span><T>**](https://msdn.microsoft.com/library/windows/apps/br225864)
 

