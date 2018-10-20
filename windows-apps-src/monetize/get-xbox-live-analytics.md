---
author: Xansky
description: Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um Xbox Live Analysedaten abzurufen.
title: Abrufen von Xbox Live Analysedaten
ms.author: mhopkins
ms.date: 06/04/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, Uwp, Store-Diensten, Microsoft Store-Analyse-API, Xbox Live Analyse
ms.localizationpriority: medium
ms.openlocfilehash: 68bc3389276acc910272d57e9cc859a7e8ffd6c7
ms.sourcegitcommit: 72835733ec429a5deb6a11da4112336746e5e9cf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/20/2018
ms.locfileid: "5168023"
---
# <a name="get-xbox-live-analytics-data"></a>Abrufen von Xbox Live Analysedaten

Verwenden Sie diese Methode in der Microsoft Store-Analyse-API zum Abrufen der letzten 30Tage von allgemeinen Analysedaten für Kunden, die Ihr [Xbox Live-fähiges Spiel](../xbox-live/index.md) spielen, einschließlich Gerätezubehörnutzung, Internetverbindungstyp, Gamerscore-Verteilung, Spielstatistiken und Freunde- und Follower-Daten. Diese Informationen sind auch im [Xbox Analyse-Bericht](../publish/xbox-analytics-report.md) im Windows Dev Center-Dashboard verfügbar.

> [!IMPORTANT]
> Diese Methode unterstützt nur Spiele für Xbox oder Spiele, die Xbox Live-Dienste verwenden. Diese Spiele müssen den [Konzeptgenehmigungsprozess](../gaming/concept-approval.md) durchlaufen, der Spiele umfasst, die von [Microsoft-Partnern](../xbox-live/developer-program-overview.md#microsoft-partners) veröffentlicht wurden, sowie Spiele, die über das [ID@Xbox-Programm](../xbox-live/developer-program-overview.md#id) übermittelt wurden. Diese Methode unterstützt derzeit keine Spiele, die über das [Xbox Live Creators-Programm](../xbox-live/get-started-with-creators/get-started-with-xbox-live-creators.md) eingereicht wurden.

Zusätzliche Analysedaten für Xbox Live-fähige Spiele sind über folgende Methoden verfügbar:
* [Abrufen von Xbox Live Erfolgsdaten](get-xbox-live-achievements-data.md)
* [Abrufen von Xbox Live Integritätsdaten](get-xbox-live-health-data.md)
* [Abrufen von Xbox Live Spielehubdaten](get-xbox-live-game-hub-data.md)
* [Abrufen von Xbox Live-Clubdaten](get-xbox-live-club-data.md)
* [Abrufen von Xbox Live Multiplayer-Daten](get-xbox-live-multiplayer-data.md)
* [Abrufen von Xbox Live Daten zur gleichzeitigen Nutzung](get-xbox-live-concurrent-usage-data.md)

## <a name="prerequisites"></a>Voraussetzungen

Zur Verwendung dieser Methode sind folgende Schritte erforderlich:

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
| applicationId | String | Die [Store-ID](in-app-purchases-and-trials.md#store-ids) des Spiels, für das Sie die allgemeinen Xbox Live Analysedaten abrufen möchten.  |  Ja  |
| metricType | String | Eine Zeichenfolge, die den Typ der abzurufenden Xbox Live Analysedaten angibt. Geben Sie für diese Methode den Wert **productvalues** an.  |  Ja  |


### <a name="request-example"></a>Anforderungsbeispiel

Das folgende Beispiel zeigt eine Anforderung zum Abrufen von allgemeinen Analysedaten für Kunden, die Ihr Xbox Live-fähiges Spiel spielen. Ersetzen Sie den *applicationId*-Wert durch die Store-ID Ihres Spiels.

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/gameanalytics?applicationId=9NBLGGGZ5QDR&metrictype=productvalues HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a>Antwort

Diese Methode gibt ein *Value*-Array zurück, das folgende Objekte enthält.

| Objekt      | Beschreibung                  |
|-------------|---------------------------------------------------|
| ProductData   |   Enthält ein [DeviceProperties](#deviceproperties)-Objekt und ein [UserProperties](#userproperties)-Objekt, die die letzten 30Tage an Geräte- und Benutzeranalysedaten für Ihr Spiel enthalten.    |  
| XboxwideData   |  Enthält ein [DeviceProperties](#deviceproperties)-Objekt und ein [UserProperties](#userproperties)-Objekt, die die letzten 30Tage der durchschnittlichen Geräte- und Benutzeranalysedaten für alle Xbox Live Kunden in Prozentsätzen enthalten. Diese Daten werden zu Vergleichszwecken mit den Daten für Ihr Spiel beigefügt.   |                                           


### <a name="deviceproperties"></a>DeviceProperties

Diese Ressource enthält Gerätenutzungsdaten für Ihr Spiel oder durchschnittliche Gerätnutzungsdaten für alle Xbox Live-Kunden in den letzten 30Tagen.

| Wert           | Typ    | Beschreibung        |
|-----------------|---------|------|
|  applicationId               |    String     |  Die [Store-ID](in-app-purchases-and-trials.md#store-ids) des Spiels, für das Sie Analysedaten abgerufen haben.   |
|  connectionTypeDistribution               |    Array     |   Enthält Objekte, die angeben, wie viele Kunden eine verkabelte Internetverbindung im Vergleich zu einer Wireless-Internetverbindung mit Xbox verwenden. Jedes Objekt hat zwei Zeichenkettenfelder: <ul><li>**conType**: Gibt den Typ der Verbindung an.</li><li>**deviceCount**: Im **ProductData**-Objekt gibt dieses Feld die Anzahl Ihrer Spiel-Kunden an, die den Verbindungstyp verwenden. Im **XboxwideData**-Objekt gibt dieses Feld den Prozentsatz aller Xbox Live-Kunden an, die den Verbindungstyp verwenden.</li></ul>   |     
|  deviceCount               |   String      |  Im **ProductData**-Objekt gibt dieses Feld die Anzahl der Kundengeräte an, auf denen Ihr Spiel während der letzten 30Tage gespielt wurde. Im **XboxwideData**-Objekt ist dieses Feld immer 1, womit ein Ausgangsprozentsatz von 100% für Daten für alle Xbox Live-Kunden angezeigt wird.   |     
|  eliteControllerPresentDeviceCount               |   String      |  Im **ProductData**-Objekt gibt dieses Feld die Anzahl der Kunden Ihres Spiels an, die den Xbox Elite Wireless Controller verwenden. Im **XboxwideData**-Objekt gibt dieses Feld den Prozentsatz aller Xbox Live-Kunden an, die den Xbox Elite Wireless Controller verwenden.  |     
|  externalDrivePresentDeviceCount               |   String      |  Im **ProductData**-Objekt gibt dieses Feld die Anzahl der Kunden Ihres Spiels an, die ein externes Laufwerk mit Xbox verwenden. Im **XboxwideData**-Objekt gibt dieses Feld den Prozentsatz aller Xbox Live-Kunden an, die ein externes Laufwerk mit Xbox verwenden.  |


### <a name="userproperties"></a>UserProperties

Diese Ressource enthält Benutzerdaten für Ihr Spiel oder durchschnittliche Benutzerdaten für alle Xbox Live-Kunden in den letzten 30Tagen.

| Wert           | Typ    | Beschreibung        |
|-----------------|---------|------|
|  applicationId               |    String     |   Die [Store-ID](in-app-purchases-and-trials.md#store-ids) des Spiels, für das Sie Analysedaten abgerufen haben.  |
|  userCount               |    String     |   Im **ProductData**-Objekt gibt dieses Feld die Anzahl der Kunden an, die Ihr Spiel während der letzten 30Tage gespielt haben. Im **XboxwideData**-Objekt ist dieses Feld immer 1, womit ein Ausgangsprozentsatz von 100% für Daten für alle Xbox Live-Kunden angezeigt wird.   |     
|  dvrUsageCounts               |   Array      |  Enthält Objekte, die angeben, wie viele Kunden einen Spiele-DVR zum Aufzeichnen und Anzeigen des Spiels verwendet haben. Jedes Objekt hat zwei Zeichenkettenfelder: <ul><li>**dvrName**: Gibt das verwendete Spiele-DVR-Merkmal an. Mögliche Werte sind **gameClipUploads**, **gameClipViews**, **screenshotUploads** und **screenshotViews**.</li><li>**userCount**: Im **ProductData**-Objekt gibt dieses Feld die Anzahl der Kunden Ihres Spiels an, die das angegebene Spiele-DVR-Merkmal verwendet haben. Im **XboxwideData**-Objekt gibt dieses Feld den Prozentsatz aller Xbox Live-Kunden an, die das angegebene Spiele-DVR-Merkmal verwendet haben.</li></ul>   |     
|  followerCountPercentiles               |   Array      |  Enthält Objekte, die Details über die Anzahl der Follower für Kunden bereitstellen. Jedes Objekt hat zwei Zeichenkettenfelder: <ul><li>**percentage**: Dieser Wert ist derzeit immer 50, womit angezeigt wird, dass die Follower-Daten als ein Mittelwert angegeben werden.</li><li>**value**: Im **ProductData**-Objekt gibt dieses Feld die mittlere Anzahl von Follower für Ihre Spielkunden an. Im **XboxwideData**-Objekt gibt dieses Feld die mittlere Anzahl von Follower für alle Xbox Live-Kunden an.</li></ul>  |   
|  friendCountPercentiles               |   Array      |  Enthält Objekte, die Details über die Anzahl der Freunde für Kunden bereitstellen. Jedes Objekt hat zwei Zeichenkettenfelder: <ul><li>**percentage**: Dieser Wert ist derzeit immer 50, womit angezeigt wird, dass die Freunde-Daten als ein Mittelwert angegeben werden.</li><li>**value**: Im **ProductData**-Objekt gibt dieses Feld die mittlere Anzahl von Freunden für Ihre Spielkunden an. Im **XboxwideData**-Objekt gibt dieses Feld die mittlere Anzahl von Freunden für alle Xbox Live-Kunden an.</li></ul>  |     
|  gamerScoreRangeDistribution               |   Array      |  Enthält Objekte, die Details über die Gamescore-Verteilung für Kunden bereitstellen. Jedes Objekt hat zwei Zeichenkettenfelder: <ul><li>**scoreRange**: Der Gamerscore-Bereich für den das folgende Feld Nutzungsdaten bereitstellt. Beispiel: **10K-25K**.</li><li>**userCount**: Im **ProductData**-Objekt gibt dieses Feld die Anzahl der Kunden Ihres Spiels an, die einen Gamerscore im angegebenen Bereich für alle Spiele haben, die sie gespielt haben. Im **XboxwideData**-Objekt gibt dieses Feld den Prozentsatz alle Xbox Live-Kunden an, die einen Gamerscore im angegebenen Bereich für alle Spiele haben, die sie gespielt haben.</li></ul>  |
|  titleGamerScoreRangeDistribution               |   Array      |  Enthält Objekte, die Details über die Gamescore-Verteilung für Ihr Spiel bereitstellen. Jedes Objekt hat zwei Zeichenkettenfelder: <ul><li>**scoreRange**: Der Gamerscore-Bereich für den das folgende Feld Nutzungsdaten bereitstellt. Beispiel: **100-200**.</li><li>**userCount**: Im **ProductData**-Objekt gibt dieses Feld die Anzahl der Kunden Ihres Spiels an, die einen Gamerscore im angegebenen Bereich für Ihr Spiel haben. Im **XboxwideData**-Objekt gibt dieses Feld den Prozentsatz alle Xbox Live-Kunden an, die einen Gamerscore im angegebenen Bereich für Ihr Spiel haben.</li></ul>   |
|  socialUsageCounts               |   Array      |  Enthält Objekte, die Details über die gemeinschaftliche Nutzung für Kunden bereitstellen. Jedes Objekt hat zwei Zeichenkettenfelder: <ul><li>**scName**: Der Typ der gemeinschaftlichen Verwendung. Beispielsweise **gameInvites** und **textMessages**.</li><li>**userCount**: Im **ProductData**-Objekt gibt dieses Feld die Anzahl der Kunden Ihres Spiels an, die am angegebenen gemeinschaftlichen Nutzungstyp teilgenommen haben. Im **XboxwideData**-Objekt gibt dieses Feld den Prozentsatz alle Xbox Live-Kunden an, die am angegebenen gemeinschaftlichen Nutzungstyp teilgenommen haben.</li></ul>   |
|  streamingUsageCounts               |   Array      |  Enthält Objekte, die Details über die Streaming-Nutzung für Kunden bereitstellen. Jedes Objekt hat zwei Zeichenkettenfelder: <ul><li>**stName**: Der Typ der Streaming-Plattform. Beispielsweise **youtubeUsage**, **twitchUsage** und **mixerUsage**.</li><li>**userCount**: Im **ProductData**-Objekt gibt dieses Feld die Anzahl der Kunden Ihres Spiels an, die die angegebene Streaming-Plattform verwendet haben. Im **XboxwideData**-Objekt gibt dieses Feld den Prozentsatz aller Xbox Live-Kunden an, die die angegebene Streaming-Plattform verwendet haben.</li></ul>  |


### <a name="response-example"></a>Antwortbeispiel

Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.

```json
{
  "Value": [
    {
      "ProductData": {
        "DeviceProperties": [
          {
            "applicationId": "9NBLGGGZ5QDR",
            "connectionTypeDistribution": [
              {
                "conType": "WIRED",
                "deviceCount": "43806"
              },
              {
                "conType": "WIRELESS",
                "deviceCount": "104035"
              }
            ],
            "deviceCount": "148063",
            "eliteControllerPresentDeviceCount": "10615",
            "externalDrivePresentDeviceCount": "46388"
          }
        ],
        "UserProperties": [
          {
            "applicationId": "9NBLGGGZ5QDR",
            "userCount": "142345",
            "dvrUsageCounts": [
              {
                "dvrName": "gameClipUploads",
                "userCount": "31264"
              },
              {
                "dvrName": "gameClipViews",
                "userCount": "52236"
              },
              {
                "dvrName": "screenshotUploads",
                "userCount": "27051"
              },
              {
                "dvrName": "screenshotViews",
                "userCount": "45640"
              }
            ],
            "followerCountPercentiles": [
              {
                "percentage": "50",
                "value": "11"
              }
            ],
            "friendCountPercentiles": [
              {
                "percentage": "50",
                "value": "11"
              }
            ],
            "gamerScoreRangeDistribution": [
              {
                "scoreRange": "10K-25K",
                "userCount": "30015"
              },
              {
                "scoreRange": "25K-50K",
                "userCount": "20495"
              },
              {
                "scoreRange": "3K-10K",
                "userCount": "32438"
              },
              {
                "scoreRange": "50K-100K",
                "userCount": "10608"
              },
              {
                "scoreRange": "<3K",
                "userCount": "45726"
              },
              {
                "scoreRange": ">100K",
                "userCount": "3063"
              }
            ],
            "titleGamerScoreRangeDistribution": [
              {
                "scoreRange": "400-600",
                "userCount": "133875"
              },
              {
                "scoreRange": "800-1000",
                "userCount": "45960"
              },
              {
                "scoreRange": "<100",
                "userCount": "269137"
              },
              {
                "scoreRange": "≥1K",
                "userCount": "11634"
              },
              {
                "scoreRange": "100-200",
                "userCount": "334471"
              },
              {
                "scoreRange": "600-800",
                "userCount": "123044"
              },
              {
                "scoreRange": "200-400",
                "userCount": "396725"
              }
            ],
            "socialUsageCounts": [
              {
                "scName": "gameInvites",
                "userCount": "82390"
              },
              {
                "scName": "textMessages",
                "userCount": "91880"
              },
              {
                "scName": "partySessionCount",
                "userCount": "68129"
              }
            ],
            "streamingUsageCounts": [
              {
                "stName": "youtubeUsage",
                "userCount": "74092"
              },
              {
                "stName": "twitchUsage",
                "userCount": "13401"
              }
              {
                "stName": "mixerUsage",
                "userCount": "22907"
              }
            ]
          }
        ]
      },
      "XboxwideData": {
        "DeviceProperties": [
          {
            "applicationId": "XBOXWIDE",
            "connectionTypeDistribution": [
              {
                "conType": "WIRED",
                "deviceCount": "0.213677732584786"
              },
              {
                "conType": "WIRELESS",
                "deviceCount": "0.786322267415214"
              }
            ],
            "deviceCount": "1",
            "eliteControllerPresentDeviceCount": "0.0476609278128012",
            "externalDrivePresentDeviceCount": "0.173747147416134"
          }
        ],
        "UserProperties": [
          {
            "applicationId": "XBOXWIDE",
            "userCount": "1",
            "dvrUsageCounts": [
              {
                "dvrName": "gameClipUploads",
                "userCount": "0.173210623993245"
              },
              {
                "dvrName": "gameClipViews",
                "userCount": "0.202104713778096"
              },
              {
                "dvrName": "screenshotUploads",
                "userCount": "0.136682414274251"
              },
              {
                "dvrName": "screenshotViews",
                "userCount": "0.158057895120314"
              }
            ],
            "followerCountPercentiles": [
              {
                "percentage": "50",
                "value": "5"
              }
            ],
            "friendCountPercentiles": [
              {
                "percentage": "50",
                "value": "5"
              }
            ],
            "gamerScoreRangeDistribution": [
              {
                "scoreRange": "10K-25K",
                "userCount": "0.134709282586519"
              },
              {
                "scoreRange": "25K-50K",
                "userCount": "0.0549468789343825"
              },
              {
                "scoreRange": "50K-100K",
                "userCount": "0.017301313342277"
              },
              {
                "scoreRange": "3K-10K",
                "userCount": "0.216512780268453"
              },
              {
                "scoreRange": "<3K",
                "userCount": "0.573515440094644"
              },
              {
                "scoreRange": ">100K",
                "userCount": "0.00301430477372488"
              }
            ],
            "titleGamerScoreRangeDistribution": [
              {
                "scoreRange": "100-200",
                "userCount": "0.178055695637076"
              },
              {
                "scoreRange": "200-400",
                "userCount": "0.173283639825241"
              },
              {
                "scoreRange": "400-600",
                "userCount": "0.0986865193958259"
              },
              {
                "scoreRange": "600-800",
                "userCount": "0.0506375775462092"
              },
              {
                "scoreRange": "800-1000",
                "userCount": "0.0232398822856435"
              },
              {
                "scoreRange": "<100",
                "userCount": "0.456443551582991"
              },
              {
                "scoreRange": "≥1K",
                "userCount": "0.0196531337270126"
              }
            ],
            "socialUsageCounts": [
              {
                "scName": "gameInvites",
                "userCount": "0.460375855738335"
              },
              {
                "scName": "textMessages",
                "userCount": "0.429256324070832"
              },
              {
                "scName": "partySessionCount",
                "userCount": "0.378446577751268"
              },
              {
                "scName": "gamehubViews",
                "userCount": "0.000197115778147329"
              }
            ],
            "streamingUsageCounts": [
              {
                "stName": "youtubeUsage",
                "userCount": "0.330320919178683"
              },
              {
                "stName": "twitchUsage",
                "userCount": "0.040666241835399"
              }
              {
                "stName": "mixerUsage",
                "userCount": "0.140193816053558"
              }
            ]
          }
        ]
      }
    }
  ],
  "@nextLink": null,
  "TotalCount": 4
}
```

## <a name="related-topics"></a>Verwandte Themen

* [Zugreifen auf Analysedaten mit MicrosoftStore-Diensten](access-analytics-data-using-windows-store-services.md)
* [Abrufen von Xbox Live Erfolgsdaten](get-xbox-live-achievements-data.md)
* [Abrufen von Xbox Live Integritätsdaten](get-xbox-live-health-data.md)
* [Abrufen von Xbox Live Spielehubdaten](get-xbox-live-game-hub-data.md)
* [Abrufen von Xbox Live Clubdaten](get-xbox-live-club-data.md)
* [Abrufen von Xbox Live Multiplayer-Daten](get-xbox-live-multiplayer-data.md)
* [Abrufen von Xbox Live gleichzeitigen Nutzungsdaten](get-xbox-live-concurrent-usage-data.md)
