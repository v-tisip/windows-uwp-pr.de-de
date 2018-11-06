---
author: Xansky
ms.assetid: bb105fbe-bbbd-4d78-899b-345af2757720
description: Erfahren Sie, wie-ID und anzeigeneinheits-IDs für Ihre app aus dem Partner Center hinzufügen, bevor Sie Ihre app an den Store übermitteln.
title: Einrichten von Anzeigeneinheiten in der App
ms.author: mhopkins
ms.date: 05/11/2018
ms.topic: article
keywords: Windows 10, UWP, Anzeigen, Werbung, Anzeigeeinheiten, Test
ms.localizationpriority: medium
ms.openlocfilehash: 11c66756d95e041a45fbc075b02eb744bf542871
ms.sourcegitcommit: e814a13978f33654d8e995584f4b047cb53e0aef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "6045480"
---
# <a name="set-up-ad-units-in-your-app"></a><span data-ttu-id="5b13e-104">Einrichten von Anzeigeneinheiten in der App</span><span class="sxs-lookup"><span data-stu-id="5b13e-104">Set up ad units in your app</span></span>

<span data-ttu-id="5b13e-105">Jedes Steuerelement für eine universelle Windows Platform (UWP) in Ihrer App verfügt über eine entsprechende *Anzeigeneinheit*. Diese wird von unseren Diensten verwendet, um Werbung auf das Steuerelement zu leiten.</span><span class="sxs-lookup"><span data-stu-id="5b13e-105">Every ad control in your Universal Windows Platform (UWP) app has a corresponding *ad unit* that is used by our services to serve ads to the control.</span></span> <span data-ttu-id="5b13e-106">Jede Anzeigeneinheit besteht aus einer *Anzeigeneinheits-ID* und *Anwendungs-ID*, die Sie Code in Ihrer App zuweisen müssen.</span><span class="sxs-lookup"><span data-stu-id="5b13e-106">Each ad unit consists of an *ad unit ID* and *application ID* that you must assign to code in your app.</span></span>

<span data-ttu-id="5b13e-107">Wir bieten [Testanzeigen-Einheitenwerte](#test-ad-units), die Sie während der Testphase verwenden können, um sicherzustellen, dass Ihre App Testanzeigen anzeigt.</span><span class="sxs-lookup"><span data-stu-id="5b13e-107">We provide [test ad unit values](#test-ad-units) that you can use during testing to confirm that your app shows test ads.</span></span> <span data-ttu-id="5b13e-108">Diese Testwerte können nur in einer Testversion Ihrer App verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="5b13e-108">These test values can only be used in a test version of your app.</span></span> <span data-ttu-id="5b13e-109">Wenn Sie Testwerte in einer veröffentlichten App verwenden, wird die App keine Livewerbung empfangen.</span><span class="sxs-lookup"><span data-stu-id="5b13e-109">If you try to use test values in your app after you publish it, your live app not receive ads.</span></span>

<span data-ttu-id="5b13e-110">Nachdem Sie Ihre UWP-app getestet haben und Sie bereit sind, die sie in das Partner Center zu übermitteln, müssen über eine Seite [In-app-anzeigen](../publish/in-app-ads.md) in Partner Center [eine liveanzeigeneinheit erstellen](#live-ad-units) und Aktualisieren Ihrer app-Code, um die-ID und anzeigeneinheits-IDs für diese anzeigeneinheit zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="5b13e-110">After you finish testing your UWP app and you are ready to submit it to Partner Center, you must [create a live ad unit](#live-ad-units) from the [In-app ads](../publish/in-app-ads.md) page in Partner Center and update your app code to use the application ID and ad unit ID values for this ad unit.</span></span>

<span data-ttu-id="5b13e-111">Weitere Informationen zum Zuweisen der Anwendungs-ID- und Anzeigeneinheits-ID-Werte in Ihrem App-Code finden Sie in den folgenden Artikeln:</span><span class="sxs-lookup"><span data-stu-id="5b13e-111">For more information about assigning the application ID and ad unit ID values in your app's code, see the following articles:</span></span>
* [<span data-ttu-id="5b13e-112">AdControl in XAML und .NET</span><span class="sxs-lookup"><span data-stu-id="5b13e-112">AdControl in XAML and .NET</span></span>](adcontrol-in-xaml-and--net.md)
* [<span data-ttu-id="5b13e-113">AdControl in HTML 5 und Javascript</span><span class="sxs-lookup"><span data-stu-id="5b13e-113">AdControl in HTML 5 and Javascript</span></span>](adcontrol-in-html-5-and-javascript.md)
* [<span data-ttu-id="5b13e-114">Interstitialwerbung</span><span class="sxs-lookup"><span data-stu-id="5b13e-114">Interstitial ads</span></span>](../monetize/interstitial-ads.md)
* [<span data-ttu-id="5b13e-115">Native Anzeigen</span><span class="sxs-lookup"><span data-stu-id="5b13e-115">Native ads</span></span>](../monetize/native-ads.md)

<span id="test-ad-units" />

## <a name="test-ad-units"></a><span data-ttu-id="5b13e-116">Testen von Anzeigeeinheiten</span><span class="sxs-lookup"><span data-stu-id="5b13e-116">Test ad units</span></span>

<span data-ttu-id="5b13e-117">Während Sie Ihre App entwickeln, verwenden Sie die entsprechende Testanwendungs-ID und Anzeigenblock-ID, um zu beobachten, wie die Werbung während der Testphase von Ihrer App gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="5b13e-117">While you are developing your app, use the test application ID and ad unit ID values from this section to see how your app renders ads during testing.</span></span>

### <a name="banner-ads-using-the-adcontrol-class"></a><span data-ttu-id="5b13e-118">Banneranzeigen (unter Verwendung der AdControl-Klasse)</span><span class="sxs-lookup"><span data-stu-id="5b13e-118">Banner ads (using the AdControl class)</span></span>

* <span data-ttu-id="5b13e-119">Anzeigeeinheiten-ID:</span><span class="sxs-lookup"><span data-stu-id="5b13e-119">Ad unit ID:</span></span> ```test```
* <span data-ttu-id="5b13e-120">Anwendungs-ID:</span><span class="sxs-lookup"><span data-stu-id="5b13e-120">Application ID:</span></span>  ```3f83fe91-d6be-434d-a0ae-7351c5a997f1```

    > [!IMPORTANT]
    > <span data-ttu-id="5b13e-121">Für ein **AdControl** wird die Größe einer Liveanzeige durch die Eigenschaften **Width** und **Height** bestimmt.</span><span class="sxs-lookup"><span data-stu-id="5b13e-121">For an **AdControl**, the size of a live ad is defined by the **Width** and **Height** properties.</span></span> <span data-ttu-id="5b13e-122">Um optimale Ergebnisse zu erzielen, stellen Sie sicher, dass die Eigenschaften **Width** und **Height** zu den [unterstützten Eigenschaften für Banneranzeigen](supported-ad-sizes-for-banner-ads.md) gehören.</span><span class="sxs-lookup"><span data-stu-id="5b13e-122">For best results, make sure that the **Width** and **Height** properties in your code are one of the [supported ad sizes for banner ads](supported-ad-sizes-for-banner-ads.md).</span></span> <span data-ttu-id="5b13e-123">Die Eigenschaften **Width** und **Height** ändern sich nicht entsprechend der Größe einer Liveanzeige.</span><span class="sxs-lookup"><span data-stu-id="5b13e-123">The **Width** and **Height** properties will not change based on the size of a live ad.</span></span>

### <a name="interstitial-ads-and-native-ads"></a><span data-ttu-id="5b13e-124">Interstitialwerbung und native Anzeigen</span><span class="sxs-lookup"><span data-stu-id="5b13e-124">Interstitial ads and native ads</span></span>

* <span data-ttu-id="5b13e-125">Anzeigeeinheiten-ID:</span><span class="sxs-lookup"><span data-stu-id="5b13e-125">Ad unit ID:</span></span> ```test```
* <span data-ttu-id="5b13e-126">Anwendungs-ID:</span><span class="sxs-lookup"><span data-stu-id="5b13e-126">Application ID:</span></span>  ```d25517cb-12d4-4699-8bdc-52040c712cab```

<span id="live-ad-units" />

## <a name="live-ad-units"></a><span data-ttu-id="5b13e-127">Live-Anzeigeneinheiten</span><span class="sxs-lookup"><span data-stu-id="5b13e-127">Live ad units</span></span>

<span data-ttu-id="5b13e-128">Live-anzeigeneinheiten von Partner Center abgerufen und in Ihrer app verwenden:</span><span class="sxs-lookup"><span data-stu-id="5b13e-128">To get a live ad unit from Partner Center and use it in your app:</span></span>

1.  <span data-ttu-id="5b13e-129">[Erstellen Sie eine anzeigeneinheit](../publish/in-app-ads.md#create-ad-unit) auf der Seite **In-app-Werbung** im Partner Center.</span><span class="sxs-lookup"><span data-stu-id="5b13e-129">[Create an ad unit](../publish/in-app-ads.md#create-ad-unit) on the **In-app ads** page in Partner Center.</span></span> <span data-ttu-id="5b13e-130">Achten Sie darauf, dass Sie den richtigen Typ der Anzeigeneinheit für das Ad-Steuerelement angeben, die Sie in Ihrer App verwenden.</span><span class="sxs-lookup"><span data-stu-id="5b13e-130">Be sure to specify the correct type of ad unit for the ad control you are using in your app.</span></span>
    > [!NOTE]
    > <span data-ttu-id="5b13e-131">Sie können optional die Anzeigenvermittlung für Ihre Anzeigeneinheit durch das Konfigurieren der Einstellungen im Abschnitt [Vermittlungseinstellungen](../publish/in-app-ads.md#mediation).</span><span class="sxs-lookup"><span data-stu-id="5b13e-131">You can optionally enable ad mediation for your ad unit by configuring the settings in the [Mediation settings](../publish/in-app-ads.md#mediation) section.</span></span> <span data-ttu-id="5b13e-132">Mit der Anzeigenvermittlung können Sie Ihre Anzeigenumsätze maximieren und Werbefunktionen optimal nutzen, indem Sie Anzeigen aus mehreren Anzeigennetzwerken anzeigen, einschließlich Anzeigen aus anderen kostenpflichtigen Anzeigennetzwerken und Anzeigen zu Werbekampagnen für Microsoft-Apps.</span><span class="sxs-lookup"><span data-stu-id="5b13e-132">Ad mediation enables you to maximize your ad revenue and app promotion capabilities by displaying ads from multiple ad networks, including ads from other paid ad networks and ads for Microsoft app promotion campaigns.</span></span> <span data-ttu-id="5b13e-133">Wir wählen standardmäßig die Einstellungen der Anzeigenvermittlung für Ihre App mithilfe von Machine Learning Algorithmen aus, um Ihnen beim Optimieren der Anzeigenumsätze in den verschiedenen Märkten zu helfen, die Ihre App unterstützt. Sie können optional die Einstellungen für die Anzeigenvermittlung auch manuell konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="5b13e-133">By default, we automatically choose the ad mediation settings for your app using machine-learning algorithms to help you maximize your ad revenue across the markets your app supports, but you can optionally manually configure your mediation settings.</span></span>

2.  <span data-ttu-id="5b13e-134">Nachdem Sie die neue Anzeigeneinheit erstellen, rufen Sie die **Anwendungs-ID** und **Anzeigeneinheits-ID** für die Anzeigeneinheit in der Tabelle der verfügbaren Anzeigeneinheiten in der **Monetisierung** &gt; **in-App-Anzeigen** Seite ab.</span><span class="sxs-lookup"><span data-stu-id="5b13e-134">After you create the new ad unit, retrieve the **Application ID** and **Ad unit ID** for the ad unit in the table of available ad units in the **Monetize** &gt; **In-app ads** page.</span></span>
    > [!NOTE]
    > <span data-ttu-id="5b13e-135">Die Anwendungs-IDs für Test-Anzeigeneinheiten und Live-UWP-Anzeigeneinheiten besitzen unterschiedliche Formate.</span><span class="sxs-lookup"><span data-stu-id="5b13e-135">The application ID values for test ad units and live UWP ad units have different formats.</span></span> <span data-ttu-id="5b13e-136">Testanwendungs-ID sind GUIDs.</span><span class="sxs-lookup"><span data-stu-id="5b13e-136">Test application ID values are GUIDs.</span></span> <span data-ttu-id="5b13e-137">Wenn Sie eine live-UWP-anzeigeneinheit in Partner Center erstellen, entspricht der Anwendung-ID-Wert für die anzeigeneinheit immer die Store-ID für Ihre app (der ein Beispiel für Store-ID-Wert ist 9nblggh4r315).).</span><span class="sxs-lookup"><span data-stu-id="5b13e-137">When you create a live UWP ad unit in Partner Center, the application ID value for the ad unit always matches the Store ID for your app (an example Store ID value looks like 9NBLGGH4R315).</span></span>

3.  <span data-ttu-id="5b13e-138">Weisen Sie die Anwendungs-ID- und Anzeigeneinheits-ID-Werte in Ihrem App Code zu.</span><span class="sxs-lookup"><span data-stu-id="5b13e-138">Assign the application ID and ad unit ID values in your app's code.</span></span> <span data-ttu-id="5b13e-139">Weitere Informationen finden Sie in den folgenden Artikeln:</span><span class="sxs-lookup"><span data-stu-id="5b13e-139">For more information, see the following articles:</span></span>
    * [<span data-ttu-id="5b13e-140">AdControl in XAML und .NET</span><span class="sxs-lookup"><span data-stu-id="5b13e-140">AdControl in XAML and .NET</span></span>](adcontrol-in-xaml-and--net.md)
    * [<span data-ttu-id="5b13e-141">AdControl in HTML 5 und Javascript</span><span class="sxs-lookup"><span data-stu-id="5b13e-141">AdControl in HTML 5 and Javascript</span></span>](adcontrol-in-html-5-and-javascript.md)
    * [<span data-ttu-id="5b13e-142">Interstitialwerbung</span><span class="sxs-lookup"><span data-stu-id="5b13e-142">Interstitial ads</span></span>](../monetize/interstitial-ads.md)
    * [<span data-ttu-id="5b13e-143">Native Anzeigen</span><span class="sxs-lookup"><span data-stu-id="5b13e-143">Native ads</span></span>](../monetize/native-ads.md)

<span id="manage" />

## <a name="manage-ad-units-for-multiple-ad-controls-in-your-app"></a><span data-ttu-id="5b13e-144">Verwalten von Anzeigeeinheiten für mehrere Steuerelemente von Anzeigen in Ihrer App</span><span class="sxs-lookup"><span data-stu-id="5b13e-144">Manage ad units for multiple ad controls in your app</span></span>

<span data-ttu-id="5b13e-145">Können mehrere Steuerelemente für Banner-, Interstitialwerbungen und native Anzeigen in einer einzelnen App verwenden.</span><span class="sxs-lookup"><span data-stu-id="5b13e-145">You can use multiple banner, interstitial, and native ad controls in a single app.</span></span> <span data-ttu-id="5b13e-146">In diesem Fall wird empfohlen, dass Sie jedem Steuerelement eine andere Anzeigeneinheit zuweisen.</span><span class="sxs-lookup"><span data-stu-id="5b13e-146">In this scenario, we recommend that you assign a different ad unit to each control.</span></span> <span data-ttu-id="5b13e-147">Durch das Verwenden verschiedener Anzeigeeinheiten für jedes Steuerelement können Sie für jedes Steuerelement [die Einstellungen für die Anzeigenvermittlung konfigurieren](../publish/in-app-ads.md#mediation) und diskrete [Berichtsdaten](../publish/advertising-performance-report.md).</span><span class="sxs-lookup"><span data-stu-id="5b13e-147">Using different ad units for each control enables you to separately [configure the mediation settings](../publish/in-app-ads.md#mediation) and get discrete [reporting data](../publish/advertising-performance-report.md) for each control.</span></span> <span data-ttu-id="5b13e-148">Außerdem können unsere Dienste so die Werbung optimieren, die wir in Ihrer App anzeigen.</span><span class="sxs-lookup"><span data-stu-id="5b13e-148">This also enables our services to better optimize the ads we serve to your app.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5b13e-149">Sie können jede Anzeigeneinheit in nur einer App verwenden.</span><span class="sxs-lookup"><span data-stu-id="5b13e-149">You can use each ad unit in only one app.</span></span> <span data-ttu-id="5b13e-150">Wenn Sie eine Anzeigeneinheit in mehr als einer App verwenden, werden für die Ad-Einheit keine Anzeigen platziert.</span><span class="sxs-lookup"><span data-stu-id="5b13e-150">If you use an ad unit in more than one app, ads will not be served for that ad unit.</span></span>

## <a name="related-topics"></a><span data-ttu-id="5b13e-151">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="5b13e-151">Related topics</span></span>

* [<span data-ttu-id="5b13e-152">AdControl in XAML und .NET</span><span class="sxs-lookup"><span data-stu-id="5b13e-152">AdControl in XAML and .NET</span></span>](adcontrol-in-xaml-and--net.md)
* [<span data-ttu-id="5b13e-153">AdControl in HTML 5 und Javascript</span><span class="sxs-lookup"><span data-stu-id="5b13e-153">AdControl in HTML 5 and Javascript</span></span>](adcontrol-in-html-5-and-javascript.md)
* [<span data-ttu-id="5b13e-154">Interstitialwerbung</span><span class="sxs-lookup"><span data-stu-id="5b13e-154">Interstitial ads</span></span>](interstitial-ads.md)
* [<span data-ttu-id="5b13e-155">Native Anzeigen</span><span class="sxs-lookup"><span data-stu-id="5b13e-155">Native ads</span></span>](native-ads.md)


 

 
