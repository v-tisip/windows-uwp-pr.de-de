---
author: stevewhims
description: C++ / WinRT stellt Funktionen und Basisklassen, die Sie speichern viel Zeit und Mühe beim Implementieren und/oder Sammlungen übergeben werden soll.
title: Sammlungen mit C++ / WinRT
ms.author: stwhi
ms.date: 08/24/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, standard, c++, Cpp, Winrt, Projektion, Sammlung
ms.localizationpriority: medium
ms.openlocfilehash: 5495649a6b7fad633e24e244aa3f6efbcc05e441
ms.sourcegitcommit: 53ba430930ecec8ea10c95b390fe6e654fe363e1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "3421098"
---
# <a name="collections-with-cwinrtwindowsuwpcpp-and-winrt-apisintro-to-using-cpp-with-winrt"></a><span data-ttu-id="313e5-104">Sammlungen mit [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)</span><span class="sxs-lookup"><span data-stu-id="313e5-104">Collections with [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)</span></span>

> [!NOTE]
> **<span data-ttu-id="313e5-105">Einige Informationen beziehen sich auf die Vorabversion, die vor der kommerziellen Freigabe möglicherweise wesentlichen Änderungen unterliegt.</span><span class="sxs-lookup"><span data-stu-id="313e5-105">Some information relates to pre-released product which may be substantially modified before it’s commercially released.</span></span> <span data-ttu-id="313e5-106">Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.</span><span class="sxs-lookup"><span data-stu-id="313e5-106">Microsoft makes no warranties, express or implied, with respect to the information provided here.</span></span>**

<span data-ttu-id="313e5-107">Intern verfügt über eine Windows-Runtime-Collection auf viele komplizierte bewegliche Teile aus.</span><span class="sxs-lookup"><span data-stu-id="313e5-107">Internally, a Windows Runtime collection has a lot of complicated moving parts.</span></span> <span data-ttu-id="313e5-108">Aber wenn Sie ein Objekt Sammlung an eine Windows-Runtime-Funktion übergeben oder Ihre eigenen Sammlungseigenschaften und Sammlungstypen implementieren möchten, Funktionen und Basisklassen in C++ stehen / WinRT, damit Sie unterstützen.</span><span class="sxs-lookup"><span data-stu-id="313e5-108">But when you want to pass a collection object to a Windows Runtime function, or to implement your own collection properties and collection types, there are functions and base classes in C++/WinRT to support you.</span></span> <span data-ttu-id="313e5-109">Diese Features vereinfachen Sie Ihre Hände und viel Aufwand in Zeit und Mühe sparen.</span><span class="sxs-lookup"><span data-stu-id="313e5-109">These features take the complexity out of your hands, and save you a lot of overhead in time and effort.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="313e5-110">In diesem Thema beschriebenen Features sind verfügbar, wenn Sie die [Windows 10 SDK Preview Build 17661](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK)installiert haben, oder höher.</span><span class="sxs-lookup"><span data-stu-id="313e5-110">The features described in this topic are available if you've installed the [Windows 10 SDK Preview Build 17661](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK), or later.</span></span>

<span data-ttu-id="313e5-111">[**IVector**](/uwp/api/windows.foundation.collections.ivector_t_) ist die Windows-Runtime-Schnittstelle, die durch wahlfreiem Zugriff eine Sammlung von Elementen implementiert.</span><span class="sxs-lookup"><span data-stu-id="313e5-111">[**IVector**](/uwp/api/windows.foundation.collections.ivector_t_) is the Windows Runtime interface implemented by any random-access collection of elements.</span></span> <span data-ttu-id="313e5-112">Würden Sie **IVector** selbst implementieren, müssen Sie auch [**IIterable**](/uwp/api/windows.foundation.collections.iiterable_t_), [**IVectorView**](/uwp/api/windows.foundation.collections.ivectorview_t_)und [**IIterator**](/uwp/api/windows.foundation.collections.iiterator_t_)implementieren.</span><span class="sxs-lookup"><span data-stu-id="313e5-112">If you were to implement **IVector** yourself, you'd also need to implement [**IIterable**](/uwp/api/windows.foundation.collections.iiterable_t_), [**IVectorView**](/uwp/api/windows.foundation.collections.ivectorview_t_), and [**IIterator**](/uwp/api/windows.foundation.collections.iiterator_t_).</span></span> <span data-ttu-id="313e5-113">Auch wenn Sie eine benutzerdefinierte Auflistung *müssen* eingeben, wird, die viel Arbeit.</span><span class="sxs-lookup"><span data-stu-id="313e5-113">Even if you *need* a custom collection type, that's a lot of work.</span></span> <span data-ttu-id="313e5-114">Wenn Sie Daten in eine **Std:: Vector** (oder eine **Std:: Map**oder eine **std::unordered_map**) haben und alles, was Sie tun möchten, die an einem Windows-Runtime-API übergeben, möchten dann aber würde, damit kein dieser Ebene der Arbeit, wenn möglich.</span><span class="sxs-lookup"><span data-stu-id="313e5-114">But if you have data in a **std::vector** (or a **std::map**, or a **std::unordered_map**) and all you want to do is pass that to a Windows Runtime API, then you'd want to avoid doing that level of work, if possible.</span></span> <span data-ttu-id="313e5-115">Und es *ist* möglich, da C++ / WinRT können Sie Sammlungen effizient und mit wenig Aufwand zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="313e5-115">And avoiding it *is* possible, because C++/WinRT helps you to create collections efficiently and with little effort.</span></span>

## <a name="helper-functions-for-collections"></a><span data-ttu-id="313e5-116">Hilfsfunktionen für Sammlungen</span><span class="sxs-lookup"><span data-stu-id="313e5-116">Helper functions for collections</span></span>

### <a name="general-purpose-collection-empty"></a><span data-ttu-id="313e5-117">Allgemeine Auflistung, leer</span><span class="sxs-lookup"><span data-stu-id="313e5-117">General-purpose collection, empty</span></span>

<span data-ttu-id="313e5-118">Um ein neues Objekt eines Typs abzurufen, die eine allgemeine Auflistung implementiert, können Sie die Funktionsvorlage [**winrt::single_threaded_vector**](/uwp/cpp-ref-for-winrt/single-threaded-vector) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="313e5-118">To retrieve a new object of a type that implements a general-purpose collection, you can call the [**winrt::single_threaded_vector**](/uwp/cpp-ref-for-winrt/single-threaded-vector) function template.</span></span> <span data-ttu-id="313e5-119">Das Objekt wird als ein [**IVector**](/uwp/api/windows.foundation.collections.ivector_t_)zurückgegeben, und dies ist die Schnittstelle, die über die Funktionen und Eigenschaften des zurückgegebenen Objekts aufrufen.</span><span class="sxs-lookup"><span data-stu-id="313e5-119">The object is returned as an [**IVector**](/uwp/api/windows.foundation.collections.ivector_t_), and that's the interface via which you call the returned object's functions and properties.</span></span>

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

<span data-ttu-id="313e5-120">Wie im obigen Codebeispiel sehen, nach dem Erstellen der Auflistung können Sie Elemente anfügen, durchlaufen sie und behandeln Sie das Objekt in der Regel, wie Sie alle Windows-Runtime-Collection-Objekt, die Sie von einer API erhalten haben.</span><span class="sxs-lookup"><span data-stu-id="313e5-120">As you can see in the code example above, after creating the collection you can append elements, iterate over them, and generally treat the object as you would any Windows Runtime collection object that you might have received from an API.</span></span> <span data-ttu-id="313e5-121">Wenn Sie eine unveränderliche Ansicht über die Auflistung benötigen, können Sie wie gezeigt [**IVector::GetView**](/uwp/api/windows.foundation.collections.ivector-1.getview), aufrufen.</span><span class="sxs-lookup"><span data-stu-id="313e5-121">If you need an immutable view over the collection, then you can call [**IVector::GetView**](/uwp/api/windows.foundation.collections.ivector-1.getview), as shown.</span></span> <span data-ttu-id="313e5-122">Das oben gezeigte Muster&mdash;der Erstellung und Nutzung von einer Sammlungs&mdash;eignet sich für einfache Fälle, in denen Sie übergeben Sie Daten in oder Abrufen von Daten aus einer API.</span><span class="sxs-lookup"><span data-stu-id="313e5-122">The pattern shown above&mdash;of creating and consuming a collection&mdash;is appropriate for simple scenarios where you want to pass data into, or get data out of, an API.</span></span>

### <a name="general-purpose-collection-primed-from-data"></a><span data-ttu-id="313e5-123">Allgemeine Sammlung von Daten vorbereitet</span><span class="sxs-lookup"><span data-stu-id="313e5-123">General-purpose collection, primed from data</span></span>

<span data-ttu-id="313e5-124">Sie können auch den Aufwand für die Aufrufe von **Append** vermeiden, die Sie im obigen Codebeispiel sehen können.</span><span class="sxs-lookup"><span data-stu-id="313e5-124">You can also avoid the overhead of the calls to **Append** that you can see in the code example above.</span></span> <span data-ttu-id="313e5-125">Möglicherweise haben Sie bereits die Quelldaten, oder Sie möchten es vor dem Erstellen des Windows-Runtime-Collection-Objekts zu füllen.</span><span class="sxs-lookup"><span data-stu-id="313e5-125">You may already have the source data, or you may prefer to populate it in advance of creating the Windows Runtime collection object.</span></span> <span data-ttu-id="313e5-126">Gehen Sie dazu wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="313e5-126">Here's how to do that.</span></span>

```cppwinrt
auto coll1{ winrt::single_threaded_vector<int>({ 1,2,3 }) };

std::vector<int> values{ 1,2,3 };
auto coll2{ winrt::single_threaded_vector<int>(std::move(values)) };

for (auto const& el : coll2)
{
    std::cout << el << std::endl;
}
```

<span data-ttu-id="313e5-127">Sie können ein temporäres Objekt, enthält Ihre Daten **winrt::single_threaded_vector**, übergeben wie bei `coll1`oben.</span><span class="sxs-lookup"><span data-stu-id="313e5-127">You can pass a temporary object containing your data to **winrt::single_threaded_vector**, as with `coll1`, above.</span></span> <span data-ttu-id="313e5-128">Oder Sie können eine **Std:: Vector** (vorausgesetzt, Sie wird nicht werden auf diese zugreifenden erneut) verschieben in der Funktion.</span><span class="sxs-lookup"><span data-stu-id="313e5-128">Or you can move a **std::vector** (assuming you won't be accessing it again) into the function.</span></span> <span data-ttu-id="313e5-129">In beiden Fällen können Sie einen *r-Wert* an die Funktion übergeben.</span><span class="sxs-lookup"><span data-stu-id="313e5-129">In both cases, you're passing an *rvalue* into the function.</span></span> <span data-ttu-id="313e5-130">Dadurch wird den Compiler effizient und vermeiden, kopieren die Daten ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="313e5-130">That enables the compiler to be efficient and to avoid copying the data.</span></span> <span data-ttu-id="313e5-131">Wenn Sie mehr über *Rvalues*erfahren möchten, finden Sie unter [Wert Kategorien, und Verweise auf diese](cpp-value-categories.md).</span><span class="sxs-lookup"><span data-stu-id="313e5-131">If you want to know more about *rvalues*, see [Value categories, and references to them](cpp-value-categories.md).</span></span>

<span data-ttu-id="313e5-132">Wenn Sie ein XAML-Items-Steuerelement an eine Sammlung binden möchten, können Sie.</span><span class="sxs-lookup"><span data-stu-id="313e5-132">If you want to bind a XAML items control to your collection, then you can.</span></span> <span data-ttu-id="313e5-133">Beachten Sie jedoch, um die Eigenschaft [**ItemsControl.ItemsSource**](/uwp/api/windows.ui.xaml.controls.itemscontrol.itemssource) richtig festzulegen, Sie festlegen, dass ein Wert vom Typ **IVector** **IInspectable** (oder ein Typ Interoperabilität, z. B. [**IBindableObservableVector müssen**](/uwp/api/windows.ui.xaml.interop.ibindableobservablevector)).</span><span class="sxs-lookup"><span data-stu-id="313e5-133">But be aware that to correctly set the [**ItemsControl.ItemsSource**](/uwp/api/windows.ui.xaml.controls.itemscontrol.itemssource) property, you need to set it to a value of type **IVector** of **IInspectable** (or of an interoperability type such as [**IBindableObservableVector**](/uwp/api/windows.ui.xaml.interop.ibindableobservablevector)).</span></span> <span data-ttu-id="313e5-134">Hier ist ein Codebeispiel, das eine Sammlung von einem Typ, der für die Bindung geeignet erzeugt Fügt ein Element hinzu.</span><span class="sxs-lookup"><span data-stu-id="313e5-134">Here's a code example that produces a collection of a type suitable for binding, and appends an element to it.</span></span>

```cppwinrt
auto bookSkus{ winrt::single_threaded_vector<Windows::Foundation::IInspectable>() };
bookSkus.Append(make<Bookstore::implementation::BookSku>(L"Moby Dick"));
```

<span data-ttu-id="313e5-135">Die Sammlung oben *können* werden an ein XAML-Items-Steuerelement gebunden; aber die Sammlung nicht feststellbar.</span><span class="sxs-lookup"><span data-stu-id="313e5-135">The collection above *can* be bound to a XAML items control; but the collection isn't observable.</span></span>

### <a name="observable-collection"></a><span data-ttu-id="313e5-136">Observable-collection</span><span class="sxs-lookup"><span data-stu-id="313e5-136">Observable collection</span></span>

<span data-ttu-id="313e5-137">Ein neues Objekt eines Typs abrufen, die eine *Observable* -Collection implementiert, rufen Sie die Funktionsvorlage [**winrt::single_threaded_observable_vector**](/uwp/cpp-ref-for-winrt/single-threaded-observable-vector) mit jedem beliebigen Elementtyp.</span><span class="sxs-lookup"><span data-stu-id="313e5-137">To retrieve a new object of a type that implements an *observable* collection, call the [**winrt::single_threaded_observable_vector**](/uwp/cpp-ref-for-winrt/single-threaded-observable-vector) function template with any element type.</span></span> <span data-ttu-id="313e5-138">Jedoch um eine Observable-Collection geeignet für die Bindung an ein XAML-Items-Steuerelement können, verwenden Sie **IInspectable** als Typ des Elements.</span><span class="sxs-lookup"><span data-stu-id="313e5-138">But to make an observable collection suitable for binding to a XAML items control, use **IInspectable** as the element type.</span></span>

<span data-ttu-id="313e5-139">Das Objekt wird als eine [**IObservableVector**](/uwp/api/windows.foundation.collections.iobservablevector_t_)zurückgegeben, und dies ist die Schnittstelle, die über die Sie (oder das Steuerelement an das sie gebunden ist) des zurückgegebenen Objekts Funktionen und Eigenschaften aufrufen.</span><span class="sxs-lookup"><span data-stu-id="313e5-139">The object is returned as an [**IObservableVector**](/uwp/api/windows.foundation.collections.iobservablevector_t_), and that's the interface via which you (or the control to which it's bound) call the returned object's functions and properties.</span></span>

```cppwinrt
auto bookSkus{ winrt::single_threaded_observable_vector<Windows::Foundation::IInspectable>() };
```

<span data-ttu-id="313e5-140">Weitere Informationen und Codebeispiele zum Binden des Benutzers Benutzeroberfläche (UI) steuert, eine Observable-Collection, finden Sie unter [XAML-items-Steuerelemente; binden an eine C++ / WinRT-Collection](binding-collection.md).</span><span class="sxs-lookup"><span data-stu-id="313e5-140">For more details, and code examples, about binding your user interface (UI) controls to an observable collection, see [XAML items controls; bind to a C++/WinRT collection](binding-collection.md).</span></span>

### <a name="associative-collection-map"></a><span data-ttu-id="313e5-141">Assoziative Sammlung (Map)</span><span class="sxs-lookup"><span data-stu-id="313e5-141">Associative collection (map)</span></span>

<span data-ttu-id="313e5-142">Es gibt Versionen der beiden Funktionen, denen bereits assoziative Sammlung.</span><span class="sxs-lookup"><span data-stu-id="313e5-142">There are associative collection versions of the two functions that we've looked at.</span></span>

- <span data-ttu-id="313e5-143">Die Funktionsvorlage [**winrt::single_threaded_map**](/uwp/cpp-ref-for-winrt/single-threaded-map) wird als eine [**IMap**](/uwp/api/windows.foundation.collections.imap_k_v_)eine assoziative nicht feststellbare Sammlung zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="313e5-143">The [**winrt::single_threaded_map**](/uwp/cpp-ref-for-winrt/single-threaded-map) function template returns a non-observable associative collection as an [**IMap**](/uwp/api/windows.foundation.collections.imap_k_v_).</span></span>
- <span data-ttu-id="313e5-144">Die Funktionsvorlage [**winrt::single_threaded_observable_map**](/uwp/cpp-ref-for-winrt/single-threaded-observable-map) gibt eine assoziative Observable-Collection als eine [**IObservableMap**](/uwp/api/windows.foundation.collections.iobservablemap_k_v_)zurück.</span><span class="sxs-lookup"><span data-stu-id="313e5-144">The [**winrt::single_threaded_observable_map**](/uwp/cpp-ref-for-winrt/single-threaded-observable-map) function template returns an observable associative collection as an [**IObservableMap**](/uwp/api/windows.foundation.collections.iobservablemap_k_v_).</span></span>

<span data-ttu-id="313e5-145">Sie können optional diese Sammlungen mit Daten initialisieren, indem Sie einen *r-Wert* der Typ **Std:: Map** oder **std::unordered_map**an die Funktion übergeben.</span><span class="sxs-lookup"><span data-stu-id="313e5-145">You can optionally prime these collections with data by passing to the function an *rvalue* of type **std::map** or **std::unordered_map**.</span></span>

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

### <a name="single-threaded"></a><span data-ttu-id="313e5-146">Singlethread-</span><span class="sxs-lookup"><span data-stu-id="313e5-146">Single-threaded</span></span>

<span data-ttu-id="313e5-147">Die "Single-threaded" in den Namen dieser Funktionen gibt an, dass sie alle Parallelität nicht&mdash;mit anderen Worten: sie sind nicht threadsicher.</span><span class="sxs-lookup"><span data-stu-id="313e5-147">The "single-threaded" in the names of these functions indicates that they don't provide any concurrency&mdash;in other words, they're not thread-safe.</span></span> <span data-ttu-id="313e5-148">Die Erwähnen Sie von Threads ist nicht im Zusammenhang mit Apartments, da die Objekte, die von diesen Funktionen zurückgegeben alle agil sind (siehe [Agile Objekte in C++ / WinRT](agile-objects.md)).</span><span class="sxs-lookup"><span data-stu-id="313e5-148">The mention of threads is unrelated to apartments, because the objects returned from these functions are all agile (see [Agile objects in C++/WinRT](agile-objects.md)).</span></span> <span data-ttu-id="313e5-149">Es ist einfach, dass die Objekte Singlethread-sind.</span><span class="sxs-lookup"><span data-stu-id="313e5-149">It's just that the objects are single-threaded.</span></span> <span data-ttu-id="313e5-150">Und das ist vollständig geeignet, wenn nur Daten eine Möglichkeit oder andere über die Application binary Interface (ABI) übergeben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="313e5-150">And that's entirely appropriate if you just want to pass data one way or the other across the application binary interface (ABI).</span></span>

## <a name="base-classes-for-collections"></a><span data-ttu-id="313e5-151">Basisklassen für Sammlungen</span><span class="sxs-lookup"><span data-stu-id="313e5-151">Base classes for collections</span></span>

<span data-ttu-id="313e5-152">Wenn Sie Flexibilität, eine eigene benutzerdefinierte Auflistung implementieren möchten, sollten Sie dabei, die schwer zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="313e5-152">If, for complete flexibility, you want to implement your own custom collection, then you'll want to avoid doing that the hard way.</span></span> <span data-ttu-id="313e5-153">Angenommen, dies ist eine benutzerdefinierte Vektoransicht aussehen würde *ohne Unterstützung von C++ / WinRT-Basisklassen*.</span><span class="sxs-lookup"><span data-stu-id="313e5-153">For example, this is what a custom vector view would look like *without the assistance of C++/WinRT's base classes*.</span></span>

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

<span data-ttu-id="313e5-154">Stattdessen ist es sehr viel einfacher, leiten Ihre benutzerdefinierte Vektoransicht aus der strukturvorlage [**winrt::vector_view_base**](/uwp/cpp-ref-for-winrt/vector-view-base) , und implementieren Sie einfach die **Get_container** -Funktion, um dem Container, Ihre Daten verfügbar zu machen.</span><span class="sxs-lookup"><span data-stu-id="313e5-154">Instead, it's much easier to derive your custom vector view from the [**winrt::vector_view_base**](/uwp/cpp-ref-for-winrt/vector-view-base) struct template, and just implement the **get_container** function to expose the container holding your data.</span></span>

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

<span data-ttu-id="313e5-155">Der Container **Get_container** zurückgegebene muss stellen die **begin** und **End** -Schnittstelle die **winrt::vector_view_base** erwartet.</span><span class="sxs-lookup"><span data-stu-id="313e5-155">The container returned by **get_container** must provide the **begin** and **end** interface that **winrt::vector_view_base** expects.</span></span> <span data-ttu-id="313e5-156">Wie im obigen Beispiel gezeigt, bereitstellt **Std:: Vector** .</span><span class="sxs-lookup"><span data-stu-id="313e5-156">As shown in the example above, **std::vector** provides that.</span></span> <span data-ttu-id="313e5-157">Aber Sie können alle Container, die den gleichen Vertrag, einschließlich Ihrer eigenen benutzerdefinierten Container erfüllt zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="313e5-157">But you can return any container that fulfils the same contract, including your own custom container.</span></span>

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

<span data-ttu-id="313e5-158">Hierbei handelt es sich um die Basis Klassen, die C++ / WinRT zur bietet benutzerdefinierte Sammlungen zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="313e5-158">These are the base classes that C++/WinRT provides to help you implement custom collections.</span></span>

### [<a name="winrtvectorviewbase"></a><span data-ttu-id="313e5-159">WinRT::vector_view_base</span><span class="sxs-lookup"><span data-stu-id="313e5-159">winrt::vector_view_base</span></span>](/uwp/cpp-ref-for-winrt/vector-view-base)

<span data-ttu-id="313e5-160">Siehe obigen Codebeispiele.</span><span class="sxs-lookup"><span data-stu-id="313e5-160">See the code examples above.</span></span>

### [<a name="winrtvectorbase"></a><span data-ttu-id="313e5-161">WinRT::vector_base</span><span class="sxs-lookup"><span data-stu-id="313e5-161">winrt::vector_base</span></span>](/uwp/cpp-ref-for-winrt/vector-base)

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

### [<a name="winrtobservablevectorbase"></a><span data-ttu-id="313e5-162">WinRT::observable_vector_base</span><span class="sxs-lookup"><span data-stu-id="313e5-162">winrt::observable_vector_base</span></span>](/uwp/cpp-ref-for-winrt/observable-vector-base)

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

### [<a name="winrtmapviewbase"></a><span data-ttu-id="313e5-163">WinRT::map_view_base</span><span class="sxs-lookup"><span data-stu-id="313e5-163">winrt::map_view_base</span></span>](/uwp/cpp-ref-for-winrt/map-view-base)

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

### [<a name="winrtmapbase"></a><span data-ttu-id="313e5-164">WinRT::map_base</span><span class="sxs-lookup"><span data-stu-id="313e5-164">winrt::map_base</span></span>](/uwp/cpp-ref-for-winrt/map-base)

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

### [<a name="winrtobservablemapbase"></a><span data-ttu-id="313e5-165">WinRT::observable_map_base</span><span class="sxs-lookup"><span data-stu-id="313e5-165">winrt::observable_map_base</span></span>](/uwp/cpp-ref-for-winrt/observable-map-base)

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

## <a name="important-apis"></a><span data-ttu-id="313e5-166">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="313e5-166">Important APIs</span></span>
* [<span data-ttu-id="313e5-167">ItemsControl.ItemsSource</span><span class="sxs-lookup"><span data-stu-id="313e5-167">ItemsControl.ItemsSource</span></span>](/uwp/api/windows.ui.xaml.controls.itemscontrol.itemssource)
* [<span data-ttu-id="313e5-168">IObservableVector</span><span class="sxs-lookup"><span data-stu-id="313e5-168">IObservableVector</span></span>](/uwp/api/windows.foundation.collections.iobservablevector_t_)
* [<span data-ttu-id="313e5-169">IVector</span><span class="sxs-lookup"><span data-stu-id="313e5-169">IVector</span></span>](/uwp/api/windows.foundation.collections.ivector_t_)
* [<span data-ttu-id="313e5-170">WinRT::map_base</span><span class="sxs-lookup"><span data-stu-id="313e5-170">winrt::map_base</span></span>](/uwp/cpp-ref-for-winrt/map-base)
* [<span data-ttu-id="313e5-171">WinRT::map_view_base</span><span class="sxs-lookup"><span data-stu-id="313e5-171">winrt::map_view_base</span></span>](/uwp/cpp-ref-for-winrt/map-view-base)
* [<span data-ttu-id="313e5-172">WinRT::observable_map_base</span><span class="sxs-lookup"><span data-stu-id="313e5-172">winrt::observable_map_base</span></span>](/uwp/cpp-ref-for-winrt/observable-map-base)
* [<span data-ttu-id="313e5-173">WinRT::observable_vector_base</span><span class="sxs-lookup"><span data-stu-id="313e5-173">winrt::observable_vector_base</span></span>](/uwp/cpp-ref-for-winrt/observable-vector-base)
* [<span data-ttu-id="313e5-174">WinRT::single_threaded_observable_map</span><span class="sxs-lookup"><span data-stu-id="313e5-174">winrt::single_threaded_observable_map</span></span>](/uwp/cpp-ref-for-winrt/single-threaded-observable-map)
* [<span data-ttu-id="313e5-175">WinRT::single_threaded_map</span><span class="sxs-lookup"><span data-stu-id="313e5-175">winrt::single_threaded_map</span></span>](/uwp/cpp-ref-for-winrt/single-threaded-map)
* [<span data-ttu-id="313e5-176">WinRT::single_threaded_observable_vector</span><span class="sxs-lookup"><span data-stu-id="313e5-176">winrt::single_threaded_observable_vector</span></span>](/uwp/cpp-ref-for-winrt/single-threaded-observable-vector)
* [<span data-ttu-id="313e5-177">WinRT::single_threaded_vector</span><span class="sxs-lookup"><span data-stu-id="313e5-177">winrt::single_threaded_vector</span></span>](/uwp/cpp-ref-for-winrt/single-threaded-vector)
* [<span data-ttu-id="313e5-178">WinRT::vector_base</span><span class="sxs-lookup"><span data-stu-id="313e5-178">winrt::vector_base</span></span>](/uwp/cpp-ref-for-winrt/vector-base)
* [<span data-ttu-id="313e5-179">WinRT::vector_view_base</span><span class="sxs-lookup"><span data-stu-id="313e5-179">winrt::vector_view_base</span></span>](/uwp/cpp-ref-for-winrt/vector-view-base)

## <a name="related-topics"></a><span data-ttu-id="313e5-180">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="313e5-180">Related topics</span></span>
* [<span data-ttu-id="313e5-181">Wert Kategorien und Verweise auf diese</span><span class="sxs-lookup"><span data-stu-id="313e5-181">Value categories, and references to them</span></span>](cpp-value-categories.md)
* [<span data-ttu-id="313e5-182">XAML-Items-Steuerelemente; Binden an eine C++/WinRT-Collection</span><span class="sxs-lookup"><span data-stu-id="313e5-182">XAML items controls; bind to a C++/WinRT collection</span></span>](binding-collection.md)
