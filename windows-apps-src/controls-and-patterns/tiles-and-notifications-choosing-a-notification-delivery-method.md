---
author: mijacobs
Description: In diesem Artikel werden die vier Benachrichtigungsoptionen&\#8212;lokal, geplant, periodisch und Push&\#8212;behandelt, die Kachel- und Signalaktualisierungen sowie Popupbenachrichtigungsinhalte bereitstellen.
title: "Auswählen einer Methode für die Übermittlung von Benachrichtigungen"
ms.assetid: FDB43EDE-C5F2-493F-952C-55401EC5172B
label: Choose a notification delivery method
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.openlocfilehash: ddbc04afd6571ac5692c2202fa292185d11e05b0
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
# <a name="choose-a-notification-delivery-method"></a><span data-ttu-id="45b14-104">Auswählen einer Methode für die Übermittlung von Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="45b14-104">Choose a notification delivery method</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css"> 


<span data-ttu-id="45b14-105">In diesem Artikel werden die vier Benachrichtigungsoptionen – lokal, geplant, periodisch und Push – behandelt, die Kachel- und Signalaktualisierungen sowie Popupbenachrichtigungsinhalte bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="45b14-105">This article covers the four notification options—local, scheduled, periodic, and push—that deliver tile and badge updates and toast notification content.</span></span> <span data-ttu-id="45b14-106">Eine Kachel oder eine Popupbenachrichtigung kann dem Benutzer Informationen anzeigen, auch wenn der Benutzer nicht direkt mit Ihrer App beschäftigt ist.</span><span class="sxs-lookup"><span data-stu-id="45b14-106">A tile or a toast notification can get information to your user even when the user is not directly engaged with your app.</span></span> <span data-ttu-id="45b14-107">Basierend auf der Art und dem Inhalt Ihrer App sowie den Informationen, die Sie bereitstellen möchten, können Sie die am besten geeignete Benachrichtigungsmethode bzw. -methoden für Ihr Szenario bestimmen.</span><span class="sxs-lookup"><span data-stu-id="45b14-107">The nature and content of your app and the information that you want to deliver can help you determine which notification method or methods is best for your scenario.</span></span>

## <a name="notification-delivery-methods-overview"></a><span data-ttu-id="45b14-108">Übersicht über Methoden für die Benachrichtigungsübermittlung</span><span class="sxs-lookup"><span data-stu-id="45b14-108">Notification delivery methods overview</span></span>


<span data-ttu-id="45b14-109">Es gibt vier Mechanismen, die von einer App zum Übermitteln einer Benachrichtigung verwendet werden können:</span><span class="sxs-lookup"><span data-stu-id="45b14-109">There are four mechanisms that an app can use to deliver a notification:</span></span>

-   **<span data-ttu-id="45b14-110">Lokal</span><span class="sxs-lookup"><span data-stu-id="45b14-110">Local</span></span>**
-   **<span data-ttu-id="45b14-111">Geplant</span><span class="sxs-lookup"><span data-stu-id="45b14-111">Scheduled</span></span>**
-   **<span data-ttu-id="45b14-112">Periodisch</span><span class="sxs-lookup"><span data-stu-id="45b14-112">Periodic</span></span>**
-   **<span data-ttu-id="45b14-113">Push</span><span class="sxs-lookup"><span data-stu-id="45b14-113">Push</span></span>**

<span data-ttu-id="45b14-114">In dieser Tabelle sind die Benachrichtigungsübermittlungstypen zusammengefasst.</span><span class="sxs-lookup"><span data-stu-id="45b14-114">This table summarizes the notification delivery types.</span></span>

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="45b14-115">Übermittlungsmethode</span><span class="sxs-lookup"><span data-stu-id="45b14-115">Delivery method</span></span></th>
<th align="left"><span data-ttu-id="45b14-116">Verwendungsart</span><span class="sxs-lookup"><span data-stu-id="45b14-116">Use with</span></span></th>
<th align="left"><span data-ttu-id="45b14-117">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="45b14-117">Description</span></span></th>
<th align="left"><span data-ttu-id="45b14-118">Beispiele</span><span class="sxs-lookup"><span data-stu-id="45b14-118">Examples</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="45b14-119">Lokal</span><span class="sxs-lookup"><span data-stu-id="45b14-119">Local</span></span></td>
<td align="left"><span data-ttu-id="45b14-120">Kachel, Signal, Popup</span><span class="sxs-lookup"><span data-stu-id="45b14-120">Tile, Badge, Toast</span></span></td>
<td align="left"><span data-ttu-id="45b14-121">Eine Reihe von API-Aufrufen, die Benachrichtigungen senden, während Ihre App ausgeführt wird, und die Kachel oder das Signal direkt aktualisieren oder eine Popupbenachrichtigung senden.</span><span class="sxs-lookup"><span data-stu-id="45b14-121">A set of API calls that send notifications while your app is running, directly updating the tile or badge, or sending a toast notification.</span></span></td>
<td align="left"><ul>
<li><span data-ttu-id="45b14-122">Eine Musik-App aktualisiert ihre Kachel so, dass &quot;Aktuelle Wiedergabe&quot; angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="45b14-122">A music app updates its tile to show what's &quot;Now Playing&quot;.</span></span></li>
<li><span data-ttu-id="45b14-123">Eine Spiele-App aktualisiert ihre Kachel mit der Bestwertung des Benutzers, wenn dieser das Spiel verlässt.</span><span class="sxs-lookup"><span data-stu-id="45b14-123">A game app updates its tile with the user's high score when the user leaves the game.</span></span></li>
<li><span data-ttu-id="45b14-124">Ein Signal, dessen Symbol anzeigt, dass neue Informationen in der App gelöscht werden, wenn die App aktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="45b14-124">A badge whose glyph indicates that there's new info int the app is cleared when the app is activated.</span></span></li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="45b14-125">Geplant</span><span class="sxs-lookup"><span data-stu-id="45b14-125">Scheduled</span></span></td>
<td align="left"><span data-ttu-id="45b14-126">Kachel, Popup</span><span class="sxs-lookup"><span data-stu-id="45b14-126">Tile, Toast</span></span></td>
<td align="left"><span data-ttu-id="45b14-127">Eine Reihe von API-Aufrufen, die eine Benachrichtigung im Voraus so planen, dass zum von Ihnen angegebenen Zeitpunkt eine Aktualisierung vorgenommen wird.</span><span class="sxs-lookup"><span data-stu-id="45b14-127">A set of API calls that schedule a notification in advance, to update at the time you specify.</span></span></td>
<td align="left"><ul>
<li><span data-ttu-id="45b14-128">Eine Kalender-App verwendet für eine anstehende Besprechung eine Erinnerung in Form einer Popupbenachrichtigung.</span><span class="sxs-lookup"><span data-stu-id="45b14-128">A calendar app sets a toast notification reminder for an upcoming meeting.</span></span></li>
</ul></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="45b14-129">Periodisch</span><span class="sxs-lookup"><span data-stu-id="45b14-129">Periodic</span></span></td>
<td align="left"><span data-ttu-id="45b14-130">Kachel, Signal</span><span class="sxs-lookup"><span data-stu-id="45b14-130">Tile, Badge</span></span></td>
<td align="left"><span data-ttu-id="45b14-131">Benachrichtigungen, mit denen Kacheln und Signale regelmäßig in einem festen Zeitintervall durch Abrufen von neuem Inhalt aus einem Clouddienst aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="45b14-131">Notifications that update tiles and badges regularly at a fixed time interval by polling a cloud service for new content.</span></span></td>
<td align="left"><ul>
<li><span data-ttu-id="45b14-132">Eine Wetter-App aktualisiert ihre Kachel, in der die Vorschau angezeigt wird, in Intervallen von 30 Minuten.</span><span class="sxs-lookup"><span data-stu-id="45b14-132">A weather app updates its tile, which shows the forecast, at 30-minute intervals.</span></span></li>
<li><span data-ttu-id="45b14-133">Eine Website für &quot;Tägliche Deals&quot; aktualisiert ihren Deal des Tages jeden Morgen.</span><span class="sxs-lookup"><span data-stu-id="45b14-133">A &quot;daily deals&quot; site updates its deal-of-the-day every morning.</span></span></li>
<li><span data-ttu-id="45b14-134">Eine Kachel, welche die Anzahl der Tage bis zu einem Ereignis anzeigt, aktualisiert den angezeigten Countdown jeden Tag um Mitternacht.</span><span class="sxs-lookup"><span data-stu-id="45b14-134">A tile that displays the days until an event updates the displayed countdown each day at midnight.</span></span></li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="45b14-135">Push</span><span class="sxs-lookup"><span data-stu-id="45b14-135">Push</span></span></td>
<td align="left"><span data-ttu-id="45b14-136">Kachel, Signal, Popup, Raw</span><span class="sxs-lookup"><span data-stu-id="45b14-136">Tile, Badge, Toast, Raw</span></span></td>
<td align="left"><span data-ttu-id="45b14-137">Von einem Cloudserver gesendete Benachrichtigungen, selbst wenn die App nicht ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="45b14-137">Notifications sent from a cloud server, even if your app isn't running.</span></span></td>
<td align="left"><ul>
<li><span data-ttu-id="45b14-138">Eine Shopping-App sendet eine Popupbenachrichtigung, um einen Benutzer über den Rabatt eines Artikels zu informieren, den er sich gerade ansieht.</span><span class="sxs-lookup"><span data-stu-id="45b14-138">A shopping app sends a toast notification to let a user know about a sale on an item that they're watching.</span></span></li>
<li><span data-ttu-id="45b14-139">Eine Nachrichten-App aktualisiert ihre Kachel mit Eilmeldungen, sobald sich die entsprechenden Geschehnisse ereignen.</span><span class="sxs-lookup"><span data-stu-id="45b14-139">A news app updates its tile with breaking news as it happens.</span></span></li>
<li><span data-ttu-id="45b14-140">Eine Sport-App hält ihre Kachel während eines laufenden Spiels auf dem neuesten Stand.</span><span class="sxs-lookup"><span data-stu-id="45b14-140">A sports app keeps its tile up-to-date during an ongoing game.</span></span></li>
<li><span data-ttu-id="45b14-141">Eine Kommunikations-App bietet Alarme zu eingehenden Nachrichten oder Telefonanrufen.</span><span class="sxs-lookup"><span data-stu-id="45b14-141">A communication app provides alerts about incoming messages or phone calls.</span></span></li>
</ul></td>
</tr>
</tbody>
</table>

 

## <a name="local-notifications"></a><span data-ttu-id="45b14-142">Lokale Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="45b14-142">Local notifications</span></span>


<span data-ttu-id="45b14-143">Das Aktualisieren der App-Kachel oder des Signals oder das Auslösen einer Popupbenachrichtigung, während die App ausgeführt wird, stellt den einfachsten der Mechanismen zur Benachrichtigungsübermittlung dar. Dafür werden nur lokale API-Aufrufe benötigt.</span><span class="sxs-lookup"><span data-stu-id="45b14-143">Updating the app tile or badge or raising a toast notification while the app is running is the simplest of the notification delivery mechanisms; it only requires local API calls.</span></span> <span data-ttu-id="45b14-144">Für jede App kann es hilfreiche oder interessante Informationen zum Anzeigen auf der Kachel geben – auch dann, wenn sich dieser Inhalt erst ändert, nachdem der Benutzer die App gestartet hat und mit ihr interagiert.</span><span class="sxs-lookup"><span data-stu-id="45b14-144">Every app can have useful or interesting information to show on the tile, even if that content only changes after the user launches and interacts with the app.</span></span> <span data-ttu-id="45b14-145">Lokale Benachrichtigungen sind auch eine gute Möglichkeit, die App-Kachel aktuell zu halten, selbst wenn Sie auch einen der anderen Benachrichtigungsmechanismen verwenden.</span><span class="sxs-lookup"><span data-stu-id="45b14-145">Local notifications are also a good way to keep the app tile current, even if you also use one of the other notification mechanisms.</span></span> <span data-ttu-id="45b14-146">Auf der Kachel einer Foto-App könnten z.B. Fotos aus einem kürzlich hinzugefügten Album angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="45b14-146">For instance, a photo app tile could show photos from a recently added album.</span></span>

<span data-ttu-id="45b14-147">Es empfiehlt sich, die Kachel beim ersten Start der App lokal zu aktualisieren (oder spätestens dann, wenn der Benutzer eine Änderung vornimmt, die üblicherweise auf der Kachel zu sehen ist).</span><span class="sxs-lookup"><span data-stu-id="45b14-147">We recommended that your app update its tile locally on first launch, or at least immediately after the user makes a change that your app would normally reflect on the tile.</span></span> <span data-ttu-id="45b14-148">Indem Sie diese Änderung schon während der Verwendung der App vornehmen, stellen Sie sicher, dass die Kachel bereits auf dem neuesten Stand ist, wenn der Benutzer die App beendet.</span><span class="sxs-lookup"><span data-stu-id="45b14-148">That update isn't seen until the user leaves the app, but by making that change while the app is being used ensures that the tile is already up-to-date when the user departs.</span></span>

<span data-ttu-id="45b14-149">Auch wenn die API-Aufrufe lokal erfolgen, können die Benachrichtigungen auf Webbilder verweisen.</span><span class="sxs-lookup"><span data-stu-id="45b14-149">While the API calls are local, the notifications can reference web images.</span></span> <span data-ttu-id="45b14-150">Wenn das Webbild nicht zum Download verfügbar oder beschädigt ist oder nicht den Bildspezifikationen entspricht, reagieren Kacheln und Popups unterschiedlich:</span><span class="sxs-lookup"><span data-stu-id="45b14-150">If the web image is not available for download, is corrupted, or doesn't meet the image specifications, tiles and toast respond differently:</span></span>

-   <span data-ttu-id="45b14-151">Kacheln: Die Aktualisierung wird nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="45b14-151">Tiles: The update is not shown</span></span>
-   <span data-ttu-id="45b14-152">Popup: Die Benachrichtigung wird angezeigt, das Bild wird jedoch gelöscht.</span><span class="sxs-lookup"><span data-stu-id="45b14-152">Toast: The notification is displayed, but your image is dropped</span></span>

<span data-ttu-id="45b14-153">Standardmäßig laufen lokale Popupbenachrichtigungen in drei Tagen und lokale Kachelbenachrichtigungen niemals ab.</span><span class="sxs-lookup"><span data-stu-id="45b14-153">By default, local toast notifications expire in three days, and local tile notifications never expire.</span></span> <span data-ttu-id="45b14-154">Es wird empfohlen, diese Standardeinstellungen mit einer expliziten Ablaufzeit zu überschreiben, die für Ihre Benachrichtigungen sinnvoll ist. (Die Ablaufzeit von Benachrichtigungen beträgt maximal drei Tage.)</span><span class="sxs-lookup"><span data-stu-id="45b14-154">We recommend overriding these defaults with an explicit expiration time that makes sense for your notifications (toasts have a max of three days).</span></span> 

<span data-ttu-id="45b14-155">Weitere Informationen finden Sie in folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="45b14-155">For more information, see these topics:</span></span>

-   [<span data-ttu-id="45b14-156">Senden einer lokalen Kachelbenachrichtigung</span><span class="sxs-lookup"><span data-stu-id="45b14-156">Send a local tile notification</span></span>](tiles-and-notifications-sending-a-local-tile-notification.md)
-   [<span data-ttu-id="45b14-157">Senden einer lokalen Popupbenachrichtigung</span><span class="sxs-lookup"><span data-stu-id="45b14-157">Send a local toast notification</span></span>](tiles-and-notifications-send-local-toast.md)
-   [<span data-ttu-id="45b14-158">Codebeispiele für Benachrichtigungen für die Universelle Windows-Plattform (UWP-Benachrichtigungen)</span><span class="sxs-lookup"><span data-stu-id="45b14-158">Universal Windows Platform (UWP) notifications code samples</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Notifications)

## <a name="scheduled-notifications"></a><span data-ttu-id="45b14-159">Geplante Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="45b14-159">Scheduled notifications</span></span>


<span data-ttu-id="45b14-160">Geplante Benachrichtigungen sind lokale Benachrichtigungen, die den genauen Zeitpunkt angeben können, zu dem eine Kachel aktualisiert oder eine Popupbenachrichtigung angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="45b14-160">Scheduled notifications are the subset of local notifications that can specify the precise time when a tile should be updated or a toast notification should be shown.</span></span> <span data-ttu-id="45b14-161">Geplante Benachrichtigungen eignen sich ideal für Situationen, in denen der zu aktualisierende Inhalt im Voraus bekannt ist (z.B. eine Besprechungseinladung).</span><span class="sxs-lookup"><span data-stu-id="45b14-161">Scheduled notifications are ideal in situations where the content to be updated is known in advance, such as a meeting invitation.</span></span> <span data-ttu-id="45b14-162">Wenn Sie den Benachrichtigungsinhalt vorher nicht kennen, müssen Sie eine Pushbenachrichtigung oder eine lokale Benachrichtigung verwenden.</span><span class="sxs-lookup"><span data-stu-id="45b14-162">If you don't have advance knowledge of the notification content, you should use a push or periodic notification.</span></span>

<span data-ttu-id="45b14-163">Beachten Sie, dass geplante Benachrichtigungen nicht für Signalbenachrichtigungen verwendet werden können. Signalbenachrichtigungen werden am besten mithilfe lokaler, regelmäßiger oder Pushbenachrichtigungen bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="45b14-163">Note that scheduled notifications cannot be used for badge notifications; badge notifications are best served by local, periodic, or push notifications.</span></span>

<span data-ttu-id="45b14-164">Geplante Benachrichtigungen laufen standardmäßig drei Tage nach Zustellung ab.</span><span class="sxs-lookup"><span data-stu-id="45b14-164">By default, scheduled notifications expire three days from the time they are delivered.</span></span> <span data-ttu-id="45b14-165">Sie können diese Standardeinstellung für die Ablaufzeit für geplante Kachelbenachrichtigungen überschreiben, jedoch nicht die Ablaufzeit für geplante Popups.</span><span class="sxs-lookup"><span data-stu-id="45b14-165">You can override this default expiration time on scheduled tile notifications, but you cannot override the expiration time on scheduled toasts.</span></span>

<span data-ttu-id="45b14-166">Weitere Informationen finden Sie in folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="45b14-166">For more information, see these topics:</span></span>

-   [<span data-ttu-id="45b14-167">Codebeispiele für Benachrichtigungen für die Universelle Windows-Plattform (UWP-Benachrichtigungen)</span><span class="sxs-lookup"><span data-stu-id="45b14-167">Universal Windows Platform (UWP) notifications code samples</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Notifications)

## <a name="periodic-notifications"></a><span data-ttu-id="45b14-168">Periodische Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="45b14-168">Periodic notifications</span></span>


<span data-ttu-id="45b14-169">Periodische Benachrichtigungen bieten Ihnen Livekachelaktualisierungen mit minimaler Investition in Clouddienst und Client.</span><span class="sxs-lookup"><span data-stu-id="45b14-169">Periodic notifications give you live tile updates with a minimal cloud service and client investment.</span></span> <span data-ttu-id="45b14-170">Sie stellen auch eine exzellente Methode zum Verteilen desselben Inhalts an eine große Zielgruppe dar.</span><span class="sxs-lookup"><span data-stu-id="45b14-170">They are also an excellent method of distributing the same content to a wide audience.</span></span> <span data-ttu-id="45b14-171">Ihr Clientcode gibt die URL eines Cloudspeicherorts an, von dem Windows Kachel- und Signalaktualisierungen abruft, und die Häufigkeit, mit der der Speicherort abgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="45b14-171">Your client code specifies the URL of a cloud location that Windows polls for tile or badge updates, and how often the location should be polled.</span></span> <span data-ttu-id="45b14-172">In jedem Abrufintervall wird die URL von Windows aufgerufen, um den angegebene XML-Inhalt herunterzuladen und auf der Kachel anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="45b14-172">At each polling interval, Windows contacts the URL to download the specified XML content and display it on the tile.</span></span>

<span data-ttu-id="45b14-173">Für periodische Benachrichtigungen muss die App einen Clouddienst hosten, und dieser Dienst wird im angegebenen Intervall von allen Benutzern abgerufen, die die App installiert haben.</span><span class="sxs-lookup"><span data-stu-id="45b14-173">Periodic notifications require the app to host a cloud service, and this service will be polled at the specified interval by all users who have the app installed.</span></span> <span data-ttu-id="45b14-174">Beachten Sie, dass periodische Aktualisierungen nicht für Popupbenachrichtigungen verwendet werden können. Popupbenachrichtigungen werden am besten mithilfe von geplanten Benachrichtigungen oder Pushbenachrichtigungen bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="45b14-174">Note that periodic updates cannot be used for toast notifications; toast notifications are best served by scheduled or push notifications.</span></span>

<span data-ttu-id="45b14-175">Regelmäßige Benachrichtigungen laufen standardmäßig drei Tage nach der Abfrage ab.</span><span class="sxs-lookup"><span data-stu-id="45b14-175">By default, periodic notifications expire three days from the time polling occurs.</span></span> <span data-ttu-id="45b14-176">Diese Standardeinstellung kann bei Bedarf mit einer anderen Ablaufzeit explizit überschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="45b14-176">If needed, you can override this default with an explicit expiration time.</span></span>

<span data-ttu-id="45b14-177">Weitere Informationen finden Sie unter folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="45b14-177">For more information, see these topics:</span></span>

-   [<span data-ttu-id="45b14-178">Übersicht über regelmäßige Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="45b14-178">Periodic notification overview</span></span>](tiles-and-notifications-periodic-notification-overview.md)
-   [<span data-ttu-id="45b14-179">Codebeispiele für UWP (universelle Windows-Plattform)-Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="45b14-179">Universal Windows Platform (UWP) notifications code samples</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Notifications)

## <a name="push-notifications"></a><span data-ttu-id="45b14-180">Pushbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="45b14-180">Push notifications</span></span>


<span data-ttu-id="45b14-181">Pushbenachrichtigungen eignen sich ideal zum Kommunizieren von Echtzeitdaten oder für den Benutzer personalisierten Daten.</span><span class="sxs-lookup"><span data-stu-id="45b14-181">Push notifications are ideal to communicate real-time data or data that is personalized for your user.</span></span> <span data-ttu-id="45b14-182">Pushbenachrichtigungen werden auch für Inhalte verwendet, die zu unvorhersehbaren Zeiten generiert werden (z.B. Eilmeldungen oder Chatnachrichten).</span><span class="sxs-lookup"><span data-stu-id="45b14-182">Push notifications are used for content that is generated at unpredictable times, such as breaking news, social network updates, or instant messages.</span></span> <span data-ttu-id="45b14-183">Pushbenachrichtigungen sind auch in Situationen hilfreich, in denen Daten so zeitempfindlich sind, dass periodische Benachrichtigungen nicht geeignet wären (z.B. Spielstände während eines Spiels).</span><span class="sxs-lookup"><span data-stu-id="45b14-183">Push notifications are also useful in situations where the data is time-sensitive in a way that would not suit periodic notifications, such as sports scores during a game.</span></span>

<span data-ttu-id="45b14-184">Für Pushbenachrichtigungen ist ein Cloud-Dienst erforderlich, der Pushbenachrichtigungskanäle verwaltet und festlegt, wann und an wen Benachrichtigungen gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="45b14-184">Push notifications require a cloud service that manages push notification channels and chooses when and to whom to send notifications.</span></span>

<span data-ttu-id="45b14-185">Pushbenachrichtigungen laufen standardmäßig drei Tage nach Empfang durch das Gerät ab.</span><span class="sxs-lookup"><span data-stu-id="45b14-185">By default, push notifications expire three days from the time they are received by the device.</span></span> <span data-ttu-id="45b14-186">Diese Standardeinstellung kann bei Bedarf mit einer expliziten Ablaufzeit überschrieben werden. (Für Popups gilt eine maximale Ablaufzeit von drei Tagen.)</span><span class="sxs-lookup"><span data-stu-id="45b14-186">If needed, you can override this default with an explicit expiration time (toasts have a max of three days).</span></span>

<span data-ttu-id="45b14-187">Weitere Informationen finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="45b14-187">For more information, see:</span></span>

-   [<span data-ttu-id="45b14-188">Übersicht über Windows-Pushbenachrichtigungsdienste (Windows Push Notification Services, WNS)</span><span class="sxs-lookup"><span data-stu-id="45b14-188">Windows Push Notification Services (WNS) overview</span></span>](tiles-and-notifications-windows-push-notification-services--wns--overview.md)
-   [<span data-ttu-id="45b14-189">Richtlinien für Pushbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="45b14-189">Guidelines for push notifications</span></span>](https://msdn.microsoft.com/library/windows/apps/hh761462)
-   [<span data-ttu-id="45b14-190">Codebeispiele für Benachrichtigungen für die Universelle Windows-Plattform (UWP-Benachrichtigungen)</span><span class="sxs-lookup"><span data-stu-id="45b14-190">Universal Windows Platform (UWP) notifications code samples</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Notifications)


## <a name="related-topics"></a><span data-ttu-id="45b14-191">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="45b14-191">Related topics</span></span>


* [<span data-ttu-id="45b14-192">Senden einer lokalen Kachelbenachrichtigung</span><span class="sxs-lookup"><span data-stu-id="45b14-192">Send a local tile notification</span></span>](tiles-and-notifications-sending-a-local-tile-notification.md)
* [<span data-ttu-id="45b14-193">Senden einer lokalen Popupbenachrichtigung</span><span class="sxs-lookup"><span data-stu-id="45b14-193">Send a local toast notification</span></span>](tiles-and-notifications-send-local-toast.md)
* [<span data-ttu-id="45b14-194">Richtlinien für Pushbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="45b14-194">Guidelines for push notifications</span></span>](https://msdn.microsoft.com/library/windows/apps/hh761462)
* [<span data-ttu-id="45b14-195">Richtlinien für Popupbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="45b14-195">Guidelines for toast notifications</span></span>](https://msdn.microsoft.com/library/windows/apps/hh465391)
* [<span data-ttu-id="45b14-196">Übersicht über regelmäßige Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="45b14-196">Periodic notification overview</span></span>](tiles-and-notifications-periodic-notification-overview.md)
* [<span data-ttu-id="45b14-197">Übersicht über die Windows-Pushbenachrichtigungsdienste (Windows Push Notification Services, WNS)</span><span class="sxs-lookup"><span data-stu-id="45b14-197">Windows Push Notification Services (WNS) overview</span></span>](tiles-and-notifications-windows-push-notification-services--wns--overview.md)
* [<span data-ttu-id="45b14-198">Codebeispiele für UWP (universelle Windows-Plattform)-Benachrichtigungen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="45b14-198">Universal Windows Platform (UWP) notifications code samples on GitHub</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Notifications)
 

 




