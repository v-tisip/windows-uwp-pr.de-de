---
author: Xansky
description: Enthält Informationen zum Anzeigen von Werbebannern in Ihrer UWP-app verwenden.
title: Banneranzeigen
ms.author: mhopkins
ms.date: 08/23/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, anzeigen, Werbung, AdControl, Banneranzeigen
ms.localizationpriority: medium
ms.openlocfilehash: fc47c8d40d10eef3e6d92f2d47485d8cf265172d
ms.sourcegitcommit: 9354909f9351b9635bee9bb2dc62db60d2d70107
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2018
ms.locfileid: "4682214"
---
# <a name="banner-ads"></a><span data-ttu-id="cbe65-104">Banneranzeigen</span><span class="sxs-lookup"><span data-stu-id="cbe65-104">Banner ads</span></span>

<span data-ttu-id="cbe65-105">Die Artikel in diesem Abschnitt zeigen, wie Sie die [AdControl](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol) -Klasse in der Microsoft Advertising-SDK verwenden, um Werbebanner zu Ihrer UWP-app hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="cbe65-105">The articles in this section show how to use the [AdControl](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol) class in the Microsoft Advertising SDK to add banner ads to your UWP app.</span></span>

<span data-ttu-id="cbe65-106">Banneranzeigen sind statische anzeigen, die einen rechteckigen Teil einer Seite in Ihrer app zum Anzeigen von Werbeinhalten nutzen.</span><span class="sxs-lookup"><span data-stu-id="cbe65-106">Banner ads are static display ads that utilize a rectangular portion of a page in your app to display promotional content.</span></span> <span data-ttu-id="cbe65-107">Diese Anzeigen können in regelmäßigen Abständen automatisch aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="cbe65-107">These ads can refresh automatically at regular intervals.</span></span> <span data-ttu-id="cbe65-108">Sie sind ein guter Ausgangspunkt, wenn Sie noch nicht mit Werbung in Ihrer App vertraut sind.</span><span class="sxs-lookup"><span data-stu-id="cbe65-108">This is a good place to start if you are new to advertising in your app.</span></span>

![addreferences](images/banner-ad.png)

## <a name="in-this-section"></a><span data-ttu-id="cbe65-110">Inhalt dieses Abschnitts</span><span class="sxs-lookup"><span data-stu-id="cbe65-110">In this section</span></span>

|  <span data-ttu-id="cbe65-111">Thema</span><span class="sxs-lookup"><span data-stu-id="cbe65-111">Topic</span></span>    | <span data-ttu-id="cbe65-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="cbe65-112">Description</span></span> |               
|----------|-------|
| [<span data-ttu-id="cbe65-113">AdControl in XAML und .NET</span><span class="sxs-lookup"><span data-stu-id="cbe65-113">AdControl in XAML and .NET</span></span>](adcontrol-in-xaml-and--net.md)     | <span data-ttu-id="cbe65-114">Hinzufügen eines Werbebanners in einer XAML-/.NET-App</span><span class="sxs-lookup"><span data-stu-id="cbe65-114">Add a banner ad in your XAML/.NET app.</span></span>        |
| [<span data-ttu-id="cbe65-115">AdControl in HTML 5 und Javascript</span><span class="sxs-lookup"><span data-stu-id="cbe65-115">AdControl in HTML 5 and Javascript</span></span>](adcontrol-in-html-5-and-javascript.md)     | <span data-ttu-id="cbe65-116">Hinzufügen eines Werbebanners in einer HTML5-/JavaScript-App</span><span class="sxs-lookup"><span data-stu-id="cbe65-116">Add a banner ad in your HTML5/JavaScript app.</span></span>        |
| [<span data-ttu-id="cbe65-117">Unterstützte Größen für Banneranzeigen</span><span class="sxs-lookup"><span data-stu-id="cbe65-117">Supported banner ad sizes</span></span>](supported-ad-sizes-for-banner-ads.md)    |  <span data-ttu-id="cbe65-118">Überprüfen Sie die unterstützten Größen für Banner-anzeigen in UWP-apps.</span><span class="sxs-lookup"><span data-stu-id="cbe65-118">Review the supported sizes for banner ads in UWP apps.</span></span>        |


## <a name="related-topics"></a><span data-ttu-id="cbe65-119">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="cbe65-119">Related topics</span></span>

* [<span data-ttu-id="cbe65-120">Anzeigenbeispiele auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cbe65-120">Advertising samples on GitHub</span></span>](http://aka.ms/githubads)
* [<span data-ttu-id="cbe65-121">Einrichten von Anzeigeneinheiten für die App</span><span class="sxs-lookup"><span data-stu-id="cbe65-121">Set up ad units for your app</span></span>](set-up-ad-units-in-your-app.md)
