---
author: normesta
ms.assetid: 34C00F9F-2196-46A3-A32F-0067AB48291B
description: Dieser Artikel beschreibt die empfohlene Vorgehensweise zur Verwendung asynchroner Methoden in für VisualC++-komponentenerweiterungen (C++ / CX) mithilfe der Task-Klasse im Concurrency Namespace in "ppltasks.h" definiert.
title: Asynchrone Programmierung in C++
ms.author: normesta
ms.date: 05/14/2018
ms.topic: article
keywords: Windows10, UWP, Threads, asynchron, C++
ms.localizationpriority: medium
ms.openlocfilehash: 33b110e713608260cd5c19544292e9211904a730
ms.sourcegitcommit: 70ab58b88d248de2332096b20dbd6a4643d137a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "5930845"
---
# <a name="asynchronous-programming-in-ccx"></a><span data-ttu-id="f0c3f-104">Asynchrone Programmierung in C++/CX</span><span class="sxs-lookup"><span data-stu-id="f0c3f-104">Asynchronous programming in C++/CX</span></span>
> [!NOTE]
> <span data-ttu-id="f0c3f-105">In diesem Thema erhalten Sie Unterstützung bei der Verwaltung Ihrer C++/CX-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-105">This topic exists to help you maintain your C++/CX application.</span></span> <span data-ttu-id="f0c3f-106">Es wird jedoch empfohlen, dass Sie [C++/WinRT](../cpp-and-winrt-apis/intro-to-using-cpp-with-winrt.md) für neue Anwendungen nutzen.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-106">But we recommend that you use [C++/WinRT](../cpp-and-winrt-apis/intro-to-using-cpp-with-winrt.md) for new applications.</span></span> <span data-ttu-id="f0c3f-107">C++/WinRT ist eine vollständig standardisierte, moderne C++17 Sprachprojektion für Windows-Runtime-(WinRT)-APIs, die als headerdateibasierte Bibliothek implementiert ist und Ihnen einen erstklassigen Zugriff auf die moderne Windows-API bietet.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-107">C++/WinRT is an entirely standard modern C++17 language projection for Windows Runtime (WinRT) APIs, implemented as a header-file-based library, and designed to provide you with first-class access to the modern Windows API.</span></span>

<span data-ttu-id="f0c3f-108">Dieser Artikel beschreibt die empfohlene Vorgehensweise zur Verwendung asynchroner Methoden in für VisualC++-komponentenerweiterungen (C++ / CX) mithilfe der `task` -Klasse, die in definiert ist die `concurrency` Namespace in "ppltasks.h".</span><span class="sxs-lookup"><span data-stu-id="f0c3f-108">This article describes the recommended way to consume asynchronous methods in VisualC++ component extensions (C++/CX) by using the `task` class that's defined in the `concurrency` namespace in ppltasks.h.</span></span>

## <a name="universal-windows-platform-uwp-asynchronous-types"></a><span data-ttu-id="f0c3f-109">Asynchrone UWP-Typen (Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="f0c3f-109">Universal Windows Platform (UWP) asynchronous types</span></span>
<span data-ttu-id="f0c3f-110">Die Universelle Windows-Plattform (UWP) umfasst ein ausgearbeitetes Modell für den Aufruf asynchroner Methoden und stellt die Typen bereit, die Sie für die Verwendung dieser Methoden benötigen.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-110">The Universal Windows Platform (UWP) features a well-defined model for calling asynchronous methods and provides the types that you need to consume such methods.</span></span> <span data-ttu-id="f0c3f-111">Wenn Sie mit dem asynchronen Modell der UWP nicht vertraut sind, sollten Sie den Artikel [Asynchrone Programmierung][AsyncProgramming] lesen, bevor Sie mit diesen Erläuterungen fortfahren.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-111">If you are not familiar with the UWP asynchronous model, read [Asynchronous Programming][AsyncProgramming] before you read the rest of this article.</span></span>

<span data-ttu-id="f0c3f-112">Sie können die asynchronen UWP-APIs zwar direkt in C++ verwenden, aber es ist besser, die [**task class**][task-class] und die zugehörigen Typen und Funktionen zu verwenden. Diese sind im [**concurrency**][concurrencyNamespace] -Namespace enthalten und in `<ppltasks.h>` definiert.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-112">Although you can consume the asynchronous UWP APIs directly in C++, the preferred approach is to use the [**task class**][task-class] and its related types and functions, which are contained in the [**concurrency**][concurrencyNamespace] namespace and defined in `<ppltasks.h>`.</span></span> <span data-ttu-id="f0c3f-113">**concurrency::task** ist eine Klasse für allgemeine Zwecke. Bei Verwendung des **/ZW**-Compilerschalters, der für UWP-Apps und die entsprechenden Komponenten benötigt wird, werden jedoch die asynchronen Typen der UWP durch die Task-Klasse gekapselt, was Folgendes vereinfacht:</span><span class="sxs-lookup"><span data-stu-id="f0c3f-113">The **concurrency::task** is a general-purpose type, but when the **/ZW** compiler switch—which is required for Universal Windows Platform (UWP) apps and components—is used, the task class encapsulates the UWP asynchronous types so that it's easier to:</span></span>

-   <span data-ttu-id="f0c3f-114">Verkettung mehrerer asynchroner und synchroner Vorgänge</span><span class="sxs-lookup"><span data-stu-id="f0c3f-114">chain multiple asynchronous and synchronous operations together</span></span>

-   <span data-ttu-id="f0c3f-115">Behandlung von Ausnahmen in Aufgabenabfolgen</span><span class="sxs-lookup"><span data-stu-id="f0c3f-115">handle exceptions in task chains</span></span>

-   <span data-ttu-id="f0c3f-116">Ausführung von Abbrüchen in Aufgabenabfolgen</span><span class="sxs-lookup"><span data-stu-id="f0c3f-116">perform cancellation in task chains</span></span>

-   <span data-ttu-id="f0c3f-117">Gewährleistung, dass einzelne Aufgaben im richtigen Threadkontext oder -apartment ausgeführt werden</span><span class="sxs-lookup"><span data-stu-id="f0c3f-117">ensure that individual tasks run in the appropriate thread context or apartment</span></span>

<span data-ttu-id="f0c3f-118">Dieser Artikel bietet einen allgemeinen Überblick über die Verwendung der **Task**-Klasse mit den asynchronen UWP-APIs.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-118">This article provides basic guidance about how to use the **task** class with the UWP asynchronous APIs.</span></span> <span data-ttu-id="f0c3f-119">Die vollständige Dokumentation zur **task**-Klasse und den dazugehörigen Methoden, einschließlich [**create\_task**][createTask], finden Sie unter [Task-Parallelität (Concurrency Runtime)][taskParallelism].</span><span class="sxs-lookup"><span data-stu-id="f0c3f-119">For more complete documentation about **task** and its related methods including [**create\_task**][createTask], see [Task Parallelism (Concurrency Runtime)][taskParallelism].</span></span> 

## <a name="consuming-an-async-operation-by-using-a-task"></a><span data-ttu-id="f0c3f-120">Verwendung asynchroner Vorgänge mit Aufgaben</span><span class="sxs-lookup"><span data-stu-id="f0c3f-120">Consuming an async operation by using a task</span></span>
<span data-ttu-id="f0c3f-121">Im folgenden Beispiel wird gezeigt, wie Sie mit der Task-Klasse eine **async**-Methode verwenden, die eine [**IAsyncOperation**][IAsyncOperation]-Schnittstelle zurückgibt und durch deren Vorgang ein Wert erzeugt wird.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-121">The following example shows how to use the task class to consume an **async** method that returns an [**IAsyncOperation**][IAsyncOperation] interface and whose operation produces a value.</span></span> <span data-ttu-id="f0c3f-122">Die grundlegenden Schritte:</span><span class="sxs-lookup"><span data-stu-id="f0c3f-122">Here are the basic steps:</span></span>

1.  <span data-ttu-id="f0c3f-123">Rufen Sie die `create_task`-Methode auf, und übergeben Sie diese an das **IAsyncOperation^**-Objekt.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-123">Call the `create_task` method and pass it the **IAsyncOperation^** object.</span></span>

2.  <span data-ttu-id="f0c3f-124">Rufen Sie in der Aufgabe die [**task::then**][taskThen]-Memberfunktion auf, und geben Sie einen Lambda-Ausdruck an, der nach Ausführung des asynchronen Vorgangs aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-124">Call the member function [**task::then**][taskThen] on the task and supply a lambda that will be invoked when the asynchronous operation completes.</span></span>

``` cpp
#include <ppltasks.h>
using namespace concurrency;
using namespace Windows::Devices::Enumeration;
...
void App::TestAsync()
{    
    //Call the *Async method that starts the operation.
    IAsyncOperation<DeviceInformationCollection^>^ deviceOp =
        DeviceInformation::FindAllAsync();

    // Explicit construction. (Not recommended)
    // Pass the IAsyncOperation to a task constructor.
    // task<DeviceInformationCollection^> deviceEnumTask(deviceOp);

    // Recommended:
    auto deviceEnumTask = create_task(deviceOp);

    // Call the task's .then member function, and provide
    // the lambda to be invoked when the async operation completes.
    deviceEnumTask.then( [this] (DeviceInformationCollection^ devices )
    {       
        for(int i = 0; i < devices->Size; i++)
        {
            DeviceInformation^ di = devices->GetAt(i);
            // Do something with di...          
        }       
    }); // end lambda
    // Continue doing work or return...
}
```

<span data-ttu-id="f0c3f-125">Die Aufgabe, die von der [**task::then**][taskThen]-Funktion erstellt und zurückgegeben wird, wird als *Fortsetzung* bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-125">The task that's created and returned by the [**task::then**][taskThen] function is known as a *continuation*.</span></span> <span data-ttu-id="f0c3f-126">Das Eingabeargument für den benutzerdefinierten Lambda-Ausdruck ist (in diesem Fall) das Ergebnis der beendeten Aufgabe.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-126">The input argument (in this case) to the user-provided lambda is the result that the task operation produces when it completes.</span></span> <span data-ttu-id="f0c3f-127">Derselbe Wert würde auch mit einem Aufruf von [**IAsyncOperation::GetResults**](https://msdn.microsoft.com/library/windows/apps/br206600) bei direkter Verwendung der **IAsyncOperation**-Schnittstelle abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-127">It's the same value that would be retrieved by calling [**IAsyncOperation::GetResults**](https://msdn.microsoft.com/library/windows/apps/br206600) if you were using the **IAsyncOperation** interface directly.</span></span>

<span data-ttu-id="f0c3f-128">Der Aufruf der [**task::then**][taskThen]-Methode wird sofort beendet. Der Delegat wird erst ausgeführt, nachdem die asynchronen Vorgänge erfolgreich beendet wurden.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-128">The [**task::then**][taskThen] method returns immediately, and its delegate doesn't run until the asynchronous work completes successfully.</span></span> <span data-ttu-id="f0c3f-129">In diesem Beispiel wird die Fortsetzung nicht ausgeführt, wenn der asynchrone Vorgang eine Ausnahme auslöst oder aufgrund einer Abbruchanforderung mit einem Abbruch beendet wird.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-129">In this example, if the asynchronous operation causes an exception to be thrown, or ends in the canceled state as a result of a cancellation request, the continuation will never execute.</span></span> <span data-ttu-id="f0c3f-130">Weiter unten erfahren Sie, wie Sie Fortsetzungen schreiben, die auch bei einem Abbruch oder Fehler der vorhergehenden Aufgabe ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-130">Later, we’ll describe how to write continuations that execute even if the previous task was cancelled or failed.</span></span>

<span data-ttu-id="f0c3f-131">Sie deklarieren die Aufgabenvariable zwar im lokalen Stapel, aber die Lebensdauer wird so verwaltet, dass die Variable erst gelöscht wird, wenn alle zugehörigen Vorgänge abgeschlossen sind und alle Verweise auf die Variable außerhalb des Bereichs liegen– auch dann, wenn der Aufruf der Methode vor Abschluss des Vorgangs beendet wird.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-131">Although you declare the task variable on the local stack, it manages its lifetime so that it is not deleted until all of its operations complete and all references to it go out of scope, even if the method returns before the operations complete.</span></span>

## <a name="creating-a-chain-of-tasks"></a><span data-ttu-id="f0c3f-132">Erstellen von Aufgabenabfolgen</span><span class="sxs-lookup"><span data-stu-id="f0c3f-132">Creating a chain of tasks</span></span>
<span data-ttu-id="f0c3f-133">Bei der asynchronen Programmierung werden in vielen Fällen Abfolgen von Vorgängen definiert, sogenannte *Aufgabenabfolgen*, bei denen eine Fortsetzung immer erst ausgeführt wird, wenn die vorhergehende Aufgabe beendet ist.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-133">In asynchronous programming, it's common to define a sequence of operations, also known as *task chains*, in which each continuation executes only when the previous one completes.</span></span> <span data-ttu-id="f0c3f-134">In manchen Fällen erzeugt die letzte (oder *vorhergehende*) Aufgabe einen Wert, den die Fortsetzung als Eingabe akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-134">In some cases, the previous (or *antecedent*) task produces a value that the continuation accepts as input.</span></span> <span data-ttu-id="f0c3f-135">Mithilfe der [**task::then**][taskThen]-Methode können Sie intuitiv und ganz einfach Aufgabenabfolgen erstellen. Die Methode gibt ein Element vom Typ **task<T>** zurück, wobei **T** der Rückgabetyp der Lambda-Funktion ist.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-135">By using the [**task::then**][taskThen] method, you can create task chains in an intuitive and straightforward manner; the method returns a **task<T>** where **T** is the return type of the lambda function.</span></span> <span data-ttu-id="f0c3f-136">Eine Aufgabenabfolge kann mehrere Fortsetzungen enthalten: </span><span class="sxs-lookup"><span data-stu-id="f0c3f-136">You can compose multiple continuations into a task chain:</span></span> `myTask.then(…).then(…).then(…);`

<span data-ttu-id="f0c3f-137">Aufgabenabfolgen sind insbesondere dann nützlich, wenn eine Fortsetzung einen neuen asynchronen Vorgang erstellt. Solche Aufgaben werden als asynchrone Aufgaben bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-137">Task chains are especially useful when a continuation creates a new asynchronous operation; such a task is known as an asynchronous task.</span></span> <span data-ttu-id="f0c3f-138">Das folgende Beispiel zeigt eine Aufgabenabfolge mit zwei Fortsetzungen.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-138">The following example illustrates a task chain that has two continuations.</span></span> <span data-ttu-id="f0c3f-139">Die einleitende Aufgabe ruft der Handle für eine bestehende Datei ab. Nach Abschluss dieses Vorgangs startet die erste Fortsetzung einen neuen asynchronen Vorgang, mit dem die Datei gelöscht wird.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-139">The initial task acquires the handle to an existing file, and when that operation completes, the first continuation starts up a new asynchronous operation to delete the file.</span></span> <span data-ttu-id="f0c3f-140">Nach Abschluss dieses Vorgangs wird die zweite Fortsetzung ausgeführt, die eine Bestätigungsmeldung ausgibt.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-140">When that operation completes, the second continuation runs, and outputs a confirmation message.</span></span>

``` cpp
#include <ppltasks.h>
using namespace concurrency;
...
void App::DeleteWithTasks(String^ fileName)
{    
    using namespace Windows::Storage;
    StorageFolder^ localFolder = ApplicationData::Current->LocalFolder;
    auto getFileTask = create_task(localFolder->GetFileAsync(fileName));

    getFileTask.then([](StorageFile^ storageFileSample) ->IAsyncAction^ {       
        return storageFileSample->DeleteAsync();
    }).then([](void) {
        OutputDebugString(L"File deleted.");
    });
}
```

<span data-ttu-id="f0c3f-141">Das Beispiel oben illustriert vier zentrale Aspekte:</span><span class="sxs-lookup"><span data-stu-id="f0c3f-141">The previous example illustrates four important points:</span></span>

-   <span data-ttu-id="f0c3f-142">Mit der ersten Fortsetzung wird das [**IAsyncAction^**][IAsyncAction]-Objekt in ein Element vom Typ **task<void>** konvertiert und das Element vom Typ **task** zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-142">The first continuation converts the [**IAsyncAction^**][IAsyncAction] object to a **task<void>** and returns the **task**.</span></span>

-   <span data-ttu-id="f0c3f-143">Die zweite Fortsetzung führt keine Fehlerbehandlung durch und verwendet daher **void** als Eingabe (und nicht **task<void>**).</span><span class="sxs-lookup"><span data-stu-id="f0c3f-143">The second continuation performs no error handling, and therefore takes **void** and not **task<void>** as input.</span></span> <span data-ttu-id="f0c3f-144">Es handelt sich um eine wertbasierte Fortsetzung.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-144">It is a value-based continuation.</span></span>

-   <span data-ttu-id="f0c3f-145">Die zweite Fortsetzung wird erst ausgeführt, wenn der [**DeleteAsync**][deleteAsync]-Vorgang beendet ist.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-145">The second continuation doesn't execute until the [**DeleteAsync**][deleteAsync] operation completes.</span></span>

-   <span data-ttu-id="f0c3f-146">Da die zweite Fortsetzung auf einem Wert basiert, wird sie nicht ausgeführt, wenn der mit dem Aufruf [**DeleteAsync**][deleteAsync] gestartete Vorgang eine Ausnahme auslöst.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-146">Because the second continuation is value-based, if the operation that was started by the call to [**DeleteAsync**][deleteAsync] throws an exception, the second continuation doesn't execute at all.</span></span>

<span data-ttu-id="f0c3f-147">**Hinweis:** Aufgabenabfolgen ist nur eine der Methoden, um die **Task** -Klasse verwenden, um asynchrone Vorgänge verfassen.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-147">**Note**Creating a task chain is just one of the ways to use the **task** class to compose asynchronous operations.</span></span> <span data-ttu-id="f0c3f-148">Sie können Vorgänge auch mit den Verknüpfungs- und Auswahloperatoren **&&** und **||** erstellen.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-148">You can also compose operations by using join and choice operators **&&** and **||**.</span></span> <span data-ttu-id="f0c3f-149">Weitere Informationen finden Sie unter [Task-Parallelität (Konkurrenz-Runtime)][taskParallelism].</span><span class="sxs-lookup"><span data-stu-id="f0c3f-149">For more information, see [Task Parallelism (Concurrency Runtime)][taskParallelism].</span></span>

## <a name="lambda-function-return-types-and-task-return-types"></a><span data-ttu-id="f0c3f-150">Rückgabetypen für Lambda-Funktionen und Aufgaben</span><span class="sxs-lookup"><span data-stu-id="f0c3f-150">Lambda function return types and task return types</span></span>
<span data-ttu-id="f0c3f-151">Bei Aufgabenfortsetzungen ist der Rückgabetyp der Lambda-Funktion von einem **task**-Objekt umschlossen.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-151">In a task continuation, the return type of the lambda function is wrapped in a **task** object.</span></span> <span data-ttu-id="f0c3f-152">Wenn die Lambda-Funktion den **double**-Typ zurückgibt, hat die Fortsetzungsaufgabe den **task<double>**-Typ.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-152">If the lambda returns a **double**, then the type of the continuation task is **task<double>**.</span></span> <span data-ttu-id="f0c3f-153">Das Aufgabenobjekt ist jedoch so konzipiert, dass es keine unnötig geschachtelten Rückgabetypen erzeugt.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-153">However, the task object is designed so that it doesn't produce needlessly nested return types.</span></span> <span data-ttu-id="f0c3f-154">Wenn eine Lambda-Funktion den **IAsyncOperation<SyndicationFeed^>^**-Typ zurückgibt, gibt die Fortsetzung den **task<SyndicationFeed^>**-Typ und nicht **task<task<SyndicationFeed^>>** oder **task<IAsyncOperation<SyndicationFeed^>^>^** zurück.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-154">If a lambda returns an **IAsyncOperation<SyndicationFeed^>^**, the continuation returns a **task<SyndicationFeed^>**, not a **task<task<SyndicationFeed^>>** or **task<IAsyncOperation<SyndicationFeed^>^>^**.</span></span> <span data-ttu-id="f0c3f-155">Dieser Vorgang wird als *asynchrones Entpacken* bezeichnet und sorgt dafür, dass der asynchrone Vorgang in der Fortsetzung vor dem Aufruf der nächsten Fortsetzung beendet wird.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-155">This process is known as *asynchronous unwrapping* and it also ensures that the asynchronous operation inside the continuation completes before the next continuation is invoked.</span></span>

<span data-ttu-id="f0c3f-156">Beachten Sie im vorhergehenden Beispiel, dass die Aufgabe den **task<void>**-Typ zurückgibt, obwohl die zugehörige Lambda-Funktion ein [**IAsyncInfo**][IAsyncInfo]-Objekt zurückgegeben hat.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-156">In the previous example, notice that the task returns a **task<void>** even though its lambda returned an [**IAsyncInfo**][IAsyncInfo] object.</span></span> <span data-ttu-id="f0c3f-157">Die folgende Tabelle gibt einen Überblick über die Typkonvertierungen zwischen Lambda-Funktionen und den einschließenden Aufgaben:</span><span class="sxs-lookup"><span data-stu-id="f0c3f-157">The following table summarizes the type conversions that occur between a lambda function and the enclosing task:</span></span>

| | |
|--------------------------------------------------------|---------------------|
| <span data-ttu-id="f0c3f-158">Lambda-Rückgabetyp</span><span class="sxs-lookup"><span data-stu-id="f0c3f-158">lambda return type</span></span>                                     | `.then` <span data-ttu-id="f0c3f-159">Rückgabetyp</span><span class="sxs-lookup"><span data-stu-id="f0c3f-159">return type</span></span> |
| <span data-ttu-id="f0c3f-160">TResult</span><span class="sxs-lookup"><span data-stu-id="f0c3f-160">TResult</span></span>                                                | <span data-ttu-id="f0c3f-161">Task</span><span class="sxs-lookup"><span data-stu-id="f0c3f-161">task</span></span><TResult> |
| <span data-ttu-id="f0c3f-162">IAsyncOperation<TResult>^</span><span class="sxs-lookup"><span data-stu-id="f0c3f-162">IAsyncOperation<TResult>^</span></span>                        | <span data-ttu-id="f0c3f-163">Task</span><span class="sxs-lookup"><span data-stu-id="f0c3f-163">task</span></span><TResult> |
| <span data-ttu-id="f0c3f-164">IAsyncOperationWithProgress<TResult, TProgress>^</span><span class="sxs-lookup"><span data-stu-id="f0c3f-164">IAsyncOperationWithProgress<TResult, TProgress>^</span></span> | <span data-ttu-id="f0c3f-165">Task</span><span class="sxs-lookup"><span data-stu-id="f0c3f-165">task</span></span><TResult> |
|<span data-ttu-id="f0c3f-166">IAsyncAction^</span><span class="sxs-lookup"><span data-stu-id="f0c3f-166">IAsyncAction^</span></span>                                           | <span data-ttu-id="f0c3f-167">Task</span><span class="sxs-lookup"><span data-stu-id="f0c3f-167">task</span></span><void>    |
| <span data-ttu-id="f0c3f-168">IAsyncActionWithProgress<TProgress>^</span><span class="sxs-lookup"><span data-stu-id="f0c3f-168">IAsyncActionWithProgress<TProgress>^</span></span>             |<span data-ttu-id="f0c3f-169">Task</span><span class="sxs-lookup"><span data-stu-id="f0c3f-169">task</span></span><void>     |
| <span data-ttu-id="f0c3f-170">Task</span><span class="sxs-lookup"><span data-stu-id="f0c3f-170">task</span></span><TResult>                                    |<span data-ttu-id="f0c3f-171">Task</span><span class="sxs-lookup"><span data-stu-id="f0c3f-171">task</span></span><TResult>  |


## <a name="canceling-tasks"></a><span data-ttu-id="f0c3f-172">Abbrechen von Aufgaben</span><span class="sxs-lookup"><span data-stu-id="f0c3f-172">Canceling tasks</span></span>
<span data-ttu-id="f0c3f-173">In vielen Fällen ist es ratsam, Benutzern die Möglichkeit zum Abbrechen eines asynchronen Vorgangs zu geben.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-173">It is often a good idea to give the user the option to cancel an asynchronous operation.</span></span> <span data-ttu-id="f0c3f-174">Mitunter müssen Sie außerdem einen Vorgang programmgesteuert von außerhalb der Aufgabenabfolge abbrechen.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-174">And in some cases you might have to cancel an operation programmatically from outside the task chain.</span></span> <span data-ttu-id="f0c3f-175">Zwar verfügt jeder \***Async** -Rückgabetyp über eine von [**Cancel**][IAsyncInfoCancel] geerbte [**IAsyncInfo**][IAsyncInfo]-Methode, aber es ist ungünstig, externen Methoden Zugriff darauf zu gewähren.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-175">Although each \***Async** return type has a [**Cancel**][IAsyncInfoCancel] method that it inherits from [**IAsyncInfo**][IAsyncInfo], it's awkward to expose it to outside methods.</span></span> <span data-ttu-id="f0c3f-176">Vorzugsweise sollte für den Abbruch in einer Aufgabenabfolge mithilfe einer [**cancellation\_token\_source**](https://msdn.microsoft.com/library/windows/apps/xaml/hh749985.aspx)-Klasse eine [**cancellation\_token**](https://msdn.microsoft.com/library/windows/apps/xaml/hh749975.aspx)-Klasse erstellt und das Token dann an den Konstruktor der ursprünglichen Aufgabe übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-176">The preferred way to support cancellation in a task chain is to use a [**cancellation\_token\_source**](https://msdn.microsoft.com/library/windows/apps/xaml/hh749985.aspx) to create a [**cancellation\_token**](https://msdn.microsoft.com/library/windows/apps/xaml/hh749975.aspx), and then pass the token to the constructor of the initial task.</span></span> <span data-ttu-id="f0c3f-177">Wird eine asynchrone Aufgabe mit einem Abbruchtoken erstellt und die [**cancellation\_token\_source::cancel**](https://msdn.microsoft.com/library/windows/apps/xaml/hh750076.aspx)-Klasse aufgerufen, ruft die Aufgabe im **IAsync\***-Vorgang automatisch **Cancel** auf und übergibt die Abbruchanforderung an die Fortsetzungskette.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-177">If an asynchronous task is created with a cancellation token, and [**cancellation\_token\_source::cancel**](https://msdn.microsoft.com/library/windows/apps/xaml/hh750076.aspx) is called, the task automatically calls **Cancel** on the **IAsync\*** operation and passes the cancellation request down its continuation chain.</span></span> <span data-ttu-id="f0c3f-178">Im folgenden Pseudocode wird dieses grundlegende Konzept illustriert.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-178">The following pseudocode demonstrates the basic approach.</span></span>

``` cpp
//Class member:
cancellation_token_source m_fileTaskTokenSource;

// Cancel button event handler:
m_fileTaskTokenSource.cancel();

// task chain
auto getFileTask2 = create_task(documentsFolder->GetFileAsync(fileName),
                                m_fileTaskTokenSource.get_token());
//getFileTask2.then ...
```

<span data-ttu-id="f0c3f-179">Beim Abbruch einer Aufgabe wird eine [**task\_canceled**][taskCanceled]-Ausnahme in der Aufgabenabfolge weitergegeben.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-179">When a task is canceled, a [**task\_canceled**][taskCanceled] exception is propagated down the task chain.</span></span> <span data-ttu-id="f0c3f-180">Wertbasierte Fortsetzungen werden nicht ausgeführt. Aufgabenbasierte Fortsetzungen dagegen lösen beim Aufruf von [**task::get**][taskGet] die Ausnahme aus.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-180">Value-based continuations will simply not execute, but task-based continuations will cause the exception to be thrown when [**task::get**][taskGet] is called.</span></span> <span data-ttu-id="f0c3f-181">Stellen Sie bei Fortsetzungen für die Fehlerbehandlung sicher, dass die **task\_canceled**-Ausnahme explizit an die Fortsetzung übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-181">If you have an error-handling continuation, make sure that it catches the **task\_canceled** exception explicitly.</span></span> <span data-ttu-id="f0c3f-182">(Diese Ausnahme wird nicht von [**Platform::Exception**](https://msdn.microsoft.com/library/windows/apps/xaml/hh755825.aspx) abgeleitet.)</span><span class="sxs-lookup"><span data-stu-id="f0c3f-182">(This exception is not derived from [**Platform::Exception**](https://msdn.microsoft.com/library/windows/apps/xaml/hh755825.aspx).)</span></span>

<span data-ttu-id="f0c3f-183">Abbruchvorgänge sind kooperativ.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-183">Cancellation is cooperative.</span></span> <span data-ttu-id="f0c3f-184">Wenn eine Fortsetzung neben dem Aufruf einer UWP-Methode zeitintensive Vorgänge ausführt, ist es wichtig, dass Sie den Status des Abbruchtokens regelmäßig überprüfen und die Ausführung bei einem Abbruch beenden.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-184">If your continuation does some long-running work beyond just invoking a UWP method, then it is your responsibility to check the state of the cancellation token periodically and stop execution if it is canceled.</span></span> <span data-ttu-id="f0c3f-185">Nach der Bereinigung aller in der Fortsetzung zugeordneten Ressourcen rufen Sie [**cancel\_current\_task**](https://msdn.microsoft.com/library/windows/apps/xaml/hh749945.aspx) auf, um die betreffende Aufgabe abzubrechen und den Abbruch an alle nachfolgenden wertbasierten Fortsetzungen weiterzugeben.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-185">After you clean up all resources that were allocated in the continuation, call [**cancel\_current\_task**](https://msdn.microsoft.com/library/windows/apps/xaml/hh749945.aspx) to cancel that task and propagate the cancellation down to any value-based continuations that follow it.</span></span> <span data-ttu-id="f0c3f-186">Ein weiteres Beispiel: Sie können Aufgabenabfolgen erstellen, die das Ergebnis eines [**FileSavePicker**](https://msdn.microsoft.com/library/windows/apps/BR207871)-Vorgangs darstellen.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-186">Here's another example: you can create a task chain that represents the result of a [**FileSavePicker**](https://msdn.microsoft.com/library/windows/apps/BR207871) operation.</span></span> <span data-ttu-id="f0c3f-187">Wählt der Benutzer die Schaltfläche **Abbrechen**, wird die [**IAsyncInfo::Cancel**][IAsyncInfoCancel]-Methode nicht aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-187">If the user chooses the **Cancel** button, the [**IAsyncInfo::Cancel**][IAsyncInfoCancel] method is not called.</span></span> <span data-ttu-id="f0c3f-188">Stattdessen wird der Vorgang erfolgreich ausgeführt, allerdings mit der Rückgabe **nullptr**.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-188">Instead, the operation succeeds but returns **nullptr**.</span></span> <span data-ttu-id="f0c3f-189">Die Fortsetzung kann den Eingabeparameter testen und **cancel\_current\_task** aufrufen, wenn die Eingabe **nullptr** ist.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-189">The continuation can test the input parameter and call **cancel\_current\_task** if the input is **nullptr**.</span></span>

<span data-ttu-id="f0c3f-190">Weitere Informationen finden Sie unter [Abbruch in der PPL](https://msdn.microsoft.com/library/windows/apps/xaml/dd984117.aspx).</span><span class="sxs-lookup"><span data-stu-id="f0c3f-190">For more information, see [Cancellation in the PPL](https://msdn.microsoft.com/library/windows/apps/xaml/dd984117.aspx)</span></span>

## <a name="handling-errors-in-a-task-chain"></a><span data-ttu-id="f0c3f-191">Behandeln von Fehlern in Aufgabenabfolgen</span><span class="sxs-lookup"><span data-stu-id="f0c3f-191">Handling errors in a task chain</span></span>
<span data-ttu-id="f0c3f-192">Wenn eine Fortsetzung auch dann ausgeführt werden soll, wenn die vorhergehende Aufgabe abgebrochen wurde oder eine Ausnahme ausgelöst hat, müssen Sie die Fortsetzung als aufgabenbasierte Fortsetzung anlegen. Geben Sie dafür die Eingabe für die entsprechende Lambda-Funktion als **task<TResult>** oder **task<void>** an, wenn die Lambda-Funktion der vorhergehenden Aufgabe den [**IAsyncAction^**][IAsyncAction]-Typ zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-192">If you want a continuation to execute even if the antecedent was canceled or threw an exception, then make the continuation a task-based continuation by specifying the input to its lambda function as a **task<TResult>** or **task<void>** if the lambda of the antecedent task returns an [**IAsyncAction^**][IAsyncAction].</span></span>

<span data-ttu-id="f0c3f-193">Zur Behandlung von Fehlern und Abbrüchen in Aufgabenabfolgen müssen jedoch nicht alle Fortsetzungen aufgabenbasiert sein, und Sie müssen nicht alle Vorgänge einschließen, die in einem `try…catch` -Block ausgelöst werden können.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-193">To handle errors and cancellation in a task chain, you don't have to make every continuation task-based or enclose every operation that might throw within a `try…catch` block.</span></span> <span data-ttu-id="f0c3f-194">Stattdessen können Sie am Ende der Abfolge eine aufgabenbasierte Fortsetzung hinzufügen und alle Fehler dort behandeln.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-194">Instead, you can add a task-based continuation at the end of the chain and handle all errors there.</span></span> <span data-ttu-id="f0c3f-195">Alle Ausnahmen (einschließlich [**task\_canceled**][taskCanceled]-Ausnahmen) werden entlang der Aufgabenabfolge weitergegeben, wobei wertbasierte Fortsetzungen ausgelassen werden. Auf diese Weise können Sie die Ausnahme in der aufgabenbasierten Fortsetzung für die Fehlerbehandlung verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-195">Any exception—this includes a [**task\_canceled**][taskCanceled] exception—will propagate down the task chain and bypass any value-based continuations, so that you can handle it in the error-handling task-based continuation.</span></span> <span data-ttu-id="f0c3f-196">Das Beispiel oben kann daher mit einer aufgabenbasierten Fortsetzung für die Fehlerbehandlung umgeschrieben werden:</span><span class="sxs-lookup"><span data-stu-id="f0c3f-196">We can rewrite the previous example to use an error-handling task-based continuation:</span></span>

``` cpp
#include <ppltasks.h>
void App::DeleteWithTasksHandleErrors(String^ fileName)
{    
    using namespace Windows::Storage;
    using namespace concurrency;

    StorageFolder^ documentsFolder = KnownFolders::DocumentsLibrary;
    auto getFileTask = create_task(documentsFolder->GetFileAsync(fileName));

    getFileTask.then([](StorageFile^ storageFileSample)
    {       
        return storageFileSample->DeleteAsync();
    })

    .then([](task<void> t)
    {

        try
        {
            t.get();
            // .get() didn' t throw, so we succeeded.
            OutputDebugString(L"File deleted.");
        }
        catch (Platform::COMException^ e)
        {
            //Example output: The system cannot find the specified file.
            OutputDebugString(e->Message->Data());
        }

    });
}
```

<span data-ttu-id="f0c3f-197">Bei aufgabenbasierten Fortsetzungen rufen wir die [**task::get**][taskGet]-Memberfunktion auf, um die Aufgabenergebnisse abzurufen.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-197">In a task-based continuation, we call the member function [**task::get**][taskGet] to get the results of the task.</span></span> <span data-ttu-id="f0c3f-198">Dabei muss weiterhin **task::get** aufgerufen werden. Dies gilt auch bei ergebnislosen [**IAsyncAction**][IAsyncAction]-Vorgängen, da **task::get** auch alle Ausnahmen abruft, die an die Aufgabe weitergegeben wurden.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-198">We still have to call **task::get** even if the operation was an [**IAsyncAction**][IAsyncAction] that produces no result because **task::get** also gets any exceptions that have been transported down to the task.</span></span> <span data-ttu-id="f0c3f-199">Wenn die Eingabeaufgabe eine Ausnahme speichert, wird diese mit dem Aufruf von **task::get** ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-199">If the input task is storing an exception, it is thrown at the call to **task::get**.</span></span> <span data-ttu-id="f0c3f-200">Wenn Sie **task::get** nicht aufrufen, am Ende der Kette keine aufgabenbasierte Fortsetzung verwenden oder den ausgelösten Ausnahmetyp nicht abfangen, wird eine **unobserved\_task\_exception**-Ausnahme ausgelöst, wenn alle Verweise auf die Aufgabe gelöscht wurden.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-200">If you don't call **task::get**, or don't use a task-based continuation at the end of the chain, or don't catch the exception type that was thrown, then an **unobserved\_task\_exception** is thrown when all references to the task have been deleted.</span></span>

<span data-ttu-id="f0c3f-201">Sie sollten nur Ausnahmen abfangen, die Sie auch behandeln können.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-201">Only catch the exceptions that you can handle.</span></span> <span data-ttu-id="f0c3f-202">Wenn die App einen Fehler ausgibt, den Sie nicht beheben können, ist es besser, die App abstürzen zu lassen, als sie mit einem unbekannten Status weiter auszuführen.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-202">If your app encounters an error that you can't recover from, it's better to let the app crash than to let it continue to run in an unknown state.</span></span> <span data-ttu-id="f0c3f-203">Außerdem sollten Sie grundsätzlich nicht versuchen, die **unobserved\_task\_exception**-Ausnahme direkt abzufangen.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-203">Also, in general, don't attempt to catch the **unobserved\_task\_exception** itself.</span></span> <span data-ttu-id="f0c3f-204">Diese Ausnahme ist in erster Linie für Diagnosezwecke gedacht.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-204">This exception is mainly intended for diagnostic purposes.</span></span> <span data-ttu-id="f0c3f-205">Wenn **unobserved\_task\_exception** ausgelöst wird, ist dies meist ein Hinweis auf einen Fehler im Code.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-205">When **unobserved\_task\_exception** is thrown, it usually indicates a bug in the code.</span></span> <span data-ttu-id="f0c3f-206">Die Ursache dafür ist entweder eine Ausnahme, die behandelt werden muss, oder eine nicht behebbare Ausnahme, die durch einen anderen Fehler im Code hervorgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-206">Often the cause is either an exception that should be handled, or an unrecoverable exception that's caused by some other error in the code.</span></span>

## <a name="managing-the-thread-context"></a><span data-ttu-id="f0c3f-207">Verwalten des Threadkontexts</span><span class="sxs-lookup"><span data-stu-id="f0c3f-207">Managing the thread context</span></span>
<span data-ttu-id="f0c3f-208">Die Benutzeroberfläche von UWP-Apps wird in einem Singlethread-Apartment (STA) ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-208">The UI of a UWP app runs in a single-threaded apartment (STA).</span></span> <span data-ttu-id="f0c3f-209">Aufgaben, deren Lambda-Ausdruck [**IAsyncAction**][IAsyncAction] oder [**IAsyncOperation**][IAsyncOperation] zurückgibt, sind apartmentfähig.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-209">A task whose lambda returns either an [**IAsyncAction**][IAsyncAction] or [**IAsyncOperation**][IAsyncOperation] is apartment-aware.</span></span> <span data-ttu-id="f0c3f-210">Wird die Aufgabe im STA erstellt, werden standardmäßig auch alle zugehörigen Fortsetzungen darin ausgeführt, sofern Sie nichts anderes angeben.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-210">If the task is created in the STA, then all of its continuations will run also run in it by default, unless you specify otherwise.</span></span> <span data-ttu-id="f0c3f-211">Anders gesagt: Die gesamte Aufgabenabfolge erbt die Apartmentfähigkeit von der übergeordneten Aufgabe.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-211">In other words, the entire task chain inherits apartment-awareness from the parent task.</span></span> <span data-ttu-id="f0c3f-212">Dieses Verhalten vereinfacht die Interaktion mit Benutzeroberflächen-Steuerelementen, auf die ausschließlich über das STA Zugriff besteht.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-212">This behavior helps simplify interactions with UI controls, which can only be accessed from the STA.</span></span>

<span data-ttu-id="f0c3f-213">Beispielsweise können Sie in einer UWP-App in der Memberfunktion jeder Klasse, die eine XAML-Seite darstellt, ein [**ListBox**](https://msdn.microsoft.com/library/windows/apps/BR242868) -Steuerelement innerhalb einer [**task::then**][taskThen] -Methode auffüllen, ohne dafür das [**Dispatcher**](https://msdn.microsoft.com/library/windows/apps/BR208211)-Objekt zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-213">For example, in a UWP app, in the member function of any class that represents a XAML page, you can populate a [**ListBox**](https://msdn.microsoft.com/library/windows/apps/BR242868) control from within a [**task::then**][taskThen] method without having to use the [**Dispatcher**](https://msdn.microsoft.com/library/windows/apps/BR208211) object.</span></span>

``` cpp
#include <ppltasks.h>
void App::SetFeedText()
{    
    using namespace Windows::Web::Syndication;
    using namespace concurrency;
    String^ url = "http://windowsteamblog.com/windows_phone/b/wmdev/atom.aspx";
    SyndicationClient^ client = ref new SyndicationClient();
    auto feedOp = client->RetrieveFeedAsync(ref new Uri(url));

    create_task(feedOp).then([this]  (SyndicationFeed^ feed)
    {
        m_TextBlock1->Text = feed->Title->Text;
    });
}
```

<span data-ttu-id="f0c3f-214">Gibt die Aufgabe nicht [**IAsyncAction**][IAsyncAction] oder [**IAsyncOperation**][IAsyncOperation] zurück, ist sie nicht apartmentfähig, und ihre Fortsetzungen werden standardmäßig im ersten verfügbaren Hintergrundthread ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-214">If a task doesn't return an [**IAsyncAction**][IAsyncAction] or [**IAsyncOperation**][IAsyncOperation], then it's not apartment-aware and, by default, its continuations are run on the first available background thread.</span></span>

<span data-ttu-id="f0c3f-215">Sie können den Standardthreadkontext für beide Aufgabenarten außer Kraft setzen, indem Sie die Überladung der [**task::then**][taskThen]-Methode verwenden, die einen [**task\_continuation\_context**](https://msdn.microsoft.com/library/windows/apps/xaml/hh749968.aspx)-Kontext verwendet.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-215">You can override the default thread context for either kind of task by using the overload of [**task::then**][taskThen] that takes a [**task\_continuation\_context**](https://msdn.microsoft.com/library/windows/apps/xaml/hh749968.aspx).</span></span> <span data-ttu-id="f0c3f-216">In manchen Fällen ist es zum Beispiel vorteilhaft, die Fortsetzung einer apartmentfähigen Aufgabe für einen Hintergrundthread zu planen.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-216">For example, in some cases, it might be desirable to schedule the continuation of an apartment-aware task on a background thread.</span></span> <span data-ttu-id="f0c3f-217">Dabei können Sie [**task\_continuation\_context::use\_arbitrary**][useArbitrary] übergeben, um die Vorgänge der Aufgabe für den nächsten verfügbaren Thread in einem Thread mit mehreren Apartments (Multithread-Apartment, MTA) zu planen.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-217">In such a case, you can pass [**task\_continuation\_context::use\_arbitrary**][useArbitrary] to schedule the task’s work on the next available thread in a multi-threaded apartment.</span></span> <span data-ttu-id="f0c3f-218">Dadurch wird die Leistung der Fortsetzung verbessert, da die entsprechenden Vorgänge nicht mit anderen Vorgängen im UI-Thread synchronisiert sein müssen.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-218">This can improve the performance of the continuation because its work doesn't have to be synchronized with other work that's happening on the UI thread.</span></span>

<span data-ttu-id="f0c3f-219">Das folgende Beispiel zeigt einen Fall, in dem es günstig ist, die [**task\_continuation\_context::use\_arbitrary**][useArbitrary]-Option anzugeben, und illustriert außerdem, in welcher Form der Standardfortsetzungskontext für die Synchronisierung gleichzeitig ablaufender Vorgänge in nicht threadsicheren Auflistungen nützlich ist.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-219">The following example demonstrates when it's useful to specify the [**task\_continuation\_context::use\_arbitrary**][useArbitrary] option, and it also shows how the default continuation context is useful for synchronizing concurrent operations on non-thread-safe collections.</span></span> <span data-ttu-id="f0c3f-220">In diesem Codebeispiel wird eine Schleife für eine Liste mit URLs für RSS-Feeds ausgeführt, und für jede URL wird zum Abrufen der Feeddaten ein asynchroner Vorgang gestartet.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-220">In this code, we loop through a list of URLs for RSS feeds, and for each URL, we start up an async operation to retrieve the feed data.</span></span> <span data-ttu-id="f0c3f-221">Die Reihenfolge, in der die Feeds abgerufen werden, können Sie nicht steuern, was jedoch auch nicht wichtig ist.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-221">We can’t control the order in which the feeds are retrieved, and we don't really care.</span></span> <span data-ttu-id="f0c3f-222">Mit dem Ende jedes [**RetrieveFeedAsync**](https://msdn.microsoft.com/library/windows/apps/BR210642)-Vorgangs akzeptiert die erste Fortsetzung das [**SyndicationFeed^**](https://msdn.microsoft.com/library/windows/apps/BR243485)-Objekt und initialisiert damit ein App-spezifisches `FeedData^`-Objekt.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-222">When each [**RetrieveFeedAsync**](https://msdn.microsoft.com/library/windows/apps/BR210642) operation completes, the first continuation accepts the [**SyndicationFeed^**](https://msdn.microsoft.com/library/windows/apps/BR243485) object and uses it to initialize an app-defined `FeedData^` object.</span></span> <span data-ttu-id="f0c3f-223">Da alle diese Vorgänge voneinander unabhängig sind, können wir durch Angabe des **task\_continuation\_context::use\_arbitrary**-Fortsetzungskontexts den Zeitaufwand verringern.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-223">Because each of these operations is independent from the others, we can potentially speed things up by specifying the **task\_continuation\_context::use\_arbitrary** continuation context.</span></span> <span data-ttu-id="f0c3f-224">Nach dem Initialisieren jedes `FeedData`-Objekts müssen wir dieses jedoch einem [**Vector**](https://msdn.microsoft.com/library/windows/apps/xaml/hh441570.aspx) hinzufügen– und das ist keine threadsichere Auflistung.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-224">However, after each `FeedData` object is initialized, we have to add it to a [**Vector**](https://msdn.microsoft.com/library/windows/apps/xaml/hh441570.aspx), which is not a thread-safe collection.</span></span> <span data-ttu-id="f0c3f-225">Aus diesem Grund erstellen wir eine Fortsetzung und geben [**task\_continuation\_context::use\_current**](https://msdn.microsoft.com/library/windows/apps/xaml/hh750085.aspx) an, damit alle Aufrufe von [**Append**](https://msdn.microsoft.com/library/windows/apps/BR206632) in demselben ASTA (Anwendungs-Single-Threaded-Apartment)-Kontext erfolgen.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-225">Therefore, we create a continuation and specify [**task\_continuation\_context::use\_current**](https://msdn.microsoft.com/library/windows/apps/xaml/hh750085.aspx) to ensure that all the calls to [**Append**](https://msdn.microsoft.com/library/windows/apps/BR206632) occur in the same Application Single-Threaded Apartment (ASTA) context.</span></span> <span data-ttu-id="f0c3f-226">[**task\_continuation\_context::use\_default**](https://msdn.microsoft.com/library/windows/apps/xaml/hh750085.aspx) müssen wir nicht direkt angeben, da es sich um den Standardkontext handelt. Wir tun es hier nur der Klarheit wegen.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-226">Because [**task\_continuation\_context::use\_default**](https://msdn.microsoft.com/library/windows/apps/xaml/hh750085.aspx) is the default context, we don’t have to specify it explicitly, but we do so here for the sake of clarity.</span></span>

``` cpp
#include <ppltasks.h>
void App::InitDataSource(Vector<Object^>^ feedList, vector<wstring> urls)
{
                using namespace concurrency;
    SyndicationClient^ client = ref new SyndicationClient();

    std::for_each(std::begin(urls), std::end(urls), [=,this] (std::wstring url)
    {
        // Create the async operation. feedOp is an
        // IAsyncOperationWithProgress<SyndicationFeed^, RetrievalProgress>^
        // but we don't handle progress in this example.

        auto feedUri = ref new Uri(ref new String(url.c_str()));
        auto feedOp = client->RetrieveFeedAsync(feedUri);

        // Create the task object and pass it the async operation.
        // SyndicationFeed^ is the type of the return value
        // that the feedOp operation will eventually produce.

        // Then, initialize a FeedData object by using the feed info. Each
        // operation is independent and does not have to happen on the
        // UI thread. Therefore, we specify use_arbitrary.
        create_task(feedOp).then([this]  (SyndicationFeed^ feed) -> FeedData^
        {
            return GetFeedData(feed);
        }, task_continuation_context::use_arbitrary())

        // Append the initialized FeedData object to the list
        // that is the data source for the items collection.
        // This all has to happen on the same thread.
        // By using the use_default context, we can append
        // safely to the Vector without taking an explicit lock.
        .then([feedList] (FeedData^ fd)
        {
            feedList->Append(fd);
            OutputDebugString(fd->Title->Data());
        }, task_continuation_context::use_default())

        // The last continuation serves as an error handler. The
        // call to get() will surface any exceptions that were raised
        // at any point in the task chain.
        .then( [this] (task<void> t)
        {
            try
            {
                t.get();
            }
            catch(Platform::InvalidArgumentException^ e)
            {
                //TODO handle error.
                OutputDebugString(e->Message->Data());
            }
        }); //end task chain

    }); //end std::for_each
}
```

<span data-ttu-id="f0c3f-227">Geschachtelte Aufgaben, bei denen es sich um neu erstellte Aufgaben in einer Fortsetzung handelt, erben nicht die Apartmentfähigkeit der ursprünglichen Aufgabe.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-227">Nested tasks, which are new tasks that are created inside a continuation, don't inherit apartment-awareness of the initial task.</span></span>

## <a name="handing-progress-updates"></a><span data-ttu-id="f0c3f-228">Behandeln von Statusaktualisierungen</span><span class="sxs-lookup"><span data-stu-id="f0c3f-228">Handing progress updates</span></span>
<span data-ttu-id="f0c3f-229">Methoden mit Unterstützung von [**IAsyncOperationWithProgress**](https://msdn.microsoft.com/library/windows/apps/br206594.aspx) oder [**IAsyncActionWithProgress**](https://msdn.microsoft.com/library/windows/apps/br206581.aspx) aktualisieren regelmäßig den Status eines laufenden Vorgangs, solange dieser nicht beendet ist.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-229">Methods that support [**IAsyncOperationWithProgress**](https://msdn.microsoft.com/library/windows/apps/br206594.aspx) or [**IAsyncActionWithProgress**](https://msdn.microsoft.com/library/windows/apps/br206581.aspx) provide progress updates periodically while the operation is in progress, before it completes.</span></span> <span data-ttu-id="f0c3f-230">Der Status wird dabei unabhängig von dem Konzept von Aufgaben und Fortsetzungen gemeldet.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-230">Progress reporting is independent from the notion of tasks and continuations.</span></span> <span data-ttu-id="f0c3f-231">Sie müssen nur den Delegaten für die [**Progress**](https://msdn.microsoft.com/library/windows/apps/br206594)-Eigenschaft des Objekts angeben.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-231">You just supply the delegate for the object’s [**Progress**](https://msdn.microsoft.com/library/windows/apps/br206594) property.</span></span> <span data-ttu-id="f0c3f-232">Eine typische Verwendung von Delegaten ist die Aktualisierung einer Statusleiste auf der Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="f0c3f-232">A typical use of the delegate is to update a progress bar in the UI.</span></span>

## <a name="related-topics"></a><span data-ttu-id="f0c3f-233">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="f0c3f-233">Related topics</span></span>
* [<span data-ttu-id="f0c3f-234">Erstellen von asynchronen Vorgängen in C++/CX für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="f0c3f-234">Creating Asynchronous Operations in C++/CX for UWP apps</span></span>](https://msdn.microsoft.com/library/hh750082)
* [<span data-ttu-id="f0c3f-235">Visual C++-Programmiersprachenreferenz</span><span class="sxs-lookup"><span data-stu-id="f0c3f-235">Visual C++ Language Reference</span></span>](http://msdn.microsoft.com/library/windows/apps/hh699871.aspx)
* <span data-ttu-id="f0c3f-236">[Asynchrone Programmierung][AsyncProgramming]</span><span class="sxs-lookup"><span data-stu-id="f0c3f-236">[Asynchronous Programming][AsyncProgramming]</span></span>
* <span data-ttu-id="f0c3f-237">[Aufgabenparallelität (Concurrency Runtime)][taskParallelism]</span><span class="sxs-lookup"><span data-stu-id="f0c3f-237">[Task Parallelism (Concurrency Runtime)][taskParallelism]</span></span>
* [<span data-ttu-id="f0c3f-238">concurrency::task</span><span class="sxs-lookup"><span data-stu-id="f0c3f-238">concurrency::task</span></span>](/cpp/parallel/concrt/reference/task-class)

<!-- LINKS -->
[AsyncProgramming]: <https://docs.microsoft.com/windows/uwp/threading-async/asynchronous-programming-universal-windows-platform-apps> "AsyncProgramming"
[concurrencyNamespace]: <https://docs.microsoft.com/cpp/parallel/concrt/reference/concurrency-namespace> "Concurrency Namespace"
[createTask]: <https://docs.microsoft.com/cpp/parallel/concrt/reference/concurrency-namespace-functions#create_task> "CreateTask"
[deleteAsync]: <https://msdn.microsoft.com/library/windows/apps/BR227199> "DeleteAsync"
[IAsyncAction]: <https://msdn.microsoft.com/library/windows/apps/windows.foundation.iasyncaction.aspx> "IAsyncAction"
[IAsyncOperation]: <https://msdn.microsoft.com/library/windows/apps/BR206598> "IAsyncOperation"
[IAsyncInfo]: <https://msdn.microsoft.com/library/windows/apps/BR206587> "IAsyncInfo"
[IAsyncInfoCancel]: <https://msdn.microsoft.com/library/windows/apps/windows.foundation.iasyncinfo.cancel> "IAsyncInfoCancel"
[taskCanceled]: <https://docs.microsoft.com/cpp/parallel/concrt/reference/task-canceled-class> "TaskCancelled"
[task-class]: <https://docs.microsoft.com/cpp/parallel/concrt/reference/task-class#get> "Task-Klasse"
[taskGet]: <https://msdn.microsoft.com/library/windows/apps/xaml/hh750017.aspx> "TaskGet"
[taskParallelism]: <https://docs.microsoft.com/cpp/parallel/concrt/task-parallelism-concurrency-runtime> "Aufgabenparallelität"
[taskThen]: <https://docs.microsoft.com/cpp/parallel/concrt/reference/task-class#then> "TaskThen"
[useArbitrary]: <https://msdn.microsoft.com/library/windows/apps/xaml/hh750036.aspx> "UseArbitrary"
