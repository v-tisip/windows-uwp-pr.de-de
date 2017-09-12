---
author: jnHs
Description: "Beim Übermitteln eines Add-Ons sind die Optionen auf der Seite „Eigenschaften“ hilfreich, um das Verhalten Ihres Add-Ons festzulegen, wenn es Kunden angeboten wird."
title: Eingeben von Add-On-Eigenschaften
ms.assetid: 26D2139F-66FD-479E-940B-7491238ADCAE
ms.author: wdg-dev-content
ms.date: 06/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp
ms.openlocfilehash: 253e008d3622094dcfe765531d71e5f37b7777b0
ms.sourcegitcommit: de6bc8acec2cd5ebc36bb21b2ce1a9980c3e78b2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="enter-add-on-properties"></a><span data-ttu-id="535c2-104">Eingeben von Add-On-Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="535c2-104">Enter add-on properties</span></span>


<span data-ttu-id="535c2-105">Beim Übermitteln eines Add-Ons sind die Optionen auf der Seite **Eigenschaften** hilfreich, um das Verhalten Ihres Add-Ons festzulegen, wenn es Kunden angeboten wird.</span><span class="sxs-lookup"><span data-stu-id="535c2-105">When submitting an add-on, the options on the **Properties** page help determine the behavior of your add-on when offered to customers.</span></span>

## <a name="product-type"></a><span data-ttu-id="535c2-106">Produkttyp</span><span class="sxs-lookup"><span data-stu-id="535c2-106">Product type</span></span>

<span data-ttu-id="535c2-107">Beim ersten [Erstellen des Add-Ons](set-your-add-on-product-id.md) wird der Produkttyp ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="535c2-107">Your product type is selected when you first [create the add-on](set-your-add-on-product-id.md).</span></span> <span data-ttu-id="535c2-108">Der ausgewählte Produkttyp wird hier angezeigt, Sie können ihn jedoch nicht ändern.</span><span class="sxs-lookup"><span data-stu-id="535c2-108">The product type you selected is displayed here, but you can't change it.</span></span>

> [!TIP]
> <span data-ttu-id="535c2-109">Hinweis Wenn Sie das Add-On nicht veröffentlicht haben, können Sie die Übermittlung löschen und von vorne beginnen, falls Sie einen anderen Produkttyp auswählen möchten.</span><span class="sxs-lookup"><span data-stu-id="535c2-109">If you haven't published the add-on, you can delete the submission and start again if you want to choose a different product type.</span></span>

<span data-ttu-id="535c2-110">Die Felder, die Sie auf dieser Seite sehen, variieren je nach den Produkttyp Ihres Add-Ons.</span><span class="sxs-lookup"><span data-stu-id="535c2-110">The fields you see on this page will vary, depending on the product type of your add-on.</span></span>

## <a name="product-lifetime"></a><span data-ttu-id="535c2-111">Produktlebensdauer</span><span class="sxs-lookup"><span data-stu-id="535c2-111">Product lifetime</span></span>


<span data-ttu-id="535c2-112">Wenn Sie als Produkttyp **Gebrauchsgut** ausgewählt haben, wird hier die **Produktlebenszeit** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="535c2-112">If you selected **Durable** for your product type, **Product lifetime** is shown here.</span></span> <span data-ttu-id="535c2-113">Die standardmäßige **Produktlebenszeit** dauerhafter Add-Ons ist **Unbegrenzt**. Das Add-On läuft also niemals ab.</span><span class="sxs-lookup"><span data-stu-id="535c2-113">The default **Product lifetime** for a durable add-on is **Forever**, which means the add-on never expires.</span></span> <span data-ttu-id="535c2-114">Sie können die **Produktlebenszeit** auch festlegen, sodass das Add-On nach einem festgelegten Zeitraum abläuft (mögliche Optionen: 1 bis 365Tage).</span><span class="sxs-lookup"><span data-stu-id="535c2-114">If you prefer, you can set the **Product lifetime** so that the add-on expires after a set duration (with options from 1-365 days).</span></span>

## <a name="quantity"></a><span data-ttu-id="535c2-115">Menge</span><span class="sxs-lookup"><span data-stu-id="535c2-115">Quantity</span></span>


<span data-ttu-id="535c2-116">Wenn Sie den Produkttyp **Vom Store verwalteter Verbrauchsartikel** ausgewählt haben, wird hier die **Menge** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="535c2-116">If you selected **Store-managed consumable** for your product type, **Quantity** is shown here.</span></span> <span data-ttu-id="535c2-117">Sie müssen eine Zahl zwischen 1 und 1000000 eingeben.</span><span class="sxs-lookup"><span data-stu-id="535c2-117">You'll need to enter a number between 1 and 1000000.</span></span> <span data-ttu-id="535c2-118">Diese Menge wird Kunden gewährt, wenn sie Ihr Add-On erwerben, und vom Store wird der Betrag nachverfolgt, wenn die App die Nutzung des Add-Ons durch Kunden meldet.</span><span class="sxs-lookup"><span data-stu-id="535c2-118">This quantity will be granted to the customer when they acquire your add-on, and the Store will track the balance as the app reports the customer’s consumption of the add-on.</span></span>


## <a name="subscription-period"></a><span data-ttu-id="535c2-119">Abonnementdauer</span><span class="sxs-lookup"><span data-stu-id="535c2-119">Subscription period</span></span>

<span data-ttu-id="535c2-120">Wenn Sie als Produkttyp **Abonnement** ausgewählt haben, wird hier die **Abonnementdauer** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="535c2-120">If you selected **Subscription** for your product type, **Subscription period** is shown here.</span></span> <span data-ttu-id="535c2-121">Müssen Sie eine der verfügbaren Optionen auswählen (**Monatlich**, **3 Monate**, **6 Monate**, **Jährlich**, oder **24 Monate**), um anzugeben, wie häufig ein Kunde für das Abonnement in Rechnung gestellt wird.</span><span class="sxs-lookup"><span data-stu-id="535c2-121">You'll need to choose one of the available options (**Monthly**, **3 months**, **6 months**, **Annually**, or **24 months**) to indicate how frequently a customer will be charged for the subscription.</span></span> <span data-ttu-id="535c2-122">Beachten Sie, dass Sie nach der Veröffentlichung Ihres Add-Ons Ihre **Abonnementdauer** auswählen können.</span><span class="sxs-lookup"><span data-stu-id="535c2-122">Note that after your add-on is published, you can't change your **Subscription period** selection.</span></span>

> [!NOTE]
> <span data-ttu-id="535c2-123">Die Fähigkeit zum Erstellen von Abonnement-Add-Ons ist derzeit nur für eine Gruppe von Entwicklerkonten verfügbar, die am frühen Adoption-Programm teilnehmen.</span><span class="sxs-lookup"><span data-stu-id="535c2-123">Currently, the ability to create subscription add-ons is only available to a set of developer accounts who are participating in an early adoption program.</span></span> <span data-ttu-id="535c2-124">Wir stellen Abonnement-Add-Ons für alle Entwicklerkonten in Zukunft zur Verfügung und wir stellen Ihnen diese vorläufige Dokumentation jetzt zur Verfügung, um Entwicklern eine Vorschau dieser Funktion zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="535c2-124">We will make subscription add-ons available to all developer accounts in the future, and we are making this preliminary documentation available now to give developers a preview of this feature.</span></span> <span data-ttu-id="535c2-125">Weitere Informationen finden Sie unter [Abonnement-Add-Ons für Ihre App aktivieren](../monetize/enable-subscription-add-ons-for-your-app.md).</span><span class="sxs-lookup"><span data-stu-id="535c2-125">For more info, see [Enable subscription add-ons for your app](../monetize/enable-subscription-add-ons-for-your-app.md).</span></span>


## <a name="free-trial"></a><span data-ttu-id="535c2-126">Kostenlose Testversion</span><span class="sxs-lookup"><span data-stu-id="535c2-126">Free trial</span></span>

<span data-ttu-id="535c2-127">Für die Abonnement-Add-Ons wird hier ebenfalls eine **kostenlose Testversion** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="535c2-127">For subscription add-ons, **Free trial** is also shown here.</span></span> <span data-ttu-id="535c2-128">Sie müssen auswählen, ob Kunden das Add-On für einen festgelegten Zeitraum kostenlos verwenden können (entweder **1 Woche** oder **1 Monat**), oder ob Sie **keine kostenlose Testversion** anbieten.</span><span class="sxs-lookup"><span data-stu-id="535c2-128">You must select whether to let customers use the add-on for free for a set period of time (either **1 week** or **1 month**), or whether to offer **No free trial**.</span></span> <span data-ttu-id="535c2-129">Beachten Sie, dass Sie nach der Veröffentlichung Ihres Add-Ons Ihre **Kostenlose Testversion** auswählen können.</span><span class="sxs-lookup"><span data-stu-id="535c2-129">Note that after your add-on is published, you can't change your **Free trial** selection.</span></span>


## <a name="content-type"></a><span data-ttu-id="535c2-130">Inhaltstyp</span><span class="sxs-lookup"><span data-stu-id="535c2-130">Content type</span></span>

<span data-ttu-id="535c2-131">Unabhängig vom Produkttyp Ihres Add-Ons müssen Sie die Art der Inhalte angeben, die Sie anbieten.</span><span class="sxs-lookup"><span data-stu-id="535c2-131">Regardless of your add-on's product type, you'll need to indicate the type of content you're offering.</span></span> <span data-ttu-id="535c2-132">Für die meisten Add-Ons sollte der Inhaltstyp **Download elektronischer Software** lauten.</span><span class="sxs-lookup"><span data-stu-id="535c2-132">For most add-ons, the content type should be **Electronic software download**.</span></span> <span data-ttu-id="535c2-133">Wenn eine andere Option aus der Liste Ihr Add-On besser beschreibt (wenn Sie z.B. einen Musikdownload oder ein E-Book anbieten), wählen Sie stattdessen diese Option.</span><span class="sxs-lookup"><span data-stu-id="535c2-133">If another option from the list describes your add-on better (for example, if you are offering a music download or an e-book), select that option instead.</span></span>

<span data-ttu-id="535c2-134">Mögliche Optionen für den Inhaltstyp eines Add-Ons:</span><span class="sxs-lookup"><span data-stu-id="535c2-134">These are the possible options for an add-on's content type:</span></span>

-   <span data-ttu-id="535c2-135">Download elektronischer Software</span><span class="sxs-lookup"><span data-stu-id="535c2-135">Electronic software download</span></span>
-   <span data-ttu-id="535c2-136">Elektronische Bücher</span><span class="sxs-lookup"><span data-stu-id="535c2-136">Electronic books</span></span>
-   <span data-ttu-id="535c2-137">Einzelausgabe einer elektronischen Zeitschrift</span><span class="sxs-lookup"><span data-stu-id="535c2-137">Electronic magazine single issue</span></span>
-   <span data-ttu-id="535c2-138">Einzelausgabe einer elektronischen Zeitung</span><span class="sxs-lookup"><span data-stu-id="535c2-138">Electronic newspaper single issue</span></span>
-   <span data-ttu-id="535c2-139">Musikdownload</span><span class="sxs-lookup"><span data-stu-id="535c2-139">Music download</span></span>
-   <span data-ttu-id="535c2-140">Musikstreaming</span><span class="sxs-lookup"><span data-stu-id="535c2-140">Music streaming</span></span>
-   <span data-ttu-id="535c2-141">Onlinedatenspeicher/-dienste</span><span class="sxs-lookup"><span data-stu-id="535c2-141">Online data storage/services</span></span>
-   <span data-ttu-id="535c2-142">Software as a Service</span><span class="sxs-lookup"><span data-stu-id="535c2-142">Software as a service</span></span>
-   <span data-ttu-id="535c2-143">Videodownload</span><span class="sxs-lookup"><span data-stu-id="535c2-143">Video download</span></span>
-   <span data-ttu-id="535c2-144">Videostreaming</span><span class="sxs-lookup"><span data-stu-id="535c2-144">Video streaming</span></span>


## <a name="additional-properties"></a><span data-ttu-id="535c2-145">Weitere Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="535c2-145">Additional properties</span></span>

<span data-ttu-id="535c2-146">Diese Felder sind optional für alle Arten von Add-Ons.</span><span class="sxs-lookup"><span data-stu-id="535c2-146">These fields are optional for all types of add-ons.</span></span>

<span id="keywords" />
### <a name="keywords"></a><span data-ttu-id="535c2-147">Schlüsselwörter</span><span class="sxs-lookup"><span data-stu-id="535c2-147">Keywords</span></span>

<span data-ttu-id="535c2-148">Sie können für jedes eingereichte Add-On bis zu zehn Schlüsselwörter von jeweils bis zu 30 Zeichen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="535c2-148">You have the option to provide up to ten keywords of up to 30 characters each for each add-on you submit.</span></span> <span data-ttu-id="535c2-149">Danach kann Ihre App nach Add-Ons suchen, die diesen Schlüsselwörtern entsprechen.</span><span class="sxs-lookup"><span data-stu-id="535c2-149">Your app can then query for add-ons that match these words.</span></span> <span data-ttu-id="535c2-150">Durch dieses Feature können Sie Bildschirme in Ihrer App erstellen, die Add-Ons laden können, ohne dass Sie die Produkt-ID im App-Code direkt angeben müssen.</span><span class="sxs-lookup"><span data-stu-id="535c2-150">This feature lets you build screens in your app that can load add-ons without you having to directly specify the product ID in your app's code.</span></span> <span data-ttu-id="535c2-151">Sie können die Schlüsselwörter des Add-Ons später jederzeit ändern, ohne Codeänderungen an der App vorzunehmen oder die App erneut einzureichen.</span><span class="sxs-lookup"><span data-stu-id="535c2-151">You can then change the add-on's keywords anytime, without having to make code changes in your app or submit the app again.</span></span>

<span data-ttu-id="535c2-152">Verwenden Sie zur Abfrage des Felds die Eigenschaft [StoreProduct.Keywords](https://docs.microsoft.com/uwp/api/windows.services.store.storeproduct#Windows_Services_Store_StoreProduct_Keywords) in [Windows.Services.Store namespace](https://msdn.microsoft.com/en-us/library/windows/apps/windows.services.store.aspx).</span><span class="sxs-lookup"><span data-stu-id="535c2-152">To query this field, use the [StoreProduct.Keywords](https://docs.microsoft.com/uwp/api/windows.services.store.storeproduct#Windows_Services_Store_StoreProduct_Keywords) property in the [Windows.Services.Store namespace](https://msdn.microsoft.com/en-us/library/windows/apps/windows.services.store.aspx).</span></span> <span data-ttu-id="535c2-153">(Wenn Sie [Windows.ApplicationModel.Store-Namespace](https://msdn.microsoft.com/en-us/library/windows/apps/windows.applicationmodel.store.aspx) verwenden, nutzen Sie die Eigenschaft [ProductListing.Keywords](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.productlisting#Windows_ApplicationModel_Store_ProductListing_Keywords).)</span><span class="sxs-lookup"><span data-stu-id="535c2-153">(Or, if you're using the [Windows.ApplicationModel.Store namespace](https://msdn.microsoft.com/en-us/library/windows/apps/windows.applicationmodel.store.aspx), use the [ProductListing.Keywords](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.productlisting#Windows_ApplicationModel_Store_ProductListing_Keywords) property.)</span></span>

> [!NOTE]
> <span data-ttu-id="535c2-154">Schlüsselwörter stehen für Pakete, die auf Windows 8 und Windows 8.1 ausgerichtet sind, nicht zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="535c2-154">Keywords are not available for use in packages targeting Windows 8 and Windows 8.1.</span></span>

<span id="custom-developer-data" />
### <a name="custom-developer-data"></a><span data-ttu-id="535c2-155">Benutzerdefinierte Entwicklerdaten</span><span class="sxs-lookup"><span data-stu-id="535c2-155">Custom developer data</span></span>

<span data-ttu-id="535c2-156">Sie können im Feld **Benutzerdefinierte Entwicklerdaten** (früher **Tag**) bis zu 3.000 Zeichen eingeben, um zusätzlichen Kontext für das In-App-Produkt bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="535c2-156">You can enter up to 3000 characters into the **Custom developer data** field (formerly called **Tag**) to provide extra context for your in-app product.</span></span> <span data-ttu-id="535c2-157">Meistens handelt es sich um eine XML-Zeichenfolge. Sie können aber beliebige Inhalte eingeben.</span><span class="sxs-lookup"><span data-stu-id="535c2-157">Most often, this is in the form of an XML string, but you can enter anything you'd like in this field.</span></span> <span data-ttu-id="535c2-158">Ihre App kann dann dieses Feld abfragen, um den Inhalt zu lesen (auch wenn die App die Daten nicht bearbeiten kann und die Änderungen zurückgibt.)</span><span class="sxs-lookup"><span data-stu-id="535c2-158">Your app can then query this field to read its content (although the app can't edit the data and pass the changes back.)</span></span>

<span data-ttu-id="535c2-159">Nehmen Sie beispielsweise an, dass Sie ein Spiel anbieten und Add-Ons verkaufen, wodurch Kunden auf zusätzliche Ebenen zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="535c2-159">For example, let’s say you have a game, and you’re selling an add-on which allows the customer to access additional levels.</span></span> <span data-ttu-id="535c2-160">Mithilfe des Felds **Benutzerdefinierte Entwicklerdaten** kann die App abfragen, welche Ebenen verfügbar sind, wenn ein Kunde dieses Add-On erwirbt.</span><span class="sxs-lookup"><span data-stu-id="535c2-160">Using the **Custom developer data** field, the app can query to see which levels are available when a customer owns this add-on.</span></span> <span data-ttu-id="535c2-161">Sie können den Wert jederzeit anpassen (in diesem Fall die zugefügten Ebenen), ohne den Code der App zu ändern oder die App erneut zu übermitteln, indem Sie die Informationen im Feld **Benutzerdefinierte Entwicklerdaten** aktualisieren und dann eine aktualisierte Übermittlung für das Add-On veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="535c2-161">You could adjust the value at any time (in this case, the levels which are included), without having to make code changes in your app or submit the app again, by updating the info in the add-on's **Custom developer data** field and then publishing an updated submission for the add-on.</span></span>

<span data-ttu-id="535c2-162">Verwenden Sie zur Abfrage des Felds die Eigenschaft [StoreSku.CustomDeveloperData](https://msdn.microsoft.com/en-us/library/windows/apps/windows.services.store.storesku.customdeveloperdata.aspx) unter [Windows.Services.Store namespace](https://msdn.microsoft.com/en-us/library/windows/apps/windows.services.store.aspx).</span><span class="sxs-lookup"><span data-stu-id="535c2-162">To query this field, use the [StoreSku.CustomDeveloperData](https://msdn.microsoft.com/en-us/library/windows/apps/windows.services.store.storesku.customdeveloperdata.aspx) property in the [Windows.Services.Store namespace](https://msdn.microsoft.com/en-us/library/windows/apps/windows.services.store.aspx).</span></span> <span data-ttu-id="535c2-163">(Wenn Sie [Windows.ApplicationModel.Store-Namespace](https://msdn.microsoft.com/en-us/library/windows/apps/windows.applicationmodel.store.aspx) verwenden, nutzen Sie die Eigenschaft [ProductListing.Tag](https://msdn.microsoft.com/en-us/library/windows/apps/windows.applicationmodel.store.productlisting.tag.aspx).)</span><span class="sxs-lookup"><span data-stu-id="535c2-163">(Or, if you're using the [Windows.ApplicationModel.Store namespace](https://msdn.microsoft.com/en-us/library/windows/apps/windows.applicationmodel.store.aspx), use the [ProductListing.Tag](https://msdn.microsoft.com/en-us/library/windows/apps/windows.applicationmodel.store.productlisting.tag.aspx) property.)</span></span>

> [!NOTE]
> <span data-ttu-id="535c2-164">Das Feld **Benutzerdefinierte Entwicklerdaten** ist nicht in Paketen verfügbar, die für Windows8 und Windows8.1 entwickelt wurden.</span><span class="sxs-lookup"><span data-stu-id="535c2-164">The **Custom developer data** field is not available for use in packages targeting Windows 8 and Windows 8.1.</span></span>

 

 

 
