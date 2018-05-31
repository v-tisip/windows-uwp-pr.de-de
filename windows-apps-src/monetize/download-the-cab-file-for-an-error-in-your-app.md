---
author: mcleanbyron
ms.assetid: ''
description: Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um die CAB-Datei für einen Fehler in der App herunterzuladen.
title: Herunterladen der CAB-Datei bei einem Fehler in Ihrer App
ms.author: mcleans
ms.date: 06/16/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Microsoft Store-Analyse-API, CAB herunterladen
ms.localizationpriority: medium
ms.openlocfilehash: a74a72e1d02a73d2b930179d9d2cb99ea09c7c40
ms.sourcegitcommit: 1773bec0f46906d7b4d71451ba03f47017a87fec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2018
ms.locfileid: "1662060"
---
# <a name="download-the-cab-file-for-an-error-in-your-app"></a><span data-ttu-id="cd2b6-104">Herunterladen der CAB-Datei bei einem Fehler in Ihrer App</span><span class="sxs-lookup"><span data-stu-id="cd2b6-104">Download the CAB file for an error in your app</span></span>

<span data-ttu-id="cd2b6-105">Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um die CAB-Datei herunterzuladen, die mit einem bestimmten im Dev Center gemeldeten Fehler in der App verknüpft ist.</span><span class="sxs-lookup"><span data-stu-id="cd2b6-105">Use this method in the Microsoft Store analytics API to download the CAB file that is associated with a particular error in your app that was reported to Dev Center.</span></span> <span data-ttu-id="cd2b6-106">Diese Methode kann nur die CAB-Datei für einen App-Fehler herunterladen, die in den letzten 30Tagen aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="cd2b6-106">This method can only download the CAB file for an app error that occurred in the last 30 days.</span></span> <span data-ttu-id="cd2b6-107">CAB-Datei-Downloads sind auch im Abschnitt **Fehler** des [Integritätsberichts](../publish/health-report.md) im Windows Dev Center-Dashboard verfügbar.</span><span class="sxs-lookup"><span data-stu-id="cd2b6-107">CAB file downloads are also available in the **Failures** section of the [Health report](../publish/health-report.md) in the Windows Dev Center dashboard.</span></span>

<span data-ttu-id="cd2b6-108">Bevor Sie diese Methode verwenden können, müssen Sie zuerst anhand der Methode zum [Abrufen von Informationen zu einem Fehler in der App](get-details-for-an-error-in-your-app.md) die ID der CAB-Datei abrufen, die Sie herunterladen möchten.</span><span class="sxs-lookup"><span data-stu-id="cd2b6-108">Before you can use this method, you must first use the [get details for an error in your app](get-details-for-an-error-in-your-app.md) method to retrieve the ID of the CAB file you want to download.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cd2b6-109">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="cd2b6-109">Prerequisites</span></span>


<span data-ttu-id="cd2b6-110">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="cd2b6-110">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="cd2b6-111">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.</span><span class="sxs-lookup"><span data-stu-id="cd2b6-111">If you have not done so already, complete all the [prerequisites](access-analytics-data-using-windows-store-services.md#prerequisites) for the Microsoft Store analytics API.</span></span>
* <span data-ttu-id="cd2b6-112">[Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="cd2b6-112">[Obtain an Azure AD access token](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="cd2b6-113">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="cd2b6-113">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="cd2b6-114">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="cd2b6-114">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="cd2b6-115">Rufen Sie die ID der CAB-Datei ab, die Sie herunterladen möchten.</span><span class="sxs-lookup"><span data-stu-id="cd2b6-115">Get the ID of the CAB file you want to download.</span></span> <span data-ttu-id="cd2b6-116">Verwenden Sie zum Abrufen dieser ID die Methode zum [Abrufen von Details zu einem Fehler in Ihrer App](get-details-for-an-error-in-your-app.md), um Details zu einem bestimmten Fehler in Ihrer App abzurufen, und verwenden Sie den **cabId**-Wert im Antworttext dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="cd2b6-116">To get this ID, use the [get details for an error in your app](get-details-for-an-error-in-your-app.md) method to retrieve details for a specific error in your app, and use the **cabId** value in the response body of that method.</span></span>

## <a name="request"></a><span data-ttu-id="cd2b6-117">Anforderung</span><span class="sxs-lookup"><span data-stu-id="cd2b6-117">Request</span></span>


### <a name="request-syntax"></a><span data-ttu-id="cd2b6-118">Anforderungssyntax</span><span class="sxs-lookup"><span data-stu-id="cd2b6-118">Request syntax</span></span>

| <span data-ttu-id="cd2b6-119">Methode</span><span class="sxs-lookup"><span data-stu-id="cd2b6-119">Method</span></span> | <span data-ttu-id="cd2b6-120">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="cd2b6-120">Request URI</span></span>                                                          |
|--------|----------------------------------------------------------------------|
| <span data-ttu-id="cd2b6-121">GET</span><span class="sxs-lookup"><span data-stu-id="cd2b6-121">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/cabdownload``` |


### <a name="request-header"></a><span data-ttu-id="cd2b6-122">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="cd2b6-122">Request header</span></span>

| <span data-ttu-id="cd2b6-123">Header</span><span class="sxs-lookup"><span data-stu-id="cd2b6-123">Header</span></span>        | <span data-ttu-id="cd2b6-124">Typ</span><span class="sxs-lookup"><span data-stu-id="cd2b6-124">Type</span></span>   | <span data-ttu-id="cd2b6-125">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="cd2b6-125">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="cd2b6-126">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="cd2b6-126">Authorization</span></span> | <span data-ttu-id="cd2b6-127">String</span><span class="sxs-lookup"><span data-stu-id="cd2b6-127">string</span></span> | <span data-ttu-id="cd2b6-128">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="cd2b6-128">Required.</span></span> <span data-ttu-id="cd2b6-129">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="cd2b6-129">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="cd2b6-130">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="cd2b6-130">Request parameters</span></span>

| <span data-ttu-id="cd2b6-131">Parameter</span><span class="sxs-lookup"><span data-stu-id="cd2b6-131">Parameter</span></span>        | <span data-ttu-id="cd2b6-132">Typ</span><span class="sxs-lookup"><span data-stu-id="cd2b6-132">Type</span></span>   |  <span data-ttu-id="cd2b6-133">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="cd2b6-133">Description</span></span>      |  <span data-ttu-id="cd2b6-134">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="cd2b6-134">Required</span></span>  |
|---------------|--------|---------------|------|
| <span data-ttu-id="cd2b6-135">applicationId</span><span class="sxs-lookup"><span data-stu-id="cd2b6-135">applicationId</span></span> | <span data-ttu-id="cd2b6-136">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="cd2b6-136">string</span></span> | <span data-ttu-id="cd2b6-137">Die Store-ID der App, für die Sie die CAB-Kaufdaten herunterladen möchten.</span><span class="sxs-lookup"><span data-stu-id="cd2b6-137">The Store ID of the app for which you want to download a CAB file.</span></span> <span data-ttu-id="cd2b6-138">Die Store-ID ist auf der [Seite mit der App-Identität](../publish/view-app-identity-details.md) des DevCenter-Dashboards verfügbar.</span><span class="sxs-lookup"><span data-stu-id="cd2b6-138">The Store ID is available on the [App identity page](../publish/view-app-identity-details.md) of the Dev Center dashboard.</span></span> <span data-ttu-id="cd2b6-139">Beispiel für eine Store-ID: 9WZDNCRFJ3Q8.</span><span class="sxs-lookup"><span data-stu-id="cd2b6-139">An example Store ID is 9WZDNCRFJ3Q8.</span></span> |  <span data-ttu-id="cd2b6-140">Ja</span><span class="sxs-lookup"><span data-stu-id="cd2b6-140">Yes</span></span>  |
| <span data-ttu-id="cd2b6-141">cabId</span><span class="sxs-lookup"><span data-stu-id="cd2b6-141">cabId</span></span> | <span data-ttu-id="cd2b6-142">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="cd2b6-142">string</span></span> | <span data-ttu-id="cd2b6-143">Die eindeutige ID der CAB-Datei ab, die Sie herunterladen möchten.</span><span class="sxs-lookup"><span data-stu-id="cd2b6-143">The unique ID of the CAB file you want to download.</span></span> <span data-ttu-id="cd2b6-144">Verwenden Sie zum Abrufen dieser ID die Methode zum [Abrufen von Details zu einem Fehler in Ihrer App](get-details-for-an-error-in-your-app.md), um Details zu einem bestimmten Fehler in Ihrer App abzurufen, und verwenden Sie den **cabId**-Wert im Antworttext dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="cd2b6-144">To get this ID, use the [get details for an error in your app](get-details-for-an-error-in-your-app.md) method to retrieve details for a specific error in your app, and use the **cabId** value in the response body of that method.</span></span> |  <span data-ttu-id="cd2b6-145">Ja</span><span class="sxs-lookup"><span data-stu-id="cd2b6-145">Yes</span></span>  |

 
### <a name="request-example"></a><span data-ttu-id="cd2b6-146">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="cd2b6-146">Request example</span></span>

<span data-ttu-id="cd2b6-147">Im folgenden Beispiel wird gezeigt, wie Sie mit dieser Methode eine CAB-Datei herunterladen.</span><span class="sxs-lookup"><span data-stu-id="cd2b6-147">The following example demonstrates how to download a CAB file using this method.</span></span> <span data-ttu-id="cd2b6-148">Ersetzen Sie die Parameter *applicationId* und *cabId* durch die entsprechende Werte für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="cd2b6-148">Replace the *applicationId* and *cabId* parameters with the appropriate values for your app.</span></span>

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/cabdownload?applicationId=9NBLGGGZ5QDR&cabId=1336373323853 HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="cd2b6-149">Antwort</span><span class="sxs-lookup"><span data-stu-id="cd2b6-149">Response</span></span>

<span data-ttu-id="cd2b6-150">Bei dieser Methode wird ein 302-Antwortcode (Umleitung) zurückgegeben, und der **Speicherort**-Header in der Antwort wird der Shared Access Signature (SAS)-URI der CAB-Datei zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="cd2b6-150">This method returns a 302 (redirect) response code, and the **Location** header in the response is assigned to the shared access signature (SAS) URI of the CAB file.</span></span> <span data-ttu-id="cd2b6-151">Der Aufrufer wird zu dieser URI für den automatischen Download der CAB-Datei weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="cd2b6-151">The caller is redirected to this URI to automatically download the CAB file.</span></span>

## <a name="related-topics"></a><span data-ttu-id="cd2b6-152">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="cd2b6-152">Related topics</span></span>

* [<span data-ttu-id="cd2b6-153">Integritätsbericht</span><span class="sxs-lookup"><span data-stu-id="cd2b6-153">Health report</span></span>](../publish/health-report.md)
* [<span data-ttu-id="cd2b6-154">Zugreifen auf Analysedaten mit MicrosoftStore-Diensten</span><span class="sxs-lookup"><span data-stu-id="cd2b6-154">Access analytics data using Microsoft Store services</span></span>](access-analytics-data-using-windows-store-services.md)
* [<span data-ttu-id="cd2b6-155">Abrufen von Fehlerberichtsdaten</span><span class="sxs-lookup"><span data-stu-id="cd2b6-155">Get error reporting data</span></span>](get-error-reporting-data.md)
* [<span data-ttu-id="cd2b6-156">Abrufen von Details zu einem Fehler in Ihrer App</span><span class="sxs-lookup"><span data-stu-id="cd2b6-156">Get details for an error in your app</span></span>](get-details-for-an-error-in-your-app.md)
* [<span data-ttu-id="cd2b6-157">Abrufen der Stapelüberwachung für einen Fehler in Ihrer App</span><span class="sxs-lookup"><span data-stu-id="cd2b6-157">Get the stack trace for an error in your app</span></span>](get-the-stack-trace-for-an-error-in-your-app.md)
