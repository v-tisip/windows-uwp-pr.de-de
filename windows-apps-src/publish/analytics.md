---
author: shawjohn
Description: "Sie können für Ihre Apps detaillierte Analysen im Windows Dev Center-Dashboard anzeigen."
title: Analysen
ms.assetid: 3A3C6F10-0DB1-416D-B632-CD388EA66759
ms.author: johnshaw
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Analysen, Berichte, Dashboard, Apps
ms.openlocfilehash: 13a37a4ae2cea67fdce843ed4e6189797d85b93e
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="analytics"></a>Analysen

Sie können für Ihre Apps detaillierte Analysen im Windows Dev Center-Dashboard anzeigen. Statistiken und Diagramme geben Aufschluss über den Erfolg Ihrer Apps, z.B. wie viele Kunden Sie erreichen, wie die Kunden Ihre App einsetzen und was die Kunden über die App denken. Außerdem finden Sie dort Informationen zur App-Integrität, Anzeigennutzung und vieles mehr. Zeigen Sie die Berichte im Dashboard an, oder [laden Sie die erforderlichen Berichte herunter](download-analytic-reports.md), um Ihre Daten offline zu analysieren. Wir stellen Ihnen auch verschiedene Möglichkeiten für den [Zugriff auf Analysedaten ohne das Dashboard](#no-dashboard) zur Verfügung.

> [!NOTE]
> Zusätzlich zu den Dashboardberichten können Sie auf einige Analysedaten auch programmgesteuert mithilfe der [Windows Store-Analyse-REST-API](../monetize/access-analytics-data-using-windows-store-services.md) zugreifen.

## <a name="analytics-for-all-your-apps"></a>Analysen für Ihre gesamten Apps

Um die wichtigsten Analysen zu den am häufigsten heruntergeladenen Apps anzuzeigen, wählen Sie im oberen Navigationsmenü **Analysen** > **Übersicht** aus. Auf der Seite **Analyseübersicht** werden standardmäßig Informationen zu den fünf während ihrer Lebensdauer am häufigsten gekauften Apps angezeigt. Um andere Apps auszuwählen und anzuzeigen, wählen Sie **Filter ändern** aus.

## <a name="available-reports-for-each-app"></a>Verfügbare Berichte für die einzelnen Apps

In diesem Abschnitt erhalten Sie Details zu den Informationen, die in den folgenden Berichten enthalten sind:

-   [Bericht „Käufe“](acquisitions-report.md)
-   [Bericht zu Add-On-Käufen](add-on-acquisitions-report.md)
-   [Installationsbericht](installs-report.md)
-   [Nutzungsbericht](usage-report.md)
-   [Integritätsbericht](health-report.md)
-   [Bericht „Bewertungen“](ratings-report.md)
-   [Bericht „Rezensionen“](reviews-report.md)
-   [Feedbackbericht](feedback-report.md)
-   [Bericht zu Kanälen und Abschlüssen](channels-and-conversions-report.md)
-   [Bericht „Anzeigenvermittlung“](ad-mediation-report.md)
-   [Bericht zur Anzeigen-Performance](advertising-performance-report.md)
-   [Bericht zur Partneranzeigen-Performance](affiliates-performance-report.md)
-   [Bewerben Ihres App-Berichts](promote-your-app-report.md)

> [!NOTE]
> Abhängig von den spezifischen Features und der Implementierung Ihrer App enthalten einige dieser Berichte möglicherweise keine Daten.

## <a name="page-and-section-filters"></a>Seitenfilter und Abschnittsfilter

Jeder Bericht enthält Filter, mit denen Sie einen Drilldown auf Ihre Daten ausführen können. Am oberen Seitenrand sehen Sie **Filter anwenden**. Mithilfe dieser Filter können Sie den Umfang aller auf der Seite angezeigten Diagramme und Informationen einschränken oder erweitern.

Innerhalb eines bestimmten Diagramms können auch einzelne Abschnittsfilter angezeigt werden. Durch diese werden die Daten eingeschränkt, die nur für dieses bestimmte Diagramm angezeigt werden.

Die spezifischen Filter variieren je nach Bericht. Die Themen in diesem Abschnitt erläutern, welche Filter verfügbar sind, und beschreiben weitere Daten, die Sie auf der Seite finden.

<span id="no-dashboard"/>
## <a name="access-analytics-data-without-using-the-dev-center-dashboard"></a>Zugreifen auf Analysedaten ohne das Dev Center-Dashboard

Neben den Analyseberichten im Dashboard gibt es weitere Möglichkeiten für den Zugriff auf Analysedaten.

### <a name="windows-store-analytics-api"></a>Windows Store-Analyse-API

Verwenden Sie die [Windows Store-Analyse-API](../monetize/access-analytics-data-using-windows-store-services.md), um programmgesteuert Analysedaten für Ihre Apps abzurufen. Mit dieser REST-API können Sie Daten für App- und Add-On-Käufe, Fehler sowie App-Bewertungen und -Rezensionen abrufen. Diese API verwendet Azure Active Directory (Azure AD), um die Aufrufe von Ihrer App oder Ihrem Dienst zu authentifizieren.

### <a name="windows-dev-center-content-pack-for-power-bi"></a>Windows Dev Center-Inhaltspaket für Power BI

Nutzen Sie das [Windows Dev Center-Inhaltspaket für Power BI](https://powerbi.microsoft.com/documentation/powerbi-content-pack-windows-dev-center/), um mehr über Ihre Dev Center-Analysedaten in Power BI zu erfahren und diese zu überwachen. Power BI ist ein cloudbasierter Geschäftsanalysedienst, der Ihnen Ihre Geschäftsdaten in einer einzelnen Ansicht präsentiert.

Verwenden Sie die folgenden Ressourcen, um mit Power BI auf Ihre Analysedaten zuzugreifen.

* [Registrieren für Power BI](https://powerbi.microsoft.com/documentation/powerbi-service-self-service-signup-for-power-bi/)
* [Informationen zum Verwenden von Power BI](https://powerbi.microsoft.com/guided-learning/)
* [Informationen zum Einsetzen des Windows Dev Center-Inhaltspakets für Power BI, um eine Verbindung zu Ihren Analysedaten herzustellen](https://powerbi.microsoft.com/documentation/powerbi-content-pack-windows-dev-center/)

> [!NOTE]
> Für die Verbindung zum Windows Dev Center-Inhaltspaket für Power BI sollten Sie Anmeldeinformationen aus einem Azure AD-Verzeichnis angeben, das mit Ihrem Dev Center-Konto verknüpft ist. Wenn Sie die Anmeldeinformationen Ihres Microsoft-Kontos verwenden, werden Ihre Analysedaten in Power BI nicht automatisch aktualisiert. Für eine Aktualisierung müssen Sie sich dann in Power BI anmelden. Wenn in Ihrer Organisation bereits mit Office365 oder anderen Unternehmensdiensten von Microsoft gearbeitet wird, verfügen Sie bereits über Azure AD. Andernfalls können Sie es [kostenlos abrufen](http://go.microsoft.com/fwlink/p/?LinkId=703757). Weitere Informationen zur Verknüpfung Ihres Dev Center-Kontos mit Azure AD finden Sie unter [Kontobenutzer verwalten](manage-account-users.md).

### <a name="dev-center-app"></a>DevCenter-App

Installieren Sie die [Dev Center](https://www.microsoft.com/store/apps/dev-center/9nblggh4r5ws)-App, um schnell Details über den Zustand und die Leistung Ihrer Apps auf Windows 10-Geräten anzuzeigen.

## <a name="related-topics"></a>Verwandte Themen
- [Veröffentlichen von Windows-Apps](index.md)
