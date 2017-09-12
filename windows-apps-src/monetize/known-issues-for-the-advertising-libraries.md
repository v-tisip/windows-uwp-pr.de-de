---
author: mcleanbyron
ms.assetid: 9ca1f880-2ced-46b4-8ea7-aba43d2ff863
description: "Erfahren Sie mehr über bekannte Probleme mit der aktuellen Version der Microsoft Advertising-Bibliotheken."
title: Bekannte Probleme mit den Advertising-Bibliotheken
ms.author: mcleans
ms.date: 07/20/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, Anzeigen, Werbung, Bekannte Probleme
ms.openlocfilehash: b18c4568770afb70bcca991c79d59a9912981705
ms.sourcegitcommit: a9e4be98688b3a6125fd5dd126190fcfcd764f95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2017
---
# <a name="known-issues-for-the-advertising-libraries"></a><span data-ttu-id="3b457-104">Bekannte Probleme mit den Advertising-Bibliotheken</span><span class="sxs-lookup"><span data-stu-id="3b457-104">Known issues for the advertising libraries</span></span>




<span data-ttu-id="3b457-105">Dieses Thema listet alle bekannten Probleme für die aktuelle Version der Microsoft Advertising-Bibliotheken im Microsoft Advertising-SDK (für UWP-Apps) und im Microsoft Advertising-SDK für Windows und Windows Phone8.x (für Windows8.1- und Windows Phone8.x-Apps) auf.</span><span class="sxs-lookup"><span data-stu-id="3b457-105">This topic lists the known issues with the current release of the Microsoft advertising libraries in the Microsoft Advertising SDK (for UWP apps) and the Microsoft Advertising SDK for Windows and Windows Phone 8.x (for Windows 8.1 and Windows Phone 8.x apps).</span></span>

## <a name="windows-phone-8x-silverlight-projects"></a><span data-ttu-id="3b457-106">Windows Phone8.x Silverlight-Projekte</span><span class="sxs-lookup"><span data-stu-id="3b457-106">Windows Phone 8.x Silverlight projects</span></span>

<span data-ttu-id="3b457-107">Der Microsoft Advertising-SDK for Windows and Windows Phone8.x verfügt nur über begrenzte Unterstützung für Windows Phone8.x Silverlight-Projekte.</span><span class="sxs-lookup"><span data-stu-id="3b457-107">The Microsoft Advertising SDK for Windows and Windows Phone 8.x has limited support for Windows Phone 8.x Silverlight projects.</span></span> <span data-ttu-id="3b457-108">Weitere Informationen finden Sie unter [Anzeigenunterstützung für Windows Phone8.x Silverlight-Projekte](adcontrol-in-windows-phone-silverlight.md#silverlight_support).</span><span class="sxs-lookup"><span data-stu-id="3b457-108">For more information, see [Advertising support for Windows Phone 8.x Silverlight projects](adcontrol-in-windows-phone-silverlight.md#silverlight_support).</span></span>

<span data-ttu-id="3b457-109">Um die Microsoft Advertising-Assemblys für Windows Phone 8.x Silverlight-Projekte abzurufen, installieren Sie den [Microsoft Advertising SDK for Windows and Windows Phone 8.x](http://aka.ms/store-8-sdk), öffnen das Projekt in Visual Studio und wechseln dann zu **Projekt** > **Verbundenen Dienst hinzufügen** > **Ad Mediator**. Die Assemblys werden anschließend automatisch geladen.</span><span class="sxs-lookup"><span data-stu-id="3b457-109">To get the Microsoft advertising assemblies for Windows Phone 8.x Silverlight projects, install the [Microsoft Advertising SDK for Windows and Windows Phone 8.x](http://aka.ms/store-8-sdk), open your project in Visual Studio, and then go to **Project** > **Add Connected Service** > **Ad Mediator** to automatically download the assemblies.</span></span> <span data-ttu-id="3b457-110">Im Anschluss daran können Sie die Ad Mediator-Referenzen aus Ihrem Projekt entfernen, wenn Sie Ad Mediator nicht verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="3b457-110">After doing this, you can remove the ad mediator references from your project if you do not want to use ad mediation.</span></span> <span data-ttu-id="3b457-111">Weitere Informationen finden Sie unter [AdControl in Windows Phone Silverlight](adcontrol-in-windows-phone-silverlight.md).</span><span class="sxs-lookup"><span data-stu-id="3b457-111">For more information, see [AdControl in Windows Phone Silverlight](adcontrol-in-windows-phone-silverlight.md).</span></span>

## <a name="adcontrol-interface-unknown-in-xaml"></a><span data-ttu-id="3b457-112">AdControl-Schnittstelle in XAML nicht bekannt</span><span class="sxs-lookup"><span data-stu-id="3b457-112">AdControl interface unknown in XAML</span></span>

<span data-ttu-id="3b457-113">Das XAML-Markup für eine [AdControl](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.aspx) zeigt möglicherweise fälschlicherweise eine blaue Kurvenlinie an, die anzeigt, dass die Schnittstelle nicht bekannt ist.</span><span class="sxs-lookup"><span data-stu-id="3b457-113">The XAML markup for an [AdControl](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.aspx) may incorrectly show a blue curvy line implying that the interface is unknown.</span></span> <span data-ttu-id="3b457-114">Dies geschieht nur im Zusammenhang mit x86 und kann ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="3b457-114">This occurs only when targeting x86, and it may be ignored.</span></span>

## <a name="lasterror-from-previous-ad-request"></a><span data-ttu-id="3b457-115">„lastError“ aus vorheriger Anzeigenanforderung</span><span class="sxs-lookup"><span data-stu-id="3b457-115">lastError from previous ad request</span></span>

<span data-ttu-id="3b457-116">Wenn es einen **lastError** aus der vorherigen Anzeigenanforderung gibt, wird das Ereignis möglicherweise während des nächsten Anzeigenaufrufs zweimal ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="3b457-116">If there is a leftover **lastError** from the previous ad request, the event may be fired twice during the next ad call.</span></span> <span data-ttu-id="3b457-117">Obwohl die neue Anzeigenanforderung dennoch ausgeführt werden kann und möglicherweise zu einer gültigen Anzeige führt, kann dieses Verhalten zu Verwirrung führen.</span><span class="sxs-lookup"><span data-stu-id="3b457-117">While the new ad request will still be made and may yield a valid ad, this behavior may cause confusion.</span></span>

## <a name="interstitial-ads-and-navigation-buttons-on-phones"></a><span data-ttu-id="3b457-118">Interstitielle Anzeigen und Navigationsschaltflächen auf Telefonen</span><span class="sxs-lookup"><span data-stu-id="3b457-118">Interstitial ads and navigation buttons on phones</span></span>

<span data-ttu-id="3b457-119">Auf Telefonen (oder Emulatoren), die über Softwareschaltflächen für **Zurück**, **Start** und **Suche** anstelle von Hardwaretasten verfügen, werden die Countdown-Timer und Klickschaltflächen für Interstitialanzeigen möglicherweise verdeckt.</span><span class="sxs-lookup"><span data-stu-id="3b457-119">On phones (or emulators) that have software **Back**, **Start**, and **Search** buttons instead of hardware buttons, the countdown timer and click through buttons for interstitial ads may be obscured.</span></span>

## <a name="recently-created-ads-are-not-being-served-to-your-app"></a><span data-ttu-id="3b457-120">Vor Kurzem erstellte Anzeigen werden Ihrer App nicht bereitgestellt</span><span class="sxs-lookup"><span data-stu-id="3b457-120">Recently created ads are not being served to your app</span></span>

<span data-ttu-id="3b457-121">Wenn Sie vor kurzem (weniger als einem Tag) eine Anzeige erstellt haben, ist diese möglicherweise nicht sofort verfügbar.</span><span class="sxs-lookup"><span data-stu-id="3b457-121">If you have created an ad recently (less than a day), it might not be available immediately.</span></span> <span data-ttu-id="3b457-122">Wenn die Anzeige hinsichtlich ihrer redaktionellen Inhalte genehmigt wurde, wird sie bereitgestellt, nachdem der Anzeigenserver sie verarbeitet hat und die Anzeige als Bestand verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="3b457-122">If the ad has been approved for editorial content, it will be served once the advertising server has processed it and the ad is available as inventory.</span></span>

## <a name="no-ads-are-shown-in-your-app"></a><span data-ttu-id="3b457-123">In Ihrer App werden keine Anzeigen angezeigt</span><span class="sxs-lookup"><span data-stu-id="3b457-123">No ads are shown in your app</span></span>

<span data-ttu-id="3b457-124">Es gibt viele Gründe, warum möglicherweise keine Anzeigen angezeigt werden, einschließlich Netzwerkfehlern.</span><span class="sxs-lookup"><span data-stu-id="3b457-124">There are many reasons you may see no ads, including network errors.</span></span> <span data-ttu-id="3b457-125">Andere Gründe können sein:</span><span class="sxs-lookup"><span data-stu-id="3b457-125">Other reasons might include:</span></span>

* <span data-ttu-id="3b457-126">Auswahl einer Anzeigeneinheit im Windows Dev Center mit einer Größe, die größer oder kleiner als die Größe der **AdControl** im Code Ihrer App ist.</span><span class="sxs-lookup"><span data-stu-id="3b457-126">Selecting an ad unit in Windows Dev Center with a size that is greater or less than the size of the **AdControl** in your app's code.</span></span>

* <span data-ttu-id="3b457-127">Anzeigen werden nicht angezeigt, wenn Sie einen [Testmoduswert](test-mode-values.md) für Ihre Anzeigeneinheiten-ID verwenden, wenn eine Live-App ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="3b457-127">Ads will not appear if you're using a [test mode value](test-mode-values.md) for your ad unit ID when running a live app.</span></span>

* <span data-ttu-id="3b457-128">Wenn Sie in der letzten halben Stunde eine neue Anzeigeneinheiten-ID erstellt haben, wird eine Anzeige möglicherweise erst angezeigt, wenn der Server neue Daten durch das System propagiert hat.</span><span class="sxs-lookup"><span data-stu-id="3b457-128">If you created a new ad unit ID in the past half-hour, you might not see an ad until the servers propagate new data through the system.</span></span> <span data-ttu-id="3b457-129">Vorhandene IDs, die zuvor bereits Anzeigen angezeigt haben, sollten Anzeigen sofort anzeigen.</span><span class="sxs-lookup"><span data-stu-id="3b457-129">Existing IDs that have shown ads before should show ads immediately.</span></span>

<span data-ttu-id="3b457-130">Wenn Sie in der App Testanzeigen sehen können, funktioniert Ihr Code und kann Anzeigen anzeigen.</span><span class="sxs-lookup"><span data-stu-id="3b457-130">If you can see test ads in the app, your code is working and is able to display ads.</span></span> <span data-ttu-id="3b457-131">Bei Problemen wenden Sie sich an den [Produktsupport](https://go.microsoft.com/fwlink/p/?LinkId=331508).</span><span class="sxs-lookup"><span data-stu-id="3b457-131">If you encounter issues, contact [product support](https://go.microsoft.com/fwlink/p/?LinkId=331508).</span></span> <span data-ttu-id="3b457-132">Wählen Sie auf dieser Seite **In App-Werbung** aus.</span><span class="sxs-lookup"><span data-stu-id="3b457-132">On that page, choose **In-App Advertising**.</span></span>

<span data-ttu-id="3b457-133">Sie können auch im [Forum](http://go.microsoft.com/fwlink/p/?LinkId=401266) eine Frage stellen.</span><span class="sxs-lookup"><span data-stu-id="3b457-133">You can also post a question in the [forum](http://go.microsoft.com/fwlink/p/?LinkId=401266).</span></span>

## <a name="test-ads-are-showing-in-your-app-instead-of-live-ads"></a><span data-ttu-id="3b457-134">In Ihrer App werden Testanzeigen anstelle von Liveanzeigen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3b457-134">Test ads are showing in your app instead of live ads</span></span>

<span data-ttu-id="3b457-135">Testanzeigen können angezeigt werden, auch wenn Sie Liveanzeigen erwarten.</span><span class="sxs-lookup"><span data-stu-id="3b457-135">Test ads can be shown, even when you are expecting live ads.</span></span> <span data-ttu-id="3b457-136">Dies kann in den folgenden Szenarien vorkommen:</span><span class="sxs-lookup"><span data-stu-id="3b457-136">This can happen in the following scenarios:</span></span>

* <span data-ttu-id="3b457-137">Unsere Werbeplattform kann die Liveanwendungs-ID nicht überprüfen oder finden, die im Store verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="3b457-137">Our advertising platform cannot verify or find the live application ID used in the Store.</span></span> <span data-ttu-id="3b457-138">Wenn eine Anzeigeneinheit von einem Benutzer erstellt wird, kann in diesem Fall der Status als live (Nicht-Test) beginnen, jedoch innerhalb von 6Stunden nach der ersten Anzeigenanforderung in den Teststatus wechseln.</span><span class="sxs-lookup"><span data-stu-id="3b457-138">In this case, when an ad unit is created by a user, its status can start as live (non-test) but will move to test status within 6 hours after the first ad request.</span></span> <span data-ttu-id="3b457-139">Er wechselt zurück zum Livestatus, wenn es 10Tage keine Anforderungen von Test-Apps gibt.</span><span class="sxs-lookup"><span data-stu-id="3b457-139">It will change back to live if there are no requests from test apps for 10 days.</span></span>

* <span data-ttu-id="3b457-140">Quergeladene Apps oder im Emulator ausgeführte Apps zeigen keine Liveanzeigen an.</span><span class="sxs-lookup"><span data-stu-id="3b457-140">Side-loaded apps or apps that are running in the emulator will not show live ads.</span></span>

<span data-ttu-id="3b457-141">Wenn eine Liveanzeigeneinheit Testanzeigen bereitstellt, wird der Status der Anzeigeeinheit im Windows Dev Center als **Aktiv und Testanzeigen bereitstellend** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3b457-141">When a live ad unit is serving test ads, the ad unit’s status shows **Active and serving test ads** in Windows Dev Center.</span></span> <span data-ttu-id="3b457-142">Dies gilt zurzeit nicht für Telefon-Apps.</span><span class="sxs-lookup"><span data-stu-id="3b457-142">This does not currently apply to phone apps.</span></span>

## <a name="obsolete-test-values-for-ad-unit-id-and-application-id-no-longer-working"></a><span data-ttu-id="3b457-143">Veraltete Testwerte für Anzeigeneinheiten-ID und Anwendungs-ID funktionieren nicht mehr</span><span class="sxs-lookup"><span data-stu-id="3b457-143">Obsolete test values for ad unit ID and application ID no longer working</span></span>

<span data-ttu-id="3b457-144">Die folgenden Testwerte für Windows Phone Silverlight-Apps sind veraltet und funktionieren nicht mehr.</span><span class="sxs-lookup"><span data-stu-id="3b457-144">The following test values for Windows Phone Silverlight apps are obsolete, and will no longer work.</span></span> <span data-ttu-id="3b457-145">Wenn ein vorhandenes Projekt diese Testwerte verwendet, aktualisieren Sie dieses Projekt, sodass es die unter [Testmoduswerte](test-mode-values.md) angegebenen Werte verwendet.</span><span class="sxs-lookup"><span data-stu-id="3b457-145">If you have an existing project that uses these test values, update your project to use the values provided in [Test mode values](test-mode-values.md).</span></span>

| <span data-ttu-id="3b457-146">Anwendungs-ID</span><span class="sxs-lookup"><span data-stu-id="3b457-146">Application ID</span></span>  |  <span data-ttu-id="3b457-147">Anzeigeeinheiten-ID</span><span class="sxs-lookup"><span data-stu-id="3b457-147">Ad unit ID</span></span>    |
|-----------------|----------------|
| <span data-ttu-id="3b457-148">test_client</span><span class="sxs-lookup"><span data-stu-id="3b457-148">test_client</span></span>     |  <span data-ttu-id="3b457-149">Image320_50</span><span class="sxs-lookup"><span data-stu-id="3b457-149">Image320_50</span></span>   |
| <span data-ttu-id="3b457-150">test_client</span><span class="sxs-lookup"><span data-stu-id="3b457-150">test_client</span></span>     |  <span data-ttu-id="3b457-151">Image300_50</span><span class="sxs-lookup"><span data-stu-id="3b457-151">Image300_50</span></span>   |
| <span data-ttu-id="3b457-152">test_client</span><span class="sxs-lookup"><span data-stu-id="3b457-152">test_client</span></span>     |  <span data-ttu-id="3b457-153">TextAd</span><span class="sxs-lookup"><span data-stu-id="3b457-153">TextAd</span></span>   |
| <span data-ttu-id="3b457-154">test_client</span><span class="sxs-lookup"><span data-stu-id="3b457-154">test_client</span></span>     |  <span data-ttu-id="3b457-155">Image480_80</span><span class="sxs-lookup"><span data-stu-id="3b457-155">Image480_80</span></span>   |

<span id="reference_errors"/>
## <a name="reference-errors-caused-by-targeting-any-cpu-in-your-project"></a><span data-ttu-id="3b457-156">Referenzfehler, die durch die Ausrichtung auf eine beliebige CPU (Any CPU) in Ihrem Projekt verursacht werden</span><span class="sxs-lookup"><span data-stu-id="3b457-156">Reference errors caused by targeting Any CPU in your project</span></span>

<span data-ttu-id="3b457-157">Wenn Sie die Microsoft Advertising-Bibliotheken verwenden, können Sie in Ihrem Projekt als Ziel nicht **Any CPU** angeben.</span><span class="sxs-lookup"><span data-stu-id="3b457-157">When using the Microsoft advertising libraries, you cannot target **Any CPU** in your project.</span></span> <span data-ttu-id="3b457-158">Wenn Ihr Projekt auf die Plattform **Any CPU** ausgerichtet ist, wird Ihnen möglicherweise eine Warnung angezeigt, nachdem Sie einen Verweis wie diesen hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="3b457-158">If your project targets the **Any CPU** platform, you may see a warning after adding the reference similar to this one.</span></span>

![referenceerror\-solutionexplorer](images/13-19629921-023c-42ec-b8f5-bc0b63d5a191.jpg)

<span data-ttu-id="3b457-160">Um diese Warnung zu entfernen, müssen Sie eine architekturspezifische Buildausgabe verwenden (beispielsweise **x86**) und das Projekt entsprechend aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="3b457-160">To remove this warning, update your project to use an architecture-specific build output (for example, **x86**).</span></span> <span data-ttu-id="3b457-161">Verwenden Sie den **Konfigurations-Manager**, um die Plattformziele für Debug- und Releasekonfigurationen festzulegen.</span><span class="sxs-lookup"><span data-stu-id="3b457-161">Use **Configuration Manager** to set the platform targets for debug and release configurations.</span></span>

![configurationmanagerwin10](images/13-87074274-c10d-4dbd-9a06-453b7184f8de.png)

<span data-ttu-id="3b457-163">Achten Sie darauf, die beabsichtigten Architekturen einzuschließen, wenn Sie App-Pakete für die Übermittlung an den Store erstellen (wie in den folgenden Bildern gezeigt).</span><span class="sxs-lookup"><span data-stu-id="3b457-163">When you create your app packages for store submission (as shown in the following images), be sure to include the architectures you intend to target.</span></span> <span data-ttu-id="3b457-164">Sie können x64 auslassen, wenn Sie x86-Builds auf dem x64-Betriebssystem ausführen möchten.</span><span class="sxs-lookup"><span data-stu-id="3b457-164">You may opt to skip x64 if you intend to run x86 builds on the x64 OS.</span></span>

![projectstorecreateapppackages](images/13-a99b05a4-8917-4c53-822e-2548fadf828a.png)

![createapppackages](images/13-16280cb1-a838-42b9-9256-eac7f33f5603.png)

## <a name="z-order-in-javascripthtml-apps"></a><span data-ttu-id="3b457-167">Z-Reihenfolge in JavaScript/HTML-Apps</span><span class="sxs-lookup"><span data-stu-id="3b457-167">Z-order in JavaScript/HTML apps</span></span>

<span data-ttu-id="3b457-168">JavaScript/HTML-Apps müssen Elemente nicht in den reservierten MAX10-Bereich der Z-Reihenfolge platzieren.</span><span class="sxs-lookup"><span data-stu-id="3b457-168">JavaScript/HTML apps must not place elements into the reserved MAX-10 range of z-order.</span></span> <span data-ttu-id="3b457-169">Die einzigen Ausnahmen sind Interrupt-Overlays wie eingehende Anrufbenachrichtigungen für Skype-Apps.</span><span class="sxs-lookup"><span data-stu-id="3b457-169">The sole exception is an interrupt overlay, such as an inbound call notification for a Skype app.</span></span>

<span id="bkmk-ui"/>
## <a name="do-not-use-borders"></a><span data-ttu-id="3b457-170">Verwenden Sie keine Rahmen</span><span class="sxs-lookup"><span data-stu-id="3b457-170">Do not use borders</span></span>

<span data-ttu-id="3b457-171">Die Festlegung von Rahmeneigenschaften, die **AdControl** von seiner übergeordneten Klasse erbt, führt zu einer falschen Platzierung der Anzeige.</span><span class="sxs-lookup"><span data-stu-id="3b457-171">Setting border-related properties inherited by the **AdControl** from its parent class will cause the ad placement to be wrong.</span></span>

## <a name="more-information"></a><span data-ttu-id="3b457-172">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="3b457-172">More Information</span></span>


<span data-ttu-id="3b457-173">Weitere Informationen zu den neuesten bekannten Problemen im Zusammenhang mit den Microsoft Advertising-Bibliotheken finden Sie im [Forum](http://go.microsoft.com/fwlink/p/?LinkId=401266). Dort können Sie auch Fragen veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="3b457-173">For more information about the latest known issues and to post questions related to the Microsoft advertising libraries, visit the [forum](http://go.microsoft.com/fwlink/p/?LinkId=401266).</span></span>

## <a name="support"></a><span data-ttu-id="3b457-174">Support</span><span class="sxs-lookup"><span data-stu-id="3b457-174">Support</span></span>


<span data-ttu-id="3b457-175">Um sich an den Produktsupport für Probleme mit den Microsoft Advertising-Bibliotheken zu wenden, besuchen Sie die [Supportseite](https://go.microsoft.com/fwlink/p/?LinkId=331508) und wählen **In-App-Werbung** aus.</span><span class="sxs-lookup"><span data-stu-id="3b457-175">To contact product support for issues with the Microsoft advertising libraries, visit the [support page](https://go.microsoft.com/fwlink/p/?LinkId=331508) and choose **In-App Advertising**.</span></span>

 

 
