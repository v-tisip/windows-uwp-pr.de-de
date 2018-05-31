---
author: joannaleecy
title: Erstellen einer Demo-App für den Einzelhandel
description: Erstellen Sie eine Demo-App für den Einzelhandel (RDX-App, Retail Demo Experience-App). Dies ist eine App, die sowohl im Einzelhandels-Demomodus als auch im Normalmodus gestartet werden kann.
ms.assetid: f83f950f-7fdd-4f18-8127-b92a8f400061
ms.author: joanlee
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, Demo-App für den Einzelhandel
ms.localizationpriority: medium
ms.openlocfilehash: 19a22e09484943d63988cef6bb6a7e7c09e016dd
ms.sourcegitcommit: 6618517dc0a4e4100af06e6d27fac133d317e545
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2018
ms.locfileid: "1691016"
---
#  <a name="create-a-retail-demo-experience-rdx-app"></a><span data-ttu-id="de5c8-104">Erstellen einer Demo-App für den Einzelhandel (RDX-App, Retail Demo Experience-App)</span><span class="sxs-lookup"><span data-stu-id="de5c8-104">Create a Retail Demo Experience (RDX) app</span></span>

<span data-ttu-id="de5c8-105">Wenn Kunden ein Geschäft betreten, erwarten sie, dort die neuesten PCs und Mobiltelefone vorzufinden. Diese Geräte werden als Demogeräte für den Einzelhandel bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="de5c8-105">When customers walk into a retail store or location, they expect to find the latest PCs and mobile phones on display and these devices on display are known as retail demo devices.</span></span>
<span data-ttu-id="de5c8-106">Solche Vorführgeräte und die darauf installierten Inhalte sind zu großen Teilen für das Kundenerlebnis im Geschäft verantwortlich, da Kunden häufig viel Zeit damit verbringen, diese Geräte auszuprobieren.</span><span class="sxs-lookup"><span data-stu-id="de5c8-106">Retail demo devices and content installed on them are largely responsible for the customer experience at the stores because customers often spend a considerable chunk of their time playing around with these devices.</span></span>

<span data-ttu-id="de5c8-107">Auf diesen PCs und Mobiltelefonen in den Einzelhandelsgeschäften muss eine Demo-App für den Einzelhandel (RDX-App) installiert sein.</span><span class="sxs-lookup"><span data-stu-id="de5c8-107">Apps that are installed on these PCs and mobile phones in the retail stores must be a retail demo experience (RDX) app.</span></span> <span data-ttu-id="de5c8-108">In diesem Artikel finden Sie Informationen zum Entwickeln und Gestalten einer Einzelhandels-Demoversion Ihrer App, die auf PCs und mobilen Demogeräten im Einzelhandel installiert wird.</span><span class="sxs-lookup"><span data-stu-id="de5c8-108">This article provides an overview of how to design and develop a retail demo version of an app to be installed on PCs and mobile demo devices at a retail store.</span></span>

<span data-ttu-id="de5c8-109">Eine Demo-App für den Einzelhandel umfasst einen einzelnen Build, der in zwei verschiedenen Modi gestartet werden kann: im _Normalmodus_ oder im _Einzelhandelsmodus_.</span><span class="sxs-lookup"><span data-stu-id="de5c8-109">A retail demo experience app comes in a single build that can be launched in one of the two different modes- _normal_ or _retail_.</span></span>
<span data-ttu-id="de5c8-110">Aus Sicht unserer Kunden gibt es nur eine App. Damit sie zwischen den beiden Versionen unterscheiden können, empfiehlt es sich, dass die im Einzelhandelsmodus ausgeführte App in der Titelleiste oder an einer anderen entsprechenden Stelle gut sichtbar das Wort „Einzelhandel“ anzeigt.</span><span class="sxs-lookup"><span data-stu-id="de5c8-110">From our customers' perspective, there is only one app and to help our customers distinguish between the two versions, it is recommended that your app running in retail mode display the words "Retail" prominently in the title bar or in a suitable location.</span></span>

<span data-ttu-id="de5c8-111">Zusätzlich zu den Store-Anforderungen für Apps müssen RDX-Apps auch vollständig mit dem Einrichtungs-, Bereinigungs- und Aktualisierungssystem der Vorführgeräte kompatibel sein, damit die Erfahrung der Kunden im Geschäft durchgehend positiv ist.</span><span class="sxs-lookup"><span data-stu-id="de5c8-111">In addition to the Store requirements for apps, RDX apps must also be fully compatible with the retail demo devices set up, clean up, and update system to ensure that customers have a consistently positive experience at the retail store.</span></span>

## <a name="design-principles"></a><span data-ttu-id="de5c8-112">Designprinzipien</span><span class="sxs-lookup"><span data-stu-id="de5c8-112">Design principles</span></span>

### <a name="show-your-best"></a><span data-ttu-id="de5c8-113">Optimale Präsentation</span><span class="sxs-lookup"><span data-stu-id="de5c8-113">Show your best</span></span>

<span data-ttu-id="de5c8-114">Verwenden Sie die Demo-App, um zu zeigen, was an Ihrer Anwendung so großartig ist.</span><span class="sxs-lookup"><span data-stu-id="de5c8-114">Use the retail demo experience to showcase why your application rocks.</span></span>  <span data-ttu-id="de5c8-115">Wahrscheinlich ist dies das erste Mal, dass die Kunden Ihre Anwendung sehen, präsentieren Sie sie also von ihrer besten Seite.</span><span class="sxs-lookup"><span data-stu-id="de5c8-115">This is likely the first time your customer will see your application, so show them the best piece!</span></span>

### <a name="show-it-fast"></a><span data-ttu-id="de5c8-116">Schnelle Vorführung</span><span class="sxs-lookup"><span data-stu-id="de5c8-116">Show it fast</span></span>

<span data-ttu-id="de5c8-117">Kunden können ungeduldig sein – je schneller ein Benutzer den Wert ihrer App erfasst, desto besser.</span><span class="sxs-lookup"><span data-stu-id="de5c8-117">Customers can be impatient - The faster a user can experience the real value of your app, the better.</span></span>

### <a name="keep-the-story-simple"></a><span data-ttu-id="de5c8-118">Einfache Demonstration</span><span class="sxs-lookup"><span data-stu-id="de5c8-118">Keep the story simple</span></span>

<span data-ttu-id="de5c8-119">Die Demo-App ist ein Elevator Pitch für den Wert Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="de5c8-119">Remember that the retail demo experience is an elevator pitch for your app’s value.</span></span>

### <a name="focus-on-the-experience"></a><span data-ttu-id="de5c8-120">Das Erlebnis in den Mittelpunkt stellen</span><span class="sxs-lookup"><span data-stu-id="de5c8-120">Focus on the experience</span></span>

<span data-ttu-id="de5c8-121">Geben Sie den Benutzern die Zeit, um Ihre Inhalte zu verdauen.</span><span class="sxs-lookup"><span data-stu-id="de5c8-121">Give the user time to digest your content.</span></span>  <span data-ttu-id="de5c8-122">Es ist zwar wichtig, dass die Benutzer schnell zum wichtigsten Teil gelangen, aber nur mithilfe entsprechender Pausen können sie den Wert der App richtig erkennen.</span><span class="sxs-lookup"><span data-stu-id="de5c8-122">While getting them to the best part fast is important, designing suitable pauses can help them to fully enjoy the experience.</span></span>

## <a name="technical-requirements"></a><span data-ttu-id="de5c8-123">Technische Anforderungen</span><span class="sxs-lookup"><span data-stu-id="de5c8-123">Technical requirements</span></span>

<span data-ttu-id="de5c8-124">Da Demo-Apps den Kunden im Einzelhandel Ihre App optimal präsentieren sollen, ist es wichtig, dass die technischen Anforderungen und Datenschutzrichtlinien des Stores in Bezug auf Demo-Apps für den Einzelhandel eingehalten werden.</span><span class="sxs-lookup"><span data-stu-id="de5c8-124">As retail demo experience apps are meant to showcase the best of your app to retail customers, it is essential that they meet these technical requirements and adhere to privacy regulations that the Store has for all retail demo experience apps.</span></span>
<span data-ttu-id="de5c8-125">Dies kann auch als Checkliste in Vorbereitung auf den Prüfprozess verwendet werden und für Klarheit beim Testen sorgen.</span><span class="sxs-lookup"><span data-stu-id="de5c8-125">This can also be used as a checklist to help you prepare for the validation process and to provide clarity in the testing process.</span></span> <span data-ttu-id="de5c8-126">Beachten Sie, dass diese Anforderungen nicht nur für den Prüfprozess, sondern für die gesamte Lebensdauer der Demo-App für den Einzelhandel (d.h. solange Ihre App auf den Vorführgeräten ausgeführt wird) eingehalten werden müssen.</span><span class="sxs-lookup"><span data-stu-id="de5c8-126">Note that these requirements have to be maintained, not just for the validation process, but for the entire lifetime of the retail demo experience app; as long as your app stays running on the retail demo devices.</span></span>

### <a name="critical-level-requirements"></a><span data-ttu-id="de5c8-127">Kritische Anforderungen</span><span class="sxs-lookup"><span data-stu-id="de5c8-127">Critical level requirements</span></span>

<span data-ttu-id="de5c8-128">RDX-Apps, die diese kritischen Anforderungen nicht erfüllen, werden umgehend von allen Vorführgeräten entfernt.</span><span class="sxs-lookup"><span data-stu-id="de5c8-128">RDX apps that do not meet these critical requirements will be removed from all retail demo devices as soon as possible.</span></span>

* <span data-ttu-id="de5c8-129">Kein Anfordern personenbezogener Informationen</span><span class="sxs-lookup"><span data-stu-id="de5c8-129">No asking for Personal Identifiable Information (PII)</span></span>

    <span data-ttu-id="de5c8-130">Die App darf Kunden nicht nach personenbezogenen Informationen fragen.</span><span class="sxs-lookup"><span data-stu-id="de5c8-130">The app is not allowed to ask customers for any personal identifiable information.</span></span>  <span data-ttu-id="de5c8-131">Dies umfasst Microsoft-Kontoinformationen, Kontaktdetails usw.</span><span class="sxs-lookup"><span data-stu-id="de5c8-131">This includes all Microsoft account information, contact details etc.</span></span>

* <span data-ttu-id="de5c8-132">Fehlerfreie Ausführung</span><span class="sxs-lookup"><span data-stu-id="de5c8-132">Error free experience</span></span>

    <span data-ttu-id="de5c8-133">Ihr App muss fehlerfrei funktionieren.</span><span class="sxs-lookup"><span data-stu-id="de5c8-133">Your app must run with no errors.</span></span> <span data-ttu-id="de5c8-134">Außerdem dürfen keine Fehler-Pop-ups oder -Benachrichtigungen angezeigt werden, wenn Kunden die Vorführgeräte verwenden.</span><span class="sxs-lookup"><span data-stu-id="de5c8-134">Additionally, no error pop ups or notifications should be shown to customers using the retail demo devices.</span></span> <span data-ttu-id="de5c8-135">Dies ist wichtig, da wir uns den Kunden von unserer besten Seite zeigen möchten – und diese muss fehlerfrei sein.</span><span class="sxs-lookup"><span data-stu-id="de5c8-135">This is important as we want to showcase our best to customers and the best should be error free.</span></span>
    <span data-ttu-id="de5c8-136">Zudem werfen Fehler ein schlechtes Licht auf die App, Ihr Unternehmen, das Gerät, auf dem die App ausgeführt wird, den Gerätehersteller und Microsoft selbst.</span><span class="sxs-lookup"><span data-stu-id="de5c8-136">Another reason is that errors reflect negatively on the app itself, your brand, the device which the app is running on, the device's manufacturer's brand, and Microsoft's brand as well.</span></span>

* <span data-ttu-id="de5c8-137">Testmodus für kostenpflichtige Apps</span><span class="sxs-lookup"><span data-stu-id="de5c8-137">Paid apps must have a Trial mode</span></span>

    <span data-ttu-id="de5c8-138">Damit Apps auf Vorführgeräten installiert werden können, müssen sie entweder kostenlos sein oder über einen Testmodus verfügen.</span><span class="sxs-lookup"><span data-stu-id="de5c8-138">In order for apps to be installed on retail demo devices, your app either needs to be a free app or have an established Trial mode.</span></span>  <span data-ttu-id="de5c8-139">Kunden, die sich in einem Laden etwas ansehen, möchten dafür nicht zahlen.</span><span class="sxs-lookup"><span data-stu-id="de5c8-139">Customers aren't looking to pay for an experience in a retail store.</span></span> <span data-ttu-id="de5c8-140">Weitere Informationen finden Sie unter [Ausschließen oder Einschränken von Features in einer Testversion](https://msdn.microsoft.com/windows/uwp/monetize/exclude-or-limit-features-in-a-trial-version-of-your-app).</span><span class="sxs-lookup"><span data-stu-id="de5c8-140">For more information, see [Exclude or limit features in a trial version](https://msdn.microsoft.com/windows/uwp/monetize/exclude-or-limit-features-in-a-trial-version-of-your-app)</span></span>

### <a name="high-priority-requirements"></a><span data-ttu-id="de5c8-141">Anforderungen mit hoher Priorität</span><span class="sxs-lookup"><span data-stu-id="de5c8-141">High priority requirements</span></span>

<span data-ttu-id="de5c8-142">Bei RDX-Apps, die diese Anforderungen mit hoher Priorität nicht erfüllen, muss sofort untersucht werden, wie das Problem behoben werden kann.</span><span class="sxs-lookup"><span data-stu-id="de5c8-142">RDX apps that do not meet these high priority requirements need to be investigated for a fix immediately.</span></span> <span data-ttu-id="de5c8-143">Wenn eine umgehende Problembehebung nicht möglich ist, kann diese App von allen Vorführgeräten entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="de5c8-143">If no immediate fix is found, this app may be removed from all retail demo devices.</span></span>

* <span data-ttu-id="de5c8-144">Einprägsame Offline-Erfahrung</span><span class="sxs-lookup"><span data-stu-id="de5c8-144">Memorable offline experience</span></span>

    <span data-ttu-id="de5c8-145">Ihre Demo-App für den Einzelhandel muss eine tolle Offline-Erfahrung bieten, da etwa 50% der Geräte an Einzelhandelsstandorten offline sind.</span><span class="sxs-lookup"><span data-stu-id="de5c8-145">Your retail demo experience app needs to demonstrate a great offline experience as about 50% of the devices are offline at retail locations.</span></span> <span data-ttu-id="de5c8-146">Dadurch wird sichergestellt, dass das Erlebnis für die Kunden auch dann positiv ist, wenn sie offline mit Ihrer App interagieren.</span><span class="sxs-lookup"><span data-stu-id="de5c8-146">This is to ensure that customers interacting with your app offline are still able to have a meaningful and positive experience.</span></span>

* <span data-ttu-id="de5c8-147">Aktualisierte Content-Erfahrung</span><span class="sxs-lookup"><span data-stu-id="de5c8-147">Updated content experience</span></span>

    <span data-ttu-id="de5c8-148">Damit die Kunden einen guten Eindruck von Ihrer App erhalten, muss diese immer aktuell sein, und Kunden sollten nicht aufgefordert werden, Aktualisierungen durchzuführen, wenn die App online ist.</span><span class="sxs-lookup"><span data-stu-id="de5c8-148">To deliver a great experience, your app needs to be always up to date and customers should never be prompted for application updates when your app is online.</span></span>

* <span data-ttu-id="de5c8-149">Keine anonyme Kommunikation</span><span class="sxs-lookup"><span data-stu-id="de5c8-149">No anonymous communication</span></span>

    <span data-ttu-id="de5c8-150">Da Kunden, die ein Vorführgerät nutzen, anonyme Benutzer sind, dürfen sie über das Gerät keine Nachrichten versenden oder Inhalte freigeben.</span><span class="sxs-lookup"><span data-stu-id="de5c8-150">Since a customer using a retail demo device is an anonymous user, they should not be able to message or share content from the device.</span></span>

* <span data-ttu-id="de5c8-151">Bereitstellen einer einheitlichen Benutzererfahrung mithilfe des Bereinigungsprozesses</span><span class="sxs-lookup"><span data-stu-id="de5c8-151">Deliver consistent experience by utilizing the clean up process</span></span>

    <span data-ttu-id="de5c8-152">Die Verwendung eines Vorführgeräts sollte für alle Kunden gleich sein.</span><span class="sxs-lookup"><span data-stu-id="de5c8-152">Every customer should have the same experience when they walk up to a retail demo device.</span></span> <span data-ttu-id="de5c8-153">Verwenden Sie daher den [Bereinigungsprozess](#clean-up-process) für Ihre App, damit diese nach jeder Verwendung zum gleichen Standardzustand zurückkehrt. So wird Kunden nicht angezeigt, was die vorherigen Kunden ausgeführt haben.</span><span class="sxs-lookup"><span data-stu-id="de5c8-153">Your app should utilize [clean up process](#clean-up-process) to return to the same default state after each use as we do not want the next customer to see what the last customer left behind.</span></span>  <span data-ttu-id="de5c8-154">Dies umfasst z.B. Punktestände, Erfolge und aufgehobene Sperren.</span><span class="sxs-lookup"><span data-stu-id="de5c8-154">This includes scoreboards, achievements, and unlocks.</span></span>

* <span data-ttu-id="de5c8-155">Altersgerechte Inhalte</span><span class="sxs-lookup"><span data-stu-id="de5c8-155">Age appropriate content</span></span>

    <span data-ttu-id="de5c8-156">Alle Inhalte von Demo-Apps für den Einzelhandel müssen für Jugendliche oder eine jüngere Altersklasse freigegeben sein.</span><span class="sxs-lookup"><span data-stu-id="de5c8-156">All retail demo experience app content needs to be assigned a Teen or lower rating category.</span></span> <span data-ttu-id="de5c8-157">Weitere Informationen finden Sie unter [Einstufung Ihrer App durch die IARC](https://www.globalratings.com/for-developers.aspx) und [ESRB-Bewertung](https://www.esrb.org/ratings/ratings_guide.aspx).</span><span class="sxs-lookup"><span data-stu-id="de5c8-157">For more information, see [Getting your app rated by IARC](https://www.globalratings.com/for-developers.aspx) and [ESRB ratings](https://www.esrb.org/ratings/ratings_guide.aspx).</span></span>

### <a name="medium-priority-requirements"></a><span data-ttu-id="de5c8-158">Anforderungen mit mittlerer Priorität</span><span class="sxs-lookup"><span data-stu-id="de5c8-158">Medium priority requirements</span></span>

<span data-ttu-id="de5c8-159">Das Windows-Team für den Einzelhandel setzt sich unter Umständen direkt mit Entwicklern in Verbindung, um mit ihnen zu besprechen, wie diese Probleme behoben werden können.</span><span class="sxs-lookup"><span data-stu-id="de5c8-159">The Windows Retail Store team may reach out to developers directly to set up a discussion on how to fix these issues.</span></span>

* <span data-ttu-id="de5c8-160">Möglichkeit zur Ausführung auf verschiedenen Geräten</span><span class="sxs-lookup"><span data-stu-id="de5c8-160">Ability to run successfully over a range of devices</span></span>

    <span data-ttu-id="de5c8-161">Demo-Apps für den Einzelhandel müssen auf allen Geräten (einschließlich leistungsschwächeren Geräten) problemlos ausgeführt werden können.</span><span class="sxs-lookup"><span data-stu-id="de5c8-161">Retail demo experience apps must run well on all devices, including devices with low-end specifications.</span></span> <span data-ttu-id="de5c8-162">Wenn die Demo-App für den Einzelhandel auf Geräten installiert wird, die die Mindestspezifikationen zum Ausführen der App nicht erfüllt, müssen die Benutzer klar darauf hingewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="de5c8-162">If the retail demo experience app is installed on devices that did not meet the minimum specifications to run the app, the app needs to clearly inform the user about this.</span></span> <span data-ttu-id="de5c8-163">Die Mindestgeräteanforderungen müssen bekanntgegeben werden, damit die App immer mit höchster Leistung ausgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="de5c8-163">Minimum device requirements has to be made known so that the app can always run with high performance.</span></span>

* <span data-ttu-id="de5c8-164">Erfüllen der Größenanforderungen für Vorführgeräte</span><span class="sxs-lookup"><span data-stu-id="de5c8-164">Meet retail store app size requirements</span></span>

    <span data-ttu-id="de5c8-165">Die App darf eine Größe von 800MB nicht übersteigen.</span><span class="sxs-lookup"><span data-stu-id="de5c8-165">The app must be smaller than 800MB.</span></span> <span data-ttu-id="de5c8-166">Wenden Sie sich direkt an das Windows-Team für den Einzelhandel, wenn Ihre Demo-App für den Einzelhandel den Größenanforderungen nicht entspricht.</span><span class="sxs-lookup"><span data-stu-id="de5c8-166">Contact the Windows Retail Store team directly for further discussion if your retail demo experience app do not meet the size requirements.</span></span>

## <a name="preparing-codebase-for-retail-demo-mode-development"></a><span data-ttu-id="de5c8-167">Vorbereiten der Codebasis für den Demomodus für den Einzelhandel</span><span class="sxs-lookup"><span data-stu-id="de5c8-167">Preparing codebase for Retail Demo Mode development</span></span>

<span data-ttu-id="de5c8-168">Die Eigenschaft [**IsDemoModeEnabled**](https://docs.microsoft.com/uwp/api/windows.system.profile.retailinfo.isdemomodeenabled) in der Hilfsklasse [**RetailInfo**](https://docs.microsoft.com/uwp/api/Windows.System.Profile.RetailInfo), die dem Namespace [Windows.System.Profile](https://docs.microsoft.com/uwp/api/windows.system.profile) im Windows 10 SDK angehört, ist ein Boolescher Wert, der angibt, welcher Codepfad Ihrer Anwendung im _Normalmodus_ oder im _Einzelhandelsmodus_ ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="de5c8-168">The [**IsDemoModeEnabled**](https://docs.microsoft.com/uwp/api/windows.system.profile.retailinfo.isdemomodeenabled) property in the [**RetailInfo**](https://docs.microsoft.com/uwp/api/Windows.System.Profile.RetailInfo) utility class, which is part of the [Windows.System.Profile](https://docs.microsoft.com/uwp/api/windows.system.profile) namespace in the Windows 10 SDK, is used as a Boolean indicator to specify which code path your application runs on - the _normal_ mode or the _retail_ mode.</span></span>

<span data-ttu-id="de5c8-169">Wenn [**IsDemoModeEnabled**](https://docs.microsoft.com/uwp/api/windows.system.profile.retailinfo.isdemomodeenabled) „true“ zurückgibt, können Sie mithilfe von [**RetailInfo.Properties**](https://docs.microsoft.com/uwp/api/windows.system.profile.retailinfo.properties) einen Satz von Eigenschaften zum Gerät abfragen, um eine besser angepasste Verwendung der Demo-App zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="de5c8-169">When [**IsDemoModeEnabled**](https://docs.microsoft.com/uwp/api/windows.system.profile.retailinfo.isdemomodeenabled) returns true, you can query for a set of properties about the device using [**RetailInfo.Properties**](https://docs.microsoft.com/uwp/api/windows.system.profile.retailinfo.properties) to build a more customized retail demo experience.</span></span> <span data-ttu-id="de5c8-170">Diese Eigenschaften umfassen [**ManufacturerName**](https://docs.microsoft.com/uwp/api/windows.system.profile.knownretailinfoproperties.manufacturername), [**Screensize**](https://docs.microsoft.com/uwp/api/windows.system.profile.knownretailinfoproperties.screensize), [**Memory**](https://docs.microsoft.com/uwp/api/windows.system.profile.knownretailinfoproperties.memory) usw.</span><span class="sxs-lookup"><span data-stu-id="de5c8-170">These properties include [**ManufacturerName**](https://docs.microsoft.com/uwp/api/windows.system.profile.knownretailinfoproperties.manufacturername), [**Screensize**](https://docs.microsoft.com/uwp/api/windows.system.profile.knownretailinfoproperties.screensize), [**Memory**](https://docs.microsoft.com/uwp/api/windows.system.profile.knownretailinfoproperties.memory) and so on.</span></span>


## <a name="clean-up-process"></a><span data-ttu-id="de5c8-171">Bereinigungsprozess</span><span class="sxs-lookup"><span data-stu-id="de5c8-171">Clean up process</span></span>

<span data-ttu-id="de5c8-172">Mit dem Bereinigungsprozess werden Vorführgeräte automatisch auf die ursprünglichen Standardeinstellungen zurückgesetzt, wenn für einen bestimmten Zeitraum keine Interaktion mit dem Gerät stattfindet.</span><span class="sxs-lookup"><span data-stu-id="de5c8-172">The clean up process is used to automatically reset retail demo devices back to original default settings when there is no interaction with the device for fixed duration.</span></span> <span data-ttu-id="de5c8-173">Dadurch wird sichergestellt, dass sich die Interaktion mit dem Gerät für alle Benutzer im Geschäft gleich gestaltet.</span><span class="sxs-lookup"><span data-stu-id="de5c8-173">This is to ensure that every user in the retail store can walk up to a device and have the exact default intended experience when interacting with the device.</span></span> <span data-ttu-id="de5c8-174">Beim Entwickeln einer Demo-App für den Einzelhandel sind Kenntnisse darüber wichtig, wann und wie der Bereinigungsprozess ausgelöst wird, was bei der Standardbereinigung ausgeführt wird und wie dies angepasst werden kann, damit der Prozess der beabsichtigten Vorführanwendung entspricht.</span><span class="sxs-lookup"><span data-stu-id="de5c8-174">When developing a retail demo experience app, it is important to understand when and how the clean up process is triggered, what happens during the default clean up process, and learn how to customize this clean up process according to the requirements of your intended retail demo experience.</span></span>

### <a name="when-does-clean-up-begin"></a><span data-ttu-id="de5c8-175">Wann beginnt die Bereinigung?</span><span class="sxs-lookup"><span data-stu-id="de5c8-175">When does clean up begin?</span></span>

<span data-ttu-id="de5c8-176">Die Bereinigung startet nach einer bestimmten Leerlaufzeit.</span><span class="sxs-lookup"><span data-stu-id="de5c8-176">The clean up sequence begins after certain amount of device idle time.</span></span> <span data-ttu-id="de5c8-177">Die Leerlaufzeit beginnt, wenn auf dem keine Touch-, Maus- oder Tastatureingabe mehr erfolgt.</span><span class="sxs-lookup"><span data-stu-id="de5c8-177">Idle time begins count when there is no input from touch, mouse, and keyboard on the device.</span></span>

#### <a name="desktoppc"></a><span data-ttu-id="de5c8-178">Desktop/PC</span><span class="sxs-lookup"><span data-stu-id="de5c8-178">Desktop/PC</span></span>

<span data-ttu-id="de5c8-179">Nach 120 Sekunden Leerlaufzeit wird auf dem Gerät das Leerlaufvideo wiedergegeben.</span><span class="sxs-lookup"><span data-stu-id="de5c8-179">After 120 seconds of idle time, the idle attract app video will start playing on the device.</span></span> <span data-ttu-id="de5c8-180">5Sekunden später startet der Bereinigungsprozess.</span><span class="sxs-lookup"><span data-stu-id="de5c8-180">5 seconds later, the cleanup process kicks in.</span></span>

#### <a name="phone"></a><span data-ttu-id="de5c8-181">Telefon</span><span class="sxs-lookup"><span data-stu-id="de5c8-181">Phone</span></span>

<span data-ttu-id="de5c8-182">Nach 60Sekunden Leerlaufzeit wird auf dem Gerät das Leerlaufvideo wiedergegeben, und der Bereinigungsprozess startet sofort.</span><span class="sxs-lookup"><span data-stu-id="de5c8-182">After 60 seconds of idle time, the idle attract app video will start playing on the device and the cleanup process kicks in immediately.</span></span>

### <a name="what-happens-during-a-default-clean-up-process"></a><span data-ttu-id="de5c8-183">Was geschieht bei einem Standardbereinigungsprozess?</span><span class="sxs-lookup"><span data-stu-id="de5c8-183">What happens during a default clean up process?</span></span>

#### <a name="step-1-clean-up"></a><span data-ttu-id="de5c8-184">Schritt1: Bereinigen</span><span class="sxs-lookup"><span data-stu-id="de5c8-184">Step 1: clean up</span></span>
* <span data-ttu-id="de5c8-185">Alle Win32- und Store-Apps werden geschlossen.</span><span class="sxs-lookup"><span data-stu-id="de5c8-185">All Win32 and store apps are closed</span></span>
* <span data-ttu-id="de5c8-186">Alle Dateien in bekannten Ordnern wie __Bilder__, __Videos__, __Musik__, __Dokumente__, __SavedPictures__, __CameraRoll__, __Desktop__ und __Downloads__ Ordner werden gelöscht.</span><span class="sxs-lookup"><span data-stu-id="de5c8-186">All files in known folders like __Pictures__, __Videos__, __Music__, __Documents__, __SavedPictures__, __CameraRoll__, __Desktop__ and __Downloads__ folders are deleted</span></span>
* <span data-ttu-id="de5c8-187">Unstrukturierte und strukturierte Roamingzustände werden gelöscht.</span><span class="sxs-lookup"><span data-stu-id="de5c8-187">Unstructured and structured roaming states are deleted</span></span>
* <span data-ttu-id="de5c8-188">Strukturierte lokale Zustände werden gelöscht.</span><span class="sxs-lookup"><span data-stu-id="de5c8-188">Structured local states are deleted</span></span>

#### <a name="step-2-set-up"></a><span data-ttu-id="de5c8-189">Schritt2: Einrichten</span><span class="sxs-lookup"><span data-stu-id="de5c8-189">Step 2: Set up</span></span>
* <span data-ttu-id="de5c8-190">Offlinegeräte: Ordner bleiben leer</span><span class="sxs-lookup"><span data-stu-id="de5c8-190">For offline devices: Folders remain empty</span></span>
* <span data-ttu-id="de5c8-191">Onlinegeräte: Demoressourcen für den Einzelhandel können vom Microsoft Store per Push an das Gerät übertragen werden.</span><span class="sxs-lookup"><span data-stu-id="de5c8-191">For online devices: Retail demo assets can be pushed to the device from the Microsoft Store</span></span>

### <a name="how-to-store-data-across-user-sessions"></a><span data-ttu-id="de5c8-192">Wie kann ich Daten sitzungsübergreifend speichern?</span><span class="sxs-lookup"><span data-stu-id="de5c8-192">How to store data across user sessions?</span></span>

<span data-ttu-id="de5c8-193">Wenn Sie Daten sitzungsübergreifend speichern möchten, können Sie die Informationen in __ApplicationData.Current.TemporaryFolder__ speichern, da der Standardbereinigungsprozess die Daten in diesem Ordner nicht automatisch löscht.</span><span class="sxs-lookup"><span data-stu-id="de5c8-193">If you want to store data across user sessions, you can store information in __ApplicationData.Current.TemporaryFolder__ as the default clean up process does not automatically delete data in this folder.</span></span> <span data-ttu-id="de5c8-194">Die mithilfe von *LocalState* gespeicherten Informationen werden bei der Bereinigung gelöscht.</span><span class="sxs-lookup"><span data-stu-id="de5c8-194">Note that information stored using *LocalState* is deleted during the clean up process.</span></span>

### <a name="how-to-customize-the-clean-up-process"></a><span data-ttu-id="de5c8-195">Wie kann ich den Bereinigungsprozess anpassen?</span><span class="sxs-lookup"><span data-stu-id="de5c8-195">How to customize the clean up process?</span></span>

<span data-ttu-id="de5c8-196">Wenn Sie den Bereinigungsprozess anpassen möchten, müssen Sie den `Microsoft-RetailDemo-Cleanup`-App-Dienst in Ihrer App implementieren.</span><span class="sxs-lookup"><span data-stu-id="de5c8-196">If you wish to customize the clean up process, you need to implement the `Microsoft-RetailDemo-Cleanup` app service into your app.</span></span>

<span data-ttu-id="de5c8-197">Szenarien, bei denen eine benutzerdefinierte Bereinigungslogik erforderlich ist, umfassen das Ausführen einer umfassenden Einrichtung, das Herunterladen und Zwischenspeichern von Daten oder das Beibehalten der *LocalState*-Daten.</span><span class="sxs-lookup"><span data-stu-id="de5c8-197">Scenarios where a custom clean up logic is needed includes running an expensive setup, downloading and caching data or not wanting *LocalState* data to be deleted.</span></span>

<span data-ttu-id="de5c8-198">Schritt1: Deklarieren des _Microsoft-RetailDemo-Cleanup_-Diensts in Ihrem Anwendungsmanifest</span><span class="sxs-lookup"><span data-stu-id="de5c8-198">Step 1: Declare the _Microsoft-RetailDemo-Cleanup_ service in your application manifest.</span></span>
``` CSharp
  <Applications>
      <Extensions>
        <uap:Extension Category="windows.appService" EntryPoint="MyCompany.MyApp.RDXCustomCleanupTask">
          <uap:AppService Name="Microsoft-RetailDemo-Cleanup" />
        </uap:Extension>
      </Extensions>
   </Application>
  </Applications>

```

<span data-ttu-id="de5c8-199">Schritt2: Implementieren der benutzerdefinierten Bereinigungslogik unter der _AppdataCleanup_-Funktion mithilfe der folgenden Beispielvorlage.</span><span class="sxs-lookup"><span data-stu-id="de5c8-199">Step 2: Implement your custom clean up logic under the _AppdataCleanup_ case function using the sample template below.</span></span>
``` CSharp
using System;
using System.IO;
using System.Runtime.Serialization.Json;
using System.Threading;
using System.Threading.Tasks;
using Windows.ApplicationModel.AppService;
using Windows.ApplicationModel.Background;
using Windows.Foundation.Collections;
using Windows.Storage;

namespace MyCompany.MyApp
{
    public sealed class RDXCustomCleanupTask : IBackgroundTask
    {
        BackgroundTaskCancellationReason _cancelReason = BackgroundTaskCancellationReason.Abort;
        BackgroundTaskDeferral _deferral = null;
        IBackgroundTaskInstance _taskInstance = null;
        AppServiceConnection _appServiceConnection = null;

        const string MessageCommand = "Command";

        public void Run(IBackgroundTaskInstance taskInstance)
        {
            // Get the deferral object from the task instance, and take a reference to the taskInstance;
            _deferral = taskInstance.GetDeferral();
            _taskInstance = taskInstance;
            _taskInstance.Canceled += new BackgroundTaskCanceledEventHandler(OnCanceled);

            AppServiceTriggerDetails appService = _taskInstance.TriggerDetails as AppServiceTriggerDetails;
            if ((appService != null) && (appService.Name == "Microsoft-RetailDemo-Cleanup"))
            {
                _appServiceConnection = appService.AppServiceConnection;
                _appServiceConnection.RequestReceived += _appServiceConnection_RequestReceived;
                _appServiceConnection.ServiceClosed += _appServiceConnection_ServiceClosed;
            }
            else
            {
                _deferral.Complete();
            }
        }

        void _appServiceConnection_ServiceClosed(AppServiceConnection sender, AppServiceClosedEventArgs args)
        {
        }

        async void _appServiceConnection_RequestReceived(AppServiceConnection sender, AppServiceRequestReceivedEventArgs args)
        {
            //Get a deferral because we will be calling async code
            AppServiceDeferral requestDeferral = args.GetDeferral();
            string command = null;
            var returnData = new ValueSet();

            try
            {
                ValueSet message = args.Request.Message;
                if (message.ContainsKey(MessageCommand))
                {
                    command = message[MessageCommand] as string;
                }

                if (command != null)
                {
                    switch (command)
                    {
                        case "AppdataCleanup":
                            {
                                // Do custom clean up logic here
                                break;
                            }
                    }
                }
            }
            catch (Exception e)
            {
            }
            finally
            {
                requestDeferral.Complete();
                // Also release the task deferral since we only process one request per instance.
                _deferral.Complete();
            }
        }

        private void OnCanceled(IBackgroundTaskInstance sender, BackgroundTaskCancellationReason reason)
        {
            _cancelReason = reason;
        }
    }
}
```

## <a name="related-links"></a><span data-ttu-id="de5c8-200">Verwandte Links</span><span class="sxs-lookup"><span data-stu-id="de5c8-200">Related links</span></span>

* [<span data-ttu-id="de5c8-201">Speichern und Abrufen von App-Daten</span><span class="sxs-lookup"><span data-stu-id="de5c8-201">Store and retrieve app data</span></span>](https://msdn.microsoft.com/windows/uwp/app-settings/store-and-retrieve-app-data)
* [<span data-ttu-id="de5c8-202">Erstellen und Nutzen eines App-Diensts</span><span class="sxs-lookup"><span data-stu-id="de5c8-202">How to create and consume an app service</span></span>](https://msdn.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service)
* [<span data-ttu-id="de5c8-203">Lokalisieren von App-Inhalten</span><span class="sxs-lookup"><span data-stu-id="de5c8-203">Localizing app contents</span></span>](https://msdn.microsoft.com/windows/uwp/globalizing/globalizing-portal)


 

 
