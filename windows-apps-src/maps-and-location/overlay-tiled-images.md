---
title: Überlagern von nebeneinander angeordneten Bildern in einer Karte
description: Überlagern Sie Bilder von Drittanbietern oder benutzerdefinierte nebeneinander angeordnete Bilder in einer Karte mithilfe von Kachelquellen. Verwenden Sie Kachelquellen, um spezielle Infos wie Wetterdaten, Einwohnerzahlen oder seismische Daten zu überlagern oder die Standardkarte vollständig zu ersetzen.
ms.assetid: 066BD6E2-C22B-4F5B-AA94-5D6C86A09BDF
ms.date: 07/19/2018
ms.topic: article
keywords: Windows10, UWP, Karte, Standort, Bilder, Überlagerung
ms.localizationpriority: medium
ms.openlocfilehash: 47b9c4335a99e7b0f17da0fb9ddb520cc917e398
ms.sourcegitcommit: b5c9c18e70625ab770946b8243f3465ee1013184
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/29/2018
ms.locfileid: "7992756"
---
# <a name="overlay-tiled-images-on-a-map"></a><span data-ttu-id="847ed-105">Überlagern von nebeneinander angeordneten Bildern in einer Karte</span><span class="sxs-lookup"><span data-stu-id="847ed-105">Overlay tiled images on a map</span></span>

<span data-ttu-id="847ed-106">Überlagern Sie Bilder von Drittanbietern oder benutzerdefinierte nebeneinander angeordnete Bilder in einer Karte mithilfe von Kachelquellen.</span><span class="sxs-lookup"><span data-stu-id="847ed-106">Overlay third-party or custom tiled images on a map by using tile sources.</span></span> <span data-ttu-id="847ed-107">Verwenden Sie Kachelquellen, um spezielle Infos wie Wetterdaten, Einwohnerzahlen oder seismische Daten zu überlagern oder die Standardkarte vollständig zu ersetzen.</span><span class="sxs-lookup"><span data-stu-id="847ed-107">Use tile sources to overlay specialized information such as weather data, population data, or seismic data; or use tile sources to replace the default map entirely.</span></span>

<span data-ttu-id="847ed-108">**Tipp**: Laden Sie das [Kartenbeispiel für die Universelle Windows-Plattform (UWP)](http://go.microsoft.com/fwlink/p/?LinkId=619977) auf Github herunter, um mehr über die Verwendung von Karten in Ihrer App zu erfahren.</span><span class="sxs-lookup"><span data-stu-id="847ed-108">**Tip** To learn more about using maps in your app, download the [Universal Windows Platform (UWP) map sample](http://go.microsoft.com/fwlink/p/?LinkId=619977) on Github.</span></span>

<a id="tileintro" />

## <a name="tiled-image-overview"></a><span data-ttu-id="847ed-109">Übersicht über nebeneinander angeordnete Bilder</span><span class="sxs-lookup"><span data-stu-id="847ed-109">Tiled image overview</span></span>

<span data-ttu-id="847ed-110">Kartendienste wie Nokia Karten und Bing Maps teilen Karten zum schnellen Abrufen und Anzeigen in quadratische Kacheln ein.</span><span class="sxs-lookup"><span data-stu-id="847ed-110">Map services such as Nokia Maps and Bing Maps cut maps into square tiles for quick retrieval and display.</span></span> <span data-ttu-id="847ed-111">Diese Kacheln messen 256 x 256 Pixel und werden vorab auf mehrere Detailebenen gerendert.</span><span class="sxs-lookup"><span data-stu-id="847ed-111">These tiles are 256 pixels by 256 pixels in size, and are pre-rendered at multiple levels of detail.</span></span> <span data-ttu-id="847ed-112">Viele Dienste von Drittanbietern umfassen auch kartenbasierte Daten, die in Kacheln aufgeteilt sind.</span><span class="sxs-lookup"><span data-stu-id="847ed-112">Many third-party services also provide map-based data that's cut into tiles.</span></span> <span data-ttu-id="847ed-113">Verwenden Sie Kachelquellen, um Kacheln von Drittanbietern abzurufen oder benutzerdefinierte Kacheln zu erstellen. Überlagern Sie diese auf der angezeigten Karte im [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="847ed-113">Use tile sources to retrieve third-party tiles, or to create your own custom tiles, and overlay them on the map displayed in the [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004).</span></span>

<span data-ttu-id="847ed-114">**Wichtige**  Wenn Sie kachelquellen verwenden, Sie müssen keinen Code zum Anfordern oder zum Positionieren der einzelner Kacheln schreiben.</span><span class="sxs-lookup"><span data-stu-id="847ed-114">**Important** When you use tile sources, you don't have to write code to request or to position individual tiles.</span></span> <span data-ttu-id="847ed-115">Das [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004)-Objekt fordert bei Bedarf Kacheln an.</span><span class="sxs-lookup"><span data-stu-id="847ed-115">The [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004) requests tiles as it needs them.</span></span> <span data-ttu-id="847ed-116">Bei jeder Anforderung werden die X- und Y-Koordinaten und der Zoomfaktor für die einzelnen Kacheln angegeben.</span><span class="sxs-lookup"><span data-stu-id="847ed-116">Each request specifies the X and Y coordinates and the zoom level for the individual tile.</span></span> <span data-ttu-id="847ed-117">Geben Sie einfach das Format des URIs oder Dateinamens an, um die Kacheln in der **UriFormatString**-Eigenschaft abzurufen.</span><span class="sxs-lookup"><span data-stu-id="847ed-117">You simply specify the format of the Uri or filename to use to retrieve the tiles in the **UriFormatString** property.</span></span> <span data-ttu-id="847ed-118">Dazu fügen Sie ersetzbare Parameter in den Basis-URI oder Dateinamen ein, um anzugeben, wo die X- und Y-Koordinaten und der Zoomfaktor für jede Kachel übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="847ed-118">That is, you insert replaceable parameters in the base Uri or filename to indicate where to pass the X and Y coordinates and the zoom level for each tile.</span></span>

<span data-ttu-id="847ed-119">In diesem Beispiel sehen Sie eine [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636992)-Eigenschaft für eine [**HttpMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636986)-Klasse. Diese zeigt die ersetzbaren Parameter für die X- und Y-Koordinaten und den Zoomfaktor an.</span><span class="sxs-lookup"><span data-stu-id="847ed-119">Here's an example of the [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636992) property for an [**HttpMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636986) that shows the replaceable parameters for the X and Y coordinates and the zoom level.</span></span>

```syntax
http://www.<web service name>.com/z={zoomlevel}&x={x}&y={y}
```

<span data-ttu-id="847ed-120">(Die X- und Y-Koordinaten stellen die Position der einzelnen Kachel in der Zuordnung der Weltkarte auf der angegebenen Detailebene dar.</span><span class="sxs-lookup"><span data-stu-id="847ed-120">(The X and Y coordinates represent the location of the individual tile within the map of the world at the specified level of detail.</span></span> <span data-ttu-id="847ed-121">Die Nummerierung der Kachel beginnt bei {0, 0} in der oberen linken Ecke der Karte.</span><span class="sxs-lookup"><span data-stu-id="847ed-121">The tile numbering system starts from {0, 0} in the upper left corner of the map.</span></span> <span data-ttu-id="847ed-122">Die Kachel bei {1, 2} befindet sich beispielsweise in der zweiten Spalte der dritten Zeile des Kachelrasters.)</span><span class="sxs-lookup"><span data-stu-id="847ed-122">For example, the tile at {1, 2} is in the second column of the third row of the grid of tiles.)</span></span>

<span data-ttu-id="847ed-123">Weitere Informationen über das Kachelsystem von Kartendiensten finden Sie unter [Kachelsystem von Bing Maps](http://go.microsoft.com/fwlink/p/?LinkId=626692).</span><span class="sxs-lookup"><span data-stu-id="847ed-123">For more info about the tile system used by mapping services, see [Bing Maps Tile System](http://go.microsoft.com/fwlink/p/?LinkId=626692).</span></span>

### <a name="overlay-tiles-from-a-tile-source"></a><span data-ttu-id="847ed-124">Überlagern von Kacheln aus einer Kachelquelle</span><span class="sxs-lookup"><span data-stu-id="847ed-124">Overlay tiles from a tile source</span></span>

<span data-ttu-id="847ed-125">Überlagern Sie nebeneinander angeordnete Bilder aus einer Kachelquelle in einer Karte mithilfe der [**MapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn637141)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="847ed-125">Overlay tiled images from a tile source on a map by using the [**MapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn637141).</span></span>

1.  <span data-ttu-id="847ed-126">Instanziieren Sie eine der drei Klassen für Kacheldatenquellen, die von der [**MapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn637141)-Klasse erben.</span><span class="sxs-lookup"><span data-stu-id="847ed-126">Instantiate one of the three tile data source classes that inherit from [**MapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn637141).</span></span>

    -   [**<span data-ttu-id="847ed-127">HttpMapTileDataSource</span><span class="sxs-lookup"><span data-stu-id="847ed-127">HttpMapTileDataSource</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn636986)
    -   [**<span data-ttu-id="847ed-128">LocalMapTileDataSource</span><span class="sxs-lookup"><span data-stu-id="847ed-128">LocalMapTileDataSource</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn636994)
    -   [**<span data-ttu-id="847ed-129">CustomMapTileDataSource</span><span class="sxs-lookup"><span data-stu-id="847ed-129">CustomMapTileDataSource</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn636983)

    <span data-ttu-id="847ed-130">Konfigurieren Sie die **UriFormatString**-Eigenschaft zum Anfordern der Kacheln, indem Sie ersetzbare Parameter im Basis-URI oder Dateinamen einfügen.</span><span class="sxs-lookup"><span data-stu-id="847ed-130">Configure the **UriFormatString** to use to request the tiles by inserting replaceable parameters in the base Uri or filename.</span></span>

    <span data-ttu-id="847ed-131">Im folgenden Beispiel wird eine [**HttpMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636986)-Klasse instanziiert.</span><span class="sxs-lookup"><span data-stu-id="847ed-131">The following example instantiates an [**HttpMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636986).</span></span> <span data-ttu-id="847ed-132">In diesem Beispiel wird der Wert der [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636992)-Eigenschaft im Konstruktor der **HttpMapTileDataSource**-Klasse veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="847ed-132">This example specifies the value of the [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636992) in the constructor of the **HttpMapTileDataSource**.</span></span>

    ```csharp
        HttpMapTileDataSource dataSource = new HttpMapTileDataSource(
          "http://www.<web service name>.com/z={zoomlevel}&x={x}&y={y}");
    ```

2.  <span data-ttu-id="847ed-133">Instanziieren und konfigurieren Sie eine [**MapTileSource**](https://msdn.microsoft.com/library/windows/apps/dn637144)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="847ed-133">Instantiate and configure a [**MapTileSource**](https://msdn.microsoft.com/library/windows/apps/dn637144).</span></span> <span data-ttu-id="847ed-134">Geben Sie die [**MapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn637141)-Klasse an, die Sie im vorherigen Schritt als [**DataSource**](https://msdn.microsoft.com/library/windows/apps/dn637149)-Eigenschaft der **MapTileSource**-Klasse festgelegt haben.</span><span class="sxs-lookup"><span data-stu-id="847ed-134">Specify the [**MapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn637141) that you configured in the previous step as the [**DataSource**](https://msdn.microsoft.com/library/windows/apps/dn637149) of the **MapTileSource**.</span></span>

    <span data-ttu-id="847ed-135">Im folgenden Beispiel wird die [**DataSource**](https://msdn.microsoft.com/library/windows/apps/dn637149)-Eigenschaft im Konstruktor der [**MapTileSource**](https://msdn.microsoft.com/library/windows/apps/dn637144)-Klasse veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="847ed-135">The following example specifies the [**DataSource**](https://msdn.microsoft.com/library/windows/apps/dn637149) in the constructor of the [**MapTileSource**](https://msdn.microsoft.com/library/windows/apps/dn637144).</span></span>

    ```csharp
        MapTileSource tileSource = new MapTileSource(dataSource);
    ```

    <span data-ttu-id="847ed-136">Sie können die Bedingungen, unter denen Kacheln angezeigt werden, mithilfe der Eigenschaften der [**MapTileSource**](https://msdn.microsoft.com/library/windows/apps/dn637144)-Klasse einschränken.</span><span class="sxs-lookup"><span data-stu-id="847ed-136">You can restrict the conditions in which the tiles are displayed by using properties of the [**MapTileSource**](https://msdn.microsoft.com/library/windows/apps/dn637144).</span></span>

    -   <span data-ttu-id="847ed-137">Zeigen Sie Kacheln nur in einem bestimmten geografischen Bereich an, indem Sie einen Wert für die [**Bounds**](https://msdn.microsoft.com/library/windows/apps/dn637147)-Eigenschaft angeben.</span><span class="sxs-lookup"><span data-stu-id="847ed-137">Display tiles only within a specific geographic area by providing a value for the [**Bounds**](https://msdn.microsoft.com/library/windows/apps/dn637147) property.</span></span>
    -   <span data-ttu-id="847ed-138">Zeigen Sie Kacheln nur auf bestimmten Detailebenen an, indem Sie einen Wert für die [**ZoomLevelRange**](https://msdn.microsoft.com/library/windows/apps/dn637171)-Eigenschaft angeben.</span><span class="sxs-lookup"><span data-stu-id="847ed-138">Display tiles only at certain levels of detail by providing a value for the [**ZoomLevelRange**](https://msdn.microsoft.com/library/windows/apps/dn637171) property.</span></span>

    <span data-ttu-id="847ed-139">Optional können Sie weitere Eigenschaften der [**MapTileSource**](https://msdn.microsoft.com/library/windows/apps/dn637144)-Klasse konfigurieren, die Auswirkungen auf das Laden oder die Anzeige von Kacheln haben, z. B. [**Layer**](https://msdn.microsoft.com/library/windows/apps/dn637157), [**AllowOverstretch**](https://msdn.microsoft.com/library/windows/apps/dn637145), [**IsRetryEnabled**](https://msdn.microsoft.com/library/windows/apps/dn637153) und [**IsTransparencyEnabled**](https://msdn.microsoft.com/library/windows/apps/dn637155).</span><span class="sxs-lookup"><span data-stu-id="847ed-139">Optionally, configure other properties of the [**MapTileSource**](https://msdn.microsoft.com/library/windows/apps/dn637144) that affect the loading or the display of the tiles, such as [**Layer**](https://msdn.microsoft.com/library/windows/apps/dn637157), [**AllowOverstretch**](https://msdn.microsoft.com/library/windows/apps/dn637145), [**IsRetryEnabled**](https://msdn.microsoft.com/library/windows/apps/dn637153), and [**IsTransparencyEnabled**](https://msdn.microsoft.com/library/windows/apps/dn637155).</span></span>

3.  <span data-ttu-id="847ed-140">Fügen Sie die [**MapTileSource**](https://msdn.microsoft.com/library/windows/apps/dn637144)-Klasse der [**TileSources**](https://msdn.microsoft.com/library/windows/apps/dn637053)-Collection dem [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004)-Objekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="847ed-140">Add the [**MapTileSource**](https://msdn.microsoft.com/library/windows/apps/dn637144) to the [**TileSources**](https://msdn.microsoft.com/library/windows/apps/dn637053) collection of the [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004).</span></span>

    ```csharp
         MapControl1.TileSources.Add(tileSource);
    ```

## <a name="overlay-tiles-from-a-web-service"></a><span data-ttu-id="847ed-141">Überlagern von Kacheln aus einem Webdienst</span><span class="sxs-lookup"><span data-stu-id="847ed-141">Overlay tiles from a web service</span></span>


<span data-ttu-id="847ed-142">Überlagern Sie nebeneinander angeordnete Bilder aus einem Webdienst mithilfe der [**HttpMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636986)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="847ed-142">Overlay tiled images retrieved from a web service by using the [**HttpMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636986).</span></span>

1.  <span data-ttu-id="847ed-143">Instanziieren Sie eine [**HttpMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636986)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="847ed-143">Instantiate an [**HttpMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636986).</span></span>
2.  <span data-ttu-id="847ed-144">Geben Sie das Format des URIs an, den der Webdienst als Wert für die [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636992)-Eigenschaft erwartet.</span><span class="sxs-lookup"><span data-stu-id="847ed-144">Specify the format of the Uri that the web service expects as the value of the [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636992) property.</span></span> <span data-ttu-id="847ed-145">Um diesen Wert zu erstellen, fügen Sie dem Basis-URI die ersetzbaren Parameter hinzu.</span><span class="sxs-lookup"><span data-stu-id="847ed-145">To create this value, insert replaceable parameters in the base Uri.</span></span> <span data-ttu-id="847ed-146">Im folgenden Codebeispiel beträgt der Wert der **UriFormatString**-Eigenschaft beispielsweise:</span><span class="sxs-lookup"><span data-stu-id="847ed-146">For example, in the following code sample, the value of the **UriFormatString** is:</span></span>

    ``` syntax
    http://www.<web service name>.com/z={zoomlevel}&x={x}&y={y}
    ```

    <span data-ttu-id="847ed-147">Der Webdienst muss einen URI unterstützen, der die ersetzbaren Parameter {x}, {y} und {zoomlevel} enthält.</span><span class="sxs-lookup"><span data-stu-id="847ed-147">The web service has to support a Uri that contains the replaceable parameters {x}, {y}, and {zoomlevel}.</span></span> <span data-ttu-id="847ed-148">Die meisten Webdienste (z.B. Nokia, Bing und Google) unterstützen URIs in diesem Format.</span><span class="sxs-lookup"><span data-stu-id="847ed-148">Most web services (for example, Nokia, Bing, and Google) support Uris in this format.</span></span> <span data-ttu-id="847ed-149">Benötigt der Webdienst zusätzliche Argumente, die mit der [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636992)-Eigenschaft nicht zur Verfügung stehen, müssen Sie einen benutzerdefinierten URI erstellen.</span><span class="sxs-lookup"><span data-stu-id="847ed-149">If the web service requires additional arguments that aren't available with the [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636992) property, then you have to create a custom Uri.</span></span> <span data-ttu-id="847ed-150">Mithilfe des [**UriRequested**](https://msdn.microsoft.com/library/windows/apps/dn636993)-Ereignisses können Sie einen benutzerdefinierten URI erstellen und zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="847ed-150">Create and return a custom Uri by handling the [**UriRequested**](https://msdn.microsoft.com/library/windows/apps/dn636993) event.</span></span> <span data-ttu-id="847ed-151">Weitere Infos finden Sie im Abschnitt [Bereitstellen eines benutzerdefinierten URIs](#customuri) weiter unten in diesem Thema.</span><span class="sxs-lookup"><span data-stu-id="847ed-151">For more info, see the [Provide a custom URI](#customuri) section later in this topic.</span></span>

3.  <span data-ttu-id="847ed-152">Befolgen Sie die verbleibenden Schritte in der [Übersicht über nebeneinander angeordnete Bilder](#tileintro).</span><span class="sxs-lookup"><span data-stu-id="847ed-152">Then, follow the remaining steps described previously in the [Tiled image overview](#tileintro).</span></span>

<span data-ttu-id="847ed-153">Im folgenden Beispiel überlagern Kacheln aus einem fiktiven Webdienst eine Karte von Nordamerika.</span><span class="sxs-lookup"><span data-stu-id="847ed-153">The following example overlays tiles from a fictitious web service on a map of North America.</span></span> <span data-ttu-id="847ed-154">Der Wert der [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636992)-Eigenschaft ist im Konstruktor der [**HttpMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636986)-Klasse angegeben.</span><span class="sxs-lookup"><span data-stu-id="847ed-154">The value of the [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636992) is specified in the constructor of the [**HttpMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636986).</span></span> <span data-ttu-id="847ed-155">In diesem Beispiel werden durch Festlegen der optionalen [**Bounds**](https://msdn.microsoft.com/library/windows/apps/dn637147)-Eigenschaft nur Kacheln innerhalb der geografischen Bereiche angegeben.</span><span class="sxs-lookup"><span data-stu-id="847ed-155">In this example, tiles are only displayed within the geographic boundaries specified by the optional [**Bounds**](https://msdn.microsoft.com/library/windows/apps/dn637147) property.</span></span>

```csharp
private void AddHttpMapTileSource()
{
    // Create the bounding box in which the tiles are displayed.
    // This example represents North America.
    BasicGeoposition northWestCorner =
        new BasicGeoposition() { Latitude = 48.38544, Longitude = -124.667360 };
    BasicGeoposition southEastCorner =
        new BasicGeoposition() { Latitude = 25.26954, Longitude = -80.30182 };
    GeoboundingBox boundingBox = new GeoboundingBox(northWestCorner, southEastCorner);

    // Create an HTTP data source.
    // This example retrieves tiles from a fictitious web service.
    HttpMapTileDataSource dataSource = new HttpMapTileDataSource(
        "http://www.<web service name>.com/z={zoomlevel}&x={x}&y={y}");

    // Optionally, add custom HTTP headers if the web service requires them.
    dataSource.AdditionalRequestHeaders.Add("header name", "header value");

    // Create a tile source and add it to the Map control.
    MapTileSource tileSource = new MapTileSource(dataSource);
    tileSource.Bounds = boundingBox;
    MapControl1.TileSources.Add(tileSource);
}
```

```cppwinrt
...
#include <winrt/Windows.Devices.Geolocation.h>
#include <winrt/Windows.UI.Xaml.Controls.Maps.h>
...
void MainPage::AddHttpMapTileSource()
{
    Windows::Devices::Geolocation::BasicGeoposition northWest{ 48.38544, -124.667360 };
    Windows::Devices::Geolocation::BasicGeoposition southEast{ 25.26954, -80.30182 };
    Windows::Devices::Geolocation::GeoboundingBox boundingBox{ northWest, southEast };

    Windows::UI::Xaml::Controls::Maps::HttpMapTileDataSource dataSource{
        L"http://www.<web service name>.com/z={zoomlevel}&x={x}&y={y}" };

    dataSource.AdditionalRequestHeaders().Insert(L"header name", L"header value");

    Windows::UI::Xaml::Controls::Maps::MapTileSource tileSource{ dataSource };
    tileSource.Bounds(boundingBox);

    MapControl1().TileSources().Append(tileSource);
}
...
```

```cpp
void MainPage::AddHttpMapTileSource()
{
    BasicGeoposition northWest = { 48.38544, -124.667360 };
    BasicGeoposition southEast = { 25.26954, -80.30182 };
    GeoboundingBox^ boundingBox = ref new GeoboundingBox(northWest, southEast);

    auto dataSource = ref new Windows::UI::Xaml::Controls::Maps::HttpMapTileDataSource(
        "http://www.<web service name>.com/z={zoomlevel}&x={x}&y={y}");

    dataSource->AdditionalRequestHeaders->Insert("header name", "header value");

    auto tileSource = ref new Windows::UI::Xaml::Controls::Maps::MapTileSource(dataSource);
    tileSource->Bounds = boundingBox;

    this->MapControl1->TileSources->Append(tileSource);
}
```

## <a name="overlay-tiles-from-local-storage"></a><span data-ttu-id="847ed-156">Überlagern von Kacheln aus dem lokalen Speicher</span><span class="sxs-lookup"><span data-stu-id="847ed-156">Overlay tiles from local storage</span></span>


<span data-ttu-id="847ed-157">Überlagern Sie nebeneinander angeordnete Bilder, die als Dateien im lokalen Speicher gespeichert sind, mithilfe der [**LocalMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636994)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="847ed-157">Overlay tiled images stored as files in local storage by using the [**LocalMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636994).</span></span> <span data-ttu-id="847ed-158">In der Regel können Sie diese Dateien mit Ihrer App verpacken und verteilen.</span><span class="sxs-lookup"><span data-stu-id="847ed-158">Typically, you package and distribute these files with your app.</span></span>

1.  <span data-ttu-id="847ed-159">Instanziieren Sie eine [**LocalMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636994)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="847ed-159">Instantiate a [**LocalMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636994).</span></span>
2.  <span data-ttu-id="847ed-160">Geben Sie das Format der Dateinamen als Wert für die [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636998)-Eigenschaft ein.</span><span class="sxs-lookup"><span data-stu-id="847ed-160">Specify the format of the file names as the value of the [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636998) property.</span></span> <span data-ttu-id="847ed-161">Um diesen Wert zu erstellen, fügen Sie dem Basis-Dateinamen die ersetzbaren Parameter hinzu.</span><span class="sxs-lookup"><span data-stu-id="847ed-161">To create this value, insert replaceable parameters in the base filename.</span></span> <span data-ttu-id="847ed-162">Im folgenden Codebeispiel hat die [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636992)-Eigenschaft beispielsweise den Wert:</span><span class="sxs-lookup"><span data-stu-id="847ed-162">For example, in the following code sample, the value of the [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636992) is:</span></span>

    ``` syntax
        Tile_{zoomlevel}_{x}_{y}.png
    ```

    <span data-ttu-id="847ed-163">Wenn das Format der Dateinamen zusätzliche Argumente benötigt, die mit der [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636998)-Eigenschaft nicht zur Verfügung stehen, müssen Sie einen benutzerdefinierten URI erstellen.</span><span class="sxs-lookup"><span data-stu-id="847ed-163">If the format of the file names requires additional arguments that aren't available with the [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636998) property, then you have to create a custom Uri.</span></span> <span data-ttu-id="847ed-164">Mithilfe des [**UriRequested**](https://msdn.microsoft.com/library/windows/apps/dn637001)-Ereignisses können Sie einen benutzerdefinierten URI erstellen und zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="847ed-164">Create and return a custom Uri by handling the [**UriRequested**](https://msdn.microsoft.com/library/windows/apps/dn637001) event.</span></span> <span data-ttu-id="847ed-165">Weitere Infos finden Sie im Abschnitt [Bereitstellen eines benutzerdefinierten URIs](#customuri) weiter unten in diesem Thema.</span><span class="sxs-lookup"><span data-stu-id="847ed-165">For more info, see the [Provide a custom URI](#customuri) section later in this topic.</span></span>

3.  <span data-ttu-id="847ed-166">Befolgen Sie die verbleibenden Schritte in der [Übersicht über nebeneinander angeordnete Bilder](#tileintro).</span><span class="sxs-lookup"><span data-stu-id="847ed-166">Then, follow the remaining steps described previously in the [Tiled image overview](#tileintro).</span></span>

<span data-ttu-id="847ed-167">Zum Laden von Kacheln aus dem lokalen Speicher können Sie die folgenden Protokolle und Speicherorte verwenden:</span><span class="sxs-lookup"><span data-stu-id="847ed-167">You can use the following protocols and locations to load tiles from local storage:</span></span>

| <span data-ttu-id="847ed-168">URI</span><span class="sxs-lookup"><span data-stu-id="847ed-168">Uri</span></span> | <span data-ttu-id="847ed-169">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="847ed-169">More info</span></span> |
|---------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="847ed-170">ms-appx:///</span><span class="sxs-lookup"><span data-stu-id="847ed-170">ms-appx:///</span></span> | <span data-ttu-id="847ed-171">Verweist auf das Stammelement des App-Installationsordners.</span><span class="sxs-lookup"><span data-stu-id="847ed-171">Points to the root of the app's installation folder.</span></span> |
|  | <span data-ttu-id="847ed-172">Dies ist der von der [Package.InstalledLocation](https://msdn.microsoft.com/library/windows/apps/br224681)-Eigenschaft referenzierte Speicherort.</span><span class="sxs-lookup"><span data-stu-id="847ed-172">This is the location referenced by the [Package.InstalledLocation](https://msdn.microsoft.com/library/windows/apps/br224681) property.</span></span> |
| <span data-ttu-id="847ed-173">ms-appdata:///local</span><span class="sxs-lookup"><span data-stu-id="847ed-173">ms-appdata:///local</span></span> | <span data-ttu-id="847ed-174">Verweist auf das Stammelement des lokalen Speichers der App.</span><span class="sxs-lookup"><span data-stu-id="847ed-174">Points to the root of the app's local storage.</span></span> |
|  | <span data-ttu-id="847ed-175">Dies ist der von der [ApplicationData.LocalFolder](https://msdn.microsoft.com/library/windows/apps/br241621)-Eigenschaft referenzierte Speicherort.</span><span class="sxs-lookup"><span data-stu-id="847ed-175">This is the location referenced by the [ApplicationData.LocalFolder](https://msdn.microsoft.com/library/windows/apps/br241621) property.</span></span> |
| <span data-ttu-id="847ed-176">ms-appdata:///temp</span><span class="sxs-lookup"><span data-stu-id="847ed-176">ms-appdata:///temp</span></span> | <span data-ttu-id="847ed-177">Verweist auf die temporären Ordner der App.</span><span class="sxs-lookup"><span data-stu-id="847ed-177">Points to the app's temp folder.</span></span> |
|  | <span data-ttu-id="847ed-178">Dies ist der Pfad, auf den die [ApplicationData.TemporaryFolder](https://msdn.microsoft.com/library/windows/apps/br241629)-Eigenschaft verweist.</span><span class="sxs-lookup"><span data-stu-id="847ed-178">This is the location referenced by the [ApplicationData.TemporaryFolder](https://msdn.microsoft.com/library/windows/apps/br241629) property.</span></span> |

 

<span data-ttu-id="847ed-179">Im folgenden Beispiel werden Kacheln, die als Dateien im Installationsverzeichnis der App gespeichert werden, mithilfe des `ms-appx:///`-Protokolls geladen.</span><span class="sxs-lookup"><span data-stu-id="847ed-179">The following example loads tiles that are stored as files in the app's installation folder by using the `ms-appx:///` protocol.</span></span> <span data-ttu-id="847ed-180">Der Wert der [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636998)-Eigenschaft ist im Konstruktor der [**LocalMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636994)-Klasse angegeben.</span><span class="sxs-lookup"><span data-stu-id="847ed-180">The value for the [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636998) is specified in the constructor of the [**LocalMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636994).</span></span> <span data-ttu-id="847ed-181">In diesem Beispiel werden Kacheln nur angezeigt, wenn der Zoomfaktor für die Karte innerhalb des Bereichs liegt, der durch die optionale [**ZoomLevelRange**](https://msdn.microsoft.com/library/windows/apps/dn637171)-Eigenschaft angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="847ed-181">In this example, tiles are only displayed when the zoom level of the map is within the range specified by the optional [**ZoomLevelRange**](https://msdn.microsoft.com/library/windows/apps/dn637171) property.</span></span>

```csharp
        void AddLocalMapTileSource()
        {
            // Specify the range of zoom levels
            // at which the overlaid tiles are displayed.
            MapZoomLevelRange range;
            range.Min = 11;
            range.Max = 20;

            // Create a local data source.
            LocalMapTileDataSource dataSource = new LocalMapTileDataSource(
                "ms-appx:///TileSourceAssets/Tile_{zoomlevel}_{x}_{y}.png");

            // Create a tile source and add it to the Map control.
            MapTileSource tileSource = new MapTileSource(dataSource);
            tileSource.ZoomLevelRange = range;
            MapControl1.TileSources.Add(tileSource);
        }
```

<a id="customuri" />

## <a name="provide-a-custom-uri"></a><span data-ttu-id="847ed-182">Bereitstellen eines benutzerdefinierten URIs</span><span class="sxs-lookup"><span data-stu-id="847ed-182">Provide a custom URI</span></span>

<span data-ttu-id="847ed-183">Wenn die ersetzbaren Parameter, die mit der [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636992)-Eigenschaft der [**HttpMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636986)-Klasse oder der [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636998)-Eigenschaft der [**LocalMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636994)-Klasse zur Verfügung stehen, nicht zum Abrufen Ihrer Kacheln ausreichen, müssen Sie einen benutzerdefinierten URI erstellen.</span><span class="sxs-lookup"><span data-stu-id="847ed-183">If the replaceable parameters available with the [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636992) property of the [**HttpMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636986) or the [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636998) property of the [**LocalMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636994) aren't sufficient to retrieve your tiles, then you have to create a custom Uri.</span></span> <span data-ttu-id="847ed-184">Indem Sie einen benutzerdefinierten Handler für das **UriRequested**-Ereignis bereitstellen, können Sie einen benutzerdefinierten URI erstellen und zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="847ed-184">Create and return a custom Uri by providing a custom handler for the **UriRequested** event.</span></span> <span data-ttu-id="847ed-185">Das **UriRequested**-Ereignis wird für jede einzelne Kachel ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="847ed-185">The **UriRequested** event is raised for each individual tile.</span></span>

1.  <span data-ttu-id="847ed-186">Kombinieren Sie in Ihrem benutzerdefinierten Handler für das **UriRequested**-Ereignis die erforderlichen benutzerdefinierten Argumente mit den Eigenschaften [**X**](https://msdn.microsoft.com/library/windows/apps/dn610743), [**Y**](https://msdn.microsoft.com/library/windows/apps/dn610744) und [**ZoomLevel**](https://msdn.microsoft.com/library/windows/apps/dn610745) der [**MapTileUriRequestedEventArgs**](https://msdn.microsoft.com/library/windows/apps/dn637177)-Klasse, um den benutzerdefinierten URI zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="847ed-186">In your custom handler for the **UriRequested** event, combine the required custom arguments with the [**X**](https://msdn.microsoft.com/library/windows/apps/dn610743), [**Y**](https://msdn.microsoft.com/library/windows/apps/dn610744), and [**ZoomLevel**](https://msdn.microsoft.com/library/windows/apps/dn610745) properties of the [**MapTileUriRequestedEventArgs**](https://msdn.microsoft.com/library/windows/apps/dn637177) to create the custom Uri.</span></span>
2.  <span data-ttu-id="847ed-187">Geben Sie die benutzerdefinierte URI in der [**Uri**](https://msdn.microsoft.com/library/windows/apps/dn610748)-Eigenschaft der [**MapTileUriRequest**](https://msdn.microsoft.com/library/windows/apps/dn637173)-Klasse zurück. Diese ist in der [**Request**](https://msdn.microsoft.com/library/windows/apps/dn637179)-Eigenschaft der [**MapTileUriRequestedEventArgs**](https://msdn.microsoft.com/library/windows/apps/dn637177)-Klasse enthalten.</span><span class="sxs-lookup"><span data-stu-id="847ed-187">Return the custom Uri in the [**Uri**](https://msdn.microsoft.com/library/windows/apps/dn610748) property of the [**MapTileUriRequest**](https://msdn.microsoft.com/library/windows/apps/dn637173), which is contained in the [**Request**](https://msdn.microsoft.com/library/windows/apps/dn637179) property of the [**MapTileUriRequestedEventArgs**](https://msdn.microsoft.com/library/windows/apps/dn637177).</span></span>

<span data-ttu-id="847ed-188">Das folgende Beispiel zeigt, wie Sie einen benutzerdefinierten URI durch Erstellen eines benutzerdefinierten Handlers für das **UriRequested**-Ereignis bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="847ed-188">The following example shows how to provide a custom Uri by creating a custom handler for the **UriRequested** event.</span></span> <span data-ttu-id="847ed-189">Sie erfahren zudem, wie Sie das Verzögerungsmuster implementieren, wenn Sie asynchron zum Erstellen des benutzerdefinierten URIs weitere Schritte ausführen müssen.</span><span class="sxs-lookup"><span data-stu-id="847ed-189">It also shows how to implement the deferral pattern if you have to do something asynchronously to create the custom Uri.</span></span>

```csharp
using Windows.UI.Xaml.Controls.Maps;
using System.Threading.Tasks;
...
            var httpTileDataSource = new HttpMapTileDataSource();
            // Attach a handler for the UriRequested event.
            httpTileDataSource.UriRequested += HandleUriRequestAsync;
            MapTileSource httpTileSource = new MapTileSource(httpTileDataSource);
            MapControl1.TileSources.Add(httpTileSource);
...
        // Handle the UriRequested event.
        private async void HandleUriRequestAsync(HttpMapTileDataSource sender,
            MapTileUriRequestedEventArgs args)
        {
            // Get a deferral to do something asynchronously.
            // Omit this line if you don't have to do something asynchronously.
            var deferral = args.Request.GetDeferral();

            // Get the custom Uri.
            var uri = await GetCustomUriAsync(args.X, args.Y, args.ZoomLevel);

            // Specify the Uri in the Uri property of the MapTileUriRequest.
            args.Request.Uri = uri;

            // Notify the app that the custom Uri is ready.
            // Omit this line also if you don't have to do something asynchronously.
            deferral.Complete();
        }

        // Create the custom Uri.
        private async Task<Uri> GetCustomUriAsync(int x, int y, int zoomLevel)
        {
            // Do something asynchronously to create and return the custom Uri.        }
        }
```

## <a name="overlay-tiles-from-a-custom-source"></a><span data-ttu-id="847ed-190">Überlagern von Kacheln aus einer benutzerdefinierten Quelle</span><span class="sxs-lookup"><span data-stu-id="847ed-190">Overlay tiles from a custom source</span></span>

<span data-ttu-id="847ed-191">Überlagern Sie benutzerdefinierte Kacheln mithilfe der [**CustomMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636983)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="847ed-191">Overlay custom tiles by using the [**CustomMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636983).</span></span> <span data-ttu-id="847ed-192">Erstellen Sie Kacheln programmgesteuert im Arbeitsspeicher, oder schreiben Sie eigenen Code, um vorhandene Kacheln aus einer anderen Quelle zu laden.</span><span class="sxs-lookup"><span data-stu-id="847ed-192">Create tiles programmatically in memory on the fly, or write your own code to load existing tiles from another source.</span></span>

<span data-ttu-id="847ed-193">Stellen Sie zum Erstellen oder Laden von benutzerdefinierten Kacheln einen benutzerdefinierten Handler für das [**BitmapRequested**](https://msdn.microsoft.com/library/windows/apps/dn636984)-Ereignis bereit.</span><span class="sxs-lookup"><span data-stu-id="847ed-193">To create or load custom tiles, provide a custom handler for the [**BitmapRequested**](https://msdn.microsoft.com/library/windows/apps/dn636984) event.</span></span> <span data-ttu-id="847ed-194">Das **BitmapRequested**-Ereignis wird für jede einzelne Kachel ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="847ed-194">The **BitmapRequested** event is raised for each individual tile.</span></span>

1.  <span data-ttu-id="847ed-195">Kombinieren Sie in Ihrem benutzerdefinierten Handler für das [**BitmapRequested**](https://msdn.microsoft.com/library/windows/apps/dn636984)-Ereignis die erforderlichen benutzerdefinierten Argumente mit den Eigenschaften [**X**](https://msdn.microsoft.com/library/windows/apps/dn637135), [**Y**](https://msdn.microsoft.com/library/windows/apps/dn637136) und [**ZoomLevel**](https://msdn.microsoft.com/library/windows/apps/dn637137) der [**MapTileBitmapRequestedEventArgs**](https://msdn.microsoft.com/library/windows/apps/dn637132)-Klasse, um eine benutzerdefinierte Kachel zu erstellen oder abzurufen.</span><span class="sxs-lookup"><span data-stu-id="847ed-195">In your custom handler for the [**BitmapRequested**](https://msdn.microsoft.com/library/windows/apps/dn636984) event, combine the required custom arguments with the [**X**](https://msdn.microsoft.com/library/windows/apps/dn637135), [**Y**](https://msdn.microsoft.com/library/windows/apps/dn637136), and [**ZoomLevel**](https://msdn.microsoft.com/library/windows/apps/dn637137) properties of the [**MapTileBitmapRequestedEventArgs**](https://msdn.microsoft.com/library/windows/apps/dn637132) to create or retrieve a custom tile.</span></span>
2.  <span data-ttu-id="847ed-196">Geben Sie die benutzerdefinierte Kachel in der [**PixelData**](https://msdn.microsoft.com/library/windows/apps/dn637140)-Eigenschaft der [**MapTileBitmapRequest**](https://msdn.microsoft.com/library/windows/apps/dn637128)-Klasse zurück, die in der [**Request**](https://msdn.microsoft.com/library/windows/apps/dn637134)-Eigenschaft der [**MapTileBitmapRequestedEventArgs**](https://msdn.microsoft.com/library/windows/apps/dn637132)-Klasse enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="847ed-196">Return the custom tile in the [**PixelData**](https://msdn.microsoft.com/library/windows/apps/dn637140) property of the [**MapTileBitmapRequest**](https://msdn.microsoft.com/library/windows/apps/dn637128), which is contained in the [**Request**](https://msdn.microsoft.com/library/windows/apps/dn637134) property of the [**MapTileBitmapRequestedEventArgs**](https://msdn.microsoft.com/library/windows/apps/dn637132).</span></span> <span data-ttu-id="847ed-197">Bei der **PixelData**-Eigenschaft handelt es sich um den Typ [**IRandomAccessStreamReference**](https://msdn.microsoft.com/library/windows/apps/hh701664).</span><span class="sxs-lookup"><span data-stu-id="847ed-197">The **PixelData** property is of type [**IRandomAccessStreamReference**](https://msdn.microsoft.com/library/windows/apps/hh701664).</span></span>

<span data-ttu-id="847ed-198">Das folgende Beispiel zeigt, wie Sie benutzerdefinierte Kacheln durch Erstellen eines benutzerdefinierten Handlers für das **BitmapRequested**-Ereignis bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="847ed-198">The following example shows how to provide custom tiles by creating a custom handler for the **BitmapRequested** event.</span></span> <span data-ttu-id="847ed-199">In diesem Beispiel werden identische rote Kacheln erstellt, die teilweise deckend sind.</span><span class="sxs-lookup"><span data-stu-id="847ed-199">This example creates identical red tiles that are partially opaque.</span></span> <span data-ttu-id="847ed-200">Im Beispiel werden die Eigenschaften [**X**](https://msdn.microsoft.com/library/windows/apps/dn637135), [**Y**](https://msdn.microsoft.com/library/windows/apps/dn637136) und [**ZoomLevel**](https://msdn.microsoft.com/library/windows/apps/dn637137) der [**MapTileBitmapRequestedEventArgs**](https://msdn.microsoft.com/library/windows/apps/dn637132)-Klasse ignoriert.</span><span class="sxs-lookup"><span data-stu-id="847ed-200">The example ignores the [**X**](https://msdn.microsoft.com/library/windows/apps/dn637135), [**Y**](https://msdn.microsoft.com/library/windows/apps/dn637136), and [**ZoomLevel**](https://msdn.microsoft.com/library/windows/apps/dn637137) properties of the [**MapTileBitmapRequestedEventArgs**](https://msdn.microsoft.com/library/windows/apps/dn637132).</span></span> <span data-ttu-id="847ed-201">Auch wenn dies kein praktisches Beispiel ist, wird im Beispiel veranschaulicht, wie Sie benutzerdefinierte Kacheln im Arbeitsspeicher erstellen können.</span><span class="sxs-lookup"><span data-stu-id="847ed-201">Although this is not a real world example, the example demonstrates how you can create in-memory custom tiles on the fly.</span></span> <span data-ttu-id="847ed-202">Sie erfahren zudem, wie Sie das Verzögerungsmuster implementieren, wenn Sie asynchron zum Erstellen der benutzerdefinierten Kacheln weitere Schritte ausführen müssen.</span><span class="sxs-lookup"><span data-stu-id="847ed-202">The example also shows how to implement the deferral pattern if you have to do something asynchronously to create the custom tiles.</span></span>

```csharp
using Windows.UI.Xaml.Controls.Maps;
using Windows.Storage.Streams;
using System.Threading.Tasks;
...
        CustomMapTileDataSource customDataSource = new CustomMapTileDataSource();
        // Attach a handler for the BitmapRequested event.
        customDataSource.BitmapRequested += customDataSource_BitmapRequestedAsync;
        customTileSource = new MapTileSource(customDataSource);
        MapControl1.TileSources.Add(customTileSource);
...
        // Handle the BitmapRequested event.
        private async void customDataSource_BitmapRequestedAsync(
            CustomMapTileDataSource sender,
            MapTileBitmapRequestedEventArgs args)
        {
            var deferral = args.Request.GetDeferral();
            args.Request.PixelData = await CreateBitmapAsStreamAsync();
            deferral.Complete();
        }

        // Create the custom tiles.
        // This example creates red tiles that are partially opaque.
        private async Task<RandomAccessStreamReference> CreateBitmapAsStreamAsync()
        {
            int pixelHeight = 256;
            int pixelWidth = 256;
            int bpp = 4;

            byte[] bytes = new byte[pixelHeight * pixelWidth * bpp];

            for (int y = 0; y < pixelHeight; y++)
            {
                for (int x = 0; x < pixelWidth; x++)
                {
                    int pixelIndex = y * pixelWidth + x;
                    int byteIndex = pixelIndex * bpp;

                    // Set the current pixel bytes.
                    bytes[byteIndex] = 0xff;        // Red
                    bytes[byteIndex + 1] = 0x00;    // Green
                    bytes[byteIndex + 2] = 0x00;    // Blue
                    bytes[byteIndex + 3] = 0x80;    // Alpha (0xff = fully opaque)
                }
            }

            // Create RandomAccessStream from byte array.
            InMemoryRandomAccessStream randomAccessStream =
                new InMemoryRandomAccessStream();
            IOutputStream outputStream = randomAccessStream.GetOutputStreamAt(0);
            DataWriter writer = new DataWriter(outputStream);
            writer.WriteBytes(bytes);
            await writer.StoreAsync();
            await writer.FlushAsync();
            return RandomAccessStreamReference.CreateFromStream(randomAccessStream);
        }
```

```cppwinrt
...
#include <winrt/Windows.Storage.Streams.h>
...
Windows::Foundation::IAsyncOperation<Windows::Storage::Streams::InMemoryRandomAccessStream> MainPage::CustomRandomAccessStream()
{
    constexpr int pixelHeight{ 256 };
    constexpr int pixelWidth{ 256 };
    constexpr int bpp{ 4 };

    std::array<uint8_t, pixelHeight * pixelWidth * bpp> bytes;

    for (int y = 0; y < pixelHeight; y++)
    {
        for (int x = 0; x < pixelWidth; x++)
        {
            int pixelIndex{ y * pixelWidth + x };
            int byteIndex{ pixelIndex * bpp };

            // Set the current pixel bytes.
            bytes[byteIndex] = (byte)(std::rand() % 256);        // Red
            bytes[byteIndex + 1] = (byte)(std::rand() % 256);    // Green
            bytes[byteIndex + 2] = (byte)(std::rand() % 256);    // Blue
            bytes[byteIndex + 3] = (byte)((std::rand() % 56) + 200);    // Alpha (0xff = fully opaque)
        }
    }

    // Create RandomAccessStream from byte array.
    Windows::Storage::Streams::InMemoryRandomAccessStream randomAccessStream;
    Windows::Storage::Streams::IOutputStream outputStream{ randomAccessStream.GetOutputStreamAt(0) };
    Windows::Storage::Streams::DataWriter writer{ outputStream };
    writer.WriteBytes(bytes);

    co_await writer.StoreAsync();
    co_await writer.FlushAsync();

    co_return randomAccessStream;
}
...
```

```cpp
InMemoryRandomAccessStream^ TileSources::CustomRandomAccessStream::get()
{
    int pixelHeight = 256;
    int pixelWidth = 256;
    int bpp = 4;

    Array<byte>^ bytes = ref new Array<byte>(pixelHeight * pixelWidth * bpp);

    for (int y = 0; y < pixelHeight; y++)
    {
        for (int x = 0; x < pixelWidth; x++)
        {
            int pixelIndex = y * pixelWidth + x;
            int byteIndex = pixelIndex * bpp;

            // Set the current pixel bytes.
            bytes[byteIndex] = (byte)(std::rand() % 256);        // Red
            bytes[byteIndex + 1] = (byte)(std::rand() % 256);    // Green
            bytes[byteIndex + 2] = (byte)(std::rand() % 256);    // Blue
            bytes[byteIndex + 3] = (byte)((std::rand() % 56) + 200);    // Alpha (0xff = fully opaque)
        }
    }

    // Create RandomAccessStream from byte array.
    InMemoryRandomAccessStream^ randomAccessStream = ref new InMemoryRandomAccessStream();
    IOutputStream^ outputStream = randomAccessStream->GetOutputStreamAt(0);
    DataWriter^ writer = ref new DataWriter(outputStream);
    writer->WriteBytes(bytes);

    create_task(writer->StoreAsync()).then([writer](unsigned int)
    {
        create_task(writer->FlushAsync());
    });

    return randomAccessStream;
}
```

## <a name="replace-the-default-map"></a><span data-ttu-id="847ed-203">Ersetzen der Standardkarte</span><span class="sxs-lookup"><span data-stu-id="847ed-203">Replace the default map</span></span>

<span data-ttu-id="847ed-204">So ersetzen Sie die Standardkarte durch Drittanbieter- oder benutzerdefinierte Kacheln:</span><span class="sxs-lookup"><span data-stu-id="847ed-204">To replace the default map entirely with third-party or custom tiles:</span></span>

-   <span data-ttu-id="847ed-205">Legen Sie [**MapTileLayer**](https://msdn.microsoft.com/library/windows/apps/dn637143).**BackgroundReplacement** als Wert für die [**Layer**](https://msdn.microsoft.com/library/windows/apps/dn637157)-Eigenschaft der [**MapTileSource**](https://msdn.microsoft.com/library/windows/apps/dn637144)-Klasse fest.</span><span class="sxs-lookup"><span data-stu-id="847ed-205">Specify [**MapTileLayer**](https://msdn.microsoft.com/library/windows/apps/dn637143).**BackgroundReplacement** as the value of the [**Layer**](https://msdn.microsoft.com/library/windows/apps/dn637157) property of the [**MapTileSource**](https://msdn.microsoft.com/library/windows/apps/dn637144).</span></span>
-   <span data-ttu-id="847ed-206">Legen Sie [**MapStyle**](https://msdn.microsoft.com/library/windows/apps/dn637127).**None** als Wert für die [**Style**](https://msdn.microsoft.com/library/windows/apps/dn637051)-Eigenschaft der [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004)-Klasse fest.</span><span class="sxs-lookup"><span data-stu-id="847ed-206">Specify [**MapStyle**](https://msdn.microsoft.com/library/windows/apps/dn637127).**None** as the value of the [**Style**](https://msdn.microsoft.com/library/windows/apps/dn637051) property of the [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004).</span></span>

## <a name="related-topics"></a><span data-ttu-id="847ed-207">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="847ed-207">Related topics</span></span>

* [<span data-ttu-id="847ed-208">Bing Maps Developer Center</span><span class="sxs-lookup"><span data-stu-id="847ed-208">Bing Maps Developer Center</span></span>](https://www.bingmapsportal.com/)
* [<span data-ttu-id="847ed-209">Beispiel für UWP-Karte</span><span class="sxs-lookup"><span data-stu-id="847ed-209">UWP map sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=619977)
* [<span data-ttu-id="847ed-210">Entwurfsrichtlinien für Karten</span><span class="sxs-lookup"><span data-stu-id="847ed-210">Design guidelines for maps</span></span>](https://msdn.microsoft.com/library/windows/apps/dn596102)
* [<span data-ttu-id="847ed-211">Build 2015-Video: Nutzen von Karten und Ortung über Telefon, Tablet und PC in Ihren Windows-Apps</span><span class="sxs-lookup"><span data-stu-id="847ed-211">Build 2015 video: Leveraging Maps and Location Across Phone, Tablet, and PC in Your Windows Apps</span></span>](https://channel9.msdn.com/Events/Build/2015/2-757)
* [<span data-ttu-id="847ed-212">Beispiel für eine UWP-App mit Verkehrsinformationen</span><span class="sxs-lookup"><span data-stu-id="847ed-212">UWP traffic app sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=619982)
