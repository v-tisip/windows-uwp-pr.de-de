---
ms.assetid: C1E42E8B-B97D-4B09-9326-25E968680A0F
description: Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um die aggregierten Kaufdaten für ein Xbox One Spiel während eines bestimmten Zeitraums und mit anderen optionalen Filtern abzurufen.
title: Abrufen von Xbox One Spielekäufen
ms.date: 10/18/2018
ms.topic: article
keywords: Windows10, UWP, Store-Dienste, Microsoft Store-Analyse-API, Xbox One Spielekäufe
ms.localizationpriority: medium
ms.openlocfilehash: 348430f7ceee66a9c4e82f258a70e57d8f344943
ms.sourcegitcommit: b11f305dbf7649c4b68550b666487c77ea30d98f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "7837585"
---
# <a name="get-xbox-one-game-acquisitions"></a>Abrufen von Xbox One Spielekäufen

Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, die aggregierte Kaufdaten im JSON-Format für einen Xbox One Spiel abzurufen, die das über das Xbox-Portal (XDP) und im XDP Analytics-Dashboard verfügbar ist.

## <a name="prerequisites"></a>Voraussetzungen

Zur Verwendung dieser Methode sind folgende Schritte erforderlich:

* Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.
* [Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird. Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft. Wenn das Token abgelaufen ist, können Sie ein neues abrufen.

## <a name="request"></a>Anforderung


### <a name="request-syntax"></a>Anforderungssyntax

| Methode | Anforderungs-URI       |
|--------|----------------------|
| GET    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/xbox/acquisitions``` |


### <a name="request-header"></a>Anforderungsheader

| Header        | Typ   | Beschreibung                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| Autorisierung | String | Erforderlich. Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;. |


### <a name="request-parameters"></a>Anforderungsparameter

| Parameter        | Typ   |  Beschreibung      |  Erforderlich  
|---------------|--------|---------------|------|
| applicationId | String | Die Produkt-ID des Xbox One Spiels, für das Sie Kaufdaten abrufen. Um die Produkt-ID Ihres Spiels zu erhalten, navigieren Sie zu Ihrem Spiel im XDP Analytics-Programm, und rufen Sie die Produkt-ID aus der URL. Wenn Sie Ihre Kaufdaten vom Partner Center-Analysebericht herunterladen, ist die Produkt-ID auch in der TSV-Datei enthalten.  |  Ja  |
| startDate | date | Das Startdatum im Datumsbereich der Kaufdaten, die abgerufen werden sollen. Der Standardwert ist das aktuelle Datum. |  Nein  |
| endDate | date | Das Enddatum im Datumsbereich der Kaufdaten, die abgerufen werden sollen. Der Standardwert ist das aktuelle Datum. |  Nein  |
| top | Int | Die Anzahl der Datenzeilen, die zurückgegeben werden sollen. Der Maximal- und Standardwert ist 10.000, wenn nicht anders angegeben. Wenn die Abfrage keine weiteren Zeilen enthält, entält der Antworttext den Link „Weiter“, den Sie verwenden können, um die nächste Seite mit Daten anzufordern. |  Nein  |
| skip | int | Die Anzahl der Zeilen, die in der Abfrage übersprungen werden sollen. Verwenden Sie diesen Parameter, um große Datensätze durchzublättern. Beispielsweise rufen „top=10000“ und „skip=0“ die ersten 10.000Datenzeilen ab, „top=10000“ und „skip=10000“ die nächsten 10.000Datenzeilen usw. |  Nein  |
| filter | string  | Mindestens eine Anweisung, die die Zeilen in der Antwort filtert. Jede Anweisung enthält einen Feldnamen aus dem Antworttext und einen Wert, die mit den Operatoren **eq** oder **ne** verknüpft sind. Anweisungen können mit **and** oder **or** kombiniert werden. Zeichenfolgenwerte im Parameter *filter* müssen von einfachen Anführungszeichen eingeschlossen werden. Beispiel: *filter=market eq 'US' and gender eq 'm'*. <p/><p/>Sie können die folgenden Felder aus dem Antworttext angeben:<p/><ul><li><strong>acquisitionType</strong></li><li><strong>Alter</strong></li><li><strong>storeClient</strong></li><li><strong>gender</strong></li><li><strong>market</strong></li><li><strong>osVersion</strong></li><li><strong>deviceType</strong></li><li><strong>sandboxId</strong></li></ul> | Nein   |
| aggregationLevel | string | Gibt den Zeitraum an, für den aggregierte Daten abgerufen werden sollen. Dies kann eine der folgenden Zeichenfolgen sein: <strong>day</strong>, <strong>week</strong> oder <strong>month</strong>. Wenn keine Angabe erfolgt, lautet der Standardwert <strong>day</strong>. | Nein |
| orderby | string | Eine Anweisung, die die Ergebnisdatenwerte für die einzelnen Käufe anfordert. Die Syntax lautet <em>orderby=field [order],field [order],...</em>, wobei der Parameter <em>field</em> eine der folgenden Zeichenfolgen sein kann:<ul><li><strong>date</strong></li><li><strong>acquisitionType</strong></li><li><strong>Alter</strong></li><li><strong>storeClient</strong></li><li><strong>gender</strong></li><li><strong>market</strong></li><li><strong>osVersion</strong></li><li><strong>deviceType</strong></li><li><strong>paymentInstrumentType</strong></li><li><strong>sandboxId</strong></li><li><strong>xboxTitleIdHex</strong></li></ul><p>Der Parameter <em>order</em> ist optional und kann <strong>asc</strong> oder <strong>desc</strong> sein, um die auf- oder absteigende Anordnung der einzelnen Felder anzugeben. Der Standard ist <strong>asc</strong>.</p><p>Dies ist eine Beispielzeichenfolge für <em>orderby</em>: <em>orderby=date,market</em></p> |  Nein  |
| groupby | string | Eine Anweisung, die nur auf die angegebenen Felder Datenaggregationen anwendet. Sie können die folgenden Felder angeben:<ul><li><strong>date</strong></li><li><strong>applicationName</strong></li><li><strong>acquisitionType</strong></li><li><strong>ageGroup</strong></li><li><strong>storeClient</strong></li><li><strong>gender</strong></li><li><strong>market</strong></li><li><strong>osVersion</strong></li><li><strong>deviceType</strong></li><li><strong>paymentInstrumentType</strong></li><li><strong>sandboxId</strong></li><li><strong>xboxTitleIdHex</strong></li></ul><p>Die zurückgegebenen Datenzeilen enthalten die Felder, die im Parameter <em>groupby</em> angegeben sind, sowie die folgenden:</p><ul><li><strong>date</strong></li><li><strong>applicationId</strong></li><li><strong>acquisitionQuantity</strong></li></ul><p>Der Parameter <em>groupby</em> kann mit dem Parameter <em>aggregationLevel</em> verwendet werden. Beispiel: <em>&amp;groupby=ageGroup,market&amp;aggregationLevel=week</em></p> |  Nein  |


### <a name="request-example"></a>Anforderungsbeispiel

Das folgende Beispiel zeigt verschiedene Anforderungen für den Abruf von Spielekaufdaten für Xbox One. Ersetzen Sie den *ApplicationId* -Wert durch die Produkt-ID für Ihr Spiel an.

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/xbox/acquisitions?applicationId=BRRT4NJ9B3D1&startDate=1/1/2017&endDate=2/1/2017&top=10&skip=0 HTTP/1.1
Authorization: Bearer <your access token>

GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/xbox/acquisitions?applicationId=BRRT4NJ9B3D1&startDate=8/1/2017&endDate=8/31/2017&skip=0&filter=market eq 'US' and gender eq 'm' HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a>Antwort


### <a name="response-body"></a>Antworttext

| Wert      | Typ   | Beschreibung                  |
|------------|--------|-------------------------------------------------------|
| Wert      | Array  | Ein Array von Objekten, die aggregierte Kaufdaten für das Spiel enthalten. Weitere Informationen zu den Daten in den einzelnen Objekten finden Sie unten im Abschnitt [Kaufwerte](#acquisition-values).                                                                                                                      |
| @nextLink  | String | Wenn weitere Seiten mit Daten vorhanden sind, enthält diese Zeichenfolge einen URI, mit dem Sie die nächste Seite mit Daten anfordern können. Beispielsweise wird dieser Wert zurückgegeben, wenn der Parameter **top** der Anforderung auf 10000 festgelegt ist, es jedoch mehr als 10.000 Zeilen mit Kaufdaten für die Abfrage gibt. |
| TotalCount | int    | Die Gesamtzahl der Zeilen im Datenergebnis für die Abfrage.              |


### <a name="acquisition-values"></a>Kaufwerte

Elemente im Array *Value* enthalten die folgenden Werte.

| Wert               | Typ   | Beschreibung                           |
|---------------------|--------|-------------------------------------------|
| date                | string | Das erste Datum im Datumsbereich für die Kaufdaten. Wenn die Anforderung einen einzelnen Tag angibt, ist dieses Datum dieser Wert. Wenn die Anforderung eine Woche, einen Monat oder einen anderen Datumsbereich angibt, ist dieser Wert das erste Datum in diesem Datumsbereich. |
| applicationId       | String | Die Produkt-ID des Xbox One Spiels, für das Sie Kaufdaten abrufen. |
| applicationName     | String | Der Anzeigename des Spiels.       |
| acquisitionType     | String | Eine der folgenden Zeichenfolgen, die den Typ des Kaufes angibt:<ul><li><strong>Free</strong></li><li><strong>Testversion</strong></li><li><strong>Kostenpflichtig</strong></li><li><strong>Angebotscode</strong></li><li><strong>lap</strong></li><li><strong>Abonnement Iap</strong></li><li><strong>Private Zielgruppe</strong></li><li><strong>Pre-Reihenfolge</strong></li><li><strong>Xbox Game Pass</strong> (oder <strong>Game Pass</strong> beim Abfragen von Daten vor dem 23.März2018)</li><li><strong>Festplatte</strong></li><li><strong>Prepaid-Code</strong></li><li><strong>Berechnete Pre-Reihenfolge</strong></li><li><strong>Abgebrochenen Pre-Reihenfolge</strong></li><li><strong>Fehlgeschlagene Pre-Reihenfolge</strong></li></ul>    |
| Alter                 | String | Eine der folgenden Zeichenfolgen, die die Altersgruppe des Benutzers anzeigt, der den Kauf getätigt hat:<ul><li><strong>jünger als 13</strong></li><li><strong>13-17</strong></li><li><strong>18-24</strong></li><li><strong>25-34</strong></li><li><strong>35-44</strong></li><li><strong>44-55</strong></li><li><strong>greater than 55</strong></li><li><strong>Unknown</strong></li></ul>     |
| deviceType          | String | Eine der folgenden Zeichenfolgen, die den Typ des Geräts angibt, mit dem der Kauf getätigt wurde:<ul><li><strong>PC</strong></li><li><strong>Phone</strong></li><li><strong>Console</strong></li><li><strong>IoT</strong></li><li><strong>Server</strong></li><li><strong>Tablet</strong></li><li><strong>Hologramm</strong></li><li><strong>Unbekannt</strong></li></ul>  |
| gender              | String | Eine der folgenden Zeichenfolgen, die das Geschlecht des Benutzer angibt, der den Kauf getätigt hat:<ul><li><strong>m</strong></li><li><strong>f</strong></li><li><strong>Unknown</strong></li></ul>     |
| market              | string | Der ISO 3166-Ländercode des Markts, in dem der Kauf erfolgte.  |
| osVersion           | string | Die Version des Betriebssystems, auf dem der Kauf ausgeführt wurde. Bei dieser Methode ist dieser Wert immer **Windows10**.</li></ul>    |
| paymentInstrumentType           | String | Eine der folgenden Zeichenfolgen, die die Kaufanweisungen anzeigt, die für den Erwerb verwendet wurde:<ul><li><strong>Kreditkarte</strong></li><li><strong>Lastschriftkarte</strong></li><li><strong>Abgeleiteter Kauf</strong></li><li><strong>MS Saldo</strong></li><li><strong>Mobilfunkanbieter</strong></li><li><strong>Online-Überweisung</strong></li><li><strong>PayPal</strong></li><li><strong>Geteilte Transaktion</strong></li><li><strong>Token einlösen</strong></li><li><strong>Nullbetrag gezahlt</strong></li><li><strong>eWallet</strong></li><li><strong>Unbekannt</strong></li></ul>    |
| sandboxId              | String | Das Sandbox-ID, die für das Spiel erstellt wurde. Dies kann der Wert **RETAIL** sein oder die ID für die private Sandbox.  |
| storeClient         | string | Eine der folgenden Zeichenfolgen, die die Version des Store anzeigt, wo der Kauf getätigt wurde:<ul><li>**Windows Phone Store (Client)**</li><li>**Microsoft Store (Client)** (oder **Windows Store (Client)** bei Abfragen von Daten vor dem 23.März2018)</li><li>**Microsoft Store (Web)** (oder **Windows Store (Web)** bei Abfragen von Daten vor dem 23.März2018)</li><li>**Volumenkäufe durch Organisationen**</li><li>**Andere**</li></ul>                             |
| xboxTitleIdHex              | String | Die Xbox Live Titel-ID (dargestellt in hexadezimalen Wert), die vom der Xbox Developer-Portal (XDP) für Xbox Live-fähige Spiele zugewiesen wurde.  |
| acquisitionQuantity | number | Die Anzahl der Käufe, die während der angegebenen Aggregationsebene erfolgten.     |
| purchasePriceUSDAmount | number | Der vom Kunden gezahlte Betrag für den Kauf, der mithilfe des monatlichen Wechselkurses in USD konvertiert wurde.    |
| taxUSDAmount     | number | Der in USD konvertierte Steuerbetrag, der für den Kauf fällig ist. |


### <a name="response-example"></a>Antwortbeispiel

Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.

```json
{
  "Value": [
    {
      "date": "2017-02-01",
      "applicationId": "BRRT4NJ9B3D1 ",
      "applicationName": "Contoso Game",
      "acquisitionType": "Paid",
      "age": "35-49",
      "deviceType": "Console",
      "gender": "m",
      "market": "US",
      "osVersion": "Windows 10",
      "PaymentInstrumentType": "Credit Card ",
      "sandboxId": "RETAIL",
      "storeClient": "Windows Store (web)",
      "xboxTitleIdHex": "",
      "acquisitionQuantity": 1,
      "purchasePriceUSDAmount": 29.99,
      "taxUSDAmount": 2.99
    }
  ],
  "@nextLink": "xbox/acquisitions?applicationId=BRRT4NJ9B3D1&aggregationLevel=day&startDate=2017/02/01&endDate=2017/03/01&top=1&skip=1&orderby=date desc",
  "TotalCount": 39812
}
```

## <a name="related-topics"></a>Verwandte Themen

* [Zugreifen auf Analysedaten mit MicrosoftStore-Diensten](access-analytics-data-using-windows-store-services.md)
