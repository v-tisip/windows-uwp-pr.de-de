---
description: Gibt im XAML-Markup einen NULL-Wert für eine Eigenschaft an.
title: xNull-Markuperweiterung
ms.assetid: E6A4038E-4ADA-4E82-9824-582FC16AB037
ms.date: 02/08/2017
ms.topic: article
keywords: windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: f0d6fd8f194a3c9c98fb969034cab5a3e9e2f0de
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8885493"
---
# <a name="xnull-markup-extension"></a><span data-ttu-id="8d8d8-104">{x:Null}-Markuperweiterung</span><span class="sxs-lookup"><span data-stu-id="8d8d8-104">{x:Null} markup extension</span></span>


<span data-ttu-id="8d8d8-105">Gibt im XAML-Markup einen **NULL**-Wert für eine Eigenschaft an.</span><span class="sxs-lookup"><span data-stu-id="8d8d8-105">In XAML markup, specifies a **null** value for a property.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="8d8d8-106">XAML-Attributsyntax</span><span class="sxs-lookup"><span data-stu-id="8d8d8-106">XAML attribute usage</span></span>

``` syntax
<object property="{x:Null}" .../>
```

## <a name="remarks"></a><span data-ttu-id="8d8d8-107">Hinweise</span><span class="sxs-lookup"><span data-stu-id="8d8d8-107">Remarks</span></span>

<span data-ttu-id="8d8d8-108">**null** ist das Nullverweis-Schlüsselwort für C# und C++.</span><span class="sxs-lookup"><span data-stu-id="8d8d8-108">**null** is the null reference keyword for C# and C++.</span></span> <span data-ttu-id="8d8d8-109">Das Microsoft Visual Basic-Schlüsselwort für einen Nullverweis lautet **Nothing**.</span><span class="sxs-lookup"><span data-stu-id="8d8d8-109">The Microsoft Visual Basic keyword for a null reference is **Nothing**.</span></span>

<span data-ttu-id="8d8d8-110">Der anfängliche Standardwert kann zwischen Abhängigkeitseigenschaften variieren und ist nicht unbedingt **null**.</span><span class="sxs-lookup"><span data-stu-id="8d8d8-110">The initial default value can vary between dependency properties, and it is not necessarily **null**.</span></span> <span data-ttu-id="8d8d8-111">Viele Abhängigkeitseigenschaften akzeptieren **null** außerdem aufgrund ihrer internen Implementierung nicht als Wert (weder per Markup noch per Code).</span><span class="sxs-lookup"><span data-stu-id="8d8d8-111">Further, many dependency properties will not accept **null** as a value (whether through markup or code) due to their internal implementation.</span></span> <span data-ttu-id="8d8d8-112">In einem solchen Fall tritt unter Umständen eine Analyseausnahme auf, wenn ein XAML-Attributwert mit **{x:Null}** festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="8d8d8-112">In such cases, setting a XAML attribute value with **{x:Null}** can result in a parser exception.</span></span>

<span data-ttu-id="8d8d8-113">Einige Windows-Runtime-Typen akzeptieren NULL-Werte.</span><span class="sxs-lookup"><span data-stu-id="8d8d8-113">Some Windows Runtime types are nullable.</span></span> <span data-ttu-id="8d8d8-114">Sollte bei einem Typ, der NULL-Werte akzeptiert, **null** nicht bereits als Standardwert festgelegt sein, können Sie **{x:Null}** in XAML verwenden, um den **NULL**-Wert festzulegen.</span><span class="sxs-lookup"><span data-stu-id="8d8d8-114">In cases where a nullable type does not already have **null** as the default, you could use **{x:Null}** in XAML to set to the **null** value.</span></span> <span data-ttu-id="8d8d8-115">Bei Verwendung für VisualC++-komponentenerweiterungen (C++ / CX), Typen werden als [**Platform:: ibox<T>**](https://msdn.microsoft.com/library/windows/apps/xaml/jj606120.aspx).</span><span class="sxs-lookup"><span data-stu-id="8d8d8-115">If using VisualC++ component extensions (C++/CX), nullable types are represented as [**Platform::IBox<T>**](https://msdn.microsoft.com/library/windows/apps/xaml/jj606120.aspx).</span></span> <span data-ttu-id="8d8d8-116">In Microsoft .NET-Sprachen werden Typen, die NULL-Werte akzeptieren, mit [**Nullable<T>**](https://msdn.microsoft.com/library/windows/apps/xaml/b3h38hb0.aspx) angegeben.</span><span class="sxs-lookup"><span data-stu-id="8d8d8-116">If using Microsoft .NET languages, nullable types are represented as [**Nullable<T>**](https://msdn.microsoft.com/library/windows/apps/xaml/b3h38hb0.aspx).</span></span>

## <a name="related-topics"></a><span data-ttu-id="8d8d8-117">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="8d8d8-117">Related topics</span></span>

* [**<span data-ttu-id="8d8d8-118">Null-Wert</span><span class="sxs-lookup"><span data-stu-id="8d8d8-118">Nullable</span></span><T>**](https://msdn.microsoft.com/library/windows/apps/xaml/b3h38hb0.aspx)
* [**<span data-ttu-id="8d8d8-119">IReference</span><span class="sxs-lookup"><span data-stu-id="8d8d8-119">IReference</span></span><T>**](https://msdn.microsoft.com/library/windows/apps/br225864)
 

