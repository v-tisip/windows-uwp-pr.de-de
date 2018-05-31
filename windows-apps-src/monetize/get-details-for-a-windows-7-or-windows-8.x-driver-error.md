---
author: mcleanbyron
ms.assetid: 2FBA0B73-17C6-4F25-A79D-63F2F262491A
description: Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um detaillierte Daten zu einem Windows7- oder Windows8.x-Treiberfehler abzurufen. Diese Methode ist nur für IHVs bestimmt.
title: Abrufen von Informationen zu einem Windows7- oder Windows8.x-Treiberfehler
ms.author: mcleans
ms.date: 01/18/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Store-Dienste, Microsoft Store-Analyse-API, Fehler, Details
ms.localizationpriority: medium
ms.openlocfilehash: 84ea23f5989f9b8c6a28b9c355175e28cae7695c
ms.sourcegitcommit: 1773bec0f46906d7b4d71451ba03f47017a87fec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2018
ms.locfileid: "1663920"
---
# <a name="get-details-for-a-windows-7-or-windows-8x-driver-error"></a>Abrufen von Informationen zu einem Windows7- oder Windows8.x-Treiberfehler

Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um detaillierte Daten zu einem spezifischen Windows7-/Windows 8.x-Treiberfehler im JSON-Format zu erhalten. Bevor Sie diese Methode verwenden können, müssen Sie zuerst die Methode zum [Abrufen von Fehlerberichtsdaten für Windows7- und Windows8.x-Treiber](get-error-reporting-data-for-windows-7-and-windows-8.x-drivers.md) verwenden, um die ID des Fehlers abzurufen, zu dem Sie detaillierte Informationen erhalten möchten.

> [!NOTE]
> Diese Methode kann nur von Entwicklerkonten verwendet werden, die zum [Windows Hardware Dev Center-Programm](https://msdn.microsoft.com/windows/hardware/drivers/dashboard/get-started-with-the-hardware-dashboard) gehören.

## <a name="prerequisites"></a>Voraussetzungen


Zur Verwendung dieser Methode sind folgende Schritte erforderlich:

* Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.
* [Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird. Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft. Wenn das Token abgelaufen ist, können Sie ein neues abrufen.
* Rufen Sie die ID des Fehlers ab, zu dem Sie detaillierte Informationen erhalten möchten. Um diese ID zu erhalten, verwenden Sie die Methode zum [Abrufen von Fehlerberichtsdaten für Windows7- und Windows8.x-Treiber](get-error-reporting-data-for-windows-7-and-windows-8.x-drivers.md), und verwenden Sie im Antworttext dieser Methode den Wert **failureHash**.

## <a name="request"></a>Anforderung


### <a name="request-syntax"></a>Anforderungssyntax

| Methode | Anforderungs-URI                                                          |
|--------|----------------------------------------------------------------------|
| GET    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/ihvdriver/failuredetails``` |


### <a name="request-header"></a>Anforderungsheader

| Header        | Typ   | Beschreibung                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| Autorisierung | String | Erforderlich. Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;. |


### <a name="request-parameters"></a>Anforderungsparameter

| Parameter        | Typ   |  Beschreibung      |  Erforderlich  
|---------------|--------|---------------|------|
| failureHash | string | Die eindeutige ID des Fehlers, zu dem Sie detaillierte Informationen erhalten möchten. Um diesen Wert für den Fehler zu erhalten, an dem Sie interessiert sind, verwenden Sie die Methode zum [Abrufen von Fehlerberichtsdaten für OEM-Hardware](get-oem-hardware-error-reporting-data.md), und verwenden Sie im Antworttext dieser Methode den Wert **failureHash**. |  Ja  |
| startDate | date | Das Startdatum im Datumsbereich der detaillierten Fehlerdaten, die abgerufen werden sollen. Der Standardwert ist 30Tage vor dem aktuellen Datum. |  Nein  |
| endDate | date | Das Enddatum im Datumsbereich der detaillierten Fehlerdaten, die abgerufen werden sollen. Der Standardwert ist das aktuelle Datum. |  Nein  |
| top | int | Die Anzahl der Datenzeilen, die in der Anforderung zurückgegeben werden sollen. Der Maximal- und Standardwert ist 10.000, wenn nicht anders angegeben. Wenn die Abfrage keine weiteren Zeilen enthält, entält der Antworttext den Link „Weiter“, den Sie verwenden können, um die nächste Seite mit Daten anzufordern. |  Nein  |
| skip | int | Die Anzahl der Zeilen, die in der Abfrage übersprungen werden sollen. Verwenden Sie diesen Parameter, um große Datensätze durchzublättern. Beispielsweise rufen „top=10“ und „skip=0“ die ersten 10 Datenzeilen ab, „top=10“ und „skip=10“ die nächsten 10Datenzeilen usw. |  Nein  |
| filter | string  | Mindestens eine Anweisung, die die Zeilen in der Antwort filtert. Jede Anweisung enthält einen Feldnamen aus dem Antworttext und einen Wert, die mit den Operatoren **eq** oder **ne** verknüpft sind. Anweisungen können mit **and** oder **or** kombiniert werden. Zeichenfolgenwerte im Parameter *filter* müssen von einfachen Anführungszeichen eingeschlossen werden. Sie können die folgenden Felder aus dem Antworttext angeben:<p/><ul><li><strong>date</strong></li><li><strong>failureName</strong></li><li><strong>failureHash</strong></li><li><strong>symbol</strong></li><li><strong>osVersion</strong></li><li><strong>osName</strong></li><li><strong>eventType</strong></li><li><strong>market</strong></li><li><strong>deviceType</strong></li><li><strong>driverName</strong></li><li><strong>driverVersion</strong></li><li><strong>oemName</strong></li><li><strong>oemModel</strong></li><li><strong>flightRing</strong></li><li><strong>architecture</strong></li><li><strong>cabType</strong></li><li><strong>cabExpirationTime</strong></li></ul> | Nein   |
| orderby | string | Eine Anweisung, die die Ergebnisdatenwerte anfordert. Die Syntax lautet <em>orderby=field [order],field [order],...</em>. Sie können die folgenden Felder vom Antworttext angeben:<p/><ul><li><strong>failureName</strong></li><li><strong>failureHash</strong></li><li><strong>cabType</strong></li><li><strong>cabExpirationTime</strong></li><li><strong>symbol</strong></li><li><strong>osVersion</strong></li><li><strong>osName</strong></li><li><strong>eventType</strong></li><li><strong>market</strong></li><li><strong>deviceType</strong></li><li><strong>driverName</strong></li><li><strong>driverVersion</strong></li><li><strong>oemName</strong></li><li><strong>oemModel</strong></li><li><strong>flightRing</strong></li><li><strong>architecture</strong></li></ul><p>Der Parameter <em>order</em> ist optional und kann <strong>asc</strong> oder <strong>desc</strong> sein, um die auf- oder absteigende Anordnung der einzelnen Felder anzugeben. Der Standard ist <strong>asc</strong>.</p><p>Dies ist eine Beispielzeichenfolge für <em>orderby</em>: <em>orderby=date,market</em></p> |  Nein  |


### <a name="request-example"></a>Anforderungsbeispiel

Die folgenden Beispiele zeigen verschiedene Anforderungen für das Abrufen detaillierter Fehlerdaten.

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/ihvdriver/failuredetails?failureHash=012e33e3-dbc9-b12f-c124-9d9810f05d8b&startDate=2016-11-05&endDate=2016-11-06&top=10&skip=0 HTTP/1.1
Authorization: Bearer <your access token>

GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/ihvdriver/failuredetails?failureHash=012e33e3-dbc9-b12f-c124-9d9810f05d8b&startDate=2016-11-05&endDate=2016-11-06&top=10&skip=0&filter=market eq 'US' and deviceType eq 'PC' HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a>Antwort


### <a name="response-body"></a>Antworttext

| Wert      | Typ    | Beschreibung    |
|------------|---------|------------|
| Wert      | array   | Ein Array von Objekten, die detaillierte Fehlerdaten enthalten. Weitere Informationen zu den Daten in den einzelnen Objekten finden Sie in der folgenden Tabelle.          |
| @nextLink  | String  | Wenn weitere Seiten mit Daten vorhanden sind, enthält diese Zeichenfolge einen URI, mit dem Sie die nächste Seite mit Daten anfordern können. Beispielsweise wird dieser Wert zurückgegeben, wenn der Parameter **top** der Anforderung auf 10 festgelegt ist, es jedoch mehr als 10 Zeilen mit Fehlern für die Abfrage gibt. |
| TotalCount | inumber | Die Gesamtzahl der Zeilen im Datenergebnis für die Abfrage.        |


Elemente im Array *Value* enthalten die folgenden Werte.

| Wert           | Typ    | Beschreibung     |
|-----------------|---------|----------------------------|
| date            | string  | Das erste Datum im Datumsbereich für die Fehlerdaten. Wenn die Anforderung einen einzelnen Tag angibt, ist dieses Datum dieser Wert. Wenn die Anforderung eine Woche, einen Monat oder einen anderen Datumsbereich angibt, ist dieser Wert das erste Datum in diesem Datumsbereich. |
| sellerId   | String  | Der Verkäufer-ID-Wert, der dem Entwicklerkonto zugeordnet ist (dies entspricht dem Wert **Seller ID** in den Einstellungen des Dev Center-Kontos). |
| failureName     | String  | Der Name des Fehlers, der aus vier Teilen besteht: eine oder mehrere Problemklassen, ein Ausnahme/Fehlerprüfcode, der Name des Treibers, in dem der Fehler aufgetreten ist, und der zugehörige Funktionsname.           |
| failureHash     | string  | Der eindeutige Bezeichner des Fehlers.     |
| symbol     | string  | Das diesem Fehler zugewiesene Symbol.     |
| osVersion       | String  | Die vierteilige Buildversion des Betriebssystems, auf dem der Fehler aufgetreten ist.    |
| osName       | String  | Der Name des Betriebssystems, auf dem der Fehler aufgetreten ist.  |
| eventType       | String  | Der Typ des Fehlers, der aufgetreten ist.      |
| market          | string  | Der ISO3166-Ländercode des Gerätemarkts.     |
| deviceType      | string  | Der Typ des Geräts, auf dem der Fehler aufgetreten ist.     |
| driverName     | String  | Der eindeutige Name des Treibers, der mit diesem Fehler verknüpft ist.      |
| driverVersion  | String  | Die Version des Treibers, der mit diesem Fehler verknüpft ist.   |
| architecture | String |  Die Architektur des Geräts, auf dem der Fehler aufgetreten ist.  |
| oemName | String | Der Name des OEM für das Gerät, auf dem der Fehler aufgetreten ist. |
| oemModel | String | Der Name des Gerätemodells, auf dem der Fehler aufgetreten ist. |
| flightRing | String | Der Name des Test-Flights des Betriebssystems, auf dem der Fehler aufgetreten ist. |
| clientDeviceId | String | Die ID des Geräts, auf dem der Fehler aufgetreten ist. |
| cabIdHash         | String  | Die eindeutige ID der CAB-Datei, die mit diesem Fehler verknüpft ist.   |
| cabType         | String  | Der Typ der CAB-Datei.   |
| cabExpirationTime  | string  | Datum und Uhrzeit im Format ISO 8601, an dem/der die CAB-Datei abgelaufen ist und nicht mehr heruntergeladen werden kann.   |


### <a name="response-example"></a>Antwortbeispiel

Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.

```json
{
  "Value": [
    {
      "sellerId": "14313740",
      "architecture": "x64",
      "cabExpirationTime": "2017-06-12 23:51:11",
      "cabIdHash": "cc1797f9-b783-44d4-b0e5-46ae7ca668bc",
      "cabType": "MINI",
      "clientDeviceId": null,
      "date": "2017-03-14 23:51:11",
      "deviceType": "PC",
      "driverName": "fastboot.sys",
      "driverVersion": "2.1.1.0",
      "failureHash": "f060c0b6-fbe6-463f-a9f1-b7ebc1cc722f",
      "failureName": "0x109_18_2_LoadImageNotify",
      "market": "US",
      "oemModel": "C-122",
      "oemName": "Contoso",
      "osName": "Windows 8.1",
      "osVersion": "6.3.9600.9600"
    }]
}
```

## <a name="related-topics"></a>Verwandte Themen

* [Abrufen von Fehlerberichtsdaten für Windows7- und Windows8.x-Treiber](get-error-reporting-data-for-windows-7-and-windows-8.x-drivers.md)
* [Herunterladen der CAB-Datei für einen Windows7- oder Windows8.x-Treiberfehler](download-the-cab-file-for-a-windows-7-or-windows-8.x-driver-error.md)
