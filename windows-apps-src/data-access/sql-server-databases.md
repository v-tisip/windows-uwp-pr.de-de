---
author: normesta
title: Verwenden einer SQL Server-Datenbank in einer UWP-App
description: Verwenden Sie eine SQL Server-Datenbank in einer UWP-App.
ms.author: normesta
ms.date: 11/13/2017
ms.topic: article
keywords: windows 10, uwp, SQL Server, datenbank
ms.localizationpriority: medium
ms.openlocfilehash: 8396fb7685a774568b6cd63acb11f78133584f46
ms.sourcegitcommit: 3257416aebb5a7b1515e107866806f8bd57845a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2018
ms.locfileid: "7169573"
---
# <a name="use-a-sql-server-database-in-a-uwp-app"></a><span data-ttu-id="d12a1-104">Verwenden einer SQL Server-Datenbank in einer UWP-App</span><span class="sxs-lookup"><span data-stu-id="d12a1-104">Use a SQL Server database in a UWP app</span></span>
<span data-ttu-id="d12a1-105">Ihre App kann sich direkt mit einer SQL Server-Datenbank verbinden und dann Daten über Klassen im Namespace [System.Data.SqlClient](https://msdn.microsoft.com/library/system.data.sqlclient.aspx) speichern und abrufen.</span><span class="sxs-lookup"><span data-stu-id="d12a1-105">Your app can connect directly to a SQL Server database and then store and retrieve data by using classes in the [System.Data.SqlClient](https://msdn.microsoft.com/library/system.data.sqlclient.aspx) namespace.</span></span>

<span data-ttu-id="d12a1-106">In diesem Leitfaden zeigen wir Ihnen, wie Sie das tun können.</span><span class="sxs-lookup"><span data-stu-id="d12a1-106">In this guide, we'll show you one way to do that.</span></span> <span data-ttu-id="d12a1-107">Wenn Sie die [Northwind](https://docs.microsoft.com/dotnet/framework/data/adonet/sql/linq/downloading-sample-databases)-Beispieldatenbank auf Ihrer SQL Server-Instanz installieren und dann diese Snippets verwenden, erhalten Sie eine grundlegende Benutzeroberfläche, die Produkte aus der Northwind-Beispieldatenbank anzeigt.</span><span class="sxs-lookup"><span data-stu-id="d12a1-107">If you install the [Northwind](https://docs.microsoft.com/dotnet/framework/data/adonet/sql/linq/downloading-sample-databases) sample database onto your SQL Server instance, and then use these snippets, you'll end up with a basic UI that shows products from the Northwind sample database.</span></span>

![Northwind-Produkte](images/products-northwind.png)

<span data-ttu-id="d12a1-109">Die in diesem Leitfaden gezeigten Snippets basieren auf diesem [vollständigeren Beispiel](https://github.com/StefanWickDev/IgniteDemos/tree/master/NorthwindDemo).</span><span class="sxs-lookup"><span data-stu-id="d12a1-109">The snippets that appear in this guide are based on this more [complete sample](https://github.com/StefanWickDev/IgniteDemos/tree/master/NorthwindDemo).</span></span>

## <a name="first-set-up-your-solution"></a><span data-ttu-id="d12a1-110">Richten Sie zunächst Ihre Lösung ein</span><span class="sxs-lookup"><span data-stu-id="d12a1-110">First, set up your solution</span></span>

<span data-ttu-id="d12a1-111">Um Ihre App direkt mit einer SQL Server-Datenbank zu verbinden, stellen Sie sicher, dass die Mindestversion Ihres Projekts auf das Fall Creators Update zielt.</span><span class="sxs-lookup"><span data-stu-id="d12a1-111">To connect your app directly to a SQL Server database, make sure that the minimum version of your project targets the Fall Creators update.</span></span>  <span data-ttu-id="d12a1-112">Sie finden diese Informationen auf der Eigenschaftsseite Ihres UWP-Projekts.</span><span class="sxs-lookup"><span data-stu-id="d12a1-112">You can find that information in the properties page of your UWP project.</span></span>

![Mindestversion des Windows SDKs](images/min-version-fall-creators.png)

<span data-ttu-id="d12a1-114">Öffnen Sie die Datei **Package.appxmanifest** Ihres UWP-Projekts im Manifest-Designer.</span><span class="sxs-lookup"><span data-stu-id="d12a1-114">Open the **Package.appxmanifest** file of your UWP project in the manifest designer.</span></span>

<span data-ttu-id="d12a1-115">Aktivieren Sie auf der Registerkarte **Funktionen** das Kontrollkästchen **Unternehmensauthentifizierung**.</span><span class="sxs-lookup"><span data-stu-id="d12a1-115">In the **Capabilities** tab, select the **Enterprise Authentication** checkbox.</span></span>

![Funktion Unternehmensauthentifizierung](images/enterprise-authentication.png)

<a id="use-data" />

## <a name="add-and-retrieve-data-in-a-sql-server-database"></a><span data-ttu-id="d12a1-117">Hinzufügen und Abrufen von Daten in einer SQL Server-Datenbank</span><span class="sxs-lookup"><span data-stu-id="d12a1-117">Add and retrieve data in a SQL Server database</span></span>

<span data-ttu-id="d12a1-118">In diesem Abschnitt werden wir diese Dinge tun:</span><span class="sxs-lookup"><span data-stu-id="d12a1-118">In this section,  we'll do these things:</span></span>

<span data-ttu-id="d12a1-119">:one: Fügen Sie eine Verbindungszeichenfolge hinzu.</span><span class="sxs-lookup"><span data-stu-id="d12a1-119">:one: Add a connection string.</span></span>

<span data-ttu-id="d12a1-120">:two: Legen Sie eine Klasse für Produktdaten an.</span><span class="sxs-lookup"><span data-stu-id="d12a1-120">:two: Create a class to hold product data.</span></span>

<span data-ttu-id="d12a1-121">:three: Rufen Sie Produkte aus der SQL Server-Datenbank ab.</span><span class="sxs-lookup"><span data-stu-id="d12a1-121">:three: Retrieve products from the SQL Server database.</span></span>

<span data-ttu-id="d12a1-122">:four: Fügen Sie eine einfache Benutzeroberfläche hinzu.</span><span class="sxs-lookup"><span data-stu-id="d12a1-122">:four: Add a basic user interface.</span></span>

<span data-ttu-id="d12a1-123">:five: Füllen Sie das UI mit Produkten.</span><span class="sxs-lookup"><span data-stu-id="d12a1-123">:five: Populate the UI with Products.</span></span>

>[!NOTE]
> <span data-ttu-id="d12a1-124">Dieser Abschnitt zeigt eine Möglichkeit, Ihren Datenzugriffscode zu organisieren.</span><span class="sxs-lookup"><span data-stu-id="d12a1-124">This section illustrates one way to organize your data access code.</span></span> <span data-ttu-id="d12a1-125">Es ist nur als Beispiel gedacht, wie Sie [System.Data.SqlClient](https://msdn.microsoft.com/library/system.data.sqlclient.aspx) zum Speichern und Abrufen von Daten aus einer SQL Server-Datenbank verwenden können.</span><span class="sxs-lookup"><span data-stu-id="d12a1-125">It's meant only to provide an example of how you can use  [System.Data.SqlClient](https://msdn.microsoft.com/library/system.data.sqlclient.aspx) to store and retrieve data from a SQL Server database.</span></span> <span data-ttu-id="d12a1-126">Sie können Ihren Code auf jede Art und Weise organisieren, die für das Design Ihrer App am sinnvollsten ist.</span><span class="sxs-lookup"><span data-stu-id="d12a1-126">You can organize your code in any way that makes the most sense to your application's design.</span></span>

### <a name="add-a-connection-string"></a><span data-ttu-id="d12a1-127">Hinzufügen einer Verbindungszeichenfolge</span><span class="sxs-lookup"><span data-stu-id="d12a1-127">Add a connection string</span></span>

<span data-ttu-id="d12a1-128">Fügen Sie in der Datei **App.xaml.cs** eine Eigenschaft zur Klasse ``App`` hinzu, die anderen Klassen in Ihrer Lösung Zugriff auf die Verbindungszeichenfolge gibt.</span><span class="sxs-lookup"><span data-stu-id="d12a1-128">In the **App.xaml.cs** file, add a property to the ``App`` class, that gives other classes in your solution access to the connection string.</span></span>

<span data-ttu-id="d12a1-129">Unsere Verbindungszeichenfolge zeigt auf die Northwind-Datenbank in einer SQL Server Express-Instanz.</span><span class="sxs-lookup"><span data-stu-id="d12a1-129">Our connection string points to the Northwind database in a SQL Server Express instance.</span></span>

```csharp
sealed partial class App : Application
{
    private string connectionString =
        @"Data Source=YourServerName\SQLEXPRESS;Initial Catalog=NORTHWIND;Integrated Security=SSPI";

    public string ConnectionString { get => connectionString; set => connectionString = value; }

    ...
}
```

### <a name="create-a-class-to-hold-product-data"></a><span data-ttu-id="d12a1-130">Legen Sie eine Klasse für Produktdaten an</span><span class="sxs-lookup"><span data-stu-id="d12a1-130">Create a class to hold product data</span></span>

<span data-ttu-id="d12a1-131">Wir erstellen eine Klasse, die das Ereignis [INotifyPropertyChanged](https://msdn.microsoft.com/library/system.componentmodel.inotifypropertychanged.aspx) implementiert, so dass wir Attribute in unserer XAML-Benutzeroberfläche an die Eigenschaften in dieser Klasse binden können.</span><span class="sxs-lookup"><span data-stu-id="d12a1-131">We'll create a class that implements the [INotifyPropertyChanged](https://msdn.microsoft.com/library/system.componentmodel.inotifypropertychanged.aspx) event so that we can bind attributes in our XAML UI to the properties in this class.</span></span>

```csharp
public class Product : INotifyPropertyChanged
{
    public int ProductID { get; set; }
    public string ProductCode { get { return ProductID.ToString(); } }
    public string ProductName { get; set; }
    public string QuantityPerUnit { get; set; }
    public decimal UnitPrice { get; set; }
    public string UnitPriceString { get { return UnitPrice.ToString("######.00"); } }
    public int UnitsInStock { get; set; }
    public string UnitsInStockString { get { return UnitsInStock.ToString("#####0"); } }
    public int CategoryId { get; set; }

    public event PropertyChangedEventHandler PropertyChanged;
    private void NotifyPropertyChanged(string propertyName)
    {
        if (PropertyChanged != null)
        {
            PropertyChanged(this, new PropertyChangedEventArgs(propertyName));
        }
    }

}
```

### <a name="retrieve-products-from-the-sql-server-database"></a><span data-ttu-id="d12a1-132">Produkte aus der SQL Server-Datenbank abrufen</span><span class="sxs-lookup"><span data-stu-id="d12a1-132">Retrieve products from the SQL Server database</span></span>

<span data-ttu-id="d12a1-133">Erstellen Sie eine Methode, die Produkte aus der Northwind-Beispieldatenbank abruft und diese dann als [ObservableCollection](https://msdn.microsoft.com/library/windows/apps/ms668604.aspx)-Collection von ``Product``-Instanzen zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="d12a1-133">Create a method that gets products from the Northwind sample database, and then returns them as an [ObservableCollection](https://msdn.microsoft.com/library/windows/apps/ms668604.aspx) collection of ``Product`` instances.</span></span>

```csharp
public ObservableCollection<Product> GetProducts(string connectionString)
{
    const string GetProductsQuery = "select ProductID, ProductName, QuantityPerUnit," +
       " UnitPrice, UnitsInStock, Products.CategoryID " +
       " from Products inner join Categories on Products.CategoryID = Categories.CategoryID " +
       " where Discontinued = 0";

    var products = new ObservableCollection<Product>();
    try
    {
        using (SqlConnection conn = new SqlConnection(connectionString))
        {
            conn.Open();
            if (conn.State == System.Data.ConnectionState.Open)
            {
                using (SqlCommand cmd = conn.CreateCommand())
                {
                    cmd.CommandText = GetProductsQuery;
                    using (SqlDataReader reader = cmd.ExecuteReader())
                    {
                        while (reader.Read())
                        {
                            var product = new Product();
                            product.ProductID = reader.GetInt32(0);
                            product.ProductName = reader.GetString(1);
                            product.QuantityPerUnit = reader.GetString(2);
                            product.UnitPrice = reader.GetDecimal(3);
                            product.UnitsInStock = reader.GetInt16(4);
                            product.CategoryId = reader.GetInt32(5);
                            products.Add(product);
                        }
                    }
                }
            }
        }
        return products;
    }
    catch (Exception eSql)
    {
        Debug.WriteLine("Exception: " + eSql.Message);
    }
    return null;
}
```

### <a name="add-a-basic-user-interface"></a><span data-ttu-id="d12a1-134">Hinzufügen einer einfachen Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="d12a1-134">Add a basic user interface</span></span>

 <span data-ttu-id="d12a1-135">Fügen Sie den folgenden XAML-Code zur Datei **MainPage.xaml** des UWP-Projekts hinzu.</span><span class="sxs-lookup"><span data-stu-id="d12a1-135">Add the following XAML to the **MainPage.xaml** file of the UWP project.</span></span>

 <span data-ttu-id="d12a1-136">Dieser XAML-Code erstellt ein [ListView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.listview), um jedes Produkt anzuzeigen, das Sie im vorherigen Snippet zurückgegeben haben. Es bindet die Attribute jeder Zeile im [ListView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.listview) an die Eigenschaften, die wir in der Klasse ``Product`` definiert haben.</span><span class="sxs-lookup"><span data-stu-id="d12a1-136">This XAML creates a [ListView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.listview) to show each product that you returned in the previous snippet, and binds the attributes of each row in the [ListView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.listview) to the properties that we defined in the ``Product`` class.</span></span>

```xml
<Grid Background="{ThemeResource SystemControlAcrylicWindowBrush}">
    <RelativePanel>
        <ListView Name="InventoryList"
                  SelectionMode="Single"
                  ScrollViewer.VerticalScrollBarVisibility="Auto"
                  ScrollViewer.IsVerticalRailEnabled="True"
                  ScrollViewer.VerticalScrollMode="Enabled"
                  ScrollViewer.HorizontalScrollMode="Enabled"
                  ScrollViewer.HorizontalScrollBarVisibility="Auto"
                  ScrollViewer.IsHorizontalRailEnabled="True"
                  Margin="20">
            <ListView.HeaderTemplate>
                <DataTemplate>
                    <StackPanel Orientation="Horizontal"  >
                        <TextBlock Text="ID" Margin="8,0" Width="50" Foreground="DarkRed" />
                        <TextBlock Text="Product description" Width="300" Foreground="DarkRed" />
                        <TextBlock Text="Packaging" Width="200" Foreground="DarkRed" />
                        <TextBlock Text="Price" Width="80" Foreground="DarkRed" />
                        <TextBlock Text="In stock" Width="80" Foreground="DarkRed" />
                    </StackPanel>
                </DataTemplate>
            </ListView.HeaderTemplate>
            <ListView.ItemTemplate>
                <DataTemplate x:DataType="local:Product">
                    <StackPanel Orientation="Horizontal" >
                        <TextBlock Name="ItemId"
                                    Text="{x:Bind ProductCode}"
                                    Width="50" />
                        <TextBlock Name="ItemName"
                                    Text="{x:Bind ProductName}"
                                    Width="300" />
                        <TextBlock Text="{x:Bind QuantityPerUnit}"
                                   Width="200" />
                        <TextBlock Text="{x:Bind UnitPriceString}"
                                   Width="80" />
                        <TextBlock Text="{x:Bind UnitsInStockString}"
                                   Width="80" />
                    </StackPanel>
                </DataTemplate>
            </ListView.ItemTemplate>
        </ListView>
    </RelativePanel>
</Grid>
```

### <a name="show-products-in-the-listview"></a><span data-ttu-id="d12a1-137">Produkte im ListView anzeigen</span><span class="sxs-lookup"><span data-stu-id="d12a1-137">Show products in the ListView</span></span>

<span data-ttu-id="d12a1-138">Öffnen Sie die Datei **MainPage.xaml.cs** und fügen Sie Code zum Konstruktor der ``MainPage``-Klasse hinzu, die die **ItemSource**-Eigenschaft des [ListView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.listview) auf die [ObservableCollection](https://msdn.microsoft.com/library/windows/apps/ms668604.aspx) der ``Product``-Instanzen setzt.</span><span class="sxs-lookup"><span data-stu-id="d12a1-138">Open the **MainPage.xaml.cs** file, and add code to the constructor of the ``MainPage`` class that sets the **ItemSource** property of the [ListView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.listview) to the [ObservableCollection](https://msdn.microsoft.com/library/windows/apps/ms668604.aspx) of ``Product`` instances.</span></span>

```csharp
public MainPage()
{
    this.InitializeComponent();
    InventoryList.ItemsSource = GetProducts((App.Current as App).ConnectionString);
}
```

<span data-ttu-id="d12a1-139">Starten Sie das Projekt und sehen Sie sich die Produkte aus der Northwind-Beispieldatenbank in der Benutzeroberfläche an.</span><span class="sxs-lookup"><span data-stu-id="d12a1-139">Start the project and see products from the Northwind sample database appear in the UI.</span></span>

![Northwind-Produkte](images/products-northwind.png)

<span data-ttu-id="d12a1-141">Erkunden Sie den [System.Data.SqlClient](https://msdn.microsoft.com/library/system.data.sqlclient.aspx)-Namespace, um zu sehen, was Sie mit Daten in Ihrer SQL Server-Datenbank noch alles machen können.</span><span class="sxs-lookup"><span data-stu-id="d12a1-141">Explore the [System.Data.SqlClient](https://msdn.microsoft.com/library/system.data.sqlclient.aspx) namespace to see what other things you can do with data in your SQL Server database.</span></span>

## <a name="trouble-connecting-to-your-database"></a><span data-ttu-id="d12a1-142">Probleme beim Herstellen einer Verbindung mit der Datenbank?</span><span class="sxs-lookup"><span data-stu-id="d12a1-142">Trouble connecting to your database?</span></span>

<span data-ttu-id="d12a1-143">In den meisten Fällen muss ein Aspekt der SQL Server-Konfiguration geändert werden.</span><span class="sxs-lookup"><span data-stu-id="d12a1-143">In most cases, some aspect of the SQL Server configuration needs to be changed.</span></span> <span data-ttu-id="d12a1-144">Wenn Sie mit einem anderen Typ von Desktopanwendung wie einer Windows Forms- oder WPF-Anwendung eine Verbindung mit der Datenbank herstellen können, stellen Sie sicher, dass Sie TCP/IP für SQL Server aktiviert haben.</span><span class="sxs-lookup"><span data-stu-id="d12a1-144">If you're able to connect to your database from another type of desktop application such as a Windows Forms or WPF application, ensure that you've enabled TCP/IP for SQL Server.</span></span> <span data-ttu-id="d12a1-145">Dies können über die Konsole **Computerverwaltung** durchführen.</span><span class="sxs-lookup"><span data-stu-id="d12a1-145">You can do that in the **Computer Management** console.</span></span>

![Computerverwaltung](images/computer-management.png)

<span data-ttu-id="d12a1-147">Stellen Sie dann sicher, dass Ihr SQL Server-Browser-Dienst ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="d12a1-147">Then, make sure that your SQL Server Browser service is running.</span></span>

![SQL Server-Browser-Dienst](images/sql-browser-service.png)

## <a name="next-steps"></a><span data-ttu-id="d12a1-149">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="d12a1-149">Next steps</span></span>

**<span data-ttu-id="d12a1-150">Verwenden einer einfachen Datenbank, um Daten auf dem Gerät des Benutzers zu speichern</span><span class="sxs-lookup"><span data-stu-id="d12a1-150">Use a light-weight database to store data on the users device</span></span>**

<span data-ttu-id="d12a1-151">Weitere Infos finden Sie unter [Verwenden Sie eine SQLite-Datenbank in einer UWP-App](sqlite-databases.md).</span><span class="sxs-lookup"><span data-stu-id="d12a1-151">See [Use a SQLite database in a UWP app](sqlite-databases.md).</span></span>

**<span data-ttu-id="d12a1-152">Nutzen Sie Code zwischen verschiedenen Apps auf verschiedenen Plattformen</span><span class="sxs-lookup"><span data-stu-id="d12a1-152">Share code between different apps across different platforms</span></span>**

<span data-ttu-id="d12a1-153">Weitere Informationen finden Sie unter [Teilen von Code zwischen einer Desktop-App und einer UWP-App](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-migrate)</span><span class="sxs-lookup"><span data-stu-id="d12a1-153">See [Share code between desktop and UWP](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-migrate).</span></span>

**<span data-ttu-id="d12a1-154">Hinzufügen von Master-Detailseiten mit Azure SQL-Backends</span><span class="sxs-lookup"><span data-stu-id="d12a1-154">Add master detail pages with Azure SQL back ends</span></span>**

<span data-ttu-id="d12a1-155">Mehr unter [Beispiel einer Kundenauftragsdatenbank.](https://github.com/Microsoft/Windows-appsample-customers-orders-database)</span><span class="sxs-lookup"><span data-stu-id="d12a1-155">See [Customer Orders Database sample](https://github.com/Microsoft/Windows-appsample-customers-orders-database).</span></span>
