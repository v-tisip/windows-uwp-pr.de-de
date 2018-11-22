---
author: stevewhims
description: In diesem Thema werden zwei Hilfsfunktionen gezeigt, die verwendet werden können, um zwischen C++ / CX- und C++ / WinRT-Objekten zu konvertieren.
title: Interoperabilität zwischen C++/WinRT und C++/CX
ms.author: stwhi
ms.date: 10/09/2018
ms.topic: article
keywords: windows 10, uwp, standard, c++, cpp, winrt, projizierung, portieren, migrieren, interoperabilität, C++/CX
ms.localizationpriority: medium
ms.openlocfilehash: ca3cc69065ef2898aebafc832da1639985231d60
ms.sourcegitcommit: 93c0a60cf531c7d9fe7b00e7cf78df86906f9d6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2018
ms.locfileid: "7561381"
---
# <a name="interop-between-cwinrt-and-ccx"></a><span data-ttu-id="958cf-104">Interoperabilität zwischen C++/WinRT und C++/CX</span><span class="sxs-lookup"><span data-stu-id="958cf-104">Interop between C++/WinRT and C++/CX</span></span>

<span data-ttu-id="958cf-105">Strategien für die schrittweise Portieren des Codes in Ihrer [C++ / CX](/cpp/cppcx/visual-c-language-reference-c-cx) -Projekts in [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) finden Sie im Abschnitt [Wechsel zu C++ / WinRT von C++ / CX](move-to-winrt-from-cx.md).</span><span class="sxs-lookup"><span data-stu-id="958cf-105">Strategies for gradually porting the code in your [C++/CX](/cpp/cppcx/visual-c-language-reference-c-cx) project to [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) are discussed in [Move to C++/WinRT from C++/CX](move-to-winrt-from-cx.md).</span></span>

<span data-ttu-id="958cf-106">Dieses Thema zeigt zwei Hilfsfunktionen, die Sie verwenden können, für die Konvertierung zwischen C++ / CX- und C++ / WinRT-Objekten im selben Projekt.</span><span class="sxs-lookup"><span data-stu-id="958cf-106">This topic shows two helper functions that you can use to convert between C++/CX and C++/WinRT objects within the same project.</span></span> <span data-ttu-id="958cf-107">Sie können sie für Interoperabilität zwischen Code, der die beiden sprachprojektionen verwendet, oder Sie können die Funktionen verwenden, wie Sie Ihren Code von C++ Portieren / CX nach C++ / WinRT.</span><span class="sxs-lookup"><span data-stu-id="958cf-107">You can use them to interop between code that uses the two language projections, or you can use the functions as you port your code from C++/CX to C++/WinRT.</span></span>

## <a name="fromcx-and-tocx-functions"></a><span data-ttu-id="958cf-108">Funktionen from_cx und to_cx</span><span class="sxs-lookup"><span data-stu-id="958cf-108">from_cx and to_cx functions</span></span>
<span data-ttu-id="958cf-109">Die folgende Hilfsfunktion konvertiert ein C++/CX-Objekt in ein äquivalentes C++/WinRT-Objekt.</span><span class="sxs-lookup"><span data-stu-id="958cf-109">The helper function below converts a C++/CX object to an equivalent C++/WinRT object.</span></span> <span data-ttu-id="958cf-110">Die Funktion bildet ein C++/CX-Objekt auf den zugrundeliegenden [**IUnknown**](https://msdn.microsoft.com/library/windows/desktop/ms680509) Schnittstellenzeiger ab.</span><span class="sxs-lookup"><span data-stu-id="958cf-110">The function casts a C++/CX object to its underlying [**IUnknown**](https://msdn.microsoft.com/library/windows/desktop/ms680509) interface pointer.</span></span> <span data-ttu-id="958cf-111">Sie ruft dann [**QueryInterface**](https://msdn.microsoft.com/library/windows/desktop/ms682521) auf diesem Zeiger auf, um de Standardschnittstelle des C++/WinRT-Objekts abzurufen.</span><span class="sxs-lookup"><span data-stu-id="958cf-111">It then calls [**QueryInterface**](https://msdn.microsoft.com/library/windows/desktop/ms682521) on that pointer to query for the default interface of the C++/WinRT object.</span></span> <span data-ttu-id="958cf-112">**QueryInterface** ist das Windows-Runtime Application Binary Interface (ABI) Äquivalent zur safe_cast-Erweiterung von C++/CX.</span><span class="sxs-lookup"><span data-stu-id="958cf-112">**QueryInterface** is the Windows Runtime application binary interface (ABI) equivalent of the C++/CX safe_cast extension.</span></span> <span data-ttu-id="958cf-113">Und die Funktion [**winrt::put_abi**](/uwp/cpp-ref-for-winrt/put-abi) ermittelt die Adresse des zugrundeliegenden **IUnknown**-Schnittstellenzeiger eines C++/WinRT-Objekts, sodass er auf einen anderen Wert gesetzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="958cf-113">And, the [**winrt::put_abi**](/uwp/cpp-ref-for-winrt/put-abi) function retrieves the address of a C++/WinRT object's underlying **IUnknown** interface pointer so that it can be set to another value.</span></span>

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

<span data-ttu-id="958cf-114">Die folgende Hilfsfunktion konvertiert ein C++/WinRT-Objekt in ein äquivalentes C++/CX-Objekt.</span><span class="sxs-lookup"><span data-stu-id="958cf-114">The helper function below converts a C++/WinRT object to an equivalent C++/CX object.</span></span> <span data-ttu-id="958cf-115">Die Funktion [**winrt::get_abi**](/uwp/cpp-ref-for-winrt/get-abi) liefert einen Zeiger auf die **IUnknown**-Schnittstelle eines C++/WinRT-Objekts.</span><span class="sxs-lookup"><span data-stu-id="958cf-115">The [**winrt::get_abi**](/uwp/cpp-ref-for-winrt/get-abi) function retrieves a pointer to a C++/WinRT object's underlying **IUnknown** interface.</span></span> <span data-ttu-id="958cf-116">Die Funktion bildet diesen Zeiger auf ein C++/CX-Objekt ab, bevor sie die safe_cast-Erweiterung von C++/CX verwendet, um den gewünschten C++/CX-Typ abzufragen.</span><span class="sxs-lookup"><span data-stu-id="958cf-116">The function casts that pointer to a C++/CX object before using the C++/CX safe_cast extension to query for the requested C++/CX type.</span></span>

```cppwinrt
template <typename T>
T^ to_cx(winrt::Windows::Foundation::IUnknown const& from)
{
    return safe_cast<T^>(reinterpret_cast<Platform::Object^>(winrt::get_abi(from)));
}
```

## <a name="example-project-showing-the-two-helper-functions-in-use"></a><span data-ttu-id="958cf-117">Beispielprojekt mit zwei Hilfsfunktionen verwendet</span><span class="sxs-lookup"><span data-stu-id="958cf-117">Example project showing the two helper functions in use</span></span>

<span data-ttu-id="958cf-118">Reproduziert werden, auf einfache Weise das Szenario für das schrittweise Portieren des Codes in C++ / CX-Projekts zu C++ / WinRT können Sie damit beginnen durch Erstellen eines neuen Projekts in Visual Studio mit einer der C++ / WinRT-Projektvorlagen (finden Sie unter [Visual Studio-Unterstützung für C++ / WinRT und VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix)).</span><span class="sxs-lookup"><span data-stu-id="958cf-118">To reproduce, in a simple way, the scenario of gradually porting the code in a C++/CX project to C++/WinRT, you can begin by creating a new project in Visual Studio using one of the C++/WinRT project templates (see [Visual Studio support for C++/WinRT, and the VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix)).</span></span>

<span data-ttu-id="958cf-119">Dieses Beispielprojekt auch zeigt, wie Sie Namespace-Aliase für die verschiedenen Inseln des Codes verwenden können, um den Umgang mit sonstigen potenziellen Namespacekonflikten zwischen der C++ / WinRT-Projektion und der C++ / CX-Projektion.</span><span class="sxs-lookup"><span data-stu-id="958cf-119">This example project also illustrates how you can use namespace aliases for the different islands of code, in order to deal with otherwise potential namespace collisions between the C++/WinRT projection and the C++/CX projection.</span></span>

- <span data-ttu-id="958cf-120">Erstellen Sie ein **Visual C++** \> **Universelle Windows-** > **Core App (C++ / WinRT)** Projekt.</span><span class="sxs-lookup"><span data-stu-id="958cf-120">Create a **Visual C++** \> **Windows Universal** > **Core App (C++/WinRT)** project.</span></span>
- <span data-ttu-id="958cf-121">In den Projekteigenschaften, **C/C++-** \> **Allgemeine** \> **Windows-Runtime-Erweiterung** \> **Ja (/ Zw)**.</span><span class="sxs-lookup"><span data-stu-id="958cf-121">In project properties, **C/C++** \> **General** \> **Consume Windows Runtime Extension** \> **Yes (/ZW)**.</span></span> <span data-ttu-id="958cf-122">Dies aktiviert die Projekt-Unterstützung für C++ / CX.</span><span class="sxs-lookup"><span data-stu-id="958cf-122">This turns on project support for C++/CX.</span></span>
- <span data-ttu-id="958cf-123">Ersetzen Sie den Inhalt des `App.cpp` mit der untenstehenden codeauflistung.</span><span class="sxs-lookup"><span data-stu-id="958cf-123">Replace the contents of `App.cpp` with the code listing below.</span></span>

```cppwinrt
// App.cpp
#include "pch.h"
#include <sstream>

namespace cx
{
    using namespace Windows::Foundation;
}

namespace winrt
{
    using namespace Windows;
    using namespace Windows::ApplicationModel::Core;
    using namespace Windows::Foundation;
    using namespace Windows::Foundation::Numerics;
    using namespace Windows::UI;
    using namespace Windows::UI::Core;
    using namespace Windows::UI::Composition;
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

struct App : winrt::implements<App, winrt::IFrameworkViewSource, winrt::IFrameworkView>
{
    winrt::CompositionTarget m_target{ nullptr };
    winrt::VisualCollection m_visuals{ nullptr };
    winrt::Visual m_selected{ nullptr };
    winrt::float2 m_offset{};

    winrt::IFrameworkView CreateView()
    {
        return *this;
    }

    void Initialize(winrt::CoreApplicationView const &)
    {
    }

    void Load(winrt::hstring const&)
    {
    }

    void Uninitialize()
    {
    }

    void Run()
    {
        winrt::CoreWindow window = winrt::CoreWindow::GetForCurrentThread();
        window.Activate();

        winrt::CoreDispatcher dispatcher = window.Dispatcher();
        dispatcher.ProcessEvents(winrt::CoreProcessEventsOption::ProcessUntilQuit);
    }

    void SetWindow(winrt::CoreWindow const & window)
    {
        winrt::Compositor compositor;
        winrt::ContainerVisual root = compositor.CreateContainerVisual();
        m_target = compositor.CreateTargetForCurrentView();
        m_target.Root(root);
        m_visuals = root.Children();

        window.PointerPressed({ this, &App::OnPointerPressed });
        window.PointerMoved({ this, &App::OnPointerMoved });

        window.PointerReleased([&](auto && ...)
        {
            m_selected = nullptr;
        });
    }

    void OnPointerPressed(IInspectable const &, winrt::PointerEventArgs const & args)
    {
        winrt::float2 const point = args.CurrentPoint().Position();

        for (winrt::Visual visual : m_visuals)
        {
            winrt::float3 const offset = visual.Offset();
            winrt::float2 const size = visual.Size();

            if (point.x >= offset.x &&
                point.x < offset.x + size.x &&
                point.y >= offset.y &&
                point.y < offset.y + size.y)
            {
                m_selected = visual;
                m_offset.x = offset.x - point.x;
                m_offset.y = offset.y - point.y;
            }
        }

        if (m_selected)
        {
            m_visuals.Remove(m_selected);
            m_visuals.InsertAtTop(m_selected);
        }
        else
        {
            AddVisual(point);
        }
    }

    void OnPointerMoved(IInspectable const &, winrt::PointerEventArgs const & args)
    {
        if (m_selected)
        {
            winrt::float2 const point = args.CurrentPoint().Position();

            m_selected.Offset(
            {
                point.x + m_offset.x,
                point.y + m_offset.y,
                0.0f
            });
        }
    }

    void AddVisual(winrt::float2 const point)
    {
        winrt::Compositor compositor = m_visuals.Compositor();
        winrt::SpriteVisual visual = compositor.CreateSpriteVisual();

        static winrt::Color colors[] =
        {
            { 0xDC, 0x5B, 0x9B, 0xD5 },
            { 0xDC, 0xED, 0x7D, 0x31 },
            { 0xDC, 0x70, 0xAD, 0x47 },
            { 0xDC, 0xFF, 0xC0, 0x00 }
        };

        static unsigned last = 0;
        unsigned const next = ++last % _countof(colors);
        visual.Brush(compositor.CreateColorBrush(colors[next]));

        float const BlockSize = 100.0f;

        visual.Size(
        {
            BlockSize,
            BlockSize
        });

        visual.Offset(
        {
            point.x - BlockSize / 2.0f,
            point.y - BlockSize / 2.0f,
            0.0f,
        });

        m_visuals.InsertAtTop(visual);

        m_selected = visual;
        m_offset.x = -BlockSize / 2.0f;
        m_offset.y = -BlockSize / 2.0f;
    }
};

int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();

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

    winrt::CoreApplication::Run(winrt::make<App>());
}
```

## <a name="important-apis"></a><span data-ttu-id="958cf-124">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="958cf-124">Important APIs</span></span>
* [<span data-ttu-id="958cf-125">IUnknown Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="958cf-125">IUnknown interface</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms680509)
* [<span data-ttu-id="958cf-126">QueryInterface-Funktion</span><span class="sxs-lookup"><span data-stu-id="958cf-126">QueryInterface function</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms682521)
* [<span data-ttu-id="958cf-127">winrt::get_abi Funktion</span><span class="sxs-lookup"><span data-stu-id="958cf-127">winrt::get_abi function</span></span>](/uwp/cpp-ref-for-winrt/get-abi)
* [<span data-ttu-id="958cf-128">winrt::get_abi Funktion</span><span class="sxs-lookup"><span data-stu-id="958cf-128">winrt::put_abi function</span></span>](/uwp/cpp-ref-for-winrt/put-abi)

## <a name="related-topics"></a><span data-ttu-id="958cf-129">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="958cf-129">Related topics</span></span>
* [<span data-ttu-id="958cf-130">C++/CX</span><span class="sxs-lookup"><span data-stu-id="958cf-130">C++/CX</span></span>](/cpp/cppcx/visual-c-language-reference-c-cx)
* [<span data-ttu-id="958cf-131">C++/CX zu C++/WinRT wechseln</span><span class="sxs-lookup"><span data-stu-id="958cf-131">Move to C++/WinRT from C++/CX</span></span>](move-to-winrt-from-cx.md)
