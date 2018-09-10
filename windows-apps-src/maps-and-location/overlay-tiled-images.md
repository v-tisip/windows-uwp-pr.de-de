---
author: normesta
title: Überlagern von nebeneinander angeordneten Bildern in einer Karte
description: Überlagern Sie Bilder von Drittanbietern oder benutzerdefinierte nebeneinander angeordnete Bilder in einer Karte mithilfe von Kachelquellen. Verwenden Sie Kachelquellen, um spezielle Infos wie Wetterdaten, Einwohnerzahlen oder seismische Daten zu überlagern oder die Standardkarte vollständig zu ersetzen.
ms.assetid: 066BD6E2-C22B-4F5B-AA94-5D6C86A09BDF
ms.author: normesta
ms.date: 07/19/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Karte, Standort, Bilder, Überlagerung
ms.localizationpriority: medium
ms.openlocfilehash: ba1f7d52a1b16fbb421202229ce724dab384ffa0
ms.sourcegitcommit: f5cf806a595969ecbb018c3f7eea86c7a34940f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "3821144"
---
# <a name="overlay-tiled-images-on-a-map"></a><span data-ttu-id="ab5e6-105">Überlagern von nebeneinander angeordneten Bildern in einer Karte</span><span class="sxs-lookup"><span data-stu-id="ab5e6-105">Overlay tiled images on a map</span></span>

<span data-ttu-id="ab5e6-106">Überlagern Sie Bilder von Drittanbietern oder benutzerdefinierte nebeneinander angeordnete Bilder in einer Karte mithilfe von Kachelquellen.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-106">Overlay third-party or custom tiled images on a map by using tile sources.</span></span> <span data-ttu-id="ab5e6-107">Verwenden Sie Kachelquellen, um spezielle Infos wie Wetterdaten, Einwohnerzahlen oder seismische Daten zu überlagern oder die Standardkarte vollständig zu ersetzen.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-107">Use tile sources to overlay specialized information such as weather data, population data, or seismic data; or use tile sources to replace the default map entirely.</span></span>

<span data-ttu-id="ab5e6-108">**Tipp**: Laden Sie das [Kartenbeispiel für die Universelle Windows-Plattform (UWP)](http://go.microsoft.com/fwlink/p/?LinkId=619977) auf Github herunter, um mehr über die Verwendung von Karten in Ihrer App zu erfahren.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-108">**Tip** To learn more about using maps in your app, download the [Universal Windows Platform (UWP) map sample](http://go.microsoft.com/fwlink/p/?LinkId=619977) on Github.</span></span>

<a id="tileintro" />

## <a name="tiled-image-overview"></a><span data-ttu-id="ab5e6-109">Übersicht über nebeneinander angeordnete Bilder</span><span class="sxs-lookup"><span data-stu-id="ab5e6-109">Tiled image overview</span></span>

<span data-ttu-id="ab5e6-110">Kartendienste wie Nokia Karten und Bing Maps teilen Karten zum schnellen Abrufen und Anzeigen in quadratische Kacheln ein.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-110">Map services such as Nokia Maps and Bing Maps cut maps into square tiles for quick retrieval and display.</span></span> <span data-ttu-id="ab5e6-111">Diese Kacheln messen 256 x 256 Pixel und werden vorab auf mehrere Detailebenen gerendert.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-111">These tiles are 256 pixels by 256 pixels in size, and are pre-rendered at multiple levels of detail.</span></span> <span data-ttu-id="ab5e6-112">Viele Dienste von Drittanbietern umfassen auch kartenbasierte Daten, die in Kacheln aufgeteilt sind.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-112">Many third-party services also provide map-based data that's cut into tiles.</span></span> <span data-ttu-id="ab5e6-113">Verwenden Sie Kachelquellen, um Kacheln von Drittanbietern abzurufen oder benutzerdefinierte Kacheln zu erstellen. Überlagern Sie diese auf der angezeigten Karte im [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-113">Use tile sources to retrieve third-party tiles, or to create your own custom tiles, and overlay them on the map displayed in the [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004).</span></span>

**<span data-ttu-id="ab5e6-114">Wichtig</span><span class="sxs-lookup"><span data-stu-id="ab5e6-114">Important</span></span>**  
<span data-ttu-id="ab5e6-115">Wenn Sie Kachelquellen verwenden, müssen Sie keinen Code schreiben, um einzelne Kacheln anzufordern oder zu positionieren.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-115">When you use tile sources, you don't have to write code to request or to position individual tiles.</span></span> <span data-ttu-id="ab5e6-116">Das [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004)-Objekt fordert bei Bedarf Kacheln an.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-116">The [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004) requests tiles as it needs them.</span></span> <span data-ttu-id="ab5e6-117">Bei jeder Anforderung werden die X- und Y-Koordinaten und der Zoomfaktor für die einzelnen Kacheln angegeben.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-117">Each request specifies the X and Y coordinates and the zoom level for the individual tile.</span></span> <span data-ttu-id="ab5e6-118">Geben Sie einfach das Format des URIs oder Dateinamens an, um die Kacheln in der **UriFormatString**-Eigenschaft abzurufen.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-118">You simply specify the format of the Uri or filename to use to retrieve the tiles in the **UriFormatString** property.</span></span> <span data-ttu-id="ab5e6-119">Dazu fügen Sie ersetzbare Parameter in den Basis-URI oder Dateinamen ein, um anzugeben, wo die X- und Y-Koordinaten und der Zoomfaktor für jede Kachel übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-119">That is, you insert replaceable parameters in the base Uri or filename to indicate where to pass the X and Y coordinates and the zoom level for each tile.</span></span>

<span data-ttu-id="ab5e6-120">In diesem Beispiel sehen Sie eine [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636992)-Eigenschaft für eine [**HttpMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636986)-Klasse. Diese zeigt die ersetzbaren Parameter für die X- und Y-Koordinaten und den Zoomfaktor an.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-120">Here's an example of the [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636992) property for an [**HttpMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636986) that shows the replaceable parameters for the X and Y coordinates and the zoom level.</span></span>

```syntax
http://www.<web service name>.com/z={zoomlevel}&x={x}&y={y}
```

<span data-ttu-id="ab5e6-121">(Die X- und Y-Koordinaten stellen die Position der einzelnen Kachel in der Zuordnung der Weltkarte auf der angegebenen Detailebene dar.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-121">(The X and Y coordinates represent the location of the individual tile within the map of the world at the specified level of detail.</span></span> <span data-ttu-id="ab5e6-122">Die Nummerierung der Kachel beginnt bei {0, 0} in der oberen linken Ecke der Karte.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-122">The tile numbering system starts from {0, 0} in the upper left corner of the map.</span></span> <span data-ttu-id="ab5e6-123">Die Kachel bei {1, 2} befindet sich beispielsweise in der zweiten Spalte der dritten Zeile des Kachelrasters.)</span><span class="sxs-lookup"><span data-stu-id="ab5e6-123">For example, the tile at {1, 2} is in the second column of the third row of the grid of tiles.)</span></span>

<span data-ttu-id="ab5e6-124">Weitere Informationen über das Kachelsystem von Kartendiensten finden Sie unter [Kachelsystem von Bing Maps](http://go.microsoft.com/fwlink/p/?LinkId=626692).</span><span class="sxs-lookup"><span data-stu-id="ab5e6-124">For more info about the tile system used by mapping services, see [Bing Maps Tile System](http://go.microsoft.com/fwlink/p/?LinkId=626692).</span></span>

### <a name="overlay-tiles-from-a-tile-source"></a><span data-ttu-id="ab5e6-125">Überlagern von Kacheln aus einer Kachelquelle</span><span class="sxs-lookup"><span data-stu-id="ab5e6-125">Overlay tiles from a tile source</span></span>

<span data-ttu-id="ab5e6-126">Überlagern Sie nebeneinander angeordnete Bilder aus einer Kachelquelle in einer Karte mithilfe der [**MapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn637141)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-126">Overlay tiled images from a tile source on a map by using the [**MapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn637141).</span></span>

1.  <span data-ttu-id="ab5e6-127">Instanziieren Sie eine der drei Klassen für Kacheldatenquellen, die von der [**MapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn637141)-Klasse erben.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-127">Instantiate one of the three tile data source classes that inherit from [**MapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn637141).</span></span>

    -   [**<span data-ttu-id="ab5e6-128">HttpMapTileDataSource</span><span class="sxs-lookup"><span data-stu-id="ab5e6-128">HttpMapTileDataSource</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn636986)
    -   [**<span data-ttu-id="ab5e6-129">LocalMapTileDataSource</span><span class="sxs-lookup"><span data-stu-id="ab5e6-129">LocalMapTileDataSource</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn636994)
    -   [**<span data-ttu-id="ab5e6-130">CustomMapTileDataSource</span><span class="sxs-lookup"><span data-stu-id="ab5e6-130">CustomMapTileDataSource</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn636983)

    <span data-ttu-id="ab5e6-131">Konfigurieren Sie die **UriFormatString**-Eigenschaft zum Anfordern der Kacheln, indem Sie ersetzbare Parameter im Basis-URI oder Dateinamen einfügen.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-131">Configure the **UriFormatString** to use to request the tiles by inserting replaceable parameters in the base Uri or filename.</span></span>

    <span data-ttu-id="ab5e6-132">Im folgenden Beispiel wird eine [**HttpMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636986)-Klasse instanziiert.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-132">The following example instantiates an [**HttpMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636986).</span></span> <span data-ttu-id="ab5e6-133">In diesem Beispiel wird der Wert der [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636992)-Eigenschaft im Konstruktor der **HttpMapTileDataSource**-Klasse veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-133">This example specifies the value of the [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636992) in the constructor of the **HttpMapTileDataSource**.</span></span>

    ```csharp
        HttpMapTileDataSource dataSource = new HttpMapTileDataSource(
          "http://www.<web service name>.com/z={zoomlevel}&x={x}&y={y}");
    ```

2.  <span data-ttu-id="ab5e6-134">Instanziieren und konfigurieren Sie eine [**MapTileSource**](https://msdn.microsoft.com/library/windows/apps/dn637144)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-134">Instantiate and configure a [**MapTileSource**](https://msdn.microsoft.com/library/windows/apps/dn637144).</span></span> <span data-ttu-id="ab5e6-135">Geben Sie die [**MapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn637141)-Klasse an, die Sie im vorherigen Schritt als [**DataSource**](https://msdn.microsoft.com/library/windows/apps/dn637149)-Eigenschaft der **MapTileSource**-Klasse festgelegt haben.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-135">Specify the [**MapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn637141) that you configured in the previous step as the [**DataSource**](https://msdn.microsoft.com/library/windows/apps/dn637149) of the **MapTileSource**.</span></span>

    <span data-ttu-id="ab5e6-136">Im folgenden Beispiel wird die [**DataSource**](https://msdn.microsoft.com/library/windows/apps/dn637149)-Eigenschaft im Konstruktor der [**MapTileSource**](https://msdn.microsoft.com/library/windows/apps/dn637144)-Klasse veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-136">The following example specifies the [**DataSource**](https://msdn.microsoft.com/library/windows/apps/dn637149) in the constructor of the [**MapTileSource**](https://msdn.microsoft.com/library/windows/apps/dn637144).</span></span>

    ```csharp
        MapTileSource tileSource = new MapTileSource(dataSource);
    ```

    <span data-ttu-id="ab5e6-137">Sie können die Bedingungen, unter denen Kacheln angezeigt werden, mithilfe der Eigenschaften der [**MapTileSource**](https://msdn.microsoft.com/library/windows/apps/dn637144)-Klasse einschränken.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-137">You can restrict the conditions in which the tiles are displayed by using properties of the [**MapTileSource**](https://msdn.microsoft.com/library/windows/apps/dn637144).</span></span>

    -   <span data-ttu-id="ab5e6-138">Zeigen Sie Kacheln nur in einem bestimmten geografischen Bereich an, indem Sie einen Wert für die [**Bounds**](https://msdn.microsoft.com/library/windows/apps/dn637147)-Eigenschaft angeben.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-138">Display tiles only within a specific geographic area by providing a value for the [**Bounds**](https://msdn.microsoft.com/library/windows/apps/dn637147) property.</span></span>
    -   <span data-ttu-id="ab5e6-139">Zeigen Sie Kacheln nur auf bestimmten Detailebenen an, indem Sie einen Wert für die [**ZoomLevelRange**](https://msdn.microsoft.com/library/windows/apps/dn637171)-Eigenschaft angeben.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-139">Display tiles only at certain levels of detail by providing a value for the [**ZoomLevelRange**](https://msdn.microsoft.com/library/windows/apps/dn637171) property.</span></span>

    <span data-ttu-id="ab5e6-140">Optional können Sie weitere Eigenschaften der [**MapTileSource**](https://msdn.microsoft.com/library/windows/apps/dn637144)-Klasse konfigurieren, die Auswirkungen auf das Laden oder die Anzeige von Kacheln haben, z. B. [**Layer**](https://msdn.microsoft.com/library/windows/apps/dn637157), [**AllowOverstretch**](https://msdn.microsoft.com/library/windows/apps/dn637145), [**IsRetryEnabled**](https://msdn.microsoft.com/library/windows/apps/dn637153) und [**IsTransparencyEnabled**](https://msdn.microsoft.com/library/windows/apps/dn637155).</span><span class="sxs-lookup"><span data-stu-id="ab5e6-140">Optionally, configure other properties of the [**MapTileSource**](https://msdn.microsoft.com/library/windows/apps/dn637144) that affect the loading or the display of the tiles, such as [**Layer**](https://msdn.microsoft.com/library/windows/apps/dn637157), [**AllowOverstretch**](https://msdn.microsoft.com/library/windows/apps/dn637145), [**IsRetryEnabled**](https://msdn.microsoft.com/library/windows/apps/dn637153), and [**IsTransparencyEnabled**](https://msdn.microsoft.com/library/windows/apps/dn637155).</span></span>

3.  <span data-ttu-id="ab5e6-141">Fügen Sie die [**MapTileSource**](https://msdn.microsoft.com/library/windows/apps/dn637144)-Klasse der [**TileSources**](https://msdn.microsoft.com/library/windows/apps/dn637053)-Collection dem [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004)-Objekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-141">Add the [**MapTileSource**](https://msdn.microsoft.com/library/windows/apps/dn637144) to the [**TileSources**](https://msdn.microsoft.com/library/windows/apps/dn637053) collection of the [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004).</span></span>

    ```csharp
         MapControl1.TileSources.Add(tileSource);
    ```

## <a name="overlay-tiles-from-a-web-service"></a><span data-ttu-id="ab5e6-142">Überlagern von Kacheln aus einem Webdienst</span><span class="sxs-lookup"><span data-stu-id="ab5e6-142">Overlay tiles from a web service</span></span>


<span data-ttu-id="ab5e6-143">Überlagern Sie nebeneinander angeordnete Bilder aus einem Webdienst mithilfe der [**HttpMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636986)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-143">Overlay tiled images retrieved from a web service by using the [**HttpMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636986).</span></span>

1.  <span data-ttu-id="ab5e6-144">Instanziieren Sie eine [**HttpMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636986)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-144">Instantiate an [**HttpMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636986).</span></span>
2.  <span data-ttu-id="ab5e6-145">Geben Sie das Format des URIs an, den der Webdienst als Wert für die [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636992)-Eigenschaft erwartet.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-145">Specify the format of the Uri that the web service expects as the value of the [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636992) property.</span></span> <span data-ttu-id="ab5e6-146">Um diesen Wert zu erstellen, fügen Sie dem Basis-URI die ersetzbaren Parameter hinzu.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-146">To create this value, insert replaceable parameters in the base Uri.</span></span> <span data-ttu-id="ab5e6-147">Im folgenden Codebeispiel beträgt der Wert der **UriFormatString**-Eigenschaft beispielsweise:</span><span class="sxs-lookup"><span data-stu-id="ab5e6-147">For example, in the following code sample, the value of the **UriFormatString** is:</span></span>

    ``` syntax
    http://www.<web service name>.com/z={zoomlevel}&x={x}&y={y}
    ```

    <span data-ttu-id="ab5e6-148">Der Webdienst muss einen URI unterstützen, der die ersetzbaren Parameter {x}, {y} und {zoomlevel} enthält.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-148">The web service has to support a Uri that contains the replaceable parameters {x}, {y}, and {zoomlevel}.</span></span> <span data-ttu-id="ab5e6-149">Die meisten Webdienste (z.B. Nokia, Bing und Google) unterstützen URIs in diesem Format.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-149">Most web services (for example, Nokia, Bing, and Google) support Uris in this format.</span></span> <span data-ttu-id="ab5e6-150">Benötigt der Webdienst zusätzliche Argumente, die mit der [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636992)-Eigenschaft nicht zur Verfügung stehen, müssen Sie einen benutzerdefinierten URI erstellen.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-150">If the web service requires additional arguments that aren't available with the [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636992) property, then you have to create a custom Uri.</span></span> <span data-ttu-id="ab5e6-151">Mithilfe des [**UriRequested**](https://msdn.microsoft.com/library/windows/apps/dn636993)-Ereignisses können Sie einen benutzerdefinierten URI erstellen und zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-151">Create and return a custom Uri by handling the [**UriRequested**](https://msdn.microsoft.com/library/windows/apps/dn636993) event.</span></span> <span data-ttu-id="ab5e6-152">Weitere Infos finden Sie im Abschnitt [Bereitstellen eines benutzerdefinierten URIs](#customuri) weiter unten in diesem Thema.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-152">For more info, see the [Provide a custom URI](#customuri) section later in this topic.</span></span>

3.  <span data-ttu-id="ab5e6-153">Befolgen Sie die verbleibenden Schritte in der [Übersicht über nebeneinander angeordnete Bilder](#tileintro).</span><span class="sxs-lookup"><span data-stu-id="ab5e6-153">Then, follow the remaining steps described previously in the [Tiled image overview](#tileintro).</span></span>

<span data-ttu-id="ab5e6-154">Im folgenden Beispiel überlagern Kacheln aus einem fiktiven Webdienst eine Karte von Nordamerika.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-154">The following example overlays tiles from a fictitious web service on a map of North America.</span></span> <span data-ttu-id="ab5e6-155">Der Wert der [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636992)-Eigenschaft ist im Konstruktor der [**HttpMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636986)-Klasse angegeben.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-155">The value of the [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636992) is specified in the constructor of the [**HttpMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636986).</span></span> <span data-ttu-id="ab5e6-156">In diesem Beispiel werden durch Festlegen der optionalen [**Bounds**](https://msdn.microsoft.com/library/windows/apps/dn637147)-Eigenschaft nur Kacheln innerhalb der geografischen Bereiche angegeben.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-156">In this example, tiles are only displayed within the geographic boundaries specified by the optional [**Bounds**](https://msdn.microsoft.com/library/windows/apps/dn637147) property.</span></span>

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

## <a name="overlay-tiles-from-local-storage"></a><span data-ttu-id="ab5e6-157">Überlagern von Kacheln aus dem lokalen Speicher</span><span class="sxs-lookup"><span data-stu-id="ab5e6-157">Overlay tiles from local storage</span></span>


<span data-ttu-id="ab5e6-158">Überlagern Sie nebeneinander angeordnete Bilder, die als Dateien im lokalen Speicher gespeichert sind, mithilfe der [**LocalMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636994)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-158">Overlay tiled images stored as files in local storage by using the [**LocalMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636994).</span></span> <span data-ttu-id="ab5e6-159">In der Regel können Sie diese Dateien mit Ihrer App verpacken und verteilen.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-159">Typically, you package and distribute these files with your app.</span></span>

1.  <span data-ttu-id="ab5e6-160">Instanziieren Sie eine [**LocalMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636994)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-160">Instantiate a [**LocalMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636994).</span></span>
2.  <span data-ttu-id="ab5e6-161">Geben Sie das Format der Dateinamen als Wert für die [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636998)-Eigenschaft ein.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-161">Specify the format of the file names as the value of the [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636998) property.</span></span> <span data-ttu-id="ab5e6-162">Um diesen Wert zu erstellen, fügen Sie dem Basis-Dateinamen die ersetzbaren Parameter hinzu.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-162">To create this value, insert replaceable parameters in the base filename.</span></span> <span data-ttu-id="ab5e6-163">Im folgenden Codebeispiel hat die [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636992)-Eigenschaft beispielsweise den Wert:</span><span class="sxs-lookup"><span data-stu-id="ab5e6-163">For example, in the following code sample, the value of the [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636992) is:</span></span>

    ``` syntax
        Tile_{zoomlevel}_{x}_{y}.png
    ```

    <span data-ttu-id="ab5e6-164">Wenn das Format der Dateinamen zusätzliche Argumente benötigt, die mit der [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636998)-Eigenschaft nicht zur Verfügung stehen, müssen Sie einen benutzerdefinierten URI erstellen.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-164">If the format of the file names requires additional arguments that aren't available with the [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636998) property, then you have to create a custom Uri.</span></span> <span data-ttu-id="ab5e6-165">Mithilfe des [**UriRequested**](https://msdn.microsoft.com/library/windows/apps/dn637001)-Ereignisses können Sie einen benutzerdefinierten URI erstellen und zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-165">Create and return a custom Uri by handling the [**UriRequested**](https://msdn.microsoft.com/library/windows/apps/dn637001) event.</span></span> <span data-ttu-id="ab5e6-166">Weitere Infos finden Sie im Abschnitt [Bereitstellen eines benutzerdefinierten URIs](#customuri) weiter unten in diesem Thema.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-166">For more info, see the [Provide a custom URI](#customuri) section later in this topic.</span></span>

3.  <span data-ttu-id="ab5e6-167">Befolgen Sie die verbleibenden Schritte in der [Übersicht über nebeneinander angeordnete Bilder](#tileintro).</span><span class="sxs-lookup"><span data-stu-id="ab5e6-167">Then, follow the remaining steps described previously in the [Tiled image overview](#tileintro).</span></span>

<span data-ttu-id="ab5e6-168">Zum Laden von Kacheln aus dem lokalen Speicher können Sie die folgenden Protokolle und Speicherorte verwenden:</span><span class="sxs-lookup"><span data-stu-id="ab5e6-168">You can use the following protocols and locations to load tiles from local storage:</span></span>

| <span data-ttu-id="ab5e6-169">URI</span><span class="sxs-lookup"><span data-stu-id="ab5e6-169">Uri</span></span> | <span data-ttu-id="ab5e6-170">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="ab5e6-170">More info</span></span> |
|---------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="ab5e6-171">ms-appx:///</span><span class="sxs-lookup"><span data-stu-id="ab5e6-171">ms-appx:///</span></span> | <span data-ttu-id="ab5e6-172">Verweist auf das Stammelement des App-Installationsordners.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-172">Points to the root of the app's installation folder.</span></span> |
|  | <span data-ttu-id="ab5e6-173">Dies ist der von der [Package.InstalledLocation](https://msdn.microsoft.com/library/windows/apps/br224681)-Eigenschaft referenzierte Speicherort.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-173">This is the location referenced by the [Package.InstalledLocation](https://msdn.microsoft.com/library/windows/apps/br224681) property.</span></span> |
| <span data-ttu-id="ab5e6-174">ms-appdata:///local</span><span class="sxs-lookup"><span data-stu-id="ab5e6-174">ms-appdata:///local</span></span> | <span data-ttu-id="ab5e6-175">Verweist auf das Stammelement des lokalen Speichers der App.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-175">Points to the root of the app's local storage.</span></span> |
|  | <span data-ttu-id="ab5e6-176">Dies ist der von der [ApplicationData.LocalFolder](https://msdn.microsoft.com/library/windows/apps/br241621)-Eigenschaft referenzierte Speicherort.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-176">This is the location referenced by the [ApplicationData.LocalFolder](https://msdn.microsoft.com/library/windows/apps/br241621) property.</span></span> |
| <span data-ttu-id="ab5e6-177">ms-appdata:///temp</span><span class="sxs-lookup"><span data-stu-id="ab5e6-177">ms-appdata:///temp</span></span> | <span data-ttu-id="ab5e6-178">Verweist auf die temporären Ordner der App.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-178">Points to the app's temp folder.</span></span> |
|  | <span data-ttu-id="ab5e6-179">Dies ist der Pfad, auf den die [ApplicationData.TemporaryFolder](https://msdn.microsoft.com/library/windows/apps/br241629)-Eigenschaft verweist.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-179">This is the location referenced by the [ApplicationData.TemporaryFolder](https://msdn.microsoft.com/library/windows/apps/br241629) property.</span></span> |

 

<span data-ttu-id="ab5e6-180">Im folgenden Beispiel werden Kacheln, die als Dateien im Installationsverzeichnis der App gespeichert werden, mithilfe des `ms-appx:///`-Protokolls geladen.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-180">The following example loads tiles that are stored as files in the app's installation folder by using the `ms-appx:///` protocol.</span></span> <span data-ttu-id="ab5e6-181">Der Wert der [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636998)-Eigenschaft ist im Konstruktor der [**LocalMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636994)-Klasse angegeben.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-181">The value for the [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636998) is specified in the constructor of the [**LocalMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636994).</span></span> <span data-ttu-id="ab5e6-182">In diesem Beispiel werden Kacheln nur angezeigt, wenn der Zoomfaktor für die Karte innerhalb des Bereichs liegt, der durch die optionale [**ZoomLevelRange**](https://msdn.microsoft.com/library/windows/apps/dn637171)-Eigenschaft angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-182">In this example, tiles are only displayed when the zoom level of the map is within the range specified by the optional [**ZoomLevelRange**](https://msdn.microsoft.com/library/windows/apps/dn637171) property.</span></span>

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

## <a name="provide-a-custom-uri"></a><span data-ttu-id="ab5e6-183">Bereitstellen eines benutzerdefinierten URIs</span><span class="sxs-lookup"><span data-stu-id="ab5e6-183">Provide a custom URI</span></span>

<span data-ttu-id="ab5e6-184">Wenn die ersetzbaren Parameter, die mit der [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636992)-Eigenschaft der [**HttpMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636986)-Klasse oder der [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636998)-Eigenschaft der [**LocalMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636994)-Klasse zur Verfügung stehen, nicht zum Abrufen Ihrer Kacheln ausreichen, müssen Sie einen benutzerdefinierten URI erstellen.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-184">If the replaceable parameters available with the [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636992) property of the [**HttpMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636986) or the [**UriFormatString**](https://msdn.microsoft.com/library/windows/apps/dn636998) property of the [**LocalMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636994) aren't sufficient to retrieve your tiles, then you have to create a custom Uri.</span></span> <span data-ttu-id="ab5e6-185">Indem Sie einen benutzerdefinierten Handler für das **UriRequested**-Ereignis bereitstellen, können Sie einen benutzerdefinierten URI erstellen und zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-185">Create and return a custom Uri by providing a custom handler for the **UriRequested** event.</span></span> <span data-ttu-id="ab5e6-186">Das **UriRequested**-Ereignis wird für jede einzelne Kachel ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-186">The **UriRequested** event is raised for each individual tile.</span></span>

1.  <span data-ttu-id="ab5e6-187">Kombinieren Sie in Ihrem benutzerdefinierten Handler für das **UriRequested**-Ereignis die erforderlichen benutzerdefinierten Argumente mit den Eigenschaften [**X**](https://msdn.microsoft.com/library/windows/apps/dn610743), [**Y**](https://msdn.microsoft.com/library/windows/apps/dn610744) und [**ZoomLevel**](https://msdn.microsoft.com/library/windows/apps/dn610745) der [**MapTileUriRequestedEventArgs**](https://msdn.microsoft.com/library/windows/apps/dn637177)-Klasse, um den benutzerdefinierten URI zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-187">In your custom handler for the **UriRequested** event, combine the required custom arguments with the [**X**](https://msdn.microsoft.com/library/windows/apps/dn610743), [**Y**](https://msdn.microsoft.com/library/windows/apps/dn610744), and [**ZoomLevel**](https://msdn.microsoft.com/library/windows/apps/dn610745) properties of the [**MapTileUriRequestedEventArgs**](https://msdn.microsoft.com/library/windows/apps/dn637177) to create the custom Uri.</span></span>
2.  <span data-ttu-id="ab5e6-188">Geben Sie die benutzerdefinierte URI in der [**Uri**](https://msdn.microsoft.com/library/windows/apps/dn610748)-Eigenschaft der [**MapTileUriRequest**](https://msdn.microsoft.com/library/windows/apps/dn637173)-Klasse zurück. Diese ist in der [**Request**](https://msdn.microsoft.com/library/windows/apps/dn637179)-Eigenschaft der [**MapTileUriRequestedEventArgs**](https://msdn.microsoft.com/library/windows/apps/dn637177)-Klasse enthalten.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-188">Return the custom Uri in the [**Uri**](https://msdn.microsoft.com/library/windows/apps/dn610748) property of the [**MapTileUriRequest**](https://msdn.microsoft.com/library/windows/apps/dn637173), which is contained in the [**Request**](https://msdn.microsoft.com/library/windows/apps/dn637179) property of the [**MapTileUriRequestedEventArgs**](https://msdn.microsoft.com/library/windows/apps/dn637177).</span></span>

<span data-ttu-id="ab5e6-189">Das folgende Beispiel zeigt, wie Sie einen benutzerdefinierten URI durch Erstellen eines benutzerdefinierten Handlers für das **UriRequested**-Ereignis bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-189">The following example shows how to provide a custom Uri by creating a custom handler for the **UriRequested** event.</span></span> <span data-ttu-id="ab5e6-190">Sie erfahren zudem, wie Sie das Verzögerungsmuster implementieren, wenn Sie asynchron zum Erstellen des benutzerdefinierten URIs weitere Schritte ausführen müssen.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-190">It also shows how to implement the deferral pattern if you have to do something asynchronously to create the custom Uri.</span></span>

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

## <a name="overlay-tiles-from-a-custom-source"></a><span data-ttu-id="ab5e6-191">Überlagern von Kacheln aus einer benutzerdefinierten Quelle</span><span class="sxs-lookup"><span data-stu-id="ab5e6-191">Overlay tiles from a custom source</span></span>

<span data-ttu-id="ab5e6-192">Überlagern Sie benutzerdefinierte Kacheln mithilfe der [**CustomMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636983)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-192">Overlay custom tiles by using the [**CustomMapTileDataSource**](https://msdn.microsoft.com/library/windows/apps/dn636983).</span></span> <span data-ttu-id="ab5e6-193">Erstellen Sie Kacheln programmgesteuert im Arbeitsspeicher, oder schreiben Sie eigenen Code, um vorhandene Kacheln aus einer anderen Quelle zu laden.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-193">Create tiles programmatically in memory on the fly, or write your own code to load existing tiles from another source.</span></span>

<span data-ttu-id="ab5e6-194">Stellen Sie zum Erstellen oder Laden von benutzerdefinierten Kacheln einen benutzerdefinierten Handler für das [**BitmapRequested**](https://msdn.microsoft.com/library/windows/apps/dn636984)-Ereignis bereit.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-194">To create or load custom tiles, provide a custom handler for the [**BitmapRequested**](https://msdn.microsoft.com/library/windows/apps/dn636984) event.</span></span> <span data-ttu-id="ab5e6-195">Das **BitmapRequested**-Ereignis wird für jede einzelne Kachel ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-195">The **BitmapRequested** event is raised for each individual tile.</span></span>

1.  <span data-ttu-id="ab5e6-196">Kombinieren Sie in Ihrem benutzerdefinierten Handler für das [**BitmapRequested**](https://msdn.microsoft.com/library/windows/apps/dn636984)-Ereignis die erforderlichen benutzerdefinierten Argumente mit den Eigenschaften [**X**](https://msdn.microsoft.com/library/windows/apps/dn637135), [**Y**](https://msdn.microsoft.com/library/windows/apps/dn637136) und [**ZoomLevel**](https://msdn.microsoft.com/library/windows/apps/dn637137) der [**MapTileBitmapRequestedEventArgs**](https://msdn.microsoft.com/library/windows/apps/dn637132)-Klasse, um eine benutzerdefinierte Kachel zu erstellen oder abzurufen.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-196">In your custom handler for the [**BitmapRequested**](https://msdn.microsoft.com/library/windows/apps/dn636984) event, combine the required custom arguments with the [**X**](https://msdn.microsoft.com/library/windows/apps/dn637135), [**Y**](https://msdn.microsoft.com/library/windows/apps/dn637136), and [**ZoomLevel**](https://msdn.microsoft.com/library/windows/apps/dn637137) properties of the [**MapTileBitmapRequestedEventArgs**](https://msdn.microsoft.com/library/windows/apps/dn637132) to create or retrieve a custom tile.</span></span>
2.  <span data-ttu-id="ab5e6-197">Geben Sie die benutzerdefinierte Kachel in der [**PixelData**](https://msdn.microsoft.com/library/windows/apps/dn637140)-Eigenschaft der [**MapTileBitmapRequest**](https://msdn.microsoft.com/library/windows/apps/dn637128)-Klasse zurück, die in der [**Request**](https://msdn.microsoft.com/library/windows/apps/dn637134)-Eigenschaft der [**MapTileBitmapRequestedEventArgs**](https://msdn.microsoft.com/library/windows/apps/dn637132)-Klasse enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-197">Return the custom tile in the [**PixelData**](https://msdn.microsoft.com/library/windows/apps/dn637140) property of the [**MapTileBitmapRequest**](https://msdn.microsoft.com/library/windows/apps/dn637128), which is contained in the [**Request**](https://msdn.microsoft.com/library/windows/apps/dn637134) property of the [**MapTileBitmapRequestedEventArgs**](https://msdn.microsoft.com/library/windows/apps/dn637132).</span></span> <span data-ttu-id="ab5e6-198">Bei der **PixelData**-Eigenschaft handelt es sich um den Typ [**IRandomAccessStreamReference**](https://msdn.microsoft.com/library/windows/apps/hh701664).</span><span class="sxs-lookup"><span data-stu-id="ab5e6-198">The **PixelData** property is of type [**IRandomAccessStreamReference**](https://msdn.microsoft.com/library/windows/apps/hh701664).</span></span>

<span data-ttu-id="ab5e6-199">Das folgende Beispiel zeigt, wie Sie benutzerdefinierte Kacheln durch Erstellen eines benutzerdefinierten Handlers für das **BitmapRequested**-Ereignis bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-199">The following example shows how to provide custom tiles by creating a custom handler for the **BitmapRequested** event.</span></span> <span data-ttu-id="ab5e6-200">In diesem Beispiel werden identische rote Kacheln erstellt, die teilweise deckend sind.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-200">This example creates identical red tiles that are partially opaque.</span></span> <span data-ttu-id="ab5e6-201">Im Beispiel werden die Eigenschaften [**X**](https://msdn.microsoft.com/library/windows/apps/dn637135), [**Y**](https://msdn.microsoft.com/library/windows/apps/dn637136) und [**ZoomLevel**](https://msdn.microsoft.com/library/windows/apps/dn637137) der [**MapTileBitmapRequestedEventArgs**](https://msdn.microsoft.com/library/windows/apps/dn637132)-Klasse ignoriert.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-201">The example ignores the [**X**](https://msdn.microsoft.com/library/windows/apps/dn637135), [**Y**](https://msdn.microsoft.com/library/windows/apps/dn637136), and [**ZoomLevel**](https://msdn.microsoft.com/library/windows/apps/dn637137) properties of the [**MapTileBitmapRequestedEventArgs**](https://msdn.microsoft.com/library/windows/apps/dn637132).</span></span> <span data-ttu-id="ab5e6-202">Auch wenn dies kein praktisches Beispiel ist, wird im Beispiel veranschaulicht, wie Sie benutzerdefinierte Kacheln im Arbeitsspeicher erstellen können.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-202">Although this is not a real world example, the example demonstrates how you can create in-memory custom tiles on the fly.</span></span> <span data-ttu-id="ab5e6-203">Sie erfahren zudem, wie Sie das Verzögerungsmuster implementieren, wenn Sie asynchron zum Erstellen der benutzerdefinierten Kacheln weitere Schritte ausführen müssen.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-203">The example also shows how to implement the deferral pattern if you have to do something asynchronously to create the custom tiles.</span></span>

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

## <a name="replace-the-default-map"></a><span data-ttu-id="ab5e6-204">Ersetzen der Standardkarte</span><span class="sxs-lookup"><span data-stu-id="ab5e6-204">Replace the default map</span></span>

<span data-ttu-id="ab5e6-205">So ersetzen Sie die Standardkarte durch Drittanbieter- oder benutzerdefinierte Kacheln:</span><span class="sxs-lookup"><span data-stu-id="ab5e6-205">To replace the default map entirely with third-party or custom tiles:</span></span>

-   <span data-ttu-id="ab5e6-206">Legen Sie [**MapTileLayer**](https://msdn.microsoft.com/library/windows/apps/dn637143).**BackgroundReplacement** als Wert für die [**Layer**](https://msdn.microsoft.com/library/windows/apps/dn637157)-Eigenschaft der [**MapTileSource**](https://msdn.microsoft.com/library/windows/apps/dn637144)-Klasse fest.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-206">Specify [**MapTileLayer**](https://msdn.microsoft.com/library/windows/apps/dn637143).**BackgroundReplacement** as the value of the [**Layer**](https://msdn.microsoft.com/library/windows/apps/dn637157) property of the [**MapTileSource**](https://msdn.microsoft.com/library/windows/apps/dn637144).</span></span>
-   <span data-ttu-id="ab5e6-207">Legen Sie [**MapStyle**](https://msdn.microsoft.com/library/windows/apps/dn637127).**None** als Wert für die [**Style**](https://msdn.microsoft.com/library/windows/apps/dn637051)-Eigenschaft der [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004)-Klasse fest.</span><span class="sxs-lookup"><span data-stu-id="ab5e6-207">Specify [**MapStyle**](https://msdn.microsoft.com/library/windows/apps/dn637127).**None** as the value of the [**Style**](https://msdn.microsoft.com/library/windows/apps/dn637051) property of the [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004).</span></span>

## <a name="related-topics"></a><span data-ttu-id="ab5e6-208">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="ab5e6-208">Related topics</span></span>

* [<span data-ttu-id="ab5e6-209">Bing Maps Developer Center</span><span class="sxs-lookup"><span data-stu-id="ab5e6-209">Bing Maps Developer Center</span></span>](https://www.bingmapsportal.com/)
* [<span data-ttu-id="ab5e6-210">Beispiel für UWP-Karte</span><span class="sxs-lookup"><span data-stu-id="ab5e6-210">UWP map sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=619977)
* [<span data-ttu-id="ab5e6-211">Entwurfsrichtlinien für Karten</span><span class="sxs-lookup"><span data-stu-id="ab5e6-211">Design guidelines for maps</span></span>](https://msdn.microsoft.com/library/windows/apps/dn596102)
* [<span data-ttu-id="ab5e6-212">Build 2015-Video: Nutzen von Karten und Ortung über Telefon, Tablet und PC in Ihren Windows-Apps</span><span class="sxs-lookup"><span data-stu-id="ab5e6-212">Build 2015 video: Leveraging Maps and Location Across Phone, Tablet, and PC in Your Windows Apps</span></span>](https://channel9.msdn.com/Events/Build/2015/2-757)
* [<span data-ttu-id="ab5e6-213">Beispiel für eine UWP-App mit Verkehrsinformationen</span><span class="sxs-lookup"><span data-stu-id="ab5e6-213">UWP traffic app sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=619982)
