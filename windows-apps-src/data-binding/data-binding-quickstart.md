---
author: mcleblanc
ms.assetid: A9D54DEC-CD1B-4043-ADE4-32CD4977D1BF
title: Übersicht Datenbindung
description: In diesem Thema erfahren Sie, wie Sie in einer UWP-App (Universelle Windows-Plattform) ein Steuerelement (oder ein anderes Benutzeroberflächenelement) an ein einzelnes Element oder ein Steuerelement eines Elements an eine Sammlung von Elementen binden.
ms.author: markl
ms.date: 07/06/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp
ms.localizationpriority: medium
ms.openlocfilehash: 9cf12bc5c875e4ce3be2d627c87e15770e4cc214
ms.sourcegitcommit: a160b91a554f8352de963d9fa37f7df89f8a0e23
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/21/2018
ms.locfileid: "4122511"
---
# <a name="data-binding-overview"></a><span data-ttu-id="d4190-104">Übersicht über Datenbindung</span><span class="sxs-lookup"><span data-stu-id="d4190-104">Data binding overview</span></span>

> [!NOTE]
> **<span data-ttu-id="d4190-105">Einige Informationen beziehen sich auf die Vorabversion, die vor der kommerziellen Freigabe möglicherweise wesentlichen Änderungen unterliegt.</span><span class="sxs-lookup"><span data-stu-id="d4190-105">Some information relates to pre-released product which may be substantially modified before it’s commercially released.</span></span> <span data-ttu-id="d4190-106">Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.</span><span class="sxs-lookup"><span data-stu-id="d4190-106">Microsoft makes no warranties, express or implied, with respect to the information provided here.</span></span>**

<span data-ttu-id="d4190-107">In diesem Thema erfahren Sie, wie Sie in einer UWP-App (Universelle Windows-Plattform) ein Steuerelement (oder ein anderes Benutzeroberflächenelement) an ein einzelnes Element oder ein Elementsteuerelement an eine Sammlung von Elementen binden.</span><span class="sxs-lookup"><span data-stu-id="d4190-107">This topic shows you how to bind a control (or other UI element) to a single item or bind an items control to a collection of items in a Universal Windows Platform (UWP) app.</span></span> <span data-ttu-id="d4190-108">Darüber hinaus wird erläutert, wie Sie die Anzeige von Elementen steuern, eine Detailansicht auf Grundlage einer Auswahl implementieren und Daten für die Anzeige umwandeln.</span><span class="sxs-lookup"><span data-stu-id="d4190-108">In addition, we show how to control the rendering of items, implement a details view based on a selection, and convert data for display.</span></span> <span data-ttu-id="d4190-109">Ausführliche Informationen finden Sie unter [Datenbindung im Detail](data-binding-in-depth.md).</span><span class="sxs-lookup"><span data-stu-id="d4190-109">For more detailed info, see [Data binding in depth](data-binding-in-depth.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d4190-110">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="d4190-110">Prerequisites</span></span>

<span data-ttu-id="d4190-111">In diesem Thema wird vorausgesetzt, dass Sie mit dem Erstellen von UWP-Apps vertraut sind.</span><span class="sxs-lookup"><span data-stu-id="d4190-111">This topic assumes that you know how to create a basic UWP app.</span></span> <span data-ttu-id="d4190-112">Eine Anleitung zum Erstellen Ihrer ersten UWP-App finden Sie unter [Erste Schrittemit Windows-Apps](https://developer.microsoft.com/windows/getstarted).</span><span class="sxs-lookup"><span data-stu-id="d4190-112">For instructions on creating your first UWP app, see [Get started with Windows apps](https://developer.microsoft.com/windows/getstarted).</span></span>

## <a name="create-the-project"></a><span data-ttu-id="d4190-113">Erstellen des Projekts</span><span class="sxs-lookup"><span data-stu-id="d4190-113">Create the project</span></span>

<span data-ttu-id="d4190-114">Erstellen Sie ein neues Projekt vom Typ **Leere Anwendung (Windows Universal)**.</span><span class="sxs-lookup"><span data-stu-id="d4190-114">Create a new **Blank Application (Windows Universal)** project.</span></span> <span data-ttu-id="d4190-115">Nennen Sie sie „Schnellstart“.</span><span class="sxs-lookup"><span data-stu-id="d4190-115">Name it "Quickstart".</span></span>

## <a name="binding-to-a-single-item"></a><span data-ttu-id="d4190-116">Binden an ein einzelnes Element</span><span class="sxs-lookup"><span data-stu-id="d4190-116">Binding to a single item</span></span>

<span data-ttu-id="d4190-117">Jede Bindung besteht aus einem Bindungsziel und einer Bindungsquelle.</span><span class="sxs-lookup"><span data-stu-id="d4190-117">Every binding consists of a binding target and a binding source.</span></span> <span data-ttu-id="d4190-118">In der Regel ist das Ziel eine Eigenschaft eines Steuerelements oder anderen Benutzeroberflächenelements, und die Quelle ist eine Eigenschaft einer Klasseninstanz (ein Datenmodell oder ein Ansichtsmodell).</span><span class="sxs-lookup"><span data-stu-id="d4190-118">Typically, the target is a property of a control or other UI element, and the source is a property of a class instance (a data model, or a view model).</span></span> <span data-ttu-id="d4190-119">In diesem Beispiel wird veranschaulicht, wie Sie ein Steuerelement an ein einzelnes Element binden.</span><span class="sxs-lookup"><span data-stu-id="d4190-119">This example shows how to bind a control to a single item.</span></span> <span data-ttu-id="d4190-120">Das Ziel ist die **Text**-Eigenschaft eines **TextBlock**.</span><span class="sxs-lookup"><span data-stu-id="d4190-120">The target is the **Text** property of a **TextBlock**.</span></span> <span data-ttu-id="d4190-121">Die Quelle ist eine Instanz einer einfachen Klasse namens **Recording**, die eine Audioaufnahme darstellt.</span><span class="sxs-lookup"><span data-stu-id="d4190-121">The source is an instance of a simple class named **Recording** that represents an audio recording.</span></span> <span data-ttu-id="d4190-122">Befassen wir uns zuerst mit der Klasse.</span><span class="sxs-lookup"><span data-stu-id="d4190-122">Let's look at the class first.</span></span>

<span data-ttu-id="d4190-123">Wenn Sie c# verwenden, fügen Sie dann eine neue Klasse zu Ihrem Projekt, und nennen Sie es `Recording.cs`.</span><span class="sxs-lookup"><span data-stu-id="d4190-123">If you're using C#, then add a new class to your project, and name it `Recording.cs`.</span></span>

<span data-ttu-id="d4190-124">Wenn Sie verwenden [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), dann neue **Midl-Datei (.idl)** Elemente hinzuzufügen, auf das Projekt, mit dem Namen wie gezeigt in C++ / WinRT Beispiel Codebeispiel unten.</span><span class="sxs-lookup"><span data-stu-id="d4190-124">If you're using [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), then add new **Midl File (.idl)** items to the project, named as shown in the C++/WinRT code example listing below.</span></span> <span data-ttu-id="d4190-125">Ersetzen Sie den Inhalt dieser neue Dateien mit dem [MIDL 3.0](/uwp/midl-3/intro) -Code in der Liste angezeigt, erstellen Sie das Projekt zu generieren `Recording.h` und `.cpp` und `RecordingViewModel.h` und `.cpp`, und fügen Sie Code für die generierten Dateien, die den Eintrag übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="d4190-125">Replace the contents of those new files with the [MIDL 3.0](/uwp/midl-3/intro) code shown in the listing, build the project to generate `Recording.h` and `.cpp` and `RecordingViewModel.h` and `.cpp`, and then add code to the generated files to match the listing.</span></span> <span data-ttu-id="d4190-126">Weitere Informationen über die generierten Dateien und wie Sie sie in Ihr Projekt kopieren, finden Sie unter [XAML-Steuerelemente; binden an eine C++ / WinRT-Eigenschaft](/windows/uwp/cpp-and-winrt-apis/binding-property).</span><span class="sxs-lookup"><span data-stu-id="d4190-126">For more info about those generated files and how to copy them into your project, see [XAML controls; bind to a C++/WinRT property](/windows/uwp/cpp-and-winrt-apis/binding-property).</span></span>

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

```cppwinrt
// Recording.idl
namespace Quickstart
{
    runtimeclass Recording : Windows.UI.Xaml.DependencyObject
    {
        Recording(String artistName, String compositionName, Windows.Globalization.Calendar releaseDateTime);
        String ArtistName{ get; };
        String CompositionName{ get; };
        Windows.Globalization.Calendar ReleaseDateTime{ get; };
        String OneLineSummary{ get; };
    }
}

// RecordingViewModel.idl
import "Recording.idl";

namespace Quickstart
{
    runtimeclass RecordingViewModel : Windows.UI.Xaml.DependencyObject
    {
        RecordingViewModel();
        Quickstart.Recording DefaultRecording{ get; };
    }
}

// Recording.h
// Add these fields:
...
#include <sstream>
...
private:
    std::wstring m_artistName;
    std::wstring m_compositionName;
    Windows::Globalization::Calendar m_releaseDateTime;
...

// Recording.cpp
// Implement like this:
...
Recording::Recording(hstring const& artistName, hstring const& compositionName, Windows::Globalization::Calendar const& releaseDateTime) :
    m_artistName{ artistName.c_str() },
    m_compositionName{ compositionName.c_str() },
    m_releaseDateTime{ releaseDateTime } {}

hstring Recording::ArtistName(){ return hstring{ m_artistName }; }
hstring Recording::CompositionName(){ return hstring{ m_compositionName }; }
Windows::Globalization::Calendar Recording::ReleaseDateTime(){ return m_releaseDateTime; }

hstring Recording::OneLineSummary()
{
    std::wstringstream wstringstream;
    wstringstream << m_compositionName.c_str();
    wstringstream << L" by " << m_artistName.c_str();
    wstringstream << L", released: " << m_releaseDateTime.MonthAsNumericString().c_str();
    wstringstream << L"/" << m_releaseDateTime.DayAsString().c_str();
    wstringstream << L"/" << m_releaseDateTime.YearAsString().c_str();
    return hstring{ wstringstream.str().c_str() };
}
...

// RecordingViewModel.h
// Add this field:
...
#include "Recording.h"
...
private:
    Quickstart::Recording m_defaultRecording{ nullptr };
...

// RecordingViewModel.cpp
// Implement like this:
...
Quickstart::Recording RecordingViewModel::DefaultRecording()
{
    Windows::Globalization::Calendar releaseDateTime;
    releaseDateTime.Year(1761);
    releaseDateTime.Month(1);
    releaseDateTime.Day(1);
    m_defaultRecording = winrt::make<Recording>(L"Wolfgang Amadeus Mozart", L"Andante in C for Piano", releaseDateTime);
    return m_defaultRecording;
}
...
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
        Recording ^ defaultRecording;
    public:
        RecordingViewModel()
        {
            Windows::Globalization::Calendar^ releaseDateTime = ref new Windows::Globalization::Calendar();
            releaseDateTime->Year = 1761;
            releaseDateTime->Month = 1;
            releaseDateTime->Day = 1;
            this->defaultRecording = ref new Recording{ L"Wolfgang Amadeus Mozart", L"Andante in C for Piano", releaseDateTime };
        }
        property Recording^ DefaultRecording
        {
            Recording^ get() { return this->defaultRecording; };
        }
    };
}
```

<span data-ttu-id="d4190-127">Machen Sie als Nächstes die Bindungsquellklasse aus der Klasse verfügbar, die die Markupseite darstellt.</span><span class="sxs-lookup"><span data-stu-id="d4190-127">Next, expose the binding source class from the class that represents your page of markup.</span></span> <span data-ttu-id="d4190-128">Zu diesem Zweck fügen Sie eine Eigenschaft vom Typ **RecordingViewModel** zu **MainPage** hinzu.</span><span class="sxs-lookup"><span data-stu-id="d4190-128">We do that by adding a property of type **RecordingViewModel** to **MainPage**.</span></span>

<span data-ttu-id="d4190-129">Wenn Sie verwenden [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), und klicken Sie dann erste Update `MainPage.idl`.</span><span class="sxs-lookup"><span data-stu-id="d4190-129">If you're using [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), then first update `MainPage.idl`.</span></span> <span data-ttu-id="d4190-130">Erstellen Sie das Projekt erneut `MainPage.h` und `.cpp`, und führen Sie die Änderungen in die generierten Dateien mit derjenigen, die in Ihrem Projekt.</span><span class="sxs-lookup"><span data-stu-id="d4190-130">Build the project to regenerate `MainPage.h` and `.cpp`, and merge the changes in those generated files into the ones in your project.</span></span>

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
        public RecordingViewModel ViewModel{ get; set; }
    }
}
```

```cppwinrt
// MainPage.idl
// Add this property:
import "RecordingViewModel.idl";
...
RecordingViewModel ViewModel{ get; };
...

// MainPage.h
// Add this property and this field:
...
#include "RecordingViewModel.h"
...
    Quickstart::RecordingViewModel ViewModel();

private:
    Quickstart::RecordingViewModel m_viewModel{ nullptr };
...

// MainPage.cpp
// Implement like this:
...
MainPage::MainPage()
{
    InitializeComponent();
    m_viewModel = winrt::make<RecordingViewModel>();
}
Quickstart::RecordingViewModel MainPage::ViewModel()
{
    return m_viewModel;
}
...
```

```cpp
namespace Quickstart
{
    public ref class MainPage sealed
    {
    private:
        RecordingViewModel ^ viewModel;
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

<span data-ttu-id="d4190-131">Der letzte Codeteil ist das Binden eines **TextBlock** an die **ViewModel.DefaultRecording.OneLiner**-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="d4190-131">The last piece is to bind a **TextBlock** to the **ViewModel.DefaultRecording.OneLiner** property.</span></span>

```xml
<Page x:Class="Quickstart.MainPage" ... >
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
        <TextBlock Text="{x:Bind ViewModel.DefaultRecording.OneLineSummary}"
    HorizontalAlignment="Center"
    VerticalAlignment="Center"/>
    </Grid>
</Page>
```

<span data-ttu-id="d4190-132">Wenn Sie verwenden [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), müssen Sie so entfernen Sie die Funktion **MainPage:: clickHandler** in der Reihenfolge für das Projekt zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="d4190-132">If you're using [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), then you'll need to remove the **MainPage::ClickHandler** function in order for the project to build.</span></span>

<span data-ttu-id="d4190-133">Dies ist das Ergebnis.</span><span class="sxs-lookup"><span data-stu-id="d4190-133">Here's the result.</span></span>

![Binden eines Textblocks](images/xaml-databinding0.png)

## <a name="binding-to-a-collection-of-items"></a><span data-ttu-id="d4190-135">Binden an eine Sammlung von Elementen</span><span class="sxs-lookup"><span data-stu-id="d4190-135">Binding to a collection of items</span></span>

<span data-ttu-id="d4190-136">Ein häufiges Szenario ist das Binden an eine Sammlung von Geschäftsobjekten.</span><span class="sxs-lookup"><span data-stu-id="d4190-136">A common scenario is to bind to a collection of business objects.</span></span> <span data-ttu-id="d4190-137">In C# und Visual Basic stellt die generische [**ObservableCollection&lt;T&gt;**](https://msdn.microsoft.com/library/windows/apps/xaml/ms668604.aspx)-Klasse eine gute Wahl für die Datenbindung bei Sammlungen dar, da sie die  [**INotifyPropertyChanged**](https://msdn.microsoft.com/library/windows/apps/xaml/system.componentmodel.inotifypropertychanged.aspx)-Schnittstelle und die [**INotifyCollectionChanged**](https://msdn.microsoft.com/library/windows/apps/xaml/system.collections.specialized.inotifycollectionchanged.aspx)-Schnittstelle implementiert.</span><span class="sxs-lookup"><span data-stu-id="d4190-137">In C# and Visual Basic, the generic [**ObservableCollection&lt;T&gt;**](https://msdn.microsoft.com/library/windows/apps/xaml/ms668604.aspx) class is a good collection choice for data binding, because it implements the [**INotifyPropertyChanged**](https://msdn.microsoft.com/library/windows/apps/xaml/system.componentmodel.inotifypropertychanged.aspx) and [**INotifyCollectionChanged**](https://msdn.microsoft.com/library/windows/apps/xaml/system.collections.specialized.inotifycollectionchanged.aspx) interfaces.</span></span> <span data-ttu-id="d4190-138">Diese Schnittstellen bieten eine Änderungsbenachrichtigung für Bindungen, wenn Elemente hinzugefügt oder entfernt werden oder eine Eigenschaft der Liste selbst geändert wird.</span><span class="sxs-lookup"><span data-stu-id="d4190-138">These interfaces provide change notification to bindings when items are added or removed or a property of the list itself changes.</span></span> <span data-ttu-id="d4190-139">Wenn Ihre gebundenen Steuerelemente bei Änderungen an Eigenschaften von Objekten in der Sammlung aktualisiert werden sollen, muss das Geschäftsobjekt auch **INotifyPropertyChanged** implementieren.</span><span class="sxs-lookup"><span data-stu-id="d4190-139">If you want your bound controls to update with changes to properties of objects in the collection, the business object should also implement **INotifyPropertyChanged**.</span></span> <span data-ttu-id="d4190-140">Weitere Informationen finden Sie unter [Datenbindung im Detail](data-binding-in-depth.md).</span><span class="sxs-lookup"><span data-stu-id="d4190-140">For more info, see [Data binding in depth](data-binding-in-depth.md).</span></span>

<span data-ttu-id="d4190-141">Wenn Sie verwenden [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), und klicken Sie dann Sie zum Binden an eine Observable-Collection in informieren [XAML-items-Steuerelemente; binden an eine C++ / WinRT-Collection](/windows/uwp/cpp-and-winrt-apis/binding-collection).</span><span class="sxs-lookup"><span data-stu-id="d4190-141">If you're using [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), then you can learn more about binding to an observable collection in [XAML items controls; bind to a C++/WinRT collection](/windows/uwp/cpp-and-winrt-apis/binding-collection).</span></span> <span data-ttu-id="d4190-142">Wenn Sie in diesem Thema zuerst, Sie dann den Zweck der C++ lesen / WinRT-Codebeispiel unten wird deutlicher werden.</span><span class="sxs-lookup"><span data-stu-id="d4190-142">If you read that topic first, then the intent of the C++/WinRT code listing shown below will be clearer.</span></span>

<span data-ttu-id="d4190-143">In diesem nächsten Beispiel wird eine [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878) an eine Sammlung von `Recording`-Objekten gebunden.</span><span class="sxs-lookup"><span data-stu-id="d4190-143">This next example binds a [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878) to a collection of `Recording` objects.</span></span> <span data-ttu-id="d4190-144">Beginnen wir, indem wir die Sammlung zum Ansichtsmodell hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="d4190-144">Let's start by adding the collection to our view model.</span></span> <span data-ttu-id="d4190-145">Fügen Sie einfach diese neuen Member zur **RecordingViewModel**-Klasse hinzu.</span><span class="sxs-lookup"><span data-stu-id="d4190-145">Just add these new members to the **RecordingViewModel** class.</span></span>

```csharp
public class RecordingViewModel
{
    ...
    private ObservableCollection<Recording> recordings = new ObservableCollection<Recording>();
    public ObservableCollection<Recording> Recordings{ get{ return this.recordings; } }
    public RecordingViewModel()
    {
        this.recordings.Add(new Recording(){ ArtistName = "Johann Sebastian Bach",
            CompositionName = "Mass in B minor", ReleaseDateTime = new DateTime(1748, 7, 8) });
        this.recordings.Add(new Recording(){ ArtistName = "Ludwig van Beethoven",
            CompositionName = "Third Symphony", ReleaseDateTime = new DateTime(1805, 2, 11) });
        this.recordings.Add(new Recording(){ ArtistName = "George Frideric Handel",
            CompositionName = "Serse", ReleaseDateTime = new DateTime(1737, 12, 3) });
    }
}
```

```cppwinrt
// RecordingViewModel.idl
// Add this property:
...
Windows.Foundation.Collections.IVector<IInspectable> Recordings{ get; };
...

// RecordingViewModel.h
// Change the constructor declaration, and add this property and this field:
...
    RecordingViewModel();
    Windows::Foundation::Collections::IVector<Windows::Foundation::IInspectable> Recordings();

private:
    Windows::Foundation::Collections::IVector<Windows::Foundation::IInspectable> m_recordings;
...

// RecordingViewModel.cpp
// Implement like this:
...
RecordingViewModel::RecordingViewModel()
{
    std::vector<Windows::Foundation::IInspectable> recordings;

    Windows::Globalization::Calendar releaseDateTime;
    releaseDateTime.Month(7); releaseDateTime.Day(8); releaseDateTime.Year(1748);
    recordings.push_back(winrt::make<Recording>(L"Johann Sebastian Bach", L"Mass in B minor", releaseDateTime));

    releaseDateTime = Windows::Globalization::Calendar{};
    releaseDateTime.Month(11); releaseDateTime.Day(2); releaseDateTime.Year(1805);
    recordings.push_back(winrt::make<Recording>(L"Ludwig van Beethoven", L"Third Symphony", releaseDateTime));

    releaseDateTime = Windows::Globalization::Calendar{};
    releaseDateTime.Month(3); releaseDateTime.Day(12); releaseDateTime.Year(1737);
    recordings.push_back(winrt::make<Recording>(L"George Frideric Handel", L"Serse", releaseDateTime));

    m_recordings = winrt::single_threaded_observable_vector<Windows::Foundation::IInspectable>(std::move(recordings));
}

Windows::Foundation::Collections::IVector<Windows::Foundation::IInspectable> RecordingViewModel::Recordings() { return m_recordings; }
...
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
        releaseDateTime->Year = 1748;
        releaseDateTime->Month = 7;
        releaseDateTime->Day = 8;
        Recording^ recording = ref new Recording{ L"Johann Sebastian Bach", L"Mass in B minor", releaseDateTime };
        this->Recordings->Append(recording);
        releaseDateTime = ref new Windows::Globalization::Calendar();
        releaseDateTime->Year = 1805;
        releaseDateTime->Month = 2;
        releaseDateTime->Day = 11;
        recording = ref new Recording{ L"Ludwig van Beethoven", L"Third Symphony", releaseDateTime };
        this->Recordings->Append(recording);
        releaseDateTime = ref new Windows::Globalization::Calendar();
        releaseDateTime->Year = 1737;
        releaseDateTime->Month = 12;
        releaseDateTime->Day = 3;
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

<span data-ttu-id="d4190-146">Binden Sie dann eine [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878) an die **ViewModel.Recordings**-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="d4190-146">And then bind a [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878) to the **ViewModel.Recordings** property.</span></span>

```xml
<Page x:Class="Quickstart.MainPage" ... >
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
        <ListView ItemsSource="{x:Bind ViewModel.Recordings}"
        HorizontalAlignment="Center" VerticalAlignment="Center"/>
    </Grid>
</Page>
```

<span data-ttu-id="d4190-147">Wir haben noch keine Datenvorlage für die **Recording**-Klasse bereitgestellt. Daher kann das Benutzeroberflächenframework nur [**ToString**](https://msdn.microsoft.com/library/windows/apps/system.object.tostring.aspx) für jedes Element in der [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="d4190-147">We haven't yet provided a data template for the **Recording** class, so the best the UI framework can do is to call [**ToString**](https://msdn.microsoft.com/library/windows/apps/system.object.tostring.aspx) for each item in the [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878).</span></span> <span data-ttu-id="d4190-148">Die Standardimplementierung von **ToString** ist die Rückgabe des Typnamens.</span><span class="sxs-lookup"><span data-stu-id="d4190-148">The default implementation of **ToString** is to return the type name.</span></span>

![Binden einer Listenansicht](images/xaml-databinding1.png)

<span data-ttu-id="d4190-150">Um dieses Problem zu beheben, können wir entweder [**ToString**](https://msdn.microsoft.com/library/windows/apps/system.object.tostring.aspx) , wenn den Wert von **OneLineSummary**überschreiben, oder wir können eine Datenvorlage bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="d4190-150">To remedy this, we can either override [**ToString**](https://msdn.microsoft.com/library/windows/apps/system.object.tostring.aspx) to return the value of **OneLineSummary**, or we can provide a data template.</span></span> <span data-ttu-id="d4190-151">Die Vorlage Data-Option ist eine mehr üblichen Lösung und eine flexiblere.</span><span class="sxs-lookup"><span data-stu-id="d4190-151">The data template option is a more usual solution, and a more flexible one.</span></span> <span data-ttu-id="d4190-152">Sie legen eine Datenvorlage mithilfe der [**ContentTemplate**](https://msdn.microsoft.com/library/windows/apps/BR209369)-Eigenschaft eines Inhaltssteuerelements oder mit der [**ItemTemplate**](https://msdn.microsoft.com/library/windows/apps/BR242830)-Eigenschaft eines Elementsteuerelements fest.</span><span class="sxs-lookup"><span data-stu-id="d4190-152">You specify a data template by using the [**ContentTemplate**](https://msdn.microsoft.com/library/windows/apps/BR209369) property of a content control or the [**ItemTemplate**](https://msdn.microsoft.com/library/windows/apps/BR242830) property of an items control.</span></span> <span data-ttu-id="d4190-153">Nachfolgend sind zwei Möglichkeiten zum Entwerfen einer Datenvorlage für **Recording** dargestellt, zusammen mit einer Abbildung des Ergebnisses.</span><span class="sxs-lookup"><span data-stu-id="d4190-153">Here are two ways we could design a data template for **Recording** together with an illustration of the result.</span></span>

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

<span data-ttu-id="d4190-156">Weitere Informationen zur XAML-Syntax finden Sie unter [Erstellen einer Benutzeroberfläche mit XAML](https://msdn.microsoft.com/library/windows/apps/Mt228349).</span><span class="sxs-lookup"><span data-stu-id="d4190-156">For more information about XAML syntax, see [Create a UI with XAML](https://msdn.microsoft.com/library/windows/apps/Mt228349).</span></span> <span data-ttu-id="d4190-157">Weitere Informationen zum Steuerelementlayout finden Sie unter [Definieren von Layouts mit XAML](https://msdn.microsoft.com/library/windows/apps/Mt228350).</span><span class="sxs-lookup"><span data-stu-id="d4190-157">For more information about control layout, see [Define layouts with XAML](https://msdn.microsoft.com/library/windows/apps/Mt228350).</span></span>

## <a name="adding-a-details-view"></a><span data-ttu-id="d4190-158">Hinzufügen einer Detailansicht</span><span class="sxs-lookup"><span data-stu-id="d4190-158">Adding a details view</span></span>

<span data-ttu-id="d4190-159">Sie können auch alle Details der **Recording**-Objekte in [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878)-Elementen anzeigen.</span><span class="sxs-lookup"><span data-stu-id="d4190-159">You can choose to display all the details of **Recording** objects in [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878) items.</span></span> <span data-ttu-id="d4190-160">Dies nimmt jedoch sehr viel Platz in Anspruch.</span><span class="sxs-lookup"><span data-stu-id="d4190-160">But that takes up a lot of space.</span></span> <span data-ttu-id="d4190-161">Stattdessen können Sie gerade so viele Daten im Element anzeigen, um es zu identifizieren, und wenn der Benutzer dann eine Auswahl vornimmt, können Sie alle Details des ausgewählten Elements in einem separaten Teil der Benutzeroberfläche anzeigen, der als „Detailansicht“ bezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="d4190-161">Instead, you can show just enough data in the item to identify it and then, when the user makes a selection, you can display all the details of the selected item in a separate piece of UI known as the details view.</span></span> <span data-ttu-id="d4190-162">Diese Anordnung wird auch als „Haupt-/Detailansicht“ oder „Listen-/Detailansicht“ bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="d4190-162">This arrangement is also known as a master/details view, or a list/details view.</span></span>

<span data-ttu-id="d4190-163">Sie haben zwei Möglichkeiten, dieses Verhalten zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="d4190-163">There are two ways to go about this.</span></span> <span data-ttu-id="d4190-164">Sie können die Detailansicht an die [**SelectedItem**](https://msdn.microsoft.com/library/windows/apps/BR209770)-Eigenschaft der [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878) binden.</span><span class="sxs-lookup"><span data-stu-id="d4190-164">You can bind the details view to the [**SelectedItem**](https://msdn.microsoft.com/library/windows/apps/BR209770) property of the [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878).</span></span> <span data-ttu-id="d4190-165">Oder Sie können eine [**CollectionViewSource**](https://msdn.microsoft.com/library/windows/apps/BR209833), in diesem Fall binden Sie sowohl **ListView** als auch die Detailansicht an die **CollectionViewSource** (tun dies dauert Vorsicht das derzeit ausgewählte Elements für Sie).</span><span class="sxs-lookup"><span data-stu-id="d4190-165">Or you can use a [**CollectionViewSource**](https://msdn.microsoft.com/library/windows/apps/BR209833), in which case you bind both the **ListView** and the details view to the **CollectionViewSource** (doing so takes care of the currently-selected item for you).</span></span> <span data-ttu-id="d4190-166">Beide Methoden sind unten aufgeführt, und beide bieten umfassende dieselben Ergebnisse (in der Abbildung gezeigt).</span><span class="sxs-lookup"><span data-stu-id="d4190-166">Both techniques are shown below, and they both give the same results (shown in the illustration).</span></span>

> [!NOTE]
> <span data-ttu-id="d4190-167">Bisher haben wir in diesem Thema nur die [{x:Bind}-Markuperweiterung](https://msdn.microsoft.com/library/windows/apps/Mt204783) verwendet. Die beiden weiter unten aufgeführten Methoden benötigen jedoch die flexiblere (aber weniger leistungsfähige) [{Binding}-Markuperweiterung](https://msdn.microsoft.com/library/windows/apps/Mt204782).</span><span class="sxs-lookup"><span data-stu-id="d4190-167">So far in this topic we've only used the [{x:Bind} markup extension](https://msdn.microsoft.com/library/windows/apps/Mt204783), but both of the techniques we'll show below require the more flexible (but less performant) [{Binding} markup extension](https://msdn.microsoft.com/library/windows/apps/Mt204782).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d4190-168">Wenn Sie verwenden [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), und klicken Sie dann das [**BindableAttribute**](https://msdn.microsoft.com/library/windows/apps/Hh701872) -Attribut (siehe unten) ist nur verfügbar, wenn Sie die [Windows 10 SDK Preview Build 17661](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK)installiert haben, oder höher.</span><span class="sxs-lookup"><span data-stu-id="d4190-168">If you're using [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), then the [**BindableAttribute**](https://msdn.microsoft.com/library/windows/apps/Hh701872) attribute (mentioned below) is available only if you've installed the [Windows 10 SDK Preview Build 17661](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK), or later.</span></span> <span data-ttu-id="d4190-169">Ohne dieses Attribut müssen Sie die [ICustomPropertyProvider](/uwp/api/windows.ui.xaml.data.icustompropertyprovider) und [ICustomProperty](/uwp/api/windows.ui.xaml.data.icustomproperty) -Schnittstellen implementieren, um die Markuperweiterung [{Binding}](https://msdn.microsoft.com/library/windows/apps/Mt204782) verwenden können.</span><span class="sxs-lookup"><span data-stu-id="d4190-169">Without that attribute, you'll need to implement the [ICustomPropertyProvider](/uwp/api/windows.ui.xaml.data.icustompropertyprovider) and [ICustomProperty](/uwp/api/windows.ui.xaml.data.icustomproperty) interfaces in order to be able to use the [{Binding}](https://msdn.microsoft.com/library/windows/apps/Mt204782) markup extension.</span></span>

<span data-ttu-id="d4190-170">Wenn Sie C++ verwenden / WinRT oder Visual C++-komponentenerweiterungen (C++ / CX) dann, da wir die Markuperweiterung [{Binding}](https://msdn.microsoft.com/library/windows/apps/Mt204782) verwenden, benötigen Sie müssen das Attribut [**BindableAttribute**](https://msdn.microsoft.com/library/windows/apps/Hh701872) der **Aufnahme** -Klasse hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="d4190-170">If you're using C++/WinRT or Visual C++ component extensions (C++/CX) then, because we'll be using the [{Binding}](https://msdn.microsoft.com/library/windows/apps/Mt204782) markup extension, you'll need to add the [**BindableAttribute**](https://msdn.microsoft.com/library/windows/apps/Hh701872) attribute to the **Recording** class.</span></span>

<span data-ttu-id="d4190-171">Sehen wir uns zuerst die [**SelectedItem**](https://msdn.microsoft.com/library/windows/apps/BR209770)-Methode an.</span><span class="sxs-lookup"><span data-stu-id="d4190-171">First, here's the [**SelectedItem**](https://msdn.microsoft.com/library/windows/apps/BR209770) technique.</span></span>

```csharp
// No code changes necessary for C#.
```

```cppwinrt
// Recording.idl
// Add this attribute:
...
[Windows.UI.Xaml.Data.Bindable]
runtimeclass Recording : Windows.UI.Xaml.DependencyObject
...
```

```cpp
[Windows::UI::Xaml::Data::Bindable]
public ref class Recording sealed
{
    ...
};
```

<span data-ttu-id="d4190-172">Darüber hinaus muss nur noch eine Änderung am Markup vorgenommen werden.</span><span class="sxs-lookup"><span data-stu-id="d4190-172">The only other change necessary is to the markup.</span></span>

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

<span data-ttu-id="d4190-173">Fügen Sie für die [**CollectionViewSource**](https://msdn.microsoft.com/library/windows/apps/BR209833)-Methode zuerst eine **CollectionViewSource** als Seitenressource hinzu.</span><span class="sxs-lookup"><span data-stu-id="d4190-173">For the [**CollectionViewSource**](https://msdn.microsoft.com/library/windows/apps/BR209833) technique, first add a **CollectionViewSource** as a page resource.</span></span>

```xml
<Page.Resources>
    <CollectionViewSource x:Name="RecordingsCollection" Source="{x:Bind ViewModel.Recordings}"/>
</Page.Resources>
```

<span data-ttu-id="d4190-174">Passen Sie dann die Bindungen in der [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878) (die nicht mehr benannt werden muss) und in der Detailansicht so an, dass die [**CollectionViewSource**](https://msdn.microsoft.com/library/windows/apps/BR209833) verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="d4190-174">And then adjust the bindings on the [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878) (which no longer needs to be named) and on the details view to use the [**CollectionViewSource**](https://msdn.microsoft.com/library/windows/apps/BR209833).</span></span> <span data-ttu-id="d4190-175">Beachten Sie, dass Sie durch die direkte Bindung der Detailansicht an die **CollectionViewSource** implizieren, dass Sie in Bindungen, in denen der Pfad in der Sammlung selbst nicht gefunden werden kann, an das aktuelle Element binden möchten.</span><span class="sxs-lookup"><span data-stu-id="d4190-175">Note that by binding the details view directly to the **CollectionViewSource**, you're implying that you want to bind to the current item in bindings where the path cannot be found on the collection itself.</span></span> <span data-ttu-id="d4190-176">Die **CurrentItem**-Eigenschaft muss nicht als Pfad für die Bindung angegeben werden, obwohl dies im Zweifelsfall möglich ist.</span><span class="sxs-lookup"><span data-stu-id="d4190-176">There's no need to specify the **CurrentItem** property as the path for the binding, although you can do that if there's any ambiguity).</span></span>

```xml
...
<ListView ItemsSource="{Binding Source={StaticResource RecordingsCollection}}">
...
<StackPanel DataContext="{Binding Source={StaticResource RecordingsCollection}}" ...>
...
```

<span data-ttu-id="d4190-177">Nachfolgend ist das identische Ergebnis für die beiden Methoden dargestellt.</span><span class="sxs-lookup"><span data-stu-id="d4190-177">And here's the identical result in each case.</span></span>

![Binden einer Listenansicht](images/xaml-databinding4.png)

## <a name="formatting-or-converting-data-values-for-display"></a><span data-ttu-id="d4190-179">Formatieren oder Konvertieren von Datenwerten für die Anzeige</span><span class="sxs-lookup"><span data-stu-id="d4190-179">Formatting or converting data values for display</span></span>

<span data-ttu-id="d4190-180">Es gibt ein kleines Problem mit dem oben gezeigten Rendering.</span><span class="sxs-lookup"><span data-stu-id="d4190-180">There is one small issue with the rendering above.</span></span> <span data-ttu-id="d4190-181">Die **ReleaseDateTime**-Eigenschaft ist nicht nur ein Datum, sondern liegt als [**DateTime**](https://msdn.microsoft.com/library/windows/apps/xaml/system.datetime.aspx) vor und wird daher mit einer Genauigkeit angezeigt, die nicht notwendig ist.</span><span class="sxs-lookup"><span data-stu-id="d4190-181">The **ReleaseDateTime** property is not just a date, it's a [**DateTime**](https://msdn.microsoft.com/library/windows/apps/xaml/system.datetime.aspx), so it's being displayed with more precision than we need.</span></span> <span data-ttu-id="d4190-182">Eine Lösung besteht darin, eine Zeichenfolgeneigenschaft zur **Recording**-Klasse hinzuzufügen, die `this.ReleaseDateTime.ToString("d")` zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="d4190-182">One solution is to add a string property to the **Recording** class that returns `this.ReleaseDateTime.ToString("d")`.</span></span> <span data-ttu-id="d4190-183">Indem wir diese Eigenschaft **ReleaseDate** nennen, geben wir an, dass sie ein Datum und nicht das Datum und die Uhrzeit zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="d4190-183">Naming that property **ReleaseDate** would indicate that it returns a date, not a date-and-time.</span></span> <span data-ttu-id="d4190-184">Die Benennung als **ReleaseDateAsString** gibt dann auch noch an, dass sie eine Zeichenfolge zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="d4190-184">Naming it **ReleaseDateAsString** would further indicate that it returns a string.</span></span>

<span data-ttu-id="d4190-185">Eine flexiblere Lösung ist die Verwendung eines so genannten „Wertkonverters“.</span><span class="sxs-lookup"><span data-stu-id="d4190-185">A more flexible solution is to use something known as a value converter.</span></span> <span data-ttu-id="d4190-186">Nachfolgend ist ein Beispiel zum Erstellen Ihres eigenen Wertkonverter aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="d4190-186">Here's an example of how to author your own value converter.</span></span> <span data-ttu-id="d4190-187">Fügen Sie diesen Code zu Ihrer „Recording.cs“-Quellcodedatei hinzu.</span><span class="sxs-lookup"><span data-stu-id="d4190-187">Add this code to your Recording.cs source code file.</span></span>

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

<span data-ttu-id="d4190-188">Jetzt können wir eine Instanz von **StringFormatter** als Seitenressource hinzufügen und in der Bindung verwenden.</span><span class="sxs-lookup"><span data-stu-id="d4190-188">Now we can add an instance of **StringFormatter** as a page resource and use it in our binding.</span></span> <span data-ttu-id="d4190-189">Wir übergeben die Formatzeichenfolge in den Konverter aus dem Markup, um eine möglichst hohe Flexibilität bei der Formatierung zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="d4190-189">We pass the format string into the converter from markup for ultimate formatting flexibility.</span></span>

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

<span data-ttu-id="d4190-190">Dies ist das Ergebnis.</span><span class="sxs-lookup"><span data-stu-id="d4190-190">Here's the result.</span></span>

![Anzeigen eines Datums mit benutzerdefinierter Formatierung](images/xaml-databinding5.png)

> [!NOTE]
> <span data-ttu-id="d4190-192">Ab Windows 10, Version 1607, bietet das XAML-Framework einen integrierten Boolean-zu-Sichtbarkeit Konverter.</span><span class="sxs-lookup"><span data-stu-id="d4190-192">Starting in Windows 10, version 1607, the XAML framework provides a built-in Boolean-to-Visibility converter.</span></span> <span data-ttu-id="d4190-193">Der Konverter ordnet der Enumerationswert **Visibility.Visible einstellen** und **"false"** auf **Visibility.Collapsed** **"true"** , sodass Sie eine Visibility-Eigenschaft an einen booleschen Wert binden können, ohne einen Konverter zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="d4190-193">The converter maps **true** to the **Visibility.Visible** enumeration value and **false** to **Visibility.Collapsed** so you can bind a Visibility property to a Boolean without creating a converter.</span></span> <span data-ttu-id="d4190-194">Für die Verwendung des integrierten Konverters muss die SDK-Zielversion der App mindestens 14393 lauten.</span><span class="sxs-lookup"><span data-stu-id="d4190-194">To use the built in converter, your app's minimum target SDK version must be 14393 or later.</span></span> <span data-ttu-id="d4190-195">Die Verwendung ist nicht möglich, wenn Ihre App für frühere Versionen von Windows10 bestimmt ist.</span><span class="sxs-lookup"><span data-stu-id="d4190-195">You can't use it when your app targets earlier versions of Windows 10.</span></span> <span data-ttu-id="d4190-196">Weitere Informationen zu Zielversionen finden Sie unter [Version adaptiven Code](https://msdn.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code).</span><span class="sxs-lookup"><span data-stu-id="d4190-196">For more info about target versions, see [Version-adaptive code](https://msdn.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code).</span></span>

## <a name="see-also"></a><span data-ttu-id="d4190-197">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d4190-197">See also</span></span>
* [<span data-ttu-id="d4190-198">Datenbindung</span><span class="sxs-lookup"><span data-stu-id="d4190-198">Data binding</span></span>](index.md)
