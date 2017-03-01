---
author: mcleanbyron
ms.assetid: dc632a4c-ce48-400b-8e6e-1dddbd13afff
description: "Verwenden Sie diese Methode in der Windows Store-Werbungs-API, um Lieferpositionen für Werbeanzeigenkampagnen zu verwalten."
title: "Verwalten von Lieferpositionen für Anzeigenkampagnen"
ms.author: mcleans
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows 10, UWP, Windows Store Werbungs-API, Anzeigenkampagnen"
translationtype: Human Translation
ms.sourcegitcommit: 5645eee3dc2ef67b5263b08800b0f96eb8a0a7da
ms.openlocfilehash: 5f9ede6a2e645a644e4650f3af7e5476bd52dd53
ms.lasthandoff: 02/08/2017

---

# <a name="manage-delivery-lines-for-ad-campaigns"></a>Verwalten von Lieferpositionen für Anzeigenkampagnen

Erstellen Sie mit diesen Methoden in Windows Store-Angebote API eine oder mehrere *Lieferpositionen*, um Inventar zu kaufen und Ihre Anzeigen für eine Werbekampagne zu übermitteln. Für jede Lieferposition können Sie Zielgruppen und Ihren Angebotspreis festlegen sowie entscheiden, wie viel Sie ausgeben möchten, indem Sie ein Budget festlegen und Verknüpfungen zu den Werbemitteln, die Sie verwenden möchten, erstellen.

Weitere Informationen über die Beziehung zwischen Lieferpositionen und Anzeigenkampagnen, Zielgruppenprofilen und Werbemitteln finden Sie unter [Anzeigenkampagnen mit Windows Store-Diensten ausführen](run-ad-campaigns-using-windows-store-services.md#call-the-windows-store-promotions-api).

## <a name="prerequisites"></a>Voraussetzungen

Zur Verwendung dieser Methoden sind folgende Schritte erforderlich:

* Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](run-ad-campaigns-using-windows-store-services.md#prerequisites) für die Windows Store-Werbungs-API.
* [Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das in der Anforderungskopfzeile für diese Methoden verwendet wird. Nach Erhalt eines Zugriffstokens können Sie es 60 Minuten lang verwenden, bevor es abläuft. Wenn das Token abgelaufen ist, können Sie ein neues abrufen.

## <a name="request"></a>Anfordern

Diese Methoden haben die folgenden URIs.

| Methodentyp | Anforderungs-URI         |  Beschreibung  |
|--------|---------------------------|---------------|
| POST   | ```https://manage.devcenter.microsoft.com/v1.0/my/promotion/line``` |  Erstellt eine neue Übermittlung Linie.  |
| PUT    | ```https://manage.devcenter.microsoft.com/v1.0/my/promotion/line/{lineId}``` |  Ändert die durch *lineId* angegebene Lieferposition.  |
| GET    | ```https://manage.devcenter.microsoft.com/v1.0/my/promotion/line/{lineId}``` |  Ändert die durch *lineId* angegebene Lieferposition.  |

<span/> 
### <a name="header"></a>Kopfzeile

| Kopfzeile        | Typ   | Beschreibung         |
|---------------|--------|---------------------|
| Autorisierung | Zeichenfolge | Erforderlich. Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*-Token*&gt;. |
| Tracking-ID   | GUID   | Optional. Eine ID, die den Abfrageablauf verfolgt.                                  |

<span/>
### <a name="request-body"></a>Anforderungstext

Die POST- und PUT-Methoden erfordern einen JSON-Anforderungstext mit den erforderlichen Feldern für ein [Lieferpositionen](#line)-Objekt und alle zusätzlichen Felder, die Sie festlegen oder ändern möchten.
 
<span/>
### <a name="request-examples"></a>Anforderungsbeispiele

Im folgenden Beispiel wird veranschaulicht, wie die POST-Methode zum Erstellen einer Lieferposition aufgerufen wird.

```json
POST https://manage.devcenter.microsoft.com/v1.0/my/promotion/line HTTP/1.1
Authorization: Bearer <your access token>

{
    "name": "Contoso App Campaign - Paid Line",
    "configuredStatus": "Active",
    "startDateTime": "2017-01-19T12:09:34Z",
    "endDateTime": "2017-01-31T23:59:59Z",
    "bidAmount": 0.4,
    "dailyBudget": 20,
    "targetProfileId": {
        "id": 310021746
    },
    "creatives": [
        {
            "id": 106851
        }
    ],
    "campaignId": 31043481,
    "minMinutesPerImp ": 1
}
```

Im folgenden Beispiel wird veranschaulicht, wie die GET-Methode zum Abrufen einer Lieferposition aufgerufen wird.

```json
GET https://manage.devcenter.microsoft.com/v1.0/my/promotion/line/31019990  HTTP/1.1
Authorization: Bearer <your access token>
```

<span/> 
## <a name="response"></a>Antwort

Diese Methoden geben einen JSON-Antworttext mit einem [Lieferpositionen](#line)-Objekt zurück, das Informationen über die Lieferposition enthält, die erstellt, aktualisiert oder abgerufen wurde. Das folgende Beispiel zeigt einen Antworttext für diese Methoden.

```json
{
    "Data": {
        "id": 31043476,
        "name": "Contoso App Campaign - Paid Line",
        "configuredStatus": "Active",
        "effectiveStatus": "Active",
        "effectiveStatusReasons": [
            "{\"ValidationStatusReasons\":null}"
        ],
        "startDateTime": "2017-01-19T12:09:34Z",
        "endDateTime": "2017-01-31T23:59:59Z",
        "createdDateTime": "2017-01-17T10:28:34Z",
        "bidType": "CPM",
        "bidAmount": 0.4,
        "dailyBudget": 20,
        "targetProfileId": {
            "id": 310021746
        },
        "creatives": [
            {
                "id": 106126
            }
        ],
        "campaignId": 31043481,
        "minMinutesPerImp ": 1,
        "pacingType ": "SpendEvenly",
        "currencyId ": 732
    }
}

```

<span id="line"/>
## <a name="delivery-line-object"></a>Lieferpositionen-Objekt

Die Anforderungs- und Antworttexte für diese Methoden enthalten die folgenden Felder. Die folgende Tabelle zeigt, welche Felder schreibgeschützt sind (d. h. sie können in der PUT-Methode nicht geändert werden) und welche Felder in dem Anforderungstext für die POST- oder PUT-Methode erforderlich sind.

| Feld        | Typ   |  Beschreibung      |  Schreibgeschützt  | Standard  | Erforderlich für POST/PUT |   
|--------------|--------|---------------|------|-------------|------------|
|  ID   |  Ganzzahl   |  Die ID der Lieferposition.     |   Ja    |      |  Nein      |    
|  Name   |  Zeichenfolge   |   Der Name der Lieferposition.    |    Nein   |      |  POST     |     
|  configuredStatus   |  Zeichenfolge   |  Einer der folgenden Werte, der den Status der vom Entwickler angegebenen Lieferposition angibt: <ul><li>**Aktiv**</li><li>**Inaktiv**</li></ul>     |  Nein     |      |   POST    |       
|  effectiveStatus   |  Zeichenfolge   |   Einer der folgenden Werte, der den effektiven Status der Lieferposition basierend auf der Systemüberprüfung angibt: <ul><li>**Aktiv**</li><li>**Inaktiv**</li><li>**Verarbeitung**</li><li>**Fehlgeschlagen**</li></ul>    |    Ja   |      |  Nein      |      
|  effectiveStatusReasons   |  Array   |  Einer oder mehrere der folgenden Werte, die den Grund für den effektive Status der Lieferposition angeben: <ul><li>**AdCreativesInactive**</li><li>**ValidationFailed**</li></ul>      |  Ja     |     |    Nein    |           
|  startDatetime   |  Zeichenfolge   |  Startdatum und -uhrzeit der Lieferposition im ISO 8601-Format. Dieser Wert kann nicht geändert werden, wenn er bereits in der Vergangenheit liegt.     |    Nein   |      |    POST, PUT     |
|  endDatetime   |  Zeichenfolge   |  Enddatum und -uhrzeit der Lieferposition im ISO 8601-Format. Dieser Wert kann nicht geändert werden, wenn er bereits in der Vergangenheit liegt.     |   Nein    |      |  POST, PUT     |
|  createdDatetime   |  Zeichenfolge   |  Erstellungsdatum und -uhrzeit der Lieferposition im ISO 8601-Format.      |    Ja   |      |  Nein      |
|  bidType   |  Zeichenfolge   |  Ein Wert, der den Angebotstyp der Lieferposition angibt. Derzeit wird als einziger Wert **CPM** unterstützt.      |    Nein   |  CPM    |  Nein     |
|  bidAmount   |  Dezimalzahl   |  Der Betrag für jede Anzeigenanforderung bieten verwendet werden.      |    Nein   |  Der durchschnittliche CPM-Wert basierend auf den Zielmärkten (dieser Wert wird in regelmäßigen Abständen überarbeitet).    |    Nein    |  
|  dailyBudget   |  Dezimalzahl   |  Das tägliche Budget für die Lieferposition. Entweder *DailyBudget* oder *lifetimeBudget* muss festgelegt werden.      |    Nein   |      |   POST, PUT (wenn *lifetimeBudget* nicht festgelegt ist)       |
|  lifetimeBudget   |  Dezimalzahl   |   Das Lebensdauer-Budget für die Lieferposition. Entweder lifetimeBudget* oder *dailyBudget* muss festgelegt werden.      |    Nein   |      |   POST, PUT (wenn *dailyBudget* nicht festgelegt ist)    |
|  targetingProfileId   |  Objekt   |  Objekt, das das [Zielgruppenprofil](manage-targeting-profiles-for-ad-campaigns.md#targeting-profile) identifiziert, das die Benutzer, Regionen und Bestandstypen beschreibt, die Sie für diese Lieferposition ansprechen möchten. Dieses Objekt umfasst ein einzelnes *ID*-Feld, das die ID des Zielgruppenprofils angibt.     |    Nein   |      |  Nein      |  
|  Werbemittel   |  Array   |  Ein oder mehrere Objekte, die die [Werbemittel](manage-creatives-for-ad-campaigns.md#creative) darstellen, die der Lieferposition zugeordnet sind. Jedes Objekt in diesem Feld umfasst ein einzelnes *ID*-Feld, das die ID eines Werbemittels angibt.      |    Nein   |      |   Nein     |  
|  campaignId   |  Ganzzahl   |  Die ID der übergeordneten Anzeigenkampagne.      |    Nein   |      |   Nein     |  
|  minMinutesPerImp   |  Ganzzahl   |  Gibt das minimale Zeitintervall (in Minuten) zwischen zwei Aufrufen von Anzeigen an, die demselben Benutzer dieser Lieferposition angezeigt werden.      |    Nein   |  4000    |  Nein      |  
|  pacingType   |  Zeichenfolge   |  Einer der folgenden Werte, die den Geschwindigkeitstyp angeben: <ul><li>**SpendEvenly**</li><li>**SpendAsFastAsPossible**</li></ul>      |    Nein   |  SpendEvenly    |  Nein      |
|  currencyId   |  Ganzzahl   |  Die ID der Währung der Kampagne.      |    Ja   |  Die Währung des Entwicklerkontos (Sie müssen dieses Feld nicht im POST- oder PUT-Aufrufen angeben)    |   Nein     |      |


## <a name="related-topics"></a>Verwandte Themen

* [Durchführen von Anzeigenkampagnen mit Windows Store-Diensten](run-ad-campaigns-using-windows-store-services.md)
* [Verwalten von Anzeigenkampagnen](manage-ad-campaigns.md)
* [Verwalten von Zielgruppenprofilen für Anzeigenkampagnen](manage-targeting-profiles-for-ad-campaigns.md)
* [Verwalten von Werbemitteln für Anzeigenkampagnen](manage-creatives-for-ad-campaigns.md)
* [Abrufen der Leistungsdaten einer Anzeigenkampagne](get-ad-campaign-performance-data.md)

