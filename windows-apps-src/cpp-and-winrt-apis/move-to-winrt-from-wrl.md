---
author: stevewhims
description: In diesem Thema wird gezeigt, wie Sie WRL-Code zum entsprechenden Äquivalent in C++/WinRT portieren.
title: Wechsel zu C++/WinRT von WRL
ms.author: stwhi
ms.date: 05/30/2018
ms.topic: article
keywords: windows 10, uwp, standard, c++, cpp, winrt, projizierung, portieren, migrieren, WRL
ms.localizationpriority: medium
ms.openlocfilehash: c0fd9be96b0709651ee31f58b0d87227cd5115e0
ms.sourcegitcommit: 9f8010fe67bb3372db1840de9f0be36097ed6258
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "7100726"
---
# <a name="move-to-cwinrt-from-wrl"></a>Von WRL zu C++/WinRT wechseln
Dieses Thema zeigt, wie Sie zum entsprechenden Äquivalent in [C++ für Windows-Runtime-Bibliothek (WRL)](/cpp/windows/windows-runtime-cpp-template-library-wrl) portiert [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt).

Der erste Schritt beim Portieren zu C++/WinRT besteht darin, C++/WinRT-Unterstützung Ihrem Projekt manuell hinzuzufügen (siehe [Visual Studio-Unterstützung für C++/WinRT und VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix)). Bearbeiten Sie dazu Ihre `.vcxproj`-Datei, suchen Sie nach `<PropertyGroup Label="Globals">`, und definieren Sie innerhalb dieser Eigenschaftengruppe die Eigenschaft `<CppWinRTEnabled>true</CppWinRTEnabled>`. Eine Auswirkung dieser Änderung ist diese Unterstützung für [C++ / CX](/cpp/cppcx/visual-c-language-reference-c-cx) im Projekt deaktiviert ist. Wenn Sie C++/CX im Projekt verwenden, können Sie die Unterstützung deaktiviert lassen und Ihren C++/CX-Code in C++/WinRT aktualisieren (siehe [Wechsel zu C++/WinRT von C++/CX](move-to-winrt-from-cx.md)). Sie können die Unterstützung auch wieder aktivieren (in den Projekteigenschaften, **C/C++** \> **Allgemein** \> **Windows-Runtime-Erweiterung verwenden** \> **Ja (/ZW)**), und sich zunächst auf das Portieren des WRL-Codes konzentrieren. C++ / CX- und C++ / WinRT-Code kann im selben Projekt, mit Ausnahme der XAML-Compiler-Unterstützung und Windows-Runtime-Komponenten gleichzeitig verwendet werden (siehe [Wechsel zu C++ / WinRT von C++ / CX](move-to-winrt-from-cx.md)).

Definieren Sie die Projekteigenschaft **Allgemein** \> **Zielplattformversion** mit 10.0.17134.0 (Windows 10, Version 1803) oder höher.

Fügen Sie Ihrer vorkompilierten Headerdatei (in der Regel `pch.h`) `winrt/base.h` hinzu.

```cppwinrt
#include <winrt/base.h>
```

Wenn Sie alle C++/WinRT-projizierten Windows-API-Header hinzufügen (z.B. `winrt/Windows.Foundation.h`), müssen Sie `winrt/base.h` nicht explizit einschließen, da dies automatisch erfolgt.

## <a name="porting-wrl-com-smart-pointers-microsoftwrlcomptrcppwindowscomptr-class"></a>Portieren von intelligenten WRL-COM-Zeigern ([Microsoft::WRL::ComPtr](/cpp/windows/comptr-class))
Portieren Sie jeglichen Code, der **Microsoft::WRL::ComPtr\<T\>** verwendet, um [**winrt::com_ptr\<T\>**](/uwp/cpp-ref-for-winrt/com-ptr) zu verwenden. Im Folgenden finden Sie ein Codebeispiel für „Vorher“ und „Nachher“: In der *Nachher*-Version ruft die [**com_ptr::put**](/uwp/cpp-ref-for-winrt/com-ptr#comptrput-function)-Mitgliedsfunktion den zugrunde liegenden Rohzeiger ab, sodass dieser definiert werden kann.

```cpp
ComPtr<IDXGIAdapter1> previousDefaultAdapter;
DX::ThrowIfFailed(m_dxgiFactory->EnumAdapters1(0, &previousDefaultAdapter));
```

```cppwinrt
winrt::com_ptr<IDXGIAdapter1> previousDefaultAdapter;
winrt::check_hresult(m_dxgiFactory->EnumAdapters1(0, previousDefaultAdapter.put()));
```

> [!IMPORTANT]
> Wenn Sie eine [**WinRT:: com_ptr**](/uwp/cpp-ref-for-winrt/com-ptr) verfügen, die bereits sitzt (seine interne rohzeiger hat bereits ein Ziel) und möchten Sie es auf ein anderes Objekt verweisen erneut einzusetzen, dann müssen Sie zuerst zuweisen `nullptr` darauf&mdash;wie im folgenden Codebeispiel dargestellt. Falls nicht, dann zeichnet ein bereits angeschlossene **Com_ptr** das Problem auf Ihre Aufmerksamkeit (Wenn Sie [**com_ptr**](/uwp/cpp-ref-for-winrt/com-ptr#comptrput-function) oder [**com_ptr:: put_void**](/uwp/cpp-ref-for-winrt/com-ptr#comptrputvoid-function)aufrufen) durch die Assertion, dass die interne Zeiger nicht null ist.

```cppwinrt
winrt::com_ptr<IDXGISwapChain1> m_pDXGISwapChain1;
...
// We execute the code below each time the window size changes.
m_pDXGISwapChain1 = nullptr; // Important because we're about to re-seat 
winrt::check_hresult(
    m_pDxgiFactory->CreateSwapChainForHwnd(
        m_pCommandQueue.get(), // For Direct3D 12, this is a pointer to a direct command queue, and not to the device.
        m_hWnd,
        &swapChainDesc,
        nullptr,
        nullptr,
        m_pDXGISwapChain1.put())
);
```

Im nächsten Beispiel (in der *Nachher* Version) ruft die [**com_ptr::put_void**](/uwp/cpp-ref-for-winrt/com-ptr#comptrputvoid-function)-Mitgliedfunktion den zugrunde liegenden normalen Zeiger als einen Zeiger auf einen Zeiger auf „void“ ab.

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

Ersetzen Sie **ComPtr::Get** durch [**com_ptr::get**](/uwp/cpp-ref-for-winrt/com-ptr#comptrget-function).

```cpp
m_d3dDevice->CreateDepthStencilView(m_depthStencil.Get(), &dsvDesc, m_dsvHeap->GetCPUDescriptorHandleForHeapStart());
```

```cppwinrt
m_d3dDevice->CreateDepthStencilView(m_depthStencil.get(), &dsvDesc, m_dsvHeap->GetCPUDescriptorHandleForHeapStart());
```

Wenn Sie den zugrunde liegenden rohzeiger an eine Funktion übergeben, die einen Zeiger auf **IUnknown**erwartet möchten, verwenden Sie die kostenlose [**winrt::get_unknown**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#getunknown-function) -Funktion, wie im nächsten Beispiel gezeigt.

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

## <a name="porting-a-wrl-module-microsoftwrlmodule"></a>Portieren eines WRL-Moduls ([Microsoft::WRL::Module]())
Sie können nach und nach C++/WinRT-Code zu einem vorhandenen Projekt hinzufügen, das WRL verwendet, um eine Komponente zu implementieren; Ihre vorhandenen WRL-Klassen werden weiterhin unterstützt. Dieser Abschnitt zeigt, wie das geht.

Wenn Sie einen neuen Projekttyp **Komponente für Windows-Runtime (C++/WinRT)** in Visual Studio erstellen und erzeugen, wird die Datei `Generated Files\module.g.cpp` für Sie generiert. Diese Datei enthält die Definitionen von zwei nützlichen C++/WinRT-Funktionen (siehe unten), die Sie kopieren und dem Projekt hinzufügen können. Diese Funktionen sind **WINRT_CanUnloadNow** und **WINRT_GetActivationFactory**. Wie Sie sehen können, rufen diese bedingt WRL auf, um Sie in jedem Portierungsstadium zu unterstützen.

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

Nachdem Sie diese Funktionen Ihrem Projekt hinzugefügt haben, rufen Sie, anstatt [**Module::GetActivationFactory**](/cpp/windows/module-getactivationfactory-method) direkt aufzurufen, **WINRT_GetActivationFactory** auf (die die WRL-Funktion intern aufruft). Im Folgenden finden Sie ein Codebeispiel für „Vorher“ und „Nachher“:

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

Anstatt [**Module::Terminate**](/cpp/windows/module-terminate-method) direkt aufzurufen, rufen Sie **WINRT_CanUnloadNow** auf (die die WRL Funktion intern aufruft). Im Folgenden finden Sie ein Codebeispiel für „Vorher“ und „Nachher“:

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

## <a name="important-apis"></a>Wichtige APIs
* [winrt::com_ptr Strukturvorlage](/uwp/cpp-ref-for-winrt/com-ptr)
* [winrt::Windows::Foundation::IUnknown-Struktur](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown)

## <a name="related-topics"></a>Verwandte Themen
* [Einführung in C++/WinRT](intro-to-using-cpp-with-winrt.md)
* [Wechsel zu C++/WinRT von C++/CX](move-to-winrt-from-cx.md)
* [C++-Vorlagenbibliothek für Windows-Runtime (WRL)](/cpp/windows/windows-runtime-cpp-template-library-wrl)
