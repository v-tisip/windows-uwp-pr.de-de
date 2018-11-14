---
author: msatranjr
title: Erstellen einer Komponente für Windows-Runtime in C++/CX und deren Aufruf über JavaScript oder C#
description: In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Sie eine einfache Komponenten-DLL-Datei für Windows-Runtime erstellen, die von JavaScript, C# oder Visual Basic aufgerufen werden kann.
ms.assetid: 764CD9C6-3565-4DFF-88D7-D92185C7E452
ms.author: misatran
ms.date: 05/14/2018
ms.topic: article
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 8d56e220a65d0de261ab0cc64b8ac417e1f480eb
ms.sourcegitcommit: bdc40b08cbcd46fc379feeda3c63204290e055af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/08/2018
ms.locfileid: "6163536"
---
# <a name="walkthrough-creating-a-windows-runtime-component-in-ccx-and-calling-it-from-javascript-or-c"></a><span data-ttu-id="b6b0d-104">Exemplarische Vorgehensweise: Erstellen einer Komponente für Windows-Runtime in C++/CX und Aufrufen der Komponente über JavaScript oder C#</span><span class="sxs-lookup"><span data-stu-id="b6b0d-104">Walkthrough: Creating a Windows Runtime component in C++/CX, and calling it from JavaScript or C#</span></span>
> [!NOTE]
> <span data-ttu-id="b6b0d-105">In diesem Thema erhalten Sie Unterstützung bei der Verwaltung Ihrer C++/CX-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-105">This topic exists to help you maintain your C++/CX application.</span></span> <span data-ttu-id="b6b0d-106">Es wird jedoch empfohlen, dass Sie [C++/WinRT](../cpp-and-winrt-apis/intro-to-using-cpp-with-winrt.md) für neue Anwendungen nutzen.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-106">But we recommend that you use [C++/WinRT](../cpp-and-winrt-apis/intro-to-using-cpp-with-winrt.md) for new applications.</span></span> <span data-ttu-id="b6b0d-107">C++/WinRT ist eine vollständig standardisierte, moderne C++17 Sprachprojektion für Windows-Runtime-(WinRT)-APIs, die als headerdateibasierte Bibliothek implementiert ist und Ihnen einen erstklassigen Zugriff auf die moderne Windows-API bietet.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-107">C++/WinRT is an entirely standard modern C++17 language projection for Windows Runtime (WinRT) APIs, implemented as a header-file-based library, and designed to provide you with first-class access to the modern Windows API.</span></span> <span data-ttu-id="b6b0d-108">Informationen zum Erstellen einer Komponente für Windows-Runtime mit C++ / WinRT, finden Sie unter [Erstellen von Ereignissen in C++ / WinRT](../cpp-and-winrt-apis/author-events.md).</span><span class="sxs-lookup"><span data-stu-id="b6b0d-108">To learn how to create a Windows Runtime Component using C++/WinRT, see [Author events in C++/WinRT](../cpp-and-winrt-apis/author-events.md).</span></span>

<span data-ttu-id="b6b0d-109">In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Sie eine einfache DLL-Datei für eine Komponente für Windows-Runtime erstellen, die von JavaScript, C# oder Visual Basic aufgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-109">This walkthrough shows how to create a basic Windows Runtime Component DLL that's callable from JavaScript, C#, or Visual Basic.</span></span> <span data-ttu-id="b6b0d-110">Bevor Sie mit dieser exemplarischen Vorgehensweise beginnen, stellen Sie sicher, dass Sie Konzepte wie die abstrakte binäre Schnittstelle (ABI), Verweisklassen und Visual C++-Komponentenerweiterungen kennen, die das Verwenden von Verweisklassen vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-110">Before you begin this walkthrough, make sure that you understand concepts such as the Abstract Binary Interface (ABI), ref classes, and the Visual C++ Component Extensions that make working with ref classes easier.</span></span> <span data-ttu-id="b6b0d-111">Weitere Informationen finden Sie unter [Erstellen von Komponenten für Windows-Runtime in C++](creating-windows-runtime-components-in-cpp.md) und [Visual C++-Programmiersprachenreferenz (C++/CX)](https://msdn.microsoft.com/library/windows/apps/xaml/hh699871.aspx).</span><span class="sxs-lookup"><span data-stu-id="b6b0d-111">For more information, see [Creating Windows Runtime Components in C++](creating-windows-runtime-components-in-cpp.md) and [Visual C++ Language Reference (C++/CX)](https://msdn.microsoft.com/library/windows/apps/xaml/hh699871.aspx).</span></span>

## <a name="creating-the-c-component-dll"></a><span data-ttu-id="b6b0d-112">Erstellen der C++-Komponenten-DLL-Datei</span><span class="sxs-lookup"><span data-stu-id="b6b0d-112">Creating the C++ component DLL</span></span>
<span data-ttu-id="b6b0d-113">In diesem Beispiel erstellen wir zunächst das Komponentenprojekt. Sie können aber auch das JavaScript-Projekt zuerst erstellen.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-113">In this example, we create the component project first, but you could create the JavaScript project first.</span></span> <span data-ttu-id="b6b0d-114">Die Reihenfolge spielt keine Rolle.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-114">The order doesn’t matter.</span></span>

<span data-ttu-id="b6b0d-115">Beachten Sie, dass die Hauptklasse der Komponente Beispiele für Eigenschafts- und Methodendefinitionen sowie eine Ereignisdeklaration enthält.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-115">Notice that the main class of the component contains examples of property and method definitions, and an event declaration.</span></span> <span data-ttu-id="b6b0d-116">Diese werden nur aus Gründen der Anschaulichkeit bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-116">These are provided just to show you how it's done.</span></span> <span data-ttu-id="b6b0d-117">Sie sind nicht erforderlich, und in diesem Beispiel ersetzen wir den gesamten generierten Code durch unseren eigenen Code.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-117">They are not required, and in this example, we'll replace all of the generated code with our own code.</span></span>

## **<a name="to-create-the-c-component-project"></a><span data-ttu-id="b6b0d-118">So erstellen Sie das C++-Komponentenprojekt</span><span class="sxs-lookup"><span data-stu-id="b6b0d-118">To create the C++ component project</span></span>**
<span data-ttu-id="b6b0d-119">Klicken Sie in der Visual Studio-Menüleiste auf **Datei, Neu, Projekt**.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-119">On the Visual Studio menu bar, choose **File, New, Project**.</span></span>

<span data-ttu-id="b6b0d-120">Erweitern Sie im Dialogfeld **Neues Projekt** im linken Bereich **Visual C++**, und wählen Sie dann den Knoten für universelle Windows-Apps aus.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-120">In the **New Project** dialog box, in the left pane, expand **Visual C++** and then select the node for Universal Windows apps.</span></span>

<span data-ttu-id="b6b0d-121">Wählen Sie im mittleren Bereich **Komponente für Windows-Runtime** aus, und geben Sie dem Projekt den Namen „WinRT\_CPP“.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-121">In the center pane, select **Windows Runtime Component** and then name the project WinRT\_CPP.</span></span>

<span data-ttu-id="b6b0d-122">Klicken Sie auf die Schaltfläche **OK**.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-122">Choose the **OK** button.</span></span>

## **<a name="to-add-an-activatable-class-to-the-component"></a><span data-ttu-id="b6b0d-123">So fügen Sie der Komponente eine aktivierbare Klasse hinzu</span><span class="sxs-lookup"><span data-stu-id="b6b0d-123">To add an activatable class to the component</span></span>**
<span data-ttu-id="b6b0d-124">Eine aktivierbare Klasse kann vom Clientcode mithilfe eines **new**-Ausdrucks (**New** in Visual Basic oder **ref new** in C++) erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-124">An activatable class is one that client code can create by using a **new** expression (**New** in Visual Basic, or **ref new** in C++).</span></span> <span data-ttu-id="b6b0d-125">In der Komponente können Sie sie als **public ref class sealed** deklarieren.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-125">In your component, you declare it as **public ref class sealed**.</span></span> <span data-ttu-id="b6b0d-126">Die Class1.h- und CPP-Dateien verfügen bereits über eine Verweisklasse.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-126">In fact, the Class1.h and .cpp files already have a ref class.</span></span> <span data-ttu-id="b6b0d-127">Sie können den Namen ändern, aber in diesem Beispiel verwenden wir den Standardnamen – Class1.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-127">You can change the name, but in this example we’ll use the default name—Class1.</span></span> <span data-ttu-id="b6b0d-128">Sie können zusätzliche Verweisklassen oder Standardklassen in der Komponente definieren, falls sie benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-128">You can define additional ref classes or regular classes in your component if they are required.</span></span> <span data-ttu-id="b6b0d-129">Weitere Informationen zu Verweisklassen finden Sie unter [Typsystem (C++/CX)](https://msdn.microsoft.com/library/windows/apps/hh755822.aspx).</span><span class="sxs-lookup"><span data-stu-id="b6b0d-129">For more information about ref classes, see [Type System (C++/CX)](https://msdn.microsoft.com/library/windows/apps/hh755822.aspx).</span></span>

<span data-ttu-id="b6b0d-130">Fügen Sie diese \#include-Direktiven zu „Class1.h“ hinzu:</span><span class="sxs-lookup"><span data-stu-id="b6b0d-130">Add these \#include directives to Class1.h:</span></span>

```cpp
#include <collection.h>
#include <ppl.h>
#include <amp.h>
#include <amp_math.h>
```

<span data-ttu-id="b6b0d-131">„collection.h“ ist die Headerdatei für konkrete C++-Klassen wie die Platform::Collections::Vector-Klasse und die Platform::Collections::Map-Klasse, die sprachunabhängige, durch die Windows-Runtime definierte Schnittstellen implementieren.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-131">collection.h is the header file for C++ concrete classes such as the Platform::Collections::Vector class and the Platform::Collections::Map class, which implement language-neutral interfaces that are defined by the Windows Runtime.</span></span> <span data-ttu-id="b6b0d-132">Die AMP-Header werden verwendet, um Berechnungen auf der GPU auszuführen.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-132">The amp headers are used to run computations on the GPU.</span></span> <span data-ttu-id="b6b0d-133">Sie haben keine Windows-Runtime-Entsprechungen. Das ist in Ordnung, da sie privat sind.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-133">They have no Windows Runtime equivalents, and that’s fine because they are private.</span></span> <span data-ttu-id="b6b0d-134">Im Allgemeinen sollten Sie aus Leistungsgründen ISO-C++-Code und Standardbibliotheken intern innerhalb der Komponente verwenden. Nur die Windows-Runtime-Schnittstelle muss in Windows-Runtime-Typen ausgedrückt werden.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-134">In general, for performance reasons you should use ISO C++ code and standard libraries internally within the component; it’s just the Windows Runtime interface that must be expressed in Windows Runtime types.</span></span>

## <a name="to-add-a-delegate-at-namespace-scope"></a><span data-ttu-id="b6b0d-135">So fügen Sie einen Delegaten im Gültigkeitsbereich des Namespaces hinzu</span><span class="sxs-lookup"><span data-stu-id="b6b0d-135">To add a delegate at namespace scope</span></span>
<span data-ttu-id="b6b0d-136">Ein Delegat ist ein Konstrukt, das die Parameter und den Rückgabetyp für Methoden definiert.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-136">A delegate is a construct that defines the parameters and return type for methods.</span></span> <span data-ttu-id="b6b0d-137">Ein Ereignis ist eine Instanz eines bestimmten Delegattyps, und eine Ereignishandlermethode, die das Ereignis abonniert, muss über die Signatur verfügen, die im Delegat angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-137">An event is an instance of a particular delegate type, and any event handler method that subscribes to the event must have the signature that's specified in the delegate.</span></span> <span data-ttu-id="b6b0d-138">Der folgende Code definiert einen Delegattyp, der „int“ erhält und „void“ zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-138">The following code defines a delegate type that takes an int and returns void.</span></span> <span data-ttu-id="b6b0d-139">Der Code deklariert danach ein öffentliches Ereignis dieses Typs. Dadurch kann der Clientcode Methoden bereitstellen, die beim Auslösen des Ereignisses aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-139">Next the code declares a public event of this type; this enables client code to provide methods that are invoked when the event is fired.</span></span>

<span data-ttu-id="b6b0d-140">Fügen Sie die folgende Delegatdeklaration im Gültigkeitsbereich des Namespaces in „Class1.h“ unmittelbar vor der Class1-Deklaration hinzu.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-140">Add the following delegate declaration at namespace scope in Class1.h, just before the Class1 declaration.</span></span>

```cpp
public delegate void PrimeFoundHandler(int result);
```

<span data-ttu-id="b6b0d-141">Wenn der Code beim Einfügen in Visual Studio nicht korrekt ausgerichtet wird, drücken Sie STRG+K+D, um den Einzug für die gesamte Datei zu korrigieren.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-141">If the code isn’t lining up correctly when you paste it into Visual Studio, just press Ctrl+K+D to fix the indentation for the entire file.</span></span>

## <a name="to-add-the-public-members"></a><span data-ttu-id="b6b0d-142">So fügen Sie öffentliche Member hinzu.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-142">To add the public members</span></span>
<span data-ttu-id="b6b0d-143">Die Klasse stellt drei öffentliche Methoden und ein öffentliches Ereignis bereit.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-143">The class exposes three public methods and one public event.</span></span> <span data-ttu-id="b6b0d-144">Die erste Methode ist synchron, da sie immer sehr schnell ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-144">The first method is synchronous because it always executes very fast.</span></span> <span data-ttu-id="b6b0d-145">Da die anderen beiden Methoden einige Zeit in Anspruch nehmen können, sind sie asynchron, damit sie den UI-Thread nicht blockieren.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-145">Because the other two methods might take some time, they are asynchronous so that they don’t block the UI thread.</span></span> <span data-ttu-id="b6b0d-146">Diese Methoden geben IAsyncOperationWithProgress und IAsyncActionWithProgress zurück.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-146">These methods return IAsyncOperationWithProgress and IAsyncActionWithProgress.</span></span> <span data-ttu-id="b6b0d-147">„IAsyncOperationWithProgress“ definiert eine asynchrone Methode, die ein Ergebnis zurückgibt, und „IAsyncActionWithProgress“ definiert eine asynchrone Methode, die „void“ zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-147">The former defines an async method that returns a result, and the latter defines an async method that returns void.</span></span> <span data-ttu-id="b6b0d-148">Diese Schnittstellen ermöglichen auch, dass der Clientcode Updates zum Status des Vorgangs erhält.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-148">These interfaces also enable client code to receive updates on the progress of the operation.</span></span>

```cpp
public:

        // Synchronous method.
        Windows::Foundation::Collections::IVector<double>^  ComputeResult(double input);

        // Asynchronous methods
        Windows::Foundation::IAsyncOperationWithProgress<Windows::Foundation::Collections::IVector<int>^, double>^
            GetPrimesOrdered(int first, int last);
        Windows::Foundation::IAsyncActionWithProgress<double>^ GetPrimesUnordered(int first, int last);

        // Event whose type is a delegate "class"
        event PrimeFoundHandler^ primeFoundEvent;

```
## <a name="to-add-the-private-members"></a><span data-ttu-id="b6b0d-149">So fügen Sie private Member hinzu</span><span class="sxs-lookup"><span data-stu-id="b6b0d-149">To add the private members</span></span>
<span data-ttu-id="b6b0d-150">Die Klasse enthält drei private Member: zwei Hilfsmethoden für die numerischen Berechnungen und ein CoreDispatcher-Objekt, das verwendet wird, um die Ereignisaufrufe von Workerthreads zurück an den UI-Thread zu marshallen.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-150">The class contains three private members: two helper methods for the numeric computations and a CoreDispatcher object that’s used to marshal the event invocations from worker threads back to the UI thread.</span></span>

```cpp
private:
        bool is_prime(int n);
        Windows::UI::Core::CoreDispatcher^ m_dispatcher;
```

## <a name="to-add-the-header-and-namespace-directives"></a><span data-ttu-id="b6b0d-151">So fügen Sie die Header- und Namespacedirektiven hinzu</span><span class="sxs-lookup"><span data-stu-id="b6b0d-151">To add the header and namespace directives</span></span>
<span data-ttu-id="b6b0d-152">Fügen Sie in „Class1.cpp“ die folgenden #include-Direktiven hinzu:</span><span class="sxs-lookup"><span data-stu-id="b6b0d-152">In Class1.cpp, add these #include directives:</span></span>

```cpp
#include <ppltasks.h>
#include <concurrent_vector.h>
```

<span data-ttu-id="b6b0d-153">Fügen Sie jetzt diese using-Anweisungen hinzu, um die erforderlichen Namespaces abzurufen:</span><span class="sxs-lookup"><span data-stu-id="b6b0d-153">Now add these using statements to pull in the required namespaces:</span></span>

```cpp
using namespace concurrency;
using namespace Platform::Collections;
using namespace Windows::Foundation::Collections;
using namespace Windows::Foundation;
using namespace Windows::UI::Core;
```

## <a name="to-add-the-implementation-for-computeresult"></a><span data-ttu-id="b6b0d-154">So fügen Sie die Implementierung für ComputeResult hinzu</span><span class="sxs-lookup"><span data-stu-id="b6b0d-154">To add the implementation for ComputeResult</span></span>
<span data-ttu-id="b6b0d-155">Fügen Sie in „Class1.cpp“ die folgende Methodenimplementierung hinzu.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-155">In Class1.cpp, add the following method implementation.</span></span> <span data-ttu-id="b6b0d-156">Diese Methode wird synchron auf dem aufrufenden Thread ausgeführt, ist aber sehr schnell, da sie C++ AMP verwendet, um die Berechnung auf der GPU zu parallelisieren.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-156">This method executes synchronously on the calling thread, but it is very fast because it uses C++ AMP to parallelize the computation on the GPU.</span></span> <span data-ttu-id="b6b0d-157">Weitere Informationen finden Sie in der C++ AMP-Übersicht.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-157">For more information, see C++ AMP Overview.</span></span> <span data-ttu-id="b6b0d-158">Die Ergebnisse werden an einen konkreten Platform::Collections::Vector<T>-Typ angefügt, der bei der Rückgabe implizit in einen Windows::Foundation::Collections::IVector<T>-Typ konvertiert wird.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-158">The results are appended to a Platform::Collections::Vector<T> concrete type, which is implicitly converted to a Windows::Foundation::Collections::IVector<T> when it is returned.</span></span>

```cpp
//Public API
IVector<double>^ Class1::ComputeResult(double input)
{
    // Implement your function in ISO C++ or
    // call into your C++ lib or DLL here. This example uses AMP.
    float numbers[] = { 1.0, 10.0, 60.0, 100.0, 600.0, 10000.0 };
    array_view<float, 1> logs(6, numbers);

    // See http://msdn.microsoft.com/en-us/library/hh305254.aspx
    parallel_for_each(
        logs.extent,
        [=] (index<1> idx) restrict(amp)
    {
        logs[idx] = concurrency::fast_math::log10(logs[idx]);
    }
    );

    // Return a Windows Runtime-compatible type across the ABI
    auto res = ref new Vector<double>();
    int len = safe_cast<int>(logs.extent.size());
    for(int i = 0; i < len; i++)
    {      
        res->Append(logs[i]);
    }

    // res is implicitly cast to IVector<double>
    return res;
}
```
## <a name="to-add-the-implementation-for-getprimesordered-and-its-helper-method"></a><span data-ttu-id="b6b0d-159">So fügen Sie die Implementierung für „GetPrimesOrdered“ und die Hilfsmethode hinzu</span><span class="sxs-lookup"><span data-stu-id="b6b0d-159">To add the implementation for GetPrimesOrdered and its helper method</span></span>
<span data-ttu-id="b6b0d-160">Fügen Sie die Implementierungen für „GetPrimesOrdered“ und die Hilfsmethode „is_prime“ in „Class1.cpp“ hinzu.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-160">In Class1.cpp, add the implementations for GetPrimesOrdered and the is_prime helper method.</span></span> <span data-ttu-id="b6b0d-161">„GetPrimesOrdered“ verwendet eine cConcurrent_vector-Klasse und eine parallel_for-Funktionsschleife zur Aufteilung der Arbeit und um die maximalen Ressourcen des Computers zu verwenden, auf dem das Programm ausgeführt wird, um Ergebnisse zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-161">GetPrimesOrdered uses a concurrent_vector class and a parallel_for function loop to divide up the work and use the maximum resources of the computer on which the program is running to produce results.</span></span> <span data-ttu-id="b6b0d-162">Nachdem die Ergebnisse berechnet, gespeichert und sortiert wurden, werden sie einem Platform::Collections::Vector<T>-Typ hinzugefügt und als „Windows::Foundation::Collections::IVector<T>“ an den Clientcode zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-162">After the results are computed, stored, and sorted, they are added to a Platform::Collections::Vector<T> and returned as Windows::Foundation::Collections::IVector<T> to client code.</span></span>

<span data-ttu-id="b6b0d-163">Beachten Sie den Code für den Statusbericht, der es dem Client ermöglicht, den Benutzer durch eine Statusanzeige oder ein anderes UI-Element darüber zu informieren, wie lange der Vorgang noch dauern wird.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-163">Notice the code for the progress reporter, which enables the client to hook up a progress bar or other UI to show the user how much longer the operation is going to take.</span></span> <span data-ttu-id="b6b0d-164">Statusberichte sind allerdings nicht kostenlos.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-164">Progress reporting has a cost.</span></span> <span data-ttu-id="b6b0d-165">Ein Ereignis muss auf der Komponentenseite ausgelöst und im UI-Thread behandelt werden, und der Statuswert muss bei jeder Iteration gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-165">An event must be fired on the component side and handled on the UI thread, and the progress value must be stored on each iteration.</span></span> <span data-ttu-id="b6b0d-166">Eine Möglichkeit, die Kosten zu minimieren, ist das Begrenzen der Häufigkeit, mit der ein Statusereignis ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-166">One way to minimize the cost is by limiting the frequency at which a progress event is fired.</span></span> <span data-ttu-id="b6b0d-167">Wenn die Kosten weiterhin unerschwinglich sind oder Sie die Länge des Vorgangs nicht einschätzen können, können Sie einen Statusring verwenden, der anzeigt, dass ein Vorgang ausgeführt wird, der aber nicht die restliche Zeit bis zum Abschluss anzeigt.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-167">If the cost is still prohibitive, or if you can't estimate the length of the operation, then consider using a progress ring, which shows that an operation is in progress but doesn't show time remaining until completion.</span></span>

```cpp
// Determines whether the input value is prime.
bool Class1::is_prime(int n)
{
    if (n < 2)
        return false;
    for (int i = 2; i < n; ++i)
    {
        if ((n % i) == 0)
            return false;
    }
    return true;
}

// This method computes all primes, orders them, then returns the ordered results.
IAsyncOperationWithProgress<IVector<int>^, double>^ Class1::GetPrimesOrdered(int first, int last)
{
    return create_async([this, first, last]
    (progress_reporter<double> reporter) -> IVector<int>^ {
        // Ensure that the input values are in range.
        if (first < 0 || last < 0) {
            throw ref new InvalidArgumentException();
        }
        // Perform the computation in parallel.
        concurrent_vector<int> primes;
        long operation = 0;
        long range = last - first + 1;
        double lastPercent = 0.0;

        parallel_for(first, last + 1, [this, &primes, &operation,
            range, &lastPercent, reporter](int n) {

                // Increment and store the number of times the parallel
                // loop has been called on all threads combined. There
                // is a performance cost to maintaining a count, and
                // passing the delegate back to the UI thread, but it's
                // necessary if we want to display a determinate progress
                // bar that goes from 0 to 100%. We can avoid the cost by
                // setting the ProgressBar IsDeterminate property to false
                // or by using a ProgressRing.
                if(InterlockedIncrement(&operation) % 100 == 0)
                {
                    reporter.report(100.0 * operation / range);
                }

                // If the value is prime, add it to the local vector.
                if (is_prime(n)) {
                    primes.push_back(n);
                }
        });

        // Sort the results.
        std::sort(begin(primes), end(primes), std::less<int>());        
        reporter.report(100.0);

        // Copy the results to a Vector object, which is
        // implicitly converted to the IVector return type. IVector
        // makes collections of data available to other
        // Windows Runtime components.
        return ref new Vector<int>(primes.begin(), primes.end());
    });
}
```

## <a name="to-add-the-implementation-for-getprimesunordered"></a><span data-ttu-id="b6b0d-168">So fügen Sie die Implementierung für „GetPrimesUnordered“ hinzu</span><span class="sxs-lookup"><span data-stu-id="b6b0d-168">To add the implementation for GetPrimesUnordered</span></span>
<span data-ttu-id="b6b0d-169">Der letzte Schritt zum Erstellen der C++-Komponente ist das Hinzufügen der Implementierung für „GetPrimesUnordered“ in „Class1.cpp“.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-169">The last step to create the C++ component is to add the implementation for the GetPrimesUnordered in Class1.cpp.</span></span> <span data-ttu-id="b6b0d-170">Diese Methode gibt jedes einzelne Ergebnis sofort beim Auffinden zurück – ohne zu warten, bis alle Ergebnisse gefunden wurden.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-170">This method returns each result as it is found, without waiting until all results are found.</span></span> <span data-ttu-id="b6b0d-171">Jedes Ergebnis wird im Ereignishandler zurückgegeben und auf der Benutzeroberfläche in Echtzeit angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-171">Each result is returned in the event handler and displayed on the UI in real time.</span></span> <span data-ttu-id="b6b0d-172">Beachten Sie auch hier, dass ein Statusbericht verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-172">Again, notice that a progress reporter is used.</span></span> <span data-ttu-id="b6b0d-173">Diese Methode verwendet auch die Hilfsmethode „is_prime“.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-173">This method also uses the is_prime helper method.</span></span>

```cpp
// This method returns no value. Instead, it fires an event each time a
// prime is found, and passes the prime through the event.
// It also passes progress info.
IAsyncActionWithProgress<double>^ Class1::GetPrimesUnordered(int first, int last)
{

    auto window = Windows::UI::Core::CoreWindow::GetForCurrentThread();
    m_dispatcher = window->Dispatcher;


    return create_async([this, first, last](progress_reporter<double> reporter) {

        // Ensure that the input values are in range.
        if (first < 0 || last < 0) {
            throw ref new InvalidArgumentException();
        }

        // In this particular example, we don't actually use this to store
        // results since we pass results one at a time directly back to
        // UI as they are found. However, we have to provide this variable
        // as a parameter to parallel_for.
        concurrent_vector<int> primes;
        long operation = 0;
        long range = last - first + 1;
        double lastPercent = 0.0;

        // Perform the computation in parallel.
        parallel_for(first, last + 1,
            [this, &primes, &operation, range, &lastPercent, reporter](int n)
        {
            // Store the number of times the parallel loop has been called  
            // on all threads combined. See comment in previous method.
            if(InterlockedIncrement(&operation) % 100 == 0)
            {
                reporter.report(100.0 * operation / range);
            }

            // If the value is prime, pass it immediately to the UI thread.
            if (is_prime(n))
            {                
                // Since this code is probably running on a worker
                // thread, and we are passing the data back to the
                // UI thread, we have to use a CoreDispatcher object.
                m_dispatcher->RunAsync( CoreDispatcherPriority::Normal,
                    ref new DispatchedHandler([this, n, operation, range]()
                {
                    this->primeFoundEvent(n);

                }, Platform::CallbackContext::Any));

            }
        });
        reporter.report(100.0);
    });
}
```

## <a name="creating-a-javascript-client-app"></a><span data-ttu-id="b6b0d-174">Erstellen einer JavaScript-Client-App</span><span class="sxs-lookup"><span data-stu-id="b6b0d-174">Creating a JavaScript client app</span></span>
<span data-ttu-id="b6b0d-175">Wenn Sie nur einen C#-Client erstellen möchten, können Sie diesen Abschnitt überspringen.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-175">If you just want to create a C# client, you can skip this section.</span></span>

## <a name="to-create-a-javascript-project"></a><span data-ttu-id="b6b0d-176">So erstellen Sie ein JavaScript-Projekt</span><span class="sxs-lookup"><span data-stu-id="b6b0d-176">To create a JavaScript project</span></span>
<span data-ttu-id="b6b0d-177">Öffnen Sie im Projektmappen-Explorer das Kontextmenü des Lösungsknotens, und wählen Sie **Hinzufügen, Neues Projekt** aus.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-177">In Solution Explorer, open the shortcut menu for the Solution node and choose **Add, New Project**.</span></span>

<span data-ttu-id="b6b0d-178">Erweitern Sie „JavaScript“ (kann unter **Andere Sprachen** verschachtelt sein), und wählen Sie **Leere App (universelle Windows-App)** aus.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-178">Expand JavaScript (it might be nested under **Other Languages**) and choose **Blank App (Universal Windows)**.</span></span>

<span data-ttu-id="b6b0d-179">Übernehmen Sie den Standardnamen – App1 – durch Auswählen der Schaltfläche **OK**.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-179">Accept the default name—App1—by choosing the **OK** button.</span></span>

<span data-ttu-id="b6b0d-180">Öffnen Sie das Kontextmenü für den Projektknoten „App1“, und wählen Sie **Als Startprojekt festlegen** aus.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-180">Open the shortcut menu for the App1 project node and choose **Set as Startup Project**.</span></span>

<span data-ttu-id="b6b0d-181">Fügen Sie einen Projektverweis zu WinRT_CPP hinzu:</span><span class="sxs-lookup"><span data-stu-id="b6b0d-181">Add a project reference to WinRT_CPP:</span></span>

<span data-ttu-id="b6b0d-182">Öffnen Sie dann das Kontextmenü für den Knoten „Verweise“, und wählen Sie **Verweis hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-182">Open the shortcut menu for the References node and choose **Add Reference**.</span></span>

<span data-ttu-id="b6b0d-183">Wählen Sie im linken Bereich des Dialogfelds „Verweis-Manager“ die Option **Projekte** aus, und wählen Sie dann **Lösung** aus.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-183">In the left pane of the References Manager dialog box, select **Projects** and then select **Solution**.</span></span>

<span data-ttu-id="b6b0d-184">Wählen Sie im mittleren Bereich „WinRT_CPP“ und dann die Schaltfläche **OK** aus.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-184">In the center pane, select WinRT_CPP and then choose the **OK** button</span></span>

## <a name="to-add-the-html-that-invokes-the-javascript-event-handlers"></a><span data-ttu-id="b6b0d-185">So fügen Sie den HTML-Code hinzu, der die JavaScript-Ereignishandler aufruft</span><span class="sxs-lookup"><span data-stu-id="b6b0d-185">To add the HTML that invokes the JavaScript event handlers</span></span>
<span data-ttu-id="b6b0d-186">Fügen Sie diesen HTML-Code in den <body>-Knoten der Seite „default.HTML“ ein:</span><span class="sxs-lookup"><span data-stu-id="b6b0d-186">Paste this HTML into the <body> node of the default.html page:</span></span>

```HTML
<div id="LogButtonDiv">
     <button id="logButton">Logarithms using AMP</button>
 </div>
 <div id="LogResultDiv">
     <p id="logResult"></p>
 </div>
 <div id="OrderedPrimeButtonDiv">
     <button id="orderedPrimeButton">Primes using parallel_for with sort</button>
 </div>
 <div id="OrderedPrimeProgress">
     <progress id="OrderedPrimesProgressBar" value="0" max="100"></progress>
 </div>
 <div id="OrderedPrimeResultDiv">
     <p id="orderedPrimes">
         Primes found (ordered):
     </p>
 </div>
 <div id="UnorderedPrimeButtonDiv">
     <button id="ButtonUnordered">Primes returned as they are produced.</button>
 </div>
 <div id="UnorderedPrimeDiv">
     <progress id="UnorderedPrimesProgressBar" value="0" max="100"></progress>
 </div>
 <div id="UnorderedPrime">
     <p id="unorderedPrimes">
         Primes found (unordered):
     </p>
 </div>
 <div id="ClearDiv">
     <button id="Button_Clear">Clear</button>
 </div>
```

## <a name="to-add-styles"></a><span data-ttu-id="b6b0d-187">So fügen Sie Formate hinzu</span><span class="sxs-lookup"><span data-stu-id="b6b0d-187">To add styles</span></span>
<span data-ttu-id="b6b0d-188">Entfernen Sie in „default.css“ das body-Format, und fügen Sie dann diese Formate hinzu:</span><span class="sxs-lookup"><span data-stu-id="b6b0d-188">In default.css, remove the body style and then add these styles:</span></span>

```css
#LogButtonDiv {
border: orange solid 1px;
-ms-grid-row: 1; /* default is 1 */
-ms-grid-column: 1; /* default is 1 */
}
#LogResultDiv {
background: black;
border: red solid 1px;
-ms-grid-row: 1;
-ms-grid-column: 2;
}
#UnorderedPrimeButtonDiv, #OrderedPrimeButtonDiv {
border: orange solid 1px;
-ms-grid-row: 2;   
-ms-grid-column:1;
}
#UnorderedPrimeProgress, #OrderedPrimeProgress {
border: red solid 1px;
-ms-grid-column-span: 2;
height: 40px;
}
#UnorderedPrimeResult, #OrderedPrimeResult {
border: red solid 1px;
font-size:smaller;
-ms-grid-row: 2;
-ms-grid-column: 3;
-ms-overflow-style:scrollbar;
}
```

## <a name="to-add-the-javascript-event-handlers-that-call-into-the-component-dll"></a><span data-ttu-id="b6b0d-189">So fügen Sie die JavaScript-Ereignishandler hinzu, die die Komponenten-DLL aufrufen</span><span class="sxs-lookup"><span data-stu-id="b6b0d-189">To add the JavaScript event handlers that call into the component DLL</span></span>
<span data-ttu-id="b6b0d-190">Fügen Sie am Ende der Datei „default.js“ die folgenden Funktionen hinzu.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-190">Add the following functions at the end of the default.js file.</span></span> <span data-ttu-id="b6b0d-191">Diese Funktionen werden aufgerufen, wenn die Schaltflächen auf der Hauptseite ausgewählt werden.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-191">These functions are called when the buttons on the main page are chosen.</span></span> <span data-ttu-id="b6b0d-192">Beachten Sie, wie JavaScript die C++-Klasse aktiviert und dann ihre Methoden aufruft und die Rückgabewerte zum Auffüllen der HTML-Beschriftungen verwendet.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-192">Notice how JavaScript activates the C++ class, and then calls its methods and uses the return values to populate the HTML labels.</span></span>

```JavaScript
var nativeObject = new WinRT_CPP.Class1();

function LogButton_Click() {

    var val = nativeObject.computeResult(0);
    var result = "";

    for (i = 0; i < val.length; i++) {
        result += val[i] + "<br/>";
    }

    document.getElementById('logResult').innerHTML = result;
}

function ButtonOrdered_Click() {
    document.getElementById('orderedPrimes').innerHTML = "Primes found (ordered): ";

    nativeObject.getPrimesOrdered(2, 10000).then(
        function (v) {
            for (var i = 0; i < v.length; i++)
                document.getElementById('orderedPrimes').innerHTML += v[i] + " ";
        },
        function (error) {
            document.getElementById('orderedPrimes').innerHTML += " " + error.description;
        },
        function (p) {
            var progressBar = document.getElementById("OrderedPrimesProgressBar");
            progressBar.value = p;
        });
}

function ButtonUnordered_Click() {
    document.getElementById('unorderedPrimes').innerHTML = "Primes found (unordered): ";
    nativeObject.onprimefoundevent = handler_unordered;

    nativeObject.getPrimesUnordered(2, 10000).then(
        function () { },
        function (error) {
            document.getElementById("unorderedPrimes").innerHTML += " " + error.description;
        },
        function (p) {
            var progressBar = document.getElementById("UnorderedPrimesProgressBar");
            progressBar.value = p;
        });
}

var handler_unordered = function (n) {
    document.getElementById('unorderedPrimes').innerHTML += n.target.toString() + " ";
};

function ButtonClear_Click() {

    document.getElementById('logResult').innerHTML = "";
    document.getElementById("unorderedPrimes").innerHTML = "";
    document.getElementById('orderedPrimes').innerHTML = "";
    document.getElementById("UnorderedPrimesProgressBar").value = 0;
    document.getElementById("OrderedPrimesProgressBar").value = 0;
}
```

<span data-ttu-id="b6b0d-193">Fügen Sie Code zum Hinzufügen von Ereignis-Listenern durch Ersetzen des vorhandenen Aufrufs von „WinJS.UI.processAll“ in „app.onactivated“ in „default.js“ durch den folgenden Code hinzu, der die Ereignisregistrierung in einem „then“-Block implementiert.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-193">Add code to add the event listeners by replacing the existing call to WinJS.UI.processAll in app.onactivated in default.js with the following code that implements event registration in a then block.</span></span> <span data-ttu-id="b6b0d-194">Eine ausführliche Erläuterung dazu finden Sie unter Erstellen der App „Hello World“ (JS).</span><span class="sxs-lookup"><span data-stu-id="b6b0d-194">For a detailed explanation of this, see Create a "Hello World" app (JS).</span></span>

```JavaScript
args.setPromise(WinJS.UI.processAll().then( function completed() {
    var logButton = document.getElementById("logButton");
    logButton.addEventListener("click", LogButton_Click, false);
    var orderedPrimeButton = document.getElementById("orderedPrimeButton");
    orderedPrimeButton.addEventListener("click", ButtonOrdered_Click, false);
    var buttonUnordered = document.getElementById("ButtonUnordered");
    buttonUnordered.addEventListener("click", ButtonUnordered_Click, false);
    var buttonClear = document.getElementById("Button_Clear");
    buttonClear.addEventListener("click", ButtonClear_Click, false);
}));
```

<span data-ttu-id="b6b0d-195">Drücken Sie F5, um die App auszuführen.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-195">Press F5 to run the app.</span></span>

## <a name="creating-a-c-client-app"></a><span data-ttu-id="b6b0d-196">Erstellen einer C#-Client-App</span><span class="sxs-lookup"><span data-stu-id="b6b0d-196">Creating a C# client app</span></span>

## <a name="to-create-a-c-project"></a><span data-ttu-id="b6b0d-197">So erstellen Sie ein C#-Projekt</span><span class="sxs-lookup"><span data-stu-id="b6b0d-197">To create a C# project</span></span>
<span data-ttu-id="b6b0d-198">Öffnen Sie im Projektmappen-Explorer das Kontextmenü für den Lösungsknoten, und wählen Sie dann **Hinzufügen, Neues Projekt** aus.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-198">In Solution Explorer, open the shortcut menu for the Solution node and then choose **Add, New Project**.</span></span>

<span data-ttu-id="b6b0d-199">Erweitern Sie Visual C# (kann unter **Andere Sprachen** verschachtelt sein), wählen Sie **Windows** und dann **universelle** im linken Bereich, und schließlich **Leere App** im mittleren Bereich aus.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-199">Expand Visual C# (it might be nested under **Other Languages**), select **Windows** and then **Universal** in the left pane, and then select **Blank App** in the middle pane.</span></span>

<span data-ttu-id="b6b0d-200">Nennen Sie diese App „CS_Client“, und wählen Sie dann die Schaltfläche **OK** aus.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-200">Name this app CS_Client and then choose the **OK** button.</span></span>

<span data-ttu-id="b6b0d-201">Öffnen Sie das Kontextmenü für den Projektknoten „CS_Client“, und wählen Sie **Als Startprojekt festlegen** aus.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-201">Open the shortcut menu for the CS_Client project node and choose **Set as Startup Project**.</span></span>

<span data-ttu-id="b6b0d-202">Fügen Sie einen Projektverweis zu WinRT_CPP hinzu:</span><span class="sxs-lookup"><span data-stu-id="b6b0d-202">Add a project reference to WinRT_CPP:</span></span>

<span data-ttu-id="b6b0d-203">Öffnen Sie dann das Kontextmenü für den Knoten **Verweise**, und wählen Sie **Verweis hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-203">Open the shortcut menu for the **References** node and choose **Add Reference**.</span></span>

<span data-ttu-id="b6b0d-204">Wählen Sie im linken Bereich des Dialogfelds **Verweis-Manager** die Option **Projekte** aus, und wählen Sie dann **Lösung** aus.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-204">In the left pane of the **References Manager** dialog box, select **Projects** and then select **Solution**.</span></span>

<span data-ttu-id="b6b0d-205">Wählen Sie im mittleren Bereich „WinRT_CPP“ und dann die Schaltfläche **OK** aus.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-205">In the center pane, select WinRT_CPP and then choose the **OK** button.</span></span>

## <a name="to-add-the-xaml-that-defines-the-user-interface"></a><span data-ttu-id="b6b0d-206">So fügen Sie den XAML-Code hinzu, der die Benutzeroberfläche definiert</span><span class="sxs-lookup"><span data-stu-id="b6b0d-206">To add the XAML that defines the user interface</span></span>
<span data-ttu-id="b6b0d-207">Kopieren Sie den folgenden Code in das Grid-Element in „MainPage.xaml“.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-207">Copy the following code into the Grid element in MainPage.xaml.</span></span>

```xaml
<ScrollViewer>
            <StackPanel Width="1400">

                <Button x:Name="Button1" Width="340" Height="50"  Margin="0,20,20,20" Content="Synchronous Logarithm Calculation" FontSize="16" Click="Button1_Click_1"/>
                <TextBlock x:Name="Result1" Height="100" FontSize="14"></TextBlock>
            <Button x:Name="PrimesOrderedButton" Content="Prime Numbers Ordered" FontSize="16" Width="340" Height="50" Margin="0,20,20,20" Click="PrimesOrderedButton_Click_1"></Button>
            <ProgressBar x:Name="PrimesOrderedProgress" IsIndeterminate="false" Height="40"></ProgressBar>
                <TextBlock x:Name="PrimesOrderedResult" MinHeight="100" FontSize="10" TextWrapping="Wrap"></TextBlock>
            <Button x:Name="PrimesUnOrderedButton" Width="340" Height="50" Margin="0,20,20,20" Click="PrimesUnOrderedButton_Click_1" Content="Prime Numbers Unordered" FontSize="16"></Button>
            <ProgressBar x:Name="PrimesUnOrderedProgress" IsIndeterminate="false" Height="40" ></ProgressBar>
            <TextBlock x:Name="PrimesUnOrderedResult" MinHeight="100" FontSize="10" TextWrapping="Wrap"></TextBlock>

            <Button x:Name="Clear_Button" Content="Clear" HorizontalAlignment="Left" Margin="0,20,20,20" VerticalAlignment="Top" Width="341" Click="Clear_Button_Click" FontSize="16"/>
        </StackPanel>
</ScrollViewer>
```

## <a name="to-add-the-event-handlers-for-the-buttons"></a><span data-ttu-id="b6b0d-208">So fügen Sie die Ereignishandler für die Schaltflächen hinzu</span><span class="sxs-lookup"><span data-stu-id="b6b0d-208">To add the event handlers for the buttons</span></span>
<span data-ttu-id="b6b0d-209">Öffnen Sie die Datei „MainPage.xaml.cs“ im Projektmappen-Explorer.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-209">In Solution Explorer, open MainPage.xaml.cs.</span></span> <span data-ttu-id="b6b0d-210">(Die Datei befindet sich möglicherweise unter „MainPage.xaml“.) Fügen Sie eine using-Direktive für „System.Text“ und dann den Ereignishandler für die Logarithmusberechnung in der „MainPage“-Klasse hinzu.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-210">(The file might be nested under MainPage.xaml.) Add a using directive for System.Text, and then add the event handler for the Logarithm calculation in the MainPage class.</span></span>

```csharp
private void Button1_Click_1(object sender, RoutedEventArgs e)
{
    // Create the object
    var nativeObject = new WinRT_CPP.Class1();

    // Call the synchronous method. val is an IList that
    // contains the results.
    var val = nativeObject.ComputeResult(0);
    StringBuilder result = new StringBuilder();
    foreach (var v in val)
    {
        result.Append(v).Append(System.Environment.NewLine);
    }
    this.Result1.Text = result.ToString();
}
```

<span data-ttu-id="b6b0d-211">Fügen Sie den Ereignishandler für das sortierte Ergebnis hinzu:</span><span class="sxs-lookup"><span data-stu-id="b6b0d-211">Add the event handler for the ordered result:</span></span>

```csharp
async private void PrimesOrderedButton_Click_1(object sender, RoutedEventArgs e)
{
    var nativeObject = new WinRT_CPP.Class1();

    StringBuilder sb = new StringBuilder();
    sb.Append("Primes found (ordered): ");

    PrimesOrderedResult.Text = sb.ToString();

    // Call the asynchronous method
    var asyncOp = nativeObject.GetPrimesOrdered(2, 100000);

    // Before awaiting, provide a lambda or named method
    // to handle the Progress event that is fired at regular
    // intervals by the asyncOp object. This handler updates
    // the progress bar in the UI.
    asyncOp.Progress = (asyncInfo, progress) =>
        {
            PrimesOrderedProgress.Value = progress;
        };

    // Wait for the operation to complete
    var asyncResult = await asyncOp;

    // Convert the results to strings
    foreach (var result in asyncResult)
    {
        sb.Append(result).Append(" ");
    }

    // Display the results
    PrimesOrderedResult.Text = sb.ToString();
}
```

<span data-ttu-id="b6b0d-212">Fügen Sie den Ereignishandler für das unsortierte Ergebnis und für die Schaltfläche hinzu, die die Ergebnisse löscht, sodass Sie den Code erneut ausführen können.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-212">Add the event handler for the unordered result, and for the button that clears the results so that you can run the code again.</span></span>

```csharp
private void PrimesUnOrderedButton_Click_1(object sender, RoutedEventArgs e)
{
    var nativeObject = new WinRT_CPP.Class1();

    StringBuilder sb = new StringBuilder();
    sb.Append("Primes found (unordered): ");
    PrimesUnOrderedResult.Text = sb.ToString();

    // primeFoundEvent is a user-defined event in nativeObject
    // It passes the results back to this thread as they are produced
    // and the event handler that we define here immediately displays them.
    nativeObject.primeFoundEvent += (n) =>
    {
        sb.Append(n.ToString()).Append(" ");
        PrimesUnOrderedResult.Text = sb.ToString();
    };

    // Call the async method.
    var asyncResult = nativeObject.GetPrimesUnordered(2, 100000);

    // Provide a handler for the Progress event that the asyncResult
    // object fires at regular intervals. This handler updates the progress bar.
    asyncResult.Progress += (asyncInfo, progress) =>
        {
            PrimesUnOrderedProgress.Value = progress;
        };
}

private void Clear_Button_Click(object sender, RoutedEventArgs e)
{
    PrimesOrderedProgress.Value = 0;
    PrimesUnOrderedProgress.Value = 0;
    PrimesUnOrderedResult.Text = "";
    PrimesOrderedResult.Text = "";
    Result1.Text = "";
}
```

## <a name="running-the-app"></a><span data-ttu-id="b6b0d-213">Ausführen der App</span><span class="sxs-lookup"><span data-stu-id="b6b0d-213">Running the app</span></span>
<span data-ttu-id="b6b0d-214">Wählen Sie das C#-Projekt oder das JavaScript-Projekt als Startprojekt aus, indem Sie das Kontextmenü für den Projektknoten im Projektmappen-Explorer öffnen und **Als Startprojekt festlegen** auswählen.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-214">Select either the C# project or JavaScript project as the startup project by opening the shortcut menu for the project node in Solution Explorer and choosing **Set As Startup Project**.</span></span> <span data-ttu-id="b6b0d-215">Drücken Sie dann F5 zum Ausführen mit Debugging oder STRG+F5 zum Ausführen ohne Debugging.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-215">Then press F5 to run with debugging, or Ctrl+F5 to run without debugging.</span></span>

## <a name="inspecting-your-component-in-object-browser-optional"></a><span data-ttu-id="b6b0d-216">Untersuchen der Komponente im Objektkatalog (optional)</span><span class="sxs-lookup"><span data-stu-id="b6b0d-216">Inspecting your component in Object Browser (optional)</span></span>
<span data-ttu-id="b6b0d-217">Im Objektkatalog können Sie alle Windows-Runtime-Typen untersuchen, die in WINMD-Dateien definiert werden.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-217">In Object Browser, you can inspect all Windows Runtime types that are defined in .winmd files.</span></span> <span data-ttu-id="b6b0d-218">Dazu zählen die Typen im Plattformnamespace und Standardnamespace.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-218">This includes the types in the Platform namespace and the default namespace.</span></span> <span data-ttu-id="b6b0d-219">Da die Typen im „Platform::Collections“-Namespace aber in der Headerdatei „collections.h“ und nicht in einer WINMD-Datei definiert werden, werden sie nicht im Objektkatalog angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-219">However, because the types in the Platform::Collections namespace are defined in the header file collections.h, not in a winmd file, they don’t appear in Object Browser.</span></span>

## **<a name="to-inspect-a-component"></a><span data-ttu-id="b6b0d-220">So untersuchen Sie eine Komponente</span><span class="sxs-lookup"><span data-stu-id="b6b0d-220">To inspect a component</span></span>**
<span data-ttu-id="b6b0d-221">Wählen Sie auf der Menüleiste **Ansicht, Objektkatalog** (STRG+ALT+J) aus.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-221">On the menu bar, choose **View, Object Browser** (Ctrl+Alt+J).</span></span>

<span data-ttu-id="b6b0d-222">Erweitern Sie im linken Bereich des Objektkatalogs den Knoten „WinRT\_CPP“ zum Anzeigen von Typen und Methoden, die in der Komponente definiert werden.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-222">In the left pane of the Object Browser, expand the WinRT\_CPP node to show the types and methods that are defined on your component.</span></span>

## <a name="debugging-tips"></a><span data-ttu-id="b6b0d-223">Tipps zum Debuggen</span><span class="sxs-lookup"><span data-stu-id="b6b0d-223">Debugging tips</span></span>
<span data-ttu-id="b6b0d-224">Laden Sie für einen besseren Debugvorgang die Debuggingsymbole von den öffentlichen Microsoft-Symbolservern herunter:</span><span class="sxs-lookup"><span data-stu-id="b6b0d-224">For a better debugging experience, download the debugging symbols from the public Microsoft symbol servers:</span></span>

## **<a name="to-download-debugging-symbols"></a><span data-ttu-id="b6b0d-225">So laden Sie Debuggingsymbole herunter</span><span class="sxs-lookup"><span data-stu-id="b6b0d-225">To download debugging symbols</span></span>**
<span data-ttu-id="b6b0d-226">Wählen Sie auf der Menüleiste **Extras, Optionen** aus.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-226">On the menu bar, choose **Tools, Options**.</span></span>

<span data-ttu-id="b6b0d-227">Erweitern Sie im Dialogfeld **Optionen** die Option **Debuggen** , und wählen Sie **Symbole** aus.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-227">In the **Options** dialog box, expand **Debugging** and select **Symbols**.</span></span>

<span data-ttu-id="b6b0d-228">Wählen Sie **Microsoft-Symbolserver** und dann die Schaltfläche **OK** aus.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-228">Select **Microsoft Symbol Servers** and the choose the **OK** button.</span></span>

<span data-ttu-id="b6b0d-229">Beim ersten Mal kann das Herunterladen der Symbole einige Zeit dauern.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-229">It might take some time to download the symbols the first time.</span></span> <span data-ttu-id="b6b0d-230">Geben Sie für eine bessere Leistung beim nächsten Drücken von F5 ein lokales Verzeichnis an, in dem Sie die Symbole zwischenspeichern.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-230">For faster performance the next time you press F5, specify a local directory in which to cache the symbols.</span></span>

<span data-ttu-id="b6b0d-231">Beim Debuggen einer JavaScript-Lösung mit einer Komponenten-DLL können Sie den Debugger so einstellen, dass er das schrittweise Ausführen von Skripts oder das schrittweise Ausführen von systemeigenem Code in der Komponente, aber nicht beides gleichzeitig ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-231">When you debug a JavaScript solution that has a component DLL, you can set the debugger to enable either stepping through script or stepping through native code in the component, but not both at the same time.</span></span> <span data-ttu-id="b6b0d-232">Um die Einstellung zu ändern, öffnen Sie im Projektmappen-Explorer das Kontextmenü für den JavaScript-Projektknoten, und wählen Sie **Eigenschaften, Debuggen, Debuggertyp** aus.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-232">To change the setting, open the shortcut menu for the JavaScript project node in Solution Explorer and choose **Properties, Debugging, Debugger Type**.</span></span>

<span data-ttu-id="b6b0d-233">Achten Sie darauf, entsprechende Funktionen im Paket-Designer auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-233">Be sure to select appropriate capabilities in the package designer.</span></span> <span data-ttu-id="b6b0d-234">Sie können den Paket-Designer durch Öffnen der Datei „Package.appxmanifest“ öffnen.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-234">You can open the package designer by opening the Package.appxmanifest file.</span></span> <span data-ttu-id="b6b0d-235">Wenn Sie z. B. versuchen, programmgesteuert auf Dateien im Ordner „Bilder“ zuzugreifen, stellen Sie sicher, dass das Kontrollkästchen **Bildbibliothek** im Bereich **Funktionen** des Paket-Designers aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-235">For example, if you are attempting to programmatically access files in the Pictures folder, be sure to select the **Pictures Library** check box in the **Capabilities** pane of the package designer.</span></span>

<span data-ttu-id="b6b0d-236">Wenn der JavaScript-Code die öffentlichen Eigenschaften oder Methoden in der Komponente nicht erkennt, stellen Sie sicher, dass Sie in JavaScript Camel Casing verwenden.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-236">If your JavaScript code doesn't recognize the public properties or methods in the component, make sure that in JavaScript you are using camel casing.</span></span> <span data-ttu-id="b6b0d-237">Auf die `ComputeResult`-C++-Methode muss beispielsweise in JavaScript als `computeResult` verwiesen werden.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-237">For example, the `ComputeResult` C++ method must be referenced as `computeResult` in JavaScript.</span></span>

<span data-ttu-id="b6b0d-238">Wenn Sie ein C++-Komponentenprojekt für Windows-Runtime aus einer Projektmappe entfernen, müssen Sie den Projektverweis auch aus dem JavaScript-Projekt manuell entfernen.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-238">If you remove a C++ Windows Runtime Component project from a solution, you must also manually remove the project reference from the JavaScript project.</span></span> <span data-ttu-id="b6b0d-239">Andernfalls werden nachfolgende Debug- oder Buildvorgänge verhindert.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-239">Failure to do so prevents subsequent debug or build operations.</span></span> <span data-ttu-id="b6b0d-240">Bei Bedarf können Sie dann einen Assemblyverweis zur DLL-Datei hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-240">If necessary, you can then add an assembly reference to the DLL.</span></span>

## <a name="related-topics"></a><span data-ttu-id="b6b0d-241">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="b6b0d-241">Related topics</span></span>
* [<span data-ttu-id="b6b0d-242">Erstellen von Komponenten für Windows-Runtime in C++/CX</span><span class="sxs-lookup"><span data-stu-id="b6b0d-242">Creating Windows Runtime Components in C++/CX</span></span>](creating-windows-runtime-components-in-cpp.md)
