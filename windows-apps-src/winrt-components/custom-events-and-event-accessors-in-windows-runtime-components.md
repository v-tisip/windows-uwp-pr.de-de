---
author: msatranjr
title: Benutzerdefinierte Ereignisse und Ereignisaccessoren in Komponenten für Windows-Runtime
description: Die .NET Framework-Unterstützung für Komponenten für Windows-Runtime erleichtert die Deklaration von Ereigniskomponenten, indem die Unterschiede zwischen dem Ereignismuster der universellen Windows-Plattform (UWP) und dem Ereignismuster von .NET Framework verborgen werden.
ms.assetid: 6A66D80A-5481-47F8-9499-42AC8FDA0EB4
ms.author: misatran
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 99e215f382bbfe409ac72d021540a471294634ca
ms.sourcegitcommit: 4d88adfaf544a3dab05f4660e2f59bbe60311c00
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "6457779"
---
# <a name="custom-events-and-event-accessors-in-windows-runtime-components"></a><span data-ttu-id="b4626-104">Benutzerdefinierte Ereignisse und Ereignisaccessoren in Komponenten für Windows-Runtime</span><span class="sxs-lookup"><span data-stu-id="b4626-104">Custom events and event accessors in Windows Runtime Components</span></span>



<span data-ttu-id="b4626-105">Die .NET Framework-Unterstützung für Komponenten für Windows-Runtime erleichtert die Deklaration von Ereigniskomponenten, indem die Unterschiede zwischen dem Ereignismuster der universellen Windows-Plattform (UWP) und dem Ereignismuster von .NET Framework verborgen werden.</span><span class="sxs-lookup"><span data-stu-id="b4626-105">.NET Framework support for Windows Runtime Components makes it easy to declare events components by hiding the differences between the Universal Windows Platform (UWP) event pattern and the .NET Framework event pattern.</span></span> <span data-ttu-id="b4626-106">Wenn Sie jedoch benutzerdefinierte Ereignisaccessoren in einer Komponente für Windows-Runtime deklarieren, müssen Sie dem Muster folgen das in der UWP verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="b4626-106">However, when you declare custom event accessors in a Windows Runtime Component, you must follow the pattern used in the UWP.</span></span>

## <a name="registering-events"></a><span data-ttu-id="b4626-107">Registrieren von Ereignissen</span><span class="sxs-lookup"><span data-stu-id="b4626-107">Registering events</span></span>


<span data-ttu-id="b4626-108">Wenn Sie die Registrierung für die Behandlung eines Ereignisses in der UWP durchführen, gibt der Add-Accessor ein Token zurück.</span><span class="sxs-lookup"><span data-stu-id="b4626-108">When you register to handle an event in the UWP, the add accessor returns a token.</span></span> <span data-ttu-id="b4626-109">Um die Registrierung aufzuheben, übergeben Sie dieses Token an den Remove-Accessor.</span><span class="sxs-lookup"><span data-stu-id="b4626-109">To unregister, you pass this token to the remove accessor.</span></span> <span data-ttu-id="b4626-110">Dies bedeutet, dass sich die Signaturen der Add- und Remove-Accessoren für UWP-Ereignisse von den üblichen Accessoren unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="b4626-110">This means that the add and remove accessors for UWP events have different signatures from the accessors you're used to.</span></span>

<span data-ttu-id="b4626-111">Glücklicherweise vereinfachen die Visual Basic- und C#-Compiler diesen Prozess: Wenn Sie ein Ereignis mit benutzerdefinierten Accessoren in einer Komponente für Windows-Runtime deklarieren, verwenden die Compiler automatisch das UWP-Muster.</span><span class="sxs-lookup"><span data-stu-id="b4626-111">Fortunately, the Visual Basic and C# compilers simplify this process: When you declare an event with custom accessors in a Windows Runtime Component, the compilers automatically use the UWP pattern.</span></span> <span data-ttu-id="b4626-112">Beispielsweise erhalten Sie einen Compilerfehler, wenn Ihr Add-Accessor kein Token zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="b4626-112">For example, you get a compiler error if your add accessor doesn't return a token.</span></span> <span data-ttu-id="b4626-113">Das .NET Framework stellt zwei Typen zur Unterstützung der Implementierung bereit:</span><span class="sxs-lookup"><span data-stu-id="b4626-113">The .NET Framework provides two types to support the implementation:</span></span>

-   <span data-ttu-id="b4626-114">Die [EventRegistrationToken](https://msdn.microsoft.com/library/windows/apps/windows.foundation.eventregistrationtoken.aspx)-Struktur stellt das Token dar.</span><span class="sxs-lookup"><span data-stu-id="b4626-114">The [EventRegistrationToken](https://msdn.microsoft.com/library/windows/apps/windows.foundation.eventregistrationtoken.aspx) structure represents the token.</span></span>
-   <span data-ttu-id="b4626-115">Die [EventRegistrationTokenTable&lt;T&gt;](https://msdn.microsoft.com/library/hh138412.aspx)-Klasse erstellt Token und verwaltet eine Zuordnung zwischen Token und Ereignishandlern.</span><span class="sxs-lookup"><span data-stu-id="b4626-115">The [EventRegistrationTokenTable&lt;T&gt;](https://msdn.microsoft.com/library/hh138412.aspx) class creates tokens and maintains a mapping between tokens and event handlers.</span></span> <span data-ttu-id="b4626-116">Das generische Typargument ist der Ereignisargumenttyp.</span><span class="sxs-lookup"><span data-stu-id="b4626-116">The generic type argument is the event argument type.</span></span> <span data-ttu-id="b4626-117">Sie erstellen eine Instanz dieser Klasse für jedes Ereignis, wenn ein Ereignishandler zum ersten Mal für dieses Ereignis registriert wird.</span><span class="sxs-lookup"><span data-stu-id="b4626-117">You create an instance of this class for each event, the first time an event handler is registered for that event.</span></span>

<span data-ttu-id="b4626-118">Der folgende Code für das Ereignis „NumberChanged” zeigt das grundlegende Muster für UWP-Ereignisse.</span><span class="sxs-lookup"><span data-stu-id="b4626-118">The following code for the NumberChanged event shows the basic pattern for UWP events.</span></span> <span data-ttu-id="b4626-119">In diesem Beispiel übernimmt der Konstruktor für das Ereignisargumentobjekt „NumberChangedEventArgs” einen einzelnen ganzzahligen Parameter, der den geänderten numerischen Wert darstellt.</span><span class="sxs-lookup"><span data-stu-id="b4626-119">In this example, the constructor for the event argument object, NumberChangedEventArgs, takes a single integer parameter that represents the changed numeric value.</span></span>

> <span data-ttu-id="b4626-120">**Hinweis:** Hierbei handelt es sich um das gleiche Muster die Compiler für gewöhnliche Ereignisse verwenden, die Sie in einer Windows-Runtime-Komponente deklarieren.</span><span class="sxs-lookup"><span data-stu-id="b4626-120">**Note**This is the same pattern the compilers use for ordinary events that you declare in a Windows Runtime Component.</span></span>

 
> [!div class="tabbedCodeSnippets"]
> ```csharp
> private EventRegistrationTokenTable<EventHandler<NumberChangedEventArgs>>
>     m_NumberChangedTokenTable = null;
>
> public event EventHandler<NumberChangedEventArgs> NumberChanged
> {
>     add
>     {
>         return EventRegistrationTokenTable<EventHandler<NumberChangedEventArgs>>
>             .GetOrCreateEventRegistrationTokenTable(ref m_NumberChangedTokenTable)
>             .AddEventHandler(value);
>     }
>     remove
>     {
>         EventRegistrationTokenTable<EventHandler<NumberChangedEventArgs>>
>             .GetOrCreateEventRegistrationTokenTable(ref m_NumberChangedTokenTable)
>             .RemoveEventHandler(value);
>     }
> }
>
> internal void OnNumberChanged(int newValue)
> {
>     EventHandler<NumberChangedEventArgs> temp =
>         EventRegistrationTokenTable<EventHandler<NumberChangedEventArgs>>
>         .GetOrCreateEventRegistrationTokenTable(ref m_NumberChangedTokenTable)
>         .InvocationList;
>     if (temp != null)
>     {
>         temp(this, new NumberChangedEventArgs(newValue));
>     }
> }
> ```
> ```vb
> Private m_NumberChangedTokenTable As  _
>     EventRegistrationTokenTable(Of EventHandler(Of NumberChangedEventArgs))
>
> Public Custom Event NumberChanged As EventHandler(Of NumberChangedEventArgs)
>
>     AddHandler(ByVal handler As EventHandler(Of NumberChangedEventArgs))
>         Return EventRegistrationTokenTable(Of EventHandler(Of NumberChangedEventArgs)).
>             GetOrCreateEventRegistrationTokenTable(m_NumberChangedTokenTable).
>             AddEventHandler(handler)
>     End AddHandler
>
>     RemoveHandler(ByVal token As EventRegistrationToken)
>         EventRegistrationTokenTable(Of EventHandler(Of NumberChangedEventArgs)).
>             GetOrCreateEventRegistrationTokenTable(m_NumberChangedTokenTable).
>             RemoveEventHandler(token)
>     End RemoveHandler
>
>     RaiseEvent(ByVal sender As Class1, ByVal args As NumberChangedEventArgs)
>         Dim temp As EventHandler(Of NumberChangedEventArgs) = _
>             EventRegistrationTokenTable(Of EventHandler(Of NumberChangedEventArgs)).
>             GetOrCreateEventRegistrationTokenTable(m_NumberChangedTokenTable).
>             InvocationList
>         If temp IsNot Nothing Then
>             temp(sender, args)
>         End If
>     End RaiseEvent
> End Event
> ```

<span data-ttu-id="b4626-121">Die statische („Shared” in Visual Basic) Methode „GetOrCreateEventRegistrationTokenTable” erstellt die Instanz des Ereignisses des EventRegistrationTokenTable&lt;T&gt;-Objekts verzögert.</span><span class="sxs-lookup"><span data-stu-id="b4626-121">The static (Shared in Visual Basic) GetOrCreateEventRegistrationTokenTable method creates the event’s instance of the EventRegistrationTokenTable&lt;T&gt; object lazily.</span></span> <span data-ttu-id="b4626-122">Übergeben Sie das Feld auf Klassenebene, das die Tokentabelleninstanz enthalten soll, an diese Methode.</span><span class="sxs-lookup"><span data-stu-id="b4626-122">Pass the class-level field that will hold the token table instance to this method.</span></span> <span data-ttu-id="b4626-123">Wenn das Feld leer ist, erstellt die Methode die Tabelle, speichert einen Verweis auf die Tabelle in dem Feld und gibt einen Verweis auf die Tabelle zurück.</span><span class="sxs-lookup"><span data-stu-id="b4626-123">If the field is empty, the method creates the table, stores a reference to the table in the field, and returns a reference to the table.</span></span> <span data-ttu-id="b4626-124">Wenn das Feld bereits einen Verweis auf die Tokentabelle enthält, gibt die Methode einfach diesen Verweis zurück.</span><span class="sxs-lookup"><span data-stu-id="b4626-124">If the field already contains a token table reference, the method just returns that reference.</span></span>

> <span data-ttu-id="b4626-125">**Wichtige**um sicherzustellen, dass Threadsicherheit, das Feld, das das Ereignis Instanz des EventRegistrationTokenTable enthält&lt;T&gt; muss ein Feld auf Klassenebene sein.</span><span class="sxs-lookup"><span data-stu-id="b4626-125">**Important**To ensure thread safety, the field that holds the event’s instance of EventRegistrationTokenTable&lt;T&gt; must be a class-level field.</span></span> <span data-ttu-id="b4626-126">Wenn dies ein Feld auf Klassenebene ist, stellt die Methode „GetOrCreateEventRegistrationTokenTable” sicher, dass alle Threads dieselbe Instanz der Tabelle abrufen, wenn mehrere Threads versuchen, die Tokentabelle zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="b4626-126">If it is a class-level field, the GetOrCreateEventRegistrationTokenTable method ensures that when multiple threads try to create the token table, all threads get the same instance of the table.</span></span> <span data-ttu-id="b4626-127">Für ein bestimmtes Ereignis müssen alle Aufrufe der Methode „GetOrCreateEventRegistrationTokenTable” dasselbe Feld auf Klassenebene verwenden.</span><span class="sxs-lookup"><span data-stu-id="b4626-127">For a given event, all calls to the GetOrCreateEventRegistrationTokenTable method must use the same class-level field.</span></span>

<span data-ttu-id="b4626-128">Durch Aufrufen der Methode „GetOrCreateEventRegistrationTokenTable” im Remove-Accessor und in der Methode [RaiseEvent](https://msdn.microsoft.com/library/fwd3bwed.aspx) („OnRaiseEvent”-Methode in C#) wird sichergestellt, dass keine Ausnahmen ausgelöst werden, wenn diese Methoden aufgerufen werden, bevor Ereignishandlerdelegaten hinzugefügt wurden.</span><span class="sxs-lookup"><span data-stu-id="b4626-128">Calling the GetOrCreateEventRegistrationTokenTable method in the remove accessor and in the [RaiseEvent](https://msdn.microsoft.com/library/fwd3bwed.aspx) method (the OnRaiseEvent method in C#) ensures that no exceptions occur if these methods are called before any event handler delegates have been added.</span></span>

<span data-ttu-id="b4626-129">Zu den anderen Membern der EventRegistrationTokenTable&lt;T&gt;-Klasse, die im UWP-Ereignismuster verwendet werden, zählen:</span><span class="sxs-lookup"><span data-stu-id="b4626-129">The other members of the EventRegistrationTokenTable&lt;T&gt; class that are used in the UWP event pattern include the following:</span></span>

-   <span data-ttu-id="b4626-130">Die [AddEventHandler](https://msdn.microsoft.com/library/hh138458.aspx)-Methode generiert ein Token für den Ereignishandlerdelegaten, speichert den Delegaten in der Tabelle, fügt ihn der Aufrufliste hinzu und gibt das Token zurück.</span><span class="sxs-lookup"><span data-stu-id="b4626-130">The [AddEventHandler](https://msdn.microsoft.com/library/hh138458.aspx) method generates a token for the event handler delegate, stores the delegate in the table, adds it to the invocation list, and returns the token.</span></span>
-   <span data-ttu-id="b4626-131">Die [RemoveEventHandler(EventRegistrationToken)](https://msdn.microsoft.com/library/hh138425.aspx)-Methodenüberladung entfernt den Delegaten aus der Tabelle und der Aufrufliste.</span><span class="sxs-lookup"><span data-stu-id="b4626-131">The [RemoveEventHandler(EventRegistrationToken)](https://msdn.microsoft.com/library/hh138425.aspx) method overload removes the delegate from the table and from the invocation list.</span></span>

    ><span data-ttu-id="b4626-132">**Hinweis:** Methoden die Methoden "AddEventHandler" und RemoveEventHandler(EventRegistrationToken) sperren die Tabelle, um Threadsicherheit zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="b4626-132">**Note**The AddEventHandler and RemoveEventHandler(EventRegistrationToken) methods lock the table to help ensure thread safety.</span></span>

-   <span data-ttu-id="b4626-133">Die [InvocationList](https://msdn.microsoft.com/library/hh138465.aspx)-Eigenschaft gibt einen Delegaten zurück, der alle Ereignishandler enthält, die derzeit zum Behandeln des Ereignisses registriert sind.</span><span class="sxs-lookup"><span data-stu-id="b4626-133">The [InvocationList](https://msdn.microsoft.com/library/hh138465.aspx) property returns a delegate that includes all the event handlers that are currently registered to handle the event.</span></span> <span data-ttu-id="b4626-134">Verwenden Sie diesen Delegaten zum Auslösen des Ereignisses, oder verwenden Sie die Methoden der Delegate-Klasse, um die Handler einzeln aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="b4626-134">Use this delegate to raise the event, or use the methods of the Delegate class to invoke the handlers individually.</span></span>

    ><span data-ttu-id="b4626-135">**Hinweis:** es wird empfohlen, dass Sie dem Muster angezeigt, in dem Beispiel oben in diesem Artikel folgen und den Delegaten in eine temporäre Variable kopieren, bevor Sie ihn aufrufen.</span><span class="sxs-lookup"><span data-stu-id="b4626-135">**Note**We recommend that you follow the pattern shown in the example provided earlier in this article, and copy the delegate to a temporary variable before invoking it.</span></span> <span data-ttu-id="b4626-136">Dadurch wird eine Racebedingung verhindert, in der ein Thread den letzten Ereignishandler entfernt, indem der Delegat auf null festlegt wird, kurz bevor ein anderer Thread versucht, den Delegaten aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="b4626-136">This avoids a race condition in which one thread removes the last handler, reducing the delegate to null just before another thread tries to invoke the delegate.</span></span> <span data-ttu-id="b4626-137">Delegaten sind unveränderlich, sodass die Kopie weiterhin gültig ist.</span><span class="sxs-lookup"><span data-stu-id="b4626-137">Delegates are immutable, so the copy is still valid.</span></span>

<span data-ttu-id="b4626-138">Nehmen Sie eigenen Code nach Bedarf in die Accessoren auf.</span><span class="sxs-lookup"><span data-stu-id="b4626-138">Place your own code in the accessors as appropriate.</span></span> <span data-ttu-id="b4626-139">Wenn Threadsicherheit wichtig ist, müssen Sie eigene Sperren für Ihren Code vorsehen.</span><span class="sxs-lookup"><span data-stu-id="b4626-139">If thread safety is an issue, you must provide your own locking for your code.</span></span>

<span data-ttu-id="b4626-140">C#-Benutzer: Wenn Sie benutzerdefinierte Ereignisaccessoren im UWP-Ereignismuster schreiben, stellt der Compiler nicht die üblichen syntaktischen Verknüpfungen bereit.</span><span class="sxs-lookup"><span data-stu-id="b4626-140">C# users: When you write custom event accessors in the UWP event pattern, the compiler doesn't provide the usual syntactic shortcuts.</span></span> <span data-ttu-id="b4626-141">Es werden Fehler generiert, wenn Sie den Namen des Ereignisses im Code verwenden.</span><span class="sxs-lookup"><span data-stu-id="b4626-141">It generates errors if you use the name of the event in your code.</span></span>

<span data-ttu-id="b4626-142">Visual Basic-Benutzer: Im .NET Framework ist ein Ereignis einfach ein Multicastdelegat, der alle registrierten Ereignishandler darstellt.</span><span class="sxs-lookup"><span data-stu-id="b4626-142">Visual Basic users: In the .NET Framework, an event is just a multicast delegate that represents all the registered event handlers.</span></span> <span data-ttu-id="b4626-143">Das Auslösen des Ereignisses bedeutet nur, dass der Delegat aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="b4626-143">Raising the event just means invoking the delegate.</span></span> <span data-ttu-id="b4626-144">Visual Basic-Syntax blendet im Allgemeinen die Interaktionen mit dem Delegaten aus, und der Compiler kopiert den Delegaten, bevor er aufgerufen wird, wie im Hinweis zu Threadsicherheit beschrieben.</span><span class="sxs-lookup"><span data-stu-id="b4626-144">Visual Basic syntax generally hides the interactions with the delegate, and the compiler copies the delegate before invoking it, as described in the note about thread safety.</span></span> <span data-ttu-id="b4626-145">Wenn Sie ein benutzerdefiniertes Ereignis in einer Komponente für Windows-Runtime erstellen, müssen Sie sich direkt mit dem Delegaten befassen.</span><span class="sxs-lookup"><span data-stu-id="b4626-145">When you create a custom event in a Windows Runtime Component, you have to deal with the delegate directly.</span></span> <span data-ttu-id="b4626-146">Dies bedeutet auch, dass Sie beispielsweise mit der [MulticastDelegate.GetInvocationList](https://msdn.microsoft.com/library/system.multicastdelegate.getinvocationlist.aspx)-Methode ein Array mit einem separaten Delegaten für jeden Ereignishandler abrufen können, wenn Sie die Handler einzeln aufrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="b4626-146">This also means that you can, for example, use the [MulticastDelegate.GetInvocationList](https://msdn.microsoft.com/library/system.multicastdelegate.getinvocationlist.aspx) method to get an array that contains a separate delegate for each event handler, if you want to invoke the handlers separately.</span></span>

## <a name="related-topics"></a><span data-ttu-id="b4626-147">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="b4626-147">Related topics</span></span>

* [<span data-ttu-id="b4626-148">Ereignisse (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4626-148">Events (Visual Basic)</span></span>](https://msdn.microsoft.com/library/ms172877.aspx)
* [<span data-ttu-id="b4626-149">Ereignisse (C#-Programmierhandbuch)</span><span class="sxs-lookup"><span data-stu-id="b4626-149">Events (C# Programming Guide)</span></span>](https://msdn.microsoft.com/library/awbftdfh.aspx)
* [<span data-ttu-id="b4626-150">.NET für UWP-apps-Übersicht</span><span class="sxs-lookup"><span data-stu-id="b4626-150">.NET for UWP apps Overview</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/br230302.aspx)
* [<span data-ttu-id="b4626-151">.NET für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="b4626-151">.NET for UWP apps</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/mt185501.aspx)
* [<span data-ttu-id="b4626-152">Exemplarische Vorgehensweise: Erstellen einer einfachen Komponente für Windows-Runtime und Aufrufen der Komponente über JavaScript</span><span class="sxs-lookup"><span data-stu-id="b4626-152">Walkthrough: Creating a Simple Windows Runtime Component and calling it from JavaScript</span></span>](walkthrough-creating-a-simple-windows-runtime-component-and-calling-it-from-javascript.md)
