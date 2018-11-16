---
author: adwilso
Description: Windows Push Notification Services (WNS) enables third-party developers to send toast, tile, badge, and raw updates from their own cloud service. There are many ways to send the notifications depending on the needs of your application
title: Auswählen des richtigen Kanaltypen für die Pushbenachrichtigungen
ms.author: mijacobs
ms.date: 07/07/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: db2cf1c732669a2ae45b8a5eb427e8864446c800
ms.sourcegitcommit: 9f8010fe67bb3372db1840de9f0be36097ed6258
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "7102184"
---
# <a name="choosing-the-right-push-notification-channel-type"></a><span data-ttu-id="8c7e2-103">Auswählen des richtigen Kanaltypen für die Pushbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="8c7e2-103">Choosing the right push notification channel type</span></span>

<span data-ttu-id="8c7e2-104">Dieser Artikel behandelt die drei Arten von UWP-Kanälen für die Push-Benachrichtigungen (primär, sekundär und alternativ), über die Sie die Inhalte für Ihre App übermitteln können.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-104">This article covers the three types of UWP push notification channels (primary, secondary, and alternate) that help you deliver content to your app.</span></span> 

<span data-ttu-id="8c7e2-105">(Weitere Informationen zum Erstellen von Pushbenachrichtigungen finden die [Übersicht über die Gruppenrichtlinien-Verwaltungskonsole (Windows Push Notification Services, WNS)](../tiles-and-notifications/windows-push-notification-services--wns--overview.md).)</span><span class="sxs-lookup"><span data-stu-id="8c7e2-105">(For details on how to create push notifications, see the [Windows Push Notification Services (WNS) overview](../tiles-and-notifications/windows-push-notification-services--wns--overview.md).)</span></span> 

## <a name="types-of-push-channels"></a><span data-ttu-id="8c7e2-106">Pushkanaltypen</span><span class="sxs-lookup"><span data-stu-id="8c7e2-106">Types of push channels</span></span> 

<span data-ttu-id="8c7e2-107">Es gibt drei Arten an Pushkanälen, die zum Senden von Benachrichtigungen an eine UWP-App verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-107">There are three types of push channels that can be used to send notifications to a UWP app.</span></span> <span data-ttu-id="8c7e2-108">Sie lauten wie folgt:</span><span class="sxs-lookup"><span data-stu-id="8c7e2-108">They are:</span></span> 

<span data-ttu-id="8c7e2-109">[Primärer Kanal](https://docs.microsoft.com/uwp/api/windows.networking.pushnotifications.pushnotificationchannelmanagerforuser#Methods_) -der "traditionelle" Pushkanal.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-109">[Primary channel](https://docs.microsoft.com/uwp/api/windows.networking.pushnotifications.pushnotificationchannelmanagerforuser#Methods_) - the "traditional" push channel.</span></span> <span data-ttu-id="8c7e2-110">Kann von jeder App im Store zum Senden von Popupbenachrichtigungen, Kacheln, unformatierten Benachrichtigungen oder Signalbenachrichtigungen verwendet werden (Link für Beschreibungen von Popups/Kacheln/Signalen)</span><span class="sxs-lookup"><span data-stu-id="8c7e2-110">Can be used by any app in the store to send toast, tile, raw, or badge notifications (Link to descriptions of toast/tiles/badge)</span></span>

<span data-ttu-id="8c7e2-111">[Sekundärer Kachelkanal](https://docs.microsoft.com/uwp/api/windows.networking.pushnotifications.pushnotificationchannelmanagerforuser#Methods_) - wird für Kachel-Updates im Pushverfahren für eine sekundäre Kachel verwendet.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-111">[Secondary tile channel](https://docs.microsoft.com/uwp/api/windows.networking.pushnotifications.pushnotificationchannelmanagerforuser#Methods_) - used to push tile updates for a secondary tile.</span></span> <span data-ttu-id="8c7e2-112">Kann nur zum Senden von Kachel- oder Signalbenachrichtigungen an eine sekundäre Kachel verwendet werden, die auf der Startseite angeheftet ist</span><span class="sxs-lookup"><span data-stu-id="8c7e2-112">Can only be used to send tile or badge notifications to a secondary tile pinned on the user's start screen</span></span>

<span data-ttu-id="8c7e2-113">[Alternativer Kanal](https://docs.microsoft.com/uwp/api/windows.networking.pushnotifications.pushnotificationchannelmanagerforuser#Methods_) -eine neue Art von Kanal, der im Creators Update hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-113">[Alternate channel](https://docs.microsoft.com/uwp/api/windows.networking.pushnotifications.pushnotificationchannelmanagerforuser#Methods_) - A new type of channel added in the Creators Update.</span></span> <span data-ttu-id="8c7e2-114">Sendet unformatierte Benachrichtigungen an alle UWP-Apps, einschließlich derjenigen, die im Store nicht registriert sind.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-114">It allows for raw notifications to be sent to any UWP app, including those which aren't registered in the Store.</span></span> 

> [!NOTE]
> <span data-ttu-id="8c7e2-115">Unabhängig vom verwendeten Pushkanal kann die App, wenn Sie auf dem Gerät ausgeführt, wird immer lokale Popupbenachrichtigungen sowie Benachrichtigungen für Kacheln oder Signalbenachrichtigungen senden.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-115">No matter which push channel you use, once your app is running on the device, it will always be able to send local toast, tile, or badge notifications.</span></span> <span data-ttu-id="8c7e2-116">Es können lokale Benachrichtigungen von im Vordergrund ausgeführten App-Prozessen oder über Hintergrundaufgaben gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-116">It can send local notifications from the foreground app processes or from a background task.</span></span> 


## <a name="primary-channels"></a><span data-ttu-id="8c7e2-117">Primäre Kanäle</span><span class="sxs-lookup"><span data-stu-id="8c7e2-117">Primary channels</span></span>

<span data-ttu-id="8c7e2-118">Diese Kanäle sind die derzeit am häufigsten verwendeten Kanäle auf Windows und eignen sich für nahezu alle Szenarien, in denen Ihre App über den Microsoft Store verteilt werden soll.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-118">These are the most commonly used channels on Windows right now, and are good for almost any scenario where your app is going to be distributed through the Microsoft Store.</span></span> <span data-ttu-id="8c7e2-119">Sie können dadurch alle Arten von Benachrichtigungen an die App senden.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-119">They allow you to send all types of notifications to the app.</span></span> 

### <a name="what-do-primary-channels-enable"></a><span data-ttu-id="8c7e2-120">Was aktivieren die primären Kanäle?</span><span class="sxs-lookup"><span data-stu-id="8c7e2-120">What do primary channels enable?</span></span>

-   **<span data-ttu-id="8c7e2-121">Senden von Kachelaktualisierungen oder Signalupdates an die primäre Kachel.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-121">Sending tile or badge updates to the primary tile.</span></span>** <span data-ttu-id="8c7e2-122">Wenn der Benutzer die Kachel an die Startseite angeheftet hat, ist dies eine großartige Möglichkeit, Ihre Fertigkeit zu zeigen.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-122">If the user has chosen to pin your tile to the start screen, this is your chance to show off.</span></span> <span data-ttu-id="8c7e2-123">Senden Sie Aktualisierungen mit nützlichen Informationen oder Erinnerungen innerhalb Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-123">Send updates with useful information or reminders of experiences within your app.</span></span> 
-   **<span data-ttu-id="8c7e2-124">Senden Sie Popupbenachrichtigungen.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-124">Sending toast notifications.</span></span>** <span data-ttu-id="8c7e2-125">Popupbenachrichtigungen sind eine Gelegenheit, dem Benutzer sofort einige Informationen zu unterbreiten.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-125">Toast notifications are a chance to get some information in front of the user immediately.</span></span> <span data-ttu-id="8c7e2-126">Sie werden von der Shell im Vordergrund der meisten Apps angezeigt sowie Live im Info-Center, so dass der Benutzer darauf zurückkehren und später mit ihnen interagieren kann.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-126">They are painted by the shell over top of most apps, and live in the action center so the user can go back and interact with them later.</span></span> 
-   **<span data-ttu-id="8c7e2-127">Von unformatierten Benachrichtigungen ausgelöste Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="8c7e2-127">Sending raw notifications to trigger a background task.</span></span>** <span data-ttu-id="8c7e2-128">Manchmal möchten Sie basierend auf einer Benachrichtigung einige Aktionen für den Benutzer ausführen.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-128">Sometimes you want to do some work on behalf of the user based on a notification.</span></span> <span data-ttu-id="8c7e2-129">Unformatiert Benachrichtigungen ermöglichen das Ausführen der Hintergrundaufgaben Ihrer Apps</span><span class="sxs-lookup"><span data-stu-id="8c7e2-129">Raw notifications allow your app's background tasks to run</span></span> 
-   **<span data-ttu-id="8c7e2-130">Nachrichtenverschlüsselung während der Übertragung durch Windows mithilfe von TLS.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-130">Message encryption in transit provided by Windows using TLS.</span></span>** <span data-ttu-id="8c7e2-131">Nachrichten werden bei der Übertragung auf der Leitung beim Eingang auf WNS und beim Ausgang auf das Gerät des Benutzers verschlüsselt.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-131">Messages are encrypted on the wire both coming into WNS and going to the user's device.</span></span>  

### <a name="limitations-of-primary-channels"></a><span data-ttu-id="8c7e2-132">Einschränkungen der primären Kanäle</span><span class="sxs-lookup"><span data-stu-id="8c7e2-132">Limitations of primary channels</span></span>

-   <span data-ttu-id="8c7e2-133">Erfordert WNS REST API, um Pushbenachrichtigungen zu senden, was bei Geräteherstellern kein Standard ist.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-133">Requires using the WNS REST API to push notifications, which isn't standard across device vendors.</span></span> 
-   <span data-ttu-id="8c7e2-134">Pro App kann nur ein Kanal erstellt werden</span><span class="sxs-lookup"><span data-stu-id="8c7e2-134">Only one channel can be created per app</span></span> 
-   <span data-ttu-id="8c7e2-135">Dabei muss die App im Microsoft Store registriert sein</span><span class="sxs-lookup"><span data-stu-id="8c7e2-135">Requires your app to be registered in the Microsoft Store</span></span>

### <a name="creating-a-primary-channel"></a><span data-ttu-id="8c7e2-136">Erstellen eines primären Kanals</span><span class="sxs-lookup"><span data-stu-id="8c7e2-136">Creating a primary channel</span></span> 

```csharp
PushNotificationChannel channel = 
    await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();
```

## <a name="secondary-tile-channels"></a><span data-ttu-id="8c7e2-137">Sekundärer Kachelkanal</span><span class="sxs-lookup"><span data-stu-id="8c7e2-137">Secondary tile channels</span></span>

<span data-ttu-id="8c7e2-138">Hierbei handelt es sich um Kanäle, die Kachel- und Signalaktualisierungen über eine Pushbenachrichtigung an eine sekundäre Kachel senden.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-138">These are channels that can be used to push tile and badge updates to a secondary tile.</span></span> <span data-ttu-id="8c7e2-139">Diese werden von Apps zum Benachrichtigen der Benutzer über interessante Aktivitäten oder Informationen genutzt, mit denen sie in der App interagieren können, wie neue Nachrichten in einem Gruppenchat oder aktualisierte Sportergebnisse.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-139">These are used by apps to notify users of interesting actions or information that they can interact with in the app, such as new messages in a group chat or an updated sports score.</span></span> 

### <a name="what-do-secondary-tile-channels-enable"></a><span data-ttu-id="8c7e2-140">Was aktivieren sekundäre Kachelkanäle?</span><span class="sxs-lookup"><span data-stu-id="8c7e2-140">What do secondary tile channels enable?</span></span>

-   <span data-ttu-id="8c7e2-141">Kachel- oder Signalbenachrichtigungen an eine sekundäre Kachel senden.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-141">Sending tile or badge notifications to secondary tiles.</span></span> <span data-ttu-id="8c7e2-142">Sekundäre Kacheln sind eine hervorragende Möglichkeit, Benutzer wieder auf Ihre App zu locken.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-142">Secondary tiles are a great way to pull users back into your app.</span></span> <span data-ttu-id="8c7e2-143">Sie sind ein Deep-Link für interessante Informationen und das Platzieren relevanter Informationen über die Kacheln lässt diese immer wieder auftauchen.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-143">They are a deep link to information they care about, and putting relevant information on the tiles helps to bring them back again and again.</span></span>
-   <span data-ttu-id="8c7e2-144">Trennung von Kanälen (und abgelaufenen Objekten) zwischen den verschiedenen Kacheln.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-144">Separation of channels (and expiries) between various tiles.</span></span> <span data-ttu-id="8c7e2-145">Dadurch können Sie die Logik im Back-End-zwischen den verschiedenen Typen von sekundären Kacheln trennen, die ein Benutzer an ihre Startseite anheften kann.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-145">This allows you to separate the logic in the backend between the various types of secondary tiles that a user might pin to their start screen.</span></span> 
-   <span data-ttu-id="8c7e2-146">Nachrichtenverschlüsselung während der Übertragung durch Windows mithilfe von TLS.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-146">Message encryption in transit provided by Windows using TLS.</span></span> <span data-ttu-id="8c7e2-147">Nachrichten werden bei der Übertragung auf der Leitung beim Eingang auf WNS und beim Ausgang auf das Gerät des Benutzers verschlüsselt.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-147">Messages are encrypted on the wire both coming into WNS and going to the user's device.</span></span>  

### <a name="limitations-of-secondary-tile-channels"></a><span data-ttu-id="8c7e2-148">Einschränkungen der sekundären Kachelkanäle</span><span class="sxs-lookup"><span data-stu-id="8c7e2-148">Limitations of secondary tile channels</span></span>

-   <span data-ttu-id="8c7e2-149">Popup- oder unformatierte Benachrichtigungen sind nicht zulässig.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-149">No toast or raw notifications allowed.</span></span> <span data-ttu-id="8c7e2-150">Popup- oder unformatierte Benachrichtigungen, die an eine sekundäre Kachel gesendet werden, werden vom System ignoriert.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-150">Toast or raw notifications sent to a secondary tile are ignored by the system.</span></span>
-   <span data-ttu-id="8c7e2-151">Dabei muss die App im Microsoft Store registriert sein</span><span class="sxs-lookup"><span data-stu-id="8c7e2-151">Requires your app to be registered in the Microsoft Store</span></span>


### <a name="creating-a-secondary-tile-channel"></a><span data-ttu-id="8c7e2-152">Erstellen eines sekundären Kachelkanals</span><span class="sxs-lookup"><span data-stu-id="8c7e2-152">Creating a secondary tile channel</span></span> 

```csharp
PushNotificationChannel channel = 
    await PushNotificationChannelManager.CreatePushNotificationChannelForSecondaryTileAsync(tileId);
```

## <a name="alternate-channels"></a><span data-ttu-id="8c7e2-153">Alternative Kanäle</span><span class="sxs-lookup"><span data-stu-id="8c7e2-153">Alternate channels</span></span>

<span data-ttu-id="8c7e2-154">Alternativen Kanäle ermöglichen Apps, Pushbenachrichtigungen zu senden, ohne beim Microsoft Store registriert zu sein oder Pushkanäle außerhalb des primären Kanals zu verwendet, der für die App verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-154">Alternate channels enable apps to send push notifications without registering to the Microsoft Store or creating push channels outside of the primary one used for the app.</span></span> 
 
### <a name="what-do-alternate-channels-enable"></a><span data-ttu-id="8c7e2-155">Was aktivieren alternative Kanäle?</span><span class="sxs-lookup"><span data-stu-id="8c7e2-155">What do alternate channels enable?</span></span>
-   <span data-ttu-id="8c7e2-156">Senden von unformatierten Pushbenachrichtigungen an eine UWP, die auf jedem Windows-Gerät ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-156">Send raw push notifications to a UWP running on any Windows device.</span></span> <span data-ttu-id="8c7e2-157">Alternative Kanäle werden nur für unformatierte Benachrichtigungen verwendet.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-157">Alternate channels only allow for raw notifications.</span></span>
-   <span data-ttu-id="8c7e2-158">Damit können Apps mehrere unformatierte Pushkanäle für verschiedene Features innerhalb der App erstellen.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-158">Allows apps to create multiple raw push channels for different features within the app.</span></span> <span data-ttu-id="8c7e2-159">Eine App kann bis zu 1.000 alternativen Kanäle erstellen und ist jeweils 30Tage lang gültig.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-159">An app can create up to 1000 alternate channels, and each one is valid for 30 days.</span></span> <span data-ttu-id="8c7e2-160">Jeder dieser Kanäle kann separat verwaltet oder von der App widerrufen werden.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-160">Each of these channels can be managed or revoked separately by the app.</span></span>
-   <span data-ttu-id="8c7e2-161">Alternative Pushkanäle können erstellt werden, ohne die App im Microsoft Store zu registrieren.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-161">Alternate push channels can be created without registering an app with the Microsoft Store.</span></span> <span data-ttu-id="8c7e2-162">Wenn Ihre App auf Geräten ohne Registrierung im Microsoft Store installiert werden soll, kann sie auch weiterhin Pushbenachrichtigungen empfangen.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-162">If you app is going to be installed on devices without registering it in the Microsoft Store, it will still be able to receive push notifications.</span></span>
-   <span data-ttu-id="8c7e2-163">Server können mit W3C-Standard-REST-APIs und dem VAPID Protokoll Pushbenachrichtigungen senden.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-163">Servers can push notifications using the W3C standard REST APIs and VAPID protocol.</span></span> <span data-ttu-id="8c7e2-164">Alternative Kanäle nutzen das W3C-Standard-Protokoll. Dadurch können Sie die Serverlogik vereinfachen, die verwaltet werden muss.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-164">Alternate channels use the W3C standard protocol, this allows you to simplify the server logic that needs to be maintained.</span></span>
-   <span data-ttu-id="8c7e2-165">Vollständige Verschlüsselung von End-to-End-Nachrichten.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-165">Full, end-to-end, message encryption.</span></span> <span data-ttu-id="8c7e2-166">Der primäre Kanal stellt Verschlüsselung während der Übertragung bereit. Wenn Sie eine zusätzliche Sicherheit wünschen, ermöglichen alternative Kanäle Ihrer App durch verschlüsselte Header eine Nachricht geschützt zu übertragen.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-166">While the primary channel provides encryption while in transit, if you want to be extra secure, alternate channels enable your app to pass through encryption headers to protect a message.</span></span> 

### <a name="limitations-of-alternate-channels"></a><span data-ttu-id="8c7e2-167">Einschränkungen alternativer Kanäle</span><span class="sxs-lookup"><span data-stu-id="8c7e2-167">Limitations of alternate channels</span></span>
-   <span data-ttu-id="8c7e2-168">Apps können keine Popup-, Kachel- oder Signalpushbenachrichtigungen übertragen.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-168">Apps cannot send toast, tile, or badge type notifications.</span></span> <span data-ttu-id="8c7e2-169">Der alternative Kanal beschränkt die Möglichkeit, andere Arten der Benachrichtigung zu senden.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-169">The alternate channel limits your ability to send other notification types.</span></span> <span data-ttu-id="8c7e2-170">Ihre App kann auch weiterhin lokale Benachrichtigungen über Ihre Hintergrundaufgabe senden.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-170">Your app is still able to send local notifications from your background task.</span></span> 
-   <span data-ttu-id="8c7e2-171">Erfordert eine andere REST-API als die primären oder sekundären Kachelkanäle.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-171">Requires a different REST API than either primary or secondary tile channels.</span></span> <span data-ttu-id="8c7e2-172">Die Verwendung der standardmäßigen W3C-REST-API bedeutet, dass Ihre App eine andere Logik für das Senden von Push-, Kachel- oder Popupbenachrichtigungen verwendet werden muss</span><span class="sxs-lookup"><span data-stu-id="8c7e2-172">Using the standard W3C REST API means that your app will need to have different logic for sending push toast or tile updates</span></span>

### <a name="creating-an-alternate-channel"></a><span data-ttu-id="8c7e2-173">Erstellen eines alternativen Kanals</span><span class="sxs-lookup"><span data-stu-id="8c7e2-173">Creating an alternate channel</span></span> 

```csharp
PushNotificationChannel webChannel = 
    await PushNotificationChannelManager.Current.CreateRawPushNotificationChannelWithAlternateKeyForApplicationAsync(applicationServerKey, appChannelId);
```

## <a name="channel-type-comparison"></a><span data-ttu-id="8c7e2-174">Vergleich von Kanaltypen</span><span class="sxs-lookup"><span data-stu-id="8c7e2-174">Channel type comparison</span></span>
<span data-ttu-id="8c7e2-175">Hier ist eine kurze Gegenüberstellung der unterschiedlichen Arten von Kanälen:</span><span class="sxs-lookup"><span data-stu-id="8c7e2-175">Here is a quick comparison between the different types of channels:</span></span>

<table>

<tr class="header">
<th align="left"><b><span data-ttu-id="8c7e2-176">Typ</span><span class="sxs-lookup"><span data-stu-id="8c7e2-176">Type</span></span></b></th>
<th align="left"><b><span data-ttu-id="8c7e2-177">Popupbenachrichtigung?</span><span class="sxs-lookup"><span data-stu-id="8c7e2-177">Push toast?</span></span></b></th>
<th align="left"><b><span data-ttu-id="8c7e2-178">Kachel-/Signalbenachrichtigung?</span><span class="sxs-lookup"><span data-stu-id="8c7e2-178">Push tile/badge?</span></span></b></th>
<th align="left"><b><span data-ttu-id="8c7e2-179">Unformatierte Pushbenachrichtigungen?</span><span class="sxs-lookup"><span data-stu-id="8c7e2-179">Push raw notifications?</span></span></b></th>
<th align="left"><b><span data-ttu-id="8c7e2-180">Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="8c7e2-180">Authentication</span></span></b></th>
<th align="left"><b><span data-ttu-id="8c7e2-181">API</span><span class="sxs-lookup"><span data-stu-id="8c7e2-181">API</span></span></b></th>
<th align="left"><b><span data-ttu-id="8c7e2-182">Ist eine Store-Registrierung erforderlich?</span><span class="sxs-lookup"><span data-stu-id="8c7e2-182">Store registration required?</span></span></b></th>
<th align="left"><b><span data-ttu-id="8c7e2-183">Kanäle</span><span class="sxs-lookup"><span data-stu-id="8c7e2-183">Channels</span></span></b></th>
<th align="left"><b><span data-ttu-id="8c7e2-184">Verschlüsselung</span><span class="sxs-lookup"><span data-stu-id="8c7e2-184">Encryption</span></span></b></th>
</tr>


<tr class="odd">
<td align="left"><span data-ttu-id="8c7e2-185">Primär</span><span class="sxs-lookup"><span data-stu-id="8c7e2-185">Primary</span></span></td>
<td align="left"><span data-ttu-id="8c7e2-186">Ja</span><span class="sxs-lookup"><span data-stu-id="8c7e2-186">Yes</span></span></td>
<td align="left"><span data-ttu-id="8c7e2-187">Ja – nur primäre Kachel</span><span class="sxs-lookup"><span data-stu-id="8c7e2-187">Yes - primary tile only</span></span></td>
<td align="left"><span data-ttu-id="8c7e2-188">Ja</span><span class="sxs-lookup"><span data-stu-id="8c7e2-188">Yes</span></span></td>
<td align="left"><span data-ttu-id="8c7e2-189">OAuth</span><span class="sxs-lookup"><span data-stu-id="8c7e2-189">OAuth</span></span></td>
<td align="left"><span data-ttu-id="8c7e2-190">WNS REST API</span><span class="sxs-lookup"><span data-stu-id="8c7e2-190">WNS REST API</span></span></td>
<td align="left"><span data-ttu-id="8c7e2-191">Ja</span><span class="sxs-lookup"><span data-stu-id="8c7e2-191">Yes</span></span></td>
<td align="left"><span data-ttu-id="8c7e2-192">Einer pro App</span><span class="sxs-lookup"><span data-stu-id="8c7e2-192">One per app</span></span></td>
<td align="left"><span data-ttu-id="8c7e2-193">Während der Übertragung</span><span class="sxs-lookup"><span data-stu-id="8c7e2-193">In Transit</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="8c7e2-194">Sekundäre Kachel</span><span class="sxs-lookup"><span data-stu-id="8c7e2-194">Secondary Tile</span></span></td>
<td align="left"><span data-ttu-id="8c7e2-195">Nein</span><span class="sxs-lookup"><span data-stu-id="8c7e2-195">No</span></span></td>
<td align="left"><span data-ttu-id="8c7e2-196">Ja – nur sekundäre Kachel</span><span class="sxs-lookup"><span data-stu-id="8c7e2-196">Yes - secondary tile only</span></span></td>
<td align="left"><span data-ttu-id="8c7e2-197">Nein</span><span class="sxs-lookup"><span data-stu-id="8c7e2-197">No</span></span></td>
<td align="left"><span data-ttu-id="8c7e2-198">OAuth</span><span class="sxs-lookup"><span data-stu-id="8c7e2-198">OAuth</span></span></td>
<td align="left"><span data-ttu-id="8c7e2-199">WNS REST API</span><span class="sxs-lookup"><span data-stu-id="8c7e2-199">WNS REST API</span></span></td>
<td align="left"><span data-ttu-id="8c7e2-200">Ja</span><span class="sxs-lookup"><span data-stu-id="8c7e2-200">Yes</span></span></td>
<td align="left"><span data-ttu-id="8c7e2-201">Einer pro sekundärer Kachel</span><span class="sxs-lookup"><span data-stu-id="8c7e2-201">One per secondary tile</span></span></td>
<td align="left"><span data-ttu-id="8c7e2-202">Während der Übertragung</span><span class="sxs-lookup"><span data-stu-id="8c7e2-202">In Transit</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="8c7e2-203">Alternativ</span><span class="sxs-lookup"><span data-stu-id="8c7e2-203">Alternate</span></span></td>
<td align="left"><span data-ttu-id="8c7e2-204">Nein</span><span class="sxs-lookup"><span data-stu-id="8c7e2-204">No</span></span></td>
<td align="left"><span data-ttu-id="8c7e2-205">Nein</span><span class="sxs-lookup"><span data-stu-id="8c7e2-205">No</span></span></td>
<td align="left"><span data-ttu-id="8c7e2-206">Ja</span><span class="sxs-lookup"><span data-stu-id="8c7e2-206">Yes</span></span></td>
<td align="left"><span data-ttu-id="8c7e2-207">VAPID</span><span class="sxs-lookup"><span data-stu-id="8c7e2-207">VAPID</span></span></td>
<td align="left"><span data-ttu-id="8c7e2-208">WebPush W3C-Standard</span><span class="sxs-lookup"><span data-stu-id="8c7e2-208">WebPush W3C Standard</span></span></td>
<td align="left"><span data-ttu-id="8c7e2-209">Nein</span><span class="sxs-lookup"><span data-stu-id="8c7e2-209">No</span></span></td>
<td align="left"><span data-ttu-id="8c7e2-210">1.000 Pro App</span><span class="sxs-lookup"><span data-stu-id="8c7e2-210">1,000 per app</span></span></td>
<td align="left"><span data-ttu-id="8c7e2-211">Während der Übertragung + End-to-End-Verschlüsselung ist mit Pass-Through-Header möglich (erfordert einen App-Code)</span><span class="sxs-lookup"><span data-stu-id="8c7e2-211">In transit + end to end encryption possible with header pass through (requires app code)</span></span></td>
</tr>
</table>

## <a name="choosing-the-right-channel"></a><span data-ttu-id="8c7e2-212">Auswählen des richtigen Kanals</span><span class="sxs-lookup"><span data-stu-id="8c7e2-212">Choosing the right channel</span></span>

<span data-ttu-id="8c7e2-213">Im Allgemeinen wird empfohlen, den primären Kanal in Ihrer App zu verwenden – mit einigen Ausnahmen:</span><span class="sxs-lookup"><span data-stu-id="8c7e2-213">In general, we recommend using the primary channel in your app, with a few exceptions:</span></span> 

1. <span data-ttu-id="8c7e2-214">Wenn Sie eine Kachelaktualisierung an eine sekundäre Kachel senden, verwenden Sie den sekundären Kachel-Pushkanal.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-214">If you are pushing a tile update to a secondary tile, use the secondary tile push channel.</span></span>
2. <span data-ttu-id="8c7e2-215">Wenn Sie Kanäle an andere Dienste übergeben (z.B. an einen Browser), verwenden Sie den alternativen Kanal.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-215">If you are passing out channels to other services (such as in the case of a browser) use the alternate channel.</span></span>
3. <span data-ttu-id="8c7e2-216">Wenn Sie eine App erstellen, die nicht im Windows Store aufgeführt wird (z.B. eine Branchen-App) verwenden Sie einen alternativen Kanal.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-216">If you are creating an app that won't be listed in the Windows store (such as an LOB app) use an alternate channel.</span></span>
4. <span data-ttu-id="8c7e2-217">Wenn Sie einen vorhandenen Web-Benachrichtigungscode auf dem Server haben, den Sie wiederverwenden möchten oder wenn Sie mehrere Kanäle in Ihrem Back-End-Dienst benötigen, verwenden Sie alternative Kanäle.</span><span class="sxs-lookup"><span data-stu-id="8c7e2-217">If you have existing web push code on your server you wish to reuse or have a need for multiple channels in your backend service, use alternate channels.</span></span>

## <a name="related-articles"></a><span data-ttu-id="8c7e2-218">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="8c7e2-218">Related articles</span></span>

* [<span data-ttu-id="8c7e2-219">Senden einer lokalen Kachelbenachrichtigung</span><span class="sxs-lookup"><span data-stu-id="8c7e2-219">Send a local tile notification</span></span>](../tiles-and-notifications/sending-a-local-tile-notification.md)
* [<span data-ttu-id="8c7e2-220">Adaptive und interaktive Popupbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="8c7e2-220">Adaptive and interactive toast notifications</span></span>](../tiles-and-notifications/adaptive-interactive-toasts.md)
* [<span data-ttu-id="8c7e2-221">Schnellstart: Senden einer Pushbenachrichtigung</span><span class="sxs-lookup"><span data-stu-id="8c7e2-221">Quickstart: Sending a push notification</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/hh868252)
* [<span data-ttu-id="8c7e2-222">So wird's gemacht: Aktualisieren eines Signals durch Pushbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="8c7e2-222">How to update a badge through push notifications</span></span>](https://msdn.microsoft.com/library/windows/apps/hh465450)
* [<span data-ttu-id="8c7e2-223">So wird's gemacht: Anfordern, Erstellen und Speichern eines Benachrichtigungskanals</span><span class="sxs-lookup"><span data-stu-id="8c7e2-223">How to request, create, and save a notification channel</span></span>](https://msdn.microsoft.com/library/windows/apps/hh465412)
* [<span data-ttu-id="8c7e2-224">So wird's gemacht: Abfangen von Benachrichtigungen für ausgeführte Anwendungen</span><span class="sxs-lookup"><span data-stu-id="8c7e2-224">How to intercept notifications for running applications</span></span>](https://msdn.microsoft.com/library/windows/apps/hh465450)
* [<span data-ttu-id="8c7e2-225">So wird's gemacht: Authentifizieren mit dem Windows-Pushbenachrichtigungsdienst (Windows Push Notification Service, WNS)</span><span class="sxs-lookup"><span data-stu-id="8c7e2-225">How to authenticate with the Windows Push Notification Service (WNS)</span></span>](https://msdn.microsoft.com/library/windows/apps/hh465407)
* [<span data-ttu-id="8c7e2-226">Anforderungs- und Antwortheader des Pushbenachrichtigungsdiensts</span><span class="sxs-lookup"><span data-stu-id="8c7e2-226">Push notification service request and response headers</span></span>](https://msdn.microsoft.com/library/windows/apps/hh465435)
* [<span data-ttu-id="8c7e2-227">Richtlinien und Prüfliste für Pushbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="8c7e2-227">Guidelines and checklist for push notifications</span></span>](https://msdn.microsoft.com/library/windows/apps/hh761462)
* [<span data-ttu-id="8c7e2-228">Unformatierte Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="8c7e2-228">Raw notifications</span></span>](raw-notification-overview.md)
