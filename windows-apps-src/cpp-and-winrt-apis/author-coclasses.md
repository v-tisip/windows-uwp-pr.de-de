---
author: stevewhims
description: C++ / WinRT hilft Ihnen beim Erstellen von klassischer COM-Komponenten, genauso, wie Sie Windows-Runtime-Klassen man erleichtert.
title: Erstellen von COM-Komponenten mit C++ / WinRT
ms.author: stwhi
ms.date: 09/06/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Standard, c++, Cpp, Winrt, Projektion, "author" COM, Komponente
ms.localizationpriority: medium
ms.openlocfilehash: 428e1e963c89b7f9061d6b579b3bd5368a3a0ad1
ms.sourcegitcommit: 00d27738325d6db5b5e481911ae7fac0711b05eb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/07/2018
ms.locfileid: "3659039"
---
# <a name="author-com-components-with-cwinrtwindowsuwpcpp-and-winrt-apisintro-to-using-cpp-with-winrt"></a><span data-ttu-id="5bcc0-104">Erstellen von COM-Komponenten mit [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)</span><span class="sxs-lookup"><span data-stu-id="5bcc0-104">Author COM components with [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)</span></span>

<span data-ttu-id="5bcc0-105">C++ / WinRT können Sie klassische Component Object Model (COM)-Komponenten (oder Co-Klassen) erstellen, genau wie Sie Windows-Runtime-Klassen man erleichtert.</span><span class="sxs-lookup"><span data-stu-id="5bcc0-105">C++/WinRT can help you to author classic Component Object Model (COM) components (or coclasses), just as it helps you to author Windows Runtime classes.</span></span> <span data-ttu-id="5bcc0-106">Hier ist eine sehr einfache Abbildung, die Sie testen können, wenn Sie ihn in Einfügen der `main.cpp` eines neuen **Windows Console Application (C++ / WinRT)** Projekt.</span><span class="sxs-lookup"><span data-stu-id="5bcc0-106">Here's a very simple illustration, which you can test out if you paste it into the `main.cpp` of a new **Windows Console Application (C++/WinRT)** project.</span></span>

```cppwinrt
// main.cpp : Defines the entry point for the console application.
//

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

## <a name="a-more-realistic-and-interesting-example"></a><span data-ttu-id="5bcc0-107">Ein Beispiel mehr realistisch und interessante</span><span class="sxs-lookup"><span data-stu-id="5bcc0-107">A more realistic and interesting example</span></span>

<span data-ttu-id="5bcc0-108">Im verbleibenden Teil dieses Thema führt Sie über eine minimale Konsole Anwendungsprojekt erstellen, C++ verwendet / WinRT, um eine grundlegende Co-Klasse und der Klassenname-Factory implementieren.</span><span class="sxs-lookup"><span data-stu-id="5bcc0-108">The remainder of this topic walks through creating a minimal console application project that uses C++/WinRT to implement a basic coclass and class factory.</span></span> <span data-ttu-id="5bcc0-109">Die Anwendung Beispiel zeigt, wie Sie eine Popupbenachrichtigung mit einer Schaltfläche Rückruf darauf zu übermitteln, und die Co-Klasse (die die **INotificationActivationCallback** COM-Schnittstelle implementiert) ermöglicht die Anwendung gestartet und aufgerufen werden zurück, wenn der Benutzer die Schaltfläche im Popup klickt.</span><span class="sxs-lookup"><span data-stu-id="5bcc0-109">The example application shows how to deliver a toast notification with a callback button on it, and the coclass (which implements the **INotificationActivationCallback** COM interface) allows the application to be launched and called back when the user clicks that button on the toast.</span></span>

<span data-ttu-id="5bcc0-110">Weitere Hintergrundinformationen zu Popup Benachrichtigungsbereich Feature finden Sie unter [einer lokalen Popupbenachrichtigung senden](/windows/uwp/design/shell/tiles-and-notifications/send-local-toast).</span><span class="sxs-lookup"><span data-stu-id="5bcc0-110">More background about the toast notification feature area can be found at [Send a local toast notification](/windows/uwp/design/shell/tiles-and-notifications/send-local-toast).</span></span> <span data-ttu-id="5bcc0-111">Keine Codebeispiele in diesem Abschnitt der Dokumentation verwenden C++ / WinRT, aber es wird empfohlen, dass Sie den Code in diesem Thema aufgeführten bevorzugen.</span><span class="sxs-lookup"><span data-stu-id="5bcc0-111">None of the code examples in that section of the documentation use C++/WinRT, though, so we recommend that you prefer the code shown in this topic.</span></span>

## <a name="create-a-windows-console-application-project-toastandcallback"></a><span data-ttu-id="5bcc0-112">Erstellen eines Projekts Windows Console Application (ToastAndCallback)</span><span class="sxs-lookup"><span data-stu-id="5bcc0-112">Create a Windows Console Application project (ToastAndCallback)</span></span>

<span data-ttu-id="5bcc0-113">Erstellen Sie zunächst ein neues Projekt in Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5bcc0-113">Begin by creating a new project in Microsoft Visual Studio.</span></span> <span data-ttu-id="5bcc0-114">Erstellen Sie ein **Visual C++** > **Windows-Desktop** > **Windows Console Application (C++ / WinRT)** Projekt und nennen Sie es *ToastAndCallback*.</span><span class="sxs-lookup"><span data-stu-id="5bcc0-114">Create a **Visual C++** > **Windows Desktop** > **Windows Console Application (C++/WinRT)** project, and name it *ToastAndCallback*.</span></span>

<span data-ttu-id="5bcc0-115">Öffnen `main.cpp`, und entfernen Sie die Verwendung von-Direktiven, die die Projektvorlage generiert.</span><span class="sxs-lookup"><span data-stu-id="5bcc0-115">Open `main.cpp`, and remove the using-directives that the project template generates.</span></span> <span data-ttu-id="5bcc0-116">Fügen Sie den folgenden Code (wodurch uns sind die Bibliotheken, Header und Typnamen portiert, die wir benötigen), in ihren Platz.</span><span class="sxs-lookup"><span data-stu-id="5bcc0-116">In their place, paste the following code (which gives us the libs, headers, and type names that we need).</span></span>

```cppwinrt
#pragma comment(lib, "onecore")
#pragma comment(lib, "propsys")
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

## <a name="implement-the-coclass-and-class-factory"></a><span data-ttu-id="5bcc0-117">Implementieren Sie die Factory CO- und -Klasse</span><span class="sxs-lookup"><span data-stu-id="5bcc0-117">Implement the coclass and class factory</span></span>

<span data-ttu-id="5bcc0-118">In C++ / WinRT implementieren Sie Co-Klassen und Klassenfactorys, indem ableiten direkt von der [**WinRT:: Implements**](/uwp/cpp-ref-for-winrt/implements) Basisstruktur.</span><span class="sxs-lookup"><span data-stu-id="5bcc0-118">In C++/WinRT, you implement coclasses, and class factories, by deriving directly from the [**winrt::implements**](/uwp/cpp-ref-for-winrt/implements) base struct.</span></span> <span data-ttu-id="5bcc0-119">Unmittelbar nach der drei using--Direktiven oben gezeigten (und vor `main`), fügen Sie diesen Code, um die Popup-COM-Aktivator-Komponente zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="5bcc0-119">Immediately after the three using-directives shown above (and before `main`), paste this code to implement your toast activator COM component.</span></span>

```cppwinrt
static constexpr GUID callback_guid // BAF2FA85-E121-4CC9-A942-CE335B6F917F
{
    0xBAF2FA85, 0xE121, 0x4CC9, {0xA9, 0x42, 0xCE, 0x33, 0x5B, 0x6F, 0x91, 0x7F}
};

std::wstring const this_app_name{ L"ToastAndCallback" };

struct callback : winrt::implements<callback, INotificationActivationCallback>
{
    HRESULT __stdcall Activate(
        [[maybe_unused]] LPCWSTR app,
        [[maybe_unused]] LPCWSTR args,
        [[maybe_unused]] NOTIFICATION_USER_INPUT_DATA const* data,
        [[maybe_unused]] ULONG count) noexcept final
    {
        std::wcout << this_app_name << L" has been called back from a notification." << std::endl;
        std::wcout << L"Value of the 'app' parameter is '" << app << L"'." << std::endl;
        std::wcout << L"Value of the 'args' parameter is '" << args << L"'." << std::endl;
        return S_OK;
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

<span data-ttu-id="5bcc0-120">Die Implementierung der oben genannten Co-folgt das gleiche Muster, die im Code gezeigt wird [Erstellen von APIs mit C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/author-apis#if-youre-not-authoring-a-runtime-class).</span><span class="sxs-lookup"><span data-stu-id="5bcc0-120">The implementation of the coclass above follows the same pattern that's demonstrated in [Author APIs with C++/WinRT](/windows/uwp/cpp-and-winrt-apis/author-apis#if-youre-not-authoring-a-runtime-class).</span></span> <span data-ttu-id="5bcc0-121">Beachten Sie, dass Sie dieses Verfahren nicht nur für Windows-Runtime-Schnittstellen (jede Schnittstelle, die letztendlich von [**IInspectable**](https://msdn.microsoft.com/library/br205821)abgeleitet ist), sondern auch zum Implementieren von COM-Schnittstellen (jede Schnittstelle, die letztendlich von [**IUnknown**](https://msdn.microsoft.com/library/windows/desktop/ms680509)abgeleitet) verwenden können.</span><span class="sxs-lookup"><span data-stu-id="5bcc0-121">Notice that you can use this technique not only for Windows Runtime interfaces (any interface that ultimately derives from [**IInspectable**](https://msdn.microsoft.com/library/br205821)), but also to implement COM interfaces (any interface that ultimately derives from [**IUnknown**](https://msdn.microsoft.com/library/windows/desktop/ms680509)).</span></span>

<span data-ttu-id="5bcc0-122">In der Co-Klasse in der obige Code implementieren wir die **INotificationActivationCallback::Activate** Methode, die die Funktion, die aufgerufen wird, wenn der Benutzer die Schaltfläche Rückruf auf eine Popupbenachrichtigung klickt.</span><span class="sxs-lookup"><span data-stu-id="5bcc0-122">In the coclass in the code above, we implement the **INotificationActivationCallback::Activate** method, which is the function that's called when the user clicks the callback button on a toast notification.</span></span> <span data-ttu-id="5bcc0-123">Aber bevor diese Funktion aufgerufen werden kann, eine Instanz der Co-erstellt werden muss, und dies ist der Auftrag der **IClassFactory:: CreateInstance** -Funktion.</span><span class="sxs-lookup"><span data-stu-id="5bcc0-123">But before that function can be called, an instance of the coclass needs to be created, and that's the job of the **IClassFactory::CreateInstance** function.</span></span>

<span data-ttu-id="5bcc0-124">Die Co-Klasse, die wir gerade implementiert wird als den *COM-Aktivator* für Benachrichtigungen bezeichnet, und es verfügt über seine Klassen-Id (CLSID) in Form von der `callback_guid` Bezeichner (des Typs **GUID**), die oben angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5bcc0-124">The coclass that we just implemented is known as the *COM activator* for notifications, and it has its class id (CLSID) in the form of the `callback_guid` identifier (of type **GUID**) that you see above.</span></span> <span data-ttu-id="5bcc0-125">Wir werden diesen Bezeichner später in Form von eine Verknüpfung im Startmenü und eine Windows-Registrierungseintrag verwenden.</span><span class="sxs-lookup"><span data-stu-id="5bcc0-125">We'll be using that identifier later, in the form of a Start menu shortcut and a Windows Registry entry.</span></span> <span data-ttu-id="5bcc0-126">Den COM-Aktivator CLSID und den Pfad zu den entsprechenden COM-Server (das den Pfad zu der ausführbaren Datei, die wir hier erstellen) ist der Mechanismus, mit der eine Popupbenachrichtigung weiß, welche Klasse erstellt eine Instanz der bei die Rückruf Schaltfläche geklickt wird (an, ob die Benachrichtigung wird im Info-Center oder nicht geklickt).</span><span class="sxs-lookup"><span data-stu-id="5bcc0-126">The COM activator CLSID, and the path to its associated COM server (which is the path to the executable that we're building here) is the mechanism by which a toast notification knows what class to create an instance of when its callback button is clicked (whether the notification is clicked in Action Center or not).</span></span>

## <a name="best-practices-for-implementing-com-methods"></a><span data-ttu-id="5bcc0-127">Bewährte Methoden für die Implementierung von COM-Methoden</span><span class="sxs-lookup"><span data-stu-id="5bcc0-127">Best practices for implementing COM methods</span></span>

<span data-ttu-id="5bcc0-128">Techniken für die Fehlerbehandlung und für das Ressourcenmanagement können Hand in Hand wechseln.</span><span class="sxs-lookup"><span data-stu-id="5bcc0-128">Techniques for error handling and for resource management can go hand-in-hand.</span></span> <span data-ttu-id="5bcc0-129">Es ist mehr praktische Art und Weise Ausnahmen als Fehlercodes verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="5bcc0-129">It's more convenient and practical to use exceptions than error codes.</span></span> <span data-ttu-id="5bcc0-130">Und wenn Sie den Kauf Ressource einsetzen Initialisierung (RAII) Ausdrucksweise lautet, dann können Sie vermeiden: explizit Suchen nach Fehlercodes; und dann durch die explizite Freigabe von Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="5bcc0-130">And if you employ the Resource acquisition is initialization (RAII) idiom, then you can avoid: explicitly checking for error codes; and then explicitly releasing resources.</span></span> <span data-ttu-id="5bcc0-131">Auf diese Weise werden Ihr Codes mehr als notwendig entwickelt und gibt Fehler ausreichend Orten ausblenden.</span><span class="sxs-lookup"><span data-stu-id="5bcc0-131">Doing so makes your code more convoluted than necessary, and it gives bugs plenty of places to hide.</span></span> <span data-ttu-id="5bcc0-132">Stattdessen verwenden Sie RAII und Abfangen von Ausnahmen.</span><span class="sxs-lookup"><span data-stu-id="5bcc0-132">Instead, use RAII and catch exceptions.</span></span> <span data-ttu-id="5bcc0-133">Auf diese Weise können die Ressource Zuweisungen sind ausnahmesicheren, und Ihr Code ist einfach.</span><span class="sxs-lookup"><span data-stu-id="5bcc0-133">That way, your resource allocations are exception-safe, and your code is simple.</span></span>

<span data-ttu-id="5bcc0-134">Allerdings ermöglicht Ihnen Ausnahmen Ihrer COM-Methode Implementierungen als Escapezeichen für darf nicht an.</span><span class="sxs-lookup"><span data-stu-id="5bcc0-134">However, you mustn't allow exceptions to escape your COM method implementations.</span></span> <span data-ttu-id="5bcc0-135">Können Sie sicherstellen, dass mithilfe der `noexcept` Spezifizierer auf Ihre COM-Methoden.</span><span class="sxs-lookup"><span data-stu-id="5bcc0-135">You can ensure that by using the `noexcept` specifier on your COM methods.</span></span> <span data-ttu-id="5bcc0-136">Es ist in Ordnung für Ausnahmen an einer beliebigen Stelle in der Aufruf der Methode ausgelöst werden, solange Sie behandelt werden, bevor die Methode beendet wird.</span><span class="sxs-lookup"><span data-stu-id="5bcc0-136">It's ok for exceptions to be thrown anywhere in the call graph of your method, as long as you handle them before your method exits.</span></span>

## <a name="add-helper-types-and-functions"></a><span data-ttu-id="5bcc0-137">Hinzufügen von Hilfstypen und Funktionen</span><span class="sxs-lookup"><span data-stu-id="5bcc0-137">Add helper types and functions</span></span>

<span data-ttu-id="5bcc0-138">In diesem Schritt fügen wir, dass einige Hilfstypen und Funktionen, die der Rest des Codes vornimmt verwenden.</span><span class="sxs-lookup"><span data-stu-id="5bcc0-138">In this step, we'll add some helper types and functions that the rest of the code makes use of.</span></span> <span data-ttu-id="5bcc0-139">Dies der Fall ist, bevor Sie `main`, fügen Sie die folgenden.</span><span class="sxs-lookup"><span data-stu-id="5bcc0-139">So, before `main`, add the following.</span></span>

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

## <a name="implement-the-remaining-functions-and-the-wmain-entry-point-function"></a><span data-ttu-id="5bcc0-140">Implementieren Sie die restlichen Funktionen und die Wmain EntryPoint-Funktion</span><span class="sxs-lookup"><span data-stu-id="5bcc0-140">Implement the remaining functions, and the wmain entry point function</span></span>

<span data-ttu-id="5bcc0-141">Die Projektvorlage generiert eine `main` Funktion für Sie.</span><span class="sxs-lookup"><span data-stu-id="5bcc0-141">The project template generates a `main` function for you.</span></span> <span data-ttu-id="5bcc0-142">Löschen, die `main` funktionieren und an dessen Stelle fügen Sie diesen Code Eintrag, einschließlich Code zum Registrieren Ihrer Co-Klasse, und klicken Sie dann auf ein Popup kann der Rückruf Ihrer Anwendungs bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="5bcc0-142">Delete that `main` function, and in its place paste this code listing, which includes code to register your coclass, and then to deliver a toast capable of calling back your application.</span></span>

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

## <a name="how-to-test-the-example-application"></a><span data-ttu-id="5bcc0-143">Wie Sie die Beispiel-Anwendung zu testen</span><span class="sxs-lookup"><span data-stu-id="5bcc0-143">How to test the example application</span></span>

<span data-ttu-id="5bcc0-144">Erstellen Sie die Anwendung, und klicken Sie dann als Administrator die Registrierung und andere Setup auszuführenden Code dazu führen, dass mindestens einmal ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="5bcc0-144">Build the application, and then run it at least once as Administrator to cause the registration, and other setup, code to run.</span></span> <span data-ttu-id="5bcc0-145">Ob Sie es als Administrator ausführen, und drücken Sie dann ' t "verursachen ein Popup angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="5bcc0-145">Whether or not you're running it as Administrator, then press 'T' to cause a toast to be displayed.</span></span> <span data-ttu-id="5bcc0-146">Sie können dann die Schaltfläche **Rückruf ToastAndCallback** entweder direkt aus der Popupbenachrichtigung Knacken nach oben oder über das Info-Center und Ihre Anwendung gestartet, instanziiert Co-Klasse und die **INotificationActivationCallback :: Aktivieren von** Methode ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="5bcc0-146">You can then click the **Call back ToastAndCallback** button either directly from the toast notification that pops up, or from the Action Center, and your application will be launched, the coclass instantiated, and the **INotificationActivationCallback::Activate** method executed.</span></span>
