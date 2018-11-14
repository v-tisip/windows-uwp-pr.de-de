---
author: PatrickFarley
title: Abrufen der Position eines Benutzers
description: Ermitteln Sie den Standort des Benutzers, und reagieren Sie auf Änderungen des Standorts. Der Zugriff auf die Position eines Benutzers wird über die Datenschutzeinstellungen in der Einstellungs-App verwaltet. In diesem Thema wird auch gezeigt, wie Sie überprüfen, ob Ihre App über die Berechtigung zum Zugriff auf den Benutzerstandort verfügt.
ms.assetid: 24DC9A41-8CC1-48B0-BC6D-24BF571AFCC8
ms.author: pafarley
ms.date: 11/28/2017
ms.topic: article
keywords: Windows10, UWP, Karte, Standort, Positionsfunktion
ms.localizationpriority: medium
ms.openlocfilehash: 2187bafa9fd2b4fdce049f3ef11d4e6766613de3
ms.sourcegitcommit: f2c9a050a9137a473f28b613968d5782866142c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "6249338"
---
# <a name="get-the-users-location"></a><span data-ttu-id="2e93d-106">Abrufen der Position eines Benutzers</span><span class="sxs-lookup"><span data-stu-id="2e93d-106">Get the user's location</span></span>




<span data-ttu-id="2e93d-107">Ermitteln Sie den Standort des Benutzers, und reagieren Sie auf Änderungen des Standorts.</span><span class="sxs-lookup"><span data-stu-id="2e93d-107">Find the user's location and respond to changes in location.</span></span> <span data-ttu-id="2e93d-108">Der Zugriff auf die Position eines Benutzers wird über die Datenschutzeinstellungen in der Einstellungs-App verwaltet.</span><span class="sxs-lookup"><span data-stu-id="2e93d-108">Access to the user's location is managed by privacy settings in the Settings app.</span></span> <span data-ttu-id="2e93d-109">In diesem Thema wird auch gezeigt, wie Sie überprüfen, ob Ihre App über die Berechtigung zum Zugriff auf den Benutzerstandort verfügt.</span><span class="sxs-lookup"><span data-stu-id="2e93d-109">This topic also shows how to check if your app has permission to access the user's location.</span></span>

<span data-ttu-id="2e93d-110">**Tipp** Um mehr über das Zugreifen auf den Benutzerstandort in Ihrer App zu erfahren, laden Sie das folgende Beispiel aus den [API-Beispielen für die Universelle Windows-Plattform](http://go.microsoft.com/fwlink/p/?LinkId=619979) auf GitHub herunter.</span><span class="sxs-lookup"><span data-stu-id="2e93d-110">**Tip** To learn more about accessing the user's location in your app, download the following sample from the [Windows-universal-samples repo](http://go.microsoft.com/fwlink/p/?LinkId=619979) on GitHub.</span></span>

-   [<span data-ttu-id="2e93d-111">Kartenbeispiel für die Universelle Windows-Plattform (UWP)</span><span class="sxs-lookup"><span data-stu-id="2e93d-111">Universal Windows Platform (UWP) map sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=619977)

## <a name="enable-the-location-capability"></a><span data-ttu-id="2e93d-112">Aktivieren der Positionsfunktion</span><span class="sxs-lookup"><span data-stu-id="2e93d-112">Enable the location capability</span></span>


1.  <span data-ttu-id="2e93d-113">Doppelklicken Sie im **Projektmappen-Explorer** auf **package.appxmanifest**, und wählen Sie die Registerkarte **Funktionen** aus.</span><span class="sxs-lookup"><span data-stu-id="2e93d-113">In **Solution Explorer**, double-click **package.appxmanifest** and select the **Capabilities** tab.</span></span>
2.  <span data-ttu-id="2e93d-114">Überprüfen Sie das Kontrollkästchen **Position** in der Liste **Funktionen**.</span><span class="sxs-lookup"><span data-stu-id="2e93d-114">In the **Capabilities** list, check the box for **Location**.</span></span> <span data-ttu-id="2e93d-115">Dadurch wird der Paketmanifestdatei die `location`-Gerätefunktion hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="2e93d-115">This adds the `location` device capability to the package manifest file.</span></span>

```XML
  <Capabilities>
    <!-- DeviceCapability elements must follow Capability elements (if present) -->
    <DeviceCapability Name="location"/>
  </Capabilities>
```

## <a name="get-the-current-location"></a><span data-ttu-id="2e93d-116">Abrufen der aktuellen Position</span><span class="sxs-lookup"><span data-stu-id="2e93d-116">Get the current location</span></span>


<span data-ttu-id="2e93d-117">In diesem Abschnitt erfahren Sie, wie Sie den geografische Standort eines Benutzers über APIs im [**Windows.Devices.Geolocation**](https://msdn.microsoft.com/library/windows/apps/br225603)-Namespace feststellen.</span><span class="sxs-lookup"><span data-stu-id="2e93d-117">This section describes how to detect the user's geographic location using APIs in the [**Windows.Devices.Geolocation**](https://msdn.microsoft.com/library/windows/apps/br225603) namespace.</span></span>

### <a name="step-1-request-access-to-the-users-location"></a><span data-ttu-id="2e93d-118">Schritt1: Anfordern des Zugriffs auf die Position des Benutzers</span><span class="sxs-lookup"><span data-stu-id="2e93d-118">Step 1: Request access to the user's location</span></span>

<span data-ttu-id="2e93d-119">Es sei denn, Ihre app grob Location-Funktion hat (siehe Hinweis), müssen Sie den Zugriff auf den Standort des Benutzers anfordern, mit der [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/dn859152) -Methode bevor Sie versuchen, auf die Position zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="2e93d-119">Unless your app has coarse location capability (see note), you must request access to the user's location by using the [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/dn859152) method before attempting to access the location.</span></span> <span data-ttu-id="2e93d-120">Sie müssen die **RequestAccessAsync**-Methode aus dem UI-Thread aufrufen, und die App muss sich im Vordergrund ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="2e93d-120">You must call the **RequestAccessAsync** method from the UI thread and your app must be in the foreground.</span></span> <span data-ttu-id="2e93d-121">Ihre App kann erst auf Positionsdaten des Benutzers zugreifen, nachdem der Benutzer der App den Zugriff gewährt hat.\*</span><span class="sxs-lookup"><span data-stu-id="2e93d-121">Your app will not be able to access the user's location information until after the user grants permission to your app.\*</span></span>

```csharp
using Windows.Devices.Geolocation;
...
var accessStatus = await Geolocator.RequestAccessAsync();
```



<span data-ttu-id="2e93d-122">Die [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/dn859152)-Methode fordert den Benutzer auf, den Zugriff auf seinen Standort zu genehmigen.</span><span class="sxs-lookup"><span data-stu-id="2e93d-122">The [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/dn859152) method prompts the user for permission to access their location.</span></span> <span data-ttu-id="2e93d-123">Der Benutzer wird nur einmal (pro App) aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="2e93d-123">The user is only prompted once (per app).</span></span> <span data-ttu-id="2e93d-124">Nachdem die Berechtigung erstmalig gewährt oder verweigert wurde, fordert die Methode keine Berechtigung mehr vom Benutzer an.</span><span class="sxs-lookup"><span data-stu-id="2e93d-124">After the first time they grant or deny permission, this method no longer prompts the user for permission.</span></span> <span data-ttu-id="2e93d-125">Um das Ändern von Standortberechtigungen nach der Aufforderung für den Benutzer zu vereinfachen, sollten Sie einen Link zu den Standorteinstellungen bereitstellen wie weiter unten in diesem Thema beschrieben.</span><span class="sxs-lookup"><span data-stu-id="2e93d-125">To help the user change location permissions after they've been prompted, we recommend that you provide a link to the location settings as demonstrated later in this topic.</span></span>

><span data-ttu-id="2e93d-126">Hinweis: Das Feature grob Speicherort kann Ihre app eine absichtlich verborgene (ungenaue) Position ohne Abrufen explizite Zustimmung des Benutzers (die systemweite Switch muss weiterhin **auf**, jedoch werden).</span><span class="sxs-lookup"><span data-stu-id="2e93d-126">Note:  The coarse location feature allows your app to obtain an intentionally obfuscated (imprecise) location without getting the user's explicit permission (the system-wide location switch must still be **on**, however).</span></span> <span data-ttu-id="2e93d-127">So nutzen Sie grob Stelle in Ihrer app finden Sie unter der [**AllowFallbackToConsentlessPositions**](https://msdn.microsoft.com/library/windows/apps/Windows.Devices.Geolocation.Geolocator.AllowFallbackToConsentlessPositions) -Methode in der [**Geolocator**](https://msdn.microsoft.com/library/windows/apps/windows.devices.geolocation.geolocator.aspx) -Klasse.</span><span class="sxs-lookup"><span data-stu-id="2e93d-127">To learn how to utilize coarse location in your app, see the [**AllowFallbackToConsentlessPositions**](https://msdn.microsoft.com/library/windows/apps/Windows.Devices.Geolocation.Geolocator.AllowFallbackToConsentlessPositions) method in the [**Geolocator**](https://msdn.microsoft.com/library/windows/apps/windows.devices.geolocation.geolocator.aspx) class.</span></span>

### <a name="step-2-get-the-users-location-and-register-for-changes-in-location-permissions"></a><span data-ttu-id="2e93d-128">Schritt2: Abrufen des Benutzerstandorts und Registrieren für Änderungen von Standortberechtigungen</span><span class="sxs-lookup"><span data-stu-id="2e93d-128">Step 2: Get the user's location and register for changes in location permissions</span></span>

<span data-ttu-id="2e93d-129">Die [**GetGeopositionAsync**](https://msdn.microsoft.com/library/windows/apps/hh973536)-Methode liest einmalig den aktuellen Standort.</span><span class="sxs-lookup"><span data-stu-id="2e93d-129">The [**GetGeopositionAsync**](https://msdn.microsoft.com/library/windows/apps/hh973536) method performs a one-time reading of the current location.</span></span> <span data-ttu-id="2e93d-130">Hier wird eine **switch**-Anweisung mit **accessStatus** (aus dem vorherigen Beispiel) verwendet, die nur aktiv ist, wenn der Zugriff auf den Standort des Benutzers zugelassen wird.</span><span class="sxs-lookup"><span data-stu-id="2e93d-130">Here, a **switch** statement is used with **accessStatus** (from the previous example) to act only when access to the user's location is allowed.</span></span> <span data-ttu-id="2e93d-131">Wenn der Zugriff auf die Position des Benutzers zugelassen wurde, erstellt der Code ein [**Geolocator**](https://msdn.microsoft.com/library/windows/apps/br225534)-Objekt, führt eine Registrierung für Änderungen von Standortberechtigungen aus und fordert den Standort des Benutzers an.</span><span class="sxs-lookup"><span data-stu-id="2e93d-131">If access to the user's location is allowed, the code creates a [**Geolocator**](https://msdn.microsoft.com/library/windows/apps/br225534) object, registers for changes in location permissions, and requests the user's location.</span></span>

```csharp
switch (accessStatus)
{
    case GeolocationAccessStatus.Allowed:
        _rootPage.NotifyUser("Waiting for update...", NotifyType.StatusMessage);

        // If DesiredAccuracy or DesiredAccuracyInMeters are not set (or value is 0), DesiredAccuracy.Default is used.
        Geolocator geolocator = new Geolocator { DesiredAccuracyInMeters = _desireAccuracyInMetersValue };

        // Subscribe to the StatusChanged event to get updates of location status changes.
        _geolocator.StatusChanged += OnStatusChanged;

        // Carry out the operation.
        Geoposition pos = await geolocator.GetGeopositionAsync();

        UpdateLocationData(pos);
        _rootPage.NotifyUser("Location updated.", NotifyType.StatusMessage);
        break;

    case GeolocationAccessStatus.Denied:
        _rootPage.NotifyUser("Access to location is denied.", NotifyType.ErrorMessage);
        LocationDisabledMessage.Visibility = Visibility.Visible;
        UpdateLocationData(null);
        break;

    case GeolocationAccessStatus.Unspecified:
        _rootPage.NotifyUser("Unspecified error.", NotifyType.ErrorMessage);
        UpdateLocationData(null);
        break;
}
```

### <a name="step-3-handle-changes-in-location-permissions"></a><span data-ttu-id="2e93d-132">Schritt 3: Behandeln von Änderungen von Standortberechtigungen</span><span class="sxs-lookup"><span data-stu-id="2e93d-132">Step 3: Handle changes in location permissions</span></span>

<span data-ttu-id="2e93d-133">Das [**Geolocator**](https://msdn.microsoft.com/library/windows/apps/br225534)-Objekt löst das [**StatusChanged**](https://msdn.microsoft.com/library/windows/apps/br225542)-Ereignis aus, um anzugeben, dass sich die Standorteinstellungen des Benutzers geändert haben.</span><span class="sxs-lookup"><span data-stu-id="2e93d-133">The [**Geolocator**](https://msdn.microsoft.com/library/windows/apps/br225534) object triggers the [**StatusChanged**](https://msdn.microsoft.com/library/windows/apps/br225542) event to indicate that the user's location settings changed.</span></span> <span data-ttu-id="2e93d-134">Das Ereignis übergibt den entsprechenden Status über die Eigenschaft **Status** des Arguments (des Typs [**PositionStatus**](https://msdn.microsoft.com/library/windows/apps/br225599).</span><span class="sxs-lookup"><span data-stu-id="2e93d-134">That event passes the corresponding status via the argument's **Status** property (of type [**PositionStatus**](https://msdn.microsoft.com/library/windows/apps/br225599)).</span></span> <span data-ttu-id="2e93d-135">Beachten Sie, dass diese Methode nicht vom UI-Thread aufgerufen wird und das [**Dispatcher**](https://msdn.microsoft.com/library/windows/apps/br208211)-Objekt die UI-Änderungen aufruft.</span><span class="sxs-lookup"><span data-stu-id="2e93d-135">Note that this method is not called from the UI thread and the [**Dispatcher**](https://msdn.microsoft.com/library/windows/apps/br208211) object invokes the UI changes.</span></span>

```csharp
using Windows.UI.Core;
...
async private void OnStatusChanged(Geolocator sender, StatusChangedEventArgs e)
{
    await Dispatcher.RunAsync(CoreDispatcherPriority.Normal, () =>
    {
        // Show the location setting message only if status is disabled.
        LocationDisabledMessage.Visibility = Visibility.Collapsed;

        switch (e.Status)
        {
            case PositionStatus.Ready:
                // Location platform is providing valid data.
                ScenarioOutput_Status.Text = "Ready";
                _rootPage.NotifyUser("Location platform is ready.", NotifyType.StatusMessage);
                break;

            case PositionStatus.Initializing:
                // Location platform is attempting to acquire a fix.
                ScenarioOutput_Status.Text = "Initializing";
                _rootPage.NotifyUser("Location platform is attempting to obtain a position.", NotifyType.StatusMessage);
                break;

            case PositionStatus.NoData:
                // Location platform could not obtain location data.
                ScenarioOutput_Status.Text = "No data";
                _rootPage.NotifyUser("Not able to determine the location.", NotifyType.ErrorMessage);
                break;

            case PositionStatus.Disabled:
                // The permission to access location data is denied by the user or other policies.
                ScenarioOutput_Status.Text = "Disabled";
                _rootPage.NotifyUser("Access to location is denied.", NotifyType.ErrorMessage);

                // Show message to the user to go to location settings.
                LocationDisabledMessage.Visibility = Visibility.Visible;

                // Clear any cached location data.
                UpdateLocationData(null);
                break;

            case PositionStatus.NotInitialized:
                // The location platform is not initialized. This indicates that the application
                // has not made a request for location data.
                ScenarioOutput_Status.Text = "Not initialized";
                _rootPage.NotifyUser("No request for location is made yet.", NotifyType.StatusMessage);
                break;

            case PositionStatus.NotAvailable:
                // The location platform is not available on this version of the OS.
                ScenarioOutput_Status.Text = "Not available";
                _rootPage.NotifyUser("Location is not available on this version of the OS.", NotifyType.ErrorMessage);
                break;

            default:
                ScenarioOutput_Status.Text = "Unknown";
                _rootPage.NotifyUser(string.Empty, NotifyType.StatusMessage);
                break;
        }
    });
}
```

## <a name="respond-to-location-updates"></a><span data-ttu-id="2e93d-136">Reagieren auf Standortupdates</span><span class="sxs-lookup"><span data-stu-id="2e93d-136">Respond to location updates</span></span>


<span data-ttu-id="2e93d-137">In diesem Abschnitt wird beschrieben, wie Sie mit dem [**PositionChanged**](https://msdn.microsoft.com/library/windows/apps/br225540)-Ereignis Standortupdates des Benutzers über einen bestimmten Zeitraum empfangen.</span><span class="sxs-lookup"><span data-stu-id="2e93d-137">This section describes how to use the [**PositionChanged**](https://msdn.microsoft.com/library/windows/apps/br225540) event to receive updates of the user's location over a period of time.</span></span> <span data-ttu-id="2e93d-138">Da der Benutzer den Zugriff auf den Standort jederzeit widerrufen kann, ist es wichtig, [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/dn859152) aufzurufen und das [**StatusChanged**](https://msdn.microsoft.com/library/windows/apps/br225542)-Ereignis zu verwenden wie im vorherigen Abschnitt dargestellt.</span><span class="sxs-lookup"><span data-stu-id="2e93d-138">Because the user could revoke access to location at any time, it's important call [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/dn859152) and use the [**StatusChanged**](https://msdn.microsoft.com/library/windows/apps/br225542) event as shown in the previous section.</span></span>

<span data-ttu-id="2e93d-139">In diesem Abschnitt wird vorausgesetzt, dass Sie die Standortfunktion bereits aktiviert und [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/dn859152) im UI-Thread der Vordergrund-App aufgerufen haben.</span><span class="sxs-lookup"><span data-stu-id="2e93d-139">This section assumes that you've already enabled the location capability and called [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/dn859152) from the UI thread of your foreground app.</span></span>

### <a name="step-1-define-the-report-interval-and-register-for-location-updates"></a><span data-ttu-id="2e93d-140">Schritt1: Definieren des Berichtsintervalls und Registrieren für Standortupdates</span><span class="sxs-lookup"><span data-stu-id="2e93d-140">Step 1: Define the report interval and register for location updates</span></span>

<span data-ttu-id="2e93d-141">In diesem Beispiel wird eine **switch**-Anweisung mit **accessStatus** (aus dem vorherigen Beispiel) verwendet, die nur aktiv ist, wenn der Zugriff auf den Standort eines Benutzers zugelassen wird.</span><span class="sxs-lookup"><span data-stu-id="2e93d-141">In this example, a **switch** statement is used with **accessStatus** (from the previous example) to act only when access to the user's location is allowed.</span></span> <span data-ttu-id="2e93d-142">Wenn der Zugriff auf den Standort des Benutzers zugelassen wurde, erstellt der Code ein [**Geolocator**](https://msdn.microsoft.com/library/windows/apps/br225534)-Objekt, gibt den Nachverfolgungstyp an und führt eine Registrierung für Standortupdates aus.</span><span class="sxs-lookup"><span data-stu-id="2e93d-142">If access to the user's location is allowed, the code creates a [**Geolocator**](https://msdn.microsoft.com/library/windows/apps/br225534) object, specifies the tracking type, and registers for location updates.</span></span>

<span data-ttu-id="2e93d-143">Das [**Geolocator**](https://msdn.microsoft.com/library/windows/apps/br225534)-Objekt kann das [**PositionChanged**](https://msdn.microsoft.com/library/windows/apps/br225540)-Ereignis basierend auf einer Standortänderung (entfernungsbasierte Nachverfolgung) oder Zeitänderung (zeitraumbasierte Nachverfolgung) auslösen.</span><span class="sxs-lookup"><span data-stu-id="2e93d-143">The [**Geolocator**](https://msdn.microsoft.com/library/windows/apps/br225534) object can trigger the [**PositionChanged**](https://msdn.microsoft.com/library/windows/apps/br225540) event based on a change in position (distance-based tracking) or a change in time (periodic-based tracking).</span></span>

-   <span data-ttu-id="2e93d-144">Für die entfernungsbasierte Nachverfolgung legen Sie die [**MovementThreshold**](https://msdn.microsoft.com/library/windows/apps/br225539)-Eigenschaft fest.</span><span class="sxs-lookup"><span data-stu-id="2e93d-144">For distance-based tracking, set the [**MovementThreshold**](https://msdn.microsoft.com/library/windows/apps/br225539) property.</span></span>
-   <span data-ttu-id="2e93d-145">Für die zeitraumbasierte Nachverfolgung legen Sie die [**ReportInterval**](https://msdn.microsoft.com/library/windows/apps/br225541)-Eigenschaft fest.</span><span class="sxs-lookup"><span data-stu-id="2e93d-145">For periodic-based tracking, set the [**ReportInterval**](https://msdn.microsoft.com/library/windows/apps/br225541) property.</span></span>

<span data-ttu-id="2e93d-146">Wenn keine der beiden Eigenschaften festgelegt wird, wird jede 1 Sekunde ein Standort zurückgegeben (entsprechend `ReportInterval = 1000`).</span><span class="sxs-lookup"><span data-stu-id="2e93d-146">If neither property is set, a position is returned every 1 second (equivalent to `ReportInterval = 1000`).</span></span> <span data-ttu-id="2e93d-147">Hier wird ein Berichtsintervall von 2 Sekunden (`ReportInterval = 2000`) verwendet.</span><span class="sxs-lookup"><span data-stu-id="2e93d-147">Here, a 2 second (`ReportInterval = 2000`) report interval is used.</span></span>
```csharp
using Windows.Devices.Geolocation;
...
var accessStatus = await Geolocator.RequestAccessAsync();

switch (accessStatus)
{
    case GeolocationAccessStatus.Allowed:
        // Create Geolocator and define perodic-based tracking (2 second interval).
        _geolocator = new Geolocator { ReportInterval = 2000 };

        // Subscribe to the PositionChanged event to get location updates.
        _geolocator.PositionChanged += OnPositionChanged;

        // Subscribe to StatusChanged event to get updates of location status changes.
        _geolocator.StatusChanged += OnStatusChanged;

        _rootPage.NotifyUser("Waiting for update...", NotifyType.StatusMessage);
        LocationDisabledMessage.Visibility = Visibility.Collapsed;
        StartTrackingButton.IsEnabled = false;
        StopTrackingButton.IsEnabled = true;
        break;

    case GeolocationAccessStatus.Denied:
        _rootPage.NotifyUser("Access to location is denied.", NotifyType.ErrorMessage);
        LocationDisabledMessage.Visibility = Visibility.Visible;
        break;

    case GeolocationAccessStatus.Unspecified:
        _rootPage.NotifyUser("Unspecificed error!", NotifyType.ErrorMessage);
        LocationDisabledMessage.Visibility = Visibility.Collapsed;
        break;
}
```

### <a name="step-2-handle-location-updates"></a><span data-ttu-id="2e93d-148">Schritt2: Behandeln von Standortupdates</span><span class="sxs-lookup"><span data-stu-id="2e93d-148">Step 2: Handle location updates</span></span>

<span data-ttu-id="2e93d-149">Das [**Geolocator**](https://msdn.microsoft.com/library/windows/apps/br225534)-Objekt löst das [**PositionChanged**](https://msdn.microsoft.com/library/windows/apps/br225540)-Ereignis aus, um anzugeben, dass sich der Benutzerstandort geändert hat bzw. dass Zeit vergangen ist, je nachdem, welche Eigenschaft Sie konfiguriert haben.</span><span class="sxs-lookup"><span data-stu-id="2e93d-149">The [**Geolocator**](https://msdn.microsoft.com/library/windows/apps/br225534) object triggers the [**PositionChanged**](https://msdn.microsoft.com/library/windows/apps/br225540) event to indicate that the user's location changed or time has passed, depending on how you've configured it.</span></span> <span data-ttu-id="2e93d-150">Dieses Ereignis übergibt den entsprechende Standort über die Eigenschaft **Position** des Arguments (des Typs [**Geoposition**](https://msdn.microsoft.com/library/windows/apps/br225543).</span><span class="sxs-lookup"><span data-stu-id="2e93d-150">That event passes the corresponding location via the argument's **Position** property (of type [**Geoposition**](https://msdn.microsoft.com/library/windows/apps/br225543)).</span></span> <span data-ttu-id="2e93d-151">In diesem Beispiel wird die Methode nicht vom UI-Thread aufgerufen. Die UI-Änderungen werden durch das [**Dispatcher**](https://msdn.microsoft.com/library/windows/apps/br208211)-Objekt aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="2e93d-151">In this example, the method is not called from the UI thread and the [**Dispatcher**](https://msdn.microsoft.com/library/windows/apps/br208211) object invokes the UI changes.</span></span>

```csharp
using Windows.UI.Core;
...
async private void OnPositionChanged(Geolocator sender, PositionChangedEventArgs e)
{
    await Dispatcher.RunAsync(CoreDispatcherPriority.Normal, () =>
    {
        _rootPage.NotifyUser("Location updated.", NotifyType.StatusMessage);
        UpdateLocationData(e.Position);
    });
}
```

## <a name="change-the-location-privacy-settings"></a><span data-ttu-id="2e93d-152">Ändern der Datenschutzeinstellungen für den Standort</span><span class="sxs-lookup"><span data-stu-id="2e93d-152">Change the location privacy settings</span></span>


<span data-ttu-id="2e93d-153">Wenn Ihre App gemäß den Standortdatenschutzeinstellungen nicht auf den Standort des Benutzers zugreifen darf, sollten Sie einen praktischen Link zu den **Standortdatenschutzeinstellungen** in der **Einstellungs**-App bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="2e93d-153">If the location privacy settings don't allow your app to access the user's location, we recommend that you provide a convenient link to the **location privacy settings** in the **Settings** app.</span></span> <span data-ttu-id="2e93d-154">In diesem Beispiel wird ein Hyperlink-Steuerelement verwendet, um zum `ms-settings:privacy-location`-URI zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="2e93d-154">In this example, a Hyperlink control is used navigate to the `ms-settings:privacy-location` URI.</span></span>

```xml
<!--Set Visibility to Visible when access to location is denied -->  
<TextBlock x:Name="LocationDisabledMessage" FontStyle="Italic"
                 Visibility="Collapsed" Margin="0,15,0,0" TextWrapping="Wrap" >
          <Run Text="This app is not able to access Location. Go to " />
              <Hyperlink NavigateUri="ms-settings:privacy-location">
                  <Run Text="Settings" />
              </Hyperlink>
          <Run Text=" to check the location privacy settings."/>
</TextBlock>
```

<span data-ttu-id="2e93d-155">Alternativ kann Ihre App die [**LaunchUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701476)-Methode aufrufen, um die **Einstellungs**-App per Code zu starten.</span><span class="sxs-lookup"><span data-stu-id="2e93d-155">Alternatively, your app can call the [**LaunchUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701476) method to launch the **Settings** app from code.</span></span> <span data-ttu-id="2e93d-156">Weitere Informationen finden Sie unter [Starten der Einstellungs-App von Windows](https://msdn.microsoft.com/library/windows/apps/mt228342).</span><span class="sxs-lookup"><span data-stu-id="2e93d-156">For more info, see [Launch the Windows Settings app](https://msdn.microsoft.com/library/windows/apps/mt228342).</span></span>

```csharp
using Windows.System;
...
bool result = await Launcher.LaunchUriAsync(new Uri("ms-settings:privacy-location"));
```

## <a name="troubleshoot-your-app"></a><span data-ttu-id="2e93d-157">Behandeln von App-Problemen</span><span class="sxs-lookup"><span data-stu-id="2e93d-157">Troubleshoot your app</span></span>


<span data-ttu-id="2e93d-158">Bevor Ihre App auf die Position des Benutzers zugreifen kann, muss **Position** auf dem Gerät aktiviert sein.</span><span class="sxs-lookup"><span data-stu-id="2e93d-158">Before your app can access the user's location, **Location** must be enabled on the device.</span></span> <span data-ttu-id="2e93d-159">Vergewissern Sie sich in der **Einstellungs**-App, dass die folgenden **Datenschutzeinstellungen für den Standort** aktiviert sind:</span><span class="sxs-lookup"><span data-stu-id="2e93d-159">In the **Settings** app, check that the following **location privacy settings** are turned on:</span></span>

-   <span data-ttu-id="2e93d-160">**Position dieses Geräts...** ist **aktiviert (gilt nicht für Windows 10 Mobile)**</span><span class="sxs-lookup"><span data-stu-id="2e93d-160">**Location for this device...** is turned **on** (not applicable in Windows10 Mobile)</span></span>
-   <span data-ttu-id="2e93d-161">Die Einstellung **Position** der Positionsdienste ist **aktiviert**.</span><span class="sxs-lookup"><span data-stu-id="2e93d-161">The location services setting, **Location**, is turned **on**</span></span>
-   <span data-ttu-id="2e93d-162">Ihre App hat unter **Wählen Sie Apps aus, die Ihre Position verwenden dürfen** die Einstellung **Ein**.</span><span class="sxs-lookup"><span data-stu-id="2e93d-162">Under **Choose apps that can use your location**, your app is set to **on**</span></span>

## <a name="related-topics"></a><span data-ttu-id="2e93d-163">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="2e93d-163">Related topics</span></span>

* [<span data-ttu-id="2e93d-164">UWP-Geolocation-Beispiel</span><span class="sxs-lookup"><span data-stu-id="2e93d-164">UWP geolocation sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=533278)
* [<span data-ttu-id="2e93d-165">Entwurfsrichtlinien für Geofencing</span><span class="sxs-lookup"><span data-stu-id="2e93d-165">Design guidelines for geofencing</span></span>](https://msdn.microsoft.com/library/windows/apps/dn631756)
* [<span data-ttu-id="2e93d-166">Entwurfsrichtlinien für Apps mit Positionsbestimmung</span><span class="sxs-lookup"><span data-stu-id="2e93d-166">Design guidelines for location-aware apps</span></span>](https://msdn.microsoft.com/library/windows/apps/hh465148)
