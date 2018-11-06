---
author: PatrickFarley
Description: Learn how to use the powerful Visits Tracking feature for more practical location tracking.
title: Richtlinien für die Verwendung von Visits Tracking
ms.assetid: 0c101684-48a9-4592-9ed5-6c20f3b830f2
ms.author: pafarley
ms.date: 05/18/2017
ms.topic: article
keywords: Windows10, UWP, Karte, Standort, Geovisit, geovisits
ms.localizationpriority: medium
ms.openlocfilehash: 3a78b2689a10dff50696e5e65cc44f79a6f1ea7d
ms.sourcegitcommit: e814a13978f33654d8e995584f4b047cb53e0aef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "6046727"
---
# <a name="guidelines-for-using-visits-tracking"></a><span data-ttu-id="f30ff-103">Richtlinien für die Verwendung von Visits Tracking</span><span class="sxs-lookup"><span data-stu-id="f30ff-103">Guidelines for using Visits tracking</span></span>

<span data-ttu-id="f30ff-104">Die Funktion Visits optimiert den Prozess der Standortnachverfolgung, um die praktische Erfahrung vieler Apps effizienter zu gestalten.</span><span class="sxs-lookup"><span data-stu-id="f30ff-104">The Visits feature streamlines the process of location tracking to make it more efficient for the practical purposes of many apps.</span></span> <span data-ttu-id="f30ff-105">Ein Besuch (Visit) wird als wichtiger geografischer Bereich definiert, den der Benutzer betritt und wieder verlässt.</span><span class="sxs-lookup"><span data-stu-id="f30ff-105">A Visit is defined as a significant geographical area that the user enters and exits.</span></span> <span data-ttu-id="f30ff-106">Besuche ähneln [Geofences](guidelines-for-geofencing.md) darin, dass die App benachrichtigt wird, wenn der Benutzer ein bestimmtes Interessengebiet betritt oder verlässt. Dies macht die kontinuierlichen Standortnachverfolgung überflüssig, die die Akkulaufzeit beeinträchtigt.</span><span class="sxs-lookup"><span data-stu-id="f30ff-106">Visits are similar to [geofences](guidelines-for-geofencing.md) in that they allow the app to be notified only when the user enters or exits certain areas of interest, eliminating the need for continual location tracking which can be a drain on battery life.</span></span> <span data-ttu-id="f30ff-107">Allerdings werden im Gegensatz zu Geofences die Bereiche eines Besuchs dynamisch auf der Plattform identifiziert und müssen nicht explizit durch einzelne Apps definiert werden.</span><span class="sxs-lookup"><span data-stu-id="f30ff-107">However, unlike geofences, Visit areas are dynamically identified at the platform level and do not need to be defined explicitly by individual apps.</span></span> <span data-ttu-id="f30ff-108">Außerdem wird die Auswahl der Besuche, die eine App aufzeichnet, durch eine einzelne Genauigkeitseinstellung behandelt und nicht durch das Abonnieren einzelner Orte.</span><span class="sxs-lookup"><span data-stu-id="f30ff-108">Also, the selection of which Visits an app will track is handled by a single granularity setting, rather than by subscribing to individual places.</span></span>

## <a name="preliminary-setup"></a><span data-ttu-id="f30ff-109">Vorläufige Einrichtung</span><span class="sxs-lookup"><span data-stu-id="f30ff-109">Preliminary setup</span></span>

<span data-ttu-id="f30ff-110">Bevor Sie fortfahren, stellen Sie sicher, dass Ihre App auf die Position des Geräts zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="f30ff-110">Before going further, make sure your app is capable of accessing the device's location.</span></span> <span data-ttu-id="f30ff-111">Sie müssen die `Location`-Funktion im Manifest angeben und die **[Geolocator.RequestAccessAsync](https://docs.microsoft.com/uwp/api/Windows.Devices.Geolocation.Geolocator.RequestAccessAsync)**-Methode aufrufen, um sicherzustellen, dass Benutzer der App Standortberechtigungen verleihen.</span><span class="sxs-lookup"><span data-stu-id="f30ff-111">You will need to declare the `Location` capability in the manifest and call the **[Geolocator.RequestAccessAsync](https://docs.microsoft.com/uwp/api/Windows.Devices.Geolocation.Geolocator.RequestAccessAsync)** method to ensure that users give the app location permissions.</span></span> <span data-ttu-id="f30ff-112">Weitere Informationen hierzu finden Sie unter [Position des Benutzers abrufen](get-location.md).</span><span class="sxs-lookup"><span data-stu-id="f30ff-112">See [Get the user's location](get-location.md) for more information on how to do this.</span></span> 

<span data-ttu-id="f30ff-113">Denken Sie daran, Ihrer Klasse einen `Geolocation`-Namespace hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="f30ff-113">Remember to add the `Geolocation` namespace to your class.</span></span> <span data-ttu-id="f30ff-114">Dies ist für die einwandfreie Ausführung aller Codeausschnitte in diesem Handbuch erforderlich.</span><span class="sxs-lookup"><span data-stu-id="f30ff-114">This will be needed for all of the code snippets in this guide to work.</span></span>

```csharp
using Windows.Devices.Geolocation;
```

## <a name="check-the-latest-visit"></a><span data-ttu-id="f30ff-115">Überprüfen Sie den neusten Besuch</span><span class="sxs-lookup"><span data-stu-id="f30ff-115">Check the latest Visit</span></span>
<span data-ttu-id="f30ff-116">Die einfachste Möglichkeit, die „Visits Tracking”-Funktion zu verwenden, ist die letzte bekannte Statusänderung abzurufen, die mit dem Besuch verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="f30ff-116">The simplest way to use the Visits tracking feature is to retrieve the last known Visit-related state change.</span></span> <span data-ttu-id="f30ff-117">Eine Statusänderung ist ein von der Plattform protokolliertes Ereignis, wobei der Benutzer entweder einen wichtigen Standort betritt/verlässt, seit dem letzten Bericht eine beträchtliche Veränderung geschah oder wenn der Standort des Benutzers verloren geht (Informationen finden Sie in der Enumeration **[VisitStateChange](https://docs.microsoft.com/uwp/api/windows.devices.geolocation.visitstatechange)**).</span><span class="sxs-lookup"><span data-stu-id="f30ff-117">A state change is a platform-logged event in which either the user enters/exits a location of significance, there is significant movement since the last report, or the user's location is lost (see the **[VisitStateChange](https://docs.microsoft.com/uwp/api/windows.devices.geolocation.visitstatechange)** enum).</span></span> <span data-ttu-id="f30ff-118">Statusänderungen werden durch **[Geovisit](https://docs.microsoft.com/uwp/api/windows.devices.geolocation.geovisit)**-Instanzen dargestellt.</span><span class="sxs-lookup"><span data-stu-id="f30ff-118">State changes are represented by **[Geovisit](https://docs.microsoft.com/uwp/api/windows.devices.geolocation.geovisit)** instances.</span></span> <span data-ttu-id="f30ff-119">Um die **Geovisit**-Instanz der letzten aufgezeichneten Statusänderung aufzurufen, verwenden Sie einfach die dafür vorgesehene Methode in der **[GeovisitMonitor](https://docs.microsoft.com/uwp/api/windows.devices.geolocation.geovisitmonitor)**-Klasse.</span><span class="sxs-lookup"><span data-stu-id="f30ff-119">To retrieve the **Geovisit** instance for the last recorded state change, simply use the designated method in the **[GeovisitMonitor](https://docs.microsoft.com/uwp/api/windows.devices.geolocation.geovisitmonitor)** class.</span></span>

> [!NOTE]
> <span data-ttu-id="f30ff-120">Das Überprüfen des letzten angemeldeten Besuchs garantiert nicht, dass alle Besuche derzeit vom System nachverfolgt werden.</span><span class="sxs-lookup"><span data-stu-id="f30ff-120">Checking the last logged Visit does not guarantee that Visits are currently being tracked by the system.</span></span> <span data-ttu-id="f30ff-121">Um Besuche direkt nachzuverfolgen, müssen Sie diese entweder im Vordergrund überwachen oder sich für die Verfolgung von Hintergrundaufgaben anmelden (siehe unten).</span><span class="sxs-lookup"><span data-stu-id="f30ff-121">In order to track Visits as they happen, you must either be monitoring them in the foreground or register for background tracking (see sections below).</span></span>

```csharp
private async void GetLatestStateChange() {
    // retrieve the Geovisit instance
    Geovisit latestVisit = await GeovisitMonitor.GetLastReportAsync();

    // Using the properties of "latestVisit", parse out the time that the state 
    // change was recorded, the device's location when the change was recorded,
    // and the type of state change.
}
```

### <a name="parse-a-geovisit-instance-optional"></a><span data-ttu-id="f30ff-122">Analysieren einer Geovisit-Instanz (optional)</span><span class="sxs-lookup"><span data-stu-id="f30ff-122">Parse a Geovisit instance (optional)</span></span>
<span data-ttu-id="f30ff-123">Die folgende Methode konvertiert alle in einer **Geovisit**-Instanz gespeicherten Informationen in eine leicht lesbare Zeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="f30ff-123">The following method converts all of the information stored in a **Geovisit** instance into an easily readable string.</span></span> <span data-ttu-id="f30ff-124">Dies kann in allen Szenarien dieses Handbuchs verwendet werden, um Feedback für die gemeldeten Besuche bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="f30ff-124">It can be used in any of the scenarios in this guide to help provide feedback for the Visits being reported.</span></span>

```csharp
private string ParseGeovisit(Geovisit visit){
    string visitString = null;

    // Use a DateTimeFormatter object to process the timestamp. The following
    // format configuration will give an intuitive representation of the date/time
    Windows.Globalization.DateTimeFormatting.DateTimeFormatter formatterLongTime;
    
    formatterLongTime = new Windows.Globalization.DateTimeFormatting.DateTimeFormatter(
        "{hour.integer}:{minute.integer(2)}:{second.integer(2)}", new[] { "en-US" }, "US", 
        Windows.Globalization.CalendarIdentifiers.Gregorian, 
        Windows.Globalization.ClockIdentifiers.TwentyFourHour);
    
    // use this formatter to convert the timestamp to a string, and add to "visitString"
    visitString = formatterLongTime.Format(visit.Timestamp);

    // Next, add on the state change type value
    visitString += " " + visit.StateChange.ToString();

    // Next, add the position information (if any is provided; this will be null if 
    // the reported event was "TrackingLost")
    if (visit.Position != null) {
        visitString += " (" +
        visit.Position.Coordinate.Point.Position.Latitude.ToString() + "," +
        visit.Position.Coordinate.Point.Position.Longitude.ToString() + 
        ")";
    }

    return visitString;
}
```

## <a name="monitor-visits-in-the-foreground"></a><span data-ttu-id="f30ff-125">Besuche im Vordergrund überwachen</span><span class="sxs-lookup"><span data-stu-id="f30ff-125">Monitor Visits in the foreground</span></span>

<span data-ttu-id="f30ff-126">Die **GeovisitMonitor**-Klasse, die im vorherigen Abschnitt verwendet wurde, sorgt auch für das Szenario der Überwachung der Statusänderung in einem gewissen Zeitraum.</span><span class="sxs-lookup"><span data-stu-id="f30ff-126">The **GeovisitMonitor** class used in the previous section also handles the scenario of listening for state changes over a period of time.</span></span> <span data-ttu-id="f30ff-127">Verwenden Sie hierzu die Instanziierung der Klasse, die Registrierung einer Handlermethode für das Ereignis und das Aufrufen der `Start`-Methode.</span><span class="sxs-lookup"><span data-stu-id="f30ff-127">You can do this by instantiating this class, registering a handler method for its event, and calling the `Start` method.</span></span>

```csharp
// this GeovisitMonitor instance will belong to the class scope
GeovisitMonitor monitor;

public void RegisterForVisits() {

    // Create and initialize a new monitor instance.
    monitor = new GeovisitMonitor();
    
    // Attach a handler to receive state change notifications.
    monitor.VisitStateChanged += OnVisitStateChanged;
    
    // Calling the start method will start Visits tracking for a specified scope:
    // For higher granularity such as venue/building level changes, choose Venue.
    // For lower granularity in the range of zipcode level changes, choose City.
    monitor.Start(VisitMonitoringScope.Venue);
}
```

<span data-ttu-id="f30ff-128">In diesem Beispiel übernimmt die `OnVisitStateChanged`-Methode eingehende Bericht über Besuche.</span><span class="sxs-lookup"><span data-stu-id="f30ff-128">In this example, the `OnVisitStateChanged` method will handle incoming Visit reports.</span></span> <span data-ttu-id="f30ff-129">Das entsprechende **Geovisit**-Instanz wird über den Ereignisparameter übergeben.</span><span class="sxs-lookup"><span data-stu-id="f30ff-129">The corresponding **Geovisit** instance is passed in through the event parameter.</span></span>

```csharp
private void OnVisitStateChanged(GeoVisitWatcher sender, GeoVisitStateChangedEventArgs args) {
    Geovisit visit = args.Visit;
    
    // Using the properties of "visit", parse out the time that the state 
    // change was recorded, the device's location when the change was recorded,
    // and the type of state change.
}
```
<span data-ttu-id="f30ff-130">Wenn die App mit der Überwachung der Statusänderungen, die mit dem Besuch verbunden sind, fertig ist, sollte die Überwachung beendet werden und die Registrierung des Ereignishandlers aufgehoben werden.</span><span class="sxs-lookup"><span data-stu-id="f30ff-130">When the app is finished monitoring for Visit-related state changes, it should stop the monitor and unregister the event handler(s).</span></span> <span data-ttu-id="f30ff-131">Dies sollte auch dann durchgeführt werden, wenn die App angehalten oder geschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="f30ff-131">This should also be done whenever the app is suspended or closed.</span></span>

```csharp
public void UnregisterFromVisits() {
    
    // Stop the monitor to stop tracking Visits. Otherwise, tracking will
    // continue until the monitor instance is destroyed.
    monitor.Stop();
    
    // Remove the handler to stop receiving state change events.
    monitor.VisitStateChanged -= OnVisitStateChanged;
}
```

## <a name="monitor-visits-in-the-background"></a><span data-ttu-id="f30ff-132">Besuche im Hintergrund überwachen</span><span class="sxs-lookup"><span data-stu-id="f30ff-132">Monitor Visits in the background</span></span>

<span data-ttu-id="f30ff-133">Sie können ebenfalls die Überwachung der Besuche als Hintergrundaufgabe implementieren, damit die mit dem Besuch verbundene Aktivitäten auf dem Gerät auch dann verarbeitet werden kann, wenn Ihre App nicht geöffnet ist.</span><span class="sxs-lookup"><span data-stu-id="f30ff-133">You can also implement Visit monitoring in a background task, so that Visit-related activity can be handled on the device even when your app isn't open.</span></span> <span data-ttu-id="f30ff-134">Diese Methode wird empfohlen, da sie vielseitiger und energieeffizienter ist.</span><span class="sxs-lookup"><span data-stu-id="f30ff-134">This is the recommended method, as it is more versatile and energy-efficient.</span></span> 

<span data-ttu-id="f30ff-135">Dieses Handbuch verwendet das unter [Erstellen und Registrieren einer Hintergrundaufgabe außerhalb des Prozesses](https://docs.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task) beschriebene Modell, in dem die Hauptanwendungsdateien sich in einem Projekt befindet und die Hintergrundaufgabendatei sich in einem separaten Projekt in der gleichen Lösung befindet.</span><span class="sxs-lookup"><span data-stu-id="f30ff-135">This guide will use the model in [Create and register an out-of-process background task](https://docs.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task), in which the main application files live in one project and the background task file lives in a separate project in the same solution.</span></span> <span data-ttu-id="f30ff-136">Wenn Sie nicht mit dem Implementieren von Hintergrundaufgaben vertraut sind, empfiehlt es sich, dass Sie dieser Anleitung vorwiegend folgen und die erforderlichen Ersetzungen durchführen, um eine Aufgabe als Hintergrundaufgabe zu erstellen, die die Besuche behandelt.</span><span class="sxs-lookup"><span data-stu-id="f30ff-136">If you are new to implementing background tasks, it is recommended that you follow that guidance primarily, making the necessary substitutions below to create a Visit-handling background task.</span></span>

> [!NOTE]
> <span data-ttu-id="f30ff-137">In den folgenden Codeausschnitten wurden einige wichtige Funktionen wie z.B. die Fehlerbehandlung und das lokale Speichern aus Gründen der Einfachheit weggelassen.</span><span class="sxs-lookup"><span data-stu-id="f30ff-137">In the following snippets, some important functionality such as error handling and local storage is absent for the sake of simplicity.</span></span> <span data-ttu-id="f30ff-138">Eine robuste Implementierung der Behandlung der Besuche im Hintergrund finden Sie in der [Beispiel-App](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Geolocation).</span><span class="sxs-lookup"><span data-stu-id="f30ff-138">For a robust implementation of background Visits handling, see the [sample app](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Geolocation).</span></span>


<span data-ttu-id="f30ff-139">Stellen Sie zunächst sicher, dass Ihre App die Berechtigung für Hintergrundaufgaben deklariert hat.</span><span class="sxs-lookup"><span data-stu-id="f30ff-139">First, make sure your app has declared background task permissions.</span></span> <span data-ttu-id="f30ff-140">Fügen Sie dem `Application/Extensions`-Element Ihrer *"Package.appxmanifest"*-Datei die folgende Erweiterung hinzu (fügen Sie ein `Extensions`-Element hinzu, wenn es nicht bereits existiert).</span><span class="sxs-lookup"><span data-stu-id="f30ff-140">In the `Application/Extensions` element of your *Package.appxmanifest* file, add the following extension (add an `Extensions` element if one does not already exist).</span></span>

```xml
<Extension Category="windows.backgroundTasks" EntryPoint="Tasks.VisitBackgroundTask">
    <BackgroundTasks>
        <Task Type="location" />
    </BackgroundTasks>
</Extension>
```

<span data-ttu-id="f30ff-141">Fügen Sie als Nächstes in der Definition der Hintergrundaufgabenklasse folgenden Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="f30ff-141">Next, in the definition of the background task class, paste in the following code.</span></span> <span data-ttu-id="f30ff-142">Die `Run`-Methode dieser Hintergrundaufgabe übergibt die Triggerdetails (die die Besuchsinformationen enthalten) ganz einfach an eine separate Methode.</span><span class="sxs-lookup"><span data-stu-id="f30ff-142">The `Run` method of this background task will simply pass the trigger details (which contain the Visits information) into a separate method.</span></span>

```csharp
using Windows.ApplicationModel.Background;

namespace Tasks {
    
    public sealed class VisitBackgroundTask : IBackgroundTask {
        
        public void Run(IBackgroundTaskInstance taskInstance) {
            
            // get a deferral
            BackgroundTaskDeferral deferral = taskInstance.GetDeferral();
            
            // this task's trigger will be a Geovisit trigger
            GeovisitTriggerDetails triggerDetails = taskInstance.TriggerDetails as GeovisitTriggerDetails;

            // Handle Visit reports
            GetVisitReports(triggerDetails);         

            finally {
                deferral.Complete();
            }
        }        
    }
}
```

<span data-ttu-id="f30ff-143">Definieren Sie die `GetVisitReports`-Methode an einer beliebigen Stelle in dieser Klasse.</span><span class="sxs-lookup"><span data-stu-id="f30ff-143">Define the `GetVisitReports` method somewhere in this same class.</span></span>

```csharp
private void GetVisitReports(GeovisitTriggerDetails triggerDetails) {

    // Read reports from the triggerDetails. This populates the "reports" variable 
    // with all of the Geovisit instances that have been logged since the previous
    // report reading.
    IReadOnlyList<Geovisit> reports = triggerDetails.ReadReports();

    foreach (Geovisit report in reports) {
        // Using the properties of "visit", parse out the time that the state 
        // change was recorded, the device's location when the change was recorded,
        // and the type of state change.
    }

    // Note: depending on the intent of the app, you many wish to store the
    // reports in the app's local storage so they can be retrieved the next time 
    // the app is opened in the foreground.
}
```

<span data-ttu-id="f30ff-144">Sie müssen als Nächstes im Hauptprojekt Ihrer App die Registrierung der Hintergrundaufgabe ausführen.</span><span class="sxs-lookup"><span data-stu-id="f30ff-144">Next, in the main project of your app, you'll need to carry out the registration of this background task.</span></span> <span data-ttu-id="f30ff-145">Erstellen Sie eine Registrierungsmethode, die durch eine Benutzeraktion aufgerufen werden kann, oder jedes Mal aufgerufen wird, wenn die Klasse aktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="f30ff-145">Create a registering method that can be called by some user action or is called each time the class is activated.</span></span>

```csharp
// a reference to this registration should be declared at the class level
private IBackgroundTaskRegistration visitTask = null;

// The app must call this method at some point to allow future use of 
// the background task. 
private async void RegisterBackgroundTask(object sender, RoutedEventArgs e) {
    
    string taskName = "MyVisitTask";
    string taskEntryPoint = "Tasks.VisitBackgroundTask";

    // First check whether the task in question is already registered
    foreach (var task in BackgroundTaskRegistration.AllTasks) {
        if (task.Value.Name == taskName) {
            // if a task is found with the name of this app's background task, then
            // return and do not attempt to register this task
            return;
        }
    }
    
    // Attempt to register the background task.
    try {
        // Get permission for a background task from the user. If the user has 
        // already responded once, this does nothing and the user must manually 
        // update their preference via Settings.
        BackgroundAccessStatus backgroundAccessStatus = await BackgroundExecutionManager.RequestAccessAsync();

        switch (backgroundAccessStatus) {
            case BackgroundAccessStatus.AlwaysAllowed:
            case BackgroundAccessStatus.AllowedSubjectToSystemPolicy:
                // BackgroundTask is allowed
                break;

            default:
                // notify user that background tasks are disabled for this app
                //...
                break;
        }

        // Create a new background task builder
        BackgroundTaskBuilder visitTaskBuilder = new BackgroundTaskBuilder();

        visitTaskBuilder.Name = exampleTaskName;
        visitTaskBuilder.TaskEntryPoint = taskEntryPoint;

        // Create a new Visit trigger
        var trigger = new GeovisitTrigger();

        // Set the desired monitoring scope.
        // For higher granularity such as venue/building level changes, choose Venue.
        // For lower granularity in the range of zipcode level changes, choose City. 
        trigger.MonitoringScope = VisitMonitoringScope.Venue; 

        // Associate the trigger with the background task builder
        visitTaskBuilder.SetTrigger(trigger);

        // Register the background task
        visitTask = visitTaskBuilder.Register();      
    }
    catch (Exception ex) {
        // notify user that the task failed to register, using ex.ToString()
    }
}
```

<span data-ttu-id="f30ff-146">Dadurch wird festgelegt, dass eine Hintergrundaufgabenklasse mit dem Namen `VisitBackgroundTask` im Namespace `Tasks` eine Aktion mit dem `location`-Triggertyp durchführt.</span><span class="sxs-lookup"><span data-stu-id="f30ff-146">This establishes that a background task class called `VisitBackgroundTask` in the namespace `Tasks` will do something with the `location` trigger type.</span></span> 

<span data-ttu-id="f30ff-147">Ihre App sollte nun das Registrieren der Hintergrundaufgabe für Besuche behandeln können, und diese Aufgabe sollte aktiviert werden, sobald das Gerät eine Änderung im Zusammenhang mit einem Besuch protokolliert.</span><span class="sxs-lookup"><span data-stu-id="f30ff-147">Your app should now be capable of registering the Visits-handling background task, and this task should be activated whenever the device logs a Visit-related state change.</span></span> <span data-ttu-id="f30ff-148">Sie müssen die Logik in Ihrer Hintergrundaufgabenklasse ausfüllen, welche Aktion mit dieser Zustandsänderungsinformation ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="f30ff-148">You will need to fill in the logic in your background task class to determine what to do with this state change information.</span></span>

## <a name="related-topics"></a><span data-ttu-id="f30ff-149">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="f30ff-149">Related topics</span></span>
* [<span data-ttu-id="f30ff-150">Erstellen und Registrieren einer Hintergrundaufgabe außerhalb des Prozesses</span><span class="sxs-lookup"><span data-stu-id="f30ff-150">Create and register an out-of-process background task</span></span>](https://docs.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task)
* [<span data-ttu-id="f30ff-151">Abrufen der Position eines Benutzers</span><span class="sxs-lookup"><span data-stu-id="f30ff-151">Get the user's location</span></span>](get-location.md)
* [<span data-ttu-id="f30ff-152">Windows.Devices.Geolocation namespace</span><span class="sxs-lookup"><span data-stu-id="f30ff-152">Windows.Devices.Geolocation namespace</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.geolocation)