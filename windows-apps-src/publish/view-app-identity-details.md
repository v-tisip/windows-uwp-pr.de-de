---
author: jnHs
Description: View details related to the unique identity assigned to your app by the Microsoft Store, and get a link to your app's Store listing.
title: Anzeigen von Details zur App-Identität
ms.assetid: 86F05A79-EFBC-4705-9A71-3A056323AC65
ms.author: wdg-dev-content
ms.date: 10/02/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 4b04033fb53a90015427feb820c91d0f4a1de7d5
ms.sourcegitcommit: c4d3115348c8b54fcc92aae8e18fdabc3deb301d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2018
ms.locfileid: "5398469"
---
# <a name="view-app-identity-details"></a><span data-ttu-id="68f72-103">Anzeigen von Details zur App-Identität</span><span class="sxs-lookup"><span data-stu-id="68f72-103">View app identity details</span></span>


<span data-ttu-id="68f72-104">Sie können Details zur eindeutigen Identität zugewiesen an Ihre app vom Microsoft Store auf **App-Identität** Seiten anzeigen.</span><span class="sxs-lookup"><span data-stu-id="68f72-104">You can view details related to the unique identity assigned to your app by the Microsoft Store on its **App identity** pages.</span></span> <span data-ttu-id="68f72-105">Eintrag auf dieser Seite können Sie auch einen Link zu Ihrer app Store abrufen.</span><span class="sxs-lookup"><span data-stu-id="68f72-105">You can also get a link to your app's Store listing on this page.</span></span>

<span data-ttu-id="68f72-106">Um diese Informationen zu suchen, navigieren Sie zu einer Ihrer Apps und erweitern im linken Navigationsmenü **App-Verwaltung**.</span><span class="sxs-lookup"><span data-stu-id="68f72-106">To find this info, navigate to one of your apps, then expand **App management** in the left navigation menu.</span></span> <span data-ttu-id="68f72-107">Wählen Sie **App-Identität** aus, um diese Details anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="68f72-107">Select **App identity** to view these details.</span></span>


## <a name="values-to-include-in-your-app-package-manifest"></a><span data-ttu-id="68f72-108">In das App-Paketmanifest einzuschließende Werte</span><span class="sxs-lookup"><span data-stu-id="68f72-108">Values to include in your app package manifest</span></span>

<span data-ttu-id="68f72-109">Die folgenden Werte müssen im Paketmanifest enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="68f72-109">The following values must be included in your package manifest.</span></span> <span data-ttu-id="68f72-110">Wenn Sie Ihre [Pakete mit Microsoft Visual Studio erstellen](../packaging/packaging-uwp-apps.md) und mit demselben Microsoft-Konto angemeldet sind, das Sie mit Ihrem Entwicklerkonto verknüpft haben, werden diese Details automatisch eingefügt.</span><span class="sxs-lookup"><span data-stu-id="68f72-110">If you [use Microsoft Visual Studio to build your packages](../packaging/packaging-uwp-apps.md), and are signed in with the same Microsoft account that you have associated with your developer account, these details are included automatically.</span></span> <span data-ttu-id="68f72-111">Wenn Sie Ihr Paket manuell erstellen, müssen Sie folgende Details selbst hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="68f72-111">If you're building your package manually, you'll need to add these items:</span></span>

-   **<span data-ttu-id="68f72-112">Paket/Identität/Name</span><span class="sxs-lookup"><span data-stu-id="68f72-112">Package/Identity/Name</span></span>**
-   **<span data-ttu-id="68f72-113">Paket/Identität/Herausgeber</span><span class="sxs-lookup"><span data-stu-id="68f72-113">Package/Identity/Publisher</span></span>**
-   **<span data-ttu-id="68f72-114">Paket/Eigenschaften/PublisherDisplayName</span><span class="sxs-lookup"><span data-stu-id="68f72-114">Package/Properties/PublisherDisplayName</span></span>**

<span data-ttu-id="68f72-115">Weitere Informationen finden Sie unter [**Identity**](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-identity) in der [Paketmanifestschema-Referenz](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/schema-root).</span><span class="sxs-lookup"><span data-stu-id="68f72-115">For more info, see [**Identity**](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-identity) in the [package manifest schema reference](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/schema-root).</span></span>

<span data-ttu-id="68f72-116">Zusammen werden durch diese Elemente die Identität Ihrer App deklariert und die „Paketfamilie“ gebildet, der alle zugehörigen Pakete angehören.</span><span class="sxs-lookup"><span data-stu-id="68f72-116">Together, these elements declare the identity of your app, establishing the "package family" to which all of its packages belong.</span></span> <span data-ttu-id="68f72-117">Einzelne Pakete verfügen über zusätzliche Details, z.B. die Architektur und Version.</span><span class="sxs-lookup"><span data-stu-id="68f72-117">Individual packages will have additional details, such as architecture and version.</span></span>


## <a name="additional-values-for-package-family"></a><span data-ttu-id="68f72-118">Zusätzliche Werte für die Paketfamilie</span><span class="sxs-lookup"><span data-stu-id="68f72-118">Additional values for package family</span></span>

<span data-ttu-id="68f72-119">Die folgenden zusätzlichen Werte beziehen sich auf die Paketfamilie der App, werden aber nicht in Ihr Manifest eingeschlossen.</span><span class="sxs-lookup"><span data-stu-id="68f72-119">The following values are additional values that refer to your app's package family, but are not included in your manifest.</span></span>

-   <span data-ttu-id="68f72-120">**Paketfamilienname (PFN)**: Dieser Wert wird bei bestimmten Windows-APIs verwendet.</span><span class="sxs-lookup"><span data-stu-id="68f72-120">**Package Family Name (PFN)**: This value is used with certain Windows APIs.</span></span>
-   <span data-ttu-id="68f72-121">**Paket-SID**: Sie benötigen diesen Wert, um WNS-Benachrichtigungen an Ihre App zu senden.</span><span class="sxs-lookup"><span data-stu-id="68f72-121">**Package SID**: You'll need this value to send WNS notifications to your app.</span></span> <span data-ttu-id="68f72-122">Weitere Informationen finden Sie unter [Übersicht über den Windows-Pushbenachrichtigungsdienst (Windows Push Notification Service, WNS)](../design/shell/tiles-and-notifications/windows-push-notification-services--wns--overview.md).</span><span class="sxs-lookup"><span data-stu-id="68f72-122">For more info, see [Windows Push Notification Services (WNS) overview](../design/shell/tiles-and-notifications/windows-push-notification-services--wns--overview.md).</span></span>


## <a name="link-to-your-apps-listing"></a><span data-ttu-id="68f72-123">Erstellen eines Links zum Eintrag Ihrer App</span><span class="sxs-lookup"><span data-stu-id="68f72-123">Link to your app's listing</span></span>

<span data-ttu-id="68f72-124">Der direkte Link zu Ihrer App-Seite kann geteilt werden, um Kunden das Auffinden der App im Store zu erleichtern.</span><span class="sxs-lookup"><span data-stu-id="68f72-124">The direct link to your app's page can be shared to help your customers find the app in the Store.</span></span> <span data-ttu-id="68f72-125">Dieser Link hat das Format **`https://www.microsoft.com/store/apps/<your app's Store ID>`**.</span><span class="sxs-lookup"><span data-stu-id="68f72-125">This link is in the format **`https://www.microsoft.com/store/apps/<your app's Store ID>`**.</span></span> <span data-ttu-id="68f72-126">Wenn ein Kunde auf diesen Link klickt, wird die webbasierte Eintragsseite für Ihre App geöffnet.</span><span class="sxs-lookup"><span data-stu-id="68f72-126">When a customer clicks this link, it opens the web-based listing page for your app.</span></span> <span data-ttu-id="68f72-127">Auf Windows-Geräten wird die Store-App auch ebenfalls Ihren App-Eintrag starten und anzeigen.</span><span class="sxs-lookup"><span data-stu-id="68f72-127">On Windows devices, the Store app will also launch and display your app's listing.</span></span>

<span data-ttu-id="68f72-128">Die **Store-ID** Ihrer App wird in diesem Abschnitt auch angezeigt.</span><span class="sxs-lookup"><span data-stu-id="68f72-128">Your app's **Store ID** is also shown in this section.</span></span> <span data-ttu-id="68f72-129">Diese Store-ID kann dazu verwendet werden, [Store-Badges zu generieren](http://go.microsoft.com/fwlink/p/?LinkId=534236) oder Ihre App anderweitig zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="68f72-129">This Store ID can be used to [generate Store badges](http://go.microsoft.com/fwlink/p/?LinkId=534236) or otherwise identify your app.</span></span>

<span data-ttu-id="68f72-130">Das **Store-Protokolllink** kann verwendet werden, um Ihre App im Store direkt und ohne einen neuen Browser zu öffnen, als ob Sie es innerhalb der App verknüpfen.</span><span class="sxs-lookup"><span data-stu-id="68f72-130">The **Store protocol link** can be used to link directly to your app in the Store without opening a browser, such as when you are linking from within an app.</span></span> <span data-ttu-id="68f72-131">Weitere Informationen finden Sie unter [Erstellen eines Links zu Ihrer App](link-to-your-app.md).</span><span class="sxs-lookup"><span data-stu-id="68f72-131">For more info, see [Link to your app](link-to-your-app.md).</span></span>



 

 




