---
author: mijacobs
Description: This article covers the four notification options&\#8212;local, scheduled, periodic, and push&\#8212;that deliver tile and badge updates and toast notification content.
title: Auswählen einer Methode für die Übermittlung von Benachrichtigungen
ms.assetid: FDB43EDE-C5F2-493F-952C-55401EC5172B
label: Choose a notification delivery method
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
keywords: windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: c01b96f70bd39c43f321935aa47393ada0400319
ms.sourcegitcommit: ed0304b8a214c03b8aab74b8ef12c9f82b8e3c5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "7281905"
---
# <a name="choose-a-notification-delivery-method"></a><span data-ttu-id="3e228-103">Auswählen einer Methode für die Übermittlung von Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="3e228-103">Choose a notification delivery method</span></span>

 


<span data-ttu-id="3e228-104">In diesem Artikel werden die vier Benachrichtigungsoptionen – lokal, geplant, periodisch und Push – behandelt, die Kachel- und Signalaktualisierungen sowie Popupbenachrichtigungsinhalte bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="3e228-104">This article covers the four notification options—local, scheduled, periodic, and push—that deliver tile and badge updates and toast notification content.</span></span> <span data-ttu-id="3e228-105">Eine Kachel oder eine Popupbenachrichtigung kann dem Benutzer Informationen anzeigen, auch wenn der Benutzer nicht direkt mit Ihrer App beschäftigt ist.</span><span class="sxs-lookup"><span data-stu-id="3e228-105">A tile or a toast notification can get information to your user even when the user is not directly engaged with your app.</span></span> <span data-ttu-id="3e228-106">Basierend auf der Art und dem Inhalt Ihrer App sowie den Informationen, die Sie bereitstellen möchten, können Sie die am besten geeignete Benachrichtigungsmethode bzw. -methoden für Ihr Szenario bestimmen.</span><span class="sxs-lookup"><span data-stu-id="3e228-106">The nature and content of your app and the information that you want to deliver can help you determine which notification method or methods is best for your scenario.</span></span>

## <a name="notification-delivery-methods-overview"></a><span data-ttu-id="3e228-107">Übersicht über Methoden für die Benachrichtigungsübermittlung</span><span class="sxs-lookup"><span data-stu-id="3e228-107">Notification delivery methods overview</span></span>


<span data-ttu-id="3e228-108">Es gibt vier Mechanismen, die von einer App zum Übermitteln einer Benachrichtigung verwendet werden können:</span><span class="sxs-lookup"><span data-stu-id="3e228-108">There are four mechanisms that an app can use to deliver a notification:</span></span>

-   **<span data-ttu-id="3e228-109">Lokal</span><span class="sxs-lookup"><span data-stu-id="3e228-109">Local</span></span>**
-   **<span data-ttu-id="3e228-110">Geplant</span><span class="sxs-lookup"><span data-stu-id="3e228-110">Scheduled</span></span>**
-   **<span data-ttu-id="3e228-111">Periodisch</span><span class="sxs-lookup"><span data-stu-id="3e228-111">Periodic</span></span>**
-   **<span data-ttu-id="3e228-112">Push</span><span class="sxs-lookup"><span data-stu-id="3e228-112">Push</span></span>**

<span data-ttu-id="3e228-113">In dieser Tabelle sind die Benachrichtigungsübermittlungstypen zusammengefasst.</span><span class="sxs-lookup"><span data-stu-id="3e228-113">This table summarizes the notification delivery types.</span></span>

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="3e228-114">Übermittlungsmethode</span><span class="sxs-lookup"><span data-stu-id="3e228-114">Delivery method</span></span></th>
<th align="left"><span data-ttu-id="3e228-115">Verwendungsart</span><span class="sxs-lookup"><span data-stu-id="3e228-115">Use with</span></span></th>
<th align="left"><span data-ttu-id="3e228-116">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3e228-116">Description</span></span></th>
<th align="left"><span data-ttu-id="3e228-117">Beispiele</span><span class="sxs-lookup"><span data-stu-id="3e228-117">Examples</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="3e228-118">Lokal</span><span class="sxs-lookup"><span data-stu-id="3e228-118">Local</span></span></td>
<td align="left"><span data-ttu-id="3e228-119">Kachel, Signal, Popup</span><span class="sxs-lookup"><span data-stu-id="3e228-119">Tile, Badge, Toast</span></span></td>
<td align="left"><span data-ttu-id="3e228-120">Eine Reihe von API-Aufrufen, die Benachrichtigungen senden, während Ihre App ausgeführt wird, und die Kachel oder das Signal direkt aktualisieren oder eine Popupbenachrichtigung senden.</span><span class="sxs-lookup"><span data-stu-id="3e228-120">A set of API calls that send notifications while your app is running, directly updating the tile or badge, or sending a toast notification.</span></span></td>
<td align="left"><ul>
<li><span data-ttu-id="3e228-121">Eine Musik-App aktualisiert ihre Kachel so, dass &quot;Aktuelle Wiedergabe&quot; angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="3e228-121">A music app updates its tile to show what's &quot;Now Playing&quot;.</span></span></li>
<li><span data-ttu-id="3e228-122">Eine Spiele-App aktualisiert ihre Kachel mit der Bestwertung des Benutzers, wenn dieser das Spiel verlässt.</span><span class="sxs-lookup"><span data-stu-id="3e228-122">A game app updates its tile with the user's high score when the user leaves the game.</span></span></li>
<li><span data-ttu-id="3e228-123">Ein Signal, dessen Symbol anzeigt, dass neue Informationen in der App gelöscht werden, wenn die App aktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="3e228-123">A badge whose glyph indicates that there's new info int the app is cleared when the app is activated.</span></span></li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="3e228-124">Geplant</span><span class="sxs-lookup"><span data-stu-id="3e228-124">Scheduled</span></span></td>
<td align="left"><span data-ttu-id="3e228-125">Kachel, Popup</span><span class="sxs-lookup"><span data-stu-id="3e228-125">Tile, Toast</span></span></td>
<td align="left"><span data-ttu-id="3e228-126">Eine Reihe von API-Aufrufen, die eine Benachrichtigung im Voraus so planen, dass zum von Ihnen angegebenen Zeitpunkt eine Aktualisierung vorgenommen wird.</span><span class="sxs-lookup"><span data-stu-id="3e228-126">A set of API calls that schedule a notification in advance, to update at the time you specify.</span></span></td>
<td align="left"><ul>
<li><span data-ttu-id="3e228-127">Eine Kalender-App verwendet für eine anstehende Besprechung eine Erinnerung in Form einer Popupbenachrichtigung.</span><span class="sxs-lookup"><span data-stu-id="3e228-127">A calendar app sets a toast notification reminder for an upcoming meeting.</span></span></li>
</ul></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="3e228-128">Periodisch</span><span class="sxs-lookup"><span data-stu-id="3e228-128">Periodic</span></span></td>
<td align="left"><span data-ttu-id="3e228-129">Kachel, Signal</span><span class="sxs-lookup"><span data-stu-id="3e228-129">Tile, Badge</span></span></td>
<td align="left"><span data-ttu-id="3e228-130">Benachrichtigungen, mit denen Kacheln und Signale regelmäßig in einem festen Zeitintervall durch Abrufen von neuem Inhalt aus einem Clouddienst aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="3e228-130">Notifications that update tiles and badges regularly at a fixed time interval by polling a cloud service for new content.</span></span></td>
<td align="left"><ul>
<li><span data-ttu-id="3e228-131">Eine Wetter-App aktualisiert ihre Kachel, in der die Vorschau angezeigt wird, in Intervallen von 30 Minuten.</span><span class="sxs-lookup"><span data-stu-id="3e228-131">A weather app updates its tile, which shows the forecast, at 30-minute intervals.</span></span></li>
<li><span data-ttu-id="3e228-132">Eine Website für &quot;Tägliche Deals&quot; aktualisiert ihren Deal des Tages jeden Morgen.</span><span class="sxs-lookup"><span data-stu-id="3e228-132">A &quot;daily deals&quot; site updates its deal-of-the-day every morning.</span></span></li>
<li><span data-ttu-id="3e228-133">Eine Kachel, welche die Anzahl der Tage bis zu einem Ereignis anzeigt, aktualisiert den angezeigten Countdown jeden Tag um Mitternacht.</span><span class="sxs-lookup"><span data-stu-id="3e228-133">A tile that displays the days until an event updates the displayed countdown each day at midnight.</span></span></li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="3e228-134">Push</span><span class="sxs-lookup"><span data-stu-id="3e228-134">Push</span></span></td>
<td align="left"><span data-ttu-id="3e228-135">Kachel, Signal, Popup, Raw</span><span class="sxs-lookup"><span data-stu-id="3e228-135">Tile, Badge, Toast, Raw</span></span></td>
<td align="left"><span data-ttu-id="3e228-136">Von einem Cloudserver gesendete Benachrichtigungen, selbst wenn die App nicht ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="3e228-136">Notifications sent from a cloud server, even if your app isn't running.</span></span></td>
<td align="left"><ul>
<li><span data-ttu-id="3e228-137">Eine Shopping-App sendet eine Popupbenachrichtigung, um einen Benutzer über den Rabatt eines Artikels zu informieren, den er sich gerade ansieht.</span><span class="sxs-lookup"><span data-stu-id="3e228-137">A shopping app sends a toast notification to let a user know about a sale on an item that they're watching.</span></span></li>
<li><span data-ttu-id="3e228-138">Eine Nachrichten-App aktualisiert ihre Kachel mit Eilmeldungen, sobald sich die entsprechenden Geschehnisse ereignen.</span><span class="sxs-lookup"><span data-stu-id="3e228-138">A news app updates its tile with breaking news as it happens.</span></span></li>
<li><span data-ttu-id="3e228-139">Eine Sport-App hält ihre Kachel während eines laufenden Spiels auf dem neuesten Stand.</span><span class="sxs-lookup"><span data-stu-id="3e228-139">A sports app keeps its tile up-to-date during an ongoing game.</span></span></li>
<li><span data-ttu-id="3e228-140">Eine Kommunikations-App bietet Alarme zu eingehenden Nachrichten oder Telefonanrufen.</span><span class="sxs-lookup"><span data-stu-id="3e228-140">A communication app provides alerts about incoming messages or phone calls.</span></span></li>
</ul></td>
</tr>
</tbody>
</table>

 

## <a name="local-notifications"></a><span data-ttu-id="3e228-141">Lokale Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="3e228-141">Local notifications</span></span>


<span data-ttu-id="3e228-142">Das Aktualisieren der App-Kachel oder des Signals oder das Auslösen einer Popupbenachrichtigung, während die App ausgeführt wird, stellt den einfachsten der Mechanismen zur Benachrichtigungsübermittlung dar. Dafür werden nur lokale API-Aufrufe benötigt.</span><span class="sxs-lookup"><span data-stu-id="3e228-142">Updating the app tile or badge or raising a toast notification while the app is running is the simplest of the notification delivery mechanisms; it only requires local API calls.</span></span> <span data-ttu-id="3e228-143">Für jede App kann es hilfreiche oder interessante Informationen zum Anzeigen auf der Kachel geben – auch dann, wenn sich dieser Inhalt erst ändert, nachdem der Benutzer die App gestartet hat und mit ihr interagiert.</span><span class="sxs-lookup"><span data-stu-id="3e228-143">Every app can have useful or interesting information to show on the tile, even if that content only changes after the user launches and interacts with the app.</span></span> <span data-ttu-id="3e228-144">Lokale Benachrichtigungen sind auch eine gute Möglichkeit, die App-Kachel aktuell zu halten, selbst wenn Sie auch einen der anderen Benachrichtigungsmechanismen verwenden.</span><span class="sxs-lookup"><span data-stu-id="3e228-144">Local notifications are also a good way to keep the app tile current, even if you also use one of the other notification mechanisms.</span></span> <span data-ttu-id="3e228-145">Auf der Kachel einer Foto-App könnten z.B. Fotos aus einem kürzlich hinzugefügten Album angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="3e228-145">For instance, a photo app tile could show photos from a recently added album.</span></span>

<span data-ttu-id="3e228-146">Es empfiehlt sich, die Kachel beim ersten Start der App lokal zu aktualisieren (oder spätestens dann, wenn der Benutzer eine Änderung vornimmt, die üblicherweise auf der Kachel zu sehen ist).</span><span class="sxs-lookup"><span data-stu-id="3e228-146">We recommended that your app update its tile locally on first launch, or at least immediately after the user makes a change that your app would normally reflect on the tile.</span></span> <span data-ttu-id="3e228-147">Indem Sie diese Änderung schon während der Verwendung der App vornehmen, stellen Sie sicher, dass die Kachel bereits auf dem neuesten Stand ist, wenn der Benutzer die App beendet.</span><span class="sxs-lookup"><span data-stu-id="3e228-147">That update isn't seen until the user leaves the app, but by making that change while the app is being used ensures that the tile is already up-to-date when the user departs.</span></span>

<span data-ttu-id="3e228-148">Auch wenn die API-Aufrufe lokal erfolgen, können die Benachrichtigungen auf Webbilder verweisen.</span><span class="sxs-lookup"><span data-stu-id="3e228-148">While the API calls are local, the notifications can reference web images.</span></span> <span data-ttu-id="3e228-149">Wenn das Webbild nicht zum Download verfügbar oder beschädigt ist oder nicht den Bildspezifikationen entspricht, reagieren Kacheln und Popups unterschiedlich:</span><span class="sxs-lookup"><span data-stu-id="3e228-149">If the web image is not available for download, is corrupted, or doesn't meet the image specifications, tiles and toast respond differently:</span></span>

-   <span data-ttu-id="3e228-150">Kacheln: Die Aktualisierung wird nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3e228-150">Tiles: The update is not shown</span></span>
-   <span data-ttu-id="3e228-151">Popup: Die Benachrichtigung wird angezeigt, das Bild wird jedoch gelöscht.</span><span class="sxs-lookup"><span data-stu-id="3e228-151">Toast: The notification is displayed, but your image is dropped</span></span>

<span data-ttu-id="3e228-152">Standardmäßig laufen lokale Popupbenachrichtigungen in drei Tagen und lokale Kachelbenachrichtigungen niemals ab.</span><span class="sxs-lookup"><span data-stu-id="3e228-152">By default, local toast notifications expire in three days, and local tile notifications never expire.</span></span> <span data-ttu-id="3e228-153">Es wird empfohlen, diese Standardeinstellungen mit einer expliziten Ablaufzeit zu überschreiben, die für Ihre Benachrichtigungen sinnvoll ist. (Die Ablaufzeit von Benachrichtigungen beträgt maximal drei Tage.)</span><span class="sxs-lookup"><span data-stu-id="3e228-153">We recommend overriding these defaults with an explicit expiration time that makes sense for your notifications (toasts have a max of three days).</span></span> 

<span data-ttu-id="3e228-154">Weitere Informationen finden Sie in folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="3e228-154">For more information, see these topics:</span></span>

-   [<span data-ttu-id="3e228-155">Senden einer lokalen Kachelbenachrichtigung</span><span class="sxs-lookup"><span data-stu-id="3e228-155">Send a local tile notification</span></span>](sending-a-local-tile-notification.md)
-   [<span data-ttu-id="3e228-156">Senden einer lokalen Popupbenachrichtigung</span><span class="sxs-lookup"><span data-stu-id="3e228-156">Send a local toast notification</span></span>](send-local-toast.md)
-   [<span data-ttu-id="3e228-157">Codebeispiele für Benachrichtigungen für die Universelle Windows-Plattform (UWP-Benachrichtigungen)</span><span class="sxs-lookup"><span data-stu-id="3e228-157">Universal Windows Platform (UWP) notifications code samples</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Notifications)

## <a name="scheduled-notifications"></a><span data-ttu-id="3e228-158">Geplante Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="3e228-158">Scheduled notifications</span></span>


<span data-ttu-id="3e228-159">Geplante Benachrichtigungen sind lokale Benachrichtigungen, die den genauen Zeitpunkt angeben können, zu dem eine Kachel aktualisiert oder eine Popupbenachrichtigung angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="3e228-159">Scheduled notifications are the subset of local notifications that can specify the precise time when a tile should be updated or a toast notification should be shown.</span></span> <span data-ttu-id="3e228-160">Geplante Benachrichtigungen eignen sich ideal für Situationen, in denen der zu aktualisierende Inhalt im Voraus bekannt ist (z.B. eine Besprechungseinladung).</span><span class="sxs-lookup"><span data-stu-id="3e228-160">Scheduled notifications are ideal in situations where the content to be updated is known in advance, such as a meeting invitation.</span></span> <span data-ttu-id="3e228-161">Wenn Sie den Benachrichtigungsinhalt vorher nicht kennen, müssen Sie eine Pushbenachrichtigung oder eine lokale Benachrichtigung verwenden.</span><span class="sxs-lookup"><span data-stu-id="3e228-161">If you don't have advance knowledge of the notification content, you should use a push or periodic notification.</span></span>

<span data-ttu-id="3e228-162">Beachten Sie, dass geplante Benachrichtigungen nicht für Signalbenachrichtigungen verwendet werden können. Signalbenachrichtigungen werden am besten mithilfe lokaler, regelmäßiger oder Pushbenachrichtigungen bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="3e228-162">Note that scheduled notifications cannot be used for badge notifications; badge notifications are best served by local, periodic, or push notifications.</span></span>

<span data-ttu-id="3e228-163">Geplante Benachrichtigungen laufen standardmäßig drei Tage nach Zustellung ab.</span><span class="sxs-lookup"><span data-stu-id="3e228-163">By default, scheduled notifications expire three days from the time they are delivered.</span></span> <span data-ttu-id="3e228-164">Sie können diese Standardeinstellung für die Ablaufzeit für geplante Kachelbenachrichtigungen überschreiben, jedoch nicht die Ablaufzeit für geplante Popups.</span><span class="sxs-lookup"><span data-stu-id="3e228-164">You can override this default expiration time on scheduled tile notifications, but you cannot override the expiration time on scheduled toasts.</span></span>

<span data-ttu-id="3e228-165">Weitere Informationen finden Sie in folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="3e228-165">For more information, see these topics:</span></span>

-   [<span data-ttu-id="3e228-166">Codebeispiele für Benachrichtigungen für die Universelle Windows-Plattform (UWP-Benachrichtigungen)</span><span class="sxs-lookup"><span data-stu-id="3e228-166">Universal Windows Platform (UWP) notifications code samples</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Notifications)

## <a name="periodic-notifications"></a><span data-ttu-id="3e228-167">Periodische Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="3e228-167">Periodic notifications</span></span>


<span data-ttu-id="3e228-168">Periodische Benachrichtigungen bieten Ihnen Livekachelaktualisierungen mit minimaler Investition in Clouddienst und Client.</span><span class="sxs-lookup"><span data-stu-id="3e228-168">Periodic notifications give you live tile updates with a minimal cloud service and client investment.</span></span> <span data-ttu-id="3e228-169">Sie stellen auch eine exzellente Methode zum Verteilen desselben Inhalts an eine große Zielgruppe dar.</span><span class="sxs-lookup"><span data-stu-id="3e228-169">They are also an excellent method of distributing the same content to a wide audience.</span></span> <span data-ttu-id="3e228-170">Ihr Clientcode gibt die URL eines Cloudspeicherorts an, von dem Windows Kachel- und Signalaktualisierungen abruft, und die Häufigkeit, mit der der Speicherort abgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="3e228-170">Your client code specifies the URL of a cloud location that Windows polls for tile or badge updates, and how often the location should be polled.</span></span> <span data-ttu-id="3e228-171">In jedem Abrufintervall wird die URL von Windows aufgerufen, um den angegebene XML-Inhalt herunterzuladen und auf der Kachel anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="3e228-171">At each polling interval, Windows contacts the URL to download the specified XML content and display it on the tile.</span></span>

<span data-ttu-id="3e228-172">Für periodische Benachrichtigungen muss die App einen Clouddienst hosten, und dieser Dienst wird im angegebenen Intervall von allen Benutzern abgerufen, die die App installiert haben.</span><span class="sxs-lookup"><span data-stu-id="3e228-172">Periodic notifications require the app to host a cloud service, and this service will be polled at the specified interval by all users who have the app installed.</span></span> <span data-ttu-id="3e228-173">Beachten Sie, dass periodische Aktualisierungen nicht für Popupbenachrichtigungen verwendet werden können. Popupbenachrichtigungen werden am besten mithilfe von geplanten Benachrichtigungen oder Pushbenachrichtigungen bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="3e228-173">Note that periodic updates cannot be used for toast notifications; toast notifications are best served by scheduled or push notifications.</span></span>

<span data-ttu-id="3e228-174">Regelmäßige Benachrichtigungen laufen standardmäßig drei Tage nach der Abfrage ab.</span><span class="sxs-lookup"><span data-stu-id="3e228-174">By default, periodic notifications expire three days from the time polling occurs.</span></span> <span data-ttu-id="3e228-175">Diese Standardeinstellung kann bei Bedarf mit einer anderen Ablaufzeit explizit überschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="3e228-175">If needed, you can override this default with an explicit expiration time.</span></span>

<span data-ttu-id="3e228-176">Weitere Informationen finden Sie unter folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="3e228-176">For more information, see these topics:</span></span>

-   [<span data-ttu-id="3e228-177">Übersicht über regelmäßige Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="3e228-177">Periodic notification overview</span></span>](periodic-notification-overview.md)
-   [<span data-ttu-id="3e228-178">Codebeispiele für UWP (universelle Windows-Plattform)-Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="3e228-178">Universal Windows Platform (UWP) notifications code samples</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Notifications)

## <a name="push-notifications"></a><span data-ttu-id="3e228-179">Pushbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="3e228-179">Push notifications</span></span>


<span data-ttu-id="3e228-180">Pushbenachrichtigungen eignen sich ideal zum Kommunizieren von Echtzeitdaten oder für den Benutzer personalisierten Daten.</span><span class="sxs-lookup"><span data-stu-id="3e228-180">Push notifications are ideal to communicate real-time data or data that is personalized for your user.</span></span> <span data-ttu-id="3e228-181">Pushbenachrichtigungen werden auch für Inhalte verwendet, die zu unvorhersehbaren Zeiten generiert werden (z.B. Eilmeldungen oder Chatnachrichten).</span><span class="sxs-lookup"><span data-stu-id="3e228-181">Push notifications are used for content that is generated at unpredictable times, such as breaking news, social network updates, or instant messages.</span></span> <span data-ttu-id="3e228-182">Pushbenachrichtigungen sind auch in Situationen hilfreich, in denen Daten so zeitempfindlich sind, dass periodische Benachrichtigungen nicht geeignet wären (z.B. Spielstände während eines Spiels).</span><span class="sxs-lookup"><span data-stu-id="3e228-182">Push notifications are also useful in situations where the data is time-sensitive in a way that would not suit periodic notifications, such as sports scores during a game.</span></span>

<span data-ttu-id="3e228-183">Für Pushbenachrichtigungen ist ein Cloud-Dienst erforderlich, der Pushbenachrichtigungskanäle verwaltet und festlegt, wann und an wen Benachrichtigungen gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="3e228-183">Push notifications require a cloud service that manages push notification channels and chooses when and to whom to send notifications.</span></span>

<span data-ttu-id="3e228-184">Pushbenachrichtigungen laufen standardmäßig drei Tage nach Empfang durch das Gerät ab.</span><span class="sxs-lookup"><span data-stu-id="3e228-184">By default, push notifications expire three days from the time they are received by the device.</span></span> <span data-ttu-id="3e228-185">Diese Standardeinstellung kann bei Bedarf mit einer expliziten Ablaufzeit überschrieben werden. (Für Popups gilt eine maximale Ablaufzeit von drei Tagen.)</span><span class="sxs-lookup"><span data-stu-id="3e228-185">If needed, you can override this default with an explicit expiration time (toasts have a max of three days).</span></span>

<span data-ttu-id="3e228-186">Weitere Informationen finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="3e228-186">For more information, see:</span></span>

-   [<span data-ttu-id="3e228-187">Übersicht über Windows-Pushbenachrichtigungsdienste (Windows Push Notification Services, WNS)</span><span class="sxs-lookup"><span data-stu-id="3e228-187">Windows Push Notification Services (WNS) overview</span></span>](windows-push-notification-services--wns--overview.md)
-   [<span data-ttu-id="3e228-188">Richtlinien für Pushbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="3e228-188">Guidelines for push notifications</span></span>](https://msdn.microsoft.com/library/windows/apps/hh761462)
-   [<span data-ttu-id="3e228-189">Codebeispiele für Benachrichtigungen für die Universelle Windows-Plattform (UWP-Benachrichtigungen)</span><span class="sxs-lookup"><span data-stu-id="3e228-189">Universal Windows Platform (UWP) notifications code samples</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Notifications)


## <a name="related-topics"></a><span data-ttu-id="3e228-190">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="3e228-190">Related topics</span></span>


* [<span data-ttu-id="3e228-191">Senden einer lokalen Kachelbenachrichtigung</span><span class="sxs-lookup"><span data-stu-id="3e228-191">Send a local tile notification</span></span>](sending-a-local-tile-notification.md)
* [<span data-ttu-id="3e228-192">Senden einer lokalen Popupbenachrichtigung</span><span class="sxs-lookup"><span data-stu-id="3e228-192">Send a local toast notification</span></span>](send-local-toast.md)
* [<span data-ttu-id="3e228-193">Richtlinien für Pushbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="3e228-193">Guidelines for push notifications</span></span>](https://msdn.microsoft.com/library/windows/apps/hh761462)
* [<span data-ttu-id="3e228-194">Richtlinien für Popupbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="3e228-194">Guidelines for toast notifications</span></span>](https://msdn.microsoft.com/library/windows/apps/hh465391)
* [<span data-ttu-id="3e228-195">Übersicht über regelmäßige Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="3e228-195">Periodic notification overview</span></span>](periodic-notification-overview.md)
* [<span data-ttu-id="3e228-196">Übersicht über die Windows-Pushbenachrichtigungsdienste (Windows Push Notification Services, WNS)</span><span class="sxs-lookup"><span data-stu-id="3e228-196">Windows Push Notification Services (WNS) overview</span></span>](windows-push-notification-services--wns--overview.md)
* [<span data-ttu-id="3e228-197">Codebeispiele für UWP (universelle Windows-Plattform)-Benachrichtigungen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="3e228-197">Universal Windows Platform (UWP) notifications code samples on GitHub</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Notifications)
 

 




