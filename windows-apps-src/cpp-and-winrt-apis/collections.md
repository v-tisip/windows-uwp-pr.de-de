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
# <a name="collections-with-cwinrtwindowsuwpcpp-and-winrt-apisintro-to-using-cpp-with-winrt"></a>Sammlungen mit [C + / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)

> [!NOTE]
> **Einige Informationen beziehen sich auf die Vorabversion, die vor der kommerziellen Freigabe möglicherweise wesentlichen Änderungen unterliegt. Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.**

Windows-Runtime-Auflistung wurde intern viel komplizierter Teile. Aber wenn Sie ein Auflistungsobjekt an eine Windows-Runtime-Funktion übergeben oder eigene Auflistungseigenschaften und Auflistungstypen implementieren möchten, Funktionen und Klassen in C# gibt / WinRT unterstützt Sie. Diese Features vereinfachen Sie Ihre Hände und viel Aufwand Zeit und Mühe sparen.

> [!IMPORTANT]
> In diesem Thema beschriebenen Features sind verfügbar, wenn die Installation von [Windows 10 SDK Vorschau erstellen 17661](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK)oder höher.

[**IVector**](/uwp/api/windows.foundation.collections.ivector_t_) ist die Windows-Runtime-Schnittstelle alle RAM Auflistung Elemente implementiert. Würden Sie **IVector** selbst implementieren, müssten Sie auch [**IIterable**](/uwp/api/windows.foundation.collections.iiterable_t_), [**IVectorView**](/uwp/api/windows.foundation.collections.ivectorview_t_)und [**IIterator**](/uwp/api/windows.foundation.collections.iiterator_t_)implementieren. Auch *müssen* Sie eine benutzerdefinierte Auflistung geben wird, die eine Menge Arbeit. Aber wenn **sind** ( **Std:: Map**oder **std::unordered_map Daten**) und benötigen Sie eine Windows-Runtime-API übergeben, dann möchten vermeiden, auf Arbeit, wenn möglich. Und es *ist* möglich, da C + / WinRT können Sie Sammlungen effizient und mit geringem Aufwand erstellen.

## <a name="helper-functions-for-collections"></a>Hilfsfunktionen für Sammlungen

### <a name="general-purpose-collection-empty"></a>Allgemeine Auflistung leer

Rufen Sie ein neues Objekt ein, das eine allgemeine Auflistung implementiert, können Sie die Funktionsvorlage [**winrt::single_threaded_vector**](/uwp/cpp-ref-for-winrt/single-threaded-vector) aufrufen. Das Objekt wird als ein [**IVector**](/uwp/api/windows.foundation.collections.ivector_t_)und ist die Schnittstelle, über die Funktionen und Eigenschaften des zurückgegebenen Objekts aufrufen.

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

Wie im obigen Beispiel sehen können, nach dem Erstellen der Auflistung können Sie fügen Elemente sie durchlaufen und behandeln Sie das Objekt im Allgemeinen wie Windows-Runtime Auflistungsobjekt, das Sie von einer API erhalten haben. Benötigen Sie eine unveränderliche Ansicht der Auflistung können Sie [**IVector::GetView**](/uwp/api/windows.foundation.collections.ivector-1.getview)aufrufen, wie gezeigt. Das oben dargestellte Muster&mdash;erstellen und eine Auflistung&mdash;eignet sich für einfache Szenarien, wo Daten in oder aus einer API. Können Sie ein **IVector**oder ein **IVectorView**übergeben, überall eine [**IIterable**](/uwp/api/windows.foundation.collections.iiterable_t_) erwartet.

### <a name="general-purpose-collection-primed-from-data"></a>Allgemeine Auflistung von Daten vorbereitet

Sie können auch durch Aufrufe auf **Anhängen** vermeiden, die im obigen Codebeispiel angezeigt. Sie haben bereits die Quelldaten und Sie vor der Erstellung von Windows-Runtime-Auflistungsobjekt füllen möchten. Gehen Sie dazu wie folgt vor:

```cppwinrt
auto coll1{ winrt::single_threaded_vector<int>({ 1,2,3 }) };

std::vector<int> values{ 1,2,3 };
auto coll2{ winrt::single_threaded_vector<int>(std::move(values)) };

for (auto const& el : coll2)
{
    std::cout << el << std::endl;
}
```

Übergeben Sie ein temporäres Objekt mit Daten aus dem **winrt::single_threaded_vector**mit `coll1`oben. Oder eine **Std** (vorausgesetzt, Sie wird nicht sein Zugriff wieder) in der Funktion. In beiden Fällen sind Sie ein *r-Wert* an die Funktion übergeben. Das ermöglicht dem Compiler das effiziente und Kopieren der Daten zu vermeiden. Weitere Informationen zu *Rvalues*, finden Sie unter [wertkategorien und Verweise](cpp-value-categories.md).

Wenn Sie ein Steuerelement XAML-Elemente der Auflistung binden möchten, können Sie. Aber beachten, um die [**ItemsControl.ItemsSource**](/uwp/api/windows.ui.xaml.controls.itemscontrol.itemssource) -Eigenschaft richtig festlegen, Sie einen Wert des Typs **IVector** **IInspectable** (oder eines Typs Interoperabilität wie [**IBindableObservableVector müssen**](/uwp/api/windows.ui.xaml.interop.ibindableobservablevector)). Hier ist ein Codebeispiel, liefert ein für die Bindung geeignet und fügt ein Element.

```cppwinrt
auto bookSkus{ winrt::single_threaded_vector<Windows::Foundation::IInspectable>() };
bookSkus.Append(make<Bookstore::implementation::BookSku>(L"Moby Dick"));
```

Sie können eine Windows-Runtime Sammlung aus Daten erstellen und hier auf eine API ohne kopieren etwas weiterleiten.

```cppwinrt
std::vector<float> values{ 0.1f, 0.2f, 0.3f };
IVectorView<float> view{ winrt::single_threaded_vector(std::move(values)).GetView() };
```

In den obigen Beispielen werden die Auflistung *erstellen wir* ein Elementsteuerelement XAML gebunden. doch die Auflistung beobachten.

### <a name="observable-collection"></a>ObservableCollection

Rufen Sie ein neues Objekt ein, das eine *Observable* -Auflistung implementiert rufen Sie die Funktionsvorlage [**winrt::single_threaded_observable_vector**](/uwp/cpp-ref-for-winrt/single-threaded-observable-vector) mit jedem beliebigen Elementtyp. Doch um eine ObservableCollection geeignet für die Bindung an ein Steuerelement XAML-Elemente, **IInspectable** als Elementtyp.

Das Objekt wird als ein [**IObservableVector**](/uwp/api/windows.foundation.collections.iobservablevector_t_)und ist die Schnittstelle, über die Sie (oder das Steuerelement, an das es gebunden ist) Funktionen und Eigenschaften des zurückgegebenen Objekts aufrufen.

```cppwinrt
auto bookSkus{ winrt::single_threaded_observable_vector<Windows::Foundation::IInspectable>() };
```

Für Weitere Informationen und Codebeispiele zum Binden des Benutzers Benutzeroberflächen-Steuerelemente an eine ObservableCollection, siehe [XAML Elemente Steuerelemente, binden an C + / WinRT-Auflistung](binding-collection.md).

### <a name="associative-collection-map"></a>Assoziative Auflistung (Karte)

Assoziative Auflistung Versionen der beiden Funktionen bereits gibt.

- Funktionsvorlage [**winrt::single_threaded_map**](/uwp/cpp-ref-for-winrt/single-threaded-map) gibt eine assoziative-Observable-Auflistung als ein [**IMap**](/uwp/api/windows.foundation.collections.imap_k_v_).
- Die Funktionsvorlage [**winrt::single_threaded_observable_map**](/uwp/cpp-ref-for-winrt/single-threaded-observable-map) gibt eine wahrnehmbare assoziative als ein [**IObservableMap**](/uwp/api/windows.foundation.collections.iobservablemap_k_v_).

Sie können diese Sammlungen mit optional vorzubereiten, einen *r-Wert* von Typ **Std:: Map** oder **std::unordered_map**an die Funktion übergeben.

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

### <a name="single-threaded"></a>Singlethread-

Die "Single-threaded" in die Namen dieser Funktionen gibt an, dass sie Parallelität nicht&mdash;in anderen Worten, sie sind nicht threadsicher. Erwähnung von Threads zusammenhängt Apartments, da alle agile Objekte, die von diesen Funktionen zurückgegeben werden (siehe [bewegliche Objekte in C / WinRT](agile-objects.md)). Es werden nur Objekte singlethreaded. Und typbasierte soll nur Daten ein oder anderen über die Application binary Interface (ABI) übergeben.

## <a name="base-classes-for-collections"></a>Basisklassen für Sammlungen

Wenn Sie volle Flexibilität, eigene benutzerdefinierte Auflistung implementieren möchten, sollten Sie vermeiden, die schwer. Beispielsweise sieht eine benutzerdefinierte Vektoransicht aussehen würde *ohne C + / WinRT Klassen*.

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

Stattdessen ist es viel einfacher, [**winrt::vector_view_base**](/uwp/cpp-ref-for-winrt/vector-view-base) Struktur Vorlage benutzerdefinierten Vektoransicht abgeleitet und implementieren die **Get_container** -Funktion, um dem Container Daten verfügbar zu machen.

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

Zurückgegebene **Get_container** Container muss stellen die Schnittstelle **begin** und **End** , **winrt::vector_view_base** erwartet. Wie im Beispiel oben dargestellt bereitstellt **sind** . Aber können Sie alle Container, der den gleichen Vertrag, einschließlich benutzerdefinierter Containers erfüllt.

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

Diese bilden die Basis Klassen, C + / WinRT zur bietet benutzerdefinierte Sammlungen implementieren.

### [<a name="winrtvectorviewbase"></a>WinRT::vector_view_base](/uwp/cpp-ref-for-winrt/vector-view-base)

Codebeispiele anzeigen

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
* [IVector-Schnittstelle](/uwp/api/windows.foundation.collections.ivector_t_)
* [WinRT::map_base Struktur Vorlage](/uwp/cpp-ref-for-winrt/map-base)
* [WinRT::map_view_base Struktur Vorlage](/uwp/cpp-ref-for-winrt/map-view-base)
* [WinRT::observable_map_base Struktur Vorlage](/uwp/cpp-ref-for-winrt/observable-map-base)
* [WinRT::observable_vector_base Struktur Vorlage](/uwp/cpp-ref-for-winrt/observable-vector-base)
* [WinRT::single_threaded_observable_map Funktionsvorlage](/uwp/cpp-ref-for-winrt/single-threaded-observable-map)
* [WinRT::single_threaded_map Funktionsvorlage](/uwp/cpp-ref-for-winrt/single-threaded-map)
* [WinRT::single_threaded_observable_vector Funktionsvorlage](/uwp/cpp-ref-for-winrt/single-threaded-observable-vector)
* [WinRT::single_threaded_vector Funktionsvorlage](/uwp/cpp-ref-for-winrt/single-threaded-vector)
* [WinRT::vector_base Struktur Vorlage](/uwp/cpp-ref-for-winrt/vector-base)
* [WinRT::vector_view_base Struktur Vorlage](/uwp/cpp-ref-for-winrt/vector-view-base)

## <a name="related-topics"></a>Verwandte Themen
* [Wertkategorien und Verweise](cpp-value-categories.md)
* [XAML-Items-Steuerelemente; Binden an eine C++/WinRT-Collection](binding-collection.md)
