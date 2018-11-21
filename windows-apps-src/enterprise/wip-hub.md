---
author: normesta
Description: This is a hub topic covering the full developer picture of how Windows Information Protection (WIP) relates to files, buffers, clipboard, networking, background tasks, and data protection under lock.
MS-HAID: dev\_enterprise.edp\_hub
MSHAttr: PreferredLib:/library/windows/apps
Search.Product: eADQiWindows 10XVcnh
title: Windows Information Protection (WIP)
ms.author: normesta
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, Uwp, Windows Information Protection, Unternehmensdaten, Schutz von Unternehmensdaten, edp, optimierte Apps
ms.assetid: 08f0cfad-f15d-46f7-ae7c-824a8b1c44ea
ms.localizationpriority: medium
ms.openlocfilehash: dec05e663e6ca7390dc3974b8a3cde2971b50426
ms.sourcegitcommit: cbe7cf620622a5e4df7414f9e38dfecec1cfca99
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2018
ms.locfileid: "7433687"
---
# <a name="windows-information-protection-wip"></a><span data-ttu-id="25131-103">Windows Information Protection (WIP)</span><span class="sxs-lookup"><span data-stu-id="25131-103">Windows Information Protection (WIP)</span></span>

<span data-ttu-id="25131-104">__Hinweis__ Die Windows Information Protection (WIP)-Richtlinie kann auf Windows 10, Version 1607 angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="25131-104">__Note__ Windows Information Protection (WIP) policy can be applied to Windows 10, version 1607.</span></span>

<span data-ttu-id="25131-105">WIP schützt Daten, die zu einem Unternehmen gehören, indem Richtlinien durchgesetzt werden, die von dem Unternehmen definiert sind.</span><span class="sxs-lookup"><span data-stu-id="25131-105">WIP protects data that belongs to an organization by enforcing policies that are defined by the organization.</span></span> <span data-ttu-id="25131-106">Wenn Ihre App diese Richtlinien enthält, unterliegen alle Daten von der App den Richtlinien.</span><span class="sxs-lookup"><span data-stu-id="25131-106">If your app is included in those polices, all data produced by your app is subject to policy restrictions.</span></span> <span data-ttu-id="25131-107">Dieses Thema unterstützt Sie beim Erstellen von Apps, die diese Richtlinien besser durchsetzen, ohne Auswirkung auf persönliche Daten des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="25131-107">This topic helps you to build apps that more gracefully enforce these policies without having any impact on the user's personal data.</span></span>
<iframe src="https://channel9.msdn.com/Blogs/Windows-Development-for-the-Enterprise/Securing-Enterprise-Data-with-Windows-Information-Protection/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>

## <a name="first-what-is-wip"></a><span data-ttu-id="25131-108">Als Erstes: Was ist WIP?</span><span class="sxs-lookup"><span data-stu-id="25131-108">First, what is WIP?</span></span>

<span data-ttu-id="25131-109">WIP ist ein Satz von Features auf Desktops, Laptops, Tablets und Smartphones, welche das Mobile Device Management (MDM)-System und das System zur mobilen Anwendungsverwaltung (Mobile Application Management; MAM) des Unternehmens unterstützen.</span><span class="sxs-lookup"><span data-stu-id="25131-109">WIP is a set of features on desktops, laptops, tablets, and phones that support the organization's Mobile Device Management (MDM) and Mobile Application Management (MAM) system.</span></span>

<span data-ttu-id="25131-110">WIP kann mit MDM dem Unternehmen mehr Kontrolle darüber geben, wie Daten des Unternehmens auf Geräten, die das Unternehmen verwaltet, behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="25131-110">WIP together with MDM gives the organization greater control over how its data is handled on devices that the organization manages.</span></span> <span data-ttu-id="25131-111">In einigen Fällen bringen Benutzer Geräte mit zur Arbeit und registrieren sie nicht im MDM der Organisation.</span><span class="sxs-lookup"><span data-stu-id="25131-111">Sometimes users bring devices to work and do not enroll them in the organization's MDM.</span></span>  <span data-ttu-id="25131-112">In diesen Fällen können Organisationen MAM verwenden, um eine bessere Kontrolle über die Behandlung ihrer Daten in bestimmten Branchen-Apps zu erhalten, die Benutzer auf dem Gerät installieren.</span><span class="sxs-lookup"><span data-stu-id="25131-112">In those cases, organizations can use MAM to achieve greater control over how their data is handled on specific line of business apps that users install on their device.</span></span>

<span data-ttu-id="25131-113">Mit MDM oder MAM können Administratoren angeben, welche Apps auf Dateien zugreifen dürfen, die dem Unternehmen gehören, und ob Benutzer Daten aus diesen Dateien kopieren und dann in persönliche Dokumente einsetzen können.</span><span class="sxs-lookup"><span data-stu-id="25131-113">using MDM or MAM, administrators can identify which apps are allowed to access files that belong to the organization and whether users can copy data from those files and then paste that data into personal documents.</span></span>

<span data-ttu-id="25131-114">So funktioniert’s.</span><span class="sxs-lookup"><span data-stu-id="25131-114">Here's how it works.</span></span> <span data-ttu-id="25131-115">Benutzer registrieren ihre Geräte im System für Verwaltung mobiler Geräte (Mobile Device Management, MDM).</span><span class="sxs-lookup"><span data-stu-id="25131-115">Users enroll their devices into the organization's mobile device management (MDM) system.</span></span> <span data-ttu-id="25131-116">Ein Administrator im Verwaltungsunternehmen verwendet Microsoft Intune oder System Center Configuration Manager (SCCM) zur Definition einer Richtlinie und anschließender Bereitstellung auf den registrierten Geräten.</span><span class="sxs-lookup"><span data-stu-id="25131-116">An administrator in the managing organization uses Microsoft Intune or System Center Configuration Manager (SCCM) to define and then deploy a policy to the enrolled devices.</span></span>

<span data-ttu-id="25131-117">Wenn Benutzer ihre Geräte nicht registrieren müssen, verwenden Administratoren ihr MAM-System, um eine Richtlinie zu definieren und bereitzustellen, die für spezifische Apps gilt.</span><span class="sxs-lookup"><span data-stu-id="25131-117">If users aren't required to enroll their devices, administrators will use their MAM system to define and deploy a policy that applies to specific apps.</span></span> <span data-ttu-id="25131-118">Wenn Benutzer diese Apps installieren, erhalten sie die zugehörige Richtlinie.</span><span class="sxs-lookup"><span data-stu-id="25131-118">When users install any of those apps, they'll receive the associated policy.</span></span>

<span data-ttu-id="25131-119">Diese Richtlinie identifiziert die Apps, die Zugriff auf Unternehmensdaten haben dürfen (auch *Liste der zugelassenen Apps*der Richtlinie genannt).</span><span class="sxs-lookup"><span data-stu-id="25131-119">That policy identifies the apps that can access enterprise data (called the policy's *allowed list*).</span></span> <span data-ttu-id="25131-120">Diese Apps können auf geschützte Unternehmensdateien, virtuelle Private Netzwerke (VPN) und Unternehmensdaten in der Zwischenablage oder über einen Freigabe-Vertrag zugreifen.</span><span class="sxs-lookup"><span data-stu-id="25131-120">These apps can access enterprise protected files, Virtual Private Networks (VPN) and enterprise data on the clipboard or through a share contract.</span></span> <span data-ttu-id="25131-121">Die Richtlinie definiert auch die Regeln, die für die Daten gelten.</span><span class="sxs-lookup"><span data-stu-id="25131-121">The policy also defines the rules that govern the data.</span></span> <span data-ttu-id="25131-122">Beispielsweise, ob Daten von unternehmenseigenen Dateien kopiert und dann in nicht unternehmenseigene Dateien eingesetzt werden können.</span><span class="sxs-lookup"><span data-stu-id="25131-122">For example, whether data can be copied from enterprise-owned files and then pasted into non enterprise-owned files.</span></span>

<span data-ttu-id="25131-123">Wenn Benutzer die Registrierung ihres Geräts im MDM-System der Organisation aufheben oder Apps deinstallieren, die vom MAM-System der Organisation erkannt werden, können Administratoren Unternehmensdaten remote vom Gerät entfernen.</span><span class="sxs-lookup"><span data-stu-id="25131-123">If users unenroll their device from the organization's MDM system, or uninstall apps identified by the organizations MAM system, administrators can remotely wipe enterprise data from the device.</span></span>

![WIP-Lebenszyklus](images/wip-lifecycle.png)

> **<span data-ttu-id="25131-125">Weitere Informationen zu WIP</span><span class="sxs-lookup"><span data-stu-id="25131-125">Read more about WIP</span></span>** <br>
* [<span data-ttu-id="25131-126">Einführung in Windows Information Protection</span><span class="sxs-lookup"><span data-stu-id="25131-126">Introducing Windows Information Protection</span></span>](https://blogs.technet.microsoft.com/windowsitpro/2016/06/29/introducing-windows-information-protection/)
* [<span data-ttu-id="25131-127">Schützen von Unternehmensdaten mit Windows Information Protection (WIP)</span><span class="sxs-lookup"><span data-stu-id="25131-127">Protect your enterprise data using Windows Information Protection (WIP)</span></span>](https://technet.microsoft.com/library/dn985838(v=vs.85).aspx)

<span data-ttu-id="25131-128">Wenn Ihre App auf der Liste der zugelassenen Apps steht, unterliegen alle von der App erstellten Daten den Einschränkungen der Richtlinien.</span><span class="sxs-lookup"><span data-stu-id="25131-128">If your app is on the allowed list, all data produced by your app is subject to policy restrictions.</span></span> <span data-ttu-id="25131-129">Das bedeutet: Wenn Administratoren den Zugriff des Benutzers auf Unternehmensdaten widerrufen, geht dem Benutzer der Zugriff auf alle Daten verloren, die Ihre App erstellt hat.</span><span class="sxs-lookup"><span data-stu-id="25131-129">That means that if administrators revoke the user's access to enterprise data, those users lose access to all of the data that your app produced.</span></span>

<span data-ttu-id="25131-130">Dies ist in Ordnung, wenn Ihre App nur für Unternehmen entwickelt wurde.</span><span class="sxs-lookup"><span data-stu-id="25131-130">This is fine if your app is designed only for enterprise use.</span></span> <span data-ttu-id="25131-131">Wenn Ihre App Daten erstellt, die die Benutzer als persönlich erachten, sollten Sie Ihre App *optimieren*, intelligent zwischen Unternehmens- und persönlichen Daten zu unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="25131-131">But if your app creates data that users consider personal to them, you'll want to *enlighten* your app to intelligently discern between enterprise and personal data.</span></span> <span data-ttu-id="25131-132">Wir bezeichnen diese Art App *unternehmensoptimiert*, da sie problemlos eine Unternehmensrichtlinie durchsetzen und gleichzeitig die Integrität der persönlichen Daten des Benutzers beibehalten kann.</span><span class="sxs-lookup"><span data-stu-id="25131-132">We call this type of an app *enterprise-enlightened* because it can gracefully enforce enterprise policy while preserving the integrity of the user's personal data.</span></span>

## <a name="create-an-enterprise-enlightened-app"></a><span data-ttu-id="25131-133">Erstellen Sie eine unternehmensoptimierte App</span><span class="sxs-lookup"><span data-stu-id="25131-133">Create an enterprise-enlightened app</span></span>

<span data-ttu-id="25131-134">Verwenden Sie WIP-APIs, um Ihre App zu optimieren und dann als unternehmensoptimiert zu deklarieren.</span><span class="sxs-lookup"><span data-stu-id="25131-134">Use WIP APIs to enlighten your app, and then declare your app as enterprise-enlightened.</span></span>

<span data-ttu-id="25131-135">Optimieren Sie Ihre App, wenn diese für Unternehmens- und persönliche Zwecke verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="25131-135">Enlighten your app if it'll be used for both organizational and personal purposes.</span></span>

<span data-ttu-id="25131-136">Optimierung der App, wenn Sie das Durchsetzen der Richtlinienelemente problemlos behandeln möchten.</span><span class="sxs-lookup"><span data-stu-id="25131-136">Enlighten your app if you want to gracefully handle the enforcement of policy elements.</span></span>

<span data-ttu-id="25131-137">Beispiel: Wenn die Richtlinie Benutzern erlaubt, Unternehmensdaten in einem privaten Dokument einzusetzen, können Sie verhindern, dass Benutzer auf ein Zustimmungsdialogfeld reagieren müssen, bevor sie die Daten einsetzen können.</span><span class="sxs-lookup"><span data-stu-id="25131-137">For example, if policy allows users to paste enterprise data into a personal document, you can prevent users from having to respond to a consent dialog before they paste the data.</span></span> <span data-ttu-id="25131-138">Auf ähnliche Weise können Sie benutzerdefinierte Dialogfelder zu Informationszwecken als Antwort auf diese Art von Ereignissen darstellen.</span><span class="sxs-lookup"><span data-stu-id="25131-138">Similarly, you can present custom informational dialog boxes in response to these sorts of events.</span></span>

<span data-ttu-id="25131-139">Wenn Sie bereit sind, die App zu optimieren, sehen Sie sich eines dieser Handbücher an:</span><span class="sxs-lookup"><span data-stu-id="25131-139">If you're ready to enlighten your app, see one of these guides:</span></span>

**<span data-ttu-id="25131-140">Für universelle Windows-Plattform (UWP)-apps, die Sie erstellen, indem Sie mithilfe von c#</span><span class="sxs-lookup"><span data-stu-id="25131-140">For Universal Windows Platform (UWP) apps that you build by using C#</span></span>**

<span data-ttu-id="25131-141">[Entwicklerhandbuch für Windows Information Protection (WIP)](wip-dev-guide.md)</span><span class="sxs-lookup"><span data-stu-id="25131-141">[Windows Information Protection (WIP) developer guide](wip-dev-guide.md).</span></span>

**<span data-ttu-id="25131-142">Für Desktop-Apps, die Sie mit C++ erstellen</span><span class="sxs-lookup"><span data-stu-id="25131-142">For Desktop apps that you build by using C++</span></span>**

<span data-ttu-id="25131-143">[Entwicklerhandbuch für Windows Information Protection (C++)](http://go.microsoft.com/fwlink/?LinkId=822192)</span><span class="sxs-lookup"><span data-stu-id="25131-143">[Windows Information Protection (WIP) developer guide (C++)](http://go.microsoft.com/fwlink/?LinkId=822192).</span></span>


## <a name="create-non-enlightened-enterprise-app"></a><span data-ttu-id="25131-144">Erstellen einer nicht für Unternehmen optimierten App</span><span class="sxs-lookup"><span data-stu-id="25131-144">Create non-enlightened enterprise app</span></span>

<span data-ttu-id="25131-145">Wenn Sie eine Branchen-App erstellen, die nicht zur privaten Verwendung vorgesehen ist, müssen Sie diese nicht optimieren.</span><span class="sxs-lookup"><span data-stu-id="25131-145">if you're creating an Line of Business (LOB) app that is not intended for personal use, you might not have to enlighten it.</span></span>

### <a name="windows-desktop-apps"></a><span data-ttu-id="25131-146">Windows-Desktop-Apps</span><span class="sxs-lookup"><span data-stu-id="25131-146">Windows desktop apps</span></span>
<span data-ttu-id="25131-147">Sie müssen eine Windows-Desktop-App nicht optimieren, sollten aber Ihre App testen, um sicherzustellen, dass sie ordnungsgemäß unter der Richtlinie funktioniert.</span><span class="sxs-lookup"><span data-stu-id="25131-147">You don't need to enlighten a Windows desktop app but you should test your app to ensure that it functions properly under policy.</span></span> <span data-ttu-id="25131-148">Starten Sie beispielsweise Ihre App, verwenden Sie sie, und heben Sie dann die Registrierung des Geräts im MDM auf.</span><span class="sxs-lookup"><span data-stu-id="25131-148">For example, start your app, use it, then unenroll the device from MDM.</span></span> <span data-ttu-id="25131-149">Stellen Sie dann sicher, dass die App gestartet werden kann.</span><span class="sxs-lookup"><span data-stu-id="25131-149">Then, make sure the app can start again.</span></span> <span data-ttu-id="25131-150">Wenn für den Betrieb der App wichtige Dateien verschlüsselt werden, kann die App möglicherweise nicht gestartet werden.</span><span class="sxs-lookup"><span data-stu-id="25131-150">If files critical to the operation of the app are encrypted, the app might not start.</span></span> <span data-ttu-id="25131-151">Überprüfen Sie außerdem die Dateien, mit denen Ihre App interagiert, um sicherzustellen, dass Ihre App nicht versehentlich private Dateien des Benutzers verschlüsselt.</span><span class="sxs-lookup"><span data-stu-id="25131-151">Also, review the files that your app interacts with to ensure that your app won't inadvertently encrypt files that are personal to the user.</span></span> <span data-ttu-id="25131-152">Dies kann Metadatendateien, Bilder und andere Dinge umfassen.</span><span class="sxs-lookup"><span data-stu-id="25131-152">This might include metadata files, images and other things.</span></span>

<span data-ttu-id="25131-153">Nach dem Test Ihrer App fügen Sie der Ressourcendatei oder Ihrem Projekt dieses Kennzeichen hinzu, und kompilieren Sie die App dann neu.</span><span class="sxs-lookup"><span data-stu-id="25131-153">After you've tested your app, add this flag to the resource file or your project, and then recompile the app.</span></span>

```cpp
MICROSOFTEDPAUTOPROTECTIONALLOWEDAPPINFO EDPAUTOPROTECTIONALLOWEDAPPINFOID
BEGIN
    0x0001
END
```
<span data-ttu-id="25131-154">Die MDM-Richtlinien erfordern zwar kein Kennzeichen, die MAM-Richtlinien allerdings schon.</span><span class="sxs-lookup"><span data-stu-id="25131-154">While MDM policies don't require the flag, MAM policies do.</span></span>

### <a name="uwp-apps"></a><span data-ttu-id="25131-155">UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="25131-155">UWP apps</span></span>

<span data-ttu-id="25131-156">Wenn Ihre App in einer MAM-Richtlinie enthalten sein soll, müssen Sie sie optimieren.</span><span class="sxs-lookup"><span data-stu-id="25131-156">If you expect your app to be included in a MAM policy, you should enlighten it.</span></span> <span data-ttu-id="25131-157">Für Richtlinien, die für Geräte unter MDM bereitgestellt wurden, ist dies nicht erforderlich. Aber wenn Sie Ihre App an Unternehmenskunden verteilen, wird es schwierig, wenn nicht unmöglich, den Typ des verwendeten Richtlinienverwaltungssystems zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="25131-157">Policies deployed to devices under MDM won't require it, but if you distribute your app to organizational consumers, it's difficult if not impossible to determine what type of policy management system they'll use.</span></span> <span data-ttu-id="25131-158">Optimieren Sie Ihre App, um zu gewährleisten, dass Ihre App in beiden Richtlinienverwaltungssystemen (MDM und MAM) funktioniert.</span><span class="sxs-lookup"><span data-stu-id="25131-158">To ensure that your app will work in both types of policy management systems (MDM and MAM), you should enlighten your app.</span></span>






 
