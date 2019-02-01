---
description: Dieses Thema zeigt, wie man eine Komponente für Windows-Runtime erstellt, die eine Laufzeitklasse enthält, die Ereignisse auslöst. Es zeigt außerdem eine App, die die Komponente nutzt und die Ereignisse verarbeitet.
title: Erstellen von Ereignissen mit C++/WinRT
ms.date: 07/18/2018
ms.topic: article
keywords: windows 10, uwp, standard, c++, cpp, winrt, projektion, erstellen, ereignis
ms.localizationpriority: medium
ms.openlocfilehash: ace1c276b878d07f5750483740dfe90ed8cb6211
ms.sourcegitcommit: 2d2483819957619b6de21b678caf887f3b1342af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2019
ms.locfileid: "9042362"
---
# <a name="author-events-in-cwinrt"></a><span data-ttu-id="33cb6-105">Erstellen von Ereignissen mit C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="33cb6-105">Author events in C++/WinRT</span></span>

<span data-ttu-id="33cb6-106">Dieses Thema zeigt, wie man eine Komponente für Windows-Runtime erstellt, die eine Laufzeitklasse für ein Bankkonto enthält, die ein Ereignis auslöst, wenn sein Saldo ins Minus gerät.</span><span class="sxs-lookup"><span data-stu-id="33cb6-106">This topic demonstrates how to author a Windows Runtime Component containing a runtime class representing a bank account, which raises an event when its balance goes into debit.</span></span> <span data-ttu-id="33cb6-107">Es demonstriert außerdem eine Core App, die die Bankkonto-Laufzeitklasse nutzt, eine Funktion zur Anpassung des Saldos aufruft und alle daraus resultierenden Ereignisse verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="33cb6-107">It also demonstrates a Core App that consumes the bank account runtime class, calls a function to adjust the balance, and handles any events that result.</span></span>

> [!NOTE]
> <span data-ttu-id="33cb6-108">Informationen zur Installation und Verwendung der [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) finden Sie in Visual Studio Extension (VSIX) (die projektvorlagenunterstützung bereitstellt) [Visual Studio-Unterstützung für C++ / WinRT](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-xaml-the-vsix-extension-and-the-nuget-package).</span><span class="sxs-lookup"><span data-stu-id="33cb6-108">For info about installing and using the [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) Visual Studio Extension (VSIX) (which provides project template support) see [Visual Studio support for C++/WinRT](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-xaml-the-vsix-extension-and-the-nuget-package).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="33cb6-109">Wichtige Konzepte und Begriffe, die Ihr Verständnis für die Verwendung von Laufzeitklassen mit C++/WinRT unterstützen, finden Sie unter [Verwenden von APIs mit C++/WinRT](consume-apis.md) und [Erstellen von APIs mit C++/WinRT](author-apis.md).</span><span class="sxs-lookup"><span data-stu-id="33cb6-109">For essential concepts and terms that support your understanding of how to consume and author runtime classes with C++/WinRT, see [Consume APIs with C++/WinRT](consume-apis.md) and [Author APIs with C++/WinRT](author-apis.md).</span></span>

## <a name="create-a-windows-runtime-component-bankaccountwrc"></a><span data-ttu-id="33cb6-110">Erstellen einer Komponente für Windows-Runtime (BankAccountWRC)</span><span class="sxs-lookup"><span data-stu-id="33cb6-110">Create a Windows Runtime Component (BankAccountWRC)</span></span>

<span data-ttu-id="33cb6-111">Erstellen Sie zunächst ein neues Projekt in Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="33cb6-111">Begin by creating a new project in Microsoft Visual Studio.</span></span> <span data-ttu-id="33cb6-112">Erstellen Sie eine **Visual C++** > **Windows Universal** > **Komponente für Windows-Runtime (C++ / WinRT)** Projekt und nennen Sie es *BankAccountWRC* (für "Bankkonto Komponente für Windows-Runtime").</span><span class="sxs-lookup"><span data-stu-id="33cb6-112">Create a **Visual C++** > **Windows Universal** > **Windows Runtime Component (C++/WinRT)** project, and name it *BankAccountWRC* (for "bank account Windows Runtime Component").</span></span>

<span data-ttu-id="33cb6-113">Das neu erstellte Projekt enthält eine Datei mit dem Namen `Class.idl`.</span><span class="sxs-lookup"><span data-stu-id="33cb6-113">The newly-created project contains a file named `Class.idl`.</span></span> <span data-ttu-id="33cb6-114">Benennen Sie diese Datei `BankAccount.idl` (Umbenennen der `.idl` Datei wird automatisch der abhängigen `.h` und `.cpp` Dateien zu).</span><span class="sxs-lookup"><span data-stu-id="33cb6-114">Rename that file `BankAccount.idl` (renaming the `.idl` file automatically renames the dependent `.h` and `.cpp` files, too).</span></span> <span data-ttu-id="33cb6-115">Ersetzen Sie den Inhalt des `BankAccount.idl` mit den folgenden Eintrag.</span><span class="sxs-lookup"><span data-stu-id="33cb6-115">Replace the contents of `BankAccount.idl` with the listing below.</span></span>

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

<span data-ttu-id="33cb6-116">Speichern Sie die Datei.</span><span class="sxs-lookup"><span data-stu-id="33cb6-116">Save the file.</span></span> <span data-ttu-id="33cb6-117">Erstellen Sie das Projekt wird nicht bis zum Abschluss im Moment, aber nun erstellen ist hilfreich, etwas zu tun, da er die Quellcodedateien generiert, in denen Sie die Laufzeitklasse **BankAccount** implementieren.</span><span class="sxs-lookup"><span data-stu-id="33cb6-117">The project won't build to completion at the moment, but building now is a useful thing to do because it generates the source code files in which you'll implement the **BankAccount** runtime class.</span></span> <span data-ttu-id="33cb6-118">So einfach, und erstellen Sie jetzt (die Buildfehler zu erwarten, dass in dieser Phase finden Sie unter müssen mit `Class.h` und `Class.g.h` nicht gefunden wird).</span><span class="sxs-lookup"><span data-stu-id="33cb6-118">So go ahead and build now (the build errors you can expect to see at this stage have to do with `Class.h` and `Class.g.h` not being found).</span></span> <span data-ttu-id="33cb6-119">Während des Buildprozesses die `midl.exe` -Tool ausgeführt, um die Datei Ihrer Komponente Windows-Runtime-Metadaten zu erstellen (also `\BankAccountWRC\Debug\BankAccountWRC\BankAccountWRC.winmd`).</span><span class="sxs-lookup"><span data-stu-id="33cb6-119">During the build process, the `midl.exe` tool is run to create your component's Windows Runtime metadata file (which is `\BankAccountWRC\Debug\BankAccountWRC\BankAccountWRC.winmd`).</span></span> <span data-ttu-id="33cb6-120">Dann wird das `cppwinrt.exe`-Tool ausgeführt (mit der Option `-component`), um Quelltextdateien zu erzeugen, die Sie bei der Erstellung Ihrer Komponente unterstützen.</span><span class="sxs-lookup"><span data-stu-id="33cb6-120">Then, the `cppwinrt.exe` tool is run (with the `-component` option) to generate source code files to support you in authoring your component.</span></span> <span data-ttu-id="33cb6-121">Diese Dateien enthalten Stubs, um die erste Schritte zum Implementieren der **BankAccount** -Runtime-Klasse, die Sie in Ihrer IDL deklariert haben.</span><span class="sxs-lookup"><span data-stu-id="33cb6-121">These files include stubs to get you started implementing the **BankAccount** runtime class that you declared in your IDL.</span></span> <span data-ttu-id="33cb6-122">Diese Stubs sind `\BankAccountWRC\BankAccountWRC\Generated Files\sources\BankAccount.h` und `BankAccount.cpp`.</span><span class="sxs-lookup"><span data-stu-id="33cb6-122">Those stubs are `\BankAccountWRC\BankAccountWRC\Generated Files\sources\BankAccount.h` and `BankAccount.cpp`.</span></span>

<span data-ttu-id="33cb6-123">Mit der rechten Maustaste in des Projektknoten, und klicken Sie auf **Ordner im Datei-Explorer öffnen**.</span><span class="sxs-lookup"><span data-stu-id="33cb6-123">Right-click the project node and click **Open Folder in File Explorer**.</span></span> <span data-ttu-id="33cb6-124">Dadurch wird den Projektordner im Datei-Explorer geöffnet.</span><span class="sxs-lookup"><span data-stu-id="33cb6-124">This opens the project folder in File Explorer.</span></span> <span data-ttu-id="33cb6-125">Kopieren Sie die Stub-Dateien, `BankAccount.h` und `BankAccount.cpp` aus dem Ordner `\BankAccountWRC\BankAccountWRC\Generated Files\sources\` und in den Ordner, die Ihre Projektdateien enthält, ist die `\BankAccountWRC\BankAccountWRC\`, und Ersetzen Sie die Dateien in das Ziel.</span><span class="sxs-lookup"><span data-stu-id="33cb6-125">There, copy the stub files `BankAccount.h` and `BankAccount.cpp` from the folder `\BankAccountWRC\BankAccountWRC\Generated Files\sources\` and into the folder that contains your project files, which is `\BankAccountWRC\BankAccountWRC\`, and replace the files in the destination.</span></span> <span data-ttu-id="33cb6-126">Nun öffnen wir `BankAccount.h` und `BankAccount.cpp` und implementieren unsere Laufzeitklasse.</span><span class="sxs-lookup"><span data-stu-id="33cb6-126">Now, let's open `BankAccount.h` and `BankAccount.cpp` and implement our runtime class.</span></span> <span data-ttu-id="33cb6-127">Fügen Sie in `BankAccount.h` zwei private Mitglieder zur Implementierung von BankAccount hinzu (*nicht* zur Factory-Implementierung).</span><span class="sxs-lookup"><span data-stu-id="33cb6-127">In `BankAccount.h`, add two private members to the implementation (*not* the factory implementation) of BankAccount.</span></span>

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

<span data-ttu-id="33cb6-128">Wie Sie oben sehen können, wird das Ereignis hinsichtlich der [**winrt::event**](/uwp/cpp-ref-for-winrt/event) Struktur-Vorlage eines bestimmten Delegattyps als Parameter implementiert.</span><span class="sxs-lookup"><span data-stu-id="33cb6-128">As you can see above, the event is implemented in terms of the [**winrt::event**](/uwp/cpp-ref-for-winrt/event) struct template, parameterized by a particular delegate type.</span></span>

<span data-ttu-id="33cb6-129">Implementieren Sie in `BankAccount.cpp` die Funktionen wie im folgenden Codebeispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="33cb6-129">In `BankAccount.cpp`, implement the functions as shown in the code example below.</span></span> <span data-ttu-id="33cb6-130">In C++/WinRT wird ein IDL-deklariertes Ereignis als ein Set überladener Funktionen implementiert (ähnlich wie eine Eigenschaft als ein Paar von überladenen Get- und Set-Funktionen implementiert wird).</span><span class="sxs-lookup"><span data-stu-id="33cb6-130">In C++/WinRT, an IDL-declared event is implemented as a set of overloaded functions (similar to the way a property is implemented as a pair of overloaded get and set functions).</span></span> <span data-ttu-id="33cb6-131">Eine Überladung übernimmt einen zu registrierenden Delegaten und gibt einen Token zurück.</span><span class="sxs-lookup"><span data-stu-id="33cb6-131">One overload takes a delegate to be registered, and returns a token.</span></span> <span data-ttu-id="33cb6-132">Die andere übernimmt einen Token und widerruft die Registrierung des zugeordneten Delegats.</span><span class="sxs-lookup"><span data-stu-id="33cb6-132">The other takes a token, and revokes the registration of the associated delegate.</span></span>

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

<span data-ttu-id="33cb6-133">Sie müssen nicht die Überladung für den Ereignis-Revoker implementieren (weitere Informationen siehe [Einen registrierten Delegaten widerrufen](handle-events.md#revoke-a-registered-delegate))– dies übernimmt die C++/WinRT-Projektion für Sie.</span><span class="sxs-lookup"><span data-stu-id="33cb6-133">You don't need to implement the overload for the event revoker (for details, see [Revoke a registered delegate](handle-events.md#revoke-a-registered-delegate))&mdash;that's taken care of for you by the C++/WinRT projection.</span></span> <span data-ttu-id="33cb6-134">Die anderen Überladungen sind nicht in die Projektion integriert, um Ihnen die Flexibilität zu geben, sie für Ihr Szenario optimal zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="33cb6-134">The other overloads are not baked into the projection, in order to give you the flexibility to implement them optimally for your scenario.</span></span> <span data-ttu-id="33cb6-135">Ein derartiger Aufruf von [**event::add**](/uwp/cpp-ref-for-winrt/event#eventadd-function) und [**event::remove**](/uwp/cpp-ref-for-winrt/event#eventremove-function) ist eine effiziente und parallele/threadsichere Standardmethode.</span><span class="sxs-lookup"><span data-stu-id="33cb6-135">Calling [**event::add**](/uwp/cpp-ref-for-winrt/event#eventadd-function) and [**event::remove**](/uwp/cpp-ref-for-winrt/event#eventremove-function) like this is an efficient and concurrency/thread-safe default.</span></span> <span data-ttu-id="33cb6-136">Wenn Sie jedoch über eine große Anzahl von Ereignissen verfügen, möchten Sie möglicherweise nicht für jedes ein Ereignisfeld, sondern vielmehr eine Implementierung mit geringer Dichte.</span><span class="sxs-lookup"><span data-stu-id="33cb6-136">But if you have a very large number of events, then you may not want an event field for each, but rather opt for some kind of sparse implementation instead.</span></span>

<span data-ttu-id="33cb6-137">Sie sehen oben, dass die Implementierung der Funktion **AdjustBalance** das Ereignis **AccountIsInDebit** auslöst, wenn der Saldo negativ wird.</span><span class="sxs-lookup"><span data-stu-id="33cb6-137">You can also see above that the implementation of the **AdjustBalance** function raises the **AccountIsInDebit** event if the balance goes negative.</span></span>

<span data-ttu-id="33cb6-138">Wenn alle Warnungen der Erstellung hindern, oder Sie anschließend beheben, bevor sie die Projekteigenschaft **C/C++-** > **Allgemeine** > **Warnungen als Fehler behandeln** **Nein (/ WX-)**, und erstellen Sie das Projekt erneut.</span><span class="sxs-lookup"><span data-stu-id="33cb6-138">If any warnings prevent you from building, then either resolve them or set the project property **C/C++** > **General** > **Treat Warnings As Errors** to **No (/WX-)**, and build the project again.</span></span>

## <a name="create-a-core-app-bankaccountcoreapp-to-test-the-windows-runtime-component"></a><span data-ttu-id="33cb6-139">Erstellen einer Core App (BankAccountCoreApp) zum Testen der Komponente für Windows-Runtime</span><span class="sxs-lookup"><span data-stu-id="33cb6-139">Create a Core App (BankAccountCoreApp) to test the Windows Runtime Component</span></span>

<span data-ttu-id="33cb6-140">Erstellen Sie nun ein neues Projekt (entweder in Ihrer `BankAccountWRC`-Lösung oder in einer neuen).</span><span class="sxs-lookup"><span data-stu-id="33cb6-140">Now create a new project (either in your `BankAccountWRC` solution, or in a new one).</span></span> <span data-ttu-id="33cb6-141">Erstellen Sie eine **Visual C++** > **Windows Universal** > **Core App (C++ / WinRT)** Projekt und nennen Sie es *BankAccountCoreApp*.</span><span class="sxs-lookup"><span data-stu-id="33cb6-141">Create a **Visual C++** > **Windows Universal** > **Core App (C++/WinRT)** project, and name it *BankAccountCoreApp*.</span></span>

<span data-ttu-id="33cb6-142">Fügen Sie einen Verweis hinzu, und navigieren Sie zu `\BankAccountWRC\Debug\BankAccountWRC\BankAccountWRC.winmd` (oder fügen Sie einen Projekt-zu-Projekt-Verweis hinzu, wenn die beiden Projekte in der gleichen Projektmappe befinden).</span><span class="sxs-lookup"><span data-stu-id="33cb6-142">Add a reference, and browse to `\BankAccountWRC\Debug\BankAccountWRC\BankAccountWRC.winmd` (or add a project-to-project reference, if the two projects are in the same solution).</span></span> <span data-ttu-id="33cb6-143">Klicken Sie auf **Hinzufügen** und dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="33cb6-143">Click **Add**, and then **OK**.</span></span> <span data-ttu-id="33cb6-144">Erstellen Sie jetzt BankAccountCoreApp.</span><span class="sxs-lookup"><span data-stu-id="33cb6-144">Now build BankAccountCoreApp.</span></span> <span data-ttu-id="33cb6-145">Im unwahrscheinlichen Fall, dass ein Fehler angezeigt, die die Payload-Datei `readme.txt` nicht existiert, schließen Sie diese Datei aus dem Komponente für Windows-Runtime-Projekt, erstellen Sie Sie neu, und erstellen Sie bankaccountcoreapp neu.</span><span class="sxs-lookup"><span data-stu-id="33cb6-145">In the unlikely event that you see an error that the payload file `readme.txt` doesn't exist, exclude that file from the Windows Runtime Component project, rebuild it, then rebuild BankAccountCoreApp.</span></span>

<span data-ttu-id="33cb6-146">Während des Buildprozesses wird das `cppwinrt.exe`-Tool ausgeführt, um die referenzierte `.winmd`-Datei in Quellcodedateien zu verarbeiten, die projizierte Typen enthalten, um Sie bei der Verwendung Ihrer Komponente zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="33cb6-146">During the build process, the `cppwinrt.exe` tool is run to process the referenced `.winmd` file into source code files containing projected types to support you in consuming your component.</span></span> <span data-ttu-id="33cb6-147">Der Header für die projizierten Typen für die Laufzeitklassen Ihrer Komponente (mit dem Namen `BankAccountWRC.h`) wird im Ordner `\BankAccountCoreApp\BankAccountCoreApp\Generated Files\winrt\` generiert.</span><span class="sxs-lookup"><span data-stu-id="33cb6-147">The header for the projected types for your component's runtime classes&mdash;named `BankAccountWRC.h`&mdash;is generated into the folder `\BankAccountCoreApp\BankAccountCoreApp\Generated Files\winrt\`.</span></span>

<span data-ttu-id="33cb6-148">Fügen Sie diesen Header in `App.cpp` ein.</span><span class="sxs-lookup"><span data-stu-id="33cb6-148">Include that header in `App.cpp`.</span></span>

```cppwinrt
#include <winrt/BankAccountWRC.h>
```

<span data-ttu-id="33cb6-149">Fügen Sie in `App.cpp` ebenfalls den folgenden Code ein, um ein BankAccount zu instanziieren (unter Verwendung des Standardkonstruktors des projizierten Typs), registrieren Sie einen Ereignis-Handler und sorgen Sie dann dafür, dass das Konto ins Minus geht.</span><span class="sxs-lookup"><span data-stu-id="33cb6-149">Also in `App.cpp`, add the following code to instantiate a BankAccount (using the projected type's default constructor), register an event handler, and then cause the account to go into debit.</span></span>

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

<span data-ttu-id="33cb6-150">Jedes Mal, wenn Sie auf das Fenster klicken, ziehen Sie 1 vom Kontostand ab.</span><span class="sxs-lookup"><span data-stu-id="33cb6-150">Each time you click the window, you subtract 1 from the bank account's balance.</span></span> <span data-ttu-id="33cb6-151">Um zu zeigen, dass das Ereignis wie erwartet ausgelöst wird, setzen Sie einen Haltepunkt in der Lambda-Ausdruck, der das Ereignis **AccountIsInDebit** verarbeitet, führen Sie die app, und klicken Sie in das Fenster.</span><span class="sxs-lookup"><span data-stu-id="33cb6-151">To demonstrate that the event is being raised as expected, put a breakpoint inside the lambda expression that's handling the **AccountIsInDebit** event, run the app, and click inside the window.</span></span>

## <a name="parameterized-delegates-and-simple-signals-across-an-abi"></a><span data-ttu-id="33cb6-152">Parametrisierten Delegaten und einfache Signale über eine ABI</span><span class="sxs-lookup"><span data-stu-id="33cb6-152">Parameterized delegates, and simple signals, across an ABI</span></span>

<span data-ttu-id="33cb6-153">Wenn das Ereignis über eine Application binary Interface (ABI) verfügbar sein muss&mdash;z. B. zwischen einer Komponente und verwendenden dargestellte&mdash;und dann das Ereignis ein Windows-Runtime-Delegattyps verwenden muss.</span><span class="sxs-lookup"><span data-stu-id="33cb6-153">If your event must be accessible across an application binary interface (ABI)&mdash;such as between a component and its consuming application&mdash;then your event must use a Windows Runtime delegate type.</span></span> <span data-ttu-id="33cb6-154">Im obigen Beispiel verwendet den [**Windows::Foundation::EventHandler\<T\>**](/uwp/api/windows.foundation.eventhandler) Windows-Runtime-Delegattyp.</span><span class="sxs-lookup"><span data-stu-id="33cb6-154">The example above uses the [**Windows::Foundation::EventHandler\<T\>**](/uwp/api/windows.foundation.eventhandler) Windows Runtime delegate type.</span></span> <span data-ttu-id="33cb6-155">[**TypedEventHandler\<TSender**](/uwp/api/windows.foundation.eventhandler) ist TResult\> ein weiteres Beispiel für ein Windows-Runtime-Delegattyp.</span><span class="sxs-lookup"><span data-stu-id="33cb6-155">[**TypedEventHandler\<TSender, TResult\>**](/uwp/api/windows.foundation.eventhandler) is another example of a Windows Runtime delegate type.</span></span>

<span data-ttu-id="33cb6-156">Die Typparameter für diese zwei Delegattypen müssen die ABI überschreiten, damit die Typparameter zu Windows-Runtime-Typen sein müssen.</span><span class="sxs-lookup"><span data-stu-id="33cb6-156">The type parameters for those two delegate types have to cross the ABI, so the type parameters must be Windows Runtime types, too.</span></span> <span data-ttu-id="33cb6-157">Dazu wird erst- und Drittanbieter-Laufzeitklassen sowie primitive Typen wie z. B. Zahlen und Zeichenfolgen.</span><span class="sxs-lookup"><span data-stu-id="33cb6-157">That includes first- and third-party runtime classes, as well as primitive types such as numbers and strings.</span></span> <span data-ttu-id="33cb6-158">Der Compiler hilft Ihnen mit dem Fehler "*WinRT-Typ*", wenn Sie diese Einschränkung vergessen.</span><span class="sxs-lookup"><span data-stu-id="33cb6-158">The compiler helps you with a "*must be WinRT type*" error if you forget that constraint.</span></span>

<span data-ttu-id="33cb6-159">Wenn Sie keine Parameter oder Argumente mit dem Ereignis übergeben müssen, können Sie Ihre eigene einfache Windows-Runtime-Delegattyp definieren.</span><span class="sxs-lookup"><span data-stu-id="33cb6-159">If you don't need to pass any parameters or arguments with your event, then you can define your own simple Windows Runtime delegate type.</span></span> <span data-ttu-id="33cb6-160">Das folgende Beispiel zeigt eine einfachere Version der Laufzeitklasse **BankAccount** .</span><span class="sxs-lookup"><span data-stu-id="33cb6-160">The example below shows a simpler version of the **BankAccount** runtime class.</span></span> <span data-ttu-id="33cb6-161">Delegattyp **SignalDelegate** deklariert, und klicken Sie dann es verwendet, um ein Ereignis Signal-Typ anstelle eines Ereignisses mit einem Parameter auszulösen.</span><span class="sxs-lookup"><span data-stu-id="33cb6-161">It declares a delegate type named **SignalDelegate** and then it uses that to raise a signal-type event instead of an event with a parameter.</span></span>

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

## <a name="parameterized-delegates-simple-signals-and-callbacks-within-a-project"></a><span data-ttu-id="33cb6-162">Parametrisierten Delegaten, einfachen Signale und Rückrufe innerhalb eines Projekts</span><span class="sxs-lookup"><span data-stu-id="33cb6-162">Parameterized delegates, simple signals, and callbacks within a project</span></span>

<span data-ttu-id="33cb6-163">Wenn das Ereignis nur intern verwendet wird, in Ihrer C++ / WinRT projizieren (nicht über Binärdateien), und Sie weiterhin die strukturvorlage [**winrt::event**](/uwp/cpp-ref-for-winrt/event) verwenden, aber Sie parametrisieren es mit C++ / WinRT nicht-Windows-Runtime- [\*\*WinRT:: Delegate&lt;… T&gt; \*\*](/uwp/cpp-ref-for-winrt/delegate) strukturvorlage, die eine effiziente und Referenz-gezählt Delegat ist.</span><span class="sxs-lookup"><span data-stu-id="33cb6-163">If your event is used only internally within your C++/WinRT project (not across binaries), then you still use the [**winrt::event**](/uwp/cpp-ref-for-winrt/event) struct template, but you parameterize it with C++/WinRT's non-Windows-Runtime [**winrt::delegate&lt;... T&gt;**](/uwp/cpp-ref-for-winrt/delegate) struct template, which is an efficient, reference-counted delegate.</span></span> <span data-ttu-id="33cb6-164">Eine beliebige Anzahl von Parametern unterstützt, und sie sind nicht auf Windows-Runtime-Typen beschränkt.</span><span class="sxs-lookup"><span data-stu-id="33cb6-164">It supports any number of parameters, and they are not limited to Windows Runtime types.</span></span>

<span data-ttu-id="33cb6-165">Das folgende Beispiel zeigt einen Delegaten zuerst, Signatur, die keine Parameter (im Wesentlichen eine einfache Signal), und klicken Sie dann, die eine Zeichenfolge akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="33cb6-165">The example below first shows a delegate signature that doesn't take any parameters (essentially a simple signal), and then one that takes a string.</span></span>

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

<span data-ttu-id="33cb6-166">Beachten Sie, wie Sie auf das Ereignis hinzufügen können beliebig viele abonnierende Delegaten wie gewünscht.</span><span class="sxs-lookup"><span data-stu-id="33cb6-166">Notice how you can add to the event as many subscribing delegates as you wish.</span></span> <span data-ttu-id="33cb6-167">Es gibt jedoch einige Aufwand, ein Ereignis.</span><span class="sxs-lookup"><span data-stu-id="33cb6-167">However, there is some overhead associated with an event.</span></span> <span data-ttu-id="33cb6-168">Wenn Sie benötigen lediglich einen einfachen Rückruf mit nur einem einzelnen abonnierenden Delegaten, Sie können [\*\*WinRT:: Delegate&lt;… T&gt; \*\*](/uwp/cpp-ref-for-winrt/delegate) selbst.</span><span class="sxs-lookup"><span data-stu-id="33cb6-168">If all you need is a simple callback with only a single subscribing delegate, then you can use [**winrt::delegate&lt;... T&gt;**](/uwp/cpp-ref-for-winrt/delegate) on its own.</span></span>

```cppwinrt
winrt::delegate<> signalCallback;
signalCallback = [] { std::wcout << L"Hello, World!" << std::endl; };
signalCallback();

winrt::delegate<std::wstring> logCallback;
logCallback = [](std::wstring const& message) { std::wcout << message.c_str() << std::endl; }f;
logCallback(L"Hello, World!");
```

<span data-ttu-id="33cb6-169">Wenn Sie von einer C++ Portieren / CX-Codebasis, in denen Ereignisse und Delegate intern innerhalb eines Projekts verwendet werden, und klicken Sie dann **WinRT:: Delegate** hilft Ihnen beim Replizieren dieses Musters in C++ / WinRT.</span><span class="sxs-lookup"><span data-stu-id="33cb6-169">If you're porting from a C++/CX codebase where events and delegates are used internally within a project, then **winrt::delegate** will help you to replicate that pattern in C++/WinRT.</span></span>

## <a name="design-guidelines"></a><span data-ttu-id="33cb6-170">Entwurfsrichtlinien</span><span class="sxs-lookup"><span data-stu-id="33cb6-170">Design guidelines</span></span>

<span data-ttu-id="33cb6-171">Es wird empfohlen, dass Sie Ereignisse und nicht Delegaten, die als Funktionsparameter übergeben.</span><span class="sxs-lookup"><span data-stu-id="33cb6-171">We recommend that you pass events, and not delegates, as function parameters.</span></span> <span data-ttu-id="33cb6-172">Die Funktion zum **Hinzufügen** von [**winrt::event**](/uwp/cpp-ref-for-winrt/event) ist die einzige Ausnahme ist, müssen Sie einen Delegaten in diesem Fall übergeben.</span><span class="sxs-lookup"><span data-stu-id="33cb6-172">The **add** function of [**winrt::event**](/uwp/cpp-ref-for-winrt/event) is the one exception, because you must pass a delegate in that case.</span></span> <span data-ttu-id="33cb6-173">Der Grund für diese Richtlinie ist, Delegaten unterschiedliche Formen, in anderen Windows-Runtime-Sprachen annehmen können (hinsichtlich der gibt an, ob sie eine Clientregistrierung oder mehrere unterstützen).</span><span class="sxs-lookup"><span data-stu-id="33cb6-173">The reason for this guideline is because delegates can take different forms across different Windows Runtime languages (in terms of whether they support one client registration, or multiple).</span></span> <span data-ttu-id="33cb6-174">Ereignisse, mit deren Modell mit mehreren Abonnenten bilden eine sehr viel besser vorhersehbare und einheitliche Option.</span><span class="sxs-lookup"><span data-stu-id="33cb6-174">Events, with their multiple subscriber model, constitute a much more predictable and consistent option.</span></span>

<span data-ttu-id="33cb6-175">Die Signatur für den Ereignishandlerdelegaten sollten bestehen aus zwei Parameter: *Absender* (**IInspectable**) und *Args* (einige Ereignisargumenttyp, z. B. [**RoutedEventArgs**](/uwp/api/windows.ui.xaml.routedeventargs)).</span><span class="sxs-lookup"><span data-stu-id="33cb6-175">The signature for an event handler delegate should consist of two parameters: *sender* (**IInspectable**), and *args* (some event argument type, for example [**RoutedEventArgs**](/uwp/api/windows.ui.xaml.routedeventargs)).</span></span>

<span data-ttu-id="33cb6-176">Beachten Sie, dass diese Richtlinien nicht unbedingt angewendet werden, wenn Sie eine interne API entwerfen.</span><span class="sxs-lookup"><span data-stu-id="33cb6-176">Note that these guidelines don't necessarily apply if you're designing an internal API.</span></span> <span data-ttu-id="33cb6-177">Obwohl interne APIs häufig im Laufe der Zeit veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="33cb6-177">Although, internal APIs often become public over time.</span></span>

## <a name="related-topics"></a><span data-ttu-id="33cb6-178">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="33cb6-178">Related topics</span></span>
* [<span data-ttu-id="33cb6-179">Erstellen von APIs mit C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="33cb6-179">Author APIs with C++/WinRT</span></span>](author-apis.md)
* [<span data-ttu-id="33cb6-180">Verwenden von APIs mit C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="33cb6-180">Consume APIs with C++/WinRT</span></span>](consume-apis.md)
* [<span data-ttu-id="33cb6-181">Verarbeiten von Ereignissen über Delegaten in C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="33cb6-181">Handle events by using delegates in C++/WinRT</span></span>](handle-events.md)
