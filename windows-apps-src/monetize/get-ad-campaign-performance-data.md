---
author: mcleanbyron
ms.assetid: A26A287C-B4B0-49E9-BB28-6F02472AE1BA
description: "Verwenden Sie diese Methode der Windows Store-Analyse-API, um die aggregierten Leistungsdaten einer Anzeigenkampagne für die angegebene Anwendung während eines bestimmten Zeitraums sowie andere optionale Filter abzurufen."
title: Abrufen der Leistungsdaten einer Anzeigenkampagne
translationtype: Human Translation
ms.sourcegitcommit: 67845c76448ed13fd458cb3ee9eb2b75430faade
ms.openlocfilehash: 8859658675d31deccc3403e4862c47a54ca25b1a

---

# Abrufen der Leistungsdaten einer Anzeigenkampagne


Verwenden Sie diese Methode der Windows Store-Analyse-API, um eine aggregierte Zusammenfassung der Leistungsdaten einer Anzeigenkampagne für Ihre Anwendungen während eines bestimmten Zeitraums sowie andere optionale Filter abzurufen. Diese Methode gibt die Daten im JSON-Format zurück.

Diese Methode gibt dieselben Daten wie der [Bericht „Anzeigen für die App-Installation“](../publish/app-install-ads-reports.md) im Windows Dev Center-Dashboard zurück. Weitere Informationen zu Anzeigenkampagnen finden Sie unter [Erstellen einer Anzeigenkampagne für Ihre App](https://msdn.microsoft.com/windows/uwp/publish/create-an-ad-campaign-for-your-app).

Um vollständige Details für alle Anzeigenkampagnen abzurufen, die für Ihr Dev Center-Konto erstellt wurden, können Sie die später in diesem Artikel beschriebene [Methode zum Abrufen von Details für alle Anzeigenkampagnen](#get-details-for-all-ad-campaigns) verwenden.

## Voraussetzungen


Zur Verwendung dieser Methode sind folgende Schritte erforderlich:

* Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Windows Store-Analyse-API.
* [Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird. Nachdem Sie ein Zugriffstoken erhalten haben, haben Sie 60Minuten Zeit, das Token zu verwenden, bevor es abläuft. Wenn das Token abgelaufen ist, können Sie ein neues abrufen.

## Anforderung


### Anforderungssyntax

| Methode | Anforderungs-URI                                                              |
|--------|--------------------------------------------------------------------------|
| GET    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/promotion``` |

<span />

### Anforderungsheader

| Header        | Typ   | Beschreibung                |
|---------------|--------|---------------|
| Autorisierung | string | Erforderlich. Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;. |

<span />

### Anforderungsparameter

Um die Leistungsdaten einer Anzeigenkampagne für eine bestimmte App abzurufen, verwenden Sie den Parameter *applicationId*. Um die Leistungsdaten einer Anzeige für alle Apps abzurufen, die Ihrem Entwicklerkonto zugeordnet sind, lassen Sie den Paramater *applicationId* aus.

| Parameter     | Typ   | Beschreibung     | Erforderlich |
|---------------|--------|-----------------|----------|
| applicationId   | string    | Die Store-ID der App, für die Sie die Leistungsdaten einer Anzeigenkampagne abrufen möchten. Die Store-ID ist auf der [Seite mit der App-Identität](../publish/view-app-identity-details.md) des DevCenter-Dashboards verfügbar. Beispiel für eine Store-ID: 9NBLGGH4R315. |    Nein      |
|  startDate  |  date   |  Das Startdatum im Datumsbereich der abzurufenden Leistungsdaten einer Anzeigenkampagne im Format JJJJ/MM/TT. Der Standardwert ist das aktuelle Datum minus 30Tage.   |   Nein    |
| endDate   |  date   |  Das Enddatum im Datumsbereich der abzurufenden Leistungsdaten einer Anzeigenkampagne im Format JJJJ/MM/TT. Der Standardwert ist das aktuelle Datum minus einen Tag.   |   Nein    |
| top   |  int   |  Die Anzahl der Datenzeilen, die in der Anforderung zurückgegeben werden sollen. Der Maximal- und Standardwert ist 10.000, wenn nicht anders angegeben. Wenn die Abfrage keine weiteren Zeilen enthält, entält der Antworttext den Link „Weiter“, den Sie verwenden können, um die nächste Seite mit Daten anzufordern.   |   Nein    |
| skip   | int    |  Die Anzahl der Zeilen, die in der Abfrage übersprungen werden sollen. Verwenden Sie diesen Parameter, um große Datensätze durchzublättern. Beispielsweise rufen „top=10000“ und „skip=0“ die ersten 10.000Datenzeilen ab, „top=10000“ und „skip=10000“ die nächsten 10.000Datenzeilen usw.   |   Nein    |
| filter   |  string   |  Mindestens eine Anweisung, die die Zeilen in der Antwort filtert. Der einzige unterstützte Filter ist **campaignId**. Alle Anweisungen können die Operatoren **eq** oder **ne** verwenden. Zudem können sie mit **and** oder **or** kombiniert werden.  Hier finden Sie ein Beispiel für den Parameter *filter*: ```filter=campaignId eq '100023'```.   |   Nein    |
|  aggregationLevel  |  string   | Gibt den Zeitraum an, für den aggregierte Daten abgerufen werden sollen. Dies kann eine der folgenden Zeichenfolgen sein: <strong>day</strong>, <strong>week</strong> oder <strong>month</strong>. Wenn keine Angabe erfolgt, lautet der Standardwert <strong>day</strong>.    |   Nein    |
| orderby   |  string   |  <p>Eine Anweisung, die die Ergebnisdatenwerte für die Leistungsdaten einer Anzeigenkampagne anfordert. Die Syntax ist <em>orderby=field [order],field [order],...</em>. Der Parameter <em>field</em> kann eine der folgenden Zeichenfolgen sein:</p><ul><li><strong>date</strong></li><li><strong>campaignId</strong></li></ul><p>Der Parameter <em>order</em> ist optional und kann <strong>asc</strong> oder <strong>desc</strong> sein, um die auf- oder absteigende Anordnung der einzelnen Felder anzugeben. Der Standard ist <strong>asc</strong>.</p><p>Dies ist eine Beispielzeichenfolge für <em>orderby</em>: <em>orderby=date,campaignId</em></p>   |   Nein    |
|  groupby  |  string   |  <p>Eine Anweisung, die nur auf die angegebenen Felder Datenaggregationen anwendet. Sie können die folgenden Felder angeben:</p><ul><li><strong>campaignId</strong></li><li><strong>applicationId</strong></li><li><strong>date</strong></li><li><strong>currencyCode</strong></li></ul><p>Der Parameter <em>groupby</em> kann mit dem Parameter <em>aggregationLevel</em> verwendet werden. Beispiel: <em>&amp;groupby=applicationId&amp;aggregationLevel=week</em></p>   |   Nein    |


<span />
 

### Anforderungsbeispiel

Das folgende Beispiel zeigt verschiedene Anforderungen für das Abrufen der Leistungsdaten einer Anzeigenkampagne auf.

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/promotion?aggregationLevel=week&groupby=applicationId,campaignId,date  HTTP/1.1
Authorization: Bearer <your access token>

GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/promotion?applicationId=9NBLGGH0XK8Z&startDate=2015/1/20&endDate=2016/8/31&skip=0&filter=campaignId eq '31007388' HTTP/1.1
Authorization: Bearer <your access token>
```

## Antwort


### Antworttext

| Wert      | Typ   | Beschreibung                                                                                                                                                                                                                                                                            |
|------------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Value      | array  | Ein Array von Objekten mit den aggregierten Leistungsdaten einer Anzeigenkampagne. Weitere Informationen zu den Daten in den einzelnen Objekten finden Sie unten im Abschnitt [Kampagnenleistungsobjekt](#campaign-performance-object).                                                                                                                      |
| @nextLink  | string | Wenn weitere Seiten mit Daten vorhanden sind, enthält diese Zeichenfolge einen URI, mit dem Sie die nächste Seite mit Daten anfordern können. Beispielsweise wird dieser Wert zurückgegeben, wenn der Parameter **top** der Anforderung auf 5 festgelegt ist, es jedoch mehr als fünf Datenelemente für die Abfrage gibt. |
| TotalCount | int    | Die Gesamtzahl der Zeilen im Datenergebnis für die Abfrage.                                                                                                                                                                                                                             |

<span id="campaign-performance-object" />
### Kampagnenleistungsobjekt

Elemente im Array *Value* enthalten die folgenden Werte.

| Wert               | Typ   | Beschreibung            |
|---------------------|--------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| date                | string | Das erste Datum im Datumsbereich für die Leistungsdaten einer Anzeigenkampagne. Wenn die Anforderung einen einzelnen Tag angibt, ist dieses Datum dieser Wert. Wenn die Anforderung eine Woche, einen Monat oder einen anderen Datumsbereich angibt, ist dieser Wert das erste Datum in diesem Datumsbereich. |
| applicationId       | string | Die Store-ID der App, für die Sie die Leistungsdaten einer Anzeigenkampagne abrufen.                     |
| campaignId     | string | Die ID der Anzeigenkampagne.           |
| currencyCode              | string | Der Währungscode für das Kampagnenbudget.              |
| spend          | string |  Der Budgetbetrag, der in die Anzeigenkampagne investiert wurde.     |
| impressions           | lang | Die Anzahl der Anzeigenaufrufe für die Kampagne.        |
| installs              | lang | Die Anzahl der App-Installationen im Zusammenhang mit der Kampagne.   |
| clicks            | lang | Die Anzahl der Klicks für die Kampagne.      |

<span />

### Antwortbeispiel

Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.

```json
{
  "Value": [
    {
      "date": "2015-04-12",
      "applicationId": "9WZDNCRFJ31Q",
      "campaignId": "4568",
      "currencyCode": "USD",
      "spend": 700.6,
      "impressions": 200,
      "installs": 30,
      "clicks": 8
    },
    {
      "date": "2015-05-12",
      "applicationId": "9WZDNCRFJ31Q",
      "campaignId": "1234",
      "currencyCode": "USD",
      "spend": 325.3,
      "impressions": 20,
      "installs": 2,
      "clicks": 5
    }
  ],
  "@nextLink": "promotion?applicationId=9NBLGGGZ5QDR&aggregationLevel=day& startDate=2015/1/20&endDate=2016/8/31&top=2&skip=2",
  "TotalCount": 1917
}
```

<span id="get-details-for-all-ad-campaigns" />
## Abrufen von Details für alle Anzeigenkampagnen


Rufen Sie mit dieser Methode detaillierte Informationen für alle Anzeigenkampagnen ab, die für Apps erstellt wurden, die in Ihrem Windows Dev Center-Konto registriert in. Diese Methode gibt die Daten im JSON-Format zurück. Weitere Informationen zu Anzeigenkampagnen finden Sie unter [Erstellen einer Anzeigenkampagne für Ihre App](https://msdn.microsoft.com/windows/uwp/publish/create-an-ad-campaign-for-your-app).

### Voraussetzungen

Zur Verwendung dieser Methode sind folgende Schritte erforderlich:

* Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Windows Store-Analyse-API.
* [Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird. Nachdem Sie ein Zugriffstoken erhalten haben, haben Sie 60Minuten Zeit, das Token zu verwenden, bevor es abläuft. Wenn das Token abgelaufen ist, können Sie ein neues abrufen.

### Anforderung


#### Anforderungssyntax

| Methode | Anforderungs-URI                                                              |
|--------|--------------------------------------------------------------------------|
| GET    | ```https://manage.devcenter.microsoft.com/v1.0/my/promotion/adscampaign``` |

<span />

#### Anforderungsheader

| Header        | Typ   | Beschreibung                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| Autorisierung | string | Erforderlich. Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;. |

<span />

#### Anforderungsparameter

| Parameter     | Typ   | Beschreibung     | Erforderlich |
|---------------|--------|-----------------|----------|
| top           | int    | Die Anzahl der Datenzeilen, die in der Anforderung zurückgegeben werden sollen. Der Maximal- und Standardwert ist 10.000, wenn nicht anders angegeben. Sind in der Abfrage keine weiteren Zeilen, enthält der Antworttext den Link „Weiter“, über den Sie die nächste Seite mit Daten anfordern können. |    Nein      |
| skip           | int    | Die Anzahl der Zeilen, die in der Abfrage übersprungen werden sollen. Verwenden Sie diesen Parameter, um große Datensätze durchzublättern. Beispielsweise rufen „top=10000“ und „skip=0“ die ersten 10.000Datenzeilen ab, „top=10000“ und „skip=10000“ die nächsten 10.000Datenzeilen usw. |    Nein      |


<span />
 

#### Anforderungsbeispiel

Das folgende Beispiel veranschaulicht verschiedene Anforderungen für das Abrufen von detaillierten Informationen für all Ihre Anzeigenkampagnen.

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/promotion/adscampaign?top=10&skip=0  HTTP/1.1
Authorization: Bearer <your access token>
```

### Antwort


#### Antworttext

| Wert      | Typ   | Beschreibung  |
|------------|--------|--------------|
| Value      | array  | Ein Array von Objekten mit Details zu Ihren Anzeigenkampagnen. Weitere Informationen zu den Daten in den einzelnen Objekten finden Sie unten im Abschnitt [Kampagnenobjekt](#campaign-object).                        |
| @nextLink  | string | Wenn weitere Seiten mit Daten vorhanden sind, enthält diese Zeichenfolge einen URI, mit dem Sie die nächste Seite mit Daten anfordern können. Beispielsweise wird dieser Wert zurückgegeben, wenn der Parameter **top** der Anforderung auf 5 festgelegt ist, es jedoch mehr als fünf Datenelemente für die Abfrage gibt. |                                   |

<span id="campaign-object" />
#### Kampagnenobjekt

Elemente im Array *Value* enthalten die folgenden Werte.

| Wert               | Typ   | Beschreibung          |
|---------------------|--------|------------------|
| id     | string | Die ID der Anzeigenkampagne. |
| name     | string | Der Name der Anzeigenkampagne. |
| createDate     | string | Das Datum, an dem die Anzeigenkampagne erstellt wurde (in der UTC-Zeitzone). |
| startDate     | string | Das Startdatum der Anzeigenkampagne (in der UTC-Zeitzone). |
| endDate     | string | Das Enddatum der Anzeigenkampagne (in der UTC-Zeitzone). |
| applicationId       | string | Die Store-ID der App, der die Anzeigenkampagne zugeordnet ist. Die Store-ID ist auf der [Seite mit der App-Identität](../publish/view-app-identity-details.md) des DevCenter-Dashboards verfügbar. Beispiel für eine Store-ID: 9NBLGGH4R315.                    |
| budget     | number | Das Budget der Anzeigenkampagne.           |
| budgetType    | string | Der Budgettyp der Anzeigenkampagne. Hierbei kann es sich um eine der folgenden Zeichenfolgen handeln: **Monthly** oder **Total**.           |
| currencyCode              | string | Der Währungscode für das Kampagnenbudget.              |
| type              | string | Der Typ der Anzeigenkampagne. Hierbei kann es sich um eine der folgenden Zeichenfolgen handeln: **Paid**, **House** oder **Community**.             |
| status              | string | Der Status der Anzeigenkampagne. Hierbei kann es sich um eine der folgenden Zeichenfolgen handeln: **Active**, **UserPaused**, **Pending**, **Ended** oder **SystemPaused**.             |
| targetingType              | string | Der Zielgruppenadressierungstyp der Anzeigenkampagne. Hierbei kann es sich um eine der folgenden Zeichenfolgen handeln: **Auto**, **Manual** oder **Segment**.             |
| target              | dictionary | Ein Wörterbuch mit Schlüssel-Wert-Paaren, die Zielgruppenadressierungsdaten für die Kampagne enthalten. Weitere Informationen zu diesem Objekt finden Sie unten im Abschnitt [Zielobjekt](#target-object).             |

<span />

<span id="target-object" />
#### Zielobjekt

Diese Ressource ist ein Wörterbuch mit den folgenden Schlüssel-Wert-Paaren.

| Schlüssel               | Typ   | Wert          |
|---------------------|--------|------------------|
| Country     | array |   Eine oder mehrere Zeichenfolgen, die die ISO3166-Alpha-2-Codes der Länder oder Regionen enthalten, auf die die Anzeigenkampagne abzielt. |
| OsVersion     | array | Eine oder mehrere der folgenden Zeichenfolgen, die die Betriebssystemversionen angeben, auf die die Anzeigenkampagne abzielt: **10** oder **8.x**.  |
| Alter     |  array |  Eine oder mehrere der folgenden Zeichenfolgen, die den Altersbereich der Zielgruppe angeben: **Age13To17**, **Age18To24**, **Age25To34**, **Age35To49** oder **Age50AndAbove**. |
| Gender     |  array |  Eine oder mehrere der folgenden Zeichenfolgen, die das Geschlecht der Zielgruppe angeben: **Female** oder **Male**. |
| DeviceType       |  array  |  Eine oder mehrere der folgenden Zeichenfolgen, die den Zielgerätetyp angeben: **PC/Tablet** oder **Phone**.                  |
| Segment     |  array |    Eine oder mehrere Zeichenfolgen, die die IDs der Kundensegmente der Zielgruppe enthalten.       |


<span />

#### Antwortbeispiel

Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.

```json
{
   "Value": [
      {
         "id":31010026,
         "name": "Contoso App 1 Campaign",
         "createDate":"2016-07-14T10:01:21Z",
         "startDate":"2016-07-21T11:23:36Z",
         "applicationId":"9NBLGGH0XK8Z",
         "budget": 100,
         "budgetType":"Monthly",
         "currencyCode": "USD",
         "type": "Paid",
         "status": "Active",
         "targetingType": "Auto",
         "target": null
      },
      {
         "id":31010025,
         "name":"Contoso App 2 Campaign",
         "createDate":"2016-07-14T10:02:21Z",
         "startDate":"2016-07-21T11:18:44Z",
         "endDate":"2016-08-21T11:18:44Z",
         "applicationId":"9WZDNCRDX48S",
         "budget": 50,
         "budgetType":"Total",
         "currencyCode": "USD",
         "type": "Paid",
         "status": "Ended",
         "targetingType": "Manual",
         "target": {
            "Country": [
               "US",
               "BR",
               "FR",
               "IN",
               "IT"
            ],
            "OsVersion": [
               "8.X"
            ],
            "Age": [
               "Age18To24",
               "Age25To34",
               "Age35To49",
               "Age50AndAbove"
            ],
            "Gender": [
               "Male"
            ],
            "DeviceType": [
               "PC/Tablet",
               "Phone"
            ]
         }
      }
   ]
}
```

## Verwandte Themen

* [Bericht „Anzeigen für die App-Installation“](../publish/app-install-ads-reports.md)
* [Erstellen einer Anzeigenkampagne für Ihre App](https://msdn.microsoft.com/windows/uwp/publish/create-an-ad-campaign-for-your-app)
* [Zugreifen auf Analysedaten mit WindowsStore-Diensten](access-analytics-data-using-windows-store-services.md)



<!--HONumber=Nov16_HO1-->


