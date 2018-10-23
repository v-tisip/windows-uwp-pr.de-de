---
author: Xansky
description: Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um aggregierte Add-on-Kaufdaten abrufen.
title: Abrufen von Xbox One Add-on-Käufen
ms.author: mhopkins
ms.date: 10/18/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Store-Dienste, Microsoft Store-Analyse-API, Xbox One Add-on-Käufe
ms.localizationpriority: medium
ms.openlocfilehash: 931cd7b351a122c22a59a3a0bc2975c61dc38aaa
ms.sourcegitcommit: c4d3115348c8b54fcc92aae8e18fdabc3deb301d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2018
ms.locfileid: "5404881"
---
# <a name="get-xbox-one-add-on-acquisitions"></a>Abrufen von Xbox One Add-on-Käufen

Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, die aggregierte Add-on-Kaufdaten im JSON-Format für einen Xbox One Spiel abzurufen, die das über das Xbox-Portal (XDP) und im XDP Analytics Partner Center-Dashboard verfügbar ist.

## <a name="prerequisites"></a>Voraussetzungen

Zur Verwendung dieser Methode sind folgende Schritte erforderlich:

* Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.
* [Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird. Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft. Wenn das Token abgelaufen ist, können Sie ein neues abrufen.

## <a name="request"></a>Anforderung


### <a name="request-syntax"></a>Anforderungssyntax

| Methode | Anforderungs-URI                                                                |
|--------|----------------------------------------------------------------------------|
| GET    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/xbox/addonacquisitions``` |


### <a name="request-header"></a>Anforderungsheader

| Header        | Typ   | Beschreibung          |
|---------------|--------|--------------|
| Autorisierung | String | Erforderlich. Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;. |


### <a name="request-parameters"></a>Anforderungsparameter

Der Parameter *ApplicationId* oder *AddonProductId* ist erforderlich. Um Kaufdaten für alle für die App registrierten Add-Ons abzurufen, geben Sie den Parameter *applicationId* an. Um Kaufdaten für ein einzelnes Add-on abzurufen, geben Sie den *AddonProductId* -Parameter. Wenn Sie beide Parameter angeben, wird der Parameter *applicationId* ignoriert.

| Parameter        | Typ   |  Beschreibung      |  Erforderlich  |
|---------------|--------|---------------|------|
| applicationId | string | Die *"ProductID"* des Xbox One Spiels, für das Sie Kaufdaten abrufen. Zum Abrufen der *"ProductID"* des Spiels, navigieren Sie zu Ihrem Spiel im XDP Analytics-Programm sowie die *"ProductID"* aus der URL. Alternativ können ist Sie Ihre Kaufdaten vom Partner Center-Analysebericht herunterladen, die *"ProductID"* in der TSV-Datei enthalten. |  Ja  |
| addonProductId | string | Die *"ProductID"* des Add-Ons, für die Sie Kaufdaten abrufen möchten.  | Ja  |
| startDate | date | Das Startdatum im Datumsbereich der Add-On-Kaufdaten, die abgerufen werden sollen. Der Standardwert ist das aktuelle Datum. |  Nein  |
| endDate | date | Das Enddatum im Datumsbereich der Add-On-Kaufdaten, die abgerufen werden sollen. Der Standardwert ist das aktuelle Datum. |  Nein  |
| top | int | Die Anzahl der Datenzeilen, die in der Anforderung zurückgegeben werden sollen. Der Maximal- und Standardwert ist 10.000, wenn nicht anders angegeben. Wenn die Abfrage keine weiteren Zeilen enthält, entält der Antworttext den Link „Weiter“, den Sie verwenden können, um die nächste Seite mit Daten anzufordern. |  Nein  |
| skip | int | Die Anzahl der Zeilen, die in der Abfrage übersprungen werden sollen. Verwenden Sie diesen Parameter, um große Datensätze durchzublättern. Beispielsweise rufen „top=10000“ und „skip=0“ die ersten 10.000Datenzeilen ab, „top=10000“ und „skip=10000“ die nächsten 10.000Datenzeilen usw. |  Nein  |
| filter |string  | <p>Mindestens eine Anweisung, die die Zeilen in der Antwort filtert. Jede Anweisung enthält einen Feldnamen aus dem Antworttext und einen Wert, die mit den Operatoren eq oder ne verknüpft sind. Anweisungen können mit and oder or kombiniert werden. Zeichenfolgenwerte im Parameter filter müssen von einfachen Anführungszeichen eingeschlossen werden. Beispiel: filter=market eq 'US' and gender eq 'm'.</p> <p>Sie können die folgenden Felder aus dem Antworttext angeben:</p> <ul><li><strong>acquisitionType</strong></li><li><strong>Alter</strong></li><li><strong>storeClient</strong></li><li><strong>gender</strong></li><li><strong>market</strong></li><li><strong>osVersion</strong></li><li><strong>deviceType</strong></li><li><strong>sandboxId</strong></li></ul>| Nein   |
| aggregationLevel | string | Gibt den Zeitraum an, für den aggregierte Daten abgerufen werden sollen. Dies kann eine der folgenden Zeichenfolgen sein: <strong>day</strong>, <strong>week</strong> oder <strong>month</strong>. Wenn keine Angabe erfolgt, lautet der Standardwert <strong>day</strong>. | Nein |
| orderby | string | Eine Anweisung, die die Ergebnisdatenwerte für die einzelnen Add-On-Käufe anfordert. Die Syntax lautet <em>Orderby = Field [Order], Field [Order],...</em> Der <em>Feld</em> Parameter kann eine der folgenden Zeichenfolgen sein:<ul><li><strong>date</strong></li><li><strong>acquisitionType</strong></li><li><strong>Alter</strong></li><li><strong>storeClient</strong></li><li><strong>gender</strong></li><li><strong>market</strong></li><li><strong>osVersion</strong></li><li><strong>deviceType</strong></li><li><strong>orderName</strong></li></ul><p>Der Parameter <em>order</em> ist optional und kann <strong>asc</strong> oder <strong>desc</strong> sein, um die auf- oder absteigende Anordnung der einzelnen Felder anzugeben. Der Standard ist <strong>asc</strong>.</p><p>Dies ist eine Beispielzeichenfolge für <em>orderby</em>: <em>orderby=date,market</em></p> |  Nein  |
| groupby | string | Eine Anweisung, die nur auf die angegebenen Felder Datenaggregationen anwendet. Sie können die folgenden Felder angeben:<ul><li><strong>date</strong></li><li><strong>applicationName</strong></li><li><strong>addonProductName</strong></li><li><strong>acquisitionType</strong></li><li><strong>Alter</strong></li><li><strong>storeClient</strong></li><li><strong>gender</strong></li><li><strong>market</strong></li><li><strong>osVersion</strong></li><li><strong>deviceType</strong></li><li><strong>paymentInstrumentType</strong></li><li><strong>sandboxId</strong></li><li><strong>xboxTitleIdHex</strong></li></ul><p>Die zurückgegebenen Datenzeilen enthalten die Felder, die im Parameter <em>groupby</em> angegeben sind, sowie die folgenden:</p><ul><li><strong>date</strong></li><li><strong>applicationId</strong></li><li><strong>addonProductId</strong></li><li><strong>acquisitionQuantity</strong></li></ul><p>Der Parameter <em>groupby</em> kann mit dem Parameter <em>aggregationLevel</em> verwendet werden. Zum Beispiel: <em> &amp;Groupby = Alter, Markt&amp;AggregationLevel = Week</em></p> |  Nein  |


### <a name="request-example"></a>Anforderungsbeispiel

Die folgenden Beispiele zeigen verschiedene Anforderungen für das Abrufen von Add-On-Kaufdaten. Ersetzen Sie die Werte *AddonProductId* und *ApplicationId* durch die entsprechende Store-ID für Ihre app oder Ihr Add-on.

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/xbox/addonacquisitions?addonProductId=BRRT4NJ9B3D2&startDate=1/1/2015&endDate=2/1/2015&top=10&skip=0 HTTP/1.1
Authorization: Bearer <your access token>

GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/xbox/addonacquisitions?applicationId=BRRT4NJ9B3D1&startDate=1/1/2015&endDate=2/1/2015&top=10&skip=0 HTTP/1.1
Authorization: Bearer <your access token>

GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/xbox/addonacquisitions?addonProductId=BRRT4NJ9B3D2&startDate=1/1/2015&endDate=7/3/2015&top=100&skip=0&filter=market ne 'US' and gender ne 'Unknown' and gender ne 'm' and market ne 'NO' and age ne '>55' HTTP/1.1
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
| addonProductId      | string  | Die *"ProductID"* des Add-Ons, für das Sie Kaufdaten abrufen.                                                                                                                                                                 |
| addonProductName    | string  | Der Anzeigename des Add-Ons. Dieser Wert wird nur in den Antwortdaten Wenn der Parameter *AggregationLevel* **Tag**, festgelegt ist, wenn Sie das Feld **AddonProductName** im *Groupby* Parameter angeben.                                                                                                                                                                                                            |
| applicationId       | string  | Die *"ProductID"* der app, für die Sie Add-on-Kaufdaten abrufen möchten.                                                                                                                                                           |
| applicationName     | String  | Der Anzeigename des Spiels.                                                                                                                                                                                                             |
| deviceType          | String  | <p>Eine der folgenden Zeichenfolgen, die den Typ des Geräts angibt, mit dem der Kauf getätigt wurde:</p> <ul><li>"PC"</li><li>-Zoll-Smartphone"</li><li>"Konsole"</li><li>"IoT"</li><li>"Server"</li><li>"Tablet"</li><li>"Holographic"</li><li>"Unknown"</li></ul>                                                                                                  |
| storeClient         | string  | <p>Eine der folgenden Zeichenfolgen, die die Version des Store anzeigt, wo der Kauf getätigt wurde:</p> <ul><li>"Windows Phone Store (Client)"</li><li>"Microsoft Store (Client)" (oder "Windows Store (Client)" beim Abfragen von Daten vor dem 23. März 2018)</li><li>"Microsoft Store (Web)" (oder "Windows Store (Web)" beim Abfragen von Daten vor dem 23. März 2018)</li><li>"Volume Purchase by Organizations"</li><li>"Andere"</li></ul>                                                                                            |
| osVersion           | string  | Die Version des Betriebssystems, auf dem der Kauf ausgeführt wurde. Für diese Methode ist dieser Wert immer "Windows 10".                                                                                                   |
| market              | string  | Die ISO 3166-Ländercode des Markts, in dem der Kauf erfolgte.                                                                                                                                                                  |
| gender              | String  | <p>Eine der folgenden Zeichenfolgen, die das Geschlecht des Benutzer angibt, der den Kauf getätigt hat:</p> <ul><li>"m"</li><li>"f"</li><li>"Unknown"</li></ul>                                                                                                    |
| Alter            | String  | <p>Eine der folgenden Zeichenfolgen, die die Altersgruppe des Benutzers anzeigt, der den Kauf getätigt hat:</p> <ul><li>"weniger als 13"</li><li>"13-17"</li><li>"18 bis 24"</li><li>"25-34"</li><li>"35-44"</li><li>"44-55"</li><li>"greater than 55"</li><li>"Unknown"</li></ul>                                                                                                 |
| acquisitionType     | String  | <p>Eine der folgenden Zeichenfolgen, die den Typ des Kaufes angibt:</p> <ul><li>"Kostenlos"</li><li>"Testversion"</li><li>"Auszahlung"</li><li>"Werbecode"</li><li>"Iap"</li><li>"Abonnement Iap"</li><li>"Private Zielgruppe"</li><li>"Vor Reihenfolge"</li><li>"Xbox Game Pass" (oder "Game Pass" beim Abfragen von Daten vor dem 23. März 2018)</li><li>"Disk"</li><li>"Prepaid-Code"</li><li>"In Rechnung gestellt Pre-Reihenfolge"</li><li>"Abgebrochen Pre-Reihenfolge"</li><li>"Konnte nicht vor Reihenfolge"</li></ul>                                                                                                    |
| acquisitionQuantity | Ganzzahl | Die Anzahl der Käufe, die ausgeführt wurden.                        |


### <a name="response-example"></a>Antwortbeispiel

Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.

```json
{
  "Value": [
    {
      "date": "2018-10-18",
      "addonProductId": " BRRT4NJ9B3D2",
      "addonProductName": "Contoso add-on 7",
      "applicationId": "BRRT4NJ9B3D1",
      "applicationName": "Contoso Demo",
      "deviceType": "Console",
      "storeClient": "Windows Phone Store (client)",
      "osVersion": "Windows 10",
      "market": "GB",
      "gender": "m",
      "age": "50orover",
      "acquisitionType": "iap",
      "acquisitionQuantity": 1
    }
  ],
  "@nextLink": "addonacquisitions?applicationId=BRRT4NJ9B3D1&addonProductId=&aggregationLevel=day&startDate=2015/01/01&endDate=2016/02/01&top=1&skip=1",
  "TotalCount": 33677
}
```
