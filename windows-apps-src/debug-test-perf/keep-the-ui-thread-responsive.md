---
ms.assetid: FA25562A-FE62-4DFC-9084-6BD6EAD73636
title: Aufrechterhalten der Reaktionsfähigkeit des UI-Threads
description: Benutzer erwarten, dass eine App beim Durchführen einer Berechnung reaktionsfähig bleibt, unabhängig vom jeweiligen Computertyp.
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 8cd5df1d22189698f6544af4ab72c09425531602
ms.sourcegitcommit: b11f305dbf7649c4b68550b666487c77ea30d98f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "7852261"
---
# <a name="keep-the-ui-thread-responsive"></a><span data-ttu-id="c3b39-104">Aufrechterhalten der Reaktionsfähigkeit des UI-Threads</span><span class="sxs-lookup"><span data-stu-id="c3b39-104">Keep the UI thread responsive</span></span>


<span data-ttu-id="c3b39-105">Benutzer erwarten, dass eine App beim Durchführen einer Berechnung reaktionsfähig bleibt, unabhängig vom jeweiligen Computertyp.</span><span class="sxs-lookup"><span data-stu-id="c3b39-105">Users expect an app to remain responsive while it does computation, regardless of the type of machine.</span></span> <span data-ttu-id="c3b39-106">Das bedeutet für jede App etwas anderes.</span><span class="sxs-lookup"><span data-stu-id="c3b39-106">This means different things for different apps.</span></span> <span data-ttu-id="c3b39-107">Für einige Apps bedeutet dies z.B. Folgendes: realistischere physische Effekte bereitstellen, Daten vom Datenträger oder aus dem Internet schneller laden, komplexe Szenen schnell darstellen, schnell zwischen Seiten navigieren, Anweisungen im Nu finden oder schnelles Verarbeiten von Daten.</span><span class="sxs-lookup"><span data-stu-id="c3b39-107">For some, this translates to providing more realistic physics, loading data from disk or the web faster, quickly presenting complex scenes and navigating between pages, finding directions in a snap, or rapidly processing data.</span></span> <span data-ttu-id="c3b39-108">Unabhängig von der Art der Berechnung möchten Benutzer, dass die App auf ihre Eingabe reagiert. Es stört sie, wenn die App scheinbar nicht reagiert, während sie "denkt".</span><span class="sxs-lookup"><span data-stu-id="c3b39-108">Regardless of the type of computation, users want their app to act on their input and eliminate instances where it appears unresponsive while it "thinks".</span></span>

<span data-ttu-id="c3b39-109">Ihre App ist ereignisgesteuert, was bedeutet, dass Ihr Code in Reaktion auf ein Ereignis eine Funktion erfüllt und anschließend befindet sich die App im Leerlauf und wartet auf das nächste Ereignis.</span><span class="sxs-lookup"><span data-stu-id="c3b39-109">Your app is event-driven, which means that your code performs work in response to an event and then it sits idle until the next.</span></span> <span data-ttu-id="c3b39-110">Plattformcode für die Benutzeroberfläche (Layout, Eingabe, Auslösen von Ereignissen usw.) und Ihr App-Code für die Benutzeroberfläche werden alle im gleichen UI-Thread ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="c3b39-110">Platform code for UI (layout, input, raising events, etc.) and your app’s code for UI all are executed on the same UI thread.</span></span> <span data-ttu-id="c3b39-111">Nur eine Anweisung kann jeweils für diesen Thread ausgeführt werden, wenn Ihr App-Code also zu lange für das Verarbeiten eines Ereignisses benötigt, kann das Framework das Layout nicht ausführen oder neue Ereignisse auslösen, die Interaktionen des Benutzers darstellen.</span><span class="sxs-lookup"><span data-stu-id="c3b39-111">Only one instruction can execute on that thread at a time so if your app code takes too long to process an event then the framework can’t run layout or raise new events representing user interaction.</span></span> <span data-ttu-id="c3b39-112">Das heißt, die Reaktionsfähigkeit Ihrer App hängt direkt davon ab, ob der UI-Thread zum Durchführen von Arbeit verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="c3b39-112">The responsiveness of your app is related to the availability of the UI thread to process work.</span></span>

<span data-ttu-id="c3b39-113">Sie müssen den UI-Thread verwenden, um fast alle Änderungen am UI-Thread vorzunehmen, einschließlich der Erstellung von UI-Typen und des Zugriffs auf ihre Member.</span><span class="sxs-lookup"><span data-stu-id="c3b39-113">You need to use the UI thread to make almost all changes to the UI thread, including creating UI types and accessing their members.</span></span> <span data-ttu-id="c3b39-114">Sie können die UI nicht aus einem Hintergrundthread aktualisieren, können jedoch mit [**CoreDispatcher.RunAsync**](https://msdn.microsoft.com/library/windows/apps/Hh750317) eine Nachricht posten, damit der Code dort ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c3b39-114">You can't update the UI from a background thread but you can post a message to it with [**CoreDispatcher.RunAsync**](https://msdn.microsoft.com/library/windows/apps/Hh750317) to cause code to be run there.</span></span>

> <span data-ttu-id="c3b39-115">**Hinweis:** die einzige Ausnahme besteht darin, einen separaten Renderthread, die UI-Änderungen anwenden können, die ohne Auswirkungen auf die Eingabeverarbeitung oder das Basislayout vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="c3b39-115">**Note**The one exception is that there's a separate render thread that can apply UI changes that won't affect how input is handled or the basic layout.</span></span> <span data-ttu-id="c3b39-116">Viele Animationen und Übergänge, die sich nicht auf das Layout auswirken, können z. B. auf diesem Renderthread ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="c3b39-116">For example many animations and transitions that don’t affect layout can run on this render thread.</span></span>

## <a name="delay-element-instantiation"></a><span data-ttu-id="c3b39-117">Verzögern der Element-Instanziierung</span><span class="sxs-lookup"><span data-stu-id="c3b39-117">Delay element instantiation</span></span>

<span data-ttu-id="c3b39-118">Einige der langsamsten Phasen in einer App können der Start und das Wechseln zwischen Ansichten sein.</span><span class="sxs-lookup"><span data-stu-id="c3b39-118">Some of the slowest stages in an app can include startup, and switching views.</span></span> <span data-ttu-id="c3b39-119">Machen Sie sich nicht mehr Arbeit als nötig, um die Benutzeroberfläche anzuzeigen, die dem Benutzer zuerst angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="c3b39-119">Don't do more work than necessary to bring up the UI that the user sees initially.</span></span> <span data-ttu-id="c3b39-120">Erstellen Sie beispielsweise nicht die Benutzeroberfläche für die schrittweise offengelegte Benutzeroberfläche und den Inhalt von Popups.</span><span class="sxs-lookup"><span data-stu-id="c3b39-120">For example, don't create the UI for progressively-disclosed UI and the contents of popups.</span></span>

-   <span data-ttu-id="c3b39-121">Verwenden Sie [x:Load attribute](../xaml-platform/x-load-attribute.md) oder [x:DeferLoadStrategy](https://msdn.microsoft.com/library/windows/apps/Mt204785), um Elemente verzögert zu instanziieren.</span><span class="sxs-lookup"><span data-stu-id="c3b39-121">Use [x:Load attribute](../xaml-platform/x-load-attribute.md) or [x:DeferLoadStrategy](https://msdn.microsoft.com/library/windows/apps/Mt204785) to delay-instantiate elements.</span></span>
-   <span data-ttu-id="c3b39-122">Fügen Sie programmgesteuerte Elemente nach Bedarf in der Struktur ein.</span><span class="sxs-lookup"><span data-stu-id="c3b39-122">Programmatically insert elements into the tree on-demand.</span></span>

<span data-ttu-id="c3b39-123">[**CoreDispatcher.RunIdleAsync**](https://msdn.microsoft.com/library/windows/apps/Hh967918)-Warteschlangen eignen sich für die Verarbeitung des UI-Threads, wenn er nicht aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="c3b39-123">[**CoreDispatcher.RunIdleAsync**](https://msdn.microsoft.com/library/windows/apps/Hh967918) queues work for the UI thread to process when it's not busy.</span></span>

## <a name="use-asynchronous-apis"></a><span data-ttu-id="c3b39-124">Verwenden von asynchronen APIs</span><span class="sxs-lookup"><span data-stu-id="c3b39-124">Use asynchronous APIs</span></span>

<span data-ttu-id="c3b39-125">Zur Verbesserung der Reaktionsfähigkeit der App stellt die Plattform asynchrone Versionen vieler APIs bereit.</span><span class="sxs-lookup"><span data-stu-id="c3b39-125">To help keep your app responsive, the platform provides asynchronous versions of many of its APIs.</span></span> <span data-ttu-id="c3b39-126">Eine asynchrone API stellt sicher, dass Ihr aktiver Ausführungsthread nie für längere Zeit blockiert wird.</span><span class="sxs-lookup"><span data-stu-id="c3b39-126">An asynchronous API ensures that your active execution thread never blocks for a significant amount of time.</span></span> <span data-ttu-id="c3b39-127">Wenn Sie ein API-Element aus dem UI-Thread heraus aufrufen, verwenden Sie die asynchrone Version, sofern diese verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="c3b39-127">When you call an API from the UI thread, use the asynchronous version if it's available.</span></span> <span data-ttu-id="c3b39-128">Weitere Informationen zum Programmieren mit **async**-Strukturen finden Sie unter [Asynchrone Programmierung](https://msdn.microsoft.com/library/windows/apps/Mt187335) oder unter [Aufrufen asynchroner APIs in C# oder Visual Basic](https://msdn.microsoft.com/library/windows/apps/Mt187337).</span><span class="sxs-lookup"><span data-stu-id="c3b39-128">For more info about programming with **async** patterns, see [Asynchronous programming](https://msdn.microsoft.com/library/windows/apps/Mt187335) or [Call asynchronous APIs in C# or Visual Basic](https://msdn.microsoft.com/library/windows/apps/Mt187337).</span></span>

## <a name="offload-work-to-background-threads"></a><span data-ttu-id="c3b39-129">Auslagern der Arbeit an Hintergrundthreads</span><span class="sxs-lookup"><span data-stu-id="c3b39-129">Offload work to background threads</span></span>

<span data-ttu-id="c3b39-130">Schreiben Sie Ereignishandler, die schnell zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="c3b39-130">Write event handlers to return quickly.</span></span> <span data-ttu-id="c3b39-131">In Fällen, in denen umfassende Arbeiten vorgenommen werden müssen, sollten Sie sie in einem Hintergrundthread planen und zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="c3b39-131">In cases where a non-trivial amount of work needs to be performed, schedule it on a background thread and return.</span></span>

<span data-ttu-id="c3b39-132">Mit dem Operator **await** in C#, dem Operator **Await** in Visual Basic oder mit Delegaten in C++ können Sie Arbeit auch asynchron planen.</span><span class="sxs-lookup"><span data-stu-id="c3b39-132">You can schedule work asynchronously by using the **await** operator in C#, the **Await** operator in Visual Basic, or delegates in C++.</span></span> <span data-ttu-id="c3b39-133">Dies garantiert jedoch nicht, dass die geplante Arbeit in einem Hintergrundthread ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c3b39-133">But this doesn't guarantee that the work you schedule will run on a background thread.</span></span> <span data-ttu-id="c3b39-134">Viele der UWP-APIs planen für Sie die Arbeit im Hintergrundthread, wenn Sie Ihren App-Code jedoch nur mit **await** oder einem Delegaten aufrufen, führen Sie diesen Delegaten oder diese Methode in einem UI-Thread aus.</span><span class="sxs-lookup"><span data-stu-id="c3b39-134">Many of the Universal Windows Platform (UWP) APIs schedule work in the background thread for you, but if you call your app code by using only **await** or a delegate, you run that delegate or method on the UI thread.</span></span> <span data-ttu-id="c3b39-135">Wenn Sie Ihren App-Code in einem Hintergrundthread ausführen möchten, müssen Sie dies explizit angeben.</span><span class="sxs-lookup"><span data-stu-id="c3b39-135">You have to explicitly say when you want to run your app code on a background thread.</span></span> <span data-ttu-id="c3b39-136">In c# und Visual Basic können Sie dies erreichen, indem Sie Code an [**Task.Run**](https://msdn.microsoft.com/library/windows/apps/xaml/system.threading.tasks.task.run.aspx)übergeben.</span><span class="sxs-lookup"><span data-stu-id="c3b39-136">In C# and Visual Basic you can accomplish this by passing code to [**Task.Run**](https://msdn.microsoft.com/library/windows/apps/xaml/system.threading.tasks.task.run.aspx).</span></span>

<span data-ttu-id="c3b39-137">Denken Sie daran, dass nur aus dem UI-Thread auf UI-Elemente zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="c3b39-137">Remember that UI elements may only be accessed from the UI thread.</span></span> <span data-ttu-id="c3b39-138">Verwenden Sie den UI-Thread für den Zugriff auf UI-Elemente vor dem Starten der Hintergrundverarbeitung und/oder der Verwendung von [**CoreDispatcher.RunAsync**](https://msdn.microsoft.com/library/windows/apps/Hh750317) oder [**CoreDispatcher.RunIdleAsync**](https://msdn.microsoft.com/library/windows/apps/Hh967918) im Hintergrundthread.</span><span class="sxs-lookup"><span data-stu-id="c3b39-138">Use the UI thread to access UI elements before launching the background work and/or use [**CoreDispatcher.RunAsync**](https://msdn.microsoft.com/library/windows/apps/Hh750317) or [**CoreDispatcher.RunIdleAsync**](https://msdn.microsoft.com/library/windows/apps/Hh967918) on the background thread.</span></span>

<span data-ttu-id="c3b39-139">Ein Beispiel für Arbeit, die in einem Hintergrundthread ausgeführt werden kann, ist die Berechnung der Computer-KI in einem Spiel.</span><span class="sxs-lookup"><span data-stu-id="c3b39-139">An example of work that can be performed on a background thread is the calculating of computer AI in a game.</span></span> <span data-ttu-id="c3b39-140">Die Ausführung des Codes zur Berechnung der nächsten Aktion des Computers nimmt viel Zeit in Anspruch.</span><span class="sxs-lookup"><span data-stu-id="c3b39-140">The code that calculates the computer's next move can take a lot of time to execute.</span></span>

```csharp
public class AsyncExample
{
    private async void NextMove-Click(object sender, RoutedEventArgs e)
    {
        // The await causes the handler to return immediately.
        await System.Threading.Tasks.Task.Run(() => ComputeNextMove());
        // Now update the UI with the results.
        // ...
    }

    private async System.Threading.Tasks.Task ComputeNextMove()
    {
        // Perform background work here.
        // Don't directly access UI elements from this method.
    }
}
```

> [!div class="tabbedCodeSnippets"]
> ```csharp
> public class Example
> {
>     // ...
>     private async void NextMove-Click(object sender, RoutedEventArgs e)
>     {
>         await Task.Run(() => ComputeNextMove());
>         // Update the UI with results
>     }
> 
>     private async Task ComputeNextMove()
>     {
>         // ...
>     }
>     // ...
> }
> ```
> ```vb
> Public Class Example
>     ' ...
>     Private Async Sub NextMove-Click(ByVal sender As Object, ByVal e As RoutedEventArgs)
>         Await Task.Run(Function() ComputeNextMove())
>         ' update the UI with results
>     End Sub
> 
>     Private Async Function ComputeNextMove() As Task
>         ' ...
>     End Function
>     ' ...
> End Class
> ```

<span data-ttu-id="c3b39-141">In diesem Beispiel wird der `NextMove-Click`-Handler bei **await** zurückgegeben, damit der UI-Thread reaktionsfähig bleibt.</span><span class="sxs-lookup"><span data-stu-id="c3b39-141">In this example, the `NextMove-Click` handler returns at the **await** in order to keep the UI thread responsive.</span></span> <span data-ttu-id="c3b39-142">Die Ausführung wird jedoch in diesem Handler fortgesetzt, nachdem `ComputeNextMove` abgeschlossen ist (in einem Hintergrundthread ausgeführt).</span><span class="sxs-lookup"><span data-stu-id="c3b39-142">But execution picks up in that handler again after `ComputeNextMove` (which executes on a background thread) completes.</span></span> <span data-ttu-id="c3b39-143">Der restliche Code im Handler aktualisiert die UI mit den Ergebnissen.</span><span class="sxs-lookup"><span data-stu-id="c3b39-143">The remaining code in the handler updates the UI with the results.</span></span>

> <span data-ttu-id="c3b39-144">**Hinweis:** es ist auch eine [**ThreadPool**](https://msdn.microsoft.com/library/windows/apps/BR229621) und [**ThreadPoolTimer**](https://msdn.microsoft.com/library/windows/apps/windows.system.threading.threadpooltimer.aspx) API für die UWP, die für ähnliche Szenarien verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="c3b39-144">**Note**There's also a [**ThreadPool**](https://msdn.microsoft.com/library/windows/apps/BR229621) and [**ThreadPoolTimer**](https://msdn.microsoft.com/library/windows/apps/windows.system.threading.threadpooltimer.aspx) API for the UWP, which can be used for similar scenarios.</span></span> <span data-ttu-id="c3b39-145">Weitere Informationen finden Sie unter [Threading und asynchrone Programmierung](https://msdn.microsoft.com/library/windows/apps/Mt187340).</span><span class="sxs-lookup"><span data-stu-id="c3b39-145">For more info, see [Threading and async programming](https://msdn.microsoft.com/library/windows/apps/Mt187340).</span></span>

## <a name="related-topics"></a><span data-ttu-id="c3b39-146">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="c3b39-146">Related topics</span></span>

* [<span data-ttu-id="c3b39-147">Benutzerdefinierte Benutzerinteraktionen</span><span class="sxs-lookup"><span data-stu-id="c3b39-147">Custom user interactions</span></span>](https://msdn.microsoft.com/library/windows/apps/Mt185599)
