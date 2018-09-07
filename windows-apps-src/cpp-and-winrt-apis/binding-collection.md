---
author: stevewhims
description: Eine Collection, die effektiv an ein XAML-Items-Steuerelement gebunden werden kann, wird als *Observable*-Collection bezeichnet. Dieses Thema zeigt, wie man eine Observable-Collection implementiert und nutzt und wie man ein XAML-Items-Steuerelement daran bindet.
title: XAML-Items-Steuerelemente; Binden an eine C++/WinRT-Collection
ms.author: stwhi
ms.date: 05/07/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp, standard, c++, cpp, winrt, projizierung, XAML, steuerelement, binden, collection
ms.localizationpriority: medium
ms.openlocfilehash: 9ba935b1a5316c2d7af9c7681705595efea7ca08
ms.sourcegitcommit: 53ba430930ecec8ea10c95b390fe6e654fe363e1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "3417853"
---
# <a name="xaml-items-controls-bind-to-a-cwinrtwindowsuwpcpp-and-winrt-apisintro-to-using-cpp-with-winrt-collection"></a>XAML-Items-Steuerelemente; Binden an eine [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)-Collection
> [!NOTE]
> **Einige Informationen beziehen sich auf die Vorabversion, die vor der kommerziellen Freigabe möglicherweise wesentlichen Änderungen unterliegt. Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.**

Eine Collection, die effektiv an ein XAML-Items-Steuerelement gebunden werden kann, wird als *Observable*-Collection bezeichnet. Dieses Konzept basiert auf dem Software-Design-Muster, das als *Observer-Pattern* bekannt ist. Dieses Thema zeigt, wie man Observable-Collections in C++/WinRT implementiert und wie man XAML-Item-Steuerelemente an diese bindet.

Diese exemplarische Vorgehensweise baut auf dem in [XAML-Steuerelemente; Binden an eine C++/WinRT-Eigenschaft](binding-property.md) erstellten Projekt auf, und sie ergänzt die in diesem Thema erläuterten Konzepte.

> [!IMPORTANT]
> Wichtige Konzepte und Begriffe, die Ihr Verständnis für die Verwendung von Laufzeitklassen mit C++/WinRT unterstützen, finden Sie unter [Verwenden von APIs mit C++/WinRT](consume-apis.md) und [Erstellen von APIs mit C++/WinRT](author-apis.md).

## <a name="what-does-observable-mean-for-a-collection"></a>Was bedeutet *observable* für eine Collection?
Wenn eine Laufzeitklasse, die eine Collection repräsentiert, das Ereignis [**IObservableVector&lt;T&gt;::VectorChanged**](/uwp/api/windows.foundation.collections.iobservablevector-1.vectorchanged) auslöst, wenn ein Element hinzugefügt oder entfernt wird, dann ist die Laufzeitklasse eine Observable-Collection. Ein XAML-Items-Steuerelement kann sich an diese Ereignisse binden und sie verarbeiten, indem es die aktualisierte Collection abruft und sich dann aktualisiert, um die aktuellen Elemente anzuzeigen.

> [!NOTE]
> Informationen zur Installation und Verwendung der C++/WinRT Visual Studio Extension (VSIX) (die Projektvorlagenunterstützung sowie C++/WinRT MSBuild-Eigenschaften und -Ziele bietet) finden Sie unter [Visual Studio-Unterstützung für C++/WinRT und VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix).

## <a name="implement-singlethreadedobservablevectorlttgt"></a>Implementieren von **single_threaded_observable_vector&lt;T&gt;**
Es ist hilfreich, eine Observable-Vektor-Vorlage zu haben, die als nützliche, universell einsetzbare Implementierung von [**IObservableVector&lt;T&gt;**](/uwp/api/windows.foundation.collections.iobservablevector_t_) dient. Hier ist eine Klasse namens **single_threaded_observable_vector\<T\>**.

> [!NOTE]
> Wenn Sie die [Windows 10 SDK Preview Build 17661](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK)installiert haben, oder höher, dann können Sie direkt verwenden die **single_threaded_observable_vector\ < T\ >** Factory-Funktion anstelle der untenstehenden codeauflistung (zeigen wir den genauen Code später In diesem Thema). Wenn Sie noch nicht auf die Version des SDKS befinden, dann werden einfach über Eintrag Codeversion an die **Winrt** -Funktion verwenden, wenn Sie sind.

```cppwinrt
// single_threaded_observable_vector.h
#pragma once

namespace winrt::Bookstore::implementation
{
    using namespace Windows::Foundation::Collections;

    template <typename T>
    struct single_threaded_observable_vector : implements<single_threaded_observable_vector<T>,
        IObservableVector<T>,
        IVector<T>,
        IVectorView<T>,
        IIterable<T>>
    {
        event_token VectorChanged(VectorChangedEventHandler<T> const& handler)
        {
            return m_changed.add(handler);
        }

        void VectorChanged(event_token const cookie)
        {
            m_changed.remove(cookie);
        }

        T GetAt(uint32_t const index) const
        {
            if (index >= m_values.size())
            {
                throw hresult_out_of_bounds();
            }

            return m_values[index];
        }

        uint32_t Size() const noexcept
        {
            return static_cast<uint32_t>(m_values.size());
        }

        IVectorView<T> GetView()
        {
            return *this;
        }

        bool IndexOf(T const& value, uint32_t& index) const noexcept
        {
            index = static_cast<uint32_t>(std::find(m_values.begin(), m_values.end(), value) - m_values.begin());
            return index < m_values.size();
        }

        void SetAt(uint32_t const index, T const& value)
        {
            if (index >= m_values.size())
            {
                throw hresult_out_of_bounds();
            }

            ++m_version;
            m_values[index] = value;
            m_changed(*this, make<args>(CollectionChange::ItemChanged, index));
        }

        void InsertAt(uint32_t const index, T const& value)
        {
            if (index > m_values.size())
            {
                throw hresult_out_of_bounds();
            }

            ++m_version;
            m_values.insert(m_values.begin() + index, value);
            m_changed(*this, make<args>(CollectionChange::ItemInserted, index));
        }

        void RemoveAt(uint32_t const index)
        {
            if (index >= m_values.size())
            {
                throw hresult_out_of_bounds();
            }

            ++m_version;
            m_values.erase(m_values.begin() + index);
            m_changed(*this, make<args>(CollectionChange::ItemRemoved, index));
        }

        void Append(T const& value)
        {
            ++m_version;
            m_values.push_back(value);
            m_changed(*this, make<args>(CollectionChange::ItemInserted, Size() - 1));
        }

        void RemoveAtEnd()
        {
            if (m_values.empty())
            {
                throw hresult_out_of_bounds();
            }

            ++m_version;
            m_values.pop_back();
            m_changed(*this, make<args>(CollectionChange::ItemRemoved, Size()));
        }

        void Clear() noexcept
        {
            ++m_version;
            m_values.clear();
            m_changed(*this, make<args>(CollectionChange::Reset, 0));
        }

        uint32_t GetMany(uint32_t const startIndex, array_view<T> values) const
        {
            if (startIndex >= m_values.size())
            {
                return 0;
            }

            uint32_t actual = static_cast<uint32_t>(m_values.size() - startIndex);

            if (actual > values.size())
            {
                actual = values.size();
            }

            std::copy_n(m_values.begin() + startIndex, actual, values.begin());
            return actual;
        }

        void ReplaceAll(array_view<T const> value)
        {
            ++m_version;
            m_values.assign(value.begin(), value.end());
            m_changed(*this, make<args>(CollectionChange::Reset, 0));
        }

        IIterator<T> First()
        {
            return make<iterator>(this);
        }

    private:

        std::vector<T> m_values;
        event<VectorChangedEventHandler<T>> m_changed;
        uint32_t m_version{};

        struct args : implements<args, IVectorChangedEventArgs>
        {
            args(CollectionChange const change, uint32_t const index) :
                m_change(change),
                m_index(index)
            {
            }

            CollectionChange CollectionChange() const
            {
                return m_change;
            }

            uint32_t Index() const
            {
                return m_index;
            }

        private:

            Windows::Foundation::Collections::CollectionChange const m_change{};
            uint32_t const m_index{};
        };

        struct iterator : implements<iterator, IIterator<T>>
        {
            explicit iterator(single_threaded_observable_vector<T>* owner) noexcept :
            m_version(owner->m_version),
                m_current(owner->m_values.begin()),
                m_end(owner->m_values.end())
            {
                m_owner.copy_from(owner);
            }

            void abi_enter() const
            {
                if (m_version != m_owner->m_version)
                {
                    throw hresult_changed_state();
                }
            }

            T Current() const
            {
                if (m_current == m_end)
                {
                    throw hresult_out_of_bounds();
                }

                return*m_current;
            }

            bool HasCurrent() const noexcept
            {
                return m_current != m_end;
            }

            bool MoveNext() noexcept
            {
                if (m_current != m_end)
                {
                    ++m_current;
                }

                return HasCurrent();
            }

            uint32_t GetMany(array_view<T> values)
            {
                uint32_t actual = static_cast<uint32_t>(std::distance(m_current, m_end));

                if (actual > values.size())
                {
                    actual = values.size();
                }

                std::copy_n(m_current, actual, values.begin());
                std::advance(m_current, actual);
                return actual;
            }

        private:

            com_ptr<single_threaded_observable_vector<T>> m_owner;
            uint32_t const m_version;
            typename std::vector<T>::const_iterator m_current;
            typename std::vector<T>::const_iterator const m_end;
        };
    };
}
```

Die **Append**-Funktion zeigt, wie das Ereignis [**IObservableVector&lt;T&gt;::VectorChanged**](/uwp/api/windows.foundation.collections.iobservablevector-1.vectorchanged) ausgelöst wird.

```cppwinrt
m_changed(*this, make<args>(CollectionChange::ItemInserted, Size() - 1));
```

Die Ereignisargumente zeigen sowohl an, dass ein Element eingefügt wurde, als auch was sein Index ist (in diesem Fall das letzte Element). Diese Argumente ermöglichen es einem XAML-Items-Steuerelement, auf das Ereignis zu reagieren und sich optimal zu aktualisieren.

## <a name="add-a-bookskus-collection-to-bookstoreviewmodel"></a>Hinzufügen einer **BookSkus**-Collection zu **BookstoreViewModel**
In [XAML-Steuerelemente; Binden an eine C++/WinRT-Eigenschaft](binding-property.md) haben wir eine Eigenschaft vom Typ **BookSku** zu unserem Hauptansichtsmodell hinzugefügt. In diesem Schritt verwenden wir **single_threaded_observable_vector&lt;T&gt;**, um eine Observable-Collection von **BookSku** für dasselbe Ansichtsmodell zu implementieren.

Deklarieren Sie eine neue Eigenschaft in `BookstoreViewModel.idl`.

```idl
// BookstoreViewModel.idl
...
runtimeclass BookstoreViewModel
{
    BookSku BookSku{ get; };
    Windows.Foundation.Collections.IVector<IInspectable> BookSkus{ get; };
}
...
```

> [!IMPORTANT]
> Beachten Sie in den oben genannten MIDL 3.0-Eintrag, dass der Typ der Eigenschaft **BookSkus** [**IVector**](/uwp/api/windows.foundation.collections.ivector_t_) von [**IInspectable**](https://msdn.microsoft.com/library/windows/desktop/br205821). Im nächsten Abschnitt dieses Themas verwenden wir die Quelle von Elementen von einer [**ListBox**](/uwp/api/windows.ui.xaml.controls.listbox) **BookSkus**binden werden. Ein Listenfeld ist ein Elementsteuerelement, und um die Eigenschaft [**ItemsControl.ItemsSource**](/uwp/api/windows.ui.xaml.controls.itemscontrol.itemssource) richtig festzulegen, müssen Sie festlegen, dass ein Wert vom Typ **IVector** **IInspectable**, oder ein Typ Interoperabilität, z. B. [**IBindableObservableVector**](/uwp/api/windows.ui.xaml.interop.ibindableobservablevector).

Speichern und erstellen Sie das Projekt. Kopieren Sie die Zugriffs-Stubs aus `BookstoreViewModel.h` und `BookstoreViewModel.cpp` in den Ordner `Generated Files` und implementieren Sie sie.

```cppwinrt
// BookstoreViewModel.h
...
#include "single_threaded_observable_vector.h"
...
struct BookstoreViewModel : BookstoreViewModelT<BookstoreViewModel>
{
    BookstoreViewModel();

    Bookstore::BookSku BookSku();

    Windows::Foundation::Collections::IVector<Windows::Foundation::IInspectable> BookSkus();

private:
    Bookstore::BookSku m_bookSku{ nullptr };
    Windows::Foundation::Collections::IVector<Windows::Foundation::IInspectable> m_bookSkus;
};
...
```

```cppwinrt
// BookstoreViewModel.cpp
...
BookstoreViewModel::BookstoreViewModel()
{
    m_bookSku = make<Bookstore::implementation::BookSku>(L"Atticus");
    m_bookSkus = winrt::make<single_threaded_observable_vector<Windows::Foundation::IInspectable>>();
    m_bookSkus.Append(m_bookSku);
}

Bookstore::BookSku BookstoreViewModel::BookSku()
{
    return m_bookSku;
}

Windows::Foundation::Collections::IVector<Windows::Foundation::IInspectable> BookstoreViewModel::BookSkus()
{
    return m_bookSkus;
}
...
```

## <a name="if-you-have-a-windows-10-sdk-preview-build"></a>Wenn Sie ein Windows 10 SDK Preview Build haben
Wenn Sie die [Windows 10 SDK Preview Build 17661](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK)installiert haben oder höher ist, ersetzen Sie diese Codezeile

```cppwinrt
m_bookSkus = winrt::make<single_threaded_observable_vector<Windows::Foundation::IInspectable>>();
```

Dieser.

```cppwinrt
m_bookSkus = winrt::single_threaded_observable_vector<Windows::Foundation::IInspectable>();
```

Anstelle von [**WinRT:: Make**](https://docs.microsoft.com/en-us/uwp/cpp-ref-for-winrt/make)aufrufen, erstellen Sie das entsprechende Collection-Objekt durch Aufrufen der **single_threaded_observable_vector\ < T\ >** Factory-Funktion.

## <a name="bind-a-listbox-to-the-bookskus-property"></a>Binden einer Listbox an die **BookSkus**-Eigenschaft
Öffnen Sie `MainPage.xaml` mit dem XAML-Markup für unsere UI-Hauptseite. Fügen Sie den folgende Markup-Code in dem **StackPanel** hinzu, indem sich der **Button** befindet.

```xaml
<ListBox ItemsSource="{x:Bind MainViewModel.BookSkus}">
    <ItemsControl.ItemTemplate>
        <DataTemplate x:DataType="local:BookSku">
            <TextBlock Text="{x:Bind Title, Mode=OneWay}"/>
        </DataTemplate>
    </ItemsControl.ItemTemplate>
</ListBox>
```

In `MainPage.cpp` fügen Sie dem **Click**-Ereignis-Handler eine Zeile Code hinzu, um ein Buch zur Collection hinzuzufügen.

```cppwinrt
// MainPage.cpp
...
void MainPage::ClickHandler(IInspectable const&, RoutedEventArgs const&)
{
    MainViewModel().BookSku().Title(L"To Kill a Mockingbird");
    MainViewModel().BookSkus().Append(make<Bookstore::implementation::BookSku>(L"Moby Dick"));
}
...
```

Erstellen Sie nun das Projekt und führen Sie es aus. Klicken Sie auf die Schaltfläche, um den **Click**-Ereignis-Handler auszuführen. Wir haben gesehen, dass die Implementierung von **Append** ein Ereignis auslöst, um die Benutzeroberfläche wissen zu lassen, dass sich die Collection geändert hat. Die **ListBox** fragt die Collection erneut ab, um ihren eigenen **Items**-Wert zu aktualisieren. Nach wie vor ändert sich der Titel eines der Bücher, und diese Titeländerung wird sowohl auf der Schaltfläche als auch in der Listbox angezeigt.

## <a name="important-apis"></a>Wichtige APIs
* [IObservableVector&lt;T&gt;::VectorChanged](/uwp/api/windows.foundation.collections.iobservablevector-1.vectorchanged)
* [winrt::make Funktionsvorlage](/uwp/cpp-ref-for-winrt/make)

## <a name="related-topics"></a>Verwandte Themen
* [Verwenden von APIs mit C++/WinRT](consume-apis.md)
* [Erstellen von APIs mit C++/WinRT](author-apis.md)
