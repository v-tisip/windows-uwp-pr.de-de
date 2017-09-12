---
author: normesta
title: Anzeigen von interessanten Orten (POI) auf einer Karte
description: "Mit Ortsmarken, Bildern, Formen und XAML-UI-Elementen können Sie interessante Orte (Points of Interest, POI) auf einer Karte hinzufügen."
ms.assetid: CA00D8EB-6C1B-4536-8921-5EAEB9B04FCA
ms.author: normesta
ms.date: 08/02/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, uwp, karten, standort, ortsmarken
ms.openlocfilehash: 280a651df949018dc9cf490e14d72d167fee0858
ms.sourcegitcommit: 0ebc8dca2fd9149ea163b7db9daa14520fc41db4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2017
---
# <a name="display-points-of-interest-poi-on-a-map"></a><span data-ttu-id="5981f-104">Anzeigen von interessanten Orten (POI) auf einer Karte</span><span class="sxs-lookup"><span data-stu-id="5981f-104">Display points of interest (POI) on a map</span></span>


<span data-ttu-id="5981f-105">\[ Aktualisiert für UWP-Apps unter Windows 10.</span><span class="sxs-lookup"><span data-stu-id="5981f-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="5981f-106">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132). \]</span><span class="sxs-lookup"><span data-stu-id="5981f-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>


<span data-ttu-id="5981f-107">Mit Ortsmarken, Bildern, Formen und XAML-UI-Elementen können Sie interessante Orte (Points of Interest, POI) auf einer Karte hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="5981f-107">Add points of interest (POI) to a map using pushpins, images, shapes, and XAML UI elements.</span></span> <span data-ttu-id="5981f-108">Ein POI ist ein Punkt auf der Karte, der Orte angibt, die von Interesse sind.</span><span class="sxs-lookup"><span data-stu-id="5981f-108">A POI is a specific point on the map that represents something of interest.</span></span> <span data-ttu-id="5981f-109">Beispiele sind die Position eines Geschäfts, eines Orts oder eines Freundes.</span><span class="sxs-lookup"><span data-stu-id="5981f-109">For example, the location of a business, city, or friend.</span></span>

<span data-ttu-id="5981f-110">**Tipp:** Um mehr über das Anzeigen von interessanten Orten in Ihrer App zu erfahren, laden Sie das folgende Beispiel aus dem [Repository Beispiele für Universelle Windows-Plattform](http://go.microsoft.com/fwlink/p/?LinkId=619979) auf GitHub herunter.</span><span class="sxs-lookup"><span data-stu-id="5981f-110">**Tip** To learn more about displaying POI on your app, download the following sample from the [Windows-universal-samples repo](http://go.microsoft.com/fwlink/p/?LinkId=619979) on GitHub.</span></span>

-   [<span data-ttu-id="5981f-111">Kartenbeispiel für die Universelle Windows-Plattform (UWP)</span><span class="sxs-lookup"><span data-stu-id="5981f-111">Universal Windows Platform (UWP) map sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=619977)

<span data-ttu-id="5981f-112">Zeigen Sie Ortsmarken, Bilder und Formen auf der Karte an, indem Sie [**MapIcon**](https://msdn.microsoft.com/library/windows/apps/dn637077)-, [**MapPolygon**](https://msdn.microsoft.com/library/windows/apps/dn637103)- und [**MapPolyline**](https://msdn.microsoft.com/library/windows/apps/dn637114)-Objekte zur Sammlung [**MapElements**](https://msdn.microsoft.com/library/windows/apps/dn637033) der Kartensteuerung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="5981f-112">Display pushpins, images, and shapes on the map by adding [**MapIcon**](https://msdn.microsoft.com/library/windows/apps/dn637077), [**MapPolygon**](https://msdn.microsoft.com/library/windows/apps/dn637103), and [**MapPolyline**](https://msdn.microsoft.com/library/windows/apps/dn637114) objects to the [**MapElements**](https://msdn.microsoft.com/library/windows/apps/dn637033) collection of the map control.</span></span> <span data-ttu-id="5981f-113">Verwenden Sie Datenbindung, oder fügen Sie Elemente programmgesteuert hinzu. Eine deklarative Bindung an die Sammlung **MapElements** im XAML-Markup ist nicht möglich.</span><span class="sxs-lookup"><span data-stu-id="5981f-113">Use data binding or add items programmatically; you can't bind to the **MapElements** collection declaratively in your XAML markup.</span></span>

<span data-ttu-id="5981f-114">Zeigen Sie XAML-UI-Elemente wie [**Button**](https://msdn.microsoft.com/library/windows/apps/br209265), [**HyperlinkButton**](https://msdn.microsoft.com/library/windows/apps/br242739) oder [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652) auf der Karte an, indem Sie diese als [**Children**](https://msdn.microsoft.com/library/windows/apps/dn637008) von [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004) hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="5981f-114">Display XAML user interface elements such as a [**Button**](https://msdn.microsoft.com/library/windows/apps/br209265), a [**HyperlinkButton**](https://msdn.microsoft.com/library/windows/apps/br242739), or a [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652) on the map by adding them as [**Children**](https://msdn.microsoft.com/library/windows/apps/dn637008) of the [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004).</span></span> <span data-ttu-id="5981f-115">Sie können sie auch zu [**MapItemsControl**](https://msdn.microsoft.com/library/windows/apps/dn637094) hinzufügen oder **MapItemsControl** an eine Sammlung von Elementen binden.</span><span class="sxs-lookup"><span data-stu-id="5981f-115">You can also add them to the [**MapItemsControl**](https://msdn.microsoft.com/library/windows/apps/dn637094), or bind the **MapItemsControl** to a collection of items.</span></span>

<span data-ttu-id="5981f-116">Zusammenfassung:</span><span class="sxs-lookup"><span data-stu-id="5981f-116">In summary:</span></span>

-   <span data-ttu-id="5981f-117">[Fügen Sie der Karte ein MapIcon hinzu](#mapicon), um ein Bild anzuzeigen, z. B. eine Ortsmarke mit optionalem Text.</span><span class="sxs-lookup"><span data-stu-id="5981f-117">[Add a MapIcon to the map](#mapicon) to display an image such as a pushpin with optional text.</span></span>
-   <span data-ttu-id="5981f-118">[Fügen Sie der Karte ein MapPolygon hinzu](#mappolygon), um eine Form mit mehreren Punkten anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="5981f-118">[Add a MapPolygon to the map](#mappolygon) to display a multi-point shape.</span></span>
-   <span data-ttu-id="5981f-119">[Fügen Sie der Karte eine MapPolyline hinzu](#mappolyline), um Linien auf der Karte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="5981f-119">[Add a MapPolyline to the map](#mappolyline) to display lines on the map.</span></span>
-   <span data-ttu-id="5981f-120">[Fügen Sie der Karte XAML hinzu](#mapxaml), um benutzerdefinierte UI-Elemente anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="5981f-120">[Add XAML to the map](#mapxaml) to display custom UI elements.</span></span>

<span data-ttu-id="5981f-121">Wenn Sie eine große Anzahl von Elementen auf der Karte platzieren möchten, sollten Sie [nebeneinander angeordnete Bilder auf der Karte überlagern](overlay-tiled-images.md).</span><span class="sxs-lookup"><span data-stu-id="5981f-121">If you have a large number of elements to place on the map, consider [overlaying tiled images on the map](overlay-tiled-images.md).</span></span> <span data-ttu-id="5981f-122">Informationen zum Anzeigen von Straßen auf der Karte finden Sie unter [Anzeigen von Routen und Wegbeschreibungen](routes-and-directions.md).</span><span class="sxs-lookup"><span data-stu-id="5981f-122">To display roads on the map, see [Display routes and directions](routes-and-directions.md).</span></span>

## <a name="add-a-mapicon"></a><span data-ttu-id="5981f-123">Hinzufügen eines MapIcon</span><span class="sxs-lookup"><span data-stu-id="5981f-123">Add a MapIcon</span></span>


<span data-ttu-id="5981f-124">Verwenden Sie die Klasse [**MapIcon**](https://msdn.microsoft.com/library/windows/apps/dn637077), um Bilder wie eine Ortsmarke mit optionalem Text auf der Karte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="5981f-124">Display an image such a pushpin, with optional text, on the map by using the [**MapIcon**](https://msdn.microsoft.com/library/windows/apps/dn637077) class.</span></span> <span data-ttu-id="5981f-125">Sie können das Standardbild akzeptieren oder mit der [**Image**](https://msdn.microsoft.com/library/windows/apps/dn637078)-Eigenschaft ein benutzerdefiniertes Bild bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="5981f-125">You can accept the default image or provide a custom image by using the [**Image**](https://msdn.microsoft.com/library/windows/apps/dn637078) property.</span></span> <span data-ttu-id="5981f-126">Die folgende Abbildung zeigt das Standardbild für ein **MapIcon** ohne festgelegten Wert für die Eigenschaft [**Title**](https://msdn.microsoft.com/library/windows/apps/dn637088) mit einem kurzen Titel, einem langen Titel und einem sehr langen Titel.</span><span class="sxs-lookup"><span data-stu-id="5981f-126">The following image displays the default image for a **MapIcon** with no value specified for the [**Title**](https://msdn.microsoft.com/library/windows/apps/dn637088) property, with a short title, with a long title, and with a very long title.</span></span>

![Beispiel für MapIcon mit Titeln unterschiedlicher Länge](images/mapctrl-mapicons.png)

<span data-ttu-id="5981f-128">Im folgenden Beispiel wird einer Karte von Seattle ein [**MapIcon**](https://msdn.microsoft.com/library/windows/apps/dn637077) mit Standardbild und optionalem Titel hinzugefügt, um den Standort der Space Needle anzugeben.</span><span class="sxs-lookup"><span data-stu-id="5981f-128">The following example shows a map of the city of Seattle and adds a [**MapIcon**](https://msdn.microsoft.com/library/windows/apps/dn637077) with the default image and an optional title to indicate the location of the Space Needle.</span></span> <span data-ttu-id="5981f-129">Außerdem wird die Karte auf dem Symbol zentriert und vergrößert.</span><span class="sxs-lookup"><span data-stu-id="5981f-129">It also centers the map over the icon and zooms in.</span></span> <span data-ttu-id="5981f-130">Allgemeine Informationen zur Verwendung des Kartensteuerelements finden Sie unter [Anzeigen von Karten mit 2D-, 3D- und Streetside-Ansichten](display-maps.md).</span><span class="sxs-lookup"><span data-stu-id="5981f-130">For general info about using the map control, see [Display maps with 2D, 3D, and Streetside views](display-maps.md).</span></span>

```csharp
      private void displayPOIButton_Click(object sender, RoutedEventArgs e)
      {
         // Specify a known location.
         BasicGeoposition snPosition = new BasicGeoposition() { Latitude = 47.620, Longitude = -122.349 };
         Geopoint snPoint = new Geopoint(snPosition);

         // Create a MapIcon.
         var mapIcon1 = new MapIcon
         {
             Location = snPoint,
             NormalizedAnchorPoint = new Point(0.5, 1.0),
             Title = "Space Needle",
             ZIndex = 0,
         };

         // Add the MapIcon to the map.
         myMap.MapElements.Add(mapIcon1);

         // Center the map over the POI.
         myMap.Center = snPoint;
         myMap.ZoomLevel = 14;
      }
```

<span data-ttu-id="5981f-131">In diesem Beispiel wird der folgende interessante Ort (POI) auf der Karte angezeigt (mit dem Standardbild in der Mitte).</span><span class="sxs-lookup"><span data-stu-id="5981f-131">This example displays the following POI on the map (the default image in the center).</span></span>

![Karte mit MapIcon](images/displaypoidefault.png)

<span data-ttu-id="5981f-133">Die folgende Codezeile zeigt [**MapIcon**](https://msdn.microsoft.com/library/windows/apps/dn637077) mit einem benutzerdefinierten Bild an, das im Ordner „Assets“ (Ressourcen) des Projekts gespeichert wurde.</span><span class="sxs-lookup"><span data-stu-id="5981f-133">The following line of code displays the [**MapIcon**](https://msdn.microsoft.com/library/windows/apps/dn637077) with a custom image saved in the Assets folder of the project.</span></span> <span data-ttu-id="5981f-134">Die Eigenschaft [**Image**](https://msdn.microsoft.com/library/windows/apps/dn637078) von **MapIcon** erwartet einen Wert vom Typ [**RandomAccessStreamReference**](https://msdn.microsoft.com/library/windows/apps/hh701813).</span><span class="sxs-lookup"><span data-stu-id="5981f-134">The [**Image**](https://msdn.microsoft.com/library/windows/apps/dn637078) property of the **MapIcon** expects a value of type [**RandomAccessStreamReference**](https://msdn.microsoft.com/library/windows/apps/hh701813).</span></span> <span data-ttu-id="5981f-135">Dieser Typ erfordert die Anweisung **using** für den Namespace [**Windows.Storage.Streams**](https://msdn.microsoft.com/library/windows/apps/br241791).</span><span class="sxs-lookup"><span data-stu-id="5981f-135">This type requires a **using** statement for the [**Windows.Storage.Streams**](https://msdn.microsoft.com/library/windows/apps/br241791) namespace.</span></span>

<span data-ttu-id="5981f-136">**Tipp** Wenn Sie dasselbe Bild für mehrere Kartensymbole verwenden, deklarieren Sie [**RandomAccessStreamReference**](https://msdn.microsoft.com/library/windows/apps/hh701813) auf Seiten- oder App-Ebene, um eine optimale Leistung zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="5981f-136">**Tip** If you use the same image for multiple map icons, declare the [**RandomAccessStreamReference**](https://msdn.microsoft.com/library/windows/apps/hh701813) at the page or app level for the best performance.</span></span>

```csharp
    MapIcon1.Image =
        RandomAccessStreamReference.CreateFromUri(new Uri("ms-appx:///Assets/customicon.png"));
```

<span data-ttu-id="5981f-137">Berücksichtigen Sie beim Arbeiten mit der [**MapIcon**](https://msdn.microsoft.com/library/windows/apps/dn637077)-Klasse Folgendes:</span><span class="sxs-lookup"><span data-stu-id="5981f-137">Keep these considerations in mind when working with the [**MapIcon**](https://msdn.microsoft.com/library/windows/apps/dn637077) class:</span></span>

-   <span data-ttu-id="5981f-138">Die [**Image**](https://msdn.microsoft.com/library/windows/apps/dn637078)-Eigenschaft unterstützt eine maximale Bildgröße von 2048x2048Pixeln.</span><span class="sxs-lookup"><span data-stu-id="5981f-138">The [**Image**](https://msdn.microsoft.com/library/windows/apps/dn637078) property supports a maximum image size of 2048×2048 pixels.</span></span>
-   <span data-ttu-id="5981f-139">Standardmäßig wird die Anzeige des Bilds für das Kartensymbol nicht garantiert.</span><span class="sxs-lookup"><span data-stu-id="5981f-139">By default, the map icon's image is not guaranteed to be shown.</span></span> <span data-ttu-id="5981f-140">Es wird möglicherweise ausgeblendet, wenn es andere Elemente oder Bezeichnungen auf der Karte verdeckt.</span><span class="sxs-lookup"><span data-stu-id="5981f-140">It may be hidden when it obscures other elements or labels on the map.</span></span> <span data-ttu-id="5981f-141">Damit es sichtbar bleibt, legen Sie die [**CollisionBehaviorDesired**](https://msdn.microsoft.com/library/windows/apps/dn974327)-Eigenschaft des Kartensymbols auf [**MapElementCollisionBehavior.RemainVisible**](https://msdn.microsoft.com/library/windows/apps/dn974314) fest.</span><span class="sxs-lookup"><span data-stu-id="5981f-141">To keep it visible, set the map icon's [**CollisionBehaviorDesired**](https://msdn.microsoft.com/library/windows/apps/dn974327) property to [**MapElementCollisionBehavior.RemainVisible**](https://msdn.microsoft.com/library/windows/apps/dn974314).</span></span>
-   <span data-ttu-id="5981f-142">Die Anzeige des optionalen [**Title**](https://msdn.microsoft.com/library/windows/apps/dn637088) für [**MapIcon**](https://msdn.microsoft.com/library/windows/apps/dn637077) wird nicht garantiert.</span><span class="sxs-lookup"><span data-stu-id="5981f-142">The optional [**Title**](https://msdn.microsoft.com/library/windows/apps/dn637088) of the [**MapIcon**](https://msdn.microsoft.com/library/windows/apps/dn637077) is not guaranteed to be shown.</span></span> <span data-ttu-id="5981f-143">Wenn der Text nicht angezeigt wird, verkleinern Sie die Ansicht, indem Sie den Wert der [**ZoomLevel**](https://msdn.microsoft.com/library/windows/apps/dn637068)-Eigenschaft von [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004) verringern.</span><span class="sxs-lookup"><span data-stu-id="5981f-143">If you don't see the text, zoom out by decreasing the value of the [**ZoomLevel**](https://msdn.microsoft.com/library/windows/apps/dn637068) property of the [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004).</span></span>
-   <span data-ttu-id="5981f-144">Wenn Sie ein [**MapIcon**](https://msdn.microsoft.com/library/windows/apps/dn637077)-Bild anzeigen, das auf eine bestimmte Position auf der Karte hinweist, z.B. eine Ortsmarkierung oder ein Pfeil, sollten Sie in Erwägung ziehen, den Wert der [**NormalizedAnchorPoint**](https://msdn.microsoft.com/library/windows/apps/dn637082)-Eigenschaft auf den ungefähren Standort des Zeigers auf dem Bild festzulegen.</span><span class="sxs-lookup"><span data-stu-id="5981f-144">When you display a [**MapIcon**](https://msdn.microsoft.com/library/windows/apps/dn637077) image that points to a specific location on the map - for example, a pushpin or an arrow - consider setting the value of the [**NormalizedAnchorPoint**](https://msdn.microsoft.com/library/windows/apps/dn637082) property to the approximate location of the pointer on the image.</span></span> <span data-ttu-id="5981f-145">Wenn Sie den Wert von **NormalizedAnchorPoint** beim Standardwert (0, 0) belassen, der die obere linke Ecke des Bilds darstellt, führen Änderungen am [**ZoomLevel**](https://msdn.microsoft.com/library/windows/apps/dn637068) der Karte möglicherweise dazu, dass das Bild auf eine andere Position zeigt.</span><span class="sxs-lookup"><span data-stu-id="5981f-145">If you leave the value of **NormalizedAnchorPoint** at its default value of (0, 0), which represents the upper left corner of the image, changes in the [**ZoomLevel**](https://msdn.microsoft.com/library/windows/apps/dn637068) of the map may leave the image pointing to a different location.</span></span>

## <a name="add-a-mapbillboard"></a><span data-ttu-id="5981f-146">Ein MapBillboard hinzufügen</span><span class="sxs-lookup"><span data-stu-id="5981f-146">Add a MapBillboard</span></span>

<span data-ttu-id="5981f-147">Zeigen Sie große Bilder an, die im Zusammenhang mit Kartenpositionen (z.B. ein Bild von einem Restaurant oder einer Sehenswürdigkeit) stehen.</span><span class="sxs-lookup"><span data-stu-id="5981f-147">Display large images that relate to map locations such as a picture of a restaurant or a landmark.</span></span> <span data-ttu-id="5981f-148">Wenn der Benutzer verkleinert, wird das Bild proportional größer, damit der Benutzer mehr von der Karte anzeigen kann.</span><span class="sxs-lookup"><span data-stu-id="5981f-148">As users zoom out, the image will shrink proportionally in size to enable the user to view more of the map.</span></span> <span data-ttu-id="5981f-149">Dies ist etwas anders als ein [**MapIcon**](https://msdn.microsoft.com/library/windows/apps/dn637077), das einen bestimmten Ort kennzeichnet. Es ist in der Regel klein und bleibt bei der gleichen Größe wenn der Benutzer eine Karte verkleinert.</span><span class="sxs-lookup"><span data-stu-id="5981f-149">This is a bit different than a [**MapIcon**](https://msdn.microsoft.com/library/windows/apps/dn637077) which marks a specific location, is typically small, and remains the same size as users zoom in and out of a map.</span></span>

![MapBillboard-Bild](images/map-billboard.png)

<span data-ttu-id="5981f-151">Der folgende Code zeigt das [**MapBillboard**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard) in der Abbildungoben.</span><span class="sxs-lookup"><span data-stu-id="5981f-151">The following code shows the [**MapBillboard**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard) presented in the image above.</span></span>

```csharp
private void mapBillboardAddButton_Click(object sender, Windows.UI.Xaml.RoutedEventArgs e)
{
    RandomAccessStreamReference mapBillboardStreamReference =
        RandomAccessStreamReference.CreateFromUri(new Uri("ms-appx:///Assets/billboard.jpg"));

        var mapBillboard = new MapBillboard(myMap.ActualCamera)
        {
            Location = myMap.Center,
            NormalizedAnchorPoint = new Point(0.5, 1.0),
            Image = mapBillboardStreamReference
        };

        myMap.MapElements.Add(mapBillboard);
}
```
<span data-ttu-id="5981f-152">Drei Teile dieses Codes sollten ein bisschen näher untersucht werden: das Bild, die Referenzkamera und die [**NormalizedAnchorPoint**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard#Windows_UI_Xaml_Controls_Maps_MapBillboard_NormalizedAnchorPoint)-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="5981f-152">There's three parts of this code worth examining a little closer: The image, the reference camera, and the [**NormalizedAnchorPoint**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard#Windows_UI_Xaml_Controls_Maps_MapBillboard_NormalizedAnchorPoint) property.</span></span>

### <a name="image"></a><span data-ttu-id="5981f-153">Bild</span><span class="sxs-lookup"><span data-stu-id="5981f-153">Image</span></span>

<span data-ttu-id="5981f-154">In diesem Beispiel wird ein benutzerdefiniertes Bild im **Assets** Ordner des Projekts gespeichert.</span><span class="sxs-lookup"><span data-stu-id="5981f-154">This example shows a custom image saved in the **Assets** folder of the project.</span></span> <span data-ttu-id="5981f-155">Die Eigenschaft [**Image**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard#Windows_UI_Xaml_Controls_Maps_MapBillboard_Image) von [**MapBillboard**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard) erwartet einen Wert vom Typ [**RandomAccessStreamReference**](https://msdn.microsoft.com/library/windows/apps/hh701813).</span><span class="sxs-lookup"><span data-stu-id="5981f-155">The [**Image**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard#Windows_UI_Xaml_Controls_Maps_MapBillboard_Image) property of the [**MapBillboard**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard) expects a value of type [**RandomAccessStreamReference**](https://msdn.microsoft.com/library/windows/apps/hh701813).</span></span> <span data-ttu-id="5981f-156">Dieser Typ erfordert die Anweisung **using** für den Namespace [**Windows.Storage.Streams**](https://msdn.microsoft.com/library/windows/apps/br241791).</span><span class="sxs-lookup"><span data-stu-id="5981f-156">This type requires a **using** statement for the [**Windows.Storage.Streams**](https://msdn.microsoft.com/library/windows/apps/br241791) namespace.</span></span>

>[!NOTE]
><span data-ttu-id="5981f-157">Wenn Sie dasselbe Bild für mehrere Kartensymbole verwenden, deklarieren Sie [**RandomAccessStreamReference**](https://msdn.microsoft.com/library/windows/apps/hh701813) auf Seiten- oder App-Ebene, um eine optimale Leistung zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="5981f-157">If you use the same image for multiple map icons, declare the [**RandomAccessStreamReference**](https://msdn.microsoft.com/library/windows/apps/hh701813) at the page or app level for the best performance.</span></span>

### <a name="reference-camera"></a><span data-ttu-id="5981f-158">Referenzkamera</span><span class="sxs-lookup"><span data-stu-id="5981f-158">Reference camera</span></span>

 <span data-ttu-id="5981f-159">Da ein [**MapBillboard**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard)-Bild skaliert sobald sich das [**ZoomLevel**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapcontrol#Windows_UI_Xaml_Controls_Maps_MapControl_ZoomLevel) der Karte ändert, es ist wichtig zu definieren, bei welchem [**ZoomLevel**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapcontrol#Windows_UI_Xaml_Controls_Maps_MapControl_ZoomLevel) das Bild mit einer normalen 1x-Skalierung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="5981f-159">Because a [**MapBillboard**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard) image scales in and out as the [**ZoomLevel**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapcontrol#Windows_UI_Xaml_Controls_Maps_MapControl_ZoomLevel) of the map changes, it's important to define where in that [**ZoomLevel**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapcontrol#Windows_UI_Xaml_Controls_Maps_MapControl_ZoomLevel) the image appears at a normal 1x scale.</span></span> <span data-ttu-id="5981f-160">Die Position ist in der Referenzkamera des [**MapBillboard**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard) definiert. Um sie festzulegen müssen Sie ein [**MapCamera**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapcamera) Objekt an den Konstruktor des [**MapBillboard**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard) übergeben.</span><span class="sxs-lookup"><span data-stu-id="5981f-160">That position is defined in the reference camera of the [**MapBillboard**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard), and to set it, you'll have to pass a [**MapCamera**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapcamera) object into the constructor of the [**MapBillboard**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard).</span></span>

 <span data-ttu-id="5981f-161">Können Sie die gewünschte Position in einem [**Geopoint**](https://docs.microsoft.com/uwp/api/windows.devices.geolocation.geopoint) definieren, und diesen [**Geopoint**](https://docs.microsoft.com/uwp/api/windows.devices.geolocation.geopoint) zum Erstellen eines [**MapCamera**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapcamera) Objekts verwenden.</span><span class="sxs-lookup"><span data-stu-id="5981f-161">You can define the position that you want in a [**Geopoint**](https://docs.microsoft.com/uwp/api/windows.devices.geolocation.geopoint), and then use that [**Geopoint**](https://docs.microsoft.com/uwp/api/windows.devices.geolocation.geopoint) to create a [**MapCamera**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapcamera) object.</span></span>  <span data-ttu-id="5981f-162">In diesem Beispiel verwenden wir jedoch das [**MapCamera**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapcamera)Objekt, das von der [**ActualCamera**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapcontrol#Windows_UI_Xaml_Controls_Maps_MapControl_ActualCamera)-Eigenschaft des Kartensteuerelements zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="5981f-162">However, in this example, we're just using the [**MapCamera**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapcamera) object returned by the [**ActualCamera**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapcontrol#Windows_UI_Xaml_Controls_Maps_MapControl_ActualCamera) property of the map control.</span></span> <span data-ttu-id="5981f-163">Hierbei handelt es sich um die interne Kamera der Karte.</span><span class="sxs-lookup"><span data-stu-id="5981f-163">This is the map's internal camera.</span></span> <span data-ttu-id="5981f-164">Die aktuelle Position der Kamera wird die Referenzkameraposition (die Position, in der das [**MapBillboard**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard) Bild mit 1x Skalierung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="5981f-164">The current position of that camera becomes the reference camera position; the position where the [**MapBillboard**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard) image appears at 1x scale.</span></span>

 <span data-ttu-id="5981f-165">Wenn Ihre App den Benutzern die Möglichkeit gibt, die Karte zu verkleinern, verringert das Bild die Größe, da die interne Kamera der Karte steigt während das Bild bei der 1x-Skalierung an der Referenzkameraposition verbleibt.</span><span class="sxs-lookup"><span data-stu-id="5981f-165">If your app gives users the ability to zoom out on the map, the image decreases in size because the maps internal camera is rising in altitude while the image at 1x scale remains fixed at the reference camera's position.</span></span>

### <a name="normalizedanchorpoint"></a><span data-ttu-id="5981f-166">NormalizedAnchorPoint</span><span class="sxs-lookup"><span data-stu-id="5981f-166">NormalizedAnchorPoint</span></span>

<span data-ttu-id="5981f-167">Der [**NormalizedAnchorPoint**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard#Windows_UI_Xaml_Controls_Maps_MapBillboard_NormalizedAnchorPoint) ist der Punkt des Bilds, das an der [**Speicherort**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard#Windows_UI_Xaml_Controls_Maps_MapBillboard_Location) Eigenschaft des [**MapBillboard**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard) verankert ist.</span><span class="sxs-lookup"><span data-stu-id="5981f-167">The [**NormalizedAnchorPoint**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard#Windows_UI_Xaml_Controls_Maps_MapBillboard_NormalizedAnchorPoint) is the point of the image that is anchored to the [**Location**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard#Windows_UI_Xaml_Controls_Maps_MapBillboard_Location) property of the [**MapBillboard**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard).</span></span> <span data-ttu-id="5981f-168">Der Punkt 0,5,1 ist die untere Mitte des Bilds.</span><span class="sxs-lookup"><span data-stu-id="5981f-168">The point 0.5,1 is the bottom center of the image.</span></span> <span data-ttu-id="5981f-169">Da wir die [**Location**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard#Windows_UI_Xaml_Controls_Maps_MapBillboard_Location) Eigenschaft des [**MapBillboard**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard)auf die untere Mitte des Kartensteuerelements festgelegt haben, wir die untere Mitte des Bilds an der unteren Mitte des Kartensteuerelements verankert.</span><span class="sxs-lookup"><span data-stu-id="5981f-169">Because we've set the [**Location**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard#Windows_UI_Xaml_Controls_Maps_MapBillboard_Location) property of the [**MapBillboard**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard) to the center of the map's control, the bottom center of the image will be anchored at the center of the maps control.</span></span>

## <a name="add-a-mappolygon"></a><span data-ttu-id="5981f-170">Hinzufügen eines MapPolygon</span><span class="sxs-lookup"><span data-stu-id="5981f-170">Add a MapPolygon</span></span>

<span data-ttu-id="5981f-171">Mithilfe der Klasse [**MapPolygon**](https://msdn.microsoft.com/library/windows/apps/dn637103) können Sie eine Form mit mehreren Punkten auf der Karte anzeigen.</span><span class="sxs-lookup"><span data-stu-id="5981f-171">Display a multi-point shape on the map by using the [**MapPolygon**](https://msdn.microsoft.com/library/windows/apps/dn637103) class.</span></span> <span data-ttu-id="5981f-172">Im folgenden Beispiel (aus dem [Beispiel zu UWP-Karten](http://go.microsoft.com/fwlink/p/?LinkId=619977)) wird ein rotes Feld mit blauem Rahmen auf der Karte angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5981f-172">The following example, from the [UWP map sample](http://go.microsoft.com/fwlink/p/?LinkId=619977), displays a red box with blue border on the map.</span></span>

```csharp
private void mapPolygonAddButton_Click(object sender, Windows.UI.Xaml.RoutedEventArgs e)
{
    double centerLatitude = myMap.Center.Position.Latitude;
    double centerLongitude = myMap.Center.Position.Longitude;

    var mapPolygon = new MapPolygon()
    {
        Path = new Geopath(new List<BasicGeoposition>() {
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

    myMap.MapElements.Add(mapPolygon);
}
```

## <a name="add-a-mappolyline"></a><span data-ttu-id="5981f-173">Hinzufügen einer MapPolyline</span><span class="sxs-lookup"><span data-stu-id="5981f-173">Add a MapPolyline</span></span>


<span data-ttu-id="5981f-174">Mithilfe der Klasse [**MapPolyline**](https://msdn.microsoft.com/library/windows/apps/dn637114) können Sie eine Linie auf der Karte anzeigen.</span><span class="sxs-lookup"><span data-stu-id="5981f-174">Display a line on the map by using the [**MapPolyline**](https://msdn.microsoft.com/library/windows/apps/dn637114) class.</span></span> <span data-ttu-id="5981f-175">Im folgenden Beispiel (aus dem [Beispiel zu UWP-Karten](http://go.microsoft.com/fwlink/p/?LinkId=619977)) wird eine gestrichelte Linie auf der Karte angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5981f-175">The following example, from the [UWP map sample](http://go.microsoft.com/fwlink/p/?LinkId=619977), displays a dashed line on the map.</span></span>

```csharp
private void mapPolylineAddButton_Click(object sender, Windows.UI.Xaml.RoutedEventArgs e)
{
    double centerLatitude = myMap.Center.Position.Latitude;
    double centerLongitude = myMap.Center.Position.Longitude;
    var mapPolyline = new MapPolyline
    {
        Path = new Geopath(new List<BasicGeoposition>() {
            new BasicGeoposition() {Latitude=centerLatitude-0.0005, Longitude=centerLongitude-0.001 },
            new BasicGeoposition() {Latitude=centerLatitude+0.0005, Longitude=centerLongitude+0.001 },
        }),
        StrokeColor = Colors.Black,
        StrokeThickness = 3,
        StrokeDashed = true,
    };

    myMap.MapElements.Add(mapPolyline);
}
```

## <a name="add-xaml"></a><span data-ttu-id="5981f-176">Hinzufügen von XAML</span><span class="sxs-lookup"><span data-stu-id="5981f-176">Add XAML</span></span>

<span data-ttu-id="5981f-177">Zeigen Sie benutzerdefinierte UI-Elemente mit XAML auf der Karte an.</span><span class="sxs-lookup"><span data-stu-id="5981f-177">Display custom UI elements on the map using XAML.</span></span> <span data-ttu-id="5981f-178">Positionieren Sie XAML auf der Karte, indem Sie die Position und den normalisierten Ankerpunkt für den XAML-Code angeben.</span><span class="sxs-lookup"><span data-stu-id="5981f-178">Position XAML on the map by specifying the location and normalized anchor point of the XAML.</span></span>

-   <span data-ttu-id="5981f-179">Rufen Sie [**SetLocation**](https://msdn.microsoft.com/library/windows/desktop/ms704369) auf, um die Position auf der Karte festzulegen, an der der XAML-Code platziert werden soll.</span><span class="sxs-lookup"><span data-stu-id="5981f-179">Set the location on the map where the XAML is placed by calling [**SetLocation**](https://msdn.microsoft.com/library/windows/desktop/ms704369).</span></span>
-   <span data-ttu-id="5981f-180">Rufen Sie [**SetNormalizedAnchorPoint**](https://msdn.microsoft.com/library/windows/apps/dn637050) auf, um die relative Position des XAML-Codes festzulegen, die der angegebenen Position entspricht.</span><span class="sxs-lookup"><span data-stu-id="5981f-180">Set the relative location on the XAML that corresponds to the specified location by calling [**SetNormalizedAnchorPoint**](https://msdn.microsoft.com/library/windows/apps/dn637050).</span></span>

<span data-ttu-id="5981f-181">Im folgenden Beispiel wird einer Karte von Seattle das XAML-Steuerelement [**Border**](https://msdn.microsoft.com/library/windows/apps/br209250) hinzugefügt, um den Standort der Space Needle anzugeben.</span><span class="sxs-lookup"><span data-stu-id="5981f-181">The following example shows a map of the city of Seattle and adds a XAML [**Border**](https://msdn.microsoft.com/library/windows/apps/br209250) control to indicate the location of the Space Needle.</span></span> <span data-ttu-id="5981f-182">Außerdem wird die Karte in diesem Bereich zentriert und vergrößert.</span><span class="sxs-lookup"><span data-stu-id="5981f-182">It also centers the map over the area and zooms in.</span></span> <span data-ttu-id="5981f-183">Allgemeine Informationen zur Verwendung des Kartensteuerelements finden Sie unter [Anzeigen von Karten mit 2D-, 3D- und Streetside-Ansichten](display-maps.md).</span><span class="sxs-lookup"><span data-stu-id="5981f-183">For general info about using the map control, see [Display maps with 2D, 3D, and Streetside views](display-maps.md).</span></span>

```csharp
private void displayXAMLButton_Click(object sender, RoutedEventArgs e)
{
   // Specify a known location.
   BasicGeoposition snPosition = new BasicGeoposition() { Latitude = 47.620, Longitude = -122.349 };
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

<span data-ttu-id="5981f-184">In diesem Beispiel wird ein blauer Rahmen auf der Karte angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5981f-184">This example displays a blue border on the map.</span></span>

![Screenshot eines XAML-Elements, das am interessanten Ort auf der Karte angezeigt wird](images/displaypoixaml.png)

<span data-ttu-id="5981f-186">Die nächsten Beispiele zeigen, wie XAML-UI-Elemente direkt im XAML-Markup der Seite mithilfe der Datenbindung hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="5981f-186">The next examples show how to add XAML UI elements directly in the XAML markup of the page using data binding.</span></span> <span data-ttu-id="5981f-187">Wie bei anderen XAML-Elementen zur Anzeige von Inhalten auch, stellt [**Children**](https://msdn.microsoft.com/library/windows/apps/dn637008) die standardmäßige Inhaltseigenschaft von [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004) dar und muss nicht explizit im XAML-Markup angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="5981f-187">As with other XAML elements that display content, [**Children**](https://msdn.microsoft.com/library/windows/apps/dn637008) is the default content property of the [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004) and does not have to be specified explicitly in XAML markup.</span></span>

<span data-ttu-id="5981f-188">In diesem Beispiel wird gezeigt, wie zwei XAML-Steuerelemente als implizite untergeordnete Objekte von [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004) angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="5981f-188">This example shows how to display two XAML controls as implicit children of the [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004).</span></span>

```xml
<maps:MapControl>
    <TextBox Text="Seattle" maps:MapControl.Location="{Binding SeattleLocation}"/>
    <TextBox Text="Bellevue" maps:MapControl.Location="{Binding BellevueLocation}"/>
</maps:MapControl>
```

<span data-ttu-id="5981f-189">In diesem Beispiel wird gezeigt, wie zwei XAML-Steuerelemente in einem [**MapItemsControl**](https://msdn.microsoft.com/library/windows/apps/dn637094) angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="5981f-189">This example shows how to display two XAML controls contained within a [**MapItemsControl**](https://msdn.microsoft.com/library/windows/apps/dn637094).</span></span>

```xml
<maps:MapControl>
  <maps:MapItemsControl>
    <TextBox Text="Seattle" maps:MapControl.Location="{Binding SeattleLocation}"/>
    <TextBox Text="Bellevue" maps:MapControl.Location="{Binding BellevueLocation}"/>
  </maps:MapItemsControl>
</maps:MapControl>
```

<span data-ttu-id="5981f-190">In diesem Beispiel wird eine Sammlung von XAML-Elementen angezeigt, die an [**MapItemsControl**](https://msdn.microsoft.com/library/windows/apps/dn637094) gebunden sind.</span><span class="sxs-lookup"><span data-stu-id="5981f-190">This example displays a collection of XAML elements bound to a [**MapItemsControl**](https://msdn.microsoft.com/library/windows/apps/dn637094).</span></span>

```xml
<maps:MapControl x:Name="MapControl" MapTapped="MapTapped" MapDoubleTapped="MapTapped" MapHolding="MapTapped">
  <maps:MapItemsControl ItemsSource="{Binding StateOverlays}">
    <maps:MapItemsControl.ItemTemplate>
      <DataTemplate>
        <StackPanel Background="Black" Tapped="Overlay_Tapped">
          <TextBlock maps:MapControl.Location="{Binding Location}" Text="{Binding Name}" maps:MapControl.NormalizedAnchorPoint="0.5,0.5" FontSize="20" Margin="5"/>
        </StackPanel>
      </DataTemplate>
    </maps:MapItemsControl.ItemTemplate>
  </maps:MapItemsControl>
</maps:MapControl>
```

## <a name="related-topics"></a><span data-ttu-id="5981f-191">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="5981f-191">Related topics</span></span>

* [<span data-ttu-id="5981f-192">Bing Maps Developer Center</span><span class="sxs-lookup"><span data-stu-id="5981f-192">Bing Maps Developer Center</span></span>](https://www.bingmapsportal.com/)
* [<span data-ttu-id="5981f-193">Beispiel für UWP-Karte</span><span class="sxs-lookup"><span data-stu-id="5981f-193">UWP map sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=619977)
* [<span data-ttu-id="5981f-194">Entwurfsrichtlinien für Karten</span><span class="sxs-lookup"><span data-stu-id="5981f-194">Design guidelines for maps</span></span>](https://msdn.microsoft.com/library/windows/apps/dn596102)
* [<span data-ttu-id="5981f-195">Build 2015-Video: Nutzen von Karten und Ortung über Telefon, Tablet und PC in Ihren Windows-Apps</span><span class="sxs-lookup"><span data-stu-id="5981f-195">Build 2015 video: Leveraging Maps and Location Across Phone, Tablet, and PC in Your Windows Apps</span></span>](https://channel9.msdn.com/Events/Build/2015/2-757)
* [<span data-ttu-id="5981f-196">Beispiel für eine UWP-App mit Verkehrsinformationen</span><span class="sxs-lookup"><span data-stu-id="5981f-196">UWP traffic app sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=619982)
* [**<span data-ttu-id="5981f-197">MapIcon</span><span class="sxs-lookup"><span data-stu-id="5981f-197">MapIcon</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn637077)
* [**<span data-ttu-id="5981f-198">MapPolygon</span><span class="sxs-lookup"><span data-stu-id="5981f-198">MapPolygon</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn637103)
* [**<span data-ttu-id="5981f-199">MapPolyline</span><span class="sxs-lookup"><span data-stu-id="5981f-199">MapPolyline</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn637114)
