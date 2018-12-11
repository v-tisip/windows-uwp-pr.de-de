---
description: Verwenden Sie diese Methode aus der Microsoft Store-Analyse-API, um die CAB-Datei für einen Fehler in der Desktopanwendung herunterzuladen.
title: Herunterladen der CAB-Datei bei einem Fehler in Ihrer Desktopanwendung
ms.date: 03/06/2018
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Analyse-API, CAB herunterladen, Desktopanwendung
ms.localizationpriority: medium
ms.openlocfilehash: 1e3535f18b8127ea18bca234cdcc9b695e89ebfd
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2018
ms.locfileid: "8879251"
---
# <a name="download-the-cab-file-for-an-error-in-your-desktop-application"></a><span data-ttu-id="e36db-104">Herunterladen der CAB-Datei bei einem Fehler in Ihrer Desktopanwendung</span><span class="sxs-lookup"><span data-stu-id="e36db-104">Download the CAB file for an error in your desktop application</span></span>

<span data-ttu-id="e36db-105">Verwenden Sie diese Methode aus der Microsoft Store-Analyse-API, um die CAB-Datei herunterzuladen, die einem bestimmten Fehler einer Desktopanwendung zugeordnet ist, die Sie zum [Windows-Desktopanwendungsprogramm](https://msdn.microsoft.com/library/windows/desktop/mt826504) hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="e36db-105">Use this method in the Microsoft Store analytics API to download the CAB file that is associated with a particular error for a desktop application that you have added to the [Windows Desktop Application program](https://msdn.microsoft.com/library/windows/desktop/mt826504).</span></span> <span data-ttu-id="e36db-106">Diese Methode kann nur die CAB-Datei für einen App-Fehler herunterladen, die in den letzten 30Tagen aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="e36db-106">This method can only download the CAB file for an app error that occurred in the last 30 days.</span></span> <span data-ttu-id="e36db-107">Downloads von CAB-Dateien sind auch im [Bericht "Integrität"](https://msdn.microsoft.com/library/windows/desktop/mt826504) für desktopanwendungen im Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="e36db-107">CAB file downloads are also available in the [Health report](https://msdn.microsoft.com/library/windows/desktop/mt826504) for desktop applications in Partner Center.</span></span>

<span data-ttu-id="e36db-108">Bevor Sie diese Methode verwenden können, müssen Sie zuerst anhand der Methode zum [Abrufen von Informationen zu einem Fehler in der Desktopanwendung](get-details-for-an-error-in-your-desktop-application.md) den ID-Hash der CAB-Datei abrufen, die Sie herunterladen möchten.</span><span class="sxs-lookup"><span data-stu-id="e36db-108">Before you can use this method, you must first use the [get details for an error in your desktop application](get-details-for-an-error-in-your-desktop-application.md) method to retrieve the ID hash of the CAB file you want to download.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e36db-109">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="e36db-109">Prerequisites</span></span>


<span data-ttu-id="e36db-110">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="e36db-110">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="e36db-111">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.</span><span class="sxs-lookup"><span data-stu-id="e36db-111">If you have not done so already, complete all the [prerequisites](access-analytics-data-using-windows-store-services.md#prerequisites) for the Microsoft Store analytics API.</span></span>
* <span data-ttu-id="e36db-112">[Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="e36db-112">[Obtain an Azure AD access token](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="e36db-113">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="e36db-113">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="e36db-114">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="e36db-114">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="e36db-115">Rufen Sie den ID-Hash der CAB-Datei ab, die Sie herunterladen möchten.</span><span class="sxs-lookup"><span data-stu-id="e36db-115">Get the ID hash of the CAB file you want to download.</span></span> <span data-ttu-id="e36db-116">Verwenden Sie zum Abrufen dieses Wertes die Methode zum [Abrufen von Details zu einem Fehler in Ihrer Desktopanwendung](get-details-for-an-error-in-your-desktop-application.md), um Details zu einem bestimmten Fehler in Ihrer App abzurufen, und verwenden Sie den **cabIdHash**-Wert im Antworttext dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="e36db-116">To get this value, use the [get details for an error in your desktop application](get-details-for-an-error-in-your-desktop-application.md) method to retrieve details for a specific error in your app, and use the **cabIdHash** value in the response body of that method.</span></span>

## <a name="request"></a><span data-ttu-id="e36db-117">Anforderung</span><span class="sxs-lookup"><span data-stu-id="e36db-117">Request</span></span>


### <a name="request-syntax"></a><span data-ttu-id="e36db-118">Anforderungssyntax</span><span class="sxs-lookup"><span data-stu-id="e36db-118">Request syntax</span></span>

| <span data-ttu-id="e36db-119">Methode</span><span class="sxs-lookup"><span data-stu-id="e36db-119">Method</span></span> | <span data-ttu-id="e36db-120">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="e36db-120">Request URI</span></span>                                                          |
|--------|----------------------------------------------------------------------|
| <span data-ttu-id="e36db-121">GET</span><span class="sxs-lookup"><span data-stu-id="e36db-121">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/desktop/cabdownload``` |


### <a name="request-header"></a><span data-ttu-id="e36db-122">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="e36db-122">Request header</span></span>

| <span data-ttu-id="e36db-123">Header</span><span class="sxs-lookup"><span data-stu-id="e36db-123">Header</span></span>        | <span data-ttu-id="e36db-124">Typ</span><span class="sxs-lookup"><span data-stu-id="e36db-124">Type</span></span>   | <span data-ttu-id="e36db-125">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e36db-125">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="e36db-126">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="e36db-126">Authorization</span></span> | <span data-ttu-id="e36db-127">String</span><span class="sxs-lookup"><span data-stu-id="e36db-127">string</span></span> | <span data-ttu-id="e36db-128">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="e36db-128">Required.</span></span> <span data-ttu-id="e36db-129">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="e36db-129">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="e36db-130">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="e36db-130">Request parameters</span></span>

| <span data-ttu-id="e36db-131">Parameter</span><span class="sxs-lookup"><span data-stu-id="e36db-131">Parameter</span></span>        | <span data-ttu-id="e36db-132">Typ</span><span class="sxs-lookup"><span data-stu-id="e36db-132">Type</span></span>   |  <span data-ttu-id="e36db-133">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e36db-133">Description</span></span>      |  <span data-ttu-id="e36db-134">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="e36db-134">Required</span></span>  |
|---------------|--------|---------------|------|
| <span data-ttu-id="e36db-135">applicationId</span><span class="sxs-lookup"><span data-stu-id="e36db-135">applicationId</span></span> | <span data-ttu-id="e36db-136">string</span><span class="sxs-lookup"><span data-stu-id="e36db-136">string</span></span> | <span data-ttu-id="e36db-137">Die Produkt-ID der Desktopanwendung, für die Sie eine CAB-Datei herunterladen möchten.</span><span class="sxs-lookup"><span data-stu-id="e36db-137">The product ID of the desktop application for which you want to download a CAB file.</span></span> <span data-ttu-id="e36db-138">Um die Produkt-ID einer desktop-Anwendung zu erhalten, öffnen Sie eine [Partner Center-Analysebericht für Ihre desktop-Anwendung](https://msdn.microsoft.com/library/windows/desktop/mt826504) (z. B. den **Bericht "Integrität"**), und rufen Sie die Produkt-ID aus der URL.</span><span class="sxs-lookup"><span data-stu-id="e36db-138">To get the product ID of a desktop application, open any [Partner Center analytics report for your desktop application](https://msdn.microsoft.com/library/windows/desktop/mt826504) (such as the **Health report**) and retrieve the product ID from the URL.</span></span> |  <span data-ttu-id="e36db-139">Ja</span><span class="sxs-lookup"><span data-stu-id="e36db-139">Yes</span></span>  |
| <span data-ttu-id="e36db-140">cabIdHash</span><span class="sxs-lookup"><span data-stu-id="e36db-140">cabIdHash</span></span> | <span data-ttu-id="e36db-141">string</span><span class="sxs-lookup"><span data-stu-id="e36db-141">string</span></span> | <span data-ttu-id="e36db-142">Der eindeutige ID-Hash der CAB-Datei ab, die Sie herunterladen möchten.</span><span class="sxs-lookup"><span data-stu-id="e36db-142">The unique ID hash of the CAB file you want to download.</span></span> <span data-ttu-id="e36db-143">Verwenden Sie zum Abrufen dieses Wertes die Methode zum [Abrufen von Details zu einem Fehler in Ihrer Desktopanwendung](get-details-for-an-error-in-your-desktop-application.md), um Details zu einem bestimmten Fehler in Ihrer Anwendung abzurufen, und verwenden Sie den **cabIdHash**-Wert im Antworttext dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="e36db-143">To get this value, use the [get details for an error in your desktop application](get-details-for-an-error-in-your-desktop-application.md) method to retrieve details for a specific error in your application, and use the **cabIdHash** value in the response body of that method.</span></span> |  <span data-ttu-id="e36db-144">Ja</span><span class="sxs-lookup"><span data-stu-id="e36db-144">Yes</span></span>  |


### <a name="request-example"></a><span data-ttu-id="e36db-145">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="e36db-145">Request example</span></span>

<span data-ttu-id="e36db-146">Im folgenden Beispiel wird gezeigt, wie Sie mit dieser Methode eine CAB-Datei herunterladen.</span><span class="sxs-lookup"><span data-stu-id="e36db-146">The following example demonstrates how to download a CAB file using this method.</span></span> <span data-ttu-id="e36db-147">Ersetzen Sie die Parameter *applicationId* und *cabIdHash* durch die entsprechende Werte für Ihre Desktopanwendung.</span><span class="sxs-lookup"><span data-stu-id="e36db-147">Replace the *applicationId* and *cabIdHash* parameters with the appropriate values for your desktop application.</span></span>

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/desktop/cabdownload?applicationId=10238467886765136388&cabIdHash=54ffb83a-e159-41d2-8158-f36f306cc01e HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="e36db-148">Antwort</span><span class="sxs-lookup"><span data-stu-id="e36db-148">Response</span></span>

<span data-ttu-id="e36db-149">Bei dieser Methode wird ein 302-Antwortcode (Umleitung) zurückgegeben, und der **Speicherort**-Header in der Antwort wird der Shared Access Signature (SAS)-URI der CAB-Datei zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="e36db-149">This method returns a 302 (redirect) response code, and the **Location** header in the response is assigned to the shared access signature (SAS) URI of the CAB file.</span></span> <span data-ttu-id="e36db-150">Der Aufrufer wird zu dieser URI für den automatischen Download der CAB-Datei weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="e36db-150">The caller is redirected to this URI to automatically download the CAB file.</span></span>

## <a name="related-topics"></a><span data-ttu-id="e36db-151">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="e36db-151">Related topics</span></span>

* [<span data-ttu-id="e36db-152">Integritätsbericht</span><span class="sxs-lookup"><span data-stu-id="e36db-152">Health report</span></span>](../publish/health-report.md)
* [<span data-ttu-id="e36db-153">Zugreifen auf Analysedaten mit MicrosoftStore-Diensten</span><span class="sxs-lookup"><span data-stu-id="e36db-153">Access analytics data using Microsoft Store services</span></span>](access-analytics-data-using-windows-store-services.md)
* [<span data-ttu-id="e36db-154">Abrufen von Fehlerberichtsdaten für Ihre Desktopanwendung</span><span class="sxs-lookup"><span data-stu-id="e36db-154">Get error reporting data for your desktop application</span></span>](get-desktop-application-error-reporting-data.md)
* [<span data-ttu-id="e36db-155">Abrufen von Details zu einem Fehler in der Desktopanwendung</span><span class="sxs-lookup"><span data-stu-id="e36db-155">Get details for an error in your desktop application</span></span>](get-details-for-an-error-in-your-desktop-application.md)
* [<span data-ttu-id="e36db-156">Abrufen der Stapelüberwachung für einen Fehler in Ihrer Desktopanwendung</span><span class="sxs-lookup"><span data-stu-id="e36db-156">Get the stack trace for an error in your desktop application</span></span>](get-the-stack-trace-for-an-error-in-your-desktop-application.md)
