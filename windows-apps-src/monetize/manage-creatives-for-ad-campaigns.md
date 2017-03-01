---
author: mcleanbyron
ms.assetid: c5246681-82c7-44df-87e1-a84a926e6496
description: "Verwenden Sie diese Methode in der Windows Store-Werbungs-API, um Werbemittel für Werbeanzeigenkampagnen zu verwalten."
title: "Verwalten von Werbemitteln für Anzeigenkampagnen"
ms.author: mcleans
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows 10, UWP, Windows Store Werbungs-API, Anzeigenkampagnen"
translationtype: Human Translation
ms.sourcegitcommit: 5645eee3dc2ef67b5263b08800b0f96eb8a0a7da
ms.openlocfilehash: 1e0755134a47b6acfb48f735ea56c4aa3c46be14
ms.lasthandoff: 02/08/2017

---

# <a name="manage-creatives-for-ad-campaigns"></a>Verwalten von Werbemitteln für Anzeigenkampagnen

Verwenden Sie diese Methoden in der Windows Store-Werbungs-API, um Ihre eigenen benutzerdefinierten Werbemittel in Werbeanzeigenkampagnen hochzuladen oder ein vorhandenes Werbemittel abzurufen. Ein Werbemittel kann einer oder mehreren Lieferpositionen sogar in verschiedenen Anzeigenkampagnen, sofern es sich immer um dieselbe App handelt, zugeordnet werden.

Weitere Informationen über die Beziehung zwischen Werbemitteln und Anzeigenkampagnen, Lieferpositionen und Zielgruppenprofilen finden Sie unter [Anzeigenkampagnen mit Windows Store-Diensten ausführen](run-ad-campaigns-using-windows-store-services.md#call-the-windows-store-promotions-api).

## <a name="prerequisites"></a>Voraussetzungen

Zur Verwendung dieser Methoden sind folgende Schritte erforderlich:

* Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](run-ad-campaigns-using-windows-store-services.md#prerequisites) für die Windows Store-Werbungs-API.
* [Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das in der Anforderungskopfzeile für diese Methoden verwendet wird. Nach Erhalt eines Zugriffstokens können Sie es 60 Minuten lang verwenden, bevor es abläuft. Wenn das Token abgelaufen ist, können Sie ein neues abrufen.

## <a name="request"></a>Anfordern

Diese Methoden haben die folgenden URIs.

| Methodentyp | Anforderungs-URI     |  Beschreibung  |
|--------|-----------------------------|---------------|
| POST   | ```https://manage.devcenter.microsoft.com/v1.0/my/promotion/creative``` |  Erstellt ein neues Werbemittel.  |
| GET    | ```https://manage.devcenter.microsoft.com/v1.0/my/promotion/creative/{creativeId}``` |  Ruft das durch *CreativeId* angegebene Werbemittel ab.  |

>**Hinweis:**&nbsp;&nbsp;Diese API unterstützt derzeit keine PUT-Methode.

<span/> 
### <a name="header"></a>Kopfzeile

| Kopfzeile        | Typ   | Beschreibung         |
|---------------|--------|---------------------|
| Autorisierung | Zeichenfolge | Erforderlich. Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*-Token*&gt;. |
| Tracking-ID   | GUID   | Optional. Eine ID, die den Abfrageablauf verfolgt.                                  |


<span/>
### <a name="request-body"></a>Anforderungstext

Die POST-Methode erfordert einen JSON-Anforderungstext mit den erforderlichen Feldern für ein [Werbemittel](#creative)-Objekt.

<span/>
### <a name="request-examples"></a>Anforderungsbeispiele

Im folgenden Beispiel wird veranschaulicht, wie die POST-Methode zum Erstellen eines Werbemittels aufgerufen wird. In diesem Beispiel wurde der Wert *content* aus Platzgründen verkürzt.

```json
POST https://manage.devcenter.microsoft.com/v1.0/my/promotion/creative HTTP/1.1
Authorization: Bearer <your access token>

{
  "name": "Contoso App Campaign - Creative 1",
  "content": "data:image/jpeg;base64,/9j/4AAQSkZJRgABAQEAAQABAAD/2wBDAAgGB...other base64 data shortened for brevity...",
  "height": 80,
  "width": 480,
  "imageAttributes":
  {
    "imageExtension": "PNG"
  }
}
```

Im folgenden Beispiel wird veranschaulicht, wie die GET-Methode zum Abrufen eines Werbemittels aufgerufen wird.

```json
GET https://manage.devcenter.microsoft.com/v1.0/my/promotion/creative/106851  HTTP/1.1
Authorization: Bearer <your access token>
```

<span/>
## <a name="response"></a>Antwort

Diese Methoden geben ein JSON-Antworttext mit einem [Creative](#creative)-Objekt zurück, das Informationen über das Werbemittel enthält, die erstellt oder abgerufen wurden. Das folgende Beispiel zeigt einen Antworttext für diese Methoden. In diesem Beispiel wurde der Wert *content* aus Platzgründen verkürzt.

```json
{
    "Data": {
        "id": 106126,
        "name": "Contoso App Campaign - Creative 2",
        "content": "data:image/jpeg;base64,/9j/4AAQSkZJRgABAQEAAQABAAD/2wBDAAgGB...other base64 data shortened for brevity...",
        "height": 50,
        "width": 300,
        "format": "Banner",
        "imageAttributes":
        {
          "imageExtension": "PNG"
        },
        "storeProductId": "9nblggh42cfd"
    }
}
```

<span id="creative"/>
## <a name="creative-object"></a>Kreative-Objekt

Die Anforderungs- und Antworttexte für diese Methoden enthalten die folgenden Felder. Die folgende Tabelle zeigt, welche Felder schreibgeschützt sind (d. h. sie können in der PUT-Methode nicht geändert werden) und welche Felder in dem Anforderungstext für die POST-Methode erforderlich sind.

| Feld        | Typ   |  Beschreibung      |  Schreibgeschützt  | Standard  |  Erforderlich für POST |  
|--------------|--------|---------------|------|-------------|------------|
|  ID   |  Ganzzahl   |  Die ID des Werbemittels.     |   Ja    |      |    Nein   |       
|  Name   |  Zeichenfolge   |   Name des Werbemittels.    |    Nein   |      |  Ja     |       
|  content   |  Zeichenfolge   |  Der Inhalt des Werbemittel-Image im Base64-codierten Format.     |  Nein     |      |   Ja    |       
|  height   |  Ganzzahl   |   Die Höhe des Werbemittels.    |    Nein    |      |   Ja    |       
|  width   |  Ganzzahl   |  Die Breite des Werbemittels.     |  Nein    |     |    Ja   |       
|  landingUrl   |  Zeichenfolge   |  Die URL der Startseite für das Werbemittel (dieser Wert muss eine gültige URI sein).     |  Nein    |     |   Ja    |       
|  Format   |  Zeichenfolge   |   Das Anzeigenformat. Derzeit wird als einziger Wert **Banner**. unterstützt.    |   Nein    |  Banner   |  Nein     |       
|  imageAttributes   | [ImageAttributes](#image-attributes)    |   Stellt Attribute für das Werbemittel bereit.     |   Nein    |      |   Ja    |       
|  storeProductId   |  Zeichenfolge   |   Die [Store-ID](in-app-purchases-and-trials.md#store-ids) der App, der diese Anzeigenkampagne zugeordnet ist. Ein Beispiel für eine Store-ID eines Produkts ist 9nblggh42cfd.    |   Nein    |    |  Nein     |   |  

<span id="image-attributes"/>
## <a name="imageattributes-object"></a>ImageAttributes-Objekt

| Feld        | Typ   |  Beschreibung      |  Schreibgeschützt  | Standardwert  | Erforderlich für POST |  
|--------------|--------|---------------|------|-------------|------------|
|  imageExtension   |   Zeichenfolge  |   Die Bilderweiterung (z. B. PNG oder JPG).    |    Nein   |      |   Ja    |       |


## <a name="related-topics"></a>Verwandte Themen

* [Durchführen von Anzeigenkampagnen mit Windows Store-Diensten](run-ad-campaigns-using-windows-store-services.md)
* [Verwalten von Anzeigenkampagnen](manage-ad-campaigns.md)
* [Verwalten von Lieferpositionen für Anzeigenkampagnen](manage-delivery-lines-for-ad-campaigns.md)
* [Verwalten von Zielgruppenprofilen für Anzeigenkampagnen](manage-targeting-profiles-for-ad-campaigns.md)
* [Abrufen der Leistungsdaten einer Anzeigenkampagne](get-ad-campaign-performance-data.md)

