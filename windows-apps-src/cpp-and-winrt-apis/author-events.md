---
author: stevewhims
description: Dieses Thema zeigt, wie man eine Komponente für Windows-Runtime erstellt, die eine Laufzeitklasse enthält, die Ereignisse auslöst. Es zeigt außerdem eine App, die die Komponente nutzt und die Ereignisse verarbeitet.
title: Erstellen von Ereignissen mit C++/WinRT
ms.author: stwhi
ms.date: 05/07/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp, standard, c++, cpp, winrt, projektion, erstellen, ereignis
ms.localizationpriority: medium
ms.openlocfilehash: 192000f937989d7218931ce1465bd96d5d9b71c6
ms.sourcegitcommit: 834992ec14a8a34320c96e2e9b887a2be5477a53
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2018
ms.locfileid: "1880881"
---
# <a name="author-events-in-cwinrtwindowsuwpcpp-and-winrt-apisintro-to-using-cpp-with-winrt"></a><span data-ttu-id="40c40-105">Erstellen von Ereignissen mit [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)</span><span class="sxs-lookup"><span data-stu-id="40c40-105">Author events in [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)</span></span>
<span data-ttu-id="40c40-106">Dieses Thema zeigt, wie man eine Komponente für Windows-Runtime erstellt, die eine Laufzeitklasse für ein Bankkonto enthält, die ein Ereignis auslöst, wenn sein Saldo ins Minus gerät.</span><span class="sxs-lookup"><span data-stu-id="40c40-106">This topic demonstrates how to author a Windows Runtime Component containing a runtime class representing a bank account, which raises an event when its balance goes into debit.</span></span> <span data-ttu-id="40c40-107">Es demonstriert außerdem eine Core App, die die Bankkonto-Laufzeitklasse nutzt, eine Funktion zur Anpassung des Saldos aufruft und alle daraus resultierenden Ereignisse verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="40c40-107">It also demonstrates a Core App that consumes the bank account runtime class, calls a function to adjust the balance, and handles any events that result.</span></span>

> [!NOTE]
> <span data-ttu-id="40c40-108">Informationen zur Installation und Verwendung der C++/WinRT Visual Studio Extension (VSIX) (die Projektvorlagenunterstützung sowie C++/WinRT MSBuild-Eigenschaften und -Ziele bietet) finden Sie unter [Visual Studio-Unterstützung für C++/WinRT und VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix).</span><span class="sxs-lookup"><span data-stu-id="40c40-108">For info about installing and using the C++/WinRT Visual Studio Extension (VSIX) (which provides project template support, as well as C++/WinRT MSBuild properties and targets) see [Visual Studio support for C++/WinRT, and the VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="40c40-109">Wichtige Konzepte und Begriffe, die Ihr Verständnis für die Verwendung von Laufzeitklassen mit C++/WinRT unterstützen, finden Sie unter [Verwenden von APIs mit C++/WinRT](consume-apis.md) und [Erstellen von APIs mit C++/WinRT](author-apis.md).</span><span class="sxs-lookup"><span data-stu-id="40c40-109">For essential concepts and terms that support your understanding of how to consume and author runtime classes with C++/WinRT, see [Consume APIs with C++/WinRT](consume-apis.md) and [Author APIs with C++/WinRT](author-apis.md).</span></span>

## <a name="windowsfoundationeventhandlerlttgt-and-typedeventhandlerlttgt"></a><span data-ttu-id="40c40-110">Windows::Foundation::EventHandler&lt;T&gt; und TypedEventHandler&lt;T&gt;</span><span class="sxs-lookup"><span data-stu-id="40c40-110">Windows::Foundation::EventHandler&lt;T&gt; and TypedEventHandler&lt;T&gt;</span></span>
<span data-ttu-id="40c40-111">Wenn Sie ein Ereignis aus einer in einer Komponente für Windows-Runtime implementierten Laufzeitklasse auslösen möchten, sollten Sie [**Windows::Foundation::EventHandler**](/uwp/api/windows.foundation.eventhandler) oder [**TypedEventHandler**](/uwp/api/windows.foundation.eventhandler) für den Delegattyp Ihres Ereignisses verwenden.</span><span class="sxs-lookup"><span data-stu-id="40c40-111">If you want to raise an event from a runtime class implemented in a Windows Runtime Component, then you should use [**Windows::Foundation::EventHandler**](/uwp/api/windows.foundation.eventhandler) or [**TypedEventHandler**](/uwp/api/windows.foundation.eventhandler) for your event's delegate type.</span></span> <span data-ttu-id="40c40-112">Die Typparameter müssen Windows-Runtime-Typen sein. Daher sind primitive Typen und Laufzeitklassen von Drittanbietern zulässig.</span><span class="sxs-lookup"><span data-stu-id="40c40-112">The type parameters must be Windows Runtime types, so primitive types are allowed as well as third-party runtime classes.</span></span>

<span data-ttu-id="40c40-113">Der Compiler hilft Ihnen mit einem „*WinRT-Typ erforderlich*”-Fehler, wenn Sie diese Einschränkung vergessen.</span><span class="sxs-lookup"><span data-stu-id="40c40-113">The compiler will help you with a "*must be WinRT type*" error if you forget this constraint.</span></span>

## <a name="winrtdelegatelt-tgt"></a><span data-ttu-id="40c40-114">winrt::delegate&lt;...T&gt;</span><span class="sxs-lookup"><span data-stu-id="40c40-114">winrt::delegate&lt;... T&gt;</span></span>
<span data-ttu-id="40c40-115">Wenn Sie ein Ereignis über einen C++-Typ auslösen wollen (im selben Projekt erstellt und genutzt), können Sie [**winrt::delegate**](/uwp/cpp-ref-for-winrt/delegate) von C++/WinRT für den Delegattyp Ihres Ereignisses nutzen.</span><span class="sxs-lookup"><span data-stu-id="40c40-115">If you want to raise an event from a C++ type (authored and consumed within the same project), then you can use C++/WinRT's [**winrt::delegate**](/uwp/cpp-ref-for-winrt/delegate) for your event's delegate type.</span></span> <span data-ttu-id="40c40-116">In diesem Fall müssen die Typ-Parameter des Delegats keine Windows-Runtime-Typen sein.</span><span class="sxs-lookup"><span data-stu-id="40c40-116">In that case, the delegate's type parameters needn't be Windows Runtime types.</span></span> <span data-ttu-id="40c40-117">Wenn Sie von einer C++/CX-Codebasis portieren, wo Ereignisse und Delegate intern verwendet werden (nicht über Binärdateien), hilft Ihnen **winrt::delegate** beim Replizieren dieses Musters in C++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="40c40-117">If you're porting from a C++/CX codebase where events and delegates are used internally (not across binaries), then **winrt::delegate** will help you to replicate that pattern in C++/WinRT.</span></span>

## <a name="create-a-windows-runtime-component-bankaccountwrc"></a><span data-ttu-id="40c40-118">Erstellen einer Komponente für Windows-Runtime (BankAccountWRC)</span><span class="sxs-lookup"><span data-stu-id="40c40-118">Create a Windows Runtime Component (BankAccountWRC)</span></span>
<span data-ttu-id="40c40-119">Erstellen Sie zunächst ein neues Projekt in Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="40c40-119">Begin by creating a new project in Microsoft Visual Studio.</span></span> <span data-ttu-id="40c40-120">Erstellen Sie ein **Visual C++ Windows-Runtime Component (C++/WinRT)** Projekt und nennen Sie es *BankAccountWRC* (für „Bankkonto-Komponente für Windows-Runtime”).</span><span class="sxs-lookup"><span data-stu-id="40c40-120">Create a **Visual C++ Windows Runtime Component (C++/WinRT)** project, and name it *BankAccountWRC* (for "bank account Windows Runtime Component").</span></span>

<span data-ttu-id="40c40-121">Das neu erstellte Projekt enthält eine Datei mit dem Namen `Class.idl`.</span><span class="sxs-lookup"><span data-stu-id="40c40-121">The newly-created project contains a file named `Class.idl`.</span></span> <span data-ttu-id="40c40-122">Benennen Sie diese Datei in `BankAccountWRC.idl` um, so dass beim Erstellen die Windows-Runtime-Metadaten-Datei Ihrer Komponente für die Komponente selbst benannt wird.</span><span class="sxs-lookup"><span data-stu-id="40c40-122">Rename that file `BankAccountWRC.idl` so that, when you build, your component's Windows Runtime metadata file is named for the component itself.</span></span> <span data-ttu-id="40c40-123">Definieren Sie in `BankAccountWRC.idl` Ihre Schnittstelle entsprechend dem folgenden Code.</span><span class="sxs-lookup"><span data-stu-id="40c40-123">In `BankAccountWRC.idl`, define your interface as in the listing below.</span></span>

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

<span data-ttu-id="40c40-124">Speichern Sie die Datei, und erstellen Sie das Projekt.</span><span class="sxs-lookup"><span data-stu-id="40c40-124">Save the file and build the project.</span></span> <span data-ttu-id="40c40-125">Die Erstellung funktioniert noch nicht.</span><span class="sxs-lookup"><span data-stu-id="40c40-125">The build won't succeed just yet.</span></span> <span data-ttu-id="40c40-126">Aber während des Buildprozesses wird das `midl.exe`-Tool ausgeführt, um die Windows-Runtime-Metadaten-Datei Ihrer Komponente zu erstellen (`\BankAccountWRC\Debug\BankAccountWRC\BankAccountWRC.winmd`).</span><span class="sxs-lookup"><span data-stu-id="40c40-126">But, during the build process, the `midl.exe` tool is run to create your component's Windows Runtime metadata file (which is `\BankAccountWRC\Debug\BankAccountWRC\BankAccountWRC.winmd`).</span></span> <span data-ttu-id="40c40-127">Dann wird das `cppwinrt.exe`-Tool ausgeführt (mit der Option `-component`), um Quelltextdateien zu erzeugen, die Sie bei der Erstellung Ihrer Komponente unterstützen.</span><span class="sxs-lookup"><span data-stu-id="40c40-127">Then, the `cppwinrt.exe` tool is run (with the `-component` option) to generate source code files to support you in authoring your component.</span></span> <span data-ttu-id="40c40-128">Diese Dateien enthalten Stubs, um mit der Implementierung der `BankAccount`-Laufzeitklasse zu beginnen, die Sie in Ihrer IDL deklariert haben.</span><span class="sxs-lookup"><span data-stu-id="40c40-128">These files include stubs to get you started implementing the `BankAccount` runtime class that you declared in your IDL.</span></span> <span data-ttu-id="40c40-129">Diese Stubs sind `\BankAccountWRC\BankAccountWRC\Generated Files\sources\BankAccount.h` und `BankAccount.cpp`.</span><span class="sxs-lookup"><span data-stu-id="40c40-129">Those stubs are `\BankAccountWRC\BankAccountWRC\Generated Files\sources\BankAccount.h` and `BankAccount.cpp`.</span></span>

<span data-ttu-id="40c40-130">Kopieren Sie die Stub-Dateien `BankAccount.h` und `BankAccount.cpp` von `\BankAccountWRC\BankAccountWRC\Generated Files\sources\` in den Projektordner `\BankAccountWRC\BankAccountWRC\`.</span><span class="sxs-lookup"><span data-stu-id="40c40-130">Copy the stub files `BankAccount.h` and `BankAccount.cpp` from `\BankAccountWRC\BankAccountWRC\Generated Files\sources\` into the project folder, which is `\BankAccountWRC\BankAccountWRC\`.</span></span> <span data-ttu-id="40c40-131">Stellen Sie im **Projektmappen-Explorer** sicher, dass **Alle Dateien anzeigen** aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="40c40-131">In **Solution Explorer**, make sure **Show All Files** is toggled on.</span></span> <span data-ttu-id="40c40-132">Klicken Sie mit der rechten Maustaste auf die kopierten Stub-Dateien und klicken Sie auf **In Projekt aufnehmen**.</span><span class="sxs-lookup"><span data-stu-id="40c40-132">Right-click the stub files that you copied, and click **Include In Project**.</span></span> <span data-ttu-id="40c40-133">Klicken Sie außerdem mit der rechten Maustaste auf `Class.h` und `Class.cpp`, und klicken Sie auf **Aus Projekt ausschließen**.</span><span class="sxs-lookup"><span data-stu-id="40c40-133">Also, right-click `Class.h` and `Class.cpp`, and click **Exclude From Project**.</span></span>

<span data-ttu-id="40c40-134">Nun öffnen wir `BankAccount.h` und `BankAccount.cpp` und implementieren unsere Laufzeitklasse.</span><span class="sxs-lookup"><span data-stu-id="40c40-134">Now, let's open `BankAccount.h` and `BankAccount.cpp` and implement our runtime class.</span></span> <span data-ttu-id="40c40-135">Fügen Sie in `BankAccount.h` zwei private Mitglieder zur Implementierung von BankAccount hinzu (*nicht* zur Factory-Implementierung).</span><span class="sxs-lookup"><span data-stu-id="40c40-135">In `BankAccount.h`, add two private members to the implementation (*not* the factory implementation) of BankAccount.</span></span>

```cppwinrt
// BankAccount.h
...
namespace winrt::BankAccountWRC::implementation
{
    struct BankAccount : BankAccountT<BankAccount>
    {
        ...

    private:
        winrt::event<Windows::Foundation::EventHandler<float>> accountIsInDebitEvent;
        float balance{ 0.f };
    };
}
...
```

<span data-ttu-id="40c40-136">Implementieren Sie in `BankAccount.cpp` die Funktionen wie im folgenden Codebeispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="40c40-136">In `BankAccount.cpp`, implement the functions as shown in the code example below.</span></span> <span data-ttu-id="40c40-137">In C++/WinRT wird ein IDL-deklariertes Ereignis als ein Set überladener Funktionen implementiert (ähnlich wie eine Eigenschaft als ein Paar von überladenen Get- und Set-Funktionen implementiert wird).</span><span class="sxs-lookup"><span data-stu-id="40c40-137">In C++/WinRT, an IDL-declared event is implemented as a set of overloaded functions (similar to the way a property is implemented as a pair of overloaded get and set functions).</span></span> <span data-ttu-id="40c40-138">Eine Überladung übernimmt einen zu registrierenden Delegaten und gibt einen Token zurück.</span><span class="sxs-lookup"><span data-stu-id="40c40-138">One overload takes a delegate to be registered, and returns a token.</span></span> <span data-ttu-id="40c40-139">Die andere übernimmt einen Token und widerruft die Registrierung des zugeordneten Delegats.</span><span class="sxs-lookup"><span data-stu-id="40c40-139">The other takes a token, and revokes the registration of the associated delegate.</span></span>

```cppwinrt
// BankAccount.cpp
...
namespace winrt::BankAccountWRC::implementation
{
    event_token BankAccount::AccountIsInDebit(Windows::Foundation::EventHandler<float> const& handler)
    {
        return accountIsInDebitEvent.add(handler);
    }

    void BankAccount::AccountIsInDebit(event_token const& token)
    {
        accountIsInDebitEvent.remove(token);
    }

    void BankAccount::AdjustBalance(float value)
    {
        balance += value;
        if (balance < 0.f) accountIsInDebitEvent(*this, balance);
    }
}
```

<span data-ttu-id="40c40-140">Sie müssen nicht die Überladung für den Ereignis-Revoker implementieren (weitere Informationen siehe [Einen registrierten Delegaten widerrufen](handle-events.md#revoke-a-registered-delegate))– dies übernimmt die C++/WinRT-Projektion für Sie.</span><span class="sxs-lookup"><span data-stu-id="40c40-140">You don't need to implement the overload for the event revoker (for details, see [Revoke a registered delegate](handle-events.md#revoke-a-registered-delegate))&mdash;that's taken care of for you by the C++/WinRT projection.</span></span> <span data-ttu-id="40c40-141">Die anderen Überladungen sind nicht in die Projektion integriert, um Ihnen die Flexibilität zu geben, sie für Ihr Szenario optimal zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="40c40-141">The other overloads are not baked into the projection, in order to give you the flexibility to implement them optimally for your scenario.</span></span> <span data-ttu-id="40c40-142">Ein derartiger Aufruf von [**event::add**](/uwp/cpp-ref-for-winrt/event#eventadd-function) und [**event::remove**](/uwp/cpp-ref-for-winrt/event#eventremove-function) ist eine effiziente und parallele/threadsichere Standardmethode.</span><span class="sxs-lookup"><span data-stu-id="40c40-142">Calling [**event::add**](/uwp/cpp-ref-for-winrt/event#eventadd-function) and [**event::remove**](/uwp/cpp-ref-for-winrt/event#eventremove-function) like this is an efficient and concurrency/thread-safe default.</span></span> <span data-ttu-id="40c40-143">Wenn Sie jedoch über eine große Anzahl von Ereignissen verfügen, möchten Sie möglicherweise nicht für jedes ein Ereignisfeld, sondern vielmehr eine Implementierung mit geringer Dichte.</span><span class="sxs-lookup"><span data-stu-id="40c40-143">But if you have a very large number of events, then you may not want an event field for each, but rather opt for some kind of sparse implementation instead.</span></span>

<span data-ttu-id="40c40-144">Sie sehen oben, dass die Implementierung der Funktion **AdjustBalance** das Ereignis **AccountIsInDebit** auslöst, wenn der Saldo negativ wird.</span><span class="sxs-lookup"><span data-stu-id="40c40-144">You can also see above that the implementation of the **AdjustBalance** function raises the **AccountIsInDebit** event if the balance goes negative.</span></span>

<span data-ttu-id="40c40-145">Wenn Sie irgendwelche Warnungen an der Erstellung hindern, dann setzen Sie die Projekteigenschaft** C/C++** > **Allgemein** > **Warnungen als Fehler behandeln** auf **Nein (/WX-)**, und erstellen Sie das Projekt neu.</span><span class="sxs-lookup"><span data-stu-id="40c40-145">If any warnings prevent you from building, then set the project property **C/C++** > **General** > **Treat Warnings As Errors** to **No (/WX-)**, and build the project again.</span></span>

## <a name="create-a-core-app-bankaccountcoreapp-to-test-the-windows-runtime-component"></a><span data-ttu-id="40c40-146">Erstellen einer Core App (BankAccountCoreApp) zum Testen der Komponente für Windows-Runtime</span><span class="sxs-lookup"><span data-stu-id="40c40-146">Create a Core App (BankAccountCoreApp) to test the Windows Runtime Component</span></span>
<span data-ttu-id="40c40-147">Erstellen Sie nun ein neues Projekt (entweder in Ihrer `BankAccountWRC`-Lösung oder in einer neuen).</span><span class="sxs-lookup"><span data-stu-id="40c40-147">Now create a new project (either in your `BankAccountWRC` solution, or in a new one).</span></span> <span data-ttu-id="40c40-148">Erstellen Sie ein **Visual C++ Core App (C++/WinRT)**-Projekt, und nennen Sie es *BankAccountCoreApp*.</span><span class="sxs-lookup"><span data-stu-id="40c40-148">Create a **Visual C++ Core App (C++/WinRT)** project, and name it *BankAccountCoreApp*.</span></span>

<span data-ttu-id="40c40-149">Fügen Sie einen Verweis hinzu, und navigieren Sie zu `\BankAccountWRC\Debug\BankAccountWRC\BankAccountWRC.winmd` (oder fügen Sie einen Projektverweis hinzu, wenn sich die beiden Projekte in der gleichen Projektmappe befinden).</span><span class="sxs-lookup"><span data-stu-id="40c40-149">Add a reference, and browse to `\BankAccountWRC\Debug\BankAccountWRC\BankAccountWRC.winmd` (or add a project reference, if the two projects are in the same solution).</span></span> <span data-ttu-id="40c40-150">Klicken Sie auf **Hinzufügen** und dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="40c40-150">Click **Add**, and then **OK**.</span></span> <span data-ttu-id="40c40-151">Erstellen Sie jetzt BankAccountCoreApp.</span><span class="sxs-lookup"><span data-stu-id="40c40-151">Now build BankAccountCoreApp.</span></span> <span data-ttu-id="40c40-152">Wenn ein Fehler anzeigt, dass die Payload-Datei `readme.txt` nicht existiert, dann schließen Sie diese Datei aus dem „Komponente für Windows-Runtime“-Projekt aus, erstellen Sie sie neu, und erstellen Sie dann BankAccountCoreApp neu.</span><span class="sxs-lookup"><span data-stu-id="40c40-152">If you see an error that the payload file `readme.txt` doesn't exist, then exclude that file from the Windows Runtime Component project, rebuild it, then rebuild BankAccountCoreApp.</span></span>

<span data-ttu-id="40c40-153">Während des Buildprozesses wird das `cppwinrt.exe`-Tool ausgeführt, um die referenzierte `.winmd`-Datei in Quellcodedateien zu verarbeiten, die projizierte Typen enthalten, um Sie bei der Verwendung Ihrer Komponente zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="40c40-153">During the build process, the `cppwinrt.exe` tool is run to process the referenced `.winmd` file into source code files containing projected types to support you in consuming your component.</span></span> <span data-ttu-id="40c40-154">Der Header für die projizierten Typen für die Laufzeitklassen Ihrer Komponente (mit dem Namen `BankAccountWRC.h`) wird im Ordner `\BankAccountCoreApp\BankAccountCoreApp\Generated Files\winrt\` generiert.</span><span class="sxs-lookup"><span data-stu-id="40c40-154">The header for the projected types for your component's runtime classes&mdash;named `BankAccountWRC.h`&mdash;is generated into the folder `\BankAccountCoreApp\BankAccountCoreApp\Generated Files\winrt\`.</span></span>

<span data-ttu-id="40c40-155">Fügen Sie diesen Header in `App.cpp` ein.</span><span class="sxs-lookup"><span data-stu-id="40c40-155">Include that header in `App.cpp`.</span></span>

```cppwinrt
#include <winrt/BankAccountWRC.h>
```

<span data-ttu-id="40c40-156">Fügen Sie in `App.cpp` ebenfalls den folgenden Code ein, um ein BankAccount zu instanziieren (unter Verwendung des Standardkonstruktors des projizierten Typs), registrieren Sie einen Ereignis-Handler und sorgen Sie dann dafür, dass das Konto ins Minus geht.</span><span class="sxs-lookup"><span data-stu-id="40c40-156">Also in `App.cpp`, add the following code to instantiate a BankAccount (using the projected type's default constructor), register an event handler, and then cause the account to go into debit.</span></span>

```cppwinrt
struct App : implements<App, IFrameworkViewSource, IFrameworkView>
{
    BankAccountWRC::BankAccount bankAccount;
    event_token eventToken;
    ...
    
    void Initialize(CoreApplicationView const &)
    {
        eventToken = bankAccount.AccountIsInDebit([](const auto &, float balance)
        {
            assert(balance < 0.f);
        });
    }
    ...

    void Uninitialize()
    {
        bankAccount.AccountIsInDebit(eventToken);
    }
    ...

    void OnPointerPressed(IInspectable const &, PointerEventArgs const & args)
    {
        bankAccount.AdjustBalance(-1.f);
        ...
    }
    ...
};
```

<span data-ttu-id="40c40-157">Jedes Mal, wenn Sie auf das Fenster klicken, ziehen Sie 1 vom Kontostand ab.</span><span class="sxs-lookup"><span data-stu-id="40c40-157">Each time you click the window, you subtract 1 from the bank account's balance.</span></span> <span data-ttu-id="40c40-158">Um zu demonstrieren, dass das Ereignis wie erwartet ausgelöst wird, setzen Sie einen Haltepunkt in den Lambda-Ausdruck, starten Sie die App und klicken Sie in das Fenster.</span><span class="sxs-lookup"><span data-stu-id="40c40-158">To demonstrate that the event is being raised as expected, put a breakpoint inside the lambda expression, run the app, and click inside the window.</span></span>

## <a name="related-topics"></a><span data-ttu-id="40c40-159">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="40c40-159">Related topics</span></span>
* [<span data-ttu-id="40c40-160">Erstellen von APIs mit C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="40c40-160">Author APIs with C++/WinRT</span></span>](author-apis.md)
* [<span data-ttu-id="40c40-161">Verwenden von APIs mit C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="40c40-161">Consume APIs with C++/WinRT</span></span>](consume-apis.md)
* [<span data-ttu-id="40c40-162">Verarbeiten von Ereignissen über Delegaten in C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="40c40-162">Handle events by using delegates in C++/WinRT</span></span>](handle-events.md)
