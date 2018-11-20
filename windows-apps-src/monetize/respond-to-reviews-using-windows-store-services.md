---
author: Xansky
ms.assetid: c92c0ea8-f742-4fc1-a3d7-e90aac11953e
description: Verwenden Sie die Microsoft Store-Rezensionen-API, um programmgesteuert Antworten auf Rezensionen Ihrer App im Store zu übermitteln.
title: Antworten auf Rezensionen mit Store-Diensten
ms.author: mhopkins
ms.date: 06/04/2018
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Rezensionen-API, Reagieren auf Rezensionen
ms.localizationpriority: medium
ms.openlocfilehash: 063c228a9a2fcfde9350af4872aabba44f9bb8a5
ms.sourcegitcommit: ed0304b8a214c03b8aab74b8ef12c9f82b8e3c5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "7292428"
---
# <a name="respond-to-reviews-using-store-services"></a>Antworten auf Rezensionen mit Store-Diensten

Verwenden Sie die *Microsoft Store-Rezensionen-API*, um programmgesteuert auf Rezensionen Ihrer App im Store zu reagieren. Diese API ist besonders nützlich für Entwickler, die gleichzeitig auf zahlreiche Rezensionen reagieren, ohne dabei Partner Center. Diese API verwendet Azure Active Directory (Azure AD), um die Aufrufe von Ihrer App oder Ihrem Dienst zu authentifizieren.

Dazu müssen folgende Schritte ausgeführt werden:

1.  Stellen Sie sicher, dass Sie alle [Voraussetzungen](#prerequisites) erfüllt haben.
2.  Vor dem Aufrufen einer Methode in der Microsoft Store-Rezensionen-API müssen Sie [ein Azure-AD-Zugriffstoken anfordern](#obtain-an-azure-ad-access-token). Nach dem Abrufen eines Tokens haben Sie 60 Minuten Zeit, um das Token zum Aufrufen der Microsoft Store-Rezensionen-API zu nutzen, bevor es abläuft. Nach dem Ablauf des Tokens können Sie ein neues Token generieren.
3.  [Aufrufen der Microsoft Store-Rezensionen-API](#call-the-windows-store-reviews-api).

> [!NOTE]
> Zusätzlich zur Verwendung von Rezensionen im Microsoft Store-API zum programmgesteuerten reagieren auf Rezensionen auch auf Rezensionen [mithilfe von Partner Center](../publish/respond-to-customer-reviews.md)Antworten können.

<span id="prerequisites" />

## <a name="step-1-complete-prerequisites-for-using-the-microsoft-store-reviews-api"></a>Schritt 1: Erfüllen der Voraussetzungen für die Verwendung der Microsoft Store-Rezensionen-API

Stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen, bevor Sie mit dem Schreiben von Code zum Aufrufen der MicrosoftStore-Rezensionen-API beginnen.

* Sie (bzw. Ihre Organisation) müssen über ein Azure AD-Verzeichnis und die Berechtigung [Globaler Administrator](http://go.microsoft.com/fwlink/?LinkId=746654) für das Verzeichnis verfügen. Wenn Sie bereits mit Office 365oder anderen Unternehmensdiensten von Microsoft arbeiten, verfügen Sie schon über ein Azure AD-Verzeichnis. Andernfalls können Sie [ein neues Azure AD im Partner Center erstellen](../publish/associate-azure-ad-with-dev-center.md#create-a-brand-new-azure-ad-to-associate-with-your-partner-center-account) , für die ohne zusätzliche Kosten.

* Sie müssen Ihr Partner Center-Konto eine Azure AD-Anwendung zuordnen, die Mandanten-ID und die Client-ID für die Anwendung abrufen und einen Schlüssel generieren. Die Azure-AD-Anwendung stellt die App oder den Dienst dar, von der/dem Sie die Microsoft Store-Rezensionen-API aufrufen möchten. Sie benötigen die Mandanten-ID, die Client-ID und den Schlüssel zum Abrufen eines Azure-AD-Zugriffstokens, das Sie an die API übergeben.
    > [!NOTE]
    > Sie müssen diesen Schritt nur einmal ausführen. Wenn Sie im Besitz der Mandanten-ID, der Client-ID und des Schlüssel sind, können Sie diese Daten jederzeit wiederverwenden, um ein neues Azure AD-Zugriffstoken zu erstellen.

Ihr Partner Center-Konto eine Azure AD-Anwendung zuordnen, und die erforderlichen Werte abzurufen:

1.  Im Partner Center, [Partner Center-Konto Ihrer Organisation mit Azure AD-Verzeichnis Ihrer Organisation zuordnen](../publish/associate-azure-ad-with-dev-center.md).

2.  Als Nächstes Rezensionen aus der Seite " **Benutzer** " im Abschnitt **kontoeinstellungen** des Partner Center, [Fügen Sie die Azure AD-Anwendung hinzu](../publish/add-users-groups-and-azure-ad-applications.md#add-azure-ad-applications-to-your-partner-center-account) , die darstellt, die app oder den Dienst, mit denen Sie zu reagieren. Weisen Sie dieser Anwendung anschließend die Rolle **Verwalter** zu. Wenn die Anwendung nicht vorhanden ist, noch in Azure AD-Verzeichnis, Sie können [Erstellen Sie ein neues Azure AD-Anwendung im Partner Center](../publish/add-users-groups-and-azure-ad-applications.md#create-a-new-azure-ad-application-account-in-your-organizations-directory-and-add-it-to-your-partner-center-account). 

3.  Wechseln Sie zurück zur Seite **Benutzer**, klicken Sie auf den Namen der Azure AD-Anwendung, um die Anwendungseinstellungen aufzurufen, und kopieren Sie die Werte unter **Mandanten-ID** und **Client-ID**.

4. Klicken Sie auf **Neuen Schlüssel hinzufügen**. Kopieren Sie auf dem folgenden Bildschirm den Wert unter **Schlüssel**. Nach dem Verlassen der Seite können Sie nicht mehr auf diese Informationen zugreifen. Weitere Informationen finden Sie unter [Verwalten von Schlüsseln für eine Azure AD-App](../publish/add-users-groups-and-azure-ad-applications.md#manage-keys).

<span id="obtain-an-azure-ad-access-token" />

## <a name="step-2-obtain-an-azure-ad-access-token"></a>Schritt 2: Abrufen eines AzureAD-Zugriffstokens

Bevor Sie die Methoden in der Microsoft Store-Rezensionen-API aufrufen, müssen Sie ein Azure-AD-Zugriffstoken abrufen, das Sie für jede Methode in der API an den **Authorization**-Header übergeben. Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft. Nachdem das Token abgelaufen ist, können Sie es aktualisieren, um es in weiteren Aufrufen an die API zu verwenden.

Befolgen Sie zum Abrufen des Zugriffstokens die Anweisungen unter [Aufrufe zwischen Diensten mithilfe von Clientanmeldeinformationen](https://azure.microsoft.com/documentation/articles/active-directory-protocols-oauth-service-to-service/), um eine HTTP POST-Anforderung an den ```https://login.microsoftonline.com/<tenant_id>/oauth2/token```-Endpunkt zu senden. Hier ist ein Beispiel für eine Anforderung angegeben.

```syntax
POST https://login.microsoftonline.com/<tenant_id>/oauth2/token HTTP/1.1
Host: login.microsoftonline.com
Content-Type: application/x-www-form-urlencoded; charset=utf-8

grant_type=client_credentials
&client_id=<your_client_id>
&client_secret=<your_client_secret>
&resource=https://manage.devcenter.microsoft.com
```

Geben Sie für *Tenant\_id* Wert im POST-URI und die Parameter *Client\_id* und *Client\_secret* die Mandanten-ID, Client-ID und den Schlüssel für Ihre Anwendung, die Sie aus dem Partner Center im vorherigen Abschnitt abgerufen. Für den Parameter *resource* müssen Sie ```https://manage.devcenter.microsoft.com``` angeben.

Nachdem das Zugriffstoken abgelaufen ist, können Sie es aktualisieren, indem Sie [diese Anleitung](https://azure.microsoft.com/documentation/articles/active-directory-protocols-oauth-code/#refreshing-the-access-tokens) befolgen.

<span id="call-the-windows-store-reviews-api" />

## <a name="step-3-call-the-microsoft-store-reviews-api"></a>Schritt 3: Aufrufen der Microsoft Store-Rezensionen-API

Nachdem Sie ein Azure AD-Zugriffstoken abgerufen haben, können Sie die MicrosoftStore-Rezensionen-API aufrufen. Sie müssen das Zugriffstoken an den **Authorization**-Header der einzelnen Methoden übergeben.

Die Microsoft Store-Rezensionen-API enthält mehrere Methoden, die Sie verwenden können, um festzustellen, ob Sie auf eine bestimmte Rezension reagieren und Reaktionen auf eine oder mehrere Rezensionen übermitteln dürfen. Folgen Sie diesem Prozess zur Verwendung dieser API:

1. Rufen Sie die IDs der Rezensionen ab, auf die Sie antworten möchten. Rezensions-IDs finden Sie in den Antwortdaten der Methode [Abrufen von App-Rezensionen](get-app-reviews.md) der Microsoft Store-Analyse-API und unter [Offlinedownload](../publish/download-analytic-reports.md) im Bericht [Rezensionen](../publish/reviews-report.md).
2. Rufen Sie die [Antwort Informationen für App-Kritiken abrufen](get-response-info-for-app-reviews.md) -Methode auf, um zu bestimmen, ob Sie berechtigt sind, auf die Rezensionen zu reagieren. Beim Übermitteln von Rezensionen können Kunden auswählen, keine Antworten auf ihre Rezension zu erhalten. Sie können nicht auf Rezensionen von Kunden reagieren, die sich dazu entschieden haben, keine Antworten auf Rezensionen zu erhalten.
3. Rufen Sie die [Reaktionen auf App-Kritiken senden](submit-responses-to-app-reviews.md) Methode auf, um programmgesteuert auf die Rezensionen zu reagieren.


## <a name="related-topics"></a>Verwandte Themen

* [Abrufen von App-Rezensionen](get-app-reviews.md)
* [Antwortinformationen für App-Rezensionen abrufen](get-response-info-for-app-reviews.md)
* [Senden von Antworten auf App-Rezensionen](submit-responses-to-app-reviews.md)

 
