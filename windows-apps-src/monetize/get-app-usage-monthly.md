---
author: Xansky
ms.assetid: 4E4CB1E3-D213-4324-91E4-7D4A0EA19C53
description: Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um die monatlichen app-Nutzungsdaten für eines bestimmten Zeitraums und andere optionale Filter abzurufen.
title: Abrufen der monatlichen App-Nutzung
ms.author: mhopkins
ms.date: 08/15/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Store-Dienste, Microsoft Store-Analyse-API, Nutzung
ms.localizationpriority: medium
ms.openlocfilehash: ad45422dea9b0c4335fa3cf67a594f819a60ca9c
ms.sourcegitcommit: 106aec1e59ba41aae2ac00f909b81bf7121a6ef1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2018
ms.locfileid: "4611352"
---
# <a name="get-monthly-app-usage"></a>Abrufen der monatlichen App-Nutzung

Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um aggregierte Nutzungsdaten (mit Ausnahme von Xbox Multiplayer-) im JSON-Format für eine Anwendung während eines bestimmten Zeitraums (letzten 90 Tage nur) und andere optionale Filter abzurufen. Diese Informationen sind auch im [Bericht "Nutzung"](../publish/usage-report.md) im Windows Dev Center-Dashboard verfügbar.

## <a name="prerequisites"></a>Voraussetzungen

Zur Verwendung dieser Methode sind folgende Schritte erforderlich:

* Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.
* [Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird. Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft. Wenn das Token abgelaufen ist, können Sie ein neues abrufen.

## <a name="request"></a>Anforderung

### <a name="request-syntax"></a>Anforderungssyntax

| Methode | Anforderungs-URI                                                                 |
|--------|-----------------------------------------------------------------------------|
| GET    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/usagemonthly``` |


### <a name="request-header"></a>Anforderungsheader

| Header        | Typ   | Beschreibung                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| Autorisierung | String | Erforderlich. Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;. |


### <a name="request-parameters"></a>Anforderungsparameter

| Parameter     | Typ   |  Beschreibung                                                                                                    |  Erforderlich  |
|---------------|--------|-----------------------------------------------------------------------------------------------------------------|------------|
| applicationId | string | Die [Store-ID](in-app-purchases-and-trials.md#store-ids) der App, für die Sie Rezensionsdaten abrufen möchten. |  Ja       |
| startDate     | date   | Das Startdatum im Datumsbereich der Rezensionsdaten, die abgerufen werden sollen. Der Standardwert ist das aktuelle Datum.                   |  Nein        |
| endDate       | date   | Das Enddatum im Datumsbereich der Rezensionsdaten, die abgerufen werden sollen. Der Standardwert ist das aktuelle Datum.                     |  Nein        |
| top           | int    | Die Anzahl der Datenzeilen, die in der Anforderung zurückgegeben werden sollen. Der Maximal- und Standardwert ist 10.000, wenn nicht anders angegeben. Wenn die Abfrage keine weiteren Zeilen enthält, entält der Antworttext den Link „Weiter“, den Sie verwenden können, um die nächste Seite mit Daten anzufordern.                          |  Nein        |
| skip          | int    | Die Anzahl der Zeilen, die in der Abfrage übersprungen werden sollen. Verwenden Sie diesen Parameter, um große Datensätze durchzublättern. Beispielsweise rufen „top=10000“ und „skip=0“ die ersten 10.000Datenzeilen ab, „top=10000“ und „skip=10000“ die nächsten 10.000Datenzeilen usw.                         |  Nein        |  
| filter        |string  | Mindestens eine Anweisung, die die Zeilen in der Antwort filtert. Jede Anweisung enthält einen Feldnamen aus dem Antworttext und einen Wert, die mit den Operatoren eq oder ne verknüpft sind. Anweisungen können mit and oder or kombiniert werden. Zeichenfolgenwerte im Parameter filter müssen von einfachen Anführungszeichen eingeschlossen werden. Sie können die folgenden Felder aus dem Antworttext angeben: <ul><li>**market**</li><li>**deviceType**</li><li>**packageVersion**</li></ul>                                                                                                                                              | Nein         |  
| orderby       | string | Eine Anweisung, die die Ergebnisdatenwerte anfordert. Die Syntax lautet <em>orderby=field [order],field [order],...</em>, wobei der Parameter <em>field</em> eine der folgenden Zeichenfolgen sein kann:<ul><li>**date**</li><li>**applicationId**</li><li>**applicationName**</li><li>**market**</li><li>**packageVersion**</li><li>**deviceType**</li><li>**subscriptionName**</li><li>**monthlySessionCount**</li><li>**engagementDurationMinutes**</li><li>**monthlyActiveUsers**</li><li>**monthlyActiveDevices**</li><li>**monthlyNewUsers**</li><li>**averageDailyActiveUsers**</li><li>**averageDailyActiveDevices**</li></ul><p>Der Parameter <em>order</em> ist optional und kann **asc** oder **desc** sein, um die auf- oder absteigende Anordnung der einzelnen Felder anzugeben. Der Standard ist **asc**.</p><p>Dies ist eine Beispielzeichenfolge für <em>orderby</em>: <em>orderby=date,market</em></p> |  Nein        |
| groupby       | string | Eine Anweisung, die Datenaggregationen nur auf die angegebenen Felder anwendet. Sie können die folgenden Felder aus dem Antworttext angeben:<ul><li>**applicationName**</li><li>**subscriptionName**</li><li>**deviceType**</li><li>**packageVersion**</li><li>**market**</li><li>**date**</li></ul><p>Die zurückgegebenen Datenzeilen enthalten die Felder, die im Parameter <em>groupby</em> angegeben sind, sowie die folgenden:</p><ul><li>**applicationId**</li><li>**subscriptionName**</li><li>**monthlySessionCount**</li><li>**engagementDurationMinutes**</li><li>**monthlyActiveUsers**</li><li>**monthlyActiveDevices**</li><li>**monthlyNewUsers**</li><li>**averageDailyActiveUsers**</li><li>**averageDailyActiveDevices**</li></ul><p>Der Parameter <em>groupby</em> kann mit dem Parameter <em>aggregationLevel</em> verwendet werden. Beispiel: <em>&amp;groupby=ageGroup,market&amp;aggregationLevel=week</em></p> |  Nein        |


### <a name="request-example"></a>Anforderungsbeispiel

Das folgende Beispiel zeigt eine Anforderung zum Abrufen der monatlichen app-Nutzungsdaten. Ersetzen Sie den Wert *applicationId* durch die Store-ID Ihrer App.

```http
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/usagemonthly?applicationId=XXXXXXXXXXXX&startDate=2018-06-01&endDate=2018-07-01 HTTP/1.1  
Authorization: Bearer <your access token>
```

## <a name="response"></a>Antwort


### <a name="response-body"></a>Antworttext

| Wert      | Typ   | Beschreibung                                                                                                                         |
|------------|--------|-------------------------------------------------------------------------------------------------------------------------------------|
| Wert      | array  | Ein Array von Objekten, die aggregierte Nutzungsdaten enthalten. Weitere Informationen zu den Daten in den einzelnen Objekten finden Sie in der folgenden Tabelle. |
| @nextLink  | String | Wenn weitere Seiten mit Daten vorhanden sind, enthält diese Zeichenfolge einen URI, mit dem Sie die nächste Seite mit Daten anfordern können. Beispielsweise wird dieser Wert zurückgegeben, wenn der Parameter **top** der Anforderung auf 10000 festgelegt ist, es jedoch mehr als 10.000 Zeilen mit Rezensionsdaten für die Abfrage gibt.                 |
| TotalCount | int    | Die Gesamtzahl der Zeilen im Datenergebnis für die Abfrage.                                                                          |

 
### <a name="usage-values"></a>Nutzung Werte

Elemente im Array *Value* enthalten die folgenden Werte.

| Wert                     | Typ    | Beschreibung                                                                                 |
|---------------------------|---------|---------------------------------------------------------------------------------------------|
| date                      | string  | Das erste Datum im Datumsbereich für die Nutzungsdaten. Wenn die Anforderung einen einzelnen Tag angibt, ist dieses Datum dieser Wert. Wenn die Anforderung eine Woche, einen Monat oder einen anderen Datumsbereich angibt, ist dieser Wert das erste Datum in diesem Datumsbereich.                          |
| applicationId             | string  | Die Store-ID der app, für die Sie Nutzungsdaten abrufen.                            |
| applicationName           | string  | Der Anzeigename der App.                                                                |
| market                    | string  | Der ISO 3166-Ländercode des Markts, in denen Ihre app an der Kunden verwendet.                   |
| packageVersion            | string  | Die Version des Pakets, in denen Nutzung aufgetreten ist.                                            |
| deviceType                | string  | Eine der folgenden Zeichenfolgen gibt an, dass der Typ des Geräts, in denen Nutzung aufgetreten ist:<ul><li>**PC**</li><li>**Phone**</li><li>**Console**</li><li>**Tablet**</li><li>**IoT**</li><li>**Server**</li><li>**Holographic**</li><li>**Unknown**</li></ul>                                                                                                                           |
| subscriptionName          | String  | Gibt an, ob die Verwendung über Xbox Game Pass befand.                                              |
| monthlySessionCount       | long    | Die Anzahl der benutzersitzungen während dieses Monats.                                              |
| engagementDurationMinutes | doppelt  | Der Minuten, in denen Benutzer aktiv Ihrer App gemessen durch einen bestimmten Zeitraum, wenn die app gestartet wird (Prozessbeginn) und endet bei beendet wird (Prozess End) oder nach einer Zeit der Inaktivität.                               |
| monthlyActiveUsers        | long    | Die Anzahl der Kunden, die mit der app dieses Monats.                                           |
| monthlyActiveDevices      | long    | Die Anzahl der Geräte, die app für einen bestimmten Zeitraum Mal, wenn die app gestartet wird (Prozessbeginn) ausführen und endet, wenn er beendet wird (Prozess End) oder nach einer Zeit der Inaktivität.                                                        |
| monthlyNewUsers           | long    | Die Anzahl der Kunden, die Ihre app zum ersten Mal dieses Monats verwendet.                    |
| averageDailyActiveUsers   | doppelt  | Die durchschnittliche Anzahl der Kunden, die die app täglich.                             |
| averageDailyActiveDevices | doppelt  | Die durchschnittliche Anzahl der Geräte, die von allen Benutzern täglich Interaktion mit Ihrer app verwendet. |


### <a name="response-example"></a>Antwortbeispiel

Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.

```http
{
  "Value": [
    {
      "date": "2018-06-01",
      "applicationId": "XXXXXXXXXXXX",
      "applicationName": "My App",
      "market": "All",
      "packageVersion": "All",
      "deviceType": "All",
      "subscriptionName": "All",
      "monthlySessionCount": 582973,
      "engagementDurationMinutes": 16941418.7,
      "monthlyActiveUsers": 139604,
      "monthlyActiveDevices": 132296,
      "monthlyNewUsers": 88127,
      "averageDailyActiveUsers": 9099.23,
      "averageDailyActiveDevices": 8999.0
    },
    {
      "date": "2018-07-01",
      "applicationId": "XXXXXXXXXXXX",
      "applicationName": "My App",
      "market": "All",
      "packageVersion": "All",
      "deviceType": "All",
      "subscriptionName": "All",
      "monthlySessionCount": 681460,
      "engagementDurationMinutes": 21656645.3,
      "monthlyActiveUsers": 130481,
      "monthlyActiveDevices": 123583,
      "monthlyNewUsers": 78465,
      "averageDailyActiveUsers": 8257.55,
      "averageDailyActiveDevices": 8170.58
    }
  ],
  "@nextLink": null,
  "TotalCount": 2
}
```

## <a name="related-topics"></a>Verwandte Themen

* [Zugreifen auf Analysedaten mit MicrosoftStore-Diensten](access-analytics-data-using-windows-store-services.md)
* [Abrufen von täglichen app ussage](get-app-usage-daily.md)
* [Abrufen von App-Käufen](get-app-acquisitions.md)
* [Abrufen von Add-On-Käufen](get-in-app-acquisitions.md)
* [Abrufen von Fehlerberichtsdaten](get-error-reporting-data.md)
