---
description: Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um die CAB-Datei für einen Fehler in Ihrer Xbox One Spiel herunterzuladen.
title: Herunterladen der CAB-Datei für einen Fehler in Ihrer Xbox One Spiel
ms.date: 11/06/2018
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Analyse-API, CAB herunterladen
ms.localizationpriority: medium
ms.openlocfilehash: 736219533a254e6380c10600e97f707f15e37de6
ms.sourcegitcommit: b11f305dbf7649c4b68550b666487c77ea30d98f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "7834840"
---
# <a name="download-the-cab-file-for-an-error-in-your-xbox-one-game"></a>Herunterladen der CAB-Datei für einen Fehler in Ihrer Xbox One Spiel

Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um die CAB-Datei herunterzuladen, die ist die mit einem bestimmten Fehler in Ihrer Xbox One Spiel, das über das Xbox-Portal (XDP) aufgenommen wurde und im XDP Analytics Partner Center-Dashboard verfügbar. Diese Methode kann nur die CAB-Datei für einen Fehler herunterladen, die in den letzten 30 Tagen aufgetreten ist.

Bevor Sie diese Methode verwenden können, müssen Sie zuerst die [Details zu einem Fehler in Ihrer Xbox One Spiel get](get-details-for-an-error-in-your-xbox-one-game.md) -Methode verwenden, um die ID der CAB-Datei abzurufen, die Sie herunterladen möchten.

## <a name="prerequisites"></a>Voraussetzungen


Zur Verwendung dieser Methode sind folgende Schritte erforderlich:

* Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.
* [Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird. Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft. Wenn das Token abgelaufen ist, können Sie ein neues abrufen.
* Rufen Sie die ID der CAB-Datei ab, die Sie herunterladen möchten. Um diese ID zu erhalten, verwenden Sie die [Details zu einem Fehler in Ihrer Xbox One Spiel abzurufen](get-details-for-an-error-in-your-xbox-one-game.md) -Methode, um Details zu einem bestimmten Fehler in Ihrer app abzurufen, und verwenden Sie den Wert **CabId** im Antworttext dieser Methode.

## <a name="request"></a>Anforderung


### <a name="request-syntax"></a>Anforderungssyntax

| Methode | Anforderungs-URI                                                          |
|--------|----------------------------------------------------------------------|
| GET    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/xbox/cabdownload``` |


### <a name="request-header"></a>Anforderungsheader

| Header        | Typ   | Beschreibung                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| Autorisierung | String | Erforderlich. Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;. |


### <a name="request-parameters"></a>Anforderungsparameter

| Parameter        | Typ   |  Beschreibung      |  Erforderlich  |
|---------------|--------|---------------|------|
| applicationId | string | Die Produkt-ID des Xbox One Spiels, für die Sie die CAB-Datei herunterladen. Um die Produkt-ID Ihres Spiels zu erhalten, wechseln Sie zu Ihrem Spiel in der Xbox-Entwickler-Portal (XDP) und rufen Sie die Produkt-ID von der URL ab. Wenn Sie Ihre integritätsdaten aus dem Windows Partner Center Analytics-Bericht herunterladen, ist die Produkt-ID auch in der TSV-Datei enthalten. |  Ja  |
| cabId | Zeichenfolge | Die eindeutige ID der CAB-Datei ab, die Sie herunterladen möchten. Um diese ID zu erhalten, verwenden Sie die [Details zu einem Fehler in Ihrer Xbox One Spiel abzurufen](get-details-for-an-error-in-your-xbox-one-game.md) -Methode, um Details zu einem bestimmten Fehler in Ihrer app abzurufen, und verwenden Sie den Wert **CabId** im Antworttext dieser Methode. |  Ja  |

 
### <a name="request-example"></a>Anforderungsbeispiel

Im folgenden Beispiel wird gezeigt, wie Sie mit dieser Methode eine CAB-Datei herunterladen. Ersetzen Sie die Parameter *applicationId* und *cabId* durch die entsprechende Werte für Ihre App.

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/xbox/cabdownload?applicationId=BRRT4NJ9B3D1&cabId=1336373323853 HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a>Antwort

Bei dieser Methode wird ein 302-Antwortcode (Umleitung) zurückgegeben, und der **Speicherort**-Header in der Antwort wird der Shared Access Signature (SAS)-URI der CAB-Datei zugewiesen. Der Aufrufer wird zu dieser URI für den automatischen Download der CAB-Datei weitergeleitet.

## <a name="related-topics"></a>Verwandte Themen

* [Zugreifen auf Analysedaten mit MicrosoftStore-Diensten](access-analytics-data-using-windows-store-services.md)
* [Abrufen von Fehlerberichtsdaten für Ihre Xbox One Spiel](get-error-reporting-data-for-your-xbox-one-game.md)
* [Abrufen von Details zu einem Fehler in Ihrer Xbox One-Spiele](get-details-for-an-error-in-your-xbox-one-game.md)
* [Abrufen der stapelüberwachung für einen Fehler in Ihrer Xbox One-Spiele](get-the-stack-trace-for-an-error-in-your-xbox-one-game.md)
