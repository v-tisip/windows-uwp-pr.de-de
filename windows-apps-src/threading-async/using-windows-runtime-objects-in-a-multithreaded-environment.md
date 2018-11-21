---
title: Verwenden von Windows-Runtime-Objekten in einer Multithread-Umgebung | Microsoft Docs
description: In diesem Artikel wird beschrieben, wie das .NET Framework Aufrufe von C#- und Visual Basic-Code auf Objekte verarbeitet, die von der Windows-Runtime oder von Komponenten für Windows-Runtime bereitgestellt werden.
ms.date: 01/14/2017
ms.topic: article
ms.assetid: 43ffd28c-c4df-405c-bf5c-29c94e0d142b
author: normesta
ms.author: normesta
keywords: Windows10, UWP, Timer, Threads
ms.localizationpriority: medium
ms.openlocfilehash: 9f4b8249a81cb7d71ba1f4775fd858ae87779c85
ms.sourcegitcommit: 93c0a60cf531c7d9fe7b00e7cf78df86906f9d6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2018
ms.locfileid: "7553757"
---
# <a name="using-windows-runtime-objects-in-a-multithreaded-environment"></a><span data-ttu-id="8cdca-104">Verwenden von Windows-Runtime-Objekten in einer Multithread-Umgebung</span><span class="sxs-lookup"><span data-stu-id="8cdca-104">Using Windows Runtime objects in a multithreaded environment</span></span>
<span data-ttu-id="8cdca-105">In diesem Artikel wird beschrieben, wie das .NET Framework Aufrufe von C#- und Visual Basic-Code auf Objekte verarbeitet, die von der Windows-Runtime oder von Komponenten für Windows-Runtime bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="8cdca-105">This article discusses the way the .NET Framework handles calls from C# and Visual Basic code to objects that are provided by the Windows Runtime or by Windows Runtime Components.</span></span>

<span data-ttu-id="8cdca-106">Im .NET Framework können Sie standardmäßig ohne besondere Verarbeitung über mehrere Threads auf alle Objekte zugreifen.</span><span class="sxs-lookup"><span data-stu-id="8cdca-106">In the .NET Framework, you can access any object from multiple threads by default, without special handling.</span></span> <span data-ttu-id="8cdca-107">Sie benötigen lediglich einen Verweis auf das Objekt.</span><span class="sxs-lookup"><span data-stu-id="8cdca-107">All you need is a reference to the object.</span></span> <span data-ttu-id="8cdca-108">Solche Objekte werden in der Windows-Runtime als *agil* bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="8cdca-108">In the Windows Runtime, such objects are called *agile*.</span></span> <span data-ttu-id="8cdca-109">Die meisten Windows-Runtime-Klassen sind agil, einige jedoch nicht, und selbst agile Klassen erfordern möglicherweise eine besondere Verarbeitung.</span><span class="sxs-lookup"><span data-stu-id="8cdca-109">Most Windows Runtime classes are agile, but a few classes are not, and even agile classes may require special handling.</span></span>

<span data-ttu-id="8cdca-110">Wann immer möglich, behandelt die Common Language Runtime (CLR) Objekte aus anderen Quellen, wie beispielsweise der Windows-Runtime, so, als wären sie .NET Framework-Objekte:</span><span class="sxs-lookup"><span data-stu-id="8cdca-110">Wherever possible, the common language runtime (CLR) treats objects from other sources, such as the Windows Runtime, as if they were .NET Framework objects:</span></span>

- <span data-ttu-id="8cdca-111">Wenn das Objekt die Schnittstelle [IAgileObject](http://msdn.microsoft.com/library/Hh802476.aspx) implementiert oder das Attribut [MarshalingBehaviorAttribute](http://go.microsoft.com/fwlink/p/?LinkId=256022) mit [MarshalingType.Agile](http://go.microsoft.com/fwlink/p/?LinkId=256023) aufweist, wird es von der CLR so behandelt, als wäre es agil.</span><span class="sxs-lookup"><span data-stu-id="8cdca-111">If the object implements the [IAgileObject](http://msdn.microsoft.com/library/Hh802476.aspx) interface, or has the [MarshalingBehaviorAttribute](http://go.microsoft.com/fwlink/p/?LinkId=256022) attribute with [MarshalingType.Agile](http://go.microsoft.com/fwlink/p/?LinkId=256023), the CLR treats it as agile.</span></span>

- <span data-ttu-id="8cdca-112">Wenn CLR einen Aufruf über den Thread marshallen kann, in dem er zum Threadingkontext des Zielobjekts gemacht wurde, geschieht dies transparent.</span><span class="sxs-lookup"><span data-stu-id="8cdca-112">If CLR can marshal a call from the thread where it was made to the threading context of the target object, it does so transparently.</span></span>

- <span data-ttu-id="8cdca-113">Wenn das Objekt über das Attribut [MarshalingBehaviorAttribute](http://go.microsoft.com/fwlink/p/?LinkId=256022) mit [MarshalingType.None](http://go.microsoft.com/fwlink/p/?LinkId=256023) verfügt, stellt die Klasse keine Marshalling-Informationen bereit.</span><span class="sxs-lookup"><span data-stu-id="8cdca-113">If the object has the [MarshalingBehaviorAttribute](http://go.microsoft.com/fwlink/p/?LinkId=256022) attribute with [MarshalingType.None](http://go.microsoft.com/fwlink/p/?LinkId=256023), the class does not provide marshaling information.</span></span> <span data-ttu-id="8cdca-114">Die CLR kann den Aufruf nicht marshallen, daher wird eine [InvalidCastException](/dotnet/api/system.invalidcastexception)-Ausnahme mit der Meldung ausgelöst, dass das Objekt nur in dem Threadingkontext verwendet werden kann, in dem es erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="8cdca-114">The CLR cannot marshal the call, so it throws an [InvalidCastException](/dotnet/api/system.invalidcastexception) exception with a message indicating that the object can be used only in the threading context where it was created.</span></span>

<span data-ttu-id="8cdca-115">In den folgenden Abschnitten werden die Auswirkungen dieses Verhaltens auf Objekte aus verschiedenen Quellen beschrieben.</span><span class="sxs-lookup"><span data-stu-id="8cdca-115">The following sections describe the effects of this behavior on objects from various sources.</span></span>

## <a name="objects-from-a-windows-runtime-component-that-is-written-in-c-or-visual-basic"></a><span data-ttu-id="8cdca-116">Objekte aus einer in C# oder Visual Basic geschriebenen Windows-Runtime-Komponente</span><span class="sxs-lookup"><span data-stu-id="8cdca-116">Objects from a Windows Runtime component that is written in C# or Visual Basic</span></span>
<span data-ttu-id="8cdca-117">Alle Typen in der Komponente, die aktiviert werden können, sind standardmäßig agil.</span><span class="sxs-lookup"><span data-stu-id="8cdca-117">All the types in the component that can be activated are agile by default.</span></span>

> [!NOTE]
>  <span data-ttu-id="8cdca-118">Agilität bedeutet nicht, dass Threadsicherheit gegeben ist.</span><span class="sxs-lookup"><span data-stu-id="8cdca-118">Agility doesn't imply thread safety.</span></span> <span data-ttu-id="8cdca-119">Sowohl in der Windows-Runtime als auch im .NET Framework sind die meisten Klassen nicht threadsicher, da Threadsicherheit mit Leistungseinbußen verbunden ist und die meisten Objekte nie von mehreren Threads aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="8cdca-119">In both the Windows Runtime and the .NET Framework, most classes are not thread safe because thread safety has a performance cost, and most objects are never accessed by multiple threads.</span></span> <span data-ttu-id="8cdca-120">Es ist effizienter, nur bei Bedarf den Zugriff auf einzelne Objekte zu synchronisieren (oder threadsichere Klassen zu verwenden).</span><span class="sxs-lookup"><span data-stu-id="8cdca-120">It's more efficient to synchronize access to individual objects (or to use thread-safe classes) only as necessary.</span></span>

<span data-ttu-id="8cdca-121">Wenn Sie eine Windows-Runtime-Komponente erstellen, können Sie die Standardeinstellung überschreiben.</span><span class="sxs-lookup"><span data-stu-id="8cdca-121">When you author a Windows Runtime component, you can override the default.</span></span> <span data-ttu-id="8cdca-122">Informationen hierzu finden Sie in den Abschnitten [ICustomQueryInterface](/dotnet/api/system.runtime.interopservices.icustomqueryinterface)-Schnittstelle und [IAgileObject](http://msdn.microsoft.com/library/Hh802476.aspx)-Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="8cdca-122">See the [ICustomQueryInterface](/dotnet/api/system.runtime.interopservices.icustomqueryinterface) interface and the [IAgileObject](http://msdn.microsoft.com/library/Hh802476.aspx) interface.</span></span>

## <a name="objects-from-the-windows-runtime"></a><span data-ttu-id="8cdca-123">Objekte aus der Windows-Runtime</span><span class="sxs-lookup"><span data-stu-id="8cdca-123">Objects from the Windows Runtime</span></span>
<span data-ttu-id="8cdca-124">Die meisten Klassen in der Windows-Runtime sind agil, und die CLR behandelt diese als agil.</span><span class="sxs-lookup"><span data-stu-id="8cdca-124">Most classes in the Windows Runtime are agile, and the CLR treats them as agile.</span></span> <span data-ttu-id="8cdca-125">In der Dokumentation für diese Klassen wird „MarshalingBehaviorAttribute(Agile)” unter den Klassenattributen genannt.</span><span class="sxs-lookup"><span data-stu-id="8cdca-125">The documentation for these classes lists "MarshalingBehaviorAttribute(Agile)" among the class attributes.</span></span> <span data-ttu-id="8cdca-126">Die Elemente in einigen dieser agilen Klassen, wie beispielsweise XAML-Steuerelemente, lösen jedoch Ausnahmen aus, wenn sie nicht für den UI-Thread aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="8cdca-126">However, the members of some of these agile classes, such as XAML controls, throw exceptions if they aren't called on the UI thread.</span></span> <span data-ttu-id="8cdca-127">Der folgende Code versucht beispielsweise, einen Hintergrundthread zu verwenden, um eine Eigenschaft der Schaltfläche festzulegen, auf die geklickt wurde.</span><span class="sxs-lookup"><span data-stu-id="8cdca-127">For example, the following code tries to use a background thread to set a property of the button that was clicked.</span></span> <span data-ttu-id="8cdca-128">Die [Content](http://go.microsoft.com/fwlink/p/?LinkId=256025)-Eigenschaft der Schaltfläche löst eine Ausnahme aus.</span><span class="sxs-lookup"><span data-stu-id="8cdca-128">The button's [Content](http://go.microsoft.com/fwlink/p/?LinkId=256025) property throws an exception.</span></span>

```csharp
private async void Button_Click_2(object sender, RoutedEventArgs e)
{
    Button b = (Button) sender;
    await Task.Run(() => {
        b.Content += ".";
    });
}
```

```vb
Private Async Sub Button_Click_2(sender As Object, e As RoutedEventArgs)
    Dim b As Button = CType(sender, Button)
    Await Task.Run(Sub()
                       b.Content &= "."
                   End Sub)
End Sub
```

<span data-ttu-id="8cdca-129">Ein sicherer Zugriff auf die Schaltfläche ist bei Verwendung ihrer [Dispatcher](http://go.microsoft.com/fwlink/p/?LinkId=256026)-Eigenschaft oder der `Dispatcher`-Eigenschaft eines beliebigen Objekts im Kontext des UI-Threads (beispielsweise die Seite, auf der sich die Schaltfläche befindet) möglich.</span><span class="sxs-lookup"><span data-stu-id="8cdca-129">You can access the button safely by using its [Dispatcher](http://go.microsoft.com/fwlink/p/?LinkId=256026) property, or the `Dispatcher` property of any object that exists in the context of the UI thread (such as the page the button is on).</span></span> <span data-ttu-id="8cdca-130">Der folgende Code verwendet die Methode [RunAsync](http://go.microsoft.com/fwlink/p/?LinkId=256030) des [CoreDispatcher](http://go.microsoft.com/fwlink/p/?LinkId=256029)-Objekts, um den Aufruf für den UI-Thread zu verteilen.</span><span class="sxs-lookup"><span data-stu-id="8cdca-130">The following code uses the [CoreDispatcher](http://go.microsoft.com/fwlink/p/?LinkId=256029) object's [RunAsync](http://go.microsoft.com/fwlink/p/?LinkId=256030) method to dispatch the call on the UI thread.</span></span>

```csharp
private async void Button_Click_2(object sender, RoutedEventArgs e)
{
    Button b = (Button) sender;
    await b.Dispatcher.RunAsync(
        Windows.UI.Core.CoreDispatcherPriority.Normal,
        () => {
            b.Content += ".";
    });
}

```

```vb
Private Async Sub Button_Click_2(sender As Object, e As RoutedEventArgs)
    Dim b As Button = CType(sender, Button)
    Await b.Dispatcher.RunAsync(
        Windows.UI.Core.CoreDispatcherPriority.Normal,
        Sub()
            b.Content &= "."
        End Sub)
End Sub
```

> [!NOTE]
>  <span data-ttu-id="8cdca-131">Die `Dispatcher`-Eigenschaft löst keine Ausnahme aus, wenn sie von einem anderen Thread aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="8cdca-131">The `Dispatcher` property does not throw an exception when it's called from another thread.</span></span>

<span data-ttu-id="8cdca-132">Die Lebensdauer eines Windows-Runtime-Objekts, das in dem UI-Thread erstellt wird, wird durch die Lebensdauer des Threads begrenzt.</span><span class="sxs-lookup"><span data-stu-id="8cdca-132">The lifetime of a Windows Runtime object that is created on the UI thread is bounded by the lifetime of the thread.</span></span> <span data-ttu-id="8cdca-133">Versuchen Sie nicht, auf Objekte in einem UI-Thread zuzugreifen, nachdem das Fenster geschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="8cdca-133">Do not try to access objects on a UI thread after the window has closed.</span></span>

<span data-ttu-id="8cdca-134">Wenn Sie ein eigenes Steuerelement erstellen, indem Sie ein XAML-Steuerelement übernehmen oder eine Reihe von XAML-Steuerelementen erstellen, ist Ihr Steuerelement agil, da es sich um ein .NET Framework-Objekt handelt.</span><span class="sxs-lookup"><span data-stu-id="8cdca-134">If you create your own control by inheriting a XAML control, or by composing a set of XAML controls, your control is agile because it's a .NET Framework object.</span></span> <span data-ttu-id="8cdca-135">Wenn es jedoch Elemente seiner Basisklasse oder Bestandteilklassen aufruft oder wenn Sie übernommene Elemente aufrufen, lösen diese Elemente Ausnahmen aus, wenn sie von einem anderen Thread als dem UI-Thread aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="8cdca-135">However, if it calls members of its base class or constituent classes, or if you call inherited members, those members will throw exceptions when they are called from any thread except the UI thread.</span></span>

### <a name="classes-that-cant-be-marshaled"></a><span data-ttu-id="8cdca-136">Klassen, die nicht gemarshallt werden kann</span><span class="sxs-lookup"><span data-stu-id="8cdca-136">Classes that can't be marshaled</span></span>
<span data-ttu-id="8cdca-137">Windows-Runtime-Klassen, die keine Marshalling Informationen bereitstellen, weisen das Attribut [MarshalingBehaviorAttribute](http://go.microsoft.com/fwlink/p/?LinkId=256022) mit [MarshalingType.None](http://go.microsoft.com/fwlink/p/?LinkId=256023) auf.</span><span class="sxs-lookup"><span data-stu-id="8cdca-137">Windows Runtime classes that do not provide marshaling information have the [MarshalingBehaviorAttribute](http://go.microsoft.com/fwlink/p/?LinkId=256022) attribute with [MarshalingType.None](http://go.microsoft.com/fwlink/p/?LinkId=256023).</span></span> <span data-ttu-id="8cdca-138">In der Dokumentation für solche Klassen wird „MarshalingBehaviorAttribute(None)” unter den Attributen genannt.</span><span class="sxs-lookup"><span data-stu-id="8cdca-138">The documentation for such a class lists "MarshalingBehaviorAttribute(None)" among its attributes.</span></span>

<span data-ttu-id="8cdca-139">Der folgende Code erstellt ein [CameraCaptureUI](http://go.microsoft.com/fwlink/p/?LinkId=256027)-Objekt im UI-Thread und versucht anschließend, eine Eigenschaft für das Objekt aus einem Threadpoolthread festzulegen.</span><span class="sxs-lookup"><span data-stu-id="8cdca-139">The following code creates a [CameraCaptureUI](http://go.microsoft.com/fwlink/p/?LinkId=256027) object on the UI thread, and then tries to set a property of the object from a thread pool thread.</span></span> <span data-ttu-id="8cdca-140">Die CLR kann den Aufruf nicht marshallen und löst eine [System.InvalidCastException](/dotnet/api/system.invalidcastexception)-Ausnahme mit der Meldung aus, dass das Objekt nur in dem Threadingkontext verwendet werden kann, in dem es erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="8cdca-140">The CLR is unable to marshal the call, and throws a [System.InvalidCastException](/dotnet/api/system.invalidcastexception) exception with a message indicating that the object can be used only in the threading context where it was created.</span></span>

```csharp
Windows.Media.Capture.CameraCaptureUI ccui;

private async void Button_Click_1(object sender, RoutedEventArgs e)
{
    ccui = new Windows.Media.Capture.CameraCaptureUI();

    await Task.Run(() => {
        ccui.PhotoSettings.AllowCropping = true;
    });
}

```

```vb
Private ccui As Windows.Media.Capture.CameraCaptureUI

Private Async Sub Button_Click_1(sender As Object, e As RoutedEventArgs)
    ccui = New Windows.Media.Capture.CameraCaptureUI()

    Await Task.Run(Sub()
                       ccui.PhotoSettings.AllowCropping = True
                   End Sub)
End Sub
```

<span data-ttu-id="8cdca-141">In der Dokumentation für [CameraCaptureUI](http://go.microsoft.com/fwlink/p/?LinkId=256027) wird auch „ThreadingAttribute(STA)” unter den Attributen der Klasse genannt, da es in einem Singlethread-Kontext erstellt werden muss, wie beispielsweise dem UI-Thread.</span><span class="sxs-lookup"><span data-stu-id="8cdca-141">The documentation for [CameraCaptureUI](http://go.microsoft.com/fwlink/p/?LinkId=256027) also lists "ThreadingAttribute(STA)" among the class's attributes, because it must be created in a single-threaded context such as the UI thread.</span></span>

<span data-ttu-id="8cdca-142">Wenn Sie von einem anderen Thread auf das [CameraCaptureUI](http://go.microsoft.com/fwlink/p/?LinkId=256027)-Objekt zugreifen möchten, können Sie das [CoreDispatcher](http://go.microsoft.com/fwlink/p/?LinkId=256029)-Objekt für den UI-Thread zwischenspeichern und später verwenden, um den Aufruf für diesen Thread zu verteilen.</span><span class="sxs-lookup"><span data-stu-id="8cdca-142">If you want to access the [CameraCaptureUI](http://go.microsoft.com/fwlink/p/?LinkId=256027) object from another thread, you can cache the [CoreDispatcher](http://go.microsoft.com/fwlink/p/?LinkId=256029) object for the UI thread and use it later to dispatch the call on that thread.</span></span> <span data-ttu-id="8cdca-143">Sie können den Dispatcher auch über ein XAML-Objekt wie beispielsweise die Seite abrufen, wie im folgenden Code dargestellt.</span><span class="sxs-lookup"><span data-stu-id="8cdca-143">Or you can obtain the dispatcher from a XAML object such as the page, as shown in the following code.</span></span>

```csharp
Windows.Media.Capture.CameraCaptureUI ccui;

private async void Button_Click_3(object sender, RoutedEventArgs e)
{
    ccui = new Windows.Media.Capture.CameraCaptureUI();

    await Dispatcher.RunAsync(Windows.UI.Core.CoreDispatcherPriority.Normal,
        () => {
            ccui.PhotoSettings.AllowCropping = true;
        });
}

```

```vb
Dim ccui As Windows.Media.Capture.CameraCaptureUI

Private Async Sub Button_Click_3(sender As Object, e As RoutedEventArgs)

    ccui = New Windows.Media.Capture.CameraCaptureUI()

    Await Dispatcher.RunAsync(Windows.UI.Core.CoreDispatcherPriority.Normal,
                                Sub()
                                    ccui.PhotoSettings.AllowCropping = True
                                End Sub)
End Sub
```

## <a name="objects-from-a-windows-runtime-component-that-is-written-in-c"></a><span data-ttu-id="8cdca-144">Objekte aus einer in C++ geschriebenen Windows-Runtime-Komponente</span><span class="sxs-lookup"><span data-stu-id="8cdca-144">Objects from a Windows Runtime component that is written in C++</span></span>
<span data-ttu-id="8cdca-145">Standardmäßig sind die Klassen in der Komponente, die aktiviert werden kann, agil.</span><span class="sxs-lookup"><span data-stu-id="8cdca-145">By default, classes in the component that can be activated are agile.</span></span> <span data-ttu-id="8cdca-146">C++ lässt jedoch eine umfassende Möglichkeit der Steuerung von Threadingmodellen und Marshallingverhalten zu.</span><span class="sxs-lookup"><span data-stu-id="8cdca-146">However, C++ allows a significant amount of control over threading models and marshaling behavior.</span></span> <span data-ttu-id="8cdca-147">Wie weiter oben in diesem Artikel beschrieben, erkennt die CLR agile Klassen, sie versucht, Aufrufe zu marshallen, wenn Klassen nicht agil sind, und sie löst eine [System.InvalidCastException](/dotnet/api/system.invalidcastexception)-Ausnahme aus, wenn eine Klasse keine Marshalling-Informationen aufweist.</span><span class="sxs-lookup"><span data-stu-id="8cdca-147">As described earlier in this article, the CLR recognizes agile classes, tries to marshal calls when classes are not agile, and throws a [System.InvalidCastException](/dotnet/api/system.invalidcastexception) exception when a class has no marshaling information.</span></span>

<span data-ttu-id="8cdca-148">Für Objekte, die im UI-Thread ausgeführt werden und Ausnahmen auslösen, wenn sie von einem anderen Thread als dem UI-Thread aufgerufen werden, können Sie das [CoreDispatcher](http://go.microsoft.com/fwlink/p/?LinkId=256029)-Objekt des UI-Threads verwenden, um den Aufruf zu verteilen.</span><span class="sxs-lookup"><span data-stu-id="8cdca-148">For objects that run on the UI thread and throw exceptions when they are called from a thread other than the UI thread, you can use the UI thread’s [CoreDispatcher](http://go.microsoft.com/fwlink/p/?LinkId=256029) object to dispatch the call.</span></span>

## <a name="see-also"></a><span data-ttu-id="8cdca-149">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="8cdca-149">See Also</span></span>
[<span data-ttu-id="8cdca-150">C#-Handbuch</span><span class="sxs-lookup"><span data-stu-id="8cdca-150">C# Guide</span></span>](/dotnet/articles/csharp/)

[<span data-ttu-id="8cdca-151">Visual Basic-Handbuch</span><span class="sxs-lookup"><span data-stu-id="8cdca-151">Visual Basic Guide</span></span>](/dotnet/articles/visual-basic/)
