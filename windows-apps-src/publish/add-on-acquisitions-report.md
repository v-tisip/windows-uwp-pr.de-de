---
author: jnHs
Description: The Add-on acquisitions report in the Windows Dev Center dashboard lets you see how many add-ons you've sold, along with demographic and platform details.
title: Bericht zu Add-On-Käufen
ms.assetid: F2DF9188-0A98-4AC3-81C0-3E2C37B15582
ms.author: wdg-dev-content
ms.date: 05/24/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Add-On-Verkäufe, Add-On-Käufe, IAP-Verkauf, In-App-Produkte, IAPS, Add-Ons
ms.localizationpriority: medium
ms.openlocfilehash: 019bb410e6ac65f9951f06052c78f40e9a5f32e2
ms.sourcegitcommit: 232543fba1fb30bb1489b053310ed6bd4b8f15d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2018
ms.locfileid: "4180373"
---
# <a name="add-on-acquisitions-report"></a><span data-ttu-id="078a5-103">Bericht zu Add-On-Käufen</span><span class="sxs-lookup"><span data-stu-id="078a5-103">Add-on acquisitions report</span></span>


<span data-ttu-id="078a5-104">Der Bericht " **Add-on-Käufe** " im Windows Dev Center-Dashboard können Sie, wie viele Add-ons Sie, und Sie können demografische verkauft haben und plattformspezifische Details einsehen und zeigt Konvertierungsinformationen für Kunden unter Windows 10 (einschließlich Xbox).</span><span class="sxs-lookup"><span data-stu-id="078a5-104">The **Add-on acquisitions** report in the Windows Dev Center dashboard lets you see how many add-ons you've sold, along with demographic and platform details, and shows conversion info for customers on Windows 10 (including Xbox).</span></span> <span data-ttu-id="078a5-105">Sie können auch in der Nähe in Echtzeit Kaufdaten für den letzten oder 70-zwei Stunden-Zeitraum anzeigen.</span><span class="sxs-lookup"><span data-stu-id="078a5-105">You can also view near real-time acquisition data for the last hour or seventy-two hour period.</span></span>

<span data-ttu-id="078a5-106">Sie können diese Daten in Ihrem Dashboard anzeigen oder den [Bericht herunterladen](download-analytic-reports.md), um ihn offline anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="078a5-106">You can view this data in your dashboard, or [download the report](download-analytic-reports.md) to view offline.</span></span> <span data-ttu-id="078a5-107">Sie können diese Daten auch programmgesteuert mit der Methode [get add-on acquisitions](../monetize/get-in-app-acquisitions.md) der [Microsoft Store-Analyse-REST-API](../monetize/access-analytics-data-using-windows-store-services.md) abrufen.</span><span class="sxs-lookup"><span data-stu-id="078a5-107">Alternatively, you can programmatically retrieve this data by using the [get add-on acquisitions](../monetize/get-in-app-acquisitions.md) method in the [Microsoft Store analytics REST API](../monetize/access-analytics-data-using-windows-store-services.md).</span></span>

<span data-ttu-id="078a5-108">In diesem Bericht bedeutet ein „Add-On-Kauf”, dass ein Kunde ein Add-On von Ihnen erworben hat (oder ohne dafür zu bezahlen, wenn Sie es kostenlos angeboten haben).</span><span class="sxs-lookup"><span data-stu-id="078a5-108">In this report, an add-on acquisition means a customer has purchased an add-on from you (or acquired it without paying, if you offered it for free).</span></span> <span data-ttu-id="078a5-109">Wenn ein Kunde mehrere Käufe desselben konsumierbaren Add-Ons getätigt hat, werden diese als separate Add-On-Käufe aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="078a5-109">Multiple purchases of the same consumable add-on by the same customer are counted as separate add-on acquisitions.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="078a5-110">Im Bericht **Add-On-Käufe** sind keine Daten über Erstattungen, Rückbuchungen, Rückvergütungen usw. enthalten. Besuchen Sie [Auszahlungszusammenfassung](payout-summary.md), um die Erträge aus Ihren Apps zu schätzen.</span><span class="sxs-lookup"><span data-stu-id="078a5-110">The **Add-on acquisitions** report does not include data about refunds, reversals, chargebacks, etc. To estimate your app proceeds, visit [Payout summary](payout-summary.md).</span></span> <span data-ttu-id="078a5-111">Klicken Sie im Abschnitt **Reserviert** auf den Link **Reservierte Transaktionen herunterladen**.</span><span class="sxs-lookup"><span data-stu-id="078a5-111">In the **Reserved** section, click the **Download reserved transactions** link.</span></span>


## <a name="apply-filters"></a><span data-ttu-id="078a5-112">Anwenden von Filtern</span><span class="sxs-lookup"><span data-stu-id="078a5-112">Apply filters</span></span>

<span data-ttu-id="078a5-113">Im oberen Bereich der Seite können Sie den Zeitraum auswählen, für den die Daten angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="078a5-113">Near the top of the page, you can select the time period for which you want to show data.</span></span> <span data-ttu-id="078a5-114">Die Standardeinstellung ist **30D** (30Tage), aber Sie können Daten für 3, 6 oder 12Monate anzeigen, oder für einen benutzerdefinierten Zeitraum, den Sie angeben.</span><span class="sxs-lookup"><span data-stu-id="078a5-114">The default selection is **30D** (30 days), but you can choose to show data for 3, 6, or 12 months, or for a custom data range that you specify.</span></span> <span data-ttu-id="078a5-115">Sie können auch **1 H** oder **72 Stunden** Kaufdaten für eine Stunde oder 70-zwei Stunden nahezu in Echtzeit anzeigen auswählen. Diese Zeiträume gelten nur auf der Registerkarte " **Add-on täglich** " des Diagramms **Add-on-Käufe** und auf der Registerkarte " **Käufe** " des Diagramms **Märkte** .</span><span class="sxs-lookup"><span data-stu-id="078a5-115">You can also select **1H** or **72H** to show acquisition data in near real time for either one hour or seventy-two hours; these time periods only apply to the **Add-on daily** tab of the **Add-on acquisitions** chart and to the **Acquisitions** tab of the **Markets** chart.</span></span> 

<span data-ttu-id="078a5-116">Sie können ebenfalls **Filter** erweitern, um alle Daten auf dieser Seite nach bestimmten Add-Ons, Markt und/oder Gerätetyp zu filtern.</span><span class="sxs-lookup"><span data-stu-id="078a5-116">You can also expand **Filters** to filter all of the data on this page by particular add-on(s), by market and/or by device type.</span></span>

-   <span data-ttu-id="078a5-117">**Add-On**: der Standardfilter lautet **Alle Add-Ons**, aber Sie können die Daten für ein oder mehrere Add-Ons der App begrenzen.</span><span class="sxs-lookup"><span data-stu-id="078a5-117">**Add-on**: The default filter is **All add-ons**, but you can limit the data to one or more of the app's add-ons.</span></span>
-   <span data-ttu-id="078a5-118">**Markt**: der Standardfilter lautet **Alle Märkte**, aber Sie können die Daten für Verkäufe auf einen oder mehrere Märkte begrenzen.</span><span class="sxs-lookup"><span data-stu-id="078a5-118">**Market**: The default filter is **All markets**, but you can limit the data to acquisitions in one or more markets.</span></span>
-   <span data-ttu-id="078a5-119">**Gerätetyp**: Die Standardeinstellung ist **Alle Geräte**.</span><span class="sxs-lookup"><span data-stu-id="078a5-119">**Device type**: The default setting is **All devices**.</span></span> <span data-ttu-id="078a5-120">Wenn Daten für Käufe nur für einen bestimmten Gerätetyp angezeigt werden sollen (beispielsweise PCs, Konsolen oder Tablets), können Sie hier einen bestimmten angeben.</span><span class="sxs-lookup"><span data-stu-id="078a5-120">If you want to show data for acquisitions from a certain device type only (such as PC, console, or tablet), you can choose a specific one here.</span></span>

<span data-ttu-id="078a5-121">Die Informationen in allen unten angezeigten Diagrammen beziehen sich auf den ausgewählten Zeitraum und alle von Ihnen ausgewählten Filter.</span><span class="sxs-lookup"><span data-stu-id="078a5-121">The info in all of the charts listed below will reflect the date range and any filters you've selected.</span></span> <span data-ttu-id="078a5-122">In einigen Abschnitten können Sie zusätzliche Filter anwenden.</span><span class="sxs-lookup"><span data-stu-id="078a5-122">Some sections also allow you to apply additional filters.</span></span>


## <a name="add-on-acquisitions"></a><span data-ttu-id="078a5-123">Add-On-Käufe</span><span class="sxs-lookup"><span data-stu-id="078a5-123">Add-on acquisitions</span></span>

<span data-ttu-id="078a5-124">Das Diagramm **Add-On-Käufe** zeigt, wie oft Ihre Add-Ons im ausgewählten Zeitraum pro Tag oder Woche gekauft wurde.</span><span class="sxs-lookup"><span data-stu-id="078a5-124">The **Add-on acquisitions** chart shows the number of daily or weekly acquisitions of your add-ons over the selected period of time.</span></span> <span data-ttu-id="078a5-125">(Wenn Sie die Daten über einen längeren Zeitraum mithilfe von **Filter anwenden** anzeigen, werden die Erwerbsdaten nach Woche gruppiert.)</span><span class="sxs-lookup"><span data-stu-id="078a5-125">(When you use **Apply filters** to show data for a longer duration, the acquisition data will be grouped by week.)</span></span>

<span data-ttu-id="078a5-126">Sie können auch anzeigen, wie oft die App während ihrer gesamten Lebensdauer gekauft wurde, indem Sie **Add-On Insgesamt** auswählen.</span><span class="sxs-lookup"><span data-stu-id="078a5-126">You can also see the lifetime number of acquisitions for your app by selecting **Add-on cumulative**.</span></span> <span data-ttu-id="078a5-127">Zeigt den kumulierten Gesamtwert aller Käufe an (ab der ersten Veröffentlichung Ihrer App).</span><span class="sxs-lookup"><span data-stu-id="078a5-127">This shows the cumulative total of all acquisitions, starting from when your app was first published.</span></span>

<span data-ttu-id="078a5-128">Sie können optional die Ergebnisse danach filtern, ob der Erwerb der Add-On vom Client oder einem webbasierten Store und/oder Betriebssystemversion stammt.</span><span class="sxs-lookup"><span data-stu-id="078a5-128">You can optionally filter the results by whether the add-on acquisition originated from the client or web-based Store and/or by OS version.</span></span>


## <a name="customer-demographic"></a><span data-ttu-id="078a5-129">Kundendemografie</span><span class="sxs-lookup"><span data-stu-id="078a5-129">Customer demographic</span></span>

<span data-ttu-id="078a5-130">Das Diagramm **Kundendemografie** zeigt demografische Informationen zu den Kontakte, die Ihre Add-Ons erworben haben.</span><span class="sxs-lookup"><span data-stu-id="078a5-130">The **Customer demographic** chart shows demographic info about the people who acquired your add-ons.</span></span> <span data-ttu-id="078a5-131">Sie können sehen, wie viele Käufe (im ausgewählten Zeitraum) von Personen einer bestimmten Altersgruppe getätigt wurden und welches Geschlecht die Käufer hatten.</span><span class="sxs-lookup"><span data-stu-id="078a5-131">You can see how many acquisitions (over the selected period of time) were made by people in a certain age group and by which gender.</span></span>

> [!NOTE]
> <span data-ttu-id="078a5-132">Einige Kunden haben festgelegt, dass sie diese Informationen nicht freigeben möchten.</span><span class="sxs-lookup"><span data-stu-id="078a5-132">Some customers have opted not to share this info.</span></span> <span data-ttu-id="078a5-133">Falls die Altergruppe oder das Geschlecht nicht ermittelt werden konnten, wird der Kauf als **Unbekannt** kategorisiert.</span><span class="sxs-lookup"><span data-stu-id="078a5-133">If we were unable to determine the age group or gender, the acquisition is categorized as **Unknown**.</span></span>


## <a name="markets"></a><span data-ttu-id="078a5-134">Märkte</span><span class="sxs-lookup"><span data-stu-id="078a5-134">Markets</span></span>

<span data-ttu-id="078a5-135">Das Diagramm **Märkte** zeigt die Gesamtanzahl von Add-On-Käufen im ausgewählten Zeitraum für jeden Markt an, auf dem Ihre App erhältlich ist.</span><span class="sxs-lookup"><span data-stu-id="078a5-135">The **Markets** chart shows the total number of add-on acquisitions over the selected period of time for each market in which your app is available.</span></span> 

<span data-ttu-id="078a5-136">Sie können diese Daten in einer visuellen **Karte** anzeigen, oder die Einstellung auf eine Anzeige in Form einer **Tabelle** festlegen.</span><span class="sxs-lookup"><span data-stu-id="078a5-136">You can view this data in a visual **Map** form, or toggle the setting to view it in **Table** form.</span></span> <span data-ttu-id="078a5-137">Die Tabellenform zeigt jeweils fünf Märkten an, die alphabetisch oder nach der höchsten/niedrigst möglichen Anzahl von Käufen oder Installationen sortiert sind.</span><span class="sxs-lookup"><span data-stu-id="078a5-137">Table form will show five markets at a time, sorted either alphabetically or by highest/lowest number of acquisitions or installs.</span></span> <span data-ttu-id="078a5-138">Sie können auch die Daten zum Anzeigen von Informationen für alle Märkte zusammen herunterladen.</span><span class="sxs-lookup"><span data-stu-id="078a5-138">You can also download the data to view info for all markets together.</span></span>


## <a name="add-on-page-views-and-conversions-by-campaign-id"></a><span data-ttu-id="078a5-139">Add-On-Seitenaufrufe und -Konvertierungen nach Kampagnen-ID</span><span class="sxs-lookup"><span data-stu-id="078a5-139">Add-on page views and conversions by campaign ID</span></span>

<span data-ttu-id="078a5-140">Das Diagramm **Add-On-Seitenaufrufe und Konvertierungen nach Kampagnen-ID** zeigt die Gesamtanzahl der Add-On-Konvertierungen (Käufe) pro Kampagnen-ID im ausgewählten Zeitraum an und hilft Ihnen, Konvertierungen und Ansichten von Kunden unter Windows10 (einschließlich Xbox) für jede Seite der [benutzerdefinierte Werbekampagnen](create-a-custom-app-promotion-campaign.md) nachzuverfolgen.</span><span class="sxs-lookup"><span data-stu-id="078a5-140">The **Add-on page views and conversions by campaign ID** chart shows you the total number of add-on conversions (acquisitions) per campaign ID over the selected period of time, helping you track conversions and page views from customers on Windows 10 (including Xbox) for each of your [custom promotion campaigns](create-a-custom-app-promotion-campaign.md).</span></span> <span data-ttu-id="078a5-141">In diesem Diagramm werden nur die Add-On-Konvertierungen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="078a5-141">Only add-on conversions are shown in this chart.</span></span>

> [!NOTE]
> <span data-ttu-id="078a5-142">Der Kunden gelangt möglicherweise zu dem Eintrag Ihrer App durch Klicken auf eine nicht von Ihnen erstellte, benutzerdefinierte Kampagne.</span><span class="sxs-lookup"><span data-stu-id="078a5-142">Customers could arrive at your app's listing by clicking on a custom campaign not created by you.</span></span> <span data-ttu-id="078a5-143">Wir zählen jeden Seitenaufruf innerhalb einer Sitzung mit der Kampagnen-ID, die der Kunde zuerst im Store eingibt.</span><span class="sxs-lookup"><span data-stu-id="078a5-143">We stamp every page view within a session with the campaign ID from which the customer first entered the Store.</span></span> <span data-ttu-id="078a5-144">Wir fügen der Kampagnen-ID anschließend Konvertierungen für alle Käufe innerhalb von 24 Stunden hinzu.</span><span class="sxs-lookup"><span data-stu-id="078a5-144">We then attribute conversions to that campaign ID for all acquisitions within 24 hours.</span></span> <span data-ttu-id="078a5-145">Aus diesem Grund sehen Sie möglicherweise eine höhere Anzahl an Gesamtkonvertierungen als die Konvertierungen für Ihre Kampagnen-ID anzeigt, und Sie haben möglicherweise Konvertierungen oder Add-On-Konvertierungen, die keine Seitenansichten haben.</span><span class="sxs-lookup"><span data-stu-id="078a5-145">Because of this, you may see a higher number of total conversions than the total conversions for your campaign IDs, and you may have conversions or add-on conversions that have zero page views.</span></span> 


## <a name="conversions-breakdown-by-campaign-id"></a><span data-ttu-id="078a5-146">Aufschlüsselung der Konvertierungen nach Kampagnen-ID</span><span class="sxs-lookup"><span data-stu-id="078a5-146">Conversions breakdown by campaign ID</span></span>

<span data-ttu-id="078a5-147">Mit dem Diagramm **Aufschlüsselung der Konvertierungen nach Kampagnen-ID** können Sie Konvertierungen und Seitenaufrufe von Kunden unter Windows 10 wie oben beschrieben für jede Ihrer [benutzerdefinierten Werbekampagnen](create-a-custom-app-promotion-campaign.md) nachverfolgen,.</span><span class="sxs-lookup"><span data-stu-id="078a5-147">The **Conversions breakdown by campaign ID** chart lets you track conversions and page views from customers on Windows 10 for each of your [custom promotion campaigns](create-a-custom-app-promotion-campaign.md).</span></span> <span data-ttu-id="078a5-148">Sowohl App- und Add-On-Konvertierungen werden nach Kampagnen-ID angezeigt.</span><span class="sxs-lookup"><span data-stu-id="078a5-148">Both app and add-on conversions are shown per campaign ID.</span></span>

<span data-ttu-id="078a5-149">In diesem Diagramm bedeutet eine *Seitenansicht*, dass sich ein Kunde den App-Store-Eintrag angesehen hat.</span><span class="sxs-lookup"><span data-stu-id="078a5-149">In this chart, a *page view* means that a customer viewed the app's Store listing.</span></span> <span data-ttu-id="078a5-150">*Konvertierung* bedeutet, dass ein Kunde eine Lizenz für die App oder Add-On (entweder für eine kostenpflichtige oder eine kostenlose App) oder für ein Add-On neu erworben hat.</span><span class="sxs-lookup"><span data-stu-id="078a5-150">A *conversion* means that a customer has newly obtained a license for the app or add-on (whether you charged money or you've offered it for free).</span></span>

<span data-ttu-id="078a5-151">Beachten Sie, dass die Seitenansicht und Konvertierungszahlen nicht die Anzahl an eindeutigen Kunden wiedergeben.</span><span class="sxs-lookup"><span data-stu-id="078a5-151">Keep in mind that these page views and conversion numbers are not counts of unique customers.</span></span> 


## <a name="top-add-ons"></a><span data-ttu-id="078a5-152">Wichtigste Add-Ons</span><span class="sxs-lookup"><span data-stu-id="078a5-152">Top add-ons</span></span>

<span data-ttu-id="078a5-153">Das Diagramm **Wichtigste Add-Ons** zeigt die Gesamtanzahl von Käufen für jedes Ihrer Add-Ons im ausgewählten Zeitraum nach Markt an, damit Sie sehen können, welche Add-Ons am beliebtesten sind.</span><span class="sxs-lookup"><span data-stu-id="078a5-153">The **Top add-ons** chart shows the total number of acquisitions for each of your add-ons over the selected period of time, so you can see which of your add-ons are the most popular.</span></span> 



 

 
