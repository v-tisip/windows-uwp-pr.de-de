---
author: PatrickFarley
title: Einrichten von Geofence-Bereichen
description: Richten Sie einen Geofence-Bereich in Ihrer App ein, und erfahren Sie, wie Sie Benachrichtigungen im Vordergrund und Hintergrund behandeln.
ms.assetid: A3A46E03-0751-4DBD-A2A1-2323DB09BDBA
ms.author: pafarley
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP, Karten, Standort, Geofence, Benachrichtigungen
ms.localizationpriority: medium
ms.openlocfilehash: 8e9fa71b3d6ae002aa37e14e23b55793876156c8
ms.sourcegitcommit: e814a13978f33654d8e995584f4b047cb53e0aef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "6041684"
---
# <a name="set-up-a-geofence"></a><span data-ttu-id="438ff-104">Einrichten eines Geofence</span><span class="sxs-lookup"><span data-stu-id="438ff-104">Set up a geofence</span></span>




<span data-ttu-id="438ff-105">Richten Sie einen [**Geofence**](https://msdn.microsoft.com/library/windows/apps/dn263587)-Bereich in Ihrer App ein, und erfahren Sie, wie Sie Benachrichtigungen im Vordergrund und Hintergrund behandeln.</span><span class="sxs-lookup"><span data-stu-id="438ff-105">Set up a [**Geofence**](https://msdn.microsoft.com/library/windows/apps/dn263587) in your app, and learn how to handle notifications in the foreground and background.</span></span>

<span data-ttu-id="438ff-106">**Tipp** Wenn Sie weitere Informationen zum Zugreifen auf die Position in Ihrer App benötigen, laden Sie das folgende Beispiel aus den [API-Beispielen für die Universelle Windows-Plattform](http://go.microsoft.com/fwlink/p/?LinkId=619979) auf GitHub herunter.</span><span class="sxs-lookup"><span data-stu-id="438ff-106">**Tip** To learn more about accessing location in your app, download the following sample from the [Windows-universal-samples repo](http://go.microsoft.com/fwlink/p/?LinkId=619979) on GitHub.</span></span>

-   [<span data-ttu-id="438ff-107">Kartenbeispiel für die Universelle Windows-Plattform (UWP)</span><span class="sxs-lookup"><span data-stu-id="438ff-107">Universal Windows Platform (UWP) map sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=619977)

## <a name="enable-the-location-capability"></a><span data-ttu-id="438ff-108">Aktivieren der Positionsfunktion</span><span class="sxs-lookup"><span data-stu-id="438ff-108">Enable the location capability</span></span>


1.  <span data-ttu-id="438ff-109">Doppelklicken Sie im **Projektmappen-Explorer** auf **package.appxmanifest**, und wählen Sie die Registerkarte **Funktionen** aus.</span><span class="sxs-lookup"><span data-stu-id="438ff-109">In **Solution Explorer**, double-click on **package.appxmanifest** and select the **Capabilities** tab.</span></span>
2.  <span data-ttu-id="438ff-110">Überprüfen Sie die Option **Position** in der Liste **Funktionen**.</span><span class="sxs-lookup"><span data-stu-id="438ff-110">In the **Capabilities** list, check **Location**.</span></span> <span data-ttu-id="438ff-111">Dadurch wird der Paketmanifestdatei die `Location`-Gerätefunktion hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="438ff-111">This adds the `Location` device capability to the package manifest file.</span></span>

```xml
  <Capabilities>
    <!-- DeviceCapability elements must follow Capability elements (if present) -->
    <DeviceCapability Name="location"/>
  </Capabilities>
```

## <a name="set-up-a-geofence"></a><span data-ttu-id="438ff-112">Einrichten von Geofence-Bereichen</span><span class="sxs-lookup"><span data-stu-id="438ff-112">Set up a geofence</span></span>


### <a name="step-1-request-access-to-the-users-location"></a><span data-ttu-id="438ff-113">Schritt 1: Anfordern des Zugriffs auf die Position des Benutzers</span><span class="sxs-lookup"><span data-stu-id="438ff-113">Step 1: Request access to the user's location</span></span>

<span data-ttu-id="438ff-114">**Wichtig** Sie müssen über die [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/dn859152)-Methode Zugriff auf Positionsdaten des Benutzers anfordern, bevor Sie versuchen, auf die Position des Benutzers zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="438ff-114">**Important** You must request access to the user's location by using the [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/dn859152) method before attempting to access the user's location.</span></span> <span data-ttu-id="438ff-115">Sie müssen die **RequestAccessAsync**-Methode aus dem UI-Thread aufrufen, und die App muss sich im Vordergrund befinden.</span><span class="sxs-lookup"><span data-stu-id="438ff-115">You must call the **RequestAccessAsync** method from the UI thread and your app must be in the foreground.</span></span> <span data-ttu-id="438ff-116">Ihre App kann erst auf Positionsdaten des Benutzers zugreifen, nachdem der Benutzer der App den Zugriff gewährt hat.</span><span class="sxs-lookup"><span data-stu-id="438ff-116">Your app will not be able to access the user's location information until after the user grants permission to your app.</span></span>

```csharp
using Windows.Devices.Geolocation;
...
var accessStatus = await Geolocator.RequestAccessAsync();
```

<span data-ttu-id="438ff-117">Die [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/dn859152)-Methode fordert den Benutzer auf, den Zugriff auf seinen Standort zu genehmigen.</span><span class="sxs-lookup"><span data-stu-id="438ff-117">The [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/dn859152) method prompts the user for permission to access their location.</span></span> <span data-ttu-id="438ff-118">Der Benutzer wird nur einmal (pro App) aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="438ff-118">The user is only prompted once (per app).</span></span> <span data-ttu-id="438ff-119">Nachdem die Berechtigung erstmalig gewährt oder verweigert wurde, fordert die Methode keine Berechtigung mehr vom Benutzer an.</span><span class="sxs-lookup"><span data-stu-id="438ff-119">After the first time they grant or deny permission, this method no longer prompts the user for permission.</span></span> <span data-ttu-id="438ff-120">Um das Ändern von Standortberechtigungen nach der Aufforderung für den Benutzer zu vereinfachen, sollten Sie einen Link zu den Standorteinstellungen bereitstellen wie weiter unten in diesem Thema beschrieben.</span><span class="sxs-lookup"><span data-stu-id="438ff-120">To help the user change location permissions after they've been prompted, we recommend that you provide a link to the location settings as demonstrated later in this topic.</span></span>

### <a name="step-2-register-for-changes-in-geofence-state-and-location-permissions"></a><span data-ttu-id="438ff-121">Schritt 2: Registrieren für Änderungen des Geofence-Zustands und für Positionsberechtigungen</span><span class="sxs-lookup"><span data-stu-id="438ff-121">Step 2: Register for changes in geofence state and location permissions</span></span>

<span data-ttu-id="438ff-122">In diesem Beispiel wird eine **switch**-Anweisung mit **accessStatus** (aus dem vorherigen Beispiel) verwendet, die nur aktiv ist, wenn der Zugriff auf den Standort eines Benutzers zugelassen wird.</span><span class="sxs-lookup"><span data-stu-id="438ff-122">In this example, a **switch** statement is used with **accessStatus** (from the previous example) to act only when access to the user's location is allowed.</span></span> <span data-ttu-id="438ff-123">Der Code greift (sofern Zugriff auf die Position des Benutzers gewährt wurde) auf die aktuellen Geofences zu und führt eine Registrierung für Geofence-Zustandsänderungen und für Positionsberechtigungsänderungen durch.</span><span class="sxs-lookup"><span data-stu-id="438ff-123">If access to the user's location is allowed, the code accesses the current geofences, registers for geofence state changes, and registers for changes in location permissions.</span></span>

<span data-ttu-id="438ff-124">**Tipp** Überwachen Sie bei Verwendung eines Geofence-Bereichs Änderungen bezüglich Positionsberechtigungen mithilfe des [**StatusChanged**](https://msdn.microsoft.com/library/windows/apps/dn263646)-Ereignisses aus der GeofenceMonitor-Klasse anstatt mit dem StatusChanged-Ereignis aus der Geolocator-Klasse.</span><span class="sxs-lookup"><span data-stu-id="438ff-124">**Tip** When using a geofence, monitor changes in location permissions using the [**StatusChanged**](https://msdn.microsoft.com/library/windows/apps/dn263646) event from the GeofenceMonitor class instead of the StatusChanged event from the Geolocator class.</span></span> <span data-ttu-id="438ff-125">Ein [**GeofenceMonitorStatus**](https://msdn.microsoft.com/library/windows/apps/dn263599)-Element mit dem Status **Disabled** entspricht einem deaktivierten [**PositionStatus**](https://msdn.microsoft.com/library/windows/apps/br225599)-Element: Beide geben an, dass die App nicht auf Positionsdaten des Benutzers zugreifen darf.</span><span class="sxs-lookup"><span data-stu-id="438ff-125">A [**GeofenceMonitorStatus**](https://msdn.microsoft.com/library/windows/apps/dn263599) of **Disabled** is equivalent to a disabled [**PositionStatus**](https://msdn.microsoft.com/library/windows/apps/br225599) - both indicate that the app does not have permission to access the user's location.</span></span>

```csharp
switch (accessStatus)
{
    case GeolocationAccessStatus.Allowed:
        geofences = GeofenceMonitor.Current.Geofences;

        FillRegisteredGeofenceListBoxWithExistingGeofences();
        FillEventListBoxWithExistingEvents();

        // Register for state change events.
        GeofenceMonitor.Current.GeofenceStateChanged += OnGeofenceStateChanged;
        GeofenceMonitor.Current.StatusChanged += OnGeofenceStatusChanged;
        break;


    case GeolocationAccessStatus.Denied:
        _rootPage.NotifyUser("Access denied.", NotifyType.ErrorMessage);
        break;

    case GeolocationAccessStatus.Unspecified:
        _rootPage.NotifyUser("Unspecified error.", NotifyType.ErrorMessage);
        break;
}
```

<span data-ttu-id="438ff-126">Heben Sie die Registrierung der Ereignislistener auf, wenn der Benutzer die Vordergrund-App verlässt.</span><span class="sxs-lookup"><span data-stu-id="438ff-126">Then, when navigating away from your foreground app, unregister the event listeners.</span></span>

```csharp
protected override void OnNavigatingFrom(NavigatingCancelEventArgs e)
{
    GeofenceMonitor.Current.GeofenceStateChanged -= OnGeofenceStateChanged;
    GeofenceMonitor.Current.StatusChanged -= OnGeofenceStatusChanged;

    base.OnNavigatingFrom(e);
}
```

### <a name="step-3-create-the-geofence"></a><span data-ttu-id="438ff-127">Schritt 3: Erstellen des Geofence-Bereichs</span><span class="sxs-lookup"><span data-stu-id="438ff-127">Step 3: Create the geofence</span></span>

<span data-ttu-id="438ff-128">Nun können Sie ein [**Geofence**](https://msdn.microsoft.com/library/windows/apps/dn263587)-Objekt definieren und einrichten.</span><span class="sxs-lookup"><span data-stu-id="438ff-128">Now, you are ready to define and set up a [**Geofence**](https://msdn.microsoft.com/library/windows/apps/dn263587) object.</span></span> <span data-ttu-id="438ff-129">Je nach Ihren Anforderungen stehen mehrere verschiedene Konstruktorüberladungen zur Auswahl.</span><span class="sxs-lookup"><span data-stu-id="438ff-129">There are several different constructor overloads to choose from, depending on your needs.</span></span> <span data-ttu-id="438ff-130">Geben Sie im einfachsten Geofence-Konstruktor wie hier gezeigt nur [**Id**](https://msdn.microsoft.com/library/windows/apps/dn263724) und [**Geoshape**](https://msdn.microsoft.com/library/windows/apps/dn263718) an.</span><span class="sxs-lookup"><span data-stu-id="438ff-130">In the most basic geofence constructor, specify only the [**Id**](https://msdn.microsoft.com/library/windows/apps/dn263724) and the [**Geoshape**](https://msdn.microsoft.com/library/windows/apps/dn263718) as shown here.</span></span>

```csharp
// Set the fence ID.
string fenceId = "fence1";

// Define the fence location and radius.
BasicGeoposition position;
position.Latitude = 47.6510;
position.Longitude = -122.3473;
position.Altitude = 0.0;
double radius = 10; // in meters

// Set a circular region for the geofence.
Geocircle geocircle = new Geocircle(position, radius);

// Create the geofence.
Geofence geofence = new Geofence(fenceId, geocircle);

```

<span data-ttu-id="438ff-131">Sie können den Geofence mit einem der anderen Konstruktoren weiter optimieren.</span><span class="sxs-lookup"><span data-stu-id="438ff-131">You can fine-tune your geofence further by using one of the other constructors.</span></span> <span data-ttu-id="438ff-132">Im nächsten Beispiel legt der Geofence-Konstruktor diese zusätzlichen Parameter fest:</span><span class="sxs-lookup"><span data-stu-id="438ff-132">In the next example, the geofence constructor specifies these additional parameters:</span></span>

-   <span data-ttu-id="438ff-133">[**MonitoredStates**](https://msdn.microsoft.com/library/windows/apps/dn263728) – Gibt an, für welche Geofence-Ereignisse Sie Benachrichtigungen erhalten möchten: Betreten der definierten Region, Verlassen der definierten Region oder Entfernen des Geofence-Bereichs.</span><span class="sxs-lookup"><span data-stu-id="438ff-133">[**MonitoredStates**](https://msdn.microsoft.com/library/windows/apps/dn263728) - Indicates what geofence events you want to receive notifications for entering the defined region, leaving the defined region, or removal of the geofence.</span></span>
-   <span data-ttu-id="438ff-134">[**SingleUse**](https://msdn.microsoft.com/library/windows/apps/dn263732) – Entfernt den Geofence-Bereich, nachdem alle Zustände erfüllt wurden, auf die der Geofence-Bereich überwacht wird.</span><span class="sxs-lookup"><span data-stu-id="438ff-134">[**SingleUse**](https://msdn.microsoft.com/library/windows/apps/dn263732) - Removes the geofence once all the states the geofence is being monitored for have been met.</span></span>
-   <span data-ttu-id="438ff-135">[**DwellTime**](https://msdn.microsoft.com/library/windows/apps/dn263703) – Gibt an, wie lange sich der Benutzer innerhalb oder außerhalb des definierten Bereichs befinden muss, bevor das Enter- oder Exit-Ereignis ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="438ff-135">[**DwellTime**](https://msdn.microsoft.com/library/windows/apps/dn263703) - Indicates how long the user must be in or out of the defined area before the enter/exit events are triggered.</span></span>
-   <span data-ttu-id="438ff-136">[**StartTime**](https://msdn.microsoft.com/library/windows/apps/dn263735) – Gibt an, wann mit der Überwachung des Geofence-Bereichs begonnen wird.</span><span class="sxs-lookup"><span data-stu-id="438ff-136">[**StartTime**](https://msdn.microsoft.com/library/windows/apps/dn263735) - Indicates when to start monitoring the geofence.</span></span>
-   <span data-ttu-id="438ff-137">[**Duration**](https://msdn.microsoft.com/library/windows/apps/dn263697) – Gibt die Dauer für die Überwachung des Geofence-Bereichs an.</span><span class="sxs-lookup"><span data-stu-id="438ff-137">[**Duration**](https://msdn.microsoft.com/library/windows/apps/dn263697) - Indicates the period for which to monitor the geofence.</span></span>

```csharp
// Set the fence ID.
string fenceId = "fence2";

// Define the fence location and radius.
BasicGeoposition position;
position.Latitude = 47.6510;
position.Longitude = -122.3473;
position.Altitude = 0.0;
double radius = 10; // in meters

// Set the circular region for geofence.
Geocircle geocircle = new Geocircle(position, radius);

// Remove the geofence after the first trigger.
bool singleUse = true;

// Set the monitored states.
MonitoredGeofenceStates monitoredStates =
                MonitoredGeofenceStates.Entered |
                MonitoredGeofenceStates.Exited |
                MonitoredGeofenceStates.Removed;

// Set how long you need to be in geofence for the enter event to fire.
TimeSpan dwellTime = TimeSpan.FromMinutes(5);

// Set how long the geofence should be active.
TimeSpan duration = TimeSpan.FromDays(1);

// Set up the start time of the geofence.
DateTimeOffset startTime = DateTime.Now;

// Create the geofence.
Geofence geofence = new Geofence(fenceId, geocircle, monitoredStates, singleUse, dwellTime, startTime, duration);
```

<span data-ttu-id="438ff-138">Denken Sie nach der Erstellung daran, das neue [**Geofence**](https://docs.microsoft.com/uwp/api/Windows.Devices.Geolocation.Geofencing.Geofence)-Objekt beim Monitor zu registrieren.</span><span class="sxs-lookup"><span data-stu-id="438ff-138">After creating, remember to register your new [**Geofence**](https://docs.microsoft.com/uwp/api/Windows.Devices.Geolocation.Geofencing.Geofence) to the monitor.</span></span>

```csharp
// Register the geofence
try {
   GeofenceMonitor.Current.Geofences.Add(geofence);
} catch {
   // Handle failure to add geofence
}
```

### <a name="step-4-handle-changes-in-location-permissions"></a><span data-ttu-id="438ff-139">Schritt 4: Behandeln von Änderungen an Positionsberechtigungen</span><span class="sxs-lookup"><span data-stu-id="438ff-139">Step 4: Handle changes in location permissions</span></span>

<span data-ttu-id="438ff-140">Das [**GeofenceMonitor**](https://msdn.microsoft.com/library/windows/apps/dn263595)-Objekt löst das [**StatusChanged**](https://msdn.microsoft.com/library/windows/apps/dn263646)-Ereignis aus, um anzugeben, dass sich die Positionseinstellungen des Benutzers geändert haben.</span><span class="sxs-lookup"><span data-stu-id="438ff-140">The [**GeofenceMonitor**](https://msdn.microsoft.com/library/windows/apps/dn263595) object triggers the [**StatusChanged**](https://msdn.microsoft.com/library/windows/apps/dn263646) event to indicate that the user's location settings changed.</span></span> <span data-ttu-id="438ff-141">Das Ereignis übergibt den entsprechenden Status über die Eigenschaft **sender.Status** des Arguments (vom Typ [**GeofenceMonitorStatus**](https://msdn.microsoft.com/library/windows/apps/dn263599)).</span><span class="sxs-lookup"><span data-stu-id="438ff-141">That event passes the corresponding status via the argument's **sender.Status** property (of type [**GeofenceMonitorStatus**](https://msdn.microsoft.com/library/windows/apps/dn263599)).</span></span> <span data-ttu-id="438ff-142">Beachten Sie, dass diese Methode nicht vom UI-Thread aufgerufen wird und das [**Dispatcher**](https://msdn.microsoft.com/library/windows/apps/br208211)-Objekt die UI-Änderungen aufruft.</span><span class="sxs-lookup"><span data-stu-id="438ff-142">Note that this method is not called from the UI thread and the [**Dispatcher**](https://msdn.microsoft.com/library/windows/apps/br208211) object invokes the UI changes.</span></span>

```csharp
using Windows.UI.Core;
...
public async void OnGeofenceStatusChanged(GeofenceMonitor sender, object e)
{
   await Dispatcher.RunAsync(CoreDispatcherPriority.Normal, () =>
   {
    // Show the location setting message only if the status is disabled.
    LocationDisabledMessage.Visibility = Visibility.Collapsed;

    switch (sender.Status)
    {
     case GeofenceMonitorStatus.Ready:
      _rootPage.NotifyUser("The monitor is ready and active.", NotifyType.StatusMessage);
      break;

     case GeofenceMonitorStatus.Initializing:
      _rootPage.NotifyUser("The monitor is in the process of initializing.", NotifyType.StatusMessage);
      break;

     case GeofenceMonitorStatus.NoData:
      _rootPage.NotifyUser("There is no data on the status of the monitor.", NotifyType.ErrorMessage);
      break;

     case GeofenceMonitorStatus.Disabled:
      _rootPage.NotifyUser("Access to location is denied.", NotifyType.ErrorMessage);

      // Show the message to the user to go to the location settings.
      LocationDisabledMessage.Visibility = Visibility.Visible;
      break;

     case GeofenceMonitorStatus.NotInitialized:
      _rootPage.NotifyUser("The geofence monitor has not been initialized.", NotifyType.StatusMessage);
      break;

     case GeofenceMonitorStatus.NotAvailable:
      _rootPage.NotifyUser("The geofence monitor is not available.", NotifyType.ErrorMessage);
      break;

     default:
      ScenarioOutput_Status.Text = "Unknown";
      _rootPage.NotifyUser(string.Empty, NotifyType.StatusMessage);
      break;
    }
   });
}
```

## <a name="set-up-foreground-notifications"></a><span data-ttu-id="438ff-143">Einrichten von Benachrichtigungen im Vordergrund</span><span class="sxs-lookup"><span data-stu-id="438ff-143">Set up foreground notifications</span></span>


<span data-ttu-id="438ff-144">Nachdem Ihre Geofence-Bereiche erstellt wurden, müssen Sie die Logik für das Eintreten eines Geofence-Ereignisses hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="438ff-144">After your geofences are created, you must add the logic to handle what happens when a geofence event occurs.</span></span> <span data-ttu-id="438ff-145">Je nach eingerichteten [**MonitoredStates**](https://msdn.microsoft.com/library/windows/apps/dn263728) können Sie in folgenden Fällen ein Ereignis empfangen:</span><span class="sxs-lookup"><span data-stu-id="438ff-145">Depending on the [**MonitoredStates**](https://msdn.microsoft.com/library/windows/apps/dn263728) that you have set up, you may receive an event when:</span></span>

-   <span data-ttu-id="438ff-146">Der Benutzer betritt eine Zielregion.</span><span class="sxs-lookup"><span data-stu-id="438ff-146">The user enters a region of interest.</span></span>
-   <span data-ttu-id="438ff-147">Der Benutzer verlässt eine Zielregion.</span><span class="sxs-lookup"><span data-stu-id="438ff-147">The user leaves a region of interest.</span></span>
-   <span data-ttu-id="438ff-148">Der Geofence-Bereich ist abgelaufen oder wurde entfernt.</span><span class="sxs-lookup"><span data-stu-id="438ff-148">The geofence has expired or been removed.</span></span> <span data-ttu-id="438ff-149">Beachten Sie, dass eine Hintergrund-App für ein Entfernungsereignis nicht aktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="438ff-149">Note that a background app is not activated for a removal event.</span></span>

<span data-ttu-id="438ff-150">Sie können direkt in der App auf Ereignisse lauschen, wenn diese ausgeführt wird, oder Sie können eine Registrierung für eine Hintergrundaufgabe vornehmen, damit Sie eine Hintergrundbenachrichtigung erhalten, sobald ein Ereignis eintritt.</span><span class="sxs-lookup"><span data-stu-id="438ff-150">You can listen for events directly from your app when it is running or register for a background task so that you receive a background notification when an event occurs.</span></span>

### <a name="step-1-register-for-geofence-state-change-events"></a><span data-ttu-id="438ff-151">Schritt 1: Durchführen der Registrierung für Ereignisse zur Änderung des Geofence-Zustands</span><span class="sxs-lookup"><span data-stu-id="438ff-151">Step 1: Register for geofence state change events</span></span>

<span data-ttu-id="438ff-152">Damit die App bei der Änderung eines Geofence-Zustands eine Vordergrundbenachrichtigung erhält, müssen Sie einen Ereignishandler registrieren.</span><span class="sxs-lookup"><span data-stu-id="438ff-152">For your app to receive a foreground notification of a geofence state change, you must register an event handler.</span></span> <span data-ttu-id="438ff-153">Dies wird normalerweise eingerichtet, wenn Sie den Geofence-Bereich erstellen.</span><span class="sxs-lookup"><span data-stu-id="438ff-153">This is typically set up when you create the geofence.</span></span>

```csharp
private void Initialize()
{
    // Other initialization logic

    GeofenceMonitor.Current.GeofenceStateChanged += OnGeofenceStateChanged;
}

```

### <a name="step-2-implement-the-geofence-event-handler"></a><span data-ttu-id="438ff-154">Schritt 2: Implementieren des Geofence-Ereignishandlers</span><span class="sxs-lookup"><span data-stu-id="438ff-154">Step 2: Implement the geofence event handler</span></span>

<span data-ttu-id="438ff-155">Der nächste Schritt ist die Implementierung der Ereignishandler.</span><span class="sxs-lookup"><span data-stu-id="438ff-155">The next step is to implement the event handlers.</span></span> <span data-ttu-id="438ff-156">Die hier durchzuführende Aktion hängt davon ab, zu welchem Zweck Ihre App den Geofence-Bereich verwendet.</span><span class="sxs-lookup"><span data-stu-id="438ff-156">The action taken here depends on what your app is using the geofence for.</span></span>

```csharp
public async void OnGeofenceStateChanged(GeofenceMonitor sender, object e)
{
    var reports = sender.ReadReports();

    await Dispatcher.RunAsync(CoreDispatcherPriority.Normal, () =>
    {
        foreach (GeofenceStateChangeReport report in reports)
        {
            GeofenceState state = report.NewState;

            Geofence geofence = report.Geofence;

            if (state == GeofenceState.Removed)
            {
                // Remove the geofence from the geofences collection.
                GeofenceMonitor.Current.Geofences.Remove(geofence);
            }
            else if (state == GeofenceState.Entered)
            {
                // Your app takes action based on the entered event.

                // NOTE: You might want to write your app to take a particular
                // action based on whether the app has internet connectivity.

            }
            else if (state == GeofenceState.Exited)
            {
                // Your app takes action based on the exited event.

                // NOTE: You might want to write your app to take a particular
                // action based on whether the app has internet connectivity.

            }
        }
    });
}



```

## <a name="set-up-background-notifications"></a><span data-ttu-id="438ff-157">Einrichten von Benachrichtigungen im Hintergrund</span><span class="sxs-lookup"><span data-stu-id="438ff-157">Set up background notifications</span></span>


<span data-ttu-id="438ff-158">Nachdem Ihre Geofence-Bereiche erstellt wurden, müssen Sie die Logik für das Eintreten eines Geofence-Ereignisses hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="438ff-158">After your geofences are created, you must add the logic to handle what happens when a geofence event occurs.</span></span> <span data-ttu-id="438ff-159">Je nach eingerichteten [**MonitoredStates**](https://msdn.microsoft.com/library/windows/apps/dn263728) können Sie in folgenden Fällen ein Ereignis empfangen:</span><span class="sxs-lookup"><span data-stu-id="438ff-159">Depending on the [**MonitoredStates**](https://msdn.microsoft.com/library/windows/apps/dn263728) that you have set up, you may receive an event when:</span></span>

-   <span data-ttu-id="438ff-160">Der Benutzer betritt eine Zielregion.</span><span class="sxs-lookup"><span data-stu-id="438ff-160">The user enters a region of interest.</span></span>
-   <span data-ttu-id="438ff-161">Der Benutzer verlässt eine Zielregion.</span><span class="sxs-lookup"><span data-stu-id="438ff-161">The user leaves a region of interest.</span></span>
-   <span data-ttu-id="438ff-162">Der Geofence-Bereich ist abgelaufen oder wurde entfernt.</span><span class="sxs-lookup"><span data-stu-id="438ff-162">The geofence has expired or been removed.</span></span> <span data-ttu-id="438ff-163">Beachten Sie, dass eine Hintergrund-App für ein Entfernungsereignis nicht aktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="438ff-163">Note that a background app is not activated for a removal event.</span></span>

<span data-ttu-id="438ff-164">So lauschen Sie auf ein Geofence-Ereignis im Hintergrund</span><span class="sxs-lookup"><span data-stu-id="438ff-164">To listen for a geofence event in the background</span></span>

-   <span data-ttu-id="438ff-165">Deklarieren der Hintergrundaufgabe im App-Manifest</span><span class="sxs-lookup"><span data-stu-id="438ff-165">Declare the background task in your app’s manifest.</span></span>
-   <span data-ttu-id="438ff-166">Registrieren der Hintergrundaufgabe in Ihrer App</span><span class="sxs-lookup"><span data-stu-id="438ff-166">Register the background task in your app.</span></span> <span data-ttu-id="438ff-167">Wenn Ihre App Internetzugriff benötigt, z.B. um auf einen Cloud-Dienst zuzugreifen, können Sie dafür ein Kennzeichen festlegen, wenn das Ereignis ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="438ff-167">If your app needs internet access, say for accessing a cloud service, you can set a flag for that when the event is triggered.</span></span> <span data-ttu-id="438ff-168">Sie können mithilfe eines Kennzeichens auch sicherstellen, dass der Benutzer anwesend ist, wenn das Ereignis ausgelöst wird. So können Sie sicher sein, dass der Benutzer die Benachrichtigung erhält.</span><span class="sxs-lookup"><span data-stu-id="438ff-168">You can also set a flag to make sure that the user is present when the event is triggered so that you are sure that the user gets notified.</span></span>
-   <span data-ttu-id="438ff-169">Fordern Sie den Benutzer bei im Vordergrund ausgeführter App auf, der App Positionsberechtigungen zu gewähren.</span><span class="sxs-lookup"><span data-stu-id="438ff-169">While your app is running in the foreground, prompt the user to grant your app location permissions.</span></span>

### <a name="step-1-register-for-geofence-state-change-events"></a><span data-ttu-id="438ff-170">Schritt 1: Durchführen der Registrierung für Ereignisse zur Änderung des Geofence-Zustands</span><span class="sxs-lookup"><span data-stu-id="438ff-170">Step 1: Register for geofence state change events</span></span>

<span data-ttu-id="438ff-171">Fügen Sie im App-Manifest auf der Registerkarte **Deklarationen** eine Deklaration für eine Hintergrundaufgabe zum Standort hinzu.</span><span class="sxs-lookup"><span data-stu-id="438ff-171">In your app's manifest, under the **Declarations** tab, add a declaration for a location background task.</span></span> <span data-ttu-id="438ff-172">Gehen Sie wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="438ff-172">To do this:</span></span>

-   <span data-ttu-id="438ff-173">Fügen Sie eine Deklaration vom Typ **Hintergrundaufgaben** hinzu.</span><span class="sxs-lookup"><span data-stu-id="438ff-173">Add a declaration of type **Background Tasks**.</span></span>
-   <span data-ttu-id="438ff-174">Legen Sie den Eigenschaftenaufgabentyp **Standort** fest.</span><span class="sxs-lookup"><span data-stu-id="438ff-174">Set a property task type of **Location**.</span></span>
-   <span data-ttu-id="438ff-175">Legen Sie einen Einstiegspunkt für die App fest, der aufgerufen wird, wenn das Ereignis ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="438ff-175">Set an entry point into your app to call when the event is triggered.</span></span>

### <a name="step-2-register-the-background-task"></a><span data-ttu-id="438ff-176">Schritt 2: Registrieren der Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="438ff-176">Step 2: Register the background task</span></span>

<span data-ttu-id="438ff-177">Mit dem Code in diesem Schritt wird die Geofencing-Hintergrundaufgabe registriert.</span><span class="sxs-lookup"><span data-stu-id="438ff-177">The code in this step registers the geofencing background task.</span></span> <span data-ttu-id="438ff-178">Beachten Sie, dass bei der Erstellung des Geofence-Bereichs eine Überprüfung auf Positionsberechtigungen durchgeführt wurde.</span><span class="sxs-lookup"><span data-stu-id="438ff-178">Recall that when the geofence was created, we checked for location permissions.</span></span>

```csharp
async private void RegisterBackgroundTask(object sender, RoutedEventArgs e)
{
    // Get permission for a background task from the user. If the user has already answered once,
    // this does nothing and the user must manually update their preference via PC Settings.
    BackgroundAccessStatus backgroundAccessStatus = await BackgroundExecutionManager.RequestAccessAsync();

    // Regardless of the answer, register the background task. Note that the user can use
    // the Settings app to prevent your app from running background tasks.
    // Create a new background task builder.
    BackgroundTaskBuilder geofenceTaskBuilder = new BackgroundTaskBuilder();

    geofenceTaskBuilder.Name = SampleBackgroundTaskName;
    geofenceTaskBuilder.TaskEntryPoint = SampleBackgroundTaskEntryPoint;

    // Create a new location trigger.
    var trigger = new LocationTrigger(LocationTriggerType.Geofence);

    // Associate the location trigger with the background task builder.
    geofenceTaskBuilder.SetTrigger(trigger);

    // If it is important that there is user presence and/or
    // internet connection when OnCompleted is called
    // the following could be called before calling Register().
    // SystemCondition condition = new SystemCondition(SystemConditionType.UserPresent | SystemConditionType.InternetAvailable);
    // geofenceTaskBuilder.AddCondition(condition);

    // Register the background task.
    geofenceTask = geofenceTaskBuilder.Register();

    // Associate an event handler with the new background task.
    geofenceTask.Completed += new BackgroundTaskCompletedEventHandler(OnCompleted);

    BackgroundTaskState.RegisterBackgroundTask(BackgroundTaskState.LocationTriggerBackgroundTaskName);

    switch (backgroundAccessStatus)
    {
    case BackgroundAccessStatus.Unspecified:
    case BackgroundAccessStatus.Denied:
        rootPage.NotifyUser("This app is not allowed to run in the background.", NotifyType.ErrorMessage);
        break;

    }
}


```

### <a name="step-3-handling-the-background-notification"></a><span data-ttu-id="438ff-179">Schritt 3: Behandeln der Hintergrundbenachrichtigung</span><span class="sxs-lookup"><span data-stu-id="438ff-179">Step 3: Handling the background notification</span></span>

<span data-ttu-id="438ff-180">Die Aktion, die Sie zum Benachrichtigen der Benutzer durchführen, richtet sich nach dem Verwendungszweck der App. Sie können aber z.B. eine Popupbenachrichtigung anzeigen, einen Ton wiedergeben oder eine Live-Kachel aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="438ff-180">The action that you take to notify the user depends on what your app does, but you can display a toast notification, play an audio sound, or update a live tile.</span></span> <span data-ttu-id="438ff-181">Der Code in diesem Schritt dient zum Behandeln der Benachrichtigung.</span><span class="sxs-lookup"><span data-stu-id="438ff-181">The code in this step handles the notification.</span></span>

```csharp
async private void OnCompleted(IBackgroundTaskRegistration sender, BackgroundTaskCompletedEventArgs e)
{
    if (sender != null)
    {
        // Update the UI with progress reported by the background task.
        await Dispatcher.RunAsync(CoreDispatcherPriority.Normal, () =>
        {
            try
            {
                // If the background task threw an exception, display the exception in
                // the error text box.
                e.CheckResult();

                // Update the UI with the completion status of the background task.
                // The Run method of the background task sets the LocalSettings.
                var settings = ApplicationData.Current.LocalSettings;

                // Get the status.
                if (settings.Values.ContainsKey("Status"))
                {
                    rootPage.NotifyUser(settings.Values["Status"].ToString(), NotifyType.StatusMessage);
                }

                // Do your app work here.

            }
            catch (Exception ex)
            {
                // The background task had an error.
                rootPage.NotifyUser(ex.ToString(), NotifyType.ErrorMessage);
            }
        });
    }
}


```

## <a name="change-the-privacy-settings"></a><span data-ttu-id="438ff-182">Ändern der Datenschutzeinstellungen</span><span class="sxs-lookup"><span data-stu-id="438ff-182">Change the privacy settings</span></span>


<span data-ttu-id="438ff-183">Wenn Ihre App gemäß den Standortdatenschutzeinstellungen nicht auf den Standort des Benutzers zugreifen darf, sollten Sie einen praktischen Link zu den **Standortdatenschutzeinstellungen** in der **Einstellungs**-App bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="438ff-183">If the location privacy settings don't allow your app to access the user's location, we recommend that you provide a convenient link to the **location privacy settings** in the **Settings** app.</span></span> <span data-ttu-id="438ff-184">In diesem Beispiel wird ein Hyperlink-Steuerelement verwendet, um zum `ms-settings:privacy-location`-URI zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="438ff-184">In this example, a Hyperlink control is used navigate to the `ms-settings:privacy-location` URI.</span></span>

```xml
<!--Set Visibility to Visible when access to the user's location is denied. -->  
<TextBlock x:Name="LocationDisabledMessage" FontStyle="Italic"
                 Visibility="Collapsed" Margin="0,15,0,0" TextWrapping="Wrap" >
          <Run Text="This app is not able to access Location. Go to " />
              <Hyperlink NavigateUri="ms-settings:privacy-location">
                  <Run Text="Settings" />
              </Hyperlink>
          <Run Text=" to check the location privacy settings."/>
</TextBlock>
```

<span data-ttu-id="438ff-185">Alternativ kann Ihre App die [**LaunchUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701476)-Methode aufrufen, um die **Einstellungs**-App per Code zu starten.</span><span class="sxs-lookup"><span data-stu-id="438ff-185">Alternatively, your app can call the [**LaunchUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701476) method to launch the **Settings** app from code.</span></span> <span data-ttu-id="438ff-186">Weitere Informationen finden Sie unter [Starten der Einstellungs-App von Windows](https://msdn.microsoft.com/library/windows/apps/mt228342).</span><span class="sxs-lookup"><span data-stu-id="438ff-186">For more info, see [Launch the Windows Settings app](https://msdn.microsoft.com/library/windows/apps/mt228342).</span></span>

```csharp
using Windows.System;
...
bool result = await Launcher.LaunchUriAsync(new Uri("ms-settings:privacy-location"));
```

## <a name="test-and-debug-your-app"></a><span data-ttu-id="438ff-187">Testen und Debuggen der App</span><span class="sxs-lookup"><span data-stu-id="438ff-187">Test and debug your app</span></span>


<span data-ttu-id="438ff-188">Das Testen und Debuggen von Geofencing-Apps kann eine Herausforderung sein, da diese Apps von der Position des Geräts abhängig sind.</span><span class="sxs-lookup"><span data-stu-id="438ff-188">Testing and debugging geofencing apps can be a challenge because they depend on a device's location.</span></span> <span data-ttu-id="438ff-189">Im Folgenden stellen wir verschiedene Methoden zum Testen von im Vordergrund und im Hintergrund ausgeführten Geofencing-Apps vor.</span><span class="sxs-lookup"><span data-stu-id="438ff-189">Here, we outline several methods for testing both foreground and background geofences.</span></span>

**<span data-ttu-id="438ff-190">So debuggen Sie eine Geofencing-App</span><span class="sxs-lookup"><span data-stu-id="438ff-190">To debug a geofencing app</span></span>**

1.  <span data-ttu-id="438ff-191">Bewegen Sie das Gerät physisch an eine neue Position.</span><span class="sxs-lookup"><span data-stu-id="438ff-191">Physically move the device to new locations.</span></span>
2.  <span data-ttu-id="438ff-192">Sie können das Betreten eines Geofences testen, indem Sie eine Geofence-Region erstellen, die Ihre aktuelle Position enthält. Auf diese Weise befinden Sie sich bereits innerhalb des Geofences, und das Ereignis „Geofence betreten“ wird sofort ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="438ff-192">Test entering a geofence by creating a geofence region that includes your current physical location, so you're already inside the geofence and the "geofence entered" event is triggered immediately.</span></span>
3.  <span data-ttu-id="438ff-193">Verwenden Sie den MicrosoftVisual Studio-Emulator, um Positionen für das Gerät zu simulieren.</span><span class="sxs-lookup"><span data-stu-id="438ff-193">Use the Microsoft Visual Studio emulator to simulate locations for the device.</span></span>

### <a name="test-and-debug-a-geofencing-app-that-is-running-in-the-foreground"></a><span data-ttu-id="438ff-194">Testen und Debuggen einer im Vordergrund ausgeführten Geofencing-App</span><span class="sxs-lookup"><span data-stu-id="438ff-194">Test and debug a geofencing app that is running in the foreground</span></span>

**<span data-ttu-id="438ff-195">So testen Sie eine im Vordergrund ausgeführte Geofencing-App</span><span class="sxs-lookup"><span data-stu-id="438ff-195">To test your geofencing app that is running the foreground</span></span>**

1.  <span data-ttu-id="438ff-196">Erstellen Sie Ihre App in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="438ff-196">Build your app in Visual Studio.</span></span>
2.  <span data-ttu-id="438ff-197">Starten Sie Ihre App im Visual Studio-Emulator.</span><span class="sxs-lookup"><span data-stu-id="438ff-197">Launch your app in the Visual Studio emulator.</span></span>
3.  <span data-ttu-id="438ff-198">Simulieren Sie mit den Tools verschiedene Positionen innerhalb und außerhalb Ihres Geofence-Bereichs.</span><span class="sxs-lookup"><span data-stu-id="438ff-198">Use these tools to simulate various locations inside and outside of your geofence region.</span></span> <span data-ttu-id="438ff-199">Damit das Ereignis ausgelöst wird, müssen Sie nach der mit der [**DwellTime**](https://msdn.microsoft.com/library/windows/apps/dn263703)-Eigenschaft festgelegten Verweilzeit ausreichend lange warten.</span><span class="sxs-lookup"><span data-stu-id="438ff-199">Be sure to wait long enough past the time specified by the [**DwellTime**](https://msdn.microsoft.com/library/windows/apps/dn263703) property to trigger the event.</span></span> <span data-ttu-id="438ff-200">Sie müssen in der Eingabeaufforderung Ihre Zustimmung geben, um der App Berechtigungen zum Verwenden der Position zu gewähren.</span><span class="sxs-lookup"><span data-stu-id="438ff-200">Note that you must accept the prompt to enable location permissions for the app.</span></span> <span data-ttu-id="438ff-201">Weitere Informationen zum Simulieren von Positionen finden Sie unter [Festlegen der simulierten geografischen Position des Geräts](http://go.microsoft.com/fwlink/p/?LinkID=325245).</span><span class="sxs-lookup"><span data-stu-id="438ff-201">For more info about simulating locations, see [Set the simulated geolocation of the device](http://go.microsoft.com/fwlink/p/?LinkID=325245).</span></span>
4.  <span data-ttu-id="438ff-202">Sie können auch den Emulator verwenden, um die Größe von Umgrenzungen sowie die Verweildauer zu schätzen, die für die Erkennung bei unterschiedlichen Geschwindigkeiten ungefähr notwendig ist.</span><span class="sxs-lookup"><span data-stu-id="438ff-202">You can also use the emulator to estimate the size of fences and dwell times approximately needed to be detected at different speeds.</span></span>

### <a name="test-and-debug-a-geofencing-app-that-is-running-in-the-background"></a><span data-ttu-id="438ff-203">Testen und Debuggen einer im Hintergrund ausgeführten Geofencing-App</span><span class="sxs-lookup"><span data-stu-id="438ff-203">Test and debug a geofencing app that is running in the background</span></span>

**<span data-ttu-id="438ff-204">So testen Sie eine im Hintergrund ausgeführte Geofencing-App</span><span class="sxs-lookup"><span data-stu-id="438ff-204">To test your geofencing app that is running the background</span></span>**

1.  <span data-ttu-id="438ff-205">Erstellen Sie Ihre App in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="438ff-205">Build your app in Visual Studio.</span></span> <span data-ttu-id="438ff-206">Beachten Sie, dass Ihre App den Hintergrundaufgabentyp **Position** festlegen muss.</span><span class="sxs-lookup"><span data-stu-id="438ff-206">Note that your app should set the **Location** background task type.</span></span>
2.  <span data-ttu-id="438ff-207">Stellen Sie die App zunächst lokal bereit.</span><span class="sxs-lookup"><span data-stu-id="438ff-207">Deploy the app locally first.</span></span>
3.  <span data-ttu-id="438ff-208">Schließen Sie die lokal ausgeführte App.</span><span class="sxs-lookup"><span data-stu-id="438ff-208">Close your app that is running locally.</span></span>
4.  <span data-ttu-id="438ff-209">Starten Sie Ihre App im Visual Studio-Emulator.</span><span class="sxs-lookup"><span data-stu-id="438ff-209">Launch your app in the Visual Studio emulator.</span></span> <span data-ttu-id="438ff-210">Die Geofencingsimulation im Hintergrund wird im Emulator jeweils nur für eine App unterstützt.</span><span class="sxs-lookup"><span data-stu-id="438ff-210">Note that background geofencing simulation is supported on only one app at a time within the emulator.</span></span> <span data-ttu-id="438ff-211">Starten Sie nicht mehrere Geofencing-Apps im Emulator.</span><span class="sxs-lookup"><span data-stu-id="438ff-211">Do not launch multiple geofencing apps within the emulator.</span></span>
5.  <span data-ttu-id="438ff-212">Simulieren Sie im Emulator verschiedene Positionen innerhalb und außerhalb Ihrer Geofence-Region.</span><span class="sxs-lookup"><span data-stu-id="438ff-212">From the emulator, simulate various locations inside and outside of your geofence region.</span></span> <span data-ttu-id="438ff-213">Damit das Ereignis ausgelöst wird, müssen Sie nach der Verweilzeit ([**DwellTime**](https://msdn.microsoft.com/library/windows/apps/dn263703)) ausreichend lange warten.</span><span class="sxs-lookup"><span data-stu-id="438ff-213">Be sure to wait long enough past the [**DwellTime**](https://msdn.microsoft.com/library/windows/apps/dn263703) to trigger the event.</span></span> <span data-ttu-id="438ff-214">Sie müssen in der Eingabeaufforderung Ihre Zustimmung geben, um der App Berechtigungen zum Verwenden der Position zu gewähren.</span><span class="sxs-lookup"><span data-stu-id="438ff-214">Note that you must accept the prompt to enable location permissions for the app.</span></span>
6.  <span data-ttu-id="438ff-215">Verwenden Sie Visual Studio, um die Hintergrundaufgabe für die Position auszulösen.</span><span class="sxs-lookup"><span data-stu-id="438ff-215">Use Visual Studio to trigger the location background task.</span></span> <span data-ttu-id="438ff-216">Weitere Informationen zum Auslösen von Hintergrundaufgaben in Visual Studio finden Sie unter [So wird’s gemacht: Auslösen von Hintergrundaufgaben](http://go.microsoft.com/fwlink/p/?LinkID=325378).</span><span class="sxs-lookup"><span data-stu-id="438ff-216">For more info about triggering background tasks in Visual Studio, see [How to trigger background tasks](http://go.microsoft.com/fwlink/p/?LinkID=325378).</span></span>

## <a name="troubleshoot-your-app"></a><span data-ttu-id="438ff-217">Behandeln von App-Problemen</span><span class="sxs-lookup"><span data-stu-id="438ff-217">Troubleshoot your app</span></span>


<span data-ttu-id="438ff-218">Bevor Ihre App auf Positionsdaten zugreifen kann, muss **Position** auf dem Gerät aktiviert sein.</span><span class="sxs-lookup"><span data-stu-id="438ff-218">Before your app can access location, **Location** must be enabled on the device.</span></span> <span data-ttu-id="438ff-219">Vergewissern Sie sich in der **Einstellungs**-App, dass die folgenden **Datenschutzeinstellungen für den Standort** aktiviert sind:</span><span class="sxs-lookup"><span data-stu-id="438ff-219">In the **Settings** app, check that the following **location privacy settings** are turned on:</span></span>

-   <span data-ttu-id="438ff-220">**Position dieses Geräts...** ist **aktiviert (gilt nicht für Windows 10 Mobile)**</span><span class="sxs-lookup"><span data-stu-id="438ff-220">**Location for this device...** is turned **on** (not applicable in Windows10 Mobile)</span></span>
-   <span data-ttu-id="438ff-221">Die Einstellung **Position** der Positionsdienste ist **aktiviert**.</span><span class="sxs-lookup"><span data-stu-id="438ff-221">The location services setting, **Location**, is turned **on**</span></span>
-   <span data-ttu-id="438ff-222">Ihre App hat unter **Wählen Sie Apps aus, die Ihre Position verwenden dürfen** die Einstellung **Ein**.</span><span class="sxs-lookup"><span data-stu-id="438ff-222">Under **Choose apps that can use your location**, your app is set to **on**</span></span>

## <a name="related-topics"></a><span data-ttu-id="438ff-223">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="438ff-223">Related topics</span></span>

* [<span data-ttu-id="438ff-224">UWP-Geolocation-Beispiel</span><span class="sxs-lookup"><span data-stu-id="438ff-224">UWP geolocation sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=533278)
* [<span data-ttu-id="438ff-225">Entwurfsrichtlinien für Geofencing</span><span class="sxs-lookup"><span data-stu-id="438ff-225">Design guidelines for geofencing</span></span>](https://msdn.microsoft.com/library/windows/apps/dn631756)
* [<span data-ttu-id="438ff-226">Entwurfsrichtlinien für Apps mit Positionsbestimmung</span><span class="sxs-lookup"><span data-stu-id="438ff-226">Design guidelines for location-aware apps</span></span>](https://msdn.microsoft.com/library/windows/apps/hh465148)
