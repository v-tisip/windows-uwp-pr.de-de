---
Description: The JavaScript API for the Microsoft Take a Test app allows you to do secure assessments. Take a Test provides a secure browser that prevents students from using other computer or internet resources during a test.
title: JavaScript-API „Prüfung”
author: PatrickFarley
ms.author: pafarley
ms.assetid: 9bff6318-504c-4d0e-ba80-1a5ea45743da
ms.date: 08/08/2018
ms.topic: article
keywords: Windows 10, Uwp, education
ms.localizationpriority: medium
ms.openlocfilehash: d64901c08e2945f34e66055d8e2e7d3a8301f66e
ms.sourcegitcommit: 144f5f127fc4fbd852f2f6780ef26054192d68fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5982842"
---
# <a name="take-a-test-javascript-api"></a><span data-ttu-id="c179f-103">JavaScript-API „Prüfung”</span><span class="sxs-lookup"><span data-stu-id="c179f-103">Take a Test JavaScript API</span></span>

<span data-ttu-id="c179f-104">[Prüfung](https://technet.microsoft.com/edu/windows/take-tests-in-windows-10) ist eine Browser-basierte UWP-app, die gesperrte onlinebewertungen für wichtige Prüfungen rendert, rendert die Dozenten auf den Prüfungsinhalt konzentrieren, wodurch Content kann anstatt auf eine sichere testumgebung zu bieten.</span><span class="sxs-lookup"><span data-stu-id="c179f-104">[Take a Test](https://technet.microsoft.com/edu/windows/take-tests-in-windows-10) is a browser-based UWP app that renders locked-down online assessments for high-stakes testing, allowing educators to focus on the assessment content rather than how to provide a secure testing environment.</span></span> <span data-ttu-id="c179f-105">Um dies zu erreichen, wird eine JavaScript-API verwendet, die von jeder Web-Anwendung genutzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="c179f-105">To achieve this, it uses a JavaScript API that any web application can utilize.</span></span> <span data-ttu-id="c179f-106">Die API „Prüfung“ unterstützt den [Browser-API-Standard SBAC](http://www.smarterapp.org/documents/SecureBrowserRequirementsSpecifications_0-3.pdf) zur Durchführung wichtiger allgemeiner Kernprüfungen.</span><span class="sxs-lookup"><span data-stu-id="c179f-106">The Take-a-test API supports the [SBAC browser API standard](http://www.smarterapp.org/documents/SecureBrowserRequirementsSpecifications_0-3.pdf) for high stakes common core testing.</span></span>

<span data-ttu-id="c179f-107">Weitere Informationen zur App selbst finden Sie unter [Technische Referenz zur App „Prüfung“](https://technet.microsoft.com/edu/windows/take-a-test-app-technical?f=255&MSPPError=-2147217396).</span><span class="sxs-lookup"><span data-stu-id="c179f-107">See the [Take a Test app technical reference](https://technet.microsoft.com/edu/windows/take-a-test-app-technical?f=255&MSPPError=-2147217396) for more information about the app itself.</span></span> <span data-ttu-id="c179f-108">Hilfe zur Problembehandlung finden Sie unter [Problembehandlung bei Microsoft Prüfung mithilfe der Ereignisanzeige](troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="c179f-108">For troubleshooting help, see [Troubleshoot Microsoft Take a Test with the event viewer](troubleshooting.md).</span></span>

## <a name="reference-documentation"></a><span data-ttu-id="c179f-109">Referenzdokumentation</span><span class="sxs-lookup"><span data-stu-id="c179f-109">Reference documentation</span></span>
<span data-ttu-id="c179f-110">Die Prüfungs-APIs gibt es in den folgenden Namespaces.</span><span class="sxs-lookup"><span data-stu-id="c179f-110">The Take a Test APIs exist in the following namespaces.</span></span> <span data-ttu-id="c179f-111">Beachten Sie, dass alle APIs von einem globalen `SecureBrowser`-Objekt abhängen.</span><span class="sxs-lookup"><span data-stu-id="c179f-111">Note that all of the APIs depend on a global `SecureBrowser` object.</span></span>

| <span data-ttu-id="c179f-112">Namespace</span><span class="sxs-lookup"><span data-stu-id="c179f-112">Namespace</span></span> | <span data-ttu-id="c179f-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c179f-113">Description</span></span> |
|-----------|-------------|
|[<span data-ttu-id="c179f-114">Sicherheitsnamespace</span><span class="sxs-lookup"><span data-stu-id="c179f-114">security namespace</span></span>](#security-namespace)|<span data-ttu-id="c179f-115">Enthält APIs, mit denen Sie das Gerät zu Testzwecken sperren und eine Testumgebung erzwingen können.</span><span class="sxs-lookup"><span data-stu-id="c179f-115">Contains APIs that enable you to lock down the device for testing and enforce a testing environment.</span></span> |

### <a name="security-namespace"></a><span data-ttu-id="c179f-116">Sicherheitsnamespace</span><span class="sxs-lookup"><span data-stu-id="c179f-116">Security namespace</span></span>

<span data-ttu-id="c179f-117">Der sicherheitsnamespace können Sie das Gerät sperren, überprüfen Sie die Liste der Benutzer- und Systemprozesse, Abrufen von Mac- und IP-Adressen und Löschen von zwischengespeicherten Webressourcen.</span><span class="sxs-lookup"><span data-stu-id="c179f-117">The security namespace allows you to lock down the device, check the list of user and system processes, obtain MAC and IP addresses, and clear cached web resources.</span></span>

| <span data-ttu-id="c179f-118">Methode</span><span class="sxs-lookup"><span data-stu-id="c179f-118">Method</span></span> | <span data-ttu-id="c179f-119">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c179f-119">Description</span></span>   |
|--------|---------------|
|[<span data-ttu-id="c179f-120">lockDown</span><span class="sxs-lookup"><span data-stu-id="c179f-120">lockDown</span></span>](#lockDown) | <span data-ttu-id="c179f-121">Sperrt das Gerät für Testzwecke.</span><span class="sxs-lookup"><span data-stu-id="c179f-121">Locks down the device for testing.</span></span> |
|[<span data-ttu-id="c179f-122">isEnvironmentSecure</span><span class="sxs-lookup"><span data-stu-id="c179f-122">isEnvironmentSecure</span></span>](#isEnvironmentSecure) | <span data-ttu-id="c179f-123">Stellt fest, ob auf das Gerät noch der Sperrmodus-Kontext angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="c179f-123">Determines whether the lockdown context is still applied to the device.</span></span> |
|[<span data-ttu-id="c179f-124">getDeviceInfo</span><span class="sxs-lookup"><span data-stu-id="c179f-124">getDeviceInfo</span></span>](#getDeviceInfo) | <span data-ttu-id="c179f-125">Ruft Details zur Plattform ab, auf der die Testanwendung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c179f-125">Gets details about the platform on which the testing application is running.</span></span> |
|[<span data-ttu-id="c179f-126">examineProcessList</span><span class="sxs-lookup"><span data-stu-id="c179f-126">examineProcessList</span></span>](#examineProcessList)|<span data-ttu-id="c179f-127">Ruft die Liste der ausgeführten Benutzer- und Systemprozesse ab.</span><span class="sxs-lookup"><span data-stu-id="c179f-127">Gets the list of running user and system processes.</span></span>|
|[<span data-ttu-id="c179f-128">close</span><span class="sxs-lookup"><span data-stu-id="c179f-128">close</span></span>](#close) | <span data-ttu-id="c179f-129">Schließt den Browser und entsperrt das Gerät.</span><span class="sxs-lookup"><span data-stu-id="c179f-129">Closes the browser and unlocks the device.</span></span> |
|[<span data-ttu-id="c179f-130">getPermissiveMode</span><span class="sxs-lookup"><span data-stu-id="c179f-130">getPermissiveMode</span></span>](#getPermissiveMode)|<span data-ttu-id="c179f-131">Überprüft, ob der eingeschränkte Modus aktiviert oder deaktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="c179f-131">Checks if permissive mode is on or off.</span></span>|
|[<span data-ttu-id="c179f-132">setPermissiveMode</span><span class="sxs-lookup"><span data-stu-id="c179f-132">setPermissiveMode</span></span>](#setPermissiveMode)|<span data-ttu-id="c179f-133">Schaltet den eingeschränkten Modus ein oder aus.</span><span class="sxs-lookup"><span data-stu-id="c179f-133">Toggles permissive mode on or off.</span></span>|
|[<span data-ttu-id="c179f-134">emptyClipBoard</span><span class="sxs-lookup"><span data-stu-id="c179f-134">emptyClipBoard</span></span>](#emptyClipBoard)|<span data-ttu-id="c179f-135">Löscht die Zwischenablage des Systems.</span><span class="sxs-lookup"><span data-stu-id="c179f-135">Clears the system clipboard.</span></span>|
|[<span data-ttu-id="c179f-136">getMACAddress</span><span class="sxs-lookup"><span data-stu-id="c179f-136">getMACAddress</span></span>](#getMACAddress)|<span data-ttu-id="c179f-137">Ruft die Liste der MAC-Adressen für das Gerät ab.</span><span class="sxs-lookup"><span data-stu-id="c179f-137">Gets the list of MAC addresses for the device.</span></span>|
|[<span data-ttu-id="c179f-138">getStartTime</span><span class="sxs-lookup"><span data-stu-id="c179f-138">getStartTime</span></span>](#getStartTime) | <span data-ttu-id="c179f-139">Ruft die Zeit ab, zu der die Test-App gestartet wurde.</span><span class="sxs-lookup"><span data-stu-id="c179f-139">Gets the time that the testing app was started.</span></span> |
|[<span data-ttu-id="c179f-140">getCapability</span><span class="sxs-lookup"><span data-stu-id="c179f-140">getCapability</span></span>](#getCapability) | <span data-ttu-id="c179f-141">Fragt ab, ob eine Funktion aktiviert oder deaktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="c179f-141">Queries whether a capability is enabled or disabled.</span></span> |
|[<span data-ttu-id="c179f-142">setCapability</span><span class="sxs-lookup"><span data-stu-id="c179f-142">setCapability</span></span>](#setCapability)|<span data-ttu-id="c179f-143">Aktiviert oder deaktiviert die angegebene Funktion.</span><span class="sxs-lookup"><span data-stu-id="c179f-143">Enables or disables the specified capability.</span></span>| 
|[<span data-ttu-id="c179f-144">isRemoteSession</span><span class="sxs-lookup"><span data-stu-id="c179f-144">isRemoteSession</span></span>](#isRemoteSession) | <span data-ttu-id="c179f-145">Überprüft, ob die aktuelle Sitzung remote angemeldet ist.</span><span class="sxs-lookup"><span data-stu-id="c179f-145">Checks if the current session is logged in remotely.</span></span> |
|[<span data-ttu-id="c179f-146">isVMSession</span><span class="sxs-lookup"><span data-stu-id="c179f-146">isVMSession</span></span>](#isVMSession) | <span data-ttu-id="c179f-147">Überprüft, ob die aktuelle Sitzung auf einem virtuellen Computer ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c179f-147">Checks if the current session is running in a virtual machine.</span></span> |

---

<span id="lockDown"/>

### <a name="lockdown"></a><span data-ttu-id="c179f-148">lockDown</span><span class="sxs-lookup"><span data-stu-id="c179f-148">lockDown</span></span>
<span data-ttu-id="c179f-149">Sperrt das Gerät.</span><span class="sxs-lookup"><span data-stu-id="c179f-149">Locks down the device.</span></span> <span data-ttu-id="c179f-150">Wird auch zum Entsperren des Geräts verwendet.</span><span class="sxs-lookup"><span data-stu-id="c179f-150">Also used to unlock the device.</span></span> <span data-ttu-id="c179f-151">Die Test-Webanwendung führt diesen Aufruf aus, bevor Studenten mit dem Testen beginnen dürfen.</span><span class="sxs-lookup"><span data-stu-id="c179f-151">The testing web application will invoke this call prior to allowing students to start testing.</span></span> <span data-ttu-id="c179f-152">Der Implementierer ist erforderlich, um alle notwendigen Aktionen zum Schutz der Testumgebung durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="c179f-152">The implementer is required to take any actions necessary to secure the testing environment.</span></span> <span data-ttu-id="c179f-153">Die Schritte zum Schutz der Umgebung sind gerätespezifisch und beinhalten Aspekte wie z.B. das Deaktivieren von Bildschirmaufnahmen, das Deaktivieren des Sprachchats im sicheren Modus, das Löschen der Zwischenablage des Systems, das Wechseln zu einem Kioskmodus, das Deaktivieren von Leerzeichen in OSX10.7+-Geräten usw. Die Testanwendung aktiviert den Sperrmodus, bevor eine Prüfung beginnt, und deaktiviert den Sperrmodus wieder, wenn der Student die Prüfung abgeschlossen und den sicheren Test verlassen hat.</span><span class="sxs-lookup"><span data-stu-id="c179f-153">The steps taken to secure the environment are device specific and for example, include aspects such as disabling screen captures, disabling voice chat when in secure mode, clearing the system clipboard, entering into a kiosk mode, disabling Spaces in OSX 10.7+ devices, etc. The testing application will enable lockdown before an assessment commences and will disable the lockdown when the student has completed the assessment and is out of the secure test.</span></span>

**<span data-ttu-id="c179f-154">Syntax</span><span class="sxs-lookup"><span data-stu-id="c179f-154">Syntax</span></span>**  
`void SecureBrowser.security.lockDown(Boolean enable, Function onSuccess, Function onError);`

**<span data-ttu-id="c179f-155">Parameter</span><span class="sxs-lookup"><span data-stu-id="c179f-155">Parameters</span></span>**  
* `enable`<span data-ttu-id="c179f-156"> - *\*true*\*, wenn die App „Prüfung“ über dem Sperrbildschirm ausgeführt werden soll und die in diesem [Dokument](https://technet.microsoft.com/edu/windows/take-a-test-app-technical?f=255&MSPPError=-2147217396) behandelten Richtlinien angewendet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="c179f-156"> - *\*true** to run the Take-a-Test app above the lock screen and apply policies discussed in this [document](https://technet.microsoft.com/edu/windows/take-a-test-app-technical?f=255&MSPPError=-2147217396).</span></span> <span data-ttu-id="c179f-157">**false** hält die Ausführung von „Prüfung“ über dem Sperrbildschirm an und beendet sie. Wirkungslos, wenn die App nicht gesperrt ist.</span><span class="sxs-lookup"><span data-stu-id="c179f-157">**false** stops running Take-a-Test above the lock screen and closes it unless the app is not locked down; in which case there is no effect.</span></span>  
* `onSuccess` <span data-ttu-id="c179f-158">- [optional] Die Funktion, die aufgerufen wird, nachdem der Sperrmodus erfolgreich aktiviert oder deaktiviert wurde.</span><span class="sxs-lookup"><span data-stu-id="c179f-158">- [optional] The function to call after the lockdown has been successfully enabled or disabled.</span></span> <span data-ttu-id="c179f-159">Sie muss im Format `Function(Boolean currentlockdownstate)` vorliegen.</span><span class="sxs-lookup"><span data-stu-id="c179f-159">It must be of the form `Function(Boolean currentlockdownstate)`.</span></span>  
* `onError` <span data-ttu-id="c179f-160">- [optional] Die Funktion, die aufgerufen wird, wenn der Sperrvorgang fehlgeschlagen ist.</span><span class="sxs-lookup"><span data-stu-id="c179f-160">- [optional] The function to call if the lockdown operation failed.</span></span> <span data-ttu-id="c179f-161">Sie muss im Format `Function(Boolean currentlockdownstate)` vorliegen.</span><span class="sxs-lookup"><span data-stu-id="c179f-161">It must be of the form `Function(Boolean currentlockdownstate)`.</span></span>  

**<span data-ttu-id="c179f-162">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="c179f-162">Requirements</span></span>**  
<span data-ttu-id="c179f-163">Windows10, Version1709</span><span class="sxs-lookup"><span data-stu-id="c179f-163">Windows 10, version 1709</span></span>

---

<span id="isEnvironmentSecure" />

### <a name="isenvironmentsecure"></a><span data-ttu-id="c179f-164">isEnvironmentSecure</span><span class="sxs-lookup"><span data-stu-id="c179f-164">isEnvironmentSecure</span></span>
<span data-ttu-id="c179f-165">Stellt fest, ob auf das Gerät noch der Sperrmodus-Kontext angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="c179f-165">Determines whether the lockdown context is still applied to the device.</span></span> <span data-ttu-id="c179f-166">Die Test-Webanwendung ruft diese Funktion auf, bevor Studenten mit dem Testen beginnen dürfen, sowie in regelmäßigen Abständen während des Tests.</span><span class="sxs-lookup"><span data-stu-id="c179f-166">The testing web application will invoke this prior to allowing students to start testing and periodically when inside the test.</span></span>

**<span data-ttu-id="c179f-167">Syntax</span><span class="sxs-lookup"><span data-stu-id="c179f-167">Syntax</span></span>**  
`void SecureBrowser.security.isEnvironmentSecure(Function callback);`

**<span data-ttu-id="c179f-168">Parameter</span><span class="sxs-lookup"><span data-stu-id="c179f-168">Parameters</span></span>**  
* `callback` <span data-ttu-id="c179f-169">- Die Funktion, die aufgerufen wird, wenn diese Funktion abgeschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="c179f-169">- The function to call when this function completes.</span></span> <span data-ttu-id="c179f-170">Sie muss im Format `Function(String state)` vorliegen, wobei `state` eine JSON-Zeichenfolge ist, die zwei Felder enthält.</span><span class="sxs-lookup"><span data-stu-id="c179f-170">It must be of the form `Function(String state)` where `state` is a JSON string containing two fields.</span></span> <span data-ttu-id="c179f-171">Das erste Feld ist `secure`. Dieses Feld zeigt nur dann `true` an, wenn alle erforderlichen Sperren aktiviert (oder Features deaktiviert) wurden, um eine sichere Testumgebung zu ermöglichen, und wenn nichts beschädigt wurde, seitdem die App in den Sperrmodus gewechselt ist.</span><span class="sxs-lookup"><span data-stu-id="c179f-171">The first is the `secure` field, which will show `true` only if all necessary locks have been enabled (or features disabled) to enable a secure testing environment, and none of these have been compromised since the app entered the lockdown mode.</span></span> <span data-ttu-id="c179f-172">Das andere Feld, `messageKey`, enthält weitere anbieterspezifische Details.</span><span class="sxs-lookup"><span data-stu-id="c179f-172">The other field, `messageKey`, includes other details or information that is vendor-specific.</span></span> <span data-ttu-id="c179f-173">Hier können Hersteller zusätzliche Informationen hinterlegen, die das boolesche Kennzeichen `secure` erweitern:</span><span class="sxs-lookup"><span data-stu-id="c179f-173">The intent here is to allow vendors to put additional information that augments the boolean `secure` flag:</span></span>

```JSON
{
    'secure' : "true/false",
    'messageKey' : "some message"
}
```

**<span data-ttu-id="c179f-174">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="c179f-174">Requirements</span></span>**  
<span data-ttu-id="c179f-175">Windows10, Version1709</span><span class="sxs-lookup"><span data-stu-id="c179f-175">Windows 10, version 1709</span></span>

---

<span id="getDeviceInfo" />

### <a name="getdeviceinfo"></a><span data-ttu-id="c179f-176">getDeviceInfo</span><span class="sxs-lookup"><span data-stu-id="c179f-176">getDeviceInfo</span></span>
<span data-ttu-id="c179f-177">Ruft Details zur Plattform ab, auf der die Testanwendung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c179f-177">Gets details about the platform on which the testing application is running.</span></span> <span data-ttu-id="c179f-178">Wird verwendet, um die Informationen anzureichern, die vom Benutzer-Agent erkennbar waren.</span><span class="sxs-lookup"><span data-stu-id="c179f-178">This is used to augment any information that was discernible from the user agent.</span></span>

**<span data-ttu-id="c179f-179">Syntax</span><span class="sxs-lookup"><span data-stu-id="c179f-179">Syntax</span></span>**  
`void SecureBrowser.security.getDeviceInfo(Function callback);`

**<span data-ttu-id="c179f-180">Parameter</span><span class="sxs-lookup"><span data-stu-id="c179f-180">Parameters</span></span>**  
* `callback` <span data-ttu-id="c179f-181">- Die Funktion, die aufgerufen wird, wenn diese Funktion abgeschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="c179f-181">- The function to call when this function completes.</span></span> <span data-ttu-id="c179f-182">Sie muss im Format `Function(String infoObj)` vorliegen, wobei `infoObj` eine JSON-Zeichenfolge ist, die mehrere Felder enthält.</span><span class="sxs-lookup"><span data-stu-id="c179f-182">It must be of the form `Function(String infoObj)` where `infoObj` is a JSON string containing several fields.</span></span> <span data-ttu-id="c179f-183">Die folgenden Felder müssen unterstützt werden:</span><span class="sxs-lookup"><span data-stu-id="c179f-183">The following fields must be supported:</span></span>
    * `os` <span data-ttu-id="c179f-184">steht für den Typ des Betriebssystems (z.B. Windows, MacOS, Linux, iOS, Android usw.)</span><span class="sxs-lookup"><span data-stu-id="c179f-184">represents the OS type (for example: Windows, macOS, Linux, iOS, Android, etc.)</span></span>
    * `name` <span data-ttu-id="c179f-185">steht für den Namen der Betriebssystemversion, sofern vorhanden (z.B. Sierra, Ubuntu).</span><span class="sxs-lookup"><span data-stu-id="c179f-185">represents the OS release name, if any (for example: Sierra, Ubuntu).</span></span>
    * `version` <span data-ttu-id="c179f-186">steht für die Version des Betriebssystems (z.B. 10.1, 10 Pro usw.).</span><span class="sxs-lookup"><span data-stu-id="c179f-186">represents the OS version (for example: 10.1, 10 Pro, etc.)</span></span>
    * `brand` <span data-ttu-id="c179f-187">steht für das sichere Browser-Branding (z.B. OAKS, CA, SmarterApp usw.).</span><span class="sxs-lookup"><span data-stu-id="c179f-187">represents the secure browser branding (for example: OAKS, CA, SmarterApp, etc.)</span></span>
    * `model` <span data-ttu-id="c179f-188">gibt nur das Gerätemodell für mobile Geräte an; null/nicht verwendet bei Desktopbrowsern.</span><span class="sxs-lookup"><span data-stu-id="c179f-188">represents the device model for mobile devices only; null/unused for desktop browsers.</span></span>

**<span data-ttu-id="c179f-189">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="c179f-189">Requirements</span></span>**  
<span data-ttu-id="c179f-190">Windows10, Version1709</span><span class="sxs-lookup"><span data-stu-id="c179f-190">Windows 10, version 1709</span></span>

---

<span id="examineProcessList" />

### <a name="examineprocesslist"></a><span data-ttu-id="c179f-191">examineProcessList</span><span class="sxs-lookup"><span data-stu-id="c179f-191">examineProcessList</span></span>
<span data-ttu-id="c179f-192">Ruft die Liste aller Prozesse ab, die auf dem Clientcomputer im Besitz des Benutzers ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="c179f-192">Gets the list of all processes running on the client machine owned by the user.</span></span> <span data-ttu-id="c179f-193">Die Testanwendung ruft diese Funktion auf, um die Liste zu überprüfen und mit einer Liste der Prozesse zu vergleichen, die während der Testphase auf die Blacklist gesetzt wurden.</span><span class="sxs-lookup"><span data-stu-id="c179f-193">The testing application will invoke this to examine the list and compare it with a list of processes that have been deemed blacklisted during testing cycle.</span></span> <span data-ttu-id="c179f-194">Dieser Aufruf sollte sowohl zu Beginn einer Prüfung sowie in regelmäßigen Abständen während der Prüfung ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="c179f-194">This call should be invoked both at the start of an assessment and periodically while the student is taking the assessment.</span></span> <span data-ttu-id="c179f-195">Wenn ein Prozess auf der Blacklist erkannt wird, sollte die Prüfung beendet werden, um die Integrität des Tests zu wahren.</span><span class="sxs-lookup"><span data-stu-id="c179f-195">If a blacklisted process is detected, the assessment should be stopped to preserve test integrity.</span></span>

**<span data-ttu-id="c179f-196">Syntax</span><span class="sxs-lookup"><span data-stu-id="c179f-196">Syntax</span></span>**  
`void SecureBrowser.security.examineProcessList(String[] blacklistedProcessList, Function callback);`

**<span data-ttu-id="c179f-197">Parameter</span><span class="sxs-lookup"><span data-stu-id="c179f-197">Parameters</span></span>**  
* `blacklistedProcessList` <span data-ttu-id="c179f-198">- Die Liste der Prozesse, die von der Testanwendung auf die Blacklist gesetzt wurden.</span><span class="sxs-lookup"><span data-stu-id="c179f-198">- The list of processes that the testing application has blacklisted.</span></span>  
`callback` <span data-ttu-id="c179f-199">- Die Funktion, die aufgerufen wird, sobald die aktiven Prozesse gefunden wurden.</span><span class="sxs-lookup"><span data-stu-id="c179f-199">- The function to invoke once the active processes have been found.</span></span> <span data-ttu-id="c179f-200">Sie muss im Format `Function(String foundBlacklistedProcesses)` vorliegen, wobei `foundBlacklistedProcesses` das Format `"['process1.exe','process2.exe','processEtc.exe']"` hat.</span><span class="sxs-lookup"><span data-stu-id="c179f-200">It must be in the form: `Function(String foundBlacklistedProcesses)` where `foundBlacklistedProcesses` is in the form: `"['process1.exe','process2.exe','processEtc.exe']"`.</span></span> <span data-ttu-id="c179f-201">Sie ist leer, wenn keine Prozesse auf der Blacklist gefunden wurden.</span><span class="sxs-lookup"><span data-stu-id="c179f-201">It will be empty if no blacklisted processes were found.</span></span> <span data-ttu-id="c179f-202">Wenn sie null ist, bedeutet dies, dass im ursprünglichen Funktionsaufruf ein Fehler aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="c179f-202">If it is null, this indicates that an error occurred in the original function call.</span></span>

<span data-ttu-id="c179f-203">**Hinweise** Diese Liste enthält keine Systemprozesse.</span><span class="sxs-lookup"><span data-stu-id="c179f-203">**Remarks** The list does not include system processes.</span></span>

**<span data-ttu-id="c179f-204">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="c179f-204">Requirements</span></span>**  
<span data-ttu-id="c179f-205">Windows10, Version1709</span><span class="sxs-lookup"><span data-stu-id="c179f-205">Windows 10, version 1709</span></span>

---

<span id="close"/>

### <a name="close"></a><span data-ttu-id="c179f-206">close</span><span class="sxs-lookup"><span data-stu-id="c179f-206">close</span></span>
<span data-ttu-id="c179f-207">Schließt den Browser und entsperrt das Gerät.</span><span class="sxs-lookup"><span data-stu-id="c179f-207">Closes the browser and unlocks the device.</span></span> <span data-ttu-id="c179f-208">Die Testanwendung sollte diese Funktion aufrufen, wenn der Benutzer beschließt, den Browser zu beenden.</span><span class="sxs-lookup"><span data-stu-id="c179f-208">The testing application should invoke this when the user elects to exit the browser.</span></span>

**<span data-ttu-id="c179f-209">Syntax</span><span class="sxs-lookup"><span data-stu-id="c179f-209">Syntax</span></span>**  
`void SecureBrowser.security.close(restart);`

**<span data-ttu-id="c179f-210">Parameter</span><span class="sxs-lookup"><span data-stu-id="c179f-210">Parameters</span></span>**  
* `restart` <span data-ttu-id="c179f-211">- Dieser Parameter wird ignoriert, muss aber angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="c179f-211">- This parameter is ignored but must be provided.</span></span>

<span data-ttu-id="c179f-212">**Hinweise** In Windows10, Version 1607, muss das Gerät zunächst gesperrt werden.</span><span class="sxs-lookup"><span data-stu-id="c179f-212">**Remarks** In Windows 10, version 1607, the device must be locked down initially.</span></span> <span data-ttu-id="c179f-213">In späteren Versionen schließt diese Methode den Browser unabhängig davon, ob das Gerät gesperrt ist.</span><span class="sxs-lookup"><span data-stu-id="c179f-213">In later versions, this method closes the browser regardless of whether the device is locked down.</span></span>

**<span data-ttu-id="c179f-214">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="c179f-214">Requirements</span></span>**  
<span data-ttu-id="c179f-215">Windows10, Version1709</span><span class="sxs-lookup"><span data-stu-id="c179f-215">Windows 10, version 1709</span></span>

---

<span id="getPermissiveMode" />

### <a name="getpermissivemode"></a><span data-ttu-id="c179f-216">getPermissiveMode</span><span class="sxs-lookup"><span data-stu-id="c179f-216">getPermissiveMode</span></span>
<span data-ttu-id="c179f-217">Die Testanwendung sollte diese Funktion aufrufen, um zu bestimmen, ob der eingeschränkte Modus aktiviert oder deaktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="c179f-217">The testing web application should invoke this to determine if permissive mode is on or off.</span></span> <span data-ttu-id="c179f-218">Im eingeschränkten Modus lockert ein Browser erwartungsgemäß einige seiner strengen Sicherheitregeln, damit Hilfstechnologien mit dem sicheren Browser funktionieren.</span><span class="sxs-lookup"><span data-stu-id="c179f-218">In permissive mode, a browser is expected to relax some of its stringent security hooks to allow assistive technology to work with the secure browser.</span></span> <span data-ttu-id="c179f-219">Browser, die die Benutzeroberflächen anderer Anwendungen strikt daran hindern, über diesen angezeigt zu werden, könnten dieses Verhalten im eingeschränkten Modus lockern.</span><span class="sxs-lookup"><span data-stu-id="c179f-219">For example, browsers that aggressively prevent other application UIs from presenting on top of them might want to relax this when in permissive mode.</span></span> 

**<span data-ttu-id="c179f-220">Syntax</span><span class="sxs-lookup"><span data-stu-id="c179f-220">Syntax</span></span>**  
`void SecureBrowser.security.getPermissiveMode(Function callback)`

**<span data-ttu-id="c179f-221">Parameter</span><span class="sxs-lookup"><span data-stu-id="c179f-221">Parameters</span></span>**  
* `callback` <span data-ttu-id="c179f-222">- Die Funktion, die aufgerufen wird, wenn dieser Aufruf abgeschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="c179f-222">- The function to invoke when this call completes.</span></span> <span data-ttu-id="c179f-223">Sie muss im Format `Function(Boolean permissiveMode)` vorliegen, wobei `permissiveMode` angibt, ob für den Browser aktuell der eingeschränkte Modus aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="c179f-223">It must be in the form: `Function(Boolean permissiveMode)` where `permissiveMode` indicates whether the browser is currently in permissive mode.</span></span> <span data-ttu-id="c179f-224">Wenn sie nicht definiert oder null ist, ist beim GET-Vorgang ein Fehler aufgetreten.</span><span class="sxs-lookup"><span data-stu-id="c179f-224">If it is undefined or null, an error occurred in the get operation.</span></span>

**<span data-ttu-id="c179f-225">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="c179f-225">Requirements</span></span>**  
<span data-ttu-id="c179f-226">Windows10, Version1709</span><span class="sxs-lookup"><span data-stu-id="c179f-226">Windows 10, version 1709</span></span>

---

<span id="setPermissiveMode" />

### <a name="setpermissivemode"></a><span data-ttu-id="c179f-227">setPermissiveMode</span><span class="sxs-lookup"><span data-stu-id="c179f-227">setPermissiveMode</span></span>
<span data-ttu-id="c179f-228">Die Testanwendung sollte diese Funktion aufrufen, um den eingeschränkten Modus zu aktivieren oder zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="c179f-228">The testing web application should invoke this to toggle permissive mode on or off.</span></span> <span data-ttu-id="c179f-229">Im eingeschränkten Modus lockert ein Browser erwartungsgemäß einige seiner strengen Sicherheitregeln, damit Hilfstechnologien mit dem sicheren Browser funktionieren.</span><span class="sxs-lookup"><span data-stu-id="c179f-229">In permissive mode, a browser is expected to relax some of its stringent security hooks to allow assistive technology to work with the secure browser.</span></span> <span data-ttu-id="c179f-230">Browser, die die Benutzeroberflächen anderer Anwendungen strikt daran hindern, über diesen angezeigt zu werden, könnten dieses Verhalten im eingeschränkten Modus lockern.</span><span class="sxs-lookup"><span data-stu-id="c179f-230">For example, browsers that aggressively prevent other application UIs from presenting on top of them might want to relax this when in permissive mode.</span></span> 

**<span data-ttu-id="c179f-231">Syntax</span><span class="sxs-lookup"><span data-stu-id="c179f-231">Syntax</span></span>**  
`void SecureBrowser.security.setPermissiveMode(Boolean enable, Function callback)`

**<span data-ttu-id="c179f-232">Parameter</span><span class="sxs-lookup"><span data-stu-id="c179f-232">Parameters</span></span>**  
* `enable` <span data-ttu-id="c179f-233">– Der boolesche Wert, der den Status des vorgesehenen eingeschränkten Modus angibt.</span><span class="sxs-lookup"><span data-stu-id="c179f-233">- The Boolean value indicating the intended permissive mode status.</span></span>  
* `callback` <span data-ttu-id="c179f-234">- Die Funktion, die aufgerufen wird, wenn dieser Aufruf abgeschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="c179f-234">- The function to invoke when this call completes.</span></span> <span data-ttu-id="c179f-235">Sie muss im Format `Function(Boolean permissiveMode)` vorliegen, wobei `permissiveMode` angibt, ob für den Browser aktuell der eingeschränkte Modus aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="c179f-235">It must be in the form: `Function(Boolean permissiveMode)` where `permissiveMode` indicates whether the browser is currently in permissive mode.</span></span> <span data-ttu-id="c179f-236">Wenn sie nicht definiert oder null ist, ist beim SET-Vorgang ein Fehler aufgetreten.</span><span class="sxs-lookup"><span data-stu-id="c179f-236">If it is undefined or null, an error occurred in the set operation.</span></span>

**<span data-ttu-id="c179f-237">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="c179f-237">Requirements</span></span>**  
<span data-ttu-id="c179f-238">Windows10, Version1709</span><span class="sxs-lookup"><span data-stu-id="c179f-238">Windows 10, version 1709</span></span>

---

<span id="emptyClipBoard"/>

### <a name="emptyclipboard"></a><span data-ttu-id="c179f-239">emptyClipBoard</span><span class="sxs-lookup"><span data-stu-id="c179f-239">emptyClipBoard</span></span>
<span data-ttu-id="c179f-240">Löscht die Zwischenablage des Systems.</span><span class="sxs-lookup"><span data-stu-id="c179f-240">Clears the system clipboard.</span></span> <span data-ttu-id="c179f-241">Die Testanwendung sollte diese Funktion aufrufen, um zu erzwingen, dass alle Daten gelöscht werden, die unter Umständen in der Zwischenablage des Systems gespeichert sind.</span><span class="sxs-lookup"><span data-stu-id="c179f-241">The testing application should invoke this to force clear any data that may be stored in the system clipboard.</span></span> <span data-ttu-id="c179f-242">Dieser Vorgang wird auch von der Funktion **[lockDown](#lockDown)** ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="c179f-242">The **[lockDown](#lockDown)** function also performs this operation.</span></span>

**<span data-ttu-id="c179f-243">Syntax</span><span class="sxs-lookup"><span data-stu-id="c179f-243">Syntax</span></span>**  
`void SecureBrowser.security.emptyClipBoard();`

**<span data-ttu-id="c179f-244">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="c179f-244">Requirements</span></span>**  
<span data-ttu-id="c179f-245">Windows10, Version1709</span><span class="sxs-lookup"><span data-stu-id="c179f-245">Windows 10, version 1709</span></span>

---

<span id="getMACAddress" />

### <a name="getmacaddress"></a><span data-ttu-id="c179f-246">getMACAddress</span><span class="sxs-lookup"><span data-stu-id="c179f-246">getMACAddress</span></span>
<span data-ttu-id="c179f-247">Ruft die Liste der MAC-Adressen für das Gerät ab.</span><span class="sxs-lookup"><span data-stu-id="c179f-247">Gets the list of MAC addresses for the device.</span></span> <span data-ttu-id="c179f-248">Die Testanwendung sollte diese Funktion aufrufen, um Unterstützung bei der Diagnose zu bieten.</span><span class="sxs-lookup"><span data-stu-id="c179f-248">The testing application should invoke this to assist in diagnostics.</span></span> 

**<span data-ttu-id="c179f-249">Syntax</span><span class="sxs-lookup"><span data-stu-id="c179f-249">Syntax</span></span>**  
`void SecureBrowser.security.getMACAddress(Function callback);`

**<span data-ttu-id="c179f-250">Parameter</span><span class="sxs-lookup"><span data-stu-id="c179f-250">Parameters</span></span>**  
* `callback` <span data-ttu-id="c179f-251">- Die Funktion, die aufgerufen wird, wenn dieser Aufruf abgeschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="c179f-251">- The function to invoke when this call completes.</span></span> <span data-ttu-id="c179f-252">Sie muss im Format `Function(String addressArray)` vorliegen, wobei `addressArray` das Format `"['00:11:22:33:44:55','etc']"` hat.</span><span class="sxs-lookup"><span data-stu-id="c179f-252">It must be in the form: `Function(String addressArray)` where `addressArray` is in the form: `"['00:11:22:33:44:55','etc']"`.</span></span>

**<span data-ttu-id="c179f-253">Hinweise</span><span class="sxs-lookup"><span data-stu-id="c179f-253">Remarks</span></span>**  
<span data-ttu-id="c179f-254">Es ist schwierig, sich bei der Unterscheidung zwischen den Endnutzercomputern innerhalb der Testserver auf die Quell-IP-Adressen zu verlassen, da in Schulen für gewöhnlich Firewalls/NATs/Proxys verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c179f-254">It is difficult to rely on source IP addresses to distinguish between end user machines within the testing servers because firewalls/NATs/Proxies are commonly in use at the schools.</span></span> <span data-ttu-id="c179f-255">Anhand der MAC-Adressen kann die App für Diagnosezwecke zwischen den Endbenutzercomputern hinter einer gängigen Firewall unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="c179f-255">The MAC addresses allow the app to distinguish end client machines behind a common firewall for diagnostics purposes.</span></span>

**<span data-ttu-id="c179f-256">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="c179f-256">Requirements</span></span>**  
<span data-ttu-id="c179f-257">Windows10, Version1709</span><span class="sxs-lookup"><span data-stu-id="c179f-257">Windows 10, version 1709</span></span>

---

<span id="getStartTime" />

### <a name="getstarttime"></a><span data-ttu-id="c179f-258">getStartTime</span><span class="sxs-lookup"><span data-stu-id="c179f-258">getStartTime</span></span>
<span data-ttu-id="c179f-259">Ruft die Zeit ab, zu der die Test-App gestartet wurde.</span><span class="sxs-lookup"><span data-stu-id="c179f-259">Gets the time that the testing app was started.</span></span>

**<span data-ttu-id="c179f-260">Syntax</span><span class="sxs-lookup"><span data-stu-id="c179f-260">Syntax</span></span>**  
`DateTime SecureBrowser.settings.getStartTime();`

**<span data-ttu-id="c179f-261">Rückgabe</span><span class="sxs-lookup"><span data-stu-id="c179f-261">Return</span></span>**  
<span data-ttu-id="c179f-262">Ein DateTime-Objekt, das den Zeitpunkt angibt, zu dem die Test-App gestartet wurde.</span><span class="sxs-lookup"><span data-stu-id="c179f-262">A DateTime object indicating the time the testing app was started.</span></span>

**<span data-ttu-id="c179f-263">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="c179f-263">Requirements</span></span>**  
<span data-ttu-id="c179f-264">Windows10, Version1709</span><span class="sxs-lookup"><span data-stu-id="c179f-264">Windows 10, version 1709</span></span>

---

<span id="getCapability"/>

### <a name="getcapability"></a><span data-ttu-id="c179f-265">getCapability</span><span class="sxs-lookup"><span data-stu-id="c179f-265">getCapability</span></span>
<span data-ttu-id="c179f-266">Fragt ab, ob eine Funktion aktiviert oder deaktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="c179f-266">Queries whether a capability is enabled or disabled.</span></span> 

**<span data-ttu-id="c179f-267">Syntax</span><span class="sxs-lookup"><span data-stu-id="c179f-267">Syntax</span></span>**  
`Object SecureBrowser.security.getCapability(String feature)`

**<span data-ttu-id="c179f-268">Parameter</span><span class="sxs-lookup"><span data-stu-id="c179f-268">Parameters</span></span>**  
`feature` <span data-ttu-id="c179f-269">- Die Zeichenfolge, die festlegt, welche Funktion abgefragt werden soll.</span><span class="sxs-lookup"><span data-stu-id="c179f-269">- The string to determine which capability to query.</span></span> <span data-ttu-id="c179f-270">Gültige Funktionszeichenfolgen sind „screenMonitoring“, „printing“ und „textSuggestions“ (Groß-/Kleinschreibung spielt keine Rolle).</span><span class="sxs-lookup"><span data-stu-id="c179f-270">Valid capability strings are "screenMonitoring", "printing", and "textSuggestions" (case insensitive).</span></span>

**<span data-ttu-id="c179f-271">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="c179f-271">Return Value</span></span>**  
<span data-ttu-id="c179f-272">Diese Funktion gibt ein JavaScript-Objekt oder Literalzeichen im folgenden Format zurück: `{<feature>:true|false}`.</span><span class="sxs-lookup"><span data-stu-id="c179f-272">This function returns either a JavaScript Object or literal with the form: `{<feature>:true|false}`.</span></span> <span data-ttu-id="c179f-273">**true**, wenn die abgefragte Funktion aktiviert ist, **false**, wenn die Funktion nicht aktiviert oder die Funktionszeichenfolge ungültig ist.</span><span class="sxs-lookup"><span data-stu-id="c179f-273">**true** if the queried capability is enabled, **false** if the capability is not enabled or the capability string is invalid.</span></span>

<span data-ttu-id="c179f-274">**Anforderungen** Windows10, Version 1703</span><span class="sxs-lookup"><span data-stu-id="c179f-274">**Requirements** Windows 10, version 1703</span></span>

---

<span id="setCapability"/>

### <a name="setcapability"></a><span data-ttu-id="c179f-275">setCapability</span><span class="sxs-lookup"><span data-stu-id="c179f-275">setCapability</span></span>
<span data-ttu-id="c179f-276">Aktiviert oder deaktiviert eine bestimmte Funktion des Browsers.</span><span class="sxs-lookup"><span data-stu-id="c179f-276">Enables or disables a specific capability on the browser.</span></span>

**<span data-ttu-id="c179f-277">Syntax</span><span class="sxs-lookup"><span data-stu-id="c179f-277">Syntax</span></span>**  
`void SecureBrowser.security.setCapability(String feature, String value, Function onSuccess, Function onError)`

**<span data-ttu-id="c179f-278">Parameter</span><span class="sxs-lookup"><span data-stu-id="c179f-278">Parameters</span></span>**  
* `feature` <span data-ttu-id="c179f-279">- Die Zeichenfolge, mit der bestimmt wird, welche Funktion festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="c179f-279">- The string to determine which capability to set.</span></span> <span data-ttu-id="c179f-280">Gültige Funktionszeichenfolgen sind `"screenMonitoring"`, `"printing"` und `"textSuggestions"` (Groß-/Kleinschreibung spielt keine Rolle).</span><span class="sxs-lookup"><span data-stu-id="c179f-280">Valid capability strings are `"screenMonitoring"`, `"printing"`, and `"textSuggestions"` (case insensitive).</span></span>  
* `value` <span data-ttu-id="c179f-281">– Die gewünschte Einstellung für das Feature.</span><span class="sxs-lookup"><span data-stu-id="c179f-281">- The intended setting for the feature.</span></span> <span data-ttu-id="c179f-282">Muss entweder `"true"` oder `"false"` sein.</span><span class="sxs-lookup"><span data-stu-id="c179f-282">It must be either `"true"` or `"false"`.</span></span>  
* `onSuccess` <span data-ttu-id="c179f-283">- [optional] Die Funktion, die aufgerufen wird, nachdem der SET-Vorgang erfolgreich abgeschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="c179f-283">- [optional] The function to call after the set operation has been completed successfully.</span></span> <span data-ttu-id="c179f-284">Sie muss im Format `Function(String jsonValue)` vorliegen, wobei *jsonValue* das Format `{<feature>:true|false|undefined}` hat.</span><span class="sxs-lookup"><span data-stu-id="c179f-284">It must be of the form `Function(String jsonValue)` where *jsonValue* is in the form: `{<feature>:true|false|undefined}`.</span></span>  
* `onError` <span data-ttu-id="c179f-285">- [optional] Die Funktion, die aufgerufen wird, wenn der SET-Vorgang fehlgeschlagen ist.</span><span class="sxs-lookup"><span data-stu-id="c179f-285">- [optional] The function to call if the set operation failed.</span></span> <span data-ttu-id="c179f-286">Sie muss im Format `Function(String jsonValue)` vorliegen, wobei *jsonValue* das Format `{<feature>:true|false|undefined}` hat.</span><span class="sxs-lookup"><span data-stu-id="c179f-286">It must be of the form `Function(String jsonValue)` where *jsonValue* is in the form: `{<feature>:true|false|undefined}`.</span></span>

**<span data-ttu-id="c179f-287">Hinweise</span><span class="sxs-lookup"><span data-stu-id="c179f-287">Remarks</span></span>**  
<span data-ttu-id="c179f-288">Wenn die Zielfunktion dem Browser nicht bekannt ist, übergibt diese Funktion den Wert `undefined` an die Rückruffunktion.</span><span class="sxs-lookup"><span data-stu-id="c179f-288">If the targeted feature is unknown to the browser, this function will pass a value of `undefined` to the callback function.</span></span>

<span data-ttu-id="c179f-289">**Anforderungen** Windows10, Version 1703</span><span class="sxs-lookup"><span data-stu-id="c179f-289">**Requirements** Windows 10, version 1703</span></span>

---

<span id="isRemoteSession"/>

### <a name="isremotesession"></a><span data-ttu-id="c179f-290">isRemoteSession</span><span class="sxs-lookup"><span data-stu-id="c179f-290">isRemoteSession</span></span>
<span data-ttu-id="c179f-291">Überprüft, ob die aktuelle Sitzung remote angemeldet ist.</span><span class="sxs-lookup"><span data-stu-id="c179f-291">Checks if the current session is logged in remotely.</span></span>

**<span data-ttu-id="c179f-292">Syntax</span><span class="sxs-lookup"><span data-stu-id="c179f-292">Syntax</span></span>**  
`Boolean SecureBrowser.security.isRemoteSession();`

**<span data-ttu-id="c179f-293">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="c179f-293">Return value</span></span>**  
<span data-ttu-id="c179f-294">**true**, wenn es sich bei der aktuellen Sitzung um eine Remotesitzung handelt, andernfalls **false**.</span><span class="sxs-lookup"><span data-stu-id="c179f-294">**true** if the current session is remote, otherwise **false**.</span></span>

**<span data-ttu-id="c179f-295">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="c179f-295">Requirements</span></span>**  
<span data-ttu-id="c179f-296">Windows10, Version1709</span><span class="sxs-lookup"><span data-stu-id="c179f-296">Windows 10, version 1709</span></span>

---

<span id="isVMSession"/>

### <a name="isvmsession"></a><span data-ttu-id="c179f-297">isVMSession</span><span class="sxs-lookup"><span data-stu-id="c179f-297">isVMSession</span></span>
<span data-ttu-id="c179f-298">Überprüft, ob die aktuelle Sitzung auf einem virtuellen Computer ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c179f-298">Checks if the current session is running within a virtual machine.</span></span>

**<span data-ttu-id="c179f-299">Syntax</span><span class="sxs-lookup"><span data-stu-id="c179f-299">Syntax</span></span>**  
`Boolean SecureBrowser.security.isVMSession();`

**<span data-ttu-id="c179f-300">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="c179f-300">Return value</span></span>**  
<span data-ttu-id="c179f-301">**true**, wenn die aktuelle Sitzung auf einem virtuellen Computer ausgeführt wird, andernfalls **false**.</span><span class="sxs-lookup"><span data-stu-id="c179f-301">**true** if the current session is running in a virtual machine, otherwise **false**.</span></span>

**<span data-ttu-id="c179f-302">Hinweise</span><span class="sxs-lookup"><span data-stu-id="c179f-302">Remarks</span></span>**  
<span data-ttu-id="c179f-303">Diese API-Prüfung erkennt nur VM Sitzungen, die in bestimmten Hypervisoren ausgeführt werden, die die entsprechenden APIs implementieren.</span><span class="sxs-lookup"><span data-stu-id="c179f-303">This API check can only detect VM sessions that are running in certain hypervisors that implement the appropriate APIs</span></span>

**<span data-ttu-id="c179f-304">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="c179f-304">Requirements</span></span>**  
<span data-ttu-id="c179f-305">Windows10, Version1709</span><span class="sxs-lookup"><span data-stu-id="c179f-305">Windows 10, version 1709</span></span>

---