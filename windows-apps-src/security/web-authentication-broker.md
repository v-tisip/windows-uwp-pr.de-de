---
title: Webauthentifizierungsbroker
description: "In diesem Artikel wird erläutert, wie Ihre App für die universelle Windows-Plattform (UWP) eine Verbindung mit einem Onlineidentitätsanbieter herstellen kann, der Authentifizierungsprotokolle wie OpenID oder OAuth verwendet, z. B. Twitter, Facebook, Flickr, Instagram usw."
ms.assetid: 05F06961-1768-44A7-B185-BCDB74488F85
author: awkoren
ms.author: alkoren
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.openlocfilehash: 2376a21efc0e2167afb64274cee4037f43ed1674
ms.sourcegitcommit: 7540962003b38811e6336451bb03d46538b35671
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/26/2017
---
# <a name="web-authentication-broker"></a><span data-ttu-id="98d27-104">Webauthentifizierungsbroker</span><span class="sxs-lookup"><span data-stu-id="98d27-104">Web authentication broker</span></span>


<span data-ttu-id="98d27-105">\[ Aktualisiert für UWP-Apps unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="98d27-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="98d27-106">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132). \]</span><span class="sxs-lookup"><span data-stu-id="98d27-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>


<span data-ttu-id="98d27-107">In diesem Artikel wird erläutert, wie Ihre App für die universelle Windows-Plattform (UWP) eine Verbindung mit einem Onlineidentitätsanbieter herstellen kann, der Authentifizierungsprotokolle wie OpenID oder OAuth verwendet, z. B. Twitter, Facebook, Flickr, Instagram usw.</span><span class="sxs-lookup"><span data-stu-id="98d27-107">This article explains how to connect your Universal Windows Platform (UWP) app to an online identity provider that uses authentication protocols like OpenID or OAuth, such as Facebook, Twitter, Flickr, Instagram, and so on.</span></span> <span data-ttu-id="98d27-108">Die [**AuthenticateAsync**](https://msdn.microsoft.com/library/windows/apps/br212066)-Methode sendet eine Anforderung an den Onlineidentitätsanbieter und erhält als Antwort ein Zugriffstoken, das die für die App zugänglichen Anbieterressourcen beschreibt.</span><span class="sxs-lookup"><span data-stu-id="98d27-108">The [**AuthenticateAsync**](https://msdn.microsoft.com/library/windows/apps/br212066) method sends a request to the online identity provider and gets back an access token that describes the provider resources to which the app has access.</span></span>

>[!NOTE]
><span data-ttu-id="98d27-109">Um ein vollständiges, funktionsfähiges Codebeispiel zu erhalten, klonen Sie [WebAuthenticationBroker-Repository auf GitHub](http://go.microsoft.com/fwlink/p/?LinkId=620622).</span><span class="sxs-lookup"><span data-stu-id="98d27-109">For a complete, working code sample, clone the [WebAuthenticationBroker repo on GitHub](http://go.microsoft.com/fwlink/p/?LinkId=620622).</span></span>

 

## <a name="register-your-app-with-your-online-provider"></a><span data-ttu-id="98d27-110">Registrieren der App beim Onlineanbieter</span><span class="sxs-lookup"><span data-stu-id="98d27-110">Register your app with your online provider</span></span>


<span data-ttu-id="98d27-111">Sie müssen Ihre App bei dem Onlineidentitätsanbieter registrieren, mit dem Sie eine Verbindung herstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="98d27-111">You must register your app with the online identity provider to which you want to connect.</span></span> <span data-ttu-id="98d27-112">Informationen zur Registrierung erhalten Sie vom Identitätsanbieter.</span><span class="sxs-lookup"><span data-stu-id="98d27-112">You can find out how to register your app from the identity provider.</span></span> <span data-ttu-id="98d27-113">Nach der Registrierung weist der Onlineanbieter Ihnen normalerweise eine ID oder einen geheimen Schlüssel für Ihre App zu.</span><span class="sxs-lookup"><span data-stu-id="98d27-113">After registering, the online provider typically gives you an Id or secret key for your app.</span></span>

## <a name="build-the-authentication-request-uri"></a><span data-ttu-id="98d27-114">Erstellen des Authentifizierungsanforderungs-URIs</span><span class="sxs-lookup"><span data-stu-id="98d27-114">Build the authentication request URI</span></span>


<span data-ttu-id="98d27-115">Der Anforderungs-URI besteht aus der Adresse, unter der Sie die Authentifizierungsanforderung an den Onlineanbieter senden, und angefügten anderen benötigten Informationen, z.B. eine App-ID oder ein Schlüssel, ein Umleitungs-URI, zu dem der Benutzer nach Abschluss der Authentifizierung umgeleitet wird, und der erwartete Antworttyp.</span><span class="sxs-lookup"><span data-stu-id="98d27-115">The request URI consists of the address where you send the authentication request to your online provider appended with other required information, such as an app ID or secret, a redirect URI where the user is sent after completing authentication, and the expected response type.</span></span> <span data-ttu-id="98d27-116">Informationen zu den erforderlichen Parametern erhalten Sie von Ihrem Anbieter.</span><span class="sxs-lookup"><span data-stu-id="98d27-116">You can find out from your provider what parameters are required.</span></span>

<span data-ttu-id="98d27-117">Der Anforderungs-URI wird als *requestUri*-Parameter der [**AuthenticateAsync**](https://msdn.microsoft.com/library/windows/apps/br212066)-Methode gesendet.</span><span class="sxs-lookup"><span data-stu-id="98d27-117">The request URI is sent as the *requestUri* parameter of the [**AuthenticateAsync**](https://msdn.microsoft.com/library/windows/apps/br212066) method.</span></span> <span data-ttu-id="98d27-118">Es muss sich dabei um eine sichere Adresse (beginnend mit `https://`) handeln.</span><span class="sxs-lookup"><span data-stu-id="98d27-118">It must be a secure address (it must start with `https://`)</span></span>

<span data-ttu-id="98d27-119">Das folgende Beispiel zeigt, wie der Anforderungs-URI erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="98d27-119">The following example shows how to build the request URI.</span></span>

```cs
string startURL = "https://<providerendpoint>?client_id=<clientid>&scope=<scopes>&response_type=token";
string endURL = "http://<appendpoint>";

System.Uri startURI = new System.Uri(startURL);
System.Uri endURI = new System.Uri(endURL);
```

## <a name="connect-to-the-online-provider"></a><span data-ttu-id="98d27-120">Herstellen einer Verbindung mit dem Onlineanbieter</span><span class="sxs-lookup"><span data-stu-id="98d27-120">Connect to the online provider</span></span>


<span data-ttu-id="98d27-121">Um eine Verbindung mit dem Onlineidentitätsanbieter herzustellen und ein Zugriffstoken abzurufen, rufen Sie die [**AuthenticateAsync**](https://msdn.microsoft.com/library/windows/apps/br212066)-Methode auf.</span><span class="sxs-lookup"><span data-stu-id="98d27-121">You call the [**AuthenticateAsync**](https://msdn.microsoft.com/library/windows/apps/br212066) method to connect to the online identity provider and get an access token.</span></span> <span data-ttu-id="98d27-122">Für die Methode wird der im vorhergehenden Schritt erstellte URI als *requestUri*-Parameter und ein URI, zu dem der Benutzer umgeleitet werden soll, als *callbackUri*-Parameter angegeben.</span><span class="sxs-lookup"><span data-stu-id="98d27-122">The method takes the URI constructed in the previous step as the *requestUri* parameter, and a URI to which you want the user to be redirected as the *callbackUri* parameter.</span></span>

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
><span data-ttu-id="98d27-123">Zusätzlich zu [**AuthenticateAsync**](https://msdn.microsoft.com/library/windows/apps/br212066) enthält der [**Windows.Security.Authentication.Web**](https://msdn.microsoft.com/library/windows/apps/br227044)-Namespace eine [**AuthenticateAndContinue**](https://msdn.microsoft.com/library/windows/apps/dn632425)-Methode.</span><span class="sxs-lookup"><span data-stu-id="98d27-123">In addition to [**AuthenticateAsync**](https://msdn.microsoft.com/library/windows/apps/br212066), the [**Windows.Security.Authentication.Web**](https://msdn.microsoft.com/library/windows/apps/br227044) namespace contains an [**AuthenticateAndContinue**](https://msdn.microsoft.com/library/windows/apps/dn632425) method.</span></span> <span data-ttu-id="98d27-124">Rufen Sie diese Methode nicht auf.</span><span class="sxs-lookup"><span data-stu-id="98d27-124">Do not call this method.</span></span> <span data-ttu-id="98d27-125">Sie ist für Apps vorgesehen, die auf Windows Phone 8.1 ausgerichtet sind und ab Windows 10 veraltet.</span><span class="sxs-lookup"><span data-stu-id="98d27-125">It is designed for apps targeting Windows Phone 8.1 only and is deprecated starting with Windows 10.</span></span>

## <a name="connecting-with-single-sign-on-sso"></a><span data-ttu-id="98d27-126">Herstellen einer Verbindung mit einmaligen Anmelden (Single Sign-On, SSO).</span><span class="sxs-lookup"><span data-stu-id="98d27-126">Connecting with single sign-on (SSO).</span></span>


<span data-ttu-id="98d27-127">Der Webauthentifizierungsbroker lässt das Beibehalten von Cookies standardmäßig nicht zu.</span><span class="sxs-lookup"><span data-stu-id="98d27-127">By default, Web authentication broker does not allow cookies to persist.</span></span> <span data-ttu-id="98d27-128">Daher muss sich der App-Benutzer jedes Mal anmelden, wenn er auf Ressourcen für diesen Anbieter zugreifen möchte – auch wenn er angibt, dass er angemeldet bleiben möchte (z.B. durch Aktivieren eines Kontrollkästchens im Anmeldedialogfeld des Anbieters).</span><span class="sxs-lookup"><span data-stu-id="98d27-128">Because of this, even if the app user indicates that they want to stay logged in (for example, by selecting a check box in the provider's login dialog), they will have to login each time they want to access resources for that provider.</span></span> <span data-ttu-id="98d27-129">Um die Anmeldung mit Single Sign-On (SSO) durchführen zu können, muss der Onlineidentitätsanbieter SSO für den Webauthentifizierungsbroker aktiviert haben, und Ihre App muss die Überladung von [**AuthenticateAsync**](https://msdn.microsoft.com/library/windows/apps/br212068) aufrufen, für die kein *callbackUri*-Parameter angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="98d27-129">To login with SSO, your online identity provider must have enabled SSO for Web authentication broker, and your app must call the overload of [**AuthenticateAsync**](https://msdn.microsoft.com/library/windows/apps/br212068) that does not take a *callbackUri* parameter.</span></span> <span data-ttu-id="98d27-130">Auf diese Weise können persistente Cookies vom Webauthentifizierungsbroker gespeichert werden, so dass durch zukünftige Authentifizierungsaufrufe von derselben App wiederholte Anmeldungen des Benutzers nicht erforderlich sind (der angemeldete Benutzer bleibt solange angemeldet, bis das Zugriffstoken abgelaufen ist).</span><span class="sxs-lookup"><span data-stu-id="98d27-130">This will allow persisted cookies to be stored by the web authentication broker, so that future authentication calls by the same app will not require repeated sign-in by the user (the user is effectively "logged in" until the access token expires).</span></span>

<span data-ttu-id="98d27-131">Zur Unterstützung von SSO muss der Onlineanbieter die Registrierung eines Umleitungs-URIs im Format `ms-app://<appSID>` zulassen (`<appSID>` ist die SID für Ihre App).</span><span class="sxs-lookup"><span data-stu-id="98d27-131">To support SSO, the online provider must allow you to register a redirect URI in the form `ms-app://<appSID>`, where `<appSID>` is the SID for your app.</span></span> <span data-ttu-id="98d27-132">Die SID Ihrer App finden Sie auf der App-Entwicklerseite Ihrer App. Sie können auch die [**GetCurrentApplicationCallbackUri**](https://msdn.microsoft.com/library/windows/apps/br212069)-Methode aufrufen, um die SID festzustellen.</span><span class="sxs-lookup"><span data-stu-id="98d27-132">You can find your app's SID from the app developer page for your app, or by calling the [**GetCurrentApplicationCallbackUri**](https://msdn.microsoft.com/library/windows/apps/br212069) method.</span></span>

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

## <a name="debugging"></a><span data-ttu-id="98d27-133">Debuggen</span><span class="sxs-lookup"><span data-stu-id="98d27-133">Debugging</span></span>


<span data-ttu-id="98d27-134">Es gibt verschiedene Möglichkeiten, die Problembehandlung für die Webauthentifizierungsbroker-APIs durchzuführen. Beispiele hierfür sind die Untersuchung von Betriebsprotokollen und die Untersuchung von Webanforderungen und -antworten mit Fiddler.</span><span class="sxs-lookup"><span data-stu-id="98d27-134">There are several ways to troubleshoot the web authentication broker APIs, including reviewing operational logs and reviewing web requests and responses using Fiddler.</span></span>

### <a name="operational-logs"></a><span data-ttu-id="98d27-135">Betriebsprotokolle</span><span class="sxs-lookup"><span data-stu-id="98d27-135">Operational logs</span></span>

<span data-ttu-id="98d27-136">Häufig können Sie anhand der Betriebsprotokolle ermitteln, was nicht funktioniert.</span><span class="sxs-lookup"><span data-stu-id="98d27-136">Often you can determine what is not working by using the operational logs.</span></span> <span data-ttu-id="98d27-137">Dank des dedizierten Ereignisprotokollkanals „Microsoft-Windows-WebAuth\\Operational“ können Websiteentwickler nachvollziehen, wie ihre Webseiten vom Webauthentifizierungsbroker verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="98d27-137">There is a dedicated event log channel Microsoft-Windows-WebAuth\\Operational that allows website developers to understand how their web pages are being processed by the Web authentication broker.</span></span> <span data-ttu-id="98d27-138">Starten Sie zur Aktivierung des Brokers „eventvwr.exe“, und aktivieren Sie das Betriebsprotokoll unter „Anwendungen und Dienste\\Microsoft\\Windows\\WebAuth“.</span><span class="sxs-lookup"><span data-stu-id="98d27-138">To enable it, launch eventvwr.exe and enable Operational log under the Application and Services\\Microsoft\\Windows\\WebAuth.</span></span> <span data-ttu-id="98d27-139">Darüber hinaus hängt der Webauthentifizierungsbroker eine eindeutige Zeichenfolge an die Zeichenfolge des Benutzer-Agents an, um sich selbst auf dem Webserver zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="98d27-139">Also, the Web authentication broker appends a unique string to the user agent string to identify itself on the web server.</span></span> <span data-ttu-id="98d27-140">Die Zeichenfolge lautet „MSAuthHost/1.0“.</span><span class="sxs-lookup"><span data-stu-id="98d27-140">The string is "MSAuthHost/1.0".</span></span> <span data-ttu-id="98d27-141">Beachten Sie, dass sich die Versionsnummer ändern kann. Verlassen Sie sich also in Ihrem Code nicht auf diese Versionsnummer.</span><span class="sxs-lookup"><span data-stu-id="98d27-141">Note that the version number may change in the future, so you should not to depend on that version number in your code.</span></span> <span data-ttu-id="98d27-142">Im Folgenden finden Sie ein Beispiel für die vollständigen Zeichenfolge des Benutzer-Agenten, gefolgt von den vollständigen Anweisungen zum Debuggen.</span><span class="sxs-lookup"><span data-stu-id="98d27-142">An example of the full user agent string, followed by full debugging steps, is as follows.</span></span>

`User-Agent: Mozilla/5.0 (compatible; MSIE 10.0; Windows NT 6.2; Win64; x64; Trident/6.0; MSAuthHost/1.0)`

1.  <span data-ttu-id="98d27-143">Aktivieren Sie die Betriebsprotokolle.</span><span class="sxs-lookup"><span data-stu-id="98d27-143">Enable operational logs.</span></span>
2.  <span data-ttu-id="98d27-144">Führen Sie die Contoso-App für soziale Netzwerke aus.</span><span class="sxs-lookup"><span data-stu-id="98d27-144">Run Contoso social application.</span></span> ![Ereignisanzeige mit webauth-Betriebsprotokollen](images/wab-event-viewer-1.png)
3.  <span data-ttu-id="98d27-146">Anhand der generierten Protokolleinträge kann das Verhalten des Webauthentifizierungsbrokers genauer nachvollzogen werden.</span><span class="sxs-lookup"><span data-stu-id="98d27-146">The generated logs entries can be used to understand the behavior of Web authentication broker in greater detail.</span></span> <span data-ttu-id="98d27-147">In diesem Fall können sie Folgendes enthalten:</span><span class="sxs-lookup"><span data-stu-id="98d27-147">In this case, these can include:</span></span>
    -   <span data-ttu-id="98d27-148">Navigation – Starten: Protokolliert, wann AuthHost gestartet wird, und enthält Informationen zu den Start- und End-URLs.</span><span class="sxs-lookup"><span data-stu-id="98d27-148">Navigation Start: Logs when the AuthHost is started and contains information about the start and termination URLs.</span></span>
    -   ![Veranschaulicht die Details von „Navigation – Starten“"](images/wab-event-viewer-2.png)
    -   <span data-ttu-id="98d27-150">Navigation abgeschlossen: Protokolliert den Abschluss des Ladevorgangs einer Webseite.</span><span class="sxs-lookup"><span data-stu-id="98d27-150">Navigation Complete: Logs the completion of loading a web page.</span></span>
    -   <span data-ttu-id="98d27-151">META-Tag: Protokolliert, wann ein META-Tag auftritt (einschließlich Details).</span><span class="sxs-lookup"><span data-stu-id="98d27-151">Meta Tag: Logs when a meta-tag is encountered including the details.</span></span>
    -   <span data-ttu-id="98d27-152">Navigation – Beenden: Die Navigation wurde vom Benutzer beendet.</span><span class="sxs-lookup"><span data-stu-id="98d27-152">Navigation Terminate: Navigation terminated by the user.</span></span>
    -   <span data-ttu-id="98d27-153">Navigationsfehler: AuthHost ermittelt einen Navigationsfehler bei einer URL, einschließlich HttpStatusCode.</span><span class="sxs-lookup"><span data-stu-id="98d27-153">Navigation Error: AuthHost encounters a navigation error at a URL including HttpStatusCode.</span></span>
    -   <span data-ttu-id="98d27-154">Navigationsende: End-URL liegt vor.</span><span class="sxs-lookup"><span data-stu-id="98d27-154">Navigation End: Terminating URL is encountered.</span></span>

### <a name="fiddler"></a><span data-ttu-id="98d27-155">Fiddler</span><span class="sxs-lookup"><span data-stu-id="98d27-155">Fiddler</span></span>

<span data-ttu-id="98d27-156">Der Fiddler-Webdebugger kann Apps verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="98d27-156">The Fiddler web debugger can be used with apps.</span></span>

1.  <span data-ttu-id="98d27-157">Da AuthHost in einem eigenen App-Container ausgeführt wird, um Funktionen für private Netzwerke zu ermöglichen, müssen Sie einen Registrierungsschlüssel festlegen: Windows Registry Editor Version 5.00</span><span class="sxs-lookup"><span data-stu-id="98d27-157">Since the AuthHost runs in its own app container to give it the private network capability, you must set a registry key: Windows Registry Editor Version 5.00</span></span>

    <span data-ttu-id="98d27-158">**HKEY\_LOCAL\_MACHINE**\\**SOFTWARE**\\**Microsoft**\\**Windows NT**\\**CurrentVersion**\\**Image File Execution Options**\\**authhost.exe**\\**EnablePrivateNetwork** = 00000001</span><span class="sxs-lookup"><span data-stu-id="98d27-158">**HKEY\_LOCAL\_MACHINE**\\**SOFTWARE**\\**Microsoft**\\**Windows NT**\\**CurrentVersion**\\**Image File Execution Options**\\**authhost.exe**\\**EnablePrivateNetwork** = 00000001</span></span>

                         Data type  
                         DWORD

2.  <span data-ttu-id="98d27-159">Fügen Sie eine Regel für AuthHost hinzu, da darüber ausgehender Datenverkehr generiert wird.</span><span class="sxs-lookup"><span data-stu-id="98d27-159">Add a rule for the AuthHost as this is what is generating the outbound traffic.</span></span>
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

3.  <span data-ttu-id="98d27-160">Fügen Sie Fiddler eine Firewallregel für eingehenden Datenverkehr hinzu.</span><span class="sxs-lookup"><span data-stu-id="98d27-160">Add a firewall rule for incoming traffic to Fiddler.</span></span>