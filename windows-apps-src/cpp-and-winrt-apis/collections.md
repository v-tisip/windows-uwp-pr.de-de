---
author: stevewhims
description: C++ / WinRT stellt Funktionen und Basisklassen, die Sie speichern und viel Zeit und Mühe beim Implementieren und/oder Sammlungen übergeben werden soll.
title: Sammlungen mit C++ / WinRT
ms.author: stwhi
ms.date: 10/03/2018
ms.topic: article
keywords: Windows 10, Uwp, standard, c++, Cpp, Winrt, Projektion, Sammlung
ms.localizationpriority: medium
ms.openlocfilehash: 93b486021813abf320645888d4f19971dc2c80ab
ms.sourcegitcommit: cd00bb829306871e5103db481cf224ea7fb613f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5861895"
---
# <a name="collections-with-cwinrt"></a><span data-ttu-id="5c4a1-104">Sammlungen mit C++ / WinRT</span><span class="sxs-lookup"><span data-stu-id="5c4a1-104">Collections with C++/WinRT</span></span>

<span data-ttu-id="5c4a1-105">Intern verfügt über eine Windows-Runtime-Auflistung viel komplizierter bewegliche Teile.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-105">Internally, a Windows Runtime collection has a lot of complicated moving parts.</span></span> <span data-ttu-id="5c4a1-106">Wenn Sie ein Collection-Objekt an eine Windows-Runtime-Funktion übergeben, oder Ihre eigenen Sammlungseigenschaften und Sammlungstypen implementieren möchten, es aber Funktionen und Basisklassen in [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) Sie unterstützen.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-106">But when you want to pass a collection object to a Windows Runtime function, or to implement your own collection properties and collection types, there are functions and base classes in [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) to support you.</span></span> <span data-ttu-id="5c4a1-107">Diese Features vereinfachen Sie Ihre Hände und Aufwand viel Zeit und Mühe sparen.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-107">These features take the complexity out of your hands, and save you a lot of overhead in time and effort.</span></span>

<span data-ttu-id="5c4a1-108">[**IVector**](/uwp/api/windows.foundation.collections.ivector_t_) ist die Windows-Runtime-Schnittstelle, die von direktem Zugriff eine Sammlung von Elementen implementiert.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-108">[**IVector**](/uwp/api/windows.foundation.collections.ivector_t_) is the Windows Runtime interface implemented by any random-access collection of elements.</span></span> <span data-ttu-id="5c4a1-109">Wenn Sie **IVector** selbst implementieren würden, müssten Sie auch [**IIterable**](/uwp/api/windows.foundation.collections.iiterable_t_), [**IVectorView**](/uwp/api/windows.foundation.collections.ivectorview_t_)und [**IIterator**](/uwp/api/windows.foundation.collections.iiterator_t_)zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-109">If you were to implement **IVector** yourself, you'd also need to implement [**IIterable**](/uwp/api/windows.foundation.collections.iiterable_t_), [**IVectorView**](/uwp/api/windows.foundation.collections.ivectorview_t_), and [**IIterator**](/uwp/api/windows.foundation.collections.iiterator_t_).</span></span> <span data-ttu-id="5c4a1-110">Selbst wenn Sie eine benutzerdefinierte Auflistung *müssen* eingeben, ist eine Menge Arbeit.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-110">Even if you *need* a custom collection type, that's a lot of work.</span></span> <span data-ttu-id="5c4a1-111">Wenn Sie Daten in einem **Std:: Vector** (oder eine **Std:: Map**oder ein **std::unordered_map**) haben, und alles, was Sie tun möchten, die an einer Windows-Runtime-API übergeben wird, möchten dann aber wäre, damit kein dieser Ebene der Arbeit, wenn möglich.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-111">But if you have data in a **std::vector** (or a **std::map**, or a **std::unordered_map**) and all you want to do is pass that to a Windows Runtime API, then you'd want to avoid doing that level of work, if possible.</span></span> <span data-ttu-id="5c4a1-112">Und es *ist* möglich, vermeiden, da C++ / WinRT können Sie zum Erstellen von Sammlungen effizient und mit wenig Aufwand.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-112">And avoiding it *is* possible, because C++/WinRT helps you to create collections efficiently and with little effort.</span></span>

<span data-ttu-id="5c4a1-113">Weitere Informationen finden Sie [XAML-items-Steuerelemente; binden an eine C++ / WinRT-Collection](binding-collection.md).</span><span class="sxs-lookup"><span data-stu-id="5c4a1-113">Also see [XAML items controls; bind to a C++/WinRT collection](binding-collection.md).</span></span>

> [!NOTE]
> <span data-ttu-id="5c4a1-114">Wenn Sie noch nicht installiert, das Windows SDK Version 10.0.17763.0 (Windows 10, Version 1809 haben) oder höher ist, dann haben Sie keinen Zugriff auf Funktionen und Basisklassen, die in diesem Thema beschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-114">If you haven't installed the Windows SDK version 10.0.17763.0 (Windows 10, version 1809), or later, then you won't have access to the functions and base classes that are documented in this topic.</span></span> <span data-ttu-id="5c4a1-115">Finden Sie stattdessen eine Liste der eine Observable-Vektor-Vorlage, die Sie stattdessen verwenden können [, wenn Sie eine ältere Version des Windows SDK verwenden](/uwp/cpp-ref-for-winrt/single-threaded-observable-vector#if-you-have-an-older-version-of-the-windows-sdk) .</span><span class="sxs-lookup"><span data-stu-id="5c4a1-115">Instead, see [If you have an older version of the Windows SDK](/uwp/cpp-ref-for-winrt/single-threaded-observable-vector#if-you-have-an-older-version-of-the-windows-sdk) for a listing of an observable vector template that you can use instead.</span></span>

## <a name="helper-functions-for-collections"></a><span data-ttu-id="5c4a1-116">Hilfsfunktionen für Sammlungen</span><span class="sxs-lookup"><span data-stu-id="5c4a1-116">Helper functions for collections</span></span>

### <a name="general-purpose-collection-empty"></a><span data-ttu-id="5c4a1-117">Allgemeine Auflistung leer.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-117">General-purpose collection, empty</span></span>

<span data-ttu-id="5c4a1-118">Dieser Abschnitt behandelt das Szenario, in dem Sie eine Sammlung erstellen, die anfänglich leer ist möchten; und füllen Sie es *nach* dem erstellen.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-118">This section covers the scenario where you wish to create a collection that's initially empty; and then populate it *after* creation.</span></span>

<span data-ttu-id="5c4a1-119">Um ein neues Objekt eines Typs abzurufen, die eine allgemeine Auflistung implementiert, können Sie die Funktionsvorlage [**winrt::single_threaded_vector**](/uwp/cpp-ref-for-winrt/single-threaded-vector) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-119">To retrieve a new object of a type that implements a general-purpose collection, you can call the [**winrt::single_threaded_vector**](/uwp/cpp-ref-for-winrt/single-threaded-vector) function template.</span></span> <span data-ttu-id="5c4a1-120">Das Objekt wird als ein [**IVector**](/uwp/api/windows.foundation.collections.ivector_t_)zurückgegeben, und dies ist die Schnittstelle, die über die Funktionen und Eigenschaften des zurückgegebenen Objekts aufrufen.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-120">The object is returned as an [**IVector**](/uwp/api/windows.foundation.collections.ivector_t_), and that's the interface via which you call the returned object's functions and properties.</span></span>

```cppwinrt
...
#include <winrt/Windows.Foundation.Collections.h>
#include <iostream>
using namespace winrt;
...
int main()
{
    winrt::init_apartment();

    Windows::Foundation::Collections::IVector<int> coll{ winrt::single_threaded_vector<int>() };
    coll.Append(1);
    coll.Append(2);
    coll.Append(3);

    for (auto const& el : coll)
    {
        std::cout << el << std::endl;
    }

    Windows::Foundation::Collections::IVectorView<int> view{ coll.GetView() };
}
```

<span data-ttu-id="5c4a1-121">Wie im obigen Codebeispiel sehen, nach dem Erstellen der Auflistung können Sie Elemente anfügen, durchlaufen sie und behandeln Sie das Objekt in der Regel wie alle Windows-Runtime-Collection-Objekt, das Sie von einer API erhalten haben.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-121">As you can see in the code example above, after creating the collection you can append elements, iterate over them, and generally treat the object as you would any Windows Runtime collection object that you might have received from an API.</span></span> <span data-ttu-id="5c4a1-122">Wenn Sie eine unveränderliche Ansicht über die Auflistung benötigen, können Sie wie gezeigt [**IVector::GetView**](/uwp/api/windows.foundation.collections.ivector-1.getview), aufrufen.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-122">If you need an immutable view over the collection, then you can call [**IVector::GetView**](/uwp/api/windows.foundation.collections.ivector-1.getview), as shown.</span></span> <span data-ttu-id="5c4a1-123">Das oben gezeigte Muster&mdash;der Erstellung und Nutzung von einer Sammlungs&mdash;eignet sich für einfache Szenarien, in denen Sie Daten in übergeben oder Abrufen von Daten aus einer API möchten.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-123">The pattern shown above&mdash;of creating and consuming a collection&mdash;is appropriate for simple scenarios where you want to pass data into, or get data out of, an API.</span></span> <span data-ttu-id="5c4a1-124">Sie können eine **IVector**oder ein **IVectorView**übergeben, an einer beliebigen Stelle einer [**IIterable**](/uwp/api/windows.foundation.collections.iiterable_t_) erwartet wird.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-124">You can pass an **IVector**, or an **IVectorView**, anywhere an [**IIterable**](/uwp/api/windows.foundation.collections.iiterable_t_) is expected.</span></span>

<span data-ttu-id="5c4a1-125">Im obigen Codebeispiel initialisiert der Aufruf von **WinRT:: init_apartment** COM; standardmäßig in einem Multithread-Apartment.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-125">In the code example above, the call to **winrt::init_apartment** initializes COM; by default, in a multithreaded apartment.</span></span>

### <a name="general-purpose-collection-primed-from-data"></a><span data-ttu-id="5c4a1-126">Allgemeine Auflistung, die von Daten vorbereitet</span><span class="sxs-lookup"><span data-stu-id="5c4a1-126">General-purpose collection, primed from data</span></span>

<span data-ttu-id="5c4a1-127">Dieser Abschnitt behandelt das Szenario, in denen Sie eine Sammlung erstellen und füllen diese zur gleichen Zeit möchten.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-127">This section covers the scenario where you wish to create a collection and populate it at the same time.</span></span>

<span data-ttu-id="5c4a1-128">Sie können den Aufwand für die Aufrufe von **Append** im vorherigen Codebeispiel vermeiden.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-128">You can avoid the overhead of the calls to **Append** in the previous code example.</span></span> <span data-ttu-id="5c4a1-129">Möglicherweise haben Sie bereits die Quelldaten, oder Sie können aber auch die Quelldaten vor dem Erstellen des Windows-Runtime-Collection-Objekts zu füllen.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-129">You may already have the source data, or you may prefer to populate the source data in advance of creating the Windows Runtime collection object.</span></span> <span data-ttu-id="5c4a1-130">Gehen Sie dazu wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="5c4a1-130">Here's how to do that.</span></span>

```cppwinrt
auto coll1{ winrt::single_threaded_vector<int>({ 1,2,3 }) };

std::vector<int> values{ 1,2,3 };
auto coll2{ winrt::single_threaded_vector<int>(std::move(values)) };

for (auto const& el : coll2)
{
    std::cout << el << std::endl;
}
```

<span data-ttu-id="5c4a1-131">Sie können ein temporäres Objekt, die Ihre Daten **winrt::single_threaded_vector**, enthält übergeben wie bei `coll1`oben.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-131">You can pass a temporary object containing your data to **winrt::single_threaded_vector**, as with `coll1`, above.</span></span> <span data-ttu-id="5c4a1-132">Oder Sie können eine **Std:: Vector** (vorausgesetzt, Sie wird nicht werden auf diese zugreifenden erneut) verschieben in die Funktion.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-132">Or you can move a **std::vector** (assuming you won't be accessing it again) into the function.</span></span> <span data-ttu-id="5c4a1-133">In beiden Fällen können Sie einen *r-Wert* an die Funktion übergeben.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-133">In both cases, you're passing an *rvalue* into the function.</span></span> <span data-ttu-id="5c4a1-134">Ermöglicht den Compiler effizient, und vermeiden die Daten zu kopieren.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-134">That enables the compiler to be efficient and to avoid copying the data.</span></span> <span data-ttu-id="5c4a1-135">Wenn Sie mehr über *Rvalues*erfahren möchten, finden Sie unter [Wertekategorien, und Verweise auf diese](cpp-value-categories.md).</span><span class="sxs-lookup"><span data-stu-id="5c4a1-135">If you want to know more about *rvalues*, see [Value categories, and references to them](cpp-value-categories.md).</span></span>

<span data-ttu-id="5c4a1-136">Wenn Sie ein XAML-Items-Steuerelement an eine Sammlung binden möchten, können Sie Sie.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-136">If you want to bind a XAML items control to your collection, then you can.</span></span> <span data-ttu-id="5c4a1-137">Beachten Sie jedoch, um die Eigenschaft [**ItemsControl.ItemsSource**](/uwp/api/windows.ui.xaml.controls.itemscontrol.itemssource) richtig festzulegen, Sie festlegen, dass ein Wert vom Typ **IVector** **IInspectable** (oder eine Interoperabilität Typ wie z. B. [**IBindableObservableVector müssen**](/uwp/api/windows.ui.xaml.interop.ibindableobservablevector)).</span><span class="sxs-lookup"><span data-stu-id="5c4a1-137">But be aware that to correctly set the [**ItemsControl.ItemsSource**](/uwp/api/windows.ui.xaml.controls.itemscontrol.itemssource) property, you need to set it to a value of type **IVector** of **IInspectable** (or of an interoperability type such as [**IBindableObservableVector**](/uwp/api/windows.ui.xaml.interop.ibindableobservablevector)).</span></span> <span data-ttu-id="5c4a1-138">Hier ist ein Codebeispiel, das eine Sammlung von einem Typ, der für die Bindung geeignet erzeugt fügt an ein Element an, ein.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-138">Here's a code example that produces a collection of a type suitable for binding, and appends an element to it.</span></span>

```cppwinrt
auto bookSkus{ winrt::single_threaded_vector<Windows::Foundation::IInspectable>() };
bookSkus.Append(make<Bookstore::implementation::BookSku>(L"Moby Dick"));
```

<span data-ttu-id="5c4a1-139">Sie können eine Windows-Runtime-Sammlung von Daten erstellen und bereiten Sie eine Ansicht für dieses auf, übergeben Sie an eine API, ohne etwas zu kopieren.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-139">You can create a Windows Runtime collection from data, and get a view on it ready to pass to an API, all without copying anything.</span></span>

```cppwinrt
std::vector<float> values{ 0.1f, 0.2f, 0.3f };
IVectorView<float> view{ winrt::single_threaded_vector(std::move(values)).GetView() };
```

<span data-ttu-id="5c4a1-140">In den obigen Beispielen werden die Sammlung *erstellen wir* an ein XAML-Items-Steuerelement gebunden. aber die Sammlung nicht feststellbar.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-140">In the examples above, the collection we create *can* be bound to a XAML items control; but the collection isn't observable.</span></span>

### <a name="observable-collection"></a><span data-ttu-id="5c4a1-141">Observable-collection</span><span class="sxs-lookup"><span data-stu-id="5c4a1-141">Observable collection</span></span>

<span data-ttu-id="5c4a1-142">Ein neues Objekt eines Typs abrufen, die eine *Observable* -Collection implementiert, rufen Sie die Funktionsvorlage [**winrt::single_threaded_observable_vector**](/uwp/cpp-ref-for-winrt/single-threaded-observable-vector) mit jedem beliebigen Elementtyp.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-142">To retrieve a new object of a type that implements an *observable* collection, call the [**winrt::single_threaded_observable_vector**](/uwp/cpp-ref-for-winrt/single-threaded-observable-vector) function template with any element type.</span></span> <span data-ttu-id="5c4a1-143">Jedoch verwenden, um eine Observable-Collection eignen sich für die Bindung an ein XAML-Items-Steuerelement machen **IInspectable** als Typ des Elements.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-143">But to make an observable collection suitable for binding to a XAML items control, use **IInspectable** as the element type.</span></span>

<span data-ttu-id="5c4a1-144">Das Objekt wird als ein [**IObservableVector**](/uwp/api/windows.foundation.collections.iobservablevector_t_)zurückgegeben, und ist die Schnittstelle, über die Sie (oder das Steuerelement an das sie gebunden ist) des zurückgegebenen Objekts Funktionen und Eigenschaften aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-144">The object is returned as an [**IObservableVector**](/uwp/api/windows.foundation.collections.iobservablevector_t_), and that's the interface via which you (or the control to which it's bound) call the returned object's functions and properties.</span></span>

```cppwinrt
auto bookSkus{ winrt::single_threaded_observable_vector<Windows::Foundation::IInspectable>() };
```

<span data-ttu-id="5c4a1-145">Weitere Details und Codebeispiele, über das den Benutzer binden Benutzeroberfläche (UI) steuert, um eine Observable-Collection, finden Sie unter [XAML-items-Steuerelemente; binden an eine C++ / WinRT-Collection](binding-collection.md).</span><span class="sxs-lookup"><span data-stu-id="5c4a1-145">For more details, and code examples, about binding your user interface (UI) controls to an observable collection, see [XAML items controls; bind to a C++/WinRT collection](binding-collection.md).</span></span>

### <a name="associative-collection-map"></a><span data-ttu-id="5c4a1-146">Assoziative Sammlung (Map)</span><span class="sxs-lookup"><span data-stu-id="5c4a1-146">Associative collection (map)</span></span>

<span data-ttu-id="5c4a1-147">Es gibt Versionen der beiden Funktionen, denen bereits assoziative Auflistung.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-147">There are associative collection versions of the two functions that we've looked at.</span></span>

- <span data-ttu-id="5c4a1-148">Die Funktionsvorlage [**winrt::single_threaded_map**](/uwp/cpp-ref-for-winrt/single-threaded-map) gibt eine assoziative nicht feststellbare Sammlung als ein [**IMap**](/uwp/api/windows.foundation.collections.imap_k_v_)zurück.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-148">The [**winrt::single_threaded_map**](/uwp/cpp-ref-for-winrt/single-threaded-map) function template returns a non-observable associative collection as an [**IMap**](/uwp/api/windows.foundation.collections.imap_k_v_).</span></span>
- <span data-ttu-id="5c4a1-149">Die Funktionsvorlage [**winrt::single_threaded_observable_map**](/uwp/cpp-ref-for-winrt/single-threaded-observable-map) gibt eine assoziative Observable-Collection als ein [**IObservableMap**](/uwp/api/windows.foundation.collections.iobservablemap_k_v_)zurück.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-149">The [**winrt::single_threaded_observable_map**](/uwp/cpp-ref-for-winrt/single-threaded-observable-map) function template returns an observable associative collection as an [**IObservableMap**](/uwp/api/windows.foundation.collections.iobservablemap_k_v_).</span></span>

<span data-ttu-id="5c4a1-150">Sie können diese Sammlungen mit Daten optional Systemdatenträgern, indem Sie einen *r-Wert* des Typs **Std:: Map** oder **std::unordered_map**an die Funktion übergeben.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-150">You can optionally prime these collections with data by passing to the function an *rvalue* of type **std::map** or **std::unordered_map**.</span></span>

```cppwinrt
auto coll1{
    winrt::single_threaded_map<winrt::hstring, int>(std::map<winrt::hstring, int>{
        { L"AliceBlue", 0xfff0f8ff }, { L"AntiqueWhite", 0xfffaebd7 }
    })
};

std::map<winrt::hstring, int> values{
    { L"AliceBlue", 0xfff0f8ff }, { L"AntiqueWhite", 0xfffaebd7 }
};
auto coll2{ winrt::single_threaded_map<winrt::hstring, int>(std::move(values)) };
```

### <a name="single-threaded"></a><span data-ttu-id="5c4a1-151">Single threaded-</span><span class="sxs-lookup"><span data-stu-id="5c4a1-151">Single-threaded</span></span>

<span data-ttu-id="5c4a1-152">Die "Single-threaded" in den Namen dieser Funktionen gibt an, dass sie alle Parallelität bieten keine&mdash;mit anderen Worten: sie sind nicht threadsicher.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-152">The "single-threaded" in the names of these functions indicates that they don't provide any concurrency&mdash;in other words, they're not thread-safe.</span></span> <span data-ttu-id="5c4a1-153">Die erwähnen von Threads ist nicht im Zusammenhang mit Apartments, da die von diesen Funktionen zurückgegebenen Objekte alle agil sind (siehe [Agile Objekte in C++ / WinRT](agile-objects.md)).</span><span class="sxs-lookup"><span data-stu-id="5c4a1-153">The mention of threads is unrelated to apartments, because the objects returned from these functions are all agile (see [Agile objects in C++/WinRT](agile-objects.md)).</span></span> <span data-ttu-id="5c4a1-154">Es ist einfach, dass die Objekte Singlethread-sind.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-154">It's just that the objects are single-threaded.</span></span> <span data-ttu-id="5c4a1-155">Und das ist vollständig geeignet, wenn nur Daten eine Möglichkeit oder andere über die Application binary Interface (ABI) übergeben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-155">And that's entirely appropriate if you just want to pass data one way or the other across the application binary interface (ABI).</span></span>

## <a name="base-classes-for-collections"></a><span data-ttu-id="5c4a1-156">Basisklassen für Sammlungen</span><span class="sxs-lookup"><span data-stu-id="5c4a1-156">Base classes for collections</span></span>

<span data-ttu-id="5c4a1-157">Wenn Sie vollständige Flexibilität, eine eigene benutzerdefinierte Auflistung implementieren möchten, sollten Sie dabei, die schwer zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-157">If, for complete flexibility, you want to implement your own custom collection, then you'll want to avoid doing that the hard way.</span></span> <span data-ttu-id="5c4a1-158">Beispielsweise sieht wie eine benutzerdefinierte Vektoransicht aussehen würde *ohne Unterstützung des C++ / WinRT-Basisklassen*.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-158">For example, this is what a custom vector view would look like *without the assistance of C++/WinRT's base classes*.</span></span>

```cppwinrt
...
using namespace winrt;
using namespace Windows::Foundation::Collections;
...
struct MyVectorView :
    implements<MyVectorView, IVectorView<float>, IIterable<float>>
{
    // IVectorView
    float GetAt(uint32_t const) { ... };
    uint32_t GetMany(uint32_t, winrt::array_view<float>) const { ... };
    bool IndexOf(float, uint32_t&) { ... };
    uint32_t Size() { ... };

    // IIterable
    IIterator<float> First() const { ... };
};
...
IVectorView<float> view{ winrt::make<MyVectorView>() };
```

<span data-ttu-id="5c4a1-159">Stattdessen ist es sehr viel einfacher, leiten Ihre benutzerdefinierte Vektoransicht aus der strukturvorlage [**winrt::vector_view_base**](/uwp/cpp-ref-for-winrt/vector-view-base) , und implementieren Sie einfach die **Get_container** -Funktion, um dem Container, Ihre Daten verfügbar zu machen.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-159">Instead, it's much easier to derive your custom vector view from the [**winrt::vector_view_base**](/uwp/cpp-ref-for-winrt/vector-view-base) struct template, and just implement the **get_container** function to expose the container holding your data.</span></span>

```cppwinrt
struct MyVectorView2 :
    implements<MyVectorView2, IVectorView<float>, IIterable<float>>,
    winrt::vector_view_base<MyVectorView2, float>
{
    auto& get_container() const noexcept
    {
        return m_values;
    }

private:
    std::vector<float> m_values{ 0.1f, 0.2f, 0.3f };
};
```

<span data-ttu-id="5c4a1-160">Der Container **Get_container** zurückgegebene muss stellen die Schnittstelle **Anfang** und **Ende** dieses **winrt::vector_view_base** erwartet.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-160">The container returned by **get_container** must provide the **begin** and **end** interface that **winrt::vector_view_base** expects.</span></span> <span data-ttu-id="5c4a1-161">Wie im obigen Beispiel gezeigt, bereitstellt **Std:: Vector** .</span><span class="sxs-lookup"><span data-stu-id="5c4a1-161">As shown in the example above, **std::vector** provides that.</span></span> <span data-ttu-id="5c4a1-162">Aber Sie können alle Container, die den gleichen Vertrag, einschließlich Ihrer eigenen benutzerdefinierten Container erfüllt zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-162">But you can return any container that fulfils the same contract, including your own custom container.</span></span>

```cppwinrt
struct MyVectorView3 :
    implements<MyVectorView3, IVectorView<float>, IIterable<float>>,
    winrt::vector_view_base<MyVectorView3, float>
{
    auto get_container() const noexcept
    {
        struct container
        {
            float const* const first;
            float const* const last;

            auto begin() const noexcept
            {
                return first;
            }

            auto end() const noexcept
            {
                return last;
            }
        };

        return container{ m_values.data(), m_values.data() + m_values.size() };
    }

private:
    std::array<float, 3> m_values{ 0.2f, 0.3f, 0.4f };
};
```

<span data-ttu-id="5c4a1-163">Hierbei handelt es sich um die Basis Klassen, C++ / WinRT bereitgestellt wird, um benutzerdefinierte Sammlungen Implementierung zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-163">These are the base classes that C++/WinRT provides to help you implement custom collections.</span></span>

### [<a name="winrtvectorviewbase"></a><span data-ttu-id="5c4a1-164">WinRT::vector_view_base</span><span class="sxs-lookup"><span data-stu-id="5c4a1-164">winrt::vector_view_base</span></span>](/uwp/cpp-ref-for-winrt/vector-view-base)

<span data-ttu-id="5c4a1-165">Siehe obigen Codebeispiele.</span><span class="sxs-lookup"><span data-stu-id="5c4a1-165">See the code examples above.</span></span>

### [<a name="winrtvectorbase"></a><span data-ttu-id="5c4a1-166">WinRT::vector_base</span><span class="sxs-lookup"><span data-stu-id="5c4a1-166">winrt::vector_base</span></span>](/uwp/cpp-ref-for-winrt/vector-base)

```cppwinrt
struct MyVector :
    implements<MyVector, IVector<float>, IVectorView<float>, IIterable<float>>,
    winrt::vector_base<MyVector, float>
{
    auto& get_container() const noexcept
    {
        return m_values;
    }

    auto& get_container() noexcept
    {
        return m_values;
    }

private:
    std::vector<float> m_values{ 0.1f, 0.2f, 0.3f };
};
```

### [<a name="winrtobservablevectorbase"></a><span data-ttu-id="5c4a1-167">WinRT::observable_vector_base</span><span class="sxs-lookup"><span data-stu-id="5c4a1-167">winrt::observable_vector_base</span></span>](/uwp/cpp-ref-for-winrt/observable-vector-base)

```cppwinrt
struct MyObservableVector :
    implements<MyObservableVector, IObservableVector<float>, IVector<float>, IVectorView<float>, IIterable<float>>,
    winrt::observable_vector_base<MyObservableVector, float>
{
    auto& get_container() const noexcept
    {
        return m_values;
    }

    auto& get_container() noexcept
    {
        return m_values;
    }

private:
    std::vector<float> m_values{ 0.1f, 0.2f, 0.3f };
};
```

### [<a name="winrtmapviewbase"></a><span data-ttu-id="5c4a1-168">WinRT::map_view_base</span><span class="sxs-lookup"><span data-stu-id="5c4a1-168">winrt::map_view_base</span></span>](/uwp/cpp-ref-for-winrt/map-view-base)

```cppwinrt
struct MyMapView :
    implements<MyMapView, IMapView<winrt::hstring, int>, IIterable<IKeyValuePair<winrt::hstring, int>>>,
    winrt::map_view_base<MyMapView, winrt::hstring, int>
{
    auto& get_container() const noexcept
    {
        return m_values;
    }

private:
    std::map<winrt::hstring, int> m_values{
        { L"AliceBlue", 0xfff0f8ff }, { L"AntiqueWhite", 0xfffaebd7 }
    };
};
```

### [<a name="winrtmapbase"></a><span data-ttu-id="5c4a1-169">WinRT::map_base</span><span class="sxs-lookup"><span data-stu-id="5c4a1-169">winrt::map_base</span></span>](/uwp/cpp-ref-for-winrt/map-base)

```cppwinrt
struct MyMap :
    implements<MyMap, IMap<winrt::hstring, int>, IMapView<winrt::hstring, int>, IIterable<IKeyValuePair<winrt::hstring, int>>>,
    winrt::map_base<MyMap, winrt::hstring, int>
{
    auto& get_container() const noexcept
    {
        return m_values;
    }

    auto& get_container() noexcept
    {
        return m_values;
    }

private:
    std::map<winrt::hstring, int> m_values{
        { L"AliceBlue", 0xfff0f8ff }, { L"AntiqueWhite", 0xfffaebd7 }
    };
};
```

### [<a name="winrtobservablemapbase"></a><span data-ttu-id="5c4a1-170">WinRT::observable_map_base</span><span class="sxs-lookup"><span data-stu-id="5c4a1-170">winrt::observable_map_base</span></span>](/uwp/cpp-ref-for-winrt/observable-map-base)

```cppwinrt
struct MyObservableMap :
    implements<MyObservableMap, IObservableMap<winrt::hstring, int>, IMap<winrt::hstring, int>, IMapView<winrt::hstring, int>, IIterable<IKeyValuePair<winrt::hstring, int>>>,
    winrt::observable_map_base<MyObservableMap, winrt::hstring, int>
{
    auto& get_container() const noexcept
    {
        return m_values;
    }

    auto& get_container() noexcept
    {
        return m_values;
    }

private:
    std::map<winrt::hstring, int> m_values{
        { L"AliceBlue", 0xfff0f8ff }, { L"AntiqueWhite", 0xfffaebd7 }
    };
};
```

## <a name="important-apis"></a><span data-ttu-id="5c4a1-171">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="5c4a1-171">Important APIs</span></span>
* [<span data-ttu-id="5c4a1-172">ItemsControl.ItemsSource-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="5c4a1-172">ItemsControl.ItemsSource property</span></span>](/uwp/api/windows.ui.xaml.controls.itemscontrol.itemssource)
* [<span data-ttu-id="5c4a1-173">IObservableVector-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5c4a1-173">IObservableVector interface</span></span>](/uwp/api/windows.foundation.collections.iobservablevector_t_)
* [<span data-ttu-id="5c4a1-174">IVector Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5c4a1-174">IVector interface</span></span>](/uwp/api/windows.foundation.collections.ivector_t_)
* [<span data-ttu-id="5c4a1-175">WinRT::map_base strukturvorlage</span><span class="sxs-lookup"><span data-stu-id="5c4a1-175">winrt::map_base struct template</span></span>](/uwp/cpp-ref-for-winrt/map-base)
* [<span data-ttu-id="5c4a1-176">WinRT::map_view_base strukturvorlage</span><span class="sxs-lookup"><span data-stu-id="5c4a1-176">winrt::map_view_base struct template</span></span>](/uwp/cpp-ref-for-winrt/map-view-base)
* [<span data-ttu-id="5c4a1-177">WinRT::observable_map_base strukturvorlage</span><span class="sxs-lookup"><span data-stu-id="5c4a1-177">winrt::observable_map_base struct template</span></span>](/uwp/cpp-ref-for-winrt/observable-map-base)
* [<span data-ttu-id="5c4a1-178">WinRT::observable_vector_base strukturvorlage</span><span class="sxs-lookup"><span data-stu-id="5c4a1-178">winrt::observable_vector_base struct template</span></span>](/uwp/cpp-ref-for-winrt/observable-vector-base)
* [<span data-ttu-id="5c4a1-179">WinRT::single_threaded_observable_map Funktionsvorlage</span><span class="sxs-lookup"><span data-stu-id="5c4a1-179">winrt::single_threaded_observable_map function template</span></span>](/uwp/cpp-ref-for-winrt/single-threaded-observable-map)
* [<span data-ttu-id="5c4a1-180">WinRT::single_threaded_map Funktionsvorlage</span><span class="sxs-lookup"><span data-stu-id="5c4a1-180">winrt::single_threaded_map function template</span></span>](/uwp/cpp-ref-for-winrt/single-threaded-map)
* [<span data-ttu-id="5c4a1-181">WinRT::single_threaded_observable_vector Funktionsvorlage</span><span class="sxs-lookup"><span data-stu-id="5c4a1-181">winrt::single_threaded_observable_vector function template</span></span>](/uwp/cpp-ref-for-winrt/single-threaded-observable-vector)
* [<span data-ttu-id="5c4a1-182">WinRT::single_threaded_vector Funktionsvorlage</span><span class="sxs-lookup"><span data-stu-id="5c4a1-182">winrt::single_threaded_vector function template</span></span>](/uwp/cpp-ref-for-winrt/single-threaded-vector)
* [<span data-ttu-id="5c4a1-183">WinRT::vector_base strukturvorlage</span><span class="sxs-lookup"><span data-stu-id="5c4a1-183">winrt::vector_base struct template</span></span>](/uwp/cpp-ref-for-winrt/vector-base)
* [<span data-ttu-id="5c4a1-184">WinRT::vector_view_base strukturvorlage</span><span class="sxs-lookup"><span data-stu-id="5c4a1-184">winrt::vector_view_base struct template</span></span>](/uwp/cpp-ref-for-winrt/vector-view-base)

## <a name="related-topics"></a><span data-ttu-id="5c4a1-185">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="5c4a1-185">Related topics</span></span>
* [<span data-ttu-id="5c4a1-186">Wertekategorien und Verweise auf diese</span><span class="sxs-lookup"><span data-stu-id="5c4a1-186">Value categories, and references to them</span></span>](cpp-value-categories.md)
* [<span data-ttu-id="5c4a1-187">XAML-Items-Steuerelemente; Binden an eine C++/WinRT-Collection</span><span class="sxs-lookup"><span data-stu-id="5c4a1-187">XAML items controls; bind to a C++/WinRT collection</span></span>](binding-collection.md)
