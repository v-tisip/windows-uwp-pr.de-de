---
author: stevewhims
description: In diesem Thema verwendet ein vollständiges Beispiel für die Direct2D-Code um zu veranschaulichen, wie c++ / WinRT COM-Klassen und Schnittstellen aufnehmen.
title: Verwenden von COM-Komponenten mit C++ / WinRT
ms.author: stwhi
ms.date: 07/23/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Standard, c++, Cpp, Winrt, COM, Komponente, Klasse, Schnittstelle
ms.localizationpriority: medium
ms.openlocfilehash: 598d0e7b4a374c18ece48f52947cec64a0f79dab
ms.sourcegitcommit: f5cf806a595969ecbb018c3f7eea86c7a34940f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "3824824"
---
# <a name="consume-com-components-with-cwinrtwindowsuwpcpp-and-winrt-apisintro-to-using-cpp-with-winrt"></a><span data-ttu-id="caff7-104">Verwenden von COM-Komponenten mit [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)</span><span class="sxs-lookup"><span data-stu-id="caff7-104">Consume COM components with [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)</span></span>

<span data-ttu-id="caff7-105">Sie können die Funktionen von C++ / WinRT-Bibliothek COM-Komponenten, z. B. die High-End-2-D- und 3-d-Grafiken, DirectX-APIs nutzen.</span><span class="sxs-lookup"><span data-stu-id="caff7-105">You can use the facilities of the C++/WinRT library to consume COM components, such as the high-performance 2-D and 3-D graphics of the DirectX APIs.</span></span> <span data-ttu-id="caff7-106">C++ / WinRT ist die einfachste Möglichkeit zum DirectX verwenden, ohne Leistungseinbußen.</span><span class="sxs-lookup"><span data-stu-id="caff7-106">C++/WinRT is the simplest way to use DirectX without compromising performance.</span></span> <span data-ttu-id="caff7-107">In diesem Thema verwendet ein Direct2D-Codebeispiel, wie Sie c++ / WinRT COM-Klassen und Schnittstellen aufnehmen.</span><span class="sxs-lookup"><span data-stu-id="caff7-107">This topic uses a Direct2D code example to show how to use C++/WinRT to consume COM classes and interfaces.</span></span> <span data-ttu-id="caff7-108">Sie können natürlich mischen COM- und Windows-Runtime-Programmierung innerhalb der gleichen C++ / WinRT-Projekt.</span><span class="sxs-lookup"><span data-stu-id="caff7-108">You can, of course, mix COM and Windows Runtime programming within the same C++/WinRT project.</span></span>

<span data-ttu-id="caff7-109">Am Ende dieses Themas finden Sie eine vollständige Quelle codeauflistung einer minimalen Direct2D-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="caff7-109">At the end of this topic, you'll find a full source code listing of a minimal Direct2D application.</span></span> <span data-ttu-id="caff7-110">Wir heben Sie Auszüge aus diesen Code und verwenden sie zum Verwenden von COM-Komponenten mit C++ veranschaulichen / WinRT mithilfe verschiedener Funktionen der C++ / WinRT-Bibliothek.</span><span class="sxs-lookup"><span data-stu-id="caff7-110">We'll lift excerpts from that code and use them to illustrate how to consume COM components using C++/WinRT using various facilities of the C++/WinRT library.</span></span>

## <a name="com-smart-pointers-winrtcomptruwpcpp-ref-for-winrtcom-ptr"></a><span data-ttu-id="caff7-111">COM-Zeigern ([**WinRT:: com_ptr**](/uwp/cpp-ref-for-winrt/com-ptr))</span><span class="sxs-lookup"><span data-stu-id="caff7-111">COM smart pointers ([**winrt::com_ptr**](/uwp/cpp-ref-for-winrt/com-ptr))</span></span>

<span data-ttu-id="caff7-112">Wenn Sie mit COM programmieren, arbeiten Sie direkt mit Schnittstellen anstatt mit Objekten (das auch im Hintergrund für Windows-Runtime-APIs, die eine Weiterentwicklung des COM sind "true").</span><span class="sxs-lookup"><span data-stu-id="caff7-112">When you program with COM, you work directly with interfaces rather than with objects (that's also true behind the scenes for Windows Runtime APIs, which are an evolution of COM).</span></span> <span data-ttu-id="caff7-113">Um eine Funktion für eine COM-Klasse aufrufen, z. B. Sie aktivieren die Klasse eine Schnittstelle zurück, und rufen Sie dann Sie Funktionen auf diese Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="caff7-113">To call a function on a COM class, for example, you activate the class, get an interface back, and then you call functions on that interface.</span></span> <span data-ttu-id="caff7-114">Um den Zustand eines Objekts zugreifen zu können, zugreifen nicht Sie Datenelemente direkt. Rufen Sie stattdessen Accessor und Zugriffsfunktion Funktionen in einer Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="caff7-114">To access the state of an object, you don't access its data members directly; instead, you call accessor and mutator functions on an interface.</span></span>

<span data-ttu-id="caff7-115">Um spezifischer sein, sprechen wir über Interface- *Zeiger*interagieren.</span><span class="sxs-lookup"><span data-stu-id="caff7-115">To be more specific, we're talking about interacting with interface *pointers*.</span></span> <span data-ttu-id="caff7-116">Und dazu nutzen wir das Vorhandensein der COM-intelligenten Zeigertyp in C++ / WinRT&mdash;den Typ [**WinRT:: com_ptr**](/uwp/cpp-ref-for-winrt/com-ptr) .</span><span class="sxs-lookup"><span data-stu-id="caff7-116">And for that, we benefit from the existence of the COM smart pointer type in C++/WinRT&mdash;the [**winrt::com_ptr**](/uwp/cpp-ref-for-winrt/com-ptr) type.</span></span>

```cppwinrt
winrt::com_ptr<ID2D1Factory1> factory;
```

<span data-ttu-id="caff7-117">Der obige Code zeigt, wie einen nicht initialisierten intelligenten Zeiger auf eine [**ID2D1Factory1**](https://msdn.microsoft.com/library/Hh404596) COM-Schnittstelle deklarieren.</span><span class="sxs-lookup"><span data-stu-id="caff7-117">The code above shows how to declare an uninitialized smart pointer to a [**ID2D1Factory1**](https://msdn.microsoft.com/library/Hh404596) COM interface.</span></span> <span data-ttu-id="caff7-118">Der intelligente Zeiger ist nicht initialisiert, sodass es noch nicht auf eine **ID2D1Factory1** -Schnittstelle zu tatsächlichen Objekt (es ist nicht auf eine Schnittstelle überhaupt zeigen) gehören verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="caff7-118">The smart pointer is uninitialized, so it's not yet pointing to a **ID2D1Factory1** interface belonging to any actual object (it's not pointing to an interface at all).</span></span> <span data-ttu-id="caff7-119">Der Nachteil ist aber das Potenzial dazu; und (wobei ein intelligenter Zeiger) die Möglichkeit, über COM-referenzzählung zum Verwalten der Lebensdauer des besitzenden Objekts der Schnittstelle, die darauf verweist, und das Medium, Sie Funktionen für diese Schnittstelle aufrufen.</span><span class="sxs-lookup"><span data-stu-id="caff7-119">But it has the potential to do so; and (being a smart pointer) it has the ability via COM reference counting to manage the lifetime of the owning object of the interface that it points to, and to be the medium by which you call functions on that interface.</span></span>

## <a name="com-functions-that-return-an-interface-pointer-as-void"></a><span data-ttu-id="caff7-120">COM-Funktionen, die einen Schnittstellenzeiger als zurückgeben \*\*Void\ \* \ \*\*\*</span><span class="sxs-lookup"><span data-stu-id="caff7-120">COM functions that return an interface pointer as **void\*\***</span></span>

<span data-ttu-id="caff7-121">Sie können die [**com_ptr:: put_void**](/uwp/cpp-ref-for-winrt/com-ptr#comptrputvoid-function) -Funktion, die auf eines nicht initialisierten intelligenten Zeigers zugrunde liegenden rohzeiger schreiben aufrufen.</span><span class="sxs-lookup"><span data-stu-id="caff7-121">You can call the [**com_ptr::put_void**](/uwp/cpp-ref-for-winrt/com-ptr#comptrputvoid-function) function to write to an uninitialized smart pointer's underlying raw pointer.</span></span>

```cppwinrt
D2D1CreateFactory(
    D2D1_FACTORY_TYPE_SINGLE_THREADED,
    __uuidof(factory),
    &options,
    factory.put_void()
);
```

<span data-ttu-id="caff7-122">Der obige Code Ruft die [**D2D1CreateFactory**](/windows/desktop/api/d2d1/nf-d2d1-d2d1createfactory) -Funktion, die einen Schnittstellenzeiger **ID2D1Factory1** über die letzte Parameter zurückgibt, hat \*\*Void\ \* \ \*\*\* Typ.</span><span class="sxs-lookup"><span data-stu-id="caff7-122">The code above calls the [**D2D1CreateFactory**](/windows/desktop/api/d2d1/nf-d2d1-d2d1createfactory) function, which returns an **ID2D1Factory1** interface pointer via its last parameter, which has **void\*\*** type.</span></span> <span data-ttu-id="caff7-123">Viele COM-Funktionen zurückgeben einer \*\*Void\ \* \ \*\*\*.</span><span class="sxs-lookup"><span data-stu-id="caff7-123">Many COM functions return a **void\*\***.</span></span> <span data-ttu-id="caff7-124">Verwenden Sie für solche Funktionen [**com_ptr:: put_void**](/uwp/cpp-ref-for-winrt/com-ptr#comptrputvoid-function) wie gezeigt.</span><span class="sxs-lookup"><span data-stu-id="caff7-124">For such functions, use [**com_ptr::put_void**](/uwp/cpp-ref-for-winrt/com-ptr#comptrputvoid-function) as shown.</span></span>

## <a name="com-functions-that-return-a-specific-interface-pointer"></a><span data-ttu-id="caff7-125">COM-Funktionen, die einen bestimmten Schnittstellenzeiger zurückgeben</span><span class="sxs-lookup"><span data-stu-id="caff7-125">COM functions that return a specific interface pointer</span></span>

<span data-ttu-id="caff7-126">Die [**D3D11CreateDevice**](/windows/desktop/api/dwrite/nf-dwrite-dwritecreatefactory) -Funktion gibt einen Schnittstellenzeiger [**ID3D11Device**](https://msdn.microsoft.com/library/Hh404596) über seinen antepenultimate Parameter, der hat \*\*ID3D11Device\ \* \ \*\*\* Typ.</span><span class="sxs-lookup"><span data-stu-id="caff7-126">The [**D3D11CreateDevice**](/windows/desktop/api/dwrite/nf-dwrite-dwritecreatefactory) function returns an [**ID3D11Device**](https://msdn.microsoft.com/library/Hh404596) interface pointer via its antepenultimate parameter, which has **ID3D11Device\*\*** type.</span></span> <span data-ttu-id="caff7-127">Verwenden Sie für die Funktionen, die einen bestimmten Schnittstellenzeiger wie den zurückgeben, [**com_ptr**](/uwp/cpp-ref-for-winrt/com-ptr#comptrput-function).</span><span class="sxs-lookup"><span data-stu-id="caff7-127">For functions that return a specific interface pointer like that, use [**com_ptr::put**](/uwp/cpp-ref-for-winrt/com-ptr#comptrput-function).</span></span>

```cppwinrt
winrt::com_ptr<ID3D11Device> device;
D3D11CreateDevice(
    ...
    device.put(),
    ...);
```

<span data-ttu-id="caff7-128">Im Codebeispiel wird im Abschnitt vor diesem zeigt, wie die unformatierte **D2D1CreateFactory** Funktion aufrufen.</span><span class="sxs-lookup"><span data-stu-id="caff7-128">The code example in the section before this one shows how to call the raw **D2D1CreateFactory** function.</span></span> <span data-ttu-id="caff7-129">Aber tatsächlich, wenn im Codebeispiel für dieses Thema **D2D1CreateFactory**aufruft, verwendet eine Hilfsmethode Funktionsvorlage, die die unformatierte API umschließt und daher im Codebeispiel wird tatsächlich [**com_ptr**](/uwp/cpp-ref-for-winrt/com-ptr#comptrput-function)verwendet.</span><span class="sxs-lookup"><span data-stu-id="caff7-129">But in fact, when the code example for this topic calls **D2D1CreateFactory**, it uses a helper function template that wraps the raw API, and so the code example actually uses [**com_ptr::put**](/uwp/cpp-ref-for-winrt/com-ptr#comptrput-function).</span></span>

```cppwinrt
winrt::com_ptr<ID2D1Factory1> factory;
D2D1CreateFactory(
    D2D1_FACTORY_TYPE_SINGLE_THREADED,
    options,
    factory.put());
```

## <a name="com-functions-that-return-an-interface-pointer-as-iunknown"></a><span data-ttu-id="caff7-130">COM-Funktionen, die einen Schnittstellenzeiger als zurückgeben \*\*IUnknown\ \* \ \*\*\*</span><span class="sxs-lookup"><span data-stu-id="caff7-130">COM functions that return an interface pointer as **IUnknown\*\***</span></span>

<span data-ttu-id="caff7-131">Die Funktion [**DWriteCreateFactory**](/windows/desktop/api/dwrite/nf-dwrite-dwritecreatefactory) gibt einen DirectWrite-Factory-Interface-Zeiger über die letzte Parameter, der verfügt \*\*IUnknown\ \* \ \*\*\* Typ.</span><span class="sxs-lookup"><span data-stu-id="caff7-131">The [**DWriteCreateFactory**](/windows/desktop/api/dwrite/nf-dwrite-dwritecreatefactory) function returns a DirectWrite factory interface pointer via its last parameter, which has **IUnknown\*\*** type.</span></span> <span data-ttu-id="caff7-132">Verwenden Sie für eine solche Funktion [**com_ptr**](/uwp/cpp-ref-for-winrt/com-ptr#comptrput-function), aber Neuinterpretation umgewandelt, um \*\*IUnknown\ \* \ \*\*\*.</span><span class="sxs-lookup"><span data-stu-id="caff7-132">For such a function, use [**com_ptr::put**](/uwp/cpp-ref-for-winrt/com-ptr#comptrput-function), but reinterpret cast that to **IUnknown\*\***.</span></span>

```cppwinrt
DWriteCreateFactory(
    DWRITE_FACTORY_TYPE_SHARED,
    __uuidof(dwriteFactory2),
    reinterpret_cast<IUnknown**>(dwriteFactory2.put()));
```

## <a name="re-seat-a-winrtcomptr"></a><span data-ttu-id="caff7-133">Setzen Sie erneut eine **WinRT:: com_ptr**</span><span class="sxs-lookup"><span data-stu-id="caff7-133">Re-seat a **winrt::com_ptr**</span></span>

> [!IMPORTANT]
> <span data-ttu-id="caff7-134">Wenn Sie eine [**WinRT:: com_ptr**](/uwp/cpp-ref-for-winrt/com-ptr) verfügen, die bereits sitzt (die interne rohzeiger bereits ein Ziel) und Sie es auf ein anderes Objekt erneut setzen möchten, dann müssen Sie zuerst zuweisen `nullptr` darauf&mdash;wie im folgenden Codebeispiel dargestellt.</span><span class="sxs-lookup"><span data-stu-id="caff7-134">If you have a [**winrt::com_ptr**](/uwp/cpp-ref-for-winrt/com-ptr) that's already seated (its internal raw pointer already has a target) and you want to re-seat it to point to a different object, then you first need to assign `nullptr` to it&mdash;as shown in the code example below.</span></span> <span data-ttu-id="caff7-135">Wenn Sie nicht, dann zeichnet ein bereits angeschlossene **Com_ptr** das Problem auf Ihre Aufmerksamkeit (Wenn Sie [**com_ptr**](/uwp/cpp-ref-for-winrt/com-ptr#comptrput-function) oder [**com_ptr:: put_void**](/uwp/cpp-ref-for-winrt/com-ptr#comptrputvoid-function)aufrufen) durch auszugehen, dass die interne Zeiger nicht null ist.</span><span class="sxs-lookup"><span data-stu-id="caff7-135">If you don't, then an already-seated **com_ptr** will draw the issue to your attention (when you call [**com_ptr::put**](/uwp/cpp-ref-for-winrt/com-ptr#comptrput-function) or [**com_ptr::put_void**](/uwp/cpp-ref-for-winrt/com-ptr#comptrputvoid-function)) by asserting that its internal pointer is not null.</span></span>

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

## <a name="handle-hresult-error-codes"></a><span data-ttu-id="caff7-136">Behandeln von HRESULT-Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="caff7-136">Handle HRESULT error codes</span></span>

<span data-ttu-id="caff7-137">Um zu prüfen, dass der Wert für eine HRESULT von einer COM-Funktion zurückgegeben und eine Ausnahme ausgelöst wird, den Fall, dass es sich um einen Fehlercode darstellt, rufen Sie [**WinRT:: check_hresult**](/uwp/cpp-ref-for-winrt/error-handling/check-hresult).</span><span class="sxs-lookup"><span data-stu-id="caff7-137">To check the value of a HRESULT returned from a COM function, and throw an exception in the event that it represents an error code, call [**winrt::check_hresult**](/uwp/cpp-ref-for-winrt/error-handling/check-hresult).</span></span>

```cppwinrt
winrt::check_hresult(D2D1CreateFactory(
    D2D1_FACTORY_TYPE_SINGLE_THREADED,
    __uuidof(factory),
    options,
    factory.put_void()));
```

## <a name="com-functions-that-take-a-specific-interface-pointer"></a><span data-ttu-id="caff7-138">COM-Funktionen, die einen bestimmten Schnittstellenzeiger nutzen</span><span class="sxs-lookup"><span data-stu-id="caff7-138">COM functions that take a specific interface pointer</span></span>

<span data-ttu-id="caff7-139">Sie können die [**com_ptr:: Get**](/uwp/cpp-ref-for-winrt/com-ptr#comptrget-function) -Funktion, um Ihre **Com_ptr** an eine Funktion übergeben, die einen bestimmten Schnittstellenzeiger des gleichen Typs übernimmt aufrufen.</span><span class="sxs-lookup"><span data-stu-id="caff7-139">You can call the [**com_ptr::get**](/uwp/cpp-ref-for-winrt/com-ptr#comptrget-function) function to pass your **com_ptr** to a function that takes a specific interface pointer of the same type.</span></span>

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

## <a name="com-functions-that-take-an-iunknown-interface-pointer"></a><span data-ttu-id="caff7-140">COM-Funktionen, die einen Schnittstellenzeiger **IUnknown** nutzen</span><span class="sxs-lookup"><span data-stu-id="caff7-140">COM functions that take an **IUnknown** interface pointer</span></span>

<span data-ttu-id="caff7-141">Sie können die kostenlose [**winrt::get_unknown**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#getunknown-function) -Funktion, um Ihre **Com_ptr** an eine Funktion übergeben, die einen Schnittstellenzeiger **IUnknown** übernimmt aufrufen.</span><span class="sxs-lookup"><span data-stu-id="caff7-141">You can call the [**winrt::get_unknown**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#getunknown-function) free function to pass your **com_ptr** to a function that takes an **IUnknown** interface pointer.</span></span>

```cppwinrt
winrt::check_hresult(factory->CreateSwapChainForCoreWindow(
    ...
    winrt::get_unknown(CoreWindow::GetForCurrentThread()),
    ...));
```

## <a name="passing-and-returning-com-smart-pointers"></a><span data-ttu-id="caff7-142">Übergeben und Zurückgeben von COM--Zeiger</span><span class="sxs-lookup"><span data-stu-id="caff7-142">Passing and returning COM smart pointers</span></span>

<span data-ttu-id="caff7-143">Eine Funktion, die einen intelligenten COM-Zeiger in Form einer **WinRT:: com_ptr** sollten als konstanten Verweis oder als Verweis tun.</span><span class="sxs-lookup"><span data-stu-id="caff7-143">A function taking a COM smart pointer in the form of a **winrt::com_ptr** should do so by constant reference, or by reference.</span></span>

```cppwinrt
... GetDxgiFactory(winrt::com_ptr<ID3D11Device> const& device) ...

... CreateDevice(..., winrt::com_ptr<ID3D11Device>& device) ...
```

<span data-ttu-id="caff7-144">Eine Funktion, die eine **WinRT:: com_ptr** zurückgibt sollten nach Wert tun.</span><span class="sxs-lookup"><span data-stu-id="caff7-144">A function that returns a **winrt::com_ptr** should do so by value.</span></span>

```cppwinrt
winrt::com_ptr<ID2D1Factory1> CreateFactory() ...
```

## <a name="query-a-com-smart-pointer-for-a-different-interface"></a><span data-ttu-id="caff7-145">Einen intelligenten COM-Zeiger für eine andere Schnittstelle Abfragen</span><span class="sxs-lookup"><span data-stu-id="caff7-145">Query a COM smart pointer for a different interface</span></span>

<span data-ttu-id="caff7-146">Die [**com_ptr:: As**](/uwp/cpp-ref-for-winrt/com-ptr#comptras-function) Funktion können Sie einen intelligenten COM-Zeiger für eine andere Schnittstelle Abfragen.</span><span class="sxs-lookup"><span data-stu-id="caff7-146">You can use the [**com_ptr::as**](/uwp/cpp-ref-for-winrt/com-ptr#comptras-function) function to query a COM smart pointer for a different interface.</span></span> <span data-ttu-id="caff7-147">Die Funktion löst eine Ausnahme aus, wenn die Abfrage nicht erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="caff7-147">The function throws an exception if the query doesn't succeed.</span></span>

```cppwinrt
void ExampleFunction(winrt::com_ptr<ID3D11Device> const& device)
{
    ...
    winrt::com_ptr<IDXGIDevice> const dxdevice{ device.as<IDXGIDevice>() };
    ...
}
```

<span data-ttu-id="caff7-148">Alternativ verwenden [**com_ptr::try_as**](/uwp/cpp-ref-for-winrt/com-ptr#comptrtryas-function), die einen Wert zurückgibt, die Sie vor überprüfen kann `nullptr` um festzustellen, ob die Abfrage erfolgreich war.</span><span class="sxs-lookup"><span data-stu-id="caff7-148">Alternatively, use [**com_ptr::try_as**](/uwp/cpp-ref-for-winrt/com-ptr#comptrtryas-function), which returns a value that you can check against `nullptr` to see whether the query succeeded.</span></span>

## <a name="full-source-code-listing-of-a-minimal-direct2d-application"></a><span data-ttu-id="caff7-149">Vollständige Quelle codeauflistung einer minimalen Direct2D-Anwendung</span><span class="sxs-lookup"><span data-stu-id="caff7-149">Full source code listing of a minimal Direct2D application</span></span>

<span data-ttu-id="caff7-150">Wenn Sie erstellen und diese Quelle Codebeispiel wird anschließend die erste, in Visual Studio ausführen möchten, erstellen Sie ein neues **Core App (C++ / WinRT)**.</span><span class="sxs-lookup"><span data-stu-id="caff7-150">If you want to build and run this source code example then first, in Visual Studio, create a new **Core App (C++/WinRT)**.</span></span> `Direct2D` <span data-ttu-id="caff7-151">ist ein angemessener Namen für das Projekt, aber Sie können nennen Sie es nichts anderes.</span><span class="sxs-lookup"><span data-stu-id="caff7-151">is a reasonable name for the project, but you can name it anything you like.</span></span> <span data-ttu-id="caff7-152">Öffnen `App.cpp`, löschen Sie den gesamten Inhalt, und fügen Sie in den folgenden Eintrag.</span><span class="sxs-lookup"><span data-stu-id="caff7-152">Open `App.cpp`, delete its entire contents, and paste in the listing below.</span></span>

```cppwinrt
#include "pch.h"

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

## <a name="important-apis"></a><span data-ttu-id="caff7-153">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="caff7-153">Important APIs</span></span>
* [<span data-ttu-id="caff7-154">winrt::check_hresult-Funktion</span><span class="sxs-lookup"><span data-stu-id="caff7-154">winrt::check_hresult function</span></span>](/uwp/cpp-ref-for-winrt/error-handling/check-hresult)
* [<span data-ttu-id="caff7-155">winrt::com_ptr Strukturvorlage</span><span class="sxs-lookup"><span data-stu-id="caff7-155">winrt::com_ptr struct template</span></span>](/uwp/cpp-ref-for-winrt/com-ptr)
* [<span data-ttu-id="caff7-156">winrt::Windows::Foundation::IUnknown-Struktur</span><span class="sxs-lookup"><span data-stu-id="caff7-156">winrt::Windows::Foundation::IUnknown struct</span></span>](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown)
