---
author: Xansky
description: Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um die Stapelüberwachung für einen Fehler in Ihrer Desktopanwendung abzurufen.
title: Abrufen der Stapelüberwachung für einen Fehler in Ihrer Desktopanwendung
ms.author: mhopkins
ms.date: 06/05/2018
ms.topic: article
keywords: Windows10, UWP, Store-Dienste, Microsoft Store-Analyse-API, Stapelüberwachung, Fehler, Desktopanwendung
ms.localizationpriority: medium
ms.openlocfilehash: b9b26f36d7fe2dc553e211ae48f7bd66651c5827
ms.sourcegitcommit: cd00bb829306871e5103db481cf224ea7fb613f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "5882756"
---
# <a name="get-the-stack-trace-for-an-error-in-your-desktop-application"></a><span data-ttu-id="eccc4-104">Abrufen der Stapelüberwachung für einen Fehler in Ihrer Desktopanwendung</span><span class="sxs-lookup"><span data-stu-id="eccc4-104">Get the stack trace for an error in your desktop application</span></span>

<span data-ttu-id="eccc4-105">Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um die Stapelüberwachung für einen Fehler in einer Desktopanwendung abzurufen, die Sie zum [Windows-Desktopanwendungsprogramm](https://msdn.microsoft.com/library/windows/desktop/mt826504) hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="eccc4-105">Use this method in the Microsoft Store analytics API to get the stack trace for an error in a desktop application that you have added to the [Windows Desktop Application program](https://msdn.microsoft.com/library/windows/desktop/mt826504).</span></span> <span data-ttu-id="eccc4-106">Diese Methode kann nur die Stapelüberwachung für einen Fehler herunterladen, die in den letzten 30Tagen aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="eccc4-106">This method can only download the stack trace for an error that occurred in the last 30 days.</span></span> <span data-ttu-id="eccc4-107">Stapelüberwachungen sind auch im [Integritätsbericht](https://msdn.microsoft.com/library/windows/desktop/mt826504) für Desktopanwendungen im Windows Dev Center-Dashboard verfügbar.</span><span class="sxs-lookup"><span data-stu-id="eccc4-107">Stack traces are also available in the [Health report](https://msdn.microsoft.com/library/windows/desktop/mt826504) for desktop applications in the Windows Dev Center dashboard.</span></span>

<span data-ttu-id="eccc4-108">Bevor Sie diese Methode verwenden können, müssen Sie zuerst die Methode für das [Abrufen von Details zu einem Fehler in Ihrer Desktopanwendung](get-details-for-an-error-in-your-desktop-application.md) aufrufen, um die ID-Hash der CAB-Datei abzurufen, die mit dem Fehler verknüpft ist, für den Sie die Stapelüberwachung abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="eccc4-108">Before you can use this method, you must first use the [get details for an error in your desktop application](get-details-for-an-error-in-your-desktop-application.md) method to retrieve the ID hash of the CAB file that is associated with the error for which you want to retrieve the stack trace.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="eccc4-109">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="eccc4-109">Prerequisites</span></span>


<span data-ttu-id="eccc4-110">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="eccc4-110">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="eccc4-111">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.</span><span class="sxs-lookup"><span data-stu-id="eccc4-111">If you have not done so already, complete all the [prerequisites](access-analytics-data-using-windows-store-services.md#prerequisites) for the Microsoft Store analytics API.</span></span>
* <span data-ttu-id="eccc4-112">[Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="eccc4-112">[Obtain an Azure AD access token](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="eccc4-113">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="eccc4-113">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="eccc4-114">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="eccc4-114">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="eccc4-115">Rufen Sie die ID-Hash der CAB-Datei ab, die mit dem Fehler verknüpft ist, für den Sie die Stapelüberwachung abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="eccc4-115">Get the ID hash of the CAB file that is associated with the error for which you want to retrieve the stack trace.</span></span> <span data-ttu-id="eccc4-116">Verwenden Sie zum Abrufen dieses Wertes die Methode zum [Abrufen von Details zu einem Fehler in Ihrer Desktopanwendung](get-details-for-an-error-in-your-desktop-application.md), um Details zu einem bestimmten Fehler in Ihrer App abzurufen, und verwenden Sie den **cabIdHash**-Wert im Antworttext dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="eccc4-116">To get this value, use the [get details for an error in your desktop application](get-details-for-an-error-in-your-desktop-application.md) method to retrieve details for a specific error in your app, and use the **cabIdHash** value in the response body of that method.</span></span>

## <a name="request"></a><span data-ttu-id="eccc4-117">Anforderung</span><span class="sxs-lookup"><span data-stu-id="eccc4-117">Request</span></span>


### <a name="request-syntax"></a><span data-ttu-id="eccc4-118">Anforderungssyntax</span><span class="sxs-lookup"><span data-stu-id="eccc4-118">Request syntax</span></span>

| <span data-ttu-id="eccc4-119">Methode</span><span class="sxs-lookup"><span data-stu-id="eccc4-119">Method</span></span> | <span data-ttu-id="eccc4-120">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="eccc4-120">Request URI</span></span>                                                          |
|--------|----------------------------------------------------------------------|
| <span data-ttu-id="eccc4-121">GET</span><span class="sxs-lookup"><span data-stu-id="eccc4-121">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/desktop/stacktrace``` |


### <a name="request-header"></a><span data-ttu-id="eccc4-122">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="eccc4-122">Request header</span></span>

| <span data-ttu-id="eccc4-123">Header</span><span class="sxs-lookup"><span data-stu-id="eccc4-123">Header</span></span>        | <span data-ttu-id="eccc4-124">Typ</span><span class="sxs-lookup"><span data-stu-id="eccc4-124">Type</span></span>   | <span data-ttu-id="eccc4-125">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="eccc4-125">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="eccc4-126">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="eccc4-126">Authorization</span></span> | <span data-ttu-id="eccc4-127">String</span><span class="sxs-lookup"><span data-stu-id="eccc4-127">string</span></span> | <span data-ttu-id="eccc4-128">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="eccc4-128">Required.</span></span> <span data-ttu-id="eccc4-129">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="eccc4-129">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |
 

### <a name="request-parameters"></a><span data-ttu-id="eccc4-130">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="eccc4-130">Request parameters</span></span>

| <span data-ttu-id="eccc4-131">Parameter</span><span class="sxs-lookup"><span data-stu-id="eccc4-131">Parameter</span></span>        | <span data-ttu-id="eccc4-132">Typ</span><span class="sxs-lookup"><span data-stu-id="eccc4-132">Type</span></span>   |  <span data-ttu-id="eccc4-133">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="eccc4-133">Description</span></span>      |  <span data-ttu-id="eccc4-134">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="eccc4-134">Required</span></span>  |
|---------------|--------|---------------|------|
| <span data-ttu-id="eccc4-135">applicationId</span><span class="sxs-lookup"><span data-stu-id="eccc4-135">applicationId</span></span> | <span data-ttu-id="eccc4-136">string</span><span class="sxs-lookup"><span data-stu-id="eccc4-136">string</span></span> | <span data-ttu-id="eccc4-137">Die Produkt-ID der Desktopanwendung, für die Sie eine Stapelüberwachung abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="eccc4-137">The product ID of the desktop application for which you want to get a stack trace.</span></span> <span data-ttu-id="eccc4-138">Um die Produkt-ID einer Desktopanwendung zu erhalten, öffnen Sie einen [Dev Center-Analysebericht für Ihre Desktopanwendung](https://msdn.microsoft.com/library/windows/desktop/mt826504) (z.B. den **Integritätsbericht**) und rufen Sie die Produkt-ID aus der URL ab.</span><span class="sxs-lookup"><span data-stu-id="eccc4-138">To get the product ID of a desktop application, open any [Dev Center analytics report for your desktop application](https://msdn.microsoft.com/library/windows/desktop/mt826504) (such as the **Health report**) and retrieve the product ID from the URL.</span></span> |  <span data-ttu-id="eccc4-139">Ja</span><span class="sxs-lookup"><span data-stu-id="eccc4-139">Yes</span></span>  |
| <span data-ttu-id="eccc4-140">cabIdHash</span><span class="sxs-lookup"><span data-stu-id="eccc4-140">cabIdHash</span></span> | <span data-ttu-id="eccc4-141">String</span><span class="sxs-lookup"><span data-stu-id="eccc4-141">string</span></span> | <span data-ttu-id="eccc4-142">Die eindeutige ID-Hash der CAB-Datei, die mit dem Fehler verknüpft ist, für den Sie die Stapelüberwachung abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="eccc4-142">The unique ID hash of the CAB file that is associated with the error for which you want to retrieve the stack trace.</span></span> <span data-ttu-id="eccc4-143">Verwenden Sie zum Abrufen dieses Wertes die Methode zum [Abrufen von Details zu einem Fehler in Ihrer Desktopanwendung](get-details-for-an-error-in-your-desktop-application.md), um Details zu einem bestimmten Fehler in Ihrer Anwendung abzurufen, und verwenden Sie den **cabIdHash**-Wert im Antworttext dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="eccc4-143">To get this value, use the [get details for an error in your desktop application](get-details-for-an-error-in-your-desktop-application.md) method to retrieve details for a specific error in your application, and use the **cabIdHash** value in the response body of that method.</span></span> |  <span data-ttu-id="eccc4-144">Ja</span><span class="sxs-lookup"><span data-stu-id="eccc4-144">Yes</span></span>  |

 
### <a name="request-example"></a><span data-ttu-id="eccc4-145">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="eccc4-145">Request example</span></span>

<span data-ttu-id="eccc4-146">Im folgenden Beispiel wird gezeigt, wie Sie mit dieser Methode eine Stapelüberwachung abrufen.</span><span class="sxs-lookup"><span data-stu-id="eccc4-146">The following example demonstrates how to get a stack trace using this method.</span></span> <span data-ttu-id="eccc4-147">Ersetzen Sie die Parameter *applicationId* und *cabIdHash* durch die entsprechende Werte für Ihre Desktopanwendung.</span><span class="sxs-lookup"><span data-stu-id="eccc4-147">Replace the *applicationId* and *cabIdHash* parameters with the appropriate values for your desktop application.</span></span>

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/desktop/stacktrace?applicationId=10238467886765136388&cabIdHash=54ffb83a-e159-41d2-8158-f36f306cc01e HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="eccc4-148">Antwort</span><span class="sxs-lookup"><span data-stu-id="eccc4-148">Response</span></span>


### <a name="response-body"></a><span data-ttu-id="eccc4-149">Antworttext</span><span class="sxs-lookup"><span data-stu-id="eccc4-149">Response body</span></span>

| <span data-ttu-id="eccc4-150">Wert</span><span class="sxs-lookup"><span data-stu-id="eccc4-150">Value</span></span>      | <span data-ttu-id="eccc4-151">Typ</span><span class="sxs-lookup"><span data-stu-id="eccc4-151">Type</span></span>    | <span data-ttu-id="eccc4-152">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="eccc4-152">Description</span></span>                  |
|------------|---------|--------------------------------|
| <span data-ttu-id="eccc4-153">Wert</span><span class="sxs-lookup"><span data-stu-id="eccc4-153">Value</span></span>      | <span data-ttu-id="eccc4-154">array</span><span class="sxs-lookup"><span data-stu-id="eccc4-154">array</span></span>   | <span data-ttu-id="eccc4-155">Ein Array von Objekten, die jeweils einen einzelnen Frame der Stapelüberwachungsdaten enthalten.</span><span class="sxs-lookup"><span data-stu-id="eccc4-155">An array of objects that each contain one frame of stack trace data.</span></span> <span data-ttu-id="eccc4-156">Weitere Informationen zu den Daten in den einzelnen Objekten finden Sie unten im Abschnitt [Stapelüberwachungswerte](#stack-trace-values).</span><span class="sxs-lookup"><span data-stu-id="eccc4-156">For more information about the data in each object, see the [stack trace values](#stack-trace-values) section below.</span></span> |
| @nextLink  | <span data-ttu-id="eccc4-157">String</span><span class="sxs-lookup"><span data-stu-id="eccc4-157">string</span></span>  | <span data-ttu-id="eccc4-158">Wenn weitere Seiten mit Daten vorhanden sind, enthält diese Zeichenfolge einen URI, mit dem Sie die nächste Seite mit Daten anfordern können.</span><span class="sxs-lookup"><span data-stu-id="eccc4-158">If there are additional pages of data, this string contains a URI that you can use to request the next page of data.</span></span> <span data-ttu-id="eccc4-159">Beispielsweise wird dieser Wert zurückgegeben, wenn der Parameter **top** der Anforderung auf 10 festgelegt ist, es jedoch mehr als 10 Zeilen mit Fehlern für die Abfrage gibt.</span><span class="sxs-lookup"><span data-stu-id="eccc4-159">For example, this value is returned if the **top** parameter of the request is set to 10 but there are more than 10 rows of errors for the query.</span></span> |
| <span data-ttu-id="eccc4-160">TotalCount</span><span class="sxs-lookup"><span data-stu-id="eccc4-160">TotalCount</span></span> | <span data-ttu-id="eccc4-161">Ganzzahl</span><span class="sxs-lookup"><span data-stu-id="eccc4-161">integer</span></span> | <span data-ttu-id="eccc4-162">Die Gesamtzahl der Zeilen im Datenergebnis für die Abfrage.</span><span class="sxs-lookup"><span data-stu-id="eccc4-162">The total number of rows in the data result for the query.</span></span>          |


### <a name="stack-trace-values"></a><span data-ttu-id="eccc4-163">Stapelüberwachungswerte</span><span class="sxs-lookup"><span data-stu-id="eccc4-163">Stack trace values</span></span>

<span data-ttu-id="eccc4-164">Elemente im Array *Value* enthalten die folgenden Werte.</span><span class="sxs-lookup"><span data-stu-id="eccc4-164">Elements in the *Value* array contain the following values.</span></span>

| <span data-ttu-id="eccc4-165">Wert</span><span class="sxs-lookup"><span data-stu-id="eccc4-165">Value</span></span>           | <span data-ttu-id="eccc4-166">Typ</span><span class="sxs-lookup"><span data-stu-id="eccc4-166">Type</span></span>    | <span data-ttu-id="eccc4-167">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="eccc4-167">Description</span></span>      |
|-----------------|---------|----------------|
| <span data-ttu-id="eccc4-168">level</span><span class="sxs-lookup"><span data-stu-id="eccc4-168">level</span></span>            | <span data-ttu-id="eccc4-169">string</span><span class="sxs-lookup"><span data-stu-id="eccc4-169">string</span></span>  |  <span data-ttu-id="eccc4-170">Die Framenummer, die dieses Element im Aufrufstapel darstellt.</span><span class="sxs-lookup"><span data-stu-id="eccc4-170">The frame number that this element represents in the call stack.</span></span>  |
| <span data-ttu-id="eccc4-171">image</span><span class="sxs-lookup"><span data-stu-id="eccc4-171">image</span></span>   | <span data-ttu-id="eccc4-172">string</span><span class="sxs-lookup"><span data-stu-id="eccc4-172">string</span></span>  |   <span data-ttu-id="eccc4-173">Den Namen der ausführbaren Datei oder des Bibliothekbilds, die/das die Funktion enthält, die in diesem Stapelframe aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="eccc4-173">The name of the executable or library image that contains the function that is called in this stack frame.</span></span>           |
| <span data-ttu-id="eccc4-174">function</span><span class="sxs-lookup"><span data-stu-id="eccc4-174">function</span></span> | <span data-ttu-id="eccc4-175">string</span><span class="sxs-lookup"><span data-stu-id="eccc4-175">string</span></span>  |  <span data-ttu-id="eccc4-176">Der Name der Funktion, die in diesem Stapelframe aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="eccc4-176">The name of the function that is called in this stack frame.</span></span> <span data-ttu-id="eccc4-177">Dies ist nur verfügbar, wenn Ihre App Symbole für die ausführbare Datei oder die Bibliothek enthält.</span><span class="sxs-lookup"><span data-stu-id="eccc4-177">This is available only if your app includes symbols for the executable or library.</span></span>              |
| <span data-ttu-id="eccc4-178">offset</span><span class="sxs-lookup"><span data-stu-id="eccc4-178">offset</span></span>     | <span data-ttu-id="eccc4-179">string</span><span class="sxs-lookup"><span data-stu-id="eccc4-179">string</span></span>  |  <span data-ttu-id="eccc4-180">Der Byte-Offset der aktuellen Anweisung relativ zum Start der Funktion.</span><span class="sxs-lookup"><span data-stu-id="eccc4-180">The byte offset of the current instruction relative to the start of the function.</span></span>      |


### <a name="response-example"></a><span data-ttu-id="eccc4-181">Antwortbeispiel</span><span class="sxs-lookup"><span data-stu-id="eccc4-181">Response example</span></span>

<span data-ttu-id="eccc4-182">Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.</span><span class="sxs-lookup"><span data-stu-id="eccc4-182">The following example demonstrates an example JSON response body for this request.</span></span>

```json
{
  "Value": [
    {
      "level": "0",
      "image": "Contoso.ContosoApp",
      "function": "Contoso.ContosoApp.MainPage.DoWork",
      "offset": "0x25C"
    }
    {
      "level": "1",
      "image": "Contoso.ContosoApp",
      "function": "Contoso.ContosoApp.MainPage.Initialize",
      "offset": "0x26"
    }
    {
      "level": "2",
      "image": "Contoso.ContosoApp",
      "function": "Contoso.ContosoApp.Start",
      "offset": "0x66"
    }
  ],
  "@nextLink": null,
  "TotalCount": 3
}

```

## <a name="related-topics"></a><span data-ttu-id="eccc4-183">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="eccc4-183">Related topics</span></span>

* [<span data-ttu-id="eccc4-184">Integritätsbericht</span><span class="sxs-lookup"><span data-stu-id="eccc4-184">Health report</span></span>](../publish/health-report.md)
* [<span data-ttu-id="eccc4-185">Zugreifen auf Analysedaten mit MicrosoftStore-Diensten</span><span class="sxs-lookup"><span data-stu-id="eccc4-185">Access analytics data using Microsoft Store services</span></span>](access-analytics-data-using-windows-store-services.md)
* [<span data-ttu-id="eccc4-186">Abrufen von Fehlerberichtsdaten für Ihre Desktopanwendung</span><span class="sxs-lookup"><span data-stu-id="eccc4-186">Get error reporting data for your desktop application</span></span>](get-desktop-application-error-reporting-data.md)
* [<span data-ttu-id="eccc4-187">Abrufen von Details zu einem Fehler in Ihrer Desktopanwendung</span><span class="sxs-lookup"><span data-stu-id="eccc4-187">Get details for an error in your desktop application</span></span>](get-details-for-an-error-in-your-desktop-application.md)
* [<span data-ttu-id="eccc4-188">Herunterladen der CAB-Datei bei einem Fehler in Ihrer Desktopanwendung</span><span class="sxs-lookup"><span data-stu-id="eccc4-188">Download the CAB file for an error in your desktop application</span></span>](download-the-cab-file-for-an-error-in-your-desktop-application.md)
