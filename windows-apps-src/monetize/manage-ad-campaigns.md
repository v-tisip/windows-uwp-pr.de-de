---
author: mcleanbyron
ms.assetid: 7b07a6ca-4be1-497c-a901-0a2da3762555
description: Verwenden Sie diese Methode in der Windows Store-Angebots-API, um Werbeanzeigenkampagnen zu erstellen, zu bearbeiten und abzurufen.
title: Verwalten von Anzeigenkampagnen
ms.author: mcleans
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows 10, UWP, Windows Store Werbungs-API, Anzeigenkampagnen"
translationtype: Human Translation
ms.sourcegitcommit: 5645eee3dc2ef67b5263b08800b0f96eb8a0a7da
ms.openlocfilehash: bde9588176c1e52ccab169ad3f51ad15781e06ee
ms.lasthandoff: 02/08/2017

---

# <a name="manage-ad-campaigns"></a>Verwalten von Anzeigenkampagnen

Verwenden Sie diese Methoden in der [Windows Store-Angebots-API-](run-ad-campaigns-using-windows-store-services.md), um werbende Anzeigenkampagnen zu erstellen, zu bearbeiten und abzurufen. Jede Kampagne, die Sie erstellen, mit dieser Methode kann nur eine App zugeordnet werden.

>**Hinweis:**&nbsp;&nbsp;Sie können Anzeigenkampagnen auch über das Windows Dev Center-Dashboard erstellen und verwalten, und auf Kampagnen, die Sie programmgesteuert erstellen, können Sie im Dashboard zugreifen. Weitere Informationen zum Verwalten von Anzeigenkampagnen im Dashboard finden Sie unter [Erstellen einer Anzeigenkampagne für Ihre App](../publish/create-an-ad-campaign-for-your-app.md).

Wenn Sie eine Kampagne mit dieser Methode erstellen oder aktualisieren, rufen Sie in der Regel auch eine oder mehrere der folgenden Methoden zum Verwalten der *Lieferpositionen*, *Zielgruppenprofile*, und *Werbemittel* ab, die der Kampagne zugeordnet sind. Weitere Informationen über die Beziehung zwischen Kampagnen, Lieferpositionen, Zielgruppenprofilen und Werbemitteln finden Sie unter [Anzeigenkampagnen mit Windows Store-Diensten ausführen](run-ad-campaigns-using-windows-store-services.md#call-the-windows-store-promotions-api).

* [Verwalten von Lieferpositionen für Anzeigenkampagnen](manage-delivery-lines-for-ad-campaigns.md)
* [Verwalten von Zielgruppenprofilen für Anzeigenkampagnen](manage-targeting-profiles-for-ad-campaigns.md)
* [Verwalten von Werbemitteln für Anzeigenkampagnen](manage-creatives-for-ad-campaigns.md)

## <a name="prerequisites"></a>Voraussetzungen

Zur Verwendung dieser Methoden sind folgende Schritte erforderlich:

* Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](run-ad-campaigns-using-windows-store-services.md#prerequisites) für die Windows Store-Werbungs-API.
* [Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methoden verwendet wird. Nach Erhalt eines Zugriffstokens können Sie es 60 Minuten lang verwenden, bevor es abläuft. Wenn das Token abgelaufen ist, können Sie ein neues abrufen.

<span/> 
## <a name="request"></a>Anfordern

Diese Methoden haben die folgenden URIs.

| Methodentyp | Anforderungs-URI                                                      |  Beschreibung  |
|--------|------------------------------------------------------------------|---------------|
| POST   | ```https://manage.devcenter.microsoft.com/v1.0/my/promotion/campaign``` |  Erstellt eine neue Anzeigenkampagne.  |
| PUT    | ```https://manage.devcenter.microsoft.com/v1.0/my/promotion/campaign/{campaignId}``` |  Bearbeitet die mit der *Kampagnen-ID* näher bezeichnete Anzeigenkampagne.  |
| GET    | ```https://manage.devcenter.microsoft.com/v1.0/my/promotion/campaign/{campaignId}``` |  Ruft die mit der *Kampagnen-ID* näher bezeichnete Anzeigenkampagne ab.  |
| GET    | ```https://manage.devcenter.microsoft.com/v1.0/my/promotion/campaign``` |  Abfragen für Anzeigenkampagnen. Siehe [Parameter](#parameters) Abschnitt zu den unterstützten Abfrageparametern.  |

<span/> 
### <a name="header"></a>Header

| Header        | Typ   | Beschreibung         |
|---------------|--------|---------------------|
| Autorisierung | String | Erforderlich. Das Azure AD-Zugriffstoken im Format **Bearer-** &lt;*Token*&gt;. |
| Tracking-ID   | GUID   | Optional. Eine ID, die den Abfrageablauf verfolgt.                                  |

<span id="parameters"/> 
### <a name="parameters"></a>Parameter

Die GET-Methode zum Abfragen für Anzeigenkampagnen unterstützt die folgenden optionalen Abfrageparameter.

| Name        | Typ   |  Beschreibung      |    
|-------------|--------|---------------|------|
| skip  |  int   | Die Anzahl der Zeilen, die in der Abfrage übersprungen werden sollen. Verwenden Sie diesen Parameter, um große Datensätze durchzublättern. Beispielsweise rufen „fetch=10“ und „skip=0“ die ersten 10 Datenzeilen ab, „top=10“ und „skip=10“ die nächsten 10 Datenzeilen usw.    |       
| fetch  |  int   | Die Anzahl der Datenzeilen, die in der Anforderung zurückgegeben werden sollen.    |       
| campaignSetSortColumn  |  Zeichenfolge   | Sortiert die Objekte der [Kampagne](#campaign) im Antworttext nach dem angegebenen Feld. Die Syntax lautet <em>CampaignSetSortColumn = field</em>, wobei der Parameter <em>field</em> eine der folgenden Zeichenfolgen sein kann:</p><ul><li><strong>ID</strong></li><li><strong>createdDateTime</strong></li></ul><p>Der Standardwert ist **createdDateTime**.     |     
| isDescending  |  Boolean   | Sortiert die Objekte der [Kampagne](#campaign) im Antworttext in absteigender oder aufsteigender Reihenfolge.   |         
| applicationId  |  Zeichenfolge   | Verwenden Sie diesen Wert, um nur die Anzeigenkampagnen zurückgegeben, die der App mit der angegebenen ID zugeordnet sind [Store-ID](in-app-purchases-and-trials.md#store-ids). Ein Beispiel für eine Store-ID eines Produkts ist 9nblggh42cfd.   |         
| Beschriftung  |  Zeichenfolge   | Verwenden Sie diesen Wert nur Anzeigenkampagnen zurückgegeben, die der angegebenen enthalten *Bezeichnung* in der [Kampagne](#campaign) Objekt.    |       |    

<span/>
### <a name="request-body"></a>Anforderungstext

Die POST und PUT-Methoden erfordern einen JSON-Anforderungstext mit den erforderlichen Feldern für ein Objekt einer [Kampagne](#campaign) und alle zusätzlichen Felder, die Sie festlegen oder ändern möchten.

<span/>
### <a name="request-examples"></a>Anforderungsbeispiele

Im folgenden Beispiel wird veranschaulicht, wie die POST-Methode zum Erstellen einer Anzeigenkampagne aufgerufen wird.

```json
POST https://manage.devcenter.microsoft.com/v1.0/my/promotion/campaign HTTP/1.1
Authorization: Bearer <your access token>

{
    "name": "Contoso App Campaign",
    "applicationId": "9nblggh42cfd",
    "configuredStatus": "Active",
    "objective": "DriveInstalls",
    "type": "Community"
}
```

Im folgenden Beispiel wird veranschaulicht, wie die GET-Methode zum Abrufen einer bestimmten Anzeigenkampagne aufgerufen wird.

```json
GET https://manage.devcenter.microsoft.com/v1.0/my/promotion/campaign/31043481  HTTP/1.1
Authorization: Bearer <your access token>
```

Im folgenden Beispiel wird veranschaulicht, wie die GET-Methode zur Abfrage einer nach dem Erstellungsdatum sortierten Gruppe von Anzeigenkampagnen aufgerufen wird.

```json
GET https://manage.devcenter.microsoft.com/v1.0/my/promotion/campaign?applicationId=9nblggh42cfd&fetch=100&skip=0&campaignSetSortColumn=createdDateTime HTTP/1.1
Authorization: Bearer <your access token>
```

<span/> 
## <a name="response"></a>Antwort

Diese Methoden geben je nach aufgerufener Methode einen JSON-Antworttext mit einem oder mehreren [Kampagne](#campaign)-Objekten zurück. Das folgende Beispiel zeigt eine Antworttext für die GET-Methode für eine bestimmte Kampagne.

```json
{
    "Data": {
        "id": 31043481,
        "name": "Contoso App Campaign",
        "createdDate": "2017-01-17T10:12:15Z",
        "applicationId": "9nblggh42cfd",
        "configuredStatus": "Active",
        "effectiveStatus": "Active",
        "effectiveStatusReasons": [
            "{\"ValidationStatusReasons\":null}"
        ],
        "labels": [],
        "objective": "DriveInstalls",
        "type": "Paid",
        "lines": [
            {
                "id": 31043476,
                "name": "Contoso App Campaign - Paid Line"
            }
        ]
    }
}
```

<span id="campaign"/>
## <a name="campaign-object"></a>Kampagnenobjekt

Die Anforderungs- und Antworttexte für diese Methoden enthalten die folgenden Felder. Die folgende Tabelle zeigt, welche Felder schreibgeschützt sind (d. h. sie können in der PUT-Methode nicht geändert werden) und welche Felder in dem Anforderungstext für die POST-Methode erforderlich sind.

| Feld        | Typ   |  Beschreibung      |  Schreibgeschützt  | Standard  | Erforderlich für POST |  
|--------------|--------|---------------|------|-------------|------------|
|  ID   |  Ganzzahl   |  Die ID der Anzeigenkampagne.     |   Ja.    |      |  Nein.     |       
|  Name   |  String   |   Der Name der Anzeigenkampagne.    |    Nein   |      |  Ja     |       
|  configuredStatus   |  String   |  Einer der folgenden Werte, der den Status der vom Entwickler angegebenen Anzeigenkampagne angibt: <ul><li>**Aktiv**</li><li>**Inaktiv**</li></ul>     |  Nein     |  Aktiv    |   Ja    |       
|  effectiveStatus   |  String   |   Einer der folgenden Werte, der den effektiven Status der Anzeigenkampagne basierend auf der Systemüberprüfung angibt: <ul><li>**Active**</li><li>**Inactive**</li><li>**Verarbeitung**</li></ul>    |    Ja   |      |   Nein      |       
|  effectiveStatusReasons   |  Array   |  Einer oder mehrere der folgenden Werte, die den Grund für den effektive Status der Anzeigenkampagne angeben: <ul><li>**AdCreativesInactive**</li><li>**BillingFailed**</li><li>**AdLinesInactive**</li><li>**ValidationFailed**</li><li>**Fehlgeschlagen**</li></ul>      |  Ja.     |     |    Nein.     |       
|  applicationId   |  String   |  Die [Store-ID](in-app-purchases-and-trials.md#store-ids) der App, der diese Anzeigenkampagne zugeordnet ist. Ein Beispiel für eine Store-ID eines Produkts ist 9nblggh42cfd.     |   Ja    |      |  Ja     |       
|  Beschriftungen   |  Array   |   Eine oder mehrere Zeichenfolgen, die benutzerdefinierte Beschriftungen für die Kampagne darstellen. Diese Beschriftungen werden für das Suchen und Kennzeichnen von Kampagnen verwendet.    |   Nein    |  Null    |    Nein     |       
|  Typ   | String    |  Einer der folgenden Werte, der den Kampagnentyp angibt: <ul><li>**Kostenpflichtig**</li><li>**Haus**</li><li>**Community**</li></ul>      |   Ja    |      |   Ja    |       
|  Ziel   |  String   |  Einer der folgenden Werte, der das Ziel der Kampagne angibt: <ul><li>**DriveInstall**</li><li>**DriveReengagement**</li><li>**DriveInAppPurchase**</li></ul>     |   Nein    |  DriveInstall    |   Ja    |       
|  Zeilen   |  Array   |   Ein oder mehrere Objekte, die die [Lieferpositionen](manage-delivery-lines-for-ad-campaigns.md#line) identifizieren, die der Kampagne zugeordnet sind. Jedes Objekt in diesem Feld umfasst ein Feld *ID* und *Name*, das die ID und den Namen der Lieferposition angibt.     |   Nein    |      |    Nein     |       
|  createdDate   |  String   |  Das Datum und die Uhrzeit, zu dem die Anzeigenkampagne erstellt wurde (im ISO 8601-Format).     |  Ja     |      |     Nein    |       |

## <a name="related-topics"></a>Verwandte Themen

* [Durchführen von Anzeigenkampagnen mit Windows Store-Diensten](run-ad-campaigns-using-windows-store-services.md)
* [Verwalten von Lieferpositionen für Anzeigenkampagnen](manage-delivery-lines-for-ad-campaigns.md)
* [Verwalten von Zielgruppenprofilen für Anzeigenkampagnen](manage-targeting-profiles-for-ad-campaigns.md)
* [Verwalten von Werbemitteln für Anzeigenkampagnen](manage-creatives-for-ad-campaigns.md)
* [Abrufen der Leistungsdaten einer Anzeigenkampagne](get-ad-campaign-performance-data.md)

