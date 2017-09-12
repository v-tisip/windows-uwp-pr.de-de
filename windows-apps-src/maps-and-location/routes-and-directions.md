---
author: normesta
title: Anzeigen von Routen und Wegbeschreibungen auf einer Karte
description: Fordern Sie Routen und Wegbeschreibungen an, und zeigen Sie diese in Ihrer App an.
ms.assetid: BBB4C23A-8F10-41D1-81EA-271BE01AED81
ms.author: normesta
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, Route, Karte, Standort, Wegbeschreibungen
ms.openlocfilehash: 83985d986f15602923a21db3d308931397a01767
ms.sourcegitcommit: 378382419f1fda4e4df76ffa9c8cea753d271e6a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2017
---
# <a name="display-routes-and-directions-on-a-map"></a><span data-ttu-id="afb6a-104">Anzeigen von Routen und Wegbeschreibungen auf einer Karte</span><span class="sxs-lookup"><span data-stu-id="afb6a-104">Display routes and directions on a map</span></span>


<span data-ttu-id="afb6a-105">\[ Aktualisiert für UWP-Apps unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="afb6a-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="afb6a-106">Artikel zu Windows 8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span><span class="sxs-lookup"><span data-stu-id="afb6a-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>


<span data-ttu-id="afb6a-107">Fordern Sie Routen und Wegbeschreibungen an, und zeigen Sie sie in Ihrer App an.</span><span class="sxs-lookup"><span data-stu-id="afb6a-107">Request routes and directions, and display them in your app.</span></span>

<span data-ttu-id="afb6a-108">**Tipp** Wenn Sie weitere Informationen über das Verwenden von Karten in Ihrer App benötigen, laden Sie das folgende Beispiel aus den [API-Beispielen für die Universelle Windows-Plattform](http://go.microsoft.com/fwlink/p/?LinkId=619979) auf GitHub herunter.</span><span class="sxs-lookup"><span data-stu-id="afb6a-108">**Tip** To learn more about using maps in your app, download the following sample from the [Windows-universal-samples repo](http://go.microsoft.com/fwlink/p/?LinkId=619979) on GitHub.</span></span>

-   [<span data-ttu-id="afb6a-109">Kartenbeispiel für die Universelle Windows-Plattform (UWP)</span><span class="sxs-lookup"><span data-stu-id="afb6a-109">Universal Windows Platform (UWP) map sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=619977)

<span data-ttu-id="afb6a-110">**Tipp**  Wenn die Kartenfunktion kein zentrales Feature Ihrer App ist, sollten Sie stattdessen die Windows-Karten-App starten.</span><span class="sxs-lookup"><span data-stu-id="afb6a-110">**Tip**  If mapping isn't a core feature of your app, consider launching the Windows Maps app instead.</span></span> <span data-ttu-id="afb6a-111">Sie können die URI-Schemas `bingmaps:`, `ms-drive-to:` und `ms-walk-to:` zum Starten der Windows-Karten-App für bestimmte Karten und für Turn-by-Turn-Wegbeschreibungen verwenden.</span><span class="sxs-lookup"><span data-stu-id="afb6a-111">You can use the `bingmaps:`, `ms-drive-to:`, and `ms-walk-to:` URI schemes to launch the Windows Maps app to specific maps and turn-by-turn directions.</span></span> <span data-ttu-id="afb6a-112">Weitere Informationen finden Sie unter [Starten der Windows-Karten-App](https://msdn.microsoft.com/library/windows/apps/mt228341).</span><span class="sxs-lookup"><span data-stu-id="afb6a-112">For more info, see [Launch the Windows Maps app](https://msdn.microsoft.com/library/windows/apps/mt228341).</span></span>

 

## <a name="an-intro-to-maproutefinder-results"></a><span data-ttu-id="afb6a-113">Eine Einführung in die MapRouteFinder-Ergebnisse</span><span class="sxs-lookup"><span data-stu-id="afb6a-113">An intro to MapRouteFinder results</span></span>


<span data-ttu-id="afb6a-114">Hier erfahren Sie, wie Klassen für Routen und Wegbeschreibungen zusammenhängen.</span><span class="sxs-lookup"><span data-stu-id="afb6a-114">Here's how the classes for routes and directions are related:</span></span>

-   <span data-ttu-id="afb6a-115">Die [**MapRouteFinder**](https://msdn.microsoft.com/library/windows/apps/dn636938)-Klasse verfügt über Methoden zum Abrufen von Routen und Wegbeschreibungen.</span><span class="sxs-lookup"><span data-stu-id="afb6a-115">The [**MapRouteFinder**](https://msdn.microsoft.com/library/windows/apps/dn636938) class has methods that get routes and directions.</span></span>
-   <span data-ttu-id="afb6a-116">Diese Methoden geben ein [**MapRouteFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn636939) zurück.</span><span class="sxs-lookup"><span data-stu-id="afb6a-116">These methods return a [**MapRouteFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn636939).</span></span>
-   <span data-ttu-id="afb6a-117">Das [**MapRouteFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn636939) enthält ein [**MapRoute**](https://msdn.microsoft.com/library/windows/apps/dn636937)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="afb6a-117">The [**MapRouteFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn636939) contains a [**MapRoute**](https://msdn.microsoft.com/library/windows/apps/dn636937) object.</span></span> <span data-ttu-id="afb6a-118">Auf dieses Objekt greifen Sie über die [**Route**](https://msdn.microsoft.com/library/windows/apps/dn636940)-Eigenschaft des **MapRouteFinderResult** zu.</span><span class="sxs-lookup"><span data-stu-id="afb6a-118">Access this object through the [**Route**](https://msdn.microsoft.com/library/windows/apps/dn636940) property of the **MapRouteFinderResult**.</span></span>
-   <span data-ttu-id="afb6a-119">Die [**MapRoute**](https://msdn.microsoft.com/library/windows/apps/dn636937) enthält eine Sammlung von [**MapRouteLeg**](https://msdn.microsoft.com/library/windows/apps/dn636955)-Objekten.</span><span class="sxs-lookup"><span data-stu-id="afb6a-119">The [**MapRoute**](https://msdn.microsoft.com/library/windows/apps/dn636937) contains a collection of [**MapRouteLeg**](https://msdn.microsoft.com/library/windows/apps/dn636955) objects.</span></span> <span data-ttu-id="afb6a-120">Auf diese Sammlung greifen Sie über die [**Legs**](https://msdn.microsoft.com/library/windows/apps/dn636973)-Eigenschaft der **MapRoute** zu.</span><span class="sxs-lookup"><span data-stu-id="afb6a-120">Access this collection through the [**Legs**](https://msdn.microsoft.com/library/windows/apps/dn636973) property of the **MapRoute**.</span></span>
-   <span data-ttu-id="afb6a-121">Jeder [**MapRouteLeg**](https://msdn.microsoft.com/library/windows/apps/dn636955) enthält eine Sammlung von [**MapRouteManeuver**](https://msdn.microsoft.com/library/windows/apps/dn636961)-Objekten.</span><span class="sxs-lookup"><span data-stu-id="afb6a-121">Each [**MapRouteLeg**](https://msdn.microsoft.com/library/windows/apps/dn636955) contains a collection of [**MapRouteManeuver**](https://msdn.microsoft.com/library/windows/apps/dn636961) objects.</span></span> <span data-ttu-id="afb6a-122">Auf diese Sammlung greifen Sie über die [**Maneuvers**](https://msdn.microsoft.com/library/windows/apps/dn636959)-Eigenschaft des **MapRouteLeg** zu.</span><span class="sxs-lookup"><span data-stu-id="afb6a-122">Access this collection through the [**Maneuvers**](https://msdn.microsoft.com/library/windows/apps/dn636959) property of the **MapRouteLeg**.</span></span>

## <a name="display-directions"></a><span data-ttu-id="afb6a-123">Anzeigen von Wegbeschreibungen</span><span class="sxs-lookup"><span data-stu-id="afb6a-123">Display directions</span></span>


<span data-ttu-id="afb6a-124">Rufen Sie Routen und Wegbeschreibungen für Auto und Fußgänger ab, indem Sie die Methoden der [**MapRouteFinder**](https://msdn.microsoft.com/library/windows/apps/dn636938)-Klasse aufrufen, z. B. [**GetDrivingRouteAsync**](https://msdn.microsoft.com/library/windows/apps/dn636943) oder [**GetWalkingRouteAsync**](https://msdn.microsoft.com/library/windows/apps/dn636953).</span><span class="sxs-lookup"><span data-stu-id="afb6a-124">Get a driving or walking route and directions by calling the methods of the [**MapRouteFinder**](https://msdn.microsoft.com/library/windows/apps/dn636938) class—for example, [**GetDrivingRouteAsync**](https://msdn.microsoft.com/library/windows/apps/dn636943) or [**GetWalkingRouteAsync**](https://msdn.microsoft.com/library/windows/apps/dn636953).</span></span> <span data-ttu-id="afb6a-125">Das [**MapRouteFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn636939)-Objekt enthält ein [**MapRoute**](https://msdn.microsoft.com/library/windows/apps/dn636937)-Objekt, auf das Sie über seine [**Route**](https://msdn.microsoft.com/library/windows/apps/dn636940)-Eigenschaft zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="afb6a-125">The [**MapRouteFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn636939) object contains a [**MapRoute**](https://msdn.microsoft.com/library/windows/apps/dn636937) object that you can access through its [**Route**](https://msdn.microsoft.com/library/windows/apps/dn636940) property.</span></span>

<span data-ttu-id="afb6a-126">Wenn Sie eine Route anfordern, können Sie Folgendes angeben:</span><span class="sxs-lookup"><span data-stu-id="afb6a-126">When you request a route, you can specify the following things:</span></span>

-   <span data-ttu-id="afb6a-127">Sie können nur einen Startpunkt und einen Endpunkt oder eine Reihe von Wegpunkten zur Berechnung angeben.</span><span class="sxs-lookup"><span data-stu-id="afb6a-127">You can provide a start point and end point only, or you can provide a series of waypoints to compute the route.</span></span>
-   <span data-ttu-id="afb6a-128">Sie können Optimierungen angeben, z.B. die Minimierung der Distanz.</span><span class="sxs-lookup"><span data-stu-id="afb6a-128">You can specify optimizations - for example, minimize the distance.</span></span>
-   <span data-ttu-id="afb6a-129">Sie können Einschränkungen festlegen, z. B. das Vermeiden von Autobahnen.</span><span class="sxs-lookup"><span data-stu-id="afb6a-129">You can specify restrictions - for example, avoid highways.</span></span>

<span data-ttu-id="afb6a-130">Die berechnete [**MapRoute**](https://msdn.microsoft.com/library/windows/apps/dn636937) hat Eigenschaften, die die Zeit zum Zurücklegen der Route, die Länge der Route und die Auflistung von [**MapRouteLeg**](https://msdn.microsoft.com/library/windows/apps/dn636955)-Objekten bereitstellen, die die Teilstrecken der Route enthalten.</span><span class="sxs-lookup"><span data-stu-id="afb6a-130">The computed [**MapRoute**](https://msdn.microsoft.com/library/windows/apps/dn636937) has properties that provide the time to traverse the route, the length of the route, and the collection of [**MapRouteLeg**](https://msdn.microsoft.com/library/windows/apps/dn636955) objects that contain the legs of the route.</span></span> <span data-ttu-id="afb6a-131">Jedes **MapRouteLeg**-Objekt enthält eine Auflistung von [**MapRouteManeuver**](https://msdn.microsoft.com/library/windows/apps/dn636961)-Objekten.</span><span class="sxs-lookup"><span data-stu-id="afb6a-131">Each **MapRouteLeg** object contains a collection of [**MapRouteManeuver**](https://msdn.microsoft.com/library/windows/apps/dn636961) objects.</span></span> <span data-ttu-id="afb6a-132">Das **MapRouteManeuver**-Objekt enthält eine Wegbeschreibung, auf die Sie über seine [**InstructionText**](https://msdn.microsoft.com/library/windows/apps/dn636964)-Eigenschaft zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="afb6a-132">The **MapRouteManeuver** object contains directions that you can access through its [**InstructionText**](https://msdn.microsoft.com/library/windows/apps/dn636964) property.</span></span>

<span data-ttu-id="afb6a-133">**Wichtig** Sie müssen einen Kartenauthentifizierungsschlüssel angeben, um Kartendienste verwenden zu können.</span><span class="sxs-lookup"><span data-stu-id="afb6a-133">**Important**  You must specify a maps authentication key before you can use map services.</span></span> <span data-ttu-id="afb6a-134">Weitere Informationen finden Sie unter [Anfordern eines Kartenauthentifizierungsschlüssels](authentication-key.md).</span><span class="sxs-lookup"><span data-stu-id="afb6a-134">For more info, see [Request a maps authentication key](authentication-key.md).</span></span>

 

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

<span data-ttu-id="afb6a-135">Dieses Beispiel zeigt die folgenden Ergebnisse im `tbOutputText`-Textfeld an:</span><span class="sxs-lookup"><span data-stu-id="afb6a-135">This example displays the following results to the `tbOutputText` text box.</span></span>

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

## <a name="display-routes"></a><span data-ttu-id="afb6a-136">Anzeigen von Routen</span><span class="sxs-lookup"><span data-stu-id="afb6a-136">Display routes</span></span>


<span data-ttu-id="afb6a-137">Blenden Sie eine [**MapRoute**](https://msdn.microsoft.com/library/windows/apps/dn636937) auf einem [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004) ein, indem Sie eine [**MapRouteView**](https://msdn.microsoft.com/library/windows/apps/dn637122) mit der ****MapRoute erstellen.</span><span class="sxs-lookup"><span data-stu-id="afb6a-137">To display a [**MapRoute**](https://msdn.microsoft.com/library/windows/apps/dn636937) on a [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004), construct a [**MapRouteView**](https://msdn.microsoft.com/library/windows/apps/dn637122) with the **MapRoute**.</span></span> <span data-ttu-id="afb6a-138">Fügen Sie die **MapRouteView** anschließend zur [**Routes**](https://msdn.microsoft.com/library/windows/apps/dn637047)-Auflistung von **MapControl** hinzu.</span><span class="sxs-lookup"><span data-stu-id="afb6a-138">Then, add the **MapRouteView** to the [**Routes**](https://msdn.microsoft.com/library/windows/apps/dn637047) collection of the **MapControl**.</span></span>

<span data-ttu-id="afb6a-139">**Wichtig** Sie müssen einen Kartenauthentifizierungsschlüssel angeben, um Kartendienste oder das Kartensteuerelement verwenden zu können.</span><span class="sxs-lookup"><span data-stu-id="afb6a-139">**Important**  You must specify a maps authentication key before you can use map services or the map control.</span></span> <span data-ttu-id="afb6a-140">Weitere Informationen finden Sie unter [Anfordern eines Kartenauthentifizierungsschlüssels](authentication-key.md).</span><span class="sxs-lookup"><span data-stu-id="afb6a-140">For more info, see [Request a maps authentication key](authentication-key.md).</span></span>

 

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

<span data-ttu-id="afb6a-141">Dieses Beispiel zeigt Folgendes in einem [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004) namens **MapWithRoute** an.</span><span class="sxs-lookup"><span data-stu-id="afb6a-141">This example displays the following on a [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004) named **MapWithRoute**.</span></span>

![Kartensteuerelement mit angezeigter Route](images/routeonmap.png)

## <a name="related-topics"></a><span data-ttu-id="afb6a-143">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="afb6a-143">Related topics</span></span>

* [<span data-ttu-id="afb6a-144">Bing Maps Developer Center</span><span class="sxs-lookup"><span data-stu-id="afb6a-144">Bing Maps Developer Center</span></span>](https://www.bingmapsportal.com/)
* [<span data-ttu-id="afb6a-145">Beispiel für UWP-Karte</span><span class="sxs-lookup"><span data-stu-id="afb6a-145">UWP map sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=619977)
* [<span data-ttu-id="afb6a-146">Entwurfsrichtlinien für Karten</span><span class="sxs-lookup"><span data-stu-id="afb6a-146">Design guidelines for maps</span></span>](https://msdn.microsoft.com/library/windows/apps/dn596102)
* [<span data-ttu-id="afb6a-147">Build 2015-Video: Nutzen von Karten und Ortung über Telefon, Tablet und PC in Ihren Windows-Apps</span><span class="sxs-lookup"><span data-stu-id="afb6a-147">Build 2015 video: Leveraging Maps and Location Across Phone, Tablet, and PC in Your Windows Apps</span></span>](https://channel9.msdn.com/Events/Build/2015/2-757)
* [<span data-ttu-id="afb6a-148">Beispiel für eine UWP-App mit Verkehrsinformationen</span><span class="sxs-lookup"><span data-stu-id="afb6a-148">UWP traffic app sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=619982)
