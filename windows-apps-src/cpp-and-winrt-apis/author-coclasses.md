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
ms.openlocfilehash: 227ffcd72150e37a513649e69bc7a6709581d65c
ms.sourcegitcommit: e4f3e1b2d08a02b9920e78e802234e5b674e7223
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/26/2018
ms.locfileid: "4205326"
---
# <a name="author-com-components-with-cwinrtwindowsuwpcpp-and-winrt-apisintro-to-using-cpp-with-winrt"></a><span data-ttu-id="bf558-104">Erstellen von COM-Komponenten mit [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)</span><span class="sxs-lookup"><span data-stu-id="bf558-104">Author COM components with [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)</span></span>

<span data-ttu-id="bf558-105">C++ / WinRT können Sie zum Erstellen von klassischen Component Object Model (COM) Komponenten (oder Co-Klassen) genauso, wie Sie Windows-Runtime-Klassen man erleichtert.</span><span class="sxs-lookup"><span data-stu-id="bf558-105">C++/WinRT can help you to author classic Component Object Model (COM) components (or coclasses), just as it helps you to author Windows Runtime classes.</span></span> <span data-ttu-id="bf558-106">Hier ist eine sehr einfache Abbildung, die Sie testen können, wenn Sie ihn in Einfügen der `main.cpp` eines neuen **Windows Console Application (C++ / WinRT)** Projekt.</span><span class="sxs-lookup"><span data-stu-id="bf558-106">Here's a very simple illustration, which you can test out if you paste it into the `main.cpp` of a new **Windows Console Application (C++/WinRT)** project.</span></span>

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

<span data-ttu-id="bf558-107">Weitere Informationen finden Sie [nutzen COM-Komponenten mit C++ / WinRT](consume-com.md).</span><span class="sxs-lookup"><span data-stu-id="bf558-107">Also see [Consume COM components with C++/WinRT](consume-com.md).</span></span>

## <a name="a-more-realistic-and-interesting-example"></a><span data-ttu-id="bf558-108">Ein Beispiel für mehr realistisch und interessante</span><span class="sxs-lookup"><span data-stu-id="bf558-108">A more realistic and interesting example</span></span>

<span data-ttu-id="bf558-109">Im verbleibenden Teil dieses Themas führt durch eine minimale Konsole Anwendungsprojekt erstellen, C++ verwendet / WinRT, um eine grundlegende Co-Klasse und die Klasse Factory implementieren.</span><span class="sxs-lookup"><span data-stu-id="bf558-109">The remainder of this topic walks through creating a minimal console application project that uses C++/WinRT to implement a basic coclass and class factory.</span></span> <span data-ttu-id="bf558-110">Die Anwendung Beispiel zeigt, wie Sie eine Popupbenachrichtigung mit einer Schaltfläche Rückruf darauf zu übermitteln, und die Co-Klasse (die die **INotificationActivationCallback** COM-Schnittstelle implementiert) kann die Anwendung gestartet und aufgerufen werden zurück, wenn der Benutzer auf diese Schaltfläche im Popup klickt.</span><span class="sxs-lookup"><span data-stu-id="bf558-110">The example application shows how to deliver a toast notification with a callback button on it, and the coclass (which implements the **INotificationActivationCallback** COM interface) allows the application to be launched and called back when the user clicks that button on the toast.</span></span>

<span data-ttu-id="bf558-111">Weitere Hintergrundinformationen zu den Popup-Benachrichtigung Featurebereich finden Sie unter [einer lokalen Popupbenachrichtigung senden](/windows/uwp/design/shell/tiles-and-notifications/send-local-toast).</span><span class="sxs-lookup"><span data-stu-id="bf558-111">More background about the toast notification feature area can be found at [Send a local toast notification](/windows/uwp/design/shell/tiles-and-notifications/send-local-toast).</span></span> <span data-ttu-id="bf558-112">Keine Codebeispiele in diesem Abschnitt der Dokumentation verwenden C++ / WinRT, aber es wird empfohlen, dass Sie den Code in diesem Thema aufgeführten bevorzugen.</span><span class="sxs-lookup"><span data-stu-id="bf558-112">None of the code examples in that section of the documentation use C++/WinRT, though, so we recommend that you prefer the code shown in this topic.</span></span>

## <a name="create-a-windows-console-application-project-toastandcallback"></a><span data-ttu-id="bf558-113">Erstellen eines Projekts Windows Console Application (ToastAndCallback)</span><span class="sxs-lookup"><span data-stu-id="bf558-113">Create a Windows Console Application project (ToastAndCallback)</span></span>

<span data-ttu-id="bf558-114">Erstellen Sie zunächst ein neues Projekt in Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bf558-114">Begin by creating a new project in Microsoft Visual Studio.</span></span> <span data-ttu-id="bf558-115">Erstellen Sie eine **Visual C++** > **Windows-Desktop** > **Windows Console Application (C++ / WinRT)** Projekt und nennen Sie es *ToastAndCallback*.</span><span class="sxs-lookup"><span data-stu-id="bf558-115">Create a **Visual C++** > **Windows Desktop** > **Windows Console Application (C++/WinRT)** project, and name it *ToastAndCallback*.</span></span>

<span data-ttu-id="bf558-116">Öffnen `main.cpp`, und entfernen Sie die Verwendung-Direktiven, die die Projektvorlage generiert.</span><span class="sxs-lookup"><span data-stu-id="bf558-116">Open `main.cpp`, and remove the using-directives that the project template generates.</span></span> <span data-ttu-id="bf558-117">Anstelle fügen Sie den folgenden Code (wodurch uns sind die Bibliotheken, Header und Typnamen portiert, die wir benötigen).</span><span class="sxs-lookup"><span data-stu-id="bf558-117">In their place, paste the following code (which gives us the libs, headers, and type names that we need).</span></span>

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

## <a name="implement-the-coclass-and-class-factory"></a><span data-ttu-id="bf558-118">Implementieren Sie die Factory CO- und -Klasse</span><span class="sxs-lookup"><span data-stu-id="bf558-118">Implement the coclass and class factory</span></span>

<span data-ttu-id="bf558-119">In C++ / WinRT können Sie Co-Klassen, und implementieren Klassenfactorys, durch eine Ableitung von der [**WinRT:: Implements**](/uwp/cpp-ref-for-winrt/implements) Basisstruktur.</span><span class="sxs-lookup"><span data-stu-id="bf558-119">In C++/WinRT, you implement coclasses, and class factories, by deriving from the [**winrt::implements**](/uwp/cpp-ref-for-winrt/implements) base struct.</span></span> <span data-ttu-id="bf558-120">Unmittelbar nach der drei using--Direktiven oben gezeigten (und vor `main`), fügen Sie diesen Code, um Ihre Popupbenachrichtigung Benachrichtigung COM-Aktivator Komponente zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="bf558-120">Immediately after the three using-directives shown above (and before `main`), paste this code to implement your toast notification COM activator component.</span></span>

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

<span data-ttu-id="bf558-121">Die Implementierung der oben genannten Co-folgt das gleiche Muster, die im Code gezeigt wird ["author"-APIs mit C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/author-apis#if-youre-not-authoring-a-runtime-class).</span><span class="sxs-lookup"><span data-stu-id="bf558-121">The implementation of the coclass above follows the same pattern that's demonstrated in [Author APIs with C++/WinRT](/windows/uwp/cpp-and-winrt-apis/author-apis#if-youre-not-authoring-a-runtime-class).</span></span> <span data-ttu-id="bf558-122">Beachten Sie, dass Sie dieses Verfahren nicht nur für Windows-Runtime-Schnittstellen (jede Schnittstelle, die letztendlich von [**IInspectable**](https://msdn.microsoft.com/library/br205821)abgeleitet ist), sondern auch zum Implementieren von COM-Schnittstellen (jede Schnittstelle, die letztendlich von [**IUnknown**](https://msdn.microsoft.com/library/windows/desktop/ms680509)abgeleitet) verwenden können.</span><span class="sxs-lookup"><span data-stu-id="bf558-122">Notice that you can use this technique not only for Windows Runtime interfaces (any interface that ultimately derives from [**IInspectable**](https://msdn.microsoft.com/library/br205821)), but also to implement COM interfaces (any interface that ultimately derives from [**IUnknown**](https://msdn.microsoft.com/library/windows/desktop/ms680509)).</span></span>

<span data-ttu-id="bf558-123">In der Co-Klasse in der obige Code implementieren wir die **INotificationActivationCallback::Activate** Methode, die die Funktion, die aufgerufen wird, wenn der Benutzer die Callback-Schaltfläche auf eine Popupbenachrichtigung klickt.</span><span class="sxs-lookup"><span data-stu-id="bf558-123">In the coclass in the code above, we implement the **INotificationActivationCallback::Activate** method, which is the function that's called when the user clicks the callback button on a toast notification.</span></span> <span data-ttu-id="bf558-124">Aber bevor diese Funktion aufgerufen werden kann, muss eine Instanz der Co-erstellt werden, und der Auftrag der **IClassFactory:: CreateInstance** -Funktion.</span><span class="sxs-lookup"><span data-stu-id="bf558-124">But before that function can be called, an instance of the coclass needs to be created, and that's the job of the **IClassFactory::CreateInstance** function.</span></span>

<span data-ttu-id="bf558-125">Die Co-Klasse, die wir gerade implementiert ist als die *COM-Aktivator* für Benachrichtigungen bezeichnet und hat die Klassen-Id (CLSID) in Form von der `callback_guid` Bezeichner (des Typs **GUID**), die oben angezeigt.</span><span class="sxs-lookup"><span data-stu-id="bf558-125">The coclass that we just implemented is known as the *COM activator* for notifications, and it has its class id (CLSID) in the form of the `callback_guid` identifier (of type **GUID**) that you see above.</span></span> <span data-ttu-id="bf558-126">Wir werden diesen Bezeichner später in Form einer Verknüpfung im Startmenü und eine Windows-Registrierungseintrag verwenden.</span><span class="sxs-lookup"><span data-stu-id="bf558-126">We'll be using that identifier later, in the form of a Start menu shortcut and a Windows Registry entry.</span></span> <span data-ttu-id="bf558-127">Die COM-Aktivator CLSID und den Pfad zu den entsprechenden COM-Server (die den Pfad der ausführbaren Datei, die wir hier erstellen) ist der Mechanismus, mit dem eine Popupbenachrichtigung weiß, welche Klasse erstellt eine Instanz der bei die Rückruf Schaltfläche geklickt wird (an, ob die Benachrichtigung wird im Info-Center oder nicht geklickt).</span><span class="sxs-lookup"><span data-stu-id="bf558-127">The COM activator CLSID, and the path to its associated COM server (which is the path to the executable that we're building here) is the mechanism by which a toast notification knows what class to create an instance of when its callback button is clicked (whether the notification is clicked in Action Center or not).</span></span>

## <a name="best-practices-for-implementing-com-methods"></a><span data-ttu-id="bf558-128">Bewährte Methoden für die Implementierung von COM-Methoden</span><span class="sxs-lookup"><span data-stu-id="bf558-128">Best practices for implementing COM methods</span></span>

<span data-ttu-id="bf558-129">Techniken für die Fehlerbehandlung und zur Verwaltung von Hand in Hand zu gelangen.</span><span class="sxs-lookup"><span data-stu-id="bf558-129">Techniques for error handling and for resource management can go hand-in-hand.</span></span> <span data-ttu-id="bf558-130">Es ist praktisch und praktische Ausnahmen als Fehlercodes verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="bf558-130">It's more convenient and practical to use exceptions than error codes.</span></span> <span data-ttu-id="bf558-131">Und wenn Sie die Ressource Erwerb ist Initialisierung (RAII) Ausdrucksweise einsetzen, dann können nicht explizit Suchen nach Fehlercodes und dann durch die explizite Freigabe von Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="bf558-131">And if you employ the resource-acquisition-is-initialization (RAII) idiom, then you can avoid explicitly checking for error codes and then explicitly releasing resources.</span></span> <span data-ttu-id="bf558-132">Expliziten Kontrollen gestalten Sie Ihre mehr als notwendig unübersichtlich und gibt Fehler ausreichend Orten ausblenden.</span><span class="sxs-lookup"><span data-stu-id="bf558-132">Such explicit checks make your code more convoluted than necessary, and it gives bugs plenty of places to hide.</span></span> <span data-ttu-id="bf558-133">Verwenden Sie stattdessen RAII, und Ausnahmen auslösen/Catch.</span><span class="sxs-lookup"><span data-stu-id="bf558-133">Instead, use RAII, and throw/catch exceptions.</span></span> <span data-ttu-id="bf558-134">Auf diese Weise können die Ressource Zuweisungen sind ausnahmesicheren, und der Code ist einfach.</span><span class="sxs-lookup"><span data-stu-id="bf558-134">That way, your resource allocations are exception-safe, and your code is simple.</span></span>

<span data-ttu-id="bf558-135">Allerdings ermöglicht Ihnen Ausnahmen die COM-Methode Implementierungen als Escapezeichen für darf nicht an.</span><span class="sxs-lookup"><span data-stu-id="bf558-135">However, you mustn't allow exceptions to escape your COM method implementations.</span></span> <span data-ttu-id="bf558-136">Können Sie sicherstellen, dass mithilfe der `noexcept` Spezifizierer auf Ihre COM-Methoden.</span><span class="sxs-lookup"><span data-stu-id="bf558-136">You can ensure that by using the `noexcept` specifier on your COM methods.</span></span> <span data-ttu-id="bf558-137">Es ist in Ordnung für Ausnahmen an einer beliebigen Stelle in der Aufruf der Methode ausgelöst werden, solange Sie behandelt werden, bevor die Methode beendet wird.</span><span class="sxs-lookup"><span data-stu-id="bf558-137">It's ok for exceptions to be thrown anywhere in the call graph of your method, as long as you handle them before your method exits.</span></span> <span data-ttu-id="bf558-138">Wenn Sie verwenden `noexcept`, aber Sie können dann eine Ausnahme die Methode als Escapezeichen für, und dann Ihre Anwendung beendet.</span><span class="sxs-lookup"><span data-stu-id="bf558-138">If you use `noexcept`, but you then allow an exception to escape your method, then your application will terminate.</span></span>

## <a name="add-helper-types-and-functions"></a><span data-ttu-id="bf558-139">Hinzufügen von Hilfstypen und Funktionen</span><span class="sxs-lookup"><span data-stu-id="bf558-139">Add helper types and functions</span></span>

<span data-ttu-id="bf558-140">In diesem Schritt fügen wir, dass einige Hilfstypen und Funktionen, die der Rest des Codes macht verwenden.</span><span class="sxs-lookup"><span data-stu-id="bf558-140">In this step, we'll add some helper types and functions that the rest of the code makes use of.</span></span> <span data-ttu-id="bf558-141">Dies der Fall ist, bevor Sie `main`, fügen Sie Folgendes hinzu.</span><span class="sxs-lookup"><span data-stu-id="bf558-141">So, before `main`, add the following.</span></span>

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

## <a name="implement-the-remaining-functions-and-the-wmain-entry-point-function"></a><span data-ttu-id="bf558-142">Implementieren Sie die restlichen Funktionen und die Wmain EntryPoint-Funktion</span><span class="sxs-lookup"><span data-stu-id="bf558-142">Implement the remaining functions, and the wmain entry point function</span></span>

<span data-ttu-id="bf558-143">Die Projektvorlage generiert eine `main` Funktion für Sie.</span><span class="sxs-lookup"><span data-stu-id="bf558-143">The project template generates a `main` function for you.</span></span> <span data-ttu-id="bf558-144">Löschen, die `main` funktionieren und an dessen Stelle fügen Sie diesen Code Eintrag, der Code zum Registrieren Ihrer Co-Klasse enthält, und klicken Sie dann auf ein Popup kann der Rückruf Ihrer Anwendung bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="bf558-144">Delete that `main` function, and in its place paste this code listing, which includes code to register your coclass, and then to deliver a toast capable of calling back your application.</span></span>

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

## <a name="how-to-test-the-example-application"></a><span data-ttu-id="bf558-145">Zum Testen der Beispiel-Anwendung</span><span class="sxs-lookup"><span data-stu-id="bf558-145">How to test the example application</span></span>

<span data-ttu-id="bf558-146">Erstellen Sie die Anwendung, und klicken Sie dann als Administrator die Registrierung und andere Setup Ausführung von Code bewirken, dass mindestens einmal ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="bf558-146">Build the application, and then run it at least once as Administrator to cause the registration, and other setup, code to run.</span></span> <span data-ttu-id="bf558-147">Ob Sie es als Administrator ausführen, und drücken Sie dann ' t "auf einem Popup angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="bf558-147">Whether or not you're running it as Administrator, then press 'T' to cause a toast to be displayed.</span></span> <span data-ttu-id="bf558-148">Sie können dann die Schaltfläche **Rückruf ToastAndCallback** entweder direkt aus der Popupbenachrichtigung Knacken nach oben oder über das Info-Center und Ihre Anwendung gestartet, instanziiert Co-Klasse und die **INotificationActivationCallback :: Aktivieren Sie** Methode ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="bf558-148">You can then click the **Call back ToastAndCallback** button either directly from the toast notification that pops up, or from the Action Center, and your application will be launched, the coclass instantiated, and the **INotificationActivationCallback::Activate** method executed.</span></span>

## <a name="in-process-com-server"></a><span data-ttu-id="bf558-149">In-Process-COM-server</span><span class="sxs-lookup"><span data-stu-id="bf558-149">In-process COM server</span></span>

<span data-ttu-id="bf558-150">Die *ToastAndCallback* Beispiel-app über Funktionen als COM-Server lokal (oder Out-of-Process).</span><span class="sxs-lookup"><span data-stu-id="bf558-150">The *ToastAndCallback* example app above functions as a local (or out-of-process) COM server.</span></span> <span data-ttu-id="bf558-151">Dies wird durch den [LocalServer32](/windows/desktop/com/localserver32) Windows-Schlüssel angezeigt, die Verwendung von zu registrieren.</span><span class="sxs-lookup"><span data-stu-id="bf558-151">This is indicated by the [LocalServer32](/windows/desktop/com/localserver32) Windows Registry key that you use to register it.</span></span> <span data-ttu-id="bf558-152">Ein lokaler com-Server hostet die coclass(es) innerhalb einer ausführbaren Binärdatei (ein `.exe`).</span><span class="sxs-lookup"><span data-stu-id="bf558-152">A local COM server hosts its coclass(es) inside an executable binary (an `.exe`).</span></span>

<span data-ttu-id="bf558-153">Sie können auch (und wohl eher), die Möglichkeit, Ihre coclass(es) innerhalb einer DLL-Bibliothek hosten (eine `.dll`).</span><span class="sxs-lookup"><span data-stu-id="bf558-153">Alternatively (and arguably more likely), you can choose to host your coclass(es) inside a dynamic-link library (a `.dll`).</span></span> <span data-ttu-id="bf558-154">Ein com-Server in Form einer DLL wird als in-Process-com-Server bezeichnet, und es wird angegeben, indem Sie mit der Taste [InprocServer32](/windows/desktop/com/inprocserver32) Windows-Registrierung registriert wurden.</span><span class="sxs-lookup"><span data-stu-id="bf558-154">A COM server in the form of a DLL is known as an in-process COM server, and it's indicated by being registered by using the [InprocServer32](/windows/desktop/com/inprocserver32) Windows Registry key.</span></span>

### <a name="create-a-dynamic-link-library-dll-project"></a><span data-ttu-id="bf558-155">Erstellen eines Projekts dll-Bibliothek (DLL)</span><span class="sxs-lookup"><span data-stu-id="bf558-155">Create a Dynamic-Link Library (DLL) project</span></span>

<span data-ttu-id="bf558-156">Die Aufgabe beim Erstellen eines in-Process-COM-Servers durch Erstellen eines neuen Projekts in Microsoft Visual Studio können Sie damit beginnen.</span><span class="sxs-lookup"><span data-stu-id="bf558-156">You can begin the task of creating an in-process COM server by creating a new project in Microsoft Visual Studio.</span></span> <span data-ttu-id="bf558-157">Erstellen Sie eine **Visual C++** > **Windows-Desktop** > **Dll-Bibliothek (DLL)** -Projekt.</span><span class="sxs-lookup"><span data-stu-id="bf558-157">Create a **Visual C++** > **Windows Desktop** > **Dynamic-Link Library (DLL)** project.</span></span>

### <a name="set-project-properties"></a><span data-ttu-id="bf558-158">Set-Projekteigenschaften</span><span class="sxs-lookup"><span data-stu-id="bf558-158">Set project properties</span></span>

<span data-ttu-id="bf558-159">Wechseln Sie zum Projekt-Eigenschaft, die **Allgemeine** \> **Windows SDK-Version**, und wählen Sie **Alle Konfigurationen** und **Alle Plattformen**.</span><span class="sxs-lookup"><span data-stu-id="bf558-159">Go to project property **General** \> **Windows SDK Version**, and select **All Configurations** and **All Platforms**.</span></span> <span data-ttu-id="bf558-160">Legen Sie die **Windows SDK-Version** *10.0.17134.0 (Windows 10, Version 1803)*, oder höher.</span><span class="sxs-lookup"><span data-stu-id="bf558-160">Set **Windows SDK Version** to *10.0.17134.0 (Windows 10, version 1803)*, or later.</span></span>

<span data-ttu-id="bf558-161">Hinzufügen von Visual Studio-Unterstützung für C++ / WinRT zu Ihrem Projekt bearbeiten Ihrer `.vcxproj` Datei, suchen Sie `<PropertyGroup Label="Globals">` aus, und legen Sie innerhalb dieser Eigenschaftengruppe die Eigenschaft `<CppWinRTEnabled>true</CppWinRTEnabled>`.</span><span class="sxs-lookup"><span data-stu-id="bf558-161">To add Visual Studio support for C++/WinRT to your project, edit your `.vcxproj` file, find `<PropertyGroup Label="Globals">` and, inside that property group, set the property `<CppWinRTEnabled>true</CppWinRTEnabled>`.</span></span>

<span data-ttu-id="bf558-162">Da C++ / WinRT Features aus dem C ++ 17-Standard verwendet, Projekteigenschaft **C/C++** > **Sprache** > **C++ Sprache Standard** in *ISO C ++ 17 Standard (/ Std: c ++ 17)*.</span><span class="sxs-lookup"><span data-stu-id="bf558-162">Because C++/WinRT uses features from the C++17 standard, set project property **C/C++** > **Language** > **C++ Language Standard** to *ISO C++17 Standard (/std:c++17)*.</span></span>

### <a name="the-precompiled-header"></a><span data-ttu-id="bf558-163">Die vorkompilierte Headerdatei</span><span class="sxs-lookup"><span data-stu-id="bf558-163">The precompiled header</span></span>

<span data-ttu-id="bf558-164">Benennen Sie Ihre `stdafx.h` und `stdafx.cpp` , `pch.h` und `pch.cpp`bzw..</span><span class="sxs-lookup"><span data-stu-id="bf558-164">Rename your `stdafx.h` and `stdafx.cpp` to `pch.h` and `pch.cpp`, respectively.</span></span> <span data-ttu-id="bf558-165">Projekteigenschaft **C/C++** > **Vorkompilierte Header** > **Vorkompilierte Headerdatei** *pch.h*.</span><span class="sxs-lookup"><span data-stu-id="bf558-165">Set project property **C/C++** > **Precompiled Headers** > **Precompiled Header File** to *pch.h*.</span></span>

<span data-ttu-id="bf558-166">Suchen und Ersetzen Sie den gesamten `#include "stdafx.h"` mit `#include "pch.h"`.</span><span class="sxs-lookup"><span data-stu-id="bf558-166">Find and replace all `#include "stdafx.h"` with `#include "pch.h"`.</span></span>

<span data-ttu-id="bf558-167">In `pch.h`, umfassen `winrt/base.h`.</span><span class="sxs-lookup"><span data-stu-id="bf558-167">In `pch.h`, include `winrt/base.h`.</span></span>

```cppwinrt
// pch.h
...
#include <winrt/base.h>
```

<span data-ttu-id="bf558-168">Stellen Sie sicher, dass Sie nicht betroffen sind [Warum nicht meine neue Projekt kompiliert?](/windows/uwp/cpp-and-winrt-apis/faq).</span><span class="sxs-lookup"><span data-stu-id="bf558-168">Confirm that you're not affected by [Why won't my new project compile?](/windows/uwp/cpp-and-winrt-apis/faq).</span></span>

### <a name="implement-the-coclass-class-factory-and-in-proc-server-exports"></a><span data-ttu-id="bf558-169">Implementieren der Co-Klassenfactory und in-Process-Server Exporte</span><span class="sxs-lookup"><span data-stu-id="bf558-169">Implement the coclass, class factory, and in-proc server exports</span></span>

<span data-ttu-id="bf558-170">Öffnen `dllmain.cpp`, und fügen Sie im Codebeispiel unten gezeigt hinzu.</span><span class="sxs-lookup"><span data-stu-id="bf558-170">Open `dllmain.cpp`, and add to it the code listing shown below.</span></span>

<span data-ttu-id="bf558-171">Wenn Sie bereits über eine DLL-Datei haben, die C++ implementiert / WinRT-Windows-Runtime-Klassen, und klicken Sie dann Sie bereits die unten angezeigte **DllCanUnloadNow** -Funktion müssen.</span><span class="sxs-lookup"><span data-stu-id="bf558-171">If you already have a DLL that implements C++/WinRT Windows Runtime classes, then you'll already have the **DllCanUnloadNow** function shown below.</span></span> <span data-ttu-id="bf558-172">Wenn Sie diese DLL Co-Klassen hinzufügen möchten, können Sie die Funktion **DllGetClassObject** hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="bf558-172">If you want to add coclasses to that DLL, then you can add the **DllGetClassObject** function.</span></span>

<span data-ttu-id="bf558-173">Wenn keine vorhandenen [Windows-Runtime C++ Template Library (WRL)](/cpp/windows/windows-runtime-cpp-template-library-wrl) -Code, der mit kompatibel bleiben soll haben, dann können Sie die WRL-Teile der gezeigte Code entfernen.</span><span class="sxs-lookup"><span data-stu-id="bf558-173">If don't have existing [Windows Runtime C++ Template Library (WRL)](/cpp/windows/windows-runtime-cpp-template-library-wrl) code that you want to stay compatible with, then you can remove the WRL parts from the code shown.</span></span>

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

## <a name="important-apis"></a><span data-ttu-id="bf558-174">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="bf558-174">Important APIs</span></span>
* [<span data-ttu-id="bf558-175">IInspectable-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="bf558-175">IInspectable interface</span></span>](https://msdn.microsoft.com/library/br205821)
* [<span data-ttu-id="bf558-176">IUnknown Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="bf558-176">IUnknown interface</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms680509)
* [<span data-ttu-id="bf558-177">winrt::implements Strukturvorlage</span><span class="sxs-lookup"><span data-stu-id="bf558-177">winrt::implements struct template</span></span>](/uwp/cpp-ref-for-winrt/implements)

## <a name="related-topics"></a><span data-ttu-id="bf558-178">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="bf558-178">Related topics</span></span>
* [<span data-ttu-id="bf558-179">Erstellen von APIs mit C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="bf558-179">Author APIs with C++/WinRT</span></span>](/windows/uwp/cpp-and-winrt-apis/author-apis)
* [<span data-ttu-id="bf558-180">Verwenden von COM-Komponenten mit C++ / WinRT</span><span class="sxs-lookup"><span data-stu-id="bf558-180">Consume COM components with C++/WinRT</span></span>](consume-com.md)
* [<span data-ttu-id="bf558-181">Senden einer lokalen Popupbenachrichtigung</span><span class="sxs-lookup"><span data-stu-id="bf558-181">Send a local toast notification</span></span>](/windows/uwp/design/shell/tiles-and-notifications/send-local-toast)
