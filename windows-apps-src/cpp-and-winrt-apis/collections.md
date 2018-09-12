---
author: stevewhims
description: C + / WinRT stellt Funktionen und Klassen, die Sie Zeit und Mühe sparen zu implementieren oder Sammlungen übergeben soll.
title: Sammlungen mit C / WinRT
ms.author: stwhi
ms.date: 08/24/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10 Uwp standard, C ++ Cpp, Winrt, Projektion, Auflistung
ms.localizationpriority: medium
ms.openlocfilehash: 1ef6fbfab45197c868296186363c168a6c443247
ms.sourcegitcommit: 2a63ee6770413bc35ace09b14f56b60007be7433
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2018
ms.locfileid: "3930786"
---
# <a name="collections-with-cwinrtwindowsuwpcpp-and-winrt-apisintro-to-using-cpp-with-winrt"></a><span data-ttu-id="3db99-104">Sammlungen mit [C + / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)</span><span class="sxs-lookup"><span data-stu-id="3db99-104">Collections with [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)</span></span>

> [!NOTE]
> **<span data-ttu-id="3db99-105">Einige Informationen beziehen sich auf die Vorabversion, die vor der kommerziellen Freigabe möglicherweise wesentlichen Änderungen unterliegt.</span><span class="sxs-lookup"><span data-stu-id="3db99-105">Some information relates to pre-released product which may be substantially modified before it’s commercially released.</span></span> <span data-ttu-id="3db99-106">Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.</span><span class="sxs-lookup"><span data-stu-id="3db99-106">Microsoft makes no warranties, express or implied, with respect to the information provided here.</span></span>**

<span data-ttu-id="3db99-107">Windows-Runtime-Auflistung wurde intern viel komplizierter Teile.</span><span class="sxs-lookup"><span data-stu-id="3db99-107">Internally, a Windows Runtime collection has a lot of complicated moving parts.</span></span> <span data-ttu-id="3db99-108">Aber wenn Sie ein Auflistungsobjekt an eine Windows-Runtime-Funktion übergeben oder eigene Auflistungseigenschaften und Auflistungstypen implementieren möchten, Funktionen und Klassen in C# gibt / WinRT unterstützt Sie.</span><span class="sxs-lookup"><span data-stu-id="3db99-108">But when you want to pass a collection object to a Windows Runtime function, or to implement your own collection properties and collection types, there are functions and base classes in C++/WinRT to support you.</span></span> <span data-ttu-id="3db99-109">Diese Features vereinfachen Sie Ihre Hände und viel Aufwand Zeit und Mühe sparen.</span><span class="sxs-lookup"><span data-stu-id="3db99-109">These features take the complexity out of your hands, and save you a lot of overhead in time and effort.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3db99-110">In diesem Thema beschriebenen Features sind verfügbar, wenn die Installation von [Windows 10 SDK Vorschau erstellen 17661](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK)oder höher.</span><span class="sxs-lookup"><span data-stu-id="3db99-110">The features described in this topic are available if you've installed the [Windows 10 SDK Preview Build 17661](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK), or later.</span></span>

<span data-ttu-id="3db99-111">[**IVector**](/uwp/api/windows.foundation.collections.ivector_t_) ist die Windows-Runtime-Schnittstelle alle RAM Auflistung Elemente implementiert.</span><span class="sxs-lookup"><span data-stu-id="3db99-111">[**IVector**](/uwp/api/windows.foundation.collections.ivector_t_) is the Windows Runtime interface implemented by any random-access collection of elements.</span></span> <span data-ttu-id="3db99-112">Würden Sie **IVector** selbst implementieren, müssten Sie auch [**IIterable**](/uwp/api/windows.foundation.collections.iiterable_t_), [**IVectorView**](/uwp/api/windows.foundation.collections.ivectorview_t_)und [**IIterator**](/uwp/api/windows.foundation.collections.iiterator_t_)implementieren.</span><span class="sxs-lookup"><span data-stu-id="3db99-112">If you were to implement **IVector** yourself, you'd also need to implement [**IIterable**](/uwp/api/windows.foundation.collections.iiterable_t_), [**IVectorView**](/uwp/api/windows.foundation.collections.ivectorview_t_), and [**IIterator**](/uwp/api/windows.foundation.collections.iiterator_t_).</span></span> <span data-ttu-id="3db99-113">Auch *müssen* Sie eine benutzerdefinierte Auflistung geben wird, die eine Menge Arbeit.</span><span class="sxs-lookup"><span data-stu-id="3db99-113">Even if you *need* a custom collection type, that's a lot of work.</span></span> <span data-ttu-id="3db99-114">Aber wenn **sind** ( **Std:: Map**oder **std::unordered_map Daten**) und benötigen Sie eine Windows-Runtime-API übergeben, dann möchten vermeiden, auf Arbeit, wenn möglich.</span><span class="sxs-lookup"><span data-stu-id="3db99-114">But if you have data in a **std::vector** (or a **std::map**, or a **std::unordered_map**) and all you want to do is pass that to a Windows Runtime API, then you'd want to avoid doing that level of work, if possible.</span></span> <span data-ttu-id="3db99-115">Und es *ist* möglich, da C + / WinRT können Sie Sammlungen effizient und mit geringem Aufwand erstellen.</span><span class="sxs-lookup"><span data-stu-id="3db99-115">And avoiding it *is* possible, because C++/WinRT helps you to create collections efficiently and with little effort.</span></span>

## <a name="helper-functions-for-collections"></a><span data-ttu-id="3db99-116">Hilfsfunktionen für Sammlungen</span><span class="sxs-lookup"><span data-stu-id="3db99-116">Helper functions for collections</span></span>

### <a name="general-purpose-collection-empty"></a><span data-ttu-id="3db99-117">Allgemeine Auflistung leer</span><span class="sxs-lookup"><span data-stu-id="3db99-117">General-purpose collection, empty</span></span>

<span data-ttu-id="3db99-118">Rufen Sie ein neues Objekt ein, das eine allgemeine Auflistung implementiert, können Sie die Funktionsvorlage [**winrt::single_threaded_vector**](/uwp/cpp-ref-for-winrt/single-threaded-vector) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="3db99-118">To retrieve a new object of a type that implements a general-purpose collection, you can call the [**winrt::single_threaded_vector**](/uwp/cpp-ref-for-winrt/single-threaded-vector) function template.</span></span> <span data-ttu-id="3db99-119">Das Objekt wird als ein [**IVector**](/uwp/api/windows.foundation.collections.ivector_t_)und ist die Schnittstelle, über die Funktionen und Eigenschaften des zurückgegebenen Objekts aufrufen.</span><span class="sxs-lookup"><span data-stu-id="3db99-119">The object is returned as an [**IVector**](/uwp/api/windows.foundation.collections.ivector_t_), and that's the interface via which you call the returned object's functions and properties.</span></span>

```cppwinrt
...
#include <winrt/Windows.Foundation.Collections.h>
#include <iostream>
using namespace winrt;
...
int main()
{
    init_apartment();

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

<span data-ttu-id="3db99-120">Wie im obigen Beispiel sehen können, nach dem Erstellen der Auflistung können Sie fügen Elemente sie durchlaufen und behandeln Sie das Objekt im Allgemeinen wie Windows-Runtime Auflistungsobjekt, das Sie von einer API erhalten haben.</span><span class="sxs-lookup"><span data-stu-id="3db99-120">As you can see in the code example above, after creating the collection you can append elements, iterate over them, and generally treat the object as you would any Windows Runtime collection object that you might have received from an API.</span></span> <span data-ttu-id="3db99-121">Benötigen Sie eine unveränderliche Ansicht der Auflistung können Sie [**IVector::GetView**](/uwp/api/windows.foundation.collections.ivector-1.getview)aufrufen, wie gezeigt.</span><span class="sxs-lookup"><span data-stu-id="3db99-121">If you need an immutable view over the collection, then you can call [**IVector::GetView**](/uwp/api/windows.foundation.collections.ivector-1.getview), as shown.</span></span> <span data-ttu-id="3db99-122">Das oben dargestellte Muster&mdash;erstellen und eine Auflistung&mdash;eignet sich für einfache Szenarien, wo Daten in oder aus einer API.</span><span class="sxs-lookup"><span data-stu-id="3db99-122">The pattern shown above&mdash;of creating and consuming a collection&mdash;is appropriate for simple scenarios where you want to pass data into, or get data out of, an API.</span></span> <span data-ttu-id="3db99-123">Können Sie ein **IVector**oder ein **IVectorView**übergeben, überall eine [**IIterable**](/uwp/api/windows.foundation.collections.iiterable_t_) erwartet.</span><span class="sxs-lookup"><span data-stu-id="3db99-123">You can pass an **IVector**, or an **IVectorView**, anywhere an [**IIterable**](/uwp/api/windows.foundation.collections.iiterable_t_) is expected.</span></span>

### <a name="general-purpose-collection-primed-from-data"></a><span data-ttu-id="3db99-124">Allgemeine Auflistung von Daten vorbereitet</span><span class="sxs-lookup"><span data-stu-id="3db99-124">General-purpose collection, primed from data</span></span>

<span data-ttu-id="3db99-125">Sie können auch durch Aufrufe auf **Anhängen** vermeiden, die im obigen Codebeispiel angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3db99-125">You can also avoid the overhead of the calls to **Append** that you can see in the code example above.</span></span> <span data-ttu-id="3db99-126">Sie haben bereits die Quelldaten und Sie vor der Erstellung von Windows-Runtime-Auflistungsobjekt füllen möchten.</span><span class="sxs-lookup"><span data-stu-id="3db99-126">You may already have the source data, or you may prefer to populate it in advance of creating the Windows Runtime collection object.</span></span> <span data-ttu-id="3db99-127">Gehen Sie dazu wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="3db99-127">Here's how to do that.</span></span>

```cppwinrt
auto coll1{ winrt::single_threaded_vector<int>({ 1,2,3 }) };

std::vector<int> values{ 1,2,3 };
auto coll2{ winrt::single_threaded_vector<int>(std::move(values)) };

for (auto const& el : coll2)
{
    std::cout << el << std::endl;
}
```

<span data-ttu-id="3db99-128">Übergeben Sie ein temporäres Objekt mit Daten aus dem **winrt::single_threaded_vector**mit `coll1`oben.</span><span class="sxs-lookup"><span data-stu-id="3db99-128">You can pass a temporary object containing your data to **winrt::single_threaded_vector**, as with `coll1`, above.</span></span> <span data-ttu-id="3db99-129">Oder eine **Std** (vorausgesetzt, Sie wird nicht sein Zugriff wieder) in der Funktion.</span><span class="sxs-lookup"><span data-stu-id="3db99-129">Or you can move a **std::vector** (assuming you won't be accessing it again) into the function.</span></span> <span data-ttu-id="3db99-130">In beiden Fällen sind Sie ein *r-Wert* an die Funktion übergeben.</span><span class="sxs-lookup"><span data-stu-id="3db99-130">In both cases, you're passing an *rvalue* into the function.</span></span> <span data-ttu-id="3db99-131">Das ermöglicht dem Compiler das effiziente und Kopieren der Daten zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="3db99-131">That enables the compiler to be efficient and to avoid copying the data.</span></span> <span data-ttu-id="3db99-132">Weitere Informationen zu *Rvalues*, finden Sie unter [wertkategorien und Verweise](cpp-value-categories.md).</span><span class="sxs-lookup"><span data-stu-id="3db99-132">If you want to know more about *rvalues*, see [Value categories, and references to them](cpp-value-categories.md).</span></span>

<span data-ttu-id="3db99-133">Wenn Sie ein Steuerelement XAML-Elemente der Auflistung binden möchten, können Sie.</span><span class="sxs-lookup"><span data-stu-id="3db99-133">If you want to bind a XAML items control to your collection, then you can.</span></span> <span data-ttu-id="3db99-134">Aber beachten, um die [**ItemsControl.ItemsSource**](/uwp/api/windows.ui.xaml.controls.itemscontrol.itemssource) -Eigenschaft richtig festlegen, Sie einen Wert des Typs **IVector** **IInspectable** (oder eines Typs Interoperabilität wie [**IBindableObservableVector müssen**](/uwp/api/windows.ui.xaml.interop.ibindableobservablevector)).</span><span class="sxs-lookup"><span data-stu-id="3db99-134">But be aware that to correctly set the [**ItemsControl.ItemsSource**](/uwp/api/windows.ui.xaml.controls.itemscontrol.itemssource) property, you need to set it to a value of type **IVector** of **IInspectable** (or of an interoperability type such as [**IBindableObservableVector**](/uwp/api/windows.ui.xaml.interop.ibindableobservablevector)).</span></span> <span data-ttu-id="3db99-135">Hier ist ein Codebeispiel, liefert ein für die Bindung geeignet und fügt ein Element.</span><span class="sxs-lookup"><span data-stu-id="3db99-135">Here's a code example that produces a collection of a type suitable for binding, and appends an element to it.</span></span>

```cppwinrt
auto bookSkus{ winrt::single_threaded_vector<Windows::Foundation::IInspectable>() };
bookSkus.Append(make<Bookstore::implementation::BookSku>(L"Moby Dick"));
```

<span data-ttu-id="3db99-136">Sie können eine Windows-Runtime Sammlung aus Daten erstellen und hier auf eine API ohne kopieren etwas weiterleiten.</span><span class="sxs-lookup"><span data-stu-id="3db99-136">You can create a Windows Runtime collection from data, and get a view on it ready to pass to an API, all without copying anything.</span></span>

```cppwinrt
std::vector<float> values{ 0.1f, 0.2f, 0.3f };
IVectorView<float> view{ winrt::single_threaded_vector(std::move(values)).GetView() };
```

<span data-ttu-id="3db99-137">In den obigen Beispielen werden die Auflistung *erstellen wir* ein Elementsteuerelement XAML gebunden. doch die Auflistung beobachten.</span><span class="sxs-lookup"><span data-stu-id="3db99-137">In the examples above, the collection we create *can* be bound to a XAML items control; but the collection isn't observable.</span></span>

### <a name="observable-collection"></a><span data-ttu-id="3db99-138">ObservableCollection</span><span class="sxs-lookup"><span data-stu-id="3db99-138">Observable collection</span></span>

<span data-ttu-id="3db99-139">Rufen Sie ein neues Objekt ein, das eine *Observable* -Auflistung implementiert rufen Sie die Funktionsvorlage [**winrt::single_threaded_observable_vector**](/uwp/cpp-ref-for-winrt/single-threaded-observable-vector) mit jedem beliebigen Elementtyp.</span><span class="sxs-lookup"><span data-stu-id="3db99-139">To retrieve a new object of a type that implements an *observable* collection, call the [**winrt::single_threaded_observable_vector**](/uwp/cpp-ref-for-winrt/single-threaded-observable-vector) function template with any element type.</span></span> <span data-ttu-id="3db99-140">Doch um eine ObservableCollection geeignet für die Bindung an ein Steuerelement XAML-Elemente, **IInspectable** als Elementtyp.</span><span class="sxs-lookup"><span data-stu-id="3db99-140">But to make an observable collection suitable for binding to a XAML items control, use **IInspectable** as the element type.</span></span>

<span data-ttu-id="3db99-141">Das Objekt wird als ein [**IObservableVector**](/uwp/api/windows.foundation.collections.iobservablevector_t_)und ist die Schnittstelle, über die Sie (oder das Steuerelement, an das es gebunden ist) Funktionen und Eigenschaften des zurückgegebenen Objekts aufrufen.</span><span class="sxs-lookup"><span data-stu-id="3db99-141">The object is returned as an [**IObservableVector**](/uwp/api/windows.foundation.collections.iobservablevector_t_), and that's the interface via which you (or the control to which it's bound) call the returned object's functions and properties.</span></span>

```cppwinrt
auto bookSkus{ winrt::single_threaded_observable_vector<Windows::Foundation::IInspectable>() };
```

<span data-ttu-id="3db99-142">Für Weitere Informationen und Codebeispiele zum Binden des Benutzers Benutzeroberflächen-Steuerelemente an eine ObservableCollection, siehe [XAML Elemente Steuerelemente, binden an C + / WinRT-Auflistung](binding-collection.md).</span><span class="sxs-lookup"><span data-stu-id="3db99-142">For more details, and code examples, about binding your user interface (UI) controls to an observable collection, see [XAML items controls; bind to a C++/WinRT collection](binding-collection.md).</span></span>

### <a name="associative-collection-map"></a><span data-ttu-id="3db99-143">Assoziative Auflistung (Karte)</span><span class="sxs-lookup"><span data-stu-id="3db99-143">Associative collection (map)</span></span>

<span data-ttu-id="3db99-144">Assoziative Auflistung Versionen der beiden Funktionen bereits gibt.</span><span class="sxs-lookup"><span data-stu-id="3db99-144">There are associative collection versions of the two functions that we've looked at.</span></span>

- <span data-ttu-id="3db99-145">Funktionsvorlage [**winrt::single_threaded_map**](/uwp/cpp-ref-for-winrt/single-threaded-map) gibt eine assoziative-Observable-Auflistung als ein [**IMap**](/uwp/api/windows.foundation.collections.imap_k_v_).</span><span class="sxs-lookup"><span data-stu-id="3db99-145">The [**winrt::single_threaded_map**](/uwp/cpp-ref-for-winrt/single-threaded-map) function template returns a non-observable associative collection as an [**IMap**](/uwp/api/windows.foundation.collections.imap_k_v_).</span></span>
- <span data-ttu-id="3db99-146">Die Funktionsvorlage [**winrt::single_threaded_observable_map**](/uwp/cpp-ref-for-winrt/single-threaded-observable-map) gibt eine wahrnehmbare assoziative als ein [**IObservableMap**](/uwp/api/windows.foundation.collections.iobservablemap_k_v_).</span><span class="sxs-lookup"><span data-stu-id="3db99-146">The [**winrt::single_threaded_observable_map**](/uwp/cpp-ref-for-winrt/single-threaded-observable-map) function template returns an observable associative collection as an [**IObservableMap**](/uwp/api/windows.foundation.collections.iobservablemap_k_v_).</span></span>

<span data-ttu-id="3db99-147">Sie können diese Sammlungen mit optional vorzubereiten, einen *r-Wert* von Typ **Std:: Map** oder **std::unordered_map**an die Funktion übergeben.</span><span class="sxs-lookup"><span data-stu-id="3db99-147">You can optionally prime these collections with data by passing to the function an *rvalue* of type **std::map** or **std::unordered_map**.</span></span>

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

### <a name="single-threaded"></a><span data-ttu-id="3db99-148">Singlethread-</span><span class="sxs-lookup"><span data-stu-id="3db99-148">Single-threaded</span></span>

<span data-ttu-id="3db99-149">Die "Single-threaded" in die Namen dieser Funktionen gibt an, dass sie Parallelität nicht&mdash;in anderen Worten, sie sind nicht threadsicher.</span><span class="sxs-lookup"><span data-stu-id="3db99-149">The "single-threaded" in the names of these functions indicates that they don't provide any concurrency&mdash;in other words, they're not thread-safe.</span></span> <span data-ttu-id="3db99-150">Erwähnung von Threads zusammenhängt Apartments, da alle agile Objekte, die von diesen Funktionen zurückgegeben werden (siehe [bewegliche Objekte in C / WinRT](agile-objects.md)).</span><span class="sxs-lookup"><span data-stu-id="3db99-150">The mention of threads is unrelated to apartments, because the objects returned from these functions are all agile (see [Agile objects in C++/WinRT](agile-objects.md)).</span></span> <span data-ttu-id="3db99-151">Es werden nur Objekte singlethreaded.</span><span class="sxs-lookup"><span data-stu-id="3db99-151">It's just that the objects are single-threaded.</span></span> <span data-ttu-id="3db99-152">Und typbasierte soll nur Daten ein oder anderen über die Application binary Interface (ABI) übergeben.</span><span class="sxs-lookup"><span data-stu-id="3db99-152">And that's entirely appropriate if you just want to pass data one way or the other across the application binary interface (ABI).</span></span>

## <a name="base-classes-for-collections"></a><span data-ttu-id="3db99-153">Basisklassen für Sammlungen</span><span class="sxs-lookup"><span data-stu-id="3db99-153">Base classes for collections</span></span>

<span data-ttu-id="3db99-154">Wenn Sie volle Flexibilität, eigene benutzerdefinierte Auflistung implementieren möchten, sollten Sie vermeiden, die schwer.</span><span class="sxs-lookup"><span data-stu-id="3db99-154">If, for complete flexibility, you want to implement your own custom collection, then you'll want to avoid doing that the hard way.</span></span> <span data-ttu-id="3db99-155">Beispielsweise sieht eine benutzerdefinierte Vektoransicht aussehen würde *ohne C + / WinRT Klassen*.</span><span class="sxs-lookup"><span data-stu-id="3db99-155">For example, this is what a custom vector view would look like *without the assistance of C++/WinRT's base classes*.</span></span>

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

<span data-ttu-id="3db99-156">Stattdessen ist es viel einfacher, [**winrt::vector_view_base**](/uwp/cpp-ref-for-winrt/vector-view-base) Struktur Vorlage benutzerdefinierten Vektoransicht abgeleitet und implementieren die **Get_container** -Funktion, um dem Container Daten verfügbar zu machen.</span><span class="sxs-lookup"><span data-stu-id="3db99-156">Instead, it's much easier to derive your custom vector view from the [**winrt::vector_view_base**](/uwp/cpp-ref-for-winrt/vector-view-base) struct template, and just implement the **get_container** function to expose the container holding your data.</span></span>

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

<span data-ttu-id="3db99-157">Zurückgegebene **Get_container** Container muss stellen die Schnittstelle **begin** und **End** , **winrt::vector_view_base** erwartet.</span><span class="sxs-lookup"><span data-stu-id="3db99-157">The container returned by **get_container** must provide the **begin** and **end** interface that **winrt::vector_view_base** expects.</span></span> <span data-ttu-id="3db99-158">Wie im Beispiel oben dargestellt bereitstellt **sind** .</span><span class="sxs-lookup"><span data-stu-id="3db99-158">As shown in the example above, **std::vector** provides that.</span></span> <span data-ttu-id="3db99-159">Aber können Sie alle Container, der den gleichen Vertrag, einschließlich benutzerdefinierter Containers erfüllt.</span><span class="sxs-lookup"><span data-stu-id="3db99-159">But you can return any container that fulfils the same contract, including your own custom container.</span></span>

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

<span data-ttu-id="3db99-160">Diese bilden die Basis Klassen, C + / WinRT zur bietet benutzerdefinierte Sammlungen implementieren.</span><span class="sxs-lookup"><span data-stu-id="3db99-160">These are the base classes that C++/WinRT provides to help you implement custom collections.</span></span>

### [<a name="winrtvectorviewbase"></a><span data-ttu-id="3db99-161">WinRT::vector_view_base</span><span class="sxs-lookup"><span data-stu-id="3db99-161">winrt::vector_view_base</span></span>](/uwp/cpp-ref-for-winrt/vector-view-base)

<span data-ttu-id="3db99-162">Codebeispiele anzeigen</span><span class="sxs-lookup"><span data-stu-id="3db99-162">See the code examples above.</span></span>

### [<a name="winrtvectorbase"></a><span data-ttu-id="3db99-163">WinRT::vector_base</span><span class="sxs-lookup"><span data-stu-id="3db99-163">winrt::vector_base</span></span>](/uwp/cpp-ref-for-winrt/vector-base)

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

### [<a name="winrtobservablevectorbase"></a><span data-ttu-id="3db99-164">WinRT::observable_vector_base</span><span class="sxs-lookup"><span data-stu-id="3db99-164">winrt::observable_vector_base</span></span>](/uwp/cpp-ref-for-winrt/observable-vector-base)

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

### [<a name="winrtmapviewbase"></a><span data-ttu-id="3db99-165">WinRT::map_view_base</span><span class="sxs-lookup"><span data-stu-id="3db99-165">winrt::map_view_base</span></span>](/uwp/cpp-ref-for-winrt/map-view-base)

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

### [<a name="winrtmapbase"></a><span data-ttu-id="3db99-166">WinRT::map_base</span><span class="sxs-lookup"><span data-stu-id="3db99-166">winrt::map_base</span></span>](/uwp/cpp-ref-for-winrt/map-base)

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

### [<a name="winrtobservablemapbase"></a><span data-ttu-id="3db99-167">WinRT::observable_map_base</span><span class="sxs-lookup"><span data-stu-id="3db99-167">winrt::observable_map_base</span></span>](/uwp/cpp-ref-for-winrt/observable-map-base)

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

## <a name="important-apis"></a><span data-ttu-id="3db99-168">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="3db99-168">Important APIs</span></span>
* [<span data-ttu-id="3db99-169">ItemsControl.ItemsSource-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="3db99-169">ItemsControl.ItemsSource property</span></span>](/uwp/api/windows.ui.xaml.controls.itemscontrol.itemssource)
* [<span data-ttu-id="3db99-170">IObservableVector-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="3db99-170">IObservableVector interface</span></span>](/uwp/api/windows.foundation.collections.iobservablevector_t_)
* [<span data-ttu-id="3db99-171">IVector-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="3db99-171">IVector interface</span></span>](/uwp/api/windows.foundation.collections.ivector_t_)
* [<span data-ttu-id="3db99-172">WinRT::map_base Struktur Vorlage</span><span class="sxs-lookup"><span data-stu-id="3db99-172">winrt::map_base struct template</span></span>](/uwp/cpp-ref-for-winrt/map-base)
* [<span data-ttu-id="3db99-173">WinRT::map_view_base Struktur Vorlage</span><span class="sxs-lookup"><span data-stu-id="3db99-173">winrt::map_view_base struct template</span></span>](/uwp/cpp-ref-for-winrt/map-view-base)
* [<span data-ttu-id="3db99-174">WinRT::observable_map_base Struktur Vorlage</span><span class="sxs-lookup"><span data-stu-id="3db99-174">winrt::observable_map_base struct template</span></span>](/uwp/cpp-ref-for-winrt/observable-map-base)
* [<span data-ttu-id="3db99-175">WinRT::observable_vector_base Struktur Vorlage</span><span class="sxs-lookup"><span data-stu-id="3db99-175">winrt::observable_vector_base struct template</span></span>](/uwp/cpp-ref-for-winrt/observable-vector-base)
* [<span data-ttu-id="3db99-176">WinRT::single_threaded_observable_map Funktionsvorlage</span><span class="sxs-lookup"><span data-stu-id="3db99-176">winrt::single_threaded_observable_map function template</span></span>](/uwp/cpp-ref-for-winrt/single-threaded-observable-map)
* [<span data-ttu-id="3db99-177">WinRT::single_threaded_map Funktionsvorlage</span><span class="sxs-lookup"><span data-stu-id="3db99-177">winrt::single_threaded_map function template</span></span>](/uwp/cpp-ref-for-winrt/single-threaded-map)
* [<span data-ttu-id="3db99-178">WinRT::single_threaded_observable_vector Funktionsvorlage</span><span class="sxs-lookup"><span data-stu-id="3db99-178">winrt::single_threaded_observable_vector function template</span></span>](/uwp/cpp-ref-for-winrt/single-threaded-observable-vector)
* [<span data-ttu-id="3db99-179">WinRT::single_threaded_vector Funktionsvorlage</span><span class="sxs-lookup"><span data-stu-id="3db99-179">winrt::single_threaded_vector function template</span></span>](/uwp/cpp-ref-for-winrt/single-threaded-vector)
* [<span data-ttu-id="3db99-180">WinRT::vector_base Struktur Vorlage</span><span class="sxs-lookup"><span data-stu-id="3db99-180">winrt::vector_base struct template</span></span>](/uwp/cpp-ref-for-winrt/vector-base)
* [<span data-ttu-id="3db99-181">WinRT::vector_view_base Struktur Vorlage</span><span class="sxs-lookup"><span data-stu-id="3db99-181">winrt::vector_view_base struct template</span></span>](/uwp/cpp-ref-for-winrt/vector-view-base)

## <a name="related-topics"></a><span data-ttu-id="3db99-182">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="3db99-182">Related topics</span></span>
* [<span data-ttu-id="3db99-183">Wertkategorien und Verweise</span><span class="sxs-lookup"><span data-stu-id="3db99-183">Value categories, and references to them</span></span>](cpp-value-categories.md)
* [<span data-ttu-id="3db99-184">XAML-Items-Steuerelemente; Binden an eine C++/WinRT-Collection</span><span class="sxs-lookup"><span data-stu-id="3db99-184">XAML items controls; bind to a C++/WinRT collection</span></span>](binding-collection.md)
