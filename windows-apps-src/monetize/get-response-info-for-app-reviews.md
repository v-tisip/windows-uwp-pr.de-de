---
author: Xansky
ms.assetid: fb6bb856-7a1b-4312-a602-f500646a3119
description: Verwenden Sie diese Methode der Microsoft Store-API für Rezensionen, um zu bestimmen, ob Sie auf eine bestimmte Rezension für eine bestimmte App oder auf alle Rezensionen für diese App antworten können.
title: Antwortinformationen für Rezensionen abrufen
ms.author: mhopkins
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Store-Dienste, Microsoft Store-API für Rezensionen, Antwortinformationen
ms.localizationpriority: medium
ms.openlocfilehash: 466455a5e8da9364206245f1e0ac10acfed07ee7
ms.sourcegitcommit: 93c0a60cf531c7d9fe7b00e7cf78df86906f9d6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2018
ms.locfileid: "7553996"
---
# <a name="get-response-info-for-reviews"></a>Antwortinformationen für Rezensionen abrufen

Wenn Sie programmgesteuert auf eine Kundenrezension zu Ihrer App antworten möchten, verwenden Sie diese Methode der Microsoft Store-API für Rezensionen, um zunächst zu ermitteln, ob Sie berechtigt sind, auf die Rezension zu antworten. Sie können nicht auf Rezensionen von Kunden antworten, die keine Antwort auf ihre Rezension erhalten möchten. Nachdem sichergestellt ist, dass Sie auf eine Rezension antworten können, verwenden Sie die Methode [Antworten auf App-Rezensionen senden](submit-responses-to-app-reviews.md), um programmgesteuert zu antworten.


## <a name="prerequisites"></a>Voraussetzungen

Zur Verwendung dieser Methode sind folgende Schritte erforderlich:

* Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](respond-to-reviews-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.
* [Rufen Sie ein Azure AD-Zugriffstoken ab](respond-to-reviews-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird. Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft. Wenn das Token abgelaufen ist, können Sie ein neues abrufen.
* Rufen Sie die ID der Rezension ab, für die Sie überprüfen möchten, ob Sie darauf antworten können. Rezensions-IDs finden Sie in den Antwortdaten der Methode [Abrufen von App-Rezensionen](get-app-reviews.md) der Microsoft Store-Analyse-API und unter [Offlinedownload](../publish/download-analytic-reports.md) im Bericht [Rezensionen](../publish/reviews-report.md).

## <a name="request"></a>Anforderung


### <a name="request-syntax"></a>Anforderungssyntax

| Methode | Anforderungs-URI                                                      |
|--------|------------------------------------------------------------------|
| GET    | ```https://manage.devcenter.microsoft.com/v1.0/my/reviews/{reviewId}/apps/{applicationId}/responses/info``` |


### <a name="request-header"></a>Anforderungsheader

| Header        | Typ   | Beschreibung                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| Autorisierung | String | Erforderlich. Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;. |


### <a name="request-parameters"></a>Anforderungsparameter

| Parameter        | Typ   | Beschreibung                                     |  Erforderlich  |
|---------------|--------|--------------------------------------------------|--------------|
| applicationId | string | Die Store-ID der App, welche die Rezension enthält, für die Sie bestimmen möchten, ob Sie antworten können. Die Store-ID ist auf der [Seite App-Identität](../publish/view-app-identity-details.md) im Partner Center verfügbar. Beispiel für eine Store-ID: 9WZDNCRFJ3Q8. |  Ja  |
| reviewId | string | Die ID der Rezension, auf die Sie antworten möchten (dies ist eine GUID). Rezensions-IDs finden Sie in den Antwortdaten der Methode [Abrufen von App-Rezensionen](get-app-reviews.md) der Microsoft Store-Analyse-API und unter [Offlinedownload](../publish/download-analytic-reports.md) im Bericht [Rezensionen](../publish/reviews-report.md). <br/>Wenn Sie diesen Parameter nicht angeben, wird im Antworttext für diese Methode stehen, ob Sie über Berechtigungen zum Beantworten von Rezensionen für die angegebene App verfügen. |  Nein  |


### <a name="request-example"></a>Anforderungsbeispiel

Das folgende Beispiel zeigt, wie Sie diese Methode verwenden, um festzustellen, ob auf eine bestimmte Rezension antworten können.

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/reviews/6be543ff-1c9c-4534-aced-af8b4fbe0316/apps/9WZDNCRFJ3Q8/responses/info HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a>Antwort


### <a name="response-body"></a>Antworttext

| Wert      | Typ   | Beschreibung    |  
|------------|--------|-----------------------|
| CanRespond      | Boolean  | Der Wert **true** gibt an, dass Sie auf die angegebene Rezension antworten können oder dass Sie berechtigt sind, auf eine beliebige Rezensionen für die angegebene App zu antworten. Andernfalls ist dieser Wert **false**.       |
| DefaultSupportEmail  | string |  Die von Ihrer App [unterstütze E-Mail-Adresse](../publish/enter-app-properties.md#support-contact-info) finden Sie im Store-Eintrag Ihrer App. Wenn Sie keine unterstützte E-Mail-Adresse angegeben haben, ist dieses Feld leer.    |

 
### <a name="response-example"></a>Antwortbeispiel

Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.

```json
{
  "CanRespond": true,
  "DefaultSupportEmail": "support@contoso.com"
}
```

## <a name="related-topics"></a>Verwandte Themen

* [Übermitteln von Antworten auf Rezensionen mithilfe der Microsoft Store-Analyse-API](submit-responses-to-app-reviews.md)
* [Reagieren Sie auf kundenrezensionen über Partner Center](../publish/respond-to-customer-reviews.md)
* [Antworten auf Rezensionen mit Microsoft Store-Diensten](respond-to-reviews-using-windows-store-services.md)
* [Abrufen von App-Rezensionen](get-app-reviews.md)
