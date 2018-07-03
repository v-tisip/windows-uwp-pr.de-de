---
author: stevewhims
description: In diesem Thema wird gezeigt, wie Sie WRL-Code zum entsprechenden Äquivalent in C++/WinRT portieren.
title: Wechsel zu C++/WinRT von WRL
ms.author: stwhi
ms.date: 05/30/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp, standard, c++, cpp, winrt, projizierung, portieren, migrieren, WRL
ms.localizationpriority: medium
ms.openlocfilehash: b606944f19561828297ef48d4aaebe25fd8a6f6f
ms.sourcegitcommit: 43ce38a4789e0a5194069cc3307cbbc20aa0367e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2018
ms.locfileid: "1934477"
---
# <a name="move-to-cwinrtwindowsuwpcpp-and-winrt-apisintro-to-using-cpp-with-winrt-from-wrl"></a><span data-ttu-id="e5927-104">Wechsel zu [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) von WRL</span><span class="sxs-lookup"><span data-stu-id="e5927-104">Move to [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) from WRL</span></span>
<span data-ttu-id="e5927-105">In diesem Thema wird gezeigt, wie Sie Code der [C++-Vorlagenbibliothek für Windows-Runtime (WRL)](/cpp/windows/windows-runtime-cpp-template-library-wrl) zum entsprechenden Äquivalent in C++/WinRT portieren.</span><span class="sxs-lookup"><span data-stu-id="e5927-105">This topic shows how to port [Windows Runtime C++ Template Library (WRL)](/cpp/windows/windows-runtime-cpp-template-library-wrl) code to its equivalent in C++/WinRT.</span></span>

<span data-ttu-id="e5927-106">Der erste Schritt beim Portieren zu C++/WinRT besteht darin, C++/WinRT-Unterstützung Ihrem Projekt manuell hinzuzufügen (siehe [Visual Studio-Unterstützung für C++/WinRT und VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix)).</span><span class="sxs-lookup"><span data-stu-id="e5927-106">The first step in porting to C++/WinRT is to manually add C++/WinRT support to your project (see [Visual Studio support for C++/WinRT, and the VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix)).</span></span> <span data-ttu-id="e5927-107">Bearbeiten Sie dazu Ihre `.vcxproj`-Datei, suchen Sie nach `<PropertyGroup Label="Globals">`, und definieren Sie innerhalb dieser Eigenschaftengruppe die Eigenschaft `<CppWinRTEnabled>true</CppWinRTEnabled>`.</span><span class="sxs-lookup"><span data-stu-id="e5927-107">To do that, edit your `.vcxproj` file, find `<PropertyGroup Label="Globals">` and, inside that property group, set the property `<CppWinRTEnabled>true</CppWinRTEnabled>`.</span></span> <span data-ttu-id="e5927-108">Eine Auswirkung dieser Änderung ist, dass die Unterstützung für C++/CX im Projekt deaktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="e5927-108">One effect of that change is that support for C++/CX is turned off in the project.</span></span> <span data-ttu-id="e5927-109">Wenn Sie C++/CX im Projekt verwenden, können Sie die Unterstützung deaktiviert lassen und Ihren C++/CX-Code in C++/WinRT aktualisieren (siehe [Wechsel zu C++/WinRT von C++/CX](move-to-winrt-from-cx.md)).</span><span class="sxs-lookup"><span data-stu-id="e5927-109">If you're using C++/CX in the project, then you can leave support turned off and update your C++/CX code to C++/WinRT as well (see [Move to C++/WinRT from C++/CX](move-to-winrt-from-cx.md)).</span></span> <span data-ttu-id="e5927-110">Sie können die Unterstützung auch wieder aktivieren (in den Projekteigenschaften, **C/C++** \> **Allgemein** \> **Windows-Runtime-Erweiterung verwenden** \> **Ja (/ZW)**), und sich zunächst auf das Portieren des WRL-Codes konzentrieren.</span><span class="sxs-lookup"><span data-stu-id="e5927-110">Or you can turn support back on (in project properties, **C/C++** \> **General** \> **Consume Windows Runtime Extension** \> **Yes (/ZW)**), and first focus on porting your WRL code.</span></span>

<span data-ttu-id="e5927-111">Definieren Sie die Projekteigenschaft **Allgemein** \> **Zielplattformversion** mit 10.0.17134.0 (Windows 10, Version 1803) oder höher.</span><span class="sxs-lookup"><span data-stu-id="e5927-111">Set project property **General** \> **Target Platform Version** to 10.0.17134.0 (Windows 10, version 1803) or greater.</span></span>

<span data-ttu-id="e5927-112">Fügen Sie Ihrer vorkompilierten Headerdatei (in der Regel `pch.h`) `winrt/base.h` hinzu.</span><span class="sxs-lookup"><span data-stu-id="e5927-112">In your precompiled header file (usually `pch.h`), include `winrt/base.h`.</span></span>

```cppwinrt
#include <winrt/base.h>
```

<span data-ttu-id="e5927-113">Wenn Sie alle C++/WinRT-projizierten Windows-API-Header hinzufügen (z.B. `winrt/Windows.Foundation.h`), müssen Sie `winrt/base.h` nicht explizit einschließen, da dies automatisch erfolgt.</span><span class="sxs-lookup"><span data-stu-id="e5927-113">If you include any C++/WinRT projected Windows API headers (for example, `winrt/Windows.Foundation.h`), then you don't need to explicitly include `winrt/base.h` like this because it will be included automatically for you.</span></span>

## <a name="porting-wrl-com-smart-pointers-microsoftwrlcomptrcppwindowscomptr-class"></a><span data-ttu-id="e5927-114">Portieren von intelligenten WRL-COM-Zeigern ([Microsoft::WRL::ComPtr](/cpp/windows/comptr-class))</span><span class="sxs-lookup"><span data-stu-id="e5927-114">Porting WRL COM smart pointers ([Microsoft::WRL::ComPtr](/cpp/windows/comptr-class))</span></span>
<span data-ttu-id="e5927-115">Portieren Sie jeglichen Code, der **Microsoft::WRL::ComPtr\<T\>** verwendet, um [**winrt::com_ptr\<T\>**](/uwp/cpp-ref-for-winrt/com-ptr) zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="e5927-115">Port any code that uses **Microsoft::WRL::ComPtr\<T\>** to use [**winrt::com_ptr\<T\>**](/uwp/cpp-ref-for-winrt/com-ptr).</span></span> <span data-ttu-id="e5927-116">Im Folgenden finden Sie ein Codebeispiel für „Vorher“ und „Nachher“:</span><span class="sxs-lookup"><span data-stu-id="e5927-116">Here's a before-and-after code example.</span></span> <span data-ttu-id="e5927-117">In der *Nachher*-Version ruft die [**com_ptr::put**](/uwp/cpp-ref-for-winrt/com-ptr#comptrput-function)-Mitgliedsfunktion den zugrunde liegenden Rohzeiger ab, sodass dieser definiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="e5927-117">In the *after* version, the [**com_ptr::put**](/uwp/cpp-ref-for-winrt/com-ptr#comptrput-function) member function retrieves the underlying raw pointer so that it can be set.</span></span>

```cpp
ComPtr<IDXGIAdapter1> previousDefaultAdapter;
DX::ThrowIfFailed(m_dxgiFactory->EnumAdapters1(0, &previousDefaultAdapter));
```

```cppwinrt
winrt::com_ptr<IDXGIAdapter1> previousDefaultAdapter;
winrt::check_hresult(m_dxgiFactory->EnumAdapters1(0, previousDefaultAdapter.put()));
```

<span data-ttu-id="e5927-118">Im nächsten Beispiel (in der *Nachher* Version) ruft die [**com_ptr::put_void**](/uwp/cpp-ref-for-winrt/com-ptr#comptrputvoid-function)-Mitgliedfunktion den zugrunde liegenden normalen Zeiger als einen Zeiger auf einen Zeiger auf „void“ ab.</span><span class="sxs-lookup"><span data-stu-id="e5927-118">In this next example (in the *after* version), the [**com_ptr::put_void**](/uwp/cpp-ref-for-winrt/com-ptr#comptrputvoid-function) member function retrieves the underlying raw pointer as a pointer to a pointer to void.</span></span>

```cpp
ComPtr<ID3D12Debug> debugController;
if (SUCCEEDED(D3D12GetDebugInterface(IID_PPV_ARGS(&debugController))))
{
    debugController->EnableDebugLayer();
}
```

```cppwinrt
winrt::com_ptr<ID3D12Debug> debugController;
if (SUCCEEDED(D3D12GetDebugInterface(__uuidof(debugController), debugController.put_void())))
{
    debugController->EnableDebugLayer();
}
```

<span data-ttu-id="e5927-119">Ersetzen Sie **ComPtr::Get** durch [**com_ptr::get**](/uwp/cpp-ref-for-winrt/com-ptr#comptrget-function).</span><span class="sxs-lookup"><span data-stu-id="e5927-119">Replace **ComPtr::Get** with [**com_ptr::get**](/uwp/cpp-ref-for-winrt/com-ptr#comptrget-function).</span></span>

```cpp
m_d3dDevice->CreateDepthStencilView(m_depthStencil.Get(), &dsvDesc, m_dsvHeap->GetCPUDescriptorHandleForHeapStart());
```

```cppwinrt
m_d3dDevice->CreateDepthStencilView(m_depthStencil.get(), &dsvDesc, m_dsvHeap->GetCPUDescriptorHandleForHeapStart());
```

<span data-ttu-id="e5927-120">Wenn Sie den zugrunde liegenden Rohzeiger an eine Funktion übergeben möchten, der einen Zeiger auf **IUnknown** erwartet, verwenden Sie die Funktion [**IUnknown::get_unknown**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#getunknown-function), wie im nächsten Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="e5927-120">When you want to pass the underlying raw pointer to a function that expects a pointer to **IUnknown**, use the [**IUnknown::get_unknown**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#getunknown-function) function, as shown in this next example.</span></span>

```cpp
ComPtr<IDXGISwapChain1> swapChain;
DX::ThrowIfFailed(
    m_dxgiFactory->CreateSwapChainForCoreWindow(
        m_commandQueue.Get(),
        reinterpret_cast<IUnknown*>(m_window.Get()),
        &swapChainDesc,
        nullptr,
        &swapChain
    )
);
```

```cppwinrt
winrt::agile_ref<winrt::Windows::UI::Core::CoreWindow> m_window; 
winrt::com_ptr<IDXGISwapChain1> swapChain;
winrt::check_hresult(
    m_dxgiFactory->CreateSwapChainForCoreWindow(
        m_commandQueue.get(),
        winrt::get_unknown(m_window.get()),
        &swapChainDesc,
        nullptr,
        swapChain.put()
    )
);
```

## <a name="porting-a-wrl-module-microsoftwrlmodule"></a><span data-ttu-id="e5927-121">Portieren eines WRL-Moduls ([Microsoft::WRL::Module]())</span><span class="sxs-lookup"><span data-stu-id="e5927-121">Porting a WRL module ([Microsoft::WRL::Module]())</span></span>
<span data-ttu-id="e5927-122">Sie können nach und nach C++/WinRT-Code zu einem vorhandenen Projekt hinzufügen, das WRL verwendet, um eine Komponente zu implementieren; Ihre vorhandenen WRL-Klassen werden weiterhin unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e5927-122">You can gradually add C++/WinRT code to an existing project that uses WRL to implement a component, and your existing WRL classes will continue to be supported.</span></span> <span data-ttu-id="e5927-123">Dieser Abschnitt zeigt, wie das geht.</span><span class="sxs-lookup"><span data-stu-id="e5927-123">This section shows how.</span></span>

<span data-ttu-id="e5927-124">Wenn Sie einen neuen Projekttyp **Komponente für Windows-Runtime (C++/WinRT)** in Visual Studio erstellen und erzeugen, wird die Datei `Generated Files\module.g.cpp` für Sie generiert.</span><span class="sxs-lookup"><span data-stu-id="e5927-124">If you create a new **Windows Runtime Component (C++/WinRT)** project type in Visual Studio, and build, then the file `Generated Files\module.g.cpp` is generated for you.</span></span> <span data-ttu-id="e5927-125">Diese Datei enthält die Definitionen von zwei nützlichen C++/WinRT-Funktionen (siehe unten), die Sie kopieren und dem Projekt hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="e5927-125">That file contains the definitions of two useful C++/WinRT functions (listed out below), which you can copy and add to your project.</span></span> <span data-ttu-id="e5927-126">Diese Funktionen sind **WINRT_CanUnloadNow** und **WINRT_GetActivationFactory**. Wie Sie sehen können, rufen diese bedingt WRL auf, um Sie in jedem Portierungsstadium zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="e5927-126">Those function are **WINRT_CanUnloadNow** and **WINRT_GetActivationFactory** and, as you can see, they conditionally call WRL in order to support you whatever stage of porting you're at.</span></span>

```cppwinrt
HRESULT WINRT_CALL WINRT_CanUnloadNow()
{
#ifdef _WRL_MODULE_H_
    if (!::Microsoft::WRL::Module<::Microsoft::WRL::InProc>::GetModule().Terminate())
    {
        return S_FALSE;
    }
#endif

    if (winrt::get_module_lock())
    {
        return S_FALSE;
    }

    winrt::clear_factory_cache();
    return S_OK;
}

HRESULT WINRT_CALL WINRT_GetActivationFactory(HSTRING classId, void** factory)
{
    try
    {
        *factory = nullptr;
        wchar_t const* const name = WINRT_WindowsGetStringRawBuffer(classId, nullptr);

        if (0 == wcscmp(name, L"MoveFromWRLTest.Class"))
        {
            *factory = winrt::detach_abi(winrt::make<winrt::MoveFromWRLTest::factory_implementation::Class>());
            return S_OK;
        }

#ifdef _WRL_MODULE_H_
        return ::Microsoft::WRL::Module<::Microsoft::WRL::InProc>::GetModule().GetActivationFactory(classId, reinterpret_cast<::IActivationFactory**>(factory));
#else
        return winrt::hresult_class_not_available().to_abi();
#endif
    }
    catch (...) { return winrt::to_hresult(); }
}
```

<span data-ttu-id="e5927-127">Nachdem Sie diese Funktionen Ihrem Projekt hinzugefügt haben, rufen Sie, anstatt [**Module::GetActivationFactory**](/cpp/windows/module-getactivationfactory-method) direkt aufzurufen, **WINRT_GetActivationFactory** auf (die die WRL-Funktion intern aufruft).</span><span class="sxs-lookup"><span data-stu-id="e5927-127">Once you have these functions in your project, instead of calling [**Module::GetActivationFactory**](/cpp/windows/module-getactivationfactory-method) directly, call **WINRT_GetActivationFactory** (which calls the WRL function internally).</span></span> <span data-ttu-id="e5927-128">Im Folgenden finden Sie ein Codebeispiel für „Vorher“ und „Nachher“:</span><span class="sxs-lookup"><span data-stu-id="e5927-128">Here's a before-and-after code example.</span></span>

```cpp
HRESULT WINAPI DllGetActivationFactory(_In_ HSTRING activatableClassId, _Out_ ::IActivationFactory **factory)
{
    auto & module = Microsoft::WRL::Module<Microsoft::WRL::InProc>::GetModule();
    return module.GetActivationFactory(activatableClassId, factory);
}
```

```cppwinrt
HRESULT __stdcall WINRT_GetActivationFactory(HSTRING activatableClassId, void** factory);
HRESULT WINAPI DllGetActivationFactory(_In_ HSTRING activatableClassId, _Out_ ::IActivationFactory **factory)
{
    return WINRT_GetActivationFactory(activatableClassId, reinterpret_cast<void**>(factory));
}
```

<span data-ttu-id="e5927-129">Anstatt [**Module::Terminate**](/cpp/windows/module-terminate-method) direkt aufzurufen, rufen Sie **WINRT_CanUnloadNow** auf (die die WRL Funktion intern aufruft).</span><span class="sxs-lookup"><span data-stu-id="e5927-129">Instead of calling [**Module::Terminate**](/cpp/windows/module-terminate-method) directly, call **WINRT_CanUnloadNow** (which calls the WRL function internally).</span></span> <span data-ttu-id="e5927-130">Im Folgenden finden Sie ein Codebeispiel für „Vorher“ und „Nachher“:</span><span class="sxs-lookup"><span data-stu-id="e5927-130">Here's a before-and-after code example.</span></span>

```cpp
HRESULT __stdcall DllCanUnloadNow(void)
{
    auto &module = Microsoft::WRL::Module<Microsoft::WRL::InProc>::GetModule();
    HRESULT hr = (module.Terminate() ? S_OK : S_FALSE);
    if (hr == S_OK)
    {
        hr = ...
    }
    return hr;
}
```

```cppwinrt
HRESULT __stdcall WINRT_CanUnloadNow();
HRESULT __stdcall DllCanUnloadNow(void)
{
    HRESULT hr = WINRT_CanUnloadNow();
    if (hr == S_OK)
    {
        hr = ...
    }
    return hr;
}
```

## <a name="important-apis"></a><span data-ttu-id="e5927-131">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="e5927-131">Important APIs</span></span>
* [<span data-ttu-id="e5927-132">winrt::com_ptr</span><span class="sxs-lookup"><span data-stu-id="e5927-132">winrt::com_ptr</span></span>](/uwp/cpp-ref-for-winrt/com-ptr)
* [<span data-ttu-id="e5927-133">winrt::Windows::Foundation::IUnknown-Struktur</span><span class="sxs-lookup"><span data-stu-id="e5927-133">winrt::Windows::Foundation::IUnknown struct</span></span>](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown)

## <a name="related-topics"></a><span data-ttu-id="e5927-134">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="e5927-134">Related topics</span></span>
* [<span data-ttu-id="e5927-135">Einführung in C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="e5927-135">Introduction to C++/WinRT</span></span>](intro-to-using-cpp-with-winrt.md)
* [<span data-ttu-id="e5927-136">Wechsel zu C++/WinRT von C++/CX</span><span class="sxs-lookup"><span data-stu-id="e5927-136">Move to C++/WinRT from C++/CX</span></span>](move-to-winrt-from-cx.md)
* [<span data-ttu-id="e5927-137">C++-Vorlagenbibliothek für Windows-Runtime (WRL)</span><span class="sxs-lookup"><span data-stu-id="e5927-137">Windows Runtime C++ Template Library (WRL)</span></span>](/cpp/windows/windows-runtime-cpp-template-library-wrl)
