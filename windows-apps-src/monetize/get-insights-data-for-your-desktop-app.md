---
author: mcleanbyron
description: Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um Einblicke Daten für Ihre Desktopanwendung zu erhalten.
title: Erhalten Sie Einblicke Daten für Ihre desktop-Anwendung
ms.author: mcleans
ms.date: 07/31/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Store-Dienste, Microsoft Store-Analyse-API, Einblicke
ms.localizationpriority: medium
ms.openlocfilehash: e7ca6eed40af37276b5b4c98ec7b1b709bdadfb9
ms.sourcegitcommit: 4f6dc806229a8226894c55ceb6d6eab391ec8ab6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/20/2018
ms.locfileid: "4088045"
---
# <a name="get-insights-data-for-your-desktop-application"></a>Erhalten Sie Einblicke Daten für Ihre desktop-Anwendung

Verwenden Sie diese Methode in der Microsoft Store-Analyse-API zum Abrufen von Einblicken, die zugehörige Daten auf Health Metrik für eine desktop-Anwendung, die Sie in der [Windows-desktopanwendungsprogramm](https://docs.microsoft.com/windows/desktop/appxpkg/windows-desktop-application-program)hinzugefügt haben. Diese Daten sind auch im [Bericht "Integrität"](https://docs.microsoft.com/windows/desktop/appxpkg/windows-desktop-application-program#health-report) für desktopanwendungen im Windows Dev Center-Dashboard verfügbar.

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
| applicationId | string | Die Produkt-ID der Desktopanwendung, für die Sie Einblicke Daten erhalten möchten. Um die Produkt-ID einer Desktopanwendung zu erhalten, öffnen Sie einen [Dev Center-Analysebericht für Ihre Desktopanwendung](https://msdn.microsoft.com/library/windows/desktop/mt826504) (z.B. den **Integritätsbericht**) und rufen Sie die Produkt-ID aus der URL ab. Wenn Sie diesen Parameter nicht angeben, enthält der Antworttext Einblicke Daten für alle apps, die für Ihr Konto registriert wurden.  |  Nein  |
| startDate | date | Das Startdatum im Datumsbereich der Einblicke Daten, die abgerufen werden sollen. Der Standardwert ist 30Tage vor dem aktuellen Datum. |  Nein  |
| endDate | date | Das Enddatum im Datumsbereich der Einblicke Daten, die abgerufen werden sollen. Der Standardwert ist das aktuelle Datum. |  Nein  |
| filter | string  | Mindestens eine Anweisung, die die Zeilen in der Antwort filtert. Jede Anweisung enthält einen Feldnamen aus dem Antworttext und einen Wert, die mit den Operatoren **eq** oder **ne** verknüpft sind. Anweisungen können mit **and** oder **or** kombiniert werden. Zeichenfolgenwerte im Parameter *filter* müssen von einfachen Anführungszeichen eingeschlossen werden. Beispielsweise *Filter = DataType Eq 'Kauf"*. <p/><p/>Diese Methode unterstützt derzeit nur der Filter- **Integrität**.  | Nein   |

### <a name="request-example"></a>Anforderungsbeispiel

Das folgende Beispiel zeigt eine Anforderung zum Abrufen von Daten Einblicke. Ersetzen Sie den Wert von *ApplicationId* mit den entsprechenden Wert für Ihre desktop-Anwendung.

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/desktop/insights?applicationId=10238467886765136388&startDate=6/1/2018&endDate=6/15/2018&filter=dataType eq 'health' HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a>Antwort

### <a name="response-body"></a>Antworttext

| Wert      | Typ   | Beschreibung                  |
|------------|--------|-------------------------------------------------------|
| Wert      | array  | Ein Array von Objekten, die Einblicke Daten für die app enthalten. Weitere Informationen zu den Daten in den einzelnen Objekten finden Sie weiter unten im Abschnitt [Insight Werte](#insight-values) .                                                                                                                      |
| TotalCount | int    | Die Gesamtzahl der Zeilen im Datenergebnis für die Abfrage.                 |


### <a name="insight-values"></a>Insight-Werte

Elemente im Array *Value* enthalten die folgenden Werte.

| Wert               | Typ   | Beschreibung                           |
|---------------------|--------|-------------------------------------------|
| applicationId       | string | Die Produkt-ID der Desktopanwendung, für die Sie Einblicke Daten abgerufen wurden.     |
| insightDate                | string | Das Datum, an dem wir die Änderung in einer bestimmten Metrik identifiziert. Dieses Datum stellt das Ende der Woche, in dem wir eine erhebliche Erhöhung erkannt, oder in einer Metrik im Vergleich zur vorherigen Woche, verringern. |
| Datentyp     | string | Eine Zeichenfolge, die den Bereich für die allgemeine Analysen gibt an, dem diese Insight informiert. Diese Methode unterstützt derzeit nur **Integrität**.    |
| insightDetail          | array | Eine oder mehrere [InsightDetail Werte](#insightdetail-values) , die die Details für aktuelle Insight darstellen.    |


### <a name="insightdetail-values"></a>InsightDetail Werte

| Wert               | Typ   | Beschreibung                           |
|---------------------|--------|-------------------------------------------|
| FactName           | string | Eine Zeichenfolge, die die Metrik gibt an, die den aktuellen Insight oder die aktuelle Dimension beschreibt. Diese Methode unterstützt derzeit nur den Wert **HitCount**.  |
| SubDimensions         | array |  Ein oder mehrere Objekte, die eine einzelne Metrik für die Einblicke zu beschreiben.   |
| Prozent            | string |  Der Prozentsatz, den die Metrik befindet sich über Ihre gesamte Kundenbasis geändert.  |
| DimensionName           | string |  Der Name des die Metrik befindet sich in der aktuellen Dimension beschrieben. Beispiele sind **EventType**, **Markt**, **Gerätetyp**und **PackageVersion**.   |
| DimensionValue              | string | Der Wert der Metrik, die in der aktuellen Dimension beschrieben wird. Beispielsweise ist **DimensionName** **EventType**, **DimensionValue** **Absturz** oder **Blockade**möglicherweise.   |
| FactValue     | string | Den absoluten Wert der Metrik auf das Datum, an das die Einblicke erkannt wurde.  |
| Richtung | string |  Die Richtung der Änderung (**positiv** oder **negativ**).   |
| Date              | String |  Das Datum, an dem wir die Änderung im Zusammenhang mit der aktuellen Insight oder die aktuelle Dimension identifiziert.   |

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

* [Windows-desktopanwendungsprogramm](https://docs.microsoft.com/windows/desktop/appxpkg/windows-desktop-application-program)
* [Integritätsbericht](https://docs.microsoft.com/windows/desktop/appxpkg/windows-desktop-application-program#health-report)
* [Zugreifen auf Analysedaten mit MicrosoftStore-Diensten](access-analytics-data-using-windows-store-services.md)
