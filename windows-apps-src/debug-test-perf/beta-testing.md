---
author: PatrickFarley
ms.assetid: 1C77C50C-5DA4-4414-9316-6EEDD78629E2
title: Betatests
description: "Betatests bieten Ihnen die Möglichkeit zum Verbessern Ihrer App anhand des Feedbacks von Personen außerhalb Ihres App-Entwicklungsteams, die die noch nicht freigegebene App auf ihren eigenen Geräten testen."
ms.author: pafarley
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 6f5a4e7f2961143f44acb533f045783fb4e4b7c1
ms.sourcegitcommit: e8cc657d85566768a6efb7cd972ebf64c25e0628
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2017
---
# <a name="beta-testing"></a><span data-ttu-id="3575f-104">Betatests</span><span class="sxs-lookup"><span data-stu-id="3575f-104">Beta testing</span></span>

<span data-ttu-id="3575f-105">\[ Aktualisiert für UWP-Apps unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="3575f-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="3575f-106">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132). \]</span><span class="sxs-lookup"><span data-stu-id="3575f-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>


<span data-ttu-id="3575f-107">*Betatests* bieten Ihnen die Möglichkeit zum Verbessern Ihrer App anhand des Feedbacks von Personen außerhalb Ihres App-Entwicklungsteams, die die noch nicht freigegebene App auf ihren eigenen Geräten testen.</span><span class="sxs-lookup"><span data-stu-id="3575f-107">*Beta testing* gives you the chance to improve your app based on feedback from individuals outside of your app-development team who try your unreleased app on their own devices.</span></span>

<span data-ttu-id="3575f-108">In diesem Abschnitt werden Ihre Optionen zum Durchführen von Betatests für universelle Windows-Apps beschrieben.</span><span class="sxs-lookup"><span data-stu-id="3575f-108">This section describes your options for beta testing Universal Windows apps.</span></span>

## <a name="why-beta-test"></a><span data-ttu-id="3575f-109">Warum Betatests?</span><span class="sxs-lookup"><span data-stu-id="3575f-109">Why beta test?</span></span>

<span data-ttu-id="3575f-110">Für einen umfassenden Test Ihrer App müssen Sie diese mit so vielen Gerätekonfigurationen und Benutzerinteraktionen wie möglich testen.</span><span class="sxs-lookup"><span data-stu-id="3575f-110">To thoroughly test an app, you need to try it against as many device configurations and user interactions as possible.</span></span> <span data-ttu-id="3575f-111">Es ist schwierig bis unmöglich, all diese Tests intern durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="3575f-111">Doing all of that testing in-house is difficult if not impossible.</span></span>

<span data-ttu-id="3575f-112">Bei Betatests testen Benutzer Ihre App auf ihren eigenen Geräten.</span><span class="sxs-lookup"><span data-stu-id="3575f-112">With beta testing, users try your app on their own devices.</span></span> <span data-ttu-id="3575f-113">Dabei gibt es keinen festen Ablauf: Benutzer absolvieren nicht spezielle Aufgaben, sondern verwenden die App nach Belieben und decken dadurch Probleme auf, mit denen Sie möglicherweise gar nicht gerechnet haben.</span><span class="sxs-lookup"><span data-stu-id="3575f-113">And it's unmoderated: instead of performing specified tasks, users have complete freedom in how they use an app, so they can find issues that you might never have expected.</span></span>

<span data-ttu-id="3575f-114">Mit Betatests können Sie folgende Aktionen ausführen:</span><span class="sxs-lookup"><span data-stu-id="3575f-114">With beta testing, you can:</span></span>

-   <span data-ttu-id="3575f-115">Ihre App auf einer Vielzahl von Geräten testen</span><span class="sxs-lookup"><span data-stu-id="3575f-115">Test your app on a variety of devices.</span></span>
-   <span data-ttu-id="3575f-116">Leistungsprobleme und andere Fehler aufdecken, die Sie möglicherweise andernfalls nicht gefunden haben</span><span class="sxs-lookup"><span data-stu-id="3575f-116">Identify performance issues and other bugs that you might not have found otherwise.</span></span>
-   <span data-ttu-id="3575f-117">Realistische Informationen zum Verbessern der Benutzerfreundlichkeit erhalten</span><span class="sxs-lookup"><span data-stu-id="3575f-117">Get real-world usage info that can be used improve the user experience.</span></span>
-   <span data-ttu-id="3575f-118">Feedback ohne Auswirkungen auf die öffentlichen Bewertungen im Windows Store erhalten</span><span class="sxs-lookup"><span data-stu-id="3575f-118">Receive feedback without affecting public ratings in the Windows Store.</span></span>

## <a name="when-to-beta-test"></a><span data-ttu-id="3575f-119">Gründe für Betatests</span><span class="sxs-lookup"><span data-stu-id="3575f-119">When to beta test</span></span>

<span data-ttu-id="3575f-120">Idealerweise führen Sie Betatests in der letzten Testphase durch, bevor Sie Ihre App freigeben.</span><span class="sxs-lookup"><span data-stu-id="3575f-120">It's best to conduct beta testing as the final stage of testing before you release your app.</span></span> <span data-ttu-id="3575f-121">Zu diesem Zeitpunkt haben Sie die App so umfassend wie möglich getestet und alle expliziten Anwendungsfälle behandelt.</span><span class="sxs-lookup"><span data-stu-id="3575f-121">At that point, you have tested the app as thoroughly as you can yourself, and you've covered all explicit use cases.</span></span> <span data-ttu-id="3575f-122">Betatests sind kein Ersatz für andere Testmethoden.</span><span class="sxs-lookup"><span data-stu-id="3575f-122">Beta testing is not a substitute for other testing methods.</span></span> <span data-ttu-id="3575f-123">Da Betatests keinem bestimmten Ablauf folgen, können die Teilnehmer unmöglich alle Fehler im Code finden, da alle Tester individuell vorgehen und es unwahrscheinlich ist, dass sie alle Features der App nutzen werden.</span><span class="sxs-lookup"><span data-stu-id="3575f-123">Since beta testing is unmoderated, participants may not catch all bugs in your code because every tester's experience is self-directed and it's unlikely that they'll explore all features of the app.</span></span> <span data-ttu-id="3575f-124">Durch das Feedback in Betatests erhalten Sie jedoch reales Feedback zur Nutzung und können Probleme aufdecken, mit denen Sie möglicherweise gar nicht gerechnet haben.</span><span class="sxs-lookup"><span data-stu-id="3575f-124">But beta-testing feedback can give you a final wave of real-world feedback that reveals issues that you might never have expected before you go live.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3575f-125">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="3575f-125">Next steps</span></span>

<span data-ttu-id="3575f-126">Im einheitlichen Windows Dev Center-Dashboard können Sie die Verteilung Ihrer Apps auf Ihre Tester beschränken, unabhängig davon, auf welche Betriebssysteme Ihrer App ausgerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="3575f-126">In the unified Windows Dev Center dashboard, you can limit distribution of your apps to only your testers, regardless of which operating systems your app targets.</span></span> <span data-ttu-id="3575f-127">Es ist nicht erforderlich, eine separate Version der App mit separatem Namen und separater Paketidentität zu erstellen. Sie können Ihre Tests durchführen, dann eine neue Einreichung erstellen, wenn Sie dazu bereit sind, die App für alle Benutzer zur Verfügung zu stellen.</span><span class="sxs-lookup"><span data-stu-id="3575f-127">There’s no need to create a separate version of your app with a separate name and package identity; you can do your testing, then create a new submission when you’re ready to make the app available to everyone.</span></span> <span data-ttu-id="3575f-128">(Selbstverständlich können Sie bei Bedarf zum Testen eine separate App erstellen.</span><span class="sxs-lookup"><span data-stu-id="3575f-128">(Of course, you can create a separate app for testing only if you prefer.</span></span> <span data-ttu-id="3575f-129">Stellen Sie in diesem Fall sicher, dass Sie ihr einen anderen als den endgültigen öffentlichen App-Namen zuzuweisen.)</span><span class="sxs-lookup"><span data-stu-id="3575f-129">If you do, make sure to give it a different name from what you intend as the final, public app name.)</span></span>

<span data-ttu-id="3575f-130">Informationen zum Übermitteln Ihrer App an den Store für Betatests finden Sie unter [Betatests und zielgerichtete Verteilung](https://msdn.microsoft.com/library/windows/apps/Mt185377).</span><span class="sxs-lookup"><span data-stu-id="3575f-130">See [Beta testing and targeted distribution](https://msdn.microsoft.com/library/windows/apps/Mt185377) to learn how to submit your app to the Store for beta testing.</span></span>

 

 




