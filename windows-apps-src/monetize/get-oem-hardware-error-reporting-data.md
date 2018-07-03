---
author: mcleanbyron
ms.assetid: AE3E003F-BDEC-438B-A80A-3CE1675B369C
description: Mittels dieser Methode der Microsoft Store-Analyse-API können Sie gesammelte Fehlerberichtsdaten für Hardware für einen bestimmten Zeitraum und andere optionale Filter abrufen. Diese Methode ist nur für OEMs bestimmt.
title: Abrufen von Fehlerberichtsdaten für OEM-Hardware
ms.author: mcleans
ms.date: 06/04/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Store-Dienst, Microsoft Store-Analyse-API, Fehler
ms.localizationpriority: medium
ms.openlocfilehash: f8d7a85a37272eb7046ca1e7f64476f94d9556e2
ms.sourcegitcommit: cd91724c9b81c836af4773df8cd78e9f808a0bb4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2018
ms.locfileid: "1989454"
---
# <a name="get-oem-hardware-error-reporting-data"></a>Abrufen von Fehlerberichtsdaten für OEM-Hardware

Mittels dieser Methode in der Microsoft Store-Analyse-API können Sie gesammelte Berichtsdaten für OEM-Hardwarefehler für einen bestimmten Zeitraum und andere optionale Filter abrufen. Sie können zusätzliche Fehlerinformationen abrufen, indem Sie die Methode zum [Abrufen von Informationen zu einem OEM-Hardwarefehler](get-details-for-an-oem-hardware-error.md) verwenden.

> [!NOTE]
> Diese Methode kann nur von Entwicklerkonten verwendet werden, die zum [Windows Hardware Dev Center-Programm](https://msdn.microsoft.com/windows/hardware/drivers/dashboard/get-started-with-the-hardware-dashboard) gehören.

## <a name="prerequisites"></a>Voraussetzungen

Zur Verwendung dieser Methode sind folgende Schritte erforderlich:

* Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.
* [Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird. Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft. Wenn das Token abgelaufen ist, können Sie ein neues abrufen.

## <a name="request"></a>Anforderung


### <a name="request-syntax"></a>Anforderungssyntax

| Methode | Anforderungs-URI                                                          |
|--------|----------------------------------------------------------------------|
| GET    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/hardware/failurehits``` |

<span/> 

### <a name="request-header"></a>Anforderungsheader

| Header        | Typ   | Beschreibung                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| Autorisierung | String | Erforderlich. Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;. |

<span/> 

### <a name="request-parameters"></a>Anforderungsparameter

| Parameter        | Typ   |  Beschreibung      |  Erforderlich  
|---------------|--------|---------------|------|
| startDate | date | Das Startdatum im Datumsbereich der Fehlerberichtsdaten, die abgerufen werden sollen. Der Standardwert ist das aktuelle Datum. |  Nein  |
| endDate | date | Das Enddatum im Datumsbereich der Fehlerberichtsdaten, die abgerufen werden sollen. Der Standardwert ist das aktuelle Datum. |  Nein  |
| top | int | Die Anzahl der Datenzeilen, die in der Anforderung zurückgegeben werden sollen. Der Maximal- und Standardwert ist 10.000, wenn nicht anders angegeben. Wenn die Abfrage keine weiteren Zeilen enthält, entält der Antworttext den Link „Weiter“, den Sie verwenden können, um die nächste Seite mit Daten anzufordern. |  Nein  |
| skip | int | Die Anzahl der Zeilen, die in der Abfrage übersprungen werden sollen. Verwenden Sie diesen Parameter, um große Datensätze durchzublättern. Beispielsweise rufen „top=10000“ und „skip=0“ die ersten 10.000Datenzeilen ab, „top=10000“ und „skip=10000“ die nächsten 10.000Datenzeilen usw. |  Nein  |
| filter |string  | Mindestens eine Anweisung, die die Zeilen in der Antwort filtert. Jede Anweisung enthält einen Feldnamen aus dem Antworttext und einen Wert, die mit den Operatoren **eq** oder **ne** verknüpft sind. Anweisungen können mit **and** oder **or** kombiniert werden. Zeichenfolgenwerte im Parameter *filter* müssen von einfachen Anführungszeichen eingeschlossen werden. Sie können die folgenden Felder angeben:<p/><ul><li><strong>failureName</strong></li><li><strong>failureHash</strong></li><li><strong>symbol</strong></li><li><strong>osVersion</strong></li><li><strong>eventType</strong></li><li><strong>market</strong></li><li><strong>deviceType</strong></li><li><strong>moduleName</strong></li><li><strong>moduleVersion</strong></li><li><strong>mode</strong></li><li><strong>architecture</strong></li><li><strong>model</strong></li><li><strong>baseboard</strong></li><li><strong>modelFamily</strong></li><li><strong>flightRing</strong></li></ul> | Nein   |
| aggregationLevel | string | Gibt den Zeitraum an, für den aggregierte Daten abgerufen werden sollen. Dies kann eine der folgenden Zeichenfolgen sein: <strong>day</strong>, <strong>week</strong> oder <strong>month</strong>. Wenn keine Angabe erfolgt, lautet der Standardwert <strong>day</strong>. Wenn Sie <strong>week</strong> oder <strong>month</strong> angeben, sind die Werte <em>failureName</em> und <em>failureHash</em> auf 1000 Buckets begrenzt. | Nein |
| orderby | string | Eine Anweisung, die die Ergebnisdatenwerte anfordert. Die Syntax lautet <em>orderby=field [order],field [order],...</em>. Sie können die folgenden Felder vom Antworttext angeben:<p/><ul><li><strong>date</strong></li><li><strong>failureName</strong></li><li><strong>failureHash</strong></li><li><strong>symbol</strong></li><li><strong>osVersion</strong></li><li><strong>eventType</strong></li><li><strong>market</strong></li><li><strong>deviceType</strong></li><li><strong>moduleName</strong></li><li><strong>moduleVersion</strong></li><li><strong>mode</strong></li><li><strong>architecture</strong></li><li><strong>model</strong></li><li><strong>baseboard</strong></li><li><strong>modelFamily</strong></li><li><strong>flightRing</strong></li></ul><p>Der Parameter <em>order</em> ist optional und kann <strong>asc</strong> oder <strong>desc</strong> sein, um die auf- oder absteigende Anordnung der einzelnen Felder anzugeben. Der Standard ist <strong>asc</strong>.</p><p>Dies ist eine Beispielzeichenfolge für <em>orderby</em>: <em>orderby=date,market</em></p> |  Nein  |
| groupby | string | Eine Anweisung, die Datenaggregationen nur auf die angegebenen Felder anwendet. Sie können die folgenden Felder aus dem Antworttext angeben:<p/><ul><li><strong>failureName</strong></li><li><strong>failureHash</strong></li><li><strong>symbol</strong></li><li><strong>osVersion</strong></li><li><strong>eventType</strong></li><li><strong>market</strong></li><li><strong>deviceType</strong></li><li><strong>moduleName</strong></li><li><strong>moduleVersion</strong></li><li><strong>mode</strong></li><li><strong>architecture</strong></li><li><strong>model</strong></li><li><strong>baseboard</strong></li><li><strong>modelFamily</strong></li><li><strong>flightRing</strong></li></ul><p>Die zurückgegebenen Datenzeilen enthalten die Felder, die im Parameter <em>groupby</em> angegeben sind, sowie die folgenden:</p><ul><li><strong>date</strong></li><li><strong>eventCount</strong></li></ul><p>Der Parameter <em>groupby</em> kann mit dem Parameter <em>aggregationLevel</em> verwendet werden. Beispiel: <em>&amp;groupby=failureName,market&amp;aggregationLevel=week</em></p></p> |  Nein  |

<span/>


### <a name="request-example"></a>Anforderungsbeispiel

Die folgenden Beispiele zeigen verschiedene Anforderungen für das Abrufen von Fehlerberichtsdaten für OEM-Hardware.

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/hardware/failurehits?startDate=1/1/2015&endDate=2/1/2015&top=10&skip=0 HTTP/1.1
Authorization: Bearer <your access token>

GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/hardware/failurehits?startDate=8/1/2015&endDate=8/31/2015&skip=0&filter=market eq 'US' and deviceType eq 'PC' HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a>Antwort


### <a name="response-body"></a>Antworttext

| Wert      | Typ    | Beschreibung     |
|------------|---------|--------------|
| Wert      | array   | Ein Array von Objekten, die gesammelte Fehlerberichtsdaten enthalten. Weitere Informationen zu den Daten in den einzelnen Objekten finden Sie in der folgenden Tabelle.     |
| @nextLink  | String  | Wenn weitere Seiten mit Daten vorhanden sind, enthält diese Zeichenfolge einen URI, mit dem Sie die nächste Seite mit Daten anfordern können. Beispielsweise wird dieser Wert zurückgegeben, wenn der Parameter **top** der Anforderung auf 10000 festgelegt ist, es jedoch mehr als 10.000 Zeilen mit Fehlern für die Abfrage gibt. |
| TotalCount | Ganzzahl | Die Gesamtzahl der Zeilen im Datenergebnis für die Abfrage.     |

<span/>

Elemente im Array *Value* enthalten die folgenden Werte.

| Wert           | Typ    | Beschreibung        |
|-----------------|---------|---------------------|
| date            | string  | Das erste Datum im Datumsbereich für die Fehlerdaten. Wenn die Anforderung einen einzelnen Tag angibt, ist dieses Datum dieser Wert. Wenn die Anforderung eine Woche, einen Monat oder einen anderen Datumsbereich angibt, ist dieser Wert das erste Datum in diesem Datumsbereich. |
| sellerId   | String  | Der Verkäufer-ID-Wert, der dem Entwicklerkonto zugeordnet ist (dies entspricht dem Wert **Seller ID** in den Einstellungen des Dev Center-Kontos). |
| failureName     | String  | Der Name des Fehlers, der aus vier Teilen besteht: eine oder mehrere Problemklassen, ein Ausnahme/Fehlerprüfcode, der Name des Image/Treibers, in dem der Fehler aufgetreten ist, und der zugehörige Funktionsname.  |
| failureHash     | string  | Der eindeutige Bezeichner des Fehlers.   |
| symbol          | string  | Das diesem Fehler zugewiesene Symbol. |
| osVersion       | String  | Die vierteilige Buildversion des Betriebssystems, auf dem der Fehler aufgetreten ist.  |
| eventType       | String  | Der Typ des Fehlers, der aufgetreten ist.       |
| market          | string  | Der ISO3166-Ländercode des Gerätemarkts.   |
| deviceType      | String  | Eine der folgenden Zeichenfolgen, die den Typ des Geräts angibt, auf dem der Fehler aufgetreten ist:<p/><ul><li><strong>PC</strong></li><li><strong>Phone</strong></li><li><strong>Console</strong></li><li><strong>IoT</strong></li><li><strong>Holographic</strong></li><li><strong>Unbekannt</strong></li></ul>    |
| moduleName     | String  | Der eindeutige Name des Moduls, das mit diesem Fehler verknüpft ist.      |
| moduleVersion  | String  | Die Version des Moduls, das mit diesem Fehler verknüpft ist.   |
| architecture | String |  Die Architektur des Geräts, auf dem der Fehler aufgetreten ist.  |
| model | String | Der Name des Gerätemodells, auf dem der Fehler aufgetreten ist. |
| baseboard | String | Der Name des Gerätebaseboards, auf dem der Fehler aufgetreten ist. |
| modelFamily | String | Der Name der Familie des Gerätemodells, auf dem der Fehler aufgetreten ist. |
| flightRing | String | Der Name des Test-Flights des Betriebssystems, auf dem der Fehler aufgetreten ist. |
| mode | String | Dieser Wert ist immer *kernel*. |
| eventCount      | Ganzzahl | Die Anzahl der Ereignisse, die diesem Fehler für die angegebene Aggregationsebene zugeordnet werden.      |

<span/> 

### <a name="response-example"></a>Antwortbeispiel

Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.

```json
{
  "Value": [
    {
      "date": "2017-02-18",
      "sellerId": "14313740",
      "mode": "Kernel",
      "failureName": "AV_wfplwfs!L2802_3ParseMacHeader",
      "failureHash": "f060c0b6-fbe6-463f-a9f1-b7ebc1cc722f",
      "symbol": "wfplwfs!L2802_3ParseMacHeader",
      "osVersion": "10.0.14393.0",
      "eventType": "System crash",
      "market": "US",
      "deviceType": "PC",
      "moduleName": "wfplwfs.sys",
      "moduleVersion": "10.0.14393.0",
      "architecture": "x64",
      "model": "Unknown",
      "baseboard": "Unknown",
      "modelFamily": "ContosoPad",
      "flightRing": "Windows 10 Retail",
      "eventCount": 2.0
    }]
}
```

## <a name="related-topics"></a>Verwandte Themen

* [Abrufen von Informationen zu einem OEM-Hardwarefehler](get-details-for-an-oem-hardware-error.md)
* [Herunterladen der CAB-Datei für einen OEM-Hardwarefehler](download-the-cab-file-for-an-oem-hardware-error.md)
