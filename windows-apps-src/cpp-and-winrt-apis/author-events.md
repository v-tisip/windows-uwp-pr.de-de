---
author: stevewhims
description: Dieses Thema zeigt, wie man eine Komponente für Windows-Runtime erstellt, die eine Laufzeitklasse enthält, die Ereignisse auslöst. Es zeigt außerdem eine App, die die Komponente nutzt und die Ereignisse verarbeitet.
title: Erstellen von Ereignissen mit C++/WinRT
ms.author: stwhi
ms.date: 07/18/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp, standard, c++, cpp, winrt, projektion, erstellen, ereignis
ms.localizationpriority: medium
ms.openlocfilehash: 3b52bf8e33bbf111dd02c695d8c3baf77e1338ac
ms.sourcegitcommit: 753dfcd0f9fdfc963579dd0b217b445c4b110a18
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "2862606"
---
# <a name="author-events-in-cwinrtwindowsuwpcpp-and-winrt-apisintro-to-using-cpp-with-winrt"></a><span data-ttu-id="f02cf-105">Erstellen von Ereignissen mit [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)</span><span class="sxs-lookup"><span data-stu-id="f02cf-105">Author events in [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)</span></span>

<span data-ttu-id="f02cf-106">Dieses Thema zeigt, wie man eine Komponente für Windows-Runtime erstellt, die eine Laufzeitklasse für ein Bankkonto enthält, die ein Ereignis auslöst, wenn sein Saldo ins Minus gerät.</span><span class="sxs-lookup"><span data-stu-id="f02cf-106">This topic demonstrates how to author a Windows Runtime Component containing a runtime class representing a bank account, which raises an event when its balance goes into debit.</span></span> <span data-ttu-id="f02cf-107">Es demonstriert außerdem eine Core App, die die Bankkonto-Laufzeitklasse nutzt, eine Funktion zur Anpassung des Saldos aufruft und alle daraus resultierenden Ereignisse verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="f02cf-107">It also demonstrates a Core App that consumes the bank account runtime class, calls a function to adjust the balance, and handles any events that result.</span></span>

> [!NOTE]
> <span data-ttu-id="f02cf-108">Informationen zur Installation und Verwendung der C++/WinRT Visual Studio Extension (VSIX) (die Projektvorlagenunterstützung sowie C++/WinRT MSBuild-Eigenschaften und -Ziele bietet) finden Sie unter [Visual Studio-Unterstützung für C++/WinRT und VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix).</span><span class="sxs-lookup"><span data-stu-id="f02cf-108">For info about installing and using the C++/WinRT Visual Studio Extension (VSIX) (which provides project template support, as well as C++/WinRT MSBuild properties and targets) see [Visual Studio support for C++/WinRT, and the VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f02cf-109">Wichtige Konzepte und Begriffe, die Ihr Verständnis für die Verwendung von Laufzeitklassen mit C++/WinRT unterstützen, finden Sie unter [Verwenden von APIs mit C++/WinRT](consume-apis.md) und [Erstellen von APIs mit C++/WinRT](author-apis.md).</span><span class="sxs-lookup"><span data-stu-id="f02cf-109">For essential concepts and terms that support your understanding of how to consume and author runtime classes with C++/WinRT, see [Consume APIs with C++/WinRT](consume-apis.md) and [Author APIs with C++/WinRT](author-apis.md).</span></span>

## <a name="create-a-windows-runtime-component-bankaccountwrc"></a><span data-ttu-id="f02cf-110">Erstellen einer Komponente für Windows-Runtime (BankAccountWRC)</span><span class="sxs-lookup"><span data-stu-id="f02cf-110">Create a Windows Runtime Component (BankAccountWRC)</span></span>

<span data-ttu-id="f02cf-111">Erstellen Sie zunächst ein neues Projekt in Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f02cf-111">Begin by creating a new project in Microsoft Visual Studio.</span></span> <span data-ttu-id="f02cf-112">Erstellen Sie ein **Visual C++ Windows-Runtime Component (C++/WinRT)** Projekt und nennen Sie es *BankAccountWRC* (für „Bankkonto-Komponente für Windows-Runtime”).</span><span class="sxs-lookup"><span data-stu-id="f02cf-112">Create a **Visual C++ Windows Runtime Component (C++/WinRT)** project, and name it *BankAccountWRC* (for "bank account Windows Runtime Component").</span></span>

<span data-ttu-id="f02cf-113">Das neu erstellte Projekt enthält eine Datei mit dem Namen `Class.idl`.</span><span class="sxs-lookup"><span data-stu-id="f02cf-113">The newly-created project contains a file named `Class.idl`.</span></span> <span data-ttu-id="f02cf-114">Benennen Sie diese Datei `BankAccount.idl` (Umbenennen der `.idl` Datei benennt automatisch der abhängigen `.h` und `.cpp` Dateien zu).</span><span class="sxs-lookup"><span data-stu-id="f02cf-114">Rename that file `BankAccount.idl` (renaming the `.idl` file automatically renames the dependent `.h` and `.cpp` files, too).</span></span> <span data-ttu-id="f02cf-115">Ersetzen Sie den Inhalt der `BankAccount.idl` mit der Liste unten.</span><span class="sxs-lookup"><span data-stu-id="f02cf-115">Replace the contents of `BankAccount.idl` with the listing below.</span></span>

```idl
// BankAccountWRC.idl
namespace BankAccountWRC
{
    runtimeclass BankAccount
    {
        BankAccount();
        event Windows.Foundation.EventHandler<Single> AccountIsInDebit;
        void AdjustBalance(Single value);
    };
}
```

<span data-ttu-id="f02cf-116">Speichern Sie die Datei.</span><span class="sxs-lookup"><span data-stu-id="f02cf-116">Save the file.</span></span> <span data-ttu-id="f02cf-117">Erstellen Sie das Projekt wird nicht erfolgreich abgeschlossen, in dem Moment, aber jetzt erstellen, ist ein sinnvoll, da die Quellcodedateien generiert wird, in denen Sie die **BankAccount** Common Language Runtime-Klasse implementieren können.</span><span class="sxs-lookup"><span data-stu-id="f02cf-117">The project won't build to completion at the moment, but building now is a useful thing to do because it generates the source code files in which you'll implement the **BankAccount** runtime class.</span></span> <span data-ttu-id="f02cf-118">So fahren Sie fort, und erstellen Sie jetzt (die Buildfehler zu erwarten, dass in dieser Phase finden Sie unter mit zu tun haben `Class.h` und `Class.g.h` nicht gefunden wurde).</span><span class="sxs-lookup"><span data-stu-id="f02cf-118">So go ahead and build now (the build errors you can expect to see at this stage have to do with `Class.h` and `Class.g.h` not being found).</span></span> <span data-ttu-id="f02cf-119">Beim Erstellen die `midl.exe` Tool wird ausgeführt, um die Komponente Windows-Runtime Metadaten-Datei zu erstellen (also `\BankAccountWRC\Debug\BankAccountWRC\BankAccountWRC.winmd`).</span><span class="sxs-lookup"><span data-stu-id="f02cf-119">During the build process, the `midl.exe` tool is run to create your component's Windows Runtime metadata file (which is `\BankAccountWRC\Debug\BankAccountWRC\BankAccountWRC.winmd`).</span></span> <span data-ttu-id="f02cf-120">Dann wird das `cppwinrt.exe`-Tool ausgeführt (mit der Option `-component`), um Quelltextdateien zu erzeugen, die Sie bei der Erstellung Ihrer Komponente unterstützen.</span><span class="sxs-lookup"><span data-stu-id="f02cf-120">Then, the `cppwinrt.exe` tool is run (with the `-component` option) to generate source code files to support you in authoring your component.</span></span> <span data-ttu-id="f02cf-121">Diese Dateien enthalten Stubs, um Ihnen den Einstieg Implementieren der **BankAccount** Runtime-Klasse, die Sie in Ihre IDL deklariert zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="f02cf-121">These files include stubs to get you started implementing the **BankAccount** runtime class that you declared in your IDL.</span></span> <span data-ttu-id="f02cf-122">Diese Stubs sind `\BankAccountWRC\BankAccountWRC\Generated Files\sources\BankAccount.h` und `BankAccount.cpp`.</span><span class="sxs-lookup"><span data-stu-id="f02cf-122">Those stubs are `\BankAccountWRC\BankAccountWRC\Generated Files\sources\BankAccount.h` and `BankAccount.cpp`.</span></span>

<span data-ttu-id="f02cf-123">Kopieren Sie die Stub-Dateien im Datei-Explorer `BankAccount.h` und `BankAccount.cpp` aus dem Ordner `\BankAccountWRC\BankAccountWRC\Generated Files\sources\` in den Ordner, die Ihre Projektdateien enthält, wird die `\BankAccountWRC\BankAccountWRC\`, und Ersetzen Sie die Dateien in das Ziel.</span><span class="sxs-lookup"><span data-stu-id="f02cf-123">In File Explorer, copy the stub files `BankAccount.h` and `BankAccount.cpp` from the folder `\BankAccountWRC\BankAccountWRC\Generated Files\sources\` into the folder that contains your project files, which is `\BankAccountWRC\BankAccountWRC\`, and replace the files in the destination.</span></span> <span data-ttu-id="f02cf-124">Nun öffnen wir `BankAccount.h` und `BankAccount.cpp` und implementieren unsere Laufzeitklasse.</span><span class="sxs-lookup"><span data-stu-id="f02cf-124">Now, let's open `BankAccount.h` and `BankAccount.cpp` and implement our runtime class.</span></span> <span data-ttu-id="f02cf-125">Fügen Sie in `BankAccount.h` zwei private Mitglieder zur Implementierung von BankAccount hinzu (*nicht* zur Factory-Implementierung).</span><span class="sxs-lookup"><span data-stu-id="f02cf-125">In `BankAccount.h`, add two private members to the implementation (*not* the factory implementation) of BankAccount.</span></span>

```cppwinrt
// BankAccount.h
...
namespace winrt::BankAccountWRC::implementation
{
    struct BankAccount : BankAccountT<BankAccount>
    {
        ...

    private:
        winrt::event<Windows::Foundation::EventHandler<float>> m_accountIsInDebitEvent;
        float m_balance{ 0.f };
    };
}
...
```

<span data-ttu-id="f02cf-126">Wie oben zu sehen ist, wird das Ereignis im Hinblick auf die Vorlage [**winrt::event**](/uwp/cpp-ref-for-winrt/event) Struktur, nach einer bestimmten Stellvertretung Typ parametrisiert implementiert.</span><span class="sxs-lookup"><span data-stu-id="f02cf-126">As you can see above, the event is implemented in terms of the [**winrt::event**](/uwp/cpp-ref-for-winrt/event) struct template, parameterized by a particular delegate type.</span></span>

<span data-ttu-id="f02cf-127">Implementieren Sie in `BankAccount.cpp` die Funktionen wie im folgenden Codebeispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="f02cf-127">In `BankAccount.cpp`, implement the functions as shown in the code example below.</span></span> <span data-ttu-id="f02cf-128">In C++/WinRT wird ein IDL-deklariertes Ereignis als ein Set überladener Funktionen implementiert (ähnlich wie eine Eigenschaft als ein Paar von überladenen Get- und Set-Funktionen implementiert wird).</span><span class="sxs-lookup"><span data-stu-id="f02cf-128">In C++/WinRT, an IDL-declared event is implemented as a set of overloaded functions (similar to the way a property is implemented as a pair of overloaded get and set functions).</span></span> <span data-ttu-id="f02cf-129">Eine Überladung übernimmt einen zu registrierenden Delegaten und gibt einen Token zurück.</span><span class="sxs-lookup"><span data-stu-id="f02cf-129">One overload takes a delegate to be registered, and returns a token.</span></span> <span data-ttu-id="f02cf-130">Die andere übernimmt einen Token und widerruft die Registrierung des zugeordneten Delegats.</span><span class="sxs-lookup"><span data-stu-id="f02cf-130">The other takes a token, and revokes the registration of the associated delegate.</span></span>

```cppwinrt
// BankAccount.cpp
...
namespace winrt::BankAccountWRC::implementation
{
    winrt::event_token BankAccount::AccountIsInDebit(Windows::Foundation::EventHandler<float> const& handler)
    {
        return m_accountIsInDebitEvent.add(handler);
    }

    void BankAccount::AccountIsInDebit(winrt::event_token const& token)
    {
        m_accountIsInDebitEvent.remove(token);
    }

    void BankAccount::AdjustBalance(float value)
    {
        m_balance += value;
        if (m_balance < 0.f) m_accountIsInDebitEvent(*this, m_balance);
    }
}
```

<span data-ttu-id="f02cf-131">Sie müssen nicht die Überladung für den Ereignis-Revoker implementieren (weitere Informationen siehe [Einen registrierten Delegaten widerrufen](handle-events.md#revoke-a-registered-delegate))– dies übernimmt die C++/WinRT-Projektion für Sie.</span><span class="sxs-lookup"><span data-stu-id="f02cf-131">You don't need to implement the overload for the event revoker (for details, see [Revoke a registered delegate](handle-events.md#revoke-a-registered-delegate))&mdash;that's taken care of for you by the C++/WinRT projection.</span></span> <span data-ttu-id="f02cf-132">Die anderen Überladungen sind nicht in die Projektion integriert, um Ihnen die Flexibilität zu geben, sie für Ihr Szenario optimal zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="f02cf-132">The other overloads are not baked into the projection, in order to give you the flexibility to implement them optimally for your scenario.</span></span> <span data-ttu-id="f02cf-133">Ein derartiger Aufruf von [**event::add**](/uwp/cpp-ref-for-winrt/event#eventadd-function) und [**event::remove**](/uwp/cpp-ref-for-winrt/event#eventremove-function) ist eine effiziente und parallele/threadsichere Standardmethode.</span><span class="sxs-lookup"><span data-stu-id="f02cf-133">Calling [**event::add**](/uwp/cpp-ref-for-winrt/event#eventadd-function) and [**event::remove**](/uwp/cpp-ref-for-winrt/event#eventremove-function) like this is an efficient and concurrency/thread-safe default.</span></span> <span data-ttu-id="f02cf-134">Wenn Sie jedoch über eine große Anzahl von Ereignissen verfügen, möchten Sie möglicherweise nicht für jedes ein Ereignisfeld, sondern vielmehr eine Implementierung mit geringer Dichte.</span><span class="sxs-lookup"><span data-stu-id="f02cf-134">But if you have a very large number of events, then you may not want an event field for each, but rather opt for some kind of sparse implementation instead.</span></span>

<span data-ttu-id="f02cf-135">Sie sehen oben, dass die Implementierung der Funktion **AdjustBalance** das Ereignis **AccountIsInDebit** auslöst, wenn der Saldo negativ wird.</span><span class="sxs-lookup"><span data-stu-id="f02cf-135">You can also see above that the implementation of the **AdjustBalance** function raises the **AccountIsInDebit** event if the balance goes negative.</span></span>

<span data-ttu-id="f02cf-136">Wenn alle Warnungen Sie zum Erstellen von zu verhindern, klicken Sie dann entweder beheben Sie diese oder legen Sie die Projekteigenschaft **C/C++-** > **Allgemeine** > **Warnungen als Fehler behandeln** , die **No (/ WX-)**, und erstellen Sie das Projekt erneut.</span><span class="sxs-lookup"><span data-stu-id="f02cf-136">If any warnings prevent you from building, then either resolve them or set the project property **C/C++** > **General** > **Treat Warnings As Errors** to **No (/WX-)**, and build the project again.</span></span>

## <a name="create-a-core-app-bankaccountcoreapp-to-test-the-windows-runtime-component"></a><span data-ttu-id="f02cf-137">Erstellen einer Core App (BankAccountCoreApp) zum Testen der Komponente für Windows-Runtime</span><span class="sxs-lookup"><span data-stu-id="f02cf-137">Create a Core App (BankAccountCoreApp) to test the Windows Runtime Component</span></span>

<span data-ttu-id="f02cf-138">Erstellen Sie nun ein neues Projekt (entweder in Ihrer `BankAccountWRC`-Lösung oder in einer neuen).</span><span class="sxs-lookup"><span data-stu-id="f02cf-138">Now create a new project (either in your `BankAccountWRC` solution, or in a new one).</span></span> <span data-ttu-id="f02cf-139">Erstellen Sie ein **Visual C++ Core App (C++/WinRT)**-Projekt, und nennen Sie es *BankAccountCoreApp*.</span><span class="sxs-lookup"><span data-stu-id="f02cf-139">Create a **Visual C++ Core App (C++/WinRT)** project, and name it *BankAccountCoreApp*.</span></span>

<span data-ttu-id="f02cf-140">Fügen Sie einen Verweis hinzu, und wechseln Sie zur `\BankAccountWRC\Debug\BankAccountWRC\BankAccountWRC.winmd` (oder einen Projekt in Project Verweis hinzufügen, wenn beide Projekte in der gleichen Projektmappe sind).</span><span class="sxs-lookup"><span data-stu-id="f02cf-140">Add a reference, and browse to `\BankAccountWRC\Debug\BankAccountWRC\BankAccountWRC.winmd` (or add a project-to-project reference, if the two projects are in the same solution).</span></span> <span data-ttu-id="f02cf-141">Klicken Sie auf **Hinzufügen** und dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="f02cf-141">Click **Add**, and then **OK**.</span></span> <span data-ttu-id="f02cf-142">Erstellen Sie jetzt BankAccountCoreApp.</span><span class="sxs-lookup"><span data-stu-id="f02cf-142">Now build BankAccountCoreApp.</span></span> <span data-ttu-id="f02cf-143">Im unwahrscheinlichen Fall, dass ein Fehler angezeigt, die die Nutzlastdatei `readme.txt` nicht vorhanden, diese Datei aus dem Windows-Laufzeitkomponente Projekt ausschließen, erstellen Sie ihn neu und dann neu erstellen BankAccountCoreApp.</span><span class="sxs-lookup"><span data-stu-id="f02cf-143">In the unlikely event that you see an error that the payload file `readme.txt` doesn't exist, exclude that file from the Windows Runtime Component project, rebuild it, then rebuild BankAccountCoreApp.</span></span>

<span data-ttu-id="f02cf-144">Während des Buildprozesses wird das `cppwinrt.exe`-Tool ausgeführt, um die referenzierte `.winmd`-Datei in Quellcodedateien zu verarbeiten, die projizierte Typen enthalten, um Sie bei der Verwendung Ihrer Komponente zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="f02cf-144">During the build process, the `cppwinrt.exe` tool is run to process the referenced `.winmd` file into source code files containing projected types to support you in consuming your component.</span></span> <span data-ttu-id="f02cf-145">Der Header für die projizierten Typen für die Laufzeitklassen Ihrer Komponente (mit dem Namen `BankAccountWRC.h`) wird im Ordner `\BankAccountCoreApp\BankAccountCoreApp\Generated Files\winrt\` generiert.</span><span class="sxs-lookup"><span data-stu-id="f02cf-145">The header for the projected types for your component's runtime classes&mdash;named `BankAccountWRC.h`&mdash;is generated into the folder `\BankAccountCoreApp\BankAccountCoreApp\Generated Files\winrt\`.</span></span>

<span data-ttu-id="f02cf-146">Fügen Sie diesen Header in `App.cpp` ein.</span><span class="sxs-lookup"><span data-stu-id="f02cf-146">Include that header in `App.cpp`.</span></span>

```cppwinrt
#include <winrt/BankAccountWRC.h>
```

<span data-ttu-id="f02cf-147">Fügen Sie in `App.cpp` ebenfalls den folgenden Code ein, um ein BankAccount zu instanziieren (unter Verwendung des Standardkonstruktors des projizierten Typs), registrieren Sie einen Ereignis-Handler und sorgen Sie dann dafür, dass das Konto ins Minus geht.</span><span class="sxs-lookup"><span data-stu-id="f02cf-147">Also in `App.cpp`, add the following code to instantiate a BankAccount (using the projected type's default constructor), register an event handler, and then cause the account to go into debit.</span></span>

```cppwinrt
struct App : implements<App, IFrameworkViewSource, IFrameworkView>
{
    BankAccountWRC::BankAccount m_bankAccount;
    winrt::event_token m_eventToken;
    ...
    
    void Initialize(CoreApplicationView const &)
    {
        m_eventToken = m_bankAccount.AccountIsInDebit([](const auto &, float balance)
        {
            WINRT_ASSERT(balance < 0.f);
        });
    }
    ...

    void Uninitialize()
    {
        m_bankAccount.AccountIsInDebit(m_eventToken);
    }
    ...

    void OnPointerPressed(IInspectable const &, PointerEventArgs const & args)
    {
        m_bankAccount.AdjustBalance(-1.f);
        ...
    }
    ...
};
```

<span data-ttu-id="f02cf-148">Jedes Mal, wenn Sie auf das Fenster klicken, ziehen Sie 1 vom Kontostand ab.</span><span class="sxs-lookup"><span data-stu-id="f02cf-148">Each time you click the window, you subtract 1 from the bank account's balance.</span></span> <span data-ttu-id="f02cf-149">Um zu veranschaulichen, dass das Ereignis ausgelöst wird, wie erwartet, setzen Sie einen Haltepunkt innerhalb der Lambda-Ausdruck, der die **AccountIsInDebit** Ereignisbehandlung, Ausführen der app, und klicken Sie in das Fenster.</span><span class="sxs-lookup"><span data-stu-id="f02cf-149">To demonstrate that the event is being raised as expected, put a breakpoint inside the lambda expression that's handling the **AccountIsInDebit** event, run the app, and click inside the window.</span></span>

## <a name="parameterized-delegates-and-simple-signals-across-an-abi"></a><span data-ttu-id="f02cf-150">Parametrisierte Stellvertretungen und einfachen signalisiert, über eine ABI</span><span class="sxs-lookup"><span data-stu-id="f02cf-150">Parameterized delegates, and simple signals, across an ABI</span></span>

<span data-ttu-id="f02cf-151">Wenn das Ereignis über eine binäre Anwendungsschnittstelle (ABI) zugegriffen werden muss&mdash;beispielsweise zwischen einer Komponente und der Dienste in Anspruch nehmenden Anwendung&mdash;und klicken Sie dann das Ereignis einen Typ der Windows-Runtime-Delegaten verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="f02cf-151">If your event must be accessible across an application binary interface (ABI)&mdash;such as between a component and its consuming application&mdash;then your event must use a Windows Runtime delegate type.</span></span> <span data-ttu-id="f02cf-152">Im obigen Beispiel verwendet [**Windows::Foundation::EventHandler\ < T\ >**](/uwp/api/windows.foundation.eventhandler) Windows-Runtime-Delegaten.</span><span class="sxs-lookup"><span data-stu-id="f02cf-152">The example above uses the [**Windows::Foundation::EventHandler\<T\>**](/uwp/api/windows.foundation.eventhandler) Windows Runtime delegate type.</span></span> <span data-ttu-id="f02cf-153">[**TypedEventHandler\ < TSender, TResult\ >**](/uwp/api/windows.foundation.eventhandler) ist ein weiteres Beispiel für einen Typ der Windows-Runtime-Delegaten.</span><span class="sxs-lookup"><span data-stu-id="f02cf-153">[**TypedEventHandler\<TSender, TResult\>**](/uwp/api/windows.foundation.eventhandler) is another example of a Windows Runtime delegate type.</span></span>

<span data-ttu-id="f02cf-154">Typparameter für diese zwei Delegattypen haben die ABI schneidet, damit die Typparameter zu Windows-Runtime-Typen werden müssen.</span><span class="sxs-lookup"><span data-stu-id="f02cf-154">The type parameters for those two delegate types have to cross the ABI, so the type parameters must be Windows Runtime types, too.</span></span> <span data-ttu-id="f02cf-155">Erste und Drittanbieter-Runtime-Klassen als auch Grundtypen wie Zahlen und Zeichenfolgen enthält.</span><span class="sxs-lookup"><span data-stu-id="f02cf-155">That includes first- and third-party runtime classes, as well as primitive types such as numbers and strings.</span></span> <span data-ttu-id="f02cf-156">Der Compiler können Sie mit einem "*muss WinRT Typ*" Fehler, wenn Sie diese Einschränkung vergessen haben.</span><span class="sxs-lookup"><span data-stu-id="f02cf-156">The compiler helps you with a "*must be WinRT type*" error if you forget that constraint.</span></span>

<span data-ttu-id="f02cf-157">Wenn Sie keine Parameter oder Argumente mit dem Ereignis übergeben möchten, können Sie Ihre eigene einfachen Typ der Windows-Runtime-Delegaten definieren.</span><span class="sxs-lookup"><span data-stu-id="f02cf-157">If you don't need to pass any parameters or arguments with your event, then you can define your own simple Windows Runtime delegate type.</span></span> <span data-ttu-id="f02cf-158">Das folgende Beispiel zeigt eine einfachere Version der Common Language Runtime **BankAccount** -Klasse.</span><span class="sxs-lookup"><span data-stu-id="f02cf-158">The example below shows a simpler version of the **BankAccount** runtime class.</span></span> <span data-ttu-id="f02cf-159">Deklariert einen Delegattyp mit dem Namen **SignalDelegate** , und klicken Sie dann verwendet, die ein Signal-Typ-Ereignis anstelle eines Ereignisses mit einem Parameter aus.</span><span class="sxs-lookup"><span data-stu-id="f02cf-159">It declares a delegate type named **SignalDelegate** and then it uses that to raise a signal-type event instead of an event with a parameter.</span></span>

```idl
// BankAccountWRC.idl
namespace BankAccountWRC
{
    delegate void SignalDelegate();

    runtimeclass BankAccount
    {
        BankAccount();
        event BankAccountWRC.SignalDelegate SignalAccountIsInDebit;
        void AdjustBalance(Single value);
    };
}
```

```cppwinrt
// BankAccount.h
...
namespace winrt::BankAccountWRC::implementation
{
    struct BankAccount : BankAccountT<BankAccount>
    {
        ...

        winrt::event_token SignalAccountIsInDebit(BankAccountWRC::SignalDelegate const& handler);
        void SignalAccountIsInDebit(winrt::event_token const& token);
        void AdjustBalance(float value);

    private:
        winrt::event<BankAccountWRC::SignalDelegate> m_signal;
        float m_balance{ 0.f };
    };
}
```

```cppwinrt
// BankAccount.cpp
...
namespace winrt::BankAccountWRC::implementation
{
    winrt::event_token BankAccount::SignalAccountIsInDebit(BankAccountWRC::SignalDelegate const& handler)
    {
        return m_signal.add(handler);
    }

    void BankAccount::SignalAccountIsInDebit(winrt::event_token const& token)
    {
        m_signal.remove(token);
    }

    void BankAccount::AdjustBalance(float value)
    {
        m_balance += value;
        if (m_balance < 0.f)
        {
            m_signal();
        }
    }
}
```

```cppwinrt
// App.cpp
struct App : implements<App, IFrameworkViewSource, IFrameworkView>
{
    BankAccountWRC::BankAccount m_bankAccount;
    winrt::event_token m_eventToken;
    ...
    
    void Initialize(CoreApplicationView const &)
    {
        m_eventToken = m_bankAccount.SignalAccountIsInDebit([] { /* ... */ });
    }
    ...

    void Uninitialize()
    {
        m_bankAccount.SignalAccountIsInDebit(m_eventToken);
    }
    ...

    void OnPointerPressed(IInspectable const &, PointerEventArgs const & args)
    {
        m_bankAccount.AdjustBalance(-1.f);
        ...
    }
    ...
};
```

## <a name="parameterized-delegates-simple-signals-and-callbacks-within-a-project"></a><span data-ttu-id="f02cf-160">Parametrisierte Stellvertretungen, einfache Anmelde- und Rückrufe innerhalb eines Projekts</span><span class="sxs-lookup"><span data-stu-id="f02cf-160">Parameterized delegates, simple signals, and callbacks within a project</span></span>

<span data-ttu-id="f02cf-161">Wenn das Ereignis nur intern verwendet wird in Ihrem C + / WinRT project (nicht über Binärdateien), und klicken Sie dann weiterhin die [**winrt::event**](/uwp/cpp-ref-for-winrt/event) Struct-Vorlage verwendet werden, aber Sie mit C + parametrisieren / WinRTs Windows-Runtime [**winrt::delegate&lt;... T&gt; **](/uwp/cpp-ref-for-winrt/delegate) Struct-Vorlage, die eine effiziente und Verweis gezählt Delegat ist.</span><span class="sxs-lookup"><span data-stu-id="f02cf-161">If your event is used only internally within your C++/WinRT project (not across binaries), then you still use the [**winrt::event**](/uwp/cpp-ref-for-winrt/event) struct template, but you parameterize it with C++/WinRT's non-Windows-Runtime [**winrt::delegate&lt;... T&gt;**](/uwp/cpp-ref-for-winrt/delegate) struct template, which is an efficient, reference-counted delegate.</span></span> <span data-ttu-id="f02cf-162">Eine beliebige Anzahl Parameter unterstützt und sind nicht auf Windows-Runtime Typen beschränkt.</span><span class="sxs-lookup"><span data-stu-id="f02cf-162">It supports any number of parameters, and they are not limited to Windows Runtime types.</span></span>

<span data-ttu-id="f02cf-163">Das folgende Beispiel zeigt eine Stellvertretung zuerst, Signatur, die keine Parameter (im Wesentlichen eine einfache Signal) und dann ein, die eine Zeichenfolge akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="f02cf-163">The example below first shows a delegate signature that doesn't take any parameters (essentially a simple signal), and then one that takes a string.</span></span>

```cppwinrt
winrt::event<winrt::delegate<>> signal;
signal.add([] { std::wcout << L"Hello, "; });
signal.add([] { std::wcout << L"World!" << std::endl; });
signal();

winrt::event<winrt::delegate<std::wstring>> log;
log.add([](std::wstring const& message) { std::wcout << message.c_str() << std::endl; });
log.add([](std::wstring const& message) { Persist(message); });
log(L"Hello, World!");
```

<span data-ttu-id="f02cf-164">Beachten Sie, wie Sie das Ereignis hinzufügen können beliebig viele abonnierende Stellvertretungen wie gewünscht.</span><span class="sxs-lookup"><span data-stu-id="f02cf-164">Notice how you can add to the event as many subscribing delegates as you wish.</span></span> <span data-ttu-id="f02cf-165">Es ist jedoch Mehraufwand ein Ereignis zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="f02cf-165">However, there is some overhead associated with an event.</span></span> <span data-ttu-id="f02cf-166">Wenn Sie benötigen lediglich einen einfachen Rückruf mit nur einem einzigen abonnierenden Delegaten, können Sie [**winrt::delegate&lt;... T&gt; **](/uwp/cpp-ref-for-winrt/delegate) eigenständig.</span><span class="sxs-lookup"><span data-stu-id="f02cf-166">If all you need is a simple callback with only a single subscribing delegate, then you can use [**winrt::delegate&lt;... T&gt;**](/uwp/cpp-ref-for-winrt/delegate) on its own.</span></span>

```cppwinrt
winrt::delegate<> signalCallback;
signalCallback = [] { std::wcout << L"Hello, World!" << std::endl; };
signalCallback();

winrt::delegate<std::wstring> logCallback;
logCallback = [](std::wstring const& message) { std::wcout << message.c_str() << std::endl; }f;
logCallback(L"Hello, World!");
```

<span data-ttu-id="f02cf-167">Wenn Sie von C + Portieren sind / CX Codebasis, in dem Ereignisse und Delegaten intern innerhalb eines Projekts verwendet werden, und klicken Sie dann **winrt::delegate** helfen Ihnen beim Replizieren dieses Muster in C + / WinRT.</span><span class="sxs-lookup"><span data-stu-id="f02cf-167">If you're porting from a C++/CX codebase where events and delegates are used internally within a project, then **winrt::delegate** will help you to replicate that pattern in C++/WinRT.</span></span>

## <a name="design-guidelines"></a><span data-ttu-id="f02cf-168">Entwurfsrichtlinien</span><span class="sxs-lookup"><span data-stu-id="f02cf-168">Design guidelines</span></span>

<span data-ttu-id="f02cf-169">Es wird empfohlen, dass Sie Ereignisse und Stellvertretungen nicht angezeigt, als Funktionsparameter übergeben.</span><span class="sxs-lookup"><span data-stu-id="f02cf-169">We recommend that you pass events, and not delegates, as function parameters.</span></span> <span data-ttu-id="f02cf-170">Die **add** -Funktion [**winrt::event**](/uwp/cpp-ref-for-winrt/event) ist die einzige Ausnahme, da Sie eine Stellvertretung müssen in diesem Fall übergeben.</span><span class="sxs-lookup"><span data-stu-id="f02cf-170">The **add** function of [**winrt::event**](/uwp/cpp-ref-for-winrt/event) is the one exception, because you must pass a delegate in that case.</span></span> <span data-ttu-id="f02cf-171">Der Grund für diese Richtlinie ist, da Delegaten in verschiedenen Sprachen von Windows-Runtime (im Hinblick auf gibt an, ob sie eine Client-Registrierung oder mehreren unterstützen) verschiedene Formen annehmen können.</span><span class="sxs-lookup"><span data-stu-id="f02cf-171">The reason for this guideline is because delegates can take different forms across different Windows Runtime languages (in terms of whether they support one client registration, or multiple).</span></span> <span data-ttu-id="f02cf-172">Ereignisse, mit deren Modell mit mehreren Abonnenten bilden eine sehr viel vorhersehbare und konsistente aus.</span><span class="sxs-lookup"><span data-stu-id="f02cf-172">Events, with their multiple subscriber model, constitute a much more predictable and consistent option.</span></span>

<span data-ttu-id="f02cf-173">Die Signatur für einen Ereignishandler-Delegaten sollten bestehen aus zwei Parameter: *Absender* (**IInspectable**) und *Args* (einige Argument Ereignistyp, beispielsweise [**"RoutedEventArgs"**](/uwp/api/windows.ui.xaml.routedeventargs)).</span><span class="sxs-lookup"><span data-stu-id="f02cf-173">The signature for an event handler delegate should consist of two parameters: *sender* (**IInspectable**), and *args* (some event argument type, for example [**RoutedEventArgs**](/uwp/api/windows.ui.xaml.routedeventargs)).</span></span>

<span data-ttu-id="f02cf-174">Beachten Sie, dass diese Richtlinien nicht unbedingt angewendet werden, wenn Sie eine interne API entwerfen.</span><span class="sxs-lookup"><span data-stu-id="f02cf-174">Note that these guidelines don't necessarily apply if you're designing an internal API.</span></span> <span data-ttu-id="f02cf-175">Obwohl interne APIs Laufe der Zeit häufig öffentliche werden.</span><span class="sxs-lookup"><span data-stu-id="f02cf-175">Although, internal APIs often become public over time.</span></span>

## <a name="related-topics"></a><span data-ttu-id="f02cf-176">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="f02cf-176">Related topics</span></span>
* [<span data-ttu-id="f02cf-177">Erstellen von APIs mit C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="f02cf-177">Author APIs with C++/WinRT</span></span>](author-apis.md)
* [<span data-ttu-id="f02cf-178">Verwenden von APIs mit C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="f02cf-178">Consume APIs with C++/WinRT</span></span>](consume-apis.md)
* [<span data-ttu-id="f02cf-179">Verarbeiten von Ereignissen über Delegaten in C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="f02cf-179">Handle events by using delegates in C++/WinRT</span></span>](handle-events.md)
