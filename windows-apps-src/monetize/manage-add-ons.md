---
author: mcleanbyron
ms.assetid: 4F9657E5-1AF8-45E0-9617-45AF64E144FC
description: Verwenden Sie diese Methoden in der Microsoft Store-Übermittlungs-API, um Add-Ons für Apps zu verwalten, die in Ihrem Windows Dev Center-Konto registriert wurden.
title: Verwalten von Add-Ons
ms.author: mcleans
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Add-Ons, In-App-Produkt, IAP
ms.localizationpriority: medium
ms.openlocfilehash: 1d603ab8901eae16da92365042e3244202539586
ms.sourcegitcommit: 1773bec0f46906d7b4d71451ba03f47017a87fec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2018
ms.locfileid: "1663050"
---
# <a name="manage-add-ons"></a><span data-ttu-id="923a5-104">Verwalten von Add-Ons</span><span class="sxs-lookup"><span data-stu-id="923a5-104">Manage add-ons</span></span>

<span data-ttu-id="923a5-105">Mithilfe der folgenden Methoden in der Microsoft Store-Übermittlungs-API können Sie Add-Ons für Ihre Apps verwalten.</span><span class="sxs-lookup"><span data-stu-id="923a5-105">Use the following methods in the Microsoft Store submission API to manage add-ons for your apps.</span></span> <span data-ttu-id="923a5-106">Eine Einführung in die Microsoft Store-Übermittlungs-API einschließlich der Voraussetzungen für die Verwendung der API finden Sie unter [Erstellen und Verwalten von Übermittlungen mit MicrosoftStore-Diensten](create-and-manage-submissions-using-windows-store-services.md).</span><span class="sxs-lookup"><span data-stu-id="923a5-106">For an introduction to the Microsoft Store submission API, including prerequisites for using the API, see [Create and manage submissions using Microsoft Store services](create-and-manage-submissions-using-windows-store-services.md).</span></span>

<span data-ttu-id="923a5-107">Diese Methoden können nur verwendet werden, um Add-Ons abzurufen, zu erstellen oder zu löschen.</span><span class="sxs-lookup"><span data-stu-id="923a5-107">These methods can only be used to get, create, or delete add-ons.</span></span> <span data-ttu-id="923a5-108">Um Übermittlungen für Add-Ons zu erstellen, verwenden Sie die Methoden in [Verwalten von Add-On-Übermittlungen](manage-add-on-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="923a5-108">To create submissions for add-ons, see the methods in [Manage add-on submissions](manage-add-on-submissions.md).</span></span>

<table>
<colgroup>
<col width="10%" />
<col width="30%" />
<col width="60%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="923a5-109">Methode</span><span class="sxs-lookup"><span data-stu-id="923a5-109">Method</span></span></th>
<th align="left"><span data-ttu-id="923a5-110">URI</span><span class="sxs-lookup"><span data-stu-id="923a5-110">URI</span></span></th>
<th align="left"><span data-ttu-id="923a5-111">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="923a5-111">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr>
<td align="left"><span data-ttu-id="923a5-112">GET</span><span class="sxs-lookup"><span data-stu-id="923a5-112">GET</span></span></td>
<td align="left">https://manage.devcenter.microsoft.com/v1.0/my/inappproducts</td>
<td align="left"><a href="get-all-add-ons.md"><span data-ttu-id="923a5-113">Abrufen aller Add-Ons für Ihre Apps</span><span class="sxs-lookup"><span data-stu-id="923a5-113">Get all add-ons for your apps</span></span></a></td>
</tr>
<tr>
<td align="left"><span data-ttu-id="923a5-114">GET</span><span class="sxs-lookup"><span data-stu-id="923a5-114">GET</span></span></td>
<td align="left">https://manage.devcenter.microsoft.com/v1.0/my/inappproducts/{inAppProductId}</td>
<td align="left"><a href="get-an-add-on.md"><span data-ttu-id="923a5-115">Abrufen eines bestimmten Add-Ons</span><span class="sxs-lookup"><span data-stu-id="923a5-115">Get a specific add-on</span></span></a></td>
</tr>
<tr>
<td align="left"><span data-ttu-id="923a5-116">POST</span><span class="sxs-lookup"><span data-stu-id="923a5-116">POST</span></span></td>
<td align="left">https://manage.devcenter.microsoft.com/v1.0/my/inappproducts</td>
<td align="left"><a href="create-an-add-on.md"><span data-ttu-id="923a5-117">Erstellen eines Add-Ons</span><span class="sxs-lookup"><span data-stu-id="923a5-117">Create an add-on</span></span></a></td>
</tr>
<tr>
<td align="left"><span data-ttu-id="923a5-118">DELETE</span><span class="sxs-lookup"><span data-stu-id="923a5-118">DELETE</span></span></td>
<td align="left">https://manage.devcenter.microsoft.com/v1.0/my/inappproducts/{inAppProductId}</td>
<td align="left"><a href="delete-an-add-on.md"><span data-ttu-id="923a5-119">Löschen eines Add-Ons</span><span class="sxs-lookup"><span data-stu-id="923a5-119">Delete an add-on</span></span></a></td>
</tr>
</tbody>
</table>

## <a name="prerequisites"></a><span data-ttu-id="923a5-120">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="923a5-120">Prerequisites</span></span>

<span data-ttu-id="923a5-121">Falls noch nicht geschehen, sorgen Sie vor der Verwendung dieser Methoden dafür, dass alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API erfüllt sind.</span><span class="sxs-lookup"><span data-stu-id="923a5-121">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API before trying to use any of these methods.</span></span>

## <a name="data-resources"></a><span data-ttu-id="923a5-122">Datenressourcen</span><span class="sxs-lookup"><span data-stu-id="923a5-122">Data resources</span></span>

<span data-ttu-id="923a5-123">Die Methoden der Microsoft Store-Übermittlungs-API für das Verwalten von Add-Ons verwenden die folgenden JSON-Datenressourcen.</span><span class="sxs-lookup"><span data-stu-id="923a5-123">The Microsoft Store submission API methods for managing add-ons use the following JSON data resources.</span></span>

<span id="add-on-object" />

### <a name="add-on-resource"></a><span data-ttu-id="923a5-124">Add-On-Ressource</span><span class="sxs-lookup"><span data-stu-id="923a5-124">Add-on resource</span></span>

<span data-ttu-id="923a5-125">Diese Ressource beschreibt ein Add-On.</span><span class="sxs-lookup"><span data-stu-id="923a5-125">This resource describes an add-on.</span></span>

```json
{
  "applications": {
    "value": [
      {
        "id": "9NBLGGH4R315",
        "resourceLocation": "applications/9NBLGGH4R315"
      }
    ],
    "totalCount": 1
  },
  "id": "9NBLGGH4TNMP",
  "productId": "TestAddOn",
  "productType": "Durable",
  "pendingInAppProductSubmission": {
    "id": "1152921504621243619",
    "resourceLocation": "inappproducts/9NBLGGH4TNMP/submissions/1152921504621243619"
  },
  "lastPublishedInAppProductSubmission": {
    "id": "1152921504621243705",
    "resourceLocation": "inappproducts/9NBLGGH4TNMP/submissions/1152921504621243705"
  }
}
```

<span data-ttu-id="923a5-126">Die Ressource hat die folgenden Werte.</span><span class="sxs-lookup"><span data-stu-id="923a5-126">This resource has the following values.</span></span>

| <span data-ttu-id="923a5-127">Wert</span><span class="sxs-lookup"><span data-stu-id="923a5-127">Value</span></span>      | <span data-ttu-id="923a5-128">Typ</span><span class="sxs-lookup"><span data-stu-id="923a5-128">Type</span></span>   | <span data-ttu-id="923a5-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="923a5-129">Description</span></span>        |
|------------|--------|--------------|
| <span data-ttu-id="923a5-130">applications</span><span class="sxs-lookup"><span data-stu-id="923a5-130">applications</span></span>      | <span data-ttu-id="923a5-131">array</span><span class="sxs-lookup"><span data-stu-id="923a5-131">array</span></span>  | <span data-ttu-id="923a5-132">Ein Array mit genau einer [Anwendungsressource](#application-object), die die App darstellt, der dieses Add-On zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="923a5-132">An array that contains one [application resource](#application-object) that represents the app that this add-on is associated with.</span></span> <span data-ttu-id="923a5-133">In diesem Array wird nur ein Element unterstützt.</span><span class="sxs-lookup"><span data-stu-id="923a5-133">Only one item is supported in this array.</span></span>  |
| <span data-ttu-id="923a5-134">id</span><span class="sxs-lookup"><span data-stu-id="923a5-134">id</span></span> | <span data-ttu-id="923a5-135">string</span><span class="sxs-lookup"><span data-stu-id="923a5-135">string</span></span>  | <span data-ttu-id="923a5-136">Die Store-ID des Add-Ons.</span><span class="sxs-lookup"><span data-stu-id="923a5-136">The Store ID of the add-on.</span></span> <span data-ttu-id="923a5-137">Dieser Wert wird vom Store bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="923a5-137">This value is supplied by the Store.</span></span> <span data-ttu-id="923a5-138">Beispiel für eine Store-ID: 9NBLGGH4TNMP.</span><span class="sxs-lookup"><span data-stu-id="923a5-138">An example Store ID is 9NBLGGH4TNMP.</span></span>  |
| <span data-ttu-id="923a5-139">productId</span><span class="sxs-lookup"><span data-stu-id="923a5-139">productId</span></span> | <span data-ttu-id="923a5-140">string</span><span class="sxs-lookup"><span data-stu-id="923a5-140">string</span></span>  | <span data-ttu-id="923a5-141">Die Produkt-ID des Add-Ons.</span><span class="sxs-lookup"><span data-stu-id="923a5-141">The product ID of the add-on.</span></span> <span data-ttu-id="923a5-142">Dies ist die ID, die vom Entwickler während der Erstellung des Add-Ons angegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="923a5-142">This is the ID that was provided by the developer when the add-on was created.</span></span> <span data-ttu-id="923a5-143">Weitere Informationen finden Sie unter [Festlegen von Produkttyp und Produkt-ID für das IAP](https://msdn.microsoft.com/windows/uwp/publish/set-your-iap-product-id).</span><span class="sxs-lookup"><span data-stu-id="923a5-143">For more information, see [Set your product type and product ID](https://msdn.microsoft.com/windows/uwp/publish/set-your-iap-product-id).</span></span> |
| <span data-ttu-id="923a5-144">productType</span><span class="sxs-lookup"><span data-stu-id="923a5-144">productType</span></span> | <span data-ttu-id="923a5-145">string</span><span class="sxs-lookup"><span data-stu-id="923a5-145">string</span></span>  | <span data-ttu-id="923a5-146">Der Produkttyp des Add-Ons.</span><span class="sxs-lookup"><span data-stu-id="923a5-146">The product type of the add-on.</span></span> <span data-ttu-id="923a5-147">Die folgenden Werte werden unterstützt: **Durable** und **Consumable**.</span><span class="sxs-lookup"><span data-stu-id="923a5-147">The following values are supported: **Durable** and **Consumable**.</span></span>  |
| <span data-ttu-id="923a5-148">lastPublishedInAppProductSubmission</span><span class="sxs-lookup"><span data-stu-id="923a5-148">lastPublishedInAppProductSubmission</span></span>       | <span data-ttu-id="923a5-149">object</span><span class="sxs-lookup"><span data-stu-id="923a5-149">object</span></span> | <span data-ttu-id="923a5-150">Eine [Übermittlungsressource](#submission-object) mit Informationen über die letzte veröffentlichte Übermittlung für das Add-On.</span><span class="sxs-lookup"><span data-stu-id="923a5-150">A [submission resource](#submission-object) that provides information about the last published submission for the add-on.</span></span>         |
| <span data-ttu-id="923a5-151">pendingInAppProductSubmission</span><span class="sxs-lookup"><span data-stu-id="923a5-151">pendingInAppProductSubmission</span></span>        | <span data-ttu-id="923a5-152">object</span><span class="sxs-lookup"><span data-stu-id="923a5-152">object</span></span>  |  <span data-ttu-id="923a5-153">Eine [Übermittlungsressource](#submission-object) mit Informationen über die aktuelle ausstehende Übermittlung für das Add-On.</span><span class="sxs-lookup"><span data-stu-id="923a5-153">A [submission resource](#submission-object) that provides information about the current pending submission for the add-on.</span></span>  |   |

<span id="application-object" />

### <a name="application-resource"></a><span data-ttu-id="923a5-154">Anwendungsressource</span><span class="sxs-lookup"><span data-stu-id="923a5-154">Application resource</span></span>

<span data-ttu-id="923a5-155">Diese Ressource beschreibt die App, der ein Add-On zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="923a5-155">This resource descries the app that an add-on is associated with.</span></span> <span data-ttu-id="923a5-156">Das folgende Beispiel veranschaulicht das Format der Ressource.</span><span class="sxs-lookup"><span data-stu-id="923a5-156">The following example demonstrates the format of this resource.</span></span>

```json
{
  "applications": {
    "value": [
      {
        "id": "9NBLGGH4R315",
        "resourceLocation": "applications/9NBLGGH4R315"
      }
    ],
    "totalCount": 1
  },
}
```

<span data-ttu-id="923a5-157">Die Ressource hat die folgenden Werte.</span><span class="sxs-lookup"><span data-stu-id="923a5-157">This resource has the following values.</span></span>

| <span data-ttu-id="923a5-158">Wert</span><span class="sxs-lookup"><span data-stu-id="923a5-158">Value</span></span>           | <span data-ttu-id="923a5-159">Typ</span><span class="sxs-lookup"><span data-stu-id="923a5-159">Type</span></span>    | <span data-ttu-id="923a5-160">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="923a5-160">Description</span></span>        |
|-----------------|---------|-----------|
| <span data-ttu-id="923a5-161">value</span><span class="sxs-lookup"><span data-stu-id="923a5-161">value</span></span>            | <span data-ttu-id="923a5-162">object</span><span class="sxs-lookup"><span data-stu-id="923a5-162">object</span></span>  |  <span data-ttu-id="923a5-163">Ein Objekt, das die folgenden Werte enthält:</span><span class="sxs-lookup"><span data-stu-id="923a5-163">An object that contains the following values:</span></span> <br/><br/> <ul><li><span data-ttu-id="923a5-164">*id*. Die Store-ID der App.</span><span class="sxs-lookup"><span data-stu-id="923a5-164">*id*. The Store ID of the app.</span></span> <span data-ttu-id="923a5-165">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="923a5-165">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span></li><li><span data-ttu-id="923a5-166">*resourceLocation*.</span><span class="sxs-lookup"><span data-stu-id="923a5-166">*resourceLocation*.</span></span> <span data-ttu-id="923a5-167">Ein relativer Pfad, den Sie an den Basisanforderungs-URI ```https://manage.devcenter.microsoft.com/v1.0/my/``` anfügen können, um die vollständigen Daten für die App abzurufen.</span><span class="sxs-lookup"><span data-stu-id="923a5-167">A relative path that you can append to the base ```https://manage.devcenter.microsoft.com/v1.0/my/``` request URI to retrieve the complete data for the app.</span></span></li></ul>   |
| <span data-ttu-id="923a5-168">totalCount</span><span class="sxs-lookup"><span data-stu-id="923a5-168">totalCount</span></span>   | <span data-ttu-id="923a5-169">int</span><span class="sxs-lookup"><span data-stu-id="923a5-169">int</span></span>  | <span data-ttu-id="923a5-170">Die Anzahl der App-Objekte im *applications*-Array des Antworttexts.</span><span class="sxs-lookup"><span data-stu-id="923a5-170">The number of app objects in the *applications* array of the response body.</span></span>                                                                                                                                                 |

<span id="submission-object" />

### <a name="submission-resource"></a><span data-ttu-id="923a5-171">Übermittlungsressource</span><span class="sxs-lookup"><span data-stu-id="923a5-171">Submission resource</span></span>

<span data-ttu-id="923a5-172">Diese Ressource enthält Informationen über eine Übermittlung für ein Add-On.</span><span class="sxs-lookup"><span data-stu-id="923a5-172">This resource provides information about a submission for an add-on.</span></span> <span data-ttu-id="923a5-173">Das folgende Beispiel veranschaulicht das Format der Ressource.</span><span class="sxs-lookup"><span data-stu-id="923a5-173">The following example demonstrates the format of this resource.</span></span>

```json
{
  "pendingInAppProductSubmission": {
    "id": "1152921504621243619",
    "resourceLocation": "inappproducts/9NBLGGH4TNMP/submissions/1152921504621243619"
  },
}
```

<span data-ttu-id="923a5-174">Die Ressource hat die folgenden Werte.</span><span class="sxs-lookup"><span data-stu-id="923a5-174">This resource has the following values.</span></span>

| <span data-ttu-id="923a5-175">Wert</span><span class="sxs-lookup"><span data-stu-id="923a5-175">Value</span></span>           | <span data-ttu-id="923a5-176">Typ</span><span class="sxs-lookup"><span data-stu-id="923a5-176">Type</span></span>    | <span data-ttu-id="923a5-177">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="923a5-177">Description</span></span>     |
|-----------------|---------|------------------|
| <span data-ttu-id="923a5-178">id</span><span class="sxs-lookup"><span data-stu-id="923a5-178">id</span></span>            | <span data-ttu-id="923a5-179">string</span><span class="sxs-lookup"><span data-stu-id="923a5-179">string</span></span>  | <span data-ttu-id="923a5-180">Die ID der Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="923a5-180">The ID of the submission.</span></span>    |
| <span data-ttu-id="923a5-181">resourceLocation</span><span class="sxs-lookup"><span data-stu-id="923a5-181">resourceLocation</span></span>   | <span data-ttu-id="923a5-182">string</span><span class="sxs-lookup"><span data-stu-id="923a5-182">string</span></span>  | <span data-ttu-id="923a5-183">Ein relativer Pfad, den Sie an den Basisanforderungs-URI ```https://manage.devcenter.microsoft.com/v1.0/my/``` anfügen können, um die vollständigen Daten für die Übermittlung abzurufen.</span><span class="sxs-lookup"><span data-stu-id="923a5-183">A relative path that you can append to the base ```https://manage.devcenter.microsoft.com/v1.0/my/``` request URI to retrieve the complete data for the submission.</span></span>     |
 
<span/>

## <a name="related-topics"></a><span data-ttu-id="923a5-184">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="923a5-184">Related topics</span></span>

* [<span data-ttu-id="923a5-185">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="923a5-185">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="923a5-186">Verwalten von Add-On-Übermittlungen mithilfe der Microsoft Store-Übermittlungs-API</span><span class="sxs-lookup"><span data-stu-id="923a5-186">Manage add-on submissions using the Microsoft Store submission API</span></span>](manage-add-on-submissions.md)
* [<span data-ttu-id="923a5-187">Abrufen aller Add-Ons</span><span class="sxs-lookup"><span data-stu-id="923a5-187">Get all add-ons</span></span>](get-all-add-ons.md)
* [<span data-ttu-id="923a5-188">Abrufen eines Add-Ons</span><span class="sxs-lookup"><span data-stu-id="923a5-188">Get an add-on</span></span>](get-an-add-on.md)
* [<span data-ttu-id="923a5-189">Erstellen eines Add-Ons</span><span class="sxs-lookup"><span data-stu-id="923a5-189">Create an add-on</span></span>](create-an-add-on.md)
* [<span data-ttu-id="923a5-190">Löschen eines Add-Ons</span><span class="sxs-lookup"><span data-stu-id="923a5-190">Delete an add-on</span></span>](delete-an-add-on.md)
