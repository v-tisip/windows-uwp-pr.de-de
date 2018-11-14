---
author: Xansky
ms.assetid: 9ca1f880-2ced-46b4-8ea7-aba43d2ff863
description: Erfahren Sie mehr über bekannte Probleme mit der aktuellen Version der Microsoft Advertising-SDK.
title: Bekannte Probleme und Informationen zur Problembehandlung von Anzeigen in Apps
ms.author: mhopkins
ms.date: 04/16/2018
ms.topic: article
keywords: Windows 10, UWP, Anzeigen, Werbung, Bekannte Probleme, Problembehandlung
ms.localizationpriority: medium
ms.openlocfilehash: d1b3b1fb68ed246d6a5a8334c5cf4d1c0754b719
ms.sourcegitcommit: 71e8eae5c077a7740e5606298951bb78fc42b22c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "6652936"
---
# <a name="known-issues-and-troubleshooting-for-ads-in-apps"></a><span data-ttu-id="e27d0-104">Bekannte Probleme und Informationen zur Problembehandlung von Anzeigen in Apps</span><span class="sxs-lookup"><span data-stu-id="e27d0-104">Known issues and troubleshooting for ads in apps</span></span>

<span data-ttu-id="e27d0-105">Erfahren Sie in diesem Thema mehr über bekannte Probleme mit der aktuellen Version des Microsoft Advertising-SDKs.</span><span class="sxs-lookup"><span data-stu-id="e27d0-105">This topic lists the known issues with the current release of the Microsoft Advertising SDK.</span></span> <span data-ttu-id="e27d0-106">Weitere Erläuterungen zur Problembehandlung finden Sie unter folgenden Themen.</span><span class="sxs-lookup"><span data-stu-id="e27d0-106">For additional troubleshooting guidance, see the following topics.</span></span>

* [<span data-ttu-id="e27d0-107">Anleitung zur Problembehandlung für HTML und JavaScript</span><span class="sxs-lookup"><span data-stu-id="e27d0-107">HTML and JavaScript troubleshooting guide</span></span>](html-and-javascript-troubleshooting-guide.md)
* [<span data-ttu-id="e27d0-108">Handbuch zur Problembehandlung für XAML und C#</span><span class="sxs-lookup"><span data-stu-id="e27d0-108">XAML and C# troubleshooting guide</span></span>](xaml-and-c-troubleshooting-guide.md)

## <a name="adcontrol-interface-unknown-in-xaml"></a><span data-ttu-id="e27d0-109">AdControl-Schnittstelle in XAML nicht bekannt</span><span class="sxs-lookup"><span data-stu-id="e27d0-109">AdControl interface unknown in XAML</span></span>

<span data-ttu-id="e27d0-110">Das XAML-Markup für eine [AdControl](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol) zeigt möglicherweise fälschlicherweise eine blaue Kurvenlinie an, die anzeigt, dass die Schnittstelle nicht bekannt ist.</span><span class="sxs-lookup"><span data-stu-id="e27d0-110">The XAML markup for an [AdControl](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol) may incorrectly show a blue curvy line implying that the interface is unknown.</span></span> <span data-ttu-id="e27d0-111">Dies geschieht nur im Zusammenhang mit x86 und kann ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="e27d0-111">This occurs only when targeting x86, and it may be ignored.</span></span>

## <a name="lasterror-from-previous-ad-request"></a><span data-ttu-id="e27d0-112">„lastError“ aus vorheriger Anzeigenanforderung</span><span class="sxs-lookup"><span data-stu-id="e27d0-112">lastError from previous ad request</span></span>

<span data-ttu-id="e27d0-113">Wenn es einen **lastError** aus der vorherigen Anzeigenanforderung gibt, wird das Ereignis möglicherweise während des nächsten Anzeigenaufrufs zweimal ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="e27d0-113">If there is a leftover **lastError** from the previous ad request, the event may be fired twice during the next ad call.</span></span> <span data-ttu-id="e27d0-114">Obwohl die neue Anzeigenanforderung dennoch ausgeführt werden kann und möglicherweise zu einer gültigen Anzeige führt, kann dieses Verhalten zu Verwirrung führen.</span><span class="sxs-lookup"><span data-stu-id="e27d0-114">While the new ad request will still be made and may yield a valid ad, this behavior may cause confusion.</span></span>

## <a name="interstitial-ads-and-navigation-buttons-on-phones"></a><span data-ttu-id="e27d0-115">Interstitielle Anzeigen und Navigationsschaltflächen auf Telefonen</span><span class="sxs-lookup"><span data-stu-id="e27d0-115">Interstitial ads and navigation buttons on phones</span></span>

<span data-ttu-id="e27d0-116">Auf Telefonen (oder Emulatoren), die über Softwareschaltflächen für **Zurück**, **Start** und **Suche** anstelle von Hardwaretasten verfügen, werden die Countdown-Timer und Klickschaltflächen für Interstitialanzeigen möglicherweise verdeckt.</span><span class="sxs-lookup"><span data-stu-id="e27d0-116">On phones (or emulators) that have software **Back**, **Start**, and **Search** buttons instead of hardware buttons, the countdown timer and click through buttons for interstitial ads may be obscured.</span></span>

## <a name="recently-created-ads-are-not-being-served-to-your-app"></a><span data-ttu-id="e27d0-117">Vor Kurzem erstellte Anzeigen werden Ihrer App nicht bereitgestellt</span><span class="sxs-lookup"><span data-stu-id="e27d0-117">Recently created ads are not being served to your app</span></span>

<span data-ttu-id="e27d0-118">Wenn Sie vor kurzem (weniger als einem Tag) eine Anzeige erstellt haben, ist diese möglicherweise nicht sofort verfügbar.</span><span class="sxs-lookup"><span data-stu-id="e27d0-118">If you have created an ad recently (less than a day), it might not be available immediately.</span></span> <span data-ttu-id="e27d0-119">Wenn die Anzeige hinsichtlich ihrer redaktionellen Inhalte genehmigt wurde, wird sie bereitgestellt, nachdem der Anzeigenserver sie verarbeitet hat und die Anzeige als Bestand verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="e27d0-119">If the ad has been approved for editorial content, it will be served once the advertising server has processed it and the ad is available as inventory.</span></span>

## <a name="no-ads-are-shown-in-your-app"></a><span data-ttu-id="e27d0-120">In Ihrer App werden keine Anzeigen angezeigt</span><span class="sxs-lookup"><span data-stu-id="e27d0-120">No ads are shown in your app</span></span>

<span data-ttu-id="e27d0-121">Es gibt viele Gründe, warum möglicherweise keine Anzeigen angezeigt werden, einschließlich Netzwerkfehlern.</span><span class="sxs-lookup"><span data-stu-id="e27d0-121">There are many reasons you may see no ads, including network errors.</span></span> <span data-ttu-id="e27d0-122">Andere Gründe können sein:</span><span class="sxs-lookup"><span data-stu-id="e27d0-122">Other reasons might include:</span></span>

* <span data-ttu-id="e27d0-123">Auswahl einer anzeigeneinheit im Partner Center mit einer Größe, die größer oder kleiner als die Größe der **AdControl** in Ihrem app Code ist.</span><span class="sxs-lookup"><span data-stu-id="e27d0-123">Selecting an ad unit in Partner Center with a size that is greater or less than the size of the **AdControl** in your app's code.</span></span>

* <span data-ttu-id="e27d0-124">Anzeigen werden nicht angezeigt, wenn Sie einen [Testmoduswert](set-up-ad-units-in-your-app.md#test-ad-units) für Ihre Anzeigeneinheiten-ID verwenden, wenn eine Live-App ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="e27d0-124">Ads will not appear if you're using a [test mode value](set-up-ad-units-in-your-app.md#test-ad-units) for your ad unit ID when running a live app.</span></span>

* <span data-ttu-id="e27d0-125">Wenn Sie in der letzten halben Stunde eine neue Anzeigeneinheiten-ID erstellt haben, wird eine Anzeige möglicherweise erst angezeigt, wenn der Server neue Daten durch das System propagiert hat.</span><span class="sxs-lookup"><span data-stu-id="e27d0-125">If you created a new ad unit ID in the past half-hour, you might not see an ad until the servers propagate new data through the system.</span></span> <span data-ttu-id="e27d0-126">Vorhandene IDs, die zuvor bereits Anzeigen angezeigt haben, sollten Anzeigen sofort anzeigen.</span><span class="sxs-lookup"><span data-stu-id="e27d0-126">Existing IDs that have shown ads before should show ads immediately.</span></span>

<span data-ttu-id="e27d0-127">Wenn Sie in der App Testanzeigen sehen können, funktioniert Ihr Code und kann Anzeigen anzeigen.</span><span class="sxs-lookup"><span data-stu-id="e27d0-127">If you can see test ads in the app, your code is working and is able to display ads.</span></span> <span data-ttu-id="e27d0-128">Bei Problemen wenden Sie sich an den [Produktsupport](https://developer.microsoft.com/en-us/windows/support).</span><span class="sxs-lookup"><span data-stu-id="e27d0-128">If you encounter issues, contact [product support](https://developer.microsoft.com/en-us/windows/support).</span></span> <span data-ttu-id="e27d0-129">Wählen Sie auf dieser Seite **Ads-In-Apps** aus.</span><span class="sxs-lookup"><span data-stu-id="e27d0-129">On that page, choose **Ads-In-Apps**.</span></span>

<span data-ttu-id="e27d0-130">Sie können auch im [Forum](http://go.microsoft.com/fwlink/p/?LinkId=401266) eine Frage stellen.</span><span class="sxs-lookup"><span data-stu-id="e27d0-130">You can also post a question in the [forum](http://go.microsoft.com/fwlink/p/?LinkId=401266).</span></span>

## <a name="test-ads-are-showing-in-your-app-instead-of-live-ads"></a><span data-ttu-id="e27d0-131">In Ihrer App werden Testanzeigen anstelle von Liveanzeigen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e27d0-131">Test ads are showing in your app instead of live ads</span></span>

<span data-ttu-id="e27d0-132">Testanzeigen können angezeigt werden, auch wenn Sie Liveanzeigen erwarten.</span><span class="sxs-lookup"><span data-stu-id="e27d0-132">Test ads can be shown, even when you are expecting live ads.</span></span> <span data-ttu-id="e27d0-133">Dies kann in den folgenden Szenarien vorkommen:</span><span class="sxs-lookup"><span data-stu-id="e27d0-133">This can happen in the following scenarios:</span></span>

* <span data-ttu-id="e27d0-134">Unsere Werbeplattform kann die Liveanwendungs-ID nicht überprüfen oder finden, die im Store verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="e27d0-134">Our advertising platform cannot verify or find the live application ID used in the Store.</span></span> <span data-ttu-id="e27d0-135">Wenn eine Anzeigeneinheit von einem Benutzer erstellt wird, kann in diesem Fall der Status als live (Nicht-Test) beginnen, jedoch innerhalb von 6Stunden nach der ersten Anzeigenanforderung in den Teststatus wechseln.</span><span class="sxs-lookup"><span data-stu-id="e27d0-135">In this case, when an ad unit is created by a user, its status can start as live (non-test) but will move to test status within 6 hours after the first ad request.</span></span> <span data-ttu-id="e27d0-136">Er wechselt zurück zum Livestatus, wenn es 10Tage keine Anforderungen von Test-Apps gibt.</span><span class="sxs-lookup"><span data-stu-id="e27d0-136">It will change back to live if there are no requests from test apps for 10 days.</span></span>

* <span data-ttu-id="e27d0-137">Quergeladene Apps oder im Emulator ausgeführte Apps zeigen keine Liveanzeigen an.</span><span class="sxs-lookup"><span data-stu-id="e27d0-137">Side-loaded apps or apps that are running in the emulator will not show live ads.</span></span>

<span data-ttu-id="e27d0-138">Wenn eine liveanzeigeneinheit testanzeigen bereitstellt, wird zeigt Status der Anzeigeeinheit **aktiv und testanzeigen bereitstellend** im Partner Center.</span><span class="sxs-lookup"><span data-stu-id="e27d0-138">When a live ad unit is serving test ads, the ad unit’s status shows **Active and serving test ads** in Partner Center.</span></span> <span data-ttu-id="e27d0-139">Dies gilt zurzeit nicht für Telefon-Apps.</span><span class="sxs-lookup"><span data-stu-id="e27d0-139">This does not currently apply to phone apps.</span></span>


<span id="reference_errors"/>

## <a name="reference-errors-caused-by-targeting-any-cpu-in-your-project"></a><span data-ttu-id="e27d0-140">Referenzfehler, die durch die Ausrichtung auf eine beliebige CPU (Any CPU) in Ihrem Projekt verursacht werden</span><span class="sxs-lookup"><span data-stu-id="e27d0-140">Reference errors caused by targeting Any CPU in your project</span></span>

<span data-ttu-id="e27d0-141">Wenn Sie die Microsoft Advertising-SDK verwenden, können Sie in Ihrem Projekt als Ziel nicht **Any CPU** angeben.</span><span class="sxs-lookup"><span data-stu-id="e27d0-141">When using the Microsoft Advertising SDK, you cannot target **Any CPU** in your project.</span></span> <span data-ttu-id="e27d0-142">Wenn Ihr Projekt auf die Plattform **Any CPU** ausgerichtet ist, wird Ihnen möglicherweise eine Warnung angezeigt, nachdem Sie einen Verweis wie diesen hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="e27d0-142">If your project targets the **Any CPU** platform, you may see a warning after adding the reference similar to this one.</span></span>

![referenceerror\-solutionexplorer](images/13-19629921-023c-42ec-b8f5-bc0b63d5a191.jpg)

<span data-ttu-id="e27d0-144">Um diese Warnung zu entfernen, müssen Sie eine architekturspezifische Buildausgabe verwenden (beispielsweise **x86**) und das Projekt entsprechend aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="e27d0-144">To remove this warning, update your project to use an architecture-specific build output (for example, **x86**).</span></span> <span data-ttu-id="e27d0-145">Verwenden Sie den **Konfigurations-Manager**, um die Plattformziele für Debug- und Releasekonfigurationen festzulegen.</span><span class="sxs-lookup"><span data-stu-id="e27d0-145">Use **Configuration Manager** to set the platform targets for debug and release configurations.</span></span>

![configurationmanagerwin10](images/13-87074274-c10d-4dbd-9a06-453b7184f8de.png)

<span data-ttu-id="e27d0-147">Achten Sie darauf, die beabsichtigten Architekturen einzuschließen, wenn Sie App-Pakete für die Übermittlung an den Store erstellen (wie in den folgenden Bildern gezeigt).</span><span class="sxs-lookup"><span data-stu-id="e27d0-147">When you create your app packages for store submission (as shown in the following images), be sure to include the architectures you intend to target.</span></span> <span data-ttu-id="e27d0-148">Sie können x64 auslassen, wenn Sie x86-Builds auf dem x64-Betriebssystem ausführen möchten.</span><span class="sxs-lookup"><span data-stu-id="e27d0-148">You may opt to skip x64 if you intend to run x86 builds on the x64 OS.</span></span>

![projectstorecreateapppackages](images/13-a99b05a4-8917-4c53-822e-2548fadf828a.png)

![createapppackages](images/13-16280cb1-a838-42b9-9256-eac7f33f5603.png)

## <a name="z-order-in-javascripthtml-apps"></a><span data-ttu-id="e27d0-151">Z-Reihenfolge in JavaScript/HTML-Apps</span><span class="sxs-lookup"><span data-stu-id="e27d0-151">Z-order in JavaScript/HTML apps</span></span>

<span data-ttu-id="e27d0-152">JavaScript/HTML-Apps müssen Elemente nicht in den reservierten MAX10-Bereich der Z-Reihenfolge platzieren.</span><span class="sxs-lookup"><span data-stu-id="e27d0-152">JavaScript/HTML apps must not place elements into the reserved MAX-10 range of z-order.</span></span> <span data-ttu-id="e27d0-153">Die einzigen Ausnahmen sind Interrupt-Overlays wie eingehende Anrufbenachrichtigungen für Skype-Apps.</span><span class="sxs-lookup"><span data-stu-id="e27d0-153">The sole exception is an interrupt overlay, such as an inbound call notification for a Skype app.</span></span>

<span id="bkmk-ui"/>

## <a name="do-not-use-borders"></a><span data-ttu-id="e27d0-154">Verwenden Sie keine Rahmen</span><span class="sxs-lookup"><span data-stu-id="e27d0-154">Do not use borders</span></span>

<span data-ttu-id="e27d0-155">Die Festlegung von Rahmeneigenschaften, die **AdControl** von seiner übergeordneten Klasse erbt, führt zu einer falschen Platzierung der Anzeige.</span><span class="sxs-lookup"><span data-stu-id="e27d0-155">Setting border-related properties inherited by the **AdControl** from its parent class will cause the ad placement to be wrong.</span></span>

## <a name="more-information"></a><span data-ttu-id="e27d0-156">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e27d0-156">More Information</span></span>

<span data-ttu-id="e27d0-157">Weitere Informationen zu den neuesten bekannten Problemen im Zusammenhang mit den Microsoft Advertising-SDKs finden Sie im [Forum](http://go.microsoft.com/fwlink/p/?LinkId=401266). Dort können Sie auch Fragen veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="e27d0-157">For more information about the latest known issues and to post questions related to the Microsoft Advertising SDK, visit the [forum](http://go.microsoft.com/fwlink/p/?LinkId=401266).</span></span>

 

 
