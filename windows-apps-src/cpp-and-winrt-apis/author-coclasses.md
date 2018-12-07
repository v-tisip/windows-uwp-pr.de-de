---
description: C++ / WinRT hilft Ihnen beim Erstellen von klassischer COM-Komponenten genauso, wie sie Windows-Runtime-Klassen erstellen kann.
title: Erstellen von COM-Komponenten mit C++ / WinRT
ms.date: 09/06/2018
ms.topic: article
keywords: Windows 10, Uwp, Standard, c++, Cpp, Winrt, Projektion, Autor, COM, Komponente
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: e6b77f8be6c75070336ad48f0c6471fc0a824a4c
ms.sourcegitcommit: a3dc929858415b933943bba5aa7487ffa721899f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "8783528"
---
# <a name="author-com-components-with-cwinrt"></a>Erstellen von COM-Komponenten mit C++ / WinRT

[C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) hilft Ihnen beim klassischen Component Object Model (COM)-Komponenten (oder Co-Klassen), erstellen genauso, wie sie Windows-Runtime-Klassen erstellen kann. Hier ist eine einfache Darstellung, die Sie testen können, wenn Sie den Code in Einfügen der `pch.h` und `main.cpp` eines neuen **Windows Console Application (C++ / WinRT)** Projekt.

```cppwinrt
// pch.h
#pragma once
#include <unknwn.h>
#include <winrt/Windows.Foundation.h>

// main.cpp : Defines the entry point for the console application.
#include "pch.h"

struct __declspec(uuid("ddc36e02-18ac-47c4-ae17-d420eece2281")) IMyComInterface : ::IUnknown
{
    virtual HRESULT __stdcall Call() = 0;
};

using namespace winrt;
using namespace Windows::Foundation;

int main()
{
    winrt::init_apartment();

    struct MyCoclass : winrt::implements<MyCoclass, IPersist, IStringable, IMyComInterface>
    {
        HRESULT __stdcall Call() noexcept override
        {
            return S_OK;
        }

        HRESULT __stdcall GetClassID(CLSID* id) noexcept override
        {
            *id = IID_IPersist; // Doesn't matter what we return, for this example.
            return S_OK;
        }

        winrt::hstring ToString()
        {
            return L"MyCoclass as a string";
        }
    };

    auto mycoclass_instance{ winrt::make<MyCoclass>() };
    CLSID id{};
    winrt::check_hresult(mycoclass_instance->GetClassID(&id));
    winrt::check_hresult(mycoclass_instance.as<IMyComInterface>()->Call());
}
```

Weitere Informationen finden Sie [nutzen COM-Komponenten mit C++ / WinRT](consume-com.md).

## <a name="a-more-realistic-and-interesting-example"></a>Eine realistische und interessante-Beispiel

Im verbleibenden Teil dieses Thema führt durch die Erstellung von einem Anwendungsprojekt der minimale Konsole, die verwendet, C++ / WinRT zur Implementierung einer grundlegenden Co-Klasse (COM-Komponente oder COM-Klasse) und die Klassenfactory. Die Anwendung Beispiel zeigt, wie Sie eine Popupbenachrichtigung mit einer Schaltfläche Rückruf darauf bereitzustellen und die Co-Klasse (die die **INotificationActivationCallback** COM-Schnittstelle implementiert) ermöglicht die Anwendung gestartet und aufgerufen werden zurück, wenn der Benutzer auf diese Schaltfläche im Popup klickt.

Weitere Hintergrundinformationen zu Popup-Infobereich Feature finden Sie unter [einer lokalen Popupbenachrichtigung senden](/windows/uwp/design/shell/tiles-and-notifications/send-local-toast). Verwenden Sie keine die Codebeispiele in diesem Abschnitt der Dokumentation C++ / WinRT jedoch, es wird empfohlen, dass Sie den Code in diesem Thema bevorzugen.

## <a name="create-a-windows-console-application-project-toastandcallback"></a>Erstellen eines Projekts Windows Console Application (ToastAndCallback)

Erstellen Sie zunächst ein neues Projekt in Microsoft Visual Studio. Erstellen Sie ein **Visual C++** > **Windows-Desktop** > **Windows Console Application (C++ / WinRT)** Projekt und nennen Sie es *ToastAndCallback*.

Öffnen `pch.h`, und fügen `#include <unknwn.h>` vor der enthält für alle C++ / WinRT-Header.

```cppwinrt
// pch.h
#pragma once
#include <unknwn.h>
#include <winrt/Windows.Foundation.h>
```

Öffnen `main.cpp`, und entfernen Sie die Verwendung von-Direktiven, die die Projektvorlage generiert. Fügen Sie in ihren Platz den folgenden Code (der ermöglichte die Bibliotheken, Header und geben Sie die Namen, die wir benötigen).

```cppwinrt
#pragma comment(lib, "shell32")

#include <iomanip>
#include <iostream>
#include <notificationactivationcallback.h>
#include <propkey.h>
#include <propvarutil.h>
#include <shlobj.h>
#include <winrt/Windows.UI.Notifications.h>
#include <winrt/Windows.Data.Xml.Dom.h>

using namespace winrt;
using namespace Windows::Data::Xml::Dom;
using namespace Windows::UI::Notifications;
```

## <a name="implement-the-coclass-and-class-factory"></a>Implementieren Sie die Factory CO- und -Klasse

In C++ / WinRT können Sie Co-Klassen, und implementieren Klassenfactorys, durch eine Ableitung von der [**WinRT:: Implements**](/uwp/cpp-ref-for-winrt/implements) Basisstruktur. Unmittelbar nach der drei using-Direktiven oben gezeigten (und vor `main`), fügen Sie diesen Code, um Ihre Popupbenachrichtigung Benachrichtigung COM-Aktivator-Komponente zu implementieren.

```cppwinrt
static constexpr GUID callback_guid // BAF2FA85-E121-4CC9-A942-CE335B6F917F
{
    0xBAF2FA85, 0xE121, 0x4CC9, {0xA9, 0x42, 0xCE, 0x33, 0x5B, 0x6F, 0x91, 0x7F}
};

std::wstring const this_app_name{ L"ToastAndCallback" };

struct callback : winrt::implements<callback, INotificationActivationCallback>
{
    HRESULT __stdcall Activate(
        LPCWSTR app,
        LPCWSTR args,
        [[maybe_unused]] NOTIFICATION_USER_INPUT_DATA const* data,
        [[maybe_unused]] ULONG count) noexcept final
    {
        try
        {
            std::wcout << this_app_name << L" has been called back from a notification." << std::endl;
            std::wcout << L"Value of the 'app' parameter is '" << app << L"'." << std::endl;
            std::wcout << L"Value of the 'args' parameter is '" << args << L"'." << std::endl;
            return S_OK;
        }
        catch (...)
        {
            return winrt::to_hresult();
        }
    }
};

struct callback_factory : implements<callback_factory, IClassFactory>
{
    HRESULT __stdcall CreateInstance(
        IUnknown* outer,
        GUID const& iid,
        void** result) noexcept final
    {
        *result = nullptr;

        if (outer)
        {
            return CLASS_E_NOAGGREGATION;
        }

        return make<callback>()->QueryInterface(iid, result);
    }

    HRESULT __stdcall LockServer(BOOL) noexcept final
    {
        return S_OK;
    }
};
```

Die Implementierung der oben genannten Co-folgt das gleiche Muster, die im Code gezeigt wird [Erstellen von APIs mit C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/author-apis#if-youre-not-authoring-a-runtime-class). Daher können Sie das gleiche Verfahren verwenden, um COM-Schnittstellen als auch für Windows-Runtime-Schnittstellen implementieren. Verfügbar machen ihre Funktionen über Schnittstellen, COM-Komponenten und Windows-Runtime-Klassen. Jede COM-Schnittstelle ist letztlich von [**IUnknown**](https://msdn.microsoft.com/library/windows/desktop/ms680509) -Schnittstelle. Die Windows-Runtime basiert auf COM&mdash;eine Unterscheidung wird, die Windows-Runtime-Schnittstellen ableiten letztendlich die [**IInspectable-Schnittstelle**](/windows/desktop/api/inspectable/nn-inspectable-iinspectable) (und **IInspectable** von **IUnknown**abgeleitet).

In der Co-Klasse in der obige Code implementieren wir die **INotificationActivationCallback::Activate** -Methode, die die Funktion, die aufgerufen wird, wenn der Benutzer auf eine Popupbenachrichtigung die Callback-Schaltfläche klickt. Aber bevor diese Funktion aufgerufen werden kann, muss eine Instanz der Co-erstellt werden und der Auftrag der **IClassFactory:: CreateInstance** -Funktion ist.

Die Co-Klasse, die wir gerade implementiert wird als die *COM-Aktivator* für Benachrichtigungen bezeichnet und hat die Klassen-Id (CLSID) in Form von der `callback_guid` Bezeichner ( **GUID**-Typ), die oben angezeigt. Wir werden diesen Bezeichner später in Form einer Verknüpfung im Startmenü und die Eingabe eines Windows-Registrierung verwenden. Die COM-Aktivator CLSID und den Pfad zu den entsprechenden COM-Server (die den Pfad zu der ausführbaren Datei, die wir hier erstellen) ist der Mechanismus, mit der eine Popupbenachrichtigung weiß, welche Klasse erstellt eine Instanz der bei die Callback-Schaltfläche geklickt wird (an, ob die Benachrichtigung wird im Info-Center oder nicht geklickt).

## <a name="best-practices-for-implementing-com-methods"></a>Bewährte Methoden für die Implementierung von COM-Methoden

Techniken für die Fehlerbehandlung und zur Verwaltung von Hand in Hand zu gelangen. Es ist praktisch und praktische Ausnahmen als Fehlercodes verwendet werden. Und wenn Sie die Ressource Erwerb ist Initialisierung (RAII) Ausdrucksweise einsetzen, dann können nicht explizit Fehlercodes überprüfen und dann durch die explizite Freigabe von Ressourcen. Expliziten Kontrollen gestalten Sie Ihre mehr als notwendig entwickelt und gibt Fehler ausreichend stellen ausblenden. Verwenden Sie stattdessen RAII, und Ausnahmen auslösen/Catch. Auf diese Weise können die Ressource Zuordnungen sind ausnahmesicheren und Ihren Code ist einfach.

Sie darf nicht jedoch Ausnahmen für die Implementierung der COM-Methode als Escapezeichen zulassen. Können Sie sicherstellen, dass mit der `noexcept` Bezeichner für die COM-Methoden. Es ist für Ausnahmen an einer beliebigen Stelle in der Aufruf der Methode ausgelöst werden, solange Sie behandelt werden, bevor die Methode beendet wird. Wenn Sie verwenden `noexcept`, aber Sie können dann eine Ausnahme die Methode als Escapezeichen für, dann ist die Anwendung zu beenden.

## <a name="add-helper-types-and-functions"></a>Hinzufügen von Hilfstypen und Funktionen

In diesem Schritt fügen wir, dass einige Hilfstypen und die Funktionen, die der Rest des Codes ist verwenden. Dies der Fall ist, bevor Sie `main`, fügen Sie die folgenden.

```cppwinrt
struct prop_variant : PROPVARIANT
{
    prop_variant() noexcept : PROPVARIANT{}
    {
    }

    ~prop_variant() noexcept
    {
        clear();
    }

    void clear() noexcept
    {
        WINRT_VERIFY_(S_OK, ::PropVariantClear(this));
    }
};

struct registry_traits
{
    using type = HKEY;

    static void close(type value) noexcept
    {
        WINRT_VERIFY_(ERROR_SUCCESS, ::RegCloseKey(value));
    }

    static constexpr type invalid() noexcept
    {
        return nullptr;
    }
};

using registry_key = winrt::handle_type<registry_traits>;

std::wstring get_module_path()
{
    std::wstring path(100, L'?');
    uint32_t path_size{};
    DWORD actual_size{};

    do
    {
        path_size = static_cast<uint32_t>(path.size());
        actual_size = ::GetModuleFileName(nullptr, path.data(), path_size);

        if (actual_size + 1 > path_size)
        {
            path.resize(path_size * 2, L'?');
        }
    } while (actual_size + 1 > path_size);

    path.resize(actual_size);
    return path;
}

std::wstring get_shortcut_path()
{
    std::wstring format{ LR"(%ProgramData%\Microsoft\Windows\Start Menu\Programs\)" };
    format += (this_app_name + L".lnk");

    auto required{ ::ExpandEnvironmentStrings(format.c_str(), nullptr, 0) };
    std::wstring path(required - 1, L'?');
    ::ExpandEnvironmentStrings(format.c_str(), path.data(), required);
    return path;
}
```

## <a name="implement-the-remaining-functions-and-the-wmain-entry-point-function"></a>Implementieren Sie die restlichen Funktionen und die Wmain EntryPoint-Funktion

Die Projektvorlage generiert eine `main` Funktion für Sie. Löschen, die `main` funktionieren, und fügen Sie stattdessen diesen Code Eintrag, der Code zum Registrieren Ihrer Co-Klasse enthält, und klicken Sie dann auf ein Popup kann der Rückruf Ihrer Anwendungs bereitzustellen.

```cppwinrt
void register_callback()
{
    DWORD registration{};

    winrt::check_hresult(::CoRegisterClassObject(
        callback_guid,
        make<callback_factory>().get(),
        CLSCTX_LOCAL_SERVER,
        REGCLS_SINGLEUSE,
        &registration));
}

void create_shortcut()
{
    auto link{ winrt::create_instance<IShellLink>(CLSID_ShellLink) };
    std::wstring module_path{ get_module_path() };
    winrt::check_hresult(link->SetPath(module_path.c_str()));

    auto store = link.as<IPropertyStore>();
    prop_variant value;
    winrt::check_hresult(::InitPropVariantFromString(this_app_name.c_str(), &value));
    winrt::check_hresult(store->SetValue(PKEY_AppUserModel_ID, value));
    value.clear();
    winrt::check_hresult(::InitPropVariantFromCLSID(callback_guid, &value));
    winrt::check_hresult(store->SetValue(PKEY_AppUserModel_ToastActivatorCLSID, value));

    auto file{ store.as<IPersistFile>() };
    std::wstring shortcut_path{ get_shortcut_path() };
    winrt::check_hresult(file->Save(shortcut_path.c_str(), TRUE));

    std::wcout << L"In " << shortcut_path << L", created a shortcut to " << module_path << std::endl;
}

void update_registry()
{
    std::wstring key_path{ LR"(SOFTWARE\Classes\CLSID\{????????-????-????-????-????????????})" };
    ::StringFromGUID2(callback_guid, key_path.data() + 23, 39);
    key_path += LR"(\LocalServer32)";
    registry_key key;

    winrt::check_win32(::RegCreateKeyEx(
        HKEY_CURRENT_USER,
        key_path.c_str(),
        0,
        nullptr,
        0,
        KEY_WRITE,
        nullptr,
        key.put(),
        nullptr));
    ::RegDeleteValue(key.get(), nullptr);

    std::wstring path{ get_module_path() };

    winrt::check_win32(::RegSetValueEx(
        key.get(),
        nullptr,
        0,
        REG_SZ,
        reinterpret_cast<BYTE const*>(path.c_str()),
        static_cast<uint32_t>((path.size() + 1) * sizeof(wchar_t))));

    std::wcout << L"In " << key_path << L", registered local server at " << path << std::endl;
}

void create_toast()
{
    XmlDocument xml;

    std::wstring toastPayload
    {
        LR"(
<toast>
  <visual>
    <binding template='ToastGeneric'>
      <text>)"
    };
    toastPayload += this_app_name;
    toastPayload += LR"(
      </text>
    </binding>
  </visual>
  <actions>
    <action content='Call back )";
    toastPayload += this_app_name;
    toastPayload += LR"(
' arguments='the_args' activationKind='Foreground' />
  </actions>
</toast>)";
    xml.LoadXml(toastPayload);

    ToastNotification toast{ xml };
    ToastNotifier notifier{ ToastNotificationManager::CreateToastNotifier(this_app_name) };
    notifier.Show(toast);
}

void LaunchedNormally(HANDLE, INPUT_RECORD &, DWORD &);
void LaunchedFromNotification(HANDLE, INPUT_RECORD &, DWORD &);

int wmain(int argc, wchar_t * argv[], wchar_t * /* envp */[])
{
    winrt::init_apartment();

    register_callback();

    HANDLE consoleHandle{ ::GetStdHandle(STD_INPUT_HANDLE) };
    INPUT_RECORD buffer{};
    DWORD events{};
    ::FlushConsoleInputBuffer(consoleHandle);

    if (argc == 1)
    {
        LaunchedNormally(consoleHandle, buffer, events);
    }
    else if (argc == 2 && wcscmp(argv[1], L"-Embedding") == 0)
    {
        LaunchedFromNotification(consoleHandle, buffer, events);
    }
}

void LaunchedNormally(HANDLE consoleHandle, INPUT_RECORD & buffer, DWORD & events)
{
    try
    {
        bool runningAsAdmin{ ::IsUserAnAdmin() == TRUE };
        std::wcout << this_app_name << L" is running" << (runningAsAdmin ? L" (Administrator)." : L".") << std::endl;

        if (runningAsAdmin)
        {
            create_shortcut();
            update_registry();
        }

        std::wcout << std::endl << L"Press 'T' to display a toast notification (press any other key to exit)." << std::endl;

        ::ReadConsoleInput(consoleHandle, &buffer, 1, &events);
        if (towupper(buffer.Event.KeyEvent.uChar.UnicodeChar) == L'T')
        {
            create_toast();
        }
    }
    catch (winrt::hresult_error const& e)
    {
        std::wcout << L"Error: " << e.message().c_str() << L" (" << std::hex << std::showbase << std::setw(8) << static_cast<uint32_t>(e.code()) << L")" << std::endl;
    }
}

void LaunchedFromNotification(HANDLE consoleHandle, INPUT_RECORD & buffer, DWORD & events)
{
    ::Sleep(50); // Give the callback chance to display its message.
    std::wcout << std::endl << L"Press any key to exit." << std::endl;
    ::ReadConsoleInput(consoleHandle, &buffer, 1, &events);
}
```

## <a name="how-to-test-the-example-application"></a>So testen Sie die Beispiel-Anwendung

Erstellen Sie die Anwendung, und klicken Sie dann als Administrator, um die Registrierung und andere Setup Ausführung von Code dazu führen, dass mindestens einmal ausgeführt. Ob Sie es als Administrator ausführen, und drücken Sie dann ' t "auf einem Popup angezeigt werden. Sie können dann die Schaltfläche **Rückruf ToastAndCallback** entweder direkt aus der Popupbenachrichtigung Knacken nach oben oder über das Info-Center und Ihre Anwendung gestartet, instanziiert Co-Klasse und die **INotificationActivationCallback :: Aktivieren von** Methode ausgeführt.

## <a name="in-process-com-server"></a>In-Process-COM-server

Die *ToastAndCallback* Beispiel-app über Funktionen als COM-Server lokal (oder Out-of-Process). Dies ist der Windows-Registrierung [LocalServer32](/windows/desktop/com/localserver32) -Schlüssel angegeben, dass Sie verwenden, um die CLSID des der Co-Klasse zu registrieren. Ein lokaler com-Server hostet die coclass(es) innerhalb einer ausführbaren Binärdatei (ein `.exe`).

Sie können auch (und wohl eher) die Möglichkeit, Ihre coclass(es) innerhalb einer DLL-Bibliothek hosten (eine `.dll`). Ein COM-Server in Form von eine DLL-Datei wird als in-Process-com-Server bezeichnet, und es wird angegeben, indem CLSIDs mithilfe des Windows-Registrierung [InprocServer32](/windows/desktop/com/inprocserver32) Schlüssels registriert wurden.

### <a name="create-a-dynamic-link-library-dll-project"></a>Erstellen eines Projekts dll-Bibliothek (DLL)

Erstellen Sie einen in-Process-COM-Server durch Erstellen eines neuen Projekts in Microsoft Visual Studio können Sie damit beginnen. Erstellen Sie ein **Visual C++** > **Windows-Desktop** > **Dll-Bibliothek (DLL)** -Projekt.

Hinzufügen von C++ / WinRT-Unterstützung in das neue Projekt, folgen Sie der Anleitung im [Ändern Sie ein Projekt der Windows-Desktop-Anwendung zum Hinzufügen von C++ / WinRT-Unterstützung](/windows/uwp/cpp-and-winrt-apis/get-started#modify-a-windows-desktop-application-project-to-add-cwinrt-support).

### <a name="implement-the-coclass-class-factory-and-in-proc-server-exports"></a>Implementieren Sie die Co-Klasse, die Klassenfactory und die Exporte für in-Process-server

Öffnen `dllmain.cpp`, und fügen Sie im Codebeispiel unten hinzu.

Wenn Sie bereits über eine DLL-Datei verfügen, die implementiert C++ / WinRT-Windows-Runtime-Klassen, und klicken Sie dann Sie bereits die unten angezeigte **DllCanUnloadNow** -Funktion müssen. Wenn Sie diese DLL Co-Klassen hinzufügen möchten, können Sie die Funktion **DllGetClassObject** hinzufügen.

Wenn keine vorhandenen [C++ für Windows-Runtime-Bibliothek (WRL)](/cpp/windows/windows-runtime-cpp-template-library-wrl) -Code, der mit kompatibel bleiben soll haben, dann können Sie die WRL-Teile der gezeigte Code entfernen.

```cppwinrt
// dllmain.cpp

struct MyCoclass : winrt::implements<MyCoclass, IPersist>
{
    HRESULT STDMETHODCALLTYPE GetClassID(CLSID* id) noexcept override
    {
        *id = IID_IPersist; // Doesn't matter what we return, for this example.
        return S_OK;
    }
};

struct __declspec(uuid("85d6672d-0606-4389-a50a-356ce7bded09"))
    MyCoclassFactory : winrt::implements<MyCoclassFactory, IClassFactory>
{
    HRESULT STDMETHODCALLTYPE CreateInstance(IUnknown *pUnkOuter, REFIID riid, void **ppvObject) noexcept override
    {
        try
        {
            *ppvObject = winrt::make<MyCoclass>().get();
            return S_OK;
        }
        catch (...)
        {
            return winrt::to_hresult();
        }
    }

    HRESULT STDMETHODCALLTYPE LockServer(BOOL fLock) noexcept override
    {
        // ...
        return S_OK;
    }

    // ...
};

HRESULT __stdcall DllCanUnloadNow()
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

HRESULT __stdcall DllGetClassObject(GUID const& clsid, GUID const& iid, void** result)
{
    try
    {
        *result = nullptr;

        if (clsid == __uuidof(MyCoclassFactory))
        {
            return winrt::make<MyCoclassFactory>()->QueryInterface(iid, result);
        }

#ifdef _WRL_MODULE_H_
        return ::Microsoft::WRL::Module<::Microsoft::WRL::InProc>::GetModule().GetClassObject(clsid, iid, result);
#else
        return winrt::hresult_class_not_available().to_abi();
#endif
    }
    catch (...)
    {
        return winrt::to_hresult();
    }
}
```

### <a name="support-for-weak-references"></a>Unterstützung für schwache Referenzen

Weitere Informationen finden Sie [schwache Referenzen in C++ / WinRT](weak-references.md#weak-references-in-cwinrt).

C++ / WinRT (insbesondere die [**WinRT:: Implements**](/uwp/cpp-ref-for-winrt/implements) Basisstruktur-Template) implementiert [**IWeakReferenceSource**](/windows/desktop/api/weakreference/nn-weakreference-iweakreferencesource) für Sie, wenn Ihr Typ implementiert [**IInspectable**](/windows/desktop/api/inspectable/nn-inspectable-iinspectable) (oder jede Schnittstelle, die von **IInspectable**abgeleitet ist).

Dies liegt daran **IWeakReferenceSource** und [**IWeakReference**](/windows/desktop/api/weakreference/nn-weakreference-iweakreference) für Windows-Runtime-Typen vorgesehen sind. Daher können Sie aktivieren Unterstützung von schwachen Referenzen für die Co-Klasse durch einfaches Hinzufügen **Winrt::Windows::Foundation::IInspectable** (oder eine Schnittstelle, die von **IInspectable**abgeleitet ist) zu Ihrer Implementierung.

```cppwinrt
struct MyCoclass : winrt::implements<MyCoclass, IMyComInterface, winrt::Windows::Foundation::IInspectable>
{
    //  ...
};
```

## <a name="important-apis"></a>Wichtige APIs
* [IInspectable-Schnittstelle](/windows/desktop/api/inspectable/nn-inspectable-iinspectable)
* [IUnknown Schnittstelle](https://msdn.microsoft.com/library/windows/desktop/ms680509)
* [winrt::implements Strukturvorlage](/uwp/cpp-ref-for-winrt/implements)

## <a name="related-topics"></a>Verwandte Themen
* [Erstellen von APIs mit C++/WinRT](/windows/uwp/cpp-and-winrt-apis/author-apis)
* [Verwenden von COM-Komponenten mit C++ / WinRT](consume-com.md)
* [Senden einer lokalen Popupbenachrichtigung](/windows/uwp/design/shell/tiles-and-notifications/send-local-toast)
