---
author: mcleanbyron
ms.assetid: 2ed21281-f996-402d-a968-d1320a4691df
description: "Verwenden Sie die für Tests vorgesehene Anwendungs-ID und die Anzeigeneinheits-ID aus diesem Artikel, um zu prüfen, wie Ihre App die Werbung während der Testphase rendert."
title: Testmoduswerte
ms.author: mcleans
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, Anzeigen, Werbung, Tests
ms.openlocfilehash: 0c3e713d9a2bb7c10bda0d9517f5cb882d5e2e57
ms.sourcegitcommit: 6b772d2a224f8a9c557dc517c6ec0592545e9a43
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2017
---
# <a name="test-mode-values"></a><span data-ttu-id="95f6b-104">Testmoduswerte</span><span class="sxs-lookup"><span data-stu-id="95f6b-104">Test mode values</span></span>

<span data-ttu-id="95f6b-105">Bei Verwendung von [AdControl](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.aspx), [InterstitialAd](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.interstitialad.aspx) oder [NativeAd](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.nativead.aspx)zum Anzeigen von Werbung in Ihrer App müssen Sie eine **AdUnitId** und eine **ApplicationId** angeben.</span><span class="sxs-lookup"><span data-stu-id="95f6b-105">When you use an [AdControl](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.aspx),  [InterstitialAd](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.interstitialad.aspx), or [NativeAd](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.nativead.aspx) to display ads in your app, you must specify an ad unit ID and application ID in the **AdUnitId** and **ApplicationId** properties.</span></span> <span data-ttu-id="95f6b-106">Während Sie Ihre App entwickeln, verwenden Sie die entsprechende Testanwendungs-ID und Anzeigenblock-ID, um zu beobachten, wie die Werbung während der Testphase von Ihrer App gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="95f6b-106">While you are developing your app, use the test application ID and ad unit ID values from this article to see how your app renders ads during testing.</span></span>

<span data-ttu-id="95f6b-107">Wenn Sie Testwerte in einer veröffentlichten App verwenden, wird die App keine Livewerbung empfangen.</span><span class="sxs-lookup"><span data-stu-id="95f6b-107">If you try to use test values in your app after you publish it, your live app not receive ads.</span></span> <span data-ttu-id="95f6b-108">Um Werbung in Ihrer veröffentlichten App zu empfangen, müssen Sie in Ihrem Code die Anwendungs-ID und die Anzeigeneinheits-ID verwenden, die im Windows Dev Center-Dashboard bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="95f6b-108">To receive ads in your published app, you must update your code to use an application ID and ad unit ID provided by the Windows Dev Center dashboard.</span></span> <span data-ttu-id="95f6b-109">Weitere Informationen finden Sie unter [Einrichten von Anzeigeneinheiten in der App](set-up-ad-units-in-your-app.md).</span><span class="sxs-lookup"><span data-stu-id="95f6b-109">For more information, see [Set up ad units in your app](set-up-ad-units-in-your-app.md).</span></span>
 
<span data-ttu-id="95f6b-110">Verwenden Sie die folgenden Werte für andere Anzeigentypen.</span><span class="sxs-lookup"><span data-stu-id="95f6b-110">Here are the test values to use for the different ad types.</span></span>

* <span data-ttu-id="95f6b-111">Für Interstitialwerbung:</span><span class="sxs-lookup"><span data-stu-id="95f6b-111">For interstitial ads:</span></span>

    <table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left"><span data-ttu-id="95f6b-112">Ziel-Betriebssystem</span><span class="sxs-lookup"><span data-stu-id="95f6b-112">Target OS</span></span></th>
    <th align="left"><span data-ttu-id="95f6b-113">AdUnitId</span><span class="sxs-lookup"><span data-stu-id="95f6b-113">AdUnitId</span></span></th>
    <th align="left"><span data-ttu-id="95f6b-114">ApplicationId</span><span class="sxs-lookup"><span data-stu-id="95f6b-114">ApplicationId</span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><p><span data-ttu-id="95f6b-115">UWP (Windows 10)</span><span class="sxs-lookup"><span data-stu-id="95f6b-115">UWP (Windows 10)</span></span></p></td>
    <td align="left"><p><span data-ttu-id="95f6b-116">test</span><span class="sxs-lookup"><span data-stu-id="95f6b-116">test</span></span></p></td>
    <td align="left"><p><span data-ttu-id="95f6b-117">d25517cb-12d4-4699-8bdc-52040c712cab</span><span class="sxs-lookup"><span data-stu-id="95f6b-117">d25517cb-12d4-4699-8bdc-52040c712cab</span></span></p></td>
    </tr>
    <tr class="odd">
    <td align="left"><p><span data-ttu-id="95f6b-118">Windows8.x und Windows Phone8.x</span><span class="sxs-lookup"><span data-stu-id="95f6b-118">Windows 8.x and Windows Phone 8.x</span></span></p></td>
    <td align="left"><p><span data-ttu-id="95f6b-119">11389925</span><span class="sxs-lookup"><span data-stu-id="95f6b-119">11389925</span></span></p></td>
    <td align="left"><p><span data-ttu-id="95f6b-120">d25517cb-12d4-4699-8bdc-52040c712cab</span><span class="sxs-lookup"><span data-stu-id="95f6b-120">d25517cb-12d4-4699-8bdc-52040c712cab</span></span></p></td>
    </tr>
    </tbody>
    </table>

     
* <span data-ttu-id="95f6b-121">Für Banneranzeigen:</span><span class="sxs-lookup"><span data-stu-id="95f6b-121">For banner ads:</span></span>

    <table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left"><span data-ttu-id="95f6b-122">Ziel-Betriebssystem</span><span class="sxs-lookup"><span data-stu-id="95f6b-122">Target OS</span></span></th>
    <th align="left"><span data-ttu-id="95f6b-123">AdUnitId</span><span class="sxs-lookup"><span data-stu-id="95f6b-123">AdUnitId</span></span></th>
    <th align="left"><span data-ttu-id="95f6b-124">ApplicationId</span><span class="sxs-lookup"><span data-stu-id="95f6b-124">ApplicationId</span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><p><span data-ttu-id="95f6b-125">UWP (Windows 10)</span><span class="sxs-lookup"><span data-stu-id="95f6b-125">UWP (Windows 10)</span></span></p></td>
    <td align="left"><p><span data-ttu-id="95f6b-126">test</span><span class="sxs-lookup"><span data-stu-id="95f6b-126">test</span></span></p></td>
    <td align="left"><p><span data-ttu-id="95f6b-127">3f83fe91-d6be-434d-a0ae-7351c5a997f1</span><span class="sxs-lookup"><span data-stu-id="95f6b-127">3f83fe91-d6be-434d-a0ae-7351c5a997f1</span></span></p></td>
    </tr>
    <tr class="even">
    <td align="left"><p><span data-ttu-id="95f6b-128">Windows8.x und Windows Phone8.x</span><span class="sxs-lookup"><span data-stu-id="95f6b-128">Windows 8.x and Windows Phone 8.x</span></span></p></td>
    <td align="left"><p><span data-ttu-id="95f6b-129">10865270</span><span class="sxs-lookup"><span data-stu-id="95f6b-129">10865270</span></span></p></td>
    <td align="left"><p><span data-ttu-id="95f6b-130">3f83fe91-d6be-434d-a0ae-7351c5a997f1</span><span class="sxs-lookup"><span data-stu-id="95f6b-130">3f83fe91-d6be-434d-a0ae-7351c5a997f1</span></span></p></td>
    </tr>
    </tbody>
    </table>

* <span data-ttu-id="95f6b-131">Für native Anzeigen:</span><span class="sxs-lookup"><span data-stu-id="95f6b-131">For native ads:</span></span>

    <table>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left"><span data-ttu-id="95f6b-132">Ziel-Betriebssystem</span><span class="sxs-lookup"><span data-stu-id="95f6b-132">Target OS</span></span></th>
    <th align="left"><span data-ttu-id="95f6b-133">AdUnitId</span><span class="sxs-lookup"><span data-stu-id="95f6b-133">AdUnitId</span></span></th>
    <th align="left"><span data-ttu-id="95f6b-134">ApplicationId</span><span class="sxs-lookup"><span data-stu-id="95f6b-134">ApplicationId</span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><p><span data-ttu-id="95f6b-135">UWP (Windows 10)</span><span class="sxs-lookup"><span data-stu-id="95f6b-135">UWP (Windows 10)</span></span></p></td>
    <td align="left"><p><span data-ttu-id="95f6b-136">test</span><span class="sxs-lookup"><span data-stu-id="95f6b-136">test</span></span></p></td>
    <td align="left"><p><span data-ttu-id="95f6b-137">d25517cb-12d4-4699-8bdc-52040c712cab</span><span class="sxs-lookup"><span data-stu-id="95f6b-137">d25517cb-12d4-4699-8bdc-52040c712cab</span></span></p></td>
    </tbody>
    </table>

> [!IMPORTANT]
> <span data-ttu-id="95f6b-138">Für ein **AdControl** wird die Größe einer Liveanzeige durch die Eigenschaften **Width** und **Height** bestimmt.</span><span class="sxs-lookup"><span data-stu-id="95f6b-138">For an **AdControl**, the size of a live ad is defined by the **Width** and **Height** properties.</span></span> <span data-ttu-id="95f6b-139">Um optimale Ergebnisse zu erzielen, stellen Sie sicher, dass die Eigenschaften **Width** und **Height** zu den [unterstützten Eigenschaften für Banneranzeigen](supported-ad-sizes-for-banner-ads.md) gehören.</span><span class="sxs-lookup"><span data-stu-id="95f6b-139">For best results, make sure that the **Width** and **Height** properties in your code are one of the [supported ad sizes for banner ads](supported-ad-sizes-for-banner-ads.md).</span></span> <span data-ttu-id="95f6b-140">Die Eigenschaften **Width** und **Height** ändern sich nicht entsprechend der Größe einer Liveanzeige.</span><span class="sxs-lookup"><span data-stu-id="95f6b-140">The **Width** and **Height** properties will not change based on the size of a live ad.</span></span>


 

 
