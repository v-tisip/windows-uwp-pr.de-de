---
author: Xansky
description: Mittels dieser Methode in der Microsoft Store-Analyse-API können Sie gesammelte Fehlerberichtsdaten für eine Desktopanwendung für einen bestimmten Zeitraum und andere optionale Filter abrufen.
title: Abrufen von Fehlerberichtsdaten für Ihre Desktopanwendung
ms.author: mhopkins
ms.date: 09/04/2018
ms.topic: article
keywords: Windows10, UWP, Store-Dienste, Microsoft Store-Analyse-API, Fehler, Desktopanwendung
ms.localizationpriority: medium
ms.openlocfilehash: eb0081024f59af5180f5018664934277e7fad835
ms.sourcegitcommit: 3257416aebb5a7b1515e107866806f8bd57845a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2018
ms.locfileid: "7161170"
---
# <a name="get-error-reporting-data-for-your-desktop-application"></a>Abrufen von Fehlerberichtsdaten für Ihre Desktopanwendung

Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um gesammelte Fehlerberichtsdaten für eine Desktopanwendung abzurufen, die Sie dem [Windows-Desktopanwendungsprogramm](https://msdn.microsoft.com/library/windows/desktop/mt826504) hinzugefügt haben. Diese Methode kann nur mit Fehlern abrufen, die in den letzten 30 Tagen aufgetreten ist. Diese Informationen sind auch im [Bericht "Integrität"](https://msdn.microsoft.com/library/windows/desktop/mt826504) für desktopanwendungen im Partner Center verfügbar.

## <a name="prerequisites"></a>Voraussetzungen

Zur Verwendung dieser Methode sind folgende Schritte erforderlich:

* Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.
* [Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird. Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft. Wenn das Token abgelaufen ist, können Sie ein neues abrufen.

## <a name="request"></a>Anforderung


### <a name="request-syntax"></a>Anforderungssyntax

| Methode | Anforderungs-URI                                                          |
|--------|----------------------------------------------------------------------|
| GET    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/desktop/failurehits``` |


### <a name="request-header"></a>Anforderungsheader

| Header        | Typ   | Beschreibung                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| Autorisierung | String | Erforderlich. Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;. |


### <a name="request-parameters"></a>Anforderungsparameter

| Parameter        | Typ   |  Beschreibung      |  Erforderlich  
|---------------|--------|---------------|------|
| applicationId | string | Die Produkt-ID der Desktopanwendung, für die Fehlerberichtsdaten abgerufen werden sollen. Um die Produkt-ID einer desktop-Anwendung zu erhalten, öffnen Sie alle [-Analysebericht für Ihre desktop-Anwendung im Partner Center](https://msdn.microsoft.com/library/windows/desktop/mt826504) (z. B. den **Bericht "Integrität"**), und rufen Sie die Produkt-ID aus der URL. |  Ja  |
| startDate | date | Das Startdatum im Datumsbereich der Fehlerberichtsdaten, die abgerufen werden sollen, im Format ```mm/dd/yyyy```. Der Standardwert ist das aktuelle Datum.<p/><p/>**Hinweis:**&nbsp;&nbsp;diese Methode kann nur in den letzten 30 Tagen aufgetretenen Fehler abrufen.  |  Nein  |
| endDate | date | Das Enddatum im Datumsbereich der Fehlerberichtsdaten, die abgerufen werden sollen, im Format ```mm/dd/yyyy```. Der Standardwert ist das aktuelle Datum.   |  Nein  |
| top | int | Die Anzahl der Datenzeilen, die in der Anforderung zurückgegeben werden sollen. Der Maximal- und Standardwert ist 10.000, wenn nicht anders angegeben. Wenn die Abfrage keine weiteren Zeilen enthält, entält der Antworttext den Link „Weiter“, den Sie verwenden können, um die nächste Seite mit Daten anzufordern. |  Nein  |
| skip | int | Die Anzahl der Zeilen, die in der Abfrage übersprungen werden sollen. Verwenden Sie diesen Parameter, um große Datensätze durchzublättern. Beispielsweise rufen „top=10000“ und „skip=0“ die ersten 10.000Datenzeilen ab, „top=10000“ und „skip=10000“ die nächsten 10.000Datenzeilen usw. |  Nein  |
| filter |string  | Mindestens eine Anweisung, die die Zeilen in der Antwort filtert. Jede Anweisung enthält einen Feldnamen aus dem Antworttext und einen Wert, die mit den Operatoren **eq** oder **ne** verknüpft sind. Anweisungen können mit **and** oder **or** kombiniert werden. Zeichenfolgenwerte im Parameter *filter* müssen von einfachen Anführungszeichen eingeschlossen werden. Sie können die folgenden Felder aus dem Antworttext angeben:<p/><ul><li><strong>fileName</strong></li><li><strong>applicationVersion</strong></li><li><strong>failureName</strong></li><li><strong>failureHash</strong></li><li><strong>symbol</strong></li><li><strong>osVersion</strong></li><li><strong>osBuild</strong></li><li><strong>osRelease</strong></li><li><strong>eventType</strong></li><li><strong>market</strong></li><li><strong>deviceType</strong></li><li><strong>productName</strong></li><li><strong>date</strong></li></ul> | Nein   |
| aggregationLevel | string | Gibt den Zeitraum an, für den aggregierte Daten abgerufen werden sollen. Dies kann eine der folgenden Zeichenfolgen sein: **day**, **week** oder **month**. Wenn keine Angabe erfolgt, lautet der Standardwert **day**. Wenn Sie **week** oder **month** angeben, sind die Werte *failureName* und *failureHash* auf 1000 Buckets begrenzt.<p/>  | Nein |
| orderby | string | Eine Anweisung, die die Ergebnisdatenwerte anfordert. Die Syntax lautet *orderby=field [order],field [order],...*, wobei der Parameter *field* eine der folgenden Zeichenfolgen sein kann:<ul><li><strong>fileName</strong></li><li><strong>applicationVersion</strong></li><li><strong>failureName</strong></li><li><strong>failureHash</strong></li><li><strong>symbol</strong></li><li><strong>osVersion</strong></li><li><strong>osBuild</strong></li><li><strong>osRelease</strong></li><li><strong>eventType</strong></li><li><strong>market</strong></li><li><strong>deviceType</strong></li><li><strong>productName</strong></li><li><strong>date</strong></li></ul>Der Parameter *order* ist optional und kann **asc** oder **desc** sein, um die auf- oder absteigende Anordnung der einzelnen Felder anzugeben. Der Standard ist **asc**.</p><p>Dies ist eine Beispielzeichenfolge für *orderby*: *orderby=date,market*</p> |  Nein  |
| groupby | string | Eine Anweisung, die nur auf die angegebenen Felder Datenaggregationen anwendet. Sie können die folgenden Felder angeben:<ul><li>**failureName**</li><li>**failureHash**</li><li>**symbol**</li><li>**osVersion**</li><li>**eventType**</li><li>**market**</li><li>**deviceType**</li></ul><p>Die zurückgegebenen Datenzeilen enthalten die Felder, die im Parameter *groupby* angegeben sind, sowie die folgenden:</p><ul><li>**date**</li><li>**applicationId**</li><li>**applicationName**</li><li>**eventCount**</li></ul><p>Der Parameter *groupby* kann mit dem Parameter *aggregationLevel* verwendet werden. Beispiel: *&amp;groupby=failureName,market&amp;aggregationLevel=week*</p></p> |  Nein  |


### <a name="request-example"></a>Anforderungsbeispiel

Die folgenden Beispiele zeigen verschiedene Anforderungen für das Abrufen von Fehlerberichtsdaten. Ersetzen Sie den Wert *applicationId* durch die Produkt-ID Ihrer Desktopanwendung.

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/desktop/failurehits?applicationId=10238467886765136388&startDate=1/1/2018&endDate=2/1/2018&top=10&skip=0 HTTP/1.1
Authorization: Bearer <your access token>

GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/desktop/failurehits?applicationId=10238467886765136388&startDate=8/1/2017&endDate=8/31/2017&skip=0&filter=market eq 'US' and deviceType eq 'PC' HTTP/1.1
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
| date            | string  | Das erste Datum im Datumsbereich für die Fehlerdaten im Format ```yyyy-mm-dd```. Wenn die Anforderung einen einzelnen Tag angibt, ist dieses Datum dieser Wert. Wenn die Anforderung einen längeren Datumsbereich angibt, ist dieser Wert das erste Datum in diesem Datumsbereich. Für Anforderungen, die einen *aggregationLevel*-Wert von **hour** angeben, enthält dieser Wert auch einen Zeitwert im Format ```hh:mm:ss```.  |
| applicationId   | string  | Die Produkt-ID der Desktopanwendung, für die Fehlerdaten abgerufen wurden.    |
| productName | string  | Der Anzeigename der Desktopanwendung, der aus den Metadaten der zugehörigen ausführbaren Datei(en) abgeleitet wurde.   |
| appName | string  |  TBD  |
| fileName | string  | Der Name der ausführbaren Datei für die Desktopanwendung.   |
| failureName     | string  | Der Name des Fehlers, der aus vier Teilen besteht: eine oder mehrere Problemklassen, ein Ausnahme/Fehlerprüfcode, der Name des Image, in dem der Fehler aufgetreten ist, und der zugehörige Funktionsname.  |
| failureHash     | string  | Der eindeutige Bezeichner des Fehlers.   |
| symbol          | string  | Das diesem Fehler zugewiesene Symbol. |
| osBuild       | string  | Die vierteilige Buildnummer des Betriebssystems, auf dem der Fehler aufgetreten ist.  |
| osVersion       | string  | Eine der folgenden Zeichenfolgen, die die Version des Betriebssystems angibt, auf dem die Desktopanwendung installiert wurde:<p/><ul><li><strong>Windows 7</strong></li><li><strong>Windows8.1</strong></li><li><strong>Windows 10</strong></li><li><strong>Windows Server 2016</strong></li><li><strong>Windows Server 1709</strong></li><li><strong>Unknown</strong></li></ul>   |   
| osRelease | string  | Eine der folgenden Zeichenfolgen, die die Betriebssystemversion oder den Verteilungsring (als eine Subpopulation innerhalb der Betriebssystemversion) angibt, in der bzw. dem der Fehler aufgetreten ist.<p/><p>Für Windows10:</p><ul><li><strong>Version1507</strong></li><li><strong>Version1511</strong></li><li><strong>Version1607</strong></li><li><strong>Version1703</strong></li><li><strong>Version1709</strong></li><li><strong>Version1803</strong></li><li><strong>Release Preview</strong></li><li><strong>Insider Fast</strong></li><li><strong>Insider Slow</strong></li></ul><p/><p>Für Windows Server 1709:</p><ul><li><strong>RTM</strong></li></ul><p>Für Windows Server 2016:</p><ul><li><strong>Version1607</strong></li></ul><p>Für Windows8.1:</p><ul><li><strong>Update 1</strong></li></ul><p>Für Windows7:</p><ul><li><strong>Service Pack 1</strong></li></ul><p>Wenn die Betriebssystemversion oder Verteilungsring unbekannt ist, hat dieses Feld den Wert <strong>Unknown</strong>.</p> |
| eventType       | string  | Eine der folgenden Zeichenfolgen, die den Typ des Fehlerereignisses angibt:<ul><li>**crash**</li><li>**hang**</li><li>**memory**</li><li>**jse**</li></ul>       |
| market          | string  | Der ISO3166-Ländercode des Gerätemarkts.   |
| deviceType      | String  | Eine der folgenden Zeichenfolgen, die den Typ des Geräts angibt, auf dem der Fehler aufgetreten ist:<p/><ul><li><strong>PC</strong></li><li><strong>Server</strong></li><li><strong>Tablet</strong></li><li><strong>Unknown</strong></li></ul>    |
| applicationVersion     | string  |   Die Version der ausführbaren Datei der Anwendung, in der der Fehler aufgetreten ist.    |
| eventCount      | number | Die Anzahl der Ereignisse, die diesem Fehler für die angegebene Aggregationsebene zugeordnet werden.      |


### <a name="response-example"></a>Antwortbeispiel

Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.

```json
{
  "Value": [
    {
      "date": "2018-02-01",
      "applicationId": "10238467886765136388",
      "productName": "Contoso Demo",
      "appName": "Contoso Demo",
      "fileName": "contosodemo.exe",
      "failureName": "SVCHOSTGROUP_localservice_IN_PAGE_ERROR_c0000006_hardware_disk!Unknown",
      "failureHash": "11242ef3-ebd8-d525-838d-b5497b225695",
      "symbol": "hardware_disk!Unknown",
      "osBuild": "10.0.15063.850",
      "osVersion": "Windows 10",
      "osRelease": "Version 1703",
      "eventType": "crash",
      "market": "US",
      "deviceType": "PC",
      "applicationVersion": "2.2.2.0",
      "eventCount": 0.0012422360248447205
    }
  ],
  "@nextLink": "desktop/failurehits?applicationId=10238467886765136388&aggregationLevel=week&startDate=2018/02/01&endDate2018/02/08&top=1&skip=1",
  "TotalCount": 21
}

```

## <a name="related-topics"></a>Verwandte Themen

* [Integritätsbericht](../publish/health-report.md)
* [Zugreifen auf Analysedaten mit MicrosoftStore-Diensten](access-analytics-data-using-windows-store-services.md)
* [Abrufen von Details zu einem Fehler in Ihrer Desktopanwendung](get-details-for-an-error-in-your-desktop-application.md)
* [Abrufen der Stapelüberwachung für einen Fehler in der Desktopanwendung](get-the-stack-trace-for-an-error-in-your-desktop-application.md)
* [Herunterladen der CAB-Datei bei einem Fehler in Ihrer Desktopanwendung](download-the-cab-file-for-an-error-in-your-desktop-application.md)
