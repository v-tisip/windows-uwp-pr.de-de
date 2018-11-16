---
author: Xansky
description: Mittels dieser Methode in der Microsoft Store-Analyse-API können Sie gesammelte Fehlerberichtsdaten für einen bestimmten Zeitraum und andere optionale Filter abrufen.
title: Abrufen von Fehlerberichtsdaten für Ihre Xbox One Spiel
ms.author: mhopkins
ms.date: 11/06/2018
ms.topic: article
keywords: Windows10, UWP, Store-Dienst, Microsoft Store-Analyse-API, Fehler
ms.localizationpriority: medium
ms.openlocfilehash: 45e494b3e93e2dd6ac23ef1562c32485bf2e7ddb
ms.sourcegitcommit: 9f8010fe67bb3372db1840de9f0be36097ed6258
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "7099957"
---
# <a name="get-error-reporting-data-for-your-xbox-one-game"></a>Abrufen von Fehlerberichtsdaten für Ihre Xbox One Spiel

Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, die gesammelte Fehlerberichtsdaten für Ihre Xbox One Spiel abzurufen, das über das Xbox-Portal (XDP) und im XDP Analytics Partner Center-Dashboard verfügbar ist.

Sie können zusätzliche Fehlerinformationen abrufen, mithilfe der Methoden zum [Abrufen von Details zu einem Fehler in Ihrer Xbox One Spiel](get-details-for-an-error-in-your-xbox-one-game.md)und [Abrufen der stapelüberwachung für einen Fehler in Ihrer Xbox One Spiel](get-the-stack-trace-for-an-error-in-your-xbox-one-game.md) [Herunterladen der CAB-Datei für einen Fehler in Ihrer Xbox One Spiel](download-the-cab-file-for-an-error-in-your-xbox-one-game.md) .

## <a name="prerequisites"></a>Voraussetzungen


Zur Verwendung dieser Methode sind folgende Schritte erforderlich:

* Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.
* [Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird. Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft. Wenn das Token abgelaufen ist, können Sie ein neues abrufen.

## <a name="request"></a>Anforderung


### <a name="request-syntax"></a>Anforderungssyntax

| Methode | Anforderungs-URI                                                          |
|--------|----------------------------------------------------------------------|
| GET    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/xbox/failurehits``` |


### <a name="request-header"></a>Anforderungsheader

| Header        | Typ   | Beschreibung                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| Autorisierung | String | Erforderlich. Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;. |


### <a name="request-parameters"></a>Anforderungsparameter

| Parameter        | Typ   |  Beschreibung      |  Erforderlich  
|---------------|--------|---------------|------|
| applicationId | string | Die Produkt-ID des Xbox One Spiels, für die Fehlerberichtsdaten abgerufen werden. Um die Produkt-ID Ihres Spiels zu erhalten, wechseln Sie zu Ihrem Spiel in der Xbox-Entwickler-Portal (XDP) und rufen Sie die Produkt-ID von der URL ab. Alternativ können ist Sie Ihre integritätsdaten vom Windows Partner Center-Analysebericht herunterladen, die Produkt-ID in der TSV-Datei enthalten. |  Ja  |
| startDate | date | Das Startdatum im Datumsbereich der Fehlerberichtsdaten, die abgerufen werden sollen. Der Standardwert ist das aktuelle Datum. Wenn *aggregationLevel* **day**, **week** oder **month** ist, sollte dieser Parameter ein Datum im Format ```mm/dd/yyyy``` angeben. Wenn *aggregationLevel* **hour** ist, kann dieser Parameter ein Datum im Format ```mm/dd/yyyy``` oder ein Datum und Uhrzeit im Format ```yyyy-mm-dd hh:mm:ss``` angeben.  |  Nein  |
| endDate | date | Das Enddatum im Datumsbereich der Fehlerberichtsdaten, die abgerufen werden sollen. Der Standardwert ist das aktuelle Datum. Wenn *aggregationLevel* **day**, **week** oder **month** ist, sollte dieser Parameter ein Datum im Format ```mm/dd/yyyy``` angeben. Wenn *aggregationLevel* **hour** ist, kann dieser Parameter ein Datum im Format ```mm/dd/yyyy``` oder ein Datum und Uhrzeit im Format ```yyyy-mm-dd hh:mm:ss``` angeben. |  Nein  |
| top | int | Die Anzahl der Datenzeilen, die in der Anforderung zurückgegeben werden sollen. Der Maximal- und Standardwert ist 10.000, wenn nicht anders angegeben. Wenn die Abfrage keine weiteren Zeilen enthält, entält der Antworttext den Link „Weiter“, den Sie verwenden können, um die nächste Seite mit Daten anzufordern. |  Nein  |
| skip | int | Die Anzahl der Zeilen, die in der Abfrage übersprungen werden sollen. Verwenden Sie diesen Parameter, um große Datensätze durchzublättern. Beispielsweise rufen „top=10000“ und „skip=0“ die ersten 10.000Datenzeilen ab, „top=10000“ und „skip=10000“ die nächsten 10.000Datenzeilen usw. |  Nein  |
| filter |string  | Mindestens eine Anweisung, die die Zeilen in der Antwort filtert. Jede Anweisung enthält einen Feldnamen aus dem Antworttext und einen Wert, die mit den Operatoren **eq** oder **ne** verknüpft sind. Anweisungen können mit **and** oder **or** kombiniert werden. Zeichenfolgenwerte im Parameter *filter* müssen von einfachen Anführungszeichen eingeschlossen werden. Sie können die folgenden Felder aus dem Antworttext angeben:<p/><ul><li>**applicationName**</li><li>**failureName**</li><li>**failureHash**</li><li>**symbol**</li><li>**osVersion**</li><li>**osRelease**</li><li>**eventType**</li><li>**market**</li><li>**deviceType**</li><li>**packageName**</li><li>**packageVersion**</li><li>**date**</li></ul> | Nein   |
| aggregationLevel | string | Gibt den Zeitraum an, für den aggregierte Daten abgerufen werden sollen. Dies kann eine der folgenden Zeichenfolgen sein: **hour**, **day**, **week** oder **month**. Wenn keine Angabe erfolgt, lautet der Standardwert **day**. Wenn Sie **week** oder **month** angeben, sind die Werte *failureName* und *failureHash* auf 1000 Buckets begrenzt.<p/><p/>**Hinweis:**&nbsp;&nbsp;Wenn Sie **hour** angeben, können Sie nur die Fehlerdaten der letzten 72 Stunden abrufen. Um Fehler anzurufen, die älter als 72 Stunden sind, geben Sie **day** oder eine der anderen Aggregationsebenen an.  | Nein |
| orderby | string | Eine Anweisung, die die Ergebnisdatenwerte anfordert. Die Syntax lautet *orderby=field [order],field [order],...*, wobei der Parameter *field* eine der folgenden Zeichenfolgen sein kann:<ul><li>**applicationName**</li><li>**failureName**</li><li>**failureHash**</li><li>**symbol**</li><li>**osVersion**</li><li>**osRelease**</li><li>**eventType**</li><li>**market**</li><li>**deviceType**</li><li>**packageName**</li><li>**packageVersion**</li><li>**date**</li></ul><p>Der Parameter *order* ist optional und kann **asc** oder **desc** sein, um die auf- oder absteigende Anordnung der einzelnen Felder anzugeben. Der Standard ist **asc**.</p><p>Dies ist eine Beispielzeichenfolge für *orderby*: *orderby=date,market*</p> |  Nein  |
| groupby | string | Eine Anweisung, die nur auf die angegebenen Felder Datenaggregationen anwendet. Sie können die folgenden Felder angeben:<ul><li>**failureName**</li><li>**failureHash**</li><li>**symbol**</li><li>**osVersion**</li><li>**eventType**</li><li>**market**</li><li>**deviceType**</li><li>**packageName**</li><li>**packageVersion**</li></ul><p>Die zurückgegebenen Datenzeilen enthalten die Felder, die im Parameter *groupby* angegeben sind, sowie die folgenden:</p><ul><li>**date**</li><li>**applicationId**</li><li>**applicationName**</li><li>**deviceCount**</li><li>**eventCount**</li></ul><p>Der Parameter *groupby* kann mit dem Parameter *aggregationLevel* verwendet werden. Beispiel: *&amp;groupby=failureName,market&amp;aggregationLevel=week*</p></p> |  Nein  |


### <a name="request-example"></a>Anforderungsbeispiel

Die folgenden Beispiele zeigen verschiedene Anforderungen für das Abrufen von Xbox One Spiel Fehlerberichtsdaten. Ersetzen Sie den Wert *ApplicationId* durch die Produkt-ID für Ihr Spiel.

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/xbox/failurehits?applicationId=BRRT4NJ9B3D1&startDate=1/1/2015&endDate=2/1/2015&top=10&skip=0 HTTP/1.1
Authorization: Bearer <your access token>

GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/xbox/failurehits?applicationId=BRRT4NJ9B3D1&startDate=8/1/2015&endDate=8/31/2015&skip=0&filter=market eq 'US' and deviceType eq 'Console' HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a>Antwort


### <a name="response-body"></a>Antworttext

| Wert      | Typ    | Beschreibung     |
|------------|---------|--------------|
| Wert      | array   | Ein Array von Objekten, die gesammelte Fehlerberichtsdaten enthalten. Weitere Informationen zu den Daten in den einzelnen Objekten finden Sie unten im Abschnitt [Fehlerwerte](#error-values).     |
| @nextLink  | String  | Wenn weitere Seiten mit Daten vorhanden sind, enthält diese Zeichenfolge einen URI, mit dem Sie die nächste Seite mit Daten anfordern können. Beispielsweise wird dieser Wert zurückgegeben, wenn der Parameter **top** der Anforderung auf 10000 festgelegt ist, es jedoch mehr als 10.000 Zeilen mit Fehlern für die Abfrage gibt. |
| TotalCount | Ganzzahl | Die Gesamtzahl der Zeilen im Datenergebnis für die Abfrage.     |


### <a name="error-values"></a>Fehlerwerte

Elemente im Array *Value* enthalten die folgenden Werte.

| Wert           | Typ    | Beschreibung        |
|-----------------|---------|---------------------|
| date            | string  | Das erste Datum im Datumsbereich für die Fehlerdaten im Format ```yyyy-mm-dd```. Wenn die Anforderung einen einzelnen Tag angibt, ist dieses Datum dieser Wert. Wenn die Anforderung einen längeren Datumsbereich angibt, ist dieser Wert das erste Datum in diesem Datumsbereich. Für Anforderungen, die einen Wert *AggregationLevel* **Stunde**angeben, enthält dieser Wert auch einen Zeitwert im Format ```hh:mm:ss``` in der lokalen Zeitzone in der der Fehler aufgetreten ist.  |
| applicationId   | string  | Die Produkt-ID des Xbox One Spiels, für die Fehlerdaten abgerufen werden soll.   |
| applicationName | String  | Der Anzeigename des Spiels.   |
| failureName     | string  | Der Name des Fehlers, der aus vier Teilen besteht: eine oder mehrere Problemklassen, ein Ausnahme/Fehlerprüfcode, der Name des Image, in dem der Fehler aufgetreten ist, und der zugehörige Funktionsname.  |
| failureHash     | string  | Der eindeutige Bezeichner des Fehlers.   |
| symbol          | string  | Das diesem Fehler zugewiesene Symbol. |
| osVersion       | string  | Die Version des Betriebssystems, auf dem der Fehler aufgetreten ist. Dies ist immer den Wert **Windows 10**.  |
| osRelease       | string  |  Einer der folgenden Zeichenfolgen, die die Windows 10-Betriebssystemversion oder verteilungsring (als ein Subpopulation innerhalb der Betriebssystemversion) angibt, auf dem der Fehler aufgetreten ist.<p/><ul><li><strong>Version1507</strong></li><li><strong>Version1511</strong></li><li><strong>Version1607</strong></li><li><strong>Version1703</strong></li><li><strong>Version1709</strong></li><li><strong>Version1803</strong></li><li><strong>Release Preview</strong></li><li><strong>Insider Fast</strong></li><li><strong>Insider Slow</strong></li></ul><p>Wenn die Betriebssystemversion oder Verteilungsring unbekannt ist, hat dieses Feld den Wert <strong>Unknown</strong>.</p>    |
| eventType       | string  | Eine der folgenden Zeichenfolgen:<ul><li>**crash**</li><li>**hang**</li><li>**Fehler beim Speicher**</li></ul>      |
| market          | string  | Der ISO3166-Ländercode des Gerätemarkts.   |
| deviceType      | string  | Der Typ des Geräts, auf dem der Fehler aufgetreten ist. Dies ist immer den Wert **Konsole**.    |
| packageName     | string  | Der eindeutige Name des Spiels-Paket, das mit diesem Fehler verknüpft ist.      |
| packageVersion  | string  | Die Version des Spiels Pakets, das mit diesem Fehler verknüpft ist.   |
| deviceCount     | Ganzzahl | Die Anzahl der eindeutigen Geräte, die diesem Fehler für die angegebene Aggregationsebene entsprechen.  |
| eventCount      | Ganzzahl | Die Anzahl der Ereignisse, die diesem Fehler für die angegebene Aggregationsebene zugeordnet werden.      |


### <a name="response-example"></a>Antwortbeispiel

Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.

```json
{
  "Value": [
    {
      "date": "2017-03-09",
      "applicationId": "BRRT4NJ9B3D1",
      "applicationName": "Contoso Sports",
      "failureName": "APPLICATION_FAULT_8013150a_StoreWrapper.ni.DLL!70475e55",
      "failureHash": "5a6b2170-1661-ed47-24d7-230fed0077af",
      "symbol": "storewrapper_ni!70475e55",
      "osVersion": "Windows 10",
      "osRelease": "Version 1803",
      "eventType": "crash",
      "market": "US",
      "deviceType": "Console",
      "packageName": "",
      "packageVersion": "0.0.0.0",
      "deviceCount": 0.0,
      "eventCount": 1.0
    }
  ],
  "@nextLink": "failurehits?applicationId=BRRT4NJ9B3D1&aggregationLevel=week&startDate=2017/03/01&endDate=2016/02/01&top=1&skip=1",
  "TotalCount": 21
}

```

## <a name="related-topics"></a>Verwandte Themen

* [Abrufen von Details zu einem Fehler in Ihrer Xbox One-Spiele](get-details-for-an-error-in-your-xbox-one-game.md)
* [Abrufen der stapelüberwachung für einen Fehler in Ihrer Xbox One-Spiele](get-the-stack-trace-for-an-error-in-your-xbox-one-game.md)
* [Herunterladen der CAB-Datei für einen Fehler in Ihrer Xbox One Spiel](download-the-cab-file-for-an-error-in-your-xbox-one-game.md)
* [Zugreifen auf Analysedaten mit MicrosoftStore-Diensten](access-analytics-data-using-windows-store-services.md)
