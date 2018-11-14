---
author: mcleblanc
ms.assetid: 089660A2-7CAE-4911-9994-F619C5D22287
title: Beispieldaten für die Entwurfsoberfläche und Prototyperstellung
description: Möglicherweise ist es nicht möglich oder nicht erwünscht (z. B. aus Gründen des Datenschutzes oder der Leistung), dass Ihre App Livedaten auf der Entwurfsoberfläche von Microsoft Visual Studio oder Blend für Visual Studio anzeigt.
ms.author: markl
ms.date: 02/08/2017
ms.topic: article
keywords: windows 10, uwp
ms.localizationpriority: medium
ms.openlocfilehash: 269d51ec6005bcd61ac01a66d72c34bdb2901add
ms.sourcegitcommit: 71e8eae5c077a7740e5606298951bb78fc42b22c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "6654236"
---
<a name="sample-data-on-the-design-surface-and-for-prototyping"></a><span data-ttu-id="2f15c-104">Beispieldaten für die Entwurfsoberfläche und Prototyperstellung</span><span class="sxs-lookup"><span data-stu-id="2f15c-104">Sample data on the design surface, and for prototyping</span></span>
=============================================================================================



<span data-ttu-id="2f15c-105">**Hinweis:** der Grad, zu dem Sie Beispieldaten – und wie viel wird – hängen davon ab, ob die Bindungen [{Binding} Markuperweiterung](https://msdn.microsoft.com/library/windows/apps/Mt204782) oder der [{X: Bind}-Markuperweiterung](https://msdn.microsoft.com/library/windows/apps/Mt204783).</span><span class="sxs-lookup"><span data-stu-id="2f15c-105">**Note**The degree to which you need sample data—and how much it will help you—depends on whether your bindings use the [{Binding} markup extension](https://msdn.microsoft.com/library/windows/apps/Mt204782) or the [{x:Bind} markup extension](https://msdn.microsoft.com/library/windows/apps/Mt204783).</span></span> <span data-ttu-id="2f15c-106">Die in diesem Thema beschriebenen Verfahren basieren auf der Verwendung eines [**DataContext**](https://msdn.microsoft.com/library/windows/apps/BR208713) und eignen sich deshalb nur für **{Binding}**.</span><span class="sxs-lookup"><span data-stu-id="2f15c-106">The techniques described in this topic are based on the use of a [**DataContext**](https://msdn.microsoft.com/library/windows/apps/BR208713), so they're only appropriate for **{Binding}**.</span></span> <span data-ttu-id="2f15c-107">Wenn Sie jedoch **{x:Bind}** verwenden, zeigen die Bindungen zumindest Platzhalterwerte auf der Entwurfsoberfläche an (selbst für Elementsteuerelemente). Deshalb besteht ein geringerer Bedarf an Beispieldaten.</span><span class="sxs-lookup"><span data-stu-id="2f15c-107">But if you're using **{x:Bind}** then your bindings at least show placeholder values on the design surface (even for items controls), so you don't have quite the same need for sample data.</span></span>

<span data-ttu-id="2f15c-108">Möglicherweise ist es nicht möglich oder nicht erwünscht (z.B. aus Gründen des Datenschutzes oder der Leistung), dass Ihre App Livedaten auf der Entwurfsoberfläche von Microsoft Visual Studio oder Blend für Visual Studio anzeigt.</span><span class="sxs-lookup"><span data-stu-id="2f15c-108">It may be impossible or undesirable (perhaps for reasons of privacy or performance) for your app to display live data on the design surface in Microsoft Visual Studio or Blend for Visual Studio.</span></span> <span data-ttu-id="2f15c-109">Es gibt mehrere Möglichkeiten, Entwurfszeit-Beispieldaten zu verwenden, damit die Steuerelemente mit Daten aufgefüllt werden (sodass Sie das Layout, die Vorlagen und andere visuelle Eigenschaften der App bearbeiten können).</span><span class="sxs-lookup"><span data-stu-id="2f15c-109">In order to have your controls populated with data (so that you can work on your app's layout, templates, and other visual properties), there are various ways in which you can use design-time sample data.</span></span> <span data-ttu-id="2f15c-110">Beispieldaten können auch hilfreich sein und Zeit sparen, wenn Sie eine App als Skizze (oder Prototyp) erstellen.</span><span class="sxs-lookup"><span data-stu-id="2f15c-110">Sample data can also be really useful and time-saving if you're building a sketch (or prototype) app.</span></span> <span data-ttu-id="2f15c-111">Sie können zur Laufzeit Beispieldaten in der Skizze oder im Prototyp verwenden, um Ihre Ideen zu veranschaulichen, ohne echte Livedaten nutzen zu müssen.</span><span class="sxs-lookup"><span data-stu-id="2f15c-111">You can use sample data in your sketch or prototype at run-time to illustrate your ideas without going as far as connecting to real, live data.</span></span>

**<span data-ttu-id="2f15c-112">Beispiel-Apps zur Veranschaulichung von {Binding}</span><span class="sxs-lookup"><span data-stu-id="2f15c-112">Sample apps that demonstrate {Binding}</span></span>**

-   <span data-ttu-id="2f15c-113">Laden Sie die App [Bookstore1](http://go.microsoft.com/fwlink/?linkid=532950) herunter.</span><span class="sxs-lookup"><span data-stu-id="2f15c-113">Download the [Bookstore1](http://go.microsoft.com/fwlink/?linkid=532950) app.</span></span>
-   <span data-ttu-id="2f15c-114">Laden Sie die App [Bookstore2](http://go.microsoft.com/fwlink/?linkid=532952) herunter.</span><span class="sxs-lookup"><span data-stu-id="2f15c-114">Download the [Bookstore2](http://go.microsoft.com/fwlink/?linkid=532952) app.</span></span>

<a name="setting-datacontext-in-markup"></a><span data-ttu-id="2f15c-115">Festlegen des DataContext im Markup</span><span class="sxs-lookup"><span data-stu-id="2f15c-115">Setting DataContext in markup</span></span>
-----------------------------

<span data-ttu-id="2f15c-116">Entwickler verwenden häufig imperativen Code (in CodeBehind), um den [**DataContext**](https://msdn.microsoft.com/library/windows/apps/BR208713) einer Seite oder eines Benutzersteuerelements auf eine Ansichtsmodellinstanz festzulegen.</span><span class="sxs-lookup"><span data-stu-id="2f15c-116">It's a fairly common developer practice to use imperative code (in code-behind) to set a page or user control's [**DataContext**](https://msdn.microsoft.com/library/windows/apps/BR208713) to a view model instance.</span></span>

``` csharp
public MainPage()
{
    InitializeComponent();
    this.DataContext = new BookstoreViewModel();
}
```

<span data-ttu-id="2f15c-117">Jedoch stehen Ihnen bei Verwendung dieses Verfahrens weniger Designmöglichkeiten für die Seite zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="2f15c-117">But if you do that then your page isn't as "designable" as it could be.</span></span> <span data-ttu-id="2f15c-118">Der Grund dafür ist, dass beim Öffnen der XAML-Seite in Visual Studio oder Blend für Visual Studio der imperative Code, der den **DataContext**-Wert zuweist, nie ausgeführt wird (es wird nicht einmal der CodeBehind ausgeführt).</span><span class="sxs-lookup"><span data-stu-id="2f15c-118">The reason is that when your XAML page is opened in Visual Studio or Blend for Visual Studio, the imperative code that assigns the **DataContext** value is never run (in fact, none of your code-behind is executed).</span></span> <span data-ttu-id="2f15c-119">Selbstverständlich wird von den XAML-Tools das Markup analysiert, und sie instanziieren alle in ihm deklarierten Objekte, sie instanziieren jedoch nicht den Typ der Seite.</span><span class="sxs-lookup"><span data-stu-id="2f15c-119">The XAML tools do of course parse your markup and instantiate any objects declared in it, but they don't actually instantiate your page's type itself.</span></span> <span data-ttu-id="2f15c-120">Deshalb werden in den Steuerelementen und im Dialogfeld **Datenbindung erstellen** keine Daten angezeigt, und es ist schwieriger, das Format und Layout der Seite zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="2f15c-120">The result is that you won't see any data in your controls or in the **Create Data Binding** dialog, and your page will be more challenging to style and to lay out.</span></span>

![Benutzeroberfläche mit geringen Entwurfsmöglichkeiten](images/displaying-data-in-the-designer-01.png)

<span data-ttu-id="2f15c-122">Als Abhilfe können Sie die **DataContext**-Zuweisung auskommentieren und den **DataContext** stattdessen im Seitenmarkup festlegen.</span><span class="sxs-lookup"><span data-stu-id="2f15c-122">The first remedy to try is to comment out that **DataContext** assignment and set the **DataContext** in your page markup instead.</span></span> <span data-ttu-id="2f15c-123">Dies bewirkt, dass die Livedaten zur Entwurfszeit und zur Laufzeit angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="2f15c-123">That way, your live data shows up at design-time as well as at run-time.</span></span> <span data-ttu-id="2f15c-124">Öffnen Sie hierzu zunächst die XAML-Seite.</span><span class="sxs-lookup"><span data-stu-id="2f15c-124">To do this, first open your XAML page.</span></span> <span data-ttu-id="2f15c-125">Klicken Sie dann im Fenster **Dokumentgliederung** auf das Stammentwurfselement (in der Regel mit der Bezeichnung **\[Page\]**), um es auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="2f15c-125">Then, in the **Document Outline** window, click the root designable element (usually with the label **\[Page\]**) to select it.</span></span> <span data-ttu-id="2f15c-126">Suchen Sie im **Eigenschaftenfenster** die **DataContext**-Eigenschaft (in der Kategorie „Allgemein“), und klicken Sie dann auf **Neu**.</span><span class="sxs-lookup"><span data-stu-id="2f15c-126">In the **Properties** window, find the **DataContext** property (inside the Common category), and then click **New**.</span></span> <span data-ttu-id="2f15c-127">Klicken Sie im Dialogfeld **Objekt auswählen** auf den Ansichtsmodelltyp, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="2f15c-127">Click your view model type from the **Select Object** dialog box, and then click **OK**.</span></span>

![Benutzeroberfläche zum Festlegen des „DataContext“](images/displaying-data-in-the-designer-02.png)

<span data-ttu-id="2f15c-129">Das resultierende Markup sieht folgendermaßen aus.</span><span class="sxs-lookup"><span data-stu-id="2f15c-129">Here's what the resulting markup looks like.</span></span>

``` xaml
<Page ... >
    <Page.DataContext>
        <local:BookstoreViewModel/>
    </Page.DataContext>
```

<span data-ttu-id="2f15c-130">Und so sieht die Benutzeroberfläche aus, wenn die Bindungen aufgelöst werden können.</span><span class="sxs-lookup"><span data-stu-id="2f15c-130">And here’s what the design surface looks like now that your bindings can resolve.</span></span> <span data-ttu-id="2f15c-131">Beachten Sie, dass das Auswahlfeld **Pfad** im Dialogfeld **Datenbindung erstellen** jetzt aufgefüllt ist, basierend auf dem **DataContext**-Typ und den Eigenschaften, an die gebunden werden kann.</span><span class="sxs-lookup"><span data-stu-id="2f15c-131">Notice that the **Path** picker in the **Create Data Binding** dialog is now populated, based on the **DataContext** type and the properties that you can bind to.</span></span>

![Designfähige Benutzeroberfläche](images/displaying-data-in-the-designer-03.png)

<span data-ttu-id="2f15c-133">Im Dialogfeld **Datenbindung erstellen** ist nur ein Typ als Grundlage erforderlich, die Bindungen erfordern jedoch, dass die Eigenschaften mit Werten initialisiert werden.</span><span class="sxs-lookup"><span data-stu-id="2f15c-133">The **Create Data Binding** dialog only needs a type to work from, but the bindings need the properties to be initialized with values.</span></span> <span data-ttu-id="2f15c-134">Wenn Sie zur Entwurfszeit nicht den Clouddienst in Anspruch nehmen möchten (aus Gründen der Leistung, der Kosten der Datenübertragung, des Datenschutzes usw.), kann der Initialisierungscode überprüfen, ob die App in einem Entwicklungstool (z.B. Visual Studio oder Blend für Visual Studio) ausgeführt wird. Wenn dies der Fall ist, laden Sie Beispieldaten, die nur zur Entwurfszeit verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="2f15c-134">If you don't want to reach out to your cloud service at design-time (due to performance, paying for data transfer, privacy issues, that kind of thing) then your initialization code can check to see whether your app is running in a design tool (such as Visual Studio or Blend for Visual Studio) and in that case load sample data for use at design-time only.</span></span>

``` csharp
if (Windows.ApplicationModel.DesignMode.DesignModeEnabled)
{
    // Load design-time books.
}
else
{
    // Load books from a cloud service.
}
```

<span data-ttu-id="2f15c-135">Sie können einen Ansichtsmodelllocator verwenden, wenn Sie Parameter an den Initialisierungscode übergeben müssen.</span><span class="sxs-lookup"><span data-stu-id="2f15c-135">You could use a view model locator if you need to pass parameters to your initialization code.</span></span> <span data-ttu-id="2f15c-136">Ein Ansichtsmodelllocator ist eine Klasse, die Sie in App-Ressourcen einfügen können.</span><span class="sxs-lookup"><span data-stu-id="2f15c-136">A view model locator is a class that you can put into app resources.</span></span> <span data-ttu-id="2f15c-137">Er verfügt über eine Eigenschaft, die das Ansichtsmodell verfügbar macht, und der **DataContext** der Seite wird an diese Eigenschaft gebunden.</span><span class="sxs-lookup"><span data-stu-id="2f15c-137">It has a property that exposes the view model, and your page's **DataContext** binds to that property.</span></span> <span data-ttu-id="2f15c-138">Ein weiteres Muster, das der Locator oder das Ansichtsmodell verwenden können, ist das Einfügen von Abhängigkeiten. Damit kann ein Entwurfszeit- bzw. Laufzeitdatenanbieter (der jeweils eine gemeinsame Schnittstelle implementiert) erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="2f15c-138">Another pattern that the locator or the view model can use is dependency injection, which can construct a design-time or a run-time data provider (each of which implements a common interface), as applicable.</span></span>

<a name="sample-data-from-class-and-design-time-attributes"></a><span data-ttu-id="2f15c-139">„Beispieldaten aus Klasse erstellen“ und Entwurfszeitattribute</span><span class="sxs-lookup"><span data-stu-id="2f15c-139">"Sample data from class", and design-time attributes</span></span>
---------------------------------------------------------------------------------------

<span data-ttu-id="2f15c-140">Wenn aus irgendeinem Grund keine der Optionen im vorherigen Abschnitt für Sie geeignet ist, stehen Ihnen immer noch über die Features der XAML-Tools und die Entwurfszeitattribute viele Optionen für Entwurfszeitdaten zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="2f15c-140">If for whatever reason none of the options in the previous section work for you then you still have plenty of design-time data options available via XAML tools features and design-time attributes.</span></span> <span data-ttu-id="2f15c-141">Eine gute Möglichkeit ist das Feature **Beispieldaten aus Klasse erstellen** in Blend für Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2f15c-141">One good option is the **Create Sample Data from Class** feature in Blend for Visual Studio.</span></span> <span data-ttu-id="2f15c-142">Sie finden diesen Befehl auf einer der Schaltflächen am oberen Rand des Bereichs **Daten**.</span><span class="sxs-lookup"><span data-stu-id="2f15c-142">You can find that command on one of the buttons at the top of the **Data** panel.</span></span>

<span data-ttu-id="2f15c-143">Sie müssen lediglich eine Klasse für den zu verwendenden Befehl angeben.</span><span class="sxs-lookup"><span data-stu-id="2f15c-143">All you need to do is to specify a class for the command to use.</span></span> <span data-ttu-id="2f15c-144">Der Befehl führt dann zwei wichtige Dinge für Sie aus.</span><span class="sxs-lookup"><span data-stu-id="2f15c-144">The command then does two important things for you.</span></span> <span data-ttu-id="2f15c-145">Erstens – er generiert eine XAML-Datei, die geeignete Beispieldaten zur rekursiven Hydration einer Instanz der ausgewählten Klasse und aller ihrer Member enthält (das Tool eignet sich für XAML-Dateien und JSON-Dateien gleichermaßen).</span><span class="sxs-lookup"><span data-stu-id="2f15c-145">First, it generates a XAML file that contains sample data suitable for hydrating an instance of your chosen class and all of its members, recursively (in fact, the tooling works equally well with XAML or JSON files).</span></span> <span data-ttu-id="2f15c-146">Zweitens füllt er den Bereich **Daten** mit dem Schema der ausgewählten Klasse auf.</span><span class="sxs-lookup"><span data-stu-id="2f15c-146">Second, it populates the **Data** panel with the schema of your chosen class.</span></span> <span data-ttu-id="2f15c-147">Sie können dann Mitglieder aus dem Bereich **Daten** auf die Entwurfsoberfläche ziehen, um verschiedene Aufgaben auszuführen.</span><span class="sxs-lookup"><span data-stu-id="2f15c-147">You can then drag members from the **Data** panel onto the design surface to perform various tasks.</span></span> <span data-ttu-id="2f15c-148">Je nachdem, was Sie ziehen und wo Sie es ablegen, können Sie vorhandenen Steuerelementen Bindungen hinzufügen (mit **{Binding}**) oder neue Steuerelemente erstellen und gleichzeitig binden.</span><span class="sxs-lookup"><span data-stu-id="2f15c-148">Depending on what you drag and where you drop it, you can add bindings to existing controls (using **{Binding}**), or create new controls and bind them at the same time.</span></span> <span data-ttu-id="2f15c-149">In beiden Fällen wird außerdem automatisch im Layoutstamm der Seite ein Entwurfszeit-Datenkontext (**d:DataContext**) für Sie festgelegt (wenn dieser nicht bereits festgelegt ist).</span><span class="sxs-lookup"><span data-stu-id="2f15c-149">In either case, the operation also sets a design-time data context (**d:DataContext**) for you (if one is not already set) on the layout root of your page.</span></span> <span data-ttu-id="2f15c-150">Der Entwurfszeit-Datenkontext verwendet das **d:DesignData**-Attribut zum Abrufen der Beispieldaten aus der generierten XAML-Datei (die Sie übrigens im Projekt suchen und bearbeiten können, damit sie die gewünschten Beispieldaten enthält).</span><span class="sxs-lookup"><span data-stu-id="2f15c-150">That design-time data context uses the **d:DesignData** attribute to get its sample data from the XAML file that was generated (which, by the way, you are free to find in your project and edit so that it contains the sample data you want).</span></span>

``` xaml
<Page ...
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d">
    <Grid ... d:DataContext="{d:DesignData /SampleData/RecordingViewModelSampleData.xaml}"/>
        <ListView ItemsSource="{Binding Recordings}" ... />
        ...
    </Grid>
</Page>
```

<span data-ttu-id="2f15c-151">Die verschiedenen xmlns-Deklarationen bedeuten, dass Attribute mit dem **d:**-Präfix nur zur Entwurfszeit interpretiert und während der Laufzeit ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="2f15c-151">The various xmlns declarations mean that attributes with the **d:** prefix are interpreted only at design-time and are ignored at run-time.</span></span> <span data-ttu-id="2f15c-152">Somit wirkt sich das **d:DataContext**-Attribut nur zur Entwurfszeit auf den Wert der Eigenschaft [**DataContext**](https://msdn.microsoft.com/library/windows/apps/BR208713) aus und hat zur Laufzeit keine Auswirkungen.</span><span class="sxs-lookup"><span data-stu-id="2f15c-152">So the **d:DataContext** attribute only affects the value of the [**DataContext**](https://msdn.microsoft.com/library/windows/apps/BR208713) property at design-time; it has no effect at run-time.</span></span> <span data-ttu-id="2f15c-153">Sie können im Markup sogar sowohl **d:DataContext** als auch **DataContext** festlegen, wenn Sie dies wünschen.</span><span class="sxs-lookup"><span data-stu-id="2f15c-153">You can even set both **d:DataContext** and **DataContext** in markup if you like.</span></span> <span data-ttu-id="2f15c-154">**d:DataContext** überschreibt zur Entwurfszeit, und **DataContext** überschreibt zur Laufzeit.</span><span class="sxs-lookup"><span data-stu-id="2f15c-154">**d:DataContext** will override at design-time, and **DataContext** will override at run-time.</span></span> <span data-ttu-id="2f15c-155">Diese Überschreibungsregeln werden auf alle Entwurfszeit- und Laufzeitattribute angewendet.</span><span class="sxs-lookup"><span data-stu-id="2f15c-155">These same override rules apply to all design-time and run-time attributes.</span></span>

<span data-ttu-id="2f15c-156">Das **d:DataContext**-Attribut und alle anderen Entwurfszeitattribute sind im Thema [Designzeitattribute](http://go.microsoft.com/fwlink/p/?LinkId=272504) dokumentiert, das für Universelle Windows-Plattform (UWP)-Apps) weiterhin Gültigkeit hat.</span><span class="sxs-lookup"><span data-stu-id="2f15c-156">The **d:DataContext** attribute, and all other design-time attributes, are documented in the [Design-Time Attributes](http://go.microsoft.com/fwlink/p/?LinkId=272504) topic, which is still valid for Universal Windows Platform (UWP) apps.</span></span>

<span data-ttu-id="2f15c-157">[**CollectionViewSource**](https://msdn.microsoft.com/library/windows/apps/BR209833) besitzt nicht die Eigenschaft **DataContext**, jedoch die Eigenschaft **Source**.</span><span class="sxs-lookup"><span data-stu-id="2f15c-157">[**CollectionViewSource**](https://msdn.microsoft.com/library/windows/apps/BR209833) doesn't have a **DataContext** property, but it does have a **Source** property.</span></span> <span data-ttu-id="2f15c-158">Daher gibt es eine Eigenschaft **d:Source**, mit der Sie auf die Entwurfszeit beschränkte Beispieldaten in einer **CollectionViewSource** festlegen können.</span><span class="sxs-lookup"><span data-stu-id="2f15c-158">Consequently, there's a **d:Source** property that you can use to set design-time-only sample data on a **CollectionViewSource**.</span></span>

``` xaml
    <Page.Resources>
        <CollectionViewSource x:Name="RecordingsCollection" Source="{Binding Recordings}"
            d:Source="{d:DesignData /SampleData/RecordingsSampleData.xaml}"/>
    </Page.Resources>

    ...

        <ListView ItemsSource="{Binding Source={StaticResource RecordingsCollection}}" ... />
    ...
```

<span data-ttu-id="2f15c-159">Damit dies funktioniert, verwenden Sie eine Klasse mit dem Namen `Recordings : ObservableCollection<Recording>` und bearbeiten die XAML-Beispieldatendatei, damit sie nur ein **Recordings**-Objekt enthält (in dem sich **Recording**-Objekte befinden), wie hier dargestellt.</span><span class="sxs-lookup"><span data-stu-id="2f15c-159">For this to work, you would have a class named `Recordings : ObservableCollection<Recording>`, and you would edit the sample data XAML file so that it contains only a **Recordings** object (with **Recording** objects inside that), as shown here.</span></span>

``` xml
<Quickstart:Recordings xmlns:Quickstart="using:Quickstart">
    <Quickstart:Recording ArtistName="Mollis massa" CompositionName="Cubilia metus"
        OneLineSummary="Morbi adipiscing sed" ReleaseDateTime="01/01/1800 15:53:17"/>
    <Quickstart:Recording ArtistName="Vulputate nunc" CompositionName="Parturient vestibulum"
        OneLineSummary="Dapibus praesent netus amet vestibulum" ReleaseDateTime="01/01/1800 15:53:17"/>
    <Quickstart:Recording ArtistName="Phasellus accumsan" CompositionName="Sit bibendum"
        OneLineSummary="Vestibulum egestas montes dictumst" ReleaseDateTime="01/01/1800 15:53:17"/>
</Quickstart:Recordings>
```

<span data-ttu-id="2f15c-160">Wenn Sie eine JSON-Beispieldatendatei anstelle einer XAML-Beispieldatendatei verwenden, müssen Sie die **Type**-Eigenschaft festlegen.</span><span class="sxs-lookup"><span data-stu-id="2f15c-160">If you use a JSON sample data file instead of XAML, you must set the **Type** property.</span></span>

``` xaml
    d:Source="{d:DesignData /SampleData/RecordingsSampleData.json, Type=local:Recordings}"
```

<span data-ttu-id="2f15c-161">Bisher haben wir zum Laden von Entwurfszeit-Beispieldaten aus einer XAML- oder JSON-Datei **d:DesignData** verwendet.</span><span class="sxs-lookup"><span data-stu-id="2f15c-161">So far, we've been using **d:DesignData** to load design-time sample data from a XAML or JSON file.</span></span> <span data-ttu-id="2f15c-162">Alternativ kann die Markuperweiterung **d:DesignInstance** verwendet werden. Diese gibt an, dass die Entwurfszeitquelle auf der von der **Type**-Eigenschaft angegebenen Klasse basiert.</span><span class="sxs-lookup"><span data-stu-id="2f15c-162">An alternative to that is the **d:DesignInstance** markup extension, which indicates that the design-time source is based on the class specified by the **Type** property.</span></span> <span data-ttu-id="2f15c-163">Hier sehen Sie ein Beispiel.</span><span class="sxs-lookup"><span data-stu-id="2f15c-163">Here's an example.</span></span>

``` xaml
    <CollectionViewSource x:Name="RecordingsCollection" Source="{Binding Recordings}"
        d:Source="{d:DesignInstance Type=local:Recordings, IsDesignTimeCreatable=True}"/>
```

<span data-ttu-id="2f15c-164">Die **IsDesignTimeCreatable**-Eigenschaft gibt an, dass das Entwicklungstool eigentlich eine Instanz der Klasse erstellen soll. Dies bedeutet, dass die Klasse über einen öffentlichen Standardkonstruktor verfügt und sich selbst mit Daten (echte oder Beispieldaten) auffüllt.</span><span class="sxs-lookup"><span data-stu-id="2f15c-164">The **IsDesignTimeCreatable** property indicates that the design tool should actually create an instance of the class, which implies that the class has a public default constructor, and that it populates itself with data (either real or sample).</span></span> <span data-ttu-id="2f15c-165">Wenn Sie **IsDesignTimeCreatable** nicht festlegen (oder wenn Sie es auf **False** festlegen), werden auf der Entwurfsoberfläche keine Beispieldaten angezeigt.</span><span class="sxs-lookup"><span data-stu-id="2f15c-165">If you don't set **IsDesignTimeCreatable** (or if you set it to **False**) then you won't get sample data displayed on the design surface.</span></span> <span data-ttu-id="2f15c-166">In diesem Fall das Entwicklungstool lediglich analysieren die Klasse für ihre bindbaren Eigenschaften und zeigt diese im Bereich **Daten** und im Dialogfeld " **Datenbindung erstellen** ".</span><span class="sxs-lookup"><span data-stu-id="2f15c-166">All the design tool does in that case is to parse the class for its bindable properties and display these in the **Data** panel and in the **Create Data Binding** dialog.</span></span>

<a name="sample-data-for-prototyping"></a><span data-ttu-id="2f15c-167">Beispieldaten für die Prototyperstellung</span><span class="sxs-lookup"><span data-stu-id="2f15c-167">Sample data for prototyping</span></span>
--------------------------------------------------------

<span data-ttu-id="2f15c-168">Für die Prototyperstellung benötigen Sie Beispieldaten zur Entwurfszeit und zur Laufzeit.</span><span class="sxs-lookup"><span data-stu-id="2f15c-168">For prototyping, you want sample data at both design-time and at run-time.</span></span> <span data-ttu-id="2f15c-169">Für diesen Anwendungsfall verfügt Blend für Visual Studio über das Feature **Neue Beispieldaten**.</span><span class="sxs-lookup"><span data-stu-id="2f15c-169">For that use case, Blend for Visual Studio has the **New Sample Data** feature.</span></span> <span data-ttu-id="2f15c-170">Sie finden diesen Befehl auf einer der Schaltflächen am oberen Rand des Bereichs **Daten**.</span><span class="sxs-lookup"><span data-stu-id="2f15c-170">You can find that command on one of the buttons at the top of the **Data** panel.</span></span>

<span data-ttu-id="2f15c-171">Statt eine Klasse anzugeben, können Sie direkt im Bereich **Daten** das Schema der Beispieldatenquelle entwerfen.</span><span class="sxs-lookup"><span data-stu-id="2f15c-171">Instead of specifying a class, you can actually design the schema of your sample data source right in the **Data** panel.</span></span> <span data-ttu-id="2f15c-172">Sie können im Bereich **Daten** auch Beispieldatenwerte bearbeiten. Es ist nicht erforderlich, eine Datei zu öffnen und zu bearbeiten (obwohl Sie bei Bedarf die Möglichkeit dazu haben).</span><span class="sxs-lookup"><span data-stu-id="2f15c-172">You can also edit sample data values in the **Data** panel: there's no need to open and edit a file (although, you can still do that if you prefer).</span></span>

<span data-ttu-id="2f15c-173">Das Feature **Neue Beispieldaten** verwendet [**DataContext**](https://msdn.microsoft.com/library/windows/apps/BR208713) und nicht **d:DataContext**. Daher sind die Beispieldaten sowohl beim Ausführen als auch beim Entwerfen der Skizze oder des Prototyps verfügbar.</span><span class="sxs-lookup"><span data-stu-id="2f15c-173">The **New Sample Data** feature uses [**DataContext**](https://msdn.microsoft.com/library/windows/apps/BR208713), and not **d:DataContext**, so that the sample data is available when you run your sketch or prototype as well as while you're designing it.</span></span> <span data-ttu-id="2f15c-174">Und der Bereich **Daten** beschleunigt Ihre Entwurfs- und Bindungsaufgaben.</span><span class="sxs-lookup"><span data-stu-id="2f15c-174">And the **Data** panel really speeds up your designing and binding tasks.</span></span> <span data-ttu-id="2f15c-175">Beispielsweise werden durch Ziehen einer Sammlungseigenschaft aus dem Bereich **Daten** auf die Entwurfsoberfläche ein datengebundenes Elementsteuerelement und die erforderlichen Vorlagen generiert, die sofort erstellt und ausgeführt werden können.</span><span class="sxs-lookup"><span data-stu-id="2f15c-175">For example, simply dragging a collection property from the **Data** panel onto the design surface generates a data-bound items control and the necessary templates, all ready to build and run.</span></span>

![Beispieldaten für die Prototyperstellung](images/displaying-data-in-the-designer-04.png)
