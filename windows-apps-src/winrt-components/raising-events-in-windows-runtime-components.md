---
author: msatranjr
title: Auslösen von Ereignissen in Komponenten für Windows-Runtime
ms.assetid: 3F7744E8-8A3C-4203-A1CE-B18584E89000
description: Wie Sie ein Ereignis eines benutzerdefinierten Delegattyps in einem Hintergrundthread auslösen, damit JavaScript das Ereignis empfangen kann.
ms.author: misatran
ms.date: 07/19/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 2dddd170f5f056de18c4729b6b6b5b4b6cbcea7b
ms.sourcegitcommit: 6cc275f2151f78db40c11ace381ee2d35f0155f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5557603"
---
# <a name="raising-events-in-windows-runtime-components"></a><span data-ttu-id="5f66e-104">Auslösen von Ereignissen in Komponenten für Windows-Runtime</span><span class="sxs-lookup"><span data-stu-id="5f66e-104">Raising Events in Windows Runtime Components</span></span>
> [!NOTE]
> <span data-ttu-id="5f66e-105">Informationen zum Auslösen von Ereignissen in einer [C++ / WinRT](../cpp-and-winrt-apis/intro-to-using-cpp-with-winrt.md) Komponente für Windows-Runtime, finden Sie unter [Erstellen von Ereignissen in C++ / WinRT](../cpp-and-winrt-apis/author-events.md).</span><span class="sxs-lookup"><span data-stu-id="5f66e-105">To learn how to raise events in a [C++/WinRT](../cpp-and-winrt-apis/intro-to-using-cpp-with-winrt.md) Windows Runtime Component, see [Author events in C++/WinRT](../cpp-and-winrt-apis/author-events.md).</span></span>

<span data-ttu-id="5f66e-106">Wenn die Komponente für Windows-Runtime ein Ereignis eines benutzerdefinierten Delegattyps in einem Hintergrundthread (Arbeitsthread) auslöst und JavaScript in der Lage sein soll, das Ereignis zu empfangen, können Sie es auf eine der folgenden Weisen implementieren und/oder auslösen:</span><span class="sxs-lookup"><span data-stu-id="5f66e-106">If your Windows Runtime component raises an event of a user-defined delegate type on a background thread (worker thread) and you want JavaScript to be able to receive the event, you can implement and/or raise it in one of these ways:</span></span>

-   <span data-ttu-id="5f66e-107">(Option1) Lösen Sie das Ereignis mit dem [Windows.UI.Core.CoreDispatcher](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.coredispatcher.aspx) aus, um das Ereignis an den JavaScript-Threadkontext zu marshallen.</span><span class="sxs-lookup"><span data-stu-id="5f66e-107">(Option 1) Raise the event through the [Windows.UI.Core.CoreDispatcher](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.coredispatcher.aspx) to marshal the event to the JavaScript thread context.</span></span> <span data-ttu-id="5f66e-108">Dies ist in der Regel zwar die beste Option, erzielt in manchen Szenarien aber möglicherweise nicht die schnellste Leistung.</span><span class="sxs-lookup"><span data-stu-id="5f66e-108">Although typically this is the best option, in some scenarios it might not provide the fastest performance.</span></span>
-   <span data-ttu-id="5f66e-109">(Option 2) Verwenden Sie [Windows.Foundation.EventHandler](https://msdn.microsoft.com/library/windows/apps/br206577.aspx)&lt;Object&gt;, allerdings mit Verlust von Ereignistypinformationen.</span><span class="sxs-lookup"><span data-stu-id="5f66e-109">(Option 2) Use [Windows.Foundation.EventHandler](https://msdn.microsoft.com/library/windows/apps/br206577.aspx)&lt;Object&gt; but lose type information (but lose the event type information).</span></span> <span data-ttu-id="5f66e-110">Falls Option1 nicht möglich oder die Leistung nicht ausreichend ist, bietet diese Option eine gute Alternative, wenn der Verlust von Typinformationen akzeptabel ist.</span><span class="sxs-lookup"><span data-stu-id="5f66e-110">If Option 1 is not feasible or its performance is not adequate, then this is a good second choice if loss of type information is acceptable.</span></span>
-   <span data-ttu-id="5f66e-111">(Option3) Erstellen Sie einen eigenen Proxy und Stub für die Komponente.</span><span class="sxs-lookup"><span data-stu-id="5f66e-111">(Option 3) Create your own proxy and stub for the component.</span></span> <span data-ttu-id="5f66e-112">Diese Option ist am schwierigsten zu implementieren, behält aber die Typinformationen bei und erzielt in anspruchsvollen Szenarien unter Umständen eine bessere Leistung als Option1.</span><span class="sxs-lookup"><span data-stu-id="5f66e-112">This option is the most difficult to implement, but it preserves type information and might provide better performance compared to Option 1 in demanding scenarios.</span></span>

<span data-ttu-id="5f66e-113">Wenn Sie nur ein Ereignis in einem Hintergrundthread ohne eine dieser Optionen auslösen, wird das Ereignis von einem JavaScript-Client nicht empfangen.</span><span class="sxs-lookup"><span data-stu-id="5f66e-113">If you just raise an event on a background thread without using one of these options, a JavaScript client will not receive the event.</span></span>

## <a name="background"></a><span data-ttu-id="5f66e-114">Hintergrund</span><span class="sxs-lookup"><span data-stu-id="5f66e-114">Background</span></span>

<span data-ttu-id="5f66e-115">Bei allen Komponenten und Apps für Windows-Runtime handelt es sich im Grunde um COM-Objekte, unabhängig davon, welche Sprache Sie bei ihrer Erstellung verwenden.</span><span class="sxs-lookup"><span data-stu-id="5f66e-115">All Windows Runtime components and apps are fundamentally COM objects, no matter what language you use to create them.</span></span> <span data-ttu-id="5f66e-116">In der Windows-API sind die meisten Komponenten agile COM-Objekte, die mit Objekten im Hintergrundthread und im UI-Thread gleichermaßen gut kommunizieren können.</span><span class="sxs-lookup"><span data-stu-id="5f66e-116">In the Windows API, most of the components are agile COM objects that can communicate equally well with objects on the background thread and on the UI thread.</span></span> <span data-ttu-id="5f66e-117">Wenn ein COM-Objekt nicht agil angelegt werden kann, sind Hilfsobjekte (auch als Proxys bzw. Stubs bezeichnet) erforderlich, um mit anderen COM-Objekten über die Threadgrenze des UI-Threadhintergrunds hinweg zu kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="5f66e-117">If a COM object can’t be made agile, then it requires helper objects known as proxies and stubs to communicate with other COM objects across the UI thread-background thread boundary.</span></span> <span data-ttu-id="5f66e-118">(In der COM-Terminologie wird dies als Kommunikation zwischen Threadapartments bezeichnet.)</span><span class="sxs-lookup"><span data-stu-id="5f66e-118">(In COM terms, this is known as communication between thread apartments.)</span></span>

<span data-ttu-id="5f66e-119">Die meisten Objekte in der Windows-API sind entweder agil oder verfügen über integrierte Proxys und Stubs.</span><span class="sxs-lookup"><span data-stu-id="5f66e-119">Most of the objects in the Windows API are either agile or have proxies and stubs built in.</span></span> <span data-ttu-id="5f66e-120">Allerdings können Proxys und Stubs nicht für generische Typen wie Windows.Foundation.[TypedEventHandler&lt;TSender, TResult&gt;](https://msdn.microsoft.com/library/windows/apps/br225997.aspx) erstellt werden, da sie erst vollständige Typen sind, wenn das Typargument bereitgestellt ist.</span><span class="sxs-lookup"><span data-stu-id="5f66e-120">However, proxies and stubs can’t be created for generic types such as Windows.Foundation.[TypedEventHandler&lt;TSender, TResult&gt;](https://msdn.microsoft.com/library/windows/apps/br225997.aspx) because they are not complete types until you provide the type argument.</span></span> <span data-ttu-id="5f66e-121">Fehlende Proxys oder Stubs stellen nur bei JavaScript-Clients ein Problem dar. Wenn die Komponente aber sowohl in JavaScript als auch in C++ oder einer .NET-Sprache verwendet werden soll, müssen Sie eine der drei folgenden Optionen verwenden.</span><span class="sxs-lookup"><span data-stu-id="5f66e-121">It's only with JavaScript clients that the lack of proxies or stubs becomes an issue, but if you want your component to be usable from JavaScript as well as from C++ or a .NET language, then you must use one of the following three options.</span></span>

## <a name="option-1-raise-the-event-through-the-coredispatcher"></a><span data-ttu-id="5f66e-122">Option1) Auslösen des Ereignisses mit dem CoreDispatcher-Ereignis</span><span class="sxs-lookup"><span data-stu-id="5f66e-122">(Option 1) Raise the event through the CoreDispatcher</span></span>

<span data-ttu-id="5f66e-123">Sie können Ereignisse eines benutzerdefinierten Delegattyps mit [Windows.UI.Core.CoreDispatcher](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.coredispatcher.aspx) senden, und JavaScript kann diese Ereignisse empfangen.</span><span class="sxs-lookup"><span data-stu-id="5f66e-123">You can send events of any user-defined delegate type by using the [Windows.UI.Core.CoreDispatcher](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.coredispatcher.aspx), and JavaScript will be able to receive them.</span></span> <span data-ttu-id="5f66e-124">Wenn Sie nicht sicher sind, welche Option Sie verwenden sollen, versuchen Sie es zunächst mit dieser ersten Option.</span><span class="sxs-lookup"><span data-stu-id="5f66e-124">If you are unsure which option to use, try this one first.</span></span> <span data-ttu-id="5f66e-125">Wenn die Wartezeit zwischen dem Auslösen von Ereignissen und der Ereignisbehandlung ein Problem darstellt, versuchen Sie es mit einer der anderen Optionen.</span><span class="sxs-lookup"><span data-stu-id="5f66e-125">If latency between the event firing and the event handling becomes an issue, then try one of the other options.</span></span>

<span data-ttu-id="5f66e-126">Im folgenden Beispiel wird gezeigt, wie der CoreDispatcher verwendet wird, um ein stark typisiertes Ereignis auszulösen.</span><span class="sxs-lookup"><span data-stu-id="5f66e-126">The following example shows how to use the CoreDispatcher to raise a strongly-typed event.</span></span> <span data-ttu-id="5f66e-127">Beachten Sie, dass es sich bei dem Typargument um „Toast“, und nicht um „Object“ handelt.</span><span class="sxs-lookup"><span data-stu-id="5f66e-127">Notice that the type argument is Toast, not Object.</span></span>

```csharp
public event EventHandler<Toast> ToastCompletedEvent;
private void OnToastCompleted(Toast args)
{
    var completedEvent = ToastCompletedEvent;
    if (completedEvent != null)
    {
        completedEvent(this, args);
    }
}

public void MakeToastWithDispatcher(string message)
{
    Toast toast = new Toast(message);
    // Assume you have a CoreDispatcher at class scope.
    // Initialize it here, then use it from the background thread.
    var window = Windows.UI.Core.CoreWindow.GetForCurrentThread();
    m_dispatcher = window.Dispatcher;

    Task.Run( () =>
    {
        if (ToastCompletedEvent != null)
        {
            m_dispatcher.RunAsync(CoreDispatcherPriority.Normal,
            new DispatchedHandler(() =>
            {
                this.OnToastCompleted(toast);
            })); // end m_dispatcher.RunAsync
         }
     }); // end Task.Run
}
```

## <a name="option-2-use-eventhandlerltobjectgt-but-lose-type-information"></a><span data-ttu-id="5f66e-128">(Option 2) Verwenden von EventHandler&lt;Object&gt;, allerdings mit Verlust von Typinformationen</span><span class="sxs-lookup"><span data-stu-id="5f66e-128">(Option 2) Use EventHandler&lt;Object&gt; but lose type information</span></span>

<span data-ttu-id="5f66e-129">Eine weitere Möglichkeit, ein Ereignis aus einem Hintergrundthread zu senden, ist die Verwendung von [Windows.Foundation.EventHandler](https://msdn.microsoft.com/library/windows/apps/br206577.aspx)&lt;Object&gt; als Typ des Ereignisses.</span><span class="sxs-lookup"><span data-stu-id="5f66e-129">Another way to send an event from a background thread is to use [Windows.Foundation.EventHandler](https://msdn.microsoft.com/library/windows/apps/br206577.aspx)&lt;Object&gt; as the type of the event.</span></span> <span data-ttu-id="5f66e-130">Windows instanziiert den generischen Typ konkret und stellt dafür einen Proxy und einen Stub bereit.</span><span class="sxs-lookup"><span data-stu-id="5f66e-130">Windows provides this concrete instantiation of the generic type and provides a proxy and stub for it.</span></span> <span data-ttu-id="5f66e-131">Der Nachteil besteht darin, dass die Typinformationen der Ereignisargumente und des Senders verloren gehen.</span><span class="sxs-lookup"><span data-stu-id="5f66e-131">The downside is that the type information of your event args and sender is lost.</span></span> <span data-ttu-id="5f66e-132">C++- und .NET-Clients müssen aus der Dokumentation entnehmen können, welcher Typ in den ursprünglichen Typ umgewandelt werden muss, wenn das Ereignis empfangen wird.</span><span class="sxs-lookup"><span data-stu-id="5f66e-132">C++ and .NET clients must know through documentation what type to cast back to when the event is received.</span></span> <span data-ttu-id="5f66e-133">JavaScript-Clients benötigt keine Informationen über die ursprünglichen Typen.</span><span class="sxs-lookup"><span data-stu-id="5f66e-133">JavaScript clients don’t need the original type information.</span></span> <span data-ttu-id="5f66e-134">Sie finden die Argumenteigenschaften anhand ihrer Namen in den Metadaten.</span><span class="sxs-lookup"><span data-stu-id="5f66e-134">They find the arg properties, based on their names in the metadata.</span></span>

<span data-ttu-id="5f66e-135">In diesem Beispiel wird gezeigt, wie Windows.Foundation.EventHandler&lt;Object&gt; in C# verwendet wird:</span><span class="sxs-lookup"><span data-stu-id="5f66e-135">This example shows how to use Windows.Foundation.EventHandler&lt;Object&gt; in C#:</span></span>

```csharp
public sealed Class1
{
// Declare the event
public event EventHandler<Object> ToastCompletedEvent;

    // Raise the event
    public async void MakeToast(string message)
    {
        Toast toast = new Toast(message);
        // Fire the event from a background thread to allow this thread to continue
        Task.Run(() =>
        {
            if (ToastCompletedEvent != null)
            {
                OnToastCompleted(toast);
            }
        });
    }

    private void OnToastCompleted(Toast args)
    {
        var completedEvent = ToastCompletedEvent;
        if (completedEvent != null)
        {
            completedEvent(this, args);
        }
    }
}
```

<span data-ttu-id="5f66e-136">Sie verwenden dieses Ereignis auf der JavaScript-Seite wie folgt:</span><span class="sxs-lookup"><span data-stu-id="5f66e-136">You consume this event on the JavaScript side like this:</span></span>

```javascript
toastCompletedEventHandler: function (event) {
   var toastType = event.toast.toastType;
   document.getElementById("toasterOutput").innerHTML = "<p>Made " + toastType + " toast</p>";
}
```

## <a name="option-3-create-your-own-proxy-and-stub"></a><span data-ttu-id="5f66e-137">(Option3) Erstellen eines eigenen Proxys und Stubs</span><span class="sxs-lookup"><span data-stu-id="5f66e-137">(Option 3) Create your own proxy and stub</span></span>

<span data-ttu-id="5f66e-138">Um bei benutzerdefinierten Ereignistypen mit vollständig beibehaltenen Typinformationen potenzielle Leistungszuwächse zu erreichen, müssen Sie eigene Proxy- und Stub-Objekte erstellen und diese in das App-Paket einbetten.</span><span class="sxs-lookup"><span data-stu-id="5f66e-138">For potential performance gains on user-defined event types that have fully-preserved type information, you have to create your own proxy and stub objects and embed them in your app package.</span></span> <span data-ttu-id="5f66e-139">In der Regel wird diese Option nur selten verwendet und zwar, wenn keine der beiden anderen Optionen geeignet ist.</span><span class="sxs-lookup"><span data-stu-id="5f66e-139">Typically, you have to use this option only in rare situations where neither of the other two options are adequate.</span></span> <span data-ttu-id="5f66e-140">Außerdem ist nicht gewährleistet, dass mit dieser Option eine bessere Leistung erzielt wird als mit den anderen beiden Optionen.</span><span class="sxs-lookup"><span data-stu-id="5f66e-140">Also, there is no guarantee that this option will provide better performance than the other two options.</span></span> <span data-ttu-id="5f66e-141">Die tatsächliche Leistung hängt von vielen Faktoren ab.</span><span class="sxs-lookup"><span data-stu-id="5f66e-141">Actual performance depends on many factors.</span></span> <span data-ttu-id="5f66e-142">Verwenden Sie den Visual Studio-Profiler oder andere Profilerstellungstools, um die tatsächliche Leistung der Anwendung zu messen und um festzustellen, ob das Ereignis tatsächlich einen Engpass darstellt.</span><span class="sxs-lookup"><span data-stu-id="5f66e-142">Use the Visual Studio profiler or other profiling tools to measure actual performance in your application and determine whether the event is in fact a bottleneck.</span></span>

<span data-ttu-id="5f66e-143">Im weiteren Verlauf dieses Artikels wird gezeigt, wie eine grundlegende Komponente für Windows-Runtime in C# und anschließend eine DLL für Proxy und Stub in C++ erstellt werden, sodass JavaScript ein Windows.Foundation.TypedEventHandler&lt;TSender, TResult&gt;-Ereignis nutzen kann, das von der Komponente in einem asynchronen Vorgang ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="5f66e-143">The rest of this article shows how to use C# to create a basic Windows Runtime component, and then use C++ to create a DLL for the proxy and stub that will enable JavaScript to consume a Windows.Foundation.TypedEventHandler&lt;TSender, TResult&gt; event that's raised by the component in an async operation.</span></span> <span data-ttu-id="5f66e-144">(Sie können die Komponente auch in C++ oder Visual Basic erstellen.</span><span class="sxs-lookup"><span data-stu-id="5f66e-144">(You can also use C++ or Visual Basic to create the component.</span></span> <span data-ttu-id="5f66e-145">Die Schritte zum Erstellen der Proxys und Stubs sind identisch.) Diese exemplarische Vorgehensweise basiert auf dem Artikel „Erstellen einer prozessinternen Komponente für Windows-Runtime (C++/CX) – Beispiel”, dessen Zielsetzungen näher erläutert werden.</span><span class="sxs-lookup"><span data-stu-id="5f66e-145">The steps that are related to creating the proxies and stubs are the same.) This walkthrough is based on Creating a Windows Runtime in-process component sample (C++/CX) and helps explain its purposes.</span></span>

<span data-ttu-id="5f66e-146">Diese exemplarische Vorgehensweise besteht aus folgenden Teilen:</span><span class="sxs-lookup"><span data-stu-id="5f66e-146">This walkthrough has these parts:</span></span>

-   <span data-ttu-id="5f66e-147">Hier erstellen Sie zwei Windows-Runtime-Basisklassen.</span><span class="sxs-lookup"><span data-stu-id="5f66e-147">Here you will create two basic Windows Runtime classes.</span></span> <span data-ttu-id="5f66e-148">Die eine Klasse macht ein Ereignis vom Typ [Windows.Foundation.TypedEventHandler&lt;TSender, TResult&gt;](https://msdn.microsoft.com/library/windows/apps/br225997.aspx) verfügbar, und die andere Klasse ist der Typ, der als Argument für TValue an JavaScript zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="5f66e-148">One class exposes an event of type [Windows.Foundation.TypedEventHandler&lt;TSender, TResult&gt;](https://msdn.microsoft.com/library/windows/apps/br225997.aspx) and the other class is the type that's returned to JavaScript as the argument for TValue.</span></span> <span data-ttu-id="5f66e-149">Diese Klassen können erst mit JavaScript kommunizieren, wenn Sie die nachfolgenden Schritten ausgeführt haben.</span><span class="sxs-lookup"><span data-stu-id="5f66e-149">These classes can't communicate with JavaScript until you complete the later steps.</span></span>
-   <span data-ttu-id="5f66e-150">Diese App aktiviert das Hauptklassenobjekt, ruft eine Methode auf und behandelt ein Ereignis, das von der Komponente für Windows-Runtime ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="5f66e-150">This app activates the main class object, calls a method, and handles an event that's raised by the Windows Runtime component.</span></span>
-   <span data-ttu-id="5f66e-151">Diese werden von den Tools benötigt, die die Proxy- und Stubklassen generieren.</span><span class="sxs-lookup"><span data-stu-id="5f66e-151">These are required by the tools that generate the proxy and stub classes.</span></span>
-   <span data-ttu-id="5f66e-152">Dann wird mithilfe der IDL-Datei der C-Quellcode für den Proxy und den Stub generiert.</span><span class="sxs-lookup"><span data-stu-id="5f66e-152">You then use the IDL file to generate the C source code for the proxy and stub.</span></span>
-   <span data-ttu-id="5f66e-153">Registrieren Sie die Proxy-Stub-Objekte, damit die COM-Laufzeitumgebung sie finden kann, und verweisen Sie im App-Projekt auf die Proxy-Stub-DLL-Datei.</span><span class="sxs-lookup"><span data-stu-id="5f66e-153">Register the proxy-stub objects so that the COM runtime can find them, and reference the proxy-stub DLL in the app project.</span></span>

## <a name="to-create-the-windows-runtime-component"></a><span data-ttu-id="5f66e-154">So erstellen Sie die Komponente für Windows-Runtime</span><span class="sxs-lookup"><span data-stu-id="5f66e-154">To create the Windows Runtime component</span></span>

<span data-ttu-id="5f66e-155">Klicken Sie in Visual Studio auf der Menüleiste auf **Datei &gt; Neues Projekt**.</span><span class="sxs-lookup"><span data-stu-id="5f66e-155">In Visual Studio, on the menu bar, choose **File &gt; New Project**.</span></span> <span data-ttu-id="5f66e-156">Erweitern Sie im Dialogfeld **Neues Projekt** die Option **JavaScript &gt; Universal Windows**, und wählen Sie dann **Leere App** aus.</span><span class="sxs-lookup"><span data-stu-id="5f66e-156">In the **New Project** dialog box, expand **JavaScript &gt; Universal Windows** and then select **Blank App**.</span></span> <span data-ttu-id="5f66e-157">Geben Sie als Projektnamen „ToasterApplication“ ein, und klicken Sie dann auf die Schaltfläche **OK**.</span><span class="sxs-lookup"><span data-stu-id="5f66e-157">Name the project ToasterApplication and then choose the **OK** button.</span></span>

<span data-ttu-id="5f66e-158">Fügen Sie der Projektmappe eine C#-Komponente für Windows-Runtime hinzu: Öffnen Sie im Projektmappen-Explorer das Kontextmenü für die Projektmappe, und wählen Sie dann **Hinzufügen &gt; Neues Projekt** aus.</span><span class="sxs-lookup"><span data-stu-id="5f66e-158">Add a C# Windows Runtime component to the solution: In Solution Explorer, open the shortcut menu for the solution and then choose **Add &gt; New Project**.</span></span> <span data-ttu-id="5f66e-159">Erweitern Sie **Visual C#- &gt; Microsoft Store** und wählen Sie dann die **Windows-Runtime-Komponente**.</span><span class="sxs-lookup"><span data-stu-id="5f66e-159">Expand **Visual C# &gt; Microsoft Store** and then select **Windows Runtime Component**.</span></span> <span data-ttu-id="5f66e-160">Geben Sie als Projektnamen „ToasterComponent“ ein, und klicken Sie dann auf die Schaltfläche **OK**.</span><span class="sxs-lookup"><span data-stu-id="5f66e-160">Name the project ToasterComponent and then choose the **OK** button.</span></span> <span data-ttu-id="5f66e-161">ToasterComponent ist der Stammnamespace für die Komponenten, die Sie in späteren Schritten erstellen.</span><span class="sxs-lookup"><span data-stu-id="5f66e-161">ToasterComponent will be the root namespace for the components you will create in later steps.</span></span>

<span data-ttu-id="5f66e-162">Öffnen Sie im Projektmappen-Explorer das Kontextmenü für die Projektmappe, und wählen Sie dann **Eigenschaften** aus.</span><span class="sxs-lookup"><span data-stu-id="5f66e-162">In Solution Explorer, open the shortcut menu for the solution and then choose **Properties**.</span></span> <span data-ttu-id="5f66e-163">Wählen Sie im Dialogfeld **Eigenschaftenseiten** im linken Bereich **Konfigurationseigenschaften** aus, und legen Sie dann oben im Dialogfeld die **Konfiguration** auf **Debuggen** und die **Plattform** auf „x86”, „x64” oder „ARM” fest.</span><span class="sxs-lookup"><span data-stu-id="5f66e-163">In the **Property Pages** dialog box, select **Configuration Properties** in the left pane, and then at the top of the dialog box, set **Configuration** to **Debug** and **Platform** to x86, x64, or ARM.</span></span> <span data-ttu-id="5f66e-164">Klicken Sie auf die Schaltfläche **OK**.</span><span class="sxs-lookup"><span data-stu-id="5f66e-164">Choose the **OK** button.</span></span>

<span data-ttu-id="5f66e-165">**Wichtige**Plattform = Any CPU funktioniert nicht, da sie nicht für die Win32-DLL in systemeigenem Code gültig ist, die Sie später der Projektmappe hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="5f66e-165">**Important**Platform = Any CPU won’t work because it's not valid for the native-code Win32 DLL that you'll add to the solution later.</span></span>

<span data-ttu-id="5f66e-166">Benennen Sie im Projektmappen-Explorer die Datei „class1.cs” in „ToasterComponent.cs” um, sodass sie dem Namen des Projekts entspricht.</span><span class="sxs-lookup"><span data-stu-id="5f66e-166">In Solution Explorer, rename class1.cs to ToasterComponent.cs so that it matches the name of the project.</span></span> <span data-ttu-id="5f66e-167">Visual Studio benennt die Klasse in der Datei entsprechend dem neuen Dateinamen automatisch um.</span><span class="sxs-lookup"><span data-stu-id="5f66e-167">Visual Studio automatically renames the class in the file to match the new file name.</span></span>

<span data-ttu-id="5f66e-168">Fügen Sie der CS-Datei eine using-Direktive für den Namespace Windows.Foundation hinzu, um TypedEventHandler in den Gültigkeitsbereich einzubinden.</span><span class="sxs-lookup"><span data-stu-id="5f66e-168">In the .cs file, add a using directive for the Windows.Foundation namespace to bring TypedEventHandler into scope.</span></span>

<span data-ttu-id="5f66e-169">Wenn Sie Proxys und Stubs benötigen, muss die Komponente mit Schnittstellen ihre öffentlichen Member verfügbar machen.</span><span class="sxs-lookup"><span data-stu-id="5f66e-169">When you require proxies and stubs, your component must use interfaces to expose its public members.</span></span> <span data-ttu-id="5f66e-170">Definieren Sie in „ToasterComponent.cs” eine Schnittstelle für den Toaster und eine andere für den „Toast” (Popup), den der Toaster erzeugt.</span><span class="sxs-lookup"><span data-stu-id="5f66e-170">In ToasterComponent.cs, define an interface for the toaster, and another one for the Toast that the toaster produces.</span></span>

<span data-ttu-id="5f66e-171">**Hinweis:** In c# können Sie diesen Schritt überspringen.</span><span class="sxs-lookup"><span data-stu-id="5f66e-171">**Note**In C# you can skip this step.</span></span> <span data-ttu-id="5f66e-172">Erstellen Sie stattdessen zuerst eine Klasse, öffnen Sie das Kontextmenü, und wählen Sie **Umgestalten &gt; Schnittstelle extrahieren** aus.</span><span class="sxs-lookup"><span data-stu-id="5f66e-172">Instead, first create a class, and then open its shortcut menu and choose **Refactor &gt; Extract Interface**.</span></span> <span data-ttu-id="5f66e-173">Ordnen Sie den Schnittstellen im generierten Code manuell öffentlichen Zugriff zu.</span><span class="sxs-lookup"><span data-stu-id="5f66e-173">In the code that's generated, manually give the interfaces public accessibility.</span></span>

```csharp
    public interface IToaster
        {
            void MakeToast(String message);
            event TypedEventHandler<Toaster, Toast> ToastCompletedEvent;

        }
        public interface IToast
        {
            String ToastType { get; }
        }
```

<span data-ttu-id="5f66e-174">Die IToast-Schnittstelle hat eine Zeichenfolge, die abgerufen werden kann, um den Typ des Popups zu beschreiben.</span><span class="sxs-lookup"><span data-stu-id="5f66e-174">The IToast interface has a string that can be retrieved to describe the type of toast.</span></span> <span data-ttu-id="5f66e-175">Die IToaster-Schnittstelle verfügt eine Methode, um das Popup zu erstellen, und über ein Ereignis, das angibt, dass das Popup erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="5f66e-175">The IToaster interface has a method to make toast, and an event to indicate that the toast is made.</span></span> <span data-ttu-id="5f66e-176">Da dieses Ereignis einen bestimmten Teil (d.h. den Typ) des Popups zurückgibt, wird es als typisiertes Ereignis bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="5f66e-176">Because this event returns the particular piece (that is, type) of toast, it's known as a typed event.</span></span>

<span data-ttu-id="5f66e-177">Als Nächstes müssen Klassen angelegt werden, die diese Schnittstellen implementieren. Diese Klassen müssen öffentlich und versiegelt sein, damit die JavaScript-App, die Sie später programmieren, darauf zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="5f66e-177">Next, we need classes that implement these interfaces, and are public and sealed so that they are accessible from the JavaScript app that you'll program later.</span></span>

```csharp
    public sealed class Toast : IToast
        {
            private string _toastType;

            public string ToastType
            {
                get
                {
                    return _toastType;
                }
            }
            internal Toast(String toastType)
            {
                _toastType = toastType;
            }

        }
        public sealed class Toaster : IToaster
        {
            public event TypedEventHandler<Toaster, Toast> ToastCompletedEvent;

            private void OnToastCompleted(Toast args)
            {
                var completedEvent = ToastCompletedEvent;
                if (completedEvent != null)
                {
                    completedEvent(this, args);
                }
            }

            public void MakeToast(string message)
            {
                Toast toast = new Toast(message);
                // Fire the event from a thread-pool thread to enable this thread to continue
                Windows.System.Threading.ThreadPool.RunAsync(
                (IAsyncAction action) =>
                {
                    if (ToastCompletedEvent != null)
                    {
                        OnToastCompleted(toast);
                    }
                });
           }
        }
```

<span data-ttu-id="5f66e-178">Im vorhergehenden Code wird das Popup erstellt und eine Arbeitsaufgabe im Threadpool ausgeführt, um die Benachrichtigung auszulösen.</span><span class="sxs-lookup"><span data-stu-id="5f66e-178">In the preceding code, we create the toast and then spin up a thread-pool work item to fire the notification.</span></span> <span data-ttu-id="5f66e-179">Auch wenn die IDE vorschlagen sollte, das „await“-Schlüsselwort dem asynchronen Aufruf zuzuweisen, ist dies in diesem Fall nicht nötig, da die Methode keine Aktionen ausführt, die von den Ergebnissen des Vorgangs abhängig sind.</span><span class="sxs-lookup"><span data-stu-id="5f66e-179">Although the IDE might suggest that you apply the await keyword to the async call, it isn’t necessary in this case because the method doesn’t do any work that depends on the results of the operation.</span></span>

<span data-ttu-id="5f66e-180">**Hinweis:** der asynchrone Aufruf im vorangehenden Code verwendet ThreadPool.RunAsync ausschließlich, um eine einfache Möglichkeit, das Ereignis in einem Hintergrundthread auslösen zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="5f66e-180">**Note**The async call in the preceding code uses ThreadPool.RunAsync solely to demonstrate a simple way to fire the event on a background thread.</span></span> <span data-ttu-id="5f66e-181">Sie könnten diese spezielle Methode auch schreiben wie im folgenden Beispiel gezeigt. Dies funktioniert, da der .NET-Taskplaner automatisch „async/await“-Aufrufe zurück an den UI-Thread marshallt.</span><span class="sxs-lookup"><span data-stu-id="5f66e-181">You could write this particular method as shown in the following example, and it would work fine because the .NET Task scheduler automatically marshals async/await calls back to the UI thread.</span></span>
  
```csharp
    public async void MakeToast(string message)
    {
        Toast toast = new Toast(message)
        await Task.Delay(new Random().Next(1000));
        OnToastCompleted(toast);
    }
```

<span data-ttu-id="5f66e-182">Wenn Sie das Projekt jetzt erstellen, sollte dies ordnungsgemäß ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="5f66e-182">If you build the project now, it should build cleanly.</span></span>

## <a name="to-program-the-javascript-app"></a><span data-ttu-id="5f66e-183">So programmieren Sie die JavaScript-App</span><span class="sxs-lookup"><span data-stu-id="5f66e-183">To program the JavaScript app</span></span>

<span data-ttu-id="5f66e-184">Jetzt können Sie der JavaScript-App eine Schaltfläche hinzufügen, damit sie die Klasse verwendet, die Sie gerade zum Erstellen des Popups definiert haben.</span><span class="sxs-lookup"><span data-stu-id="5f66e-184">Now we can add a button to the JavaScript app to cause it to use the class we just defined to make toast.</span></span> <span data-ttu-id="5f66e-185">Vorher müssen Sie einen Verweis auf das ToasterComponent-Projekt hinzufügen, das Sie gerade erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="5f66e-185">Before we do this, we must add a reference to the ToasterComponent project we just created.</span></span> <span data-ttu-id="5f66e-186">Öffnen Sie im Projektmappen-Explorer das Kontextmenü für das Projekt "toasterapplication" ein, wählen Sie **Hinzufügen &gt; Verweise**, und wählen Sie dann die Schaltfläche " **Neuen Verweis hinzufügen** ".</span><span class="sxs-lookup"><span data-stu-id="5f66e-186">In Solution Explorer, open the shortcut menu for the ToasterApplication project, choose **Add &gt; References**, and then choose the **Add New Reference** button.</span></span> <span data-ttu-id="5f66e-187">Wählen Sie im Dialogfeld „Verweis hinzufügen” im linken Bereich unter „Projektmappe” das Komponentenprojekt aus, und wählen Sie dann im mittleren Bereich „ToasterComponent” aus.</span><span class="sxs-lookup"><span data-stu-id="5f66e-187">In the Add Reference dialog box, in the left pane under Solution, select the component project, and then in the middle pane, select ToasterComponent.</span></span> <span data-ttu-id="5f66e-188">Klicken Sie auf die Schaltfläche **OK**.</span><span class="sxs-lookup"><span data-stu-id="5f66e-188">Choose the **OK** button.</span></span>

<span data-ttu-id="5f66e-189">Öffnen Sie im Projektmappen-Explorer das Kontextmenü für das ToasterApplication-Projekt, und wählen Sie **Als Startprojekt festlegen** aus.</span><span class="sxs-lookup"><span data-stu-id="5f66e-189">In Solution Explorer, open the shortcut menu for the ToasterApplication project and then choose **Set as Startup Project**.</span></span>

<span data-ttu-id="5f66e-190">Fügen Sie am Ende der Datei „default.js” einen Namespace hinzu, der die Funktionen zum Aufrufen der Komponente und zum Zurückrufen durch die Komponente enthält.</span><span class="sxs-lookup"><span data-stu-id="5f66e-190">At the end of the default.js file, add a namespace to contain the functions to call the component and be called back by it.</span></span> <span data-ttu-id="5f66e-191">Der Namespace hat zwei Funktionen: eine zum Erstellen des Popups und eine zum Behandeln des Abschlussereignisses des Popups.</span><span class="sxs-lookup"><span data-stu-id="5f66e-191">The namespace will have two functions, one to make toast and one to handle the toast-complete event.</span></span> <span data-ttu-id="5f66e-192">Die Implementierung von makeToast erstellt ein Toaster-Objekt, registriert den Ereignishandler und erstellt das Popup.</span><span class="sxs-lookup"><span data-stu-id="5f66e-192">The implementation of makeToast creates a Toaster object, registers the event handler, and makes the toast.</span></span> <span data-ttu-id="5f66e-193">Bisher führt der Ereignishandler nicht viel aus, wie hier gezeigt:</span><span class="sxs-lookup"><span data-stu-id="5f66e-193">So far, the event handler doesn’t do much, as shown here:</span></span>

```javascript
    WinJS.Namespace.define("ToasterApplication"), {
       makeToast: function () {

          var toaster = new ToasterComponent.Toaster();
          //toaster.addEventListener("ontoastcompletedevent", ToasterApplication.toastCompletedEventHandler);
          toaster.ontoastcompletedevent = ToasterApplication.toastCompletedEventHandler;
          toaster.makeToast("Peanut Butter");
       },

       toastCompletedEventHandler: function(event) {
           // The sender of the event (the delegate's first type parameter)
           // is mapped to event.target. The second argument of the delegate
           // is contained in event, which means in this case event is a
           // Toast class, with a toastType string.
           var toastType = event.toastType;

           document.getElementById('toastOutput').innerHTML = "<p>Made " + toastType + " toast</p>";
        },
    });
```

<span data-ttu-id="5f66e-194">Die makeToast-Funktion muss mit einer Schaltfläche verknüpft werden.</span><span class="sxs-lookup"><span data-stu-id="5f66e-194">The makeToast function must be hooked up to a button.</span></span> <span data-ttu-id="5f66e-195">Aktualisieren Sie die Datei „default.HTML” so, dass eine Schaltfläche und Leerzeichen eingefügt werden, um das Ergebnis der Popuperstellung auszugeben:</span><span class="sxs-lookup"><span data-stu-id="5f66e-195">Update default.html to include a button and some space to output the result of making toast:</span></span>

```html
    <body>
        <h1>Click the button to make toast</h1>
        <button onclick="ToasterApplication.makeToast()">Make Toast!</button>
        <div id="toasterOutput">
            <p>No Toast Yet...</p>
        </div>
    </body>
```

<span data-ttu-id="5f66e-196">Ohne TypedEventHandler könnte die App schon auf dem lokalen Computer ausgeführt und auf die Schaltfläche zum Erstellen des Popups geklickt werden.</span><span class="sxs-lookup"><span data-stu-id="5f66e-196">If we weren’t using a TypedEventHandler, we would now be able to run the app on the local machine and click the button to make toast.</span></span> <span data-ttu-id="5f66e-197">In dieser App passiert aber nichts.</span><span class="sxs-lookup"><span data-stu-id="5f66e-197">But in our app, nothing happens.</span></span> <span data-ttu-id="5f66e-198">Um herauszufinden, woran das liegt, wird der verwaltete Code gedebuggt, der ToastCompletedEvent auslöst.</span><span class="sxs-lookup"><span data-stu-id="5f66e-198">To find out why, let’s debug the managed code that fires the ToastCompletedEvent.</span></span> <span data-ttu-id="5f66e-199">Halten Sie das Projekt, und wählen Sie dann auf der Menüleiste **Debuggen &gt; Toaster Anwendungseigenschaften**.</span><span class="sxs-lookup"><span data-stu-id="5f66e-199">Stop the project, and then on the menu bar, choose **Debug &gt; Toaster Application properties**.</span></span> <span data-ttu-id="5f66e-200">Ändern Sie den **Debuggertyp** in **Nur verwaltet**.</span><span class="sxs-lookup"><span data-stu-id="5f66e-200">Change **Debugger Type** to **Managed Only**.</span></span> <span data-ttu-id="5f66e-201">Wählen Sie auf der Menüleiste erneut **Debuggen &gt; Ausnahmen**, und wählen Sie dann die **Common Language Runtime-Ausnahmen**.</span><span class="sxs-lookup"><span data-stu-id="5f66e-201">Again on the menu bar, choose **Debug &gt; Exceptions**, and then select **Common Language Runtime Exceptions**.</span></span>

<span data-ttu-id="5f66e-202">Führen Sie die App jetzt aus, und klicken Sie auf die Schaltfläche zum Erstellen des Popups.</span><span class="sxs-lookup"><span data-stu-id="5f66e-202">Now run the app and click the make-toast button.</span></span> <span data-ttu-id="5f66e-203">Der Debugger fängt die Ausnahme „ungültige Umwandlung” ab.</span><span class="sxs-lookup"><span data-stu-id="5f66e-203">The debugger catches an invalid cast exception.</span></span> <span data-ttu-id="5f66e-204">Obwohl dies nicht aus der Meldung ersichtlich ist, wird diese Ausnahme ausgelöst, weil Proxys für diese Schnittstelle fehlen.</span><span class="sxs-lookup"><span data-stu-id="5f66e-204">Although it’s not obvious from its message, this exception is occurring because proxies are missing for that interface.</span></span>

![Fehlende Proxys](./images/debuggererrormissingproxy.png)

<span data-ttu-id="5f66e-206">Der erste Schritt zum Erstellen eines Proxys und Stubs für eine Komponente besteht darin, den Schnittstellen eine eindeutige ID oder GUID hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="5f66e-206">The first step in creating a proxy and stub for a component is to add a unique ID or GUID to the interfaces.</span></span> <span data-ttu-id="5f66e-207">Das zu verwendende GUID-Format hängt davon ab, ob Sie in C#, Visual Basic, einer anderen .NET-Sprache oder in C++ programmieren.</span><span class="sxs-lookup"><span data-stu-id="5f66e-207">However, the GUID format to use differs depending on whether you're coding in C#, Visual Basic, or another .NET language, or in C++.</span></span>

## <a name="to-generate-guids-for-the-components-interfaces-c-and-other-net-languages"></a><span data-ttu-id="5f66e-208">So generieren Sie GUIDs für die Schnittstellen der Komponente (C#- oder andere .NET-Sprachen)</span><span class="sxs-lookup"><span data-stu-id="5f66e-208">To generate GUIDs for the component's interfaces (C# and other .NET languages)</span></span>

<span data-ttu-id="5f66e-209">Wählen Sie auf der Menüleiste Tools &gt; GUID erstellen.</span><span class="sxs-lookup"><span data-stu-id="5f66e-209">On the menu bar, choose Tools &gt; Create GUID.</span></span> <span data-ttu-id="5f66e-210">Wählen Sie im Dialogfeld „5.</span><span class="sxs-lookup"><span data-stu-id="5f66e-210">In the dialog box, select 5.</span></span> <span data-ttu-id="5f66e-211">\[GUID ("Xxxxxxxx-Xxxx Xxxx) \].</span><span class="sxs-lookup"><span data-stu-id="5f66e-211">\[Guid(“xxxxxxxx-xxxx...xxxx)\].</span></span> <span data-ttu-id="5f66e-212">Klicken Sie auf die Schaltfläche „Neue GUID” und dann auf die Schaltfläche „Kopieren”.</span><span class="sxs-lookup"><span data-stu-id="5f66e-212">Choose the New GUID button and then choose the Copy button.</span></span>

![GUID-Generator-tool](./images/guidgeneratortool.png)

<span data-ttu-id="5f66e-214">Wechseln Sie zurück zur Schnittstellendefinition, und fügen Sie die neue GUID direkt vor der IToaster-Schnittstelle ein, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="5f66e-214">Go back to the interface definition, and then paste the new GUID just before the IToaster interface, as shown in the following example.</span></span> <span data-ttu-id="5f66e-215">(Verwenden Sie nicht die GUID aus dem Beispiel.</span><span class="sxs-lookup"><span data-stu-id="5f66e-215">(Don't use the GUID in the example.</span></span> <span data-ttu-id="5f66e-216">Jede eindeutige Schnittstelle sollte eine eigene GUID haben.)</span><span class="sxs-lookup"><span data-stu-id="5f66e-216">Every unique interface should have its own GUID.)</span></span>

```cpp
[Guid("FC198F74-A808-4E2A-9255-264746965B9F")]
        public interface IToaster...
```

<span data-ttu-id="5f66e-217">Fügen Sie eine using-Direktive für den System.Runtime.InteropServices-Namespace hinzu.</span><span class="sxs-lookup"><span data-stu-id="5f66e-217">Add a using directive for the System.Runtime.InteropServices namespace.</span></span>

<span data-ttu-id="5f66e-218">Wiederholen Sie diese Schritte für die IToast-Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="5f66e-218">Repeat these steps for the IToast interface.</span></span>

## <a name="to-generate-guids-for-the-components-interfaces-c"></a><span data-ttu-id="5f66e-219">So generieren Sie GUIDs für die Schnittstellen der Komponente (C++)</span><span class="sxs-lookup"><span data-stu-id="5f66e-219">To generate GUIDs for the component's interfaces (C++)</span></span>

<span data-ttu-id="5f66e-220">Wählen Sie auf der Menüleiste Tools &gt; GUID erstellen.</span><span class="sxs-lookup"><span data-stu-id="5f66e-220">On the menu bar, choose Tools &gt; Create GUID.</span></span> <span data-ttu-id="5f66e-221">Wählen Sie im Dialogfeld „3.</span><span class="sxs-lookup"><span data-stu-id="5f66e-221">In the dialog box, select 3.</span></span> <span data-ttu-id="5f66e-222">Struktur-GUID mit statischem Konstruktor = { ... }” aus.</span><span class="sxs-lookup"><span data-stu-id="5f66e-222">static const struct GUID = {...}.</span></span> <span data-ttu-id="5f66e-223">Klicken Sie auf die Schaltfläche „Neue GUID” und dann auf die Schaltfläche „Kopieren”.</span><span class="sxs-lookup"><span data-stu-id="5f66e-223">Choose the New GUID button and then choose the Copy button.</span></span>

<span data-ttu-id="5f66e-224">Fügen Sie die GUID direkt vor der Definition der IToaster-Schnittstelle ein.</span><span class="sxs-lookup"><span data-stu-id="5f66e-224">Paste the GUID just before the IToaster interface definition.</span></span> <span data-ttu-id="5f66e-225">Nach dem Einfügen sollte die GUID dem folgenden Beispiel ähneln:</span><span class="sxs-lookup"><span data-stu-id="5f66e-225">After you paste, the GUID should resemble the following example.</span></span> <span data-ttu-id="5f66e-226">(Verwenden Sie nicht die GUID aus dem Beispiel.</span><span class="sxs-lookup"><span data-stu-id="5f66e-226">(Don't use the GUID in the example.</span></span> <span data-ttu-id="5f66e-227">Jede eindeutige Schnittstelle sollte eine eigene GUID haben.)</span><span class="sxs-lookup"><span data-stu-id="5f66e-227">Every unique interface should have its own GUID.)</span></span>
```cpp
// {F8D30778-9EAF-409C-BCCD-C8B24442B09B}
    static const GUID <<name>> = { 0xf8d30778, 0x9eaf, 0x409c, { 0xbc, 0xcd, 0xc8, 0xb2, 0x44, 0x42, 0xb0, 0x9b } };
```
<span data-ttu-id="5f66e-228">Fügen Sie eine using-Direktive für Windows.Foundation.Metadata hinzu, um GuidAttribute in den Gültigkeitsbereich einzubinden.</span><span class="sxs-lookup"><span data-stu-id="5f66e-228">Add a using directive for Windows.Foundation.Metadata to bring GuidAttribute into scope.</span></span>

<span data-ttu-id="5f66e-229">Konvertieren Sie nun die GUID mit dem Konstruktor manuell in ein GuidAttribute, damit die GUID wie im folgenden Beispiel gezeigt formatiert wird.</span><span class="sxs-lookup"><span data-stu-id="5f66e-229">Now manually convert the const GUID to a GuidAttribute so that it's formatted as shown in the following example.</span></span> <span data-ttu-id="5f66e-230">Beachten Sie, dass die geschweiften Klammern durch eckige und runde Klammern ersetzt werden und das nachfolgende Semikolon entfernt wird.</span><span class="sxs-lookup"><span data-stu-id="5f66e-230">Notice that the curly braces are replaced with brackets and parentheses, and the trailing semicolon is removed.</span></span>
```cpp
// {E976784C-AADE-4EA4-A4C0-B0C2FD1307C3}
    [GuidAttribute(0xe976784c, 0xaade, 0x4ea4, 0xa4, 0xc0, 0xb0, 0xc2, 0xfd, 0x13, 0x7, 0xc3)]
    public interface IToaster
    {...
```
<span data-ttu-id="5f66e-231">Wiederholen Sie diese Schritte für die IToast-Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="5f66e-231">Repeat these steps for the IToast interface.</span></span>

<span data-ttu-id="5f66e-232">Da die Schnittstellen nun über eindeutige IDs verfügen, kann eine IDL-Datei erstellt werden, indem die WINMD-Datei in das winmdidl-Befehlszeilentool eingefügt wird. Anschließend wird der C-Quellcode für den Proxy und den Stub generiert, indem diese IDL-Datei in das MIDL-Befehlszeilentool eingefügt wird.</span><span class="sxs-lookup"><span data-stu-id="5f66e-232">Now that the interfaces have unique IDs, we can create an IDL file by feeding the .winmd file into the winmdidl command-line tool, and then generate the C source code for the proxy and stub by feeding that IDL file into the MIDL command-line tool.</span></span> <span data-ttu-id="5f66e-233">Visual Studio führt dies automatisch aus, wenn Postbuildereignisse erstellt werden, wie in den nachfolgenden Schritten gezeigt.</span><span class="sxs-lookup"><span data-stu-id="5f66e-233">Visual Studio do this for us if we create post-build events as shown in the following steps.</span></span>

## <a name="to-generate-the-proxy-and-stub-source-code"></a><span data-ttu-id="5f66e-234">So generieren Sie den Proxy- und Stubquellcode</span><span class="sxs-lookup"><span data-stu-id="5f66e-234">To generate the proxy and stub source code</span></span>

<span data-ttu-id="5f66e-235">Um ein benutzerdefiniertes Postbuildereignis hinzuzufügen, öffnen Sie im Projektmappen-Explorer das Kontextmenü für das ToasterComponent-Projekt, und wählen Sie dann „Eigenschaften” aus.</span><span class="sxs-lookup"><span data-stu-id="5f66e-235">To add a custom post-build event, in Solution Explorer, open the shortcut menu for the ToasterComponent project and then choose Properties.</span></span> <span data-ttu-id="5f66e-236">Wählen Sie im linken Bereich der Eigenschaftenseiten „Buildereignisse” aus, und klicken Sie dann auf die Schaltfläche „Postbuild bearbeiten”.</span><span class="sxs-lookup"><span data-stu-id="5f66e-236">In the left pane of the property pages, select Build Events, and then choose the Edit Post-build button.</span></span> <span data-ttu-id="5f66e-237">Fügen Sie der Postbuildbefehlszeile die folgenden Befehle hinzu.</span><span class="sxs-lookup"><span data-stu-id="5f66e-237">Add the following commands to the post-build command line.</span></span> <span data-ttu-id="5f66e-238">(Die Batchdatei muss zuerst aufgerufen werden, um die Umgebungsvariablen zum Suchen des winmdidl-Tools festzulegen.)</span><span class="sxs-lookup"><span data-stu-id="5f66e-238">(The batch file must be called first to set the environment variables to find the winmdidl tool.)</span></span>

```cpp
call "$(DevEnvDir)..\..\vc\vcvarsall.bat" $(PlatformName)
winmdidl /outdir:output "$(TargetPath)"
midl /metadata_dir "%WindowsSdkDir%References\CommonConfiguration\Neutral" /iid "$(ProjectDir)$(TargetName)_i.c" /env win32 /h "$(ProjectDir)$(TargetName).h" /winmd "Output\$(TargetName).winmd" /W1 /char signed /nologo /winrt /dlldata "$(ProjectDir)dlldata.c" /proxy "$(ProjectDir)$(TargetName)_p.c" "Output\$(TargetName).idl"
```

<span data-ttu-id="5f66e-239">**Wichtige**für eine ARM oder X64 Projekt-Konfiguration, ändern Sie den MIDL/env Parameter X64 oder arm32.</span><span class="sxs-lookup"><span data-stu-id="5f66e-239">**Important**For an ARM or x64 project configuration, change the MIDL /env parameter to x64 or arm32.</span></span>

<span data-ttu-id="5f66e-240">Um sicherzustellen, dass die IDL-Datei ist neu generiert, jedes Mal, wenn die winmd-Datei geändert wird, ändern, **Führen Sie das Postbuildereignis** **bei der Build die Projektausgabe updates.**</span><span class="sxs-lookup"><span data-stu-id="5f66e-240">To make sure the IDL file is regenerated every time the .winmd file is changed, change **Run the post-build event** to **When the build updates the project output.**</span></span>
<span data-ttu-id="5f66e-241">Die Eigenschaftenseite Buildereignisse sollte wie folgt aussehen: ![Buildereignisse</span><span class="sxs-lookup"><span data-stu-id="5f66e-241">The Build Events property page should resemble this: ![build events</span></span>](./images/buildevents.png)

<span data-ttu-id="5f66e-242">Erstellen Sie die Projektmappe neu, um die IDL zu generieren und zu kompilieren.</span><span class="sxs-lookup"><span data-stu-id="5f66e-242">Rebuild the solution to generate and compile the IDL.</span></span>

<span data-ttu-id="5f66e-243">Sie können überprüfen, ob MIDL die Projektmappe ordnungsgemäß kompiliert hat, indem Sie im ToasterComponent-Projektverzeichnis nach ToasterComponent.h, ToasterComponent_i.c, ToasterComponent_p.c und dlldata.c suchen.</span><span class="sxs-lookup"><span data-stu-id="5f66e-243">You can verify that MIDL correctly compiled the solution by looking for ToasterComponent.h, ToasterComponent_i.c, ToasterComponent_p.c, and dlldata.c in the ToasterComponent project directory.</span></span>

## <a name="to-compile-the-proxy-and-stub-code-into-a-dll"></a><span data-ttu-id="5f66e-244">So kompilieren Sie den Proxy- und Stubcode in eine DLL-Datei</span><span class="sxs-lookup"><span data-stu-id="5f66e-244">To compile the proxy and stub code into a DLL</span></span>

<span data-ttu-id="5f66e-245">Nachdem Sie nun über die erforderlichen Dateien verfügen, können Sie diese kompilieren, um eine DLL (C++-Datei) zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="5f66e-245">Now that you have the required files, you can compile them to produce a DLL, which is a C++ file.</span></span> <span data-ttu-id="5f66e-246">Um dies so einfach wie möglich zu machen, fügen Sie ein neues Projekt hinzu, um das Erstellen der Proxys zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="5f66e-246">To make this as easy as possible, add a new project to support building the proxies.</span></span> <span data-ttu-id="5f66e-247">Öffnen Sie das Kontextmenü für die ToasterApplication-Projektmappe, und wählen Sie dann **Hinzufügen > Neues Projekt** aus.</span><span class="sxs-lookup"><span data-stu-id="5f66e-247">Open the shortcut menu for the ToasterApplication solution and then choose **Add > New Project**.</span></span> <span data-ttu-id="5f66e-248">Erweitern Sie im linken Bereich des Dialogfelds **Neues Projekt** **Visual C++ &gt; Windows &gt; ausdrückt Windows**, und wählen Sie im mittleren Bereich **DLL (UWP-apps)**.</span><span class="sxs-lookup"><span data-stu-id="5f66e-248">In the left pane of the **New Project** dialog box, expand **Visual C++ &gt; Windows &gt; Univeral Windows**, and then in the middle pane, select **DLL (UWP apps)**.</span></span> <span data-ttu-id="5f66e-249">(Beachten Sie, dass dies kein C++-Komponente für Windows-Runtime-Projekt handelt.) Nennen Sie das Projekt Proxys, und wählen Sie dann die Schaltfläche " **OK** ".</span><span class="sxs-lookup"><span data-stu-id="5f66e-249">(Notice that this is NOT a C++ Windows Runtime Component project.) Name the project Proxies and then choose the **OK** button.</span></span> <span data-ttu-id="5f66e-250">Diese Dateien werden bei Änderungen der C#-Klasse von den Postbuildereignissen aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="5f66e-250">These files will be updated by the post-build events when something changes in the C# class.</span></span>

<span data-ttu-id="5f66e-251">Standardmäßig generiert das Proxies-Projekt Headerdateien (.h) und C++-Dateien (.cpp).</span><span class="sxs-lookup"><span data-stu-id="5f66e-251">By default, the Proxies project generates header .h files and C++ .cpp files.</span></span> <span data-ttu-id="5f66e-252">Da die DLL aus den Dateien erstellt wird, die von MIDL generiert werden, sind die H- und CPP-Dateien nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="5f66e-252">Because the DLL is built from the files produced from MIDL, the .h and .cpp files are not required.</span></span> <span data-ttu-id="5f66e-253">Öffnen Sie im Projektmappen-Explorer das Kontextmenü für diese Dateien, wählen Sie **Entfernen**, und bestätigen Sie dann die Löschung.</span><span class="sxs-lookup"><span data-stu-id="5f66e-253">In Solution Explorer, open the shortcut menu for them, choose **Remove**, and then confirm the deletion.</span></span>

<span data-ttu-id="5f66e-254">Da das Projekt nun leer ist, können Sie die von MIDL generierten Dateien wieder hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="5f66e-254">Now that the project is empty, you can add back the MIDL-generated files.</span></span> <span data-ttu-id="5f66e-255">Öffnen Sie das Kontextmenü für das Projekt Proxys, und wählen Sie dann **Hinzufügen > Vorhandenes Element.**</span><span class="sxs-lookup"><span data-stu-id="5f66e-255">Open the shortcut menu for the Proxies project, and then choose **Add > Existing Item.**</span></span> <span data-ttu-id="5f66e-256">Navigieren Sie im Dialogfeld zum ToasterComponent-Projektverzeichnis, und wählen Sie die folgenden Dateien aus: ToasterComponent.h, ToasterComponent_i.c, ToasterComponent_p.c, und dlldata.c.</span><span class="sxs-lookup"><span data-stu-id="5f66e-256">In the dialog box, navigate to the ToasterComponent project directory and select these files: ToasterComponent.h, ToasterComponent_i.c, ToasterComponent_p.c, and dlldata.c files.</span></span> <span data-ttu-id="5f66e-257">Klicken Sie auf die Schaltfläche **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="5f66e-257">Choose the **Add** button.</span></span>

<span data-ttu-id="5f66e-258">Erstellen Sie im Proxies-Projekt eine DEF-Datei, um die DLL-Exporte zu definieren, die in dlldata.c beschrieben sind.</span><span class="sxs-lookup"><span data-stu-id="5f66e-258">In the Proxies project, create a .def file to define the DLL exports described in dlldata.c.</span></span> <span data-ttu-id="5f66e-259">Öffnen Sie das Kontextmenü für das Projekt, und wählen Sie dann **Hinzufügen > Neues Element**.</span><span class="sxs-lookup"><span data-stu-id="5f66e-259">Open the shortcut menu for the project, and then choose **Add > New Item**.</span></span> <span data-ttu-id="5f66e-260">Wählen Sie im linken Bereich des Dialogfelds „Code” aus, und wählen Sie dann im mittleren Bereich „Moduldefinitionsdatei” aus.</span><span class="sxs-lookup"><span data-stu-id="5f66e-260">In the left pane of the dialog box, select Code and then in the middle pane, select Module-Definition File.</span></span> <span data-ttu-id="5f66e-261">Nennen Sie die Datei „proxies.def”, und klicken Sie dann auf die Schaltfläche **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="5f66e-261">Name the file proxies.def and then choose the **Add** button.</span></span> <span data-ttu-id="5f66e-262">Öffnen Sie diese DEF-Datei und bearbeiten Sie sie, um die EXPORTS einzuschließen, die in dlldata.c definiert sind:</span><span class="sxs-lookup"><span data-stu-id="5f66e-262">Open this .def file and modify it to include the EXPORTS that are defined in dlldata.c:</span></span>

```cpp
EXPORTS
    DllCanUnloadNow         PRIVATE
    DllGetClassObject       PRIVATE
```

<span data-ttu-id="5f66e-263">Wenn Sie das Projekt jetzt erstellen, tritt ein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="5f66e-263">If you build the project now, it will fail.</span></span> <span data-ttu-id="5f66e-264">Damit dieses Projekt ordnungsgemäß kompiliert wird, müssen Sie die Einstellungen für die Kompilierung und Verknüpfung des Projekts ändern.</span><span class="sxs-lookup"><span data-stu-id="5f66e-264">To correctly compile this project, you have to change how the project is compiled and linked.</span></span> <span data-ttu-id="5f66e-265">Öffnen Sie im Projektmappen-Explorer das Kontextmenü für das Proxies-Projekt, und wählen Sie dann **Eigenschaften** aus.</span><span class="sxs-lookup"><span data-stu-id="5f66e-265">In Solution Explorer, open the shortcut menu for the Proxies project and then choose **Properties**.</span></span> <span data-ttu-id="5f66e-266">Ändern Sie die Eigenschaftenseiten wie folgt.</span><span class="sxs-lookup"><span data-stu-id="5f66e-266">Change the property pages as follows.</span></span>

<span data-ttu-id="5f66e-267">Wählen Sie im linken Bereich **C/C++ > Präprozessor** und dann im rechten Bereich **Präprozessordefinitionen** aus, klicken Sie auf die Schaltfläche mit dem Pfeil nach unten und dann auf **Bearbeiten**.</span><span class="sxs-lookup"><span data-stu-id="5f66e-267">In the left pane, select **C/C++ > Preprocessor**, and then in the right pane, select **Preprocessor Definitions**, choose the down-arrow button, and then select **Edit**.</span></span> <span data-ttu-id="5f66e-268">Fügen Sie diese Definitionen in das Feld ein:</span><span class="sxs-lookup"><span data-stu-id="5f66e-268">Add these definitions in the box:</span></span>

```cpp
WIN32;_WINDOWS
```
<span data-ttu-id="5f66e-269">Ändern Sie unter **C/C++ > Vorkompilierte Header** die Option **Vorkompilierter Header** in **Vorkompilierte Header nicht verwenden**, und klicken Sie dann auf die Schaltfläche **Übernehmen**.</span><span class="sxs-lookup"><span data-stu-id="5f66e-269">Under **C/C++ > Precompiled Headers**, change **Precompiled Header** to **Not Using Precompiled Headers**, and then choose the **Apply** button.</span></span>

<span data-ttu-id="5f66e-270">Unter **Linker > Allgemein**, ändern Sie **Importbibliothek ignorieren** zu **Ye**s, und wählen Sie dann die Schaltfläche **anwenden** .</span><span class="sxs-lookup"><span data-stu-id="5f66e-270">Under **Linker > General**, change **Ignore Import Library** to **Ye**s, and then choose the **Apply** button.</span></span>

<span data-ttu-id="5f66e-271">Wählen Sie unter **Linker > Eingabe** die Option **Zusätzliche Abhängigkeiten** aus, klicken Sie auf die Schaltfläche mit dem Pfeil nach unten, und klicken Sie dann auf **Bearbeiten**.</span><span class="sxs-lookup"><span data-stu-id="5f66e-271">Under **Linker > Input**, select **Additional Dependencies**, choose the down-arrow button, and then select **Edit**.</span></span> <span data-ttu-id="5f66e-272">Fügen Sie diesen Text in das Feld ein:</span><span class="sxs-lookup"><span data-stu-id="5f66e-272">Add this text in the box:</span></span>

```cpp
rpcrt4.lib;runtimeobject.lib
```

<span data-ttu-id="5f66e-273">Fügen Sie diese Bibliotheken nicht direkt in die Listenzeile ein.</span><span class="sxs-lookup"><span data-stu-id="5f66e-273">Do not paste these libs directly into the list row.</span></span> <span data-ttu-id="5f66e-274">Verwenden Sie das **Eingabefeld**, um sicherzustellen, dass MSBuild in Visual Studio die richtigen zusätzlichen Abhängigkeiten beibehält.</span><span class="sxs-lookup"><span data-stu-id="5f66e-274">Use the **Edit** box to ensure that MSBuild in Visual Studio will maintain the correct additional dependencies.</span></span>

<span data-ttu-id="5f66e-275">Wenn Sie diese Änderungen vorgenommen haben, klicken Sie im Dialogfeld **Eigenschaftenseiten** auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="5f66e-275">When you have made these changes, choose the **OK** button in the **Property Pages** dialog box.</span></span>

<span data-ttu-id="5f66e-276">Legen Sie als Nächstes eine Abhängigkeit vom ToasterComponent-Projekt fest.</span><span class="sxs-lookup"><span data-stu-id="5f66e-276">Next, take a dependency on the ToasterComponent project.</span></span> <span data-ttu-id="5f66e-277">Dadurch wird sichergestellt, dass der Toaster vor dem Proxies-Projekt erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="5f66e-277">This ensures that the Toaster will build before the proxy project builds.</span></span> <span data-ttu-id="5f66e-278">Dies ist erforderlich, da das Toaster-Projekt für das Generieren der Dateien zum Erstellen des Proxys zuständig ist.</span><span class="sxs-lookup"><span data-stu-id="5f66e-278">This is required because the Toaster project is responsible for generating the files to build the proxy.</span></span>

<span data-ttu-id="5f66e-279">Öffnen Sie das Kontextmenü für das Proxies-Projekt, und wählen Sie dann „Projektabhängigkeiten” aus.</span><span class="sxs-lookup"><span data-stu-id="5f66e-279">Open the shortcut menu for the Proxies project and then choose Project Dependencies.</span></span> <span data-ttu-id="5f66e-280">Aktivieren Sie die Kontrollkästchen, um anzugeben, dass das Proxies-Projekt vom ToasterComponent-Projekt abhängig ist, damit Visual Studio die Projekte in der richtigen Reihenfolge erstellt.</span><span class="sxs-lookup"><span data-stu-id="5f66e-280">Select the check boxes to indicate that the Proxies project depends on the ToasterComponent project, to ensure that Visual Studio builds them in the correct order.</span></span>

<span data-ttu-id="5f66e-281">Stellen Sie sicher, dass die Projektmappe ordnungsgemäß erstellt wird, indem Sie in Visual Studio in der Menüleiste **Erstellen > Projektmappe neu erstellen** auswählen.</span><span class="sxs-lookup"><span data-stu-id="5f66e-281">Verify that the solution builds correctly by choosing **Build > Rebuild Solution** on the Visual Studio menu bar.</span></span>


## <a name="to-register-the-proxy-and-stub"></a><span data-ttu-id="5f66e-282">So registrieren Sie den Proxy und den Stub</span><span class="sxs-lookup"><span data-stu-id="5f66e-282">To register the proxy and stub</span></span>

<span data-ttu-id="5f66e-283">Öffnen Sie im ToasterApplication-Projekt das Kontextmenü für „package.appxmanifest”, und wählen Sie dann **Öffnen mit** aus.</span><span class="sxs-lookup"><span data-stu-id="5f66e-283">In the ToasterApplication project, open the shortcut menu for package.appxmanifest and then choose **Open With**.</span></span> <span data-ttu-id="5f66e-284">Wählen Sie im Dialogfeld Öffnen mit die Option **XML-Text-Editor** aus, und klicken Sie dann auf die Schaltfläche **OK**.</span><span class="sxs-lookup"><span data-stu-id="5f66e-284">In the Open With dialog box, select **XML Text Editor** and then choose the **OK** button.</span></span> <span data-ttu-id="5f66e-285">Um eine windows.activatableClass.proxyStub-Erweiterungsregistrierung bereitzustellen, wird XML-Code eingefügt, der auf den GUIDs im Proxy basiert.</span><span class="sxs-lookup"><span data-stu-id="5f66e-285">We're going to paste in some XML that provides a windows.activatableClass.proxyStub extension registration and which are based on the GUIDs in the proxy.</span></span> <span data-ttu-id="5f66e-286">Öffnen Sie „ToasterComponent_i.c”, um die GUIDs für die .appxmanifest-Datei zu suchen.</span><span class="sxs-lookup"><span data-stu-id="5f66e-286">To find the GUIDs to use in the .appxmanifest file, open ToasterComponent_i.c.</span></span> <span data-ttu-id="5f66e-287">Suchen Sie Einträge, die denen im folgenden Beispiel ähneln</span><span class="sxs-lookup"><span data-stu-id="5f66e-287">Find entries that resemble the ones in the following example.</span></span> <span data-ttu-id="5f66e-288">Beachten Sie außerdem die Definitionen für IToast, IToaster sowie für eine dritte Schnittstelle – einen typisierten Ereignishandler mit den beiden Parametern: Toaster und Toast.</span><span class="sxs-lookup"><span data-stu-id="5f66e-288">Also notice the definitions for IToast, IToaster, and a third interface—a typed event handler that has two parameters: a Toaster and Toast.</span></span> <span data-ttu-id="5f66e-289">Dies entspricht dem Ereignis, das in der Toaster-Klasse definiert ist.</span><span class="sxs-lookup"><span data-stu-id="5f66e-289">This matches the event that's defined in the Toaster class.</span></span> <span data-ttu-id="5f66e-290">Die GUIDs für IToast und IToaster stimmen mit den GUIDs überein, die für die Schnittstellen in der C#-Datei definiert sind.</span><span class="sxs-lookup"><span data-stu-id="5f66e-290">Notice that the GUIDs for IToast and IToaster match the GUIDs that are defined on the interfaces in the C# file.</span></span> <span data-ttu-id="5f66e-291">Da die typisierte Ereignishandlerschnittstelle automatisch generiert wird, wird die GUID für diese Schnittstelle ebenfalls automatisch generiert.</span><span class="sxs-lookup"><span data-stu-id="5f66e-291">Because the typed event handler interface is autogenerated, the GUID for this interface is also autogenerated.</span></span>

```cpp
MIDL_DEFINE_GUID(IID, IID___FITypedEventHandler_2_ToasterComponent__CToaster_ToasterComponent__CToast,0x1ecafeff,0x1ee1,0x504a,0x9a,0xf5,0xa6,0x8c,0x6f,0xb2,0xb4,0x7d);

MIDL_DEFINE_GUID(IID, IID___x_ToasterComponent_CIToast,0xF8D30778,0x9EAF,0x409C,0xBC,0xCD,0xC8,0xB2,0x44,0x42,0xB0,0x9B);

MIDL_DEFINE_GUID(IID, IID___x_ToasterComponent_CIToaster,0xE976784C,0xAADE,0x4EA4,0xA4,0xC0,0xB0,0xC2,0xFD,0x13,0x07,0xC3);
```

<span data-ttu-id="5f66e-292">Die GUIDs werden jetzt kopiert, in einen hinzugefügten Knoten mit Namen „Extensions” in „package.appxmanifest” eingefügt und anschließend neu formatiert.</span><span class="sxs-lookup"><span data-stu-id="5f66e-292">Now we copy the GUIDs, paste them in package.appxmanifest in a node that we add and name Extensions, and then reformat them.</span></span> <span data-ttu-id="5f66e-293">Der Manifesteintrag ähnelt dem folgenden Beispiel – denken Sie aber auch hier daran, eigene GUIDs zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="5f66e-293">The manifest entry resembles the following example—but again, remember to use your own GUIDs.</span></span> <span data-ttu-id="5f66e-294">Beachten Sie, dass die ClassId-GUID in XML mit „ITypedEventHandler2” identisch ist.</span><span class="sxs-lookup"><span data-stu-id="5f66e-294">Notice that the ClassId GUID in the XML is the same as ITypedEventHandler2.</span></span> <span data-ttu-id="5f66e-295">Dies liegt daran, dass diese GUID als erste in ToasterComponent_i.c aufgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="5f66e-295">This is because that GUID is the first one that's listed in ToasterComponent_i.c.</span></span> <span data-ttu-id="5f66e-296">Bei diesen GUIDs wird zwischen Groß-/Kleinschreibung unterschieden.</span><span class="sxs-lookup"><span data-stu-id="5f66e-296">The GUIDs here are case-insensitive.</span></span> <span data-ttu-id="5f66e-297">Anstatt die GUIDs für IToast und IToaster manuell neu zu formatieren, können Sie zurück zur Schnittstellendefinitionen wechseln und den GuidAttribute-Wert suchen, der das richtige Format aufweist.</span><span class="sxs-lookup"><span data-stu-id="5f66e-297">Instead of manually reformatting the GUIDs for IToast and IToaster, you can go back into the interface definitions and get the GuidAttribute value, which has the correct format.</span></span> <span data-ttu-id="5f66e-298">In C++ ist eine richtig formatierte GUID im Kommentar enthalten.</span><span class="sxs-lookup"><span data-stu-id="5f66e-298">In C++, there is a correctly-formatted GUID in the comment.</span></span> <span data-ttu-id="5f66e-299">Auf jeden Fall müssen Sie die GUID, die für die ClassId und für den Ereignishandler verwendet wird, manuell neu formatieren.</span><span class="sxs-lookup"><span data-stu-id="5f66e-299">In any case, you must manually reformat the GUID that's used for both the ClassId and the event handler.</span></span>

```cpp
      <Extensions> <!--Use your own GUIDs!!!-->
        <Extension Category="windows.activatableClass.proxyStub">
          <ProxyStub ClassId="1ecafeff-1ee1-504a-9af5-a68c6fb2b47d">
            <Path>Proxies.dll</Path>
            <Interface Name="IToast" InterfaceId="F8D30778-9EAF-409C-BCCD-C8B24442B09B"/>
            <Interface Name="IToaster"  InterfaceId="E976784C-AADE-4EA4-A4C0-B0C2FD1307C3"/>  
            <Interface Name="ITypedEventHandler_2_ToasterComponent__CToaster_ToasterComponent__CToast" InterfaceId="1ecafeff-1ee1-504a-9af5-a68c6fb2b47d"/>
          </ProxyStub>      
        </Extension>
      </Extensions>
```

<span data-ttu-id="5f66e-300">Fügen Sie den „Extensions”-XML-Knoten als direkt dem Package-Knoten untergeordnetes Element und einen Peer, z.B. den „Resources”-Knoten, ein.</span><span class="sxs-lookup"><span data-stu-id="5f66e-300">Paste the Extensions XML node as a direct child of the Package node, and a peer of, for example, the Resources node.</span></span>

<span data-ttu-id="5f66e-301">Bevor Sie fortfahren, muss Folgendes sichergestellt sein: </span><span class="sxs-lookup"><span data-stu-id="5f66e-301">Before moving on, it’s important to ensure that:</span></span>

-   <span data-ttu-id="5f66e-302">ProxyStub ClassId wird auf die erste GUID in der Datei ToasterComponent\_i.c festgelegt.</span><span class="sxs-lookup"><span data-stu-id="5f66e-302">The ProxyStub ClassId is set to the first GUID in the ToasterComponent\_i.c file.</span></span> <span data-ttu-id="5f66e-303">Verwenden Sie die erste GUID, die in dieser Datei für die classId definiert ist.</span><span class="sxs-lookup"><span data-stu-id="5f66e-303">Use the first GUID that's defined in this file for the classId.</span></span> <span data-ttu-id="5f66e-304">(Diese ist möglicherweise mit der GUID für „ITypedEventHandler2” identisch.)</span><span class="sxs-lookup"><span data-stu-id="5f66e-304">(This might be the same as the GUID for ITypedEventHandler2.)</span></span>
-   <span data-ttu-id="5f66e-305">„Path” ist der relative Pfad des Pakets der Proxybinärdatei.</span><span class="sxs-lookup"><span data-stu-id="5f66e-305">The Path is the package relative path of the proxy binary.</span></span> <span data-ttu-id="5f66e-306">(In dieser exemplarischen Vorgehensweise befindet sich „proxies.dll” im gleichen Ordner wie „ToasterApplication.winmd”.)</span><span class="sxs-lookup"><span data-stu-id="5f66e-306">(In this walkthrough, proxies.dll is in the same folder as ToasterApplication.winmd.)</span></span>
-   <span data-ttu-id="5f66e-307">Die GUIDs haben das richtige Format.</span><span class="sxs-lookup"><span data-stu-id="5f66e-307">The GUIDs are in the correct format.</span></span> <span data-ttu-id="5f66e-308">(Hier können leicht Fehler passieren.)</span><span class="sxs-lookup"><span data-stu-id="5f66e-308">(This is easy to get wrong.)</span></span>
-   <span data-ttu-id="5f66e-309">Die Schnittstellen-IDs im Manifest übereinstimmen, die IIDs in ToasterComponent\_i.c-Datei.</span><span class="sxs-lookup"><span data-stu-id="5f66e-309">The interface IDs in the manifest match the IIDs in ToasterComponent\_i.c file.</span></span>
-   <span data-ttu-id="5f66e-310">Die Namen der Schnittstellen sind im Manifest eindeutig.</span><span class="sxs-lookup"><span data-stu-id="5f66e-310">The interface names are unique in the manifest.</span></span> <span data-ttu-id="5f66e-311">Da diese nicht vom System verwendet werden, können Sie die Werte festlegen.</span><span class="sxs-lookup"><span data-stu-id="5f66e-311">Because these are not used by the system, you can choose the values.</span></span> <span data-ttu-id="5f66e-312">Es sollten Schnittstellennamen gewählt werden, die eindeutig mit Schnittstellen übereinstimmen, die Sie definiert haben.</span><span class="sxs-lookup"><span data-stu-id="5f66e-312">It is a good practice to choose interface names that clearly match interfaces that you have defined.</span></span> <span data-ttu-id="5f66e-313">Bei generierten Schnittstellen sollten die Namen auf die generierten Schnittstellen schließen lassen.</span><span class="sxs-lookup"><span data-stu-id="5f66e-313">For generated interfaces, the names should be indicative of the generated interfaces.</span></span> <span data-ttu-id="5f66e-314">Die ToasterComponent\_i.c-Datei können Sie die Schnittstellennamen zu generieren.</span><span class="sxs-lookup"><span data-stu-id="5f66e-314">You can use the ToasterComponent\_i.c file to help you generate interface names.</span></span>

<span data-ttu-id="5f66e-315">Wenn Sie die Projektmappe jetzt auszuführen versuchen, erhalten Sie eine Fehlermeldung, die angibt, dass „proxies.dll” nicht Teil der Nutzlast ist.</span><span class="sxs-lookup"><span data-stu-id="5f66e-315">If you try to run the solution now, you will get an error that proxies.dll is not part of the payload.</span></span> <span data-ttu-id="5f66e-316">Öffnen Sie im ToasterApplication-Projekt das Kontextmenü für den Ordner **Verweise**, und wählen Sie **Verweis hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="5f66e-316">Open the shortcut menu for the **References** folder in the ToasterApplication project and then choose **Add Reference**.</span></span> <span data-ttu-id="5f66e-317">Aktivieren Sie das Kontrollkästchen neben dem Proxies-Projekt.</span><span class="sxs-lookup"><span data-stu-id="5f66e-317">Select the check box next to the Proxies project.</span></span> <span data-ttu-id="5f66e-318">Stellen Sie außerdem sicher, dass auch das Kontrollkästchen neben „ToasterComponent” aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="5f66e-318">Also, make sure that the check box next to ToasterComponent is also selected.</span></span> <span data-ttu-id="5f66e-319">Klicken Sie auf die Schaltfläche **OK**.</span><span class="sxs-lookup"><span data-stu-id="5f66e-319">Choose the **OK** button.</span></span>

<span data-ttu-id="5f66e-320">Das Projekt sollte nun erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="5f66e-320">The project should now build.</span></span> <span data-ttu-id="5f66e-321">Führen Sie das Projekt aus, und überprüfen Sie, ob Sie ein Popup erstellen können.</span><span class="sxs-lookup"><span data-stu-id="5f66e-321">Run the project and verify that you can make toast.</span></span>

## <a name="related-topics"></a><span data-ttu-id="5f66e-322">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="5f66e-322">Related topics</span></span>

* [<span data-ttu-id="5f66e-323">Erstellen von Komponenten für Windows-Runtime in C++</span><span class="sxs-lookup"><span data-stu-id="5f66e-323">Creating Windows Runtime Components in C++</span></span>](creating-windows-runtime-components-in-cpp.md)
