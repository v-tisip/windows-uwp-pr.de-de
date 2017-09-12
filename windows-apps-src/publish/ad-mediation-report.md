---
author: jnHs
Description: "Der Bericht „Anzeigenvermittlung“ gibt Aufschluss über Ihre effektive Füllrate und die jeweiligen Füllraten für die verwendeten Anzeigennetzwerke."
title: "Bericht „Anzeigenvermittlung“"
ms.assetid: 18A33928-B9F2-4F76-9A9C-F01FEE42FEA1
ms.author: wdg-dev-content
ms.date: 06/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 0c08c1061231b033dc5401c77085e16ea7001bb1
ms.sourcegitcommit: fadde8afee46238443ec1cb71846d36c91db9fb9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2017
---
# <a name="ad-mediation-report"></a><span data-ttu-id="7d889-104">Bericht „Anzeigenvermittlung“</span><span class="sxs-lookup"><span data-stu-id="7d889-104">Ad mediation report</span></span>

<span data-ttu-id="7d889-105">Dieser Bericht zeigt Anzeigenvermittlungsdaten für Windows8.x- oder Windows Phone8.x-Apps, die ein **AdMediatorControl**-Element aus dem [Microsoft Advertising-SDK für Windows und Windows Phone8.x](http://aka.ms/store-8-sdk) zum Einblenden von Banneranzeigen aus mehreren Anzeigennetzwerken verwenden.</span><span class="sxs-lookup"><span data-stu-id="7d889-105">This report shows ad mediation data for Windows 8.x or Windows Phone 8.x apps that use an **AdMediatorControl** from the [Microsoft Advertising SDK for Windows and Windows Phone 8.x](http://aka.ms/store-8-sdk) to mediate banner ads from multiple ad networks.</span></span> <span data-ttu-id="7d889-106">Für diese Apps gibt der Bericht „Anzeigenvermittlung“ Aufschluss über Ihre effektive Füllrate und die jeweiligen Füllraten für die verwendeten Anzeigennetzwerke.</span><span class="sxs-lookup"><span data-stu-id="7d889-106">For these apps, this report lets you see your effective fill rate and the respective fill rates for the ad networks you're using.</span></span> <span data-ttu-id="7d889-107">Außerdem finden Sie hier die Übernahmeraten Ihrer jeweiligen Vermittlungskonfigurationen sowie Informationen zu Fehlern, die von Anzeigennetzwerken oder vom Vermittler gemeldet wurden.</span><span class="sxs-lookup"><span data-stu-id="7d889-107">It also shows the adoption rates of each of your mediation configurations and provides visibility into errors reported by ad networks and the mediator.</span></span> <span data-ttu-id="7d889-108">Sie können diese Daten in Ihrem Dashboard anzeigen oder den [Bericht herunterladen](download-analytic-reports.md), um ihn offline anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="7d889-108">You can view this data in your dashboard, or [download the report](download-analytic-reports.md) to view offline.</span></span>

> [!NOTE]
> <span data-ttu-id="7d889-109">Der Bericht **Anzeigenvermittlung** ist nur verfügbar, wenn Sie **AdMediatorControl** in Ihrer Windows8.x oder Windows Phone8.x-App verwenden.</span><span class="sxs-lookup"><span data-stu-id="7d889-109">The **Ad mediation** report is only available if you are using an **AdMediatorControl** in your Windows 8.x or Windows Phone 8.x app.</span></span> <span data-ttu-id="7d889-110">Weitere Informationen finden Sie in [diesem Artikel](https://msdn.microsoft.com/library/windows/apps/xaml/dn864359).</span><span class="sxs-lookup"><span data-stu-id="7d889-110">For more information, see [this article](https://msdn.microsoft.com/library/windows/apps/xaml/dn864359).</span></span> <span data-ttu-id="7d889-111">Für eine UWP-App, die [Anzeigenvermittlung](monetize-with-ads.md#mediation) in einem **AdControl**- oder **InterstitialAd**-Steuerelement verwendet, verwenden Sie den [Bericht zur Anzeigenleistung](advertising-performance-report.md), um Performance-Daten für die Anzeigennetzwerke zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="7d889-111">For a UWP app that uses [ad mediation](monetize-with-ads.md#mediation) in an **AdControl** or **InterstitialAd** control, use the [Advertising performance report](advertising-performance-report.md) to review performance data for the ad networks.</span></span>

## <a name="page-filters"></a><span data-ttu-id="7d889-112">Seitenfilter</span><span class="sxs-lookup"><span data-stu-id="7d889-112">Page filters</span></span>

<span data-ttu-id="7d889-113">Im oberen Seitenbereich können Sie die **Seitenfilter** erweitern, um alle Daten auf dieser Seite nach Datumsbereich und/oder Markt zu filtern.</span><span class="sxs-lookup"><span data-stu-id="7d889-113">Near the top of the page, you can expand **Page filters** to filter all of the data on this page by date range and/or by market.</span></span>

-   <span data-ttu-id="7d889-114">**Datum**: Der Standardfilter lautet **Letzte 30 Tage**, aber er kann bis auf **Letzte 12 Monate** erweitert werden.</span><span class="sxs-lookup"><span data-stu-id="7d889-114">**Date**: The default filter is **Last 30 days**, but you can expand this up to **Last 12 months**.</span></span>
-   <span data-ttu-id="7d889-115">**Markt**: Die Standardeinstellung ist **Alle Märkte**.</span><span class="sxs-lookup"><span data-stu-id="7d889-115">**Market**: The default setting is **All markets**.</span></span> <span data-ttu-id="7d889-116">Sie können einen bestimmten Markt auswählen, wenn auf dieser Seite nur Bewertungen der in diesem Markt ansässigen Kunden angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="7d889-116">You can choose a specific market if you want this page to only show ratings from customers in that market.</span></span>
-   <span data-ttu-id="7d889-117">**Plattform**: Die Standardeinstellung ist **Alle Plattformen**.</span><span class="sxs-lookup"><span data-stu-id="7d889-117">**Platform**: The default setting is **All platforms**.</span></span> <span data-ttu-id="7d889-118">Wenn Ihre App auf mehrere Plattformen ausgerichtet ist, können Sie eine bestimmte Plattform auswählen.</span><span class="sxs-lookup"><span data-stu-id="7d889-118">If your app targets multiple platforms, you can choose a specific platform.</span></span>

<span data-ttu-id="7d889-119">Die Informationen in allen unten angezeigten Diagrammen beziehen sich auf den unter **Seitenfilter** ausgewählten Zeitraum.</span><span class="sxs-lookup"><span data-stu-id="7d889-119">The info in all of the charts listed below will reflect the period of time selected in **Page filters**.</span></span> <span data-ttu-id="7d889-120">Standardmäßig gehören dazu Daten aus allen Märkten und Plattformen, unter denen Ihre App aufgeführt ist, sofern Sie nicht den **Seitenfilter** ausgewählt haben, um einen bestimmten Markt und/oder eine bestimmte Plattform festzulegen.</span><span class="sxs-lookup"><span data-stu-id="7d889-120">By default this will include data from all of the markets and platforms in which your app is listed, unless you've used the **Page filters** to specify a specific market and/or platform.</span></span>

## <a name="ad-mediation-performance"></a><span data-ttu-id="7d889-121">Leistung der Anzeigenvermittlung</span><span class="sxs-lookup"><span data-stu-id="7d889-121">Ad mediation performance</span></span>

<span data-ttu-id="7d889-122">Das Diagramm **Leistung der Anzeigenvermittlung** zeigt die durchschnittliche Gesamtfüllrate im ausgewählten Zeitraum.</span><span class="sxs-lookup"><span data-stu-id="7d889-122">The **Ad mediation performance** chart shows the average total fill rate over the selected period of time.</span></span> <span data-ttu-id="7d889-123">Dies ist die durchschnittliche Füllrate bezogen auf alle Benutzersitzungen. Die Füllrate ist unabhängig von der Vermittlungskonfiguration oder der Anzahl von Aufrufen unterschiedlicher Anzeigennetzwerke.</span><span class="sxs-lookup"><span data-stu-id="7d889-123">This is the average fill rate across all user sessions, regardless of your mediation configuration or how often different ad networks were called.</span></span>

<span data-ttu-id="7d889-124">Sie können auf die Überschrift **Vermittlungsanforderungen** klicken, um die durchschnittliche Anzahl einzelner Vermittlungsanforderungen anzuzeigen. Um die durchschnittliche Anzahl bereitgestellter Anzeigen anzuzeigen, klicken Sie auf **Bereitgestellte Anzeigen**.</span><span class="sxs-lookup"><span data-stu-id="7d889-124">You can click the **Mediation requests** heading to see the average number of individual mediation requests, or click **Ads delivered** to see the average total number of ads delivered.</span></span>

## <a name="ad-provider-fill-rates"></a><span data-ttu-id="7d889-125">Füllrate der Anzeigenanbieter</span><span class="sxs-lookup"><span data-stu-id="7d889-125">Ad provider fill rates</span></span>

<span data-ttu-id="7d889-126">Das Diagramm **Füllrate der Anzeigenanbieter** zeigt die durchschnittliche Füllrate jedes Ihrer Anzeigennetzwerke im ausgewählten Zeitraum.</span><span class="sxs-lookup"><span data-stu-id="7d889-126">The **Ad provider fill rates** chart shows the average fill rate of each of your ad networks over the selected period of time.</span></span>

<span data-ttu-id="7d889-127">Die Informationen zu den einzelnen Anzeigennetzwerken werden zusammen angezeigt, um Leistungsvergleiche zwischen den Anzeigennetzwerken zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="7d889-127">Info for each ad network is shown together to help you compare each ad network's performance.</span></span>

## <a name="unique-users-per-mediation-configuration"></a><span data-ttu-id="7d889-128">Individuelle Benutzer pro Vermittlungskonfiguration</span><span class="sxs-lookup"><span data-stu-id="7d889-128">Unique users per mediation configuration</span></span>

<span data-ttu-id="7d889-129">Das Diagramm **Individuelle Benutzer pro Vermittlungskonfiguration** zeigt die Gesamtanzahl von eindeutigen Benutzern, die im ausgewählten Zeitraum jede Version Ihrer Vermittlungskonfiguration erhalten haben.</span><span class="sxs-lookup"><span data-stu-id="7d889-129">The **Unique users per mediation configuration** chart shows the total number of unique users who received each version of your mediation configuration over the selected period of time.</span></span>

## <a name="errors-by-ad-network"></a><span data-ttu-id="7d889-130">Fehler nach Anzeigennetzwerk</span><span class="sxs-lookup"><span data-stu-id="7d889-130">Errors by ad network</span></span>

<span data-ttu-id="7d889-131">Das Diagramm **Fehler nach Anzeigennetzwerk** zeigt die Gesamtanzahl von Anforderungen und Fehlern der einzelnen Anzeigennetzwerke zusammen mit dem Prozentsatz der Anforderungen, die einen Fehler verursacht haben.</span><span class="sxs-lookup"><span data-stu-id="7d889-131">The **Errors by ad network** chart shows the total number of requests and errors for each of your ad networks, along with the percentage of requests that resulted in an error.</span></span>

## <a name="errors-by-type"></a><span data-ttu-id="7d889-132">Fehler nach Typ</span><span class="sxs-lookup"><span data-stu-id="7d889-132">Errors by type</span></span>

<span data-ttu-id="7d889-133">Das Diagramm **Fehler nach Typ** zeigt die spezifischen Fehler, die in den einzelnen Anzeigennetzwerken aufgetreten sind.</span><span class="sxs-lookup"><span data-stu-id="7d889-133">The **Errors by type** chart shows the specific errors experienced by each ad network.</span></span> <span data-ttu-id="7d889-134">Darüber hinaus enthält das Diagramm einen Prozentsatz, der angibt, wie häufig ein bestimmter Fehler bezogen auf die Gesamtfehleranzahl im Netzwerk aufgetreten ist. So erhalten Sie einen Eindruck davon, welche Fehler in einem Anzeigennetzwerk häufig vorkommen.</span><span class="sxs-lookup"><span data-stu-id="7d889-134">It also shows the percentage of total errors for that network that a specific error represents, so you can get an idea of which errors are coming up frequently per ad network.</span></span>

 

 
