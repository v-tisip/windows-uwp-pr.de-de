---
description: Verwenden Sie HttpClient und die übrige Windows.Web.Http-Namespace-API zum Senden und Empfangen von Informationen über die HTTP-Protokolle 1.1 und 2.0.
title: HttpClient
ms.assetid: EC9820D3-3A46-474F-8A01-AE1C27442750
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
dev_langs:
- csharp
- cppwinrt
ms.openlocfilehash: 9cd5d9d275241ab107a3b1b06044ba0109d4bb3d
ms.sourcegitcommit: 1901a43b9e40a05c28c7799e0f9b08ce92f8c8a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2019
ms.locfileid: "9035391"
---
# <a name="httpclient"></a><span data-ttu-id="9bfd2-104">HttpClient</span><span class="sxs-lookup"><span data-stu-id="9bfd2-104">HttpClient</span></span>

**<span data-ttu-id="9bfd2-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="9bfd2-105">Important APIs</span></span>**

-   [**<span data-ttu-id="9bfd2-106">HttpClient</span><span class="sxs-lookup"><span data-stu-id="9bfd2-106">HttpClient</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn298639)
-   [**<span data-ttu-id="9bfd2-107">Windows.Web.Http</span><span class="sxs-lookup"><span data-stu-id="9bfd2-107">Windows.Web.Http</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn279692)
-   [**<span data-ttu-id="9bfd2-108">Windows.Web.Http.HttpResponseMessage</span><span class="sxs-lookup"><span data-stu-id="9bfd2-108">Windows.Web.Http.HttpResponseMessage</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn279631)

<span data-ttu-id="9bfd2-109">Verwenden Sie [**HttpClient**](https://msdn.microsoft.com/library/windows/apps/dn298639) und die übrige [**Windows.Web.Http**](https://msdn.microsoft.com/library/windows/apps/dn279692)-Namespace-API zum Senden und Empfangen von Informationen über die HTTP-Protokolle 1.1 und 2.0.</span><span class="sxs-lookup"><span data-stu-id="9bfd2-109">Use [**HttpClient**](https://msdn.microsoft.com/library/windows/apps/dn298639) and the rest of the [**Windows.Web.Http**](https://msdn.microsoft.com/library/windows/apps/dn279692) namespace API to send and receive information using the HTTP 2.0 and HTTP 1.1 protocols.</span></span>

## <a name="overview-of-httpclient-and-the-windowswebhttp-namespace"></a><span data-ttu-id="9bfd2-110">Übersicht über HttpClient und den Windows.Web.Http-Namespace</span><span class="sxs-lookup"><span data-stu-id="9bfd2-110">Overview of HttpClient and the Windows.Web.Http namespace</span></span>

<span data-ttu-id="9bfd2-111">Die Klassen im [**Windows.Web.Http**](https://msdn.microsoft.com/library/windows/apps/dn279692)-Namespace und die zugehörigen [**Windows.Web.Http.Headers**](https://msdn.microsoft.com/library/windows/apps/dn252713)- und [**Windows.Web.Http.Filters**](https://msdn.microsoft.com/library/windows/apps/dn298623)-Namespaces stellen eine Programmierschnittstelle für UWP-Apps bereit, die als HTTP-Client ausgeführt werden, um grundlegende GET-Anforderungen auszuführen oder die weiter unten aufgeführte erweiterte HTTP-Funktionalität zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="9bfd2-111">The classes in the [**Windows.Web.Http**](https://msdn.microsoft.com/library/windows/apps/dn279692) namespace and the related [**Windows.Web.Http.Headers**](https://msdn.microsoft.com/library/windows/apps/dn252713) and [**Windows.Web.Http.Filters**](https://msdn.microsoft.com/library/windows/apps/dn298623) namespaces provide a programming interface for Universal Windows Platform (UWP) apps that act as an HTTP client to perform basic GET requests or implement more advanced HTTP functionality listed below.</span></span>

-   <span data-ttu-id="9bfd2-112">Methoden für häufige Verben (**DELETE**, **GET**, **PUT** und **POST**).</span><span class="sxs-lookup"><span data-stu-id="9bfd2-112">Methods for common verbs (**DELETE**, **GET**, **PUT**, and **POST**).</span></span> <span data-ttu-id="9bfd2-113">Jede dieser Anforderungen wird als asynchroner Vorgang gesendet.</span><span class="sxs-lookup"><span data-stu-id="9bfd2-113">Each of these requests are sent as an asynchronous operation.</span></span>

-   <span data-ttu-id="9bfd2-114">Unterstützung für häufige Authentifizierungseinstellungen und -muster.</span><span class="sxs-lookup"><span data-stu-id="9bfd2-114">Support for common authentication settings and patterns.</span></span>

-   <span data-ttu-id="9bfd2-115">Zugriff auf SSL-Details (Secure Sockets Layer) zum Transport.</span><span class="sxs-lookup"><span data-stu-id="9bfd2-115">Access to Secure Sockets Layer (SSL) details on the transport.</span></span>

-   <span data-ttu-id="9bfd2-116">Möglichkeit zum Einbinden benutzerdefinierter Filter in erweiterte Apps.</span><span class="sxs-lookup"><span data-stu-id="9bfd2-116">Ability to include customized filters in advanced apps.</span></span>

-   <span data-ttu-id="9bfd2-117">Möglichkeit zum Abrufen, Festlegen und Löschen von Cookies.</span><span class="sxs-lookup"><span data-stu-id="9bfd2-117">Ability to get, set, and delete cookies.</span></span>

-   <span data-ttu-id="9bfd2-118">Verfügbarkeit von Statusinformationen zu HTTP-Anforderungen in asynchronen Methoden.</span><span class="sxs-lookup"><span data-stu-id="9bfd2-118">HTTP Request progress info available on asynchronous methods.</span></span>

<span data-ttu-id="9bfd2-119">Die [**Windows.Web.Http.HttpRequestMessage**](https://msdn.microsoft.com/library/windows/apps/dn279617)-Klasse stellt eine HTTP-Anforderungsnachricht dar, die von [**Windows.Web.Http.HttpClient**](https://msdn.microsoft.com/library/windows/apps/dn298639) gesendet wurde.</span><span class="sxs-lookup"><span data-stu-id="9bfd2-119">The [**Windows.Web.Http.HttpRequestMessage**](https://msdn.microsoft.com/library/windows/apps/dn279617) class represents an HTTP request message sent by [**Windows.Web.Http.HttpClient**](https://msdn.microsoft.com/library/windows/apps/dn298639).</span></span> <span data-ttu-id="9bfd2-120">Die [**Windows.Web.Http.HttpResponseMessage**](https://msdn.microsoft.com/library/windows/apps/dn279631)-Klasse stellt eine HTTP-Antwortnachricht dar, die von einer HTTP-Anforderung empfangen wurde.</span><span class="sxs-lookup"><span data-stu-id="9bfd2-120">The [**Windows.Web.Http.HttpResponseMessage**](https://msdn.microsoft.com/library/windows/apps/dn279631) class represents an HTTP response message received from an HTTP request.</span></span> <span data-ttu-id="9bfd2-121">HTTP-Nachrichten werden von IETF in [RFC 2616](http://go.microsoft.com/fwlink/p/?linkid=241642) definiert.</span><span class="sxs-lookup"><span data-stu-id="9bfd2-121">HTTP messages are defined in [RFC 2616](http://go.microsoft.com/fwlink/p/?linkid=241642) by the IETF.</span></span>

<span data-ttu-id="9bfd2-122">Der [**Windows.Web.Http**](https://msdn.microsoft.com/library/windows/apps/dn279692)-Namespace stellt HTTP-Inhalte als HTTP-Entitätskörper und Header dar, darunter auch Cookies.</span><span class="sxs-lookup"><span data-stu-id="9bfd2-122">The [**Windows.Web.Http**](https://msdn.microsoft.com/library/windows/apps/dn279692) namespace represents HTTP content as the HTTP entity body and headers including cookies.</span></span> <span data-ttu-id="9bfd2-123">HTTP-Inhalte können einer HTTP-Anforderung oder einer HTTP-Antwort zugeordnet sein.</span><span class="sxs-lookup"><span data-stu-id="9bfd2-123">HTTP content can be associated with an HTTP request or an HTTP response.</span></span> <span data-ttu-id="9bfd2-124">Der **Windows.Web.Http**-Namespace stellt eine Reihe unterschiedlicher Klassen zum Darstellen von HTTP-Inhalten bereit.</span><span class="sxs-lookup"><span data-stu-id="9bfd2-124">The **Windows.Web.Http** namespace provides a number of different classes to represent HTTP content.</span></span>

-   <span data-ttu-id="9bfd2-125">[**HttpBufferContent**](https://msdn.microsoft.com/library/windows/apps/dn298625).</span><span class="sxs-lookup"><span data-stu-id="9bfd2-125">[**HttpBufferContent**](https://msdn.microsoft.com/library/windows/apps/dn298625).</span></span> <span data-ttu-id="9bfd2-126">Inhalt als Puffer</span><span class="sxs-lookup"><span data-stu-id="9bfd2-126">Content as a buffer</span></span>
-   <span data-ttu-id="9bfd2-127">[**HttpFormUrlEncodedContent**](https://msdn.microsoft.com/library/windows/apps/dn298685).</span><span class="sxs-lookup"><span data-stu-id="9bfd2-127">[**HttpFormUrlEncodedContent**](https://msdn.microsoft.com/library/windows/apps/dn298685).</span></span> <span data-ttu-id="9bfd2-128">Inhalt als Name und Wert-Tupel, die mit dem MIME-Typ **application/x-www-form-urlencoded** codiert sind</span><span class="sxs-lookup"><span data-stu-id="9bfd2-128">Content as name and value tuples encoded with the **application/x-www-form-urlencoded** MIME type</span></span>
-   <span data-ttu-id="9bfd2-129">[**HttpMultipartContent**](https://msdn.microsoft.com/library/windows/apps/dn298708).</span><span class="sxs-lookup"><span data-stu-id="9bfd2-129">[**HttpMultipartContent**](https://msdn.microsoft.com/library/windows/apps/dn298708).</span></span> <span data-ttu-id="9bfd2-130">Inhalt in Form des MIME-Typs **multipart/\***</span><span class="sxs-lookup"><span data-stu-id="9bfd2-130">Content in the form of the **multipart/\*** MIME type.</span></span>
-   <span data-ttu-id="9bfd2-131">[**HttpMultipartFormDataContent**](https://msdn.microsoft.com/library/windows/apps/dn279596).</span><span class="sxs-lookup"><span data-stu-id="9bfd2-131">[**HttpMultipartFormDataContent**](https://msdn.microsoft.com/library/windows/apps/dn279596).</span></span> <span data-ttu-id="9bfd2-132">Inhalt, der als MIME-Typ **multipart/form-data** codiert ist</span><span class="sxs-lookup"><span data-stu-id="9bfd2-132">Content that is encoded as the **multipart/form-data** MIME type.</span></span>
-   <span data-ttu-id="9bfd2-133">[**HttpStreamContent**](https://msdn.microsoft.com/library/windows/apps/dn279649).</span><span class="sxs-lookup"><span data-stu-id="9bfd2-133">[**HttpStreamContent**](https://msdn.microsoft.com/library/windows/apps/dn279649).</span></span> <span data-ttu-id="9bfd2-134">Inhalt als Stream (Der interne Typ wird von der HTTPGET-Methode zum Empfangen von Daten und von der HTTPPOST-Methode zum Hochladen von Daten verwendet.)</span><span class="sxs-lookup"><span data-stu-id="9bfd2-134">Content as a stream (the internal type is used by the HTTP GET method to receive data and the HTTP POST method to upload data)</span></span>
-   <span data-ttu-id="9bfd2-135">[**HttpStringContent**](https://msdn.microsoft.com/library/windows/apps/dn279661).</span><span class="sxs-lookup"><span data-stu-id="9bfd2-135">[**HttpStringContent**](https://msdn.microsoft.com/library/windows/apps/dn279661).</span></span> <span data-ttu-id="9bfd2-136">Inhalt als Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="9bfd2-136">Content as a string.</span></span>
-   <span data-ttu-id="9bfd2-137">[**IHttpContent**](https://msdn.microsoft.com/library/windows/apps/dn279684) – Basisschnittstelle für Entwickler zum Erstellen eigener Inhaltsobjekte</span><span class="sxs-lookup"><span data-stu-id="9bfd2-137">[**IHttpContent**](https://msdn.microsoft.com/library/windows/apps/dn279684) - A base interface for developers to create their own content objects</span></span>

<span data-ttu-id="9bfd2-138">Der Codeausschnitt im Abschnitt „Senden einer einfachen GET-Anforderung über HTTP“ verwendet die [**HttpStringContent**](https://msdn.microsoft.com/library/windows/apps/dn279661)-Klasse, um die HTTP-Antwort einer HTTP GET-Anforderung als Zeichenfolge darzustellen.</span><span class="sxs-lookup"><span data-stu-id="9bfd2-138">The code snippet in the "Send a simple GET request over HTTP" section uses the [**HttpStringContent**](https://msdn.microsoft.com/library/windows/apps/dn279661) class to represent the HTTP response from an HTTP GET request as a string.</span></span>

<span data-ttu-id="9bfd2-139">Der [**Windows.Web.Http.Headers**](https://msdn.microsoft.com/library/windows/apps/dn252713)-Namespace unterstützt die Erstellung von HTTP-Headern und -Cookies, die dann als Eigenschaften mit [**HttpRequestMessage**](https://msdn.microsoft.com/library/windows/apps/dn279617)- und [**HttpResponseMessage**](https://msdn.microsoft.com/library/windows/apps/dn279631)-Objekten zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="9bfd2-139">The [**Windows.Web.Http.Headers**](https://msdn.microsoft.com/library/windows/apps/dn252713) namespace supports creation of HTTP headers and cookies, which are then associated as properties with [**HttpRequestMessage**](https://msdn.microsoft.com/library/windows/apps/dn279617) and [**HttpResponseMessage**](https://msdn.microsoft.com/library/windows/apps/dn279631) objects.</span></span>

## <a name="send-a-simple-get-request-over-http"></a><span data-ttu-id="9bfd2-140">Senden einer einfachen GET-Anforderung über HTTP</span><span class="sxs-lookup"><span data-stu-id="9bfd2-140">Send a simple GET request over HTTP</span></span>

<span data-ttu-id="9bfd2-141">Wie weiter oben in diesem Artikel beschrieben wurde, können UWP-Apps mit dem [**Windows.Web.Http**](https://msdn.microsoft.com/library/windows/apps/dn279692)-Namespace GET-Anforderungen senden.</span><span class="sxs-lookup"><span data-stu-id="9bfd2-141">As mentioned earlier in this article, the [**Windows.Web.Http**](https://msdn.microsoft.com/library/windows/apps/dn279692) namespace allows UWP apps to send GET requests.</span></span> <span data-ttu-id="9bfd2-142">Der folgende Codeausschnitt veranschaulicht, wie eine GET-Anforderung zu senden http://www.contoso.com mit, dass die [**Windows.Web.Http.HttpClient**](https://msdn.microsoft.com/library/windows/apps/dn298639) -Klasse und die [**Windows.Web.Http.HttpResponseMessage**](https://msdn.microsoft.com/library/windows/apps/dn279631) -Klasse um die Antwort der GET-Anforderung zu lesen.</span><span class="sxs-lookup"><span data-stu-id="9bfd2-142">The following code snippet demonstrates how to send a GET request to http://www.contoso.com using the [**Windows.Web.Http.HttpClient**](https://msdn.microsoft.com/library/windows/apps/dn298639) class and the [**Windows.Web.Http.HttpResponseMessage**](https://msdn.microsoft.com/library/windows/apps/dn279631) class to read the response from the GET request.</span></span>

```csharp
//Create an HTTP client object
Windows.Web.Http.HttpClient httpClient = new Windows.Web.Http.HttpClient();

//Add a user-agent header to the GET request. 
var headers = httpClient.DefaultRequestHeaders;

//The safe way to add a header value is to use the TryParseAdd method and verify the return value is true,
//especially if the header value is coming from user input.
string header = "ie";
if (!headers.UserAgent.TryParseAdd(header))
{
    throw new Exception("Invalid header value: " + header);
}

header = "Mozilla/5.0 (compatible; MSIE 10.0; Windows NT 6.2; WOW64; Trident/6.0)";
if (!headers.UserAgent.TryParseAdd(header))
{
    throw new Exception("Invalid header value: " + header);
}

Uri requestUri = new Uri("http://www.contoso.com");

//Send the GET request asynchronously and retrieve the response as a string.
Windows.Web.Http.HttpResponseMessage httpResponse = new Windows.Web.Http.HttpResponseMessage();
string httpResponseBody = "";

try
{
    //Send the GET request
    httpResponse = await httpClient.GetAsync(requestUri);
    httpResponse.EnsureSuccessStatusCode();
    httpResponseBody = await httpResponse.Content.ReadAsStringAsync();
}
catch (Exception ex)
{
    httpResponseBody = "Error: " + ex.HResult.ToString("X") + " Message: " + ex.Message;
}
```

```cppwinrt
// pch.h
#pragma once

#include "winrt/Windows.Foundation.h"
#include <winrt/Windows.Web.Http.Headers.h>

// main.cpp : Defines the entry point for the console application.
#include "pch.h"
#include <iostream>

using namespace winrt;
using namespace Windows::Foundation;

int main()
{
    init_apartment();

    // Create an HttpClient object.
    Windows::Web::Http::HttpClient httpClient;

    // Add a user-agent header to the GET request.
    auto headers{ httpClient.DefaultRequestHeaders() };

    // The safe way to add a header value is to use the TryParseAdd method, and verify the return value is true.
    // This is especially important if the header value is coming from user input.
    std::wstring header{ L"ie" };
    if (!headers.UserAgent().TryParseAdd(header))
    {
        throw L"Invalid header value: " + header;
    }

    header = L"Mozilla/5.0 (compatible; MSIE 10.0; Windows NT 6.2; WOW64; Trident/6.0)";
    if (!headers.UserAgent().TryParseAdd(header))
    {
        throw L"Invalid header value: " + header;
    }

    Uri requestUri{ L"http://www.contoso.com" };

    // Send the GET request asynchronously, and retrieve the response as a string.
    Windows::Web::Http::HttpResponseMessage httpResponseMessage;
    std::wstring httpResponseBody;

    try
    {
        // Send the GET request.
        httpResponseMessage = httpClient.GetAsync(requestUri).get();
        httpResponseMessage.EnsureSuccessStatusCode();
        httpResponseBody = httpResponseMessage.Content().ReadAsStringAsync().get();
    }
    catch (winrt::hresult_error const& ex)
    {
        httpResponseBody = ex.message();
    }
    std::wcout << httpResponseBody;
}
```

## <a name="exceptions-in-windowswebhttp"></a><span data-ttu-id="9bfd2-143">Ausnahmen in „Windows.Web.Http“</span><span class="sxs-lookup"><span data-stu-id="9bfd2-143">Exceptions in Windows.Web.Http</span></span>

<span data-ttu-id="9bfd2-144">Eine Ausnahme wird ausgelöst, wenn eine ungültige Zeichenfolge für einen Uniform Resource Identifier (URI) an den Konstruktor für das [**Windows.Foundation.Uri**](https://msdn.microsoft.com/library/windows/apps/br225998)-Objekt übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="9bfd2-144">An exception is thrown when an invalid string for a the Uniform Resource Identifier (URI) is passed to the constructor for the [**Windows.Foundation.Uri**](https://msdn.microsoft.com/library/windows/apps/br225998) object.</span></span>

<span data-ttu-id="9bfd2-145">**NET:** der [**Windows.Foundation.Uri**](https://msdn.microsoft.com/library/windows/apps/br225998) -Typ wird als [**System.Uri**](https://msdn.microsoft.com/library/windows/apps/xaml/system.uri.aspx) in c# und VB angezeigt.</span><span class="sxs-lookup"><span data-stu-id="9bfd2-145">**.NET:** The [**Windows.Foundation.Uri**](https://msdn.microsoft.com/library/windows/apps/br225998) type appears as [**System.Uri**](https://msdn.microsoft.com/library/windows/apps/xaml/system.uri.aspx) in C# and VB.</span></span>

<span data-ttu-id="9bfd2-146">In C# und Visual Basic kann dieser Fehler vermieden werden, indem die [**System.Uri**](https://msdn.microsoft.com/library/windows/apps/xaml/system.uri.aspx)-Klasse in .NET4.5 und eine der [**System.Uri.TryCreat**](https://msdn.microsoft.com/library/windows/apps/xaml/system.uri.trycreate.aspx)-Methoden zum Testen der von einem Benutzer erhaltenen Zeichenfolge verwendet wird, bevor der URI erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="9bfd2-146">In C# and Visual Basic, this error can be avoided by using the [**System.Uri**](https://msdn.microsoft.com/library/windows/apps/xaml/system.uri.aspx) class in the .NET 4.5 and one of the [**System.Uri.TryCreate**](https://msdn.microsoft.com/library/windows/apps/xaml/system.uri.trycreate.aspx) methods to test the string received from a user before the URI is constructed.</span></span>

<span data-ttu-id="9bfd2-147">In C++ gibt es keine Methode zum Analysieren einer Zeichenfolge für einen URI.</span><span class="sxs-lookup"><span data-stu-id="9bfd2-147">In C++, there is no method to try and parse a string to a URI.</span></span> <span data-ttu-id="9bfd2-148">Wenn eine App vom Benutzer eine Eingabe für das [**Windows.Foundation.Uri**](https://msdn.microsoft.com/library/windows/apps/br225998)-Element erhält, sollte sich der Konstruktor innerhalb eines try/catch-Blocks befinden.</span><span class="sxs-lookup"><span data-stu-id="9bfd2-148">If an app gets input from the user for the [**Windows.Foundation.Uri**](https://msdn.microsoft.com/library/windows/apps/br225998), the constructor should be in a try/catch block.</span></span> <span data-ttu-id="9bfd2-149">Wenn eine Ausnahme ausgelöst wird, kann die App den Benutzer benachrichtigen und einen neuen Hostnamen anfordern.</span><span class="sxs-lookup"><span data-stu-id="9bfd2-149">If an exception is thrown, the app can notify the user and request a new hostname.</span></span>

<span data-ttu-id="9bfd2-150">[**Windows.Web.Http**](https://msdn.microsoft.com/library/windows/apps/dn279692) bietet keine Funktion, die die Behandlung von Ausnahmen erleichtert.</span><span class="sxs-lookup"><span data-stu-id="9bfd2-150">The [**Windows.Web.Http**](https://msdn.microsoft.com/library/windows/apps/dn279692) lacks a convenience function.</span></span> <span data-ttu-id="9bfd2-151">Eine App, die [**HttpClient**](https://msdn.microsoft.com/library/windows/apps/dn298639) und andere Klassen in diesem Namespace verwendet, muss daher den **HRESULT**-Wert verwenden.</span><span class="sxs-lookup"><span data-stu-id="9bfd2-151">So an app using [**HttpClient**](https://msdn.microsoft.com/library/windows/apps/dn298639) and other classes in this namespace needs to use the **HRESULT** value.</span></span>

<span data-ttu-id="9bfd2-152">In apps unter Verwendung der .NET Framework4.5 in c#, VB.NET, der [System.Exception](http://msdn.microsoft.com/library/system.exception.aspx) einen Fehler darstellt während der Ausführung der app beim Auftreten einer Ausnahme.</span><span class="sxs-lookup"><span data-stu-id="9bfd2-152">In apps using the .NET Framework4.5 in C#, VB.NET, the [System.Exception](http://msdn.microsoft.com/library/system.exception.aspx) represents an error during app execution when an exception occurs.</span></span> <span data-ttu-id="9bfd2-153">Die [System.Exception.HResult](http://msdn.microsoft.com/library/system.exception.hresult.aspx)-Eigenschaft gibt den **HRESULT**-Wert zurück, der der jeweiligen Ausnahme zugewiesen ist.</span><span class="sxs-lookup"><span data-stu-id="9bfd2-153">The [System.Exception.HResult](http://msdn.microsoft.com/library/system.exception.hresult.aspx) property returns the **HRESULT** assigned to the specific exception.</span></span> <span data-ttu-id="9bfd2-154">Die [System.Exception.Message](http://msdn.microsoft.com/library/system.exception.message.aspx)-Eigenschaft gibt die Meldung zurück, die die Ausnahme beschreibt.</span><span class="sxs-lookup"><span data-stu-id="9bfd2-154">The [System.Exception.Message](http://msdn.microsoft.com/library/system.exception.message.aspx) property returns the message that describes the exception.</span></span> <span data-ttu-id="9bfd2-155">Mögliche **HRESULT**-Werte sind in der Headerdatei *Winerror.h* aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="9bfd2-155">Possible **HRESULT** values are listed in the *Winerror.h* header file.</span></span> <span data-ttu-id="9bfd2-156">Eine App kann nach bestimmten **HRESULT**-Werten filtern, um das App-Verhalten je nach Ausnahmeursache zu ändern.</span><span class="sxs-lookup"><span data-stu-id="9bfd2-156">An app can filter on specific **HRESULT** values to modify app behavior depending on the cause of the exception.</span></span>

<span data-ttu-id="9bfd2-157">In Apps mit verwaltetem C++ stellt das [Platform::Exception](http://msdn.microsoft.com/library/windows/apps/hh755825.aspx)-Objekt einen Fehler während der App-Ausführung dar, wenn eine Ausnahme auftritt.</span><span class="sxs-lookup"><span data-stu-id="9bfd2-157">In apps using managed C++, the [Platform::Exception](http://msdn.microsoft.com/library/windows/apps/hh755825.aspx) represents an error during app execution when an exception occurs.</span></span> <span data-ttu-id="9bfd2-158">Die [Platform::Exception::HResult](http://msdn.microsoft.com/library/windows/apps/hh763371.aspx)-Eigenschaft gibt den **HRESULT**-Wert zurück, der der jeweiligen Ausnahme zugewiesen ist.</span><span class="sxs-lookup"><span data-stu-id="9bfd2-158">The [Platform::Exception::HResult](http://msdn.microsoft.com/library/windows/apps/hh763371.aspx) property returns the **HRESULT** assigned to the specific exception.</span></span> <span data-ttu-id="9bfd2-159">Die [Platform::Exception::Message](http://msdn.microsoft.com/library/windows/apps/hh763375.aspx)-Eigenschaft gibt die vom System bereitgestellte Zeichenfolge zurück, die dem **HRESULT**-Wert zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="9bfd2-159">The [Platform::Exception::Message](http://msdn.microsoft.com/library/windows/apps/hh763375.aspx) property returns the system-provided string that is associated with the **HRESULT** value.</span></span> <span data-ttu-id="9bfd2-160">Mögliche **HRESULT**-Werte sind in der Headerdatei *Winerror.h* aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="9bfd2-160">Possible **HRESULT** values are listed in the *Winerror.h* header file.</span></span> <span data-ttu-id="9bfd2-161">Eine App kann nach bestimmten **HRESULT**-Werten filtern, um das App-Verhalten je nach Ausnahmeursache zu ändern.</span><span class="sxs-lookup"><span data-stu-id="9bfd2-161">An app can filter on specific **HRESULT** values to modify app behavior depending on the cause of the exception.</span></span>

<span data-ttu-id="9bfd2-162">Für die meisten Parameterüberprüfungsfehler wird der **HRESULT**-Wert **E\_INVALIDARG** zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="9bfd2-162">For most parameter validation errors, the **HRESULT** returned is **E\_INVALIDARG**.</span></span> <span data-ttu-id="9bfd2-163">Bei manchen unzulässigen Methodenaufrufen wird der **HRESULT**-Wert **E\_ILLEGAL\_METHOD\_CALL** zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="9bfd2-163">For some illegal method calls, the **HRESULT** returned is **E\_ILLEGAL\_METHOD\_CALL**.</span></span>

