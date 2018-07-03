---
author: mcleanbyron
ms.assetid: 527660fb-8e32-41b4-89cb-d422ed48c69b
description: Verwenden Sie die exemplarischen Vorgehensweisen in diesem Abschnitt, um zu erfahren, wie Sie Banneranzeigen, Interstitialwerbung und native Anzeigen mithilfe der Microsoft Advertising-SDK hinzufügen.
title: Implementieren von Werbung in Ihrer App
ms.author: mcleans
ms.date: 05/11/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Anzeigen, Werbung, exemplarische Vorgehensweisen
ms.localizationpriority: medium
ms.openlocfilehash: c7562dd63206326f6cd278195effffdd2afa7b7f
ms.sourcegitcommit: 834992ec14a8a34320c96e2e9b887a2be5477a53
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2018
ms.locfileid: "1880831"
---
# <a name="implement-ads-in-your-app"></a><span data-ttu-id="06c07-104">Implementieren von Werbung in Ihrer App</span><span class="sxs-lookup"><span data-stu-id="06c07-104">Implement ads in your app</span></span>

<span data-ttu-id="06c07-105">In diesem Abschnitt wird erläutert, wie Sie Banneranzeigen, Interstitialwerbung und native Anzeigen mithilfe der Microsoft Advertising-SDK hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="06c07-105">The articles in this section show you how to add banner ads, interstitial ads, and native ads to apps by using the Microsoft Advertising SDK.</span></span> <span data-ttu-id="06c07-106">Vollständige Beispielprojekte finden Sie unter den [Anzeigenbeispielen auf GitHub](http://aka.ms/githubads).</span><span class="sxs-lookup"><span data-stu-id="06c07-106">For complete sample projects, see the [advertising samples on GitHub](http://aka.ms/githubads).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="06c07-107">Inhalt dieses Abschnitts</span><span class="sxs-lookup"><span data-stu-id="06c07-107">In this section</span></span>

|  <span data-ttu-id="06c07-108">Thema</span><span class="sxs-lookup"><span data-stu-id="06c07-108">Topic</span></span>    | <span data-ttu-id="06c07-109">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="06c07-109">Description</span></span> |               
|----------|-------|
| [<span data-ttu-id="06c07-110">Banneranzeigen</span><span class="sxs-lookup"><span data-stu-id="06c07-110">Banner ads</span></span>](banner-ads.md)     | <span data-ttu-id="06c07-111">Enthält Informationen zum Hinzufügen einer Banneranzeige für Ihre UWP-App mithilfe der [AdControl](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.aspx)-Klasse in der Microsoft Advertising-SDK.</span><span class="sxs-lookup"><span data-stu-id="06c07-111">Provides instructions for adding a banner ad to your UWP app by using the [AdControl](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.aspx) class in the Microsoft Advertising SDK.</span></span>        |
| [<span data-ttu-id="06c07-112">Interstitialanzeigen</span><span class="sxs-lookup"><span data-stu-id="06c07-112">Interstitial Ads</span></span>](interstitial-ads.md)    | <span data-ttu-id="06c07-113">Enthält Informationen zum Hinzufügen einer Interstitialwerbung für Ihre UWP-App mithilfe der [Interstitialwerbung](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.interstitialad.aspx)-Klasse in der Microsoft Advertising-SDK.</span><span class="sxs-lookup"><span data-stu-id="06c07-113">Provides instructions for adding an interstitial ad to your UWP app by using the [InterstitialAd](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.interstitialad.aspx) class in the Microsoft Advertising SDK.</span></span>       |
| [<span data-ttu-id="06c07-114">Native Anzeigen</span><span class="sxs-lookup"><span data-stu-id="06c07-114">Native ads</span></span>](native-ads.md)       | <span data-ttu-id="06c07-115">Enthält Informationen zum Hinzufügen einer nativen Anzeige für Ihre UWP-App mithilfe des **NativeAdsManagerV2** und der **NativeAdV2**-Klasse in der Microsoft Advertising-SDK.</span><span class="sxs-lookup"><span data-stu-id="06c07-115">Provides instructions for adding a native ad to your UWP app by using the **NativeAdsManagerV2** and **NativeAdV2** classes in the Microsoft Advertising SDK.</span></span>  |
| [<span data-ttu-id="06c07-116">Anzeigen von Werbung in Videoinhalten</span><span class="sxs-lookup"><span data-stu-id="06c07-116">Show ads in video content</span></span>](add-advertisements-to-video-content.md)     |  <span data-ttu-id="06c07-117">Enthält Anweisungen zum Anzeigen von Werbung während der Videoinhalte in Ihrer UWP-App (dieses Feature ist derzeit nur für Apps verfügbar, die mit JavaScript und HTML geschrieben werden).</span><span class="sxs-lookup"><span data-stu-id="06c07-117">Provides instructions for showing ads during video content in your UWP app (this feature is currently supported only for apps that are written using JavaScript with HTML).</span></span> |



 

 
