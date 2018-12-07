---
Description: Follow these best practices for geofencing in your app.
title: Richtlinien für Geofencing-Apps
ms.assetid: F817FA55-325F-4302-81BE-37E6C7ADC281
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Karte, Standort, Ort, Geofencing
ms.localizationpriority: medium
ms.openlocfilehash: e29bcdb8c36cc8cbbb5de11d669da1249e10d706
ms.sourcegitcommit: a3dc929858415b933943bba5aa7487ffa721899f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "8791185"
---
# <a name="guidelines-for-geofencing-apps"></a><span data-ttu-id="340df-103">Richtlinien für Geofencing-Apps</span><span class="sxs-lookup"><span data-stu-id="340df-103">Guidelines for geofencing apps</span></span>




**<span data-ttu-id="340df-104">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="340df-104">Important APIs</span></span>**

-   [**<span data-ttu-id="340df-105">Geofence-Klasse (XAML)</span><span class="sxs-lookup"><span data-stu-id="340df-105">Geofence class (XAML)</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn263587)
-   [**<span data-ttu-id="340df-106">Geolocator-Klasse (XAML)</span><span class="sxs-lookup"><span data-stu-id="340df-106">Geolocator class (XAML)</span></span>**](https://msdn.microsoft.com/library/windows/apps/br225534)

<span data-ttu-id="340df-107">Halten Sie sich bei der Verwendung von [**Geofencing**](https://msdn.microsoft.com/library/windows/apps/dn263744) in Ihrer App an die folgenden bewährten Methoden.</span><span class="sxs-lookup"><span data-stu-id="340df-107">Follow these best practices for [**geofencing**](https://msdn.microsoft.com/library/windows/apps/dn263744) in your app.</span></span>

## <a name="recommendations"></a><span data-ttu-id="340df-108">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="340df-108">Recommendations</span></span>


-   <span data-ttu-id="340df-109">Falls die App beim Eintreten eines [**Geofence**](https://msdn.microsoft.com/library/windows/apps/dn263587)-Ereignisses Internetzugriff benötigt, überprüfen Sie den Internetzugriff, bevor Sie den Geofence erstellen.</span><span class="sxs-lookup"><span data-stu-id="340df-109">If your app will need internet access when a [**Geofence**](https://msdn.microsoft.com/library/windows/apps/dn263587) event occurs, check for internet access before creating the geofence.</span></span>
    -   <span data-ttu-id="340df-110">Falls die App gerade nicht über Internetzugriff verfügt, können Sie Benutzer zum Herstellen einer Internetverbindung auffordern, bevor Sie den Geofence einrichten.</span><span class="sxs-lookup"><span data-stu-id="340df-110">If the app doesn't currently have internet access, you can prompt the user to connect to the internet before you set up the geofence.</span></span>
    -   <span data-ttu-id="340df-111">Falls kein Internetzugriff möglich ist, vermeiden Sie den Energieverbrauch, der für die Überprüfungen des Geofencing-Standorts anfällt.</span><span class="sxs-lookup"><span data-stu-id="340df-111">If internet access isn't possible, avoid consuming the power required for the geofencing location checks.</span></span>
-   <span data-ttu-id="340df-112">Stellen Sie die Relevanz der Geofencing-Benachrichtigungen sicher, indem Sie den Zeitstempel und den aktuellen Standort prüfen, wenn ein Geofence-Ereignis eine Änderung für einen [**Entered**](https://msdn.microsoft.com/library/windows/apps/dn263660)- oder **Exited**-Zustand anzeigt.</span><span class="sxs-lookup"><span data-stu-id="340df-112">Ensure the relevance of geofencing notifications by checking the time stamp and current location when a geofence event indicates changes to an [**Entered**](https://msdn.microsoft.com/library/windows/apps/dn263660) or **Exited** state.</span></span> <span data-ttu-id="340df-113">Weitere Informationen finden Sie weiter unten im Abschnitt **Überprüfen des Zeitstempels und aktuellen Standorts**.</span><span class="sxs-lookup"><span data-stu-id="340df-113">See **Checking the time stamp and current location** below for more information.</span></span>
<span data-ttu-id="340df-114">Weitere Informationen unter (#timestamp).</span><span class="sxs-lookup"><span data-stu-id="340df-114">(#timestamp) below for more information.</span></span>
-   <span data-ttu-id="340df-115">Ausnahmen für Fälle erstellen, wenn ein Gerät keinen Zugriff auf Standortinformationen hat, und ggf. den Benutzer benachrichtigen.</span><span class="sxs-lookup"><span data-stu-id="340df-115">Create exceptions to manage cases when a device can't access location info, and notify the user if necessary.</span></span> <span data-ttu-id="340df-116">Standortinformationen können aus verschiedenen Gründen nicht verfügbar sein, z.B. wenn die Berechtigungen deaktiviert sind, das Gerät keine GPS-Funkeinheit enthält, das GPS-Signal blockiert wird oder das WLAN-Signal nicht stark genug ist.</span><span class="sxs-lookup"><span data-stu-id="340df-116">Location info may be unavailable because permissions are turned off, the device doesn't contain a GPS radio, the GPS signal is blocked, or the Wi-Fi signal isn't strong enough.</span></span>
-   <span data-ttu-id="340df-117">Es ist im Allgemeinen nicht erforderlich, die Überwachung auf Geofence-Ereignisse sowohl im Vordergrund als auch im Hintergrund durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="340df-117">In general, it isn't necessary to listen for geofence events in the foreground and background at the same time.</span></span> <span data-ttu-id="340df-118">Wenn für Ihre App jedoch eine Überwachung auf Geofence-Ereignisse im Vordergrund und im Hintergrund erforderlich ist, empfehlen wir Folgendes:</span><span class="sxs-lookup"><span data-stu-id="340df-118">However, if your app needs to listen for geofence events in both the foreground and background:</span></span>

    -   <span data-ttu-id="340df-119">Rufen Sie die [**ReadReports**](https://msdn.microsoft.com/library/windows/apps/dn263633)-Methode auf, um zu prüfen, ob ein Ereignis eingetreten ist.</span><span class="sxs-lookup"><span data-stu-id="340df-119">Call the [**ReadReports**](https://msdn.microsoft.com/library/windows/apps/dn263633) method to find out if an event has occurred.</span></span>
    -   <span data-ttu-id="340df-120">Heben Sie die Registrierung des Ereignis-Listeners im Vordergrund jeweils auf, wenn die App für Benutzer nicht sichtbar ist, und registrieren Sie den Listener wieder, wenn die App wieder sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="340df-120">Unregister your foreground event listener when your app isn't visible to the user and re-register when it becomes visible again.</span></span>

    <span data-ttu-id="340df-121">Codebeispiele und weitere Informationen finden Sie unter [Listener im Hintergrund und Vordergrund](#background-and-foreground-listeners).</span><span class="sxs-lookup"><span data-stu-id="340df-121">See [Background and foreground listeners](#background-and-foreground-listeners) for code examples and more information.</span></span>

-   <span data-ttu-id="340df-122">Verwenden Sie pro App maximal 1000Geofence-Bereiche.</span><span class="sxs-lookup"><span data-stu-id="340df-122">Don't use more than 1000 geofences per app.</span></span> <span data-ttu-id="340df-123">Das System unterstützt zwar grundsätzlich mehrere tausend Geofence-Bereiche pro App, durch die Beschränkung auf maximal 1000Geofence-App können Sie jedoch die App-Leistung verbessern und den Speicherbedarf der App verringern.</span><span class="sxs-lookup"><span data-stu-id="340df-123">The system actually supports thousands of geofences per app, you can maintain good app performance to help reduce the app's memory usage by using no more than 1000.</span></span>
-   <span data-ttu-id="340df-124">Erstellen Sie keine Geofence-Bereiche mit einem Radius von weniger als 50Metern.</span><span class="sxs-lookup"><span data-stu-id="340df-124">Don't create a geofence with a radius smaller than 50 meters.</span></span> <span data-ttu-id="340df-125">Falls Ihre App Geofence-Bereiche mit kleinem Radius erfordert, empfehlen Sie Benutzern, die App auf einem Gerät mit GPS-Funkeinheit zu verwenden, um bestmögliche Ergebnisse zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="340df-125">If your app needs to use a geofence with a small radius, advise users to use your app on a device with a GPS radio to ensure the best performance.</span></span>

## <a name="additional-usage-guidance"></a><span data-ttu-id="340df-126">Weitere Hinweise zur Verwendung</span><span class="sxs-lookup"><span data-stu-id="340df-126">Additional usage guidance</span></span>

### <a name="checking-the-time-stamp-and-current-location"></a><span data-ttu-id="340df-127">Überprüfen des Zeitstempels und des aktuellen Standorts</span><span class="sxs-lookup"><span data-stu-id="340df-127">Checking the time stamp and current location</span></span>

<span data-ttu-id="340df-128">Wenn ein Ereignis eine Änderung für einen [**Entered**](https://msdn.microsoft.com/library/windows/apps/dn263660)- oder **Exited**-Zustand anzeigt, sollten Sie sowohl den Zeitstempel des Ereignisses als auch Ihren aktuellen Standort überprüfen.</span><span class="sxs-lookup"><span data-stu-id="340df-128">When an event indicates a change to an [**Entered**](https://msdn.microsoft.com/library/windows/apps/dn263660) or **Exited** state, check both the time stamp of the event and your current location.</span></span> <span data-ttu-id="340df-129">Wann das Ereignis letztendlich vom Benutzer verarbeitet wird, hängt von verschiedenen Faktoren ab, z.B. das Fehlen von Ressourcen zum Starten einer Hintergrundaufgabe, das Übersehen der Benachrichtigung durch den Benutzer oder das Gerät befindet sich im Standbymodus (unter Windows).</span><span class="sxs-lookup"><span data-stu-id="340df-129">Various factors, such as the system not having enough resources to launch a background task, the user not noticing the notification, or the device being in standby (on Windows), may affect when the event is actually processed by the user.</span></span> <span data-ttu-id="340df-130">Beispielsweise kann es zu folgendem Ablauf kommen:</span><span class="sxs-lookup"><span data-stu-id="340df-130">For example, the following sequence may occur:</span></span>

-   <span data-ttu-id="340df-131">Von der App wird ein Geofence erstellt und auf enter- und exit-Ereignisse überwacht.</span><span class="sxs-lookup"><span data-stu-id="340df-131">Your app creates a geofence and monitors the geofence for enter and exit events.</span></span>
-   <span data-ttu-id="340df-132">Der Benutzer bewegt sich mit dem Gerät in den Geofence-Bereich, sodass ein enter-Ereignis ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="340df-132">The user moves the device inside of the geofence, causing an enter event to be triggered.</span></span>
-   <span data-ttu-id="340df-133">Von der App wird eine Benachrichtigung an den Benutzer gesendet, dass er sich jetzt innerhalb des Geofence-Bereichs befindet.</span><span class="sxs-lookup"><span data-stu-id="340df-133">Your app sends a notification to the user that they are now inside the geofence.</span></span>
-   <span data-ttu-id="340df-134">Der Benutzer war beschäftigt und sieht die Benachrichtigung erst 10Minuten später.</span><span class="sxs-lookup"><span data-stu-id="340df-134">The user was busy and does not notice the notification until 10 minutes later.</span></span>
-   <span data-ttu-id="340df-135">Während dieser zehnminütigen Verzögerung hat sich der Benutzer wieder aus dem Geofence-Bereich herausbewegt.</span><span class="sxs-lookup"><span data-stu-id="340df-135">During that 10 minute delay, the user has moved back outside of the geofence.</span></span>

<span data-ttu-id="340df-136">Anhand des Zeitstempels können Sie erkennen, dass die Aktion in der Vergangenheit erfolgt ist.</span><span class="sxs-lookup"><span data-stu-id="340df-136">From the timestamp, you can tell that the action occurred in the past.</span></span> <span data-ttu-id="340df-137">Am aktuellen Standort kann abgelesen werden, dass sich der Benutzer wieder außerhalb des Geofence-Bereichs befindet.</span><span class="sxs-lookup"><span data-stu-id="340df-137">From the current location, you can see that the user is now back outside of the geofence.</span></span> <span data-ttu-id="340df-138">Je nach Funktion der App kann es ratsam sein, dieses Ereignis herauszufiltern.</span><span class="sxs-lookup"><span data-stu-id="340df-138">Depending on the functionality of your app, you may want to filter out this event.</span></span>

### <a name="background-and-foreground-listeners"></a><span data-ttu-id="340df-139">Listener im Hintergrund und Vordergrund</span><span class="sxs-lookup"><span data-stu-id="340df-139">Background and foreground listeners</span></span>

<span data-ttu-id="340df-140">Im Allgemeinen muss eine App nicht gleichzeitig im Vordergrund und Hintergrund eine Überwachung auf [**Geofence**](https://msdn.microsoft.com/library/windows/apps/dn263587)-Ereignisse durchführen.</span><span class="sxs-lookup"><span data-stu-id="340df-140">In general, your app doesn't need to listen for [**Geofence**](https://msdn.microsoft.com/library/windows/apps/dn263587) events both in the foreground and in a background task at the same time.</span></span> <span data-ttu-id="340df-141">Die sauberste Vorgehensweise zur Behandlung eines Falls, in dem beide erforderlich sind, ist die Behandlung der Benachrichtigungen durch die Hintergrundaufgabe.</span><span class="sxs-lookup"><span data-stu-id="340df-141">The cleanest method for handling a case where you might need both is to let the background task handle the notifications.</span></span> <span data-ttu-id="340df-142">Wenn Sie Geofencing-Listener sowohl im Vordergrund als auch im Hintergrund einrichten, kann nicht garantiert werden, welcher zuerst ausgelöst wird. Daher müssen Sie immer per Aufruf der [**ReadReports**](https://msdn.microsoft.com/library/windows/apps/dn263633)-Methode ermitteln, ob ein Ereignis eingetreten ist.</span><span class="sxs-lookup"><span data-stu-id="340df-142">If you do set up both foreground and background geofence listeners, there is no guarantee which will be triggered first and so you must always call the [**ReadReports**](https://msdn.microsoft.com/library/windows/apps/dn263633) method to find out if an event has occurred.</span></span>

<span data-ttu-id="340df-143">Wenn Sie Geofencing-Listener sowohl im Vordergrund als auch im Hintergrund eingerichtet haben, heben Sie die Registrierung für den Ereignislistener im Vordergrund jeweils auf, wenn die App für Benutzer nicht sichtbar ist, und registrieren Sie die App wieder, sobald sie wieder sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="340df-143">If you have set up both foreground and background geofence listeners, you should unregister your foreground event listener whenever your app is not visible to the user and re-register your app when it becomes visible again.</span></span> <span data-ttu-id="340df-144">Unten ist Beispielcode angegeben, mit dem die Registrierung für das visibility-Ereignis durchgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="340df-144">Here's some example code that registers for the visibility event.</span></span>

```csharp
    Windows.UI.Core.CoreWindow coreWindow;    

    // This needs to be set before InitializeComponent sets up event registration for app visibility
    coreWindow = CoreWindow.GetForCurrentThread();
    coreWindow.VisibilityChanged += OnVisibilityChanged;
```

```javascript
 document.addEventListener("visibilitychange", onVisibilityChanged, false);
```

<span data-ttu-id="340df-145">Wenn sich die Sichtbarkeit ändert, können Sie die Ereignishandler im Vordergrund wie hier gezeigt aktivieren oder deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="340df-145">When the visibility changes, you can then enable or disable the foreground event handlers as shown here.</span></span>

```csharp
private void OnVisibilityChanged(CoreWindow sender, VisibilityChangedEventArgs args)
{
    // NOTE: After the app is no longer visible on the screen and before the app is suspended
    // you might want your app to use toast notification for any geofence activity.
    // By registering for VisibiltyChanged the app is notified when the app is no longer visible in the foreground.

    if (args.Visible)
    {
        // register for foreground events
        GeofenceMonitor.Current.GeofenceStateChanged += OnGeofenceStateChanged;
        GeofenceMonitor.Current.StatusChanged += OnGeofenceStatusChanged;
    }
    else
    {
        // unregister foreground events (let background capture events)
        GeofenceMonitor.Current.GeofenceStateChanged -= OnGeofenceStateChanged;
        GeofenceMonitor.Current.StatusChanged -= OnGeofenceStatusChanged;
    }
}
```

```javascript
function onVisibilityChanged() {
    // NOTE: After the app is no longer visible on the screen and before the app is suspended
    // you might want your app to use toast notification for any geofence activity.
    // By registering for VisibiltyChanged the app is notified when the app is no longer visible in the foreground.

    if (document.msVisibilityState === "visible") {
        // register for foreground events
        Windows.Devices.Geolocation.Geofencing.GeofenceMonitor.current.addEventListener("geofencestatechanged", onGeofenceStateChanged);
        Windows.Devices.Geolocation.Geofencing.GeofenceMonitor.current.addEventListener("statuschanged", onGeofenceStatusChanged);
    } else {
        // unregister foreground events (let background capture events)
        Windows.Devices.Geolocation.Geofencing.GeofenceMonitor.current.removeEventListener("geofencestatechanged", onGeofenceStateChanged);
        Windows.Devices.Geolocation.Geofencing.GeofenceMonitor.current.removeEventListener("statuschanged", onGeofenceStatusChanged);
    }
}
```

### <a name="sizing-your-geofences"></a><span data-ttu-id="340df-146">Festlegen der Größe von Geofence-Bereichen</span><span class="sxs-lookup"><span data-stu-id="340df-146">Sizing your geofences</span></span>

<span data-ttu-id="340df-147">Per GPS können sehr genaue Informationen zum Standort bereitgestellt werden, aber für das Geofencing können auch WLAN- oder andere Standortsensoren genutzt werden, um die aktuelle Position von Benutzern zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="340df-147">While GPS can provide the most accurate location info, geofencing can also use Wi-Fi or other location sensors to determine the user's current position.</span></span> <span data-ttu-id="340df-148">Diese anderen Methoden können sich jedoch auf die Größe der Geofence-Bereiche auswirken, die Sie erstellen können.</span><span class="sxs-lookup"><span data-stu-id="340df-148">But using these other methods can affect the size of the geofences you can create.</span></span> <span data-ttu-id="340df-149">Wenn die Genauigkeit nicht ausreicht, ist das Erstellen von kleinen Geofence-Bereichen nicht sinnvoll.</span><span class="sxs-lookup"><span data-stu-id="340df-149">If the accuracy level is low, creating small geofences won't be useful.</span></span> <span data-ttu-id="340df-150">Allgemein empfiehlt es sich, nur Geofence-Bereiche mit einem Mindestradius von 50Metern zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="340df-150">In general, it is recommended that you do not create a geofence with a radius smaller than 50 meters.</span></span> <span data-ttu-id="340df-151">Bedenken Sie außerdem, dass Geofence-Hintergrundaufgaben unter Windows nur periodisch ausgeführt werden. Bei Verwendung eines kleinen Geofence-Bereichs besteht das Risiko, dass Sie ein [**Enter**](https://msdn.microsoft.com/library/windows/apps/dn263660)- oder ein **Exit**-Ereignis verpassen.</span><span class="sxs-lookup"><span data-stu-id="340df-151">Also, geofence background tasks only run periodically on Windows; if you use a small geofence, there's a possibility that you could miss an [**Enter**](https://msdn.microsoft.com/library/windows/apps/dn263660) or **Exit** event entirely.</span></span>

<span data-ttu-id="340df-152">Falls Ihre App Geofence-Bereiche mit kleinem Radius erfordert, empfehlen Sie Benutzern, die App auf einem Gerät mit GPS-Funkeinheit zu verwenden, um bestmögliche Ergebnisse zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="340df-152">If your app needs to use a geofence with a small radius, advise users to use your app on a device with a GPS radio to ensure the best performance.</span></span>

## <a name="related-topics"></a><span data-ttu-id="340df-153">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="340df-153">Related topics</span></span>


* [<span data-ttu-id="340df-154">Einrichten von Geofence-Bereichen</span><span class="sxs-lookup"><span data-stu-id="340df-154">Set up a geofence</span></span>](https://msdn.microsoft.com/library/windows/apps/mt219702)
* [<span data-ttu-id="340df-155">Abrufen der aktuellen Position</span><span class="sxs-lookup"><span data-stu-id="340df-155">Get current location</span></span>](https://msdn.microsoft.com/library/windows/apps/mt219698)
* [<span data-ttu-id="340df-156">UWP-Positionsbeispiel (Geolocation)</span><span class="sxs-lookup"><span data-stu-id="340df-156">UWP location sample (geolocation)</span></span>](http://go.microsoft.com/fwlink/p/?linkid=533278)
 

 
