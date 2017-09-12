---
author: mcleanbyron
ms.assetid: 48a1ef86-8514-4af8-9c93-81e869d36de7
description: Hier erfahren Sie, wie Sie programmgesteuert ein **AdControl** (Anzeigensteuerelement) mit JavaScript erstellen.
title: Erstellen eines AdControl-Elements in JavaScript
ms.author: mcleans
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Anzeigen, Werbung, AdControl, JavaScript
ms.openlocfilehash: 5a64f58c7f66dd1177549562364a483641b1fd32
ms.sourcegitcommit: 378382419f1fda4e4df76ffa9c8cea753d271e6a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2017
---
# <a name="create-an-adcontrol-in-javascript"></a><span data-ttu-id="02eef-104">Erstellen eines AdControl-Elements in JavaScript</span><span class="sxs-lookup"><span data-stu-id="02eef-104">Create an AdControl in Javascript</span></span>

<span data-ttu-id="02eef-105">Die Beispiele in diesem Artikel zeigen, wie Sie programmgesteuert ein [AdControl](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.aspx)-Element mit JavaScript erstellen.</span><span class="sxs-lookup"><span data-stu-id="02eef-105">The examples in this article shows how to programmatically create an [AdControl](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.aspx) using JavaScript.</span></span> <span data-ttu-id="02eef-106">In diesem Artikel wird davon ausgegangen, dass Sie die erforderlichen Verweise auf das Projekt zur Verwendung eines **AdControl**-Elements bereits hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="02eef-106">This article assumes that you have already added the necessary references to your project to use an **AdControl**.</span></span> <span data-ttu-id="02eef-107">Weitere Informationen, einschließlich einer ausführlichen exemplarischem Vorgehensweise zum Erstellen und Initialisieren eines **AdControl**-Elements im HTML-Markup anstelle von JavaScript, finden Sie unter [„AdControl“ in HTML5 und Javascript](adcontrol-in-html-5-and-javascript.md).</span><span class="sxs-lookup"><span data-stu-id="02eef-107">For more information, including a detailed walkthrough for creating and initializing an **AdControl** in HTML markup instead of JavaScript, see [AdControl in HTML 5 and Javascript](adcontrol-in-html-5-and-javascript.md).</span></span>

## <a name="html-div-for-an-adcontrol"></a><span data-ttu-id="02eef-108">HTML-div-Element für „AdControl“</span><span class="sxs-lookup"><span data-stu-id="02eef-108">HTML div for an AdControl</span></span>

<span data-ttu-id="02eef-109">**AdControl** benötigt ein **div**-Element auf der HTML-Seite, auf der die Werbung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="02eef-109">An **AdControl** needs to have a **div** on the html page that will show the ad.</span></span> <span data-ttu-id="02eef-110">Der folgende Code ist ein Beispiel für so ein **div**-Element.</span><span class="sxs-lookup"><span data-stu-id="02eef-110">The code below provides an example of such a **div**.</span></span>

> [!div class="tabbedCodeSnippets"]
``` html
<div id="myAd" style="position: absolute; top: 50px; left: 0px; width: 300px; height: 250px; z-index: 1"
    data-win-control="MicrosoftNSJS.Advertising.AdControl">
</div>
```

## <a name="javascript-for-creating-an-adcontrol"></a><span data-ttu-id="02eef-111">JavaScript zum Erstellen eines AdControl</span><span class="sxs-lookup"><span data-stu-id="02eef-111">JavaScript for creating an AdControl</span></span>

<span data-ttu-id="02eef-112">Im folgenden Beispiel wird davon ausgegangen, dass Sie in Ihrem HTML-Code ein vorhandenes **div**-Element mit der ID **MyAd** verwenden.</span><span class="sxs-lookup"><span data-stu-id="02eef-112">The following example assumes that you are using an existing **div** in your HTML with the ID **myAd**.</span></span>

<span data-ttu-id="02eef-113">Instanziieren Sie **AdControl** in der **app.onactivated**-Funktion.</span><span class="sxs-lookup"><span data-stu-id="02eef-113">Instantiate the **AdControl** in the **app.onactivated** function.</span></span>

> [!div class="tabbedCodeSnippets"]
[!code-javascript[<span data-ttu-id="02eef-114">AdControl</span><span class="sxs-lookup"><span data-stu-id="02eef-114">AdControl</span></span>](./code/AdvertisingSamples/AdControlSamples/js/main.js#DeclareAdControl)]

<span data-ttu-id="02eef-115">In diesem Beispiel wird davon ausgegangen, dass Sie die Ereignishandlermethoden **myAdError**, **myAdRefreshed** und **myAdEngagedChanged** bereits deklariert haben.</span><span class="sxs-lookup"><span data-stu-id="02eef-115">This example assumes that you have already declared event handler methods named **myAdError**, **myAdRefreshed**, and **myAdEngagedChanged**.</span></span>

> [!NOTE]
> <span data-ttu-id="02eef-116">Die in diesem Beispiel angezeigten Werte *applicationId* und *adUnitId* sind [Testmoduswerte](test-mode-values.md).</span><span class="sxs-lookup"><span data-stu-id="02eef-116">The *applicationId* and *adUnitId* values shown in this example are [test mode values](test-mode-values.md).</span></span> <span data-ttu-id="02eef-117">Sie müssen [diese Werte mit Livewerten aus Windows Dev Center ersetzen](set-up-ad-units-in-your-app.md), bevor Sie Ihre App für die Übermittlung einreichen.</span><span class="sxs-lookup"><span data-stu-id="02eef-117">You must [replace these values with live values](set-up-ad-units-in-your-app.md) from Windows Dev Center before submitting your app for submission.</span></span>

<span data-ttu-id="02eef-118">Wenn Sie diesen Code verwenden und keine Anzeigen angezeigt werden, können Sie versuchen, ein **position:relativ**-Attribut im **div**-Element einzufügen, das das **AdControl** enthält.</span><span class="sxs-lookup"><span data-stu-id="02eef-118">If you use this code and do not see ads, you can try inserting an attribute of **position:relative** in the **div** that contains the **AdControl**.</span></span> <span data-ttu-id="02eef-119">Dadurch wird die Standardeinstellung von **IFrame** überschrieben.</span><span class="sxs-lookup"><span data-stu-id="02eef-119">This will override the default setting of the **IFrame**.</span></span> <span data-ttu-id="02eef-120">Anzeigen werden ordnungsgemäß angezeigt, sofern sie nicht aufgrund des Werts dieses Attributs nicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="02eef-120">Ads will be displayed correctly, unless they are not being shown due to the value of this attribute.</span></span> <span data-ttu-id="02eef-121">Beachten Sie, dass neue Anzeigeeinheiten unter Umständen bis zu 30 Minuten nicht verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="02eef-121">Note that new ad units may not be available for up to 30 minutes.</span></span>

## <a name="related-topics"></a><span data-ttu-id="02eef-122">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="02eef-122">Related topics</span></span>

* [<span data-ttu-id="02eef-123">Anzeigenbeispiele bei GitHub</span><span class="sxs-lookup"><span data-stu-id="02eef-123">Advertising samples on GitHub</span></span>](http://aka.ms/githubads)

 

 
