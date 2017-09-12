---
author: jnHs
Description: "Der Bericht „Nutzung“ im Windows Dev Center-Dashboard gibt Aufschluss darüber, wie Kunden Ihre App verwenden."
title: Nutzungsbericht
ms.assetid: 5F0E7F94-D121-4AD3-A6E5-9C0DEC437BD3
ms.author: wdg-dev-content
ms.date: 08/16/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: b3e7154a9dc8b7ecea8a319300ab482f61e0bb68
ms.sourcegitcommit: de6bc8acec2cd5ebc36bb21b2ce1a9980c3e78b2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="usage-report"></a><span data-ttu-id="fccc7-104">Nutzungsbericht</span><span class="sxs-lookup"><span data-stu-id="fccc7-104">Usage report</span></span>


<span data-ttu-id="fccc7-105">Im Bericht **Nutzung** im Windows Dev Center-Dashboard erfahren Sie, wie Kunden mit Windows10 Ihre App verwenden, und zeigt Informationen zu den von Ihnen definierten benutzerdefinierten Ereignissen.</span><span class="sxs-lookup"><span data-stu-id="fccc7-105">The **Usage** report in the Windows Dev Center dashboard lets you see how customers on Windows 10 are using your app and shows info about custom events that you've defined.</span></span> <span data-ttu-id="fccc7-106">Sie können diese Daten in Ihrem Dashboard anzeigen oder den [Bericht herunterladen](download-analytic-reports.md), um ihn offline anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="fccc7-106">You can view this data in your dashboard, or [download the report](download-analytic-reports.md) to view offline.</span></span>


## <a name="apply-filters"></a><span data-ttu-id="fccc7-107">Anwenden von Filtern</span><span class="sxs-lookup"><span data-stu-id="fccc7-107">Apply filters</span></span>

<span data-ttu-id="fccc7-108">Im oberen Bereich der Seite können Sie den Zeitraum auswählen, für den die Daten angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="fccc7-108">Near the top of the page, you can select the time period for which you want to show data.</span></span> <span data-ttu-id="fccc7-109">Die Standardeinstellung ist **30D** (30Tage), aber Sie können Daten für 3, 6 oder 12Monate anzeigen, oder für einen benutzerdefinierten Zeitraum, den Sie angeben.</span><span class="sxs-lookup"><span data-stu-id="fccc7-109">The default selection is **30D** (30 days), but you can choose to show data for 3, 6, or 12 months, or for a custom data range that you specify.</span></span>

<span data-ttu-id="fccc7-110">Sie können ebenfalls **Filter** erweitern, um Daten auf dieser Seite nach Paketversion, Markt und/oder Gerätetyp zu filtern.</span><span class="sxs-lookup"><span data-stu-id="fccc7-110">You can also expand **Filters** to filter the data on this page by package version, market, and/or device type.</span></span>

-   <span data-ttu-id="fccc7-111">**Paketversion**: Die Standardeinstellung ist **Alle**.</span><span class="sxs-lookup"><span data-stu-id="fccc7-111">**Package version**: The default setting is **All**.</span></span> <span data-ttu-id="fccc7-112">Wenn Ihre App mehr als ein Paket enthält, können Sie hier ein bestimmtes Paket auswählen.</span><span class="sxs-lookup"><span data-stu-id="fccc7-112">If your app includes more than one package, you can choose a specific one here.</span></span>
-   <span data-ttu-id="fccc7-113">**Markt**: der Standardfilter lautet **Alle Märkte**, aber Sie können die Daten für Verkäufe auf einen oder mehrere Märkte begrenzen.</span><span class="sxs-lookup"><span data-stu-id="fccc7-113">**Market**: The default filter is **All markets**, but you can limit the data to acquisitions in one or more markets.</span></span>
-   <span data-ttu-id="fccc7-114">**Gerätetyp**: Die Standardeinstellung ist **Alle**, Sie können jedoch festlegen, dass nur Daten für einen bestimmten Gerätetyp angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="fccc7-114">**Device type**: The default setting is **All**, but you can choose to show data for only one specific device type.</span></span>

<span data-ttu-id="fccc7-115">Die Informationen in allen unten angezeigten Diagrammen spiegelt den Zeitraum und die ausgewählten Filter wider (mit Ausnahme von **Neue Benutzer** im Diagramm **Nutzung**, das nicht angezeigt wird, wenn keine Filter ausgewählt sind).</span><span class="sxs-lookup"><span data-stu-id="fccc7-115">The info in all of the charts listed below will reflect the date range and any filters you've selected (with the exception of **New users** in the **Usage** chart, which will not appear if any filters are selected).</span></span> <span data-ttu-id="fccc7-116">In einigen Abschnitten können Sie zusätzliche Filter anwenden.</span><span class="sxs-lookup"><span data-stu-id="fccc7-116">Some sections also allow you to apply additional filters.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fccc7-117">Dieser Bericht enthält nur Nutzungsdaten von Kunden unter Windows10, die die Bereitstellung von Telemetriedaten nicht deaktiviert haben.</span><span class="sxs-lookup"><span data-stu-id="fccc7-117">This report only includes usage data from customers on Windows 10 who have not opted out of providing telemetry info.</span></span>


##<a name="usage"></a><span data-ttu-id="fccc7-118">Nutzung</span><span class="sxs-lookup"><span data-stu-id="fccc7-118">Usage</span></span>

<span data-ttu-id="fccc7-119">Das Diagramm **Nutzung** zeigt im Detail, wie Kunden Ihre App über den ausgewählten Zeitraum verwenden.</span><span class="sxs-lookup"><span data-stu-id="fccc7-119">The **Usage** chart shows details about how your customers are using your app over the selected period of time.</span></span> <span data-ttu-id="fccc7-120">In diesem Diagramm werden individuelle Benutzer Ihrer App oder Benutzersitzungen nicht einzeln nachverfolgt (d.h., ein Benutzer wird in diesem Diagramm unabhängig davon dargestellt, ob er Ihre App nur einmal oder mehrmals verwendet hat).</span><span class="sxs-lookup"><span data-stu-id="fccc7-120">Note this chart does not track unique users for your app or unique user sessions (that is, a user is represented in this chart whether they used your app just once or multiple times).</span></span>

<span data-ttu-id="fccc7-121">Dieses Diagramm enthält vier separate Registerkarten, die die Nutzung pro Tag oder Woche anzeigen (abhängig von der Dauer, die Sie ausgewählt haben).</span><span class="sxs-lookup"><span data-stu-id="fccc7-121">This chart has four separate tabs that you can view, showing usage by day or week (depending on the duration you've selected).</span></span>

- <span data-ttu-id="fccc7-122">**Benutzer**: Zeigt die Gesamtanzahl der **Benutzersitzungen** über den ausgewählten Zeitraum an.</span><span class="sxs-lookup"><span data-stu-id="fccc7-122">**Users**: Shows the total number of **user sessions** over the selected period of time.</span></span> <span data-ttu-id="fccc7-123">Jede Benutzersitzung stellt einen bestimmten Zeitraum dar, in dem ein Kunde mit der App interagiert hat.</span><span class="sxs-lookup"><span data-stu-id="fccc7-123">Each user session represents a distinct period of time when a customer interacted with your app.</span></span> <span data-ttu-id="fccc7-124">Da davon ausgegangen wird, dass jede Benutzersitzung nach einer Zeit der Inaktivität endet, kann ein einzelner Kunde am selben Tag oder in derselben Woche mehrere Benutzersitzungen führen.</span><span class="sxs-lookup"><span data-stu-id="fccc7-124">Each user session is considered to end after a period of inactivity, so a single customer could have multiple user sessions over the same day or week.</span></span> <span data-ttu-id="fccc7-125">Die Gesamtanzahl der **aktiven Benutzer** (alle Kunden, die die App an diesem Tag oder in dieser Woche nutzen) und **neuen Benutzer** (ein Kunde, der Ihre App das erste Mal an diesem Tag oder in der Woche nutzt) wird ebenfalls angezeigt.</span><span class="sxs-lookup"><span data-stu-id="fccc7-125">The total number of **Active users** (any customer using the app that day or week) and **New users** (a customer who used your app for the first time that day or week) are also shown.</span></span> <span data-ttu-id="fccc7-126">Wenn Sie Filter auf der Seite angewendet haben, werden **neue Benutzer** in diesem Diagramm nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="fccc7-126">Note that if you have applied any filters to the page, you won't see **New users** in this chart.</span></span>
- <span data-ttu-id="fccc7-127">**Geräte**: Zeigt die Anzahl der täglichen Geräte an, die von allen Benutzern zur Interaktion mit Ihrer App verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="fccc7-127">**Devices**: Shows the number of daily devices used to interact with your app by all users.</span></span>
- <span data-ttu-id="fccc7-128">**Dauer**: Zeigt die Gesamtanzahl der aktiven Minuten an (Minuten, in denen ein Benutzer aktiv Ihrer App verwendet).</span><span class="sxs-lookup"><span data-stu-id="fccc7-128">**Duration**: Shows the total engagement minutes (minutes where a user is actively using your app).</span></span>
- <span data-ttu-id="fccc7-129">**Beibehaltung**: Zeigt die Gesamtanzahl der **DAU/MAU** (tägliche aktive Benutzer/monatliche aktive Benutzer) über den ausgewählten Zeitraum an.</span><span class="sxs-lookup"><span data-stu-id="fccc7-129">**Retention**: Shows the total number of **DAU/MAU** (Daily Active Users/Monthly Active Users) over the selected period of time.</span></span>


## <a name="user-sessions"></a><span data-ttu-id="fccc7-130">Benutzersitzungen</span><span class="sxs-lookup"><span data-stu-id="fccc7-130">User sessions</span></span>

<span data-ttu-id="fccc7-131">Das Diagramm **Benutzersitzungen** zeigt die Gesamtzahl der Benutzersitzungen pro Markt für die App über den ausgewählten Zeitraum an.</span><span class="sxs-lookup"><span data-stu-id="fccc7-131">The **User sessions** chart shows the total number of user sessions for your app per market, over the selected period of time.</span></span>

<span data-ttu-id="fccc7-132">Genau wie in den Infos für die **Benutzersitzungen** stellen die Infos im Diagramm **Nutzung** eine Sitzung des Benutzers für einen bestimmten Zeitraum dar, wenn der Kunde mit der App interagiert. Dieses Diagramm verfolgt keine individuellen Benutzer Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="fccc7-132">As with the **User sessions** info in the **Usage** chart, a user session represents one distinct period of time when a customer interacted with your app, and this chart does not track unique users for your app.</span></span>

<span data-ttu-id="fccc7-133">Sie können diese Daten in einer visuellen **Karte** anzeigen, oder die Einstellung auf eine Anzeige in Form einer **Tabelle** festlegen.</span><span class="sxs-lookup"><span data-stu-id="fccc7-133">You can view this data in a visual **Map** form, or toggle the setting to view it in **Table** form.</span></span> <span data-ttu-id="fccc7-134">Die Tabellenform zeigt jeweils fünf Märkten an, die alphabetisch oder nach der höchsten/niedrigst möglichen Anzahl von Anwendersitzungen sortiert sind.</span><span class="sxs-lookup"><span data-stu-id="fccc7-134">Table form will show five markets at a time, sorted either alphabetically or by highest/lowest number of user sessions.</span></span> <span data-ttu-id="fccc7-135">Sie können auch die Daten zum Anzeigen von Informationen für alle Märkte zusammen herunterladen.</span><span class="sxs-lookup"><span data-stu-id="fccc7-135">You can also download the data to view info for all markets together.</span></span>


## <a name="package-version"></a><span data-ttu-id="fccc7-136">Paketversion</span><span class="sxs-lookup"><span data-stu-id="fccc7-136">Package version</span></span>

<span data-ttu-id="fccc7-137">Das Diagramm **Benutzersitzungen** zeigt die Gesamtzahl täglicher Benutzersitzungen pro Paketversion für die App über den ausgewählten Zeitraum an.</span><span class="sxs-lookup"><span data-stu-id="fccc7-137">The **User sessions** chart shows the total number of daily user sessions for your app per package version over the selected period of time.</span></span>

<span data-ttu-id="fccc7-138">Genau wie im Diagramm **Benutzersitzungen** stellen die Infos eine Sitzung des Benutzers für einen bestimmten Zeitraum dar, wenn der Kunde mit der App interagiert. Dieses Diagramm verfolgt keine individuellen Benutzer Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="fccc7-138">As with the **User sessions** chart, a user session represents one distinct period of time when a customer interacted with your app, and this chart does not track unique users for your app.</span></span>


## <a name="custom-events"></a><span data-ttu-id="fccc7-139">Benutzerdefinierte Ereignisse</span><span class="sxs-lookup"><span data-stu-id="fccc7-139">Custom events</span></span>

<span data-ttu-id="fccc7-140">Das Diagramm **Benutzerdefinierte Ereignisse** zeigt, wie häufig die für Ihre App definierten benutzerdefinierten Ereignisse insgesamt aufgetreten sind.</span><span class="sxs-lookup"><span data-stu-id="fccc7-140">The **Custom events** chart shows the total occurrences for custom events that you have defined for your app.</span></span> <span data-ttu-id="fccc7-141">Dazu können mehrere Vorkommen für denselben Kunden gehören.</span><span class="sxs-lookup"><span data-stu-id="fccc7-141">This may include multiple occurrences for the same customer.</span></span> <span data-ttu-id="fccc7-142">Mithilfe der Filter können Sie die benutzerdefinierten Ereignisse auswählen, für die Daten angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="fccc7-142">You can use the filters to select the specific custom events for which you want to see this data.</span></span>

<span data-ttu-id="fccc7-143">Benutzerdefinierte Ereignisse werden unter Verwendung der [StoreServicesCustomEventLogger.Log](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicescustomeventlogger.log.aspx)-Methode im [Microsoft Store Services SDK](../monetize/microsoft-store-services-sdk.md) implementiert.</span><span class="sxs-lookup"><span data-stu-id="fccc7-143">Custom events are implemented using the [StoreServicesCustomEventLogger.Log](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicescustomeventlogger.log.aspx) method in the [Microsoft Store Services SDK](../monetize/microsoft-store-services-sdk.md).</span></span>

<span data-ttu-id="fccc7-144">Weitere Informationen finden Sie unter [Protokollieren benutzerdefinierter Ereignisse für Dev Center](../monetize/log-custom-events-for-dev-center.md).</span><span class="sxs-lookup"><span data-stu-id="fccc7-144">For more info, see [Log custom events for Dev Center](../monetize/log-custom-events-for-dev-center.md).</span></span>


## <a name="custom-events-breakdown"></a><span data-ttu-id="fccc7-145">Übersicht über benutzerdefinierte Ereignisse</span><span class="sxs-lookup"><span data-stu-id="fccc7-145">Custom events breakdown</span></span>

<span data-ttu-id="fccc7-146">Das Diagramm **Übersicht über benutzerdefinierte Ereignisse** enthält weitere Details, wie oft jedes Ihre benutzerdefinierten Ereignisse aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="fccc7-146">The **Custom events breakdown** chart shows more details about how often each of your custom events occurred.</span></span> <span data-ttu-id="fccc7-147">Dadurch können Sie ermitteln, ob Ereignisse für einen bestimmten Markt, Gerätetyp oder eine Paketversionen häufiger auftreten.</span><span class="sxs-lookup"><span data-stu-id="fccc7-147">This can help you determine if events are occurring more often for a particular market, device type, or package versions.</span></span>

<span data-ttu-id="fccc7-148">Für jedes Ereignis wird der Name des Ereignisses und ein Ereignisanzahl angezeigt, die einer bestimmte Kombination von Markt, Gerätetyp und Paketversion des Benutzers entsprechen.</span><span class="sxs-lookup"><span data-stu-id="fccc7-148">For each event, you will see the event name and an event count that correspond to a specific combination of the user's market, device type, and package version.</span></span> <span data-ttu-id="fccc7-149">In der Regel wird ein Ereignis mehrmals angezeigt, zusammen mit verschiedenen Kombinationen dieser Faktoren.</span><span class="sxs-lookup"><span data-stu-id="fccc7-149">Typically, you'll see an event listed multiple times along with different combinations of these factors.</span></span> 




 
