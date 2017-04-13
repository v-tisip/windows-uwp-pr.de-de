---
author: mcleanbyron
ms.assetid: BAC79A64-445D-4702-8E96-7727FF180245
description: "Mittels dieser Methode in der Windows Store-Analyse-API können Sie gesammelte Fehlerberichtsdaten für Windows10-Treiber für einen bestimmten Zeitraum und andere optionale Filter abrufen. Diese Methode ist nur für IHVs bestimmt."
title: "Abrufen von Fehlerberichtsdaten für Windows10-Treiber"
ms.author: mcleans
ms.date: 03/17/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Store-Dienst, Windows Store-Analyse-API, Fehler
ms.openlocfilehash: ea2465feda869a07eef06b57a5ca8b4e04cf99f1
ms.sourcegitcommit: 64cfb79fd27b09d49df99e8c9c46792c884593a7
translationtype: HT
---
# <a name="get-error-reporting-data-for-windows-10-drivers"></a>Abrufen von Fehlerberichtsdaten für Windows10-Treiber

Mittels dieser Methode in der Windows Store-Analyse-API können Sie gesammelte Berichtsdaten für Windows10-Treiberfehler für einen bestimmten Zeitraum und andere optionale Filter abrufen. Sie können zusätzliche Fehlerinformationen mithilfe der Methode zum [Abrufen von Informationen zu einem Windows10-Treiberfehler](get-details-for-a-windows-10-driver-error.md) abrufen.

> [!NOTE]
> Diese Methode kann nur von Entwicklerkonten verwendet werden, die zum [Windows Hardware Dev Center-Programm](https://msdn.microsoft.com/windows/hardware/drivers/dashboard/get-started-with-the-hardware-dashboard) gehören.

## <a name="prerequisites"></a>Voraussetzungen

Zur Verwendung dieser Methode sind folgende Schritte erforderlich:

* Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Windows Store-Analyse-API.
* [Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird. Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft. Wenn das Token abgelaufen ist, können Sie ein neues abrufen.

## <a name="request"></a>Anforderung


### <a name="request-syntax"></a>Anforderungssyntax

| Methode | Anforderungs-URI                                                          |
|--------|----------------------------------------------------------------------|
| GET    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/driver/failurehits``` |

<span/> 

### <a name="request-header"></a>Anforderungsheader

| Header        | Typ   | Beschreibung                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| Autorisierung | String | Erforderlich. Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;. |

<span/> 

### <a name="request-parameters"></a>Anforderungsparameter

| Parameter        | Typ   |  Beschreibung      |  Erforderlich  
|---------------|--------|---------------|------|
| applicationId   | String  | Der Produkt-ID-Wert des Treibers, für den Fehlerdaten abgerufen werden sollen. | Ja  |
| startDate | date | Das Startdatum im Datumsbereich der Fehlerberichtsdaten, die abgerufen werden sollen. Der Standardwert ist das aktuelle Datum. |  Nein  |
| endDate | date | Das Enddatum im Datumsbereich der Fehlerberichtsdaten, die abgerufen werden sollen. Der Standardwert ist das aktuelle Datum. |  Nein  |
| top | int | Die Anzahl der Datenzeilen, die in der Anforderung zurückgegeben werden sollen. Der Maximal- und Standardwert ist 10.000, wenn nicht anders angegeben. Wenn die Abfrage keine weiteren Zeilen enthält, entält der Antworttext den Link „Weiter“, den Sie verwenden können, um die nächste Seite mit Daten anzufordern. |  Nein  |
| skip | int | Die Anzahl der Zeilen, die in der Abfrage übersprungen werden sollen. Verwenden Sie diesen Parameter, um große Datensätze durchzublättern. Beispielsweise rufen „top=10000“ und „skip=0“ die ersten 10.000Datenzeilen ab, „top=10000“ und „skip=10000“ die nächsten 10.000Datenzeilen usw. |  Nein  |
| filter |string  | Mindestens eine Anweisung, die die Zeilen in der Antwort filtert. Jede Anweisung enthält einen Feldnamen aus dem Antworttext und einen Wert, die mit den Operatoren **eq** oder **ne** verknüpft sind. Anweisungen können mit **and** oder **or** kombiniert werden. Zeichenfolgenwerte im Parameter *filter* müssen von einfachen Anführungszeichen eingeschlossen werden. Sie können die folgenden Felder aus dem Antworttext angeben:<p/><ul><li><strong>date</strong></li><li><strong>submissionId</strong></li><li><strong>failureName</strong></li><li><strong>failureHash</strong></li><li><strong>symbol</strong></li><li><strong>osVersion</strong></li><li><strong>osName</strong></li><li><strong>eventType</strong></li><li><strong>market</strong></li><li><strong>deviceType</strong></li><li><strong>driverName</strong></li><li><strong>driverVersion</strong></li><li><strong>oemName</strong></li><li><strong>oemModel</strong></li><li><strong>flightRing</strong></li><li><strong>architecture</strong></li></ul> | Nein   |
| aggregationLevel | string | Gibt den Zeitraum an, für den aggregierte Daten abgerufen werden sollen. Dies kann eine der folgenden Zeichenfolgen sein: <strong>day</strong>, <strong>week</strong> oder <strong>month</strong>. Wenn keine Angabe erfolgt, lautet der Standardwert <strong>day</strong>. Wenn Sie <strong>week</strong> oder <strong>month</strong> angeben, sind die Werte <em>failureName</em> und <em>failureHash</em> auf 1000 Buckets begrenzt. | Nein |
| orderby | string | Eine Anweisung, die die Ergebnisdatenwerte anfordert. Die Syntax ist <em>orderby=field [order],field [order],...</em>. Sie können die folgenden Felder aus dem Antworttext angeben:<p/><ul><li><strong>date</strong></li><li><strong>submissionId</strong></li><li><strong>failureName</strong></li><li><strong>failureHash</strong></li><li><strong>symbol</strong></li><li><strong>osVersion</strong></li><li><strong>osName</strong></li><li><strong>eventType</strong></li><li><strong>market</strong></li><li><strong>deviceType</strong></li><li><strong>driverName</strong></li><li><strong>driverVersion</strong></li><li><strong>oemName</strong></li><li><strong>oemModel</strong></li><li><strong>flightRing</strong></li><li><strong>architecture</strong></li></ul><p>Der Parameter <em>order</em> ist optional und kann <strong>asc</strong> oder <strong>desc</strong> sein, um die auf- oder absteigende Anordnung der einzelnen Felder anzugeben. Der Standard ist <strong>asc</strong>.</p><p>Dies ist eine Beispielzeichenfolge für <em>orderby</em>: <em>orderby=date,market</em></p> |  Nein  |
| groupby | string | Eine Anweisung, die Datenaggregationen nur auf die angegebenen Felder anwendet. Sie können die folgenden Felder aus dem Antworttext angeben:<p/><ul><li><strong>submissionId</strong></li><li><strong>failureName</strong></li><li><strong>failureHash</strong></li><li><strong>symbol</strong></li><li><strong>osVersion</strong></li><li><strong>eventType</strong></li><li><strong>market</strong></li><li><strong>deviceType</strong></li><li><strong>driverName</strong></li><li><strong>driverVersion</strong></li><li><strong>oemName</strong></li><li><strong>oemModel</strong></li><li><strong>flightRing</strong></li><li><strong>architecture</strong></li></ul><p>Die zurückgegebenen Datenzeilen enthalten die Felder, die im Parameter <em>groupby</em> angegeben sind, sowie die folgenden:</p><ul><li><strong>date</strong></li><li><strong>applicationId</strong></li><li><strong>eventCount</strong></li></ul><p>Der Parameter <em>groupby</em> kann mit dem Parameter <em>aggregationLevel</em> verwendet werden. Beispiel: <em>&amp;groupby=failureName,market&amp;aggregationLevel=week</em></p></p> |  Nein  |

<span/>


### <a name="request-example"></a>Anforderungsbeispiel

Die folgenden Beispiele zeigen verschiedene Anforderungen für das Abrufen von Fehlerberichtsdaten für OEM-Hardware.

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/driver/failurehits?applicationId=18430592857500421&startDate=1/1/2015&endDate=2/1/2015&top=10&skip=0 HTTP/1.1
Authorization: Bearer <your access token>

GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/driver/failurehits?applicationId=18430592857500421&startDate=8/1/2015&endDate=8/31/2015&skip=0&filter=market eq 'US' and deviceType eq 'PC' HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a>Antwort


### <a name="response-body"></a>Antworttext

| Wert      | Typ    | Beschreibung     |
|------------|---------|--------------|
| Wert      | array   | Ein Array von Objekten, die gesammelte Fehlerberichtsdaten enthalten. Weitere Informationen zu den Daten in den einzelnen Objekten finden Sie in der folgenden Tabelle.     |
| @nextLink  | String  | Wenn weitere Seiten mit Daten vorhanden sind, enthält diese Zeichenfolge einen URI, mit dem Sie die nächste Seite mit Daten anfordern können. Beispielsweise wird dieser Wert zurückgegeben, wenn der Parameter **top** der Anforderung auf 10000 festgelegt ist, es jedoch mehr als 10.000 Zeilen mit Fehlern für die Abfrage gibt. |
| TotalCount | inumber | Die Gesamtzahl der Zeilen im Datenergebnis für die Abfrage.     |

<span/>

Elemente im Array *Value* enthalten die folgenden Werte.

| Wert           | Typ    | Beschreibung        |
|-----------------|---------|---------------------|
| date            | string  | Das erste Datum im Datumsbereich für die Fehlerdaten. Wenn die Anforderung einen einzelnen Tag angibt, ist dieses Datum dieser Wert. Wenn die Anforderung eine Woche, einen Monat oder einen anderen Datumsbereich angibt, ist dieser Wert das erste Datum in diesem Datumsbereich. |
| applicationId   | String  | Der Produkt-ID-Wert des Treibers, für den Fehlerdaten abgerufen wurden. |
| submissionId   | String  | Die ID der Einreichung, die dem Treiber zugeordnet ist. |
| failureName     | string  | Der Name des Fehlers.  |
| failureHash     | string  | Der eindeutige Bezeichner des Fehlers.   |
| symbol          | string  | Das diesem Fehler zugewiesene Symbol. |
| osVersion       | String  | Die vierteilige Buildversion des Betriebssystems, auf dem der Fehler aufgetreten ist.  |
| osName       | String  | Der Name des Betriebssystems, auf dem der Fehler aufgetreten ist.  |
| eventType       | String  | Der Typ des Fehlers, der aufgetreten ist.      |
| market          | string  | Der ISO3166-Ländercode des Gerätemarkts.   |
| deviceType      | String  | Eine der folgenden Zeichenfolgen, die den Typ des Geräts angibt, auf dem der Fehler aufgetreten ist:<p/><ul><li><strong>PC</strong></li><li><strong>Phone</strong></li><li><strong>Console</strong></li><li><strong>IoT</strong></li><li><strong>Holographic</strong></li><li><strong>Unbekannt</strong></li></ul>    |
| driverName     | String  | Der eindeutige Name des Treibers, der mit diesem Fehler verknüpft ist.      |
| driverVersion  | String  | Die Version des Treibers, der mit diesem Fehler verknüpft ist.   |
| architecture | String |  Die Architektur des Geräts, auf dem der Fehler aufgetreten ist.  |
| oemName | String | Der Name des OEM für das Gerät, auf dem der Fehler aufgetreten ist. |
| oemModel | String | Der Name des Gerätemodells, auf dem der Fehler aufgetreten ist. |
| flightRing | String | Der Name des Test-Flights des Betriebssystems, auf dem der Fehler aufgetreten ist. |
| eventCount      | inumber | Die Anzahl der Ereignisse, die diesem Fehler für die angegebene Aggregationsebene zugeordnet werden.      |

<span/> 

### <a name="response-example"></a>Antwortbeispiel

Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.

```json
{
  "Value": [
    {
      "date": "2017-02-26",
      "submissionId":"29989500_13736592797500435_1152921504626321174",
      "applicationId":"18430592857500421",
      "driverName": "fastboot.sys",
      "osVersion": "10.0.14393.693",
      "osName": "Windows 10",
      "flightRing": "Windows 10 Retail",
      "oemName": "Contoso",
      "oemModel": "C-122",
      "market": "US",
      "symbol": "fastboot",
      "failureName": "AV_fastboot!unknown_function",
      "failureHash": "f060c0b6-fbe6-463f-a9f1-b7ebc1cc722f",
      "architecture": "x64",
      "driverVersion": "2.1.1.0",
      "deviceType": "Unknown",
      "eventType": "System crash",
      "deviceCount": 1.0,
      "eventCount": 1.0
    }]
}
```

## <a name="related-topics"></a>Verwandte Themen

* [Abrufen von Informationen zu einem Windows10-Treiberfehler](get-details-for-a-windows-10-driver-error.md)
* [Herunterladen der CAB-Datei für einen Windows10-Treiberfehler](download-the-cab-file-for-a-windows-10-driver-error.md)
