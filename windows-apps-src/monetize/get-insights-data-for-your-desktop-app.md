---
author: Xansky
description: Verwenden Sie diese Methode in Microsoft Store Analytics API zu Statistikdaten für die Desktop-Anwendung.
title: Abrufen von internen Daten für die Desktopanwendung
ms.author: mhopkins
ms.date: 07/31/2018
ms.topic: article
keywords: Windows 10 Uwp Speicher-Services, Microsoft Store Analytics API Einblicke
ms.localizationpriority: medium
ms.openlocfilehash: 5e1ecdf192f54c0158ce503a58aafb65108b8fdc
ms.sourcegitcommit: cd00bb829306871e5103db481cf224ea7fb613f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5862832"
---
# <a name="get-insights-data-for-your-desktop-application"></a>Abrufen von internen Daten für die Desktopanwendung

Verwenden Sie diese Methode in Microsoft Store Analytics API zu Einsichten Daten bezüglich Zustandsmetriken für eine desktop-Anwendung, die [Windows Desktop-Anwendung](https://docs.microsoft.com/windows/desktop/appxpkg/windows-desktop-application-program)hinzugefügt. Diese Daten werden auch im [Integritätsbericht](https://docs.microsoft.com/windows/desktop/appxpkg/windows-desktop-application-program#health-report) platzsparend im Windows-Entwicklungscenter Dashboard.

## <a name="prerequisites"></a>Voraussetzungen

Zur Verwendung dieser Methode sind folgende Schritte erforderlich:

* Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.
* [Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird. Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft. Wenn das Token abgelaufen ist, können Sie ein neues abrufen.

## <a name="request"></a>Anforderung


### <a name="request-syntax"></a>Anforderungssyntax

| Methode | Anforderungs-URI       |
|--------|----------------------|
| GET    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/desktop/insights``` |


### <a name="request-header"></a>Anforderungsheader

| Header        | Typ   | Beschreibung                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| Autorisierung | String | Erforderlich. Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;. |


### <a name="request-parameters"></a>Anforderungsparameter

| Parameter        | Typ   |  Beschreibung      |  Erforderlich  
|---------------|--------|---------------|------|
| applicationId | string | Die Product ID der desktop-Anwendung Statistikdaten abgerufen werden soll. Um die Produkt-ID einer Desktopanwendung zu erhalten, öffnen Sie einen [Dev Center-Analysebericht für Ihre Desktopanwendung](https://msdn.microsoft.com/library/windows/desktop/mt826504) (z.B. den **Integritätsbericht**) und rufen Sie die Produkt-ID aus der URL ab. Wenn Sie diesen Parameter nicht angeben, enthält der Antworttext Statistikdaten für alle apps für Ihr Konto registriert.  |  Nein  |
| startDate | date | Das Startdatum im Datumsbereich Statistikdaten abrufen. Der Standardwert ist 30Tage vor dem aktuellen Datum. |  Nein  |
| endDate | date | Das Enddatum im Datumsbereich Statistikdaten abrufen. Der Standardwert ist das aktuelle Datum. |  Nein  |
| filter | string  | Mindestens eine Anweisung, die die Zeilen in der Antwort filtert. Jede Anweisung enthält einen Feldnamen aus dem Antworttext und einen Wert, die mit den Operatoren **eq** oder **ne** verknüpft sind. Anweisungen können mit **and** oder **or** kombiniert werden. Zeichenfolgenwerte im Parameter *filter* müssen von einfachen Anführungszeichen eingeschlossen werden. Beispielsweise *Filter = Datentyp Eq "Übernahme"*. <p/><p/>Diese Methode unterstützt derzeit nur Filter **Gesundheit**.  | Nein   |

### <a name="request-example"></a>Anforderungsbeispiel

Das folgende Beispiel veranschaulicht eine Anforderung Einblicke Daten. Ersetzen Sie den Wert *ApplicationId* mit dem entsprechenden Wert für die Desktop-Anwendung.

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/desktop/insights?applicationId=10238467886765136388&startDate=6/1/2018&endDate=6/15/2018&filter=dataType eq 'health' HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a>Antwort

### <a name="response-body"></a>Antworttext

| Wert      | Typ   | Beschreibung                  |
|------------|--------|-------------------------------------------------------|
| Wert      | array  | Ein Array von Objekten, die Statistikdaten für die Anwendung enthalten. Weitere Informationen über die Daten in jedem Objekt finden Sie in Abschnitt [Insight Werte](#insight-values) .                                                                                                                      |
| TotalCount | int    | Die Gesamtzahl der Zeilen im Datenergebnis für die Abfrage.                 |


### <a name="insight-values"></a>Insight-Werte

Elemente im Array *Value* enthalten die folgenden Werte.

| Wert               | Typ   | Beschreibung                           |
|---------------------|--------|-------------------------------------------|
| applicationId       | string | Die Product ID der desktop-Anwendung für die Statistikdaten abgerufen.     |
| insightDate                | string | Das Datum, an dem wir die Änderung einer bestimmten Metrik identifiziert. Dieses Datum stellt das Ende der Woche in dem wir eine beachtliche festgestellt oder eine Woche bevor diese Metrik reduzieren. |
| Datentyp     | string | Eine Zeichenfolge, die allgemein Analysebereich angibt, die diese Erkenntnis informiert. Diese Methode unterstützt derzeit nur **Gesundheit**.    |
| insightDetail          | array | Ein oder mehrere [InsightDetail Werte](#insightdetail-values) , die die Details für aktuelle Insight darstellen.    |


### <a name="insightdetail-values"></a>InsightDetail Werte

| Wert               | Typ   | Beschreibung                           |
|---------------------|--------|-------------------------------------------|
| FactName           | string | Eine Zeichenfolge, die die Metrik angibt, die der aktuellen Insight oder aktuelle Dimension beschrieben. Diese Methode unterstützt derzeit nur den Wert **Trefferanzahl**.  |
| Subdimensionen         | array |  Ein oder mehrere Objekte, die Metrik für die Einsicht beschreiben.   |
| Prozent            | string |  Der Prozentsatz die Metrik über Ihre gesamte Kundenbasis geändert.  |
| DimensionName           | string |  Der Name der Metrik in die aktuelle Dimension beschrieben. Beispiele: **EventType**, **Markt**, **Sicherung**und **PackageVersion**.   |
| DimensionValue              | string | Der Wert der Metrik, die in die aktuelle Dimension beschrieben. Beispielsweise ist **DimensionName** **EventType** **DimensionValue** **abstürzen** oder **hängen**möglicherweise.   |
| FactValue     | string | Der Absolute Wert der Metrik haben die Einblicke erkannt wurde.  |
| Richtung | string |  Die Richtung der Änderung (**positiv** oder **negativ**).   |
| Date              | String |  Das Datum, auf dem wir die Änderung im Zusammenhang mit den aktuellen Einblick oder die aktuelle Dimension identifiziert.   |

### <a name="response-example"></a>Antwortbeispiel

Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.

```json
{
  "Value": [
    {
      "applicationId": "9NBLGGGZ5QDR",
      "insightDate": "2018-06-03T00:00:00",
      "dataType": "health",
      "insightDetail": [
        {
          "FactName": "HitCount",
          "SubDimensions": [
            {
              "FactName:": "HitCount",
              "PercentChange": "21",
              "DimensionValue:": "DE",
              "FactValue": "109",
              "Direction": "Positive",
              "Date": "6/3/2018 12:00:00 AM",
              "DimensionName": "Market"
            }
          ],
          "DimensionValue": "crash",
          "Date": "6/3/2018 12:00:00 AM",
          "DimensionName": "EventType"
        },
        {
          "FactName": "HitCount",
          "SubDimensions": [
            {
              "FactName:": "HitCount",
              "PercentChange": "71",
              "DimensionValue:": "JP",
              "FactValue": "112",
              "Direction": "Positive",
              "Date": "6/3/2018 12:00:00 AM",
              "DimensionName": "Market"
            }
          ],
          "DimensionValue": "hang",
          "Date": "6/3/2018 12:00:00 AM",
          "DimensionName": "EventType"
        },
      ],
      "insightId": "9CY0F3VBT1AS942AFQaeyO0k2zUKfyOhrOHc0036Iwc="
    }
  ],
  "@nextLink": null,
  "TotalCount": 2
}
```

## <a name="related-topics"></a>Verwandte Themen

* [Windows Desktop-Anwendung](https://docs.microsoft.com/windows/desktop/appxpkg/windows-desktop-application-program)
* [Integritätsbericht](https://docs.microsoft.com/windows/desktop/appxpkg/windows-desktop-application-program#health-report)
* [Zugreifen auf Analysedaten mit MicrosoftStore-Diensten](access-analytics-data-using-windows-store-services.md)
