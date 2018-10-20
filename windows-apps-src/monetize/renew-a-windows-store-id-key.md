---
author: Xansky
ms.assetid: 3569C505-8D8C-4D85-B383-4839F13B2466
description: Verwenden Sie diese Microsoft zum Verlängern eines Microsoft Store-Schlüssels.
title: Verlängern eines Microsoft Store-ID-Schlüssels
ms.author: mhopkins
ms.date: 03/16/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Microsoft Store-Sammlungs-API, Microsoft Store-Einkaufs-API, Microsoft Store-ID-Schlüssel, verlängern
ms.localizationpriority: medium
ms.openlocfilehash: 70bda5022e52c0b18a43563a0492bd56d09b88a0
ms.sourcegitcommit: 72835733ec429a5deb6a11da4112336746e5e9cf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/20/2018
ms.locfileid: "5170029"
---
# <a name="renew-a-microsoft-store-id-key"></a>Verlängern eines Microsoft Store-ID-Schlüssels


Verwenden Sie diese Microsoft zum Verlängern eines Microsoft Store-Schlüssels. Wenn Sie einen [Microsoft Store-ID-Schlüssel generieren](view-and-grant-products-from-a-service.md#step-4), ist dieser 90Tage lang gültig. Nach Ablauf des Schlüssels können Sie anhand des abgelaufenen Schlüssels einen neuen Schlüssel aushandeln, indem Sie diese Methode anwenden.

## <a name="prerequisites"></a>Voraussetzungen


Zur Verwendung dieser Methode benötigen Sie:

* Ein AzureAD-Zugriffstoken, das mit dem Zielgruppen-URI `https://onestore.microsoft.com` erstellt wurde.
* Ein abgelaufener MicrosoftStore-ID-Schlüssel, der [aus clientseitigem Code in Ihrer App generiert wurde](view-and-grant-products-from-a-service.md#step-4).

Weitere Informationen finden Sie unter [Verwalten von Produktansprüchen aus einem Dienst](view-and-grant-products-from-a-service.md).

## <a name="request"></a>Anforderung

### <a name="request-syntax"></a>Anforderungssyntax

| Schlüsseltyp    | Methode | Anforderungs-URI                                              |
|-------------|--------|----------------------------------------------------------|
| Sammlungen | POST   | ```https://collections.mp.microsoft.com/v6.0/b2b/keys/renew``` |
| Einkauf    | POST   | ```https://purchase.mp.microsoft.com/v6.0/b2b/keys/renew```    |


### <a name="request-header"></a>Anforderungsheader

| Header         | Typ   | Beschreibung                                                                                           |
|----------------|--------|-------------------------------------------------------------------------------------------------------|
| Host           | string | Muss auf den Wert **collections.mp.microsoft.com** oder **purchase.mp.microsoft.com** festgelegt werden.           |
| Content-Length | number | Die Länge des Anforderungstexts.                                                                       |
| Inhaltstyp   | string | Gibt den Anforderungs- und Antworttyp an. Derzeit wird als einziger Wert **application/json** unterstützt. |


### <a name="request-body"></a>Anforderungstext

| Parameter     | Typ   | Beschreibung                       | Erforderlich |
|---------------|--------|-----------------------------------|----------|
| serviceTicket | string | Das Azure AD-Zugriffstoken.        | Ja      |
| key           | string | Der abgelaufene Microsoft Store-ID-Schlüssel. | Ja       |


### <a name="request-example"></a>Anforderungsbeispiel

```syntax
POST https://collections.mp.microsoft.com/v6.0/b2b/keys/renew HTTP/1.1
Content-Length: 2774
Content-Type: application/json
Host: collections.mp.microsoft.com

{
    "serviceTicket": "eyJ0eXAiOiJKV1QiLCJhb….",
    "Key": "eyJ0eXAiOiJKV1QiLCJhbG…."
}
```

## <a name="response"></a>Antwort


### <a name="response-body"></a>Antworttext

| Parameter | Typ   | Beschreibung                                                                                                            |
|-----------|--------|------------------------------------------------------------------------------------------------------------------------|
| key       | string | Der aktualisierte Microsoft Store-Schlüssel kann dann für zukünftige Aufrufe der Sammlungs- oder Einkaufs-API von Microsoft Store verwendet werden. |


### <a name="response-example"></a>Antwortbeispiel

```syntax
HTTP/1.1 200 OK
Content-Length: 1646
Content-Type: application/json
MS-CorrelationId: bfebe80c-ff89-4c4b-8897-67b45b916e47
MS-RequestId: 1b5fa630-d672-4971-b2c0-3713f4ea6c85
MS-CV: xu2HW6SrSkyfHyFh.0.0
MS-ServerId: 030011428
Date: Tue, 13 Sep 2015 07:31:12 GMT

{
    "key":"eyJ0eXAi….."
}
```

## <a name="error-codes"></a>Fehlercodes


| Code | Fehler        | Interner Fehlercode           | Beschreibung   |
|------|--------------|----------------------------|---------------|
| 401  | Nicht autorisiert | AuthenticationTokenInvalid | Das Azure AD-Zugriffstoken ist ungültig. In einigen Fällen enthalten die Details zu ServiceError weitere Informationen, z. B. wenn das Token abgelaufen ist oder der *appid*-Anspruch fehlt. |
| 401  | Nicht autorisiert | InconsistentClientId       | Der *clientId*-Anspruch im Microsoft Store-ID-Schlüssel und der *appid*-Anspruch im Azure AD-Zugriffstoken stimmen nicht überein.                                                                     |


## <a name="related-topics"></a>Verwandte Themen


* [Verwalten von Produktansprüchen aus einem Dienst](view-and-grant-products-from-a-service.md)
* [Produktabfrage](query-for-products.md)
* [Melden von Verbrauchsprodukten als erfüllt](report-consumable-products-as-fulfilled.md)
* [Gewähren kostenloser Produkte](grant-free-products.md)
