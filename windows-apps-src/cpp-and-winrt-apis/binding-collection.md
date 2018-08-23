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
ms.openlocfilehash: 9337c0625c68970d9e68df74fa13228369e8bf41
ms.sourcegitcommit: 9c79fdab9039ff592edf7984732d300a14e81d92
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/23/2018
ms.locfileid: "2823152"
---
# <a name="xaml-items-controls-bind-to-a-cwinrtwindowsuwpcpp-and-winrt-apisintro-to-using-cpp-with-winrt-collection"></a><span data-ttu-id="9826d-105">XAML-Items-Steuerelemente; Binden an eine [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)-Collection</span><span class="sxs-lookup"><span data-stu-id="9826d-105">XAML items controls; bind to a [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) collection</span></span>
> [!NOTE]
> **<span data-ttu-id="9826d-106">Einige Informationen beziehen sich auf die Vorabversion, die vor der kommerziellen Freigabe möglicherweise wesentlichen Änderungen unterliegt.</span><span class="sxs-lookup"><span data-stu-id="9826d-106">Some information relates to pre-released product which may be substantially modified before it’s commercially released.</span></span> <span data-ttu-id="9826d-107">Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.</span><span class="sxs-lookup"><span data-stu-id="9826d-107">Microsoft makes no warranties, express or implied, with respect to the information provided here.</span></span>**

<span data-ttu-id="9826d-108">Eine Collection, die effektiv an ein XAML-Items-Steuerelement gebunden werden kann, wird als *Observable*-Collection bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="9826d-108">A collection that can be effectively bound to a XAML items control is known as an *observable* collection.</span></span> <span data-ttu-id="9826d-109">Dieses Konzept basiert auf dem Software-Design-Muster, das als *Observer-Pattern* bekannt ist.</span><span class="sxs-lookup"><span data-stu-id="9826d-109">This idea is based on the software design pattern known as the *observer pattern*.</span></span> <span data-ttu-id="9826d-110">Dieses Thema zeigt, wie man Observable-Collections in C++/WinRT implementiert und wie man XAML-Item-Steuerelemente an diese bindet.</span><span class="sxs-lookup"><span data-stu-id="9826d-110">This topic shows how to implement observable collections in C++/WinRT, and how to bind XAML items controls to them.</span></span>

<span data-ttu-id="9826d-111">Diese exemplarische Vorgehensweise baut auf dem in [XAML-Steuerelemente; Binden an eine C++/WinRT-Eigenschaft](binding-property.md) erstellten Projekt auf, und sie ergänzt die in diesem Thema erläuterten Konzepte.</span><span class="sxs-lookup"><span data-stu-id="9826d-111">This walkthrough builds on the project created in [XAML controls; bind to a C++/WinRT property](binding-property.md), and it adds to the concepts explained in that topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9826d-112">Wichtige Konzepte und Begriffe, die Ihr Verständnis für die Verwendung von Laufzeitklassen mit C++/WinRT unterstützen, finden Sie unter [Verwenden von APIs mit C++/WinRT](consume-apis.md) und [Erstellen von APIs mit C++/WinRT](author-apis.md).</span><span class="sxs-lookup"><span data-stu-id="9826d-112">For essential concepts and terms that support your understanding of how to consume and author runtime classes with C++/WinRT, see [Consume APIs with C++/WinRT](consume-apis.md) and [Author APIs with C++/WinRT](author-apis.md).</span></span>

## <a name="what-does-observable-mean-for-a-collection"></a><span data-ttu-id="9826d-113">Was bedeutet *observable* für eine Collection?</span><span class="sxs-lookup"><span data-stu-id="9826d-113">What does *observable* mean for a collection?</span></span>
<span data-ttu-id="9826d-114">Wenn eine Laufzeitklasse, die eine Collection repräsentiert, das Ereignis [**IObservableVector&lt;T&gt;::VectorChanged**](/uwp/api/windows.foundation.collections.iobservablevector-1.vectorchanged) auslöst, wenn ein Element hinzugefügt oder entfernt wird, dann ist die Laufzeitklasse eine Observable-Collection.</span><span class="sxs-lookup"><span data-stu-id="9826d-114">If a runtime class that represents a collection chooses to raise the [**IObservableVector&lt;T&gt;::VectorChanged**](/uwp/api/windows.foundation.collections.iobservablevector-1.vectorchanged) event whenever an element is added to it or removed from it, then the runtime class is an observable collection.</span></span>

<span data-ttu-id="9826d-115">Ein XAML-Items-Steuerelement kann sich an diese Ereignisse binden und sie verarbeiten, indem es die aktualisierte Collection abruft und sich dann aktualisiert, um die aktuellen Elemente anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="9826d-115">A XAML items control can bind to, and handle, these events by retrieving the updated collection and then updating itself to show the current elements.</span></span>

> [!NOTE]
> <span data-ttu-id="9826d-116">Informationen zur Installation und Verwendung der C++/WinRT Visual Studio Extension (VSIX) (die Projektvorlagenunterstützung sowie C++/WinRT MSBuild-Eigenschaften und -Ziele bietet) finden Sie unter [Visual Studio-Unterstützung für C++/WinRT und VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix).</span><span class="sxs-lookup"><span data-stu-id="9826d-116">For info about installing and using the C++/WinRT Visual Studio Extension (VSIX) (which provides project template support, as well as C++/WinRT MSBuild properties and targets) see [Visual Studio support for C++/WinRT, and the VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix).</span></span>

## <a name="implement-singlethreadedobservablevectorlttgt"></a><span data-ttu-id="9826d-117">Implementieren von **single_threaded_observable_vector&lt;T&gt;**</span><span class="sxs-lookup"><span data-stu-id="9826d-117">Implement **single_threaded_observable_vector&lt;T&gt;**</span></span>
<span data-ttu-id="9826d-118">Es ist hilfreich, eine Observable-Vektor-Vorlage zu haben, die als nützliche, universell einsetzbare Implementierung von [**IObservableVector&lt;T&gt;**](/uwp/api/windows.foundation.collections.iobservablevector_t_) dient.</span><span class="sxs-lookup"><span data-stu-id="9826d-118">It will be good to have an observable vector template to serve as a useful, general-purpose implementation of  [**IObservableVector&lt;T&gt;**](/uwp/api/windows.foundation.collections.iobservablevector_t_).</span></span> <span data-ttu-id="9826d-119">Hier ist eine Klasse namens **single_threaded_observable_vector\<T\>**.</span><span class="sxs-lookup"><span data-stu-id="9826d-119">Below is a listing of a class called **single_threaded_observable_vector\<T\>**.</span></span>

> [!NOTE]
> <span data-ttu-id="9826d-120">Wenn Sie die [Windows 10 SDK Vorschau erstellen 17661](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK)installiert haben oder höher, klicken Sie dann Sie nur direkt können verwenden Sie die **Winrt::single_threaded_observable_vector\ < T\ >** Factory-Funktion anstelle der Code weiter unten.</span><span class="sxs-lookup"><span data-stu-id="9826d-120">If you've installed the [Windows 10 SDK Preview Build 17661](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK), or later, then you can just directly use the **winrt::single_threaded_observable_vector\<T\>** factory function instead of the code listing below.</span></span> <span data-ttu-id="9826d-121">Wenn Sie noch nicht auf diese Version des SDK befinden, klicken Sie dann werden einfach zu die Code Listing Version der **Winrt** -Funktion verwenden, wenn Sie sind zu wechseln.</span><span class="sxs-lookup"><span data-stu-id="9826d-121">If you're not already on that version of the SDK, then it will be easy to switch over from using the code listing version to the **winrt** function when you are.</span></span> <span data-ttu-id="9826d-122">Denken Sie daran, rufen Sie mit den unten aufgeführten Typ [**winrt::make**]() , sondern Sie stattdessen die Funktion **Winrt::single_threaded_observable_vector\ < T\ >** aufrufen.</span><span class="sxs-lookup"><span data-stu-id="9826d-122">Just remember that instead of calling [**winrt::make**]() with the type listed below, you instead call the **winrt::single_threaded_observable_vector\<T\>** function.</span></span>

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

<span data-ttu-id="9826d-123">Die **Append**-Funktion zeigt, wie das Ereignis [**IObservableVector&lt;T&gt;::VectorChanged**](/uwp/api/windows.foundation.collections.iobservablevector-1.vectorchanged) ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="9826d-123">The **Append** function illustrates how to raise the [**IObservableVector&lt;T&gt;::VectorChanged**](/uwp/api/windows.foundation.collections.iobservablevector-1.vectorchanged) event.</span></span>

```cppwinrt
m_changed(*this, make<args>(CollectionChange::ItemInserted, Size() - 1));
```

<span data-ttu-id="9826d-124">Die Ereignisargumente zeigen sowohl an, dass ein Element eingefügt wurde, als auch was sein Index ist (in diesem Fall das letzte Element).</span><span class="sxs-lookup"><span data-stu-id="9826d-124">The event arguments indicate both that an element was inserted, and also what its index is (the last element, in this case).</span></span> <span data-ttu-id="9826d-125">Diese Argumente ermöglichen es einem XAML-Items-Steuerelement, auf das Ereignis zu reagieren und sich optimal zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="9826d-125">These arguments enable a XAML items control to respond to the event and to refresh itself in the optimal way.</span></span>

## <a name="add-a-bookskus-collection-to-bookstoreviewmodel"></a><span data-ttu-id="9826d-126">Hinzufügen einer **BookSkus**-Collection zu **BookstoreViewModel**</span><span class="sxs-lookup"><span data-stu-id="9826d-126">Add a **BookSkus** collection to **BookstoreViewModel**</span></span>
<span data-ttu-id="9826d-127">In [XAML-Steuerelemente; Binden an eine C++/WinRT-Eigenschaft](binding-property.md) haben wir eine Eigenschaft vom Typ **BookSku** zu unserem Hauptansichtsmodell hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="9826d-127">In [XAML controls; bind to a C++/WinRT property](binding-property.md), we added a property of type **BookSku** to our main view model.</span></span> <span data-ttu-id="9826d-128">In diesem Schritt verwenden wir **single_threaded_observable_vector&lt;T&gt;**, um eine Observable-Collection von **BookSku** für dasselbe Ansichtsmodell zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="9826d-128">In this step, we'll use **single_threaded_observable_vector&lt;T&gt;** to help us implement an observable collection of **BookSku** on the same view model.</span></span>

<span data-ttu-id="9826d-129">Deklarieren Sie eine neue Eigenschaft in `BookstoreViewModel.idl`.</span><span class="sxs-lookup"><span data-stu-id="9826d-129">Declare a new property in `BookstoreViewModel.idl`.</span></span>

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

<span data-ttu-id="9826d-130">Speichern und erstellen Sie das Projekt.</span><span class="sxs-lookup"><span data-stu-id="9826d-130">Save and build.</span></span> <span data-ttu-id="9826d-131">Kopieren Sie die Zugriffs-Stubs aus `BookstoreViewModel.h` und `BookstoreViewModel.cpp` in den Ordner `Generated Files` und implementieren Sie sie.</span><span class="sxs-lookup"><span data-stu-id="9826d-131">Copy the accessor stubs from `BookstoreViewModel.h` and `BookstoreViewModel.cpp` in the `Generated Files` folder, and implement them.</span></span>

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

    Windows::Foundation::Collections::IVector<Windows::Foundation::IInspectable> BookstoreViewModel::BookSkus()
    {
        return m_bookSkus;
    }
...
```

## <a name="bind-a-listbox-to-the-bookskus-property"></a><span data-ttu-id="9826d-132">Binden einer Listbox an die **BookSkus**-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="9826d-132">Bind a ListBox to the **BookSkus** property</span></span>
<span data-ttu-id="9826d-133">Öffnen Sie `MainPage.xaml` mit dem XAML-Markup für unsere UI-Hauptseite.</span><span class="sxs-lookup"><span data-stu-id="9826d-133">Open `MainPage.xaml`, which contains the XAML markup for our main UI page.</span></span> <span data-ttu-id="9826d-134">Fügen Sie den folgende Markup-Code in dem **StackPanel** hinzu, indem sich der **Button** befindet.</span><span class="sxs-lookup"><span data-stu-id="9826d-134">Add the following markup inside the same **StackPanel** as the **Button**.</span></span>

```xaml
<ListBox ItemsSource="{x:Bind MainViewModel.BookSkus}">
    <ItemsControl.ItemTemplate>
        <DataTemplate x:DataType="local:BookSku">
            <TextBlock Text="{x:Bind Title, Mode=OneWay}"/>
        </DataTemplate>
    </ItemsControl.ItemTemplate>
</ListBox>
```

<span data-ttu-id="9826d-135">In `MainPage.cpp` fügen Sie dem **Click**-Ereignis-Handler eine Zeile Code hinzu, um ein Buch zur Collection hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="9826d-135">In `MainPage.cpp`, add a line of code to the **Click** event handler to append a book to the collection.</span></span>

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

<span data-ttu-id="9826d-136">Erstellen Sie nun das Projekt und führen Sie es aus.</span><span class="sxs-lookup"><span data-stu-id="9826d-136">Now build and run the project.</span></span> <span data-ttu-id="9826d-137">Klicken Sie auf die Schaltfläche, um den **Click**-Ereignis-Handler auszuführen.</span><span class="sxs-lookup"><span data-stu-id="9826d-137">Click the button to execute the **Click** event handler.</span></span> <span data-ttu-id="9826d-138">Wir haben gesehen, dass die Implementierung von **Append** ein Ereignis auslöst, um die Benutzeroberfläche wissen zu lassen, dass sich die Collection geändert hat. Die **ListBox** fragt die Collection erneut ab, um ihren eigenen **Items**-Wert zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="9826d-138">We saw that the implementation of **Append** raises an event to let the UI know that the collection has changed; and the **ListBox** re-queries the collection to update its own **Items** value.</span></span> <span data-ttu-id="9826d-139">Nach wie vor ändert sich der Titel eines der Bücher, und diese Titeländerung wird sowohl auf der Schaltfläche als auch in der Listbox angezeigt.</span><span class="sxs-lookup"><span data-stu-id="9826d-139">Just as before, the title of one of the books changes; and that title change is reflected both on the button and in the list box.</span></span>

## <a name="important-apis"></a><span data-ttu-id="9826d-140">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="9826d-140">Important APIs</span></span>
* [<span data-ttu-id="9826d-141">IObservableVector&lt;T&gt;::VectorChanged</span><span class="sxs-lookup"><span data-stu-id="9826d-141">IObservableVector&lt;T&gt;::VectorChanged</span></span>](/uwp/api/windows.foundation.collections.iobservablevector-1.vectorchanged)
* [<span data-ttu-id="9826d-142">winrt::make Funktionsvorlage</span><span class="sxs-lookup"><span data-stu-id="9826d-142">winrt::make function template</span></span>](/uwp/cpp-ref-for-winrt/make)

## <a name="related-topics"></a><span data-ttu-id="9826d-143">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="9826d-143">Related topics</span></span>
* [<span data-ttu-id="9826d-144">Verwenden von APIs mit C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="9826d-144">Consume APIs with C++/WinRT</span></span>](consume-apis.md)
* [<span data-ttu-id="9826d-145">Erstellen von APIs mit C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="9826d-145">Author APIs with C++/WinRT</span></span>](author-apis.md)
