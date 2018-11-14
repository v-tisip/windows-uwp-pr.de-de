---
author: normesta
title: Anzeigen von Routen und Wegbeschreibungen auf einer Karte
description: Fordern Sie Routen und Wegbeschreibungen an, und zeigen Sie diese in Ihrer App an.
ms.assetid: BBB4C23A-8F10-41D1-81EA-271BE01AED81
ms.author: normesta
ms.date: 09/20/2017
ms.topic: article
keywords: Windows 10, UWP, Route, Karte, Standort, Wegbeschreibungen
ms.localizationpriority: medium
ms.openlocfilehash: 69283f6b53f3a8483376e3b8fe77a4491d4b01b1
ms.sourcegitcommit: 71e8eae5c077a7740e5606298951bb78fc42b22c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "6654216"
---
# <a name="display-routes-and-directions-on-a-map"></a><span data-ttu-id="d5829-104">Anzeigen von Routen und Wegbeschreibungen auf einer Karte</span><span class="sxs-lookup"><span data-stu-id="d5829-104">Display routes and directions on a map</span></span>



<span data-ttu-id="d5829-105">Fordern Sie Routen und Wegbeschreibungen an, und zeigen Sie diese in Ihrer App an.</span><span class="sxs-lookup"><span data-stu-id="d5829-105">Request routes and directions, and display them in your app.</span></span>

>[!Note]
><span data-ttu-id="d5829-106">Laden Sie das [Kartenbeispiel für die Universelle Windows-Plattform (UWP)](http://go.microsoft.com/fwlink/p/?LinkId=619977) herunter, um mehr über die Verwendung von Karten in Ihrer App zu erfahren.</span><span class="sxs-lookup"><span data-stu-id="d5829-106">To learn more about using maps in your app, download the [Universal Windows Platform (UWP) map sample](http://go.microsoft.com/fwlink/p/?LinkId=619977).</span></span>
><span data-ttu-id="d5829-107">Wenn die Kartenfunktion kein zentrales Feature Ihrer App ist, sollten Sie stattdessen die Windows-Karten-App starten.</span><span class="sxs-lookup"><span data-stu-id="d5829-107">If mapping isn't a core feature of your app, consider launching the Windows Maps app instead.</span></span> <span data-ttu-id="d5829-108">Sie können die URI-Schemas `bingmaps:`, `ms-drive-to:` und `ms-walk-to:` zum Starten der Windows-Karten-App für bestimmte Karten und für Turn-by-Turn-Wegbeschreibungen verwenden.</span><span class="sxs-lookup"><span data-stu-id="d5829-108">You can use the `bingmaps:`, `ms-drive-to:`, and `ms-walk-to:` URI schemes to launch the Windows Maps app to specific maps and turn-by-turn directions.</span></span> <span data-ttu-id="d5829-109">Weitere Informationen finden Sie unter [Starten der Windows-Karten-App](https://msdn.microsoft.com/library/windows/apps/mt228341).</span><span class="sxs-lookup"><span data-stu-id="d5829-109">For more info, see [Launch the Windows Maps app](https://msdn.microsoft.com/library/windows/apps/mt228341).</span></span>

 
## <a name="an-intro-to-maproutefinder-results"></a><span data-ttu-id="d5829-110">Eine Einführung in die MapRouteFinder-Ergebnisse</span><span class="sxs-lookup"><span data-stu-id="d5829-110">An intro to MapRouteFinder results</span></span>


<span data-ttu-id="d5829-111">Hier erfahren Sie, wie Klassen für Routen und Wegbeschreibungen zusammenhängen.</span><span class="sxs-lookup"><span data-stu-id="d5829-111">Here's how the classes for routes and directions are related:</span></span>

* <span data-ttu-id="d5829-112">Die [**MapRouteFinder**](https://msdn.microsoft.com/library/windows/apps/dn636938)-Klasse verfügt über Methoden zum Abrufen von Routen und Wegbeschreibungen.</span><span class="sxs-lookup"><span data-stu-id="d5829-112">The [**MapRouteFinder**](https://msdn.microsoft.com/library/windows/apps/dn636938) class has methods that get routes and directions.</span></span> <span data-ttu-id="d5829-113">Diese Methoden geben ein [**MapRouteFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn636939) zurück.</span><span class="sxs-lookup"><span data-stu-id="d5829-113">These methods return a [**MapRouteFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn636939).</span></span>

* <span data-ttu-id="d5829-114">Das [**MapRouteFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn636939) enthält ein [**MapRoute**](https://msdn.microsoft.com/library/windows/apps/dn636937)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="d5829-114">The [**MapRouteFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn636939) contains a [**MapRoute**](https://msdn.microsoft.com/library/windows/apps/dn636937) object.</span></span> <span data-ttu-id="d5829-115">Auf dieses Objekt greifen Sie über die [**Route**](https://msdn.microsoft.com/library/windows/apps/dn636940)-Eigenschaft des **MapRouteFinderResult** zu.</span><span class="sxs-lookup"><span data-stu-id="d5829-115">Access this object through the [**Route**](https://msdn.microsoft.com/library/windows/apps/dn636940) property of the **MapRouteFinderResult**.</span></span>

* <span data-ttu-id="d5829-116">Die [**MapRoute**](https://msdn.microsoft.com/library/windows/apps/dn636937) enthält eine Sammlung von [**MapRouteLeg**](https://msdn.microsoft.com/library/windows/apps/dn636955)-Objekten.</span><span class="sxs-lookup"><span data-stu-id="d5829-116">The [**MapRoute**](https://msdn.microsoft.com/library/windows/apps/dn636937) contains a collection of [**MapRouteLeg**](https://msdn.microsoft.com/library/windows/apps/dn636955) objects.</span></span> <span data-ttu-id="d5829-117">Auf diese Sammlung greifen Sie über die [**Legs**](https://msdn.microsoft.com/library/windows/apps/dn636973)-Eigenschaft der **MapRoute** zu.</span><span class="sxs-lookup"><span data-stu-id="d5829-117">Access this collection through the [**Legs**](https://msdn.microsoft.com/library/windows/apps/dn636973) property of the **MapRoute**.</span></span>

* <span data-ttu-id="d5829-118">Jeder [**MapRouteLeg**](https://msdn.microsoft.com/library/windows/apps/dn636955) enthält eine Sammlung von [**MapRouteManeuver**](https://msdn.microsoft.com/library/windows/apps/dn636961)-Objekten.</span><span class="sxs-lookup"><span data-stu-id="d5829-118">Each [**MapRouteLeg**](https://msdn.microsoft.com/library/windows/apps/dn636955) contains a collection of [**MapRouteManeuver**](https://msdn.microsoft.com/library/windows/apps/dn636961) objects.</span></span> <span data-ttu-id="d5829-119">Auf diese Sammlung greifen Sie über die [**Maneuvers**](https://msdn.microsoft.com/library/windows/apps/dn636959)-Eigenschaft des **MapRouteLeg** zu.</span><span class="sxs-lookup"><span data-stu-id="d5829-119">Access this collection through the [**Maneuvers**](https://msdn.microsoft.com/library/windows/apps/dn636959) property of the **MapRouteLeg**.</span></span>

<span data-ttu-id="d5829-120">Rufen Sie Routen und Wegbeschreibungen für Auto und Fußgänger ab, indem Sie die Methoden der [**MapRouteFinder**](https://msdn.microsoft.com/library/windows/apps/dn636938)-Klasse aufrufen.</span><span class="sxs-lookup"><span data-stu-id="d5829-120">Get a driving or walking route and directions by calling the methods of the [**MapRouteFinder**](https://msdn.microsoft.com/library/windows/apps/dn636938) class.</span></span> <span data-ttu-id="d5829-121">Beispielsweise [**GetDrivingRouteAsync**](https://msdn.microsoft.com/library/windows/apps/dn636943) oder [**GetWalkingRouteAsync**](https://msdn.microsoft.com/library/windows/apps/dn636953).</span><span class="sxs-lookup"><span data-stu-id="d5829-121">For example, [**GetDrivingRouteAsync**](https://msdn.microsoft.com/library/windows/apps/dn636943) or [**GetWalkingRouteAsync**](https://msdn.microsoft.com/library/windows/apps/dn636953).</span></span>

<span data-ttu-id="d5829-122">Wenn Sie eine Route anfordern, können Sie Folgendes angeben:</span><span class="sxs-lookup"><span data-stu-id="d5829-122">When you request a route, you can specify the following things:</span></span>

* <span data-ttu-id="d5829-123">Sie können nur einen Startpunkt und einen Endpunkt oder eine Reihe von Wegpunkten zur Berechnung angeben.</span><span class="sxs-lookup"><span data-stu-id="d5829-123">You can provide a start point and end point only, or you can provide a series of waypoints to compute the route.</span></span>

    <span data-ttu-id="d5829-124">*Endwegpunkte* fügt zusätzliche Etappen jeweils mit eigener Reiseroute hinzu.</span><span class="sxs-lookup"><span data-stu-id="d5829-124">*Stop* waypoints adds additional route legs, each with their own Itinerary.</span></span> <span data-ttu-id="d5829-125">Um *Endwegpunkte* anzugeben, verwenden Sie die [**GetDrivingRouteFromWaypointsAsync**](https://docs.microsoft.com/uwp/api/windows.services.maps.maproutefinder.getwalkingroutefromwaypointsasync)-Überladungen.</span><span class="sxs-lookup"><span data-stu-id="d5829-125">To specify *stop* waypoints, use any of the [**GetDrivingRouteFromWaypointsAsync**](https://docs.microsoft.com/uwp/api/windows.services.maps.maproutefinder.getwalkingroutefromwaypointsasync) overloads.</span></span>

    <span data-ttu-id="d5829-126">*Über* Wegpunkt werden Zwischenpositionen zwischen *Endwegpunkten* definiert.</span><span class="sxs-lookup"><span data-stu-id="d5829-126">*Via* waypoint defines intermediate locations between *stop* waypoints.</span></span> <span data-ttu-id="d5829-127">Es werden keine Teilstrecken der Route hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="d5829-127">They do not add route legs.</span></span>  <span data-ttu-id="d5829-128">Es handelt sich lediglich um Wegpunkte, die eine Route durchlaufen muss.</span><span class="sxs-lookup"><span data-stu-id="d5829-128">They are merely waypoints that a route must pass through.</span></span> <span data-ttu-id="d5829-129">Um *Über*-Wegpunkte festzulegen, verwenden Sie eine der [**GetDrivingRouteFromEnhancedWaypointsAsync**](https://docs.microsoft.com/uwp/api/windows.services.maps.maproutefinder.getdrivingroutefromenhancedwaypointsasync)-Überladungen.</span><span class="sxs-lookup"><span data-stu-id="d5829-129">To specify *via* waypoints, use any of the [**GetDrivingRouteFromEnhancedWaypointsAsync**](https://docs.microsoft.com/uwp/api/windows.services.maps.maproutefinder.getdrivingroutefromenhancedwaypointsasync) overloads.</span></span>

* <span data-ttu-id="d5829-130">Sie können Optimierungen angeben (z.B. die Minimierung der Distanz).</span><span class="sxs-lookup"><span data-stu-id="d5829-130">You can specify optimizations (For example: minimize the distance).</span></span>

* <span data-ttu-id="d5829-131">Sie können Einschränkungen festlegen (z. B. das Vermeiden von Autobahnen).</span><span class="sxs-lookup"><span data-stu-id="d5829-131">You can specify restrictions (For example: avoid highways).</span></span>

## <a name="display-directions"></a><span data-ttu-id="d5829-132">Anzeigen von Wegbeschreibungen</span><span class="sxs-lookup"><span data-stu-id="d5829-132">Display directions</span></span>

<span data-ttu-id="d5829-133">Das [**MapRouteFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn636939)-Objekt enthält ein [**MapRoute**](https://msdn.microsoft.com/library/windows/apps/dn636937)-Objekt, auf das Sie über seine [**Route**](https://msdn.microsoft.com/library/windows/apps/dn636940)-Eigenschaft zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="d5829-133">The [**MapRouteFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn636939) object contains a [**MapRoute**](https://msdn.microsoft.com/library/windows/apps/dn636937) object that you can access through its [**Route**](https://msdn.microsoft.com/library/windows/apps/dn636940) property.</span></span>

<span data-ttu-id="d5829-134">Die berechnete [**MapRoute**](https://msdn.microsoft.com/library/windows/apps/dn636937) hat Eigenschaften, die die Zeit zum Zurücklegen der Route, die Länge der Route und die Auflistung von [**MapRouteLeg**](https://msdn.microsoft.com/library/windows/apps/dn636955)-Objekten bereitstellen, die die Teilstrecken der Route enthalten.</span><span class="sxs-lookup"><span data-stu-id="d5829-134">The computed [**MapRoute**](https://msdn.microsoft.com/library/windows/apps/dn636937) has properties that provide the time to traverse the route, the length of the route, and the collection of [**MapRouteLeg**](https://msdn.microsoft.com/library/windows/apps/dn636955) objects that contain the legs of the route.</span></span> <span data-ttu-id="d5829-135">Jedes **MapRouteLeg**-Objekt enthält eine Auflistung von [**MapRouteManeuver**](https://msdn.microsoft.com/library/windows/apps/dn636961)-Objekten.</span><span class="sxs-lookup"><span data-stu-id="d5829-135">Each **MapRouteLeg** object contains a collection of [**MapRouteManeuver**](https://msdn.microsoft.com/library/windows/apps/dn636961) objects.</span></span> <span data-ttu-id="d5829-136">Das **MapRouteManeuver**-Objekt enthält eine Wegbeschreibung, auf die Sie über seine [**InstructionText**](https://msdn.microsoft.com/library/windows/apps/dn636964)-Eigenschaft zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="d5829-136">The **MapRouteManeuver** object contains directions that you can access through its [**InstructionText**](https://msdn.microsoft.com/library/windows/apps/dn636964) property.</span></span>

>[!IMPORTANT]
><span data-ttu-id="d5829-137">Sie müssen einen Kartenauthentifizierungsschlüssel angeben, bevor Sie Kartendienste verwenden können.</span><span class="sxs-lookup"><span data-stu-id="d5829-137">You must specify a maps authentication key before you can use map services.</span></span> <span data-ttu-id="d5829-138">Weitere Informationen finden Sie unter [Anfordern eines Kartenauthentifizierungsschlüssels](authentication-key.md).</span><span class="sxs-lookup"><span data-stu-id="d5829-138">For more info, see [Request a maps authentication key](authentication-key.md).</span></span>

 

```csharp
using System;
using Windows.UI.Xaml;
using Windows.UI.Xaml.Controls;
using Windows.Services.Maps;
using Windows.Devices.Geolocation;
...
private async void button_Click(object sender, RoutedEventArgs e)
{
   // Start at Microsoft in Redmond, Washington.
   BasicGeoposition startLocation = new BasicGeoposition() {Latitude=47.643,Longitude=-122.131};

   // End at the city of Seattle, Washington.
   BasicGeoposition endLocation = new BasicGeoposition() {Latitude = 47.604,Longitude= -122.329};

   // Get the route between the points.
   MapRouteFinderResult routeResult =
         await MapRouteFinder.GetDrivingRouteAsync(
         new Geopoint(startLocation),
         new Geopoint(endLocation),
         MapRouteOptimization.Time,
         MapRouteRestrictions.None);

   if (routeResult.Status == MapRouteFinderStatus.Success)
   {
      System.Text.StringBuilder routeInfo = new System.Text.StringBuilder();

      // Display summary info about the route.
      routeInfo.Append("Total estimated time (minutes) = ");
      routeInfo.Append(routeResult.Route.EstimatedDuration.TotalMinutes.ToString());
      routeInfo.Append("\nTotal length (kilometers) = ");
      routeInfo.Append((routeResult.Route.LengthInMeters / 1000).ToString());

      // Display the directions.
      routeInfo.Append("\n\nDIRECTIONS\n");

      foreach (MapRouteLeg leg in routeResult.Route.Legs)
      {
         foreach (MapRouteManeuver maneuver in leg.Maneuvers)
         {
            routeInfo.AppendLine(maneuver.InstructionText);
         }
      }

      // Load the text box.
      tbOutputText.Text = routeInfo.ToString();
   }
   else
   {
      tbOutputText.Text =
            "A problem occurred: " + routeResult.Status.ToString();
   }
}
```

<span data-ttu-id="d5829-139">Dieses Beispiel zeigt die folgenden Ergebnisse im `tbOutputText`-Textfeld an:</span><span class="sxs-lookup"><span data-stu-id="d5829-139">This example displays the following results to the `tbOutputText` text box.</span></span>

``` syntax
Total estimated time (minutes) = 18.4833333333333
Total length (kilometers) = 21.847

DIRECTIONS
Head north on 157th Ave NE.
Turn left onto 159th Ave NE.
Turn left onto NE 40th St.
Turn left onto WA-520 W.
Enter the freeway WA-520 from the right.
Keep left onto I-5 S/Portland.
Keep right and leave the freeway at exit 165A towards James St..
Turn right onto James St.
You have reached your destination.
```

## <a name="display-routes"></a><span data-ttu-id="d5829-140">Anzeigen von Routen</span><span class="sxs-lookup"><span data-stu-id="d5829-140">Display routes</span></span>


<span data-ttu-id="d5829-141">Blenden Sie eine [**MapRoute**](https://msdn.microsoft.com/library/windows/apps/dn636937) auf einem [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004) ein, indem Sie eine [**MapRouteView**](https://msdn.microsoft.com/library/windows/apps/dn637122) mit der \*\*\*\* MapRoute erstellen.</span><span class="sxs-lookup"><span data-stu-id="d5829-141">To display a [**MapRoute**](https://msdn.microsoft.com/library/windows/apps/dn636937) on a [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004), construct a [**MapRouteView**](https://msdn.microsoft.com/library/windows/apps/dn637122) with the **MapRoute**.</span></span> <span data-ttu-id="d5829-142">Fügen Sie die **MapRouteView** anschließend zur [**Routes**](https://msdn.microsoft.com/library/windows/apps/dn637047)-Auflistung von **MapControl** hinzu.</span><span class="sxs-lookup"><span data-stu-id="d5829-142">Then, add the **MapRouteView** to the [**Routes**](https://msdn.microsoft.com/library/windows/apps/dn637047) collection of the **MapControl**.</span></span>

>[!IMPORTANT]
><span data-ttu-id="d5829-143">Sie müssen einen Kartenauthentifizierungsschlüssel angeben, bevor Sie Kartendienste oder das Kartensteuerelement verwenden können.</span><span class="sxs-lookup"><span data-stu-id="d5829-143">You must specify a maps authentication key before you can use map services or the map control.</span></span> <span data-ttu-id="d5829-144">Weitere Informationen finden Sie unter [Anfordern eines Kartenauthentifizierungsschlüssels](authentication-key.md).</span><span class="sxs-lookup"><span data-stu-id="d5829-144">For more info, see [Request a maps authentication key](authentication-key.md).</span></span>

 

```csharp
using System;
using Windows.Devices.Geolocation;
using Windows.Services.Maps;
using Windows.UI;
using Windows.UI.Xaml.Controls;
using Windows.UI.Xaml.Controls.Maps;
...
private async void ShowRouteOnMap()
{
   // Start at Microsoft in Redmond, Washington.
   BasicGeoposition startLocation = new BasicGeoposition() { Latitude = 47.643, Longitude = -122.131 };

   // End at the city of Seattle, Washington.
   BasicGeoposition endLocation = new BasicGeoposition() { Latitude = 47.604, Longitude = -122.329 };


   // Get the route between the points.
   MapRouteFinderResult routeResult =
         await MapRouteFinder.GetDrivingRouteAsync(
         new Geopoint(startLocation),
         new Geopoint(endLocation),
         MapRouteOptimization.Time,
         MapRouteRestrictions.None);

   if (routeResult.Status == MapRouteFinderStatus.Success)
   {
      // Use the route to initialize a MapRouteView.
      MapRouteView viewOfRoute = new MapRouteView(routeResult.Route);
      viewOfRoute.RouteColor = Colors.Yellow;
      viewOfRoute.OutlineColor = Colors.Black;

      // Add the new MapRouteView to the Routes collection
      // of the MapControl.
      MapWithRoute.Routes.Add(viewOfRoute);

      // Fit the MapControl to the route.
      await MapWithRoute.TrySetViewBoundsAsync(
            routeResult.Route.BoundingBox,
            null,
            Windows.UI.Xaml.Controls.Maps.MapAnimationKind.None);
   }
}
```

<span data-ttu-id="d5829-145">Dieses Beispiel zeigt Folgendes in einem [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004) namens **MapWithRoute** an.</span><span class="sxs-lookup"><span data-stu-id="d5829-145">This example displays the following on a [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004) named **MapWithRoute**.</span></span>

![Kartensteuerelement mit angezeigter Route](images/routeonmap.png)

<span data-ttu-id="d5829-147">Nachfolgend finden Sie eine Version dieses Beispiels, das einen *Über*-Wegpunkt zwischen zwei *Endwegpunkten* verwendet:</span><span class="sxs-lookup"><span data-stu-id="d5829-147">Here's a version of this example that uses a *via* waypoint in between two *stop* waypoints:</span></span>

```csharp
using System;
using Windows.Devices.Geolocation;
using Windows.Services.Maps;
using Windows.UI;
using Windows.UI.Xaml.Controls;
using Windows.UI.Xaml.Controls.Maps;
...
private async void ShowRouteOnMap()
{
  Geolocator locator = new Geolocator();
  locator.DesiredAccuracyInMeters = 1;
  locator.PositionChanged += Locator_PositionChanged;

  BasicGeoposition point1 = new BasicGeoposition() { Latitude = 47.649693, Longitude = -122.144908 };
  BasicGeoposition point2 = new BasicGeoposition() { Latitude = 47.6205, Longitude = -122.3493 };
  BasicGeoposition point3 = new BasicGeoposition() { Latitude = 48.649693, Longitude = -122.144908 };

  // Get Driving Route from point A  to point B thru point C
  var path = new List<EnhancedWaypoint>();

  path.Add(new EnhancedWaypoint(new Geopoint(point1), WaypointKind.Stop));
  path.Add(new EnhancedWaypoint(new Geopoint(point2), WaypointKind.Via));
  path.Add(new EnhancedWaypoint(new Geopoint(point3), WaypointKind.Stop));

  MapRouteFinderResult routeResult =  await MapRouteFinder.GetDrivingRouteFromEnhancedWaypointsAsync(path);

  if (routeResult.Status == MapRouteFinderStatus.Success)
  {
      MapRouteView viewOfRoute = new MapRouteView(routeResult.Route);
      viewOfRoute.RouteColor = Colors.Yellow;
      viewOfRoute.OutlineColor = Colors.Black;

      myMap.Routes.Add(viewOfRoute);

      await myMap.TrySetViewBoundsAsync(
            routeResult.Route.BoundingBox,
            null,
            Windows.UI.Xaml.Controls.Maps.MapAnimationKind.None);
  }
}
```

## <a name="related-topics"></a><span data-ttu-id="d5829-148">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="d5829-148">Related topics</span></span>

* [<span data-ttu-id="d5829-149">Bing Maps Developer Center</span><span class="sxs-lookup"><span data-stu-id="d5829-149">Bing Maps Developer Center</span></span>](https://www.bingmapsportal.com/)
* [<span data-ttu-id="d5829-150">Beispiel für UWP-Karte</span><span class="sxs-lookup"><span data-stu-id="d5829-150">UWP map sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=619977)
* [<span data-ttu-id="d5829-151">Entwurfsrichtlinien für Karten</span><span class="sxs-lookup"><span data-stu-id="d5829-151">Design guidelines for maps</span></span>](https://msdn.microsoft.com/library/windows/apps/dn596102)
* [<span data-ttu-id="d5829-152">Build 2015-Video: Nutzen von Karten und Ortung über Telefon, Tablet und PC in Ihren Windows-Apps</span><span class="sxs-lookup"><span data-stu-id="d5829-152">Build 2015 video: Leveraging Maps and Location Across Phone, Tablet, and PC in Your Windows Apps</span></span>](https://channel9.msdn.com/Events/Build/2015/2-757)
* [<span data-ttu-id="d5829-153">Beispiel für eine UWP-App mit Verkehrsinformationen</span><span class="sxs-lookup"><span data-stu-id="d5829-153">UWP traffic app sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=619982)
