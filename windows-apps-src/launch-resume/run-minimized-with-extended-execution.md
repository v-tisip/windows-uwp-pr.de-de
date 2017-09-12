---
author: TylerMSFT
description: "Erfahren Sie, wie Sie die erweiterte Ausführung verwenden, damit Ihre App auch bei Minimierung weiter ausgeführt wird."
title: "Verschieben der angehaltenen App mithilfe der erweiterten Ausführung"
ms.author: twhitney
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "windows10, UWP, erweiterte Ausführung, minimiert, ExtendedExecutionSession, Hintergrundaufgabe, Anwendungslebenszyklus, Sperrbildschirm"
ms.assetid: e6a6a433-5550-4a19-83be-bbc6168fe03a
ms.openlocfilehash: f82fa37ade38d6a92fa1fec427079f75057a1a4a
ms.sourcegitcommit: e7e8de39e963b73ba95cb34d8049e35e8d5eca61
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2017
---
# <a name="postpone-app-suspension-with-extended-execution"></a><span data-ttu-id="3437a-104">Verschieben der angehaltenen App mithilfe der erweiterten Ausführung</span><span class="sxs-lookup"><span data-stu-id="3437a-104">Postpone app suspension with extended execution</span></span>

<span data-ttu-id="3437a-105">In diesem Artikel wird gezeigt, wie Sie mithilfe der erweiterten Ausführung das Anhalten Ihrer App verschieben können, damit sie auch bei Minimierung oder beim Sperrbildschirm weiter ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="3437a-105">This article shows you how to use extended execution to postpone when your app is suspended so that it can run while minimized or under the lock screen.</span></span>

<span data-ttu-id="3437a-106">Wenn der Benutzer eine App minimiert oder sie verlässt, wird sie in einen angehaltenen Zustand versetzt.</span><span class="sxs-lookup"><span data-stu-id="3437a-106">When the user minimizes or switches away from an app it is put into a suspended state.</span></span>  <span data-ttu-id="3437a-107">Der Arbeitsspeicher wird nicht gelöscht, der App-Code wird jedoch nicht ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="3437a-107">Its memory is maintained, but its code does not run.</span></span> <span data-ttu-id="3437a-108">Dies gilt für alle Betriebssystemeditionen mit einer grafischen Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="3437a-108">This is true across all OS Editions with a visual user interface.</span></span> <span data-ttu-id="3437a-109">Weitere Informationen zum Anhalten von Apps finden Sie unter [Anwendungslebenszyklus](app-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="3437a-109">For more details about when your app is suspended, see [Application Lifecycle](app-lifecycle.md).</span></span>

<span data-ttu-id="3437a-110">Es gibt Fälle, in denen eine App bei einer Minimierung möglicherweise weiter ausgeführt werden muss, statt angehalten zu werden.</span><span class="sxs-lookup"><span data-stu-id="3437a-110">There are cases where an app may need to keep running, rather than be suspended, while it is minimized.</span></span> <span data-ttu-id="3437a-111">Wenn eine App weiter ausgeführt muss, kann sie entweder vom Betriebssystem weiter ausgeführt werden, oder sie kann die weitere Ausführung anfordern.</span><span class="sxs-lookup"><span data-stu-id="3437a-111">If an app needs to keep running, either the OS can keep it running, or it can request to keep running.</span></span> <span data-ttu-id="3437a-112">Wenn beispielsweise im Hintergrund Audioinhalte wiedergegeben werden, kann das Betriebssystem eine App weiter ausführen, wenn Sie diese Schritte für [Medienwiedergabe im Hintergrund](../audio-video-camera/background-audio.md) ausführen.</span><span class="sxs-lookup"><span data-stu-id="3437a-112">For example, when playing audio in the background, the OS can keep an app running longer if you follow these steps for [Background Media Playback](../audio-video-camera/background-audio.md).</span></span> <span data-ttu-id="3437a-113">Andernfalls müssen Sie manuell mehr Zeit anfordern.</span><span class="sxs-lookup"><span data-stu-id="3437a-113">Otherwise, you must manually request more time.</span></span> <span data-ttu-id="3437a-114">Sie erhalten möglicherweise mehrere Minuten Zeit für die Ausführung im Hintergrund, aber Sie müssen jederzeit auf die Verarbeitung der widerrufenen Sitzung vorbereitet sein.</span><span class="sxs-lookup"><span data-stu-id="3437a-114">The amount of time you may get to perform background execution may be several minutes but you must be prepared to handle the session being revoked at any time.</span></span>

<span data-ttu-id="3437a-115">Um mehr Zeit für das Ausführen eines Vorgangs im Hintergrund anzufordern, erstellen Sie eine [ExtendedExecutionSession](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.extendedexecution.extendedexecutionsession.aspx).</span><span class="sxs-lookup"><span data-stu-id="3437a-115">Create an [ExtendedExecutionSession](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.extendedexecution.extendedexecutionsession.aspx) to request more time to complete an operation in the background.</span></span> <span data-ttu-id="3437a-116">Die Art der von Ihnen erstellten **ExtendedExecutionSession** wird durch den [ExtendedExecutionReason](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.extendedexecution.extendedexecutionreason.aspx) festgelegt, den Sie während des Erstellens angeben.</span><span class="sxs-lookup"><span data-stu-id="3437a-116">The kind of **ExtendedExecutionSession** you create is determined by the  [ExtendedExecutionReason](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.extendedexecution.extendedexecutionreason.aspx) that you provide when you create it.</span></span> <span data-ttu-id="3437a-117">Es gibt drei Enumerationswerte für **ExtendedExecutionReason**: **Unspecified, LocationTracking** und **SavingData**.</span><span class="sxs-lookup"><span data-stu-id="3437a-117">There are three **ExtendedExecutionReason** enum values: **Unspecified, LocationTracking** and **SavingData**.</span></span> <span data-ttu-id="3437a-118">Es kann nur eine **ExtendedExecutionSession** zu einem beliebigen Zeitpunkt angefordert werden. Wenn Sie versuchen, eine andere Sitzung zu erstellen, während eine derzeit aktiv ist, wird eine Ausnahme des **ExtendedExecutionSession**-Konstruktors hervorgerufen.</span><span class="sxs-lookup"><span data-stu-id="3437a-118">Only one **ExtendedExecutionSession** can be requested at any time; attempting to create another session while one is currently active will cause an exception to be thrown from the **ExtendedExecutionSession** constructor.</span></span> <span data-ttu-id="3437a-119">Verwenden Sie [ExtendedExecutionForegroundSession](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.extendedexecution.foreground.extendedexecutionforegroundsession.aspx) und [ExtendedExecutionForegroundReason](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.extendedexecution.foreground.extendedexecutionforegroundreason.aspx) nicht. Sie erfordern eingeschränkte Funktionen und sind nicht zur Verwendung in Store-Anwendungen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="3437a-119">Do not use [ExtendedExecutionForegroundSession](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.extendedexecution.foreground.extendedexecutionforegroundsession.aspx) and [ExtendedExecutionForegroundReason](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.extendedexecution.foreground.extendedexecutionforegroundreason.aspx); they require restricted capabilities and are not available for use in Store applications.</span></span>

## <a name="run-while-minimized"></a><span data-ttu-id="3437a-120">Ausführen bei Minimierung</span><span class="sxs-lookup"><span data-stu-id="3437a-120">Run while minimized</span></span>

<span data-ttu-id="3437a-121">Geben Sie **ExtendedExecutionReason.Unspecified** an, wenn Sie eine **ExtendedExecutionSession** erstellen, um zusätzliche Zeit anzufordern, bevor Ihre App in Szenarien wie Medienverarbeitung, Projektkompilierung oder Aufrechterhalten einer Netzwerkverbindung in den Hintergrund verschoben wird.</span><span class="sxs-lookup"><span data-stu-id="3437a-121">Specify **ExtendedExecutionReason.Unspecified** when you create an **ExtendedExecutionSession** to request additional time before your app moves into the background for scenarios such as media processing, project compilation, or keeping a network connection alive.</span></span> <span data-ttu-id="3437a-122">Auf Desktopgeräten, auf denen Windows10-Editionen für Desktops ausgeführt werden (Home, Pro, Enterprise und Education), verwenden Sie diesen Ansatz, um zu vermeiden, dass eine App bei Minimierung angehalten wird.</span><span class="sxs-lookup"><span data-stu-id="3437a-122">On desktop devices running Windows 10 for desktop editions (Home, Pro, Enterprise, and Education), this is the approach to use if an app needs to avoid being suspended while it is minimized.</span></span>

<span data-ttu-id="3437a-123">Sie fordern die Erweiterung an, wenn ein über lange Zeit ausgeführter Vorgang gestartet wird, um den Wechsel in den Zustand **Suspending** zu verschieben, der andernfalls beim Verschieben der App in den Hintergrund ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="3437a-123">Request the extension when starting a long running operation in order to defer the **Suspending** state transition that otherwise occurs when the app moves into the background.</span></span> <span data-ttu-id="3437a-124">Auf Desktopgeräten gibt es für mit **ExtendedExecutionReason.Unspecified** erstellte erweiterte Ausführungssitzungen eine akkubasierte zeitliche Begrenzung.</span><span class="sxs-lookup"><span data-stu-id="3437a-124">On desktop devices, extended execution sessions created with **ExtendedExecutionReason.Unspecified** have a battery-aware time limit.</span></span> <span data-ttu-id="3437a-125">Wenn das Gerät an eine Steckdose angeschlossen ist, gibt es keine zeitliche Begrenzung für die erweiterte Ausführung.</span><span class="sxs-lookup"><span data-stu-id="3437a-125">If the device is connected to wall power, there is no limit to the length of the extended execution time period.</span></span> <span data-ttu-id="3437a-126">Wenn das Gerät mit Akku betrieben wird, kann der Zeitraum für die erweiterte Ausführung im Hintergrund bis zu zehn Minuten betragen.</span><span class="sxs-lookup"><span data-stu-id="3437a-126">If the device is on battery power, the extended execution time period can run up to ten minutes in the background.</span></span> <span data-ttu-id="3437a-127">Tablet- oder Laptopbenutzer können auf Kosten der Akkulaufzeit den gleichen Zeitraum erhalten, wenn die Option **Immer zugelassen** in den **Akkunutzungseinstellungen** ausgewählt wird.</span><span class="sxs-lookup"><span data-stu-id="3437a-127">A tablet or laptop user can get the same long running behavior at the expense of battery life when the **Always Allowed** option is selected in **Battery Usage Settings**.</span></span>

<span data-ttu-id="3437a-128">Diese Art der erweiterten Ausführung wird auf allen Betriebssystemeditionen beendet, wenn das Gerät in den Zustand „Verbundener Standbymodus“ versetzt wird.</span><span class="sxs-lookup"><span data-stu-id="3437a-128">On all OS editions this kind of extended execution session stops when the device enters Connected Standby.</span></span> <span data-ttu-id="3437a-129">Auf mobilen Geräten mit Windows10 Mobile wird diese Art von erweiterter Ausführung solange ausgeführt, wie der Bildschirm aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="3437a-129">On mobile devices running Windows 10 Mobile, this kind of extended execution session will run as long as the screen is on.</span></span> <span data-ttu-id="3437a-130">Wenn der Bildschirm deaktiviert wird, versucht das Gerät sofort, in den energiesparenden Zustand „Verbundener Standbymodus“ zu wechseln.</span><span class="sxs-lookup"><span data-stu-id="3437a-130">When the screen turns off, the device immediately attempts to enter the low-power Connected-Standby mode.</span></span> <span data-ttu-id="3437a-131">Auf Desktopgeräten wird die Sitzung weiter ausgeführt, wenn der Sperrbildschirm angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="3437a-131">On desktop devices, the session will continue running if the lock screen appears.</span></span> <span data-ttu-id="3437a-132">Das Gerät wechselt nach Deaktivierung des Bildschirms für einen gewissen Zeitraum nicht in den Zustand „Verbundener Standbymodus“.</span><span class="sxs-lookup"><span data-stu-id="3437a-132">The device does not enter Connected Standby for a period of time after the screen turns off.</span></span> <span data-ttu-id="3437a-133">In der Xbox-Betriebssystemedition wechselt das Gerät nach einer Stunde in den Zustand „Verbundener Standbymodus“, wenn der Benutzer die Standardeinstellung nicht geändert hat.</span><span class="sxs-lookup"><span data-stu-id="3437a-133">On the Xbox OS Edition, the device enters Connect Standby after one hour unless the user changes the default.</span></span>

## <a name="track-the-users-location"></a><span data-ttu-id="3437a-134">Abrufen des Standorts eines Benutzers</span><span class="sxs-lookup"><span data-stu-id="3437a-134">Track the user's location</span></span>

<span data-ttu-id="3437a-135">Geben Sie beim Erstellen einer **ExtendedExecutionSession** **ExtendedExecutionReason.LocationTracking** an, wenn Ihre App regelmäßig den Standort aus [GeoLocator](https://msdn.microsoft.com/library/windows/apps/windows.devices.geolocation.geolocator.aspx) protokollieren muss.</span><span class="sxs-lookup"><span data-stu-id="3437a-135">Specify **ExtendedExecutionReason.LocationTracking** when you create an **ExtendedExecutionSession** if your app needs to regularly log the location from the [GeoLocator](https://msdn.microsoft.com/library/windows/apps/windows.devices.geolocation.geolocator.aspx).</span></span> <span data-ttu-id="3437a-136">Apps für Fitnessnachverfolgung und Navigation, die regelmäßig den Standort des Benutzers überwachen müssen, sollten diesen Grund verwenden.</span><span class="sxs-lookup"><span data-stu-id="3437a-136">Apps for fitness tracking and navigation that need to regularly monitor the user's location and should use this reason.</span></span>

<span data-ttu-id="3437a-137">Eine erweiterte Ausführungssitzung der Standortnachverfolgung kann bei Bedarf auch ausgeführt werden, während der Bildschirm auf einem mobilen Gerät gesperrt ist.</span><span class="sxs-lookup"><span data-stu-id="3437a-137">A location tracking extended execution session can run as long as needed, including while the screen is locked on a mobile device.</span></span> <span data-ttu-id="3437a-138">Pro Gerät kann jedoch nur eine solche Sitzung ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="3437a-138">However, there can only be one such session running per device.</span></span> <span data-ttu-id="3437a-139">Eine erweiterte Ausführung zur Standortnachverfolgung kann nur im Vordergrund angefordert werden, und die App muss sich im Zustand **Ausgeführt** befinden.</span><span class="sxs-lookup"><span data-stu-id="3437a-139">A location tracking extended execution session can only be requested in the foreground, and the app must be in the **Running** state.</span></span> <span data-ttu-id="3437a-140">Dadurch wird sichergestellt, dass der Benutzer weiß, dass die App die erweiterte Ausführung zur Standortnachverfolgung initiiert hat.</span><span class="sxs-lookup"><span data-stu-id="3437a-140">This ensures that the user is aware that the app has initiated an extended location tracking session.</span></span> <span data-ttu-id="3437a-141">GeoLocator kann mittels einer Hintergrundaufgabe oder eines App-Diensts während der Ausführung der App im Hintergrund weiter verwendet werden, ohne dass eine erweiterte Ausführung zur Standortnachverfolgung angefordert wird.</span><span class="sxs-lookup"><span data-stu-id="3437a-141">It is still possible to use the GeoLocator while the app is in the background by using a background task, or an app service, without requesting a location tracking extended execution session.</span></span>

## <a name="save-critical-data-locally"></a><span data-ttu-id="3437a-142">Lokales Speichern wichtiger Daten</span><span class="sxs-lookup"><span data-stu-id="3437a-142">Save Critical Data Locally</span></span>

<span data-ttu-id="3437a-143">Geben Sie beim Erstellen einer **ExtendedExecutionSession** **ExtendedExecutionReason.SavingData** an, wenn Sie in Fällen, in das Nichtspeichern von Daten vor Beenden der App zu Datenverlusten und einer negativen Benutzererfahrung führt, Benutzerdaten speichern möchten.</span><span class="sxs-lookup"><span data-stu-id="3437a-143">Specify **ExtendedExecutionReason.SavingData** when you create an **ExtendedExecutionSession** to save user data in the case where not saving the data before the app is terminated will result in data loss and a negative user experience.</span></span>

<span data-ttu-id="3437a-144">Verwenden Sie diese Art von Sitzung nicht, um den Lebenszyklus einer App zum Zweck des Hoch- oder Herunterladens von Daten zu verlängern.</span><span class="sxs-lookup"><span data-stu-id="3437a-144">Don't use this kind of session to extend the lifetime of an app to upload or download data.</span></span> <span data-ttu-id="3437a-145">Fordern Sie eine [Hintergrundübertragung](https://msdn.microsoft.com/windows/uwp/networking/background-transfers) an, wenn Sie Daten hochladen müssen, oder registrieren Sie einen **MaintenanceTrigger**, um die Übertragung zu verarbeiten, wenn die Stromversorgung verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="3437a-145">If you need to upload data, request a [background transfer](https://msdn.microsoft.com/windows/uwp/networking/background-transfers) or register a **MaintenanceTrigger** to handle the transfer when AC power is available.</span></span> <span data-ttu-id="3437a-146">Eine erweiterte Ausführungssitzung mit dem Grund **ExtendedExecutionReason.SavingData** kann angefordert werden, wenn sich die App im Vordergrund und im Zustand **Ausgeführt** befindet oder wenn sie sich im Hintergrund und im Zustand **Angehalten** befindet.</span><span class="sxs-lookup"><span data-stu-id="3437a-146">A **ExtendedExecutionReason.SavingData** extended execution session can be requested either when the app is in the foreground and in the **Running** state, or in the background and in the **Suspending** state.</span></span>

<span data-ttu-id="3437a-147">Der Zustand **Angehalten** ist die letzte Phase während des App-Lebenszyklus, in der die App Aufgaben ausführen kann, bevor sie beendet wird.</span><span class="sxs-lookup"><span data-stu-id="3437a-147">The **Suspending** state is the last opportunity during the app lifecycle that an app can do work before the app is terminated.</span></span> <span data-ttu-id="3437a-148">**ExtendedExecutionReason.SavingData** ist die einzige Art von **ExtendedExecutionSession**, die im **Suspending**-Zustand angefordert werden kann.</span><span class="sxs-lookup"><span data-stu-id="3437a-148">**ExtendedExecutionReason.SavingData** is the only type of **ExtendedExecutionSession** that can be requested in the **Suspending** state.</span></span> <span data-ttu-id="3437a-149">Das Anfordern einer erweiterten Ausführungssitzung mit dem Grund **ExtendedExecutionReason.SavingData**, während sich die App im Zustand **Angehalten** befindet, kann ein Problem verursachen, das Sie beachten sollten.</span><span class="sxs-lookup"><span data-stu-id="3437a-149">Requesting a **ExtendedExecutionReason.SavingData** extended execution session while the app is in the **Suspending** state creates a potential issue that you should be aware of.</span></span> <span data-ttu-id="3437a-150">Wenn im Zustand **Suspending** eine erweiterte Ausführungssitzung angefordert wird, und der Benutzer das erneute Starten der App anfordert, benötigt sie zum Starten scheinbar eine lange Zeit.</span><span class="sxs-lookup"><span data-stu-id="3437a-150">If an extended execution session is requested while in the **Suspending** state, and the user requests the app be launched again, it may appear to take a long time to launch.</span></span> <span data-ttu-id="3437a-151">Der Grund hierfür ist, dass die erweiterte Ausführungssitzung abgeschlossen werden muss, bevor die alte Instanz der App geschlossen und eine neue Instanz der App gestartet werden kann.</span><span class="sxs-lookup"><span data-stu-id="3437a-151">This is because the extended execution session time period must complete before the old instance of the app can be closed and a new instance of the app can be launched.</span></span> <span data-ttu-id="3437a-152">Es wird auf Leistung beim Starten verzichtet, um sicherzustellen, dass der Benutzerstatus nicht verloren geht.</span><span class="sxs-lookup"><span data-stu-id="3437a-152">Launch performance time is sacrificed in order to guarantee that user state is not lost.</span></span>

## <a name="request-disposal-and-revocation"></a><span data-ttu-id="3437a-153">Anfordern, Löschen und Sperren</span><span class="sxs-lookup"><span data-stu-id="3437a-153">Request, disposal, and revocation</span></span>

<span data-ttu-id="3437a-154">Es gibt drei grundsätzliche Interaktionen mit erweiterten Ausführungssitzungen: Anfordern, Löschen und Sperren.</span><span class="sxs-lookup"><span data-stu-id="3437a-154">There are three fundamental interactions with an extended execution session: the request, disposal, and revocation.</span></span>  <span data-ttu-id="3437a-155">Das Anfordern wird im folgenden Codeausschnitt gezeigt.</span><span class="sxs-lookup"><span data-stu-id="3437a-155">Making the request is modeled in the following code snippet.</span></span>

### <a name="request"></a><span data-ttu-id="3437a-156">Anfordern</span><span class="sxs-lookup"><span data-stu-id="3437a-156">Request</span></span>

```csharp
var newSession = new ExtendedExecutionSession();
newSession.Reason = ExtendedExecutionReason.Unspecified;
newSession.Revoked += SessionRevoked;
ExtendedExecutionResult result = await newSession.RequestExtensionAsync();

switch (result)
{
    case ExtendedExecutionResult.Allowed:
        DoLongRunningWork();
        break;

    default:
    case ExtendedExecutionResult.Denied:
        DoShortRunningWork();
        break;
}
```
[<span data-ttu-id="3437a-157">Siehe Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="3437a-157">See code sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/ExtendedExecution/cs/Scenario1_UnspecifiedReason.xaml.cs#L81-L110)  

<span data-ttu-id="3437a-158">Durch Aufrufen von **RequestExtensionAsync** wird durch das Betriebssystem geprüft, ob der Benutzer Hintergrundaktivitäten für die App genehmigt hat und ob das System über genügend Ressourcen verfügt, um die Hintergrundausführung zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="3437a-158">Calling **RequestExtensionAsync** checks with the operating system to see if the user has approved background activity for the app and whether the system has the available resources to enable background execution.</span></span>

<span data-ttu-id="3437a-159">Sie können [BackgroundExecutionManager](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.backgroundexecutionmanager.aspx) im Voraus überprüfen, um den [BackgroundAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.backgroundaccessstatus.aspx?f=255&MSPPError=-2147217396) zu ermitteln. Dies ist die Benutzereinstellung, die festlegt, ob Ihre App im Hintergrund ausgeführt werden kann oder nicht.</span><span class="sxs-lookup"><span data-stu-id="3437a-159">You can check the [BackgroundExecutionManager](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.backgroundexecutionmanager.aspx) beforehand to determine the [BackgroundAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.backgroundaccessstatus.aspx?f=255&MSPPError=-2147217396), which is the user setting that indicates whether your app can run in the background or not.</span></span> <span data-ttu-id="3437a-160">Weitere Informationen zu diesen Benutzereinstellungen finden Sie unter [Hintergrundaktivitäten und Energieinformationen](https://blogs.windows.com/buildingapps/2016/08/01/battery-awareness-and-background-activity/#XWK8mEgWD7JHvC10.97).</span><span class="sxs-lookup"><span data-stu-id="3437a-160">To learn more about these user settings see [Background Activity and Energy Awareness](https://blogs.windows.com/buildingapps/2016/08/01/battery-awareness-and-background-activity/#XWK8mEgWD7JHvC10.97).</span></span>

<span data-ttu-id="3437a-161">Der **ExtendedExecutionReason** gibt den Vorgang an, der von Ihrer App im Hintergrund ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="3437a-161">The **ExtendedExecutionReason** indicates the operation your app is performing in the background.</span></span> <span data-ttu-id="3437a-162">Die Zeichenfolge **Beschreibung** ist eine lesbare Zeichenfolge, die beschreibt, warum Ihre App den Vorgang ausführen muss.</span><span class="sxs-lookup"><span data-stu-id="3437a-162">The **Description** string is a human-readable string that explains why your app needs to perform the operation.</span></span> <span data-ttu-id="3437a-163">Der Ereignishandler **Revoked** ist erforderlich, damit eine erweiterte Ausführungssitzung ordnungsgemäß angehalten werden kann, wenn der Benutzer oder das System festlegen, dass die App nicht mehr im Hintergrund ausgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="3437a-163">The **Revoked** event handler is required so that an extended execution session can halt gracefully if the user, or the system, decides that the app can no longer run in the background.</span></span>

### <a name="revoked"></a><span data-ttu-id="3437a-164">Sperren</span><span class="sxs-lookup"><span data-stu-id="3437a-164">Revoked</span></span>

<span data-ttu-id="3437a-165">Wenn es für eine App eine aktive erweiterte Ausführungssitzung gibt, und das System Hintergrundaktivitäten anhalten muss, wird die Sitzung gesperrt.</span><span class="sxs-lookup"><span data-stu-id="3437a-165">If an app has an active extended execution session and the system requires background activity to halt, then the session is revoked.</span></span> <span data-ttu-id="3437a-166">Der Zeitraum für eine erweiterte Ausführungssitzung wird nie beendet, ohne dass zuerst der Ereignishandler **Revoked** aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="3437a-166">An extended execution session time period is never terminated without first firing the **Revoked** event handler.</span></span>

<span data-ttu-id="3437a-167">Wenn das Ereignis **Revoked** für eine erweiterte Ausführungssitzung mit dem Grund **ExtendedExecutionReason.SavingData** ausgelöst wird, hat die App nur eine Sekunde Zeit, um den gerade ausgeführten Vorgang abzuschließen und den Zustand **Angehalten** zu beenden.</span><span class="sxs-lookup"><span data-stu-id="3437a-167">When the **Revoked** event is fired for an **ExtendedExecutionReason.SavingData** extended execution session, the app has one second to complete the operation it was performing and finish **Suspending**.</span></span>

<span data-ttu-id="3437a-168">Das Sperren kann aus verschiedenen Gründen erfolgen: das Erreichen der zeitlichen Begrenzung für die Ausführung, das Erreichen der Begrenzung für den Energieverbrauch für Hintergrundaufgaben oder das notwendige Freigeben von Arbeitsspeicher, damit der Benutzer eine neue App im Vordergrund öffnen kann.</span><span class="sxs-lookup"><span data-stu-id="3437a-168">Revocation can occur for many reasons: an execution time limit was reached, a background energy quota was reached, or memory needs to be reclaimed in order for the user to open a new app in the foreground.</span></span>

<span data-ttu-id="3437a-169">Im Folgenden wird Ihnen ein Beispiel für den Ereignishandler „Revoked“ angezeigt:</span><span class="sxs-lookup"><span data-stu-id="3437a-169">Here is an example of a Revoked event handler:</span></span>

```cs
private async void SessionRevoked(object sender, ExtendedExecutionRevokedEventArgs args)
{
    await Dispatcher.RunAsync(CoreDispatcherPriority.Normal, () =>
    {
        switch (args.Reason)
        {
            case ExtendedExecutionRevokedReason.Resumed:
                rootPage.NotifyUser("Extended execution revoked due to returning to foreground.", NotifyType.StatusMessage);
                break;

            case ExtendedExecutionRevokedReason.SystemPolicy:
                rootPage.NotifyUser("Extended execution revoked due to system policy.", NotifyType.StatusMessage);
                break;
        }

        EndExtendedExecution();
    });
}
```
[<span data-ttu-id="3437a-170">Siehe Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="3437a-170">See code sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/ExtendedExecution/cs/Scenario1_UnspecifiedReason.xaml.cs#L124-L141)

### <a name="dispose"></a><span data-ttu-id="3437a-171">Löschen</span><span class="sxs-lookup"><span data-stu-id="3437a-171">Dispose</span></span>

<span data-ttu-id="3437a-172">Der letzte Schritt besteht im Löschen der erweiterten Ausführungssitzung.</span><span class="sxs-lookup"><span data-stu-id="3437a-172">The final step is to dispose of the extended execution session.</span></span> <span data-ttu-id="3437a-173">Sie sollten die Sitzung und alle weiteren, Arbeitsspeicher in Anspruch nehmenden Ressourcen löschen, da andernfalls die von der App beim Warten auf das Beenden der Sitzung verbrauchte Energie auf das Energiekontingent der App angerechnet wird.</span><span class="sxs-lookup"><span data-stu-id="3437a-173">You want to dispose of the session, and any other memory intensive assets, because otherwise the energy used by the app while it is waiting for the session to close will be counted against the app's energy quota.</span></span> <span data-ttu-id="3437a-174">Um einen möglichst großen Teil des Energiekontingents der App zu bewahren, ist es wichtig, die Sitzung zu löschen, wenn sie nicht mehr benötigt wird, damit die App schneller in den Zustand **Angehalten** wechseln kann.</span><span class="sxs-lookup"><span data-stu-id="3437a-174">To preserve as much of the energy quota for the app as possible, it is important to dispose of the session when you are done with your work for the session so that the app can move into the **Suspended** state more quickly.</span></span>

<span data-ttu-id="3437a-175">Wenn Sie die Sitzung selbst löschen, statt auf das Sperrereignis zu warten, wird die Energiekontingentnutzung Ihrer App reduziert.</span><span class="sxs-lookup"><span data-stu-id="3437a-175">Disposing of the session yourself, rather than waiting for the revocation event, reduces your app's energy quota usage.</span></span> <span data-ttu-id="3437a-176">Das bedeutet, dass Ihre App zukünftig länger im Hintergrund ausgeführt werden darf, da ihr hierfür ein größeres Energiekontingent zur Verfügung steht.</span><span class="sxs-lookup"><span data-stu-id="3437a-176">This means that your app will be permitted to run in the background longer in future sessions because you'll have more energy quota available to do so.</span></span> <span data-ttu-id="3437a-177">Sie müssen bis zum Abschluss des Vorgangs einen Verweis auf das Objekt **ExtendedExecutionSession** beibehalten, damit Sie dessen Methode **Dispose** aufrufen können.</span><span class="sxs-lookup"><span data-stu-id="3437a-177">You must maintain a reference to the **ExtendedExecutionSession** object until the end of the operation so that you can call its **Dispose** method.</span></span>

<span data-ttu-id="3437a-178">Im Folgenden wird ein Codeausschnitt angezeigt, in dem eine erweiterte Ausführungssitzung gelöscht wird:</span><span class="sxs-lookup"><span data-stu-id="3437a-178">A snippet that disposes an extended execution session follows:</span></span>

```cs
void ClearExtendedExecution(ExtendedExecutionSession session)
{
    if (session != null)
    {
        session.Revoked -= SessionRevoked;
        session.Dispose();
        session = null;
    }
}
```
[<span data-ttu-id="3437a-179">Siehe Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="3437a-179">See code sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/ExtendedExecution/cs/Scenario1_UnspecifiedReason.xaml.cs#L49-L63)

<span data-ttu-id="3437a-180">Für eine App kann jeweils nur eine **ExtendedExecutionSession** aktiv sein.</span><span class="sxs-lookup"><span data-stu-id="3437a-180">An app can only have one **ExtendedExecutionSession** active at a time.</span></span> <span data-ttu-id="3437a-181">Viele Apps verwenden asynchrone Aufgaben, um komplexe Vorgänge ausführen, die Zugriff auf Ressourcen wie Speicher, Netzwerk oder netzwerkbasierte Dienste erfordern.</span><span class="sxs-lookup"><span data-stu-id="3437a-181">Many apps use asynchronous tasks in order to complete complex operations that require access to resources such as storage, network, or network-based services.</span></span> <span data-ttu-id="3437a-182">Wenn ein Vorgang mehrere asynchrone Vorgänge erfordert, um abgeschlossen zu werden, muss der Zustand jeder dieser Aufgaben berücksichtigt werden, bevor **ExtendedExecutionSession** gelöscht wird und die App angehalten werden kann.</span><span class="sxs-lookup"><span data-stu-id="3437a-182">If an operation requires multiple asynchronous tasks to complete, then the state of each of these tasks must be accounted for before disposing the **ExtendedExecutionSession** and allowing the app to be suspended.</span></span> <span data-ttu-id="3437a-183">Dies erfordert eine Verweiszählung der Anzahl der Aufgaben, die weiter ausgeführt werden. Erst wenn dieser Wert null erreicht, kann die Sitzung gelöscht werden.</span><span class="sxs-lookup"><span data-stu-id="3437a-183">This requires reference counting the number of tasks that are still running, and not disposing of the session until that value reaches zero.</span></span>

<span data-ttu-id="3437a-184">Im Folgenden wird ein Beispielcode für das Verwalten mehrerer Aufgaben während einer erweiterten Ausführungssitzung angezeigt:</span><span class="sxs-lookup"><span data-stu-id="3437a-184">Here is some example code for managing multiple tasks during an extended execution session period:</span></span>

```cs
static class ExtendedExecutionHelper
{
    private static ExtendedExecutionSession session = null;
    private static int taskCount = 0;

    public static bool IsRunning
    {
        get
        {
            if (session != null)
            {
                return true;
            }
            else
            {
                return false;
            }
        }
    }

    public static async Task<ExtendedExecutionResult> RequestSessionAsync(ExtendedExecutionReason reason, TypedEventHandler<object, ExtendedExecutionRevokedEventArgs> revoked)
    {
        // The previous Extended Execution must be closed before a new one can be requested.       
        ClearSession();

        var newSession = new ExtendedExecutionSession();
        newSession.Reason = ExtendedExecutionReason.Unspecified;
        newSession.Revoked += SessionRevoked;

        if(revoked != null)
        {
            newSession.Revoked += revoked;
        }

        ExtendedExecutionResult result = await newSession.RequestExtensionAsync();

        switch (result)
        {
            case ExtendedExecutionResult.Allowed:
                session = newSession;
                break;
            default:
            case ExtendedExecutionResult.Denied:
                newSession.Dispose();
                break;
        }
        return result;
    }

    public static void ClearSession()
    {
        if (session != null)
        {
            session.Dispose();
            session = null;
        }

        taskCount = 0;
    }

    public static Deferral GetExecutionDeferral()
    {
        if (session == null)
        {
            throw new InvalidOperationException("No extended execution session is active");
        }

        taskCount++;
        return new Deferral(OnTaskCompleted);
    }

    private static void OnTaskCompleted()
    {
        if (taskCount > 0)
        {
            taskCount--;
        }
        else if (taskCount == 0 && session != null)
        {
            ClearSession();
        }
    }

    private static void SessionRevoked(object sender, ExtendedExecutionRevokedEventArgs args)
    {
        if (session != null)
        {
            session.Dispose();
            session = null;
        }
    }
}
```
[<span data-ttu-id="3437a-185">Siehe Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="3437a-185">See code sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/ExtendedExecution/cs/Scenario4_MultipleTasks.xaml.cs)

## <a name="ensure-that-your-app-uses-resources-well"></a><span data-ttu-id="3437a-186">Gute Nutzung von Ressourcen durch Ihre App</span><span class="sxs-lookup"><span data-stu-id="3437a-186">Ensure that your app uses resources well</span></span>

<span data-ttu-id="3437a-187">Das Optimieren von Arbeitsspeicher und Energieverbrauch Ihrer App ist der Schlüssel, um sicherzustellen, dass das Betriebssystem die Ausführung Ihrer App auch dann zulässt, wenn sie sich nicht mehr im Vordergrund befindet.</span><span class="sxs-lookup"><span data-stu-id="3437a-187">Tuning your app's memory and energy use is key to ensuring that the operating system will allow your app to continue to run when it is no longer the foreground app.</span></span> <span data-ttu-id="3437a-188">Um zu ermitteln, wie viel Arbeitsspeicher Ihre App verwendet, verwenden Sie die [Speicherverwaltungs-APIs](https://msdn.microsoft.com/library/windows/apps/windows.system.memorymanager.aspx).</span><span class="sxs-lookup"><span data-stu-id="3437a-188">Use the [Memory Management APIs](https://msdn.microsoft.com/library/windows/apps/windows.system.memorymanager.aspx) to see how much memory your app is using.</span></span> <span data-ttu-id="3437a-189">Je mehr Arbeitsspeicher Ihre App verwendet, desto schwieriger wird es für das Betriebssystem, Ihre App weiter auszuführen, wenn sich eine andere App im Vordergrund befindet.</span><span class="sxs-lookup"><span data-stu-id="3437a-189">The more memory your app uses, the harder it is for the OS to keep your app running when another app is in the foreground.</span></span> <span data-ttu-id="3437a-190">Der Benutzer hat letztendlich die Kontrolle über alle Hintergrundaktivitäten, die Ihre App ausführen kann, und kann die Auswirkungen Ihrer App auf den Akkuverbrauch erkennen.</span><span class="sxs-lookup"><span data-stu-id="3437a-190">The user is ultimately in control of all background activity that your app can perform and has visibility on the impact your app has on battery use.</span></span>

<span data-ttu-id="3437a-191">Um zu ermitteln, ob der Benutzer die Hintergrundaktivität Ihrer App begrenzt hat, verwenden Sie [BackgroundExecutionManager.RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.backgroundexecutionmanager.aspx).</span><span class="sxs-lookup"><span data-stu-id="3437a-191">Use [BackgroundExecutionManager.RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.backgroundexecutionmanager.aspx) to determine if the user has decided that your app’s background activity should be limited.</span></span> <span data-ttu-id="3437a-192">Achten Sie auf die Akkunutzung, und führen Sie Ihre App nur dann im Hintergrund aus, wenn dies zum Ausführen einer vom Benutzer gewünschten Aktion notwendig ist.</span><span class="sxs-lookup"><span data-stu-id="3437a-192">Be aware of your battery usage and only run in the background when it is necessary to complete an action that the user wants.</span></span>

## <a name="see-also"></a><span data-ttu-id="3437a-193">Weitere Informationen finden Sie unter</span><span class="sxs-lookup"><span data-stu-id="3437a-193">See also</span></span>

[<span data-ttu-id="3437a-194">Beispiel für die erweiterte Ausführung</span><span class="sxs-lookup"><span data-stu-id="3437a-194">Extended Execution Sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/ExtendedExecution)  
[<span data-ttu-id="3437a-195">Anwendungslebenszyklus</span><span class="sxs-lookup"><span data-stu-id="3437a-195">Application Lifecycle</span></span>](https://msdn.microsoft.com/windows/uwp/launch-resume/app-lifecycle)  
[<span data-ttu-id="3437a-196">Hintergrundspeicherverwaltung</span><span class="sxs-lookup"><span data-stu-id="3437a-196">Background Memory Management</span></span>](https://msdn.microsoft.com/windows/uwp/launch-resume/reduce-memory-usage)  
[<span data-ttu-id="3437a-197">Hintergrundübertragungen</span><span class="sxs-lookup"><span data-stu-id="3437a-197">Background Transfers</span></span>](https://msdn.microsoft.com/windows/uwp/networking/background-transfers)  
[<span data-ttu-id="3437a-198">Akkuinformationen und Hintergrundaktivität</span><span class="sxs-lookup"><span data-stu-id="3437a-198">Battery Awareness and Background Activity</span></span>](https://blogs.windows.com/buildingapps/2016/08/01/battery-awareness-and-background-activity/#I2bkQ6861TRpbRjr.97)  
[<span data-ttu-id="3437a-199">MemoryManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="3437a-199">MemoryManager class</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.system.memorymanager.aspx)  
[<span data-ttu-id="3437a-200">Wiedergeben von Medien im Hintergrund</span><span class="sxs-lookup"><span data-stu-id="3437a-200">Play Media in the Background</span></span>](https://msdn.microsoft.com/windows/uwp/audio-video-camera/background-audio)  
