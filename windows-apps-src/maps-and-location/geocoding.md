---
author: PatrickFarley
title: "Durchführen der Geocodierung und umgekehrten Geocodierung"
description: Sie konvertieren Adressen in geografische Standorte (Geocodierung) und geografische Standorte in Adressen (umgekehrte Geocodierung), indem Sie die Methoden der MapLocationFinder-Klasse im Windows.Services.Maps-Namespace aufrufen.
ms.assetid: B912BE80-3E1D-43BB-918F-7A43327597D2
ms.author: pafarley
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Geocodierung, Karte, Ort, Standort
ms.openlocfilehash: a68898e86ad2e901499077e8f856c5318a7feae7
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
ms.translationtype: HT
ms.contentlocale: de-DE
---
# <a name="perform-geocoding-and-reverse-geocoding"></a><span data-ttu-id="6bc73-104">Durchführen von Geocodierung und umgekehrter Geocodierung</span><span class="sxs-lookup"><span data-stu-id="6bc73-104">Perform geocoding and reverse geocoding</span></span>


<span data-ttu-id="6bc73-105">\[ Aktualisiert für UWP-Apps unter Windows 10.</span><span class="sxs-lookup"><span data-stu-id="6bc73-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="6bc73-106">Artikel zu Windows 8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span><span class="sxs-lookup"><span data-stu-id="6bc73-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>


<span data-ttu-id="6bc73-107">Sie konvertieren Adressen in geografische Standorte (Geocodierung) und geografische Standorte in Adressen (umgekehrte Geocodierung), indem Sie die Methoden der [**MapLocationFinder**](https://msdn.microsoft.com/library/windows/apps/dn627550)-Klasse im [**Windows.Services.Maps**](https://msdn.microsoft.com/library/windows/apps/dn636979)-Namespace aufrufen.</span><span class="sxs-lookup"><span data-stu-id="6bc73-107">Convert addresses to geographic locations (geocoding) and convert geographic locations to addresses (reverse geocoding) by calling the methods of the [**MapLocationFinder**](https://msdn.microsoft.com/library/windows/apps/dn627550) class in the [**Windows.Services.Maps**](https://msdn.microsoft.com/library/windows/apps/dn636979) namespace.</span></span>

<span data-ttu-id="6bc73-108">**Tipp** Um mehr über das Verwenden von Karten in Ihrer App zu erfahren, laden Sie das folgende Beispiel aus dem [Repository Beispiele für Universelle Windows-Plattform](http://go.microsoft.com/fwlink/p/?LinkId=619979) auf GitHub herunter.</span><span class="sxs-lookup"><span data-stu-id="6bc73-108">**Tip** To learn more about using maps in your app, download the following sample from the [Windows-universal-samples repo](http://go.microsoft.com/fwlink/p/?LinkId=619979) on GitHub.</span></span>

-   [<span data-ttu-id="6bc73-109">Kartenbeispiel für die Universelle Windows-Plattform (UWP)</span><span class="sxs-lookup"><span data-stu-id="6bc73-109">Universal Windows Platform (UWP) map sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=619977)

<span data-ttu-id="6bc73-110">Hier erfahren Sie, welchen Zusammenhang es zwischen den Klassen für Geocodierung und umgekehrte Geocodierung gibt:</span><span class="sxs-lookup"><span data-stu-id="6bc73-110">Here's how the classes for geocoding and reverse geocoding are related:</span></span>

-   <span data-ttu-id="6bc73-111">Die [**MapLocationFinder**](https://msdn.microsoft.com/library/windows/apps/dn627550)-Klasse verfügt über Methoden zur Geocodierung ([**FindLocationsAsync**](https://msdn.microsoft.com/library/windows/apps/dn636925)) und umgekehrten Geocodierung ([**FindLocationsAtAsync**](https://msdn.microsoft.com/library/windows/apps/dn636928)).</span><span class="sxs-lookup"><span data-stu-id="6bc73-111">The [**MapLocationFinder**](https://msdn.microsoft.com/library/windows/apps/dn627550) class has methods that do geocoding ([**FindLocationsAsync**](https://msdn.microsoft.com/library/windows/apps/dn636925)) and reverse geocoding ([**FindLocationsAtAsync**](https://msdn.microsoft.com/library/windows/apps/dn636928)).</span></span>
-   <span data-ttu-id="6bc73-112">Diese Methoden geben ein [**MapLocationFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn627551) zurück.</span><span class="sxs-lookup"><span data-stu-id="6bc73-112">These methods return a [**MapLocationFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn627551).</span></span>
-   <span data-ttu-id="6bc73-113">[**MapLocationFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn627551) enthält eine Sammlung von [**MapLocation**](https://msdn.microsoft.com/library/windows/apps/dn627549)-Objekten.</span><span class="sxs-lookup"><span data-stu-id="6bc73-113">The [**MapLocationFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn627551) contains a collection of [**MapLocation**](https://msdn.microsoft.com/library/windows/apps/dn627549) objects.</span></span> <span data-ttu-id="6bc73-114">Auf diese Sammlung greifen Sie über die [**Locations**](https://msdn.microsoft.com/library/windows/apps/dn627552)-Eigenschaft von **MapLocationFinderResult** zu.</span><span class="sxs-lookup"><span data-stu-id="6bc73-114">Access this collection through the [**Locations**](https://msdn.microsoft.com/library/windows/apps/dn627552) property of the **MapLocationFinderResult**.</span></span>
-   <span data-ttu-id="6bc73-115">Jedes [**MapLocation**](https://msdn.microsoft.com/library/windows/apps/dn627549)-Objekt enthält ein [**MapAddress**](https://msdn.microsoft.com/library/windows/apps/dn627533)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="6bc73-115">Each [**MapLocation**](https://msdn.microsoft.com/library/windows/apps/dn627549) object contains a [**MapAddress**](https://msdn.microsoft.com/library/windows/apps/dn627533) object.</span></span> <span data-ttu-id="6bc73-116">Auf dieses Objekt greifen Sie über die [**Address**](https://msdn.microsoft.com/library/windows/apps/dn636929)-Eigenschaft des jeweiligen **MapLocation** zu.</span><span class="sxs-lookup"><span data-stu-id="6bc73-116">Access this object through the [**Address**](https://msdn.microsoft.com/library/windows/apps/dn636929) property of each **MapLocation**.</span></span>

<span data-ttu-id="6bc73-117">**Wichtig:** Sie müssen einen Kartenauthentifizierungsschlüssel angeben, um Kartendienste verwenden zu können.</span><span class="sxs-lookup"><span data-stu-id="6bc73-117">**Important**  You must specify a maps authentication key before you can use map services.</span></span> <span data-ttu-id="6bc73-118">Weitere Informationen finden Sie unter [Anfordern eines Kartenauthentifizierungsschlüssels](authentication-key.md).</span><span class="sxs-lookup"><span data-stu-id="6bc73-118">For more info, see [Request a maps authentication key](authentication-key.md).</span></span>

 

## <a name="get-a-location-geocode"></a><span data-ttu-id="6bc73-119">Abrufen eines Standorts (Geocode)</span><span class="sxs-lookup"><span data-stu-id="6bc73-119">Get a location (Geocode)</span></span>


<span data-ttu-id="6bc73-120">Sie konvertieren eine Adresse oder einen Ortsnamen in einen geografischen Standort (Geocodierung), indem Sie die folgenden Schritte ausführen.</span><span class="sxs-lookup"><span data-stu-id="6bc73-120">Convert an address or a place name to a geographic location (geocoding) by performing the following steps.</span></span>

1.  <span data-ttu-id="6bc73-121">Rufen Sie eine der Überladungen der [**FindLocationsAsync**](https://msdn.microsoft.com/library/windows/apps/dn636925)-Methode der [**MapLocationFinder**](https://msdn.microsoft.com/library/windows/apps/dn627550)-Klasse auf.</span><span class="sxs-lookup"><span data-stu-id="6bc73-121">Call one of the overloads of the [**FindLocationsAsync**](https://msdn.microsoft.com/library/windows/apps/dn636925) method of the [**MapLocationFinder**](https://msdn.microsoft.com/library/windows/apps/dn627550) class.</span></span>
2.  <span data-ttu-id="6bc73-122">Die [**FindLocationsAsync**](https://msdn.microsoft.com/library/windows/apps/dn636925)-Methode gibt ein [**MapLocationFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn627551)-Objekt zurück, das eine Sammlung übereinstimmender [**MapLocation**](https://msdn.microsoft.com/library/windows/apps/dn627549)-Objekte enthält.</span><span class="sxs-lookup"><span data-stu-id="6bc73-122">The [**FindLocationsAsync**](https://msdn.microsoft.com/library/windows/apps/dn636925) method returns a [**MapLocationFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn627551) object that contains a collection of matching [**MapLocation**](https://msdn.microsoft.com/library/windows/apps/dn627549) objects.</span></span>
3.  <span data-ttu-id="6bc73-123">Auf diese Sammlung greifen Sie über die [**Locations**](https://msdn.microsoft.com/library/windows/apps/dn627552)-Eigenschaft von [**MapLocationFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn627551) zu.</span><span class="sxs-lookup"><span data-stu-id="6bc73-123">Access this collection through the [**Locations**](https://msdn.microsoft.com/library/windows/apps/dn627552) property of the [**MapLocationFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn627551).</span></span>

```csharp
using Windows.Services.Maps;
using Windows.Devices.Geolocation;
...
private async void geocodeButton_Click(object sender, RoutedEventArgs e)
{
   // The address or business to geocode.
   string addressToGeocode = "Microsoft";

   // The nearby location to use as a query hint.
   BasicGeoposition queryHint = new BasicGeoposition();
   queryHint.Latitude = 47.643;
   queryHint.Longitude = -122.131;
   Geopoint hintPoint = new Geopoint(queryHint);

   // Geocode the specified address, using the specified reference point
   // as a query hint. Return no more than 3 results.
   MapLocationFinderResult result =
         await MapLocationFinder.FindLocationsAsync(
                           addressToGeocode,
                           hintPoint,
                           3);

   // If the query returns results, display the coordinates
   // of the first result.
   if (result.Status == MapLocationFinderStatus.Success)
   {
      tbOutputText.Text = "result = (" +
            result.Locations[0].Point.Position.Latitude.ToString() + "," +
            result.Locations[0].Point.Position.Longitude.ToString() + ")";
   }
}
```

<span data-ttu-id="6bc73-124">Dieser Code zeigt die folgenden Ergebnisse im `tbOutputText`-Textfeld an:</span><span class="sxs-lookup"><span data-stu-id="6bc73-124">This code displays the following results to the `tbOutputText` textbox.</span></span>

``` syntax
result = (47.6406099647284,-122.129339994863)
```

## <a name="get-an-address-reverse-geocode"></a><span data-ttu-id="6bc73-125">Abrufen einer Adresse (umgekehrte Geocodierung)</span><span class="sxs-lookup"><span data-stu-id="6bc73-125">Get an address (reverse geocode)</span></span>


<span data-ttu-id="6bc73-126">Sie konvertieren einen geografischen Standort in eine Adresse (umgekehrte Geocodierung), indem Sie die folgenden Schritte ausführen.</span><span class="sxs-lookup"><span data-stu-id="6bc73-126">Convert a geographic location to an address (reverse geocoding) by performing the following steps.</span></span>

1.  <span data-ttu-id="6bc73-127">Rufen Sie die [**FindLocationsAtAsync**](https://msdn.microsoft.com/library/windows/apps/dn636928)-Methode der [**MapLocationFinder**](https://msdn.microsoft.com/library/windows/apps/dn627550)-Klasse auf.</span><span class="sxs-lookup"><span data-stu-id="6bc73-127">Call the [**FindLocationsAtAsync**](https://msdn.microsoft.com/library/windows/apps/dn636928) method of the [**MapLocationFinder**](https://msdn.microsoft.com/library/windows/apps/dn627550) class.</span></span>
2.  <span data-ttu-id="6bc73-128">Die [**FindLocationsAtAsync**](https://msdn.microsoft.com/library/windows/apps/dn636928)-Methode gibt ein [**MapLocationFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn627551)-Objekt zurück, das eine Sammlung übereinstimmender [**MapLocation**](https://msdn.microsoft.com/library/windows/apps/dn627549)-Objekte enthält.</span><span class="sxs-lookup"><span data-stu-id="6bc73-128">The [**FindLocationsAtAsync**](https://msdn.microsoft.com/library/windows/apps/dn636928) method returns a [**MapLocationFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn627551) object that contains a collection of matching [**MapLocation**](https://msdn.microsoft.com/library/windows/apps/dn627549) objects.</span></span>
3.  <span data-ttu-id="6bc73-129">Auf diese Sammlung greifen Sie über die [**Locations**](https://msdn.microsoft.com/library/windows/apps/dn627552)-Eigenschaft von [**MapLocationFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn627551) zu.</span><span class="sxs-lookup"><span data-stu-id="6bc73-129">Access this collection through the [**Locations**](https://msdn.microsoft.com/library/windows/apps/dn627552) property of the [**MapLocationFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn627551).</span></span>
4.  <span data-ttu-id="6bc73-130">Auf das [**MapAddress**](https://msdn.microsoft.com/library/windows/apps/dn627533)-Objekt greifen Sie über die [**Address**](https://msdn.microsoft.com/library/windows/apps/dn636929)-Eigenschaft jedes [**MapLocation**](https://msdn.microsoft.com/library/windows/apps/dn627549)-Objekts zu.</span><span class="sxs-lookup"><span data-stu-id="6bc73-130">Access the [**MapAddress**](https://msdn.microsoft.com/library/windows/apps/dn627533) object through the [**Address**](https://msdn.microsoft.com/library/windows/apps/dn636929) property of each [**MapLocation**](https://msdn.microsoft.com/library/windows/apps/dn627549).</span></span>

```csharp
using Windows.Services.Maps;
using Windows.Devices.Geolocation;
...
private async void reverseGeocodeButton_Click(object sender, RoutedEventArgs e)
{
   // The location to reverse geocode.
   BasicGeoposition location = new BasicGeoposition();
   location.Latitude = 47.643;
   location.Longitude = -122.131;
   Geopoint pointToReverseGeocode = new Geopoint(location);

   // Reverse geocode the specified geographic location.
   MapLocationFinderResult result =
         await MapLocationFinder.FindLocationsAtAsync(pointToReverseGeocode);

   // If the query returns results, display the name of the town
   // contained in the address of the first result.
   if (result.Status == MapLocationFinderStatus.Success)
   {
      tbOutputText.Text = "town = " +
            result.Locations[0].Address.Town;
   }
}
```

<span data-ttu-id="6bc73-131">Dieser Code zeigt die folgenden Ergebnisse im `tbOutputText`-Textfeld an:</span><span class="sxs-lookup"><span data-stu-id="6bc73-131">This code displays the following results to the `tbOutputText` textbox.</span></span>

``` syntax
town = Redmond
```

## <a name="related-topics"></a><span data-ttu-id="6bc73-132">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="6bc73-132">Related topics</span></span>

* [<span data-ttu-id="6bc73-133">Bing Maps Developer Center</span><span class="sxs-lookup"><span data-stu-id="6bc73-133">Bing Maps Developer Center</span></span>](https://www.bingmapsportal.com/)
* [<span data-ttu-id="6bc73-134">Beispiel für UWP-Karte</span><span class="sxs-lookup"><span data-stu-id="6bc73-134">UWP map sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=619977)
* [<span data-ttu-id="6bc73-135">Entwurfsrichtlinien für Karten</span><span class="sxs-lookup"><span data-stu-id="6bc73-135">Design guidelines for maps</span></span>](https://msdn.microsoft.com/library/windows/apps/dn596102)
* [<span data-ttu-id="6bc73-136">Build 2015-Video: Nutzen von Karten und Ortung über Telefon, Tablet und PC in Ihren Windows-Apps</span><span class="sxs-lookup"><span data-stu-id="6bc73-136">Build 2015 video: Leveraging Maps and Location Across Phone, Tablet, and PC in Your Windows Apps</span></span>](https://channel9.msdn.com/Events/Build/2015/2-757)
* [<span data-ttu-id="6bc73-137">Beispiel für eine UWP-App mit Verkehrsinformationen</span><span class="sxs-lookup"><span data-stu-id="6bc73-137">UWP traffic app sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=619982)
* [**<span data-ttu-id="6bc73-138">MapLocationFinder</span><span class="sxs-lookup"><span data-stu-id="6bc73-138">MapLocationFinder</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn627550)
* [**<span data-ttu-id="6bc73-139">FindLocationsAsync</span><span class="sxs-lookup"><span data-stu-id="6bc73-139">FindLocationsAsync</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn636925)
* [**<span data-ttu-id="6bc73-140">FindLocationsAtAsync</span><span class="sxs-lookup"><span data-stu-id="6bc73-140">FindLocationsAtAsync</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn636928)
