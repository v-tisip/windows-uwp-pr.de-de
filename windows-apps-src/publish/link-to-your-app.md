---
author: jnHs
Description: "Sie können Kunden helfen, Ihre App zu entdecken, indem Sie einen Link zum Store-Eintrag Ihrer App einfügen."
title: Erstellen eines Links zu Ihrer App
ms.assetid: 5420B65C-7ECE-4364-8959-D1683684E146
ms.author: wdg-dev-content
ms.date: 06/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows10, UWP, Links, Windows Store-Protokoll, mit einer App verknüpfen, App verknüpfen"
ms.openlocfilehash: 2d0750493926937a6326c5f72f568d4294b137c5
ms.sourcegitcommit: fadde8afee46238443ec1cb71846d36c91db9fb9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2017
---
# <a name="link-to-your-app"></a><span data-ttu-id="ed222-104">Erstellen eines Links zu Ihrer App</span><span class="sxs-lookup"><span data-stu-id="ed222-104">Link to your app</span></span>


<span data-ttu-id="ed222-105">Sie können Kunden helfen, Ihre App zu entdecken, indem Sie einen Link zum Store-Eintrag Ihrer App einfügen.</span><span class="sxs-lookup"><span data-stu-id="ed222-105">You can help customers discover your app by linking to your app's Store listing.</span></span>

## <a name="getting-the-link-to-your-apps-store-listing"></a><span data-ttu-id="ed222-106">Abrufen des Links zum Store-Eintrag Ihrer App</span><span class="sxs-lookup"><span data-stu-id="ed222-106">Getting the link to your app's Store listing</span></span>

<span data-ttu-id="ed222-107">Um die URL für den Store-Eintrag Ihrer App zu erhalten, wechseln Sie zur Seite der App [App-Identität](view-app-identity-details.md) im Abschnitt **App-Verwaltung**.</span><span class="sxs-lookup"><span data-stu-id="ed222-107">To get the URL for your app's Store listing, navigate to the app's [App identity](view-app-identity-details.md) page in the **App management** section.</span></span> <span data-ttu-id="ed222-108">Das URL-Format heißt **`https://www.microsoft.com/store/apps/<your app's Store ID>`**.</span><span class="sxs-lookup"><span data-stu-id="ed222-108">The URL is in the format **`https://www.microsoft.com/store/apps/<your app's Store ID>`**.</span></span>

<span data-ttu-id="ed222-109">Wenn ein Kunde auf diesen Link klickt, wird die webbasierte Eintragsseite für Ihre App geöffnet.</span><span class="sxs-lookup"><span data-stu-id="ed222-109">When a customer clicks this link, it opens the web-based listing page for your app.</span></span> <span data-ttu-id="ed222-110">Auf Windows-Geräten wird die Store-App auch ebenfalls Ihren App-Eintrag starten und anzeigen.</span><span class="sxs-lookup"><span data-stu-id="ed222-110">On Windows devices, the Store app will also launch and display your app's listing.</span></span>


## <a name="linking-to-your-apps-store-listing-with-the-windows-store-badge"></a><span data-ttu-id="ed222-111">Setzen eines Links zum Store-Eintrag Ihrer App mit dem Windows Store-Badge</span><span class="sxs-lookup"><span data-stu-id="ed222-111">Linking to your app's Store listing with the Windows Store badge</span></span>

<span data-ttu-id="ed222-112">Sie können mit einem benutzerdefinierten Badge einen direkten Link zum Eintrag Ihrer App erstellen, um Kunden darüber zu informieren, dass Ihre App im Windows Store vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="ed222-112">You can link directly to your app's listing with a custom badge to let customers know your app is in the Windows Store.</span></span>

<span data-ttu-id="ed222-113">Besuchen Sie zum Erstellen Ihres Badges die Seite [WindowsStore-Badges](http://go.microsoft.com/fwlink/p/?LinkID=534236).</span><span class="sxs-lookup"><span data-stu-id="ed222-113">To create your badge, visit the [Windows Store badges](http://go.microsoft.com/fwlink/p/?LinkID=534236) page.</span></span> <span data-ttu-id="ed222-114">Sie benötigen die zwölfstellige **Store-ID** Ihrer App, um dieses Formular zum Generieren von Badge und Link verwenden zu können.</span><span class="sxs-lookup"><span data-stu-id="ed222-114">You'll need to have your app's 12-character **Store ID** in order to generate the badge and link.</span></span> <span data-ttu-id="ed222-115">Die **Store ID** Ihrer App finden Sie auf der Seite [App-Identität](view-app-identity-details.md) unter **App-Verwaltung**.</span><span class="sxs-lookup"><span data-stu-id="ed222-115">You can find your app's **Store ID** on the [App identity](view-app-identity-details.md) page in the **App management** section.</span></span>

> [!NOTE]
> <span data-ttu-id="ed222-116">Weitere Informationen und Anforderungen in Bezug auf Ihre Verwendung der Windows Store-Signals finden Sie unter [Marketingrichtlinien für Apps](app-marketing-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="ed222-116">See [App marketing guidelines](app-marketing-guidelines.md) for info and requirements related to your use of the Windows Store badge.</span></span>


## <a name="linking-directly-to-your-app-in-the-windows-store"></a><span data-ttu-id="ed222-117">Erstellen direkter Links zum Windows Store</span><span class="sxs-lookup"><span data-stu-id="ed222-117">Linking directly to your app in the Windows Store</span></span>

<span data-ttu-id="ed222-118">Sie können unter Verwendung des **ms-windows-store:**-URI-Schemas einen Link erstellen, der den Windows Store öffnet und direkt zur Eintragsseite Ihrer App wechselt.</span><span class="sxs-lookup"><span data-stu-id="ed222-118">You can create a link that launches the Windows Store and goes directly to your app's listing page without opening a browser by using the **ms-windows-store:** URI scheme.</span></span>

<span data-ttu-id="ed222-119">Diese Links sind hilfreich, wenn Sie wissen, dass Benutzer Windows-Geräte verwenden, und möchten, dass sie direkt zur Eintragsseite im Store gelangen.</span><span class="sxs-lookup"><span data-stu-id="ed222-119">These links are useful if you know your users are on a Windows device and you want them to arrive directly at the listing page in the Store.</span></span> <span data-ttu-id="ed222-120">Sie sollten z.B. diesen Link verwenden, nachdem Sie die Zeichenfolge des Benutzer-Agent in einem Browser bestätigt haben, um zu überprüfen, dass das Betriebssystem des Benutzers den Store unterstützt, oder wenn Sie bereits über eine UWP-App kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="ed222-120">For example, you might want to use this link after checking user agent strings in a browser to confirm that the user's operating system supports the Store, or when you are already communicating via a UWP app.</span></span>

<span data-ttu-id="ed222-121">Um das Windows Store-Protokoll für einen direkten Link mit dem Store-Eintrag Ihrer App zu verwenden, fügen Sie diesem Link die Store-ID der App hinzu:</span><span class="sxs-lookup"><span data-stu-id="ed222-121">To use the Windows Store protocol to link directly to your app's Store listing, append your app's Store ID to this link:</span></span>

`ms-windows-store://pdp/?ProductId=`

<span data-ttu-id="ed222-122">Weitere Informationen zur Verwendung des Windows Store-Protokolls finden Sie unter [Starten der Windows Store-App](../launch-resume/launch-store-app.md).</span><span class="sxs-lookup"><span data-stu-id="ed222-122">For more about using the Windows Store protocol, see [Launch the Windows Store app](../launch-resume/launch-store-app.md).</span></span>

 

 




