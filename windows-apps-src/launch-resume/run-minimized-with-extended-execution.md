---
description: Erfahren Sie, wie Sie die erweiterte Ausführung verwenden, damit Ihre App auch bei Minimierung weiter ausgeführt wird.
title: Verschieben der angehaltenen App mithilfe der erweiterten Ausführung
ms.date: 02/08/2017
ms.topic: article
keywords: windows10, UWP, erweiterte Ausführung, minimiert, ExtendedExecutionSession, Hintergrundaufgabe, Anwendungslebenszyklus, Sperrbildschirm
ms.assetid: e6a6a433-5550-4a19-83be-bbc6168fe03a
ms.localizationpriority: medium
ms.openlocfilehash: 8cc67a7593a340ada8f807fc0fb0c1b846c6f05b
ms.sourcegitcommit: 89ff8ff88ef58f4fe6d3b1368fe94f62e59118ad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "8215912"
---
# <a name="postpone-app-suspension-with-extended-execution"></a><span data-ttu-id="8a377-104">Verschieben der angehaltenen App mithilfe der erweiterten Ausführung</span><span class="sxs-lookup"><span data-stu-id="8a377-104">Postpone app suspension with extended execution</span></span>

<span data-ttu-id="8a377-105">In diesem Artikel wird gezeigt, wie Sie mithilfe der erweiterten Ausführung das Anhalten Ihrer App verschieben können, damit sie auch bei Minimierung oder beim Sperrbildschirm weiter ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="8a377-105">This article shows you how to use extended execution to postpone when your app is suspended so that it can run while minimized or under the lock screen.</span></span>

<span data-ttu-id="8a377-106">Wenn der Benutzer eine App minimiert oder sie verlässt, wird sie in einen angehaltenen Zustand versetzt.</span><span class="sxs-lookup"><span data-stu-id="8a377-106">When the user minimizes or switches away from an app it is put into a suspended state.</span></span>  <span data-ttu-id="8a377-107">Der Arbeitsspeicher wird nicht gelöscht, der App-Code wird jedoch nicht ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="8a377-107">Its memory is maintained, but its code does not run.</span></span> <span data-ttu-id="8a377-108">Dies gilt für alle Betriebssystemeditionen mit einer grafischen Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="8a377-108">This is true across all OS Editions with a visual user interface.</span></span> <span data-ttu-id="8a377-109">Weitere Informationen zum Anhalten von Apps finden Sie unter [Anwendungslebenszyklus](app-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="8a377-109">For more details about when your app is suspended, see [Application Lifecycle](app-lifecycle.md).</span></span> 

<span data-ttu-id="8a377-110">Es gibt Fälle, in denen eine App bei einer Minimierung möglicherweise weiter ausgeführt werden muss, statt angehalten zu werden, beispielsweise wenn der Benutzer die App wechselt oder diese minimiert wird.</span><span class="sxs-lookup"><span data-stu-id="8a377-110">There are cases where an app may need to keep running, rather than be suspended, when the user navigates away from the app, or while it is minimized.</span></span> <span data-ttu-id="8a377-111">Zum Beispiel muss eine App zur Schrittzählung weiterhin ausgeführt werden, auch wenn der Benutzer eine andere App öffnet.</span><span class="sxs-lookup"><span data-stu-id="8a377-111">For example, a step counting app needs to keep running and tracking steps even when the user navigates away to use other apps.</span></span> 

<span data-ttu-id="8a377-112">Wenn eine App weiter ausgeführt muss, kann sie entweder vom Betriebssystem weiter ausgeführt werden, oder sie kann die weitere Ausführung anfordern.</span><span class="sxs-lookup"><span data-stu-id="8a377-112">If an app needs to keep running, either the OS can keep it running, or it can request to keep running.</span></span> <span data-ttu-id="8a377-113">Wenn beispielsweise im Hintergrund Audioinhalte wiedergegeben werden, kann das Betriebssystem eine App weiter ausführen, wenn Sie diese Schritte für [Medienwiedergabe im Hintergrund](../audio-video-camera/background-audio.md) ausführen.</span><span class="sxs-lookup"><span data-stu-id="8a377-113">For example, when playing audio in the background, the OS can keep an app running longer if you follow these steps for [Background Media Playback](../audio-video-camera/background-audio.md).</span></span> <span data-ttu-id="8a377-114">Andernfalls müssen Sie manuell mehr Zeit anfordern.</span><span class="sxs-lookup"><span data-stu-id="8a377-114">Otherwise, you must manually request more time.</span></span> <span data-ttu-id="8a377-115">Sie erhalten möglicherweise mehrere Minuten Zeit für die Ausführung im Hintergrund, aber Sie müssen jederzeit auf die Verarbeitung der widerrufenen Sitzung vorbereitet sein.</span><span class="sxs-lookup"><span data-stu-id="8a377-115">The amount of time you may get to perform background execution may be several minutes but you must be prepared to handle the session being revoked at any time.</span></span> <span data-ttu-id="8a377-116">Diese Einschränkungen für die Lebenszykluszeit einer Anwendung sind deaktiviert, während sie unter einem Debugger ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="8a377-116">These application lifecycle time constraints are disabled while the app is running under a debugger.</span></span> <span data-ttu-id="8a377-117">Aus diesem Grund ist es wichtig, Extended Execution und andere Tools zum Verschieben von App-Aussetzungen nur zu testen, wenn die App nicht unter einem Debugger ausgeführt wird, oder die in Visual Studio verfügbaren Lifecycle Events zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="8a377-117">For this reason it is important to test Extended Execution and other tools for postponing app suspension while not running under a debugger or by using the Lifecycle Events available in Visual Studio.</span></span> 
 
<span data-ttu-id="8a377-118">Um mehr Zeit für das Ausführen eines Vorgangs im Hintergrund anzufordern, erstellen Sie eine [ExtendedExecutionSession](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.extendedexecution.extendedexecutionsession.aspx).</span><span class="sxs-lookup"><span data-stu-id="8a377-118">Create an [ExtendedExecutionSession](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.extendedexecution.extendedexecutionsession.aspx) to request more time to complete an operation in the background.</span></span> <span data-ttu-id="8a377-119">Die Art der von Ihnen erstellten **ExtendedExecutionSession** wird durch den [ExtendedExecutionReason](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.extendedexecution.extendedexecutionreason.aspx) festgelegt, den Sie während des Erstellens angeben.</span><span class="sxs-lookup"><span data-stu-id="8a377-119">The kind of **ExtendedExecutionSession** you create is determined by the  [ExtendedExecutionReason](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.extendedexecution.extendedexecutionreason.aspx) that you provide when you create it.</span></span> <span data-ttu-id="8a377-120">Es gibt drei Enumerationswerte für **ExtendedExecutionReason**: **Unspecified, LocationTracking** und **SavingData**.</span><span class="sxs-lookup"><span data-stu-id="8a377-120">There are three **ExtendedExecutionReason** enum values: **Unspecified, LocationTracking** and **SavingData**.</span></span> <span data-ttu-id="8a377-121">Es kann jeweils nur eine **ExtendedExecutionSession** angefordert werden. Wenn Sie versuchen, eine neue Sitzung zu erstellen, während eine genehmigte Sitzungsanforderung aktiv ist, wird die Ausnahme 0x8007139F vom **ExtendedExecutionSession**-Konstruktor ausgelöst, die besagt, dass die Gruppe oder Ressource nicht den richtigen Status zum Ausführen der angeforderten Operation aufweist.</span><span class="sxs-lookup"><span data-stu-id="8a377-121">Only one **ExtendedExecutionSession** can be requested at any time; attempting to create another session while an approved session request is currently active will cause exception 0x8007139F to be thrown from the **ExtendedExecutionSession** constructor stating that the group or resource is not in the correct state to perform the requested operation.</span></span> <span data-ttu-id="8a377-122">Verwenden Sie [ExtendedExecutionForegroundSession](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.extendedexecution.foreground.extendedexecutionforegroundsession.aspx) und [ExtendedExecutionForegroundReason](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.extendedexecution.foreground.extendedexecutionforegroundreason.aspx) nicht. Sie erfordern eingeschränkte Funktionen und sind nicht zur Verwendung in Store-Anwendungen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="8a377-122">Do not use [ExtendedExecutionForegroundSession](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.extendedexecution.foreground.extendedexecutionforegroundsession.aspx) and [ExtendedExecutionForegroundReason](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.extendedexecution.foreground.extendedexecutionforegroundreason.aspx); they require restricted capabilities and are not available for use in Store applications.</span></span>

## <a name="run-while-minimized"></a><span data-ttu-id="8a377-123">Ausführen bei Minimierung</span><span class="sxs-lookup"><span data-stu-id="8a377-123">Run while minimized</span></span>

<span data-ttu-id="8a377-124">Es gibt zwei Fälle, in denen eine erweiterter Ausführung verwendet werden kann:</span><span class="sxs-lookup"><span data-stu-id="8a377-124">There are two cases where extended execution can be used:</span></span>
- <span data-ttu-id="8a377-125">Zu jedem Zeitpunkt während der regulären Vordergrundausführung, während sich die Anwendung im aktiven Zustand befindet.</span><span class="sxs-lookup"><span data-stu-id="8a377-125">At any point during regular foreground execution, while the application is in the running state.</span></span>
- <span data-ttu-id="8a377-126">Nachdem die Anwendung ein Halteereignis (das Betriebssystem ist dabei, die App anzuhalten) im entsprechenden Ereignishandler registriert hat.</span><span class="sxs-lookup"><span data-stu-id="8a377-126">After the application has received a suspending event (the OS is about to move the app to the suspended state) in the application’s suspending event handler.</span></span>

<span data-ttu-id="8a377-127">Der Code ist in beiden Fälle identisch, aber die Anwendung verhält sich in jedem Fall ein wenig anders.</span><span class="sxs-lookup"><span data-stu-id="8a377-127">The code for these two cases is the same, but the application behaves a little differently in each.</span></span> <span data-ttu-id="8a377-128">Im ersten Fall bleibt die Anwendung im aktiven Zustand, auch wenn ein Ereignis auftritt, das normalerweise einen Halt auslösen würde (z. B. wenn der Benutzer die Anwendung wechselt).</span><span class="sxs-lookup"><span data-stu-id="8a377-128">In the first case, the application stays in the running state, even if an event that normally would trigger suspension occurs (for example, the user navigating away from the application).</span></span> <span data-ttu-id="8a377-129">Die Anwendung reagiert niemals auf ein Halteereignis, während die Ausführungserweiterung aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="8a377-129">The application will never receive a suspending event while the execution extension is in effect.</span></span> <span data-ttu-id="8a377-130">Sobald die Erweiterung freigegeben wird, kann die Anwendung wieder angehalten werden.</span><span class="sxs-lookup"><span data-stu-id="8a377-130">When the extension is disposed, the application becomes eligible for suspension again.</span></span>

<span data-ttu-id="8a377-131">Wenn die Anwendung im zweiten Fall in den Haltezustand wechselt, verbleibt sie darin für den Zeitraum der Erweiterung.</span><span class="sxs-lookup"><span data-stu-id="8a377-131">In the second case, if the application is transitioning to the suspended state, it will stay in a suspending state for the period of the extension.</span></span> <span data-ttu-id="8a377-132">Sobald die Erweiterung abgelaufen ist, wechselt die Anwendung ohne weitere Benachrichtigung in den Haltezustand.</span><span class="sxs-lookup"><span data-stu-id="8a377-132">Once the extension expires, the application enters the suspended state without further notification.</span></span>

<span data-ttu-id="8a377-133">Verwenden Sie **ExtendedExecutionReason.Unspecified**, wenn Sie eine **ExtendedExecutionSession** erstellen, um zusätzliche Zeit anzufordern, bevor Ihre App in Szenarien wie Medienverarbeitung, Projektkompilierung oder zum Aufrechterhalten einer Netzwerkverbindung in den Hintergrund verschoben wird.</span><span class="sxs-lookup"><span data-stu-id="8a377-133">Use **ExtendedExecutionReason.Unspecified** when you create an **ExtendedExecutionSession** to request additional time before your app moves into the background for scenarios such as media processing, project compilation, or keeping a network connection alive.</span></span> <span data-ttu-id="8a377-134">Auf Desktopgeräten, auf denen Windows10-Editionen für Desktops ausgeführt werden (Home, Pro, Enterprise und Education), verwenden Sie diesen Ansatz, um zu vermeiden, dass eine App bei Minimierung angehalten wird.</span><span class="sxs-lookup"><span data-stu-id="8a377-134">On desktop devices running Windows 10 for desktop editions (Home, Pro, Enterprise, and Education), this is the approach to use if an app needs to avoid being suspended while it is minimized.</span></span>

<span data-ttu-id="8a377-135">Sie fordern die Erweiterung an, wenn ein über lange Zeit ausgeführter Vorgang gestartet wird, um den Wechsel in den Zustand **Suspending** zu verschieben, der andernfalls beim Verschieben der App in den Hintergrund ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="8a377-135">Request the extension when starting a long running operation in order to defer the **Suspending** state transition that otherwise occurs when the app moves into the background.</span></span> <span data-ttu-id="8a377-136">Auf Desktopgeräten gibt es für mit **ExtendedExecutionReason.Unspecified** erstellte erweiterte Ausführungssitzungen eine akkubasierte zeitliche Begrenzung.</span><span class="sxs-lookup"><span data-stu-id="8a377-136">On desktop devices, extended execution sessions created with **ExtendedExecutionReason.Unspecified** have a battery-aware time limit.</span></span> <span data-ttu-id="8a377-137">Wenn das Gerät an eine Steckdose angeschlossen ist, gibt es keine zeitliche Begrenzung für die erweiterte Ausführung.</span><span class="sxs-lookup"><span data-stu-id="8a377-137">If the device is connected to wall power, there is no limit to the length of the extended execution time period.</span></span> <span data-ttu-id="8a377-138">Wenn das Gerät mit Akku betrieben wird, kann der Zeitraum für die erweiterte Ausführung im Hintergrund bis zu zehn Minuten betragen.</span><span class="sxs-lookup"><span data-stu-id="8a377-138">If the device is on battery power, the extended execution time period can run up to ten minutes in the background.</span></span>

<span data-ttu-id="8a377-139">Tablet- oder Laptopbenutzer können auf Kosten der Akkulaufzeit den gleichen Zeitraum erhalten, wenn die Option **App Hintergrundaufgaben ausführen lassen** in den Einstellungen **Akkunutzung nach App** ausgewählt wird.</span><span class="sxs-lookup"><span data-stu-id="8a377-139">A tablet or laptop user can get the same long running behavior--at the expense of battery life--when the **Allow the app to run background tasks** option is selected in **Battery usage by app** settings.</span></span> <span data-ttu-id="8a377-140">(So finden Sie diese Option auf einem Laptop: wechseln Sie zu **Einstellungen** > **System** > **Akku** > **Akkunutzung nach App** (der Link unter dem Prozentsatz der verbleibenden Lebensdauer des Akkus) > wählen Sie eine App aus > deaktivieren Sie **Von Windows verwaltet** > wählen Sie **App Hintergrundaufgaben ausführen lassen** aus.</span><span class="sxs-lookup"><span data-stu-id="8a377-140">(To find this option on a laptop, go to **Settings** > **System** > **Battery** > **Battery usage by App** (the link under the percent of battery power remaining) > select an app > turn off **Managed By Windows** > select **Allow app to run background tasks**.</span></span>  

<span data-ttu-id="8a377-141">Diese Art der erweiterten Ausführung wird auf allen Betriebssystemeditionen beendet, wenn das Gerät in den Zustand „Verbundener Standbymodus“ versetzt wird.</span><span class="sxs-lookup"><span data-stu-id="8a377-141">On all OS editions this kind of extended execution session stops when the device enters Connected Standby.</span></span> <span data-ttu-id="8a377-142">Auf mobilen Geräten mit Windows10 Mobile wird diese Art von erweiterter Ausführung solange ausgeführt, wie der Bildschirm aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="8a377-142">On mobile devices running Windows 10 Mobile, this kind of extended execution session will run as long as the screen is on.</span></span> <span data-ttu-id="8a377-143">Wenn der Bildschirm deaktiviert wird, versucht das Gerät sofort, in den energiesparenden Zustand „Verbundener Standbymodus“ zu wechseln.</span><span class="sxs-lookup"><span data-stu-id="8a377-143">When the screen turns off, the device immediately attempts to enter the low-power Connected-Standby mode.</span></span> <span data-ttu-id="8a377-144">Auf Desktopgeräten wird die Sitzung weiter ausgeführt, wenn der Sperrbildschirm angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="8a377-144">On desktop devices, the session will continue running if the lock screen appears.</span></span> <span data-ttu-id="8a377-145">Das Gerät wechselt nach Deaktivierung des Bildschirms für einen gewissen Zeitraum nicht in den Zustand „Verbundener Standbymodus“.</span><span class="sxs-lookup"><span data-stu-id="8a377-145">The device does not enter Connected Standby for a period of time after the screen turns off.</span></span> <span data-ttu-id="8a377-146">In der Xbox-Betriebssystemedition wechselt das Gerät nach einer Stunde in den Zustand „Verbundener Standbymodus“, wenn der Benutzer die Standardeinstellung nicht geändert hat.</span><span class="sxs-lookup"><span data-stu-id="8a377-146">On the Xbox OS Edition, the device enters Connect Standby after one hour unless the user changes the default.</span></span>

## <a name="track-the-users-location"></a><span data-ttu-id="8a377-147">Abrufen des Standorts eines Benutzers</span><span class="sxs-lookup"><span data-stu-id="8a377-147">Track the user's location</span></span>

<span data-ttu-id="8a377-148">Geben Sie beim Erstellen einer **ExtendedExecutionSession** **ExtendedExecutionReason.LocationTracking** an, wenn Ihre App regelmäßig den Standort aus [GeoLocator](https://msdn.microsoft.com/library/windows/apps/windows.devices.geolocation.geolocator.aspx) protokollieren muss.</span><span class="sxs-lookup"><span data-stu-id="8a377-148">Specify **ExtendedExecutionReason.LocationTracking** when you create an **ExtendedExecutionSession** if your app needs to regularly log the location from the [GeoLocator](https://msdn.microsoft.com/library/windows/apps/windows.devices.geolocation.geolocator.aspx).</span></span> <span data-ttu-id="8a377-149">Apps für Fitnessnachverfolgung und Navigation, die regelmäßig den Standort des Benutzers überwachen müssen, sollten diesen Grund verwenden.</span><span class="sxs-lookup"><span data-stu-id="8a377-149">Apps for fitness tracking and navigation that need to regularly monitor the user's location and should use this reason.</span></span>

<span data-ttu-id="8a377-150">Eine erweiterte Ausführungssitzung der Standortnachverfolgung kann bei Bedarf auch ausgeführt werden, während der Bildschirm auf einem mobilen Gerät gesperrt ist.</span><span class="sxs-lookup"><span data-stu-id="8a377-150">A location tracking extended execution session can run as long as needed, including while the screen is locked on a mobile device.</span></span> <span data-ttu-id="8a377-151">Pro Gerät kann jedoch nur eine solche Sitzung ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="8a377-151">However, there can only be one such session running per device.</span></span> <span data-ttu-id="8a377-152">Eine erweiterte Ausführung zur Standortnachverfolgung kann nur im Vordergrund angefordert werden, und die App muss sich im Zustand **Ausgeführt** befinden.</span><span class="sxs-lookup"><span data-stu-id="8a377-152">A location tracking extended execution session can only be requested in the foreground, and the app must be in the **Running** state.</span></span> <span data-ttu-id="8a377-153">Dadurch wird sichergestellt, dass der Benutzer weiß, dass die App die erweiterte Ausführung zur Standortnachverfolgung initiiert hat.</span><span class="sxs-lookup"><span data-stu-id="8a377-153">This ensures that the user is aware that the app has initiated an extended location tracking session.</span></span> <span data-ttu-id="8a377-154">GeoLocator kann mittels einer Hintergrundaufgabe oder eines App-Diensts während der Ausführung der App im Hintergrund weiter verwendet werden, ohne dass eine erweiterte Ausführung zur Standortnachverfolgung angefordert wird.</span><span class="sxs-lookup"><span data-stu-id="8a377-154">It is still possible to use the GeoLocator while the app is in the background by using a background task, or an app service, without requesting a location tracking extended execution session.</span></span>

## <a name="save-critical-data-locally"></a><span data-ttu-id="8a377-155">Lokales Speichern wichtiger Daten</span><span class="sxs-lookup"><span data-stu-id="8a377-155">Save Critical Data Locally</span></span>

<span data-ttu-id="8a377-156">Geben Sie beim Erstellen einer **ExtendedExecutionSession** **ExtendedExecutionReason.SavingData** an, wenn Sie in Fällen, in das Nichtspeichern von Daten vor Beenden der App zu Datenverlusten und einer negativen Benutzererfahrung führt, Benutzerdaten speichern möchten.</span><span class="sxs-lookup"><span data-stu-id="8a377-156">Specify **ExtendedExecutionReason.SavingData** when you create an **ExtendedExecutionSession** to save user data in the case where not saving the data before the app is terminated will result in data loss and a negative user experience.</span></span>

<span data-ttu-id="8a377-157">Verwenden Sie diese Art von Sitzung nicht, um den Lebenszyklus einer App zum Zweck des Hoch- oder Herunterladens von Daten zu verlängern.</span><span class="sxs-lookup"><span data-stu-id="8a377-157">Don't use this kind of session to extend the lifetime of an app to upload or download data.</span></span> <span data-ttu-id="8a377-158">Fordern Sie eine [Hintergrundübertragung](https://msdn.microsoft.com/windows/uwp/networking/background-transfers) an, wenn Sie Daten hochladen müssen, oder registrieren Sie einen **MaintenanceTrigger**, um die Übertragung zu verarbeiten, wenn die Stromversorgung verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="8a377-158">If you need to upload data, request a [background transfer](https://msdn.microsoft.com/windows/uwp/networking/background-transfers) or register a **MaintenanceTrigger** to handle the transfer when AC power is available.</span></span> <span data-ttu-id="8a377-159">Eine erweiterte Ausführungssitzung mit dem Grund **ExtendedExecutionReason.SavingData** kann angefordert werden, wenn sich die App im Vordergrund und im Zustand **Ausgeführt** befindet oder wenn sie sich im Hintergrund und im Zustand **Angehalten** befindet.</span><span class="sxs-lookup"><span data-stu-id="8a377-159">A **ExtendedExecutionReason.SavingData** extended execution session can be requested either when the app is in the foreground and in the **Running** state, or in the background and in the **Suspending** state.</span></span>

<span data-ttu-id="8a377-160">Der Zustand **Angehalten** ist die letzte Phase während des App-Lebenszyklus, in der die App Aufgaben ausführen kann, bevor sie beendet wird.</span><span class="sxs-lookup"><span data-stu-id="8a377-160">The **Suspending** state is the last opportunity during the app lifecycle that an app can do work before the app is terminated.</span></span> <span data-ttu-id="8a377-161">**ExtendedExecutionReason.SavingData** ist die einzige Art von **ExtendedExecutionSession**, die im **Suspending**-Zustand angefordert werden kann.</span><span class="sxs-lookup"><span data-stu-id="8a377-161">**ExtendedExecutionReason.SavingData** is the only type of **ExtendedExecutionSession** that can be requested in the **Suspending** state.</span></span> <span data-ttu-id="8a377-162">Das Anfordern einer erweiterten Ausführungssitzung mit dem Grund **ExtendedExecutionReason.SavingData**, während sich die App im Zustand **Angehalten** befindet, kann ein Problem verursachen, das Sie beachten sollten.</span><span class="sxs-lookup"><span data-stu-id="8a377-162">Requesting a **ExtendedExecutionReason.SavingData** extended execution session while the app is in the **Suspending** state creates a potential issue that you should be aware of.</span></span> <span data-ttu-id="8a377-163">Wenn im Zustand **Suspending** eine erweiterte Ausführungssitzung angefordert wird, und der Benutzer das erneute Starten der App anfordert, benötigt sie zum Starten scheinbar eine lange Zeit.</span><span class="sxs-lookup"><span data-stu-id="8a377-163">If an extended execution session is requested while in the **Suspending** state, and the user requests the app be launched again, it may appear to take a long time to launch.</span></span> <span data-ttu-id="8a377-164">Der Grund hierfür ist, dass die erweiterte Ausführungssitzung abgeschlossen werden muss, bevor die alte Instanz der App geschlossen und eine neue Instanz der App gestartet werden kann.</span><span class="sxs-lookup"><span data-stu-id="8a377-164">This is because the extended execution session time period must complete before the old instance of the app can be closed and a new instance of the app can be launched.</span></span> <span data-ttu-id="8a377-165">Es wird auf Leistung beim Starten verzichtet, um sicherzustellen, dass der Benutzerstatus nicht verloren geht.</span><span class="sxs-lookup"><span data-stu-id="8a377-165">Launch performance time is sacrificed in order to guarantee that user state is not lost.</span></span>

## <a name="request-disposal-and-revocation"></a><span data-ttu-id="8a377-166">Anfordern, Löschen und Sperren</span><span class="sxs-lookup"><span data-stu-id="8a377-166">Request, disposal, and revocation</span></span>

<span data-ttu-id="8a377-167">Es gibt drei grundsätzliche Interaktionen mit erweiterten Ausführungssitzungen: Anfordern, Löschen und Sperren.</span><span class="sxs-lookup"><span data-stu-id="8a377-167">There are three fundamental interactions with an extended execution session: the request, disposal, and revocation.</span></span>  <span data-ttu-id="8a377-168">Das Anfordern wird im folgenden Codeausschnitt gezeigt.</span><span class="sxs-lookup"><span data-stu-id="8a377-168">Making the request is modeled in the following code snippet.</span></span>

### <a name="request"></a><span data-ttu-id="8a377-169">Anfordern</span><span class="sxs-lookup"><span data-stu-id="8a377-169">Request</span></span>

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
[<span data-ttu-id="8a377-170">Siehe Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="8a377-170">See code sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/ExtendedExecution/cs/Scenario1_UnspecifiedReason.xaml.cs#L81-L110)  

<span data-ttu-id="8a377-171">Durch Aufrufen von **RequestExtensionAsync** wird durch das Betriebssystem geprüft, ob der Benutzer Hintergrundaktivitäten für die App genehmigt hat und ob das System über genügend Ressourcen verfügt, um die Hintergrundausführung zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="8a377-171">Calling **RequestExtensionAsync** checks with the operating system to see if the user has approved background activity for the app and whether the system has the available resources to enable background execution.</span></span> <span data-ttu-id="8a377-172">Pro App wird jeweils nur eine Sitzung genehmigt, sodass weitere Aufrufe von **RequestExtensionAsync** dazu führen, dass die Sitzung abgelehnt wird.</span><span class="sxs-lookup"><span data-stu-id="8a377-172">Only one session will be approved for an app at any time, causing additional calls to **RequestExtensionAsync** to result in the session being denied.</span></span>

<span data-ttu-id="8a377-173">Sie können [BackgroundExecutionManager](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.backgroundexecutionmanager.aspx) im Voraus überprüfen, um den [BackgroundAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.backgroundaccessstatus.aspx?f=255&MSPPError=-2147217396) zu ermitteln. Dies ist die Benutzereinstellung, die festlegt, ob Ihre App im Hintergrund ausgeführt werden kann oder nicht.</span><span class="sxs-lookup"><span data-stu-id="8a377-173">You can check the [BackgroundExecutionManager](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.backgroundexecutionmanager.aspx) beforehand to determine the [BackgroundAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.backgroundaccessstatus.aspx?f=255&MSPPError=-2147217396), which is the user setting that indicates whether your app can run in the background or not.</span></span> <span data-ttu-id="8a377-174">Weitere Informationen zu diesen Benutzereinstellungen finden Sie unter [Hintergrundaktivitäten und Energieinformationen](https://blogs.windows.com/buildingapps/2016/08/01/battery-awareness-and-background-activity/#XWK8mEgWD7JHvC10.97).</span><span class="sxs-lookup"><span data-stu-id="8a377-174">To learn more about these user settings see [Background Activity and Energy Awareness](https://blogs.windows.com/buildingapps/2016/08/01/battery-awareness-and-background-activity/#XWK8mEgWD7JHvC10.97).</span></span>

<span data-ttu-id="8a377-175">Der **ExtendedExecutionReason** gibt den Vorgang an, der von Ihrer App im Hintergrund ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="8a377-175">The **ExtendedExecutionReason** indicates the operation your app is performing in the background.</span></span> <span data-ttu-id="8a377-176">Die Zeichenfolge **Beschreibung** ist eine lesbare Zeichenfolge, die beschreibt, warum Ihre App den Vorgang ausführen muss.</span><span class="sxs-lookup"><span data-stu-id="8a377-176">The **Description** string is a human-readable string that explains why your app needs to perform the operation.</span></span> <span data-ttu-id="8a377-177">Diese Zeichenfolge wird dem Benutzer nicht angezeigt, wird aber möglicherweise in zukünftigen Windows-Versionen verfügbar gemacht.</span><span class="sxs-lookup"><span data-stu-id="8a377-177">This string is not presented to the user, but may be made available in a future release of Windows.</span></span> <span data-ttu-id="8a377-178">Der Ereignishandler **Revoked** ist erforderlich, damit eine erweiterte Ausführungssitzung ordnungsgemäß angehalten werden kann, wenn der Benutzer oder das System festlegen, dass die App nicht mehr im Hintergrund ausgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="8a377-178">The **Revoked** event handler is required so that an extended execution session can halt gracefully if the user, or the system, decides that the app can no longer run in the background.</span></span>

### <a name="revoked"></a><span data-ttu-id="8a377-179">Sperren</span><span class="sxs-lookup"><span data-stu-id="8a377-179">Revoked</span></span>

<span data-ttu-id="8a377-180">Wenn eine App über eine aktive erweiterte Ausführungssitzung verfügt und das System das Anhalten der Hintergrundaktivität erfordert, weil eine Vordergrundanwendung die Ressourcen benötigt, wird die Sitzung widerrufen.</span><span class="sxs-lookup"><span data-stu-id="8a377-180">If an app has an active extended execution session and the system requires background activity to halt because a foreground application requires the resources, then the session is revoked.</span></span> <span data-ttu-id="8a377-181">Der Zeitraum für eine erweiterte Ausführungssitzung wird nie beendet, ohne dass zuerst der Ereignishandler **Revoked** aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="8a377-181">An extended execution session time period is never terminated without first firing the **Revoked** event handler.</span></span>

<span data-ttu-id="8a377-182">Wenn das Ereignis **Revoked** für eine erweiterte Ausführungssitzung mit dem Grund **ExtendedExecutionReason.SavingData** ausgelöst wird, hat die App nur eine Sekunde Zeit, um den gerade ausgeführten Vorgang abzuschließen und den Zustand **Angehalten** zu beenden.</span><span class="sxs-lookup"><span data-stu-id="8a377-182">When the **Revoked** event is fired for an **ExtendedExecutionReason.SavingData** extended execution session, the app has one second to complete the operation it was performing and finish **Suspending**.</span></span>

<span data-ttu-id="8a377-183">Das Sperren kann aus verschiedenen Gründen erfolgen: das Erreichen der zeitlichen Begrenzung für die Ausführung, das Erreichen der Begrenzung für den Energieverbrauch für Hintergrundaufgaben oder das notwendige Freigeben von Arbeitsspeicher, damit der Benutzer eine neue App im Vordergrund öffnen kann.</span><span class="sxs-lookup"><span data-stu-id="8a377-183">Revocation can occur for many reasons: an execution time limit was reached, a background energy quota was reached, or memory needs to be reclaimed in order for the user to open a new app in the foreground.</span></span>

<span data-ttu-id="8a377-184">Im Folgenden wird Ihnen ein Beispiel für den Ereignishandler „Revoked“ angezeigt:</span><span class="sxs-lookup"><span data-stu-id="8a377-184">Here is an example of a Revoked event handler:</span></span>

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
[<span data-ttu-id="8a377-185">Siehe Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="8a377-185">See code sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/ExtendedExecution/cs/Scenario1_UnspecifiedReason.xaml.cs#L124-L141)

### <a name="dispose"></a><span data-ttu-id="8a377-186">Löschen</span><span class="sxs-lookup"><span data-stu-id="8a377-186">Dispose</span></span>

<span data-ttu-id="8a377-187">Der letzte Schritt besteht im Löschen der erweiterten Ausführungssitzung.</span><span class="sxs-lookup"><span data-stu-id="8a377-187">The final step is to dispose of the extended execution session.</span></span> <span data-ttu-id="8a377-188">Sie sollten die Sitzung und alle weiteren, Arbeitsspeicher in Anspruch nehmenden Ressourcen löschen, da andernfalls die von der App beim Warten auf das Beenden der Sitzung verbrauchte Energie auf das Energiekontingent der App angerechnet wird.</span><span class="sxs-lookup"><span data-stu-id="8a377-188">You want to dispose of the session, and any other memory intensive assets, because otherwise the energy used by the app while it is waiting for the session to close will be counted against the app's energy quota.</span></span> <span data-ttu-id="8a377-189">Um einen möglichst großen Teil des Energiekontingents der App zu bewahren, ist es wichtig, die Sitzung zu löschen, wenn sie nicht mehr benötigt wird, damit die App schneller in den Zustand **Angehalten** wechseln kann.</span><span class="sxs-lookup"><span data-stu-id="8a377-189">To preserve as much of the energy quota for the app as possible, it is important to dispose of the session when you are done with your work for the session so that the app can move into the **Suspended** state more quickly.</span></span>

<span data-ttu-id="8a377-190">Wenn Sie die Sitzung selbst löschen, statt auf das Sperrereignis zu warten, wird die Energiekontingentnutzung Ihrer App reduziert.</span><span class="sxs-lookup"><span data-stu-id="8a377-190">Disposing of the session yourself, rather than waiting for the revocation event, reduces your app's energy quota usage.</span></span> <span data-ttu-id="8a377-191">Das bedeutet, dass Ihre App zukünftig länger im Hintergrund ausgeführt werden darf, da ihr hierfür ein größeres Energiekontingent zur Verfügung steht.</span><span class="sxs-lookup"><span data-stu-id="8a377-191">This means that your app will be permitted to run in the background longer in future sessions because you'll have more energy quota available to do so.</span></span> <span data-ttu-id="8a377-192">Sie müssen bis zum Abschluss des Vorgangs einen Verweis auf das Objekt **ExtendedExecutionSession** beibehalten, damit Sie dessen Methode **Dispose** aufrufen können.</span><span class="sxs-lookup"><span data-stu-id="8a377-192">You must maintain a reference to the **ExtendedExecutionSession** object until the end of the operation so that you can call its **Dispose** method.</span></span>

<span data-ttu-id="8a377-193">Im Folgenden wird ein Codeausschnitt angezeigt, in dem eine erweiterte Ausführungssitzung gelöscht wird:</span><span class="sxs-lookup"><span data-stu-id="8a377-193">A snippet that disposes an extended execution session follows:</span></span>

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
[<span data-ttu-id="8a377-194">Siehe Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="8a377-194">See code sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/ExtendedExecution/cs/Scenario1_UnspecifiedReason.xaml.cs#L49-L63)

<span data-ttu-id="8a377-195">Für eine App kann jeweils nur eine **ExtendedExecutionSession** aktiv sein.</span><span class="sxs-lookup"><span data-stu-id="8a377-195">An app can only have one **ExtendedExecutionSession** active at a time.</span></span> <span data-ttu-id="8a377-196">Viele Apps verwenden asynchrone Aufgaben, um komplexe Vorgänge ausführen, die Zugriff auf Ressourcen wie Speicher, Netzwerk oder netzwerkbasierte Dienste erfordern.</span><span class="sxs-lookup"><span data-stu-id="8a377-196">Many apps use asynchronous tasks in order to complete complex operations that require access to resources such as storage, network, or network-based services.</span></span> <span data-ttu-id="8a377-197">Wenn ein Vorgang mehrere asynchrone Vorgänge erfordert, um abgeschlossen zu werden, muss der Zustand jeder dieser Aufgaben berücksichtigt werden, bevor **ExtendedExecutionSession** gelöscht wird und die App angehalten werden kann.</span><span class="sxs-lookup"><span data-stu-id="8a377-197">If an operation requires multiple asynchronous tasks to complete, then the state of each of these tasks must be accounted for before disposing the **ExtendedExecutionSession** and allowing the app to be suspended.</span></span> <span data-ttu-id="8a377-198">Dies erfordert eine Verweiszählung der Anzahl der Aufgaben, die weiter ausgeführt werden. Erst wenn dieser Wert null erreicht, kann die Sitzung gelöscht werden.</span><span class="sxs-lookup"><span data-stu-id="8a377-198">This requires reference counting the number of tasks that are still running, and not disposing of the session until that value reaches zero.</span></span>

<span data-ttu-id="8a377-199">Der folgende Beispielcode dient zum Verwalten mehrerer Aufgaben während einer erweiterten Ausführungssitzung:</span><span class="sxs-lookup"><span data-stu-id="8a377-199">Here is some example code for managing multiple tasks during an extended execution session period.</span></span> <span data-ttu-id="8a377-200">Weitere Informationen zur Verwendung in Ihrer App finden Sie im folgenden Codebeispiel:</span><span class="sxs-lookup"><span data-stu-id="8a377-200">For more information on how to use this in your app please see the code sample linked below:</span></span>

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

    public static async Task<ExtendedExecutionResult> RequestSessionAsync(ExtendedExecutionReason reason, TypedEventHandler<object, ExtendedExecutionRevokedEventArgs> revoked, String description)
    {
        // The previous Extended Execution must be closed before a new one can be requested.       
        ClearSession();

        var newSession = new ExtendedExecutionSession();
        newSession.Reason = reason;
        newSession.Description = description;
        newSession.Revoked += SessionRevoked;

        // Add a revoked handler provided by the app in order to clean up an operation that had to be halted prematurely
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
        
        //If there are no more running tasks than end the extended lifetime by clearing the session
        if (taskCount == 0 && session != null)
        {
            ClearSession();
        }
    }

    private static void SessionRevoked(object sender, ExtendedExecutionRevokedEventArgs args)
    {
        //The session has been prematurely revoked due to system constraints, ensure the session is disposed
        if (session != null)
        {
            session.Dispose();
            session = null;
        }
        
        taskCount = 0;
    }
}
```
[<span data-ttu-id="8a377-201">Siehe Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="8a377-201">See code sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/ExtendedExecution/cs/Scenario4_MultipleTasks.xaml.cs)

## <a name="ensure-that-your-app-uses-resources-well"></a><span data-ttu-id="8a377-202">Gute Nutzung von Ressourcen durch Ihre App</span><span class="sxs-lookup"><span data-stu-id="8a377-202">Ensure that your app uses resources well</span></span>

<span data-ttu-id="8a377-203">Das Optimieren von Arbeitsspeicher und Energieverbrauch Ihrer App ist der Schlüssel, um sicherzustellen, dass das Betriebssystem die Ausführung Ihrer App auch dann zulässt, wenn sie sich nicht mehr im Vordergrund befindet.</span><span class="sxs-lookup"><span data-stu-id="8a377-203">Tuning your app's memory and energy use is key to ensuring that the operating system will allow your app to continue to run when it is no longer the foreground app.</span></span> <span data-ttu-id="8a377-204">Um zu ermitteln, wie viel Arbeitsspeicher Ihre App verwendet, verwenden Sie die [Speicherverwaltungs-APIs](https://msdn.microsoft.com/library/windows/apps/windows.system.memorymanager.aspx).</span><span class="sxs-lookup"><span data-stu-id="8a377-204">Use the [Memory Management APIs](https://msdn.microsoft.com/library/windows/apps/windows.system.memorymanager.aspx) to see how much memory your app is using.</span></span> <span data-ttu-id="8a377-205">Je mehr Arbeitsspeicher Ihre App verwendet, desto schwieriger wird es für das Betriebssystem, Ihre App weiter auszuführen, wenn sich eine andere App im Vordergrund befindet.</span><span class="sxs-lookup"><span data-stu-id="8a377-205">The more memory your app uses, the harder it is for the OS to keep your app running when another app is in the foreground.</span></span> <span data-ttu-id="8a377-206">Der Benutzer hat letztendlich die Kontrolle über alle Hintergrundaktivitäten, die Ihre App ausführen kann, und kann die Auswirkungen Ihrer App auf den Akkuverbrauch erkennen.</span><span class="sxs-lookup"><span data-stu-id="8a377-206">The user is ultimately in control of all background activity that your app can perform and has visibility on the impact your app has on battery use.</span></span>

<span data-ttu-id="8a377-207">Um zu ermitteln, ob der Benutzer die Hintergrundaktivität Ihrer App begrenzt hat, verwenden Sie [BackgroundExecutionManager.RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.backgroundexecutionmanager.aspx).</span><span class="sxs-lookup"><span data-stu-id="8a377-207">Use [BackgroundExecutionManager.RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.backgroundexecutionmanager.aspx) to determine if the user has decided that your app’s background activity should be limited.</span></span> <span data-ttu-id="8a377-208">Achten Sie auf die Akkunutzung, und führen Sie Ihre App nur dann im Hintergrund aus, wenn dies zum Ausführen einer vom Benutzer gewünschten Aktion notwendig ist.</span><span class="sxs-lookup"><span data-stu-id="8a377-208">Be aware of your battery usage and only run in the background when it is necessary to complete an action that the user wants.</span></span>

## <a name="see-also"></a><span data-ttu-id="8a377-209">Weitere Informationen finden Sie unter</span><span class="sxs-lookup"><span data-stu-id="8a377-209">See also</span></span>

[<span data-ttu-id="8a377-210">Beispiel für die erweiterte Ausführung</span><span class="sxs-lookup"><span data-stu-id="8a377-210">Extended Execution Sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/ExtendedExecution)  
[<span data-ttu-id="8a377-211">Anwendungslebenszyklus</span><span class="sxs-lookup"><span data-stu-id="8a377-211">Application Lifecycle</span></span>](https://msdn.microsoft.com/windows/uwp/launch-resume/app-lifecycle)  
<span data-ttu-id="8a377-212">[App Lifecycle - Keep Apps Alive with Background Tasks and Extended Execution](https://msdn.microsoft.com/en-us/magazine/mt590969.aspx)
[Geben Sie Speicher frei, wenn Ihre App in den Hintergrund verschoben wird](https://msdn.microsoft.com/windows/uwp/launch-resume/reduce-memory-usage)</span><span class="sxs-lookup"><span data-stu-id="8a377-212">[App Lifecycle - Keep Apps Alive with Background Tasks and Extended Execution](https://msdn.microsoft.com/en-us/magazine/mt590969.aspx)
[Background Memory Management](https://msdn.microsoft.com/windows/uwp/launch-resume/reduce-memory-usage)</span></span>  
[<span data-ttu-id="8a377-213">Hintergrundübertragungen</span><span class="sxs-lookup"><span data-stu-id="8a377-213">Background Transfers</span></span>](https://msdn.microsoft.com/windows/uwp/networking/background-transfers)  
[<span data-ttu-id="8a377-214">Akkuinformationen und Hintergrundaktivität</span><span class="sxs-lookup"><span data-stu-id="8a377-214">Battery Awareness and Background Activity</span></span>](https://blogs.windows.com/buildingapps/2016/08/01/battery-awareness-and-background-activity/#I2bkQ6861TRpbRjr.97)  
[<span data-ttu-id="8a377-215">MemoryManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="8a377-215">MemoryManager class</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.system.memorymanager.aspx)  
[<span data-ttu-id="8a377-216">Wiedergeben von Medien im Hintergrund</span><span class="sxs-lookup"><span data-stu-id="8a377-216">Play Media in the Background</span></span>](https://msdn.microsoft.com/windows/uwp/audio-video-camera/background-audio)  