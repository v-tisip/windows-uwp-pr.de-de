---
author: PatrickFarley
title: Durchführen der Geocodierung und umgekehrten Geocodierung
description: Dieses Handbuch erfahren Sie, wie Sie konvertieren Adressen in geografische Standorte (geocodierung) und geografische Standorte in Adressen (umgekehrte geocodierung) durch Aufrufen der Methoden der MapLocationFinder-Klasse im Windows.Services.Maps-Namespace.
ms.assetid: B912BE80-3E1D-43BB-918F-7A43327597D2
ms.author: pafarley
ms.date: 07/02/2018
ms.topic: article
keywords: Windows10, UWP, Geocodierung, Karte, Ort, Standort
ms.localizationpriority: medium
ms.openlocfilehash: bdd956dece4435ceb8e14121ec2b545095af3a11
ms.sourcegitcommit: e814a13978f33654d8e995584f4b047cb53e0aef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "6043413"
---
# <a name="perform-geocoding-and-reverse-geocoding"></a><span data-ttu-id="2aedf-104">Durchführen von Geocodierung und umgekehrter Geocodierung</span><span class="sxs-lookup"><span data-stu-id="2aedf-104">Perform geocoding and reverse geocoding</span></span>

<span data-ttu-id="2aedf-105">Dieses Handbuch beschreibt, wie Sie konvertieren Adressen in geografische Standorte (geocodierung) und geografische Standorte in Adressen (umgekehrte geocodierung) durch Aufrufen der Methoden der [**MapLocationFinder**](https://msdn.microsoft.com/library/windows/apps/dn627550) -Klasse in der [\*\*Windows.Services.Maps \*\*](https://msdn.microsoft.com/library/windows/apps/dn636979)Namespace.</span><span class="sxs-lookup"><span data-stu-id="2aedf-105">This guide shows you how to convert street addresses to geographic locations (geocoding) and convert geographic locations to street addresses (reverse geocoding) by calling the methods of the [**MapLocationFinder**](https://msdn.microsoft.com/library/windows/apps/dn627550) class in the [**Windows.Services.Maps**](https://msdn.microsoft.com/library/windows/apps/dn636979) namespace.</span></span>

> [!TIP]
> <span data-ttu-id="2aedf-106">Um mehr über die Verwendung von Karten in Ihrer app zu erfahren, laden Sie das Beispiel [MapControl](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MapControl) aus dem [Windows-universal-Samples-Repository](hhttps://github.com/Microsoft/Windows-universal-samples) auf GitHub.</span><span class="sxs-lookup"><span data-stu-id="2aedf-106">To learn more about using maps in your app, download the [MapControl](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MapControl) sample from the [Windows universal samples repo](hhttps://github.com/Microsoft/Windows-universal-samples) on GitHub.</span></span>

<span data-ttu-id="2aedf-107">Die Klassen geocodierung und umgekehrte geocodierung beteiligt sind wie folgt aufgebaut.</span><span class="sxs-lookup"><span data-stu-id="2aedf-107">The classes involved in geocoding and reverse geocoding are organized as follows.</span></span>

-   <span data-ttu-id="2aedf-108">[**MapLocationFinder**](https://msdn.microsoft.com/library/windows/apps/dn627550) -Klasse enthält Methoden, die zum Behandeln geocodierung ([**FindLocationsAsync**](https://msdn.microsoft.com/library/windows/apps/dn636925)) und umgekehrten geocodierung ([**FindLocationsAtAsync**](https://msdn.microsoft.com/library/windows/apps/dn636928)).</span><span class="sxs-lookup"><span data-stu-id="2aedf-108">The [**MapLocationFinder**](https://msdn.microsoft.com/library/windows/apps/dn627550) class contains methods that handle geocoding ([**FindLocationsAsync**](https://msdn.microsoft.com/library/windows/apps/dn636925)) and reverse geocoding ([**FindLocationsAtAsync**](https://msdn.microsoft.com/library/windows/apps/dn636928)).</span></span>
-   <span data-ttu-id="2aedf-109">Diese Methoden geben eine [**MapLocationFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn627551) -Instanz zurück.</span><span class="sxs-lookup"><span data-stu-id="2aedf-109">These methods both return a [**MapLocationFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn627551) instance.</span></span>
-   <span data-ttu-id="2aedf-110">Die [**Speicherorte**](https://msdn.microsoft.com/library/windows/apps/dn627552) -Eigenschaft der [**MapLocationFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn627551) enthält eine Auflistung der [**Kartenregion**](https://msdn.microsoft.com/library/windows/apps/dn627549) Objekte.</span><span class="sxs-lookup"><span data-stu-id="2aedf-110">The [**Locations**](https://msdn.microsoft.com/library/windows/apps/dn627552) property of the [**MapLocationFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn627551) exposes a collection of [**MapLocation**](https://msdn.microsoft.com/library/windows/apps/dn627549) objects.</span></span> 
-   <span data-ttu-id="2aedf-111">[**Kartenregion**](https://msdn.microsoft.com/library/windows/apps/dn627549) Objekte enthalten eine [**Adresse**](https://msdn.microsoft.com/library/windows/apps/dn636929) -Eigenschaft, die ein [**MapAddress**](https://msdn.microsoft.com/library/windows/apps/dn627533) -Objekt, eine Straße darstellen verfügbar macht, und ein [**Punkt**](https://docs.microsoft.com/uwp/api/windows.services.maps.maplocation.point) -Eigenschaft, die ein [**Geopoint**](https://docs.microsoft.com/uwp/api/windows.devices.geolocation.geopoint) -Objekt zurück, einen geografischen Standort verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="2aedf-111">[**MapLocation**](https://msdn.microsoft.com/library/windows/apps/dn627549) objects have both an [**Address**](https://msdn.microsoft.com/library/windows/apps/dn636929) property, which exposes a [**MapAddress**](https://msdn.microsoft.com/library/windows/apps/dn627533) object representing a street address, and a [**Point**](https://docs.microsoft.com/uwp/api/windows.services.maps.maplocation.point) property, which exposes a [**Geopoint**](https://docs.microsoft.com/uwp/api/windows.devices.geolocation.geopoint) object representing a geographic location.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2aedf-112">Sie müssen einen Kartenauthentifizierungsschlüssel angeben, bevor Sie Kartendienste verwenden können.</span><span class="sxs-lookup"><span data-stu-id="2aedf-112">You must specify a maps authentication key before you can use map services.</span></span> <span data-ttu-id="2aedf-113">Weitere Informationen finden Sie unter [Anfordern eines Kartenauthentifizierungsschlüssels](authentication-key.md).</span><span class="sxs-lookup"><span data-stu-id="2aedf-113">For more info, see [Request a maps authentication key](authentication-key.md).</span></span>

## <a name="get-a-location-geocode"></a><span data-ttu-id="2aedf-114">Abrufen eines Standorts (Geocode)</span><span class="sxs-lookup"><span data-stu-id="2aedf-114">Get a location (Geocode)</span></span>

<span data-ttu-id="2aedf-115">In diesem Abschnitt zeigt, wie eine Adresse oder einen Ortsnamen in einen geografischen Standort (geocodierung) konvertieren.</span><span class="sxs-lookup"><span data-stu-id="2aedf-115">This section shows how to convert a street address or a place name to a geographic location (geocoding).</span></span>

1.  <span data-ttu-id="2aedf-116">Rufen Sie eine Überladung der Methode [**FindLocationsAsync**](https://msdn.microsoft.com/library/windows/apps/dn636925) der [**MapLocationFinder**](https://msdn.microsoft.com/library/windows/apps/dn627550) -Klasse mit einem Ortsnamen oder Straße.</span><span class="sxs-lookup"><span data-stu-id="2aedf-116">Call one of the overloads of the [**FindLocationsAsync**](https://msdn.microsoft.com/library/windows/apps/dn636925) method of the [**MapLocationFinder**](https://msdn.microsoft.com/library/windows/apps/dn627550) class with a place name or street address.</span></span>
2.  <span data-ttu-id="2aedf-117">Die [**FindLocationsAsync**](https://msdn.microsoft.com/library/windows/apps/dn636925) -Methode gibt ein [**MapLocationFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn627551) -Objekt.</span><span class="sxs-lookup"><span data-stu-id="2aedf-117">The [**FindLocationsAsync**](https://msdn.microsoft.com/library/windows/apps/dn636925) method returns a [**MapLocationFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn627551) object.</span></span>
3.  <span data-ttu-id="2aedf-118">Verwenden Sie die [**Speicherorte**](https://msdn.microsoft.com/library/windows/apps/dn627552) -Eigenschaft der [**MapLocationFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn627551) , um eine Sammlung [**Kartenregion**](https://msdn.microsoft.com/library/windows/apps/dn627549) Objekte verfügbar zu machen.</span><span class="sxs-lookup"><span data-stu-id="2aedf-118">Use the [**Locations**](https://msdn.microsoft.com/library/windows/apps/dn627552) property of the [**MapLocationFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn627551) to expose a collection [**MapLocation**](https://msdn.microsoft.com/library/windows/apps/dn627549) objects.</span></span> <span data-ttu-id="2aedf-119">Da das System mehreren Standorten finden kann, die der Eingabe entsprechen, möglicherweise mehrere [**Kartenregion**](https://msdn.microsoft.com/library/windows/apps/dn627549) Objekte vor.</span><span class="sxs-lookup"><span data-stu-id="2aedf-119">There may be multiple [**MapLocation**](https://msdn.microsoft.com/library/windows/apps/dn627549) objects because the system may find multiple locations that correspond to the given input.</span></span>

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

<span data-ttu-id="2aedf-120">Dieser Code zeigt die folgenden Ergebnisse im `tbOutputText`-Textfeld an:</span><span class="sxs-lookup"><span data-stu-id="2aedf-120">This code displays the following results to the `tbOutputText` textbox.</span></span>

``` syntax
result = (47.6406099647284,-122.129339994863)
```

## <a name="get-an-address-reverse-geocode"></a><span data-ttu-id="2aedf-121">Abrufen einer Adresse (umgekehrte Geocodierung)</span><span class="sxs-lookup"><span data-stu-id="2aedf-121">Get an address (reverse geocode)</span></span>

<span data-ttu-id="2aedf-122">In diesem Abschnitt zeigt, wie einen geografischen Standort in eine Adresse (umgekehrte geocodierung) konvertieren.</span><span class="sxs-lookup"><span data-stu-id="2aedf-122">This section shows how to convert a geographic location to an address (reverse geocoding).</span></span>

1.  <span data-ttu-id="2aedf-123">Rufen Sie die [**FindLocationsAtAsync**](https://msdn.microsoft.com/library/windows/apps/dn636928)-Methode der [**MapLocationFinder**](https://msdn.microsoft.com/library/windows/apps/dn627550)-Klasse auf.</span><span class="sxs-lookup"><span data-stu-id="2aedf-123">Call the [**FindLocationsAtAsync**](https://msdn.microsoft.com/library/windows/apps/dn636928) method of the [**MapLocationFinder**](https://msdn.microsoft.com/library/windows/apps/dn627550) class.</span></span>
2.  <span data-ttu-id="2aedf-124">Die [**FindLocationsAtAsync**](https://msdn.microsoft.com/library/windows/apps/dn636928)-Methode gibt ein [**MapLocationFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn627551)-Objekt zurück, das eine Sammlung übereinstimmender [**MapLocation**](https://msdn.microsoft.com/library/windows/apps/dn627549)-Objekte enthält.</span><span class="sxs-lookup"><span data-stu-id="2aedf-124">The [**FindLocationsAtAsync**](https://msdn.microsoft.com/library/windows/apps/dn636928) method returns a [**MapLocationFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn627551) object that contains a collection of matching [**MapLocation**](https://msdn.microsoft.com/library/windows/apps/dn627549) objects.</span></span>
3.  <span data-ttu-id="2aedf-125">Verwenden Sie die [**Speicherorte**](https://msdn.microsoft.com/library/windows/apps/dn627552) -Eigenschaft der [**MapLocationFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn627551) , um eine Sammlung [**Kartenregion**](https://msdn.microsoft.com/library/windows/apps/dn627549) Objekte verfügbar zu machen.</span><span class="sxs-lookup"><span data-stu-id="2aedf-125">Use the [**Locations**](https://msdn.microsoft.com/library/windows/apps/dn627552) property of the [**MapLocationFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn627551) to expose a collection [**MapLocation**](https://msdn.microsoft.com/library/windows/apps/dn627549) objects.</span></span> <span data-ttu-id="2aedf-126">Da das System mehreren Standorten finden kann, die der Eingabe entsprechen, möglicherweise mehrere [**Kartenregion**](https://msdn.microsoft.com/library/windows/apps/dn627549) Objekte vor.</span><span class="sxs-lookup"><span data-stu-id="2aedf-126">There may be multiple [**MapLocation**](https://msdn.microsoft.com/library/windows/apps/dn627549) objects because the system may find multiple locations that correspond to the given input.</span></span>
4.  <span data-ttu-id="2aedf-127">Greifen Sie über die [**Adresse**](https://msdn.microsoft.com/library/windows/apps/dn636929) -Eigenschaft jedes [**Kartenregion**](https://msdn.microsoft.com/library/windows/apps/dn627549) [**MapAddress**](https://msdn.microsoft.com/library/windows/apps/dn627533) Objekte auf.</span><span class="sxs-lookup"><span data-stu-id="2aedf-127">Access [**MapAddress**](https://msdn.microsoft.com/library/windows/apps/dn627533) objects through the [**Address**](https://msdn.microsoft.com/library/windows/apps/dn636929) property of each [**MapLocation**](https://msdn.microsoft.com/library/windows/apps/dn627549).</span></span>

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

<span data-ttu-id="2aedf-128">Dieser Code zeigt die folgenden Ergebnisse im `tbOutputText`-Textfeld an:</span><span class="sxs-lookup"><span data-stu-id="2aedf-128">This code displays the following results to the `tbOutputText` textbox.</span></span>

``` syntax
town = Redmond
```

## <a name="related-topics"></a><span data-ttu-id="2aedf-129">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="2aedf-129">Related topics</span></span>

* [<span data-ttu-id="2aedf-130">Beispiel für UWP-Karte</span><span class="sxs-lookup"><span data-stu-id="2aedf-130">UWP map sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=619977)
* [<span data-ttu-id="2aedf-131">Beispiel für eine UWP-App mit Verkehrsinformationen</span><span class="sxs-lookup"><span data-stu-id="2aedf-131">UWP traffic app sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=619982)
* [<span data-ttu-id="2aedf-132">Entwurfsrichtlinien für Karten</span><span class="sxs-lookup"><span data-stu-id="2aedf-132">Design guidelines for maps</span></span>](https://msdn.microsoft.com/library/windows/apps/dn596102)
* [<span data-ttu-id="2aedf-133">Video: Nutzen von Karten und Speicherort über Telefon, Tablet und PC in Ihren Windows-Apps</span><span class="sxs-lookup"><span data-stu-id="2aedf-133">Video: Leveraging Maps and Location Across Phone, Tablet, and PC in Your Windows Apps</span></span>](https://channel9.msdn.com/Events/Build/2015/2-757)
* [<span data-ttu-id="2aedf-134">Bing Maps Developer Center</span><span class="sxs-lookup"><span data-stu-id="2aedf-134">Bing Maps Developer Center</span></span>](https://www.bingmapsportal.com/)
* [<span data-ttu-id="2aedf-135">**MapLocationFinder** Klasse</span><span class="sxs-lookup"><span data-stu-id="2aedf-135">**MapLocationFinder** class</span></span>](https://msdn.microsoft.com/library/windows/apps/dn627550)
* [<span data-ttu-id="2aedf-136">**FindLocationsAsync** -Methode</span><span class="sxs-lookup"><span data-stu-id="2aedf-136">**FindLocationsAsync** method</span></span>](https://msdn.microsoft.com/library/windows/apps/dn636925)
* [<span data-ttu-id="2aedf-137">**FindLocationsAtAsync** -Methode</span><span class="sxs-lookup"><span data-stu-id="2aedf-137">**FindLocationsAtAsync** method</span></span>](https://msdn.microsoft.com/library/windows/apps/dn636928)
