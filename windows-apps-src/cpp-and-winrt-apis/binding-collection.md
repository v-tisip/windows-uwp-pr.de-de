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
ms.sourcegitcommit: c4d3115348c8b54fcc92aae8e18fdabc3deb301d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2018
ms.locfileid: "5409407"
---
# <a name="xaml-items-controls-bind-to-a-cwinrt-collection"></a>XAML-Items-Steuerelemente; Binden an eine C++/WinRT-Collection

Eine Collection, die effektiv an ein XAML-Items-Steuerelement gebunden werden kann, wird als *Observable*-Collection bezeichnet. Dieses Konzept basiert auf dem Software-Design-Muster, das als *Observer-Pattern* bekannt ist. Dieses Thema zeigt, wie Sie feststellbare Sammlungen im implementieren [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), und wie man XAML-Item-items-Steuerelemente an diese.

Diese exemplarische Vorgehensweise baut auf dem in [XAML-Steuerelemente; Binden an eine C++/WinRT-Eigenschaft](binding-property.md) erstellten Projekt auf, und sie ergänzt die in diesem Thema erläuterten Konzepte.

> [!IMPORTANT]
> Wichtige Konzepte und Begriffe, die Ihr Verständnis für die Verwendung von Laufzeitklassen mit C++/WinRT unterstützen, finden Sie unter [Verwenden von APIs mit C++/WinRT](consume-apis.md) und [Erstellen von APIs mit C++/WinRT](author-apis.md).

## <a name="what-does-observable-mean-for-a-collection"></a>Was bedeutet *observable* für eine Collection?
Wenn eine Laufzeitklasse, die eine Collection repräsentiert, das Ereignis [**IObservableVector&lt;T&gt;::VectorChanged**](/uwp/api/windows.foundation.collections.iobservablevector-1.vectorchanged) auslöst, wenn ein Element hinzugefügt oder entfernt wird, dann ist die Laufzeitklasse eine Observable-Collection. Ein XAML-Items-Steuerelement kann sich an diese Ereignisse binden und sie verarbeiten, indem es die aktualisierte Collection abruft und sich dann aktualisiert, um die aktuellen Elemente anzuzeigen.

> [!NOTE]
> Informationen zur Installation und Verwendung der C++/WinRT Visual Studio Extension (VSIX) (die Projektvorlagenunterstützung sowie C++/WinRT MSBuild-Eigenschaften und -Ziele bietet) finden Sie unter [Visual Studio-Unterstützung für C++/WinRT und VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix).

## <a name="add-a-bookskus-collection-to-bookstoreviewmodel"></a>Hinzufügen einer **BookSkus**-Collection zu **BookstoreViewModel**

In [XAML-Steuerelemente; Binden an eine C++/WinRT-Eigenschaft](binding-property.md) haben wir eine Eigenschaft vom Typ **BookSku** zu unserem Hauptansichtsmodell hinzugefügt. In diesem Schritt verwenden wir die [**winrt::single_threaded_observable_vector**](/uwp/cpp-ref-for-winrt/single-threaded-observable-vector) Factory-Funktionsvorlage um zu helfen, eine Observable-Collection von **booksku-Objekten** für dasselbe Ansichtsmodell zu implementieren.

> [!NOTE]
> Wenn Sie noch nicht das Windows SDK-Version 10.0.17763.0 (Windows 10, Version 1809 installiert) oder höher ist, dann finden Sie unter [besitzen Sie eine ältere Version von Windows SDK](/uwp/cpp-ref-for-winrt/single-threaded-observable-vector#if-you-have-an-older-version-of-the-windows-sdk) für eine Liste der eine Observable-Vektor-Vorlage, die Sie anstelle von **winrt::single_ verwenden können Threaded_observable_vector**.

Deklarieren Sie eine neue Eigenschaft in `BookstoreViewModel.idl`.

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
> Beachten Sie in den oben genannten MIDL 3.0-Eintrag, dass der Typ der Eigenschaft **BookSkus** [**IObservableVector**](/uwp/api/windows.foundation.collections.ivector_t_) von [**IInspectable**](/windows/desktop/api/inspectable/nn-inspectable-iinspectable)ist. Im nächsten Abschnitt dieses Themas verwenden wir die Quelle von Elementen von einer [**ListBox**](/uwp/api/windows.ui.xaml.controls.listbox) **BookSkus**binden werden. Ein Listenfeld ist ein Elementsteuerelement und um die Eigenschaft [**ItemsControl.ItemsSource**](/uwp/api/windows.ui.xaml.controls.itemscontrol.itemssource) richtig festzulegen, müssen Sie es auf einen Wert vom Typ **IObservableVector** (oder **IVector**) festgelegt **IInspectable**, oder eine Interoperabilität Typ wie z. B. [** IBindableObservableVector**](/uwp/api/windows.ui.xaml.interop.ibindableobservablevector).

Speichern und erstellen Sie das Projekt. Kopieren Sie die Zugriffs-Stubs aus `BookstoreViewModel.h` und `BookstoreViewModel.cpp` in den Ordner `Generated Files` und implementieren Sie sie.

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
    MainViewModel().BookSkus().Append(winrt::make<Bookstore::implementation::BookSku>(L"Moby Dick"));
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
