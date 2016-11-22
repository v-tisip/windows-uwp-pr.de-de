---
author: mcleanbyron
description: "Hier erfahren Sie, wie Sie die REST-API für App-Metadaten verwenden, um auf bestimmte Typen von Metadaten für Apps zuzugreifen. Diese API soll von Anzeigennetzwerken verwendet werden, um Informationen zu Apps im Windows Store abzurufen und so den Vertrieb von Werbeflächen an Inserenten zu verbessern."
title: "App-Metadaten-API für Anzeigennetzwerke"
translationtype: Human Translation
ms.sourcegitcommit: 97f7d8e5ebc2df1752a182d5765b6a8b28b539e5
ms.openlocfilehash: e2b0680e62014526f684e7c1f7fd7da83a14f5d3

---

# App-Metadaten-API für Anzeigennetzwerke

Anzeigennetzwerke können die *App-Metadaten-API* nutzen, um programmgesteuert Metadaten zu Apps im Windows Store abzurufen, einschließlich Details wie die Beschreibung und Kategorie für den Store-Eintrag der App und Angaben dazu, ob die App für Kinder unter 13Jahren geeignet ist. Der Zugriff auf die API beschränkt sich derzeit auf Entwickler, die von Microsoft eine Berechtigung zur Nutzung der API erhalten haben.

In diesem Artikel wird erläutert, wie Sie über das [Portal für die App-Metadaten-API](https://admetadata.portal.azure-api.net/) Zugriff auf die API anfordern, Ihren Abonnementschlüssel für den Zugriff auf die API abrufen und die API aufrufen.

## Anfordern des Zugriffs

Betreiber von Anzeigennetzwerken können den Zugriff auf die App-Metadaten-API anfordern, indem sie die nachstehenden Schritte befolgen:

1. Wechseln Sie im Portal für die App-Metadaten-API zur Seite [https://admetadata.portal.azure-api.net/signup](https://admetadata.portal.azure-api.net/signup).
2. Geben Sie die erforderlichen Informationen ein, und klicken Sie auf die Schaltfläche **Registrieren**.
3. Klicken Sie auf der gleichen Website auf die Registerkarte **Produkte** und dann auf **App details for advertising**.
4. Klicken Sie auf der nächsten Seite auf die Schaltfläche **Abonnieren**. Dadurch wird Ihre Anfrage für den Zugriff auf die App-Metadaten-API an Microsoft übermittelt.

Nachdem Ihre Anfrage übermittelt wurde, erhalten Sie innerhalb von ca. 24 Stunden eine E-Mail mit der Mitteilung, ob Ihre Anfrage gewährt oder abgelehnt wurde.

<span id="get-key" />
## Abrufen des Abonnementschlüssels

Wenn Ihnen Zugriff auf die App-Metadaten-API gewährt wurde, befolgen Sie die nachstehenden Schritte, um Ihren Abonnementschlüssel abzurufen. Sie müssen diesen Schlüssel im Anforderungsheader von Aufrufen der API übergeben.

1. Wechseln Sie im Portal für die App-Metadaten-API zur Seite [https://admetadata.portal.azure-api.net/signin](https://admetadata.portal.azure-api.net/signin), und melden Sie sich mit Ihrer E-Mail-Adresse und Ihrem Kennwort an.
2. Klicken Sie in der oberen rechten Ecke der Website auf Ihren Namen, und klicken Sie dann auf **Profil**.
3. Klicken Sie auf der Seite im Abschnitt **Ihre Abonnements** neben **Primärschlüssel** auf **Anzeigen**. Dies ist Ihr Abonnementschlüssel. Kopieren Sie den Schlüssel, damit Sie ihn später beim Aufrufen der API verwenden können.

<span id="call-the-api" />
## Aufrufen der API

Nachdem Sie über Ihren Abonnementschlüssel verfügen, können Sie die API mithilfe von HTTP-REST-Syntax in der Programmiersprache Ihrer Wahl aufrufen. Informationen zur Syntax der API finden Sie im Abschnitt [API-Syntax](#syntax) weiter unten. Um Codebeispiele in C#, JavaScript, Python und einigen anderen Programmiersprachen anzuzeigen, klicken Sie im Portal für die App-Metadaten-API auf die Registerkarte **APIs** und auf **App-Details**. Am unteren Seitenrand ist der Abschnitt **Codebeispiele** zu sehen.

Alternativ können Sie die API über die Benutzeroberfläche aufrufen, die vom Portal für die App-Metadaten-API bereitgestellt wird:
  1. Klicken Sie im Portal auf die Registerkarte **APIs** und dann auf **App-Details**.
  2. Geben Sie auf der folgenden Seite die [app_id](#request-parameters) der App, für die Metadaten abgerufen werden sollen, in das Feld **app_id** und Ihren Abonnementschlüssel in das Feld **Ocp_Apim_Subscription-Key** ein.
  3. Klicken Sie auf **Senden**. Die Antwort wird unten auf der Seite angezeigt.


<span id="syntax" />
## API-Syntax

Diese Methode hat die folgende Anforderungssyntax.

| Methode | Anforderungs-URI                                                      |
|--------|------------------------------------------------------------------|
| GET   | ```https://admetadata.azure-api.net/v1/app/{app_id}``` |

<span/>
 

### Anforderungsheader

| Header        | Typ   | Beschreibung                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| Ocp-Apim-Subscription-Key | String | Erforderlich. Der Abonnementschlüssel, den Sie aus dem [Portal für die App-Metadaten-API abgerufen haben](#get-key).  |

<span/>

### Anforderungsparameter

| Name        | Typ   | Beschreibung                                                                 |
|---------------|--------|-----------------------|
| app_id | String | Erforderlich. Die ID der App, für die Sie Metadaten abrufen möchten. Folgende Werte sind möglich:<br/><br/><ul><li>Die Store-ID für die App. Beispiel für eine Store-ID: 9NBLGGH29DM8.</li><li>Die Produkt-ID (manchmal auch als *App-ID* bezeichnet) für eine App, die ursprünglich für Windows8.x oder Windows Phone8.x erstellt wurde. Die Produkt-ID ist eine GUID.</li></ul> |

<span/>

### Anforderungsbeispiel

Im folgenden Beispiel wird veranschaulicht, wie Metadaten für eine App mit der Store-ID 9NBLGGH29DM8 abgerufen werden.

```syntax
GET https://admetadata.azure-api.net/v1/app/9NBLGGH29DM8 HTTP/1.1
Ocp-Apim-Subscription-Key: <subscription key>
```

### Antworttext

Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.

```json
{
    "storeId":"9NBLGGH29DM8",
    "name":"Contoso Sports App",
    "description":"Catch the latest scores and replays using Contoso Sports App!",
    "phoneStoreGuid":"920217d7-90da-4019-99e8-46e4a6bd2594",
    "windowsStoreGuid":"d7e982e7-fbf3-42b5-9dad-72b65bd4e248",
    "storeCategory":"Sports",
    "iabCategory":"Sports",
    "iabCategoryId":"IAB17",
    "coppa":false,
    "downloadUrl":"https://www.microsoft.com/store/apps/9nblggh29dm8","isLive":true,
    "iconUrls":["//store-images.microsoft.com/image/apps.15753.13510798883747357.b6981489-6fdd-4fec-b655-a822247d5a76.33529096-a723-4204-9da9-a5dd8b328d4e"],
    "type":"App"
}
```

Weitere Informationen zu den Werten im Antworttext finden Sie in der folgenden Tabelle.

| Wert      | Typ   | Beschreibung    |
|------------|--------|--------------------|
| storeId           | String  | Die Store-ID der App. Beispiel für eine Store-ID: 9NBLGGH29DM8.     |  
| name           | String  | Der Name der App.   |
| description           | String  | Die Beschreibung aus dem Store-Eintrag für die App.  |
| phoneStoreGuid           | String  | Die Produkt-ID (Windows Phone8.x) für die App. Dies ist eine GUID.  |
| windowsStoreGuid           | String  | Die Produkt-ID (Windows8.x) für die App. Dies ist eine GUID. |
| storeCategory           | String  | Die Kategorie für die App im Store. Die unterstützten Werte finden Sie in der [Kategorie- und Unterkategorietabelle](../publish/category-and-subcategory-table.md) für Apps im Store.  |
| iabCategory           | String  | Die Inhaltskategorie für die App gemäß Definition des Interactive Advertising Bureau (IAB). Beispielsweise **Nachrichten** oder **Sport**. Eine Liste der Inhaltskategorien finden Sie auf der Seite [IAB Tech Lab Content Taxonomy](https://www.iab.com/guidelines/iab-quality-assurance-guidelines-qag-taxonomy) der IAB-Website.   |
| iabCategoryId           | String  | Die ID der Inhaltskategorie für die App. **IAB12** ist beispielsweise die ID für die Nachrichtenkategorie und **IAB17** die ID für die Sportkategorie. Eine Liste der IDs für Inhaltskategorien finden Sie in Abschnitt 5.1 der [OpenRTB API Specification](http://www.iab.com/wp-content/uploads/2015/05/OpenRTB_API_Specification_Version_2_3_1.pdf). |
| coppa           | Boolean  | „True“, wenn sich die App an Kinder unter 13Jahren richtet und daher bestimmten Anforderungen gemäß dem Children's Online Privacy Protection Act („COPPA“) unterliegt; andernfalls „False“.  |
| downloadUrl           | String  | Der Link zum App-Eintrag im Store. Dieser Link hat das Format ```https://www.microsoft.com/store/apps/<Store ID>```.  |
| iconUrls           | String  |  Der relative Pfad zu den Symbol-URLs, die dieser App zugeordnet sind. Um die Symbole abzurufen, stellen Sie den URLs *http* oder *https* voran.  |
| type           | String  | Eine der folgenden Zeichenfolgen: **App** oder **Game**.  |

<span/>



 

 



<!--HONumber=Nov16_HO1-->


