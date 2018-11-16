---
author: Xansky
ms.assetid: 1599605B-4243-4081-8D14-40F6F7734E25
description: Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um die aggregierten Kaufdaten für ein Add-On während eines bestimmten Zeitraums und andere optionale Filter abzurufen.
title: Abrufen von Add-On-Käufen
ms.author: mhopkins
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Store-Dienste, Microsoft Store-Analyse-API, Add-On-Käufe
ms.localizationpriority: medium
ms.openlocfilehash: 4adb202df2806caeb0dc88469521b0f373886c43
ms.sourcegitcommit: e38b334edb82bf2b1474ba686990f4299b8f59c7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/14/2018
ms.locfileid: "6833273"
---
# <a name="get-add-on-acquisitions"></a>Abrufen von Add-On-Käufen

Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um die aggregierten Kaufdaten für Add-Ons in Ihrer App (im JSON-Format) für eine Anwendung während eines bestimmten Zeitraums und andere optionale Filter abzurufen. Diese Informationen sind auch im [Bericht zu Add-on-Käufen](../publish/add-on-acquisitions-report.md) im Partner Center verfügbar.

## <a name="prerequisites"></a>Voraussetzungen

Zur Verwendung dieser Methode sind folgende Schritte erforderlich:

* Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.
* [Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird. Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft. Wenn das Token abgelaufen ist, können Sie ein neues abrufen.

## <a name="request"></a>Anforderung


### <a name="request-syntax"></a>Anforderungssyntax

| Methode | Anforderungs-URI                                                                |
|--------|----------------------------------------------------------------------------|
| GET    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/inappacquisitions``` |


### <a name="request-header"></a>Anforderungsheader

| Header        | Typ   | Beschreibung          |
|---------------|--------|--------------|
| Autorisierung | String | Erforderlich. Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;. |


### <a name="request-parameters"></a>Anforderungsparameter

Die Parameter *applicationId* oder *inAppProductId* sind erforderlich. Um Kaufdaten für alle für die App registrierten Add-Ons abzurufen, geben Sie den Parameter *applicationId* an. Um Kaufdaten für ein einzelnes für die App registriertes Add-On abzurufen, geben Sie den Parameter *inAppProductId* an. Wenn Sie beide Parameter angeben, wird der Parameter *applicationId* ignoriert.

| Parameter        | Typ   |  Beschreibung      |  Erforderlich  
|---------------|--------|---------------|------|
| applicationId | string | Die [Store-ID](in-app-purchases-and-trials.md#store-ids) der App, für die Sie die Add-On-Kaufdaten abrufen möchten.  |  Ja  |
| inAppProductId | String | Die [Store-ID](in-app-purchases-and-trials.md#store-ids) des Add-On, für das Sie Kaufdaten abrufen möchten.  | Ja  |
| startDate | date | Das Startdatum im Datumsbereich der Add-On-Kaufdaten, die abgerufen werden sollen. Der Standardwert ist das aktuelle Datum. |  Nein  |
| endDate | date | Das Enddatum im Datumsbereich der Add-On-Kaufdaten, die abgerufen werden sollen. Der Standardwert ist das aktuelle Datum. |  Nein  |
| top | int | Die Anzahl der Datenzeilen, die in der Anforderung zurückgegeben werden sollen. Der Maximal- und Standardwert ist 10.000, wenn nicht anders angegeben. Wenn die Abfrage keine weiteren Zeilen enthält, entält der Antworttext den Link „Weiter“, den Sie verwenden können, um die nächste Seite mit Daten anzufordern. |  Nein  |
| skip | int | Die Anzahl der Zeilen, die in der Abfrage übersprungen werden sollen. Verwenden Sie diesen Parameter, um große Datensätze durchzublättern. Beispielsweise rufen „top=10000“ und „skip=0“ die ersten 10.000Datenzeilen ab, „top=10000“ und „skip=10000“ die nächsten 10.000Datenzeilen usw. |  Nein  |
| filter |string  | Mindestens eine Anweisung, die die Zeilen in der Antwort filtert. Weitere Informationen finden Sie unten im Abschnitt [Filterfelder](#filter-fields). | Nein   |
| aggregationLevel | string | Gibt den Zeitraum an, für den aggregierte Daten abgerufen werden sollen. Dies kann eine der folgenden Zeichenfolgen sein: <strong>day</strong>, <strong>week</strong> oder <strong>month</strong>. Wenn keine Angabe erfolgt, lautet der Standardwert <strong>day</strong>. | Nein |
| orderby | string | Eine Anweisung, die die Ergebnisdatenwerte für die einzelnen Add-On-Käufe anfordert. Die Syntax lautet <em>orderby=field [order],field [order],...</em>, wobei der Parameter <em>field</em> eine der folgenden Zeichenfolgen sein kann:<ul><li><strong>date</strong></li><li><strong>acquisitionType</strong></li><li><strong>ageGroup</strong></li><li><strong>storeClient</strong></li><li><strong>gender</strong></li><li><strong>market</strong></li><li><strong>osVersion</strong></li><li><strong>deviceType</strong></li><li><strong>orderName</strong></li></ul><p>Der Parameter <em>order</em> ist optional und kann <strong>asc</strong> oder <strong>desc</strong> sein, um die auf- oder absteigende Anordnung der einzelnen Felder anzugeben. Der Standard ist <strong>asc</strong>.</p><p>Dies ist eine Beispielzeichenfolge für <em>orderby</em>: <em>orderby=date,market</em></p> |  Nein  |
| groupby | string | Eine Anweisung, die nur auf die angegebenen Felder Datenaggregationen anwendet. Sie können die folgenden Felder angeben:<ul><li><strong>date</strong></li><li><strong>applicationName</strong></li><li><strong>inAppProductName</strong></li><li><strong>acquisitionType</strong></li><li><strong>ageGroup</strong></li><li><strong>storeClient</strong></li><li><strong>gender</strong></li><li><strong>market</strong></li><li><strong>osVersion</strong></li><li><strong>deviceType</strong></li><li><strong>orderName</strong></li></ul><p>Die zurückgegebenen Datenzeilen enthalten die Felder, die im Parameter <em>groupby</em> angegeben sind, sowie die folgenden:</p><ul><li><strong>date</strong></li><li><strong>applicationId</strong></li><li><strong>inAppProductId</strong></li><li><strong>acquisitionQuantity</strong></li></ul><p>Der Parameter <em>groupby</em> kann mit dem Parameter <em>aggregationLevel</em> verwendet werden. Beispiel: <em>&amp;groupby=ageGroup,market&amp;aggregationLevel=week</em></p> |  Nein  |


### <a name="filter-fields"></a>Filterfelder

Der Parameter *filter* der Anforderung enthält mindestens eine Anweisung, die die Zeilen in der Antwort filtert. Jede Anweisung enthält ein Feld und einen Wert, das/der mit den Operatoren **eq** oder **ne** verknüpft ist. Anweisungen können mit **and** oder **or** kombiniert werden. Dies sind einige Beispielparameter für *Filter*:

-   *filter=market eq 'US' and gender eq 'm'*
-   *filter=(market ne 'US') and (gender ne 'Unknown') and (gender ne 'm') and (market ne 'NO') and (ageGroup ne 'greater than 55' or ageGroup ne ‘less than 13’)*

Die Liste der unterstützten Felder finden Sie in der folgenden Tabelle. Zeichenfolgenwerte im Parameter *Filter* müssen von einfachen Anführungszeichen eingeschlossen werden.

| Felder        |  Beschreibung        |
|---------------|-----------------|
| acquisitionType | Eine der folgenden Zeichenfolgen:<ul><li><strong>free</strong></li><li><strong>trial</strong></li><li><strong>paid</strong></li><li><strong>promotional code</strong></li><li><strong>iap</strong></li></ul> |
| ageGroup | Eine der folgenden Zeichenfolgen:<ul><li><strong>less than 13</strong></li><li><strong>13-17</strong></li><li><strong>18-24</strong></li><li><strong>25-34</strong></li><li><strong>35-44</strong></li><li><strong>44-55</strong></li><li><strong>greater than 55</strong></li><li><strong>Unknown</strong></li></ul> |
| storeClient | Eine der folgenden Zeichenfolgen:<ul><li><strong>Windows Phone Store (Client)</strong></li><li><strong>Microsoft Store (Client)</strong></li><li><strong>Microsoft Store (Web)</strong></li><li><strong>Volumeneinkauf durch Organisationen</strong></li><li><strong>Other</strong></li></ul> |
| gender | Eine der folgenden Zeichenfolgen:<ul><li><strong>m</strong></li><li><strong>f</strong></li><li><strong>Unknown</strong></li></ul> |
| market | Eine Zeichenfolge, die den ISO 3166-Ländercode des Markts enthält, in dem der Kauf erfolgte. |
| osVersion | Eine der folgenden Zeichenfolgen:<ul><li><strong>Windows Phone 7.5</strong></li><li><strong>Windows Phone 8</strong></li><li><strong>Windows Phone 8.1</strong></li><li><strong>Windows Phone 10</strong></li><li><strong>Windows8</strong></li><li><strong>Windows8.1</strong></li><li><strong>Windows 10</strong></li><li><strong>Unknown</strong></li></ul> |
| deviceType | Eine der folgenden Zeichenfolgen:<ul><li><strong>PC</strong></li><li><strong>Phone</strong></li><li><strong>Console</strong></li><li><strong>IoT</strong></li><li><strong>Holographic</strong></li><li><strong>Unknown</strong></li></ul> |
| orderName | Eine Zeichenfolge, die den Namen der Bestellung für den Werbecode angibt, der für den Kauf des Add-Ons verwendet wurde. (Dies gilt nur, wenn der Benutzer das Add-On durch Einlösen eines Werbecodes erworben hat.) |


### <a name="request-example"></a>Anforderungsbeispiel

Die folgenden Beispiele zeigen verschiedene Anforderungen für das Abrufen von Add-On-Kaufdaten. Ersetzen Sie die Werte *inAppProductId* und *applicationId* durch die entsprechende Store-ID für Ihre App oder Ihr Add-On.

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/inappacquisitions?inAppProductId=9NBLGGGZ5QDR&startDate=1/1/2015&endDate=2/1/2015&top=10&skip=0 HTTP/1.1
Authorization: Bearer <your access token>

GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/inappacquisitions?applicationId=9NBLGGGZ5QDR&startDate=1/1/2015&endDate=2/1/2015&top=10&skip=0 HTTP/1.1
Authorization: Bearer <your access token>

GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/inappacquisitions?inAppProductId=9NBLGGGZ5QDR&startDate=1/1/2015&endDate=7/3/2015&top=100&skip=0&filter=market ne 'US' and gender ne 'Unknown' and gender ne 'm' and market ne 'NO' and ageGroup ne '>55' HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a>Antwort


### <a name="response-body"></a>Antworttext

| Wert      | Typ   | Beschreibung         |
|------------|--------|------------------|
| Wert      | array  | Ein Array von Objekten, die aggregierte Add-On-Kaufdaten enthalten. Weitere Informationen zu den Daten in den einzelnen Objekten finden Sie unten im Abschnitt [Add-On-Kaufwerte](#add-on-acquisition-values).                                                                                                              |
| @nextLink  | String | Wenn weitere Seiten mit Daten vorhanden sind, enthält diese Zeichenfolge einen URI, mit dem Sie die nächste Seite mit Daten anfordern können. Beispielsweise wird dieser Wert zurückgegeben, wenn der Parameter **top** der Anforderung auf 10000 festgelegt ist, es jedoch mehr als 10.000 Zeilen mit Add-On-Kaufdaten für die Abfrage gibt. |
| TotalCount | int    | Die Gesamtzahl der Zeilen im Datenergebnis für die Abfrage.    |


<span id="add-on-acquisition-values" />

### <a name="add-on-acquisition-values"></a>Add-On-Kaufwerte

Elemente im Array *Value* enthalten die folgenden Werte.

| Wert               | Typ    | Beschreibung        |
|---------------------|---------|---------------------|
| date                | string  | Das erste Datum im Datumsbereich für die Kaufdaten. Wenn die Anforderung einen einzelnen Tag angibt, ist dieses Datum dieser Wert. Wenn die Anforderung eine Woche, einen Monat oder einen anderen Datumsbereich angibt, ist dieser Wert das erste Datum in diesem Datumsbereich. |
| inAppProductId      | string  | Die Store-ID des Add-Ons, für das Sie Kaufdaten abrufen.                                                                                                                                                                 |
| inAppProductName    | string  | Der Anzeigename des Add-Ons. Dieser Wert wird in den zurückgegebenen Daten nur angezeigt, wenn der Parameter *aggregationLevel* auf **day** festgelegt ist. Dies gilt nicht, wenn im *groupby*-Parameter das Feld **InAppProductName** angegeben wurde.                                                                                                                                                                                                            |
| applicationId       | string  | Die Store-ID der App, für die Sie die Add-On-Kaufdaten abrufen möchten.                                                                                                                                                           |
| applicationName     | String  | Der Anzeigename der App.                                                                                                                                                                                                             |
| deviceType          | string  | Der Typ des Geräts, auf dem der Kauf ausgeführt wurde. Eine Liste der unterstützten Zeichenfolgen finden Sie oben im Abschnitt [Filterfelder](#filter-fields).                                                                                                  |
| orderName           | string  | Der Name der Bestellung.                                                                                                                                                                                                                   |
| storeClient         | string  | Die Version des Store, in dem der Kauf erfolgte. Eine Liste der unterstützten Zeichenfolgen finden Sie oben im Abschnitt [Filterfelder](#filter-fields).                                                                                            |
| osVersion           | string  | Die Version des Betriebssystems, auf dem der Kauf ausgeführt wurde. Eine Liste der unterstützten Zeichenfolgen finden Sie oben im Abschnitt [Filterfelder](#filter-fields).                                                                                                   |
| market              | string  | Die ISO 3166-Ländercode des Markts, in dem der Kauf erfolgte.                                                                                                                                                                  |
| gender              | string  | Das Geschlecht des Benutzers, der den Kauf ausgeführt hat. Eine Liste der unterstützten Zeichenfolgen finden Sie oben im Abschnitt [Filterfelder](#filter-fields).                                                                                                    |
| ageGroup            | string  | Die Altersgruppe des Benutzers, der den Kauf ausgeführt hat. Eine Liste der unterstützten Zeichenfolgen finden Sie oben im Abschnitt [Filterfelder](#filter-fields).                                                                                                 |
| acquisitionType     | string  | Der Typ des Kaufs (kostenlos, kostenpflichtig usw.). Eine Liste der unterstützten Zeichenfolgen finden Sie oben im Abschnitt [Filterfelder](#filter-fields).                                                                                                    |
| acquisitionQuantity | Ganzzahl | Die Anzahl der Käufe, die ausgeführt wurden.                        |


### <a name="response-example"></a>Antwortbeispiel

Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.

```json
{
  "Value": [
    {
      "date": "2015-01-02",
      "inAppProductId": "9NBLGGH3LHKL",
      "inAppProductName": "Contoso add-on 7",
      "applicationId": "9NBLGGGZ5QDR",
      "applicationName": "Contoso Demo",
      "deviceType": "Phone",
      "orderName": "",
      "storeClient": "Windows Phone Store (client)",
      "osVersion": "Windows Phone 8.1",
      "market": "GB",
      "gender": "m",
      "ageGroup": "50orover",
      "acquisitionType": "iap",
      "acquisitionQuantity": 1
    }
  ],
  "@nextLink": "inappacquisitions?applicationId=9NBLGGGZ5QDR&inAppProductId=&aggregationLevel=day&startDate=2015/01/01&endDate=2016/02/01&top=1&skip=1",
  "TotalCount": 33677
}
```

## <a name="related-topics"></a>Verwandte Themen

* [Bericht zu Add-On-Käufen](../publish/add-on-acquisitions-report.md)
* [Zugreifen auf Analysedaten mit MicrosoftStore-Diensten](access-analytics-data-using-windows-store-services.md)
* [Abrufen von Add-On-Konvertierungen nach Kanal](get-add-on-conversions-by-channel.md)
* [Abrufen von App-Käufen](get-app-acquisitions.md)
* [Abrufen von App-Erwerbstrichterdaten](get-acquisition-funnel-data.md)
* [Abrufen von App-Konvertierungen nach Kanal](get-app-conversions-by-channel.md)

 

 
