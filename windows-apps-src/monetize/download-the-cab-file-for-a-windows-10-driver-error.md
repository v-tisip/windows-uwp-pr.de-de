---
author: mcleanbyron
ms.assetid: 3D6EE7D7-7D75-499D-AA7A-55DA1C485BA6
description: Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um die CAB-Datei für einen Windows10-Treiberfehler herunterzuladen. Diese Methode ist nur für IHVs bestimmt.
title: Herunterladen der CAB-Datei für einen Windows10-Treiberfehler
ms.author: mcleans
ms.date: 03/17/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Microsoft Store-Analyse-API, CAB herunterladen
ms.localizationpriority: medium
ms.openlocfilehash: 98d83dd6bbaeb67f4601315dbb92b1d2cf8dfd23
ms.sourcegitcommit: 1773bec0f46906d7b4d71451ba03f47017a87fec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2018
ms.locfileid: "1664510"
---
# <a name="download-the-cab-file-for-a-windows-10-driver-error"></a><span data-ttu-id="ee02e-105">Herunterladen der CAB-Datei für einen Windows10-Treiberfehler</span><span class="sxs-lookup"><span data-stu-id="ee02e-105">Download the CAB file for a Windows 10 driver error</span></span>

<span data-ttu-id="ee02e-106">Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um die CAB-Datei herunterzuladen, die mit einem bestimmten Windows10-Treiberfehler verknüpft ist.</span><span class="sxs-lookup"><span data-stu-id="ee02e-106">Use this method in the Microsoft Store analytics API to download the CAB file that is associated with a particular Windows 10 driver error.</span></span> <span data-ttu-id="ee02e-107">Bevor Sie diese Methode verwenden können, müssen Sie zuerst anhand der Methode zum [Abrufen von Informationen zu einem Windows10-Treiberfehler](get-details-for-a-windows-10-driver-error.md) die ID der CAB-Datei abrufen, die Sie herunterladen möchten.</span><span class="sxs-lookup"><span data-stu-id="ee02e-107">Before you can use this method, you must first use the [get details for a Windows 10 driver error](get-details-for-a-windows-10-driver-error.md) method to retrieve the ID of the CAB file you want to download.</span></span>

<span data-ttu-id="ee02e-108">Anhand der Methoden zum [Abrufen von Fehlerberichtsdaten für Windows10-Treiber](get-error-reporting-data-for-windows-10-drivers.md) und [Abrufen von Informationen zu einem Windows10-Treiberfehler](get-details-for-a-windows-10-driver-error.md) in der Microsoft Store-Analyse-API können Sie weitere Informationen zu OEM-Hardwarefehlern abrufen.</span><span class="sxs-lookup"><span data-stu-id="ee02e-108">You can get other info about OEM hardware errors by using the [get error reporting data for Windows 10 drivers](get-error-reporting-data-for-windows-10-drivers.md) and [get details for a Windows 10 driver error](get-details-for-a-windows-10-driver-error.md) methods in the Microsoft Store analytics API.</span></span>

> [!NOTE]
> <span data-ttu-id="ee02e-109">Diese Methode kann nur von Entwicklerkonten verwendet werden, die zum [Windows Hardware Dev Center-Programm](https://msdn.microsoft.com/windows/hardware/drivers/dashboard/get-started-with-the-hardware-dashboard) gehören.</span><span class="sxs-lookup"><span data-stu-id="ee02e-109">This method can only be used by developer accounts that belong to the [Windows Hardware Dev Center program](https://msdn.microsoft.com/windows/hardware/drivers/dashboard/get-started-with-the-hardware-dashboard).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ee02e-110">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="ee02e-110">Prerequisites</span></span>

<span data-ttu-id="ee02e-111">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="ee02e-111">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="ee02e-112">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.</span><span class="sxs-lookup"><span data-stu-id="ee02e-112">If you have not done so already, complete all the [prerequisites](access-analytics-data-using-windows-store-services.md#prerequisites) for the Microsoft Store analytics API.</span></span>
* <span data-ttu-id="ee02e-113">[Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="ee02e-113">[Obtain an Azure AD access token](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="ee02e-114">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="ee02e-114">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="ee02e-115">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="ee02e-115">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="ee02e-116">Rufen Sie die ID der CAB-Datei ab, die Sie herunterladen möchten.</span><span class="sxs-lookup"><span data-stu-id="ee02e-116">Get the ID of the CAB file you want to download.</span></span> <span data-ttu-id="ee02e-117">Verwenden Sie zum Abrufen dieser ID die Methode zum [Abrufen von Informationen zu einem Windows10-Treiberfehler](get-details-for-a-windows-10-driver-error.md), um Details zu einem bestimmten Treiberfehler abzurufen, und verwenden Sie den **cabIdHash**-Wert im Antworttext dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="ee02e-117">To get this ID, use the [get details for a Windows 10 driver error](get-details-for-a-windows-10-driver-error.md) method to retrieve details for a specific driver error, and use the **cabIdHash** value in the response body of that method.</span></span>

## <a name="request"></a><span data-ttu-id="ee02e-118">Anforderung</span><span class="sxs-lookup"><span data-stu-id="ee02e-118">Request</span></span>


### <a name="request-syntax"></a><span data-ttu-id="ee02e-119">Anforderungssyntax</span><span class="sxs-lookup"><span data-stu-id="ee02e-119">Request syntax</span></span>

| <span data-ttu-id="ee02e-120">Methode</span><span class="sxs-lookup"><span data-stu-id="ee02e-120">Method</span></span> | <span data-ttu-id="ee02e-121">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="ee02e-121">Request URI</span></span>                                                          |
|--------|----------------------------------------------------------------------|
| <span data-ttu-id="ee02e-122">GET</span><span class="sxs-lookup"><span data-stu-id="ee02e-122">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/driver/cabdownload``` |


### <a name="request-header"></a><span data-ttu-id="ee02e-123">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="ee02e-123">Request header</span></span>

| <span data-ttu-id="ee02e-124">Header</span><span class="sxs-lookup"><span data-stu-id="ee02e-124">Header</span></span>        | <span data-ttu-id="ee02e-125">Typ</span><span class="sxs-lookup"><span data-stu-id="ee02e-125">Type</span></span>   | <span data-ttu-id="ee02e-126">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ee02e-126">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="ee02e-127">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="ee02e-127">Authorization</span></span> | <span data-ttu-id="ee02e-128">String</span><span class="sxs-lookup"><span data-stu-id="ee02e-128">string</span></span> | <span data-ttu-id="ee02e-129">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="ee02e-129">Required.</span></span> <span data-ttu-id="ee02e-130">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="ee02e-130">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="ee02e-131">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="ee02e-131">Request parameters</span></span>

| <span data-ttu-id="ee02e-132">Parameter</span><span class="sxs-lookup"><span data-stu-id="ee02e-132">Parameter</span></span>        | <span data-ttu-id="ee02e-133">Typ</span><span class="sxs-lookup"><span data-stu-id="ee02e-133">Type</span></span>   |  <span data-ttu-id="ee02e-134">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ee02e-134">Description</span></span>      |  <span data-ttu-id="ee02e-135">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="ee02e-135">Required</span></span>  |
|---------------|--------|---------------|------|
| <span data-ttu-id="ee02e-136">applicationId</span><span class="sxs-lookup"><span data-stu-id="ee02e-136">applicationId</span></span> | <span data-ttu-id="ee02e-137">String</span><span class="sxs-lookup"><span data-stu-id="ee02e-137">string</span></span> | <span data-ttu-id="ee02e-138">Der Produkt-ID-Wert des Treibers, für den Fehlerdaten abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="ee02e-138">The product ID value of the driver for which you want to retrieve error data.</span></span> |  <span data-ttu-id="ee02e-139">Ja</span><span class="sxs-lookup"><span data-stu-id="ee02e-139">Yes</span></span>  |
| <span data-ttu-id="ee02e-140">cabIdHash</span><span class="sxs-lookup"><span data-stu-id="ee02e-140">cabIdHash</span></span> | <span data-ttu-id="ee02e-141">String</span><span class="sxs-lookup"><span data-stu-id="ee02e-141">string</span></span> | <span data-ttu-id="ee02e-142">Die eindeutige ID der CAB-Datei ab, die Sie herunterladen möchten.</span><span class="sxs-lookup"><span data-stu-id="ee02e-142">The unique ID of the CAB file you want to download.</span></span> <span data-ttu-id="ee02e-143">Verwenden Sie zum Abrufen dieser ID die Methode zum [Abrufen von Informationen zu einem Windows10-Treiberfehler](get-details-for-a-windows-10-driver-error.md), um Details zu einem bestimmten Fehler in Ihrer App abzurufen, und verwenden Sie den **cabIdHash**-Wert im Antworttext dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="ee02e-143">To get this ID, use the [get details for a Windows 10 driver error](get-details-for-a-windows-10-driver-error.md) method to retrieve details for a specific error in your app, and use the **cabIdHash** value in the response body of that method.</span></span> |  <span data-ttu-id="ee02e-144">Ja</span><span class="sxs-lookup"><span data-stu-id="ee02e-144">Yes</span></span>  |

 
### <a name="request-example"></a><span data-ttu-id="ee02e-145">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="ee02e-145">Request example</span></span>

<span data-ttu-id="ee02e-146">Im folgenden Beispiel wird gezeigt, wie Sie mit dieser Methode eine CAB-Datei herunterladen.</span><span class="sxs-lookup"><span data-stu-id="ee02e-146">The following example demonstrates how to download a CAB file using this method.</span></span>

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/driver/cabdownload?applicationId=18430592857500421&cabIdHash=c1a51104-d682-4230-be14-7278b18e3555 HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="ee02e-147">Antwort</span><span class="sxs-lookup"><span data-stu-id="ee02e-147">Response</span></span>

<span data-ttu-id="ee02e-148">Bei dieser Methode wird ein 302-Antwortcode (Umleitung) zurückgegeben, und der **Speicherort**-Header in der Antwort wird der Shared Access Signature (SAS)-URI der CAB-Datei zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="ee02e-148">This method returns a 302 (redirect) response code, and the **Location** header in the response is assigned to the shared access signature (SAS) URI of the CAB file.</span></span> <span data-ttu-id="ee02e-149">Der Aufrufer wird zu dieser URI für den automatischen Download der CAB-Datei weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="ee02e-149">The caller is redirected to this URI to automatically download the CAB file.</span></span>

## <a name="related-topics"></a><span data-ttu-id="ee02e-150">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="ee02e-150">Related topics</span></span>

* [<span data-ttu-id="ee02e-151">Abrufen von Fehlerberichtsdaten für Windows10-Treiber</span><span class="sxs-lookup"><span data-stu-id="ee02e-151">Get error reporting data for Windows 10 drivers</span></span>](get-error-reporting-data-for-windows-10-drivers.md)
* [<span data-ttu-id="ee02e-152">Abrufen von Informationen zu einem Windows10-Treiberfehler</span><span class="sxs-lookup"><span data-stu-id="ee02e-152">Get details for a Windows 10 driver error</span></span>](get-details-for-a-windows-10-driver-error.md)
