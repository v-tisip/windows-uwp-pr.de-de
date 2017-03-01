---
author: mcleanbyron
ms.assetid: 8e6c3d3d-0120-40f4-9f90-0b0518188a1a
description: "Mit der Werbungs-API des Windows Store verwalten Sie programmgesteuert Werbeanzeigenkampagnen für Apps, die für Ihr Windows Dev Center-Konto oder das Ihrer Organisation registriert sind."
title: "Durchführen von Anzeigenkampagnen mit Windows Store-Diensten"
ms.author: mcleans
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, Windows Store Werbungs-API, Anzeigenkampagnen
translationtype: Human Translation
ms.sourcegitcommit: 5645eee3dc2ef67b5263b08800b0f96eb8a0a7da
ms.openlocfilehash: ec245f07098a662c80517de49ba5637a69b30f35
ms.lasthandoff: 02/08/2017

---

# <a name="run-ad-campaigns-using-windows-store-services"></a>Durchführen von Anzeigenkampagnen mit Windows Store-Diensten

Mit der *Werbungs-API des Windows Store* verwalten Sie programmgesteuert Werbeanzeigenkampagnen für Apps, die für Ihr Windows Dev Center-Konto oder das Ihrer Organisation registriert sind. Mit dieser API können Sie Ihre Kampagnen und andere zugehörige Ressourcen, z. B. Zielgruppen und Werbemittel, erstellen, aktualisieren und überwachen. Diese API ist besonders für Entwickler nützlich, die umfangreiche Kampagnen erstellen und dies nicht im Windows Dev Center-Dashboards ausführen möchten. Diese API verwendet Azure Active Directory (Azure AD), um die Aufrufe von Ihrer App oder Ihrem Dienst zu authentifizieren.

Dazu müssen folgende Schritte ausgeführt werden:

1.  Stellen Sie sicher, dass Sie alle [Voraussetzungen](#prerequisites) erfüllt haben.
2.  Vor dem Aufrufen einer Methode in der Windows Store-Werbungs-API müssen Sie [ein Azure AD-Zugriffstoken anfordern](#obtain-an-azure-ad-access-token). Nach dem Abruf eines Zugriffstokens können Sie es für einen Zeitraum von 60 Minuten in Aufrufen der Windows Store-Werbungs-API verwenden, bevor es abläuft. Nach dem Ablauf des Tokens können Sie ein neues Token generieren.
3.  [Aufrufen der Windows Store-Werbungs-API](#call-the-windows-store-promotions-api).

Sie können Anzeigenkampagnen alternativ mit dem Windows Dev Center-Dashboard erstellen und verwalten, und auf alle Anzeigenkampagnen, die Sie programmgesteuert über die Windows Store-Werbungs-API erstellen, kann auch im Dashboard zugegriffen werden. Weitere Informationen zur Verwaltung von Anzeigenkampagnen im Dashboard finden Sie unter [Erstellen einer Anzeigenkampagne für Ihre App](../publish/create-an-ad-campaign-for-your-app.md).

>**Hinweis**&nbsp;&nbsp;Alle Entwickler mit einem Windows Dev Center-Konto können die Windows Store-Werbungs-API verwenden, um Anzeigenkampagnen für ihre Apps zu verwalten. Medienagenturen können auch den Zugriff auf diese API anfordern, um Anzeigenkampagnen für ihre Werbekunden durchzuführen. Wenn Sie einer Medienagentur angehören und weitere Informationen zu dieser API wünschen oder den Zugriff darauf anfordern möchten, senden Sie Ihre Anfrage an storepromotionsapi@microsoft.com.

<span id="prerequisites" />
## <a name="step-1-complete-prerequisites-for-using-the-windows-store-promotions-api"></a>Schritt 1: Erfüllen der Voraussetzungen für die Verwendung der Windows Store-Werbungs-API

Stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllt haben, bevor Sie mit dem Schreiben von Code zum Aufrufen der Windows Store-Werbungs-API beginnen.

* Sie (bzw. Ihre Organisation) müssen über ein Azure AD-Verzeichnis und die Berechtigung [Globaler Administrator](http://go.microsoft.com/fwlink/?LinkId=746654) für das Verzeichnis verfügen. Wenn Sie bereits mit Office 365 oder anderen Unternehmensdiensten von Microsoft arbeiten, verfügen Sie schon über ein Azure AD-Verzeichnis. Andernfalls können Sie [innerhalb von Dev Center ohne zusätzliche Kosten eine neue Azure AD-Instanz erstellen](https://msdn.microsoft.com/windows/uwp/publish/manage-account-users).

* Sie müssen Ihrem Dev Center-Konto eine Azure AD-Anwendung zuordnen, die Mandanten-ID und die Client-ID für die Anwendung abrufen und einen Schlüssel generieren. Die Azure AD-Anwendung stellt die App oder den Dienst dar, aus denen Sie die Windows Store-Werbungs-API aufrufen möchten. Sie benötigen die Mandanten-ID, die Client-ID und den Schlüssel zum Abrufen eines Azure AD-Zugriffstokens, das Sie an die API übergeben.

  >**Hinweis**&nbsp;&nbsp;Sie müssen diesen Schritt nur einmal ausführen. Wenn Sie im Besitz der Mandanten-ID, der Client-ID und des Schlüssel sind, können Sie diese Daten jederzeit wiederverwenden, um ein neues Azure AD-Zugriffstoken zu erstellen.

Gehen Sie wie folgt vor, um Ihrem Dev Center-Konto eine Azure AD-Anwendung zuzuordnen und die erforderlichen Werte abzurufen:

1.  Rufen Sie in Dev Center die **Kontoeinstellungen** auf, klicken Sie auf **Benutzer verwalten**, und ordnen Sie das Dev Center-Konto Ihrer Organisation dem Azure AD-Verzeichnis Ihrer Organisation zu. Ausführliche Anweisungen finden Sie unter [Verwalten von Kontobenutzern](https://msdn.microsoft.com/windows/uwp/publish/manage-account-users).

2.  Klicken Sie auf der Seite **Benutzer verwalten** auf **Azure AD-Apps hinzufügen**, und fügen Sie die Azure AD-Anwendung hinzu, die die App oder den Dienst darstellt, mit denen Sie Werbekampagnen für Ihr Dev Center-Konto verwalten. Weisen Sie ihr anschließend die Rolle **Manager** zu. Wenn diese Anwendung bereits in Ihrem Azure AD-Verzeichnis vorhanden ist, können Sie sie auf der Seite **Azure AD-Apps hinzufügen** auswählen, um sie Ihrem Dev Center-Konto hinzuzufügen. Andernfalls können Sie eine neue Azure AD-Anwendung auf der Seite **Azure AD-Apps hinzufügen** erstellen. Weitere Informationen finden Sie unter [Hinzufügen und Verwalten von Azure AD-Apps](https://msdn.microsoft.com/windows/uwp/publish/manage-account-users#add-and-manage-azure-ad-applications).

3.  Wechseln Sie zurück zur Seite **Benutzer verwalten**, klicken Sie auf den Namen Ihrer Azure AD-Anwendung, um die Anwendungseinstellungen aufzurufen, und kopieren Sie die Werte unter **Mandanten-ID** und **Client-ID**.

4. Klicken Sie auf **Neuen Schlüssel hinzufügen**. Kopieren Sie auf dem folgenden Bildschirm den Wert unter **Schlüssel**. Nach dem Verlassen der Seite können Sie nicht mehr auf diese Informationen zugreifen. Weitere Informationen zum Verwalten von Schlüsseln finden Sie unter [Hinzufügen und Verwalten von Azure AD-Apps](https://msdn.microsoft.com/windows/uwp/publish/manage-account-users#add-and-manage-azure-ad-applications).

<span id="obtain-an-azure-ad-access-token" />
## <a name="step-2-obtain-an-azure-ad-access-token"></a>Schritt 2: Abrufen eines Azure AD-Zugriffstokens

Bevor Sie die Methoden in der Windows Store-Werbungs-API aufrufen, müssen Sie zuerst ein Azure AD-Zugriffstoken abrufen, das Sie an den **Authorization**-Header der einzelnen Methoden in der API übergeben. Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft. Nachdem das Token abgelaufen ist, können Sie es aktualisieren, um es in weiteren Aufrufen an die API zu verwenden.

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

Geben Sie für den Wert *tenant\_id* im POST-URI und die Parameter *client\_id* und *client\_secret* die Mandanten-ID, die Client-ID und den Schlüssel für Ihre Anwendung an, die Sie im vorherigen Abschnitt aus Dev Center abgerufen haben. Für den Parameter *resource* müssen Sie ```https://manage.devcenter.microsoft.com``` angeben.

Nachdem das Zugriffstoken abgelaufen ist, können Sie es aktualisieren, indem Sie [diese Anleitung](https://azure.microsoft.com/documentation/articles/active-directory-protocols-oauth-code/#refreshing-the-access-tokens) befolgen.

<span id="call-the-windows-store-promotions-api" />
## <a name="step-3-call-the-windows-store-promotions-api"></a>Schritt 3: Aufrufen der Windows Store-Werbungs-API

Nachdem Sie ein Azure AD-Zugriffstoken abgerufen haben, können Sie die Windows Store-Werbungs-API aufrufen. Sie müssen das Zugriffstoken an den **Authorization**-Header der einzelnen Methoden übergeben.

Im Kontext der Windows Store-Werbungs-API besteht eine Anzeigenkampagne aus einem *Kampagne*-Objekt, das allgemeine Informationen zur Kampagne enthält, und weiteren Objekten, die die *Lieferpositionen*, *Zielgruppenprofile* und *Werbemittel* für die Anzeigenkampagne darstellen. Die API enthält unterschiedliche Methodensätze, die nach diesen Objekttypen gruppiert sind. Um eine Kampagne zu erstellen, rufen Sie normalerweise für jedes dieser Objekte eine andere POST-Methode auf. Die API bietet auch GET-Methoden, die Sie verwenden können, um ein Objekt abzurufen, und PUT-Methoden, mit denen Sie die Objekte „Kampagne”, „Lieferposition” und „Zielgruppenprofil” bearbeiten können.

Weitere Informationen zu diesen Objekten und den zugehörigen Methoden finden Sie in der folgenden Tabelle:


| Objekt       | Beschreibung   |
|---------------|-----------------|
| Kampagnen |  Dieses Objekt stellt die Anzeigenkampagne dar und befindet sich an der Spitze der Objektmodellhierarchie für Anzeigenkampagnen. Dieses Objekt gibt den Typ der Kampagne, die Sie durchführen (bezahlt, Eigenwerbung oder Community), das Ziel der Kampagne, die Lieferpositionen für die Kampagne und andere Details an. Jede Kampagne kann nur einer App zugeordnet werden.<br/><br/>Weitere Informationen zu den Methoden für dieses Objekt finden Sie unter [Verwalten von Anzeigenkampagnen](manage-ad-campaigns.md).<br/><br/>**Hinweis**&nbsp;&nbsp;Nach dem Erstellen einer Anzeigenkampagne können Sie mit der Methode [Abrufen der Leistungsdaten einer Anzeigenkampagne](get-ad-campaign-performance-data.md) in der [Windows Store-Analyse-API](access-analytics-data-using-windows-store-services.md) Leistungsdaten für die Kampagne abrufen.  |
| Lieferpositionen | Jede Kampagne verfügt über eine oder mehrere Lieferpositionen, die zum Kaufen von Inventar und Übermitteln Ihrer Anzeigen verwendet werden. Für jede Lieferposition können Sie Zielgruppen und Ihren Angebotspreis festlegen sowie entscheiden, wie viel Sie ausgeben möchten, indem Sie ein Budget angeben und eine Verknüpfung zu den Werbemitteln herstellen, die Sie verwenden möchten.<br/><br/>Weitere Informationen zu den Methoden für dieses Objekt finden Sie unter [Verwalten von Lieferpositionen für Anzeigenkampagnen](manage-delivery-lines-for-ad-campaigns.md). |
| Zielgruppenprofile | Jede Lieferposition verfügt über ein Zielgruppenprofil, das die Benutzer, Regionen und Inventartypen für die Zielgruppe angibt. Zielgruppenprofile können als Vorlage erstellt und für alle Lieferpositionen gemeinsam genutzt werden.<br/><br/>Weitere Informationen zu den Methoden für dieses Objekt finden Sie unter [Verwalten von Zielgruppenprofilen für Anzeigenkampagnen](manage-targeting-profiles-for-ad-campaigns.md). |
| Werbemittel | Jede Lieferposition verfügt über ein oder mehrere Werbemittel, die die Anzeigen darstellen, die im Rahmen der Kampagne für Kunden angezeigt werden. Ein Werbemittel kann einer oder mehreren Lieferpositionen sogar in verschiedenen Anzeigenkampagnen, sofern es sich immer um dieselbe App handelt, zugeordnet werden.<br/><br/>Weitere Informationen zu den Methoden für dieses Objekt finden Sie unter [Verwalten von Werbemitteln für Anzeigenkampagnen](manage-creatives-for-ad-campaigns.md). |


Das folgende Diagramm zeigt die Beziehung zwischen Kampagnen, Lieferpositionen, Zielgruppenprofilen und Werbemitteln.

![Hierarchie von Anzeigenkampagnen](images/ad-campaign-hierarchy.png)

## <a name="code-example"></a>Codebeispiel

Im folgenden Codebeispiel wird gezeigt, wie Sie ein Azure AD-Zugriffstoken abrufen und die Windows Store-Werbungs-API aus einer C#-Konsolen-App aufrufen. Wenn Sie dieses Codebeispiel verwenden möchten, weisen Sie den Variablen *tenantId*, *clientId*, *clientSecret* und *appID* die entsprechenden Werte für Ihr Szenario zu. In diesem Beispiel wird das [Json.NET-Paket](http://www.newtonsoft.com/json) von Newtonsoft benötigt, um die von der Windows Store-Werbungs-API zurückgegebenen JSON-Daten zu deserialisieren.

> [!div class="tabbedCodeSnippets"]
[!code-cs[PromotionsApi](./code/StoreServicesExamples_Promotions/cs/Program.cs#PromotionsApiExample)]

## <a name="related-topics"></a>Verwandte Themen

* [Verwalten von Anzeigenkampagnen](manage-ad-campaigns.md)
* [Verwalten von Lieferpositionen für Anzeigenkampagnen](manage-delivery-lines-for-ad-campaigns.md)
* [Verwalten von Zielgruppenprofilen für Anzeigenkampagnen](manage-targeting-profiles-for-ad-campaigns.md)
* [Verwalten von Werbemitteln für Anzeigenkampagnen](manage-creatives-for-ad-campaigns.md)
* [Abrufen der Leistungsdaten einer Anzeigenkampagne](get-ad-campaign-performance-data.md)


 

