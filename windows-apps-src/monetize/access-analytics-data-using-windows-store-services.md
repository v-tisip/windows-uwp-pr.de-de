---
author: mcleanbyron
ms.assetid: 4BF9EF21-E9F0-49DB-81E4-062D6E68C8B1
description: Verwenden Sie zum programmgesteuerten Abrufen von Analysedaten für Apps, die für Ihr WindowsDevCenter-Konto oder für das Konto Ihrer Organisation registriert sind, die Microsoft Store-Analyse-API.
title: Zugreifen auf Analysedaten mit Store-Diensten
ms.author: mcleans
ms.date: 03/23/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Store-Dienste Microsoft Store-Analyse-API
ms.localizationpriority: medium
ms.openlocfilehash: 0a8523acb06a0bda48f85221f384d8a3d554c7dc
ms.sourcegitcommit: 346b5c9298a6e9e78acf05944bfe13624ea7062e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/05/2018
ms.locfileid: "1707155"
---
# <a name="access-analytics-data-using-store-services"></a>Zugreifen auf Analysedaten mit Store-Diensten

Verwenden Sie zum programmgesteuerten Abrufen von Analysedaten für Apps, die für Ihr Windows Dev Center-Konto oder für das Konto Ihrer Organisation registriert sind, die *Microsoft Store-Analyse-API*. Mit dieser API können Sie Daten zum Kauf von Apps und Add-Ons (auch als In-App-Produkte (IAPs) bezeichnet), Fehler, App-Bewertungen und App-Rezensionen abrufen. Diese API verwendet Azure Active Directory (Azure AD), um die Aufrufe von Ihrer App oder Ihrem Dienst zu authentifizieren.

Dazu müssen folgende Schritte ausgeführt werden:

1.  Vergewissern Sie sich, dass Sie alle [Voraussetzungen](#prerequisites) erfüllt haben.
2.  Vor dem Aufrufen einer Methode in der Microsoft Store-Analyse-API müssen Sie [ein AzureAD-Zugriffstoken anfordern](#obtain-an-azure-ad-access-token). Nach dem Abrufen eines Tokens haben Sie 60Minuten Zeit, um das Token zum Aufrufen der Microsoft Store-Analyse-API zu nutzen, bevor es abläuft. Nach dem Ablauf des Tokens können Sie ein neues Token generieren.
3.  [Aufrufen der Microsoft Store-Analyse-API](#call-the-windows-store-analytics-api).

<span id="prerequisites" />

## <a name="step-1-complete-prerequisites-for-using-the-microsoft-store-analytics-api"></a>Schritt1: Erfüllen der Voraussetzungen für die Verwendung der Microsoft Store-Analyse-API

Stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllt haben, bevor Sie mit dem Schreiben von Code zum Aufrufen der Microsoft Store-Analyse-API beginnen:

* Sie (bzw. Ihre Organisation) müssen über ein Azure AD-Verzeichnis und die Berechtigung [Globaler Administrator](http://go.microsoft.com/fwlink/?LinkId=746654) für das Verzeichnis verfügen. Wenn Sie bereits mit Office 365oder anderen Unternehmensdiensten von Microsoft arbeiten, verfügen Sie schon über ein Azure AD-Verzeichnis. Andernfalls können Sie [innerhalb von Dev Center ohne zusätzliche Kosten eine neue Azure AD-Instanz erstellen](../publish/associate-azure-ad-with-dev-center.md#create-a-brand-new-azure-ad-to-associate-with-your-dev-center-account).

* Sie müssen Ihrem Dev Center-Konto eine Azure AD-Anwendung zuordnen, die Mandanten-ID und die Client-ID für die Anwendung abrufen und einen Schlüssel generieren. Die Azure AD-Anwendung stellt die App oder den Dienst dar, aus denen Sie die Microsoft Store-Analyse-API aufrufen möchten. Sie benötigen die Mandanten-ID, die Client-ID und den Schlüssel zum Abrufen eines Azure AD-Zugriffstokens, das Sie an die API übergeben.
    > [!NOTE]
    > Sie müssen diesen Schritt nur einmal ausführen. Wenn Sie im Besitz der Mandanten-ID, der Client-ID und des Schlüssel sind, können Sie diese Daten jederzeit wiederverwenden, um ein neues Azure AD-Zugriffstoken zu erstellen.

Gehen Sie wie folgt vor, um Ihrem Dev Center-Konto eine Azure AD-Anwendung zuzuordnen und die erforderlichen Werte abzurufen:

1.  Rufen Sie in Dev Center die **Kontoeinstellungen** auf, klicken Sie auf **Benutzer verwalten**, und [ordnen Sie das Dev Center-Konto Ihrer Organisation dem Azure AD-Verzeichnis Ihrer Organisation zu](../publish/associate-azure-ad-with-dev-center.md).

2.  Klicken Sie auf der Seite **Benutzer verwalten** auf **Azure AD-Apps hinzufügen**, und fügen Sie die AzureAD-Anwendung hinzu, die die App oder den Dienst darstellt, mit dem Sie auf Analysedaten für Ihr Dev Center-Konto zugreifen. Weisen Sie ihr anschließend die Rolle **Manager** zu. Wenn diese Anwendung bereits in Ihrem AzureAD-Verzeichnis vorhanden ist, können Sie sie auf der Seite **Azure AD-Apps hinzufügen** auswählen, um sie Ihrem Dev Center-Konto hinzuzufügen. Andernfalls können Sie eine neue Azure AD-Anwendung auf der Seite **Azure AD-Apps hinzufügen** erstellen. Weitere Informationen finden Sie unter [Hinzufügen von Azure AD-Anwendungen zu Ihrem Dev Center-Konto](../publish/add-users-groups-and-azure-ad-applications.md#azure-ad-applications).

3.  Wechseln Sie zurück zur Seite **Benutzer verwalten**, klicken Sie auf den Namen Ihrer Azure AD-Anwendung, um die Anwendungseinstellungen aufzurufen, und kopieren Sie die Werte unter **Mandanten-ID** und **Client-ID**.

4. Klicken Sie auf **Neuen Schlüssel hinzufügen**. Kopieren Sie auf dem folgenden Bildschirm den Wert unter **Schlüssel**. Nach dem Verlassen der Seite können Sie nicht mehr auf diese Informationen zugreifen. Weitere Informationen finden Sie unter [Verwalten von Schlüsseln für eine Azure AD-App](../publish/add-users-groups-and-azure-ad-applications.md#manage-keys).

<span id="obtain-an-azure-ad-access-token" />

## <a name="step-2-obtain-an-azure-ad-access-token"></a>Schritt 2: Abrufen eines AzureAD-Zugriffstokens

Bevor Sie die Methoden in der Microsoft Store-Analyse-API aufrufen, müssen Sie zuerst ein Azure AD-Zugriffstoken abrufen, das Sie für jede Methode in der API an den **Authorization**-Header übergeben. Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft. Nachdem das Token abgelaufen ist, können Sie es aktualisieren, um es in weiteren Aufrufen an die API zu verwenden.

Befolgen Sie zum Abrufen des Zugriffstokens die Anweisungen unter [Aufrufe zwischen Diensten mithilfe von Clientanmeldeinformationen](https://azure.microsoft.com/documentation/articles/active-directory-protocols-oauth-service-to-service/), um eine HTTP POST-Anforderung an den ```https://login.microsoftonline.com/<tenant_id>/oauth2/token```-Endpunkt zu senden. Hier ist ein Beispiel für eine Anforderung angegeben.

```
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

<span id="call-the-windows-store-analytics-api" />

## <a name="step-3-call-the-microsoft-store-analytics-api"></a>Schritt 3: Aufrufen der Microsoft Store-Analyse-API

Nachdem Sie ein AzureAD-Zugriffstoken abgerufen haben, können Sie die Microsoft Store-Analyse-API aufrufen. Sie müssen das Zugriffstoken an den **Authorization**-Header der einzelnen Methoden übergeben.

### <a name="methods-for-uwp-apps"></a>Methoden für UWP-Apps

Die folgenden Analysemethoden sind für UWP-Apps im Dev Center verfügbar.

| Szenario       | Methoden      |
|---------------|--------------------|
| Käufe, Konversionen und Installationen |  <ul><li>[Abrufen von App-Käufen](get-app-acquisitions.md)</li><li>[Abrufen von App-Erwerbstrichterdaten](get-acquisition-funnel-data.md)</li><li>[Abrufen von App-Konvertierungen nach Kanal](get-app-conversions-by-channel.md)</li><li>[Abrufen von Add-On-Käufen](get-in-app-acquisitions.md)</li><li>[Abrufen von Add-On-Käufen für Abonnements](get-subscription-acquisitions.md)</li><li>[Abrufen von Add-On-Konvertierungen nach Kanal](get-add-on-conversions-by-channel.md)</li><li>[Abrufen von App-Installationen](get-app-installs.md)</li></ul> |
| App-Fehler | <ul><li>[Abrufen von Fehlerberichtsdaten](get-error-reporting-data.md)</li><li>[Abrufen von Details zu einem Fehler in Ihrer App](get-details-for-an-error-in-your-app.md)</li><li>[Abrufen der Stapelüberwachung für einen Fehler in Ihrer App](get-the-stack-trace-for-an-error-in-your-app.md)</li><li>[Herunterladen der CAB-Datei bei einem Fehler in Ihrer App](download-the-cab-file-for-an-error-in-your-app.md)</li></ul> |
| Bewertungen und Prüfungen | <ul><li>[Abrufen von App-Bewertungen](get-app-ratings.md)</li><li>[Abrufen von App-Rezensionen](get-app-reviews.md)</li></ul> |
| In-App-Werbung und Anzeigenkampagnen | <ul><li>[Abrufen von Anzeigenleistungsdaten](get-ad-performance-data.md)</li><li>[Abrufen der Leistungsdaten einer Anzeigenkampagne](get-ad-campaign-performance-data.md)</li></ul> |

### <a name="methods-for-desktop-applications"></a>Methoden für Desktopanwendungen

Die folgenden Analysemethoden stehen für die Verwendung durch Entwicklerkonten zur Verfügung, die zum [Windows Desktop Application-Programm](https://msdn.microsoft.com/library/windows/desktop/mt826504) gehören.

| Szenario       | Methoden      |
|---------------|--------------------|
| Installiert |  <ul><li>[Abrufen von Desktopanwendungsinstallationen](get-desktop-app-installs.md)</li></ul> |
| Anwendungsfehler |  <ul><li>[Abrufen von Fehlerberichtsdaten für Ihre Desktopanwendung](get-desktop-application-error-reporting-data.md)</li><li>[Abrufen von Details zu einem Fehler in Ihrer Desktopanwendung](get-details-for-an-error-in-your-desktop-application.md)</li><li>[Abrufen der Stapelüberwachung für einen Fehler in Ihrer Desktopanwendung](get-the-stack-trace-for-an-error-in-your-desktop-application.md)</li><li>[Herunterladen der CAB-Datei bei einem Fehler in Ihrer Desktopanwendung](download-the-cab-file-for-an-error-in-your-desktop-application.md)</li></ul> |

### <a name="methods-for-hardware-and-drivers"></a>Methoden für Hardware und Treiber

Die folgenden Analysemethoden stehen für die Verwendung durch Entwicklerkonten zur Verfügung, die zum [Windows Hardware Dev Center-Programm](https://msdn.microsoft.com/windows/hardware/drivers/dashboard/get-started-with-the-hardware-dashboard) gehören.

| Szenario       | Methoden      |
|---------------|--------------------|
| Fehler in Windows10-Treibern (für IHVs) |  <ul><li>[Abrufen von Fehlerberichtsdaten für Windows10-Treiber](get-error-reporting-data-for-windows-10-drivers.md)</li><li>[Abrufen von Informationen zu einem Windows10-Treiberfehler](get-details-for-a-windows-10-driver-error.md)</li><li>[Herunterladen der CAB-Datei für einen Windows10-Treiberfehler](download-the-cab-file-for-a-windows-10-driver-error.md)</li></ul> |
| Fehler in Windows7-/Windows8.x-Treibern (für IHVs) |  <ul><li>[Abrufen von Fehlerberichtsdaten für Windows7- und Windows8.x-Treiber](get-error-reporting-data-for-windows-7-and-windows-8.x-drivers.md)</li><li>[Abrufen von Informationen zu einem Windows7- oder Windows8.x-Treiberfehler](get-details-for-a-windows-7-or-windows-8.x-driver-error.md)</li><li>[Herunterladen der CAB-Datei für einen Windows7- oder Windows8.x-Treiberfehler](download-the-cab-file-for-a-windows-7-or-windows-8.x-driver-error.md)</li></ul> |
| Hardwarefehler (für OEMs) |  <ul><li>[Abrufen von Fehlerberichtsdaten für OEM-Hardware](get-oem-hardware-error-reporting-data.md)</li><li>[Abrufen von Informationen zu einem OEM-Hardwarefehler](get-details-for-an-oem-hardware-error.md)</li><li>[Herunterladen der CAB-Datei für einen OEM-Hardwarefehler](download-the-cab-file-for-an-oem-hardware-error.md)</li></ul> |

### <a name="methods-for-xbox-live-services"></a>Methoden für Xbox Live-Dienste

Die folgenden zusätzlichen Methoden stehen für Entwicklerkonten mit Spielen zur Verfügung, die [Xbox Live-Dienste](../xbox-live/developer-program-overview.md) verwenden.

| Szenario       | Methoden      |
|---------------|--------------------|
| Allgemeine Analysen |  <ul><li>[Abrufen von Xbox Live-Analysedaten](get-xbox-live-analytics.md)</li><li>[Abrufen von Xbox Live-Erfolgsdaten](get-xbox-live-achievements-data.md)</li><li>[Abrufen von Xbox Live-Daten zur gleichzeitigen Nutzung](get-xbox-live-concurrent-usage-data.md)</li></ul> |
| Integritätsanalyse |  <ul><li>[Abrufen von Xbox Live-Integritätsdaten](get-xbox-live-health-data.md)</li></ul> |
| Community-Analyse |  <ul><li>[Abrufen von Xbox Live-Spielehubdaten](get-xbox-live-game-hub-data.md)</li><li>[Abrufen von Xbox Live-Clubdaten](get-xbox-live-club-data.md)</li><li>[Abrufen von Xbox Live Multiplayerdaten](get-xbox-live-multiplayer-data.md)</li></ul>  |

### <a name="methods-for-xbox-one-games"></a>Methoden für Xbox One-Spiele

Die folgenden zusätzlichen Methoden stehen für Entwicklerkonten mit Xbox One-Spielen zur Verfügung, die über das Xbox-Entwicklerportal (XDP) aufgenommen und im XDP Analytics Dev Center-Dashboard verfügbar sind.

| Szenario       | Methoden      |
|---------------|--------------------|
| Käufe |  <ul><li>[Abrufen von Xbox One-Spielekäufen](get-xbox-one-game-acquisitions.md)</li></ul> |

## <a name="code-example"></a>Codebeispiel

Im folgenden Codebeispiel wird veranschaulicht, wie Sie ein AzureAD-Zugriffstoken abrufen und die Microsoft Store-Analyse-API aus einer C#-Konsolen-App aufrufen. Wenn Sie dieses Codebeispiel verwenden möchten, weisen Sie den Variablen *tenantId*, *clientId*, *clientSecret* und *appID* die entsprechenden Werte für Ihr Szenario zu. In diesem Beispiel wird das [Json.NET-Paket](http://www.newtonsoft.com/json) von Newtonsoft benötigt, um die von der Microsoft Store-Analyse-API zurückgegebenen JSON-Daten zu deserialisieren.

> [!div class="tabbedCodeSnippets"]
[!code-cs[AnalyticsApi](./code/StoreServicesExamples_Analytics/cs/Program.cs#AnalyticsApiExample)]

## <a name="error-responses"></a>Fehlerantworten

Die Microsoft Store-Analyse-API gibt Fehlerantworten in einem JSON-Objekt zurück, das Fehlercodes und -meldungen enthält. Im folgenden Beispiel wird eine Fehlerantwort veranschaulicht, die durch einen ungültigen Parameter verursacht wurde.

```json
{
    "code":"BadRequest",
    "data":[],
    "details":[],
    "innererror":{
        "code":"InvalidQueryParameters",
        "data":[
            "top parameter cannot be more than 10000"
        ],
        "details":[],
        "message":"One or More Query Parameters has invalid values.",
        "source":"AnalyticsAPI"
    },
    "message":"The calling client sent a bad request to the service.",
    "source":"AnalyticsAPI"
}
```
