---
author: stevewhims
description: C + / WinRT bietet Funktionen und Basisklassen, die Sie speichern viel Zeit und Mühe beim Implementieren und/oder Sammlungen übergeben werden soll.
title: Sammlungen mit C + / WinRT
ms.author: stwhi
ms.date: 08/24/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, standard, C ++, Cpp, Winrt, Projektion, -Auflistung
ms.localizationpriority: medium
ms.openlocfilehash: 54f949c41af885ec379eaa9e5b12764710532b50
ms.sourcegitcommit: 753dfcd0f9fdfc963579dd0b217b445c4b110a18
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "2867943"
---
# <a name="collections-with-cwinrtwindowsuwpcpp-and-winrt-apisintro-to-using-cpp-with-winrt"></a>Sammlungen mit [C + / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)

> [!NOTE]
> **Einige Informationen beziehen sich auf die Vorabversion, die vor der kommerziellen Freigabe möglicherweise wesentlichen Änderungen unterliegt. Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.**

Intern, verfügt über eine Windows-Runtime-Auflistung ein Großteil kompliziert Transfers. Aber wenn Sie ein Auflistungsobjekt an eine Windows-Runtime-Funktion übergeben oder eigene Auflistungseigenschaften und Auflistungstypen implementieren möchten, Funktionen und in C + Basisklassen sind / WinRT, um Sie zu unterstützen. Diese Features vereinfachen Sie Ihre Hände und Aufwand viel Zeit und Mühe sparen.

> [!IMPORTANT]
> In diesem Thema beschriebenen Features sind verfügbar, wenn Sie die [Windows 10 SDK Vorschau erstellen 17661](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK)installiert haben, oder höher.

[**IVector**](/uwp/api/windows.foundation.collections.ivector_t_) ist die Windows-Runtime-Schnittstelle, die von jeder direktem Zugriff-Auflistung von Elementen implementiert. Würden Sie **IVector** selbst implementieren, müssen Sie auch [**IIterable**](/uwp/api/windows.foundation.collections.iiterable_t_), [**IVectorView**](/uwp/api/windows.foundation.collections.ivectorview_t_)und [**IIterator**](/uwp/api/windows.foundation.collections.iiterator_t_)implementieren. Auch wenn *müssen* Sie eine benutzerdefinierte Auflistung eingeben, wird, die viel Arbeit. Aber wenn Sie die Daten in eine **Std** (oder eine **Std:: Map**oder ein **std::unordered_map**) haben, und alles, was Sie tun möchten ist, die an eine Windows-Laufzeit-API zu übergeben, klicken Sie dann möchten, damit kein diese Stufe der Arbeit, sofern möglich. Und es *ist* möglich, vermeiden, da C + / WinRT finden Sie Informationen zum Erstellen von Websitesammlungen effizient und mit minimalem Aufwand.

## <a name="helper-functions-for-collections"></a>Hilfsfunktionen für Websitesammlungen

### <a name="general-purpose-collection-empty"></a>Allgemeine Auflistung leer

Um ein neues Objekt eines Typs abzurufen, die eine allgemeine Auflistung implementiert wird, können Sie die Vorlage **winrt::single_threaded_vector** Funktion aufrufen. Das Objekt wird als ein [**IVector**](/uwp/api/windows.foundation.collections.ivector_t_)zurückgegeben, und das ist die Schnittstelle, über die Funktionen und Eigenschaften des zurückgegebenen Objekts aufrufen.

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

Wie Sie in der obigen Codebeispiel sehen können, nach dem Erstellen der Auflistung können Sie Elemente anfügen, durchlaufen sie und behandeln Sie das Objekt im Allgemeinen wie alle Windows-Runtime-Auflistungsobjekt, das Sie von einer API erhalten haben. Wenn Sie eine Ansicht in der Auflistung benötigen, können Sie wie dargestellt [IVector::GetView](/uwp/api/windows.foundation.collections.ivector-1.getview), aufrufen. Das Muster oben gezeigten&mdash;über das Erstellen und Verarbeiten von einer Auflistung&mdash;eignet sich für einfache Szenarien, in dem Sie Daten in übergeben oder Abrufen von Daten aus einer API möchten.

### <a name="general-purpose-collection-primed-from-data"></a>Allgemeine Auflistung, die anhand von Daten vorbereitet

Sie können auch den Aufwand für die Aufrufe von **Append** vermeiden, die im obigen Codebeispiel angezeigt werden können. Möglicherweise haben Sie bereits die Quelldaten, oder Sie möchten sie vor dem Erstellen des Windows-Runtime-Auflistungsobjekt zu füllen. Gehen Sie dazu wie folgt vor:

```cppwinrt
auto coll1{ winrt::single_threaded_vector<int>({ 1,2,3 }) };

std::vector<int> values{ 1,2,3 };
auto coll2{ winrt::single_threaded_vector<int>(std::move(values)) };

for (auto const& el : coll2)
{
    std::cout << el << std::endl;
}
```

Sie können ein temporäres Objekt mit Daten aus dem **winrt::single_threaded_vector**, übergeben wie bei der `coll1`oben. Oder Sie können eine **Std** (vorausgesetzt, Sie werden nicht werden auf diese zugreifen erneut) verschieben in der Funktion. In beiden Fällen haben Sie einen *r-Wert* an die Funktion übergeben. Ermöglicht den Compiler zu mehr Effizienz und Kopieren der Daten zu vermeiden. Wenn Sie mehr über *Rvalues*erfahren möchten, finden Sie unter [Wert Kategorien und Verweise auf diese](cpp-value-categories.md).

Wenn Sie ein XAML-Elemente-Steuerelement an eine Auflistung binden möchten, können Sie Sie. Aber Bedenken Sie, dass zum ordnungsgemäß die [**ItemsControl.ItemsSource**](/uwp/api/windows.ui.xaml.controls.itemscontrol.itemssource) -Eigenschaft festlegen, Sie es auf einen Wert vom Typ **IVector** **IInspectable** (oder eines Typs Interoperabilität wie [**IBindableObservableVector**](/uwp/api/windows.ui.xaml.interop.ibindableobservablevector)) festlegen müssen. Hier ist ein Codebeispiel, das eine Auflistung von einen Typ für die Bindung geeignet erzeugt Fügt ein Element hinzu.

```cppwinrt
auto bookSkus{ winrt::single_threaded_vector<Windows::Foundation::IInspectable>() };
bookSkus.Append(make<Bookstore::implementation::BookSku>(L"Moby Dick"));
```

Die oben aufgeführten *können* Auflistung werden auf ein XAML-Elementsteuerelement gebunden; aber nicht wahrnehmbare Element die Auflistung zur Verfügung.

### <a name="observable-collection"></a>Sichtbare-Auflistung

Um ein neues Objekt eines Typs abzurufen, die eine *Observable* -Auflistung implementiert, rufen Sie die Vorlage **winrt::single_threaded_observable_vector** -Funktion mit jedem beliebigen Elementtyp. Aber damit erkennbare-Auflistung für die Bindung an ein Steuerelement der XAML-Elemente geeignet ist, verwenden Sie **IInspectable** als Elementtyp.

Das Objekt wird als ein [**IObservableVector**](/uwp/api/windows.foundation.collections.iobservablevector_t_)zurückgegeben, und das ist die Schnittstelle, über die Sie (oder das Steuerelement an dem er gebunden ist) Funktionen und Eigenschaften des zurückgegebenen Objekts aufrufen.

```cppwinrt
auto bookSkus{ winrt::single_threaded_observable_vector<Windows::Foundation::IInspectable>() };
```

Finden Sie weitere Informationen und Codebeispielen zum Binden Ihre Benutzers Benutzeroberfläche (UI) steuert erkennbare-Auflistung [XAML Elemente Steuerelemente; binden an C + / WinRT Auflistung](binding-collection.md).

### <a name="associative-container-map"></a>Assoziative Container (Map)

Assoziative Container Versionen der beiden Funktionen, denen bereits sind vorhanden.

- Die Vorlage **Single_threaded_map** -Funktion gibt einen assoziativen Container als ein [**IMap**](/uwp/api/windows.foundation.collections.imap_k_v_)zurück. Die Zuordnung ist nicht sichtbare.
- Die Vorlage **Single_threaded_observable_map** -Funktion gibt einen erkennbare assoziativen Container als ein [**IObservableMap**](/uwp/api/windows.foundation.collections.iobservablemap_k_v_)zurück.

Optional können Sie diese Container mit Daten Systemdatenträgern, durch einen *r-Wert* des Typs **Std:: Map** oder **std::unordered_map**an die Funktion übergeben.

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

### <a name="single-threaded"></a>Single Threading-

Die "Single-Threading" in den Namen dieser Funktionen gibt an, dass sie alle gleichzeitig nicht&mdash;mit anderen Worten, sie sind nicht threadsicheren. Die Erwähnung von Threads ist nicht im Zusammenhang mit Apartments, da die Objekte zurückgegeben, die aus diesen Funktionen alle agile sind (finden Sie unter [Agile-Objekte in C + / WinRT](agile-objects.md)). Es ist einfach, dass die Objekte Single-Threading sind. Und das ist vollständig geeignet, wenn Sie einfach eine Möglichkeit der Daten oder der anderen über die binären Anwendungsschnittstelle (ABI) übergeben möchten.

## <a name="base-classes-for-collections"></a>Basisklassen für Websitesammlungen

Wenn Sie Flexibilität, eigene benutzerdefinierte Auflistung implementieren möchten, sollten Sie wie folgt, die schwer zu vermeiden. Beispielsweise sieht wie eine benutzerdefinierte Vektoransicht aussehen würde *ohne Unterstützung des C + / Basisklassen WinRT des*.

```cppwinrt
...
using namespace Windows::Foundation::Collections;

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

Stattdessen ist jedoch viel einfacher, leiten Sie Ihre benutzerdefinierte Vektoransicht aus der **winrt::vector_view_base** Struct Vorlage, und implementieren Sie nur die **Get_container** -Funktion, um dem Container, Ihre Daten verfügbar zu machen.

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

Der Container **Get_container** zurückgegebene muss stellen die **Anfang** und **Ende** -Schnittstelle, **winrt::vector_view_base** erwartet. Wie im obigen Beispiel gezeigt, bereitstellt **Std** . Jedoch können Sie alle Container, die den gleichen Vertrag, einschließlich Ihrer eigenen benutzerdefinierten Container erfüllt zurück.

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

Hierbei handelt es sich um die Basis Klassen, C + / WinRT enthält, mit denen Sie benutzerdefinierte Websitesammlungen zu implementieren.

- **WinRT::vector_view_base**
- **WinRT::vector_base**
- **WinRT::observable_vector_base**
- **WinRT::map_view_base**
- **WinRT::map_base**
- **WinRT::observable_map_base**

## <a name="important-apis"></a>Wichtige APIs
* [ItemsControl.ItemsSource](/uwp/api/windows.ui.xaml.controls.itemscontrol.itemssource)
* [IObservableVector](/uwp/api/windows.foundation.collections.iobservablevector_t_)
* [IVector](/uwp/api/windows.foundation.collections.ivector_t_)

## <a name="related-topics"></a>Verwandte Themen
* [Wert Kategorien und Verweise auf diese](cpp-value-categories.md)
* [XAML-Items-Steuerelemente; Binden an eine C++/WinRT-Collection](binding-collection.md)
