---
author: Xansky
ms.assetid: 16D4C3B9-FC9B-46ED-9F87-1517E1B549FA
description: Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API zum Löschen eines Add-Ons für eine App, die für Ihr Windows Dev Center-Konto registriert ist.
title: Löschen eines Add-Ons
ms.author: mhopkins
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Add-on, löschen, In-App-Produkt, IAP
ms.localizationpriority: medium
ms.openlocfilehash: db8c394cac29afabba5229e21712320c82b89364
ms.sourcegitcommit: ca96031debe1e76d4501621a7680079244ef1c60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "5821134"
---
# <a name="delete-an-add-on"></a><span data-ttu-id="0e2d0-104">Löschen eines Add-Ons</span><span class="sxs-lookup"><span data-stu-id="0e2d0-104">Delete an add-on</span></span>

<span data-ttu-id="0e2d0-105">Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API, um ein Add-On (auch als In-App-Produkt oder IAP bezeichnet) für eine App zu löschen, die in Ihrem Windows Dev Center-Konto registriert wurde.</span><span class="sxs-lookup"><span data-stu-id="0e2d0-105">Use this method in the Microsoft Store submission API to delete an add-on (also known as in-app product or IAP) for an app that is registered to your Windows Dev Center account.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0e2d0-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="0e2d0-106">Prerequisites</span></span>

<span data-ttu-id="0e2d0-107">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="0e2d0-107">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="0e2d0-108">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="0e2d0-108">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="0e2d0-109">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="0e2d0-109">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="0e2d0-110">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="0e2d0-110">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="0e2d0-111">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="0e2d0-111">After the token expires, you can obtain a new one.</span></span>

## <a name="request"></a><span data-ttu-id="0e2d0-112">Anforderung</span><span class="sxs-lookup"><span data-stu-id="0e2d0-112">Request</span></span>

<span data-ttu-id="0e2d0-113">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="0e2d0-113">This method has the following syntax.</span></span> <span data-ttu-id="0e2d0-114">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="0e2d0-114">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="0e2d0-115">Methode</span><span class="sxs-lookup"><span data-stu-id="0e2d0-115">Method</span></span> | <span data-ttu-id="0e2d0-116">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="0e2d0-116">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="0e2d0-117">DELETE</span><span class="sxs-lookup"><span data-stu-id="0e2d0-117">DELETE</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/inappproducts/{inAppProductId}``` |


### <a name="request-header"></a><span data-ttu-id="0e2d0-118">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="0e2d0-118">Request header</span></span>

| <span data-ttu-id="0e2d0-119">Header</span><span class="sxs-lookup"><span data-stu-id="0e2d0-119">Header</span></span>        | <span data-ttu-id="0e2d0-120">Typ</span><span class="sxs-lookup"><span data-stu-id="0e2d0-120">Type</span></span>   | <span data-ttu-id="0e2d0-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0e2d0-121">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="0e2d0-122">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="0e2d0-122">Authorization</span></span> | <span data-ttu-id="0e2d0-123">String</span><span class="sxs-lookup"><span data-stu-id="0e2d0-123">string</span></span> | <span data-ttu-id="0e2d0-124">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="0e2d0-124">Required.</span></span> <span data-ttu-id="0e2d0-125">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="0e2d0-125">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="0e2d0-126">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="0e2d0-126">Request parameters</span></span>

| <span data-ttu-id="0e2d0-127">Name</span><span class="sxs-lookup"><span data-stu-id="0e2d0-127">Name</span></span>        | <span data-ttu-id="0e2d0-128">Typ</span><span class="sxs-lookup"><span data-stu-id="0e2d0-128">Type</span></span>   | <span data-ttu-id="0e2d0-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0e2d0-129">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="0e2d0-130">id</span><span class="sxs-lookup"><span data-stu-id="0e2d0-130">id</span></span> | <span data-ttu-id="0e2d0-131">String</span><span class="sxs-lookup"><span data-stu-id="0e2d0-131">string</span></span> | <span data-ttu-id="0e2d0-132">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="0e2d0-132">Required.</span></span> <span data-ttu-id="0e2d0-133">Die Store-ID des zu löschenden Add-Ons.</span><span class="sxs-lookup"><span data-stu-id="0e2d0-133">The Store ID of the add-on to delete.</span></span> <span data-ttu-id="0e2d0-134">Die Store-ID ist im Dev Center-Dashboard verfügbar.</span><span class="sxs-lookup"><span data-stu-id="0e2d0-134">The Store ID is available on the Dev Center dashboard.</span></span>  |


### <a name="request-body"></a><span data-ttu-id="0e2d0-135">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="0e2d0-135">Request body</span></span>

<span data-ttu-id="0e2d0-136">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="0e2d0-136">Do not provide a request body for this method.</span></span>


### <a name="request-example"></a><span data-ttu-id="0e2d0-137">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="0e2d0-137">Request example</span></span>

<span data-ttu-id="0e2d0-138">Im folgenden Beispiel wird das Löschen eines Add-Ons veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="0e2d0-138">The following example demonstrates how to delete an add-on.</span></span>

```
DELETE https://manage.devcenter.microsoft.com/v1.0/my/inappproducts/9NBLGGH4TNMP HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="0e2d0-139">Antwort</span><span class="sxs-lookup"><span data-stu-id="0e2d0-139">Response</span></span>

<span data-ttu-id="0e2d0-140">Wenn dies erfolgreich war, gibt die Methode einen leeren Antworttext zurück.</span><span class="sxs-lookup"><span data-stu-id="0e2d0-140">If successful, this method returns an empty response body.</span></span>

## <a name="error-codes"></a><span data-ttu-id="0e2d0-141">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="0e2d0-141">Error codes</span></span>

<span data-ttu-id="0e2d0-142">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="0e2d0-142">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="0e2d0-143">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="0e2d0-143">Error code</span></span> |  <span data-ttu-id="0e2d0-144">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0e2d0-144">Description</span></span>                                                                                                                                                                           |
|--------|------------------|
| <span data-ttu-id="0e2d0-145">400</span><span class="sxs-lookup"><span data-stu-id="0e2d0-145">400</span></span>  | <span data-ttu-id="0e2d0-146">Die Anforderung ist ungültig.</span><span class="sxs-lookup"><span data-stu-id="0e2d0-146">The request is invalid.</span></span> |
| <span data-ttu-id="0e2d0-147">404</span><span class="sxs-lookup"><span data-stu-id="0e2d0-147">404</span></span>  | <span data-ttu-id="0e2d0-148">Das angegebene Add-On konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="0e2d0-148">The specified add-on could not be found.</span></span>  |
| <span data-ttu-id="0e2d0-149">409</span><span class="sxs-lookup"><span data-stu-id="0e2d0-149">409</span></span>  | <span data-ttu-id="0e2d0-150">Das angegebene Add-On wurde gefunden, konnte jedoch nicht im aktuellen Zustand gelöscht werden. Oder das Add-On verwendet ein Dev Center-Dashboard-Feature, das [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt wird](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span><span class="sxs-lookup"><span data-stu-id="0e2d0-150">The specified add-on was found but it could not be deleted in its current state, or the add-on uses a Dev Center dashboard feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span> |   


## <a name="related-topics"></a><span data-ttu-id="0e2d0-151">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="0e2d0-151">Related topics</span></span>

* [<span data-ttu-id="0e2d0-152">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="0e2d0-152">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="0e2d0-153">Abrufen aller Add-Ons</span><span class="sxs-lookup"><span data-stu-id="0e2d0-153">Get all add-ons</span></span>](get-all-add-ons.md)
* [<span data-ttu-id="0e2d0-154">Abrufen eines Add-Ons</span><span class="sxs-lookup"><span data-stu-id="0e2d0-154">Get an add-on</span></span>](get-an-add-on.md)
* [<span data-ttu-id="0e2d0-155">Erstellen eines Add-Ons</span><span class="sxs-lookup"><span data-stu-id="0e2d0-155">Create an add-on</span></span>](create-an-add-on.md)
