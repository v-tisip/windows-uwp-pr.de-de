---
author: jnHs
Description: The Xbox analytics report in the Windows Dev Center dashboard shows you statistics about how your customers are engaging with the Xbox features in your product.
title: Bericht der Xbox Analyse
ms.author: wdg-dev-content
ms.date: 06/04/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Xbox Analyse, Xbox Live-Analyse, Xbox-Statistiken
ms.localizationpriority: medium
ms.openlocfilehash: 9e69c41ec2ae6dface93b9f3148e699e448faa18
ms.sourcegitcommit: 753dfcd0f9fdfc963579dd0b217b445c4b110a18
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "2857041"
---
# <a name="xbox-analytics-report"></a><span data-ttu-id="20d64-103">Xbox Analysebericht</span><span class="sxs-lookup"><span data-stu-id="20d64-103">Xbox analytics report</span></span>

<span data-ttu-id="20d64-104">Der **Xbox Analysebericht** im Windows Dev Center-Dashboard zeigt Ihnen Statistiken darüber an, wie Ihre Kunden die Xbox-Features in Ihrem Spiel nutzen.</span><span class="sxs-lookup"><span data-stu-id="20d64-104">The **Xbox analytics** report in the Windows Dev Center dashboard shows you statistics about how your customers are engaging with the Xbox features in your game.</span></span> <span data-ttu-id="20d64-105">Es enthält auch Informationen zur Dienstintegrität, um Clientfehler zu beheben.</span><span class="sxs-lookup"><span data-stu-id="20d64-105">It also provides service health info to help you address client errors.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="20d64-106">Dieser Bericht wird nur angezeigt, wenn Sie ein Spiel für Xbox oder ein Spiel veröffentlichen, das Xbox Live-Dienste verwendet.</span><span class="sxs-lookup"><span data-stu-id="20d64-106">You’ll only see this report if you’re publishing a game for Xbox or a game that uses Xbox Live services.</span></span> <span data-ttu-id="20d64-107">Dazu müssen Sie durch den [Genehmigungsprozess Konzept](../gaming/concept-approval.md)Spiele von [Microsoft-Partnern](../xbox-live/developer-program-overview.md#microsoft-partners) spielen per und gehen die [ ID@Xbox Programm](../xbox-live/developer-program-overview.md#id).</span><span class="sxs-lookup"><span data-stu-id="20d64-107">To do so, you must go through the [concept approval process](../gaming/concept-approval.md), which includes games published by [Microsoft partners](../xbox-live/developer-program-overview.md#microsoft-partners) and games submitted via the [ID@Xbox program](../xbox-live/developer-program-overview.md#id).</span></span> <span data-ttu-id="20d64-108">Spiele über [Xbox Live Ersteller Programm](../xbox-live/get-started-with-creators/get-started-with-xbox-live-creators.md) sind nicht in diesem Bericht angezeigten.</span><span class="sxs-lookup"><span data-stu-id="20d64-108">Games published via the [Xbox Live Creators Program](../xbox-live/get-started-with-creators/get-started-with-xbox-live-creators.md) are not currently visible in this report.</span></span>

<span data-ttu-id="20d64-109">Zeigen Sie den **Xbox Analyse**-Bericht im linken Navigationsmenü für Ihr Spiel an, indem Sie **Analyse** erweitern und **Xbox Analyse** auswählen.</span><span class="sxs-lookup"><span data-stu-id="20d64-109">You can view the **Xbox analytics** report from the left navigation menu for your game by expanding **Analytics** and selecting **Xbox analytics**.</span></span>  <span data-ttu-id="20d64-110">Sie können diese Daten in Ihrem Dashboard anzeigen oder den [Bericht herunterladen](download-analytic-reports.md), um ihn offline anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="20d64-110">You can view this data in your dashboard, or [download the report](download-analytic-reports.md) to view offline.</span></span>


## <a name="overview-tab"></a><span data-ttu-id="20d64-111">Registerkarte Übersicht</span><span class="sxs-lookup"><span data-stu-id="20d64-111">Overview tab</span></span>

<span data-ttu-id="20d64-112">Die Abschnitte der Registerkarte **Übersicht** zeigen Informationen über die Spieler und deren Interaktion mit Xbox Live-Features an.</span><span class="sxs-lookup"><span data-stu-id="20d64-112">The sections on the **Overview** tab shows info about who your players are and how they're engaging with Xbox Live features.</span></span>

<span data-ttu-id="20d64-113">Für viele dieser Statistiken zeigen wir auch den **Xbox Durchschnitt** an, damit Sie leicht erkennen können, wie Ihre Kunden im Vergleich zu den durchschnittlichen Xbox-Kunden mit Xbox interagieren.</span><span class="sxs-lookup"><span data-stu-id="20d64-113">For many of these statistics, we also show the **Xbox average** so you can easily see how your customers interact with Xbox compared to the average Xbox customer.</span></span>

> [!NOTE]
> <span data-ttu-id="20d64-114">Diese Statistiken enthalten Kunden, die mit Xbox Live verbunden sind und nicht alle Xbox-Kunden.</span><span class="sxs-lookup"><span data-stu-id="20d64-114">These statistics are from customers who are connected to Xbox Live, not all Xbox customers.</span></span>


### <a name="concurrent-usage"></a><span data-ttu-id="20d64-115">Gleichzeitige Nutzung</span><span class="sxs-lookup"><span data-stu-id="20d64-115">Concurrent usage</span></span>

<span data-ttu-id="20d64-116">In diesem Abschnitt zeigt die Nutzungsdaten nahezu in Echtzeit an (5-15 Minuten Latenz) gegenüber der Anzahl Kunden, die Ihr Spiel stündlich oder pro Minute spielen.</span><span class="sxs-lookup"><span data-stu-id="20d64-116">This section shows near real time usage data (with 5-15 minutes latency) about the average number of customers playing your game each minute or hour.</span></span> <span data-ttu-id="20d64-117">Sie können den Zeitraum auswählen (von **Letzte Stunde** bis **Letzten 7 Tage**), indem Sie das Filtersymbol in der oberen rechten Ecke in diesem Abschnitt auswählen.</span><span class="sxs-lookup"><span data-stu-id="20d64-117">You can choose the time range (from **Last hour** up to **Last 7 days**) by selecting the filter icon in the top right corner of this section.</span></span>


### <a name="gamerscore-distribution"></a><span data-ttu-id="20d64-118">Gamerscore-Verteilung</span><span class="sxs-lookup"><span data-stu-id="20d64-118">Gamerscore distribution</span></span>

<span data-ttu-id="20d64-119">In diesem Abschnitt finden Sie Informationen zum Gamerscore Ihrer Kunden.</span><span class="sxs-lookup"><span data-stu-id="20d64-119">This section shows info about the gamerscore of your customers.</span></span> <span data-ttu-id="20d64-120">Sie können **alle Spiele** auswählen, um die Verteilung aller Gamerscores Ihren Kunden anzuzeigen oder **dieses Spiel** auswählen, um die Verteilung von Gamerscores anzuzeigen, die nur durch Ihr Spiel erhalten wurden.</span><span class="sxs-lookup"><span data-stu-id="20d64-120">You can select **All games** to see the distribution of total gamerscore across your customers, or select **This game** to view the distribution of gamerscore obtained through your game only.</span></span>


### <a name="achievement-unlocks"></a><span data-ttu-id="20d64-121">Freigeschaltete Erfolge</span><span class="sxs-lookup"><span data-stu-id="20d64-121">Achievement unlocks</span></span>

<span data-ttu-id="20d64-122">In diesem Abschnitt wird die Gesamtanzahl der Kunden angezeigt, die im angegebenen Zeitraum den Erfolg freigeschaltet haben.</span><span class="sxs-lookup"><span data-stu-id="20d64-122">This section shows the total number of customers who have unlocked each achievement in the specified time range.</span></span> <span data-ttu-id="20d64-123">Sie können den Zeitraum auswählen (**Letzter Tag**, **Letzen 30 Tage** oder **Lebensdauer**), indem Sie das Filtersymbol in der oberen rechten Ecke in diesem Abschnitt auswählen.</span><span class="sxs-lookup"><span data-stu-id="20d64-123">You can choose the time range (**Last day**, **Last 30 days**, or **Lifetime**) by selecting the filter icon in the top right corner of this section.</span></span>


### <a name="game-statistics"></a><span data-ttu-id="20d64-124">Spielstatistiken</span><span class="sxs-lookup"><span data-stu-id="20d64-124">Game statistics</span></span>

<span data-ttu-id="20d64-125">Dieser Abschnitt enthält Registerkarten, die Sie auswählen können, um unterschiedliche Daten über die Kunden Ihres Spiels anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="20d64-125">This section includes tabs that you can select to show different data for your game's customers.</span></span> <span data-ttu-id="20d64-126">Beachten Sie, dass die Statistiken in diesem Abschnitt auf die allgemeine Featureverwendung hinweisen und nicht auf Ihr bestimmtes Produkt.</span><span class="sxs-lookup"><span data-stu-id="20d64-126">Note that the statistics in this section refer to feature usage in general and not within your specific product.</span></span>

- <span data-ttu-id="20d64-127">Die Registerkarte **Social Usage** zeigt Daten im Zusammenhang über die sozialen Interaktionen Ihrer Kunden an.</span><span class="sxs-lookup"><span data-stu-id="20d64-127">The **Social usage** tab shows data related to how your customers interact socially.</span></span>
   - <span data-ttu-id="20d64-128">**Spieleinladungen** zeigt den Prozentsatz Ihrer Kunden an, denen Sie Einladungen (für ein Spiel) gesendet haben.</span><span class="sxs-lookup"><span data-stu-id="20d64-128">**Game invites** shows the percentage of your customers who have sent out invites (for any game).</span></span>
   - <span data-ttu-id="20d64-129">**Party-Chat** zeigt den Prozentsatz Ihrer Kunden an, die Party-Chat verwenden (für alle Spiele).</span><span class="sxs-lookup"><span data-stu-id="20d64-129">**Party chat** shows the percentage of your customers who use party chat (for any game).</span></span>
   - <span data-ttu-id="20d64-130">**SMS** zeigt den Prozentsatz Ihrer Kunden an, die Nachrichten über die Xbox-Shell senden (für ein Spiel).</span><span class="sxs-lookup"><span data-stu-id="20d64-130">**Text messages** shows the percentage of your customers who send messages through the Xbox shell (for any game).</span></span>
- <span data-ttu-id="20d64-131">Die Registerkarte **Streaming Usage** zeigt die Prozentsätze der Kunden Ihrer Spiele an, die Spiele auf Twitch und YouTube ansehen oder streamen (für alle Spiele).</span><span class="sxs-lookup"><span data-stu-id="20d64-131">The **Streaming usage** tab shows the percentages of your game's customers who watch or stream gameplay (for any game) on Twitch and YouTube.</span></span>
- <span data-ttu-id="20d64-132">Die Registerkarte **Game DVR usage** zeigt Daten darüber an, wie Ihre Kunden Spiele aufzeichnen und anzeigen.</span><span class="sxs-lookup"><span data-stu-id="20d64-132">The **Game DVR usage** tab shows data related to how your customers record and view gameplay.</span></span> <span data-ttu-id="20d64-133">Sie können die Prozentsätze der Kunden sehen, die Spielclips und Bildschirmfotos des Spiels angezeigt und hochgeladen haben (für alle Spiele).</span><span class="sxs-lookup"><span data-stu-id="20d64-133">You can see the percentages of customers who have viewed and uploaded game clips and screenshots of gameplay (for any game).</span></span>


### <a name="friends-and-followers"></a><span data-ttu-id="20d64-134">Freunde und Follower</span><span class="sxs-lookup"><span data-stu-id="20d64-134">Friends and followers</span></span>

<span data-ttu-id="20d64-135">In diesem Abschnitt wird die **durchschnittliche Anzahl der Freunde** und **die durchschnittliche Anzahl der Follower** für Kunden angezeigt, die Ihr Spiel spielen.</span><span class="sxs-lookup"><span data-stu-id="20d64-135">This section shows the **Median number of friends** and **Median number of followers** for the customers playing your game.</span></span>


### <a name="accessory-usage"></a><span data-ttu-id="20d64-136">Nutzung des Zubehörs</span><span class="sxs-lookup"><span data-stu-id="20d64-136">Accessory usage</span></span>

<span data-ttu-id="20d64-137">Dieses Diagramm zeigt die Prozentsätze der Kunden Ihres Spiels an, die externe Festplatten und Xbox Elite Wireless Controller verwenden (auf der Xbox).</span><span class="sxs-lookup"><span data-stu-id="20d64-137">This chart shows the percentages of your game's customers who use external hard drives and who use Xbox Elite Wireless Controllers (on Xbox).</span></span>

<span data-ttu-id="20d64-138">Diese Daten bedeutet nicht, das diese Kunden Ihr Produkt auf externen Festplatten installiert haben oder Elite-Controller während der Wiedergabe verwenden.</span><span class="sxs-lookup"><span data-stu-id="20d64-138">This data does not mean that these customers who installed your product on external hard drives or used an Elite Controller while playing it.</span></span> <span data-ttu-id="20d64-139">Er bezieht sich darauf, wie viele Kunden Ihres Produkts diese Features in der Regel verwenden.</span><span class="sxs-lookup"><span data-stu-id="20d64-139">It refers to how many of your product's customers use these features in general.</span></span>


### <a name="connection-type"></a><span data-ttu-id="20d64-140">Verbindungstyp</span><span class="sxs-lookup"><span data-stu-id="20d64-140">Connection type</span></span>

<span data-ttu-id="20d64-141">Dieses Diagramm zeigt die Prozentsätze für die Benutzer Ihres Produkts an, die **verkabelte** Internetverbindungen im Vergleich zu **WLAN** nutzen (auf der Xbox).</span><span class="sxs-lookup"><span data-stu-id="20d64-141">This chart shows the percentages of your product’s customers who use **Wired** internet connections versus **Wireless** (on Xbox).</span></span>


## <a name="xbox-live-service-health-tab"></a><span data-ttu-id="20d64-142">Xbox Live Registerkarte „Dienstintegrität”</span><span class="sxs-lookup"><span data-stu-id="20d64-142">Xbox Live service health tab</span></span>

<span data-ttu-id="20d64-143">In den Abschnitten auf der **Xbox Live Registerkarte „Dienstintegrität”** können Sie die Auswirkung der Xbox Live Clientfehler sehen, einschließlich der Begrenzung der Übertragungsrate.</span><span class="sxs-lookup"><span data-stu-id="20d64-143">The sections on the **Xbox Live service health tab** help you understand the impact of any Xbox Live client errors, including rate limiting.</span></span> <span data-ttu-id="20d64-144">Außerdem können Sie einen Drilldown nach Endpunkt und Statuscode durchführen, um Informationen abzurufen, die bei der Behebung der Probleme helfen. Sie können dort ebenfalls die Verfügbarkeit von Xbox Live-Diensten für die Aufrufe Ihres Produkts einsehen.</span><span class="sxs-lookup"><span data-stu-id="20d64-144">It also lets you drill down by endpoint and status code to get info that helps you resolve these issues, and keeps you informed about Xbox Live service availability specific to your product’s calls.</span></span>

> [!NOTE]
> <span data-ttu-id="20d64-145">Wenn Sie diese Informationen einsehen und Probleme behandeln, empfehlen wir ein Priorisieren der Begrenzung der Übertragungsrate, da diese Fehler in der Regel die größte Auswirkung auf Ihre Kunden haben.</span><span class="sxs-lookup"><span data-stu-id="20d64-145">When reviewing this info and addressing issues, we recommend prioritizing rate limiting, as those errors usually have the greatest customer impact.</span></span>


### <a name="apply-filters"></a><span data-ttu-id="20d64-146">Anwenden von Filtern</span><span class="sxs-lookup"><span data-stu-id="20d64-146">Apply filters</span></span>

<span data-ttu-id="20d64-147">Im oberen Bereich der Registerkarte können Sie den Zeitraum auswählen, für den die Daten angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="20d64-147">Near the top of the tab, you can select the time period for which you want to show data.</span></span> <span data-ttu-id="20d64-148">Die Standardeinstellung ist **30D** (30Tage), aber Sie können Daten für **7D** (7Tage) oder einen benutzerdefinierten Datumsbereich auswählen, den Sie festlegen (nicht mehr als 30Tage).</span><span class="sxs-lookup"><span data-stu-id="20d64-148">The default selection is **30D** (30 days), but you can choose to show data for **7D** (7 days) or a custom date range that you specify (of no more than 30 days).</span></span> <span data-ttu-id="20d64-149">Beachten Sie für einen benutzerdefinierten Datumsbereich, dass alle Diagramme den Diagrammbereich auf den ersten und letzten Tag der Daten innerhalb des Bereichs kürzen, den Sie eingegeben haben.</span><span class="sxs-lookup"><span data-stu-id="20d64-149">For a custom date range, note that all of the charts will trim the chart range to the first and last day of data provided within the date range you enter.</span></span>

<span data-ttu-id="20d64-150">Sie können ebenfalls **Filter** erweitern, um alle Daten auf dieser Seite nach Paketversion, Gerätetyp und/oder Sandbox zu filtern.</span><span class="sxs-lookup"><span data-stu-id="20d64-150">You can also expand **Filters** to filter all of the data on this page by package version, device type, and/or sandbox.</span></span>
- <span data-ttu-id="20d64-151">**Paketversion**: Der Standardfilter ist **Alle Versionen**, aber Sie können die Dienstintegritätsdaten auf eine bestimmte Paketversion beschränken.</span><span class="sxs-lookup"><span data-stu-id="20d64-151">**Package version**: The default filter is **All versions**, but you can limit the service health data to a specific package version.</span></span>
- <span data-ttu-id="20d64-152">**Gerätetyp**: Die Standardeinstellung ist **Alle Gerät**, Sie können jedoch die Dienstintegritätsdaten auf einen bestimmten Gerätetyp beschränken.</span><span class="sxs-lookup"><span data-stu-id="20d64-152">**Device type**: The default setting is **All devices**, but you can limit the service health data to a specific device type.</span></span>
- <span data-ttu-id="20d64-153">**Sandbox**: Die Standardeinstellung ist **RETAIL**, Sie können jedoch die Dienstintegritätsdaten auf eine bestimmte Sandbox beschränken.</span><span class="sxs-lookup"><span data-stu-id="20d64-153">**Sandbox**: The default setting is **RETAIL**, but you can limit the service health data to a specific sandbox.</span></span>

<span data-ttu-id="20d64-154">Die Informationen in allen unten angezeigten Diagrammen beziehen sich auf den ausgewählten Zeitraum und alle von Ihnen ausgewählten Filter.</span><span class="sxs-lookup"><span data-stu-id="20d64-154">The info in all of the charts listed below will reflect the date range and any filters you've selected.</span></span> <span data-ttu-id="20d64-155">In einigen Abschnitten können Sie zusätzliche Filter anwenden.</span><span class="sxs-lookup"><span data-stu-id="20d64-155">Some sections also allow you to apply additional filters.</span></span>


### <a name="client-errors-by-service"></a><span data-ttu-id="20d64-156">Clientfehler pro Dienst</span><span class="sxs-lookup"><span data-stu-id="20d64-156">Client errors by service</span></span>

<span data-ttu-id="20d64-157">Das Diagramm **Clientfehler pro Dienst** zeigt die Anzahl der täglichen Clientfehler (4xx) auf jedem Xbox Live-Dienst über einen ausgewählten Zeitraum an.</span><span class="sxs-lookup"><span data-stu-id="20d64-157">The **Client errors by service** chart shows the number of daily client (4xx) errors across each Xbox Live service over the selected period of time.</span></span>

<span data-ttu-id="20d64-158">Sie können auch nur Ratenbegrenzungsfehler anzeigen, indem Sie **Begrenzung der Übertragungsrate** auswählen.</span><span class="sxs-lookup"><span data-stu-id="20d64-158">You can also view only rate limiting errors by selecting **Rate limiting**.</span></span> <span data-ttu-id="20d64-159">Zeigt die täglichen Fehler bei der Begrenzung der Übertragungsrate (429) und der Ratenbegrenzungsausnahmen (429E) bei Xbox Live-Diensten über den ausgewählten Zeitraum an.</span><span class="sxs-lookup"><span data-stu-id="20d64-159">This shows the number of daily rate limiting (429) and rate limiting exempt (429E) errors across each Xbox Live service over the selected period of time.</span></span>

> [!NOTE]
> <span data-ttu-id="20d64-160">Ein Statuscode 429E wurde tatsächlich erfolgreich als Statuscode 200 zurückgegeben, wäre jedoch in der Rate begrenzt, wenn der Dienst ein hohes Volumen zu dem Zeitpunkt hatte, daher wird empfohlen, dass Sie es den Fehler genauso behandeln, als ob er erzwungen (429) wurde.</span><span class="sxs-lookup"><span data-stu-id="20d64-160">A 429E status code was actually successfully returned as a 200 status code, but would have been rate-limited if the service was experiencing high volume at the time, so we recommend you treat it exactly the same as if it were enforced (429).</span></span>

<span data-ttu-id="20d64-161">Dieses Diagramm zeigt standardmäßig die sechs Top-Dienste nach Fehleranzahl an.</span><span class="sxs-lookup"><span data-stu-id="20d64-161">By default, this chart displays the top six services by error count.</span></span> <span data-ttu-id="20d64-162">Sie können das Filtersymbol in der oberen rechten Ecke dieses Abschnitts auswählen, um unterschiedliche Dienste auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="20d64-162">You can select the filter icon in the top right corner of this section to choose different services.</span></span> <span data-ttu-id="20d64-163">Sie können Fehler für maximal sechs Dienste auf einmal anzeigen.</span><span class="sxs-lookup"><span data-stu-id="20d64-163">You can view errors for up to six services at once.</span></span>

> [!NOTE]
> <span data-ttu-id="20d64-164">Die Legende zeigt nur die unterschiedlichen Präfixe für die einzelnen Dienste an (z.B. **presence** anstelle von **presence.xboxlive.com**).</span><span class="sxs-lookup"><span data-stu-id="20d64-164">The legend only displays the distinguishing prefix for each service (for example, **presence** instead of **presence.xboxlive.com**).</span></span> <span data-ttu-id="20d64-165">Sie finden die vollständige Service-Adresse in der Tabelle **Clientfehler nach Endpunkt** weiter unten in der Registerkarte **Xbox Live-Dienstintegrität** .</span><span class="sxs-lookup"><span data-stu-id="20d64-165">You can find the full service address in the **Client errors by endpoint** table lower in the **Xbox Live service health** tab.</span></span>


### <a name="service-availability"></a><span data-ttu-id="20d64-166">Dienstverfügbarkeit</span><span class="sxs-lookup"><span data-stu-id="20d64-166">Service availability</span></span>

<span data-ttu-id="20d64-167">Das Diagramm **Dienstverfügbarkeit** zeigt die tägliche Verfügbarkeit aller Xbox Live-Dienste über den ausgewählten Zeitraum an.</span><span class="sxs-lookup"><span data-stu-id="20d64-167">The **Service availability** chart shows the daily availability across each Xbox Live service over the selected period of time.</span></span> <span data-ttu-id="20d64-168">Dies wird als *1-(Serverfehler insgesamt (5xx) /Antworten insgesamt)* berechnet. Dies ist produktspezifisch und nicht Xbox Live-spezifisch.</span><span class="sxs-lookup"><span data-stu-id="20d64-168">This is calculated as *1-(total server (5xx) errors/total responses)*, and is specific to your product, not Xbox Live as a whole.</span></span>

<span data-ttu-id="20d64-169">Dieses Diagramm zeigt standardmäßig die sechs Dienste mit der niedrigsten Verfügbarkeit an.</span><span class="sxs-lookup"><span data-stu-id="20d64-169">By default, this chart displays the six services which have experienced the lowest availability.</span></span> <span data-ttu-id="20d64-170">Sie können das Filtersymbol in der oberen rechten Ecke dieses Abschnitts auswählen, um unterschiedliche Dienste auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="20d64-170">You can select the filter icon in the top right corner of this section to choose different services.</span></span> <span data-ttu-id="20d64-171">Sie können die Verfügbarkeit für maximal sechs Dienste auf einmal anzeigen.</span><span class="sxs-lookup"><span data-stu-id="20d64-171">You can view availability for up to six services at once.</span></span>

> [!NOTE]
> <span data-ttu-id="20d64-172">Die Legende zeigt nur die unterschiedlichen Präfixe für die einzelnen Dienste an (z.B. **presence** anstelle von **presence.xboxlive.com**).</span><span class="sxs-lookup"><span data-stu-id="20d64-172">The legend only displays the distinguishing prefix for each service (for example, **presence** instead of **presence.xboxlive.com**).</span></span> <span data-ttu-id="20d64-173">Sie finden die vollständige Service-Adresse in der Tabelle **Clientfehler nach Endpunkt** weiter unten in der Registerkarte **Xbox Live-Dienstintegrität** .</span><span class="sxs-lookup"><span data-stu-id="20d64-173">You can find the full service address in the **Client errors by endpoint** table lower in the **Xbox Live service health** tab.</span></span>


### <a name="client-errors-by-endpoint"></a><span data-ttu-id="20d64-174">Clientfehler nach Endpunkt</span><span class="sxs-lookup"><span data-stu-id="20d64-174">Client errors by endpoint</span></span>

<span data-ttu-id="20d64-175">Die Tabelle **Clientfehler nach Endpunkt** zeigt die Anzahl der täglichen Clientfehler (4xx) pro Xbox Live-Dienst, Endpunkt und Statuscode über einen ausgewählten Zeitraum an.</span><span class="sxs-lookup"><span data-stu-id="20d64-175">The **Client errors by endpoint** table shows the number of daily client (4xx) errors broken down by each Xbox Live service, endpoint, and status code over the selected period of time.</span></span> <span data-ttu-id="20d64-176">Standardmäßig wird diese Tabelle nach der Gesamtzahl der Service-Antworten in absteigender Reihenfolge sortiert, Sie können die Sortierreihenfolge allerdings ändern, indem Sie auf die Spaltenüberschriften klicken.</span><span class="sxs-lookup"><span data-stu-id="20d64-176">By default, the table is sorted by the total number of service responses in descending order, but you can change the sorting order by clicking any of the column headers.</span></span>

<span data-ttu-id="20d64-177">Sie können auch nur Ratenbegrenzungsfehler anzeigen, indem Sie **Begrenzung der Übertragungsrate** auswählen.</span><span class="sxs-lookup"><span data-stu-id="20d64-177">You can also view only rate limiting errors by selecting **Rate limiting**.</span></span> <span data-ttu-id="20d64-178">Zeigt die täglichen Fehler bei der Begrenzung der Übertragungsrate (429) und der Ratenbegrenzungsausnahmen (429E) bei Xbox Live-Diensten, Endpunkten und Statuscodes über den ausgewählten Zeitraum an.</span><span class="sxs-lookup"><span data-stu-id="20d64-178">This shows the number of daily rate limiting (429) and rate limiting exempt (429E) errors across each Xbox Live service, endpoint, and status code over the selected period of time.</span></span>

> [!NOTE]
> <span data-ttu-id="20d64-179">Ein Statuscode 429E wurde tatsächlich erfolgreich als Statuscode 200 zurückgegeben, wäre jedoch in der Rate begrenzt, wenn der Dienst ein hohes Volumen zu dem Zeitpunkt hatte, daher wird empfohlen, dass Sie es den Fehler genauso behandeln, als ob er erzwungen (429) wurde.</span><span class="sxs-lookup"><span data-stu-id="20d64-179">A 429E status code was actually successfully returned as a 200 status code, but would have been rate-limited if the service was experiencing high volume at the time, so we recommend you treat it exactly the same as if it were enforced (429).</span></span>










 

 
