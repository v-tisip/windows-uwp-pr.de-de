---
author: andrewleader
Description: Learn how to use Notification Listener to access all of the user's notifications.
title: Notification-Listener
ms.assetid: E9AB7156-A29E-4ED7-B286-DA4A6E683638
label: Chaseable tiles
template: detail.hbs
ms.author: mijacobs
ms.date: 06/13/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, Uwp, notification listener, Usernotificationlistener, Dokumentation, Zugriff auf Benachrichtigungen
ms.localizationpriority: medium
ms.openlocfilehash: f4d8cb9ef7589bd8f0c56586ab8fcfec7c1f01e3
ms.sourcegitcommit: 2c4daa36fb9fd3e8daa83c2bd0825f3989d24be8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "5520401"
---
# <a name="notification-listener-access-all-notifications"></a><span data-ttu-id="59efd-103">Notification-Listener: Zugriff auf alle Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="59efd-103">Notification listener: Access all notifications</span></span>

<span data-ttu-id="59efd-104">Der Notification-Listener ermöglicht den Zugriff auf die Benachrichtigungen eines Benutzers.</span><span class="sxs-lookup"><span data-stu-id="59efd-104">The notification listener provides access to a user's notifications.</span></span> <span data-ttu-id="59efd-105">Smartwatches und andere Wearables können die Benachrichtigungsfunktion nutzen, um die Benachrichtigungen des Telefons an das tragbare Gerät zu senden.</span><span class="sxs-lookup"><span data-stu-id="59efd-105">Smartwatches and other wearables can use the notification listener to send the phone's notifications to the wearable device.</span></span> <span data-ttu-id="59efd-106">Anwendungen für die Heimautomation können Notification-Listener verwenden, um bestimmte Aktionen auszuführen, wenn Benachrichtigungen empfangen werden, z. B. Blinken, wenn Sie einen Anruf erhalten.</span><span class="sxs-lookup"><span data-stu-id="59efd-106">Home automation apps can use notification listener to perform specific actions when notifications are received, such as making the lights blink when you recieve a call.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="59efd-107">**Benötigt Anniversary Update**: Sie müssen das SDK 14393 als Ziel und Build 14393 oder höher ausführen, um Notification-Listener verwenden zu können.</span><span class="sxs-lookup"><span data-stu-id="59efd-107">**Requires Anniversary Update**: You must target SDK 14393 and be running build 14393 or higher to use Notification Listener.</span></span>


> <span data-ttu-id="59efd-108">**Wichtige APIs**: [UserNotificationListener-Klasse](https://docs.microsoft.com/uwp/api/Windows.UI.Notifications.Management.UserNotificationListener), [UserNotificationChangedTrigger-Klasse](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.UserNotificationChangedTrigger)</span><span class="sxs-lookup"><span data-stu-id="59efd-108">**Important APIs**: [UserNotificationListener class](https://docs.microsoft.com/uwp/api/Windows.UI.Notifications.Management.UserNotificationListener), [UserNotificationChangedTrigger class](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.UserNotificationChangedTrigger)</span></span>


## <a name="enable-the-listener-by-adding-the-user-notification-capability"></a><span data-ttu-id="59efd-109">Aktivieren des Listeners durch Hinzufügen der User Notification-Funktion</span><span class="sxs-lookup"><span data-stu-id="59efd-109">Enable the listener by adding the User Notification capability</span></span> 

<span data-ttu-id="59efd-110">Um den Notification-Listener verwenden zu können, müssen Sie die User Notification Listener-Funktion zu Ihrem Anwendungsmanifest hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="59efd-110">To use the notification listener, you must add the User Notification Listener capability to your app manifest.</span></span>

1. <span data-ttu-id="59efd-111">Klicken Sie in Visual Studio im Projektmappen-Explorer doppelt auf Ihre `Package.appxmanifest`-Datei, um den Manifestdesigner zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="59efd-111">In Visual Studio, in the Solution Explorer, double click your `Package.appxmanifest` file to open the manifest designer.</span></span>
2. <span data-ttu-id="59efd-112">Öffnen Sie die Registerkarte „Funktionen“.</span><span class="sxs-lookup"><span data-stu-id="59efd-112">Open the Capabilities tab.</span></span>
3. <span data-ttu-id="59efd-113">Überprüfen Sie die **User Notification Listener**-Funktion.</span><span class="sxs-lookup"><span data-stu-id="59efd-113">Check the **User Notification Listener** capability.</span></span>


## <a name="check-whether-the-listener-is-supported"></a><span data-ttu-id="59efd-114">Prüfen, ob der Listener unterstützt wird</span><span class="sxs-lookup"><span data-stu-id="59efd-114">Check whether the listener is supported</span></span>

<span data-ttu-id="59efd-115">Wenn Ihre App ältere Versionen von Windows 10 unterstützt, müssen Sie die [ApiInformation](https://docs.microsoft.com/uwp/api/Windows.Foundation.Metadata.ApiInformation)-Klasse verwenden, um zu überprüfen, ob der Listener unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="59efd-115">If your app supports older versions of Windows 10, you need to use the [ApiInformation class](https://docs.microsoft.com/uwp/api/Windows.Foundation.Metadata.ApiInformation) to check whether the listener is supported.</span></span>  <span data-ttu-id="59efd-116">Wenn der Listener nicht unterstützt wird, vermeiden Sie Aufrufe der Listener-APIs.</span><span class="sxs-lookup"><span data-stu-id="59efd-116">If the listener isn't supported, avoid executing any calls to the listener APIs.</span></span>

```csharp
if (ApiInformation.IsTypePresent("Windows.UI.Notifications.Management.UserNotificationListener"))
{
    // Listener supported!
}
 
else
{
    // Older version of Windows, no Listener
}
```


## <a name="requesting-access-to-the-listener"></a><span data-ttu-id="59efd-117">Zugriff auf den Listener anfordern</span><span class="sxs-lookup"><span data-stu-id="59efd-117">Requesting access to the listener</span></span>

<span data-ttu-id="59efd-118">Da der Listener den Zugriff auf die Benachrichtigungen des Benutzers erlaubt, müssen Benutzer Ihrer App Zugriffsberechtigung für die Benachrichtigungen erteilen.</span><span class="sxs-lookup"><span data-stu-id="59efd-118">Since the listener allows access to the user's notifications, users must give your app permission to access their notifications.</span></span> <span data-ttu-id="59efd-119">Während der ersten Ausführung Ihrer App sollten Sie den Zugriff beantragen, um den Notification-Listener zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="59efd-119">During your app's first-run experience, you should request access to use the notification listener.</span></span> <span data-ttu-id="59efd-120">Wenn Sie möchten, können Sie eine Vorab-Benutzeroberfläche anzeigen, die erklärt, warum Ihre Anwendung Zugriff auf die Benachrichtigungen des Benutzers benötigt, bevor Sie [RequestAccessAsync](https://docs.microsoft.com/uwp/api/windows.ui.notifications.management.usernotificationlistener.RequestAccessAsync) aufrufen, damit der Benutzer versteht, warum er Zugriff erlauben sollte.</span><span class="sxs-lookup"><span data-stu-id="59efd-120">If you want, you can show some preliminary UI that explains why your app needs access to the user's notifications before you call [RequestAccessAsync](https://docs.microsoft.com/uwp/api/windows.ui.notifications.management.usernotificationlistener.RequestAccessAsync), so that the user understands why they should allow access.</span></span>

```csharp
// Get the listener
UserNotificationListener listener = UserNotificationListener.Current;
 
// And request access to the user's notifications (must be called from UI thread)
UserNotificationListenerAccessStatus accessStatus = await listener.RequestAccessAsync();
 
switch (accessStatus)
{
    // This means the user has granted access.
    case UserNotificationListenerAccessStatus.Allowed:
 
        // Yay! Proceed as normal
        break;
 
    // This means the user has denied access.
    // Any further calls to RequestAccessAsync will instantly
    // return Denied. The user must go to the Windows settings
    // and manually allow access.
    case UserNotificationListenerAccessStatus.Denied:
 
        // Show UI explaining that listener features will not
        // work until user allows access.
        break;
 
    // This means the user closed the prompt without
    // selecting either allow or deny. Further calls to
    // RequestAccessAsync will show the dialog again.
    case UserNotificationListenerAccessStatus.Unspecified:
 
        // Show UI that allows the user to bring up the prompt again
        break;
}
```

<span data-ttu-id="59efd-121">Der Benutzer kann den Zugriff jederzeit über Windows-Einstellungen widerrufen.</span><span class="sxs-lookup"><span data-stu-id="59efd-121">The user can revoke access at any time via Windows Settings.</span></span> <span data-ttu-id="59efd-122">Daher sollte Ihre App immer den Zugriffsstatus über die Methode [GetAccessStatus](https://docs.microsoft.com/uwp/api/windows.ui.notifications.management.usernotificationlistener.GetAccessStatus) überprüfen, bevor Sie Code ausführen, der den Notfication-Listener verwendet.</span><span class="sxs-lookup"><span data-stu-id="59efd-122">Therefore, your app should always check the access status via the [GetAccessStatus](https://docs.microsoft.com/uwp/api/windows.ui.notifications.management.usernotificationlistener.GetAccessStatus) method before executing code that uses the notfication listener.</span></span> <span data-ttu-id="59efd-123">Wenn der Benutzer den Zugriff widerruft, schlagen die APIs stillschweigend fehl, anstatt eine Ausnahme auszulösen (z. B. gibt die API zum Abrufen aller Benachrichtigungen einfach eine leere Liste zurück).</span><span class="sxs-lookup"><span data-stu-id="59efd-123">If the user revokes access, the APIs will silently fail rather than throwing an exception (for example, the API to get all notifications will simply return an empty list).</span></span>


## <a name="access-the-users-notifications"></a><span data-ttu-id="59efd-124">Zugriff auf Benachrichtigungen des Benutzers</span><span class="sxs-lookup"><span data-stu-id="59efd-124">Access the user's notifications</span></span>

<span data-ttu-id="59efd-125">Mit dem Listener können Sie eine Liste der aktuellen Benachrichtigungen des Benutzers erhalten.</span><span class="sxs-lookup"><span data-stu-id="59efd-125">With the notification listener, you can get a list of the user's current notifications.</span></span> <span data-ttu-id="59efd-126">Rufen Sie einfach die Methode [GetNotificationsAsync](https://docs.microsoft.com/uwp/api/windows.ui.notifications.management.usernotificationlistener.GetNotificationsAsync) auf und geben Sie den Typ der Benachrichtigungen an, die Sie erhalten möchten (derzeit werden nur Popup-Benachrichtigungen unterstützt).</span><span class="sxs-lookup"><span data-stu-id="59efd-126">Simply call the [GetNotificationsAsync](https://docs.microsoft.com/uwp/api/windows.ui.notifications.management.usernotificationlistener.GetNotificationsAsync) method, and specify the type of notifications you want to get (currently, the only type of notifications supported are toast notifications).</span></span>

```csharp
// Get the toast notifications
IReadOnlyList<UserNotification> notifs = await listener.GetNotificationsAsync(NotificationKinds.Toast);
```


## <a name="displaying-the-notifications"></a><span data-ttu-id="59efd-127">Anzeigen der Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="59efd-127">Displaying the notifications</span></span>

<span data-ttu-id="59efd-128">Jede Benachrichtigung wird als [UserNotification](https://docs.microsoft.com/uwp/api/windows.ui.notifications.usernotification) dargestellt, die Informationen über die App, von der die Benachrichtigung stammt, den Zeitpunkt der Erstellung der Benachrichtigung, die Benachrichtigungs-ID und die Benachrichtigung selbst enthält.</span><span class="sxs-lookup"><span data-stu-id="59efd-128">Each notification is represented as a [UserNotification](https://docs.microsoft.com/uwp/api/windows.ui.notifications.usernotification), which provides information about the app that the notification is from, the time the notification was created, the notification's ID, and the notification itself.</span></span>

```csharp
public sealed class UserNotification
{
    public AppInfo AppInfo { get; }
    public DateTimeOffset CreationTime { get; }
    public uint Id { get; }
    public Notification Notification { get; }
}
```

<span data-ttu-id="59efd-129">Die [AppInfo](https://docs.microsoft.com/uwp/api/windows.ui.notifications.usernotification.AppInfo) -Eigenschaft enthält die Informationen, die mit der Benachrichtigung angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="59efd-129">The [AppInfo](https://docs.microsoft.com/uwp/api/windows.ui.notifications.usernotification.AppInfo) property provides the info you need to display the notification.</span></span>

> [!NOTE]
> <span data-ttu-id="59efd-130">Wir empfehlen, Ihren gesamten Code für die Verarbeitung einer einzelnen Benachrichtigung von einem Try/Catch zu umschließen, falls beim Erfassen einer einzelnen Benachrichtigung eine unerwartete Ausnahme auftritt.</span><span class="sxs-lookup"><span data-stu-id="59efd-130">We recommend surrounding all your code for processing a single notification in a try/catch, in case an unexpected exception occurs when you are capturing a single notification.</span></span> <span data-ttu-id="59efd-131">Das Anzeigen von anderen Benachrichtigungen sollte nicht komplett fehlschlagen, nur weil ein Problem mit einer bestimmten Benachrichtigung aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="59efd-131">You shouldn't completely fail to display other notifications just because of an issue with one specific notification.</span></span>

```csharp
// Select the first notification
UserNotification notif = notifs[0];
 
// Get the app's display name
string appDisplayName = notif.AppInfo.DisplayInfo.DisplayName;
 
// Get the app's logo
BitmapImage appLogo = new BitmapImage();
RandomAccessStreamReference appLogoStream = notif.AppInfo.DisplayInfo.GetLogo(new Size(16, 16));
await appLogo.SetSourceAsync(await appLogoStream.OpenReadAsync());
```

<span data-ttu-id="59efd-132">Der Inhalt der Benachrichtigung selbst, wie z. B. der Benachrichtigungstext, ist in der Eigenschaft [Notification](https://docs.microsoft.com/uwp/api/windows.ui.notifications.usernotification.Notification) enthalten.</span><span class="sxs-lookup"><span data-stu-id="59efd-132">The content of the notification itself, such as the notification text, is contained in the [Notification](https://docs.microsoft.com/uwp/api/windows.ui.notifications.usernotification.Notification) property.</span></span> <span data-ttu-id="59efd-133">Diese Eigenschaft enthält den visuellen Teil der Benachrichtigung.</span><span class="sxs-lookup"><span data-stu-id="59efd-133">This property contains the visual portion of the notification.</span></span> <span data-ttu-id="59efd-134">(Wenn Sie mit dem Senden von Benachrichtigungen unter Windows vertraut sind, werden Sie feststellen, dass die [Visual](https://docs.microsoft.com/uwp/api/windows.ui.notifications.notification.Visual)- und [Visual Bindings](https://docs.microsoft.com/uwp/api/windows.ui.notifications.notificationvisual.Bindings)-Eigenschaften im [Notification](https://docs.microsoft.com/uwp/api/windows.ui.notifications.notification)-Objekt dem entsprechen, was Entwickler beim anzeigen einer Benachrichtigung senden.)</span><span class="sxs-lookup"><span data-stu-id="59efd-134">(If you are familiar with sending notifications on Windows, you will notice that the [Visual](https://docs.microsoft.com/uwp/api/windows.ui.notifications.notification.Visual) and [Visual.Bindings](https://docs.microsoft.com/uwp/api/windows.ui.notifications.notificationvisual.Bindings) properties in the [Notification](https://docs.microsoft.com/uwp/api/windows.ui.notifications.notification) object correspond to what developers send when popping a notification.)</span></span>

<span data-ttu-id="59efd-135">Wir wollen nach der Toast-Bindung suchen (für fehlersicheren Code sollten Sie überprüfen, ob die Bindung nicht null ist).</span><span class="sxs-lookup"><span data-stu-id="59efd-135">We want to look for the toast binding (for error-proof code, you should check that the binding isn't null).</span></span> <span data-ttu-id="59efd-136">Aus der Bindung können Sie die Textelemente entnehmen.</span><span class="sxs-lookup"><span data-stu-id="59efd-136">From the binding, you can obtain the text elements.</span></span> <span data-ttu-id="59efd-137">Sie können sich beliebig viele Textelemente anzeigen lassen.</span><span class="sxs-lookup"><span data-stu-id="59efd-137">You can choose to display as many text elements as you would like.</span></span> <span data-ttu-id="59efd-138">(Im Idealfall sollten Sie alle anzeigen.) Sie können die Textelemente unterschiedlich behandeln, z. B. das erste als Titeltext und nachfolgende Elemente als Fließtext.</span><span class="sxs-lookup"><span data-stu-id="59efd-138">(Ideally, you should display them all.) You can choose to treat the text elements differently; for example, treat the first one as title text, and subsequent elements as body text.</span></span>

```csharp
// Get the toast binding, if present
NotificationBinding toastBinding = notif.Notification.Visual.GetBinding(KnownNotificationBindings.ToastGeneric);
 
if (toastBinding != null)
{
    // And then get the text elements from the toast binding
    IReadOnlyList<AdaptiveNotificationText> textElements = toastBinding.GetTextElements();
 
    // Treat the first text element as the title text
    string titleText = textElements.FirstOrDefault()?.Text;
 
    // We'll treat all subsequent text elements as body text,
    // joining them together via newlines.
    string bodyText = string.Join("\n", textElements.Skip(1).Select(t => t.Text));
}
```


## <a name="remove-a-specific-notification"></a><span data-ttu-id="59efd-139">Eine bestimmte Benachrichtigung entfernen</span><span class="sxs-lookup"><span data-stu-id="59efd-139">Remove a specific notification</span></span>

<span data-ttu-id="59efd-140">Wenn Ihr Wearable oder Service es dem Benutzer erlaubt, Benachrichtigungen zu schließen, können Sie die Benachrichtigung entfernen, so dass der Benutzer sie später nicht mehr auf seinem Telefon oder PC sieht.</span><span class="sxs-lookup"><span data-stu-id="59efd-140">If your wearable or service allows the user to dismiss notifications, you can remove the actual notification so the user doesn't see it later on their phone or PC.</span></span> <span data-ttu-id="59efd-141">Geben Sie einfach die Benachrichtigungs-ID (die Sie vom Objekt [UserNotification](https://docs.microsoft.com/uwp/api/windows.ui.notifications.usernotification) erhalten haben) der Benachrichtigung an, die Sie entfernen möchten:</span><span class="sxs-lookup"><span data-stu-id="59efd-141">Simply provide the notification ID (obtained from the [UserNotification](https://docs.microsoft.com/uwp/api/windows.ui.notifications.usernotification) object) of the notification you'd like to remove:</span></span> 

```csharp
// Remove the notification
listener.RemoveNotification(notifId);
```


## <a name="clear-all-notifications"></a><span data-ttu-id="59efd-142">Alle Benachrichtigungen löschen</span><span class="sxs-lookup"><span data-stu-id="59efd-142">Clear all notifications</span></span>

<span data-ttu-id="59efd-143">Die Methode [UserNotificationListener.ClearNotifications](https://docs.microsoft.com/uwp/api/windows.ui.notifications.management.usernotificationlistener.ClearNotifications) löscht alle Benachrichtigungen des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="59efd-143">The [UserNotificationListener.ClearNotifications](https://docs.microsoft.com/uwp/api/windows.ui.notifications.management.usernotificationlistener.ClearNotifications) method clears all the user's notifications.</span></span> <span data-ttu-id="59efd-144">Verwenden Sie diese Methode mit Vorsicht.</span><span class="sxs-lookup"><span data-stu-id="59efd-144">Use this method with caution.</span></span> <span data-ttu-id="59efd-145">Sie sollten nur dann alle Benachrichtigungen löschen, wenn in Ihrem Wearable oder Service ALLE Benachrichtigungen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="59efd-145">You should only clear all notifications if your wearable or service displays ALL notifications.</span></span> <span data-ttu-id="59efd-146">Wenn Ihr Wearable oder Service nur bestimmte Benachrichtigungen anzeigt, wenn der Benutzer auf die Schaltfläche „?Benachrichtigungen löschen“ klickt, erwartet der Benutzer lediglich, dass bestimmte Benachrichtigungen entfernt werden. Wenn Sie jedoch die [ClearNotifications](https://docs.microsoft.com/uwp/api/windows.ui.notifications.management.usernotificationlistener.ClearNotifications)-Methode aufrufen, werden tatsächlich alle Benachrichtigungen, einschließlich der Benachrichtigungen, die nicht angezeigt werden, entfernt.</span><span class="sxs-lookup"><span data-stu-id="59efd-146">If your wearable or service only displays certain notifications, when the user clicks your "Clear notifications" button, the user is only expecting those specific notifications to be removed; however, calling the [ClearNotifications](https://docs.microsoft.com/uwp/api/windows.ui.notifications.management.usernotificationlistener.ClearNotifications) method would actually cause all the notifications, including ones that your wearable or service wasn't displaying, to be removed.</span></span>

```csharp
// Clear all notifications. Use with caution.
listener.ClearNotifications();
```


## <a name="background-task-for-notification-addeddismissed"></a><span data-ttu-id="59efd-147">Hintergrundaufgabe für hinzugefügte/geschlossene Benachrichtigung</span><span class="sxs-lookup"><span data-stu-id="59efd-147">Background task for notification added/dismissed</span></span>

<span data-ttu-id="59efd-148">Eine gängige Methode, um eine Anwendung zum Abrufen von Benachrichtigungen zu erstellen, ist die Einrichtung einer Hintergrundaufgabe, damit Sie wissen, wann eine Benachrichtigung hinzugefügt oder geschlossen wurde, unabhängig davon, ob Ihre Anwendung gerade läuft.</span><span class="sxs-lookup"><span data-stu-id="59efd-148">A common way to enable an app to listen to notifications is to set up a background task, so that you can know when a notification was added or dismissed regardless of whether your app is currently running.</span></span>

<span data-ttu-id="59efd-149">Dank des [gemeinsamen Prozessmodells](../../../launch-resume/create-and-register-an-inproc-background-task.md), das im Anniversary Update hinzugefügt wurde, ist das Hinzufügen von Hintergrundaufgaben relativ einfach.</span><span class="sxs-lookup"><span data-stu-id="59efd-149">Thanks to the [single process model](../../../launch-resume/create-and-register-an-inproc-background-task.md) added in the Anniversary Update, adding background tasks is fairly simple.</span></span> <span data-ttu-id="59efd-150">Nachdem Sie im Code Ihrer Hauptanwendung den Zugriff des Benutzers auf Notification-Listener erhalten haben und Zugriff auf die Ausführung von Hintergrundaufgaben erhalten haben, registrieren Sie einfach eine neue Hintergrundaufgabe und setzen Sie den [UserNotificationChangedTrigger](https://docs.microsoft.com/uwp/api/windows.applicationmodel.background.usernotificationchangedtrigger) mit der [Toast-Benachrichtigung](https://docs.microsoft.com/uwp/api/windows.ui.notifications.notificationkinds).</span><span class="sxs-lookup"><span data-stu-id="59efd-150">In your main app's code, after you have obtained the user's access to Notification Listener and obtained access to run background tasks, simply register a new background task, and set the [UserNotificationChangedTrigger](https://docs.microsoft.com/uwp/api/windows.applicationmodel.background.usernotificationchangedtrigger) using the [Toast notification kind](https://docs.microsoft.com/uwp/api/windows.ui.notifications.notificationkinds).</span></span>

```csharp
// TODO: Request/check Listener access via UserNotificationListener.Current.RequestAccessAsync
 
// TODO: Request/check background task access via BackgroundExecutionManager.RequestAccessAsync
 
// If background task isn't registered yet
if (!BackgroundTaskRegistration.AllTasks.Any(i => i.Value.Name.Equals("UserNotificationChanged")))
{
    // Specify the background task
    var builder = new BackgroundTaskBuilder()
    {
        Name = "UserNotificationChanged"
    };
 
    // Set the trigger for Listener, listening to Toast Notifications
    builder.SetTrigger(new UserNotificationChangedTrigger(NotificationKinds.Toast));
 
    // Register the task
    builder.Register();
}
```

<span data-ttu-id="59efd-151">Dann überschreiben Sie in Ihrer App.xaml.cs die [OnBackgroundActivated](https://docs.microsoft.com/uwp/api/windows.ui.xaml.application.OnBackgroundActivated)-Methode, falls Sie es noch nicht getan haben, und verwenden eine Switch-Anweisung für den Tasknamen, um festzustellen, welche Ihrer vielen Trigger für Hintergrundaufgaben aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="59efd-151">Then, in your App.xaml.cs, override the [OnBackgroundActivated](https://docs.microsoft.com/uwp/api/windows.ui.xaml.application.OnBackgroundActivated) method if you haven't yet, and use a switch statement on the task name to determine which of your many background task triggers was invoked.</span></span>

```csharp
protected override async void OnBackgroundActivated(BackgroundActivatedEventArgs args)
{
    var deferral = args.TaskInstance.GetDeferral();
 
    switch (args.TaskInstance.Task.Name)
    {
        case "UserNotificationChanged":
            // Call your own method to process the new/removed notifications
            // The next section of documentation discusses this code
            await MyWearableHelpers.SyncNotifications();
            break;
    }
 
    deferral.Complete();
}
```

<span data-ttu-id="59efd-152">Die Hintergrundaufgabe ist lediglich ein Hinweis: Sie gibt keine Auskunft darüber, welche Benachrichtigung hinzugefügt oder entfernt wurde.</span><span class="sxs-lookup"><span data-stu-id="59efd-152">The background task is simply a "shoulder tap": it doesn't provide any information about which specific notification was added or removed.</span></span> <span data-ttu-id="59efd-153">Wenn Ihre Hintergrundaufgabe ausgelöst wird, sollten Sie die Benachrichtigungen auf Ihrem Wearable synchronisieren, damit sie die Benachrichtigungen in der Plattform widerspiegeln.</span><span class="sxs-lookup"><span data-stu-id="59efd-153">When your background task is triggered, you should sync the notifications on your wearable so that they reflect the notifications in the platform.</span></span> <span data-ttu-id="59efd-154">Wenn Ihre Hintergrundaufgabe fehlschlägt, können Sie beim nächsten Ausführen Ihrer Hintergrundaufgabe immer noch Benachrichtigungen über Ihre Wearable wiederherstellen.</span><span class="sxs-lookup"><span data-stu-id="59efd-154">This ensures that if your background task fails, notifications on your wearable can still be recovered the next time your background task executes.</span></span>

`SyncNotifications` <span data-ttu-id="59efd-155">ist eine Methode, die Sie implementieren. Der nächste Abschnitt zeigt wie.</span><span class="sxs-lookup"><span data-stu-id="59efd-155">is a method you implement; the next section shows how.</span></span> 


## <a name="determining-which-notifications-were-added-and-removed"></a><span data-ttu-id="59efd-156">Ermitteln welche Benachrichtigungen hinzugefügt und entfernt wurden</span><span class="sxs-lookup"><span data-stu-id="59efd-156">Determining which notifications were added and removed</span></span>

<span data-ttu-id="59efd-157">In Ihrer `SyncNotifications`-Methode müssen Sie das Delta zwischen Ihrer aktuellen Benachrichtigungssammlung und den Benachrichtigungen in der Plattform berechnen (Benachrichtigungen mit Ihrem Wearable synchronisieren), um festzustellen, welche Benachrichtigungen hinzugefügt oder entfernt wurden.</span><span class="sxs-lookup"><span data-stu-id="59efd-157">In your `SyncNotifications` method, to determine which notifications have been added or removed (syncing notifications with your wearable), you have to calculate the delta between your current notification collection, and the notifications in the platform.</span></span>

```csharp
// Get all the current notifications from the platform
IReadOnlyList<UserNotification> userNotifications = await listener.GetNotificationsAsync(NotificationKinds.Toast);
 
// Obtain the notifications that our wearable currently has displayed
IList<uint> wearableNotificationIds = GetNotificationsOnWearable();
 
// Copy the currently displayed into a list of notification ID's to be removed
var toBeRemoved = new List<uint>(wearableNotificationIds);
 
// For each notification in the platform
foreach (UserNotification userNotification in userNotifications)
{
    // If we've already displayed this notification
    if (wearableNotificationIds.Contains(userNotification.Id))
    {
        // We want to KEEP it displayed, so take it out of the list
        // of notifications to remove.
        toBeRemoved.Remove(userNotification.Id);
    }
 
    // Othwerise it's a new notification
    else
    {
        // Display it on the Wearable
        SendNotificationToWearable(userNotification);
    }
}
 
// Now our toBeRemoved list only contains notification ID's that no longer exist in the platform.
// So we will remove all those notifications from the wearable.
foreach (uint id in toBeRemoved)
{
    RemoveNotificationFromWearable(id);
}
```


## <a name="foreground-event-for-notification-addeddismissed"></a><span data-ttu-id="59efd-158">Vordergrundereignis für hinzugefügt/geschlossene Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="59efd-158">Foreground event for notification added/dismissed</span></span>

> [!IMPORTANT] 
> <span data-ttu-id="59efd-159">Bekanntes Problem: das Ereignis im Vordergrund bewirkt eine Schleife CPU auf die aktuellen Versionen von Windows und zuvor davor nicht funktioniert.</span><span class="sxs-lookup"><span data-stu-id="59efd-159">Known issue: The foreground event will cause a CPU loop on recent versions of Windows, and previously did not work before that.</span></span> <span data-ttu-id="59efd-160">Verwenden Sie nicht das Ereignis im Vordergrund.</span><span class="sxs-lookup"><span data-stu-id="59efd-160">Do NOT use the foreground event.</span></span> <span data-ttu-id="59efd-161">Ein bevorstehenden Windows Update werden wir dieses Problem beheben.</span><span class="sxs-lookup"><span data-stu-id="59efd-161">In an upcoming update to Windows, we will fix this.</span></span>

<span data-ttu-id="59efd-162">Verwenden Sie anstelle das vordergrundereignis für eine Hintergrundaufgabe [gemeinsamen Prozessmodells](../../../launch-resume/create-and-register-an-inproc-background-task.md) den zuvor aufgeführten Code.</span><span class="sxs-lookup"><span data-stu-id="59efd-162">Instead of using the foreground event, use the code shown earlier for a [single process model](../../../launch-resume/create-and-register-an-inproc-background-task.md) background task.</span></span> <span data-ttu-id="59efd-163">Zudem wird die Hintergrundaufgabe können Sie Änderung ereignisbenachrichtigungen beide erhalten, während Ihre app geschlossen ist oder ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="59efd-163">The background task will also allow you to receive change event notifications both while your app is closed or running.</span></span>

```csharp
// Subscribe to foreground event (DON'T USE THIS)
listener.NotificationChanged += Listener_NotificationChanged;
 
private void Listener_NotificationChanged(UserNotificationListener sender, UserNotificationChangedEventArgs args)
{
    // NOTE: This event WILL CAUSE CPU LOOPS, DO NOT USE. Use the background task instead.
}
```


## <a name="howto-fixdelays-in-the-background-task"></a><span data-ttu-id="59efd-164">So wird's gemacht Fixdelays in der Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="59efd-164">Howto fixdelays in the background task</span></span>

<span data-ttu-id="59efd-165">Beim Testen Ihrer Anwendung werden Sie möglicherweise feststellen, dass die Hintergrundaufgabe manchmal verzögert ist und mehrere Minuten lang nicht ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="59efd-165">When testing your app, you might notice that the background task is sometimes delayed, and doesn't trigger for several minutes.</span></span> <span data-ttu-id="59efd-166">Um dieses Problem zu beheben, sollten Sie fordern Sie den Benutzer Togo auf den Systemeinstellungen -> System -> Akku -> Akkunutzung nach app, suchen Sie Ihre app in der Liste, wählen Sie ihn und ändern Sie den Wert "Immer im Hintergrund zugelassen" sein.</span><span class="sxs-lookup"><span data-stu-id="59efd-166">To fix this, you'll want to prompt the user togo to the system settings -> System -> Battery -> Battery usage by app, find your app in the list,select it, and change it to be"Always allowed in background".</span></span><span data-ttu-id="59efd-167">Danach sollte die Hintergrundaufgabe immer innerhalb einer Sekunde der Benachrichtigung angestoßen werden.</span><span class="sxs-lookup"><span data-stu-id="59efd-167">After this,the background task should always be triggered within around a second of the notification being received.</span></span>