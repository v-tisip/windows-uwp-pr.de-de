---
author: jnHs
Description: "Der Bericht „Anzeigenvermittlung“ gibt Aufschluss über Ihre effektive Füllrate und die jeweiligen Füllraten für die verwendeten Anzeigennetzwerke."
title: "Bericht „Anzeigenvermittlung“"
ms.assetid: 18A33928-B9F2-4F76-9A9C-F01FEE42FEA1
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows 10, UWP"
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: 3f3f3dd3b594e174def693b7decd21a5753172b9
ms.lasthandoff: 02/07/2017

---

# <a name="ad-mediation-report"></a>Bericht „Anzeigenvermittlung“


Der Bericht **Anzeigenvermittlung** gibt Aufschluss über Ihre effektive Füllrate und die jeweiligen Füllraten für die verwendeten Anzeigennetzwerke. Außerdem finden Sie hier die Übernahmeraten Ihrer jeweiligen Vermittlungskonfigurationen sowie Informationen zu Fehlern, die von Anzeigennetzwerken oder vom Vermittler gemeldet wurden. Sie können diese Informationen in Ihrem Dashboard anzeigen oder [den Bericht herunterladen](download-analytic-reports.md), um die Daten offline anzuzeigen.

**Wichtig**  Der Bericht **Anzeigenvermittlung** enthält nur Daten, wenn Sie die [Windows-Anzeigenvermittlung](https://msdn.microsoft.com/library/windows/apps/xaml/dn864359) in Ihrer App verwenden.

 

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

 

 





