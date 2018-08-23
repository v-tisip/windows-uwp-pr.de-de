---
author: mcleanbyron
description: Verwenden Sie diese Methode in der Microsoft Store Analytics API zum Abrufen von Daten für desktop-Anwendung.
title: Rufen Sie Einblicke in die Daten für desktop-Anwendung
ms.author: mcleans
ms.date: 07/31/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Store Services, Microsoft Store Analytics Insights-API
ms.localizationpriority: medium
ms.openlocfilehash: e7ca6eed40af37276b5b4c98ec7b1b709bdadfb9
ms.sourcegitcommit: 9c79fdab9039ff592edf7984732d300a14e81d92
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/23/2018
ms.locfileid: "2820119"
---
# <a name="get-insights-data-for-your-desktop-application"></a>Rufen Sie Einblicke in die Daten für desktop-Anwendung

Verwenden Sie diese Methode in der Microsoft Store Analytics API zum Abrufen von Einblicke in die Daten mit Health Metriken für eine desktop-Anwendung zusammen, die Sie an der [Windows-Desktop-Anwendung](https://docs.microsoft.com/windows/desktop/appxpkg/windows-desktop-application-program)hinzugefügt haben. Diese Daten werden auch in den [Bericht](https://docs.microsoft.com/windows/desktop/appxpkg/windows-desktop-application-program#health-report) für desktopanwendungen im Windows-Entwicklungscenter Dashboard.

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
| applicationId | string | Die Produkt-ID der desktop Anwendung Einblicke in die Daten abgerufen werden sollen. Um die Produkt-ID einer Desktopanwendung zu erhalten, öffnen Sie einen [Dev Center-Analysebericht für Ihre Desktopanwendung](https://msdn.microsoft.com/library/windows/desktop/mt826504) (z.B. den **Integritätsbericht**) und rufen Sie die Produkt-ID aus der URL ab. Wenn Sie diesen Parameter nicht angeben, wird der Antworttext Einblicke in die Daten für alle apps, die für Ihr Konto registriert enthalten.  |  Nein  |
| startDate | date | Das Startdatum in der Datumsbereich der Daten abgerufen. Der Standardwert ist 30Tage vor dem aktuellen Datum. |  Nein  |
| endDate | date | Das Enddatum im Datumsbereich der Daten abgerufen. Der Standardwert ist das aktuelle Datum. |  Nein  |
| filter | string  | Mindestens eine Anweisung, die die Zeilen in der Antwort filtert. Jede Anweisung enthält einen Feldnamen aus dem Antworttext und einen Wert, die mit den Operatoren **eq** oder **ne** verknüpft sind. Anweisungen können mit **and** oder **or** kombiniert werden. Zeichenfolgenwerte im Parameter *filter* müssen von einfachen Anführungszeichen eingeschlossen werden. Beispielsweise *Filter = DataType-Eq "Erwerb'*. <p/><p/>Diese Methode unterstützt derzeit nur die Filter- **Integrität**.  | Nein   |

### <a name="request-example"></a>Anforderungsbeispiel

Im folgenden Beispiel wird eine Anforderung zum Abrufen von Daten. Ersetzen Sie den Wert des *ApplicationId* , mit dem entsprechenden Wert für die desktop aus.

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/desktop/insights?applicationId=10238467886765136388&startDate=6/1/2018&endDate=6/15/2018&filter=dataType eq 'health' HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a>Antwort

### <a name="response-body"></a>Antworttext

| Wert      | Typ   | Beschreibung                  |
|------------|--------|-------------------------------------------------------|
| Wert      | array  | Ein Array von Objekten, die Daten für die app enthalten. Weitere Informationen zu den Daten in jedem-Objekt finden Sie unter [Einblicke Werte](#insight-values) im Abschnitt weiter unten.                                                                                                                      |
| TotalCount | int    | Die Gesamtzahl der Zeilen im Datenergebnis für die Abfrage.                 |


### <a name="insight-values"></a>Insight Werte

Elemente im Array *Value* enthalten die folgenden Werte.

| Wert               | Typ   | Beschreibung                           |
|---------------------|--------|-------------------------------------------|
| applicationId       | string | Die Produkt-ID der desktop-Anwendung für die Daten werden abgerufen.     |
| insightDate                | string | Das Datum, an dem wir die Änderung in eine bestimmte Metrik identifiziert. Dieses Datum stellt das Ende der Woche, in dem wir eine erhebliche Steigerung erkannt, oder in eine Metrik in der Woche vor, die im Vergleich zu verringern. |
| Datentyp     | string | Eine Zeichenfolge, die den Bereich Allgemein Analytics gibt an, dem diese Erkenntnisse informiert. Diese Methode unterstützt derzeit nur **Integrität**.    |
| insightDetail          | array | Eine oder mehrere [InsightDetail Werte](#insightdetail-values) , die die Details zur aktuellen Erkenntnisse darstellen.    |


### <a name="insightdetail-values"></a>InsightDetail Werte

| Wert               | Typ   | Beschreibung                           |
|---------------------|--------|-------------------------------------------|
| FactName           | string | Eine Zeichenfolge, die die Metrik gibt an, der dem aktuellen Erkenntnisse oder der aktuellen Dimension beschreibt. Diese Methode unterstützt derzeit nur den Wert **HitCount**.  |
| SubDimensions         | array |  Ein oder mehrere Objekte, die eine einzelne Metrik für den Einblick beschreiben.   |
| Änderung            | string |  Der Prozentsatz, den die Metrik über Ihre gesamte Kunden geändert.  |
| DimensionName           | string |  Der Name der Metrik in der aktuellen Dimension beschrieben. Beispiele sind **EventType**, **Land/Ihrer Region**, **DeviceType**und **PackageVersion**.   |
| DimensionValue              | string | Der Wert der Metrik, die in der aktuellen Dimension beschrieben wird. Beispielsweise ist **DimensionName** **EventType**, **DimensionValue** **Absturz** **reagiert**möglicherweise oder.   |
| FactValue     | string | Der Absolute Wert der Metrik auf das Datum, an das die Einblicke erkannt wurde.  |
| Richtung | string |  Die Richtung der Änderung (**positiven** oder **negativen**).   |
| Date              | String |  Das Datum, an dem wir die Änderung im Zusammenhang mit der aktuellen Erkenntnisse oder die aktuelle Dimension identifiziert.   |

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

* [Windows-Desktop-Anwendung](https://docs.microsoft.com/windows/desktop/appxpkg/windows-desktop-application-program)
* [Integritätsbericht](https://docs.microsoft.com/windows/desktop/appxpkg/windows-desktop-application-program#health-report)
* [Zugreifen auf Analysedaten mit MicrosoftStore-Diensten](access-analytics-data-using-windows-store-services.md)
