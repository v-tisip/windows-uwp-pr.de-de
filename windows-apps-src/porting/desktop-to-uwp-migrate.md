---
author: normesta
Description: Share code between a desktop application and a UWP app
Search.Product: eADQiWindows 10XVcnh
title: Teilen von Code zwischen einer desktop-Anwendung und eine UWP-app
ms.author: normesta
ms.date: 10/03/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 4a4eda15a18a441da2e06db17aaf7bea3d1842d1
ms.sourcegitcommit: 144f5f127fc4fbd852f2f6780ef26054192d68fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5976897"
---
# <a name="share-code-between-a-desktop-application-and-a-uwp-app"></a><span data-ttu-id="7317a-103">Teilen von Code zwischen einer desktop-Anwendung und eine UWP-app</span><span class="sxs-lookup"><span data-stu-id="7317a-103">Share code between a desktop application and a UWP app</span></span>

<span data-ttu-id="7317a-104">Sie können den Code in .NET Standardbibliotheken übertragen und so eine universelle Windows-Plattform (UWP)-App erstellen, um alle Windows10-Geräten zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="7317a-104">You can move your code into .NET Standard libraries, and then create a Universal Windows Platform (UWP) app to reach all Windows 10 devices.</span></span> <span data-ttu-id="7317a-105">Obwohl kein Tool existiert, das eine Desktopanwendung in eine UWP-App konvertieren kann, können Sie einen Großteil Ihres vorhandenen Codes wiederverwenden und so die Kosten der Programmierung verringern.</span><span class="sxs-lookup"><span data-stu-id="7317a-105">While there's no tool that can convert a desktop application to a UWP app, you can reuse a lot of your existing code and that lowers the cost of building one.</span></span> <span data-ttu-id="7317a-106">Die entsprechende Vorgehensweise wird in dieser Anleitung beschrieben.</span><span class="sxs-lookup"><span data-stu-id="7317a-106">This guide shows you how to do that.</span></span>

## <a name="share-code-in-a-net-standard-20-library"></a><span data-ttu-id="7317a-107">Teilen von Code in Bibliotheken für .NET Standard 2.0</span><span class="sxs-lookup"><span data-stu-id="7317a-107">Share code in a .NET Standard 2.0 library</span></span>

<span data-ttu-id="7317a-108">Platzieren Sie so viel Code wie möglich in die standardmäßigen Klassenbibliotheken für .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="7317a-108">Place as much code as you can into .NET Standard 2.0 class libraries.</span></span>  <span data-ttu-id="7317a-109">Solange Ihr Code-APIs verwendet, die standardmäßig definiert sind, können Sie diesen in einer UWP-App wiederverwenden.</span><span class="sxs-lookup"><span data-stu-id="7317a-109">As long as your code uses APIs that are defined in the standard, you can reuse it in a UWP app.</span></span> <span data-ttu-id="7317a-110">Es ist einfacher denn je, Code in den Bibliotheken für .NET Standard zu teilen, da viele andere APIs in .NET Standard 2.0 enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="7317a-110">It's easier than it's ever been to share code in a .NET Standard library because so many more APIs are included in the .NET Standard 2.0.</span></span>

<span data-ttu-id="7317a-111">In diesem großartigen Video finden Sie weitere Informationen.</span><span class="sxs-lookup"><span data-stu-id="7317a-111">Here's a great video that tells you more about it.</span></span>
<span data-ttu-id="7317a-112">&nbsp;</span><span class="sxs-lookup"><span data-stu-id="7317a-112">&nbsp;</span></span>
> [!VIDEO https://www.youtube.com/embed/YI4MurjfMn8]

### <a name="add-net-standard-libraries"></a><span data-ttu-id="7317a-113">Hinzufügen von Bibliotheken für .NET Standard</span><span class="sxs-lookup"><span data-stu-id="7317a-113">Add .NET Standard libraries</span></span>

<span data-ttu-id="7317a-114">Fügen Sie der Lösung zunächst eine oder mehrere Klassenbibliotheken für .NET Standard 2.0 hinzu.</span><span class="sxs-lookup"><span data-stu-id="7317a-114">First, add one or more .NET Standard class libraries to your solution.</span></span>  

![Hinzufügen eines Dotnet-Standardprojekts](images/desktop-to-uwp/dot-net-standard-project-template.png)

<span data-ttu-id="7317a-116">Die Anzahl der Bibliotheken, die Sie der Lösung hinzufügen, hängt davon ab, wie Sie Ihren Code organisieren möchten.</span><span class="sxs-lookup"><span data-stu-id="7317a-116">The number of libraries that you add to your solution depends on how you plan to organize your code.</span></span>

<span data-ttu-id="7317a-117">Stellen Sie sicher, dass jede Klassenbibliothek auf **.NET Standard 2.0** abzielt.</span><span class="sxs-lookup"><span data-stu-id="7317a-117">Make sure that each class library targets the **.NET Standard 2.0**.</span></span>

![Festlegen von .NET Standard 2.0 als Ziel](images/desktop-to-uwp/target-standard-20.png)

<span data-ttu-id="7317a-119">Sie finden diese Einstellung auf den Eigenschaftenseiten des Klassenbibliotheksprojekts.</span><span class="sxs-lookup"><span data-stu-id="7317a-119">You can find this setting in the property pages of the class library project.</span></span>

<span data-ttu-id="7317a-120">Fügen Sie dem Desktopanwendungsprojekt einfach einen Verweis auf das Klassenbibliotheksprojekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="7317a-120">From your desktop application project, add a reference to the class library project.</span></span>

![Verweis auf die Klassenbibliothek](images/desktop-to-uwp/class-library-reference.png)

<span data-ttu-id="7317a-122">Sie können anschließend mit den Tools bestimmen, welcher Teil des Codes dem Standard entspricht.</span><span class="sxs-lookup"><span data-stu-id="7317a-122">Next, use tools to determine how much of your code conforms to the standard.</span></span> <span data-ttu-id="7317a-123">Auf diese Weise können Sie vor dem Verschieben des Code in die Bibliothek entscheiden, welche Teile Sie wiederverwenden können, welche Teile minimal geändert werden müssen und welche Teile anwendungsspezifisch bleiben.</span><span class="sxs-lookup"><span data-stu-id="7317a-123">That way, before you move code into the library, you can decide which parts you can reuse, which parts require minimal modification, and which parts will remain application-specific.</span></span>

### <a name="check-library-and-code-compatibility"></a><span data-ttu-id="7317a-124">Überprüfen der Kompatibilität für die Bibliothek und den Code</span><span class="sxs-lookup"><span data-stu-id="7317a-124">Check library and code compatibility</span></span>

<span data-ttu-id="7317a-125">Wir beginnen mit NuGet-Paketen und anderen DLL-Dateien, die Sie von einem Drittanbieter erhalten haben.</span><span class="sxs-lookup"><span data-stu-id="7317a-125">We'll start with Nuget Packages and other dll files that you obtained from a third party.</span></span>

<span data-ttu-id="7317a-126">Wenn Ihre Anwendung diese verwendet, bestimmen Sie, ob sie mit .NET Standard 2.0 kompatibel sind.</span><span class="sxs-lookup"><span data-stu-id="7317a-126">If your application uses any of them, determine if they are compatible with the .NET Standard 2.0.</span></span> <span data-ttu-id="7317a-127">Sie können dazu eine Visual Studio-Erweiterung oder ein Befehlszeilendienstprogramm verwenden.</span><span class="sxs-lookup"><span data-stu-id="7317a-127">You can use a Visual Studio extension or a command-line utility to do that.</span></span>

<span data-ttu-id="7317a-128">Verwenden Sie die gleichen Tools, um Ihren Code zu analysieren.</span><span class="sxs-lookup"><span data-stu-id="7317a-128">Use these same tools to analyze your code.</span></span> <span data-ttu-id="7317a-129">Laden Sie die Tools hier herunter ([dotnet-apiport](https://github.com/Microsoft/dotnet-apiport/releases)). Schauen Sie sich dieses Video an, um zu erfahren, wie Sie diese verwenden können.</span><span class="sxs-lookup"><span data-stu-id="7317a-129">Download the tools here ([dotnet-apiport](https://github.com/Microsoft/dotnet-apiport/releases)) and then watch this video to learn how to use them.</span></span>
<span data-ttu-id="7317a-130">&nbsp;</span><span class="sxs-lookup"><span data-stu-id="7317a-130">&nbsp;</span></span>
> [!VIDEO https://www.youtube.com/embed/rzs_FGPyAlY]

<span data-ttu-id="7317a-131">Wenn Ihr Code nicht mit dem Standard kompatibel ist, ziehen Sie weitere Möglichkeiten in Betracht, um diesen Code zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="7317a-131">If your code isn't compatible with the standard, consider other ways that you could implement that code.</span></span> <span data-ttu-id="7317a-132">Öffnen Sie dazu den [.NET API-Browser](https://docs.microsoft.com/dotnet/api/?view=netstandard-2.0).</span><span class="sxs-lookup"><span data-stu-id="7317a-132">Start by opening the [.NET API Browser](https://docs.microsoft.com/dotnet/api/?view=netstandard-2.0).</span></span> <span data-ttu-id="7317a-133">Sie können diesen Browsers verwenden, um die APIs zu überprüfen, die in .NET Standard 2.0 verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="7317a-133">You can use that browser to review the API's that are available in the .NET Standard 2.0.</span></span> <span data-ttu-id="7317a-134">Beschränken Sie die Liste unbedingt auf den .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="7317a-134">Make sure to scope the list to the .NET Standard 2.0.</span></span>

![Dot-Net-Option](images/desktop-to-uwp/dot-net-option.png)

<span data-ttu-id="7317a-136">Ein Teil Ihres Codes ist plattformspezifisch und muss in Ihrem Desktopanwendungsprojekt verbleiben.</span><span class="sxs-lookup"><span data-stu-id="7317a-136">Some of your code will be platform-specific and will need to remain in your desktop application project.</span></span>

### <a name="example-migrating-data-access-code-to-a-net-standard-20-library"></a><span data-ttu-id="7317a-137">Beispiel: Migrieren von Datenzugriffscode auf eine Bibliothek für .NET Standard 2.0</span><span class="sxs-lookup"><span data-stu-id="7317a-137">Example: Migrating data access code to a .NET Standard 2.0 library</span></span>

<span data-ttu-id="7317a-138">Angenommen, Sie haben wir eine sehr einfache Windows Forms-Anwendung, die Kunden aus unserer Northwind-Beispieldatenbank anzeigt.</span><span class="sxs-lookup"><span data-stu-id="7317a-138">Let's assume that we have a very basic Windows Forms application that shows customers from our Northwind sample database.</span></span>

![Windows Forms-App](images/desktop-to-uwp/win-forms-app.png)

<span data-ttu-id="7317a-140">Das Projekt enthält eine Klassenbibliothek für .NET Standard 2.0 mit einer statischen Klasse namens **Northwind**.</span><span class="sxs-lookup"><span data-stu-id="7317a-140">The project contains a .NET Standard 2.0 class library with a static class named **Northwind**.</span></span> <span data-ttu-id="7317a-141">Wenn wir diesen Code in die **Northwind**-Klasse verschieben, wird er nicht kompiliert, da er die Klassen ``SQLConnection``, ``SqlCommand`` und ``SqlDataReader`` verwendet und diese Klassen in .NET Standard 2.0 nicht verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="7317a-141">If we move this code into the **Northwind** class, it won't compile because it uses the ``SQLConnection``, ``SqlCommand``, and ``SqlDataReader`` classes, and those classes that are not available in the .NET Standard 2.0.</span></span>

```csharp
public static ArrayList GetCustomerNames()
{
    ArrayList customers = new ArrayList();

    using (SqlConnection conn = new SqlConnection())
    {
        conn.ConnectionString =
            @"Data Source=" +
            @"<Your Server Name>\SQLEXPRESS;Initial Catalog=NORTHWIND;Integrated Security=SSPI";

        conn.Open();

        SqlCommand command = new SqlCommand("select ContactName from customers order by ContactName asc", conn);

        using (SqlDataReader reader = command.ExecuteReader())
        {
            while (reader.Read())
            {
                customers.Add(reader[0]);
            }
        }
    }

    return customers;
}

```
<span data-ttu-id="7317a-142">Wir können jedoch den [.NET API-Browser](https://docs.microsoft.com/dotnet/api/?view=netstandard-2.0) verwenden, um eine Alternative zu finden.</span><span class="sxs-lookup"><span data-stu-id="7317a-142">We can use the [.NET API Browser](https://docs.microsoft.com/dotnet/api/?view=netstandard-2.0) to find an alternative though.</span></span> <span data-ttu-id="7317a-143">Die Klassen ``DbConnection``, ``DbCommand``, und ``DbDataReader`` sind alle in .NET Standard 2.0 verfügbar, sodass wir diese stattdessen verwenden können.</span><span class="sxs-lookup"><span data-stu-id="7317a-143">The ``DbConnection``, ``DbCommand``, and ``DbDataReader`` classes are all available in the .NET Standard 2.0 so we can use them instead.</span></span>  

<span data-ttu-id="7317a-144">Die überarbeitete Version verwendet diese Klassen, um eine Liste der Kunden zu erhalten. Zum Erstellen einer ``DbConnection``-Klasse müssen wir allerdings ein Factoryobjekt übergeben, das wir in der Clientanwendung erstellen.</span><span class="sxs-lookup"><span data-stu-id="7317a-144">This revised version uses those classes to get a list of customers, but to create a ``DbConnection`` class, we'll need to pass in a factory object that we create in the client application.</span></span>

```csharp
public static ArrayList GetCustomerNames(DbProviderFactory factory)
{
    ArrayList customers = new ArrayList();

    using (DbConnection conn = factory.CreateConnection())
    {
        conn.ConnectionString = @"Data Source=" +
                        @"<Your Server Name>\SQLEXPRESS;Initial Catalog=NORTHWIND;Integrated Security=SSPI";

        conn.Open();

        DbCommand command = factory.CreateCommand();
        command.Connection = conn;
        command.CommandText = "select ContactName from customers order by ContactName asc";

        using (DbDataReader reader = command.ExecuteReader())
        {
            while (reader.Read())
            {
                customers.Add(reader[0]);
            }
        }
    }

    return customers;
}
```  

<span data-ttu-id="7317a-145">In der CodeBehind-Seite von Windows Form können wir einfach eine Factoryinstanz erstellen und Sie diese an unsere Methode übergeben.</span><span class="sxs-lookup"><span data-stu-id="7317a-145">In the code-behind page of the Windows Form, we can just create factory instance and pass it into our method.</span></span>

```csharp
public partial class Customers : Form
{
    public Customers()
    {
        InitializeComponent();

        dataGridView1.Rows.Clear();

        SqlClientFactory factory = SqlClientFactory.Instance;

        foreach (string customer in Northwind.GetCustomerNames(factory))
        {
            dataGridView1.Rows.Add(customer);
        }
    }
}
```

## <a name="reach-all-windows-devices"></a><span data-ttu-id="7317a-146">Erreichen aller Windows-Geräte</span><span class="sxs-lookup"><span data-stu-id="7317a-146">Reach all Windows devices</span></span>

<span data-ttu-id="7317a-147">Jetzt können Sie der Lösung eine UWP-App hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="7317a-147">Now you're ready to add a UWP app to your solution.</span></span>

![Abbildung der Desktop-zu-UWP-Brücke](images/desktop-to-uwp/adaptive-ui.png)

<span data-ttu-id="7317a-149">Sie müssen allerdings noch die Seiten der Benutzeroberfläche in XAML erstellen und den für jedes Gerät oder jede Plattform spezifischen Code schreiben. Wenn Sie damit fertig sind, können Sie den gesamten Umfang der Windows10-Geräte erreichen und Ihre App-Seiten werden modern dargestellt und eignen sich so gut für unterschiedliche Bildschirmgrößen und -Auflösungen.</span><span class="sxs-lookup"><span data-stu-id="7317a-149">You'll still have to design UI pages in XAML and write any device or platform-specific code, but when you are done, you'll be able to reach the full breadth of Windows 10 devices and your app pages will have a modern feel that adapts well to different screen sizes and resolutions.</span></span>

<span data-ttu-id="7317a-150">Ihre App reagiert auf andere Eingabemechanismen als nur Tastatur und Maus, und die Funktionen und Einstellungen sind auf allen Geräten intuitiv.</span><span class="sxs-lookup"><span data-stu-id="7317a-150">Your app will respond to input mechanisms other than just a keyboard and mouse, and features and settings will be intuitive across devices.</span></span> <span data-ttu-id="7317a-151">Dies bedeutet, dass Benutzer lernen, Aufgaben nur einmal durchzuführen. Dies funktioniert in vertrauter Art und Weise und ist vom Gerät unabhängig.</span><span class="sxs-lookup"><span data-stu-id="7317a-151">This means that users learn how to do things one time, and then it works in a very familiar way no matter the device.</span></span>

<span data-ttu-id="7317a-152">Dies sind nur einige Beispiele für die interessanten Funktionen, die in der UWP enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="7317a-152">These are just a few of the goodies that come with UWP.</span></span> <span data-ttu-id="7317a-153">Weitere Informationen finden Sie unter [Erstellen Sie mit Windows herausragende Umgebungen](https://developer.microsoft.com/windows/why-build-for-uwp).</span><span class="sxs-lookup"><span data-stu-id="7317a-153">To learn more, see [Build great experiences with Windows](https://developer.microsoft.com/windows/why-build-for-uwp).</span></span>

### <a name="add-a-uwp-project"></a><span data-ttu-id="7317a-154">Hinzufügen eines UWP-Projekts</span><span class="sxs-lookup"><span data-stu-id="7317a-154">Add a UWP project</span></span>

<span data-ttu-id="7317a-155">Fügen Sie Ihrer Lösung zunächst ein UWP-Projekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="7317a-155">First, add a UWP project to your solution.</span></span>

![UWP-Projekt](images/desktop-to-uwp/new-uwp-app.png)

<span data-ttu-id="7317a-157">Fügen Sie dann vom UWP-Projekt einen Verweis auf das Projekt der Bibliothek für .NET Standard 2.0 hinzu.</span><span class="sxs-lookup"><span data-stu-id="7317a-157">Then, from your UWP project, add a reference the .NET Standard 2.0 library project.</span></span>

![Verweis auf die Klassenbibliothek](images/desktop-to-uwp/class-library-reference2.png)

### <a name="build-your-pages"></a><span data-ttu-id="7317a-159">Erstellen der Seiten</span><span class="sxs-lookup"><span data-stu-id="7317a-159">Build your pages</span></span>

<span data-ttu-id="7317a-160">Fügen Sie XAML-Seiten hinzu, und rufen Sie den Code in der Bibliothek für .NET Standard 2.0 auf.</span><span class="sxs-lookup"><span data-stu-id="7317a-160">Add XAML pages and call the code in your .NET Standard 2.0 library.</span></span>

![UWP-App](images/desktop-to-uwp/uwp-app.png)

```xml
<Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
    <StackPanel x:Name="customerStackPanel">
        <ListView x:Name="customerList"/>
    </StackPanel>
</Grid>
```

```csharp
public sealed partial class MainPage : Page
{
    public MainPage()
    {
        this.InitializeComponent();

        SqlClientFactory factory = SqlClientFactory.Instance;

        customerList.ItemsSource = Northwind.GetCustomerNames(factory);
    }
}
```


<span data-ttu-id="7317a-162">Erste Schritte mit UWP finden Sie unter [Was ist eine UWP-App](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide).</span><span class="sxs-lookup"><span data-stu-id="7317a-162">To get started with UWP, see [What's a UWP app](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide).</span></span>

## <a name="reach-ios-and-android-devices"></a><span data-ttu-id="7317a-163">Erreichen von iOS- und Android-Geräten</span><span class="sxs-lookup"><span data-stu-id="7317a-163">Reach iOS and Android devices</span></span>

<span data-ttu-id="7317a-164">Durch das Hinzufügen von Xamarin-Projekten können Sie Android und iOS-Geräten erreichen.</span><span class="sxs-lookup"><span data-stu-id="7317a-164">You can reach Android and iOS devices by adding Xamarin projects.</span></span>  

![Xamarin-Apps](images/desktop-to-uwp/xamarin-apps.png)

<span data-ttu-id="7317a-166">Diese Projekte ermöglichen die Verwendung von C# zur Entwicklung von Android- und iOS-Apps mit Vollzugriff auf plattformspezifische und gerätespezifische APIs.</span><span class="sxs-lookup"><span data-stu-id="7317a-166">These projects let you use C# to build Android and iOS apps with full access to platform-specific and device-specific APIs.</span></span> <span data-ttu-id="7317a-167">Diese Apps nutzen die plattformspezifische Hardwarebeschleunigung und wurden für die native Leistung kompiliert.</span><span class="sxs-lookup"><span data-stu-id="7317a-167">These apps leverage platform-specific hardware acceleration, and are compiled for native performance.</span></span>

<span data-ttu-id="7317a-168">Sie haben Zugriff auf das gesamte Spektrum der Funktionen, die von der zugrunde liegenden Plattform und dem Gerät verfügbar gemacht wurden, einschließlich der Plattformfunktionen wie iBeacons und Android Fragments. Sie verwenden standardmäßig native Steuerelemente der Benutzeroberfläche, um Benutzeroberflächen zu erstellen, die dem gewünschten Erscheinungsbild der Benutzer entsprechen.</span><span class="sxs-lookup"><span data-stu-id="7317a-168">They have access to the full spectrum of functionality exposed by the underlying platform and device, including platform-specific capabilities like iBeacons and Android Fragments and you'll use standard native user interface controls to build UIs that look and feel the way that users expect them to.</span></span>

<span data-ttu-id="7317a-169">Genau wie bei UWPs sind die Kosten für das Hinzufügen einer Android- oder iOS-App niedriger, da Sie die Geschäftslogik in einer Klassenbibliothek für .NET Standard 2.0 wiederverwenden können.</span><span class="sxs-lookup"><span data-stu-id="7317a-169">Just like UWPs, the cost to add an Android or iOS app is lower because you can reuse business logic in a .NET Standard 2.0 class library.</span></span> <span data-ttu-id="7317a-170">Sie müssen allerdings noch die Seiten der Benutzeroberfläche in XAML erstellen und den für jedes Gerät oder jede Plattform spezifischen Code schreiben.</span><span class="sxs-lookup"><span data-stu-id="7317a-170">You'll have to design your UI pages in XAML and write any device or platform-specific code.</span></span>

### <a name="add-a-xamarin-project"></a><span data-ttu-id="7317a-171">Hinzufügen eines Xamarin-Projekts</span><span class="sxs-lookup"><span data-stu-id="7317a-171">Add a Xamarin project</span></span>

<span data-ttu-id="7317a-172">Fügen Sie zuerst der Lösung ein **Android**-, **iOS**- oder **plattformübergreifendes** hinzu.</span><span class="sxs-lookup"><span data-stu-id="7317a-172">First, add an **Android**, **iOS**, or **Cross-Platform** project to your solution.</span></span>

<span data-ttu-id="7317a-173">Sie finden diese Vorlagen im Dialogfeld **Neues Projekt hinzufügen** in der **Visual C#-**-Gruppe.</span><span class="sxs-lookup"><span data-stu-id="7317a-173">You can find these templates in the **Add New Project** dialog box under the **Visual C#** group.</span></span>

![Xamarin-Apps](images/desktop-to-uwp/xamarin-projects.png)

>[!NOTE]
><span data-ttu-id="7317a-175">Plattformübergreifende Projekte sind ideal für Apps mit wenigen plattformspezifischen Funktionen.</span><span class="sxs-lookup"><span data-stu-id="7317a-175">Cross-platform projects are great for apps with little platform-specific functionality.</span></span> <span data-ttu-id="7317a-176">Sie können diese zur Entwicklung einer nativen XAML-basierten Benutzeroberfläche verwenden, die unter iOS, Android und Windows ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="7317a-176">You can use them to build one native XAML-based UI that runs on iOS, Android, and Windows.</span></span> <span data-ttu-id="7317a-177">Weitere Informationen finden Sie [hier](https://www.xamarin.com/forms).</span><span class="sxs-lookup"><span data-stu-id="7317a-177">Learn more [here](https://www.xamarin.com/forms).</span></span>

<span data-ttu-id="7317a-178">Fügen Sie anschließen von Ihrem Android-, iOS- oder plattformübergreifenden Projekt einen Verweis auf das Klassenbibliotheksprojekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="7317a-178">Then, from your Android, iOS, or cross-platform project, add a reference the class library project.</span></span>

![Verweis auf die Klassenbibliothek](images/desktop-to-uwp/class-library-reference3.png)

### <a name="build-your-pages"></a><span data-ttu-id="7317a-180">Erstellen der Seiten</span><span class="sxs-lookup"><span data-stu-id="7317a-180">Build your pages</span></span>

<span data-ttu-id="7317a-181">Unser Beispiel zeigt eine Liste der Kunden in einer Android-App.</span><span class="sxs-lookup"><span data-stu-id="7317a-181">Our example shows a list of customers in an Android app.</span></span>

![Android-App](images/desktop-to-uwp/android-app.png)

```xml
<?xml version="1.0" encoding="utf-8"?>
<TextView xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="fill_parent"
    android:layout_height="fill_parent"
    android:padding="10dp" android:textSize="16sp"
    android:id="@android:id/list">
</TextView>
```

```csharp
[Activity(Label = "MyAndroidApp", MainLauncher = true)]
public class MainActivity : ListActivity
{
    protected override void OnCreate(Bundle savedInstanceState)
    {
        base.OnCreate(savedInstanceState);

        SqlClientFactory factory = SqlClientFactory.Instance;

        var customers = (string[])Northwind.GetCustomerNames(factory).ToArray(typeof(string));

        ListAdapter = new ArrayAdapter<string>(this, Resource.Layout.list_item, customers);
    }
}
```

<span data-ttu-id="7317a-183">Informationen zu den ersten Schritten mit Android-, iOS- und plattformübergreifenden Projekten finden Sie im [Xamarin-Entwicklerportal](https://developer.xamarin.com/).</span><span class="sxs-lookup"><span data-stu-id="7317a-183">To get started with Android, iOS, and cross-platform projects, see the [Xamarin developer portal](https://developer.xamarin.com/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="7317a-184">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="7317a-184">Next steps</span></span>

**<span data-ttu-id="7317a-185">Finden Sie Antworten auf Ihre Fragen</span><span class="sxs-lookup"><span data-stu-id="7317a-185">Find answers to your questions</span></span>**

<span data-ttu-id="7317a-186">Haben Sie Fragen?</span><span class="sxs-lookup"><span data-stu-id="7317a-186">Have questions?</span></span> <span data-ttu-id="7317a-187">Fragen Sie uns auf Stack Overflow.</span><span class="sxs-lookup"><span data-stu-id="7317a-187">Ask us on Stack Overflow.</span></span> <span data-ttu-id="7317a-188">Unser Team überwacht diese [Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span><span class="sxs-lookup"><span data-stu-id="7317a-188">Our team monitors these [tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span></span> <span data-ttu-id="7317a-189">Fragen Sie uns [hier](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).</span><span class="sxs-lookup"><span data-stu-id="7317a-189">You can also ask us [here](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).</span></span>

**<span data-ttu-id="7317a-190">Geben Sie Feedback oder Verbesserungsvorschläge</span><span class="sxs-lookup"><span data-stu-id="7317a-190">Give feedback or make feature suggestions</span></span>**

<span data-ttu-id="7317a-191">Weitere Informationen finden Sie unter [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).</span><span class="sxs-lookup"><span data-stu-id="7317a-191">See [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).</span></span>
