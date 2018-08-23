---
author: jnHs
Description: You can help customers discover your app by linking to your app's listing in the Microsoft Store.
title: Erstellen eines Links zu Ihrer App
ms.assetid: 5420B65C-7ECE-4364-8959-D1683684E146
ms.author: wdg-dev-content
ms.date: 10/26/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Links, Windows Store-Protokoll, mit einer App verknüpfen, App verknüpfen
ms.localizationpriority: medium
ms.openlocfilehash: 0025321aa73a66cc0a976bd347e613de3c3c4765
ms.sourcegitcommit: 9c79fdab9039ff592edf7984732d300a14e81d92
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/23/2018
ms.locfileid: "2815630"
---
# <a name="link-to-your-app"></a><span data-ttu-id="d03b8-103">Erstellen eines Links zu Ihrer App</span><span class="sxs-lookup"><span data-stu-id="d03b8-103">Link to your app</span></span>


<span data-ttu-id="d03b8-104">Sie können Kunden Ihre app zu ermitteln, indem Sie zu Ihrer app Angebot in Microsoft Store verknüpfen.</span><span class="sxs-lookup"><span data-stu-id="d03b8-104">You can help customers discover your app by linking to your app's listing in the Microsoft Store.</span></span>

## <a name="getting-the-link-to-your-apps-store-listing"></a><span data-ttu-id="d03b8-105">Abrufen des Links zum Store-Eintrag Ihrer App</span><span class="sxs-lookup"><span data-stu-id="d03b8-105">Getting the link to your app's Store listing</span></span>

<span data-ttu-id="d03b8-106">Um die URL für den Store-Eintrag Ihrer App zu erhalten, wechseln Sie zur Seite der App [App-Identität](view-app-identity-details.md) im Abschnitt **App-Verwaltung**.</span><span class="sxs-lookup"><span data-stu-id="d03b8-106">To get the URL for your app's Store listing, navigate to the app's [App identity](view-app-identity-details.md) page in the **App management** section.</span></span> <span data-ttu-id="d03b8-107">Das URL-Format heißt **`https://www.microsoft.com/store/apps/<your app's Store ID>`**.</span><span class="sxs-lookup"><span data-stu-id="d03b8-107">The URL is in the format **`https://www.microsoft.com/store/apps/<your app's Store ID>`**.</span></span>

<span data-ttu-id="d03b8-108">Wenn ein Kunde auf diesen Link klickt, wird die webbasierte Eintragsseite für Ihre App geöffnet.</span><span class="sxs-lookup"><span data-stu-id="d03b8-108">When a customer clicks this link, it opens the web-based listing page for your app.</span></span> <span data-ttu-id="d03b8-109">Auf Windows-Geräten wird die Store-App auch ebenfalls Ihren App-Eintrag starten und anzeigen.</span><span class="sxs-lookup"><span data-stu-id="d03b8-109">On Windows devices, the Store app will also launch and display your app's listing.</span></span>


## <a name="linking-to-your-apps-store-listing-with-the-microsoft-store-badge"></a><span data-ttu-id="d03b8-110">Verknüpfen mit Ihrer app Store-Eintrags mit der Microsoft Store-Logo</span><span class="sxs-lookup"><span data-stu-id="d03b8-110">Linking to your app's Store listing with the Microsoft Store badge</span></span>

<span data-ttu-id="d03b8-111">Sie können Sie eine direkte Verknüpfung Ihrer app-Angebot mit einer benutzerdefinierten Logo können Kunden wissen, dass Ihre app im Store Microsoft ist.</span><span class="sxs-lookup"><span data-stu-id="d03b8-111">You can link directly to your app's listing with a custom badge to let customers know your app is in the Microsoft Store.</span></span>

<span data-ttu-id="d03b8-112">Wenn Ihr Logo erstellen möchten, finden Sie auf der Seite [Microsoft Store Badges](http://go.microsoft.com/fwlink/p/?LinkID=534236) .</span><span class="sxs-lookup"><span data-stu-id="d03b8-112">To create your badge, visit the [Microsoft Store badges](http://go.microsoft.com/fwlink/p/?LinkID=534236) page.</span></span> <span data-ttu-id="d03b8-113">Sie benötigen die zwölfstellige **Store-ID** Ihrer App, um dieses Formular zum Generieren von Badge und Link verwenden zu können.</span><span class="sxs-lookup"><span data-stu-id="d03b8-113">You'll need to have your app's 12-character **Store ID** in order to generate the badge and link.</span></span> <span data-ttu-id="d03b8-114">Die **Store ID** Ihrer App finden Sie auf der Seite [App-Identität](view-app-identity-details.md) unter **App-Verwaltung**.</span><span class="sxs-lookup"><span data-stu-id="d03b8-114">You can find your app's **Store ID** on the [App identity](view-app-identity-details.md) page in the **App management** section.</span></span>

> [!NOTE]
> <span data-ttu-id="d03b8-115">Info und Anforderungen in Bezug auf Ihre Verwendung des das Logo Microsoft Store finden Sie unter [App-marketing-Richtlinien](app-marketing-guidelines.md) .</span><span class="sxs-lookup"><span data-stu-id="d03b8-115">See [App marketing guidelines](app-marketing-guidelines.md) for info and requirements related to your use of the Microsoft Store badge.</span></span>


## <a name="linking-directly-to-your-app-in-the-microsoft-store"></a><span data-ttu-id="d03b8-116">Direkte Verknüpfung mit Ihrer app im Microsoft-Speicher</span><span class="sxs-lookup"><span data-stu-id="d03b8-116">Linking directly to your app in the Microsoft Store</span></span>

<span data-ttu-id="d03b8-117">Sie können einen Link, startet Microsoft Store und nehmen direkt an Ihre app-Angebotsseite ohne Öffnen eines Browsers mit, Erstellen der **ms-Windows-Store:** URI-Schema.</span><span class="sxs-lookup"><span data-stu-id="d03b8-117">You can create a link that launches the Microsoft Store and goes directly to your app's listing page without opening a browser by using the **ms-windows-store:** URI scheme.</span></span>

<span data-ttu-id="d03b8-118">Diese Links sind hilfreich, wenn Sie wissen, dass Benutzer Windows-Geräte verwenden, und möchten, dass sie direkt zur Eintragsseite im Store gelangen.</span><span class="sxs-lookup"><span data-stu-id="d03b8-118">These links are useful if you know your users are on a Windows device and you want them to arrive directly at the listing page in the Store.</span></span> <span data-ttu-id="d03b8-119">Sie sollten z.B. diesen Link verwenden, nachdem Sie die Zeichenfolge des Benutzer-Agent in einem Browser bestätigt haben, um zu überprüfen, dass das Betriebssystem des Benutzers den Store unterstützt, oder wenn Sie bereits über eine UWP-App kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="d03b8-119">For example, you might want to use this link after checking user agent strings in a browser to confirm that the user's operating system supports the Store, or when you are already communicating via a UWP app.</span></span>

<span data-ttu-id="d03b8-120">Um diese URI-Schema verwenden, um direkt mit Ihrer app-Shop zu verknüpfen, fügen Sie Ihrer app-ID anmelden zu diesem Link:</span><span class="sxs-lookup"><span data-stu-id="d03b8-120">To use this URI scheme to link directly to your app's Store listing, append your app's Store ID to this link:</span></span>

`ms-windows-store://pdp/?ProductId=`

<span data-ttu-id="d03b8-121">Weitere Informationen zur Verwendung des Microsoft Store-Protokolls finden Sie unter [Starten Sie die Microsoft-Anwendung](../launch-resume/launch-store-app.md).</span><span class="sxs-lookup"><span data-stu-id="d03b8-121">For more about using the Microsoft Store protocol, see [Launch the Microsoft app](../launch-resume/launch-store-app.md).</span></span>

 

 




