---
author: mcleanbyron
ms.assetid: 48D891CD-706C-4759-AB33-B0663774A829
description: Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um die CAB-Datei für einen Windows7- oder Windows8.x Treiberfehler herunterzuladen. Diese Methode ist nur für IHVs bestimmt.
title: Herunterladen der CAB-Datei für einen Windows7- oder Windows8.x-Treiberfehler
ms.author: mcleans
ms.date: 03/17/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Microsoft Store-Analyse-API, CAB herunterladen
ms.localizationpriority: medium
ms.openlocfilehash: 8640506ca954658ad41c5cf70015af52995f7b38
ms.sourcegitcommit: 1773bec0f46906d7b4d71451ba03f47017a87fec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2018
ms.locfileid: "1662330"
---
# <a name="download-the-cab-file-for-a-windows-7-or-windows-8x-driver-error"></a><span data-ttu-id="fcdd6-105">Herunterladen der CAB-Datei für einen Windows7- oder Windows8.x-Treiberfehler</span><span class="sxs-lookup"><span data-stu-id="fcdd6-105">Download the CAB file for a Windows 7 or Windows 8.x driver error</span></span>

<span data-ttu-id="fcdd6-106">Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um die CAB-Datei herunterzuladen, die mit einem bestimmten Windows7-/Windows8.x-Treiberfehler verknüpft ist.</span><span class="sxs-lookup"><span data-stu-id="fcdd6-106">Use this method in the Microsoft Store analytics API to download the CAB file that is associated with a particular Windows 7/Windows 8.x driver error.</span></span> <span data-ttu-id="fcdd6-107">Bevor Sie diese Methode verwenden können, müssen Sie zuerst anhand der Methode zum [Abrufen von Informationen zu einem Windows7- oder Windows8.x-Treiberfehler](get-details-for-a-windows-7-or-windows-8.x-driver-error.md) die ID der CAB-Datei abrufen, die Sie herunterladen möchten.</span><span class="sxs-lookup"><span data-stu-id="fcdd6-107">Before you can use this method, you must first use the [get details for a Windows 7 or Windows 8.x driver error](get-details-for-a-windows-7-or-windows-8.x-driver-error.md) method to retrieve the ID of the CAB file you want to download.</span></span>

<span data-ttu-id="fcdd6-108">Anhand der Methoden zum [Abrufen von Fehlerberichtsdaten für Windows7- und Windows8.x-Treiber](get-error-reporting-data-for-windows-7-and-windows-8.x-drivers.md) und [Abrufen von Informationen zu einem Windows7- oder Windows8.x-Treiberfehler](get-details-for-a-windows-7-or-windows-8.x-driver-error.md) in der Microsoft Store-Analyse-API können Sie weitere Informationen zu Windows7-/Windows8.x-Treiberfehlern abrufen.</span><span class="sxs-lookup"><span data-stu-id="fcdd6-108">You can get other info about Windows 7/Windows 8.x driver errors by using the [get error reporting data for Windows 7 and Windows 8.x drivers](get-error-reporting-data-for-windows-7-and-windows-8.x-drivers.md) and [get details for a Windows 7 or Windows 8.x driver error](get-details-for-a-windows-7-or-windows-8.x-driver-error.md) methods in the Microsoft Store analytics API.</span></span>

> [!NOTE]
> <span data-ttu-id="fcdd6-109">Diese Methode kann nur von Entwicklerkonten verwendet werden, die zum [Windows Hardware Dev Center-Programm](https://msdn.microsoft.com/windows/hardware/drivers/dashboard/get-started-with-the-hardware-dashboard) gehören.</span><span class="sxs-lookup"><span data-stu-id="fcdd6-109">This method can only be used by developer accounts that belong to the [Windows Hardware Dev Center program](https://msdn.microsoft.com/windows/hardware/drivers/dashboard/get-started-with-the-hardware-dashboard).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fcdd6-110">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="fcdd6-110">Prerequisites</span></span>

<span data-ttu-id="fcdd6-111">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="fcdd6-111">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="fcdd6-112">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.</span><span class="sxs-lookup"><span data-stu-id="fcdd6-112">If you have not done so already, complete all the [prerequisites](access-analytics-data-using-windows-store-services.md#prerequisites) for the Microsoft Store analytics API.</span></span>
* <span data-ttu-id="fcdd6-113">[Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="fcdd6-113">[Obtain an Azure AD access token](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="fcdd6-114">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="fcdd6-114">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="fcdd6-115">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="fcdd6-115">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="fcdd6-116">Rufen Sie die ID der CAB-Datei ab, die Sie herunterladen möchten.</span><span class="sxs-lookup"><span data-stu-id="fcdd6-116">Get the ID of the CAB file you want to download.</span></span> <span data-ttu-id="fcdd6-117">Verwenden Sie zum Abrufen dieser ID die Methode zum [Abrufen von Informationen zu einem Windows7- oder Windows8.x-Treiberfehler](get-details-for-a-windows-7-or-windows-8.x-driver-error.md), um Details zu einem bestimmten Treiberfehler abzurufen, und verwenden Sie den **cabIdHash**-Wert im Antworttext dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="fcdd6-117">To get this ID, use the [get details for a Windows 7 or Windows 8.x driver error](get-details-for-a-windows-7-or-windows-8.x-driver-error.md) method to retrieve details for a specific driver error, and use the **cabIdHash** value in the response body of that method.</span></span>

## <a name="request"></a><span data-ttu-id="fcdd6-118">Anforderung</span><span class="sxs-lookup"><span data-stu-id="fcdd6-118">Request</span></span>


### <a name="request-syntax"></a><span data-ttu-id="fcdd6-119">Anforderungssyntax</span><span class="sxs-lookup"><span data-stu-id="fcdd6-119">Request syntax</span></span>

| <span data-ttu-id="fcdd6-120">Methode</span><span class="sxs-lookup"><span data-stu-id="fcdd6-120">Method</span></span> | <span data-ttu-id="fcdd6-121">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="fcdd6-121">Request URI</span></span>                                                          |
|--------|----------------------------------------------------------------------|
| <span data-ttu-id="fcdd6-122">GET</span><span class="sxs-lookup"><span data-stu-id="fcdd6-122">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/ihvdriver/cabdownload``` |


### <a name="request-header"></a><span data-ttu-id="fcdd6-123">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="fcdd6-123">Request header</span></span>

| <span data-ttu-id="fcdd6-124">Header</span><span class="sxs-lookup"><span data-stu-id="fcdd6-124">Header</span></span>        | <span data-ttu-id="fcdd6-125">Typ</span><span class="sxs-lookup"><span data-stu-id="fcdd6-125">Type</span></span>   | <span data-ttu-id="fcdd6-126">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="fcdd6-126">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="fcdd6-127">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="fcdd6-127">Authorization</span></span> | <span data-ttu-id="fcdd6-128">String</span><span class="sxs-lookup"><span data-stu-id="fcdd6-128">string</span></span> | <span data-ttu-id="fcdd6-129">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="fcdd6-129">Required.</span></span> <span data-ttu-id="fcdd6-130">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="fcdd6-130">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |
 

### <a name="request-parameters"></a><span data-ttu-id="fcdd6-131">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="fcdd6-131">Request parameters</span></span>

| <span data-ttu-id="fcdd6-132">Parameter</span><span class="sxs-lookup"><span data-stu-id="fcdd6-132">Parameter</span></span>        | <span data-ttu-id="fcdd6-133">Typ</span><span class="sxs-lookup"><span data-stu-id="fcdd6-133">Type</span></span>   |  <span data-ttu-id="fcdd6-134">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="fcdd6-134">Description</span></span>      |  <span data-ttu-id="fcdd6-135">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="fcdd6-135">Required</span></span>  |
|---------------|--------|---------------|------|
| <span data-ttu-id="fcdd6-136">cabIdHash</span><span class="sxs-lookup"><span data-stu-id="fcdd6-136">cabIdHash</span></span> | <span data-ttu-id="fcdd6-137">String</span><span class="sxs-lookup"><span data-stu-id="fcdd6-137">string</span></span> | <span data-ttu-id="fcdd6-138">Die eindeutige ID der CAB-Datei ab, die Sie herunterladen möchten.</span><span class="sxs-lookup"><span data-stu-id="fcdd6-138">The unique ID of the CAB file you want to download.</span></span> <span data-ttu-id="fcdd6-139">Verwenden Sie zum Abrufen dieser ID die Methode zum [Abrufen von Informationen zu einem Windows7- oder Windows8.x-Treiberfehler](get-details-for-a-windows-7-or-windows-8.x-driver-error.md), um Details zu einem bestimmten Fehler in Ihrer App abzurufen, und verwenden Sie den **cabIdHash**-Wert im Antworttext dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="fcdd6-139">To get this ID, use the [get details for a Windows 7 or Windows 8.x driver error](get-details-for-a-windows-7-or-windows-8.x-driver-error.md) method to retrieve details for a specific error in your app, and use the **cabIdHash** value in the response body of that method.</span></span> |  <span data-ttu-id="fcdd6-140">Ja</span><span class="sxs-lookup"><span data-stu-id="fcdd6-140">Yes</span></span>  |

 
### <a name="request-example"></a><span data-ttu-id="fcdd6-141">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="fcdd6-141">Request example</span></span>

<span data-ttu-id="fcdd6-142">Im folgenden Beispiel wird gezeigt, wie Sie mit dieser Methode eine CAB-Datei herunterladen.</span><span class="sxs-lookup"><span data-stu-id="fcdd6-142">The following example demonstrates how to download a CAB file using this method.</span></span>

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/ihvdriver/cabdownload?cabIdHash=c1a51104-d682-4230-be14-7278b18e3555 HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="fcdd6-143">Antwort</span><span class="sxs-lookup"><span data-stu-id="fcdd6-143">Response</span></span>

<span data-ttu-id="fcdd6-144">Bei dieser Methode wird ein 302-Antwortcode (Umleitung) zurückgegeben, und der **Speicherort**-Header in der Antwort wird der Shared Access Signature (SAS)-URI der CAB-Datei zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="fcdd6-144">This method returns a 302 (redirect) response code, and the **Location** header in the response is assigned to the shared access signature (SAS) URI of the CAB file.</span></span> <span data-ttu-id="fcdd6-145">Der Aufrufer wird zu dieser URI für den automatischen Download der CAB-Datei weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="fcdd6-145">The caller is redirected to this URI to automatically download the CAB file.</span></span>

## <a name="related-topics"></a><span data-ttu-id="fcdd6-146">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="fcdd6-146">Related topics</span></span>

* [<span data-ttu-id="fcdd6-147">Abrufen von Fehlerberichtsdaten für Windows7- und Windows8.x-Treiber</span><span class="sxs-lookup"><span data-stu-id="fcdd6-147">Get error reporting data for Windows 7 and Windows 8.x drivers</span></span>](get-error-reporting-data-for-windows-7-and-windows-8.x-drivers.md)
* [<span data-ttu-id="fcdd6-148">Abrufen von Informationen zu einem Windows7- oder Windows8.x-Treiberfehler</span><span class="sxs-lookup"><span data-stu-id="fcdd6-148">Get details for a Windows 7 or Windows 8.x driver error</span></span>](get-details-for-a-windows-7-or-windows-8.x-driver-error.md)
