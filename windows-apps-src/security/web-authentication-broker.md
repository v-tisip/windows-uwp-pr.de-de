---
title: Webauthentifizierungsbroker
description: In diesem Artikel wird erläutert, wie Ihre App für die universelle Windows-Plattform (UWP) eine Verbindung mit einem Onlineidentitätsanbieter herstellen kann, der Authentifizierungsprotokolle wie OpenID oder OAuth verwendet, z. B. Twitter, Facebook, Flickr, Instagram usw.
ms.assetid: 05F06961-1768-44A7-B185-BCDB74488F85
author: PatrickFarley
ms.author: pafarley
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Sicherheit
ms.localizationpriority: medium
ms.openlocfilehash: d354f0babec3ec2346c6e76fcae8666f40f3f6be
ms.sourcegitcommit: 9354909f9351b9635bee9bb2dc62db60d2d70107
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/17/2018
ms.locfileid: "4694107"
---
# <a name="web-authentication-broker"></a><span data-ttu-id="65d2d-104">Webauthentifizierungsbroker</span><span class="sxs-lookup"><span data-stu-id="65d2d-104">Web authentication broker</span></span>




<span data-ttu-id="65d2d-105">In diesem Artikel wird erläutert, wie Ihre App für die universelle Windows-Plattform (UWP) eine Verbindung mit einem Onlineidentitätsanbieter herstellen kann, der Authentifizierungsprotokolle wie OpenID oder OAuth verwendet, z. B. Twitter, Facebook, Flickr, Instagram usw.</span><span class="sxs-lookup"><span data-stu-id="65d2d-105">This article explains how to connect your Universal Windows Platform (UWP) app to an online identity provider that uses authentication protocols like OpenID or OAuth, such as Facebook, Twitter, Flickr, Instagram, and so on.</span></span> <span data-ttu-id="65d2d-106">Die [**AuthenticateAsync**](https://msdn.microsoft.com/library/windows/apps/br212066)-Methode sendet eine Anforderung an den Onlineidentitätsanbieter und erhält als Antwort ein Zugriffstoken, das die für die App zugänglichen Anbieterressourcen beschreibt.</span><span class="sxs-lookup"><span data-stu-id="65d2d-106">The [**AuthenticateAsync**](https://msdn.microsoft.com/library/windows/apps/br212066) method sends a request to the online identity provider and gets back an access token that describes the provider resources to which the app has access.</span></span>

>[!NOTE]
><span data-ttu-id="65d2d-107">Um ein vollständiges, funktionsfähiges Codebeispiel zu erhalten, klonen Sie [WebAuthenticationBroker-Repository auf GitHub](http://go.microsoft.com/fwlink/p/?LinkId=620622).</span><span class="sxs-lookup"><span data-stu-id="65d2d-107">For a complete, working code sample, clone the [WebAuthenticationBroker repo on GitHub](http://go.microsoft.com/fwlink/p/?LinkId=620622).</span></span>

 

## <a name="register-your-app-with-your-online-provider"></a><span data-ttu-id="65d2d-108">Registrieren der App beim Onlineanbieter</span><span class="sxs-lookup"><span data-stu-id="65d2d-108">Register your app with your online provider</span></span>


<span data-ttu-id="65d2d-109">Sie müssen Ihre App bei dem Onlineidentitätsanbieter registrieren, mit dem Sie eine Verbindung herstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="65d2d-109">You must register your app with the online identity provider to which you want to connect.</span></span> <span data-ttu-id="65d2d-110">Informationen zur Registrierung erhalten Sie vom Identitätsanbieter.</span><span class="sxs-lookup"><span data-stu-id="65d2d-110">You can find out how to register your app from the identity provider.</span></span> <span data-ttu-id="65d2d-111">Nach der Registrierung weist der Onlineanbieter Ihnen normalerweise eine ID oder einen geheimen Schlüssel für Ihre App zu.</span><span class="sxs-lookup"><span data-stu-id="65d2d-111">After registering, the online provider typically gives you an Id or secret key for your app.</span></span>

## <a name="build-the-authentication-request-uri"></a><span data-ttu-id="65d2d-112">Erstellen des Authentifizierungsanforderungs-URIs</span><span class="sxs-lookup"><span data-stu-id="65d2d-112">Build the authentication request URI</span></span>


<span data-ttu-id="65d2d-113">Der Anforderungs-URI besteht aus der Adresse, unter der Sie die Authentifizierungsanforderung an den Onlineanbieter senden, und angefügten anderen benötigten Informationen, z.B. eine App-ID oder ein Schlüssel, ein Umleitungs-URI, zu dem der Benutzer nach Abschluss der Authentifizierung umgeleitet wird, und der erwartete Antworttyp.</span><span class="sxs-lookup"><span data-stu-id="65d2d-113">The request URI consists of the address where you send the authentication request to your online provider appended with other required information, such as an app ID or secret, a redirect URI where the user is sent after completing authentication, and the expected response type.</span></span> <span data-ttu-id="65d2d-114">Informationen zu den erforderlichen Parametern erhalten Sie von Ihrem Anbieter.</span><span class="sxs-lookup"><span data-stu-id="65d2d-114">You can find out from your provider what parameters are required.</span></span>

<span data-ttu-id="65d2d-115">Der Anforderungs-URI wird als *requestUri*-Parameter der [**AuthenticateAsync**](https://msdn.microsoft.com/library/windows/apps/br212066)-Methode gesendet.</span><span class="sxs-lookup"><span data-stu-id="65d2d-115">The request URI is sent as the *requestUri* parameter of the [**AuthenticateAsync**](https://msdn.microsoft.com/library/windows/apps/br212066) method.</span></span> <span data-ttu-id="65d2d-116">Es muss sich dabei um eine sichere Adresse (beginnend mit `https://`) handeln.</span><span class="sxs-lookup"><span data-stu-id="65d2d-116">It must be a secure address (it must start with `https://`)</span></span>

<span data-ttu-id="65d2d-117">Das folgende Beispiel zeigt, wie der Anforderungs-URI erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="65d2d-117">The following example shows how to build the request URI.</span></span>

```cs
string startURL = "https://<providerendpoint>?client_id=<clientid>&scope=<scopes>&response_type=token";
string endURL = "http://<appendpoint>";

System.Uri startURI = new System.Uri(startURL);
System.Uri endURI = new System.Uri(endURL);
```

## <a name="connect-to-the-online-provider"></a><span data-ttu-id="65d2d-118">Herstellen einer Verbindung mit dem Onlineanbieter</span><span class="sxs-lookup"><span data-stu-id="65d2d-118">Connect to the online provider</span></span>


<span data-ttu-id="65d2d-119">Um eine Verbindung mit dem Onlineidentitätsanbieter herzustellen und ein Zugriffstoken abzurufen, rufen Sie die [**AuthenticateAsync**](https://msdn.microsoft.com/library/windows/apps/br212066)-Methode auf.</span><span class="sxs-lookup"><span data-stu-id="65d2d-119">You call the [**AuthenticateAsync**](https://msdn.microsoft.com/library/windows/apps/br212066) method to connect to the online identity provider and get an access token.</span></span> <span data-ttu-id="65d2d-120">Für die Methode wird der im vorhergehenden Schritt erstellte URI als *requestUri*-Parameter und ein URI, zu dem der Benutzer umgeleitet werden soll, als *callbackUri*-Parameter angegeben.</span><span class="sxs-lookup"><span data-stu-id="65d2d-120">The method takes the URI constructed in the previous step as the *requestUri* parameter, and a URI to which you want the user to be redirected as the *callbackUri* parameter.</span></span>

```cs
string result;

try
{
    var webAuthenticationResult = 
        await Windows.Security.Authentication.Web.WebAuthenticationBroker.AuthenticateAsync( 
        Windows.Security.Authentication.Web.WebAuthenticationOptions.None, 
        startURI, 
        endURI);

    switch (webAuthenticationResult.ResponseStatus)
    {
        case Windows.Security.Authentication.Web.WebAuthenticationStatus.Success:
            // Successful authentication. 
            result = webAuthenticationResult.ResponseData.ToString(); 
            break;
        case Windows.Security.Authentication.Web.WebAuthenticationStatus.ErrorHttp:
            // HTTP error. 
            result = webAuthenticationResult.ResponseErrorDetail.ToString(); 
            break;
        default:
            // Other error.
            result = webAuthenticationResult.ResponseData.ToString(); 
            break;
    } 
}
catch (Exception ex)
{
    // Authentication failed. Handle parameter, SSL/TLS, and Network Unavailable errors here. 
    result = ex.Message;
}
```

>[!WARNING]
><span data-ttu-id="65d2d-121">Zusätzlich zu [**AuthenticateAsync**](https://msdn.microsoft.com/library/windows/apps/br212066) enthält der [**Windows.Security.Authentication.Web**](https://msdn.microsoft.com/library/windows/apps/br227044)-Namespace eine [**AuthenticateAndContinue**](https://msdn.microsoft.com/library/windows/apps/dn632425)-Methode.</span><span class="sxs-lookup"><span data-stu-id="65d2d-121">In addition to [**AuthenticateAsync**](https://msdn.microsoft.com/library/windows/apps/br212066), the [**Windows.Security.Authentication.Web**](https://msdn.microsoft.com/library/windows/apps/br227044) namespace contains an [**AuthenticateAndContinue**](https://msdn.microsoft.com/library/windows/apps/dn632425) method.</span></span> <span data-ttu-id="65d2d-122">Rufen Sie diese Methode nicht auf.</span><span class="sxs-lookup"><span data-stu-id="65d2d-122">Do not call this method.</span></span> <span data-ttu-id="65d2d-123">Sie ist für Apps vorgesehen, die auf Windows Phone 8.1 ausgerichtet sind und ab Windows 10 veraltet.</span><span class="sxs-lookup"><span data-stu-id="65d2d-123">It is designed for apps targeting Windows Phone 8.1 only and is deprecated starting with Windows 10.</span></span>

## <a name="connecting-with-single-sign-on-sso"></a><span data-ttu-id="65d2d-124">Herstellen einer Verbindung mit einmaligen Anmelden (Single Sign-On, SSO).</span><span class="sxs-lookup"><span data-stu-id="65d2d-124">Connecting with single sign-on (SSO).</span></span>


<span data-ttu-id="65d2d-125">Der Webauthentifizierungsbroker lässt das Beibehalten von Cookies standardmäßig nicht zu.</span><span class="sxs-lookup"><span data-stu-id="65d2d-125">By default, Web authentication broker does not allow cookies to persist.</span></span> <span data-ttu-id="65d2d-126">Daher muss sich der App-Benutzer jedes Mal anmelden, wenn er auf Ressourcen für diesen Anbieter zugreifen möchte – auch wenn er angibt, dass er angemeldet bleiben möchte (z.B. durch Aktivieren eines Kontrollkästchens im Anmeldedialogfeld des Anbieters).</span><span class="sxs-lookup"><span data-stu-id="65d2d-126">Because of this, even if the app user indicates that they want to stay logged in (for example, by selecting a check box in the provider's login dialog), they will have to login each time they want to access resources for that provider.</span></span> <span data-ttu-id="65d2d-127">Um die Anmeldung mit Single Sign-On (SSO) durchführen zu können, muss der Onlineidentitätsanbieter SSO für den Webauthentifizierungsbroker aktiviert haben, und Ihre App muss die Überladung von [**AuthenticateAsync**](https://msdn.microsoft.com/library/windows/apps/br212068) aufrufen, für die kein *callbackUri*-Parameter angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="65d2d-127">To login with SSO, your online identity provider must have enabled SSO for Web authentication broker, and your app must call the overload of [**AuthenticateAsync**](https://msdn.microsoft.com/library/windows/apps/br212068) that does not take a *callbackUri* parameter.</span></span> <span data-ttu-id="65d2d-128">Auf diese Weise können persistente Cookies vom Webauthentifizierungsbroker gespeichert werden, so dass durch zukünftige Authentifizierungsaufrufe von derselben App wiederholte Anmeldungen des Benutzers nicht erforderlich sind (der angemeldete Benutzer bleibt solange angemeldet, bis das Zugriffstoken abgelaufen ist).</span><span class="sxs-lookup"><span data-stu-id="65d2d-128">This will allow persisted cookies to be stored by the web authentication broker, so that future authentication calls by the same app will not require repeated sign-in by the user (the user is effectively "logged in" until the access token expires).</span></span>

<span data-ttu-id="65d2d-129">Zur Unterstützung von SSO muss der Onlineanbieter die Registrierung eines Umleitungs-URIs im Format `ms-app://<appSID>` zulassen (`<appSID>` ist die SID für Ihre App).</span><span class="sxs-lookup"><span data-stu-id="65d2d-129">To support SSO, the online provider must allow you to register a redirect URI in the form `ms-app://<appSID>`, where `<appSID>` is the SID for your app.</span></span> <span data-ttu-id="65d2d-130">Die SID Ihrer App finden Sie auf der App-Entwicklerseite Ihrer App. Sie können auch die [**GetCurrentApplicationCallbackUri**](https://msdn.microsoft.com/library/windows/apps/br212069)-Methode aufrufen, um die SID festzustellen.</span><span class="sxs-lookup"><span data-stu-id="65d2d-130">You can find your app's SID from the app developer page for your app, or by calling the [**GetCurrentApplicationCallbackUri**](https://msdn.microsoft.com/library/windows/apps/br212069) method.</span></span>

```cs
string result;

try
{
    var webAuthenticationResult = 
        await Windows.Security.Authentication.Web.WebAuthenticationBroker.AuthenticateAsync( 
        Windows.Security.Authentication.Web.WebAuthenticationOptions.None, 
        startURI);

    switch (webAuthenticationResult.ResponseStatus)
    {
        case Windows.Security.Authentication.Web.WebAuthenticationStatus.Success:
            // Successful authentication. 
            result = webAuthenticationResult.ResponseData.ToString(); 
            break;
        case Windows.Security.Authentication.Web.WebAuthenticationStatus.ErrorHttp:
            // HTTP error. 
            result = webAuthenticationResult.ResponseErrorDetail.ToString(); 
            break;
        default:
            // Other error.
            result = webAuthenticationResult.ResponseData.ToString(); 
            break;
    } 
}
catch (Exception ex)
{
    // Authentication failed. Handle parameter, SSL/TLS, and Network Unavailable errors here. 
    result = ex.Message;
}
```

## <a name="debugging"></a><span data-ttu-id="65d2d-131">Debuggen</span><span class="sxs-lookup"><span data-stu-id="65d2d-131">Debugging</span></span>


<span data-ttu-id="65d2d-132">Es gibt verschiedene Möglichkeiten, die Problembehandlung für die Webauthentifizierungsbroker-APIs durchzuführen. Beispiele hierfür sind die Untersuchung von Betriebsprotokollen und die Untersuchung von Webanforderungen und -antworten mit Fiddler.</span><span class="sxs-lookup"><span data-stu-id="65d2d-132">There are several ways to troubleshoot the web authentication broker APIs, including reviewing operational logs and reviewing web requests and responses using Fiddler.</span></span>

### <a name="operational-logs"></a><span data-ttu-id="65d2d-133">Betriebsprotokolle</span><span class="sxs-lookup"><span data-stu-id="65d2d-133">Operational logs</span></span>

<span data-ttu-id="65d2d-134">Häufig können Sie anhand der Betriebsprotokolle ermitteln, was nicht funktioniert.</span><span class="sxs-lookup"><span data-stu-id="65d2d-134">Often you can determine what is not working by using the operational logs.</span></span> <span data-ttu-id="65d2d-135">Dank des dedizierten Ereignisprotokollkanals „Microsoft-Windows-WebAuth\\Operational“ können Websiteentwickler nachvollziehen, wie ihre Webseiten vom Webauthentifizierungsbroker verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="65d2d-135">There is a dedicated event log channel Microsoft-Windows-WebAuth\\Operational that allows website developers to understand how their web pages are being processed by the Web authentication broker.</span></span> <span data-ttu-id="65d2d-136">Starten Sie zur Aktivierung des Brokers „eventvwr.exe“, und aktivieren Sie das Betriebsprotokoll unter „Anwendungen und Dienste\\Microsoft\\Windows\\WebAuth“.</span><span class="sxs-lookup"><span data-stu-id="65d2d-136">To enable it, launch eventvwr.exe and enable Operational log under the Application and Services\\Microsoft\\Windows\\WebAuth.</span></span> <span data-ttu-id="65d2d-137">Darüber hinaus hängt der Webauthentifizierungsbroker eine eindeutige Zeichenfolge an die Zeichenfolge des Benutzer-Agents an, um sich selbst auf dem Webserver zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="65d2d-137">Also, the Web authentication broker appends a unique string to the user agent string to identify itself on the web server.</span></span> <span data-ttu-id="65d2d-138">Die Zeichenfolge lautet „MSAuthHost/1.0“.</span><span class="sxs-lookup"><span data-stu-id="65d2d-138">The string is "MSAuthHost/1.0".</span></span> <span data-ttu-id="65d2d-139">Beachten Sie, dass sich die Versionsnummer ändern kann. Verlassen Sie sich also in Ihrem Code nicht auf diese Versionsnummer.</span><span class="sxs-lookup"><span data-stu-id="65d2d-139">Note that the version number may change in the future, so you should not to depend on that version number in your code.</span></span> <span data-ttu-id="65d2d-140">Im Folgenden finden Sie ein Beispiel für die vollständigen Zeichenfolge des Benutzer-Agenten, gefolgt von den vollständigen Anweisungen zum Debuggen.</span><span class="sxs-lookup"><span data-stu-id="65d2d-140">An example of the full user agent string, followed by full debugging steps, is as follows.</span></span>

`User-Agent: Mozilla/5.0 (compatible; MSIE 10.0; Windows NT 6.2; Win64; x64; Trident/6.0; MSAuthHost/1.0)`

1.  <span data-ttu-id="65d2d-141">Aktivieren Sie die Betriebsprotokolle.</span><span class="sxs-lookup"><span data-stu-id="65d2d-141">Enable operational logs.</span></span>
2.  <span data-ttu-id="65d2d-142">Führen Sie die Contoso-App für soziale Netzwerke aus.</span><span class="sxs-lookup"><span data-stu-id="65d2d-142">Run Contoso social application.</span></span> ![Ereignisanzeige mit webauth-Betriebsprotokollen](images/wab-event-viewer-1.png)
3.  <span data-ttu-id="65d2d-144">Anhand der generierten Protokolleinträge kann das Verhalten des Webauthentifizierungsbrokers genauer nachvollzogen werden.</span><span class="sxs-lookup"><span data-stu-id="65d2d-144">The generated logs entries can be used to understand the behavior of Web authentication broker in greater detail.</span></span> <span data-ttu-id="65d2d-145">In diesem Fall können sie Folgendes enthalten:</span><span class="sxs-lookup"><span data-stu-id="65d2d-145">In this case, these can include:</span></span>
    -   <span data-ttu-id="65d2d-146">Navigation – Starten: Protokolliert, wann AuthHost gestartet wird, und enthält Informationen zu den Start- und End-URLs.</span><span class="sxs-lookup"><span data-stu-id="65d2d-146">Navigation Start: Logs when the AuthHost is started and contains information about the start and termination URLs.</span></span>
    -   ![Veranschaulicht die Details von „Navigation – Starten“"](images/wab-event-viewer-2.png)
    -   <span data-ttu-id="65d2d-148">Navigation abgeschlossen: Protokolliert den Abschluss des Ladevorgangs einer Webseite.</span><span class="sxs-lookup"><span data-stu-id="65d2d-148">Navigation Complete: Logs the completion of loading a web page.</span></span>
    -   <span data-ttu-id="65d2d-149">META-Tag: Protokolliert, wann ein META-Tag auftritt (einschließlich Details).</span><span class="sxs-lookup"><span data-stu-id="65d2d-149">Meta Tag: Logs when a meta-tag is encountered including the details.</span></span>
    -   <span data-ttu-id="65d2d-150">Navigation – Beenden: Die Navigation wurde vom Benutzer beendet.</span><span class="sxs-lookup"><span data-stu-id="65d2d-150">Navigation Terminate: Navigation terminated by the user.</span></span>
    -   <span data-ttu-id="65d2d-151">Navigationsfehler: AuthHost ermittelt einen Navigationsfehler bei einer URL, einschließlich HttpStatusCode.</span><span class="sxs-lookup"><span data-stu-id="65d2d-151">Navigation Error: AuthHost encounters a navigation error at a URL including HttpStatusCode.</span></span>
    -   <span data-ttu-id="65d2d-152">Navigationsende: End-URL liegt vor.</span><span class="sxs-lookup"><span data-stu-id="65d2d-152">Navigation End: Terminating URL is encountered.</span></span>

### <a name="fiddler"></a><span data-ttu-id="65d2d-153">Fiddler</span><span class="sxs-lookup"><span data-stu-id="65d2d-153">Fiddler</span></span>

<span data-ttu-id="65d2d-154">Der Fiddler-Webdebugger kann Apps verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="65d2d-154">The Fiddler web debugger can be used with apps.</span></span>

1.  <span data-ttu-id="65d2d-155">Da AuthHost in einem eigenen app-Container ausgeführt wird, um die VPN-Funktion zu ermöglichen Sie müssen einen Registrierungsschlüssel festlegen: Windows Registry Editor Version 5.00</span><span class="sxs-lookup"><span data-stu-id="65d2d-155">Since the AuthHost runs in its own app container, to give it the private network capability you must set a registry key: Windows Registry Editor Version 5.00</span></span>

    <span data-ttu-id="65d2d-156">**HKEY\_LOCAL\_MACHINE**\\**SOFTWARE**\\**Microsoft**\\**Windows NT**\\**CurrentVersion**\\**Image File Execution Options**\\**authhost.exe**\\**EnablePrivateNetwork** = 00000001</span><span class="sxs-lookup"><span data-stu-id="65d2d-156">**HKEY\_LOCAL\_MACHINE**\\**SOFTWARE**\\**Microsoft**\\**Windows NT**\\**CurrentVersion**\\**Image File Execution Options**\\**authhost.exe**\\**EnablePrivateNetwork** = 00000001</span></span>

    <span data-ttu-id="65d2d-157">Wenn Sie diesen Registrierungsschlüssel nicht verfügen, können Sie es in einem Eingabeaufforderungsfenster mit Administratorrechten erstellen.</span><span class="sxs-lookup"><span data-stu-id="65d2d-157">If you do not have this registry key, you can create it in a Command Prompt with administrator privileges.</span></span>

    ```cmd 
    REG ADD "HKLM\Software\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\authhost.exe" /v EnablePrivateNetwork /t REG_DWORD /d 1 /f
    ```

2.  <span data-ttu-id="65d2d-158">Fügen Sie eine Regel für AuthHost hinzu, da darüber ausgehender Datenverkehr generiert wird.</span><span class="sxs-lookup"><span data-stu-id="65d2d-158">Add a rule for the AuthHost as this is what is generating the outbound traffic.</span></span>
    ```syntax
    CheckNetIsolation.exe LoopbackExempt -a -n=microsoft.windows.authhost.a.p_8wekyb3d8bbwe
    CheckNetIsolation.exe LoopbackExempt -a -n=microsoft.windows.authhost.sso.p_8wekyb3d8bbwe
    CheckNetIsolation.exe LoopbackExempt -a -n=microsoft.windows.authhost.sso.c_8wekyb3d8bbwe
    D:\Windows\System32>CheckNetIsolation.exe LoopbackExempt -s
    List Loopback Exempted AppContainers
    [1] -----------------------------------------------------------------
        Name: microsoft.windows.authhost.sso.c_8wekyb3d8bbwe
        SID:  S-1-15-2-1973105767-3975693666-32999980-3747492175-1074076486-3102532000-500629349
    [2] -----------------------------------------------------------------
        Name: microsoft.windows.authhost.sso.p_8wekyb3d8bbwe
        SID:  S-1-15-2-166260-4150837609-3669066492-3071230600-3743290616-3683681078-2492089544
    [3] -----------------------------------------------------------------
        Name: microsoft.windows.authhost.a.p_8wekyb3d8bbwe
        SID:  S-1-15-2-3506084497-1208594716-3384433646-2514033508-1838198150-1980605558-3480344935
    ```

3.  <span data-ttu-id="65d2d-159">Fügen Sie Fiddler eine Firewallregel für eingehenden Datenverkehr hinzu.</span><span class="sxs-lookup"><span data-stu-id="65d2d-159">Add a firewall rule for incoming traffic to Fiddler.</span></span>