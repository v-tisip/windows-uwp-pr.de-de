---
Description: Get detailed analytics for your Windows apps, in Partner Center or via other methods.
title: Analysieren der App-Leistung
ms.assetid: 3A3C6F10-0DB1-416D-B632-CD388EA66759
ms.date: 10/31/2018
ms.topic: article
keywords: Windows 10, Uwp, Analysen, Berichte, Dashboard, apps, Daten, Metriken
ms.localizationpriority: medium
ms.openlocfilehash: f6a6d79745ec98af2c7f562297092eea3feda659
ms.sourcegitcommit: d7613c791107f74b6a3dc12a372d9de916c0454b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8729675"
---
# <a name="analyze-app-performance"></a>Analysieren der App-Leistung

Sie können detaillierte Analysen für Ihre apps im [Partner Center](https://partner.microsoft.com/dashboard)anzeigen. Statistiken und Diagramme geben Aufschluss über den Erfolg Ihrer Apps, z.B. wie viele Kunden Sie erreichen, wie die Kunden Ihre App einsetzen und was die Kunden über die App denken. Außerdem finden Sie dort Metriken zur App-Integrität, zur Anzeigennutzung und mehr.

Sie können Analyseberichte anzeigen rechts im Partner Center oder [die Berichte herunterladen, die Sie benötigen](download-analytic-reports.md) , um Ihre Daten offline zu analysieren. Wir bieten auch verschiedene Möglichkeiten für Sie für [den Zugriff auf Analysedaten außerhalb von Partner Center](#outside).

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

<span id="outside"/>

## <a name="access-analytics-data-outside-of-partner-center"></a>Zugreifen auf Analysedaten außerhalb von Partner Center

Zusätzlich zur Anzeige der Berichte im Partner Center, können Sie app-Analyse auf andere Weise zugreifen.

### <a name="microsoft-store-analytics-api"></a>Microsoft Store-Analyse-API

Verwenden Sie die [Store-Analyse-API](../monetize/access-analytics-data-using-windows-store-services.md), um programmgesteuert Analysedaten für Ihre Apps abzurufen. Mit dieser REST-API können Sie Daten für App- und Add-On-Käufe, Fehler sowie App-Bewertungen und -Rezensionen abrufen. Diese API verwendet Azure Active Directory (Azure AD), um die Aufrufe von Ihrer App oder Ihrem Dienst zu authentifizieren.

### <a name="windows-dev-center-content-pack-for-power-bi"></a>Windows Dev Center-Inhaltspaket für Power BI

Verwenden Sie das [Windows Dev Center-Inhaltspaket für Power BI](https://powerbi.microsoft.com/documentation/powerbi-content-pack-windows-dev-center/) zu erkunden und Partner Center-Analysedaten in Power BI zu überwachen. Power BI ist ein cloudbasierter Geschäftsanalysedienst, der Ihnen Ihre Geschäftsdaten in einer einzelnen Ansicht präsentiert.

Verwenden Sie die folgenden Ressourcen, um mit Power BI auf Ihre Analysedaten zuzugreifen.

* [Registrieren für Power BI](https://powerbi.microsoft.com/documentation/powerbi-service-self-service-signup-for-power-bi/)
* [Informationen zum Verwenden von Power BI](https://powerbi.microsoft.com/guided-learning/)
* [Informationen zum Einsetzen des Windows Dev Center-Inhaltspakets für Power BI, um eine Verbindung zu Ihren Analysedaten herzustellen](https://powerbi.microsoft.com/documentation/powerbi-content-pack-windows-dev-center/)

> [!NOTE]
> Um das Windows Dev Center-Inhaltspaket für Power BI zu verbinden, wird empfohlen, dass Sie Anmeldeinformationen aus Azure AD-Verzeichnis angeben, die Ihr Partner Center-Konto zugeordnet ist. Wenn Sie die Anmeldeinformationen Ihres Microsoft-Kontos verwenden, werden Ihre Analysedaten in Power BI nicht automatisch aktualisiert. Für eine Aktualisierung müssen Sie sich dann in Power BI anmelden. Wenn in Ihrer Organisation bereits mit Office365 oder anderen Unternehmensdiensten von Microsoft gearbeitet wird, verfügen Sie bereits über Azure AD. Andernfalls können Sie es [kostenlos abrufen](http://go.microsoft.com/fwlink/p/?LinkId=703757). Weitere Informationen zur Einrichtung der Zuordnung finden Sie unter [Ordnen Sie Azure Active Directory mit Ihrem Partner Center-Konto](associate-azure-ad-with-dev-center.md).
