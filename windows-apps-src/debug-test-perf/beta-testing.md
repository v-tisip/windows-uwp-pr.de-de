---
ms.assetid: 1C77C50C-5DA4-4414-9316-6EEDD78629E2
title: Betatests
description: Betatests bieten Ihnen die Möglichkeit zum Verbessern Ihrer App anhand des Feedbacks von Personen außerhalb Ihres App-Entwicklungsteams, die die noch nicht freigegebene App auf ihren eigenen Geräten testen.
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 2eca388b37cc95803b7ecb94bc0b0b5b990f5de3
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8893450"
---
# <a name="beta-testing"></a><span data-ttu-id="1119e-104">Betatests</span><span class="sxs-lookup"><span data-stu-id="1119e-104">Beta testing</span></span>



<span data-ttu-id="1119e-105">*Betatests* bieten Ihnen die Möglichkeit zum Verbessern Ihrer App anhand des Feedbacks von Personen außerhalb Ihres App-Entwicklungsteams, die die noch nicht freigegebene App auf ihren eigenen Geräten testen.</span><span class="sxs-lookup"><span data-stu-id="1119e-105">*Beta testing* gives you the chance to improve your app based on feedback from individuals outside of your app-development team who try your unreleased app on their own devices.</span></span>

<span data-ttu-id="1119e-106">In diesem Abschnitt werden Ihre Optionen zum Durchführen von Betatests für universelle Windows-Apps beschrieben.</span><span class="sxs-lookup"><span data-stu-id="1119e-106">This section describes your options for beta testing Universal Windows apps.</span></span>

## <a name="why-beta-test"></a><span data-ttu-id="1119e-107">Warum Betatests?</span><span class="sxs-lookup"><span data-stu-id="1119e-107">Why beta test?</span></span>

<span data-ttu-id="1119e-108">Für einen umfassenden Test Ihrer App müssen Sie diese mit so vielen Gerätekonfigurationen und Benutzerinteraktionen wie möglich testen.</span><span class="sxs-lookup"><span data-stu-id="1119e-108">To thoroughly test an app, you need to try it against as many device configurations and user interactions as possible.</span></span> <span data-ttu-id="1119e-109">Es ist schwierig bis unmöglich, all diese Tests intern durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="1119e-109">Doing all of that testing in-house is difficult if not impossible.</span></span>

<span data-ttu-id="1119e-110">Bei Betatests testen Benutzer Ihre App auf ihren eigenen Geräten.</span><span class="sxs-lookup"><span data-stu-id="1119e-110">With beta testing, users try your app on their own devices.</span></span> <span data-ttu-id="1119e-111">Dabei gibt es keinen festen Ablauf: Benutzer absolvieren nicht spezielle Aufgaben, sondern verwenden die App nach Belieben und decken dadurch Probleme auf, mit denen Sie möglicherweise gar nicht gerechnet haben.</span><span class="sxs-lookup"><span data-stu-id="1119e-111">And it's unmoderated: instead of performing specified tasks, users have complete freedom in how they use an app, so they can find issues that you might never have expected.</span></span>

<span data-ttu-id="1119e-112">Mit Betatests können Sie folgende Aktionen ausführen:</span><span class="sxs-lookup"><span data-stu-id="1119e-112">With beta testing, you can:</span></span>

-   <span data-ttu-id="1119e-113">Ihre App auf einer Vielzahl von Geräten testen</span><span class="sxs-lookup"><span data-stu-id="1119e-113">Test your app on a variety of devices.</span></span>
-   <span data-ttu-id="1119e-114">Leistungsprobleme und andere Fehler aufdecken, die Sie möglicherweise andernfalls nicht gefunden haben</span><span class="sxs-lookup"><span data-stu-id="1119e-114">Identify performance issues and other bugs that you might not have found otherwise.</span></span>
-   <span data-ttu-id="1119e-115">Realistische Informationen zum Verbessern der Benutzerfreundlichkeit erhalten</span><span class="sxs-lookup"><span data-stu-id="1119e-115">Get real-world usage info that can be used improve the user experience.</span></span>
-   <span data-ttu-id="1119e-116">Erhalten Sie Feedback ohne Auswirkungen auf die öffentlichen Bewertungen im Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="1119e-116">Receive feedback without affecting public ratings in the Microsoft Store.</span></span>

## <a name="when-to-beta-test"></a><span data-ttu-id="1119e-117">Gründe für Betatests</span><span class="sxs-lookup"><span data-stu-id="1119e-117">When to beta test</span></span>

<span data-ttu-id="1119e-118">Idealerweise führen Sie Betatests in der letzten Testphase durch, bevor Sie Ihre App freigeben.</span><span class="sxs-lookup"><span data-stu-id="1119e-118">It's best to conduct beta testing as the final stage of testing before you release your app.</span></span> <span data-ttu-id="1119e-119">Zu diesem Zeitpunkt haben Sie die App so umfassend wie möglich getestet und alle expliziten Anwendungsfälle behandelt.</span><span class="sxs-lookup"><span data-stu-id="1119e-119">At that point, you have tested the app as thoroughly as you can yourself, and you've covered all explicit use cases.</span></span> <span data-ttu-id="1119e-120">Betatests sind kein Ersatz für andere Testmethoden.</span><span class="sxs-lookup"><span data-stu-id="1119e-120">Beta testing is not a substitute for other testing methods.</span></span> <span data-ttu-id="1119e-121">Da Betatests keinem bestimmten Ablauf folgen, können die Teilnehmer unmöglich alle Fehler im Code finden, da alle Tester individuell vorgehen und es unwahrscheinlich ist, dass sie alle Features der App nutzen werden.</span><span class="sxs-lookup"><span data-stu-id="1119e-121">Since beta testing is unmoderated, participants may not catch all bugs in your code because every tester's experience is self-directed and it's unlikely that they'll explore all features of the app.</span></span> <span data-ttu-id="1119e-122">Durch das Feedback in Betatests erhalten Sie jedoch reales Feedback zur Nutzung und können Probleme aufdecken, mit denen Sie möglicherweise gar nicht gerechnet haben.</span><span class="sxs-lookup"><span data-stu-id="1119e-122">But beta-testing feedback can give you a final wave of real-world feedback that reveals issues that you might never have expected before you go live.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1119e-123">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="1119e-123">Next steps</span></span>

<span data-ttu-id="1119e-124">Im [Partner Center](https://partner.microsoft.com/dashboard)können Sie die Verteilung Ihrer Apps auf Ihre Tester, unabhängig davon, welche Betriebssysteme Ihre app ausgerichtet ist beschränken.</span><span class="sxs-lookup"><span data-stu-id="1119e-124">In [Partner Center](https://partner.microsoft.com/dashboard), you can limit distribution of your apps to only your testers, regardless of which operating systems your app targets.</span></span> <span data-ttu-id="1119e-125">Es ist nicht erforderlich, eine separate Version der App mit separatem Namen und separater Paketidentität zu erstellen. Sie können Ihre Tests durchführen, dann eine neue Einreichung erstellen, wenn Sie dazu bereit sind, die App für alle Benutzer zur Verfügung zu stellen.</span><span class="sxs-lookup"><span data-stu-id="1119e-125">There’s no need to create a separate version of your app with a separate name and package identity; you can do your testing, then create a new submission when you’re ready to make the app available to everyone.</span></span> <span data-ttu-id="1119e-126">(Selbstverständlich können Sie bei Bedarf zum Testen eine separate App erstellen.</span><span class="sxs-lookup"><span data-stu-id="1119e-126">(Of course, you can create a separate app for testing only if you prefer.</span></span> <span data-ttu-id="1119e-127">Stellen Sie in diesem Fall sicher, dass Sie ihr einen anderen als den endgültigen öffentlichen App-Namen zuzuweisen.)</span><span class="sxs-lookup"><span data-stu-id="1119e-127">If you do, make sure to give it a different name from what you intend as the final, public app name.)</span></span>

<span data-ttu-id="1119e-128">Informationen zum Übermitteln Ihrer App an den Store für Betatests finden Sie unter [Betatests und zielgerichtete Verteilung](../publish/beta-testing-and-targeted-distribution.md).</span><span class="sxs-lookup"><span data-stu-id="1119e-128">See [Beta testing and targeted distribution](../publish/beta-testing-and-targeted-distribution.md) to learn how to submit your app to the Store for beta testing.</span></span>

 

 




