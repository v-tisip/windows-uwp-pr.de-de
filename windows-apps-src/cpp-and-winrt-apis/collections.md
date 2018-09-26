---
author: stevewhims
description: C++ / WinRT stellt Funktionen und Basisklassen, die Sie speichern und viel Zeit und Mühe beim Implementieren und/oder Sammlungen übergeben werden soll.
title: Sammlungen mit C++ / WinRT
ms.author: stwhi
ms.date: 09/21/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, standard, c++, Cpp, Winrt, Projektion, Sammlung
ms.localizationpriority: medium
ms.openlocfilehash: c7ac3635a96b8dd3d757f25da1b826ea318c1ad4
ms.sourcegitcommit: e4f3e1b2d08a02b9920e78e802234e5b674e7223
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/26/2018
ms.locfileid: "4211148"
---
# <a name="collections-with-cwinrtwindowsuwpcpp-and-winrt-apisintro-to-using-cpp-with-winrt"></a>Sammlungen mit [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)

> [!NOTE]
> **Einige Informationen beziehen sich auf die Vorabversion, die vor der kommerziellen Freigabe möglicherweise wesentlichen Änderungen unterliegt. Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.**

Intern verfügt über eine Windows-Runtime-Sammlung ein Großteil komplizierte bewegliche Teile. Aber wenn Sie ein Objekt Sammlung an eine Windows-Runtime-Funktion übergeben oder Ihre eigenen Sammlungseigenschaften und Sammlungstypen implementieren möchten, Funktionen und Basisklassen in C++ stehen / WinRT, damit Sie unterstützen. Diese Features die Komplexität der Hand und Aufwand viel Zeit und Mühe sparen.

> [!IMPORTANT]
> Die in diesem Thema beschriebenen Funktionen sind verfügbar, wenn Sie die [Windows 10 SDK Preview Build 17661](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK)installiert haben, oder höher.

[**IVector**](/uwp/api/windows.foundation.collections.ivector_t_) ist die Windows-Runtime-Schnittstelle, die von direktem Zugriff eine Sammlung von Elementen implementiert. Würden Sie **IVector** selbst implementieren, müssen Sie auch [**IIterable**](/uwp/api/windows.foundation.collections.iiterable_t_), [**IVectorView**](/uwp/api/windows.foundation.collections.ivectorview_t_)und [**IIterator**](/uwp/api/windows.foundation.collections.iiterator_t_)implementieren. Auch wenn Sie *müssen* eine benutzerdefinierte Auflistung eingeben, wird, die eine Menge Arbeit. Wenn Sie Daten in eine **Std:: Vector** (oder eine **Std:: Map**oder eine **std::unordered_map**) und alles, was Sie tun möchten, die an einer Windows-Runtime-API übergeben, möchten dann aber würde, damit kein dieser Ebene der Arbeit, wenn möglich. Und es *ist* möglich, da C++ / WinRT können Sie zum Erstellen von Sammlungen effizient und mit minimalem Aufwand.

## <a name="helper-functions-for-collections"></a>Hilfsfunktionen für Sammlungen

### <a name="general-purpose-collection-empty"></a>Allgemeine Auflistung, leer

In diesem Abschnitt behandelt das Szenario, in denen Sie eine Sammlung erstellen, die anfänglich leer ist möchten. und fügen sie dann *nach* dem erstellen.

Um ein neues Objekt eines Typs abzurufen, die eine allgemeine Auflistung implementiert, können Sie die Funktionsvorlage [**winrt::single_threaded_vector**](/uwp/cpp-ref-for-winrt/single-threaded-vector) aufrufen. Das Objekt wird als ein [**IVector**](/uwp/api/windows.foundation.collections.ivector_t_)zurückgegeben, und ist die Schnittstelle, die über die Funktionen und Eigenschaften des zurückgegebenen Objekts aufrufen.

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

Wie im obigen Codebeispiel sehen, nach dem Erstellen der Auflistung können Sie Elemente anfügen, durchlaufen sie und in der Regel behandeln Sie das Objekt wie alle Windows-Runtime-Collection-Objekt, das Sie von einer API erhalten haben. Wenn Sie eine unveränderliche Ansicht über die Auflistung benötigen, können Sie wie gezeigt [**IVector::GetView**](/uwp/api/windows.foundation.collections.ivector-1.getview), aufrufen. Das oben gezeigte Muster&mdash;der Erstellung und Nutzung von einer Sammlungs&mdash;eignet sich für einfache Fälle, in denen Sie Daten in übergeben oder Abrufen von Daten aus einer API. Sie können eine **IVector**oder ein **IVectorView**übergeben, an einer beliebigen Stelle einer [**IIterable**](/uwp/api/windows.foundation.collections.iiterable_t_) erwartet wird.

Im obigen Codebeispiel initialisiert der Aufruf von **WinRT:: init_apartment** COM; Standardmäßig werden in einem Multithread-Apartment.

### <a name="general-purpose-collection-primed-from-data"></a>Allgemeine Sammlung von Daten vorbereitet

Dieser Abschnitt beschreibt das Szenario, in denen Sie eine Sammlung erstellen und füllen diese zur gleichen Zeit möchten.

Sie können den Aufwand für die Aufrufe von **Append** im vorherigen Codebeispiel vermeiden. Möglicherweise haben Sie bereits die Quelldaten, oder Sie können aber auch die Quelldaten vor dem Erstellen des Windows-Runtime-Collection-Objekts zu füllen. Gehen Sie dazu wie folgt vor:

```cppwinrt
auto coll1{ winrt::single_threaded_vector<int>({ 1,2,3 }) };

std::vector<int> values{ 1,2,3 };
auto coll2{ winrt::single_threaded_vector<int>(std::move(values)) };

for (auto const& el : coll2)
{
    std::cout << el << std::endl;
}
```

Sie können ein temporäres Objekt enthält Daten aus die **winrt::single_threaded_vector**, übergeben wie bei `coll1`oben. Oder Sie können eine **Std:: Vector** (vorausgesetzt, Sie wird nicht werden auf diese zugreifenden erneut) verschieben in die Funktion. In beiden Fällen können Sie einen *r-Wert* an die Funktion übergeben. Ermöglicht den Compiler effizient, und vermeiden, die Daten zu kopieren. Wenn Sie mehr über *Rvalues*erfahren möchten, finden Sie unter [Wert Kategorien und Verweise auf diese](cpp-value-categories.md).

Wenn Sie ein XAML-Items-Steuerelement an eine Sammlung binden möchten, können Sie Sie. Beachten Sie jedoch, um die Eigenschaft [**ItemsControl.ItemsSource**](/uwp/api/windows.ui.xaml.controls.itemscontrol.itemssource) richtig festzulegen, Sie festlegen, dass ein Wert vom Typ **IVector** **IInspectable** (oder ein Typ Interoperabilität, z. B. [**IBindableObservableVector müssen**](/uwp/api/windows.ui.xaml.interop.ibindableobservablevector)). Hier ist ein Codebeispiel, das eine Sammlung von einem Typ, der für die Bindung geeignet erzeugt fügt an ein Element an, ein.

```cppwinrt
auto bookSkus{ winrt::single_threaded_vector<Windows::Foundation::IInspectable>() };
bookSkus.Append(make<Bookstore::implementation::BookSku>(L"Moby Dick"));
```

Sie können Erstellen einer Windows-Runtime-Sammlung von Daten und bereiten Sie eine Ansicht für dieses auf, übergeben Sie an eine API, ohne etwas zu kopieren.

```cppwinrt
std::vector<float> values{ 0.1f, 0.2f, 0.3f };
IVectorView<float> view{ winrt::single_threaded_vector(std::move(values)).GetView() };
```

In den obigen Beispielen werden die Sammlung *erstellen wir* an ein XAML-Items-Steuerelement gebunden. aber die Sammlung nicht feststellbar.

### <a name="observable-collection"></a>Observable-collection

Ein neues Objekt eines Typs abrufen, die eine *Observable* -Collection implementiert, rufen Sie die Funktionsvorlage [**winrt::single_threaded_observable_vector**](/uwp/cpp-ref-for-winrt/single-threaded-observable-vector) mit jedem beliebigen Elementtyp. Jedoch um eine Observable-Collection geeignet für die Bindung an ein XAML-Items-Steuerelement können, verwenden Sie **IInspectable** als Typ des Elements.

Das Objekt wird als eine [**IObservableVector**](/uwp/api/windows.foundation.collections.iobservablevector_t_)zurückgegeben, und dies ist die Schnittstelle, die über die Sie (oder das Steuerelement an das sie gebunden ist) des zurückgegebenen Objekts Funktionen und Eigenschaften aufgerufen werden.

```cppwinrt
auto bookSkus{ winrt::single_threaded_observable_vector<Windows::Foundation::IInspectable>() };
```

Weitere Details und Codebeispiele, über das Binden des Benutzers Benutzeroberfläche (UI) steuert, um eine Observable-Collection, finden Sie unter [XAML-items-Steuerelemente; binden an eine C++ / WinRT-Collection](binding-collection.md).

### <a name="associative-collection-map"></a>Assoziative Sammlung (Map)

Es gibt Versionen der zwei Funktionen, denen bereits assoziative Auflistung.

- Die Funktionsvorlage [**winrt::single_threaded_map**](/uwp/cpp-ref-for-winrt/single-threaded-map) gibt eine assoziative nicht feststellbare Sammlung als ein [**IMap**](/uwp/api/windows.foundation.collections.imap_k_v_)zurück.
- Die Funktionsvorlage [**winrt::single_threaded_observable_map**](/uwp/cpp-ref-for-winrt/single-threaded-observable-map) gibt eine assoziative Observable-Collection als ein [**IObservableMap**](/uwp/api/windows.foundation.collections.iobservablemap_k_v_)zurück.

Sie können diese Sammlungen mit Daten optional vorzubereiten, indem Sie einen *r-Wert* des Typs **Std:: Map** oder **std::unordered_map**an die Funktion übergeben.

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

### <a name="single-threaded"></a>Single threaded-

Die "Single-threaded" in den Namen dieser Funktionen gibt an, dass sie alle Parallelität nicht&mdash;mit anderen Worten: sie sind nicht threadsicher. Die erwähnen von Threads ist nicht im Zusammenhang mit Apartments, da die von diesen Funktionen zurückgegebenen Objekte alle agil sind (siehe [Agile Objekte in C++ / WinRT](agile-objects.md)). Es ist einfach, dass die Objekte Singlethread-Apartment. Und das ist vollständig geeignet, wenn nur Daten eine Möglichkeit oder andere über die Application binary Interface (ABI) übergeben werden sollen.

## <a name="base-classes-for-collections"></a>Basisklassen für Sammlungen

Wenn Sie Flexibilität, eine eigene benutzerdefinierte Auflistung implementieren möchten, sollten Sie dabei, die schwer zu vermeiden. Angenommen, dies ist eine benutzerdefinierte Vektoransicht aussehen würde *ohne Unterstützung von C++ / WinRT-Basisklassen*.

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

Stattdessen ist es sehr viel einfacher, leiten Ihre benutzerdefinierte Vektoransicht aus der strukturvorlage [**winrt::vector_view_base**](/uwp/cpp-ref-for-winrt/vector-view-base) , und implementieren Sie einfach die **Get_container** -Funktion, um dem Container, die Daten verfügbar zu machen.

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

Der Container **Get_container** zurückgegebene muss stellen die Schnittstelle **Anfang** und **Ende** dieses **winrt::vector_view_base** erwartet. Wie im obigen Beispiel gezeigt, bereitstellt **Std:: Vector** . Aber Sie können alle Container, die den gleichen Vertrag, einschließlich Ihrer eigenen benutzerdefinierten Container erfüllt zurückgeben.

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

Hierbei handelt es sich um die Basis Klassen, die C++ / WinRT zur bietet benutzerdefinierte Sammlungen implementieren.

### [<a name="winrtvectorviewbase"></a>WinRT::vector_view_base](/uwp/cpp-ref-for-winrt/vector-view-base)

Finden Sie unter der obigen Codebeispiele.

### [<a name="winrtvectorbase"></a>WinRT::vector_base](/uwp/cpp-ref-for-winrt/vector-base)

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

### [<a name="winrtobservablevectorbase"></a>WinRT::observable_vector_base](/uwp/cpp-ref-for-winrt/observable-vector-base)

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

### [<a name="winrtmapviewbase"></a>WinRT::map_view_base](/uwp/cpp-ref-for-winrt/map-view-base)

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

### [<a name="winrtmapbase"></a>WinRT::map_base](/uwp/cpp-ref-for-winrt/map-base)

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

### [<a name="winrtobservablemapbase"></a>WinRT::observable_map_base](/uwp/cpp-ref-for-winrt/observable-map-base)

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

## <a name="important-apis"></a>Wichtige APIs
* [ItemsControl.ItemsSource-Eigenschaft](/uwp/api/windows.ui.xaml.controls.itemscontrol.itemssource)
* [IObservableVector-Schnittstelle](/uwp/api/windows.foundation.collections.iobservablevector_t_)
* [IVector Schnittstelle](/uwp/api/windows.foundation.collections.ivector_t_)
* [WinRT::map_base strukturvorlage](/uwp/cpp-ref-for-winrt/map-base)
* [WinRT::map_view_base strukturvorlage](/uwp/cpp-ref-for-winrt/map-view-base)
* [WinRT::observable_map_base strukturvorlage](/uwp/cpp-ref-for-winrt/observable-map-base)
* [WinRT::observable_vector_base strukturvorlage](/uwp/cpp-ref-for-winrt/observable-vector-base)
* [WinRT::single_threaded_observable_map Funktionsvorlage](/uwp/cpp-ref-for-winrt/single-threaded-observable-map)
* [WinRT::single_threaded_map Funktionsvorlage](/uwp/cpp-ref-for-winrt/single-threaded-map)
* [WinRT::single_threaded_observable_vector Funktionsvorlage](/uwp/cpp-ref-for-winrt/single-threaded-observable-vector)
* [WinRT::single_threaded_vector Funktionsvorlage](/uwp/cpp-ref-for-winrt/single-threaded-vector)
* [WinRT::vector_base strukturvorlage](/uwp/cpp-ref-for-winrt/vector-base)
* [WinRT::vector_view_base strukturvorlage](/uwp/cpp-ref-for-winrt/vector-view-base)

## <a name="related-topics"></a>Verwandte Themen
* [Wert Kategorien und Verweise auf diese](cpp-value-categories.md)
* [XAML-Items-Steuerelemente; Binden an eine C++/WinRT-Collection](binding-collection.md)
