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
# <a name="ad-mediation-report"></a>Bericht „Anzeigenvermittlung“

Dieser Bericht zeigt Anzeigenvermittlungsdaten für Windows8.x- oder Windows Phone8.x-Apps, die ein **AdMediatorControl**-Element aus dem [Microsoft Advertising-SDK für Windows und Windows Phone8.x](http://aka.ms/store-8-sdk) zum Einblenden von Banneranzeigen aus mehreren Anzeigennetzwerken verwenden. Für diese Apps gibt der Bericht „Anzeigenvermittlung“ Aufschluss über Ihre effektive Füllrate und die jeweiligen Füllraten für die verwendeten Anzeigennetzwerke. Außerdem finden Sie hier die Übernahmeraten Ihrer jeweiligen Vermittlungskonfigurationen sowie Informationen zu Fehlern, die von Anzeigennetzwerken oder vom Vermittler gemeldet wurden. Sie können diese Daten in Ihrem Dashboard anzeigen oder den [Bericht herunterladen](download-analytic-reports.md), um ihn offline anzuzeigen.

> [!NOTE]
> Der Bericht **Anzeigenvermittlung** ist nur verfügbar, wenn Sie **AdMediatorControl** in Ihrer Windows8.x oder Windows Phone8.x-App verwenden. Weitere Informationen finden Sie in [diesem Artikel](https://msdn.microsoft.com/library/windows/apps/xaml/dn864359). Für eine UWP-App, die [Anzeigenvermittlung](monetize-with-ads.md#mediation) in einem **AdControl**- oder **InterstitialAd**-Steuerelement verwendet, verwenden Sie den [Bericht zur Anzeigenleistung](advertising-performance-report.md), um Performance-Daten für die Anzeigennetzwerke zu überprüfen.

## <a name="page-filters"></a>Seitenfilter

Im oberen Seitenbereich können Sie die **Seitenfilter** erweitern, um alle Daten auf dieser Seite nach Datumsbereich und/oder Markt zu filtern.

-   **Datum**: Der Standardfilter lautet **Letzte 30 Tage**, aber er kann bis auf **Letzte 12 Monate** erweitert werden.
-   **Markt**: Die Standardeinstellung ist **Alle Märkte**. Sie können einen bestimmten Markt auswählen, wenn auf dieser Seite nur Bewertungen der in diesem Markt ansässigen Kunden angezeigt werden sollen.
-   **Plattform**: Die Standardeinstellung ist **Alle Plattformen**. Wenn Ihre App auf mehrere Plattformen ausgerichtet ist, können Sie eine bestimmte Plattform auswählen.

Die Informationen in allen unten angezeigten Diagrammen beziehen sich auf den unter **Seitenfilter** ausgewählten Zeitraum. Standardmäßig gehören dazu Daten aus allen Märkten und Plattformen, unter denen Ihre App aufgeführt ist, sofern Sie nicht den **Seitenfilter** ausgewählt haben, um einen bestimmten Markt und/oder eine bestimmte Plattform festzulegen.

## <a name="ad-mediation-performance"></a>Leistung der Anzeigenvermittlung

Das Diagramm **Leistung der Anzeigenvermittlung** zeigt die durchschnittliche Gesamtfüllrate im ausgewählten Zeitraum. Dies ist die durchschnittliche Füllrate bezogen auf alle Benutzersitzungen. Die Füllrate ist unabhängig von der Vermittlungskonfiguration oder der Anzahl von Aufrufen unterschiedlicher Anzeigennetzwerke.

Sie können auf die Überschrift **Vermittlungsanforderungen** klicken, um die durchschnittliche Anzahl einzelner Vermittlungsanforderungen anzuzeigen. Um die durchschnittliche Anzahl bereitgestellter Anzeigen anzuzeigen, klicken Sie auf **Bereitgestellte Anzeigen**.

## <a name="ad-provider-fill-rates"></a>Füllrate der Anzeigenanbieter

Das Diagramm **Füllrate der Anzeigenanbieter** zeigt die durchschnittliche Füllrate jedes Ihrer Anzeigennetzwerke im ausgewählten Zeitraum.

Die Informationen zu den einzelnen Anzeigennetzwerken werden zusammen angezeigt, um Leistungsvergleiche zwischen den Anzeigennetzwerken zu ermöglichen.

## <a name="unique-users-per-mediation-configuration"></a>Individuelle Benutzer pro Vermittlungskonfiguration

Das Diagramm **Individuelle Benutzer pro Vermittlungskonfiguration** zeigt die Gesamtanzahl von eindeutigen Benutzern, die im ausgewählten Zeitraum jede Version Ihrer Vermittlungskonfiguration erhalten haben.

## <a name="errors-by-ad-network"></a>Fehler nach Anzeigennetzwerk

Das Diagramm **Fehler nach Anzeigennetzwerk** zeigt die Gesamtanzahl von Anforderungen und Fehlern der einzelnen Anzeigennetzwerke zusammen mit dem Prozentsatz der Anforderungen, die einen Fehler verursacht haben.

## <a name="errors-by-type"></a>Fehler nach Typ

Das Diagramm **Fehler nach Typ** zeigt die spezifischen Fehler, die in den einzelnen Anzeigennetzwerken aufgetreten sind. Darüber hinaus enthält das Diagramm einen Prozentsatz, der angibt, wie häufig ein bestimmter Fehler bezogen auf die Gesamtfehleranzahl im Netzwerk aufgetreten ist. So erhalten Sie einen Eindruck davon, welche Fehler in einem Anzeigennetzwerk häufig vorkommen.

 

 
