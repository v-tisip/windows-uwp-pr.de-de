---
author: manoskow
Description: Learn how to group notifications in Action Center using collections.
title: Popupsammlungen
label: Toast Collections
template: detail.hbs
ms.author: mijacobs
ms.date: 05/16/2018
ms.topic: article
keywords: Windows10, UWP, Benachrichtigungen, Sammlungen, Sammlung, Gruppenbenachrichtigungen, Gruppieren von Benachrichtigungen, gruppieren, organisieren, Info-Center, Popup
ms.localizationpriority: medium
ms.openlocfilehash: be7c4ec2e9a47eeeb00663ae94f89e44c6751352
ms.sourcegitcommit: cd00bb829306871e5103db481cf224ea7fb613f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5862114"
---
# <a name="grouping-toast-notifications-with-collections"></a><span data-ttu-id="17dbd-103">Gruppieren von Popupbenachrichtigungen mit Sammlungen</span><span class="sxs-lookup"><span data-stu-id="17dbd-103">Grouping toast notifications with collections</span></span>
<span data-ttu-id="17dbd-104">Verwenden Sie Sammlungen, um Ihre App-Popups im Info-Center zu organisieren.</span><span class="sxs-lookup"><span data-stu-id="17dbd-104">Use collections to organize your app's toasts in Action Center.</span></span> <span data-ttu-id="17dbd-105">Mithilfe von Sammlungen können Benutzer Informationen im Info-Center leichter finden und Entwickler können ihre Benachrichtigungen besser verwalten.</span><span class="sxs-lookup"><span data-stu-id="17dbd-105">Collections help users locate information within Action Center more easily and allow for developers to better manage their notifications.</span></span>  <span data-ttu-id="17dbd-106">Die folgenden APIs ermöglichen das Entfernen, Erstellen und Aktualisieren von Benachrichtigungssammlungen.</span><span class="sxs-lookup"><span data-stu-id="17dbd-106">The APIs below allow for removing, creating, and updating notification collections.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="17dbd-107">**Erfordert Creators Update**: Sie müssen als Ziel das SDK 15063 angeben und Build 15063 oder höher ausführen, um Popupbenachrichtigungen zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="17dbd-107">**Requires Creators Update**: You must target SDK 15063 and be running build 15063 or higher to use toast collections.</span></span> <span data-ttu-id="17dbd-108">Zugehörige APIs: [Windows.UI.Notifications.ToastCollection](https://docs.microsoft.com/en-us/uwp/api/windows.ui.notifications.toastcollection) und [Windows.UI.Notifications.ToastCollectionManager](https://docs.microsoft.com/en-us/uwp/api/windows.ui.notifications.toastcollectionmanager)</span><span class="sxs-lookup"><span data-stu-id="17dbd-108">Related APIs include [Windows.UI.Notifications.ToastCollection](https://docs.microsoft.com/en-us/uwp/api/windows.ui.notifications.toastcollection), and [Windows.UI.Notifications.ToastCollectionManager](https://docs.microsoft.com/en-us/uwp/api/windows.ui.notifications.toastcollectionmanager)</span></span>

<span data-ttu-id="17dbd-109">Sie sehen das folgende Beispiel einer Messaging-App, die die Benachrichtigungen basierend auf der Chatgruppe trennt. Jeder Titel (Comp Sci 160A Project Chat, Direct Messages, Lacrosse Team Chat) ist eine separate Sammlung.</span><span class="sxs-lookup"><span data-stu-id="17dbd-109">You can see the example below with a messaging app that separates the notifications based on the chat group; each title (Comp Sci 160A Project Chat, Direct Messages, Lacrosse Team Chat) is a separate collection.</span></span>  <span data-ttu-id="17dbd-110">Beachten Sie, wie die Benachrichtigungen unterschiedlich gruppiert werden, als wären sie von einer separaten App, obwohl sie alle Benachrichtigungen von derselben App sind.</span><span class="sxs-lookup"><span data-stu-id="17dbd-110">Notice how the notifications are distinctly grouped as if they were from a seperate app, even though they are all notifications from the same app.</span></span>  <span data-ttu-id="17dbd-111">Wenn Sie Benachrichtigungen auf raffiniertere Art organisieren möchten, lesen Sie [Popup-Header](toast-headers.md).</span><span class="sxs-lookup"><span data-stu-id="17dbd-111">If you are looking for a more subtle way to organize your notifications, see [toast headers](toast-headers.md).</span></span>  
![Sammlungsbeispiel mit zwei unterschiedlichen Gruppen von Benachrichtigungen](images/toast-collection-example.png)

## <a name="creating-collections"></a><span data-ttu-id="17dbd-113">Erstellen von Sammlungen</span><span class="sxs-lookup"><span data-stu-id="17dbd-113">Creating collections</span></span>
<span data-ttu-id="17dbd-114">Bei der Erstellung jeder Sammlung müssen Sie einen Anzeigenamen und ein Symbol angeben, die als Teil des Sammlungstitels im Info-Center angezeigt werden, wie in der Abbildung oben dargestellt.</span><span class="sxs-lookup"><span data-stu-id="17dbd-114">When creating each collection, you are required to provide a display name and an icon, which are displayed inside Action Center as part of the collection's title, as shown in the image above.</span></span> <span data-ttu-id="17dbd-115">Sammlungen erfordern außerdem ein Start-Argument, damit die App zur richtigen Stelle in der App navigieren kann, wenn ein Benutzer auf den Titel der Sammlung klickt.</span><span class="sxs-lookup"><span data-stu-id="17dbd-115">Collections also require a launch argument to help the app navigate to the right location within the app when the collection’s title is clicked on by the user.</span></span>  

### <a name="create-a-collection"></a><span data-ttu-id="17dbd-116">Erstellen einer Sammlung</span><span class="sxs-lookup"><span data-stu-id="17dbd-116">Create a collection</span></span>

``` csharp 
public const string toastCollectionId = "ToastCollection";

// Create a toast collection
public async void CreateToastCollection()
{
    string displayName = "Work Email"; 
    string launchArg = "NavigateToWorkEmailInbox"; 
    Uri icon = new Windows.Foundation.Uri("ms-appx:///Assets/workEmail.png");

    // Constructor
    ToastCollection workEmailToastCollection = new ToastCollection(MainPage.toastCollectionId, 
        displayName,
        launchArg, 
        icon);

    // Calls the platform to create the collection
    await ToastNotificationManager.GetDefault().GetToastCollectionManager().SaveToastCollectionAsync(workEmailToastCollection);                                 
}
```

## <a name="sending-notifications-to-a-collection"></a><span data-ttu-id="17dbd-117">Senden von Benachrichtigungen an eine Sammlung</span><span class="sxs-lookup"><span data-stu-id="17dbd-117">Sending notifications to a collection</span></span>
<span data-ttu-id="17dbd-118">Wir betrachten das Senden von Benachrichtigungen aus drei verschiedenen Popup-Pipelines: lokal, geplant und push.</span><span class="sxs-lookup"><span data-stu-id="17dbd-118">We will cover sending notifications from three different toast pipelines: local, scheduled, and push.</span></span>  <span data-ttu-id="17dbd-119">Für jedes dieser Beispiele erstellen wir ein Beispielpopup, das mit dem nachfolgenden Code sofort gesendet wird. Dann konzentrieren wir uns darauf, wie das Popup über jede Pipeline einer Sammlung hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="17dbd-119">For each of these examples we will be creating a sample toast to send with the code immediately below, then we will focus on how to add the toast to a collection via each pipeline.</span></span>

<span data-ttu-id="17dbd-120">Erstellen der Benachrichtigungsnutzlast:</span><span class="sxs-lookup"><span data-stu-id="17dbd-120">Construct the notification payload:</span></span>

``` csharp
public const string toastCollectionId = "MyToastCollection";

public async void SendToastToToastCollection()
{
    // Construct the notification Content
    string toastXmlString = 
        $@"<toast launch=’’>
            <visual>
                <binding template=’ToastGeneric’>
                    <text>Hello,</text>
                    <text>it’s me</text>
                </binding>
            </visual>
        </toast>";
    // Convert to XML
    XmlDocument toastXml = new XmlDocment();
    toastXml.LoadXml(toastXmlString);
    ToastNotification toast = new ToastNotification(toastXml);
```

### <a name="send-a-toast-to-a-collection"></a><span data-ttu-id="17dbd-121">Senden eines Popups an eine Sammlung</span><span class="sxs-lookup"><span data-stu-id="17dbd-121">Send a toast to a collection</span></span>

```csharp
// Get the collection notifier
var notifier = await ToastNotificationManager.GetDefault().GetToastNotifierForToastCollectionIdAsync(MainPage.toastCollectionId);

// And show the toast
notifier.Show(toast);
```

### <a name="add-a-scheduled-toast-to-a-collection"></a><span data-ttu-id="17dbd-122">Hinzufügen eines geplanten Popups zu einer Sammlung</span><span class="sxs-lookup"><span data-stu-id="17dbd-122">Add a scheduled toast to a collection</span></span>

``` csharp
// Create scheduled toast from XML above
ScheduledToastNotification scheduledToast = new ScheduledToastNotification(toastXml, DateTimeOffset.Now.AddSeconds(10));

// Get notifier
var notifier = await ToastNotificationManager.GetDefault().GetToastNotifierForToastCollectionIdAsync(MainPage.toastCollectionId);
    
// Add to schedule
notifier.AddToSchedule(scheduledToast);
```

### <a name="send-a-push-toast-to-a-collection"></a><span data-ttu-id="17dbd-123">Senden eines Push-Popups an eine Sammlung</span><span class="sxs-lookup"><span data-stu-id="17dbd-123">Send a push toast to a collection</span></span>
<span data-ttu-id="17dbd-124">Für Push-Popups müssen Sie den X-WNS-CollectionId-Header zur POST-Nachricht hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="17dbd-124">For push toasts, you need to add the X-WNS-CollectionId header to the POST message.</span></span>
```csharp
// Add header to HTTP request
request.Headers.Add("X-WNS-CollectionId", collectionId); 

```

## <a name="managing-collections"></a><span data-ttu-id="17dbd-125">Verwalten von Sammlungen</span><span class="sxs-lookup"><span data-stu-id="17dbd-125">Managing collections</span></span>
#### <a name="create-the-toast-collection-manager"></a><span data-ttu-id="17dbd-126">Erstellen der Popupsammlungsverwaltung</span><span class="sxs-lookup"><span data-stu-id="17dbd-126">Create the toast collection manager</span></span>
<span data-ttu-id="17dbd-127">Für die verbleibenden Codeausschnitte in diesem Abschnitt „Verwalten von Sammlungen“ verwenden wir den folgenden collectionManager.</span><span class="sxs-lookup"><span data-stu-id="17dbd-127">For the rest of the code snippets in this 'Managing Collections' section we will be using the collectionManager below.</span></span>
```csharp
ToastCollectionManger collectionManager = ToastNotificationManager.GetDefault().GetToastCollectionManager();
```

#### <a name="get-all-collections"></a><span data-ttu-id="17dbd-128">Abrufen aller Sammlungen</span><span class="sxs-lookup"><span data-stu-id="17dbd-128">Get all collections</span></span>

``` csharp
IReadOnlyList<ToastCollection> collections = await collectionManager.FindAllToastCollectionsAsync();
``` 

#### <a name="get-the-number-of-collections-created"></a><span data-ttu-id="17dbd-129">Abrufen der Anzahl der erstellten Sammlungen</span><span class="sxs-lookup"><span data-stu-id="17dbd-129">Get the number of collections created</span></span>

``` csharp
int toastCollectionCount = (await collectionManager.FindAllToastCollectionsAsync()).Count;
```

#### <a name="remove-a-collection"></a><span data-ttu-id="17dbd-130">Entfernen einer Sammlung</span><span class="sxs-lookup"><span data-stu-id="17dbd-130">Remove a collection</span></span>

``` csharp
await collectionManager.RemoveToastCollectionAsync(MainPage.toastCollectionId);
```

#### <a name="update-a-collection"></a><span data-ttu-id="17dbd-131">Aktualisieren einer Sammlung</span><span class="sxs-lookup"><span data-stu-id="17dbd-131">Update a collection</span></span>
<span data-ttu-id="17dbd-132">Sie können Sammlungen aktualisieren, indem Sie eine neue Sammlung mit derselben ID erstellen und die neue Instanz der Sammlung speichern.</span><span class="sxs-lookup"><span data-stu-id="17dbd-132">You can update collections by creating a new collection with the same ID and saving the new instance of the collection.</span></span>
``` csharp
string displayName = "Updated Display Name"; 
string launchArg = "UpdatedLaunchArgs"; 
Uri icon = new Windows.Foundation.Uri("ms-appx:///Assets/updatedPicture.png");

// Construct a new toast collection with the same collection id
ToastCollection updatedToastCollection = new ToastCollection(MainPage.toastCollectionId, 
            displayName,
            launchArg, 
            icon);

// Calls the platform to update the collection by saving the new instance
await collectionManager.SaveToastCollectionAsync(updatedToastCollection);                               
```
## <a name="managing-toasts-within-a-collection"></a><span data-ttu-id="17dbd-133">Verwalten von Popups in einer Sammlung</span><span class="sxs-lookup"><span data-stu-id="17dbd-133">Managing toasts within a collection</span></span>
#### <a name="group-and-tag-properties"></a><span data-ttu-id="17dbd-134">Gruppierungs- und Tag-Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="17dbd-134">Group and tag properties</span></span>
<span data-ttu-id="17dbd-135">Die Gruppierungs- und Tag-Eigenschaften identifizieren zusammen eine Benachrichtigung in einer Sammlung eindeutig.</span><span class="sxs-lookup"><span data-stu-id="17dbd-135">The group and tag properties together uniquely identify a notification within a collection.</span></span>  <span data-ttu-id="17dbd-136">Gruppe (und Tag) dienen als zusammengesetzter primärer Schlüssel (mehr als eine ID) zur Identifizierung der Benachrichtigung.</span><span class="sxs-lookup"><span data-stu-id="17dbd-136">Group (and Tag) serves as a composite primary key (more than one identifier) to identify your notification.</span></span> <span data-ttu-id="17dbd-137">Wenn Sie z.B. eine Benachrichtigung entfernen oder ersetzen möchten, müssen Sie angeben können, *welche Benachrichtigung* entfernt/ersetzt werden soll. Dies erreichen Sie durch Angabe von Tag und Gruppe.</span><span class="sxs-lookup"><span data-stu-id="17dbd-137">For example, if you want to remove or replace a notification, you have to be able to specify *what notification* you want to remove/replace; you do that by specifying the Tag and Group.</span></span> <span data-ttu-id="17dbd-138">Ein Beispiel ist eine Messaging-App.</span><span class="sxs-lookup"><span data-stu-id="17dbd-138">An example is a messaging app.</span></span>  <span data-ttu-id="17dbd-139">Der Entwickler könnte die Unterhaltungs-ID als Gruppe und die Nachrichten-ID als Tag verwenden.</span><span class="sxs-lookup"><span data-stu-id="17dbd-139">The developer could use the conversation ID as the Group, and the message ID as the Tag.</span></span>

#### <a name="remove-a-toast-from-a-collection"></a><span data-ttu-id="17dbd-140">Entfernen eines Popups aus einer Sammlung</span><span class="sxs-lookup"><span data-stu-id="17dbd-140">Remove a toast from a collection</span></span>
<span data-ttu-id="17dbd-141">Sie können einzelne Popups mithilfe der Tag- und Gruppen-IDs entfernen oder alle Popups in einer Sammlung löschen.</span><span class="sxs-lookup"><span data-stu-id="17dbd-141">You can remove individual toasts using the tag and group IDs, or clear all toasts in a collection.</span></span>
``` csharp
// Get the history
var collectionHistory = await ToastNotificationManager.GetDefault().GetHistoryForToastCollectionAsync(MainPage.toastCollectionId);

// Remove toast
collectionHistory.Remove(tag, group); 
```

#### <a name="clear-all-toasts-within-a-collection"></a><span data-ttu-id="17dbd-142">Löschen aller Popups in einer Sammlung</span><span class="sxs-lookup"><span data-stu-id="17dbd-142">Clear all toasts within a collection</span></span>
``` csharp
// Get the history
var collectionHistory = await ToastNotificationManager.GetDefault().GetHistoryForToastCollectionAsync(MainPage.toastCollectionId);

// Remove toast
collectionHistory.Clear();
```


## <a name="collections-in-notifications-visualizer"></a><span data-ttu-id="17dbd-143">Sammlungen im Notifications Visualizer</span><span class="sxs-lookup"><span data-stu-id="17dbd-143">Collections in Notifications Visualizer</span></span>
<span data-ttu-id="17dbd-144">Sie können beim Entwerfen Ihrer Sammlungen das Tool [Notifications Visualizer](notifications-visualizer.md) verwenden.</span><span class="sxs-lookup"><span data-stu-id="17dbd-144">You can use the [Notifications Visualizer](notifications-visualizer.md) tool to help design your collections.</span></span> <span data-ttu-id="17dbd-145">Führen Sie die unten beschriebenen Schritte aus.</span><span class="sxs-lookup"><span data-stu-id="17dbd-145">Follow the steps below:</span></span>

* <span data-ttu-id="17dbd-146">Klicken Sie in der unteren rechten Ecke auf das Zahnradsymbol.</span><span class="sxs-lookup"><span data-stu-id="17dbd-146">Click on the gear icon in the bottom right corner.</span></span> 
* <span data-ttu-id="17dbd-147">Wählen Sie „Popupsammlungen“ aus.</span><span class="sxs-lookup"><span data-stu-id="17dbd-147">Select 'Toast collections'.</span></span>
* <span data-ttu-id="17dbd-148">Über der Vorschau des Popups wird das Dropdownmenü „Popupsammlungen“ angezeigt.</span><span class="sxs-lookup"><span data-stu-id="17dbd-148">Above the preview of the toast, there is a 'Toast Collection' dropdown menu.</span></span> <span data-ttu-id="17dbd-149">Wählen Sie die Option zum Verwalten von Sammlungen aus.</span><span class="sxs-lookup"><span data-stu-id="17dbd-149">Select manage collections.</span></span>
* <span data-ttu-id="17dbd-150">Klicken Sie auf „Sammlung hinzufügen“, geben Sie die Details zur Sammlung an, und speichern Sie.</span><span class="sxs-lookup"><span data-stu-id="17dbd-150">Click 'Add collection', fill out the details for the collection, and save.</span></span>
* <span data-ttu-id="17dbd-151">Sie können weitere Sammlungen hinzufügen oder die Option zum Verwalten von Sammlungen deaktivieren, um zum Hauptbildschirm zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="17dbd-151">You can add more collections, or click off of the manage collections box to return to the main screen.</span></span>
* <span data-ttu-id="17dbd-152">Wählen Sie im Dropdownmenü „Popupsammlung“ die Sammlung aus, der Sie das Popup hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="17dbd-152">Select the collection you want to add the toast to from the 'Toast Collection' dropdown menu.</span></span>
* <span data-ttu-id="17dbd-153">Wenn das Popup ausgelöst wird, wird es der entsprechenden Sammlung im Info-Center hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="17dbd-153">When you fire the toast, it will be added to the appropriate collection in Action Center.</span></span>


## <a name="other-details"></a><span data-ttu-id="17dbd-154">Weitere Details</span><span class="sxs-lookup"><span data-stu-id="17dbd-154">Other details</span></span>
<span data-ttu-id="17dbd-155">Die Popupsammlungen, die Sie erstellen, werden auch in den Benachrichtigungseinstellungen des Benutzers angezeigt.</span><span class="sxs-lookup"><span data-stu-id="17dbd-155">The toast collections that you create will also be reflected in the user's notification settings.</span></span>  <span data-ttu-id="17dbd-156">Benutzer können die Einstellungen für jede einzelne Sammlung umschalten, um diese Untergruppen zu aktivieren oder zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="17dbd-156">Users can toggle the settings for each individual collection to turn these subgroups on or off.</span></span>  <span data-ttu-id="17dbd-157">Wenn Benachrichtigungen auf der obersten Ebene für die App deaktiviert werden, werden auch alle Sammlungsbenachrichtigungen deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="17dbd-157">If notifications are turned off at the top level for the app, then all collections notifications will be turned off as well.</span></span>  <span data-ttu-id="17dbd-158">Jede Sammlung zeigt standardmäßig drei Benachrichtigungen im Info-Center an. Der Benutzer kann sie erweitern, um bis zu 20 Benachrichtigungen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="17dbd-158">In addition, each collection will by default show 3 notifications in Action Center, and the user can expand it to show up to 20 notifications.</span></span>

## <a name="related-topics"></a><span data-ttu-id="17dbd-159">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="17dbd-159">Related topics</span></span>

* [<span data-ttu-id="17dbd-160">Popupinhalt</span><span class="sxs-lookup"><span data-stu-id="17dbd-160">Toast content</span></span>](adaptive-interactive-toasts.md)
* [<span data-ttu-id="17dbd-161">Popup-Header</span><span class="sxs-lookup"><span data-stu-id="17dbd-161">Toast headers</span></span>](toast-headers.md)
* [<span data-ttu-id="17dbd-162">Benachrichtigungsbibliothek auf GitHub (Teil des Windows-Community-Toolkit)</span><span class="sxs-lookup"><span data-stu-id="17dbd-162">Notifications library on GitHub (part of the Windows Community Toolkit)</span></span>](https://github.com/Microsoft/UWPCommunityToolkit/tree/master/Microsoft.Toolkit.Uwp.Notifications)