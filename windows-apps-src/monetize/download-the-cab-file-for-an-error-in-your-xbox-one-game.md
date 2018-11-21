---
author: Xansky
description: Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um die CAB-Datei für einen Fehler in Ihrer Xbox One Spiel herunterzuladen.
title: Herunterladen der CAB-Datei für einen Fehler in Ihrer Xbox One Spiel
ms.author: mhopkins
ms.date: 11/06/2018
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Analyse-API, CAB herunterladen
ms.localizationpriority: medium
ms.openlocfilehash: ad1e3339fe50087c3a3d8cdcf3a99f27c1c868df
ms.sourcegitcommit: 93c0a60cf531c7d9fe7b00e7cf78df86906f9d6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2018
ms.locfileid: "7561147"
---
# <a name="download-the-cab-file-for-an-error-in-your-xbox-one-game"></a><span data-ttu-id="7aa73-104">Herunterladen der CAB-Datei für einen Fehler in Ihrer Xbox One Spiel</span><span class="sxs-lookup"><span data-stu-id="7aa73-104">Download the CAB file for an error in your Xbox One game</span></span>

<span data-ttu-id="7aa73-105">Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um die CAB-Datei herunterzuladen, die mit einem bestimmten Fehler in Ihrer Xbox One Spiel, das über das Xbox-Portal (XDP) aufgenommen wurde und im XDP Analytics Partner Center-Dashboard verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="7aa73-105">Use this method in the Microsoft Store analytics API to download the CAB file that is associated with a particular error in your Xbox One game that was ingested through the Xbox Developer Portal (XDP) and available in the XDP Analytics Partner Center dashboard.</span></span> <span data-ttu-id="7aa73-106">Diese Methode kann nur die CAB-Datei für einen Fehler herunterladen, die in den letzten 30 Tagen aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="7aa73-106">This method can only download the CAB file for an error that occurred in the last 30 days.</span></span>

<span data-ttu-id="7aa73-107">Bevor Sie diese Methode verwenden können, müssen Sie zuerst die Methode zum [Abrufen von Details zu einem Fehler in Ihrer Xbox One Spiel](get-details-for-an-error-in-your-xbox-one-game.md) verwenden, um die ID der CAB-Datei abzurufen, die Sie herunterladen möchten.</span><span class="sxs-lookup"><span data-stu-id="7aa73-107">Before you can use this method, you must first use the [get details for an error in your Xbox One game](get-details-for-an-error-in-your-xbox-one-game.md) method to retrieve the ID of the CAB file you want to download.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7aa73-108">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="7aa73-108">Prerequisites</span></span>


<span data-ttu-id="7aa73-109">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="7aa73-109">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="7aa73-110">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.</span><span class="sxs-lookup"><span data-stu-id="7aa73-110">If you have not done so already, complete all the [prerequisites](access-analytics-data-using-windows-store-services.md#prerequisites) for the Microsoft Store analytics API.</span></span>
* <span data-ttu-id="7aa73-111">[Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="7aa73-111">[Obtain an Azure AD access token](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="7aa73-112">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="7aa73-112">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="7aa73-113">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="7aa73-113">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="7aa73-114">Rufen Sie die ID der CAB-Datei ab, die Sie herunterladen möchten.</span><span class="sxs-lookup"><span data-stu-id="7aa73-114">Get the ID of the CAB file you want to download.</span></span> <span data-ttu-id="7aa73-115">Um diese ID zu erhalten, verwenden Sie die [Details zu einem Fehler in Ihrer Xbox One Spiel abzurufen](get-details-for-an-error-in-your-xbox-one-game.md) Methode zum Abrufen von Details zu einem bestimmten Fehler in Ihrer app, und verwenden Sie den Wert **CabId** im Antworttext dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="7aa73-115">To get this ID, use the [get details for an error in your Xbox One game](get-details-for-an-error-in-your-xbox-one-game.md) method to retrieve details for a specific error in your app, and use the **cabId** value in the response body of that method.</span></span>

## <a name="request"></a><span data-ttu-id="7aa73-116">Anforderung</span><span class="sxs-lookup"><span data-stu-id="7aa73-116">Request</span></span>


### <a name="request-syntax"></a><span data-ttu-id="7aa73-117">Anforderungssyntax</span><span class="sxs-lookup"><span data-stu-id="7aa73-117">Request syntax</span></span>

| <span data-ttu-id="7aa73-118">Methode</span><span class="sxs-lookup"><span data-stu-id="7aa73-118">Method</span></span> | <span data-ttu-id="7aa73-119">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="7aa73-119">Request URI</span></span>                                                          |
|--------|----------------------------------------------------------------------|
| <span data-ttu-id="7aa73-120">GET</span><span class="sxs-lookup"><span data-stu-id="7aa73-120">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/xbox/cabdownload``` |


### <a name="request-header"></a><span data-ttu-id="7aa73-121">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="7aa73-121">Request header</span></span>

| <span data-ttu-id="7aa73-122">Header</span><span class="sxs-lookup"><span data-stu-id="7aa73-122">Header</span></span>        | <span data-ttu-id="7aa73-123">Typ</span><span class="sxs-lookup"><span data-stu-id="7aa73-123">Type</span></span>   | <span data-ttu-id="7aa73-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7aa73-124">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="7aa73-125">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="7aa73-125">Authorization</span></span> | <span data-ttu-id="7aa73-126">String</span><span class="sxs-lookup"><span data-stu-id="7aa73-126">string</span></span> | <span data-ttu-id="7aa73-127">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="7aa73-127">Required.</span></span> <span data-ttu-id="7aa73-128">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="7aa73-128">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="7aa73-129">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="7aa73-129">Request parameters</span></span>

| <span data-ttu-id="7aa73-130">Parameter</span><span class="sxs-lookup"><span data-stu-id="7aa73-130">Parameter</span></span>        | <span data-ttu-id="7aa73-131">Typ</span><span class="sxs-lookup"><span data-stu-id="7aa73-131">Type</span></span>   |  <span data-ttu-id="7aa73-132">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7aa73-132">Description</span></span>      |  <span data-ttu-id="7aa73-133">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="7aa73-133">Required</span></span>  |
|---------------|--------|---------------|------|
| <span data-ttu-id="7aa73-134">applicationId</span><span class="sxs-lookup"><span data-stu-id="7aa73-134">applicationId</span></span> | <span data-ttu-id="7aa73-135">string</span><span class="sxs-lookup"><span data-stu-id="7aa73-135">string</span></span> | <span data-ttu-id="7aa73-136">Die Produkt-ID des Xbox One Spiels, für die Sie die CAB-Datei herunterladen.</span><span class="sxs-lookup"><span data-stu-id="7aa73-136">The product ID of the Xbox One game for which you are downloading the CAB file.</span></span> <span data-ttu-id="7aa73-137">Um die Produkt-ID Ihres Spiels zu erhalten, wechseln Sie zu Ihrem Spiel in der Xbox-Entwickler-Portal (XDP) und rufen Sie die Produkt-ID von der URL ab.</span><span class="sxs-lookup"><span data-stu-id="7aa73-137">To get the product ID of your game, navigate to your game in the Xbox Developer Portal (XDP) and retrieve the product ID from the URL.</span></span> <span data-ttu-id="7aa73-138">Alternativ können ist Sie Ihre integritätsdaten vom Windows Partner Center-Analysebericht herunterladen, die Produkt-ID in der TSV-Datei enthalten.</span><span class="sxs-lookup"><span data-stu-id="7aa73-138">Alternatively, if you download your health data from the Windows Partner Center analytics report, the product ID is included in the .tsv file.</span></span> |  <span data-ttu-id="7aa73-139">Ja</span><span class="sxs-lookup"><span data-stu-id="7aa73-139">Yes</span></span>  |
| <span data-ttu-id="7aa73-140">cabId</span><span class="sxs-lookup"><span data-stu-id="7aa73-140">cabId</span></span> | <span data-ttu-id="7aa73-141">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="7aa73-141">string</span></span> | <span data-ttu-id="7aa73-142">Die eindeutige ID der CAB-Datei ab, die Sie herunterladen möchten.</span><span class="sxs-lookup"><span data-stu-id="7aa73-142">The unique ID of the CAB file you want to download.</span></span> <span data-ttu-id="7aa73-143">Um diese ID zu erhalten, verwenden Sie die [Details zu einem Fehler in Ihrer Xbox One Spiel abzurufen](get-details-for-an-error-in-your-xbox-one-game.md) Methode zum Abrufen von Details zu einem bestimmten Fehler in Ihrer app, und verwenden Sie den Wert **CabId** im Antworttext dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="7aa73-143">To get this ID, use the [get details for an error in your Xbox One game](get-details-for-an-error-in-your-xbox-one-game.md) method to retrieve details for a specific error in your app, and use the **cabId** value in the response body of that method.</span></span> |  <span data-ttu-id="7aa73-144">Ja</span><span class="sxs-lookup"><span data-stu-id="7aa73-144">Yes</span></span>  |

 
### <a name="request-example"></a><span data-ttu-id="7aa73-145">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="7aa73-145">Request example</span></span>

<span data-ttu-id="7aa73-146">Im folgenden Beispiel wird gezeigt, wie Sie mit dieser Methode eine CAB-Datei herunterladen.</span><span class="sxs-lookup"><span data-stu-id="7aa73-146">The following example demonstrates how to download a CAB file using this method.</span></span> <span data-ttu-id="7aa73-147">Ersetzen Sie die Parameter *applicationId* und *cabId* durch die entsprechende Werte für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="7aa73-147">Replace the *applicationId* and *cabId* parameters with the appropriate values for your app.</span></span>

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/xbox/cabdownload?applicationId=BRRT4NJ9B3D1&cabId=1336373323853 HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="7aa73-148">Antwort</span><span class="sxs-lookup"><span data-stu-id="7aa73-148">Response</span></span>

<span data-ttu-id="7aa73-149">Bei dieser Methode wird ein 302-Antwortcode (Umleitung) zurückgegeben, und der **Speicherort**-Header in der Antwort wird der Shared Access Signature (SAS)-URI der CAB-Datei zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="7aa73-149">This method returns a 302 (redirect) response code, and the **Location** header in the response is assigned to the shared access signature (SAS) URI of the CAB file.</span></span> <span data-ttu-id="7aa73-150">Der Aufrufer wird zu dieser URI für den automatischen Download der CAB-Datei weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="7aa73-150">The caller is redirected to this URI to automatically download the CAB file.</span></span>

## <a name="related-topics"></a><span data-ttu-id="7aa73-151">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="7aa73-151">Related topics</span></span>

* [<span data-ttu-id="7aa73-152">Zugreifen auf Analysedaten mit MicrosoftStore-Diensten</span><span class="sxs-lookup"><span data-stu-id="7aa73-152">Access analytics data using Microsoft Store services</span></span>](access-analytics-data-using-windows-store-services.md)
* [<span data-ttu-id="7aa73-153">Abrufen von Fehlerberichtsdaten für Ihre Xbox One Spiel</span><span class="sxs-lookup"><span data-stu-id="7aa73-153">Get error reporting data for your Xbox One game</span></span>](get-error-reporting-data-for-your-xbox-one-game.md)
* [<span data-ttu-id="7aa73-154">Abrufen von Details zu einem Fehler in Ihrer Xbox One-Spiele</span><span class="sxs-lookup"><span data-stu-id="7aa73-154">Get details for an error in your Xbox One game</span></span>](get-details-for-an-error-in-your-xbox-one-game.md)
* [<span data-ttu-id="7aa73-155">Abrufen der stapelüberwachung für einen Fehler in Ihrer Xbox One-Spiele</span><span class="sxs-lookup"><span data-stu-id="7aa73-155">Get the stack trace for an error in your Xbox One game</span></span>](get-the-stack-trace-for-an-error-in-your-xbox-one-game.md)
