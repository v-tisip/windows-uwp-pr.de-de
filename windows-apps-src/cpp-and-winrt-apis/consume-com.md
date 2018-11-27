---
description: In diesem Thema verwendet ein vollständiges Beispiel für die Direct2D-Code, wie Sie c++ / WinRT-COM-Klassen und Schnittstellen aufnehmen.
title: Verwenden von COM-Komponenten mit C++ / WinRT
ms.date: 07/23/2018
ms.topic: article
keywords: Windows 10, Uwp, Standard, c++, Cpp, Winrt, COM, Komponente, Klasse, Schnittstelle
ms.localizationpriority: medium
ms.openlocfilehash: 9000cad79e12a645689d90ef37a8ff43b9fc95b7
ms.sourcegitcommit: 681c70f964210ab49ac5d06357ae96505bb78741
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "7706311"
---
# <a name="consume-com-components-with-cwinrt"></a>Verwenden von COM-Komponenten mit C++ / WinRT

Sie können die Funktionen von der [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) Bibliothek COM-Komponenten, z. B. die High-End-2-D- und 3-d-Grafiken, DirectX-APIs nutzen. C++ / WinRT ist die einfachste Möglichkeit zum DirectX verwenden, ohne Leistungseinbußen. In diesem Thema verwendet ein Direct2D-Codebeispiel, wie Sie c++ / WinRT-COM-Klassen und Schnittstellen aufnehmen. Sie können natürlich mischen COM- und Windows-Runtime-Programmierung innerhalb der gleichen C++ / WinRT-Projekt.

Am Ende dieses Themas finden Sie eine vollständige Quelle codeauflistung einer minimalen Direct2D-Anwendung. Wir heben Sie Auszüge aus diesen Code und verwenden sie zum Verwenden von COM-Komponenten mit C++ veranschaulichen / WinRT mithilfe verschiedener Funktionen der C++ / WinRT-Bibliothek.

## <a name="com-smart-pointers-winrtcomptruwpcpp-ref-for-winrtcom-ptr"></a>COM-Zeigern ([**WinRT:: com_ptr**](/uwp/cpp-ref-for-winrt/com-ptr))

Wenn Sie mit COM-Programmierung, arbeiten Sie direkt mit Schnittstellen anstatt mit Objekten (das auch im Hintergrund für Windows-Runtime-APIs, die eine Weiterentwicklung des COM sind "true"). Um eine Funktion für eine COM-Klasse aufrufen, z. B. Sie aktivieren die Klasse, eine Schnittstelle zurück, und rufen Sie dann Sie Funktionen auf diese Schnittstelle. Um den Zustand eines Objekts zuzugreifen, zugreifen nicht Sie Datenelemente direkt. Rufen Sie stattdessen Accessor und Zugriffsfunktion Funktionen für eine Schnittstelle.

Um spezifischer sein, sprechen wir über Interface- *Zeiger*interagieren. Und dazu nutzen wir das Vorhandensein der COM-intelligenten Zeigertyp in C++ / WinRT&mdash;den Typ [**WinRT:: com_ptr**](/uwp/cpp-ref-for-winrt/com-ptr) .

```cppwinrt
winrt::com_ptr<ID2D1Factory1> factory;
```

Der obige Code veranschaulicht, wie einen nicht initialisierten intelligenten Zeiger auf eine [**ID2D1Factory1**](https://msdn.microsoft.com/library/Hh404596) COM-Schnittstelle deklarieren. Der intelligente Zeiger ist nicht initialisiert, damit es noch nicht auf eine **ID2D1Factory1** -Schnittstelle, die an alle eigentliche Objekt (es ist nicht auf eine Schnittstelle überhaupt zeigen) gehören verwiesen wird. Aber sie hat die Möglichkeit dazu. und (wobei ein intelligenter Zeiger) die Möglichkeit über COM-referenzzählung zum Verwalten der Lebensdauer des besitzenden Objekts der Schnittstelle, die darauf verweist, und das Medium mit dem Sie Funktionen für diese Schnittstelle aufrufen.

## <a name="com-functions-that-return-an-interface-pointer-as-void"></a>COM-Funktionen, die einen Schnittstellenzeiger als **"void"** zurückgibt.

Sie können die [**com_ptr:: put_void**](/uwp/cpp-ref-for-winrt/com-ptr#comptrputvoid-function) -Funktion zum Schreiben in eines nicht initialisierten intelligenten Zeigers zugrunde liegenden rohzeiger aufrufen.

```cppwinrt
D2D1CreateFactory(
    D2D1_FACTORY_TYPE_SINGLE_THREADED,
    __uuidof(factory),
    &options,
    factory.put_void()
);
```

Der obige Code Ruft die [**D2D1CreateFactory**](/windows/desktop/api/d2d1/nf-d2d1-d2d1createfactory) Funktion, die einen Schnittstellenzeiger **ID2D1Factory1** über die letzte Parameter über **Void\ * \ *** Typ. Viele COM-Funktionen geben Sie einen **Void\ * \ ***. Verwenden Sie für solche Funktionen [**com_ptr:: put_void**](/uwp/cpp-ref-for-winrt/com-ptr#comptrputvoid-function) wie gezeigt.

## <a name="com-functions-that-return-a-specific-interface-pointer"></a>COM-Funktionen, die einen bestimmten Schnittstellenzeiger zurückzugeben

Die [**D3D11CreateDevice**](/windows/desktop/api/dwrite/nf-dwrite-dwritecreatefactory) -Funktion gibt einen Schnittstellenzeiger [**ID3D11Device**](https://msdn.microsoft.com/library/Hh404596) über seinen antepenultimate Parameter, der hat **ID3D11Device\ * \ *** Typ. Verwenden Sie für die Funktionen, die einen bestimmten Schnittstellenzeiger wie den zurückgeben, [**com_ptr**](/uwp/cpp-ref-for-winrt/com-ptr#comptrput-function).

```cppwinrt
winrt::com_ptr<ID3D11Device> device;
D3D11CreateDevice(
    ...
    device.put(),
    ...);
```

Im Codebeispiel wird im Abschnitt vor diesem zeigt, wie die unformatierte **D2D1CreateFactory** -Funktion aufrufen. Aber in der Tat Wenn im Codebeispiel für dieses Thema **D2D1CreateFactory**aufruft, verwendet eine Hilfsprogramm-Funktionsvorlage, die die unformatierte API umschließt und daher im Codebeispiel tatsächlich [**com_ptr**](/uwp/cpp-ref-for-winrt/com-ptr#comptrput-function)verwendet.

```cppwinrt
winrt::com_ptr<ID2D1Factory1> factory;
D2D1CreateFactory(
    D2D1_FACTORY_TYPE_SINGLE_THREADED,
    options,
    factory.put());
```

## <a name="com-functions-that-return-an-interface-pointer-as-iunknown"></a>COM-Funktionen, die einen Schnittstellenzeiger als **IUnknown** zurückgeben

Die [**DWriteCreateFactory**](/windows/desktop/api/dwrite/nf-dwrite-dwritecreatefactory) -Funktion gibt einen DirectWrite-Factory-Interface-Zeiger über die letzte Parameter, der [**IUnknown**](https://msdn.microsoft.com/library/windows/desktop/ms680509) Typ verfügt. Für eine solche Funktion umwandeln verwenden [**com_ptr**](/uwp/cpp-ref-for-winrt/com-ptr#comptrput-function), aber Neuinterpretation, um **IUnknown**.

```cppwinrt
DWriteCreateFactory(
    DWRITE_FACTORY_TYPE_SHARED,
    __uuidof(dwriteFactory2),
    reinterpret_cast<IUnknown**>(dwriteFactory2.put()));
```

## <a name="re-seat-a-winrtcomptr"></a>Setzen Sie erneut eine **WinRT:: com_ptr**

> [!IMPORTANT]
> Wenn Sie eine [**WinRT:: com_ptr**](/uwp/cpp-ref-for-winrt/com-ptr) verfügen, die bereits verbunden ist (die interne rohzeiger hat bereits ein Ziel) und Sie es auf ein anderes Objekt erneut setzen möchten, dann müssen Sie zuerst zuweisen `nullptr` darauf&mdash;wie im folgenden Codebeispiel dargestellt. Wenn Sie nicht, dann zeichnet ein bereits angeschlossene **Com_ptr** das Problem auf Ihre Aufmerksamkeit (Wenn Sie [**com_ptr**](/uwp/cpp-ref-for-winrt/com-ptr#comptrput-function) oder [**com_ptr:: put_void**](/uwp/cpp-ref-for-winrt/com-ptr#comptrputvoid-function)aufrufen) durch auszugehen, dass der interne Zeiger nicht null ist.

```cppwinrt
winrt::com_ptr<ID2D1SolidColorBrush> brush;
...
    brush.put()
...
brush = nullptr; // Important because we're about to re-seat
target->CreateSolidColorBrush(
    color_orange,
    D2D1::BrushProperties(0.8f),
    brush.put()));
```

## <a name="handle-hresult-error-codes"></a>Behandeln von HRESULT-Fehlercodes

Um zu prüfen, dass der Wert für eine HRESULT von COM-Funktionen zurückgegeben und löst eine Ausnahme aus, wenn es sich um einen Fehlercode darstellt, rufen Sie [**WinRT:: check_hresult**](/uwp/cpp-ref-for-winrt/error-handling/check-hresult).

```cppwinrt
winrt::check_hresult(D2D1CreateFactory(
    D2D1_FACTORY_TYPE_SINGLE_THREADED,
    __uuidof(factory),
    options,
    factory.put_void()));
```

## <a name="com-functions-that-take-a-specific-interface-pointer"></a>COM-Funktionen, die einen bestimmten Schnittstellenzeiger nutzen

Sie können die [**com_ptr:: Get**](/uwp/cpp-ref-for-winrt/com-ptr#comptrget-function) -Funktion, um Ihre **Com_ptr** an eine Funktion übergeben, die einen bestimmten Schnittstellenzeiger des gleichen Typs akzeptiert aufrufen.

```cppwinrt
... ExampleFunction(
    winrt::com_ptr<ID2D1Factory1> const& factory,
    winrt::com_ptr<IDXGIDevice> const& dxdevice)
{
    ...
    winrt::check_hresult(factory->CreateDevice(dxdevice.get(), ...));
    ...
}
```

## <a name="com-functions-that-take-an-iunknown-interface-pointer"></a>COM-Funktionen, die einen Schnittstellenzeiger **IUnknown** nutzen

Sie können die kostenlose [**winrt::get_unknown**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#getunknown-function) -Funktion, um Ihre **Com_ptr** an eine Funktion übergeben, der einen Schnittstellenzeiger **IUnknown** akzeptiert aufrufen.

```cppwinrt
winrt::check_hresult(factory->CreateSwapChainForCoreWindow(
    ...
    winrt::get_unknown(CoreWindow::GetForCurrentThread()),
    ...));
```

## <a name="passing-and-returning-com-smart-pointers"></a>Übergeben und Zurückgeben von COM--Zeiger

Eine Funktion, die einen intelligenten COM-Zeiger in Form einer **WinRT:: com_ptr** sollten als konstanten Verweis oder als Verweis tun.

```cppwinrt
... GetDxgiFactory(winrt::com_ptr<ID3D11Device> const& device) ...

... CreateDevice(..., winrt::com_ptr<ID3D11Device>& device) ...
```

Eine Funktion, die eine **WinRT:: com_ptr** gibt sollten Wert tun.

```cppwinrt
winrt::com_ptr<ID2D1Factory1> CreateFactory() ...
```

## <a name="query-a-com-smart-pointer-for-a-different-interface"></a>Einen intelligenten COM-Zeiger für eine andere Schnittstelle Abfragen

Die [**com_ptr:: As**](/uwp/cpp-ref-for-winrt/com-ptr#comptras-function) Funktion können Sie einen intelligenten COM-Zeiger für eine andere Schnittstelle Abfragen. Die Funktion löst eine Ausnahme aus, wenn die Abfrage nicht erfolgreich.

```cppwinrt
void ExampleFunction(winrt::com_ptr<ID3D11Device> const& device)
{
    ...
    winrt::com_ptr<IDXGIDevice> const dxdevice{ device.as<IDXGIDevice>() };
    ...
}
```

Alternativ verwenden [**com_ptr::try_as**](/uwp/cpp-ref-for-winrt/com-ptr#comptrtryas-function), die einen Wert zurückgibt, die Sie vor überprüfen kann `nullptr` um festzustellen, ob die Abfrage erfolgreich war.

## <a name="full-source-code-listing-of-a-minimal-direct2d-application"></a>Vollständige Quelle codeauflistung einer minimalen Direct2D-Anwendung

Wenn Sie erstellen und dieses Codebeispiel Quelle anschließend zunächst in Visual Studio ausführen möchten, erstellen Sie ein neues **Core App (C++ / WinRT)**. `Direct2D` der name kann sich nichts anderes ist ein angemessener Namen für das Projekt. Öffnen `App.cpp`, löschen Sie den gesamten Inhalt, und fügen Sie in den folgenden Eintrag.

```cppwinrt
#include "pch.h"
#include <d2d1_1.h>
#include <d3d11.h>
#include <dxgi1_2.h>
#include <winrt/Windows.Graphics.Display.h>

using namespace winrt;

using namespace Windows;
using namespace Windows::ApplicationModel::Core;
using namespace Windows::UI;
using namespace Windows::UI::Core;
using namespace Windows::Graphics::Display;

namespace
{
    winrt::com_ptr<ID2D1Factory1> CreateFactory()
    {
        D2D1_FACTORY_OPTIONS options{};

#ifdef _DEBUG
        options.debugLevel = D2D1_DEBUG_LEVEL_INFORMATION;
#endif

        winrt::com_ptr<ID2D1Factory1> factory;

        winrt::check_hresult(D2D1CreateFactory(
            D2D1_FACTORY_TYPE_SINGLE_THREADED,
            options,
            factory.put()));

        return factory;
    }

    HRESULT CreateDevice(D3D_DRIVER_TYPE const type, winrt::com_ptr<ID3D11Device>& device)
    {
        WINRT_ASSERT(!device);

        return D3D11CreateDevice(
            nullptr,
            type,
            nullptr,
            D3D11_CREATE_DEVICE_BGRA_SUPPORT,
            nullptr, 0,
            D3D11_SDK_VERSION,
            device.put(),
            nullptr,
            nullptr);
    }

    winrt::com_ptr<ID3D11Device> CreateDevice()
    {
        winrt::com_ptr<ID3D11Device> device;
        HRESULT hr{ CreateDevice(D3D_DRIVER_TYPE_HARDWARE, device) };

        if (DXGI_ERROR_UNSUPPORTED == hr)
        {
            hr = CreateDevice(D3D_DRIVER_TYPE_WARP, device);
        }

        winrt::check_hresult(hr);
        return device;
    }

    winrt::com_ptr<ID2D1DeviceContext> CreateRenderTarget(
        winrt::com_ptr<ID2D1Factory1> const& factory,
        winrt::com_ptr<ID3D11Device> const& device)
    {
        WINRT_ASSERT(factory);
        WINRT_ASSERT(device);

        winrt::com_ptr<IDXGIDevice> const dxdevice{ device.as<IDXGIDevice>() };

        winrt::com_ptr<ID2D1Device> d2device;
        winrt::check_hresult(factory->CreateDevice(dxdevice.get(), d2device.put()));

        winrt::com_ptr<ID2D1DeviceContext> target;
        winrt::check_hresult(d2device->CreateDeviceContext(D2D1_DEVICE_CONTEXT_OPTIONS_NONE, target.put()));
        return target;
    }

    winrt::com_ptr<IDXGIFactory2> GetDxgiFactory(winrt::com_ptr<ID3D11Device> const& device)
    {
        WINRT_ASSERT(device);

        winrt::com_ptr<IDXGIDevice> const dxdevice{ device.as<IDXGIDevice>() };

        winrt::com_ptr<IDXGIAdapter> adapter;
        winrt::check_hresult(dxdevice->GetAdapter(adapter.put()));

        winrt::com_ptr<IDXGIFactory2> factory;
        winrt::check_hresult(adapter->GetParent(__uuidof(factory), factory.put_void()));
        return factory;
    }

    void CreateDeviceSwapChainBitmap(
        winrt::com_ptr<IDXGISwapChain1> const& swapchain,
        winrt::com_ptr<ID2D1DeviceContext> const& target)
    {
        WINRT_ASSERT(swapchain);
        WINRT_ASSERT(target);

        winrt::com_ptr<IDXGISurface> surface;
        winrt::check_hresult(swapchain->GetBuffer(0, __uuidof(surface), surface.put_void()));

        D2D1_BITMAP_PROPERTIES1 const props{ D2D1::BitmapProperties1(
            D2D1_BITMAP_OPTIONS_TARGET | D2D1_BITMAP_OPTIONS_CANNOT_DRAW,
            D2D1::PixelFormat(DXGI_FORMAT_B8G8R8A8_UNORM, D2D1_ALPHA_MODE_IGNORE)) };

        winrt::com_ptr<ID2D1Bitmap1> bitmap;

        winrt::check_hresult(target->CreateBitmapFromDxgiSurface(surface.get(),
            props,
            bitmap.put()));

        target->SetTarget(bitmap.get());
    }

    winrt::com_ptr<IDXGISwapChain1> CreateSwapChainForCoreWindow(winrt::com_ptr<ID3D11Device> const& device)
    {
        WINRT_ASSERT(device);

        winrt::com_ptr<IDXGIFactory2> const factory{ GetDxgiFactory(device) };

        DXGI_SWAP_CHAIN_DESC1 props{};
        props.Format = DXGI_FORMAT_B8G8R8A8_UNORM;
        props.SampleDesc.Count = 1;
        props.BufferUsage = DXGI_USAGE_RENDER_TARGET_OUTPUT;
        props.BufferCount = 2;
        props.SwapEffect = DXGI_SWAP_EFFECT_FLIP_SEQUENTIAL;

        winrt::com_ptr<IDXGISwapChain1> swapChain;

        winrt::check_hresult(factory->CreateSwapChainForCoreWindow(
            device.get(),
            winrt::get_unknown(CoreWindow::GetForCurrentThread()),
            &props,
            nullptr, // all or nothing
            swapChain.put()));

        return swapChain;
    }

    constexpr D2D1_COLOR_F color_white{ 1.0f,  1.0f,  1.0f,  1.0f };
    constexpr D2D1_COLOR_F color_orange{ 0.92f,  0.38f,  0.208f,  1.0f };
}

struct App : implements<App, IFrameworkViewSource, IFrameworkView>
{
    winrt::com_ptr<ID2D1Factory1> m_factory;
    winrt::com_ptr<ID2D1DeviceContext> m_target;
    winrt::com_ptr<IDXGISwapChain1> m_swapChain;
    winrt::com_ptr<ID2D1SolidColorBrush> m_brush;
    float m_dpi{};

    IFrameworkView CreateView()
    {
        return *this;
    }

    void Initialize(CoreApplicationView const&)
    {
    }

    void Load(hstring const&)
    {
        CoreWindow const window{ CoreWindow::GetForCurrentThread() };

        window.SizeChanged([&](auto&&...)
        {
            if (m_target)
            {
                ResizeSwapChainBitmap();
                Render();
            }
        });

        DisplayInformation const display{ DisplayInformation::GetForCurrentView() };
        m_dpi = display.LogicalDpi();

        display.DpiChanged([&](DisplayInformation const& display, IInspectable const&)
        {
            if (m_target)
            {
                m_dpi = display.LogicalDpi();
                m_target->SetDpi(m_dpi, m_dpi);
                CreateDeviceSizeResources();
                Render();
            }
        });

        m_factory = CreateFactory();
        CreateDeviceIndependentResources();
    }

    void Uninitialize()
    {
    }

    void Run()
    {
        CoreWindow const window{ CoreWindow::GetForCurrentThread() };
        window.Activate();

        Render();
        CoreDispatcher const dispatcher{ window.Dispatcher() };
        dispatcher.ProcessEvents(CoreProcessEventsOption::ProcessUntilQuit);
    }

    void SetWindow(CoreWindow const&) {}

    void Draw()
    {
        m_target->Clear(color_white);

        D2D1_SIZE_F const size{ m_target->GetSize() };
        D2D1_RECT_F const rect{ 100.0f, 100.0f, size.width - 100.0f, size.height - 100.0f };
        m_target->DrawRectangle(rect, m_brush.get(), 100.0f);

        WINRT_TRACE("Draw %.2f x %.2f @ %.2f\n", size.width, size.height, m_dpi);
    }

    void Render()
    {
        if (!m_target)
        {
            winrt::com_ptr<ID3D11Device> const device{ CreateDevice() };
            m_target = CreateRenderTarget(m_factory, device);
            m_swapChain = CreateSwapChainForCoreWindow(device);

            CreateDeviceSwapChainBitmap(m_swapChain, m_target);

            m_target->SetDpi(m_dpi, m_dpi);

            CreateDeviceResources();
            CreateDeviceSizeResources();
        }

        m_target->BeginDraw();
        Draw();
        m_target->EndDraw();

        HRESULT const hr{ m_swapChain->Present(1, 0) };

        if (S_OK != hr && DXGI_STATUS_OCCLUDED != hr)
        {
            ReleaseDevice();
        }
    }

    void ReleaseDevice()
    {
        m_target = nullptr;
        m_swapChain = nullptr;

        ReleaseDeviceResources();
    }

    void ResizeSwapChainBitmap()
    {
        WINRT_ASSERT(m_target);
        WINRT_ASSERT(m_swapChain);

        m_target->SetTarget(nullptr);

        if (S_OK == m_swapChain->ResizeBuffers(0, // all buffers
            0, 0, // client area
            DXGI_FORMAT_UNKNOWN, // preserve format
            0)) // flags
        {
            CreateDeviceSwapChainBitmap(m_swapChain, m_target);
            CreateDeviceSizeResources();
        }
        else
        {
            ReleaseDevice();
        }
    }

    void CreateDeviceIndependentResources()
    {
    }

    void CreateDeviceResources()
    {
        winrt::check_hresult(m_target->CreateSolidColorBrush(
            color_orange,
            D2D1::BrushProperties(0.8f),
            m_brush.put()));
    }

    void CreateDeviceSizeResources()
    {
    }

    void ReleaseDeviceResources()
    {
        m_brush = nullptr;
    }
};

int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    CoreApplication::Run(App());
}
```

## <a name="working-with-com-types-such-as-bstr-and-variant"></a>Arbeiten mit COM-Typen, wie und VARIANT

Wie Sie sehen können, C++ / WinRT stellt Unterstützung für das Implementieren und Aufrufen von COM-Schnittstellen. Für die Verwendung von COM-Typen, wie und VARIANT, ist immer die Möglichkeit, die in ihrer unformatierten Form (zusammen mit der entsprechenden APIs) verwenden. Alternativ können Sie die Wrapper durch ein Framework, z. B. die [Active Template Library (ATL)](/cpp/atl/active-template-library-atl-concepts), oder die Visual C++-Compiler- [COM-Unterstützung](/cpp/cpp/compiler-com-support)von oder auch durch Ihre eigenen Wrapper bereitgestellt.

## <a name="important-apis"></a>Wichtige APIs
* [winrt::check_hresult-Funktion](/uwp/cpp-ref-for-winrt/error-handling/check-hresult)
* [winrt::com_ptr Strukturvorlage](/uwp/cpp-ref-for-winrt/com-ptr)
* [winrt::Windows::Foundation::IUnknown-Struktur](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown)
