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
ms.openlocfilehash: 02aa86231cd611bd20a386d3da2f9d2b6dc5df66
ms.sourcegitcommit: 9a17266f208ec415fc718e5254d5b4c08835150c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2018
ms.locfileid: "2885757"
---
# <a name="interop-between-cwinrtwindowsuwpcpp-and-winrt-apisintro-to-using-cpp-with-winrt-and-ccx"></a>Interoperabilität zwischen [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) und C++/CX
In diesem Thema werden zwei Hilfsfunktionen gezeigt, die verwendet werden können, um zwischen [C++ / CX](/cpp/cppcx/visual-c-language-reference-c-cx?branch=live)- und C++ / WinRT-Objekten zu konvertieren. Können sie Sie Interop zwischen Code, die zwei Sprache Projektionen verwendet wird, oder Sie können die Funktionen verwenden, wie Sie den Code schrittweise aus C + verschieben / C + CX / WinRT (finden Sie unter [C + verschieben / WinRT von C + / CX](move-to-winrt-from-cx.md)).

## <a name="fromcx-and-tocx-functions"></a>Funktionen from_cx und to_cx
Die folgende Hilfsfunktion konvertiert ein C++/CX-Objekt in ein äquivalentes C++/WinRT-Objekt. Die Funktion bildet ein C++/CX-Objekt auf den zugrundeliegenden [**IUnknown**](https://msdn.microsoft.com/library/windows/desktop/ms680509) Schnittstellenzeiger ab. Sie ruft dann [**QueryInterface**](https://msdn.microsoft.com/library/windows/desktop/ms682521) auf diesem Zeiger auf, um de Standardschnittstelle des C++/WinRT-Objekts abzurufen. **QueryInterface** ist das Windows-Runtime Application Binary Interface (ABI) Äquivalent zur safe_cast-Erweiterung von C++/CX. Und die Funktion [**winrt::put_abi**](/uwp/cpp-ref-for-winrt/put-abi) ermittelt die Adresse des zugrundeliegenden **IUnknown**-Schnittstellenzeiger eines C++/WinRT-Objekts, sodass er auf einen anderen Wert gesetzt werden kann.

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

Die folgende Hilfsfunktion konvertiert ein C++/WinRT-Objekt in ein äquivalentes C++/CX-Objekt. Die Funktion [**winrt::get_abi**](/uwp/cpp-ref-for-winrt/get-abi) liefert einen Zeiger auf die **IUnknown**-Schnittstelle eines C++/WinRT-Objekts. Die Funktion bildet diesen Zeiger auf ein C++/CX-Objekt ab, bevor sie die safe_cast-Erweiterung von C++/CX verwendet, um den gewünschten C++/CX-Typ abzufragen.

```cppwinrt
template <typename T>
T^ to_cx(winrt::Windows::Foundation::IUnknown const& from)
{
    return safe_cast<T^>(reinterpret_cast<Platform::Object^>(winrt::get_abi(from)));
}
```

## <a name="code-example"></a>Codebeispiel
Hier ist ein Codebeispiel (basierend auf der C++/CX **Blank App**-Projektvorlage), das die beiden verwendeten Hilfsfunktionen zeigt. Es wird außerdem veranschaulicht, wie Namespace-Aliase für die verschiedenen Inseln verwendet werden können, um mit sonstigen potenziellen Namespacekonflikten zwischen der C++/WinRT-Projektion und der C++/CX-Projektion umzugehen.

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

## <a name="important-apis"></a>Wichtige APIs
* [IUnknown Schnittstelle](https://msdn.microsoft.com/library/windows/desktop/ms680509)
* [QueryInterface](https://msdn.microsoft.com/library/windows/desktop/ms682521)
* [winrt::get_abi Funktion](/uwp/cpp-ref-for-winrt/get-abi)
* [winrt::get_abi Funktion](/uwp/cpp-ref-for-winrt/put-abi)

## <a name="related-topics"></a>Verwandte Themen
* [C++/CX](/cpp/cppcx/visual-c-language-reference-c-cx)
