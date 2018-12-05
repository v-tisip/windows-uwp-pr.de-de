---
ms.assetid: 63A9EDCF-A418-476C-8677-D8770B45D1D7
description: Mit dem Microsoft Advertising-SDK haben Sie mehrere Möglichkeiten zur Monetarisierung Ihrer App mit Anzeigen.
title: Zeigt Werbung mithilfe der Microsoft Advertising-SDK in Ihrer App an
ms.date: 06/20/2018
ms.topic: article
keywords: Windows10, UWP, Anzeigen, Werbung, banner, Anzeigensteuerelement,Interstitial
ms.localizationpriority: medium
ms.openlocfilehash: baf26335ccdf34c8403cc15ecc1e68527d92e90e
ms.sourcegitcommit: c01c29cd97f1cbf050950526e18e15823b6a12a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8696518"
---
# <a name="display-ads-in-your-app-with-the-microsoft-advertising-sdk"></a><span data-ttu-id="5ac1e-104">Zeigt Werbung mithilfe der Microsoft Advertising-SDK in Ihrer App an</span><span class="sxs-lookup"><span data-stu-id="5ac1e-104">Display ads in your app with the Microsoft Advertising SDK</span></span>

<span data-ttu-id="5ac1e-105">Erhöhen Sie Ihre Umsatzchancen, indem Sie mithilfe des Microsoft Advertising-SDKs Anzeigen in Ihre universelle Windows-Plattform-App für Windows 10 einfügen.</span><span class="sxs-lookup"><span data-stu-id="5ac1e-105">Increase your revenue opportunities by putting ads in your Universal Windows Platform (UWP) app for Windows 10 by using the Microsoft Advertising SDK.</span></span> <span data-ttu-id="5ac1e-106">Unsere anzeigen-monetarisierungsplattform bietet eine Vielzahl von Ad-Formate, die nahtlos in Ihre apps und unterstützt die anzeigenvermittlung mit unterschiedlichen beliebten Anzeigennetzwerken integriert werden kann.</span><span class="sxs-lookup"><span data-stu-id="5ac1e-106">Our ad monetization platform offers a variety of ad formats that can be seamlessly integrated into your apps and supports mediation with many popular ad networks.</span></span> <span data-ttu-id="5ac1e-107">Unsere Plattform ist kompatibel mit OpenRTB, große 2.x, MRAID 2 und 3 VPAID Standards und ist kompatibel mit MOAT und IAS.</span><span class="sxs-lookup"><span data-stu-id="5ac1e-107">Our platform is compliant with the OpenRTB, VAST 2.x, MRAID 2, and VPAID 3 standards and is compatible with MOAT and IAS.</span></span> 

<br/>

<table style="border: none !important;">
<colgroup>
<col width="10%" />
<col width="23%" />
<col width="10%" />
<col width="23%" />
<col width="10%" />
<col width="23%" />
</colgroup>
<tbody>
<tr>
<td align="left"><img src="images/install-sdk.png" alt="Install SDK icon" /></td>
<td align="left"><b><span data-ttu-id="5ac1e-108">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="5ac1e-108">Get started</span></span></b><br/><br/>
    <a href="http://aka.ms/ads-sdk-uwp"><span data-ttu-id="5ac1e-109">Installieren des Microsoft Advertising-SDK</span><span class="sxs-lookup"><span data-stu-id="5ac1e-109">Install the Microsoft Advertising SDK</span></span></a>
</td>
<td align="left"><img src="images/write-code.png" alt="Develop icon" /></td>
<td align="left"><b><span data-ttu-id="5ac1e-110">Entwicklerhandbuch</span><span class="sxs-lookup"><span data-stu-id="5ac1e-110">Developer guides</span></span></b><br/><br/>
    <a href="banner-ads.md"><span data-ttu-id="5ac1e-111">Banneranzeigen</span><span class="sxs-lookup"><span data-stu-id="5ac1e-111">Banner ads</span></span></a>
    <br/>
    <a href="interstitial-ads.md"><span data-ttu-id="5ac1e-112">Interstitialwerbung</span><span class="sxs-lookup"><span data-stu-id="5ac1e-112">Interstitial ads</span></span></a>
    <br/>
    <a href="native-ads.md"><span data-ttu-id="5ac1e-113">Native Anzeigen</span><span class="sxs-lookup"><span data-stu-id="5ac1e-113">Native ads</span></span></a>
    </td>
<td align="left"><img src="images/api-reference.png" alt="API ref icon" /></td>
<td align="left"><b><span data-ttu-id="5ac1e-114">Weitere Ressourcen</span><span class="sxs-lookup"><span data-stu-id="5ac1e-114">Other resources</span></span></b><br/><br/>
    <a href="set-up-ad-units-in-your-app.md"><span data-ttu-id="5ac1e-115">Einrichten von Anzeigenblöcken in der App</span><span class="sxs-lookup"><span data-stu-id="5ac1e-115">Set up ad units in your app</span></span></a>
    <br/>
    <a href="best-practices-for-ads-in-apps.md"><span data-ttu-id="5ac1e-116">Bewährte Verfahren</span><span class="sxs-lookup"><span data-stu-id="5ac1e-116">Best practices</span></span></a>
    <br/>
    <a href="https://msdn.microsoft.com/en-us/library/windows/apps/mt691884.aspx"><span data-ttu-id="5ac1e-117">API-Referenz</span><span class="sxs-lookup"><span data-stu-id="5ac1e-117">API reference</span></span></a>
    </td>
</tr>
</tbody>
</table>

## <a name="step-1-install-the-microsoft-advertising-sdk"></a><span data-ttu-id="5ac1e-118">Schritt 1: Installieren des Microsoft Advertising-SDK</span><span class="sxs-lookup"><span data-stu-id="5ac1e-118">Step 1: Install the Microsoft Advertising SDK</span></span>

<span data-ttu-id="5ac1e-119">Installieren Sie zunächst die [Microsoft Advertising-SDK](http://aka.ms/ads-sdk-uwp) auf dem Entwicklungscomputer, den Sie verwenden, um Ihre App zu entwickeln.</span><span class="sxs-lookup"><span data-stu-id="5ac1e-119">To get started, install the [Microsoft Advertising SDK](http://aka.ms/ads-sdk-uwp) on the development computer you use to build your app.</span></span> <span data-ttu-id="5ac1e-120">Installationsanweisungen finden Sie in [diesem Artikel](install-the-microsoft-advertising-libraries.md).</span><span class="sxs-lookup"><span data-stu-id="5ac1e-120">For installation instructions, see [this article](install-the-microsoft-advertising-libraries.md).</span></span>

## <a name="step-2-implement-ads-in-your-app"></a><span data-ttu-id="5ac1e-121">Schritt 2: Implementieren von Werbung in Ihrer App</span><span class="sxs-lookup"><span data-stu-id="5ac1e-121">Step 2: Implement ads in your app</span></span>

<span data-ttu-id="5ac1e-122">Das Microsoft Advertising-SDK enthält verschiedene Arten von Anzeigenkontrollen, die in Ihrer App verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="5ac1e-122">The Microsoft Advertising SDK provides several different types of ad controls you can use in your app.</span></span> <span data-ttu-id="5ac1e-123">Wählen Sie, welche Arten von Anzeigen für Ihr Szenario am besten geeignet sind, und fügen Sie Code für Ihre App hinzu, um diese Anzeigen darzustellen.</span><span class="sxs-lookup"><span data-stu-id="5ac1e-123">Choose which types of ads are best for your scenario and then add code to your app to display those ads.</span></span> <span data-ttu-id="5ac1e-124">In diesem Schritt verwenden Sie eine Testanzeigeneinheit, um zu sehen, wie Ihre App die Anzeigen während der Testphase rendert.</span><span class="sxs-lookup"><span data-stu-id="5ac1e-124">During this step, you will use a test ad unit so you can see how your app renders ads during testing.</span></span>

### <a name="banner-ads"></a><span data-ttu-id="5ac1e-125">Banneranzeigen</span><span class="sxs-lookup"><span data-stu-id="5ac1e-125">Banner ads</span></span>

<span data-ttu-id="5ac1e-126">Es handelt sich um statische Anzeigen von Werbung, die einen rechteckigen Teil einer Seite in Ihrer App zum Anzeigen von Werbeinhalten nutzen.</span><span class="sxs-lookup"><span data-stu-id="5ac1e-126">These are static display ads that utilize a rectangular portion of a page in your app to display promotional content.</span></span> <span data-ttu-id="5ac1e-127">Diese Anzeigen können in regelmäßigen Abständen automatisch aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="5ac1e-127">These ads can refresh automatically at regular intervals.</span></span> <span data-ttu-id="5ac1e-128">Sie sind ein guter Ausgangspunkt, wenn Sie noch nicht mit Werbung in Ihrer App vertraut sind.</span><span class="sxs-lookup"><span data-stu-id="5ac1e-128">This is a good place to start if you are new to advertising in your app.</span></span>

<span data-ttu-id="5ac1e-129">Anweisungen und Codebeispiele finden Sie in [diesem Artikel](adcontrol-in-xaml-and--net.md).</span><span class="sxs-lookup"><span data-stu-id="5ac1e-129">For instructions and code examples, see [this article](adcontrol-in-xaml-and--net.md).</span></span>

![addreferences](images/banner-ad.png)

### <a name="interstitial-video-and-interstitial-banner-ads"></a><span data-ttu-id="5ac1e-131">Interstitialwerbung durch Videos und Banneranzeigen</span><span class="sxs-lookup"><span data-stu-id="5ac1e-131">Interstitial video and interstitial banner ads</span></span>

<span data-ttu-id="5ac1e-132">Interstitialanzeigen sind Vollbildanzeigen, durch die der Benutzer in der Regel gezwungen wird, sich ein Video anzusehen oder sich durch die Anzeige zu klicken, um mit der App oder dem Spiel fortfahren zu können.</span><span class="sxs-lookup"><span data-stu-id="5ac1e-132">These are full-screen ads that typically require the user to watch a video or click through them to continue in the app or game.</span></span> <span data-ttu-id="5ac1e-133">Wir unterstützen zwei Arten von Interstitialanzeigen: Videos und Banner.</span><span class="sxs-lookup"><span data-stu-id="5ac1e-133">We support two types of interstitial ads: video and banner.</span></span>

<span data-ttu-id="5ac1e-134">Anweisungen und Codebeispiele finden Sie in [diesem Artikel](interstitial-ads.md).</span><span class="sxs-lookup"><span data-stu-id="5ac1e-134">For instructions and code examples, see [this article](interstitial-ads.md).</span></span>

![addreferences](images/interstitial-ad.png)

### <a name="native-ads"></a><span data-ttu-id="5ac1e-136">Native Anzeigen</span><span class="sxs-lookup"><span data-stu-id="5ac1e-136">Native ads</span></span>

<span data-ttu-id="5ac1e-137">Hierbei handelt es sich um komponentenbasierte Anzeigen anzeigen.</span><span class="sxs-lookup"><span data-stu-id="5ac1e-137">These are component-based ads.</span></span> <span data-ttu-id="5ac1e-138">Jeder Teil des Anzeigen-Creatives (z. B. Titel, Bild, Beschreibung und Handlungsaufforderungstext) wird als einzelnes Element an Ihre App übermittelt. Sie können die Elemente mit eigenen Schriften, Farben und anderen UI-Komponenten in Ihre App integrieren.</span><span class="sxs-lookup"><span data-stu-id="5ac1e-138">Each piece of the ad creative (such as the title, image, description, and call-to-action text) is delivered to your app as an individual element that you can integrate into your app using your own fonts, colors, and other UI components.</span></span>

<span data-ttu-id="5ac1e-139">Anweisungen und Codebeispiele finden Sie in [diesem Artikel](native-ads.md).</span><span class="sxs-lookup"><span data-stu-id="5ac1e-139">For instructions and code examples, see [this article](native-ads.md).</span></span>

![addreferences](images/native-ad.png)

<span id="ad-mediation"/>

## <a name="step-3-create-an-ad-unit-and-configure-mediation"></a><span data-ttu-id="5ac1e-141">Schritt 3: Erstellen einer Anzeigeneinheit und Konfigurieren der Anzeigenvermittlung</span><span class="sxs-lookup"><span data-stu-id="5ac1e-141">Step 3: Create an ad unit and configure mediation</span></span>

<span data-ttu-id="5ac1e-142">Nachdem Sie Ihre app getestet und Sie sie an den Store übermitteln, erstellen Sie eine anzeigeneinheit auf der Seite [In-app-Werbung](../publish/in-app-ads.md) im Partner Center.</span><span class="sxs-lookup"><span data-stu-id="5ac1e-142">After you finish testing your app and you are ready to submit it to the Store, create an ad unit on the [In-app ads](../publish/in-app-ads.md) page in Partner Center.</span></span> <span data-ttu-id="5ac1e-143">Aktualisieren Sie anschließend Ihren App-Code, um diese Anzeigeneinheit zu verwenden, damit Ihre App Live-Anzeigen empfängt.</span><span class="sxs-lookup"><span data-stu-id="5ac1e-143">Then, update your app code to use this ad unit so that your app will receive live ads.</span></span> <span data-ttu-id="5ac1e-144">Weitere Informationen finden Sie unter [Einrichten von Anzeigeneinheiten in der App](set-up-ad-units-in-your-app.md#live-ad-units).</span><span class="sxs-lookup"><span data-stu-id="5ac1e-144">For more information, see [Set up ad units in your app](set-up-ad-units-in-your-app.md#live-ad-units).</span></span>

<span data-ttu-id="5ac1e-145">Standardmäßig zeigt Ihre App Werbung der Microsoft Netzwerke für kostenpflichtige Werbeanzeigen an.</span><span class="sxs-lookup"><span data-stu-id="5ac1e-145">By default, your app will show ads from Microsoft's network for paid ads.</span></span> <span data-ttu-id="5ac1e-146">Zur Maximierung Ihres Anzeigenumsatzes können Sie für Ihre Anzeigeneinheit die [Anzeigenvermittlung](ad-mediation-service.md) aktivieren, um kostenpflichtige Anzeigen von weiteren Anzeigennetzwerken anzuzeigen (z. B. Taboola und Smaato).</span><span class="sxs-lookup"><span data-stu-id="5ac1e-146">To maximize your ad revenue, you can enable [ad mediation](ad-mediation-service.md) for your ad unit to display ads from additional paid ad networks such as Taboola and Smaato.</span></span> <span data-ttu-id="5ac1e-147">Sie können Ihrer App-Werbung auch steigern, indem Sie Anzeigen aus Microsoft App-Werbekampagnen darstellen.</span><span class="sxs-lookup"><span data-stu-id="5ac1e-147">You can also increase your app promotion capabilities by serving ads from Microsoft app promotion campaigns.</span></span>

<span data-ttu-id="5ac1e-148">Zum Starten der Anzeigenvermittlung in Ihrer UWP-App [Konfigurieren Sie die Anzeigenvermittlungseinstellungen](../publish/in-app-ads.md#mediation-settings) für Ihre Anzeigeneinheit.</span><span class="sxs-lookup"><span data-stu-id="5ac1e-148">To start using ad mediation in your UWP app, [configure ad mediation settings](../publish/in-app-ads.md#mediation-settings) for your ad unit.</span></span> <span data-ttu-id="5ac1e-149">Standardmäßig werden die Einstellungen für die Anzeigenvermittlung automatisch mithilfe von Machine Learning-Algorithmen konfiguriert, die ihnen bei der Optimierung der Anzeigenumsätze in den verschiedenen Märkten helfen, die Ihre App unterstützt.</span><span class="sxs-lookup"><span data-stu-id="5ac1e-149">By default, we automatically configure the mediation settings using machine-learning algorithms to help you maximize your ad revenue across the markets your app supports.</span></span> <span data-ttu-id="5ac1e-150">Sie haben jedoch auch die Möglichkeit, die gewünschten Netzwerke manuell auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="5ac1e-150">However, you also have the option to manually choose the networks you want to use.</span></span> <span data-ttu-id="5ac1e-151">In beiden Fällen werden die Einstellungen für die Anzeigenvermittlung vollständig auf unseren Servern konfiguriert; Sie müssen keine Codes in Ihrer App ändern.</span><span class="sxs-lookup"><span data-stu-id="5ac1e-151">Either way, the mediation settings are configured entirely on our servers; you do not need to make any code changes in your app.</span></span>    

## <a name="step-4-submit-your-app-and-review-performance"></a><span data-ttu-id="5ac1e-152">Schritt 4: Übermitteln der App und Überprüfen der Leistung</span><span class="sxs-lookup"><span data-stu-id="5ac1e-152">Step 4: Submit your app and review performance</span></span>

<span data-ttu-id="5ac1e-153">Nach Abschluss der Entwicklung Ihrer Apps mit anzeigen, können Sie [die aktualisierte app übermitteln](https://docs.microsoft.com/windows/uwp/publish/app-submissions) , im Partner Center im Store verfügbar machen.</span><span class="sxs-lookup"><span data-stu-id="5ac1e-153">After you finish developing your app with ads, you can [submit your updated app](https://docs.microsoft.com/windows/uwp/publish/app-submissions) in Partner Center to make it available in the Store.</span></span> <span data-ttu-id="5ac1e-154">Apps, die Anzeigen darstellen, müssen zusätzlich die Anforderungen erfüllen, die in [Abschnitt 10.10 der Microsoft Store-Richtlinien](https://docs.microsoft.com/legal/windows/agreements/store-policies#1010-advertising-conduct-and-content) [Anlage E der Vereinbarung für App-Entwickler](https://docs.microsoft.com/legal/windows/agreements/app-developer-agreement) angegeben sind.</span><span class="sxs-lookup"><span data-stu-id="5ac1e-154">Apps that display ads must meet the additional requirements that are specified in [section 10.10 of the Microsoft Store Policies](https://docs.microsoft.com/legal/windows/agreements/store-policies#1010-advertising-conduct-and-content) and [Exhibit E of the App Developer Agreement](https://docs.microsoft.com/legal/windows/agreements/app-developer-agreement).</span></span>

<span data-ttu-id="5ac1e-155">Nachdem Ihre app im Store veröffentlicht und verfügbar ist, können Sie Ihre [Berichte zur anzeigenleistung](../publish/advertising-performance-report.md) im Partner Center überprüfen und Änderungen an den für die anzeigenvermittlung zur Optimierung der Leistung Ihrer anzeigen vornehmen.</span><span class="sxs-lookup"><span data-stu-id="5ac1e-155">After your app is published and available in the Store, you can review your [advertising performance reports](../publish/advertising-performance-report.md) in Partner Center and continue to make changes to your mediation settings to optimize the performance of your ads.</span></span> <span data-ttu-id="5ac1e-156">Der Umsatz befindet sich in der [Auszahlungszusammenfassung](../publish/payout-summary.md).</span><span class="sxs-lookup"><span data-stu-id="5ac1e-156">Your advertising revenue is included in your [payout summary](../publish/payout-summary.md).</span></span>

<span id="additional-help" />

## <a name="additional-help"></a><span data-ttu-id="5ac1e-157">Zusätzliche Hilfe</span><span class="sxs-lookup"><span data-stu-id="5ac1e-157">Additional help</span></span>

<span data-ttu-id="5ac1e-158">Weitere Hilfe zum Microsoft Advertising-SDK finden Sie in den folgenden Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="5ac1e-158">For additional help using the Microsoft Advertising SDK, use the following resources.</span></span>

|  <span data-ttu-id="5ac1e-159">Aufgabe</span><span class="sxs-lookup"><span data-stu-id="5ac1e-159">Task</span></span>    | <span data-ttu-id="5ac1e-160">Ressource</span><span class="sxs-lookup"><span data-stu-id="5ac1e-160">Resource</span></span> |               
|----------|-------|
| <span data-ttu-id="5ac1e-161">Melden eines Fehlers und Supportunterstützung für Werbung</span><span class="sxs-lookup"><span data-stu-id="5ac1e-161">Report a bug or get assisted support for advertising</span></span>     | <span data-ttu-id="5ac1e-162">Besuchen Sie die [Supportseite](https://developer.microsoft.com/en-us/windows/support), und wählen Sie **Werbung in Apps**.</span><span class="sxs-lookup"><span data-stu-id="5ac1e-162">Visit the [support page](https://developer.microsoft.com/en-us/windows/support) and choose **Ads-In-Apps**.</span></span>        |
| <span data-ttu-id="5ac1e-163">Community-Support erhalten</span><span class="sxs-lookup"><span data-stu-id="5ac1e-163">Get community support</span></span>     | <span data-ttu-id="5ac1e-164">Besuchen Sie das [Forum](http://go.microsoft.com/fwlink/p/?LinkId=401266).</span><span class="sxs-lookup"><span data-stu-id="5ac1e-164">Visit the [forum](http://go.microsoft.com/fwlink/p/?LinkId=401266).</span></span>       |
| <span data-ttu-id="5ac1e-165">Laden Sie Beispielprojekte herunter, die veranschaulichen, wie Sie Banner und Interstitialwerbung zu Apps hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="5ac1e-165">Download sample projects that demonstrate how to add banner and interstitial ads to apps.</span></span>     | <span data-ttu-id="5ac1e-166">Weitere Informationen finden Sie unter [Anzeigenbeispiele bei GitHub](http://aka.ms/githubads).</span><span class="sxs-lookup"><span data-stu-id="5ac1e-166">See the [Advertising samples on GitHub](http://aka.ms/githubads).</span></span>       |
| <span data-ttu-id="5ac1e-167">Weitere Informationen zu den neuesten Umsatzchancen für Windows-Apps</span><span class="sxs-lookup"><span data-stu-id="5ac1e-167">Learn about the latest monetization opportunities for Windows apps</span></span>     | <span data-ttu-id="5ac1e-168">Besuchen Sie Seite [Monetarisierung Ihrer Apps](https://developer.microsoft.com/store/monetize).</span><span class="sxs-lookup"><span data-stu-id="5ac1e-168">Visit [Monetize your apps](https://developer.microsoft.com/store/monetize).</span></span>        |

## <a name="windows-81-and-windows-phone-8x-apps"></a><span data-ttu-id="5ac1e-169">Windows 8.1 und Windows Phone 8.x-Apps</span><span class="sxs-lookup"><span data-stu-id="5ac1e-169">Windows 8.1 and Windows Phone 8.x apps</span></span>

<span data-ttu-id="5ac1e-170">Für Apps für Windows8.1 und Windows Phone8.x bieten wir das [Microsoft Advertising-SDK for Windows and Windows Phone 8.x](http://aka.ms/store-8-sdk).</span><span class="sxs-lookup"><span data-stu-id="5ac1e-170">For Windows 8.1 and Windows Phone 8.x apps, we provide the [Microsoft Advertising SDK for Windows and Windows Phone 8.x](http://aka.ms/store-8-sdk).</span></span> <span data-ttu-id="5ac1e-171">Weitere Informationen zur Verwendung des SDKs für Anzeigen in einer Windows8.1- oder Windows Phone8.x-App finden Sie in [diesem Artikel](https://docs.microsoft.com/en-us/previous-versions/windows/apps/dn792120(v=win.10)).</span><span class="sxs-lookup"><span data-stu-id="5ac1e-171">For more information about using this SDK to show ads in Windows 8.1 and Windows Phone 8.x apps, see [this article](https://docs.microsoft.com/en-us/previous-versions/windows/apps/dn792120(v=win.10)).</span></span>

## <a name="related-topics"></a><span data-ttu-id="5ac1e-172">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="5ac1e-172">Related topics</span></span>

* [<span data-ttu-id="5ac1e-173">MicrosoftAdvertising-SDK</span><span class="sxs-lookup"><span data-stu-id="5ac1e-173">Microsoft Advertising SDK</span></span>](http://aka.ms/ads-sdk-uwp)
* [<span data-ttu-id="5ac1e-174">Bericht zur Anzeigenleistung</span><span class="sxs-lookup"><span data-stu-id="5ac1e-174">Advertising performance report</span></span>](../publish/advertising-performance-report.md)
* [<span data-ttu-id="5ac1e-175">Programm für Herausgeber von Windows Premium-Anzeigen</span><span class="sxs-lookup"><span data-stu-id="5ac1e-175">Windows Premium Ads Publishers Program</span></span>](windows-premium-ads-publishers-program.md)
