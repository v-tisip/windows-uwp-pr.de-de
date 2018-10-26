---
author: QuinnRadich
title: Lernpfad– Anzeigen von Kunden in einer Liste
description: Hier erfahren Sie, was Sie tun müssen, um eine Sammlung von Kundenobjekten in einer Liste anzuzeigen.
ms.author: quradic
ms.date: 05/07/2018
ms.topic: article
keywords: Erste Schritte, UWP, Windows10, Lernpfad, Datenbindung, Liste
ms.localizationpriority: medium
ms.openlocfilehash: 4e58231d644616a088eb06f24a2465c240e10c16
ms.sourcegitcommit: b7e3d222e229cdbf04e837fcb94fb7d84a93de09
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5597218"
---
# <a name="display-customers-in-a-list"></a><span data-ttu-id="d32cb-104">Anzeigen von Kunden in einer Liste</span><span class="sxs-lookup"><span data-stu-id="d32cb-104">Display customers in a list</span></span>

<span data-ttu-id="d32cb-105">Das Anzeigen und Bearbeiten von echten Daten auf der Benutzeroberfläche ist für die Funktionalität vieler Apps von entscheidender Bedeutung.</span><span class="sxs-lookup"><span data-stu-id="d32cb-105">Displaying and manipulating real data in the UI is crucial to the functionality of many apps.</span></span> <span data-ttu-id="d32cb-106">In diesem Artikel erfahren Sie, was Sie wissen müssen, um eine Sammlung von Kundenobjekten in einer Liste anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="d32cb-106">This article will show you what you need to know to display a collection of Customer objects in a list.</span></span>

<span data-ttu-id="d32cb-107">Dies ist kein Lernprogramm.</span><span class="sxs-lookup"><span data-stu-id="d32cb-107">This is not a tutorial.</span></span> <span data-ttu-id="d32cb-108">Wenn Sie ein Lernprogramm suchen, sehen Sie sich unser [Datenbindungs-Tutorial](../data-binding/xaml-basics-data-binding.md) an, in dem Sie schrittweise Anleitungen finden.</span><span class="sxs-lookup"><span data-stu-id="d32cb-108">If you want one, see our [data binding tutorial](../data-binding/xaml-basics-data-binding.md), which will provide you with a step-by-step guided experience.</span></span>

<span data-ttu-id="d32cb-109">Wir beginnen mit einer kurzen Erläuterung der Datenbindung.</span><span class="sxs-lookup"><span data-stu-id="d32cb-109">We’ll start with a quick discussion of data binding - what it is and how it works.</span></span> <span data-ttu-id="d32cb-110">Im Anschluss daran fügen wir eine **ListView** (Listenansicht) zur Benutzeroberfläche hinzu, fügen eine Datenbindung hinzu und passen die Datenbindung mit weiteren Features an.</span><span class="sxs-lookup"><span data-stu-id="d32cb-110">Then we'll add a **ListView** to the UI, add data binding, and customize the data binding with additional features.</span></span> 

## <a name="what-do-you-need-to-know"></a><span data-ttu-id="d32cb-111">Wissenswertes</span><span class="sxs-lookup"><span data-stu-id="d32cb-111">What do you need to know?</span></span>

<span data-ttu-id="d32cb-112">Das Binden von Daten ist eine Möglichkeit, die Daten einer App auf ihrer Benutzeroberfläche anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="d32cb-112">Data binding is a way to display an app's data in its UI.</span></span> <span data-ttu-id="d32cb-113">Dies ermöglicht eine Art *Aufgabentrennung* in der App, um die Benutzeroberfläche vom anderen Code zu separieren.</span><span class="sxs-lookup"><span data-stu-id="d32cb-113">This allows for *separation of concerns* in your app, keeping your UI separate from your other code.</span></span> <span data-ttu-id="d32cb-114">Dadurch entsteht ein übersichtlicheres konzeptionelles Modell, das leichter zu lesen und besser zu pflegen ist.</span><span class="sxs-lookup"><span data-stu-id="d32cb-114">This creates a cleaner conceptual model that’s easier to read and maintain.</span></span>

<span data-ttu-id="d32cb-115">Jede Bindung besteht aus zwei Teilen:</span><span class="sxs-lookup"><span data-stu-id="d32cb-115">Every data binding has two pieces:</span></span>

* <span data-ttu-id="d32cb-116">Einer Quelle, die die zu bindenden Daten bereitstellt</span><span class="sxs-lookup"><span data-stu-id="d32cb-116">A source which provides the data to be bound.</span></span>
* <span data-ttu-id="d32cb-117">Einem Ziel auf der Benutzeroberfläche, wo die Daten angezeigt werden</span><span class="sxs-lookup"><span data-stu-id="d32cb-117">A target in the UI where the data is displayed.</span></span>

<span data-ttu-id="d32cb-118">Um eine Datenbindung zu implementieren, müssen Sie der Quelle, die die Daten für die Bindung bereitstellt, Code hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="d32cb-118">To implement a data binding, you'll need to add code to your source that provides data to the binding.</span></span> <span data-ttu-id="d32cb-119">Sie müssen auch eine der beiden Markuperweiterungen zu Ihrem XAML-Code hinzufügen, um die Eigenschaften der Datenquelle anzugeben.</span><span class="sxs-lookup"><span data-stu-id="d32cb-119">You'll also need to add one of two markup extensions to your XAML to specify the data source properties.</span></span> <span data-ttu-id="d32cb-120">Dies ist der wichtigste Unterschied zwischen beiden Erweiterungen:</span><span class="sxs-lookup"><span data-stu-id="d32cb-120">Here's the key difference between the two:</span></span>

* <span data-ttu-id="d32cb-121">[**x:Bind**](../xaml-platform/x-bind-markup-extension.md) ist stark typisiert und generiert Code zum Zeitpunkt der Kompilierung, um die Leistung zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="d32cb-121">[**x:Bind**](../xaml-platform/x-bind-markup-extension.md) is strongly typed, and generates code at compile time for better performance.</span></span> <span data-ttu-id="d32cb-122">Standardmäßig wird für x:Bind eine einmalige Bindung verwendet, die die schnelle Anzeige von schreibgeschützten Daten optimiert, die sich nicht ändern.</span><span class="sxs-lookup"><span data-stu-id="d32cb-122">x:Bind defaults to a one-time binding, which optimizes for the fast display of read-only data that doesn't change.</span></span>
* <span data-ttu-id="d32cb-123">[**Binding**](../xaml-platform/binding-markup-extension.md) ist schwach typisiert und wird zur Laufzeit zusammengesetzt.</span><span class="sxs-lookup"><span data-stu-id="d32cb-123">[**Binding**](../xaml-platform/binding-markup-extension.md) is weakly typed and assembled at runtime.</span></span> <span data-ttu-id="d32cb-124">Dies führt zu einer schlechteren Leistung als bei x:Bind.</span><span class="sxs-lookup"><span data-stu-id="d32cb-124">This results in poorer performance than with x:Bind.</span></span> <span data-ttu-id="d32cb-125">In fast allen Fällen sollten Sie x:Bind anstelle von Bindung verwenden.</span><span class="sxs-lookup"><span data-stu-id="d32cb-125">In almost all cases, you should use x:Bind instead of Binding.</span></span> <span data-ttu-id="d32cb-126">Allerdings ist Binding wahrscheinlich noch in älterem Code zu finden.</span><span class="sxs-lookup"><span data-stu-id="d32cb-126">However, you're likely to encounter it in older code.</span></span> <span data-ttu-id="d32cb-127">Bei Binding wird standardmäßig eine unidirektionale Datenübertragung verwendet, die für schreibgeschützte Daten optimiert ist, die sich an der Quelle ändern können.</span><span class="sxs-lookup"><span data-stu-id="d32cb-127">Binding defaults to one-way data transfer, which optimizes for read-only data that can change at the source.</span></span>

<span data-ttu-id="d32cb-128">Wir empfehlen, immer möglichst **x:Bind** zu verwenden. Dies wird in diesem Artikel anhand von Codeausschnitten veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="d32cb-128">We recommend you use **x:Bind** whenever possible, and we'll be showing it in the snippets in this article.</span></span> <span data-ttu-id="d32cb-129">Weitere Informationen zu den Unterschieden finden Sie unter [Vergleich der Features von {x:Bind} und {Binding}](../data-binding/data-binding-in-depth.md#xbind-and-binding-feature-comparison).</span><span class="sxs-lookup"><span data-stu-id="d32cb-129">For more information on the differences, see [{x:Bind} and {Binding} feature comparison](../data-binding/data-binding-in-depth.md#xbind-and-binding-feature-comparison).</span></span>

## <a name="create-a-data-source"></a><span data-ttu-id="d32cb-130">Erstellen einer Datenquelle</span><span class="sxs-lookup"><span data-stu-id="d32cb-130">Create a data source</span></span>

<span data-ttu-id="d32cb-131">Zunächst benötigen Sie eine Klasse zur Darstellung Ihrer Kundendaten.</span><span class="sxs-lookup"><span data-stu-id="d32cb-131">First, you'll need a class to represent your Customer data.</span></span> <span data-ttu-id="d32cb-132">Um Ihnen einen Referenzpunkt zu geben, zeigen wir den Prozess anhand dieses einfachen Beispiels:</span><span class="sxs-lookup"><span data-stu-id="d32cb-132">To give you a reference point, we'll be showing the process on this bare-bones example:</span></span>

```csharp
public class Customer
{
    public string Name { get; set; }
}
```

## <a name="create-a-list"></a><span data-ttu-id="d32cb-133">Erstellen einer Liste</span><span class="sxs-lookup"><span data-stu-id="d32cb-133">Create a list</span></span>

<span data-ttu-id="d32cb-134">Bevor Sie Kunden anzeigen können, müssen Sie eine Liste dieser Kunden erstellen, in der sie gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="d32cb-134">Before you can display any customers, you need to create the list to hold them.</span></span> <span data-ttu-id="d32cb-135">Die [Listenansicht](../design/controls-and-patterns/listview-and-gridview.md) ist ein einfaches XAML-Steuerelement, das sich für diese Aufgabe perfekt eignet.</span><span class="sxs-lookup"><span data-stu-id="d32cb-135">The [List View](../design/controls-and-patterns/listview-and-gridview.md) is a basic XAML control which is ideal for this task.</span></span> <span data-ttu-id="d32cb-136">Ihre Listenansicht erfordert eine Position auf der Seite und gleich auch einen Wert für ihre **ItemSource**-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="d32cb-136">Your ListView currently requires a position on the page, and will shortly need a value for its **ItemSource** property.</span></span>

```xaml
<ListView ItemsSource=""
    HorizontalAlignment="Center"
    VerticalAlignment="Center"/>
```

<span data-ttu-id="d32cb-137">Nachdem Sie Daten an Ihre ListView gebunden haben, empfehlen wir Ihnen, zur Dokumentation zurückzukehren und mit der Anpassung der Darstellung und des Layouts zu experimentieren.</span><span class="sxs-lookup"><span data-stu-id="d32cb-137">Once you have bound data to your ListView, we encourage you to return to the documentation, and experiment with customizing its appearance and layout to best fit your needs.</span></span>

## <a name="bind-data-to-your-list"></a><span data-ttu-id="d32cb-138">Binden von Daten an Ihre Liste</span><span class="sxs-lookup"><span data-stu-id="d32cb-138">Bind data to your list</span></span>

<span data-ttu-id="d32cb-139">Nun, da Sie eine grundlegende Oberfläche zum Speichern der Bindungen erstellt haben, müssen Sie Ihre Quelle konfigurieren, um sie bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="d32cb-139">Now that you've made a basic UI to hold your bindings, you need to configure your source to provide them.</span></span> <span data-ttu-id="d32cb-140">Dies ist ein Beispiel hierfür:</span><span class="sxs-lookup"><span data-stu-id="d32cb-140">Here's an example of how this may be done:</span></span>

```csharp
public sealed partial class MainPage : Page
{
    public ObservableCollection<Customer> Customers { get; }
        = new ObservableCollection<Customer>();

    public MainPage()
    {
        this.InitializeComponent();
          // Add some customers
        this.Customers.Add(new Customer() { Name = "NAME1"});
        this.Customers.Add(new Customer() { Name = "NAME2"});
        this.Customers.Add(new Customer() { Name = "NAME3"});
    }
}
```
```xaml
<ListView ItemsSource="{x:Bind Customers}"
    HorizontalAlignment="Center"
    VerticalAlignment="Center">
    <ListView.ItemTemplate>
        <DataTemplate x:DataType="local:Customer">
            <TextBlock Text="{x:Bind Name}"/>
        </DataTemplate>
    </ListView.ItemTemplate>
</ListView>
```

<span data-ttu-id="d32cb-141">In der [Übersicht über Datenbindung](../data-binding/data-binding-quickstart.md#binding-to-a-collection-of-items) werden Sie durch ein ähnliches Problem geführt (siehe Abschnitt zum Binden an eine Sammlung von Elementen).</span><span class="sxs-lookup"><span data-stu-id="d32cb-141">The [Data Binding overview](../data-binding/data-binding-quickstart.md#binding-to-a-collection-of-items) walks you through a similar problem, in its section about binding to a collection of items.</span></span> <span data-ttu-id="d32cb-142">Unser Beispiel zeigt die folgenden wesentlichen Schritte:</span><span class="sxs-lookup"><span data-stu-id="d32cb-142">Our example here shows the following crucial steps:</span></span>

* <span data-ttu-id="d32cb-143">Erstellen Sie im Code hinter Ihrer Benutzeroberfläche eine Eigenschaft vom Typ **ObservableCollection<T>**, um Ihre Kundenobjekte abzulegen.</span><span class="sxs-lookup"><span data-stu-id="d32cb-143">In the code-behind of your UI, create a property of type **ObservableCollection<T>** to hold your Customer objects.</span></span>
* <span data-ttu-id="d32cb-144">Binden Sie die **ItemSource** Ihrer Listenansicht an diese Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="d32cb-144">Bind your ListView’s **ItemSource** to that property.</span></span>
* <span data-ttu-id="d32cb-145">Stellen Sie ein einfaches **ItemTemplate** für die Listenansicht bereit. Diese Vorlage legt fest, wie jedes Element in der Liste angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="d32cb-145">Provide a basic **ItemTemplate** for the ListView, which will configure how each item in the list is displayed.</span></span>

<span data-ttu-id="d32cb-146">Schauen Sie sich gern noch einmal die Dokumente zur [Listenansicht](../design/controls-and-patterns/listview-and-gridview.md) an, wenn Sie das Layout anpassen, eine Auswahl von Elementen hinzufügen oder das soeben erstellte **DataTemplate** anpassen möchten.</span><span class="sxs-lookup"><span data-stu-id="d32cb-146">Feel free to look back at the [List View](../design/controls-and-patterns/listview-and-gridview.md) docs if you want to customize layout, add item selection, or tweak the **DataTemplate** you just made.</span></span> <span data-ttu-id="d32cb-147">Aber was geschieht, wenn Sie Ihre Kunden bearbeiten möchten?</span><span class="sxs-lookup"><span data-stu-id="d32cb-147">But what if you want to edit your Customers?</span></span>

## <a name="edit-your-customers-through-the-ui"></a><span data-ttu-id="d32cb-148">Bearbeiten der Kunden über die Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="d32cb-148">Edit your Customers through the UI</span></span>

<span data-ttu-id="d32cb-149">Sie haben Kunden in einer Liste angezeigt, aber die Datenbindung bietet noch mehr Möglichkeiten.</span><span class="sxs-lookup"><span data-stu-id="d32cb-149">You’ve displayed customers in a list, but data B=binding lets you do more.</span></span> <span data-ttu-id="d32cb-150">Was wäre, wenn Sie Ihre Daten direkt über die Benutzeroberfläche bearbeiten könnten?</span><span class="sxs-lookup"><span data-stu-id="d32cb-150">What if you could edit your data directly from the UI?</span></span> <span data-ttu-id="d32cb-151">Zu diesem Zweck müssen wir zunächst über die drei Modi der Datenbindung sprechen:</span><span class="sxs-lookup"><span data-stu-id="d32cb-151">To do this, let’s first talk about the three modes of data binding:</span></span>

* <span data-ttu-id="d32cb-152">*Einmalig*: Diese Datenbindung wird nur einmal aktiviert. Sie reagiert nicht auf Änderungen.</span><span class="sxs-lookup"><span data-stu-id="d32cb-152">*One-Time*: This data binding is only activated once, and doesn’t react to changes.</span></span>
* <span data-ttu-id="d32cb-153">*Unidirektional*: Diese Datenbindung aktualisiert die Benutzeroberfläche mit allen Änderungen, die an der Datenquelle vorgenommen werden.</span><span class="sxs-lookup"><span data-stu-id="d32cb-153">*One-Way*: This data binding will update the UI with any changes made to the data source.</span></span>
* <span data-ttu-id="d32cb-154">*Bidirektional*: Diese Datenbindung aktualisiert die Benutzeroberfläche mit allen Änderungen, die an der Datenquelle vorgenommen wurden, und aktualisiert die Daten außerdem mit allen Änderungen auf der Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="d32cb-154">*Two-Way*: This data binding will update the UI with any changes made to the data source, and also update the data with any changes made within the UI.</span></span>

<span data-ttu-id="d32cb-155">Wenn Sie die Codeausschnitte von vorher befolgt haben, verwendet Ihre Bindung x:Bind und gibt keinen Modus an; folglich handelt es sich um eine einmalige Bindung.</span><span class="sxs-lookup"><span data-stu-id="d32cb-155">If you've followed the code snippets from earlier, the binding you made uses x:Bind and doesn't specify a mode, making it a One-Time binding.</span></span> <span data-ttu-id="d32cb-156">Wenn Sie Ihre Kunden direkt über die Benutzeroberfläche bearbeiten möchten, müssen Sie die Bindung in eine bidirektionale Bindung ändern, damit die Änderungen von den Daten zurück an die Kundenobjekte übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="d32cb-156">If you want to edit your Customers directly from the UI, you'll need to change it to a Two-Way binding, so that changes from the data will be passed back to the Customer objects.</span></span> <span data-ttu-id="d32cb-157">Weitere Informationen finden Sie unter [Datenbindung im Detail](../data-binding/data-binding-in-depth.md).</span><span class="sxs-lookup"><span data-stu-id="d32cb-157">[Data binding in depth](../data-binding/data-binding-in-depth.md) has more information.</span></span>

<span data-ttu-id="d32cb-158">Die bidirektionale Bindung aktualisiert ebenfalls die Benutzeroberfläche, wenn die Datenquelle geändert wird.</span><span class="sxs-lookup"><span data-stu-id="d32cb-158">Two-way binding will also update the UI if the data source is changed.</span></span> <span data-ttu-id="d32cb-159">Damit dies funktioniert, müssen Sie [**INotifyPropertyChanged**](https://msdn.microsoft.com/library/system.componentmodel.inotifypropertychanged(d=robot).aspx) an der Quelle implementieren und sicherstellen, dass durch die Eigenschaftseinstellungen das Ereignis **PropertyChanged** ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="d32cb-159">For this to work, you must implement [**INotifyPropertyChanged**](https://msdn.microsoft.com/library/system.componentmodel.inotifypropertychanged(d=robot).aspx) on the source and ensure its property setters raise the **PropertyChanged** event.</span></span> <span data-ttu-id="d32cb-160">Üblicherweise rufen diese eine Hilfsmethode wie **OnPropertyChanged** auf, wie unten dargestellt:</span><span class="sxs-lookup"><span data-stu-id="d32cb-160">Common practice is to have them call a helper method like the **OnPropertyChanged** method, as shown below:</span></span>

```csharp
public class Customer : INotifyPropertyChanged
{
    private string _name;
    public string Name
    {
        get => _name;
        set
        {
            if (_name != value)
                {
                    _name = value;
                    this.OnPropertyChanged();
                }
        }
    }
    public event PropertyChangedEventHandler PropertyChanged;

    public void OnPropertyChanged([CallerMemberName] string propertyName = null) =>
        this.PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(propertyName));
}
```
<span data-ttu-id="d32cb-161">Machen Sie dann den Text in der Listenansicht bearbeitbar, indem Sie ein **TextBox** anstelle eines **TextBlock** verwenden. Stellen Sie sicher, dass Sie den **Modus** für Ihre Datenbindung auf **TwoWay** (bidirektional) festlegen.</span><span class="sxs-lookup"><span data-stu-id="d32cb-161">Then make the text in your ListView editable by using a **TextBox** instead of a **TextBlock**, and ensure that you set the **Mode** on your data bindings to **TwoWay**.</span></span>

```xaml
<ListView ItemsSource="{x:Bind Customers}"
    HorizontalAlignment="Center"
    VerticalAlignment="Center">
    <ListView.ItemTemplate>
        <DataTemplate x:DataType="local:Customer">
            <TextBox Text="{x:Bind Name, Mode=TwoWay}"/>
        </DataTemplate>
    </ListView.ItemTemplate>
</ListView>
```

<span data-ttu-id="d32cb-162">Sie können schnell sicherzustellen, dass dies funktioniert, indem Sie eine zweite Listenansicht mit TextBox-Steuerelementen und unidirektionalen (OneWay) Bindungen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="d32cb-162">A quick way to ensure that this works is to add a second ListView with TextBox controls and OneWay bindings.</span></span> <span data-ttu-id="d32cb-163">Die Werte in der zweiten Liste werden automatisch geändert, wenn die erste bearbeitet wird.</span><span class="sxs-lookup"><span data-stu-id="d32cb-163">The values in the second list will automatically change as you edit the first one.</span></span>

> [!NOTE]
> <span data-ttu-id="d32cb-164">Das direkte Bearbeiten innerhalb einer Listenansicht ist eine einfache Möglichkeit, die bidirektionale Bindung in Aktion zu zeigen. Dies kann jedoch zu Komplikationen bei der Verwendbarkeit führen.</span><span class="sxs-lookup"><span data-stu-id="d32cb-164">Editing directly inside a ListView is a simple way to show Two-Way binding in action, but can lead to usability complications.</span></span> <span data-ttu-id="d32cb-165">Wenn Sie Ihre App weiter vertiefen möchten, erwägen Sie, [andere XAML-Steuerelemente](../design/controls-and-patterns/controls-and-events-intro.md) zum Bearbeiten Ihrer Daten zu verwenden und Ihre Listansicht schreibgeschützt zu lassen.</span><span class="sxs-lookup"><span data-stu-id="d32cb-165">If you're looking to take your app further, consider using [other XAML controls](../design/controls-and-patterns/controls-and-events-intro.md) to edit your data, and keep your ListView as display-only.</span></span>

## <a name="going-further"></a><span data-ttu-id="d32cb-166">Vertiefung</span><span class="sxs-lookup"><span data-stu-id="d32cb-166">Going Further</span></span>

<span data-ttu-id="d32cb-167">Nun, da Sie eine Liste von Kunden mit einer bidirektionalen Bindung erstellt haben, können Sie noch einmal die Dokumente durcharbeiten, für die wir Links zur Verfügung gestellt haben, und etwas experimentieren.</span><span class="sxs-lookup"><span data-stu-id="d32cb-167">Now that you’ve created a list of customers with two-way binding, feel free to go back through the docs we’ve linked you to and experiment.</span></span> <span data-ttu-id="d32cb-168">Sie können auch unser [Datenbindungs-Tutorial](../data-binding/xaml-basics-data-binding.md) abrufen, wenn Sie eine schrittweise Anleitung für die grundlegenden und erweiterten Bindungen erhalten oder sich näher mit Steuerelementen wie die [Master/Detail-Muster](../design/controls-and-patterns/master-details.md) beschäftigen möchten, um eine stabilere Benutzeroberfläche zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="d32cb-168">You can also check out our [data binding tutorial](../data-binding/xaml-basics-data-binding.md) if you want a step-by-step walkthrough of basic and advanced bindings, or investigate controls like the [master/details pattern](../design/controls-and-patterns/master-details.md) to make a more robust UI.</span></span>

## <a name="useful-apis-and-docs"></a><span data-ttu-id="d32cb-169">Nützliche APIs und Dokumente</span><span class="sxs-lookup"><span data-stu-id="d32cb-169">Useful APIs and docs</span></span>

<span data-ttu-id="d32cb-170">Nachfolgend finden Sie eine kurze Zusammenfassung zu den APIs und weiterer nützlicher Dokumentation, die Sie bei Ihren ersten Schritten rund um die Datenbindung unterstützen.</span><span class="sxs-lookup"><span data-stu-id="d32cb-170">Here's a quick summary of APIs and other useful documentation to help you get started working with Data Binding.</span></span>

### <a name="useful-apis"></a><span data-ttu-id="d32cb-171">Nützliche APIs</span><span class="sxs-lookup"><span data-stu-id="d32cb-171">Useful APIs</span></span>

| <span data-ttu-id="d32cb-172">API</span><span class="sxs-lookup"><span data-stu-id="d32cb-172">API</span></span> | <span data-ttu-id="d32cb-173">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d32cb-173">Description</span></span> |
|------|---------------|
| [<span data-ttu-id="d32cb-174">Datenvorlage</span><span class="sxs-lookup"><span data-stu-id="d32cb-174">Data template</span></span>](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.DataTemplate) | <span data-ttu-id="d32cb-175">Beschreibt die visuelle Struktur eines Datenobjekts, was die Anzeige bestimmter Elementen auf der Benutzeroberfläche ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="d32cb-175">Describes the visual structure of a data object, allowing for the display of specific elements in the UI.</span></span> |
| [<span data-ttu-id="d32cb-176">x:Bind</span><span class="sxs-lookup"><span data-stu-id="d32cb-176">x:Bind</span></span>](../xaml-platform/x-bind-markup-extension.md) | <span data-ttu-id="d32cb-177">Dokumentation zur empfohlenen x:Bind-Markuperweiterung.</span><span class="sxs-lookup"><span data-stu-id="d32cb-177">Documentation on the recommended x:Bind markup extension.</span></span> |
| [<span data-ttu-id="d32cb-178">Binding</span><span class="sxs-lookup"><span data-stu-id="d32cb-178">Binding</span></span>](../xaml-platform/binding-markup-extension.md) | <span data-ttu-id="d32cb-179">Dokumentation zur älteren Binding-Markuperweiterung.</span><span class="sxs-lookup"><span data-stu-id="d32cb-179">Documentation on the older Binding markup extension.</span></span> |
| [<span data-ttu-id="d32cb-180">ListView (Listenansicht)</span><span class="sxs-lookup"><span data-stu-id="d32cb-180">ListView</span></span>](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ListView) | <span data-ttu-id="d32cb-181">Stellt ein UI-Steuerelement dar, das Datenelemente in einem vertikalen Stapel anzeigt.</span><span class="sxs-lookup"><span data-stu-id="d32cb-181">A UI control that displays data items in a vertical stack.</span></span> |
| [<span data-ttu-id="d32cb-182">TextBox (Textfeld)</span><span class="sxs-lookup"><span data-stu-id="d32cb-182">TextBox</span></span>](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.TextBox) | <span data-ttu-id="d32cb-183">Stellt ein einfaches Text-Steuerelement zum Anzeigen bearbeitbarer Textdaten auf der Benutzeroberfläche dar.</span><span class="sxs-lookup"><span data-stu-id="d32cb-183">A basic text control for displaying editable text data in the UI.</span></span> |
| [<span data-ttu-id="d32cb-184">INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="d32cb-184">INotifyPropertyChanged</span></span>](https://msdn.microsoft.com/library/system.componentmodel.inotifypropertychanged(d=robot).aspx) | <span data-ttu-id="d32cb-185">Schnittstelle, um Daten feststellbar („observable“) zu machen und für eine Datenbindung bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="d32cb-185">The interface for making data observable, providing it to a data binding.</span></span> |
| [<span data-ttu-id="d32cb-186">ItemsControl</span><span class="sxs-lookup"><span data-stu-id="d32cb-186">ItemsControl</span></span>](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ItemsControl) | <span data-ttu-id="d32cb-187">Die **ItemsSource**-Eigenschaft dieser Klasse ermöglicht die Bindung einer Listenansicht an eine Datenquelle.</span><span class="sxs-lookup"><span data-stu-id="d32cb-187">The **ItemsSource** property of this class allows a ListView to bind to a data source.</span></span> |

### <a name="useful-docs"></a><span data-ttu-id="d32cb-188">Nützliche Dokumente</span><span class="sxs-lookup"><span data-stu-id="d32cb-188">Useful docs</span></span>

| <span data-ttu-id="d32cb-189">Thema</span><span class="sxs-lookup"><span data-stu-id="d32cb-189">Topic</span></span> | <span data-ttu-id="d32cb-190">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d32cb-190">Description</span></span> |
|-------|----------------|
| [<span data-ttu-id="d32cb-191">Datenbindung im Detail</span><span class="sxs-lookup"><span data-stu-id="d32cb-191">Data binding in depth</span></span>](../data-binding/data-binding-in-depth.md) | <span data-ttu-id="d32cb-192">Eine grundlegende Übersicht über die Prinzipien der Datenbindung</span><span class="sxs-lookup"><span data-stu-id="d32cb-192">A basic overview of data binding principles</span></span> |
| [<span data-ttu-id="d32cb-193">Übersicht über Datenbindung</span><span class="sxs-lookup"><span data-stu-id="d32cb-193">Data Binding overview</span></span>](../data-binding/data-binding-quickstart.md) | <span data-ttu-id="d32cb-194">Ausführliche konzeptionelle Informationen zur Datenbindung.</span><span class="sxs-lookup"><span data-stu-id="d32cb-194">Detailed conceptual information on data binding.</span></span> |
| [<span data-ttu-id="d32cb-195">Listenansicht</span><span class="sxs-lookup"><span data-stu-id="d32cb-195">List View</span></span>](../design/controls-and-patterns/listview-and-gridview.md) | <span data-ttu-id="d32cb-196">Informationen zum Erstellen und Konfigurieren einer Listenansicht, einschließlich der Implementierung einer Datenvorlage (**DataTemplate**)</span><span class="sxs-lookup"><span data-stu-id="d32cb-196">Information on creating and configuring a ListView, including implementation of a **DataTemplate**</span></span> |

## <a name="useful-code-samples"></a><span data-ttu-id="d32cb-197">Nützliche Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="d32cb-197">Useful code samples</span></span>

| <span data-ttu-id="d32cb-198">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="d32cb-198">Code sample</span></span> | <span data-ttu-id="d32cb-199">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d32cb-199">Description</span></span> |
|-----------------|---------------|
| [<span data-ttu-id="d32cb-200">Datenbindungs-Tutorial</span><span class="sxs-lookup"><span data-stu-id="d32cb-200">Data binding tutorial</span></span>](../data-binding/xaml-basics-data-binding.md) | <span data-ttu-id="d32cb-201">Eine schrittweise Anleitung durch die Grundlagen der Datenbindung.</span><span class="sxs-lookup"><span data-stu-id="d32cb-201">A step-by-step guided experience through the basics of data binding.</span></span> |
| [<span data-ttu-id="d32cb-202">Listenansicht und Rasteransicht</span><span class="sxs-lookup"><span data-stu-id="d32cb-202">ListView and GridView</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlListView) | <span data-ttu-id="d32cb-203">Erkunden Sie ausführlichere Listenansichten mit Datenbindung.</span><span class="sxs-lookup"><span data-stu-id="d32cb-203">Explore more elaborate ListViews with data binding.</span></span> |
| [<span data-ttu-id="d32cb-204">QuizGame</span><span class="sxs-lookup"><span data-stu-id="d32cb-204">QuizGame</span></span>](https://github.com/Microsoft/Windows-appsample-networkhelper) | <span data-ttu-id="d32cb-205">Hier sehen Sie die Datenbindung in Aktion, einschließlich der **BindableBase**-Klasse (im Ordner „Common“) für eine Standardimplementierung von **INotifyPropertyChanged**.</span><span class="sxs-lookup"><span data-stu-id="d32cb-205">See data binding in action, including the **BindableBase** class (in the "Common" folder) for a standard implementation of **INotifyPropertyChanged**.</span></span> |
