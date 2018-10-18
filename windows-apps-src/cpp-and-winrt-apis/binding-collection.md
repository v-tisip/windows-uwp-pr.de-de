---
author: stevewhims
description: Eine Collection, die effektiv an ein XAML-Items-Steuerelement gebunden werden kann, wird als *Observable*-Collection bezeichnet. Dieses Thema zeigt, wie man eine Observable-Collection implementiert und nutzt und wie man ein XAML-Items-Steuerelement daran bindet.
title: XAML-Items-Steuerelemente; Binden an eine C++/WinRT-Collection
ms.author: stwhi
ms.date: 10/03/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp, standard, c++, cpp, winrt, projizierung, XAML, steuerelement, binden, collection
ms.localizationpriority: medium
ms.openlocfilehash: 22594c1cfc503b28163d9fca1f46a6861a4f59ad
ms.sourcegitcommit: e16c9845b52d5bd43fc02bbe92296a9682d96926
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2018
ms.locfileid: "4967027"
---
# <a name="xaml-items-controls-bind-to-a-cwinrt-collection"></a><span data-ttu-id="85aff-105">XAML-Items-Steuerelemente; Binden an eine C++/WinRT-Collection</span><span class="sxs-lookup"><span data-stu-id="85aff-105">XAML items controls; bind to a C++/WinRT collection</span></span>

<span data-ttu-id="85aff-106">Eine Collection, die effektiv an ein XAML-Items-Steuerelement gebunden werden kann, wird als *Observable*-Collection bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="85aff-106">A collection that can be effectively bound to a XAML items control is known as an *observable* collection.</span></span> <span data-ttu-id="85aff-107">Dieses Konzept basiert auf dem Software-Design-Muster, das als *Observer-Pattern* bekannt ist.</span><span class="sxs-lookup"><span data-stu-id="85aff-107">This idea is based on the software design pattern known as the *observer pattern*.</span></span> <span data-ttu-id="85aff-108">Dieses Thema zeigt, wie Sie feststellbare Sammlungen im implementieren [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), und wie man XAML-Item-items-Steuerelemente an diese.</span><span class="sxs-lookup"><span data-stu-id="85aff-108">This topic shows how to implement observable collections in [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), and how to bind XAML items controls to them.</span></span>

<span data-ttu-id="85aff-109">Diese exemplarische Vorgehensweise baut auf dem in [XAML-Steuerelemente; Binden an eine C++/WinRT-Eigenschaft](binding-property.md) erstellten Projekt auf, und sie ergänzt die in diesem Thema erläuterten Konzepte.</span><span class="sxs-lookup"><span data-stu-id="85aff-109">This walkthrough builds on the project created in [XAML controls; bind to a C++/WinRT property](binding-property.md), and it adds to the concepts explained in that topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="85aff-110">Wichtige Konzepte und Begriffe, die Ihr Verständnis für die Verwendung von Laufzeitklassen mit C++/WinRT unterstützen, finden Sie unter [Verwenden von APIs mit C++/WinRT](consume-apis.md) und [Erstellen von APIs mit C++/WinRT](author-apis.md).</span><span class="sxs-lookup"><span data-stu-id="85aff-110">For essential concepts and terms that support your understanding of how to consume and author runtime classes with C++/WinRT, see [Consume APIs with C++/WinRT](consume-apis.md) and [Author APIs with C++/WinRT](author-apis.md).</span></span>

## <a name="what-does-observable-mean-for-a-collection"></a><span data-ttu-id="85aff-111">Was bedeutet *observable* für eine Collection?</span><span class="sxs-lookup"><span data-stu-id="85aff-111">What does *observable* mean for a collection?</span></span>
<span data-ttu-id="85aff-112">Wenn eine Laufzeitklasse, die eine Collection repräsentiert, das Ereignis [**IObservableVector&lt;T&gt;::VectorChanged**](/uwp/api/windows.foundation.collections.iobservablevector-1.vectorchanged) auslöst, wenn ein Element hinzugefügt oder entfernt wird, dann ist die Laufzeitklasse eine Observable-Collection.</span><span class="sxs-lookup"><span data-stu-id="85aff-112">If a runtime class that represents a collection chooses to raise the [**IObservableVector&lt;T&gt;::VectorChanged**](/uwp/api/windows.foundation.collections.iobservablevector-1.vectorchanged) event whenever an element is added to it or removed from it, then the runtime class is an observable collection.</span></span> <span data-ttu-id="85aff-113">Ein XAML-Items-Steuerelement kann sich an diese Ereignisse binden und sie verarbeiten, indem es die aktualisierte Collection abruft und sich dann aktualisiert, um die aktuellen Elemente anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="85aff-113">A XAML items control can bind to, and handle, these events by retrieving the updated collection and then updating itself to show the current elements.</span></span>

> [!NOTE]
> <span data-ttu-id="85aff-114">Informationen zur Installation und Verwendung der C++/WinRT Visual Studio Extension (VSIX) (die Projektvorlagenunterstützung sowie C++/WinRT MSBuild-Eigenschaften und -Ziele bietet) finden Sie unter [Visual Studio-Unterstützung für C++/WinRT und VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix).</span><span class="sxs-lookup"><span data-stu-id="85aff-114">For info about installing and using the C++/WinRT Visual Studio Extension (VSIX) (which provides project template support, as well as C++/WinRT MSBuild properties and targets) see [Visual Studio support for C++/WinRT, and the VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix).</span></span>

## <a name="add-a-bookskus-collection-to-bookstoreviewmodel"></a><span data-ttu-id="85aff-115">Hinzufügen einer **BookSkus**-Collection zu **BookstoreViewModel**</span><span class="sxs-lookup"><span data-stu-id="85aff-115">Add a **BookSkus** collection to **BookstoreViewModel**</span></span>

<span data-ttu-id="85aff-116">In [XAML-Steuerelemente; Binden an eine C++/WinRT-Eigenschaft](binding-property.md) haben wir eine Eigenschaft vom Typ **BookSku** zu unserem Hauptansichtsmodell hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="85aff-116">In [XAML controls; bind to a C++/WinRT property](binding-property.md), we added a property of type **BookSku** to our main view model.</span></span> <span data-ttu-id="85aff-117">In diesem Schritt verwenden wir die [**winrt::single_threaded_observable_vector**](/uwp/cpp-ref-for-winrt/single-threaded-observable-vector) Factory-Funktionsvorlage um zu helfen, eine Observable-Collection von **booksku-Objekten** für dasselbe Ansichtsmodell zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="85aff-117">In this step, we'll use the [**winrt::single_threaded_observable_vector**](/uwp/cpp-ref-for-winrt/single-threaded-observable-vector) factory function template to help us implement an observable collection of **BookSku** on the same view model.</span></span>

> [!NOTE]
> <span data-ttu-id="85aff-118">Wenn Sie noch nicht das Windows SDK-Version 10.0.17763.0 (Windows 10, Version 1809 installiert) oder höher ist, dann finden Sie unter [besitzen Sie eine ältere Version von Windows SDK](/uwp/cpp-ref-for-winrt/single-threaded-observable-vector#if-you-have-an-older-version-of-the-windows-sdk) für eine Liste der eine Observable-Vektor-Vorlage, die Sie anstelle von **winrt::single_ verwenden können Threaded_observable_vector**.</span><span class="sxs-lookup"><span data-stu-id="85aff-118">If you haven't installed the Windows SDK version 10.0.17763.0 (Windows 10, version 1809), or later, then see [If you have an older version of the Windows SDK](/uwp/cpp-ref-for-winrt/single-threaded-observable-vector#if-you-have-an-older-version-of-the-windows-sdk) for a listing of an observable vector template that you can use instead of **winrt::single_threaded_observable_vector**.</span></span>

<span data-ttu-id="85aff-119">Deklarieren Sie eine neue Eigenschaft in `BookstoreViewModel.idl`.</span><span class="sxs-lookup"><span data-stu-id="85aff-119">Declare a new property in `BookstoreViewModel.idl`.</span></span>

```idl
// BookstoreViewModel.idl
...
runtimeclass BookstoreViewModel
{
    BookSku BookSku{ get; };
    Windows.Foundation.Collections.IObservableVector<IInspectable> BookSkus{ get; };
}
...
```

> [!IMPORTANT]
> <span data-ttu-id="85aff-120">Beachten Sie in den oben genannten MIDL 3.0-Eintrag, dass der Typ der Eigenschaft **BookSkus** [**IObservableVector**](/uwp/api/windows.foundation.collections.ivector_t_) von [**IInspectable**](/windows/desktop/api/inspectable/nn-inspectable-iinspectable)ist.</span><span class="sxs-lookup"><span data-stu-id="85aff-120">In the MIDL 3.0 listing above, note that the type of the **BookSkus** property is [**IObservableVector**](/uwp/api/windows.foundation.collections.ivector_t_) of [**IInspectable**](/windows/desktop/api/inspectable/nn-inspectable-iinspectable).</span></span> <span data-ttu-id="85aff-121">Im nächsten Abschnitt dieses Themas verwenden wir die Quelle von Elementen von einer [**ListBox**](/uwp/api/windows.ui.xaml.controls.listbox) **BookSkus**binden werden.</span><span class="sxs-lookup"><span data-stu-id="85aff-121">In the next section of this topic, we'll be binding the items source of a [**ListBox**](/uwp/api/windows.ui.xaml.controls.listbox) to **BookSkus**.</span></span> <span data-ttu-id="85aff-122">Ein Listenfeld ist ein Elementsteuerelement und um die Eigenschaft [**ItemsControl.ItemsSource**](/uwp/api/windows.ui.xaml.controls.itemscontrol.itemssource) richtig festzulegen, müssen Sie es auf einen Wert vom Typ **IObservableVector** (oder **IVector**) festgelegt **IInspectable**, oder eine Interoperabilität Typ wie z. B. [\*\* IBindableObservableVector\*\*](/uwp/api/windows.ui.xaml.interop.ibindableobservablevector).</span><span class="sxs-lookup"><span data-stu-id="85aff-122">A list box is an items control, and to correctly set the [**ItemsControl.ItemsSource**](/uwp/api/windows.ui.xaml.controls.itemscontrol.itemssource) property, you need to set it to a value of type **IObservableVector** (or **IVector**) of **IInspectable**, or of an interoperability type such as [**IBindableObservableVector**](/uwp/api/windows.ui.xaml.interop.ibindableobservablevector).</span></span>

<span data-ttu-id="85aff-123">Speichern und erstellen Sie das Projekt.</span><span class="sxs-lookup"><span data-stu-id="85aff-123">Save and build.</span></span> <span data-ttu-id="85aff-124">Kopieren Sie die Zugriffs-Stubs aus `BookstoreViewModel.h` und `BookstoreViewModel.cpp` in den Ordner `Generated Files` und implementieren Sie sie.</span><span class="sxs-lookup"><span data-stu-id="85aff-124">Copy the accessor stubs from `BookstoreViewModel.h` and `BookstoreViewModel.cpp` in the `Generated Files` folder, and implement them.</span></span>

```cppwinrt
// BookstoreViewModel.h
...
struct BookstoreViewModel : BookstoreViewModelT<BookstoreViewModel>
{
    BookstoreViewModel();

    Bookstore::BookSku BookSku();

    Windows::Foundation::Collections::IObservableVector<Windows::Foundation::IInspectable> BookSkus();

private:
    Bookstore::BookSku m_bookSku{ nullptr };
    Windows::Foundation::Collections::IObservableVector<Windows::Foundation::IInspectable> m_bookSkus;
};
...
```

```cppwinrt
// BookstoreViewModel.cpp
...
BookstoreViewModel::BookstoreViewModel()
{
    m_bookSku = winrt::make<Bookstore::implementation::BookSku>(L"Atticus");
    m_bookSkus = winrt::single_threaded_observable_vector<Windows::Foundation::IInspectable>();
    m_bookSkus.Append(m_bookSku);
}

Bookstore::BookSku BookstoreViewModel::BookSku()
{
    return m_bookSku;
}

Windows::Foundation::Collections::IObservableVector<Windows::Foundation::IInspectable> BookstoreViewModel::BookSkus()
{
    return m_bookSkus;
}
...
```

## <a name="bind-a-listbox-to-the-bookskus-property"></a><span data-ttu-id="85aff-125">Binden einer Listbox an die **BookSkus**-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="85aff-125">Bind a ListBox to the **BookSkus** property</span></span>
<span data-ttu-id="85aff-126">Öffnen Sie `MainPage.xaml` mit dem XAML-Markup für unsere UI-Hauptseite.</span><span class="sxs-lookup"><span data-stu-id="85aff-126">Open `MainPage.xaml`, which contains the XAML markup for our main UI page.</span></span> <span data-ttu-id="85aff-127">Fügen Sie den folgende Markup-Code in dem **StackPanel** hinzu, indem sich der **Button** befindet.</span><span class="sxs-lookup"><span data-stu-id="85aff-127">Add the following markup inside the same **StackPanel** as the **Button**.</span></span>

```xaml
<ListBox ItemsSource="{x:Bind MainViewModel.BookSkus}">
    <ItemsControl.ItemTemplate>
        <DataTemplate x:DataType="local:BookSku">
            <TextBlock Text="{x:Bind Title, Mode=OneWay}"/>
        </DataTemplate>
    </ItemsControl.ItemTemplate>
</ListBox>
```

<span data-ttu-id="85aff-128">In `MainPage.cpp` fügen Sie dem **Click**-Ereignis-Handler eine Zeile Code hinzu, um ein Buch zur Collection hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="85aff-128">In `MainPage.cpp`, add a line of code to the **Click** event handler to append a book to the collection.</span></span>

```cppwinrt
// MainPage.cpp
...
void MainPage::ClickHandler(IInspectable const&, RoutedEventArgs const&)
{
    MainViewModel().BookSku().Title(L"To Kill a Mockingbird");
    MainViewModel().BookSkus().Append(winrt::make<Bookstore::implementation::BookSku>(L"Moby Dick"));
}
...
```

<span data-ttu-id="85aff-129">Erstellen Sie nun das Projekt und führen Sie es aus.</span><span class="sxs-lookup"><span data-stu-id="85aff-129">Now build and run the project.</span></span> <span data-ttu-id="85aff-130">Klicken Sie auf die Schaltfläche, um den **Click**-Ereignis-Handler auszuführen.</span><span class="sxs-lookup"><span data-stu-id="85aff-130">Click the button to execute the **Click** event handler.</span></span> <span data-ttu-id="85aff-131">Wir haben gesehen, dass die Implementierung von **Append** ein Ereignis auslöst, um die Benutzeroberfläche wissen zu lassen, dass sich die Collection geändert hat. Die **ListBox** fragt die Collection erneut ab, um ihren eigenen **Items**-Wert zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="85aff-131">We saw that the implementation of **Append** raises an event to let the UI know that the collection has changed; and the **ListBox** re-queries the collection to update its own **Items** value.</span></span> <span data-ttu-id="85aff-132">Nach wie vor ändert sich der Titel eines der Bücher, und diese Titeländerung wird sowohl auf der Schaltfläche als auch in der Listbox angezeigt.</span><span class="sxs-lookup"><span data-stu-id="85aff-132">Just as before, the title of one of the books changes; and that title change is reflected both on the button and in the list box.</span></span>

## <a name="important-apis"></a><span data-ttu-id="85aff-133">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="85aff-133">Important APIs</span></span>
* [<span data-ttu-id="85aff-134">IObservableVector&lt;T&gt;::VectorChanged</span><span class="sxs-lookup"><span data-stu-id="85aff-134">IObservableVector&lt;T&gt;::VectorChanged</span></span>](/uwp/api/windows.foundation.collections.iobservablevector-1.vectorchanged)
* [<span data-ttu-id="85aff-135">winrt::make Funktionsvorlage</span><span class="sxs-lookup"><span data-stu-id="85aff-135">winrt::make function template</span></span>](/uwp/cpp-ref-for-winrt/make)

## <a name="related-topics"></a><span data-ttu-id="85aff-136">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="85aff-136">Related topics</span></span>
* [<span data-ttu-id="85aff-137">Verwenden von APIs mit C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="85aff-137">Consume APIs with C++/WinRT</span></span>](consume-apis.md)
* [<span data-ttu-id="85aff-138">Erstellen von APIs mit C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="85aff-138">Author APIs with C++/WinRT</span></span>](author-apis.md)
