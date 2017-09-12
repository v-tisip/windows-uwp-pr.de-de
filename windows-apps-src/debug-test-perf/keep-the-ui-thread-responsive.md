---
author: jwmsft
ms.assetid: FA25562A-FE62-4DFC-9084-6BD6EAD73636
title: "Aufrechterhalten der Reaktionsfähigkeit des UI-Threads"
description: "Benutzer erwarten, dass eine App beim Durchführen einer Berechnung reaktionsfähig bleibt, unabhängig vom jeweiligen Computertyp."
ms.author: jimwalk
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.openlocfilehash: d5be2a8ea14f35d048b4402f2cfb1018d5998c3d
ms.sourcegitcommit: ec18e10f750f3f59fbca2f6a41bf1892072c3692
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2017
---
# <a name="keep-the-ui-thread-responsive"></a><span data-ttu-id="7c9a0-104">Aufrechterhalten der Reaktionsfähigkeit des UI-Threads</span><span class="sxs-lookup"><span data-stu-id="7c9a0-104">Keep the UI thread responsive</span></span>

<span data-ttu-id="7c9a0-105">\[ Aktualisiert für UWP-Apps unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="7c9a0-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="7c9a0-106">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span><span class="sxs-lookup"><span data-stu-id="7c9a0-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>

<span data-ttu-id="7c9a0-107">Benutzer erwarten, dass eine App beim Durchführen einer Berechnung reaktionsfähig bleibt, unabhängig vom jeweiligen Computertyp.</span><span class="sxs-lookup"><span data-stu-id="7c9a0-107">Users expect an app to remain responsive while it does computation, regardless of the type of machine.</span></span> <span data-ttu-id="7c9a0-108">Das bedeutet für jede App etwas anderes.</span><span class="sxs-lookup"><span data-stu-id="7c9a0-108">This means different things for different apps.</span></span> <span data-ttu-id="7c9a0-109">Für einige Apps bedeutet dies z.B. Folgendes: realistischere physische Effekte bereitstellen, Daten vom Datenträger oder aus dem Internet schneller laden, komplexe Szenen schnell darstellen, schnell zwischen Seiten navigieren, Anweisungen im Nu finden oder schnelles Verarbeiten von Daten.</span><span class="sxs-lookup"><span data-stu-id="7c9a0-109">For some, this translates to providing more realistic physics, loading data from disk or the web faster, quickly presenting complex scenes and navigating between pages, finding directions in a snap, or rapidly processing data.</span></span> <span data-ttu-id="7c9a0-110">Unabhängig von der Art der Berechnung möchten Benutzer, dass die App auf ihre Eingabe reagiert. Es stört sie, wenn die App scheinbar nicht reagiert, während sie "denkt".</span><span class="sxs-lookup"><span data-stu-id="7c9a0-110">Regardless of the type of computation, users want their app to act on their input and eliminate instances where it appears unresponsive while it "thinks".</span></span>

<span data-ttu-id="7c9a0-111">Ihre App ist ereignisgesteuert, was bedeutet, dass Ihr Code in Reaktion auf ein Ereignis eine Funktion erfüllt und anschließend befindet sich die App im Leerlauf und wartet auf das nächste Ereignis.</span><span class="sxs-lookup"><span data-stu-id="7c9a0-111">Your app is event-driven, which means that your code performs work in response to an event and then it sits idle until the next.</span></span> <span data-ttu-id="7c9a0-112">Plattformcode für die Benutzeroberfläche (Layout, Eingabe, Auslösen von Ereignissen usw.) und Ihr App-Code für die Benutzeroberfläche werden alle im gleichen UI-Thread ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="7c9a0-112">Platform code for UI (layout, input, raising events, etc.) and your app’s code for UI all are executed on the same UI thread.</span></span> <span data-ttu-id="7c9a0-113">Nur eine Anweisung kann jeweils für diesen Thread ausgeführt werden, wenn Ihr App-Code also zu lange für das Verarbeiten eines Ereignisses benötigt, kann das Framework das Layout nicht ausführen oder neue Ereignisse auslösen, die Interaktionen des Benutzers darstellen.</span><span class="sxs-lookup"><span data-stu-id="7c9a0-113">Only one instruction can execute on that thread at a time so if your app code takes too long to process an event then the framework can’t run layout or raise new events representing user interaction.</span></span> <span data-ttu-id="7c9a0-114">Das heißt, die Reaktionsfähigkeit Ihrer App hängt direkt davon ab, ob der UI-Thread zum Durchführen von Arbeit verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="7c9a0-114">The responsiveness of your app is related to the availability of the UI thread to process work.</span></span>

<span data-ttu-id="7c9a0-115">Sie müssen den UI-Thread verwenden, um fast alle Änderungen am UI-Thread vorzunehmen, einschließlich der Erstellung von UI-Typen und des Zugriffs auf ihre Member.</span><span class="sxs-lookup"><span data-stu-id="7c9a0-115">You need to use the UI thread to make almost all changes to the UI thread, including creating UI types and accessing their members.</span></span> <span data-ttu-id="7c9a0-116">Sie können die UI nicht aus einem Hintergrundthread aktualisieren, können jedoch mit [**CoreDispatcher.RunAsync**](https://msdn.microsoft.com/library/windows/apps/Hh750317) eine Nachricht posten, damit der Code dort ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="7c9a0-116">You can't update the UI from a background thread but you can post a message to it with [**CoreDispatcher.RunAsync**](https://msdn.microsoft.com/library/windows/apps/Hh750317) to cause code to be run there.</span></span>

> <span data-ttu-id="7c9a0-117">**Hinweis**  Die einzige Ausnahme besteht darin, dass es einen separaten Renderthread gibt, der UI-Änderungen ohne Auswirkungen auf die Eingabeverarbeitung oder auf das Basislayout anwenden kann.</span><span class="sxs-lookup"><span data-stu-id="7c9a0-117">**Note**  The one exception is that there's a separate render thread that can apply UI changes that won't affect how input is handled or the basic layout.</span></span> <span data-ttu-id="7c9a0-118">Viele Animationen und Übergänge, die sich nicht auf das Layout auswirken, können z. B. auf diesem Renderthread ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="7c9a0-118">For example many animations and transitions that don’t affect layout can run on this render thread.</span></span>

## <a name="delay-element-instantiation"></a><span data-ttu-id="7c9a0-119">Verzögern der Element-Instanziierung</span><span class="sxs-lookup"><span data-stu-id="7c9a0-119">Delay element instantiation</span></span>

<span data-ttu-id="7c9a0-120">Einige der langsamsten Phasen in einer App können der Start und das Wechseln zwischen Ansichten sein.</span><span class="sxs-lookup"><span data-stu-id="7c9a0-120">Some of the slowest stages in an app can include startup, and switching views.</span></span> <span data-ttu-id="7c9a0-121">Machen Sie sich nicht mehr Arbeit als nötig, um die Benutzeroberfläche anzuzeigen, die dem Benutzer zuerst angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="7c9a0-121">Don't do more work than necessary to bring up the UI that the user sees initially.</span></span> <span data-ttu-id="7c9a0-122">Erstellen Sie beispielsweise nicht die Benutzeroberfläche für die schrittweise offengelegte Benutzeroberfläche und den Inhalt von Popups.</span><span class="sxs-lookup"><span data-stu-id="7c9a0-122">For example, don't create the UI for progressively-disclosed UI and the contents of popups.</span></span>

-   <span data-ttu-id="7c9a0-123">Verwenden Sie [x:Load attribute](../xaml-platform/x-load-attribute.md) oder [x:DeferLoadStrategy](https://msdn.microsoft.com/library/windows/apps/Mt204785), um Elemente verzögert zu instanziieren.</span><span class="sxs-lookup"><span data-stu-id="7c9a0-123">Use [x:Load attribute](../xaml-platform/x-load-attribute.md) or [x:DeferLoadStrategy](https://msdn.microsoft.com/library/windows/apps/Mt204785) to delay-instantiate elements.</span></span>
-   <span data-ttu-id="7c9a0-124">Fügen Sie programmgesteuerte Elemente nach Bedarf in der Struktur ein.</span><span class="sxs-lookup"><span data-stu-id="7c9a0-124">Programmatically insert elements into the tree on-demand.</span></span>

<span data-ttu-id="7c9a0-125">[**CoreDispatcher.RunIdleAsync**](https://msdn.microsoft.com/library/windows/apps/Hh967918)-Warteschlangen eignen sich für die Verarbeitung des UI-Threads, wenn er nicht aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="7c9a0-125">[**CoreDispatcher.RunIdleAsync**](https://msdn.microsoft.com/library/windows/apps/Hh967918) queues work for the UI thread to process when it's not busy.</span></span>

## <a name="use-asynchronous-apis"></a><span data-ttu-id="7c9a0-126">Verwenden von asynchronen APIs</span><span class="sxs-lookup"><span data-stu-id="7c9a0-126">Use asynchronous APIs</span></span>

<span data-ttu-id="7c9a0-127">Zur Verbesserung der Reaktionsfähigkeit der App stellt die Plattform asynchrone Versionen vieler APIs bereit.</span><span class="sxs-lookup"><span data-stu-id="7c9a0-127">To help keep your app responsive, the platform provides asynchronous versions of many of its APIs.</span></span> <span data-ttu-id="7c9a0-128">Eine asynchrone API stellt sicher, dass Ihr aktiver Ausführungsthread nie für längere Zeit blockiert wird.</span><span class="sxs-lookup"><span data-stu-id="7c9a0-128">An asynchronous API ensures that your active execution thread never blocks for a significant amount of time.</span></span> <span data-ttu-id="7c9a0-129">Wenn Sie ein API-Element aus dem UI-Thread heraus aufrufen, verwenden Sie die asynchrone Version, sofern diese verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="7c9a0-129">When you call an API from the UI thread, use the asynchronous version if it's available.</span></span> <span data-ttu-id="7c9a0-130">Weitere Informationen zum Programmieren mit **async**-Strukturen finden Sie unter [Asynchrone Programmierung](https://msdn.microsoft.com/library/windows/apps/Mt187335) oder unter [Aufrufen asynchroner APIs in C# oder Visual Basic](https://msdn.microsoft.com/library/windows/apps/Mt187337).</span><span class="sxs-lookup"><span data-stu-id="7c9a0-130">For more info about programming with **async** patterns, see [Asynchronous programming](https://msdn.microsoft.com/library/windows/apps/Mt187335) or [Call asynchronous APIs in C# or Visual Basic](https://msdn.microsoft.com/library/windows/apps/Mt187337).</span></span>

## <a name="offload-work-to-background-threads"></a><span data-ttu-id="7c9a0-131">Auslagern der Arbeit an Hintergrundthreads</span><span class="sxs-lookup"><span data-stu-id="7c9a0-131">Offload work to background threads</span></span>

<span data-ttu-id="7c9a0-132">Schreiben Sie Ereignishandler, die schnell zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="7c9a0-132">Write event handlers to return quickly.</span></span> <span data-ttu-id="7c9a0-133">In Fällen, in denen umfassende Arbeiten vorgenommen werden müssen, sollten Sie sie in einem Hintergrundthread planen und zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="7c9a0-133">In cases where a non-trivial amount of work needs to be performed, schedule it on a background thread and return.</span></span>

<span data-ttu-id="7c9a0-134">Mit dem Operator **await** in C#, dem Operator **Await** in Visual Basic oder mit Delegaten in C++ können Sie Arbeit auch asynchron planen.</span><span class="sxs-lookup"><span data-stu-id="7c9a0-134">You can schedule work asynchronously by using the **await** operator in C#, the **Await** operator in Visual Basic, or delegates in C++.</span></span> <span data-ttu-id="7c9a0-135">Dies garantiert jedoch nicht, dass die geplante Arbeit in einem Hintergrundthread ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="7c9a0-135">But this doesn't guarantee that the work you schedule will run on a background thread.</span></span> <span data-ttu-id="7c9a0-136">Viele der UWP-APIs planen für Sie die Arbeit im Hintergrundthread, wenn Sie Ihren App-Code jedoch nur mit **await** oder einem Delegaten aufrufen, führen Sie diesen Delegaten oder diese Methode in einem UI-Thread aus.</span><span class="sxs-lookup"><span data-stu-id="7c9a0-136">Many of the Universal Windows Platform (UWP) APIs schedule work in the background thread for you, but if you call your app code by using only **await** or a delegate, you run that delegate or method on the UI thread.</span></span> <span data-ttu-id="7c9a0-137">Wenn Sie Ihren App-Code in einem Hintergrundthread ausführen möchten, müssen Sie dies explizit angeben.</span><span class="sxs-lookup"><span data-stu-id="7c9a0-137">You have to explicitly say when you want to run your app code on a background thread.</span></span> <span data-ttu-id="7c9a0-138">In C# und Visual Basic können Sie dies erreichen, indem Sie Code an [**Task.Run**](https://msdn.microsoft.com/library/windows/apps/xaml/system.threading.tasks.task.run.aspx) übergeben.</span><span class="sxs-lookup"><span data-stu-id="7c9a0-138">In C#C# and Visual Basic you can accomplish this by passing code to [**Task.Run**](https://msdn.microsoft.com/library/windows/apps/xaml/system.threading.tasks.task.run.aspx).</span></span>

<span data-ttu-id="7c9a0-139">Denken Sie daran, dass nur aus dem UI-Thread auf UI-Elemente zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="7c9a0-139">Remember that UI elements may only be accessed from the UI thread.</span></span> <span data-ttu-id="7c9a0-140">Verwenden Sie den UI-Thread für den Zugriff auf UI-Elemente vor dem Starten der Hintergrundverarbeitung und/oder der Verwendung von [**CoreDispatcher.RunAsync**](https://msdn.microsoft.com/library/windows/apps/Hh750317) oder [**CoreDispatcher.RunIdleAsync**](https://msdn.microsoft.com/library/windows/apps/Hh967918) im Hintergrundthread.</span><span class="sxs-lookup"><span data-stu-id="7c9a0-140">Use the UI thread to access UI elements before launching the background work and/or use [**CoreDispatcher.RunAsync**](https://msdn.microsoft.com/library/windows/apps/Hh750317) or [**CoreDispatcher.RunIdleAsync**](https://msdn.microsoft.com/library/windows/apps/Hh967918) on the background thread.</span></span>

<span data-ttu-id="7c9a0-141">Ein Beispiel für Arbeit, die in einem Hintergrundthread ausgeführt werden kann, ist die Berechnung der Computer-KI in einem Spiel.</span><span class="sxs-lookup"><span data-stu-id="7c9a0-141">An example of work that can be performed on a background thread is the calculating of computer AI in a game.</span></span> <span data-ttu-id="7c9a0-142">Die Ausführung des Codes zur Berechnung der nächsten Aktion des Computers nimmt viel Zeit in Anspruch.</span><span class="sxs-lookup"><span data-stu-id="7c9a0-142">The code that calculates the computer's next move can take a lot of time to execute.</span></span>

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

<span data-ttu-id="7c9a0-143">In diesem Beispiel wird der `NextMove-Click`-Handler bei **await** zurückgegeben, damit der UI-Thread reaktionsfähig bleibt.</span><span class="sxs-lookup"><span data-stu-id="7c9a0-143">In this example, the `NextMove-Click` handler returns at the **await** in order to keep the UI thread responsive.</span></span> <span data-ttu-id="7c9a0-144">Die Ausführung wird jedoch in diesem Handler fortgesetzt, nachdem `ComputeNextMove` abgeschlossen ist (in einem Hintergrundthread ausgeführt).</span><span class="sxs-lookup"><span data-stu-id="7c9a0-144">But execution picks up in that handler again after `ComputeNextMove` (which executes on a background thread) completes.</span></span> <span data-ttu-id="7c9a0-145">Der restliche Code im Handler aktualisiert die UI mit den Ergebnissen.</span><span class="sxs-lookup"><span data-stu-id="7c9a0-145">The remaining code in the handler updates the UI with the results.</span></span>

> <span data-ttu-id="7c9a0-146">**Hinweis**  Es gibt darüber hinaus eine [**ThreadPool**](https://msdn.microsoft.com/library/windows/apps/BR229621)- und eine [**ThreadPoolTimer**](https://msdn.microsoft.com/library/windows/apps/windows.system.threading.threadpooltimer.aspx)-API für die UWP, die für ähnliche Szenarien verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="7c9a0-146">**Note**  There's also a [**ThreadPool**](https://msdn.microsoft.com/library/windows/apps/BR229621) and [**ThreadPoolTimer**](https://msdn.microsoft.com/library/windows/apps/windows.system.threading.threadpooltimer.aspx) API for the UWP, which can be used for similar scenarios.</span></span> <span data-ttu-id="7c9a0-147">Weitere Informationen finden Sie unter [Threading und asynchrone Programmierung](https://msdn.microsoft.com/library/windows/apps/Mt187340).</span><span class="sxs-lookup"><span data-stu-id="7c9a0-147">For more info, see [Threading and async programming](https://msdn.microsoft.com/library/windows/apps/Mt187340).</span></span>

## <a name="related-topics"></a><span data-ttu-id="7c9a0-148">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="7c9a0-148">Related topics</span></span>

* [<span data-ttu-id="7c9a0-149">Benutzerdefinierte Benutzerinteraktionen</span><span class="sxs-lookup"><span data-stu-id="7c9a0-149">Custom user interactions</span></span>](https://msdn.microsoft.com/library/windows/apps/Mt185599)