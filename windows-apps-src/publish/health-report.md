---
author: jnHs
Description: "Über den Bericht „Integrität“ im Windows Dev Center-Dashboard können Sie Daten zur Leistung und Qualität Ihrer App einschließlich App-Abstürzen abrufen."
title: "Integritätsbericht"
ms.assetid: 4F671543-1E91-4E59-88A3-638E3E64539A
ms.author: wdg-dev-content
ms.date: 07/10/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 67f87405f7738dec591c71678ecfa5122e673502
ms.sourcegitcommit: ae93435e1f9c010a054f55ed7d6bd2f268223957
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2017
---
# <a name="health-report"></a><span data-ttu-id="43df8-104">Integritätsbericht</span><span class="sxs-lookup"><span data-stu-id="43df8-104">Health report</span></span>


<span data-ttu-id="43df8-105">Über den Bericht **Integrität** im Windows Dev Center-Dashboard können Sie Daten zur Leistung und Qualität Ihrer App, einschließlich App-Abstürzen, abrufen.</span><span class="sxs-lookup"><span data-stu-id="43df8-105">The **Health** report in the Windows Dev Center dashboard lets you get data related to the performance and quality of your app, including crashes and unresponsive events.</span></span> <span data-ttu-id="43df8-106">Sie können diese Daten in Ihrem Dashboard anzeigen oder den [Bericht herunterladen](download-analytic-reports.md), um ihn offline anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="43df8-106">You can view this data in your dashboard, or [download the report](download-analytic-reports.md) to view offline.</span></span> <span data-ttu-id="43df8-107">Bei Bedarf können Sie Stapelüberwachungen und/oder CAB-Dateien für weitere Debugzwecke anzeigen.</span><span class="sxs-lookup"><span data-stu-id="43df8-107">Where applicable, you can view stack traces and/or CAB files for further debugging.</span></span>

<span data-ttu-id="43df8-108">Sie können die Daten in diesem Bericht aber auch programmgesteuert mit der [Windows Store-REST-API für Analysen](../monetize/access-analytics-data-using-windows-store-services.md) abrufen.</span><span class="sxs-lookup"><span data-stu-id="43df8-108">Alternatively, you can programmatically retrieve the data in this report by using the [Windows Store analytics REST API](../monetize/access-analytics-data-using-windows-store-services.md).</span></span>


## <a name="apply-filters"></a><span data-ttu-id="43df8-109">Anwenden von Filtern</span><span class="sxs-lookup"><span data-stu-id="43df8-109">Apply filters</span></span>

<span data-ttu-id="43df8-110">Im oberen Bereich der Seite können Sie den Zeitraum auswählen, für den die Daten angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="43df8-110">Near the top of the page, you can select the time period for which you want to show data.</span></span> <span data-ttu-id="43df8-111">Die Standardeinstellung ist **72 H** (72 Stunden), Sie können stattdessen aber auch **30D** auswählen, um die Daten der letzten 30Tage anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="43df8-111">The default selection is **72H** (72 hours), but you can choose **30D** instead to show data over the last 30 days.</span></span>

<span data-ttu-id="43df8-112">Sie können ebenfalls **Filter** erweitern, um alle Daten auf dieser Seite nach Paketversion, Markt und/oder Gerätetyp zu filtern.</span><span class="sxs-lookup"><span data-stu-id="43df8-112">You can also expand **Filters** to filter all of the data on this page by package version, market, and/or device type.</span></span>

-   <span data-ttu-id="43df8-113">**Paketversion**: Die Standardeinstellung ist **Alle**.</span><span class="sxs-lookup"><span data-stu-id="43df8-113">**Package version**: The default setting is **All**.</span></span> <span data-ttu-id="43df8-114">Wenn Ihre App mehr als ein Paket enthält, können Sie hier ein bestimmtes Paket auswählen.</span><span class="sxs-lookup"><span data-stu-id="43df8-114">If your app includes more than one package, you can choose a specific one here.</span></span>
-   <span data-ttu-id="43df8-115">**Markt**: der Standardfilter lautet **Alle Märkte**, aber Sie können die Daten für Verkäufe auf einen oder mehrere Märkte begrenzen.</span><span class="sxs-lookup"><span data-stu-id="43df8-115">**Market**: The default filter is **All markets**, but you can limit the data to acquisitions in one or more markets.</span></span>
-   <span data-ttu-id="43df8-116">**Gerätetyp**: Die Standardeinstellung ist **Alle**, Sie können jedoch festlegen, dass nur Daten für einen bestimmten Gerätetyp angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="43df8-116">**Device type**: The default setting is **All**, but you can choose to show data for only one specific device type.</span></span>
-   <span data-ttu-id="43df8-117">**Betriebssystemversion**: Die Standardeinstellung lautet **Alle BS-Versionen**, Sie können jedoch eine bestimmte Version des Betriebssystems auswählen.</span><span class="sxs-lookup"><span data-stu-id="43df8-117">**OS version**: The default is **All OS versions**, but you can choose a specific OS version.</span></span>

<span data-ttu-id="43df8-118">Die Informationen in allen unten angezeigten Diagrammen beziehen sich auf den ausgewählten Zeitraum und alle von Ihnen ausgewählten Filter.</span><span class="sxs-lookup"><span data-stu-id="43df8-118">The info in all of the charts listed below will reflect the date range and any filters you've selected.</span></span> <span data-ttu-id="43df8-119">In einigen Abschnitten können Sie zusätzliche Filter anwenden.</span><span class="sxs-lookup"><span data-stu-id="43df8-119">Some sections also allow you to apply additional filters.</span></span>


## <a name="failure-hits"></a><span data-ttu-id="43df8-120">Fehlertreffer</span><span class="sxs-lookup"><span data-stu-id="43df8-120">Failure hits</span></span>

<span data-ttu-id="43df8-121">Das Diagramm **Fehlertreffer** zeigt die Anzahl von täglichen Abstürzen und Ereignissen, die Kunden bei der Nutzung Ihrer App im ausgewählten Zeitraum festgestellt haben.</span><span class="sxs-lookup"><span data-stu-id="43df8-121">The **Failure hits** chart shows the number of daily crashes and events that customers experienced when using your app during the selected period of time.</span></span> <span data-ttu-id="43df8-122">Jeder Ereignistyp, der in der App aufgetreten ist, wird separat überwacht: Abstürze, Blockaden, JavaScript-Ausnahmen und Speicherfehler.</span><span class="sxs-lookup"><span data-stu-id="43df8-122">Each type of event that your app experienced is tracked separately: crashes, hangs, JavaScript exceptions, and memory failures.</span></span>


## <a name="failure-hits-by-market"></a><span data-ttu-id="43df8-123">Fehlertreffer nach Markt</span><span class="sxs-lookup"><span data-stu-id="43df8-123">Failure hits by market</span></span>

<span data-ttu-id="43df8-124">Das Diagramm **Fehlertreffer nach Markt** zeigt die Gesamtanzahl von Abstürzen und Ereignissen im ausgewählten Zeitraum nach Markt an.</span><span class="sxs-lookup"><span data-stu-id="43df8-124">The **Failure hits by market** chart shows the total number of crashes and events over the selected period of time by market.</span></span>

<span data-ttu-id="43df8-125">Sie können diese Daten in einer visuellen **Karte** anzeigen, oder die Einstellung auf eine Anzeige in Form einer **Tabelle** festlegen.</span><span class="sxs-lookup"><span data-stu-id="43df8-125">You can view this data in a visual **Map** form, or toggle the setting to view it in **Table** form.</span></span> <span data-ttu-id="43df8-126">Die Tabellenform zeigt jeweils fünf Märkten an, die alphabetisch oder nach der höchsten/niedrigst möglichen Anzahl von Anwendersitzungen sortiert sind.</span><span class="sxs-lookup"><span data-stu-id="43df8-126">Table form will show five markets at a time, sorted either alphabetically or by highest/lowest number of user sessions.</span></span> <span data-ttu-id="43df8-127">Sie können auch die Daten zum Anzeigen von Informationen für alle Märkte zusammen herunterladen.</span><span class="sxs-lookup"><span data-stu-id="43df8-127">You can also download the data to view info for all markets together.</span></span>


## <a name="package-version"></a><span data-ttu-id="43df8-128">Paketversion</span><span class="sxs-lookup"><span data-stu-id="43df8-128">Package version</span></span>

<span data-ttu-id="43df8-129">Das Diagramm **Paketversion** zeigt die Gesamtanzahl von Abstürzen und Ereignissen im ausgewählten Zeitraum nach Paketversion an.</span><span class="sxs-lookup"><span data-stu-id="43df8-129">The **Package version** chart shows the total number of crashes and events over the selected period of time by package version.</span></span> <span data-ttu-id="43df8-130">In der Standardeinstellung wird die Paketversion mit den meisten Treffern an oberster Stelle vor den Märkten mit weniger Treffern angezeigt.</span><span class="sxs-lookup"><span data-stu-id="43df8-130">By default, we show you the package version that had the most hits on top and continue downward from there.</span></span> <span data-ttu-id="43df8-131">Sie können die Reihenfolge umkehren, indem Sie auf den Pfeil in der Spalte **Treffer** des Diagramms klicken.</span><span class="sxs-lookup"><span data-stu-id="43df8-131">You can reverse this order by toggling the arrow in the **Hits** column of this chart.</span></span>

## <a name="failures"></a><span data-ttu-id="43df8-132">Fehler</span><span class="sxs-lookup"><span data-stu-id="43df8-132">Failures</span></span>

<span data-ttu-id="43df8-133">Das Diagramm **Fehler** zeigt die Gesamtanzahl von Abstürzen und Ereignissen im ausgewählten Zeitraum nach Fehlername an.</span><span class="sxs-lookup"><span data-stu-id="43df8-133">The **Failures** chart shows the total number of crashes and events over the selected period of time by failure name.</span></span> <span data-ttu-id="43df8-134">In der Standardeinstellung wird der Fehler mit den meisten Treffern an oberster Stelle vor den Fehlern mit weniger Treffern angezeigt.</span><span class="sxs-lookup"><span data-stu-id="43df8-134">By default, we show you the failure that had the most hits on top and continue downward from there.</span></span> <span data-ttu-id="43df8-135">Sie können die Reihenfolge umkehren, indem Sie auf den Pfeil in der Spalte **Treffer** des Diagramms klicken.</span><span class="sxs-lookup"><span data-stu-id="43df8-135">You can reverse this order by toggling the arrow in the **Hits** column of this chart.</span></span> <span data-ttu-id="43df8-136">Außerdem wird für die einzelnen Fehler der Prozentsatz der Gesamtanzahl von Fehlern angezeigt.</span><span class="sxs-lookup"><span data-stu-id="43df8-136">For each failure, we also show its percentage of the total number of failures.</span></span>

<span data-ttu-id="43df8-137">Wählen Sie zum Anzeigen der **Fehlerdetails** für einen bestimmten Fehler den Fehlernamen aus.</span><span class="sxs-lookup"><span data-stu-id="43df8-137">To display the **Failure details** report for a particular failure, select the failure name.</span></span> <span data-ttu-id="43df8-138">Wenn Sie PDB-Symboldateien eingefügt haben, beinhaltet der Bericht **Fehlerdetails** die Anzahl der Fehlertreffer im letzten Monat sowie ein Fehlerprotokoll, in dem die entsprechenden Details (Datum, Paketversion, Gerätetyp, Gerätemodell, Betriebssystembuild) sowie ein Link zu der Ablaufverfolgung und/oder einer CAB-Datei, wenn verfügbar, aufgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="43df8-138">If you have included PDB symbol files, the **Failure details** report includes the number of failure hits over the last month, as well as a failure log that lists occurrence details (date, package version, device type, device model, OS build) and a link to the stack trace and/or CAB file, if available.</span></span>

> [!TIP]
> <span data-ttu-id="43df8-139">CAB-Dateien sind nur verfügbar, wenn Fehler auf einem Computer mit einer Windows-Insider-Build auftreten, daher haben nicht alle Fehler die Option zum Herunterladen einer CAB-Datei.</span><span class="sxs-lookup"><span data-stu-id="43df8-139">CAB files will only be available when the failure occurred on a computer using a Windows Insider build, so not all failures will include the CAB download option.</span></span> <span data-ttu-id="43df8-140">Klicken Sie auf die **Links** -Header im **Fehlerprotokoll** zum Sortieren der Ergebnisse, sodass Fehler, die CAB-Dateien enthalten, am oberen Rand der Liste angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="43df8-140">You can click the **Links** header in the **Failure log** to sort the results so that failures which include CAB files appear at the top of the list.</span></span>

 

 
