---
Description: The JavaScript API for the Microsoft Take a Test app allows you to do secure assessments. Take a Test provides a secure browser that prevents students from using other computer or internet resources during a test.
title: JavaScript-API „Prüfung”
author: PatrickFarley
ms.author: pafarley
ms.assetid: 9bff6318-504c-4d0e-ba80-1a5ea45743da
ms.date: 10/06/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 43edadfba169ddae85818f8ef1dbd1e7f4adba64
ms.sourcegitcommit: 6618517dc0a4e4100af06e6d27fac133d317e545
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2018
ms.locfileid: "1691359"
---
# <a name="take-a-test-javascript-api"></a><span data-ttu-id="0847c-103">JavaScript-API „Prüfung”</span><span class="sxs-lookup"><span data-stu-id="0847c-103">Take a Test JavaScript API</span></span>

<span data-ttu-id="0847c-104">[Prüfung](https://technet.microsoft.com/edu/windows/take-tests-in-windows-10) ist eine browserbasierte App, die gesperrte Online-Prüfungen rendert. So können sich Lehrer/Dozenten auf den Prüfungsinhalt konzentrieren, anstatt sich um die Bereitstellung einer sicheren Testumgebung kümmern zu müssen.</span><span class="sxs-lookup"><span data-stu-id="0847c-104">[Take a Test](https://technet.microsoft.com/edu/windows/take-tests-in-windows-10) is a browser-based app that renders locked down online assessments for high-stakes testing, allowing educators to focus on the assessment content rather than how to provide a secure testing environment.</span></span> <span data-ttu-id="0847c-105">Um dies zu erreichen, wird eine JavaScript-API verwendet, die von jeder Web-Anwendung genutzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="0847c-105">To achieve this, it uses a JavaScript API that any web application can utilize.</span></span> <span data-ttu-id="0847c-106">Die API „Prüfung“ unterstützt den [Browser-API-Standard SBAC](http://www.smarterapp.org/documents/SecureBrowserRequirementsSpecifications_0-3.pdf) zur Durchführung wichtiger allgemeiner Kernprüfungen.</span><span class="sxs-lookup"><span data-stu-id="0847c-106">The Take-a-test API supports the [SBAC browser API standard](http://www.smarterapp.org/documents/SecureBrowserRequirementsSpecifications_0-3.pdf) for high stakes common core testing.</span></span>

<span data-ttu-id="0847c-107">Weitere Informationen zur App selbst finden Sie unter [Technische Referenz zur App „Prüfung“](https://technet.microsoft.com/edu/windows/take-a-test-app-technical?f=255&MSPPError=-2147217396).</span><span class="sxs-lookup"><span data-stu-id="0847c-107">See the [Take a Test app technical reference](https://technet.microsoft.com/edu/windows/take-a-test-app-technical?f=255&MSPPError=-2147217396) for more information about the app itself.</span></span>

<span data-ttu-id="0847c-108">Hilfe zur Problembehandlung finden Sie unter [Problembehandlung bei Microsoft Prüfung mithilfe der Ereignisanzeige](troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="0847c-108">For troubleshooting help, see [Troubleshoot Microsoft Take a Test with the event viewer](troubleshooting.md).</span></span>

## <a name="reference-documentation"></a><span data-ttu-id="0847c-109">Referenzdokumentation</span><span class="sxs-lookup"><span data-stu-id="0847c-109">Reference documentation</span></span>
<span data-ttu-id="0847c-110">Die Prüfungs-APIs gibt es in den folgenden Namespaces.</span><span class="sxs-lookup"><span data-stu-id="0847c-110">The Take a Test APIs exist in the following namespaces.</span></span> <span data-ttu-id="0847c-111">Beachten Sie, dass alle APIs von einem globalen `SecureBrowser`-Objekt abhängen.</span><span class="sxs-lookup"><span data-stu-id="0847c-111">Note that all of the APIs depend on a global `SecureBrowser` object.</span></span>

| <span data-ttu-id="0847c-112">Namespace</span><span class="sxs-lookup"><span data-stu-id="0847c-112">Namespace</span></span> | <span data-ttu-id="0847c-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0847c-113">Description</span></span> |
|-----------|-------------|
|[<span data-ttu-id="0847c-114">Sicherheitsnamespace</span><span class="sxs-lookup"><span data-stu-id="0847c-114">security namespace</span></span>](#security-namespace)|<span data-ttu-id="0847c-115">Enthält APIs, mit denen Sie das Gerät zu Testzwecken sperren und eine Testumgebung erzwingen können.</span><span class="sxs-lookup"><span data-stu-id="0847c-115">Contains APIs that enable you to lock down the device for testing and enforce a testing environment.</span></span> |

> [!NOTE]
> <span data-ttu-id="0847c-116">Der Namespace Text-zu-Sprache (TTS) wurde ab Windows10 Version 1709 entfernt.</span><span class="sxs-lookup"><span data-stu-id="0847c-116">The text-to-speech (TTS) namespace has been removed as of Windows 10 version 1709.</span></span> <span data-ttu-id="0847c-117">Die [Microsoft Edge Speech Synthesis API](https://blogs.windows.com/msedgedev/2016/06/01/introducing-speech-synthesis-api/), eine Implementierung der [W3C-Sprach-API](https://dvcs.w3.org/hg/speech-api/raw-file/tip/webspeechapi.html), ist nun die empfohlene Lösung für die Text-zu-Sprache-Implementierung.</span><span class="sxs-lookup"><span data-stu-id="0847c-117">The [Microsoft Edge Speech Synthesis API](https://blogs.windows.com/msedgedev/2016/06/01/introducing-speech-synthesis-api/), an implementation of the [W3C Speech Api](https://dvcs.w3.org/hg/speech-api/raw-file/tip/webspeechapi.html), is now the recommended solution for text-to-speech implementation.</span></span>

### <a name="security-namespace"></a><span data-ttu-id="0847c-118">Sicherheitsnamespace</span><span class="sxs-lookup"><span data-stu-id="0847c-118">Security namespace</span></span>

<span data-ttu-id="0847c-119">Der Sicherheitsnamespace ermöglicht das Sperren des Geräts, das Überprüfen der Liste der Benutzer- und Systemprozesse, das Abrufen von MAC- und IP-Adressen und das Löschen von zwischengespeicherten Webressourcen.</span><span class="sxs-lookup"><span data-stu-id="0847c-119">The security namespace you to lock down the device, check the list of user and system processes, obtain MAC and IP addresses, and clear cached web resources.</span></span>

| <span data-ttu-id="0847c-120">Methode</span><span class="sxs-lookup"><span data-stu-id="0847c-120">Method</span></span> | <span data-ttu-id="0847c-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0847c-121">Description</span></span>   |
|--------|---------------|
|[<span data-ttu-id="0847c-122">lockDown</span><span class="sxs-lookup"><span data-stu-id="0847c-122">lockDown</span></span>](#lockDown) | <span data-ttu-id="0847c-123">Sperrt das Gerät für Testzwecke.</span><span class="sxs-lookup"><span data-stu-id="0847c-123">Locks down the device for testing.</span></span> |
|[<span data-ttu-id="0847c-124">isEnvironmentSecure</span><span class="sxs-lookup"><span data-stu-id="0847c-124">isEnvironmentSecure</span></span>](#isEnvironmentSecure) | <span data-ttu-id="0847c-125">Stellt fest, ob auf das Gerät noch der Sperrmodus-Kontext angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="0847c-125">Determines whether the lockdown context is still applied to the device.</span></span> |
|[<span data-ttu-id="0847c-126">getDeviceInfo</span><span class="sxs-lookup"><span data-stu-id="0847c-126">getDeviceInfo</span></span>](#getDeviceInfo) | <span data-ttu-id="0847c-127">Ruft Details zur Plattform ab, auf der die Testanwendung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="0847c-127">Gets details about the platform on which the testing application is running.</span></span> |
|[<span data-ttu-id="0847c-128">examineProcessList</span><span class="sxs-lookup"><span data-stu-id="0847c-128">examineProcessList</span></span>](#examineProcessList)|<span data-ttu-id="0847c-129">Ruft die Liste der ausgeführten Benutzer- und Systemprozesse ab.</span><span class="sxs-lookup"><span data-stu-id="0847c-129">Gets the list of running user and system processes.</span></span>|
|[<span data-ttu-id="0847c-130">close</span><span class="sxs-lookup"><span data-stu-id="0847c-130">close</span></span>](#close) | <span data-ttu-id="0847c-131">Schließt den Browser und entsperrt das Gerät.</span><span class="sxs-lookup"><span data-stu-id="0847c-131">Closes the browser and unlocks the device.</span></span> |
|[<span data-ttu-id="0847c-132">getPermissiveMode</span><span class="sxs-lookup"><span data-stu-id="0847c-132">getPermissiveMode</span></span>](#getPermissiveMode)|<span data-ttu-id="0847c-133">Überprüft, ob der eingeschränkte Modus aktiviert oder deaktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="0847c-133">Checks if permissive mode is on or off.</span></span>|
|[<span data-ttu-id="0847c-134">setPermissiveMode</span><span class="sxs-lookup"><span data-stu-id="0847c-134">setPermissiveMode</span></span>](#setPermissiveMode)|<span data-ttu-id="0847c-135">Schaltet den eingeschränkten Modus ein oder aus.</span><span class="sxs-lookup"><span data-stu-id="0847c-135">Toggles permissive mode on or off.</span></span>|
|[<span data-ttu-id="0847c-136">emptyClipBoard</span><span class="sxs-lookup"><span data-stu-id="0847c-136">emptyClipBoard</span></span>](#emptyClipBoard)|<span data-ttu-id="0847c-137">Löscht die Zwischenablage des Systems.</span><span class="sxs-lookup"><span data-stu-id="0847c-137">Clears the system clipboard.</span></span>|
|[<span data-ttu-id="0847c-138">getMACAddress</span><span class="sxs-lookup"><span data-stu-id="0847c-138">getMACAddress</span></span>](#getMACAddress)|<span data-ttu-id="0847c-139">Ruft die Liste der MAC-Adressen für das Gerät ab.</span><span class="sxs-lookup"><span data-stu-id="0847c-139">Gets the list of MAC addresses for the device.</span></span>|
|[<span data-ttu-id="0847c-140">getStartTime</span><span class="sxs-lookup"><span data-stu-id="0847c-140">getStartTime</span></span>](#getStartTime) | <span data-ttu-id="0847c-141">Ruft die Zeit ab, zu der die Test-App gestartet wurde.</span><span class="sxs-lookup"><span data-stu-id="0847c-141">Gets the time that the testing app was started.</span></span> |
|[<span data-ttu-id="0847c-142">getCapability</span><span class="sxs-lookup"><span data-stu-id="0847c-142">getCapability</span></span>](#getCapability) | <span data-ttu-id="0847c-143">Fragt ab, ob eine Funktion aktiviert oder deaktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="0847c-143">Queries whether a capability is enabled or disabled.</span></span> |
|[<span data-ttu-id="0847c-144">setCapability</span><span class="sxs-lookup"><span data-stu-id="0847c-144">setCapability</span></span>](#setCapability)|<span data-ttu-id="0847c-145">Aktiviert oder deaktiviert die angegebene Funktion.</span><span class="sxs-lookup"><span data-stu-id="0847c-145">Enables or disables the specified capability.</span></span>| 
|[<span data-ttu-id="0847c-146">isRemoteSession</span><span class="sxs-lookup"><span data-stu-id="0847c-146">isRemoteSession</span></span>](#isRemoteSession) | <span data-ttu-id="0847c-147">Überprüft, ob die aktuelle Sitzung remote angemeldet ist.</span><span class="sxs-lookup"><span data-stu-id="0847c-147">Checks if the current session is logged in remotely.</span></span> |
|[<span data-ttu-id="0847c-148">isVMSession</span><span class="sxs-lookup"><span data-stu-id="0847c-148">isVMSession</span></span>](#isVMSession) | <span data-ttu-id="0847c-149">Überprüft, ob die aktuelle Sitzung auf einem virtuellen Computer ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="0847c-149">Checks if the current session is running in a virtual machine.</span></span> |

---

<span id="lockDown"/>

### <a name="lockdown"></a><span data-ttu-id="0847c-150">lockDown</span><span class="sxs-lookup"><span data-stu-id="0847c-150">lockDown</span></span>
<span data-ttu-id="0847c-151">Sperrt das Gerät.</span><span class="sxs-lookup"><span data-stu-id="0847c-151">Locks down the device.</span></span> <span data-ttu-id="0847c-152">Wird auch zum Entsperren des Geräts verwendet.</span><span class="sxs-lookup"><span data-stu-id="0847c-152">Also used to unlock the device.</span></span> <span data-ttu-id="0847c-153">Die Test-Webanwendung führt diesen Aufruf aus, bevor Studenten mit dem Testen beginnen dürfen.</span><span class="sxs-lookup"><span data-stu-id="0847c-153">The testing web application will invoke this call prior to allowing students to start testing.</span></span> <span data-ttu-id="0847c-154">Der Implementierer ist erforderlich, um alle notwendigen Aktionen zum Schutz der Testumgebung durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="0847c-154">The implementer is required to take any actions necessary to secure the testing environment.</span></span> <span data-ttu-id="0847c-155">Die Schritte zum Schutz der Umgebung sind gerätespezifisch und beinhalten Aspekte wie z.B. das Deaktivieren von Bildschirmaufnahmen, das Deaktivieren des Sprachchats im sicheren Modus, das Löschen der Zwischenablage des Systems, das Wechseln zu einem Kioskmodus, das Deaktivieren von Leerzeichen in OSX10.7+-Geräten usw. Die Testanwendung aktiviert den Sperrmodus, bevor eine Prüfung beginnt, und deaktiviert den Sperrmodus wieder, wenn der Student die Prüfung abgeschlossen und den sicheren Test verlassen hat.</span><span class="sxs-lookup"><span data-stu-id="0847c-155">The steps taken to secure the environment are device specific and for example, include aspects such as disabling screen captures, disabling voice chat when in secure mode, clearing the system clipboard, entering into a kiosk mode, disabling Spaces in OSX 10.7+ devices, etc. The testing application will enable lockdown before an assessment commences and will disable the lockdown when the student has completed the assessment and is out of the secure test.</span></span>

**<span data-ttu-id="0847c-156">Syntax</span><span class="sxs-lookup"><span data-stu-id="0847c-156">Syntax</span></span>**  
`void SecureBrowser.security.lockDown(Boolean enable, Function onSuccess, Function onError);`

**<span data-ttu-id="0847c-157">Parameter</span><span class="sxs-lookup"><span data-stu-id="0847c-157">Parameters</span></span>**  
* `enable`<span data-ttu-id="0847c-158"> - **true**, wenn die App „Prüfung“ über dem Sperrbildschirm ausgeführt werden soll und die in diesem [Dokument](https://technet.microsoft.com/edu/windows/take-a-test-app-technical?f=255&MSPPError=-2147217396) behandelten Richtlinien angewendet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="0847c-158"> - **true** to run the Take-a-Test app above the lock screen and apply policies discussed in this [document](https://technet.microsoft.com/edu/windows/take-a-test-app-technical?f=255&MSPPError=-2147217396).</span></span> <span data-ttu-id="0847c-159">**false** hält die Ausführung von „Prüfung“ über dem Sperrbildschirm an und beendet sie. Wirkungslos, wenn die App nicht gesperrt ist.</span><span class="sxs-lookup"><span data-stu-id="0847c-159">**false** stops running Take-a-Test above the lock screen and closes it unless the app is not locked down; in which case there is no effect.</span></span>  
* `onSuccess` <span data-ttu-id="0847c-160">- [optional] Die Funktion, die aufgerufen wird, nachdem der Sperrmodus erfolgreich aktiviert oder deaktiviert wurde.</span><span class="sxs-lookup"><span data-stu-id="0847c-160">- [optional] The function to call after the lockdown has been successfully enabled or disabled.</span></span> <span data-ttu-id="0847c-161">Sie muss im Format `Function(Boolean currentlockdownstate)` vorliegen.</span><span class="sxs-lookup"><span data-stu-id="0847c-161">It must be of the form `Function(Boolean currentlockdownstate)`.</span></span>  
* `onError` <span data-ttu-id="0847c-162">- [optional] Die Funktion, die aufgerufen wird, wenn der Sperrvorgang fehlgeschlagen ist.</span><span class="sxs-lookup"><span data-stu-id="0847c-162">- [optional] The function to call if the lockdown operation failed.</span></span> <span data-ttu-id="0847c-163">Sie muss im Format `Function(Boolean currentlockdownstate)` vorliegen.</span><span class="sxs-lookup"><span data-stu-id="0847c-163">It must be of the form `Function(Boolean currentlockdownstate)`.</span></span>  

**<span data-ttu-id="0847c-164">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="0847c-164">Requirements</span></span>**  
<span data-ttu-id="0847c-165">Windows10, Version1709</span><span class="sxs-lookup"><span data-stu-id="0847c-165">Windows 10, version 1709</span></span>

---

<span id="isEnvironmentSecure" />

### <a name="isenvironmentsecure"></a><span data-ttu-id="0847c-166">isEnvironmentSecure</span><span class="sxs-lookup"><span data-stu-id="0847c-166">isEnvironmentSecure</span></span>
<span data-ttu-id="0847c-167">Stellt fest, ob auf das Gerät noch der Sperrmodus-Kontext angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="0847c-167">Determines whether the lockdown context is still applied to the device.</span></span> <span data-ttu-id="0847c-168">Die Test-Webanwendung ruft diese Funktion auf, bevor Studenten mit dem Testen beginnen dürfen, sowie in regelmäßigen Abständen während des Tests.</span><span class="sxs-lookup"><span data-stu-id="0847c-168">The testing web application will invoke this prior to allowing students to start testing and periodically when inside the test.</span></span>

**<span data-ttu-id="0847c-169">Syntax</span><span class="sxs-lookup"><span data-stu-id="0847c-169">Syntax</span></span>**  
`void SecureBrowser.security.isEnvironmentSecure(Function callback);`

**<span data-ttu-id="0847c-170">Parameter</span><span class="sxs-lookup"><span data-stu-id="0847c-170">Parameters</span></span>**  
* `callback` <span data-ttu-id="0847c-171">- Die Funktion, die aufgerufen wird, wenn diese Funktion abgeschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="0847c-171">- The function to call when this function completes.</span></span> <span data-ttu-id="0847c-172">Sie muss im Format `Function(String state)` vorliegen, wobei `state` eine JSON-Zeichenfolge ist, die zwei Felder enthält.</span><span class="sxs-lookup"><span data-stu-id="0847c-172">It must be of the form `Function(String state)` where `state` is a JSON string containing two fields.</span></span> <span data-ttu-id="0847c-173">Das erste Feld ist `secure`. Dieses Feld zeigt nur dann `true` an, wenn alle erforderlichen Sperren aktiviert (oder Features deaktiviert) wurden, um eine sichere Testumgebung zu ermöglichen, und wenn nichts beschädigt wurde, seitdem die App in den Sperrmodus gewechselt ist.</span><span class="sxs-lookup"><span data-stu-id="0847c-173">The first is the `secure` field, which will show `true` only if all necessary locks have been enabled (or features disabled) to enable a secure testing environment, and none of these have been compromised since the app entered the lockdown mode.</span></span> <span data-ttu-id="0847c-174">Das andere Feld, `messageKey`, enthält weitere anbieterspezifische Details.</span><span class="sxs-lookup"><span data-stu-id="0847c-174">The other field, `messageKey`, includes other details or information that is vendor-specific.</span></span> <span data-ttu-id="0847c-175">Hier können Hersteller zusätzliche Informationen hinterlegen, die das boolesche Kennzeichen `secure` erweitern:</span><span class="sxs-lookup"><span data-stu-id="0847c-175">The intent here is to allow vendors to put additional information that augments the boolean `secure` flag:</span></span>

```JSON
{
    'secure' : "true/false",
    'messageKey' : "some message"
}
```

**<span data-ttu-id="0847c-176">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="0847c-176">Requirements</span></span>**  
<span data-ttu-id="0847c-177">Windows10, Version1709</span><span class="sxs-lookup"><span data-stu-id="0847c-177">Windows 10, version 1709</span></span>

---

<span id="getDeviceInfo" />

### <a name="getdeviceinfo"></a><span data-ttu-id="0847c-178">getDeviceInfo</span><span class="sxs-lookup"><span data-stu-id="0847c-178">getDeviceInfo</span></span>
<span data-ttu-id="0847c-179">Ruft Details zur Plattform ab, auf der die Testanwendung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="0847c-179">Gets details about the platform on which the testing application is running.</span></span> <span data-ttu-id="0847c-180">Wird verwendet, um die Informationen anzureichern, die vom Benutzer-Agent erkennbar waren.</span><span class="sxs-lookup"><span data-stu-id="0847c-180">This is used to augment any information that was discernible from the user agent.</span></span>

**<span data-ttu-id="0847c-181">Syntax</span><span class="sxs-lookup"><span data-stu-id="0847c-181">Syntax</span></span>**  
`void SecureBrowser.security.getDeviceInfo(Function callback);`

**<span data-ttu-id="0847c-182">Parameter</span><span class="sxs-lookup"><span data-stu-id="0847c-182">Parameters</span></span>**  
* `callback` <span data-ttu-id="0847c-183">- Die Funktion, die aufgerufen wird, wenn diese Funktion abgeschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="0847c-183">- The function to call when this function completes.</span></span> <span data-ttu-id="0847c-184">Sie muss im Format `Function(String infoObj)` vorliegen, wobei `infoObj` eine JSON-Zeichenfolge ist, die mehrere Felder enthält.</span><span class="sxs-lookup"><span data-stu-id="0847c-184">It must be of the form `Function(String infoObj)` where `infoObj` is a JSON string containing several fields.</span></span> <span data-ttu-id="0847c-185">Die folgenden Felder müssen unterstützt werden:</span><span class="sxs-lookup"><span data-stu-id="0847c-185">The following fields must be supported:</span></span>
    * `os` <span data-ttu-id="0847c-186">steht für den Typ des Betriebssystems (z.B. Windows, MacOS, Linux, iOS, Android usw.)</span><span class="sxs-lookup"><span data-stu-id="0847c-186">represents the OS type (for example: Windows, macOS, Linux, iOS, Android, etc.)</span></span>
    * `name` <span data-ttu-id="0847c-187">steht für den Namen der Betriebssystemversion, sofern vorhanden (z.B. Sierra, Ubuntu).</span><span class="sxs-lookup"><span data-stu-id="0847c-187">represents the OS release name, if any (for example: Sierra, Ubuntu).</span></span>
    * `version` <span data-ttu-id="0847c-188">steht für die Version des Betriebssystems (z.B. 10.1, 10 Pro usw.).</span><span class="sxs-lookup"><span data-stu-id="0847c-188">represents the OS version (for example: 10.1, 10 Pro, etc.)</span></span>
    * `brand` <span data-ttu-id="0847c-189">steht für das sichere Browser-Branding (z.B. OAKS, CA, SmarterApp usw.).</span><span class="sxs-lookup"><span data-stu-id="0847c-189">represents the secure browser branding (for example: OAKS, CA, SmarterApp, etc.)</span></span>
    * `model` <span data-ttu-id="0847c-190">gibt nur das Gerätemodell für mobile Geräte an; null/nicht verwendet bei Desktopbrowsern.</span><span class="sxs-lookup"><span data-stu-id="0847c-190">represents the device model for mobile devices only; null/unused for desktop browsers.</span></span>

**<span data-ttu-id="0847c-191">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="0847c-191">Requirements</span></span>**  
<span data-ttu-id="0847c-192">Windows10, Version1709</span><span class="sxs-lookup"><span data-stu-id="0847c-192">Windows 10, version 1709</span></span>

---

<span id="examineProcessList" />

### <a name="examineprocesslist"></a><span data-ttu-id="0847c-193">examineProcessList</span><span class="sxs-lookup"><span data-stu-id="0847c-193">examineProcessList</span></span>
<span data-ttu-id="0847c-194">Ruft die Liste aller Prozesse ab, die auf dem Clientcomputer im Besitz des Benutzers ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="0847c-194">Gets the list of all processes running on the client machine owned by the user.</span></span> <span data-ttu-id="0847c-195">Die Testanwendung ruft diese Funktion auf, um die Liste zu überprüfen und mit einer Liste der Prozesse zu vergleichen, die während der Testphase auf die Blacklist gesetzt wurden.</span><span class="sxs-lookup"><span data-stu-id="0847c-195">The testing application will invoke this to examine the list and compare it with a list of processes that have been deemed blacklisted during testing cycle.</span></span> <span data-ttu-id="0847c-196">Dieser Aufruf sollte sowohl zu Beginn einer Prüfung sowie in regelmäßigen Abständen während der Prüfung ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="0847c-196">This call should be invoked both at the start of an assessment and periodically while the student is taking the assessment.</span></span> <span data-ttu-id="0847c-197">Wenn ein Prozess auf der Blacklist erkannt wird, sollte die Prüfung beendet werden, um die Integrität des Tests zu wahren.</span><span class="sxs-lookup"><span data-stu-id="0847c-197">If a blacklisted process is detected, the assessment should be stopped to preserve test integrity.</span></span>

**<span data-ttu-id="0847c-198">Syntax</span><span class="sxs-lookup"><span data-stu-id="0847c-198">Syntax</span></span>**  
`void SecureBrowser.security.examineProcessList(String[] blacklistedProcessList, Function callback);`

**<span data-ttu-id="0847c-199">Parameter</span><span class="sxs-lookup"><span data-stu-id="0847c-199">Parameters</span></span>**  
* `blacklistedProcessList` <span data-ttu-id="0847c-200">- Die Liste der Prozesse, die von der Testanwendung auf die Blacklist gesetzt wurden.</span><span class="sxs-lookup"><span data-stu-id="0847c-200">- The list of processes that the testing application has blacklisted.</span></span>  
`callback` <span data-ttu-id="0847c-201">- Die Funktion, die aufgerufen wird, sobald die aktiven Prozesse gefunden wurden.</span><span class="sxs-lookup"><span data-stu-id="0847c-201">- The function to invoke once the active processes have been found.</span></span> <span data-ttu-id="0847c-202">Sie muss im Format `Function(String foundBlacklistedProcesses)` vorliegen, wobei `foundBlacklistedProcesses` das Format `"['process1.exe','process2.exe','processEtc.exe']"` hat.</span><span class="sxs-lookup"><span data-stu-id="0847c-202">It must be in the form: `Function(String foundBlacklistedProcesses)` where `foundBlacklistedProcesses` is in the form: `"['process1.exe','process2.exe','processEtc.exe']"`.</span></span> <span data-ttu-id="0847c-203">Sie ist leer, wenn keine Prozesse auf der Blacklist gefunden wurden.</span><span class="sxs-lookup"><span data-stu-id="0847c-203">It will be empty if no blacklisted processes were found.</span></span> <span data-ttu-id="0847c-204">Wenn sie null ist, bedeutet dies, dass im ursprünglichen Funktionsaufruf ein Fehler aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="0847c-204">If it is null, this indicates that an error occurred in the original function call.</span></span>

<span data-ttu-id="0847c-205">**Hinweise** Diese Liste enthält keine Systemprozesse.</span><span class="sxs-lookup"><span data-stu-id="0847c-205">**Remarks** The list does not include system processes.</span></span>

**<span data-ttu-id="0847c-206">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="0847c-206">Requirements</span></span>**  
<span data-ttu-id="0847c-207">Windows10, Version1709</span><span class="sxs-lookup"><span data-stu-id="0847c-207">Windows 10, version 1709</span></span>

---

<span id="close"/>

### <a name="close"></a><span data-ttu-id="0847c-208">close</span><span class="sxs-lookup"><span data-stu-id="0847c-208">close</span></span>
<span data-ttu-id="0847c-209">Schließt den Browser und entsperrt das Gerät.</span><span class="sxs-lookup"><span data-stu-id="0847c-209">Closes the browser and unlocks the device.</span></span> <span data-ttu-id="0847c-210">Die Testanwendung sollte diese Funktion aufrufen, wenn der Benutzer beschließt, den Browser zu beenden.</span><span class="sxs-lookup"><span data-stu-id="0847c-210">The testing application should invoke this when the user elects to exit the browser.</span></span>

**<span data-ttu-id="0847c-211">Syntax</span><span class="sxs-lookup"><span data-stu-id="0847c-211">Syntax</span></span>**  
`void SecureBrowser.security.close(restart);`

**<span data-ttu-id="0847c-212">Parameter</span><span class="sxs-lookup"><span data-stu-id="0847c-212">Parameters</span></span>**  
* `restart` <span data-ttu-id="0847c-213">- Dieser Parameter wird ignoriert, muss aber angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="0847c-213">- This parameter is ignored but must be provided.</span></span>

<span data-ttu-id="0847c-214">**Hinweise** In Windows10, Version 1607, muss das Gerät zunächst gesperrt werden.</span><span class="sxs-lookup"><span data-stu-id="0847c-214">**Remarks** In Windows 10, version 1607, the device must be locked down initially.</span></span> <span data-ttu-id="0847c-215">In späteren Versionen schließt diese Methode den Browser unabhängig davon, ob das Gerät gesperrt ist.</span><span class="sxs-lookup"><span data-stu-id="0847c-215">In later versions, this method closes the browser regardless of whether the device is locked down.</span></span>

**<span data-ttu-id="0847c-216">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="0847c-216">Requirements</span></span>**  
<span data-ttu-id="0847c-217">Windows10, Version1709</span><span class="sxs-lookup"><span data-stu-id="0847c-217">Windows 10, version 1709</span></span>

---

<span id="getPermissiveMode" />

### <a name="getpermissivemode"></a><span data-ttu-id="0847c-218">getPermissiveMode</span><span class="sxs-lookup"><span data-stu-id="0847c-218">getPermissiveMode</span></span>
<span data-ttu-id="0847c-219">Die Testanwendung sollte diese Funktion aufrufen, um zu bestimmen, ob der eingeschränkte Modus aktiviert oder deaktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="0847c-219">The testing web application should invoke this to determine if permissive mode is on or off.</span></span> <span data-ttu-id="0847c-220">Im eingeschränkten Modus lockert ein Browser erwartungsgemäß einige seiner strengen Sicherheitregeln, damit Hilfstechnologien mit dem sicheren Browser funktionieren.</span><span class="sxs-lookup"><span data-stu-id="0847c-220">In permissive mode, a browser is expected to relax some of its stringent security hooks to allow assistive technology to work with the secure browser.</span></span> <span data-ttu-id="0847c-221">Browser, die die Benutzeroberflächen anderer Anwendungen strikt daran hindern, über diesen angezeigt zu werden, könnten dieses Verhalten im eingeschränkten Modus lockern.</span><span class="sxs-lookup"><span data-stu-id="0847c-221">For example, browsers that aggressively prevent other application UIs from presenting on top of them might want to relax this when in permissive mode.</span></span> 

**<span data-ttu-id="0847c-222">Syntax</span><span class="sxs-lookup"><span data-stu-id="0847c-222">Syntax</span></span>**  
`void SecureBrowser.security.getPermissiveMode(Function callback)`

**<span data-ttu-id="0847c-223">Parameter</span><span class="sxs-lookup"><span data-stu-id="0847c-223">Parameters</span></span>**  
* `callback` <span data-ttu-id="0847c-224">- Die Funktion, die aufgerufen wird, wenn dieser Aufruf abgeschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="0847c-224">- The function to invoke when this call completes.</span></span> <span data-ttu-id="0847c-225">Sie muss im Format `Function(Boolean permissiveMode)` vorliegen, wobei `permissiveMode` angibt, ob für den Browser aktuell der eingeschränkte Modus aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="0847c-225">It must be in the form: `Function(Boolean permissiveMode)` where `permissiveMode` indicates whether the browser is currently in permissive mode.</span></span> <span data-ttu-id="0847c-226">Wenn sie nicht definiert oder null ist, ist beim GET-Vorgang ein Fehler aufgetreten.</span><span class="sxs-lookup"><span data-stu-id="0847c-226">If it is undefined or null, an error occurred in the get operation.</span></span>

**<span data-ttu-id="0847c-227">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="0847c-227">Requirements</span></span>**  
<span data-ttu-id="0847c-228">Windows10, Version1709</span><span class="sxs-lookup"><span data-stu-id="0847c-228">Windows 10, version 1709</span></span>

---

<span id="setPermissiveMode" />

### <a name="setpermissivemode"></a><span data-ttu-id="0847c-229">setPermissiveMode</span><span class="sxs-lookup"><span data-stu-id="0847c-229">setPermissiveMode</span></span>
<span data-ttu-id="0847c-230">Die Testanwendung sollte diese Funktion aufrufen, um den eingeschränkten Modus zu aktivieren oder zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="0847c-230">The testing web application should invoke this to toggle permissive mode on or off.</span></span> <span data-ttu-id="0847c-231">Im eingeschränkten Modus lockert ein Browser erwartungsgemäß einige seiner strengen Sicherheitregeln, damit Hilfstechnologien mit dem sicheren Browser funktionieren.</span><span class="sxs-lookup"><span data-stu-id="0847c-231">In permissive mode, a browser is expected to relax some of its stringent security hooks to allow assistive technology to work with the secure browser.</span></span> <span data-ttu-id="0847c-232">Browser, die die Benutzeroberflächen anderer Anwendungen strikt daran hindern, über diesen angezeigt zu werden, könnten dieses Verhalten im eingeschränkten Modus lockern.</span><span class="sxs-lookup"><span data-stu-id="0847c-232">For example, browsers that aggressively prevent other application UIs from presenting on top of them might want to relax this when in permissive mode.</span></span> 

**<span data-ttu-id="0847c-233">Syntax</span><span class="sxs-lookup"><span data-stu-id="0847c-233">Syntax</span></span>**  
`void SecureBrowser.security.setPermissiveMode(Boolean enable, Function callback)`

**<span data-ttu-id="0847c-234">Parameter</span><span class="sxs-lookup"><span data-stu-id="0847c-234">Parameters</span></span>**  
* `enable` <span data-ttu-id="0847c-235">– Der boolesche Wert, der den Status des vorgesehenen eingeschränkten Modus angibt.</span><span class="sxs-lookup"><span data-stu-id="0847c-235">- The Boolean value indicating the intended permissive mode status.</span></span>  
* `callback` <span data-ttu-id="0847c-236">- Die Funktion, die aufgerufen wird, wenn dieser Aufruf abgeschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="0847c-236">- The function to invoke when this call completes.</span></span> <span data-ttu-id="0847c-237">Sie muss im Format `Function(Boolean permissiveMode)` vorliegen, wobei `permissiveMode` angibt, ob für den Browser aktuell der eingeschränkte Modus aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="0847c-237">It must be in the form: `Function(Boolean permissiveMode)` where `permissiveMode` indicates whether the browser is currently in permissive mode.</span></span> <span data-ttu-id="0847c-238">Wenn sie nicht definiert oder null ist, ist beim SET-Vorgang ein Fehler aufgetreten.</span><span class="sxs-lookup"><span data-stu-id="0847c-238">If it is undefined or null, an error occurred in the set operation.</span></span>

**<span data-ttu-id="0847c-239">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="0847c-239">Requirements</span></span>**  
<span data-ttu-id="0847c-240">Windows10, Version1709</span><span class="sxs-lookup"><span data-stu-id="0847c-240">Windows 10, version 1709</span></span>

---

<span id="emptyClipBoard"/>

### <a name="emptyclipboard"></a><span data-ttu-id="0847c-241">emptyClipBoard</span><span class="sxs-lookup"><span data-stu-id="0847c-241">emptyClipBoard</span></span>
<span data-ttu-id="0847c-242">Löscht die Zwischenablage des Systems.</span><span class="sxs-lookup"><span data-stu-id="0847c-242">Clears the system clipboard.</span></span> <span data-ttu-id="0847c-243">Die Testanwendung sollte diese Funktion aufrufen, um zu erzwingen, dass alle Daten gelöscht werden, die unter Umständen in der Zwischenablage des Systems gespeichert sind.</span><span class="sxs-lookup"><span data-stu-id="0847c-243">The testing application should invoke this to force clear any data that may be stored in the system clipboard.</span></span> <span data-ttu-id="0847c-244">Dieser Vorgang wird auch von der Funktion **[lockDown](#lockDown)** ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="0847c-244">The **[lockDown](#lockDown)** function also performs this operation.</span></span>

**<span data-ttu-id="0847c-245">Syntax</span><span class="sxs-lookup"><span data-stu-id="0847c-245">Syntax</span></span>**  
`void SecureBrowser.security.emptyClipBoard();`

**<span data-ttu-id="0847c-246">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="0847c-246">Requirements</span></span>**  
<span data-ttu-id="0847c-247">Windows10, Version1709</span><span class="sxs-lookup"><span data-stu-id="0847c-247">Windows 10, version 1709</span></span>

---

<span id="getMACAddress" />

### <a name="getmacaddress"></a><span data-ttu-id="0847c-248">getMACAddress</span><span class="sxs-lookup"><span data-stu-id="0847c-248">getMACAddress</span></span>
<span data-ttu-id="0847c-249">Ruft die Liste der MAC-Adressen für das Gerät ab.</span><span class="sxs-lookup"><span data-stu-id="0847c-249">Gets the list of MAC addresses for the device.</span></span> <span data-ttu-id="0847c-250">Die Testanwendung sollte diese Funktion aufrufen, um Unterstützung bei der Diagnose zu bieten.</span><span class="sxs-lookup"><span data-stu-id="0847c-250">The testing application should invoke this to assist in diagnostics.</span></span> 

**<span data-ttu-id="0847c-251">Syntax</span><span class="sxs-lookup"><span data-stu-id="0847c-251">Syntax</span></span>**  
`void SecureBrowser.security.getMACAddress(Function callback);`

**<span data-ttu-id="0847c-252">Parameter</span><span class="sxs-lookup"><span data-stu-id="0847c-252">Parameters</span></span>**  
* `callback` <span data-ttu-id="0847c-253">- Die Funktion, die aufgerufen wird, wenn dieser Aufruf abgeschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="0847c-253">- The function to invoke when this call completes.</span></span> <span data-ttu-id="0847c-254">Sie muss im Format `Function(String addressArray)` vorliegen, wobei `addressArray` das Format `"['00:11:22:33:44:55','etc']"` hat.</span><span class="sxs-lookup"><span data-stu-id="0847c-254">It must be in the form: `Function(String addressArray)` where `addressArray` is in the form: `"['00:11:22:33:44:55','etc']"`.</span></span>

**<span data-ttu-id="0847c-255">Hinweise</span><span class="sxs-lookup"><span data-stu-id="0847c-255">Remarks</span></span>**  
<span data-ttu-id="0847c-256">Es ist schwierig, sich bei der Unterscheidung zwischen den Endnutzercomputern innerhalb der Testserver auf die Quell-IP-Adressen zu verlassen, da in Schulen für gewöhnlich Firewalls/NATs/Proxys verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="0847c-256">It is difficult to rely on source IP addresses to distinguish between end user machines within the testing servers because firewalls/NATs/Proxies are commonly in use at the schools.</span></span> <span data-ttu-id="0847c-257">Anhand der MAC-Adressen kann die App für Diagnosezwecke zwischen den Endbenutzercomputern hinter einer gängigen Firewall unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="0847c-257">The MAC addresses allow the app to distinguish end client machines behind a common firewall for diagnostics purposes.</span></span>

**<span data-ttu-id="0847c-258">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="0847c-258">Requirements</span></span>**  
<span data-ttu-id="0847c-259">Windows10, Version1709</span><span class="sxs-lookup"><span data-stu-id="0847c-259">Windows 10, version 1709</span></span>

---

<span id="getStartTime" />

### <a name="getstarttime"></a><span data-ttu-id="0847c-260">getStartTime</span><span class="sxs-lookup"><span data-stu-id="0847c-260">getStartTime</span></span>
<span data-ttu-id="0847c-261">Ruft die Zeit ab, zu der die Test-App gestartet wurde.</span><span class="sxs-lookup"><span data-stu-id="0847c-261">Gets the time that the testing app was started.</span></span>

**<span data-ttu-id="0847c-262">Syntax</span><span class="sxs-lookup"><span data-stu-id="0847c-262">Syntax</span></span>**  
`DateTime SecureBrowser.settings.getStartTime();`

**<span data-ttu-id="0847c-263">Rückgabe</span><span class="sxs-lookup"><span data-stu-id="0847c-263">Return</span></span>**  
<span data-ttu-id="0847c-264">Ein DateTime-Objekt, das den Zeitpunkt angibt, zu dem die Test-App gestartet wurde.</span><span class="sxs-lookup"><span data-stu-id="0847c-264">A DateTime object indicating the time the testing app was started.</span></span>

**<span data-ttu-id="0847c-265">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="0847c-265">Requirements</span></span>**  
<span data-ttu-id="0847c-266">Windows10, Version1709</span><span class="sxs-lookup"><span data-stu-id="0847c-266">Windows 10, version 1709</span></span>

---

<span id="getCapability"/>

### <a name="getcapability"></a><span data-ttu-id="0847c-267">getCapability</span><span class="sxs-lookup"><span data-stu-id="0847c-267">getCapability</span></span>
<span data-ttu-id="0847c-268">Fragt ab, ob eine Funktion aktiviert oder deaktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="0847c-268">Queries whether a capability is enabled or disabled.</span></span> 

**<span data-ttu-id="0847c-269">Syntax</span><span class="sxs-lookup"><span data-stu-id="0847c-269">Syntax</span></span>**  
`Object SecureBrowser.security.getCapability(String feature)`

**<span data-ttu-id="0847c-270">Parameter</span><span class="sxs-lookup"><span data-stu-id="0847c-270">Parameters</span></span>**  
`feature` <span data-ttu-id="0847c-271">- Die Zeichenfolge, die festlegt, welche Funktion abgefragt werden soll.</span><span class="sxs-lookup"><span data-stu-id="0847c-271">- The string to determine which capability to query.</span></span> <span data-ttu-id="0847c-272">Gültige Funktionszeichenfolgen sind „screenMonitoring“, „printing“ und „textSuggestions“ (Groß-/Kleinschreibung spielt keine Rolle).</span><span class="sxs-lookup"><span data-stu-id="0847c-272">Valid capability strings are "screenMonitoring", "printing", and "textSuggestions" (case insensitive).</span></span>

**<span data-ttu-id="0847c-273">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="0847c-273">Return Value</span></span>**  
<span data-ttu-id="0847c-274">Diese Funktion gibt ein JavaScript-Objekt oder Literalzeichen im folgenden Format zurück: `{<feature>:true|false}`.</span><span class="sxs-lookup"><span data-stu-id="0847c-274">This function returns either a JavaScript Object or literal with the form: `{<feature>:true|false}`.</span></span> <span data-ttu-id="0847c-275">**true**, wenn die abgefragte Funktion aktiviert ist, **false**, wenn die Funktion nicht aktiviert oder die Funktionszeichenfolge ungültig ist.</span><span class="sxs-lookup"><span data-stu-id="0847c-275">**true** if the queried capability is enabled, **false** if the capability is not enabled or the capability string is invalid.</span></span>

<span data-ttu-id="0847c-276">**Anforderungen** Windows10, Version 1703</span><span class="sxs-lookup"><span data-stu-id="0847c-276">**Requirements** Windows 10, version 1703</span></span>

---

<span id="setCapability"/>

### <a name="setcapability"></a><span data-ttu-id="0847c-277">setCapability</span><span class="sxs-lookup"><span data-stu-id="0847c-277">setCapability</span></span>
<span data-ttu-id="0847c-278">Aktiviert oder deaktiviert eine bestimmte Funktion des Browsers.</span><span class="sxs-lookup"><span data-stu-id="0847c-278">Enables or disables a specific capability on the browser.</span></span>

**<span data-ttu-id="0847c-279">Syntax</span><span class="sxs-lookup"><span data-stu-id="0847c-279">Syntax</span></span>**  
`void SecureBrowser.security.setCapability(String feature, String value, Function onSuccess, Function onError)`

**<span data-ttu-id="0847c-280">Parameter</span><span class="sxs-lookup"><span data-stu-id="0847c-280">Parameters</span></span>**  
* `feature` <span data-ttu-id="0847c-281">- Die Zeichenfolge, mit der bestimmt wird, welche Funktion festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="0847c-281">- The string to determine which capability to set.</span></span> <span data-ttu-id="0847c-282">Gültige Funktionszeichenfolgen sind `"screenMonitoring"`, `"printing"` und `"textSuggestions"` (Groß-/Kleinschreibung spielt keine Rolle).</span><span class="sxs-lookup"><span data-stu-id="0847c-282">Valid capability strings are `"screenMonitoring"`, `"printing"`, and `"textSuggestions"` (case insensitive).</span></span>  
* `value` <span data-ttu-id="0847c-283">– Die gewünschte Einstellung für das Feature.</span><span class="sxs-lookup"><span data-stu-id="0847c-283">- The intended setting for the feature.</span></span> <span data-ttu-id="0847c-284">Muss entweder `"true"` oder `"false"` sein.</span><span class="sxs-lookup"><span data-stu-id="0847c-284">It must be either `"true"` or `"false"`.</span></span>  
* `onSuccess` <span data-ttu-id="0847c-285">- [optional] Die Funktion, die aufgerufen wird, nachdem der SET-Vorgang erfolgreich abgeschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="0847c-285">- [optional] The function to call after the set operation has been completed successfully.</span></span> <span data-ttu-id="0847c-286">Sie muss im Format `Function(String jsonValue)` vorliegen, wobei *jsonValue* das Format `{<feature>:true|false|undefined}` hat.</span><span class="sxs-lookup"><span data-stu-id="0847c-286">It must be of the form `Function(String jsonValue)` where *jsonValue* is in the form: `{<feature>:true|false|undefined}`.</span></span>  
* `onError` <span data-ttu-id="0847c-287">- [optional] Die Funktion, die aufgerufen wird, wenn der SET-Vorgang fehlgeschlagen ist.</span><span class="sxs-lookup"><span data-stu-id="0847c-287">- [optional] The function to call if the set operation failed.</span></span> <span data-ttu-id="0847c-288">Sie muss im Format `Function(String jsonValue)` vorliegen, wobei *jsonValue* das Format `{<feature>:true|false|undefined}` hat.</span><span class="sxs-lookup"><span data-stu-id="0847c-288">It must be of the form `Function(String jsonValue)` where *jsonValue* is in the form: `{<feature>:true|false|undefined}`.</span></span>

**<span data-ttu-id="0847c-289">Hinweise</span><span class="sxs-lookup"><span data-stu-id="0847c-289">Remarks</span></span>**  
<span data-ttu-id="0847c-290">Wenn die Zielfunktion dem Browser nicht bekannt ist, übergibt diese Funktion den Wert `undefined` an die Rückruffunktion.</span><span class="sxs-lookup"><span data-stu-id="0847c-290">If the targeted feature is unknown to the browser, this function will pass a value of `undefined` to the callback function.</span></span>

<span data-ttu-id="0847c-291">**Anforderungen** Windows10, Version 1703</span><span class="sxs-lookup"><span data-stu-id="0847c-291">**Requirements** Windows 10, version 1703</span></span>

---

<span id="isRemoteSession"/>

### <a name="isremotesession"></a><span data-ttu-id="0847c-292">isRemoteSession</span><span class="sxs-lookup"><span data-stu-id="0847c-292">isRemoteSession</span></span>
<span data-ttu-id="0847c-293">Überprüft, ob die aktuelle Sitzung remote angemeldet ist.</span><span class="sxs-lookup"><span data-stu-id="0847c-293">Checks if the current session is logged in remotely.</span></span>

**<span data-ttu-id="0847c-294">Syntax</span><span class="sxs-lookup"><span data-stu-id="0847c-294">Syntax</span></span>**  
`Boolean SecureBrowser.security.isRemoteSession();`

**<span data-ttu-id="0847c-295">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="0847c-295">Return value</span></span>**  
<span data-ttu-id="0847c-296">**true**, wenn es sich bei der aktuellen Sitzung um eine Remotesitzung handelt, andernfalls **false**.</span><span class="sxs-lookup"><span data-stu-id="0847c-296">**true** if the current session is remote, otherwise **false**.</span></span>

**<span data-ttu-id="0847c-297">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="0847c-297">Requirements</span></span>**  
<span data-ttu-id="0847c-298">Windows10, Version1709</span><span class="sxs-lookup"><span data-stu-id="0847c-298">Windows 10, version 1709</span></span>

---

<span id="isVMSession"/>

### <a name="isvmsession"></a><span data-ttu-id="0847c-299">isVMSession</span><span class="sxs-lookup"><span data-stu-id="0847c-299">isVMSession</span></span>
<span data-ttu-id="0847c-300">Überprüft, ob die aktuelle Sitzung auf einem virtuellen Computer ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="0847c-300">Checks if the current session is running within a virtual machine.</span></span>

**<span data-ttu-id="0847c-301">Syntax</span><span class="sxs-lookup"><span data-stu-id="0847c-301">Syntax</span></span>**  
`Boolean SecureBrowser.security.isVMSession();`

**<span data-ttu-id="0847c-302">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="0847c-302">Return value</span></span>**  
<span data-ttu-id="0847c-303">**true**, wenn die aktuelle Sitzung auf einem virtuellen Computer ausgeführt wird, andernfalls **false**.</span><span class="sxs-lookup"><span data-stu-id="0847c-303">**true** if the current session is running in a virtual machine, otherwise **false**.</span></span>

**<span data-ttu-id="0847c-304">Hinweise</span><span class="sxs-lookup"><span data-stu-id="0847c-304">Remarks</span></span>**  
<span data-ttu-id="0847c-305">Diese API-Prüfung erkennt nur VM Sitzungen, die in bestimmten Hypervisoren ausgeführt werden, die die entsprechenden APIs implementieren.</span><span class="sxs-lookup"><span data-stu-id="0847c-305">This API check can only detect VM sessions that are running in certain hypervisors that implement the appropriate APIs</span></span>

**<span data-ttu-id="0847c-306">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="0847c-306">Requirements</span></span>**  
<span data-ttu-id="0847c-307">Windows10, Version1709</span><span class="sxs-lookup"><span data-stu-id="0847c-307">Windows 10, version 1709</span></span>

---