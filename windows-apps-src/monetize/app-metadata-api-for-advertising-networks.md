---
author: Xansky
description: Hier erfahren Sie, wie Sie die REST-API für App-Metadaten verwenden, um auf bestimmte Typen von Metadaten für Apps zuzugreifen. Diese API soll von Anzeigennetzwerken verwendet werden, um Informationen zu Apps im Microsoft Store abzurufen und so den Vertrieb von Werbeflächen an Inserenten zu verbessern.
title: App-Metadaten-API für Anzeigennetzwerke
ms.author: mhopkins
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Anzeigennetzwerke, App-Metadaten
ms.assetid: f0904086-d61f-4adb-82b6-25968cbec7f3
ms.localizationpriority: medium
ms.openlocfilehash: 9533b244174cc5770a68f866c722db1781fdd544
ms.sourcegitcommit: f2c9a050a9137a473f28b613968d5782866142c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2018
ms.locfileid: "6268775"
---
# <a name="app-metadata-api-for-advertising-networks"></a><span data-ttu-id="ecef4-105">App-Metadaten-API für Anzeigennetzwerke</span><span class="sxs-lookup"><span data-stu-id="ecef4-105">App metadata API for advertising networks</span></span>

<span data-ttu-id="ecef4-106">Anzeigennetzwerke können die *App-Metadaten-API* nutzen, um programmgesteuert Metadaten zu Apps im Microsoft Store abzurufen, einschließlich Details wie die Beschreibung und Kategorie für den Store-Eintrag der App und Angaben dazu, ob die App für Kinder unter 13Jahren geeignet ist.</span><span class="sxs-lookup"><span data-stu-id="ecef4-106">Advertising networks can use the *app metadata API* to programmatically retrieve metadata about apps in the Microsoft Store, including details such as the description and category for the Store listing of the app and whether the app is targeted to children under 13.</span></span> <span data-ttu-id="ecef4-107">Der Zugriff auf die API beschränkt sich derzeit auf Entwickler, die von Microsoft eine Berechtigung zur Nutzung der API erhalten haben.</span><span class="sxs-lookup"><span data-stu-id="ecef4-107">Access to this API is currently restricted to developers who are granted permission to the API by Microsoft.</span></span>

<span data-ttu-id="ecef4-108">In diesem Artikel wird erläutert, wie Sie über das [Portal für die App-Metadaten-API](https://admetadata.portal.azure-api.net/) Zugriff auf die API anfordern, Ihren Abonnementschlüssel für den Zugriff auf die API abrufen und die API aufrufen.</span><span class="sxs-lookup"><span data-stu-id="ecef4-108">This article provides instructions for how to request access to the API using the [app metadata API portal](https://admetadata.portal.azure-api.net/), how to get your subscription key to access the API, and how to call the API.</span></span>

## <a name="request-access"></a><span data-ttu-id="ecef4-109">Anfordern des Zugriffs</span><span class="sxs-lookup"><span data-stu-id="ecef4-109">Request access</span></span>

<span data-ttu-id="ecef4-110">Betreiber von Anzeigennetzwerken können den Zugriff auf die App-Metadaten-API anfordern, indem sie die nachstehenden Schritte befolgen:</span><span class="sxs-lookup"><span data-stu-id="ecef4-110">Advertising networks can request access to the app metadata API by following these instructions:</span></span>

1. <span data-ttu-id="ecef4-111">Wechseln Sie auf die [https://admetadata.portal.azure-api.net/signup](https://admetadata.portal.azure-api.net/signup) Seite mit dem Portal für die App-Metadaten-API.</span><span class="sxs-lookup"><span data-stu-id="ecef4-111">Go to the [https://admetadata.portal.azure-api.net/signup](https://admetadata.portal.azure-api.net/signup) page of the app metadata API portal.</span></span>
2. <span data-ttu-id="ecef4-112">Geben Sie die erforderlichen Informationen ein, und klicken Sie auf die Schaltfläche **Registrieren**.</span><span class="sxs-lookup"><span data-stu-id="ecef4-112">Enter the required information and click the **Sign up** button.</span></span>
3. <span data-ttu-id="ecef4-113">Klicken Sie auf der gleichen Website auf die Registerkarte **Produkte** und dann auf **App details for advertising**.</span><span class="sxs-lookup"><span data-stu-id="ecef4-113">On the same site, click the **Products** tab and then click **App details for advertising**.</span></span>
4. <span data-ttu-id="ecef4-114">Klicken Sie auf der nächsten Seite auf die Schaltfläche **Abonnieren**.</span><span class="sxs-lookup"><span data-stu-id="ecef4-114">On the next page, click the **Subscribe** button.</span></span> <span data-ttu-id="ecef4-115">Dadurch wird Ihre Anfrage für den Zugriff auf die App-Metadaten-API an Microsoft übermittelt.</span><span class="sxs-lookup"><span data-stu-id="ecef4-115">This submits your request to access the app metadata API to Microsoft.</span></span>

<span data-ttu-id="ecef4-116">Nachdem Ihre Anfrage übermittelt wurde, erhalten Sie innerhalb von ca. 24 Stunden eine E-Mail mit der Mitteilung, ob Ihre Anfrage gewährt oder abgelehnt wurde.</span><span class="sxs-lookup"><span data-stu-id="ecef4-116">After your request is submitted, you will receive an email within approximately 24 hours that notifies you if your request was granted or denied.</span></span>

<span id="get-key" />

## <a name="get-your-subscription-key"></a><span data-ttu-id="ecef4-117">Abrufen des Abonnementschlüssels</span><span class="sxs-lookup"><span data-stu-id="ecef4-117">Get your subscription key</span></span>

<span data-ttu-id="ecef4-118">Wenn Ihnen Zugriff auf die App-Metadaten-API gewährt wurde, befolgen Sie die nachstehenden Schritte, um Ihren Abonnementschlüssel abzurufen.</span><span class="sxs-lookup"><span data-stu-id="ecef4-118">If you are granted access to the app metadata API, follow these instructions to get your subscription key.</span></span> <span data-ttu-id="ecef4-119">Sie müssen diesen Schlüssel im Anforderungsheader von Aufrufen der API übergeben.</span><span class="sxs-lookup"><span data-stu-id="ecef4-119">You must pass this key in the request header of calls to the API.</span></span>

1. <span data-ttu-id="ecef4-120">Wechseln Sie auf die [https://admetadata.portal.azure-api.net/signin](https://admetadata.portal.azure-api.net/signin) Seite mit dem Portal für die App-Metadaten-API, und melden Sie sich mit Ihrer E-Mail-Adresse und Ihrem Kennwort an.</span><span class="sxs-lookup"><span data-stu-id="ecef4-120">Go to the [https://admetadata.portal.azure-api.net/signin](https://admetadata.portal.azure-api.net/signin) page of the app metadata API portal and sign in with your email and password.</span></span>
2. <span data-ttu-id="ecef4-121">Klicken Sie in der oberen rechten Ecke der Website auf Ihren Namen, und klicken Sie dann auf **Profil**.</span><span class="sxs-lookup"><span data-stu-id="ecef4-121">Click your name in the top-right corner of the site and then click **Profile**.</span></span>
3. <span data-ttu-id="ecef4-122">Klicken Sie auf der Seite im Abschnitt **Ihre Abonnements** neben **Primärschlüssel** auf **Anzeigen**.</span><span class="sxs-lookup"><span data-stu-id="ecef4-122">In the **Your subscriptions** section of the page, click **Show** next to **Primary key**.</span></span> <span data-ttu-id="ecef4-123">Dies ist Ihr Abonnementschlüssel.</span><span class="sxs-lookup"><span data-stu-id="ecef4-123">This is your subscription key.</span></span> <span data-ttu-id="ecef4-124">Kopieren Sie den Schlüssel, damit Sie ihn später beim Aufrufen der API verwenden können.</span><span class="sxs-lookup"><span data-stu-id="ecef4-124">Copy the key so you can use it later when you call the API.</span></span>

<span id="call-the-api" />

## <a name="call-the-api"></a><span data-ttu-id="ecef4-125">Aufrufen der API</span><span class="sxs-lookup"><span data-stu-id="ecef4-125">Call the API</span></span>

<span data-ttu-id="ecef4-126">Nachdem Sie über Ihren Abonnementschlüssel verfügen, können Sie die API mithilfe von HTTP-REST-Syntax in der Programmiersprache Ihrer Wahl aufrufen.</span><span class="sxs-lookup"><span data-stu-id="ecef4-126">After you have your subscription key, you are ready to call the API using HTTP REST syntax from the programming language of your choice.</span></span> <span data-ttu-id="ecef4-127">Informationen zur Syntax der API finden Sie im Abschnitt [API-Syntax](#syntax) weiter unten.</span><span class="sxs-lookup"><span data-stu-id="ecef4-127">For information about the syntax of the API, see the [API syntax](#syntax) section below.</span></span> <span data-ttu-id="ecef4-128">Um Codebeispiele in C#, JavaScript, Python und einigen anderen Programmiersprachen anzuzeigen, klicken Sie im Portal für die App-Metadaten-API auf die Registerkarte **APIs** und auf **App-Details**. Am unteren Seitenrand ist der Abschnitt **Codebeispiele** zu sehen.</span><span class="sxs-lookup"><span data-stu-id="ecef4-128">To see code examples in C#, JavaScript, Python, and several other languages, click the **APIs** tab of the app metadata API portal, click **App details**, and then see the **Code samples** section on the bottom of the page.</span></span>

<span data-ttu-id="ecef4-129">Alternativ können Sie die API über die Benutzeroberfläche aufrufen, die vom Portal für die App-Metadaten-API bereitgestellt wird:</span><span class="sxs-lookup"><span data-stu-id="ecef4-129">Alternatively, you can call the API using the UI provided by the app metadata API portal:</span></span>
  1. <span data-ttu-id="ecef4-130">Klicken Sie im Portal auf die Registerkarte **APIs** und dann auf **App-Details**.</span><span class="sxs-lookup"><span data-stu-id="ecef4-130">In the portal, click the **APIs** tab and then click **App details**.</span></span>
  2. <span data-ttu-id="ecef4-131">Geben Sie auf der folgenden Seite die [app_id](#request-parameters) der App, für die Metadaten abgerufen werden sollen, in das Feld **app_id** und Ihren Abonnementschlüssel in das Feld **Ocp_Apim_Subscription-Key** ein.</span><span class="sxs-lookup"><span data-stu-id="ecef4-131">On the following page, enter the [app_id](#request-parameters) of the app for which you want to retrieve metadata in the **app_id** field and enter your subscription key in the **Ocp_Apim_Subscription-Key** field.</span></span>
  3. <span data-ttu-id="ecef4-132">Klicken Sie auf **Senden**.</span><span class="sxs-lookup"><span data-stu-id="ecef4-132">Click **Send**.</span></span> <span data-ttu-id="ecef4-133">Die Antwort wird unten auf der Seite angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ecef4-133">The response appears at the bottom of the page.</span></span>


<span id="syntax" />

## <a name="api-syntax"></a><span data-ttu-id="ecef4-134">API-Syntax</span><span class="sxs-lookup"><span data-stu-id="ecef4-134">API syntax</span></span>

<span data-ttu-id="ecef4-135">Diese Methode hat die folgende Anforderungssyntax.</span><span class="sxs-lookup"><span data-stu-id="ecef4-135">This method has the following request syntax.</span></span>

| <span data-ttu-id="ecef4-136">Methode</span><span class="sxs-lookup"><span data-stu-id="ecef4-136">Method</span></span> | <span data-ttu-id="ecef4-137">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="ecef4-137">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="ecef4-138">GET</span><span class="sxs-lookup"><span data-stu-id="ecef4-138">GET</span></span>   | ```https://admetadata.azure-api.net/v1/app/{app_id}``` |

<span/>
 

### <a name="request-header"></a><span data-ttu-id="ecef4-139">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="ecef4-139">Request header</span></span>

| <span data-ttu-id="ecef4-140">Header</span><span class="sxs-lookup"><span data-stu-id="ecef4-140">Header</span></span>        | <span data-ttu-id="ecef4-141">Typ</span><span class="sxs-lookup"><span data-stu-id="ecef4-141">Type</span></span>   | <span data-ttu-id="ecef4-142">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ecef4-142">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="ecef4-143">Ocp-Apim-Subscription-Key</span><span class="sxs-lookup"><span data-stu-id="ecef4-143">Ocp-Apim-Subscription-Key</span></span> | <span data-ttu-id="ecef4-144">String</span><span class="sxs-lookup"><span data-stu-id="ecef4-144">string</span></span> | <span data-ttu-id="ecef4-145">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="ecef4-145">Required.</span></span> <span data-ttu-id="ecef4-146">Der Abonnementschlüssel, den Sie aus dem [Portal für die App-Metadaten-API abgerufen haben](#get-key).</span><span class="sxs-lookup"><span data-stu-id="ecef4-146">The subscription key that you [retrieved from the app metadata API portal](#get-key).</span></span>  |

<span/>

### <a name="request-parameters"></a><span data-ttu-id="ecef4-147">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="ecef4-147">Request parameters</span></span>

| <span data-ttu-id="ecef4-148">Name</span><span class="sxs-lookup"><span data-stu-id="ecef4-148">Name</span></span>        | <span data-ttu-id="ecef4-149">Typ</span><span class="sxs-lookup"><span data-stu-id="ecef4-149">Type</span></span>   | <span data-ttu-id="ecef4-150">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ecef4-150">Description</span></span>                                                                 |
|---------------|--------|-----------------------|
| <span data-ttu-id="ecef4-151">app_id</span><span class="sxs-lookup"><span data-stu-id="ecef4-151">app_id</span></span> | <span data-ttu-id="ecef4-152">String</span><span class="sxs-lookup"><span data-stu-id="ecef4-152">string</span></span> | <span data-ttu-id="ecef4-153">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="ecef4-153">Required.</span></span> <span data-ttu-id="ecef4-154">Die ID der App, für die Sie Metadaten abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="ecef4-154">The ID of the app for which you want retrieve metadata.</span></span> <span data-ttu-id="ecef4-155">Folgende Werte sind möglich:</span><span class="sxs-lookup"><span data-stu-id="ecef4-155">This can be one of the following values:</span></span><br/><br/><ul><li><span data-ttu-id="ecef4-156">Die Store-ID für die App.</span><span class="sxs-lookup"><span data-stu-id="ecef4-156">The Store ID for the app.</span></span> <span data-ttu-id="ecef4-157">Beispiel für eine Store-ID: 9NBLGGH29DM8.</span><span class="sxs-lookup"><span data-stu-id="ecef4-157">An example Store ID is 9NBLGGH29DM8.</span></span></li><li><span data-ttu-id="ecef4-158">Die Produkt-ID (manchmal auch als *App-ID* bezeichnet) für eine App, die ursprünglich für Windows8.x oder Windows Phone8.x erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="ecef4-158">The Product ID (also sometimes called the *app ID*) for an app that was originally built for Windows 8.x or Windows Phone 8.x.</span></span> <span data-ttu-id="ecef4-159">Die Produkt-ID ist eine GUID.</span><span class="sxs-lookup"><span data-stu-id="ecef4-159">The Product ID is a GUID.</span></span></li></ul> |

<span/>

### <a name="request-example"></a><span data-ttu-id="ecef4-160">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="ecef4-160">Request example</span></span>

<span data-ttu-id="ecef4-161">Im folgenden Beispiel wird veranschaulicht, wie Metadaten für eine App mit der Store-ID 9NBLGGH29DM8 abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="ecef4-161">The following example demonstrates how to retrieve metadata for an app that has the Store ID 9NBLGGH29DM8.</span></span>

```syntax
GET https://admetadata.azure-api.net/v1/app/9NBLGGH29DM8 HTTP/1.1
Ocp-Apim-Subscription-Key: <subscription key>
```

### <a name="response-body"></a><span data-ttu-id="ecef4-162">Antworttext</span><span class="sxs-lookup"><span data-stu-id="ecef4-162">Response body</span></span>

<span data-ttu-id="ecef4-163">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="ecef4-163">The following example demonstrates the JSON response body for a successful call to this method.</span></span>

```json
{
    "storeId":"9NBLGGH29DM8",
    "name":"Contoso Sports App",
    "description":"Catch the latest scores and replays using Contoso Sports App!",
    "phoneStoreGuid":"920217d7-90da-4019-99e8-46e4a6bd2594",
    "windowsStoreGuid":"d7e982e7-fbf3-42b5-9dad-72b65bd4e248",
    "storeCategory":"Sports",
    "iabCategory":"Sports",
    "iabCategoryId":"IAB17",
    "coppa":false,
    "downloadUrl":"https://www.microsoft.com/store/apps/9nblggh29dm8",
    "isLive":true,
    "iconUrls":[
      "//store-images.microsoft.com/image/apps.15753.13510798883747357.b6981489-6fdd-4fec-b655-a822247d5a76.33529096-a723-4204-9da9-a5dd8b328d4e"
    ],
    "type":"App",
    "devices":[
      "PC",
      "Phone"
    ],
    "platformVersions":[
      "Windows.Universal"
    ],
    "screenshotUrls":[
      "//store-images.microsoft.com/image/apps.15901.19810723133740207.c9781069-6fef-5fba-a055-c922051d59b6.40129896-d083-5604-ab79-aba68bfa084f"
    ]
}
```

<span data-ttu-id="ecef4-164">Weitere Informationen zu den Werten im Antworttext finden Sie in der folgenden Tabelle.</span><span class="sxs-lookup"><span data-stu-id="ecef4-164">For more details about the values in the response body, see the following table.</span></span>

| <span data-ttu-id="ecef4-165">Wert</span><span class="sxs-lookup"><span data-stu-id="ecef4-165">Value</span></span>      | <span data-ttu-id="ecef4-166">Typ</span><span class="sxs-lookup"><span data-stu-id="ecef4-166">Type</span></span>   | <span data-ttu-id="ecef4-167">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ecef4-167">Description</span></span>    |
|------------|--------|--------------------|
| <span data-ttu-id="ecef4-168">storeId</span><span class="sxs-lookup"><span data-stu-id="ecef4-168">storeId</span></span>           | <span data-ttu-id="ecef4-169">String</span><span class="sxs-lookup"><span data-stu-id="ecef4-169">string</span></span>  | <span data-ttu-id="ecef4-170">Die Store-ID der App.</span><span class="sxs-lookup"><span data-stu-id="ecef4-170">The Store ID of the app.</span></span> <span data-ttu-id="ecef4-171">Beispiel für eine Store-ID: 9NBLGGH29DM8.</span><span class="sxs-lookup"><span data-stu-id="ecef4-171">An example Store ID is 9NBLGGH29DM8.</span></span>     |  
| <span data-ttu-id="ecef4-172">name</span><span class="sxs-lookup"><span data-stu-id="ecef4-172">name</span></span>           | <span data-ttu-id="ecef4-173">String</span><span class="sxs-lookup"><span data-stu-id="ecef4-173">string</span></span>  | <span data-ttu-id="ecef4-174">Der Name der App.</span><span class="sxs-lookup"><span data-stu-id="ecef4-174">The name of the app.</span></span>   |
| <span data-ttu-id="ecef4-175">description</span><span class="sxs-lookup"><span data-stu-id="ecef4-175">description</span></span>           | <span data-ttu-id="ecef4-176">String</span><span class="sxs-lookup"><span data-stu-id="ecef4-176">string</span></span>  | <span data-ttu-id="ecef4-177">Die Beschreibung aus dem Store-Eintrag für die App.</span><span class="sxs-lookup"><span data-stu-id="ecef4-177">The description from the Store listing for the app.</span></span>  |
| <span data-ttu-id="ecef4-178">phoneStoreGuid</span><span class="sxs-lookup"><span data-stu-id="ecef4-178">phoneStoreGuid</span></span>           | <span data-ttu-id="ecef4-179">String</span><span class="sxs-lookup"><span data-stu-id="ecef4-179">string</span></span>  | <span data-ttu-id="ecef4-180">Die Produkt-ID (Windows Phone8.x) für die App.</span><span class="sxs-lookup"><span data-stu-id="ecef4-180">The Product ID (Windows Phone 8.x) for the app.</span></span> <span data-ttu-id="ecef4-181">Dies ist eine GUID.</span><span class="sxs-lookup"><span data-stu-id="ecef4-181">This is a GUID.</span></span>  |
| <span data-ttu-id="ecef4-182">windowsStoreGuid</span><span class="sxs-lookup"><span data-stu-id="ecef4-182">windowsStoreGuid</span></span>           | <span data-ttu-id="ecef4-183">String</span><span class="sxs-lookup"><span data-stu-id="ecef4-183">string</span></span>  | <span data-ttu-id="ecef4-184">Die Produkt-ID (Windows8.x) für die App.</span><span class="sxs-lookup"><span data-stu-id="ecef4-184">The Product ID (Windows 8.x) for the app.</span></span> <span data-ttu-id="ecef4-185">Dies ist eine GUID.</span><span class="sxs-lookup"><span data-stu-id="ecef4-185">This is a GUID.</span></span> |
| <span data-ttu-id="ecef4-186">storeCategory</span><span class="sxs-lookup"><span data-stu-id="ecef4-186">storeCategory</span></span>           | <span data-ttu-id="ecef4-187">String</span><span class="sxs-lookup"><span data-stu-id="ecef4-187">string</span></span>  | <span data-ttu-id="ecef4-188">Die Kategorie für die App im Store.</span><span class="sxs-lookup"><span data-stu-id="ecef4-188">The category for the app in the Store.</span></span> <span data-ttu-id="ecef4-189">Die unterstützten Werte finden Sie in der [Kategorie- und Unterkategorietabelle](../publish/category-and-subcategory-table.md) für Apps im Store.</span><span class="sxs-lookup"><span data-stu-id="ecef4-189">For the supported values, see the [category and subcategory table](../publish/category-and-subcategory-table.md) for apps in the Store.</span></span>  |
| <span data-ttu-id="ecef4-190">iabCategory</span><span class="sxs-lookup"><span data-stu-id="ecef4-190">iabCategory</span></span>           | <span data-ttu-id="ecef4-191">String</span><span class="sxs-lookup"><span data-stu-id="ecef4-191">string</span></span>  | <span data-ttu-id="ecef4-192">Die Inhaltskategorie für die App gemäß Definition des Interactive Advertising Bureau (IAB).</span><span class="sxs-lookup"><span data-stu-id="ecef4-192">The content category for the app as defined by the Interactive Advertising Bureau (IAB).</span></span> <span data-ttu-id="ecef4-193">Beispielsweise **Nachrichten** oder **Sport**.</span><span class="sxs-lookup"><span data-stu-id="ecef4-193">For example, **News** or **Sports**.</span></span> <span data-ttu-id="ecef4-194">Eine Liste der Inhaltskategorien finden Sie auf der Seite [IAB Tech Lab Content Taxonomy](https://www.iab.com/guidelines/iab-quality-assurance-guidelines-qag-taxonomy) der IAB-Website.</span><span class="sxs-lookup"><span data-stu-id="ecef4-194">For a list of content categories, see the [IAB Tech Lab Content Taxonomy](https://www.iab.com/guidelines/iab-quality-assurance-guidelines-qag-taxonomy) page on the IAB web site.</span></span>   |
| <span data-ttu-id="ecef4-195">iabCategoryId</span><span class="sxs-lookup"><span data-stu-id="ecef4-195">iabCategoryId</span></span>           | <span data-ttu-id="ecef4-196">String</span><span class="sxs-lookup"><span data-stu-id="ecef4-196">string</span></span>  | <span data-ttu-id="ecef4-197">Die ID der Inhaltskategorie für die App.</span><span class="sxs-lookup"><span data-stu-id="ecef4-197">The ID of the content category for the app.</span></span> <span data-ttu-id="ecef4-198">**IAB12** ist beispielsweise die ID für die Nachrichtenkategorie und **IAB17** die ID für die Sportkategorie.</span><span class="sxs-lookup"><span data-stu-id="ecef4-198">For example, **IAB12** is the ID for the News category, and **IAB17** is the ID for the Sports category.</span></span> <span data-ttu-id="ecef4-199">Eine Liste der IDs für Inhaltskategorien finden Sie in Abschnitt 5.1 der [OpenRTB API Specification](http://www.iab.com/wp-content/uploads/2015/05/OpenRTB_API_Specification_Version_2_3_1.pdf).</span><span class="sxs-lookup"><span data-stu-id="ecef4-199">For a list of content category IDs, see section 5.1 in the [OpenRTB API Specification](http://www.iab.com/wp-content/uploads/2015/05/OpenRTB_API_Specification_Version_2_3_1.pdf).</span></span> |
| <span data-ttu-id="ecef4-200">coppa</span><span class="sxs-lookup"><span data-stu-id="ecef4-200">coppa</span></span>           | <span data-ttu-id="ecef4-201">Boolesch</span><span class="sxs-lookup"><span data-stu-id="ecef4-201">Boolean</span></span>  | <span data-ttu-id="ecef4-202">„True“, wenn sich die App an Kinder unter 13Jahren richtet und daher bestimmten Anforderungen gemäß dem Children's Online Privacy Protection Act („COPPA“) unterliegt; andernfalls „False“.</span><span class="sxs-lookup"><span data-stu-id="ecef4-202">True if the app is directed at children under the age of 13 and therefore has obligations under the Children's Online Privacy Protection Act (COPPA); otherwise, false.</span></span>  |
| <span data-ttu-id="ecef4-203">downloadUrl</span><span class="sxs-lookup"><span data-stu-id="ecef4-203">downloadUrl</span></span>           | <span data-ttu-id="ecef4-204">String</span><span class="sxs-lookup"><span data-stu-id="ecef4-204">string</span></span>  | <span data-ttu-id="ecef4-205">Der Link zum App-Eintrag im Store.</span><span class="sxs-lookup"><span data-stu-id="ecef4-205">The link to the app's listing in the Store.</span></span> <span data-ttu-id="ecef4-206">Dieser Link hat das Format ```https://www.microsoft.com/store/apps/<Store ID>```.</span><span class="sxs-lookup"><span data-stu-id="ecef4-206">This link is in the format ```https://www.microsoft.com/store/apps/<Store ID>```.</span></span>  |
| <span data-ttu-id="ecef4-207">isLive</span><span class="sxs-lookup"><span data-stu-id="ecef4-207">isLive</span></span>           | <span data-ttu-id="ecef4-208">Boolesch</span><span class="sxs-lookup"><span data-stu-id="ecef4-208">Boolean</span></span>  | <span data-ttu-id="ecef4-209">„True“, wenn die App im Store derzeit verfügbar ist. Andernfalls „false“.</span><span class="sxs-lookup"><span data-stu-id="ecef4-209">True if the app is currently available in the Store; otherwise, false.</span></span>  |
| <span data-ttu-id="ecef4-210">iconUrls</span><span class="sxs-lookup"><span data-stu-id="ecef4-210">iconUrls</span></span>           | <span data-ttu-id="ecef4-211">Array</span><span class="sxs-lookup"><span data-stu-id="ecef4-211">array</span></span>  |  <span data-ttu-id="ecef4-212">Ein Array von einer oder mehreren Zeichenfolgen, die die relativen Pfade zu den Symbol-URLs enthalten, die der App zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="ecef4-212">An array of one or more strings that contain the relative paths to the icon URLs associated with the app.</span></span> <span data-ttu-id="ecef4-213">Um die Symbole abzurufen, stellen Sie den URLs *http* oder *https* voran.</span><span class="sxs-lookup"><span data-stu-id="ecef4-213">To retrieve the icons, prepend *http* or *https* to the URLs.</span></span>  |
| <span data-ttu-id="ecef4-214">type</span><span class="sxs-lookup"><span data-stu-id="ecef4-214">type</span></span>           | <span data-ttu-id="ecef4-215">String</span><span class="sxs-lookup"><span data-stu-id="ecef4-215">string</span></span>  | <span data-ttu-id="ecef4-216">Eine der folgenden Zeichenfolgen: **App** oder **Game**.</span><span class="sxs-lookup"><span data-stu-id="ecef4-216">One of the following strings: **App** or **Game**.</span></span>  |
| <span data-ttu-id="ecef4-217">Geräte</span><span class="sxs-lookup"><span data-stu-id="ecef4-217">devices</span></span>           |  <span data-ttu-id="ecef4-218">Array</span><span class="sxs-lookup"><span data-stu-id="ecef4-218">array</span></span>  | <span data-ttu-id="ecef4-219">Ein Array von einer oder mehreren der folgenden Zeichenfolgen, die die Gerätetypen angeben, die die App unterstützt: **PC**, **Telefon**, **Xbox**, **IoT**, **Server** und **Hologramm**.</span><span class="sxs-lookup"><span data-stu-id="ecef4-219">An array of one or more of the following strings that specify the device types that the app supports: **PC**, **Phone**, **Xbox**, **IoT**, **Server**, and **Holographic**.</span></span>  |
| <span data-ttu-id="ecef4-220">platformVersions</span><span class="sxs-lookup"><span data-stu-id="ecef4-220">platformVersions</span></span>           | <span data-ttu-id="ecef4-221">Array</span><span class="sxs-lookup"><span data-stu-id="ecef4-221">array</span></span>  |  <span data-ttu-id="ecef4-222">Ein Array von einer oder mehreren der folgenden Zeichenfolgen, die die Plattform angeben, die die App unterstützt: **Windows.Universal**, **Windows.Windows8x** und **Windows.WindowsPhone8x**.</span><span class="sxs-lookup"><span data-stu-id="ecef4-222">An array of one or more of the following strings that specify the platforms that the app supports: **Windows.Universal**, **Windows.Windows8x**, and **Windows.WindowsPhone8x**.</span></span>  |
| <span data-ttu-id="ecef4-223">screenshotUrls</span><span class="sxs-lookup"><span data-stu-id="ecef4-223">screenshotUrls</span></span>           | <span data-ttu-id="ecef4-224">Array</span><span class="sxs-lookup"><span data-stu-id="ecef4-224">array</span></span>  | <span data-ttu-id="ecef4-225">Ein Array von einer oder mehreren Zeichenfolgen, die die relativen Pfade zu den Screenshot-URLs für diese App enthalten.</span><span class="sxs-lookup"><span data-stu-id="ecef4-225">An array of one or more strings that contain the relative paths to the screenshot URLs for this app.</span></span> <span data-ttu-id="ecef4-226">Um die Screenshots abzurufen, stellen Sie den URLs *http* oder *https* voran.</span><span class="sxs-lookup"><span data-stu-id="ecef4-226">To retrieve the screenshots, prepend *http* or *https* to the URLs.</span></span>  |

<span/>



 

 
