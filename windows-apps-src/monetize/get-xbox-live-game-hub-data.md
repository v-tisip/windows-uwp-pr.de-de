---
author: mcleanbyron
description: Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um Xbox Live Spielehubdaten abzurufen.
title: Abrufen von Xbox Live Spielehubdaten
ms.author: mcleans
ms.date: 04/16/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, Uwp, Store-Diensten, Microsoft Store-Analyse-API, Xbox Live Analyse, Spielehubs
ms.localizationpriority: medium
ms.openlocfilehash: 0d34c95e615a10131b3e7f3ffe9ceb246b652727
ms.sourcegitcommit: 91511d2d1dc8ab74b566aaeab3ef2139e7ed4945
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2018
ms.locfileid: "1815785"
---
# <a name="get-xbox-live-game-hub-data"></a>Abrufen von Xbox Live Spielehubdaten


Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um Spielehubdaten für Ihr [Xbox Live-fähiges Spiel](../xbox-live/index.md) abzurufen. Diese Informationen sind auch im [Xbox Analyse-Bericht](../publish/xbox-analytics-report.md) im Windows Dev Center-Dashboard verfügbar.

> [!IMPORTANT]
> Diese Methode unterstützt derzeit nur Xbox Live-fähige Spiele, die von [Microsoft Partnern](../xbox-live/developer-program-overview.md#microsoft-partners) veröffentlicht werden oder die mithilfe des [ID@Xbox Programms](../xbox-live/developer-program-overview.md#id) eingereicht wurden. Es gibt keine Daten für Spiele zurück, die mithilfe des [Xbox Live Creators-Programms](../xbox-live/developer-program-overview.md#xbox-live-creators-program) eingereicht wurden.

## <a name="prerequisites"></a>Voraussetzungen

Um diese Methode zu verwenden, sind die folgenden Schritte erforderlich:

* Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.
* [Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird. Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft. Wenn das Token abgelaufen ist, können Sie ein neues abrufen.

## <a name="request"></a>Anforderung


### <a name="request-syntax"></a>Anforderungssyntax

| Methode | Anforderungs-URI       |
|--------|----------------------|
| GET    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/gameanalytics``` |


### <a name="request-header"></a>Anforderungsheader

| Header        | Typ   | Beschreibung                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| Autorisierung | String | Erforderlich. Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;. |


### <a name="request-parameters"></a>Anforderungsparameter

| Parameter        | Typ   |  Beschreibung      |  Erforderlich  
|---------------|--------|---------------|------|
| applicationId | String | Die [Store-ID](in-app-purchases-and-trials.md#store-ids) des Spiels, für das Sie die Xbox Live Spielehubdaten abrufen möchten.  |  Ja  |
| metricType | String | Eine Zeichenfolge, die den Typ der abzurufenden Xbox Live Analysedaten angibt. Geben Sie für diese Methode den Wert **communitymanagergamehub** an.  |  Ja  |
| startDate | date | Das Startdatum im Datumsbereich der Spielehubdaten, die abgerufen werden sollen. Der Standardwert ist 30Tage vor dem aktuellen Datum. |  Nein  |
| endDate | date | Das Enddatum im Datumsbereich der Spielehubdaten, die abgerufen werden sollen. Der Standardwert ist das aktuelle Datum. |  Nein  |
| top | int | Die Anzahl der Datenzeilen, die in der Anforderung zurückgegeben werden sollen. Der Maximal- und Standardwert ist 10.000, wenn nicht anders angegeben. Wenn die Abfrage keine weiteren Zeilen enthält, entält der Antworttext den Link „Weiter“, den Sie verwenden können, um die nächste Seite mit Daten anzufordern. |  Nein  |
| skip | int | Die Anzahl der Zeilen, die in der Abfrage übersprungen werden sollen. Verwenden Sie diesen Parameter, um große Datensätze durchzublättern. Beispielsweise rufen „top=10000“ und „skip=0“ die ersten 10.000Datenzeilen ab, „top=10000“ und „skip=10000“ die nächsten 10.000Datenzeilen usw. |  Nein  |


### <a name="request-example"></a>Anforderungsbeispiel

Das folgende Beispiel zeigt eine Anforderung zum Abrufen von Spielehubdaten für Ihr Xbox Live-fähiges Spiel an. Ersetzen Sie den *applicationId*-Wert durch die Store-ID Ihres Spiels.

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/gameanalytics?applicationId=9NBLGGGZ5QDR&metrictype=communitymanagergamehub&top=10&skip=0 HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a>Antwort


| Wert      | Typ   | Beschreibung                  |
|------------|--------|-------------------------------------------------------|
| Wert      | Array  | Ein Array von Objekten, die für jedes Datum im Datumsbereich der angegebenen Spielehubdaten enthalten. Weitere Informationen zu den Daten in den einzelnen Objekten finden Sie in der folgenden Tabelle.                                                                                                                      |
| @nextLink  | String | Wenn weitere Seiten mit Daten vorhanden sind, enthält diese Zeichenfolge einen URI, mit dem Sie die nächste Seite mit Daten anfordern können. Beispielsweise wird dieser Wert zurückgegeben, wenn der Parameter **top** der Anforderung auf 10000 festgelegt ist, es jedoch mehr als 10000 Zeilen mit Daten für die Abfrage gibt. |
| TotalCount | int    | Die Gesamtzahl der Zeilen im Datenergebnis für die Abfrage.  |


Elemente im Array *Value* enthalten die folgenden Werte.

| Wert               | Typ   | Beschreibung                           |
|---------------------|--------|-------------------------------------------|
| date                | String | Das Datum für die Spielehubdaten in diesem Objekt. |
| applicationId       | String | Die Store-ID des Spiels, für das Sie Spielehubdaten abrufen.     |
| gameHubLikeCount     | number |   Die Anzahl der Vorlieben, die zur Spielehubseite an dem angegebenen Datum hinzugefügt wurden.   |
| gameHubCommentCount          | number |  Die Anzahl der Kommentare, die zur Spielehubseite für Ihre App an dem angegebenen Datum hinzugefügt wurden.  |
| gameHubShareCount           | number | Die Anzahl der Male, die die Spielehubseite für Ihre App von Kunden dem angegebenen Datum geteilt wurden.   |


### <a name="response-example"></a>Antwortbeispiel

Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.

```json
{
  "Value": [
    {
      "date": "2018-01-04",
      "applicationId": "9NBLGGGZ5QDR",
      "gameHubLikeCount": 10,
      "gameHubCommentCount": 1,
      "gameHubShareCount": 0
    },
    {
      "date": "2018-01-05",
      "applicationId": "9NBLGGGZ5QDR",
      "gameHubLikeCount": 12,
      "gameHubCommentCount": 1,
      "gameHubShareCount": 0
    }
  ],
  "@nextLink": null,
  "TotalCount": 26
}
```

## <a name="related-topics"></a>Verwandte Themen

* [Zugreifen auf Analysedaten mit MicrosoftStore-Diensten](access-analytics-data-using-windows-store-services.md)
* [Abrufen von Xbox Live Analysedaten](get-xbox-live-analytics.md)
* [Abrufen von Xbox Live Erfolgsdaten](get-xbox-live-achievements-data.md)
* [Abrufen von Xbox Live Integritätsdaten](get-xbox-live-health-data.md)
* [Abrufen von Xbox Live Clubdaten](get-xbox-live-club-data.md)
* [Abrufen von Xbox Live Multiplayerdaten](get-xbox-live-multiplayer-data.md)
