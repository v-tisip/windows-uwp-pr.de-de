---
author: andrewleader
Description: Learn how to use a progress bar within your toast notification.
title: Popup-Statusanzeige und Datenbindungen
label: Toast progress bar and data binding
template: detail.hbs
ms.author: mijacobs
ms.date: 12/7/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Popup, Statusanzeige, Popup-Statusanzeige, Benachrichtigungen, Datenbindung der Popups
ms.localizationpriority: medium
ms.openlocfilehash: b99c2479bef3c10ecc82707e475f49fd2b9014ec
ms.sourcegitcommit: 933e71a31989f8063b020746fdd16e9da94a44c4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2018
ms.locfileid: "4537086"
---
# <a name="toast-progress-bar-and-data-binding"></a><span data-ttu-id="351cb-103">Popup-Statusanzeige und Datenbindungen</span><span class="sxs-lookup"><span data-stu-id="351cb-103">Toast progress bar and data binding</span></span>

<span data-ttu-id="351cb-104">Durch die Verwendung einer Statusanzeige innerhalb Ihrer Popupbenachrichtigung können Sie den Status der zeitintensiven Vorgänge für den Benutzer vermitteln, z.B. Downloads, Videowiedergabe, Übungen und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="351cb-104">Using a progress bar inside your toast notification allows you to convey the status of long-running operations to the user, like downloads, video rendering, exercise goals, and more.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="351cb-105">**Erfordert Creators Update und 1.4.0 der Benachrichtigungsbibliothek**: Sie müssen als Ziel SDK 15063 und Build 15063 oder höher ausführen, um Statusanzeigen auf Popups zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="351cb-105">**Requires Creators Update and 1.4.0 of Notifications library**: You must target SDK 15063 and be running build 15063 or higher to use progress bars on toasts.</span></span> <span data-ttu-id="351cb-106">Sie müssen Version 1.4.0 oder höher der [UWP Community Toolkit Benachrichtigungen NuGet-Bibliothek](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) verwenden, um die Statusanzeige der Popup-Inhalte zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="351cb-106">You must use version 1.4.0 or higher of the [UWP Community Toolkit Notifications NuGet library](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) to construct the progress bar in your toast's content.</span></span>

<span data-ttu-id="351cb-107">Eine Statusanzeige in einem Popup kann entweder "unbestimmt" (ohne spezifischen Wert, ein Vorgang erfolgt durch das Anzeigen animierter Punkte) oder "exakt" (ein bestimmtes Prozentsatz der Leiste wird gefüllt, z.B. 60%) sein.</span><span class="sxs-lookup"><span data-stu-id="351cb-107">A progress bar inside a toast can either be "indetermindate" (no specific value, animated dots indicate an operation is occurring) or "determinate" (a specific percent of the bar is filled, like 60%).</span></span>

> <span data-ttu-id="351cb-108">**Wichtige APIs**: [NotificationData-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.notifications.notificationdata), [ToastNotifier.Update Methode](https://docs.microsoft.com/uwp/api/Windows.UI.Notifications.ToastNotifier.Update), [ToastNotification-Klasse](https://docs.microsoft.com/uwp/api/Windows.UI.Notifications.ToastNotification)</span><span class="sxs-lookup"><span data-stu-id="351cb-108">**Important APIs**: [NotificationData class](https://docs.microsoft.com/uwp/api/windows.ui.notifications.notificationdata), [ToastNotifier.Update method](https://docs.microsoft.com/uwp/api/Windows.UI.Notifications.ToastNotifier.Update), [ToastNotification class](https://docs.microsoft.com/uwp/api/Windows.UI.Notifications.ToastNotification)</span></span>

> [!NOTE]
> <span data-ttu-id="351cb-109">Nur Desktop unterstützt Statusanzeigen in Popupbenachrichtigungen.</span><span class="sxs-lookup"><span data-stu-id="351cb-109">Only Desktop supports progress bars in toast notifications.</span></span> <span data-ttu-id="351cb-110">Auf anderen Geräten wird die Statusanzeige aus der Benachrichtigung gelöscht.</span><span class="sxs-lookup"><span data-stu-id="351cb-110">On other devices, the progress bar will be dropped from your notification.</span></span>

<span data-ttu-id="351cb-111">Die folgende Abbildung zeigt eine exakte Statusanzeige mit allen entsprechenden Eigenschaften mit Bezeichnung.</span><span class="sxs-lookup"><span data-stu-id="351cb-111">The picture below shows a determinate progress bar with all of its corresponding properties labeled.</span></span>

<img alt="Toast with progress bar properties labeled" src="images/toast-progressbar-annotated.png" width="626"/>

| <span data-ttu-id="351cb-112">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="351cb-112">Property</span></span> | <span data-ttu-id="351cb-113">Typ</span><span class="sxs-lookup"><span data-stu-id="351cb-113">Type</span></span> | <span data-ttu-id="351cb-114">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="351cb-114">Required</span></span> | <span data-ttu-id="351cb-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="351cb-115">Description</span></span> |
|---|---|---|---|
| **<span data-ttu-id="351cb-116">Titel</span><span class="sxs-lookup"><span data-stu-id="351cb-116">Title</span></span>** | <span data-ttu-id="351cb-117">Zeichenfolge oder [BindableString](toast-schema.md#bindablestring)</span><span class="sxs-lookup"><span data-stu-id="351cb-117">string or [BindableString](toast-schema.md#bindablestring)</span></span> | <span data-ttu-id="351cb-118">Falsch</span><span class="sxs-lookup"><span data-stu-id="351cb-118">false</span></span> | <span data-ttu-id="351cb-119">Ruft einen optionalen Zeichenfolgetitel auf oder legt diesen fest.</span><span class="sxs-lookup"><span data-stu-id="351cb-119">Gets or sets an optional title string.</span></span> <span data-ttu-id="351cb-120">Unterstützt die Datenbindung.</span><span class="sxs-lookup"><span data-stu-id="351cb-120">Supports data binding.</span></span> |
| **<span data-ttu-id="351cb-121">Wert</span><span class="sxs-lookup"><span data-stu-id="351cb-121">Value</span></span>** | <span data-ttu-id="351cb-122">doppelt oder [AdaptiveProgressBarValue](toast-schema.md#adaptiveprogressbarvalue) oder [BindableProgressBarValue](toast-schema.md#bindableprogressbarvalue)</span><span class="sxs-lookup"><span data-stu-id="351cb-122">double or [AdaptiveProgressBarValue](toast-schema.md#adaptiveprogressbarvalue) or [BindableProgressBarValue](toast-schema.md#bindableprogressbarvalue)</span></span> | <span data-ttu-id="351cb-123">Falsch</span><span class="sxs-lookup"><span data-stu-id="351cb-123">false</span></span> | <span data-ttu-id="351cb-124">Ruft den Wert der Statusanzeige auf oder legt diesen fest.</span><span class="sxs-lookup"><span data-stu-id="351cb-124">Gets or sets the value of the progress bar.</span></span> <span data-ttu-id="351cb-125">Unterstützt die Datenbindung.</span><span class="sxs-lookup"><span data-stu-id="351cb-125">Supports data binding.</span></span> <span data-ttu-id="351cb-126">Die Standardeinstellung ist 0.</span><span class="sxs-lookup"><span data-stu-id="351cb-126">Defaults to 0.</span></span> <span data-ttu-id="351cb-127">Kann entweder ein Double zwischen 0,0 und 1,0, `AdaptiveProgressBarValue.Indeterminate` oder `new BindableProgressBarValue("myProgressValue")` sein.</span><span class="sxs-lookup"><span data-stu-id="351cb-127">Can either be a double between 0.0 and 1.0, `AdaptiveProgressBarValue.Indeterminate`, or `new BindableProgressBarValue("myProgressValue")`.</span></span> |
| **<span data-ttu-id="351cb-128">ValueStringOverride</span><span class="sxs-lookup"><span data-stu-id="351cb-128">ValueStringOverride</span></span>** | <span data-ttu-id="351cb-129">Zeichenfolge oder [BindableString](toast-schema.md#bindablestring)</span><span class="sxs-lookup"><span data-stu-id="351cb-129">string or [BindableString](toast-schema.md#bindablestring)</span></span> | <span data-ttu-id="351cb-130">Falsch</span><span class="sxs-lookup"><span data-stu-id="351cb-130">false</span></span> | <span data-ttu-id="351cb-131">Ruft eine optionale Zeichenfolge auf oder legt diese fest, damit sie anstelle der Standardzeichenfolge in Prozent angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="351cb-131">Gets or sets an optional string to be displayed instead of the default percentage string.</span></span> <span data-ttu-id="351cb-132">Wenn dies nicht bereitgestellt ist, wird etwas wie "70 %" angezeigt.</span><span class="sxs-lookup"><span data-stu-id="351cb-132">If this isn't provided, something like "70%" will be displayed.</span></span> |
| **<span data-ttu-id="351cb-133">Status</span><span class="sxs-lookup"><span data-stu-id="351cb-133">Status</span></span>** | <span data-ttu-id="351cb-134">Zeichenfolge oder [BindableString](toast-schema.md#bindablestring)</span><span class="sxs-lookup"><span data-stu-id="351cb-134">string or [BindableString](toast-schema.md#bindablestring)</span></span> | <span data-ttu-id="351cb-135">Wahr</span><span class="sxs-lookup"><span data-stu-id="351cb-135">true</span></span> | <span data-ttu-id="351cb-136">Ruft eine Statuszeichenfolge auf oder legt diese fest (erforderlich), die unter der Statusanzeige auf der linken Seite angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="351cb-136">Gets or sets a status string (required), which is displayed underneath the progress bar on the left.</span></span> <span data-ttu-id="351cb-137">Diese Zeichenfolge sollte den Status des Vorgangs widerspiegeln, z.B. "Herunterladen..." oder "Installieren von..."</span><span class="sxs-lookup"><span data-stu-id="351cb-137">This string should reflect the status of the operation, like "Downloading..." or "Installing..."</span></span> |


<span data-ttu-id="351cb-138">So würde die oben dargestellte Benachrichtigung generiert...</span><span class="sxs-lookup"><span data-stu-id="351cb-138">Here's how you would generate the notification seen above...</span></span>

```csharp
ToastContent content = new ToastContent()
{
    Visual = new ToastVisual()
    {
        BindingGeneric = new ToastBindingGeneric()
        {
            Children =
            {
                new AdaptiveText()
                {
                    Text = "Downloading your weekly playlist..."
                },
 
                new AdaptiveProgressBar()
                {
                    Title = "Weekly playlist",
                    Value = 0.6,
                    ValueStringOverride = "15/26 songs",
                    Status = "Downloading..."
                }
            }
        }
    }
};
```

```xml
<toast>
    <visual>
        <binding template="ToastGeneric">
            <text>Downloading your weekly playlist...</text>
            <progress
                title="Weekly playlist"
                value="0.6"
                valueStringOverride="15/26 songs"
                status="Downloading..."/>
        </binding>
    </visual>
</toast>
```

<span data-ttu-id="351cb-139">Allerdings müssen Sie die Werte der Statusanzeige dynamisch aktualisieren, da diese tatsächlich "live" ist.</span><span class="sxs-lookup"><span data-stu-id="351cb-139">However, you'll need to dynamically update the values of the progress bar for it to actually be "live".</span></span> <span data-ttu-id="351cb-140">Dies kann durch die Verwendung einer Datenbindung erfolgen, um das Popup zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="351cb-140">This can be done by using data binding to update the toast.</span></span>


## <a name="using-data-binding-to-update-a-toast"></a><span data-ttu-id="351cb-141">Verwenden der Datenbindung zum Aktualisieren eines Popups</span><span class="sxs-lookup"><span data-stu-id="351cb-141">Using data binding to update a toast</span></span>

<span data-ttu-id="351cb-142">Das Verwenden der Datenbindung umfasst die folgenden Schritte...</span><span class="sxs-lookup"><span data-stu-id="351cb-142">Using data binding involves the following steps...</span></span>

1. <span data-ttu-id="351cb-143">Erstellen von Popup-Inhalten, die Datenbildungsfelder verwenden</span><span class="sxs-lookup"><span data-stu-id="351cb-143">Construct toast content that utilizes data bound fields</span></span>
2. <span data-ttu-id="351cb-144">Fügen Sie einen **Tag** (und optional eine **Gruppe**) auf **ToastNotification** hinzu</span><span class="sxs-lookup"><span data-stu-id="351cb-144">Assign a **Tag** (and optionally a **Group**) to your **ToastNotification**</span></span>
3. <span data-ttu-id="351cb-145">Definieren Sie Ihre ersten **Daten**werte für Ihre **ToastNotification**</span><span class="sxs-lookup"><span data-stu-id="351cb-145">Define your initial **Data** values on your **ToastNotification**</span></span>
4. <span data-ttu-id="351cb-146">Senden Sie das Popup</span><span class="sxs-lookup"><span data-stu-id="351cb-146">Send the toast</span></span>
5. <span data-ttu-id="351cb-147">Nutzen Sie **Tag** und **Gruppe** zum Aktualisieren der **Daten** mit neuen Werten</span><span class="sxs-lookup"><span data-stu-id="351cb-147">Utilize **Tag** and **Group** to update the **Data** values with new values</span></span>

<span data-ttu-id="351cb-148">Der folgende Codeausschnitt zeigt die Schritte1 bis 4.</span><span class="sxs-lookup"><span data-stu-id="351cb-148">The following code snippet shows steps 1-4.</span></span> <span data-ttu-id="351cb-149">Der nächste Codeausschnitt zeigt, wie das Popup **Daten**werte aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="351cb-149">The next snippet will show how to update the toast **Data** values.</span></span>

```csharp
using Windows.UI.Notifications;
using Microsoft.Toolkit.Uwp.Notifications;
 
public void SendUpdatableToastWithProgress()
{
    // Define a tag (and optionally a group) to uniquely identify the notification, in order update the notification data later;
    string tag = "weekly-playlist";
    string group = "downloads";
 
    // Construct the toast content with data bound fields
    var content = new ToastContent()
    {
        Visual = new ToastVisual()
        {
            BindingGeneric = new ToastBindingGeneric()
            {
                Children =
                {
                    new AdaptiveText()
                    {
                        Text = "Downloading your weekly playlist..."
                    },
    
                    new AdaptiveProgressBar()
                    {
                        Title = "Weekly playlist",
                        Value = new BindableProgressBarValue("progressValue"),
                        ValueStringOverride = new BindableString("progressValueString"),
                        Status = new BindableString("progressStatus")
                    }
                }
            }
        }
    };
 
    // Generate the toast notification
    var toast = new ToastNotification(content.GetXml());
 
    // Assign the tag and group
    toast.Tag = tag;
    toast.Group = group;
 
    // Assign initial NotificationData values
    // Values must be of type string
    toast.Data = new NotificationData();
    toast.Data.Values["progressValue"] = "0.6";
    toast.Data.Values["progressValueString"] = "15/26 songs";
    toast.Data.Values["progressStatus"] = "Downloading...";
 
    // Provide sequence number to prevent out-of-order updates, or assign 0 to indicate "always update"
    toast.Data.SequenceNumber = 1;
 
    // Show the toast notification to the user
    ToastNotificationManager.CreateToastNotifier().Show(toast);
}
```

<span data-ttu-id="351cb-150">Wenn Sie Ihre **Daten**werte ändern möchten, verwenden Sie die [**Update**](https://docs.microsoft.com/uwp/api/Windows.UI.Notifications.ToastNotifier.Update)-Methode, um die neuen Daten bereitzustellen, ohne die gesamte Popupnutzlast neu zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="351cb-150">Then, when you want to change your **Data** values, use the [**Update**](https://docs.microsoft.com/uwp/api/Windows.UI.Notifications.ToastNotifier.Update) method to provide the new data without re-constructing the entire toast payload.</span></span>

```csharp
using Windows.UI.Notifications;
 
public void UpdateProgress()
{
    // Construct a NotificationData object;
    string tag = "weekly-playlist";
    string group = "downloads";
 
    // Create NotificationData and make sure the sequence number is incremented
    // since last update, or assign 0 for updating regardless of order
    var data = new NotificationData
    {
        SequenceNumber = 2
    };

    // Assign new values
    // Note that you only need to assign values that changed. In this example
    // we don't assign progressStatus since we don't need to change it
    data.Values["progressValue"] = "0.7";
    data.Values["progressValueString"] = "18/26 songs";

    // Update the existing notification's data by using tag/group
    ToastNotificationManager.CreateToastNotifier().Update(data, tag, group);
}
```

<span data-ttu-id="351cb-151">Statt das gesamte Popup zu ersetzen, sorgt die **Update**-Methode dafür, dass die Popupbenachrichtigung in der gleichen Position im Info-Center bleibt und nicht nach oben oder unten verschoben wird.</span><span class="sxs-lookup"><span data-stu-id="351cb-151">Using the **Update** method rather than replacing the entire toast also ensures that the toast notification stays in the same position in Action Center and doesn't move up or down.</span></span> <span data-ttu-id="351cb-152">Es wäre verwirrend für den Benutzer, wenn das Popup alle paar Sekunden an den Anfang des Info-Centers verschoben würde, während die Statusanzeige gefüllt wird.</span><span class="sxs-lookup"><span data-stu-id="351cb-152">It would be quite confusing to the user if the toast kept jumping to the top of Action Center every few seconds while the progress bar filled!</span></span>

<span data-ttu-id="351cb-153">Die **Update**-Methode gibt eine Enumeration wieder, [**NotificationUpdateResult**](https://docs.microsoft.com/uwp/api/windows.ui.notifications.notificationupdateresult), und teilt Ihnen mit, ob das Update erfolgreich war oder ob die Benachrichtigung nicht gefunden werden konnte (d.h. der Benutzer hat möglicherweise die Benachrichtigung geschlossen und Sie müssen aufhören, Updates zu senden).</span><span class="sxs-lookup"><span data-stu-id="351cb-153">The **Update** method returns an enum, [**NotificationUpdateResult**](https://docs.microsoft.com/uwp/api/windows.ui.notifications.notificationupdateresult), which lets you know whether the update succeeded or whether the notification couldn't be found (which means the user has likely dismissed your notification and you should stop sending updates to it).</span></span> <span data-ttu-id="351cb-154">Es wird nicht empfohlen, ein anderes Popup einzublenden, bis der Vorgang abgeschlossen ist (z.B. wenn der Download abgeschlossen ist).</span><span class="sxs-lookup"><span data-stu-id="351cb-154">We do not recommend popping another toast until your progress operation has been completed (like when the download completes).</span></span>


## <a name="elements-that-support-data-binding"></a><span data-ttu-id="351cb-155">Elemente, die die Datenbindung unterstützen</span><span class="sxs-lookup"><span data-stu-id="351cb-155">Elements that support data binding</span></span>
<span data-ttu-id="351cb-156">Folgende Elemente in Popupbenachrichtigungen unterstützen die Datenbindung</span><span class="sxs-lookup"><span data-stu-id="351cb-156">The following elements in toast notifications support data binding</span></span>

- <span data-ttu-id="351cb-157">Alle Eigenschaften für **AdaptiveProgress**</span><span class="sxs-lookup"><span data-stu-id="351cb-157">All properties on **AdaptiveProgress**</span></span>
- <span data-ttu-id="351cb-158">Die **Text**-Eigenschaft auf der obersten Ebene des **AdaptiveText**-Elements</span><span class="sxs-lookup"><span data-stu-id="351cb-158">The **Text** property on the top-level **AdaptiveText** elements</span></span>


## <a name="update-or-replace-a-notification"></a><span data-ttu-id="351cb-159">Aktualisieren oder Ersetzen einer Benachrichtigung</span><span class="sxs-lookup"><span data-stu-id="351cb-159">Update or replace a notification</span></span>

<span data-ttu-id="351cb-160">Ab Windows10 könnten Sie immer eine Benachrichtigung **ersetzen**, indem Sie eine neue Popupbenachrichtigung mit dem gleichen **Tag** und der gleichen **Gruppe** senden.</span><span class="sxs-lookup"><span data-stu-id="351cb-160">Since Windows 10, you could always **replace** a notification by sending a new toast with the same **Tag** and **Group**.</span></span> <span data-ttu-id="351cb-161">Worin liegt der Unterschied zwischen dem **Ersetzen** des Popups und dem **Aktualisieren** der Popupdaten?</span><span class="sxs-lookup"><span data-stu-id="351cb-161">So what's the difference between **replacing** the toast and **updating** the toast's data?</span></span>

| | <span data-ttu-id="351cb-162">Ersetzen</span><span class="sxs-lookup"><span data-stu-id="351cb-162">Replacing</span></span> | <span data-ttu-id="351cb-163">Aktualisieren</span><span class="sxs-lookup"><span data-stu-id="351cb-163">Updating</span></span> |
| -- | -- | --
| **<span data-ttu-id="351cb-164">Position im Info-Center</span><span class="sxs-lookup"><span data-stu-id="351cb-164">Position in Action Center</span></span>** | <span data-ttu-id="351cb-165">Verschiebt die Benachrichtigung oben auf das Info-Center.</span><span class="sxs-lookup"><span data-stu-id="351cb-165">Moves the notification to the top of Action Center.</span></span> | <span data-ttu-id="351cb-166">Behält die Stelle der Benachrichtigung im Info-Center bei.</span><span class="sxs-lookup"><span data-stu-id="351cb-166">Leaves the notification in place within Action Center.</span></span> |
| **<span data-ttu-id="351cb-167">Ändern des Inhalts</span><span class="sxs-lookup"><span data-stu-id="351cb-167">Modifying content</span></span>** | <span data-ttu-id="351cb-168">Alle Inhalte/Layout des Popups können dadurch vollständig geändert werden.</span><span class="sxs-lookup"><span data-stu-id="351cb-168">Can completely change all content/layout of the toast</span></span> | <span data-ttu-id="351cb-169">Kann nur Eigenschaften ändern, die die Datenbindung unterstützen (Statusanzeige und Text der obersten Ebene).</span><span class="sxs-lookup"><span data-stu-id="351cb-169">Can only change properties that support data binding (progress bar and top-level text)</span></span> |
| **<span data-ttu-id="351cb-170">Erneutes Anzeigen als Popup</span><span class="sxs-lookup"><span data-stu-id="351cb-170">Reappearing as popup</span></span>** | <span data-ttu-id="351cb-171">Kann als Popup eingeblendet werden, wenn Sie **SuppressPopup** auf `false` festgelegt haben (oder auf „wahr”, um es lautlos im Hintergrund an das Info-Center zu senden)</span><span class="sxs-lookup"><span data-stu-id="351cb-171">Can reappear as a toast popup if you leave **SuppressPopup** set to `false` (or set to true to silently send it to Action Center)</span></span> | <span data-ttu-id="351cb-172">Wird nicht erneut als Popup angezeigt; die Popup-Daten werden im Info-Center automatisch aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="351cb-172">Won't reappear as a popup; the toast's data is silently updated within Action Center</span></span> |
| **<span data-ttu-id="351cb-173">Vom Benutzer verworfen</span><span class="sxs-lookup"><span data-stu-id="351cb-173">User dismissed</span></span>** | <span data-ttu-id="351cb-174">Unabhängig davon, ob der Benutzer die vorherige Benachrichtigung verworfen hat, wird der Popup-Ersatz immer gesendet</span><span class="sxs-lookup"><span data-stu-id="351cb-174">Regardless of whether user dismissed your previous notification, your replacement toast will always be sent</span></span> | <span data-ttu-id="351cb-175">Wenn der Benutzer das Popup verworfen hat, schlägt das Popup-Update fehl</span><span class="sxs-lookup"><span data-stu-id="351cb-175">If the user dismissed your toast, the toast update will fail</span></span> |

<span data-ttu-id="351cb-176">Allgemein: **Aktualisierung ist besonders nützlich für...**</span><span class="sxs-lookup"><span data-stu-id="351cb-176">In general, **updating is useful for...**</span></span>

- <span data-ttu-id="351cb-177">Informationen, die sich häufig und in kurzer Zeit ändern und die nicht die Aufmerksamkeit des Benutzers erfordern</span><span class="sxs-lookup"><span data-stu-id="351cb-177">Information that frequently changes in a short period of time and doesn't require being brought to the front of the user's attention</span></span>
- <span data-ttu-id="351cb-178">Kleine Verbesserungen am Popupinhalt, z.B. das Ändern von 50% auf 65%</span><span class="sxs-lookup"><span data-stu-id="351cb-178">Subtle changes to your toast content, like changing 50% to 65%</span></span>

<span data-ttu-id="351cb-179">Nachdem die Sequenz der Updates abgeschlossen ist, (z.B. die Datei heruntergeladen wurden) empfehlen wir den letzten Schritt zu ersetzen, da...</span><span class="sxs-lookup"><span data-stu-id="351cb-179">Often times, after your sequence of updates have completed (like the file has been downloaded), we recommend replacing for the final step, because...</span></span>

- <span data-ttu-id="351cb-180">Die letzte Benachrichtigung hat wahrscheinlich drastische Layoutänderungen, z.B. ein Entfernen der Statusanzeige, das Hinzufügen neuer Schaltflächen usw.</span><span class="sxs-lookup"><span data-stu-id="351cb-180">Your final notification likely has drastic layout changes, like removal of the progress bar, addition of new buttons, etc</span></span>
- <span data-ttu-id="351cb-181">Der Benutzer hat möglicherweise die ausstehenden Statusbenachrichtigung verworfen, da er den Download nicht ansehen möchte, er sollte allerdings weiterhin über ein Popup benachrichtigt werden, wenn der Vorgang abgeschlossen ist</span><span class="sxs-lookup"><span data-stu-id="351cb-181">The user might have dismissed your pending progress notification since they don't care about watching it download, but still want to be notified with a popup toast when the operation is completed</span></span>


## <a name="related-topics"></a><span data-ttu-id="351cb-182">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="351cb-182">Related topics</span></span>

- [<span data-ttu-id="351cb-183">Vollständiges Codebeispiel auf GitHub</span><span class="sxs-lookup"><span data-stu-id="351cb-183">Full code sample on GitHub</span></span>](https://github.com/WindowsNotifications/quickstart-toast-progress-bar)
- [<span data-ttu-id="351cb-184">Dokumentation zu Popupinhalt</span><span class="sxs-lookup"><span data-stu-id="351cb-184">Toast content documentation</span></span>](adaptive-interactive-toasts.md)