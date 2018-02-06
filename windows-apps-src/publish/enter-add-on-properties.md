---
author: jnHs
Description: When submitting an add-on, the options on the Properties page help determine the behavior of your add-on when offered to customers.
title: Eingeben von Add-On-Eigenschaften
ms.assetid: 26D2139F-66FD-479E-940B-7491238ADCAE
ms.author: wdg-dev-content
ms.date: 01/12/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Add-Ons, Eigenschaften, Abonnementzeitraum, Produktlebensdauer, Inhaltstyp, IAP, In-App-Kauf, In-App-Produkt
ms.localizationpriority: high
ms.openlocfilehash: 63fc414c230e5a988013b1509280bfdb083a93c0
ms.sourcegitcommit: 446fe2861651f51a129baa80791f565f81b4f317
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/12/2018
---
# <a name="enter-add-on-properties"></a><span data-ttu-id="15709-103">Eingeben von Add-On-Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="15709-103">Enter add-on properties</span></span>


<span data-ttu-id="15709-104">Beim Übermitteln eines Add-Ons sind die Optionen auf der Seite **Eigenschaften** hilfreich, um das Verhalten Ihres Add-Ons festzulegen, wenn es Kunden angeboten wird.</span><span class="sxs-lookup"><span data-stu-id="15709-104">When submitting an add-on, the options on the **Properties** page help determine the behavior of your add-on when offered to customers.</span></span>

## <a name="product-type"></a><span data-ttu-id="15709-105">Produkttyp</span><span class="sxs-lookup"><span data-stu-id="15709-105">Product type</span></span>

<span data-ttu-id="15709-106">Beim ersten [Erstellen des Add-Ons](set-your-add-on-product-id.md) wird der Produkttyp ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="15709-106">Your product type is selected when you first [create the add-on](set-your-add-on-product-id.md).</span></span> <span data-ttu-id="15709-107">Der ausgewählte Produkttyp wird hier angezeigt, Sie können ihn jedoch nicht ändern.</span><span class="sxs-lookup"><span data-stu-id="15709-107">The product type you selected is displayed here, but you can't change it.</span></span>

> [!TIP]
> <span data-ttu-id="15709-108">Hinweis Wenn Sie das Add-On nicht veröffentlicht haben, können Sie die Übermittlung löschen und von vorne beginnen, falls Sie einen anderen Produkttyp auswählen möchten.</span><span class="sxs-lookup"><span data-stu-id="15709-108">If you haven't published the add-on, you can delete the submission and start again if you want to choose a different product type.</span></span>

<span data-ttu-id="15709-109">Die Felder, die Sie auf dieser Seite sehen, variieren je nach den Produkttyp Ihres Add-Ons.</span><span class="sxs-lookup"><span data-stu-id="15709-109">The fields you see on this page will vary, depending on the product type of your add-on.</span></span>


## <a name="product-lifetime"></a><span data-ttu-id="15709-110">Produktlebensdauer</span><span class="sxs-lookup"><span data-stu-id="15709-110">Product lifetime</span></span>

<span data-ttu-id="15709-111">Wenn Sie als Produkttyp **Gebrauchsgut** ausgewählt haben, wird hier die **Produktlebenszeit** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="15709-111">If you selected **Durable** for your product type, **Product lifetime** is shown here.</span></span> <span data-ttu-id="15709-112">Die standardmäßige **Produktlebenszeit** dauerhafter Add-Ons ist **Unbegrenzt**. Das Add-On läuft also niemals ab.</span><span class="sxs-lookup"><span data-stu-id="15709-112">The default **Product lifetime** for a durable add-on is **Forever**, which means the add-on never expires.</span></span> <span data-ttu-id="15709-113">Sie können die **Produktlebenszeit** auch festlegen, sodass das Add-On nach einem festgelegten Zeitraum abläuft (mögliche Optionen: 1 bis 365Tage).</span><span class="sxs-lookup"><span data-stu-id="15709-113">If you prefer, you can set the **Product lifetime** so that the add-on expires after a set duration (with options from 1-365 days).</span></span>


## <a name="quantity"></a><span data-ttu-id="15709-114">Menge</span><span class="sxs-lookup"><span data-stu-id="15709-114">Quantity</span></span>

<span data-ttu-id="15709-115">Wenn Sie den Produkttyp **Vom Store verwalteter Verbrauchsartikel** ausgewählt haben, wird hier die **Menge** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="15709-115">If you selected **Store-managed consumable** for your product type, **Quantity** is shown here.</span></span> <span data-ttu-id="15709-116">Sie müssen eine Zahl zwischen 1 und 1000000 eingeben.</span><span class="sxs-lookup"><span data-stu-id="15709-116">You'll need to enter a number between 1 and 1000000.</span></span> <span data-ttu-id="15709-117">Diese Menge wird Kunden gewährt, wenn sie Ihr Add-On erwerben, und vom Store wird der Betrag nachverfolgt, wenn die App die Nutzung des Add-Ons durch Kunden meldet.</span><span class="sxs-lookup"><span data-stu-id="15709-117">This quantity will be granted to the customer when they acquire your add-on, and the Store will track the balance as the app reports the customer’s consumption of the add-on.</span></span>


## <a name="subscription-period"></a><span data-ttu-id="15709-118">Abonnementdauer</span><span class="sxs-lookup"><span data-stu-id="15709-118">Subscription period</span></span>

<span data-ttu-id="15709-119">Wenn Sie als Produkttyp **Abonnement** ausgewählt haben, wird hier die **Abonnementdauer** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="15709-119">If you selected **Subscription** for your product type, **Subscription period** is shown here.</span></span> <span data-ttu-id="15709-120">Wählen Sie eine Option aus, um anzugeben, wie häufig der Kunde für das Abonnement in Rechnung gestellt wird.</span><span class="sxs-lookup"><span data-stu-id="15709-120">Choose an option to specify how frequently a customer will be charged for the subscription.</span></span> <span data-ttu-id="15709-121">Die Standardoption ist **monatlich, aber Sie können auch **3 Monate**, **6 Monate**, **Jährlich** oder **24 Monate** auswählen</span><span class="sxs-lookup"><span data-stu-id="15709-121">The default option is **Monthly, but you can also select **3 months**, **6 months**, **Annually**, or **24 months** to</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="15709-122">Sie können nach der Veröffentlichung Ihres Add-Ons Ihre **Abonnementdauer** auswählen.</span><span class="sxs-lookup"><span data-stu-id="15709-122">After your add-on is published, you can't change your **Subscription period** selection.</span></span>


## <a name="free-trial"></a><span data-ttu-id="15709-123">Kostenlose Testversion</span><span class="sxs-lookup"><span data-stu-id="15709-123">Free trial</span></span>

<span data-ttu-id="15709-124">Wenn Sie als Produkttyp **Abonnement** ausgewählt haben, wird hier die **Kostenlos testen** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="15709-124">If you selected **Subscription** for your product type, **Free trial** is also shown here.</span></span> <span data-ttu-id="15709-125">Die Standardoption ist **Keine kostenlose Testversion.**</span><span class="sxs-lookup"><span data-stu-id="15709-125">The default option is **No free trial.**</span></span> <span data-ttu-id="15709-126">Falls gewünscht, können Kunden das Add-On für einen festgelegten Zeitraum kostenlos verwenden (entweder **1 Woche** oder **1 Monat**).</span><span class="sxs-lookup"><span data-stu-id="15709-126">If you prefer, you can let customers use the add-on for free for a set period of time (either **1 week** or **1 month**).</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="15709-127">Sie können nach der Veröffentlichung Ihres Add-Ons Ihre **Kostenlose Testversion** auswählen.</span><span class="sxs-lookup"><span data-stu-id="15709-127">After your add-on is published, you can't change your **Free trial** selection.</span></span>


## <a name="content-type"></a><span data-ttu-id="15709-128">Inhaltstyp</span><span class="sxs-lookup"><span data-stu-id="15709-128">Content type</span></span>

<span data-ttu-id="15709-129">Unabhängig vom Produkttyp Ihres Add-Ons müssen Sie die Art der Inhalte angeben, die Sie anbieten.</span><span class="sxs-lookup"><span data-stu-id="15709-129">Regardless of your add-on's product type, you'll need to indicate the type of content you're offering.</span></span> <span data-ttu-id="15709-130">Für die meisten Add-Ons sollte der Inhaltstyp **Download elektronischer Software** lauten.</span><span class="sxs-lookup"><span data-stu-id="15709-130">For most add-ons, the content type should be **Electronic software download**.</span></span> <span data-ttu-id="15709-131">Wenn eine andere Option aus der Liste Ihr Add-On besser beschreibt (wenn Sie z.B. einen Musikdownload oder ein E-Book anbieten), wählen Sie stattdessen diese Option.</span><span class="sxs-lookup"><span data-stu-id="15709-131">If another option from the list describes your add-on better (for example, if you are offering a music download or an e-book), select that option instead.</span></span>

<span data-ttu-id="15709-132">Mögliche Optionen für den Inhaltstyp eines Add-Ons:</span><span class="sxs-lookup"><span data-stu-id="15709-132">These are the possible options for an add-on's content type:</span></span>

-   <span data-ttu-id="15709-133">Download elektronischer Software</span><span class="sxs-lookup"><span data-stu-id="15709-133">Electronic software download</span></span>
-   <span data-ttu-id="15709-134">Elektronische Bücher</span><span class="sxs-lookup"><span data-stu-id="15709-134">Electronic books</span></span>
-   <span data-ttu-id="15709-135">Einzelausgabe einer elektronischen Zeitschrift</span><span class="sxs-lookup"><span data-stu-id="15709-135">Electronic magazine single issue</span></span>
-   <span data-ttu-id="15709-136">Einzelausgabe einer elektronischen Zeitung</span><span class="sxs-lookup"><span data-stu-id="15709-136">Electronic newspaper single issue</span></span>
-   <span data-ttu-id="15709-137">Musikdownload</span><span class="sxs-lookup"><span data-stu-id="15709-137">Music download</span></span>
-   <span data-ttu-id="15709-138">Musikstreaming</span><span class="sxs-lookup"><span data-stu-id="15709-138">Music streaming</span></span>
-   <span data-ttu-id="15709-139">Onlinedatenspeicher/-dienste</span><span class="sxs-lookup"><span data-stu-id="15709-139">Online data storage/services</span></span>
-   <span data-ttu-id="15709-140">Software as a Service</span><span class="sxs-lookup"><span data-stu-id="15709-140">Software as a service</span></span>
-   <span data-ttu-id="15709-141">Videodownload</span><span class="sxs-lookup"><span data-stu-id="15709-141">Video download</span></span>
-   <span data-ttu-id="15709-142">Videostreaming</span><span class="sxs-lookup"><span data-stu-id="15709-142">Video streaming</span></span>


## <a name="additional-properties"></a><span data-ttu-id="15709-143">Weitere Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="15709-143">Additional properties</span></span>

<span data-ttu-id="15709-144">Diese Felder sind optional für alle Arten von Add-Ons.</span><span class="sxs-lookup"><span data-stu-id="15709-144">These fields are optional for all types of add-ons.</span></span>

<span id="keywords" />
### <a name="keywords"></a><span data-ttu-id="15709-145">Schlüsselwörter</span><span class="sxs-lookup"><span data-stu-id="15709-145">Keywords</span></span>

<span data-ttu-id="15709-146">Sie können für jedes eingereichte Add-On bis zu zehn Schlüsselwörter von jeweils bis zu 30 Zeichen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="15709-146">You have the option to provide up to ten keywords of up to 30 characters each for each add-on you submit.</span></span> <span data-ttu-id="15709-147">Danach kann Ihre App nach Add-Ons suchen, die diesen Schlüsselwörtern entsprechen.</span><span class="sxs-lookup"><span data-stu-id="15709-147">Your app can then query for add-ons that match these words.</span></span> <span data-ttu-id="15709-148">Durch dieses Feature können Sie Bildschirme in Ihrer App erstellen, die Add-Ons laden können, ohne dass Sie die Produkt-ID im App-Code direkt angeben müssen.</span><span class="sxs-lookup"><span data-stu-id="15709-148">This feature lets you build screens in your app that can load add-ons without you having to directly specify the product ID in your app's code.</span></span> <span data-ttu-id="15709-149">Sie können die Schlüsselwörter des Add-Ons später jederzeit ändern, ohne Codeänderungen an der App vorzunehmen oder die App erneut einzureichen.</span><span class="sxs-lookup"><span data-stu-id="15709-149">You can then change the add-on's keywords anytime, without having to make code changes in your app or submit the app again.</span></span>

<span data-ttu-id="15709-150">Verwenden Sie zur Abfrage des Felds die Eigenschaft [StoreProduct.Keywords](https://docs.microsoft.com/uwp/api/windows.services.store.storeproduct#Windows_Services_Store_StoreProduct_Keywords) in [Windows.Services.Store namespace](https://msdn.microsoft.com/en-us/library/windows/apps/windows.services.store.aspx).</span><span class="sxs-lookup"><span data-stu-id="15709-150">To query this field, use the [StoreProduct.Keywords](https://docs.microsoft.com/uwp/api/windows.services.store.storeproduct#Windows_Services_Store_StoreProduct_Keywords) property in the [Windows.Services.Store namespace](https://msdn.microsoft.com/en-us/library/windows/apps/windows.services.store.aspx).</span></span> <span data-ttu-id="15709-151">(Wenn Sie [Windows.ApplicationModel.Store-Namespace](https://msdn.microsoft.com/en-us/library/windows/apps/windows.applicationmodel.store.aspx) verwenden, nutzen Sie die Eigenschaft [ProductListing.Keywords](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.productlisting#Windows_ApplicationModel_Store_ProductListing_Keywords).)</span><span class="sxs-lookup"><span data-stu-id="15709-151">(Or, if you're using the [Windows.ApplicationModel.Store namespace](https://msdn.microsoft.com/en-us/library/windows/apps/windows.applicationmodel.store.aspx), use the [ProductListing.Keywords](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.productlisting#Windows_ApplicationModel_Store_ProductListing_Keywords) property.)</span></span>

> [!NOTE]
> <span data-ttu-id="15709-152">Schlüsselwörter stehen für Pakete, die auf Windows 8 und Windows 8.1 ausgerichtet sind, nicht zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="15709-152">Keywords are not available for use in packages targeting Windows 8 and Windows 8.1.</span></span>

<span id="custom-developer-data" />
### <a name="custom-developer-data"></a><span data-ttu-id="15709-153">Benutzerdefinierte Entwicklerdaten</span><span class="sxs-lookup"><span data-stu-id="15709-153">Custom developer data</span></span>

<span data-ttu-id="15709-154">Sie können im Feld **Benutzerdefinierte Entwicklerdaten** (früher **Tag**) bis zu 3.000 Zeichen eingeben, um zusätzlichen Kontext für das In-App-Produkt bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="15709-154">You can enter up to 3000 characters into the **Custom developer data** field (formerly called **Tag**) to provide extra context for your in-app product.</span></span> <span data-ttu-id="15709-155">Meistens handelt es sich um eine XML-Zeichenfolge. Sie können aber beliebige Inhalte eingeben.</span><span class="sxs-lookup"><span data-stu-id="15709-155">Most often, this is in the form of an XML string, but you can enter anything you'd like in this field.</span></span> <span data-ttu-id="15709-156">Ihre App kann dann dieses Feld abfragen, um den Inhalt zu lesen (auch wenn die App die Daten nicht bearbeiten kann und die Änderungen zurückgibt.)</span><span class="sxs-lookup"><span data-stu-id="15709-156">Your app can then query this field to read its content (although the app can't edit the data and pass the changes back.)</span></span>

<span data-ttu-id="15709-157">Nehmen Sie beispielsweise an, dass Sie ein Spiel anbieten und Add-Ons verkaufen, wodurch Kunden auf zusätzliche Ebenen zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="15709-157">For example, let’s say you have a game, and you’re selling an add-on which allows the customer to access additional levels.</span></span> <span data-ttu-id="15709-158">Mithilfe des Felds **Benutzerdefinierte Entwicklerdaten** kann die App abfragen, welche Ebenen verfügbar sind, wenn ein Kunde dieses Add-On erwirbt.</span><span class="sxs-lookup"><span data-stu-id="15709-158">Using the **Custom developer data** field, the app can query to see which levels are available when a customer owns this add-on.</span></span> <span data-ttu-id="15709-159">Sie können den Wert jederzeit anpassen (in diesem Fall die zugefügten Ebenen), ohne den Code der App zu ändern oder die App erneut zu übermitteln, indem Sie die Informationen im Feld **Benutzerdefinierte Entwicklerdaten** aktualisieren und dann eine aktualisierte Übermittlung für das Add-On veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="15709-159">You could adjust the value at any time (in this case, the levels which are included), without having to make code changes in your app or submit the app again, by updating the info in the add-on's **Custom developer data** field and then publishing an updated submission for the add-on.</span></span>

<span data-ttu-id="15709-160">Verwenden Sie zur Abfrage des Felds die Eigenschaft [StoreSku.CustomDeveloperData](https://msdn.microsoft.com/en-us/library/windows/apps/windows.services.store.storesku.customdeveloperdata.aspx) unter [Windows.Services.Store namespace](https://msdn.microsoft.com/en-us/library/windows/apps/windows.services.store.aspx).</span><span class="sxs-lookup"><span data-stu-id="15709-160">To query this field, use the [StoreSku.CustomDeveloperData](https://msdn.microsoft.com/en-us/library/windows/apps/windows.services.store.storesku.customdeveloperdata.aspx) property in the [Windows.Services.Store namespace](https://msdn.microsoft.com/en-us/library/windows/apps/windows.services.store.aspx).</span></span> <span data-ttu-id="15709-161">(Wenn Sie [Windows.ApplicationModel.Store-Namespace](https://msdn.microsoft.com/en-us/library/windows/apps/windows.applicationmodel.store.aspx) verwenden, nutzen Sie die Eigenschaft [ProductListing.Tag](https://msdn.microsoft.com/en-us/library/windows/apps/windows.applicationmodel.store.productlisting.tag.aspx).)</span><span class="sxs-lookup"><span data-stu-id="15709-161">(Or, if you're using the [Windows.ApplicationModel.Store namespace](https://msdn.microsoft.com/en-us/library/windows/apps/windows.applicationmodel.store.aspx), use the [ProductListing.Tag](https://msdn.microsoft.com/en-us/library/windows/apps/windows.applicationmodel.store.productlisting.tag.aspx) property.)</span></span>

> [!NOTE]
> <span data-ttu-id="15709-162">Das Feld **Benutzerdefinierte Entwicklerdaten** ist nicht in Paketen verfügbar, die für Windows8 und Windows8.1 entwickelt wurden.</span><span class="sxs-lookup"><span data-stu-id="15709-162">The **Custom developer data** field is not available for use in packages targeting Windows 8 and Windows 8.1.</span></span>

 

 

 
