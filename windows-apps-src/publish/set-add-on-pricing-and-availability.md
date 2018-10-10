---
author: jnHs
Description: When submitting an add-on, the options on the Pricing and availability page determine what to charge for your add-on and how it should be offered to customers.
title: Festlegen der Preise und Verfügbarkeit von Add-Ons
ms.assetid: B3D4B753-716B-460B-A3B1-ED5712ECD694
ms.author: wdg-dev-content
ms.date: 05/08/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Add-Ons, IAP, Preis
ms.localizationpriority: medium
ms.openlocfilehash: b5b7a6424fea3d62849e992f56b0b40ab72a55f5
ms.sourcegitcommit: 8e30651fd691378455ea1a57da10b2e4f50e66a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/10/2018
ms.locfileid: "4500941"
---
# <a name="set-add-on-pricing-and-availability"></a><span data-ttu-id="4fd29-103">Festlegen der Preise und Verfügbarkeit von Add-Ons</span><span class="sxs-lookup"><span data-stu-id="4fd29-103">Set add-on pricing and availability</span></span>


<span data-ttu-id="4fd29-104">Beim Übermitteln eines Add-Ons bestimmen die Optionen auf der Seite **Preise und Verfügbarkeit**, zu welchem Preis und wie das Add-On Kunden angeboten werden soll.</span><span class="sxs-lookup"><span data-stu-id="4fd29-104">When submitting an add-on, the options on the **Pricing and availability** page determine what to charge for your add-on and how it should be offered to customers.</span></span>

## <a name="markets"></a><span data-ttu-id="4fd29-105">Märkte</span><span class="sxs-lookup"><span data-stu-id="4fd29-105">Markets</span></span>

<span data-ttu-id="4fd29-106">Ihr Add-On wird standardmäßig in allen möglichen Märkten, einschließlich zukünftigen Märkten, die möglicherweise später hinzukommen, zum Grundpreis eingetragen.</span><span class="sxs-lookup"><span data-stu-id="4fd29-106">By default, your add-on will be listed in all possible markets, including any future markets that we may add later, at its base price.</span></span>

<span data-ttu-id="4fd29-107">Allerdings können Sie genauso wie bei einer App bestimmen, in welchen Märkten Ihr Add-On angeboten werden soll.</span><span class="sxs-lookup"><span data-stu-id="4fd29-107">However, just as with an app, you have the option to choose the markets in which you'd like to offer your add-on.</span></span> <span data-ttu-id="4fd29-108">In den meisten Fällen werden Sie dieselben Märkte wie für die App auswählen, haben aber die Flexibilität, nach Bedarf Änderungen vorzunehmen.</span><span class="sxs-lookup"><span data-stu-id="4fd29-108">In most cases you'll want to pick the same set of markets as the app, but you have the flexibility to make changes as needed.</span></span> 

<span data-ttu-id="4fd29-109">Weitere Informationen und eine vollständige Liste der verfügbaren Märkte finden Sie unter [Festlegen der Märkte](define-pricing-and-market-selection.md).</span><span class="sxs-lookup"><span data-stu-id="4fd29-109">For more info and a full list of the available markets, see [Define market selection](define-pricing-and-market-selection.md).</span></span>

## <a name="visibility"></a><span data-ttu-id="4fd29-110">Sichtbarkeit</span><span class="sxs-lookup"><span data-stu-id="4fd29-110">Visibility</span></span>

<span data-ttu-id="4fd29-111">Sie können festlegen, ob Ihr Add-On Kunden zum Kauf angeboten werden soll.</span><span class="sxs-lookup"><span data-stu-id="4fd29-111">You can determine whether your add-on should be offered for purchase to customers.</span></span> 

<span data-ttu-id="4fd29-112">Die Standardoption ist **Can be displayed in the parent product’s Store listing**.</span><span class="sxs-lookup"><span data-stu-id="4fd29-112">The default option is **Can be displayed in the parent product’s Store listing**.</span></span> <span data-ttu-id="4fd29-113">Lassen Sie diese Option für Add-Ons aktiviert, die für alle Kunden verfügbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="4fd29-113">Leave this option checked for add-ons that will be made available to any customer.</span></span> 

<span data-ttu-id="4fd29-114">Wählen Sie für Add-Ons, die Sie nicht allgemein verfügbar machen möchten, **Hidden in the Store** und eine der folgenden Optionen aus:</span><span class="sxs-lookup"><span data-stu-id="4fd29-114">For add-ons that you don't want to make broadly available, select **Hidden in the Store** and one of the following options:</span></span>

-   <span data-ttu-id="4fd29-115">**Nur innerhalb des übergeordneten Produkts zum Kauf erhältlich:** Bei Auswahl dieser Option können Kunden das Add-On innerhalb Ihrer App kaufen, es wird aber im Store-Eintrag Ihrer App nicht aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="4fd29-115">**Available for purchase from within the parent product only**: Choosing this option allows any customer to purchase the add-on from within your app, but the add-on will not be displayed in your app's Store listing.</span></span> <span data-ttu-id="4fd29-116">Verwenden Sie diese Option nur, wenn das Angebot nicht allgemein verfügbar ist, z.B. im Anfangszeitraum interner Tests.</span><span class="sxs-lookup"><span data-stu-id="4fd29-116">Use this only when the offer is not broadly available, for example during initial periods of internal testing.</span></span>
-   <span data-ttu-id="4fd29-117">**Beenden des Erwerbs: Alle Kunden mit einem direkten Link können den Produkt-Store-Eintrag sehen, aber sie können ihn nur herunterladen, wenn sie das Produkts vorher erworben haben oder einen Werbecode und ein Windows10-Gerät verwenden. Dieses Add-On wird nicht im übergeordneten Produkteintrag angezeigt**: Wenn Sie diese Option auswählen, wird das Add-On nicht im App Eintrag angezeigt, und neuen Kunden können das Add-On nicht erwerben.</span><span class="sxs-lookup"><span data-stu-id="4fd29-117">**Stop acquisition: Any customer with a direct link can see the product’s Store listing, but they can only download it if they owned the product before, or have a promotional code and are using a Windows 10 device. This add-on is not displayed in the parent product's listing**: Choosing this option means that the add-on won't be displayed in your app's listing, and no new customers may purchase the add-on.</span></span> <span data-ttu-id="4fd29-118">Allerdings wird **diese Option für Kunden mit Windows8.1 oder einer früheren Version nicht unterstützt**.</span><span class="sxs-lookup"><span data-stu-id="4fd29-118">However, **this option is not supported for customers on Windows 8.1 or earlier**.</span></span> <span data-ttu-id="4fd29-119">Wenn Ihre App für Windows8.1 oder eine frühere Version verfügbar ist, kann das Add-On von diesen Kunden erworben werden.</span><span class="sxs-lookup"><span data-stu-id="4fd29-119">If your app is available on Windows 8.1 or earlier, the add-on will still be available for purchase to those customers.</span></span> <span data-ttu-id="4fd29-120">Um das Add-On-Angebot für Kunden mit Windows8.1 oder einer früheren Version einzustellen, müssen Sie die App aktualisieren, indem Sie den Code entfernen, durch den das Add-On angeboten wird, und eine neue Übermittlung für die App veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="4fd29-120">To stop offering the add-on to customers on Windows 8.1 or earlier, you'll need to update your app to remove the code that offers the add-on, then publish a new submission for the app.</span></span> <span data-ttu-id="4fd29-121">Dieser Schritt wird selbst dann empfohlen, wenn Ihre App keine Unterstützung für Windows8.1 oder frühere Versionen bietet, da die Kundenerfahrung beeinträchtigt werden könnte, wenn Sie erst ein Add-On anbieten, das Sie später zurückziehen.</span><span class="sxs-lookup"><span data-stu-id="4fd29-121">This is recommended even if your app doesn't target Windows 8.1 or earlier; it's a better experience for your customers if you never offer them an add-on that you've opted to make unavailable.</span></span>
    
 > [!NOTE] 
 > <span data-ttu-id="4fd29-122">Das Auswählen der Option **Beenden des Erwerbs** und/oder das Übermitteln eines App-Updates, durch das das Add-On aus dem Code der App entfernt wird, wirkt sich nicht auf Kunden aus, die das Add-On bereits erworben haben, und zwar unabhängig von ihrem Betriebssystem.</span><span class="sxs-lookup"><span data-stu-id="4fd29-122">Choosing the **Stop acquisition** option, and/or submitting an app update that removes the add-on from your app's code, does not affect customers who have already purchased the add-on, regardless of their operating system.</span></span>


## <a name="schedule"></a><span data-ttu-id="4fd29-123">Zeitplan</span><span class="sxs-lookup"><span data-stu-id="4fd29-123">Schedule</span></span>

<span data-ttu-id="4fd29-124">Standardmäßig (es sei denn, Sie haben eine der Optionen für **Hidden in the Store** im Abschnitt **Sichtbarkeit** ausgewählt) wird Ihre Add-On für Kunden zur Verfügung gestellt, sobald sie die Zertifizierung bestanden und den Veröffentlichungsprozess abgeschlossen hat.</span><span class="sxs-lookup"><span data-stu-id="4fd29-124">By default (unless you have selected one of the **Hidden in the Store** options in the **Visibility** section), your add-on will be available to customers as soon as it passes certification and complete the publishing process.</span></span> <span data-ttu-id="4fd29-125">Um ein anderes Datum auszuwählen, wählen Sie **Optionen anzeigen**, um diesen Abschnittzu erweitern.</span><span class="sxs-lookup"><span data-stu-id="4fd29-125">To choose other dates, select **Show options** to expand this section.</span></span> 

<span data-ttu-id="4fd29-126">Weitere Informationen finden Sie unter [Konfigurieren des genauen Veröffentlichungszeitplans](configure-precise-release-scheduling.md).</span><span class="sxs-lookup"><span data-stu-id="4fd29-126">For more info, see [Configure precise release scheduling](configure-precise-release-scheduling.md).</span></span>


## <a name="pricing"></a><span data-ttu-id="4fd29-127">Preise</span><span class="sxs-lookup"><span data-stu-id="4fd29-127">Pricing</span></span>

<span data-ttu-id="4fd29-128">Sie müssen einen Grundpreis für Ihr Add-on auswählen (es sei denn, Sie das **Beenden des Erwerbs** im Abschnitt **Sichtbarkeit** gewählt haben).</span><span class="sxs-lookup"><span data-stu-id="4fd29-128">You must select a base price for your add-on (unless you have selected the **Stop acquisition** option in the **Visibility** section).</span></span> <span data-ttu-id="4fd29-129">Die Standardeinstellung ist **frei**, wenn Sie Geld für das Add-on erheben möchten, werden Sie eine der verfügbaren Preisniveaus auswählen (beginnend mit.99 US-Dollar) auswählen.</span><span class="sxs-lookup"><span data-stu-id="4fd29-129">The default selection is **Free**, so if you want to charge money for the add-on, be sure to choose one of the available price tiers (starting at .99 USD).</span></span>

<span data-ttu-id="4fd29-130">Sie können auch Preisänderungen planen, um das Datum und die Uhrzeit anzugeben, an dem bzw. zu der sich der Preis Ihrer Add-On ändern soll.</span><span class="sxs-lookup"><span data-stu-id="4fd29-130">You can also schedule price changes to indicate the date and time at which the add-on’s price should change.</span></span> <span data-ttu-id="4fd29-131">Darüber hinaus haben Sie die Möglichkeit, diese Änderungen für bestimmte Märkte anzupassen.</span><span class="sxs-lookup"><span data-stu-id="4fd29-131">Additionally, you have the option to customize these changes for specific markets.</span></span> 

> [!TIP]
> <span data-ttu-id="4fd29-132">Für die Abonnement-Add-Ons können nicht Sie den Preis auslösen, nach der Veröffentlichung des Add-Ons, entweder durch die Auswahl eines höheren Grundpreis in einer späteren Übermittlung oder durch einen Preis ändern, die Preiserhöhungen planen.</span><span class="sxs-lookup"><span data-stu-id="4fd29-132">For subscription add-ons, you can't raise the price after you publish the add-on, either by selecting a higher base price in a later submission or by scheduling a price change that increases the price.</span></span> <span data-ttu-id="4fd29-133">Sie können einen geringeren Preis mit einer der folgenden Methoden auswählen, aber sobald der Preis gesenkt wird nicht mehr es höher als dieser neuen Preis ausgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="4fd29-133">You can select a lower price using either of these methods, but once the price is lowered you won't be able to raise it higher than that new price.</span></span> <span data-ttu-id="4fd29-134">Aus diesem Grund ist es besonders wichtig, um sicherzustellen, dass Sie die entsprechenden Preisstufe für Abonnement-Add-Ons auswählen.</span><span class="sxs-lookup"><span data-stu-id="4fd29-134">Because of this, it's especially important to be sure you select the appropriate price tier for subscription add-ons.</span></span> 

<span data-ttu-id="4fd29-135">Weitere Informationen finden Sie unter [Festlegen und Planen von App-Preisen](set-and-schedule-app-pricing.md).</span><span class="sxs-lookup"><span data-stu-id="4fd29-135">For more info, see [Set and schedule app pricing](set-and-schedule-app-pricing.md).</span></span>


## <a name="sale-pricing"></a><span data-ttu-id="4fd29-136">Sonderpreise</span><span class="sxs-lookup"><span data-stu-id="4fd29-136">Sale pricing</span></span>

<span data-ttu-id="4fd29-137">Wenn Sie Ihr Add-On zu einem reduzierten Preis für einen begrenzten Zeitraum anbieten möchten, können Sie ein Sonderangebot erstellen und planen.</span><span class="sxs-lookup"><span data-stu-id="4fd29-137">If you want to offer your add-on at a reduced price for a limited period of time, you can create and schedule a sale.</span></span> <span data-ttu-id="4fd29-138">Weitere Informationen finden Sie unter [Anbieten von Apps und Add-Ons](put-apps-and-add-ons-on-sale.md).</span><span class="sxs-lookup"><span data-stu-id="4fd29-138">For more info, see [Put apps and add-ons on sale](put-apps-and-add-ons-on-sale.md).</span></span>



