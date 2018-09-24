---
author: stevewhims
description: C++ / WinRT helfen Ihnen zum Erstellen von klassischer COM-Komponenten, wie Sie Windows-Runtime-Klassen man erleichtert.
title: Erstellen von COM-Komponenten mit C++ / WinRT
ms.author: stwhi
ms.date: 09/06/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Standard, c++, Cpp, Winrt, Projektion, "author", COM, Komponente
ms.localizationpriority: medium
ms.openlocfilehash: 729cfae39f302ae6b5bae275d9e28a39f3d9503b
ms.sourcegitcommit: 194ab5aa395226580753869c6b66fce88be83522
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2018
ms.locfileid: "4152093"
---
# <a name="author-com-components-with-cwinrtwindowsuwpcpp-and-winrt-apisintro-to-using-cpp-with-winrt"></a>Erstellen von COM-Komponenten mit [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)

C++ / WinRT können Sie zum Erstellen von klassischen Component Object Model (COM) Komponenten (oder Co-Klassen) genauso, wie Sie Windows-Runtime-Klassen man erleichtert. Hier ist eine sehr einfache Abbildung, die Sie testen können, wenn Sie ihn in Einfügen der `main.cpp` eines neuen **Windows Console Application (C++ / WinRT)** Projekt.

```cppwinrt
// main.cpp : Defines the entry point for the console application.
#include "pch.h"

using namespace winrt;

int main()
{
    init_apartment();

    struct MyCoclass : winrt::implements<MyCoclass, IPersist>
    {
        HRESULT STDMETHODCALLTYPE GetClassID(CLSID* id) noexcept override
        {
            *id = IID_IPersist; // Doesn't matter what we return, for this example.
            return S_OK;
        }
    };

    auto mycoclass_instance{ winrt::make<MyCoclass>() };
    CLSID id{};
    winrt::check_hresult(mycoclass_instance->GetClassID(&id));
}
```

Weitere Informationen finden Sie [nutzen COM-Komponenten mit C++ / WinRT](consume-com.md).

## <a name="a-more-realistic-and-interesting-example"></a>Ein Beispiel für mehr realistisch und interessante

Im verbleibenden Teil dieses Themas führt durch eine minimale Konsole Anwendungsprojekt erstellen, C++ verwendet / WinRT, um eine grundlegende Co-Klasse und die Klasse Factory implementieren. Die Anwendung Beispiel zeigt, wie Sie eine Popupbenachrichtigung mit einer Schaltfläche Rückruf darauf zu übermitteln, und die Co-Klasse (die die **INotificationActivationCallback** COM-Schnittstelle implementiert) kann die Anwendung gestartet und aufgerufen werden zurück, wenn der Benutzer auf diese Schaltfläche im Popup klickt.

Weitere Hintergrundinformationen zu den Popup-Benachrichtigung Featurebereich finden Sie unter [einer lokalen Popupbenachrichtigung senden](/windows/uwp/design/shell/tiles-and-notifications/send-local-toast). Keine Codebeispiele in diesem Abschnitt der Dokumentation verwenden C++ / WinRT, aber es wird empfohlen, dass Sie den Code in diesem Thema aufgeführten bevorzugen.

## <a name="create-a-windows-console-application-project-toastandcallback"></a>Erstellen eines Projekts Windows Console Application (ToastAndCallback)

Erstellen Sie zunächst ein neues Projekt in Microsoft Visual Studio. Erstellen Sie eine **Visual C++** > **Windows-Desktop** > **Windows Console Application (C++ / WinRT)** Projekt und nennen Sie es *ToastAndCallback*.

Öffnen `main.cpp`, und entfernen Sie die Verwendung-Direktiven, die die Projektvorlage generiert. Anstelle fügen Sie den folgenden Code (wodurch uns sind die Bibliotheken, Header und Typnamen portiert, die wir benötigen).

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

In C++ / WinRT können Sie Co-Klassen, und implementieren Klassenfactorys, durch eine Ableitung von der [**WinRT:: Implements**](/uwp/cpp-ref-for-winrt/implements) Basisstruktur. Unmittelbar nach der drei using--Direktiven oben gezeigten (und vor `main`), fügen Sie diesen Code, um Ihre Popupbenachrichtigung Benachrichtigung COM-Aktivator Komponente zu implementieren.

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

Die Implementierung der oben genannten Co-folgt das gleiche Muster, die im Code gezeigt wird ["author"-APIs mit C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/author-apis#if-youre-not-authoring-a-runtime-class). Beachten Sie, dass Sie dieses Verfahren nicht nur für Windows-Runtime-Schnittstellen (jede Schnittstelle, die letztendlich von [**IInspectable**](https://msdn.microsoft.com/library/br205821)abgeleitet ist), sondern auch zum Implementieren von COM-Schnittstellen (jede Schnittstelle, die letztendlich von [**IUnknown**](https://msdn.microsoft.com/library/windows/desktop/ms680509)abgeleitet) verwenden können.

In der Co-Klasse in der obige Code implementieren wir die **INotificationActivationCallback::Activate** Methode, die die Funktion, die aufgerufen wird, wenn der Benutzer die Callback-Schaltfläche auf eine Popupbenachrichtigung klickt. Aber bevor diese Funktion aufgerufen werden kann, muss eine Instanz der Co-erstellt werden, und der Auftrag der **IClassFactory:: CreateInstance** -Funktion.

Die Co-Klasse, die wir gerade implementiert ist als die *COM-Aktivator* für Benachrichtigungen bezeichnet und hat die Klassen-Id (CLSID) in Form von der `callback_guid` Bezeichner (des Typs **GUID**), die oben angezeigt. Wir werden diesen Bezeichner später in Form einer Verknüpfung im Startmenü und eine Windows-Registrierungseintrag verwenden. Die COM-Aktivator CLSID und den Pfad zu den entsprechenden COM-Server (die den Pfad der ausführbaren Datei, die wir hier erstellen) ist der Mechanismus, mit dem eine Popupbenachrichtigung weiß, welche Klasse erstellt eine Instanz der bei die Rückruf Schaltfläche geklickt wird (an, ob die Benachrichtigung wird im Info-Center oder nicht geklickt).

## <a name="best-practices-for-implementing-com-methods"></a>Bewährte Methoden für die Implementierung von COM-Methoden

Techniken für die Fehlerbehandlung und zur Verwaltung von Hand in Hand zu gelangen. Es ist praktisch und praktische Ausnahmen als Fehlercodes verwendet werden. Und wenn Sie die Ressource Erwerb ist Initialisierung (RAII) Ausdrucksweise einsetzen, dann können nicht explizit Suchen nach Fehlercodes und dann durch die explizite Freigabe von Ressourcen. Expliziten Kontrollen gestalten Sie Ihre mehr als notwendig unübersichtlich und gibt Fehler ausreichend Orten ausblenden. Verwenden Sie stattdessen RAII, und Ausnahmen auslösen/Catch. Auf diese Weise können die Ressource Zuweisungen sind ausnahmesicheren, und der Code ist einfach.

Allerdings ermöglicht Ihnen Ausnahmen die COM-Methode Implementierungen als Escapezeichen für darf nicht an. Können Sie sicherstellen, dass mithilfe der `noexcept` Spezifizierer auf Ihre COM-Methoden. Es ist in Ordnung für Ausnahmen an einer beliebigen Stelle in der Aufruf der Methode ausgelöst werden, solange Sie behandelt werden, bevor die Methode beendet wird. Wenn Sie verwenden `noexcept`, aber Sie können dann eine Ausnahme die Methode als Escapezeichen für, und dann Ihre Anwendung beendet.

## <a name="add-helper-types-and-functions"></a>Hinzufügen von Hilfstypen und Funktionen

In diesem Schritt fügen wir, dass einige Hilfstypen und Funktionen, die der Rest des Codes macht verwenden. Dies der Fall ist, bevor Sie `main`, fügen Sie Folgendes hinzu.

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

Die Projektvorlage generiert eine `main` Funktion für Sie. Löschen, die `main` funktionieren und an dessen Stelle fügen Sie diesen Code Eintrag, der Code zum Registrieren Ihrer Co-Klasse enthält, und klicken Sie dann auf ein Popup kann der Rückruf Ihrer Anwendung bereitzustellen.

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
    init_apartment();

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

## <a name="how-to-test-the-example-application"></a>Zum Testen der Beispiel-Anwendung

Erstellen Sie die Anwendung, und klicken Sie dann als Administrator die Registrierung und andere Setup Ausführung von Code bewirken, dass mindestens einmal ausgeführt. Ob Sie es als Administrator ausführen, und drücken Sie dann ' t "auf einem Popup angezeigt werden. Sie können dann die Schaltfläche **Rückruf ToastAndCallback** entweder direkt aus der Popupbenachrichtigung Knacken nach oben oder über das Info-Center und Ihre Anwendung gestartet, instanziiert Co-Klasse und die **INotificationActivationCallback :: Aktivieren Sie** Methode ausgeführt.

## <a name="important-apis"></a>Wichtige APIs
* [IInspectable-Schnittstelle](https://msdn.microsoft.com/library/br205821)
* [IUnknown Schnittstelle](https://msdn.microsoft.com/library/windows/desktop/ms680509)
* [winrt::implements Strukturvorlage](/uwp/cpp-ref-for-winrt/implements)

## <a name="related-topics"></a>Verwandte Themen
* [Erstellen von APIs mit C++/WinRT](/windows/uwp/cpp-and-winrt-apis/author-apis)
* [Verwenden von COM-Komponenten mit C++ / WinRT](consume-com.md)
* [Senden einer lokalen Popupbenachrichtigung](/windows/uwp/design/shell/tiles-and-notifications/send-local-toast)
