---
author: Xansky
ms.assetid: 038903d6-efab-4da6-96b5-046c7431e6e7
description: Verwenden Sie diese Methode in der Microsoft Store-Rezensions-API zum Senden von Antworten auf Rezensionen Ihrer App.
title: Antworten auf Rezensionen übermitteln
ms.author: mhopkins
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP, Store-Dienste, Microsoft Store-Rezensions-API, Add-On-Käufe
ms.localizationpriority: medium
ms.openlocfilehash: 8a8a336d477e7d66222632821f0fa0855faae6f7
ms.sourcegitcommit: f2c9a050a9137a473f28b613968d5782866142c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2018
ms.locfileid: "6275358"
---
# <a name="submit-responses-to-reviews"></a>Antworten auf Rezensionen übermitteln


Verwenden Sie diese Methode in der Microsoft Store-Rezensions-API, um Antworten auf Rezensionen Ihrer App zu senden. Wenn Sie diese Methode aufrufen, müssen Sie die IDs der Rezensionen angeben, auf die Sie antworten möchten. Rezensions-IDs finden Sie in den Antwortdaten der Methode [Abrufen von App-Rezensionen](get-app-reviews.md) der Microsoft Store-Analyse-API und unter [Offlinedownload](../publish/download-analytic-reports.md) im Bericht [Rezensionen](../publish/reviews-report.md).

Beim Übermitteln von Rezensionen können Kunden festlegen, dass sie keine Antworten auf ihre Rezension erhalten möchten. Wenn Sie versuchen, auf eine Rezension zu antworten, für die der Kunde ausgewählt hat, keine Antworten zu erhalten, wird im Antworttext dieser Methode angegeben, dass der Antwortversuch fehlgeschlagen ist. Vor dem Aufrufen dieser Methode können Sie mit der Methode [Antwortinformationen für App-Rezensionen abrufen](get-response-info-for-app-reviews.md) ermitteln, ob Sie auf eine bestimmte Rezension antworten dürfen.

> [!NOTE]
> Zusätzlich zur Verwendung dieser Methode zum programmgesteuerten reagieren auf Rezensionen können Sie alternativ auf Rezensionen [mithilfe von Partner Center](../publish/respond-to-customer-reviews.md)reagieren.

## <a name="prerequisites"></a>Voraussetzungen

Um diese Methode zu verwenden, sind die folgenden Schritte erforderlich:

* Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](respond-to-reviews-using-windows-store-services.md#prerequisites) für die Microsoft Store-Rezensions-API.
* [Rufen Sie ein AzureAD-Zugriffstoken ab](respond-to-reviews-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird. Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft. Wenn das Token abgelaufen ist, können Sie ein neues abrufen.
* Rufen Sie die IDs der Rezensionen ab, auf die Sie antworten möchten. Rezensions-IDs finden Sie in den Antwortdaten der Methode [Abrufen von App-Rezensionen](get-app-reviews.md) der Microsoft Store-Analyse-API und unter [Offlinedownload](../publish/download-analytic-reports.md) im Bericht [Rezensionen](../publish/reviews-report.md).

## <a name="request"></a>Anforderung

### <a name="request-syntax"></a>Anforderungssyntax

| Methode | Anforderungs-URI                                                      |
|--------|------------------------------------------------------------------|
| POST    | ```https://manage.devcenter.microsoft.com/v1.0/my/reviews/responses``` |


### <a name="request-header"></a>Anforderungsheader

| Header        | Typ   | Beschreibung                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| Autorisierung | String | Erforderlich. Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;. |


### <a name="request-parameters"></a>Anforderungsparameter

Diese Methode hat keine Anforderungsparameter.


### <a name="request-body"></a>Anforderungstext

Der Anforderungstext hat folgende Werte:

| Wert        | Typ   | Beschreibung                                                                 |
|---------------|--------|-----------------------------------------|
| Responses | Array | Ein Array von Objekten, die die Antwortdaten enthalten, die Sie senden möchten. Weitere Informationen zu den Daten in den einzelnen Objekten finden Sie in der folgenden Tabelle. |


Jedes Objekt im *Responses*-Array enthält die folgenden Werte:

| Wert        | Typ   | Beschreibung           |  Erforderlich  |
|---------------|--------|-----------------------------|-----|
| ApplicationId | String |  Die Store-ID der App, auf deren Rezension Sie antworten möchten. Die Store-ID ist auf der [Seite App-Identität](../publish/view-app-identity-details.md) des Partner Center verfügbar. Beispiel für eine Store-ID: 9WZDNCRFJ3Q8.   |  Ja  |
| ReviewId | String |  Die ID der Rezension, auf die Sie antworten möchten (dies ist eine GUID). Rezensions-IDs finden Sie in den Antwortdaten der Methode [Abrufen von App-Rezensionen](get-app-reviews.md) der Microsoft Store-Analyse-API und unter [Offlinedownload](../publish/download-analytic-reports.md) im Bericht [Rezensionen](../publish/reviews-report.md).   |  Ja  |
| ResponseText | String | Die Antwort, die Sie senden möchten. Ihre Antwort muss [diesen Richtlinien](../publish/respond-to-customer-reviews.md#guidelines-for-responses) entsprechen.   |  Ja  |
| SupportEmail | String | Die Support-E-Mail-Adresse Ihrer App, über die der Kunde Sie direkt kontaktieren kann. Dies muss eine gültige E-Mail-Adresse sein.     |  Ja  |
| IsPublic | Boolean |  Wenn Sie auf **"true"** angeben, wird Ihre Antwort im Store-Eintrag, direkt unter der Rezension des Kunden, Ihre app angezeigt wird und für alle Kunden sichtbar. Bei Angabe von **"false",** und der Benutzer noch nicht den Empfang von e-Mail-Antworten zugelassen wird Ihre Antwort an den Kunden per e-Mail gesendet werden, und es wird nicht für andere Kunden im Store-Eintrag Ihrer app sichtbar sein. Wenn Sie angeben, **"false",** und der Benutzer den Empfang von Antworten e-Mail entschieden hat, wird ein Fehler zurückgegeben.   |  Ja  |


### <a name="request-example"></a>Anforderungsbeispiel

Im folgenden Beispiel wird gezeigt, wie diese Methode verwendet wird, um Antworten auf mehrere Rezensionen zu senden.

```json
POST https://manage.devcenter.microsoft.com/v1.0/my/reviews/responses HTTP/1.1
Authorization: Bearer <your access token>
Content-Type: application/json
{
  "Responses": [
    {
      "ApplicationId": "9WZDNCRFJ3Q8",
      "ReviewId": "6be543ff-1c9c-4534-aced-af8b4fbe0316",
      "ResponseText": "Thank you for pointing out this bug. I fixed it and published an update, you should have the fix soon",
      "SupportEmail": "support@contoso.com",
      "IsPublic": "true"
    },
    {
      "ApplicationId": "9NBLGGH1RP08",
      "ReviewId": "80c9671a-96c2-4278-bcbc-be0ce5a32a7c",
      "ResponseText": "Thank you for submitting your review. Can you tell more about what you were doing in the app when it froze? Thanks very much for your help.",
      "SupportEmail": "support@contoso.com",
      "IsPublic": "false"
    }
  ]
}
```

## <a name="response"></a>Antwort

### <a name="response-body"></a>Antworttext

| Wert        | Typ   | Beschreibung            |
|---------------|--------|---------------------|
| Result | Array | Ein Array von Objekten, die Daten über jede Antwort enthalten, die Sie gesendet haben. Weitere Informationen zu den Daten in den einzelnen Objekten finden Sie in der folgenden Tabelle.  |


Jedes Objekt im *Result*-Array enthält die folgenden Werte:

| Wert        | Typ   | Beschreibung                                                                 |
|---------------|--------|-----------------------------------------------|
| ApplicationId | String |  Die Store-ID der App, auf deren Rezension Sie geantwortet haben. Beispiel für eine Store-ID: 9WZDNCRFJ3Q8.   |
| ReviewId | String |  Die ID der Rezension, auf die Sie geantwortet haben. Dies ist eine GUID.   |
| Successful | String | Der Wert **true** gibt an, dass Ihre Antwort erfolgreich gesendet wurde. Der Wert **false** gibt an, dass Ihre Antwort nicht erfolgreich war.    |
| FailureReason | String | Wenn **Successful** **false** ist, dann enthält dieser Wert einen Grund für den Fehler. Wenn **Successful** **true** ist, dann ist dieser Wert leer.      |


### <a name="response-example"></a>Antwortbeispiel

Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.

```json
{
  "Result": [
    {
      "ApplicationId": "9WZDNCRFJ3Q8",
      "ReviewId": "6be543ff-1c9c-4534-aced-af8b4fbe0316",
      "Successful": "true",
      "FailureReason": ""
    },
    {
      "ApplicationId": "9NBLGGH1RP08",
      "ReviewId": "80c9671a-96c2-4278-bcbc-be0ce5a32a7c",
      "Successful": "false",
      "FailureReason": "No Permission"
    }
  ]
}
```

## <a name="related-topics"></a>Verwandte Themen

* [Reagieren Sie auf kundenrezensionen über Partner Center](../publish/respond-to-customer-reviews.md)
* [Antworten auf Rezensionen mit Microsoft Store-Diensten](respond-to-reviews-using-windows-store-services.md)
* [Abrufen von Antwortinformationen für App-Rezensionen](get-response-info-for-app-reviews.md)
* [Abrufen von App-Rezensionen](get-app-reviews.md)
