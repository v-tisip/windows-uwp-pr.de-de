---
author: mcleblanc
ms.assetid: A9D54DEC-CD1B-4043-ADE4-32CD4977D1BF
title: Übersicht Datenbindung
description: In diesem Thema erfahren Sie, wie Sie in einer UWP-App (Universelle Windows-Plattform) ein Steuerelement (oder ein anderes Benutzeroberflächenelement) an ein einzelnes Element oder ein Steuerelement eines Elements an eine Sammlung von Elementen binden.
ms.author: markl
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp
ms.localizationpriority: medium
ms.openlocfilehash: fd9b9b4f1c6ddd48db8801d714568ccb011ea7e5
ms.sourcegitcommit: 4b522af988273946414a04fbbd1d7fde40f8ba5e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2018
ms.locfileid: "1494047"
---
<a name="data-binding-overview"></a><span data-ttu-id="24ab4-104">Übersicht über Datenbindung</span><span class="sxs-lookup"><span data-stu-id="24ab4-104">Data binding overview</span></span>
=====================



<span data-ttu-id="24ab4-105">In diesem Thema erfahren Sie, wie Sie in einer UWP-App (Universelle Windows-Plattform) ein Steuerelement (oder ein anderes Benutzeroberflächenelement) an ein einzelnes Element oder ein Elementsteuerelement an eine Sammlung von Elementen binden.</span><span class="sxs-lookup"><span data-stu-id="24ab4-105">This topic shows you how to bind a control (or other UI element) to a single item or bind an items control to a collection of items in a Universal Windows Platform (UWP) app.</span></span> <span data-ttu-id="24ab4-106">Darüber hinaus wird erläutert, wie Sie die Anzeige von Elementen steuern, eine Detailansicht auf Grundlage einer Auswahl implementieren und Daten für die Anzeige umwandeln.</span><span class="sxs-lookup"><span data-stu-id="24ab4-106">In addition, we show how to control the rendering of items, implement a details view based on a selection, and convert data for display.</span></span> <span data-ttu-id="24ab4-107">Ausführliche Informationen finden Sie unter [Datenbindung im Detail](data-binding-in-depth.md).</span><span class="sxs-lookup"><span data-stu-id="24ab4-107">For more detailed info, see [Data binding in depth](data-binding-in-depth.md).</span></span>

<a name="prerequisites"></a><span data-ttu-id="24ab4-108">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="24ab4-108">Prerequisites</span></span>
-------------------------------------------------------------------------------------------------------------

<span data-ttu-id="24ab4-109">In diesem Thema wird vorausgesetzt, dass Sie mit dem Erstellen von UWP-Apps vertraut sind.</span><span class="sxs-lookup"><span data-stu-id="24ab4-109">This topic assumes that you know how to create a basic UWP app.</span></span> <span data-ttu-id="24ab4-110">Eine Anleitung zum Erstellen Ihrer ersten UWP-App finden Sie unter [Erste Schrittemit Windows-Apps](https://developer.microsoft.com/windows/getstarted).</span><span class="sxs-lookup"><span data-stu-id="24ab4-110">For instructions on creating your first UWP app, see [Get started with Windows apps](https://developer.microsoft.com/windows/getstarted).</span></span>

<a name="create-the-project"></a><span data-ttu-id="24ab4-111">Erstellen des Projekts</span><span class="sxs-lookup"><span data-stu-id="24ab4-111">Create the project</span></span>
---------------------------------------------------------------------------------------------------------------------------------

<span data-ttu-id="24ab4-112">Erstellen Sie ein neues Projekt vom Typ **Leere Anwendung (Windows Universal)**.</span><span class="sxs-lookup"><span data-stu-id="24ab4-112">Create a new **Blank Application (Windows Universal)** project.</span></span> <span data-ttu-id="24ab4-113">Nennen Sie sie „Schnellstart“.</span><span class="sxs-lookup"><span data-stu-id="24ab4-113">Name it "Quickstart".</span></span>

<a name="binding-to-a-single-item"></a><span data-ttu-id="24ab4-114">Binden an ein einzelnes Element</span><span class="sxs-lookup"><span data-stu-id="24ab4-114">Binding to a single item</span></span>
---------------------------------------------------------------------------------------------------------------------------------------------------------

<span data-ttu-id="24ab4-115">Jede Bindung besteht aus einem Bindungsziel und einer Bindungsquelle.</span><span class="sxs-lookup"><span data-stu-id="24ab4-115">Every binding consists of a binding target and a binding source.</span></span> <span data-ttu-id="24ab4-116">In der Regel ist das Ziel eine Eigenschaft eines Steuerelements oder anderen Benutzeroberflächenelements, und die Quelle ist eine Eigenschaft einer Klasseninstanz (ein Datenmodell oder ein Ansichtsmodell).</span><span class="sxs-lookup"><span data-stu-id="24ab4-116">Typically, the target is a property of a control or other UI element, and the source is a property of a class instance (a data model, or a view model).</span></span> <span data-ttu-id="24ab4-117">In diesem Beispiel wird veranschaulicht, wie Sie ein Steuerelement an ein einzelnes Element binden.</span><span class="sxs-lookup"><span data-stu-id="24ab4-117">This example shows how to bind a control to a single item.</span></span> <span data-ttu-id="24ab4-118">Das Ziel ist die **Text**-Eigenschaft eines **TextBlock**.</span><span class="sxs-lookup"><span data-stu-id="24ab4-118">The target is the **Text** property of a **TextBlock**.</span></span> <span data-ttu-id="24ab4-119">Die Quelle ist eine Instanz einer einfachen Klasse namens **Recording**, die eine Audioaufnahme darstellt.</span><span class="sxs-lookup"><span data-stu-id="24ab4-119">The source is an instance of a simple class named **Recording** that represents an audio recording.</span></span> <span data-ttu-id="24ab4-120">Befassen wir uns zuerst mit der Klasse.</span><span class="sxs-lookup"><span data-stu-id="24ab4-120">Let's look at the class first.</span></span>

<span data-ttu-id="24ab4-121">Fügen Sie Ihrem Projekt eine neue Klasse hinzu, nennen Sie sie „Recording.cs“ (bei Verwendung von C#, im Folgenden finden Sie auch C++-Codeausschnitte), und fügen Sie ihr diesen Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="24ab4-121">Add a new class to your project, name it Recording.cs (if you're using C#, C++ snippets provided below as well), and add this code to it.</span></span>

> [!div class="tabbedCodeSnippets"]
```csharp
namespace Quickstart
{
    public class Recording
    {
        public string ArtistName { get; set; }
        public string CompositionName { get; set; }
        public DateTime ReleaseDateTime { get; set; }
        public Recording()
        {
            this.ArtistName = "Wolfgang Amadeus Mozart";
            this.CompositionName = "Andante in C for Piano";
            this.ReleaseDateTime = new DateTime(1761, 1, 1);
        }
        public string OneLineSummary
        {
            get
            {
                return $"{this.CompositionName} by {this.ArtistName}, released: "
                    + this.ReleaseDateTime.ToString("d");
            }
        }
    }
    public class RecordingViewModel
    {
        private Recording defaultRecording = new Recording();
        public Recording DefaultRecording { get { return this.defaultRecording; } }
    }
}
```
```cpp
    #include <sstream>
    namespace Quickstart
    {
        public ref class Recording sealed
        {
        private:
            Platform::String^ artistName;
            Platform::String^ compositionName;
            Windows::Globalization::Calendar^ releaseDateTime;
        public:
            Recording(Platform::String^ artistName, Platform::String^ compositionName,
                Windows::Globalization::Calendar^ releaseDateTime) :
                artistName{ artistName },
                compositionName{ compositionName },
                releaseDateTime{ releaseDateTime } {}
            property Platform::String^ ArtistName
            {
                Platform::String^ get() { return this->artistName; }
            }
            property Platform::String^ CompositionName
            {
                Platform::String^ get() { return this->compositionName; }
            }
            property Windows::Globalization::Calendar^ ReleaseDateTime
            {
                Windows::Globalization::Calendar^ get() { return this->releaseDateTime; }
            }
            property Platform::String^ OneLineSummary
            {
                Platform::String^ get()
                {
                    std::wstringstream wstringstream;
                    wstringstream << this->CompositionName->Data();
                    wstringstream << L" by " << this->ArtistName->Data();
                    wstringstream << L", released: " << this->ReleaseDateTime->MonthAsNumericString()->Data();
                    wstringstream << L"/" << this->ReleaseDateTime->DayAsString()->Data();
                    wstringstream << L"/" << this->ReleaseDateTime->YearAsString()->Data();
                    return ref new Platform::String(wstringstream.str().c_str());
                }
            }
        };
        public ref class RecordingViewModel sealed
        {
        private:
            Recording^ defaultRecording;
        public:
            RecordingViewModel()
            {
                Windows::Globalization::Calendar^ releaseDateTime = ref new Windows::Globalization::Calendar();
                releaseDateTime->Month = 1;
                releaseDateTime->Day = 1;
                releaseDateTime->Year = 1761;
                this->defaultRecording = ref new Recording{ L"Wolfgang Amadeus Mozart", L"Andante in C for Piano", releaseDateTime };
            }
            property Recording^ DefaultRecording
            {
                Recording^ get() { return this->defaultRecording; };
            }
        };
    }
```

<span data-ttu-id="24ab4-122">Machen Sie als Nächstes die Bindungsquellklasse aus der Klasse verfügbar, die die Markupseite darstellt.</span><span class="sxs-lookup"><span data-stu-id="24ab4-122">Next, expose the binding source class from the class that represents your page of markup.</span></span> <span data-ttu-id="24ab4-123">Zu diesem Zweck fügen Sie eine Eigenschaft vom Typ **RecordingViewModel** zu **MainPage** hinzu.</span><span class="sxs-lookup"><span data-stu-id="24ab4-123">We do that by adding a property of type **RecordingViewModel** to **MainPage**.</span></span>

> [!div class="tabbedCodeSnippets"]
```csharp
    namespace Quickstart
    {
        public sealed partial class MainPage : Page
        {
            public MainPage()
            {
                this.InitializeComponent();
                this.ViewModel = new RecordingViewModel();
            }
            public RecordingViewModel ViewModel { get; set; }
        }
    }
```
```cpp
    namespace Quickstart
    {
        public ref class MainPage sealed
        {
        private:
            RecordingViewModel^ viewModel;
        public:
            MainPage()
            {
                InitializeComponent();
                this->viewModel = ref new RecordingViewModel();
            }
            property RecordingViewModel^ ViewModel
            {
                RecordingViewModel^ get() { return this->viewModel; };
            }
        };
    }
```

<span data-ttu-id="24ab4-124">Der letzte Codeteil ist das Binden eines **TextBlock** an die **ViewModel.DefaultRecording.OneLiner**-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="24ab4-124">The last piece is to bind a **TextBlock** to the **ViewModel.DefaultRecording.OneLiner** property.</span></span>

```xml
    <Page x:Class="Quickstart.MainPage" ... >
        <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
            <TextBlock Text="{x:Bind ViewModel.DefaultRecording.OneLineSummary}"
            HorizontalAlignment="Center"
            VerticalAlignment="Center"/>
        </Grid>
    </Page>
```

<span data-ttu-id="24ab4-125">Dies ist das Ergebnis.</span><span class="sxs-lookup"><span data-stu-id="24ab4-125">Here's the result.</span></span>

![Binden eines Textblocks](images/xaml-databinding0.png)

<a name="binding-to-a-collection-of-items"></a><span data-ttu-id="24ab4-127">Binden an eine Sammlung von Elementen</span><span class="sxs-lookup"><span data-stu-id="24ab4-127">Binding to a collection of items</span></span>
------------------------------------------------------------------------------------------------------------------

<span data-ttu-id="24ab4-128">Ein häufiges Szenario ist das Binden an eine Sammlung von Geschäftsobjekten.</span><span class="sxs-lookup"><span data-stu-id="24ab4-128">A common scenario is to bind to a collection of business objects.</span></span> <span data-ttu-id="24ab4-129">In C# und Visual Basic stellt die generische [**ObservableCollection&lt;T&gt;**](https://msdn.microsoft.com/library/windows/apps/xaml/ms668604.aspx)-Klasse eine gute Wahl für die Datenbindung bei Sammlungen dar, da sie die  [**INotifyPropertyChanged**](https://msdn.microsoft.com/library/windows/apps/xaml/system.componentmodel.inotifypropertychanged.aspx)-Schnittstelle und die [**INotifyCollectionChanged**](https://msdn.microsoft.com/library/windows/apps/xaml/system.collections.specialized.inotifycollectionchanged.aspx)-Schnittstelle implementiert.</span><span class="sxs-lookup"><span data-stu-id="24ab4-129">In C# and Visual Basic, the generic [**ObservableCollection&lt;T&gt;**](https://msdn.microsoft.com/library/windows/apps/xaml/ms668604.aspx) class is a good collection choice for data binding, because it implements the [**INotifyPropertyChanged**](https://msdn.microsoft.com/library/windows/apps/xaml/system.componentmodel.inotifypropertychanged.aspx) and [**INotifyCollectionChanged**](https://msdn.microsoft.com/library/windows/apps/xaml/system.collections.specialized.inotifycollectionchanged.aspx) interfaces.</span></span> <span data-ttu-id="24ab4-130">Diese Schnittstellen bieten eine Änderungsbenachrichtigung für Bindungen, wenn Elemente hinzugefügt oder entfernt werden oder eine Eigenschaft der Liste selbst geändert wird.</span><span class="sxs-lookup"><span data-stu-id="24ab4-130">These interfaces provide change notification to bindings when items are added or removed or a property of the list itself changes.</span></span> <span data-ttu-id="24ab4-131">Wenn Ihre gebundenen Steuerelemente bei Änderungen an Eigenschaften von Objekten in der Sammlung aktualisiert werden sollen, muss das Geschäftsobjekt auch **INotifyPropertyChanged** implementieren.</span><span class="sxs-lookup"><span data-stu-id="24ab4-131">If you want your bound controls to update with changes to properties of objects in the collection, the business object should also implement **INotifyPropertyChanged**.</span></span> <span data-ttu-id="24ab4-132">Weitere Informationen finden Sie unter [Datenbindung im Detail](data-binding-in-depth.md).</span><span class="sxs-lookup"><span data-stu-id="24ab4-132">For more info, see [Data binding in depth](data-binding-in-depth.md).</span></span>

<span data-ttu-id="24ab4-133">In diesem nächsten Beispiel wird eine [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878) an eine Sammlung von `Recording`-Objekten gebunden.</span><span class="sxs-lookup"><span data-stu-id="24ab4-133">This next example binds a [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878) to a collection of `Recording` objects.</span></span> <span data-ttu-id="24ab4-134">Beginnen wir, indem wir die Sammlung zum Ansichtsmodell hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="24ab4-134">Let's start by adding the collection to our view model.</span></span> <span data-ttu-id="24ab4-135">Fügen Sie einfach diese neuen Member zur **RecordingViewModel**-Klasse hinzu.</span><span class="sxs-lookup"><span data-stu-id="24ab4-135">Just add these new members to the **RecordingViewModel** class.</span></span>

> [!div class="tabbedCodeSnippets"]
```csharp
    public class RecordingViewModel
    {
        ...
        private ObservableCollection<Recording> recordings = new ObservableCollection<Recording>();
        public ObservableCollection<Recording> Recordings { get { return this.recordings; } }
        public RecordingViewModel()
        {
            this.recordings.Add(new Recording() { ArtistName = "Johann Sebastian Bach",
            CompositionName = "Mass in B minor", ReleaseDateTime = new DateTime(1748, 7, 8) });
            this.recordings.Add(new Recording() { ArtistName = "Ludwig van Beethoven",
            CompositionName = "Third Symphony", ReleaseDateTime = new DateTime(1805, 2, 11) });
            this.recordings.Add(new Recording() { ArtistName = "George Frideric Handel",
            CompositionName = "Serse", ReleaseDateTime = new DateTime(1737, 12, 3) });
        }
    }
```
```cpp
    public ref class RecordingViewModel sealed
    {
    private:
        ...
        Windows::Foundation::Collections::IVector<Recording^>^ recordings;
    public:
        RecordingViewModel()
        {
            ...
            releaseDateTime = ref new Windows::Globalization::Calendar();
            releaseDateTime->Month = 7;
            releaseDateTime->Day = 8;
            releaseDateTime->Year = 1748;
            Recording^ recording = ref new Recording{ L"Johann Sebastian Bach", L"Mass in B minor", releaseDateTime };
            this->Recordings->Append(recording);
            releaseDateTime = ref new Windows::Globalization::Calendar();
            releaseDateTime->Month = 2;
            releaseDateTime->Day = 11;
            releaseDateTime->Year = 1805;
            recording = ref new Recording{ L"Ludwig van Beethoven", L"Third Symphony", releaseDateTime };
            this->Recordings->Append(recording);
            releaseDateTime = ref new Windows::Globalization::Calendar();
            releaseDateTime->Month = 12;
            releaseDateTime->Day = 3;
            releaseDateTime->Year = 1737;
            recording = ref new Recording{ L"George Frideric Handel", L"Serse", releaseDateTime };
            this->Recordings->Append(recording);
        }
        ...
        property Windows::Foundation::Collections::IVector<Recording^>^ Recordings
        {
            Windows::Foundation::Collections::IVector<Recording^>^ get()
            {
                if (this->recordings == nullptr)
                {
                    this->recordings = ref new Platform::Collections::Vector<Recording^>();
                }
                return this->recordings;
            };
        }
    };
```

<span data-ttu-id="24ab4-136">Binden Sie dann eine [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878) an die **ViewModel.Recordings**-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="24ab4-136">And then bind a [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878) to the **ViewModel.Recordings** property.</span></span>

```xml
<Page x:Class="Quickstart.MainPage" ... >
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
        <ListView ItemsSource="{x:Bind ViewModel.Recordings}"
        HorizontalAlignment="Center" VerticalAlignment="Center"/>
    </Grid>
</Page>
```

<span data-ttu-id="24ab4-137">Wir haben noch keine Datenvorlage für die **Recording**-Klasse bereitgestellt. Daher kann das Benutzeroberflächenframework nur [**ToString**](https://msdn.microsoft.com/library/windows/apps/system.object.tostring.aspx) für jedes Element in der [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="24ab4-137">We haven't yet provided a data template for the **Recording** class, so the best the UI framework can do is to call [**ToString**](https://msdn.microsoft.com/library/windows/apps/system.object.tostring.aspx) for each item in the [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878).</span></span> <span data-ttu-id="24ab4-138">Die Standardimplementierung von **ToString** ist die Rückgabe des Typnamens.</span><span class="sxs-lookup"><span data-stu-id="24ab4-138">The default implementation of **ToString** is to return the type name.</span></span>

![Binden einer Listenansicht](images/xaml-databinding1.png)

<span data-ttu-id="24ab4-140">Um dies zu beheben, können wir entweder [**ToString**](https://msdn.microsoft.com/library/windows/apps/system.object.tostring.aspx) so überschreiben, dass der Wert von **OneLineSummary** zurückgegeben wird, oder wir können eine Datenvorlage bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="24ab4-140">To remedy this we can either override [**ToString**](https://msdn.microsoft.com/library/windows/apps/system.object.tostring.aspx) to return the value of **OneLineSummary**, or we can provide a data template.</span></span> <span data-ttu-id="24ab4-141">Die Datenvorlagenoption wird häufiger verwendet ist auch deutlich flexibler.</span><span class="sxs-lookup"><span data-stu-id="24ab4-141">The data template option is more common and arguably more flexible.</span></span> <span data-ttu-id="24ab4-142">Sie legen eine Datenvorlage mithilfe der [**ContentTemplate**](https://msdn.microsoft.com/library/windows/apps/BR209369)-Eigenschaft eines Inhaltssteuerelements oder mit der [**ItemTemplate**](https://msdn.microsoft.com/library/windows/apps/BR242830)-Eigenschaft eines Elementsteuerelements fest.</span><span class="sxs-lookup"><span data-stu-id="24ab4-142">You specify a data template by using the [**ContentTemplate**](https://msdn.microsoft.com/library/windows/apps/BR209369) property of a content control or the [**ItemTemplate**](https://msdn.microsoft.com/library/windows/apps/BR242830) property of an items control.</span></span> <span data-ttu-id="24ab4-143">Nachfolgend sind zwei Möglichkeiten zum Entwerfen einer Datenvorlage für **Recording** dargestellt, zusammen mit einer Abbildung des Ergebnisses.</span><span class="sxs-lookup"><span data-stu-id="24ab4-143">Here are two ways we could design a data template for **Recording** together with an illustration of the result.</span></span>

```xml
    <ListView ItemsSource="{x:Bind ViewModel.Recordings}"
        HorizontalAlignment="Center" VerticalAlignment="Center">
        <ListView.ItemTemplate>
            <DataTemplate x:DataType="local:Recording">
                <TextBlock Text="{x:Bind OneLineSummary}"/>
            </DataTemplate>
        </ListView.ItemTemplate>
    </ListView>
```

![Binden einer Listenansicht](images/xaml-databinding2.png)

```xml
    <ListView ItemsSource="{x:Bind ViewModel.Recordings}"
    HorizontalAlignment="Center" VerticalAlignment="Center">
        <ListView.ItemTemplate>
            <DataTemplate x:DataType="local:Recording">
                <StackPanel Orientation="Horizontal" Margin="6">
                    <SymbolIcon Symbol="Audio" Margin="0,0,12,0"/>
                    <StackPanel>
                        <TextBlock Text="{x:Bind ArtistName}" FontWeight="Bold"/>
                        <TextBlock Text="{x:Bind CompositionName}"/>
                    </StackPanel>
                </StackPanel>
            </DataTemplate>
        </ListView.ItemTemplate>
    </ListView>
```

![Binden einer Listenansicht](images/xaml-databinding3.png)

<span data-ttu-id="24ab4-146">Weitere Informationen zur XAML-Syntax finden Sie unter [Erstellen einer Benutzeroberfläche mit XAML](https://msdn.microsoft.com/library/windows/apps/Mt228349).</span><span class="sxs-lookup"><span data-stu-id="24ab4-146">For more information about XAML syntax, see [Create a UI with XAML](https://msdn.microsoft.com/library/windows/apps/Mt228349).</span></span> <span data-ttu-id="24ab4-147">Weitere Informationen zum Steuerelementlayout finden Sie unter [Definieren von Layouts mit XAML](https://msdn.microsoft.com/library/windows/apps/Mt228350).</span><span class="sxs-lookup"><span data-stu-id="24ab4-147">For more information about control layout, see [Define layouts with XAML](https://msdn.microsoft.com/library/windows/apps/Mt228350).</span></span>

<a name="adding-a-details-view"></a><span data-ttu-id="24ab4-148">Hinzufügen einer Detailansicht</span><span class="sxs-lookup"><span data-stu-id="24ab4-148">Adding a details view</span></span>
-----------------------------------------------------------------------------------------------------

<span data-ttu-id="24ab4-149">Sie können auch alle Details der **Recording**-Objekte in [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878)-Elementen anzeigen.</span><span class="sxs-lookup"><span data-stu-id="24ab4-149">You can choose to display all the details of **Recording** objects in [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878) items.</span></span> <span data-ttu-id="24ab4-150">Dies nimmt jedoch sehr viel Platz in Anspruch.</span><span class="sxs-lookup"><span data-stu-id="24ab4-150">But that takes up a lot of space.</span></span> <span data-ttu-id="24ab4-151">Stattdessen können Sie gerade so viele Daten im Element anzeigen, um es zu identifizieren, und wenn der Benutzer dann eine Auswahl vornimmt, können Sie alle Details des ausgewählten Elements in einem separaten Teil der Benutzeroberfläche anzeigen, der als „Detailansicht“ bezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="24ab4-151">Instead, you can show just enough data in the item to identify it and then, when the user makes a selection, you can display all the details of the selected item in a separate piece of UI known as the details view.</span></span> <span data-ttu-id="24ab4-152">Diese Anordnung wird auch als „Haupt-/Detailansicht“ oder „Listen-/Detailansicht“ bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="24ab4-152">This arrangement is also known as a master/details view, or a list/details view.</span></span>

<span data-ttu-id="24ab4-153">Sie haben zwei Möglichkeiten, dieses Verhalten zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="24ab4-153">There are two ways to go about this.</span></span> <span data-ttu-id="24ab4-154">Sie können die Detailansicht an die [**SelectedItem**](https://msdn.microsoft.com/library/windows/apps/BR209770)-Eigenschaft der [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878) binden.</span><span class="sxs-lookup"><span data-stu-id="24ab4-154">You can bind the details view to the [**SelectedItem**](https://msdn.microsoft.com/library/windows/apps/BR209770) property of the [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878).</span></span> <span data-ttu-id="24ab4-155">Alternativ können Sie eine [**CollectionViewSource**](https://msdn.microsoft.com/library/windows/apps/BR209833) verwenden: Binden Sie sowohl die **ListView** als auch die Detailansicht an die **CollectionViewSource** (dies behandelt das derzeit ausgewählte Elements für Sie).</span><span class="sxs-lookup"><span data-stu-id="24ab4-155">Or you can use a [**CollectionViewSource**](https://msdn.microsoft.com/library/windows/apps/BR209833): bind both the **ListView** and the details view to the **CollectionViewSource** (which will take care of the currently-selected item for you).</span></span> <span data-ttu-id="24ab4-156">Die beiden Methoden sind unten aufgeführt, und haben dieselben Ergebnisse, wie in der Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="24ab4-156">Both techniques are shown below, and they both give the same results shown in the illustration.</span></span>

> [!NOTE]
> <span data-ttu-id="24ab4-157">Bisher haben wir in diesem Thema nur die [{x:Bind}-Markuperweiterung](https://msdn.microsoft.com/library/windows/apps/Mt204783) verwendet. Die beiden weiter unten aufgeführten Methoden benötigen jedoch die flexiblere (aber weniger leistungsfähige) [{Binding}-Markuperweiterung](https://msdn.microsoft.com/library/windows/apps/Mt204782).</span><span class="sxs-lookup"><span data-stu-id="24ab4-157">So far in this topic we've only used the [{x:Bind} markup extension](https://msdn.microsoft.com/library/windows/apps/Mt204783), but both of the techniques we'll show below require the more flexible (but less performant) [{Binding} markup extension](https://msdn.microsoft.com/library/windows/apps/Mt204782).</span></span>

<span data-ttu-id="24ab4-158">Sehen wir uns zuerst die [**SelectedItem**](https://msdn.microsoft.com/library/windows/apps/BR209770)-Methode an.</span><span class="sxs-lookup"><span data-stu-id="24ab4-158">First, here's the [**SelectedItem**](https://msdn.microsoft.com/library/windows/apps/BR209770) technique.</span></span> <span data-ttu-id="24ab4-159">Bei Verwendung von Komponentenerweiterungen für Visual C++ (C++/CX) muss dann– da wir [{Binding}](https://msdn.microsoft.com/library/windows/apps/Mt204782) verwenden– das [**BindableAttribute**](https://msdn.microsoft.com/library/windows/apps/Hh701872)-Attribut zur **Recording**-Klasse hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="24ab4-159">If you're using Visual C++ component extensions (C++/CX) then, because we'll be using [{Binding}](https://msdn.microsoft.com/library/windows/apps/Mt204782), you'll need to add the [**BindableAttribute**](https://msdn.microsoft.com/library/windows/apps/Hh701872) attribute to the **Recording** class.</span></span>

```cpp
    [Windows::UI::Xaml::Data::Bindable]
    public ref class Recording sealed
    {
        ...
    };
```

<span data-ttu-id="24ab4-160">Darüber hinaus muss nur noch eine Änderung am Markup vorgenommen werden.</span><span class="sxs-lookup"><span data-stu-id="24ab4-160">The only other change necessary is to the markup.</span></span>

```xml
<Page x:Class="Quickstart.MainPage" ... >
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
        <StackPanel HorizontalAlignment="Center" VerticalAlignment="Center">
            <ListView x:Name="recordingsListView" ItemsSource="{x:Bind ViewModel.Recordings}">
                <ListView.ItemTemplate>
                    <DataTemplate x:DataType="local:Recording">
                        <StackPanel Orientation="Horizontal" Margin="6">
                            <SymbolIcon Symbol="Audio" Margin="0,0,12,0"/>
                            <StackPanel>
                                <TextBlock Text="{x:Bind CompositionName}"/>
                            </StackPanel>
                        </StackPanel>
                    </DataTemplate>
                </ListView.ItemTemplate>
            </ListView>
            <StackPanel DataContext="{Binding SelectedItem, ElementName=recordingsListView}"
            Margin="0,24,0,0">
                <TextBlock Text="{Binding ArtistName}"/>
                <TextBlock Text="{Binding CompositionName}"/>
                <TextBlock Text="{Binding ReleaseDateTime}"/>
            </StackPanel>
        </StackPanel>
    </Grid>
</Page>
```

<span data-ttu-id="24ab4-161">Fügen Sie für die [**CollectionViewSource**](https://msdn.microsoft.com/library/windows/apps/BR209833)-Methode zuerst eine **CollectionViewSource** als Seitenressource hinzu.</span><span class="sxs-lookup"><span data-stu-id="24ab4-161">For the [**CollectionViewSource**](https://msdn.microsoft.com/library/windows/apps/BR209833) technique, first add a **CollectionViewSource** as a page resource.</span></span>

```xml
    <Page.Resources>
        <CollectionViewSource x:Name="RecordingsCollection" Source="{x:Bind ViewModel.Recordings}"/>
    </Page.Resources>
```

<span data-ttu-id="24ab4-162">Passen Sie dann die Bindungen in der [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878) (die nicht mehr benannt werden muss) und in der Detailansicht so an, dass die [**CollectionViewSource**](https://msdn.microsoft.com/library/windows/apps/BR209833) verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="24ab4-162">And then adjust the bindings on the [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878) (which no longer needs to be named) and on the details view to use the [**CollectionViewSource**](https://msdn.microsoft.com/library/windows/apps/BR209833).</span></span> <span data-ttu-id="24ab4-163">Beachten Sie, dass Sie durch die direkte Bindung der Detailansicht an die **CollectionViewSource** implizieren, dass Sie in Bindungen, in denen der Pfad in der Sammlung selbst nicht gefunden werden kann, an das aktuelle Element binden möchten.</span><span class="sxs-lookup"><span data-stu-id="24ab4-163">Note that by binding the details view directly to the **CollectionViewSource**, you're implying that you want to bind to the current item in bindings where the path cannot be found on the collection itself.</span></span> <span data-ttu-id="24ab4-164">Die **CurrentItem**-Eigenschaft muss nicht als Pfad für die Bindung angegeben werden, obwohl dies im Zweifelsfall möglich ist.</span><span class="sxs-lookup"><span data-stu-id="24ab4-164">There's no need to specify the **CurrentItem** property as the path for the binding, although you can do that if there's any ambiguity).</span></span>

```xml
    ...

    <ListView ItemsSource="{Binding Source={StaticResource RecordingsCollection}}">

    ...

    <StackPanel DataContext="{Binding Source={StaticResource RecordingsCollection}}" ...>
    ...
```

<span data-ttu-id="24ab4-165">Nachfolgend ist das identische Ergebnis für die beiden Methoden dargestellt.</span><span class="sxs-lookup"><span data-stu-id="24ab4-165">And here's the identical result in each case.</span></span>

![Binden einer Listenansicht](images/xaml-databinding4.png)

<a name="formatting-or-converting-data-values-for-display"></a><span data-ttu-id="24ab4-167">Formatieren oder Konvertieren von Datenwerten für die Anzeige</span><span class="sxs-lookup"><span data-stu-id="24ab4-167">Formatting or converting data values for display</span></span>
--------------------------------------------------------------------------------------------------------------------------------------------

<span data-ttu-id="24ab4-168">Es gibt ein kleines Problem mit dem oben gezeigten Rendering.</span><span class="sxs-lookup"><span data-stu-id="24ab4-168">There is one small issue with the rendering above.</span></span> <span data-ttu-id="24ab4-169">Die **ReleaseDateTime**-Eigenschaft ist nicht nur ein Datum, sondern liegt als [**DateTime**](https://msdn.microsoft.com/library/windows/apps/xaml/system.datetime.aspx) vor und wird daher mit einer Genauigkeit angezeigt, die nicht notwendig ist.</span><span class="sxs-lookup"><span data-stu-id="24ab4-169">The **ReleaseDateTime** property is not just a date, it's a [**DateTime**](https://msdn.microsoft.com/library/windows/apps/xaml/system.datetime.aspx), so it's being displayed with more precision than we need.</span></span> <span data-ttu-id="24ab4-170">Eine Lösung besteht darin, eine Zeichenfolgeneigenschaft zur **Recording**-Klasse hinzuzufügen, die `this.ReleaseDateTime.ToString("d")` zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="24ab4-170">One solution is to add a string property to the **Recording** class that returns `this.ReleaseDateTime.ToString("d")`.</span></span> <span data-ttu-id="24ab4-171">Indem wir diese Eigenschaft **ReleaseDate** nennen, geben wir an, dass sie ein Datum und nicht das Datum und die Uhrzeit zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="24ab4-171">Naming that property **ReleaseDate** would indicate that it returns a date, not a date-and-time.</span></span> <span data-ttu-id="24ab4-172">Die Benennung als **ReleaseDateAsString** gibt dann auch noch an, dass sie eine Zeichenfolge zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="24ab4-172">Naming it **ReleaseDateAsString** would further indicate that it returns a string.</span></span>

<span data-ttu-id="24ab4-173">Eine flexiblere Lösung ist die Verwendung eines so genannten „Wertkonverters“.</span><span class="sxs-lookup"><span data-stu-id="24ab4-173">A more flexible solution is to use something known as a value converter.</span></span> <span data-ttu-id="24ab4-174">Nachfolgend ist ein Beispiel zum Erstellen Ihres eigenen Wertkonverter aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="24ab4-174">Here's an example of how to author your own value converter.</span></span> <span data-ttu-id="24ab4-175">Fügen Sie diesen Code zu Ihrer „Recording.cs“-Quellcodedatei hinzu.</span><span class="sxs-lookup"><span data-stu-id="24ab4-175">Add this code to your Recording.cs source code file.</span></span>

```csharp
public class StringFormatter : Windows.UI.Xaml.Data.IValueConverter
{
    // This converts the value object to the string to display.
    // This will work with most simple types.
    public object Convert(object value, Type targetType,
        object parameter, string language)
    {
        // Retrieve the format string and use it to format the value.
        string formatString = parameter as string;
        if (!string.IsNullOrEmpty(formatString))
        {
            return string.Format(formatString, value);
        }

        // If the format string is null or empty, simply
        // call ToString() on the value.
        return value.ToString();
    }

    // No need to implement converting back on a one-way binding
    public object ConvertBack(object value, Type targetType,
        object parameter, string language)
    {
        throw new NotImplementedException();
    }
}
```

<span data-ttu-id="24ab4-176">Jetzt können wir eine Instanz von **StringFormatter** als Seitenressource hinzufügen und in der Bindung verwenden.</span><span class="sxs-lookup"><span data-stu-id="24ab4-176">Now we can add an instance of **StringFormatter** as a page resource and use it in our binding.</span></span> <span data-ttu-id="24ab4-177">Wir übergeben die Formatzeichenfolge in den Konverter aus dem Markup, um eine möglichst hohe Flexibilität bei der Formatierung zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="24ab4-177">We pass the format string into the converter from markup for ultimate formatting flexibility.</span></span>

```xml
    <Page.Resources>
        <local:StringFormatter x:Key="StringFormatterValueConverter"/>
    </Page.Resources>
    ...

    <TextBlock Text="{Binding ReleaseDateTime,
        Converter={StaticResource StringFormatterValueConverter},
        ConverterParameter=Released: \{0:d\}}"/>

    ...
```

<span data-ttu-id="24ab4-178">Dies ist das Ergebnis.</span><span class="sxs-lookup"><span data-stu-id="24ab4-178">Here's the result.</span></span>

![Anzeigen eines Datums mit benutzerdefinierter Formatierung](images/xaml-databinding5.png)

> [!NOTE]
> <span data-ttu-id="24ab4-180">Ab Windows10, Version1607, wird über das XAML-Framework ein integrierter Konverter für die Konvertierung eines booleschen Operanden in einen Sichtbarkeitszustand bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="24ab4-180">Starting in Windows 10, version 1607, the XAML framework provides a built in boolean to Visibility converter.</span></span> <span data-ttu-id="24ab4-181">Der Konverter verknüpft **true** mit dem Enumerationswert **Visible** und **false** mit dem Wert **Collapsed**, sodass Sie eine Visibility-Eigenschaft an einen booleschen Wert binden können, ohne einen Konverter zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="24ab4-181">The converter maps **true** to the **Visible** enumeration value and **false** to **Collapsed** so you can bind a Visibility property to a boolean without creating a converter.</span></span> <span data-ttu-id="24ab4-182">Für die Verwendung des integrierten Konverters muss die SDK-Zielversion der App mindestens 14393 lauten.</span><span class="sxs-lookup"><span data-stu-id="24ab4-182">To use the built in converter, your app's minimum target SDK version must be 14393 or later.</span></span> <span data-ttu-id="24ab4-183">Die Verwendung ist nicht möglich, wenn Ihre App für frühere Versionen von Windows10 bestimmt ist.</span><span class="sxs-lookup"><span data-stu-id="24ab4-183">You can't use it when your app targets earlier versions of Windows 10.</span></span> <span data-ttu-id="24ab4-184">Weitere Informationen zu Zielversionen finden Sie unter [Versionsadaptiver Code](https://msdn.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code).</span><span class="sxs-lookup"><span data-stu-id="24ab4-184">For more info about target versions, see [Version adaptive code](https://msdn.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code).</span></span>

## <a name="see-also"></a><span data-ttu-id="24ab4-185">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="24ab4-185">See also</span></span>
- [<span data-ttu-id="24ab4-186">Datenbindung</span><span class="sxs-lookup"><span data-stu-id="24ab4-186">Data binding</span></span>](index.md)
