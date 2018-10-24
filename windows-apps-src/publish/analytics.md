---
author: JnHs
Description: Get detailed analytics for your Windows apps, in the dashboard or via other methods.
title: Analysieren der App-Leistung
ms.assetid: 3A3C6F10-0DB1-416D-B632-CD388EA66759
ms.author: wdg-dev-content
ms.date: 07/17/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Analysen, Berichte, Dashboard, apps, Daten, Metriken
ms.localizationpriority: medium
ms.openlocfilehash: 090ddfdfbed1ae49e87f4dc419765e006913764f
ms.sourcegitcommit: 4b97117d3aff38db89d560502a3c372f12bb6ed5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "5441260"
---
# <a name="analyze-app-performance"></a>Analysieren der App-Leistung

Sie können für Ihre Apps detaillierte Analysen im Windows Dev Center-Dashboard anzeigen. Statistiken und Diagramme geben Aufschluss über den Erfolg Ihrer Apps, z.B. wie viele Kunden Sie erreichen, wie die Kunden Ihre App einsetzen und was die Kunden über die App denken. Außerdem finden Sie dort Metriken zur App-Integrität, zur Anzeigennutzung und mehr.

Zeigen Sie die Analyseberichte im Dashboard an, oder [laden Sie die erforderlichen Berichte herunter](download-analytic-reports.md), um Ihre Daten offline zu analysieren. Wir stellen Ihnen auch verschiedene Möglichkeiten für den [Zugriff auf Analysedaten ohne das Dashboard](#no-dashboard) zur Verfügung.

## <a name="view-key-analytics-for-all-your-apps"></a>Zeigen Sie die wichtigsten Analysen für Ihre gesamten Apps an

Um die wichtigsten Analysen zu den am häufigsten heruntergeladenen Apps anzuzeigen, erweitern Sie **Analyse** und wählen Sie **Übersicht** aus. Auf der Seite „Übersicht” werden standardmäßig Informationen zu den fünf während ihrer Lebensdauer am häufigsten gekauften Apps angezeigt. Um andere veröffentlichte Apps auszuwählen und anzuzeigen, wählen Sie **Filter** aus.

## <a name="view-individual-reports-for-each-app"></a>Zeigen Sie einzelne Berichte für die einzelnen Apps an

In diesem Abschnitt erhalten Sie Details zu den Informationen, die in den folgenden Berichten enthalten sind:

-   [Bericht „Käufe“](acquisitions-report.md)
-   [Bericht zu Add-On-Käufen](add-on-acquisitions-report.md)
-   [Nutzungsbericht](usage-report.md)
-   [Integritätsbericht](health-report.md)
-   [Bericht „Bewertungen“](ratings-report.md)
-   [Bericht „Rezensionen“](reviews-report.md)
-   [Feedbackbericht](feedback-report.md)
-   [Bericht der Xbox Analyse](xbox-analytics-report.md)
-   [Bericht über Geschäftsverlauf](insights-report.md)
-   [Bericht zur Anzeigenleistung](advertising-performance-report.md)
-   [Bericht „Anzeigenkampagne“](promote-your-app-report.md)


> [!NOTE]
> Abhängig von den spezifischen Features und der Implementierung Ihrer App enthalten einige dieser Berichte möglicherweise keine Daten.

<span id="no-dashboard"/>

## <a name="access-analytics-data-without-using-the-dev-center-dashboard"></a>Zugreifen auf Analysedaten ohne das Dev Center-Dashboard

Zusätzlich zur Anzeige der Berichte im Dashboard können Sie auf unterschiedliche Arten auf Ihre App-Analyse zugreifen.

### <a name="microsoft-store-analytics-api"></a>Microsoft Store-Analyse-API

Verwenden Sie die [Store-Analyse-API](../monetize/access-analytics-data-using-windows-store-services.md), um programmgesteuert Analysedaten für Ihre Apps abzurufen. Mit dieser REST-API können Sie Daten für App- und Add-On-Käufe, Fehler sowie App-Bewertungen und -Rezensionen abrufen. Diese API verwendet Azure Active Directory (Azure AD), um die Aufrufe von Ihrer App oder Ihrem Dienst zu authentifizieren.

### <a name="windows-dev-center-content-pack-for-power-bi"></a>Windows Dev Center-Inhaltspaket für Power BI

Nutzen Sie das [Windows Dev Center-Inhaltspaket für Power BI](https://powerbi.microsoft.com/documentation/powerbi-content-pack-windows-dev-center/), um mehr über Ihre Dev Center-Analysedaten in Power BI zu erfahren und diese zu überwachen. Power BI ist ein cloudbasierter Geschäftsanalysedienst, der Ihnen Ihre Geschäftsdaten in einer einzelnen Ansicht präsentiert.

Verwenden Sie die folgenden Ressourcen, um mit Power BI auf Ihre Analysedaten zuzugreifen.

* [Registrieren für Power BI](https://powerbi.microsoft.com/documentation/powerbi-service-self-service-signup-for-power-bi/)
* [Informationen zum Verwenden von Power BI](https://powerbi.microsoft.com/guided-learning/)
* [Informationen zum Einsetzen des Windows Dev Center-Inhaltspakets für Power BI, um eine Verbindung zu Ihren Analysedaten herzustellen](https://powerbi.microsoft.com/documentation/powerbi-content-pack-windows-dev-center/)

> [!NOTE]
> Für die Verbindung zum Windows Dev Center-Inhaltspaket für Power BI sollten Sie Anmeldeinformationen aus einem Azure AD-Verzeichnis angeben, das mit Ihrem Dev Center-Konto verknüpft ist. Wenn Sie die Anmeldeinformationen Ihres Microsoft-Kontos verwenden, werden Ihre Analysedaten in Power BI nicht automatisch aktualisiert. Für eine Aktualisierung müssen Sie sich dann in Power BI anmelden. Wenn in Ihrer Organisation bereits mit Office365 oder anderen Unternehmensdiensten von Microsoft gearbeitet wird, verfügen Sie bereits über Azure AD. Andernfalls können Sie es [kostenlos abrufen](http://go.microsoft.com/fwlink/p/?LinkId=703757). Weitere Informationen zur Einrichtung der Zuordnung finden Sie unter [Zuordnen Ihres Azure Active Directory zum Dev Center-Konto](associate-azure-ad-with-dev-center.md).

### <a name="dev-center-app"></a>DevCenter-App

Installieren Sie die [Dev Center](https://www.microsoft.com/store/apps/dev-center/9nblggh4r5ws)-App, um schnell Details über den Zustand und die Leistung Ihrer Apps auf Windows 10-Geräten anzuzeigen.

