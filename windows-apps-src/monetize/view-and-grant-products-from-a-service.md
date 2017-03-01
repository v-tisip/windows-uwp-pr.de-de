---
author: mcleanbyron
ms.assetid: B071F6BC-49D3-4E74-98EA-0461A1A55EFB
description: "Wenn Sie über einen Katalog mit Apps und Add-ons verfügen, können Sie mithilfe der Windows Store-Sammlungs-API und der Windows Store-Einkaufs-API Besitzerinformationen zu diesen Produkten aus Ihren Diensten abrufen."
title: "Verwalten von Produktansprüchen aus einem Dienst"
ms.author: mcleans
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows 10, UWP, Windows Store-Sammlungs-API, Windows Store-Einkaufs-API, Produkte anzeigen, Produkte gewähren"
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: 7f4f74c887509e772fd01dbdcfe28d86c583fbc1
ms.lasthandoff: 02/07/2017

---

# <a name="manage-product-entitlements-from-a-service"></a>Verwalten von Produktansprüchen aus einem Dienst

Wenn Sie über einen Katalog mit Apps und Add-ons (auch als In-App-Produkte oder IAPs bezeichnet) verfügen, können Sie mithilfe der *Windows Store-Sammlungs-API* und der *Windows Store-Einkaufs-API* Berechtigungsinformationen zu diesen Produkten aus Ihren Diensten abrufen. Eine *Berechtigung* ist das Recht des Kunden zur Nutzung einer über den Windows Store veröffentlichten App oder eines Add-ons.

Diese APIs bestehen aus REST-Methoden, die für Entwickler mit Add-on-Katalogen konzipiert sind, die von plattformübergreifenden Diensten unterstützt werden. Diese APIs bieten folgende Möglichkeiten:

-   Windows Store-Sammlungs-API: [Abfrage von Produkten, die einem Benutzer gehören](query-for-products.md) sowie [Meldung eines Verbrauchsprodukts als erfüllt](report-consumable-products-as-fulfilled.md).
-   Windows Store-Einkaufs-API: [Gewähren eines kostenlosen Produkts für einen Benutzer](grant-free-products.md).

>**Hinweis**&nbsp;&nbsp;Die Windows Store-Sammlungs-API und -Einkaufs-API nutzen die Azure Active Directory (Azure AD)-Authentifizierung, um auf Eigentümerinformationen von Kunden zuzugreifen. Zur Verwendung dieser APIs müssen Sie (bzw. Ihre Organisation) über ein Azure AD-Verzeichnis und die Berechtigung [Globaler Administrator](http://go.microsoft.com/fwlink/?LinkId=746654) für das Verzeichnis verfügen. Wenn Sie bereits mit Office 365 oder anderen Business Services von Microsoft arbeiten, verfügen Sie schon über ein Azure AD-Verzeichnis.

## <a name="overview"></a>Übersicht

Die folgenden Schritte beschreiben den vollständigen Vorgang der Verwendung der Windows Store-Sammlungs-API und der Windows Store-Einkaufs-API.:

1.  [Konfigurieren Sie eine Webanwendung in Azure AD](#step-1).
2.  [Ordnen Sie Ihre Azure AD-Client-ID im Windows Dev Center-Dashboard Ihrer Anwendung zu](#step-2).
3.  In Ihrem Dienst: [Erstellen Sie Azure AD-Zugriffstokens](#step-3), die Ihre Herausgeberidentität darstellen.
4.  Im clientseitigen Code in Ihrer Windows-App: [Erstellen Sie einen Windows Store-ID-Schlüssel](#step-4), der die Identität des aktuellen Benutzers darstellt, und übergeben Sie den Windows Store-ID-Schlüssel zurück an Ihren Dienst.
5.  Sobald Sie über das erforderliche Azure AD-Zugriffstoken und den Windows Store-ID-Schlüssel verfügen, [rufen Sie die Windows Store-Sammlungs-API oder -Einkaufs-API aus Ihrem Dienst auf](#step-5).

Die folgenden Abschnitte enthalten weitere Details zu den einzelnen Schritten.

<span id="step-1"/>
### <a name="step-1-configure-a-web-application-in-azure-ad"></a>Schritt 1: Konfigurieren einer Webanwendung in Azure AD

Bevor Sie die Windows Store-Sammlungs-API oder -Einkaufs-API verwenden können, müssen Sie eine Azure AD-Webanwendung erstellen, die Mandanten-ID und die Client-ID für die Anwendung abrufen und einen Schlüssel erzeugen. Die Azure AD-Anwendung ist die Anwendung oder der Dienst, aus denen Sie die Windows Store-Sammlungs- oder -Einkaufs-API aufrufen möchten. Sie benötigen die Mandanten-ID, die Client-ID und den Schlüssel zum Abrufen eines Azure AD-Zugriffstokens, das Sie an die API übergeben.

>**Hinweis:**&nbsp;&nbsp;Sie müssen die in diesem Abschnitt beschriebenen Vorgänge nur einmal durchführen. Nachdem Sie Ihr Azure AD-Anwendungsmanifest aktualisiert haben und über Ihre Mandanten-ID, die Client-ID und das Clientgeheimnis verfügen, können Sie diese Werte immer verwenden, wenn Sie ein neues Azure AD-Zugriffstoken erstellen müssen.

1.  Führen Sie die Schritte unter [Integrieren von Anwendungen in Azure Active Directory](http://go.microsoft.com/fwlink/?LinkId=722502) aus, um Azure AD eine Webanwendung hinzuzufügen.

    > **Hinweis**&nbsp;&nbsp;Wählen Sie auf der Seite **Geben Sie uns Informationen zu Ihrer Anwendung** die Option **Webanwendung und/oder Web-API** aus. Dies ist erforderlich, damit Sie für Ihre Anwendung einen Schlüssel (auch *Clientgeheimnis* genannt) erhalten. Zum Aufrufen der Windows Store-Sammlungs-API oder -Einkaufs-API müssen Sie ein Clientgeheimnis angeben, wenn Sie in einem späteren Schritt ein Zugriffstoken von Azure AD anfordern.

2.  Navigieren Sie im [Azure-Verwaltungsportal](http://manage.windowsazure.com/) zu **Active Directory**. Wählen Sie Ihr Verzeichnis aus, klicken Sie oben auf die Registerkarte **Anwendungen**, und wählen Sie Ihre Anwendung aus.
3.  Klicken Sie auf die Registerkarte **Konfigurieren**. Ermitteln Sie auf dieser Registerkarte die Client-ID für Ihre Anwendung, und fordern Sie einen Schlüssel an. Dieser Schlüssel wird in den weiteren Schritten als *geheimer Clientschlüssel* bezeichnet.
4.  Klicken Sie am unteren Bildschirmrand auf **Manifest verwalten**. Laden Sie Ihr Azure AD-Anwendungsmanifest herunter, und ersetzen Sie den Abschnitt `"identifierUris"` durch folgenden Text:

    ```json
    "identifierUris" : [                                
            "https://onestore.microsoft.com",
            "https://onestore.microsoft.com/b2b/keys/create/collections",
            "https://onestore.microsoft.com/b2b/keys/create/purchase"
        ],
    ```

    Diese Zeichenfolgen stellen die von der Anwendung unterstützten Zielgruppen dar. In einem späteren Schritt erstellen Sie Azure AD-Zugriffstoken, die den einzelnen Zielgruppenwerten zugeordnet werden. Weitere Informationen zum Herunterladen Ihres Anwendungsmanifests finden Sie unter [Grundlegendes zum Azure Active Directory-Anwendungsmanifest](http://go.microsoft.com/fwlink/?LinkId=722500).

5.  Speichern Sie Ihr Anwendungsmanifest, und laden Sie es im [Azure-Verwaltungsportal](http://manage.windowsazure.com/) für Ihre Anwendung hoch.

<span id="step-2"/>
### <a name="step-2-associate-your-azure-ad-client-id-with-your-app-in-windows-dev-center"></a>Schritt 2: Zuordnen Ihrer Azure AD-Client-ID zu Ihrer Anwendung in Windows Dev Center

Bevor Sie mit der Windows Store-Sammlungs-API oder -Einkaufs-API eine Anwendung oder ein Add-on ausführen können, müssen Sie Ihre Azure AD-Client-ID der App im Windows Dev Center-Dashboard zuordnen.

>**Hinweis**&nbsp;&nbsp;Sie müssen diesen Schritt nur einmal ausführen.

1.  Melden Sie sich beim [Windows Dev Center-Dashboard](https://dev.windows.com/overview) an, und wählen Sie Ihre App aus.
2.  Geben Sie auf der Seite **Dienste** &gt; **Produktsammlungen und Einkäufe** Ihre Azure AD-Client-ID in eines der verfügbaren Felder ein.

<span id="step-3"/>
### <a name="step-3-create-azure-ad-access-tokens"></a>Schritt 3: Erstellen von Azure AD-Zugriffstokens

Bevor Sie einen Windows Store-ID-Schlüssel abrufen oder die Windows Store-Sammlungs-API oder -Einkaufs-API aufrufen können, muss Ihr Dienst mehrere verschiedene Azure AD-Zugriffstokens erstellen, die Ihre Herausgeberidentität darstellen. Jedes Token wird mit einer anderen API verwendet. Jedes Token ist 60 Minuten gültig und kann nach Ablauf aktualisiert werden.

<span id="access-tokens" />
#### <a name="understanding-the-different-tokens-and-audience-uris"></a>Grundlegendes zu den unterschiedlichen Tokens und Zielgruppen-URIs

Je nach den Methoden, die Sie in der Windows Store-Sammlungs-API oder -Einkaufs-API aufrufen möchten, müssen Sie zwei oder drei unterschiedliche Tokens erstellen. Jedes Zugriffstoken ist einem anderen Zielgruppen-URI zugeordnet (Hierbei handelt es sich um die gleichen URIs, die Sie zuvor dem `"identifierUris"`-Abschnitt des Azure AD-Anwendungsmanifests hinzugefügt haben).

  * In allen Fällen müssen Sie ein Token mit dem `https://onestore.microsoft.com`-Zielgruppen-URI erstellen. In einem späteren Schritt übergeben Sie dieses Token an den **Autorisierung**-Kopf der Methoden in der Windows Store-Sammlungs- oder -Einkaufs-API.

  > **Wichtig**&nbsp;&nbsp;Verwenden Sie die Zielgruppe `https://onestore.microsoft.com` nur mit Zugriffstokens, die sicher in Ihrem Dienst gespeichert sind. Durch das Verfügbarmachen von Zugriffstokens mit dieser Zielgruppe außerhalb Ihres Diensts kann dieser anfällig für Replay-Angriffe werden.

  * Wenn Sie eine Methode in der Windows Store-Sammlungs-API zur [Abfrage von Produkten, die einem Benutzer gehören](query-for-products.md) oder zum [Melden eines Verbrauchsprodukts als erfüllt](report-consumable-products-as-fulfilled.md) aufrufen möchten, müssen Sie auch ein Token mit dem `https://onestore.microsoft.com/b2b/keys/create/collections`-Zielgruppen-URI erstellen. In einem späteren Schritt übergeben Sie dieses Token an eine Client-Methode im Windows SDK zur Abfrage eines Windows Store-ID-Schlüssels, den Sie mit der Windows Store-Sammlungs-API verwenden können.

  * Wenn Sie eine Methode in der Windows Store-Einkaufs-API zum [Gewähren eines kostenlosen Produkts für einen Benutzer](grant-free-products.md) aufrufen möchten, müssen Sie auch ein Token mit dem `https://onestore.microsoft.com/b2b/keys/create/purchase`-Zielgruppen-URI erstellen. In einem späteren Schritt übergeben Sie dieses Token an eine Client-Methode im Windows SDK zur Abfrage eines Windows Store-ID-Schlüssels, den Sie mit der Windows Store-Einkaufs-API verwenden können.

<span />
#### <a name="how-to-create-the-tokens"></a>So erstellen Sie die Tokens:

Verwenden Sie zum Erstellen der Zugriffstokens die OAuth 2.0-API in Ihrem Dienst gemäß den Anweisungen in [Aufrufe zwischen Diensten mithilfe von Clientanmeldeinformationen](https://azure.microsoft.com/documentation/articles/active-directory-protocols-oauth-service-to-service), um einen HTTP POST an den ```https://login.microsoftonline.com/<tenant_id>/oauth2/token```-Endpunkt zu senden. Hier ist ein Beispiel für eine Anforderung angegeben.

``` syntax
POST https://login.microsoftonline.com/<tenant_id>/oauth2/token HTTP/1.1
Host: login.microsoftonline.com
Content-Type: application/x-www-form-urlencoded; charset=utf-8

grant_type=client_credentials
&client_id=<your_client_id>
&client_secret=<your_client_secret>
&resource=https://onestore.microsoft.com
```

Geben Sie für jedes Token die folgenden Parameterdaten an:

* Geben Sie für den *client\_id*-Parameter und den *client\_secret*-Parameter die Client-ID und das Clientgeheimnis Ihrer Anwendung aus dem [Azure-Verwaltungsportal](http://manage.windowsazure.com) an. Beide Parameter sind erforderlich, um ein Zugriffstoken mit der Authentifizierungsebene zu erstellen, die für die Windows Store-Sammlungs-API oder -Einkaufs-API benötigt wird.

* Geben Sie für den Parameter *Ressource* einen der Zielgruppen-URIs aus dem [vorherigen Abschnitt](#access-tokens) an, je nach der Art des Zugriffstokens, den Sie erstellen.

Nachdem das Zugriffstoken abgelaufen ist, können Sie es aktualisieren, indem Sie [diese Anleitung](https://azure.microsoft.com/documentation/articles/active-directory-protocols-oauth-code/#refreshing-the-access-tokens) befolgen. Weitere Informationen zur Struktur eines Zugriffstokens finden Sie unter [Unterstützte Token- und Anspruchstypen](http://go.microsoft.com/fwlink/?LinkId=722501).

> **Wichtig:**&nbsp;&nbsp;Azure AD-Zugriffstoken sollten nur im Kontext Ihres Diensts und nicht in Ihrer App erstellt werden. Ihr Clientgeheimnis könnte gefährdet sein, wenn es an Ihre App gesendet wird.

<span id="step-4"/>
### <a name="step-4-create-a-windows-store-id-key"></a>Schritt 4: Erstellen eines Windows Store-ID-Schlüssels

Bevor Sie eine Methode in der Windows Store-Sammlungs- oder -Einkaufs-API aufrufen können, muss Ihr Dienst einen Windows Store-ID-Schlüssel erstellen. Hierbei handelt es sich um ein JSON Web Token (JWT), das die Identität des Benutzers darstellt, auf dessen Produktbesitzerinformationen Sie zugreifen möchten. Weitere Informationen zu den Ansprüchen in diesem Schlüssel finden Sie unter [Ansprüche in einem Windows Store-ID-Schlüssel](#claims).

Derzeit kann ein Windows Store-ID-Schlüssel ausschließlich durch Aufrufen einer UWP-API im clientseitigen Code Ihrer App erstellt werden. Der generierte Schlüssel repräsentiert die Identität des Benutzers, der derzeit auf dem Gerät beim Windows Store angemeldet ist.

> **Hinweis:**&nbsp;&nbsp;Jeder Windows Store-ID-Schlüssel ist 90 Tage gültig. Nach dem Ablauf eines Schlüssels können Sie [den Schlüssel verlängern](renew-a-windows-store-id-key.md). Wir empfehlen, Windows Store-ID-Schlüssel zu verlängern, anstatt neue zu erstellen.

<span />
#### <a name="to-create-a-windows-store-id-key-for-the-windows-store-collection-api"></a>So erstellen Sie einen Windows Store-ID-Schlüssel für die Windows Store-Sammlungs-API:

Gehen Sie wie folgt vor, um einen Windows Store-ID-Schlüssel zu erstellen, den Sie mit der Windows Store-Sammlungs-API zur [Abfrage von Produkten, die einem Benutzer gehören](query-for-products.md) oder zum [Melden eines Verbrauchsprodukts als erfüllt](report-consumable-products-as-fulfilled.md) verwenden können.

1.  Übergeben Sie das Azure AD-Zugriffstoken, das Sie mit dem `https://onestore.microsoft.com/b2b/keys/create/collections`-Zielgruppen-URI erstellt haben, aus Ihrem Dienst an Ihre Client-App.

2.  Rufen Sie in Ihrem App-Code diese Methoden auf, um einen Windows Store-ID-Schlüssel abzurufen:

  * Wenn Ihre App die [StoreContext](https://msdn.microsoft.com/library/windows/apps/windows.services.store.storecontext.aspx)-Klasse im [Windows.Services.Store](https://msdn.microsoft.com/library/windows/apps/windows.services.store.aspx)-Namespace zur Verwaltung von In-App-Käufen verwendet, verwenden Sie die Methode [StoreContext.GetCustomerCollectionsIdAsync](https://msdn.microsoft.com/library/windows/apps/windows.services.store.storecontext.getcustomercollectionsidasync.aspx).

  * Wenn Ihre App die [CurrentApp](https://msdn.microsoft.com/library/windows/apps/hh779765) -Klasse im [Windows.ApplicationModel.Store](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.store.aspx) -Namespace zur Verwaltung von In-App-Käufen verwendet, verwenden Sie die Methode [CurrentApp.GetCustomerCollectionsIdAsync](https://msdn.microsoft.com/library/windows/apps/mt608674).

  Übergeben Sie Ihr Azure AD-Zugriffstoken an den *serviceTicket*-Parameter der Methode. Sie können optional eine ID an den *publisherUserId*-Parameter übergeben, der den aktuellen Benutzer im Kontext Ihrer Dienste identifiziert. Wenn Sie Benutzer-IDs für Ihre Dienste verwalten, können Sie diesen Parameter verwenden, um die Benutzer-IDs mit den Aufrufen an die Windows Store-Sammlungs-API zu korrelieren.

3.  Übergeben Sie den von Ihrer App erfolgreich abgerufenen Windows Store-ID-Schlüssel zurück an Ihren Dienst.

<span />
#### <a name="to-create-a-windows-store-id-key-for-the-windows-store-purchase-api"></a>So erstellen Sie einen Windows Store-ID-Schlüssel für die Windows Store-Einkaufs-API:

Befolgen Sie diese Schritte, um einen Windows Store-ID-Schlüssel zu erstellen, mit dem Sie mit der Windows Store-Einkaufs-API [einem Benutzer ein kostenloses Produkt gewähren](grant-free-products.md) können.

1.  Übergeben Sie das Azure AD-Zugriffstoken, das Sie mit dem `https://onestore.microsoft.com/b2b/keys/create/purchase`-Zielgruppen-URI erstellt haben, aus Ihrem Dienst an Ihre Client-App.

2.  Rufen Sie in Ihrem App-Code diese Methoden auf, um einen Windows Store-ID-Schlüssel abzurufen:

  * Wenn Ihre App die [StoreContext](https://msdn.microsoft.com/library/windows/apps/windows.services.store.storecontext.aspx)-Klasse im [Windows.Services.Store](https://msdn.microsoft.com/library/windows/apps/windows.services.store.aspx)-Namespace zur Verwaltung von In-App-Käufen verwendet, verwenden Sie die Methode [StoreContext.GetCustomerPurchaseIdAsync](https://msdn.microsoft.com/library/windows/apps/windows.services.store.storecontext.getcustomerpurchaseidasync.aspx).

  * Wenn Ihre App die [CurrentApp](https://msdn.microsoft.com/library/windows/apps/hh779765) -Klasse im [Windows.ApplicationModel.Store](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.store.aspx) -Namespace zur Verwaltung von In-App-Käufen verwendet, verwenden Sie die Methode [CurrentApp.GetCustomerPurchaseIdAsync](https://msdn.microsoft.com/library/windows/apps/mt608675).

  Übergeben Sie Ihr Azure AD-Zugriffstoken an den *serviceTicket*-Parameter der Methode. Sie können optional eine ID an den *publisherUserId*-Parameter übergeben, der den aktuellen Benutzer im Kontext Ihrer Dienste identifiziert. Wenn Sie Benutzer-IDs für Ihre Dienste verwalten, können Sie diesen Parameter verwenden, um die Benutzer-IDs mit den Aufrufen an die Windows Store-Einkaufs-API zu korrelieren.

3.  Übergeben Sie den von Ihrer App erfolgreich abgerufenen Windows Store-ID-Schlüssel zurück an Ihren Dienst.

<span id="step-5"/>
### <a name="step-5-call-the-windows-store-collection-api-or-purchase-api-from-your-service"></a>Schritt 5: Aufrufen der Windows Store-Sammlungs-API oder -Einkaufs-API aus Ihrem Dienst

Wenn Ihr Dienst über einen Windows Store-ID-Schlüssel verfügt, der den Zugriff auf die Produkteigentümerinformationen eines bestimmten Benutzers ermöglicht, kann der Dienst wie folgt die Windows Store-Sammlungs-API oder -Einkaufs-API aufrufen.

* [Produktabfrage](query-for-products.md)
* [Melden von Verbrauchsprodukten als erfüllt](report-consumable-products-as-fulfilled.md)
* [Gewähren kostenloser Produkte](grant-free-products.md)

Übergeben Sie bei jedem Szenario die folgenden Informationen an die API:

-   Das Azure AD-Zugriffstoken, das Sie zuvor mit dem Zielgruppen-URI `https://onestore.microsoft.com` erstellt haben. Dieses Token stellt die Herausgeberidentität dar. Übergeben Sie das Token im Anforderungsheader.
-   Den Windows Store-ID-Schlüssel, den Sie aus clientseitigem Code in Ihrer App abgerufen haben. Dieser Schlüssel stellt die Identität des Benutzers dar, auf dessen Produktbesitzerinformationen Sie zugreifen möchten.

<span id="claims"/>
## <a name="claims-in-a-windows-store-id-key"></a>Ansprüche in einem Windows Store-ID-Schlüssel

Ein Windows Store-ID-Schlüssel ist ein JSON Web Token (JWT), das die Identität des Benutzers darstellt, auf dessen Produktbesitzerinformationen Sie zugreifen möchten. Bei der Decodierung unter Verwendung von Base64 enthält ein Windows Store-ID-Schlüssel die folgenden Ansprüche.

* `iat`:&nbsp;&nbsp;&nbsp;Gibt den Ausgabezeitpunkt des Schlüssels an. Mit diesem Anspruch kann das Alter des Tokens bestimmt werden. Dieser Wert wird als Epoche ausgedrückt.
* `iss`:&nbsp;&nbsp;&nbsp;Gibt den Aussteller an. Dieser hat den gleichen Wert wie der `aud`-Anspruch.
* `aud`:&nbsp;&nbsp;&nbsp;Gibt die Zielgruppe an. Muss einem der folgenden Werte entsprechen: `https://collections.mp.microsoft.com/v6.0/keys` oder `https://purchase.mp.microsoft.com/v6.0/keys`.
* `exp`:&nbsp;&nbsp;&nbsp;Gibt die Ablaufzeit an, nach der der Schlüssel nicht mehr für Verarbeitungsvorgänge akzeptiert wird, außer für die Verlängerung von Schlüsseln. Der Wert dieses Anspruchs wird als Epoche ausgedrückt.
* `nbf`&nbsp;&nbsp;&nbsp;Gibt die Zeit an, zu der das Token für die Verarbeitung akzeptiert wird. Der Wert dieses Anspruchs wird als Epoche ausgedrückt.
* `http://schemas.microsoft.com/marketplace/2015/08/claims/key/clientId`:&nbsp;&nbsp;&nbsp;Die Client-ID, die den Entwickler angibt.
* `http://schemas.microsoft.com/marketplace/2015/08/claims/key/payload`:&nbsp;&nbsp;&nbsp;Eine opake (verschlüsselte und Base64-codierte) Nutzlast mit Informationen, die ausschließlich von Windows Store-Diensten verwendet werden sollen.
* `http://schemas.microsoft.com/marketplace/2015/08/claims/key/userId`:&nbsp;&nbsp;&nbsp;Eine Benutzer-ID, die den aktuellen Benutzer im Kontext Ihrer Dienste angibt. Dies ist der gleiche Wert, den Sie an den optionalen *publisherUserId*-Parameter der [Methode zum Erstellen des Schlüssels](#step-4) übergeben.
* `http://schemas.microsoft.com/marketplace/2015/08/claims/key/refreshUri`:&nbsp;&nbsp;&nbsp;Der URI, mit dem Sie den Schlüssel verlängern können.

Hier ist ein Beispiel für einen decodierten Windows Store-ID-Schlüsselkopf.

```json
{
    "typ":"JWT",
    "alg":"RS256",
    "x5t":"agA_pgJ7Twx_Ex2_rEeQ2o5fZ5g"
}
```

Hier ein Beispiel für einen decodierten Satz von Windows Store-ID-Schlüsselansprüchen.

```json
{
    "http://schemas.microsoft.com/marketplace/2015/08/claims/key/clientId": "1d5773695a3b44928227393bfef1e13d",
    "http://schemas.microsoft.com/marketplace/2015/08/claims/key/payload": "ZdcOq0/N2rjytCRzCHSqnfczv3f0343wfSydx7hghfu0snWzMqyoAGy5DSJ5rMSsKoQFAccs1iNlwlGrX+/eIwh/VlUhLrncyP8c18mNAzAGK+lTAd2oiMQWRRAZxPwGrJrwiq2fTq5NOVDnQS9Za6/GdRjeiQrv6c0x+WNKxSQ7LV/uH1x+IEhYVtDu53GiXIwekltwaV6EkQGphYy7tbNsW2GqxgcoLLMUVOsQjI+FYBA3MdQpalV/aFN4UrJDkMWJBnmz3vrxBNGEApLWTS4Bd3cMswXsV9m+VhOEfnv+6PrL2jq8OZFoF3FUUpY8Fet2DfFr6xjZs3CBS1095J2yyNFWKBZxAXXNjn+zkvqqiVRjjkjNajhuaNKJk4MGHfk2rZiMy/aosyaEpCyncdisHVSx/S4JwIuxTnfnlY24vS0OXy7mFiZjjB8qL03cLsBXM4utCyXSIggb90GAx0+EFlVoJD7+ZKlm1M90xO/QSMDlrzFyuqcXXDBOnt7rPynPTrOZLVF+ODI5HhWEqArkVnc5MYnrZD06YEwClmTDkHQcxCvU+XUEvTbEk69qR2sfnuXV4cJRRWseUTfYoGyuxkQ2eWAAI1BXGxYECIaAnWF0W6ThweL5ZZDdadW9Ug5U3fZd4WxiDlB/EZ3aTy8kYXTW4Uo0adTkCmdLibw=",
    "http://schemas.microsoft.com/marketplace/2015/08/claims/key/userId": "infusQMLaYCrgtC0d/SZWoPB4FqLEwHXgZFuMJ6TuTY=",
    "http://schemas.microsoft.com/marketplace/2015/08/claims/key/refreshUri": "https://collections.mp.microsoft.com/v6.0/b2b/keys/renew",
    "iat": 1442395542,
    "iss": "https://collections.mp.microsoft.com/v6.0/keys",
    "aud": "https://collections.mp.microsoft.com/v6.0/keys",
    "exp": 1450171541,
    "nbf": 1442391941
}
```

## <a name="related-topics"></a>Verwandte Themen

* [Produktabfrage](query-for-products.md)
* [Melden von Verbrauchsprodukten als erfüllt](report-consumable-products-as-fulfilled.md)
* [Gewähren kostenloser Produkte](grant-free-products.md)
* [Verlängern eines Windows Store-ID-Schlüssels](renew-a-windows-store-id-key.md)
* [Integrieren von Anwendungen in Azure Active Directory](http://go.microsoft.com/fwlink/?LinkId=722502)
* [Grundlegendes zum Azure Active Directory-Anwendungsmanifest]( http://go.microsoft.com/fwlink/?LinkId=722500)
* [Unterstützte Token- und Anspruchstypen](http://go.microsoft.com/fwlink/?LinkId=722501)

