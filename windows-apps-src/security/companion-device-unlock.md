---
title: Entsperren von Windows mit Windows Hello-Begleitgeräten (IoT)
description: Ein Windows Hello-Begleitgerät ist ein Gerät, das in Verbindung mit dem Windows10-Desktopgerät zur Verbesserung der Benutzerauthentifizierung verwendet werden kann. Mit dem Windows Hello-Begleitgeräteframework kann ein Begleitgerät umfangreiche Funktionen für Windows Hello bereitstellen, auch wenn Biometrie nicht verfügbar ist (beispielsweise, wenn das Windows10-Desktopgerät über keine Kamera für die Gesichtsauthentifizierung oder kein Fingerabdrucklesegerät verfügt).
author: msatranjr
ms.author: misatran
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Sicherheit
ms.assetid: 89f3d331-20cd-457b-83e8-1a22aaab2658
ms.localizationpriority: medium
ms.openlocfilehash: ac2e29d5219809058edee2d7a92c2e2475d9752e
ms.sourcegitcommit: f5321b525034e2b3af202709e9b942ad5557e193
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/18/2018
ms.locfileid: "4022572"
---
# <a name="windows-unlock-with-windows-hello-companion-iot-devices"></a><span data-ttu-id="e6322-105">Entsperren von Windows mit Windows Hello-Begleitgeräten (IoT)</span><span class="sxs-lookup"><span data-stu-id="e6322-105">Windows Unlock with Windows Hello companion (IoT) devices</span></span>

<span data-ttu-id="e6322-106">Ein Windows Hello-Begleitgerät ist ein Gerät, das in Verbindung mit dem Windows10-Desktopgerät zur Verbesserung der Benutzerauthentifizierung verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="e6322-106">A Windows Hello companion device is a device that can act in conjunction with your Windows 10 desktop to enhance the user authentication experience.</span></span> <span data-ttu-id="e6322-107">Mit dem Windows Hello-Begleitgeräteframework kann ein Begleitgerät umfangreiche Funktionen für Windows Hello bereitstellen, auch wenn Biometrie nicht verfügbar ist (beispielsweise, wenn das Windows10-Desktopgerät über keine Kamera für die Gesichtsauthentifizierung oder kein Fingerabdrucklesegerät verfügt).</span><span class="sxs-lookup"><span data-stu-id="e6322-107">Using the Windows Hello companion device framework, a companion device can provide a rich experience for Windows Hello even when biometrics are not available (e.g., if the Windows 10 desktop lacks a camera for face authentication or fingerprint reader device, for example).</span></span>

> <span data-ttu-id="e6322-108">**Hinweis** Das Windows Hello-Begleitgeräteframework ist ein spezielles Feature und nicht für alle App-Entwickler verfügbar.</span><span class="sxs-lookup"><span data-stu-id="e6322-108">**Note** The Windows Hello companion device framework is a specialized feature not available to all app developers.</span></span> <span data-ttu-id="e6322-109">Damit dieses Framework verwendet werden kann, muss Ihre App speziell von Microsoft bereitgestellt werden und die eingeschränkte Funktion *SecondaryAuthenticatorFactor* muss im Manifest angegeben sein.</span><span class="sxs-lookup"><span data-stu-id="e6322-109">To use this framework, your app must be specifically provisioned by Microsoft and list the restricted *secondaryAuthenticationFactor* capability in its manifest.</span></span> <span data-ttu-id="e6322-110">Um eine Genehmigung zu erhalten, wenden Sie sich an [cdfonboard@microsoft.com](mailto:cdfonboard@microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="e6322-110">To obtain approval, contact [cdfonboard@microsoft.com](mailto:cdfonboard@microsoft.com).</span></span>

## <a name="introduction"></a><span data-ttu-id="e6322-111">Einführung</span><span class="sxs-lookup"><span data-stu-id="e6322-111">Introduction</span></span>

> <span data-ttu-id="e6322-112">Eine Videoübersicht finden Sie in der Sitzung [Windows Unlock with IoT Devices](https://channel9.msdn.com/Events/Build/2016/P491) von Build 2016 in Channel 9.</span><span class="sxs-lookup"><span data-stu-id="e6322-112">For a video overview, see the [Windows Unlock with IoT Devices](https://channel9.msdn.com/Events/Build/2016/P491) session from Build 2016 on Channel 9.</span></span>

> <span data-ttu-id="e6322-113">Codebeispiele finden Sie im [Windows Hello-Begleitgeräteframework-Github-Repository](https://github.com/Microsoft/companion-device-framework).</span><span class="sxs-lookup"><span data-stu-id="e6322-113">For code samples, see the [Windows Hello companion device framework Github repository](https://github.com/Microsoft/companion-device-framework).</span></span>

### <a name="use-cases"></a><span data-ttu-id="e6322-114">Anwendungsfälle</span><span class="sxs-lookup"><span data-stu-id="e6322-114">Use cases</span></span>

<span data-ttu-id="e6322-115">Das Windows Hello-Begleitgeräteframework kann auf unterschiedliche Weise verwendet werden, um eine erstklassige Windows-Entsperrung mit einem Begleitgerät zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="e6322-115">There are numerous ways one can use the Windows Hello companion device framework to build a great Windows unlock experience with a companion device.</span></span> <span data-ttu-id="e6322-116">Beispiele:</span><span class="sxs-lookup"><span data-stu-id="e6322-116">For example, users could:</span></span>

- <span data-ttu-id="e6322-117">Benutzer können Ihr Begleitgerät per USB am PC anschließen, auf die Schaltfläche des Begleitgeräts tippen und den PC automatisch entsperren.</span><span class="sxs-lookup"><span data-stu-id="e6322-117">Attach their companion device to PC via USB, touch the button on the companion device, and automatically unlock their PC.</span></span>
- <span data-ttu-id="e6322-118">Benutzer können in ihrer Tasche ein Smartphone mit sich führen, das bereits über Bluetooth mit dem PC gekoppelt ist.</span><span class="sxs-lookup"><span data-stu-id="e6322-118">Carry a phone in their pocket that is already paired with PC over Bluetooth.</span></span> <span data-ttu-id="e6322-119">Durch Drücken der LEERTASTE des PCs wird eine Benachrichtigung an ihr Smartphone gesendet.</span><span class="sxs-lookup"><span data-stu-id="e6322-119">Upon hitting the spacebar on their PC, their phone receives a notification.</span></span> <span data-ttu-id="e6322-120">Diese muss zum Entsperren des PCs einfach nur bestätigt werden.</span><span class="sxs-lookup"><span data-stu-id="e6322-120">Approve it and the PC simply unlocks.</span></span>
- <span data-ttu-id="e6322-121">Benutzer können das Begleitgerät an ein NFC-Lesegerät halten und den PC so entsperren.</span><span class="sxs-lookup"><span data-stu-id="e6322-121">Tap their companion device to an NFC reader to quickly unlock their PC.</span></span>
- <span data-ttu-id="e6322-122">Benutzer können ein Fitness-Armband tragen, das den Träger bereits authentifiziert hat.</span><span class="sxs-lookup"><span data-stu-id="e6322-122">Wear a fitness band that has already authenticated the wearer.</span></span> <span data-ttu-id="e6322-123">Wenn sich der Benutzer dem PC nähert und eine spezielle Geste (beispielsweise Klatschen) ausführt, wird der PC entsperrt.</span><span class="sxs-lookup"><span data-stu-id="e6322-123">Upon approaching PC, and by performing a special gesture (like clapping), the PC unlocks.</span></span>

### <a name="biometric-enabled-windows-hello-companion-devices"></a><span data-ttu-id="e6322-124">Biometriefähige Windows Hello-Begleitgeräte</span><span class="sxs-lookup"><span data-stu-id="e6322-124">Biometric enabled Windows Hello companion devices</span></span>

<span data-ttu-id="e6322-125">Falls das Begleitgerät über Biometrieunterstützung verfügt, ist das [Windows-Biometrieframework](https://msdn.microsoft.com/library/windows/hardware/mt608302(v=vs.85).aspx) in manchen Fällen eine bessere Lösung als das Windows Hello-Begleitgeräteframework.</span><span class="sxs-lookup"><span data-stu-id="e6322-125">If the companion device supports biometrics, in some cases the [Windows Biometric framework](https://msdn.microsoft.com/library/windows/hardware/mt608302(v=vs.85).aspx) may be a better solution than the Windows Hello companion device framework.</span></span> <span data-ttu-id="e6322-126">Wenden Sie sich an [cdfonboard@microsoft.com](mailto:cdfonboard@microsoft.com), und wir helfen Ihnen bei der Auswahl des richtigen Ansatzes.</span><span class="sxs-lookup"><span data-stu-id="e6322-126">Please contact [cdfonboard@microsoft.com](mailto:cdfonboard@microsoft.com) and we'll help you pick the right approach.</span></span>

### <a name="components-of-the-solution"></a><span data-ttu-id="e6322-127">Komponenten der Lösung</span><span class="sxs-lookup"><span data-stu-id="e6322-127">Components of the solution</span></span>

<span data-ttu-id="e6322-128">Das folgende Diagramm zeigt die Komponenten der Lösung und wer jeweils für deren Erstellung zuständig ist.</span><span class="sxs-lookup"><span data-stu-id="e6322-128">The diagram below depicts the components of the solution and who is responsible for building them.</span></span>

![Frameworkübersicht](images/companion-device-1.png)

<span data-ttu-id="e6322-130">Das Windows Hello-Begleitgeräteframework wird als Dienst unter Windows implementiert, der in diesem Artikel als Begleitauthentifizierungsdienst bezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="e6322-130">The Windows Hello companion device framework is implemented as a service running on Windows (called the Companion Authentication Service in this article).</span></span> <span data-ttu-id="e6322-131">Dieser Dienst generiert ein Entsperrtoken, das durch einen auf dem Windows Hello-Begleitgerät gespeicherten HMAC-Schlüssel geschützt werden muss.</span><span class="sxs-lookup"><span data-stu-id="e6322-131">This service is responsible for generating an unlock token which needs to be protected by an HMAC key stored on the Windows Hello companion device.</span></span> <span data-ttu-id="e6322-132">Dadurch wird sichergestellt, dass für den Zugriff auf das Entsperrtoken das Windows Hello-Begleitgerät benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="e6322-132">This guarantees that access to the unlock token requires Windows Hello companion device presence.</span></span> <span data-ttu-id="e6322-133">Pro Tupel (PC, Windows-Benutzer) ist jeweils ein eindeutiges Entsperrtoken vorhanden.</span><span class="sxs-lookup"><span data-stu-id="e6322-133">Per each (PC, Windows user) tuple, there will be a unique unlock token.</span></span>

<span data-ttu-id="e6322-134">Die Integration des Windows Hello-Begleitgeräteframeworks erfordert Folgendes:</span><span class="sxs-lookup"><span data-stu-id="e6322-134">Integration with the Windows Hello Companion Device Framework requires:</span></span>

- <span data-ttu-id="e6322-135">Eine aus dem Windows Store heruntergeladene, für das Windows Hello-Begleitgerät bestimmte Begleitgeräte-App für die [universelle Windows-Plattform (UWP)](https://msdn.microsoft.com/windows/uwp/get-started/universal-application-platform-guide).</span><span class="sxs-lookup"><span data-stu-id="e6322-135">A [Universal Windows Platform (UWP)](https://msdn.microsoft.com/windows/uwp/get-started/universal-application-platform-guide) Windows Hello companion device app for the companion device, downloaded from the Windows app store.</span></span> 
- <span data-ttu-id="e6322-136">Die Möglichkeit, auf dem Windows Hello-Begleitgerät zwei 256-Bit-HMAC-Schlüssel zu erstellen und damit HMAC (mit SHA-256) zu generieren.</span><span class="sxs-lookup"><span data-stu-id="e6322-136">The ability to create two 256 bit HMAC keys on the Windows Hello companion device and generate HMAC with it (using SHA-256).</span></span>
- <span data-ttu-id="e6322-137">Ordnungsgemäß konfigurierte Sicherheitsreinstellungen auf dem Windows10-Desktopgerät.</span><span class="sxs-lookup"><span data-stu-id="e6322-137">Security settings on the Windows 10 desktop properly configured.</span></span> <span data-ttu-id="e6322-138">Bevor Windows Hello-Begleitgeräte eingebunden werden können, muss diese PIN für den Begleitauthentifizierungsdienst eingerichtet werden.</span><span class="sxs-lookup"><span data-stu-id="e6322-138">The Companion Authentication Service will require this PIN to be set up before any Windows Hello companion device can be plugged into it.</span></span> <span data-ttu-id="e6322-139">Die Benutzer müssen über „Einstellungen“ > „Konten“ > „Anmeldeoptionen“ eine PIN einrichten.</span><span class="sxs-lookup"><span data-stu-id="e6322-139">The users must set up a PIN via Settings > Accounts > Sign-in options.</span></span>

<span data-ttu-id="e6322-140">Zusätzlich zu den oben genannten Anforderungen ist die Windows Hello-Begleitgeräte-App für Folgendes zuständig:</span><span class="sxs-lookup"><span data-stu-id="e6322-140">In addition to the above requirements, the Windows Hello companion device app is responsible for:</span></span>

- <span data-ttu-id="e6322-141">Benutzeroberfläche und Branding der ersten Registrierung und spätere Aufhebung der Registrierung des Windows Hello-Begleitgeräts</span><span class="sxs-lookup"><span data-stu-id="e6322-141">User experience and branding of initial registration and later de-registration of the Windows Hello companion device.</span></span>
- <span data-ttu-id="e6322-142">Ausführung im Hintergrund, Erkennung des Windows Hello-Begleitgeräts, Kommunikation mit dem Windows Hello-Begleitgerät und Begleitauthentifizierungsdienst</span><span class="sxs-lookup"><span data-stu-id="e6322-142">Running in the background, discovering the Windows Hello companion device, communicating to the Windows Hello companion device and also Companion Authentication Service.</span></span>
- <span data-ttu-id="e6322-143">Fehlerbehandlung</span><span class="sxs-lookup"><span data-stu-id="e6322-143">Error handling</span></span>

<span data-ttu-id="e6322-144">In der Regel werden Begleitgeräte mit einer Ersteinrichtungs-App (beispielsweise für die Ersteinrichtung eines Fitnessarmbands) ausgeliefert.</span><span class="sxs-lookup"><span data-stu-id="e6322-144">Normally, companion devices ship with an app for initial setup, like setting up a fitness band for the first time.</span></span> <span data-ttu-id="e6322-145">Die in diesem Dokument beschriebenen Funktionen können Teil dieser App sein, sodass keine separate App erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="e6322-145">The functionality described in this document can be part of that app and a separate app should not be required.</span></span>  

### <a name="user-signals"></a><span data-ttu-id="e6322-146">Benutzersignale</span><span class="sxs-lookup"><span data-stu-id="e6322-146">User signals</span></span>

<span data-ttu-id="e6322-147">Jedes Windows Hello-Begleitgerät muss mit einer App kombiniert werden, die drei Benutzersignale unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e6322-147">Each Windows Hello companion device should be combined with an app that supports three user signals.</span></span> <span data-ttu-id="e6322-148">Bei diesen Signalen kann es sich um eine Aktion oder um eine Geste handeln.</span><span class="sxs-lookup"><span data-stu-id="e6322-148">These signals can be in form of an action or gesture.</span></span>

- <span data-ttu-id="e6322-149">**Absichtssignal**: Ermöglicht dem Benutzer, seine Entsperrabsicht deutlich zu machen (beispielsweise durch Drücken einer Taste auf dem Windows Hello-Begleitgerät).</span><span class="sxs-lookup"><span data-stu-id="e6322-149">**Intent signal**: Allows the user to show his intent for unlock by, for example, hitting a button on the Windows Hello companion device.</span></span> <span data-ttu-id="e6322-150">Das Absichtssignal muss auf dem **Windows Hello-Begleitgerät** erfasst werden.</span><span class="sxs-lookup"><span data-stu-id="e6322-150">The intent signal must be collected on **Windows Hello companion device** side.</span></span>
- <span data-ttu-id="e6322-151">**Benutzeranwesenheitssignal**: Bestätigt die Anwesenheit des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="e6322-151">**User presence signal**: Proves the presence of the user.</span></span> <span data-ttu-id="e6322-152">Das Windows Hello-Begleitgerät kann beispielsweise eine PIN anfordern, bevor es zum Entsperren des PCs verwendet werden kann (nicht zu verwechseln mit einer PC-PIN), oder es ist unter Umständen ein Tastendruck erforderlich.</span><span class="sxs-lookup"><span data-stu-id="e6322-152">The Windows Hello companion device might, for instance, require a PIN before it can be used for unlocking PC (not to be confused with PC PIN), or it might require press of a button.</span></span>
- <span data-ttu-id="e6322-153">**Mehrdeutigkeitsvermeidungssignal**: Gibt an, welches Windows10-Desktopgerät der Benutzer entsperren möchte, wenn dem Windows Hello-Begleitgerät mehrere Optionen zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="e6322-153">**Disambiguation signal**: Disambiguates which Windows 10 desktop the user wants to unlock when multiple options are available to the Windows Hello companion device.</span></span>

<span data-ttu-id="e6322-154">Von diesen Benutzersignalen kann eine beliebige Anzahl zu einem einzelnen Signal kombiniert werden.</span><span class="sxs-lookup"><span data-stu-id="e6322-154">Any number of these user signals can be combined into one.</span></span> <span data-ttu-id="e6322-155">Benutzeranwesenheits- und Absichtssignale sind bei jeder Verwendung erforderlich.</span><span class="sxs-lookup"><span data-stu-id="e6322-155">User presence and intent signals must be required on each use.</span></span>

### <a name="registration-and-future-communication-between-a-pc-and-windows-hello-companion-devices"></a><span data-ttu-id="e6322-156">Registrierung und zukünftige Kommunikation zwischen einem PC und Windows Hello-Begleitgeräten</span><span class="sxs-lookup"><span data-stu-id="e6322-156">Registration and future communication between a PC and Windows Hello companion devices</span></span>

<span data-ttu-id="e6322-157">Damit ein Windows Hello-Begleitgerät in das Windows Hello-Begleitgeräteframework eingebunden werden kann, muss es zunächst beim Framework registriert werden.</span><span class="sxs-lookup"><span data-stu-id="e6322-157">Before a Windows Hello companion device can be plugged into the Windows Hello companion device framework, it needs to be registered with the framework.</span></span> <span data-ttu-id="e6322-158">Für den Registrierungsprozess ist allein die Windows Hello-Begleitgeräte-App zuständig.</span><span class="sxs-lookup"><span data-stu-id="e6322-158">The experience for registration is completely owned by the Windows Hello companion device app.</span></span>

<span data-ttu-id="e6322-159">Bei der Beziehung zwischen dem Windows Hello-Begleitgerät und dem Windows10-Desktopgerät kann es sich um eine 1:n-Beziehung handeln. (Ein Begleitgerät kann also für viele Windows10-Desktopgeräte verwendet werden.)</span><span class="sxs-lookup"><span data-stu-id="e6322-159">The relationship between the Windows Hello companion device and the Windows 10 desktop  device can be one to many (i.e., one companion device can be used for many Windows 10 desktop  devices).</span></span> <span data-ttu-id="e6322-160">Jedes Windows Hello-Begleitgerät kann jedoch nur für einen einzelnen Benutzer auf dem jeweiligen Windows10-Desktopgerät verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e6322-160">However, each Windows Hello companion device can only be used for one user on each Windows 10 desktop  device.</span></span>   

<span data-ttu-id="e6322-161">Damit ein Windows Hello-Begleitgerät mit einem PC kommunizieren kann, müssen sich beide auf einen Transport einigen.</span><span class="sxs-lookup"><span data-stu-id="e6322-161">Before a Windows Hello companion device can communicate with a PC, they need to agree on a transport to use.</span></span> <span data-ttu-id="e6322-162">Die Entscheidung wird von der Windows Hello-Begleitgeräte-App getroffen. Das Windows Hello-Begleitgeräteframework schränkt weder den Transporttyp (USB, NFC, WLAN, Bluetooth, BLE usw.) noch das Protokoll zwischen Windows Hello-Begleitgerät und Windows Hello-Begleitgeräte-App des Windows10-Desktopgeräts ein.</span><span class="sxs-lookup"><span data-stu-id="e6322-162">Such choice is left to the Windows Hello companion device app; the Windows Hello companion device framework does not impose any limitations on transport type (USB, NFC, WiFi, BT, BLE, etc) or protocol being used between the Windows Hello companion device and the Windows Hello companion device app on the Windows 10 desktop device side.</span></span> <span data-ttu-id="e6322-163">Es schlägt jedoch bestimmte Sicherheitsaspekte für die Transportschicht vor (wie in diesem Dokument im Abschnitt „Sicherheitsanforderungen“ beschrieben).</span><span class="sxs-lookup"><span data-stu-id="e6322-163">It does, however, suggest certain security considerations for the transport layer as outlined in the "Security Requirements" section of this document.</span></span> <span data-ttu-id="e6322-164">Für die Erfüllung dieser Anforderungen ist der Geräteanbieter verantwortlich.</span><span class="sxs-lookup"><span data-stu-id="e6322-164">It is the device provider’s responsibility to provide those requirements.</span></span> <span data-ttu-id="e6322-165">Sie werden nicht vom Framework bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="e6322-165">The framework does not provide them for you.</span></span>


## <a name="user-interaction-model"></a><span data-ttu-id="e6322-166">Benutzerinteraktionsmodell</span><span class="sxs-lookup"><span data-stu-id="e6322-166">User Interaction Model</span></span>

### <a name="windows-hello-companion-device-app-discovery-installation-and-first-time-registration"></a><span data-ttu-id="e6322-167">Erkennung, Installation und erstmalige Registrierung der Windows Hello-Begleitgeräte-App</span><span class="sxs-lookup"><span data-stu-id="e6322-167">Windows Hello companion device app discovery, installation, and first-time registration</span></span>

<span data-ttu-id="e6322-168">Im Anschluss sehen Sie einen typischen Benutzerworkflow:</span><span class="sxs-lookup"><span data-stu-id="e6322-168">A typical user workflow is as follows:</span></span>

- <span data-ttu-id="e6322-169">Der Benutzer richtet die PIN auf jedem der Windows10-Zieldesktopgeräte ein, die er mit dem Windows Hello-Begleitgerät entsperren möchte.</span><span class="sxs-lookup"><span data-stu-id="e6322-169">The user sets up the PIN on each of target Windows 10 desktop devices she wants to unlock with that Windows Hello companion device.</span></span>
- <span data-ttu-id="e6322-170">Der Benutzer führt auf dem Windows10-Desktopgerät die Windows Hello-Begleitgeräte-App aus, um sein Windows Hello-Begleitgerät bei dem Windows10-Desktopgerät zu registrieren.</span><span class="sxs-lookup"><span data-stu-id="e6322-170">The user runs the Windows Hello companion device app on their Windows 10 desktop device to register her Windows Hello companion device with Windows 10 desktop.</span></span>

<span data-ttu-id="e6322-171">Hinweise:</span><span class="sxs-lookup"><span data-stu-id="e6322-171">Notes:</span></span>

- <span data-ttu-id="e6322-172">Es empfiehlt sich, die Erkennung, das Herunterladen und das Starten der Windows Hello-Begleitgeräte-App zu optimieren und nach Möglichkeit zu automatisieren, sodass die App beispielsweise aufseiten des Windows10-Desktopgeräts durch Tippen auf das Windows Hello-Begleitgerät auf einem NFC-Lesegerät heruntergeladen werden kann.</span><span class="sxs-lookup"><span data-stu-id="e6322-172">We recommend the discovery, download, and launch of the Windows Hello companion device app is streamlined and, if possible, automated (e.g., the app can be downloaded upon tapping the Windows Hello companion device on an NFC reader on Windows 10 desktop device side).</span></span> <span data-ttu-id="e6322-173">Dies ist allerdings Aufgabe des Windows Hello-Begleitgeräts und der Windows Hello-Begleitgeräte-App.</span><span class="sxs-lookup"><span data-stu-id="e6322-173">This is, however, the responsibility of the Windows Hello companion device and Windows Hello companion device app.</span></span>
- <span data-ttu-id="e6322-174">In einer Unternehmensumgebung kann die Windows Hello-Begleitgeräte-App per MDM bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="e6322-174">In an enterprise environment, the Windows Hello companion device app can be deployed via MDM.</span></span>
- <span data-ttu-id="e6322-175">Fehlermeldungen, die unter Umständen im Rahmen der Registrierung auftreten, müssen dem Benutzer von der Windows Hello-Begleitgeräte-App angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="e6322-175">The Windows Hello companion device app is responsible for showing the user any error messages that happen as part of registration.</span></span>

### <a name="registration-and-de-registration-protocol"></a><span data-ttu-id="e6322-176">Protokoll für Registrierung und Registrierungsaufhebung</span><span class="sxs-lookup"><span data-stu-id="e6322-176">Registration and de-registration protocol</span></span>

<span data-ttu-id="e6322-177">Das folgende Diagramm zeigt, wie das Windows Hello-Begleitgerät bei der Registrierung mit dem Begleitauthentifizierungsdienst interagiert.</span><span class="sxs-lookup"><span data-stu-id="e6322-177">The following diagram illustrates how the Windows Hello companion device interacts with Companion Authentication Service during registration.</span></span>  

![Registrierungsfluss](images/companion-device-2.png)

<span data-ttu-id="e6322-179">In unserem Protokoll werden zwei Schlüssel verwendet:</span><span class="sxs-lookup"><span data-stu-id="e6322-179">There are two keys used in our protocol:</span></span>

- <span data-ttu-id="e6322-180">Geräteschlüssel (**devicekey**): Dient zum Schutz von Entsperrtoken, die der PC zum Entsperren von Windows benötigt.</span><span class="sxs-lookup"><span data-stu-id="e6322-180">Device key (**devicekey**): used to protect unlock tokens that the PC needs to unlock Windows.</span></span>
- <span data-ttu-id="e6322-181">Authentifizierungsschlüssel (**authkey**): Dient zur gegenseitigen Authentifizierung von Windows Hello-Begleitgerät und Begleitauthentifizierungsdienst.</span><span class="sxs-lookup"><span data-stu-id="e6322-181">The authentication key (**authkey**): used to mutually authenticate the Windows Hello companion device and Companion Authentication Service.</span></span>

<span data-ttu-id="e6322-182">Der Geräteschlüssel und die Authentifizierungsschlüssel werden bei der Registrierung zwischen Windows Hello-Begleitgeräte-App und dem Windows Hello-Begleitgerät ausgetauscht.</span><span class="sxs-lookup"><span data-stu-id="e6322-182">The device key and authentication keys are exchanged at registration time between the Windows Hello companion device app and Windows Hello companion device.</span></span> <span data-ttu-id="e6322-183">Zum Schutz der Schlüssel müssen die Windows Hello-Begleitgeräte-App und das Windows Hello-Begleitgerät daher einen sicheren Transport verwenden.</span><span class="sxs-lookup"><span data-stu-id="e6322-183">As a result, the Windows Hello companion device app and Windows Hello companion device must use a secure transport to protect keys.</span></span>

<span data-ttu-id="e6322-184">Beachten Sie außerdem Folgendes: Im obigen Diagramm ist zwar zu sehen, dass zwei HMAC-Schlüssel auf dem Windows Hello-Begleitgerät generiert werden, diese können jedoch auch von der App generiert und zur Speicherung an das Windows Hello-Begleitgerät gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="e6322-184">Also, note that while the diagram above displays two HMAC keys generating on the Windows Hello companion device, it is also possible for the app to generate them and send them to the Windows Hello companion device for storage.</span></span>

### <a name="starting-authentication-flows"></a><span data-ttu-id="e6322-185">Starten von Authentifizierungsflüssen</span><span class="sxs-lookup"><span data-stu-id="e6322-185">Starting authentication flows</span></span>

<span data-ttu-id="e6322-186">Der Anmeldefluss für Windows10-Desktopgeräte kann vom Benutzer (durch ein Absichtssignal) über das Windows Hello-Begleitgeräteframework auf zwei Arten gestartet werden:</span><span class="sxs-lookup"><span data-stu-id="e6322-186">There are two ways for the user to start the signing in flow to Windows 10 desktop using Windows Hello companion device framework (i.e., provide intent signal):</span></span>

- <span data-ttu-id="e6322-187">Durch Öffnen des Deckels (Laptop) oder durch Drücken der LEERTASTE oder Wischen nach oben (PC)</span><span class="sxs-lookup"><span data-stu-id="e6322-187">Open up the lid on laptop, or hit the space bar or swipe up on PC.</span></span>
- <span data-ttu-id="e6322-188">Durch eine Geste oder eine Aktion auf dem Windows Hello-Begleitgerät</span><span class="sxs-lookup"><span data-stu-id="e6322-188">Perform a gesture or an action on the Windows Hello companion device side.</span></span>

<span data-ttu-id="e6322-189">Welche Option als Ausgangspunkt verwendet wird, liegt beim Windows Hello-Begleitgerät.</span><span class="sxs-lookup"><span data-stu-id="e6322-189">It is the Windows Hello companion device's choice to select which one is the starting point.</span></span> <span data-ttu-id="e6322-190">Das Windows Hello-Begleitgeräteframework informiert die Begleitgeräte-App, wenn der erste Fall eintritt.</span><span class="sxs-lookup"><span data-stu-id="e6322-190">The Windows Hello companion device framework will inform companion device app when option one happens.</span></span> <span data-ttu-id="e6322-191">Im zweiten Fall muss die Windows Hello-Begleitgeräte-App das Begleitgerät abfragen, um zu ermitteln, ob das Ereignis erfasst wurde.</span><span class="sxs-lookup"><span data-stu-id="e6322-191">For option two, the Windows Hello companion device app should query the companion device to see if that event has been captured.</span></span> <span data-ttu-id="e6322-192">Dadurch wird sichergestellt, dass das Windows Hello-Begleitgerät vor dem erfolgreichen Entsperren das Absichtssignal erfasst.</span><span class="sxs-lookup"><span data-stu-id="e6322-192">This ensures the Windows Hello companion device collects the intent signal before the unlock succeeds.</span></span>

### <a name="windows-hello-companion-device-credential-provider"></a><span data-ttu-id="e6322-193">Anmeldeinformationsanbieter für Windows Hello-Begleitgeräte</span><span class="sxs-lookup"><span data-stu-id="e6322-193">Windows Hello companion device credential provider</span></span>

<span data-ttu-id="e6322-194">Windows10 verfügt über einen neuen Anmeldeinformationsanbieter zur Behandlung sämtlicher Windows Hello-Begleitgeräte.</span><span class="sxs-lookup"><span data-stu-id="e6322-194">There is a new credential provider in Windows 10 that handles all Windows Hello companion devices.</span></span>

<span data-ttu-id="e6322-195">Der Anmeldeinformationsanbieter für Windows Hello-Begleitgeräte startet die Begleitgerät-Hintergrundaufgabe mittels Aktivierung eines Triggers.</span><span class="sxs-lookup"><span data-stu-id="e6322-195">The Windows Hello companion device credential provider is responsible for launching the companion device background task via activating a trigger.</span></span> <span data-ttu-id="e6322-196">Der Trigger wird erstmals festgelegt, wenn der PC aktiviert und ein Sperrbildschirm angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="e6322-196">The trigger is set the first time when the PC awakens and a lock screen is displayed.</span></span> <span data-ttu-id="e6322-197">Das zweite Mal erfolgt, wenn der PC die Anmeldebenutzeroberfläche anzeigt und der Anmeldeinformationsanbieter für Windows Hello-Begleitgeräte die ausgewählte Kachel ist.</span><span class="sxs-lookup"><span data-stu-id="e6322-197">The second time is when the PC is entering logon UI and the Windows Hello companion device credential provider is the selected tile.</span></span>

<span data-ttu-id="e6322-198">Die Hilfsbibliothek für die Windows Hello-Begleitgeräte-App lauscht auf die Änderung des Sperrbildschirmstatus und sendet das Ereignis, das der Windows Hello-Begleitgerät-Hintergrundaufgabe entspricht.</span><span class="sxs-lookup"><span data-stu-id="e6322-198">The helper library for the Windows Hello companion device app will listen to the lock screen status change and send the event corresponding to the Windows Hello companion device background task.</span></span>

<span data-ttu-id="e6322-199">Sollten mehrere Windows Hello-Begleitgerät-Hintergrundaufgaben vorhanden sein, wird der PC durch die erste Hintergrundaufgabe entsperrt, die den Authentifizierungsprozess abgeschlossen hat.</span><span class="sxs-lookup"><span data-stu-id="e6322-199">If there are multiple Windows Hello companion device background tasks, the first background task that has finished the authentication process will unlock the PC.</span></span> <span data-ttu-id="e6322-200">Alle übrigen Authentifizierungsaufrufe werden vom Begleitgerät-Authentifizierungsdienst ignoriert.</span><span class="sxs-lookup"><span data-stu-id="e6322-200">The companion device authentication service will ignore any remaining authentication calls.</span></span>

<span data-ttu-id="e6322-201">Die Vorgänge aufseiten des Windows Hello-Begleitgeräts werden von der Windows Hello-Begleitgeräte-App abgewickelt und verwaltet.</span><span class="sxs-lookup"><span data-stu-id="e6322-201">The experience on the Windows Hello companion device side is owned and managed by the Windows Hello companion device app.</span></span> <span data-ttu-id="e6322-202">Das Windows Hello-Begleitgeräteframework hat keinen Einfluss auf diesen Teil der Benutzererfahrung.</span><span class="sxs-lookup"><span data-stu-id="e6322-202">The Windows Hello companion device framework has no control over this part of the user experience.</span></span> <span data-ttu-id="e6322-203">Genauer gesagt: Der Begleitauthentifizierungsanbieter informiert die Windows Hello-Begleitgeräte-App (mittels der dazugehörigen Hintergrund-App) über Zustandsänderungen der Anmeldebenutzeroberfläche (wie Einblendung des Sperrbildschirms oder Ausblendung des Sperrbildschirms durch Drücken der LEERTASTE), und die Windows Hello-Begleitgeräte-App muss daraufhin mit einer entsprechenden Benutzererfahrung reagieren (beispielsweise, indem nach dem Drücken der LEERTASTE und Ausblenden des Sperrbildschirms über USB nach dem Gerät gesucht wird).</span><span class="sxs-lookup"><span data-stu-id="e6322-203">More specifically, the companion authentication provider informs the Windows Hello companion device app (via its background app) about state changes in logon UI (e.g., lock screen just came down, or the user just dispelled lock screen by hitting spacebar), and it is the responsibility of the Windows Hello companion device app to build an experience around that (e.g., upon user hitting spacebar and dispelling unlock screen, start looking for the device over USB).</span></span>

<span data-ttu-id="e6322-204">Das Windows Hello-Begleitgeräteframework stellt eine Reihe (lokalisierter) Text- und Fehlermeldungen für die Windows Hello-Begleitgeräte-App zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="e6322-204">The Windows Hello companion device Framework will provide a stock of (localized) text and error messages for the Windows Hello companion device app to choose from.</span></span> <span data-ttu-id="e6322-205">Diese werden im Vordergrund des Sperrbildschirms (oder auf der Anmeldebenutzeroberfläche) angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e6322-205">These will be displayed on top of lock screen (or in logon UI).</span></span> <span data-ttu-id="e6322-206">Weitere Informationen finden Sie im Abschnitt „Umgang mit Meldungen und Fehlern“.</span><span class="sxs-lookup"><span data-stu-id="e6322-206">See the Dealing with Messages and Errors section for more details.</span></span>

### <a name="authentication-protocol"></a><span data-ttu-id="e6322-207">Authentifizierungsprotokoll</span><span class="sxs-lookup"><span data-stu-id="e6322-207">Authentication protocol</span></span>

<span data-ttu-id="e6322-208">Nachdem die mit einer Windows Hello-Begleitgeräte-App verknüpfte Hintergrundaufgabe per Trigger gestartet wurde, muss sie die Unterstützung des Windows Hello-Begleitgeräts bei der Überprüfung eines durch den Begleitauthentifizierungsdienst berechneten HMAC-Werts und bei der Berechnung zweier HMAC-Werte anfordern:</span><span class="sxs-lookup"><span data-stu-id="e6322-208">Once the background task associated with a Windows Hello companion device app is trigger started, it is responsible for asking the Windows Hello companion device to validate an HMAC value computed by the Companion Authentication Service and help calculate two HMAC values:</span></span>
- <span data-ttu-id="e6322-209">Dienst-HMAC überprüfen = HMAC(Authentifizierungsschlüssel, Dienst-Nonce || Geräte-Nonce || Sitzungs-Nonce).</span><span class="sxs-lookup"><span data-stu-id="e6322-209">Validate Service HMAC = HMAC(authentication key, service nonce || device nonce || session nonce).</span></span>
- <span data-ttu-id="e6322-210">Berechnen Sie den HMAC des Geräteschlüssels mit einer Nonce.</span><span class="sxs-lookup"><span data-stu-id="e6322-210">Calculate the HMAC of the device key with a nonce.</span></span>
- <span data-ttu-id="e6322-211">Berechnen Sie den HMAC des Authentifizierungsschlüssels mit dem ersten HMAC-Wert, verkettet mit einer durch den Begleitauthentifizierungsdienst generierten Nonce.</span><span class="sxs-lookup"><span data-stu-id="e6322-211">Calculate the HMAC of the authentication key with first HMAC value concatenated with a nonce generated by the Companion Authentication Service.</span></span>

<span data-ttu-id="e6322-212">Der zweite berechnete Wert wird vom Dienst nicht nur zur Authentifizierung des Geräts, sondern auch zur Verhinderung von Replay-Angriffen im Transportkanal verwendet.</span><span class="sxs-lookup"><span data-stu-id="e6322-212">The second computed value is used by the service to authenticate the device and also prevent replay attack in transport channel.</span></span>

![Registrierungsfluss](images/companion-device-3.png)

## <a name="lifecycle-management"></a><span data-ttu-id="e6322-214">Lebenszyklusverwaltung</span><span class="sxs-lookup"><span data-stu-id="e6322-214">Lifecycle management</span></span>

### <a name="register-once-use-everywhere"></a><span data-ttu-id="e6322-215">Einmalige Registrierung, ortsunabhängige Verwendung</span><span class="sxs-lookup"><span data-stu-id="e6322-215">Register once, use everywhere</span></span>

<span data-ttu-id="e6322-216">Ohne Back-End-Server müssen Benutzer ihr Windows Hello-Begleitgerät separat bei jedem Windows10-Desktopgerät registrieren.</span><span class="sxs-lookup"><span data-stu-id="e6322-216">Without a backend server, users must register their Windows Hello companion device with each Windows 10 desktop device separately.</span></span>

<span data-ttu-id="e6322-217">Eine Begleitgerätehersteller oder OEM kann einen Webdienst implementieren, um den Registrierungszustand für mehrere Windows10-Desktopgeräte oder mobile Geräte des Benutzers zur Verfügung zu stellen.</span><span class="sxs-lookup"><span data-stu-id="e6322-217">A companion device vendor or OEM can implement a web service to roam the registration state across user Windows 10 desktops or mobile devices.</span></span> <span data-ttu-id="e6322-218">Ausführlichere Informationen finden Sie im Abschnitt „Roaming, Sperrung und Filterdienst“.</span><span class="sxs-lookup"><span data-stu-id="e6322-218">For more details, see the Roaming, Revocation, and Filter Service section.</span></span>

### <a name="pin-management"></a><span data-ttu-id="e6322-219">PIN-Verwaltung</span><span class="sxs-lookup"><span data-stu-id="e6322-219">PIN management</span></span>

<span data-ttu-id="e6322-220">Bevor ein Begleitgerät verwendet werden kann, muss auf dem Windows10-Desktopgerät eine PIN eingerichtet werden.</span><span class="sxs-lookup"><span data-stu-id="e6322-220">Before a companion device can be used, a PIN needs to be set up on Windows 10 desktop device.</span></span> <span data-ttu-id="e6322-221">Dadurch wird sichergestellt, dass der Benutzer über eine Ausweichmöglichkeit verfügt, falls das Windows Hello-Begleitgerät nicht funktioniert.</span><span class="sxs-lookup"><span data-stu-id="e6322-221">This ensures the user has a backup in case their Windows Hello companion device is not working.</span></span> <span data-ttu-id="e6322-222">Die PIN wird von Windows verwaltet und den Apps gegenüber nie offengelegt.</span><span class="sxs-lookup"><span data-stu-id="e6322-222">The PIN is something that Windows manages and that apps never see.</span></span> <span data-ttu-id="e6322-223">Sie kann unter „Einstellungen“ > „Konten“ > „Anmeldeoptionen“ geändert werden.</span><span class="sxs-lookup"><span data-stu-id="e6322-223">To change it, the user navigates to Settings > Accounts > Sign-in options.</span></span>

### <a name="management-and-policy"></a><span data-ttu-id="e6322-224">Verwaltung und Richtlinie</span><span class="sxs-lookup"><span data-stu-id="e6322-224">Management and policy</span></span>

<span data-ttu-id="e6322-225">Benutzer können ein Windows Hello-Begleitgerät von einem Windows10-Desktopgerät entfernen, indem sie die Windows Hello-Begleitgeräte-App auf dem entsprechenden Desktopgerät ausführen.</span><span class="sxs-lookup"><span data-stu-id="e6322-225">Users can remove a Windows Hello companion device from a Windows 10 desktops by running the Windows Hello companion device app on that desktop device.</span></span>

<span data-ttu-id="e6322-226">Unternehmen stehen zum Steuern des Windows Hello-Begleitgeräteframeworks zwei Optionen zur Verfügung:</span><span class="sxs-lookup"><span data-stu-id="e6322-226">Enterprises have two options for controlling the Windows Hello companion device framework:</span></span>

- <span data-ttu-id="e6322-227">Aktivieren oder Deaktivieren des Features</span><span class="sxs-lookup"><span data-stu-id="e6322-227">Turn the feature on or off</span></span>
- <span data-ttu-id="e6322-228">Definieren einer Whitelist mit Windows Hello-Begleitgeräten, die das Windows-App-Schließfach verwenden dürfen</span><span class="sxs-lookup"><span data-stu-id="e6322-228">Define the whitelist of Windows Hello companion devices allowed using Windows app locker</span></span>

<span data-ttu-id="e6322-229">Das Windows Hello-Begleitgeräteframework unterstützt keine zentralisierte Inventarisierung verfügbarer Begleitgeräte und keine Methode zur weiteren Filterung der zulässigen Instanzen eines Windows Hello-Begleitgerätetyps. (So kann beispielsweise nicht festgelegt werden, dass nur Begleitgeräte mit einer Seriennummer zwischen X und Y zulässig sind.)</span><span class="sxs-lookup"><span data-stu-id="e6322-229">The Windows Hello companion device framework does not support any centralized way to keep inventory of available companion devices, or a method to further filter which instances of a Windows Hello companion device type is allowed (for example, only a companion device with a serial number between X and Y are allowed).</span></span> <span data-ttu-id="e6322-230">App-Entwickler können solche Funktionen jedoch über einen eigenen Dienst bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="e6322-230">Apps developers can, however, build a service to provide such functionality.</span></span> <span data-ttu-id="e6322-231">Ausführlichere Informationen finden Sie im Abschnitt „Roaming, Sperrung und Filterdienst“.</span><span class="sxs-lookup"><span data-stu-id="e6322-231">For more details, see the Roaming, Revocation, and Filter Service section.</span></span>

### <a name="revocation"></a><span data-ttu-id="e6322-232">Sperrung</span><span class="sxs-lookup"><span data-stu-id="e6322-232">Revocation</span></span>

<span data-ttu-id="e6322-233">Die Remoteentfernung eines Begleitgeräts von einem bestimmten Windows10-Desktopgerät wird vom Windows Hello-Begleitgeräteframework nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e6322-233">The Windows Hello companion device framework does not support removing a companion device from a specific Windows 10 desktop device remotely.</span></span> <span data-ttu-id="e6322-234">Stattdessen können Benutzer das Windows Hello-Begleitgerät über die auf dem Windows10-Desktopgerät ausgeführte Windows Hello-Begleitgeräte-App entfernen.</span><span class="sxs-lookup"><span data-stu-id="e6322-234">Instead, users can remove the Windows Hello companion device via the Windows Hello companion device app running on that Windows 10 desktop.</span></span>

<span data-ttu-id="e6322-235">Begleitgerätehersteller können jedoch einen Dienst erstellen, der eine Remotesperrung ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="e6322-235">Companion device vendors, however, can build a service to provide remote revocation functionality.</span></span> <span data-ttu-id="e6322-236">Ausführlichere Informationen finden Sie im Abschnitt „Roaming, Sperrung und Filterdienst“.</span><span class="sxs-lookup"><span data-stu-id="e6322-236">For more details, see Roaming, Revocation, and Filter Service section.</span></span>

### <a name="roaming-and-filter-services"></a><span data-ttu-id="e6322-237">Roaming- und Filterdienste</span><span class="sxs-lookup"><span data-stu-id="e6322-237">Roaming and filter services</span></span>

<span data-ttu-id="e6322-238">Begleitgerätehersteller können einen Webdienst implementieren, der für folgende Szenarien verwendet werden kann:</span><span class="sxs-lookup"><span data-stu-id="e6322-238">Companion device vendors can implement a web service that can be used for the following scenarios:</span></span>

- <span data-ttu-id="e6322-239">Filterdienst für Unternehmen: Ein Unternehmen kann die Windows Hello-Begleitgeräte, die in seiner Umgebung verwendet werden können, auf eine kleine Gruppe von Geräten eines bestimmten Herstellers beschränken.</span><span class="sxs-lookup"><span data-stu-id="e6322-239">A filter service for enterprise: An enterprise can limit the set of Windows Hello companion devices that can work in their environment to a select few from a specific vendor.</span></span> <span data-ttu-id="e6322-240">So kann das Unternehmen Contoso beispielsweise beim HerstellerX 10.000Begleitgeräte des ModellsY bestellen und sicherstellen, dass in der Contoso-Domäne ausschließlich diese Geräte (und kein anderes Gerätemodell des HerstellersX) verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="e6322-240">For example, the company Contoso could order 10,000 Model Y companion devices from Vendor X and ensure only those devices will work in the Contoso domain (and not any other device model from Vendor X).</span></span>
- <span data-ttu-id="e6322-241">Inventarisierung: Ein Unternehmen kann eine Liste mit vorhandenen Begleitgeräten erstellen, die in einer Unternehmensumgebung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e6322-241">Inventory:  An enterprise can determine the list of existing companion devices used in an enterprise environment.</span></span>
- <span data-ttu-id="e6322-242">Echtzeitsperrung: Wenn ein Mitarbeiter sein Begleitgerät als verloren oder gestohlen meldet, kann dieses Gerät über den Webdienst gesperrt werden.</span><span class="sxs-lookup"><span data-stu-id="e6322-242">Real time revocation: If an employee reports that his companion device is lost or stolen, the web service can be used to revoke that device.</span></span>
- <span data-ttu-id="e6322-243">Roaming: Ein Benutzer muss sein Begleitgerät lediglich einmal registrieren und kann es danach für alle seine Desktopgeräte und mobilen Geräte unter Windows10 verwenden.</span><span class="sxs-lookup"><span data-stu-id="e6322-243">Roaming: A user only has to register his companion device once and it works on all of his Windows 10 desktops and Mobile.</span></span>

<span data-ttu-id="e6322-244">Zur Implementierung dieser Features muss die Windows Hello-Begleitgeräte-App bei der Registrierung und Verwendung mit dem Webdienst kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="e6322-244">Implementing these features requires the Windows Hello companion device app to check with the web service at registration and usage time.</span></span> <span data-ttu-id="e6322-245">Die Windows Hello-Begleitgeräte-App kann zur Optimierung in Anmeldeszenarien mit Zwischenspeicherung verwendet werden, sodass beispielsweise nur einmal täglich mit dem Webdienst kommuniziert werden muss. (Dadurch verlängert sich allerdings die Zeit für die Sperrung auf bis zu einen Tag.)</span><span class="sxs-lookup"><span data-stu-id="e6322-245">The Windows Hello companion device app can optimize for cached logon scenarios like requiring checking with web service only once a day (at the cost of extending the revocation time to up to one day).</span></span>  

## <a name="windows-hello-companion-device-framework-api-model"></a><span data-ttu-id="e6322-246">API-Modell des Windows Hello-Begleitgeräteframeworks</span><span class="sxs-lookup"><span data-stu-id="e6322-246">Windows Hello companion device framework API model</span></span>

### <a name="overview"></a><span data-ttu-id="e6322-247">Übersicht</span><span class="sxs-lookup"><span data-stu-id="e6322-247">Overview</span></span>

<span data-ttu-id="e6322-248">Eine Windows Hello-Begleitgeräte-App muss zwei Komponenten umfassen: eine Vordergrund-App mit Benutzeroberfläche zum Registrieren und Aufheben der Registrierung des Geräts sowie eine Hintergrundaufgabe für die Authentifizierung.</span><span class="sxs-lookup"><span data-stu-id="e6322-248">A Windows Hello companion device app should contain two components: a foregroud app with UI responsible for registering and unregistering the device, and a background task that handles authentication.</span></span>

<span data-ttu-id="e6322-249">Der gesamte API-Fluss sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="e6322-249">The overall API flow is as follows:</span></span>

1. <span data-ttu-id="e6322-250">Registrieren Sie das Windows Hello-Begleitgerät.</span><span class="sxs-lookup"><span data-stu-id="e6322-250">Register the Windows Hello companion device</span></span>
    * <span data-ttu-id="e6322-251">Überprüfen Sie, ob sich das Gerät in Reichweite befindet, und fragen Sie dessen Funktionen ab (falls erforderlich).</span><span class="sxs-lookup"><span data-stu-id="e6322-251">Make sure the device is nearby and query its capability (if required)</span></span>
    * <span data-ttu-id="e6322-252">Generieren Sie zwei HMAC-Schlüssel (entweder aufseiten des Begleitgeräts oder aufseiten der App).</span><span class="sxs-lookup"><span data-stu-id="e6322-252">Generate two HMAC keys (either on the companion device side or the app side)</span></span>
    * <span data-ttu-id="e6322-253">Rufen Sie „RequestStartRegisteringDeviceAsync“ auf.</span><span class="sxs-lookup"><span data-stu-id="e6322-253">Call RequestStartRegisteringDeviceAsync</span></span>
    * <span data-ttu-id="e6322-254">Rufen Sie „FinishRegisteringDeviceAsync“ auf.</span><span class="sxs-lookup"><span data-stu-id="e6322-254">Call FinishRegisteringDeviceAsync</span></span>
    * <span data-ttu-id="e6322-255">Stellen Sie sicher, dass die Windows Hello-Begleitgeräte-App die HMAC-Schlüssel speichert (sofern unterstützt) und die Kopien verwirft.</span><span class="sxs-lookup"><span data-stu-id="e6322-255">Make sure Windows Hello companion device app stores HMAC keys (if supported) and Windows Hello companion device app discards its copies</span></span>
2. <span data-ttu-id="e6322-256">Registrieren Sie die Hintergrundaufgabe.</span><span class="sxs-lookup"><span data-stu-id="e6322-256">Register your background task</span></span>
3. <span data-ttu-id="e6322-257">Warten Sie auf das passende Ereignis in der Hintergrundaufgabe.</span><span class="sxs-lookup"><span data-stu-id="e6322-257">Wait for the right event in the background task</span></span>
    * <span data-ttu-id="e6322-258">WaitingForUserConfirmation: Warten Sie auf dieses Ereignis, wenn zum Starten des Authentifizierungsablaufs eine Benutzeraktion/-geste auf dem Windows Hello-Begleitgerät erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="e6322-258">WaitingForUserConfirmation: Wait for this event if the user action/gesture on the Windows Hello companion device side is required to start authentication flow</span></span>
    * <span data-ttu-id="e6322-259">CollectingCredential: Warten Sie auf dieses Ereignis, wenn der Start des Authentifizierungsablaufs auf einer Benutzeraktion/-geste auf dem PC (beispielsweise Drücken der LEERTASTE) beruht.</span><span class="sxs-lookup"><span data-stu-id="e6322-259">CollectingCredential: Wait for this event if the Windows Hello companion device relies on user action/gesture on the PC side to start authentication flow (e.g., by hitting spacebar)</span></span>
    * <span data-ttu-id="e6322-260">Anderer Trigger (beispielsweise eine Smartcard): Fragen Sie den aktuellen Authentifizierungszustand ab, um die richtigen APIs aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="e6322-260">Other trigger, like a smartcard: Make sure to query for current authentication state to call the right APIs.</span></span>
4. <span data-ttu-id="e6322-261">Halten Sie den Benutzer durch Aufrufen von „ShowNotificationMessageAsync“ über Fehlermeldungen oder nächste Schritte auf dem Laufenden.</span><span class="sxs-lookup"><span data-stu-id="e6322-261">Keep user informed about error messages or required next steps by calling ShowNotificationMessageAsync.</span></span> <span data-ttu-id="e6322-262">Rufen Sie diese API erst auf, nachdem ein Absichtssignal erfasst wurde.</span><span class="sxs-lookup"><span data-stu-id="e6322-262">Only call this API once an intent signal is collected</span></span>
5. <span data-ttu-id="e6322-263">Entsperrung</span><span class="sxs-lookup"><span data-stu-id="e6322-263">Unlock</span></span>
    * <span data-ttu-id="e6322-264">Vergewissern Sie sich, dass Absichts- und Benutzeranwesenheitssignale erfasst wurden.</span><span class="sxs-lookup"><span data-stu-id="e6322-264">Make sure intent and user presence signals were collected</span></span>
    * <span data-ttu-id="e6322-265">Rufen Sie „StartAuthenticationAsync“ auf.</span><span class="sxs-lookup"><span data-stu-id="e6322-265">Call StartAuthenticationAsync</span></span>
    * <span data-ttu-id="e6322-266">Kommunizieren Sie mit dem Begleitgerät, um die erforderlichen HMAC-Vorgänge auszuführen.</span><span class="sxs-lookup"><span data-stu-id="e6322-266">Communicate with the companion device to perform required HMAC operations</span></span>
    * <span data-ttu-id="e6322-267">Rufen Sie „FinishAuthenticationAsync“ auf.</span><span class="sxs-lookup"><span data-stu-id="e6322-267">Call FinishAuthenticationAsync</span></span>
6. <span data-ttu-id="e6322-268">Heben Sie auf Wunsch des Benutzers die Registrierung eines Windows Hello-Begleitgeräts auf (etwa, wenn der Benutzer sein Begleitgerät verloren hat).</span><span class="sxs-lookup"><span data-stu-id="e6322-268">Un-register a Windows Hello companion device when the user requests it (for example, if they've lost their companion device)</span></span>
    * <span data-ttu-id="e6322-269">Führen Sie das Windows Hello-Begleitgerät für den angemeldeten Benutzer mittels „FindAllRegisteredDeviceInfoAsync“ auf.</span><span class="sxs-lookup"><span data-stu-id="e6322-269">Enumerate the Windows Hello companion device for logged in user via FindAllRegisteredDeviceInfoAsync</span></span>
    * <span data-ttu-id="e6322-270">Heben Sie die Registrierung mithilfe von „UnregisterDeviceAsync“ auf.</span><span class="sxs-lookup"><span data-stu-id="e6322-270">Un-register it using UnregisterDeviceAsync</span></span>

### <a name="registration-and-de-registration"></a><span data-ttu-id="e6322-271">Registrierung und Registrierungsaufhebung</span><span class="sxs-lookup"><span data-stu-id="e6322-271">Registration and de-registration</span></span>

<span data-ttu-id="e6322-272">Die Registrierung erfordert zwei API-Aufrufe an den Begleitauthentifizierungsdienst: „RequestStartRegisteringDeviceAsync“ und „FinishRegisteringDeviceAsync“.</span><span class="sxs-lookup"><span data-stu-id="e6322-272">Registration requires two API calls to the Companion Authentication Service: RequestStartRegisteringDeviceAsync and FinishRegisteringDeviceAsync.</span></span>

<span data-ttu-id="e6322-273">Bevor diese Aufrufe vorgenommen werden können, muss die Windows Hello-Begleitgeräte-App überprüfen, ob das Windows Hello-Begleitgerät verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="e6322-273">Before any of these calls are made, the Windows Hello companion device app must make sure that the Windows Hello companion device is available.</span></span> <span data-ttu-id="e6322-274">Wenn das Windows Hello-Begleitgerät für die Generierung der HMAC-Schlüssel (Authentifizierungs- und Geräteschlüssel) zuständig ist, muss die Windows Hello-Begleitgeräte-App außerdem das Begleitgerät zur Generierung der Schlüssel auffordern, bevor einer der beiden obigen Aufrufe durchgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="e6322-274">If the Windows Hello companion device is responsible for generating HMAC keys (authentication and device keys), then the Windows Hello companion device app should also ask the companion device to generate them before making any of the above two calls.</span></span> <span data-ttu-id="e6322-275">Wenn die Windows Hello-Begleitgeräte-App für die Generierung der HMAC-Schlüssel zuständig ist, muss dieser Schritt vor den beiden obigen Aufrufen durchgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="e6322-275">If the Windows Hello companion device app is responsible for generating HMAC keys, then it should do so before calling the above two calls.</span></span>

<span data-ttu-id="e6322-276">Im Zuge des ersten API-Aufrufs (RequestStartRegisteringDeviceAsync) muss die Windows Hello-Begleitgeräte-App außerdem die Gerätefunktionen ermitteln (beispielsweise, ob die Möglichkeit zum sicheren Speichern von HMAC-Schlüsseln besteht) und sie ggf. im Rahmen des API-Aufrufs übergeben.</span><span class="sxs-lookup"><span data-stu-id="e6322-276">Additionally, as part of first API call (RequestStartRegisteringDeviceAsync), the Windows Hello companion device app must decide on device capability and be prepared to pass it as part of the API call; for example, whether the Windows Hello companion device supports secure storage for HMAC keys.</span></span> <span data-ttu-id="e6322-277">Wenn mit der gleichen Windows Hello-Begleitgeräte-App mehrere Versionen des gleichen Begleitgeräts verwaltet werden und sich diese Funktionen ändern (und dies mithilfe einer Geräteabfrage ermittelt werden muss), empfiehlt es sich, die entsprechende Abfrage vor dem ersten API-Aufruf durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="e6322-277">If the same Windows Hello companion device app is used to manage multiple versions of the same companion device and those capabilities change (and requires a device query to decide), we recommend this queries occurs before first API call is made.</span></span>   

<span data-ttu-id="e6322-278">Die erste API (RequestStartRegisteringDeviceAsync) gibt ein Handle zurück, das von der zweiten API (FinishRegisteringDeviceAsync) verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="e6322-278">The first API (RequestStartRegisteringDeviceAsync) will return a handle used by the second API (FinishRegisteringDeviceAsync).</span></span> <span data-ttu-id="e6322-279">Der erste Aufruf für die Registrierung startet die PIN-Abfrage, um sicherzustellen, dass der Benutzer anwesend ist.</span><span class="sxs-lookup"><span data-stu-id="e6322-279">The first call for registration will launch the PIN prompt to make sure user is present.</span></span> <span data-ttu-id="e6322-280">Ist keine PIN eingerichtet, ist dieser Aufruf nicht erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="e6322-280">If no PIN is set up, this call will fail.</span></span> <span data-ttu-id="e6322-281">Über einen Aufruf von „KeyCredentialManager.IsSupportedAsync“ kann die Windows Hello-Begleitgeräte-App auch abfragen, ob eine PIN eingerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="e6322-281">The Windows Hello companion device app can query whether PIN is set up or not via KeyCredentialManager.IsSupportedAsync call as well.</span></span> <span data-ttu-id="e6322-282">Bei dem Aufruf von „RequestStartRegisteringDeviceAsync“ kann auch ein Fehler auftreten, falls die Verwendung des Windows Hello-Begleitgeräts per Richtlinie deaktiviert wurde.</span><span class="sxs-lookup"><span data-stu-id="e6322-282">RequestStartRegisteringDeviceAsync call can also fail if policy has disabled the usage of the Windows Hello companion device.</span></span>

<span data-ttu-id="e6322-283">Das Ergebnis des ersten Aufrufs wird über die Enumeration „SecondaryAuthenticationFactorRegistrationStatus“ zurückgegeben:</span><span class="sxs-lookup"><span data-stu-id="e6322-283">The result of first call is returned via SecondaryAuthenticationFactorRegistrationStatus enum:</span></span>

```C#
{
    Failed = 0,         // Something went wrong in the underlying components
    Started,            // First call succeeded
    CanceledByUser,     // User cancelled PIN prompt
    PinSetupRequired,   // PIN is not set up
    DisabledByPolicy,   // Companion device framework or this app is disabled
}
```

<span data-ttu-id="e6322-284">Mit dem zweiten Aufruf (FinishRegisteringDeviceAsync) wird die Registrierung abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="e6322-284">The second call (FinishRegisteringDeviceAsync) finishes the registration.</span></span> <span data-ttu-id="e6322-285">Im Rahmen des Registrierungsprozesses kann die Windows Hello-Begleitgeräte-App Konfigurationsdaten des Begleitgeräts mit dem Begleitauthentifizierungsdienst speichern.</span><span class="sxs-lookup"><span data-stu-id="e6322-285">As part of registration process, the Windows Hello companion device app can store companion device configuration data with Companion Authentication Service.</span></span> <span data-ttu-id="e6322-286">Für diese Daten gilt eine Größenbeschränkung von 4KB.</span><span class="sxs-lookup"><span data-stu-id="e6322-286">There is a 4K size limit for this data.</span></span> <span data-ttu-id="e6322-287">Die Daten stehen der Windows Hello-Begleitgeräte-App bei der Authentifizierung zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="e6322-287">This data will be available to the Windows Hello companion device app at authentication time.</span></span> <span data-ttu-id="e6322-288">Diese Daten können etwa zum Herstellen einer Verbindung mit dem Windows Hello-Begleitgerät verwendet werden (beispielsweise im Falle einer MAC-Adresse). Ein weiteres Verwendungsbeispiel für Konfigurationsdaten wäre die Verwendung des PCs als Speicherort, falls das Windows Hello-Begleitgerät über keine Speichermöglichkeit verfügt.</span><span class="sxs-lookup"><span data-stu-id="e6322-288">This data can be used, as an example, to connect to the Windows Hello companion device like a MAC address, or if the Windows Hello companion device does not have storage and companion device wants to use PC for storage, then configuration data can be used.</span></span> <span data-ttu-id="e6322-289">Beachten Sie, dass in den Konfigurationsdaten gespeicherte vertrauliche Daten mit einem Schlüssel verschlüsselt werden müssen, der nur dem Windows Hello-Begleitgerät bekannt ist.</span><span class="sxs-lookup"><span data-stu-id="e6322-289">Note that any sensitive data stored as part of configuration data must be encrypted with a key that only the Windows Hello companion device knows.</span></span> <span data-ttu-id="e6322-290">Wenn Konfigurationsdaten von einem Windows-Dienst gespeichert werden, stehen sie der Windows Hello-Begleitgeräte-App außerdem benutzerprofilübergreifend zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="e6322-290">Also, given that configuration data is stored by a Windows service, it is available to the Windows Hello companion device app across user profiles.</span></span>

<span data-ttu-id="e6322-291">Die Windows Hello-Begleitgeräte-App kann „AbortRegisteringDeviceAsync“ aufrufen, um die Registrierung abzubrechen und einen Fehlercode zu übergeben.</span><span class="sxs-lookup"><span data-stu-id="e6322-291">The Windows Hello companion device app can call AbortRegisteringDeviceAsync to cancel the registration and pass in an error code.</span></span> <span data-ttu-id="e6322-292">Der Begleitauthentifizierungsdienst protokolliert den Fehler in den Telemetriedaten.</span><span class="sxs-lookup"><span data-stu-id="e6322-292">The Companion Authentication Service will log the error in the telemetry data.</span></span> <span data-ttu-id="e6322-293">Ein gutes Beispiel für diesen Aufruf wäre etwa, wenn die Registrierung aufgrund eines Windows Hello-Begleitgerätefehlers nicht abgeschlossen werden konnte (beispielsweise, weil die HMAC Schlüssel nicht gespeichert werden können oder die Bluetooth-Verbindung unterbrochen wurde).</span><span class="sxs-lookup"><span data-stu-id="e6322-293">A good example for this call would be when something went wrong with the Windows Hello companion device and it could not finish registration (e.g., it cannot store HMAC keys or BT connection was lost).</span></span>

<span data-ttu-id="e6322-294">Die Windows Hello-Begleitgeräte-App muss dem Benutzer eine Option zur Verfügung stellen, über die er die Registrierung des Windows Hello-Begleitgeräts bei seinem Windows10-Desktopgerät aufheben kann (beispielsweise, wenn er sein Begleitgerät verloren oder eine neuere Version gekauft hat).</span><span class="sxs-lookup"><span data-stu-id="e6322-294">The Windows Hello companion device app must provide an option for the user to de-register their Windows Hello companion device from their Windows 10 desktop (e.g., if they lost their companion device or bought a newer version).</span></span> <span data-ttu-id="e6322-295">Bei Verwendung dieser Option muss die Windows Hello-Begleitgeräte-App „UnregisterDeviceAsync“ aufrufen.</span><span class="sxs-lookup"><span data-stu-id="e6322-295">When the user selects that option, then the Windows Hello companion device app must call UnregisterDeviceAsync.</span></span> <span data-ttu-id="e6322-296">Dieser Aufruf durch die Windows Hello-Begleitgeräte-App sorgt dafür, dass der Begleitgeräte-Authentifizierungsdienst aufseiten des PCs alle Daten (einschließlich der HMAC-Schlüssel) löscht, die mit der speziellen Geräte- und App-ID zusammenhängen.</span><span class="sxs-lookup"><span data-stu-id="e6322-296">This call by the Windows Hello companion device app will trigger the companion device authentication service to delete all data (including HMAC keys) corresponding to the specific device Id and AppId of the caller app from PC side.</span></span> <span data-ttu-id="e6322-297">Dieser API-Aufruf versucht nicht, HMAC-Schlüssel aus der Windows Hello-Begleitgeräte-App oder aufseiten des Begleitgeräts zu löschen.</span><span class="sxs-lookup"><span data-stu-id="e6322-297">This API call does not attempt to delete HMAC keys from either the Windows Hello companion device app or companion device side.</span></span> <span data-ttu-id="e6322-298">Dies muss in der Windows Hello-Begleitgeräte-App implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="e6322-298">That is left for the Windows Hello companion device app to implement.</span></span>

<span data-ttu-id="e6322-299">Sämtliche Fehlermeldungen der Registrierungs- und Registrierungsaufhebungsphase müssen von der Windows Hello-Begleitgeräte-App angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="e6322-299">The Windows Hello companion device app is responsible for showing any error messages that happen in registration and de-registration phase.</span></span>

```C#
using System;
using Windows.Security.Authentication.Identity.Provider;
using Windows.Storage.Streams;
using Windows.Security.Cryptography;
using Windows.UI.Popups;

namespace SecondaryAuthFactorSample
{
    public class DeviceRegistration
    {

        public void async OnRegisterButtonClick()
        {
            //
            // Pseudo function, the deviceId should be retrieved by the application from the device
            //
            string deviceId = await ReadSerialNumberFromDevice();

            IBuffer deviceKey = CryptographicBuffer.GenerateRandom(256/8);
            IBuffer mutualAuthenticationKey = CryptographicBuffer.GenerateRandom(256/8);

            SecondaryAuthenticationFactorRegistration registrationResult =
                await SecondaryAuthenticationFactorRegistration.RequestStartRegisteringDeviceAsync(
                    deviceId,  // deviceId: max 40 wide characters. For example, serial number of the device
                    SecondaryAuthenticationFactorDeviceCapabilities.SecureStorage |
                        SecondaryAuthenticationFactorDeviceCapabilities.HMacSha256 |
                        SecondaryAuthenticationFactorDeviceCapabilities.StoreKeys,
                    "My test device 1", // deviceFriendlyName: max 64 wide characters. For example: John's card
                    "SAMPLE-001", // deviceModelNumber: max 32 wide characters. The app should read the model number from device.
                    deviceKey,
                    mutualAuthenticationKey);

            switch(registerResult.Status)
            {
            case SecondaryAuthenticationFactorRegistrationStatus.Started:
                //
                // Pseudo function:
                // The app needs to retrieve the value from device and set into opaqueBlob
                //
                IBuffer deviceConfigData = ReadConfigurationDataFromDevice();

                if (deviceConfigData != null)
                {
                    await registrationResult.Registration.FinishRegisteringDeviceAsync(deviceConfigData); //config data limited to 4096 bytes
                    MessageDialog dialog = new MessageDialog("The device is registered correctly.");
                    await dialog.ShowAsync();
                }
                else
                {
                    await registrationResult.Registration.AbortRegisteringDeviceAsync("Failed to connect to the device");
                    MessageDialog dialog = new MessageDialog("Failed to connect to the device.");
                    await dialog.ShowAsync();
                }
                break;

            case SecondaryAuthenticationFactorRegistrationStatus.CanceledByUser:
                MessageDialog dialog = new MessageDialog("You didn't enter your PIN.");
                await dialog.ShowAsync();
                break;

            case SecondaryAuthenticationFactorRegistrationStatus.PinSetupRequired:
                MessageDialog dialog = new MessageDialog("Please setup PIN in settings.");
                await dialog.ShowAsync();
                break;

            case SecondaryAuthenticationFactorRegistrationStatus.DisabledByPolicy:
                MessageDialog dialog = new MessageDialog("Your enterprise prevents using this device to sign in.");
                await dialog.ShowAsync();
                break;
            }
        }

        public void async UpdateDeviceList()
        {
            IReadOnlyList<SecondaryAuthenticationFactorInfo> deviceInfoList =
                await SecondaryAuthenticationFactorRegistration.FindAllRegisteredDeviceInfoAsync(
                    SecondaryAuthenticationFactorDeviceFindScope.User);

            if (deviceInfoList.Count > 0)
            {
                foreach (SecondaryAuthenticationFactorInfo deviceInfo in deviceInfoList)
                {
                    //
                    // Add deviceInfo.FriendlyName and deviceInfo.DeviceId into a combo box
                    //
                }
            }
        }

        public void async OnUnregisterButtonClick()
        {
            string deviceId;
            //
            // Read the deviceId from the selected item in the combo box
            //
            await SecondaryAuthenticationFactorRegistration.UnregisterDeviceAsync(deviceId);
        }
    }
}
```

### <a name="authentication"></a><span data-ttu-id="e6322-300">Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="e6322-300">Authentication</span></span>

<span data-ttu-id="e6322-301">Die Authentifizierung erfordert zwei API-Aufrufe an den Begleitauthentifizierungsdienst: „StartAuthenticationAsync“ und „FinishAuthencationAsync“.</span><span class="sxs-lookup"><span data-stu-id="e6322-301">Authentication requires two API calls to the Companion Authentication Service: StartAuthenticationAsync and FinishAuthencationAsync.</span></span>

<span data-ttu-id="e6322-302">Die erste Initiierungs-API gibt ein Handle zurück, das dann von der zweiten API verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="e6322-302">The first initiation API will return a handle used by the second API.</span></span>  <span data-ttu-id="e6322-303">Der erste Aufruf gibt unter anderem eine Nonce zurück, für die (nach Verkettung mit anderen Elementen) ein HMAC-Vorgang mit dem auf dem Windows Hello-Begleitgerät gespeicherten Geräteschlüssel durchgeführt werden muss.</span><span class="sxs-lookup"><span data-stu-id="e6322-303">The first call returns, among other things, a nonce that – once concatenated with other things - needs to be HMAC'ed with the device key stored on the Windows Hello companion device.</span></span> <span data-ttu-id="e6322-304">Der zweite Aufruf gibt die Ergebnisse des HMAC-Vorgangs mit dem Geräteschlüssel zurück und kann in eine erfolgreiche Authentifizierung (Anzeige des Desktops) münden.</span><span class="sxs-lookup"><span data-stu-id="e6322-304">The second call returns the results of HMAC with device key and can potentially end in successful authentication (i.e., the user will see their desktop).</span></span>

<span data-ttu-id="e6322-305">Bei der ersten Initiierungs-API (StartAuthenticationAsync) kann ein Fehler auftreten, falls das Windows Hello-Begleitgerät nach der ursprünglichen Registrierung durch eine Richtlinie deaktiviert wurde.</span><span class="sxs-lookup"><span data-stu-id="e6322-305">The first initiation API (StartAuthenticationAsync) can fail if policy has disabled that Windows Hello companion device after initial registration.</span></span> <span data-ttu-id="e6322-306">Ein Fehler kann außerdem auftreten, wenn der API-Aufruf außerhalb des Zustands „WaitingForUserConfirmation“ oder „CollectingCredential“ erfolgt. (Weitere Informationen finden Sie weiter unten in diesem Abschnitt.)</span><span class="sxs-lookup"><span data-stu-id="e6322-306">It can also fail if the API call was made outside WaitingForUserConfirmation or CollectingCredential states (more on this later in this section).</span></span> <span data-ttu-id="e6322-307">Darüber hinaus kann ein Fehler auftreten, wenn der Aufruf von einer nicht registrierten Begleitgeräte-App stammt.</span><span class="sxs-lookup"><span data-stu-id="e6322-307">It can also fail if an unregistered companion device app calls it.</span></span> <span data-ttu-id="e6322-308">Die Enumeration „SecondaryAuthenticationFactorAuthenticationStatus“ fasst die möglichen Ergebnisse zusammen:</span><span class="sxs-lookup"><span data-stu-id="e6322-308">SecondaryAuthenticationFactorAuthenticationStatus Enum summarizes the possible outcomes:</span></span>

```C#
{
    Failed = 0,                     // Something went wrong in the underlying components
    Started,
    UnknownDevice,                  // Companion device app is not registered with framework
    DisabledByPolicy,               // Policy disabled this device after registration
    InvalidAuthenticationStage,     // Companion device framework is not currently accepting
                                    // incoming authentication requests
}
```

<span data-ttu-id="e6322-309">Beim zweiten API-Aufruf (FinishAuthencationAsync) kann ein Fehler auftreten, wenn die Nonce aus dem ersten Aufruf nicht mehr gültig ist. (Dies ist nach 20Sekunden der Fall.)</span><span class="sxs-lookup"><span data-stu-id="e6322-309">The second API call (FinishAuthencationAsync) can fail if the nonce that was provided in the first call is expired (20 seconds).</span></span> <span data-ttu-id="e6322-310">Die Enumeration „SecondaryAuthenticationFactorFinishAuthenticationStatus“ erfasst die möglichen Ergebnisse.</span><span class="sxs-lookup"><span data-stu-id="e6322-310">SecondaryAuthenticationFactorFinishAuthenticationStatus enum captures possible outcomes.</span></span>

```C#
{
    Failed = 0,     // Something went wrong in the underlying components
    Completed,      // Success
    NonceExpired,   // Nonce is expired
}
```

<span data-ttu-id="e6322-311">Das Timing der beiden API-Aufrufe („StartAuthenticationAsync“ und „FinishAuthencationAsync“) muss sich an der Erfassung der Absichts-, Benutzeranwesenheits- und Mehrdeutigkeitsvermeidungssignale durch das Windows Hello-Begleitgerät orientieren. (Weitere Informationen finden Sie unter „Benutzersignale“.)</span><span class="sxs-lookup"><span data-stu-id="e6322-311">The timing of two API calls (StartAuthenticationAsync and FinishAuthencationAsync) needs to align with how the Windows Hello companion device collects intent, user presence, and disambiguation signals (see User Signals for more details).</span></span> <span data-ttu-id="e6322-312">So darf der zweite Aufruf beispielsweise erst nach Verfügbarkeit des Absichtssignals übermittelt werden.</span><span class="sxs-lookup"><span data-stu-id="e6322-312">For example, the second call must not be submitted until intent signal is available.</span></span> <span data-ttu-id="e6322-313">Anders ausgedrückt: Der PC darf nicht entsperrt werden, wenn der Benutzer dies nicht ausdrücklich beabsichtigt.</span><span class="sxs-lookup"><span data-stu-id="e6322-313">In other words, the PC should not unlock if the user has not expressed intent for it.</span></span> <span data-ttu-id="e6322-314">Um es noch etwas deutlicher zu machen: Wenn die Entsperrung des PCs darauf beruht, dass sich ein Bluetooth-Gerät in Reichweite befindet, muss ein explizites Absichtssignal erfasst werden. Andernfalls wird der PC jedes Mal entsperrt, wenn der Benutzer auf dem Weg in die Küche daran vorbeiläuft.</span><span class="sxs-lookup"><span data-stu-id="e6322-314">To make this more clear, assume that Bluetooth proximity is used for PC unlock, then an explicit intent signal must be collected, otherwise, as soon as user walks by his PC on the way to kitchen, the PC will unlock.</span></span> <span data-ttu-id="e6322-315">Darüber hinaus ist die im ersten Aufruf zurückgegebene Nonce nur für 20Sekunden gültig und läuft dann ab.</span><span class="sxs-lookup"><span data-stu-id="e6322-315">Also, the nonce returned from the first call is time bound (20 seconds) and will expire after certain period.</span></span> <span data-ttu-id="e6322-316">Daher darf der erste Aufruf erst erfolgen, wenn die Windows Hello-Begleitgeräte-App davon ausgehen kann, dass das Begleitgerät vorhanden ist (also etwa per USB angeschlossen oder an das NFC-Lesegerät gehalten wird).</span><span class="sxs-lookup"><span data-stu-id="e6322-316">As a result, the first call only should be made when the Windows Hello companion device app has good indication of companion device presence, e.g., the companion device is inserted into USB port, or tapped on NFC reader.</span></span> <span data-ttu-id="e6322-317">Achten Sie bei Verwendung von Bluetooth darauf, weder den Akku des PCs noch andere laufende Bluetooth-Aktivitäten zu beeinträchtigen, während geprüft wird, ob sich das Windows Hello-Begleitgerät in Reichweite befindet.</span><span class="sxs-lookup"><span data-stu-id="e6322-317">With Bluetooth, care must be taken to avoid affecting battery on PC side or affecting other Bluetooth activities going on at that point when checking for Windows Hello companion device presence.</span></span> <span data-ttu-id="e6322-318">Falls ein Benutzeranwesenheitssignal (etwa die Eingabe einer PIN) erforderlich ist, empfiehlt es sich zudem, den ersten Authentifizierungsaufruf erst nach Erfassung dieses Signals durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="e6322-318">Also, if a user presence signal needs to be provided (e.g., by typing in PIN), it is recommended that the first authentication call is only made after that signal is collected.</span></span>

<span data-ttu-id="e6322-319">Dank des Windows Hello-Begleitgeräteframeworks kann die Windows Hello-Begleitgeräte-App die beiden obigen Aufrufe zu einem geeigneten Zeitpunkt durchführen, da immer genau bekannt ist, in welcher Phase des Authentifizierungsablaufs sich der Benutzer befindet.</span><span class="sxs-lookup"><span data-stu-id="e6322-319">The Windows Hello companion device framework helps the Windows Hello companion device app to make informed decision on when to make above two calls by providing a complete picture of where user is in authentication flow.</span></span> <span data-ttu-id="e6322-320">Zu diesem Zweck informiert das Windows Hello-Begleitgeräteframework die App-Hintergrundaufgabe über Sperrzustandsänderungen.</span><span class="sxs-lookup"><span data-stu-id="e6322-320">Windows Hello companion device framework provides this functionality by providing lock state change notification to app background task.</span></span>

![Begleitgerätefluss](images/companion-device-4.png)

<span data-ttu-id="e6322-322">Im Anschluss finden Sie Details zu den einzelnen Zuständen:</span><span class="sxs-lookup"><span data-stu-id="e6322-322">Details of each of these states are as follows:</span></span>

| <span data-ttu-id="e6322-323">Zustand</span><span class="sxs-lookup"><span data-stu-id="e6322-323">State</span></span>                         | <span data-ttu-id="e6322-324">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e6322-324">Description</span></span>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|----------------------------   |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------    |
| <span data-ttu-id="e6322-325">WaitingForUserConfirmation</span><span class="sxs-lookup"><span data-stu-id="e6322-325">WaitingForUserConfirmation</span></span>    | <span data-ttu-id="e6322-326">Dieses Zustandsänderungs-Benachrichtigungsereignis wird ausgelöst, wenn der Sperrbildschirm eingeblendet wird (beispielsweise, weil der Benutzer WINDOWS+L gedrückt hat).</span><span class="sxs-lookup"><span data-stu-id="e6322-326">This state change notification event is fired when the lock screen comes down (e.g., user pressed Windows + L).</span></span> <span data-ttu-id="e6322-327">Es wird davon abgeraten, Fehlermeldungen in Bezug auf Probleme bei der Suche nach einem Gerät in diesem Zustand anzufordern.</span><span class="sxs-lookup"><span data-stu-id="e6322-327">We recommend not to request any error messages relating to having difficulty finding a device in this state.</span></span> <span data-ttu-id="e6322-328">Im Allgemeinen empfiehlt es sich, nur dann Meldungen anzuzeigen, wenn das Absichtssignal vorliegt.</span><span class="sxs-lookup"><span data-stu-id="e6322-328">In general, we recommend to only show messages when intent signal is available.</span></span> <span data-ttu-id="e6322-329">Die Windows Hello-Begleitgeräte-App muss in diesem Zustand den ersten API-Aufruf für die Authentifizierung durchführen, wenn das Begleitgerät das Absichtssignal (beispielsweise Halten an ein NFC-Lesegerät, Drücken einer Taste des Begleitgeräts oder Ausführen einer bestimmten Geste – etwa Klatschen) erfasst und die Hintergrundaufgabe der Windows Hello-Begleitgeräte-App vom Begleitgerät einen Hinweis dafür erhält, dass das Absichtssignal erkannt wurde.</span><span class="sxs-lookup"><span data-stu-id="e6322-329">The Windows Hello companion device app should make the first API call for authentication in this state if the companion device collects the intent signal (e.g., tapping on NFC reader, press of a button on the companion device or a specific gesture, like clapping), and the Windows Hello companion device app background task receives indication from the companion device that intent signal was detected.</span></span> <span data-ttu-id="e6322-330">Ansonsten gilt: Wenn die Windows Hello-Begleitgeräte-App darauf wartet, dass der Authentifizierungsablauf durch den PC gestartet wird (indem der Benutzer auf dem Sperrbildschirm nach oben wischt oder die LEERTASTE drückt), muss die Windows Hello-Begleitgeräte-App auf den nächsten Zustand (CollectingCredential) warten.</span><span class="sxs-lookup"><span data-stu-id="e6322-330">Otherwise, if the Windows Hello companion device app relies on the PC to start authentication flow (by having user swipe up the unlock screen or hitting space bar), then the Windows Hello companion device app needs to wait for the next state (CollectingCredential).</span></span>     |
| <span data-ttu-id="e6322-331">CollectingCredential</span><span class="sxs-lookup"><span data-stu-id="e6322-331">CollectingCredential</span></span>          | <span data-ttu-id="e6322-332">Dieses Zustandsänderungs-Benachrichtigungsereignis wird ausgelöst, wenn der Benutzer den Laptopdeckel öffnet, eine beliebige Taste auf der Tastatur drückt oder auf dem Sperrbildschirm nach oben wischt.</span><span class="sxs-lookup"><span data-stu-id="e6322-332">This state change notification event is fired when the user either opens their laptop lid, hits any key on their keyboard, or swipes up to the unlock screen.</span></span> <span data-ttu-id="e6322-333">Wenn der Start der Absichtssignalerfassung auf den obigen Aktionen basiert, muss die Windows Hello-Begleitgeräte-App mit der Erfassung des Signals beginnen (etwa mithilfe eines Popupfensters auf dem Begleitgerät, in dem der Benutzer gefragt wird, ob er den PC entsperren möchte).</span><span class="sxs-lookup"><span data-stu-id="e6322-333">If the Windows Hello companion device relies on the above actions to start collecting the intent signal, then the Windows Hello companion device app should start collecting it (e.g., via a pop up on the companion device asking whether user wants to unlock the PC).</span></span> <span data-ttu-id="e6322-334">Dies ist ein guter Zeitpunkt für die Anzeige von Fehlermeldungen, falls die Windows Hello-Begleitgeräte-App ein Benutzeranwesenheitssignal auf dem Begleitgerät benötigt (etwa durch Eingabe einer PIN auf dem Windows Hello-Begleitgerät).</span><span class="sxs-lookup"><span data-stu-id="e6322-334">This would be a good time to provide error cases if the Windows Hello companion device app needs the user to provide a user presence signal on the companion device (like typing in PIN on the Windows Hello companion device).</span></span>                                                                                                                                                                                                                                                                                                                                            |
| <span data-ttu-id="e6322-335">SuspendingAuthentication</span><span class="sxs-lookup"><span data-stu-id="e6322-335">SuspendingAuthentication</span></span>      | <span data-ttu-id="e6322-336">Wenn die Windows Hello-Begleitgeräte-App diesen Zustand empfängt, bedeutet das, dass der Begleitauthentifizierungsdienst keine Authentifizierungsanforderungen mehr akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="e6322-336">When the Windows Hello companion device app receives this state, it means that the Companion Authentication Service has stopped accepting authentication requests.</span></span>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| <span data-ttu-id="e6322-337">CredentialCollected</span><span class="sxs-lookup"><span data-stu-id="e6322-337">CredentialCollected</span></span>           | <span data-ttu-id="e6322-338">Dieser Zustand bedeutet, dass eine andere Windows Hello-Begleitgeräte-App die zweite API aufgerufen hat und der Begleitauthentifizierungsdienst die übermittelten Daten überprüft.</span><span class="sxs-lookup"><span data-stu-id="e6322-338">This means that another Windows Hello companion device app has called the second API and that the Companion Authentication Service is verifying what was submitted.</span></span> <span data-ttu-id="e6322-339">An diesem Punkt akzeptiert der Begleitauthentifizierungsdienst keine weiteren Authentifizierungsanforderungen, es sei denn, die Überprüfung der aktuell übermittelten Anforderung ist nicht erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="e6322-339">At this point, the Companion Authentication Service is not accepting any other authentication requests unless the currently submitted one does not pass verification.</span></span> <span data-ttu-id="e6322-340">Die Windows Hello-Begleitgeräte-App sollte auf den nächsten Zustand warten.</span><span class="sxs-lookup"><span data-stu-id="e6322-340">The Windows Hello companion device app should stay tuned until next state is reached.</span></span>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| <span data-ttu-id="e6322-341">CredentialAuthenticated</span><span class="sxs-lookup"><span data-stu-id="e6322-341">CredentialAuthenticated</span></span>       | <span data-ttu-id="e6322-342">Dieser Zustand bedeutet, dass die übermittelten Anmeldeinformationen akzeptiert wurden.</span><span class="sxs-lookup"><span data-stu-id="e6322-342">This means that the submitted credential worked.</span></span> <span data-ttu-id="e6322-343">„CredentialAuthenticated“ verfügt über die Geräte-ID des erfolgreichen Windows Hello-Begleitgeräts.</span><span class="sxs-lookup"><span data-stu-id="e6322-343">The credentialAuthenticated has the device ID of the Windows Hello companion device that succeeded.</span></span> <span data-ttu-id="e6322-344">Diese muss von der Windows Hello-Begleitgeräte-App überprüft werden, um zu ermitteln, ob das ihr zugeordnete Gerät erfolgreich war.</span><span class="sxs-lookup"><span data-stu-id="e6322-344">The Windows Hello companion device app should make sure to check on that to see if its associated device was the winner.</span></span> <span data-ttu-id="e6322-345">Falls nicht, darf die Windows Hello-Begleitgeräte-App keine nachfolgenden Authentifizierungsabläufe (wie etwa eine Erfolgsmeldung auf dem Begleitgerät oder eine Vibration des Geräts) durchführen.</span><span class="sxs-lookup"><span data-stu-id="e6322-345">If not, then the Windows Hello companion device app should avoid showing any post authentication flows (like success message on the companion device or perhaps a vibration on that device).</span></span> <span data-ttu-id="e6322-346">Falls die übermittelten Anmeldeinformationen nicht akzeptiert wurden, ändert sich der Zustand in „CollectingCredential“.</span><span class="sxs-lookup"><span data-stu-id="e6322-346">Note that if the submitted credential did not work, the state will change to CollectingCredential state.</span></span>                                                                                                                                                                                                                                                                                                                                                                                       |
| <span data-ttu-id="e6322-347">StoppingAuthentication</span><span class="sxs-lookup"><span data-stu-id="e6322-347">StoppingAuthentication</span></span>        | <span data-ttu-id="e6322-348">Die Authentifizierung war erfolgreich, und dem Benutzer wurde der Desktop angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e6322-348">Authentication succeeded and user saw the desktop.</span></span> <span data-ttu-id="e6322-349">Jetzt kann die Beendigung der Hintergrundaufgabe erzwungen werden.</span><span class="sxs-lookup"><span data-stu-id="e6322-349">Time to kill your background task.</span></span> <span data-ttu-id="e6322-350">Heben Sie vor dem Beenden der Hintergrundaufgabe ausdrücklich die Registrierung des StageEvent-Handlers auf.</span><span class="sxs-lookup"><span data-stu-id="e6322-350">Before exiting the backround task, explicitly unregister the StageEvent handler.</span></span> <span data-ttu-id="e6322-351">Dadurch wird die Hintergrundaufgabe schnell beendet.</span><span class="sxs-lookup"><span data-stu-id="e6322-351">This will help the background task exit quickly.</span></span>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |



<span data-ttu-id="e6322-352">Windows Hello-Begleitgeräte-Apps dürfen die beiden Authentifizierungs-APIs nur in den ersten beiden Zuständen aufrufen.</span><span class="sxs-lookup"><span data-stu-id="e6322-352">Windows Hello companion device apps should only call the two authentication APIs in the first two states.</span></span> <span data-ttu-id="e6322-353">Windows Hello-Begleitgeräte-Apps müssen ermitteln, in welchem Szenario das Ereignis ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="e6322-353">Windows Hello companion device apps should check for what scenario this event is being fired.</span></span> <span data-ttu-id="e6322-354">Es gibt zwei Möglichkeiten: beim Entsperren oder nach dem Entsperren.</span><span class="sxs-lookup"><span data-stu-id="e6322-354">There are two possibilities: unlock or post unlock.</span></span> <span data-ttu-id="e6322-355">Derzeit wird nur das Entsperrszenario unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e6322-355">Currently, only unlock is supported.</span></span> <span data-ttu-id="e6322-356">In späteren Versionen werden unter Umständen auch Szenarien nach dem Entsperren unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e6322-356">In upcoming releases, post unlock scenarios may be supported.</span></span> <span data-ttu-id="e6322-357">Die Enumeration „SecondaryAuthenticationFactorAuthenticationScenario“ erfasst diese beiden Optionen:</span><span class="sxs-lookup"><span data-stu-id="e6322-357">The SecondaryAuthenticationFactorAuthenticationScenario enum captures these two options:</span></span>

```C#
{
    SignIn = 0,         // Running under lock screen mode
    CredentialPrompt,   // Running post unlock
}
```

<span data-ttu-id="e6322-358">Vollständiges Codebeispiel:</span><span class="sxs-lookup"><span data-stu-id="e6322-358">Complete code sample:</span></span>

```C#
using System;
using Windows.Security.Authentication.Identity.Provider;
using Windows.Storage.Streams;
using Windows.Security.Cryptography;
using System.Threading;
using Windows.ApplicationModel.Background;

namespace SecondaryAuthFactorSample
{
    public sealed class AuthenticationTask : IBackgroundTask
    {
        private string _deviceId;
        private static AutoResetEvent _exitTaskEvent = new AutoResetEvent(false);
        private static IBackgroundTaskInstance _taskInstance;
        private BackgroundTaskDeferral _deferral;

        private void Authenticate()
        {
            int retryCount = 0;

            while (retryCount < 3)
            {
                //
                // Pseudo code, the svcAuthNonce should be passed to device or generated from device
                //
                IBuffer svcAuthNonce = CryptographicBuffer.GenerateRandom(256/8);

                SecondaryAuthenticationFactorAuthenticationResult authResult = await
                    SecondaryAuthenticationFactorAuthentication.StartAuthenticationAsync(
                        _deviceId,
                        svcAuthNonce);
                if (authResult.Status != SecondaryAuthenticationFactorAuthenticationStatus.Started)
                {
                    SecondaryAuthenticationFactorAuthenticationMessage message;
                    switch (authResult.Status)
                    {
                        case SecondaryAuthenticationFactorAuthenticationStatus.DisabledByPolicy:
                            message = SecondaryAuthenticationFactorAuthenticationMessage.DisabledByPolicy;
                            break;
                        case SecondaryAuthenticationFactorAuthenticationStatus.InvalidAuthenticationStage:
                            // The task might need to wait for a SecondaryAuthenticationFactorAuthenticationStageChangedEvent
                            break;
                        default:
                            return;
                    }

                    // Show error message. Limited to 512 characters wide
                    await SecondaryAuthenticationFactorAuthentication.ShowNotificationMessageAsync(null, message);
                    return;
                }

                //
                // Pseudo function:
                // The device calculates and returns sessionHmac and deviceHmac
                //
                await GetHmacsFromDevice(
                    authResult.Authentication.ServiceAuthenticationHmac,
                    authResult.Authentication.DeviceNonce,
                    authResult.Authentication.SessionNonce,
                    out deviceHmac,
                    out sessionHmac);
                if (sessionHmac == null ||
                    deviceHmac == null)
                {
                    await authResult.Authentication.AbortAuthenticationAsync(
                        "Failed to read data from device");
                    return;
                }

                SecondaryAuthenticationFactorFinishAuthenticationStatus status =
                    await authResult.Authentication.FinishAuthencationAsync(deviceHmac, sessionHmac);
                if (status == SecondaryAuthenticationFactorFinishAuthenticationStatus.NonceExpired)
                {
                    retryCount++;
                    continue;
                }
                else if (status == SecondaryAuthenticationFactorFinishAuthenticationStatus.Completed)
                {
                    // The credential data is collected and ready for unlock
                    return;
                }
            }
        }

        public void OnAuthenticationStageChanged(
            object sender,
            SecondaryAuthenticationFactorAuthenticationStageChangedEventArgs args)
        {
            // The application should check the args.StageInfo.Stage to determine what to do in next. Note that args.StageInfo.Scenario will have the scenario information (SignIn vs CredentialPrompt).

            switch(args.StageInfo.Stage)
            {
            case SecondaryAuthenticationFactorAuthenticationStage.WaitingForUserConfirmation:
                // Show welcome message
                await SecondaryAuthenticationFactorAuthentication.ShowNotificationMessageAsync(
                    null,
                    SecondaryAuthenticationFactorAuthenticationMessage.WelcomeMessageSwipeUp);
                break;

            case SecondaryAuthenticationFactorAuthenticationStage.CollectingCredential:
                // Authenticate device
                Authenticate();
                break;

            case SecondaryAuthenticationFactorAuthenticationStage.CredentialAuthenticated:
                if (args.StageInfo.DeviceId = _deviceId)
                {
                    // Show notification on device about PC unlock
                }
                break;

            case SecondaryAuthenticationFactorAuthenticationStage.StoppingAuthentication:
                // Quit from background task
                _exitTaskEvent.Set();
                break;
            }

            Debug.WriteLine("Authentication Stage = " + args.StageInfo.AuthenticationStage.ToString());
        }

        //
        // The Run method is the entry point of a background task.
        //
        public void Run(IBackgroundTaskInstance taskInstance)
        {
            _taskInstance = taskInstance;
            _deferral = taskInstance.GetDeferral();

            // Register canceled event for this task
            taskInstance.Canceled += TaskInstanceCanceled;

            // Find all device registred by this application
            IReadOnlyList<SecondaryAuthenticationFactorInfo> deviceInfoList =
                await SecondaryAuthenticationFactorRegistration.FindAllRegisteredDeviceInfoAsync(
                    SecondaryAuthenticationFactorDeviceFindScope.AllUsers);

            if (deviceInfoList.Count == 0)
            {
                // Quit the task silently
                return;
            }
            _deviceId = deviceInfoList[0].DeviceId;
            Debug.WriteLine("Use first device '" + _deviceId + "' in the list to signin");

            // Register AuthenticationStageChanged event
            SecondaryAuthenticationFactorRegistration.AuthenticationStageChanged += OnAuthenticationStageChanged;

            // Wait the task exit event
            _exitTaskEvent.WaitOne();

            _deferral.Complete();
        }

        void TaskInstanceCanceled(IBackgroundTaskInstance sender, BackgroundTaskCancellationReason reason)
        {
            _exitTaskEvent.Set();
        }
    }
}
```

### <a name="register-a-background-task"></a><span data-ttu-id="e6322-359">Registrieren einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="e6322-359">Register a background task</span></span>

<span data-ttu-id="e6322-360">Wenn die Windows Hello-Begleitgeräte-App das erste Begleitgerät registriert, muss sie auch die Hintergrundaufgabenkomponente registrieren, die Authentifizierungsinformationen zwischen Gerät und Begleitgeräte-Authentifizierungsdienst übergibt.</span><span class="sxs-lookup"><span data-stu-id="e6322-360">When the Windows Hello companion device app registers the first companion device, it should also register its background task component which will pass authentication information between device and companion device authentication service.</span></span>

```C#
using System;
using Windows.Security.Authentication.Identity.Provider;
using Windows.Storage.Streams;
using Windows.ApplicationModel.Background;

namespace SecondaryAuthFactorSample
{
    public class BackgroundTaskManager
    {
        // Register background task
        public static async Task<IBackgroundTaskRegistration> GetOrRegisterBackgroundTaskAsync(
            string bgTaskName,
            string taskEntryPoint)
        {
            // Check if there's an existing background task already registered
            var bgTask = (from t in BackgroundTaskRegistration.AllTasks
                          where t.Value.Name.Equals(bgTaskName)
                          select t.Value).SingleOrDefault();
            if (bgTask == null)
            {
                BackgroundAccessStatus status =
                    BackgroundExecutionManager.RequestAccessAsync().AsTask().GetAwaiter().GetResult();

                if (status == BackgroundAccessStatus.Denied)
                {
                    Debug.WriteLine("Background Execution is denied.");
                    return null;
                }

                var taskBuilder = new BackgroundTaskBuilder();
                taskBuilder.Name = bgTaskName;
                taskBuilder.TaskEntryPoint = taskEntryPoint;
                taskBuilder.SetTrigger(new SecondaryAuthenticationFactorAuthenticationTrigger());
                bgTask = taskBuilder.Register();
                // Background task is registered
            }

            bgTask.Completed += BgTask_Completed;
            bgTask.Progress += BgTask_Progress;

            return bgTask;
        }
    }
}
```

### <a name="errors-and-messages"></a><span data-ttu-id="e6322-361">Fehler und Meldungen</span><span class="sxs-lookup"><span data-stu-id="e6322-361">Errors and messages</span></span>

<span data-ttu-id="e6322-362">Das Windows Hello-Begleitgeräteframework muss den Benutzer mittels Feedback über Erfolg oder Misserfolg der Anmeldung informieren.</span><span class="sxs-lookup"><span data-stu-id="e6322-362">The Windows Hello companion device framework is responsible for providing feedback to the user about success or failure of signing in.</span></span> <span data-ttu-id="e6322-363">Das Windows Hello-Begleitgeräteframework stellt eine Reihe (lokalisierter) Text- und Fehlermeldungen für die Windows Hello-Begleitgeräte-App zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="e6322-363">The Windows Hello companion device framework will provide a stock of (localized) text and error messages for the Windows Hello companion device app to choose from.</span></span> <span data-ttu-id="e6322-364">Diese werden auf der Anmeldebenutzeroberfläche angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e6322-364">These will be displayed in the logon UI.</span></span>

![Begleitgerätefehler](images/companion-device-5.png)

<span data-ttu-id="e6322-366">Windows Hello-Begleitgeräte-Apps können auf der Anmeldebenutzeroberfläche mithilfe von „ShowNotificationMessageAsync“ Meldungen für den Benutzer anzeigen.</span><span class="sxs-lookup"><span data-stu-id="e6322-366">Windows Hello companion device apps can use ShowNotificationMessageAsync to show messages to user as part of the logon UI.</span></span> <span data-ttu-id="e6322-367">Rufen Sie diese API auf, wenn ein Absichtssignal verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="e6322-367">Call this API when an intent signal is available.</span></span> <span data-ttu-id="e6322-368">Beachten Sie, dass ein Absichtssignal immer aufseiten des Windows Hello-Begleitgeräts erfasst werden muss.</span><span class="sxs-lookup"><span data-stu-id="e6322-368">Note that an intent signal must always be collected on the Windows Hello companion device side.</span></span>

<span data-ttu-id="e6322-369">Es gibt zwei Arten von Meldungen: Anleitungen und Fehler.</span><span class="sxs-lookup"><span data-stu-id="e6322-369">There are two types of messages: guidance and errors.</span></span>

<span data-ttu-id="e6322-370">Anleitungsmeldungen dienen dazu, den Benutzer über die Vorgehensweise zum Starten des Entsperrprozesses zu informieren.</span><span class="sxs-lookup"><span data-stu-id="e6322-370">Guidance messages are designed to show the user how to start the unlock process.</span></span> <span data-ttu-id="e6322-371">Diese Meldungen werden dem Benutzer lediglich einmal (bei der erstmaligen Geräteregistrierung) auf dem Sperrbildschirm angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e6322-371">These messages are only shown to the user once on the lock screen, upon first device registration, and never shown there again.</span></span> <span data-ttu-id="e6322-372">Diese Nachrichten werden auch weiterhin auf dem Sperrbildschirm angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e6322-372">These messages will continue to be shown under the lock screen.</span></span>

<span data-ttu-id="e6322-373">Fehlermeldungen werden immer angezeigt und werden angezeigt, nachdem ein Absichtssignal angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="e6322-373">Error messages are always shown and will be shown after an intent signal is provided.</span></span> <span data-ttu-id="e6322-374">Angesichts der Tatsache, dass vor dem Anzeigen von Meldungen für den Benutzer ein Absichtssignal erfasst werden muss und der Benutzer seine Absicht nur über eines der Windows Hello-Begleitgeräte zum Ausdruck bringt, darf es nicht dazu kommen, dass mehrere Windows Hello-Begleitgeräte um die Anzeige von Fehlermeldungen konkurrieren.</span><span class="sxs-lookup"><span data-stu-id="e6322-374">Given that an intent signal must be collected before showing messages to the user, and the user will provide that intent only using one of the Windows Hello companion devices, there must not be a situation where multiple Windows Hello companion devices race for showing error messages.</span></span> <span data-ttu-id="e6322-375">Daher pflegt das Windows Hello-Begleitgeräteframework keine Warteschlange.</span><span class="sxs-lookup"><span data-stu-id="e6322-375">As a result, the Windows Hello companion device framework does not maintain any queue.</span></span> <span data-ttu-id="e6322-376">Wenn ein Aufrufer eine Fehlermeldung anfordert, wird sie fünf Sekunden lang angezeigt. Während dieser fünf Sekunden werden alle anderen Anforderungen zum Anzeigen einer Fehlermeldung verworfen.</span><span class="sxs-lookup"><span data-stu-id="e6322-376">When a caller asks for an error message, it will be shown for 5 seconds and all other requests for showing an error message in that 5 seconds are dropped.</span></span> <span data-ttu-id="e6322-377">Nach Ablauf der fünf Sekunden hat ein anderer Aufrufer die Möglichkeit, eine Fehlermeldung anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="e6322-377">Once 5 seconds has passed, then the opportunity arises for another caller to show an error message.</span></span> <span data-ttu-id="e6322-378">Das Blockieren des Fehlerkanals durch Aufrufer ist nicht zulässig.</span><span class="sxs-lookup"><span data-stu-id="e6322-378">We prohibit any caller from jamming the error channel.</span></span>

<span data-ttu-id="e6322-379">Folgende Anleitungs- und Fehlermeldungen stehen zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="e6322-379">Guidance and error messages are as follows.</span></span> <span data-ttu-id="e6322-380">Der Gerätename ist ein Parameter und wird von der Begleitgeräte-App als Teil von „ShowNotificationMessageAsync“ übergeben.</span><span class="sxs-lookup"><span data-stu-id="e6322-380">Device name is a parameter passed by the companion device app as part of ShowNotificationMessageAsync.</span></span>

**<span data-ttu-id="e6322-381">Anleitung</span><span class="sxs-lookup"><span data-stu-id="e6322-381">Guidance</span></span>**

- <span data-ttu-id="e6322-382">„Wischen Sie nach oben oder drücken Sie die LEERTASTE, um sich mit *Gerätename* anzumelden.“</span><span class="sxs-lookup"><span data-stu-id="e6322-382">"Swipe up or press space bar to sign in with *device name*."</span></span>
- <span data-ttu-id="e6322-383">„Einrichtung des Begleitgeräts.</span><span class="sxs-lookup"><span data-stu-id="e6322-383">"Setting up your companion device.</span></span> <span data-ttu-id="e6322-384">Bitte warten Sie oder verwenden Sie eine andere Anmeldeoption.“</span><span class="sxs-lookup"><span data-stu-id="e6322-384">Please wait or use another sign-in option."</span></span>
- <span data-ttu-id="e6322-385">„Berühren Sie *Gerätename* zur Anmeldung an das NFC-Lesegerät.“</span><span class="sxs-lookup"><span data-stu-id="e6322-385">"Tap *device name* to the NFC reader to sign in."</span></span>
- <span data-ttu-id="e6322-386">„*Gerätename* wird gesucht ...“</span><span class="sxs-lookup"><span data-stu-id="e6322-386">"Looking for *device name* ..."</span></span>
- <span data-ttu-id="e6322-387">„Schließen Sie *Gerätename* zur Anmeldung an einen USB-Anschluss an.“</span><span class="sxs-lookup"><span data-stu-id="e6322-387">"Plug *device name* into a USB port to sign in."</span></span>

**<span data-ttu-id="e6322-388">Fehler</span><span class="sxs-lookup"><span data-stu-id="e6322-388">Errors</span></span>**

- <span data-ttu-id="e6322-389">„Anmeldeanweisungen finden Sie auf *Gerätename*.“</span><span class="sxs-lookup"><span data-stu-id="e6322-389">"See *device name* for sign-in instructions."</span></span>
- <span data-ttu-id="e6322-390">„Aktivieren Sie Bluetooth, um *Gerätename* für die Anmeldung zu verwenden.“</span><span class="sxs-lookup"><span data-stu-id="e6322-390">"Turn on Bluetooth to use *device name* to sign in."</span></span>
- <span data-ttu-id="e6322-391">„Aktivieren Sie NFC, um *Gerätename* für die Anmeldung zu verwenden.“</span><span class="sxs-lookup"><span data-stu-id="e6322-391">"Turn on NFC to use *device name* to sign in."</span></span>
- <span data-ttu-id="e6322-392">„Stellen Sie eine WLAN-Verbindung her, um *Gerätename* für die Anmeldung zu verwenden.“</span><span class="sxs-lookup"><span data-stu-id="e6322-392">"Connect to a Wi-Fi network to use *device name* to sign in."</span></span>
- <span data-ttu-id="e6322-393">„Tippen Sie erneut auf *Gerätename*.“</span><span class="sxs-lookup"><span data-stu-id="e6322-393">"Tap *device name* again."</span></span>
- <span data-ttu-id="e6322-394">„In Ihrem Unternehmen ist keine Anmeldung mit *Gerätename* möglich.</span><span class="sxs-lookup"><span data-stu-id="e6322-394">"Your enterprise prevents sign in with *device name*.</span></span> <span data-ttu-id="e6322-395">Verwenden Sie eine andere Anmeldeoption.“</span><span class="sxs-lookup"><span data-stu-id="e6322-395">Use another sign-in option."</span></span>
- <span data-ttu-id="e6322-396">„Tippen Sie zur Anmeldung auf *Gerätename*.“</span><span class="sxs-lookup"><span data-stu-id="e6322-396">"Tap *device name* to sign in."</span></span>
- <span data-ttu-id="e6322-397">„Legen Sie Ihren Finger zur Anmeldung auf *Gerätename*.“</span><span class="sxs-lookup"><span data-stu-id="e6322-397">"Rest your finger on *device name* to sign in."</span></span>
- <span data-ttu-id="e6322-398">„Wischen Sie zur Anmeldung mit Ihrem Finger über *Gerätename*.“</span><span class="sxs-lookup"><span data-stu-id="e6322-398">"Swipe your finger on *device name* to sign in."</span></span>
- <span data-ttu-id="e6322-399">„Anmeldung mit *Gerätename* nicht möglich.</span><span class="sxs-lookup"><span data-stu-id="e6322-399">"Couldn’t sign in with *device name*.</span></span> <span data-ttu-id="e6322-400">Verwenden Sie eine andere Anmeldeoption.“</span><span class="sxs-lookup"><span data-stu-id="e6322-400">Use another sign-in option."</span></span>
- <span data-ttu-id="e6322-401">„Es ist ein Fehler aufgetreten.</span><span class="sxs-lookup"><span data-stu-id="e6322-401">"Something went wrong.</span></span> <span data-ttu-id="e6322-402">Verwenden Sie eine andere Anmeldeoption, und richten Sie *Gerätename* erneut ein.“</span><span class="sxs-lookup"><span data-stu-id="e6322-402">Use another sign-in option, and then set up *device name* again."</span></span>
- <span data-ttu-id="e6322-403">„Versuchen Sie es noch mal.“</span><span class="sxs-lookup"><span data-stu-id="e6322-403">"Try again."</span></span>
- <span data-ttu-id="e6322-404">„Sagen Sie Ihre gesprochene Passphrase in *Gerätename*.“</span><span class="sxs-lookup"><span data-stu-id="e6322-404">"Say your Spoken Passphrase into *device name*."</span></span>
- <span data-ttu-id="e6322-405">„Bereit für die Anmeldung mit *Gerätename*.“</span><span class="sxs-lookup"><span data-stu-id="e6322-405">"Ready to sign in with *device name*."</span></span>
- <span data-ttu-id="e6322-406">„Verwenden Sie zuerst eine andere Anmeldeoption. Dann können Sie *Gerätename* verwenden, um sich anzumelden.“</span><span class="sxs-lookup"><span data-stu-id="e6322-406">"Use another sign-in option first, then you can use *device name* to sign in."</span></span>

### <a name="enumerating-registered-devices"></a><span data-ttu-id="e6322-407">Aufzählen registrierter Geräte</span><span class="sxs-lookup"><span data-stu-id="e6322-407">Enumerating registered devices</span></span>

<span data-ttu-id="e6322-408">Die Windows Hello-Begleitgeräte-App kann durch Aufrufen von „FindAllRegisteredDeviceInfoAsync“ die registrierten Begleitgeräte aufzählen.</span><span class="sxs-lookup"><span data-stu-id="e6322-408">The Windows Hello companion device app can enumerate the list of registered companion devices via FindAllRegisteredDeviceInfoAsync call.</span></span> <span data-ttu-id="e6322-409">Diese API unterstützt zwei Abfragetypen (definiert durch die Enumeration „SecondaryAuthenticationFactorDeviceFindScope“):</span><span class="sxs-lookup"><span data-stu-id="e6322-409">This API supports two query types defined via enum SecondaryAuthenticationFactorDeviceFindScope:</span></span>

```C#
{
    User = 0,
    AllUsers,
}
```

<span data-ttu-id="e6322-410">Der erste Bereich gibt die Liste der Geräte für den angemeldeten Benutzer zurück.</span><span class="sxs-lookup"><span data-stu-id="e6322-410">The first scope returns the list of devices for the logged on user.</span></span> <span data-ttu-id="e6322-411">Der zweite gibt die Liste für alle Benutzer auf dem PC zurück.</span><span class="sxs-lookup"><span data-stu-id="e6322-411">The second one returns the list for all users on that PC.</span></span> <span data-ttu-id="e6322-412">Der erste Bereich muss beim Aufheben der Registrierung verwendet werden, um zu verhindern, dass die Registrierung für ein Windows Hello-Begleitgerät eines anderen Benutzers aufgehoben wird.</span><span class="sxs-lookup"><span data-stu-id="e6322-412">The first scope must be used at un-registration time to avoid un-registering another user's Windows Hello companion device.</span></span> <span data-ttu-id="e6322-413">Der zweite muss bei der Authentifizierung oder Registrierung verwendet werden: Bei der Registrierung kann diese Enumeration dazu beitragen, eine doppelte Registrierung des gleichen Windows Hello-Begleitgeräts durch die App zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="e6322-413">The second one must be used at authentication or registration time: at registration time, this enumeration can help the app avoid trying to register the same Windows Hello companion device twice.</span></span>

<span data-ttu-id="e6322-414">Hinweis: Selbst wenn die App diese Überprüfung nicht durchführt, wird eine mehrmalige Registrierung des gleichen Windows Hello-Begleitgeräts durch den PC verhindert.</span><span class="sxs-lookup"><span data-stu-id="e6322-414">Note that even if the app does not perform this check, the PC does and will reject the same Windows Hello companion device from being registered more than once.</span></span> <span data-ttu-id="e6322-415">Wenn zum Zeitpunkt der Authentifizierung der Bereich „AllUsers“ verwendet wird, kann die Windows Hello-Begleitgeräte-App den Wechsel des Benutzerflusses besser unterstützen: BenutzerA wird angemeldet, während BenutzerB angemeldet ist. (Dazu müssen beide Benutzer die Windows Hello-Begleitgeräte-App installiert haben, BenutzerA muss seine Begleitgeräte beim PC registriert haben, und auf dem PC muss der Sperr- oder der Anmeldebildschirm angezeigt werden.)</span><span class="sxs-lookup"><span data-stu-id="e6322-415">At authentication time, using the AllUsers scope helps the Windows Hello companion device app support switch user flow: log on user A when user B is logged in (this requires that both users have installed the Windows Hello companion device app and user A has registered their companion devices with the PC and the PC is sitting on lock screen (or logon screen)).</span></span>

## <a name="security-requirements"></a><span data-ttu-id="e6322-416">Sicherheitsanforderungen</span><span class="sxs-lookup"><span data-stu-id="e6322-416">Security requirements</span></span>

<span data-ttu-id="e6322-417">Der Begleitauthentifizierungsdienst bietet folgende Sicherheitsvorkehrungen:</span><span class="sxs-lookup"><span data-stu-id="e6322-417">The Companion Authentication Service provides the following security protections.</span></span>

- <span data-ttu-id="e6322-418">Schadsoftware auf einem Windows10-Desktopgerät, die als mittlerer Benutzer oder App-Container ausgeführt wird, kann über das Windows Hello-Begleitgerät nicht unbemerkt auf (im Rahmen von Windows Hello gespeicherte) Benutzeranmeldeinformationsschlüssel auf dem PC zugreifen.</span><span class="sxs-lookup"><span data-stu-id="e6322-418">Malware on a Windows 10 desktop device running as a medium user or app container cannot use the Windows Hello companion device to access user credential keys (stored as part of Windows Hello) on a PC silently.</span></span>
- <span data-ttu-id="e6322-419">Ein böswilliger Benutzer auf einem Windows10-Desktopgerät kann kein Windows Hello-Begleitgerät eines anderen Benutzers auf dem Windows10-Desktopgerät verwenden, um unbemerkt auf dessen Benutzeranmeldeinformationsschlüssel (auf dem gleichen Windows10-Desktopgerät) zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="e6322-419">A malicious user on a Windows 10 desktop device cannot use the Windows Hello companion device that belongs to another user on that Windows 10 desktop device to get silent access to his user credential keys (on the same Windows 10 desktop device).</span></span>
- <span data-ttu-id="e6322-420">Schadsoftware auf dem Windows Hello-Begleitgerät kann nicht unbemerkt auf die Benutzeranmeldeinformationsschlüssel auf dem Windows10-Desktopgerät zugreifen und auch keine Funktionen und keinen Code nutzen, die speziell für das Windows Hello-Begleitgeräteframework entwickelt wurden.</span><span class="sxs-lookup"><span data-stu-id="e6322-420">Malware on the Windows Hello companion device cannot silently get access to user credential keys on a Windows 10 desktop device, including leveraging functionality or code developed specifically for the Windows Hello companion device framework.</span></span>
- <span data-ttu-id="e6322-421">Ein böswilliger Benutzer kann ein Windows10-Desktopgerät nicht durch Abfangen und späteres Wiedergeben von Datenverkehr zwischen Windows Hello-Begleitgerät und Windows10-Desktopgerät entsperren.</span><span class="sxs-lookup"><span data-stu-id="e6322-421">A malicious user cannot unlock a Windows 10 desktop device by capturing traffic between the Windows Hello companion device and the Windows 10 desktop device and replaying it later.</span></span> <span data-ttu-id="e6322-422">Die Verwendung von Nonce, Authentifizierungsschlüssel und HMAC in unserem Protokoll schützt zuverlässig vor Replay-Angriffen.</span><span class="sxs-lookup"><span data-stu-id="e6322-422">Usage of nonce, authkey, and HMAC in our protocol guarantees protection against a replay attack.</span></span>
- <span data-ttu-id="e6322-423">Schadsoftware oder ein böswilliger Benutzer auf einem nicht autorisierten PC kann nicht über ein Windows Hello-Begleitgerät auf den PC eines regulären Benutzers zugreifen.</span><span class="sxs-lookup"><span data-stu-id="e6322-423">Malware or a malicious user on a rouge PC cannot use Windows Hello companion device to get access to honest user PC.</span></span> <span data-ttu-id="e6322-424">Dies wird durch die gegenseitige Authentifizierung zwischen Begleitauthentifizierungsdienst und Windows Hello-Begleitgerät mit Authentifizierungsschlüssel und HMAC in unserem Protokoll erreicht.</span><span class="sxs-lookup"><span data-stu-id="e6322-424">This is achieved through mutual authentication between Companion Authentication Service and Windows Hello companion device through usage of authkey and HMAC in our protocol.</span></span>

<span data-ttu-id="e6322-425">Der Schlüssel für die oben aufgeführten Sicherheitsvorkehrungen liegt im Schutz der HMAC Schlüssel vor unbefugtem Zugriff sowie in der Überprüfung der Benutzeranwesenheit.</span><span class="sxs-lookup"><span data-stu-id="e6322-425">The key to achieve the security protections enumerated above is to protect HMAC keys from unauthorized access and also verifying user presence.</span></span> <span data-ttu-id="e6322-426">Genauer gesagt müssen folgende Anforderungen erfüllt werden:</span><span class="sxs-lookup"><span data-stu-id="e6322-426">More specifically, it must satisfy these requirements:</span></span>

- <span data-ttu-id="e6322-427">Schutz des Windows Hello-Begleitgeräts vor Klonversuchen</span><span class="sxs-lookup"><span data-stu-id="e6322-427">Provide protection against cloning the Windows Hello companion device</span></span>
- <span data-ttu-id="e6322-428">Schutz vor Abhörversuchen, wenn HMAC-Schlüssel zur Registrierung an den PC gesendet werden</span><span class="sxs-lookup"><span data-stu-id="e6322-428">Provide protection against eavesdropping when sending HMAC keys at registration time to the PC</span></span>
- <span data-ttu-id="e6322-429">Verfügbarkeit des Benutzeranwesenheitssignals</span><span class="sxs-lookup"><span data-stu-id="e6322-429">Make sure that user presence signal is available</span></span>
