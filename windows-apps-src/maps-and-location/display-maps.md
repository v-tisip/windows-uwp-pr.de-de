---
author: normesta
title: Anzeigen von Karten mit 2D-, 3D- und Streetside-Ansichten
description: "Sie können mit der MapControl-Klasse anpassbare Karten in Ihrer App anzeigen. In diesem Thema werden auch 3D-Luftbilder und Streetside-Ansichten behandelt."
ms.assetid: 3839E00B-2C1E-4627-A45F-6DDA98D7077F
ms.author: normesta
ms.date: 07/31/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, uwp, karten, standort, kartensteuerelement, kartenansichten
ms.openlocfilehash: a926188912cf0cd36e1bc787e7c0cbc32f8ae95b
ms.sourcegitcommit: 0ebc8dca2fd9149ea163b7db9daa14520fc41db4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2017
---
# <a name="display-maps-with-2d-3d-and-streetside-views"></a><span data-ttu-id="054b4-105">Anzeigen von Karten mit 2D-, 3D- und Streetside-Ansichten</span><span class="sxs-lookup"><span data-stu-id="054b4-105">Display maps with 2D, 3D, and Streetside views</span></span>


<span data-ttu-id="054b4-106">\[ Aktualisiert für UWP-Apps unter Windows 10.</span><span class="sxs-lookup"><span data-stu-id="054b4-106">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="054b4-107">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132). \]</span><span class="sxs-lookup"><span data-stu-id="054b4-107">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>

<span data-ttu-id="054b4-108">Sie können mit der [MapControl](https://msdn.microsoft.com/library/windows/apps/dn637004)-Klasse anpassbare Karten in Ihrer App anzeigen.</span><span class="sxs-lookup"><span data-stu-id="054b4-108">Display customizable maps in your app by using the [MapControl](https://msdn.microsoft.com/library/windows/apps/dn637004) class.</span></span> <span data-ttu-id="054b4-109">In diesem Thema werden auch 3D-Luftbilder und Streetside-Ansichten behandelt.</span><span class="sxs-lookup"><span data-stu-id="054b4-109">This topic also introduces aerial 3D and Streetside views.</span></span>

> [!NOTE]
> <span data-ttu-id="054b4-110">Laden Sie das [Beispiel für Universelle Windows-Plattform (UWP)-Karten](http://go.microsoft.com/fwlink/p/?LinkId=619977) herunter, um mehr über die Verwendung von Karten in Ihrer App zu erfahren.</span><span class="sxs-lookup"><span data-stu-id="054b4-110">To learn more about using maps in your app, download the [Universal Windows Platform (UWP) map sample](http://go.microsoft.com/fwlink/p/?LinkId=619977)</span></span>

<span id="map-control" />
## <a name="the-map-control"></a><span data-ttu-id="054b4-111">Das Kartensteuerelement</span><span class="sxs-lookup"><span data-stu-id="054b4-111">The map control</span></span>

<span data-ttu-id="054b4-112">Mithilfe des Kartensteuerelements können Straßenkarten, Luftbilder, 3D-Ansichten, Wegbeschreibungen, Suchergebnisse und Verkehrsinformationen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="054b4-112">The map control can display road maps, aerial, 3D, views, directions, search results, and traffic.</span></span> <span data-ttu-id="054b4-113">In einer Karte können Sie die Position des Benutzers, Wegbeschreibungen und interessante Orte anzeigen.</span><span class="sxs-lookup"><span data-stu-id="054b4-113">On a map, you can display the user's location, directions, and points of interest.</span></span> <span data-ttu-id="054b4-114">Zudem kann eine Karte 3D-Luftbilder, Streetside-Ansichten, Verkehrsinformationen, öffentliche Verkehrsmittel und lokale Unternehmen enthalten.</span><span class="sxs-lookup"><span data-stu-id="054b4-114">A map can also show aerial 3D views, Streetside views, traffic, transit, and local businesses.</span></span>

<span data-ttu-id="054b4-115">Verwenden Sie ein Kartensteuerelement, wenn Sie in Ihrer App eine Karte benötigen, auf der Benutzer App-spezifische oder allgemeine geografische Informationen anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="054b4-115">Use a map control when you want a map within your app that allows users to view app-specific or general geographic information.</span></span> <span data-ttu-id="054b4-116">Wenn die App ein Kartensteuerelement enthält, müssen Benutzer die App nicht verlassen, um diese Informationen zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="054b4-116">Having a map control in your app means that users don't have to go outside your app to get that information.</span></span>

> [!NOTE]
><span data-ttu-id="054b4-117">Wenn es Ihnen nichts ausmacht, dass Benutzer dafür die App verlassen, können Sie diese Informationen auch mit der Windows-Karten-App bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="054b4-117">If you don't mind users going outside your app, consider using the Windows Maps app to provide that information.</span></span> <span data-ttu-id="054b4-118">Ihre App kann die Windows-Karten-App starten, um bestimmte Karten, Wegbeschreibungen und Suchergebnisse anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="054b4-118">Your app can launch the Windows Maps app to display specific maps, directions, and search results.</span></span> <span data-ttu-id="054b4-119">Weitere Informationen finden Sie unter [Starten der Windows-Karten-App](https://msdn.microsoft.com/library/windows/apps/mt228341).</span><span class="sxs-lookup"><span data-stu-id="054b4-119">For more info, see [Launch the Windows Maps app](https://msdn.microsoft.com/library/windows/apps/mt228341).</span></span>

## <a name="add-the-map-control-to-your-app"></a><span data-ttu-id="054b4-120">Hinzufügen des Kartensteuerelements zur App</span><span class="sxs-lookup"><span data-stu-id="054b4-120">Add the map control to your app</span></span>


<span data-ttu-id="054b4-121">Zeigen Sie eine Karte auf einer XAML-Seite durch Hinzufügen eines [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004) an.</span><span class="sxs-lookup"><span data-stu-id="054b4-121">Display a map on a XAML page by adding a [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004).</span></span> <span data-ttu-id="054b4-122">Um **MapControl** zu verwenden, müssen Sie den Namespace [**Windows.UI.Xaml.Controls.Maps**](https://msdn.microsoft.com/library/windows/apps/dn610751) in der XAML-Seite oder im Code deklarieren.</span><span class="sxs-lookup"><span data-stu-id="054b4-122">To use the **MapControl**, you must declare the [**Windows.UI.Xaml.Controls.Maps**](https://msdn.microsoft.com/library/windows/apps/dn610751) namespace in the XAML page or in your code.</span></span> <span data-ttu-id="054b4-123">Wenn Sie das Steuerelement der Toolbox entnehmen, wird die Namespacedeklaration automatisch hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="054b4-123">If you drag the control from the Toolbox, this namespace declaration is added automatically.</span></span> <span data-ttu-id="054b4-124">Wenn Sie **MapControl** manuell zur XAML-Seite hinzufügen, müssen Sie die Namespacedeklaration oben auf der Seite manuell hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="054b4-124">If you add the **MapControl** to the XAML page manually, you must add the namespace declaration manually at the top of the page.</span></span>

<span data-ttu-id="054b4-125">Das folgende Beispiel zeigt ein einfaches Kartensteuerelement. Außerdem wird die Karte so konfiguriert, dass Toucheingaben möglich sind und gleichzeitig die Steuerelemente für Zoom und Neigung angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="054b4-125">The following example displays a basic map control and configures the map to display the zoom and tilt controls in addition to accepting touch inputs.</span></span> <span data-ttu-id="054b4-126">Weitere Informationen zum Anpassen der Darstellung der Karte finden Sie unter [Konfigurieren der Karte](#mapconfig).</span><span class="sxs-lookup"><span data-stu-id="054b4-126">For more info about customizing the appearance of the map, see [Configure the map](#mapconfig).</span></span>

```xml
<Page
    x:Class="MapsAndLocation1.DisplayMaps"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:MapsAndLocation1"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    xmlns:Maps="using:Windows.UI.Xaml.Controls.Maps"
    mc:Ignorable="d">

 <Grid x:Name="pageGrid" Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">

    <Maps:MapControl
       x:Name="MapControl1"            
       ZoomInteractionMode="GestureAndControl"
       TiltInteractionMode="GestureAndControl"   
       MapServiceToken="EnterYourAuthenticationKeyHere"/>

 </Grid>
</Page>
```

<span data-ttu-id="054b4-127">Wenn Sie das Kartensteuerelement im Code hinzufügen, müssen Sie den Namespace oben in der Codedatei manuell deklarieren.</span><span class="sxs-lookup"><span data-stu-id="054b4-127">If you add the map control in your code, you must declare the namespace manually at the top of the code file.</span></span>

```csharp
using Windows.UI.Xaml.Controls.Maps;
...

// Add the MapControl and the specify maps authentication key.
MapControl MapControl2 = new MapControl();
MapControl2.ZoomInteractionMode = MapInteractionMode.GestureAndControl;
MapControl2.TiltInteractionMode = MapInteractionMode.GestureAndControl;
MapControl2.MapServiceToken = "EnterYourAuthenticationKeyHere";
pageGrid.Children.Add(MapControl2);
```

## <a name="get-and-set-a-maps-authentication-key"></a><span data-ttu-id="054b4-128">Abrufen und Festlegen eines Kartenauthentifizierungsschlüssels</span><span class="sxs-lookup"><span data-stu-id="054b4-128">Get and set a maps authentication key</span></span>


<span data-ttu-id="054b4-129">Bevor Sie [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004) und Kartendienste verwenden können, müssen Sie den Kartenauthentifizierungsschlüssel als Wert für die [**MapServiceToken**](https://msdn.microsoft.com/library/windows/apps/dn637036)-Eigenschaft angeben.</span><span class="sxs-lookup"><span data-stu-id="054b4-129">Before you can use [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004) and map services, you must specify the maps authentication key as the value of the [**MapServiceToken**](https://msdn.microsoft.com/library/windows/apps/dn637036) property.</span></span> <span data-ttu-id="054b4-130">Ersetzen Sie in den vorherigen Beispielen `EnterYourAuthenticationKeyHere` durch den Schlüssel, den Sie über das [Bing Maps Developer Center](https://www.bingmapsportal.com/) abgerufen haben.</span><span class="sxs-lookup"><span data-stu-id="054b4-130">In the previous examples, replace `EnterYourAuthenticationKeyHere` with the key you get from the [Bing Maps Developer Center](https://www.bingmapsportal.com/).</span></span> <span data-ttu-id="054b4-131">Bis Sie den Kartenauthentifizierungsschlüssel angeben, wird unterhalb des Steuerelements weiterhin der Text **Warnung: MapServiceToken wurde nicht angegeben** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="054b4-131">The text **Warning: MapServiceToken not specified** continues to appear below the control until you specify the maps authentication key.</span></span> <span data-ttu-id="054b4-132">Weitere Informationen zum Abrufen und Festlegen eines Kartenauthentifizierungsschlüssels finden Sie unter [Anfordern eines Kartenauthentifizierungsschlüssels](authentication-key.md).</span><span class="sxs-lookup"><span data-stu-id="054b4-132">For more info about getting and setting a maps authentication key, see [Request a maps authentication key](authentication-key.md).</span></span>

## <a name="set-a-starting-location-for-the-map"></a><span data-ttu-id="054b4-133">Festlegen einer Ausgangsposition für die Karte</span><span class="sxs-lookup"><span data-stu-id="054b4-133">Set a starting location for the map</span></span>


<span data-ttu-id="054b4-134">Legen Sie die Position fest, die auf der Karte angezeigt werden soll, indem Sie die [**Center**](https://msdn.microsoft.com/library/windows/apps/dn637005)-Eigenschaft von [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004) im Code angeben oder die Eigenschaft im XAML-Markup binden.</span><span class="sxs-lookup"><span data-stu-id="054b4-134">Set the location to display on the map by specifying the [**Center**](https://msdn.microsoft.com/library/windows/apps/dn637005) property of the [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004) in your code or by binding the property in your XAML markup.</span></span> <span data-ttu-id="054b4-135">Im folgenden Beispiel wird eine Karte mit Seattle in der Mitte angezeigt.</span><span class="sxs-lookup"><span data-stu-id="054b4-135">The following example displays a map with the city of Seattle as its center.</span></span>

> [!NOTE]
> <span data-ttu-id="054b4-136">Da eine Zeichenfolge nicht in einen [**Geopoint**](https://msdn.microsoft.com/library/windows/apps/dn263675) konvertiert werden kann, können Sie nur dann einen Wert für die [**Center**](https://msdn.microsoft.com/library/windows/apps/dn637005)-Eigenschaft im XAML-Markup festlegen, wenn Sie die Datenbindung verwenden.</span><span class="sxs-lookup"><span data-stu-id="054b4-136">Since a string can't be converted to a [**Geopoint**](https://msdn.microsoft.com/library/windows/apps/dn263675), you can't specify a value for the [**Center**](https://msdn.microsoft.com/library/windows/apps/dn637005) property in XAML markup unless you use data binding.</span></span> <span data-ttu-id="054b4-137">(Diese Einschränkung gilt auch für die angefügte Eigenschaft [**MapControl.Location**](https://msdn.microsoft.com/library/windows/apps/dn653264).</span><span class="sxs-lookup"><span data-stu-id="054b4-137">(This limitation also applies to the [**MapControl.Location**](https://msdn.microsoft.com/library/windows/apps/dn653264) attached property.)</span></span>

 
```csharp
protected override void OnNavigatedTo(NavigationEventArgs e)
{
   // Specify a known location.
   BasicGeoposition cityPosition = new BasicGeoposition() { Latitude = 47.604, Longitude = -122.329 };
   Geopoint cityCenter = new Geopoint(cityPosition);

   // Set the map location.
   MapControl1.Center = cityCenter;
   MapControl1.ZoomLevel = 12;
   MapControl1.LandmarksVisible = true;
}
```

![Beispiel für das Kartensteuerelement](images/displaymapsexample1.png)

## <a name="set-the-current-location-of-the-map"></a><span data-ttu-id="054b4-139">Festlegen der aktuellen Kartenposition</span><span class="sxs-lookup"><span data-stu-id="054b4-139">Set the current location of the map</span></span>

<span data-ttu-id="054b4-140">Bevor die App auf die Position des Benutzers zugreifen kann, muss die App die [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/dn859152)-Methode aufrufen.</span><span class="sxs-lookup"><span data-stu-id="054b4-140">Before your app can access the user’s location, your app must call the [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/dn859152) method.</span></span> <span data-ttu-id="054b4-141">Zu diesem Zeitpunkt muss sich Ihre App im Vordergrund befinden, und **RequestAccessAsync** muss vom UI-Thread aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="054b4-141">At that time, your app must be in the foreground and **RequestAccessAsync** must be called from the UI thread.</span></span> <span data-ttu-id="054b4-142">Solange der Benutzer Ihrer App keinen Zugriff auf seine Position gewährt, kann Ihre App nicht auf Positionsdaten zugreifen.</span><span class="sxs-lookup"><span data-stu-id="054b4-142">Until the user grants your app permission to their location, your app can't access location data.</span></span>

<span data-ttu-id="054b4-143">Rufen Sie mit der [**GetGeopositionAsync**](https://msdn.microsoft.com/library/windows/apps/hh973536)-Methode der Klasse [**Geolocator**](https://msdn.microsoft.com/library/windows/apps/br225534) die aktuelle Position des Geräts ab (wenn die Position verfügbar ist).</span><span class="sxs-lookup"><span data-stu-id="054b4-143">Get the current location of the device (if location is available) by using the [**GetGeopositionAsync**](https://msdn.microsoft.com/library/windows/apps/hh973536) method of the [**Geolocator**](https://msdn.microsoft.com/library/windows/apps/br225534) class.</span></span> <span data-ttu-id="054b4-144">Zum Abrufen des entsprechenden [**Geopoint**](https://msdn.microsoft.com/library/windows/apps/dn263675) verwenden Sie die [**Point**](https://msdn.microsoft.com/library/windows/apps/dn263665)-Eigenschaft der Geoposition-Geokoordinate.</span><span class="sxs-lookup"><span data-stu-id="054b4-144">To obtain the corresponding [**Geopoint**](https://msdn.microsoft.com/library/windows/apps/dn263675), use the [**Point**](https://msdn.microsoft.com/library/windows/apps/dn263665) property of the geoposition's geocoordinate.</span></span> <span data-ttu-id="054b4-145">Weitere Informationen finden Sie unter [Abrufen der aktuellen Position](get-location.md).</span><span class="sxs-lookup"><span data-stu-id="054b4-145">For more info, see [Get current location](get-location.md).</span></span>

```csharp
// Set your current location.
var accessStatus = await Geolocator.RequestAccessAsync();
switch (accessStatus)
{
   case GeolocationAccessStatus.Allowed:

      // Get the current location.
      Geolocator geolocator = new Geolocator();
      Geoposition pos = await geolocator.GetGeopositionAsync();
      Geopoint myLocation = pos.Coordinate.Point;

      // Set the map location.
      MapControl1.Center = myLocation;
      MapControl1.ZoomLevel = 12;
      MapControl1.LandmarksVisible = true;
      break;

   case GeolocationAccessStatus.Denied:
      // Handle the case  if access to location is denied.
      break;

   case GeolocationAccessStatus.Unspecified:
      // Handle the case if  an unspecified error occurs.
      break;
}
```

<span data-ttu-id="054b4-146">Beim Anzeigen der Geräteposition auf einer Karte sollten Sie für das Anzeigen von Grafiken und Festlegen des Zoomfaktors die Genauigkeit der Positionsdaten berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="054b4-146">When you display your device's location on a map, consider displaying graphics and setting the zoom level based on the accuracy of the location data.</span></span> <span data-ttu-id="054b4-147">Weitere Informationen finden Sie unter [Richtlinien für Apps mit Standortbestimmung](https://msdn.microsoft.com/library/windows/apps/hh465148).</span><span class="sxs-lookup"><span data-stu-id="054b4-147">For more info, see [Guidelines for location-aware apps](https://msdn.microsoft.com/library/windows/apps/hh465148).</span></span>

## <a name="change-the-location-of-the-map"></a><span data-ttu-id="054b4-148">Ändern der Kartenposition</span><span class="sxs-lookup"><span data-stu-id="054b4-148">Change the location of the map</span></span>

<span data-ttu-id="054b4-149">Rufen Sie zum Ändern der Position, die in einer 2D-Karte angezeigt wird, eine der Überladungen der [**TrySetViewAsync**](https://msdn.microsoft.com/library/windows/apps/dn637060)-Methode auf.</span><span class="sxs-lookup"><span data-stu-id="054b4-149">To change the location that appears in a 2D map, call one of the overloads of the [**TrySetViewAsync**](https://msdn.microsoft.com/library/windows/apps/dn637060) method.</span></span> <span data-ttu-id="054b4-150">Verwenden Sie diese Methode, um neue Werte für [**Center**](https://msdn.microsoft.com/library/windows/apps/dn637005), [**ZoomLevel**](https://msdn.microsoft.com/library/windows/apps/dn637068), [**Heading**](https://msdn.microsoft.com/library/windows/apps/dn637019) und [**Pitch**](https://msdn.microsoft.com/library/windows/apps/dn637044) anzugeben.</span><span class="sxs-lookup"><span data-stu-id="054b4-150">Use that method to specify new values for [**Center**](https://msdn.microsoft.com/library/windows/apps/dn637005), [**ZoomLevel**](https://msdn.microsoft.com/library/windows/apps/dn637068), [**Heading**](https://msdn.microsoft.com/library/windows/apps/dn637019), and [**Pitch**](https://msdn.microsoft.com/library/windows/apps/dn637044).</span></span> <span data-ttu-id="054b4-151">Darüber hinaus können Sie eine optionale Animation angeben, die beim Ändern der Ansicht angezeigt werden soll, indem Sie eine Konstante aus der Enumeration [**MapAnimationKind**](https://msdn.microsoft.com/library/windows/apps/dn637002) angeben.</span><span class="sxs-lookup"><span data-stu-id="054b4-151">You can also specify an optional animation to use when the view changes by providing a constant from the [**MapAnimationKind**](https://msdn.microsoft.com/library/windows/apps/dn637002) enumeration.</span></span>

<span data-ttu-id="054b4-152">Verwenden Sie zum Ändern des Standorts einer 3D-Karte stattdessen die [**TrySetSceneAsync**](https://msdn.microsoft.com/library/windows/apps/dn974296)-Methode.</span><span class="sxs-lookup"><span data-stu-id="054b4-152">To change the location of a 3D map, use the [**TrySetSceneAsync**](https://msdn.microsoft.com/library/windows/apps/dn974296) method instead.</span></span> <span data-ttu-id="054b4-153">Weitere Informationen finden Sie unter [Anzeigen von 3D-Ansichten](#display3d).</span><span class="sxs-lookup"><span data-stu-id="054b4-153">For more info, see [Display 3D views](#display3d).</span></span>

<span data-ttu-id="054b4-154">Rufen Sie die [**TrySetViewBoundsAsync**](https://msdn.microsoft.com/library/windows/apps/dn637065)-Methode zum Anzeigen der Inhalte eines [**GeoboundingBox**](https://msdn.microsoft.com/library/windows/apps/dn607949) auf der Karte auf.</span><span class="sxs-lookup"><span data-stu-id="054b4-154">Call the [**TrySetViewBoundsAsync**](https://msdn.microsoft.com/library/windows/apps/dn637065) method to display the contents of a [**GeoboundingBox**](https://msdn.microsoft.com/library/windows/apps/dn607949) on the map.</span></span> <span data-ttu-id="054b4-155">Diese Methode verwenden Sie beispielsweise, um eine Route oder einen Abschnitt einer Route auf der Karte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="054b4-155">Use this method, for example, to display a route or a portion of a route on the map.</span></span> <span data-ttu-id="054b4-156">Weitere Informationen finden Sie unter [Anzeigen von Routen und Wegbeschreibungen auf einer Karte](routes-and-directions.md).</span><span class="sxs-lookup"><span data-stu-id="054b4-156">For more info, see [Display routes and directions on a map](routes-and-directions.md).</span></span>

## <a name="customize-the-appearance-of-the-map"></a><span data-ttu-id="054b4-157">Hier können Sie das Aussehen der Karte anpassen.</span><span class="sxs-lookup"><span data-stu-id="054b4-157">Customize the appearance of the map</span></span>

<span data-ttu-id="054b4-158">Um das Aussehen und Verhalten der Karte anzupassen, legen Sie die [**StyleSheet**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapcontrol#Windows_UI_Xaml_Controls_Maps_MapControl_StyleSheet)-Eigenschaft des Kartensteuerelements auf eines der vorhandenen [**MapStyleSheet**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapstylesheet) Objekte fest.</span><span class="sxs-lookup"><span data-stu-id="054b4-158">To customize the look and feel of the map, set the [**StyleSheet**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapcontrol#Windows_UI_Xaml_Controls_Maps_MapControl_StyleSheet) property of the map control to any of the existing [**MapStyleSheet**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapstylesheet) objects.</span></span>

```csharp
myMap.StyleSheet = MapStyleSheet.RoadDark();
```

![Karte im dunklen Stil](images/style-dark.png)

<span data-ttu-id="054b4-160">Sie können auch JSON verwenden, um benutzerdefinierte Stile zu definieren und dann JSON zum Erstellen eines [**MapStyleSheet**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapstylesheet) Objekt nutzen.</span><span class="sxs-lookup"><span data-stu-id="054b4-160">You can also use JSON to define custom styles and then use that JSON to create a [**MapStyleSheet**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapstylesheet) object.</span></span>

```csharp
myMap.StyleSheet = MapStyleSheet.ParseFromJson(@"
    {
        ""version"": ""1.0"",
        ""settings"": {
            ""landColor"": ""#FFFFFF"",
            ""spaceColor"": ""#000000""
        },
        ""elements"": {
            ""mapElement"": {
                ""labelColor"": ""#000000"",
                ""labelOutlineColor"": ""#FFFFFF""
            },
            ""water"": {
                ""fillColor"": ""#DDDDDD""
            },
            ""area"": {
                ""fillColor"": ""#EEEEEE""
            },
            ""political"": {
                ""borderStrokeColor"": ""#CCCCCC"",
                ""borderOutlineColor"": ""#00000000""
            }
        }
    }
");
```

![Karte im benutzerdefinierten Stil](images/style-custom.png)

<span data-ttu-id="054b4-162">Die vollständige JSON-Referenz finden Sie unter [Karten-Stylesheet-Referenz](elements-of-map-style-sheet.md).</span><span class="sxs-lookup"><span data-stu-id="054b4-162">For the complete JSON entry reference, see [Map style sheet reference](elements-of-map-style-sheet.md).</span></span>

<span data-ttu-id="054b4-163">Können Sie mit einem vorhandenen Sheet beginnen und dann JSON verwenden, um alle gewünschten Elemente zu überschreiben.</span><span class="sxs-lookup"><span data-stu-id="054b4-163">You can start with an existing sheet and then use JSON to override any elements that you want.</span></span> <span data-ttu-id="054b4-164">Dieses Beispiel beginnt mit einem vorhandenen Stil und verwendet JSON, um nur die Farbe der Wasserbereiche zu ändern.</span><span class="sxs-lookup"><span data-stu-id="054b4-164">This example, starts with an existing style and uses JSON to change only the color of water areas.</span></span>

```csharp
MapStyleSheet customSheet = MapStyleSheet.ParseFromJson(@"
    {
        ""version"": ""1.0"",
        ""elements"": {
            ""water"": {
                ""fillColor"": ""#DDDDDD""
            }
        }
    }
");

MapStyleSheet builtInSheet = MapStyleSheet.RoadDark();

myMap.StyleSheet = MapStyleSheet.Combine(new List<MapStyleSheet> { builtInSheet, customSheet });
```

![Kombinierter Kartenstil](images/style-combined.png)

>[!NOTE]
><span data-ttu-id="054b4-166">Stile, die Sie in einem zweiten Stylesheet definieren, überschreiben die Stile in der ersten.</span><span class="sxs-lookup"><span data-stu-id="054b4-166">Styles that you define in the second style sheet override the styles in the first.</span></span>

## <a name="change-the-orientation-and-perspective-of-the-map"></a><span data-ttu-id="054b4-167">Ändern der Ausrichtung und Perspektive der Karte</span><span class="sxs-lookup"><span data-stu-id="054b4-167">Change the orientation and perspective of the map</span></span>

<span data-ttu-id="054b4-168">Vergrößern, verkleinern, drehen Sie und kippen Sie der Kamera der Karte, um den passen Winkel für den gewünschten Effekt zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="054b4-168">Zoom in, zoom out, rotate, and tilt the map's camera to get just the right angle for the effect that you want.</span></span> <span data-ttu-id="054b4-169">Versuchen Sie diese Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="054b4-169">Try these properties.</span></span>

-   <span data-ttu-id="054b4-170">Legen Sie das **Zentrum** der Karte auf einen geografischen Punkt fest, indem Sie die Eigenschaft [**Center**](https://msdn.microsoft.com/library/windows/apps/dn637005) festlegen.</span><span class="sxs-lookup"><span data-stu-id="054b4-170">Set the **center** of the map to a geographic point by setting the [**Center**](https://msdn.microsoft.com/library/windows/apps/dn637005) property.</span></span>
-   <span data-ttu-id="054b4-171">Legen Sie die **Zoomstufe** der Karte fest, indem Sie die Eigenschaft [**ZoomLevel**](https://msdn.microsoft.com/library/windows/apps/dn637068) auf einen Wert zwischen 1 und 20 Grad festlegen.</span><span class="sxs-lookup"><span data-stu-id="054b4-171">Set the **zoom level** of the map by setting the [**ZoomLevel**](https://msdn.microsoft.com/library/windows/apps/dn637068) property to a value between 1 and 20.</span></span>
-   <span data-ttu-id="054b4-172">Legen Sie die **Rotation** der Karte fest, indem Sie die Eigenschaft [**Heading**](https://msdn.microsoft.com/library/windows/apps/dn637019) festlegen, wobei 0 oder 360 Grad = Nord, 90 = Ost, 180 = Süd und 270 =West ist.</span><span class="sxs-lookup"><span data-stu-id="054b4-172">Set the **rotation** of the map by setting the [**Heading**](https://msdn.microsoft.com/library/windows/apps/dn637019) property, where 0 or 360 degrees = North, 90 = East, 180 = South, and 270 = West.</span></span>
-   <span data-ttu-id="054b4-173">Legen Sie die **Neigung** der Karte fest, indem Sie die Eigenschaft [**DesiredPitch**](https://msdn.microsoft.com/library/windows/apps/dn637012) auf einen Wert zwischen 0 und 65 Grad festlegen.</span><span class="sxs-lookup"><span data-stu-id="054b4-173">Set the **tilt** of the map by setting the [**DesiredPitch**](https://msdn.microsoft.com/library/windows/apps/dn637012) property to a value between 0 and 65 degrees.</span></span>

## <a name="show-and-hide-map-features"></a><span data-ttu-id="054b4-174">Ein- und Ausblenden von Kartefeatures</span><span class="sxs-lookup"><span data-stu-id="054b4-174">Show and hide map features</span></span>

<span data-ttu-id="054b4-175">Ausblenden und Anzeigen von Features wie Straßen und Orten, indem Sie die Werte der folgenden Eigenschaften von [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004) festlegen.</span><span class="sxs-lookup"><span data-stu-id="054b4-175">Show or hide map features such as roads and landmarks by setting the values of the following properties of the [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004).</span></span>

-   <span data-ttu-id="054b4-176">Zeigen Sie **Gebäude und Sehenswürdigkeiten** auf der Karte an, indem Sie die Eigenschaft [**LandmarksVisible**](https://msdn.microsoft.com/library/windows/apps/dn637023) aktivieren oder deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="054b4-176">Display **buildings and landmarks** on the map by enabling or disabling the [**LandmarksVisible**](https://msdn.microsoft.com/library/windows/apps/dn637023) property.</span></span>
-   <span data-ttu-id="054b4-177">Zeigen Sie **Features für Fußgänger** auf der Karte an, wie öffentliche Treppen, indem Sie die Eigenschaft [**PedestrianFeaturesVisible**](https://msdn.microsoft.com/library/windows/apps/dn637042) aktivieren oder deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="054b4-177">Display **pedestrian features** such as public stairs on the map by enabling or disabling the [**PedestrianFeaturesVisible**](https://msdn.microsoft.com/library/windows/apps/dn637042) property.</span></span>
-   <span data-ttu-id="054b4-178">Zeigen Sie den **Verkehr** auf der Seite an, indem Sie die Eigenschaft [**TrafficFlowVisible**](https://msdn.microsoft.com/library/windows/apps/dn637055) aktivieren oder deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="054b4-178">Display **traffic** on the map by enabling or disabling the [**TrafficFlowVisible**](https://msdn.microsoft.com/library/windows/apps/dn637055) property.</span></span>
-   <span data-ttu-id="054b4-179">Geben Sie an, ob das **Wasserzeichen** auf der Karte angezeigt wird, indem Sie die Eigenschaft [**WatermarkMode**](https://msdn.microsoft.com/library/windows/apps/dn637066) auf eine der [**MapWatermarkMode**](https://msdn.microsoft.com/library/windows/apps/dn610749)-Konstanten festlegen.</span><span class="sxs-lookup"><span data-stu-id="054b4-179">Specify whether the **watermark** is displayed on the map by setting the [**WatermarkMode**](https://msdn.microsoft.com/library/windows/apps/dn637066) property to one of the [**MapWatermarkMode**](https://msdn.microsoft.com/library/windows/apps/dn610749) constants.</span></span>
-   <span data-ttu-id="054b4-180">Zeigen Sie eine **Auto- oder Fußgängerroute** auf der Karte an, indem Sie [**MapRouteView**](https://msdn.microsoft.com/library/windows/apps/dn637122) zur Sammlung [**Routes**](https://msdn.microsoft.com/library/windows/apps/dn637047) des Kartensteuerelements hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="054b4-180">Display a **driving or walking route** on the map by adding a [**MapRouteView**](https://msdn.microsoft.com/library/windows/apps/dn637122) to the [**Routes**](https://msdn.microsoft.com/library/windows/apps/dn637047) collection of the Map control.</span></span> <span data-ttu-id="054b4-181">Weitere Informationen und ein Beispiel finden Sie in [Anzeigen von Routen und Wegbeschreibungen auf einer Karte](routes-and-directions.md).</span><span class="sxs-lookup"><span data-stu-id="054b4-181">For more info and an example, see [Display routes and directions on a map](routes-and-directions.md).</span></span>

<span data-ttu-id="054b4-182">Informationen zum Anzeigen von Ortsmarken, Formen und XAML-Steuerelementen in [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004) finden Sie unter [Anzeigen von interessanten Orten (POI) auf einer Karte](display-poi.md).</span><span class="sxs-lookup"><span data-stu-id="054b4-182">For info about how to display pushpins, shapes, and XAML controls in the [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004), see [Display points of interest (POI) on a map](display-poi.md).</span></span>

## <a name="display-streetside-views"></a><span data-ttu-id="054b4-183">Anzeigen von Streetside-Ansichten</span><span class="sxs-lookup"><span data-stu-id="054b4-183">Display Streetside views</span></span>


<span data-ttu-id="054b4-184">Bei einer Streetside-Ansicht handelt es sich um die Straßenansicht eines Standorts, die über dem Kartensteuerelement angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="054b4-184">A Streetside view is a street-level perspective of a location that appears on top of the map control.</span></span>

![Beispiel für eine Streetside-Ansicht des Kartensteuerelements](images/onlystreetside-730width.png)

<span data-ttu-id="054b4-186">Betrachten Sie die Vorgänge „innerhalb“ der Streetside-Ansicht getrennt von der ursprünglich im Kartensteuerelement angezeigten Karte.</span><span class="sxs-lookup"><span data-stu-id="054b4-186">Consider the experience "inside" the Streetside view separate from the map originally displayed in the map control.</span></span> <span data-ttu-id="054b4-187">Wenn z.B. der Standort in der Streetside-Ansicht geändert wird, führt dies nicht zu einer Änderung der Position oder der Darstellung der Karte "unter" der Streetside-Ansicht.</span><span class="sxs-lookup"><span data-stu-id="054b4-187">For example, changing the location in the Streetside view does not change the location or appearance of the map "under" the Streetside view.</span></span> <span data-ttu-id="054b4-188">Nach dem Schließen der Streetside-Ansicht (durch Klicken auf **X** oben rechts im Steuerelement) bleibt die ursprüngliche Karte unverändert.</span><span class="sxs-lookup"><span data-stu-id="054b4-188">After you close the Streetside view (by clicking the **X** in the upper right corner of the control), the original map remains unchanged.</span></span>

<span data-ttu-id="054b4-189">So zeigen Sie eine Streetside-Ansicht an</span><span class="sxs-lookup"><span data-stu-id="054b4-189">To display a Streetside view</span></span>

1.  <span data-ttu-id="054b4-190">Überprüfen Sie mittels [**IsStreetsideSupported**](https://msdn.microsoft.com/library/windows/apps/dn974271), ob Streetside-Ansichten auf dem Gerät unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="054b4-190">Determine if Streetside views are supported on the device by checking [**IsStreetsideSupported**](https://msdn.microsoft.com/library/windows/apps/dn974271).</span></span>
2.  <span data-ttu-id="054b4-191">Wenn Streetside-Ansichten unterstützt werden, erstellen Sie in der Nähe der angegebenen Position [**StreetsidePanorama**](https://msdn.microsoft.com/library/windows/apps/dn974360), indem Sie [**FindNearbyAsync**](https://msdn.microsoft.com/library/windows/apps/dn974361) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="054b4-191">If Streetside view is supported, create a [**StreetsidePanorama**](https://msdn.microsoft.com/library/windows/apps/dn974360) near the specified location by calling [**FindNearbyAsync**](https://msdn.microsoft.com/library/windows/apps/dn974361).</span></span>
3.  <span data-ttu-id="054b4-192">Bestimmen Sie, ob ein Panorama in der Nähe gefunden wurde, indem Sie überprüfen, ob [**StreetsidePanorama**](https://msdn.microsoft.com/library/windows/apps/dn974360) ungleich NULL ist.</span><span class="sxs-lookup"><span data-stu-id="054b4-192">Determine if a nearby panorama was found by checking if the [**StreetsidePanorama**](https://msdn.microsoft.com/library/windows/apps/dn974360) is not null</span></span>
4.  <span data-ttu-id="054b4-193">Wenn ein Panorama in der Nähe gefunden wurde, erstellen Sie eine [**StreetsideExperience**](https://msdn.microsoft.com/library/windows/apps/dn974356) für die [**CustomExperience**](https://msdn.microsoft.com/library/windows/apps/dn974263)-Eigenschaft des Kartensteuerelements.</span><span class="sxs-lookup"><span data-stu-id="054b4-193">If a nearby panorama was found, create a [**StreetsideExperience**](https://msdn.microsoft.com/library/windows/apps/dn974356) for the map control's [**CustomExperience**](https://msdn.microsoft.com/library/windows/apps/dn974263) property.</span></span>

<span data-ttu-id="054b4-194">In diesem Beispiel wird gezeigt, wie Sie eine Streetside-Ansicht ähnlich wie in der Abbildung oben anzeigen.</span><span class="sxs-lookup"><span data-stu-id="054b4-194">This example shows how to display a Streetside view similar to the previous image.</span></span>

<span data-ttu-id="054b4-195">**Hinweis** Die Übersichtskarte wird nicht angezeigt, wenn das Kartensteuerelement zu klein bemessen ist.</span><span class="sxs-lookup"><span data-stu-id="054b4-195">**Note**  The overview map will not appear if the map control is sized too small.</span></span>

 

```csharp
private async void showStreetsideView()
{
   // Check if Streetside is supported.
   if (MapControl1.IsStreetsideSupported)
   {
      // Find a panorama near Avenue Gustave Eiffel.
      BasicGeoposition cityPosition = new BasicGeoposition() { Latitude = 48.858, Longitude = 2.295};
      Geopoint cityCenter = new Geopoint(cityPosition);
      StreetsidePanorama panoramaNearCity = await StreetsidePanorama.FindNearbyAsync(cityCenter);

      // Set the Streetside view if a panorama exists.
      if (panoramaNearCity != null)
      {
         // Create the Streetside view.
         StreetsideExperience ssView = new StreetsideExperience(panoramaNearCity);
         ssView.OverviewMapVisible = true;
         MapControl1.CustomExperience = ssView;
      }
   }
   else
   {
      // If Streetside is not supported
      ContentDialog viewNotSupportedDialog = new ContentDialog()
      {
         Title = "Streetside is not supported",
         Content ="\nStreetside views are not supported on this device.",
         PrimaryButtonText = "OK"
      };
      await viewNotSupportedDialog.ShowAsync();            
   }
}
```

## <a name="display-aerial-3d-views"></a><span data-ttu-id="054b4-196">Anzeigen von 3D-Luftbildern</span><span class="sxs-lookup"><span data-stu-id="054b4-196">Display aerial 3D views</span></span>


<span data-ttu-id="054b4-197">Mithilfe der Klasse [**MapScene**](https://msdn.microsoft.com/library/windows/apps/dn974329) können Sie eine 3D-Perspektive der Karte angeben.</span><span class="sxs-lookup"><span data-stu-id="054b4-197">Specify a 3D perspective of the map by using the [**MapScene**](https://msdn.microsoft.com/library/windows/apps/dn974329) class.</span></span> <span data-ttu-id="054b4-198">Die Kartenszene stellt die 3D-Ansicht dar, die in der Karte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="054b4-198">The map scene represents the 3D view that appears in the map.</span></span> <span data-ttu-id="054b4-199">Die Klasse [**MapCamera**](https://msdn.microsoft.com/library/windows/apps/dn974244) stellt die Position der Kamera dar, mit der eine solche Ansicht angezeigt würde.</span><span class="sxs-lookup"><span data-stu-id="054b4-199">The [**MapCamera**](https://msdn.microsoft.com/library/windows/apps/dn974244) class represents the position of the camera that would display such a view.</span></span>

![Diagramm mit MapCamera-Position und Kartenszenenposition](images/mapcontrol-techdiagram.png)

<span data-ttu-id="054b4-201">Damit Gebäude und andere Merkmale auf der Kartenoberfläche in 3D angezeigt werden, legen Sie die [**Style**](https://msdn.microsoft.com/library/windows/apps/dn637051)-Eigenschaft des Kartensteuerelements auf [**MapStyle.Aerial3DWithRoads**](https://msdn.microsoft.com/library/windows/apps/dn637127) fest.</span><span class="sxs-lookup"><span data-stu-id="054b4-201">To make buildings and other features on the map surface appear in 3D, set the map control's [**Style**](https://msdn.microsoft.com/library/windows/apps/dn637051) property to [**MapStyle.Aerial3DWithRoads**](https://msdn.microsoft.com/library/windows/apps/dn637127).</span></span> <span data-ttu-id="054b4-202">Dies ist ein Beispiel für eine 3D-Ansicht mit dem Stil **Aerial3DWithRoads**.</span><span class="sxs-lookup"><span data-stu-id="054b4-202">This is an example of a 3D view with the **Aerial3DWithRoads** style.</span></span>

![Beispiel für eine 3D-Kartenansicht](images/only3d-730width.png)

<span data-ttu-id="054b4-204">So zeigen Sie eine 3D-Ansicht an</span><span class="sxs-lookup"><span data-stu-id="054b4-204">To display a 3D view</span></span>

1.  <span data-ttu-id="054b4-205">Überprüfen Sie mittels [**Is3DSupported**](https://msdn.microsoft.com/library/windows/apps/dn974265), ob 3D-Ansichten auf dem Gerät unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="054b4-205">Determine if 3D views are supported on the device by checking [**Is3DSupported**](https://msdn.microsoft.com/library/windows/apps/dn974265).</span></span>
2.  <span data-ttu-id="054b4-206">Wenn 3D-Ansichten unterstützt werden, legen Sie die [**Style**](https://msdn.microsoft.com/library/windows/apps/dn637051)-Eigenschaft des Kartensteuerelements auf [**MapStyle.Aerial3DWithRoads**](https://msdn.microsoft.com/library/windows/apps/dn637127) fest.</span><span class="sxs-lookup"><span data-stu-id="054b4-206">If 3D views is supported, set the map control's [**Style**](https://msdn.microsoft.com/library/windows/apps/dn637051) property to [**MapStyle.Aerial3DWithRoads**](https://msdn.microsoft.com/library/windows/apps/dn637127).</span></span>
3.  <span data-ttu-id="054b4-207">Erstellen Sie ein [**MapScene**](https://msdn.microsoft.com/library/windows/apps/dn974329)-Objekt mithilfe einer der zahlreichen **CreateFrom**-Methoden, z.B. [**CreateFromLocationAndRadius**](https://msdn.microsoft.com/library/windows/apps/dn974336) und [**CreateFromCamera**](https://msdn.microsoft.com/library/windows/apps/dn974334).</span><span class="sxs-lookup"><span data-stu-id="054b4-207">Create a [**MapScene**](https://msdn.microsoft.com/library/windows/apps/dn974329) object using one of the many **CreateFrom** methods, such as [**CreateFromLocationAndRadius**](https://msdn.microsoft.com/library/windows/apps/dn974336) and [**CreateFromCamera**](https://msdn.microsoft.com/library/windows/apps/dn974334).</span></span>
4.  <span data-ttu-id="054b4-208">Rufen Sie [**TrySetSceneAsync**](https://msdn.microsoft.com/library/windows/apps/dn974296) auf, um die 3D-Ansicht anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="054b4-208">Call [**TrySetSceneAsync**](https://msdn.microsoft.com/library/windows/apps/dn974296) to display the 3D view.</span></span> <span data-ttu-id="054b4-209">Darüber hinaus können Sie eine optionale Animation angeben, die beim Ändern der Ansicht angezeigt werden soll, indem Sie eine Konstante aus der Enumeration [**MapAnimationKind**](https://msdn.microsoft.com/library/windows/apps/dn637002) angeben.</span><span class="sxs-lookup"><span data-stu-id="054b4-209">You can also specify an optional animation to use when the view changes by providing a constant from the [**MapAnimationKind**](https://msdn.microsoft.com/library/windows/apps/dn637002) enumeration.</span></span>

<span data-ttu-id="054b4-210">In diesem Beispiel wird das Anzeigen einer 3D-Ansicht gezeigt.</span><span class="sxs-lookup"><span data-stu-id="054b4-210">This example shows how to display a 3D view.</span></span>

```csharp
private async void display3DLocation()
{
   if (MapControl1.Is3DSupported)
   {
      // Set the aerial 3D view.
      MapControl1.Style = MapStyle.Aerial3DWithRoads;

      // Specify the location.
      BasicGeoposition hwGeoposition = new BasicGeoposition() { Latitude = 43.773251, Longitude = 11.255474};
      Geopoint hwPoint = new Geopoint(hwGeoposition);

      // Create the map scene.
      MapScene hwScene = MapScene.CreateFromLocationAndRadius(hwPoint,
                                                                           80, /* show this many meters around */
                                                                           0, /* looking at it to the North*/
                                                                           60 /* degrees pitch */);
      // Set the 3D view with animation.
      await MapControl1.TrySetSceneAsync(hwScene,MapAnimationKind.Bow);
   }
   else
   {
      // If 3D views are not supported, display dialog.
      ContentDialog viewNotSupportedDialog = new ContentDialog()
      {
         Title = "3D is not supported",
         Content = "\n3D views are not supported on this device.",
         PrimaryButtonText = "OK"
      };
      await viewNotSupportedDialog.ShowAsync();
   }
}
```

## <a name="get-info-about-locations-and-elements"></a><span data-ttu-id="054b4-211">Abrufen von Informationen zu Standorten und Elementen</span><span class="sxs-lookup"><span data-stu-id="054b4-211">Get info about locations and elements</span></span>


<span data-ttu-id="054b4-212">Rufen Sie Informationen zu Positionen auf der Karte ab, indem Sie die folgenden Methoden von [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="054b4-212">Get info about locations on the map by calling the following methods of the [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004).</span></span>

-   <span data-ttu-id="054b4-213">[**GetLocationFromOffset**](https://msdn.microsoft.com/library/windows/apps/dn637016)-Methode – Ruft den geografischen Standort ab, der dem angegebenen Punkt im Viewport des Kartensteuerelements entspricht.</span><span class="sxs-lookup"><span data-stu-id="054b4-213">[**GetLocationFromOffset**](https://msdn.microsoft.com/library/windows/apps/dn637016) method - Get the geographic location that corresponds to the specified point in the viewport of the Map control.</span></span>
-   <span data-ttu-id="054b4-214">[**GetOffsetFromLocation**](https://msdn.microsoft.com/library/windows/apps/dn637018)-Methode – Ruft den Punkt im Viewport des Kartensteuerelements ab, der dem angegebenen geografischen Standort entspricht.</span><span class="sxs-lookup"><span data-stu-id="054b4-214">[**GetOffsetFromLocation**](https://msdn.microsoft.com/library/windows/apps/dn637018) method - Get the point in the viewport of the Map control that corresponds to the specified geographic location.</span></span>
-   <span data-ttu-id="054b4-215">[**IsLocationInView**](https://msdn.microsoft.com/library/windows/apps/dn637022)-Methode – Bestimmt, ob der angegebene geografische Standort aktuell im Viewport des Kartensteuerelements sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="054b4-215">[**IsLocationInView**](https://msdn.microsoft.com/library/windows/apps/dn637022) method - Determine whether the specified geographic location is currently visible in the viewport of the Map control.</span></span>
-   <span data-ttu-id="054b4-216">[**FindMapElementsAtOffset**](https://msdn.microsoft.com/library/windows/apps/dn637014)-Methode – Ruft die Elemente auf der Karte ab, die sich am angegebenen Punkt im Viewport des Kartensteuerelements befinden.</span><span class="sxs-lookup"><span data-stu-id="054b4-216">[**FindMapElementsAtOffset**](https://msdn.microsoft.com/library/windows/apps/dn637014) method - Get the elements on the map located at the specified point in the viewport of the Map control.</span></span>

## <a name="handle-user-interaction-and-changes"></a><span data-ttu-id="054b4-217">Behandeln von Benutzerinteraktionen und Änderungen</span><span class="sxs-lookup"><span data-stu-id="054b4-217">Handle user interaction and changes</span></span>


<span data-ttu-id="054b4-218">Sie behandeln Benutzereingabegesten auf der Karte, indem Sie die folgenden Ereignisse von [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004) behandeln.</span><span class="sxs-lookup"><span data-stu-id="054b4-218">Handle user input gestures on the map by handling the following events of the [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004).</span></span> <span data-ttu-id="054b4-219">Rufen Sie Informationen zum geografischen Standort auf der Karte und der physischen Position im Viewport ab, an der die Geste ausgeführt wurde, indem Sie die Werte der [**Location**](https://msdn.microsoft.com/library/windows/apps/dn637091)-Eigenschaft und der [**Position**](https://msdn.microsoft.com/library/windows/apps/dn637093)-Eigenschaft von [**MapInputEventArgs**](https://msdn.microsoft.com/library/windows/apps/dn637090) überprüfen.</span><span class="sxs-lookup"><span data-stu-id="054b4-219">Get info about the geographic location on the map and the physical position in the viewport where the gesture occurred by checking the values of the [**Location**](https://msdn.microsoft.com/library/windows/apps/dn637091) and [**Position**](https://msdn.microsoft.com/library/windows/apps/dn637093) properties of the [**MapInputEventArgs**](https://msdn.microsoft.com/library/windows/apps/dn637090).</span></span>

-   [**<span data-ttu-id="054b4-220">MapTapped</span><span class="sxs-lookup"><span data-stu-id="054b4-220">MapTapped</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn637038)
-   [**<span data-ttu-id="054b4-221">MapDoubleTapped</span><span class="sxs-lookup"><span data-stu-id="054b4-221">MapDoubleTapped</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn637032)
-   [**<span data-ttu-id="054b4-222">MapHolding</span><span class="sxs-lookup"><span data-stu-id="054b4-222">MapHolding</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn637035)

<span data-ttu-id="054b4-223">Sie stellen fest, ob die Karte geladen wird oder vollständig geladen wurde, indem Sie das [**LoadingStatusChanged**](https://msdn.microsoft.com/library/windows/apps/dn637028)-Ereignis des Steuerelements behandeln.</span><span class="sxs-lookup"><span data-stu-id="054b4-223">Determine whether the map is loading or completely loaded by handling the control's [**LoadingStatusChanged**](https://msdn.microsoft.com/library/windows/apps/dn637028) event.</span></span>

<span data-ttu-id="054b4-224">Sie behandeln Änderungen, die durch Ändern der Karteneinstellungen durch den Benutzer oder die App entstehen, indem Sie die folgenden Ereignisse von [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004) behandeln.</span><span class="sxs-lookup"><span data-stu-id="054b4-224">Handle changes that happen when the user or the app changes the settings of the map by handling the following events of the [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004).</span></span> [<span data-ttu-id="054b4-225">Richtlinien für Karten</span><span class="sxs-lookup"><span data-stu-id="054b4-225">Guidelines for maps</span></span>](https://msdn.microsoft.com/library/windows/apps/dn596102)

-   [**<span data-ttu-id="054b4-226">CenterChanged</span><span class="sxs-lookup"><span data-stu-id="054b4-226">CenterChanged</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn637006)
-   [**<span data-ttu-id="054b4-227">HeadingChanged</span><span class="sxs-lookup"><span data-stu-id="054b4-227">HeadingChanged</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn637020)
-   [**<span data-ttu-id="054b4-228">PitchChanged</span><span class="sxs-lookup"><span data-stu-id="054b4-228">PitchChanged</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn637045)
-   [**<span data-ttu-id="054b4-229">ZoomLevelChanged</span><span class="sxs-lookup"><span data-stu-id="054b4-229">ZoomLevelChanged</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn637069)

## <a name="best-practice-recommendations"></a><span data-ttu-id="054b4-230">Bewährte Methoden und Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="054b4-230">Best practice recommendations</span></span>

-   <span data-ttu-id="054b4-231">Verwenden Sie für die Anzeige der Karte ausreichend Platz auf dem Bildschirm (oder den gesamten Bildschirm), sodass Benutzer beim Anzeigen geografischer Informationen keine übermäßigen Verschiebungen oder Zoomvorgänge ausführen müssen.</span><span class="sxs-lookup"><span data-stu-id="054b4-231">Use ample screen space (or the entire screen) to display the map so that users don't have to pan and zoom excessively to view geographical information.</span></span>

-   <span data-ttu-id="054b4-232">Wenn die Karte nur zum Anzeigen einer statischen, informativen Ansicht dient, ist möglicherweise eine kleinere Karte ausreichend.</span><span class="sxs-lookup"><span data-stu-id="054b4-232">If the map is only used to present a static, informational view, then using a smaller map might be more appropriate.</span></span> <span data-ttu-id="054b4-233">Wenn Sie eine kleinere, statische Karte verwenden, orientieren Sie sich für die Größe an der Benutzerfreundlichkeit. Die Karte sollte klein genug sein, um genügend Platz auf dem Bildschirm zu lassen, aber groß genug, um lesbar zu bleiben.</span><span class="sxs-lookup"><span data-stu-id="054b4-233">If you go with a smaller, static map, base its dimensions on usability—small enough to conserve enough screen real estate, but large enough to remain legible.</span></span>

-   <span data-ttu-id="054b4-234">Betten Sie die interessanten Orte mithilfe von [**map elements**](https://msdn.microsoft.com/library/windows/apps/dn637034) in die Kartenszene ein. Zusätzliche Informationen können als vorübergehende, die Kartenszene überlagernde Benutzeroberfläche angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="054b4-234">Embed the points of interest in the map scene using [**map elements**](https://msdn.microsoft.com/library/windows/apps/dn637034); any additional information can be displayed as transient UI that overlays the map scene.</span></span>

## <a name="related-topics"></a><span data-ttu-id="054b4-235">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="054b4-235">Related topics</span></span>

* [<span data-ttu-id="054b4-236">Bing Maps Developer Center</span><span class="sxs-lookup"><span data-stu-id="054b4-236">Bing Maps Developer Center</span></span>](https://www.bingmapsportal.com/)
* [<span data-ttu-id="054b4-237">Beispiel für UWP-Karte</span><span class="sxs-lookup"><span data-stu-id="054b4-237">UWP map sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=619977)
* [<span data-ttu-id="054b4-238">Abrufen der aktuellen Position</span><span class="sxs-lookup"><span data-stu-id="054b4-238">Get current location</span></span>](get-location.md)
* [<span data-ttu-id="054b4-239">Entwurfsrichtlinien für Apps mit Standortbestimmung</span><span class="sxs-lookup"><span data-stu-id="054b4-239">Design guidelines for location-aware apps</span></span>](https://msdn.microsoft.com/library/windows/apps/hh465148)
* [<span data-ttu-id="054b4-240">Entwurfsrichtlinien für Karten</span><span class="sxs-lookup"><span data-stu-id="054b4-240">Design guidelines for maps</span></span>](https://msdn.microsoft.com/library/windows/apps/dn596102)
* [<span data-ttu-id="054b4-241">Build 2015-Video: Nutzen von Karten und Ortung über Telefon, Tablet und PC in Ihren Windows-Apps</span><span class="sxs-lookup"><span data-stu-id="054b4-241">Build 2015 video: Leveraging Maps and Location Across Phone, Tablet, and PC in Your Windows Apps</span></span>](https://channel9.msdn.com/Events/Build/2015/2-757)
* [<span data-ttu-id="054b4-242">Beispiel für eine UWP-App mit Verkehrsinformationen</span><span class="sxs-lookup"><span data-stu-id="054b4-242">UWP traffic app sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=619982)
* [**<span data-ttu-id="054b4-243">MapControl</span><span class="sxs-lookup"><span data-stu-id="054b4-243">MapControl</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn637004)
