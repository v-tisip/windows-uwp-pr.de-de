---
author: normesta
title: Anzeigen von interessanten Orten (POI) auf einer Karte
description: Mit Ortsmarken, Bildern, Formen und XAML-UI-Elementen können Sie interessante Orte (Points of Interest, POI) auf einer Karte hinzufügen.
ms.assetid: CA00D8EB-6C1B-4536-8921-5EAEB9B04FCA
ms.author: normesta
ms.date: 08/11/2017
ms.topic: article
keywords: windows10, uwp, karten, standort, ortsmarken
ms.localizationpriority: medium
ms.openlocfilehash: 13c0ea463cbab97e03c87c4e558bba0eff92300c
ms.sourcegitcommit: e38b334edb82bf2b1474ba686990f4299b8f59c7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6845615"
---
# <a name="display-points-of-interest-on-a-map"></a><span data-ttu-id="61454-104">Anzeigen von interessanten Orten (POI) auf einer Karte</span><span class="sxs-lookup"><span data-stu-id="61454-104">Display points of interest on a map</span></span>

<span data-ttu-id="61454-105">Mit Markiernadeln, Bildern, Formen und XAML-UI-Elementen können Sie interessante Orte (Points of Interest, POI) auf einer Karte hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="61454-105">Add points of interest (POI) to a map using pushpins, images, shapes, and XAML UI elements.</span></span> <span data-ttu-id="61454-106">Ein POI ist ein Punkt auf der Karte, der Orte angibt, die von Interesse sind.</span><span class="sxs-lookup"><span data-stu-id="61454-106">A POI is a specific point on the map that represents something of interest.</span></span> <span data-ttu-id="61454-107">Beispiele sind die Position eines Geschäfts, eines Orts oder eines Freundes.</span><span class="sxs-lookup"><span data-stu-id="61454-107">For example, the location of a business, city, or friend.</span></span>

<span data-ttu-id="61454-108">Wenn Sie mehr über das Anzeigen von POIs in Ihrer App erfahren möchten, laden Sie das folgende Beispiel aus dem [Windows-universal-samples-Repository](http://go.microsoft.com/fwlink/p/?LinkId=619979) auf GitHub herunter: [Universal Windows Platform (UWP)-Kartenbeispiel](http://go.microsoft.com/fwlink/p/?LinkId=619977).</span><span class="sxs-lookup"><span data-stu-id="61454-108">To learn more about displaying POI on your app, download the following sample from the [Windows-universal-samples repo](http://go.microsoft.com/fwlink/p/?LinkId=619979) on GitHub: [Universal Windows Platform (UWP) map sample](http://go.microsoft.com/fwlink/p/?LinkId=619977).</span></span>

<span data-ttu-id="61454-109">Zeigen Sie die Markiernadeln, Bilder und Formen auf der Karte an, indem Sie die Objekte [**MapIcon**](https://msdn.microsoft.com/library/windows/apps/dn637077), [**MapBillboard**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard),  [**MapPolygon**](https://msdn.microsoft.com/library/windows/apps/dn637103) und [**MapPolyline**](https://msdn.microsoft.com/library/windows/apps/dn637114) zu der **MapElements**-Sammlung eines [**MapElementsLayer**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapelementslayer)-Objekts hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="61454-109">Display pushpins, images, and shapes on the map by adding [**MapIcon**](https://msdn.microsoft.com/library/windows/apps/dn637077), [**MapBillboard**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard),  [**MapPolygon**](https://msdn.microsoft.com/library/windows/apps/dn637103), and [**MapPolyline**](https://msdn.microsoft.com/library/windows/apps/dn637114) objects to a **MapElements** collection of a [**MapElementsLayer**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapelementslayer) object.</span></span> <span data-ttu-id="61454-110">Fügen Sie dann der **Layers**-Sammlung eines Kartensteuerelements das Layer-Objekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="61454-110">Then, add that layer object to the **Layers** collection of a map control.</span></span>

>[!NOTE]
> <span data-ttu-id="61454-111">In früheren Versionen wurde in dieser Anleitung gezeigt, wie Sie der [**MapElements**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapcontrol.MapElements)-Sammlung Kartenelemente hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="61454-111">In previous releases, this guide showed you how to add map elements to the [**MapElements**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapcontrol.MapElements) collection.</span></span> <span data-ttu-id="61454-112">Sie können diesen Ansatz weiterhin verwenden, doch werden Ihnen dann einige der Vorteile des neuen Kartenschichtenmodells nicht zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="61454-112">While you can still use this approach, you'll miss out on some of the advantages of the new map layer model.</span></span> <span data-ttu-id="61454-113">Weitere Informationen hierzu finden Sie im Abschnitt [Arbeiten mit Schichten](#layers) dieser Anleitung.</span><span class="sxs-lookup"><span data-stu-id="61454-113">To learn more, see the [Working with layers](#layers) section of this guide.</span></span>

<span data-ttu-id="61454-114">Sie können auch XAML-Benutzeroberflächenelemente wie [**Button**](https://msdn.microsoft.com/library/windows/apps/br209265), [**HyperlinkButton**](https://msdn.microsoft.com/library/windows/apps/br242739) oder [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652) auf der Karte einsetzen, indem Sie sie zu [**MapItemsControl**](https://msdn.microsoft.com/library/windows/apps/dn637094) hinzufügen oder als [**Children**](https://msdn.microsoft.com/library/windows/apps/dn637008) für das [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004) verwenden.</span><span class="sxs-lookup"><span data-stu-id="61454-114">You can also display XAML user interface elements such as a [**Button**](https://msdn.microsoft.com/library/windows/apps/br209265), a [**HyperlinkButton**](https://msdn.microsoft.com/library/windows/apps/br242739), or a [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652) on the map by adding them to the [**MapItemsControl**](https://msdn.microsoft.com/library/windows/apps/dn637094) or as [**Children**](https://msdn.microsoft.com/library/windows/apps/dn637008) of the [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004).</span></span>

<span data-ttu-id="61454-115">Wenn Sie eine große Anzahl von Elementen auf der Karte platzieren möchten, sollten Sie [nebeneinander angeordnete Bilder auf der Karte überlagern](overlay-tiled-images.md).</span><span class="sxs-lookup"><span data-stu-id="61454-115">If you have a large number of elements to place on the map, consider [overlaying tiled images on the map](overlay-tiled-images.md).</span></span> <span data-ttu-id="61454-116">Informationen zum Anzeigen von Straßen auf der Karte finden Sie unter [Anzeigen von Routen und Wegbeschreibungen](routes-and-directions.md).</span><span class="sxs-lookup"><span data-stu-id="61454-116">To display roads on the map, see [Display routes and directions](routes-and-directions.md)</span></span>

## <a name="add-a-pushpin"></a><span data-ttu-id="61454-117">Hinzufügen einer Markiernadel</span><span class="sxs-lookup"><span data-stu-id="61454-117">Add a pushpin</span></span>

<span data-ttu-id="61454-118">Verwenden Sie die Klasse [**MapIcon**](https://msdn.microsoft.com/library/windows/apps/dn637077), um Bilder wie eine Markiernadel mit optionalem Text auf der Karte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="61454-118">Display an image such a pushpin, with optional text, on the map by using the [**MapIcon**](https://msdn.microsoft.com/library/windows/apps/dn637077) class.</span></span> <span data-ttu-id="61454-119">Sie können das Standardbild akzeptieren oder mit der [**Image**](https://msdn.microsoft.com/library/windows/apps/dn637078)-Eigenschaft ein benutzerdefiniertes Bild bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="61454-119">You can accept the default image or provide a custom image by using the [**Image**](https://msdn.microsoft.com/library/windows/apps/dn637078) property.</span></span> <span data-ttu-id="61454-120">Die folgende Abbildung zeigt das Standardbild für ein **MapIcon** ohne festgelegten Wert für die Eigenschaft [**Title**](https://msdn.microsoft.com/library/windows/apps/dn637088) mit einem kurzen Titel, einem langen Titel und einem sehr langen Titel.</span><span class="sxs-lookup"><span data-stu-id="61454-120">The following image displays the default image for a **MapIcon** with no value specified for the [**Title**](https://msdn.microsoft.com/library/windows/apps/dn637088) property, with a short title, with a long title, and with a very long title.</span></span>

![Beispiel für MapIcon mit Titeln unterschiedlicher Länge](images/mapctrl-mapicons.png)

<span data-ttu-id="61454-122">Im folgenden Beispiel wird einer Karte von Seattle ein [**MapIcon**](https://msdn.microsoft.com/library/windows/apps/dn637077) mit Standardbild und optionalem Titel hinzugefügt, um den Standort der Space Needle anzugeben.</span><span class="sxs-lookup"><span data-stu-id="61454-122">The following example shows a map of the city of Seattle and adds a [**MapIcon**](https://msdn.microsoft.com/library/windows/apps/dn637077) with the default image and an optional title to indicate the location of the Space Needle.</span></span> <span data-ttu-id="61454-123">Außerdem wird die Karte auf dem Symbol zentriert und vergrößert.</span><span class="sxs-lookup"><span data-stu-id="61454-123">It also centers the map over the icon and zooms in.</span></span> <span data-ttu-id="61454-124">Allgemeine Informationen zur Verwendung des Kartensteuerelements finden Sie unter [Anzeigen von Karten mit 2D-, 3D- und Streetside-Ansichten](display-maps.md).</span><span class="sxs-lookup"><span data-stu-id="61454-124">For general info about using the map control, see [Display maps with 2D, 3D, and Streetside views](display-maps.md).</span></span>

```csharp
public void AddSpaceNeedleIcon()
{
    var MyLandmarks = new List<MapElement>();

    BasicGeoposition snPosition = new BasicGeoposition { Latitude = 47.620, Longitude = -122.349 };
    Geopoint snPoint = new Geopoint(snPosition);

    var spaceNeedleIcon = new MapIcon
    {
        Location = snPoint,
        NormalizedAnchorPoint = new Point(0.5, 1.0),
        ZIndex = 0,
        Title = "Space Needle"
    };

    MyLandmarks.Add(spaceNeedleIcon);

    var LandmarksLayer = new MapElementsLayer
    {
        ZIndex = 1,
        MapElements = MyLandmarks
    };

    myMap.Layers.Add(LandmarksLayer);

    myMap.Center = snPoint;
    myMap.ZoomLevel = 14;

}
```

<span data-ttu-id="61454-125">In diesem Beispiel wird der folgende interessante Ort (POI) auf der Karte angezeigt (mit dem Standardbild in der Mitte).</span><span class="sxs-lookup"><span data-stu-id="61454-125">This example displays the following POI on the map (the default image in the center).</span></span>

![Karte mit MapIcon](images/displaypoidefault.png)

<span data-ttu-id="61454-127">Die folgende Codezeile zeigt [**MapIcon**](https://msdn.microsoft.com/library/windows/apps/dn637077) mit einem benutzerdefinierten Bild an, das im Ordner „Assets“ (Ressourcen) des Projekts gespeichert wurde.</span><span class="sxs-lookup"><span data-stu-id="61454-127">The following line of code displays the [**MapIcon**](https://msdn.microsoft.com/library/windows/apps/dn637077) with a custom image saved in the Assets folder of the project.</span></span> <span data-ttu-id="61454-128">Die Eigenschaft [**Image**](https://msdn.microsoft.com/library/windows/apps/dn637078) von **MapIcon** erwartet einen Wert vom Typ [**RandomAccessStreamReference**](https://msdn.microsoft.com/library/windows/apps/hh701813).</span><span class="sxs-lookup"><span data-stu-id="61454-128">The [**Image**](https://msdn.microsoft.com/library/windows/apps/dn637078) property of the **MapIcon** expects a value of type [**RandomAccessStreamReference**](https://msdn.microsoft.com/library/windows/apps/hh701813).</span></span> <span data-ttu-id="61454-129">Dieser Typ erfordert die Anweisung **using** für den Namespace [**Windows.Storage.Streams**](https://msdn.microsoft.com/library/windows/apps/br241791).</span><span class="sxs-lookup"><span data-stu-id="61454-129">This type requires a **using** statement for the [**Windows.Storage.Streams**](https://msdn.microsoft.com/library/windows/apps/br241791) namespace.</span></span>

>[!NOTE]
><span data-ttu-id="61454-130">Wenn Sie dasselbe Bild für mehrere Kartensymbole verwenden, deklarieren Sie [**RandomAccessStreamReference**](https://msdn.microsoft.com/library/windows/apps/hh701813) auf Seiten- oder App-Ebene, um eine optimale Leistung zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="61454-130">If you use the same image for multiple map icons, declare the [**RandomAccessStreamReference**](https://msdn.microsoft.com/library/windows/apps/hh701813) at the page or app level for the best performance.</span></span>

```csharp
    MapIcon1.Image =
        RandomAccessStreamReference.CreateFromUri(new Uri("ms-appx:///Assets/customicon.png"));
```

<span data-ttu-id="61454-131">Berücksichtigen Sie beim Arbeiten mit der [**MapIcon**](https://msdn.microsoft.com/library/windows/apps/dn637077)-Klasse Folgendes:</span><span class="sxs-lookup"><span data-stu-id="61454-131">Keep these considerations in mind when working with the [**MapIcon**](https://msdn.microsoft.com/library/windows/apps/dn637077) class:</span></span>

-   <span data-ttu-id="61454-132">Die [**Image**](https://msdn.microsoft.com/library/windows/apps/dn637078)-Eigenschaft unterstützt eine maximale Bildgröße von 2048x2048Pixeln.</span><span class="sxs-lookup"><span data-stu-id="61454-132">The [**Image**](https://msdn.microsoft.com/library/windows/apps/dn637078) property supports a maximum image size of 2048×2048 pixels.</span></span>
-   <span data-ttu-id="61454-133">Standardmäßig wird die Anzeige des Bilds für das Kartensymbol nicht garantiert.</span><span class="sxs-lookup"><span data-stu-id="61454-133">By default, the map icon's image is not guaranteed to be shown.</span></span> <span data-ttu-id="61454-134">Es wird möglicherweise ausgeblendet, wenn es andere Elemente oder Bezeichnungen auf der Karte verdeckt.</span><span class="sxs-lookup"><span data-stu-id="61454-134">It may be hidden when it obscures other elements or labels on the map.</span></span> <span data-ttu-id="61454-135">Damit es sichtbar bleibt, legen Sie die [**CollisionBehaviorDesired**](https://msdn.microsoft.com/library/windows/apps/dn974327)-Eigenschaft des Kartensymbols auf [**MapElementCollisionBehavior.RemainVisible**](https://msdn.microsoft.com/library/windows/apps/dn974314) fest.</span><span class="sxs-lookup"><span data-stu-id="61454-135">To keep it visible, set the map icon's [**CollisionBehaviorDesired**](https://msdn.microsoft.com/library/windows/apps/dn974327) property to [**MapElementCollisionBehavior.RemainVisible**](https://msdn.microsoft.com/library/windows/apps/dn974314).</span></span>
-   <span data-ttu-id="61454-136">Die Anzeige des optionalen [**Title**](https://msdn.microsoft.com/library/windows/apps/dn637088) für [**MapIcon**](https://msdn.microsoft.com/library/windows/apps/dn637077) wird nicht garantiert.</span><span class="sxs-lookup"><span data-stu-id="61454-136">The optional [**Title**](https://msdn.microsoft.com/library/windows/apps/dn637088) of the [**MapIcon**](https://msdn.microsoft.com/library/windows/apps/dn637077) is not guaranteed to be shown.</span></span> <span data-ttu-id="61454-137">Wenn der Text nicht angezeigt wird, verkleinern Sie die Ansicht, indem Sie den Wert der [**ZoomLevel**](https://msdn.microsoft.com/library/windows/apps/dn637068)-Eigenschaft von [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004) verringern.</span><span class="sxs-lookup"><span data-stu-id="61454-137">If you don't see the text, zoom out by decreasing the value of the [**ZoomLevel**](https://msdn.microsoft.com/library/windows/apps/dn637068) property of the [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004).</span></span>
-   <span data-ttu-id="61454-138">Wenn Sie ein [**MapIcon**](https://msdn.microsoft.com/library/windows/apps/dn637077)-Bild anzeigen, das auf eine bestimmte Position auf der Karte hinweist, z.B. eine Ortsmarkierung oder ein Pfeil, sollten Sie in Erwägung ziehen, den Wert der [**NormalizedAnchorPoint**](https://msdn.microsoft.com/library/windows/apps/dn637082)-Eigenschaft auf den ungefähren Standort des Zeigers auf dem Bild festzulegen.</span><span class="sxs-lookup"><span data-stu-id="61454-138">When you display a [**MapIcon**](https://msdn.microsoft.com/library/windows/apps/dn637077) image that points to a specific location on the map - for example, a pushpin or an arrow - consider setting the value of the [**NormalizedAnchorPoint**](https://msdn.microsoft.com/library/windows/apps/dn637082) property to the approximate location of the pointer on the image.</span></span> <span data-ttu-id="61454-139">Wenn Sie den Wert von **NormalizedAnchorPoint** beim Standardwert (0, 0) belassen, der die obere linke Ecke des Bilds darstellt, führen Änderungen am [**ZoomLevel**](https://msdn.microsoft.com/library/windows/apps/dn637068) der Karte möglicherweise dazu, dass das Bild auf eine andere Position zeigt.</span><span class="sxs-lookup"><span data-stu-id="61454-139">If you leave the value of **NormalizedAnchorPoint** at its default value of (0, 0), which represents the upper left corner of the image, changes in the [**ZoomLevel**](https://msdn.microsoft.com/library/windows/apps/dn637068) of the map may leave the image pointing to a different location.</span></span>
-   <span data-ttu-id="61454-140">Wenn Sie [Altitude](https://docs.microsoft.com/uwp/api/windows.devices.geolocation.basicgeoposition) und [AltitudeReferenceSystem](https://docs.microsoft.com/uwp/api/windows.devices.geolocation.geopoint.AltitudeReferenceSystem) nicht explizit festlegen, wird [**MapIcon**](https://msdn.microsoft.com/library/windows/apps/dn637077) auf der Oberfläche platziert.</span><span class="sxs-lookup"><span data-stu-id="61454-140">If you don't explicitly set an [Altitude](https://docs.microsoft.com/uwp/api/windows.devices.geolocation.basicgeoposition) and [AltitudeReferenceSystem](https://docs.microsoft.com/uwp/api/windows.devices.geolocation.geopoint.AltitudeReferenceSystem), the [**MapIcon**](https://msdn.microsoft.com/library/windows/apps/dn637077) will be placed on the surface.</span></span>

## <a name="add-a-3d-pushpin"></a><span data-ttu-id="61454-141">Hinzufügen einer 3D-Markiernadel</span><span class="sxs-lookup"><span data-stu-id="61454-141">Add a 3D pushpin</span></span>

<span data-ttu-id="61454-142">Sie können dreidimensionale Objekte auf einer Karte hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="61454-142">You can add three-dimensional objects to a map.</span></span> <span data-ttu-id="61454-143">Verwenden Sie die Klasse [MapModel3D](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapmodel3d), um ein 3D-Objekt aus einer [3D Manufacturing Format (3MF)](http://3mf.io/specification/)-Datei zu importieren.</span><span class="sxs-lookup"><span data-stu-id="61454-143">Use the [MapModel3D](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapmodel3d) class to import a 3D object from a [3D Manufacturing Format (3MF)](http://3mf.io/specification/) file.</span></span>

<span data-ttu-id="61454-144">Diese Abbildung verwendet 3D-Kaffeekannen, um die Standorte von Cafés der Umgebung zu markieren.</span><span class="sxs-lookup"><span data-stu-id="61454-144">This image uses 3D coffee cups to mark the locations of coffee shops in a neighborhood.</span></span>

![Tassen auf der Karte](images/mugs.png)

<span data-ttu-id="61454-146">Der folgende Code fügt der Karte eine Kaffeetasse hinzu, die aus einer 3MF-Datei importiert wird.</span><span class="sxs-lookup"><span data-stu-id="61454-146">The following code adds a coffee cup to the map by using importing a 3MF file.</span></span> <span data-ttu-id="61454-147">Dieser Code fügt das Bild der Einfachheit halber in die Mitte der Karte ein. In Ihrem Code würden Sie das Bild wahrscheinlich an einer bestimmten Position einfügen.</span><span class="sxs-lookup"><span data-stu-id="61454-147">To keep things simple, this code adds the image to the center of the map, but your code would likely add the image to a specific location.</span></span>

```csharp
public async void Add3DMapModel()
{
    var mugStreamReference = RandomAccessStreamReference.CreateFromUri
        (new Uri("ms-appx:///Assets/mug.3mf"));

    var myModel = await MapModel3D.CreateFrom3MFAsync(mugStreamReference,
        MapModel3DShadingOption.Smooth);

    myMap.Layers.Add(new MapElementsLayer
    {
       ZIndex = 1,
       MapElements = new List<MapElement>
       {
          new MapElement3D
          {
              Location = myMap.Center,
              Model = myModel,
          },
       },
    });
}
```

## <a name="add-an-image"></a><span data-ttu-id="61454-148">Hinzufügen eines Bilds</span><span class="sxs-lookup"><span data-stu-id="61454-148">Add an image</span></span>

<span data-ttu-id="61454-149">Zeigen Sie große Bilder an, die im Zusammenhang mit Kartenpositionen (z.B. ein Bild von einem Restaurant oder einer Sehenswürdigkeit) stehen.</span><span class="sxs-lookup"><span data-stu-id="61454-149">Display large images that relate to map locations such as a picture of a restaurant or a landmark.</span></span> <span data-ttu-id="61454-150">Wenn der Benutzer verkleinert, wird das Bild proportional größer, damit der Benutzer mehr von der Karte anzeigen kann.</span><span class="sxs-lookup"><span data-stu-id="61454-150">As users zoom out, the image will shrink proportionally in size to enable the user to view more of the map.</span></span> <span data-ttu-id="61454-151">Dies ist etwas anders als ein [**MapIcon**](https://msdn.microsoft.com/library/windows/apps/dn637077), das einen bestimmten Ort kennzeichnet. Es ist in der Regel klein und bleibt bei der gleichen Größe wenn der Benutzer eine Karte verkleinert.</span><span class="sxs-lookup"><span data-stu-id="61454-151">This is a bit different than a [**MapIcon**](https://msdn.microsoft.com/library/windows/apps/dn637077) which marks a specific location, is typically small, and remains the same size as users zoom in and out of a map.</span></span>

![MapBillboard-Bild](images/map-billboard.png)

<span data-ttu-id="61454-153">Der folgende Code zeigt das [**MapBillboard**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard) in der Abbildungoben.</span><span class="sxs-lookup"><span data-stu-id="61454-153">The following code shows the [**MapBillboard**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard) presented in the image above.</span></span>

```csharp
public void AddLandmarkPhoto()
{
    // Create MapBillboard.

    RandomAccessStreamReference mapBillboardStreamReference =
        RandomAccessStreamReference.CreateFromUri(new Uri("ms-appx:///Assets/billboard.jpg"));

    var mapBillboard = new MapBillboard(myMap.ActualCamera)
    {
        Location = myMap.Center,
        NormalizedAnchorPoint = new Point(0.5, 1.0),
        Image = mapBillboardStreamReference
    };

    // Add MapBillboard to a layer on the map control.

    var MyLandmarkPhotos = new List<MapElement>();

    MyLandmarkPhotos.Add(mapBillboard);

    var LandmarksPhotoLayer = new MapElementsLayer
    {
        ZIndex = 1,
        MapElements = MyLandmarkPhotos
    };

    myMap.Layers.Add(LandmarksPhotoLayer);
}
```

<span data-ttu-id="61454-154">Drei Teile dieses Codes sollten ein bisschen näher untersucht werden: das Bild, die Referenzkamera und die [**NormalizedAnchorPoint**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard.NormalizedAnchorPoint)-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="61454-154">There's three parts of this code worth examining a little closer: The image, the reference camera, and the [**NormalizedAnchorPoint**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard.NormalizedAnchorPoint) property.</span></span>

### <a name="image"></a><span data-ttu-id="61454-155">Bild</span><span class="sxs-lookup"><span data-stu-id="61454-155">Image</span></span>

<span data-ttu-id="61454-156">In diesem Beispiel wird ein benutzerdefiniertes Bild im **Assets** Ordner des Projekts gespeichert.</span><span class="sxs-lookup"><span data-stu-id="61454-156">This example shows a custom image saved in the **Assets** folder of the project.</span></span> <span data-ttu-id="61454-157">Die Eigenschaft [**Image**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard.Image) von [**MapBillboard**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard) erwartet einen Wert vom Typ [**RandomAccessStreamReference**](https://msdn.microsoft.com/library/windows/apps/hh701813).</span><span class="sxs-lookup"><span data-stu-id="61454-157">The [**Image**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard.Image) property of the [**MapBillboard**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard) expects a value of type [**RandomAccessStreamReference**](https://msdn.microsoft.com/library/windows/apps/hh701813).</span></span> <span data-ttu-id="61454-158">Dieser Typ erfordert die Anweisung **using** für den Namespace [**Windows.Storage.Streams**](https://msdn.microsoft.com/library/windows/apps/br241791).</span><span class="sxs-lookup"><span data-stu-id="61454-158">This type requires a **using** statement for the [**Windows.Storage.Streams**](https://msdn.microsoft.com/library/windows/apps/br241791) namespace.</span></span>

>[!NOTE]
><span data-ttu-id="61454-159">Wenn Sie dasselbe Bild für mehrere Kartensymbole verwenden, deklarieren Sie [**RandomAccessStreamReference**](https://msdn.microsoft.com/library/windows/apps/hh701813) auf Seiten- oder App-Ebene, um eine optimale Leistung zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="61454-159">If you use the same image for multiple map icons, declare the [**RandomAccessStreamReference**](https://msdn.microsoft.com/library/windows/apps/hh701813) at the page or app level for the best performance.</span></span>

### <a name="reference-camera"></a><span data-ttu-id="61454-160">Referenzkamera</span><span class="sxs-lookup"><span data-stu-id="61454-160">Reference camera</span></span>

 <span data-ttu-id="61454-161">Da ein [**MapBillboard**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard)-Bild skaliert sobald sich das [**ZoomLevel**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapcontrol.ZoomLevel) der Karte ändert, es ist wichtig zu definieren, bei welchem [**ZoomLevel**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapcontrol.ZoomLevel) das Bild mit einer normalen 1x-Skalierung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="61454-161">Because a [**MapBillboard**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard) image scales in and out as the [**ZoomLevel**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapcontrol.ZoomLevel) of the map changes, it's important to define where in that [**ZoomLevel**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapcontrol.ZoomLevel) the image appears at a normal 1x scale.</span></span> <span data-ttu-id="61454-162">Die Position ist in der Referenzkamera des [**MapBillboard**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard) definiert. Um sie festzulegen müssen Sie ein [**MapCamera**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapcamera) Objekt an den Konstruktor des [**MapBillboard**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard) übergeben.</span><span class="sxs-lookup"><span data-stu-id="61454-162">That position is defined in the reference camera of the [**MapBillboard**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard), and to set it, you'll have to pass a [**MapCamera**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapcamera) object into the constructor of the [**MapBillboard**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard).</span></span>

 <span data-ttu-id="61454-163">Können Sie die gewünschte Position in einem [**Geopoint**](https://docs.microsoft.com/uwp/api/windows.devices.geolocation.geopoint) definieren, und diesen [**Geopoint**](https://docs.microsoft.com/uwp/api/windows.devices.geolocation.geopoint) zum Erstellen eines [**MapCamera**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapcamera) Objekts verwenden.</span><span class="sxs-lookup"><span data-stu-id="61454-163">You can define the position that you want in a [**Geopoint**](https://docs.microsoft.com/uwp/api/windows.devices.geolocation.geopoint), and then use that [**Geopoint**](https://docs.microsoft.com/uwp/api/windows.devices.geolocation.geopoint) to create a [**MapCamera**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapcamera) object.</span></span>  <span data-ttu-id="61454-164">In diesem Beispiel verwenden wir jedoch das [**MapCamera**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapcamera)Objekt, das von der [**ActualCamera**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapcontrol.ActualCamera)-Eigenschaft des Kartensteuerelements zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="61454-164">However, in this example, we're just using the [**MapCamera**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapcamera) object returned by the [**ActualCamera**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapcontrol.ActualCamera) property of the map control.</span></span> <span data-ttu-id="61454-165">Hierbei handelt es sich um die interne Kamera der Karte.</span><span class="sxs-lookup"><span data-stu-id="61454-165">This is the map's internal camera.</span></span> <span data-ttu-id="61454-166">Die aktuelle Position der Kamera wird die Referenzkameraposition (die Position, in der das [**MapBillboard**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard) Bild mit 1x Skalierung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="61454-166">The current position of that camera becomes the reference camera position; the position where the [**MapBillboard**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard) image appears at 1x scale.</span></span>

 <span data-ttu-id="61454-167">Wenn Ihre App den Benutzern die Möglichkeit gibt, die Karte zu verkleinern, verringert das Bild die Größe, da die interne Kamera der Karte steigt während das Bild bei der 1x-Skalierung an der Referenzkameraposition verbleibt.</span><span class="sxs-lookup"><span data-stu-id="61454-167">If your app gives users the ability to zoom out on the map, the image decreases in size because the maps internal camera is rising in altitude while the image at 1x scale remains fixed at the reference camera's position.</span></span>

### <a name="normalizedanchorpoint"></a><span data-ttu-id="61454-168">NormalizedAnchorPoint</span><span class="sxs-lookup"><span data-stu-id="61454-168">NormalizedAnchorPoint</span></span>

<span data-ttu-id="61454-169">Der [**NormalizedAnchorPoint**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard.NormalizedAnchorPoint) ist der Punkt des Bilds, das an der [**Speicherort**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard.Location) Eigenschaft des [**MapBillboard**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard) verankert ist.</span><span class="sxs-lookup"><span data-stu-id="61454-169">The [**NormalizedAnchorPoint**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard.NormalizedAnchorPoint) is the point of the image that is anchored to the [**Location**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard.Location) property of the [**MapBillboard**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard).</span></span> <span data-ttu-id="61454-170">Der Punkt 0,5,1 ist die untere Mitte des Bilds.</span><span class="sxs-lookup"><span data-stu-id="61454-170">The point 0.5,1 is the bottom center of the image.</span></span> <span data-ttu-id="61454-171">Da wir die [**Location**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard.Location) Eigenschaft des [**MapBillboard**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard)auf die untere Mitte des Kartensteuerelements festgelegt haben, wir die untere Mitte des Bilds an der unteren Mitte des Kartensteuerelements verankert.</span><span class="sxs-lookup"><span data-stu-id="61454-171">Because we've set the [**Location**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard.Location) property of the [**MapBillboard**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard) to the center of the map's control, the bottom center of the image will be anchored at the center of the maps control.</span></span> <span data-ttu-id="61454-172">Wenn das Bild direkt über einem Punkt zentriert angezeigt werden soll, müssen Sie [**NormalizedAnchorPoint**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard.NormalizedAnchorPoint) auf 0.5,0.5 festlegen.</span><span class="sxs-lookup"><span data-stu-id="61454-172">If you want your image to appear centered directly over a point, set the [**NormalizedAnchorPoint**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard.NormalizedAnchorPoint) to 0.5,0.5.</span></span>  

## <a name="add-a-shape"></a><span data-ttu-id="61454-173">Hinzufügen einer Form</span><span class="sxs-lookup"><span data-stu-id="61454-173">Add a shape</span></span>

<span data-ttu-id="61454-174">Mithilfe der Klasse [**MapPolygon**](https://msdn.microsoft.com/library/windows/apps/dn637103) können Sie eine Multipoint-Form auf der Karte anzeigen.</span><span class="sxs-lookup"><span data-stu-id="61454-174">Display a multi-point shape on the map by using the [**MapPolygon**](https://msdn.microsoft.com/library/windows/apps/dn637103) class.</span></span> <span data-ttu-id="61454-175">Im folgenden Beispiel (aus dem [UWP-Kartenbeispiel](http://go.microsoft.com/fwlink/p/?LinkId=619977)) wird ein rotes Feld mit blauem Rahmen auf der Karte angezeigt.</span><span class="sxs-lookup"><span data-stu-id="61454-175">The following example, from the [UWP map sample](http://go.microsoft.com/fwlink/p/?LinkId=619977), displays a red box with blue border on the map.</span></span>

```csharp
public void HighlightArea()
{
    // Create MapPolygon.

    double centerLatitude = myMap.Center.Position.Latitude;
    double centerLongitude = myMap.Center.Position.Longitude;

    var mapPolygon = new MapPolygon
    {
        Path = new Geopath(new List<BasicGeoposition> {
                    new BasicGeoposition() {Latitude=centerLatitude+0.0005, Longitude=centerLongitude-0.001 },
                    new BasicGeoposition() {Latitude=centerLatitude-0.0005, Longitude=centerLongitude-0.001 },
                    new BasicGeoposition() {Latitude=centerLatitude-0.0005, Longitude=centerLongitude+0.001 },
                    new BasicGeoposition() {Latitude=centerLatitude+0.0005, Longitude=centerLongitude+0.001 },
                }),
        ZIndex = 1,
        FillColor = Colors.Red,
        StrokeColor = Colors.Blue,
        StrokeThickness = 3,
        StrokeDashed = false,
    };

    // Add MapPolygon to a layer on the map control.
    var MyHighlights = new List<MapElement>();

    MyHighlights.Add(mapPolygon);

    var HighlightsLayer = new MapElementsLayer
    {
        ZIndex = 1,
        MapElements = MyHighlights
    };

    myMap.Layers.Add(HighlightsLayer);
}
```

## <a name="add-a-line"></a><span data-ttu-id="61454-176">Hinzufügen einer Linie</span><span class="sxs-lookup"><span data-stu-id="61454-176">Add a line</span></span>


<span data-ttu-id="61454-177">Mithilfe der Klasse [**MapPolyline**](https://msdn.microsoft.com/library/windows/apps/dn637114) können Sie eine Linie auf der Karte anzeigen.</span><span class="sxs-lookup"><span data-stu-id="61454-177">Display a line on the map by using the [**MapPolyline**](https://msdn.microsoft.com/library/windows/apps/dn637114) class.</span></span> <span data-ttu-id="61454-178">Im folgenden Beispiel (aus dem [Beispiel zu UWP-Karten](http://go.microsoft.com/fwlink/p/?LinkId=619977)) wird eine gestrichelte Linie auf der Karte angezeigt.</span><span class="sxs-lookup"><span data-stu-id="61454-178">The following example, from the [UWP map sample](http://go.microsoft.com/fwlink/p/?LinkId=619977), displays a dashed line on the map.</span></span>

```csharp
public void DrawLineOnMap()
{
    // Create Polyline.

    double centerLatitude = myMap.Center.Position.Latitude;
    double centerLongitude = myMap.Center.Position.Longitude;
    var mapPolyline = new MapPolyline
    {
        Path = new Geopath(new List<BasicGeoposition> {
                    new BasicGeoposition() {Latitude=centerLatitude-0.0005, Longitude=centerLongitude-0.001 },
                    new BasicGeoposition() {Latitude=centerLatitude+0.0005, Longitude=centerLongitude+0.001 },
                }),
        StrokeColor = Colors.Black,
        StrokeThickness = 3,
        StrokeDashed = true,
    };

   // Add Polyline to a layer on the map control.

   var MyLines = new List<MapElement>();

   MyLines.Add(mapPolyline);

   var LinesLayer = new MapElementsLayer
   {
       ZIndex = 1,
       MapElements = MyLines
   };

   myMap.Layers.Add(LinesLayer);

}
```

## <a name="add-xaml"></a><span data-ttu-id="61454-179">Hinzufügen von XAML</span><span class="sxs-lookup"><span data-stu-id="61454-179">Add XAML</span></span>

<span data-ttu-id="61454-180">Zeigen Sie benutzerdefinierte UI-Elemente mit XAML auf der Karte an.</span><span class="sxs-lookup"><span data-stu-id="61454-180">Display custom UI elements on the map using XAML.</span></span> <span data-ttu-id="61454-181">Positionieren Sie XAML auf der Karte, indem Sie die Position und den normalisierten Ankerpunkt für den XAML-Code angeben.</span><span class="sxs-lookup"><span data-stu-id="61454-181">Position XAML on the map by specifying the location and normalized anchor point of the XAML.</span></span>

-   <span data-ttu-id="61454-182">Rufen Sie [**SetLocation**](https://msdn.microsoft.com/library/windows/desktop/ms704369) auf, um die Position auf der Karte festzulegen, an der der XAML-Code platziert werden soll.</span><span class="sxs-lookup"><span data-stu-id="61454-182">Set the location on the map where the XAML is placed by calling [**SetLocation**](https://msdn.microsoft.com/library/windows/desktop/ms704369).</span></span>
-   <span data-ttu-id="61454-183">Rufen Sie [**SetNormalizedAnchorPoint**](https://msdn.microsoft.com/library/windows/apps/dn637050) auf, um die relative Position des XAML-Codes festzulegen, die der angegebenen Position entspricht.</span><span class="sxs-lookup"><span data-stu-id="61454-183">Set the relative location on the XAML that corresponds to the specified location by calling [**SetNormalizedAnchorPoint**](https://msdn.microsoft.com/library/windows/apps/dn637050).</span></span>

<span data-ttu-id="61454-184">Im folgenden Beispiel wird einer Karte von Seattle das XAML-Steuerelement [**Border**](https://msdn.microsoft.com/library/windows/apps/br209250) hinzugefügt, um den Standort der Space Needle anzugeben.</span><span class="sxs-lookup"><span data-stu-id="61454-184">The following example shows a map of the city of Seattle and adds a XAML [**Border**](https://msdn.microsoft.com/library/windows/apps/br209250) control to indicate the location of the Space Needle.</span></span> <span data-ttu-id="61454-185">Außerdem wird die Karte in diesem Bereich zentriert und vergrößert.</span><span class="sxs-lookup"><span data-stu-id="61454-185">It also centers the map over the area and zooms in.</span></span> <span data-ttu-id="61454-186">Allgemeine Informationen zur Verwendung des Kartensteuerelements finden Sie unter [Anzeigen von Karten mit 2D-, 3D- und Streetside-Ansichten](display-maps.md).</span><span class="sxs-lookup"><span data-stu-id="61454-186">For general info about using the map control, see [Display maps with 2D, 3D, and Streetside views](display-maps.md).</span></span>

```csharp
private void displayXAMLButton_Click(object sender, RoutedEventArgs e)
{
   // Specify a known location.
   BasicGeoposition snPosition = new BasicGeoposition { Latitude = 47.620, Longitude = -122.349 };
   Geopoint snPoint = new Geopoint(snPosition);

   // Create a XAML border.
   Border border = new Border
   {
      Height = 100,
      Width = 100,
      BorderBrush = new SolidColorBrush(Windows.UI.Colors.Blue),
      BorderThickness = new Thickness(5),
   };

   // Center the map over the POI.
   MapControl1.Center = snPoint;
   MapControl1.ZoomLevel = 14;

   // Add XAML to the map.
   MapControl1.Children.Add(border);
   MapControl.SetLocation(border, snPoint);
   MapControl.SetNormalizedAnchorPoint(border, new Point(0.5, 0.5));
}
```

<span data-ttu-id="61454-187">In diesem Beispiel wird ein blauer Rahmen auf der Karte angezeigt.</span><span class="sxs-lookup"><span data-stu-id="61454-187">This example displays a blue border on the map.</span></span>

![Screenshot eines XAML-Elements, das am interessanten Ort auf der Karte angezeigt wird](images/displaypoixaml.png)

<span data-ttu-id="61454-189">Die nächsten Beispiele zeigen, wie XAML-UI-Elemente direkt im XAML-Markup der Seite mithilfe der Datenbindung hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="61454-189">The next examples show how to add XAML UI elements directly in the XAML markup of the page using data binding.</span></span> <span data-ttu-id="61454-190">Wie bei anderen XAML-Elementen zur Anzeige von Inhalten auch, stellt [**Children**](https://msdn.microsoft.com/library/windows/apps/dn637008) die standardmäßige Inhaltseigenschaft von [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004) dar und muss nicht explizit im XAML-Markup angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="61454-190">As with other XAML elements that display content, [**Children**](https://msdn.microsoft.com/library/windows/apps/dn637008) is the default content property of the [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004) and does not have to be specified explicitly in XAML markup.</span></span>

<span data-ttu-id="61454-191">In diesem Beispiel wird gezeigt, wie zwei XAML-Steuerelemente als implizite untergeordnete Elemente von [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004) angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="61454-191">This example shows how to display two XAML controls as implicit children of the [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004).</span></span> <span data-ttu-id="61454-192">Diese Steuerelemente werden auf der Karte an den datengebundenen Positionen angezeigt</span><span class="sxs-lookup"><span data-stu-id="61454-192">These controls appear on the map at the data bound locations.</span></span>

```xml
<maps:MapControl>
    <TextBox Text="Seattle" maps:MapControl.Location="{x:Bind SeattleLocation}"/>
    <TextBox Text="Bellevue" maps:MapControl.Location="{x:Bind BellevueLocation}"/>
</maps:MapControl>
```

<span data-ttu-id="61454-193">Legen Sie diese Positionen mithilfe der Eigenschaften in der CodeBehind-Datei fest.</span><span class="sxs-lookup"><span data-stu-id="61454-193">Set these locations by using a properties in your code-behind file.</span></span>

```csharp
public Geopoint SeattleLocation { get; set; }
public Geopoint BellevueLocation { get; set; }
```

<span data-ttu-id="61454-194">Dieses Beispiel zeigt, wie zwei XAML-Steuerelemente aus einem [**MapItemsControl**](https://msdn.microsoft.com/library/windows/apps/dn637094)angezeigt werden. Diese Steuerelemente werden auf der Karte an den datengebundenen Positionen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="61454-194">This example shows how to display two XAML controls contained within a [**MapItemsControl**](https://msdn.microsoft.com/library/windows/apps/dn637094).These controls appear on the map at the data bound locations.</span></span>

```xml
<maps:MapControl>
  <maps:MapItemsControl>
    <TextBox Text="Seattle" maps:MapControl.Location="{x:Bind SeattleLocation}"/>
    <TextBox Text="Bellevue" maps:MapControl.Location="{x:Bind BellevueLocation}"/>
  </maps:MapItemsControl>
</maps:MapControl>
```

<span data-ttu-id="61454-195">In diesem Beispiel wird eine Sammlung von XAML-Elementen angezeigt, die an [**MapItemsControl**](https://msdn.microsoft.com/library/windows/apps/dn637094) gebunden sind.</span><span class="sxs-lookup"><span data-stu-id="61454-195">This example displays a collection of XAML elements bound to a [**MapItemsControl**](https://msdn.microsoft.com/library/windows/apps/dn637094).</span></span>

```xml
<maps:MapControl x:Name="MapControl" MapTapped="MapTapped" MapDoubleTapped="MapTapped" MapHolding="MapTapped">
  <maps:MapItemsControl ItemsSource="{x:Bind LandmarkOverlays}">
      <maps:MapItemsControl.ItemTemplate>
          <DataTemplate>
              <StackPanel Background="Black" Tapped ="Overlay_Tapped">
                  <TextBlock maps:MapControl.Location="{Binding Location}" Text="{Binding Title}"
                    maps:MapControl.NormalizedAnchorPoint="0.5,0.5" FontSize="20" Margin="5"/>
              </StackPanel>
          </DataTemplate>
      </maps:MapItemsControl.ItemTemplate>
  </maps:MapItemsControl>
</maps:MapControl>
```

<span data-ttu-id="61454-196">Die Eigenschaft ``ItemsSource`` im obigen Beispiel ist in der CodeBehind-Datei an eine Eigenschaft vom Typ [IList](https://docs.microsoft.com/dotnet/api/system.collections.ilist?view=netframework-4.70) gebunden.</span><span class="sxs-lookup"><span data-stu-id="61454-196">The ``ItemsSource`` property in the example above is bound to a property of type [IList](https://docs.microsoft.com/dotnet/api/system.collections.ilist?view=netframework-4.70) in the code-behind file.</span></span>

```csharp
public sealed partial class Scenario1 : Page
{
    public IList LandmarkOverlays { get; set; }

    public MyClassConstructor()
    {
         SetLandMarkLocations();
         this.InitializeComponent();   
    }

    private void SetLandMarkLocations()
    {
        LandmarkOverlays = new List<MapElement>();

        var pikePlaceIcon = new MapIcon
        {
            Location = new Geopoint(new BasicGeoposition
            { Latitude = 47.610, Longitude = -122.342 }),
            Title = "Pike Place Market"
        };

        LandmarkOverlays.Add(pikePlaceIcon);

        var SeattleSpaceNeedleIcon = new MapIcon
        {
            Location = new Geopoint(new BasicGeoposition
            { Latitude = 47.6205, Longitude = -122.3493 }),
            Title = "Seattle Space Needle"
        };

        LandmarkOverlays.Add(SeattleSpaceNeedleIcon);
    }
}
```

<a id="layers" />

## <a name="working-with-layers"></a><span data-ttu-id="61454-197">Arbeiten mit Schichten</span><span class="sxs-lookup"><span data-stu-id="61454-197">Working with layers</span></span>

<span data-ttu-id="61454-198">In den Beispielen dieser Anleitung werden einer [MapElementLayers](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapelementslayer)-Sammlung Elemente hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="61454-198">The examples in this guide add elements to a [MapElementLayers](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapelementslayer) collection.</span></span> <span data-ttu-id="61454-199">Dann zeigen sie, wie diese Sammlung der Eigenschaft **Layers** des Kartensteuerelements hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="61454-199">Then they show how to add that collection to the **Layers** property of the map control.</span></span> <span data-ttu-id="61454-200">In früheren Versionen wurde in dieser Anleitung gezeigt, wie Sie wie folgt der [**MapElements**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapcontrol.MapElements)-Sammlung Kartenelemente hinzufügen können:</span><span class="sxs-lookup"><span data-stu-id="61454-200">In previous releases, this guide showed you how to add map elements to the [**MapElements**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapcontrol.MapElements) collection as follows:</span></span>

```csharp
var pikePlaceIcon = new MapIcon
{
    Location = new Geopoint(new BasicGeoposition
    { Latitude = 47.610, Longitude = -122.342 }),
    NormalizedAnchorPoint = new Point(0.5, 1.0),
    ZIndex = 0,
    Title = "Pike Place Market"
};

myMap.MapElements.Add(pikePlaceIcon);
```

<span data-ttu-id="61454-201">Sie können diesen Ansatz weiterhin verwenden, doch werden Ihnen dann einige der Vorteile des neuen Kartenschichtenmodells nicht zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="61454-201">While you can still use this approach, you'll miss out on some of the advantages of the new map layer model.</span></span> <span data-ttu-id="61454-202">Durch die Gruppierung der Elemente in Schichten können Sie jede davon unabhängig bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="61454-202">By grouping your elements into layers, you can manipulate each layer independently from one another.</span></span> <span data-ttu-id="61454-203">Beispielsweise hat jede Ebene einen eigenen Satz an Ereignissen, sodass Sie auf ein Ereignis in einer bestimmten Ebene antworten und eine Aktion ausführen, die speziell für das Ereignis gilt.</span><span class="sxs-lookup"><span data-stu-id="61454-203">For example, each layer has it's own set of events so you can respond to an event on a specific layer and perform an action specific to that event.</span></span>

<span data-ttu-id="61454-204">Zudem können Sie XAML direkt an eine [MapLayer](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.maplayer) binden.</span><span class="sxs-lookup"><span data-stu-id="61454-204">Also, you can bind XAML directly to a [MapLayer](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.maplayer).</span></span> <span data-ttu-id="61454-205">Das ist mit der [MapElements](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapcontrol.MapElements)-Sammlung nicht möglich.</span><span class="sxs-lookup"><span data-stu-id="61454-205">This is something that you can't do by using the [MapElements](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapcontrol.MapElements)  collection.</span></span>

<span data-ttu-id="61454-206">Eine Möglichkeit besteht darin, eine Ansichtsmodellklasse, CodeBehind für eine XAML-Seite und eine XAML-Seite zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="61454-206">One way you could do this is by using a view model class, code-behind a XAML page, and a XAML page.</span></span>

### <a name="view-model-class"></a><span data-ttu-id="61454-207">Ansichtsmodellklasse</span><span class="sxs-lookup"><span data-stu-id="61454-207">View model class</span></span>

```csharp
public class LandmarksViewModel
{
    public ObservableCollection<MapLayer> LandmarkLayer
        { get; } = new ObservableCollection<MapLayer>();

    public LandmarksViewModel()
    {
        var MyElements = new List<MapElement>();

        var pikePlaceIcon = new MapIcon
        {
            Location = new Geopoint(new BasicGeoposition
            { Latitude = 47.610, Longitude = -122.342 }),
            Title = "Pike Place Market"
        };

        MyElements.Add(pikePlaceIcon);

        var LandmarksLayer = new MapElementsLayer
        {
            ZIndex = 1,
            MapElements = MyElements
        };

        LandmarkLayer.Add(LandmarksLayer);         
    }

```

### <a name="code-behind-a-xaml-page"></a><span data-ttu-id="61454-208">CodeBehind für eine XAML-Seite</span><span class="sxs-lookup"><span data-stu-id="61454-208">Code-behind a XAML page</span></span>

<span data-ttu-id="61454-209">Verknüpfen Sie die Ansichtsmodellklasse mit der CodeBehind-Seite.</span><span class="sxs-lookup"><span data-stu-id="61454-209">Connect the view model class to your code behind page.</span></span>

```csharp
public LandmarksViewModel ViewModel { get; set; }

public myMapPage()
{
    this.InitializeComponent();
    this.ViewModel = new LandmarksViewModel();
}
```

### <a name="xaml-page"></a><span data-ttu-id="61454-210">XAML-Seite</span><span class="sxs-lookup"><span data-stu-id="61454-210">XAML page</span></span>

<span data-ttu-id="61454-211">Binden Sie in der XAML-Seite die Eigenschaft aus der Ansichtsmodellklasse, die die Ebene zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="61454-211">In your XAML page, bind to the property in your view model class that returns the layer.</span></span>

```XML
<maps:MapControl
    x:Name="myMap" TransitFeaturesVisible="False" Loaded="MyMap_Loaded" Grid.Row="2"
    MapServiceToken="Your token" Layers="{x:Bind ViewModel.LandmarkLayer}"/>
```

## <a name="related-topics"></a><span data-ttu-id="61454-212">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="61454-212">Related topics</span></span>

* [<span data-ttu-id="61454-213">Bing Maps Developer Center</span><span class="sxs-lookup"><span data-stu-id="61454-213">Bing Maps Developer Center</span></span>](https://www.bingmapsportal.com/)
* [<span data-ttu-id="61454-214">Beispiel für UWP-Karte</span><span class="sxs-lookup"><span data-stu-id="61454-214">UWP map sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=619977)
* [<span data-ttu-id="61454-215">Entwurfsrichtlinien für Karten</span><span class="sxs-lookup"><span data-stu-id="61454-215">Design guidelines for maps</span></span>](https://msdn.microsoft.com/library/windows/apps/dn596102)
* [<span data-ttu-id="61454-216">Build 2015-Video: Nutzen von Karten und Ortung über Telefon, Tablet und PC in Ihren Windows-Apps</span><span class="sxs-lookup"><span data-stu-id="61454-216">Build 2015 video: Leveraging Maps and Location Across Phone, Tablet, and PC in Your Windows Apps</span></span>](https://channel9.msdn.com/Events/Build/2015/2-757)
* [<span data-ttu-id="61454-217">Beispiel für eine UWP-App mit Verkehrsinformationen</span><span class="sxs-lookup"><span data-stu-id="61454-217">UWP traffic app sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=619982)
* [**<span data-ttu-id="61454-218">MapIcon</span><span class="sxs-lookup"><span data-stu-id="61454-218">MapIcon</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn637077)
* [**<span data-ttu-id="61454-219">MapPolygon</span><span class="sxs-lookup"><span data-stu-id="61454-219">MapPolygon</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn637103)
* [**<span data-ttu-id="61454-220">MapPolyline</span><span class="sxs-lookup"><span data-stu-id="61454-220">MapPolyline</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn637114)
