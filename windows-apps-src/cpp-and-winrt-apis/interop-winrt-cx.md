---
author: stevewhims
description: In diesem Thema werden zwei Hilfsfunktionen gezeigt, die verwendet werden können, um zwischen C++ / CX- und C++ / WinRT-Objekten zu konvertieren.
title: Interoperabilität zwischen C++/WinRT und C++/CX
ms.author: stwhi
ms.date: 05/21/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp, standard, c++, cpp, winrt, projizierung, portieren, migrieren, interoperabilität, C++/CX
ms.localizationpriority: medium
ms.openlocfilehash: b60b0d7c201f172261de1546fc250e40b8cd670f
ms.sourcegitcommit: e16c9845b52d5bd43fc02bbe92296a9682d96926
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2018
ms.locfileid: "4950588"
---
# <a name="interop-between-cwinrt-and-ccx"></a><span data-ttu-id="d62de-104">Interoperabilität zwischen C++/WinRT und C++/CX</span><span class="sxs-lookup"><span data-stu-id="d62de-104">Interop between C++/WinRT and C++/CX</span></span>
<span data-ttu-id="d62de-105">In diesem Thema werden zwei Hilfsfunktionen gezeigt, die verwendet werden können, für die Konvertierung zwischen [C++ / CX](/cpp/cppcx/visual-c-language-reference-c-cx?branch=live) und [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) Objekte.</span><span class="sxs-lookup"><span data-stu-id="d62de-105">This topic shows two helper functions that can be used to convert between [C++/CX](/cpp/cppcx/visual-c-language-reference-c-cx?branch=live) and [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) objects.</span></span> <span data-ttu-id="d62de-106">Sie verwenden, um Interoperabilität zwischen Code, der die beiden sprachprojektionen verwendet, oder Sie können die Funktionen verwenden, wie Sie Ihren Code schrittweise von C++ verschieben / CX nach C++ / WinRT (siehe [Wechsel zu C++ / WinRT von C++ / CX](move-to-winrt-from-cx.md)).</span><span class="sxs-lookup"><span data-stu-id="d62de-106">You can use them to interop between code that uses the two language projections, or you can use the functions as you gradually move your code from C++/CX to C++/WinRT (see [Move to C++/WinRT from C++/CX](move-to-winrt-from-cx.md)).</span></span>

## <a name="fromcx-and-tocx-functions"></a><span data-ttu-id="d62de-107">Funktionen from_cx und to_cx</span><span class="sxs-lookup"><span data-stu-id="d62de-107">from_cx and to_cx functions</span></span>
<span data-ttu-id="d62de-108">Die folgende Hilfsfunktion konvertiert ein C++/CX-Objekt in ein äquivalentes C++/WinRT-Objekt.</span><span class="sxs-lookup"><span data-stu-id="d62de-108">The helper function below converts a C++/CX object to an equivalent C++/WinRT object.</span></span> <span data-ttu-id="d62de-109">Die Funktion bildet ein C++/CX-Objekt auf den zugrundeliegenden [**IUnknown**](https://msdn.microsoft.com/library/windows/desktop/ms680509) Schnittstellenzeiger ab.</span><span class="sxs-lookup"><span data-stu-id="d62de-109">The function casts a C++/CX object to its underlying [**IUnknown**](https://msdn.microsoft.com/library/windows/desktop/ms680509) interface pointer.</span></span> <span data-ttu-id="d62de-110">Sie ruft dann [**QueryInterface**](https://msdn.microsoft.com/library/windows/desktop/ms682521) auf diesem Zeiger auf, um de Standardschnittstelle des C++/WinRT-Objekts abzurufen.</span><span class="sxs-lookup"><span data-stu-id="d62de-110">It then calls [**QueryInterface**](https://msdn.microsoft.com/library/windows/desktop/ms682521) on that pointer to query for the default interface of the C++/WinRT object.</span></span> <span data-ttu-id="d62de-111">**QueryInterface** ist das Windows-Runtime Application Binary Interface (ABI) Äquivalent zur safe_cast-Erweiterung von C++/CX.</span><span class="sxs-lookup"><span data-stu-id="d62de-111">**QueryInterface** is the Windows Runtime application binary interface (ABI) equivalent of the C++/CX safe_cast extension.</span></span> <span data-ttu-id="d62de-112">Und die Funktion [**winrt::put_abi**](/uwp/cpp-ref-for-winrt/put-abi) ermittelt die Adresse des zugrundeliegenden **IUnknown**-Schnittstellenzeiger eines C++/WinRT-Objekts, sodass er auf einen anderen Wert gesetzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="d62de-112">And, the [**winrt::put_abi**](/uwp/cpp-ref-for-winrt/put-abi) function retrieves the address of a C++/WinRT object's underlying **IUnknown** interface pointer so that it can be set to another value.</span></span>

```cppwinrt
template <typename T>
T from_cx(Platform::Object^ from)
{
    T to{ nullptr };

    winrt::check_hresult(reinterpret_cast<::IUnknown*>(from)
        ->QueryInterface(winrt::guid_of<T>(),
            reinterpret_cast<void**>(winrt::put_abi(to))));

    return to;
}
```

<span data-ttu-id="d62de-113">Die folgende Hilfsfunktion konvertiert ein C++/WinRT-Objekt in ein äquivalentes C++/CX-Objekt.</span><span class="sxs-lookup"><span data-stu-id="d62de-113">The helper function below converts a C++/WinRT object to an equivalent C++/CX object.</span></span> <span data-ttu-id="d62de-114">Die Funktion [**winrt::get_abi**](/uwp/cpp-ref-for-winrt/get-abi) liefert einen Zeiger auf die **IUnknown**-Schnittstelle eines C++/WinRT-Objekts.</span><span class="sxs-lookup"><span data-stu-id="d62de-114">The [**winrt::get_abi**](/uwp/cpp-ref-for-winrt/get-abi) function retrieves a pointer to a C++/WinRT object's underlying **IUnknown** interface.</span></span> <span data-ttu-id="d62de-115">Die Funktion bildet diesen Zeiger auf ein C++/CX-Objekt ab, bevor sie die safe_cast-Erweiterung von C++/CX verwendet, um den gewünschten C++/CX-Typ abzufragen.</span><span class="sxs-lookup"><span data-stu-id="d62de-115">The function casts that pointer to a C++/CX object before using the C++/CX safe_cast extension to query for the requested C++/CX type.</span></span>

```cppwinrt
template <typename T>
T^ to_cx(winrt::Windows::Foundation::IUnknown const& from)
{
    return safe_cast<T^>(reinterpret_cast<Platform::Object^>(winrt::get_abi(from)));
}
```

## <a name="code-example"></a><span data-ttu-id="d62de-116">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="d62de-116">Code example</span></span>
<span data-ttu-id="d62de-117">Hier ist ein Codebeispiel (basierend auf der C++/CX **Blank App**-Projektvorlage), das die beiden verwendeten Hilfsfunktionen zeigt.</span><span class="sxs-lookup"><span data-stu-id="d62de-117">Here's a code example (based on the C++/CX **Blank App** project template) showing the two helper functions in use.</span></span> <span data-ttu-id="d62de-118">Es wird außerdem veranschaulicht, wie Namespace-Aliase für die verschiedenen Inseln verwendet werden können, um mit sonstigen potenziellen Namespacekonflikten zwischen der C++/WinRT-Projektion und der C++/CX-Projektion umzugehen.</span><span class="sxs-lookup"><span data-stu-id="d62de-118">It also illustrates how you can use namespace aliases for the different islands to deal with otherwise potential namespace collisions between the C++/WinRT projection and the C++/CX projection.</span></span>

```cppwinrt
// MainPage.xaml.cpp

#include "pch.h"
#include "MainPage.xaml.h"
#include <winrt/Windows.Foundation.h>
#include <sstream>

using namespace InteropExample;

namespace cx
{
    using namespace Windows::Foundation;
}

namespace winrt
{
    using namespace Windows::Foundation;
}

template <typename T>
T from_cx(Platform::Object^ from)
{
    T to{ nullptr };

    winrt::check_hresult(reinterpret_cast<::IUnknown*>(from)
        ->QueryInterface(winrt::guid_of<T>(),
            reinterpret_cast<void**>(winrt::put_abi(to))));

    return to;
}

template <typename T>
T^ to_cx(winrt::Windows::Foundation::IUnknown const& from)
{
    return safe_cast<T^>(reinterpret_cast<Platform::Object^>(winrt::get_abi(from)));
}

MainPage::MainPage()
{
    InitializeComponent();

    winrt::init_apartment(winrt::apartment_type::single_threaded);

    winrt::Uri uri(L"http://aka.ms/cppwinrt");
    std::wstringstream wstringstream;
    wstringstream << L"C++/WinRT: " << uri.Domain().c_str() << std::endl;

    // Convert from a C++/WinRT type to a C++/CX type.
    cx::Uri^ cx = to_cx<cx::Uri>(uri);
    wstringstream << L"C++/CX: " << cx->Domain->Data() << std::endl;
    ::OutputDebugString(wstringstream.str().c_str());

    // Convert from a C++/CX type to a C++/WinRT type.
    winrt::Uri uri_from_cx = from_cx<winrt::Uri>(cx);
    WINRT_ASSERT(uri.Domain() == uri_from_cx.Domain());
    WINRT_ASSERT(uri == uri_from_cx);
}
```

## <a name="important-apis"></a><span data-ttu-id="d62de-119">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="d62de-119">Important APIs</span></span>
* [<span data-ttu-id="d62de-120">IUnknown Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="d62de-120">IUnknown interface</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms680509)
* [<span data-ttu-id="d62de-121">QueryInterface-Funktion</span><span class="sxs-lookup"><span data-stu-id="d62de-121">QueryInterface function</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms682521)
* [<span data-ttu-id="d62de-122">winrt::get_abi Funktion</span><span class="sxs-lookup"><span data-stu-id="d62de-122">winrt::get_abi function</span></span>](/uwp/cpp-ref-for-winrt/get-abi)
* [<span data-ttu-id="d62de-123">winrt::get_abi Funktion</span><span class="sxs-lookup"><span data-stu-id="d62de-123">winrt::put_abi function</span></span>](/uwp/cpp-ref-for-winrt/put-abi)

## <a name="related-topics"></a><span data-ttu-id="d62de-124">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="d62de-124">Related topics</span></span>
* [<span data-ttu-id="d62de-125">C++/CX</span><span class="sxs-lookup"><span data-stu-id="d62de-125">C++/CX</span></span>](/cpp/cppcx/visual-c-language-reference-c-cx)
