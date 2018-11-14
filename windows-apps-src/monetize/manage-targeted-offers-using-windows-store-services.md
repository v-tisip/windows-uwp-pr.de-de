---
author: Xansky
ms.assetid: 9F0A59A1-FAD7-4AD5-B78B-C1280F215D23
description: Verwenden Sie die Microsoft Store-API für gezielte Angebote, um die gezielten Angebote abzurufen, die für den aktuellen Benutzer Ihrer App verfügbar sind.
title: Verwalten von gezielten Angeboten mithilfe von Store-Diensten
ms.author: mhopkins
ms.date: 10/10/2017
ms.topic: article
keywords: Windows10, UWP, Store-Dienste, Microsoft Store-API für gezielte Angebote, gezielte Angebote
ms.localizationpriority: medium
ms.openlocfilehash: dbfefefdb7f7b96dbe99b35656b610b393ab3afa
ms.sourcegitcommit: f2c9a050a9137a473f28b613968d5782866142c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2018
ms.locfileid: "6260365"
---
# <a name="manage-targeted-offers-using-store-services"></a><span data-ttu-id="e3493-104">Verwalten von gezielten Angeboten mithilfe von Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="e3493-104">Manage targeted offers using Store services</span></span>

<span data-ttu-id="e3493-105">Wenn Sie ein *gezieltes Angebot* in Erstellen der **einbeziehen > zielgerichtete Angebote** Seite für Ihre app im Partner Center verwenden, die der *Microsoft Store für gezielte Angebote API* in Ihrem app Code zum Abrufen von Informationen, die Ihnen bei der Implementierung der in-app-Umgebung für die Gezieltes Angebot.</span><span class="sxs-lookup"><span data-stu-id="e3493-105">If you create a *targeted offer* in the **Engage > Targeted offers** page for your app in Partner Center, use the *Microsoft Store targeted offers API* in your app's code to retrieve info that helps you implement the in-app experience for the targeted offer.</span></span> <span data-ttu-id="e3493-106">Weitere Informationen zu gezielten Angeboten und Anleitungen zu deren Erstellung im Dashboard finden Sie unter [Verwenden Sie gezielte Angebote, um Interaktionen und Abschlüsse zu maximieren.](../publish/use-targeted-offers-to-maximize-engagement-and-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="e3493-106">For more information about targeted offers and how to create them in the dashboard, see [Use targeted offers to maximize engagement and conversions](../publish/use-targeted-offers-to-maximize-engagement-and-conversions.md).</span></span>

<span data-ttu-id="e3493-107">Die Gezielte-Angebote-API ist eine einfache REST-API, mit der Sie gezielte Angebote abrufen können, die für den aktuellen Benutzer verfügbar sind– basierend darauf, ob der Benutzer zum Kundensegment für das gezielte Angebot gehört.</span><span class="sxs-lookup"><span data-stu-id="e3493-107">The targeted offers API is a simple REST API that you can use to get the targeted offers that are available for the current user, based on whether or not the user is part of the customer segment for the targeted offer.</span></span> <span data-ttu-id="e3493-108">Gehen Sie folgendermaßen vor, um diese API in Ihrem App-Code zu verwenden:</span><span class="sxs-lookup"><span data-stu-id="e3493-108">To use this API in your app's code, follow these steps:</span></span>

1.  <span data-ttu-id="e3493-109">[Rufen Sie ein Microsoft-Kontotoken](#obtain-a-microsoft-account-token) für den aktuell angemeldeten Benutzer Ihrer App ab.</span><span class="sxs-lookup"><span data-stu-id="e3493-109">[Get a Microsoft Account token](#obtain-a-microsoft-account-token) for the current signed-in user of your app.</span></span>
2.  <span data-ttu-id="e3493-110">[Rufen Sie die gezielten Angebote für den aktuellen Benutzer ab](#get-targeted-offers).</span><span class="sxs-lookup"><span data-stu-id="e3493-110">[Get the targeted offers for the current user](#get-targeted-offers).</span></span>
3.  <span data-ttu-id="e3493-111">Implementieren Sie die In-App-Kaufumgebung für das Add-On, das einem der gezielten Angebote zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="e3493-111">Implement the in-app purchase experience for the add-on that is associated with one of the targeted offers.</span></span> <span data-ttu-id="e3493-112">Weitere Informationen zur Implementierung von In-App-Käufen finden Sie in [diesem Artikel](enable-in-app-purchases-of-apps-and-add-ons.md).</span><span class="sxs-lookup"><span data-stu-id="e3493-112">For more information about implementing in-app purchases, see [this article](enable-in-app-purchases-of-apps-and-add-ons.md).</span></span>

<span data-ttu-id="e3493-113">Ein vollständiges Codebeispiel, das alle diese Schritteveranschaulicht, finden Sie unter der [Codebeispiel](#code-example) am Ende dieses Artikels.</span><span class="sxs-lookup"><span data-stu-id="e3493-113">For a complete code example that demonstrates all of these steps, see the [code example](#code-example) at the end of this article.</span></span> <span data-ttu-id="e3493-114">Die folgenden Abschnitte enthalten weitere Details zu den einzelnen Schritten.</span><span class="sxs-lookup"><span data-stu-id="e3493-114">The following sections provide more details about each step.</span></span>

<span id="obtain-a-microsoft-account-token" />

## <a name="get-a-microsoft-account-token-for-the-current-user"></a><span data-ttu-id="e3493-115">Abrufen eines Microsoft-Kontotokens für den aktuellen Benutzer</span><span class="sxs-lookup"><span data-stu-id="e3493-115">Get a Microsoft Account token for the current user</span></span>

<span data-ttu-id="e3493-116">Rufen Sie in Ihrem App-Code ein Microsoft-Konto (MSA)-Token für den aktuell angemeldeten Benutzer ab.</span><span class="sxs-lookup"><span data-stu-id="e3493-116">In your app's code, get a Microsoft Account (MSA) token for the current signed-in user.</span></span> <span data-ttu-id="e3493-117">Sie müssen dieses Token im ```Authorization```-Anforderungsheader für jede Methode in der Microsoft Store-API für gezielte Angebote übergeben.</span><span class="sxs-lookup"><span data-stu-id="e3493-117">You must pass this token in the ```Authorization``` request header for the Microsoft Store targeted offers API.</span></span> <span data-ttu-id="e3493-118">Dieses Token wird vom Store verwendet, um die gezielten Angebote abzurufen, die für den aktuellen Benutzer verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="e3493-118">This token is used by the Store to retrieve the targeted offers that are available for the current user.</span></span>

<span data-ttu-id="e3493-119">Um das MSA-Token abzurufen, verwenden Sie die [WebAuthenticationCoreManager](https://docs.microsoft.com/uwp/api/windows.security.authentication.web.core.webauthenticationcoremanager)-Klasse, um ein Token unter Angabe des Bereichs anzufordern ```devcenter_implicit.basic,wl.basic```.</span><span class="sxs-lookup"><span data-stu-id="e3493-119">To get the MSA token, use the [WebAuthenticationCoreManager](https://docs.microsoft.com/uwp/api/windows.security.authentication.web.core.webauthenticationcoremanager) class to request a token using the scope ```devcenter_implicit.basic,wl.basic```.</span></span> <span data-ttu-id="e3493-120">Das folgende Beispiel veranschaulicht die Vorgehensweise.</span><span class="sxs-lookup"><span data-stu-id="e3493-120">The following example demonstrates how to do this.</span></span> <span data-ttu-id="e3493-121">In diesem Beispiel wird ein Auszug aus dem [vollständige Beispiel](#code-example) verwendet. Es erfordert **using**-Anweisungen, die im vollständigen Beispiel bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="e3493-121">This example is an excerpt from the [complete example](#code-example), and it requires **using** statements that are provided in the complete example.</span></span>

[!code-cs[TargetedOffers](./code/StoreServicesExamples_TargetedOffers/cs/TargetedOffers.cs#GetMSAToken)]

<span data-ttu-id="e3493-122">Weitere Informationen zum Abrufen von MSA-Token finden Sie unter [Web Account Manager](../security/web-account-manager.md).</span><span class="sxs-lookup"><span data-stu-id="e3493-122">For more information about getting MSA tokens, see [Web account manager](../security/web-account-manager.md).</span></span>

<span id="get-targeted-offers" />

## <a name="get-the-targeted-offers-for-the-current-user"></a><span data-ttu-id="e3493-123">Abrufen der gezielten Angebote für den aktuellen Benutzer</span><span class="sxs-lookup"><span data-stu-id="e3493-123">Get the targeted offers for the current user</span></span>

<span data-ttu-id="e3493-124">Rufen Sie nach Erhalt des MSA-Tokens für den aktuellen Benutzer die GET-Methode zum ```https://manage.devcenter.microsoft.com/v2.0/my/storeoffers/user```-URI auf, um die für den aktuellen Benutzer verfügbaren Angebote abzurufen.</span><span class="sxs-lookup"><span data-stu-id="e3493-124">After you have an MSA token for the current user, call the GET method of the ```https://manage.devcenter.microsoft.com/v2.0/my/storeoffers/user``` URI to get the available targeted offers for the current user.</span></span> <span data-ttu-id="e3493-125">Weitere Informationen zu dieser REST-Methode finden Sie unter [Abrufen gezielter Angebote](get-targeted-offers.md).</span><span class="sxs-lookup"><span data-stu-id="e3493-125">For more information about this REST method, see [Get targeted offers](get-targeted-offers.md).</span></span>

<span data-ttu-id="e3493-126">Bei dieser Methode wird ein Array mit Produkt-IDs für die Add-Ons zurückgegeben, die den gezielten Angeboten zugeordnet sind, die für den aktuellen Benutzer verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="e3493-126">This method returns the product IDs of the add-ons that that are associated with the targeted offers that are available for the current user.</span></span> <span data-ttu-id="e3493-127">Mit diesen Informationen können Sie ein oder mehrere gezielte Angebote als In-App-Einkauf für den Benutzer erstellen.</span><span class="sxs-lookup"><span data-stu-id="e3493-127">With this information, you can offer one or more of the targeted offers as an in-app purchase to the user.</span></span>

<span data-ttu-id="e3493-128">Das folgende Beispiel zeigt, wie Sie die gezielten Angebote für den aktuellen Benutzer abrufen.</span><span class="sxs-lookup"><span data-stu-id="e3493-128">The following example demonstrates how to get the targeted offers for the current user.</span></span> <span data-ttu-id="e3493-129">Dieses Beispiel ist ein Auszug aus dem [vollständige Beispiel](#code-example).</span><span class="sxs-lookup"><span data-stu-id="e3493-129">This example is an excerpt from the [complete example](#code-example).</span></span> <span data-ttu-id="e3493-130">Erfordert die [Json.NET](http://www.newtonsoft.com/json)-Bibliothek von Newtonsoft und zusätzliche Klassen und **using**-Anweisungen, die im vollständigen Beispiel bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="e3493-130">It requires the [Json.NET](http://www.newtonsoft.com/json) library from Newtonsoft and additional classes and **using** statements that are provided in the complete example.</span></span>

[!code-cs[TargetedOffers](./code/StoreServicesExamples_TargetedOffers/cs/TargetedOffers.cs#GetTargetedOffers)]

<span id="code-example" />

## <a name="complete-code-example"></a><span data-ttu-id="e3493-131">Vollständiger Beispielcode</span><span class="sxs-lookup"><span data-stu-id="e3493-131">Complete code example</span></span>

<span data-ttu-id="e3493-132">Das folgende Codebeispiel veranschaulicht die folgenden Aufgaben:</span><span class="sxs-lookup"><span data-stu-id="e3493-132">The following code example demonstrates the following tasks:</span></span>

* <span data-ttu-id="e3493-133">Abrufen eines MSA-Tokens für den aktuellen Benutzer</span><span class="sxs-lookup"><span data-stu-id="e3493-133">Get an MSA token for the current user.</span></span>
* <span data-ttu-id="e3493-134">Abrufen aller gezielten Angebote für den aktuellen Benutzer mithilfe der Methode zum [Abrufen gezielter Angebote](get-targeted-offers.md)</span><span class="sxs-lookup"><span data-stu-id="e3493-134">Get all of the targeted offers for the current user by using the [Get targeted offers](get-targeted-offers.md) method.</span></span>
* <span data-ttu-id="e3493-135">Kaufen Sie das Add-On, das mit einem gezielten Angebot verknüpft ist.</span><span class="sxs-lookup"><span data-stu-id="e3493-135">Purchase the add-on that is associated with a targeted offer.</span></span>

<span data-ttu-id="e3493-136">Dieses Beispiel erfordert die [Json.NET](http://www.newtonsoft.com/json)-Bibliothek von Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="e3493-136">This example requires the [Json.NET](http://www.newtonsoft.com/json) library from Newtonsoft.</span></span> <span data-ttu-id="e3493-137">Im Beispiel wird diese Bibliothek verwendet, um Daten im JSON-Format zu serialisieren bzw. deserialisieren.</span><span class="sxs-lookup"><span data-stu-id="e3493-137">The example uses this library to serialize and deserialize JSON-formatted data.</span></span>

[!code-cs[TargetedOffers](./code/StoreServicesExamples_TargetedOffers/cs/TargetedOffers.cs#GetTargetedOffersSample)]

## <a name="related-topics"></a><span data-ttu-id="e3493-138">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="e3493-138">Related topics</span></span>

* [<span data-ttu-id="e3493-139">Verwenden Sie zielgerichtete Angebote, um Interaktionen und Abschlüsse zu maximieren.</span><span class="sxs-lookup"><span data-stu-id="e3493-139">Use targeted offers to maximize engagement and conversions</span></span>](../publish/use-targeted-offers-to-maximize-engagement-and-conversions.md)
* [<span data-ttu-id="e3493-140">Abrufen gezielter Angebote</span><span class="sxs-lookup"><span data-stu-id="e3493-140">Get targeted offers</span></span>](get-targeted-offers.md)
