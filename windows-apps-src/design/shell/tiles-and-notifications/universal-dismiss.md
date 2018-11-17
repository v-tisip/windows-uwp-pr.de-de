---
author: andrewleader
Description: Learn how to use Universal Dismiss on your toast notifications.
title: Universelles Schließen
label: Universal Dismiss
template: detail.hbs
ms.author: mijacobs
ms.date: 12/15/2017
ms.topic: article
keywords: Windows10, UWP, Popup, Info-Center in der Cloud, universelles Schließen, Benachrichtigung, geräteübergreifend, einmal Schließen, überall Schließen
ms.localizationpriority: medium
ms.openlocfilehash: 40a9c446172b25f2430a3f75014c8e168a91c233
ms.sourcegitcommit: 3257416aebb5a7b1515e107866806f8bd57845a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "7147249"
---
# <a name="universal-dismiss"></a><span data-ttu-id="1a7a9-103">Universelles Schließen</span><span class="sxs-lookup"><span data-stu-id="1a7a9-103">Universal Dismiss</span></span>

<span data-ttu-id="1a7a9-104">Universelles Schließen wird vom Info-Center in der Cloud unterstützt und bedeutet, dass Sie beim Schließen einer Benachrichtigung auf einem Gerät die gleiche Benachrichtigung auf allen anderen Geräten ebenfalls Schließen.</span><span class="sxs-lookup"><span data-stu-id="1a7a9-104">Universal Dismiss, powered by Action Center in the Cloud, means that when you dismiss a notification from one device, the same notification on your other devices is also dismissed.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1a7a9-105">**Benötigt Anniversary Update**: Sie müssen das SDK 14393 als Ziel und Build 14393 oder höher ausführen, um das universelle Schließen verwenden zu können.</span><span class="sxs-lookup"><span data-stu-id="1a7a9-105">**Requires Anniversary Update**: You must target SDK 14393 and be running build 14393 or higher to use Universal Dismiss.</span></span>

<span data-ttu-id="1a7a9-106">Ein gängiges Beispiel für ein solches Szenario sind Kalendererinnerungen... wenn Sie eine Kalender-App auf beiden Geräten haben... erhalten Sie ebenfalls eine Erinnerung auf Ihrem Handy und PC... klicken Sie auf dem Desktop auf „Schließen”... Dank des universellen Schließens, wird ebenfalls die Erinnerung auf Ihrem Handy verworfen!</span><span class="sxs-lookup"><span data-stu-id="1a7a9-106">The common example of this scenario is calendar reminders... you have a calendar app on both of your devices... you get a reminder on your phone and desktop... you click dismiss on your desktop... thanks to Universal Dismiss, the reminder on your phone is also dismissed!</span></span> **<span data-ttu-id="1a7a9-107">Das Aktivieren des universellen Schließens erfordert nur eine Codezeile!</span><span class="sxs-lookup"><span data-stu-id="1a7a9-107">Enabling Universal Dismiss only requires one line of code!</span></span>**

<img alt="Diagram of Universal Dismiss" src="images/universal-dismiss.gif" width="406"/>

<span data-ttu-id="1a7a9-108">In diesem Szenario ist das Schlüsselelement, das **die gleiche App auf mehreren Geräten installiert ist**, d.h., das **jedes Gerät bereits Benachrichtigungen empfängt**.</span><span class="sxs-lookup"><span data-stu-id="1a7a9-108">In this scenario, the key fact is that **the same app is installed on multiple devices**, meaning that **each device is already receiving notifications**.</span></span> <span data-ttu-id="1a7a9-109">Eine Kalender-App ist ein Paradebeispiel, da Sie in der Regel die gleichen Kalender-App auf Ihrem Windows-PC und Ihrem Handy installiert haben, und jede Instanz der App bereits Erinnerungen auf beide Geräte sendet.</span><span class="sxs-lookup"><span data-stu-id="1a7a9-109">A calendar app is the iconic example, since you typically have the same calendar app installed on both your Windows PC and your phone, and each instance of the app already sends you reminders on each device.</span></span> <span data-ttu-id="1a7a9-110">Durch das Hinzufügen von Unterstützung für das universellen Schließen können diese Instanzen für die gleichen Erinnerungen geräteübergreifend verknüpft werden.</span><span class="sxs-lookup"><span data-stu-id="1a7a9-110">By adding support for Universal Dismiss, those instances of the same reminders can be linked across devices.</span></span>


## <a name="how-to-enable-universal-dismiss"></a><span data-ttu-id="1a7a9-111">So aktivieren Sie das universelle Schließen</span><span class="sxs-lookup"><span data-stu-id="1a7a9-111">How to enable Universal Dismiss</span></span>

<span data-ttu-id="1a7a9-112">Als Entwickler ist das Aktivieren des universellen Schließens ganz einfach.</span><span class="sxs-lookup"><span data-stu-id="1a7a9-112">As a developer, enabling Universal Dismiss is extremely easy.</span></span> <span data-ttu-id="1a7a9-113">Sie müssen lediglich eine ID bereitstellen, die uns ermöglicht, jede Benachrichtigung geräteübergreifend zu verknüpfen. So wird die entsprechende verknüpfte Benachrichtigung auf einem Gerät geschlossen, wenn der Benutzer die Benachrichtigung auf einem anderen Gerät schließt.</span><span class="sxs-lookup"><span data-stu-id="1a7a9-113">You simply need to provide an ID that allows us to link each notification across devices, so that when the user dismisses a notification from one device, the corresponding linked notification is dismissed from the other device.</span></span>

![RemoteID-Diagramm für das universelle Schließen](images/universal-dismiss-remoteid.jpg)

> <span data-ttu-id="1a7a9-115">**RemoteId**: Eine ID, die eine Benachrichtigung eindeutig *geräteübergreifend* identifiziert.</span><span class="sxs-lookup"><span data-stu-id="1a7a9-115">**RemoteId**: An identifier that uniquely identifies a notification *across devices*.</span></span>

<span data-ttu-id="1a7a9-116">Es muss nur eine Zeile Code für RemoteId hinzugefügt werden, was die Unterstützung für das universelle Schließen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="1a7a9-116">t only takes one line of code to add RemoteId, enabling support for Universal Dismiss!</span></span> <span data-ttu-id="1a7a9-117">Wie Sie Ihre RemoteId generieren, ist Ihre Entscheidung – Sie müssen allerdings sicherstellen, dass sie die Benachrichtigung geräteübergreifend eindeutig identifiziert, und die gleiche ID von verschiedenen Instanzen Ihrer App generiert werden kann, die auf verschiedenen Geräten läuft.</span><span class="sxs-lookup"><span data-stu-id="1a7a9-117">How you generate your RemoteId is up to you - however, you need to make sure that it uniquely identifies your notification across devices, and that the same identifier can be generated from different instances of your app running on different devices.</span></span>

<span data-ttu-id="1a7a9-118">Beispielsweise generiere ich in meiner App für den Hausaufgabenplaner meine RemoteId so, dass Sie vom Typ "Erinnerung" ist. Ich füge anschließend die Online-Konto-ID und die Online-ID des Elements Hausaufgaben hinzu.</span><span class="sxs-lookup"><span data-stu-id="1a7a9-118">For example, in my homework planner app, I generate my RemoteId by saying that it is of type "reminder", and then I include the online account ID and the online identifier of the homework item.</span></span> <span data-ttu-id="1a7a9-119">Ich kann konsistent die exakt gleiche RemoteId konsistent generieren, unabhängig davon, welches Gerät die Benachrichtigung sendet, da diese online-IDs geräteübergreifend freigegeben werden.</span><span class="sxs-lookup"><span data-stu-id="1a7a9-119">I can consistently generate the exact same RemoteId, regardless of which device is sending the notification, since these online IDs are shared across the devices.</span></span>

```csharp
var toast = new ScheduledToastNotification(content.GetXml(), startTime);
 
// If the RemoteId property is present
if (ApiInformation.IsPropertyPresent(typeof(ScheduledToastNotification).FullName, nameof(ScheduledToastNotification.RemoteId)))
{
    // Assign the RemoteId to add support for Universal Dismiss
    toast.RemoteId = $"reminder_{account.AccountId}_{homework.Identifier}"
}
  
ToastNotificationManager.CreateToastNotifier().AddToSchedule(toast);
```

<span data-ttu-id="1a7a9-120">Der folgende Code wird auf meinem Handy und meiner Desktop-App ausgeführt, d.h., dass die Benachrichtigung auf beiden Geräten die gleiche RemoteId hat.</span><span class="sxs-lookup"><span data-stu-id="1a7a9-120">The following code runs on both my phone and desktop app, meaning that the notification on both devices will have the same RemoteId.</span></span>

<span data-ttu-id="1a7a9-121">Dies ist alles!</span><span class="sxs-lookup"><span data-stu-id="1a7a9-121">That's all you have to do!</span></span> <span data-ttu-id="1a7a9-122">Wenn der Benutzer eine Benachrichtigung schließt (oder darauf klickt), wird geprüft, ob es über eine RemoteId verfügt, und wenn dies der Fall ist, fächern wir das Schließen von dieser RemoteId auf allen Geräten des Benutzers aus.</span><span class="sxs-lookup"><span data-stu-id="1a7a9-122">When the user dismisses (or clicks on) a notification, we'll check if it has a RemoteId, and if so, we'll fan out a dismiss of that RemoteId across all the user's devices.</span></span>

<span data-ttu-id="1a7a9-123">**Bekanntes Problem**: Das Abrufen der **RemoteId** über die `ToastNotificationHistory.GetHistory()`-API gibt immer eine leere Zeichenfolge zurück anstelle der **RemoteId**, die angegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="1a7a9-123">**Known Issue**: Retrieving the **RemoteId** via the `ToastNotificationHistory.GetHistory()` API's will always return empty string rather than the **RemoteId** you specified.</span></span> <span data-ttu-id="1a7a9-124">Keine Sorge, alles funktioniert – es wird nur der Wert abgerufen, der beschädigt ist.</span><span class="sxs-lookup"><span data-stu-id="1a7a9-124">Don't worry, everything is functional - it's only retrieving the value that's broken.</span></span>

> [!NOTE]
> <span data-ttu-id="1a7a9-125">Wenn der Benutzer oder das Unternehmen die [Benachrichtigungsspiegelung](notification-mirroring.md) für Ihre App deaktiviert (oder die Benachrichtigungsspiegelung vollständig deaktiviert), funktioniert das universelle Schließen nicht, da Ihre Benachrichtigungen nicht in der Cloud vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="1a7a9-125">If the user or enterprise disables [notification mirroring](notification-mirroring.md) for your app (or completely disables notification mirroring), then Universal Dismiss will not work, since we do not have your notifications in the cloud.</span></span>


## <a name="supported-devices"></a><span data-ttu-id="1a7a9-126">Unterstützte Geräte</span><span class="sxs-lookup"><span data-stu-id="1a7a9-126">Supported devices</span></span>

<span data-ttu-id="1a7a9-127">Seit dem Anniversary Update wird das universelle Schließen auf Windows Mobile und Windows Desktop unterstützt.</span><span class="sxs-lookup"><span data-stu-id="1a7a9-127">Since the Anniversary Update, Universal Dismiss is supported on Windows Mobile and Windows Desktop.</span></span> <span data-ttu-id="1a7a9-128">Universelles Schließen funktioniert in beide Richtungen, zwischen PCs, PC und Handy oder Handy und Handy.</span><span class="sxs-lookup"><span data-stu-id="1a7a9-128">Universal Dismiss works both directions, between PC-PC, PC-Phone, and Phone-Phone.</span></span>