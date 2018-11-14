---
author: Xansky
description: Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um die stapelüberwachung für einen Fehler in Ihrer Xbox One Spiel abzurufen.
title: Abrufen der stapelüberwachung für einen Fehler in Ihrer Xbox One-Spiele
ms.author: mhopkins
ms.date: 11/06/2018
ms.topic: article
keywords: Windows10, UWP, Store-Dienste, Microsoft Store-Analyse-API, Stapelüberwachung, Fehler
ms.localizationpriority: medium
ms.openlocfilehash: df3af90bda9d972a891dce67730f8f320b7607c1
ms.sourcegitcommit: 71e8eae5c077a7740e5606298951bb78fc42b22c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/14/2018
ms.locfileid: "6672917"
---
# <a name="get-the-stack-trace-for-an-error-in-your-xbox-one-game"></a>Abrufen der stapelüberwachung für einen Fehler in Ihrer Xbox One-Spiele

Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, die stapelüberwachung für einen Fehler in Ihrer Xbox One Spiel abzurufen, die das über das Xbox-Portal (XDP) und im XDP Analytics Dev Center-Dashboard verfügbar ist. Diese Methode kann nur die Stapelüberwachung für einen Fehler herunterladen, die in den letzten 30Tagen aufgetreten ist.

Bevor Sie diese Methode verwenden können, müssen Sie zuerst die Methode zum [Abrufen von Details zu einem Fehler in Ihrer Xbox One Spiel](get-details-for-an-error-in-your-xbox-one-game.md) verwenden, um die ID der CAB-Datei abzurufen, die mit dem Fehler verknüpft ist, für die Sie die stapelüberwachung abrufen möchten.

## <a name="prerequisites"></a>Voraussetzungen


Zur Verwendung dieser Methode sind folgende Schritte erforderlich:

* Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.
* [Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird. Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft. Wenn das Token abgelaufen ist, können Sie ein neues abrufen.
* Rufen Sie die ID der CAB-Datei an, die mit dem Fehler verknüpft ist, für den Sie die Stapelüberwachung abrufen möchten. Um diese ID zu erhalten, verwenden Sie die [Details zu einem Fehler in Ihrer Xbox One Spiel abzurufen](get-details-for-an-error-in-your-xbox-one-game.md) Methode zum Abrufen von Details zu einem bestimmten Fehler in Ihrer app, und verwenden Sie den Wert **CabId** im Antworttext dieser Methode.

## <a name="request"></a>Anforderung


### <a name="request-syntax"></a>Anforderungssyntax

| Methode | Anforderungs-URI                                                          |
|--------|----------------------------------------------------------------------|
| GET    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/xbox/stacktrace``` |


### <a name="request-header"></a>Anforderungsheader

| Header        | Typ   | Beschreibung                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| Autorisierung | String | Erforderlich. Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;. |


### <a name="request-parameters"></a>Anforderungsparameter

| Parameter        | Typ   |  Beschreibung      |  Erforderlich  |
|---------------|--------|---------------|------|
| applicationId | string | Die Produkt-ID des Xbox One Spiels, für die Sie eine stapelüberwachung abrufen möchten. Um die Produkt-ID Ihres Spiels zu erhalten, wechseln Sie zu Ihrem Spiel in der Xbox-Entwickler-Portal (XDP) und rufen Sie die Produkt-ID von der URL ab. Alternativ können ist Sie Ihre integritätsdaten vom Windows Dev Center-Analysebericht herunterladen, die Produkt-ID in der TSV-Datei enthalten. |  Ja  |
| cabId | string | Die eindeutige ID der CAB-Datei, die mit dem Fehler verknüpft ist, für den Sie die Stapelüberwachung abrufen möchten. Um diese ID zu erhalten, verwenden Sie die [Details zu einem Fehler in Ihrer Xbox One Spiel abzurufen](get-details-for-an-error-in-your-xbox-one-game.md) Methode zum Abrufen von Details zu einem bestimmten Fehler in Ihrer app, und verwenden Sie den Wert **CabId** im Antworttext dieser Methode. |  Ja  |

 
### <a name="request-example"></a>Anforderungsbeispiel

Im folgende Beispiel wird veranschaulicht, wie eine stapelüberwachung für einen Xbox One-Spiele mit dieser Methode abrufen. Ersetzen Sie den Wert *ApplicationId* durch die Produkt-ID für Ihr Spiel.

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/xbox/stacktrace?applicationId=BRRT4NJ9B3D1&cabId=1336373323853 HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a>Antwort


### <a name="response-body"></a>Antworttext

| Wert      | Typ    | Beschreibung                  |
|------------|---------|--------------------------------|
| Wert      | array   | Ein Array von Objekten, die jeweils einen einzelnen Frame der Stapelüberwachungsdaten enthalten. Weitere Informationen zu den Daten in den einzelnen Objekten finden Sie unten im Abschnitt [Stapelüberwachungswerte](#stack-trace-values). |
| @nextLink  | String  | Wenn weitere Seiten mit Daten vorhanden sind, enthält diese Zeichenfolge einen URI, mit dem Sie die nächste Seite mit Daten anfordern können. Beispielsweise wird dieser Wert zurückgegeben, wenn der Parameter **top** der Anforderung auf 10 festgelegt ist, es jedoch mehr als 10 Zeilen mit Fehlern für die Abfrage gibt. |
| TotalCount | Ganzzahl | Die Gesamtzahl der Zeilen im Datenergebnis für die Abfrage.          |


### <a name="stack-trace-values"></a>Stapelüberwachungswerte

Elemente im Array *Value* enthalten die folgenden Werte.

| Wert           | Typ    | Beschreibung      |
|-----------------|---------|----------------|
| level            | string  |  Die Framenummer, die dieses Element im Aufrufstapel darstellt.  |
| image   | string  |   Den Namen der ausführbaren Datei oder des Bibliothekbilds, die/das die Funktion enthält, die in diesem Stapelframe aufgerufen wird.           |
| function | string  |  Der Name der Funktion, die in diesem Stapelframe aufgerufen wird. Dies ist nur verfügbar, wenn Ihr Spiel Symbole für die ausführbare Datei oder Bibliothek enthält.              |
| offset     | string  |  Der Byte-Offset der aktuellen Anweisung relativ zum Start der Funktion.      |


### <a name="response-example"></a>Antwortbeispiel

Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.

```json
{
  "Value": [
    {
      "level": "0",
      "image": "Contoso.ContosoApp",
      "function": "Contoso.ContosoApp.MainPage.DoWork",
      "offset": "0x25C"
    }
    {
      "level": "1",
      "image": "Contoso.ContosoApp",
      "function": "Contoso.ContosoApp.MainPage.Initialize",
      "offset": "0x26"
    }
    {
      "level": "2",
      "image": "Contoso.ContosoApp",
      "function": "Contoso.ContosoApp.Start",
      "offset": "0x66"
    }
  ],
  "@nextLink": null,
  "TotalCount": 3
}

```

## <a name="related-topics"></a>Verwandte Themen

* [Zugreifen auf Analysedaten mit MicrosoftStore-Diensten](access-analytics-data-using-windows-store-services.md)
* [Abrufen von Fehlerberichtsdaten für Ihre Xbox One Spiel](get-error-reporting-data-for-your-xbox-one-game.md)
* [Abrufen von Details zu einem Fehler in Ihrer Xbox One-Spiele](get-details-for-an-error-in-your-xbox-one-game.md)
* [Herunterladen der CAB-Datei für einen Fehler in Ihrer Xbox One Spiel](download-the-cab-file-for-an-error-in-your-xbox-one-game.md)
