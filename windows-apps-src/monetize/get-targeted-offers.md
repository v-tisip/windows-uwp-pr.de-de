---
author: Xansky
ms.assetid: A4C6098B-6CB9-4FAF-B2EA-50B03D027FF1
description: Verwenden Sie diese Methode in der Microsoft Store-API für gezielte Angebote, um die gezielten Angebote abzurufen, die für den aktuellen Benutzer im Zusammenhang mit der aktuellen App verfügbar sind.
title: Abrufen gezielter Angebote
ms.author: mhopkins
ms.date: 10/10/2017
ms.topic: article
keywords: Windows10, UWP, Store-Dienste, Microsoft Store-API für gezielte Angebote, gezielte Angebote abrufen
ms.localizationpriority: medium
ms.openlocfilehash: 87d59a4b5dabbc76c231e84034d701fccfe36fcf
ms.sourcegitcommit: e814a13978f33654d8e995584f4b047cb53e0aef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "6043230"
---
# <a name="get-targeted-offers"></a>Abrufen gezielter Angebote

Verwenden Sie diese Methode, um die gezielten Angebote abzurufen, die für den aktuellen Benutzer verfügbar sind– basierend darauf, ob der Benutzer zum Kundensegment für das gezielte Angebot gehört. Weitere Informationen finden Sie unter [Verwalten gezielter Angebote mithilfe von Store-Diensten](manage-targeted-offers-using-windows-store-services.md).

## <a name="prerequisites"></a>Voraussetzungen

Um diese Methode zu verwenden, müssen Sie zunächst [ein Microsoft-Kontotoken abrufen](manage-targeted-offers-using-windows-store-services.md#obtain-a-microsoft-account-token), und zwar für den aktuell angemeldeten Benutzer Ihrer App. Sie müssen bei dieser Methode das Token an den ```Authorization```-Anforderungsheader übergeben. Dieses Token wird vom Store verwendet, um gezielte Angebote für den aktuellen Benutzer abzurufen.

## <a name="request"></a>Anforderung


### <a name="request-syntax"></a>Anforderungssyntax

| Methode | Anforderungs-URI                                                                |
|--------|----------------------------------------------------------------------------|
| GET    | ```https://manage.devcenter.microsoft.com/v2.0/my/storeoffers/user``` |


### <a name="request-header"></a>Anforderungsheader

| Header        | Typ   | Beschreibung  |
|---------------|--------|--------------|
| Autorisierung | String | Erforderlich. Das Microsoft-Kontotoken für den aktuell angemeldeten Benutzer Ihrer App im Format **Bearer**&lt;*-Token*&gt;. |


### <a name="request-parameters"></a>Anforderungsparameter

Diese Methode hat keinen URI oder Anforderungsparameter.

### <a name="request-example"></a>Anforderungsbeispiel

```syntax
GET https://manage.devcenter.microsoft.com/v2.0/my/storeoffers/user HTTP/1.1
Authorization: Bearer <Microsoft Account token>
```

## <a name="response"></a>Antwort

Diese Methode gibt einen Antworttext im JSON-Format zurück, der ein Array mit Objekten und den folgenden Feldern enthält. Jedes Objekt im Array stellt gezielte Angebote dar, die für den angegebenen Kunden im Rahmen eines bestimmten Kundensegments verfügbar sind.

| Feld      | Typ   | Beschreibung         |
|------------|--------|------------------|
| Angebote      | Array  | Ein Array mit Produkt-IDs für die Add-Ons, die den gezielten Angeboten zugeordnet sind, die für den aktuellen Benutzer verfügbar sind. Diese Produkt-IDs werden in der Seite **gezielte Angebote** für Ihre app im Partner Center angegeben.            |
| trackingId  | String | Eine GUID, mit der Sie optional das gezielte Angebot in Ihrem eigenen Code oder Diensten nachverfolgen können. |


### <a name="example"></a>Beispiel

Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.

```json
[
  {
    "offers": [
      "10x gold coins",
      "100x gold coins"
    ],
    "trackingId": "5de5dd29-6dce-4e68-b45e-d8ee6c2cd203"
  }
]
```

## <a name="related-topics"></a>Verwandte Themen

* [Verwalten von gezielten Angeboten mithilfe von Store-Diensten](manage-targeted-offers-using-windows-store-services.md)

 

 
